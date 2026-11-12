---
title: "Series and Parallel Resistors"
module: "FEEG1004 Electronics"
type: concept
stream: "Part A: Electrical Fundamentals and DC Circuits"
aliases: ["resistors in series", "resistors in parallel", "product over sum", "equivalent resistance"]
tags: [feeg1004, concept, dc-circuits]
status: complete
parent_lectures: ["[[FEEG1004 A3 - DC Circuit Laws - Ohm, KCL, KVL and Dividers]]"]
related_concepts: ["[[Kirchhoff's Current and Voltage Laws]]", "[[Potential Divider]]"]
sources: ["02 - Sources/S1 Fundamentals/S1-W04-3ab Circuits KCL KVL Resistors - Recorded.pdf", "Recorded lecture 3a", "Tutorial 1 Q4"]
---

# Series and Parallel Resistors

Resistors are in **series** when every node they share has nothing else attached, so the same current flows through all of them, and in **parallel** when they all join the same pair of nodes, so the same voltage appears across all of them.

$$
R_s = R_1 + R_2 + R_3,\qquad \frac{1}{R_p} = \frac{1}{R_1} + \frac{1}{R_2} + \frac{1}{R_3},\qquad R_1\parallel R_2 = \frac{R_1R_2}{R_1 + R_2}
$$

Both rules follow from Kirchhoff's laws. In series, KCL gives a common current and KVL sums the individual voltage drops; in parallel, the voltage is common and KCL sums the branch currents. The parallel value is always smaller than the smallest branch, so a short circuit (0 Ω) in parallel with anything gives 0 Ω.

Series and parallel groups are hard to recognise in a real circuit until it is redrawn, dragging components around without changing which nodes they connect. The same rules apply to complex impedances in AC circuits ([[Complex Impedance]]).

As examples, 2 Ω ∥ 4 Ω = 4/3 Ω, and a 2 Ω resistor in parallel with 4 Ω and 6 Ω in series gives the Thévenin resistance $2\parallel(4 + 6)$ = 5/3 Ω (recorded lecture 7a network).

## Related

- [[FEEG1004 A3 - DC Circuit Laws - Ohm, KCL, KVL and Dividers]]
- [[Potential Divider]] · [[Current Divider]] · [[Thevenin and Norton Equivalent Circuits]]
- Cross-module: springs combine the other way round, [[Equivalent Spring Stiffness]]
- Sources: Recorded lecture 3a; Tutorial 1 Q4
