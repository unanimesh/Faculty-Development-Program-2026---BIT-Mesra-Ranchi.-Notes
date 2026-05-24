#  Faculty Development Program 2026 - BIT Mesra
## Session 06: PEM Fuel Cell Stability via Port-Hamiltonian Control

---

##  Speaker Details

| Field | Details |
|---|---|
| **Name** | Dr. Lalitesh Kumar |
| **Current Position** | Visiting Researcher / Ph.D. Candidate |
| **Institution** | Southern University of Science and Technology (SUSTech), Shenzhen, China |
| **Department** | Automation and Intelligent Manufacturing |
| **Also Affiliated With** | College of Control Science and Engineering, Zhejiang University, Hangzhou, China |
| **Supervisor** | Prof. Jian Chen (Zhejiang University) |
| **Co-collaborator** | Prof. Arjan van der Schaft (University of Groningen, Netherlands) — the **founder of port-Hamiltonian theory** |

### Academic Background — A Direct BIT Mesra Connection!
| Degree | Year | Institution |
|---|---|---|
| B.S. (Electrical Engineering) | 2008 | Muzaffarpur Institute of Technology, Bihar |
| **M.E. (Electrical Engineering)** | **2012** | **Birla Institute of Technology (BIT) Mesra, Ranchi** ← Your institution! |
| Ph.D. (Ongoing) | Current | Zhejiang University / SUSTech, China |

> **Dr. Lalitesh Kumar is a BIT Mesra alumnus — he did his M.E. from your own department!**

### Research Areas
- PEM Fuel Cell Modeling and Control
- Port-Hamiltonian Systems
- Passivity-Based Control (IDA-PBC)
- Nonlinear and Optimal Control
- Fractional Order Control Systems

### Key Publications

1. **"A Segmented Model Based Fuel Delivery Control of PEM Fuel Cells: A Port-Hamiltonian Approach"**
   — *Automatica*, Vol. 168, 2024 (Elsevier) — **Top-tier journal** in control theory
   — Co-authors: Jian Chen, Chengshuai Wu, Yuzhu Chen, **Arjan van der Schaft**
   — Uses IDA-PBC to control the hydrogen delivery subsystem of PEMFC stacks

2. **"Air Supply Control of a Non-Affine PEM Fuel Cell System Under a Port-Hamiltonian Framework"**
   — Journal publication
   — Controls oxygen (air) supply to the cathode via port-Hamiltonian formulation

3. **"Air Supply Control for PEM Fuel Cells Under Hamiltonian Framework: A Segmentation Approach"**
   — Conference Paper, May 2024

4. **"Purge Strategy for PEM Fuel Cells Considering Economy and Durability"**
   — Conference Paper, October 2023
   — Co-authored with Prof. Jian Chen and Harsh Mohan Sharma

5. **"Tracking Control Design for Fractional Order Systems: A Passivity-Based Port-Hamiltonian Framework"**
   — March 2023
   — Combines fractional calculus + port-Hamiltonian control — a niche frontier topic

6. **"Multiobjective Based LQR Design for Fractional Order Systems with Perturbations using PESA-II Algorithm"**
   — (2020) — connects to Dr. Subhojit Ghosh (Session 5) via shared interest in fractional control

7. **"Design of PI Controller: A Multiobjective Optimization Approach"**
   — ICACCI 2014 — co-authored with **Dr. Subhojit Ghosh (NIT Raipur)** ← Session 5 speaker!

---

##  Topic Deep Dive: PEM Fuel Cell Stability via Port-Hamiltonian Control

This is one of the **most mathematically advanced** topics in the FDP — combining electrochemical engineering, nonlinear control theory, and physics-based modeling. Let's break it down step by step.

---

### 1. PEM Fuel Cell — Quick Recap

A Proton Exchange Membrane Fuel Cell (PEMFC) converts hydrogen and oxygen into electricity:

```
Anode:   H₂ → 2H⁺ + 2e⁻
Cathode: ½O₂ + 2H⁺ + 2e⁻ → H₂O
Overall: H₂ + ½O₂ → H₂O + Electricity + Heat
```

