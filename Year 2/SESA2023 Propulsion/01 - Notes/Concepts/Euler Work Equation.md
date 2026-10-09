---
title: "Euler Work Equation"
module: "SESA2023 Propulsion"
type: concept
stream: "Section 4: Turbomachinery and Propellers"
aliases: ["Euler turbine equation", "Euler pump equation", "angular momentum", "work transfer"]
tags: [sesa2023, concept, turbomachinery]
status: complete
parent_lectures: ["[[SESA2023 W08 - Turbomachinery Principles - Euler Equation and Velocity Triangles]]"]
related_concepts: ["[[Velocity Triangles]]", "[[Flow and Work Coefficients]]", "[[Steady Flow Energy Equation]]"]
sources: ["02 - Sources/Lectures/Week 08 - Turbomachinery Principles.pdf"]
---
# Euler Work Equation

## Definition

> [!note] Definition
> $$\Delta h_0 = U_2V_{\theta2}-U_1V_{\theta1},\qquad\dot W_x = \dot m\,\Delta h_0 = T\Omega,\qquad T = \dot m(r_2V_{\theta2}-r_1V_{\theta1})$$
> At constant radius: $\Delta h_0 = U\,\Delta V_\theta = U\,\Delta V_{\theta,rel} = UV_x(\tan\alpha_2-\tan\alpha_1)$.

## Explanation
- **Origin**: Newton's second law for rotation (torque = rate of change of the angular-momentum flux $\dot m\,rV_\theta$), plus the SFEE for adiabatic flow ($\dot W_x = \dot m\Delta h_0$).
- **Validity** (a lecture quiz):
  - ✔ Compressible flow.
  - ✔ Losses, blade friction included: the work transfer is still set by the swirl change, and losses only reduce the pressure change achieved.
  - ✔ Periodic, unsteady flow (time-averaged).
  - ✔ Whole-flow average.
  - ✘ With heat transfer, $\Delta h_0\neq$ work.
  - Hub or casing friction applies torque too, so it must be included in $T$.
- **Signs**: compressors have $\Delta h_0>0$ (swirl added in the direction of rotation). Turbines have $\Delta h_0<0$ (swirl removed, and the exit swirl can be *negative*).
- Only the **rotor** does work. The stators change static enthalpy, never $h_0$.
- **Radial machines**: with no inlet swirl and radial vanes (exit $V_\theta = U_2$), $\Delta h_0 = U_2^2$.

## Examples
- Centrifugal impeller at 20,000 rpm, $r_2 = 0.1$ m, 10 kg/s: $U_2 = 209.4$ m/s, $T = 209.4$ N m, $P = 438.6$ kW.
- Axial turbine, $U = 300$ m/s, $\Delta h_0 = -200$ kJ/kg, $V_{\theta1} = 500$: $V_{\theta2} = -167$ m/s.
- 2024-25 Q4: 15,000 rpm, $r = 0.2$ m, $V_{\theta2} = 200$: $w = 62.8$ kJ/kg, $P = 125.7$ kW, and $p_{02}/p_{01} = 1.94$ if isentropic.
- 2020-21 Q4: an LPT stage count from $\Delta h_{0,stage} = \psi U^2$.

## Related
- [[Velocity Triangles]] · [[Flow and Work Coefficients]] · [[Steady Flow Energy Equation]]

## Sources
- Week 8 handout §8.3; Lecture 23
