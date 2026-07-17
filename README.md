# PRIMER — Process-First AI Readiness Intelligence

> **Document first, deploy second.** PRIMER is a 10-prompt structured playbook — plus a
> multi-agent Claude Code configuration — for discovering, documenting, scoring, and
> prioritizing an organization's repeatable processes *before* any AI agent or automation
> investment. An AI agent pointed at an undocumented process does not fix the process —
> it amplifies it.

**P**rocess **R**eadiness **I**ntelligence, **M**apping, **E**valuation & **R**anking

A [Barry Hurd Intelligence Lab](https://github.com/PolymathWizard) framework.
*Human-Directed. AI-Enabled. Commercially Tested.*

---

## What PRIMER Produces

| Deliverable | Source Module | Format |
|---|---|---|
| Process inventory (census register) | SP-1 | CSV / Markdown, schema-validated |
| Canonical SOP register to AI-readiness standard | SP-2 | Markdown records, schema-validated |
| Decision-logic register (codified vs. tribal) | SP-3 | Markdown + JSON |
| Data dependency & fragility audit | SP-4 | Markdown + JSON |
| Metrics baseline register | SP-5 | Markdown + CSV |
| Bottleneck & friction map | SP-6 | Markdown |
| Volume-weighted automation prioritization matrix | SP-7 | Scored JSON + rendered table |
| Inter-process value stream map | SP-8 | Markdown |
| Process Readiness Snapshot (standalone diagnostic) | SP-9 | Scored 0–10 per process |
| AI readiness roadmap & governance model | SP-10 | Markdown |

Every quantitative cell carries a five-tier evidence classification:
**VERIFIED / CORROBORATED / UNCORROBORATED / INFERENCE / STATED**.
STATED claims never directly support a readiness grade or a gate pass.
See [docs/evidence-classification.md](docs/evidence-classification.md).

## Start Here

- **"What is this and why does it exist?"** → [docs/overview.md](docs/overview.md)
- **"I want to run an assessment."** → [docs/running-an-engagement.md](docs/running-an-engagement.md), then [prompts/](prompts/)
- **"I want the fast standalone diagnostic."** → [prompts/sp-09-readiness-snapshot.md](prompts/sp-09-readiness-snapshot.md)
- **"I want the agents to run it."** → [docs/agent-operations.md](docs/agent-operations.md) and [CLAUDE.md](CLAUDE.md)
- **"How is the matrix scored?"** → [docs/scoring-model.md](docs/scoring-model.md)
- **"What gates a process from automation?"** → [docs/readiness-gate.md](docs/readiness-gate.md)
- **"What does PRIMER deliberately not do?"** → [docs/scope-lock.md](docs/scope-lock.md)
- **"I found an error / have a question."** → [CONTRIBUTING.md](CONTRIBUTING.md)

## Repository Structure

```
PRIMER-Process-First-AI-Readiness/
├── README.md                  # You are here
├── CLAUDE.md                  # Claude Code orchestrator instructions
├── .claude/agents/            # 10 subagent definitions (one per SP module)
├── prompts/                   # Master prompt + SP-1 … SP-10 (the framework contract)
├── docs/                      # Methodology, evidence standard, gate, scoring, FAQ
├── adr/                       # Architecture Decision Records
├── schemas/                   # JSON Schemas for every register and scorecard
├── templates/                 # Copy-paste SOP record, snapshot, and register templates
├── tools/                     # Validators, snapshot scorer, matrix placement engine
├── tests/                     # Conformance tests for scoring and validation logic
├── examples/acme-fulfillment/ # Fictional worked example (end-to-end)
├── engagements/               # Client artifacts — gitignored, never committed
└── .github/                   # Issue forms, PR template, CI workflows
```

## The Framework in 60 Seconds

1. **Discover** every repeatable process — including the shadow ones living in inboxes
   and one operator's habits (SP-1).
2. **Document** each to the PRIMER SOP standard: the record a new hire — and therefore
   an AI agent — could execute from alone (SP-2).
3. **Externalize** the decision logic; flag tribal knowledge and ambiguities (SP-3).
4. **Audit** every data dependency for fragility and provenance (SP-4).
5. **Baseline** cycle time, cost, and quality before any deployment claim (SP-5).
6. **Map** bottlenecks as structural or incidental — they have opposite automation
   implications (SP-6).
7. **Rank** the portfolio on a volume-weighted impact × complexity matrix, then apply
   the readiness gate: matrix position is *potential*; the gate is *permission* (SP-7).
8. **Link** processes into value streams so automation accounts for propagation (SP-8).
9. **Snapshot** 3–5 processes as the standalone entry diagnostic (SP-9).
10. **Govern** the register so documentation doesn't decay back into tribal knowledge
    (SP-10).

## Two Ways to Run PRIMER

**Prompt-driven.** Run the [Master Prompt](prompts/master-prompt.md) for a single-pass
first draft, then deepen with SP-1 through SP-10 sequentially. Each prompt file is
self-contained with intake variables, output contract, and cross-references.

**Agent-driven.** Open this repo in Claude Code. The orchestrator ([CLAUDE.md](CLAUDE.md))
sequences ten specialist subagents ([.claude/agents/](.claude/agents/)) through the full
pipeline, enforcing the readiness gate and evidence classification at every handoff.
Outputs land in `engagements/<id>/` and are validated by [tools/](tools/) before any
deliverable is assembled.

## Commercial Architecture

| Tier | SKU | Scope | Duration |
|---|---|---|---|
| 1 | Process Readiness Snapshot (SP-9) | 3–5 nominated processes | 1–2 weeks |
| 2 | Readiness Assessment | Department census + top 8–12 SOPs + matrix | 4–6 weeks |
| 3 | Enterprise Process Census | Full SP-1–SP-8 build | 8–12 weeks |
| 4 | Process Governance Retainer | SP-10 operated continuously | Ongoing |

Details: [docs/commercial-architecture.md](docs/commercial-architecture.md)

## License

- Code, schemas, and tooling: [MIT](LICENSE)
- Documentation and prompt content: [CC BY 4.0](LICENSE-CONTENT)

## Attribution

Framework and methodology by Barry Hurd, Barry Hurd Intelligence Lab (BHIL).
PRIMER pairs with the BHIL framework ecosystem: NEXUS (data architecture),
VERDICT (integrity audit), COUNSEL (engagement structure), and CODEX (corporate dossier).

*Human-Directed. AI-Enabled. Commercially Tested.*
