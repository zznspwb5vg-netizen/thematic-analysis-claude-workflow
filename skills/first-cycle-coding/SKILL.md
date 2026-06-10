---
name: first-cycle-coding
description: Use this skill for first-cycle qualitative coding of open-ended survey comments, interview excerpts, or customer feedback. This skill codes each response individually, stays close to participant language, separates surface issues from underlying needs/behaviors, and avoids jumping directly to themes.
---

# First-Cycle Coding Skill

## Purpose

Use this skill to conduct first-cycle qualitative coding on open-ended responses.

The goal is to create grounded, traceable child codes that preserve the participant/customer's language and meaning. This skill should not generate broader themes. Broader grouping happens later during theme candidate generation and broader theme generation.

---

## When to Use This Skill

Use this skill when the input is raw qualitative data, such as:

- Open-ended survey comments
- Interview excerpts
- Usability test notes
- Customer feedback
- Support comments
- App store reviews
- Retail/customer experience verbatims

---

## Core Rule

Do not jump directly from raw comments to themes.

The only goal of this stage is to code each response individually and produce grounded first-cycle codes.

---

## Coding Procedure

### Step 1: Read each response individually

Read one response at a time. Do not infer patterns across the full dataset yet.

Assign only as many codes as necessary. Follow a "less is more" rule while still capturing the meaning of the response.

Most responses should receive 1–3 child codes. Use more only when the response clearly contains multiple distinct ideas.

---

### Step 2: Create Subject Codes

Create codes that capture the main subject(s), object(s), or topic(s) in the response.

Subject codes should stay close to the participant/customer's language.

Examples:
- appointment wait
- trade-in estimate
- product comparison
- store noise
- pickup process
- staff explanation
- unavailable fabric

Do not convert subject codes into broader themes.

---

### Step 3: Create Pain Point Codes

Create codes that capture any friction, barrier, confusion, disappointment, or unmet expectation expressed in the response.

Examples:
- long wait before help
- unclear order status
- inventory uncertainty
- felt rushed
- insufficient explanation
- difficult wayfinding
- no proactive update

Do not create a pain point code if no pain point is expressed.

**Implied pain points:** A pain point does not have to be stated directly to be coded. If the response implies friction through contrast or comparison — for example, "I wish the reports section was the same" — it is acceptable to code an implied pain point. When doing so: label it clearly as implied (e.g., `reports section slow (implied by contrast)`), explain the basis in Ambiguity/Notes, and mark Confidence as Medium at highest.

**Primary friction vs. behavioral consequence:** Separate what went wrong from what the participant/customer did because of it.

- **Primary friction** — the thing that failed, confused, or blocked the participant: `cancellation page stuck loading`, `irrelevant search results`, `upgrade button unresponsive`
- **Behavioral consequence** — what the participant did as a result: `forced to call support`, `gave up on search`, `abandoned task`

Primary friction belongs in Pain Point Codes. Behavioral consequences are not the same as pain points. They can be captured in Child Codes, Need/Behavior, or Ambiguity/Notes. If a behavioral consequence is included in Pain Point Codes, it must be explicitly labeled as a consequence rather than treated as the primary friction.

---

### Step 4: Create Motivation Codes

Create codes that capture the participant/customer's motivation, goal, expectation, or reason for behavior.

Examples:
- wanted informed decision
- wanted efficient visit
- wanted confidence before purchase
- expected proactive communication
- wanted pressure-free guidance
- wanted to compare options
- wanted issue resolved quickly

Do not invent a motivation if it is not supported by the comment. If the motivation is unclear, leave this blank or flag it in Ambiguity/Notes.

**Inferred motivation rule:** If a motivation is strongly grounded in the response but not directly stated, it may be included — but it must not be presented as certain. Mark Confidence as Medium at highest, and explain the inference in Ambiguity/Notes. If the inference feels like a stretch, leave the field blank instead.

---

### Step 5: Create Child Codes

Create 1–3 concise child codes that combine the most important meaning from the subject, pain point, and motivation codes.

Child codes should be specific enough to be useful later but not so broad that they become themes.

