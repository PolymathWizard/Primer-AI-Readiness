---
module: SP-3
title: "Decision Logic & Trigger Extraction"
framework: PRIMER
version: 1.0.0
feeds: [SP-7, SP-10]
consumes: [SP-2]
schema: ../schemas/decision-rule.schema.json
---

# SP-3 — Decision Logic & Trigger Extraction

**Goal**: Externalize every decision rule, branch condition, and
tribal-knowledge judgment call in each process — the layer an AI agent
actually inherits — and classify each as codified or tribal.

Steps are easy; the if-then rules, exception paths, and judgment calls are
what automation encodes. Skip this module and the deployment will encode one
operator's private heuristics as organizational policy.

**The single most predictive automation-failure signal PRIMER captures:**
two operators giving different rules for the same condition. Every such
ambiguity is a stop sign until resolved with the process owner.

## Intake

- SP-2 SOP records with inline decision rules
- Access to at least two operators per process where the process has more
  than one operator
- Transaction outcomes for rule verification where available

## Output Contract — Decision Logic Register per Process

Conforms to [decision-rule.schema.json](../schemas/decision-rule.schema.json).

### 1. Rule Extraction Table

| Rule ID | Step | Condition | Rule (If → Then) | Rule Source | Exception Path Documented? | Class |
|---|---|---|---|---|---|---|

Rule source taxonomy: **policy** (written), **habit** (consistent but
unwritten), **individual judgment** (varies by operator).

### 2. Tribal Knowledge Flags

Every rule that exists only in one operator's head: the operator's **role**,
and a knowledge-transfer risk rating (High / Medium / Low) with rationale.

### 3. Ambiguity Register

Decision points where two operators gave different rules for the same
condition. Record both versions verbatim-in-substance, the operators' roles,
and the resolution status. **Unresolved ambiguities block the SP-7 gate.**

### 4. Trigger Taxonomy

Every process trigger classified: **scheduled / event-driven /
threshold-driven / human-initiated**. Automation feasibility differs sharply
by class — scheduled triggers automate trivially; human-initiated triggers
import all the ambiguity of the human.

### 5. Judgment vs. Rule Split

For each decision point, an explicit call: is this genuinely
rule-expressible, or does it require judgment that should remain human? This
split becomes the human-in-the-loop design input for SP-10's pilot design.

### 6. Evidence Classification

Rules confirmed against transaction outcomes are VERIFIED / CORROBORATED;
owner-described rules are STATED.

## The Prompt

> You are extracting the decision logic from the process `[Process Name]`
> using its SP-2 SOP record and operator interviews. Register every decision
> point: condition, rule, source (policy / habit / individual judgment), and
> whether the exception path is documented. Flag every rule resident in one
> person's head with a knowledge-transfer risk rating. Where two operators
> give different rules for the same condition, record both in the ambiguity
> register — do not reconcile them yourself; that resolution belongs to the
> process owner. Classify every trigger. For each decision point, make the
> judgment-vs-rule call explicitly. Tag everything.

## Quality Bar

- Every SP-2 inline rule appears here with a Rule ID — round-trip complete.
- No ambiguity silently resolved by the analyst.
- The judgment/rule split is a decision on every row, never "TBD."
- At least one rule per process tested against transaction outcomes where
  system data exists; the result recorded with its class.

## Feeds

- **SP-7** — the gate requires zero unresolved ambiguities.
- **SP-10** — the judgment/rule split drives human-in-the-loop pilot design.
