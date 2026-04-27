# Symmetric Encryption — Chiffrement Symétrique

| Property          | Value                                         |
| ----------------- | --------------------------------------------- |
| **Topic**         | Symmetric Encryption / Chiffrement Symétrique |
| **Domain**        | 01-cryptography                               |
| **Difficulty**    | 🟡 Intermediate                               |
| **Prerequisites** | [Cryptography Basics](cryptography-basics.md) |
| **Learning Time** | 60-75 minutes                                 |
| **Status**        | ✅ Complete                                   |

---

## Review Schedule

- [ ] Day 2 — First review after initial study
- [ ] Week 1 — Consolidation review
- [ ] Month 1 — Long-term retention check
- [ ] Month 3 — Mastery verification

---

## Quick Summary

**What:** Symmetric encryption uses the **same secret key** for both encryption and decryption. Fast, efficient, but requires secure key distribution.

**Offensive:** Weak symmetric encryption (short keys, ECB mode, obsolete algorithms like DES) can be broken through brute force or cryptanalysis.
**Defensive:** Modern symmetric encryption (AES-256, proper modes like GCM, strong key management) provides strong confidentiality for data at rest and in transit.

**Why it matters:** Symmetric encryption is the **workhorse of cryptography**—used for disk encryption (BitLocker, FileVault), file encryption, VPNs, and bulk data encryption in TLS. Understanding stream vs block ciphers, cipher modes, and algorithm selection is foundational.

---

## Prerequisites

**Required knowledge:**

- [Cryptography Basics](cryptography-basics.md) — Encryption fundamentals, plaintext/ciphertext
- Basic binary operations (XOR)
- Understanding of confidentiality (CIA triad)

**Quick check:** Do you know the difference between encryption and hashing? Can you explain what a "key" is? If yes, you're ready.

---

## Layer 1 — Intuition

Symmetric encryption is like a lockbox with **one key** that both locks and unlocks it:

🔒 **Encryption:** Lock the box with the key (plaintext → ciphertext)
🔓 **Decryption:** Unlock the box with **the same key** (ciphertext → plaintext)

**Key insight:** Both sender and receiver must have the **same secret key**. If an attacker gets the key, all past and future messages are compromised.

**Analogy:**

- You and your friend share a secret code (key)
- You write a message in the code (encrypt)
- Your friend decodes it using the same code (decrypt)
- If someone steals your codebook (key), they can read all your messages

---

## Layer 2 — Formal Definitions

### Symmetric Encryption — Chiffrement Symétrique

**Definition:** Cryptographic system where the same secret key K is used for both encryption E and decryption D:

```
Encryption: C = E_K(P)  (Ciphertext = Encrypt with Key K of Plaintext)
Decryption: P = D_K(C)  (Plaintext = Decrypt with Key K of Ciphertext)

Property: D_K(E_K(P)) = P  (Decryption reverses encryption)
```

**Key characteristics:**