**Key Subsystems of a PEM Fuel Cell System:**

| Subsystem | Function | Control Challenge |
|---|---|---|
| **Fuel Delivery (Anode)** | Supplies H₂ at correct pressure | Maintain anode pressure uniformly along stack |
| **Air Supply (Cathode)** | Supplies O₂ via compressor | Balance O₂ stoichiometry vs compressor power |
| **Water Management** | Keeps membrane humidified, prevents flooding | Flooding degrades performance; drying causes damage |
| **Thermal Management** | Keeps stack at ~60–80°C | Overheating degrades membrane |
| **Power Conditioning** | DC-DC boost converter output | Wide voltage variation with load current |

**Why Stability Is a Challenge:**
- PEMFC has nonlinear, time-varying electrochemical dynamics
- The I-V (polarization) curve is nonlinear — three regions (activation, ohmic, concentration)
- The **anode and cathode pressures** must be balanced — differential pressure damages the membrane
- When connected to a **Constant Power Load (CPL)** — like a motor drive or inverter — the load exhibits **negative incremental impedance**, which can cause oscillation and instability
- Traditional PID controllers cannot provide **provable stability guarantees** for these nonlinear dynamics

---

### 2. What Is Port-Hamiltonian Theory? — The Foundation

Developed by **Prof. Arjan van der Schaft** (University of Groningen) and colleagues, Port-Hamiltonian (pH) systems theory is a framework for modeling and controlling physical systems using **energy** as the fundamental concept.

#### The Core Idea
Every physical system stores, dissipates, and exchanges energy. A port-Hamiltonian model explicitly represents these three things:
- **H(x)** — the Hamiltonian function = total stored energy of the system (electrical + mechanical + chemical)
- **J(x)** — Interconnection matrix (skew-symmetric) — how energy flows between subsystems (conservative, no dissipation)
- **R(x)** — Damping/dissipation matrix (positive semi-definite) — how energy is dissipated
- **g(x)** — Input/output (port) matrix — how external energy enters and exits

**The Port-Hamiltonian System equation:**
```
ẋ = [J(x) - R(x)] ∇H(x) + g(x)u
y  = g(x)ᵀ ∇H(x)
```

Where:
- `x` = state vector (e.g., inductor currents, capacitor voltages, fuel cell pressures)
- `u` = input (e.g., duty cycle of converter, compressor speed)
- `y` = output (e.g., voltage, current)
- `∇H(x)` = gradient of Hamiltonian = "generalized forces"

#### Why Is This Powerful?
- **Physical insight**: The model directly reflects energy storage (inductors, capacitors, gas chambers) and dissipation (resistors, friction)
- **Stability by Lyapunov**: The Hamiltonian H(x) serves naturally as a **Lyapunov function** — if H decreases, the system is stable. No need to guess a Lyapunov function (the hardest step in nonlinear control)
- **Modularity**: Subsystems can be interconnected by composing their pH models while preserving the pH structure
- **Passivity guaranteed**: pH systems are inherently passive — they cannot generate energy

---

### 3. Passivity-Based Control (PBC) and IDA-PBC

**Passivity** means a system cannot produce more energy than it stores. A passive system is inherently safe and stable.

**Passivity-Based Control (PBC)**: Design feedback control such that the closed-loop system behaves like a desired passive (energy-dissipating) system.

**IDA-PBC — Interconnection and Damping Assignment PBC:**
The most powerful variant, developed by Ortega, van der Schaft, Maschke, Escobar (2002).

**Key steps of IDA-PBC design:**
1. Model the system in port-Hamiltonian form
2. Choose a **desired Hamiltonian** Hd(x) — a new energy function with minimum at the desired equilibrium
3. Choose desired **Jd** and **Rd** — modify how energy flows and dissipates
4. Solve the **matching equations** — find the control law u that transforms the original pH system into the desired one
5. The resulting closed-loop is a pH system with Hd as Lyapunov function → **global stability guaranteed**

