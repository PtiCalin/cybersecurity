# DoS and DDoS Attacks — Attaques par Déni de Service

| Property          | Value                                                                                        |
| ----------------- | -------------------------------------------------------------------------------------------- |
| **Topic**         | Denial of Service / Déni de Service                                                          |
| **Domain**        | 02-network-security                                                                          |
| **Difficulty**    | 🟡 Intermediate                                                                              |
| **Prerequisites** | [CIA Triad (Availability)](../00-foundations/cia-triad.md), TCP/IP basics, network protocols |
| **Learning Time** | 90-120 minutes                                                                               |
| **Status**        | ✅ Complete                                                                                  |

---

## Review Schedule

- [ ] Day 2 — First review after initial study
- [ ] Week 1 — Consolidation review
- [ ] Month 1 — Long-term retention check
- [ ] Month 3 — Mastery verification

---

## Quick Summary

**What:** Denial of Service (DoS) attacks overwhelm systems, networks, or services to make them unavailable to legitimate users.

**Offensive:** Attackers exploit protocol weaknesses, resource limitations, and amplification mechanisms to exhaust system capacity.
**Defensive:** Defenders implement rate limiting, traffic filtering, overprovisioning, and distributed architectures to maintain availability.

**Why it matters:** DoS/DDoS attacks are the #1 threat to **availability** (the A in CIA). They're easy to launch, hard to prevent, and can cost millions in downtime. Unlike confidentiality or integrity breaches, DoS attacks are immediately visible to users and customers.

---

## Prerequisites

**Required knowledge:**

- [CIA Triad - Availability](../00-foundations/cia-triad.md) — Understanding what availability means
- TCP/IP networking basics (TCP handshake, UDP, IP packets)
- Client-server architecture

**Quick check:** Can you explain the TCP three-way handshake (SYN → SYN-ACK → ACK)? If yes, you're ready.

---

## Layer 1 — Intuition

Think of a DoS attack like blocking the entrance to a popular restaurant:

🚪 **DoS (Denial of Service)** = One person standing in the doorway, blocking everyone
👥 **DDoS (Distributed DoS)** = 100 people standing in all doorways, blocking everyone

**Restaurant (Server):**

- Has limited capacity (tables, staff)
- Can serve legitimate customers under normal load
- Overwhelmed when all capacity is consumed by attackers

**Customers (Legitimate Users):**

- Cannot enter (connect)
- Cannot be served (get service)
- Experience "service unavailable" (timeout, error)

**Attack goal:** Exhaust resources (bandwidth, connections, CPU, memory) so legitimate users are denied service.

---

## Layer 2 — Formal Definitions

### Core DoS Concepts

#### DoS (Denial of Service / Déni de Service)

**Definition:** An attack that prevents legitimate users from accessing a system, network, or service by exhausting its resources.

**Mechanism:** Single source overwhelms target.

**Target resources:**

- **Bandwidth (Bande passante):** Network capacity (Mbps/Gbps)
- **Connections (Connexions):** TCP connection slots, file descriptors
- **CPU/Memory (Processeur/Mémoire):** Computational resources
- **Application logic (Logique applicative):** Slow database queries, algorithmic complexity

**French term:** _Déni de Service (DoS)_

---

#### DDoS (Distributed Denial of Service / Déni de Service Distribué)

**Definition:** A DoS attack launched from multiple sources simultaneously.

**Mechanism:** Many compromised machines (botnet) coordinate to overwhelm target.

**Key difference from DoS:**

- **Volume:** 1000× more traffic
- **Mitigation difficulty:** Cannot block a single IP
- **Coordination:** Requires botnet infrastructure

**French term:** _Déni de Service Distribué (DDoS)_

---

#### Botnet

**Definition:** A network of compromised machines (bots/zombies) controlled by an attacker (botmaster).

**Purpose:** Launch coordinated DDoS attacks.

**Examples:** Mirai, Zeus, Emotet

**French term:** _Botnet_ (also _Réseau de machines zombies_)

---

### DoS/DDoS Attack Types

#### 1. Saturation (Bandwidth Exhaustion / Saturation de Bande Passante)

