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
  - Created domain directory structure in `01_theory/` with README files for navigation
  - Populated `00-foundations/` with two comprehensive theory modules:
    - `cia-triad.md`: Confidentialité, Intégrité, Disponibilité — foundational security properties with French terminology integration
    - `risk-analysis.md`: Complete risk assessment framework covering actifs, menaces, vulnérabilités, probabilité, impact, risk treatment strategies, and methodologies (EBIOS, MEHARI, OCTAVE, Risk IT, ISO 27005)
  - Populated `02-network-security/` with comprehensive network attack module:
    - `dos-ddos-attacks.md`: Denial of service techniques including SYN floods, amplification attacks, reflection, ping of death, with defensive countermeasures
  - Populated `03-offensive-security/` with complete attack methodology module:
    - `attack-lifecycle.md`: Eight-phase attack chain from reconnaissance to cleanup with worked web server compromise example, persistence mechanisms, and APT considerations
  - All modules follow four-layer pedagogical model (Intuition → Formal → Worked Examples → Edge Cases)
  - Integrated French terminology from IFT2830 course materials throughout (bilingual support)
  - Added real-world incident examples (WannaCry, Equifax, Stuxnet, Mirai, SolarWinds)
  - Included 10 active recall prompts per module (understanding, application, transfer questions)
  - Linked modules to IFT2830 course materials in `05_references/course-materials/`
  - Each module includes spaced repetition schedule, personal notes section, and change log

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
