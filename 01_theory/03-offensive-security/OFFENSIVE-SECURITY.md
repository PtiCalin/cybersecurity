# Offensive Security — Ethical Hacking and Penetration Testing

This directory contains theory modules on offensive security techniques, attack methodologies, and penetration testing.

## Topics Covered

### Attack Lifecycle

- **[Attack Lifecycle](attack-lifecycle.md)** ✅ — Complete attack chain from recon to cleanup
- [Reconnaissance Techniques](reconnaissance-techniques.md) — Information gathering
- [Scanning and Enumeration](scanning-enumeration.md) — Network mapping
- [Vulnerability Assessment](vulnerability-assessment.md) — Finding weaknesses

### Exploitation

- [Exploitation Theory](exploitation-theory.md) — How exploits work
- [Exploit Development](exploit-development.md) — Creating exploits
- [Buffer Overflow](buffer-overflow.md) — Memory corruption attacks
- [Code Injection](code-injection.md) — Injection techniques

### Post-Exploitation

- [Privilege Escalation](privilege-escalation.md) — Gaining higher access
- [Persistence Mechanisms](persistence-mechanisms.md) — Maintaining access
- [Lateral Movement](lateral-movement.md) — Moving through networks
- [Data Exfiltration](data-exfiltration.md) — Stealing information

### Authentication Attacks

- **[Password Attacks](password-attacks.md)** ✅ — Brute force, dictionary, rainbow tables
- [Credential Stuffing](credential-stuffing.md) — Reusing stolen credentials
- [Pass-the-Hash](pass-the-hash.md) — Authentication without passwords

### Social Engineering

- [Social Engineering](social-engineering.md) — Human-based attacks
- [Phishing](phishing.md) — Email-based deception
- [Pretexting](pretexting.md) — Fabricated scenarios

---

## Learning Path

**Recommended study order:**

1. Attack Lifecycle — Understand the complete process
2. Reconnaissance Techniques — Information gathering
3. Scanning and Enumeration — Target discovery
4. Password Attacks — Common entry point
5. Exploitation Theory — How attacks work
6. Privilege Escalation — Gaining control
7. Persistence Mechanisms — Maintaining access

**Prerequisites:**

- [CIA Triad](../00-foundations/cia-triad.md)
- [Risk Analysis](../00-foundations/risk-analysis.md)
- [Network Security basics](../02-network-security/)

**Leads to:**

- [Defensive Security](../04-defensive-security/) — Understanding defense through attack knowledge
- [Malware Analysis](../06-malware-analysis/) — Understanding malicious code

---

## Ethical Guidelines

⚠️ **CRITICAL:** All offensive techniques must be:

- Practiced in authorized lab environments only
- Never used on systems without explicit permission
- Paired with defensive countermeasures
- Understood within legal and ethical boundaries

**Every offensive module includes:**

- Defensive perspective
- Detection methods
- Prevention strategies
- Legal considerations

---

## Integration

**Examples:** See `02_examples/03-offensive-security/` for practical demonstrations
**Exercises:** Practice in `03_exercises/03-offensive-security/` (CTF challenges)
**References:**

- Course: `05_references/course-materials/IFT2830_course-materials/`
- Frameworks: `05_references/frameworks/MITRE-ATT&CK/`

---

**Key:** 🟢 Beginner | 🟡 Intermediate | 🟠 Advanced | 🔴 Expert | **Bold** = Priority/Complete