**Mechanism:** Flood the target with massive volume of traffic, consuming all available bandwidth.

**Effect:** Network pipes are full; legitimate traffic cannot reach the target.

**Examples:**

- **UDP Flood:** Send millions of UDP packets to random ports
- **ICMP Flood (Ping Flood):** Overwhelm with ICMP Echo Requests
- **HTTP Flood:** Massive HTTP GET/POST requests

**French term:** _Saturation_

---

#### 2. Exploitation (Protocol/Resource Exploitation)

**Mechanism:** Exploit protocol weaknesses or resource limitations to exhaust system capacity with relatively low traffic volume.

**Effect:** System resources (connections, CPU, memory) are exhausted, even with moderate bandwidth usage.

**Examples:**

- **SYN Flood:** Exploit TCP handshake
- **Slowloris:** Keep connections alive indefinitely
- **Ping of Death:** Malformed packets crash systems

**French term:** _Exploitation_

---

### Attack Techniques

#### SYN Flood

**Mechanism:** Exploit TCP three-way handshake by sending SYN packets without completing the handshake.

**Normal TCP Handshake:**

```
Client → Server: SYN (request connection)
Server → Client: SYN-ACK (acknowledge, allocate resources)
Client → Server: ACK (confirm, connection established)
```

**SYN Flood Attack:**

```
Attacker → Server: SYN (spoofed source IP)
Server → ??? : SYN-ACK (sent to fake IP, no response)
[Server waits for ACK, connection remains "half-open"]
[Repeat 10,000 times → connection queue full]
```

**Effect:** Server's **connection queue** (file of semi-open connections) fills up. New legitimate connections are rejected.

**French terms:** _Inondation SYN_, _Connexion semi-ouverte_ (half-open connection), _File de connexions_

---

#### Amplification

**Mechanism:** Send small requests with **spoofed source IP** to public services that respond with much larger responses to the victim.

**Formula:**
**Amplification Factor = Response Size / Request Size**

**Example: DNS Amplification**

```
Attacker → Open DNS Resolver:  Request 60 bytes  (spoofed victim IP)
Open DNS Resolver → Victim:    Response 3000 bytes
Amplification Factor = 3000 / 60 = 50×
```

**Popular amplification protocols:**
| Protocol | Default Port | Amplification Factor |
|----------|--------------|----------------------|
| DNS | 53/UDP | 28-54× |
| NTP | 123/UDP | 556× |
| SSDP | 1900/UDP | 30× |
| Memcached | 11211/UDP | 10,000-51,000× |

**Why it works:**

- Attacker sends 1 Mbps of requests
- Victim receives 50+ Mbps of responses
- Attacker's bandwidth is multiplied

**French term:** _Amplification_

---

#### Reflection

**Mechanism:** Combine amplification with **IP spoofing** to hide the attacker's identity.

**Process:**

1. Attacker spoofs victim's IP address
2. Attacker sends requests to public servers (DNS, NTP, etc.)
3. Servers respond to victim's IP (they think the victim made the request)
4. Victim is flooded with unsolicited responses

**Effect:**

- Victim receives massive traffic
- Attacker's IP is hidden (responses go to victim, not attacker)
- Public servers act as "reflectors"

**French term:** _Reflection_ (also _Attaque par réflexion_)

---

#### Ping of Death

**Mechanism:** Send malformed or oversized ICMP packets that crash or freeze the target system.

**Classic example:** Send ICMP packet larger than maximum IP packet size (65,535 bytes) using IP fragmentation.

**Effect:** Operating system's TCP/IP stack crashes due to buffer overflow or reassembly error.

**Modern relevance:** Patched in most modern systems, but variations still exist.

**French term:** _Ping de la mort_

---

### Network Protocol Concepts

#### IP Fragmentation

**Definition:** Splitting large IP packets into smaller fragments to fit network MTU (Maximum Transmission Unit).

**Normal use:** Router fragments packet, destination reassembles.

**DoS exploitation:**

- Send fragments with overlapping offsets
- Send fragments that don't reassemble correctly
- Exhaust reassembly buffers

