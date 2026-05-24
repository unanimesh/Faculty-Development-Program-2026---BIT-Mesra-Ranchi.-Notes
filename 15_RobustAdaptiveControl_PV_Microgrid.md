#  Faculty Development Program 2026 - BIT Mesra
## Session 15: Robust and Adaptive Control for PV and Microgrid Systems

---

##  Speaker Details

| Field | Details |
|---|---|
| **Name** | Prof. Bidyadhar Subudhi |
| **Designation** | Professor, School of Electrical Sciences + **Dean (Research & Development)** |
| **Institution** | Indian Institute of Technology (IIT) Goa |
| **Email** | bidyadhar@iitgoa.ac.in |
| **Additional Role** | **Director (on lien), NIT Warangal** |
| **Ph.D. Students Supervised** | **34 completed** |
| **Journal Publications** | **130+ in reputed international journals** |
| **Conference Papers** | 70+ |
| **Books Edited** | 3 books, 13 book chapters |

### Academic Background — Extraordinary Pedigree

| Degree | Institution | Year |
|---|---|---|
| B.E. (Electrical Engineering) | **NIT Rourkela** (then REC Rourkela) | 1988 |
| M.Tech. (Control & Instrumentation) | **IIT Delhi** | 1994 |
| **Ph.D. (Control Systems Engineering)** | **University of Sheffield, United Kingdom** | **2002** |
| Post-Doctoral Fellow | **National University of Singapore (NUS)** | May–Nov 2005 |

> **NIT Rourkela → IIT Delhi → University of Sheffield (UK) → NUS Singapore → IIT Goa** — one of the most prestigious academic trajectories in Indian electrical engineering.

### Fellowships and Memberships 

- **Fellow, Indian National Academy of Engineering (INAE)** — India's highest engineering fellowship
- **Fellow, IET (UK)** — Institution of Engineering and Technology, United Kingdom
- **Senior Member, IEEE (USA)**
- **Associate Editor, IEEE Transactions on Sustainable Energy** — the most prestigious journal in sustainable energy

### Previous Position
- **Professor and Head, Department of Electrical Engineering, NIT Rourkela** — where Prof. K.B. Mohanty (Session 14) is also a professor! They are colleagues from the same department.

### Research Areas 

1. **System & Control Theory**
2. **Robust and Adaptive Control** — his primary theoretical contribution
3. **Control of Photovoltaic Systems** — Lyapunov-based, adaptive, sliding mode MPPT and voltage control
4. **Microgrid Control** — distributed, fixed-time, secondary voltage/frequency restoration
5. **Active Power Filtering**
6. **Wide Area Control of Power Systems**
7. **Control of Autonomous Underwater Vehicles (AUVs)** — a unique interdisciplinary area
8. **Machine Learning and Adaptive Systems**
9. **Marine Robotics**

### Key  Publications

| Paper | Journal | Contribution |
|---|---|---|
| **"A Lyapunov-based Adaptive Voltage Controller for a Grid Connected PV System"** | *IET Smart Grid* (2021) | Lyapunov stability theory → provably stable adaptive PV voltage control |
| **"Self-tuned Adaptation Rate Lyapunov based Voltage Controller for a Grid Connected PV System"** | IEEE IARIA 2021 | Automatic adaptation rate tuning — no manual gain setting |
| **"Distributed Extended-State-Observer Based Backstepping Control of a PV Integrated AC Microgrid"** | IEEE IARIA 2021 | Backstepping control for PV-microgrid with disturbance observer |
| **"An Optimized Double-Integral Sliding Mode Controller for a PV Microgrid"** | *COMPEL*, Emerald (2021) | DISMC for PV microgrid — enhanced disturbance rejection |
| **"Distributed, Fixed-Time and Bounded Control for Secondary Voltage and Frequency Restoration in Islanded Microgrids"** | *IET Smart Grid* | Fixed-time convergence — restores frequency and voltage in guaranteed finite time |
| **"Design and Real-time Implementation of a New Auto-tuned Adaptive MPPT Control for a PV System"** | *Int. J. Electrical Power & Energy Systems* (Elsevier, 2015) | Real-time auto-tuned adaptive MPPT |
| **"Real-Time Digital Simulation and Analysis of Sliding Mode and P&O MPPT Algorithms for a PV System"** | *Int. J. Emerging Electric Power Engineering* (2015) | Real-time OPAL-RT validation of SMC-MPPT vs P&O |
| **"Grey Wolf Optimization Based MPPT for PV System under Changing Insolation"** | IEEE Techsym | Metaheuristic optimization for MPPT |
| **"Nonlinear H∞ State Feedback Technique for Autonomous Underwater Vehicle"** | AUV steering control | Robust H∞ control — same mathematical framework applied to AUV |

