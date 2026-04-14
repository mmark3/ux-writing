---
name: ux-writing-strategy
description: >
  Plan content structure and information architecture before writing. Use when
  someone needs to define content hierarchy, map user flows with content
  requirements, establish terminology, model content types, or plan the
  content approach for a new feature or product area.
---

# Content Strategy & IA

Define the content structure, hierarchy, and approach before any copy gets
written. This sub-skill bridges the gap between discovery findings (or a new
product brief) and the actual drafting work.

## Workflow

### Step 1: Understand the scope and inputs

Determine what the user is planning for and what inputs are available.

**Common starting points:**
- **Audit findings** from the Discovery sub-skill — the user has identified
  gaps or issues and needs a plan to address them.
- **A new feature or product brief** — no existing content; the user needs to
  plan content from scratch.
- **A Figma link to wireframes or early designs** — screens exist but have no
  copy yet. Use Figma MCP to pull the structure and understand the layout and
  component hierarchy.
- **A user flow or journey map** — the user has the experience mapped and
  needs content defined at each step.
- **A vague "we need content for this"** — the user knows the area but hasn't
  defined the content approach yet.

Clarify what decisions need to be made. Strategy work can mean very different
things depending on the situation. Common needs include:

- What content goes on which screens (content allocation)
- How content is organized and labeled (IA and navigation)
- What content types are needed and how they relate (content modeling)
- What terminology to use and where (naming and vocabulary)
- What the content requirements are at each step in a flow

### Step 2: Pull relevant context from Supernova

Retrieve standards and patterns that will inform the strategy:

1. **Foundational standards** — voice and tone context, existing terminology
   conventions.
2. **Component/pattern-level standards** — if you already know which components
   are in play (e.g., from Figma wireframes), pull their content standards to
   understand what each component needs.
3. **Existing content models or pattern libraries** — if Supernova has
   documented content types or patterns for similar product areas, pull those
   as reference.

Don't treat this as a full standards retrieval — pull what's needed to make
informed structural decisions.

### Step 3: Define the content approach

Based on inputs and context, produce the strategy artifacts the user needs.
Not every project requires all of these — match the output to the complexity
of the problem.

#### Content requirements map

For flow-based work, map content requirements to each step in the user
journey:

```markdown
## Flow: [Flow Name]

### Step 1: [Step Name]
**User goal:** What the user is trying to do at this point
**Screen/page:** Where this happens (Figma link or description)
**Content needed:**
- Heading: orient the user to this step
- Body: explain what they need to do and why
- Form labels and helper text: [list specific fields]
- CTA: advance to next step
- Error states: [list possible failures]
- Empty state: [if applicable]
**Tone:** [tone appropriate for this moment in the journey]
**Notes:** [constraints, compliance considerations, dependencies]

### Step 2: [Step Name]
...
```

#### Information architecture recommendations

For IA work, define structure and labeling:

- **Navigation labels** — what things are called and where they sit in the
  hierarchy.
- **Content hierarchy** — what's primary, secondary, and tertiary on each
  screen.
- **Grouping logic** — why content is organized the way it is (task-based,
  topic-based, audience-based).
- **Label rationale** — why specific terms were chosen, especially where
  there were competing options.

#### Terminology decisions

When naming or vocabulary is part of the scope:

| Concept | Recommended term | Avoid | Rationale |
|---------|-----------------|-------|-----------|
| The person using the product | Member | User, Customer | Aligns with brand voice; "member" implies belonging |

Cross-reference Supernova terminology standards. If your recommendations
conflict with existing standards, flag it and recommend whether the standard
should be updated.

#### Content model

For complex product areas, define what content types exist and how they
relate:

- **Content type** — what it is (e.g., benefit summary, plan comparison,
  notification).
- **Purpose** — what job it does for the user.
- **Components** — what design system components render it.
- **Required elements** — what must always be present.
- **Optional elements** — what appears conditionally.
- **Relationships** — how it connects to other content types.

### Step 4: Connect strategy to execution

Strategy artifacts are only useful if they lead to action. End with clear
connections to next steps:

- **If the next step is drafting:** explicitly note which sections of the
  strategy the Drafting sub-skill should use as input. The content
  requirements map is the primary handoff artifact.
- **If the strategy reveals Supernova gaps:** flag components or patterns
  that need content standards created or updated.
- **If the strategy needs stakeholder review:** call that out — some
  decisions (terminology, IA changes) may need buy-in before drafting
  begins.

## Edge cases

**User wants strategy but the product isn't designed yet:** Work at a higher
level — define content requirements and principles rather than screen-level
specs. The strategy becomes input to design, not a layer on top of it.

**User wants IA recommendations but can't change the navigation:** Clarify
constraints upfront. If IA changes aren't on the table, focus on optimizing
content within the existing structure — labeling, hierarchy within screens,
content prioritization.

**Overlap with product or UX strategy:** Content strategy touches adjacent
disciplines. Stay in your lane — focus on the content layer (what words go
where, how content is structured and labeled) rather than feature scoping,
interaction design, or business requirements. Note dependencies on those
disciplines when relevant.

**Existing strategy docs the user wants to build on:** If the user provides
previous strategy work, build on it rather than starting fresh. Note what
you're preserving, what you're extending, and what you're recommending
changes to.
