# [TOPIC NAME]

---

## Metadata

| Field | Value |
|-------|-------|
| **Topic** | [Precise concept name] |
| **Domain** | [Cryptography / Network Security / Offensive Security / Defensive Security / Application Security / Malware Analysis / Specialized / Frameworks] |
| **Difficulty** | [Beginner / Intermediate / Advanced / Expert] |
| **Prerequisites** | [List concepts that must be understood first] |
| **Learning Time** | [Estimated study time: 30min / 1h / 2h / etc.] |
| **Last Updated** | [YYYY-MM-DD] |
| **Status** | [Draft / In Progress / Complete / Needs Review] |

### Review Schedule

- [ ] Day 1: [YYYY-MM-DD] — Initial read
- [ ] Day 2: [YYYY-MM-DD] — First review (active recall)
- [ ] Week 1: [YYYY-MM-DD] — Second review
- [ ] Month 1: [YYYY-MM-DD] — Third review
- [ ] Month 3: [YYYY-MM-DD] — Fourth review

---

## Quick Summary

**One-sentence summary:**
[Write a single sentence that captures the essence of this concept]

**Why this matters:**
[1-2 sentences explaining the practical importance of this concept in cybersecurity]

**Offensive perspective:**
[How attackers use/exploit this]

**Defensive perspective:**
[How defenders protect against/detect this]

---

## Prerequisites

Before studying this module, you should understand:

- [Prerequisite concept 1](../domain/prerequisite-1.md)
- [Prerequisite concept 2](../domain/prerequisite-2.md)
- [Prerequisite concept 3](../domain/prerequisite-3.md)

**Quick prerequisite check:**
- [ ] Can you explain [prerequisite 1] in your own words?
- [ ] Do you understand [prerequisite 2] at a practical level?
- [ ] Have you worked with [prerequisite 3] before?

If you answered "no" to any of these, review the prerequisite modules first.

---

## Layer 1: Intuition (Fast Mental Model)

> **Goal:** Build instant recognition. Use concrete analogy, zero jargon, 1-2 sentences maximum.

[Write the simplest correct explanation using a concrete, familiar analogy]

**Example intuition:**
"[Concept] is like [everyday analogy]. When [scenario], [simplified mechanism]."

**Visual mental model:**
```
[Optional: Simple ASCII diagram or description of mental model]
```

---

## Layer 2: Formal Definition

> **Goal:** Precise, unambiguous understanding. Introduce necessary terminology.

### Technical Definition

[Provide the formal, technical definition of the concept]

### Key Terminology

| Term | Definition |
|------|------------|
| **[Term 1]** | [Clear definition] |
| **[Term 2]** | [Clear definition] |
| **[Term 3]** | [Clear definition] |

### Core Mechanism

[Explain HOW the concept works, step by step]

1. **Step 1:** [What happens first]
2. **Step 2:** [What happens next]
3. **Step 3:** [What happens finally]

**Why this works:**
[Explain the underlying principle or reason why the mechanism functions]

---

## Layer 3: Worked Example

> **Goal:** Demonstrate concept application step-by-step with both offensive and defensive perspectives.

### Scenario

[Describe a realistic scenario where this concept applies]

**Context:**
- Environment: [Describe the system/network/application]
- Actors: [Who is involved - attacker, defender, user, etc.]
- Objective: [What is being attempted]

### Offensive Walkthrough

#### Step 1: [First action]

**What happens:**
[Describe what the attacker does]

**Why this works:**
[Explain the underlying reason this step succeeds]

**Command/Code example:**
```bash
# [Context for this command]
[command or code here]
```

**Output:**
```
[Expected output]
```

**Reasoning:**
[Explain the reasoning at this step - what information is gained, what vulnerability is exploited, etc.]

#### Step 2: [Second action]

**What happens:**
[Describe the next action]

**Why this works:**
[Explain the mechanism]

