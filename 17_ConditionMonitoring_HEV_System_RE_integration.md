#  Faculty Development Program 2026 - BIT Mesra
## Session 17: Condition Monitoring of HEV System with Renewable Energy Integration

---

##  Speaker Details

| Field | Details |
|---|---|
| **Name** | Dr. Soumya Chatterjee |
| **Designation** | Assistant Professor, Department of Electrical Engineering |
| **Institution** | National Institute of Technology (NIT) Durgapur, West Bengal |
| **Email** | schatterjee.ee@nitdgp.ac.in |
| **Institution Joined** | August 2022 |
| **Google Scholar Citations** | 1,538+ |

### Academic Background 

| Degree | Thesis | Institution | Grade/Year |
|---|---|---|---|
| B.Tech. (EE) | — | — | — |
| M.Tech. | "Investigations on influence of viscosity, conductivity and permittivity of water droplet on partial discharge inception voltage of polymeric insulators" | — | Good |
| **Ph.D.** | **"Studies on measurement time reduction techniques for insulation diagnostics in high voltage"** | — | **10/10, First Class** |

> Ph.D. thesis submitted March 2019, defended September 2019, degree awarded October 2019.

### Career History 

| Period | Role | Institution |
|---|---|---|
| Before academia | Electrical Power Distribution Engineer | **Calcutta Electric Supply Corporation Limited (CESC), Kolkata** |
| Earlier faculty | Assistant Professor, EEE | **Birla Institute of Technology (BIT) Mesra** ← Your institution! |
| Earlier faculty | Assistant Professor, EE | Techno India University, Kolkata |
| Guest Faculty | EE Department | Jadavpur University, Kolkata |
| **2022–Present** | **Assistant Professor, EE** | **NIT Durgapur** |

> **Dr. Soumya Chatterjee was a faculty member at BIT Mesra before joining NIT Durgapur.** This is a direct institutional connection — he taught in the same department hosting this FDP!

### Research Areas 

1. **Condition Monitoring** — his primary area
2. **Insulation Diagnosis** — high voltage insulation in transformers, motors, cables, insulators
3. **Signal and Image Processing with Machine Learning** — for fault feature extraction
4. **Graph Theory and Complex Networks** — Visibility Graph applied to PD signals
5. **Power System Asset Management** — predictive maintenance, aging assessment
6. **High Voltage Engineering** — partial discharge, dielectric spectroscopy

### Key Publications

| Paper | Contribution |
|---|---|
| **"Detection and Classification of Partial Discharge Sources for Condition Monitoring of Electrical Insulation Employing Visibility Graph Theory"** | Novel graph-based feature extraction from PD signals — replaces conventional statistical features |
| **"Deep Learning Aided Power Quality Disturbance Detection with Improved Time-Frequency Resolution Employing Adaptive Superlet Transform"** | Superlet Transform + deep learning for PQ event classification |
| **"Condition Monitoring of Polymeric Insulators: A Remote Diagnostic Framework with Improved Intermediate Hydrophobicity Grade Detection"** | Remote, non-invasive insulator health monitoring |
| **"Modified Stockwell Transform with Optimum Selection of Window Parameters for Improved Time-Frequency Analysis of Bio-potentials"** | Signal processing technique applicable to both biomedical and power signals |
| **"Recognition of Power System Transients Based on Higher Order Statistical Moments using Empirical Mode Decomposition"** | EMD-based PQ disturbance classification |
| **"Identification of Salt and Salinity Level of 11kV Contaminated Porcelain Disc Insulator using STD-MRA Analysis of Leakage Current"** | Distribution insulator contamination diagnosis |
| **"Stress Control on RTV Coated Porcelain Disc Insulator using BaTiO₃ Nano-composites"** | Novel nano-composite coating for high-voltage insulator protection |

---

## Topic Deep Dive: Condition Monitoring of HEV System with Renewable Energy Integration

