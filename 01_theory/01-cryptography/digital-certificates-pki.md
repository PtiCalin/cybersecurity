# Digital Certificates & PKI — Certificats Numériques & Infrastructure à Clé Publique

| Property | Value |
|----------|-------|
| **Topic** | Digital Certificates & PKI / Certificats Numériques & ICP |
| **Domain** | 01-cryptography |
| **Difficulty** | 🟡 Intermediate |
| **Prerequisites** | [Asymmetric Encryption](asymmetric-encryption.md), [Cryptography Basics](cryptography-basics.md) |
| **Learning Time** | 75-90 minutes |
| **Status** | ✅ Complete |

---

## Review Schedule

- [ ] Day 2 — First review after initial study
- [ ] Week 1 — Consolidation review  
- [ ] Month 1 — Long-term retention check
- [ ] Month 3 — Mastery verification

---

## Quick Summary

**What:** Digital certificates are **electronic credentials** that bind a public key to an identity, signed by a trusted third party (Certificate Authority). PKI is the infrastructure that issues, manages, and validates certificates.

**Offensive:** Certificate misuse (stolen certs, rogue CAs), weak validation (domain-only verification), expired certificates, certificate pinning bypass, man-in-the-middle attacks with forged certificates.  
**Defensive:** Certificate pinning, Certificate Transparency logs, OCSP stapling, proper validation (EV certificates), CAA records, short certificate lifetimes (90 days), hardware-backed private keys.

**Why it matters:** Digital certificates are the **foundation of internet trust**—TLS/HTTPS, code signing, email encryption, VPNs, document signing. Understanding certificate validation, PKI hierarchy, and trust models is essential for secure communications.

---

## Prerequisites

**Required knowledge:**
- [Asymmetric Encryption](asymmetric-encryption.md) — Public/private keys, digital signatures
- [Cryptography Basics](cryptography-basics.md) — Hashing, encryption fundamentals

**Quick check:** Do you understand how digital signatures work? Can you explain what a public/private key pair is? If yes, you're ready.

---

## Layer 1 — Intuition

A digital certificate is like a **passport or driver's license** for the internet:

📄 **Certificate contains:**
- Your identity (name, organization, domain)
- Your public key
- Signature from a trusted authority (Certificate Authority)

🔐 **How it proves trust:**
- Government (CA) verifies your identity
- Government signs your passport (CA signs certificate)
- Anyone can verify the government's signature (validate certificate chain)
- Passport proves you are who you claim to be (certificate proves server identity)

**Key insight:** Certificates solve the **public key distribution problem**. How do you know a public key actually belongs to "amazon.com" and not an attacker? Certificate Authority vouches for the binding.

**Analogy:**
- Without certificates: Anyone can claim "I'm your bank, here's my public key" (could be attacker)
- With certificates: "I'm your bank, and Trusted CA has verified and signed my certificate" (verifiable trust)

**French term:** *Certificat numérique*, *Tiers de confiance* (trusted third party / Certificate Authority)

---

## Layer 2 — Formal Definitions

### Digital Certificate — Certificat Numérique

**Definition:** Electronic document that binds a public key to an entity (person, organization, device) and is signed by a trusted third party (Certificate Authority).

**Structure:**
```
Certificate = {
  Version
  Serial Number (unique)
  Signature Algorithm
  Issuer (CA that signed this)
  Validity Period (Not Before, Not After)
  Subject (owner identity)
  Subject Public Key
  Extensions (optional constraints, key usage)
  CA's Digital Signature (over all above fields)
}
```

**Trust model:**
```
1. CA verifies subject's identity (validation process)
2. CA signs certificate with CA's private key
3. Anyone with CA's public key can verify the signature
4. If signature is valid → certificate is authentic → public key is trustworthy
```

**French term:** *Certificat numérique* (digital certificate), *Tiers de confiance* (trusted third party)

---

### Certificate Authority (CA) — Autorité de Certification

**Definition:** Trusted third party that:
- Verifies identities
- Issues digital certificates
- Signs certificates with CA private key
- Maintains certificate revocation lists
- Provides OCSP responders for real-time validation

**Examples:**
- **Root CAs:** DigiCert, Let's Encrypt, Sectigo (formerly Comodo), GlobalSign, IdenTrust
- **Government CAs:** ANTS (France), Gov.ca (Canada), GSA (USA)
- **Internal CAs:** Organization-specific (Active Directory Certificate Services)

**Trust anchor:**
```
Root CA certificates are pre-installed in:
  - Operating systems (Windows, macOS, Linux)
  - Browsers (Firefox maintains own root store)
  - Devices (smartphones, IoT)

When you install OS → ~100-200 root CA certificates installed
These are the "trust anchors" for all certificate validation
```

**French term:** *Autorité de Certification (AC)*

---

### Public Key Infrastructure (PKI) — Infrastructure à Clé Publique (ICP)

**Definition:** Complete system for creating, managing, distributing, using, storing, and revoking digital certificates.

**PKI components:**

#### 1. Certificate Authority (CA) — Autorité de Certification
```
Role: Sign and issue certificates
Responsibilities:
  - Maintain security of CA private key (HSM)
  - Publish Certificate Practice Statement (CPS)
  - Operate according to published policies
  - Respond to compromise incidents
```

