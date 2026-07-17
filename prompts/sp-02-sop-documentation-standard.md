---
module: SP-2
title: "SOP Master Documentation Standard"
framework: PRIMER
version: 1.0.0
feeds: [SP-3, SP-4, SP-5, SP-6, SP-7]
consumes: [SP-1]
schema: ../schemas/sop-record.schema.json
---

# SP-2 — SOP Master Documentation Standard

**Goal**: Document each in-scope process to the PRIMER SOP standard — the
canonical, copy-pasteable record that captures everything an automation
decision (and later, an AI agent) will need to inherit.

The test is simple and unforgiving: **a competent new hire could execute the
process from the record alone.** That is the same test an AI agent must pass.
"We all know how it works" is a disqualifying statement, not a qualifying one.

## Intake

- The SP-1 census register (in-scope rows)
- Process-owner interviews per process
- System evidence where available: logs, timestamps, transaction exports

## Output Contract — One SOP Master Record per Process

Conforms to [sop-record.schema.json](../schemas/sop-record.schema.json).
Template: [../templates/sop-master-record.md](../templates/sop-master-record.md).

1. **Process Name & Owner** — Clear title; accountable person or team; backup
   owner if one exists (**flag if none does** — single-owner processes are a
   knowledge-transfer risk finding).
2. **Goal / Objective** — The specific business outcome, one sentence,
   business language.
3. **Trigger** — The event or condition that starts the process. Distinguish
   *scheduled* from *event-driven* triggers.
4. **Intake / Inputs** — Every data item, document, or request required to
   start: source, format, system of record, who supplies it.
5. **Outputs / Deliverables** — The specific product, record, or outcome:
   format, destination system, who consumes it.
6. **Sequential Steps** — Numbered, one action per step, in operator
   language. Each step names the **actor as a role, not a person**, and the
   system touched.
7. **Decision Rules & Branches** — Every if-then rule inline at the step
   where it occurs, cross-referenced to the SP-3 register.
8. **Exceptions & Edge Cases** — What goes wrong, how often, the recovery
   path. "It never breaks" is a STATED claim requiring corroboration.
9. **Success & Failure Definition** — What done-and-correct looks like; what
   constitutes an error; cross-referenced to SP-5 metrics.
10. **Human Touchpoints & Bottlenecks** — Every manual review, approval, or
    judgment call, cross-referenced to SP-6.
11. **Volume & Frequency** — Runs per period, with the measurement source
    stated.
12. **Claimed-vs-Performed Gap Flag** — Where owner testimony and system
    evidence diverge, state **both versions** and classify each. The gap is a
    primary finding, not a footnote — it is usually where the automation risk
    lives.

## The Prompt

> You are documenting the process `[Process Name]` to the PRIMER SOP
> standard. Interview the owner, then corroborate against system evidence
> where it exists. Produce the twelve-section SOP Master Record. Write every
> step so a competent new hire could execute it without asking anyone
> anything. Name actors by role. Externalize every if-then rule inline and
> cross-reference it to the decision-logic register. Where the owner's
> account and the system evidence diverge, record both versions with their
> evidence classes — do not average them, do not pick one silently.

## Quality Bar

- Zero steps that require unstated context ("process it the usual way").
- Every input has a named source; every output has a named consumer.
- No process passes with an empty exceptions section — probe until something
  surfaces, or record the "never fails" claim as STATED with a corroboration
  plan.
- The claimed-vs-performed flag is present on every record, even when the
  finding is "no divergence detected (CORROBORATED)."

## Feeds

- **SP-3** extracts and classifies the decision rules registered here.
- **SP-4** audits the inputs/outputs registered here.
- **SP-5** attaches baselines to the success/failure definitions here.
- **SP-6** expands the human touchpoints registered here.
- **SP-7** — no process enters the matrix without a complete SP-2 record.
