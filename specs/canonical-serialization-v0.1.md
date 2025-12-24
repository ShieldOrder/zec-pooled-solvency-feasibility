# Canonical Serialization v0.1

Purpose:
Ensure that independent verifiers produce identical results from identical inputs.

### Encoding rules
- Unsigned integers only
- Fixed-width little-endian encoding
- No floating point representations
- No implicit defaults

### Arithmetic safety
- All arithmetic operations must be range-checked
- Any overflow or underflow results in FAIL

### Artifact format
- RFC 8785 JSON Canonicalization Scheme
- Proof blobs base64 encoded
- Field ordering fixed by canonicalization

### Determinism requirements
- No network access
- No randomness
- No clock or wall-time inputs
- Pure function behavior

Violation of any rule invalidates the verification result.

### Scope limitation

This document does not define numeric bounds, arithmetic domains, or field limits.
All such limits must be explicitly specified in the corresponding feasibility or circuit specification.
EOF