#### 2. Registration Authority (RA) — Autorité d'Enregistrement
```
Role: Verify identity before certificate issuance
Responsibilities:
  - Collect identity documentation
  - Validate identity proofs
  - Approve/reject certificate requests
  - Act as CA's front-end (CA does not directly interact with certificate requesters)

Example: Bank branch verifies your identity, then sends request to central CA
```

#### 3. Certificate Revocation List (CRL) — Liste de Révocation de Certificats
```
Role: Published list of revoked certificates
Format:
  - Serial numbers of revoked certificates
  - Revocation date
  - Revocation reason
  - Signed by CA

Problem: CRLs can be large (megabytes) and grow over time
Download frequency: Clients check periodically (every 24 hours)
```

#### 4. Certificate Repository (CR) — Répertoire de Certificats
```
Role: Publicly accessible database of issued certificates
Access: LDAP, HTTP, FTP
Content:
  - Issued certificates
  - CRLs
  - CA certificates
  - Certificate policies

Example: https://crt.sh (Certificate Transparency logs)
```

#### 5. End Entity (Subscriber) — Entité Finale
```
Role: Certificate holder (person, server, device)
Responsibilities:
  - Generate key pair
  - Submit Certificate Signing Request (CSR)
  - Protect private key
  - Use certificate according to policy
  - Request revocation if compromised
```

#### 6. Relying Party (Verifier) — Partie Utilisatrice
```
Role: Entity that validates certificates (your browser, email client)
Responsibilities:
  - Verify certificate signature
  - Check validity period
  - Check revocation status (CRL or OCSP)
  - Validate certificate chain to trusted root
```

**French terms:** *Infrastructure à clé publique (ICP)*, *Autorité de certification (AC)*, *Autorité d'enregistrement (AE)*, *Liste de révocation (LCR)*

---

## Certificate Classes — Validation Levels

Certificates are classified by the rigor of identity verification:

### Class 1 — Individual Email (No Verification)
```
Validation: Email address ownership only
Process: Send verification link to email
Use case: Personal email encryption (S/MIME)
Trust level: Low (attacker can create throwaway email)
Example: Free S/MIME certificates

NOT SUITABLE FOR: Websites, code signing, document signing
```

### Class 2 — Individual (Soft Verification)
```
Validation: Name + email + soft identity check
Process: Cross-reference with database (credit bureau, government DB)
Use case: Personal digital signatures, client authentication
Trust level: Medium
Example: Personal code signing certificates

Note: Less common today, mostly replaced by Class 3
```

### Class 3 — Server & Organization (Domain Validation - DV)
```
Validation: Domain ownership only
Process: 
  - Place file at http://domain.com/.well-known/
  - OR respond to challenge at DNS TXT record
  - OR respond to email to admin@domain.com
Time: Minutes (automated)
Use case: HTTPS websites (90% of certificates)
Trust level: Medium (proves domain control, not organization identity)
Example: Let's Encrypt certificates

Certificate shows:
  Common Name (CN): domain.com
  No organization name
```

### Class 4 — Organization Validation (OV)
```
Validation: Domain + Organization verification
Process:
  - Domain validation (Class 3)
  - + Verify organization existence (government registry)
  - + Verify organization address (phone call)
  - + Verify requester authority (employment verification)
Time: 1-3 days
Use case: Corporate websites, business applications
Trust level: High
Example: DigiCert OV SSL

Certificate shows:
  Common Name (CN): domain.com
  Organization (O): Acme Inc.
  Location (L): San Francisco
  State (ST): California
  Country (C): US
```

### Class 5 — Extended Validation (EV)
```
Validation: Highest rigor
Process:
  - All Class 4 validations
  - + Face-to-face meeting or notarized letter
  - + Verify legal existence (business registration)
  - + Verify physical address (third-party database)
  - + Verify operational status (domain ownership, phone call)
  - + Background check on requester
Time: 1-2 weeks
Use case: Banks, financial institutions, e-commerce
Trust level: Highest
Example: PayPal, banks

Browser UI (deprecated in 2019-2020):
  - Older browsers: Green bar with organization name
  - Modern browsers: Same UI as DV/OV (EV indicators removed due to phishing concerns)

Certificate shows:
  All Class 4 fields + EV-specific policies
```

**French terms:** *Validation de domaine (DV)*, *Validation d'organisation (OV)*, *Validation étendue (EV)*

---

### Special Certificate Types

#### SSL EV (Extended Validation SSL)
```
Same as Class 5, specifically for HTTPS
Displays organization name in certificate details
Deprecated green bar UI (removed 2019-2020 due to phishing concerns)
```

#### Dual-Key Certificate
```
Two key pairs in one certificate:
  - Key 1: Encryption (for confidentiality)
  - Key 2: Signing (for authenticity)

Use case: S/MIME email encryption
Benefit: Separation of concerns (compromise of signature key doesn't break encryption)
```

#### Dual-Sided Certificate (Mutual TLS)
```
Both client and server have certificates
Server validates client certificate (not just password)
Use case: High-security environments (VPN, banking, B2B APIs)

TLS flow:
  1. Client → Server: Hello
  2. Server → Client: Certificate
  3. Client validates server certificate
  4. Server requests client certificate
  5. Client → Server: Certificate
  6. Server validates client certificate
  7. Secure channel established
```

---

## X.509 Standard — Certificate Format

**X.509** is the ITU-T standard defining digital certificate format (RFC 5280).

### X.509 Certificate Structure

