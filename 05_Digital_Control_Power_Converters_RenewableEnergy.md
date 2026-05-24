#  Faculty Development Program 2026 - BIT Mesra
## Session 05:  Digital Control in Power Converters for Renewable Energy

---

## Speaker Details

| Field | Details |
|---|---|
| **Name** | Dr. Subhojit Ghosh |
| **Designation** | Professor, Department of Electrical Engineering |
| **Institution** | National Institute of Technology (NIT) Raipur |
| **Email** | sghosh.ee@nitrr.ac.in |
| **Google Scholar Citations** | 4,660+ |
| **Publications** | 155+ |
| **Research Projects** | 5 funded projects |
| **Award** | **NIT Raipur Best Faculty Award 2020** (Foundation Day, December 1, 2020) |

### Research Areas (Google Scholar)
- **Control Systems** — optimal, state feedback, fractional order, LQR/LQI
- **Cyber Physical Systems** — smart grid security, IoT-based attacks
- **Optimization** — differential evolution, PSO, hybrid methods

### Key Publications & Research Highlights

**A. Digital Control of Power Converters (Core Topic Today)**
1. **"Optimal State Feedback-Integral Control of Fuel-Cell Integrated Boost Converter"** — *IEEE Transactions on Circuits and Systems II: Express Briefs* (2022). State-feedback + integrator for fuel cell DC-DC boost converter — digital optimal control at its best.
2. **"Modified LQR Technique for Fuel-Cell-Integrated Boost Converter"** — *IEEE Transactions on Industrial Electronics* (2021). LQR-based digital control for PEM fuel cell power conditioning.
3. **"Fractional Order Modeling and Two Loop Control of PEM Fuel Cell"** — *International Journal of Hydrogen Energy* (2018). Fractional calculus-based digital controller for voltage regulation in fuel cells.
4. **"Operational Adaptability of PEM Fuel Cell for Optimal Voltage Regulation with Maximum Power Extraction"** — *IEEE Transactions on Energy Conversion* (2020). Optimal digital control for PEM fuel cell.
5. **"Real-Time Implementation of Fractional-Order PID Controller for Magnetic Levitation Plant with Time Delay"** — *IEEE Transactions on Instrumentation and Measurement* (2022).

**B. Multiple Input Converters for PV Systems**
6. **"Stand-Alone Multiple Input Photovoltaic Inverter for Maximum Power Extraction and Voltage Regulation under Mismatched Atmospheric Conditions"** — *IET Renewable Power Generation* (2020). Multi-source PV digital control.
7. **"Comparative Analysis on Selection and Synthesis of Multiple Input Converters"** — *IET Power Electronics* (2019).

**C. Battery & Energy Storage Control**
8. **"Robust Observer Design for SOC Estimation of LiFePO₄ Batteries using Fractional Calculus"** — *IEEE Transactions on Vehicular Technology* (2021). Advanced digital observer for battery state estimation.
9. **"Analytical Formulation for Power, Energy and Efficiency Measurement of Ultracapacitor Using Fractional Calculus"** — *IEEE Transactions on Instrumentation and Measurement* (2019).

**D. Microgrid Protection & CPS Security**
10. **"Design of a Coordinated Cyber-Physical Attack in IoT-Based Smart Grid"** — *International Journal of Critical Infrastructure Protection, Elsevier* (2021). Research on attack design — to understand and then defend against CPS threats.
11. **"Communication-less Ensemble Classifier-Based Protection for DC Microgrid"** — *Sustainable Energy, Grids and Networks* (2021).

### BIT Mesra Connection
- **Dr. Gauri Shanker Gupta (BIT Mesra)** and **Dr. Suraj (BIT Mesra)** are listed as collaborators on Dr. Ghosh's IRINS profile — a direct research bridge to your own institution!

---

##  Topic Deep Dive: Digital Control in Power Converters for Renewable Energy

---

### 1. Why Digital Control? — The Evolution

**The Old Way — Analog Control:**
- Simple RC-based compensators, analog PID circuits
- Hardwired — changing the controller meant changing hardware
- Sensitive to component aging, temperature drift
- Cannot implement complex algorithms (MPC, LQR, fractional PID)

**The New Way — Digital Control:**

