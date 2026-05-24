#  Faculty Development Program 2026 - BIT Mesra
## Session 07:  Cyber Resiliency of Legacy Power Networks

---

##  Speaker Details

| Field | Details |
|---|---|
| **Name** | Dr. Rajesh Gupta |
| **Designation** | Professor, Department of Electrical Engineering |
| **Institution** | Motilal Nehru National Institute of Technology (MNNIT), Allahabad, Prayagraj |
| **Email** | rajeshgupta@mnnit.ac.in |
| **Google Scholar Citations** | 3,158+ |
| **IEEE Membership** | Senior Member (since 2011), PES, IES, PELS, IAS |

### Academic Background — Another BIT Mesra Alumnus!

| Degree | Year | Institution |
|---|---|---|
| B.E. (Electrical Engineering) | 1993 | Madan Mohan Malviya Engineering College, Gorakhpur |
| **M.E. (Electrical Engineering — Control Systems)** | **1995** | **Birla Institute of Technology, Mesra, Ranchi** ← Your institution! |
| Ph.D. | 2007 | IIT Kanpur — *"Characterization and Design of Inverter Switching Control for Distribution System Compensation"* |

> **Dr. Rajesh Gupta is ALSO a BIT Mesra M.E. alumnus — just like Dr. Lalitesh Kumar (Session 6)!**

### Career History

| Period | Institution | Role |
|---|---|---|
| 1995–1996 | I.E.T. Sitapur Road, Lucknow | Lecturer |
| 1996–1999 | G.B. Pant Engineering College, Pauri (Garhwal) | Lecturer |
| 1999–2001 | MNREC, Allahabad | Lecturer |
| 2001–2006 | MNNIT, Allahabad | Senior Lecturer |
| 2006–2009 | MNNIT, Allahabad | Assistant Professor |
| 2009–2018 | MNNIT, Allahabad | Associate Professor |
| **2018–Present** | **MNNIT, Allahabad** | **Professor** |

