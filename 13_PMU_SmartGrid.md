#  Faculty Development Program 2026 - BIT Mesra
## Session 13: PMU Applications in Smart Grid

---

##  Speaker Details

| Field | Details |
|---|---|
| **Name** | Dr. M. Jaya Bharata Reddy |
| **Designation** | Professor, Department of Electrical & Electronics Engineering |
| **Institution** | National Institute of Technology (NIT) Tiruchirappalli, Tamil Nadu |
| **Email** | jbreddy@nitt.edu |
| **Google Scholar Citations** | 2,903+ |
| **Publications** | 100+ journal and conference papers |
| **Patents** | 2 granted |

### Academic Background — BIT Mesra Alumnus AND Former Faculty!

| Degree/Role | Year | Institution |
|---|---|---|
| B.Tech. (Electrical Engineering) | 2002 | Nagarjuna University, Guntur |
| **M.E. (Electrical Engineering)** | **2004** | **BIT Mesra, Ranchi** |
| **Ph.D. (DSP for Digital Relaying)** | **2008** | **BIT Mesra, Ranchi** |
| **Lecturer** | **2004–2009** | **BIT Mesra, Ranchi** |
| Professor | 2019–Present | NIT Tiruchirappalli |

> Both M.E. and Ph.D. from BIT Mesra. Taught here for 5 years. His Ph.D. supervisor is Prof. D.K. Mohanta — your own department's faculty. He literally wrote the book on PMU applications (IET, 2017), co-edited with Prof. Mohanta of BIT Mesra.

### Awards 
- **IEI Young Engineers Award 2010** — national-level, Electrical Engineering
- **SERC Fast Track Young Scientist Award 2013** — DST, Govt. of India
- **Innovating Contributions Award 2023** — NIT Tiruchirappalli
- **Sponsored Research Projects Award 2016 & 2018** — NIT Trichy EEE
- **Research Publication Award 2018** — NIT Trichy EEE

### Funded Research Projects 
| Project | Agency | Amount | Role |
|---|---|---|---|
| Wide-Area Disturbance Monitoring & Protection using PMUs | SERB, DST | ₹31.56 Lakhs | PI |
| Data-Driven Event Detection using Indian Power Grid Synchrophasor Data | SERB, DST | ₹19.41 Lakhs | Co-PI |
| Solar PV-Powered Cold Storage System | DST | ₹105.81 Lakhs | PI |

### Book 
**"Synchronized Phasor Measurements for Smart Grid"** — IET Power & Energy Series 97, UK, 2017. Co-edited with Prof. D.K. Mohanta, BIT Mesra. *He literally wrote the book on today's topic.*

---

## 📡 Topic Deep Dive: PMU Applications in Smart Grid

---

### 1. What Is a PMU?

A **Phasor Measurement Unit (PMU)** measures electrical quantities on the power grid with GPS-based synchronization — enabling simultaneous measurements across the entire grid.

**What it measures:**
- Voltage phasor: magnitude + phase angle (V∠θ)
- Current phasor: magnitude + phase angle (I∠θ)
- Frequency and ROCOF (Rate of Change of Frequency)
- Active and Reactive Power (P, Q)

**The GPS synchronization revolution:**

| Feature | Traditional SCADA/RTU | PMU |
|---|---|---|
| Time reference | Local clock | GPS (±1 microsecond) |
| Update rate | 1 per 2–4 seconds | 10–120 per second (50 fps for India) |
| Measurement | P, Q, \|V\| (magnitude only) | V∠θ, I∠θ (magnitude + phase angle) |
| Phase angle difference | Cannot measure across locations | Directly measured between any two buses |
| Dynamic visibility | Cannot see oscillations | Sees oscillations at 0.1 Hz and above |
| Fault location accuracy | ±5–10% | ±1–2% |

**Standard**: IEEE C37.118 — international PMU compliance standard.

---

### 2. Wide Area Measurement System (WAMS)

PMU is just a sensor. WAMS is the complete infrastructure:

```
PMU (at each substation)
     ↓ (IEEE C37.118, 50 fps, optical fiber)
PDC — Phasor Data Concentrator (regional aggregator)
     ↓
Super PDC (national aggregator)
     ↓
WAMS Control Center (real-time visualization + analytics + alarms)
                   ← POSOCO / NLDC in India
```

**India's WAMS**: POSOCO (Power System Operation Corporation of India) operates PMUs at all 400 kV and 765 kV substations. Dr. Jaya Bharata Reddy's research directly uses this Indian grid synchrophasor data.

---

### 3. PMU Applications — Dr. Jaya Bharata Reddy's Research

