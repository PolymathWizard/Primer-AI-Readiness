---
module: SP-6
title: "Human Bottleneck & Friction Analysis"
framework: PRIMER
version: 1.0.0
feeds: [SP-7, SP-10]
consumes: [SP-2]
schema: null
---

# SP-6 — Human Bottleneck & Friction Analysis

**Goal**: Map where work actually slows — approval loops, review gates,
handoffs, rework — and classify each bottleneck as **structural** (the
process requires it) or **incidental** (a workaround that calcified).

The two classes have opposite automation implications, and this is the
highest-leverage classification in the framework:

- Automating away a **structural** bottleneck (regulatory review,
  segregation-of-duties approval) creates a compliance incident.
- Preserving an **incidental** bottleneck (the one person who knows the
  spreadsheet) in the automated design fossilizes a workaround.

Misclassifying one as the other is the costliest error this module prevents.

## Intake

- SP-2 SOP records (section 10: human touchpoints)
- Queue data, approval logs, rework records where available
- Operator interviews focused on "where does work wait, and on whom?"

## Output Contract — Bottleneck & Friction Map per Process

### 1. Queue Point Register

| Queue Point | Average Wait | Measured or STATED | Waits On (Role) | Reason |
|---|---|---|---|---|

### 2. Structural vs. Incidental Classification

Every queue point classified, with rationale. Structural bottlenecks become
human-in-the-loop design inputs (SP-10); incidental bottlenecks become
remediation targets. When classification is genuinely uncertain, say so and
name what evidence would resolve it — do not default to either class.

### 3. Approval Chain Audit

Every approval step, with the question that separates control from ritual:
**audit the last N approvals — how many changed the outcome?** An approval
that has approved 200 consecutive requests unchanged is a ritual wearing a
control's badge. Record N, the change count, and the class.

### 4. Rework Loop Analysis

Where output bounces back, how often, and the upstream cause. Rework
frequency is an impact driver; rework *cause* is usually an SP-3 ambiguity
or an SP-4 data-quality finding in disguise — cross-reference it.

### 5. Bottleneck-to-Matrix Feed

Each significant bottleneck expressed as an impact driver for the SP-7
matrix: the time or cost it represents, per period, with its evidence class.

## The Prompt

> You are mapping the bottlenecks and friction in `[Process Name]` from its
> SP-2 record, queue data, and operator interviews. Register every point
> where work waits, with the wait time honestly classified as measured or
> STATED. Classify every bottleneck structural or incidental with rationale.
> Audit each approval chain by asking how many of the last N approvals
> changed the outcome. Trace rework loops to their upstream causes,
> cross-referencing SP-3 ambiguities and SP-4 data findings where they are
> the true cause. Express each significant bottleneck as a quantified impact
> driver for the prioritization matrix.

## Quality Bar

- No queue point without an actor role — work waits *on someone*.
- Every structural classification cites the requirement (regulation, control,
  contract) that makes it structural.
- Every approval chain has an outcome-change count or a stated reason one
  could not be obtained.
- Rework causes cross-referenced, not free-floating.

## Feeds

- **SP-7** — bottleneck impact drivers feed the impact score.
- **SP-10** — structural bottlenecks feed human-in-the-loop pilot design;
  a structural bottleneck automated away requires an explicit
  control-replacement note.
