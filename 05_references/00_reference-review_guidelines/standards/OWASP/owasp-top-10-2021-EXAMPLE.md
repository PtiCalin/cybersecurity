# OWASP Top 10 — 2021

> Example reference note demonstrating the template structure

---

## Metadata

| Field | Value |
|-------|-------|
| **Type** | Standard / Framework |
| **Authors/Organization** | OWASP Foundation |
| **Year** | 2021 |
| **Publication/Venue** | OWASP.org |
| **URL** | https://owasp.org/Top10/ |
| **DOI** | N/A |
| **Date Accessed** | 2026-04-27 |
| **Version** | 2021 |
| **Reading Status** | Completed |
| **Relevance** | High |
| **Difficulty** | Beginner to Intermediate |
| **Est. Reading Time** | 2-3 hours for full document |

### Tags

`#web-security` `#application-security` `#owasp` `#vulnerabilities` `#defensive` `#standard`

### Related References

- [Link to OWASP ASVS note when created]
- [Link to related CVE notes]

---

## Executive Summary

**One-sentence summary:**
OWASP Top 10 is a consensus-driven ranking of the most critical web application security risks based on data from security practitioners worldwide.

**Key contribution:**
Provides a standardized framework for understanding, prioritizing, and mitigating the most prevalent web security vulnerabilities, enabling organizations to focus limited security resources on the highest-impact risks.

**Why this matters:**
Web applications are primary attack surfaces for modern organizations. The Top 10 framework has become the de facto industry standard for web security awareness, training, and secure development practices, directly influencing security policies, testing methodologies, and compliance requirements.

---

## Context and Background

### Problem/Question Addressed

How should organizations prioritize web application security efforts when facing unlimited potential vulnerabilities with limited resources?

### Scope and Limitations

- **Scope:** Web application security risks, ranked by prevalence and impact
- **Out of scope:** Infrastructure security, network security, physical security, non-web applications
- **Limitations:** 
  - Updated every 3-4 years (may lag emerging threats)
  - Focus on prevalence over sophistication (APT techniques may not rank highly)
  - Western-centric data collection
  - Does not replace comprehensive security testing

### Prerequisites

Knowledge required to understand this reference:
- Basic web architecture (client-server, HTTP/HTTPS)
- Common web technologies (HTML, JavaScript, SQL)
- Basic security concepts (authentication, authorization, encryption)

---

## Key Concepts

### Core Ideas

1. **Risk-Based Prioritization**
   - **Definition:** Ranking vulnerabilities by likelihood × impact rather than theoretical severity alone
   - **Mechanism:** Data-driven analysis of real-world exploitation frequency combined with business impact assessment
   - **Significance:** Enables efficient resource allocation focused on actual, not hypothetical, risks

2. **Shift-Left Security**
   - **Definition:** Integrating security considerations early in the development lifecycle
   - **Mechanism:** Using the Top 10 as a checklist during design, development, and code review phases
   - **Significance:** Prevention is cheaper and more effective than post-deployment remediation

3. **Defense in Depth**
   - **Definition:** Multiple overlapping security controls at different layers
   - **Mechanism:** No single mitigation prevents all instances of a vulnerability class
   - **Significance:** Reduces single points of failure in security architecture

### Terminology

| Term | Definition | Context |
|------|------------|---------|
| CWE | Common Weakness Enumeration | Underlying vulnerability patterns that map to Top 10 categories |
| CVSS | Common Vulnerability Scoring System | Standardized severity scoring referenced in impact assessments |
| SAST | Static Application Security Testing | Automated code analysis for vulnerability detection |
| DAST | Dynamic Application Security Testing | Runtime testing of deployed applications |

---

## Main Content Extraction

### A01:2021 — Broken Access Control

**Summary:**
Access control failures occur when users can act outside their intended permissions, accessing unauthorized data or functionality.

**Key Points:**
- Moved from #5 (2017) to #1 (2021) — highest prevalence
- 34 CWEs mapped to this category
- Average incidence rate: 3.81%
- Includes: IDOR, privilege escalation, forced browsing, missing function-level access control

