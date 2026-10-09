---
title: "Current Divider"
module: "FEEG1004 Electronics"
type: concept
stream: "Part A: Electrical Fundamentals and DC Circuits"
aliases: ["current divider rule"]
tags: [feeg1004, concept, dc-circuits, ac-circuits]
status: complete
parent_lectures: ["[[FEEG1004 A3 - DC Circuit Laws - Ohm, KCL, KVL and Dividers]]", "[[FEEG1004 A7 - Thevenin, Superposition and Relays]]"]
related_concepts: ["[[Potential Divider]]", "[[Series and Parallel Resistors]]"]
sources: ["02 - Sources/S1 Fundamentals/S1-W06 Thevenin and Superposition - Interactive.pdf"]
---

# Current Divider

## Definition

> [!note] Definition
> A current $I$ splitting between two parallel branches:
> $$I_1 = I\frac{R_2}{R_1 + R_2},\qquad I_2 = I\frac{R_1}{R_1 + R_2}$$
> The **other** branch's resistance goes on top.

## Explanation
- Both branches share a voltage $V = I(R_1\parallel R_2)$, so $I_1 = V/R_1$.
- More current takes the lower-resistance path.
- In AC, replace $R$ by $Z$. Tutorial 7 Q5 applies the rule twice with complex impedances.

## Examples
- W6 superposition: $I_2 = 4\times13.33/(13.33 + 20)$ = 1.6 A.
- Tutorial 7 Q5: $I_1 = 20\angle45°\times2/(2 + 4.24\angle28.2°)$ = 6.59∠25.7° A.

## Related
- Topic notes: [[FEEG1004 A3 - DC Circuit Laws - Ohm, KCL, KVL and Dividers]] · [[FEEG1004 D2 - Impedance and Phasor Circuit Analysis]]
- Concepts: [[Potential Divider]] · [[Complex Impedance]]

## Sources
- Week 6 interactive session; Tutorial Sheet 7
