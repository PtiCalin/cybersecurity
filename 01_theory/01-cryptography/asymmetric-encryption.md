# Asymmetric Encryption — Chiffrement Asymétrique

| Property          | Value                                                                                          |
| ----------------- | ---------------------------------------------------------------------------------------------- |
| **Topic**         | Asymmetric Encryption / Chiffrement Asymétrique                                                |
| **Domain**        | 01-cryptography                                                                                |
| **Difficulty**    | 🟡 Intermediate                                                                                |
| **Prerequisites** | [Cryptography Basics](cryptography-basics.md), [Symmetric Encryption](symmetric-encryption.md) |
| **Learning Time** | 75-90 minutes                                                                                  |
| **Status**        | ✅ Complete                                                                                    |

---

## Review Schedule

- [ ] Day 2 — First review after initial study
- [ ] Week 1 — Consolidation review
- [ ] Month 1 — Long-term retention check
- [ ] Month 3 — Mastery verification

---

## Quick Summary

**What:** Asymmetric encryption uses **two different keys**—a public key (shared openly) and a private key (kept secret). Data encrypted with one key can **only** be decrypted with the other.

**Offensive:** Weak key sizes (RSA <2048 bits), improper implementations, side-channel attacks (timing, padding oracles), quantum computing threats.
**Defensive:** Strong key sizes (RSA ≥3072 bits, ECC-256+), proper padding (OAEP), signature verification, quantum-resistant algorithms (post-quantum crypto).

**Why it matters:** Asymmetric crypto solves the **key distribution problem** of symmetric encryption. Enables secure communication without pre-shared secrets—foundation of TLS, SSH, PGP, code signing, and blockchain.

---

## Prerequisites

**Required knowledge:**

- [Cryptography Basics](cryptography-basics.md) — Encryption fundamentals
- [Symmetric Encryption](symmetric-encryption.md) — Understanding symmetric crypto limitations
- Modular arithmetic basics (helpful but not required)

**Quick check:** Do you understand the key distribution problem in symmetric encryption? Can you explain what "confidentiality" and "authenticity" mean? If yes, you're ready.

---

## Layer 1 — Intuition

Asymmetric encryption is like a **mailbox with a slot** (public key) and a **unique key to open it** (private key):

🔓 **Public key:** Anyone can drop letters into the mailbox (encrypt)
🔒 **Private key:** Only you can open the mailbox and read letters (decrypt)

**Key insight:** The two keys are mathematically related but **computationally infeasible to derive one from the other**. Knowing the public key doesn't help you find the private key.

**Two main use cases:**

1. **Encryption (Confidentiality):**
   - Encrypt with **recipient's public key**
   - Decrypt with **recipient's private key**
   - Use case: Secure messaging, email encryption

2. **Digital Signatures (Authenticity):**
   - Sign with **sender's private key**
   - Verify with **sender's public key**
   - Use case: Code signing, document authentication, blockchain

**Analogy:**

- Public key = your mailing address (anyone can send you letters)
- Private key = your house key (only you can open your mailbox)
- If someone steals your house key, all past and future mail is compromised

---

## Layer 2 — Formal Definitions

### Asymmetric Encryption — Chiffrement Asymétrique

**Definition:** Cryptographic system using a **key pair**:

```
Key pair = (PK, SK)
  PK = Public Key (clé publique)  — distributed openly
  SK = Secret/Private Key (clé privée)  — kept secret

Encryption (for confidentiality):
  C = Encrypt_PK(P)  — Encrypt plaintext P with recipient's public key
  P = Decrypt_SK(C)  — Decrypt ciphertext C with recipient's private key

Digital Signature (for authenticity):
  S = Sign_SK(M)  — Sign message M with sender's private key
  Valid = Verify_PK(M, S)  — Verify signature with sender's public key
```

**Key properties:**

- **Trapdoor function:** Easy to compute one way, hard to reverse without secret
- **Slower than symmetric:** 100-10,000x slower than AES
- **Larger keys:** Typical sizes: RSA 2048-4096 bits, ECC 256-521 bits
- **Key distribution solved:** Public keys can be shared openly

**French terms:** _Clé publique_ (public key), _Clé privée_ (private key), _Paire de clés_ (key pair)

