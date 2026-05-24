#  Faculty Development Program 2026 - BIT Mesra
## Session 19: Advanced Control for High-Performance Wind Electrical Systems

---

##  Speaker Details

| Field | Details |
|---|---|
| **Name** | Prof. Kanungo Barada Mohanty (K. B. Mohanty) |
| **Designation** | Professor, Department of Electrical Engineering |
| **Institution** | National Institute of Technology (NIT) Rourkela, Odisha |
| **Service at NIT Rourkela** | **34 years** |
| **Google Scholar Citations** | 2,915+ |
| **Journal Publications** | 70+ |
| **Conference Papers** | 130+ |
| **Ph.D. Students Guided** | 15 completed + 9 ongoing |

### Academic Background

| Degree | Institution |
|---|---|
| M.Tech. (Electrical Engineering) | **IIT Kharagpur** |
| Ph.D. (Electrical Engineering) | **IIT Kharagpur** |

### Awards & Recognition 

- **World's Top 2% Most Influential Scientists** — Stanford University–Elsevier Research Survey (listed)
- **Global Research Excellence Award**
- **IEI NMLC-FCRIT Excellence Awards** — Academic Excellence & Research Excellence
- **IETE J.C. Bose Memorial Award** — IETE's most prestigious award, named after Sir Jagadish Chandra Bose
- **Institution of Engineers (India) Certificates of Merit**
- **Engineer Sandeep Mohapatra Memorial Award**

### Fellowships & Memberships
- **Fellow, Institution of Engineers (India)** (FIE)
- **Fellow, IETE**
- **Senior Member, IEEE**
- **Academic Visitor** — Loughborough University, UK
- **Visiting Professor & Research Mission** — Faculty of Electrical and Control Engineering, **Gdansk University of Technology, Poland**

### Research Areas 
- **Wind Energy Systems** — DFIG, PMSG, variable speed wind turbines — his primary focus
- **Solar PV Systems** — grid-connected PV control
- **Vector Control of Induction Machines** — rotor flux-oriented control (FOC)
- **Direct Torque Control (DTC)** — of induction generators and motors
- **Sliding Mode Control (SMC)** — robust nonlinear control for wind systems
- **Fuzzy Logic Control** — soft computing for wind energy systems
- **Power Quality Improvement** — THD, harmonics, power factor
- **Multilevel Converter Topologies** — for renewable energy interface

---

## 🌬️ Topic Deep Dive: Advanced Control for High-Performance Wind Electrical Systems

---

### 1. Wind Energy Conversion System (WECS) — The Full Picture

```
Wind → [Wind Turbine Rotor] → [Gearbox (optional)] → [Generator] → [Power Electronics] → Grid
           ↑                                               ↑               ↑
      Aerodynamic control                         Electrical control   Grid-side control
      (pitch angle β)                           (torque/flux control)  (voltage/current)
```

**The control challenge**: Wind speed is **random and variable**. The entire system — aerodynamics, mechanical drivetrain, electrical generator, power converter — must be controlled simultaneously to extract maximum energy while protecting equipment and maintaining grid quality.

---

### 2. Wind Turbine Generators — The Main Types

| Generator Type | Abbreviation | Speed | Converter | Prof. Mohanty's Focus |
|---|---|---|---|---|
| Squirrel Cage Induction Generator | SCIG | Fixed | Full-rated converter or none | Historical — now replaced |
| **Doubly Fed Induction Generator** | **DFIG** | Variable (±30%) | Partial-rated (~30% of rated power) | **Primary research focus** |
| **Permanent Magnet Synchronous Generator** | **PMSG** | Variable (full range) | Full-rated converter | Secondary research focus |
| Wound Rotor Synchronous Generator | WRSG | Variable | Full-rated | Used in large offshore |

**Why DFIG dominates globally (60%+ of installed wind capacity):**
- Only 25–30% of power flows through the converter → lower converter cost and losses
- Can operate ±30% around synchronous speed → captures wind over a wide range
- Proven, mature technology
- Grid code compliance well-established

