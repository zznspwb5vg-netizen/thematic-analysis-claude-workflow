# Quality Standards

Standards that apply across all stages of the thematic analysis workflow. Each skill references these. When a standard is violated, the model must flag the issue rather than proceed silently.

---

## General Standards

### Stay in participant language
Use the words and phrases the participant used whenever possible. If paraphrasing is necessary, stay as close to the original as possible. Never substitute analyst vocabulary for participant vocabulary at the coding stage.

**Violation:** Participant says "I couldn't find where to cancel" → code written as "poor navigation discoverability"
**Correct:** code written as "couldn't find where to cancel"

---

### Do not over-code
Assign only as many codes as the comment genuinely supports. A comment with one clear idea gets one code per dimension, not three to be thorough.

**Violation:** A two-sentence comment receives six codes across three dimensions.
**Correct:** A two-sentence comment receives one or two codes that capture what was actually said.

---

### Do not invent motivations
Motivation codes and Need/Behavior entries must be supported by something the participant said or strongly implied. Do not infer motivations from demographics, context, or what "most users probably want."

**Violation:** "Participant likely wanted to save time" when no time-related language appears in the comment.
**Correct:** Flag the absence of motivation language; leave Motivation Code blank or mark as inferred with Low confidence.

**Inferred motivation rule:** A motivation that is strongly grounded in the response but not directly stated may be included — but it must not be presented as certain. Mark Confidence as Medium at highest, and explain the basis for the inference in Ambiguity/Notes. If the inference requires reading between the lines rather than reading the response itself, leave the field blank instead.

---

### Separate surface from underlying
Surface issue: what the participant described as the problem.
Underlying need or behavior: what they were trying to accomplish or the pattern the surface issue reflects.

Coding them separately keeps the analysis honest. Surface issues cluster differently than underlying needs.

---

### Implied pain points
A pain point does not have to be stated directly to be coded. A response that implies friction through contrast or comparison — for example, "I wish the reports section was the same" — can support an implied pain point code.

**Required when coding an implied pain point:**
1. Label it as implied in the code itself: `reports section slow (implied by contrast)`
2. Explain the basis for the inference in Ambiguity/Notes
3. Mark Confidence as Medium at highest — an implied pain point cannot hold a High rating

**Violation:** Coding `reports section slow` without any label or note, as if the participant stated it directly.
**Correct:** Coding `reports section slow (implied by contrast)` with a note: "Pain point inferred from positive comparison — participant did not describe a failed task."

---

### Primary friction vs. behavioral consequence
When a response describes both what went wrong and what the participant did as a result, code them separately.

- **Primary friction** — the event or condition that failed, confused, or blocked the participant. This belongs in Pain Point Codes: `cancellation page stuck loading`, `irrelevant search results`, `upgrade button unresponsive`
- **Behavioral consequence** — what the participant did because of the friction. This is not a pain point: `forced to call support`, `gave up on search`, `abandoned task`

Behavioral consequences are analytically important — they show the impact of the friction — but they belong in Child Codes, Need/Behavior, or Ambiguity/Notes, not as standalone pain point codes. If a consequence is included in Pain Point Codes it must be explicitly labeled as a consequence.

**Violation:** Listing `forced to call support` as a pain point alongside `cancellation page stuck loading` without distinguishing which is the friction and which is the result.
**Correct:** `cancellation page stuck loading` in Pain Point Codes; consequence captured in Child Code (`broken cancellation page forced support escalation`) or Need/Behavior.

---

### Flag ambiguity — do not resolve it
When a comment could reasonably support two different interpretations, record both possibilities in the Ambiguity/Notes field and mark confidence as Low or Medium. Do not pick one interpretation arbitrarily.

The analyst resolves ambiguity. The model surfaces it.

---

### No stage-skipping
Theme candidates are never generated from raw comments directly. Insights are never generated from codes directly. Each stage's output must exist before the next stage begins. The model should refuse to run a later stage if the prior output is not present.

---

## Confidence Ratings

Used at every stage. Applied per row.

| Rating | Meaning |
|---|---|
| High | The evidence clearly supports this code / theme / insight. The participant's meaning is unambiguous. |
| Medium | The evidence supports this code / theme / insight but involves some inference or interpretation that a reasonable analyst might contest. |
| Low | The comment is vague, short, or ambiguous. The code or theme relies heavily on inference. Human review is required before this item advances to the next stage. |

