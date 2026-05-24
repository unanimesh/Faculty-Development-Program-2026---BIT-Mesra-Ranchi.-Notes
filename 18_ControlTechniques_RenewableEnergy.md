#  Faculty Development Program 2026 - BIT Mesra
## Session 18: Control Techniques for Renewable Energy Applications

---

##  Speaker Details

| Field | Details |
|---|---|
| **Name** | Dr. Aditya R. Gautam (Aditya Raw Gautam) |
| **Designation** | Assistant Professor, Department of Electrical & Electronics Engineering |
| **Institution** | Birla Institute of Technology and Science (BITS), Pilani, Rajasthan |
| **Room** | 2210-R, FD-II, EEE Department |
| **Google Scholar Citations** | 603+ |
| **Research Group** | Deepak Fulwani's Lab (IIT Jodhpur collaboration) |

### Academic Background 

| Degree | Institution | Period |
|---|---|---|
| Ph.D. (Electrical Engineering) | IIT Jodhpur (under Prof. Deepak Fulwani) | — |
| Researcher | IIT Jodhpur, EE Programme | July 2013 – August 2015 |
| Current | BITS Pilani, EEE Department | July 2019 – Present |

### Research Areas 

- **Control of Power Electronic Converters** — his primary area
- **DC Microgrids** — constant power load stability, 2ω ripple, SMC control
- **AC-DC and DC-AC Converters** — for renewable energy integration
- **Sliding Mode Control (SMC)** — adaptive SMC for converters and inverters
- **2nd Order Harmonic Ripple Mitigation** — in single-phase inverters and DC microgrids
- **Electric Vehicles** — control of bidirectional EV charging systems
- **Renewable Energy Technologies** — solar PV MPPT, wind integration
- **Power Factor Correction** — adaptive SMC-based loss-free resistor

### World-Class Collaborator — Prof. Josep M. Guerrero

His Google Scholar profile lists co-author **Prof. Josep M. Guerrero** — one of the world's most cited researchers in microgrid and distributed energy systems (IEEE Fellow, currently at Center for Research on Microgrids, Huanjiang Lab, Zhejiang University, China). Co-authoring with Guerrero places Dr. Gautam's work in the global top tier of microgrid research.

Also co-authors with **Prof. Akshay Rathore (IEEE Fellow, National University of Singapore)** — another globally recognized power electronics researcher.

### Key Verified Publications

| Paper | Journal | Year | Contribution |
|---|---|---|---|
| **"Ripple Mitigation With Improved Line-Load Transients Response in a Two-Stage DC-DC-AC Converter: Adaptive SMC Approach"** | *IEEE Transactions on Industrial Electronics* | 2018 | Adaptive SMC eliminates 2ω ripple from DC link in single-phase renewable inverters |
| **"Adaptive Sliding Mode Based Loss-Free Resistor for Power-Factor Correction Application"** | *IEEE Transactions on Industry Applications* | 2019 | Adaptive SMC for PFC — loss-free and parameter-insensitive |
| **"Constant Power Loads and Their Effects in DC Distributed Power Systems: A Review"** | *Renewable and Sustainable Energy Reviews* | 2017 | Comprehensive review of CPL instability — 487+ citations |
| **"Control Strategies and Power Decoupling Topologies to Mitigate 2ω-Ripple in Single-Phase Inverters: A Review and Open Challenges"** | *IEEE* | 2020 | Defines the state-of-art in 2ω ripple control — open challenges |
| **"Transformer-based Time Series Prediction of Maximum Power Point for Solar PV Cells"** | *Energy Science & Engineering* | 2022 | ML Transformer model for MPPT prediction |
| **"Techno-economic and Reliability Assessment of an Off-grid Solar-Powered Energy System"** | *Applied Energy* | 2024 | Techno-economic sizing of standalone solar systems |
| **"Hybrid Protection Algorithm for Power System with Renewable Energy Generation using Stockwell Transform and Wigner Distribution Function"** | *The Journal of Engineering* | 2022 | Power system protection in renewable-integrated grid |
| **"A Double Input DC/DC Buck-Boost Converter for Low Voltage Solar/Wind Systems"** | Int. J. Chem-Tech Research | — | Multi-input converter for combining PV + wind |

---

##  Topic Deep Dive: Control Techniques for Renewable Energy Applications

