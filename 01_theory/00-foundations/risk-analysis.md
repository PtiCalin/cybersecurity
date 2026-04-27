# Risk Analysis — Analyse du Risque

| Property          | Value                                                                         |
| ----------------- | ----------------------------------------------------------------------------- |
| **Topic**         | Risk Analysis / Analyse du Risque                                             |
| **Domain**        | 00-foundations                                                                |
| **Difficulty**    | 🟡 Intermediate                                                               |
| **Prerequisites** | [CIA Triad](cia-triad.md), basic understanding of threats and vulnerabilities |
| **Learning Time** | 60-90 minutes                                                                 |
| **Status**        | ✅ Complete                                                                   |

---

## Review Schedule

- [ ] Day 2 — First review after initial study
- [ ] Week 1 — Consolidation review
- [ ] Month 1 — Long-term retention check
- [ ] Month 3 — Mastery verification

---

## Quick Summary

**What:** Risk analysis is the systematic process of identifying, evaluating, and prioritizing security risks to determine how to treat them.

**Offensive:** Attackers exploit vulnerabilities to threaten assets; understanding risk helps prioritize attack vectors.
**Defensive:** Defenders use risk analysis to allocate resources effectively and implement countermeasures where they matter most.

**Why it matters:** You can't defend everything perfectly. Risk analysis tells you _what_ to defend, _how much_ to invest, and _when_ to act.

---

## Prerequisites

**Required knowledge:**

- [CIA Triad](cia-triad.md) — Understanding what you're protecting
- Basic probability concepts
- Understanding of organizational assets

**Quick check:** Can you explain the difference between a "threat" and a "vulnerability"? If yes, you're ready.

---

## Layer 1 — Intuition

Think of risk analysis like evaluating whether to cross a busy street:

🏃 **Capability (C)** = How fast cars are moving (threat capability)
🚦 **Opportunity (O)** = Is there a crosswalk? Traffic light? (vulnerabilities)
💰 **Motivation (M)** = How badly do you need to cross? (attacker motivation)

**Risk = Probability × Impact**

- **Probability** = How likely you'll get hit = median(C, O, M)
- **Impact** = How bad getting hit would be (injury, death)

**Decision:** Cross now? Wait for a light? Take a bridge? (Risk treatment)

---

## Layer 2 — Formal Definitions

### Core Risk Concepts

#### Actif (Asset)

**Definition:** An element having value to the organization.

**Examples:**

- **Technical:** Servers, databases, networks, applications
- **Information:** Customer data, trade secrets, source code
- **Organizational:** Reputation, employee expertise, brand
- **Physical:** Buildings, equipment, infrastructure

**French term:** _Actif_

---

#### Menace (Threat)

**Definition:** A potential cause that can harm an asset.

**Categories:**

- **Délibérée (Deliberate):** Hacker, insider threat, competitor
- **Accidentelle (Accidental):** Human error, misconfiguration
- **Naturelle (Natural):** Fire, flood, earthquake
- **Technique (Technical):** System failure, software bug

**French term:** _Menace_

---

#### Vulnérabilité (Vulnerability)

**Definition:** A weakness that can be exploited by a threat.

**Examples:**

- Unpatched software
- Weak passwords
- Missing encryption
- Unsecured Wi-Fi
- Lack of access controls

**French term:** _Vulnérabilité_

---

#### Scénario de Risque (Risk Scenario)

**Definition:** A threat exploiting a vulnerability to affect an asset and cause an impact.

**Structure:**
`Menace` exploits `Vulnérabilité` → Affects `Actif` → Causes `Impact`

**Example:**
_Hacker_ (menace) exploits _unpatched SQL vulnerability_ (vulnérabilité) → Affects _customer database_ (actif) → Causes _data breach_ (impact)

**French term:** _Scénario de risque_

---

### Risk Components

#### Impact (Impact)

**Definition:** The severity of consequences if the risk materializes.

**Measures:**

- **Qualitative:** Low, Medium, High, Critical
- **Quantitative:** Dollar loss, downtime hours, records exposed

**Affects:**

- Confidentiality, Integrity, Availability (CIA)
- Reputation, legal compliance, financial stability

**French term:** _Impact_

---

#### Probabilité (Probability)

**Definition:** The likelihood that a risk scenario will occur.

