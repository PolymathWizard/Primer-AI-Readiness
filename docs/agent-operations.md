---
title: "Agent Operations"
description: "How the Claude Code multi-agent configuration operates the PRIMER pipeline."
---

# Agent Operations

This repository doubles as a Claude Code workspace. Open it in Claude Code
and the orchestrator instructions in [CLAUDE.md](../CLAUDE.md) sequence ten
specialist subagents — one per SP module — through the pipeline, enforcing
the readiness gate and the evidence standard at every handoff.

## Topology (CADRE pattern)

- **Orchestrator** — runs on **Opus**. Owns intake, sequencing, gate
  enforcement, evidence-register integrity, and deliverable assembly. Never
  produces module content itself.
- **Ten subagents** — run on **Sonnet**. Each owns exactly one SP module's
  output contract. Defined in [.claude/agents/](../.claude/agents/):

| Subagent | Module | Writes To |
|---|---|---|
| `census-taker` | SP-1 | `census/` |
| `sop-scribe` | SP-2 | `sops/` |
| `logic-auditor` | SP-3 | `decision-logic/` |
| `data-auditor` | SP-4 | `data-audit/` |
| `baseline-keeper` | SP-5 | `baselines/` |
| `friction-mapper` | SP-6 | `bottlenecks/` |
| `gatekeeper` | SP-7 | `matrix/` |
| `stream-weaver` | SP-8 | `streams/` |
| `snapshot-assessor` | SP-9 | `snapshot/` |
| `governance-architect` | SP-10 | `roadmap/` |

## Handoff Protocol

1. The orchestrator confirms the six intake variables with the human and
   writes `engagements/<id>/intake.md`. **No subagent launches before intake
   sign-off.**
2. Each subagent reads only its declared inputs (predecessor registers +
   human-supplied evidence), writes only to its declared directory, and tags
   every quantitative claim.
3. On completion, the subagent appends its claims to
   `evidence-register.csv` and returns a completion summary: rows produced,
   class distribution, open flags.
4. The orchestrator validates the output (`tools/validate_evidence_tags.py`,
   schema checks) **before** unlocking the next module.
5. Human checkpoint after every module — the orchestrator presents the
   summary and waits. PRIMER is human-directed; the agents never advance the
   engagement on their own authority.

## Gate Enforcement

The `gatekeeper` subagent computes matrix placements via
[tools/matrix_placement.py](../tools/matrix_placement.py) — it does not
score freehand. The tool refuses `gate_passed: true` if:

- any SP-3 ambiguity for the process is unresolved,
- any SP-4 gating finding is open,
- no SP-5 baseline exists, or
- any gate-supporting evidence is classed STATED.

The orchestrator independently re-runs the check before accepting the matrix.
Two enforcement points, one rule source — the tool.

## Hard Rules (bind all agents)

1. STATED claims never support a grade, placement, or gate pass.
2. No agent resolves an SP-3 ambiguity — resolution belongs to the process
   owner, via the human.
3. No agent invents a number. Missing evidence is recorded as missing.
4. The evidence register is append-only.
5. Client material never leaves `engagements/`.
6. Tool-agnosticism holds: no vendor names, no product recommendations in
   any client-facing output.

## Running It

```bash
# In Claude Code, from the repo root:
# "Start a Tier 2 PRIMER engagement for <org>, scope <dept>."
# The orchestrator will run intake, then sequence subagents with
# human checkpoints between modules.
```

For a Tier 1 snapshot, only `snapshot-assessor` (and the orchestrator) run —
mirroring the commercial scope lock.
