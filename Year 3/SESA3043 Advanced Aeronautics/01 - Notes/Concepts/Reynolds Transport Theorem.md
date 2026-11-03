---
title: "Reynolds Transport Theorem"
module: "SESA3043 Advanced Aeronautics"
type: concept
stream: "Chapter 1: Conservation Laws"
aliases: ["RTT", "system-to-control-volume theorem"]
tags: [sesa3043, concept, conservation-laws]
status: complete
parent_lectures: ["[[SESA3043 1.1 - Mathematical Tools and Flow Description]]", "[[SESA3043 1.2 - Conservation Laws and Governing Equations]]"]
related_concepts: ["[[Eulerian and Lagrangian Flow Descriptions]]", "[[Fluid Flow Rate, Flux and Specific Quantity]]"]
sources: ["02 - Sources/Lectures/L1 - SESA3043.txt", "02 - Sources/Lectures/CH1-2 Governing Equations(1).pdf"]
---

# Reynolds Transport Theorem

The Reynolds transport theorem links the rate of change of a property of a material system to what happens in a fixed control volume. For an extensive property $B$ with specific value $b=B/m$,

$$
\boxed{
\frac{\mathrm dB_{sys}}{\mathrm dt}
=\frac{\partial}{\partial t}\int_{CV}\rho b\,\mathrm dV
+\oint_{CS}\rho b(\mathbf u\cdot\mathbf n)\,\mathrm dA
}.
$$

The left side is the Lagrangian rate of change for the system. On the right, the first term is the accumulation inside the Eulerian control volume and the second is the net outward transport through its boundary. Choosing $b=1$ gives the mass balance, $b=\mathbf u$ linear momentum, and $b=E_T$ total energy.

## Related

- [[Eulerian and Lagrangian Flow Descriptions]] · [[Continuity Equation in Conservation Form]]
