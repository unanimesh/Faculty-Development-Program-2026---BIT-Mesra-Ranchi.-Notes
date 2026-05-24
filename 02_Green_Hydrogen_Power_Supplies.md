#  Faculty Development Program 2026 - BIT Mesra
## Session: Green Hydrogen Power Supplies

---

##  Speaker Details

| Field | Details |
|---|---|
| **Name** | Dr. Shiva S. Sarode (Sarode Shiva Kumar) |
| **Designation** | Faculty, Electrical & Electronics Engineering |
| **Institution** | Birla Institute of Technology (BIT), Mesra, Ranchi |
| **Research Areas** | Power Electronics Converters, Machine Drives, Power Factor Correction, Multilevel Inverter Topology |
| **Google Scholar** | ~74+ Citations |
| **Key Collaborations** | Dr. Prem Prakash (BIT Mesra) — joint work on Power Management for Renewable Energy Integrated EV Charging Stations |

### About the Speaker
Dr. Sarode is a Power Electronics specialist at BIT Mesra. His expertise lies at the intersection of:
- **Power Electronic Converter Design** — DC-DC, AC-DC topologies for energy systems
- **Soft-Switching Converters** — e.g., high-efficiency soft-switching step-down DC-DC converters for EV battery charging
- **Multilevel Inverter Topologies** — reducing harmonic distortion in power systems
- **Machine Drives** — motor control for industrial and EV applications
- **Power Factor Correction** — critical for grid-connected power supplies
- **Renewable Energy Integration** — power management for solar/wind-fed charging systems

> **Connection to today's topic:** Green Hydrogen production fundamentally requires **high-efficiency, tightly regulated power supplies** (DC-DC and AC-DC converters) to drive electrolyzers. Dr. Sarode's core expertise in power electronics converters is directly relevant to the **electrolyzer power supply design** — the "heart" of any green hydrogen plant.

---

##  Topic Deep Dive: Green Hydrogen Power Supplies

---

### 1. What Is Green Hydrogen?

Hydrogen is **not an energy source** — it is an **energy carrier**. Unlike fossil fuels which naturally store energy, hydrogen must be produced using energy from another source.

The "color" of hydrogen tells you how it was made:

| Color | Production Method | Emissions |
|---|---|---|
| **Grey** | Steam Methane Reforming (SMR) from natural gas | High CO₂ |
| **Blue** | SMR + Carbon Capture & Storage (CCS) | Reduced CO₂ |
| **Green** | Water Electrolysis using Renewable Energy | Near Zero |
| **Pink** | Electrolysis using Nuclear Energy | Near Zero |
| **Turquoise** | Methane Pyrolysis | Solid carbon byproduct |

**Green Hydrogen** is produced by splitting water (H₂O) into hydrogen (H₂) and oxygen (O₂) using electricity from solar, wind, or hydro sources — making it the cleanest form.

**The reaction:** `2H₂O → 2H₂ + O₂` (electrolysis)

---

### 2. The Electrolyzer — Heart of Green Hydrogen Production

An electrolyzer is the device that performs water electrolysis. There are four main types:

| Type | Full Name | Efficiency | Status |
|---|---|---|---|
| **AWE** | Alkaline Water Electrolyzer | 60–70% | Mature, cheapest, widely deployed |
| **PEM** | Proton Exchange Membrane | 70–80% | Fast response, suits renewables, growing rapidly |
| **SOEC** | Solid Oxide Electrolyzer Cell | Up to 94% | High temp, still emerging |
| **AEM** | Anion Exchange Membrane | Similar to PEM | Early-stage, no precious metals needed |

- **AWE** is well-established and cost-effective but uses corrosive liquid electrolytes and operates at low current densities.
- **PEM** is ideal for pairing with intermittent renewables (solar/wind) due to fast start/stop capability, but uses platinum-group catalysts, making it expensive.
- **SOEC** achieves the highest efficiency by using thermal + electrical energy but needs stable high temperatures (~700–900°C).

---

### 3. What Are "Green Hydrogen Power Supplies"?

This is the **power electronics** side of the topic — Dr. Sarode's specialization.

Electrolyzers require **low-voltage, high-current DC power** (typically 1.8–2.5V per cell, stacked). The grid supplies AC. So between the renewable energy source and the electrolyzer, a chain of power converters is needed:

```
Renewable Energy (Solar PV / Wind)
         ↓
   AC-DC Rectifier (Grid or Generator)
         ↓
   DC-DC Converter (Regulates voltage/current precisely)
         ↓
   Electrolyzer Stack (AWE / PEM / SOEC)
         ↓
   Green Hydrogen (H₂ output)
```

