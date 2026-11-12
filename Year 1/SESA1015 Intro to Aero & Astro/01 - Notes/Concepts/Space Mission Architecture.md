---
title: "Space Mission Architecture"
module: "SESA1015 Intro to Aero & Astro"
type: concept
stream: "Astronautics"
aliases: ["Mission Architecture", "Space mission elements"]
tags: [sesa1015, concept, astronautics, mission-architecture, systems-engineering]
status: complete
parent_lectures: ["[[SESA1015 A01 - Astronautics Foundations, Missions and Applications]]", "[[SESA1015 A06 - Launch Vehicles, Systems and Interfaces]]"]
related_concepts: ["[[Earth Orbit Zones]]", "[[Launch Vehicle Interfaces]]", "[[Space Environment Hazards]]", "[[Spacecraft Subsystems]]"]
sources: ["Astronautics Part 1 (Introduction), pp. 30–77", "Astronautics Part 3 (Launch Vehicles), pp. 27–29"]
---

# Space Mission Architecture

A space mission architecture is the set of elements that together deliver a mission's purpose: the payload that produces the value, the spacecraft bus that keeps it working, the orbit or trajectory, the launch vehicle, the ground segment and the operations concept, including how the mission ends.

The usual order of reasoning starts from the need and works towards the hardware. A need (warn of wildfires earlier, relay television to Europe, return a comet sample) becomes a measurable objective, the objective fixes what must be measured or delivered and how often, that fixes the payload, and the payload with its coverage and revisit needs fixes the orbit. Only then are the bus, the launcher and the ground stations sized. The commercial and science missions of [[SESA1015 A01 - Astronautics Foundations, Missions and Applications|A01]] show the pattern: broadcasting wants a fixed point in the sky and so GEO; navigation wants several satellites in view everywhere and so MEO constellations; high-resolution imaging wants to be close and so LEO; deep-space science wants a transfer trajectory and an autonomous spacecraft, because a command to Voyager 1 takes about 21 hours to arrive.

The elements are coupled, so changing one moves the others. A lower orbit improves resolution and shortens the link, but raises drag ([[Exponential Atmosphere and Scale Height]]) and atomic-oxygen erosion and narrows the view; a higher one passes through the Van Allen belts and multiplies the radiation dose ([[Van Allen Radiation Belts]]). The launcher fixes the mass, the stowed volume inside the fairing, the centre-of-mass position and the launch loads ([[Launch Vehicle Interfaces]], [[Launch Environment Loads]]). The ground segment sets how fast data return, which can matter more than the payload: a requirement for fire alerts within minutes can reshape a constellation and its ground network more than any change of camera.

Missions fail at the joints between elements as often as inside them. Mars Climate Orbiter was lost through a unit mismatch between a contractor's ground software and the navigation team; Philae's lander was healthy but its harpoons and hold-down thruster did not work at touchdown. A good architecture therefore states its success criteria, carries margins on mass, power, propellant and data, identifies single-point failures and plans how each requirement will be verified.

## Related

- Topics: [[SESA1015 A01 - Astronautics Foundations, Missions and Applications]] (§7) · [[SESA1015 A06 - Launch Vehicles, Systems and Interfaces]]
- Concepts: [[Earth Orbit Zones]] · [[Launch Vehicle Interfaces]] · [[Space Environment Hazards]] · [[Spacecraft Subsystems]] · [[Systems Engineering Design Phases]]
- Later: [[SESA2024 01 - Systems Engineering and Spacecraft Design]] · [[SESA2024 11 - Payload and Orbit Selection]]
- Sources: Astronautics Part 1, pp. 30–77; Part 3, pp. 27–29
