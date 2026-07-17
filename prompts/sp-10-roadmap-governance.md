---
module: SP-10
title: "AI Readiness Roadmap & Process Governance"
framework: PRIMER
version: 1.0.0
feeds: [engagement close]
consumes: [SP-3, SP-5, SP-6, SP-7, SP-8]
schema: null
commercial_tier: 4
---

# SP-10 — AI Readiness Roadmap & Process Governance

**Goal**: Convert the assessment into a sequenced roadmap and a governance
model that keeps documentation current after go-live — because an SOP
register that is not maintained decays back into tribal knowledge within two
quarters.

An unmaintained SOP register is worse than none: it is documentation the
organization trusts and shouldn't. The governance model is not an appendix —
operated continuously, it is the Tier 4 retainer.

## Intake

- SP-7 gated sequence and rejection log
- SP-5 baselines and success-gate values
- SP-3 judgment/rule splits
- SP-6 structural bottleneck classifications
- SP-8 stream structure

## Output Contract — Roadmap & Governance Package

### 1. Sequenced Roadmap

The SP-7 queue expressed as a phased plan — **remediation → pilot → gate
review → scale** — each phase with owner, entry criteria, and exit criteria.
Remediation work (gap register items) is scheduled *before* the processes it
unblocks, and stream logic (SP-8) orders chains upstream-first.

### 2. Pilot Design

- The recommended first process and why.
- The **success gate**: the SP-5 baseline metric value the pilot must clear,
  measured by the pre-registered comparison design.
- The **rollback condition**: the observable state that triggers reversion,
  decided now, while nobody is defending a sunk cost.
- The **human-in-the-loop design**: judgment-class decisions (SP-3 split)
  stay human; structural bottlenecks (SP-6) are preserved as controls, with
  an explicit control-replacement note for any that automation touches.

### 3. Process Governance Model

- **Register ownership** — a named role owns the SOP register the day after
  the advisor leaves. No engagement closes without this name.
- **Change-control rule** — process changes require record updates *before*
  deployment, not after.
- **Re-verification cadence** — scheduled, calendar-owned.
- **Forced re-documentation triggers** — system change, owner change, volume
  shift ≥ 25%.

### 4. Documentation Decay Controls

The lightweight ritual that keeps the register alive: quarterly owner
attestation; annual claimed-vs-performed spot check on a rotating sample.
Heavier rituals get skipped; design for the organization that exists.

### 5. Capability Handoff

What the organization's own team must be able to do without the advisor:
run SP-1 discovery on a new department, complete an SP-2 record to standard,
and score SP-9 internally. The handoff is tested, not assumed — have them do
one of each before close.

### 6. The Next Two Decisions

Named explicitly, with dates and owners: (1) the pilot go/no-go criteria and
decision date; (2) the governance ownership decision. An engagement that
closes without these has produced a document, not a decision.

## The Prompt

> You are converting the completed PRIMER assessment into the roadmap and
> governance package. Sequence the gated queue into phases with owners and
> entry/exit criteria, scheduling remediation before the processes it
> unblocks and respecting stream order. Design the pilot: process, success
> gate from the SP-5 baseline, rollback condition, and human-in-the-loop
> design from the SP-3 split and SP-6 structural bottlenecks — with a
> control-replacement note for any structural control automation touches.
> Define the governance model with a named register owner, the
> change-control rule, re-verification cadence, and forced re-documentation
> triggers. Specify the decay controls and the tested capability handoff.
> Close by naming the next two decisions with owners and dates.

## Quality Bar

- No phase without entry and exit criteria.
- The rollback condition is observable and pre-committed.
- The register owner is a named role, accepted by its occupant.
- The capability handoff is demonstrated, not described.

## Feeds

- Engagement close; Tier 4 retainer operates this module continuously.
