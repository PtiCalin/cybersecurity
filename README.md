# Cybersecurity Knowledge Hub

**Owner:** PtiCalin (Charlie)
**Purpose:** Centralized cybersecurity learning workspace and personal knowledge base

---

## Overview

This repository serves as a comprehensive, structured environment for mastering cybersecurity—from foundational theory to advanced offensive and defensive techniques. It is designed as a living knowledge base that evolves with learning progression, academic coursework, and hands-on practice.

### Learning Objectives

- Master core cybersecurity concepts: threat modeling, attack vectors, defense strategies
- Develop practical skills in offensive security (ethical hacking, penetration testing)
- Build defensive security competence (incident response, hardening, monitoring)
- Understand cryptography, network security, and application security principles
- Document techniques with both offensive mechanisms and defensive countermeasures
- Maintain an annotated catalog of tools, papers, CVEs, and industry resources
- Support academic coursework with structured, citable references

### Design Principles

| Principle                         | Implementation                                                        |
| --------------------------------- | --------------------------------------------------------------------- |
| **Progressive disclosure**        | Content organized by learning complexity, not just topic              |
| **Offensive ↔ Defensive balance** | Every attack technique paired with mitigation strategies              |
| **Academic rigor**                | Citations, references, and sources tracked in ATTRIBUTIONS.md         |
| **Hands-on learning**             | Theory complemented by worked examples and exercises                  |
| **Extensibility**                 | Structure supports future labs, CTF writeups, and interactive content |
| **Knowledge retention**           | Spaced repetition markers, cross-references, and review checkpoints   |

---

## Repository Structure

```text
cybersecurity/
├── 01_theory/              # Core concepts, methodologies, frameworks
│   ├── threat-modeling/
│   ├── network-security/
│   ├── cryptography/
│   ├── offensive-security/
│   ├── defensive-security/
│   ├── application-security/
│   └── ...
├── 02_examples/            # Attack scenarios, defense implementations
│   ├── case-studies/
│   ├── exploit-analysis/
│   ├── mitigation-demos/
│   └── ...
├── 03_exercises/           # Practice problems, CTF challenges, labs
│   ├── beginner/
│   ├── intermediate/
│   ├── advanced/
│   └── ...
├── 04_resources/           # Curated resources with commentary
│   ├── engines/            # Search engines, OSINT tools
│   ├── tools/              # Security tool catalog
│   ├── papers/             # Academic papers
│   └── ...
├── 05_references/          # Standards, CVE databases, frameworks
│   ├── OWASP/
│   ├── NIST/
│   ├── CVE/
│   └── ...
├── README.md               # This file
├── ATTRIBUTIONS.md         # Workspace development attribution
├── AUTHORS.md              # Contributor information
├── LICENSE                 # MIT License (educational use)
├── CHANGE-LOG.md           # Evolution and version history
└── .claude/
    ├── CLAUDE.md           # AI assistance context
    └── rules/              # Coding standards and workflows
```

---

## Quick Start

### For Learning

1. **Start with theory** → Navigate to `01_theory/` and select a domain
2. **Study examples** → Review corresponding attack/defense scenarios in `02_examples/`
3. **Practice** → Work through exercises in `03_exercises/`
4. **Deep dive** → Explore academic papers and tool documentation in `04_resources/` and `05_references/`
5. **Document insights** → Add personal notes and commentary directly in files

### For Contributing Content

1. Create a working branch from `main`
2. Add content to the appropriate directory:
   - Theory explanations → `01_theory/`
   - Worked examples → `02_examples/`
   - Practice problems → `03_exercises/`
   - Resource links → `04_resources/`
   - Reference materials → `05_references/`
3. Document sources within the resource/reference files themselves
4. Update `ATTRIBUTIONS.md` only if you're contributing to workspace development
5. Update `CHANGE-LOG.md` with the change
6. Open a Pull Request

---

## Domain Coverage

Primary cybersecurity domains organized in this knowledge base:

### Offensive Security

- Reconnaissance and OSINT
- Vulnerability assessment
- Exploitation techniques
- Post-exploitation and persistence
- Social engineering
- Wireless security

### Defensive Security

- Threat detection and monitoring
- Incident response
- System hardening
- Security architecture
- Forensics and analysis

### Foundational Topics

- Threat modeling and risk assessment
- Network protocols and security
- Cryptography and applied security
- Application security (OWASP Top 10)
- Mobile security (Android/iOS)
- Cloud security

### Tools and Automation

- Security tooling catalog
- Automation frameworks
- Lab environment setup
- Custom scripts and utilities

---

## Quality Standards

### Content Requirements

- **Accuracy:** All technical content verified against authoritative sources
- **Source tracking:** Security tools, papers, and CVEs documented in `04_resources/` and `05_references/`
- **Workspace attribution:** Development contributions tracked in ATTRIBUTIONS.md
- **Balance:** Offensive techniques paired with defensive countermeasures
- **Clarity:** Concepts explained at multiple abstraction levels (L1 intuition → L2 formal → L3 example → L4 edge cases)
- **Reproducibility:** Examples and exercises include enough detail for independent reproduction

### Ethical Guidelines

- All offensive security content is for **educational purposes only**
- Techniques documented within **legal and ethical boundaries**
- Every attack vector includes corresponding **defensive mitigations**
- No operational exploit code targeting production systems
- Disclosure and responsible security practices emphasized

---

## Key Files

| File                                               | Purpose                                               |
| -------------------------------------------------- | ----------------------------------------------------- |
| [README.md](README.md)                             | Project overview and navigation (this file)           |
| [ATTRIBUTIONS.md](ATTRIBUTIONS.md)                 | Workspace development contributions and AI disclosure |
| [AUTHORS.md](AUTHORS.md)                           | Contributors and maintainers                          |
| [CHANGE-LOG.md](.github/versionning/CHANGE-LOG.md) | Version history and evolution log                     |
| [.claude/CLAUDE.md](.claude/CLAUDE.md)             | AI assistance context and rules                       |
| [LICENSE](LICENSE)                                 | MIT License with educational use notice               |
| [04_resources/](04_resources/)                     | Curated cybersecurity tools, papers, and links        |
| [05_references/](05_references/)                   | Standards, CVEs, frameworks (OWASP, NIST, etc.)       |

---

## Academic Context

This repository supports coursework at **Université de Montréal** and ongoing personal research in cybersecurity. Content is structured to meet university-level academic standards while remaining accessible for progressive learning.

### Citation

When referencing material from this repository in academic work:

```
Calin, Charlie (PtiCalin). (2026). Cybersecurity Knowledge Hub [Personal knowledge base].
GitHub. https://github.com/PtiCalin/cybersecurity
```

---

## Contact

**Maintainer:** PtiCalin (Charlie)
**Institution:** Université de Montréal
**Repository:** [github.com/PtiCalin/cybersecurity](https://github.com/PtiCalin/cybersecurity)

## Latest Changes

<!-- LATEST-CHANGES:START -->

### Snapshot from Changelog

_Last sync: 2026-04-19 17:49:28 UTC_

## [Unreleased]

### Added

### Changed

### Deprecated

### Removed

### Fixed

### Security

<!-- LATEST-CHANGES:END -->
