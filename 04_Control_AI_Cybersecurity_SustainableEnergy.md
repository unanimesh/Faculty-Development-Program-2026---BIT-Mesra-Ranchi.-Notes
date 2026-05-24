#  Faculty Development Program 2026 - BIT Mesra
## Session 04: Emerging Control, AI & Cybersecurity for Sustainable Energy

---

## Speaker Details

| Field | Details |
|---|---|
| **Name** | Dr. Kalyan Chatterjee |
| **Designation** | Professor, Department of Electrical Engineering |
| **Institution** | IIT (ISM) Dhanbad — Indian Institute of Technology (Indian School of Mines), Dhanbad |
| **Email** | kalyanchatterjee@iitism.ac.in |
| **Google Scholar Citations** | 4,240+ |
| **Ph.D. Students Guided** | 17 completed + 4 ongoing |
| **PG Students Guided** | 30+ |
| **Teaching Experience** | 25+ years |

### Research Areas
- Power Systems & Small Signal Stability
- Soft Computing / AI Applications in Power Systems
- Renewable Energy (Solar PV, Wind — DFIG)
- Cyber Physical Systems (CPS) for Energy
- Smart Grid & Grid Security

### Administrative Roles at IIT(ISM) Dhanbad
- **Head of Electrical Engineering Department** (Dec 2018 – Jan 2023)
- **Associate Dean — R&D (Industrial Consultancy)** (Jul 2018 – Mar 2019)
- **Chairman, PG-Ph.D. Admission Committee** (Sep 2024 – Present)
- **President, Cyber Society** (March 2012 – Aug 2018) ← Directly relevant to today's topic!
- **Vice Chairman, PG-Ph.D. Admission Committee** (2023–2024)

### Key Publications & Work
1. **LQI Controller for Small-Signal Stability of DFIG Wind Energy Systems** — Demonstrates superiority of Linear Quadratic Integral controller over LQR for wind turbine stability
2. **Solar PV Grid-Connected System Research** — Multiple publications on PV modeling, MPPT, and grid integration
3. **Cyber Physical System Security** — Active research in CPS vulnerabilities and protection for energy systems
4. **Feature Extraction using MRDWT** — AI/ML applied to classification problems (ECG, power system signals)
5. **Fault Ride Through (LVRT) for DFIG Wind Systems** — comprehensive review and hardware + control strategy work

### Patent
- **Patent No. 202531004108** (Indian Patent Office, July 31, 2025) — *"Compact Three-Phase Saturated Core Fault Current Limiter (SCFCL) for Grid-Connected DFIG Systems"* — Inventors: Kalyan Chatterjee & Prashant Mani Tripathi

### Connections to BIT Mesra
- Previously **Lecturer at BIT Mesra, Ranchi** before joining IIT(ISM)
- **Prof. T. Ghose (BIT Mesra EEE)** appears as a collaborator on Dr. Chatterjee's Google Scholar — a direct BIT Mesra connection in the room!

---

## Topic Deep Dive: Emerging Control, AI & Cybersecurity for Sustainable Energy

This session covers **three deeply intertwined pillars** in modern energy systems:

```
        SUSTAINABLE ENERGY SYSTEMS
               /        |        \
    Emerging      Artificial    Cyber-
    Control    Intelligence   Security
    Strategies    (AI/ML)      (CPS)
               \        |        /
         Smart Grid / Microgrid / DFIG
```

---

### PILLAR 1: Emerging Control Strategies for Sustainable Energy

#### Why Traditional PID Control Is No Longer Enough

Modern power systems are increasingly nonlinear, uncertain, and distributed — driven by:
- Intermittent renewables (Solar PV, Wind) with variable output
- Distributed Generation (DG) connected to weak grids
- Microgrids with island/grid-connected mode transitions
- EV loads and bidirectional V2G power flows

Traditional PID tuning struggles with these dynamics. **Emerging control strategies** address this.

#### Key Emerging Control Methods

| Control Strategy | How It Works | Best For |
|---|---|---|
| **LQR / LQI** | State-space optimal control minimizing cost function | Wind turbine (DFIG) small-signal stability |
| **Sliding Mode Control (SMC)** | Drives system state to a "sliding surface" — robust to disturbances | EV chargers, PV inverters |
| **Model Predictive Control (MPC)** | Predicts future states, optimizes over a receding horizon | Microgrids, energy storage management |
| **Fuzzy Logic Control** | Human-like rules using fuzzy sets — handles imprecision | MPPT, load management |
| **Droop Control** | Proportional P-f and Q-V relationship for grid-forming inverters | Microgrid frequency/voltage regulation |
| **Virtual Synchronous Generator (VSG)** | Makes inverters mimic synchronous generator inertia | Grid stability with high inverter penetration |
| **Reinforcement Learning (RL) Control** | Agent learns optimal policy via environment interaction | Energy management, demand response |

