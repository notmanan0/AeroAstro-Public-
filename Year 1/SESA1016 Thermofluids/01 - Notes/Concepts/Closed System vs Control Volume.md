---
title: "Closed System vs Control Volume"
module: "SESA1016 Thermofluids"
type: concept
stream: "Foundations"
aliases: ["system", "control volume", "open system"]
tags: [sesa1016, concept, modelling]
status: complete
parent_lectures: ["[[SESA1016 T1 - Thermodynamic Systems, Properties and State]]", "[[SESA1016 T11 - Conservation of Mass]]"]
related_concepts: ["[[Control-volume Analysis Workflow]]", "[[Mass Flow Rate]]", "[[Thermodynamic State and Process]]"]
sources: ["02 - Sources/Lectures/Chapter 1.pdf"]
---

# Closed System vs Control Volume

A closed system is a fixed quantity of matter, whose boundary may move and deform but which no mass crosses; a control volume is a fixed region of space through which mass flows in and out.

The distinction decides which form of the conservation laws to use. For a closed system the laws are the familiar ones written for a body: its mass is constant, $\Delta U=Q-W$, and Newton's second law applies to it directly. A gas in a piston–cylinder is the standard example; the piston moves, so the volume changes, but the same molecules stay inside.

Most engineering devices with a through-flow, such as nozzles, compressors, turbines, jet engines and pipes, are much easier to analyse as control volumes. The analysis then follows not a given lump of fluid but the mass, momentum and energy that cross the boundary per second and the amount that accumulates inside. The Reynolds transport theorem connects the two views: the rate of change for the system that happens to occupy the control volume equals the rate of accumulation inside the control volume plus the net outflow across its surface.

A control volume is chosen, not given. A good choice cuts the flow where the velocity, pressure and properties are known or wanted, and puts the boundary normal to the flow there; the same device can be analysed with several different control volumes.

![[tf_system_types.png|760]]

## Related

- [[SESA1016 T1 - Thermodynamic Systems, Properties and State#1. Closed systems and control volumes|T1 §1]] · [[SESA1016 T11 - Conservation of Mass#3. The control volume|T11 §3]] · [[SESA1016 T13 - Conservation of Energy and Propulsion#4. The Reynolds transport theorem|Reynolds transport theorem]]
- [[Control-volume Analysis Workflow]] · [[Mass Flow Rate]] · [[Thermodynamic State and Process]]
