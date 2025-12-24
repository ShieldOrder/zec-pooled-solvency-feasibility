# Verification Profile v0.1

Verification requirements:
Verification must be permissionless, deterministic, and reproducible.

### Execution constraints
- No network access
- No randomness
- No clock or wall-time inputs
- No environmental dependencies

### Evaluation semantics
- Overflow results in FAIL
- Missing fields result in FAIL
- Unexpected fields must be ignored
- Output is binary: PASS or FAIL

Any deviation from this profile invalidates verification.

if [ -f verification/verification-profile-v0.1.md ]; then
  if ! grep -q "Anchor acquisition model" verification/verification-profile-v0.1.md; then
    cat >> verification/verification-profile-v0.1.md <<
