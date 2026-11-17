---
title: "Induced Velocity in Forward Flight"
module: "SESA3043 Advanced Aeronautics"
type: concept
stream: "Chapter 4: Rotor Aerodynamics"
aliases: ["Glauert's inflow formula", "Glauert's hypothesis", "forward-flight momentum theory", "forward flight induced velocity"]
tags: [sesa3043, concept, rotor, forward-flight, actuator-disc]
status: complete
parent_lectures: ["[[SESA3043 4.3 - Rotor in Forward Flight]]"]
related_concepts: ["[[Disc Tilt]]", "[[Rotor Power Consumption]]", "[[Induced Velocity in Axial Flight]]", "[[Direct Substitution and Newton-Raphson]]"]
sources: ["02 - Sources/Lectures/CH4 Rotor Aerodynamics.pdf"]
---

# Induced Velocity in Forward Flight

The uniform induced velocity of a rotor in forward flight, from actuator disc theory with the mass flow through the disc taken as $\rho AV'$, where $V'$ is the overall inflow velocity.

With $\dot m=\rho AV'$ and a far-wake increment $v_2=2v_i$ normal to the disc (which an energy balance confirms), $T=\rho AV'\cdot2v_i$, so

$$
v_i=\left(\frac{T}{2\rho A}\right)\frac{1}{\sqrt{V_x^2+(V_z+v_i)^2}},\qquad \lambda_i=\frac{C_T}{4}\frac{1}{\sqrt{\mu_x^2+(\mu_z+\lambda_i)^2}}.
$$

It is implicit in $v_i$ and is solved by Newton–Raphson on $f(v_i)=v_i-k/V'$, $k=T/2\rho A$, with $f'=1+k(V_z+v_i)/V'^3$, starting from the hover value $v_0$. It reduces to hover ($v_i=v_0$) when $V=0$, to the climb equation of [[SESA3043 4.2 - Rotor in Axial Flight|4.2]] when $V_x=0$, and at high speed to $v_i\approx T/(2\rho AV)$, the downwash of an elliptically loaded wing of span $2R$ ([[Downwash and Induced Drag]]). With zero tilt it has the closed form $\bar v_i^2=\left(-\bar V^2+\sqrt{\bar V^4+4}\right)/2$.

For the Lynx at 60 m/s ($T=52\,392$ N, $V_x=59.88$ m/s, $V_z=3.79$ m/s) three Newton–Raphson steps from 12.89 m/s give $v_i=2.757$ m/s; the high-speed estimate is 2.768 m/s.

## Related

- Parent lecture: [[SESA3043 4.3 - Rotor in Forward Flight]]
- Related concepts: [[Disc Tilt]] · [[Rotor Power Consumption]] · [[Induced Velocity in Axial Flight]] · [[Direct Substitution and Newton-Raphson]] (SESA2029) · [[Actuator Disk Theory]] (SESA2023)

## Sources

- Sources: CH4 Rotor Aerodynamics, slides 79–87, 90.
- Notes: written ahead from the slides, 17 Nov 2026.
