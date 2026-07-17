---
module: SP-9
title: "Process Readiness Snapshot (Standalone Diagnostic)"
framework: PRIMER
version: 1.0.0
feeds: [Tier-2 bridge]
consumes: []
schema: ../schemas/readiness-scorecard.schema.json
standalone: true
commercial_tier: 1
---

# SP-9 — Process Readiness Snapshot *(Standalone Paid Diagnostic)*

**Goal**: A fixed-scope, fast-turn diagnostic — audit 3–5 nominated processes
against the PRIMER readiness standard and deliver a scored snapshot with a
gap register and a matrix placement.

SP-9 is the only module sanctioned to run independently of the full stack.
It is the door-opener SKU: priced standalone, scoped to protect margin (3–5
processes, no census, no value-stream map), and it always ends with the
bridge recommendation to Tier 2+.

## Intake

- 3–5 nominated processes, and **who nominated them** (the nomination itself
  is evidence about what the organization believes matters)
- Owner interviews per process; system evidence for at least one process

## The Scorecard — Five Dimensions, 0–2 Each, 10 Maximum

Machine implementation: [../tools/score_snapshot.py](../tools/score_snapshot.py).
Conforms to [readiness-scorecard.schema.json](../schemas/readiness-scorecard.schema.json).

| Dimension | 0 | 1 | 2 |
|---|---|---|---|
| **Documentation** | No SOP record | Partial or stale record | SOP record exists and is current |
| **Decision Logic** | Rules undocumented / tribal | Rules partially externalized | Rules externalized, no unresolved ambiguities |
| **Data Dependencies** | Gating fragility present | Fragility flagged, remediation planned | No gating fragility findings |
| **Metrics Baseline** | No baseline | Estimated (INFERENCE/STATED) | Measured baseline captured |
| **Bottleneck Clarity** | Bottlenecks unmapped | Mapped, unclassified | Structural vs. incidental classified |

**Grade bands**: 8–10 **Automation-Ready** · 5–7 **Conditionally Ready** ·
0–4 **Not Ready**.

## Output Contract — Process Readiness Snapshot

### 1. Scope Statement

The 3–5 processes, who nominated them, and what the snapshot explicitly does
not cover (no census, no value-stream map, no whole-portfolio claims).

### 2. Per-Process Readiness Scorecard

The five-dimension scorecard per process, each dimension score justified in
one or two sentences with its evidence class.

### 3. Gap Register

Every point lost, with the specific remediation and effort estimate. A "1"
without a named path to "2" is an incomplete finding.

### 4. Snapshot Matrix

The 3–5 processes placed on the impact × complexity matrix with the readiness
gate result — clearly labeled as a snapshot placement, not a portfolio
ranking.

### 5. Claimed-vs-Performed Spot Check

For at least one process, a direct comparison of owner testimony against
system evidence. **This is the snapshot's signature exhibit.** Organizations
do not pay for a transcription of what they told you; they pay for the
documented distance between what they believe happens and what the evidence
shows.

### 6. Bridge Recommendation

The explicit path from snapshot to full engagement: which SP modules the
findings indicate, and what a full census would likely surface. Every
snapshot ends here.

## The Prompt

> You are running the PRIMER Process Readiness Snapshot on the following
> nominated processes: `[Process List]`, nominated by `[Nominator]`. State
> the scope and its limits up front. Score each process on the five
> dimensions (0–2 each), justifying every score with its evidence class.
> Register every lost point with remediation and effort. Place the processes
> on the snapshot matrix with gate results, labeled as snapshot placements.
> Run the claimed-vs-performed spot check on at least one process — owner
> testimony against system evidence, both versions recorded. Close with the
> bridge recommendation: the SP modules indicated and what a full census
> would likely surface.

## Quality Bar

- No dimension scored 2 on STATED evidence alone.
- The spot check compares testimony to *system* evidence, not to another
  person's testimony.
- The snapshot never claims portfolio-level conclusions from 3–5 processes.
- The bridge recommendation is specific — named modules, named reasons.

## Commercial Note

Tier 1 SKU. 10–15 page deliverable, 1–2 week engagement. The margin
protection is the scope lock: 3–5 processes, no census, no value-stream map.
Scope creep here is priced at zero and delivered at cost — hold the line.
