---
title: "Systems Engineering Design Phases"
module: "SESA2024 Astronautics"
type: concept
stream: "Systems"
aliases: ["ECSS phases", "Phase 0 A B C D E F", "design requirements", "top-level requirements", "TLR"]
tags: [sesa2024, concept, systems-engineering]
status: complete
parent_lectures: ["[[SESA2024 01 - Systems Engineering and Spacecraft Design]]"]
related_concepts: ["[[Spacecraft Subsystems]]"]
sources: ["02 - Sources/Lectures/Chapter 1/SESA2024 Astronautics - Chapter 1 (Systems Eng.) - Lecture 1 2025-26 BB_sys eng_V1.pdf"]
---

# Systems Engineering Design Phases

## Definition

> [!note] Definition
> **Requirements chain**: mission objectives (customer) → payload definition (specialist working group) → **top-level requirements** (systems team) → **design requirements** (per subsystem).
>
> **ECSS-E-ST-10C phases**: **0** mission analysis / need identification · **A** feasibility · **B** preliminary definition · **C** detailed definition · **D** qualification and production · **E** operations / utilisation · **F** disposal.

## Explanation
- **TLR** examples: trajectory, fly-by geometry, payload operations plan.
- **DR** examples: orbit parameters, ΔVs, fields of view, pointing accuracy and stability, slew rates, data storage, comms link.
- "Payload operation + mission → design requirements."
- System-level work in C, D and E is very expensive, so most cost is committed in phases 0, A and B.
- **Initial study logic**: customer requirement → objective → design requirements → system options (stabilisation type, launch-vehicle constraints) → analysis → trade-off and baseline → customer agreement → preliminary design (budgets, schedule and cost, key technologies).
- Major trade-offs:
  - mission analysis (launcher, orbit);
  - ACS type;
  - propulsion (solid, liquid, electric);
  - comms (power vs gain);
  - power (arrays, RTGs, batteries, fuel cells);
  - thermal (passive vs active);
  - technology (new vs old);
  - politics and regulation.

## Examples
- 2013/14 Q1(i): "What are the design phases for a satellite?" (4 marks).
- 2019/20 A1(i): the key steps leading to the DRs (3 marks).
- 2024/25 A1: the two activities before the TLRs: mission objectives and payload definition (2 marks).
- 2021/22 A1: why use old technology? Lower cost, shorter schedule, less uncertainty, flight heritage.

## Related
- [[Spacecraft Subsystems]] · [[SESA2024 01 - Systems Engineering and Spacecraft Design]]

## Sources
- Chapter 1 lecture; ECSS-E-ST-10C Rev. 1
