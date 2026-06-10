# Thematic Analysis Workflow

## Overview

This workflow supports staged, rigorous thematic analysis of open-ended survey comments and interview excerpts. It is designed to preserve analytical integrity by enforcing a strict sequence — you cannot generate themes before coding, and you cannot generate insights before validating evidence.

Each stage produces a structured output that feeds the next. No stage is skipped.

---

## Guiding Principles

**Stay close to participant language.**
Codes should reflect what participants said, not what the analyst assumes they meant. Paraphrase minimally. Quote directly when possible.

**Less is more.**
Assign only as many codes as a response genuinely supports. A single code that captures the comment well is better than three codes that fragment it.

**Separate surface from underlying.**
Distinguish what the participant complained about (surface issue) from what they needed or were trying to do (underlying need or behavior).

**Flag ambiguity; do not resolve it prematurely.**
If a comment could support multiple interpretations, note it and mark confidence accordingly. Human review resolves ambiguity — the model does not guess.

**Preserve traceability.**
Every insight must trace back to a broader theme → theme candidates → first-cycle codes → raw comments. IDs connect the chain.

**Confidence ratings are required at every stage.**
Low / Medium / High. When in doubt, go lower.

---

## Stage Sequence

### Stage 1 — First-Cycle Coding (`/first-cycle-coding`)

**Input:** Raw comments or interview excerpts with IDs.

**What happens:** Each response is read closely and assigned codes across five dimensions:
- **Subject Codes** — the main topic(s) or object(s) of the comment, in participant language
- **Pain Point Codes** — friction, confusion, unmet expectations, disappointment
- **Motivation Codes** — goals, desires, what the participant was trying to accomplish
- **Child Codes** — 1–3 concise codes that combine the most important meaning from the subject, pain point, and motivation codes; the bridge between first-cycle coding and theme candidate generation
- **Need/Behavior** — the underlying need, behavior pattern, or decision logic

Sentiment and confidence are assigned per response. Ambiguities are flagged for human review.

**Output:** `outputs/first-cycle-codes.csv`

**Do not:** generate theme candidates or broader themes during this stage.

---

### Stage 2 — Theme Candidate Generation (`/theme-candidate-generation`)

**Input:** `outputs/first-cycle-codes.csv`

**What happens:** Child codes from the first-cycle output are grouped into theme candidates — patterns that appear across multiple responses. Each candidate is grounded in specific child codes and supported by example IDs.

**Output:** `outputs/theme-candidates.csv`

**Do not:** generate broader themes or insights during this stage.

---

### Stage 3 — Broader Theme Generation (`/broader-theme-generation`)

**Input:** `outputs/theme-candidates.csv`

**What happens:** Theme candidates are reviewed for overlap, hierarchy, and relationships. Related candidates are grouped into broader themes with descriptive names and working definitions.

**Output:** `outputs/broader-themes.csv`

**Do not:** write insights or recommendations during this stage.

---

### Stage 4 — Evidence Validation (`/evidence-validation`)

**Input:** `outputs/broader-themes.csv` + `outputs/first-cycle-codes.csv`

**What happens:** Each broader theme is tested against the raw codes and original responses. The analyst checks that:
- Supporting codes genuinely reflect the theme
- Example IDs exist and are correctly attributed
- No theme is supported by only one or two isolated responses (unless genuinely singular)
- Competing or disconfirming evidence is acknowledged

**Output:** `outputs/evidence-validation.csv`

**Do not:** write insights until validation is complete.

---

### Stage 5 — Insight Generation (`/insight-generation`)

**Input:** `outputs/evidence-validation.csv`

**What happens:** Validated themes are synthesized into insights — interpretive statements about what the data means for the product, service, or decision context. Each insight is scoped, evidenced, and includes a recommended action or implication.

**Output:** `outputs/insights.csv`

---

## File Naming Convention

| Stage | Input | Output |
|---|---|---|
| First-cycle coding | raw comments CSV | `outputs/first-cycle-codes.csv` |
| Theme candidates | first-cycle-codes.csv | `outputs/theme-candidates.csv` |
| Broader themes | theme-candidates.csv | `outputs/broader-themes.csv` |
| Evidence validation | broader-themes.csv + first-cycle-codes.csv | `outputs/evidence-validation.csv` |
| Insights | evidence-validation.csv | `outputs/insights.csv` |

---

## Human Review Checkpoints

Review is expected between every stage. The model pauses and surfaces what needs human judgment before the next stage begins. These checkpoints are not optional — they are part of the methodology.

Specifically, human review is required when:
- Confidence is Low on any code or theme
- Ambiguity is flagged and not resolved
- Two codes or theme candidates appear to overlap substantially
- A theme is supported by fewer than three distinct responses
- A motivation or need/behavior was inferred rather than stated

---

## What This Workflow Is Not

- It is not a sentiment analysis tool. Sentiment is one signal, not the output.
- It is not a topic modeler. Codes must be grounded in specific language from specific responses.
- It is not a summary generator. Insights must trace to evidence.
- It does not resolve ambiguity automatically. Ambiguity is flagged and handed to the analyst.
