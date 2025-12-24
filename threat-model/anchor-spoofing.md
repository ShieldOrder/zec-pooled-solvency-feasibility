# Anchor Spoofing and Non-Canonical Binding

Status: threat model addendum
Posture: descriptive, adversarial to assumptions, non-prescriptive
Scope: failures when a proof is bound to a non-canonical or unverifiable anchor

## Summary

A solvency proof is only meaningful if the verifier can bind its referenced anchor to the canonical Zcash chain under an explicit trust model.

If the anchor cannot be validated, "PASS/FAIL" becomes a statement about an unspecified chain view.

## Adversary capability

An operator (or any proof publisher) may:

- generate proofs against a non-canonical branch
- present an anchor from an orphaned or private fork
- provide a fabricated anchor value with plausible formatting
- exploit verifier limitations if the verifier cannot validate chain inclusion

## Failure modes

### F1. Ghost anchor acceptance
Verifier accepts an anchor without validating inclusion.
Result: proof may be internally consistent but externally meaningless.

### F2. Orphaned-branch anchoring
Proof is generated against a branch that is later orphaned.
Result: historical proofs may appear valid out of context, and disputes become social.

### F3. Epoch ambiguity via anchor drift
Different artifacts for the "same epoch" reference different anchors.
Result: reserve/liability comparisons no longer refer to the same chain view.

## Detection and mitigation (by anchor acquisition model)

This repository requires an explicit anchor acquisition model in the verification profile.

### Model A: Trustless (preferred if available)
A verifier obtains sufficient chain evidence to validate anchor inclusion under standard consensus assumptions.

Mitigation intent:
- anchor is validated against a canonical header chain
- proofs bound to non-canonical anchors are rejected

### Model B: Trusted (allowed if explicitly declared)
A verifier accepts the anchor from a named checkpoint source.

Mitigation intent:
- the trust assumption is explicit and auditable
- disputes reduce to checkpoint trust, not proof logic

If Model B is used, all published proof artifacts must include:
- checkpoint source identity
- checkpoint retrieval method
- timestamp or retrieval context
- explicit statement that the anchor is trusted input

## Stop condition

If no acceptable anchor acquisition model can be declared, solvency proofs are out of scope for this repository under its verification hygiene posture.
EOF
