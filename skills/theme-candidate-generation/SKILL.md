---
name: theme-candidate-generation
description: Use this skill for Stage 2 of the thematic analysis workflow. Takes the first-cycle coding output as input and groups related child codes into focused theme candidates. Does not generate broader themes or insights. Each theme candidate must be traceable to specific child codes and source IDs.
---

# Theme Candidate Generation Skill

## Purpose

Use this skill to group related child codes from the first-cycle output into focused theme candidates — provisional patterns that appear across multiple responses.

Theme candidates are more abstract than child codes, but they are not final themes. They describe a recurring pattern in participant experience that is grounded in specific evidence. They exist to make Stage 3 (broader theme generation) possible without skipping the analytical step of identifying and evaluating the patterns first.

---

## When to Use This Skill

Use this skill after first-cycle coding is complete and the analyst has reviewed and approved `outputs/first-cycle-codes.csv`.

Do not use this skill if:
- `outputs/first-cycle-codes.csv` does not exist
- The analyst has not reviewed the first-cycle output
- There are unresolved Low-confidence rows that the analyst has not yet assessed

**Trigger phrases:**
- "Generate theme candidates"
- "Run theme candidate generation"
- "Move to Stage 2"
- "Group the child codes"

---

## Core Rules

**Group only on conceptual relationship, not sentiment or surface similarity.**
Two child codes belong in the same theme candidate only if they describe the same underlying pattern in participant experience. Shared negative sentiment is not a reason to group. Vague topical similarity is not a reason to group.

**The grouping test:** Can you write one sentence that accurately describes what all child codes in this group share — using participant-grounded language, not analyst conclusions? If not, the grouping is not ready.

**Preserve traceability.**
Every theme candidate must list its supporting child codes and the source IDs those codes came from. The chain is: theme candidate → child codes → source IDs → raw responses.

**Apply the minimum support threshold.**
A theme candidate should be supported by at least three distinct responses. Candidates supported by only one or two responses must be flagged for human review and cannot advance to Stage 3 without analyst approval.

**Inherit source confidence.**
If the child codes feeding a candidate came from Medium- or Low-confidence first-cycle rows, that uncertainty carries forward. A theme candidate cannot hold a confidence rating higher than its weakest supporting source without explicit analyst override.

**Document what does not group.**
Isolated child codes — those that do not share a clear pattern with any other code — should be listed separately at the end of the output. They are not discarded; they may become singleton findings, or they may gain more support in a larger dataset.

**Every child code must be accounted for.**
After grouping, every child code from the first-cycle output must appear in exactly one place: either grouped under a theme candidate, or listed in the Isolated / Ungrouped section. No child code may be silently dropped. Run a coverage check at the end to verify the counts add up.

**Child Codes are the primary grouping unit.**
Group on child codes. Subject codes, pain point codes, motivation codes, and need/behavior statements are supporting context — consult them to clarify what a child code means, but do not use them as the basis for grouping decisions.

**Do not create a theme candidate from a single child code.**
A theme candidate requires at least two child codes from different source responses. A child code that stands alone belongs in the Isolated / Ungrouped section. Exception: if there is a strong methodological reason to treat a singleton as a standalone finding, document the justification explicitly.

**Do not reinterpret the raw response unless clarification is needed.**
Work from the child codes as written. Consult the raw response only when a child code is ambiguous or when you need to decide whether two child codes describe the same pattern.

---

## Input Requirements

**Required:** `outputs/first-cycle-codes.csv`

Read the full file before beginning. Pay attention to:
- The **Child Codes** column — this is the primary grouping unit
- The **Confidence** column — Low or Medium confidence rows carry forward to candidates
- The **Ambiguity/Notes** column — unresolved ambiguity affects whether a child code can anchor a candidate
- The **Need/Behavior** column — useful for cross-checking whether two child codes represent the same underlying need

Do not use raw responses as the primary input. Consult them only to clarify meaning when a child code is ambiguous.

---

## Process

### Step 1: Extract and list all child codes

Pull every child code from the first-cycle output. Index each one with its source ID and the confidence rating of that row.

Format: `[ID] [Confidence] child code`

Example:
```
[R002] [High] irrelevant search results caused abandonment of self-service and escalation to support
[R004] [High] unresponsive upgrade button led to task abandonment
[R008] [High] broken cancellation page forced support escalation after repeated self-service failure
```

Do not reorganise or relabel child codes at this step. Copy them as written.

Count the total number of child codes extracted. This becomes the denominator for the coverage check at the end. If a response has more than one child code, list each as a separate entry — every one must be accounted for.

---

### Step 2: Identify potential groupings

Read through the full list of child codes. Look for pairs or clusters where the codes describe the same underlying pattern in participant experience.