**Good child code examples:**
- appointment wait undermined predictability
- pressure-free guidance supported purchase confidence
- inventory uncertainty reduced value of store visit
- unclear order status increased customer effort
- staff disengagement reduced service quality

**Weak child code examples:**
- bad experience
- customer service
- satisfaction
- operational issue
- positive feedback

---

### Step 6: Identify Need/Behavior

Write a short statement describing the underlying need, behavior, expectation, or decision pattern.

Examples:
- Customer wants to feel informed before making a purchase decision.
- Customer expects the store visit to be efficient after scheduling an appointment.
- Customer wants proactive updates when fulfillment is delayed.
- Customer relies on staff guidance to reduce uncertainty.
- Customer expects in-store inventory to make the visit worthwhile.

---

### Step 7: Assign Sentiment

Assign one sentiment label:

- Positive
- Mixed
- Negative
- Neutral

Use Mixed when the response includes both positive and negative elements.

---

### Step 8: Assign Confidence

Assign one confidence label:

- **High:** The meaning is clear and the codes are strongly supported by the response.
- **Medium:** The coding is mostly supported, but the response could use human review.
- **Low:** The response is vague, ambiguous, incomplete, or requires human interpretation.

Human review is always allowed, even for High confidence rows.

---

### Step 9: Flag Ambiguity

Use Ambiguity/Notes to flag:

- unclear meaning
- multiple possible interpretations
- missing context
- vague emotional language
- uncertain motivation
- possible mismatch between surface issue and underlying need

Do not guess when meaning is ambiguous.

---

## Required Output Format

Return the output as a table with these columns:

```
ID | Response | Subject Codes | Pain Point Codes | Motivation Codes | Child Codes | Need/Behavior | Sentiment | Confidence | Ambiguity/Notes
```

When saving to file, write to `outputs/first-cycle-codes.csv`.

---

## Quality Standards

Before finalizing, check:

- Did I code each response individually?
- Did I avoid jumping to themes?
- Did I stay close to participant/customer language?
- Did I separate subject, pain point, and motivation?
- Did I avoid over-coding?
- Did I flag ambiguity instead of guessing?
- Did I include confidence ratings?
- Is every child code traceable to the original response?
- Did I distinguish direct evidence from inferred interpretation?
- Did I label implied pain points clearly?
- Did I separate primary friction from behavioral consequence?
- Did I avoid unsupported frequency claims in the summary?

---

## Important Constraints

- Do not create broader themes in this skill.
- Do not summarize the dataset.
- Do not calculate prevalence.
- Do not create insights.
- Do not force pain point or motivation codes when they are not present.
- Do not invent unstated motivations.
- Do not overwrite participant language with vague business language.
- Do not treat a single comment as evidence of a broader theme.
- Do not make frequency or "most frequent" claims in the end-of-run summary unless counts have been verified against the output table. If exact counting is uncertain, use qualitative language ("several responses mentioned…") and note it is approximate.

---

## Example

**Input:**

```
ID: 2
Response: I had to wait over 20 minutes on the shop floor before anyone came to help me. Once I was being served it was great, but the initial wait was frustrating.
```

**Output:**

| Field | Value |
|---|---|
| ID | 2 |
| Response | I had to wait over 20 minutes on the shop floor before anyone came to help me. Once I was being served it was great, but the initial wait was frustrating. |
| Subject Codes | shop floor wait; staff help |
| Pain Point Codes | long wait before help; initial wait frustration |
| Motivation Codes | wanted timely assistance; expected efficient service |
| Child Codes | initial wait undermined service experience; staff help partially recovered experience |
| Need/Behavior | Customer wants an efficient and predictable support experience, especially before receiving staff help. |
| Sentiment | Mixed |
| Confidence | High |
| Ambiguity/Notes | Positive service after the wait should be preserved separately from the initial wait frustration. |

---

## References

- `docs/thematic-analysis-workflow.md` — full workflow overview and stage sequence
- `docs/quality-standards.md` — confidence ratings, sentiment definitions, code standards
- `templates/first-cycle-coding-template.csv` — blank template for manual coding
- `sample-data/sample-comments.csv` — sample input for practice runs