### NIT Rourkela Connection
Prof. Subudhi was previously a Professor and HOD at NIT Rourkela — **the same institution as Prof. K.B. Mohanty (Session 14 — Wind Control)**. They are academic colleagues from the same EEE department.

---

##  Topic Deep Dive: Robust and Adaptive Control for PV and Microgrid Systems

Prof. Subudhi brings the most advanced **control theory perspective** of the entire FDP. While earlier sessions (Dr. Ghosh, Dr. Gautam, Dr. Ghose) covered standard PI, SMC, and SRF control, Prof. Subudhi's session elevates to **Lyapunov stability theory, robust H∞, adaptive control with formal proofs, and fixed-time convergence** — the mathematical frontier of power systems control.

---

### 1. The Control Theory Hierarchy

```
Level 1 — Empirical:     PID, P&O MPPT
Level 2 — Classical:     Lead-lag, root locus, frequency domain design
Level 3 — Modern:        State-space, LQR, Kalman filter
Level 4 — Nonlinear:     Feedback linearization, Backstepping, SMC
Level 5 — Robust:        H∞ control, μ-synthesis (parameter uncertainty)
Level 6 — Adaptive:      MRAC, Lyapunov-based adaptive, self-tuning
Level 7 — Provably safe: Fixed-time controllers, IDA-PBC, CLF-based
           ↑ Prof. Subudhi's domain
```

**Why does PV/microgrid control need this level of sophistication?**
- Solar irradiance varies from 0 to 1000 W/m² — the system operating point changes continuously
- Grid parameters (impedance, voltage) are uncertain and variable
- Microgrids switch between grid-connected and islanded modes — different dynamics
- Standard PI controllers are tuned at one operating point — performance degrades elsewhere
- Robust and adaptive control provides **guaranteed performance across the entire operating range**

---

### 2. Robust Control — H∞ and Structured Uncertainty

**Robust control** designs a single controller that maintains stability and performance despite **bounded parameter uncertainty**.

**H∞ Control:**
- Minimize the worst-case gain from disturbance input to output: `min ||T_zw||∞`
- The ∞-norm = worst-case gain across all frequencies — minimizing it = best worst-case rejection
- Designed using Linear Matrix Inequalities (LMIs) — solved by convex optimization tools (YALMIP, CVX)
- **Prof. Subudhi's application**: H∞ state feedback for Autonomous Underwater Vehicle steering control — same mathematical framework directly applicable to grid-connected PV systems

**Robust PV control application:**
- Uncertain parameters: solar irradiance (unknown, fast-varying), temperature (drifts slowly), parasitic capacitance (varies with PV array configuration)
- H∞ controller designed for the worst-case combination of all these uncertainties
- **Guarantee**: Performance specifications (voltage regulation, THD) satisfied for ALL possible irradiance/temperature combinations within specified bounds

**The uncertainty model:**
- **Parametric uncertainty**: Resistance, capacitance, inductance values vary ±20%
- **Unmodeled dynamics**: High-frequency resonances of LCL filter not in design model
- **Perturbations**: Grid voltage disturbances, load changes, switching noise
- H∞ design incorporates all three — the controller is "pessimistic" enough to handle all of them

---

### 3. Adaptive Control — Lyapunov-Based Approach (Prof. Subudhi's Signature)

**Adaptive control** adjusts controller parameters **in real-time** based on measured behavior — no prior knowledge of exact plant parameters needed.