**Factors determining probability:**

1. **Capacité (Capability)** — Attacker's skills and resources
   - Script kiddie (low) vs. Nation-state actor (high)

2. **Opportunité (Opportunity)** — Environmental conditions favoring the attack
   - Exposed services, weak defenses, outdated systems

3. **Motivation (Motivation)** — Attacker's incentive or benefit
   - Financial gain, espionage, hacktivism, revenge

**Formula:**
`Probabilité (P) = median(Capacité, Opportunité, Motivation)`

**French terms:** _Probabilité_, _Capacité_, _Opportunité_, _Motivation_

---

#### Risque (Risk)

**Definition:** The combination of probability and impact.

**Formula:**
**R (Risque) = P (Probabilité) × I (Impact)**

**Risk Matrix:**

|                        | Impact faible (1) | Impact moyen (2) | Impact élevé (3) | Impact critique (4) |
| ---------------------- | ----------------- | ---------------- | ---------------- | ------------------- |
| **Prob. faible (1)**   | 🟢 1 (Bas)        | 🟢 2 (Bas)       | 🟡 3 (Moyen)     | 🟡 4 (Moyen)        |
| **Prob. moyenne (2)**  | 🟢 2 (Bas)        | 🟡 4 (Moyen)     | 🟠 6 (Élevé)     | 🟠 8 (Élevé)        |
| **Prob. élevée (3)**   | 🟡 3 (Moyen)      | 🟠 6 (Élevé)     | 🟠 9 (Élevé)     | 🔴 12 (Critique)    |
| **Prob. critique (4)** | 🟡 4 (Moyen)      | 🟠 8 (Élevé)     | 🔴 12 (Critique) | 🔴 16 (Critique)    |

**French term:** _Risque_

---

### Risk Management Actions

#### Contre-mesure (Countermeasure)

**Definition:** An action taken to reduce the probability or impact of a risk.

**Types:**

- **Préventive (Preventive):** Prevents the risk from occurring (firewall, access control)
- **Corrective (Corrective):** Reduces consequences after the incident (backups, incident response)

**French term:** _Contre-mesure_

---

#### Traitement du Risque (Risk Treatment)

**Definition:** The decision on how to handle a risk.

**Four strategies:**

1. **Réduction (Mitigation):** Implement controls to reduce P or I
   _Example:_ Install firewall, enforce MFA

2. **Acceptation (Acceptance):** Tolerate the risk without additional action
   _Example:_ Low-probability, low-impact scenario within risk appetite

3. **Transfert (Transfer):** Shift the risk to a third party
   _Example:_ Cyber insurance, outsource to cloud provider with SLA

4. **Élimination (Elimination):** Remove the source of the risk
   _Example:_ Decommission vulnerable legacy system, stop using risky technology

**French terms:** _Traitement du risque_, _Réduction_, _Acceptation_, _Transfert_, _Élimination_

---

## Layer 3 — Worked Examples

### Example 1: E-commerce Database Risk Analysis

**Organization:** Online retail company with customer database (payment info, personal data)

#### Step 1: Identify Assets

- **Primary asset:** Customer database (1M records, credit cards, addresses)

#### Step 2: Identify Threats

- External hacker seeking financial data
- Insider with administrative access
- Malware (ransomware)

#### Step 3: Identify Vulnerabilities

- Unpatched database server (6 months behind)
- No multi-factor authentication for admin accounts
- Database backup stored on same server
- No encryption at rest

#### Step 4: Construct Risk Scenarios

**Scenario 1: SQL Injection Attack**

| Component         | Value                | Justification                                            |
| ----------------- | -------------------- | -------------------------------------------------------- |
| **Menace**        | External hacker      | Financially motivated, targets e-commerce                |
| **Vulnérabilité** | Unpatched SQL server | Known CVE-2023-XXXX exploit available                    |
| **Actif**         | Customer database    | 1M records, payment data                                 |
| **Impact**        | 🔴 Critical (4)      | Data breach, GDPR fines, reputation loss, financial loss |
| **Capacité**      | 🟠 Élevée (3)        | Public exploits available, moderate skill required       |
| **Opportunité**   | 🔴 Critique (4)      | Server exposed to internet, no WAF, unpatched            |
| **Motivation**    | 🟠 Élevée (3)        | Financial gain from selling credit cards                 |
| **Probabilité**   | 🟠 Élevée (3)        | median(3, 4, 3) = 3                                      |
| **Risque**        | 🔴 **12 (Critique)** | P(3) × I(4) = 12                                         |