#### A. Fault Detection, Classification & Location (His Core Work)

Traditional impedance-based fault location using single-end measurements gives ±5–10% error. PMU-based both-end synchronized fault location achieves **±1–2% accuracy** — locating faults to within kilometers on 500 km lines.

**His verified publications:**
- "Fault Detection and Localization Methodology for Self-healing in Smart Power Grids Incorporating PMUs" — *Electric Power Components and Systems*, 2015
- "Adaptive Fault Identification and Classification Methodology for Smart Power Grids Using Synchronous Phasor Angle Measurements" — *IET GT&D*, 2015
- "Transmission Line Fault Detection and Localisation Methodology using PMU Measurements" — *IET GT&D*, 2015
- "Real-Time Synchronized Harmonic Phasor Measurements-Based Fault Location Method" — uses harmonic phasors (novel)

**His AI-enhanced approach**: ANN + Fuzzy Logic classifies fault types using phasor angle data — handles fault resistance variation, load current effects, and CT saturation.

#### B. Wide-Area Protection (WAP)

Local protection relays only see their own CTs/PTs. When a disturbance spans multiple zones, local relays can mis-operate or fail to operate.

**Wide-Area Protection using PMUs:**
- Coordinates protection across multiple zones using WAMS data
- **System Integrity Protection Schemes (SIPS)**: Automatic actions (load shedding, islanding) triggered by WAMS when large disturbances detected
- His ₹31.56 Lakh SERB project: "Realization and Implementation of Wide-Area Disturbance Monitoring and Protection Methodology for Future Grids using PMUs"

#### C. Optimal PMU Placement (OPP)

PMUs cost ₹10–25 lakh each. Minimum placement for full grid observability is a combinatorial optimization problem.

**His verified publication**: "Optimal Redundant Placement of PMUs in Indian Power Grid — Northern, Eastern and North-Eastern Regions" — *Frontiers in Energy, Springer*, 2013.

Applied to actual Indian grid topology. Methods: Integer Linear Programming + graph-based observability analysis + redundancy constraints.

**Observability rule**: A bus is observable if it has a PMU OR if Kirchhoff's laws allow calculation from neighboring PMU measurements.

#### D. State Estimation with PMUs

- Traditional SCADA state estimation: iterative, nonlinear, uses P/Q/|V| — slow and approximate
- PMU-based state estimation: direct linear calculation using V∠θ and I∠θ — real-time, no iteration
- **Hybrid SE** combining SCADA + PMU is the current industry standard — redundancy + accuracy

#### E. Inter-Area Oscillation Detection

Low-frequency inter-area oscillations (0.1–0.8 Hz) can grow unstable and cause blackouts. PMUs at 50 fps easily capture these oscillations.

**Methods:**
- **Prony analysis / FFT**: Extract oscillation mode frequencies and damping ratios from PMU data
- Alert operators when damping ratio < 5% (critical stability threshold)
- **WAMS-based PSS tuning**: Power System Stabilizers re-tuned in real-time using PMU data

#### F. Voltage Stability Monitoring

The **2012 India blackout** (670 million people — largest in history) was caused by voltage instability cascading across northern, eastern, and northeastern grids.

**PMU-based Voltage Stability Indices:**
- **L-Index**: Computed from synchronized phasors — 0 = secure, approaching 1 = voltage collapse imminent
- Real-time P-V nose curve tracing: operators see exactly how close they are to collapse
- WAMS alerts operators with margin-to-collapse estimates in real time

#### G. Data-Driven Event Detection using ML (His Latest Work)

His SERB project (2018–2021) uses **actual Indian grid PMU data** — not simulation — for ML-based event detection:

| Event Type | ML Method Used | Key Challenge |
|---|---|---|
| Generation trip | SVM, Random Forest | Fast frequency transient, < 1 second |
| Load shedding | CNN on phasor time-series | Distinguishes from generation trip |
| Line switching | Decision Tree + frequency signature | Similar signature to fault events |
| Inter-area oscillation onset | Prony + LSTM | Slow-developing, needs temporal context |
| Islanding detection | Frequency + ROCOF + phasor angle | Must not confuse with frequency event |

**India-specific finding**: Monsoon seasons cause systematic frequency dips due to hydro generation variation that trained models must learn to ignore — not possible without real Indian grid data.

---

### 4. Smart Grid Self-Healing with PMUs

One of the most compelling applications — the grid that heals itself after a fault:

```
Fault occurs on transmission line
       ↓
PMUs detect fault signature (microseconds)
       ↓
WAMS event classifier identifies: fault type, location, severity
       ↓
SIPS triggers automatic protective actions:
  - Trip faulted line
  - Shed minimum load to prevent cascade
  - Reconfigure network to isolate fault
  - Restore supply to healthy zones
       ↓
All within 100–500 milliseconds
       ↓
Human operator informed — grid already stabilized
```

**Dr. Jaya Bharata Reddy's paper**: "Fault Detection and Localization Methodology for Self-healing in Smart Power Grids Incorporating PMUs" — directly addresses this automated self-healing architecture.

---

### 5. India Context & National Relevance

- **POSOCO WAMS**: PMUs deployed at all 400 kV + 765 kV substations across India — national-scale real data
- **2012 Blackout lessons**: India's massive grid failure directly accelerated PMU deployment — Dr. Jaya Bharata Reddy's research is part of India's response to that event
- **Renewable integration challenge**: India's 90+ GW solar + 46+ GW wind causes fast frequency events that SCADA (1 per 4 sec) cannot detect — PMUs at 50 fps are essential
- **Northeast India**: Remote substations with poor fiber connectivity — his research addresses communication-constrained PMU deployment
- **μPMU (Micro-PMU)**: Low-cost PMUs (~₹20,000) now being piloted for distribution-level smart grids — could enable state estimation in India's 11 kV distribution networks

---

##  Questions to Ask 

1. 
   > *"Your SERB project used actual Indian power grid synchrophasor data for ML-based event detection. What was the most unexpected behavior in the real Indian PMU data — something no simulation would have revealed — and how did it force you to redesign your event classification model?"*

2. > *"Your optimal PMU placement work was done for Northern, Eastern and NE India in 2013. With μPMU costs now dropping to ₹20,000 — two orders of magnitude cheaper than traditional PMUs — does the optimal placement problem need to be completely rethought? Is the new question 'where NOT to place PMUs' rather than 'where to place them'?"*

3. > *"The 2012 India blackout evolved in under 2 minutes. Your wide-area protection scheme using PMUs must act faster than cascade propagation. Given that PMU data latency through PDC chains is 100–500 ms and ML classifiers add delay — is WAMS-based protection actually fast enough for cascade prevention, or is it fundamentally a post-event monitoring tool?"*

4. > *"With high solar PV penetration (India targeting 500 GW renewables), the grid becomes inverter-dominated — low inertia, fast frequency changes, no synchronous reference. Does conventional PMU-based state estimation (designed for synchronous generator-dominated grids) remain valid in a high-inverter grid, or do the algorithms need rethinking?"*

5. > *"As someone who did both M.E. and Ph.D. at BIT Mesra, taught here for 5 years, and co-edited the defining IET book on PMUs with Prof. Mohanta of this department — what specific steps would you recommend BIT Mesra EEE take to build a PMU/WAMS research program that could attract SERB funding at the level of your NIT Trichy lab?"*

---

##  Key Terms Glossary

| Term | Meaning |
|---|---|
| PMU | Phasor Measurement Unit — GPS-synchronized power measurement device |
| Phasor | Complex representation: magnitude + phase angle (V∠θ) |
| Synchrophasor | GPS-synchronized phasor — simultaneously measured across entire grid |
| WAMS | Wide Area Measurement System — complete PMU infrastructure |
| PDC | Phasor Data Concentrator — aggregates data from multiple PMUs |
| IEEE C37.118 | PMU measurement accuracy and communication standard |
| WAP | Wide Area Protection — protection using multi-location PMU data |
| SIPS | System Integrity Protection Scheme — automatic large-scale protective action |
| OPP | Optimal PMU Placement — minimum PMUs for full grid observability |
| L-Index | Voltage stability index from synchronized phasors (0=secure, 1=collapse) |
| ROCOF | Rate of Change of Frequency — fast frequency derivative |
| Inter-area Oscillation | 0.1–0.8 Hz power oscillation between generator groups |
| Prony Analysis | Signal processing to extract oscillation modes from PMU data |
| Digital Relay | Microprocessor-based protection relay — Dr. Jaya Bharata Reddy's Ph.D. topic |
| POSOCO | Power System Operation Corporation of India — national grid operator |
| NLDC | National Load Despatch Centre — India's national grid control center |
| μPMU | Micro-PMU — low-cost PMU for distribution-level monitoring |
| Hybrid SE | State estimation combining SCADA + PMU measurements |

---

## **My Profiles**

- LinkedIn: [Link](https://www.linkedin.com/in/un-animesh/)
- GitHub: [Link](https://github.com/unanimesh)
- Email: [Link](https://mailto:un.animesh@zohomail.com)
