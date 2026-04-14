# UX Writing Process Overview

This document maps the full UX writing process and how the sub-skills relate
to each other. Use it to understand where a task falls in the process and
what upstream/downstream dependencies exist.

## Process phases

### 1. Discovery & Audit
**Purpose:** Understand what exists and where the gaps are.

Typical activities:
- Content inventory of existing screens or flows
- Heuristic review against usability and content standards
- Gap analysis (what's missing, inconsistent, or outdated)
- Competitive content analysis
- Stakeholder and user research synthesis (content-focused)

**Inputs:** Figma links to existing screens, product documentation, user
research findings, analytics data, or a general description of the product area.

**Outputs:** Audit report, gap analysis, findings summary, recommended next
steps. Feeds into the Strategy phase.

### 2. Content Strategy & IA
**Purpose:** Plan the content structure and approach before writing.

Typical activities:
- Information architecture definition (navigation, hierarchy, labeling)
- Content modeling (what content types exist, their relationships)
- User flow mapping with content requirements at each step
- Content requirements documentation
- Terminology and naming conventions

**Inputs:** Discovery findings, product requirements, user flows, site maps,
or a description of the problem space.

**Outputs:** Content strategy documentation, IA recommendations, flow maps
with content annotations, content requirements. Feeds into the Drafting phase.

### 3. Drafting
**Purpose:** Write the actual user-facing copy.

Typical activities:
- Screen-level copy for full flows (onboarding, checkout, enrollment, etc.)
- Component-level microcopy (buttons, labels, tooltips, helper text)
- Error messages and validation copy
- Empty states and zero-data states
- Notification and alert copy
- Onboarding and instructional copy

**Inputs:** Figma links, plain text briefs, ticket/story descriptions, content
requirements from Strategy phase, or a conversational description of the need.

**Outputs:** Structured markdown (multi-screen flows) or compact tables
(single-component asks) with copy mapped to components. Feeds into the Review
phase.

### 4. Review & Critique
**Purpose:** Evaluate copy against standards and provide actionable feedback.

Typical activities:
- Voice and tone compliance check
- Style standards review (capitalization, punctuation, terminology)
- Readability and clarity assessment
- Consistency review across a flow or product area
- Accessibility review (plain language, screen reader considerations)
- Pattern compliance (does copy follow established component patterns)

**Inputs:** Drafted copy (from the Drafting phase or provided by the user),
existing copy to evaluate, Figma links to implemented screens.

**Outputs:** Annotated feedback with specific recommendations, compliance
scorecard, revised copy suggestions.

## Phase dependencies

```
Discovery → Strategy → Drafting → Review
    ↑                                 |
    └─────────── (iterate) ───────────┘
```

Most users won't go through all four phases in a single session. The most
common patterns are:

- **Drafting only** — "Write me an error message for X" (single sub-skill)
- **Drafting → Review** — "Write copy for this screen, then check it against
  our standards" (two sub-skills in sequence)
- **Full process** — New feature or product area requiring discovery through
  review (all four, usually across multiple sessions)
- **Review only** — "Check this copy I already wrote" (single sub-skill)
