---
title: "Equivalent Spring Stiffness"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part D: Dynamics"
aliases: ["equivalent stiffness", "k = 3EI/L^3", "springs in series", "springs in parallel", "lumped parameter model", "effective stiffness", "spring rate"]
tags: [feeg1002, concept, dynamics, vibration, stiffness]
status: complete
date: 2026-11-05
parent_lectures: ["[[FEEG1002 D6 - Single Degree of Freedom Vibration]]"]
related_concepts: ["[[Logarithmic Decrement]]", "[[Standard Beam Deflections]]", "[[Stress, Strain and Young's Modulus]]", "[[Torsion of Circular Shafts]]"]
sources: ["02 - Sources/Dynamics/Lectures/Lecture 06 - SDOF Vibration.pdf"]
---

# Equivalent Spring Stiffness

The equivalent stiffness of a structural member is the force per unit deflection, $k=F/\delta$, at the point where the mass sits and in the direction it moves; it lets a real structure act as the spring of a single-degree-of-freedom model.

Any static deflection formula, inverted, gives a stiffness. A rod in tension extends by $\delta=FL/EA$, so $k=EA/L$; a cantilever with a tip load deflects by $FL^3/3EI$, so $k=3EI/L^3$. The other common cases are:

- a block in shear, $k=GA/L$;
- a shaft in torsion, $k=GJ/L$ in N m/rad;
- a helical coil spring, $k=Gd^4/8D^3n$, governed by $G$ because the wire twists;
- an air spring, $k=B_0S^2/V$;
- a beam loaded at midspan, $192EI/L^3$ if both ends are fixed and $48EI/L^3$ if simply supported.

Springs **in parallel** share a displacement, so their forces add and $k=k_1+k_2$. Springs **in series** carry the same force, so their extensions add and $1/k=1/k_1+1/k_2$, the opposite way round from resistors. The test is what is shared, not how the drawing looks. A car wheel held by the tyre (to the road) and the suspension spring (to a body taken as fixed) has both springs connecting it to ground with the same displacement, so they are in parallel: $300+30=330$ kN/m. A post in a flexible clamp is in series with the clamp, which lowers the stiffness and so the natural frequency.

When the static deflection under the weight is known, $k=mg/\delta$ and the mass cancels from the natural frequency, $\omega_n=\sqrt{g/\delta}$: the gantry sign that sags 0.11 m vibrates at 9.44 rad/s (1.50 Hz). For the speed-camera post, a 3 m hollow square section with $I=1.827\times10^{-6}$ m⁴ and $E=210$ GPa gives $k=3EI/L^3=42.6$ kN/m and, with the 25 kg camera, $f_n=6.57$ Hz.

![[d_equivalent_springs.png|760]]

## Related

- [[FEEG1002 D6 - Single Degree of Freedom Vibration#Equivalent springs|equivalent springs in D6]] · [[FEEG1002 D6 - Single Degree of Freedom Vibration#Lumped-parameter models|lumped-parameter models]] · [[FEEG1002 D6 - Single Degree of Freedom Vibration#Gantry sign|gantry sign]] · [[FEEG1002 D6 - Single Degree of Freedom Vibration#Speed camera on a cantilever post|speed camera]] · [[FEEG1002 D6 - Single Degree of Freedom Vibration#Wheel hop of a car|wheel hop]] · [[FEEG1002 A5 - Beam Deflection and Macaulay's Method]] · [[FEEG1002 A8 - Torsion of Circular Shafts]]
- [[Logarithmic Decrement]] · [[Standard Beam Deflections]] · [[Stress, Strain and Young's Modulus]] · [[Torsion of Circular Shafts]]
- Year 2: [[Damping Ratio and Natural Frequency]] · beam deflection in [[SESA2028 S2 - Beam Deflection and Bending Design]] · element stiffness matrices in [[Euler-Bernoulli Beam Element]]
