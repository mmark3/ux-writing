---
name: ux-writing-review
description: >
  Evaluate and critique user-facing copy against organizational content
  standards. Use when someone wants feedback on existing copy, a compliance
  check against voice/tone/style guidelines, a readability review, or
  consistency analysis across screens or flows.
---

# Review & Critique

Evaluate UI copy against content standards and provide actionable, specific
feedback. This sub-skill is a quality gate — it tells the user what's working,
what isn't, and exactly how to fix it.

## Workflow

### Step 1: Gather the copy to review

The user may provide copy in several ways:

**Pasted text or inline copy:**
Take it as-is. Ask what component or screen it belongs to if it's not clear
from context — the component type affects which standards apply.

**A Figma link to screens with existing copy:**
Use the Figma MCP to pull the frame. Extract the copy from the component tree
along with the design system component names. This gives you both the text to
review and the component context to pull the right standards.

**Output from the Drafting sub-skill:**
If the user just ran a drafting workflow and wants a review pass, use the
drafted output directly. You already know the component types.

**A description of the copy location:**
If the user says "review the copy on our login screen" without providing the
actual text, ask them to share it — either paste it, provide a Figma link,
or point you to where it lives.

### Step 2: Pull review criteria from Supernova

Retrieve the standards you'll evaluate against:

1. **Foundational standards** — voice and tone, style rules, terminology.
   Always pull these.
2. **Component/pattern-level standards** — for each component type present in
   the copy being reviewed. These define component-specific expectations
   (e.g., how an error message should be structured, what a button label
   should look like).

If the user asks to review against a specific dimension only (e.g., "just
check the tone"), still pull the full foundational standards but focus your
feedback on the requested dimension.

### Step 3: Evaluate the copy

Assess the copy across these dimensions. Not every dimension will apply to
every review — use judgment about what's relevant to the specific content.

**Voice and tone alignment**
Does the copy match the organizational voice? Is the tone appropriate for the
user's emotional context at this point in the experience? Flag any shifts that
feel inconsistent with the moment (e.g., overly casual in a serious context,
overly formal in a simple interaction).

**Style standards compliance**
Check against the specific rules from Supernova: capitalization conventions,
punctuation patterns, number formatting, terminology usage. These are binary —
copy either follows the rules or it doesn't.

**Clarity and scannability**
Is the copy easy to understand on first read? Is the most important
information front-loaded? Are sentences concise? Flag jargon, passive
constructions, or unnecessary words.

**Component pattern compliance**
Does the copy follow the established pattern for its component type? If
Supernova defines a structure for error messages (e.g., what happened + what
to do), does this copy follow it?

**Consistency**
When reviewing multiple screens or a flow, check for consistency in
terminology, tone, and structure across screens. Flag places where the same
concept is described differently or where tone shifts unexpectedly between
steps.

**Accessibility considerations**
Flag copy that might cause accessibility issues: ambiguous link text
("click here"), reliance on color or position to convey meaning ("the red
text above"), or language complexity that could be simplified.

### Step 4: Deliver feedback

Structure your feedback to be immediately actionable.

**For each issue found:**

1. **Quote the specific copy** that has the issue.
2. **Name the issue** concisely (e.g., "Tone mismatch," "Terminology
   deviation," "Unclear next action").
3. **Explain why** it's an issue — reference the specific standard when
   relevant.
4. **Provide a suggested revision** — don't just flag problems, fix them.

**Example format:**

> **"Click here to view your benefits"**
> *Issue: Ambiguous link text*
> "Click here" doesn't describe the destination and creates accessibility
> issues for screen readers. Per [style standard]: use descriptive link text.
> → Suggested: **"View your benefits summary"**

**Organize feedback by severity:**

- **Must fix** — standards violations, clarity failures, accessibility issues.
  These should be addressed before the copy ships.
- **Should fix** — tone adjustments, minor consistency issues, optimization
  opportunities. Important but not blocking.
- **Consider** — subjective improvements, alternative phrasings, polish.
  Take it or leave it.

**What's working:**
Don't only flag problems. Call out what's effective — especially if the copy
handles a difficult moment well, uses a pattern in a smart way, or is
particularly clear. This helps the team learn what good looks like, not just
what bad looks like.

### Step 5: Summarize and offer next steps

After the detailed feedback, provide a brief summary:

- Overall assessment (how close is this to shippable?)
- Count of issues by severity
- The single highest-impact change

Then offer logical next steps:

- **If there are must-fix issues:** offer to revise the copy by loading the
  Drafting sub-skill and applying the feedback.
- **If the copy is part of a larger flow:** offer to review additional screens.
- **If the review revealed pattern gaps:** note that the component may need
  content standards added in Supernova (flag for the content design lead).

## Edge cases

**Reviewing copy you just drafted:** This is a common pattern (draft → review).
Approach it with fresh eyes — evaluate the drafted copy against the same
standards you would apply to anyone else's work. Don't be easier on your own
output.

**Partial copy:** If the user only shares a few strings without full screen
context, review what you have but note which dimensions you can't fully assess
without more context (e.g., flow consistency requires seeing the full flow).

**No applicable standards in Supernova:** If a component type doesn't have
specific standards in Supernova, evaluate against foundational standards and
general UX writing best practices. Note the gap — it may be worth creating
component-level standards for it.

**User disagrees with a standard:** If the user pushes back on feedback that
comes from a Supernova standard, don't insist. Note the standard and let them
decide. They may have context you don't, or the standard may need updating.
