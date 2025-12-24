# ZEC Pooled Solvency — Feasibility Hub

Status: feasibility analysis  
Posture: descriptive, adversarial to assumptions, non-prescriptive  
Scope: cryptographic and verification feasibility under explicit constraints

This repository documents the minimum technical and verification conditions that would need to hold for any ZEC pooled solvency proof system to be considered viable.

It does not propose a product.
It does not recommend deployment.
It does not request funding.
It does not assume that a viable system exists.

Failure, impossibility, or abandonment are acceptable and informative outcomes.

## Purpose

The purpose of this repository is to make feasibility explicit.

Specifically:
- to identify cryptographic primitives required for pooled solvency proofs
- to surface verification and inspection requirements
- to document threat models and failure modes
- to define feasibility gates that must be satisfied before any system could be responsibly considered

This work exists to prevent premature system-building driven by narrative or assumption rather than evidence.

## Scope Constraints

This feasibility analysis is intentionally narrow.

In scope:
- Orchard-only ZEC
- Pooled solvency proofs without Zcash protocol changes
- Externally inspectable and reproducible artifacts
- Explicit adversary modeling and failure analysis

Out of scope:
- Product design or UX
- Custodial business models
- Governance, policy, or regulatory positioning
- Changes to Zcash consensus rules
- Claims about desirability, adoption, or incentives

## Feasibility Gates

The following gates must be satisfied for feasibility to hold.

Failure at any gate is a valid terminal outcome.

### Gate 1: Primitive Support (Non-Spending Continuity)

The protocol must support proving control of shielded reserves across time without:
- revealing nullifiers
- enabling note reuse across epochs
- requiring protocol changes

If no such primitive exists under current Orchard semantics, pooled solvency continuity is infeasible.

### Gate 2: Epoch Safety and Reorg Robustness

Proofs must be bound to a verifiable canonical chain anchor.

A verifier must be able to:
- authenticate the anchor’s inclusion in the canonical chain
- reason about reorg depth and finality assumptions

Proofs anchored to unverifiable or orphaned states are invalid.

### Gate 3: Liability Inclusion Verifiability

If liabilities are claimed:
- inclusion semantics must be explicit
- exclusion must be detectable or named as a trust assumption

Undetectable omission of liabilities is a terminal failure mode.

### Gate 4: Privacy Degradation Bounds

Any privacy degradation introduced by aggregation must be:
- explicitly described
- bounded
- treated as a technical property, not a policy decision

Unbounded or unanalyzed metadata leakage is a feasibility failure.

### Gate 5: Arithmetic and Serialization Integrity

All public inputs must be:
- canonically serialized
- domain-bounded
- arithmetically safe under the chosen field

Silent wraparound, malleability, or ambiguity invalidate proofs.

## What This Repository Provides

- Explicit feasibility gates
- Cryptographic constraint analysis
- Canonical serialization requirements
- Threat models and adversary assumptions
- Verification and inspection profiles
- Negative test vectors and failure conditions

All artifacts are designed to be inspectable, falsifiable, and discardable.

## What This Repository Does Not Provide

- No recommendations to build or deploy
- No endorsements of pooled custody
- No authority claims or representation
- No assumptions of institutional or community support
- No conclusions about economic or social desirability

Absence of a solution is a valid outcome.

## Repository Structure

- notes/  
  Exploratory analysis and feasibility reasoning.

- specs/  
  Canonical specifications required for reproducible proofs.

- threat-model/  
  Explicit adversary models, trust assumptions, and failure conditions.

- verification/  
  Definitions of what must be externally observable to support claims.

- test-vectors/  
  Schemas and examples for validating implementations.

## How to Use This Repository

- Treat each feasibility gate independently.
- Assume failure until demonstrated otherwise.
- Prefer explicit impossibility over optimistic ambiguity.
- Discard any downstream proposal that cannot satisfy these constraints.

This repository is a filter, not a funnel.

## Guardrails

This repository includes a non-claims guardrail to prevent ungrounded endorsements, tool-theater, or false certainty:

- `docs/non-claims.md`

## Versioning

Current version is tracked in `VERSION`.

Versioning intent:
- Patch releases clarify language without changing meaning.
- Any change to feasibility assumptions or threat models requires a version increment.
- Deprecated approaches remain accessible for historical analysis.

## Interpretation and Disagreement

This repository represents one analytical framing of feasibility.

Other researchers may:
- disagree with assumptions
- identify alternative constructions
- reach different conclusions

Disagreement should be expressed through:
- counterexamples
- alternative proofs
- revised threat models

This repository does not arbitrate disputes.

## Related Work

This repository is part of a set of independent, descriptive process artifacts published by ShieldOrder.

- Process Layer Doctrine (PLD)  
  https://github.com/ShieldOrder/process-layer-doctrine  
  Execution hygiene and verification boundaries for governance systems.

- Proposal Disclosure Schema (PDS)  
  https://github.com/ShieldOrder/proposal-disclosure-schema  
  Applicant-side disclosure of assumptions, risks, and verification surfaces.

- Evaluation Surfaces  
  https://github.com/ShieldOrder/evaluation-surfaces  
  Taxonomy separating decision types from legitimacy signals.

Relationship:
- PDS addresses input clarity.
- PLD addresses process hygiene.
- Evaluation Surfaces addresses evaluation semantics.
- This repository addresses technical feasibility under strict constraints.

Each repository is standalone, non-authoritative, and independently discardable.

## License

CC0