> **Intuition**: IDA-PBC reshapes the system's energy landscape so that the desired operating point is the natural energy minimum — like tilting a bowl so a marble naturally rolls to the desired position.

---

### 4. Dr. Lalitesh Kumar's Specific Work — PEM Fuel Cell via pH Control

#### Paper 1: Hydrogen Delivery Control (Anode) — *Automatica* 2024
**Problem**: The fuel delivery subsystem (FDS) of a PEMFC is governed by **Partial Differential Equations (PDEs)** — the hydrogen gas pressure varies spatially along the anode channel.

**Challenge**: PDEs are infinite-dimensional — classical control cannot directly handle them.

**Dr. Kumar's Approach:**
1. **Segmentation**: The anode channel is divided into N segments — each described by lumped ODEs (approximation of PDEs)
2. Each segment has its own pressure state → creates a **multi-input multi-output (MIMO)** port-Hamiltonian model based on mass balance
3. **IDA-PBC** is designed for this segmented model to regulate pressure uniformly across all segments
4. Result: Provably stable hydrogen delivery that keeps anode pressure uniform — preventing membrane damage

**Key co-author: Prof. Arjan van der Schaft** — the founder of pH theory — lending extraordinary mathematical credibility to this work.

#### Paper 2: Air Supply Control (Cathode) — Non-Affine System
**Problem**: The cathode air supply system (compressor → manifold → stack) is a **non-affine** nonlinear system — the control input (compressor voltage) appears nonlinearly, making standard IDA-PBC inapplicable.

**Dr. Kumar's Approach:**
- Models the non-affine cathode subsystem in a **generalized port-Hamiltonian framework**
- Formulates the air supply control to balance: O₂ stoichiometry (for performance) vs. compressor parasitic power consumption (for efficiency)
- Derives a passivity-based controller despite the non-affine structure

#### Fractional Order + Port-Hamiltonian (2023)
- Extends port-Hamiltonian control to **fractional-order systems** — a rare frontier combination
- Addresses chaotic dynamics in fractional systems using passivity-based stabilization
- Application: Fuel cells and batteries exhibit fractional-order electrochemical dynamics — this work directly enables more accurate control of their real behavior

---

### 5. The Constant Power Load (CPL) Instability Problem

This is central to why pH control is needed for fuel cells in vehicle/microgrid applications.

**The Problem:**
- A fuel cell powers a motor drive inverter
- The inverter maintains constant power to the motor: P = V × I = constant
- As voltage drops (e.g., during load transient): V↓ → I must increase to maintain P → looks like **negative resistance** (dV/dI < 0)
- This negative impedance destabilizes the DC bus → oscillations, voltage collapse

**Port-Hamiltonian Solution:**
- The port-controlled Hamiltonian approach proposes simple solutions to the dynamic performance and convergence problems when interaction occurs between power sources and constant power loads — the cascade architecture of power converters in DC microgrids may lead to large oscillation and even risks of instability given that load converters feature CPL characteristics.
- IDA-PBC reshapes the closed-loop energy function to make the operating point globally stable despite CPL
- Adds **virtual damping** via the control law to counteract the negative impedance

---

### 6. Why pH Control Beats Classical Methods for PEMFC

| Control Method | Stability Guarantee | Handles Nonlinearity | Model Required | Robustness |
|---|---|---|---|---|
| **PID** | Local (linearized) | No | Minimal | Low |
| **LQR/LQI** (Session 5) | Global (linear) | No (linearized) | State-space linear | Medium |
| **Sliding Mode** | Local/regional | Yes | Nonlinear | High |
| **MPC** | Depends on horizon | Partially | Nonlinear model | Medium |
| **IDA-PBC (pH)** | **Global (Lyapunov)** | **Yes** | **pH model** | **Very High** |
| **Fractional-order PBC** | Global | Yes | Fractional pH | Highest |

**pH control advantages:**
- Stability guaranteed globally, not just near operating point
- Works with the system's **physical energy structure** — no cancellation of nonlinearities (which is fragile)
- Modular — interconnect subsystem controllers while maintaining stability of the whole
- Naturally handles parameter uncertainty — robustness comes from passivity property

