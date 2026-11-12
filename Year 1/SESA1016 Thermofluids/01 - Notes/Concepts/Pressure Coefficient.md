---
title: "Pressure Coefficient"
module: "SESA1016 Thermofluids"
type: concept
stream: "Inviscid Flow"
aliases: ["Cp", "pressure coefficient"]
tags: [sesa1016, concept, pressure]
status: complete
parent_lectures: ["[[SESA1016 T10 - Euler and Bernoulli Equations]]", "[[SESA1016 T14 - Boundary Layers and the Origin of Drag]]"]
related_concepts: ["[[Bernoulli Equation]]", "[[Skin-friction and Pressure Drag]]", "[[Stagnation Pressure and Pitot Tube]]"]
sources: ["02 - Sources/Lectures/Chapter 10.pdf"]
---

# Pressure Coefficient

The pressure coefficient is the local pressure relative to the free stream, divided by the free-stream dynamic pressure: $C_p=\dfrac{p-p_\infty}{\tfrac12\rho V_\infty^2}$.

Making the pressure dimensionless this way removes the dependence on the free-stream speed and density, so one $C_p$ distribution describes a shape at every speed for which the flow pattern is the same. Where the flow obeys the [[Bernoulli Equation]] (outside boundary layers and wakes, with no height change), it depends only on the local speed:

$$
C_p=1-\left(\frac{V}{V_\infty}\right)^2
$$

At a stagnation point $V=0$ and $C_p=1$, its maximum possible value in incompressible flow. Where the flow is faster than the free stream $C_p$ is negative (suction). On a circular cylinder in inviscid flow the surface speed is $2V_\infty\sin\beta$, so $C_p=1-4\sin^2\beta$, reaching $-3$ at the shoulders.

On an aerofoil the lift comes mostly from the suction on the upper surface, so $-C_p$ is often plotted upwards. In a real flow the measured $C_p$ follows the inviscid curve on the front of a bluff body but stays low over the separated rear, and the resulting front-to-back pressure difference is the pressure drag.

![[tf_cylinder_cp.png|760]]

## Related

- [[SESA1016 T10 - Euler and Bernoulli Equations#The pressure coefficient|T10 pressure coefficient]] · [[SESA1016 T10 - Euler and Bernoulli Equations#Worked example - flow round a cylinder|cylinder example]] · [[SESA1016 T14 - Boundary Layers and the Origin of Drag#7. Pressure drag|pressure drag]]
- [[Bernoulli Equation]] · [[Skin-friction and Pressure Drag]] · [[Stagnation Pressure and Pitot Tube]]