**Valid grouping criteria:**
- The codes describe the same type of friction, barrier, or experience
- The codes describe the same underlying need or behavioral pattern
- A single participant-grounded sentence can describe what they share

**Invalid grouping criteria:**
- Shared sentiment alone (all negative, all positive)
- Shared surface topic without shared meaning (both mention "onboarding" but describe opposite experiences)
- Vague conceptual proximity ("these both seem to be about the product being hard to use")

For each potential grouping, write a draft description of the shared pattern before committing to the group. If you cannot write a clear, falsifiable description of what belongs in the group and what does not, the grouping is not ready.

---

### Step 3: Evaluate each grouping

Before formalising a theme candidate, check:

1. **Minimum support:** Does the grouping have at least 3 distinct source IDs? If not, flag it as below threshold.
2. **Conceptual coherence:** Do all child codes in the group describe the same pattern, or does one code feel forced?
3. **Source confidence:** Are the source rows High, Medium, or Low confidence? Record the lowest confidence level present.
4. **Overlap:** Does this grouping substantially overlap with another? If so, flag the overlap and do not duplicate.

Reject a grouping if:
- The shared connection only holds at a very high level of abstraction (e.g., "things that went wrong")
- One code dominates the grouping and the others are peripheral fits
- The grouping requires resolving an ambiguity that was flagged in the first-cycle output

---

### Step 4: Name each theme candidate

Write a short descriptive name for each theme candidate. The name should:
- Describe the pattern, not the conclusion
- Be more abstract than the child codes it contains, but not as broad as a final theme
- Be falsifiable — a good name makes it clear what would NOT belong in this candidate
- Use participant-grounded language where possible

**Good names:**
- `self-service paths blocked by functional failures led to task abandonment or escalation`
- `navigation and findability friction increased effort to access features`
- `unexplained system failures created uncertainty about system state`

**Weak names:**
- `usability problems` (too broad — what would not belong?)
- `negative experiences with the product` (sentiment, not pattern)
- `things customers struggled with` (describes no specific pattern)

---

### Step 5: Write the rationale

For each theme candidate, write a short rationale (3–6 sentences) explaining:
- What the child codes have in common
- Why they belong together rather than separately
- How this candidate is distinct from adjacent candidates
- What makes this pattern analytically meaningful

The rationale must be grounded in the child codes and source responses. Do not write rationale that goes beyond what the evidence supports.

---

### Step 6: Assign confidence

Apply one confidence rating to each theme candidate.

| Rating | Criteria |
|---|---|
| High | 3+ source IDs; all or mostly High confidence source rows; conceptual connection is direct and does not require interpretation |
| Medium | 2–3 source IDs; some Medium confidence source rows; or conceptual connection requires mild interpretation that a reasonable analyst might contest |
| Low | Below the 3-source threshold; or conceptual connection requires significant interpretation; or source rows include Low confidence entries |

A candidate rated High must not include any source rows rated Low from the first-cycle output without an explicit analyst note.

---

### Step 7: Flag ambiguity and uncertain groupings

Use the Ambiguity/Notes column to flag:
- Groupings below the 3-response threshold
- Cases where one code feels like a partial fit
- Cases where two candidates could legitimately be merged or split
- Isolated responses that might extend a thin candidate with more data
- Contrast cases (e.g., two responses describing opposite experiences of the same topic)

Do not advance flagged candidates to Stage 3 without analyst review.

---

### Step 8: Document isolated child codes and run the coverage check

List every child code that did not fit into any theme candidate. For each, provide all four fields:

- **Isolated / Ungrouped Child Code** — copy the child code exactly as written; do not rewrite it
- **Example IDs** — the source ID(s) for that child code
- **Reason Not Grouped** — why it was not placed in a theme candidate (e.g., single response with no conceptual match; ambiguity unresolved from first-cycle output; contrasts with another response on the same topic)
- **Suggested Review** — a specific action for the analyst (e.g., "Consider as singleton finding if analytically important"; "Check whether future data extends this"; "Resolve first-cycle ambiguity before deciding")

Isolated codes are not failures — they are honest findings. Some may become singleton findings in Stage 3; others may indicate gaps worth investigating in future data collection.

After completing this step, run the coverage check:

```
Coverage Check:
- Total Child Codes reviewed: [N]
- Child Codes grouped into theme candidates: [N]
- Child Codes left isolated/ungrouped: [N]
- Any Child Codes missing from the output? Yes / No
```

The grouped count plus the isolated count must equal the total. If they do not match, identify the missing code before proceeding.

---

## Required Output Format

Produce three sections in order.

**Section 1 — Theme Candidates:**

```
Focused Code / Theme Candidate | Child Codes | Example IDs | Rationale | Confidence | Ambiguity/Notes
```

