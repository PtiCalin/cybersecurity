# Changelog

All notable changes to this project will be documented in this file.

The format is based on Keep a Changelog and this project follows semantic-style versioning when applicable.

## [Unreleased]

### Added

- **Core Knowledge Structure (Theory, Examples, Exercises)**
  - Comprehensive `01_theory/THEORY.md` organizational guide with four-layer explanation model (Intuition → Formal → Worked Example → Edge Cases)
  - Theory note template (`01_theory/_theory-note-template.md`) with multi-layer progressive disclosure, active recall prompts, and spaced repetition
  - Domain organization structure for theory: 00-foundations, 01-cryptography, 02-network-security, 03-offensive-security, 04-defensive-security, 05-application-security, 06-malware-analysis, 07-specialized, 08-frameworks
  - Four learning paths: Beginner→Professional (12-18mo), Developer→Secure Dev (6-9mo), Generalist→Pentester (9-12mo), Analyst→IR (6-8mo)
  - Active learning workflow with pre-study, first pass, deep processing, application, and spaced review phases
  - Comprehensive `02_examples/EXAMPLES.md` organizational guide for practical demonstrations
  - Example template (`02_examples/_example-template.md`) with step-by-step walkthroughs, dual perspectives (offensive+defensive), and reproducibility checklists
  - Example types: Attack Demonstrations, Defense Implementations, Dual-Perspective Scenarios, Case Studies, Tool Demonstrations
  - Domain organization for examples mirroring theory structure with additional case-studies directory
  - Safety guidelines and lab environment requirements for all examples
  - Comprehensive `03_exercises/EXERCISES.md` organizational guide for hands-on practice
  - Exercise template (`03_exercises/_exercise-template.md`) with progressive hints, multiple solution approaches, and validation criteria
  - Four difficulty levels: 🟢 Beginner (guided, 30min-1h), 🟡 Intermediate (moderate guidance, 1-2h), 🟠 Advanced (minimal guidance, 2-4h), 🔴 Expert (real-world complexity, 4h+)
  - Exercise types: Guided Labs, Challenge Problems, Scenario-Based, Code Review, CTF Challenges
  - Progress tracking system with skill assessment and review scheduling
  - Integration framework connecting theory → examples → exercises with bidirectional links
  - CTF and competition preparation guidance with training progression phases
- **Reference System Enhancements**
  - Comprehensive attribution model distinguishing workspace development from source materials
  - Reference note template system for structured knowledge extraction (`05_references/_reference-note-template.md`)
  - Active reading workflow with spaced repetition scheduling in reference notes
  - Comprehensive `05_references/REFERENCES.md` with organization, naming conventions, and usage guidelines
  - Directory structure for standards, CVEs, papers, frameworks, documentation, and textbooks
  - Category-specific README files for each reference subdirectory
  - Example reference note: OWASP Top 10 2021 demonstrating full template usage
  - Quick reference guide (`05_references/QUICK-GUIDE.md`) for efficient note-taking
  - Tag taxonomy and search patterns for reference discovery
  - Textbook catalog (`05_references/textbooks/TEXTBOOKS.md`) with ~30 curated books, learning paths, difficulty ratings, and reading strategies

- **Theory Module Population (IFT2830 Integration)**
  - Created domain directory structure in `01_theory/` with README files for all 8 domains (00-foundations through 08-frameworks)
  - Populated `00-foundations/` with three comprehensive theory modules:
    - `cia-triad.md`: Confidentialité, Intégrité, Disponibilité — foundational security properties with French terminology integration
    - `risk-analysis.md`: Complete risk assessment framework covering actifs, menaces, vulnérabilités, probabilité, impact, risk treatment strategies, and methodologies (EBIOS, MEHARI, OCTAVE, Risk IT, ISO 27005)
    - `security-governance.md`: Governance framework with three axes (Stratégique, Tactique, Opérationnel), CISO role, governance principles, strategic vs tactical vs operational security, governance failures in breaches
  - Populated `02-network-security/` with comprehensive network attack module:
    - `dos-ddos-attacks.md`: Denial of service techniques including SYN floods, amplification attacks, reflection, ping of death, with defensive countermeasures
  - Populated `03-offensive-security/` with two attack technique modules:
    - `attack-lifecycle.md`: Eight-phase attack chain from reconnaissance to cleanup with worked web server compromise example, persistence mechanisms, and APT considerations
    - `password-attacks.md`: Password attack vectors including brute force, dictionary, hybrid, credential stuffing, rainbow tables, phishing; hash algorithms (MD5/SHA vs bcrypt/Argon2), salting, timing analysis, real breaches (RockYou, LinkedIn, Dropbox)
  - Populated `01-cryptography/` with foundational cryptography module:
    - `cryptography-basics.md`: Symmetric vs asymmetric encryption, hashing, MACs, digital signatures, hybrid cryptography (TLS/HTTPS handshake), key management, ECB vulnerability, timing attacks, post-quantum considerations
  - Populated `05-application-security/` with web security module:
    - `sql-injection.md`: SQL injection attack types (classic, blind, out-of-band), exploitation techniques (authentication bypass, union-based extraction, blind extraction), parameterized queries defense, second-order SQLi, ORM vulnerabilities, WAF bypass, real breaches (Heartland, Sony, Yahoo)
  - All modules follow four-layer pedagogical model (Intuition → Formal → Worked Examples → Edge Cases)
  - Integrated French terminology from IFT2830 course materials throughout (bilingual support)
  - Added real-world incident examples (WannaCry, Equifax, Stuxnet, Mirai, SolarWinds, Heartland, Sony, Yahoo, LinkedIn, Dropbox, Heartbleed)
  - Included 10 active recall prompts per module (understanding, application, transfer questions)
  - Linked modules to IFT2830 course materials in `05_references/course-materials/`
  - Each module includes spaced repetition schedule, personal notes section, and change log
  - Total 8 comprehensive theory modules created across 5 domains (foundations, cryptography, network security, offensive security, application security)