**French terms:** _Fragmentation IP_, _Offset IP_

---

#### IP Spoofing (Usurpation d'adresse IP)

**Definition:** Forging the source IP address in a packet to hide the attacker's identity or impersonate another system.

**Mechanism:**

- Attacker modifies the "Source IP" field in the IP header
- Victim (or intermediate server) responds to the spoofed IP

**Use in DoS:**

- **SYN Flood:** Spoof random IPs so SYN-ACKs go nowhere
- **Amplification:** Spoof victim's IP so responses flood the victim

**Limitation:** Attacker cannot receive responses (blind attack).

**French term:** _Usurpation d'adresse IP_

---

#### TCP Sequence Numbers

**Definition:** Unique numbers assigned to each byte in a TCP stream to ensure reliable, ordered delivery.

**Mechanism:**

- Initial Sequence Number (ISN) is chosen during handshake
- Each byte sent increments the sequence number

**DoS relevance:**

- **Blind attack:** Attacker spoofs victim's IP but cannot see responses (doesn't know sequence numbers)
- **SYN Cookies:** Defense mechanism that encodes connection state in sequence number

**French term:** _Numéros de séquence TCP_

---

#### TTL (Time To Live / Durée de Vie)

**Definition:** A field in the IP header indicating how many hops (routers) a packet can traverse before being discarded.

**Purpose:** Prevent packets from circulating forever in routing loops.

**Mechanism:**

- Initial TTL value (e.g., 64)
- Each router decrements TTL by 1
- TTL reaches 0 → packet discarded

**DoS relevance:**

- Can be used to fingerprint OS (different OSes use different initial TTL values)
- Low TTL packets may be used to probe network topology

**French term:** _Durée de vie (TTL)_

---

## Layer 3 — Worked Examples

### Example 1: SYN Flood Attack on Web Server

**Scenario:** E-commerce website hosted on single web server with connection limit of 1,000 simultaneous TCP connections.

#### Attack Steps:

**Phase 1: Reconnaissance**

- Attacker discovers web server at `192.0.2.100:443` (HTTPS)
- Server advertises max 1,000 connections

**Phase 2: SYN Flood Execution**

```
Attacker generates SYN packets with:
- Destination: 192.0.2.100:443
- Source: Spoofed random IPs (e.g., 198.51.100.X)
- Rate: 5,000 SYN packets/second
```

**Phase 3: Server Impact**

```
Server receives SYN → allocates connection slot → sends SYN-ACK → waits for ACK
SYN-ACK is sent to spoofed IP (non-existent) → no ACK received
Connection remains "half-open" in queue
After 1,000 half-open connections → connection queue full
New legitimate connections → REJECTED (RST or timeout)
```

**Timeline:**

- **T=0s:** Attack starts, 5,000 SYN/sec
- **T=0.2s:** 1,000 connections saturated (1,000 / 5,000 = 0.2s)
- **T=0.2s+:** Legitimate users see "Connection refused" or timeout

#### Defensive Countermeasures:

| Defense                       | Mechanism                                                                   | Effectiveness                                 |
| ----------------------------- | --------------------------------------------------------------------------- | --------------------------------------------- |
| **SYN Cookies**               | Encode connection state in ISN; don't allocate resources until ACK received | ✅ Eliminates half-open queue                 |
| **Rate Limiting**             | Limit SYN packets per source IP (e.g., 10 SYN/sec)                          | ⚠️ Partially effective (attacker rotates IPs) |
| **Firewall SYN Proxy**        | Firewall completes handshake on behalf of server                            | ✅ Effective but adds latency                 |
| **Increase connection limit** | Overprovisioning (10,000 connections instead of 1,000)                      | ⚠️ Delays exhaustion, doesn't prevent         |
| **SYN-ACK timeout reduction** | Reduce wait time from 30s to 3s                                             | ⚠️ Helps, but not sufficient alone            |

**Real incident:** GitHub (2018) — 1.35 Tbps DDoS using Memcached amplification (not SYN flood, but similar resource exhaustion).

---

### Example 2: DNS Amplification Attack

