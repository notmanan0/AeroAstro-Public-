---
title: "Degree of Reaction"
module: "SESA2023 Propulsion"
type: concept
stream: "Section 4: Turbomachinery and Propellers"
aliases: ["reaction", "50% reaction", "mirror blading", "repeating stage"]
tags: [sesa2023, concept, turbomachinery]
status: complete
parent_lectures: ["[[SESA2023 W08 - Turbomachinery Principles - Euler Equation and Velocity Triangles]]"]
related_concepts: ["[[Velocity Triangles]]", "[[Euler Work Equation]]", "[[Flow and Work Coefficients]]"]
sources: ["02 - Sources/Lectures/Week 08 - Turbomachinery Principles.pdf"]
---

# Degree of Reaction

The degree of reaction is the fraction of a stage's static-enthalpy change, roughly its pressure change, that happens in the rotor:

$$
R = \frac{h_2-h_1}{h_3-h_1} .
$$

For a repeating stage with constant $V_x$ and $\alpha_3 = \alpha_1$,

$$
R = -\frac{\phi}{2}(\tan\alpha_{1,rel}+\tan\alpha_{2,rel}) = 1-\frac{\phi}{2}(\tan\alpha_1+\tan\alpha_2) .
$$

The lectures themselves speak of mirror blading and repeating stages (L24, ll. 327–346); the phrase "degree of reaction" appears on [[SESA2023 Problem Sheet 8 Turbomachinery Solutions|Problem Sheet 8]] Q8.3, so in the exam describe a 50 % stage as mirror blading and give the reaction definition alongside.

A 50 % reaction stage has mirror-image blading: the stator is the rotor reflected, so $\alpha_1 = -\alpha_{2,rel}$ and $\alpha_2 = -\alpha_{1,rel}$, the velocity triangles are symmetric and the static pressure rise is shared equally between the rows. That balances the blade loading and makes it a good starting point for axial compressors, though real machines needn't use it. Its first rotor needs inlet swirl, so inlet guide vanes are required. For incompressible, loss-free flow in a blade row, $\Delta p/(\rho U^2) = \Delta h/U^2$. A 50 % stage is solved from $\phi$ and $\psi$ with

$$
\tan\alpha_1+\tan\alpha_2 = \frac{1}{\phi},\qquad\tan\alpha_2-\tan\alpha_1 = \frac{\psi}{\phi} .
$$

In PS8 Q8.3, $\phi = 0.55$ and $\psi = 0.439$ give $\tan\alpha_2 = (1.818+0.798)/2$, so $\alpha_2 = 52.6^\circ$, $\alpha_1 = 27.0^\circ$, $\alpha_{1,rel} = -52.6^\circ$ and $\alpha_{2,rel} = -27.0^\circ$, with $R = 0.500$. The lecture stage ($26^\circ$, $\phi = 0.55$, $\psi = 0.45$) has $R = 0.507$, almost 50 %.

## Related

- [[Velocity Triangles]] · [[Euler Work Equation]] · [[Flow and Work Coefficients]]
