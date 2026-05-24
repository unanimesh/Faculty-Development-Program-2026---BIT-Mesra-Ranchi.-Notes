#  Faculty Development Program 2026 - BIT Mesra
## Session 8: Energy Management for Sustainable Microgrid

---

##  Speaker Details

| Field | Details |
|---|---|
| **Name** | Dr. Arghya Mitra |
| **Designation** | Associate Professor, Department of Electrical Engineering |
| **Institution** | Visvesvaraya National Institute of Technology (VNIT), Nagpur |
| **Email** | mitraarghya@eee.vnit.ac.in |
| **ORCID** | 0000-0002-8316-4072 |
| **Google Scholar Citations** | 1,500+ |
| **Publications** | 80+ research papers |

### Academic Background

| Degree | Year | Institution |
|---|---|---|
| B.E. (Electrical Engineering) | 2002 | Jadavpur University, Kolkata |
| M.Tech. (Electrical Engineering) | 2008 | University of Calcutta |
| Ph.D. | 2015 | **IIT Kharagpur** |

### Awards
- **POSOCO Power System Award, 2016** — one of India's most prestigious power sector research awards

### Funded Projects
1. **PI — MoE SPARC Project**: *"Global Grid: The Future of Earth"* — Ministry of Education funded project on the concept of a globally interconnected supergrid
2. **Co-PI — DST Project under EU-India Horizon 2020 Program** — International collaboration between Indian and European institutions on sustainable energy
3. **Completed — BARC (Bhabha Atomic Research Centre) Project** — Nuclear energy + grid integration research

### Key Research Areas
- **Microgrid Energy Management Systems (EMS)**
- **Demand Response for Isolated Microgrids**
- **PV Forecasting using LSTM + Attention Networks**
- **DC Microgrid Voltage Regulation & Droop Control**
- **Multi-energy Vector Integration** (electricity, hydrogen, heat)
- **Hybrid AC/DC Microgrid Architecture**
- **Nanogrid Technologies for Rural Electrification**
- **Renewable Integration: PV-Hydro-Battery DC Microgrids**
- **Machine Learning for Load Forecasting & Battery EMS**
- **Optimal Location for Solar PV Farm Installation**

### Key Publications Directly on Today's Topic

1. **"Demand Response Enabled Energy Management Tool for an Isolated Microgrid Integrated With Different Energy Vectors"** — Uses multiple energy carriers (electricity, hydrogen, heat) in an isolated microgrid EMS with demand response
2. **"A Hybrid LSTM-Attention Residual Network for Photovoltaic Forecasting in Isolated Microgrid Environments"** — AI-based solar forecasting for EMS in isolated microgrids with unpredictable weather
3. **"Adaptive Energy Management Strategy for Sustainable Voltage Control of Photovoltaic-Hydro-Battery Integrated DC Microgrid"** — *Journal of Cleaner Production* (2021) — Real hybrid renewable DC microgrid EMS
4. **"Adaptive Energy Management Strategy for Optimal Power Flow Control of Hybrid DC Microgrid"** — *SpliTech 2020*, Croatia
5. **"Machine Learning-Based Load Forecasting and Battery Energy Management for Efficient Renewable Integration"**
6. **"Analytic Hierarchy Process-Based Optimal Load Scheduling Framework in an Islanded Distribution Network"**
7. **"Optimizing Renewable Energy Integration in Microgrids Using Graph-Based Optimization Modeling Language"**
8. **"Resiliency-Driven Approach of DC Microgrid Voltage Regulation Based on Droop Index Control for High Step-Up DC-DC Converter"** — *Int. Trans. Electrical Energy Systems, Wiley* (2022)

### VNIT Connection
- Note: **Dr. Ritesh Kumar Keshri (Session 1)** is also from VNIT Nagpur — making Sessions 1 and 8 from the same department. Dr. Mitra's student projects include **"Protection of a DC Microgrid using a Z Source Circuit Breaker"** — directly connecting to Session 3 (Z-Source inverter, Dr. Kadwane).

---

##  Topic Deep Dive: Energy Management for Sustainable Microgrid

---

### 1. What Is a Microgrid?

A **microgrid** is a localized energy system that can:
- Generate electricity from local Distributed Energy Resources (DERs)
- Store energy in batteries or other storage
- Supply loads within a defined boundary
- **Operate in two modes:**
  - **Grid-Connected mode**: Exchanges power with the main grid
  - **Islanded (isolated) mode**: Operates autonomously without the main grid

