---
title: "Blade Twist and Annulus Theory"
module: "SESA3043 Advanced Aeronautics"
type: concept
stream: "Chapter 4: Rotor Aerodynamics"
aliases: ["blade twist", "linear twist", "ideal twist", "annulus theory", "blade element momentum theory", "BEMT", "combined momentum and blade element theory", "three-quarter radius pitch"]
tags: [sesa3043, concept, rotor, hover, blade-element, twist]
status: complete
parent_lectures: ["[[SESA3043 4.1 - Rotor in Hover]]"]
related_concepts: ["[[Blade Element Theory]]", "[[Induced Power Factor]]", "[[Hover Induced Velocity and Disc Loading]]"]
sources: ["02 - Sources/Lectures/CH4 Rotor Aerodynamics.pdf", "02 - Sources/Lectures/20 November 2026 at 14_51_19.txt"]
---

# Blade Twist and Annulus Theory

Blade twist is the variation of blade pitch along the span, $\theta=\theta_0-\kappa r/R$ in linear form, and annulus theory is the combination of momentum and blade element theory, ring by ring, that predicts the non-uniform downwash a given blade produces.

With linear twist the angle of attack is collective minus twist minus inflow, $\alpha=\theta_0-\kappa r/R-v_i/\Omega r$, and the blade-element thrust becomes $C_T/sa=\theta_0/3-\kappa/4-\lambda_i/2$ ([[SESA3043 4.1 - Rotor in Hover#12. Blade twist|4.1 §12]]). Since $\theta_0-\tfrac34\kappa$ is the pitch at $r=0.75R$, a linearly twisted blade makes the same thrust (with uniform inflow) as an untwisted blade set to its three-quarter-radius pitch.

Annulus theory equates the momentum thrust of an annulus, $4\pi\rho v_i^2r\,\mathrm dr$, with its blade-element thrust, which gives

$$
v_i^2(r)=\frac18V_T^2\frac{Nc(r)}{\pi R}a(r)\left(\frac{\theta r}{R}-\frac{v_i(r)}{V_T}\right),
$$

a quadratic for the local downwash with chord, lift slope and pitch all free to vary with radius ([[SESA3043 4.1 - Rotor in Hover#13. Annulus theory|4.1 §13]]). For constant chord the downwash is uniform only if $\theta r$ is constant, $\theta=\theta_{tip}R/r$. This ideal twist gives the minimum induced power ($k_i=1$, [[Induced Power Factor]]) but needs infinite pitch at the root, so real blades use a linear washout of order $8$–$12^\circ$ as an approximation. For a Lynx-sized rotor ($s=0.08$, $C_T=0.0139$) the induced power factor is 1.077 untwisted, 1.036 with $8^\circ$ of linear twist and 1.000 with ideal twist.

## Related

- Parent lecture: [[SESA3043 4.1 - Rotor in Hover]]
- Related concepts: [[Blade Element Theory]] · [[Induced Power Factor]] · [[Hover Induced Velocity and Disc Loading]]
