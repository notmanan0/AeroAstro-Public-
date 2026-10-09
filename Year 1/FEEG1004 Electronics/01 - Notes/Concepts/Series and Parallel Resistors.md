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
sources: ["02 - Sources/S1 Fundamentals/S1-W04-3ab Circuits KCL KVL Resistors - Recorded.pdf"]
---

# Series and Parallel Resistors

## Definition

> [!note] Definition
>
> $$R_s = R_1 + R_2 + R_3,\qquad \frac{1}{R_p} = \frac{1}{R_1} + \frac{1}{R_2} + \frac{1}{R_3},\qquad R_1\parallel R_2 = \frac{R_1R_2}{R_1 + R_2}$$

## Explanation
- **Series**: every shared node has nothing else attached, so the same current flows. **Parallel**: all resistors join the same **pair of nodes**, so the same voltage appears.
- **Derivation**:
  - Series: KVL sums the voltages and KCL gives a common current.
  - Parallel: KCL sums the currents and the voltage is common.
- The parallel value is always smaller than the smallest branch. A short (0 Ω) dominates.
- Recognition is "harder than you think": redraw by dragging components without changing the topology.
- The same rules apply to complex impedances in AC ([[Complex Impedance]]).

## Examples
- 2 Ω ∥ 4 Ω = 4/3 Ω.
- Thévenin resistance of the lecture 7a network: $2\parallel(4 + 6)$ = 5/3 Ω.

## Related
- Topic notes: [[FEEG1004 A3 - DC Circuit Laws - Ohm, KCL, KVL and Dividers]]
- Concepts: [[Potential Divider]] · [[Current Divider]] · [[Thevenin and Norton Equivalent Circuits]]
- Cross-module: springs combine the other way round, [[Equivalent Spring Stiffness]]

## Sources
- Recorded lecture 3a; Tutorial 1 Q4
