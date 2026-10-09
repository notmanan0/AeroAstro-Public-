---
title: "Spacecraft Subsystems"
module: "SESA2024 Astronautics"
type: concept
stream: "Systems"
aliases: ["subsystems", "payload and services", "bus", "platform"]
tags: [sesa2024, concept, systems-engineering]
status: complete
parent_lectures: ["[[SESA2024 01 - Systems Engineering and Spacecraft Design]]"]
related_concepts: ["[[Systems Engineering Design Phases]]"]
sources: ["02 - Sources/Lectures/Chapter 1/SESA2024 Astronautics - Chapter 1 (Systems Eng.) - Lecture 1 2025-26 BB_sys eng_V1.pdf"]
---

# Spacecraft Subsystems

## Definition

> [!note] Definition
> A spacecraft is a **payload**, which fulfils the mission objectives, plus the **services** (bus or platform) that keep it working: structure, attitude control, propulsion, communications, data handling, power and thermal.

## Explanation
| Subsystem | Function | Driven by payload through |
|---|---|---|
| Payload (Ch 4) | sensors or comms hardware for the objective | – |
| Structure | support in all environments (launch loads, thermal) | envelope, mass |
| ACS (Ch 6) | pointing: payload, arrays, antennas, radiators, thrust | pointing accuracy, stability, slew |
| Propulsion (Ch 7) | orbit transfer and control; ACS thrusters | orbit, lifetime, station-keeping |
| Communications (Ch 9) | payload data, telemetry and command link | data rate, ground-station coverage |
| OBDH | storage, processing and routing of data | data volume |
| Power (Ch 8) | generation, storage, distribution | load, duty cycle, eclipse |
| Thermal (Ch 10) | benign temperatures for reliability | tolerances, dissipation |

- **Everything couples**. Examples:
  - The LST of the node sets the eclipse, which sets battery and array size and heater power.
  - Dish size sets the pointing requirement (ACS) and the RF power (EPS and thermal).
  - EP choice sets the power demand.
  - The stabilisation type sets array type and payload accommodation.

## Examples
- 2020/21 Q9: "Discuss the subsystem interactions that have influenced this design process."
- 2014/15 Q1(ix): the eclipse fraction affects **power** (battery and array) and **thermal** (heaters) design.

## Related
- [[Systems Engineering Design Phases]] · [[SESA2024 01 - Systems Engineering and Spacecraft Design]]

## Sources
- Chapter 1 lecture slides 6–7; Chapter 4 Payload
