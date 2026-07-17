# Worked Example — Acme Fulfillment Co. (Fictional)

A fully fictional Tier 1 (SP-9 Process Readiness Snapshot) engagement
demonstrating the artifact shapes, the evidence discipline, and the
mechanical scoring. Nothing here derives from a real client.

| Artifact | Demonstrates |
|---|---|
| [scorecards.json](scorecards.json) | The SP-9 scorecard package — including a STATED demotion and one Not Ready process |
| [placements.json](placements.json) | An SP-7-shape snapshot matrix — including a gate FAIL on an "Automate Now" process and a provisional flag from STATED volume |
| [evidence-register.csv](evidence-register.csv) | The append-only register, including a STATED → CORROBORATED promotion row |

Recompute and verify:

```bash
python tools/score_snapshot.py examples/acme-fulfillment/scorecards.json --check
python tools/matrix_placement.py examples/acme-fulfillment/placements.json --check
python tools/validate_evidence_tags.py examples/acme-fulfillment/
```

The story the numbers tell: **order-entry** looks like the obvious win
(high impact, low complexity — "Automate Now") but fails the gate on an
unresolved decision-rule ambiguity and STATED volume; **returns-processing**
scores Conditionally Ready with a documentation demotion; **invoice-matching**
is the actual pilot candidate — lower drama, gate-clean.
