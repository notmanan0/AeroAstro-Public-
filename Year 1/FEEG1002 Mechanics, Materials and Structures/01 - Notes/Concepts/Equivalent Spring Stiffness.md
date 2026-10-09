---
title: "Equivalent Spring Stiffness"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part D: Dynamics"
aliases: ["equivalent stiffness", "k = 3EI/L^3", "springs in series", "springs in parallel", "lumped parameter model"]
tags: [feeg1002, concept, dynamics, vibration, stiffness]
status: complete
parent_lectures: ["[[FEEG1002 D6 - Single Degree of Freedom Vibration]]"]
related_concepts: ["[[Damping Ratio and Natural Frequency]]", "[[Standard Beam Deflections]]", "[[Stress, Strain and Young's Modulus]]"]
sources: []
---

# Equivalent Spring Stiffness

## Definition

> [!note] Definition
> The stiffness **at the location and in the direction of the mass**, $k = F/\delta$:
> - rod in tension: $k = EA/L$;
> - cantilever tip: $k = 3EI/L^3$;
> - solid in shear: $k = GA/L$;
> - shaft in torsion: $k_t = GJ/L$;
> - helical spring: $k = Gd^4/8D^3n$;
> - air spring: $k = B_0S^2/V$;
> - parallel: $k_1 + k_2$;
> - series: $1/k = 1/k_1 + 1/k_2$.

## Explanation

- Invert any static deflection formula: $k = P/\delta$. The beam cases come straight from [[Standard Beam Deflections]] ([[FEEG1002 A5 - Beam Deflection and Macaulay's Method]]).
- The same beam has **different** stiffness at different points. A cantilever is 8× stiffer at mid-length than at the tip (the diving board, Tutorial 6 Q4).
- Parallel springs share a displacement and their forces add. Series springs share a force and their compliances add.
- **Static-deflection shortcut**: $k/m = g/\delta_{st}$, so $f_n = \frac1{2\pi}\sqrt{g/\delta_{st}}$.

## Examples

- **Speed camera** (Lecture 6): a 3 m hollow square post gives $k = 3EI/L^3 = 42.7$ kN/m and $f_n = 6.58$ Hz.
- **Tutorial 6 Q2**: a tubular pole gives $k = 1880$ N/m.

![[d_equivalent_springs.png|760]]

## Related

- Topic notes: [[FEEG1002 D6 - Single Degree of Freedom Vibration]]
- Concepts: [[Damping Ratio and Natural Frequency]] · [[Standard Beam Deflections]] · [[Stress, Strain and Young's Modulus]]
- Year 2: [[SESA2028 S2 - Beam Deflection and Bending Design]] · stiffness matrices in FE, [[Euler-Bernoulli Beam Element]]

## Sources

- Dynamics Lecture 6.1
