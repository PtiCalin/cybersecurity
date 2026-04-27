# Application Security — Secure Software Development

This directory contains theory modules on application-level security vulnerabilities, secure coding practices, and web/mobile security.

## Topics Covered

### Web Application Security
- [OWASP Top 10](owasp-top-10.md) — Most critical web vulnerabilities
- [SQL Injection](sql-injection.md) — Database attack and prevention
- [Cross-Site Scripting (XSS)](cross-site-scripting.md) — Client-side injection
- [Cross-Site Request Forgery (CSRF)](csrf.md) — Session hijacking
- [Authentication Vulnerabilities](authentication-vulnerabilities.md) — Broken auth, session management

### Secure Development
- [Secure Coding Practices](secure-coding-practices.md) — Input validation, output encoding
- [Security by Design](security-by-design.md) — Threat modeling during development
- [Code Review for Security](code-review-security.md) — Identifying vulnerabilities in code
- [Dependency Management](dependency-management.md) — Supply chain security

### Mobile Security
- [Mobile Application Security](mobile-app-security.md) — Android/iOS vulnerabilities
- [API Security](api-security.md) — REST/GraphQL security
- [OAuth and OpenID Connect](oauth-openid.md) — Secure authentication flows

### Advanced Topics
- [Deserialization Attacks](deserialization-attacks.md) — Object injection
- [Server-Side Request Forgery (SSRF)](ssrf.md) — Backend exploitation
- [XML External Entity (XXE)](xxe.md) — XML parsing vulnerabilities

---

## Learning Path

**Recommended study order:**
1. OWASP Top 10 — Overview of critical vulnerabilities
2. SQL Injection — Most common database attack
3. Cross-Site Scripting (XSS) — Client-side exploitation
4. Authentication Vulnerabilities — Broken access control
5. Secure Coding Practices — Prevention strategies
6. API Security — Modern application architecture
7. Security by Design — Proactive security

**Prerequisites:** 
- [CIA Triad](../00-foundations/cia-triad.md) — Understanding security properties
- Web development basics (HTTP, HTML, JavaScript)
- Database fundamentals (SQL)

**Leads to:** 
- [Defensive Security](../04-defensive-security/) — Application monitoring and WAF
- [Offensive Security](../03-offensive-security/) — Web application pentesting

---

## Integration

**Examples:** See `02_examples/05-application-security/` for practical demonstrations
**Exercises:** Practice in `03_exercises/05-application-security/` (vulnerable app challenges)
**References:** 
- Standards: `05_references/standards/OWASP/`
- Course: IFT2830 application security topics

---

**Key:** 🟢 Beginner | 🟡 Intermediate | 🟠 Advanced
