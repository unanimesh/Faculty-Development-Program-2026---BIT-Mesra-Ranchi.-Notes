#  Faculty Development Program 2026 - BIT Mesra
## Session 03: Z-Source Inverter Bidirectional EV Charger for V2G Applications

---

## 🎤 Speaker Details

| Field | Details |
|---|---|
| **Name** | Dr. Sumant G. Kadwane |
| **Designation** | Professor, Department of Electrical Engineering |
| **Institution** | Yeshwantrao Chavan College of Engineering (YCCE), Nagpur |
| **Email** | sgkadwane@gmail.com / ycce.edu |
| **ORCID** | 0000-0002-0054-3086 |
| **Research Areas** | Power Electronics, Renewable Energy, Z-Source & Quasi-Z-Source Inverters, Grid-Connected Systems, EV Charging |

### About YCCE
- Established **1984**, Hingna Road, Nagpur, Maharashtra
- First private engineering college in Central India to achieve **Autonomous Status**
- **NAAC Grade A++ (3.6/4)** — highest among engineering colleges in Maharashtra (2023)
- **NIRF Ranked 151–200** nationally
- Affiliated to Rashtrasant Tukadoji Maharaj Nagpur University (RTMNU)

### Dr. Kadwane's Research Highlights

**Core Expertise:**
- Z-Source Inverter (ZSI) and Quasi-Z-Source Inverter (qZSI) topologies
- Grid-connected inverter systems
- Bidirectional power converters for EV applications
- Sliding mode and advanced control strategies for inverters
- Multilevel inverters with selective harmonic elimination
- Solar PV grid integration and MPPT strategies

**Key Publications & Work:**
1. **"Design of Quasi-Z Source Converter for Vehicle-to-Vehicle (V2V) Battery Charging"** — Published in *Energy Storage*, Wiley (2022). Specifically developed QZSC for V2V EV charging — directly tied to today's topic.
2. **"Sliding Mode Control of Single-Phase Grid-Connected Quasi-Z-Source Inverter"** (2019) — Advanced control for qZSI grid connection.
3. **"Multi-DG qZSI Based Grid-Tied Inverters"** — *AIP Advances*, June 2024 — multi-source quasi-ZSI for distributed generation.
4. **"Symmetrical Shoot-Through (SST) based Modulation for Z-Source Inverter"** — reduces THD vs asymmetric shoot-through.
5. **"Passive Islanding Method for Inverter-Based Grid-Connected Systems"** — safety critical for V2G deployment.
6. **"Maximizing Solar Water Pump Efficiency: MPPT Strategies"** — *AIP Advances* (SCI), 2024.

**Patent:**
- Co-inventor of **Indian Patent No. 201821003085**: *"Device for providing load compensation and harmonic mitigation in an alternating current power system"* — granted February 2023.

**Collaborators:**
- Dr. Ritesh Kumar Keshri (VNIT Nagpur) — the same speaker from Session 1 of this FDP!
- Prof. T. Ghose (BIT Mesra) — direct connection to your own institution
- Jyoti M. Kumbhare (YCCE)

---

##  Topic Deep Dive: Z-Source Inverter Bidirectional EV Charger for V2G

---

### 1. The Problem with Traditional Inverters

Before understanding Z-Source, understand why traditional inverters fall short for EV/V2G:

| Inverter Type | Limitation |
|---|---|
| **Voltage Source Inverter (VSI)** | Output AC voltage ≤ DC input; cannot boost. Needs a separate DC-DC boost stage |
| **Current Source Inverter (CSI)** | Output AC voltage ≥ DC input; cannot buck. Needs separate stage for wide range |
| **Both** | Shoot-through (both switches in same leg ON) is **forbidden** — destroys the device |

For EV batteries, the voltage varies widely with state of charge (e.g., 200–450V for a typical pack). A charger must handle this **wide variable voltage range**, requiring either a multi-stage converter (complex, heavy, costly) or a smarter single-stage solution.

**The Z-Source Inverter (ZSI) solves this.**

---

### 2. What Is a Z-Source Inverter (ZSI)?

