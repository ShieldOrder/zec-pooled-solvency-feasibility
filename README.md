# ZEC Pooled Solvency — Feasibility Hub

Status: feasibility analysis  
Posture: descriptive, non-prescriptive  
Scope: cryptographic and verification feasibility

This repository documents the minimum technical and verification conditions that would need to hold for any ZEC pooled solvency proof system to be considered viable.

It does not propose a product.
It does not recommend deployment.
It does not request funding.
It does not assume that a viable system exists.

Failure to meet feasibility conditions is an acceptable and expected outcome.

## Purpose

The purpose of this repository is to make feasibility explicit.

Specifically:
- to identify cryptographic constraints
- to surface verification requirements
- to document threat models and failure modes
- to define what would need to be provable before pooled custody could be responsibly considered

This work exists to prevent premature system-building driven by narrative or assumption rather than evidence.

## Scope Constraints

This feasibility analysis is intentionally narrow.

In scope:
- Orchard-only ZEC
- Proofs of pooled solvency without protocol changes
- Verifiable, externally inspectable artifacts
- Explicit threat modeling and failure analysis

Out of scope:
- Product design or UX
- Custodial business models
- Governance, policy, or regulatory positioning
- Changes to Zcash consensus rules
- Claims about desirability or adoption

## What This Repository Provides

- Cryptographic feasibility gates
- Canonical serialization specifications
- Threat models and adversary assumptions
- Verification profiles and inspection surfaces
- Test vector schemas for reproducibility

All artifacts are designed to be inspectable, falsifiable, and discardable.

## What This Repository Does Not Provide

- No recommendations to build or deploy
- No endorsements of pooled custody
- No authority claims or representation
- No assumptions of community or institutional support
- No conclusions about economic or social desirability

Absence of a solution is a valid outcome.

## Repository Structure

- notes/  
  Exploratory analysis, open questions, and feasibility reasoning.

- specs/  
  Canonical specifications required for reproducible proofs.

- test-vectors/  
  Schemas and examples for validating implementations.

- threat-model/  
  Explicit adversary models, trust assumptions, and failure conditions.

- verification/  
  Definitions of what must be externally observable to support claims.

## How to Use This Repository

- Treat each section as a feasibility gate.
- Assume failure until demonstrated otherwise.
- Prefer explicit impossibility over optimistic ambiguity.
- Discard any downstream proposal that cannot satisfy these constraints.

This repository is a filter, not a funnel.

## Versioning

Current version is tracked in `VERSION`.

Versioning intent:
- Patch releases clarify language or framing without changing meaning.
- Any change to feasibility assumptions or threat models requires a version increment and changelog entry.
- Deprecated approaches remain documented for historical analysis.

## Interpretation and Disagreement

This repository represents one analytical framing of feasibility.

Other researchers may:
- disagree with assumptions
- identify alternative constructions
- reach different conclusions

Disagreement should be expressed through counterexamples, alternative proofs, or revised threat models.

This repository does not arbitrate disputes.

## Related Work

This repository is part of a set of independent, descriptive process artifacts published by ShieldOrder.

Related repositories include:

- **Process Layer Doctrine (PLD)**  
  Defines execution hygiene invariants for governance and funding systems.  
  PLD addresses how decisions are made legible and verifiable.  
  https://github.com/ShieldOrder/process-layer-doctrine

- **Proposal Disclosure Schema (PDS)**  
  A voluntary disclosure template for surfacing assumptions, risks, and verification surfaces in proposals.  
  PDS addresses applicant-side clarity.  
  https://github.com/ShieldOrder/proposal-disclosure-schema

- **Evaluation Surfaces**  
  A taxonomy separating decision types from legitimacy signals to reduce category errors in governance evaluation.  
  https://github.com/ShieldOrder/evaluation-surfaces

Relationship between repositories:

- PDS addresses *input clarity*.
- PLD addresses *process hygiene*.
- Evaluation Surfaces addresses *evaluation semantics*.
- This repository addresses *technical feasibility under strict constraints*.

Each repository is standalone, non-authoritative, and independently discardable.

## License

CC0
