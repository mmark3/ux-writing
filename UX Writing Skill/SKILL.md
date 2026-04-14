---
name: ux-writing
description: >
  End-to-end UX writing and content design skill for creating, evaluating, and
  managing UI copy across digital products. Use this skill whenever someone needs
  to write microcopy, draft screen flows, audit existing content, define content
  strategy or information architecture for a UI, or review/critique UX copy
  against standards. Also trigger when someone drops a Figma link and asks for
  copy, references voice and tone or content patterns, mentions UX writing or
  content design, asks to write error messages, empty states, button labels,
  onboarding flows, notifications, or any user-facing strings in a product
  interface. This skill routes to the appropriate sub-skill based on the task —
  you don't need to know which sub-skill to use, just describe what you need.
---

# UX Writing

A modular skill for the full UX writing process. It supports both end-to-end
content design workflows (discovery → strategy → drafting → review) and quick
single-task requests like writing a few button labels.

## How this skill works

This is a **router skill**. Based on what the user needs, you'll load and follow
the instructions in the appropriate sub-skill. Most requests will hit one
sub-skill directly. Larger projects may move through several in sequence.

### Sub-skills

| Sub-skill | When to use it | Path |
|-----------|---------------|------|
| **Discovery & Audit** | Auditing existing content, identifying gaps, heuristic reviews, competitive analysis | `sub-skills/discovery/SKILL.md` |
| **Content Strategy & IA** | Information architecture, content modeling, flow mapping, defining content structure before writing | `sub-skills/strategy/SKILL.md` |
| **Drafting** | Writing microcopy, screen flows, component-level copy, any user-facing strings | `sub-skills/drafting/SKILL.md` |
| **Review & Critique** | Evaluating copy against standards, readability checks, consistency reviews, providing feedback on existing copy | `sub-skills/review/SKILL.md` |

### Input types

Users may provide any combination of:

- **A Figma link** — to a screen or frame. Use the Figma MCP to pull the
  component tree and design system component names. This enriches the output
  but is never required.
- **A plain text brief** — a description of what they need ("write an error
  message for failed payment processing").
- **A ticket or task reference** — a Jira link, story description, or
  acceptance criteria to extract requirements from.
- **Existing copy to evaluate** — pasted text, a screenshot, or a Figma link
  to screens that already have copy in them.
- **A vague or conversational ask** — "I need some help with this screen."
  Ask enough clarifying questions to understand the component type, user
  context, and intent before proceeding.

All sub-skills should be able to work with any of these inputs. A Figma link
is a bonus that enables richer scaffolding and component-aware output — not a
prerequisite for any workflow.

### Routing logic

Detect which sub-skill to load based on these signals:

**→ Drafting** (most common — default here when ambiguous)
- User asks to "write," "draft," or "create" copy for a screen, component, or flow
- User describes a UI scenario and needs the words for it
- User asks for error messages, empty states, CTAs, tooltips, labels, etc.
- User provides a Figma link and asks for copy
- Quick microcopy asks with no broader context

**→ Review & Critique**
- User shares existing copy and asks for feedback
- User says "review," "check," "critique," or "evaluate" their content
- User wants to verify copy against brand voice, style, or accessibility standards
- User asks "does this sound right" or "how can I improve this"

**→ Discovery & Audit**
- User wants to understand what content currently exists
- User asks for a content audit, gap analysis, or heuristic review
- User is starting a new project and needs to assess the current state
- User asks to analyze a competitor's content patterns

**→ Content Strategy & IA**
- User needs to plan content structure before writing
- User asks about information architecture, navigation labels, content hierarchy
- User wants to map a user flow or define content requirements

When a request spans multiple sub-skills (e.g., "audit this flow and then
rewrite it"), load them in process order: discovery → strategy → drafting →
review. Confirm the output of each phase with the user before moving to the
next.

## MCP integrations

This skill connects to external tools via MCP. These connections are lazy-loaded
— only pull from them when a sub-skill needs the data.

### Supernova (content standards)

The organization's single source of truth for content standards. Access via the
Supernova MCP server.

Supernova content is organized in two layers:

- **Foundational standards** — voice and tone, style rules, terminology, and
  general writing guidelines that apply across all UI copy.
- **Component and pattern standards** — content guidance scoped to specific
  atomic components (e.g., buttons, text fields, tooltips) and molecular
  patterns (e.g., form groups, card layouts, notification banners). Each
  component or pattern may have its own content standards available through
  the MCP.

When writing or auditing for specific components, pull both the foundational
standards and the relevant component/pattern-level standards.

**When to pull from Supernova:**
- **Drafting** — retrieve voice and tone guidelines, relevant content patterns,
  and component-specific writing examples before generating copy.
- **Review** — retrieve the evaluation criteria, style rules, and pattern
  standards to assess copy against.
- **Strategy** — retrieve content model definitions or pattern libraries when
  planning content architecture.
- **Discovery** — retrieve existing standards to use as the baseline for audits.

Do not pull Supernova content speculatively. Wait until a sub-skill identifies
what it needs, then make targeted requests for that specific content.

### Figma (screen and component context)

Access to design files via the Figma MCP server. Currently **read-only**.

**When to use Figma:**
- User provides a Figma link (frame, screen, or page URL).
- Pull the component tree to identify design system components by name.
- Use component names to scaffold structured output and to make targeted
  Supernova requests for component-specific patterns.

Figma is an input enrichment tool. Never block a workflow because no Figma
link was provided.

**Future:** When Figma write access becomes available, the drafting sub-skill
will gain an output step to push finalized copy back to Figma frames.

## Output formats

Sub-skills produce output in one of two formats depending on task complexity.

### Structured markdown (default for flows and multi-component work)

```markdown
## Screen: [Screen Name]

### [Component Name]
- **Heading:** Copy here
- **Body:** Copy here
- **CTA (primary):** Button label
- **Error state:** Error message
- **Empty state:** Empty state copy
```

When a Figma link is provided, use the actual design system component names
from the component tree instead of generic placeholders.

### Compact table (for quick single-component or microcopy asks)

| Element | Copy | Notes |
|---------|------|-------|
| Heading | Copy here | Context or rationale |
| CTA | Button label | Character count if relevant |
| Error | Error message | Trigger condition |

The sub-skill determines which format to use based on the scope of the request.
If the user asks for copy for a single component or a handful of strings, use
the table. If the request involves multiple screens or a flow, use structured
markdown.

## Users

This skill is built for content designers and adjacent roles (product designers,
UX designers, product managers) who need to create or evaluate user-facing copy.
Assume the user has working knowledge of UX concepts and design systems. Don't
over-explain what a component is or how a design system works — focus on the
content.

The skill is also designed to be usable by AI agents operating autonomously
within a content design workflow. Instructions should be specific and
deterministic enough for an agent to follow without human clarification when
given sufficient input context.