```
Certificate:
    Data:
        Version: 3 (0x2)
        Serial Number: 3a:ef:94:... (unique)
        Signature Algorithm: sha256WithRSAEncryption
        Issuer: CN=DigiCert Global Root CA, O=DigiCert Inc, C=US
        Validity
            Not Before: Jan 1 00:00:00 2026 GMT
            Not After : Dec 31 23:59:59 2026 GMT
        Subject: CN=example.com, O=Example Corp, C=US
        Subject Public Key Info:
            Public Key Algorithm: rsaEncryption
                RSA Public-Key: (2048 bit)
                Modulus: 00:b4:3f:...
                Exponent: 65537 (0x10001)
        X509v3 extensions:
            X509v3 Subject Alternative Name:
                DNS:example.com, DNS:www.example.com
            X509v3 Key Usage: critical
                Digital Signature, Key Encipherment
            X509v3 Extended Key Usage:
                TLS Web Server Authentication
            X509v3 CRL Distribution Points:
                URI:http://crl.digicert.com/root.crl
            Authority Information Access:
                OCSP - URI:http://ocsp.digicert.com
    Signature Algorithm: sha256WithRSAEncryption
         3f:8a:2e:9b:... (CA's signature over all above data)
```

### Key X.509 Extensions

#### Subject Alternative Name (SAN)
```
Lists additional identities for certificate
Example:
  SAN: DNS:example.com, DNS:www.example.com, DNS:*.example.com, IP:203.0.113.1

Allows one certificate for multiple domains
```

#### Key Usage
```
Specifies allowed uses for key:
  - Digital Signature (sign messages)
  - Key Encipherment (encrypt symmetric keys)
  - Data Encipherment (encrypt data)
  - Certificate Signing (CA certificates only)
  - CRL Signing (CA certificates only)

Critical extension: If client doesn't understand, must reject certificate
```

#### Extended Key Usage (EKU)
```
Specifies allowed high-level applications:
  - TLS Web Server Authentication (id-kp-serverAuth)
  - TLS Web Client Authentication (id-kp-clientAuth)
  - Code Signing (id-kp-codeSigning)
  - Email Protection (id-kp-emailProtection)

Example: Code signing certificate cannot be used for TLS
```

#### Basic Constraints
```
Is CA: TRUE/FALSE (whether certificate can sign other certificates)
Path Length: Maximum depth of certificate chain

Example:
  Root CA: Is CA=TRUE, Path Length=unlimited
  Intermediate CA: Is CA=TRUE, Path Length=0 (cannot issue sub-CAs)
  End-entity: Is CA=FALSE
```

---

## PKCS — Public-Key Cryptography Standards

**PKCS:** Series of standards by RSA Security (now RSA Labs), defining cryptographic data formats.

### PKCS #1 — RSA Cryptography Standard
```
Defines: RSA key format, encryption/signature schemes
File formats: .pem, .der
Padding: PKCS#1 v1.5 (legacy), OAEP (modern)
Use case: RSA keys, signatures
```

### PKCS #3 — Diffie-Hellman Key Agreement
```
Defines: DH key exchange protocol
Use case: TLS key exchange (pre-ECDHE)
Status: Largely replaced by ECDHE
```

### PKCS #5 — Password-Based Cryptography
```
Defines: PBKDF2 (key derivation from passwords)
Use case: Encrypt private keys with password protection
Example: Encrypted PEM files
```

### PKCS #7 — Cryptographic Message Syntax (CMS)
```
Defines: Format for signed/encrypted data
Use case: S/MIME email, Windows code signing
File format: .p7b, .p7c, .p7m, .p7s
```

### PKCS #8 — Private Key Information Syntax
```
Defines: Private key storage format
Encrypted or unencrypted
Use case: Storing private keys
File format: .pem (with "BEGIN PRIVATE KEY")
```

### PKCS #10 — Certificate Signing Request (CSR)
```
Defines: CSR format
Content:
  - Subject information (CN, O, L, ST, C)
  - Public key
  - Signature (signed by private key to prove possession)

Workflow:
  1. Generate key pair
  2. Create CSR with public key + identity
  3. Send CSR to CA
  4. CA validates identity
  5. CA signs certificate and returns it
```

### PKCS #11 — Cryptographic Token Interface
```
Defines: API for hardware security modules (HSM), smart cards
Use case: Access keys stored in hardware
Example: YubiKey, TPM, HSM devices
```

### PKCS #12 — Personal Information Exchange
```
Defines: Container format for certificate + private key
File format: .p12, .pfx
Encrypted with password
Use case: Export/import certificate bundles
Example: Windows certificate export, Java keystores

Contents:
  - Private key (encrypted)
  - Certificate
  - Optionally: Intermediate certificates, root certificate
```

### Other PKCS Standards

| Standard | Purpose | Status |
|----------|---------|--------|
| PKCS #2 | RSA encryption (incorporated into PKCS #1) | Merged |
| PKCS #4 | RSA key syntax (incorporated into PKCS #1) | Merged |
| PKCS #6 | Extended-Certificate Syntax | Obsolete |
| PKCS #9 | Selected Attribute Types | Active (used in CSR) |
| PKCS #13 | Elliptic Curve Cryptography | Active |
| PKCS #14 | Pseudo-random Number Generation | Draft |
| PKCS #15 | Cryptographic Token Information Format | Active |

**French term:** *Normes PKCS* (PKCS standards)

