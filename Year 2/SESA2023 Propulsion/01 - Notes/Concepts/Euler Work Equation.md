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

The Euler work equation gives the work done on the flow by a turbomachine rotor from the change in swirl:

$$
\Delta h_0 = U_2V_{\theta2}-U_1V_{\theta1},\qquad\dot W_x = \dot m\,\Delta h_0 = T\Omega,\qquad T = \dot m(r_2V_{\theta2}-r_1V_{\theta1}) .
$$

At constant radius it becomes $\Delta h_0 = U\,\Delta V_\theta = U\,\Delta V_{\theta,rel} = UV_x(\tan\alpha_2-\tan\alpha_1)$.

It comes from Newton's second law for rotation, torque equals the rate of change of the angular-momentum flux $\dot m\,rV_\theta$, combined with the steady-flow energy equation for adiabatic flow, $\dot W_x = \dot m\Delta h_0$. The lecture quiz on its validity is worth remembering: it holds for compressible flow, with losses including blade friction (the swirl change still sets the work; losses only reduce the pressure rise achieved), for periodic unsteady flow when time-averaged, and for the whole-flow average. It fails with heat transfer, when $\Delta h_0$ is no longer the work, and friction on the hub or casing applies torque too, so it has to be included in $T$.

Compressors have $\Delta h_0>0$, adding swirl in the direction of rotation; turbines have $\Delta h_0<0$, removing swirl, and their exit swirl can be negative. Only the rotor does work: the stators change the static enthalpy, never $h_0$. A radial machine with no inlet swirl and radial vanes, so that the exit $V_\theta = U_2$, has $\Delta h_0 = U_2^2$.

Worked values: a centrifugal impeller at 20,000 rpm with $r_2 = 0.1$ m and 10 kg/s has $U_2 = 209.4$ m/s, $T = 209.4$ N m and $P = 438.6$ kW. An axial turbine with $U = 300$ m/s, $\Delta h_0 = -200$ kJ/kg and $V_{\theta1} = 500$ m/s has $V_{\theta2} = -167$ m/s. In 2024-25 Q4, 15,000 rpm at $r = 0.2$ m with $V_{\theta2} = 200$ m/s gives $w = 62.8$ kJ/kg, $P = 125.7$ kW and $p_{02}/p_{01} = 1.94$ if isentropic. 2020-21 Q4 counts LPT stages from $\Delta h_{0,stage} = \psi U^2$.

## Related

- [[Velocity Triangles]] · [[Flow and Work Coefficients]] · [[Steady Flow Energy Equation]]