This session connects **condition monitoring** (Dr. Soumya Chatterjee's core expertise) with **Hybrid Electric Vehicles (HEV)** and **renewable energy** — the FDP's central theme. It answers: *how do you know when the electrical components inside an HEV or renewable energy system are degrading, before they fail catastrophically?*

---

### 1. What Is Condition Monitoring?

**Condition Monitoring (CM)** is the practice of continuously or periodically measuring physical parameters of equipment to detect degradation before it leads to failure.

**The Philosophy — From Reactive to Predictive Maintenance:**

```
Reactive:   Run to failure → Repair/Replace → Unexpected downtime, safety risk
Preventive: Replace at fixed schedule → Often replaced too early (waste) or too late (failure)
Predictive: Monitor continuously → Detect early degradation → Replace exactly when needed
             ↑ This is Condition Monitoring — Dr. Soumya Chatterjee's domain
```

**Why CM matters for HEV and Renewable Energy Systems:**
- HEV components (traction motor, inverter, battery) are expensive — unplanned failure costs ₹5–20 lakh per incident
- Wind turbine gearbox failure costs ₹30–80 lakh + 2–4 weeks downtime
- Solar inverter IGBT failure in a solar plant → loss of generation + revenue
- **Predictive maintenance using CM can reduce maintenance costs by 25–30% and unplanned downtime by 70–75%**

---

### 2. HEV System — The Components That Need Monitoring

A **Hybrid Electric Vehicle (HEV)** combines an internal combustion engine (ICE) with an electric drive:

```
┌──────────────────────────────────────────────────────┐
│                    HEV SYSTEM                        │
│                                                      │
│  [ICE Engine] ←→ [Power Split Device]                │
│                         ↕                            │
│  [Traction Motor/Generator 1 (MG1)]                  │  ← CM needed
│  [Traction Motor/Generator 2 (MG2)]                  │  ← CM needed
│                         ↕                            │
│  [Power Electronics (Inverter/Converter)]            │  ← CM needed
│                         ↕                            │
│  [High Voltage Battery Pack (200–400V, 5–10 kWh)]    │  ← CM needed (SOH)
│                         ↕                            │
│  [DC-DC Converter (HV to 12V LV)]                    │  ← CM needed
└──────────────────────────────────────────────────────┘
```

**BEV (Battery Electric Vehicle)** — same monitoring needs minus the ICE.

**HEV + Renewable Integration** — when the HEV battery is charged by rooftop solar or a wind-powered charging station, the renewable source and its power electronics also need condition monitoring.

---

### 3. Condition Monitoring of the Traction Motor — Dr. Soumya Chatterjee's Core Expertise Applied

**Why traction motors fail:**
- Insulation breakdown due to: thermal aging, moisture, partial discharge from inverter switching, mechanical vibration
- Bearing failure (most common, ~40% of motor failures)
- Stator winding inter-turn faults
- Rotor eccentricity

#### A. Partial Discharge (PD) Monitoring — Dr. Chatterjee's Specialty

**What is Partial Discharge?**
A PD is a small electrical discharge that occurs in a localized region of insulation where the electric field exceeds the dielectric strength locally, but does not bridge the full gap between conductors. It is a **precursor to complete insulation breakdown**.

**Why PD matters in HEV motors:**
- Modern HEV traction motors are fed by high-switching-frequency inverters (10–50 kHz, GaN/SiC)
- The fast voltage pulses (dV/dt up to 50 kV/μs) cause **voltage reflections** at motor terminals → **overvoltage spikes** up to 2× DC bus voltage
- These overvoltages stress the motor winding insulation → initiate partial discharges
- PD erodes insulation progressively → eventually → winding-to-ground fault → motor failure

**Dr. Chatterjee's contribution — Visibility Graph Theory for PD:**
PD signals are complex, random-looking time series. Conventional statistical features (mean, skewness, kurtosis) are insufficient for reliable PD classification.

**Visibility Graph** transforms a time-series signal into a graph:
- Each data point → a node in the graph
- Two nodes are "visible" (connected by an edge) if there is a direct line-of-sight between the corresponding time-series values (no taller value in between)
- Different PD sources produce graphs with distinct topological properties (degree distribution, clustering coefficient, path length)
- Machine learning classifiers (SVM, Random Forest, CNN) then classify PD source from graph features

**Result**: More reliable PD source classification → correctly identifies whether the PD is from:
- Void discharges (internal air bubbles in insulation)
- Surface discharges (tracking along insulation surface)
- Corona discharge (sharp electrode in air)

#### B. Motor Stator Insulation Diagnosis — Dielectric Spectroscopy

**Frequency Domain Spectroscopy (FDS):**
- Applied to motor windings and transformers
- Measures complex permittivity of insulation across a range of frequencies (0.1 mHz – 10 kHz)
- From the FDS response, estimates: moisture content, aging level, contamination
- **Dr. Chatterjee's Ph.D. thesis**: "Measurement time reduction techniques for insulation diagnostics in high voltage" — makes FDS practical by reducing the hours-long test duration

#### C. Bearing Fault Detection

Bearing faults generate characteristic vibration frequencies (BPFO, BPFI, BSF — Ball Pass Frequency Outer/Inner race, Ball Spin Frequency). Detected from:
- **Vibration sensors** (accelerometers)
- **Motor current signature analysis (MCSA)** — bearing faults modulate stator current
- **EMD (Empirical Mode Decomposition)** — Dr. Chatterjee's signal processing technique

#### D. Power Quality Disturbance Detection — HEV Grid Interaction

Dr. Chatterjee published on **deep learning for power quality disturbance detection using Adaptive Superlet Transform**. In HEV charging contexts:
- Grid-connected EV chargers cause PQ disturbances: harmonics, voltage sags, flicker
- These PQ events can themselves damage HEV components if undetected
- His Superlet Transform achieves better time-frequency resolution than standard STFT or wavelet for short-duration transient PQ events

---

### 4. Condition Monitoring of the HV Battery — SOH Estimation

The battery pack is the most expensive component in an EV/HEV (₹4–10 lakh for a typical pack). Its **State of Health (SOH)** determines remaining useful life.

**Battery degradation mechanisms:**
- Lithium plating (during fast charging in cold)
- SEI (Solid Electrolyte Interphase) layer growth → increased internal resistance
- Active material loss → reduced capacity
- Mechanical stress → electrode cracking

**Condition monitoring approaches:**

| Method | Measured Parameter | CM Insight |
|---|---|---|
| **Electrochemical Impedance Spectroscopy (EIS)** | Impedance vs frequency | Internal resistance, SEI thickness, diffusion |
| **Incremental Capacity Analysis (ICA)** | dQ/dV curve peaks | Identifies degradation mechanisms |
| **Voltage relaxation analysis** | Open circuit voltage decay | Lithium plating detection |
| **Temperature mapping** | Cell-level temperature | Hot spots → accelerated aging |
| **Acoustic sensing** | Ultrasound through cell | Detects gassing, delamination |

**Dr. Soumya Chatterjee's connection**: His insulation diagnosis and signal processing expertise directly transfers to battery CM — both involve analyzing complex signals (FDS, impedance spectra) to infer internal degradation state.

---

### 5. Condition Monitoring of Power Electronics in HEV and Renewable Systems

**Critical components:**
- **IGBTs / SiC MOSFETs** — in traction inverters, charger, DC-DC converter
- **DC link capacitors** (electrolytic or film) — most failure-prone passive component
- **Gate drivers** — can fail due to overvoltage or thermal stress

**IGBT degradation CM:**
- Monitor: junction temperature (Tj), on-state voltage VCE(sat), thermal impedance Zth
- **Degradation indicators**: VCE(sat) increases as bond wires degrade; Zth increases as solder delamination occurs
- **Prognostic approach**: Fit degradation model, predict remaining useful life (RUL)

**Capacitor CM:**
- Monitor: capacitance, Equivalent Series Resistance (ESR)
- ESR increases as electrolyte dries out → increased ripple voltage → damage to other components
- ESR monitoring using ripple current injection or frequency-domain analysis

**Dr. Chatterjee's signal processing tools applied here:**
- **Empirical Mode Decomposition (EMD)**: Decomposes non-stationary switching-frequency signals
- **Stockwell Transform**: Time-frequency analysis of inverter output for fault detection
- **Visibility Graph**: Converts power electronics fault signatures to graph features for ML classification

---

### 6. Renewable Energy Integration in HEV — The CM Connection

**Renewable charging introduces additional CM challenges:**

| Renewable Source | CM Challenge for HEV Charging |
|---|---|
| **Solar PV + EVSE** | PV panel soiling/degradation → under-performance detection; PV inverter IGBT aging |
| **Wind + EVSE** | Wind turbine gearbox/generator bearing CM; grid harmonics from wind inverter stressing EV charger |
| **V2G (bidirectional)** | Additional battery cycling → accelerated degradation; more frequent CM needed |
| **Wireless charging** | Coil misalignment detection, thermal monitoring of receiver coil inside EV |

**Dr. Chatterjee's CV explicitly mentions**: "The objective is to maximize the share of renewable energies in the related energy mix (Solar PV and Wind) and minimize the electricity cost" — confirming his renewable energy interest alongside condition monitoring.

---

### 7. Signal Processing Toolkit — Dr. Soumya Chatterjee's Methods

These are the technical tools at the heart of his research:

| Method | What It Does | Applied To |
|---|---|---|
| **Stockwell (S) Transform** | Time-frequency representation with frequency-dependent resolution | PQ disturbance detection, bio-signals |
| **Modified Stockwell Transform** | Optimized window parameters for improved resolution | Better than standard ST for short transients |
| **Adaptive Superlet Transform** | Multi-cycle transform with super-resolution in time-frequency | PQ events, inverter fault signatures |
| **EMD (Empirical Mode Decomposition)** | Decomposes signal into Intrinsic Mode Functions (IMFs) | Non-stationary fault signals |
| **Visibility Graph (VG)** | Converts time-series → graph → topological features | PD source classification |
| **MFDFA (Multifractal Detrended Fluctuation Analysis)** | Extracts fractal scaling features | EEG, potentially battery/motor signals |
| **STD-MRA (Standard Deviation of Multi-Resolution Analysis)** | Wavelet-based feature extraction | Insulator contamination diagnosis |
| **Machine Learning** | SVM, Random Forest, CNN, deep learning | Classification of PD, faults, PQ events |
| **Graph Theory** | Network topology metrics (degree, clustering, path length) | PD source fingerprinting |

---

### 8. India Context

- India has **1.7 million+ EVs** (2024) — growing rapidly; traction motor and battery CM is critical for fleet reliability
- Indian climate challenges: high ambient temperatures (40–50°C) → accelerated insulation aging; monsoon humidity → increased PD inception risk
- India's distribution transformers are heavily loaded and aging — Dr. Chatterjee's insulation CM directly applies to preventing transformer failures
- **CESC, Kolkata** (his former employer) — India's oldest and largest private distribution utility — his real-world power distribution experience informs his CM research priorities
- India's solar + wind capacity growing fast → CM of renewable energy equipment (PV inverters, wind generators) is a growing industry need

---

## Questions to Ask 

1. 
   > *"In your Visibility Graph approach to PD classification, you transform a PD time series into a graph and extract topological features. When a traction motor is fed by a SiC inverter at high dV/dt, the PD pulses are superimposed on fast switching transients that are orders of magnitude larger. How do you isolate the genuine PD signal from switching noise in the graph construction step — and does the visibility algorithm degrade at the SNR levels seen in a real HEV inverter environment?"*

2. > *"Your Ph.D. thesis focused on 'measurement time reduction techniques for insulation diagnostics.' Frequency Domain Spectroscopy can take 6–12 hours for one complete low-frequency sweep. In a field-deployed HEV or wind turbine generator, you cannot take the equipment offline for hours. What is the practical minimum measurement time your technique achieves, and what diagnostics fidelity is sacrificed?"*

3. > *"You applied the Adaptive Superlet Transform for power quality disturbance detection. In a V2G-capable EV charging station — where bidirectional power flow creates non-stationary current waveforms with both charging and discharging transients — how does the Superlet Transform handle the direction reversal events, and can it distinguish a V2G discharge ramp from a genuine power quality disturbance?"*

4. > *"Battery SOH estimation for HEV traction packs typically uses Electrochemical Impedance Spectroscopy, which your insulation FDS expertise closely parallels — both are frequency-domain impedance measurements on a dielectric/electrochemical system. Have you applied or considered applying your FDS measurement time reduction techniques to battery EIS to enable faster, on-board SOH estimation during EV charging events?"*

5. > *"As a former BIT Mesra faculty member — looking at the FDP topics covered over these sessions (EV charging, PV control, wind control, cybersecurity, microgrids) — where do you see the most natural entry point for a new BIT Mesra researcher to build a condition monitoring research programme that complements rather than duplicates what NIT Durgapur and others are already doing?"*

---

##  Key Terms Glossary

| Term | Meaning |
|---|---|
| CM | Condition Monitoring — continuous measurement to detect equipment degradation |
| HEV | Hybrid Electric Vehicle — combines ICE and electric drive |
| BEV | Battery Electric Vehicle — pure electric |
| PD | Partial Discharge — localized insulation breakdown precursor |
| PDIV | Partial Discharge Inception Voltage — voltage at which PD starts |
| FDS | Frequency Domain Spectroscopy — measures insulation permittivity vs frequency |
| EIS | Electrochemical Impedance Spectroscopy — battery internal state measurement |
| SOH | State of Health — measure of battery capacity relative to new |
| RUL | Remaining Useful Life — predicted time to failure |
| Visibility Graph (VG) | Graph constructed from time-series where each point is a node |
| EMD | Empirical Mode Decomposition — adaptive decomposition of non-stationary signals |
| Stockwell Transform | Time-frequency analysis with frequency-dependent resolution |
| Superlet Transform | Advanced time-frequency method for super-resolution |
| MFDFA | Multifractal Detrended Fluctuation Analysis — fractal feature extraction |
| STD-MRA | Standard Deviation of Multi-Resolution Analysis — wavelet feature |
| MCSA | Motor Current Signature Analysis — detects motor faults from stator current |
| BPFO/BPFI | Ball Pass Frequency Outer/Inner race — bearing fault vibration frequencies |
| VCE(sat) | Collector-emitter saturation voltage — IGBT aging indicator |
| ESR | Equivalent Series Resistance — capacitor degradation indicator |
| Solder Delamination | Separation of solder layer in IGBT power module — aging indicator |
| dV/dt | Rate of voltage rise in inverter output — high in GaN/SiC systems |
| CESC | Calcutta Electric Supply Corporation — Dr. Chatterjee's former employer |

---

## **My Profiles**

- LinkedIn: [Link](https://www.linkedin.com/in/un-animesh/)
- GitHub: [Link](https://github.com/unanimesh)
- Email: [Link](https://mailto:un.animesh@zohomail.com)

