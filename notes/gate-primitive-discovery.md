# Gate 0: Primitive Discovery
Status: feasibility gate
Posture: descriptive, adversarial to assumptions, non-prescriptive
Scope: protocol and primitive constraints for "unspent reserve" claims

This document defines the first feasibility gate: whether the current Zcash protocol and available primitives can support the core solvency claim under this repository's constraints.

This gate exists to prevent downstream work that implicitly assumes a missing primitive.

## Objective

Determine whether a verifier can obtain credible evidence that "reserves are unspent" (or an equivalent condition) under the constraints:

- Orchard-only
- no protocol changes
- externally inspectable artifacts
- adversarial operator model

## Pass condition

PASS only if there exists a construction that:

- binds reserve claims to a well-defined on-chain state
- prevents trivial "prove at time t, spend at time t+1" failure
- avoids privacy collapse that defeats the stated posture
- does not require protocol changes

A construction may be partial, but it must specify:
- what is proven
- what is not proven
- what assumptions are required
- what the verifier must check

## Fail condition

FAIL if the core claim requires any of:

- revealing nullifiers (or equivalent linkage) that permanently degrades privacy beyond the repository's tolerances
- protocol support not currently available (new commitments, new proof types, consensus changes)
- unverifiable trust anchors (social attestations as a substitute for defined verification)

## Required outputs

A PASS or FAIL decision must be backed by artifacts, not narrative.

Acceptable artifacts include:

- references to concrete protocol properties
- explicit construction sketches with clearly named assumptions
- demonstrations of impossibility under stated constraints
- minimal counterexamples showing why a claimed construction fails

## Notes

This gate does not decide desirability.
It decides whether the repository's constraints are internally satisfiable.

If this gate FAILs, the correct action is to halt or revise constraints.
EOF
