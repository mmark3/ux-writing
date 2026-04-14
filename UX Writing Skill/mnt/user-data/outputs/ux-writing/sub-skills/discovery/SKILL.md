---
name: ux-writing-discovery
description: >
  Audit and analyze existing UI content to identify gaps, inconsistencies, and
  opportunities. Use when someone wants a content inventory, heuristic review,
  gap analysis, or competitive content analysis before writing or rewriting
  product copy.
---

# Discovery & Audit

Assess the current state of content in a product or flow. This sub-skill helps
you understand what exists, what's missing, and what needs to change before
moving into strategy or drafting.

## Workflow

### Step 1: Define the scope

Clarify what the user wants to audit and how deep to go.

**Scope questions to resolve:**
- What product area, feature, or flow are we looking at?
- Are we auditing everything in that area, or specific aspects (e.g., only
  error messages, only onboarding copy)?
- What's the goal — a full inventory, a quality check, identifying gaps,
  or something else?

If the user provides a Figma link, use the Figma MCP to pull the screens and
establish scope from the component tree. If they describe the area verbally,
work with that.

Don't expand scope beyond what the user asked for. A request to "look at our
error messages" doesn't mean audit the entire flow.

### Step 2: Pull baseline standards from Supernova

Retrieve the content standards that will serve as the evaluation baseline:

1. **Foundational standards** — voice and tone, style rules, terminology.
2. **Component/pattern-level standards** — for each component type present in
   the audit scope. These define what "good" looks like for each component.

These standards become your audit criteria. Content that aligns with them is
compliant; content that deviates is a finding.

### Step 3: Inventory the content

Catalog what exists. The format depends on the audit type.

**Content inventory** — a comprehensive catalog of all content within scope:

| Screen | Component | Element | Current copy | Status |
|--------|-----------|---------|-------------|--------|
| Login | Error alert | Heading | "Something went wrong" | Needs review |
| Login | Error alert | Body | "Please try again later" | Needs review |
| Login | CTA | Primary | "Sign In" | Compliant |

Status values: Compliant, Needs review, Missing, Inconsistent, Outdated.

If working from Figma, populate Screen, Component, and Element from the
component tree. If working from user descriptions or screenshots, build the
inventory from what's available.

**Targeted audit** — when the scope is narrower (e.g., "audit our error
messages"), skip the full inventory and focus on the specific content type
across the relevant screens.

### Step 4: Analyze findings

Evaluate the inventoried content against the Supernova standards. Organize
findings into categories:

**Standards compliance**
Where does existing copy deviate from foundational or component-level
standards? Be specific — reference the standard and the deviation.

**Consistency**
Where does the same concept use different language across screens? Where
does tone shift unexpectedly? Where are patterns used inconsistently?

**Gaps**
What's missing entirely? Common gaps: empty states, error messages for edge
cases, helper text, loading states, accessibility-relevant copy (alt text,
aria labels).

**Quality issues**
Copy that is technically compliant but still problematic: unclear language,
jargon, overly long strings, passive voice where active would be clearer,
missing context for the user.

**What's working**
Identify content that's strong — good patterns worth preserving or extending
to other areas.

### Step 5: Deliver the audit report

Structure the output as a clear, scannable report.

**Summary**
- Scope of what was audited
- Total content items inventoried
- High-level finding counts (compliant, needs review, missing, etc.)
- Top 3 highest-impact issues

**Detailed findings**
Organized by category (compliance, consistency, gaps, quality). For each
finding:
- The specific content and where it lives
- What the issue is
- The applicable standard (if relevant)
- Recommended action

**Content inventory**
The full inventory table from Step 3, included as a reference artifact.

**Recommended next steps**
Based on findings, suggest what to do next:
- If there are strategy-level issues (IA problems, missing content models) →
  suggest the Content Strategy & IA sub-skill.
- If findings are mostly execution-level (copy needs rewriting) → suggest
  the Drafting sub-skill with the audit findings as input.
- If the copy just needs polish → suggest the Review & Critique sub-skill
  for targeted feedback.

## Audit types

### Heuristic review

A quick, expert-judgment evaluation rather than a comprehensive inventory.
Useful for a fast read on content quality without cataloging every string.

Focus on the most impactful dimensions:
- First impressions: is the voice consistent and appropriate?
- Key moments: are errors, confirmations, and calls to action clear?
- Cognitive load: is the user asked to process too much at once?
- Navigation clarity: do labels and headings help the user orient?

Output a prioritized list of observations rather than a full inventory.

### Gap analysis

Focused specifically on what's missing, not what's wrong with what exists.
Walk through the user flow step by step and identify where content is needed
but absent.

Common areas to check: error states for each possible failure, empty/zero-data
states, loading states, confirmation messages, helper text for complex inputs,
edge cases (timeouts, session expiry, permission issues).

### Competitive content analysis

Evaluate how comparable products handle similar content challenges. The user
provides competitors or comparable products to analyze.

Focus on patterns and approaches, not specific copy (don't plagiarize). Note
what works well, what doesn't, and what ideas could be adapted.

## Edge cases

**Large scope with no Figma access:** If the user wants a broad audit but
can only describe screens verbally, structure the inventory around their
descriptions and note that the audit is based on reported content, not a
direct review. Recommend a follow-up with Figma links for accuracy.

**No existing standards in Supernova:** If Supernova doesn't have standards
for the components in scope, evaluate against general UX writing best
practices and flag the standards gap as a finding. Recommend creating
component-level standards.

**User wants to audit a competitor, not their own product:** This is a
competitive content analysis. Don't apply Supernova standards to competitor
content — analyze it on its own merits and as a reference for what works.
