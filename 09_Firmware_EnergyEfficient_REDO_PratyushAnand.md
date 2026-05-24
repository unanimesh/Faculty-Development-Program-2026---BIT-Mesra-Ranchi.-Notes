#  Faculty Development Program 2026 - BIT Mesra
## Session 09: Writing Software/Firmware for Energy Efficient Systems

---

##  Speaker Details

| Field | Details |
|---|---|
| **Name** | Pratyush Anand |
| **Role** | Senior Principal Firmware Engineering Manager |
| **Company** | Microsoft, Bengaluru |
| **Education** | IIT Delhi |
| **LinkedIn** |[link] (linkedin.com/in/pratyush-anand-b5a8688) |
| **Specialization** | Firmware for ARM Servers and AI Accelerators |

### Career Journey (Verified from LinkedIn)

| Company | Role | Key Work |
|---|---|---|
| **STMicroelectronics** | Embedded Firmware Engineer | Wrote BootROM, U-Boot, Linux BSP for SPEAr1340 (Dual-core ARM Cortex-A9 SoC for multimedia) |
| **Microsoft (Current)** | Senior Principal Firmware Engg. Manager | Manages vertical teams for Azure Cobalt (ARM Server) and Azure Maia (AI Accelerator) firmware |

### His Guest Lecture at BIT Mesra
He previously delivered a talk on **"Open Source Tools and Technologies used for Embedded Linux"** at a National Student Congress organized by **IETE at BIT Mesra** — making this a return visit to your institution.

### What Colleagues Say About Him
> *"He is a great mentor and a patient person. Very analytical and a stellar problem solver. He carries deep expertise in the embedded domain."* — Former colleague at STMicroelectronics

---

##  Important Note on Today's Topic

> Unlike previous 8 sessions (all academic researchers), **Pratyush is an industry practitioner**. His session is not a research paper — it is a **career + technology perspective** from someone who ships firmware used by millions of Azure cloud customers. He taught you two things today:
> 1. **Why firmware matters** — the foundational motivation
> 2. **Data Centers** — the large-scale real-world context

---

##  What He Taught — Reconstructed from the Session Theme

---

### PART 1: Why Firmware Matters

#### What Is Firmware?

Firmware is the software that lives closest to hardware — below the OS, above the bare silicon.

```
┌──────────────────────────┐
│  Your Application / Cloud│  ← What users see
├──────────────────────────┤
│  Operating System        │  ← Linux, Windows
├──────────────────────────┤
│  ★ FIRMWARE ★            │  ← Pratyush's world
│  (BootROM, UEFI, BSP,    │     — Boots the hardware
│   Power Management FW)   │     — Manages power states
├──────────────────────────┤
│  Hardware Silicon        │  ← CPU, GPU, SoC
└──────────────────────────┘
```

**Firmware is responsible for:**
- First code that runs when power is applied (BootROM)
- Initializing all hardware subsystems (clocks, memory, power rails)
- Telling the OS what hardware exists (Device Tree, ACPI tables)
- Managing CPU power states (C-states, P-states) throughout operation
- Thermal management — reading temperature sensors, adjusting compute
- Security — Secure Boot, hardware root of trust

#### Why Does Firmware Matter for Energy Systems?

The entire power electronics chain you've studied this FDP — solar inverters, EV chargers, BMS, fuel cells, microgrids — **all run on microcontrollers or DSPs that need firmware.** Without well-written firmware:

- A BMS that never enters sleep mode drains the battery it's supposed to protect
- A solar inverter that polls sensors continuously instead of using interrupts wastes compute power
- An EV charger that keeps its WiFi radio active 24/7 adds measurable parasitic load
- A microgrid EMS that runs heavy optimization algorithms continuously instead of event-driven wastes energy and generates heat

**The paradox**: Energy systems designed to save energy can themselves waste energy through poorly written firmware.

---

### PART 2: Data Centers — The Large Scale Context

This is where Pratyush's day job connects to energy efficiency at a scale that most engineers never encounter.

#### Why Data Centers Matter for Sustainable Energy

