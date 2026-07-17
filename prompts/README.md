# PRIMER Prompt Modules

This directory is the framework contract: the Master Prompt and ten specialist
modules that constitute PRIMER. Each file is self-contained — frontmatter,
purpose, intake variables, output contract, the runnable prompt, and
cross-references to the modules it feeds and consumes.

## Run Order

| Order | File | Module | Feeds |
|---|---|---|---|
| 0 | [master-prompt.md](master-prompt.md) | Single-pass first draft | All |
| 1 | [sp-01-process-discovery-census.md](sp-01-process-discovery-census.md) | Process Discovery Census | SP-2, SP-7, SP-8 |
| 2 | [sp-02-sop-documentation-standard.md](sp-02-sop-documentation-standard.md) | SOP Master Documentation Standard | SP-3–SP-7 |
| 3 | [sp-03-decision-logic-extraction.md](sp-03-decision-logic-extraction.md) | Decision Logic & Trigger Extraction | SP-7, SP-10 |
| 4 | [sp-04-data-dependency-audit.md](sp-04-data-dependency-audit.md) | Input/Output & Data Dependency Audit | SP-7, NEXUS |
| 5 | [sp-05-metrics-baseline.md](sp-05-metrics-baseline.md) | Metrics Architecture & Baseline Capture | SP-7, VERDICT |
| 6 | [sp-06-bottleneck-friction-analysis.md](sp-06-bottleneck-friction-analysis.md) | Human Bottleneck & Friction Analysis | SP-7, SP-10 |
| 7 | [sp-07-prioritization-matrix.md](sp-07-prioritization-matrix.md) | Automation Prioritization Matrix | SP-10 |
| 8 | [sp-08-value-stream-mapping.md](sp-08-value-stream-mapping.md) | Inter-Process Value Stream Mapping | SP-7, SP-10 |
| 9 | [sp-09-readiness-snapshot.md](sp-09-readiness-snapshot.md) | Process Readiness Snapshot *(standalone)* | Tier-2 bridge |
| 10 | [sp-10-roadmap-governance.md](sp-10-roadmap-governance.md) | AI Readiness Roadmap & Process Governance | Engagement close |

## Deployment Recipes

- **Entry diagnostic (Tier 1):** SP-9 alone.
- **Department assessment (Tier 2):** SP-1 → SP-2 (top 8–12) → SP-3 → SP-4 → SP-7.
- **Enterprise census (Tier 3):** SP-1 → SP-8 in full, sequentially.
- **Governance retainer (Tier 4):** SP-10 operated continuously.

## Ground Rules (apply to every module)

1. Every quantitative cell carries a five-tier evidence tag — see
   [../docs/evidence-classification.md](../docs/evidence-classification.md).
2. STATED claims never directly support a readiness grade, matrix placement,
   or gate pass.
3. Output structure conforms to the matching schema in
   [../schemas/](../schemas/) — the schema wins any disagreement.
4. After each module, confirm with the user before continuing to the next.