#### Lyapunov-Based Adaptive Control (LBAC) — His Key Method

The key insight: use **Lyapunov stability theory** not just to analyze stability, but to **design** the adaptive update law.

**Design steps:**
1. Choose a **Lyapunov function** V(x, θ̃) — depends on system states x AND parameter estimation errors θ̃
2. Derive the control law u(x, θ̂) and adaptive update law θ̂̇ such that V̇ ≤ 0
3. By Lyapunov's theorem: V̇ ≤ 0 guarantees asymptotic stability

**Key property**: The adaptive update law is **derived from mathematics** — not heuristically tuned. This gives a **formal proof of stability** even as parameters adapt.

**Prof. Subudhi's LBAC for Grid-Connected PV (IET Smart Grid 2021):**
- **Problem**: Single-stage 3-phase grid-connected PV system; irradiance uncertainty affects PV voltage
- **Uncertain parameter**: Solar irradiance G (affects the PV current source magnitude I_ph = f(G))
- **LBAC design**:
  - Lyapunov function: V = ½e² + (1/γ)θ̃² where e = voltage error, θ̃ = irradiance estimation error
  - Adaptive law: γ is the adaptation gain — how fast the irradiance estimate updates
  - Control law guarantees: voltage tracks reference → PV operates at MPPT even under fast irradiance change
- **Self-tuned adaptation rate**: The adaptation gain γ itself adjusts automatically — his 2021 IEEE paper extension

**Why this beats standard PI:**
| | PI Controller | LBAC |
|---|---|---|
| Stability proof | Only for linearized system | Global Lyapunov proof |
| Parameter variation | Performance degrades | Adapts in real-time |
| Tuning | Manual (trial and error) | Derived from stability condition |
| Irradiance change response | May oscillate | Smooth, provably stable |

---

### 4. Sliding Mode Control for PV — Double Integral SMC

**Prof. Subudhi's COMPEL 2021 paper**: Optimized Double-Integral Sliding Mode Controller (DISMC) for PV Microgrid.

**Standard SMC for PV:**
- Sliding surface: S = e + c·ė (error + weighted derivative)
- Forces voltage error to zero along the surface
- Robust to parameter uncertainty

**Double-Integral SMC (DISMC):**
- Sliding surface: S = e + c₁·ėe + c₂·∫e + c₃·∫∫e
- The double integral term: eliminates steady-state error even for ramp-type disturbances (slowly varying irradiance)
- Better disturbance rejection than standard SMC
- "Optimized" parameters: c₁, c₂, c₃ chosen by optimization (PSO or analytical LMI)

**PV microgrid application**: Maintains stable DC link voltage + MPPT simultaneously, with formal robustness guarantees.

---

### 5. Adaptive MPPT — Auto-Tuned Controller (Elsevier 2015)

Traditional MPPT controllers (P&O, INC) are fixed — they don't adapt to how fast irradiance is changing.

**Prof. Subudhi's Auto-Tuned Adaptive MPPT:**
- Detects whether irradiance is changing slowly (→ use small perturbation step for accuracy) or fast (→ use large step for speed)
- Adaptation mechanism: estimate rate of change of irradiance from PV voltage/current → adjust MPPT step size in real-time
- **Formally proven convergence** to MPP — unlike P&O which oscillates indefinitely

**Real-time implementation**: Validated on **hardware** using real-time digital simulation — bridging theory and practice.

---

### 6. Backstepping Control for PV-Microgrid — Extended State Observer

**Prof. Subudhi's recent work** (IEEE IARIA 2021): Distributed Extended-State-Observer (ESO) Based Backstepping Control for PV-Integrated AC Microgrid.

**Backstepping control:**
- A systematic design method for nonlinear systems
- Builds controller layer by layer (each "step" stabilizes one subsystem)
- The PV microgrid has: PV source → DC-DC converter → inverter → LCL filter → AC microgrid bus → loads
- Backstepping designs a controller for each layer, with each layer's output as the next layer's reference
- **Guarantees**: Each subsystem is stable → entire cascade is stable