Dr. Gautam sits at the precise intersection of **control theory** and **power electronics** — designing controllers that make renewable energy converters behave optimally despite the inherent variability and nonlinearity of solar, wind, and EV charging systems.

---

### 1. Why Control Is the Central Challenge in Renewable Energy Systems

**The Physics Problem:**
- Solar PV: output varies with irradiance (0–1000 W/m²) and temperature (0–75°C) — nonlinear I-V curve
- Wind: power varies with v³ — huge dynamic range
- Battery: charging/discharging voltage varies with SOC — nonlinear chemistry
- Loads: constant power loads (motors, inverters) exhibit **negative incremental impedance** — destabilizing

**The Control Goal:**
Design feedback controllers that, despite all this variability and nonlinearity, ensure:
1. Maximum power extraction (MPPT)
2. Stable voltage and current
3. High power quality (low THD, unity PF)
4. Fast dynamic response
5. Robustness to parameter uncertainty

---

### 2. Adaptive Sliding Mode Control (SMC) — Dr. Gautam's Core Technique

**Why Adaptive SMC for renewable energy converters?**
- Converters are nonlinear switched systems — classical linear control (PI) degrades at off-nominal conditions
- SMC provides **inherent robustness** to parameter variations and disturbances — perfect for variable renewable sources
- **Adaptive SMC** additionally estimates unknown parameters in real-time — handles component aging and environmental changes

#### Dr. Gautam's Key SMC Result — Ripple Mitigation (IEEE Trans. Ind. Electron. 2018)

**The 2ω Ripple Problem** (one of his signature research contributions):

In a two-stage DC-DC-AC converter for single-phase renewable applications:
```
PV / Battery (DC)
      ↓
[DC-DC Converter] → DC Link Capacitor → [Single-Phase Inverter] → Grid
```

**The problem**: A single-phase inverter draws power from the DC link at **twice the output frequency (2ω = 100 Hz for 50 Hz grid)**. This causes a 100 Hz ripple on the DC link voltage:
- Ripple stresses the electrolytic DC link capacitor → reduces its lifetime
- Ripple propagates back through DC-DC converter → affects MPPT accuracy
- Ripple appears in grid current → increases THD → PQ violation

**Conventional solution**: Large electrolytic capacitor — bulky, short lifetime (5–8 years vs 25-year PV panel), failure-prone.

**Dr. Gautam's adaptive SMC solution**:
- Designs an adaptive sliding mode controller for the DC-DC converter
- The SMC actively **regulates the DC link voltage** against the 100 Hz ripple — eliminating the need for large capacitors
- Simultaneously improves **line-load transient response** — faster recovery when grid voltage or load changes
- Result: Smaller capacitor, longer converter life, better dynamic performance

**Published in IEEE Transactions on Industrial Electronics** — the most prestigious journal for power electronics applications.

#### Adaptive SMC for Power Factor Correction (IEEE Trans. Ind. Appl. 2019)

**Power Factor Correction (PFC):**
- AC-DC converters (EV chargers, solar inverters with AC input) draw distorted current from the grid → poor power factor
- PFC forces the converter to draw sinusoidal current in phase with grid voltage → unity PF → no reactive power, no harmonics

**Dr. Gautam's approach — Loss-Free Resistor (LFR) concept:**
- The AC-DC converter is controlled to emulate a **pure resistor** from the grid's perspective
- Current drawn from grid becomes purely sinusoidal and proportional to grid voltage → unity PF
- **Adaptive SMC** estimates the LFR parameter adaptively — no manual tuning needed even as grid conditions change
- **Loss-free**: The emulated resistor dissipates no power (unlike a real resistor) — all energy is transferred to the output

---

### 3. Constant Power Loads in DC Microgrids — Dr. Gautam's Most-Cited Work

**The Constant Power Load (CPL) Problem** (487+ citations paper, 2017):

In DC microgrids with renewable sources:
- Load converters (motor drives, laptop chargers, LED drivers) draw constant power: P = V × I = constant
- When source voltage drops: V↓ → I must increase to maintain P → current increases despite voltage decrease
- This looks like **negative resistance** (dV/dI < 0) → destabilizes the DC bus → voltage oscillations → collapse

**Why this is critical for renewable systems:**
- Solar PV + DC microgrid + motor loads → classic CPL instability scenario
- EV charging + DC bus → EV charger is a CPL → can destabilize the bus
- Off-grid renewable systems with battery storage → battery internal resistance + CPL → oscillation risk

