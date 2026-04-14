# Client Customization & Contentful Integration

This document describes the planned architecture for flow-level client
customization using the UX Writing skill. It covers the content token system
in Contentful, the client customization spec, and how each sub-skill will
be updated when the Contentful MCP integration is available.

## Content token architecture

Content in the system is managed at the token level in Contentful. Each
piece of UI copy — a heading, a button label, an error message — is a
discrete entry with a semantic token identifier.

### How tokens work

A token is a semantic identifier that maps to a piece of content. The same
token appears in the UI layer (Figma variables), and at runtime the system
resolves the token to the correct content entry in Contentful.

**Base entries** represent the standard/default content for a flow. They
are the canonical version that ships unless a client-specific variant exists.

**Variant entries** are created for client customizations. They share the
same token as the base entry but are tagged with metadata identifying which
client they belong to. At runtime, the system matches on the token + client
metadata to resolve the correct variant.

### Example: Registration welcome headline

```
Base entry:
  token: reg.welcome.header.headline
  value: "Welcome to {brand_name}"
  metadata: { brand: ["default"], channel: ["web", "mobile"] }

Client variant (Acme Health):
  token: reg.welcome.header.headline
  value: "Start your Acme Health journey"
  metadata: { brand: ["acme"], channel: ["web", "mobile"] }
```

The token stays the same. The value changes. The metadata tells the system
which variant to serve.

### Token naming convention

Tokens follow a hierarchical dot notation:
`{feature}.{step}.{component_intent}.{format}`

Examples:
- `reg.welcome.header.headline`
- `reg.eligibility.error.description`
- `reg.confirmation.cta.primary`
- `claims.status.empty.headline`

This structure encodes where the content lives in the flow (feature + step),
what role it plays (component intent), and what type of content it is (format).

## Client customization spec

Before customizing any flow for a new client, a structured customization
spec must be created. This replaces the ad hoc process and serves as the
single source of truth for what changes per client.

### Spec template

```markdown
# Client Customization Spec: [Client Name]

## Client identity
- **Client name:** [Display name]
- **Client identifier:** [Metadata tag used in Contentful, e.g., "acme"]
- **Effective date:** [When this client goes live]

## Terminology overrides
| Standard term | Client term | Scope | Notes |
|--------------|-------------|-------|-------|
| Member | Participant | Global | Used in all member-facing content |
| Provider | Doctor | Contextual | Use "provider" in formal/legal contexts |
| Plan | Coverage | Global | |

## Voice and tone adjustments
- **Base voice:** [Reference to Supernova foundational standards]
- **Adjustments:** [How this client's tone differs — e.g., more formal,
  warmer, more clinical, etc.]
- **Examples of the shift:**
  - Base: "You're all set! Your coverage starts on {date}."
  - Client variant: "Your enrollment is confirmed. Coverage begins {date}."

## Structural changes
| Flow | Change | Details |
|------|--------|---------|
| Registration | Remove screen | Dental selection — client doesn't offer dental |
| Registration | Add screen | Employer verification step after eligibility |
| Claims | Reorder | Move "upload documents" before "submit claim" |

## Content rules
- **Required disclosures:** [Any compliance language specific to this client]
- **Forbidden terms:** [Words or phrases that cannot appear]
- **Character constraints:** [Any client-specific length limits]
- **Legal review required:** [Yes/No — and for which content types]

## Business logic differences
- **Available products:** [What this client offers vs. the standard set]
- **Feature flags:** [Features enabled/disabled for this client]
- **Eligibility rules:** [Any differences in who qualifies and how]
```

### How the spec is used

The spec is the input to any customization workflow. When a content designer
(or an AI agent) needs to customize a flow for a client:

1. Pull the client customization spec.
2. Pull the base flow's token entries from Contentful.
3. Walk through each token and apply the spec:
   - Does this token need a terminology swap? → Create variant with new term.
   - Does the tone need adjusting? → Create variant with adjusted copy.
   - Is this token's screen removed for this client? → Skip it (no variant needed).
   - Is a new screen added? → Create new base tokens for it + client variants.
   - Does the base content work as-is? → No variant needed.
