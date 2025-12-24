# ZEC Pooled Solvency — Feasibility Hub

Version: v0.1.x
Status: feasibility analysis
Posture: descriptive, adversarial to assumptions, non-prescriptive
Scope: cryptographic and verification feasibility under explicit constraints

This repository specifies the minimum cryptographic and governance conditions that would need to hold before any pooled ZEC custody system could be considered acceptable.
It does not assume that pooled custody, yield generation, or capital aggregation is desirable or appropriate.

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

## Likely infeasibility under current constraints

Preliminary analysis suggests this may not be feasible under the current constraints.

The central problem is Gate 1: proving control of Orchard reserves across multiple epochs without:
- revealing nullifiers (privacy degradation)
- enabling note reuse (security failure)
- requiring protocol changes (out of scope)

Orchard notes are designed to be spent exactly once, with nullifiers enforcing that property.
A continuity claim that prevents reuse without revealing linkage may require primitives that do not exist under current Orchard semantics.

Common approach classes and why they violate constraints:
- protocol extensions (out of scope)
- trusted hardware attestations (adds trust assumptions)
- probabilistic fingerprinting (detectable signals, not cryptographic guarantees)
- nullifier revelation (privacy collapse)

If no viable approach exists, the correct conclusion is:
pooled solvency proofs are infeasible under the stated constraints.

This repository exists to determine whether that conclusion is correct.

## Scope constraints

This feasibility analysis is intentionally narrow.

In scope:
- Orchard-only ZEC
- pooled solvency proofs without Zcash protocol changes
- externally inspectable and reproducible artifacts
- explicit adversary modeling and failure analysis

Out of scope:
- product design or UX
- custodial business models
- governance, policy, or regulatory positioning
- changes to Zcash consensus rules
- claims about desirability, adoption, or incentives

## Primary adversaries

This analysis assumes the following threat actors:

1. Malicious operator
Controls prover infrastructure and liability accounting and attempts to publish false solvency artifacts.

2. Cross-epoch note reuse
Attempts to reuse the same reserve notes across epochs to inflate apparent solvency.

3. Anchor spoofing and forking
Attempts to anchor proofs to non-canonical or unverifiable chain state.

4. Verifier implementation bugs
A reference verifier accepts invalid proofs or misparses inputs.

5. Collusion and selective acceptance
Prover and a subset of verifiers coordinate to present false acceptance.

6. Timing and metadata analysis
Passive observers infer information from proof timing, cadence, or aggregate values.

7. Key compromise
Compromise of reserve-control keys results in reserve theft regardless of proof soundness.
Operational key management is acknowledged but is out of scope for cryptographic feasibility.

Detailed adversary modeling is in threat-model/.

## What feasible means

Feasibility is not a gradient. A system is either feasible or it is not.

For pooled solvency proofs to be feasible under this analysis, all of the following must hold:

1. Technical possibility
Required primitives exist or can be composed from existing primitives without protocol changes.

2. Practical implementability
Circuit complexity, proving time, and verification cost are bounded within practical limits.

3. Security under adversarial conditions
The threat model holds under realistic adversary capabilities.

4. Explicit tradeoff acknowledgment
Where properties cannot be achieved simultaneously, tradeoffs are stated explicitly and bounded.

Failure at any level is a valid terminal outcome.

## Why this work exists

Pooled custody systems with solvency claims periodically appear.

These efforts often fail due to:
- reliance on operator attestations rather than verifiable artifacts
- opaque accounting that cannot be externally inspected
- unacknowledged privacy regressions at service boundaries
- implicit trust assumptions not made explicit
- feasibility assumptions that are not analyzed

This repository inverts the question.

Instead of:
should we build a pooled solvency system

We ask:
what must be provably true for such a system to not be fraudulent by construction

If the answer is that nothing can satisfy these requirements, non-deployment is the correct outcome.

## Feasibility gates

