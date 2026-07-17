# ADR-0006: Orchestrator + Ten Single-Module Subagents (CADRE Pattern)

**Status**: Accepted · **Date**: 2026-07-15

## Context

The framework has ten module contracts with strict input/output boundaries,
mandatory human checkpoints, and mechanical enforcement points. A single
agent running the whole pipeline accumulates context bloat, blurs module
boundaries, and — worst — can quietly reconcile conflicts (two volume
figures, two operator rules) that the methodology requires be surfaced, not
resolved.

## Decision

One orchestrator (recommended: Opus) that owns intake, sequencing,
validation between modules, gate re-checks, and deliverable assembly — and
produces no module content. Ten subagents (recommended: Sonnet), one per SP
module, each with: declared read-only inputs, a single write directory under
`engagements/<id>/`, the module's quality bar restated, and a completion
summary contract. This mirrors the CADRE deployment pattern.

Two rules are duplicated deliberately at both levels: the STATED quarantine
and the ambiguity non-resolution rule — defense in depth for the two rules
whose violation is silent.

## Consequences

- Module boundaries are enforced by agent definition, not agent discipline.
- Human checkpoints are structural: the orchestrator cannot delegate
  advancing the engagement.
- Ten small agent files are cheaper to audit and evolve than one large one;
  a module contract change touches exactly one subagent.
- Cost: more handoffs. Accepted — the handoffs are where validation lives.
