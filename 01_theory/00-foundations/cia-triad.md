# CIA Triad — Confidentialité, Intégrité, Disponibilité

| Property          | Value                                 |
| ----------------- | ------------------------------------- |
| **Topic**         | CIA Triad / Tripartite de la Sécurité |
| **Domain**        | 00-foundations                        |
| **Difficulty**    | 🟢 Beginner                           |
| **Prerequisites** | None (foundational concept)           |
| **Learning Time** | 30-45 minutes                         |
| **Status**        | ✅ Complete                           |

---

## Review Schedule

- [ ] Day 2 — First review after initial study
- [ ] Week 1 — Consolidation review
- [ ] Month 1 — Long-term retention check
- [ ] Month 3 — Mastery verification

---

## Quick Summary

**What:** The CIA Triad defines the three fundamental pillars of information security.

**Offensive:** Attackers target one or more CIA properties to compromise systems.
**Defensive:** Security controls aim to preserve CIA properties.

**Why it matters:** Every security threat, vulnerability, and control maps to CIA. Understanding this triad provides a universal framework for analyzing security situations.

---

## Prerequisites

**Required knowledge:**

- Basic understanding of computer systems
- Familiarity with data and information concepts

**Quick check:** Can you explain what "data" and "information" mean in computing? If yes, you're ready.

---

## Layer 1 — Intuition

Think of the CIA Triad as three locks on a safe containing valuable information:

🔒 **Confidentiality (Confidentialité)** = Only authorized people have the key
🔒 **Integrity (Intégrité)** = The contents can't be tampered with
🔒 **Availability (Disponibilité)** = The safe can be opened when needed

**Break any one lock, and the information is compromised.**

---

## Layer 2 — Formal Definition

### Confidentiality (Confidentialité)

**Definition:** Information is accessible only to those authorized to have access.

**Property:** Prevents unauthorized disclosure of sensitive information.

**Violation examples:** Data breach, eavesdropping, stolen credentials

**French term:** _Confidentialité_

---

### Integrity (Intégrité)

**Definition:** Information remains accurate, complete, and unmodified except by authorized entities.

**Property:** Prevents unauthorized modification or destruction of information.

**Violation examples:** Data tampering, man-in-the-middle attacks, bit-flipping

**French term:** _Intégrité_

---

### Availability (Disponibilité)

**Definition:** Information and systems are accessible to authorized users when needed.

**Property:** Prevents denial of service and ensures operational continuity.

**Violation examples:** DoS/DDoS attacks, ransomware, system crashes

**French term:** _Disponibilité_

---

## Layer 3 — Worked Examples

### Example 1: Medical Records System

**Scenario:** A hospital maintains electronic health records (EHR).

#### CIA Analysis:

| Property            | Requirement                                                                                 | Threat                                                                | Control                                                            |
| ------------------- | ------------------------------------------------------------------------------------------- | --------------------------------------------------------------------- | ------------------------------------------------------------------ |
| **Confidentiality** | Only authorized medical staff can view patient records                                      | Unauthorized access by hackers or curious employees                   | Role-based access control (RBAC), encryption at rest, audit logs   |
| **Integrity**       | Medical records must be accurate and complete; no tampering with diagnoses or prescriptions | Malicious modification of treatment plans, accidental data corruption | Digital signatures, version control, write-once storage, checksums |
| **Availability**    | Doctors must access records 24/7 for emergency care                                         | Ransomware locking records, server downtime, network outages          | Redundant systems, backups, DDoS mitigation, disaster recovery     |

**Real incident:** In 2017, WannaCry ransomware attacked UK's NHS, compromising **availability** (patients couldn't be treated) while leaving confidentiality and integrity intact.

---

### Example 2: Password Attack on Web Application

**Attacker action:** Brute-force attack to guess user passwords

#### CIA Impact:

- **Confidentiality: VIOLATED** — Attacker gains access to user account and views private data
- **Integrity: AT RISK** — Once inside, attacker could modify user data, settings, or posts
- **Availability: MINIMAL** — Unless the attack causes system overload, availability is preserved

**Defensive countermeasures:**

- **Preserve Confidentiality:** Strong password policy, MFA (multi-factor authentication), rate limiting
- **Preserve Integrity:** Account activity monitoring, change logs, anomaly detection
- **Preserve Availability:** CAPTCHA after failed attempts, IP-based rate limiting

---

### Example 3: DDoS Attack on E-commerce Site

**Attacker action:** Distributed Denial of Service (DDoS) flooding web server with traffic

