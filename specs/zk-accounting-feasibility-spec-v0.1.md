# ZK Accounting Feasibility Spec v0.1

Goal:
Determine whether pooled ZEC solvency can be proven cryptographically without social trust.

Scope constraints:
- ZEC-only
- Orchard-only
- No external venues
- No protocol changes

### Statements to prove (per epoch)

1. Ledger correctness  
A committed ledger of user balances is well-formed and sums to the declared total liabilities.

2. Reserve control  
The prover controls Orchard notes whose total value is at least the declared reserves.

3. Solvency  
Declared reserves are greater than or equal to declared liabilities.

### Public artifacts

Each proof publication must include:
- Accounts Merkle root
- Total liabilities
- Total reserves
- Reference chain height or finality declaration
- Proof artifact
- Circuit identifier
- Verifying key fingerprint

### Primary feasibility risk

Cross-epoch Orchard note reuse.

A construction that allows the same Orchard notes to be reused across multiple solvency epochs without detection is considered unsound.

Phase 1 feasibility work must either:
- prevent note reuse, or
- make reuse publicly detectable through commitments or linkage

Failure to establish a credible mitigation path fails feasibility.

### Reorg sensitivity

Height-anchored proofs must declare their finality assumptions.

If chain reorgs can invalidate or ambiguate solvency claims without deterministic detection, the construction fails feasibility.
