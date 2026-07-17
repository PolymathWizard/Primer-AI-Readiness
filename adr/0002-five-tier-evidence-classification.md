# ADR-0002: Five-Tier Evidence Classification with STATED Quarantine

**Status**: Accepted · **Date**: 2026-07-15

## Context

Readiness assessments fail in front of committees when scores cannot be
audited back to evidence, and fail in the field when owner testimony is
treated as measurement. A binary verified/unverified split loses the
distinctions that matter operationally: corroboration, analyst inference,
and self-report.

## Decision

Every quantitative claim carries exactly one of five classes:
**VERIFIED / CORROBORATED / UNCORROBORATED / INFERENCE / STATED**. The enum
is locked in `schemas/evidence-classification.schema.json`. STATED claims
are quarantined: they never directly support a readiness grade, matrix
placement, or gate pass until promoted to CORROBORATED or VERIFIED. The
evidence register is append-only; promotions add rows referencing the
original.

This is the same five-tier standard used across BHIL frameworks (CIPHER,
VERDICT), kept identical deliberately so cross-framework engagements share
one evidence vocabulary.

## Consequences

- Every score is auditable to a classified register row — the close
  criterion for every engagement.
- Adding or renaming a tier is a breaking change: ADR + major version bump.
- Tooling (`validate_evidence_tags.py`, `score_snapshot.py`,
  `matrix_placement.py`) enforces the quarantine mechanically, so the rule
  survives operator fatigue.
