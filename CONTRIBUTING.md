# Contributing to PRIMER

PRIMER is a living framework repository. Corrections, questions, and content
suggestions are welcome — from practitioners running the framework, operators
whose processes it documents, and builders extending the agent configuration.

## Ways to Contribute

### Report an error or correction

Open a [Correction issue](../../issues/new?template=correction.yml). Include the
file affected, the error, your suggested correction, and — in keeping with the
framework's own standard — the evidence class of your correction. A correction
backed by a retrievable source (VERIFIED) merges faster than a STATED one.

### Ask a question

Open a [Question issue](../../issues/new?template=question.yml). Check
[docs/faq.md](docs/faq.md) first; many methodology questions are answered there.

### Suggest new content

Open a [Suggestion issue](../../issues/new?template=suggestion.yml). State what
you'd add, why, where it belongs, and any supporting evidence.

### Submit changes directly

1. Fork the repository and create a branch: `git checkout -b docs/short-description`
2. Make your changes. Content files target 100–300 lines.
3. Run the validators locally:
   ```bash
   pip install -r tools/requirements.txt
   python tools/validate_schemas.py
   python tools/validate_evidence_tags.py examples/
   pytest tests/
   ```
4. Commit using conventional commits with the `primer` scope (see below).
5. Open a PR — the template checklist walks you through the review criteria.

No GitHub experience? Every Markdown file can be edited from the browser:
open the file, press the pencil icon, make the change, and GitHub will create
the fork, branch, and PR for you.

## Commit Convention

Conventional commits with framework-specific scopes:

```
<type>(primer): <description>

Types: feat | fix | docs | schema | agent | prompt | tool | test | ci | chore
```

Examples:

- `prompt(primer): tighten SP-3 ambiguity register instructions`
- `schema(primer): add backup_owner field to sop-record schema`
- `agent(primer): raise gate strictness in prioritization subagent`
- `docs(primer): clarify STATED promotion rules in evidence standard`

## Content Standards

- **Prompts** (`prompts/`) are the framework contract. Changes to output
  contracts, gate criteria, or the evidence standard require an ADR.
- **Schemas** (`schemas/`) are the single source of truth for register
  structure. If a prompt and a schema disagree, the schema wins and the
  prompt must be corrected in the same PR.
- **Evidence classification enums** are locked: `VERIFIED`, `CORROBORATED`,
  `UNCORROBORATED`, `INFERENCE`, `STATED`. Adding a tier requires an ADR and
  a major version bump.
- **No client material.** Anything derived from a real engagement stays in
  `engagements/` (gitignored) or is fully fictionalized before entering
  `examples/`.
- Markdown must pass `markdownlint` with the repo's `.markdownlint.json`.

## Label Taxonomy

| Label | Purpose |
|---|---|
| `type:correction` | Error report or factual correction |
| `type:question` | Methodology or usage question |
| `type:suggestion` | Content or feature suggestion |
| `type:agent` | Claude Code agent configuration |
| `type:schema` | Register schema change |
| `status:triage` | Awaiting review |
| `status:accepted` | Approved for action |
| `status:needs-adr` | Requires an Architecture Decision Record |

## Review Process

PRs touching `prompts/`, `schemas/`, `adr/`, or the evidence standard route to
the framework owner via CODEOWNERS. Everything else follows standard review.
CI must pass: markdown lint, schema validation, and the pytest suite.

## License of Contributions

By contributing, you agree your contributions are licensed under the
repository's dual license: MIT for code/schemas/tooling, CC BY 4.0 for content.
