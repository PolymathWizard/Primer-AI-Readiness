# ADR-0005: SP-9 as the Only Sanctioned Standalone Module

**Status**: Accepted · **Date**: 2026-07-15

## Context

Commercially, the framework needs a fixed-scope, fast-turn entry SKU.
Methodologically, most modules are unsafe to run alone: a matrix without a
census optimizes the visible portion of the operation; SOP records without
discovery inherit the client's blind spots. But a fully sequential-only
framework has no door-opener.

## Decision

SP-9 (Process Readiness Snapshot) is the only module sanctioned to run
standalone. Its safety comes from its scope lock: 3–5 nominated processes,
no census, no value-stream map, no portfolio-level claims, snapshot-labeled
matrix placements, and a mandatory bridge recommendation. Conversely, SP-9
never runs *inside* a Tier 2+ engagement — snapshot-grade evidence must not
sit under assessment-grade claims.

## Consequences

- The Tier 1 SKU has a defensible boundary; scope creep is a priced
  decision, not a drift.
- The `snapshot-assessor` agent enforces the lock (out-of-scope requests go
  to the bridge memo).
- The nomination source is recorded as evidence — who chose the 3–5
  processes is itself a finding about what the organization believes
  matters.