#### Key Power Supply Requirements for Electrolyzers:
- **Tight current regulation** — hydrogen production rate is proportional to current (Faraday's law)
- **Low voltage ripple** — ripple causes electrode degradation and reduces efficiency
- **High efficiency** — even 1% extra loss at MW scale wastes enormous energy
- **Fast dynamic response** — especially for PEM paired with variable solar/wind input
- **Fault tolerance** — electrolyzer stacks are expensive; converters must protect them

#### Power Converter Topologies Used:
- **Non-isolated DC-DC:** Buck, Boost, Buck-Boost converters (simple, high efficiency)
- **Isolated DC-DC:** Full-bridge, Phase-Shift Full Bridge (PSFB), LLC resonant (galvanic isolation, safety)
- **AC-DC:** Active Front-End rectifiers with Power Factor Correction (PFC) — avoids grid harmonics
- **Multilevel Converters:** Reduce switching losses and voltage stress at high power levels

**Soft-switching techniques** (ZVS/ZCS) — Dr. Sarode's research area — are critical here to reduce switching losses in high-frequency converters, enabling compact and efficient electrolyzer power supplies.

---

### 4. Green Hydrogen Storage

Once produced, hydrogen must be stored — a major engineering challenge:

| Method | Description | Energy Density | Challenges |
|---|---|---|---|
| **Compressed Gas** | High-pressure tanks (350–700 bar) | Moderate | Tank weight, safety |
| **Liquid H₂** | Cryogenic (-253°C) | High | Boil-off losses, cost |
| **Metal Hydrides** | H₂ absorbed in solid metal lattice | High gravimetric | Slow kinetics, temperature needed |
| **LOHC** | Liquid Organic Hydrogen Carriers | High | Release energy requirement |
| **Underground/Caverns** | Salt caverns, depleted gas fields | Massive scale | Geography-limited |

---

### 5. Green Hydrogen in Power Systems (Fuel Cells)

Hydrogen stored can be reconverted to electricity via **Fuel Cells**:

- **PEMFC** (Proton Exchange Membrane Fuel Cell) — most common for transport and backup power
- **SOFC** (Solid Oxide Fuel Cell) — high efficiency for stationary power
- The process: `H₂ + O₂ → H₂O + Electricity + Heat` (reverse of electrolysis)
- **No combustion, no CO₂ emissions** — only water vapour as byproduct

**Role in Power Grid:**
- Acts as long-duration energy storage (seasonal storage) — far beyond what batteries can offer
- Balances intermittent renewable generation
- Powers fuel cell vehicles (FCEV), ships, aircraft, heavy industry

---

### 6. India's Green Hydrogen Push

- **National Green Hydrogen Mission** launched January 2023 by Government of India
- **Budget:** ₹19,744 crore (~$2.4B) up to 2029-30
- **Target by 2030:** 5 Million Metric Tonnes Per Annum (MMTPA) production capacity
- **Renewable capacity needed:** 125 GW additional
- **Cost target:** Reduce green hydrogen cost to **$1.5/kg by 2030** (currently ~$4–6/kg)
- **Jobs:** 6 lakh new jobs expected
- **CO₂ savings:** 50 MMTPA of CO₂ emissions abated
- **Hydrogen Hubs** being developed at Kandla, Paradip, and Tuticorin ports for export
- Key players: NTPC, Reliance, IOCL, along with startups and MSMEs

---

### 7. Challenges in Green Hydrogen

| Challenge | Details |
|---|---|
| **High production cost** | Green H₂ costs ~$4–6/kg vs grey H₂ at ~$1–2/kg |
| **Electrolyzer cost** | PEM systems at $750–1,300/kW (Chinese: $300–500/kW) |
| **Renewable intermittency** | Power supply fluctuations affect electrolyzer health and efficiency |
| **H₂ storage & transport** | Low volumetric density, high infrastructure cost |
| **Power supply design** | Achieving high efficiency, low ripple, reliable operation at MW scale |
| **Water requirement** | Electrolysis needs ultra-pure water — scarce in many regions |
| **Safety** | H₂ is highly flammable; requires strict storage and handling protocols |
| **Policy framework** | India still building regulatory and market infrastructure |

---

##  Questions to Ask 



1. 
   > *"For electrolyzer power supplies, what converter topology — isolated or non-isolated, with soft-switching — do you recommend for large-scale PEM electrolyzers paired with variable solar input, and why?"*

2. > *"Power ripple in the electrolyzer supply is known to degrade membrane lifetime. From a power electronics design perspective, what is the acceptable ripple threshold, and how do you achieve it practically?"*

3. > *"Multilevel inverter topologies are known to reduce harmonic distortion. Can they play a role in the AC-DC front-end of green hydrogen power supplies, especially for grid-connected large plants?"*

4. > *"India's National Green Hydrogen Mission targets $1.5/kg by 2030. How much of that cost reduction must come from improved power supply efficiency versus cheaper electrolyzers or cheaper renewable energy?"*

5. > *"As a faculty member at BIT Mesra working in power electronics — what research problems at the converter-electrolyzer interface do you see as the most impactful for students and faculty here to work on?"*

---

##  Key Terms to Know Before the Session

| Term | Meaning |
|---|---|
| Electrolysis | Splitting water into H₂ and O₂ using electrical energy |
| AWE | Alkaline Water Electrolyzer — mature, low-cost |
| PEM | Proton Exchange Membrane electrolyzer — fast, dynamic |
| SOEC | Solid Oxide Electrolyzer Cell — high efficiency, high temp |
| PEMFC | Proton Exchange Membrane Fuel Cell — generates electricity from H₂ |
| PSFB | Phase-Shift Full Bridge — isolated DC-DC converter topology |
| ZVS / ZCS | Zero Voltage / Zero Current Switching — soft-switching techniques |
| PFC | Power Factor Correction — grid-friendly rectifier design |
| THD | Total Harmonic Distortion — measure of power quality |
| LOHC | Liquid Organic Hydrogen Carrier — hydrogen storage medium |
| MMTPA | Million Metric Tonnes Per Annum |
| NGHM | National Green Hydrogen Mission (India, 2023) |
| SECI | Solar Energy Corporation of India |

---


## **My Profiles**

- LinkedIn: [Link](https://www.linkedin.com/in/un-animesh/)
- GitHub: [Link](https://github.com/unanimesh)
- Email: [Link](https://mailto:un.animesh@zohomail.com)
