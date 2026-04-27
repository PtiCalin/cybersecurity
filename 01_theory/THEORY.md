# Theory

This directory contains structured, pedagogically optimized cybersecurity theory modules. Each module is designed for deep understanding, long-term retention, and practical application.

---

## Quick Access

- **[Theory Note Template](_theory-note-template.md)** — Standardized structure for all theory explanations
- **[Example Theory Modules](#example-modules)** — See templates in action
- **[Learning Paths](#learning-paths)** — Recommended study sequences
- **[Domain Map](#domain-organization)** — Navigate by cybersecurity domain

---

## Purpose

Theory modules provide the conceptual foundation for cybersecurity knowledge. Unlike passive textbook reading, these notes are **active learning tools** designed to:

1. **Build mental models** through multi-layer explanations (intuition → formal → worked example → edge cases)
2. **Support retention** via spaced repetition markers and active recall prompts
3. **Enable transfer learning** by connecting concepts across domains
4. **Balance perspectives** with both offensive and defensive viewpoints
5. **Link to practice** through tight integration with examples and exercises
6. **Maintain academic rigor** with citations to authoritative references

---

## Domain Organization

```
01_theory/
├── THEORY.md                        # This file
├── _theory-note-template.md         # Template for new theory notes
│
├── 00-foundations/                  # Prerequisites and core concepts
│   ├── security-principles.md
│   ├── threat-modeling-basics.md
│   ├── cia-triad.md
│   ├── defense-in-depth.md
│   └── security-mindset.md
│
├── 01-cryptography/                 # Cryptographic theory
│   ├── symmetric-encryption.md
│   ├── asymmetric-encryption.md
│   ├── hash-functions.md
│   ├── digital-signatures.md
│   ├── key-exchange.md
│   └── applied-cryptography.md
│
├── 02-network-security/             # Network protocols and attacks
│   ├── tcp-ip-fundamentals.md
│   ├── network-reconnaissance.md
│   ├── man-in-the-middle.md
│   ├── dns-security.md
│   ├── vpn-and-tunneling.md
│   └── network-defense.md
│
├── 03-offensive-security/           # Ethical hacking and penetration testing
│   ├── reconnaissance-techniques.md
│   ├── vulnerability-assessment.md
│   ├── exploitation-theory.md
│   ├── privilege-escalation.md
│   ├── persistence-mechanisms.md
│   ├── lateral-movement.md
│   └── post-exploitation.md
│
├── 04-defensive-security/           # Detection, response, and hardening
│   ├── intrusion-detection.md
│   ├── incident-response.md
│   ├── security-monitoring.md
│   ├── log-analysis.md
│   ├── system-hardening.md
│   ├── security-operations.md
│   └── threat-hunting.md
│
├── 05-application-security/         # Web, mobile, and API security
│   ├── owasp-top-10.md
│   ├── injection-attacks.md
│   ├── authentication-flaws.md
│   ├── authorization-flaws.md
│   ├── secure-coding.md
│   ├── api-security.md
│   └── mobile-security.md
│
├── 06-malware-analysis/             # Malware theory and analysis
│   ├── malware-types.md
│   ├── static-analysis.md
│   ├── dynamic-analysis.md
│   ├── reverse-engineering-basics.md
│   ├── evasion-techniques.md
│   └── malware-defense.md
│
├── 07-specialized/                  # Advanced and specialized topics
│   ├── cloud-security.md
│   ├── container-security.md
│   ├── iot-security.md
│   ├── social-engineering.md
│   ├── physical-security.md
│   └── compliance-frameworks.md
│
└── 08-frameworks/                   # Security frameworks and methodologies
    ├── mitre-attack.md
    ├── cyber-kill-chain.md
    ├── diamond-model.md
    ├── nist-csf.md
    └── owasp-samm.md
```

---

## Theory Note Structure

Every theory module follows a **four-layer explanation model** optimized for comprehension and retention:

### Layer 1: Intuition (Fast Mental Model)

**Purpose:** Build instant recognition and gist understanding
**Format:** 1-2 sentences, concrete analogy, zero jargon
**Example:** "SQL injection is like slipping a forged instruction into a conversation. Instead of answering a question, you trick the database into following your command."

### Layer 2: Formal Definition

**Purpose:** Precise, unambiguous understanding
**Format:** Technical definition with necessary terminology
**Example:** "SQL injection is a code injection technique that exploits unsanitized user input in SQL queries, allowing attackers to manipulate database operations."

### Layer 3: Worked Example

**Purpose:** Demonstrate concept application step-by-step
**Format:** Real scenario with annotated reasoning at each step
**Requirement:** Both offensive mechanism AND defensive countermeasure

### Layer 4: Edge Cases & Failure Modes

**Purpose:** Develop robust understanding of limitations
**Format:** Where the model breaks, what to watch for, limits of analogies
**Example:** "Defense works when inputs are validated, but fails if validation happens client-side only."

---

## How to Create a New Theory Module

### Step 1: Copy the Template

```bash
# From repository root
cp 01_theory/_theory-note-template.md 01_theory/[domain]/[concept-name].md
```

**Example:**
```bash
cp 01_theory/_theory-note-template.md 01_theory/03-offensive-security/sql-injection.md
```

### Step 2: Fill Metadata

Start with the frontmatter:
- **Topic**: Precise concept name
- **Domain**: Primary domain (cryptography, network, offensive, etc.)
- **Difficulty**: Beginner | Intermediate | Advanced | Expert
- **Prerequisites**: List concepts that must be understood first
- **Learning Time**: Estimated study time
- **Review Schedule**: Spaced repetition dates

### Step 3: Write Layer by Layer

Don't skip layers. Work through all four:
1. **L1 Intuition** — Write the simplest correct explanation first
2. **L2 Formal** — Add precision and terminology
3. **L3 Worked Example** — Show both attack and defense
4. **L4 Edge Cases** — Document limitations and failure modes

### Step 4: Add Active Recall Prompts

Include 3-5 questions that:
- Test understanding, not memorization
- Require application or transfer
- Surface common misconceptions
- Check both offensive and defensive perspectives

### Step 5: Link Across Workspace

Connect to related content:
- **Prerequisites** in other theory modules
- **References** in `05_references/` (papers, standards, CVEs)
- **Examples** in `02_examples/` that demonstrate the concept
- **Exercises** in `03_exercises/` for practice

### Step 6: Set Review Schedule

Use spaced repetition:
- Day 1 (initial read)
- Day 2 (first review)
- Day 7 (one week)
- Day 30 (one month)
- Day 90 (three months)

---

## Learning Paths

Theory modules can be studied in different sequences depending on learning goals.

### Path 1: Absolute Beginner → Security Professional

**Duration:** 12-18 months
**Prerequisites:** Basic computer literacy

| Phase | Domains | Duration | Outcome |
|-------|---------|----------|---------|
| **Phase 1: Foundations** | 00-foundations + selected 01-cryptography | 2-3 months | Understand security principles, threat modeling, CIA triad |
| **Phase 2: Network Basics** | 02-network-security | 2-3 months | TCP/IP, protocols, basic network attacks |
| **Phase 3: Application Security** | 05-application-security | 3-4 months | OWASP Top 10, secure coding, web vulnerabilities |
| **Phase 4: Offensive Core** | 03-offensive-security | 3-4 months | Reconnaissance, exploitation, privilege escalation |
| **Phase 5: Defensive Core** | 04-defensive-security | 2-3 months | Detection, response, hardening |
| **Phase 6: Specialization** | 06-malware-analysis OR 07-specialized | 2-3 months | Choose depth area |

### Path 2: Developer → Secure Developer

**Duration:** 6-9 months
**Prerequisites:** Programming experience

| Phase | Focus | Modules |
|-------|-------|---------|
| **Phase 1** | Security mindset | 00-foundations/security-principles.md, 00-foundations/threat-modeling-basics.md |
| **Phase 2** | Crypto fundamentals | 01-cryptography/ (all basics) |
| **Phase 3** | Web security deep dive | 05-application-security/ (complete) |
| **Phase 4** | Secure coding | 03-offensive-security/ (to understand attacker mindset) + 04-defensive-security/system-hardening.md |
| **Phase 5** | Frameworks | 08-frameworks/owasp-samm.md, 08-frameworks/nist-csf.md |

### Path 3: Security Generalist → Penetration Tester

**Duration:** 9-12 months
**Prerequisites:** Basic security knowledge

| Phase | Focus | Modules |
|-------|-------|---------|
| **Phase 1** | Reconnaissance mastery | 03-offensive-security/reconnaissance-techniques.md, 02-network-security/network-reconnaissance.md |
| **Phase 2** | Exploitation theory | 03-offensive-security/ (complete offensive security domain) |
| **Phase 3** | Attack frameworks | 08-frameworks/mitre-attack.md, 08-frameworks/cyber-kill-chain.md |
| **Phase 4** | Application attacks | 05-application-security/ (offensive perspective) |
| **Phase 5** | Post-exploitation | 03-offensive-security/persistence-mechanisms.md, 03-offensive-security/lateral-movement.md |
| **Phase 6** | Evasion | 06-malware-analysis/evasion-techniques.md, 04-defensive-security/ (to understand detection) |

### Path 4: Security Analyst → Incident Responder

**Duration:** 6-8 months
**Prerequisites:** SOC or security monitoring experience

| Phase | Focus | Modules |
|-------|-------|---------|
| **Phase 1** | Incident response theory | 04-defensive-security/incident-response.md, 04-defensive-security/security-operations.md |
| **Phase 2** | Detection engineering | 04-defensive-security/intrusion-detection.md, 04-defensive-security/threat-hunting.md |
| **Phase 3** | Forensics foundations | 04-defensive-security/log-analysis.md, 06-malware-analysis/ (defensive perspective) |
| **Phase 4** | Threat intelligence | 08-frameworks/diamond-model.md, 08-frameworks/mitre-attack.md |
| **Phase 5** | Offensive understanding | 03-offensive-security/ (to think like attackers) |

---

## Active Learning Workflow

### Phase 1: Pre-Study (5 minutes)

Before reading a theory module:
1. **Preview structure** — Scan headings and diagrams
2. **Check prerequisites** — Ensure foundational concepts are understood
3. **Set learning objective** — What specific question will this answer?
4. **Prime mental model** — What do I already know about this?

### Phase 2: First Pass (30-90 minutes)

1. **Read L1 (Intuition)** — Build the mental model
2. **Read L2 (Formal)** — Add precision
3. **Study L3 (Worked Example)** — Follow step-by-step reasoning
   - Cover the explanation and try to work through it yourself first
   - Compare your reasoning to the provided explanation
4. **Read L4 (Edge Cases)** — Understand limitations
5. **Attempt active recall prompts** — Answer without looking back

### Phase 3: Deep Processing (30-60 minutes)

1. **Write summary in your own words** (Feynman technique)
2. **Create connections** — Link to other theory modules
3. **Explore references** — Read cited papers/standards in `05_references/`
4. **Study corresponding example** — Go to `02_examples/` for practical demonstration
5. **Identify gaps** — What still doesn't make sense?

### Phase 4: Application (30-90 minutes)

1. **Work through exercises** — Practice in `03_exercises/`
2. **Try to teach it** — Explain to someone (or rubber duck)
3. **Build mental test cases** — Create your own attack/defense scenarios
4. **Document personal insights** — Add notes directly in the theory file

### Phase 5: Spaced Review

| Review | Focus | Duration |
|--------|-------|----------|
| **Day 2** | Active recall prompts only, test retention | 10-15 min |
| **Week 1** | Re-read L1-L2, regenerate L3 from memory | 20-30 min |
| **Month 1** | Full re-read, update personal notes, explore new connections | 30-45 min |
| **Month 3** | Active recall only, apply to new problems | 15-20 min |

---

## Quality Standards

Each theory module should:

### Content Quality
- [ ] Provides all four explanation layers (L1-L4)
- [ ] Includes both offensive mechanism AND defensive countermeasure
- [ ] Contains at least one fully worked example
- [ ] Cites authoritative references from `05_references/`
- [ ] Links to practical examples in `02_examples/`
- [ ] Links to practice exercises in `03_exercises/`

### Pedagogical Quality
- [ ] Builds on clearly stated prerequisites
- [ ] Uses concrete analogies in L1 (with limits stated in L4)
- [ ] Provides step-by-step reasoning in L3
- [ ] Includes 3-5 active recall prompts
- [ ] Sets spaced repetition schedule
- [ ] Identifies common misconceptions

### Technical Quality
- [ ] Technically accurate (verified against references)
- [ ] Appropriate difficulty level (matches stated prerequisites)
- [ ] Balanced (doesn't favor offensive or defensive only)
- [ ] Current (reflects modern security landscape)
- [ ] Avoids hand-waving (every claim grounded in mechanism)

---

## Writing Style

### Do

✅ **Use multi-layer progressive disclosure** — Start simple, add complexity incrementally
✅ **Name abstraction levels** — Be explicit about what layer you're operating at
✅ **Show reasoning, not just results** — Explain WHY, not just WHAT
✅ **Use worked examples** — Demonstrate application step-by-step
✅ **State assumptions explicitly** — Don't leave context implicit
✅ **Balance offensive ↔ defensive** — Every attack has a countermeasure
✅ **Connect concepts** — Link to prerequisites and related theory
✅ **Use precise terminology** — But define it when first introduced

### Don't

❌ **Dump information without structure** — Always layer from simple to complex
❌ **Skip reasoning steps** — Don't assume learner fills gaps
❌ **Use vague language** — "kind of", "basically", "it depends" without grounding
❌ **Copy-paste from sources** — Synthesize and explain in your own words
❌ **Ignore edge cases** — Document where the model breaks
❌ **Write passively** — Use active voice and direct language
❌ **Forget the dual perspective** — Always show both attack and defense

---

## Integration with Workspace

Theory modules are the foundation that connects to all other sections:

| Directory | Connection | How to Link |
|-----------|------------|-------------|
| **05_references/** | References provide source material and citations | Link to specific reference notes: `[OWASP Top 10](../../05_references/standards/OWASP/owasp-top-10-2021.md)` |
| **02_examples/** | Examples demonstrate theory in practice | Link to worked demonstrations: `See [SQL Injection Demo](../../02_examples/application-security/sql-injection-demo.md)` |
| **03_exercises/** | Exercises test understanding of theory | Link to practice problems: `Practice: [SQL Injection Exercises](../../03_exercises/application-security/sql-injection-practice.md)` |
| **04_resources/** | Resources provide tools mentioned in theory | Link to tool documentation: `Tool: [Burp Suite](../../04_resources/tools/burp-suite.md)` |

### Linking Convention

Use relative paths from theory module location:
```markdown
**Prerequisites:**
- [CIA Triad](../00-foundations/cia-triad.md)
- [Threat Modeling Basics](../00-foundations/threat-modeling-basics.md)

**References:**
- [OWASP Top 10 2021](../../05_references/standards/OWASP/owasp-top-10-2021.md)
- [CVE-2024-12345](../../05_references/CVE/by-year/2024/cve-2024-12345.md)

**Examples:**
- [SQL Injection Attack Demo](../../02_examples/05-application-security/sql-injection-attack.md)

**Exercises:**
- [SQL Injection Practice](../../03_exercises/05-application-security/sql-injection-beginner.md)
```

---

## Example Modules

See these theory modules for template usage examples:

- [Coming soon: Security Principles example]
- [Coming soon: SQL Injection example]
- [Coming soon: Cryptography example]

---

## Contribution Guidelines

When adding new theory modules:

1. **Check for duplicates** — Search existing modules first
2. **Follow the template** — Use `_theory-note-template.md`
3. **Cite sources** — Link to references in `05_references/`
4. **Create companion content** — Add corresponding example and exercise
5. **Test pedagogical quality** — Can someone learn from this without external resources?
6. **Request review** — Have another learner read and provide feedback

---

## Maintenance

### Monthly Review

- Update outdated techniques or tools
- Add new discoveries and insights
- Refine explanations based on learning experience
- Fix broken links
- Check that references are still current

### Quarterly Audit

- Verify all active recall prompts still test the right concepts
- Update difficulty ratings if needed
- Ensure offensive ↔ defensive balance maintained
- Add connections to newly created modules

---

## Questions or Improvements

Found ways to improve a theory module? Add a note directly in the file under "Personal Insights" or open an issue.

Remember: **These modules are living documents.** Update them as your understanding deepens.