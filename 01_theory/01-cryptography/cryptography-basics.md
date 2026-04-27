# Cryptography Basics — Bases de la Cryptographie

| Property          | Value                                                 |
| ----------------- | ----------------------------------------------------- |
| **Topic**         | Cryptography Fundamentals / Bases de la Cryptographie |
| **Domain**        | 01-cryptography                                       |
| **Difficulty**    | 🟡 Intermediate                                       |
| **Prerequisites** | [CIA Triad](../00-foundations/cia-triad.md)           |
| **Learning Time** | 70-90 minutes                                         |
| **Status**        | ✅ Complete                                           |

---

## Review Schedule

- [ ] Day 2 — First review after initial study
- [ ] Week 1 — Consolidation review
- [ ] Month 1 — Long-term retention check
- [ ] Month 3 — Mastery verification

---

## Quick Summary

**What:** Cryptography is the science of secure communication using mathematical algorithms to protect confidentiality, integrity, and authenticity.

**Offensive:** Weak cryptography is a high-value target. Broken algorithms = data exposure.
**Defensive:** Strong cryptography protects data at rest, in transit, and in use. Foundation of modern security.

**Why it matters:** Cryptography underpins almost every security control: TLS/HTTPS, VPNs, password storage, file encryption, digital signatures, blockchain. **Understanding crypto is mandatory** for both offensive and defensive security work.

---

## Prerequisites

**Required knowledge:**

- [CIA Triad](../00-foundations/cia-triad.md) — Confidentiality, Integrity, Authenticity
- Basic mathematics: modular arithmetic, XOR operation
- Binary/hexadecimal number systems

**Quick check:** Can you explain what "one-way function" means? If yes, you're ready.

---

## Layer 1 — Intuition

Cryptography is like sending a locked box through the mail:

🔒 **Encryption (Chiffrement)** = Locking the box with a key
🔓 **Decryption (Déchiffrement)** = Unlocking the box with the key
🔑 **Key (Clé)** = The physical key to the lock
🔨 **Hashing (Hachage)** = Breaking the box into sawdust (one-way, can't rebuild)
🪶 **Signature (Signature)** = Wax seal proving who sent the box

**Key insight:** Cryptography transforms readable data (plaintext) into unreadable data (ciphertext) using mathematical functions. Only those with the **key** can reverse the process.

---

## Layer 2 — Formal Definitions

### Core Concepts

#### Cryptography — Cryptographie

**Definition:** The study and practice of secure communication techniques that prevent unauthorized access to information.

**Goals (aligned with CIA triad):**

- **Confidentiality (Confidentialité):** Only authorized parties can read the data
- **Integrity (Intégrité):** Data hasn't been altered
- **Authentication (Authentification):** Verify identity of sender
- **Non-repudiation (Non-répudiation):** Sender cannot deny sending message

**French term:** _Cryptographie_

---

#### Plaintext & Ciphertext

**Plaintext (Texte en clair):**

- Original, readable message
- Example: `"Transfer $1000 to account 12345"`

**Ciphertext (Texte chiffré):**

- Encrypted, unreadable message
- Example: `"8f3a9c2e7b1d4f6a8e2c5b7d9e1f3a5c"`

**Cryptographic transformation:**

```
Plaintext + Key → [Encryption Algorithm] → Ciphertext
Ciphertext + Key → [Decryption Algorithm] → Plaintext
```

**French terms:** _Texte en clair, Texte chiffré_

---

#### Key — Clé

**Definition:** Secret parameter used in cryptographic algorithms to control encryption/decryption.

**Key properties:**

- **Secrecy:** Security depends on key secrecy, not algorithm secrecy (Kerckhoffs's principle)
- **Randomness:** Keys must be randomly generated (not "password123")
- **Length:** Longer keys = more security (128-bit, 256-bit)

**Key types:**

- **Symmetric:** Same key for encryption and decryption
- **Asymmetric:** Key pair (public key + private key)

**French term:** _Clé_

---

### Cryptographic Primitives

#### 1. Encryption — Chiffrement

**Definition:** Transforming plaintext into ciphertext using an algorithm and a key.

**Types:**

- **Symmetric (Symétrique):** Same key for encryption/decryption (AES, ChaCha20)
- **Asymmetric (Asymétrique):** Different keys for encryption/decryption (RSA, ECC)

**Use cases:**

- Protecting data at rest (disk encryption: BitLocker, FileVault)
- Protecting data in transit (TLS/HTTPS)
- Secure messaging (Signal, WhatsApp)

**French term:** _Chiffrement_

---

#### 2. Hashing — Hachage

**Definition:** One-way function that produces a fixed-size output (hash/digest) from arbitrary input.

**Properties:**

- **Deterministic:** Same input → same hash
- **One-way:** Easy to compute hash, impossible to reverse
- **Fixed size:** Any input length → fixed output (e.g., SHA-256 always 256 bits)
- **Collision resistance:** Hard to find two inputs with same hash

**Common algorithms:**

- **MD5:** 128-bit output, **BROKEN** (collisions found)
- **SHA-1:** 160-bit output, **WEAK** (collision attack feasible)
- **SHA-256:** 256-bit output, **STRONG** (current standard)
- **SHA-3:** 256-bit output, **STRONG** (alternative to SHA-2)

**Use cases:**

- Password storage (with salting: bcrypt, Argon2)
- File integrity verification (download checksums)
- Digital signatures (sign the hash, not the file)
- Blockchain (proof-of-work)

**French term:** _Hachage, Fonction de hachage_

---

#### 3. Message Authentication Code (MAC)

**Definition:** Cryptographic checksum that verifies **both integrity and authenticity** of a message.

**How it works:**

```
MAC = Hash(Message + Secret Key)
```

**Verification:**

```
Recipient computes MAC with their copy of secret key
If computed MAC == received MAC → message is authentic and unmodified
```

**Common algorithm:**

- **HMAC (Hash-based MAC):** Uses hash function (SHA-256) + secret key
- **CMAC (Cipher-based MAC):** Uses block cipher (AES)

**Use cases:**

- API request authentication
- Cookie integrity (tamper-proof sessions)
- VPN tunnel authentication

**French term:** _Code d'authentification de message (CAM)_

---

#### 4. Digital Signature — Signature Numérique

**Definition:** Cryptographic proof that a message was created by a specific sender and hasn't been altered.

**How it works (asymmetric):**

```
Sender:
  1. Hash the message → digest
  2. Encrypt digest with sender's private key → signature
  3. Send message + signature

Receiver:
  1. Hash the received message → digest_received
  2. Decrypt signature with sender's public key → digest_decrypted
  3. If digest_received == digest_decrypted → valid signature
```

**Properties:**

- **Authentication:** Proves sender identity
- **Integrity:** Detects message tampering
- **Non-repudiation:** Sender can't deny signing (only they have private key)

**Common algorithms:**

- **RSA signatures:** Based on RSA encryption
- **ECDSA (Elliptic Curve Digital Signature Algorithm):** More efficient than RSA
- **EdDSA (Edwards-curve DSA):** Modern, fast, secure (used in Signal)

**Use cases:**

- Code signing (verify software publisher)
- Email signatures (S/MIME, PGP)
- Document signing (PDF signatures)
- Blockchain transactions

**French term:** _Signature numérique_

---

### Symmetric vs. Asymmetric Cryptography

| Aspect               | Symmetric (Symétrique)            | Asymmetric (Asymétrique)               |
| -------------------- | --------------------------------- | -------------------------------------- |
| **Keys**             | 1 shared secret key               | 2 keys: public + private               |
| **Speed**            | Fast (hardware acceleration)      | Slow (100-1000x slower)                |
| **Key distribution** | Hard (how to share key securely?) | Easy (public key can be shared openly) |
| **Use case**         | Bulk data encryption              | Key exchange, digital signatures       |
| **Algorithms**       | AES, ChaCha20, 3DES               | RSA, ECC, Diffie-Hellman               |
| **Key size**         | 128-256 bits                      | 2048-4096 bits (RSA), 256 bits (ECC)   |

**Hybrid approach (used in TLS/HTTPS):**

1. Use **asymmetric** crypto to exchange a symmetric key securely
2. Use **symmetric** crypto to encrypt the actual data (fast)

---

## Layer 3 — Worked Examples

### Example 1: Symmetric Encryption (AES)

**Scenario:** Encrypt a file before uploading to cloud storage

**Algorithm:** AES-256-CBC (Advanced Encryption Standard, 256-bit key, Cipher Block Chaining mode)

**Process:**

**1. Key generation:**

```
Generate random 256-bit key (32 bytes):
Key = 0x3a5f9c8e2b7d4f6a1e8c3b5d7f9e1a3c4b6d8f1e2a4c6e8d0f2b4a6c8e1d3f5a
```

**2. Encryption:**

```
Plaintext: "Confidential Report 2026.pdf" (file content)
Algorithm: AES-256-CBC
IV (Initialization Vector): Random 16 bytes (required for CBC mode)

Ciphertext = AES_Encrypt(Plaintext, Key, IV)
Result: 0x7f3e9a1c5b8d2f4e6a9c1d3f5b7e9a2c... (unreadable binary)
```

**3. Storage:**

```
Upload to cloud:
  - Ciphertext (encrypted file)
  - IV (can be stored in plaintext, doesn't need to be secret)
  - Key is stored securely locally (NOT uploaded)
```

**4. Decryption (when downloading):**

```
Download ciphertext + IV
Use stored key:
Plaintext = AES_Decrypt(Ciphertext, Key, IV)
Result: Original file content restored
```

**Security note:**

- **Key security:** If key is compromised, all files encrypted with it are compromised
- **IV randomness:** Must use unique random IV for each encryption (prevents pattern analysis)
- **Key storage:** Store key in OS keychain, hardware security module (HSM), or password manager

---

### Example 2: Hashing for Password Storage

**Scenario:** Store user passwords securely in database

**WRONG approach (plaintext):**

```
Database:
  username: alice, password: MyPassword123
  username: bob, password: SecretPass456

Problem: Database breach → all passwords stolen in plaintext
```

**WRONG approach (simple hash):**

```
Database:
  username: alice, password_hash: 5f4dcc3b5aa765d61d8327deb882cf99 (MD5)
  username: bob, password_hash: e38ad214943daad1d64c102faec29de4afe9da3d (SHA-1)

Problems:
  1. MD5/SHA-1 are broken, fast to crack
  2. No salt → rainbow tables can crack instantly
  3. Same password = same hash (reveals password reuse)
```

**CORRECT approach (bcrypt with salt):**

```
User registration:
  1. User enters password: "MyPassword123"
  2. Generate random salt (unique per user): "a92jd83k"
  3. Hash with bcrypt (10 rounds, slow by design):
     hash = bcrypt("MyPassword123", "a92jd83k", rounds=10)
     → $2b$10$a92jd83kf... (salt embedded in hash string)
  4. Store in database:
     username: alice
     password_hash: $2b$10$a92jd83kf8e3a9c2e7b1d4f6a (contains salt + hash)

User login:
  1. User enters password: "MyPassword123"
  2. Retrieve stored hash from database
  3. Extract salt from hash string
  4. Recompute: bcrypt("MyPassword123", extracted_salt, rounds=10)
  5. If computed_hash == stored_hash → password correct

Security benefits:
  - Slow hashing (10 rounds = ~100ms per attempt) → brute force takes years
  - Unique salt per user → rainbow tables useless
  - Even if two users have same password, hashes are different
```

---

### Example 3: Asymmetric Encryption & Digital Signatures

**Scenario:** Alice wants to send a confidential, authenticated message to Bob

**Setup:**

```
Bob generates RSA key pair:
  Public key (can share with anyone): 0x3048... (2048 bits)
  Private key (kept secret): 0x30820... (2048 bits)

Alice knows Bob's public key (Bob published it)
```

**Process:**

**Step 1: Encrypt message (for confidentiality)**

```
Alice:
  Plaintext: "Meet at 5pm tomorrow. -Alice"
  Encrypts with Bob's public key:
    Ciphertext = RSA_Encrypt(Plaintext, Bob_PublicKey)

  Result: 0x8f3a9c2e... (only Bob can decrypt with his private key)
```

**Step 2: Sign message (for authentication)**

```
Alice:
  1. Hash the plaintext: SHA-256("Meet at 5pm...") → digest
  2. Encrypt digest with Alice's private key → signature
  3. Send: Ciphertext + Signature

Alice sends to Bob: [Ciphertext, Signature]
```

**Step 3: Bob receives and verifies**

```
Bob:
  1. Decrypt ciphertext with his private key:
     Plaintext = RSA_Decrypt(Ciphertext, Bob_PrivateKey)
     → "Meet at 5pm tomorrow. -Alice"

  2. Verify signature:
     - Hash the plaintext: SHA-256("Meet at 5pm...") → digest_computed
     - Decrypt signature with Alice's public key: digest_signature
     - If digest_computed == digest_signature → message is authentic

  Result: Bob knows:
    - Message is confidential (only he could decrypt it)
    - Message is from Alice (only she could sign it)
    - Message is unmodified (hash matches)
```

**Security properties achieved:**

- ✅ **Confidentiality:** Only Bob can read (encrypted with his public key)
- ✅ **Authentication:** Message is from Alice (signed with her private key)
- ✅ **Integrity:** Message hasn't been tampered (hash verification)
- ✅ **Non-repudiation:** Alice can't deny sending (only she has her private key)

---

### Example 4: TLS/HTTPS Handshake (Hybrid Cryptography)

**Scenario:** User visits `https://bank.com` — how does encryption work?

**TLS Handshake (simplified):**

**1. Client Hello:**

```
Browser → Server:
  "I support these cipher suites: TLS_AES_256_GCM, TLS_CHACHA20_POLY1305..."
  "Here's a random nonce: 0x3a5f9c8e..."
```

**2. Server Hello + Certificate:**

```
Server → Browser:
  "Let's use TLS_AES_256_GCM"
  "Here's my certificate (contains public key, signed by Certificate Authority)"
  "Here's my random nonce: 0x7b1d4f6a..."
```

**3. Browser verifies certificate:**

```
Browser:
  1. Extract server's public key from certificate
  2. Verify certificate signature using CA's public key (already trusted in browser)
  3. If valid → server is authentic bank.com
```

**4. Key exchange (asymmetric):**

```
Browser:
  1. Generate random pre-master secret: 0x2e7b9c1d...
  2. Encrypt with server's public key: RSA_Encrypt(pre_master_secret, server_public_key)
  3. Send to server

Server:
  1. Decrypt with private key: RSA_Decrypt(ciphertext, server_private_key)
  2. Both now have pre-master secret
```

**5. Derive session key (symmetric):**

```
Both browser and server:
  session_key = KDF(pre_master_secret, client_nonce, server_nonce)
  → Generates 256-bit AES key
```

**6. Encrypted communication (symmetric):**

```
All subsequent data:
  Browser → Server: AES_Encrypt(HTTP_request, session_key)
  Server → Browser: AES_Encrypt(HTTP_response, session_key)

Speed: Thousands of requests per second (AES is fast)
Security: Session key is unique per connection, discarded after
```

**Why hybrid?**

- **Asymmetric (RSA):** Used only for key exchange (slow but solves key distribution problem)
- **Symmetric (AES):** Used for bulk data (fast, efficient)

**Result:** Secure, authenticated, confidential connection between browser and bank.

---

## Layer 4 — Edge Cases, Nuances, and Limitations

### Edge Case 1: Key Length vs. Security

**Question:** How long should keys be?

**Analysis by algorithm:**

| Algorithm            | Minimum Secure | Recommended | Overkill  |
| -------------------- | -------------- | ----------- | --------- |
| **AES (symmetric)**  | 128 bits       | 256 bits    | N/A       |
| **RSA (asymmetric)** | 2048 bits      | 3072 bits   | 4096 bits |
| **ECC (asymmetric)** | 224 bits       | 256 bits    | 384 bits  |

**Key equivalence:**

- **AES-128 ≈ RSA-3072 ≈ ECC-256** (roughly equivalent security)

**Why RSA needs longer keys:**

- Mathematical structure allows faster attacks than brute force
- Factoring large numbers is easier than brute-forcing AES

**Quantum computing impact:**

- **AES:** Quantum computers halve effective key length (AES-256 → effective 128 bits)
- **RSA/ECC:** Broken by Shor's algorithm (quantum computers can factor efficiently)
- **Post-quantum:** NIST standardizing quantum-resistant algorithms (CRYSTALS-Kyber, Dilithium)

**Recommendation:** Use **AES-256** and **RSA-3072+** (or ECC-256+) for new systems. Plan for post-quantum migration.

---

### Edge Case 2: ECB Mode Vulnerability (Block Cipher Pitfall)

**Problem:** Using wrong mode with block ciphers leaks information

**ECB (Electronic Codebook) — NEVER USE:**

```
Plaintext: "AAAAAAAAAAAAAAAA" (repeated pattern)
ECB mode: Each block encrypted independently
Ciphertext: [Block1][Block1][Block1][Block1] (same ciphertext blocks)

Result: Patterns in plaintext → patterns in ciphertext (information leak)
```

**Famous example:** ECB penguin

- Original image: Tux the Linux penguin (clear outline)
- Encrypted with AES-ECB: Penguin outline still visible in ciphertext
- Reason: Same pixel colors → same ciphertext blocks

**Correct modes:**

- **CBC (Cipher Block Chaining):** Each block depends on previous (requires IV)
- **GCM (Galois/Counter Mode):** Authenticated encryption (encryption + MAC in one)
- **CTR (Counter Mode):** Turns block cipher into stream cipher

**Lesson:** **Algorithm choice is half the battle. Mode selection matters equally.**

---

### Edge Case 3: Timing Attacks on Cryptographic Implementations

**Problem:** Cryptographic code that takes different time based on secret values leaks information

**Vulnerable password comparison:**

```python
def check_password(user_input, stored_hash):
    if user_input == stored_hash:  # String comparison stops at first difference
        return True
    return False

Attack:
  Try: "a0000000" → returns False in 1μs (fails at position 0)
  Try: "b0000000" → returns False in 1μs (fails at position 0)
  Try: "c0000000" → returns False in 2μs (fails at position 1) ← FOUND FIRST CHAR!
```

**Attacker learns:** First character is 'c' (took longer to fail)

**Secure comparison (constant-time):**

```python
def check_password_secure(user_input, stored_hash):
    result = 0
    for a, b in zip(user_input, stored_hash):
        result |= ord(a) ^ ord(b)  # XOR all bytes, always checks all
    return result == 0  # Same time regardless of where difference is
```

**Other timing attacks:**

- **RSA signature verification:** Timing leaks private key bits
- **Cache timing:** Observing CPU cache behavior reveals encryption keys

**Lesson:** **Cryptographic implementations must be constant-time.** Use vetted libraries (OpenSSL, libsodium), don't roll your own.

---

### Limitation 1: Cryptography Doesn't Solve Key Management

**Misconception:** "I encrypted everything with AES-256, so I'm secure."

**Reality:** If keys are stored insecurely, encryption is worthless.

**Common key management failures:**

- **Hardcoded keys in source code:** Keys committed to Git → public repository → exposed
- **Keys in environment variables:** Still accessible to attackers with server access
- **Weak password-based encryption:** User password → derive key → weak password = weak key

**Proper key management:**

- **Hardware Security Modules (HSM):** Keys never leave secure hardware
- **Key Management Services (KMS):** AWS KMS, Azure Key Vault, Google Cloud KMS
- **Envelope encryption:** Encrypt data with data key, encrypt data key with master key (stored in KMS)
- **Key rotation:** Change keys periodically (yearly/quarterly)
- **Key destruction:** Securely delete old keys when no longer needed

**Lesson:** **Cryptography is 20% algorithm choice, 80% key management.**

---

### Limitation 2: Encrypted Data Doesn't Mean Private Data

**Problem:** Metadata, access patterns, and traffic analysis leak information even when content is encrypted.

**Examples:**

**1. Traffic analysis:**

```
Encrypted messaging app (Signal, WhatsApp):
  - Message content is encrypted ✅
  - But metadata visible:
    → Who messaged whom (phone numbers)
    → When messages were sent (timestamps)
    → Message sizes (approximate)
    → Location (IP address)

Attacker learns: "Alice and Bob exchanged 50 messages on Jan 15, likely planning something"
```

**2. Search pattern leakage:**

```
Encrypted database:
  - Data is encrypted ✅
  - But queries reveal patterns:
    → "SELECT * FROM users WHERE name = ?" (query structure visible)
    → Same search term → same encrypted token (deterministic encryption)

Attacker learns: "This encrypted value was searched 100 times, probably a common name"
```

**3. File system metadata:**

```
Encrypted disk (BitLocker, FileVault):
  - File contents encrypted ✅
  - But filesystem metadata visible:
    → File names (document-2026-04-27.pdf)
    → File sizes (15MB)
    → Directory structure (C:\Users\Alice\SecretProject\)

Attacker learns: "User has 50 files in SecretProject folder, total 500MB"
```

**Mitigations:**

- **Tor/VPN:** Hide IP addresses, traffic routing
- **Padding:** Add dummy data to hide real message sizes
- **Oblivious RAM:** Hide access patterns in encrypted databases
- **Filename encryption:** Encrypt file names and metadata (VeraCrypt)

**Lesson:** **Cryptography protects content, not always context.** Consider metadata leakage.

---

## Active Recall Prompts

### Understanding Questions

1. **Symmetric vs. Asymmetric:** Without looking, explain the difference. Give one example algorithm for each and one use case.

2. **Hashing properties:** What makes a hash function secure? Why is MD5 broken but SHA-256 still secure?

3. **Digital signatures:** Walk through the signature creation and verification process. What properties does it provide?

---

### Application Questions

4. **Algorithm selection:** You're building a secure file storage system. For each requirement, choose the appropriate cryptographic primitive:
   - Encrypt files at rest: ****\_\_\_****
   - Verify file hasn't been tampered: ****\_\_\_****
   - Prove who uploaded the file: ****\_\_\_****
   - Store user passwords: ****\_\_\_****

5. **Hybrid cryptography:** Explain why TLS uses both RSA (asymmetric) and AES (symmetric). Why not use RSA for everything?

6. **Key length:** A colleague suggests using AES-128 because "128 bits is enough." Another suggests AES-512 for "maximum security." What would you recommend and why?

---

### Transfer Questions

7. **Real-world attack:** Research the **Heartbleed vulnerability (2014)**. How did it break TLS security? What cryptographic property did it violate?

8. **Tool exploration:** Use `openssl` command-line tool to:
   - Generate an RSA key pair
   - Encrypt a file with AES-256
   - Compute SHA-256 hash of a file
     Document the commands and outputs.

9. **Post-quantum impact:** Research NIST's post-quantum cryptography standards (2024). Which algorithms are being standardized? How will they replace RSA/ECC?

10. **Cryptanalysis:** Choose one historical cipher (Caesar, Vigenère, Enigma). Explain:
    - How it works
    - How it was broken
    - What modern cryptography principle would have prevented the break

---

## References

### Primary Sources

- **Course:** IFT2830 - Sécurité des systèmes informatiques (UdeM)
  Lectures: [Cryptography Fundamentals](../../../05_references/course-materials/IFT2830_course-materials/)

### Textbooks & Standards

- Schneier, B. (2015). _Applied Cryptography_ (2nd ed.). Wiley. — Classic reference
- Ferguson, N., Schneier, B., & Kohno, T. (2010). _Cryptography Engineering_. Wiley. — Practical implementation
- **NIST FIPS 197** — AES specification
- **NIST FIPS 180-4** — SHA-2 specification
- **RFC 5246** — TLS 1.2 protocol
- **RFC 8446** — TLS 1.3 protocol

### Online Resources

- **CryptoHack** — Interactive cryptography challenges (cryptohack.org)
- **Crypto101** — Free cryptography course (crypto101.io)
- **NIST Post-Quantum Cryptography** — https://csrc.nist.gov/projects/post-quantum-cryptography

### Tools

- **OpenSSL** — Cryptographic toolkit (command-line)
- **libsodium** — Modern, easy-to-use crypto library
- **Cryptool** — Educational cryptography software
- **KeyCzar** — High-level crypto library (deprecated, but educational)

### Real-World Incidents

- **Heartbleed (2014)** — OpenSSL memory leak vulnerability (CVE-2014-0160)
- **POODLE (2014)** — SSL 3.0 padding oracle attack
- **ROBOT (2017)** — RSA padding oracle attack on TLS
- **ROCA (2017)** — Weak RSA key generation in smart cards

### Academic Research

- Katz, J., & Lindell, Y. (2020). _Introduction to Modern Cryptography_ (3rd ed.). CRC Press.
- Boneh, D., & Shoup, V. (2020). _A Graduate Course in Applied Cryptography_. (free online)

---

## Related Content

### Theory Modules

- **Next:** [Symmetric Encryption](symmetric-encryption.md) — Deep dive into AES, ChaCha20
- **Next:** [Asymmetric Encryption](asymmetric-encryption.md) — RSA, ECC, key exchange
- **Next:** [Hashing & MACs](hashing-macs.md) — SHA-2, SHA-3, HMAC, password hashing
- **Related:** [Password Attacks](../03-offensive-security/password-attacks.md) — Cracking hashes

### Examples

- [AES File Encryption](../../../02_examples/01-cryptography/aes-file-encryption/) — Practical symmetric crypto
- [RSA Key Generation & Signing](../../../02_examples/01-cryptography/rsa-signing/) — Asymmetric crypto demo
- [TLS Handshake Analysis](../../../02_examples/02-network-security/tls-handshake/) — Hybrid crypto in action

### Exercises

- [Hash Collisions Lab](../../../03_exercises/01-cryptography/hash-collisions/) 🟢 — Understanding hash security
- [Implement Caesar Cipher](../../../03_exercises/01-cryptography/caesar-cipher/) 🟢 — Classical crypto
- [Break Weak Encryption](../../../03_exercises/01-cryptography/break-weak-crypto/) 🟡 — Cryptanalysis practice

### Tools & Resources

- **Crypto Tools:** `04_resources/tools/cryptography/`
- **OpenSSL Cheatsheet:** `04_resources/tools/cryptography/openssl-cheatsheet.md`
- **Algorithm Comparison:** `04_resources/tools/cryptography/algorithm-comparison.xlsx`

---

## Personal Insights & Notes

### Study Notes

_Record your observations, "aha" moments, and connections here._

**Example:**

- "Encryption ≠ Hashing. Encryption is two-way (reversible), hashing is one-way (irreversible)."
- "TLS handshake uses asymmetric for key exchange, symmetric for data. Hybrid = best of both worlds."

---

### Real-World Connections

_Link this concept to incidents, news, or work experience._

**Example:**

- "Heartbleed — not a cryptographic algorithm failure, but an implementation bug. Reminds me: vetted libraries are critical."

---

### Questions & Confusion

_Track what's unclear or needs deeper investigation._

**Example:**

- "How exactly does elliptic curve cryptography work? Need to study the math behind ECC."

---

### Exam/Interview Prep

_Key points to remember for assessments._

**Exam focus (IFT2830):**

- Symmetric vs Asymmetric: Clé partagée vs. Clé publique/privée
- Hashing: Fonction à sens unique, résistance aux collisions
- Signature numérique: Chiffre le hachage avec clé privée, vérifie avec clé publique
- Modes de chiffrement: CBC, GCM (jamais ECB)
- Sel (Salt): Valeur aléatoire unique par utilisateur, défend contre tables arc-en-ciel

**Interview talking points:**

- "Never roll your own crypto. Use vetted libraries like OpenSSL, libsodium, or language-standard crypto APIs."
- "Cryptography is 20% algorithm choice, 80% secure implementation and key management."
- "Post-quantum transition is happening now. RSA/ECC will be replaced by CRYSTALS-Kyber and Dilithium."

---

## Change Log

| Date       | Change                        | Reason                                                       |
| ---------- | ----------------------------- | ------------------------------------------------------------ |
| 2026-04-27 | Created module                | Cryptography fundamentals for theory section                 |
| 2026-04-27 | Added primitives              | Encryption, hashing, MAC, digital signatures                 |
| 2026-04-27 | Added symmetric vs asymmetric | Comparison table and hybrid approach                         |
| 2026-04-27 | Added worked examples         | AES encryption, password hashing, RSA signing, TLS handshake |
| 2026-04-27 | Added edge cases              | ECB vulnerability, timing attacks, key management            |
| 2026-04-27 | Integrated French terminology | Bilingual support throughout                                 |