**Scenario:** Attacker wants to DDoS victim `203.0.113.50` with only 10 Mbps of attack bandwidth.

#### Attack Amplification Calculation:

**Step 1: Find open DNS resolvers**

- Shodan/Censys reveals 10,000 open DNS resolvers accepting recursive queries

**Step 2: Craft DNS request**

```
DNS Query:
- Query: ANY record for "example.com" (returns all DNS records)
- Request size: ~60 bytes
- Response size: ~3,000 bytes
- Amplification factor: 50×
```

**Step 3: Spoof victim's IP**

```
Attacker sends DNS request with:
- Source IP: 203.0.113.50 (victim)
- Destination: Open DNS resolver
- Payload: 60 bytes
```

**Step 4: DNS resolver responds**

```
DNS Resolver sends response with:
- Source: DNS resolver
- Destination: 203.0.113.50 (victim)
- Payload: 3,000 bytes (50× amplification)
```

**Step 5: Multiply by 10,000 resolvers**

```
Attacker bandwidth: 10 Mbps
Attack traffic to victim: 10 Mbps × 50 (amplification) = 500 Mbps
With 10,000 resolvers: potentially 5+ Gbps
```

**Impact on victim:**

- Victim's 1 Gbps network link is saturated
- Legitimate traffic cannot reach victim
- Website becomes unreachable

#### Defensive Countermeasures:

| Defense                        | Mechanism                                            | Effectiveness                               |
| ------------------------------ | ---------------------------------------------------- | ------------------------------------------- |
| **Upstream filtering**         | ISP/transit provider filters spoofed IPs (BCP 38)    | ✅ Prevents IP spoofing at source           |
| **DDoS mitigation service**    | Cloudflare, Akamai, AWS Shield absorb attack traffic | ✅ High capacity, distributed absorption    |
| **Rate limiting**              | Limit inbound DNS responses (victim side)            | ⚠️ Can block legitimate DNS traffic         |
| **Disable DNS open recursion** | Configure DNS servers to reject external queries     | ✅ Removes amplification vector (proactive) |
| **Anycast routing**            | Distribute load across multiple locations            | ✅ Dilutes attack traffic                   |

**Real incident:** Dyn DNS (2016) — Mirai botnet DDoS using DNS and IoT devices, took down Twitter, Netflix, Reddit.

---

### Example 3: Application-Layer DoS (HTTP Flood)

**Scenario:** Attacker targets e-commerce search function that triggers expensive database queries.

#### Attack Strategy:

**Phase 1: Identify expensive endpoint**

```
Normal request: GET /products?category=shoes (cheap query)
Expensive request: GET /search?q=* (full-text search across 1M products, 5s query time)
```

**Phase 2: Launch low-rate application attack**

```
Botnet of 1,000 nodes sends:
- 10 requests/second per node
- Total: 10,000 requests/second to /search endpoint
- Each request ties up database for 5 seconds
```

**Phase 3: Resource exhaustion**

```
Database connections: 100 max
Attack requests: 10,000/sec × 5s = 50,000 concurrent queries needed
Result: Database connection pool exhausted in <1 second
Legitimate users: Cannot search or browse products
```

#### Impact:

- **Bandwidth:** Minimal (HTTP requests are small)
- **Connection saturation:** No (HTTP Keep-Alive reuses connections)
- **Application logic:** Completely overwhelmed

**Why traditional DoS defenses fail:**

- Not a volumetric attack (low bandwidth)
- Requests look "legitimate" (valid HTTP GET)
- Cannot be stopped by rate limiting alone (distributed botnet)

#### Defensive Countermeasures:

| Defense                            | Mechanism                                                  | Effectiveness                               |
| ---------------------------------- | ---------------------------------------------------------- | ------------------------------------------- |
| **Query optimization**             | Cache search results, add indexes, limit wildcard searches | ✅ Reduces resource consumption per request |
| **Rate limiting (per user)**       | Limit search requests to 10/min per IP/session             | ✅ Slows attack, but botnet can rotate IPs  |
| **CAPTCHA**                        | Require human verification for expensive operations        | ✅ Blocks automated bots                    |
| **Web Application Firewall (WAF)** | Detect and block malicious patterns (e.g., `q=*`)          | ✅ Signatures for known bad patterns        |
| **Queueing/Circuit breaker**       | Reject requests when queue is full, return HTTP 503        | ⚠️ Degrades service for all users           |