---

### Clé Publique / Clé Privée — Public/Private Key Pair

**Public Key (Clé Publique):**

- Can be shared openly (published in directory, key servers, certificates)
- Used by **others** to encrypt messages **to you**
- Used by **others** to verify signatures **from you**
- Compromise: No immediate security loss (but enables targeted attacks)

**Private Key (Clé Privée):**

- **Must be kept secret** and protected
- Used by **you** to decrypt messages encrypted with your public key
- Used by **you** to sign messages proving they came from you
- Compromise: **Complete security failure**—attacker can decrypt all past messages (if no forward secrecy) and forge signatures

**Mathematical relationship:**

```
PK and SK are mathematically linked by a trapdoor function:
  - Computing PK from SK: Easy (milliseconds)
  - Computing SK from PK: Computationally infeasible (would take billions of years)
```

**Example analogy:**

```
Factorization problem (RSA):
  - Easy: Multiply two primes: 61 × 53 = 3233
  - Hard: Factor 3233 back to 61 and 53 (try all possibilities)

For large numbers (2048 bits):
  - Multiplication: Instant
  - Factorization: Would take longer than the age of the universe
```

---

## RSA Algorithm — Rivest-Shamir-Adleman

**Invented:** 1977 by Ron Rivest, Adi Shamir, Leonard Adleman (MIT)
**Security basis:** Difficulty of factoring large semi-primes (product of two primes)

**Use cases:**

- Key exchange (TLS handshake)
- Digital signatures (code signing, PKI certificates)
- Email encryption (PGP/GPG)

**Status:** Still widely used but **post-quantum vulnerable**. Migration to quantum-resistant algorithms underway.

---

### RSA Key Generation (Worked Example)

**Step 1: Choose two prime numbers**

```
p = 7
q = 19

(In real RSA, these would be 1024-bit primes)
```

**Step 2: Compute n = p × q**

```
n = 7 × 19 = 133

n is the modulus (public component)
```

**Step 3: Compute φ(n) = (p - 1) × (q - 1)**

```
φ(n) = (7 - 1) × (19 - 1) = 6 × 18 = 108

φ(n) is Euler's totient function (counts numbers coprime to n)
```

**Step 4: Choose public exponent e**

```
Requirements:
  - 1 < e < φ(n)
  - gcd(e, φ(n)) = 1  (e and φ(n) are coprime)

Common choice: e = 65537 (0x10001)
  - Allows fast encryption
  - Large enough to avoid attacks

For our small example: e = 5
Check: gcd(5, 108) = 1 ✓
```

**Step 5: Compute private exponent d**

```
Find d such that: (e × d) mod φ(n) = 1
This means: d is the modular multiplicative inverse of e modulo φ(n)

Formula: d = e^(-1) mod φ(n)

For our example:
  (5 × d) mod 108 = 1

Extended Euclidean Algorithm gives:
  d = 65

Verify: (5 × 65) mod 108 = 325 mod 108 = 1 ✓
```

**Step 6: Key pair created**

```
Public key: (n, e) = (133, 5)
  - Share openly

Private key: (n, d) = (133, 65)
  - Keep secret
  - Destroy p, q, φ(n) after generation
```

---

### RSA Encryption & Decryption (Worked Example)

**Scenario:** Encrypt message M = 42 with RSA public key (n=133, e=5)

**Encryption (anyone can do this with public key):**

```
Ciphertext C = M^e mod n
             = 42^5 mod 133
             = 130691232 mod 133
             = 87

C = 87 (send this over the network)
```

**Decryption (only private key holder can do this):**

```
Plaintext M = C^d mod n
            = 87^65 mod 133
            = (very large number) mod 133
            = 42  (original message recovered!)

M = 42 ✓
```

**Why this works mathematically:**

```
M^(e×d) mod n = M mod n  (Fermat's Little Theorem / Euler's Theorem)

Since (e × d) mod φ(n) = 1, we have:
  C^d = (M^e)^d = M^(e×d) = M mod n
```

---

### RSA Digital Signature (Worked Example)

**Digital signature proves:** "This message came from me and hasn't been altered."

**5-Step Signature Process:**

**Step 1: Hash the message (Résumé)**

