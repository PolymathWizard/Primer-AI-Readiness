---
title: "Running an Engagement"
description: "The operational guide: intake, tier selection, module sequencing, workspace conventions, and close criteria."
---

# Running an Engagement

## 1. Intake

Confirm the six intake variables before any module runs:

| Variable | Options / Notes |
|---|---|
| `[Target Organization]` | The org or business unit assessed |
| `[Process Scope]` | Single department / cross-functional value stream / whole-of-business |
| `[Documentation Maturity]` | none / partial-informal / partial-formal / mature-but-stale |
| `[Automation Ambition]` | task-level assist / workflow automation / autonomous AI agents / undecided |
| `[Decision Stakeholder]` | COO / CIO / owner / transformation lead |
| `[Evidence in Hand]` | SOPs, system exports, org charts, ticketing data, prior maps |

Calibration: low maturity → weight SP-1/SP-2 heavily and treat all existing
descriptions as STATED; autonomous-agent ambition → SP-3 and SP-4 become
gating, not advisory.

## 2. Tier Selection

| Trigger Heard | Tier | Sequence |
|---|---|---|
| "We want to deploy AI agents — where do we start?" | 1 → 2 | SP-9, then bridge |
| "We tried automating X and it made things worse" | 2 | SP-2/SP-3 heavy |
| "Document our SOPs before we scale / sell / hire" | 3 | Full SP-1–SP-8 |
| "Which processes should we automate first?" | 2 | SP-1 → SP-2 → SP-3/4 → SP-7 |
| "Board wants an AI strategy with substance" | 2 or 3 | Assessment + roadmap |
| "Our data is a mess and we know it" | 2 | SP-4 heavy, NEXUS bridge |
| "Prove the automation actually worked" | 1 + SP-5 | Re-baseline, VERDICT pair |

## 3. Workspace Convention

Client artifacts live in `engagements/<engagement-id>/` — gitignored, never
committed. Standard layout:

```
engagements/acme-2026-q3/
├── intake.md              # The six variables, signed off
├── census/                # SP-1 outputs
├── sops/                  # SP-2 records, one file per process
├── decision-logic/        # SP-3 registers
├── data-audit/            # SP-4 outputs
├── baselines/             # SP-5 registers
├── bottlenecks/           # SP-6 maps
├── matrix/                # SP-7 package (JSON + rendered)
├── streams/               # SP-8 map
├── snapshot/              # SP-9 (Tier 1 engagements)
├── roadmap/               # SP-10 package
└── evidence-register.csv  # The consolidated, append-only register
```

The evidence register is **append-only**: promotions add a new row referencing
the original, they never edit it. The trace chain must be auditable.

## 4. Module Sequencing Rules

1. Run modules in order; each consumes its predecessors' registers.
2. After each module, confirm with the client contact before proceeding —
   findings often re-scope the next module.
3. SP-3 ambiguities are resolved with the process owner **before** SP-7 runs.
4. SP-9 runs alone or not at all — it never substitutes for SP-1/SP-2 inside
   a Tier 2+ engagement.
5. Validators run before any deliverable is assembled:

```bash
python tools/validate_evidence_tags.py engagements/<id>/
python tools/matrix_placement.py engagements/<id>/matrix/placements.json --check
python tools/score_snapshot.py engagements/<id>/snapshot/scorecards.json --check
```

## 5. Deliverable Assembly

Deliverables render from the engagement workspace — the workspace is the
source of truth, the document is a view. For BHIL-branded `.docx` output,
the `bhil-docx` skill consumes the workspace Markdown. Deliverable page
targets by tier: Tier 1, 10–15 pages; Tier 2, 30–50; Tier 3, 60–100.

## 6. Close Criteria

An engagement is committee-ready when — and only when:

- Every score is auditable to a classified row in the evidence register.
- Every automation candidate has passed the gate (or is explicitly gated with
  a remediation plan).
- The rejection log is present and reasoned.
- The next-two-decisions section is complete with owners and dates.
- A governance owner is named — the organization can say who owns the
  register the day after the advisor leaves.
