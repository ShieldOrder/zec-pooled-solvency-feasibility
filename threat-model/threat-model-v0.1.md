# Threat Model v0.1
## ZEC Pooled Solvency Proofs

Scope constraints:
- ZEC-only
- Orchard-only
- No external venues
- No protocol changes assumed

### Assets
- Orchard reserves
- Declared liabilities
- Proof soundness
- Verifier determinism
- Privacy boundaries at the service edge

### Adversaries
- Malicious or dishonest operator
- Compromised prover environment
- Verifier implementation bugs
- Proof withholding or delayed publication
- Chain reorgs and finality ambiguity
- Timing and metadata analysis

### In-scope threats
- Hidden liabilities
- Fractional reserves
- Cross-epoch Orchard note reuse
- Arithmetic or circuit bugs
- Key compromise
- Selective disclosure
- Reorg-induced ambiguity in height-anchored proofs

### Out-of-scope
- Regulatory seizure
- Fiat rails
- Cross-chain bridges
- Wallet telemetry outside the service boundary

### Security posture
- No social trust anchors
- Permissionless verification
- Deterministic, offline verification
- Explicit failure states