---

### 3. DFIG — Structure and Working Principle

```
Wind Turbine Rotor
      ↓
Gearbox (steps up speed ~1:100)
      ↓
DFIG (Wound Rotor Induction Generator)
      ↓                    ↓
Stator (directly         Rotor (via slip rings)
connected to grid)           ↓
      ↓              [Back-to-Back Converter]
      ↓              Rotor-Side Converter (RSC) + DC Link + Grid-Side Converter (GSC)
      ↓                    ↓
        ← ← ← Grid ← ← ←
```

**Power flow:**
- At **super-synchronous speed** (ω > ωs): Both stator AND rotor deliver power to grid
- At **sub-synchronous speed** (ω < ωs): Stator delivers power, grid feeds rotor via converter
- At **synchronous speed** (ω = ωs): Only stator delivers power, rotor converter carries zero current

**The Rotor-Side Converter (RSC)** controls:
- Active power output P (by controlling rotor d-axis current)
- Reactive power Q (by controlling rotor q-axis current)
- Stator flux orientation — the foundation of vector control

**The Grid-Side Converter (GSC)** controls:
- DC link voltage (constant)
- Grid-side power factor (unity usually)

---

### 4. Prof. Mohanty's Core: Vector Control of DFIG

#### A. Field-Oriented Control (FOC) / Vector Control

The foundation of high-performance DFIG control. Transforms the complex, coupled AC machine equations into a simple, decoupled DC-like form using the **rotating reference frame**.

**The key transformation:**
- **Park Transform**: Converts 3-phase (abc) quantities → rotating d-q frame aligned with stator flux vector
- In the stator flux-oriented d-q frame:
  - d-axis → flux component → controls reactive power Q
  - q-axis → torque component → controls active power P (and hence electromagnetic torque)
- PI controllers in d-q frame act on DC signals → simple, fast, decoupled control

**Performance achieved:**
- Independent control of P and Q
- Fast torque response (< 1 ms)
- Grid-compliant current injection

**Prof. Mohanty's contribution**: Advanced vector control with adaptive/intelligent components replacing the basic PI controllers.

#### B. Direct Torque Control (DTC) of DFIG

An alternative to FOC. Instead of using coordinate transforms and PI controllers:

- **Directly** controls electromagnetic torque and stator flux magnitude
- Uses a **hysteresis controller** + **switching table** — selects the optimal voltage vector directly
- **Advantages over FOC**: No coordinate transform needed, faster dynamic response, simpler implementation
- **Disadvantages**: Variable switching frequency, torque ripple (higher than FOC)

**Prof. Mohanty's DTC work**: Applied to both induction generators (wind) and induction motors — his 34 years at NIT Rourkela spans both domains.

---

### 5. Sliding Mode Control (SMC) for Wind Systems — Prof. Mohanty's Specialty

One of his primary research areas. SMC is a **robust nonlinear control** technique.

#### Why SMC for Wind Energy?

Wind systems are highly nonlinear:
- Wind speed is unpredictable — turbine operating point changes constantly
- Generator parameters vary with temperature and saturation
- Grid disturbances affect the machine
- Traditional PI controllers (linear, tuned at one operating point) can become sluggish or unstable when conditions change

**Sliding Mode Control principle:**
- Define a **sliding surface** S(x) = 0 — a manifold in the state space where the system behaves as desired
- Design a control law that **drives the system onto the surface** and keeps it there
- Once on the sliding surface, system dynamics are completely determined by the surface equation — **independent of parameter variations and disturbances**

**Control law:**
```
u = u_eq + u_sw

u_eq = equivalent control (keeps system on surface once there)
u_sw = switching control = K × sign(S) (drives toward surface)
```

**Key property**: Once on the sliding surface, the system is **insensitive to matched uncertainties** (parameter variations, external disturbances matching the control input direction).