---

## Trust Models — Modèles de Confiance

How do you know which CAs to trust? Different trust models:

### 1. Direct Trust (Confiance Directe)
```
Trust model: Verify identity in person, exchange public keys directly

Example:
  - Meet face-to-face
  - Exchange USB drives with public keys
  - Fingerprint verification (Signal safety numbers)

Pros: Maximum trust (no third party)
Cons: Doesn't scale (must meet everyone)

Use case: Small groups, high-security environments
```

**French term:** *Confiance directe*

---

### 2. Third-Party Trust (Tiers de Confiance)
```
Trust model: Trust a third party (CA) to verify identities

Example:
  - Install root CA certificates in OS
  - Root CA vouches for all certificates it signs
  - Transitivity: If you trust CA, you trust certificates signed by CA

Pros: Scales well (trust one CA → trust millions of sites)
Cons: Single point of failure (compromised CA → all certificates compromised)

Use case: Internet PKI (TLS/HTTPS)
```

**French term:** *Tiers de confiance*

---

### 3. Hierarchical Trust (Confiance Hiérarchique)
```
Trust model: Tree structure with root CA at top

Structure:
  Root CA (offline, highly secure)
    ↓
  Intermediate CA 1         Intermediate CA 2
    ↓                         ↓
  End-entity certs         End-entity certs

Certificate chain:
  [End-entity] ← signed by [Intermediate] ← signed by [Root]

Validation:
  1. Verify end-entity signature with intermediate's public key
  2. Verify intermediate signature with root's public key
  3. Verify root is in trust store

Pros: 
  - Root key offline (highest security)
  - Intermediate compromise doesn't require root rotation
Cons: 
  - Longer validation chains
  - More complex

Use case: Enterprise PKI, Internet PKI
```

**French term:** *Confiance hiérarchique*

---

### 4. Distributed Trust (Web of Trust) — Confiance Distribuée
```
Trust model: No central authority; users sign each other's keys

Example: PGP/GPG key signing

Process:
  1. Alice meets Bob in person, verifies Bob's key fingerprint
  2. Alice signs Bob's key (creates certificate binding)
  3. Carol trusts Alice
  4. Carol sees Alice signed Bob's key → Carol partially trusts Bob
  5. More signatures on Bob's key → higher trust

Trust levels:
  - Full trust: You signed the key yourself
  - Marginal trust: 1 signature from trusted person
  - Acceptable trust: 3 marginal trusts or 1 full trust

Pros:
  - No single point of failure
  - Democratic/decentralized
Cons:
  - Doesn't scale well
  - Complex trust decisions
  - Key revocation difficult

Use case: PGP email encryption, developer code signing (Debian packages)
```

**French term:** *Confiance distribuée*

---

### 5. Bridge Trust (Confiance Passerelle)
```
Trust model: Connect multiple independent PKI hierarchies

Structure:
  PKI A ← → Bridge CA ← → PKI B

Example:
  - US Government PKI ← → Bridge CA ← → Canadian Government PKI
  - Corporate PKI A ← → Bridge CA ← → Corporate PKI B

How it works:
  1. Bridge CA cross-certifies with Root CA A
  2. Bridge CA cross-certifies with Root CA B
  3. Users in PKI A can validate certificates from PKI B through bridge

Pros:
  - Connects isolated PKI domains
  - Maintains independence (each PKI keeps own policies)
Cons:
  - Complex trust relationships
  - Policy mapping required

Use case: Government PKIs, B2B certificate trust
```

**French term:** *Confiance passerelle* (bridge trust)

---

## Layer 3 — Worked Examples

### Example 1: Certificate Chain Validation (HTTPS)

**Scenario:** Your browser connects to https://example.com

**Step 1: Server sends certificate chain**
```
Server → Browser:
  [Certificate 1: example.com]
    Issued to: CN=example.com
    Issued by: CN=DigiCert TLS RSA SHA256 2020 CA1
    Public key: <server's RSA public key>
    Signature: <signed by intermediate CA>
  
  [Certificate 2: DigiCert Intermediate CA]
    Issued to: CN=DigiCert TLS RSA SHA256 2020 CA1
    Issued by: CN=DigiCert Global Root CA
    Public key: <intermediate CA's public key>
    Signature: <signed by root CA>
  
  [Certificate 3: DigiCert Root CA (optional)]
    Issued to: CN=DigiCert Global Root CA
    Issued by: CN=DigiCert Global Root CA (self-signed)
    Public key: <root CA's public key>
    Signature: <self-signed>
```

**Step 2: Browser validates chain**

```
Step 2a: Find root certificate
  - Browser looks for "DigiCert Global Root CA" in trust store
  - Found ✓ (pre-installed with OS)

Step 2b: Verify intermediate certificate signature
  - Extract signature from Certificate 2
  - Decrypt signature with DigiCert Root public key
  - Compute hash of Certificate 2 (without signature)
  - Compare: decrypted hash == computed hash ✓

Step 2c: Verify end-entity certificate signature
  - Extract signature from Certificate 1
  - Decrypt signature with Intermediate CA public key
  - Compute hash of Certificate 1 (without signature)
  - Compare: decrypted hash == computed hash ✓

Step 2d: Check validity period
  - Current date: April 27, 2026
  - Certificate 1 validity: Jan 1, 2026 - Dec 31, 2026 ✓

Step 2e: Check revocation status (OCSP or CRL)
  - Query OCSP responder: http://ocsp.digicert.com
  - Response: Certificate NOT revoked ✓

Step 2f: Check hostname
  - Certificate CN: example.com
  - Certificate SAN: DNS:example.com, DNS:www.example.com
  - Requested URL: https://example.com ✓

All checks pass → Certificate is valid → Establish TLS connection
```

