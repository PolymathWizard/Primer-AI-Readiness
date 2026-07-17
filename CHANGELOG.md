# Changelog

All notable changes to the PRIMER framework repository are documented here.
Format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/);
versioning follows [SemVer](https://semver.org/).

## [1.0.0] — 2026-07-15

### Added

- Initial public release of the PRIMER framework repository.
- Master prompt plus ten specialist prompt modules (SP-1 … SP-10) as
  first-class, self-contained prompt files under `prompts/`.
- Claude Code multi-agent configuration: root `CLAUDE.md` orchestrator and
  ten subagent definitions under `.claude/agents/` (CADRE pattern —
  orchestrator on Opus, subagents on Sonnet).
- Five-tier evidence classification standard (VERIFIED / CORROBORATED /
  UNCORROBORATED / INFERENCE / STATED) enforced across every register.
- JSON Schemas for the census register, SOP record, decision rule, matrix
  placement, readiness scorecard, and evidence entry under `schemas/`.
- Validation tooling: schema validator, evidence-tag validator, snapshot
  scorer, and matrix placement engine under `tools/`.
- Conformance test suite (pytest) under `tests/`.
- Fictional end-to-end worked example under `examples/acme-fulfillment/`.
- Architecture Decision Records 0001–0006 under `adr/`.
- Contribution infrastructure: issue forms, PR template, CONTRIBUTING.md,
  label taxonomy, CODEOWNERS.
- CI workflows: markdown lint, schema/prompt validation, test matrix,
  release packaging.
- MkDocs Material publishing configuration.
- Dual licensing: MIT (code/schemas/tooling) and CC BY 4.0 (content).

[1.0.0]: https://github.com/PolymathWizard/Primer-AI-Readiness/releases/tag/v1.0.0
