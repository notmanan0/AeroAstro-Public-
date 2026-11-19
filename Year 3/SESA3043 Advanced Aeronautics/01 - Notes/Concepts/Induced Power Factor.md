---
title: "Induced Power Factor"
module: "SESA3043 Advanced Aeronautics"
type: concept
stream: "Chapter 4: Rotor Aerodynamics"
aliases: ["k_i", "ki", "induced power correction factor", "annular wake division", "annular wake", "non-uniform downwash", "induced velocity distribution"]
tags: [sesa3043, concept, rotor, hover, induced-power]
status: complete
parent_lectures: ["[[SESA3043 4.1 - Rotor in Hover]]"]
related_concepts: ["[[Hover Induced Velocity and Disc Loading]]", "[[Blade Twist and Annulus Theory]]", "[[Figure of Merit]]"]
sources: ["02 - Sources/Lectures/CH4 Rotor Aerodynamics.pdf", "02 - Sources/Lectures/19 November 2026 at 13_51_11.txt"]
---

# Induced Power Factor

The induced power factor $k_i$ is the ratio of a rotor's actual induced power to the ideal induced power of a uniform actuator disc producing the same thrust, $k_i=P_i/P_{iIDEAL}$ with $P_{iIDEAL}=T\sqrt{T/2\rho A}$.

It comes from annular wake division. A blade's tip moves much faster than its root, so a real rotor pushes the air down unequally along the radius, and the uniform downwash of actuator disc theory is replaced by one that varies with radius but not round the circumference. Each thin annulus of the disc is treated as its own actuator disc with far-wake velocity $2v_i(r)$, so $\mathrm dT=4\pi\rho v_i^2r\,\mathrm dr$ and $\mathrm dP_i=4\pi\rho v_i^3r\,\mathrm dr$. For the power-law family $v_i=v_i^{T_s}(r/R)^n$, where $v_i^{T_s}$ is the tip value, the integrals give $T=2\rho A\left(v_i^{T_s}\right)^2/(n+1)$ and $P_i=4\rho A\left(v_i^{T_s}\right)^3/(3n+2)$, and eliminating $v_i^{T_s}$ at fixed thrust gives

$$
k_i=\frac{(n+1)^{3/2}}{1+3n/2}.
$$

The values are 1.00, 1.05, 1.13, 1.30, 1.45 and 1.73 for $n=0$, 0.5, 1, 2, 3 and 5. $k_i>1$ for every $n>0$, because thrust grows as $v_i^2$ but power as $v_i^3$, so concentrating the downwash costs power faster than it buys thrust. In other words, the thrust is the momentum the wake carries away per second and the induced power the kinetic energy, and for a given momentum flow the kinetic-energy flow is least when the velocity is uniform ([[SESA3043 4.1 - Rotor in Hover#Induced power factor|4.1 §8]]). The uniform distribution is the minimum, and the blade pitch distribution that produces it is the ideal twist $\theta\propto1/r$ ([[Blade Twist and Annulus Theory]]).

Real hovering rotors have $k_i$ of about 1.1–1.2; the untwisted Lynx-like rotor of 4.1 §13 has 1.077. Leishman writes the same factor as $\kappa$, the symbol used here for blade twist.

## Related

- Parent lecture: [[SESA3043 4.1 - Rotor in Hover]]
- Related concepts: [[Hover Induced Velocity and Disc Loading]] · [[Blade Twist and Annulus Theory]] · [[Figure of Merit]]