**Command/Code example:**
```bash
[command or code here]
```

**Output:**
```
[Expected output]
```

**Reasoning:**
[Explain the reasoning]

#### Step 3: [Final action]

**What happens:**
[Describe the final action or outcome]

**Result:**
[What the attacker achieves]

---

### Defensive Walkthrough

> **Critical:** For every attack, there must be a defense.

#### Detection Strategy

**Indicators of compromise:**
1. [Observable indicator 1]
2. [Observable indicator 2]
3. [Observable indicator 3]

**Detection method:**
```bash
# [Context for detection command]
[command or monitoring rule]
```

**What to look for:**
- [Specific pattern or signature]
- [Anomaly or deviation from baseline]
- [Timing or sequence indicator]

#### Prevention Strategy

**Immediate mitigation:**
1. [First defensive action]
2. [Second defensive action]
3. [Third defensive action]

**Long-term hardening:**
- [Configuration change]
- [Architectural improvement]
- [Process improvement]

**Defensive code/configuration:**
```
# [Context - what this protects]
[secure code or configuration example]
```

**Why this works:**
[Explain the defensive mechanism]

---

### Analysis

**Attack chain summary:**
[High-level overview of the attack flow]

**Defense chain summary:**
[High-level overview of the defensive strategy]

**Critical control points:**
[Identify where the defense can break the attack chain most effectively]

---

## Layer 4: Edge Cases & Failure Modes

> **Goal:** Develop robust understanding of limitations. Document where the model breaks.

### When the Attack Fails

**Scenario 1: [Defensive control present]**
- Why it fails: [Explanation]
- Bypass technique (if exists): [Advanced technique, if applicable]

**Scenario 2: [Environmental constraint]**
- Why it fails: [Explanation]
- Alternative approach: [If one exists]

**Scenario 3: [Detection/response]**
- Why it fails: [Explanation]
- Evasion technique (if exists): [Advanced technique]

### When the Defense Fails

**Scenario 1: [Misconfiguration]**
- How it's bypassed: [Explanation]
- Correct configuration: [Fix]

**Scenario 2: [Incomplete coverage]**
- How it's bypassed: [Explanation]
- Complete solution: [Fix]

**Scenario 3: [Novel attack variation]**
- How it's bypassed: [Explanation]
- Adaptive defense: [Solution]

### Limitations of the Analogy

**Where the L1 analogy breaks down:**
- [Limitation 1 of the intuitive analogy]
- [Limitation 2 of the intuitive analogy]
- [What the analogy misses or oversimplifies]

### Common Misconceptions

| Misconception | Reality |
|---------------|---------|
| [Common wrong belief 1] | [Correct understanding] |
| [Common wrong belief 2] | [Correct understanding] |
| [Common wrong belief 3] | [Correct understanding] |

### Advanced Variations

[Describe more complex or advanced versions of this concept that go beyond the basics covered above]

---

## Active Recall Prompts

> **Instructions:** Try to answer these WITHOUT looking back at the content above. Write your answers, then verify.

### Understanding Check

1. **Explain in your own words:** What is [concept] and why does it matter?

2. **Mechanism:** Describe the core mechanism step-by-step without looking at Layer 2.

3. **Offensive application:** Given scenario [X], how would an attacker use [concept]?

4. **Defensive application:** How would you detect and prevent [concept] in production?

5. **Edge case:** When does [concept] fail? Provide at least two scenarios.

### Application Prompts

6. **New scenario:** [Describe a novel scenario different from the worked example]
   - How would the attack work here?
   - How would you defend?

7. **Variation:** What happens if [change one constraint from the worked example]?

8. **Real-world:** Find a CVE or real-world incident that demonstrates [concept]. Link it in your notes.

### Transfer Learning

9. **Connection:** How does [concept] relate to [another security concept]?

10. **Generalization:** What general security principle does [concept] exemplify?

---

## References

### Primary Sources

