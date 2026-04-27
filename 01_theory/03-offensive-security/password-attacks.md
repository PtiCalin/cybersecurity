# Password Attacks — Attaques par Mot de Passe

| Property          | Value                                                                                                         |
| ----------------- | ------------------------------------------------------------------------------------------------------------- |
| **Topic**         | Password Attacks / Attaques par Mot de Passe                                                                  |
| **Domain**        | 03-offensive-security                                                                                         |
| **Difficulty**    | 🟢 Beginner                                                                                                   |
| **Prerequisites** | [CIA Triad](../00-foundations/cia-triad.md), [Cryptography Basics](../01-cryptography/cryptography-basics.md) |
| **Learning Time** | 50-60 minutes                                                                                                 |
| **Status**        | ✅ Complete                                                                                                   |

---

## Review Schedule

- [ ] Day 2 — First review after initial study
- [ ] Week 1 — Consolidation review
- [ ] Month 1 — Long-term retention check
- [ ] Month 3 — Mastery verification

---

## Quick Summary

**What:** Password attacks are techniques used to obtain, crack, or bypass user authentication credentials.

**Offensive:** Password attacks are often the initial access vector. Weak passwords = easy entry.
**Defensive:** Strong password policies, MFA, and account lockout mechanisms defend against password attacks.

**Why it matters:** Passwords remain the most common authentication method. **81% of data breaches involve weak or stolen passwords** (Verizon DBIR 2023). Understanding password attacks is foundational for both offensive and defensive security.

---

## Prerequisites

**Required knowledge:**

- [CIA Triad](../00-foundations/cia-triad.md) — Confidentiality threats
- Basic cryptography (hashing: MD5, SHA, bcrypt)
- Authentication concepts (username/password, sessions)

**Quick check:** Do you know the difference between encryption and hashing? If yes, you're ready.

---

## Layer 1 — Intuition

Password attacks are like trying to open a locked door:

🔑 **Guessing (Brute Force)** = Try every possible key combination (1234, 1235, 1236...)
📋 **Dictionary Attack** = Try common keys first (password, 123456, admin)
🎭 **Social Engineering** = Trick the owner into giving you the key
🗂️ **Database Breach** = Steal the locksmith's key list
🔓 **Bypass** = Pick the lock or break the door frame

**Key insight:** Passwords are the **weakest link** in authentication. Humans choose predictable passwords, reuse them, and fall for phishing.

---

## Layer 2 — Formal Definitions

### Attack Types

#### 1. Brute Force Attack — Attaque par Force Brute

**Definition:** Systematically trying every possible password combination until the correct one is found.

**Mechanism:**

```
For each possible password in keyspace:
    Try login(username, password)
    If successful: STOP
    Else: Continue
```

**Keyspace:** All possible password combinations given character set and length.

**Example keyspace calculation:**

- Character set: lowercase (a-z) = 26 characters
- Length: 6 characters
- Keyspace: 26^6 = **308,915,776 possible passwords**

**Time to crack (assuming 1000 attempts/second):**

- 308,915,776 ÷ 1000 = **308,916 seconds** ≈ **3.6 days**

**French term:** _Attaque par force brute_

---

#### 2. Dictionary Attack — Attaque par Dictionnaire

**Definition:** Trying passwords from a pre-compiled list of common or likely passwords.

**Common dictionaries:**

- **Top passwords:** password, 123456, qwerty, letmein, admin
- **Common words:** dictionary words in target language (English, French, etc.)
- **Leaked passwords:** RockYou list (14M+ real passwords from breaches)
- **Targeted lists:** Company-specific terms, sports teams, local landmarks

**Efficiency:** Instead of trying all 308M combinations, try **10,000 common passwords first** → **99% of cracks happen here**.

**French term:** _Attaque par dictionnaire_

---

#### 3. Hybrid Attack — Attaque Hybride

**Definition:** Combines dictionary words with common patterns (numbers, symbols, capitalization).

**Pattern examples:**

