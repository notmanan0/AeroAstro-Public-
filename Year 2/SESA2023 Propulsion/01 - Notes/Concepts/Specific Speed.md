---
title: "Specific Speed"
module: "SESA2023 Propulsion"
type: concept
stream: "Section 4: Turbomachinery and Propellers"
aliases: ["shape factor", "Ns", "machine selection"]
tags: [sesa2023, concept, turbomachinery, dimensional-analysis]
status: complete
parent_lectures: ["[[SESA2023 W09 - Turbomachinery Characteristics - Coefficients, Similarity and Maps]]"]
related_concepts: ["[[Dimensional Analysis of Turbomachines]]", "[[Flow and Work Coefficients]]"]
sources: ["02 - Sources/Lectures/Week 09 - Turbomachinery Characteristics.pdf"]
---

# Specific Speed

The **specific speed** is a combination of $\phi$ and $\psi$ that eliminates the size $D$, so it can be worked out from the duty ($Q$, $\Delta p$, $\Omega$) before the machine is designed:

$$
N_s = \frac{\phi^{1/2}}{\psi^{3/4}} = \frac{Q^{1/2}\,\Omega}{(\Delta p/\rho)^{3/4}}\quad(\Omega\text{ in rad/s, SI units}).
$$

It is better thought of as a shape factor, because each type of machine has its best efficiency at a particular $N_s$. A low specific speed means low flow and high head (low $\phi$, high $\psi$), which calls for positive-displacement or centrifugal machines with short blades and a large radius ratio, such as a vacuum-cleaner fan. A high specific speed means high flow and low head, which calls for axial machines and propellers with a few long, widely spaced blades, such as a windmill. For compressible machines use the inlet volume flow, since $Q$ changes through the machine.

| $N_s$ | Machine |
|---|---|
| < 0.4 | centrifugal |
| ~0.4–2 | mixed flow |
| > 2 | axial |

Aero engines are axial because axial machines give the best efficiency at high mass flow per frontal area, and their stages can be stacked to reach a high pressure ratio at an acceptable weight; small helicopter engines use centrifugal stages instead, at a lower $N_s$, accepting the losses between stages. The legacy question comparing the two (2015-16 Q1(i)) expects the radial compressor's roughly 10:1 per stage, robustness, short length and damage tolerance against its large diameter and inter-stage losses, and the axial compressor's under 2:1 per stage, stackability, small frontal area and higher efficiency at high flow against its fragility and cost.

## Related

- [[Dimensional Analysis of Turbomachines]] · [[Flow and Work Coefficients]]