The following gates must be satisfied for feasibility to hold.

Failure at any gate is a valid terminal outcome.

### Gate 1: Primitive support (non-spending continuity)

Status: likely infeasible under stated constraints

The protocol would need to support proving control of shielded reserves across time without:
- revealing nullifiers (breaks privacy)
- enabling note reuse across epochs (breaks security)
- requiring protocol changes (out of scope)

If no such construction exists under current Orchard semantics, Gate 1 FAILs and pooled solvency continuity is infeasible under these constraints.

This is the primary research question this repository addresses.

### Gate 2: Epoch safety and reorg robustness

Proofs must be bound to a verifiable canonical chain anchor.

A verifier must be able to:
- authenticate the anchor’s inclusion in the canonical chain under an explicit anchor acquisition model
- reason about reorg depth and finality assumptions

Proofs anchored to unverifiable or orphaned states are invalid.

### Gate 3: Liability inclusion verifiability

Status: fundamental tension between privacy and verifiability

If liabilities are claimed, the system must address:
- inclusion semantics (who is in the liability set)
- exclusion risk (how omission is prevented or bounded)

Liability exclusion is cryptographically undetectable without compromising privacy or introducing trusted parties.

Available approach classes and their tradeoffs:
- publish liabilities publicly: verifiable completeness, privacy loss
- user-verifiable inclusion proofs: requires identifiers and distribution model, privacy and linkage risk
- trusted auditor: completeness via trust assumption
- accept undetectable exclusion: system proves reserves >= claimed liabilities, but cannot prove all liabilities are included

This gate requires stating which property is sacrificed:
privacy, trustlessness, or completeness.

Unacknowledged exclusion risk is a terminal failure mode.

### Gate 4: Privacy degradation bounds

Any privacy degradation introduced by aggregation must be:
- explicitly described
- bounded under a stated threat model
- treated as a technical property, not a policy decision

Unbounded or unanalyzed metadata leakage is a feasibility failure.

### Gate 5: Arithmetic and serialization integrity

All public inputs must be:
- canonically serialized
- domain-bounded
- arithmetically safe under an explicitly stated arithmetic domain

Silent wraparound, malleability, or ambiguity invalidate proofs.

## What this repository provides

- explicit feasibility gates
- cryptographic constraint analysis
- canonical serialization requirements
- threat models and adversary assumptions
- verification and inspection profiles
- negative test vectors and failure conditions

All artifacts are designed to be inspectable, falsifiable, and discardable.

## What this repository does not provide

- no recommendations to build or deploy
- no endorsements of pooled custody
- no authority claims or representation
- no assumptions of institutional or community support
- no conclusions about economic or social desirability

Absence of a solution is a valid outcome.

## Repository structure

- docs/
  guardrails and scope boundaries

- notes/
  exploratory analysis and feasibility reasoning

- specs/
  canonical specifications required for reproducible proofs

- threat-model/
  explicit adversary models, trust assumptions, and failure conditions

- verification/
  definitions of what must be externally observable to support claims

- test-vectors/
  schemas and examples for validating implementations

## How to use this repository

- treat each feasibility gate independently
- assume failure until demonstrated otherwise
- prefer explicit impossibility over optimistic ambiguity
- discard any downstream proposal that cannot satisfy these constraints

This repository is a filter, not a funnel.

## Guardrails

See docs/non-claims.md for language and attribution constraints.

## Versioning

Current version is tracked in VERSION.

Versioning intent:
- patch releases clarify language without changing meaning
- any change to feasibility assumptions or threat models requires a version increment
- deprecated approaches remain accessible for historical analysis

## Interpretation and disagreement

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

## Related work

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
- PDS addresses input clarity
- PLD addresses process hygiene
- Evaluation Surfaces addresses evaluation semantics
- This repository addresses technical feasibility under strict constraints

Each repository is standalone, non-authoritative, and independently discardable.

## License

CC0
EOF
