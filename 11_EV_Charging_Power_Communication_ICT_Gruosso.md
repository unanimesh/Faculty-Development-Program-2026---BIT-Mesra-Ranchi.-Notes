#  Faculty Development Program 2026 - BIT Mesra
## Session 11: Shaping the Future of EV Charging — Impact and Integration with Power, Communication and ICT Systems

---

## 🎤 Speaker Details

| Field | Details |
|---|---|
| **Name** | Prof. Giambattista Gruosso |
| **Designation** | Associate Professor |
| **Department** | Department of Electronics, Information and Bioengineering (DEIB) |
| **Institution** | Politecnico di Milano, Milan, Italy |
| **Email** | giambattista.gruosso@polimi.it |
| **Education** | B.S. + Ph.D. (Electrical Engineering) — Politecnico di Torino, 2003 |
| **Publications** | 150+ journal and conference papers |
| **IEEE Role** | **Chair, IEEE Vehicular Technology Society (VTS) — 2023–2026 triennium** |
| **IEEE Italy** | Vice-Chair, IEEE Italy Section; Member, IEEE European Public Policy Committee |

> **This is the only international (non-Indian) speaker of the entire FDP** — and from one of Europe's most prestigious technical universities, Politecnico di Milano (consistently ranked Top 10 in Europe for engineering).

### Research Areas 
- **Electric Vehicles & Transportation Electrification** — his primary focus
- **Electrical Power Systems** — grid impact, optimization
- **EV Charging & Grid Integration** — coordination strategies, stochastic modeling
- **ICT + Communication for EV Charging** — the unique angle of today's talk
- **Circuit Theory & Hardware-in-the-Loop Simulation**
- **AI/ML for Grid Stability** — Reinforcement Learning, Physics-Informed ML

### Industry Connections
He has done consulting and research for companies in the mobility sector, including IVECO (currently CNH Industrial) and FIAT (currently Stellantis) — two of Europe's largest commercial vehicle manufacturers.

### Key Publications 

| Paper | Journal | Contribution |
|---|---|---|
| **"Coordination Strategies for Electric Vehicle Chargers Integration in Electrical Grids"** | IEEE Open J. Vehicular Technology | Constrains EV charging power within transformer limits via coordination |
| **"Evaluating the Electrical Network Impact of EV Charging Strategies Across Residential, Workplace, and Public Users"** | ResearchGate 2025 | Compares impact of home vs workplace vs public charging on distribution network |
| **"A Data Driven Approach to Model EV Charging Behaviour for Grid Integration Analysis"** | IET Electrical Systems in Transportation | Stochastic, data-driven EV charging behavioral model for grid simulation |
| **"Enhancing Grid Stability Through Physics-Informed ML Integrated-MPC for EV Disturbance Management"** | Recent (2025) | Combines Physics-Informed Neural Networks + MPC to manage EV grid disturbances |
| **"Smart EV Charging Algorithm to Reduce Grid Impact: A Reinforcement Learning Based Methodology"** | IEEE Open J. VTS (Feature Paper) | RL-based charging optimizer with expert pre-training — reduces cost, avoids overloads |
| **"Future Smart Grids Control and Optimization: A Reinforcement Learning Tool"** | Recent | AI-based planning for smart grids incorporating EV charging |

---

##  Topic Deep Dive: EV Charging — Impact and Integration with Power, Communication and ICT Systems

This session is uniquely positioned at the **system-level intersection** of three worlds: power engineering, communication protocols, and ICT/data systems. It goes beyond hardware (Sessions 1, 3) to ask: **how does the entire EV charging ecosystem — hardware, software, communication, grid — work together?**

---

### 1. The Three-Layer EV Charging Ecosystem

```
┌─────────────────────────────────────────────────────────┐
│              ICT / Data Layer                           │
│  Fleet Management | Billing | CSMS | Cloud | Analytics  │
├─────────────────────────────────────────────────────────┤
│              Communication Layer                        │
│    OCPP (Charger↔Backend) | ISO 15118 (EV↔Charger)      │
│    IEC 61851 | CAN | PLC | WiFi | 4G/5G | V2G Protocol  │
├─────────────────────────────────────────────────────────┤
│              Power / Physical Layer                     │
│  Grid | Transformer | EVSE Hardware | EV Battery | BMS  │
└─────────────────────────────────────────────────────────┘
```

