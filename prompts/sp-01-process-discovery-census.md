---
module: SP-1
title: "Process Discovery Census"
framework: PRIMER
version: 1.0.0
feeds: [SP-2, SP-7, SP-8]
consumes: []
schema: ../schemas/census-register.schema.json
---

# SP-1 — Process Discovery Census

**Goal**: Systematically surface every repeatable process in `[Process Scope]`
— including the invisible ones that live in inboxes, calendars, and one
operator's habits — and produce a census register with a coverage confidence
score.

SP-1 sets the ceiling for the entire engagement. A census that misses the
shadow processes produces a prioritization matrix that optimizes the visible
60% of the operation. A census that silently narrows its own scope produces
false completeness — state what was not covered.

## Intake

- `[Process Scope]` — the boundary of the census (department / value stream / whole business)
- Access to: calendars, shared inboxes or ticket queues, system logs, and 3+
  operator interviews per function where possible

## The Discovery Method Stack

Apply and document **at least three** of the following methods. Record which
were used and which were unavailable — unavailability is a coverage finding.

1. **Calendar archaeology** — recurring meetings imply recurring processes.
2. **Inbox / ticket archaeology** — repeated request patterns are undeclared
   processes.
3. **Handoff interviews** — "What do you receive, what do you send, from
   whom, to whom?"
4. **System log review** — recurring transactions and scheduled reports.
5. **The Monday question** — "Walk me through what you do every Monday."
6. **Exception mining** — "What breaks most often?" Failure clusters mark
   process boundaries.

## Output Contract

### 1. Discovery Method Stack Record

Which methods were applied, to which functions, and what each surfaced.

### 2. Census Register

| # | Process Name | Owner | Function | Trigger | Frequency | Est. Volume/Mo | Systems Touched | Documentation Status | Evidence Class |
|---|---|---|---|---|---|---|---|---|---|

One row per discovered process. Conforms to
[census-register.schema.json](../schemas/census-register.schema.json).

### 3. Shadow Process Flags

Processes discovered that no one named as a process: workarounds, unofficial
approval chains, spreadsheet-mediated handoffs. These are frequently the
highest-fragility, highest-dependency items in the portfolio.

### 4. Coverage Confidence Score

An explicit estimate of census completeness, per function — e.g., "high
confidence for finance ops; low for field operations — two roles not yet
interviewed." Name the specific gaps. A confidence score without named gaps
is a STATED claim about your own work.

### 5. Evidence Classification

Every register row tagged. Interview-only discoveries are STATED;
log-confirmed discoveries are VERIFIED or CORROBORATED.

## The Prompt

> You are a fractional Chief Data Officer running a process discovery census
> for `[Process Scope]`. Apply at least three methods from the discovery
> method stack and document which you used. Register every repeatable process
> with owner, function, trigger, frequency, estimated monthly volume, systems
> touched, and documentation status. Flag shadow processes explicitly. Close
> with a per-function coverage confidence score naming the specific gaps, and
> tag every row with its evidence class. Interview testimony enters as STATED
> until corroborated by system evidence.

## Quality Bar

- No function in scope with zero registered processes and no explanation.
- Every "everyone knows" process appears in the register anyway.
- Shadow processes flagged, not folded silently into their parent process.
- Coverage gaps named by role and function, not waved at.

## Feeds

- **SP-2** documents each in-scope register row to the SOP standard.
- **SP-7** consumes register volume figures for matrix weighting.
- **SP-8** consumes the register as the node list for value-stream mapping.