- [Reference 1 - link to 05_references/](../../05_references/category/reference-name.md)
- [Reference 2 - link to 05_references/](../../05_references/category/reference-name.md)
- [Reference 3 - link to 05_references/](../../05_references/category/reference-name.md)

### Standards & Frameworks

- [OWASP / NIST / MITRE reference](../../05_references/standards/standard-name.md)
- [Relevant framework](../../05_references/frameworks/framework-name.md)

### CVEs & Real-World Examples

- [CVE-YYYY-XXXXX](../../05_references/CVE/by-year/YYYY/cve-yyyy-xxxxx.md) — [Brief description]
- [CVE-YYYY-XXXXX](../../05_references/CVE/by-year/YYYY/cve-yyyy-xxxxx.md) — [Brief description]

### Further Reading

- [Academic paper](../../05_references/papers/domain/paper-name.md)
- [Technical documentation](../../05_references/documentation/category/doc-name.md)
- [Textbook section](../../05_references/textbooks/TEXTBOOKS.md) — [Book name, chapter X]

---

## Related Content

### Examples

Practical demonstrations of this concept:
- [Example 1](../../02_examples/domain/example-name.md) — [Brief description]
- [Example 2](../../02_examples/domain/example-name.md) — [Brief description]

### Exercises

Practice problems to test understanding:
- [Exercise 1 - Beginner](../../03_exercises/domain/exercise-name-beginner.md)
- [Exercise 2 - Intermediate](../../03_exercises/domain/exercise-name-intermediate.md)
- [Exercise 3 - Advanced](../../03_exercises/domain/exercise-name-advanced.md)

### Tools

Security tools mentioned in this module:
- [Tool 1](../../04_resources/tools/tool-name.md) — [Purpose]
- [Tool 2](../../04_resources/tools/tool-name.md) — [Purpose]

### Related Theory Modules

**Prerequisites:**
- [Prerequisite module](../domain/prerequisite.md)

**Builds upon:**
- [Foundational module](../domain/foundation.md)

**Leads to:**
- [Advanced module](../domain/advanced.md)

**Related concepts:**
- [Parallel concept 1](../domain/related-1.md)
- [Parallel concept 2](../domain/related-2.md)

---

## Personal Insights

> **Instructions:** Add your own notes, questions, and insights here as you learn.

### Questions I Still Have

- [Question 1]
- [Question 2]
- [Question 3]

### Insights from Experience

[Add notes from hands-on practice, CTF challenges, or real-world application]

### Connections I Discovered

[Note connections to other concepts that weren't explicitly mentioned above]

### Evolution of Understanding

**[Date]:** [Note about how your understanding changed or deepened]

**[Date]:** [New insight or correction]

---

## Change Log

| Date | Change | Reason |
|------|--------|--------|
| [YYYY-MM-DD] | [Description of change] | [Why the change was made] |
| [YYYY-MM-DD] | [Description of change] | [Why the change was made] |

---

## Template Usage Notes

**When creating a new theory module from this template:**

1. Delete this section
2. Replace all [placeholders] with actual content
3. Fill out all four layers - do not skip any
4. Ensure offensive AND defensive perspectives are covered
5. Provide at least one fully worked example
6. Include 5-10 active recall prompts
7. Link to at least 2 references
8. Create corresponding example and exercise files
9. Set your review schedule dates
10. Update metadata (date, status, learning time estimate)

**Quality check before marking "Complete":**
- [ ] All four explanation layers present and complete
- [ ] Both offensive and defensive perspectives included
- [ ] At least one worked example with step-by-step reasoning
- [ ] Edge cases and failure modes documented
- [ ] Active recall prompts test understanding (not just memorization)
- [ ] References to authoritative sources
- [ ] Links to related examples and exercises
- [ ] Prerequisites clearly stated
- [ ] Common misconceptions identified
- [ ] Personal insights section ready for use
