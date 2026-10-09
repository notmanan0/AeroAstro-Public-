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

## Definition

> [!note] Definition
> The fraction of a stage's static-enthalpy (≈ pressure) change that happens in the **rotor**:
> $$R = \frac{h_2-h_1}{h_3-h_1}$$
> For a constant-$V_x$ repeating stage ($\alpha_3 = \alpha_1$):
> $$R = -\frac{\phi}{2}(\tan\alpha_{1,rel}+\tan\alpha_{2,rel}) = 1-\frac{\phi}{2}(\tan\alpha_1+\tan\alpha_2)$$

## Explanation
- **50 % reaction** gives **mirror-image blading**: the stator is the rotor reflected, so $\alpha_1 = -\alpha_{2,rel}$ and $\alpha_2 = -\alpha_{1,rel}$. The velocity triangles are symmetric, and the static pressure rise is shared equally. It is a good starting point for axial compressors: blade loading is balanced, and it is an acceptable choice (the lecture calls it "mirror blading"). Real machines don't have to use it.
- For **incompressible, loss-free** flow in a blade row, $\Delta p/(\rho U^2) = \Delta h/U^2$.
- **Solving a 50 % stage from $\phi$ and $\psi$**:
  $$\tan\alpha_1+\tan\alpha_2 = \frac{1}{\phi},\qquad\tan\alpha_2-\tan\alpha_1 = \frac{\psi}{\phi}$$
- The first rotor of a 50 % machine needs inlet swirl, so **inlet guide vanes** are required.

## Examples
- PS8 Q8.3: $\phi = 0.55$, $\psi = 0.439$. Then $\tan\alpha_2 = (1.818+0.798)/2$, so **$\alpha_2 = 52.6^\circ$, $\alpha_1 = 27.0^\circ$, $\alpha_{1,rel} = -52.6^\circ$, $\alpha_{2,rel} = -27.0^\circ$**, and $R = 0.500$.
- Lecture stage ($26^\circ$, $\phi = 0.55$, $\psi = 0.45$): $R = 0.507$, almost 50 %.

## Related
- [[Velocity Triangles]] · [[Euler Work Equation]] · [[Flow and Work Coefficients]]

## Sources
- Lecture 24 ("mirror blading"); PS8 Turbomachinery Q8.2–8.3