**Prof. Gruosso's unique contribution**: He studies all three layers together — most researchers focus on only one. His work captures how decisions in the ICT layer (when to charge, at what rate) directly cause physical consequences in the power layer (transformer overload, voltage deviation).

---

### 2. PART 1 — Power Grid Impact of EV Charging

#### The Grid Challenge

Uncoordinated EV charging, particularly during evening peak hours, can cause voltage deviations and potential transformer and cable overloads. Home charging shifts load to evenings; workplace charging shifts demand to daytime, alleviating evening peaks but introducing a different load pattern; public charging presents the highest level of unpredictability, making its grid impact most challenging to anticipate.

**Prof. Gruosso's Data-Driven Modeling:**
Having the means to study the impact of EV recharge on the power distribution network is one key aspect needed to manage the development of this technology. Power distribution grid and EVs are strongly connected elements that require wise integration to avoid that limitations of the distribution network may hinder vehicle diffusion, or that rapid growth of recharge demand causes grid instability.

#### Key Grid Impacts Quantified by His Research

| Impact Type | Cause | Prof. Gruosso's Solution Approach |
|---|---|---|
| **Transformer Overload** | Multiple EVs charging simultaneously exceed transformer rating | Coordination strategies constraining total power to transformer limits |
| **Voltage Deviation** | High charging current causes voltage drop on feeders | Stochastic simulation to quantify worst-case deviations |
| **Evening Peak Amplification** | Home EV charging coincides with household peak (6–9 PM) | Time-of-Use pricing + demand response |
| **Unpredictable Public Charging** | Random arrival/departure of EVs at public stations | Data-driven behavioral model from real charging data |
| **Transformer Ageing** | Repeated thermal stress from EV peaks shortens transformer life | Load coordination + smart scheduling |

#### Stochastic Modeling Approach
Prof. Gruosso uses **data-driven stochastic models** — not deterministic worst-case analysis:
- Real EV charging session data → statistical distribution of arrival time, session duration, energy demand
- Monte Carlo simulations → probability distribution of grid impact scenarios
- This gives planners a **probabilistic risk map** — e.g., "under current EV growth, there is a 15% probability the local transformer will be overloaded by 2027"

#### Coordination Strategies
His paper presents different coordination strategies for charging electric vehicles by constraining the power delivered by the grid within transformer limits. Smart grids are integrating EVs into power grids, and this requires careful coordination across multiple chargers.

Strategies include:
- **Dumb charging**: No coordination — maximum grid stress, cheapest to implement
- **Time-of-Use (ToU) pricing**: Price signal shifts charging to off-peak
- **Direct Load Control**: Utility caps charger power in real-time
- **Smart/Managed charging (V1G)**: Charger adapts rate based on grid signal
- **V2G Bidirectional**: EV discharges during peak — requires ISO 15118-20

---

### 3. PART 2 — Communication Layer: How EVs "Talk" to the Grid

This is Prof. Gruosso's distinctive research area — the **communication and ICT integration** that makes smart charging possible.

#### The Communication Stack

```
EV ←─── ISO 15118 ───→ Charging Station (EVSE)
                              │
                           OCPP 2.0.1
                              │
                    CSMS (Central System / Cloud)
                              │
                         DSO / Utility
                              │
                         Energy Market
```

#### ISO 15118 — The EV-to-Charger Language

ISO 15118 enables a unified communication framework that transforms EVs into mobile energy assets rather than just transportation devices. Vehicles can authenticate directly with charging stations using embedded digital certificates, reducing manual user actions. ISO 15118-20 supports vehicle-to-grid (V2G), vehicle-to-home (V2H), and vehicle-to-building (V2B) — enabling EVs to discharge energy back to the grid during peak demand.

**Key ISO 15118 features:**
- **Plug & Charge (PnC)**: EV authenticates automatically via PKI certificate — no RFID card or app needed
- **Smart Charging**: EV tells charger its battery state, desired charge level, departure time → charger optimizes
- **V2G negotiation**: EV and charger negotiate bidirectional power flow parameters
- **Security**: TLS mandatory in ISO 15118-20; hardware root of trust (TPM 2.0)

#### OCPP — The Charger-to-Backend Protocol

The two main internationally recognized standards for EV charging communication are ISO 15118 (EV to charger) and OCPP (Open Charge Point Protocol) by the Open Charge Alliance (charger to backend). Using OCPP, the charger receives energy tariffs and data needed to define charging schedules from the CPO and other stakeholders like the DSO. OCPP's smart charging allows the CPO or DSO to set the maximum power available at a given time for EV charging, enabling desired consumption behavior over time depending on forecast grid capacity or energy price.