**Dr. Chatterjee's Focus — LQR/LQI for DFIG:**
- Doubly Fed Induction Generator (DFIG) wind turbines have complex multi-variable dynamics
- LQI adds an integrator state to LQR — eliminates steady-state error under disturbances
- Provides superior small-signal stability margin vs conventional PI controllers

#### Small Signal Stability — Why It Matters
- Power systems can experience low-frequency oscillations (0.1–3 Hz) when generators interact dynamically
- These can grow unstable with high renewable penetration
- **Small signal stability analysis** uses eigenvalue methods to check stability margins
- Emerging AI-based controllers aim to guarantee stability even under uncertain renewable output

---

### PILLAR 2: Artificial Intelligence (AI) for Sustainable Energy

#### AI's Role in Energy Systems

<br>

**A. Forecasting & Prediction**
- **LSTM (Long Short-Term Memory)** networks: Best for time-series forecasting of wind speed, solar irradiance, and load demand
- **Random Forest / GBM**: Predicts solar power from weather parameters
- Accurate forecasting → better scheduling → fewer curtailments, lower cost

**B. Control & Optimization**
- **Deep Reinforcement Learning (DRL / DQN)**: Learns optimal energy dispatch policy in real-time microgrids
- **Multi-Agent RL**: Multiple DG sources / EV aggregators each run their own RL agent, coordinate via communication
- **Evolutionary Algorithms (GA, PSO, ACO)**: Optimize controller parameters (e.g., PID gains, SHE switching angles)
- **Physics-Informed Neural Networks (PINNs)**: Combines physical laws with neural networks — ensures physical consistency