**Extended State Observer (ESO):**
- An observer that estimates **not just states but also total disturbances** (lumped uncertainty from irradiance variation, grid disturbances, parameter uncertainty)
- The backstepping controller then **cancels** the estimated disturbance in real-time
- Result: Near-perfect disturbance rejection — PV microgrid maintains stable operation despite unknown and unmeasured disturbances

---

### 7. Distributed Fixed-Time Microgrid Control (IET Smart Grid)

One of Prof. Subudhi's most advanced contributions — **fixed-time convergence** for microgrid secondary control.

**Context — Microgrid Hierarchical Control:**
- Primary: Local droop control (instant, no communication)
- **Secondary**: Restore frequency/voltage to nominal after droop drops them (requires communication)
- Tertiary: Economic optimization (slow)

**Standard secondary control problem**: Consensus algorithms restore frequency/voltage, but convergence time depends on initial conditions — could take seconds or minutes in a large microgrid.

**Fixed-Time Control:**
- Convergence is guaranteed within a **pre-specified time T*** — independent of initial conditions
- Mathematical tool: Fixed-time Lyapunov theorem — V̇ ≤ -αV^p - βV^q where p < 1 < q
- This guarantees: regardless of how large the initial voltage/frequency error is, restoration completes within T*
- **Critical for islanded microgrids** where a large fault could cause a big frequency deviation — operators need to know exactly when the grid will be restored

**Prof. Subudhi's contribution**: Distributed implementation — no central controller needed, each inverter runs the algorithm using only local + neighbor information — robust to single-point-of-failure.

---

### 8. Comparison — All Control Methods for PV/Microgrid

| Method | Stability | Handles Uncertainty | Convergence | Tuning | Prof. Subudhi's Work |
|---|---|---|---|---|---|
| **PI / PID** | Local linear | No | Asymptotic | Manual | Baseline only |
| **SMC** | Lyapunov | Yes (matched) | Asymptotic | Semi-manual | DISMC for PV microgrid |
| **H∞ Robust** | Global (bounded uncertainty) | Yes (worst-case) | Asymptotic | LMI-based | AUV → PV application |
| **LBAC (Lyapunov Adaptive)** | Global Lyapunov proof | Yes (adapts) | Asymptotic | Derived from stability | PV voltage control — his signature |
| **Backstepping + ESO** | Global Lyapunov | Yes (disturbance cancelled) | Asymptotic | Systematic | PV-AC microgrid |
| **Fixed-Time Control** | Global Lyapunov | Yes | **Fixed T* guaranteed** | LMI-based | Secondary microgrid control |
| **IDA-PBC** (Session 6) | Global Lyapunov | Yes (energy-based) | Asymptotic | Energy function design | Dr. Lalitesh Kumar |

---

### 9. Connection to Autonomous Underwater Vehicle (AUV) Research

Prof. Subudhi's unique interdisciplinary work — the same robust/adaptive control theory he applies to PV and microgrids, he also applies to **AUV heading and trajectory control**:
- **Nonlinear H∞ state feedback** for AUV steering: Handles hydrodynamic parameter uncertainty — same LMI framework as robust PV control
- **NARMAX-based adaptive heading controller**: Self-identifies AUV model in real-time — same adaptive update law as LBAC for PV
- **Way-point tracking** using backstepping — same systematic nonlinear design as PV-microgrid control

This cross-domain application demonstrates the universality of the mathematical tools — and makes his perspective uniquely broad.

---

### 10. India Context

- India's **90+ GW solar capacity** requires 90+ GW of grid-connected PV inverters — all of which need robust controllers to operate reliably through India's wide irradiance variation, monsoon cloud dynamics, and weak rural grid conditions
- India's **microgrid program** (₹700+ crore investment in smart grid pilots) requires secondary and tertiary controllers that work reliably in India's variable demand environment
- **IIT Goa** is located in the coastal tropics — high solar irradiance but frequent cloud cover, making adaptive MPPT research particularly relevant to Goa's own solar installations
- Prof. Subudhi's **Dean R&D role at IIT Goa** and **Director role at NIT Warangal** means his research directly influences India's national technical education and research priorities

