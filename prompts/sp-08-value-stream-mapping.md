---
module: SP-8
title: "Inter-Process Value Stream Mapping"
framework: PRIMER
version: 1.0.0
feeds: [SP-7, SP-10]
consumes: [SP-1, SP-2]
schema: null
---

# SP-8 — Inter-Process Value Stream Mapping

**Goal**: Link the documented SOPs into end-to-end value streams — which
outputs become which inputs — so automation decisions account for propagation
effects instead of optimizing processes in isolation.

A process scored in isolation can look like a "Quick Win" while sitting in
the middle of a chain whose upstream feeds it garbage and whose downstream
amplifies its errors. The stream view is what turns a portfolio of scores
into a sequence with logic.

## Intake

- SP-1 census register (the node list)
- SP-2 SOP records (sections 4 and 5 — the inputs and outputs to be linked)

## Output Contract — Value Stream Map

### 1. Linkage Register

| Producing Process | Consuming Process | Artifact | Format | Handoff Mechanism | Class |
|---|---|---|---|---|---|

Every output→input connection between documented processes.

### 2. Stream Assembly

The end-to-end chains in plain sequence notation:

```
Order Intake → Credit Check → Fulfillment → Invoicing → Collections
```

Name the customer- or cash-touching endpoint for each stream — a stream that
touches neither deserves a hard look at why it exists.

### 3. Propagation Analysis

Per stream: which upstream failure modes propagate downstream, how far, and
at what amplification. Identify the **two or three processes whose automation
unblocks the most downstream value** — these carry a downstream-unblocking
impact bonus into SP-7.

### 4. Format Friction Points

Every handoff where the artifact changes format
(system → spreadsheet → email → re-keyed). Each is simultaneously an
automation opportunity and a fragility — record it as both, cross-referenced
to the SP-4 fragility flags.

### 5. Orphan Register

Processes with no mapped upstream or downstream connection. Two possible
findings, both of which matter: the census missed a link, or the process may
not need to exist. Assign each orphan one of those hypotheses and the check
that would resolve it.

## The Prompt

> You are assembling the value stream map from the census register and SOP
> records. Register every output→input linkage with its artifact, format, and
> handoff mechanism. Assemble the end-to-end streams and name each stream's
> customer- or cash-touching endpoint. Analyze failure propagation per stream
> and identify the two or three processes whose automation unblocks the most
> downstream value. Register every format friction point as both opportunity
> and fragility. List orphan processes with a hypothesis for each — missed
> link or unnecessary process — and the check that resolves it.

## Quality Bar

- Every linkage has a named artifact — "they coordinate" is not a linkage.
- Every stream has an endpoint; endpoint-less streams flagged.
- Downstream-unblocking candidates carry quantified reasoning, not vibes.
- No orphan left without a hypothesis and a resolution check.

## Feeds

- **SP-7** — downstream-unblocking analysis feeds the impact score.
- **SP-10** — stream structure informs roadmap sequencing (automate upstream
  of the chain you want to fix, not downstream of the chaos).