#### CIA Impact:

- **Confidentiality: INTACT** — No data is stolen or exposed
- **Integrity: INTACT** — Data is not modified
- **Availability: VIOLATED** — Legitimate customers cannot access the site; revenue loss

**Defensive countermeasures:**

- **Preserve Availability:** CDN with DDoS mitigation (Cloudflare, AWS Shield), rate limiting, load balancing, traffic filtering

**Real incident:** In 2016, Dyn DNS was hit by Mirai botnet DDoS, taking down Twitter, Netflix, Reddit — pure **availability** attack.

---

## Layer 4 — Edge Cases, Nuances, and Limitations

### Edge Case 1: CIA Conflicts and Trade-offs

**Problem:** Maximizing one CIA property can weaken another.

**Example:**

- **High Confidentiality + High Availability conflict:**
  Strong encryption protects confidentiality but adds latency and complexity, potentially reducing availability.

- **High Integrity + High Availability conflict:**
  Strict integrity checks (e.g., blockchain consensus) slow down transaction speed, reducing availability.

**Solution:** Risk-based prioritization. Medical records prioritize **integrity** and **confidentiality** over speed. Financial trading systems prioritize **availability** with strong integrity controls.

---

### Edge Case 2: Extended CIA Models

The basic CIA Triad is often extended:

| Extended Property   | French Term       | Meaning                                            |
| ------------------- | ----------------- | -------------------------------------------------- |
| **Authenticity**    | _Authenticité_    | Assurance that entities are who they claim to be   |
| **Non-repudiation** | _Non-répudiation_ | Proof that an action occurred and cannot be denied |
| **Accountability**  | _Imputabilité_    | Ability to trace actions to specific individuals   |
| **Traceability**    | _Traçabilité_     | Ability to track the history of data and actions   |

**When to use extended model:**

- Legal/compliance contexts (banking, government)
- Forensics and incident response
- Advanced threat modeling

**IFT2830 course note:** The course covers these extended properties as _propriétés supplémentaires de sécurité_.

---

### Edge Case 3: Partial CIA Violations

**Reality:** Most attacks don't completely destroy a CIA property; they degrade it.

**Examples:**

- **Partial confidentiality breach:** Only some user records are stolen, not the entire database
- **Partial integrity violation:** Metadata is modified, but core data remains intact
- **Partial availability loss:** System is slow but not completely offline

**Analysis implication:** Risk assessment must consider **degree of impact**, not just binary success/failure.

---

### Limitation 1: CIA Does Not Address All Security Concerns

**What CIA does NOT cover:**

- **Privacy** — Protection of personal identity and personal data (related to but distinct from confidentiality)
- **Safety** — Physical harm prevention (e.g., medical device security, industrial control systems)
- **Compliance** — Legal and regulatory requirements (GDPR, HIPAA)

**When CIA is insufficient:** Use domain-specific frameworks (e.g., NIST Cybersecurity Framework, ISO 27001).

---

### Limitation 2: CIA Assumes Clear Trust Boundaries

**Problem:** Modern systems blur trust boundaries (cloud, microservices, zero-trust networks).

**Example:**

- In cloud environments, **confidentiality** depends on the cloud provider's security posture, not just your own controls.
- In zero-trust architectures, **availability** might be reduced by continuous authentication checks.

**Solution:** Complement CIA with Zero Trust principles, shared responsibility models, and supply chain security.

---

## Active Recall Prompts

Test your understanding with these questions. Answer before revealing solutions.

### Understanding Questions

1. **Define each property:** Without looking, write one-sentence definitions of Confidentiality, Integrity, and Availability.

2. **Map attacks to CIA:** Classify these attacks by primary CIA violation:
   - SQL injection modifying database records
   - Ransomware encrypting files
   - Packet sniffing on unencrypted Wi-Fi
   - DDoS flooding a web server

3. **French terminology:** Match French terms to English:
   - Confidentialité
   - Intégrité
   - Disponibilité
   - Non-répudiation
   - Traçabilité

---

### Application Questions

4. **Design scenario:** You're securing an online banking system. For each CIA property, propose one technical control and explain why it's effective.

5. **Prioritization:** A startup has limited budget. They handle user-generated content (social media posts). Should they prioritize Confidentiality, Integrity, or Availability? Justify.

6. **Incident analysis:** A company discovers that an insider modified financial reports over 6 months. Which CIA property was violated? What controls could have prevented this?

---

### Transfer Questions

7. **Real-world mapping:** Think of a recent cybersecurity incident in the news. Map it to the CIA Triad. Which properties were violated? Were there trade-offs?

