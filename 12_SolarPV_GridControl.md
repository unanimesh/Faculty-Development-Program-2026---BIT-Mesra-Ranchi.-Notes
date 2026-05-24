#  Faculty Development Program 2026 - BIT Mesra
## Session 12: Control of Solar PV System Integrated with Grid

---

##  Speaker Details

| Field | Details |
|---|---|
| **Name** | Dr. Tirthadip Ghose |
| **Designation** | Professor, Department of Electrical & Electronics Engineering |
| **Institution** | Birla Institute of Technology (BIT) Mesra, Ranchi |
| **Research Areas** | Demand Response, Renewable Energy Grid Integration, Microgrid Operation & Control, AC-DC Power Systems |
| **Funded Project** | AICTE-funded microgrid research (current) |
| **Workshop** | Organized SERB-sponsored KARYASHALA on "Power Electronics Interface for Green Energy Sources and e-Mobility" (July 2022) |

> **Dr. Ghose is a core BIT Mesra faculty member** who organizes high-end research workshops sponsored by the Government of India (SERB). He is also the **collaborator of Dr. Subhojit Ghosh (Session 5, NIT Raipur)** and **Dr. Kalyan Chatterjee (Session 4, IIT ISM Dhanbad)** — both named him in their research networks.

### Research Interests 
1. **Demand Response** — load management for grid stability
2. **Integration of Renewable Sources to Grid** — PV-grid control, power quality
3. **Microgrid Operation and Control** — AC, DC, hybrid microgrids
4. **AC-DC Coexistence in Power Networks** — grid-connected PV inverter design
5. **Multifunctional PV Inverter** — his students developed and validated via MATLAB/Simulink, Microcontroller, and OPAL-RT real-time hardware-in-loop simulation

### Notable Work 
- **"PN Inference Based Autonomous Sequential Restoration of Distribution Networks"** — autonomous distribution network self-healing
- **Blockchain-based Decentralized Energy Intra-Trading with Battery Storage** — shared on LinkedIn (2022)
- **Co-authored with Dr. Subhojit Ghosh (NIT Raipur)** — confirmed research collaboration
- **Research with Dr. Kalyan Chatterjee (IIT ISM)** — confirmed from Dr. Chatterjee's collaborator list
- Students under his guidance developed: **Multifunctional PV Inverter** (MATLAB/Simulink + Microcontroller + OPAL-RT)

---

##  Topic Deep Dive: Control of Solar PV System Integrated with Grid

This topic is one of the most practically important in modern power engineering — **every rooftop solar panel, every utility-scale solar farm in India needs a well-controlled grid integration system.** Dr. Ghose brings both theoretical depth and hands-on OPAL-RT real-time simulation experience to this.

---

### 1. Solar PV System Architecture — Grid-Connected

**Two-stage grid-connected PV system:**

```
Solar PV Array
      ↓
[DC-DC Boost Converter]  ← Stage 1: MPPT — extracts maximum power
      ↓
DC Link (Capacitor)
      ↓
[DC-AC Inverter (VSI)]   ← Stage 2: Grid synchronization + current control
      ↓
LCL Filter               ← Filters switching harmonics
      ↓
Point of Common Coupling (PCC)
      ↓
Grid (3-phase / 1-phase)
```