**What browser verifies:**
- ✅ Certificate chain from end-entity to trusted root
- ✅ All signatures valid
- ✅ No certificate expired
- ✅ Certificate not revoked
- ✅ Hostname matches certificate

**What browser does NOT verify (unless EV/OV):**
- ❌ Organization actually exists
- ❌ Certificate holder has legal right to use domain
- ❌ Server is the actual intended destination

**This is why phishing works with DV certificates:**
```
Attacker registers: amaz0n-secure-login.com
Gets Let's Encrypt certificate for that domain
Browser shows green lock (certificate valid!)
User sees "secure" → trusts → enters credentials
```

---

### Example 2: Certificate Signing Request (CSR) Generation

**Scenario:** Generate CSR for www.example.com

**Step 1: Generate private key**
```bash
openssl genrsa -out example.com.key 2048

# Output: 2048-bit RSA private key
# CRITICAL: Keep this file secure! If compromised, attacker can impersonate your site.
```

**Step 2: Create CSR**
```bash
openssl req -new -key example.com.key -out example.com.csr

# Prompts:
Country Name (2 letter code) []: US
State or Province Name []: California
Locality Name []: San Francisco
Organization Name []: Example Corp
Organizational Unit Name []: IT Department
Common Name []: www.example.com
Email Address []: admin@example.com
```

**Step 3: Inspect CSR**
```bash
openssl req -text -noout -in example.com.csr

# Output:
Certificate Request:
    Data:
        Version: 1 (0x0)
        Subject: C=US, ST=California, L=San Francisco, O=Example Corp, OU=IT, CN=www.example.com
        Subject Public Key Info:
            Public Key Algorithm: rsaEncryption
                RSA Public-Key: (2048 bit)
                Modulus: 00:b4:3f:ae:...
                Exponent: 65537 (0x10001)
    Signature Algorithm: sha256WithRSAEncryption
         8f:3a:2e:... (CSR signed by private key)
```

**Step 4: Submit CSR to CA**
```
Upload example.com.csr to CA website
CA validates:
  - Domain ownership (via DV challenge)
  - Organization (if OV/EV)
CA signs certificate
CA returns: example.com.crt
```

**Step 5: Install certificate on server**
```nginx
# Nginx configuration
ssl_certificate /etc/ssl/certs/example.com.crt;
ssl_certificate_key /etc/ssl/private/example.com.key;
```

---

### Example 3: Certificate Revocation Check (OCSP)

**Scenario:** Check if certificate is revoked

**Method 1: OCSP (Online Certificate Status Protocol) — Modern**

```bash
# Extract OCSP responder URL from certificate
openssl x509 -in example.com.crt -noout -ocsp_uri

# Output:
http://ocsp.digicert.com

# Query OCSP responder
openssl ocsp \
  -issuer intermediate-ca.crt \
  -cert example.com.crt \
  -url http://ocsp.digicert.com \
  -CAfile root-ca.crt

# Response:
example.com.crt: good
    This Update: Apr 27 12:00:00 2026 GMT
    Next Update: May 4 12:00:00 2026 GMT
```

**OCSP Stapling (performance optimization):**
```
Problem: Client must query OCSP responder on every TLS handshake (slow, leaks privacy)
Solution: Server queries OCSP responder, caches response, sends with certificate

TLS handshake with OCSP stapling:
  Server → Client: Certificate + OCSP response (digitally signed by CA)
  Client verifies OCSP response signature (proves freshness)
  
Benefits:
  - Faster (no client OCSP query)
  - Better privacy (CA doesn't see which sites you visit)
  - Works even if OCSP responder is down
```

**Method 2: CRL (Certificate Revocation List) — Legacy**

```bash
# Extract CRL distribution point from certificate
openssl x509 -in example.com.crt -noout -ext crlDistributionPoints

# Output:
URI:http://crl.digicert.com/root.crl

# Download CRL
wget http://crl.digicert.com/root.crl

# Parse CRL
openssl crl -inform DER -text -noout -in root.crl

# Output:
Certificate Revocation List (CRL):
        Version 2 (0x1)
    Signature Algorithm: sha256WithRSAEncryption
        Issuer: /C=US/O=DigiCert Inc/CN=DigiCert Global Root CA
        Last Update: Apr 27 00:00:00 2026 GMT
        Next Update: May 4 00:00:00 2026 GMT
Revoked Certificates:
    Serial Number: 3A5C9F1E...
        Revocation Date: Apr 20 14:23:45 2026 GMT
        CRL entry extensions:
            X509v3 CRL Reason Code:
                Key Compromise
    Serial Number: 8F2B3C4D...
        Revocation Date: Apr 25 09:15:32 2026 GMT
```

**CRL problems:**
- Large files (can be megabytes for large CAs)
- Infrequent updates (24-48 hours)
- Privacy leak (CA sees which CRLs you download)

**OCSP vs CRL:**

