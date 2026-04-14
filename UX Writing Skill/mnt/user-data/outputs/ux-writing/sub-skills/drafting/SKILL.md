---
name: ux-writing-drafting
description: >
  Write user-facing copy for digital product interfaces. Handles everything from
  quick microcopy (a single error message, button label, or tooltip) to full
  multi-screen flows (onboarding, enrollment, checkout). Works with or without
  a Figma link — adapts to whatever input the user provides.
---

# Drafting

Write UI copy that is clear, useful, and consistent with organizational
standards. This sub-skill handles the full range of drafting tasks, from a
single string to a complete flow.

## Workflow

### Step 1: Understand the request

Determine what you're working with. The user may provide any of the following —
adapt accordingly.

**If a Figma link is provided:**
1. Use the Figma MCP to pull the frame or screen.
2. Identify design system components by name from the component tree.
3. Use the component names to build the output scaffold (Step 3).
4. Use the component names to make targeted Supernova requests for
   component-specific content standards (Step 2).

**If a plain text brief is provided:**
1. Identify the component type(s) from the description (e.g., "error message"
   → error alert component, "sign-up form" → form pattern with field labels,
   helper text, CTAs).
2. If the brief is too vague to determine component types, ask clarifying
   questions. Focus on: what is the user trying to do, what component or
   screen are they writing for, and what triggers this content (e.g., what
   causes the error).

**If a ticket or task reference is provided:**
1. Extract the relevant content requirements — user story, acceptance criteria,
   screen descriptions, or flow steps.
2. Identify the component types involved.
3. Flag any gaps: if the ticket doesn't specify enough for you to write
   (e.g., missing error scenarios, unclear user context), ask before drafting.

**If the ask is vague or conversational:**
Ask targeted questions to establish the minimum context needed to draft. You
need to understand at least:
- What type of UI element or screen is this for?
- What is the user doing or trying to accomplish at this point?
- Are there specific states to cover (success, error, empty, loading)?

Don't over-interview. If you have enough to produce a reasonable first draft,
draft it and let the user react. It's faster to revise than to interrogate.

### Step 2: Pull content standards from Supernova

Before drafting, retrieve the relevant standards from Supernova via MCP.

1. **Always pull foundational standards** — voice and tone, core style rules.
2. **Pull component/pattern-level standards** for each component type you
   identified in Step 1. For example, if the request involves an error alert
   and a form, pull standards for both.
3. If no component-specific standards exist in Supernova for a given component,
   fall back to foundational standards only.

Apply these standards as constraints during drafting — they define the
boundaries for tone, terminology, capitalization, punctuation, and structure.
Don't reference the standards explicitly in your output unless the user asks
you to justify a choice.

### Step 3: Draft the copy

Generate copy mapped to the components identified in Step 1.

**For multi-screen flows or multi-component requests**, use structured markdown:

```markdown
## Screen: [Screen Name]

### [Component Name]
- **Heading:** Copy here
- **Body:** Copy here
- **CTA (primary):** Button label
- **CTA (secondary):** Link or secondary action
- **Helper text:** Instructional copy
- **Error state:** Error message copy
- **Empty state:** Empty state copy
```

If you pulled the component tree from Figma, use the actual design system
component names in place of `[Component Name]`.

Not every element will be needed for every component. Include only the elements
that are relevant to the specific component and context. Don't pad output with
placeholder entries.

**For quick microcopy or single-component asks**, use a compact table:

| Element | Copy | Notes |
|---------|------|-------|
| Heading | Copy here | Context or rationale |
| CTA | Button label | Character count if relevant |
| Error | Error message | Trigger condition |

**Drafting principles:**

- Lead with the user's goal or next action, not the system's state.
- Be specific. "Your payment of $50.00 was received" over "Payment successful."
- Front-load the important information — users scan, they don't read.
- Use the terminology defined in Supernova standards. Don't invent synonyms.
- Match the voice and tone to the moment. An error message during a payment
  flow has different emotional weight than a tooltip on a settings toggle.
- Include the trigger or condition for state-based copy (errors, empty states,
  loading) so developers and designers know when the string appears.
- Consider character constraints for the component. A button label has
  different length limits than a body paragraph. Flag anything that might
  overflow its container.

### Step 4: Provide rationale when useful

For non-obvious choices — why you picked a particular word, why you structured
a message a certain way, why you avoided a term — add brief rationale. This
helps in review and builds shared understanding.

Don't over-explain. If the choice follows directly from the standards or is
self-evident, skip the rationale.

### Step 5: Offer next steps

After delivering the draft, suggest logical next steps based on context:

- **If the copy covers a single screen in a larger flow:** offer to continue
  drafting the next screen.
- **If there are states you didn't cover:** flag them ("I didn't write the
  loading state — want me to add it?").
- **If review would be valuable:** offer to run the output through the
  Review & Critique sub-skill against Supernova standards.
- **If the user provided a Figma link:** note that the copy is ready to be
  mapped back to the frame (manual for now, automated when Figma write
  access is available).

## Edge cases

**Multiple variants or A/B options:** If the user asks for options, provide
2–3 variants with a brief note on the tradeoff for each (e.g., shorter vs.
more descriptive, formal vs. conversational). Don't provide more than 3
unless asked.

**Content the user provides is already close:** If the user shares draft copy
that's nearly there, don't rewrite from scratch. Edit in place and call out
what you changed and why. This respects their work and is more useful than
a from-zero rewrite.

**Healthcare or regulated content:** Flag any copy that might have compliance
implications (e.g., claims language, benefit descriptions, cost disclosures).
Note the concern but don't attempt to write compliant copy without confirmed
requirements — compliance review is a separate process.

**Missing context you can't infer:** If you don't know the user's goal, the
screen's purpose, or the trigger condition, ask. Don't generate generic
placeholder copy — it wastes everyone's time.
