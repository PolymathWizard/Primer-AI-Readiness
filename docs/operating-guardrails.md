---
title: "Operating Guardrails"
description: "The eight hard rules that bind every PRIMER engagement, prompt run, and agent."
---

# Operating Guardrails

Eight rules. They bind human operators, prompt runs, and agents equally.
Each names its enforcement point — a guardrail without enforcement is a
suggestion.

| # | Rule | Enforced By |
|---|---|---|
| 1 | **No process enters the automation queue without a complete SP-2 record.** | Gate criterion 1; `matrix_placement.py` |
| 2 | **No matrix placement without classified evidence for both scores.** | SP-7 contract; `validate_evidence_tags.py` |
| 3 | **No readiness grade built on unpromoted STATED claims.** | STATED quarantine; `score_snapshot.py` demotion rule |
| 4 | **No unresolved SP-3 ambiguity carried into a gate pass.** | Gate criterion 2; orchestrator re-check |
| 5 | **No baseline, no automation. Estimates flag the matrix as provisional.** | Gate criterion 4; provisional flag in matrix schema |
| 6 | **No structural bottleneck automated away without an explicit control-replacement note.** | SP-10 pilot design contract |
| 7 | **No assessment without a rejection log.** What was not recommended, and why, is part of the deliverable. | SP-7 contract; close criteria |
| 8 | **No engagement close without the next-two-decisions section and a governance owner named.** | SP-10 contract; close criteria |

## The Shape of the Rules

Notice what the guardrails share: each one blocks a *shortcut that feels
reasonable in the moment*. Skipping the SOP record for a process "everyone
knows." Averaging two operators' conflicting rules. Letting a confident
estimate stand in for a baseline. Closing the engagement with the governance
question "to be determined."

PRIMER is methodologically opinionated where the discipline is settled —
document before deploying, baseline before improving, externalize decision
logic before delegating it to software — and deliberately conservative where
organizations are most tempted to rush: the readiness gate, the STATED
quarantine, the ambiguity stop-sign.

## For Agent Operators

The agent configuration restates these rules in [CLAUDE.md](../CLAUDE.md)
and each subagent definition. Where a rule has a mechanical enforcement point
(rules 1–5), the agent calls the tool rather than reasoning its way to
compliance. Where it does not (rules 6–8), the orchestrator checks the
artifact before accepting the module output.