- **Speed:** Very fast (hardware acceleration available)
- **Key length:** Typically 128-256 bits
- **Security:** Security depends entirely on key secrecy (Kerckhoffs's principle)
- **Key distribution problem:** How do you share the key securely?

**French term:** _Chiffrement symétrique_

---

### Stream Ciphers vs Block Ciphers

Symmetric algorithms are divided into two categories based on how they process data:

| Aspect              | Stream Cipher (Chiffrement de flux) | Block Cipher (Chiffrement par bloc)        |
| ------------------- | ----------------------------------- | ------------------------------------------ |
| **Processing unit** | 1 bit or 1 byte at a time           | Fixed-size blocks (64, 128, 256 bits)      |
| **Speed**           | Very fast for small data            | Optimized for large data                   |
| **Use case**        | Real-time streaming (voice, video)  | Files, disks, network packets              |
| **Examples**        | RC4, ChaCha20, Salsa20              | AES, DES, 3DES, Blowfish                   |
| **Complexity**      | Simpler                             | More complex (requires modes of operation) |

---

### Stream Ciphers — Chiffrement de Flux

**Definition:** Encrypt data one bit or byte at a time by combining plaintext with a pseudo-random keystream.

**Mechanism:**

```
Keystream = PseudoRandomGenerator(Key, IV)
Ciphertext = Plaintext XOR Keystream
```

**How XOR works:**

```
Plaintext:  0 1 0 1 1 0 0 1
Keystream:  1 0 1 1 0 1 0 0
          ─────────────────  (XOR operation)
Ciphertext: 1 1 1 0 1 1 0 1
```

**Decryption (symmetric XOR property):**

```
Ciphertext: 1 1 1 0 1 1 0 1
Keystream:  1 0 1 1 0 1 0 0
          ─────────────────  (XOR again)
Plaintext:  0 1 0 1 1 0 0 1  (original message restored)
```

**Advantages:**

- Very fast
- No padding required
- Bit-level encryption (works on any data size)

**Disadvantages:**

- **Must never reuse keystream** (key + IV combination)
- Vulnerable to known-plaintext attacks if keystream is reused
- No integrity protection

**French term:** _Chiffrement de flux_

---

### Block Ciphers — Chiffrement par Bloc

**Definition:** Encrypt fixed-size blocks of data (typically 128 bits) at a time using a symmetric key.

**Mechanism:**

```
For each block B of plaintext:
    C_block = EncryptionFunction(B, Key)
```

**Block size:** Most modern block ciphers use **128-bit blocks** (16 bytes)

**Advantages:**

- More structure and security analysis
- Can be used in different modes for different purposes
- Hardware acceleration widely available

**Disadvantages:**

- Requires padding if plaintext is not multiple of block size
- Needs mode of operation (see below)

**French term:** _Chiffrement par bloc_

---

### Classical Substitution Ciphers

Before modern cryptography, substitution and transposition were the main techniques:

#### Mono-alphabetic Substitution (Substitution mono-alphabétique)

**Caesar Cipher example:**

```
Plaintext alphabet:  ABCDEFGHIJKLMNOPQRSTUVWXYZ
Ciphertext alphabet: DEFGHIJKLMNOPQRSTUVWXYZABC  (shift by 3)

Plaintext:  HELLO
Ciphertext: KHOOR
```

**Weakness:** Frequency analysis (E is most common letter in English → reveals the shift)

**French term:** _Substitution mono-alphabétique_

---

#### Homo-alphabetic Substitution (Substitution homo-alphabétique)

**Definition:** One plaintext letter can map to multiple ciphertext letters to hide frequency patterns.

**Example:**

```
A → {ILS, QZT, MNO}  (3 possible ciphertext representations)
Plaintext:  AAA
Ciphertext: ILS-QZT-MNO  (different each time)
```

**Advantage:** Defeats frequency analysis (A appears with different frequencies)

**French term:** _Substitution homo-alphabétique_

---

#### Transposition Cipher (Chiffrement par transposition)

**Definition:** Rearrange letters without changing them.

**Example (Columnar transposition):**

```
Key: CRYPTO (assign numbers by alphabetical order)
     C R Y P T O
     3 5 6 4 2 1

Plaintext written in rows:
     C R Y P T O
     3 5 6 4 2 1
     ─────────────
     A T T A C K
     A T D A W N

Read by columns (by key order):
Column 1 (O): K, N
Column 2 (T): C, W
Column 3 (C): A, A
Column 4 (P): A, A
Column 5 (R): T, T
Column 6 (Y): T, D

Ciphertext: KNCWAAAA TTTD
```

**French term:** _Chiffrement par transposition_

---

## Layer 3 — Worked Examples

### Example 1: Stream Cipher (RC4 conceptual)

**Scenario:** Encrypt "HELLO" using stream cipher

**Step 1: Generate keystream**

```
Key: "SECRET"
IV: "12345"

PseudoRandomGenerator(Key, IV) → Keystream: 0x8A3F2E9B1C...
```

**Step 2: Convert plaintext to binary**

```
H = 0x48 = 01001000
E = 0x45 = 01000101
L = 0x4C = 01001100
L = 0x4C = 01001100
O = 0x4F = 01001111
```

**Step 3: XOR with keystream**

```
H (01001000) XOR keystream[0] (10001010) = 11000010 = 0xC2
E (01000101) XOR keystream[1] (00111111) = 01111010 = 0x7A
L (01001100) XOR keystream[2] (00101110) = 01100010 = 0x62
L (01001100) XOR keystream[3] (10011011) = 11010111 = 0xD7
O (01001111) XOR keystream[4] (00011100) = 01010011 = 0x53
```

**Ciphertext (hex):** `C2 7A 62 D7 53`

**Decryption (recipient with same key):**

```
Generate same keystream with Key + IV
XOR ciphertext with keystream → recovers plaintext
```

**Critical security rule:** **Never reuse (Key, IV) pair!** If you do:

```
C1 = P1 XOR Keystream
C2 = P2 XOR Keystream  (same keystream!)

Attacker computes: C1 XOR C2 = (P1 XOR Keystream) XOR (P2 XOR Keystream)
                                = P1 XOR P2  (keystream cancels out)

If attacker knows P1, they recover P2 = P1 XOR (C1 XOR C2)
```

---

### Example 2: Block Cipher (DES with ECB mode)

**Scenario:** Encrypt "TOPSECRETMESSAGE" with DES

**DES parameters:**

- **Block size:** 64 bits (8 bytes)
- **Key size:** 56 bits (8 bytes with parity)
- **Algorithm:** 16 rounds of substitution and permutation

**Step 1: Divide plaintext into 8-byte blocks**

```
Plaintext: "TOPSECRETMESSAGE"
Block 1: "TOPSECRE" (8 bytes)
Block 2: "TMESSAGE" (8 bytes)
```

**Step 2: Encrypt each block independently (ECB mode)**

```
Key = "MYKEY123" (56-bit effective key)

C1 = DES_Encrypt("TOPSECRE", Key) = 0x3F8A2E9B1C4D5E6F
C2 = DES_Encrypt("TMESSAGE", Key) = 0x7A3C5E9F1B2D4E6A
```

**Ciphertext:** `3F8A2E9B1C4D5E6F 7A3C5E9F1B2D4E6A`

**Problem with ECB mode:**

```
If plaintext has repeated blocks:
  "TOPSECRETOPSECRE" → same first and third blocks

ECB ciphertext:
  C1 = DES("TOPSECRE") = 0x3F8A...
  C2 = DES("TOPSECRE") = 0x3F8A...  (same ciphertext!)

Attacker sees pattern: C1 = C2 → knows plaintext blocks are identical
```

**Lesson:** **Never use ECB mode!** Use CBC, GCM, or CTR instead.

---

### Example 3: Modern Symmetric Encryption (AES-256-GCM)

**Scenario:** Encrypt sensitive file with AES-256-GCM

**AES-GCM parameters:**

- **Block size:** 128 bits (16 bytes)
- **Key size:** 256 bits (32 bytes)
- **Mode:** GCM (Galois/Counter Mode) — authenticated encryption
- **IV size:** 96 bits (12 bytes) — must be unique per encryption

**Step 1: Generate key and IV**

```python
import os
from cryptography.hazmat.primitives.ciphers import Cipher, algorithms, modes
from cryptography.hazmat.backends import default_backend

# Generate random 256-bit key (store securely!)
key = os.urandom(32)  # 32 bytes = 256 bits

# Generate random 96-bit IV (nonce)
iv = os.urandom(12)  # 12 bytes = 96 bits
```

**Step 2: Encrypt**

```python
plaintext = b"Confidential financial report Q4 2026"

# Create AES-GCM cipher
cipher = Cipher(
    algorithms.AES(key),
    modes.GCM(iv),
    backend=default_backend()
)

encryptor = cipher.encryptor()

# Encrypt
ciphertext = encryptor.update(plaintext) + encryptor.finalize()

# Get authentication tag (16 bytes)
tag = encryptor.tag

# Store: IV + Ciphertext + Tag
encrypted_data = iv + ciphertext + tag
```

**Step 3: Decrypt**

```python
# Extract components
iv = encrypted_data[:12]
ciphertext = encrypted_data[12:-16]
tag = encrypted_data[-16:]

# Create cipher with tag
cipher = Cipher(
    algorithms.AES(key),
    modes.GCM(iv, tag),
    backend=default_backend()
)

decryptor = cipher.decryptor()

# Decrypt and verify
plaintext = decryptor.update(ciphertext) + decryptor.finalize()
# If tag doesn't match, raises cryptography.exceptions.InvalidTag
```

**Security guarantees:**

- ✅ **Confidentiality:** Plaintext hidden
- ✅ **Integrity:** Tag verifies data hasn't been tampered
- ✅ **Authenticity:** Tag proves data came from holder of key

---

### Example 4: Triple DES (3DES) Encryption

**Why 3DES exists:** DES (56-bit key) is too weak (brute-forced in 1999). 3DES applies DES three times for effective 112-bit security.

**3DES operation (EDE mode — Encrypt-Decrypt-Encrypt):**

```
Key1, Key2, Key3 (three 56-bit DES keys)

Encryption:
  C = DES_Encrypt(Key3, DES_Decrypt(Key2, DES_Encrypt(Key1, Plaintext)))

Decryption:
  P = DES_Decrypt(Key1, DES_Encrypt(Key2, DES_Decrypt(Key3, Ciphertext)))
```

**Why DES_Decrypt in the middle?**

- Backward compatibility: If Key1 = Key2 = Key3, 3DES becomes single DES

**3DES keying options:**

1. **Keying Option 1:** Three independent keys (168-bit key, 112-bit effective security due to meet-in-the-middle)
2. **Keying Option 2:** Key1 = Key3 ≠ Key2 (112-bit key)
3. **Keying Option 3:** Key1 = Key2 = Key3 (56-bit key, equivalent to DES — not recommended)

**Example encryption:**

```
Plaintext: "HELLO123" (8 bytes)
Key1: "SECRET1!"
Key2: "SECRET2!"
Key3: "SECRET3!"

Step 1: DES_Encrypt(Plaintext, Key1) → Intermediate1
Step 2: DES_Decrypt(Intermediate1, Key2) → Intermediate2
Step 3: DES_Encrypt(Intermediate2, Key3) → Ciphertext
```

**Status:** 3DES is **deprecated** (NIST phasing out by 2023). Use AES instead.

---

## Layer 4 — Edge Cases, Nuances, and Limitations

### Edge Case 1: Block Cipher Modes of Operation

**Problem:** Block ciphers only encrypt fixed-size blocks. How do you encrypt data larger than one block? **Answer:** Modes of operation.

#### ECB (Electronic Codebook) — **NEVER USE**

```
Each block encrypted independently
Same plaintext block → same ciphertext block (pattern leakage)
```

**Example vulnerability (ECB Penguin):**

```
Original image: Tux penguin (Linux logo)
Encrypted with AES-ECB: Penguin outline still visible
Reason: Large areas of same color → identical ciphertext blocks
```

**Lesson:** ECB is **not semantically secure**.

---

#### CBC (Cipher Block Chaining) — **Good**

```
C[0] = IV (Initialization Vector, random, sent in clear)
C[i] = Encrypt(P[i] XOR C[i-1], Key)

Decryption:
P[i] = Decrypt(C[i], Key) XOR C[i-1]
```

**Properties:**

- ✅ Each ciphertext block depends on all previous plaintext blocks
- ✅ Same plaintext → different ciphertext (if IV is random)
- ⚠️ **Padding oracle attacks** possible if implementation reveals padding errors
- ⚠️ No built-in integrity protection

**Use case:** Legacy systems, file encryption (with separate MAC)

---

#### CTR (Counter Mode) — **Good**

```
Turn block cipher into stream cipher:
Keystream[i] = Encrypt(Nonce || Counter[i], Key)
C[i] = P[i] XOR Keystream[i]
```

**Properties:**

- ✅ Parallelizable (encrypt blocks independently)
- ✅ No padding required
- ✅ Random access (can decrypt any block without decrypting previous blocks)
- ⚠️ **Must never reuse (Key, Nonce) pair**

**Use case:** Disk encryption, network protocols

---

#### GCM (Galois/Counter Mode) — **Best (Authenticated Encryption)**

```
GCM = CTR mode + GMAC (authentication tag)

Provides:
  - Confidentiality (CTR encryption)
  - Integrity (GMAC tag)
  - Authenticity (tag proves possession of key)
```

**Properties:**

- ✅ Authenticated Encryption with Associated Data (AEAD)
- ✅ Parallelizable
- ✅ High performance (hardware acceleration)
- ✅ Single-pass (encrypt and authenticate simultaneously)

**Use case:** TLS 1.3, IPsec, modern protocols

---

### Edge Case 2: Padding in Block Ciphers

**Problem:** Plaintext may not be exact multiple of block size.

**Solution:** Padding schemes.

#### PKCS#7 Padding

```
Block size: 16 bytes
Plaintext: "HELLO" (5 bytes)

Padding needed: 16 - 5 = 11 bytes
Padding value: 0x0B (11 in hex)

Padded plaintext: "HELLO\x0B\x0B\x0B\x0B\x0B\x0B\x0B\x0B\x0B\x0B\x0B"
                   (5 bytes + 11 bytes = 16 bytes)
```

**Edge case: Plaintext is exact multiple of block size**

```
Plaintext: "HELLOWORLDHELLO!" (16 bytes, exact block size)

Must add full padding block:
Padded: "HELLOWORLDHELLO!\x10\x10\x10\x10\x10\x10\x10\x10\x10\x10\x10\x10\x10\x10\x10\x10"
        (16 bytes + 16 bytes padding = 32 bytes)

Why? Decryptor needs to distinguish "no padding" from "padding value 0x01"
```

**Padding Oracle Attack:**

```
If server reveals whether padding is valid:
  - Attacker can decrypt ciphertext byte-by-byte
  - No key needed!

Defense: Use authenticated encryption (GCM) or constant-time padding validation
```

---

### Edge Case 3: Key Derivation from Passwords

**Problem:** Users choose weak passwords. How to derive strong encryption keys?

**Solution:** Key Derivation Functions (KDF)

#### PBKDF2 (Password-Based Key Derivation Function 2)

```
Key = PBKDF2(
    password,
    salt,        # Random value (prevent rainbow tables)
    iterations,  # 100,000+ (slow down brute force)
    key_length   # 256 bits for AES-256
)
```

**Example:**

```python
from cryptography.hazmat.primitives.kdf.pbkdf2 import PBKDF2HMAC
from cryptography.hazmat.primitives import hashes
import os

password = b"MyPassword123"
salt = os.urandom(16)  # 16 bytes random salt

kdf = PBKDF2HMAC(
    algorithm=hashes.SHA256(),
    length=32,  # 32 bytes = 256 bits
    salt=salt,
    iterations=480000,  # OWASP 2023 recommendation
)

key = kdf.derive(password)
# key is now a strong 256-bit encryption key
```

**Why iterations matter:**

```
Attacker brute-forcing:
  - 1 iteration: 1 billion passwords/sec → cracks in hours
  - 480,000 iterations: 2,000 passwords/sec → takes months/years
```

---

### Limitation 1: Key Distribution Problem

**Problem:** Symmetric encryption requires both parties to have the same secret key. How do you share it securely?

**Naive approach (WRONG):**

```
Alice: "Hey Bob, our encryption key is: 3a5f9c8e..."
Attacker intercepts message → key compromised
```

**Solutions:**

1. **Pre-shared key (PSK):**
   - Exchange key in person (USB drive, physical meeting)
   - Use case: Small groups, high-security environments

2. **Key exchange protocol (Diffie-Hellman):**
   - Generate shared secret over insecure channel
   - Use case: TLS handshake

3. **Hybrid encryption:**
   - Use asymmetric crypto (RSA) to exchange symmetric key
   - Then use symmetric crypto for bulk data
   - Use case: TLS, PGP, S/MIME

**Lesson:** **Symmetric encryption alone is insufficient for most real-world use cases.** Must be combined with key exchange or asymmetric crypto.

---

### Limitation 2: No Non-Repudiation

**Problem:** Symmetric encryption proves confidentiality, but not sender identity.

**Example:**

```
Alice and Bob share key K
Alice sends encrypted message: C = Encrypt("I agree to the contract", K)
Bob receives and decrypts: P = Decrypt(C, K)

Problem: Bob could have created this message himself (he has key K too)
Result: Alice can deny sending it ("Bob forged it")
```

**Solution:** Use digital signatures (asymmetric crypto) for non-repudiation.

---

## Active Recall Prompts

### Understanding Questions

1. **Stream vs Block:** Explain the difference between stream ciphers and block ciphers. Give one example of each and their typical use case.

2. **Cipher modes:** Why is ECB mode insecure? What makes GCM mode better than CBC?

3. **Key reuse:** Why is reusing a (Key, IV) pair in stream ciphers catastrophic? Walk through the attack.

---

### Application Questions

4. **Algorithm selection:** You need to encrypt:
   - A 10GB backup file
   - A real-time video stream
   - An email message

   For each, choose: stream cipher or block cipher? Which mode of operation? Why?

5. **3DES calculation:** If DES has 56-bit keys and 3DES uses three keys, why is 3DES security only 112 bits (not 168 bits)?

6. **Padding attack:** A server returns different error messages for "invalid padding" vs "invalid MAC". Explain how an attacker can exploit this.

---

### Transfer Questions

7. **Real-world analysis:** Research the **WEP vulnerability (2001)**. How did RC4 key reuse lead to complete WiFi security compromise?

8. **Tool exploration:** Use `openssl` to encrypt a file with AES-256-CBC:

   ```bash
   openssl enc -aes-256-cbc -in plaintext.txt -out encrypted.bin
   ```

   Document: how is the key derived from password? Where is the IV stored?

9. **Mode comparison:** Encrypt the same file with ECB and CBC modes. Compare ciphertext patterns. What information leaks in ECB?

10. **Performance benchmark:** Measure encryption speed of AES-128, AES-256, ChaCha20 on your system. Which is fastest? Why?

---

## References

### Primary Sources

- **Course:** IFT2830 - Sécurité des systèmes informatiques (UdeM)
  Final exam materials: [02_theory-final.md](../../../05_references/course-materials/IFT2830_course-materials/02_theory-final.md)

### Standards & Specifications

- **NIST FIPS 197** — Advanced Encryption Standard (AES)
- **NIST SP 800-38A** — Block Cipher Modes of Operation
- **NIST SP 800-38D** — GCM and GMAC specification
- **NIST SP 800-57** — Key Management recommendations

### Academic & Industry

- Schneier, B. (1996). _Applied Cryptography_ (2nd ed.). Wiley. — Chapters on symmetric ciphers
- Rogaway, P., & Shrimpton, T. (2004). "Cryptographic Hash-Function Basics: Definitions, Implications, and Separations." _FSE_.
- McGrew, D., & Viega, J. (2004). "The Galois/Counter Mode of Operation (GCM)." _NIST_.

### Tools & Libraries

- **OpenSSL** — Cryptographic toolkit (command-line and library)
- **cryptography** (Python) — Modern cryptography library
- **libsodium** — High-level crypto library (uses ChaCha20-Poly1305)
- **Bouncy Castle** — Java cryptography library

### Real-World Incidents

- **WEP broken (2001)** — RC4 key reuse in WiFi encryption
- **BEAST attack (2011)** — CBC mode vulnerability in TLS 1.0
- **POODLE attack (2014)** — Padding oracle in SSL 3.0
- **Sweet32 (2016)** — Birthday attack on 64-bit block ciphers (3DES, Blowfish)

---

## Related Content

### Theory Modules

- **Previous:** [Cryptography Basics](cryptography-basics.md) — Foundational concepts
- **Next:** [Asymmetric Encryption](asymmetric-encryption.md) — Public-key cryptography
- **Related:** [Hashing Functions](hashing-functions.md) — One-way functions

### Examples

- [AES File Encryption](../../../02_examples/01-cryptography/aes-file-encryption/) — Practical symmetric encryption
- [Breaking WEP](../../../02_examples/01-cryptography/breaking-wep/) — Stream cipher key reuse exploitation
- [Padding Oracle Attack](../../../02_examples/01-cryptography/padding-oracle/) — CBC mode vulnerability

### Exercises

- [Caesar Cipher Cryptanalysis](../../../03_exercises/01-cryptography/caesar-cryptanalysis/) 🟢 — Frequency analysis
- [Implement AES-CTR](../../../03_exercises/01-cryptography/implement-ctr/) 🟡 — Mode of operation coding
- [ECB vs CBC Comparison](../../../03_exercises/01-cryptography/ecb-vs-cbc/) 🟢 — Visual pattern analysis

### Tools & Resources

- **Cipher Tools:** `04_resources/tools/cryptography/`
- **OpenSSL Cheatsheet:** `04_resources/tools/cryptography/openssl-cheatsheet.md`
- **Mode Diagrams:** `04_resources/tools/cryptography/cipher-modes-diagrams.pdf`

---

## Personal Insights & Notes

### Study Notes

_Record your observations, "aha" moments, and connections here._

**Example:**

- "XOR is reversible: P XOR K = C, then C XOR K = P. That's why stream ciphers work."
- "GCM = CTR + authentication. Best of both worlds: speed + integrity."

---

### Real-World Connections

_Link this concept to incidents, news, or work experience._

**Example:**

- "WEP broke because RC4 reused keystreams. WiFi security was completely compromised until WPA2."

---

### Questions & Confusion

_Track what's unclear or needs deeper investigation._

**Example:**

- "How exactly does GMAC authentication work in GCM mode? Need to study Galois field arithmetic."

---

### Exam/Interview Prep

_Key points to remember for assessments._

**Exam focus (IFT2830):**

- Chiffrement symétrique: même clé pour chiffrement et déchiffrement
- Chiffrement de flux: bit par bit, rapide, XOR avec keystream
- Chiffrement par bloc: blocs fixes (64, 128 bits), modes (ECB, CBC, CTR, GCM)
- DES: 56 bits (obsolète), 3DES: 112 bits effectifs (déprécié), AES: 128/192/256 bits (recommandé)
- Modes: ECB (vulnérable), CBC (bon), GCM (meilleur - authentification intégrée)
- Problème clé: distribution sécurisée de la clé symétrique

**Interview talking points:**

- "Always use AES-256-GCM for new systems. It provides confidentiality, integrity, and authenticity in one operation."
- "Never use ECB mode. It leaks patterns and is not semantically secure."
- "Symmetric encryption is fast but has a key distribution problem. That's why we use hybrid encryption in TLS."

---

## Change Log

| Date       | Change                        | Reason                                        |
| ---------- | ----------------------------- | --------------------------------------------- |
| 2026-04-27 | Created module                | Symmetric encryption deep dive for final exam |
| 2026-04-27 | Added stream vs block ciphers | Core distinction in symmetric crypto          |
| 2026-04-27 | Added cipher modes            | ECB, CBC, CTR, GCM comparison                 |
| 2026-04-27 | Added classical ciphers       | Historical context (Caesar, transposition)    |
| 2026-04-27 | Added DES, 3DES, AES          | Algorithm evolution and current standards     |
| 2026-04-27 | Integrated French terminology | Bilingual support from IFT2830 materials      |
