---
title: "SESA2024 01 - Systems Engineering and Spacecraft Design"
module: "SESA2024 Astronautics"
type: topic
stream: "Systems"
order: 1
tags:
  - sesa2024
  - systems-engineering
  - design-process
aliases: ["Spacecraft Systems Engineering", "Chapter 1"]
date: 2026-09-25
status: complete
parent: ["[[SESA2024 Astronautics Hub]]"]
prerequisites: []
next_topics: ["[[SESA2024 02 - Kepler's Laws and the Orbit Equation]]"]
key_concepts: ["[[Systems Engineering Design Phases]]", "[[Spacecraft Subsystems]]"]
tutorial_sheets: []
sources: ["02 - Sources/Lectures/Chapter 1/SESA2024 Astronautics - Chapter 1 (Systems Eng.) - Lecture 1 2025-26 BB_sys eng_V1.pdf", "02 - Sources/Lectures/Chapter 4/2025 WEEK 9 - Lecture 1 - Chapter 4 - Payload - v1.pdf"]
---

# SESA2024 01 - Systems Engineering and Spacecraft Design

> [!abstract] Summary
> A spacecraft is a **payload** plus the **services** it needs: structure, ACS, propulsion, power, thermal, comms and data handling.
>
> Systems engineering turns the mission objective into design requirements through four steps: **mission objectives → payload definition → top-level requirements → design requirements**. It then balances the subsystems by trade-off across the ECSS phases 0–F.
>
> The rest of the module is this chain: the orbit (Ch 5, 11) and each subsystem (Ch 6–10) are sized from the payload's needs (Ch 4).

## Key Concepts
- [[Systems Engineering Design Phases]] · [[Spacecraft Subsystems]]

---

## 1. What is systems engineering?
> "Space systems engineering is the science (and **art**) of developing an operable space system capable of meeting the mission objectives efficiently, within the imposed constraints (mass, cost, schedule…)."

**The team**: subsystem specialists, led by the **systems engineer**, who:
- does "first-cut" analysis in every area;
- understands **subsystem interactions**;
- has people skills (leadership, productivity, team spirit, running meetings);
- accepts that **success requires compromise**.

**Example: INTEGRAL** (ESA gamma-ray observatory, launched 2002):
- 4000 kg, of which 2000 kg is payload; 5 m tall;
- highly elliptical orbit with a 3-day period;
- planned for 2–3 years, operated for about 20.

## 2. Spacecraft subsystems

| Subsystem | Function | Ch |
|---|---|---|
| **Payload** | fulfil the mission objectives (sensors, comms hardware) | 4 |
| Structure | support payload and subsystems in all predicted environments | – |
| **ACS** | achieve the pointing requirements (payload, power, thermal, comms) | 6 |
| **Propulsion** | orbit transfer and orbit control | 7 |
| **Communications** | link to the ground: payload data, telemetry, commands | 9 |
| Data handling (OBDH) | store and process payload, command and health data; route data between subsystems | – |
| **Power** | generate, store and distribute electrical power | 8 |
| **Thermal** | a benign thermal environment, for reliability | 10 |

## 3. From mission objective to design requirements
1. **Mission objectives**, set by the customer. Example: *"fly by Pluto and characterise the Pluto/Charon system"*.
2. **Payload definition**, by a working group of specialists: the specific observations and instrument types (CCD imager, IR spectrometer, field detector).
3. **Top-level requirements (TLRs)**, by the systems team: trajectory, fly-by geometry, payload operations plan.
4. **Design requirements (DRs)** for each subsystem: orbit parameters, ΔVs, fields of view, pointing accuracy and stability, slew rates, data storage, comms link.

> **Payload operation + mission → design requirements.**

> [!example] Exam (2024/25 A1, 2 marks)
> *"What two activities are needed before the TLRs can be defined?"* Define the **mission objectives** and define the **payload**. (2019/20 A1(i) asks for the full chain for 3 marks.)