```
┌─────────────────────── MICROGRID ───────────────────────┐
│                                                         │
│  Solar PV ──┐                              ┌── Homes    │
│  Wind ──────┤                              ├── Industry │
│  Diesel Gen─┤──► [AC/DC Bus + EMS]  ───────┤── EV Chrgr │
│  Fuel Cell ─┤                              ├── Hospital │
│  Battery ───┘                              └── Loads    │
│                          ↕                              │
└──────────────── Main Grid (when connected) ─────────────┘
```

**Why Microgrids Are Critical for Sustainability:**
- Enable **100% renewable-powered** local communities
- Provide **energy resilience** — local power during grid outages
- Essential for **rural electrification** in India (Dr. Mitra's nanogrid work)
- Enable integration of diverse energy sources (PV + wind + battery + fuel cell + hydro)

---

### 2. What Is the Energy Management System (EMS)?

The **EMS** is the brain of the microgrid — the software and control system that decides:
- **What** to generate (which sources to use)
- **When** to generate/store/discharge
- **How much** to generate from each source
- **When** to buy/sell power with the main grid
- **How** to prioritize loads (critical vs. non-critical)

**EMS Goals (often competing):**
1. Minimize operating cost
2. Minimize carbon emissions
3. Maximize renewable utilization
4. Ensure voltage and frequency stability
5. Maximize battery life (avoid over-charge / deep-discharge)
6. Satisfy all load demands at all times
7. Respond to demand-side flexibility (Demand Response)

---

### 3. Hierarchical Control Architecture of a Microgrid

Modern microgrid EMS uses a **three-layer hierarchical structure**:

<br>

####  Primary Control Layer (Milliseconds)
- **Job**: Instantaneous voltage and frequency regulation
- **Methods**: Droop control (P-f, Q-V), Virtual Synchronous Generator (VSG)
- **Runs on**: Local controllers of each inverter/converter
- **Dr. Mitra's work**: Droop Index Control for DC microgrid voltage regulation via high step-up DC-DC converter
- **No communication needed** between units — purely local

####  Secondary Control Layer (Seconds to Minutes)
- **Job**: Correct steady-state errors left by primary control; power sharing optimization
- **Methods**: Consensus algorithms, centralized PI, MPC, event-triggered control
- **Runs on**: Microgrid Central Controller (MGCC)
- Coordinates power sharing between DERs
- **2025 findings**: Adaptive droop + event-triggered consensus reduces communication overhead by 80% while maintaining voltage accuracy within ±2%

####  Tertiary/Supervisory EMS Layer (Minutes to Days)
- **Job**: Economic optimization, demand response, grid interaction scheduling
- **Methods**: MILP, MPC, Stochastic Optimization, Reinforcement Learning, Metaheuristics (PSO, GA, Jaya)
- **Runs on**: Central dispatch server / cloud-based EMS with SCADA interface
- **Dr. Mitra's focus**: This is his primary research domain

---

### 4. Optimization Formulations in Microgrid EMS

The EMS scheduling problem is typically formulated as:

**Objective Function (Minimize):**
```
min Σ [C_gen(t) × P_gen(t) + C_batt(t) × P_batt(t) - C_export(t) × P_export(t)]
```
Where:
- C_gen = generation cost (diesel, gas turbine)
- C_batt = battery degradation cost
- C_export = revenue from selling power to grid

**Subject to Constraints:**
- Power balance: Generation + Storage = Load ± Grid exchange (always)
- Battery SOC limits: SOC_min ≤ SOC(t) ≤ SOC_max
- Ramp rate limits for generators
- Voltage and frequency limits
- Renewable curtailment limits

**Problem Type: Mixed-Integer Nonlinear Programming (MINLP)** — NP-hard for large microgrids

**Solution Methods Used:**

| Method | Type | Dr. Mitra's Relevance |
|---|---|---|
| **MILP** | Deterministic optimization | Benchmark method |
| **PSO (Particle Swarm Optimization)** | Metaheuristic | Used in EMS scheduling |
| **Jaya Algorithm** | Metaheuristic | Shown to outperform PSO in microgrid scheduling |
| **MPC (Model Predictive Control)** | Receding horizon optimization | 25-40% cost reduction vs rule-based |
| **Stochastic MPC** | Handles uncertainty | For variable solar/wind forecasts |
| **Deep Reinforcement Learning (DRL)** | AI-based, learns policy | Emerging; handles uncertainty well |
| **Analytic Hierarchy Process (AHP)** | Multi-criteria decision | Dr. Mitra's islanded network load scheduling |

---

### 5. Dr. Mitra's Key Specialty: Multi-Energy Vector Microgrids

One of the most advanced and emerging concepts in sustainable energy systems.

**Traditional microgrid**: Only manages **electrical power**

**Multi-Energy Vector (MEV) Microgrid**: Manages **multiple energy carriers simultaneously**:

| Energy Vector | Sources | Storage | Loads |
|---|---|---|---|
| **Electricity** | PV, Wind, Diesel, Fuel Cell | Lithium-ion Battery, Supercapacitor | All electrical loads |
| **Hydrogen** | Electrolyzer (from PV surplus) | Hydrogen tank | Fuel cell (reconverts to electricity) |
| **Heat/Thermal** | CHP (Combined Heat and Power), Solar thermal | Hot water tank | Space heating, industrial heat |
| **Natural Gas** | Grid gas, biogas | Gas storage | Gas turbine, CHP, cooking |

**Why Multi-Energy Vector EMS?**
- Electricity surplus from solar can be stored as **hydrogen** (long-duration storage) rather than curtailed
- CHP units generate both power and heat simultaneously — joint optimization saves 30–40% vs separate
- Hydrogen + fuel cell enables **seasonal storage** — solar surplus in summer stored as H₂ for winter use
- **Connects to Session 2** (Green Hydrogen — Dr. Sarode) and **Session 6** (PEM Fuel Cell — Dr. Lalitesh Kumar)

---

### 6. Demand Response (DR) in Microgrid EMS

**Demand Response** = Shifting or curtailing loads in response to grid signals or price incentives.

**Dr. Mitra's work**: Demand Response Enabled EMS for isolated microgrid with different energy vectors.

**Types of DR:**

| Type | Mechanism | Example |
|---|---|---|
| **Price-Based DR** | Consumers respond to dynamic electricity prices | Shift EV charging from peak (₹10/kWh) to off-peak (₹4/kWh) |
| **Incentive-Based DR** | Utility pays consumers to reduce load on demand | Hospital sheds non-critical HVAC during grid stress |
| **Direct Load Control** | Utility directly switches off loads remotely | Air conditioners cycled off for 15 min during peak |
| **Interruptible/Curtailable** | Consumer agrees to allow curtailment in exchange for lower rates | Industrial consumers |

**DR in Isolated Microgrids:**
- Particularly critical when there's **no grid backup** — demand must always match supply
- Solar/wind intermittency creates frequent supply-demand mismatches
- DR can **defer or advance loads** to match renewable generation peaks
- **Optimal DR scheduling** using AHP/MILP/PSO: Dr. Mitra's published approach

---

### 7. AI/ML in Microgrid EMS (Dr. Mitra's AI Work)

#### PV Forecasting — LSTM + Attention Residual Network
Dr. Mitra's most recent AI publication:
- **Problem**: Solar irradiance is highly unpredictable in isolated microgrid regions (mountains, islands) with drastic weather changes
- **Architecture**: Hybrid LSTM-Attention Residual Network
  - **LSTM**: Captures long-term temporal dependencies in irradiance/weather data
  - **Attention Mechanism**: Focuses on the most relevant past time steps for the current forecast
  - **Residual connections**: Prevents vanishing gradient — enables deeper, more accurate networks
- **Impact**: More accurate PV forecasting → better EMS scheduling → fewer diesel generator starts → lower cost and emissions

#### Machine Learning for Load Forecasting + Battery EMS
- **Load forecasting**: Predicts future electricity demand using historical data + weather + calendar features
- **Battery EMS**: ML-based controller decides optimal charge/discharge timing
- Together: Proactive EMS that anticipates supply-demand mismatches before they occur

#### Graph-Based Optimization Modeling
- Models the microgrid as a graph (nodes = DERs, edges = power flows)
- Graph-based optimization language (AMPL/GAMS/Pyomo) formulates the EMS problem systematically
- Enables scalable EMS for multi-microgrid networks

---

### 8. Nanogrid — Dr. Mitra's Rural India Vision

A **nanogrid** is a scaled-down microgrid for single households or small clusters:

```
Solar PV (1–5 kW) + Battery (5–20 kWh) + Small Diesel/Fuel Cell backup
→ Powers: Lights, fans, pumps, phone charging, small appliances
→ Target: Rural India villages without reliable grid access
```

- **Dr. Mitra's review paper** on nanogrid technologies specifically targets **rural electrification of India**
- Two control approaches reviewed: **centralized vs. decentralized** source-load coordination
- Connects to India's PM-KUSUM scheme (solar for rural farmers) and energy access goals

---

### 9. India Context

- India has **200,000+ remote villages** and island territories where grid connectivity is weak or absent — ideal nanogrid/microgrid candidates
- India's **RE capacity**: 90+ GW solar, 46+ GW wind (2024) — but intermittency demands smart EMS
- **PM-KUSUM, DESP, RESCO model** — government pushing distributed solar with storage
- Dr. Mitra's **Solar Farm Location Optimization** paper directly aids Maharashtra's solar deployment planning
- **SPARC "Global Grid"** project: India's ambition to participate in a transcontinental power superhighway — connecting Eurasian and African grids for 24×7 renewable power globally

---

## Questions to Ask 

1. 
   > *"In your demand response-enabled EMS for isolated microgrids with multiple energy vectors — how do you handle the temporal coupling between hydrogen storage (slow dynamics, hours-to-days) and battery storage (fast dynamics, seconds-to-minutes) within the same optimization framework? Do you use multi-timescale MPC or a bilevel formulation?"*

2. > *"Your LSTM-Attention Residual Network for PV forecasting is designed for isolated microgrids with drastic and unpredictable weather. How does the attention mechanism specifically improve performance compared to vanilla LSTM — and how many days of historical data are needed before the model reaches useful accuracy for a new deployment site?"*

3. > *"In your Adaptive Energy Management Strategy for PV-Hydro-Battery DC Microgrids — what happens during a multi-day cloudy period when both PV is near zero and the hydro resource is seasonal? Does the adaptive strategy gracefully degrade to diesel backup, and how is load shedding prioritized?"*

4. > *"The MoE SPARC project you lead is titled 'Global Grid: The Future of Earth' — a transcontinental supergrid concept. Given that India, China, Europe, and the Middle East have very different regulatory frameworks and geopolitical relationships, what do you see as the most critical non-technical barrier to realizing a global grid — and is there a realistic path forward within this decade?"*

5. > *"For rural India nanogrid deployment, decentralized control is often preferred because communication infrastructure is unreliable. But decentralized EMS cannot achieve global optimality — how large is the efficiency gap between centralized and decentralized EMS in your studied nanogrid configurations, and is it worth the communication cost in practice?"*

---

##  Key Terms Glossary

| Term | Meaning |
|---|---|
| Microgrid | Local energy system with DERs that can island from the main grid |
| Nanogrid | Household-scale microgrid for rural/remote electrification |
| EMS | Energy Management System — brain of the microgrid |
| DER | Distributed Energy Resource (solar PV, wind, battery, fuel cell, diesel) |
| Islanded Mode | Microgrid operating autonomously, disconnected from main grid |
| Grid-Connected Mode | Microgrid exchanging power with the main utility grid |
| Demand Response (DR) | Shifting/curtailing loads in response to price or grid signals |
| Multi-Energy Vector | EMS managing electricity + hydrogen + heat + gas simultaneously |
| MILP | Mixed Integer Linear Programming — optimization method for EMS scheduling |
| MINLP | Mixed Integer Nonlinear Programming — more general, harder to solve |
| PSO | Particle Swarm Optimization — nature-inspired metaheuristic |
| Jaya Algorithm | Simple metaheuristic algorithm (no tuning parameters) for optimization |
| MPC | Model Predictive Control — receding horizon optimization |
| Stochastic MPC | MPC that handles uncertain inputs (solar/wind forecasts) |
| DRL | Deep Reinforcement Learning — AI agent learns optimal EMS policy |
| AHP | Analytic Hierarchy Process — multi-criteria decision-making |
| LSTM | Long Short-Term Memory — neural network for time-series forecasting |
| Attention Mechanism | Neural network component that weights importance of different time steps |
| Droop Control | Primary control: P-f and Q-V proportional regulation without communication |
| SOC | State of Charge — battery energy level |
| CHP | Combined Heat and Power — simultaneous electricity + heat generation |
| SPARC | Scheme for Promotion of Academic and Research Collaboration (MoE, India) |
| EU-India Horizon 2020 | EU-India joint research funding program |
| POSOCO | Power System Operation Corporation of India |

---


## **My Profiles**

- LinkedIn: [Link](https://www.linkedin.com/in/un-animesh/)
- GitHub: [Link](https://github.com/unanimesh)
- Email: [Link](https://mailto:un.animesh@zohomail.com)

