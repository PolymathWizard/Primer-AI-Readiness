---
module: SP-7
title: "Automation Prioritization Matrix"
framework: PRIMER
version: 1.0.0
feeds: [SP-10]
consumes: [SP-1, SP-2, SP-3, SP-4, SP-5, SP-6, SP-8]
schema: ../schemas/matrix-placement.schema.json
---

# SP-7 — Automation Prioritization Matrix

**Goal**: Rank the documented process portfolio on a volume-weighted
impact × complexity matrix, producing a defensible automation sequence — with
a readiness gate that no process passes without SP-2 through SP-5 complete.

The queue is set by evidence, not enthusiasm — not by which team is loudest
or which vendor demo was most recent. And the matrix is not the decision:
**matrix position is *potential*; the gate is *permission*.** The gate is the
framework's spine — it exists to prevent enthusiastic automation of a
well-scored, poorly understood process.

## Intake

- Complete SP-2 records for every candidate process
- SP-3 decision-logic registers (ambiguity status)
- SP-4 gating findings status
- SP-5 baseline status
- SP-6 bottleneck impact drivers
- SP-1 volume figures (with evidence classes)
- SP-8 downstream-unblocking analysis where available

## Scoring Model

Full derivation: [../docs/scoring-model.md](../docs/scoring-model.md).
Machine implementation: [../tools/matrix_placement.py](../tools/matrix_placement.py).

**Impact (1–5)** — sub-scores shown, not just the composite:
volume × time-per-run × error cost × downstream unblocking.

**Complexity (1–5)** — sub-scores shown:
decision-rule count, tribal-knowledge density, data fragility, exception
rate, system count.

**Volume weighting** applied and shown explicitly.

## Quadrant Definitions

| Quadrant | Criteria |
|---|---|
| **Automate Now** | impact ≥ 4, complexity ≤ 2 |
| **Design Carefully** | impact ≥ 4, complexity ≥ 3 |
| **Quick Wins If Idle** | impact ≤ 3, complexity ≤ 2 |
| **Leave Alone** | impact ≤ 3, complexity ≥ 3 |

## The Readiness Gate

A process may score "Automate Now" and still fail the gate. All four
criteria, no exceptions:

1. **SOP record complete** (SP-2, all twelve sections)
2. **Decision logic externalized with zero unresolved ambiguities** (SP-3)
3. **No open gating data findings** (SP-4)
4. **Baseline captured** (SP-5 — measured, or instrumented with a dated plan)

Full gate specification: [../docs/readiness-gate.md](../docs/readiness-gate.md).

## Output Contract — Prioritization Matrix Package

### 1. Scoring Worksheets

Per process: every impact and complexity sub-score with its evidence class
and the register row it traces to.

### 2. The Matrix

| Process | Impact | Complexity | Volume Weight | Quadrant | Gate Passed? | Class |
|---|---|---|---|---|---|---|

Conforms to [matrix-placement.schema.json](../schemas/matrix-placement.schema.json).
A matrix built on STATED volume claims ships **flagged as provisional**, with
the instrumentation plan attached.

### 3. Sequence Recommendation

The ordered queue with rationale, including the recommended pilot and its
success gate (from SP-5).

### 4. Rejection Log

Processes explicitly **not** recommended for automation and why. The log is
what makes the queue defensible — no assessment ships without one.

### 5. Evidence Classification Summary

Every score traceable to classified evidence in the engagement's evidence
register.

## The Prompt

> You are building the automation prioritization matrix for the documented
> portfolio. Score impact and complexity per process, showing every
> sub-score with its evidence class and source row. Apply volume weighting
> explicitly. Place each process in its quadrant, then apply the readiness
> gate separately — a quadrant is potential, the gate is permission, and you
> will report both. Produce the ordered sequence with the recommended pilot
> and its success gate. Write the rejection log: every process not
> recommended, with reasons. If any score rests on unpromoted STATED volume,
> flag the entire matrix as provisional and attach the instrumentation plan.

## Quality Bar

- No composite score without visible sub-scores.
- No gate pass with an unresolved SP-3 ambiguity, open SP-4 gating finding,
  or missing SP-5 baseline.
- The rejection log is present and reasoned.
- Provisional status declared, never discovered.

## Feeds

- **SP-10** — the gated sequence becomes the roadmap's phase structure.
