---
name: broader-theme-generation
description: Use this skill for Stage 3 of the thematic analysis workflow. Takes the theme candidate output as input, applies a research question as an analytic lens, and groups related theme candidates into broader themes with working definitions. Does not generate insights, recommendations, or business implications.
---

# Broader Theme Generation Skill

## Purpose

Use this skill to group related theme candidates from Stage 2 into broader themes — the highest level of analytical abstraction before evidence validation.

Broader themes describe patterns at a level that is meaningful for interpretation and action. They are more abstract than theme candidates but must still be grounded in specific evidence. Each broader theme must have a working definition, full traceability back to theme candidates and child codes, and a clear rationale for why the candidates belong together.

This stage does not produce insights or recommendations. Those come after evidence validation in Stage 5.

---

## When to Use This Skill

Use this skill after the analyst has reviewed and approved `outputs/theme-candidates.csv`, including any below-threshold candidates flagged in Stage 2.

Do not use this skill if:
- `outputs/theme-candidates.csv` does not exist
- The analyst has not reviewed the Stage 2 output
- There are unresolved Low-confidence theme candidates from Stage 2 that the analyst has not assessed
- A research question or analytic focus has not been provided

**Trigger phrases:**
- "Generate broader themes"
- "Run broader theme generation"
- "Move to Stage 3"
- "Group the theme candidates"

---

## Research Question Requirement

**A research question or analytic focus is required before this skill runs.**

If the user has not provided one, ask:
> "Please provide the research question or analytic focus that should guide this stage. For example: 'How do users experience friction and self-service breakdown in the product journey?' This will shape how theme candidates are grouped and named."

Do not begin grouping until a research question is received.

### How the research question is used

The research question guides:
- Which relationships between theme candidates are most analytically meaningful
- How broader themes are named and framed
- Which theme candidates are central versus peripheral to the analysis
- How working definitions are written

### What the research question does not do

The research question is an analytic lens, not a justification to force unsupported groupings.

**Rule:** If a theme candidate does not clearly relate to the research question, keep it as peripheral, unresolved, or out of scope rather than forcing it into a broader theme. A theme candidate that is out of scope for the current research question is still a valid finding — it should be documented in the Unresolved / Peripheral section with a note explaining its relationship to the research question.

---

## Core Rules

**Group theme candidates, not child codes.**
The primary grouping unit at this stage is the theme candidate. Child codes and example IDs are carried forward for traceability, but they are not re-analysed at this stage.

**A broader theme requires at least two theme candidates.**
A single theme candidate does not constitute a broader theme. If only one theme candidate exists for a potential grouping, it must be marked Low confidence or moved to the Unresolved / Peripheral section. Exception: document explicitly if a singleton theme candidate has strong methodological justification for standalone status.

**Preserve analytical distinctions from Stage 2.**
If Stage 2 kept two patterns separate as distinct theme candidates, Stage 3 should preserve that distinction within the broader theme. Broader themes can contain sub-patterns; they should not collapse those sub-patterns into a single undifferentiated label.

**Every theme candidate must be accounted for.**
Every theme candidate from the Stage 2 output — including those that were below threshold — must appear in exactly one place in the Stage 3 output: either grouped into a broader theme, or placed in the Unresolved / Peripheral section. Run a coverage check at the end.

**Inherit confidence from Stage 2.**
A broader theme cannot hold a higher confidence rating than its weakest component theme candidate without explicit analyst override and documentation.

**Descriptive names, not interpretive conclusions.**
Broader theme names should describe what the data shows, not what the analyst concludes about its significance. Avoid names that embed recommendations, business judgements, or causal claims that go beyond the evidence.

**Working definitions are required.**
Every broader theme must have a working definition before Stage 4 (evidence validation) begins. The working definition is one sentence that describes what the broader theme covers and what it does not cover.

**Do not generate new codes or candidates.**
Do not create new child codes, new theme candidates, or reinterpret first-cycle codes at this stage. If a gap is noticed, flag it for the analyst rather than filling it by generating new material.

---

## Input Requirements

**Required:** `outputs/theme-candidates.csv`

The file contains two sections that must both be reviewed:

1. **Grouped theme candidates** — the main table with Focused Code / Theme Candidate, Child Codes, Example IDs, Rationale, Confidence, and Ambiguity/Notes
2. **Isolated / Ungrouped child codes from Stage 2** — these did not form theme candidates; they are not theme candidates themselves but should be reviewed to understand what the Stage 2 output could not account for

Read both sections before beginning.

**Do not return to `outputs/first-cycle-codes.csv` or raw responses as the primary input.** Consult them only if a theme candidate or child code is ambiguous and clarification is needed.

---

## Research Question Analysis (before grouping)

Before grouping, complete a brief written analysis of the research question in relation to the available theme candidates. This should take the form of a short mapping:

