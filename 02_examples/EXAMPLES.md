# Examples

This directory contains worked demonstrations, attack scenarios, and defense implementations that bring cybersecurity theory to life through practical, annotated examples.

---

## Quick Access

- **[Example Template](_example-template.md)** — Standardized structure for all examples
- **[By Domain](#domain-organization)** — Navigate by security domain
- **[By Type](#example-types)** — Browse by example category
- **[Usage Guide](#how-to-use-examples)** — Learn effectively from examples

---

## Purpose

Examples bridge the gap between theory and practice. Each example provides:

1. **Concrete demonstrations** of concepts from `01_theory/`
2. **Step-by-step walkthroughs** with annotated reasoning
3. **Both offensive and defensive perspectives** in action
4. **Real-world context** with environment setup and prerequisites
5. **Analysis and lessons learned** extracting transferable insights
6. **Links to exercises** for hands-on practice

Examples are **active learning tools**, not passive read-throughs. Work through each step, understand the reasoning, and try variations before moving to exercises.

---

## Domain Organization

```
02_examples/
├── EXAMPLES.md                      # This file
├── _example-template.md             # Template for new examples
│
├── 00-foundations/                  # Foundational concept demonstrations
│   ├── threat-modeling-demo.md
│   ├── cia-triad-scenarios.md
│   └── defense-in-depth-implementation.md
│
├── 01-cryptography/                 # Cryptographic implementations
│   ├── symmetric-encryption-demo.md
│   ├── hash-collision-demo.md
│   ├── rsa-key-generation.md
│   └── tls-handshake-walkthrough.md
│
├── 02-network-security/             # Network attack and defense examples
│   ├── arp-spoofing-demo.md
│   ├── dns-tunneling-example.md
│   ├── packet-analysis-walkthrough.md
│   └── firewall-configuration.md
│
├── 03-offensive-security/           # Penetration testing scenarios
│   ├── reconnaissance-full-cycle.md
│   ├── sql-injection-attack.md
│   ├── privilege-escalation-linux.md
│   ├── privilege-escalation-windows.md
│   ├── buffer-overflow-exploitation.md
│   └── phishing-campaign-anatomy.md
│
├── 04-defensive-security/           # Defense and detection examples
│   ├── intrusion-detection-setup.md
│   ├── log-analysis-incident.md
│   ├── incident-response-scenario.md
│   ├── honeypot-deployment.md
│   └── security-baseline-hardening.md
│
├── 05-application-security/         # Application security demonstrations
│   ├── xss-attack-defense.md
│   ├── csrf-vulnerability-demo.md
│   ├── authentication-bypass.md
│   ├── secure-api-design.md
│   └── secure-file-upload.md
│
├── 06-malware-analysis/             # Malware analysis walkthroughs
│   ├── static-analysis-walkthrough.md
│   ├── dynamic-analysis-sandbox.md
│   ├── ransomware-behavior-analysis.md
│   └── reverse-engineering-simple-binary.md
│
├── 07-specialized/                  # Specialized domain examples
│   ├── cloud-misconfiguration-exploit.md
│   ├── container-escape-demo.md
│   ├── social-engineering-scenario.md
│   └── physical-security-breach.md
│
└── 08-case-studies/                 # Real-world case studies
    ├── major-breaches/
    │   ├── equifax-2017.md
    │   ├── solarwinds-2020.md
    │   └── log4shell-2021.md
    ├── cve-analyses/
    │   └── [CVE-specific deep dives]
    └── red-team-operations/
        └── [Full red team engagement reports]
```

---

## Example Types

### 1. Attack Demonstrations

**Purpose:** Show how attacks work in practice
**Structure:** Setup → Reconnaissance → Exploitation → Post-exploitation → Analysis
**Focus:** Understanding attacker methodology and technique mechanics

**Typical sections:**

- Environment setup
- Attack prerequisites
- Step-by-step execution with commands
- Output analysis
- Indicators of compromise

### 2. Defense Implementations

**Purpose:** Show how defenses work in practice
**Structure:** Threat model → Defense design → Implementation → Validation → Analysis
**Focus:** Hardening, detection, and response mechanisms

**Typical sections:**

- Threat scenario
- Defense strategy
- Configuration/code implementation
- Testing and validation
- Limitations and trade-offs

### 3. Dual-Perspective Scenarios

**Purpose:** Show attack AND defense side-by-side
**Structure:** Scenario → Attack phase → Detection phase → Response phase → Analysis
**Focus:** Complete picture of offensive and defensive interplay

**Typical sections:**

- Scenario context
- Attacker actions (chronological)
- Defender observations (parallel timeline)
- Defense response
- Post-incident analysis

### 4. Case Studies

**Purpose:** Extract lessons from real-world incidents
**Structure:** Context → Timeline → Technical analysis → Impact → Lessons learned
**Focus:** Understanding real breaches, vulnerabilities, and responses

**Typical sections:**

- Incident background
- Attack chain reconstruction
- Technical vulnerability analysis
- Organizational/process failures
- Mitigation recommendations

### 5. Tool Demonstrations

**Purpose:** Show security tools in action
**Structure:** Tool overview → Use case → Setup → Demonstration → Analysis
**Focus:** Practical tool usage for offensive or defensive tasks

**Typical sections:**

- Tool capabilities
- Installation and configuration
- Practical usage scenarios
- Output interpretation
- Best practices and limitations

---

## How to Use Examples

### Active Learning Approach

Examples are designed for **active engagement**, not passive reading:

#### Phase 1: Preview (5 minutes)

1. Read the scenario and objective
2. Check prerequisites (theory, tools, environment)
3. Predict: What do you think will happen?
4. Note: What are you trying to learn?

#### Phase 2: Follow-Through (30-90 minutes)

1. **Read each step carefully**
2. **Try to predict the next step** before reading ahead
3. **Execute commands yourself** (in a safe lab environment)
4. **Compare outputs** — If yours differs, understand why
5. **Pause at decision points** — Why was this approach chosen?

#### Phase 3: Analysis (15-30 minutes)

1. Review the "Analysis" section
2. Answer the "Understanding Check" questions without looking back
3. Identify what worked and why
4. Identify failure points and defensive opportunities

#### Phase 4: Extension (30-60 minutes)

1. Try variations suggested in "Extensions"
2. Change one constraint — how does the attack/defense change?
3. Document what you learned in "Personal Notes"
4. Connect to related theory modules

#### Phase 5: Practice (ongoing)

1. Move to corresponding exercises in `03_exercises/`
2. Apply concepts without step-by-step guidance
3. Build your own scenarios
4. Document your process

---

## Example Structure

Every example follows a consistent structure optimized for learning:

### 1. Metadata & Overview

- **Domain, difficulty, prerequisites**
- **Time estimate** for working through the example
- **Learning objectives** — what you'll understand after completion
- **Theory connection** — links to `01_theory/` modules

### 2. Scenario Context

- **Realistic scenario** with clear actors and objectives
- **Environment description** with setup requirements
- **Scope and constraints** — what's in/out of scope
- **Success criteria** — what constitutes a successful outcome

### 3. Demonstration

- **Step-by-step walkthrough** with commands, code, or configurations
- **Annotated reasoning** at each step
- **Expected outputs** with interpretation
- **Branching points** where decisions matter
- **Both perspectives** (offensive + defensive) where applicable

### 4. Analysis

- **What worked and why**
- **What failed and why**
- **Key lessons** — transferable insights
- **Common mistakes** — what beginners typically get wrong
- **Defensive takeaways** — even from offensive examples

### 5. Extensions & Variations

- **Suggested variations** to deepen understanding
- **Advanced techniques** building on the basics
- **What-if scenarios** testing adaptability

### 6. Integration

- **Links to theory** — concepts demonstrated
- **Links to references** — authoritative sources, CVEs
- **Links to exercises** — practice opportunities
- **Links to tools** — resources used

---

## Quality Standards

Each example should:

### Technical Quality

- [ ] Technically accurate and verified
- [ ] Works in the described environment
- [ ] Commands/code produce stated outputs
- [ ] Reflects current best practices and techniques
- [ ] Includes both success and failure scenarios

### Pedagogical Quality

- [ ] Clear learning objectives stated upfront
- [ ] Prerequisites explicitly listed
- [ ] Step-by-step reasoning provided
- [ ] Common mistakes identified
- [ ] Understanding checks included
- [ ] Extensions for deeper learning provided

### Safety & Ethics

- [ ] Lab environment clearly specified
- [ ] Ethical boundaries stated
- [ ] Potential harm identified
- [ ] Legal considerations noted
- [ ] Responsible disclosure principles followed

### Integration

- [ ] Links to corresponding theory module
- [ ] Links to practice exercises
- [ ] Links to references and sources
- [ ] Links to tools used
- [ ] Both offensive and defensive perspectives (where applicable)

---

## Creating New Examples

### Step 1: Identify the Concept

Choose a theory module from `01_theory/` that needs practical demonstration.

### Step 2: Copy the Template

```bash
cp 02_examples/_example-template.md 02_examples/[domain]/[descriptive-name].md
```

**Example:**

```bash
cp 02_examples/_example-template.md 02_examples/03-offensive-security/sql-injection-attack.md
```

### Step 3: Set Up the Environment

**Document your lab setup:**

- Operating system and version
- Required software/tools
- Network topology (if applicable)
- Vulnerable application/system
- Safety constraints

**Ensure reproducibility** — someone following your example should be able to recreate your environment.

### Step 4: Execute and Document

1. **Perform the attack/defense** yourself first
2. **Document every step** with commands and outputs
3. **Explain your reasoning** at each decision point
4. **Capture screenshots** where visual context helps
5. **Note unexpected outcomes** and how you handled them

### Step 5: Add Analysis

**Extract lessons:**

- What made this attack successful?
- Where could detection occur?
- What defensive controls would break the attack chain?
- What are the key takeaways?

### Step 6: Create Variations

**Suggest extensions:**

- Change one variable — how does it affect the outcome?
- Advanced techniques building on this foundation
- Alternative approaches to the same objective

### Step 7: Link Integration

**Connect to workspace:**

- Link to theory module(s) this demonstrates
- Link to exercises for hands-on practice
- Link to references, CVEs, or standards
- Link to tools used

### Step 8: Test Reproducibility

**Have someone else follow your example:**

- Can they set up the environment?
- Do they get the same results?
- Is the reasoning clear?
- Are there gaps in explanation?

---

## Safety Guidelines

### Lab Environment Requirements

**NEVER run offensive examples on:**

- Production systems
- Systems you don't own
- Networks you're not authorized to test
- Systems without explicit permission

**ALWAYS use isolated labs:**

- Virtual machines
- Separate lab network
- Snapshots before testing
- Network isolation from production

### Ethical Boundaries

Every offensive example must:

- State its educational purpose
- Specify legal constraints
- Include defensive countermeasures
- Emphasize responsible disclosure
- Link to ethical hacking principles

### Documentation Standards

- Document the lab environment clearly
- State assumptions about permissions
- Warn about potentially harmful techniques
- Provide cleanup instructions
- Include defensive analysis

---

## Example Naming Conventions

### Format

`[concept]-[perspective].md`

**Patterns:**

- `sql-injection-attack.md` — Offensive demonstration
- `intrusion-detection-setup.md` — Defensive implementation
- `xss-attack-defense.md` — Dual perspective
- `equifax-breach-analysis.md` — Case study
- `buffer-overflow-exploitation.md` — Technique demonstration

### Domain Prefixes (Optional)

When examples span multiple domains, use descriptive names:

- `web-sql-injection-attack.md`
- `linux-privilege-escalation.md`
- `cloud-misconfiguration-exploit.md`

---

## Example Roadmap

Examples to prioritize based on theory coverage:

### High Priority (Foundational)

- [ ] CIA triad demonstration
- [ ] Threat modeling walkthrough
- [ ] Basic cryptographic implementations
- [ ] Common OWASP Top 10 examples
- [ ] Network reconnaissance basics

### Medium Priority (Core Techniques)

- [ ] Privilege escalation scenarios
- [ ] Incident response walkthroughs
- [ ] Malware analysis basics
- [ ] Secure coding examples
- [ ] Defense-in-depth implementations

### Advanced (Specialization)

- [ ] Advanced exploitation techniques
- [ ] Red team operation reports
- [ ] Cloud security scenarios
- [ ] Mobile application security
- [ ] Zero-day analysis

---

## Integration with Workspace

Examples connect the workspace sections:

| Directory          | Connection                                  |
| ------------------ | ------------------------------------------- |
| **01_theory/**     | Examples demonstrate concepts from theory   |
| **03_exercises/**  | Exercises test skills learned from examples |
| **04_resources/**  | Examples use tools cataloged in resources   |
| **05_references/** | Examples cite authoritative sources         |

### Linking Convention

```markdown
**Theory:** [SQL Injection Theory](../../01_theory/05-application-security/sql-injection.md)

**Exercises:** [SQL Injection Practice](../../03_exercises/05-application-security/sql-injection-beginner.md)

**Tools:** [Burp Suite](../../04_resources/tools/burp-suite.md)

**References:** [OWASP Top 10](../../05_references/standards/OWASP/owasp-top-10-2021.md)
```

---

## Contribution Guidelines

When contributing examples:

1. **Verify legality and ethics** — ensure all actions are authorized
2. **Test in isolated lab** — never use production systems
3. **Document environment** — enable reproducibility
4. **Follow template** — use `_example-template.md`
5. **Include defensive perspective** — even for offensive examples
6. **Link to theory and exercises** — maintain integration
7. **Peer review** — have someone test your example

---

## Questions or Improvements

Found an issue with an example? Document it in the example's "Personal Notes" section or open an issue with:

- Which example
- What didn't work
- Your environment details
- Steps to reproduce

Remember: **Examples are living documents.** Update them as tools, techniques, and defenses evolve.