**Wind energy application:**
- Sliding surface defined on: speed error, flux error, current error
- RSC controller uses SMC → robust to wind speed variations and generator parameter changes
- Achieves MPPT even during fast wind speed transients

**The chattering problem**: The `sign(S)` function causes high-frequency switching → mechanical wear, acoustic noise. Solutions:
- **Boundary layer**: Replace `sign(S)` with `sat(S/φ)` — smooth near the surface
- **Super-twisting SMC**: Higher-order SMC — eliminates chattering while maintaining robustness

#### Prof. Mohanty's SMC Publications:
Applied to DFIG wind systems with vector control framework — combining FOC structure with SMC inner loop controllers for robustness against wind gusts and grid faults.

---

### 6. Fuzzy Logic Control for Wind Systems

Prof. Mohanty's other soft computing research area.

**Why Fuzzy Logic?**
- Wind turbine dynamics are complex and nonlinear — hard to model precisely
- Human expert knowledge (if-then rules) can be encoded in fuzzy rules
- No precise mathematical model required

**Fuzzy controller structure for DFIG:**
```
Error (e) + Rate of Change (de/dt)
           ↓
   Fuzzification (convert to fuzzy sets)
           ↓
   Rule base: IF e is "Large Positive" AND de/dt is "Zero" THEN output is "Large Positive"
           ↓
   Inference (compute fuzzy output)
           ↓
   Defuzzification (convert back to crisp control signal)
           ↓
   Control action → RSC gate signals
```

**DFIG fuzzy applications:**
- MPPT using fuzzy-based speed reference generation
- Fuzzy-tuned PI (self-tuning gains based on operating conditions)
- Fuzzy speed controller for sub/super-synchronous transition
- Reactive power management under grid voltage variation

**Prof. Mohanty's contribution**: Fuzzy + sliding mode hybrid controllers for wind systems — combines fuzzy's adaptability with SMC's robustness.

---

### 7. MPPT — Maximum Power Point Tracking for Wind

Like solar PV, wind turbines must track the maximum power point. But the physics is different.

**Wind turbine power:**
`P = ½ × ρ × A × Cp(λ, β) × v³`

Where:
- ρ = air density
- A = rotor swept area
- **Cp = power coefficient** — aerodynamic efficiency (max ~0.59, Betz limit)
- **λ = tip speed ratio** = (blade tip speed) / (wind speed) = ωR/v
- **β = pitch angle** of blades

**Maximum Cp** occurs at an **optimal λ*** (typically 7–10) → optimal rotor speed for each wind speed.

**MPPT strategies:**

| Method | Principle | Prof. Mohanty's Relevance |
|---|---|---|
| **Optimal Torque Control (OTC)** | T_ref = K_opt × ω² | Simple, no wind speed sensor needed |
| **Tip Speed Ratio (TSR) Control** | Maintain λ = λ* by measuring wind speed | Needs anemometer |
| **Power Signal Feedback (PSF)** | Follow pre-computed optimal P-ω curve | Needs accurate turbine model |
| **Hill Climbing / P&O** | Perturb speed, observe power change | No model needed, slow |
| **SMC-based MPPT** | Sliding surface on power error | Robust, fast — Prof. Mohanty's approach |
| **Fuzzy MPPT** | Fuzzy rules for speed reference | Adaptive to wind variations |

---

### 8. Low Voltage Ride-Through (LVRT) for DFIG