```
Message: "Transfer $1000 to Bob"
Hash: H(M) = SHA-256("Transfer $1000 to Bob")
           = 0x3a5c9f... (256-bit hash)

Why hash?
  - RSA can only sign data smaller than modulus
  - Hashing produces fixed-size output
  - Any change to message changes hash completely
```

**Step 2: Sign the hash with private key**

```
Signature S = H(M)^d mod n
            = (hash value)^private_exponent mod modulus

Only private key holder can create this
```

**Step 3: Send message + signature**

```
Send: (Message, Signature)
  - Message: "Transfer $1000 to Bob" (in clear)
  - Signature: 0x8f3a... (encrypted hash)
```

**Step 4: Recipient hashes message**

```
Received message: "Transfer $1000 to Bob"
Compute: H(M) = SHA-256("Transfer $1000 to Bob")
```

**Step 5: Verify signature with public key**

```
Decrypted_hash = S^e mod n
                = Signature^public_exponent mod modulus

If Decrypted_hash == H(M):
  ✓ Signature is valid
  ✓ Message came from holder of private key
  ✓ Message hasn't been altered

If they don't match:
  ✗ Signature invalid — message tampered or forged
```

**Complete example with small numbers:**

```
Message: M = "HELLO" → Hash: H(M) = 42 (simplified)
Private key: d = 65, n = 133

Sign:
  S = 42^65 mod 133 = 87

Send: (M, S) = ("HELLO", 87)

Verify:
  H(M) = 42  (recipient computes)
  87^5 mod 133 = 42  (decrypt signature with public key)
  42 == 42 ✓ Signature valid!
```

**What signature proves:**

- ✅ **Authenticity:** Message came from holder of private key
- ✅ **Integrity:** Message hasn't been altered (hash would differ)
- ✅ **Non-repudiation:** Signer cannot deny signing (only they have private key)

**What signature does NOT prove:**

- ❌ **Confidentiality:** Message is sent in clear (anyone can read)

**French term:** _Signature numérique_ (digital signature), _Résumé_ (hash/digest)

---

## ECC — Elliptic Curve Cryptography

**Invented:** 1985 by Neal Koblitz and Victor Miller
**Security basis:** Difficulty of Elliptic Curve Discrete Logarithm Problem (ECDLP)

**Key advantage:** **Smaller keys with equivalent security**

| Security Level | RSA Key Size | ECC Key Size | Performance    |
| -------------- | ------------ | ------------ | -------------- |
| 80-bit         | 1024 bits    | 160 bits     | ECC 10x faster |
| 112-bit        | 2048 bits    | 224 bits     | ECC 10x faster |
| 128-bit        | 3072 bits    | 256 bits     | ECC 10x faster |
| 192-bit        | 7680 bits    | 384 bits     | ECC 10x faster |
| 256-bit        | 15360 bits   | 521 bits     | ECC 10x faster |

**Why ECC is faster:**

- Smaller keys → faster operations
- Lower bandwidth (important for IoT, mobile)
- Lower computational requirements

**Popular ECC curves:**

