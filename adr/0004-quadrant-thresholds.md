# ADR-0004: Quadrant Thresholds and Volume Weighting Formula

**Status**: Accepted · **Date**: 2026-07-15

## Context

Quadrant boundaries and intra-quadrant ordering must be identical across the
SP-7 prompt, the schema, the placement tool, and rendered deliverables.
Threshold drift between consumers (the QUADRA midpoint lesson, ADR-0006 in
that repo) produces deliverables whose tables contradict their own charts.

## Decision

Single source of truth: `schemas/matrix-placement.schema.json` documents the
thresholds; `tools/matrix_placement.py` implements them; `tests/` pins them.

- Quadrants: **Automate Now** (impact ≥ 4, complexity ≤ 2) ·
  **Design Carefully** (impact ≥ 4, complexity ≥ 3) ·
  **Quick Wins If Idle** (impact ≤ 3, complexity ≤ 2) ·
  **Leave Alone** (impact ≤ 3, complexity ≥ 3).
- Composite scores: sub-scores averaged, rounded half-up to an integer 1–5.
- Intra-quadrant ordering: `priority = impact × log10(monthly_volume + 1)`,
  weight shown in the output.
- Any STATED-class volume input marks the entire matrix `provisional: true`.

## Consequences

- Prompt text describing thresholds is documentation of the schema, not an
  independent authority; disagreement is a prompt bug.
- Changing a threshold is a schema + tool + test + prompt change in one PR,
  with a superseding ADR.
- The rounding rule is pinned by test — "half-up" is not left to a
  language's default banker's rounding.