**Section 2 — Isolated / Ungrouped Child Codes:**

```
Isolated / Ungrouped Child Codes | Example IDs | Reason Not Grouped | Suggested Review
```

Every child code from the first-cycle input must appear in exactly one of these two sections.

**Section 3 — Coverage Check:**

```
Coverage Check:
- Total Child Codes reviewed: [N]
- Child Codes grouped into theme candidates: [N]
- Child Codes left isolated/ungrouped: [N]
- Any Child Codes missing from the output? Yes / No
```

When saving to file, write to `outputs/theme-candidates.csv`. Separate the three sections with a blank row and a clear label row.

---

## Quality Standards

Before finalising, check:

- Did I group on conceptual relationship, not sentiment or surface similarity?
- Can I write a single participant-grounded sentence describing what each group shares?
- Does every candidate list its supporting child codes and source IDs?
- Did I flag candidates below the 3-response threshold?
- Did I inherit and record source confidence levels?
- Did I document isolated codes rather than discarding them?
- Did I avoid resolving ambiguities that were flagged in the first-cycle output?
- Did I avoid generating broader themes or insights?
- Does every child code from the first-cycle input appear in either a theme candidate or the isolated section?
- Did I use child codes — not subject, pain point, or motivation codes — as the primary grouping unit?
- Did I avoid creating a theme candidate from a single child code?
- Did I complete the coverage check and verify the counts add up to the total?

---

## Important Constraints

- Do not generate broader themes. That is Stage 3.
- Do not generate insights. That is Stage 5.
- Do not group child codes on the basis of sentiment alone.
- Do not force a code into a group because it is "close enough."
- Do not advance below-threshold candidates without analyst review.
- Do not relabel or rewrite child codes when grouping them — copy them as written.
- Do not discard isolated codes. Document them in the Isolated / Ungrouped section.
- Do not resolve ambiguities that were flagged in the first-cycle output.
- Do not drop any child code from the output — every one must appear in either a theme candidate or the isolated section.
- Do not use subject codes, pain point codes, motivation codes, or need/behavior statements as the primary basis for grouping. Child codes are the grouping unit; the others are supporting context.
- Do not create a theme candidate from a single child code without explicit methodological justification documented in the Ambiguity/Notes field.
- Do not reinterpret the raw response from scratch. Work from child codes; consult the raw response only when a child code is ambiguous.

---

## Example

**Input (excerpt from `outputs/first-cycle-codes.csv`):**

| ID | Child Codes | Confidence |
|---|---|---|
| R002 | irrelevant search results caused abandonment of self-service and escalation to support | High |
| R004 | unresponsive upgrade button led to task abandonment | High |
| R008 | broken cancellation page forced support escalation after repeated self-service failure | High |

**Step 1 output (indexed list):**
```
[R002] [High] irrelevant search results caused abandonment of self-service and escalation to support
[R004] [High] unresponsive upgrade button led to task abandonment
[R008] [High] broken cancellation page forced support escalation after repeated self-service failure
```

**Step 2 — draft grouping description:**
*"All three describe a specific self-service task that failed because a specific UI mechanism did not work. In each case, the customer persisted before giving up or escalating. Pattern: clear intent + broken mechanism → task abandoned or escalated."*

**Step 3 — evaluation:**
- Minimum support: 3 source IDs ✓
- Conceptual coherence: all three match the pattern directly ✓
- Source confidence: all High ✓
- Overlap: distinct from navigation friction (different mechanism) ✓

**Output row:**

| Focused Code / Theme Candidate | Child Codes | Example IDs | Rationale | Confidence | Ambiguity/Notes |
|---|---|---|---|---|---|
| self-service paths blocked by functional failures led to task abandonment or support escalation | irrelevant search results caused abandonment of self-service and escalation to support; unresponsive upgrade button led to task abandonment; broken cancellation page forced support escalation after repeated self-service failure | R002, R004, R008 | All three describe a self-service task (search, upgrade, cancel) that failed because a specific UI mechanism did not work. Each customer persisted before giving up or escalating. The shared pattern is: clear intent + broken mechanism → abandonment or escalation. This is distinct from navigation friction, where the mechanism may work but cannot be reached. | High | R007 (non-functional mobile buttons) may be adjacent — functional failure blocking use — but no behavioral consequence described. Analyst should assess whether R007 extends this candidate. |

---

## References

- `docs/thematic-analysis-workflow.md` — full workflow overview and stage sequence
- `docs/quality-standards.md` — confidence ratings, theme standards, grouping rules
- `outputs/first-cycle-codes.csv` — required input
- `templates/theme-candidate-template.csv` — blank template for manual use
- `outputs/theme-candidates.csv` — output file
