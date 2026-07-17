---
title: "PRIMER Overview"
description: "What PRIMER is, the problem it exists to solve, and how the framework is organized."
---

# PRIMER Overview

PRIMER — **P**rocess **R**eadiness **I**ntelligence, **M**apping,
**E**valuation & **R**anking — is a structured playbook for discovering,
documenting, scoring, and prioritizing an organization's repeatable processes
before any AI agent or automation investment. It is operated from the
fractional CDO / operational advisor posture and is deliberately
tool-agnostic: no vendor evaluation, no agent construction, no code delivered
to the client.

## The Problem

Organizations under pressure to "deploy AI" point agents at processes that
were never documented, whose decision rules live in individual operators'
heads, whose data flows through emailed spreadsheets, and whose performance
has never been baselined. The result is predictable: **an AI agent pointed at
an undocumented process does not fix the process — it amplifies it.** One
operator's private heuristics become organizational policy; a workaround
calcifies into the automated design; and no one can prove the deployment
improved anything, because nothing was measured before it.

## The Discipline

PRIMER enforces "document first, deploy second" through seven non-negotiable
operating principles:

1. **Document first, deploy second.** No process enters the automation queue
   without a complete SOP record to the PRIMER standard.
2. **The process-as-claimed is not the process-as-performed.** Owner
   testimony enters as STATED until corroborated by system evidence. The gap
   between the two is a primary finding — usually where the automation risk
   lives.
3. **Decision logic is the asset.** Steps are easy; the if-then rules and
   tribal judgment calls are what an agent inherits.
4. **Data dependencies are load-bearing.** A process running on one person's
   emailed spreadsheet is a data-architecture finding first.
5. **Metrics before automation.** No baseline, no auditable improvement claim.
6. **Prioritize by evidence, not enthusiasm.** The queue comes from the
   volume-weighted matrix, not the loudest team.
7. **Evidence classification is non-optional.** Every claim tagged VERIFIED /
   CORROBORATED / UNCORROBORATED / INFERENCE / STATED.

## The Architecture

One master prompt generates a single-pass first draft; ten specialist modules
deepen and defend each layer. SP-9 (the Readiness Snapshot) is the sanctioned
standalone — the commercial entry diagnostic. The repository also ships a
Claude Code multi-agent configuration that operates the full pipeline with
the readiness gate and evidence standard enforced at every handoff.

| Layer | Module | Output |
|---|---|---|
| Discovery | SP-1 | Census register + coverage confidence |
| Documentation | SP-2 | SOP Master Records |
| Logic | SP-3 | Decision-logic register, ambiguity stop-signs |
| Data | SP-4 | Dependency audit, gating findings |
| Measurement | SP-5 | Metrics baseline, comparison design |
| Friction | SP-6 | Bottleneck map, structural/incidental split |
| Ranking | SP-7 | Gated prioritization matrix + rejection log |
| Systems | SP-8 | Value stream map, propagation analysis |
| Diagnostic | SP-9 | Standalone scored snapshot |
| Governance | SP-10 | Roadmap, pilot design, governance model |

## Where PRIMER Sits in the BHIL Ecosystem

- **NEXUS** — SP-4 data-architecture findings escalate to NEXUS when the data
  itself becomes the engagement.
- **VERDICT** — post-deployment improvement claims are audited against the
  SP-5 baseline register.
- **COUNSEL** — the assessment slots into COUNSEL's Diagnose and Map phases.
- **CODEX** — "document our SOPs before we scale / sell / hire" pairs the
  Tier 3 census with the corporate dossier.

## Next

- Run an engagement: [running-an-engagement.md](running-an-engagement.md)
- The evidence standard: [evidence-classification.md](evidence-classification.md)
- The gate: [readiness-gate.md](readiness-gate.md)
- The agents: [agent-operations.md](agent-operations.md)
