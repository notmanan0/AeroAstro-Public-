---
title: "Passive vs Active Thermal Control"
module: "SESA2024 Astronautics"
type: concept
stream: "Spacecraft Subsystems"
aliases: ["passive thermal control", "active thermal control", "MLI", "radiators", "heaters", "fluid loop"]
tags: [sesa2024, concept, thermal-control]
status: complete
parent_lectures: ["[[SESA2024 10 - Thermal Control]]"]
related_concepts: ["[[Absorptance and Emittance]]", "[[Spacecraft Thermal Balance Equation]]"]
sources: ["02 - Sources/Lectures/Chapter 10/2025 WEEK 8 - Chapter 10 - Thermal Control - Lecture slides - complete.pdf"]
---

# Passive vs Active Thermal Control

## Definition

> [!note] Definition
> - **Passive**: surface finishes (paints, SSMs), MLI blankets, heat pipes and fixed radiators. No power and no moving parts.
> - **Active**: pumped fluid loops, louvres, (thermostatic) heaters, refrigerators. Needs power, often mechanisms.

## Explanation
| Passive | Active |
|---|---|
| no power, no mechanisms | power, mechanisms (reliability) |
| simple, reliable, cheap | heavier, costlier |
| fixed performance | adaptable; higher heat-transfer rates |

**Passive design guidelines**:
1. Balance environmental input + dissipation against emission.
2. **Insulate** non-radiating surfaces with MLI.
3. Size **radiators** for the **hot** case (upper limits).
4. Size **heaters** for the **cold** case (eclipse, low-power modes).

- Active control is needed when passive cannot hold the limits: cryogenic payload sensors, very tight stability, or harsh and highly variable environments.
- Industry uses **passive whenever possible**. The thermal engineer is involved in nearly every onboard system.

## Examples
- Hubble: tight thermal stability for pointing.
- IR observatories: sensor cooling.
- Exam material-selection problems (2023/24 B3, 2024/25 B3): a heater in eclipse plus the right finish. That is passive design with a thermostatic heater.

## Related
- [[Absorptance and Emittance]] · [[Spacecraft Thermal Balance Equation]]

## Sources
- Chapter 10 slides 27–30; workbook Ch10 Q6
