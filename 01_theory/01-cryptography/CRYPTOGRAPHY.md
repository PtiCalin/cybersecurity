# Cryptography — Cryptographic Principles and Protocols

This directory contains theory modules on cryptography, encryption, hashing, digital signatures, and secure protocols.

## Topics Covered

### Cryptographic Fundamentals

- **[Cryptography Basics](cryptography-basics.md)** ✅ — History, types, principles
- **[Symmetric Encryption](symmetric-encryption.md)** ✅ — AES, DES, 3DES, block ciphers, stream ciphers, cipher modes
- **[Asymmetric Encryption](asymmetric-encryption.md)** ✅ — RSA, ECC, NTRUEncrypt, public-key cryptography, digital signatures
- [Hashing Functions](hashing-functions.md) — SHA-256, MD5, bcrypt, Argon2, integrity verification

### Applied Cryptography

- **[Digital Certificates & PKI](digital-certificates-pki.md)** ✅ — X.509, certificate authorities, trust chains, PKCS, trust models
- [Key Management](key-management.md) — Generation, distribution, storage, rotation
- [Cryptographic Protocols](cryptographic-protocols.md) — TLS/SSL, SSH, IPsec

### Advanced Topics

- [Cryptanalysis](cryptanalysis.md) — Breaking encryption, attack methods
- [Post-Quantum Cryptography](post-quantum-crypto.md) — Future-proof algorithms
- [Homomorphic Encryption](homomorphic-encryption.md) — Computing on encrypted data
- [Zero-Knowledge Proofs](zero-knowledge-proofs.md) — Proving without revealing

---

## Learning Path

**Recommended study order:**

1. Cryptography Basics — Historical context and principles
2. Symmetric Encryption — Fast encryption for data at rest
3. Asymmetric Encryption — Public-key cryptography
4. Hashing Functions — Integrity verification
5. Digital Signatures — Authentication and non-repudiation
6. Certificates and PKI — Trust infrastructure
7. Cryptographic Protocols — Applied security (TLS, SSH)

**Prerequisites:**

- [CIA Triad](../00-foundations/cia-triad.md) — Understanding confidentiality and integrity
- Basic mathematics (modular arithmetic helpful)

**Leads to:**

- [Network Security](../02-network-security/) — Secure protocols
- [Application Security](../05-application-security/) — Secure coding practices

---

## Integration

**Examples:** See `02_examples/01-cryptography/` for practical demonstrations
**Exercises:** Practice in `03_exercises/01-cryptography/` (encryption challenges)
**References:**

- Textbook: _Applied Cryptography_ by Bruce Schneier
- Standards: `05_references/standards/NIST/`

---

**Key:** 🟢 Beginner | 🟡 Intermediate | 🟠 Advanced | 🔴 Expert