**Dr. Gautam's review paper** thoroughly classifies:
- CPL stability criteria (eigenvalue analysis, Lyapunov methods)
- **Passive stabilization**: add resistance/inductance/capacitance at CPL terminal
- **Active stabilization**: modify converter control → virtual impedance emulation, SMC
- **Input filter design**: LCL or LC filter with damping to attenuate CPL negative impedance effect

**Connection to FDP**: This CPL problem is exactly why Dr. Lalitesh Kumar (Session 6) uses IDA-PBC for PEM fuel cell boost converters — the fuel cell output feeds a CPL (the grid-tied inverter), and port-Hamiltonian control is one rigorous way to guarantee stability.

---

### 4. Control Techniques Taxonomy for Renewable Energy

Building on Sessions 4, 5, 12, 14 — here is how Dr. Gautam's work fits into the broader landscape:

| Control Category | Techniques | Dr. Gautam's Application |
|---|---|---|
| **Linear Control** | PI, PID, PR, lead-lag | Baseline for MPPT, current control |
| **Sliding Mode Control** | Fixed SMC, Adaptive SMC, Super-Twisting | 2ω ripple elimination, PFC, CPL stabilization |
| **Passivity-Based / Energy** | IDA-PBC, Hamiltonian | Connects to Session 6 — stabilizes CPL via energy shaping |
| **Predictive Control** | FCS-MPC, Deadbeat | Fast current tracking in grid converters |
| **Adaptive Control** | MRAC, Self-tuning, Adaptive SMC | Handles parameter variation in aging converters |
| **Intelligent / Soft** | Fuzzy, Neural Network, RL | MPPT under partial shading, EMS |
| **Model-Free / Data-Driven** | ML Transformer (Dr. Gautam), RL | Solar MPP prediction |

#### Adaptive SMC vs Fixed SMC — Dr. Gautam's Distinction

| Feature | Fixed SMC | **Adaptive SMC** |
|---|---|---|
| Parameter tuning | Manual, fixed gains | **Auto-adapts in real time** |
| Chattering | Present | Reduced via adaptive gain |
| Robustness | Good for known uncertainty | **Better for unknown/varying parameters** |
| Convergence | May be slow if gains mismatch | **Faster — gains adapt to error magnitude** |
| Dr. Gautam's use | — | 2ω ripple, PFC, CPL stabilization |

---

### 5. Solar PV MPPT — ML Transformer Model (2022)

Dr. Gautam's recent AI work: using a **Transformer neural network** (the architecture behind ChatGPT) for solar MPP prediction.

**Why Transformer for MPPT?**
- Traditional P&O MPPT perturbs duty cycle every few milliseconds — reacts to change, doesn't predict
- Under fast irradiance changes (passing clouds), P&O lags → misses the true MPP temporarily
- Transformer model: trained on historical irradiance + temperature + MPP data → **predicts** the upcoming MPP before the irradiance change happens
- **Proactive MPPT** → better energy yield under dynamic weather conditions
- Published in *Energy Science & Engineering* (Wiley) — a journal focused on practical energy technology

---

### 6. Off-Grid Solar System — Techno-Economic Assessment (2024)

Dr. Gautam's most recent Applied Energy paper:
- **Techno-economic + reliability assessment** of off-grid solar-powered energy system
- Sizes PV panels + battery storage + inverter + backup generator optimally
- Considers: capital cost, O&M cost, replacement cost, net present cost (NPC), LCOE
- Reliability metrics: Loss of Power Supply Probability (LPSP)
- **India relevance**: Direct application for rural electrification in Rajasthan, Jharkhand, and remote NE India

---

### 7. The 2ω Ripple — A Complete Picture

Since this is one of Dr. Gautam's signature topics, a deeper explanation:

**Why does 2ω ripple occur?**

Power flow in single-phase system: `p(t) = V·I·cos(φ) - V·I·cos(2ωt - φ)`

The first term: constant (average power). The second term: **pulsating at 2ω** — this is the 2ω ripple.

In a DC microgrid with a single-phase inverter:
- Average power = solar or battery power (DC, constant)
- But the grid takes pulsating power at 100 Hz
- The DC source must "absorb" this pulsation → it appears as voltage ripple on DC link

