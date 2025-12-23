# ShieldOrder Feasibility Hub
## ZEC Pooled Solvency Proofs

Status: pre-release draft for January community review  
Scope: cryptographic feasibility and governance hygiene

This repository is intentionally narrow.

It is not a product, proposal, funding request, or deployment commitment.

Release posture:
- Public for transparency.
- Intended for early January community discussion.
- Feedback accepted via GitHub issues.
- This work is exploratory and does not imply endorsement by any Zcash entity.

Funding posture:
- This repository does not request funding.
- Any funding discussion, if it ever occurs, would be external and subsequent to feasibility work.

Purpose:
This repository specifies the minimum cryptographic and governance conditions that would need to hold before any pooled ZEC custody system could be considered acceptable.

This work is downstream of existing protocol capabilities and does not assume any specific outcome of ZSA or NU7 discussions.

If those conditions cannot be met, the correct outcome is to not build the system.

Scope discipline:
The focus is system-level feasibility under combined constraints. Approaches that relax constraints to achieve partial success are out of scope.

Primary documents:
- Research framing: notes/research-note-001.md
- Threat model: threat-model/threat-model-v0.1.md
- Feasibility spec: specs/zk-accounting-feasibility-spec-v0.1.md
- Canonical serialization: specs/canonical-serialization-v0.1.md
- Verification profile: verification/verification-profile-v0.1.md
- Feasibility gates: notes/non-roadmap-feasibility-gates.md
- Test vectors: test-vectors/ (including schema)

Hard constraints:
- ZEC-only
- Orchard-only reserves
- No external venues
- No protocol changes assumed
- Explicit privacy degradation at the service boundary
- Failure is acceptable

License:
CC0-1.0
