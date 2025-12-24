# ShieldOrder Research Note 001
## Feasibility Conditions for Pooled ZEC Solvency Proofs

Status: research note  
Scope: cryptographic feasibility and governance hygiene

### Purpose

This note examines whether it is technically and governance-sound to construct a pooled ZEC custody system that is solvent by construction, publicly verifiable without social trust, compatible with Zcash’s privacy model, and achievable without protocol changes.

The goal is clarity, not advocacy. If the conditions cannot be met, the system should not exist.

### Context

Ideas involving pooled custody or delegated ZEC usage surface regularly.  Historically, they fail in predictable ways: reliance on operator attestations, opaque accounting, unacknowledged privacy regressions, or dependence on external venues that reintroduce trust.  This work does not treat yield generation, capital efficiency, or return optimization as requirements or objectives.

Rather than debating desirability, this work asks a narrower question: what would need to be provably true for such a system to avoid being unsound by construction.

### Yield Non-Assumption

This feasibility analysis does not assume that pooled custody should generate yield,
returns, or economic advantage.

If yield is present, it is treated as an external property requiring independent
evaluation and separate admissibility criteria.

Yield considerations do not substitute for solvency, correctness, or verifiability.

### Related and Partial Work

There is no claim of novelty at the component level. Shielded pools, zero-knowledge proofs, and proof-of-reserves techniques exist.

What appears missing is an end-to-end design that satisfies, simultaneously, native shielded custody on the base chain, public cryptographic proof of liabilities and reserves, absence of operator attestations as trust anchors, no protocol changes, and explicit handling of privacy loss at service boundaries.

That gap is treated here as an open feasibility question.

### Non-goals

This work does not attempt to design wallets, products, yield mechanisms, DeFi protocols, governance processes, or user experiences.

### Evaluation posture

Failure is a valid outcome.

In the Zcash ecosystem, declining to ship systems that cannot meet invariants is a form of progress.
