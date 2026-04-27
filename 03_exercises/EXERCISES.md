# Exercises

This directory contains hands-on practice problems, challenges, and labs designed to test and reinforce cybersecurity knowledge through active application.

---

## Quick Access

- **[Exercise Template](_exercise-template.md)** — Standardized structure for all exercises
- **[By Domain](#domain-organization)** — Navigate by security domain
- **[By Difficulty](#difficulty-levels)** — Browse by skill level
- **[Progress Tracking](#tracking-progress)** — Monitor your learning journey

---

## Purpose

Exercises transform theoretical knowledge and demonstrated examples into practical skills through deliberate practice. Each exercise provides:

1. **Hands-on challenges** requiring application of concepts from `01_theory/` and `02_examples/`
2. **Progressive difficulty** from guided practice to open-ended challenges
3. **Immediate feedback** through solution validation
4. **Skill assessment** identifying gaps in understanding
5. **Real-world scenarios** mimicking actual security work
6. **Both offensive and defensive practice** maintaining balance

Exercises are where **learning becomes competence**. Theory explains, examples demonstrate, exercises build mastery.

---

## Domain Organization

```
03_exercises/
├── EXERCISES.md                     # This file
├── _exercise-template.md            # Template for new exercises
│
├── 00-foundations/                  # Foundational skills
│   ├── threat-modeling-lab.md
│   ├── cia-triad-scenarios.md
│   └── security-principles-quiz.md
│
├── 01-cryptography/                 # Cryptographic practice
│   ├── symmetric-encryption-challenge.md
│   ├── hash-function-lab.md
│   ├── rsa-implementation.md
│   └── crypto-ctf-challenges.md
│
├── 02-network-security/             # Network security practice
│   ├── packet-analysis-lab.md
│   ├── network-scanning-exercise.md
│   ├── firewall-configuration-lab.md
│   └── protocol-exploitation.md
│
├── 03-offensive-security/           # Penetration testing practice
│   ├── reconnaissance-challenge.md
│   ├── sql-injection-beginner.md
│   ├── sql-injection-advanced.md
│   ├── privilege-escalation-lab.md
│   ├── buffer-overflow-practice.md
│   └── ctf-challenges/
│       ├── beginner/
│       ├── intermediate/
│       └── advanced/
│
├── 04-defensive-security/           # Defense and detection practice
│   ├── log-analysis-challenge.md
│   ├── incident-response-scenario.md
│   ├── security-hardening-lab.md
│   ├── threat-hunting-exercise.md
│   └── blue-team-scenarios/
│
├── 05-application-security/         # Application security practice
│   ├── xss-exploitation-lab.md
│   ├── secure-coding-challenge.md
│   ├── api-security-testing.md
│   └── code-review-exercises.md
│
├── 06-malware-analysis/             # Malware analysis practice
│   ├── static-analysis-challenge.md
│   ├── dynamic-analysis-lab.md
│   ├── reverse-engineering-crackme.md
│   └── behavioral-analysis.md
│
├── 07-specialized/                  # Specialized domain practice
│   ├── cloud-security-lab.md
│   ├── container-security-challenge.md
│   └── social-engineering-simulation.md
│
└── 08-ctf-practice/                 # Capture-the-flag challenges
    ├── jeopardy-style/
    │   ├── crypto/
    │   ├── web/
    │   ├── binary/
    │   ├── forensics/
    │   └── misc/
    └── attack-defense/
```

---

## Difficulty Levels

### 🟢 Beginner

**Characteristics:**

- Clear objectives and constraints
- Step-by-step guidance available
- Single concept focus
- Limited scope
- Validation checks at each stage

**Prerequisites:**

- Basic understanding of the concept from theory
- Reviewed corresponding example
- Fundamental tool familiarity

**Time:** 30 minutes - 1 hour

---

### 🟡 Intermediate

**Characteristics:**

- Multiple concept integration
- Less explicit guidance
- Requires problem-solving and adaptation
- Moderate scope
- Real-world-like constraints

**Prerequisites:**

- Completed beginner exercises in domain
- Strong understanding of theory
- Comfortable with relevant tools
- Can troubleshoot independently

**Time:** 1-2 hours

---

### 🟠 Advanced

**Characteristics:**

- Open-ended challenges
- Minimal guidance
- Multiple solution paths
- Complex scenarios with interconnected systems
- Requires research and creativity

**Prerequisites:**

- Completed intermediate exercises
- Deep theoretical knowledge
- Expert tool usage
- Strong troubleshooting skills

**Time:** 2-4 hours

---

### 🔴 Expert

**Characteristics:**

- Real-world complexity
- No guidance provided
- Multi-stage challenges
- Unknown vulnerabilities or techniques
- Requires advanced research and tool development

**Prerequisites:**

- Mastery of domain fundamentals
- Completed advanced exercises
- Ability to discover novel techniques
- Professional-level expertise

**Time:** 4+ hours or multi-day

---

## Exercise Types

### 1. Guided Labs

**Purpose:** Build foundational skills with structured guidance
**Structure:** Step-by-step instructions with checkpoints
**Validation:** Expected outcomes at each step

**When to use:**

- Learning a new tool or technique
- Reinforcing concepts from examples
- Building confidence before independent work

---

### 2. Challenge Problems

**Purpose:** Test understanding and problem-solving
**Structure:** Objective + constraints, no step-by-step
**Validation:** Success criteria defined, path is open

**When to use:**

- After completing guided labs
- Testing concept mastery
- Preparing for CTF competitions

---

### 3. Scenario-Based Exercises

**Purpose:** Simulate real-world security work
**Structure:** Realistic context with multiple objectives
**Validation:** Mission success criteria

**When to use:**

- Integration of multiple skills
- Practicing decision-making
- Career preparation

---

### 4. Code Review Exercises

**Purpose:** Develop secure code analysis skills
**Structure:** Vulnerable code + find/fix mission
**Validation:** All vulnerabilities identified and patched

**When to use:**

- Application security practice
- Defensive skill development
- Secure coding mastery

---

### 5. CTF Challenges

**Purpose:** Competitive skill testing
**Structure:** Flag-based objectives, minimal context
**Validation:** Capture the flag

**When to use:**

- Skill assessment
- Competition preparation
- Rapid problem-solving practice

---

## How to Use Exercises

### Learning Workflow

```
Theory → Examples → Exercises → Mastery
   ↑                              ↓
   └──────── Feedback loop ───────┘
```

### Progression Path

1. **Read theory** in `01_theory/` — Understand concepts
2. **Study example** in `02_examples/` — See concepts applied
3. **Attempt exercise** (beginner) — Apply without guidance
4. **Compare to solution** — Identify gaps
5. **Reattempt or advance** — Build confidence
6. **Progress to next difficulty** — Deepen mastery

### Active Practice Principles

#### Before Starting

- [ ] Review relevant theory module
- [ ] Work through corresponding example
- [ ] Ensure lab environment is ready
- [ ] Set a time limit (avoid endless attempts)
- [ ] Define success criteria

#### During the Exercise

- [ ] Read the full challenge before starting
- [ ] Document your approach and reasoning
- [ ] Try multiple methods if stuck
- [ ] Time-box problem-solving attempts (20-30 min)
- [ ] Take notes on what you learn

#### After Completion

- [ ] Review the solution (if provided)
- [ ] Identify what you did well
- [ ] Identify knowledge gaps
- [ ] Document lessons learned
- [ ] Revisit theory if needed
- [ ] Mark for spaced review

---

## Quality Standards

Each exercise should:

### Design Quality

- [ ] Clear learning objectives stated
- [ ] Appropriate difficulty level
- [ ] Realistic scenario or context
- [ ] Well-defined success criteria
- [ ] Reproducible environment
- [ ] Ethical boundaries clear

### Pedagogical Quality

- [ ] Builds on stated prerequisites
- [ ] Tests specific skills or concepts
- [ ] Provides appropriate level of guidance
- [ ] Includes hints without giving away solution
- [ ] Solution explains reasoning, not just steps
- [ ] Encourages multiple solution approaches

### Technical Quality

- [ ] Technically accurate and verified
- [ ] Works in described environment
- [ ] Fair difficulty (no guess-work required)
- [ ] Solution is achievable with documented tools
- [ ] Flags or success indicators are clear

---

## Creating New Exercises

### Step 1: Identify Learning Objective

**Ask:**

- What specific skill does this test?
- What theory concept does this reinforce?
- What example does this build upon?

### Step 2: Choose Difficulty

**Beginner:** Single concept, clear guidance
**Intermediate:** Multiple concepts, moderate guidance
**Advanced:** Open-ended, minimal guidance
**Expert:** Real-world complexity, no guidance

### Step 3: Design the Challenge

**Components:**

- Scenario and context
- Environment requirements
- Objective (what success looks like)
- Constraints (rules, limitations)
- Hints (progressive difficulty)

### Step 4: Build and Test

1. Create the lab environment
2. Solve the challenge yourself
3. Document the solution path(s)
4. Identify common mistakes
5. Add progressive hints
6. Have others test it

### Step 5: Create Solution

**Solution should include:**

- Multiple solution approaches
- Detailed reasoning at each step
- Common pitfalls explained
- Alternative methods discussed
- Key lessons highlighted

### Step 6: Link Integration

- Link to theory module
- Link to corresponding example
- Link to tools used
- Link to references and standards

---

## Tracking Progress

### Personal Progress Log

Create a progress tracking file:

```markdown
# My Cybersecurity Exercise Progress

## Foundations

- [x] Threat Modeling Lab — Completed 2026-04-15
- [ ] CIA Triad Scenarios
- [ ] Security Principles Quiz

## Cryptography

- [x] Symmetric Encryption Challenge — Completed 2026-04-20
- [x] Hash Function Lab — Completed 2026-04-22
- [ ] RSA Implementation

## Statistics

- Total exercises completed: 3
- Current focus: Cryptography
- Next target: RSA Implementation
```

### Skill Assessment

After each exercise, rate yourself:

| Skill Area              | Before | After |
| ----------------------- | ------ | ----- |
| [Concept understanding] | 3/5    | 4/5   |
| [Tool proficiency]      | 2/5    | 4/5   |
| [Problem-solving speed] | 3/5    | 4/5   |

### Review Schedule

Mark exercises for periodic review:

- [ ] 1 week: Re-attempt without notes
- [ ] 1 month: Solve a variant
- [ ] 3 months: Solve advanced version

---

## Hints System

Exercises use a progressive hint system:

**Hint 1 (Conceptual):** Points to the theory concept
**Hint 2 (Directional):** Suggests the approach
**Hint 3 (Technical):** Names the tool or technique
**Hint 4 (Detailed):** Provides specific command structure

**Use hints strategically:**

- Try for 20-30 minutes before first hint
- Wait 10-15 minutes between hints
- Document what you learned from each hint

---

## Solutions

### When to Check Solutions

**❌ Don't look at solutions when:**

- You haven't seriously attempted the challenge
- You're stuck but haven't asked for help
- You're taking the easy way out

**✅ Do look at solutions when:**

- You've exhausted all approaches for 1-2 hours
- You've used all hints and still stuck
- You've completed it and want to compare methods
- You want to learn alternative approaches

### How to Use Solutions

1. **Compare approaches:** How does your method differ?
2. **Understand reasoning:** Why did the solution take this path?
3. **Learn alternatives:** What other methods exist?
4. **Identify gaps:** What knowledge did you lack?
5. **Retry later:** Attempt again in 1 week without solution

---

## Integration with Workspace

Exercises connect all workspace sections:

| Directory          | Connection                               |
| ------------------ | ---------------------------------------- |
| **01_theory/**     | Exercises test concepts from theory      |
| **02_examples/**   | Exercises build on demonstrated examples |
| **04_resources/**  | Exercises use tools from resources       |
| **05_references/** | Exercises cite standards and CVEs        |

### Linking Convention

```markdown
**Theory:** [SQL Injection](../../01_theory/05-application-security/sql-injection.md)

**Example:** [SQL Injection Demo](../../02_examples/05-application-security/sql-injection-attack.md)

**Tools:** [sqlmap](../../04_resources/tools/sqlmap.md), [Burp Suite](../../04_resources/tools/burp-suite.md)

**References:** [OWASP Top 10](../../05_references/standards/OWASP/owasp-top-10-2021.md)
```

---

## CTF and Competition Prep

### Competition Types

**Jeopardy-Style:**

- Multiple independent challenges
- Points per challenge
- No interaction between teams
- Common categories: web, crypto, binary, forensics, misc

**Attack-Defense:**

- Each team defends their services
- Each team attacks other teams
- Points for defense uptime + successful attacks
- Requires both offensive and defensive skills

**King of the Hill:**

- Single target system
- Teams compete for persistent access
- Points for maintaining control
- Defensive hardening required

### Training Progression

**Phase 1: Fundamentals** (3-6 months)

- Complete all beginner exercises
- Focus on one category at a time
- Build tool proficiency

**Phase 2: Integration** (3-6 months)

- Complete intermediate exercises
- Practice cross-category challenges
- Develop speed and efficiency

**Phase 3: Competition** (ongoing)

- Complete advanced exercises
- Participate in live CTFs
- Practice under time pressure

**Phase 4: Mastery** (ongoing)

- Attempt expert challenges
- Create your own challenges
- Mentor beginners

---

## Safety Guidelines

### Lab Environment

**ALWAYS use isolated environments:**

- Virtual machines with snapshots
- Separate lab network
- No connection to production
- Clearly labeled as lab systems

**NEVER practice on:**

- Production systems
- Systems you don't own
- Public internet without authorization
- Anything without explicit permission

### Legal and Ethical

**Before attempting any exercise:**

- Ensure you own or have permission for target systems
- Understand legal implications
- Follow responsible disclosure principles
- Document authorization

**For realistic practice:**

- Use purpose-built vulnerable environments (DVWA, WebGoat, HackTheBox, TryHackMe)
- Build your own lab infrastructure
- Participate in authorized CTF competitions
- Follow ethical hacking certifications (CEH, OSCP)

---

## Resources for Practice

### Vulnerable Environments

- **DVWA** (Damn Vulnerable Web Application)
- **WebGoat** (OWASP)
- **Metasploitable** (Vulnerable Linux VM)
- **VulnHub** (Vulnerable VM collection)
- **OWASP Juice Shop**

### Online Platforms

- **HackTheBox** — Realistic penetration testing lab
- **TryHackMe** — Guided cybersecurity training
- **PentesterLab** — Web application security
- **OverTheWire** — Wargames for learning security concepts
- **Pwnable.kr** — Binary exploitation challenges

### CTF Platforms

- **CTFtime** — CTF event calendar and team rankings
- **PicoCTF** — Beginner-friendly CTF
- **CTF Challenge** — Practice CTF challenges

---

## Contribution Guidelines

When creating exercises:

1. **Test thoroughly** — Solve it yourself multiple times
2. **Peer review** — Have others attempt it
3. **Document clearly** — Success criteria must be unambiguous
4. **Provide solutions** — Include detailed solution with reasoning
5. **Link integration** — Connect to theory, examples, tools, references
6. **Ethical boundaries** — Clear lab environment requirements
7. **Progressive hints** — Help without giving away answers

---

## Questions or Improvements

Found an issue with an exercise? Document it in the exercise file under "Personal Notes" or report:

- Exercise name and difficulty
- What didn't work
- Your environment details
- Expected vs actual behavior

Remember: **Exercises are living documents.** Update them as tools, techniques, and knowledge evolve.