- Global data centers consume approximately **200–250 TWh of electricity per year** — roughly 1% of global electricity demand
- With AI workloads exploding, Microsoft is spending **>$50 billion/year** on data center infrastructure
- A single large AI model training run can consume tens of GWh — equivalent to powering thousands of homes for a year
- Every 1% improvement in firmware-level energy efficiency at Microsoft's scale = **hundreds of millions of dollars** and significant carbon reduction

#### The Azure Cobalt CPU (ARM Server)

Microsoft's custom ARM-based server CPU deployed in Azure:
- **128-core ARM processor** designed for general-purpose cloud workloads
- Delivers ~40% performance improvement over previous generation Azure ARM chips
- Already runs: Microsoft Teams, Azure SQL Database, Azure Communications Services
- **Energy efficiency focus**: ARM architecture is inherently more power-efficient than x86 for many workloads

**Firmware's job on Cobalt:**
- Boot the 128-core chip in the correct power state
- Expose ACPI power state tables (C-states, P-states) to Linux kernel
- Allow Linux cpufreq governor to dynamically scale each core's voltage and frequency
- Handle thermal events — throttle cores before overheating

#### The Azure Maia AI Accelerator

Microsoft's custom chip specifically designed for AI (like an in-house GPU for LLM training/inference):
- Purpose-built for workloads like GPT, Copilot, GitHub Copilot, Azure OpenAI
- Features low-precision math (FP8/FP4) — uses ~8× less energy per operation vs FP32
- Liquid cooling system — enables higher density without overheating
- Custom Ethernet network protocol at 4.8 terabits/second bandwidth

**Firmware's job on Maia:**
- Dynamic power budget enforcement — if chip draws too much, firmware throttles compute
- Real-time thermal monitoring and fan/pump control
- Configuring tensor core precision (FP8 vs FP16 vs FP32) per workload type
- Managing HBM (High Bandwidth Memory) power domains — powering down unused banks
- Boot and initialize the custom accelerator so the AI software stack can run on it

---

### PART 3: Key Firmware Concepts for Energy Efficiency

#### 1. Power States (The Core Concept)

| State | Hardware | Power Consumption | Wake-up Time |
|---|---|---|---|
| **Active (C0)** | Everything running | 100% | Instant |
| **Idle (C1)** | CPU clock halted | ~70% | Microseconds |
| **Sleep (C2/C3)** | CPU + caches off | ~30–40% | Milliseconds |
| **Deep Sleep (C6)** | Core fully powered off | ~5–10% | ~100 μs |
| **System Off** | Almost everything off | ~1% | Seconds |

**Firmware decides which state to enter and when** — this is one of the most impactful energy decisions in any system.

#### 2. Dynamic Voltage and Frequency Scaling (DVFS)

**Physics**: `Power ∝ Voltage² × Frequency`

Reducing voltage by 20% and frequency by 20% → ~36% power reduction.

Firmware manages the **Operating Performance Points (OPP)** table:
- High performance mode: 3.5 GHz @ 1.2V
- Balanced mode: 2.5 GHz @ 1.0V
- Power saving mode: 1.2 GHz @ 0.8V

The OS (Linux) reads these from firmware's ACPI tables and switches between them based on workload demand.

#### 3. Clock Gating and Power Gating

**Clock gating**: Switch off the clock signal to an idle hardware block → eliminates dynamic switching power
**Power gating**: Completely cut power to an unused block → eliminates even leakage current

These are hardware features — but **firmware controls them** by writing to power management registers.

#### 4. Interrupt-Driven vs Polling

| Approach | How It Works | Energy Impact |
|---|---|---|
| **Polling** | CPU continuously checks "is data ready?" | CPU never sleeps → maximum power |
| **Interrupt-driven** | CPU sleeps; hardware wakes it only when needed | CPU sleeps 95%+ of the time |

In energy systems firmware: always prefer interrupt-driven for sensor reading, communication events, and protection triggers.

#### 5. DMA (Direct Memory Access)

Without DMA: CPU wakes up for **every byte** of data from a sensor → never gets to sleep.

With DMA: The DMA controller collects sensor data autonomously into a buffer. CPU wakes only when the buffer is full → sleeps 95% of the time.

