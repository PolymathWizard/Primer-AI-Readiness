---
title: "Evidence Classification Standard"
description: "The five-tier, non-negotiable evidence classification applied to every claim in every PRIMER output."
---

# Evidence Classification Standard *(Non-Negotiable)*

Every output cell, claim, input, and matrix placement in a PRIMER engagement
is tagged with exactly one of five classes. The classification appears next
to every quantitative cell in every output — the readiness committee sees the
class, not just the score.

## The Five Tiers

| Class | Definition | Example |
|---|---|---|
| **VERIFIED** | Primary source, named, dated, retrievable; or directly observed / system-inspected | Ticket-system export showing 412 runs/month; direct observation of the close process |
| **CORROBORATED** | Two or more independent sources agree | Owner-described volume matches system log count |
| **UNCORROBORATED** | Single source, undated, or unnamed | One operator's recollection of an exception rate, no log available |
| **INFERENCE** | Analyst reasoning from incomplete data, method stated | Cycle time inferred from timestamp gaps across a 20-run sample |
| **STATED** | Self-reported claim by a process owner, vendor, or stakeholder — quarantined from the recommendation layer until corroborated | "This process never fails"; "everyone follows the same steps"; vendor-claimed automation fit |

The enum is locked in
[schemas/evidence-classification.schema.json](../schemas/evidence-classification.schema.json).
Adding or renaming a tier requires an ADR and a major version bump.

## The STATED Quarantine

STATED claims **never directly support** a readiness grade, a matrix
placement, or a gate pass. They support them only after promotion to
CORROBORATED or VERIFIED.

Promotion paths:

- **STATED → CORROBORATED**: a second independent source agrees (another
  operator, a system log, a document produced before the engagement began).
- **STATED → VERIFIED**: direct inspection or a retrievable primary source
  confirms the claim.
- **STATED → (stays STATED)**: no corroboration found. The claim remains in
  the record with its class visible; anything built on it is flagged
  provisional.

Independence matters: two operators who learned the process from the same
person are one source wearing two badges.

## Rules of Application

1. **Estimates are allowed; disguised estimates are not.** A volume figure
   from an owner's memory is STATED. The matrix can be built on STATED
   inputs, but it ships flagged as provisional with the instrumentation plan
   attached.
2. **INFERENCE requires a stated method.** Reasoning without a visible chain
   is UNCORROBORATED at best.
3. **Analyst confidence is not a class.** "I'm pretty sure" upgrades nothing.
4. **"It never breaks" is always STATED.** Absence-of-failure claims are the
   most common disguised estimates in process work.
5. **Self-assessment gets the same treatment.** A coverage confidence score
   without named gaps is a STATED claim about the analyst's own work.
6. **The classification travels with the datum.** A VERIFIED volume figure
   quoted in a summary paragraph is still VERIFIED; a summary that blends
   VERIFIED and STATED figures into one number takes the lower class.

## Why This Is the Product

Organizations do not pay for a transcription of what they told the advisor.
They pay for the documented distance between what they believe happens
(STATED) and what the evidence shows (VERIFIED) — the claimed-vs-performed
gap. The classification standard is what makes that gap visible, auditable,
and defensible in front of the people whose testimony it corrects.

## Tooling

[tools/validate_evidence_tags.py](../tools/validate_evidence_tags.py) scans
engagement and example artifacts for untagged quantitative claims and invalid
class values. CI runs it against `examples/` on every PR.
