---
module: MASTER
title: "Process-First AI Readiness Assessment — Master Prompt"
framework: PRIMER
version: 1.0.0
feeds: [SP-1, SP-2, SP-3, SP-4, SP-5, SP-6, SP-7, SP-8, SP-9, SP-10]
consumes: []
schema: null
---

# Master Prompt — Process-First AI Readiness Assessment

Use this to generate a complete, first-draft Process-First AI Readiness
Assessment in a single pass — then use the ten supporting modules to deepen,
corroborate, and defend each layer. The master output is always a draft:
its evidence classifications are predominantly STATED until the SP modules
promote them.

## Intake Variables — confirm all six before running

| Variable | Description |
|---|---|
| `[Target Organization]` | The organization or business unit being assessed |
| `[Process Scope]` | Single department / cross-functional value stream / whole-of-business census |
| `[Documentation Maturity]` | none / partial-informal / partial-formal / mature-but-stale |
| `[Automation Ambition]` | task-level assist / workflow automation / autonomous AI agents / undecided |
| `[Decision Stakeholder]` | Who owns the automation investment decision (COO / CIO / owner / transformation lead) |
| `[Evidence in Hand]` | Existing SOPs, system exports, org charts, ticketing data, prior process maps |

## Calibration Rules

- If `[Documentation Maturity]` is **none** or **partial-informal**: weight
  SP-1 and SP-2 heavily; treat every existing process description as STATED.
- If `[Automation Ambition]` is **autonomous AI agents**: raise the readiness
  bar — decision-logic completeness (SP-3) and data-dependency quality (SP-4)
  become gating criteria, not advisory findings.

## The Prompt

> **Goal**: Generate a structured, comprehensive Process-First AI Readiness
> Assessment for `[Target Organization]` across `[Process Scope]`, calibrated
> to `[Documentation Maturity]` and `[Automation Ambition]`, defensible to
> `[Decision Stakeholder]` — producing a process inventory, an SOP register
> built to the PRIMER documentation standard, a decision-logic and
> data-dependency audit, a metrics baseline, and a volume-weighted automation
> prioritization with explicit evidence classification.
>
> **Role**: Act as a fractional Chief Data Officer and operational advisor.
> You specialize in preparing organizations for intelligent automation by
> documenting, auditing, and scoring their core operational processes before
> any AI investment. Your methodology is practical and designed for adoption
> by business teams — no BPMN or Six Sigma jargon unless simplified and
> explained. You are tool-agnostic: no software recommendations, no vendor
> names, no code.
>
> **Instructions**: Confirm the six intake values before running. Apply the
> calibration rules above. Tag every quantitative cell with its evidence
> class. Where evidence is absent, say so — a gap named is worth more than a
> number invented.

## Output Contract

**`[Target Organization]` — Process-First AI Readiness Assessment**
*Version 1.0 | Draft | `[Date]` | Scope: `[Process Scope]` | Ambition: `[Automation Ambition]`*

### 1. Executive Readiness Verdict

A single committee-ready paragraph: overall readiness grade; processes
discovered vs. documented to standard; top three automation candidates with
matrix placement; top three readiness gaps blocking deployment; recommended
sequence. State the evidence classification of the headline grade explicitly.

### 2. Process Inventory (Census Register)

| # | Process Name | Owner | Function | Frequency | Est. Volume/Mo | Documentation Status | Evidence Class |
|---|---|---|---|---|---|---|---|

### 3. SOP Register Summary

Per documented process: goal, inputs, outputs, step count, decision-rule
count, known exceptions, claimed-vs-performed gap flag.

### 4. Decision Logic Exposure

| Process | Decision Point | Rule (If → Then) | Codified or Tribal? | Exception Path Documented? | Class |
|---|---|---|---|---|---|

Flag every decision currently resident in one person's head.

### 5. Data Dependency Audit

Every input and output classified by source system, format, quality, and
provenance. Single-person data dependencies and unversioned-spreadsheet
dependencies flagged as automation blockers.

### 6. Metrics Baseline

Cycle time, cost, quality/error rate, and rework rate per process — with the
measurement method stated. Processes with no measurable baseline flagged:
they cannot enter the automation queue until one exists.

### 7. Bottleneck & Friction Map

Where work queues: approval loops, manual handoffs, review gates, rework
cycles. Each bottleneck classified as *structural* (the process requires it)
or *incidental* (a workaround that calcified).

### 8. Automation Prioritization Matrix

| Process | Impact (1–5) | Complexity (1–5) | Volume Weight | Quadrant | Readiness Gate Passed? | Class |
|---|---|---|---|---|---|---|

Quadrants: **Automate Now** · **Design Carefully** · **Quick Wins If Idle** ·
**Leave Alone**. Every placement traceable to documented volume and
complexity drivers.

### 9. Inter-Process Value Stream

Output→input linkage map; end-to-end chains; upstream failures that propagate
downstream; the two or three processes whose automation unblocks the most
downstream value.

### 10. Readiness Gaps & Remediation Register

Every gap blocking automation — undocumented decision logic, missing
baselines, fragile data dependencies, single-person knowledge — with owner,
remediation action, and effort estimate.

### 11. Sequence Logic — The Next Two Decisions

The matrix is the first decision; name the next two explicitly (pilot-process
selection and its success gate; the process-governance model that keeps
documentation current after go-live).

### 12. Evidence Register & Classification Summary

A consolidated register of every claim cited, with source, date, method, and
classification. The readiness committee must be able to audit any score back
to a row in this register.

## Cross-References

- Evidence standard: [../docs/evidence-classification.md](../docs/evidence-classification.md)
- Gate criteria: [../docs/readiness-gate.md](../docs/readiness-gate.md)
- Scoring model: [../docs/scoring-model.md](../docs/scoring-model.md)
- Deepen each section with [SP-1](sp-01-process-discovery-census.md) through
  [SP-10](sp-10-roadmap-governance.md); SP-9 runs standalone.
