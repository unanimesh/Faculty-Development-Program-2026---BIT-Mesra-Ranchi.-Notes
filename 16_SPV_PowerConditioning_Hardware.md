#  Faculty Development Program 2026 - BIT Mesra
## Session 16: Development and Hardware Implementation of Power Conditioning System for SPV System

---

##  Speaker Details

| Field | Details |
|---|---|
| **Name** | Dr. Ajay Kumar |
| **Designation** | Assistant Professor, Department of Electrical Engineering |
| **Institution** | Punjab Engineering College (PEC), Deemed to be University, Chandigarh |
| **Email** | pec.edu.in (institutional) |
| **Google Scholar Citations** | 587+ |
| **Research Areas** | Power Electronics, Power Quality, Renewable Energy, Grid-tied Solar PV, Optimization |

### Academic Background 

| Degree | Focus | Institution |
|---|---|---|
| M.Tech. | Power Quality Improvement | **Malaviya National Institute of Technology (MNIT), Jaipur** |
| Ph.D. | Grid Integration of Photovoltaic Systems | **MNIT Jaipur** |

### Awards 

- **SERB Young Scientist** — Science and Engineering Research Board, Govt. of India — one of India's most competitive early-career research fellowships
- **Best Paper Award** — 11th IEEE Power India International Conference (PIICON 2024) — for paper titled **"Variable Step-size LMS Filter for Power Quality Enhancement using Grid Supportive Photovoltaic System"**

### What Makes His Profile Unique in This FDP

> His LinkedIn tagline literally reads: "Developed Multifunctional PV Inverter and its Control | MATLAB/Simulink | Microcontroller | OPAL-RT" — this is not just a theoretical researcher. He **builds and tests hardware**. Today's session is specifically about the **hardware journey** of taking a solar PV power conditioning system from simulation to real implementation.

> **Interesting BIT Mesra Connection**: Dr. Tirthadip Ghose (Session 12) also had a student who developed a Multifunctional PV Inverter validated on OPAL-RT — the same experimental platform. Dr. Ajay Kumar and Dr. Ghose are working on virtually the same hardware problem from different institutions!

### Key Research 

| Paper | Journal/Conference | Key Contribution |
|---|---|---|
| **"Real-time implementation of an SRF-based control strategy for efficient grid integration of solar PV system"** | *Engineering Research Express*, IOP, 2026 | SRF (Synchronous Reference Frame) control implemented and validated in real hardware for grid-connected SPV |
| **"Variable Step-size LMS Filter for Power Quality Enhancement using Grid Supportive Photovoltaic System"** | IEEE PIICON 2024 (**Best Paper Award**) | VSS-LMS adaptive filter algorithm for harmonic extraction in multifunctional PV system |
| **"Optimized and Robust Current Controller for Transformerless Grid-Integrated Photovoltaic Inverter"** | (Research paper) | Transformerless PV inverter with DC leakage current minimization |
| **"Comprehensive Review on Grid-tied Solar PV System"** | Review paper | Full architecture of grid-tied SPV: PV array → MPPT → DC-DC → inverter → control → grid |

---

##  Topic Deep Dive: Development and Hardware Implementation of Power Conditioning System for SPV

This session is **the most hands-on, hardware-focused session** of the FDP. While Sessions 5, 12, and 14 covered control algorithms in theory and simulation, Dr. Ajay Kumar focuses on the **practical journey from MATLAB simulation → DSP/microcontroller implementation → hardware prototype → OPAL-RT real-time validation**.

---

### 1. What Is a Power Conditioning System (PCS) for SPV?

A **Power Conditioning System** is the complete electronic interface between the solar PV array and the grid (or load). It conditions the raw, unregulated DC power from PV panels into clean, regulated AC power suitable for the grid.

**Complete PCS Architecture:**

```
Solar PV Array (Variable DC: 100–600V depending on irradiance & temp)
        ↓
[Stage 1: DC-DC Converter]
  — Boosts PV voltage to stable DC link
  — Runs MPPT algorithm (P&O / INC / etc.)
        ↓
DC Link Capacitor (400–800V regulated)
        ↓
[Stage 2: DC-AC Inverter (VSI)]
  — Converts DC to AC (230V/50Hz for single-phase; 415V/50Hz 3-phase)
  — Grid synchronization (PLL)
  — Current control (SRF / PR / deadbeat / LMS-based)
  — Power quality functions (harmonics, reactive power)
        ↓
LCL Filter (reduces switching harmonics to grid-acceptable levels)
        ↓
Point of Common Coupling (PCC) → Grid
```