### Initial study logic (L1 slides 13–17)
customer/user requirement → mission objective → design requirements → **identify system options**:
- stabilisation type: 3-axis, pure spin or dual spin;
- launch-vehicle constraints.

Then: analysis of the options → trade-off and **baseline selection** → customer agreement → preliminary design (performance and budgets, schedule and cost, key technology areas).

The design concept is a synthesis of the **payload** (specification and operation), the **orbit**, the **launch vehicle** (interface and environment) and the **services**.

## 4. Design phases (ECSS-E-ST-10C)
See [[Systems Engineering Design Phases]].

| Phase | Name |
|---|---|
| 0 | Mission analysis / need identification |
| A | Feasibility |
| B | Preliminary definition |
| C | Detailed definition |
| D | Qualification and production |
| E | Operations / utilisation |
| F | Disposal |

System-level activity in phases C, D and E is very expensive, so decisions made early (0, A, B) fix most of the cost.

## 5. Principal system-level trade-offs
| Area | Options |
|---|---|
| Mission analysis | launch vehicle, orbit type, orbit acquisition: a major influence on **all** subsystems |
| ACS | 3-axis, pure spin, dual spin: also a major influence on all subsystems |
| Propulsion | solid; liquid (mono or bi); electric |
| Communications | **power vs gain** |
| Power | solar arrays, RTGs, batteries, fuel cells |
| Thermal | passive vs active |
| Technology | **new vs old** |
| Other | political, regulatory, commercial |

> [!tip] New vs old technology (2021/22 A1, 3 marks)
> Old, flight-proven technology is **conservative**: it minimises cost, schedule and uncertainty (risk), and it has heritage and qualification data. New technology may bring performance, but it needs development, qualification and margin. It is favoured by subsystem specialists, not by the project manager.

## 6. Payload impact on the spacecraft (Ch 4)
The payload **defines the configuration, sizes the spacecraft and specifies the subsystems**.

| Payload requirement | Impact |
|---|---|
| Pointing (accuracy °, stability °/s, slew rates) | choice of stabilisation; ACS sensors, actuators, processor, mass and power |
| Envelope (size, mass) and accommodation | overall configuration; choice of stabilisation |
| Resolution and coverage | **orbit selection**: elements, transfer, station-keeping → propellant; ground-station coverage and eclipse → power and thermal |
| Data rate (plus telemetry and command) | OBDH: storage and processing; comms: power vs gain, frequency, bandwidth |
| Power (peak and average, duty cycle, emergency) | arrays, batteries (cycles, DoD), regulation |
| Thermal (component tolerances, dissipation) | coatings (paint, MLI), heaters, radiator placement |

**Mission and payload types**:
- **communications**: Intelsat, Skynet, TDRSS;
- **Earth observation**: Landsat, SPOT, Envisat, Meteosat;
- **science**: Hubble, XMM-Newton, INTEGRAL, Cassini, Deep Impact;
- **other**: GPS, Galileo, ISS;
- **military**: surveillance, ELINT, early warning.

## 7. Worked example: Ulysses
- A solar-polar mission. A Jupiter gravity assist was needed to leave the ecliptic.
- It was far from the Sun, so it used an **RTG** and was a **spinner** with an Earth-pointing high-gain antenna.
- It shows how the trajectory drove the power, ACS, comms and thermal choices.

## Links
- Parent: [[SESA2024 Astronautics Hub]] · Next: [[SESA2024 02 - Kepler's Laws and the Orbit Equation]]
- Applied throughout: [[SESA2024 11 - Payload and Orbit Selection]], [[SESA2024 13 - Calculating Orbital Elements for a Remote Sensing Mission]]

## Sources
- Chapter 1 lecture (C. Ryan); Chapter 4 Payload lecture (H. Sykulska-Lawrence); Fortescue, Stark & Swinerd, *Spacecraft Systems Engineering*, Ch. 20