| Aspect | OCSP | CRL |
|--------|------|-----|
| Response size | Small (~1KB) | Large (1MB+) |
| Freshness | Real-time | 24-48 hours |
| Privacy | CA sees queries | Better (download whole list) |
| Performance | Slower (network query) | Faster (cached locally) |
| Status | Modern standard | Legacy |

---

### Example 4: Certificate Pinning (Mobile App)

**Problem:** Rogue CAs can issue fake certificates for your domain

**Solution:** Pin expected certificate or public key in app code

**Certificate pinning (strict):**
```kotlin
// Android app
val certificatePinner = CertificatePinner.Builder()
    .add(
        "api.example.com",
        "sha256/AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA=" // Certificate hash
    )
    .build()

val client = OkHttpClient.Builder()
    .certificatePinner(certificatePinner)
    .build()

// If server presents certificate with different hash:
// javax.net.ssl.SSLPeerUnverifiedException: Certificate pinning failure!
```

**Public key pinning (flexible):**
```kotlin
// Pin public key instead of certificate
// Allows certificate rotation without app update (if key stays same)
val certificatePinner = CertificatePinner.Builder()
    .add(
        "api.example.com",
        "sha256/AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA=", // Current key
        "sha256/BBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBB="  // Backup key
    )
    .build()
```

**Pinning trade-offs:**

**Pros:**
- ✅ Prevents MitM attacks with rogue certificates
- ✅ Protects against compromised CAs
- ✅ Defense-in-depth

**Cons:**
- ⚠️ App update required for certificate rotation (if pin expires)
- ⚠️ Risk of "bricking" app if pin incorrect (users locked out)
- ⚠️ Doesn't help if attacker controls device (rooted phone, corporate proxy)

**Best practice:**
- Pin backup keys (have 2+ pins)
- Use public key pinning (allows cert rotation)
- Have emergency unpin mechanism (server-controlled kill switch)
- Monitor Certificate Transparency logs

---

## Layer 4 — Edge Cases, Nuances, and Limitations

### Edge Case 1: Certificate Transparency (CT) Logs

**Problem:** Rogue CAs can issue fake certificates without detection

**Example attack:**
```
Scenario: Rogue CA issues certificate for "google.com"
Without CT: Google never knows (until breach discovered)
With CT: Certificate logged publicly → Google monitors logs → detects rogue certificate immediately
```

**Certificate Transparency (RFC 6962):**
```
Requirement (since 2018): All publicly-trusted certificates must be logged

Workflow:
  1. CA issues certificate
  2. CA submits certificate to multiple CT logs (public append-only logs)
  3. CT log returns Signed Certificate Timestamp (SCT)
  4. CA includes SCT in certificate or TLS handshake
  5. Browser validates SCT (proves certificate is logged)
  6. Domain owners monitor CT logs for their domains

If certificate not logged → browsers reject it
```

**CT log monitors:**
- https://crt.sh — Search CT logs
- Facebook CT monitor — Alert on new certificates for your domains
- Google CT monitor — Part of Google Search Console

**Detection example:**
```
Attacker obtains fraudulent certificate for "yourcompany.com"
Certificate appears in CT logs within minutes
Your monitoring system detects it:
  Alert: New certificate for "yourcompany.com" from unknown CA
  Action: Investigate, revoke if unauthorized, report to CA
```

---

### Edge Case 2: CAA Records (DNS-Based Authorization)

**Problem:** Any CA can issue certificates for any domain (by default)

**Solution:** CAA (Certificate Authority Authorization) DNS records

**CAA record format:**
```dns
; Only DigiCert and Let's Encrypt can issue certificates
example.com. IN CAA 0 issue "digicert.com"
example.com. IN CAA 0 issue "letsencrypt.org"

; All other CAs must NOT issue certificates (policy violation)
```

**How it works:**
```
1. Attacker requests certificate for example.com from RogueCA
2. RogueCA checks DNS: example.com CAA records
3. RogueCA sees: Only DigiCert and Let's Encrypt authorized
4. RogueCA must refuse issuance (per CA/B Forum rules)
```

**CAA record types:**
```
issue "ca.example.com"       — Standard issuance
issuewild "ca.example.com"   — Wildcard certificates only
iodef "mailto:security@example.com"  — Report violations
```

**Attack mitigation:**
```
Without CAA: Compromised CA can issue cert for any domain
With CAA: Compromised CA cannot issue cert (policy violation)

Limitation: Relies on CA compliance (CAs could ignore CAA)
Enforcement: CA/B Forum audits, browser distrust for violations
```

---

### Edge Case 3: Wildcard Certificates

**Wildcard certificate:** Covers domain and all direct subdomains

**Format:**
```
Common Name: *.example.com

Valid for:
  ✓ www.example.com
  ✓ api.example.com
  ✓ mail.example.com

NOT valid for:
  ✗ example.com (apex domain)
  ✗ admin.internal.example.com (two levels deep)
```

**Security consideration:**
```
Risk: Wildcard private key compromise affects all subdomains

Better approach:
  - Use SAN certificates (multiple specific domains)
  - Or separate certificates per subdomain
  - Limit wildcard cert exposure (use only where necessary)

Example SAN cert:
  SAN: DNS:example.com, DNS:www.example.com, DNS:api.example.com
  More control, same convenience
```

---

### Edge Case 4: Name Constraints (PKI Hierarchy)

**Problem:** Intermediate CA should only issue certificates for certain domains

**Solution:** Name constraints extension in intermediate certificate