> *"By replacing analog circuits with high-speed digital signal processors (DSPs), microcontrollers (MCUs), and field-programmable gate arrays (FPGAs), engineers can now implement sophisticated control algorithms that were previously impossible to realize in hardware."*

| Feature | Analog Control | Digital Control |
|---|---|---|
| Flexibility | Fixed in hardware | Reprogrammable in software |
| Complexity | Simple (PID max) | LQR, MPC, Fuzzy, Fractional PID, RL |
| Noise immunity | Poor | Excellent (digital signals) |
| Auto-tuning | Not possible | AI/optimization-based auto-tuning |
| Cost (high volume) | Lower | Decreasing rapidly |
| Communication | Not possible | UART, CAN, USB, Ethernet built in |
| Diagnostics | None | Full internal state logging |

---

### 2. The Digital Control Hardware Platform

Three main hardware platforms are used in power converter digital control:

#### A. DSP — Digital Signal Processor
- Specialized processor optimized for real-time signal processing
- Example: **TI TMS320F28xxx series** — industry standard for power converters
- Built-in: ADC, PWM generator (HRPWM — nanosecond resolution), CAN, SPI, I²C
- Runs control loop at 10 kHz–100 kHz sampling rates
- Used in: solar inverters, motor drives, EV chargers, fuel cell converters (Dr. Ghosh's research)

#### B. FPGA — Field Programmable Gate Array
- Hardware-level parallelism — multiple control loops run simultaneously
- Ultra-fast execution — can do 10–50 ns control loops
- Used for: high-frequency converters (GaN/SiC), multilevel inverters, hardware-in-loop (HIL) simulation
- DSP-FPGA co-processing: DSP handles high-level control, FPGA handles fast PWM generation and protection

#### C. Microcontroller (MCU)
- Cost-effective — used in smaller, less demanding converters
- ARM Cortex-M based (STM32, TI C2000, Arduino)
- Sufficient for: solar MPPT, battery chargers, small inverters

**Modern Trend — SoC (System on Chip):**
- Single chip with ARM CPU + FPGA fabric (e.g., Xilinx Zynq)
- Combines flexibility of FPGA with software ease of CPU

---

### 3. Digital Control Loop for Power Converters

**The sampling and control cycle — this is where digital control introduces unique challenges:**

```
Physical Plant (Converter)
      ↓ (Voltage/Current sensors)
    ADC Sampling  ←  Sampling Delay
      ↓
  Digital Computation (DSP/FPGA)  ←  Computational Delay
  [Control Algorithm Executes]
      ↓
    PWM Update  ←  PWM Update Delay
      ↓
    Power Switches (MOSFET/IGBT/GaN)
      ↓
Physical Plant (back to top)
```

**Key Challenges in Digital Implementation:**
- **Sampling delay**: ADC takes finite time → introduces phase lag → reduces stability margin
- **Computational delay**: The DSP/FPGA needs time to run the algorithm
- **PWM quantization**: Finite resolution of digital PWM counter → small steady-state error
- **Coefficient quantization**: Controller gains stored in finite-precision binary → rounding errors
- **Aliasing**: If sampling frequency too low → high-frequency noise folds into signal

**Rule of thumb**: Sampling frequency should be ≥ 10× switching frequency for adequate control bandwidth

---

### 4. Key Digital Control Algorithms (Dr. Ghosh's Specialization)

#### A. State Feedback Control (LQR / LQI)
The cornerstone of Dr. Ghosh's converter research.

- The converter is modeled as a **state-space system**: `ẋ = Ax + Bu`, `y = Cx`
- **LQR (Linear Quadratic Regulator)**: Find gain matrix K that minimizes: `J = ∫(xᵀQx + uᵀRu)dt`
  - Q penalizes state deviation (e.g., voltage error)
  - R penalizes control effort (e.g., duty cycle changes)
  - Trade-off between fast response and control effort
- **LQI (adds Integral state)**: Eliminates steady-state error under disturbances — critical for converters feeding fuel cells or PV arrays that have slowly varying source voltage

**Dr. Ghosh's Application:**
- Applied LQR and LQI to **PEM Fuel Cell + Boost Converter** system
- Fuel cell has complex nonlinear electrochemical dynamics
- LQI ensures tight voltage regulation despite load changes and fuel cell current variations
- Published in *IEEE Trans. Circuits Syst. II* and *IEEE Trans. Ind. Electron.*

#### B. Fractional Order Control (Dr. Ghosh's Signature Work)
A highly advanced and relatively novel area:

- Classical PID uses integer-order derivatives (d¹/dt¹) and integrals
- **Fractional PID** uses non-integer orders: PIᵅDᵝ where α, β ∈ ℝ
- Benefits: extra tuning freedom, better noise rejection, more robust to plant uncertainty
- **Fractional order modeling**: Describes electrochemical systems (fuel cells, batteries, ultracapacitors) more accurately than integer-order models because they inherently have memory effects

**Dr. Ghosh's Applications:**
- Fractional order control of **PEM fuel cell** converters — published in *Int. J. Hydrogen Energy*
- Fractional calculus for **SOC estimation** of LiFePO₄ batteries — published in *IEEE Trans. Veh. Technol.*
- Fractional calculus for **ultracapacitor** energy/power measurement — published in *IEEE Trans. Instrum. Meas.*

#### C. Model Predictive Control (MPC) for Converters
- Predicts converter behavior over a finite horizon
- At each sampling instant, solves an optimization problem to find the optimal switching state
- **Finite Control Set MPC (FCS-MPC)**: Evaluates all possible switching states of the converter, picks the one minimizing a cost function
- Very fast dynamic response — gaining rapid adoption for solar inverters and motor drives

#### D. Digital MPPT (Maximum Power Point Tracking)
Specific to PV and fuel cells:
- **Perturb & Observe (P&O)**: Simplest — perturbs duty cycle, observes power, follows gradient
- **Incremental Conductance**: Tracks dP/dV = 0 condition
- **Fractional Open Circuit Voltage**: Fast but approximate
- **AI-based MPPT**: ANN, fuzzy logic, PSO-based — handles partial shading and dynamic irradiance changes
- **Dr. Ghosh's contribution**: Non-iterative resistance estimation approach for PEM fuel cell maximum power extraction

#### E. Digital PWM Modulation Techniques
- **SPWM (Sinusoidal PWM)**: Standard, simple, well-understood
- **SV-PWM (Space Vector PWM)**: Better DC bus utilization, lower THD — implemented digitally in DSP
- **Selective Harmonic Elimination (SHE)**: Pre-calculated switching angles stored in DSP lookup tables to eliminate specific harmonics
- **High-Resolution PWM (HRPWM)**: TI DSP feature — achieves sub-nanosecond resolution by using edge delay — critical for precise voltage regulation

---

### 5. Power Converters in Renewable Energy — Where Digital Control Is Applied

#### Solar PV Converters
```
PV Array → [DC-DC Boost] → [DC link] → [Single/3-phase Inverter] → Grid
                ↑                              ↑
          MPPT Controller              Grid-tied current control
          (Digital DSP)               (d-q current control, PLL)
```
- **DC-DC stage**: LQI/fractional PID/MPC controls duty cycle for MPPT + voltage regulation
- **Inverter stage**: DSP runs d-q frame current controller + Phase Locked Loop (PLL) for grid synchronization

#### PEM Fuel Cell Converters (Dr. Ghosh's main focus)
```
PEM Fuel Cell → [Boost Converter] → DC Bus / Grid
                      ↑
              LQR/LQI State Feedback
              Fractional Order PID
              (Optimal Voltage + Max Power)
```
- Fuel cell has complex I-V characteristics — digital state feedback adapts in real time
- Goal: regulate DC output voltage tightly while extracting maximum power

#### Battery Energy Storage (BESS)
- **DC-DC bidirectional converter** between battery and DC bus
- Digital controller manages: charging mode (CC/CV), discharging mode, SOC estimation
- **Fractional calculus observer** for robust SOC estimation (Dr. Ghosh's work)

#### Multiple Input Converters (Dr. Ghosh's Specialty)
- Single converter that accepts **multiple renewable sources** (PV + wind + battery + fuel cell)
- Reduces component count vs separate converter per source
- Digital controller manages power flow priority between all sources simultaneously

#### Wind Energy — DFIG Digital Control
- Digital vector control of rotor-side converter and grid-side converter
- DSP runs: rotor current control, grid synchronization, reactive power management

---

### 6. GaN / SiC — The New Hardware Driving Digital Control Demand

- Wide-bandgap semiconductors (GaN, SiC) switch at **1–5 MHz** vs IGBT's 20 kHz
- Higher switching frequency → smaller inductors/capacitors → compact converters
- But: digital controller must now run at **>5 MHz** sampling — demands FPGA-level speed
- GaN-based multi-converter systems for PV + battery + grid: Dr. Ghosh's recent research area

---

### 7. India Context

- India's solar capacity crossed **90 GW** (2024) and is targeting **500 GW renewables by 2030**
- Every solar panel, fuel cell, and battery connects to the grid through a **digitally controlled power converter**
- India's domestic power electronics industry is growing — NIT and IIT research directly feeds into Make-in-India converter design
- Low-cost DSP/MCU (TI C2000 series starting ₹500) makes digital control accessible for rural solar pumps and microgrids

---

## Top Questions to Ask 


1.
   > *"In your LQI control of fuel-cell-integrated boost converters, how do you handle the strongly nonlinear and time-varying impedance of the PEM fuel cell — do you linearize around a single operating point or use gain scheduling, and how robust is the LQI to membrane degradation over time?"*

2. > *"Fractional-order controllers for power converters show superior robustness, but implementing fractional derivatives digitally requires approximations like Oustaloup or Grünwald-Letnikov. At what switching frequencies does the approximation error become significant enough to compromise controller performance?"*

3. > *"For multiple-input PV converters under partially shaded conditions, global MPPT is an NP-hard optimization problem. Have you explored any AI/metaheuristic approaches — like differential evolution or PSO — integrated directly into the DSP real-time control loop for global MPPT?"*

4. > *"You've published on cyber-physical attacks on IoT-based smart grids. For digitally controlled converters in grid-connected solar plants — what are the specific attack surfaces that a malicious actor could exploit in the PWM reference chain, and how should the digital controller be hardened?"*

5. > *"With GaN converters switching at 1–5 MHz, the computational window for the digital controller shrinks to under 200 ns. What control architectures — FPGA, SoC, or custom ASIC — do you see as the practical path forward for real-time digital control at these switching speeds?"*

---

##  Key Terms Glossary

| Term | Meaning |
|---|---|
| DSP | Digital Signal Processor — real-time controller for power converters |
| FPGA | Field Programmable Gate Array — ultra-fast reconfigurable hardware |
| HRPWM | High Resolution PWM — sub-nanosecond switching control (TI DSP feature) |
| ADC | Analog-to-Digital Converter — samples physical signals for DSP processing |
| LQR | Linear Quadratic Regulator — optimal state feedback controller |
| LQI | Linear Quadratic Regulator with Integrator — eliminates steady-state error |
| Fractional PID | PIᵅDᵝ — non-integer order controller for improved robustness |
| MPC | Model Predictive Control — optimization-based digital control |
| FCS-MPC | Finite Control Set MPC — evaluates all switch states at each instant |
| MPPT | Maximum Power Point Tracking — extracts maximum power from PV/fuel cell |
| P&O | Perturb & Observe — simplest MPPT algorithm |
| SV-PWM | Space Vector PWM — optimal 3-phase switching pattern |
| SHE | Selective Harmonic Elimination — pre-calculated angles to remove harmonics |
| d-q Control | Synchronous reference frame — decouples P and Q in 3-phase systems |
| PLL | Phase Locked Loop — digital synchronization to grid voltage |
| SOC | State of Charge — battery energy level |
| PEM | Proton Exchange Membrane — type of fuel cell / electrolyzer |
| GaN / SiC | Gallium Nitride / Silicon Carbide — wide-bandgap fast-switching semiconductors |
| Multiple Input Converter | Single converter accepting several sources (PV + wind + battery) |
| BESS | Battery Energy Storage System |

---


## **My Profiles**

- LinkedIn: [Link](https://www.linkedin.com/in/un-animesh/)
- GitHub: [Link](https://github.com/unanimesh)
- Email: [Link](https://mailto:un.animesh@zohomail.com)

