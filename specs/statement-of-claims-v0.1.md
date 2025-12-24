# Statement of Claims v0.1

Status: claim inventory
Posture: descriptive, non-prescriptive
Scope: define exactly what is being proven, checked, or assumed

This document enumerates the candidate claims this repository discusses.

It does not assert that any claim is achievable under the stated constraints.
It exists to prevent category errors and to support feasibility gating.

## Definitions

- Anchor: a commitment root (or other chain state identifier) that binds a proof to a specific chain view.
- Epoch: a discrete reporting interval for which a proof artifact may be generated.
- Reserve set: the set of shielded notes (or equivalent commitments) treated as backing the pool at an anchor.
- Liability set: the set of account balances (or equivalent representations) treated as obligations at an anchor or epoch.

## Candidate reserve-side claims (R)

### R1. Snapshot reserve magnitude
Claim: At anchor A, a reserve set exists whose value sum is >= X, under the repository's value representation rules.

Status: candidate; depends on Gate 0 and verification profile.

### R2. Reserve membership well-formedness
Claim: The reserve set used for R1 is well-formed under the repository's serialization and validity constraints.

Status: candidate; depends on canonical serialization and circuit/spec constraints.

### R3. Reserve continuity across epochs (strong form)
Claim: Between anchors A and A', the same reserve value backing persists under an explicit continuity definition.

Status: undefined until Gate 0 clarifies whether continuity is expressible without violating constraints.

Notes:
- If continuity cannot be stated precisely under the constraints, this claim is out of scope.
- If continuity is required, the repository must define the exact continuity predicate and its observables.

## Candidate liability-side claims (L)

### L1. Snapshot liability total
Claim: At epoch E (or anchor A), total liabilities sum to X under an explicit representation (domain, encoding, rounding rules).

Status: candidate; requires explicit arithmetic domain and inclusion semantics.

### L2. Individual inclusion proof (per-user)
Claim: A specific user entry U with balance b is included in the liability set committed by root R, with an inclusion proof.

Status: optional; if included, the repository must define:
- what U represents (identifier model)
- what "included" means
- what artifacts the user receives

### L3. Liability completeness (strong form)
Claim: The committed liability set includes all liabilities that should be included, under an explicit completeness definition.

Status: high risk; may be infeasible under privacy constraints.
If infeasible, completeness must be treated as either:
- a named trust assumption, or
- a stop condition.

## Cross-claims (C)

### C1. Solvency inequality
Claim: For the same epoch/anchor pairing, reserve sum >= liability sum.

Status: candidate; only meaningful if:
- reserve claim(s) and liability claim(s) are defined
- anchor binding is meaningful under the verification profile

### C2. Binding consistency across artifacts
Claim: All published artifacts for an epoch are consistent (same anchor, same roots, same domain parameters).

Status: required if any artifacts are published.

## Non-claims

This repository does not claim:
- real-time solvency
- continuous solvency unless continuity is explicitly defined and supported
- absence of metadata leakage
- completeness of liabilities unless explicitly defined and supported
EOF
