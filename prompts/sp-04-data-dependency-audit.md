---
module: SP-4
title: "Input/Output & Data Dependency Audit"
framework: PRIMER
version: 1.0.0
feeds: [SP-7]
consumes: [SP-2]
schema: null
escalates_to: NEXUS
---

# SP-4 — Input/Output & Data Dependency Audit

**Goal**: Audit every input and output for source, format, quality, and
provenance — the fractional-CDO layer — and flag the data-architecture
findings that gate automation regardless of process quality.

Data dependencies are load-bearing. A process that runs on a spreadsheet
emailed by one person is not automation-ready regardless of its volume — it
is a data-architecture finding first, a process finding second.

## Intake

- SP-2 SOP records (sections 4 and 5: inputs and outputs)
- System access or screen-share inspection of the actual data flows
- The people who produce and consume each critical input

## Output Contract — Data Dependency Audit per Process

### 1. Dependency Map

| Item | Direction | System of Record | Format | Owner | Update Cadence | Class |
|---|---|---|---|---|---|---|

Every input and output, no exceptions.

### 2. Fragility Flags

Flag every instance of:

- **Single-person data dependency** — one human is the pipeline.
- **Unversioned spreadsheet** — the file *is* the system of record.
- **Manual re-keying** — data typed from one system into another.
- **Email-as-database** — the inbox is the queue and the archive.
- **Copy-paste bridge** — a human clipboard connecting two systems.

Each flag carries the process affected, the failure mode it implies, and a
severity rating.

### 3. Quality Assessment

Per critical input: **completeness**, **accuracy method** ("how would you
know it's wrong?" — a question with no answer is itself a finding),
**timeliness**, and **duplication** (does this data live in two places that
can disagree?).

### 4. Provenance Chains

For the three most critical data items: where the data is born, every hand it
passes through, every transformation applied. Automation inherits the whole
chain — including the step where someone "cleans it up a bit in Excel."

### 5. Gating Findings

Data findings that block automation independent of process readiness, each
with a remediation action and effort estimate. These flow directly to the
SP-7 gate and, where the data architecture itself becomes the engagement,
escalate to **NEXUS**.

### 6. Evidence Classification

System-inspected findings are VERIFIED; described-but-not-inspected flows are
STATED. "The data is clean" from the person who maintains it is STATED by
definition.

## The Prompt

> You are a fractional Chief Data Officer auditing the data dependencies of
> `[Process Name]` from its SP-2 record. Map every input and output with
> system of record, format, owner, and update cadence. Hunt the five
> fragility patterns explicitly — single-person dependencies, unversioned
> spreadsheets, re-keying, email-as-database, copy-paste bridges. Assess
> quality on the four dimensions, asking "how would you know it's wrong?" of
> every critical input. Trace provenance for the three most critical items
> end to end. State which findings gate automation outright. Inspect where
> you can; classify honestly where you cannot.

## Quality Bar

- No dependency map row with an empty "system of record" cell — "someone's
  laptop" is an answer, and a finding.
- Every fragility flag names a concrete failure mode, not just a pattern.
- Provenance chains include transformations, not just handoffs.
- Gating findings are separated from advisory findings — the gate consumes
  only the former.

## Feeds

- **SP-7** — no gating data finding may be open for a gate pass.
- **NEXUS** — data-architecture remediation escalates out of PRIMER scope.
