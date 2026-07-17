---
title: "The Readiness Gate"
description: "The four-criterion gate that separates matrix position (potential) from automation permission."
---

# The Readiness Gate

The gate is the framework's spine. It exists to prevent the exact failure
PRIMER was built against: **enthusiastic automation of a well-scored, poorly
understood process.**

## Position vs. Permission

The SP-7 matrix answers "where would automation pay off?" The gate answers
"is this process understood well enough to automate safely?" These are
different questions, and PRIMER never lets one answer stand in for the other:

> **Matrix position is *potential*; the gate is *permission*.**

A process can sit squarely in "Automate Now" — high impact, low complexity —
and still fail the gate because its decision logic contains an unresolved
ambiguity or its volume figure is an unpromoted STATED claim.

## The Four Criteria

A process passes the gate when — and only when — all four hold:

| # | Criterion | Source | Failure Looks Like |
|---|---|---|---|
| 1 | **SOP record complete** — all twelve sections of the PRIMER standard | SP-2 | Empty exceptions section; steps requiring unstated context |
| 2 | **Decision logic externalized, zero unresolved ambiguities** | SP-3 | Two operators, two rules, no owner resolution |
| 3 | **No open gating data findings** | SP-4 | Single-person data dependency; unversioned spreadsheet as system of record |
| 4 | **Baseline captured** — measured, or instrumented with a dated plan | SP-5 | "We think it takes about a day" as the cycle-time record |

If `[Automation Ambition]` is **autonomous AI agents**, criteria 2 and 3 are
evaluated at full strictness — no advisory-grade exceptions.

## Gate Outcomes

- **PASS** — all four criteria met with CORROBORATED or VERIFIED evidence.
  The process may enter the automation queue at its matrix position.
- **CONDITIONAL** — criteria met but one or more rests on INFERENCE-class
  evidence. The process enters the queue flagged; the promotion plan is part
  of the phase entry criteria in SP-10.
- **FAIL** — one or more criteria unmet. The specific gaps go to the
  remediation register with owner and effort estimate. The process does not
  enter the queue, regardless of quadrant.

A FAIL is not a criticism of the process — it is a statement about the
completeness of the organization's knowledge of it. High-impact FAILs are
often the most valuable findings in the assessment: they name exactly what
must be true before the biggest opportunity can be taken.

## Structural Controls

One additional rule rides with the gate: **no structural bottleneck is
automated away without an explicit control-replacement note** (SP-6 / SP-10).
A regulatory review or segregation-of-duties approval that automation removes
must be replaced by a named, equivalent control in the pilot design — or the
design changes.

## Enforcement

- The prompt modules state the gate in SP-7 and consume it in SP-10.
- The agent configuration enforces it at the orchestrator level: the
  prioritization subagent cannot emit a PASS with an unresolved SP-3
  ambiguity or open SP-4 gating finding in the engagement workspace.
- [tools/matrix_placement.py](../tools/matrix_placement.py) implements the
  gate mechanically and refuses to mark `gate_passed: true` unless the four
  criterion flags are all true and no supporting class is STATED.
