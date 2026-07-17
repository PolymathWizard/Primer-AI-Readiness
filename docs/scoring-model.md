---
title: "Scoring Model"
description: "The impact and complexity sub-score derivation, volume weighting, quadrant thresholds, and snapshot scorecard."
---

# Scoring Model

Two scoring systems operate in PRIMER: the **SP-7 prioritization matrix**
(portfolio ranking) and the **SP-9 readiness scorecard** (per-process
diagnostic). Both show their sub-scores — composites without visible
derivation are not defensible, and defensibility is the deliverable.

## SP-7: Impact Score (1–5)

Four sub-scores, each 1–5, averaged and rounded half-up:

| Sub-score | What It Measures | Evidence Source |
|---|---|---|
| Volume | Runs per month, banded against the portfolio | SP-1 register |
| Time per run | Labor minutes, trigger to output | SP-5 baseline |
| Error cost | Cost of a failed run × failure rate | SP-5 quality metrics |
| Downstream unblocking | How much downstream value this process gates | SP-8 propagation analysis |

## SP-7: Complexity Score (1–5)

Five sub-scores, each 1–5, averaged and rounded half-up:

| Sub-score | What It Measures | Evidence Source |
|---|---|---|
| Decision-rule count | Rules registered for the process | SP-3 |
| Tribal-knowledge density | Share of rules classed tribal | SP-3 |
| Data fragility | Count and severity of fragility flags | SP-4 |
| Exception rate | Exceptions per 100 runs | SP-2 / SP-5 |
| System count | Distinct systems touched | SP-2 |

## Volume Weighting

Matrix ordering within a quadrant is volume-weighted:
`priority = impact × log10(monthly_volume + 1)`. The weight is shown in the
matrix table, never applied silently. Volume figures classed STATED render
the entire matrix **provisional**.

## Quadrant Thresholds

| Quadrant | Impact | Complexity |
|---|---|---|
| Automate Now | ≥ 4 | ≤ 2 |
| Design Carefully | ≥ 4 | ≥ 3 |
| Quick Wins If Idle | ≤ 3 | ≤ 2 |
| Leave Alone | ≤ 3 | ≥ 3 |

The threshold midpoint (impact 4, complexity boundary between 2 and 3) is an
architecture decision — see [ADR-0004](../adr/0004-quadrant-thresholds.md) —
and propagates from
[schemas/matrix-placement.schema.json](../schemas/matrix-placement.schema.json)
through [tools/matrix_placement.py](../tools/matrix_placement.py) and the
SP-7 prompt. If any consumer disagrees with the schema, the schema wins.

## SP-9: Readiness Scorecard (0–10)

Five dimensions, 0–2 each:

| Dimension | 0 | 1 | 2 |
|---|---|---|---|
| Documentation | No SOP record | Partial / stale | Current SOP record |
| Decision Logic | Tribal / undocumented | Partially externalized | Externalized, zero ambiguities |
| Data Dependencies | Gating fragility | Flagged, remediation planned | No gating findings |
| Metrics Baseline | None | Estimated | Measured |
| Bottleneck Clarity | Unmapped | Mapped, unclassified | Classified structural/incidental |

**Grade bands**: 8–10 Automation-Ready · 5–7 Conditionally Ready ·
0–4 Not Ready.

Rule: **no dimension scores 2 on STATED evidence alone.** The scorer
([tools/score_snapshot.py](../tools/score_snapshot.py)) enforces this
mechanically by demoting any 2 backed only by STATED evidence to 1.

## Reference Implementations

The Python implementations in [tools/](../tools/) are the executable
specification. The conformance tests in [tests/](../tests/) pin the rounding
rule, the volume weight formula, the quadrant boundaries, and the STATED
demotion rule. Changing any of these is a schema + tool + test + prompt
change in a single PR, with an ADR.
