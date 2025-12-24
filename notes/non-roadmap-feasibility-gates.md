# Non-Roadmap: Feasibility Gates

Status: dependency graph, not a timeline  
Posture: descriptive, non-prescriptive  
Scope: feasibility gating only

All steps are conditional. Stopping is an acceptable and correct outcome.

This document does not describe a plan, commitment, or intent to execute work.
It enumerates logical dependency gates that must be satisfied for feasibility to hold.

## Phase 0: Framing

Deliverable:
- This repository and its constraints

Exit:
- If assumptions, scope, or constraints are internally inconsistent, stop.

## Phase 1: Feasibility construction attempt (conditional)

This phase exists only to test whether the feasibility gates can be satisfied
under the stated constraints.

No execution, deployment, or production readiness is implied.

Candidate artifacts (if feasible):
- A construction sketch or circuit outline sufficient to evaluate feasibility
- A verifier definition under an explicit anchor acquisition model
- Canonical negative cases demonstrating failure modes
- Explicit performance bounds, if relevant to feasibility

Primary risk focus:
- Cross-epoch Orchard note reuse
- Ambiguity introduced by chain reorgs or unverifiable anchors

If these risks cannot be prevented or made publicly detectable, feasibility fails.

Exit conditions:
- Unsound or under-specified construction
- Verification dependent on implicit trust
- Unverifiable artifacts
- Inability to define continuity or anchor semantics
- Infeasibility demonstrated under stated constraints

## Phase 2: Adversarial review (if Phase 1 passes)

Independent critique, red-team analysis, and public scrutiny.

## Phase 3: Conditional discussion

No commitments implied.
Any downstream judgment is external to this repository.

This document is not a roadmap.
EOF