**Example:**
```
Root CA
  ↓ (signs intermediate with name constraints)
Intermediate CA for "*.company.com"
  Name Constraints: Permitted subtrees: DNS:.company.com
  
Intermediate CA can issue certs for:
  ✓ www.company.com
  ✓ mail.company.com
  
Cannot issue certs for:
  ✗ evil.com
  ✗ google.com
```

**Use case:** Enterprise PKI, government PKI

**If intermediate violates constraint:**
```
Intermediate issues certificate for "evil.com"
Browser validates certificate chain
Browser sees name constraints in intermediate certificate
evil.com not in permitted subtrees → REJECT certificate
```

---

### Limitation 1: Certificate Lifetime and Revocation Lag

**Problem:** Certificate revocation is not instant

**Revocation timeline:**
```
T+0h: Private key compromised
T+1h: Certificate owner notices breach
T+2h: Certificate revocation requested from CA
T+3h: CA processes revocation, updates CRL/OCSP
T+24h: CRL cached by browsers expires, new CRL downloaded
T+???: User's browser finally learns certificate is revoked

During this window: Attacker can still use compromised certificate
```

**Short certificate lifetimes help:**
```
Historical:
  - 2015: Certificates valid for 5 years
  - 2018: Maximum 825 days (2.3 years)
  - 2020: Maximum 398 days (13 months)
  - 2023: Industry push for 90 days (Let's Encrypt default)

Rationale:
  - Shorter lifetime = less time for undetected compromise
  - Forces automation (good security hygiene)
  - Reduced revocation checking reliance
```

---

### Limitation 2: Trust Store Bloat

**Problem:** OS/browser trust stores contain 100-200+ root CAs

**Risk:** Any one CA compromise can issue fake certificates for any domain

**Historical compromises:**
- **DigiNotar (2011):** Compromised, issued fake google.com certificates, used by Iranian government for surveillance → CA completely untrusted, removed from all browsers
- **Symantec (2017):** Policy violations, improper issuance → gradual distrust, eventually removed → rebranded as DigiCert
- **TrustCor (2022):** Alleged ties to surveillance company → removed from Mozilla trust store

**Trust store management:**
```
Browsers monitor CAs:
  - Certificate Transparency logs
  - Incident reports
  - Compliance audits (WebTrust, ETSI)
  
Gradual distrust process:
  1. Incident discovered
  2. Investigation period (30-90 days)
  3. Warning period (issue deprecation notices)
  4. Gradual distrust (mark certificates untrusted, but allow override)
  5. Full removal (hard fail)
```

**Recommendation:** Limit trust to essential CAs (if possible), use CAA records, monitor CT logs

---

### Limitation 3: Human Factor in EV Validation

**Problem:** EV validation requires human judgment

**Social engineering attacks:**
```
Attacker registers company "Paypal Services Inc." (legitimate business)
Attacker requests EV certificate for "paypaI.com" (capital i looks like lowercase L)
CA validates: "Paypal Services Inc." exists (✓), domain ownership (✓)
CA issues EV certificate
Phishing site now has "legitimate" EV certificate

User sees: Green bar (removed 2019) or organization name in certificate
User trusts (looks official)
```

**This is why EV indicators were removed:**
```
Browser UI change (2019-2020):
  - Chrome, Firefox, Safari removed green bar
  - Reason: Research showed EV didn't prevent phishing
  - Attackers could obtain EV certificates for lookalike domains
  - Users didn't check certificate details anyway

Current status:
  - EV certificates still issued (higher validation)
  - No special browser UI (same as DV/OV)
  - Value: Legal identity binding, audit trail, internal policy
```

---

## Active Recall Prompts

### Understanding Questions

1. **Certificate components:** What information does an X.509 certificate contain? Which fields are signed by the CA?

2. **PKI roles:** Explain the roles of CA, RA, CRL, and CR in a PKI system. How do they work together?

3. **Trust models:** Compare hierarchical trust (PKI) vs web of trust (PGP). What are the trade-offs?

---

### Application Questions

4. **Certificate validation:** Walk through the steps a browser performs when validating an HTTPS certificate. What checks are mandatory?

5. **Revocation methods:** Compare CRL vs OCSP. Which is better for real-time validation? What is OCSP stapling and why is it useful?

6. **Certificate classes:** When would you use Class 3 (DV) vs Class 5 (EV)? What additional validation does EV provide?

---

### Transfer Questions

7. **DigiNotar breach (2011):** Research the DigiNotar CA compromise. How were fake certificates used? What was the industry response?

8. **Certificate Transparency:** Set up a CT log monitor for a domain you control. Simulate certificate issuance and observe the CT log entry. How quickly does it appear?

9. **CAA records:** Add CAA records to a domain's DNS. Test that unauthorized CAs refuse issuance. What happens if you request a certificate from a non-authorized CA?

10. **Certificate pinning implementation:** Implement certificate pinning in a mobile app or API client. Test with correct and incorrect certificates. What happens when the pin fails?

---

## References

### Primary Sources
- **Course:** IFT2830 - Sécurité des systèmes informatiques (UdeM)  
  Final exam materials: [02_theory-final.md](../../../05_references/course-materials/IFT2830_course-materials/02_theory-final.md)

