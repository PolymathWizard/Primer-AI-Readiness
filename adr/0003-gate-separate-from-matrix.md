# ADR-0003: Readiness Gate Separate from Matrix Position

**Status**: Accepted · **Date**: 2026-07-15

## Context

The classic prioritization failure: a process scores "Automate Now" on
impact × complexity, and the score is read as permission. The scoring inputs
(volume, time-per-run) are orthogonal to the understanding inputs (complete
SOP, resolved ambiguities, sound data, captured baseline). Collapsing them
into one number lets a well-scored, poorly understood process into the
queue — the exact failure PRIMER exists to prevent.

## Decision

Matrix position and gate status are computed, reported, and stored
separately. Matrix position is *potential*; the gate is *permission*. The
gate has four criteria (SP-2 record complete; SP-3 zero unresolved
ambiguities; SP-4 no open gating findings; SP-5 baseline captured) and three
outcomes (PASS / CONDITIONAL / FAIL). `tools/matrix_placement.py` implements
the gate mechanically and refuses `gate_passed: true` when any criterion
fails or rests on STATED evidence.

## Consequences

- High-impact gate FAILs become named remediation lists — often the most
  valuable finding in an assessment — instead of being hidden by a good
  score.
- Two enforcement points (gatekeeper agent + orchestrator re-check) share
  one rule source: the tool.
- The matrix table carries two columns readers might expect to be one;
  docs/readiness-gate.md exists to explain why.
