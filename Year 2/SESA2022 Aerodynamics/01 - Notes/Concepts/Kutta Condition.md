---
title: "Kutta Condition"
module: "SESA2022 Aerodynamics"
type: concept
stream: "Topic 4: Thin Aerofoil Theory"
aliases: ["Kutta condition", "smooth trailing-edge flow"]
tags: [sesa2022, concept, thin-aerofoil-theory]
status: complete
parent_lectures: ["[[SESA2022 T4 - Thin Aerofoil Theory]]"]
related_concepts: ["[[Vortex Sheet]]", "[[Kelvin's Circulation Theorem]]", "[[Kutta-Joukowski Theorem]]"]
sources: ["02 - Sources/Airfoils and Wings/Topic 4 Thin airfoil theory_v3.pdf"]
---

# Kutta Condition

## Definition

> [!note] Definition
> Of all the potential-flow solutions round a sharp-trailing-edge aerofoil (one for every value of $\Gamma$), nature picks the one where the **flow leaves the trailing edge smoothly**. For a vortex sheet this means
>
> $$\gamma(TE) = V_1-V_2 = 0$$

## Explanation
- Inviscid theory alone allows any circulation. With the wrong $\Gamma$ the flow would wrap round the sharp TE at infinite velocity, which viscosity forbids.
- **Finite-angle TE**: the TE is a stagnation point ($V_1 = V_2 = 0$). **Cusped TE**: the velocities are finite and equal ($V_1 = V_2$). Either way $\gamma(TE) = 0$.
- In the Fourier solution, the $\frac{1+\cos\theta}{\sin\theta}$ form of the $A_0$ term is chosen precisely so that $\gamma\to0$ at $\theta = \pi$.
- **Physical mechanism**: during start-up, viscous shear at the TE sheds a **starting vortex**. By [[Kelvin's Circulation Theorem]] an equal and opposite bound circulation appears on the aerofoil. The shedding stops once the flow leaves the TE smoothly, which is exactly the Kutta condition.

## Examples
- Used implicitly in every TAT question, e.g. [[SESA2022 Examples Sheet 4 - Thin Aerofoil Theory Solutions]].

## Related
- Parent lectures: [[SESA2022 T4 - Thin Aerofoil Theory]]
- Related concepts: [[Vortex Sheet]], [[Kelvin's Circulation Theorem]], [[Kutta-Joukowski Theorem]]

## Sources
- `02 - Sources/Airfoils and Wings/Topic 4 Thin airfoil theory_v3.pdf`