**Solutions (Dr. Gautam's review covers all):**

| Approach | Method | Trade-off |
|---|---|---|
| **Large capacitor** | Store 100 Hz energy in big electrolytic cap | Bulky, short life, failure risk |
| **Active power decoupling** | Extra LC circuit + switches + controller | Added hardware cost |
| **Adaptive SMC (Dr. Gautam)** | Controller rejects ripple without extra hardware | Control complexity |
| **Battery as buffer** | Battery absorbs 100 Hz pulsation | Increases battery cycling → SOH degradation |
| **H6 / HERIC inverter** | Modified topology reduces ripple at source | Higher switching losses |

---

## Questions to Ask 

1. 
   > *"Your adaptive SMC for 2ω ripple mitigation regulates the DC link voltage against 100 Hz disturbance while simultaneously maintaining MPPT from the solar PV source. These two objectives conflict — tight DC link regulation requires drawing non-constant power from the PV, which moves the PV away from its MPP. How does your adaptive SMC resolve this conflict, and what is the actual MPPT efficiency penalty compared to a large capacitor solution?"*

2. > *"Your 2017 review on Constant Power Load instability in DC distributed power systems has 487+ citations. Since then, CPL penetration has grown dramatically with the spread of DC microgrids, EV charging stations, and data centers. Which of the stabilization approaches you reviewed — passive, active, or input filter design — do you now believe is the most scalable for large DC microgrids with hundreds of EV chargers as CPLs?"*

3. > *"Your Transformer-based MPP prediction model enables proactive MPPT under fast irradiance changes. For a rooftop solar installation in Jharkhand — where monsoon cloud dynamics cause rapid, large irradiance transients — how much additional energy yield (% gain) does proactive Transformer-MPPT achieve over conventional P&O, and what is the minimum historical dataset size needed to train the model for a new location?"*

4. > *"Your adaptive SMC-based Loss-Free Resistor for PFC eliminates manual tuning by estimating the LFR parameter adaptively. In a V2G bidirectional EV charger, the 'load' seen by the AC grid switches between capacitive (charging) and inductive (discharging) characteristics depending on power flow direction. Can your adaptive LFR concept be extended to bidirectional PFC — and what is the stability challenge at the transition point between G2V and V2G modes?"*

5. > *"You co-authored with Prof. Josep Guerrero — one of the world's most cited microgrid researchers. What is the key research question in DC microgrid control that you and Prof. Guerrero believe the community has not yet adequately answered, and where do you see the next major breakthrough coming from?"*

---

##  Key Terms Glossary

| Term | Meaning |
|---|---|
| SMC | Sliding Mode Control — robust nonlinear control using a sliding surface |
| Adaptive SMC | SMC with real-time parameter estimation — no manual tuning needed |
| 2ω Ripple | Second harmonic (100 Hz) power pulsation on DC link in single-phase systems |
| CPL | Constant Power Load — exhibits negative incremental impedance → instability |
| LFR | Loss-Free Resistor — converter emulates a pure resistor from grid perspective |
| PFC | Power Factor Correction — forces sinusoidal, in-phase grid current draw |
| MPPT | Maximum Power Point Tracking |
| Proactive MPPT | Predicts future MPP using ML before irradiance changes |
| DC Microgrid | DC bus-based local power network (PV + battery + DC loads) |
| LPSP | Loss of Power Supply Probability — off-grid system reliability metric |
| LCOE | Levelized Cost of Energy — lifetime energy cost (₹/kWh) |
| NPC | Net Present Cost — total lifecycle cost of a renewable energy system |
| Techno-economic | Analysis combining technical performance AND economic cost |
| Negative Impedance | Property of CPL: current increases as voltage drops — destabilizes systems |
| Virtual Impedance | Software-emulated impedance in converter control — stabilizes CPL |
| Power Decoupling | Circuit/control technique to decouple 2ω ripple from DC source |
| Active Power Decoupling | Extra switching circuit + control to absorb 100 Hz pulsation |
| IDA-PBC | Interconnection and Damping Assignment PBC — energy-based CPL stabilization |
| Transformer Model | Deep learning architecture (self-attention) — used by Dr. Gautam for MPPT |

---

## **My Profiles**

- LinkedIn: [Link](https://www.linkedin.com/in/un-animesh/)
- GitHub: [Link](https://github.com/unanimesh)
- Email: [Link](https://mailto:un.animesh@zohomail.com)