**Critical for**: Smart meters, EV charger data logging, battery cell voltage monitoring.

---

### PART 4: Software-Hardware Co-design Philosophy

This is Pratyush's key insight from building Cobalt and Maia:

> **Hardware and firmware cannot be designed independently.** They must be co-designed from day one.

At Microsoft, the silicon architects, firmware engineers, and software teams all work together from the earliest design phase. Hardware choices (power rail granularity, number of power domains, voltage regulator resolution) directly constrain what firmware can do for energy management.

**For energy systems engineers in this FDP** — this means:
- The power converter hardware designer (Dr. Kadwane, Dr. Ghosh) and the firmware engineer must collaborate from the start
- Gate driver timing requirements affect what MCU/DSP timer resolution is needed
- Sensor placement affects interrupt latency and sleep mode feasibility
- Protection relay response time requirements determine whether the firmware can ever sleep deeply

---

##  Questions to Ask 

1. 
   > *"You've worked from bare-metal embedded firmware at STMicroelectronics all the way to firmware for 128-core ARM servers and AI accelerators at Microsoft. What is the single biggest conceptual shift — in how you think about energy-efficient firmware design — when you move from a microcontroller-class system to a data center-scale system?"*

2. > *"For DSP-based power converter firmware (like a solar inverter or EV charger), the control loop must run at 10–50 kHz deterministically, but the system also needs to sleep between iterations. How do you architect the firmware — RTOS vs bare-metal timer interrupts — to get both hard real-time performance AND energy efficiency without compromising safety?"*

3. > *"Secure Boot and firmware signing are critical for energy systems — especially for V2G-capable EV chargers that communicate with the grid. From your experience building secure firmware for Azure infrastructure, what are the top two firmware security practices that even small embedded energy system companies should implement today?"*

4. > *"When Azure Cobalt's firmware exposes C-state tables to the Linux kernel, who actually decides how deep a sleep state the CPU enters — the firmware, the OS governor, or is it a negotiation? And how does this differ for a real-time energy management controller where you cannot afford unexpected latency?"*

5. > *"From your hiring perspective at Microsoft — what skills gap do you most commonly see in firmware engineering candidates from Indian engineering colleges, and what should BIT Mesra students focus on to close that gap?"*

---

## Key Terms Glossary

| Term | Meaning |
|---|---|
| Firmware | Software tightly coupled to hardware — between silicon and OS |
| BootROM | First code executed on power-up, stored in read-only memory on chip |
| BSP | Board Support Package — hardware abstraction for OS drivers |
| U-Boot | Open-source bootloader used in embedded Linux systems |
| UEFI | Unified Extensible Firmware Interface — standard for server firmware |
| ACPI | Advanced Config & Power Interface — firmware-OS power management contract |
| C-states | CPU idle states — deeper = less power, more wake-up latency |
| P-states | CPU performance (voltage/frequency) states — DVFS control |
| DVFS | Dynamic Voltage & Frequency Scaling |
| Clock Gating | Disabling clock to idle hardware — stops dynamic power |
| Power Gating | Cutting power to idle silicon block — stops leakage too |
| DMA | Direct Memory Access — data transfer without CPU involvement |
| Interrupt-driven | CPU sleeps, wakes only on hardware signal — energy-efficient |
| OPP | Operating Performance Point — a voltage + frequency pair |
| SoC | System on Chip — CPU + peripherals integrated on one die |
| ARM Cortex-M | Low-power MCU cores used in embedded energy systems |
| Azure Cobalt | Microsoft's custom 128-core ARM server CPU |
| Azure Maia | Microsoft's custom AI accelerator chip |
| FP8 / FP4 | 8-bit / 4-bit floating point — low precision, high energy efficiency |
| HBM | High Bandwidth Memory — very fast memory used in AI accelerators |
| Co-design | Hardware and firmware/software designed together from the start |
| RTOS | Real-Time Operating System (FreeRTOS, Zephyr) — used in embedded energy systems |

---

## **My Profiles**

- LinkedIn: [Link](https://www.linkedin.com/in/un-animesh/)
- GitHub: [Link](https://github.com/unanimesh)
- Email: [Link](https://mailto:un.animesh@zohomail.com)