**Real incident:** Cloudflare (2020) — Application-layer DDoS targeting WordPress sites with expensive query strings.

---

## Layer 4 — Edge Cases, Nuances, and Limitations

### Edge Case 1: Legitimate vs. Malicious Traffic

**Problem:** How do you distinguish between:

- **Legitimate traffic spike:** Product launch, viral social media post, Black Friday
- **DDoS attack:** Coordinated botnet flooding

**Challenge:**

- Both generate massive traffic
- Both may come from diverse IPs (global user base vs. botnet)
- Both may look "legitimate" at protocol level (valid HTTP requests)

**Indicators of DDoS (not definitive, but suspicious):**

- **Sudden spike:** Traffic increases 1000× in seconds (legitimate growth is gradual)
- **Unusual geographic distribution:** Traffic from countries you don't serve
- **Repetitive patterns:** Same User-Agent, same query strings, same request rate
- **Low engagement:** High requests/sec but no meaningful interaction (no clicks, no purchases)
- **Protocol anomalies:** Malformed headers, unusual HTTP methods

**Defense strategy:**

- **Behavioral analysis:** Baseline normal traffic patterns
- **CAPTCHA challenges:** Verify humans during spikes
- **Gradual filtering:** Start lenient, increase strictness as attack persists

---

### Edge Case 2: Amplification Factor Arms Race

**Evolution:**

- **2000s:** ICMP/UDP floods (no amplification, 1:1 ratio)
- **2010s:** DNS amplification (50× factor)
- **2014:** NTP amplification (556× factor)
- **2018:** Memcached amplification (51,000× factor)

**Trend:** Attackers seek higher amplification factors to maximize damage with minimal bandwidth.

**Memcached case study:**

```
Request:  UDP packet to Memcached server, 15 bytes ("stats" command)
Response: Up to 1 MB of cached data
Amplification: 1,000,000 / 15 = 66,666×
```

**Defensive implication:**

- **Proactive mitigation:** Secure all UDP services (disable public access, firewall rules)
- **BCP 38 enforcement:** ISPs must filter spoofed IPs at the edge
- **Continuous monitoring:** New amplification vectors emerge constantly

---

### Edge Case 3: Collateral Damage in DDoS Mitigation

**Problem:** DDoS defenses can harm legitimate users.

**Examples:**

1. **CAPTCHA fatigue:** Legitimate users frustrated by constant verification
2. **Geo-blocking:** Users from certain countries blocked entirely (even legitimate ones)
3. **Aggressive rate limiting:** Legitimate power users hit rate limits
4. **CDN caching:** Dynamic content (user dashboards, search) degraded or broken

**Trade-off:**

- **Security vs. Usability:** Strict defenses → secure but unusable site
- **Availability vs. Functionality:** Keep site up but degrade features

**Best practice:**

- **Tiered defenses:** Start lenient, escalate gradually
- **Whitelists:** Verified users/IPs bypass strict defenses
- **Communication:** Inform users of ongoing attack and temporary measures

---

### Edge Case 4: Economic DoS (Ransom DDoS)

**Evolution:** Attackers no longer just disrupt; they **extort**.

**Ransom DDoS workflow:**

1. Attacker sends ransom note: "Pay $50,000 in Bitcoin or we DDoS your site"
2. Attacker launches "demo" DDoS (10-minute burst) to prove capability
3. Victim has 24-48 hours to pay
4. If unpaid: Full-scale multi-day DDoS attack

**Prevalence:** Increased 2020-2024, targeting e-commerce, gaming, financial services.

**Victim's dilemma:**

- **Pay:** Encourages future attacks, no guarantee attacker stops
- **Don't pay:** Suffer downtime, revenue loss, reputation damage

**Defensive strategy:**