**Single-stage grid-connected PV system** (Dr. Ghose's multifunctional inverter focus):
```
Solar PV Array → [DC-AC Inverter (with MPPT built-in)] → LCL Filter → Grid
```
- Fewer components → higher efficiency → lower cost
- But: control is more complex — MPPT and grid control must be handled simultaneously by one inverter
- This is the emerging topology for **multifunctional PV inverters**

---

### 2. Stage 1: MPPT — Maximum Power Point Tracking

A PV panel's I-V curve shifts with temperature and irradiance. The **Maximum Power Point (MPP)** is where the panel delivers maximum power (P = V × I is maximized).

**MPPT Algorithms:**

| Algorithm | Method | Pros | Cons |
|---|---|---|---|
| **Perturb & Observe (P&O)** | Perturbs duty cycle, observes ΔP | Simple, widely used | Oscillates around MPP; poor under fast irradiance change |
| **Incremental Conductance (INC)** | Tracks dP/dV = 0 (dI/dV = -I/V) | Better accuracy than P&O | Slightly more complex |
| **Fractional Open Circuit Voltage** | V_MPP ≈ 0.76 × V_OC | Very fast | Approximate only |
| **PSO / GA-based** | Metaheuristic search | Handles partial shading | Computationally heavy |
| **ANN-based MPPT** | Neural net maps irradiance + temp → duty cycle | Fast, accurate | Needs training data |
| **Model Predictive MPPT** | MPC directly on inverter switch states | Very fast dynamic response | Requires accurate model |

**Dr. Ghose's focus**: Multifunctional inverter control that integrates MPPT with simultaneous power quality compensation — both functions in one control algorithm.

---

### 3. Stage 2: Grid-Connected Inverter Control

The inverter must:
- Inject **sinusoidal current in phase with grid voltage** (unity power factor, or controllable PF)
- Maintain **DC link voltage** stable
- Synchronize with the grid frequency and phase
- Comply with grid standards: IEEE 1547, IEC 61727, CEA 2019 (India)

#### The d-q Frame Current Control (Industry Standard)

The standard control architecture:

```
Measured Grid Voltage (Vabc)
         ↓
    PLL (Phase Locked Loop)  ← Extracts grid phase angle θ
         ↓
Transform Iabc → I_d, I_q (Park Transform using θ)
         ↓
PI Controllers:
  I_d error → V_d reference  (controls active power P)
  I_q error → V_q reference  (controls reactive power Q)
         ↓
Inverse Park Transform → Vabc reference
         ↓
PWM Generator → Gate signals to inverter switches
```

**Key elements:**
- **PLL (Phase Locked Loop)**: Synchronizes inverter output to grid frequency (50 Hz in India). Grid disturbances, harmonics, voltage sags can destabilize PLL — a key research area
- **I_d control** → controls Active Power (P = 3/2 × V_d × I_d)
- **I_q control** → controls Reactive Power (Q = -3/2 × V_d × I_q)
- Setting I_q reference = 0 → unity power factor (pure active power injection)
- Setting I_q ≠ 0 → reactive power support for grid voltage regulation

---

### 4. Multifunctional PV Inverter — Dr. Ghose's Specialty

Traditional PV inverters do only one job: inject solar power into the grid. A **Multifunctional PV Inverter** simultaneously provides additional grid support functions using the same hardware:

| Function | Description | Benefit |
|---|---|---|
| **Active Power Injection** | Inject PV-generated power | Primary function |
| **Reactive Power Compensation** | Injects/absorbs Q to regulate PCC voltage | Eliminates need for separate capacitor bank / STATCOM |
| **Harmonic Compensation** | Cancels load harmonics at PCC | Eliminates need for separate active filter |
| **Unbalance Compensation** | Corrects unbalanced current injection | Improves power quality |
| **Voltage Ride-Through (LVRT)** | Stays connected during grid voltage dips | Grid code compliance |
| **Islanding Detection** | Detects when grid is lost → disconnects safely | Safety critical |

**Dr. Ghose's students implemented this on:**
- MATLAB/Simulink simulation
- Microcontroller (hardware prototype)
- **OPAL-RT real-time simulator** — the most advanced validation step

> This is exactly the "multifunctional PV inverter" that modern Indian grid codes (CEA 2019) are beginning to mandate — Dr. Ghose's work is directly industry-relevant.

---

### 5. OPAL-RT — Real-Time Hardware-in-Loop (HIL) Simulation

A key tool in Dr. Ghose's lab and a distinguishing feature of his research validation.

**What is OPAL-RT?**
- A real-time digital simulator based on FPGA + multi-core processors
- Runs power system models **at actual hardware speed** (microsecond time steps)
- Used to test control algorithms on real hardware before connecting to the actual grid

**OPAL-RT Test Setup for PV Grid Control:**
```
OPAL-RT (runs the PV + Grid model in real-time)
      ↕ (analog signals — voltages, currents)
Real DSP/Microcontroller (runs the actual control algorithm)
      ↕ (PWM signals)
OPAL-RT (receives and applies PWM to the simulated converter)
```

This is **Control Hardware-in-Loop (CHIL)** — the real controller fights against a simulated power system. Any bug in the control firmware is caught here, not on a live grid.

**Why OPAL-RT matters:**
- Eliminates the risk of testing on a real grid (which can cause blackouts or equipment damage)
- More accurate than pure simulation — includes real measurement noise, delays, ADC quantization
- Required by many power utilities before commissioning a new controller

---

### 6. Power Quality Challenges in Grid-Connected PV

When solar PV is connected to the grid, several power quality issues arise:

#### A. Voltage Rise (The most common issue)
- PV injects power → current flows backward through feeder impedance → voltage at PCC rises
- IEEE 1547 / CEA 2019: voltage must stay within ±10% of nominal
- **Control solution**: Reactive power absorption by PV inverter (set I_q to absorb Q)

#### B. Harmonic Injection
- Inverter switching creates harmonic currents (5th, 7th, 11th, 13th most common)
- LCL filter attenuates harmonics but doesn't eliminate them
- **Control solution**: Resonant controllers, repetitive controllers, or active harmonic cancellation in multifunctional inverter

#### C. DC Offset Injection
- Inverter imperfections inject small DC current into the AC grid
- Causes transformer saturation, meter errors
- IEEE 1547 limits DC injection to < 0.5% of rated current

#### D. Frequency Deviation
- In weak grids or microgrids with high PV penetration, frequency can deviate
- **Control solution**: Frequency-Watt (f-P) droop — PV reduces output when frequency rises

#### E. Islanding
- If grid disconnects but PV keeps running, it creates an uncontrolled "island"
- Dangerous for line workers who think the line is dead
- **Detection methods**: Passive (under/over frequency, voltage), Active (signal injection — AFD, SFS), Remote (communication-based)

---

### 7. Advanced Control Strategies for Grid-Connected PV

Building on Sessions 4 & 5, these are the control methods applied to PV-grid systems:

| Control Method | Application in PV-Grid | Dr. Ghose's Relevance |
|---|---|---|
| **PI in d-q frame** | Standard current control | Baseline for all PV inverter control |
| **PR (Proportional Resonant)** | Harmonic current control | Better than PI for AC-domain control (no need for d-q transform) |
| **Deadbeat Control** | Ultra-fast current tracking | Requires accurate plant model |
| **Model Predictive Control (FCS-MPC)** | Predicts and selects optimal switch state | Very fast, no PWM needed |
| **Sliding Mode Control** | Robust nonlinear control | Handles irradiance variations |
| **Droop Control** | Multi-inverter power sharing | Needed when multiple PV inverters share a bus |
| **Virtual Synchronous Generator (VSG)** | Adds inertia to PV inverter | Stabilizes weak grids with high PV penetration |
| **Nonlinear / Backstepping** | Handles severe nonlinearities | Research area for partial shading + grid faults |

---

### 8. Grid Standards Every PV Engineer Must Know (India)

| Standard | Scope | Key Requirements |
|---|---|---|
| **CEA (Technical Standards) 2019** | India — mandatory for grid connection | Voltage ride-through, anti-islanding, power factor, harmonics |
| **IEEE 1547-2018** | USA standard (widely referenced) | Volt-VAR, Freq-Watt, ride-through, islanding |
| **IEC 61727** | International PV grid connection | General requirements |
| **IEC 61000-3-2** | Harmonic limits | THD < 5% for grid-connected systems |
| **IS 16169** | India — PV inverter standard | Performance requirements |

**India-specific**: With 100+ GW solar target, MNRE and CEA are rapidly updating grid codes to mandate reactive power support, LVRT, and frequency response from all PV installations > 1 MW.

---

### 9. Demand Response + PV Grid Integration (Dr. Ghose's Broader Research)

Dr. Ghose's AICTE-funded research connects PV grid control with demand response:
- When PV generation exceeds local demand, instead of curtailing or feeding back to the grid, **demand response shifts flexible loads** (water heaters, EV chargers, HVAC) to absorb the surplus
- This is the concept behind **Demand-Side Management (DSM)** — manage loads to match generation, not just generation to match loads
- **Blockchain-based decentralized energy trading**: Dr. Ghose's work on peer-to-peer energy trading — excess PV generation sold directly to neighbors via a blockchain ledger (no utility intermediary)
- **PN (Petri Net) Inference for distribution network restoration**: Sequential, autonomous fault recovery in distribution networks with PV sources

---

## Questions to Ask



1.
   > *"Your multifunctional PV inverter validated on OPAL-RT simultaneously handles active power injection, reactive power compensation, and harmonic cancellation. When all three functions conflict for the available inverter current capacity — for example, during a low-irradiance period when both reactive support and harmonic cancellation are needed — what is your priority scheme, and how does the control algorithm resolve the capacity constraint in real-time?"*

2. > *"In your SERB KARYASHALA workshop you covered 'Power Electronics Interface for Green Energy Sources and e-Mobility' — bringing together PV and EV charging in one framework. Given that EV charging is a nonlinear, rapidly varying load connected at the same PCC as a PV inverter, what are the specific control interactions you've observed, and how does the PV inverter's d-q current controller respond to the EV charger's harmonic injection?"*

3. > *"The Phase Locked Loop (PLL) is the Achilles heel of grid-connected PV inverters — it can become unstable under weak grid conditions (high grid impedance), voltage sags, or harmonic distortion. India's rural distribution feeders are typically weak grids. What PLL topology — SOGI-PLL, DSOGI-PLL, or FLL-based — do you recommend for Indian rural grid conditions, and have you validated this on OPAL-RT?"*

4. > *"Your blockchain-based decentralized energy intra-trading research is fascinating. In a BIT Mesra context — if the campus installs rooftop PV across multiple departments, is the blockchain peer-to-peer trading model technically and legally feasible within an institutional boundary today, without a DISCOM interconnection agreement?"*

5. > *"For high PV penetration scenarios — where PV covers 50–70% of local load — voltage rise becomes the binding constraint that limits PV deployment. Between reactive power absorption by the inverter and active power curtailment, which strategy better preserves PV energy yield while keeping voltage within CEA 2019 limits, and what does your simulation show for a typical Indian feeder topology?"*

---

##  Key Terms Glossary

| Term | Meaning |
|---|---|
| MPPT | Maximum Power Point Tracking — algorithm to extract max power from PV panel |
| P&O | Perturb & Observe — simplest MPPT algorithm |
| INC | Incremental Conductance MPPT — tracks dP/dV = 0 |
| DC-DC Boost | Converter that steps up PV panel voltage to DC link level |
| VSI | Voltage Source Inverter — converts DC to AC |
| PCC | Point of Common Coupling — where PV system connects to the grid |
| LCL Filter | Inductor-Capacitor-Inductor filter — attenuates switching harmonics |
| d-q Frame | Synchronous reference frame — transforms AC signals to DC quantities for easy PI control |
| PLL | Phase Locked Loop — tracks grid voltage phase angle for synchronization |
| I_d | d-axis current — controls active power (P) |
| I_q | q-axis current — controls reactive power (Q) |
| PR Controller | Proportional-Resonant — resonates at fundamental/harmonic frequency for zero steady-state error |
| FCS-MPC | Finite Control Set MPC — selects optimal inverter switch state at each sample |
| VSG | Virtual Synchronous Generator — inverter mimics synchronous machine inertia |
| LVRT | Low Voltage Ride-Through — staying grid-connected during voltage dips |
| OPAL-RT | Real-time digital simulator for power electronics validation |
| CHIL | Control Hardware-in-Loop — real controller tested against simulated power system |
| Multifunctional Inverter | PV inverter that also does reactive power / harmonic compensation |
| THD | Total Harmonic Distortion — power quality measure |
| CEA 2019 | Central Electricity Authority Technical Standards 2019 — India's grid code |
| STATCOM | Static Synchronous Compensator — reactive power device (multifunctional PV inverter can replace this) |
| Demand Response | Adjusting loads in response to generation/grid conditions |
| Blockchain Energy Trading | Peer-to-peer decentralized energy market using blockchain ledger |
| PN Inference | Petri Net-based method for autonomous distribution network restoration |

---

## **My Profiles**

- LinkedIn: [Link](https://www.linkedin.com/in/un-animesh/)
- GitHub: [Link](https://github.com/unanimesh)
- Email: [Link](https://mailto:un.animesh@zohomail.com)