# Reference Note Quick Guide

Fast reference for creating effective notes from cybersecurity sources.

---

## Minimum Viable Note

If time is limited, complete these sections first:

1. **Metadata** — Citation information for later use
2. **Executive Summary** — One-sentence + key contribution + why it matters
3. **Key Concepts** (top 3) — Core ideas with definitions
4. **Personal Insights** — What you learned, questions raised
5. **Review Schedule** — Set first review date

You can expand later during review sessions.

---

## Active Reading Checklist

While reading, ask yourself:

### Understanding Layer
- [ ] Can I explain this concept to someone else?
- [ ] What problem does this solve?
- [ ] What are the prerequisites I needed to understand this?

### Critical Layer
- [ ] What assumptions does the author make?
- [ ] What evidence supports the claims?
- [ ] What are the limitations or edge cases?
- [ ] Do I agree with the conclusions?

### Application Layer
- [ ] How can I use this in practice?
- [ ] What examples demonstrate this concept?
- [ ] What tools implement this?
- [ ] How does this connect to what I already know?

### Security Layer (Offensive ↔ Defensive)
- [ ] If this describes an attack, what's the defense?
- [ ] If this describes a defense, what attacks does it prevent?
- [ ] What are the limitations of this technique?
- [ ] What are the detection/evasion strategies?

---

## Section Priority Guide

### Must Complete
- Metadata (for citation)
- Executive Summary (for understanding)
- Key Concepts (core knowledge)
- Review Schedule (for retention)

### High Value
- Main Content Extraction (detailed knowledge)
- Personal Insights (learning)
- Critical Analysis (evaluation)
- Practical Application (skill transfer)

### Contextual
- Important Quotes (when memorable insights exist)
- Implementation Notes (for technical references)
- Evidence and Data (for research papers)

### Optional
- Additional Resources (if you'll revisit)
- Change Log (for evolving notes)

---

## Note-Taking Patterns

### For Standards (OWASP, NIST, etc.)

Focus on:
- What does compliance require?
- How to implement controls?
- Common failure patterns
- Testing methodology

### For CVEs

Focus on:
- Attack vector and exploitability
- Affected versions and configurations
- Proof of concept understanding (not exploitation)
- Mitigation and patches
- Detection strategies

### For Academic Papers

Focus on:
- Research question and hypothesis
- Methodology and experimental design
- Key findings and statistical significance
- Limitations and future work
- How this advances the field

### For Frameworks (MITRE ATT&CK, Kill Chain)

Focus on:
- Structure and taxonomy
- How attackers/defenders use it
- Mapping to real-world scenarios
- Integration with other frameworks

### For Technical Documentation

Focus on:
- Security-relevant features
- Attack surface analysis
- Configuration best practices
- Known vulnerabilities

---

## Common Mistakes to Avoid

❌ **Copying without processing** — Write in your own words to ensure understanding

❌ **Skipping the summary** — If you can't summarize it, you don't understand it

❌ **No connections** — Isolated knowledge is forgotten knowledge

❌ **Forgetting the defensive side** — Every attack needs a defense, every defense assumes an attack

❌ **No review schedule** — You'll forget 80% without spaced repetition

❌ **Perfectionism** — Better to have minimal notes than no notes

❌ **Passive reading** — Active note-taking forces engagement

---

## Spaced Repetition Schedule

Default intervals:
- **1 day** after initial reading
- **1 week** after first review
- **1 month** after second review
- **3 months** after third review
- **1 year** for long-term retention

Adjust based on:
- Importance (critical concepts = more frequent)
- Difficulty (harder material = more frequent)
- Usage (actively applying = less frequent reviews needed)

---

## Speed Optimization

### 10-Minute Note
- Metadata + Executive Summary only
- Tag it for deeper processing later

### 30-Minute Note
- Add Key Concepts (top 3)
- Add Personal Insights
- Set review schedule

### 60-Minute Note
- Complete Main Content Extraction
- Add Critical Analysis
- Include Practical Application

### 90-Minute Deep Dive
- Everything above + examples
- Cross-reference extensively
- Create related exercises

---

## Tag Taxonomy

### Domain Tags
`#offensive` `#defensive` `#cryptography` `#network` `#web` `#mobile` `#cloud` `#iot`

### Activity Tags
`#reconnaissance` `#exploitation` `#post-exploitation` `#persistence` `#detection` `#response` `#hardening` `#forensics`

### Level Tags
`#beginner` `#intermediate` `#advanced` `#expert`

### Type Tags
`#paper` `#standard` `#framework` `#cve` `#documentation` `#book` `#tool`

### Status Tags
`#in-progress` `#needs-review` `#outdated` `#high-priority`

Use consistently for searchability:
```bash
# Find all offensive papers
grep -r "#offensive" 05_references/papers/

# Find beginner-friendly standards
grep -r "#beginner" 05_references/standards/
```

---

## Review Workflow

### Weekly Review Session

```bash
# Find notes due for review this week
grep -r "REVIEW: $(date +%Y-%m)" 05_references/

# For each note:
# 1. Can I recall key concepts?
# 2. Any new connections?
# 3. Is information still current?
# 4. Update next review date
```

### Monthly Audit

- Check for broken links
- Update outdated information
- Add new cross-references discovered
- Archive or delete low-value notes

---

## Integration Points

| Your Notes In | Feed Into | How |
|---------------|-----------|-----|
| 05_references/ | 01_theory/ | References provide evidence for theory explanations |
| 05_references/ | 02_examples/ | Examples demonstrate concepts from references |
| 05_references/ | 03_exercises/ | Exercises test understanding of referenced material |
| 05_references/ | 04_resources/ | Resources mentioned in references get cataloged |

Always create these connections explicitly in your notes.

---

## Questions?

- Unclear what goes in a section? Check the [example note](standards/OWASP/owasp-top-10-2021-EXAMPLE.md)
- Need more detail? See the [full template](_reference-note-template.md)
- Organizational questions? See the [main README](README.md)
