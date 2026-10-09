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

## Theorem

For an extensive system property $B$ with specific value $b=B/m$, and a fixed control volume,

$$
\boxed{
\frac{\mathrm dB_{sys}}{\mathrm dt}
=\frac{\partial}{\partial t}\int_{CV}\rho b\,\mathrm dV
+\oint_{CS}\rho b(\mathbf u\cdot\mathbf n)\,\mathrm dA
}.
$$

## Meaning

- left: Lagrangian rate of change of the material system;
- first term: accumulation inside the Eulerian control volume;
- second term: net outward transport through its boundary.

## Choices

| $b$ | Balance generated |
|---|---|
| $1$ | mass |
| $\mathbf u$ | linear momentum |
| $e_t$ | total energy |

## Related

- [[Eulerian and Lagrangian Flow Descriptions]] · [[Continuity Equation in Conservative Form]]

