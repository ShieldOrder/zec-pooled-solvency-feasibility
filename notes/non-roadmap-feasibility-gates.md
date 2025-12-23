# Non-Roadmap: Feasibility Gates

Status: dependency graph, not a timeline

All steps are conditional. Stopping is an acceptable result.

## Phase 0: Framing

Deliverable:
- This repository

Exit:
- If assumptions or framing are flawed, stop.

## Phase 1: Feasibility prototype (if independently and externally funded)

Estimated duration: 2–3 months  
Estimated budget: 50k–100k USD  
Required capability: production Halo 2 experience

Deliverables:
- Halo 2 circuit demonstrating ledger correctness, Orchard reserve control, and reserves >= liabilities
- Deterministic offline verifier with binary PASS or FAIL output
- Canonical test vectors, including negative cases
- Circuit specification with explicit constraints and public inputs
- Performance benchmarks with disclosed hardware context

Primary risk focus:
Cross-epoch Orchard note reuse and ambiguity introduced by chain reorgs. These are known failure modes in height-anchored constructions.

Phase 1 must either prevent these issues or make them publicly detectable.

Finality posture (feasibility surface, not a commitment):
- Proof anchoring must declare its finality assumption (depth threshold or explicit detection model).
- If reorg effects cannot be handled without unacceptable false positives or unverifiable assumptions, stop.

Exit conditions:
- Unsound circuit
- Non-deterministic verification
- Unverifiable artifacts
- Impractical performance
- No credible handling of note reuse or reorg effects
- Budget or duration exceeded by more than 50 percent

## Phase 2: Adversarial review

Security audit, red team exercise, and public scrutiny.

## Phase 3: Conditional discussion

No commitments implied. Ecosystem judgment applies.

This is not a roadmap.
