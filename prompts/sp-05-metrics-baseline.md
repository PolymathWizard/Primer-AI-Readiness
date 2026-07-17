---
module: SP-5
title: "Metrics Architecture & Baseline Capture"
framework: PRIMER
version: 1.0.0
feeds: [SP-7, SP-10]
consumes: [SP-2]
schema: null
pairs_with: VERDICT
---

# SP-5 — Metrics Architecture & Baseline Capture

**Goal**: Define meaningful success and failure metrics per process and
capture the pre-automation baseline — so every post-deployment improvement
claim is auditable against a documented starting point.

Metrics before automation. A process with no baseline cycle-time, cost, or
quality measure cannot demonstrate that automation improved anything. The
comparison design is written **now**, before deployment, so it cannot be
gamed later. Post-deployment claims are audited against this register by
**VERDICT**.

## Intake

- SP-2 SOP records (section 9: success/failure definitions)
- System timestamps, labor allocations, error/rework logs where available

## Output Contract — Metrics Baseline Register per Process

### 1. Metric Selection Logic

2–4 metrics maximum per process, drawn from the four families:

| Family | Definition |
|---|---|
| **Cycle time** | Trigger to output |
| **Cost** | Labor hours × loaded rate + system cost |
| **Quality** | Error / exception / rework rate |
| **Volume / throughput** | Runs per period |

For each chosen metric: why it was chosen, and **what behavior it could
distort if over-optimized**. A metric without its distortion note is half a
metric.

### 2. Failure Definition

What constitutes a failed run, in operator-verifiable terms. A process whose
failures are invisible cannot be safely automated — there is no way to know
the agent broke it.

### 3. Baseline Capture

| Metric | Current Value | Measurement Method | Window | Class |
|---|---|---|---|---|

Estimates are permitted but enter as INFERENCE or STATED, **never** as
VERIFIED. An estimate wearing a decimal point is still an estimate.

### 4. Measurability Gaps

Processes where no baseline can currently be captured, with the specific
instrumentation needed to create one. **No baseline, no automation** — these
processes are gated until instrumented.

### 5. Post-Automation Comparison Design

The measurement plan that will run after deployment: same metrics, same
methods, same windows, defined now. Include the success gate value the pilot
must clear (consumed by SP-10's pilot design).

## The Prompt

> You are establishing the metrics baseline for `[Process Name]` from its
> SP-2 record. Select 2–4 metrics across the four families, stating for each
> why it was chosen and what it could distort. Define failure in terms an
> operator could verify. Capture the current baseline with method and window
> stated, classifying estimates honestly — INFERENCE or STATED, never
> disguised as measurement. Where no baseline is capturable, specify the
> instrumentation required. Close with the post-automation comparison design,
> including the success gate value, written so the comparison cannot be
> gamed after deployment.

## Quality Bar

- No process with more than four metrics — metric sprawl is avoidance.
- Every baseline value carries method, window, and class.
- Every over-optimization distortion is named, not gestured at.
- The comparison design would survive being handed to a hostile auditor.

## Feeds

- **SP-7** — baseline captured is a gate criterion.
- **SP-10** — the success gate value anchors the pilot design.
- **VERDICT** — post-deployment improvement claims audit against this register.