```
Research question: [state it]

Mapping:
- [Theme candidate name] → [central / peripheral / out of scope] to the research question
  Reason: [one sentence]
- [repeat for each candidate]
```

This mapping makes the analytic lens explicit and auditable. It also identifies candidates that are unlikely to group with others under this research question, so they can be placed in the Unresolved / Peripheral section rather than forced into a broader theme.

---

## Process

### Step 1: State the research question and load the input

Write the research question at the top of your working notes. Keep it visible throughout.

Read all theme candidates from `outputs/theme-candidates.csv`, noting:
- The name of each theme candidate
- Its confidence rating and whether it was below threshold at Stage 2
- Its supporting child codes and example IDs
- Any ambiguity flags from Stage 2

Also note any Stage 2 isolated codes that may be relevant context for the research question.

---

### Step 2: Map each theme candidate to the research question

For each theme candidate, assess its relationship to the research question:
- **Central** — directly addresses the research question
- **Peripheral** — related but not the primary focus of the research question
- **Out of scope** — does not relate to the research question for this analysis

This mapping guides grouping decisions but does not override evidence. A central candidate still needs a genuine conceptual relationship with other central candidates to be grouped with them.

---

### Step 3: Identify relationships between theme candidates

For central and peripheral theme candidates, look for:
- **Overlap** — two candidates describe overlapping patterns that could be one broader theme
- **Hierarchy** — one candidate is a specific instance of a broader pattern described by another
- **Complementarity** — two candidates describe different aspects of the same underlying experience (e.g., a breakdown through two different mechanisms)
- **Contrast** — two candidates describe opposing experiences of the same topic (treat carefully — contrasting candidates usually should not be merged)

The grouping test at this stage: *Can you write a working definition that accurately describes what both theme candidates share, while preserving what makes each distinct?* If not, the grouping is not ready.

---

### Step 4: Form broader themes

Group theme candidates that pass the grouping test. For each broader theme:
- Name it descriptively (see naming rules below)
- Write a one-sentence working definition
- List all contributing theme candidates
- Compile the child codes and example IDs from those candidates
- Write a rationale explaining the relationship between the candidates and why they form a coherent broader theme

**Naming rules:**
- Describe the pattern, not the conclusion or recommendation
- Broader than a theme candidate name, but not so broad it loses meaning
- Avoid vague labels: `customer experience`, `usability issues`, `satisfaction`, `product problems`
- Should make clear what would NOT belong in this theme

**Working definition rules:**
- One sentence only
- Describes what the theme covers
- Implicitly or explicitly distinguishes it from adjacent themes
- Does not contain insights or recommendations

---

### Step 5: Assign confidence

| Rating | Criteria |
|---|---|
| High | Two or more theme candidates, both meeting the 3-response threshold from Stage 2, conceptual relationship is direct and does not require interpretation |
| Medium | At least two theme candidates, but one or more was below threshold at Stage 2, or conceptual relationship requires mild interpretation |
| Low | Based on a single theme candidate; or all contributing candidates were below threshold; or the conceptual relationship requires significant interpretation |

---

### Step 6: Flag ambiguity and difficult groupings

Use the Ambiguity/Notes column to flag:
- Cases where a below-threshold Stage 2 candidate is included in a broader theme
- Cases where two sub-patterns within the same broader theme are analytically distinct and should not be conflated
- Cases where the research question influenced a grouping decision and the connection might not hold under a different research question
- Contrasting evidence from Stage 2 isolated codes that complicates the broader theme

---

### Step 7: Document unresolved and peripheral candidates

Place in the Unresolved / Peripheral section any theme candidate that:
- Could not be grouped with any other candidate
- Is out of scope for the research question
- Was below threshold at Stage 2 and has no clear home in a broader theme
- Produces a broader theme that would be based on a single candidate

For each, provide:
- The theme candidate name as written in Stage 2
- Its child codes and example IDs
- The reason it was not grouped into a broader theme
- A suggested review action for the analyst

---

### Step 8: Note Stage 2 isolated codes as context

After completing the broader theme and unresolved sections, add a brief note on any Stage 2 isolated codes that are relevant to the research question. These are not theme candidates and do not count toward the coverage check — but they may:
- Provide context that strengthens or complicates a broader theme
- Represent singleton findings relevant to the research question
- Indicate directions for future data collection

---

### Step 9: Run the coverage check

Verify that every theme candidate from Stage 2 appears in either a broader theme or the Unresolved / Peripheral section.

```
Coverage Check:
- Total theme candidates reviewed: [N]
- Theme candidates grouped into broader themes: [N]
- Theme candidates left unresolved/peripheral: [N]
- Any theme candidates missing from the output? Yes / No
```

---

## Required Output Format