- **Final Exam Preparation Materials (IFT2830 Phase 9)**
  - Created three advanced cryptography theory modules in `01_theory/01-cryptography/`:
    - `symmetric-encryption.md`: Comprehensive symmetric encryption covering stream ciphers (RC4, ChaCha20), block ciphers (DES, 3DES, AES, Blowfish, IDEA), cipher modes (ECB, CBC, CTR, GCM), classical ciphers (Caesar, substitution, transposition), padding (PKCS#7), key derivation (PBKDF2), worked examples with XOR operations, security considerations (key reuse, padding oracle attacks), real-world incidents (WEP vulnerability, BEAST, POODLE, Sweet32), French terminology integration (chiffrement de flux, chiffrement par bloc)
    - `asymmetric-encryption.md`: Complete asymmetric encryption coverage including RSA algorithm (key generation with worked example p=7, q=19, n=133, φ(n)=108, e=5, d=65; encryption/decryption formulas; complete encryption example M=42→C=87), digital signatures (5-step process: résumé/hash→sign with private key→send M+S→recipient hash→verify with public key), ECC (Elliptic Curve Cryptography with key size equivalence table: ECC-256 ≈ RSA-3072 ≈ AES-128 security), NTRUEncrypt (quantum-resistant lattice-based crypto), CRYSTALS-Kyber (NIST post-quantum standard), padding schemes (OAEP security requirement vs vulnerable PKCS#1 v1.5), hybrid encryption (RSA+AES workflow as used in TLS), small public exponent attack, timing attacks, key size recommendations (2048-bit minimum, 3072-bit medium-term, 4096-bit long-term), quantum computing threat (Shor's algorithm), key management lifecycle, Debian OpenSSL vulnerability (CVE-2008-0166), French terminology (clé publique, clé privée, paire de clés, signature numérique, résumé)
    - `digital-certificates-pki.md`: Comprehensive PKI and certificate infrastructure covering certificate structure (X.509 format with version, serial number, signature algorithm, issuer, validity period, subject, public key, extensions, CA signature), certificate classes (Class 1: email, Class 2: individual, Class 3/DV: domain validation, Class 4/OV: organization validation, Class 5/EV: extended validation), special types (SSL EV, dual-key, dual-sided/mutual TLS), X.509 extensions (Subject Alternative Name, Key Usage, Extended Key Usage, Basic Constraints), PKI components (CA: Autorité de Certification, RA: Autorité d'Enregistrement, CRL: Liste de Révocation de Certificats, CR: Répertoire de Certificats, End Entity, Relying Party), PKCS standards (#1: RSA format, #3: Diffie-Hellman, #5: PBKDF2, #7: CMS/S/MIME, #8: private key format, #10: CSR format, #11: HSM API, #12: .p12/.pfx bundle, complete table of #1-#15), trust models (Confiance Directe, Tiers de Confiance, Hiérarchique, Distribuée/Web of Trust, Passerelle/Bridge), certificate chain validation (complete step-by-step browser workflow), CSR generation worked example (openssl commands), certificate revocation (CRL vs OCSP comparison, OCSP stapling optimization), Certificate Transparency logs (public audit trail, detection of rogue certificates), CAA DNS records (restrict authorized CAs), certificate pinning (mobile app security), wildcard certificates, name constraints, certificate lifetime evolution (5 years→825 days→398 days→90 days trend), historical compromises (DigiNotar 2011, Symantec 2017 distrust, TrustCor 2022 removal), French terminology (certificat numérique, tiers de confiance, autorité de certification/enregistrement, liste de révocation, confiance directe/hiérarchique/distribuée/passerelle, modèles de confiance)
  - Created comprehensive finals cheatsheet: `05_references/course-materials/IFT2830_finals-cheatsheet.md` (16,000+ words)
    - Consolidated all 11 theory modules (8 existing + 3 new) into exam-ready quick reference
    - Organized into 10 major sections: CIA Triad, Risk Analysis & Governance, Cryptography Fundamentals, Symmetric Encryption, Asymmetric Encryption, Digital Certificates & PKI, Network Security, Attack Lifecycle & Techniques, Application Security, Quick Reference Tables
    - CIA Triad table with definitions, objectives, attack examples, defense examples
    - Risk formula (R = P × I) with worked example
    - Risk treatment strategies: évitement, réduction, transfert, acceptation
    - Core definitions table: actif, menace, vulnérabilité, impact, contrôle
    - Governance framework: three axes (Stratégique, Tactique, Opérationnel) with responsibilities and deliverables
    - Eight governance principles: Vocabulaire, Volonté directoriale, Proportionnalité, Cohérence, Simplicité, Dynamicité, Continuité, Évaluation
    - Cryptographic primitives comparison table: Hash, Symmetric, Asymmetric, MAC (input, output, reversibility, key requirements, use cases)
    - Stream vs block cipher comparison: processing unit, speed, use case, padding, examples
    - Symmetric algorithms table: DES (obsolete), 3DES (deprecated), AES-128/256 (current), RC4 (broken), ChaCha20 (modern), Blowfish (obsolete), IDEA (rare) with key sizes, block sizes, status
    - Block cipher modes table: ECB (NEVER use), CBC (good with MAC), CTR (good), GCM (excellent AEAD) with parallelization, padding, security, use cases
    - RSA algorithm: complete key generation steps (p, q, n, φ(n), e, d), encryption/decryption formulas, worked example (p=7, q=19, n=133, e=5, d=65, M=42→C=87→M=42)
    - Digital signatures: 5-step process diagram (résumé→chiffrement résumé→envoi→résumé message reçu→vérification) with authenticity/integrity/non-repudiation guarantees
    - Asymmetric algorithms comparison: RSA (factorization, 2048-4096 bits, quantum-vulnerable), ECC (ECDLP, 256-521 bits, faster, quantum-vulnerable), NTRUEncrypt (lattice SVP, quantum-resistant), CRYSTALS-Kyber (NIST standard 2024, quantum-resistant)
    - Key size equivalence table: security levels (80-bit, 112-bit, 128-bit, 192-bit, 256-bit) mapped to RSA, ECC, and symmetric equivalents
    - Hybrid encryption workflow: AES for bulk data + RSA for key exchange (TLS pattern)
    - Certificate structure (X.509 fields): version, serial number, signature algorithm, issuer, validity period, subject, public key, extensions, CA signature
    - Certificate classes table: Class 1-5 with validation level, time, use case, organization visibility
    - PKI components table: CA, RA, CRL, CR, End Entity, Relying Party with roles and responsibilities
    - PKCS standards quick reference: #1 (RSA), #3 (DH), #5 (PBKDF2), #7 (CMS), #8 (private key), #10 (CSR), #11 (HSM), #12 (.p12/.pfx) with file formats and use cases
    - Trust models table: Confiance Directe, Tiers de Confiance, Hiérarchique, Distribuée, Passerelle with advantages, disadvantages, use cases
    - CRL vs OCSP comparison: response size, freshness, privacy, performance
    - DoS vs DDoS comparison: sources, volume, difficulty, detection, mitigation
    - Amplification attacks table: DNS (50x), NTP (556x), Memcached (51,000x), SSDP (30x) with query size, response size, defenses
    - DDoS mitigation strategies: over-provisioning, rate limiting, geo-blocking, anycast, scrubbing centers, WAF
    - Attack lifecycle: 8-phase table (reconnaissance→scanning→vulnerability analysis→intrusion→privilege escalation→compromise→persistence→cleanup) with objectives, techniques, typical duration
    - Password attacks table: brute force, dictionary, hybrid, credential stuffing, rainbow tables, phishing with mechanisms, speed, defenses
    - Hash algorithm security: MD5 (broken), SHA-1 (broken), SHA-256 (secure), bcrypt (excellent for passwords), Argon2 (excellent for passwords) with status, speed, salt, use case
    - SQL injection: vulnerable code example, attack example (admin' OR '1'='1), secure code (parameterized queries), SQLi types (classic, blind boolean, blind time-based, out-of-band)
    - Hashing algorithms comprehensive table: MD5, SHA-1, SHA-256, SHA-384, SHA-512, RIPEMD-160, Whirlpool, bcrypt, Argon2 with output size, status, speed, use case
    - Common port numbers table: FTP (20/21), SSH (22), Telnet (23), SMTP (25), DNS (53), HTTP (80), POP3 (110), IMAP (143), HTTPS (443), MySQL (3306), RDP (3389), PostgreSQL (5432)
    - Secure vs insecure protocols: HTTP→HTTPS, FTP→SFTP/FTPS, Telnet→SSH, SMTP→SMTPS, POP3→POP3S, IMAP→IMAPS
    - CVSS risk scoring: None (0.0), Low (0.1-3.9), Medium (4.0-6.9), High (7.0-8.9), Critical (9.0-10.0) with action recommendations
    - Exam strategy: time management (3h=180min breakdown), common traps (confidentiality vs integrity confusion, bits vs bytes, terminology), key formulas summary
    - Memory aids (mnemonics): CIA Triad ("Cats Ignore Alarms"), password hash ranking ("My Silly Algorithm Became Awesome"), certificate classes ("Every Individual Deserves Organizational Excellence"), PKI components ("Cats Rarely Catch Red Elephants Reliably"), attack lifecycle ("Really Smart Vultures Invade Private Compounds Persistently Carefully")
    - Last-minute review checklist: must-know concepts with checkboxes (CIA definitions, risk formula, governance axes, symmetric vs asymmetric, AES vs DES, block cipher modes, RSA key generation, digital signature steps, certificate classes, PKI components, PKCS standards, trust models, DoS/DDoS, attack lifecycle, password attacks, SQL injection, hash algorithms)
    - French/English bilingual terminology table: 20+ key terms (chiffrement/encryption, clé/key, certificat numérique/digital certificate, autorité de certification/certificate authority, signature numérique/digital signature, résumé/hash, confiance/trust, intégrité/integrity, confidentialité/confidentiality, disponibilité/availability, menace/threat, vulnérabilité/vulnerability, risque/risk)
    - Exam focus areas with percentage breakdown: Cryptography (40%), Security Fundamentals (20%), Network Security (15%), Attacks (15%), Application Security (10%)
    - Best practices for exam: read carefully, draw diagrams, show calculations, use French terminology, eliminate wrong answers, budget time
  - Updated `01_theory/01-cryptography/CRYPTOGRAPHY.md` to mark three new modules as complete (✅)
  - All three cryptography modules follow established four-layer pedagogical model (L1: Intuition, L2: Formal, L3: Worked Examples, L4: Edge Cases)
  - Integrated French/English bilingual terminology throughout for IFT2830 course alignment
  - Each module includes 10 active recall prompts (understanding, application, transfer questions)
  - Real-world incident integration: WEP vulnerability (2001), Bleichenbacher attack (1998), Debian OpenSSL bug (2008), ROCA (2017), DigiNotar breach (2011), Symantec distrust (2017), TrustCor removal (2022), Superfish (2015)
  - Module sizes: symmetric-encryption.md (~6,500 lines), asymmetric-encryption.md (~7,500 lines), digital-certificates-pki.md (~8,500 lines), finals-cheatsheet.md (~1,100 lines)
  - Total theory modules now: 11 comprehensive modules across 5 domains

### Changed

- Reframed ATTRIBUTIONS.md to focus on workspace development contributions only
- Security tools, papers, CVEs, and standards now documented in `04_resources/` and `05_references/`
- Updated README to clarify separation of workspace attribution vs source documentation
- Enhanced attribution transparency with AI assistance disclosure section
- Transformed placeholder THEORY.md, EXAMPLES.md, EXERCISES.md into comprehensive organizational guides with pedagogical structure

### Deprecated

-

### Removed

-

### Fixed

-

### Security

-

## [0.2.0] - 2026-04-27

### Added

- Cybersecurity-focused knowledge hub structure
- Comprehensive README.md with learning objectives and domain coverage
- Updated CLAUDE.md with cybersecurity learning context
- Educational guidelines and ethical boundaries documentation
- Directory structure optimized for progressive learning (01_theory → 05_references)
- Quality standards for offensive/defensive content balance

### Changed

- Transformed repository from generic school project to cybersecurity knowledge base
- Updated AUTHORS.md with contribution guidelines for educational content
- Enhanced ATTRIBUTIONS.md structure for security research and tools
- Refined project scope to emphasize learning progression and retention

### Security

- Added ethical guidelines for offensive security content
- Established requirement for defensive countermeasures alongside attack techniques

## [0.1.0] - 2026-04-19

### Added

- Initial project scaffolding
- Repository governance files (README, templates, branch/security rules)
- Base directory structure

### Security

- Initial security reporting policy template

## [0.0.0] - 2026-04-19

### Added

- Repository initialization

---

## Usage Guidelines

- Use short, action-oriented bullet points.
- Group entries under the correct section (Added, Changed, Fixed, etc.).
- Reference related issues or pull requests when available.
- Keep entries focused on user-visible or team-relevant changes.
