# [EXAMPLE NAME] — [Attack / Defense / Dual-Perspective / Case Study]

---

## Metadata

| Field             | Value                                                                                                             |
| ----------------- | ----------------------------------------------------------------------------------------------------------------- |
| **Type**          | [Attack Demonstration / Defense Implementation / Dual-Perspective / Case Study / Tool Demonstration]              |
| **Domain**        | [Cryptography / Network Security / Offensive / Defensive / Application Security / Malware Analysis / Specialized] |
| **Difficulty**    | [Beginner / Intermediate / Advanced / Expert]                                                                     |
| **Time Estimate** | [30min / 1h / 2h / etc.]                                                                                          |
| **Lab Required**  | [Yes / No]                                                                                                        |
| **Last Updated**  | [YYYY-MM-DD]                                                                                                      |
| **Status**        | [Draft / Tested / Verified / Needs Update]                                                                        |

### Prerequisites

**Knowledge:**

- [Theory concept 1](../../01_theory/domain/concept-1.md)
- [Theory concept 2](../../01_theory/domain/concept-2.md)

**Tools:**

- [Tool 1](../../04_resources/tools/tool-1.md) — Version X.X
- [Tool 2](../../04_resources/tools/tool-2.md) — Version X.X

**Environment:**

- [Operating system and version]
- [Network topology if applicable]
- [Required services or applications]

---

## Learning Objectives

After working through this example, you will understand:

1. [Specific learning objective 1]
2. [Specific learning objective 2]
3. [Specific learning objective 3]
4. [How to apply this technique / defense in practice]
5. [How to detect / prevent this attack (for offensive examples)]

---

## Scenario

### Context

**Situation:**
[Describe the realistic scenario this example demonstrates]

**Actors:**

- **Attacker:** [Role, capabilities, objectives]
- **Defender:** [Role, capabilities, objectives]
- **Target:** [System, application, or network being targeted]

**Objective:**

- **Offensive goal:** [What the attacker is trying to achieve]
- **Defensive goal:** [What the defender is trying to prevent/detect]

### Environment Setup

**Lab Configuration:**

```
[Describe network topology, systems involved, IP addresses, etc.]

Example:
Attacker: Kali Linux 2024.1 (192.168.1.100)
Target: Ubuntu 22.04 LTS (192.168.1.10)
Network: Isolated lab network (192.168.1.0/24)
```

**Software Versions:**

- [Application 1]: Version X.X
- [Application 2]: Version X.X
- [Tool 1]: Version X.X

**Setup Instructions:**

```bash
# Step 1: [Setup step description]
[command]

# Step 2: [Setup step description]
[command]

# Step 3: [Setup step description]
[command]
```

**Safety Note:**

> ⚠️ **WARNING:** [Describe safety constraints - isolated lab, permissions, etc.]

---

## Demonstration

### Phase 1: [First Phase Name - e.g., Reconnaissance / Initial Setup]

#### Step 1: [Specific Action]

**Objective:**
[What this step aims to achieve]