### Research Areas
- Power Electronics Converters
- Control in Power Electronics
- Multilevel Inverters
- Bidirectional Converters
- **Power Quality & Grid Interface**
- **Microgrid, Hybrid AC/DC Systems**
- Solar and Wind Power Conversion
- Energy Storage, Electric Vehicles
- **Cyber-Physical System Security** (today's focus)
- FACTS (Flexible AC Transmission Systems)

### Awards & Recognition
- **Outstanding Section Volunteer Award** — IEEE Uttar Pradesh Section, 2014
- **POSOCO Power System Award (2014, 2015, 2016)** — Two Ph.D. students and two M.Tech. students guided by Dr. Gupta placed in top 25 nationally
- **1st Prize, VI MANTRA Contest 2006** — Best solution in Computer-Based Measurement and Automation
- **9 Ph.D. students supervised, 42 M.Tech. students supervised**
- IEEE Conference chair at IECON 2020/2023, PEDES 2018/2020, TENCON 2014, ISIE 2012/2014

### Teaching Courses (Directly Relevant Today)
- Advanced Power Electronics
- FACTS (Flexible AC Transmission Systems)
- Digital Control
- Active Power Conditioning
- Renewable Energy and Distributed Generation

---

##  Topic Deep Dive: Cyber Resiliency of Legacy Power Networks

This topic sits at the **intersection of two worlds**: decades-old power infrastructure (legacy systems) and modern cyber threats. It is arguably the most urgent cybersecurity challenge in critical infrastructure today.

---

### 1. What Are "Legacy Power Networks"?

**Legacy systems** in the power sector refer to equipment and networks installed **10–40+ years ago**, designed purely for operational reliability — **not for cybersecurity**.

#### Characteristics of Legacy Power Infrastructure:

| Feature | Legacy System | Modern Smart Grid |
|---|---|---|
| **Protocols** | Modbus (1979), DNP3 (1990), Profibus (1989) | IEC 61850, XMPP, IEC 62351 (secure) |
| **Authentication** | None or minimal | Certificate-based, PKI |
| **Encryption** | None — cleartext transmission | TLS, AES-256 |
| **Connectivity** | Mostly air-gapped (isolated) | Internet-connected, cloud-integrated |
| **Update cycle** | 20–30 year hardware lifecycle | Regular software patching |
| **Design intent** | Operational continuity only | Operational + security |
| **Remote access** | Rarely | Widespread (cloud SCADA) |

**The Core Problem:** Legacy systems were designed in an era when the power grid was **physically isolated** from public networks. Digitization and smart grid integration have **eroded this air gap** while the underlying hardware and protocols remain unchanged.

---

### 2. The Legacy Protocol Vulnerability Problem

#### Modbus (created 1979)
- Developed by Modicon for PLC communication
- Used in: RTUs, meters, protection relays in distribution systems
- **Security gaps**: No authentication, no encryption, no source verification
- Any device on the network can send a Modbus command to any other — no questions asked
- An attacker who gains network access can **directly command breakers, valves, or actuators**

#### DNP3 (Distributed Network Protocol 3, created 1990)
- Developed for electric utilities — widely used in Indian grid SCADA systems
- Supports unsolicited messages from slave to master — creates **large remote attack surfaces**
- Original version: no encryption, no authentication
- DNP3-SA (Secure Authentication) was added in 2007 updates — but **most legacy deployments still run unauthenticated DNP3**
- Vulnerable to: MitM attacks, packet manipulation, master impersonation, replay attacks

#### IEC 60870-5 (Series)
- European counterpart to DNP3
- Similar security gaps in older implementations
- Used in Indian state transmission utility SCADA systems

#### ICCP / TASE.2
- Used for inter-utility (substation to control center) communication
- Legacy implementations lack modern cryptographic protections

> **Critical statistic**: SCADA systems prioritize operational continuity over security by architectural design — creating fundamental vulnerabilities when retrofitted with remote monitoring capabilities. Protocols like Modbus, DNP3, and Profibus were developed before internet standardization and employ minimal encryption and optional authentication.

---

### 3. What Is Cyber Resiliency? (vs. Cybersecurity)

These are related but distinct concepts:

| Concept | Focus | Assumption |
|---|---|---|
| **Cybersecurity** | Prevention — stop attacks from happening | Can be fully protected |
| **Cyber Resiliency** | Recovery — survive, adapt, and recover when attacks succeed | Assume breach will occur |

**Cyber Resiliency Framework (NIST SP 800-160 Vol. 2):**
1. **Anticipate** — Identify threats, model attack surfaces, assess vulnerabilities
2. **Withstand** — Maintain essential functions during a cyberattack
3. **Recover** — Restore full operational capability after an attack
4. **Adapt** — Update protections based on lessons learned

For **legacy power networks**, the goal shifts from "prevent all attacks" (impossible with aging hardware) to **"maintain critical power delivery even while under attack."**

---

### 4. Why Legacy Power Networks Are Prime Targets

#### Converging IT-OT Networks
- **IT** (Information Technology): Business networks, internet-facing, frequently patched
- **OT** (Operational Technology): SCADA, DCS, PLCs, RTUs — the legacy control systems
- Modern grid operations connect IT and OT for efficiency → the previously air-gapped OT network now has pathways to the internet
- Attackers use IT networks as **stepping stones** into OT/SCADA systems

#### The Asset Lifecycle Problem
- A typical **distribution transformer** has a 30–40 year operational life
- The **RTU (Remote Terminal Unit)** communicating with it may date from 2005 — running Windows XP or older
- Patching is impossible — the vendor stopped supporting the OS
- Replacing is too expensive — India has millions of such devices deployed

#### Scale of India's Exposure
- India's grid covers **1.4 million square kilometers** — 1,600+ substations at transmission level alone
- Smart meter rollout: ~250 million smart meters by 2025 — each is a network endpoint
- Distribution Automation (DA) connecting thousands of feeders — most using legacy SCADA
- **CERT-In** and **NCIIPC** have documented multiple intrusion attempts on Indian power utilities

---

### 5. Major Attack Vectors on Legacy Power Networks

#### A. False Command Injection
- Attacker gains access to the SCADA network
- Sends authenticated-looking Modbus or DNP3 commands to RTUs
- Commands: open circuit breakers, trip protection relays, change transformer tap positions
- Effect: **targeted blackouts, equipment damage**
- 2015 Ukraine attack used exactly this method — first known cyber-induced blackout

#### B. False Data Injection (FDIA) on State Estimation
- Manipulates sensor readings fed into the Energy Management System (EMS)
- EMS makes wrong dispatch and switching decisions
- Can overload transmission lines, cause voltage collapse
- **Stealthy** — bypasses bad data detection algorithms

#### C. Denial-of-Service on Control Channels
- Floods the SCADA communication network
- Control center loses visibility of substation status
- Operators fly blind — cannot respond to real grid disturbances
- In legacy systems with low-bandwidth serial communications, even small DoS can be devastating

#### D. Reconnaissance and Lateral Movement
- Attacker maps the OT network slowly over weeks/months
- Uses IT network access to move laterally into SCADA historian, then to control network
- **Patient, persistent** attacks by state actors (APTs — Advanced Persistent Threats)

#### E. Supply Chain Attacks on Legacy Hardware
- Malicious firmware in RTUs, IEDs (Intelligent Electronic Devices), protection relays
- Pre-positioned at hardware manufacturing or distribution stage
- Triggered remotely months or years after installation

---

### 6. Defense Strategies for Legacy Power Networks

The fundamental constraint: **You cannot patch legacy hardware**. Solutions must be **add-on (non-intrusive)** to avoid disrupting live grid operations.

#### A. Network Segmentation & Defense in Depth
- **Purdue Model / ISA-99**: Separates corporate IT, SCADA, and field device networks with strict controlled interfaces
- Industrial firewalls with **Deep Packet Inspection (DPI)** for Modbus/DNP3 — can detect anomalous commands without modifying existing devices
- **DMZ (Demilitarized Zone)**: Intermediate network between IT and OT — data flows one direction via data diode

#### B. Data Diode (Hardware Security)
- A **one-way hardware link** — data can only flow from OT to IT, never the reverse
- Physically impossible for an attacker to send commands from IT into OT through a data diode
- Used in highest-security substations and nuclear facilities
- Limitation: breaks bidirectional communication — operators lose ability to remote-control

#### C. Detect-and-Respond Strategy
- Add-on **intrusion detection system (IDS)** monitors all SCADA traffic passively
- Anomaly detection: flags unusual Modbus/DNP3 command patterns (e.g., a command to open 50 breakers simultaneously)
- Machine learning-based: learns normal operational patterns, alerts on deviations
- Does not modify existing legacy devices — purely a monitoring overlay

#### D. Protocol Tunneling & Encryption Wrappers
- Wrap legacy protocols (Modbus, DNP3) inside **secure VPN tunnels** that authenticate endpoints
- Implements TLS-level security without modifying the field devices themselves
- **DNP3-SA**: Cryptographic authentication extension — can be applied at SCADA master level even for some older RTUs

#### E. Moving Target Defense (MTD)
- Continuously changes network addresses, ports, and communication paths
- Confuses attackers during reconnaissance phase — makes the network topology a moving target
- Applied at the SCADA communication layer without changing underlying hardware

#### F. AI/ML-Based Anomaly Detection (Dr. Gupta's domain connection)
- Train models on normal grid operational patterns (load curves, switching sequences, seasonal patterns)
- **CNN + LSTM**: Detect simultaneous FDIA and DoS attacks in real-time SCADA streams
- **Digital Twin monitoring**: Parallel virtual model of the power network — detects divergence between physical and virtual states, indicating an attack or fault
- Can be deployed as an overlay on legacy SCADA without modifying field devices

#### G. Resilience-Oriented Switching
- Pre-designed **islanding and reconfiguration strategies** — when an attack is detected, automatically reconfigure the network to isolate the compromised section
- Maintain power supply to **critical loads** (hospitals, defense, water treatment) even during attack
- Tie-line switching validated on IEEE 33-bus and similar test systems

---

### 7. Cyber Resiliency Metrics for Power Networks

How do you **measure** resiliency? This is an active research area:

| Metric | Description |
|---|---|
| **Load Served Ratio (LSR)** | Fraction of total load still served during/after attack |
| **Recovery Time (RT)** | Time from attack detection to full restoration |
| **Resilience Triangle** | Area of performance degradation over time — smaller = more resilient |
| **CVSS Score** | Common Vulnerability Scoring System — rates severity of discovered vulnerabilities |
| **Attack Impact Index** | Combines attack probability, severity, and affected load |
| **Mean Time to Detect (MTTD)** | How quickly the attack is identified |
| **Mean Time to Respond (MTTR)** | How quickly response and isolation occurs |

Power distribution systems use the **CVSS framework** combined with complex network graph parameters — identifying critical nodes whose compromise most impacts the network.

---

### 8. India-Specific Context

- **Mumbai Blackout Investigation (2020)**: U.S. researchers linked a partial Mumbai grid disturbance to suspected Chinese state-sponsored intrusion into Maharashtra State Electricity Board's systems — later investigated but not conclusively proven by Indian agencies
- **CERT-In Alerts**: Multiple advisories issued to Indian power utilities about DNP3 and Modbus vulnerabilities
- **NCIIPC**: National Critical Information Infrastructure Protection Centre designates power grids as Category 1 critical infrastructure — highest protection priority
- **Regulatory Framework**: Central Electricity Authority (CEA) issued "Cyber Security Guidelines for Power Sector" in 2021 — mandatory baseline for all licensed utilities
- **Smart Meter Risk**: India's mass smart meter rollout creates 250 million new network endpoints — most using ZigBee or RF-based communication protocols with variable security implementations
- **AI for Grid Security**: NTPC and Power Grid Corporation of India are piloting AI-based anomaly detection on their SCADA systems

---

##  Questions to Ask 


1.
   > *"India's distribution grid has millions of RTUs and protection relays running legacy DNP3 or Modbus — replacement is economically infeasible. In your view, what is the single most effective add-on cyber resiliency measure that can be deployed at scale across India's distribution system without disrupting live grid operations or requiring hardware replacement?"*

2. > *"Your research background is in active power conditioning, FACTS, and distribution system compensation using inverter control. Given that today's grid-connected inverters (solar, ESS, EVs) are all digitally controlled and internet-accessible — do they represent a more dangerous attack surface than legacy SCADA RTUs, since they can inject real power disturbances if compromised?"*

3. > *"The Resilience Triangle metric captures performance degradation over time. For legacy power distribution networks under a coordinated cyber attack targeting multiple substations simultaneously — how do you model interdependency cascades, and does this change the optimal reconfiguration strategy compared to single-fault analysis?"*

4. > *"CEA's 2021 Cyber Security Guidelines for the Power Sector are mandatory for licensed utilities. From your assessment — are these guidelines technically sufficient to address the legacy protocol vulnerability problem, or are they primarily compliance exercises that do not meaningfully reduce actual cyber risk?"*

5. > *"Moving Target Defense (MTD) is promising for SCADA networks — but legacy protocols like Modbus operate on fixed polling addresses. How can MTD principles be applied at the network layer above legacy protocols without breaking the deterministic timing requirements that grid protection systems depend on?"*

---

## Key Terms Glossary

| Term | Meaning |
|---|---|
| Legacy System | Equipment/software designed 10–40+ years ago, before cybersecurity was a design criterion |
| SCADA | Supervisory Control and Data Acquisition — industrial control system for power grid |
| RTU | Remote Terminal Unit — field device reporting grid status to SCADA control center |
| IED | Intelligent Electronic Device — modern protection relay/monitor (more capable than RTU) |
| Modbus | Industrial protocol from 1979 — no security, widely used in legacy systems |
| DNP3 | Distributed Network Protocol 3 (1990) — standard for power utility SCADA, legacy security gaps |
| DNP3-SA | DNP3 Secure Authentication — cryptographic add-on for DNP3 |
| OT | Operational Technology — systems that monitor/control physical processes (SCADA, PLCs, RTUs) |
| IT | Information Technology — business/enterprise networks |
| IT-OT Convergence | Connection of previously isolated OT networks to IT/internet |
| Air Gap | Physical isolation of OT network from internet — eroded by smart grid integration |
| APT | Advanced Persistent Threat — sophisticated, patient, often state-sponsored attacker |
| DPI | Deep Packet Inspection — examining packet contents to detect malicious Modbus/DNP3 commands |
| Data Diode | One-way hardware link — physically prevents commands flowing into OT network |
| DMZ | Demilitarized Zone — intermediate network buffer between IT and OT |
| MTD | Moving Target Defense — continuously changing network parameters to confuse attackers |
| CVSS | Common Vulnerability Scoring System — standardized vulnerability severity scoring |
| FDIA | False Data Injection Attack — manipulates sensor data to fool state estimation |
| NCIIPC | National Critical Information Infrastructure Protection Centre (India) |
| CERT-In | Computer Emergency Response Team India |
| CEA | Central Electricity Authority (India) — regulatory body for power sector |
| Resilience Triangle | Area of performance degradation over time — key cyber-physical resilience metric |
| Digital Twin | Virtual replica of power system — used for anomaly detection and attack simulation |
| FACTS | Flexible AC Transmission Systems — advanced power flow control devices |

---
## **My Profiles**

- LinkedIn: [Link](https://www.linkedin.com/in/un-animesh/)
- GitHub: [Link](https://github.com/unanimesh)
- Email: [Link](https://mailto:un.animesh@zohomail.com)
