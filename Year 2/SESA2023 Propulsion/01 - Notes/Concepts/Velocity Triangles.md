---
title: "Velocity Triangles"
module: "SESA2023 Propulsion"
type: concept
stream: "Section 4: Turbomachinery and Propellers"
aliases: ["vector diagrams", "relative velocity", "absolute frame", "rotating frame", "flow angles"]
tags: [sesa2023, concept, turbomachinery]
status: complete
parent_lectures: ["[[SESA2023 W08 - Turbomachinery Principles - Euler Equation and Velocity Triangles]]"]
related_concepts: ["[[Euler Work Equation]]", "[[Degree of Reaction]]", "[[Flow and Work Coefficients]]", "[[Actuator Disk Theory]]"]
sources: ["02 - Sources/Lectures/Week 08 - Turbomachinery Principles.pdf"]
---

# Velocity Triangles

A velocity triangle is the vector relation between the absolute velocity $\mathbf V$, the velocity relative to the blade $\mathbf V_{rel}$, and the blade velocity $\mathbf U$, $\mathbf V = \mathbf V_{rel}+\mathbf U$. In components,

$$
V_x = V_{x,rel},\qquad V_{\theta,rel} = V_\theta-U,\qquad\tan\alpha = \frac{V_\theta}{V_x},\qquad\tan\alpha_{rel} = \frac{V_\theta-U}{V_x} .
$$

Stators are analysed in the absolute frame and rotors in the relative frame. In both, the flow follows the blade metal, with zero incidence at the inlet at design and a small deviation at the exit (the Kutta condition). Angles are measured from axial and are positive in the direction of blade motion, so compressors typically have $\alpha>0$ and $\alpha_{rel}<0$.

In a compressor, the rotor turns the relative flow towards axial, so $|\alpha_{rel}|$ and $V_{rel}$ fall (diffusion) and the pressure rises, while the absolute velocity rises as work is added; the stator then turns the absolute flow back towards axial, slowing it and raising the pressure further. In a turbine, the stator (nozzle guide vanes) accelerates and swirls the flow, and the rotor turns the relative flow further from axial, so $V_{rel}$ rises and the pressure falls, leaving a small or negative absolute swirl at exit. Three identities are useful: $V_x/U = 1/(\tan\alpha-\tan\alpha_{rel})$, $\psi = \phi(\tan\alpha_2-\tan\alpha_1)$, and the static rise is $\tfrac12(V_{1,rel}^2-V_{2,rel}^2)$ in the rotor and $\tfrac12(V_2^2-V_3^2)$ in the stator.

To draw the triangles, put $U$ tangentially and $V_x$ axially, draw the rotor inlet and exit triangles on a common $V_x$, label all four angles and all the magnitudes, and sketch the blade sections so their metal angles match $\alpha_{rel}$ on the rotor and $\alpha$ on the stator.

![[prop_compressor_velocity_triangles.png|700]]

Worked values: the lecture compressor ($U = 300$ m/s, $\phi = 0.55$, $\psi = 0.45$, $\alpha_1 = 26^\circ$) has $\alpha_{1,rel} = -53.1^\circ$, $\alpha_2 = 52.6^\circ$ and $\alpha_{2,rel} = -27.1^\circ$. 2021-22 Q4 ($U = 280$ m/s, $\phi = 0.5$, $\psi = 0.4$, $\alpha_1 = 23^\circ$) gives $V_1 = 152$ m/s, $V_{1,rel} = 261$ m/s at $-57.6^\circ$, $V_2 = 221$ m/s at $50.8^\circ$ and $V_{2,rel} = 177$ m/s at $-37.8^\circ$. The 2022-23 Q4 turbine ($V_x = 200$ m/s, $\alpha_2 = 60^\circ$, $U = 350$ m/s, $w = 100$ kJ/kg) has rotor metal angles of $-1.0^\circ$ at inlet and $-55.3^\circ$ at exit.

![[prop_e2223_q4_turbine_triangles.png|700]]

## Related

- [[Euler Work Equation]] · [[Degree of Reaction]] · [[Flow and Work Coefficients]] · [[Actuator Disk Theory]]
