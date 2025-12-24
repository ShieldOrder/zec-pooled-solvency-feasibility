# Threat Model: Anchor Forking and Non-Canonical State
Status: threat model addendum
Posture: descriptive, adversarial to assumptions, non-prescriptive
Scope: chain anchoring, reorgs, and verifier trust model

## Summary

Solvency proofs typically bind to a chain state anchor (for example, a commitment tree root at some height).
If an anchor is not bound to the canonical chain tip under a defined trust model, proofs can be generated against non-canonical history.

## Adversary model

- Operator can choose which chain view to present.
- Operator can generate proofs using orphaned blocks or private forks.
- Verifier may be offline or may lack independent chain verification.

## Failure mode

### FM-A1: Proofs over non-canonical anchors

A proof can verify correctly with respect to an anchor that does not correspond to the canonical chain.
In that case, PASS/FAIL only means "consistent with provided data," not "true on main chain."

## Reorg sensitivity

Even honest proofs can become stale under reorgs.
Any construction must specify:
- what depth of reorg is tolerated
- how anchor finality is defined
- how stale proofs are treated

## Explicit failure condition

The feasibility target fails if the verifier cannot, under a stated model, obtain credible evidence that the anchor corresponds to the canonical chain.

## Required mitigation class (must pick one)

- Trustless: header chain / light client style evidence sufficient to bind anchor
- Trusted: explicitly named checkpoint source and explicit trust assumption

If neither is defined, verification is underspecified.
EOF
