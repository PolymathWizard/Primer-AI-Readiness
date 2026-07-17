---
title: "FAQ"
description: "Common questions about running PRIMER, the evidence standard, the gate, and the agents."
---

# Frequently Asked Questions

## Methodology

### Can I skip the census and just document the processes the client names?

Only in Tier 1 (SP-9), where nomination is the design. In Tier 2+, no — a
census that starts from the client's list optimizes the visible portion of
the operation and misses the shadow processes, which are typically the
highest-fragility items. If budget forces a partial census, state the
coverage gaps explicitly; false completeness is worse than known
incompleteness.

### The client insists a process "never fails." How do I record that?

As STATED, verbatim in substance, with a corroboration plan (exception logs,
rework records, or a claimed-vs-performed spot check). "Never fails" is the
most common disguised estimate in process work.

### Two operators gave me different rules for the same condition. Can I pick the more senior operator's version?

No. Record both in the ambiguity register and route the resolution to the
process owner. Automating an ambiguous rule silently chooses one operator's
version as policy — the single most predictive automation-failure signal the
framework captures.

### Can the matrix be built on estimated volumes?

Yes — and it ships flagged as **provisional**, with the instrumentation plan
attached. Estimates are allowed; disguised estimates are not.

### A process scored "Automate Now" but failed the gate. Which wins?

The gate, always. Matrix position is potential; the gate is permission. The
failed criteria go to the remediation register — for a high-impact process,
that remediation list is often the most valuable finding in the assessment.

## Evidence Standard

### What promotes a STATED claim?

A second independent source (→ CORROBORATED) or direct inspection /
retrievable primary source (→ VERIFIED). Independence matters: two operators
trained by the same person are one source.

### Is analyst reasoning worth anything?

Yes — as INFERENCE, with the method stated. Reasoning without a visible
chain is UNCORROBORATED at best. Confidence is not a class.

## Commercial

### Can SP-9 run inside a Tier 2 engagement to save time?

No. SP-9 is the standalone entry diagnostic; inside Tier 2+ its job is done
properly by SP-1 through SP-5. Using the snapshot as a shortcut inside a
full assessment produces snapshot-grade evidence under assessment-grade
claims.

### The client wants a vendor recommendation in the deliverable. Now what?

Name the boundary (scope lock, deliberate), name the destination (tool
selection belongs downstream), capture the demand in the roadmap. A
readiness assessment with a vendor name in it becomes a sales document, and
every classification in it becomes arguable.

## Agents

### Do the agents run the whole engagement autonomously?

No. The orchestrator pauses at a human checkpoint after every module.
PRIMER is human-directed by design — the agents produce registers; humans
own resolutions, sign-offs, and the engagement relationship.

### What stops the gatekeeper agent from passing a process it shouldn't?

Two enforcement points, one rule source: the agent must compute placements
via `tools/matrix_placement.py` (which refuses gate passes on unresolved
ambiguities, open gating findings, missing baselines, or STATED support),
and the orchestrator independently re-runs the check before accepting the
output.

### Can I run the agents against my own org without a client engagement?

Yes — that's the internal-lab deployment mode. Same workspace convention
(`engagements/<id>/`), same rules. Practicing on your own processes is also
the fastest way to internalize the claimed-vs-performed discipline.