Proposed by Prof. Fang Zheng Peng (Michigan State University) in **IEEE Trans. Ind. Appl., 2003** — one of the most cited power electronics papers ever.

**Topology:**
- An **X-shaped impedance network** (two inductors L₁, L₂ and two capacitors C₁, C₂) is inserted between the DC source and the traditional inverter bridge
- This network allows a unique operating state called **Shoot-Through (ST)**

```
DC Source (Battery)
      ↓
[Z-Network: L₁-C₁-L₂-C₂ in X-shape]
      ↓
[Inverter Bridge (6 switches)]
      ↓
AC Output (Grid / Motor)
```

**Key Innovation — Shoot-Through State:**
- In traditional VSI, if both upper and lower switches in one leg turn ON simultaneously → short circuit → device destruction
- In ZSI, the Z-network **absorbs the short-circuit** — capacitors charge inductors, and when active state returns, the stored inductor energy **adds to** the DC source voltage
- Result: **DC-link voltage is boosted** beyond the source voltage

**Boost Factor B:**
`B = 1 / (1 - 2D)` where D = shoot-through duty ratio

**Voltage Gain G = M × B** where M = modulation index

**Advantages of ZSI:**
- Single-stage buck AND boost — no separate DC-DC converter needed
- Shoot-through is safe — improves reliability
- Wide input voltage range — ideal for EV batteries
- Reduced component count vs two-stage converters
- Can ride through momentary short circuits

---

### 3. Quasi-Z-Source Inverter (qZSI) — The Improved Version

Dr. Kadwane's primary research focus. The qZSI improves upon ZSI:

| Feature | ZSI | qZSI |
|---|---|---|
| Input current | Discontinuous | **Continuous**  |
| Capacitor voltage | Higher rating needed | Lower (reduced stress)  |
| Component sharing | Separate ground | **Common DC rail**  |
| Source current ripple | Higher | Lower  |

