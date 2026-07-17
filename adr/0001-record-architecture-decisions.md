# ADR-0001: Record Architecture Decisions

**Status**: Accepted · **Date**: 2026-07-15

## Context

PRIMER is a framework whose value depends on internal consistency: prompts,
schemas, tools, agents, and docs all restate the same contracts (evidence
enums, gate criteria, scoring thresholds). Undocumented changes to any one
consumer cause silent drift among the others — the exact failure the
framework diagnoses in client organizations.

## Decision

We record every architecturally significant decision as an ADR in `adr/`,
numbered sequentially, immutable after acceptance (superseded, never
edited). Changes to the framework contract require an ADR in the same PR.
The PR template enforces the check; CODEOWNERS routes contract paths to the
framework owner.

## Consequences

- Methodology choices propagate from a single documented source.
- Contract changes are auditable — the same append-only, traceable standard
  PRIMER applies to engagement evidence applies to the framework itself.
- Contributors bear a small documentation cost on contract PRs; that cost is
  the point.