### Standards & Specifications
- **RFC 5280** — X.509 Public Key Infrastructure Certificate and CRL Profile
- **RFC 6960** — OCSP (Online Certificate Status Protocol)
- **RFC 6962** — Certificate Transparency
- **RFC 8659** — CAA (Certificate Authority Authorization)
- **CA/Browser Forum Baseline Requirements** — Industry standards for publicly-trusted certificates

### Academic & Industry
- Adams, C., & Lloyd, S. (2003). *Understanding PKI: Concepts, Standards, and Deployment Considerations* (2nd ed.). Addison-Wesley.
- Durumeric, Z., et al. (2013). "Analysis of the HTTPS Certificate Ecosystem." *IMC*.
- Sleevi, R., & Szeto, E. (2013). "Sustaining Digital Certificate Security." *Google Security Blog*.

### Tools & Resources
- **OpenSSL** — Certificate generation and validation
- **crt.sh** — Certificate Transparency log search
- **SSL Labs** — HTTPS configuration testing (ssllabs.com/ssltest)
- **Let's Encrypt** — Free automated certificate issuance

### Real-World Incidents
- **DigiNotar (2011)** — Compromised CA, fake certificates for google.com, Iran surveillance
- **Symantec distrust (2017)** — Policy violations, gradual distrust by browsers
- **Superfish (2015)** — Lenovo laptops shipped with rogue CA, intercepted HTTPS
- **TrustCor removal (2022)** — Alleged surveillance ties, Mozilla distrust

---

## Related Content

### Theory Modules
- **Previous:** [Asymmetric Encryption](asymmetric-encryption.md) — Public-key cryptography foundation
- **Related:** [Cryptography Basics](cryptography-basics.md) — Core concepts
- **Related:** [Symmetric Encryption](symmetric-encryption.md) — Bulk data encryption

### Examples
- [Generate CSR & Install Certificate](../../../02_examples/01-cryptography/certificate-management/) — Practical PKI
- [Certificate Chain Validation](../../../02_examples/01-cryptography/cert-chain-validation/) — Step-by-step browser checks
- [Certificate Pinning](../../../02_examples/01-cryptography/cert-pinning/) — Mobile app security

### Exercises
- [Create Self-Signed Certificate](../../../03_exercises/01-cryptography/self-signed-cert/) 🟢 — OpenSSL basics
- [Set Up Internal CA](../../../03_exercises/01-cryptography/internal-ca/) 🟡 — PKI hierarchy
- [Monitor CT Logs](../../../03_exercises/01-cryptography/ct-monitoring/) 🟡 — Certificate Transparency

### Tools & Resources
- **Certificate Tools:** `04_resources/tools/cryptography/certificate-tools.md`
- **OpenSSL Cheatsheet:** `04_resources/tools/cryptography/openssl-cheatsheet.md`
- **PKI Diagram:** `04_resources/tools/cryptography/pki-diagram.pdf`

---

## Personal Insights & Notes

### Study Notes
_Record your observations, "aha" moments, and connections here._

**Example:**
- "Certificates are like government-issued IDs for the internet. CA = government, certificate = passport."
- "OCSP stapling is brilliant—server caches revocation status so client doesn't have to query."

---

### Real-World Connections
_Link this concept to incidents, news, or work experience._

**Example:**
- "DigiNotar collapse (2011) shows single CA compromise affects entire PKI trust model. That's why Certificate Transparency is critical."

---

### Questions & Confusion
_Track what's unclear or needs deeper investigation._

**Example:**
- "How exactly does Certificate Transparency prevent rogue certificates? Need to understand Merkle tree structure."
- "What happens if all CAs in CAA record are compromised? Is there a fallback?"

---

### Exam/Interview Prep
_Key points to remember for assessments._

**Exam focus (IFT2830):**
- Certificat numérique: lie une clé publique à une identité, signé par tiers de confiance (AC)
- Classes: 1 (email), 2 (individu), 3/DV (domaine), 4/OV (organisation), 5/EV (validation étendue)
- X.509: format standard (ITU-T), champs critiques (subject, issuer, validity, public key, signature)
- PKI composants: AC (autorité certification), AE (autorité enregistrement), LCR (liste révocation), répertoire certificats
- PKCS: standards RSA (#1 RSA, #7 CMS, #10 CSR, #12 .p12/.pfx)
- Modèles confiance: directe, tiers, hiérarchique, distribuée (web of trust), passerelle (bridge)

**Interview talking points:**
- "Certificate chain validation: verify signature at each level, check validity period, check revocation, confirm hostname match."
- "OCSP is better than CRL for real-time revocation checking. OCSP stapling improves performance and privacy."
- "Certificate Transparency logs provide public audit trail. Domain owners can monitor for unauthorized certificates."
- "CAA DNS records restrict which CAs can issue certificates for a domain. Defense against rogue CA issuance."

---

## Change Log

| Date | Change | Reason |
|------|--------|--------|
| 2026-04-27 | Created module | PKI and digital certificates for final exam |
| 2026-04-27 | Added certificate classes | DV, OV, EV validation levels |
| 2026-04-27 | Added X.509 structure | Standard certificate format |
| 2026-04-27 | Added PKI components | CA, RA, CRL, CR roles |
| 2026-04-27 | Added PKCS standards | #1-#15 cryptographic standards |
| 2026-04-27 | Added trust models | Direct, third-party, hierarchical, distributed, bridge |
| 2026-04-27 | Added CT and CAA | Modern security enhancements |
| 2026-04-27 | Integrated French terminology | Bilingual support from IFT2830 materials |