4. Output the results for review.

## Sub-skill updates (when Contentful MCP is available)

### Drafting sub-skill

Add a **"Customize from base"** workflow mode. This mode activates when the
user indicates they're customizing an existing flow for a client.

**New workflow steps:**

1. **Identify the base flow.** User specifies which flow to customize (e.g.,
   "registration"). Pull the base flow's token entries from Contentful via MCP.

2. **Load the client customization spec.** Either pull from a stored location
   or ask the user to provide it. If no spec exists for this client yet, walk
   the user through creating one using the template above.

3. **Analyze tokens against spec.** For each token in the base flow:
   - Determine if a variant is needed based on the spec.
   - If yes, generate the variant content applying the spec's rules.
   - If no, note that the base entry is used as-is.

4. **Output in two layers:**
   - **Human-readable structured markdown** — the customized flow with copy
     mapped to screens and components, annotated with what changed from base.
   - **Token map** — a structured output showing each token, the base value,
     the variant value (or "use base"), and the metadata for the new entry.

**Token map output format:**

```markdown
## Token Map: [Flow Name] — [Client Name]

| Token | Base value | Variant value | Change type | Notes |
|-------|-----------|---------------|-------------|-------|
| reg.welcome.header.headline | Welcome to {brand_name} | Start your Acme Health journey | Tone + terminology | Per spec: warmer, branded |
| reg.welcome.header.description | Create your account to get started | Create your account to get started | No change | Base works as-is |
| reg.eligibility.error.description | We couldn't verify your eligibility | We couldn't verify your eligibility as an Acme Health participant | Terminology | "member" → "participant" |
| reg.dental.selection.headline | Choose your dental plan | — | Removed | Client doesn't offer dental |
```

### Discovery sub-skill

Add a **"Base vs. client"** audit mode.

**Purpose:** Compare a client's variant entries against the current base flow
to identify drift, gaps, and staleness.

**What it checks:**
- **Missing variants** — base tokens that should have a client variant (per
  the spec) but don't.
- **Stale variants** — client variants whose base entry has been updated
  since the variant was created. The variant may need to be refreshed.
- **Orphaned variants** — client variants whose base token no longer exists
  (the base flow was restructured).
- **Spec compliance** — do existing variants actually reflect the client
  customization spec? Terminology overrides applied consistently?

**Output:** An audit report organized by finding type, with specific tokens
flagged and recommended actions.

### Review sub-skill

Add evaluation dimensions for variant content:

- **Consistency with base intent** — does the variant preserve the meaning
  and purpose of the base content, or did the customization change what the
  content actually communicates?
- **Spec compliance** — does the variant correctly apply the client
  customization spec (terminology, tone, structural changes)?
- **Cross-variant consistency** — within this client's variants, is
  terminology used consistently? Does tone stay stable across the flow?

### Strategy sub-skill

Minimal changes. Strategy can help plan which tokens need variants for a
new client by walking the base flow against the customization spec before
drafting begins. This is useful for large flows where not every token needs
a variant — strategy identifies the subset that does.

## Dependencies

| Dependency | Status | Impact |
|-----------|--------|--------|
| Contentful MCP | Not yet available | Required for pulling/pushing token entries. Until available, users provide token data manually or via export. |
| Client customization specs | Process to be established | Specs need to be created and stored somewhere accessible. Location TBD. |
| Base flows modeled in Contentful | In progress | Base flows need to be fully tokenized in Contentful before "customize from base" mode works. |
| Figma write access | Not yet available | Would enable pushing variant content back to Figma after customization. Independent of Contentful integration. |

## Migration path

Until the Contentful MCP is available, the customization workflow can still
operate in a reduced mode:

1. Users export the base flow's token list manually (e.g., CSV or JSON from
   Contentful).
2. The drafting sub-skill works from the exported data instead of pulling
   live from the MCP.
3. The token map output can be imported back into Contentful manually.

This preserves the structured process (spec → analyze → generate → review)
even without live MCP integration. The MCP connection replaces the manual
export/import steps but doesn't change the workflow logic.