8. **Cross-domain application:** Apply CIA to physical security. What is the "confidentiality" of a building? "Integrity"? "Availability"?

9. **Extended CIA:** When would you add "Non-repudiation" as a fourth pillar? Give a concrete scenario where CIA alone is insufficient.

10. **Attacker perspective:** You're a pentester. Your client asks you to test each CIA property separately. Design three distinct attacks targeting C, I, and A individually.

---

## References

### Primary Sources

- **Course:** IFT2830 - Sécurité des systèmes informatiques (UdeM)
  Lectures: [2026-01-12 Introductions](../../../05_references/course-materials/IFT2830_course-materials/notes/2026-01-12_Introductions%20et%20Généralités.md), [01_theory-intra](../../../05_references/course-materials/IFT2830_course-materials/01_theory-intra.md)

- **ISO 27001:2022** — Information Security Management Systems
  Sections 5.1-5.3: Security policies and CIA principles

### Standards & Frameworks

- **NIST SP 800-53** — Security and Privacy Controls
  Controls organized by CIA objectives

- **OWASP** — Application security maps to CIA violations
  See: [OWASP Top 10](../../../05_references/standards/OWASP/owasp-top-10-2021.md)

### Academic Papers

- Stallings, W. (2017). _Network Security Essentials_, Chapter 1: "Security Goals"
- Anderson, R. (2020). _Security Engineering_, Chapter 1: "What is Security Engineering?"

### Real-World Incidents

- **WannaCry (2017)** — Availability violation via ransomware
- **Equifax breach (2017)** — Confidentiality violation (143M records)
- **Stuxnet (2010)** — Integrity violation (modified SCADA commands)

---

## Related Content

### Theory Modules

- **Next:** [Security Properties](security-properties.md) — Extended security characteristics beyond CIA
- **Next:** [Risk Analysis](risk-analysis.md) — Assessing threats to CIA properties
- **Related:** [Threat Modeling Basics](threat-modeling-basics.md) — Identifying CIA threats

### Examples

- [Medical Records CIA Analysis](../../../02_examples/00-foundations/medical-records-cia-analysis/) — Worked healthcare example
- [Web App CIA Failures](../../../02_examples/00-foundations/web-app-cia-failures/) — Common CIA violations in web apps

### Exercises

- [CIA Property Classification](../../../03_exercises/00-foundations/cia-property-classification/) 🟢 — Practice categorizing attacks
- [CIA Trade-off Analysis](../../../03_exercises/00-foundations/cia-tradeoff-analysis/) 🟡 — Explore conflicts between properties
- [Build a Secure System](../../../03_exercises/00-foundations/build-secure-system/) 🟡 — Design controls for each CIA property

### Tools & Resources

- **CIA Visual Diagrams:** `04_resources/tools/visualization/cia-triad-diagram.md`
- **Attack-to-CIA Mapping:** `04_resources/tools/frameworks/attack-cia-mapping.csv`

---

## Personal Insights & Notes

### Study Notes

_Record your observations, "aha" moments, and connections here._

**Example:**

- "Realized that most web vulnerabilities (XSS, SQLi, CSRF) are primarily **integrity** attacks disguised as confidentiality threats."
- "DDoS is pure availability attack — no data stolen, no data modified, just denial."

---

### Real-World Connections

_Link this concept to incidents, news, or work experience._

**Example:**

- "GitLab outage (2017) — accidental deletion = integrity + availability failure, not a confidentiality issue."

---

### Questions & Confusion

_Track what's unclear or needs deeper investigation._

**Example:**

- "How do you measure 'partial availability'? Is 90% uptime enough? Context-dependent?"

---

### Exam/Interview Prep

_Key points to remember for assessments._

**Exam focus (IFT2830):**

- French terminology: Confidentialité, Intégrité, Disponibilité
- Map attacks to CIA violations
- Understand extended properties: Non-répudiation, Traçabilité, Imputabilité

**Interview talking points:**

- "Every security control maps to preserving one or more CIA properties."
- "CIA conflicts require risk-based prioritization."

---

## Change Log

| Date       | Change                     | Reason                                            |
| ---------- | -------------------------- | ------------------------------------------------- |
| 2026-02-16 | Created module             | Initial theory module based on IFT2830 curriculum |
| 2026-02-16 | Added French terminology   | Bilingual support for UdeM course                 |
| 2026-02-16 | Added real-world incidents | Concrete examples (WannaCry, Equifax, Stuxnet)    |