**Reasoning:**
[Why we're taking this approach]

**Command:**

```bash
# [Context for this command]
[command with flags explained]
```

**Output:**

```
[Expected output]
```

**Analysis:**
[Interpret the output — what does this tell us?]

**Key Observation:**
[What important information do we extract here?]

---

#### Step 2: [Next Action]

**Objective:**
[What this step aims to achieve]

**Reasoning:**
[Why we're taking this approach]

**Command:**

```bash
[command]
```

**Output:**

```
[Expected output]
```

**Analysis:**
[Interpret the output]

**Decision Point:**

> Based on [observation], we could either [option A] or [option B].
> We choose [option] because [reasoning].

---

#### Step 3: [Next Action]

**Objective:**
[What this step aims to achieve]

**Reasoning:**
[Why we're taking this approach]

**Code/Config Example:**

```python
# [Context for this code]
[code with inline comments]
```

**Execution:**

```bash
[command to run the code]
```

**Output:**

```
[Expected output]
```

**Analysis:**
[Interpret the output]

---

### Phase 2: [Second Phase Name - e.g., Exploitation / Detection]

#### Step 1: [Specific Action]

**Objective:**
[What this step aims to achieve]

**Reasoning:**
[Why we're taking this approach]

**[Command/Code/Configuration]:**

```
[command or code]
```

**Output:**

```
[Expected output]
```

**Analysis:**
[Interpret the output]

**Indicator of Compromise (if applicable):**

- [IOC 1]: [Description]
- [IOC 2]: [Description]

---

#### Step 2: [Next Action]

[Continue pattern for each step]

---

### Phase 3: [Third Phase Name - e.g., Post-Exploitation / Response]

#### Step 1: [Specific Action]

[Continue pattern]

---

#### Step 2: [Next Action]

[Continue pattern]

---

### Phase 4: [Final Phase - e.g., Impact Assessment / Cleanup]

#### Step 1: [Specific Action]

[Continue pattern]

---

## Dual Perspective

> **For dual-perspective examples:** Show both attack and defense timelines side by side.

### Attacker Timeline

| Time    | Action           | Outcome  |
| ------- | ---------------- | -------- |
| T+0     | [Initial action] | [Result] |
| T+5min  | [Next action]    | [Result] |
| T+15min | [Next action]    | [Result] |

### Defender Timeline

| Time    | Observation          | Response                  |
| ------- | -------------------- | ------------------------- |
| T+0     | [Normal baseline]    | [No action]               |
| T+6min  | [Anomaly detected]   | [Investigation triggered] |
| T+16min | [Incident confirmed] | [Containment action]      |

---

## Analysis

### What Worked

**Attack Perspective:**

1. [Why this attack succeeded]
2. [What made this technique effective]
3. [Critical factors that enabled success]

**Defense Perspective:**

1. [Where detection occurred (or could have)]
2. [What defensive controls were effective]
3. [Response actions that limited impact]

### What Failed

**Attack Perspective:**

1. [What didn't work or caused issues]
2. [Limitations encountered]
3. [Trade-offs made]

**Defense Perspective:**

1. [Where detection failed (or would fail)]
2. [Gaps in defensive coverage]
3. [Response limitations]

### Key Lessons

**Offensive Takeaways:**

- [Lesson 1]: [Explanation]
- [Lesson 2]: [Explanation]
- [Lesson 3]: [Explanation]

**Defensive Takeaways:**

- [Lesson 1]: [Explanation]
- [Lesson 2]: [Explanation]
- [Lesson 3]: [Explanation]

**Transferable Principles:**

- [General principle this demonstrates]
- [How this applies to other scenarios]
- [Pattern recognition for future encounters]

### Common Mistakes

| Mistake          | Why It Happens  | How to Avoid          |
| ---------------- | --------------- | --------------------- |
| [Common error 1] | [Typical cause] | [Prevention strategy] |
| [Common error 2] | [Typical cause] | [Prevention strategy] |
| [Common error 3] | [Typical cause] | [Prevention strategy] |

---

## Defensive Countermeasures

> **For offensive examples:** Always include how to defend against this attack.

### Detection

**Indicators of Compromise:**

1. [Observable indicator 1]
2. [Observable indicator 2]
3. [Observable indicator 3]

**Detection Methods:**

```bash
# [Detection approach description]
[command or rule to detect this activity]
```

**Log Signatures:**

```
[Example log entries that would indicate this attack]
```

**SIEM Rule Example:**

```
[Example detection rule for SIEM/IDS]
```

### Prevention

**Immediate Mitigations:**

1. [Quick action to stop the attack]
2. [Emergency response measure]
3. [Short-term fix]

**Long-Term Hardening:**

1. [Configuration change]
2. [Architectural improvement]
3. [Process improvement]

**Secure Configuration Example:**

```
# [Context for this configuration]
[secure configuration that prevents this attack]
```

### Response

**Incident Response Steps:**

1. **Contain:** [Containment action]
2. **Investigate:** [Investigation steps]
3. **Remediate:** [Remediation action]
4. **Recover:** [Recovery process]
5. **Learn:** [Post-incident improvement]

---

## Extensions & Variations

### Variation 1: [Change One Constraint]

**Scenario:**
[Describe how the scenario changes]

**Impact:**
[How does this change the attack/defense?]

**Approach:**
[How would you adapt your technique?]

**Try It:**
[Concrete steps to try this variation]

---

### Variation 2: [Advanced Technique]

**Scenario:**
[Describe the advanced scenario]

**Prerequisites:**
[Additional knowledge or tools needed]

**Approach:**
[High-level description of advanced technique]

**Reference:**
[Link to relevant advanced theory or reference]

---

### Variation 3: [Alternative Approach]

**Scenario:**
[Describe alternative approach to same objective]

**Trade-offs:**
[Advantages and disadvantages of this approach]

**When to Use:**
[Situations where this approach is preferable]

---

## Tool Notes

### [Tool 1 Name]

**Version Used:** X.X.X

**Key Flags:**

- `-flag1`: [What this does]
- `-flag2`: [What this does]
- `-flag3`: [What this does]

**Common Issues:**

- [Issue]: [Solution]
- [Issue]: [Solution]

**Alternatives:**

- [Alternative tool 1]: [When to use]
- [Alternative tool 2]: [When to use]

---

### [Tool 2 Name]

[Same structure as above]

---

## Understanding Check

> **Instructions:** Try to answer these without looking back at the demonstration.

### Comprehension Questions

1. **Explain the attack/defense flow:** Describe the key steps in your own words.

2. **Critical decision point:** At [specific step], why was [action] chosen over alternatives?

3. **Detection opportunity:** Where could a defender detect this activity? What would they observe?

4. **Mitigation strategy:** How would you prevent this attack with [different constraint]?

5. **Variation:** If [one thing changed], how would the attack/defense need to adapt?

### Application Questions

6. **New scenario:** [Describe a different but related scenario]
   - How would you apply this technique?
   - What would change?

7. **Tool selection:** If [tool used] was unavailable, what alternative would you use and why?

8. **Risk assessment:** What are the top 3 risks of this attack/defense approach?

### Transfer Learning

9. **Pattern recognition:** What general attack/defense pattern does this exemplify?

10. **Real-world application:** Where have you seen this technique used in real incidents? Link a CVE or breach report.

---

## References

### Theory Modules

- [Core concept theory](../../01_theory/domain/concept.md)
- [Related theory](../../01_theory/domain/related-concept.md)

### Standards & Frameworks

- [MITRE ATT&CK](../../05_references/frameworks/MITRE-ATT&CK/relevant-technique.md) — [Technique ID and name]
- [OWASP](../../05_references/standards/OWASP/relevant-standard.md)

### CVEs & Real-World Examples

- [CVE-YYYY-XXXXX](../../05_references/CVE/by-year/YYYY/cve-yyyy-xxxxx.md) — [Description]
- [Incident report](../../02_examples/08-case-studies/major-breaches/incident.md)

### Tools Used

- [Tool 1](../../04_resources/tools/tool-1.md)
- [Tool 2](../../04_resources/tools/tool-2.md)

### Further Reading

- [Related paper](../../05_references/papers/domain/paper.md)
- [Technical documentation](../../05_references/documentation/category/doc.md)

---

## Related Content

### Practice Exercises

Apply what you learned:

- [Beginner exercise](../../03_exercises/domain/exercise-beginner.md)
- [Intermediate exercise](../../03_exercises/domain/exercise-intermediate.md)
- [Advanced exercise](../../03_exercises/domain/exercise-advanced.md)

### Related Examples

- [Related example 1](../domain/related-example-1.md) — [Brief description]
- [Related example 2](../domain/related-example-2.md) — [Brief description]

---

## Personal Notes

> **Instructions:** Add your own observations, troubleshooting notes, and insights here.

### Environment Notes

[Document any environment-specific issues or configurations]

### Troubleshooting

| Issue Encountered | Solution            |
| ----------------- | ------------------- |
| [Problem]         | [How you solved it] |

### Performance Notes

[Observations about speed, reliability, or efficiency]

### Alternative Approaches Tried

[Document variations you attempted and their outcomes]

### Questions

- [Question about this technique]
- [Uncertainty or area for further research]

### Personal Insights

**[Date]:** [Your observation or insight]

**[Date]:** [Connection to other knowledge]

---

## Reproducibility Checklist

Before marking this example "Verified":

- [ ] Environment setup instructions are complete and accurate
- [ ] All commands execute successfully in clean environment
- [ ] Outputs match what's documented
- [ ] Screenshots/diagrams are current (if included)
- [ ] Tools are at specified versions
- [ ] Safety warnings are prominent
- [ ] Alternative approaches are noted
- [ ] Defensive countermeasures are included
- [ ] Links to theory, exercises, and references work
- [ ] Understanding checks test the right concepts
- [ ] Someone else has successfully reproduced this example

---

## Change Log

| Date         | Change        | Reason                    |
| ------------ | ------------- | ------------------------- |
| [YYYY-MM-DD] | [Description] | [Why the change was made] |
| [YYYY-MM-DD] | [Description] | [Why the change was made] |

---

## Template Usage Notes

**When creating a new example from this template:**

1. Delete this section
2. Choose the example type (attack, defense, dual-perspective, case study, tool demo)
3. Fill out all metadata
4. Document environment setup completely
5. Work through demonstration yourself first
6. Capture all commands and outputs
7. Analyze what worked and what failed
8. Always include defensive countermeasures (even for offensive examples)
9. Add understanding checks
10. Link to theory, exercises, references, and tools
11. Have someone else test reproducibility
12. Mark status as "Verified" only after peer review

**Quality check before marking "Verified":**

- [ ] Reproducible in documented environment
- [ ] All commands tested and outputs verified
- [ ] Step-by-step reasoning provided
- [ ] Both offensive and defensive perspectives covered
- [ ] Common mistakes documented
- [ ] Understanding checks test application, not memorization
- [ ] Links to related content complete
- [ ] Safety and ethical guidelines included
- [ ] Variations and extensions suggested
- [ ] Tool notes comprehensive