Produce three sections in order.

**Section 1 — Broader Themes:**

```
Broader Theme | Working Definition | Theme Candidates | Child Codes | Example IDs | Relationship/Rationale | Confidence | Ambiguity/Notes
```

**Section 2 — Unresolved / Peripheral Theme Candidates:**

```
Unresolved / Peripheral Theme Candidate | Child Codes | Example IDs | Reason Not Grouped | Suggested Review
```

**Section 3 — Coverage Check:**

```
Coverage Check:
- Total theme candidates reviewed: [N]
- Theme candidates grouped into broader themes: [N]
- Theme candidates left unresolved/peripheral: [N]
- Any theme candidates missing from the output? Yes / No
```

When saving to file, write to `outputs/broader-themes.csv`. Separate the three sections with a blank row and a clear label row.

---

## Quality Standards

Before finalising, check:

- Did I state the research question and map each theme candidate to it before grouping?
- Did each broader theme receive at least two theme candidates?
- Does every broader theme have a working definition?
- Is the rationale grounded in theme candidates and child codes — not in analyst conclusions that go beyond the evidence?
- Did I preserve analytical distinctions from Stage 2 rather than collapsing sub-patterns?
- Did I inherit and record confidence from Stage 2 sources?
- Did I flag every below-threshold Stage 2 candidate that appears in a broader theme?
- Is every theme candidate accounted for in either the broader themes or the unresolved/peripheral section?
- Did I avoid generating insights, recommendations, or business implications?
- Did I complete the coverage check?

---

## Important Constraints

- Do not generate insights. That is Stage 5.
- Do not write recommendations or business implications.
- Do not return to raw responses or first-cycle codes as the primary input.
- Do not generate new child codes or theme candidates.
- Do not merge theme candidates only because they share positive or negative sentiment.
- Do not force every theme candidate into a broader theme — unresolved is a valid and honest outcome.
- Do not create vague broader theme names such as `customer experience`, `usability issues`, `satisfaction`, or `product problems`.
- Do not allow the research question to override the evidence — it is an analytic lens, not a justification.
- Do not create a broader theme from a single theme candidate without explicit methodological justification.
- Do not collapse sub-patterns from Stage 2 into a single undifferentiated broader theme label.
- Do not drop any theme candidate from the output — every one must appear in a broader theme or the unresolved/peripheral section.

---

## Example

**Research question:** "How do customers experience self-service breakdown in the product journey?"

**Theme candidates available:**
- TC1: self-service paths blocked by functional failures (High, R002, R004, R008)
- TC2: navigation and findability friction increased effort to complete tasks (Medium, R001, R009)

**Research question mapping:**
- TC1 → Central: directly describes self-service breakdown via functional failure
- TC2 → Central: directly describes self-service breakdown via navigation friction

**Grouping test:** Can a working definition cover both?
> "A pattern in which customers were unable to complete product tasks independently — either because a UI mechanism failed or because the route to the feature could not be found — resulting in task abandonment or significantly increased effort."
> ✓ This covers both without collapsing their distinction.

**Output row:**

| Broader Theme | Working Definition | Theme Candidates | Child Codes | Example IDs | Relationship/Rationale | Confidence | Ambiguity/Notes |
|---|---|---|---|---|---|---|---|
| self-service breakdown: customers were blocked from completing tasks independently by broken mechanisms or navigation friction | A pattern in which customers attempted product tasks without assistance but could not complete them — either because a specific UI mechanism failed or because the route to the feature could not be found — resulting in task abandonment, increased effort, or support escalation. | self-service paths blocked by functional failures led to task abandonment or support escalation; navigation and findability friction increased effort to access features or complete tasks | irrelevant search results caused abandonment...; unresponsive upgrade button led to task abandonment; broken cancellation page forced support escalation...; billing navigation failure blocked self-service task; buried features and low intuitiveness increase effort to find functionality | R001, R002, R004, R008, R009 | Both candidates describe the same outcome — self-service failure — through different mechanisms. TC1: UI mechanism reached but did not function. TC2: UI mechanism could not be reached. The sub-patterns are analytically distinct (different remediation paths) but share the same broader failure: the customer could not complete the task independently. | Medium | TC2 was below the 3-response threshold in Stage 2. Grouping with TC1 does not resolve that concern. Analyst should assess whether TC2 should be a distinct sub-theme pending more data, or whether TC1 alone is sufficient as a standalone High-confidence broader theme. |

---

## References

- `docs/thematic-analysis-workflow.md` — full workflow overview and stage sequence
- `docs/quality-standards.md` — confidence ratings, theme standards, working definition requirements
- `outputs/theme-candidates.csv` — required input
- `templates/broader-theme-template.csv` — blank template for manual use
- `outputs/broader-themes.csv` — output file
