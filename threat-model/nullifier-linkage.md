# Threat Model: Nullifier Linkage and "Unspent Reserve" Claims
Status: threat model addendum
Posture: descriptive, adversarial to assumptions, non-prescriptive
Scope: privacy and soundness constraints of non-spend evidence

## Summary

A pooled solvency claim often requires evidence that reserve notes remain unspent.
In Zcash shielded systems, "non-spend" evidence can collide with privacy because spentness is typically detected via nullifiers.

This document names the failure mode where proving non-spendability requires revealing information that creates durable linkage.

## Adversary model

- Operator is malicious or partially malicious.
- Operator can time proofs strategically.
- Operator may accept privacy degradation if it benefits them.
- External observers may perform long-horizon correlation.

## Failure mode

### FM-N1: Linkage-by-spentness evidence

If the construction requires revealing nullifiers (or equivalent identifiers) to demonstrate non-spendability, it creates durable linkage between reserve notes and future spends.

This can:
- permanently tag reserve notes
- enable correlation of pool behavior over time
- degrade privacy for reserve management and withdrawals

## Soundness caveat

A proof that only establishes "reserves existed at anchor A" without constraining post-proof spend is not a solvency proof.
It is a point-in-time existence statement.

## Explicit failure condition

The feasibility target fails if the only known path to "unspent reserves" under constraints requires disclosing nullifiers or equivalent linkage that creates durable traceability.

## Acceptable outcomes

- Explicit acknowledgement that privacy degradation is out of bounds and the approach halts
- Revision of constraints (if and only if the repository scope is updated accordingly)
- Protocol-change requirement documented as infeasible under current constraints
EOF