The continuous input current of qZSI makes it ideal for **battery-fed EV systems** (batteries don't like current pulsation) and **solar PV** (protects panels).

---

### 4. Bidirectional Z-Source / qZS Converter for EV Charging

For V2G, the converter must allow power to flow **in both directions**:

| Mode | Power Direction | Operation |
|---|---|---|
| **G2V (Charging)** | Grid → EV Battery | Rectifier + Buck mode: AC to DC, step down to charge battery |
| **V2G (Discharging)** | EV Battery → Grid | Inverter + Boost mode: DC to AC, boost battery voltage to grid level |

**The Bidirectional Z-Source/qZS topology enables this in a single stage:**
- In G2V: Works as an AC-DC rectifier with controlled DC output
- In V2G: Works as a DC-AC inverter with boost capability
- The same Z-network and bridge handle both modes with appropriate control

**Dr. Kadwane's V2V Application (2022):**
- Designed Quasi-Z-Source Converter specifically for **Vehicle-to-Vehicle (V2V)** charging
- QZSC advantages: uninterrupted input current + broad input voltage range — both critical for EV-to-EV direct energy transfer

---

### 5. Control Strategies for Bidirectional ZSI in V2G

Controlling a bidirectional ZSI requires managing:

1. **Shoot-Through Duty Ratio (D)** — controls DC-link boost voltage
2. **Modulation Index (M)** — controls AC output voltage
3. **Power Factor** — must be unity (or controllable) for grid compliance
4. **d-q Current Control** — separates active power (P) and reactive power (Q) control
5. **Active and Reactive Power (P-Q) Control** — in V2G, the grid operator can request both P and Q

**Dr. Kadwane's Control Work:**
- **Symmetrical Shoot-Through (SST) Modulation** — reduces THD by inserting shoot-through symmetrically within PWM cycles
- **Sliding Mode Control** for qZSI — robust, fast-response control that handles EV battery voltage variation
- **Passive Islanding Detection** — when the grid fails, the inverter must detect and disconnect; critical safety requirement for V2G

---

### 6. Z-Source vs Conventional Bidirectional Charger

| Feature | Conventional Bidirectional Charger | Z-Source Bidirectional Charger |
|---|---|---|
| Stages | 2-stage (AC-DC + DC-DC) | **Single stage** |
| Voltage range | Limited | **Wide (buck-boost)** |
| Reliability | Lower (more components) | **Higher** |
| Size/Weight | Larger | **Compact** |
| Shoot-through | Forbidden | **Allowed (safe)** |
| Cost | Higher | **Lower potential** |
| Control complexity | Moderate | Slightly higher |

---

### 7. V2G Applications Enabled by Bidirectional ZSI

- **Peak Shaving**: EV discharges during evening peak demand, reducing grid stress
- **Frequency Regulation**: Fast response of power electronics helps grid frequency stay at 50 Hz
- **Reactive Power Compensation**: The inverter injects/absorbs reactive power (Q control) — essentially a STATCOM capability
- **Renewable Energy Integration**: EV + ZSI can store solar surplus and return it to grid at night
- **Harmonic Mitigation** (Dr. Kadwane's patent area): Active filtering while charging/discharging
- **Islanding / Microgrid**: EVs with ZSI can form a local microgrid during grid outage

---

### 8. India Context & Relevance

- India's EV boom (EV sales crossing 2 million units in FY2024) is driving demand for smart, compact bidirectional chargers
- Z-Source topology is particularly relevant for **Indian conditions** — wide grid voltage fluctuations (±10–15%), making the buck-boost capability of ZSI highly valuable
- National Green Hydrogen Mission + EV Mission together make the **power electronics interface** (ZSI chargers) a critical research domain

---

## Questions to Ask


1.
   > *"In your V2V quasi-Z-source converter work, how did you handle the dynamic impedance mismatch between two batteries at different SOC levels during charging — and how does this extend to V2G where one side is an infinite bus?"*

2. > *"Symmetrical Shoot-Through (SST) reduces THD compared to conventional PWM for ZSI — but does it impose any constraint on the maximum achievable boost factor or modulation index range, particularly at low battery voltages?"*

3. > *"For V2G grid compliance in India, what are the key IEEE/IEC standards a ZSI-based bidirectional charger must meet regarding power quality, islanding, and reactive power injection, and which is the hardest to satisfy?"*

4. > *"Sliding mode control offers robustness for qZSI, but chattering remains a challenge. Have you explored higher-order sliding mode or super-twisting algorithms specifically for the shoot-through state control in EV applications?"*

5. > *"Given that your patent addresses harmonic mitigation in AC power systems, can a bidirectional ZSI-based EV charger simultaneously act as an active power filter while performing V2G — and what are the trade-offs?"*

---

##  Key Terms Glossary

| Term | Meaning |
|---|---|
| ZSI | Z-Source Inverter — single-stage buck-boost inverter |
| qZSI | Quasi-Z-Source Inverter — improved ZSI with continuous input current |
| Shoot-Through (ST) | Both switches in one inverter leg ON simultaneously; normally forbidden but safe in ZSI |
| G2V | Grid-to-Vehicle — conventional charging |
| V2G | Vehicle-to-Grid — EV discharges back to the grid |
| V2V | Vehicle-to-Vehicle — one EV charges another |
| d-q Control | Synchronous reference frame control for AC systems — separates P and Q |
| SPWM | Sinusoidal Pulse Width Modulation |
| SST | Symmetrical Shoot-Through — Dr. Kadwane's modulation scheme |
| THD | Total Harmonic Distortion — power quality measure |
| SOC | State of Charge of battery |
| Boost Factor (B) | B = 1/(1-2D) — how much ZSI boosts DC voltage |
| Modulation Index (M) | Controls AC output voltage magnitude |
| Islanding | When grid-connected inverter keeps running after grid disconnects — dangerous |
| MPPT | Maximum Power Point Tracking — for solar PV |
| STATCOM | Static Synchronous Compensator — reactive power device; ZSI charger can mimic this |

---


## **My Profiles**

- LinkedIn: [Link](https://www.linkedin.com/in/un-animesh/)
- GitHub: [Link](https://github.com/unanimesh)
- Email: [Link](https://mailto:un.animesh@zohomail.com)