**OCPP versions:**
- **OCPP 1.6**: Widely deployed; basic smart charging profiles
- **OCPP 2.0.1**: Supports V2G, ISO 15118-20 integration, enhanced security, device management
- **OCPP 2.1** (incoming): Backward compatible; adds payment terminal integration

#### The Full Communication Protocol Stack

| Layer | Protocol | Purpose |
|---|---|---|
| **EV ↔ Charger Physical** | IEC 61851-1 | Basic control pilot signaling (PWM) |
| **EV ↔ Charger High-Level** | ISO 15118 (PLC/WiFi) | Smart charging, PnC, V2G negotiation |
| **Charger ↔ Backend** | OCPP 2.0.1 | Session management, smart charging commands, billing |
| **Backend ↔ Grid/DSO** | OpenADR, ENTSO-E APIs | Demand response, grid balancing signals |
| **Backend ↔ Energy Market** | Market APIs | Dynamic pricing, energy trading |

---

### 4. PART 3 — ICT Layer: Data, AI and Fleet Intelligence

#### The Charging Station Management System (CSMS)

The ICT layer sits above the communication layer — it is the cloud software that:
- Manages thousands of charging stations remotely
- Handles billing, authentication, and session records
- Receives demand response signals from the grid operator
- Runs optimization algorithms for smart charging
- Provides analytics dashboards for fleet operators

#### AI/ML in EV Charging (Prof. Gruosso's Latest Work)

**Reinforcement Learning for Smart Charging:**
A reinforcement learning-based method optimizes EV charging and discharging using expert pre-training and realistic grid simulations. By accounting for real battery limits and adapting to changing grid conditions, the proposed method reduces costs, avoids grid overloads, and enables EVs to support the grid when needed — offering a practical and scalable solution for integrating large EV fleets.

**Physics-Informed ML + MPC:**
Enhancing grid stability through Physics-Informed Machine Learning Integrated-Model Predictive Control for EV disturbance management — integrating EVs into modern power grids enhances grid stability and supports green energy transportation solutions, but introduces significant challenges due to unpredictable and dynamic EV charging and discharging behaviors.

**Key AI applications in CSMS:**

| AI Method | Application |
|---|---|
| **LSTM + Attention** | Forecasting EV arrival patterns and charging demand |
| **Reinforcement Learning** | Real-time optimal charging/V2G scheduling |
| **Physics-Informed NN** | Grid-aware charging — respects Kirchhoff's laws |
| **Random Forest / GBM** | Predicting transformer loading under EV penetration |
| **Digital Twin** | Virtual replica of charging network for simulation |
| **Stochastic optimization** | Fleet charging under uncertainty |

---

### 5. EMI and Power Quality — The Hidden ICT Problem

One of Prof. Gruosso's niche research areas: **the communication system inside the EV charger is disrupted by the power electronics it lives next to.**

- EV chargers use high-frequency switching converters (IGBT/SiC at 10–100 kHz)
- These generate **Electromagnetic Interference (EMI)** — electrical noise
- ISO 15118 uses **Power Line Communication (PLC)** — the control signal travels over the same cable as the power
- **The power electronics noise can corrupt the PLC signal** — causing communication errors and failed charging sessions
- Prof. Gruosso's circuit theory and Hardware-in-Loop expertise addresses this co-existence problem

---

### 6. Cybersecurity of EV Charging ICT

With EV chargers now internet-connected and using complex protocols:

ISO 15118 specifies two authentication methods: certificate-based Plug-and-Charge and generic External Identification Means. The new ISO 15118-20 edition makes TLS mandatory and integrates TPM 2.0 for hardware security. However, vulnerabilities in OCPP implementations and botnet attacks targeting high-wattage IoT EV chargers represent significant attack surfaces for grid destabilization.

**Key cyber risks in EV charging ICT:**
- OCPP injection attacks — fraudulent charging commands to chargers
- ISO 15118 certificate spoofing — fake EV identity
- CSMS ransomware — locks the backend, all chargers go offline
- Grid-level botnet — thousands of compromised chargers simultaneously commanded to charge at maximum → grid overload

> **Connection to Session 7 (Dr. Rajesh Gupta — Cyber Resiliency)**: The EV charging ICT stack is exactly the kind of modern infrastructure with legacy protocol vulnerabilities that Dr. Gupta's session addressed.

---

### 7. India Context