**Treatment Decision:** **Réduction immédiate (Immediate mitigation)**

- Patch database server within 48 hours
- Implement Web Application Firewall (WAF)
- Deploy SQL injection detection
- Encrypt database at rest

---

**Scenario 2: Insider Data Exfiltration**

| Component         | Value                                 | Justification                                 |
| ----------------- | ------------------------------------- | --------------------------------------------- |
| **Menace**        | Disgruntled employee                  | Insider with legitimate access                |
| **Vulnérabilité** | No MFA, no data loss prevention (DLP) | Single password protects admin access         |
| **Actif**         | Customer database                     | 1M records                                    |
| **Impact**        | 🔴 Critical (4)                       | Same as Scenario 1                            |
| **Capacité**      | 🟠 Élevée (3)                         | Already has access and knowledge              |
| **Opportunité**   | 🟡 Moyenne (2)                        | Logging exists but not monitored in real-time |
| **Motivation**    | 🟢 Faible (1)                         | Low likelihood of employee turning malicious  |
| **Probabilité**   | 🟡 Moyenne (2)                        | median(3, 2, 1) = 2                           |
| **Risque**        | 🟠 **8 (Élevé)**                      | P(2) × I(4) = 8                               |

**Treatment Decision:** **Réduction progressive (Progressive mitigation)**

- Implement MFA for admin accounts (high priority)
- Deploy Data Loss Prevention (DLP) solution
- Enable real-time database access monitoring
- Enforce principle of least privilege

---

**Scenario 3: Ransomware Encryption**

| Component         | Value                                          | Justification                                 |
| ----------------- | ---------------------------------------------- | --------------------------------------------- |
| **Menace**        | Ransomware (e.g., Ryuk)                        | Financially motivated cybercrime              |
| **Vulnérabilité** | Backups on same server, no offline backup      | Ransomware can encrypt backups too            |
| **Actif**         | Customer database + entire system availability | Data + operations                             |
| **Impact**        | 🔴 Critical (4)                                | Business halt, data loss, ransom payment      |
| **Capacité**      | 🟡 Moyenne (2)                                 | Ransomware-as-a-Service (RaaS) lowers barrier |
| **Opportunité**   | 🟠 Élevée (3)                                  | Email phishing common, no user training       |
| **Motivation**    | 🟠 Élevée (3)                                  | Financial gain from ransom                    |
| **Probabilité**   | 🟠 Élevée (3)                                  | median(2, 3, 3) = 3                           |
| **Risque**        | 🔴 **12 (Critique)**                           | P(3) × I(4) = 12                              |

**Treatment Decision:** **Réduction + Transfert (Mitigation + Transfer)**

- Implement offline, air-gapped backups (mitigation)
- Deploy endpoint detection and response (EDR)
- User security awareness training
- Purchase cyber insurance (transfer residual risk)

---

### Example 2: Risk Analysis Worksheet (Tabular Format)

| Scénario             | Capacité (C) | Opportunité (O) | Motivation (M) | Probabilité (P = median) | Impact (I) | Risque (R = P × I) | Traitement            |
| -------------------- | ------------ | --------------- | -------------- | ------------------------ | ---------- | ------------------ | --------------------- |
| SQL Injection        | 3            | 4               | 3              | 3                        | 4          | 🔴 **12**          | Réduction immédiate   |
| Insider exfiltration | 3            | 2               | 1              | 2                        | 4          | 🟠 **8**           | Réduction progressive |
| Ransomware           | 2            | 3               | 3              | 3                        | 4          | 🔴 **12**          | Réduction + Transfert |
| DDoS attack          | 2            | 3               | 2              | 2                        | 2          | 🟡 **4**           | Acceptation + CDN     |
| Physical theft       | 1            | 2               | 1              | 1                        | 3          | 🟢 **3**           | Acceptation           |

**Priority order:** SQL Injection = Ransomware > Insider > DDoS > Physical theft

---

## Layer 4 — Edge Cases, Nuances, and Limitations

### Edge Case 1: Cascading Risks

