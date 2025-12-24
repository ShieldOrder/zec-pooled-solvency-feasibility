# Contributing

Status: feasibility analysis artifact  
Posture: descriptive, adversarial to assumptions, non-prescriptive  
Scope: cryptographic and verification feasibility under explicit constraints

This repository examines whether specific cryptographic constructions and verification claims are feasible under stated constraints.

It is not a product effort.
It is not a deployment plan.
It does not assume a viable system exists.

Failure, impossibility, or abandonment are valid and informative outcomes.

## What contributions are for

Contributions are intended to:

- increase rigor
- reduce ambiguity
- surface hidden assumptions
- tighten threat models
- clarify verification boundaries
- identify explicit failure conditions

Contributions should treat feasibility as an open question, not an objective.

## In scope

- Cryptographic soundness analysis
- Proof sketch critique or gap identification
- Threat model critique or expansion
- Deterministic verification analysis
- Canonical serialization review
- Negative or adversarial test vector design
- Reorg, finality, and chain state analysis
- Explicit infeasibility or impossibility arguments

All claims should be grounded in artifacts.

## Out of scope

- Product framing or roadmap discussion
- Wallet or UX considerations
- Integration planning
- Yield, incentive, or economic modeling
- Governance, policy, or regulatory advocacy
- Assumptions of adoption or deployment
- Scope expansion beyond stated feasibility constraints

## Contribution discipline

When contributing:

- state assumptions explicitly
- name trust boundaries
- identify failure modes
- prefer counterexamples over optimism
- treat missing artifacts as blocking defects
- avoid narrative justification in place of evidence

A contribution that weakens feasibility is a successful contribution.

## Disagreement

Disagreement is expected.

Disputes should be expressed through:

- counterexamples
- alternative constructions
- revised threat models
- tighter or conflicting constraints

This repository does not arbitrate conclusions.

## License

CC0
