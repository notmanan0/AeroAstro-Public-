---
title: "Lift-Curve Slope"
module: "SESA1015 Intro to Aero & Astro"
type: concept
stream: "Mechanics of Flight"
aliases: ["lift curve slope", "lift slope", "dCL/dalpha", "C_L alpha", "no lift angle", "zero-lift angle"]
tags: [sesa1015, concept, lift-curve]
status: complete
parent_lectures: ["[[SESA1015 M03 - Aerodynamic Characteristics and the Drag Polar]]"]
related_concepts: ["[[Downwash and Induced Drag]]", "[[Oswald Efficiency Factor]]", "[[Aerofoil Stall]]", "[[Parabolic Drag Polar]]"]
sources: ["02 - Sources/Mechanics of Flight/Mechanics of Flight - Course Notes.pdf (§3.1, pp. 12–13)", "02 - Sources/Mechanics of Flight/Mechanics of Flight - Lecture Slides version 2.pdf (pp. 49–50, 59)"]
---

# Lift-Curve Slope

The lift-curve slope $a=dC_L/d\alpha$ is the rate at which the lift coefficient rises with angle of attack on the straight part of the lift curve; with the no lift angle $\alpha_0$ it gives $C_L=a(\alpha-\alpha_0)$ up to near the stall.

A typical conventional aircraft has $C_L=0.09(\alpha+2)$ with $\alpha$ in degrees: a slope of 0.09 per degree and a no lift angle of $-2^\circ$. The slope depends on the angle unit, $a_{\text{per rad}}=(180/\pi)\,a_{\text{per deg}}$, so the same aircraft has 5.16 per radian. Mixing the two units is the commonest error in lift-curve questions; a value near 0.1 per degree, or 5 to 6 per radian, is the check. The no lift angle is negative for a positively cambered wing, which lifts at zero angle, and zero for a symmetric one.

Thin aerofoil theory gives a two-dimensional section $a_0=2\pi$ per radian. A finite wing has less, because the downwash of its trailing vortices reduces the angle each section sees by the induced angle $\alpha_i=C_L(1+\tau)/\pi AR$. Writing $C_L=a_0(\alpha-\alpha_0-\alpha_i)$ and collecting the $C_L$ terms gives

$$
a=\frac{a_0}{1+\dfrac{a_0}{\pi AR}(1+\tau)},
$$

with $\tau=0$ for an elliptic lift distribution and up to about 0.3 otherwise. A rectangular wing of aspect ratio 13.3 with $\tau=0.1$ has $a=5.39$ per radian, and an aspect ratio of 7 gives about 4.8; the slope approaches $2\pi$ only as the aspect ratio becomes very large. Sweep and the fuselage reduce it further.

From two wind-tunnel readings $(\alpha_1,C_{L1})$ and $(\alpha_2,C_{L2})$ on the linear part, $a=(C_{L2}-C_{L1})/(\alpha_2-\alpha_1)$ and $\alpha_0=\alpha_1-C_{L1}/a$ ([[SESA1015 T03 - Wind-Tunnel Data Reduction Solutions#Question 9]], [[SESA1015 T03 - Wind-Tunnel Data Reduction Solutions#Question 10]]). The line stops at the stall, where separation caps $C_L$ at $C_{L\max}$, about 1.2 clean ([[Aerofoil Stall]]); high-lift devices shift the line upwards and raise $C_{L\max}$, but leave the slope roughly unchanged.

## Related

- Topics: [[SESA1015 M03 - Aerodynamic Characteristics and the Drag Polar]] ([[SESA1015 M03 - Aerodynamic Characteristics and the Drag Polar#2. The lift coefficient|the lift coefficient]]) · [[SESA2022 T4 - Thin Aerofoil Theory]] · [[SESA2022 T5 - Finite Wing Theory]]
- Solutions: [[SESA1015 T03 - Wind-Tunnel Data Reduction Solutions]]
- Concepts: [[Downwash and Induced Drag]] · [[Oswald Efficiency Factor]] · [[Elliptic Lift Distribution]] · [[Aerofoil Stall]] · [[Parabolic Drag Polar]]
- Sources: Course Notes §3.1 (pp. 12–13); Lecture Slides v2, pp. 49–50 and 59.
