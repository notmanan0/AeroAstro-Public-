---
title: "Spacecraft Subsystems"
module: "SESA2024 Astronautics"
type: concept
stream: "Systems"
aliases: ["subsystems", "payload and services", "bus", "platform", "spacecraft bus"]
tags: [sesa2024, concept, systems-engineering]
status: lectured
parent_lectures: ["[[SESA2024 01 - Systems Engineering and Spacecraft Design]]"]
related_concepts: ["[[Systems Engineering Design Phases]]"]
sources: ["02 - Sources/Lectures/Chapter 1/SESA2024 Astronautics - Chapter 1 (Systems Eng.) - Lecture 1 2025-26 BB_sys eng_V1.pdf", "02 - Sources/Lectures/Chapter 4/2025 WEEK 9 - Lecture 1 - Chapter 4 - Payload - v1.pdf"]
---

# Spacecraft Subsystems

A spacecraft is a payload, which fulfils the mission objectives, plus a bus (or platform) of service subsystems that deliver it to orbit and keep it working: structure, attitude control, propulsion, communications, data handling, power and thermal.

Each service has one job on the course slides. The structure supports everything through launch loads, vibration and the pressure drop to vacuum. The ACS achieves the pointing requirements of the payload, arrays, antennas and radiators. Propulsion provides orbit transfer and control, and on many spacecraft also dumps reaction-wheel momentum. Communications links the spacecraft to the ground segment for payload data, telemetry and commands. Data handling stores, processes and routes data. Power generates, stores and distributes electricity. Thermal keeps the interior benign, typically near room temperature, for reliability.

The point of listing them together is that they are coupled. The local solar time of the node sets the eclipse, which sizes the battery, the array and the heater power. A larger dish lowers the RF power needed but tightens the pointing requirement. Electric propulsion needs a large array, which in LEO raises the drag. The stabilisation type decides whether the arrays are body-mounted or deployed. Changing one subsystem therefore changes the others, which is the main difference from a car, where a spare wheel can be fitted without redesigning anything else.

The payload drives all of them through its pointing, envelope, resolution and coverage, data rate, power and thermal requirements, and every one of those ends up in the mass and power budgets.

Past-paper use: 2020/21 Q9 (subsystem interactions in a design), 2014/15 Q1(ix) (eclipse fraction and its effect on power and thermal).

## Related

- [[SESA2024 01 - Systems Engineering and Spacecraft Design#1. Payload and bus|Payload and bus in the lecture note]] · [[SESA2024 01 - Systems Engineering and Spacecraft Design#7. How the payload drives the design (Chapter 4)|Payload impact table]]
- [[Systems Engineering Design Phases]]