- **Proactive DDoS mitigation:** Have defenses in place _before_ ransom demand
- **Don't negotiate:** Paying encourages attackers
- **Law enforcement:** Report to authorities (FBI, Europol)

**Real incidents:**

- **Armada Collective (2016):** Fake ransom DDoS group (claimed capability, never attacked)
- **REvil ransomware (2021):** Combined ransomware with DDoS extortion

---

### Limitation 1: DDoS Defenses Are Expensive

**Cost factors:**

- **DDoS mitigation services:** $1,000-$10,000/month (Cloudflare, Akamai, AWS Shield Advanced)
- **Overprovisioning:** 10× bandwidth capacity "just in case"
- **Opportunity cost:** Engineering time spent on DDoS defenses vs. features

**Reality:** Most small/medium businesses cannot afford enterprise-grade DDoS protection.

**Alternative approaches:**

- **Cloud-native architecture:** Use CDN + auto-scaling to absorb traffic (AWS, Google Cloud)
- **Community defenses:** Cloudflare offers free tier for basic DDoS protection
- **Insurance:** Cyber insurance may cover downtime losses

---

### Limitation 2: Distributed Defenses Create Complexity

**Modern DDoS defense:** Distributed architecture (CDN, Anycast, multi-region)

**Complexity challenges:**

- **Latency:** Additional hops through CDN add ~20-50ms
- **Debugging:** Hard to trace issues across distributed nodes
- **Costs:** Multiple regions = higher infrastructure costs
- **Configuration drift:** Inconsistent settings across regions

**Trade-off:** Resilience vs. operational complexity.

---

## Active Recall Prompts

### Understanding Questions

1. **DoS vs. DDoS:** Explain the difference between DoS and DDoS. Why is DDoS harder to defend against?

2. **SYN Flood mechanics:** Without looking, describe the TCP three-way handshake. How does a SYN flood exploit this?

3. **Amplification formula:** What is the amplification factor? Calculate the factor if an attacker sends 100-byte requests that trigger 5,000-byte responses.

---

### Application Questions

4. **Defense selection:** Your web application is under SYN flood attack. You have these options:
   - Enable SYN cookies
   - Increase connection limit from 1,000 to 10,000
   - Deploy CAPTCHA on all pages
     Which is most effective? Why?

5. **Attack cost:** An attacker wants to DDoS a victim with 10 Gbps of traffic. Using DNS amplification (50× factor), how much bandwidth does the attacker need? How many bots if each bot has 10 Mbps?

6. **CIA mapping:** For each attack, identify which CIA property is violated:
   - SYN flood
   - DNS amplification
   - Slowloris (keeps connections open)
   - HTTP flood targeting search function

---

### Transfer Questions

7. **Real-world incident:** Research the **Mirai botnet** (2016). What was the amplification technique? What was the scale? How was it eventually mitigated?

8. **Offensive perspective:** You're a pentester hired to test a company's DDoS resilience. Design three distinct DoS tests targeting:
   - Network layer (bandwidth)
   - Transport layer (connections)
   - Application layer (logic)

9. **Defensive architecture:** Design a DDoS-resistant architecture for an e-commerce site. Include:
   - CDN/WAF layer
   - Auto-scaling application tier
   - Database protection
   - Cost considerations

10. **Legal/ethical question:** Is launching a DoS attack against your own infrastructure (for testing) legal? What precautions should you take?

---

## References

### Primary Sources

- **Course:** IFT2830 - Sécurité des systèmes informatiques (UdeM)
  Lectures: [2026-02-09 Techniques d'attaque](../../../05_references/course-materials/IFT2830_course-materials/notes/2026-02-09_Techniques%20d'attaque.md)

### Standards & Protocols

- **RFC 793** — Transmission Control Protocol (TCP)
- **RFC 4987** — TCP SYN Flooding Attacks and Common Mitigations
- **BCP 38 (RFC 2827)** — Network Ingress Filtering: Defeating Denial of Service Attacks

### Academic Papers