- Dictionary word + year: `password2024`, `summer2025`
- Dictionary word + symbols: `password!`, `secret@123`
- Capitalization: `Password`, `SECRET`
- Leet speak: `p@ssw0rd`, `h@ck3r`

**Why it works:** Users think adding `1` or `!` to a dictionary word makes it "strong." It doesn't.

**French term:** _Attaque hybride_

---

#### 4. Credential Stuffing — Bourrage de Références

**Definition:** Using username/password pairs stolen from one breach to attempt login on other services.

**Why it works:** **Password reuse.** User uses same password on:

- Email (Gmail)
- Bank account
- Social media (LinkedIn)
- Work system

**Attacker workflow:**

1. Obtain breach database (e.g., LinkedIn 2021 breach: 700M users)
2. Extract username/password pairs
3. Try each pair on target site (bank, corporate VPN)

**Success rate:** 0.1-1% (but with millions of credentials, that's thousands of successes)

**French term:** _Bourrage de références_

---

#### 5. Rainbow Table Attack

**Definition:** Pre-computed hash lookup tables to crack password hashes instantly.

**How it works:**

1. **Pre-computation phase:** Hash millions of passwords, store in lookup table
   - `password` → `5f4dcc3b5aa765d61d8327deb882cf99` (MD5)
   - `123456` → `e10adc3949ba59abbe56e057f20f883e` (MD5)

2. **Attack phase:** Given a hash, look it up in the table → instant plaintext password

**Defense:** **Salting.** Add random value to each password before hashing.

- Without salt: `hash("password")` = same for all users
- With salt: `hash("password" + "a83jd92k")` = unique per user

**Limitation:** Rainbow tables are huge (100GB+ for comprehensive coverage) and don't work against salted hashes.

**French term:** _Table arc-en-ciel_

---

#### 6. Phishing — Hameçonnage

**Definition:** Tricking users into revealing their passwords through social engineering.

**Common tactics:**

- **Fake login page:** Email says "Your account is locked, click here to verify" → lands on fake bank/email login
- **Urgent request:** "CEO needs you to reset the system password immediately"
- **Spear phishing:** Targeted attack using personal details ("Hi Sarah, as discussed at the conference...")

**Why it works:** Exploits **human psychology** (urgency, authority, fear, curiosity).

**French term:** _Hameçonnage_

---

### Password Storage & Cracking

#### Password Hashing

**Concept:** Passwords should never be stored in plaintext. Instead, store the **hash**.

**Hash properties:**

- **One-way:** Easy to compute hash from password, impossible to reverse
- **Deterministic:** Same input always produces same hash
- **Fixed length:** Any password length → fixed hash length

**Example (MD5):**

```
password → 5f4dcc3b5aa765d61d8327deb882cf99
admin123 → e6e061838856bf47e1de730719fb2609
```

---

#### Hash Functions for Passwords

| Algorithm   | Security     | Speed                    | Usage                          |
| ----------- | ------------ | ------------------------ | ------------------------------ |
| **MD5**     | ❌ Broken    | Very fast (billions/sec) | NEVER for passwords            |
| **SHA-1**   | ❌ Weak      | Fast (millions/sec)      | NEVER for passwords            |
| **SHA-256** | ⚠️ Too fast  | Fast (millions/sec)      | Not recommended for passwords  |
| **bcrypt**  | ✅ Strong    | Slow (designed)          | ✅ Good for passwords          |
| **Argon2**  | ✅ Strongest | Configurable             | ✅ Best for passwords (modern) |
| **PBKDF2**  | ✅ Strong    | Configurable             | ✅ Good for passwords          |

**Key principle:** Password hashing should be **SLOW** to resist brute force. MD5 is fast (great for file integrity), terrible for passwords.

---

#### Salting

**Definition:** Adding a unique random value (salt) to each password before hashing.

**Without salt:**

```
User A: password → 5f4dcc3b5aa765d61d8327deb882cf99
User B: password → 5f4dcc3b5aa765d61d8327deb882cf99  (same hash!)
```

**With salt:**

```
User A: password + salt_A (a83jd92k) → hash_A (unique)
User B: password + salt_B (k92jd83a) → hash_B (different!)
```

**Benefit:** Attacker must crack each password individually. Rainbow tables useless.

**French term:** _Salage_

---

## Layer 3 — Worked Examples

### Example 1: Brute Force Attack Timing

**Target:** 8-character password, lowercase only

**Keyspace calculation:**

- Character set: a-z = 26 characters
- Length: 8 characters
- Total combinations: 26^8 = **208,827,064,576 passwords**

**Attack hardware:**

- **Consumer GPU (GTX 3090):** 100 billion MD5 hashes/second
- **Time to crack:** 208B ÷ 100B = **2.08 seconds** (if hashed with MD5)

**Same password with bcrypt (10 rounds):**

- **GPU performance:** 10,000 bcrypt hashes/second
- **Time to crack:** 208B ÷ 10,000 = **20,882,706 seconds** ≈ **242 days**

**Lesson:** **Hash algorithm choice matters more than password complexity** for security at scale.

---

### Example 2: Dictionary Attack Success

**Scenario:** Corporate VPN login, 10,000 employee accounts

**Attack setup:**

1. Obtain common password list (RockYou top 1,000)
2. Try each password against each username

**Attack math:**

- Usernames: 10,000
- Passwords to try: 1,000
- Total attempts: 10,000 × 1,000 = **10 million attempts**
- Rate limit: 10 attempts/second (slow to avoid detection)
- Time required: 10M ÷ 10 = **1 million seconds** ≈ **11.6 days**

**Expected success:**

- Weak password prevalence: ~5% of users use top-100 passwords
- Compromised accounts: 10,000 × 5% = **500 accounts**

**Defense failures in this scenario:**

- No account lockout after N failed attempts
- No rate limiting per IP
- No alerting on mass login failures

**Defensive fix:**

- Lockout after 5 failed attempts (reduces attempts to 50,000 total)
- Alert SOC on >100 failures from one IP
- Require MFA (even with correct password, attacker needs second factor)

---

### Example 3: Credential Stuffing Attack

**Real-world scenario:** LinkedIn breach (2021) → banking attack

**Attack chain:**

**Step 1: Obtain credential list**

```
Breach: LinkedIn (700 million accounts)
Format: email:password pairs
Example:
  john.doe@company.com:Summer2021!
  jane.smith@company.com:LinkedIn123
```

**Step 2: Target banking site**

```
For each credential pair:
    Try login on bank.com
    If successful:
        Log in, check balance, initiate transfer
```

**Step 3: Success metrics**

- Credentials tested: 700,000,000
- Success rate: 0.1% (password reuse)
- Compromised bank accounts: **700,000 accounts**

**Why it worked:**

- Users reused their LinkedIn password on bank site
- No detection of mass login attempts from same IP
- No MFA on bank accounts

**Defensive measures (realistic):**

- **Multi-factor authentication (MFA):** Even with stolen password, attacker needs phone/token
- **Compromised credential checking:** Block logins with passwords found in breach databases (e.g., Have I Been Pwned API)
- **Behavioral analysis:** Flag logins from unusual locations/devices
- **Rate limiting:** Slow down automated login attempts

---

### Example 4: Phishing Attack Flow

**Scenario:** Attacker targets company employees to gain VPN access

**Attack phases:**

**Phase 1: Reconnaissance**

```
Target: Acme Corp
Research:
  - Scrape LinkedIn for employee names/roles
  - Identify IT admin: John Smith (LinkedIn profile: "Senior SysAdmin at Acme")
  - Find company email format: firstname.lastname@acme.com
```

**Phase 2: Phishing email**

```
From: it-security@acme-corp.com (fake domain, looks like acme.com)
To: john.smith@acme.com
Subject: URGENT: VPN Certificate Expiring Today

Hi John,

Your VPN certificate expires in 2 hours. Click here to renew:
https://acme-vpn-renewal.com/login

This is an automated message from IT Security.
```

**Phase 3: Fake login page**

```
Page looks identical to real Acme VPN portal
User enters: john.smith / RealPassword123
Attacker captures: john.smith:RealPassword123
Page displays: "Certificate renewed. You may close this window."
```

**Phase 4: Exploitation**

```
Attacker uses captured credentials:
  → Logs into real VPN
  → Gains internal network access
  → Escalates privileges
  → Deploys ransomware
```

**Defensive measures:**

- **Security awareness training:** Teach employees to verify sender, hover over links, check URL
- **Email authentication:** SPF, DKIM, DMARC to block spoofed domains
- **MFA:** Even if phished, attacker needs second factor
- **Link protection:** Email gateway rewrites URLs, scans destinations
- **Passwordless authentication:** FIDO2/WebAuthn (no password to phish)

---

## Layer 4 — Edge Cases, Nuances, and Limitations

### Edge Case 1: Long Passwords vs. Complex Passwords

**Question:** Which is stronger?

- **Option A:** 8 characters, complex: `X7!kQ#2p`
- **Option B:** 20 characters, simple: `correct horse battery staple`

**Analysis:**

**Option A entropy:**

- Character set: 26 lowercase + 26 uppercase + 10 digits + 10 symbols = 72 chars
- Length: 8
- Entropy: log₂(72^8) ≈ **49.5 bits**

**Option B entropy:**

- Character set: 26 lowercase + space = 27 chars
- Length: 28 (with spaces)
- Entropy: log₂(27^28) ≈ **133 bits**

**But:** If Option B uses common words from dictionary:

- Dictionary size: 10,000 common words
- Words in passphrase: 4
- Entropy: log₂(10000^4) ≈ **53 bits** (still stronger than Option A)

**Lesson:** **Length beats complexity.** Passphrases are easier to remember and harder to crack.

**Modern recommendation (NIST 800-63B):**

- Minimum 8 characters (12+ preferred)
- No complexity requirements (they make passwords weaker by encouraging predictable patterns)
- Check against breach databases
- Use MFA

---

### Edge Case 2: Account Lockout Trade-offs

**Defense mechanism:** Lock account after N failed login attempts

**Problem:** Creates a denial-of-service vector

**Scenario:**

- Attacker knows usernames (public: john.smith@company.com)
- Attacker makes 5 failed login attempts per user
- Result: **Entire company locked out of their accounts**

**Solution trade-offs:**

| Approach                   | Pros                               | Cons                   |
| -------------------------- | ---------------------------------- | ---------------------- |
| **Hard lockout**           | Strong defense against brute force | DoS risk               |
| **Soft lockout (CAPTCHA)** | Slows attacks, no DoS              | Annoys users           |
| **Progressive delays**     | 1 sec, 2 sec, 5 sec, 30 sec...     | Slows legitimate users |
| **IP-based rate limiting** | Doesn't affect user's account      | VPN/NAT bypass         |
| **MFA**                    | No lockout needed                  | Requires second device |

**Best practice (Modern):** MFA + breach database checking + behavioral analysis. Avoid lockout entirely.

---

### Edge Case 3: Password Manager Master Password

**Question:** If a password manager uses one master password, isn't that a single point of failure?

**Analysis:**

**Threat model:**

- **Online attack:** Attacker tries to brute force master password via cloud sync service
  - **Defense:** Rate limiting, account lockout, MFA
  - **Risk:** Low (attacker gets ~10 attempts)

- **Offline attack:** Attacker steals encrypted password vault file, cracks locally
  - **Defense:** Strong encryption (AES-256), slow KDF (PBKDF2 100k+ rounds, Argon2)
  - **Time to crack:** Years to centuries for strong master password
  - **Risk:** Medium (depends on master password strength)

**Recommendation:**

- Master password: 20+ characters, passphrase (5-6 words)
- MFA for password manager login
- YubiKey for additional protection (hardware token required to decrypt vault)

**Why still better than no password manager:**

- Enables unique passwords per site (no reuse)
- Prevents phishing (autofills only on real domain)
- Generates random strong passwords

---

### Limitation 1: Hash Cracking Doesn't Need the Target System

**Misconception:** "We have rate limiting, so brute force is impossible."

**Reality:** If attacker obtains the **password database** (via SQL injection, backup exposure), they can crack **offline** at billions of attempts per second.

**Example: LinkedIn breach (2012)**

- Attacker stole 6.5M password hashes (unsalted SHA-1)
- Cracked offline at 100M+ hashes/second
- 90% cracked within days

**Defense:** Assume database breach will happen. Use strong hashing (bcrypt/Argon2) + salting so offline cracking takes years.

---

### Limitation 2: Biometric Authentication Doesn't Solve Password Problems

**Alternative:** Replace passwords with fingerprint/face recognition?

**Problems:**

- **Non-revocable:** Can't change your fingerprint if it's stolen
- **Replayable:** Attacker can steal biometric data (fingerprint scan from OPM breach 2015: 5.6M fingerprints)
- **False positives:** Biometric systems have error rates (1-5% FAR, False Accept Rate)
- **Accessibility:** Not everyone can use biometric auth (injury, disability)

**Best use:** Biometrics as **second factor** (something you are) + password/passkey (something you know/have).

---

## Active Recall Prompts

### Understanding Questions

1. **Attack types:** Explain the difference between brute force, dictionary, and hybrid attacks. When would you use each?

2. **Hash functions:** Why is MD5 bad for passwords? What makes bcrypt/Argon2 better?

3. **Salting:** How does salting defend against rainbow tables? Draw the flow for salted password storage and verification.

---

### Application Questions

4. **Time-to-crack estimation:** A password database uses bcrypt (10 rounds). Attacker has a GPU that can test 10,000 bcrypt hashes/second. How long to crack:
   - A 6-character lowercase password? (keyspace: 26^6)
   - An 8-character alphanumeric password? (keyspace: 62^8)

5. **Defense design:** You're implementing login for a web app. Design a defense against:
   - Brute force attacks
   - Credential stuffing
   - Phishing

6. **Password policy:** Your company currently requires:
   - Minimum 8 characters
   - At least 1 uppercase, 1 lowercase, 1 digit, 1 symbol
   - Change every 90 days

   Critique this policy using modern best practices (NIST 800-63B). What would you change?

---

### Transfer Questions

7. **Real-world analysis:** Research the **RockYou breach (2009)**. What password storage mistakes were made? How many passwords were cracked immediately?

8. **Tool exploration:** Install and use **John the Ripper** or **Hashcat** on a practice hash list. Document:
   - Time to crack MD5 vs bcrypt
   - Success rate of dictionary vs brute force

9. **Phishing defense:** Create a security awareness training module on password phishing. Include:
   - Red flags to spot phishing emails
   - How to verify login pages
   - What to do if you suspect phishing

10. **Passwordless future:** Research **FIDO2/WebAuthn** and **passkeys**. How do they eliminate password attacks? What are the trade-offs?

---

## References

### Primary Sources

- **Course:** IFT2830 - Sécurité des systèmes informatiques (UdeM)
  Lectures: [Password Attacks & Authentication](../../../05_references/course-materials/IFT2830_course-materials/)

### Standards & Best Practices

- **NIST SP 800-63B** — Digital Identity Guidelines (Authentication and Lifecycle Management)
- **OWASP Authentication Cheat Sheet** — https://cheatsheetseries.owasp.org/cheatsheets/Authentication_Cheat_Sheet.html
- **CWE-259** — Use of Hard-coded Password
- **CWE-521** — Weak Password Requirements

### Tools & Resources

- **John the Ripper** — Open-source password cracker
- **Hashcat** — Advanced password recovery tool
- **Have I Been Pwned** — Breach database for checking compromised credentials (haveibeenpwned.com)
- **Password strength meter** — zxcvbn (Dropbox library for estimating password strength)

### Real-World Incidents

- **RockYou (2009)** — 32M plaintext passwords stolen, revealed password habits
- **LinkedIn (2012, 2021)** — 167M (2012), 700M (2021) credentials breached
- **Dropbox (2016)** — 68M passwords stolen (bcrypt, but still cracked 5%)
- **LastPass (2022)** — Master password vault encrypted, but threat remains

### Academic Research

- Bonneau, J. (2012). "The Science of Guessing: Analyzing an Anonymized Corpus of 70 Million Passwords." _IEEE S&P_.
- Florêncio, D., & Herley, C. (2007). "A Large-Scale Study of Web Password Habits." _WWW Conference_.

---

## Related Content

### Theory Modules

- **Previous:** [Attack Lifecycle](attack-lifecycle.md) — Initial access phase
- **Next:** [Social Engineering](social-engineering.md) — Human-factor attacks
- **Related:** [Cryptography Basics](../01-cryptography/cryptography-basics.md) — Hashing deep dive

### Examples

- [Cracking Hashes with Hashcat](../../../02_examples/03-offensive-security/cracking-hashes/) — Hands-on password cracking
- [Phishing Campaign Demo](../../../02_examples/03-offensive-security/phishing-campaign/) — Social engineering attack
- [Implementing Secure Password Storage](../../../02_examples/05-application-security/secure-password-storage/) — Defensive implementation

### Exercises

- [Password Strength Analysis](../../../03_exercises/03-offensive-security/password-strength/) 🟢 — Analyze real passwords
- [Hash Cracking Lab](../../../03_exercises/03-offensive-security/hash-cracking/) 🟡 — Use John/Hashcat
- [Phishing Email Creation](../../../03_exercises/03-offensive-security/phishing-email/) 🟡 — Ethical red team exercise

### Tools & Resources

- **Password Tools:** `04_resources/tools/password-cracking/`
- **Wordlists:** `04_resources/tools/wordlists/rockyou.txt`
- **Hash Examples:** `04_resources/examples/password-hashes/`

---

## Personal Insights & Notes

### Study Notes

_Record your observations, "aha" moments, and connections here._

**Example:**

- "Length > complexity. `correct horse battery staple` beats `X7!kQ#2p` every time."
- "Hash algorithm choice is more important than password complexity at scale."

---

### Real-World Connections

_Link this concept to incidents, news, or work experience._

**Example:**

- "LinkedIn breach — unsalted SHA-1 hashes. 90% cracked in days. Shows importance of salting + slow hashing."

---

### Questions & Confusion

_Track what's unclear or needs deeper investigation._

**Example:**

- "How exactly does bcrypt's adaptive cost factor work? Need to research the algorithm internals."

---

### Exam/Interview Prep

_Key points to remember for assessments._

**Exam focus (IFT2830):**

- Attack types: Force brute, Dictionnaire, Hybride, Bourrage de références, Table arc-en-ciel, Hameçonnage
- Hash functions: MD5/SHA (fast, bad), bcrypt/Argon2 (slow, good)
- Salting: Unique random value per password, defeats rainbow tables
- Defense: Lockout, rate limiting, MFA, breach database checking

**Interview talking points:**

- "Passwords should never be stored in plaintext. Always hash with bcrypt or Argon2."
- "Length beats complexity. Passphrases are stronger and more user-friendly."
- "MFA is the most effective defense against password attacks. Even stolen passwords become useless."

---

## Change Log

| Date       | Change                          | Reason                                                                         |
| ---------- | ------------------------------- | ------------------------------------------------------------------------------ |
| 2026-04-27 | Created module                  | Password attacks foundational offensive technique                              |
| 2026-04-27 | Added 6 attack types            | Brute force, dictionary, hybrid, credential stuffing, rainbow tables, phishing |
| 2026-04-27 | Added hash algorithm comparison | MD5/SHA vs bcrypt/Argon2 security analysis                                     |
| 2026-04-27 | Added real breach examples      | RockYou, LinkedIn, Dropbox, LastPass                                           |
| 2026-04-27 | Integrated French terminology   | Bilingual support throughout                                                   |