- India's public EV charger count crossed **25,000** in 2024 — but penetration is still very low
- **Bharat AC-001 and DC-001** standards — India's national EV charging standards (not yet aligned with ISO 15118)
- **OCPP adoption**: Growing in India's large CPOs (Tata Power EZ Charge, Ather Grid, ChargeZone) but implementations vary
- **Grid readiness**: India's distribution network was not designed for EV loads — Prof. Gruosso's grid impact modeling is directly applicable to Indian cities
- **IT infrastructure**: India's strong ICT capability (cloud, mobile, AI) is an asset for building world-class CSMS platforms
- **V2G opportunity**: India's afternoon solar surplus + evening EV charging peak align perfectly — V2G could help balance both simultaneously

---

##  Questions to Ask 



1. 
   > *"Your stochastic data-driven models of EV charging behavior were built from European driving and charging data. India has very different mobility patterns — shorter daily distances, more two-wheelers, severe evening grid peaks from air conditioning + EV charging coinciding, and weak distribution transformers. How fundamentally would your grid impact models need to be re-parameterized for an Indian city like Bengaluru or Delhi — and is the stochastic framework itself transferable, or does it need rethinking?"*

2. > *"ISO 15118 uses Power Line Communication for EV-to-charger signaling, but the same cable carries high-frequency switching noise from the power electronics converter. How significant is the EMI-induced communication error rate in real deployments, and what is the state-of-the-art mitigation — signal conditioning, frequency planning, or redundant communication channels?"*

3. > *"Your RL-based smart charging optimizer accounts for real battery limits and adapts to changing grid conditions. The training environment uses realistic grid simulations — but real distribution networks in developing countries often have data gaps, outdated single-line diagrams, and no real-time grid state visibility. How does your RL model degrade when grid model accuracy is poor, and what is the minimum data requirement to deploy it?"*

4. > *"OCPP 2.0.1 enables the DSO to directly control charger power output. But in India, the DSO-to-charger communication chain involves multiple layers — national grid, state DISCOM, last-mile feeder operator — with unclear authority over demand response. From your European experience with regulated demand response, what single institutional or technical change would most accelerate smart charging deployment in a developing country context?"*

5. > *"As IEEE VTS Chair — what do you see as the most underappreciated research problem in EV charging today, one that receives less attention than it deserves given its potential impact on the long-term success of transportation electrification globally?"*

---

##  Key Terms Glossary

| Term | Meaning |
|---|---|
| EVSE | Electric Vehicle Supply Equipment — the charging station hardware |
| CSMS | Charging Station Management System — cloud backend managing all chargers |
| CPO | Charge Point Operator — company operating charging stations |
| DSO | Distribution System Operator — manages the local electricity distribution grid |
| eMSP | e-Mobility Service Provider — handles EV driver accounts and billing |
| ISO 15118 | International standard for EV-to-charger communication (smart charging, V2G, PnC) |
| OCPP | Open Charge Point Protocol — charger-to-backend communication standard |
| Plug & Charge (PnC) | Automatic authentication via digital certificate — no RFID/app needed |
| PKI | Public Key Infrastructure — certificate-based security system |
| TLS | Transport Layer Security — encryption protocol (mandatory in ISO 15118-20) |
| PLC | Power Line Communication — sending data signals over power cables |
| OpenADR | Open Automated Demand Response — grid-to-building demand response protocol |
| V1G | Unidirectional smart charging — grid controls when/how fast EV charges |
| V2G | Vehicle-to-Grid — EV discharges back to grid |
| Stochastic Model | Probabilistic model capturing uncertainty (arrival times, session duration) |
| Monte Carlo | Simulation technique using many random samples to estimate outcomes |
| RL | Reinforcement Learning — AI learns optimal charging policy by trial and error |
| Physics-Informed ML | Neural network that incorporates physical laws (Kirchhoff, power flow) |
| EMI | Electromagnetic Interference — noise from power electronics disrupting communication |
| Polimi | Politecnico di Milano — Italy's top technical university |
| VTS | IEEE Vehicular Technology Society — professional society for vehicle tech |
| DEIB | Dept. of Electronics, Information and Bioengineering — Prof. Gruosso's department |
| Digital Twin | Virtual replica of charging network for real-time simulation |

---

## **My Profiles**

- LinkedIn: [Link](https://www.linkedin.com/in/un-animesh/)
- GitHub: [Link](https://github.com/unanimesh)
- Email: [Link](https://mailto:un.animesh@zohomail.com)

