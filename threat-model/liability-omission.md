# Threat Model: Liability Omission and Offset Attacks
Status: threat model addendum
Posture: descriptive, adversarial to assumptions, non-prescriptive
Scope: liability completeness and accounting integrity

## Summary

A solvency system can appear solvent by under-reporting liabilities or offsetting liabilities via malformed accounting.
This document names failure modes where total liabilities becomes a trust anchor.

## Adversary model

- Operator can exclude accounts from liabilities.
- Operator can manipulate internal accounting representations.
- Operator may attempt offsetting via negative balances or wraparound arithmetic.

## Failure modes

### FM-L1: Omitted liabilities

Operator excludes some user accounts from the liability set.
Total liabilities are understated.
Proofs can still verify against the presented set.

### FM-L2: Offset liabilities

Operator injects balancing entries (for example, negative balances or equivalent encoding tricks) to reduce total liabilities.

### FM-L3: Arithmetic wraparound

If arithmetic is performed in a finite field without explicit range constraints, sums may wrap mod p and misrepresent totals.

## Explicit failure condition

The feasibility target fails if:

- liability completeness depends on unverifiable operator honesty, or
- the construction permits offsets, negative representations, or wraparound totals without detection.

## Required mitigation primitives (examples)

- Explicit non-negativity and range constraints for balances
- Sum correctness enforced in-circuit
- User-verifiable inclusion proofs for stated balances
- Clear definition of how total liabilities are derived and checked
EOF
