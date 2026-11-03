---
title: "Chemical Propulsion Systems"
module: "SESA2024 Astronautics"
type: concept
stream: "Spacecraft Subsystems"
aliases: ["monopropellant", "bipropellant", "hydrazine", "solid rocket motor", "hybrid rocket", "cold gas thruster", "hypergolic"]
tags: [sesa2024, concept, propulsion]
status: lectured
parent_lectures: ["[[SESA2024 07 - Spacecraft Propulsion]]"]
related_concepts: ["[[Electric Propulsion Sizing]]", "[[Tsiolkovsky Rocket Equation]]", "[[Rocket Performance Parameters]]"]
sources: ["02 - Sources/Lectures/Chapter 7/Chapter 7 - Propulsion - original slides(1)(1).pdf", "02 - Sources/Lectures/SESA2024 Lecture Chapter 7 - Propulsion - prerecorded material.txt"]
---

# Chemical Propulsion Systems

Chemical propulsion releases energy stored in the propellant by a chemical reaction and expands the hot products through a nozzle; it gives high thrust at specific impulses of roughly 200–450 s.

Liquid monopropellants decompose one liquid on a catalyst bed. Hydrazine, giving ammonia, nitrogen and hydrogen, is the standard, at 1–10 N and 240 s (about 290 s with an electric heater); it is used for attitude control thrusters, and needs only one feed line per thruster, but it is carcinogenic. Bipropellants burn a fuel with an oxidiser. Hydrogen with oxygen or fluorine performs best (fluorine about 410 s) but needs cryogenic storage; monomethylhydrazine with nitrogen tetroxide is hypergolic (ignites on contact) and storable, and is the usual spacecraft choice at 1–400 N and a little over 300 s, at the cost of two feed lines to every thruster and a pressurant system.

Solid motors cannot be stopped once lit. The grain geometry sets the thrust curve, the mass flow rate gives high thrust, and they suit launcher first stages or one-shot apogee motors (the lecture's example gives 60 kN at just under 300 s), but not attitude control. Hybrids keep one component solid to ease storage while keeping some throttle and restart capability. Cold-gas thrusters release stored inert gas: low thrust and limited, but clean near sensitive optics.

For a GEO spacecraft the choice is between a monopropellant system with a solid apogee motor (simpler, easier handling, better structure ratio, lower $I_{sp}$, no restart) and a unified bipropellant system (higher $I_{sp}$, throttle and restart, but more complex and hazardous).

## Related

- [[SESA2024 07 - Spacecraft Propulsion#3. Chemical propulsion|Chemical propulsion in the lecture note]]
- [[Electric Propulsion Sizing]] · [[Tsiolkovsky Rocket Equation]] · [[Rocket Performance Parameters]]