**C. Fault Detection & Diagnostics**
- **Convolutional Neural Networks (CNN)**: Extract features from power signal waveforms for fault classification
- **MRDWT + PNN (Dr. Chatterjee's work)**: Maximum Resolution Discrete Wavelet Transform + Probabilistic Neural Network for ECG / power signal anomaly classification
- Can detect incipient faults in wind turbines, transformers, and transmission lines

**D. Energy Management Systems (EMS)**
- AI-based EMS can reduce electricity cost by up to 67% vs conventional fixed-rule systems
- Manages solar generation, storage charging/discharging, grid import/export, and EV charging simultaneously

#### AI Paradigms Emerging in Energy
- **Federated Learning**: Multiple sites train a shared model without sharing raw data — privacy-preserving for smart meters
- **Explainable AI (XAI)**: SHAP, LIME — makes AI decisions interpretable for grid operators
- **Digital Twins**: AI-powered virtual replica of a power plant or microgrid for real-time simulation and anomaly detection
- **LLMs for Grid Cybersecurity**: Large Language Models emerging for threat detection and intelligent SCADA monitoring

---

### PILLAR 3: Cybersecurity for Sustainable Energy (Cyber Physical Systems)

#### What Is a Cyber Physical System (CPS)?

A Cyber Physical System tightly integrates:
- **Physical layer**: Generators, transformers, transmission lines, sensors
- **Communication layer**: SCADA, IEC 61850, DNP3, IoT, smart meters, PMUs
- **Cyber layer**: Control algorithms, EMS, DMS, data servers

Modern smart grids, microgrids, EV charging networks, solar plants — **all are CPS**. This is both their strength and their vulnerability.

#### Why Energy Systems Are Prime Cyber Targets
- Attacking a power grid causes **cascading blackouts** affecting millions
- Energy infrastructure is "always-on" — operators cannot easily shut down for patching
- Highly distributed architecture = massively expanded **attack surface**
- Legacy SCADA systems often run unpatched software

#### Real-World Energy Cyber Attacks

| Event | Year | Attack Type | Impact |
|---|---|---|---|
| **Stuxnet** | 2010 | Malware on PLCs | Destroyed Iranian nuclear centrifuges |
| **Ukraine Power Grid** | 2015 | Spear phishing + malware | 230,000 customers lost power |
| **Ukraine Grid Attack 2** | 2016 | Industroyer malware | Transmission substation shutdown |
| **Colonial Pipeline** | 2021 | Ransomware | US fuel supply disrupted for days |
| **Solar Winds** | 2020 | Supply chain attack | Compromised 18,000+ organizations |

#### Major Attack Categories on Energy CPS

**1. False Data Injection Attacks (FDIA)** ← Dr. Chatterjee's core research area
- Attacker injects carefully crafted false measurements into SCADA / state estimation
- System appears normal to bad data detectors — attack is **stealthy**
- Can cause: wrong dispatch decisions, overloads, financial losses, blackouts
- Targets: PMUs, smart meters, RTUs

**2. Denial of Service (DoS) / Distributed DoS**
- Floods communication channels — control signals delayed or lost
- DFIG wind turbine controllers lose communication → turbine trips offline
- Can be combined with FDIA for compound attacks

**3. Replay Attacks**
- Attacker records legitimate control/sensor signals, replays them later
- Makes physical process appear normal while attacker does something else

**4. Man-in-the-Middle (MitM)**
- Intercepts and modifies messages between SCADA and field devices
- Targets: IEC 61850 GOOSE messages, Modbus, DNP3

**5. Supply Chain Attacks**
- Compromised hardware/software before it reaches the energy facility
- Increasingly common vector for sophisticated state actors

**6. Ransomware**
- Encrypts SCADA or EMS databases — operators lose visibility
- Company pays or goes blind to grid operations

#### AI-Based Detection and Defense

Modern defense uses AI/ML to detect the above attacks:

| AI Method | Application |
|---|---|
| **CNN + LSTM** | Detect FDI + DoS attacks simultaneously in SCADA streams |
| **Autoencoders** | Anomaly detection — learn normal behavior, flag deviations |
| **Fuzzy Broad Learning (CP-BLS)** | FDIA detection with up to 99.99% accuracy |
| **Graph Neural Networks (GNN)** | Detect topological attacks on power network |
| **Federated Learning** | Distributed anomaly detection without centralizing data |
| **LLMs** | Intelligent threat analysis, natural language incident response |

**Defense Strategies:**
- **Moving Target Defense (MTD)**: Continuously changes system parameters to confuse attackers
- **Blockchain for SCADA**: Immutable logs of control commands — detect tampering
- **Zero Trust Architecture**: Every device, every message must authenticate — no implicit trust
- **Digital Twin Monitoring**: Shadow model detects divergence between virtual and physical state

#### India-Specific Context
- India's power grid increasingly SCADA-controlled and internet-connected
- Smart meter rollout (~250 million by 2025) vastly expands attack surface
- **CERT-In** and **NCIIPC** (National Critical Information Infrastructure Protection Centre) are primary cyber defense agencies
- India has experienced documented intrusion attempts on power utilities (Mumbai grid incident, 2020)

---

## Questions to Ask 


1. 
   > *"False Data Injection Attacks that bypass bad data detection are designed using knowledge of the grid topology. As renewable DG penetration grows and grid topology changes dynamically, does this make FDIA harder or easier for attackers — and how does your research address the moving-topology problem?"*

2. > *"You've worked on LQI control for DFIG small-signal stability. With AI-based controllers like Deep RL now being proposed — do you believe they can provide provable stability guarantees comparable to LQR/LQI, or is explainability and safety a fundamental barrier to AI replacing classical optimal control in critical energy systems?"*

3. > *"In a Cyber Physical System, a cyber attack can cause a physical consequence (like a blackout) and a physical fault can look like a cyber anomaly. How do you design detection systems that correctly distinguish between a natural grid fault and a cyber-induced disturbance — especially for DFIG-based wind farms?"*

4. > *"Federated Learning is proposed for privacy-preserving cybersecurity across distributed smart meters. But federated learning itself is vulnerable to poisoning attacks from compromised clients. How do you see this contradiction being resolved for energy CPS deployments in India?"*

5. > *"Given your experience as President of the Cyber Society at IIT(ISM) — what do you think is the single most underestimated cybersecurity threat to India's power grid right now, that neither industry nor academia is adequately addressing?"*

---

##  Key Terms Glossary

| Term | Meaning |
|---|---|
| CPS | Cyber Physical System — tight integration of computing, communication, and physical processes |
| SCADA | Supervisory Control and Data Acquisition — industrial control system for power grids |
| FDIA | False Data Injection Attack — stealthy attack on state estimation |
| DoS | Denial of Service — flooding communications to cause delay/loss |
| PMU | Phasor Measurement Unit — high-speed GPS-synchronized power measurement device |
| RTU | Remote Terminal Unit — field device reporting to SCADA |
| IEC 61850 | International standard for substation communication |
| DNP3 | Distributed Network Protocol 3 — SCADA communication protocol |
| DFIG | Doubly Fed Induction Generator — most common wind turbine generator type |
| LQR / LQI | Linear Quadratic Regulator/Integrator — optimal state-space controllers |
| MPC | Model Predictive Control — receding horizon optimization-based control |
| RL / DRL | Reinforcement Learning / Deep RL — AI learning by reward signals |
| LSTM | Long Short-Term Memory — neural network for time-series data |
| XAI | Explainable AI — making AI decisions interpretable |
| LVRT / FRT | Low Voltage Ride-Through / Fault Ride-Through — ability of wind turbines to stay connected during grid faults |
| Moving Target Defense | Cybersecurity strategy that continuously changes system parameters |
| CERT-In | Computer Emergency Response Team — India |
| NCIIPC | National Critical Information Infrastructure Protection Centre — India |
| VSG | Virtual Synchronous Generator — inverter mimicking generator inertia |
| Digital Twin | AI-powered virtual replica of a physical energy system |

---

## **My Profiles**

- LinkedIn: [Link](https://www.linkedin.com/in/un-animesh/)
- GitHub: [Link](https://github.com/unanimesh)
- Email: [Link](https://mailto:un.animesh@zohomail.com)
