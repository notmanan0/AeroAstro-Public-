---
title: "Systems Engineering Design Phases"
module: "SESA2024 Astronautics"
type: concept
stream: "Systems"
aliases: ["ECSS phases", "Phase 0 A B C D E F", "design requirements", "top-level requirements", "TLR", "DR"]
tags: [sesa2024, concept, systems-engineering]
status: lectured
parent_lectures: ["[[SESA2024 01 - Systems Engineering and Spacecraft Design]]"]
related_concepts: ["[[Spacecraft Subsystems]]", "[[Agile Aerospace]]"]
sources: ["02 - Sources/Lectures/Chapter 1/SESA2024 Astronautics - Chapter 1 (Systems Eng.) - Lecture 1 2025-26 BB_sys eng_V1.pdf", "02 - Sources/Lectures/SESA2024 Lecture 2025-10-02.txt", "ECSS-E-ST-10C Rev. 1, System Engineering General Requirements (2017)"]
---

# Systems Engineering Design Phases

Spacecraft development turns a customer's mission objective into subsystem design requirements in four steps, and the ECSS standard ECSS-E-ST-10C divides the life of a project into seven phases, 0 and A to F.

The four steps run in a fixed order because each needs the one before it. The customer or user sets the mission objectives ("fly by Pluto and characterise the Pluto/Charon system"). A working group of specialists defines the payload: the specific observations and the instrument types. The systems team then converts objectives and payload into top-level requirements (TLRs) such as the trajectory, fly-by geometry and payload operation plan, and finally into design requirements (DRs) for each subsystem: orbit parameters, ΔVs, fields of view, pointing accuracy and stability, slew rates, data storage and the communications link. The slide summary is "payload operation + mission → design requirements".

The phases are 0 mission analysis and need identification, A feasibility, B preliminary definition, C detailed definition, D qualification and production, E operations and utilisation, and F disposal. The early work of the course (options, trade-off, baseline selection, preliminary design with budgets, schedule and cost) sits in phases 0 to B and ends at the preliminary design review. System-level work in C, D and E is very expensive because the team grows to detail every subsystem, so a wrong decision before PDR multiplies in cost later. Aeolus, whose novel wind lidar had to be reworked after the spacecraft was built, is the lecture's cautionary example.

Disposal (Phase F) usually means a controlled re-entry from low orbit, or a boost into a graveyard orbit just above GEO.

Past-paper use: 2024/25 A1 (the two activities before the TLRs), 2019/20 A1(i) (all four steps), 2013/14 Q1(i) (the phases).

## Related

- [[SESA2024 01 - Systems Engineering and Spacecraft Design#3. From mission objective to design requirements|Requirements chain in the lecture note]] · [[SESA2024 01 - Systems Engineering and Spacecraft Design#5. Design phases (ECSS)|Phases in the lecture note]]
- [[Spacecraft Subsystems]] · [[Agile Aerospace]] (the iterative alternative)