---

### 7. Connection to the FDP's Broader Themes

| This Session | Connected To |
|---|---|
| PEM Fuel Cell | Session 2 (Green Hydrogen — Dr. Sarode), Session 5 (Digital Control — Dr. Ghosh) |
| pH/IDA-PBC for boost converter | Session 3 (Z-Source inverter — Dr. Kadwane), Session 5 (LQR for fuel cell — Dr. Ghosh) |
| Fractional Order Control | Session 5 (Dr. Ghosh — fractional PID for PEM fuel cells) |
| Lyapunov stability | Session 4 (Dr. Chatterjee — small signal stability, LQI) |

---

## Questions to Ask 



1. 
   > *"In your Automatica 2024 paper, you segment the PDE model of the anode fuel delivery subsystem into N lumped-ODE segments for IDA-PBC design. How does the number of segments N affect the trade-off between modeling accuracy and controller complexity — and is there a systematic method to choose the optimal N for a given stack geometry?"*

2. > *"The non-affine cathode air supply system cannot be handled by standard IDA-PBC. You formulated it in a generalized port-Hamiltonian framework — what is the key structural insight that made the matching equations solvable for a non-affine system, and does this technique generalize beyond fuel cells?"*

3. > *"You co-authored a fractional-order passivity-based port-Hamiltonian paper (2023). Fuel cell electrochemical impedance spectroscopy (EIS) shows fractional-order behavior. Do you believe fractional-order pH models will eventually replace integer-order models as the standard for PEMFC control design?"*

4. > *"Prof. Arjan van der Schaft — the founder of port-Hamiltonian theory — is your co-author on the Automatica paper. From your experience working with him: what are the open mathematical problems in port-Hamiltonian control of distributed-parameter energy systems that you see as the most promising research directions for the next five years?"*

5. > *"As a BIT Mesra M.E. alumnus — what advice would you give to the faculty and students here who want to enter the field of energy-based nonlinear control and port-Hamiltonian methods? What mathematical prerequisites are most important, and what are the best entry-point research problems?"*

---

## 📚 Key Terms Glossary

| Term | Meaning |
|---|---|
| PEM / PEMFC | Proton Exchange Membrane Fuel Cell |
| Port-Hamiltonian (pH) | Energy-based framework for modeling physical systems |
| Hamiltonian H(x) | Total stored energy of the system — used as Lyapunov function |
| Passivity | System property: cannot generate more energy than stored (inherently safe) |
| PBC | Passivity-Based Control — ensures closed-loop passivity |
| IDA-PBC | Interconnection and Damping Assignment PBC — shapes energy and damping to achieve desired equilibrium |
| J(x) | Interconnection matrix (skew-symmetric) — energy flow, no dissipation |
| R(x) | Damping matrix (positive semi-definite) — energy dissipation |
| Matching Equations | PDEs that must be solved to find IDA-PBC control law |
| Lyapunov Function | A "virtual energy" function — if it decreases, system is stable |
| CPL | Constant Power Load — load with negative incremental impedance; destabilizes DC bus |
| FDS | Fuel Delivery Subsystem — hydrogen supply to anode |
| Non-Affine System | System where control input appears nonlinearly (not just multiplied by state) |
| Segmentation | Approximating PDE (infinite-dimensional) model with multiple coupled ODEs |
| MIMO | Multi-Input Multi-Output system |
| EIS | Electrochemical Impedance Spectroscopy — characterizes fuel cell dynamics |
| Fractional-Order pH | Port-Hamiltonian framework extended to non-integer order dynamics |
| Lyapunov-Energy function | Combination of Lyapunov stability theory with physical energy concept |
| Adaptive Hamiltonian PI | Extended pH controller with integral action for robustness to parameter variation |

---

## **My Profiles**

- LinkedIn: [Link](https://www.linkedin.com/in/un-animesh/)
- GitHub: [Link](https://github.com/unanimesh)
- Email: [Link](https://mailto:un.animesh@zohomail.com)