- **secp256r1 (P-256):** NIST standard, widely supported (Bitcoin, TLS)
- **Curve25519:** Fast, designed for security (used in Signal, SSH, TLS 1.3)
- **secp384r1 (P-384):** Higher security level
- **secp521r1 (P-521):** Maximum security (not 512, it's 521!)

**Use cases:**

- TLS 1.3 (ECDHE key exchange)
- Bitcoin, Ethereum (ECDSA signatures)
- Signal Protocol (E2E encrypted messaging)
- SSH (ECDSA host keys)
- Apple Secure Enclave

**How ECC works (simplified):**

```
Elliptic curve equation: y² = x³ + ax + b

Define a "point addition" operation on the curve
Public key: Q = k × G
  - k = private key (random large number)
  - G = generator point (standard curve parameter)
  - Q = public key (point on curve after k additions)

Computing Q from k: Fast (point multiplication)
Computing k from Q: Computationally infeasible (ECDLP)
```

**Status:** ECC is **also quantum-vulnerable** (Shor's algorithm). Post-quantum alternatives: lattice-based (CRYSTALS-Kyber), hash-based (SPHINCS+).

---

## NTRUEncrypt — Quantum-Resistant Alternative

**Invented:** 1996 by Jeffrey Hoffstein, Jill Pipher, Joseph H. Silverman
**Security basis:** Shortest Vector Problem (SVP) in lattice cryptography

**Key advantage:** **Resistant to quantum computer attacks**

**Why it matters:**

- Shor's algorithm (quantum) breaks RSA and ECC
- NTRUEncrypt based on different mathematical problem (lattice SVP)
- No known quantum algorithm to efficiently solve SVP

**NIST Post-Quantum Cryptography Standardization:**

- **CRYSTALS-Kyber** (lattice-based) — selected for standardization (2022)
- **CRYSTALS-Dilithium** (lattice-based signatures)
- **SPHINCS+** (hash-based signatures)

**Performance comparison:**

```
RSA-2048:     Slow key generation, slow operations, large keys
ECC-256:      Fast, small keys, quantum-vulnerable
NTRUEncrypt:  Fast encryption/decryption, moderate key size, quantum-resistant
CRYSTALS-Kyber: Fast, quantum-resistant, NIST selected
```

**Use cases (emerging):**

- Future TLS versions (hybrid classical + post-quantum)
- Long-term confidential data (data that must remain secret for decades)
- Government/military communications

**Status:** Active standardization. Expect widespread deployment in 2025-2030.

---

## Layer 3 — Worked Examples

### Example 1: RSA Complete Workflow (Confidentiality)

**Scenario:** Alice sends encrypted message to Bob

**Setup:**

```
Bob generates RSA key pair:
  Public key:  (n=3233, e=17)
  Private key: (n=3233, d=2753)

Bob publishes public key (3233, 17) on key server
```

**Step 1: Alice encrypts message**

```
Alice's plaintext: M = 123
Alice uses Bob's public key (n=3233, e=17):

C = M^e mod n
  = 123^17 mod 3233
  = 855

Alice sends C = 855 to Bob (over insecure channel)
```

**Step 2: Bob decrypts message**

```
Bob receives C = 855
Bob uses his private key (n=3233, d=2753):

M = C^d mod n
  = 855^2753 mod 3233
  = 123

Bob recovers original message: M = 123 ✓
```

**Attacker Eve intercepts:**

```
Eve knows:
  - n = 3233 (public)
  - e = 17 (public)
  - C = 855 (intercepted)

To decrypt, Eve needs d
To find d, Eve needs to factor n:
  3233 = 61 × 53

For small n, factorization is easy
For RSA-2048, would take billions of years with current computers
```

---

### Example 2: Digital Signature Complete Workflow

**Scenario:** Alice signs a contract and sends to Bob

**Setup:**

```
Alice's key pair:
  Public key:  (n=3233, e=17) — published
  Private key: (n=3233, d=2753) — kept secret
```

**Step 1: Alice creates signature**

```
Contract: "I agree to pay $10,000"
Hash: H(contract) = SHA-256(...) = 42 (simplified)

Sign with Alice's private key:
S = H^d mod n
  = 42^2753 mod 3233
  = 1234

Alice sends: (Contract, Signature) = ("I agree...", 1234)
```

**Step 2: Bob verifies signature**

```
Bob receives: Contract + Signature (1234)

Step 2a: Bob hashes the contract
  H(contract) = 42

Step 2b: Bob decrypts signature with Alice's public key
  H' = S^e mod n
     = 1234^17 mod 3233
     = 42

Step 2c: Compare
  H(contract) = 42
  H' (from signature) = 42
  42 == 42 ✓ Signature is valid!
```

**What Bob can conclude:**

- ✅ Contract was signed by Alice (only she has the private key)
- ✅ Contract hasn't been altered (hash matches)
- ✅ Alice cannot deny signing (non-repudiation)

**Attempted forgery:**

```
Attacker Eve modifies contract to "I agree to pay $100,000"
Eve sends: (Modified contract, Original signature 1234)

Bob verifies:
  H(modified contract) = 99 (different hash!)
  H' = 1234^17 mod 3233 = 42 (from original signature)
  99 ≠ 42 ✗ Signature invalid — forgery detected!
```

---

### Example 3: Hybrid Encryption (RSA + AES)

**Problem:** RSA is slow. Can't efficiently encrypt large files.

**Solution:** Hybrid encryption (how TLS, PGP, S/MIME work)

**Scenario:** Alice sends 100MB encrypted video to Bob

**Step 1: Alice generates random AES key**

```
AES_key = random_256_bits()
  = 0x3a5c9f1e2b4d6f8a... (32 bytes)
```

**Step 2: Alice encrypts video with AES**

```
Encrypted_video = AES-256-GCM(Video, AES_key)

Fast: 100MB encrypted in ~1 second
```

**Step 3: Alice encrypts AES key with Bob's RSA public key**

```
Encrypted_AES_key = RSA_Encrypt(AES_key, Bob_public_key)

Slow: But only encrypting 32 bytes (instant)
```

**Step 4: Alice sends bundle**

```
Send to Bob:
  - Encrypted_video (100MB)
  - Encrypted_AES_key (256 bytes)
```

**Step 5: Bob decrypts**

```
AES_key = RSA_Decrypt(Encrypted_AES_key, Bob_private_key)
Video = AES_Decrypt(Encrypted_video, AES_key)
```

**Benefits:**

- ✅ Fast bulk encryption (AES)
- ✅ Secure key exchange (RSA)
- ✅ Best of both worlds

**This is how TLS works:**

```
TLS Handshake:
  1. Server sends RSA/ECC public key (in certificate)
  2. Client generates random symmetric key (session key)
  3. Client encrypts session key with server's public key
  4. Server decrypts session key with private key
  5. Both use symmetric encryption (AES-GCM) for actual data

Result: Fast symmetric encryption with secure asymmetric key exchange
```

---

### Example 4: Key Size Selection (Real-World)

**Question:** What RSA key size should I use in 2026?

**NIST recommendations (SP 800-57):**

| Use Case                 | RSA Key Size | ECC Key Size | Valid Until |
| ------------------------ | ------------ | ------------ | ----------- |
| Short-term (1-2 years)   | 2048 bits    | 224 bits     | 2030        |
| Medium-term (5-10 years) | 3072 bits    | 256 bits     | 2030+       |
| Long-term (20+ years)    | 4096 bits    | 384 bits     | 2050+       |
| Top secret               | 7680 bits    | 512 bits     | ?           |

**Quantum threat considerations:**

```
Shor's algorithm (quantum computer):
  - Breaks RSA of any key size efficiently
  - Breaks ECC of any key size efficiently

Timeline:
  - Large-scale quantum computer: 2030-2040 (estimated)
  - "Harvest now, decrypt later" attacks ongoing

Action: Start migrating to post-quantum crypto (CRYSTALS-Kyber)
```

**Practical recommendation (2026):**

```
New systems:
  - Use ECC-256 (faster) OR RSA-3072 (compatibility)
  - Prepare for post-quantum migration (hybrid mode)

Legacy systems:
  - RSA-2048 still acceptable if upgrade difficult
  - Plan replacement by 2030

Top secret / long-term confidential:
  - Use post-quantum algorithms NOW (CRYSTALS-Kyber, Dilithium)
```

---

## Layer 4 — Edge Cases, Nuances, and Limitations

### Edge Case 1: RSA Padding Schemes

**Problem:** Textbook RSA is insecure for direct message encryption.

**Vulnerability (deterministic encryption):**

```
Same plaintext → same ciphertext
Attacker can build dictionary of common messages

Example:
  Encrypt("Yes") with RSA public key → always same ciphertext
  Encrypt("No") with RSA public key → always same ciphertext

Attacker sees ciphertext → looks up in dictionary → knows plaintext
```

**Solution: Padding schemes add randomness**

#### PKCS#1 v1.5 Padding (Legacy)

```
Padded = 0x00 || 0x02 || Random_bytes || 0x00 || Message

Then RSA encrypt the padded value
```

**Status:** Vulnerable to Bleichenbacher's attack (1998). **DO NOT USE for new systems.**

---

#### OAEP (Optimal Asymmetric Encryption Padding) — **USE THIS**

```
OAEP uses:
  - Random seed
  - Two hash functions (typically SHA-256)
  - Mask generation function

Result: Same message encrypted multiple times → different ciphertexts
```

**Python example:**

```python
from cryptography.hazmat.primitives import hashes
from cryptography.hazmat.primitives.asymmetric import rsa, padding

# Generate key pair
private_key = rsa.generate_private_key(
    public_exponent=65537,
    key_size=2048
)
public_key = private_key.public_key()

# Encrypt with OAEP padding
ciphertext = public_key.encrypt(
    b"Confidential message",
    padding.OAEP(
        mgf=padding.MGF1(algorithm=hashes.SHA256()),
        algorithm=hashes.SHA256(),
        label=None
    )
)

# Decrypt
plaintext = private_key.decrypt(
    ciphertext,
    padding.OAEP(
        mgf=padding.MGF1(algorithm=hashes.SHA256()),
        algorithm=hashes.SHA256(),
        label=None
    )
)
```

**Lesson:** Always use OAEP padding with RSA encryption.

---

### Edge Case 2: Small Public Exponent Attack

**Common choice:** e = 3 (very fast encryption)

**Vulnerability:** If sending same message to 3+ recipients with e=3

**Attack scenario:**

```
Alice sends M to Bob, Carol, and Dave (all have e=3, different n)
Attacker intercepts all three ciphertexts:
  C1 = M^3 mod n1
  C2 = M^3 mod n2
  C3 = M^3 mod n3

Using Chinese Remainder Theorem:
  Attacker recovers M^3 mod (n1 × n2 × n3)
  Since M^3 < n1 × n2 × n3, attacker computes cube root → M

No factorization needed!
```

**Solution:** Use e = 65537 (0x10001) — standard choice

---

### Edge Case 3: Timing Attacks

**Vulnerability:** Decryption time reveals information about private key

**Attack mechanism:**

```
RSA decryption: M = C^d mod n

Modular exponentiation uses square-and-multiply algorithm:
  - If bit of d is 0: square only
  - If bit of d is 1: square and multiply

Different operations → different timing → reveals bits of d
```

**Mitigation:**

- Constant-time implementations (no branches based on secret data)
- Blinding (multiply by random value, decrypt, unblind)

**Lesson:** Cryptographic implementations must be constant-time.

---

### Edge Case 4: Key Reuse Across Domains

**Problem:** Using same key pair for encryption AND signatures is dangerous

**Vulnerability:**

```
If same key used for both:
  - Attacker may trick you into signing a ciphertext
  - Signed ciphertext = M^d mod n
  - Attacker uses this as decryption of M

Result: Attacker obtains plaintext without breaking crypto
```

**Best practice:**

- Separate key pairs for encryption and signing
- Or use different padding schemes (OAEP for encryption, PSS for signatures)

---

### Limitation 1: Computational Cost

**RSA performance (relative to AES):**

| Operation      | RSA-2048 | AES-256  | Slowdown Factor   |
| -------------- | -------- | -------- | ----------------- |
| Encryption     | 0.5ms    | 0.0001ms | 5,000x slower     |
| Decryption     | 15ms     | 0.0001ms | 150,000x slower   |
| Key generation | 100ms    | 0.0001ms | 1,000,000x slower |

**Why so slow:**

- Large number arithmetic (2048-bit modular exponentiation)
- Not parallelizable for single operation

**This is why we use hybrid encryption:** RSA only for key exchange, AES for bulk data.

---

### Limitation 2: Quantum Computing Threat

**Shor's Algorithm (1994):**

```
Quantum computer with ~4000 logical qubits can:
  - Factor RSA-2048 in hours
  - Solve ECDLP for ECC-256 in hours

Current status (2026):
  - ~1000 noisy qubits exist
  - Need error correction (1 logical qubit ≈ 1000 physical qubits)
  - Timeline: 2030-2040 for practical quantum computer
```

**"Harvest now, decrypt later" threat:**

```
Attackers are storing encrypted traffic TODAY
When quantum computers arrive, decrypt archived traffic
Threat to: long-term secrets, government communications, medical records
```

**Post-quantum migration:**

```
NIST Post-Quantum Cryptography Standards (2024):
  - CRYSTALS-Kyber (key encapsulation)
  - CRYSTALS-Dilithium (signatures)
  - SPHINCS+ (stateless hash-based signatures)

Migration strategy:
  - Hybrid mode: Classical (RSA/ECC) + Post-Quantum (Kyber)
  - Transition period: 2024-2030
```

---

### Limitation 3: Key Management Complexity

**Key lifecycle:**

```
1. Generation (secure random number generator critical)
2. Distribution (public key must be authentic — solved by PKI/certificates)
3. Storage (private key protection — HSM, TPM, secure enclave)
4. Rotation (best practice: rotate every 1-2 years)
5. Revocation (if compromised, must notify all parties)
6. Destruction (secure key deletion at end of life)
```

**Common mistakes:**

- Weak random number generator (Debian OpenSSL bug 2008)
- Private key stored unencrypted on disk
- No key backup → key loss = data loss forever
- No revocation mechanism → compromised keys still trusted

**Best practices:**

- Hardware security modules (HSM) for key storage
- Key escrow for critical data (with proper access controls)
- Certificate transparency logs (detect rogue certificates)
- Regular key rotation (limit damage from undetected compromise)

---

## Active Recall Prompts

### Understanding Questions

1. **Key pair concept:** Explain the relationship between public and private keys. Why can't you derive the private key from the public key?

2. **Encryption vs Signature:** Explain the difference between encrypting with RSA (for confidentiality) and signing with RSA (for authenticity). Which key is used in each case?

3. **RSA math:** Walk through the RSA key generation steps. Why do we compute φ(n)? What is the relationship between e and d?

---

### Application Questions

4. **Hybrid encryption:** Why does TLS use both RSA/ECDH and AES? What would happen if we only used RSA for all data?

5. **Signature verification:** You receive a signed document. The signature verification succeeds. What can you conclude? What can you NOT conclude?

6. **Padding necessity:** Why is OAEP padding required for RSA encryption? Give an example attack that works without padding.

---

### Transfer Questions

7. **Real-world incident:** Research the **Debian OpenSSL vulnerability (CVE-2008-0166)**. How did weak randomness lead to predictable RSA keys?

8. **Key size recommendation:** You're designing a system to encrypt patient health records that must remain confidential for 50 years. What asymmetric algorithm and key size would you choose? Justify your answer considering quantum threats.

9. **Certificate pinning:** Mobile apps use certificate pinning to prevent MitM attacks. Explain how RSA signatures in certificates enable trust. What happens if the pinned certificate expires?

10. **Performance experiment:** Generate RSA-2048 and ECC-256 key pairs. Measure generation time, encryption time, signature time. Compare results. Why is ECC faster despite equivalent security?

---

## References

### Primary Sources

- **Course:** IFT2830 - Sécurité des systèmes informatiques (UdeM)
  Final exam materials: [02_theory-final.md](../../../05_references/course-materials/IFT2830_course-materials/02_theory-final.md)

### Standards & Specifications

- **NIST FIPS 186-5** — Digital Signature Standard (DSS)
- **RFC 8017** — PKCS #1: RSA Cryptography Specifications Version 2.2
- **RFC 8446** — TLS 1.3 Protocol (uses ECDHE + RSA/ECDSA)
- **NIST SP 800-57** — Key Management Recommendations

### Academic & Industry

- Rivest, R., Shamir, A., & Adleman, L. (1978). "A Method for Obtaining Digital Signatures and Public-Key Cryptosystems." _Communications of the ACM_.
- Koblitz, N. (1987). "Elliptic Curve Cryptosystems." _Mathematics of Computation_.
- Shor, P. (1994). "Algorithms for Quantum Computation: Discrete Logarithms and Factoring." _IEEE_.
- Bernstein, D. J. (2006). "Curve25519: New Diffie-Hellman Speed Records." _PKC_.

### Post-Quantum Cryptography

- **NIST PQC Standardization** — Post-Quantum Cryptography Project
- **CRYSTALS-Kyber** — Lattice-based key encapsulation
- **CRYSTALS-Dilithium** — Lattice-based signatures
- **SPHINCS+** — Stateless hash-based signatures

### Real-World Incidents

- **Debian OpenSSL (2008, CVE-2008-0166)** — Weak RNG generated predictable RSA keys
- **ROCA (2017, CVE-2017-15361)** — Infineon TPM RSA key generation flaw
- **Factoring RSA-768 (2009)** — Demonstrated need for larger keys

---

## Related Content

### Theory Modules

- **Previous:** [Symmetric Encryption](symmetric-encryption.md) — Fast encryption with shared keys
- **Next:** [Digital Certificates & PKI](digital-certificates-pki.md) — Trust infrastructure
- **Related:** [Cryptography Basics](cryptography-basics.md) — Foundational concepts

### Examples

- [RSA Key Generation](../../../02_examples/01-cryptography/rsa-keygen/) — Generate and use RSA keys
- [Digital Signature Demo](../../../02_examples/01-cryptography/digital-signatures/) — Sign and verify documents
- [TLS Handshake Analysis](../../../02_examples/01-cryptography/tls-handshake/) — Hybrid encryption in action

### Exercises

- [RSA Math Calculation](../../../03_exercises/01-cryptography/rsa-math/) 🟡 — Hand-calculate RSA encryption/decryption
- [Break Small RSA](../../../03_exercises/01-cryptography/factor-rsa/) 🟡 — Factor small modulus
- [Implement Digital Signatures](../../../03_exercises/01-cryptography/implement-signatures/) 🟠 — Code signature generation/verification

### Tools & Resources

- **OpenSSL:** `04_resources/tools/cryptography/openssl-cheatsheet.md`
- **GPG/PGP:** `04_resources/tools/cryptography/gpg-guide.md`
- **Key Size Calculator:** https://www.keylength.com/

---

## Personal Insights & Notes

### Study Notes

_Record your observations, "aha" moments, and connections here._

**Example:**

- "RSA is like a one-way math door. Easy to walk through (encrypt with public key), impossible to walk back without the key (decrypt requires private key)."
- "Digital signatures are encryption in reverse: sign with private (prove you), verify with public (anyone can check)."

---

### Real-World Connections

_Link this concept to incidents, news, or work experience._

**Example:**

- "TLS certificates use RSA signatures. When browser shows green lock, it verified server's certificate signature chain back to trusted root CA."

---

### Questions & Confusion

_Track what's unclear or needs deeper investigation._

**Example:**

- "How exactly does OAEP padding work? What is the mask generation function doing?"
- "Why is ECC so much faster? Need to understand elliptic curve point addition math."

---

### Exam/Interview Prep

_Key points to remember for assessments._

**Exam focus (IFT2830):**

- Chiffrement asymétrique: deux clés différentes (publique, privée)
- Clé publique: partagée ouvertement, chiffrer ou vérifier signature
- Clé privée: gardée secrète, déchiffrer ou créer signature
- RSA: basé sur factorisation (p × q = n), étapes génération (φ(n), e, d)
- Signature numérique: 5 étapes (résumé → signer avec clé privée → envoyer M+S → résumé M → vérifier avec clé publique)
- ECC: clés plus petites pour même sécurité (256 bits ECC ≈ 3072 bits RSA)
- NTRUEncrypt: résistant quantique (lattice-based)
- Chiffrement hybride: RSA pour échanger clé AES, AES pour données volumineuses

**Interview talking points:**

- "RSA solves the key distribution problem but is slow. That's why we use hybrid encryption—RSA for key exchange, AES for data."
- "Digital signatures provide authenticity and non-repudiation. Encryption provides confidentiality. They solve different problems."
- "Always use OAEP padding with RSA encryption and PSS padding with signatures. Textbook RSA is insecure."
- "Quantum computers will break RSA and ECC. We're migrating to post-quantum algorithms like CRYSTALS-Kyber."

---

## Change Log

| Date       | Change                        | Reason                                                     |
| ---------- | ----------------------------- | ---------------------------------------------------------- |
| 2026-04-27 | Created module                | Asymmetric encryption deep dive for final exam             |
| 2026-04-27 | Added RSA complete algorithm  | Key generation, encryption, decryption with worked example |
| 2026-04-27 | Added digital signatures      | 5-step process with French terminology (résumé)            |
| 2026-04-27 | Added ECC section             | Modern alternative with smaller keys                       |
| 2026-04-27 | Added NTRUEncrypt             | Quantum-resistant cryptography                             |
| 2026-04-27 | Added padding schemes         | OAEP security requirement                                  |
| 2026-04-27 | Integrated French terminology | Bilingual support from IFT2830 materials                   |