- Mirkovic, J., & Reiher, P. (2004). "A Taxonomy of DDoS Attack and DDoS Defense Mechanisms." _ACM SIGCOMM Computer Communication Review_, 34(2), 39-53.
- Rossow, C. (2014). "Amplification Hell: Revisiting Network Protocols for DDoS Abuse." _Network and Distributed System Security Symposium (NDSS)_.

### Real-World Incidents

- **Mirai botnet (2016)** — 1 Tbps attack on Dyn DNS using IoT devices
- **GitHub (2018)** — 1.35 Tbps Memcached amplification attack
- **AWS (2020)** — 2.3 Tbps DDoS attack, largest on record

### Tools & Resources

- **DDoS testing tools:** hping3, LOIC (Low Orbit Ion Cannon) — **use only in authorized lab environments**
- **DDoS simulation platforms:** Cloudflare's DDoS simulator, AWS Shield test

---

## Related Content

### Theory Modules

- **Previous:** [CIA Triad - Availability](../00-foundations/cia-triad.md) — Understanding availability
- **Next:** [IP Spoofing](ip-spoofing.md) — Address forgery techniques
- **Related:** [Firewall Fundamentals](firewall-fundamentals.md) — Network defense

### Examples

- [SYN Flood Lab](../../../02_examples/02-network-security/syn-flood-lab/) — Hands-on SYN flood simulation
- [DNS Amplification Demo](../../../02_examples/02-network-security/dns-amplification-demo/) — Amplification mechanics

### Exercises

- [DDoS Defense Design](../../../03_exercises/02-network-security/ddos-defense-design/) 🟡 — Architect a DDoS-resistant system
- [Amplification Calculator](../../../03_exercises/02-network-security/amplification-calculator/) 🟢 — Practice amplification math
- [Attack Traffic Analysis](../../../03_exercises/02-network-security/attack-traffic-analysis/) 🟠 — Distinguish attack from legitimate traffic

### Tools & Resources

- **DDoS Mitigation Comparison:** `04_resources/tools/network-security/ddos-mitigation-comparison.md`
- **Attack Flowcharts:** `04_resources/tools/network-security/dos-attack-flowcharts/`

---

## Personal Insights & Notes

### Study Notes

_Record your observations, "aha" moments, and connections here._

**Example:**

- "SYN cookies are clever — they encode connection state in the ISN, eliminating the need for a half-open queue."
- "Amplification attacks are essentially 'bandwidth multiplication' — attacker's 10 Mbps becomes victim's 500 Mbps."

---

### Real-World Connections

_Link this concept to incidents, news, or work experience._

**Example:**

- "GitHub 2018 attack — Memcached amplification, 51,000× factor. Takeaway: Always secure UDP services."

---

### Questions & Confusion

_Track what's unclear or needs deeper investigation._

**Example:**

- "How does Anycast routing actually distribute attack traffic? Need to research BGP mechanics."

---

### Exam/Interview Prep

_Key points to remember for assessments._

**Exam focus (IFT2830):**

- SYN flood mechanics (three-way handshake, half-open connections)
- Amplification formula: Response Size / Request Size
- French terms: Déni de Service, Inondation SYN, Saturation, Amplification, Reflection
- Defenses: SYN cookies, rate limiting, BCP 38

**Interview talking points:**

- "DoS targets availability exclusively — no confidentiality or integrity breach."
- "Modern DDoS defenses require distributed architecture: CDN, Anycast, overprovisioning."
- "Application-layer DoS (e.g., expensive queries) bypasses traditional network defenses."

---

## Change Log

| Date       | Change                              | Reason                                                           |
| ---------- | ----------------------------------- | ---------------------------------------------------------------- |
| 2026-02-16 | Created module                      | Initial theory module based on IFT2830 attack techniques lecture |
| 2026-02-16 | Added amplification protocols table | Comprehensive coverage of DNS, NTP, SSDP, Memcached              |
| 2026-02-16 | Added worked examples               | SYN flood, DNS amplification, HTTP flood scenarios               |
| 2026-02-16 | Integrated French terminology       | Bilingual support with technical terms                           |
| 2026-02-16 | Added real-world incidents          | Mirai, GitHub, AWS record-breaking attacks                       |