**Single-stage alternative** (Dr. Ajay Kumar's focus):
- One inverter does both MPPT and grid current control simultaneously
- Fewer components → higher reliability → lower cost
- But: control is more complex

---

### 2. The Hardware Implementation Journey

This is the unique story Dr. Ajay Kumar tells — the gap between simulation and real hardware.

#### Step 1: MATLAB/Simulink Simulation
- Design the control algorithm (SRF, LMS, MPC, etc.)
- Simulate the complete PCS model: PV array model + MPPT + converter + LCL filter + grid
- Verify: MPPT efficiency, current THD, reactive power compensation, transient response
- **Ideal world** — no delays, no noise, perfect sensors

#### Step 2: Processor-in-Loop (PIL)
- Replace the MATLAB controller block with actual compiled code running on a DSP/microcontroller
- The DSP receives simulated sensor values, computes control output, sends back to MATLAB
- Catches: integer overflow, fixed-point precision errors, compiler-specific issues
- **Still no real hardware** — but real code

#### Step 3: Hardware-in-Loop (HIL) using OPAL-RT
- The power circuit (PV array + converter + grid) runs in OPAL-RT real-time simulator
- The control code runs on **real DSP/microcontroller hardware**
- Analog signals between OPAL-RT and DSP: real voltages and currents (scaled)
- Catches: ADC noise, PWM dead-time effects, digital communication delays, interrupt timing
- **This is where most real-world issues appear** — and Dr. Ajay Kumar's expertise shines

#### Step 4: Full Hardware Prototype
- Build the actual power electronics prototype:
  - IGBTs or MOSFETs (SiC for high efficiency) + gate drivers
  - Gate driver isolation, bootstrap circuits
  - Current sensors (Hall-effect), voltage sensors (differential amplifier)
  - DSP/STM32/TMS320F28xxx based controller board
  - LCL filter (wound inductors, film capacitors)
  - Protection circuits: overcurrent, overvoltage, under-frequency, anti-islanding
- Connect to real PV panels or PV simulator
- **This is the final proof** — hardware working in the lab

---

### 3. SRF-Based Control — Dr. Ajay Kumar's Hardware-Validated Approach

The power electronics interface of grid-connected Solar Photovoltaic (SPV) system requires a robust and computationally efficient control framework for synchronization with active/reactive power support and power quality enhancement under weak grid conditions. The Synchronous Reference Frame (SRF) based control framework is developed in conjunction with reliable Perturb & Observe (P&O) based MPPT to drive power converters. The proposed SRF structure is developed using simple mathematical operators, which reduces the mathematical burden from the digital controller and requires smaller memory space.

**Why SRF for hardware?**
- Standard PI controllers in d-q frame are simple and computationally light
- Runs on a TMS320F28xxx DSP at 10–20 kHz control loop without overloading the CPU
- Well-understood — easy to tune and debug on hardware
- **Dr. Ajay Kumar's contribution**: Optimized SRF formulation with reduced computation → fits into low-cost microcontrollers

**SRF Control Loop:**
```
Measured Iabc (3-phase currents from Hall-effect sensors)
         ↓
  Park Transform → Id, Iq (using PLL angle θ)
         ↓
  Id_ref = MPPT output (active current reference)
  Iq_ref = 0 (unity PF) or reactive current demand
         ↓
  PI controllers: Id_error → Vd_ref, Iq_error → Vq_ref
         ↓
  Inverse Park → Vabc_ref
         ↓
  SPWM → Gate signals to inverter
```

---

### 4. VSS-LMS Filter — His Best Paper Award Work

**LMS (Least Mean Squares)** is an adaptive filter algorithm — it learns the signal it needs to extract.

**Application to PV power quality:**
- At the PCC, the grid current contains: fundamental (50 Hz, wanted) + harmonics (unwanted)
- LMS filter extracts the fundamental component from a distorted signal
- The difference between measured current and LMS-estimated fundamental = harmonic content
- This harmonic content is fed back into the controller to cancel it

**Variable Step-Size LMS (VSS-LMS) — Dr. Ajay Kumar's Innovation:**
- Standard LMS has fixed step size μ → slow convergence if μ too small, unstable if μ too large
- VSS-LMS: **μ adapts dynamically** based on error magnitude
  - Large error → large μ → fast convergence
  - Small error → small μ → low steady-state noise
- **Result**: Faster harmonic extraction + lower steady-state distortion + more stable under grid transients

**Why this won Best Paper at PIICON 2024**: It directly solves a practical hardware problem — existing fixed-LMS implementations are sluggish under fast load changes in real grid conditions. VSS-LMS makes it viable for real deployment.

---

### 5. Transformerless PV Inverter — The Critical Safety Problem

Dr. Ajay Kumar's research proposes an optimized and robust current controller for the transformerless grid-integrated photovoltaic inverter, addressing the challenge of ensuring improved power quality while minimizing the DC component under non-ideal conditions.

**Why transformerless?**
- Traditional PV inverters use a 50 Hz transformer for isolation → heavy, bulky, ~2% efficiency loss
- **Transformerless inverters** eliminate this → lighter, smaller, cheaper, 2–3% more efficient
- Used in: most modern residential PV inverters (SMA, Huawei, Fronius)

**The leakage current problem — the key hardware challenge:**
- Without transformer isolation, there is a **common mode voltage** between PV array and grid
- This causes **leakage current** flowing through the stray capacitance between PV panels and ground (earth)
- Leakage current: dangerous (electrocution risk), causes EMI, trips RCD (residual current device), reduces efficiency
- **IEC 62109-2** standard: leakage current < 300 mA (absolute limit)

**Transformerless inverter topologies designed to minimize leakage:**
| Topology | Method | Leakage Level |
|---|---|---|
| **H4 (standard full bridge)** | No special provision | High — not suitable |
| **H5** | Extra switch disconnects PV during freewheeling | Low |
| **HERIC** | Bypass path maintains DC link isolation | Very low |
| **H6** | 6 switches — better control of common mode | Low |
| **Highly Efficient Reliable Inverter Concept (HERIC)** | Industry standard for European residential | Very low |
| **NPC (3-level)** | 3-level output → lower dV/dt → lower leakage | Very low |

**Dr. Ajay Kumar's hardware work**: Designing and testing transformerless topologies with control algorithms that actively minimize the DC offset and leakage current simultaneously — the dual challenge of efficiency + safety.

---

### 6. Multifunctional PV Inverter — Hardware Reality

Beyond just injecting solar power, Dr. Ajay Kumar's hardware prototype demonstrates simultaneous:

| Function | Hardware Requirement | Control Implementation |
|---|---|---|
| **MPPT** | PV voltage/current sensors + DC-DC converter | P&O algorithm on DSP |
| **Active power injection** | Grid current sensors + VSI | SRF d-axis PI controller |
| **Reactive power support** | Same hardware | SRF q-axis PI controller |
| **Harmonic cancellation** | Same hardware | VSS-LMS harmonic extraction + injection |
| **DC offset elimination** | DC sensor or observer | DC removal algorithm in current reference |
| **Anti-islanding** | Frequency/voltage monitoring | Active frequency drift (AFD) algorithm |
| **Grid synchronization** | Grid voltage sensors | SRF-PLL |

**The hardware challenge**: All these functions share the **same inverter current capacity**. When both harmonic cancellation and reactive power support are needed simultaneously — the inverter may not have enough headroom. Dr. Ajay Kumar's priority/capacity management is the practical engineering contribution.

---

### 7. Power Quality Standards for Grid-Connected SPV

| Standard | Country | Key Requirement |
|---|---|---|
| **IEEE 1547-2018** | USA (referenced globally) | THD < 5%, DC injection < 0.5%, anti-islanding |
| **CEA Technical Standards 2019** | **India — mandatory** | Power factor, LVRT, anti-islanding, harmonics |
| **IEC 61727** | International | General PV grid connection requirements |
| **IEC 62109-2** | International | Safety of PV inverters — leakage current < 300 mA |
| **IS 16169** | India | PV inverter performance standard |
| **IEC 61000-3-2** | International | Harmonic current limits for grid equipment |

**India-specific**: CEA 2019 mandates that all grid-connected PV systems > 1 MW must support reactive power injection and LVRT — making Dr. Ajay Kumar's multifunctional inverter research directly commercially relevant.

---

### 8. Hardware Components — What Goes Into a PCS Prototype

| Component | Specification (Typical 3 kW prototype) | Notes |
|---|---|---|
| **DC-DC Boost Converter** | MOSFET (SiC: 650V, 30A) + Inductor (500 μH) | SiC for 95%+ efficiency |
| **VSI (Inverter)** | IGBT/SiC module (600V, 30A) | 6-switch 3-phase or 4-switch 1-phase |
| **Gate Drivers** | HCPL-3120 or TLP250H (isolated) | 2500V isolation |
| **DSP Controller** | TI TMS320F28335 or STM32F4 | 150 MHz, 12-bit ADC, HRPWM |
| **Current Sensors** | LEM LA 25-P (Hall effect, ±25A) | Galvanic isolation |
| **Voltage Sensors** | Differential amplifier + voltage divider | Must handle 400V DC, 230V AC |
| **LCL Filter** | L1=3 mH, C=4.7 μF, L2=1.5 mH | Designed for 10 kHz switching frequency |
| **PV Simulator** | Chroma 62150H or similar | Programmable I-V curve, avoids roof testing |
| **OPAL-RT** | OP4510 (real-time simulator) | For HIL validation before full hardware |
| **Oscilloscope** | 4-channel, 200 MHz, current probe | Essential for waveform capture |

---

## Questions to Ask 
1.
   > *"Your VSS-LMS filter adapts its step size based on error magnitude — which makes it faster during transients and more accurate at steady state. In hardware, the error signal itself is corrupted by ADC quantization noise and switching-frequency ripple from the inverter. How do you prevent the VSS-LMS step size from responding to measurement noise rather than genuine harmonic content — and does this noise floor fundamentally limit your achievable THD?"*

2. > *"In your transformerless PV inverter work, DC offset injection into the grid is both a grid code violation and a transformer saturation risk for nearby distribution transformers. Since DSP-based controllers have ADC offset drift with temperature, how do you distinguish controller-induced DC offset from genuinely asymmetric grid conditions — and what is your hardware compensation strategy?"*

3. > *"Your SRF-based control was validated on OPAL-RT. When you moved from OPAL-RT to the full hardware prototype, what was the single most unexpected problem that the HIL simulation did not reveal — and what did it teach you about the gap between real-time simulation and actual power hardware?"*

4. > *"For a multifunctional PV inverter simultaneously handling active power injection, reactive power support, and harmonic compensation — the inverter's apparent power rating (VA) must be sized larger than its active power (W) rating. For a 5 kW PV inverter, what is the practical VA derating you've found necessary in hardware to deliver full solar power while still compensating third and fifth harmonics from a nonlinear local load?"*

5. > *"India's rooftop solar market is driven by small installers who need plug-and-play inverters — complex multifunctional inverters with LMS-based control sound great in a lab but require skilled commissioning. What is the path to making your hardware research 'productizable' — what is the minimum feature set, and what control auto-tuning or self-commissioning is needed for field deployment?"*

---

##  Key Terms Glossary

| Term | Meaning |
|---|---|
| PCS | Power Conditioning System — complete electronic interface between PV and grid |
| SPV | Solar PhotoVoltaic |
| SRF | Synchronous Reference Frame — d-q frame control for grid-connected converters |
| LMS | Least Mean Squares — adaptive filter algorithm for harmonic extraction |
| VSS-LMS | Variable Step-Size LMS — adapts convergence speed to error magnitude |
| MPPT | Maximum Power Point Tracking — P&O, INC algorithms |
| Transformerless Inverter | PV inverter without 50 Hz isolation transformer — lighter, more efficient |
| Leakage Current | Current through stray capacitance (PV-to-ground) — safety hazard |
| Common Mode Voltage | Voltage between PV array and grid ground — drives leakage current |
| H5 / HERIC | Transformerless inverter topologies with low leakage current |
| LCL Filter | 2-inductor + 1-capacitor harmonic filter at inverter output |
| THD | Total Harmonic Distortion — power quality measure (must be < 5% for grid) |
| PIL | Processor-in-Loop — real code tested against simulated power circuit |
| HIL | Hardware-in-Loop — real controller hardware tested against real-time simulator |
| OPAL-RT | Real-time digital power system simulator (OP4510 model) |
| TMS320F28xxx | Texas Instruments DSP — industry standard for power converter control |
| Hall-Effect Sensor | Non-contact current measurement — essential for isolated PCS hardware |
| PLL | Phase Locked Loop — extracts grid frequency and phase angle |
| Anti-islanding | Protection that disconnects PV when grid fails — safety critical |
| AFD | Active Frequency Drift — active anti-islanding detection method |
| CEA 2019 | Central Electricity Authority Technical Standards — India's grid code |
| SERB | Science and Engineering Research Board — India's research funding agency |
| PIICON | IEEE Power India International Conference |

---


## **My Profiles**

- LinkedIn: [Link](https://www.linkedin.com/in/un-animesh/)
- GitHub: [Link](https://github.com/unanimesh)
- Email: [Link](https://mailto:un.animesh@zohomail.com)