---

## Questions to Ask 

1. 
   > *"Your Lyapunov-based adaptive voltage controller for grid-connected PV systems uses the adaptation gain γ to determine how quickly the irradiance estimate updates. In your self-tuned version, γ adapts automatically. However, a too-large γ can cause parameter drift and instability, while too-small γ makes the adaptation too slow for fast cloud transients. What is the theoretical bound on γ that your Lyapunov analysis provides — and does this bound change with operating point or grid impedance?"*

2. > *"Your distributed fixed-time secondary control for islanded microgrids guarantees frequency/voltage restoration within a pre-specified time T* regardless of initial conditions. In a large microgrid with many nodes, the communication graph topology determines the convergence rate within T*. How do you select T* in practice — and what communication graph requirements (minimum connectivity, edge weights) are needed to make T* achievable without aggressive, chattering-prone control gains?"*

3. > *"Your Double-Integral SMC for PV microgrid uses a double integral sliding surface to eliminate steady-state error for ramp-type irradiance disturbances. But double integration can cause windup — especially during the startup transient when the PV is first connecting to the grid. How do you handle sliding surface initialization and anti-windup for the DISMC in a real hardware implementation?"*

4. > *"You've applied the same H∞ robust control framework to both autonomous underwater vehicle steering (with hydrodynamic uncertainty) and grid-connected PV systems (with irradiance uncertainty). What is the deepest mathematical reason these two seemingly different physical systems admit the same control design framework — and are there structural properties unique to energy systems (passivity, port-Hamiltonian structure) that H∞ does not exploit, but could?"*

5. > *"As a Fellow of INAE, Fellow of IET (UK), Associate Editor of IEEE Transactions on Sustainable Energy, and now Director of NIT Warangal — from your vantage point at the top of Indian engineering academia, what is the single most important investment India's NIT/IIT system should make in the next decade to ensure Indian researchers lead — not follow — the global frontier in renewable energy control systems?"*

---

##  Key Terms Glossary

| Term | Meaning |
|---|---|
| Robust Control | Controller designed to maintain performance despite bounded parameter uncertainty |
| Adaptive Control | Controller that adjusts its parameters in real-time based on measured behavior |
| H∞ Control | Minimizes worst-case disturbance-to-output gain — the ∞-norm |
| LMI | Linear Matrix Inequality — convex optimization tool for robust control design |
| Lyapunov Function V(x) | Scalar energy-like function — if V̇ ≤ 0, system is stable |
| LBAC | Lyapunov-Based Adaptive Controller — Prof. Subudhi's signature PV control method |
| Adaptation Gain γ | Rate at which LBAC updates its parameter estimate |
| MRAC | Model Reference Adaptive Control — output tracks a reference model |
| Backstepping | Systematic nonlinear controller design for cascade systems |
| ESO | Extended State Observer — estimates both states and total disturbances |
| DISMC | Double-Integral Sliding Mode Controller — enhanced steady-state performance |
| Fixed-Time Control | Controller with convergence guaranteed within T* regardless of initial conditions |
| Finite-Time Control | Converges in finite time, but time depends on initial conditions |
| Consensus Algorithm | Distributed algorithm where each node uses only local + neighbor info |
| Secondary Control | Microgrid control layer that restores frequency/voltage after primary droop |
| NARMAX | Nonlinear AutoRegressive Moving Average with eXogenous input — system ID model |
| INAE | Indian National Academy of Engineering — India's highest engineering fellowship |
| IET (UK) | Institution of Engineering and Technology (UK) — Dr. Subudhi is a Fellow |
| AUV | Autonomous Underwater Vehicle — marine robot; Prof. Subudhi's interdisciplinary domain |
| Grey Wolf Optimization | Metaheuristic MPPT — mimics grey wolf hunting behavior |

---

## **My Profiles**

- LinkedIn: [Link](https://www.linkedin.com/in/un-animesh/)
- GitHub: [Link](https://github.com/unanimesh)
- Email: [Link](https://mailto:un.animesh@zohomail.com)