**Offensive Techniques:**
- Parameter tampering (changing user IDs in URLs/requests)
- Forced browsing (accessing admin pages without authentication)
- Horizontal privilege escalation (accessing other users' data)
- Vertical privilege escalation (gaining admin rights)

**Defensive Countermeasures:**
- Deny by default access control model
- Centralized access control mechanism
- Server-side enforcement (never trust client-side checks)
- Log access control failures for anomaly detection
- Rate limiting on APIs to prevent automated attacks

**Code Example (Vulnerable):**
```java
// Insecure Direct Object Reference (IDOR)
@GetMapping("/api/user/{userId}/profile")
public UserProfile getProfile(@PathVariable String userId) {
    // No check if requester owns this userId!
    return userService.getProfile(userId);
}
```

**Code Example (Secure):**
```java
@GetMapping("/api/user/{userId}/profile")
public UserProfile getProfile(@PathVariable String userId, Principal principal) {
    if (!userId.equals(principal.getName()) && !hasAdminRole(principal)) {
        throw new AccessDeniedException("Unauthorized access");
    }
    return userService.getProfile(userId);
}
```

---

### A02:2021 — Cryptographic Failures

**Summary:**
Previously "Sensitive Data Exposure," refocused on cryptographic failures that lead to data compromise.

**Key Points:**
- Includes failures related to encryption, hashing, and randomness
- Common issues: weak algorithms, improper key management, missing encryption
- Data in transit and data at rest both require protection

**Offensive Techniques:**
- Man-in-the-middle attacks on unencrypted channels
- Rainbow table attacks on unsalted hashes
- Padding oracle attacks on weak encryption
- Downgrade attacks to force weaker algorithms

**Defensive Countermeasures:**
- TLS 1.2+ for data in transit (enforce perfect forward secrecy)
- AES-256 or ChaCha20 for data at rest
- bcrypt, scrypt, or Argon2 for password hashing (never MD5/SHA1)
- Proper key management (HSM or key vault)
- Disable legacy protocols (SSLv3, TLS 1.0/1.1)

---

### A03:2021 — Injection

**Summary:**
Hostile data sent to an interpreter is executed as commands or queries, leading to data loss, corruption, or unauthorized access.

**Key Points:**
- Dropped from #1 (2017) to #3 (2021) but still critical
- Includes: SQL, NoSQL, OS command, LDAP, XPath, XXE
- 33 CWEs mapped to this category
- 94% of applications tested showed some form of injection

**Offensive Techniques:**
- SQL injection (extracting database contents, authentication bypass)
- Command injection (OS command execution)
- LDAP injection (authentication bypass, data exfiltration)
- XML External Entity (XXE) attacks

**Defensive Countermeasures:**
- Parameterized queries / prepared statements (NEVER string concatenation)
- ORM with proper escaping
- Input validation with allowlist approach
- Least privilege database accounts
- WAF for defense in depth

**Code Example (Vulnerable SQL):**
```python
# NEVER DO THIS
query = "SELECT * FROM users WHERE username = '" + username + "'"
cursor.execute(query)
```

**Code Example (Secure):**
```python
# Use parameterized queries
query = "SELECT * FROM users WHERE username = ?"
cursor.execute(query, (username,))
```

---

## Important Quotes

> "Security is a continuous process, not a destination. The Top 10 represents the most critical risks at this point in time."
> 
> — OWASP Top 10 Introduction

**Context:** Emphasizes that the Top 10 is a snapshot, not exhaustive. Organizations must maintain ongoing security vigilance beyond these ten categories.

---

> "Developers and security professionals must share responsibility for application security. Security cannot be bolted on at the end."
> 
> — OWASP Top 10 Forward

**Context:** Core philosophy of shift-left security and DevSecOps integration.

---

## Critical Analysis

### Strengths

- Data-driven methodology (real-world evidence, not theoretical)
- Industry consensus and broad adoption
- Actionable guidance with specific mitigation strategies
- Free and vendor-neutral
- Excellent educational resource

### Weaknesses

- Update cycle can lag emerging threats (3-4 year gaps)
- May miss low-prevalence but high-sophistication attacks
- Some categories are broad and could be further decomposed
- Prevalence data biased toward tested applications
- Does not address all security concerns (business logic flaws often missed)

### Assumptions and Biases

- Assumes web application context (not applicable to all software)
- Data primarily from organizations that actively test security
- Western security community perspective
- Focus on OWASP testing methodology may miss other vulnerability types

---

## Personal Insights and Reflections

### Key Takeaways

1. **Access control is the highest risk** — Easy to implement incorrectly, difficult to test comprehensively, high impact when exploited
2. **Prevention requires multiple controls** — No single mitigation eliminates a vulnerability class entirely
3. **Data-driven approach is powerful** — Real-world prevalence matters more than theoretical severity

### Questions Raised

- How do newer technologies (GraphQL, serverless, containers) affect these rankings?
- What about security risks specific to mobile applications or APIs?
- How to prioritize when facing multiple Top 10 categories simultaneously?

### Connections to Other Knowledge

**Relates to Theory:**
- [01_theory/application-security/](../../01_theory/) — Foundation for understanding each category
- [01_theory/threat-modeling/](../../01_theory/) — Risk assessment methodology

**Practical Applications:**
- [02_examples/](../../02_examples/) — Demonstrations of each vulnerability type
- [03_exercises/](../../03_exercises/) — Practice identifying and exploiting these vulnerabilities

**Tool/Framework Mentioned:**
- [04_resources/tools/](../../04_resources/tools/) — SAST, DAST, and testing tools

### Contradictions or Conflicts

The ranking is based on prevalence, not sophistication. Advanced attackers may focus on categories NOT in the Top 10. Organizations must balance addressing common issues with preparing for targeted attacks.

---

## Practical Application

### Use Cases

1. **Security Training**
   - **Scenario:** Onboarding developers to security fundamentals
   - **Implementation:** Use Top 10 as curriculum structure, one category per training session
   - **Expected Outcome:** Baseline security awareness across development team

2. **Secure Code Review**
   - **Scenario:** Reviewing pull requests for security issues
   - **Implementation:** Checklist based on Top 10 categories relevant to changes
   - **Expected Outcome:** Early detection of vulnerabilities before merge

3. **Penetration Testing Scope**
   - **Scenario:** Defining what to test in a security assessment
   - **Implementation:** Use Top 10 as minimum baseline coverage
   - **Expected Outcome:** Comprehensive testing of highest-risk areas

### Lab Exercise Ideas

- Build intentionally vulnerable application with all 10 categories
- Exploit each vulnerability type in a controlled lab environment
- Implement defenses and verify mitigation effectiveness
- Compare SAST vs DAST detection rates for each category

### Tools and Resources Mentioned

- OWASP ZAP — Web application security testing
- Burp Suite — Web security testing platform
- SonarQube — Static analysis with OWASP rules
- SQLMap — SQL injection testing tool

---

## Review Schedule

> Learning retention strategy: revisit this note at spaced intervals

- **First Review:** 2026-04-28 — `<!-- REVIEW: 2026-04-28 -->`
- **Second Review:** 2026-05-04 — `<!-- REVIEW: 2026-05-04 -->`
- **Third Review:** 2026-05-27 — `<!-- REVIEW: 2026-05-27 -->`
- **Fourth Review:** 2026-07-27 — `<!-- REVIEW: 2026-07-27 -->`

### Review Checklist

On each review:
- [ ] Can I explain each of the 10 categories without looking?
- [ ] Can I identify these vulnerabilities in code?
- [ ] Have I updated knowledge of recent CVEs in these categories?
- [ ] Do I need to revise any understanding based on new information?

---

## Citation

### APA Format

OWASP Foundation. (2021). *OWASP Top 10 - 2021: The Ten Most Critical Web Application Security Risks*. https://owasp.org/Top10/

### BibTeX

```bibtex
@techreport{owasp2021top10,
  author = {{OWASP Foundation}},
  title = {OWASP Top 10 - 2021: The Ten Most Critical Web Application Security Risks},
  year = {2021},
  url = {https://owasp.org/Top10/},
  institution = {OWASP Foundation}
}
```

---

## Change Log

| Date | Change | Reason |
|------|--------|--------|
| 2026-04-27 | Initial note created | Example reference for template demonstration |

---

## Additional Resources

### Supplementary Reading

- OWASP Application Security Verification Standard (ASVS)
- OWASP Testing Guide
- CWE Top 25 Most Dangerous Software Weaknesses

### Video/Talks

- OWASP Top 10 2021 webinar series
- Conference talks on each individual category

### Code Repositories

- WebGoat — Intentionally insecure application for learning
- DVWA — Damn Vulnerable Web Application
- OWASP Juice Shop — Modern vulnerable web application