**Problem:** One risk materializing can trigger others.

**Example:**

- **Primary risk:** Ransomware encrypts systems (Availability loss)
- **Cascading risk 1:** Backups also encrypted → Integrity + Availability loss
- **Cascading risk 2:** Attacker threatens to leak stolen data (Extortion) → Confidentiality loss
- **Cascading risk 3:** Downtime violates SLA with customers → Financial + Reputation loss

**Solution:**

- Risk analysis must consider **dependencies** and **secondary impacts**
- Use attack trees or fault trees to map cascades
- Prioritize controls that break the chain (e.g., offline backups stop cascade)

---

### Edge Case 2: Zero-Day Vulnerabilities

**Problem:** How do you assess probability when the vulnerability is unknown?

**Scenario:** You're analyzing risk of a zero-day exploit in your web framework.

**Challenge:**

- **Capacité:** Unknown (depends on who discovers it first)
- **Opportunité:** Unknown (you don't know the vulnerability exists)
- **Motivation:** Known (attackers seek high-value targets)

**Approach:**

- Use **historical data**: How often have zero-days been discovered in this framework?
- **Assume vulnerability exists**: Evaluate impact if it were exploited
- **Implement defense in depth**: Even if P is unknown, reduce I through layering (WAF, IDS, segmentation)

**Risk treatment:** **Réduction proactive** — Defense in depth, even without known threats

---

### Edge Case 3: Quantitative vs. Qualitative Risk Assessment

**Qualitative (used in examples above):**

- Scales: Low/Medium/High/Critical
- Fast, intuitive, requires less data
- **Limitation:** Subjective, hard to compare across different risk types

**Quantitative:**

- Numerical: Probability in %, Impact in $ or hours
- **Formula:** `ALE (Annual Loss Expectancy) = SLE (Single Loss Expectancy) × ARO (Annual Rate of Occurrence)`
- More objective, supports ROI calculations
- **Limitation:** Requires accurate historical data, which is often unavailable

**When to use each:**

- **Qualitative:** Startup, SME, rapid risk assessment
- **Quantitative:** Enterprise, insurance, compliance (e.g., financial services)
- **Hybrid:** Start qualitative, refine critical risks quantitatively

---

### Edge Case 4: Risk Appetite and Tolerance

**Concepts:**

- **Risk Appetite:** The level of risk the organization is willing to accept to achieve its objectives
- **Risk Tolerance:** The maximum acceptable variation around risk appetite

**Problem:** What is "acceptable" risk?

**Example:**

- **Startup:** High risk appetite (rapid growth, aggressive innovation)
- **Bank:** Low risk appetite (regulatory compliance, reputation critical)

**Implication:** The same risk score (e.g., R=6) may be:

- **Acceptable** for a startup (within appetite)
- **Unacceptable** for a bank (exceeds tolerance)

**Solution:**

- Define organizational risk thresholds
- Map risk scores to treatment strategies:
  - R ≥ 9: Always mitigate or eliminate
  - R = 6-8: Mitigate or transfer
  - R = 3-5: Accept or mitigate (case-by-case)
  - R ≤ 2: Accept

---

### Limitation 1: Risk Analysis is Snapshot in Time

**Problem:** Threats, vulnerabilities, and assets change constantly.

**Example:**

- You assess ransomware risk as "Low" because backups exist
- One month later, backup system fails → Risk now "Critical"
- Risk analysis is outdated

**Solution:**

- **Continuous monitoring:** Reassess risks quarterly or after significant changes
- **Trigger events:** New vulnerability disclosure, system change, policy change
- **Living document:** Risk register is never "done"

---

### Limitation 2: Human Factors Are Hard to Quantify

**Problem:** Social engineering, insider threats, human error are difficult to model.

**Example:**

- Probability of successful phishing depends on user training, awareness, fatigue, trust culture
- These factors are qualitative and variable

**Solution:**

- Use **behavioral metrics**: Phishing simulation results, security awareness scores
- Assume **baseline human error rate**: ~5-10% failure rate in security controls
- Layer technical controls to compensate (e.g., email filtering, EDR)

---

## Risk Analysis Methodologies

### EBIOS (Expression des Besoins et Identification des Objectifs de Sécurité)

**Origin:** French ANSSI (Agence Nationale de la Sécurité des Systèmes d'Information)

**Approach:** Strategic, scenario-based, business-driven

**Key features:**

- Maps business objectives to security needs
- Focuses on critical scenarios (événements redoutés)
- Aligns with ISO 27001

**Best for:** French organizations, government, strategic planning

---

### MEHARI (Méthode Harmonisée d'Analyse de Risques)

**Origin:** CLUSIF (France)

**Approach:** Semi-quantitative, structured, audit-oriented

**Key features:**

- Uses predefined vulnerability and threat databases
- Quantifies risks with numerical scales
- Strong on risk treatment and control effectiveness

**Best for:** Large enterprises, audit-driven environments

---

### OCTAVE (Operationally Critical Threat, Asset, and Vulnerability Evaluation)

**Origin:** Carnegie Mellon University (US)

**Approach:** Self-assessment, organizational focus

**Key features:**

- Facilitated workshops with internal teams
- Focuses on organizational risk, not just technical
- Three phases: Build asset-based threat profiles → Identify infrastructure vulnerabilities → Develop security strategy

**Best for:** Organizations wanting internal ownership of risk management

---

### Risk IT

**Origin:** ISACA

**Approach:** IT governance integration

**Key features:**

- Integrates risk management with IT governance
- Aligns with COBIT framework
- Focuses on risk appetite and risk-aware decision-making

**Best for:** IT organizations, CIO/CISO collaboration

---

### ISO 27005 (International Standard for Information Security Risk Management)

**Origin:** ISO/IEC

**Approach:** Framework-agnostic, process-oriented

**Key features:**

- Defines risk management process (context, assessment, treatment, monitoring)
- Compatible with any risk methodology
- Aligns with ISO 27001 ISMS

**Best for:** Organizations seeking ISO 27001 certification, international alignment

---

## Active Recall Prompts

### Understanding Questions

1. **Define risk components:** Without looking, write definitions of: Actif, Menace, Vulnérabilité, Impact, Probabilité, Risque.

2. **Risk formula:** Write the formula for calculating risk. Explain what each component means.

3. **Probability factors:** What three factors determine probability in risk analysis? How do you combine them?

---

### Application Questions

4. **Scenario construction:** Your organization uses unencrypted USB drives to transport sensitive documents. Construct a complete risk scenario: Menace → Vulnérabilité → Actif → Impact. Calculate Probabilité and Risque.

5. **Treatment decision:** You identify a risk with P=2, I=4, R=8. Your budget is limited. Should you:
   - Implement full mitigation ($50k, reduces R to 2)?
   - Transfer to insurance ($10k/year, covers financial loss)?
   - Accept and monitor?
     Justify your choice.

6. **Risk matrix:** Plot these scenarios on a risk matrix:
   - Phishing attack: P=3, I=2
   - Datacenter fire: P=1, I=4
   - Weak password compromise: P=4, I=3

---

### Transfer Questions

7. **Methodology selection:** You're a security consultant for three clients:
   - French government agency
   - Startup with 10 employees
   - Global bank
     Which risk methodology (EBIOS, OCTAVE, ISO 27005, or hybrid) would you recommend for each? Why?

8. **Cascading risk:** Think of a real incident (e.g., SolarWinds supply chain attack). Map the cascading risks. How did one initial compromise lead to multiple downstream risks?

9. **Quantitative risk:** A server has ALE = $50,000. Mitigation costs $30,000 upfront + $5,000/year maintenance. Is mitigation justified? Calculate ROI over 3 years.

10. **Risk vs. compliance:** Your risk analysis shows a "Low" risk, but a regulation (GDPR, PCI-DSS) mandates a control. Do you implement it? How does compliance interact with risk-based decision-making?

---

## References

### Primary Sources

- **Course:** IFT2830 - Sécurité des systèmes informatiques (UdeM)
  Lectures: [2026-01-19 Gouvernance](../../../05_references/course-materials/IFT2830_course-materials/notes/2026-01-19_Gouvernance,%20stratégie%20et%20politique%20de%20sécurité.md), [2026-01-26 L'analyse du risque](../../../05_references/course-materials/IFT2830_course-materials/notes/2026-01-26_L'analyse%20du%20risque.md)

### Standards & Frameworks

- **ISO 27005:2022** — Information Security Risk Management
- **NIST SP 800-30** — Guide for Conducting Risk Assessments
- **ISO 31000:2018** — Risk Management — Guidelines (generic, not IT-specific)

### Methodologies

- **EBIOS Risk Manager** — ANSSI (France), [www.ssi.gouv.fr](https://www.ssi.gouv.fr)
- **MEHARI** — CLUSIF, [www.clusif.fr](https://www.clusif.fr)
- **OCTAVE** — Carnegie Mellon SEI, [resources.sei.cmu.edu](https://resources.sei.cmu.edu)
- **Risk IT** — ISACA, [www.isaca.org](https://www.isaca.org)

### Academic Papers

- Pfleeger, S. L., & Cunningham, R. K. (2010). "Why Measuring Security Is Hard." _IEEE Security & Privacy_, 8(4), 46-54.
- Jouini, M., Rabai, L. B. A., & Aissa, A. B. (2014). "Classification of Security Threats in Information Systems." _Procedia Computer Science_, 32, 489-496.

### Real-World Incidents

- **Target breach (2013)** — Poor risk analysis of HVAC vendor access
- **Equifax breach (2017)** — Unpatched vulnerability (missed risk scenario)
- **Colonial Pipeline (2021)** — Ransomware, poor backup strategy

---

## Related Content

### Theory Modules

- **Previous:** [CIA Triad](cia-triad.md) — Understanding what you're protecting
- **Next:** [Security Governance](security-governance.md) — Organizational risk management
- **Related:** [Threat Modeling Basics](threat-modeling-basics.md) — Identifying threats

### Examples

- [Risk Analysis Worksheet](../../../02_examples/00-foundations/risk-analysis-worksheet/) — Practical risk assessment template
- [E-commerce Risk Scenario](../../../02_examples/00-foundations/ecommerce-risk-scenario/) — Full worked example

### Exercises

- [Risk Scenario Builder](../../../03_exercises/00-foundations/risk-scenario-builder/) 🟢 — Practice constructing scenarios
- [Risk Matrix Practice](../../../03_exercises/00-foundations/risk-matrix-practice/) 🟡 — Calculate and prioritize risks
- [Risk Treatment Decision](../../../03_exercises/00-foundations/risk-treatment-decision/) 🟡 — Choose appropriate treatments

### Tools & Resources

- **Risk Matrix Generator:** `04_resources/tools/risk-analysis/risk-matrix-generator.xlsx`
- **Risk Register Template:** `04_resources/tools/risk-analysis/risk-register-template.md`

---

## Personal Insights & Notes

### Study Notes

_Record your observations, "aha" moments, and connections here._

**Example:**

- "The median(C, O, M) formula for probability makes sense — the 'bottleneck' factor limits overall probability."
- "Risk analysis is not about eliminating all risk — it's about prioritizing where to invest."

---

### Real-World Connections

_Link this concept to incidents, news, or work experience._

**Example:**

- "Target breach — vendor had high Opportunity (network access) despite low Motivation."

---

### Questions & Confusion

_Track what's unclear or needs deeper investigation._

**Example:**

- "How do you estimate ARO (Annual Rate of Occurrence) when you have no historical data?"

---

### Exam/Interview Prep

_Key points to remember for assessments._

**Exam focus (IFT2830):**

- Risk formula: R = P × I
- Probability: P = median(Capacité, Opportunité, Motivation)
- Four risk treatments: Réduction, Acceptation, Transfert, Élimination
- French terminology

**Interview talking points:**

- "Risk analysis enables risk-based prioritization of security investments."
- "Methodologies (EBIOS, MEHARI, OCTAVE) differ in approach but all follow: Identify → Assess → Treat → Monitor."

---

## Change Log

| Date       | Change                        | Reason                                                              |
| ---------- | ----------------------------- | ------------------------------------------------------------------- |
| 2026-02-16 | Created module                | Initial theory module based on IFT2830 lectures                     |
| 2026-02-16 | Added risk methodologies      | Comprehensive coverage of EBIOS, MEHARI, OCTAVE, Risk IT, ISO 27005 |
| 2026-02-16 | Added worked examples         | E-commerce scenario with SQL injection, insider, ransomware         |
| 2026-02-16 | Integrated French terminology | Bilingual support throughout                                        |