**Rule:** When in doubt, go lower. Medium is not a safe default — use it when the evidence is genuinely mixed, not to avoid committing to Low.

---

## Sentiment Ratings

Used at the first-cycle coding stage. Applied per response.

| Value | Meaning |
|---|---|
| Positive | Comment expresses satisfaction, appreciation, or enthusiasm. |
| Negative | Comment expresses frustration, disappointment, confusion, or unmet expectations. |
| Mixed | Comment contains both positive and negative elements. |
| Neutral | Comment is factual, descriptive, or neither positive nor negative. |

**Note:** Sentiment describes the emotional tone of the comment as expressed, not the severity of the issue or the analyst's judgment of it.

---

## Code Formatting Standards

Codes are written in plain English, lowercase, using spaces — not hyphenated slugs. Stay close to participant language. Avoid abstract or business-level labels.

- **Subject codes** name the main topic, object, or area: `appointment wait`, `search results`, `cancellation page`, `trade-in estimate`
- **Pain point codes** name a friction, failure, or unmet expectation: `long wait before help`, `unclear order status`, `no confirmation sent`, `felt rushed`
- **Motivation codes** name a goal, intent, or expectation: `wanted informed decision`, `wanted efficient visit`, `expected proactive update`, `wanted to compare options`
- **Child codes** combine the most important meaning from subject, pain point, and motivation into 1–3 concise codes. They are the primary unit fed into Stage 2. Child codes should be more specific than a single parent code but not so broad they are already a theme: `appointment wait undermined predictability`, `inventory uncertainty reduced store visit value`, `unclear order status increased customer effort`
- **Need/Behavior entries** are written as a short plain-English sentence: "Customer wants to feel informed before making a purchase decision."

---

## Theme Standards (Stages 2 and 3)

- A theme candidate must be supported by at least three distinct responses, from at least two different participants, unless the finding is genuinely singular and analytically important.
- A broader theme must be supported by at least two theme candidates.
- Theme names should be descriptive but not interpretive — they describe what the data shows, not what the analyst concludes.
- Working definitions (one sentence) are required for every broader theme before evidence validation begins.

---

## Evidence Validation Standards (Stage 4)

- Every broader theme must have at least three example IDs cited.
- Cited IDs must actually exist in `outputs/first-cycle-codes.csv`.
- Disconfirming evidence — responses that complicate or contradict the theme — must be acknowledged if present.
- If a theme collapses under validation (not enough real support), it is removed or merged, not kept and weakened.

---

## Insight Standards (Stage 5)

- Each insight must state: what the data shows, for whom, with what frequency or pattern, and what it implies.
- Insights are interpretive — they go beyond restating what participants said. But they must trace back to validated evidence.
- Recommendations are optional but must follow logically from the insight, not be appended generically.
- Do not generate insights for themes that did not pass evidence validation.

---

## What to Do When Quality Standards Cannot Be Met

| Situation | Required action |
|---|---|
| Comment is too vague to code | Assign no codes; note in Ambiguity/Notes; mark confidence Low |
| Motivation cannot be inferred without guessing | Leave Motivation Code blank; flag in notes |
| Motivation is inferred but strongly grounded | Include it; mark Confidence Medium at highest; explain inference in Ambiguity/Notes |
| Pain point is implied through contrast, not stated | Label it as implied in the code; note in Ambiguity/Notes; mark Confidence Medium at highest |
| Response includes both friction and a behavioral consequence | Code the friction in Pain Point Codes; capture the consequence in Child Codes, Need/Behavior, or Ambiguity/Notes |
| Child code would be identical to a subject or pain point code | Rewrite it to add synthesis — a child code that restates one parent code is not adding value |
| Two codes overlap significantly | Flag the overlap; do not duplicate; let analyst decide |
| Theme has only one or two supporting responses | Flag; do not advance to broader themes without review |
| Validated theme still feels weak | Flag; do not generate an insight from it |

---

## What the Model Must Not Do

- Generate themes directly from raw comments
- Resolve ambiguity without flagging it
- Assign High confidence to vague or short comments
- Assign High confidence when motivation or pain point is inferred rather than stated
- Invent participant motivations
- Present inferred motivations as if they were directly stated
- Treat behavioral consequences as pain points without labeling them as such
- Skip a stage because the prior output looks "good enough"
- Write insights for themes that have not been validated
- Make frequency or "most frequent" claims in end-of-run summaries without verifying counts against the output table