**Grid codes worldwide (including India's CEA 2019) require:**
Wind turbines must remain connected during grid voltage dips (faults) and support voltage recovery — they cannot simply disconnect.

**The DFIG LVRT challenge:**
- During a grid fault, stator voltage drops suddenly → large transient rotor currents → risk of converter damage
- The DC link capacitor may overvolt
- Without protection, the DFIG disconnects via crowbar → this is exactly what grid codes now prohibit

**LVRT solutions:**

| Method | Description |
|---|---|
| **Crowbar protection** | Short-circuit rotor windings during fault — protects converter but loses control |
| **DC chopper** | Dissipates excess DC link energy — maintains converter controllability |
| **Enhanced RSC control** | SMC/MPC-based fast demagnetization — most elegant solution |
| **Series dynamic braking resistor** | Limits fault current while keeping converter online |
| **Advanced vector control with demagnetization** | Detects flux oscillation, applies counteracting rotor voltage |

**Prof. Mohanty's work**: Advanced vector control and SMC-based LVRT strategies for DFIG — maintains control of rotor currents during grid faults, enables smooth recovery.

---

### 9. PMSG Wind Systems (Full Converter)

The second major wind turbine type — increasingly popular for offshore and large onshore:

```
Wind → Turbine → [No gearbox — direct drive] → PMSG → [Full-rated AC-DC-AC Converter] → Grid
```

**Full converter advantages over DFIG:**
- Complete electrical isolation from grid — better fault ride-through
- Full speed range control
- No slip rings → reduced maintenance
- Better for offshore (less maintenance access)

**Control structure:**
- **Machine-Side Converter (MSC)**: Controls generator torque → implements MPPT. Methods: FOC, DTC, SMC
- **Grid-Side Converter (GSC)**: Controls DC link voltage and grid current quality

**Prof. Mohanty's application**: Vector control and DTC applied to PMSG wind systems — the same mathematical framework as DFIG but without the doubly-fed complexity.

---

### 10. Power Quality in Wind Systems

**Prof. Mohanty's research area**: Power Quality Improvement for wind-connected grids.

Wind-connected grids face:

| Issue | Cause | Impact |
|---|---|---|
| **Flicker** | Wind speed turbulence → power fluctuation | Voltage fluctuation → light flicker, equipment issues |
| **Harmonics** | Back-to-back converter switching | Grid THD increase, equipment heating |
| **Reactive power variation** | Wind speed change → Q variation | Voltage regulation problems |
| **Sub-synchronous resonance** | DFIG interacting with series-compensated lines | Shaft torsional oscillations — catastrophic |
| **Inter-harmonic injection** | Non-integer harmonics from variable speed | Interference with communication, protection relays |

**Control solutions:**
- LCL filter at converter output
- Active filtering function in GSC (multifunctional converter)
- Reactive power compensation via STATCOM or Q control in GSC

---

### 11. Multilevel Converter Topologies — Prof. Mohanty's Work

For high-power wind systems (3–10 MW offshore turbines), conventional 2-level VSIs are inadequate. Prof. Mohanty researches:

| Topology | Levels | Application |
|---|---|---|
| **NPC (Neutral Point Clamped)** | 3-level | Standard for medium-voltage wind drives |
| **CHB (Cascaded H-Bridge)** | 5, 7, 9+ levels | High-voltage direct connection |
| **MMC (Modular Multilevel Converter)** | Many | Offshore HVDC wind farm collection |
| **Flying Capacitor** | 3, 4-level | Compact alternative to NPC |

**Advantages for wind**: Lower dV/dt stress on generator insulation, lower THD, can interface with medium-voltage grid directly (eliminates transformer in some cases).

---

### 12. India Wind Energy Context

- India has **46+ GW installed wind capacity** (2024) — 4th largest in world
- Target: **140 GW wind by 2030** (including 30 GW offshore)
- **Tamil Nadu, Gujarat, Rajasthan, Karnataka, Andhra Pradesh** — major wind states
- **Odisha** (NIT Rourkela's home state): Cyclone-prone coastline with significant offshore wind potential
- India's wind turbines are predominantly DFIG-based (Suzlon, Siemens Gamesa India, GE Wind)
- **Grid code**: CEA requires LVRT, reactive power support, frequency response from all wind farms >5 MW
- **Offshore wind**: MNRE issued first offshore wind tender in 2023 — PMSG full-converter systems will dominate

---

##  Questions to Ask

1. 
   > *"In your sliding mode control of DFIG wind systems, the chattering problem is fundamental — the high-frequency switching from the sign function excites mechanical resonances in the drivetrain and causes acoustic noise. Between the boundary layer approach and super-twisting SMC, which have you found more effective for a wind turbine with a long flexible drivetrain, and what does the chatter reduction cost in terms of robustness margin against parameter uncertainty?"*

2. > *"You apply both Vector Control (FOC) and Direct Torque Control (DTC) to DFIG systems. For a practical wind farm operator in India — where maintenance technicians may not have advanced control backgrounds — which control architecture is more fault-tolerant and easier to retune when generator parameters drift due to temperature variation or bearing wear?"*

3. > *"India's grid code (CEA 2019) requires LVRT for wind farms above 5 MW. During a severe three-phase fault, the natural flux of the DFIG stator generates large oscillating rotor currents that can destroy the RSC even before the controller can react. What is the minimum protection response time needed — and can an SMC-based demagnetization controller achieve it, or is hardware crowbar still unavoidable?"*

4. > *"With India targeting 30 GW offshore wind — which will predominantly use direct-drive PMSG with full converters — is the vector control expertise developed over decades for DFIG still transferable, or does the industry need to pivot training and research toward a fundamentally different control paradigm for offshore PMSG systems?"*

5. > *"You've been at NIT Rourkela for 34 years and are listed among the world's top 2% most influential scientists. Looking at the entire arc of wind energy control — from the early fixed-speed squirrel cage systems to today's AI-enhanced DFIG and PMSG systems — what do you believe is the single most important unsolved problem in wind electrical system control that the research community should focus on for the next decade?"*

---

##  Key Terms Glossary

| Term | Meaning |
|---|---|
| DFIG | Doubly Fed Induction Generator — most common variable-speed wind generator |
| PMSG | Permanent Magnet Synchronous Generator — used in direct-drive wind turbines |
| RSC | Rotor-Side Converter — controls DFIG torque and reactive power |
| GSC | Grid-Side Converter — controls DC link voltage and grid-side power factor |
| FOC | Field-Oriented Control — vector control using rotating reference frame (d-q) |
| DTC | Direct Torque Control — directly controls torque and flux without transforms |
| SMC | Sliding Mode Control — robust nonlinear control using sliding surface |
| Sliding Surface | A manifold S(x)=0 where system behaves as desired |
| Chattering | High-frequency oscillation in SMC due to sign function discontinuity |
| Super-Twisting SMC | Higher-order SMC that eliminates chattering |
| Park Transform | Converts 3-phase abc → rotating d-q reference frame |
| MPPT | Maximum Power Point Tracking — extracts maximum wind power |
| Cp | Power coefficient — aerodynamic efficiency of wind turbine rotor |
| Tip Speed Ratio (λ) | Ratio of blade tip speed to wind speed — controls Cp |
| Pitch Angle (β) | Blade pitch — reduces power above rated wind speed |
| Betz Limit | Maximum theoretical Cp = 0.593 — physical limit of wind power extraction |
| OTC | Optimal Torque Control — MPPT via T = K_opt × ω² |
| LVRT | Low Voltage Ride-Through — staying connected during grid voltage dips |
| Crowbar | Short-circuit protection for DFIG rotor during faults |
| Flicker | Rapid voltage fluctuation causing light flicker — wind-induced |
| NPC | Neutral Point Clamped converter — 3-level multilevel topology |
| MMC | Modular Multilevel Converter — used in offshore HVDC wind collection |
| Sub-synchronous Resonance | DFIG oscillation with series-compensated grid — potentially catastrophic |

---

## **My Profiles**

- LinkedIn: [Link](https://www.linkedin.com/in/un-animesh/)
- GitHub: [Link](https://github.com/unanimesh)
- Email: [Link](https://mailto:un.animesh@zohomail.com)
