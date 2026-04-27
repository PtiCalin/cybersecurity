# References

This directory contains annotated notes on cybersecurity references including academic papers, standards, frameworks, CVEs, and authoritative documentation.

---

## Quick Access

- **[Textbook Catalog](textbooks/TEXTBOOKS.md)** — Curated list with learning paths, difficulty ratings, and reading strategies
- **[Reference Review Guidelines](00_reference-review_guidelines/)** — Standards for reviewing and validating references
- **[Quick Guide](QUICK-GUIDE.md)** — Fast reference for efficient note-taking (if exists)
- **[Example Notes](standards/OWASP/)** — See template in action

---

## Purpose

Each reference note serves as:

- **Knowledge extraction**: Distilled key concepts and insights
- **Learning aid**: Structured summaries optimized for retention
- **Quick reference**: Fast lookup for concepts and quotes
- **Connection hub**: Links to related theory, examples, and exercises
- **Review system**: Spaced repetition schedule for long-term retention

---

## Organization Structure

```
05_references/
├── REFERENCES.md                # This file
├── 00_reference-review_guidelines/  # Reference validation standards
├── literature/                  # PDF collection (books, papers)
├── textbooks/                   # Textbook catalog and learning paths
│   └── TEXTBOOKS.md
├── standards/                   # Security standards and frameworks
│   ├── OWASP/
│   ├── NIST/
│   ├── ISO/
│   └── CIS/
├── CVE/                         # Vulnerability notes
│   ├── by-year/
│   └── by-category/
├── papers/                      # Academic paper notes (companion to literature/)
│   ├── offensive/
│   ├── defensive/
│   └── foundational/
├── frameworks/                  # Security frameworks
│   ├── MITRE-ATT&CK/
│   ├── Kill-Chain/
│   └── Diamond-Model/
└── documentation/               # Technical documentation
    ├── protocols/
    ├── tools/
    └── platforms/
```

**Note:** The `literature/` folder contains actual PDF files. The `textbooks/` folder contains the catalog with learning paths and reading recommendations. Create corresponding notes in `papers/` using the reference template.

---

## How to Create a New Reference Note

### Step 1: Copy the Template

```bash
# From the repository root
cp 05_references/_reference-note-template.md 05_references/[category]/[descriptive-name].md
```

**Example:**

```bash
cp 05_references/_reference-note-template.md 05_references/standards/OWASP/owasp-top-10-2021.md
```

### Step 2: Fill Out Metadata

Start with the metadata table at the top:

- Classification (type, difficulty, relevance)
- Citation information
- Tags for searchability

### Step 3: Write as You Read

The template is designed for **active reading**:

1. Write the executive summary first (forces you to understand the big picture)
2. Extract key concepts section by section
3. Note important quotes with context
4. Add personal reflections and questions
5. Identify practical applications

### Step 4: Link and Cross-Reference

Connect to related content:

- Theory files in `01_theory/`
- Examples in `02_examples/`
- Exercises in `03_exercises/`
- Tools in `04_resources/`
- Other references

### Step 5: Schedule Reviews

Set review dates using spaced repetition:

- 1 day after first read
- 1 week later
- 1 month later
- 3 months later

---

## Naming Conventions

### Standards and Frameworks

Format: `[org]-[name]-[version].md`

Examples:

- `owasp-top-10-2021.md`
- `nist-csf-v1.1.md`
- `mitre-attack-v14.md`
- `cis-controls-v8.md`

### CVE References

Format: `cve-[year]-[number].md`

Examples:

- `cve-2024-12345.md`
- `cve-2023-67890.md`

### Academic Papers

Format: `[first-author-lastname]-[year]-[short-title].md`

Examples:

- `anderson-2001-security-engineering.md`
- `schneier-1996-applied-cryptography.md`
- `stallings-2017-cryptography-network-security.md`

### Framework Documentation

Format: `[framework-name]-[topic].md`

Examples:

- `mitre-attack-initial-access.md`
- `kill-chain-reconnaissance-phase.md`
- `diamond-model-adversary-analysis.md`

---

## Reference Categories

### Textbooks (textbooks/)

Comprehensive learning resources with structured curricula:

- **See [TEXTBOOKS.md](textbooks/TEXTBOOKS.md)** for full catalog
- Organized by domain (offensive, defensive, network, application security)
- Includes learning paths for progressive skill development
- Difficulty ratings and time estimates
- Reading strategies and progress tracking

### Standards (standards/)

Security industry standards and best practices:

- **OWASP** — Web application security (Top 10, ASVS, SAMM)
- **NIST** — Cybersecurity frameworks (CSF, SP 800 series)
- **ISO** — Information security management (27001, 27002)
- **CIS** — Security controls and benchmarks
- **PCI DSS** — Payment card industry standards

### CVEs (CVE/)

Vulnerability documentation:

- Organize by year: `CVE/by-year/2024/`
- Organize by category: `CVE/by-category/injection/`, `CVE/by-category/authentication/`
- Include CVSS scoring, affected systems, exploits, and patches

### Papers (papers/)

Academic research:

- **Offensive** — Exploitation techniques, attack methodologies
- **Defensive** — Detection, response, hardening strategies
- **Foundational** — Core security concepts, cryptography, theory

### Frameworks (frameworks/)

Attack and defense frameworks:

- **MITRE ATT&CK** — Adversary tactics and techniques
- **Cyber Kill Chain** — Attack lifecycle stages
- **Diamond Model** — Intrusion analysis
- **Pyramid of Pain** — Defensive indicator effectiveness

### Documentation (documentation/)

Technical documentation and protocol specs:

- **Protocols** — TCP/IP, TLS, HTTP, DNS, etc.
- **Tools** — Security tool documentation
- **Platforms** — Operating systems, cloud platforms

---

## Tagging System

Use consistent tags for searchability:

### Domain Tags

`#offensive` `#defensive` `#cryptography` `#network-security` `#web-security` `#mobile-security` `#cloud-security`

### Technique Tags

`#reconnaissance` `#exploitation` `#privilege-escalation` `#persistence` `#lateral-movement` `#exfiltration` `#detection` `#response` `#hardening`

### Difficulty Tags

`#beginner` `#intermediate` `#advanced` `#expert`

### Reference Type Tags

`#paper` `#standard` `#framework` `#cve` `#documentation` `#book`

---

## Active Reading Workflow

### Phase 1: Pre-Reading (5 minutes)

1. Skim the abstract/introduction
2. Read section headings
3. Check figures and tables
4. Fill out metadata section

### Phase 2: First Pass (60-90 minutes)

1. Read through completely
2. Extract key concepts as you go
3. Note important quotes
4. Flag sections for deeper study

### Phase 3: Deep Processing (30-60 minutes)

1. Write executive summary in your own words
2. Fill critical analysis section
3. Add personal insights and questions
4. Create connections to other knowledge
5. Identify practical applications

### Phase 4: Consolidation (15 minutes)

1. Review what you wrote
2. Add cross-references
3. Set spaced repetition schedule
4. Tag appropriately

---

## Quality Standards

Each reference note should:

- [ ] Have complete metadata for citation
- [ ] Include an executive summary
- [ ] Extract key concepts with clear explanations
- [ ] Provide personal analysis, not just copying
- [ ] Link to related workspace content
- [ ] Include practical applications
- [ ] Set up spaced repetition schedule
- [ ] Use consistent terminology

---

## Review Process

### Weekly Review

Check notes scheduled for review this week:

```bash
# Search for review markers
grep -r "REVIEW: $(date +%Y-%m-%d)" 05_references/
```

### Monthly Maintenance

- Update outdated information
- Add new connections discovered
- Refine summaries based on deeper understanding
- Check for broken links

---

## Tips for Effective Notes

### Do

✅ Write in your own words (Feynman technique)
✅ Focus on understanding, not copying
✅ Connect concepts across references
✅ Note what you don't understand
✅ Add practical examples
✅ Include both offensive and defensive perspectives
✅ Update notes as understanding deepens

### Don't

❌ Copy-paste large blocks without processing
❌ Skip the critical analysis section
❌ Forget to set review dates
❌ Leave metadata incomplete
❌ Ignore cross-referencing opportunities
❌ Create notes without reading the source

---

## Integration with Workspace

Reference notes feed into:

| Directory         | How References Connect                                       |
| ----------------- | ------------------------------------------------------------ |
| **01_theory/**    | References provide the foundation for theory explanations    |
| **02_examples/**  | Examples cite and demonstrate concepts from references       |
| **03_exercises/** | Exercises test understanding of referenced material          |
| **04_resources/** | Resources point to tools and sources mentioned in references |

Keep this flow in mind when creating notes.

---

## Examples

See these example reference notes:

- [OWASP Top 10 2021](standards/OWASP/owasp-top-10-2021-EXAMPLE.md) — Demonstrates full template usage with a security standard
- [Coming soon: CVE analysis example]
- [Coming soon: Academic paper example]

---

## Questions or Improvements

Found ways to improve the template or process? Update this README or open an issue.
