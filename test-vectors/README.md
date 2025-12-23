# Test Vectors

This directory defines feasibility-level test vectors.

Test vectors are mandatory artifacts for any Phase 1 feasibility prototype.

### Requirements

Each test vector must include:
- Canonical artifact bundle
- Declared expected result: PASS or FAIL
- Explicit finality declaration
- Deterministic verification outcome

### Minimum coverage

At minimum, the following cases must be represented:
- One positive solvency proof
- Negative case: inflated liabilities
- Negative case: reduced reserves
- Negative case: altered ledger root
- Negative case: cross-epoch note reuse attempt
- Negative case: reorg-induced ambiguity

Vectors that do not fail deterministically under negative conditions are invalid.
