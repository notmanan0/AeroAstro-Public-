---
title: "Orbit Equation and Conic Sections"
module: "SESA2024 Astronautics"
type: concept
stream: "Mission Analysis"
aliases: ["ellipse equation", "polar equation of an orbit", "conic sections", "semi-latus rectum", "true anomaly equation", "orbit equation"]
tags: [sesa2024, concept, orbital-mechanics]
status: lectured
parent_lectures: ["[[SESA2024 02 - Kepler's Laws and the Orbit Equation]]", "[[SESA2024 03 - Orbital Elements and Conic Sections]]"]
related_concepts: ["[[Kepler's Laws]]", "[[Keplerian Orbital Elements]]", "[[Vis-Viva Equation]]"]
sources: ["02 - Sources/Lectures/Chapter 5/SESA2024 Astronautics - Chapter 5_Keplers Laws and the ellipse equation_2025-26_V5.pdf", "02 - Sources/Lectures/Chapter 5/SESA2024 Astronautics - Chapter 5_orbital elements and conic sections_2025-26_V2.pdf"]
---

# Orbit Equation and Conic Sections

The orbit equation gives the distance of an orbiting body from the central body as a function of its true anomaly $\theta$, measured from periapsis:

$$
r=\frac{a(1-e^2)}{1+e\cos\theta}=\frac{h^2/\mu}{1+e\cos\theta}=\frac{p}{1+e\cos\theta}.
$$

It comes out of two independent routes that the course compares. Pure geometry turns the Cartesian ellipse into polar form about a focus, giving the first expression. Newton's second law with inverse-square gravity, after the substitution $u=1/r$, gives $u''+u=\mu/h^2$, whose solution is the second. Matching them gives the semi-latus rectum $p=a(1-e^2)=h^2/\mu$ and proves Kepler's first law.

The same equation is the polar form of every conic section, and $e$ chooses which: $e=0$ is a circle, $0<e<1$ an ellipse, $e=1$ a parabola and $e>1$ a hyperbola, with $a$ negative for a hyperbola. Exactly circular and exactly parabolic orbits are idealisations, since any perturbation moves $e$ off 0 or 1; comet NEOWISE ($e=0.9992$) is near-parabolic and ʻOumuamua ($e=1.20$) is hyperbolic.

At the apses, $r_p=a(1-e)$ and $r_a=a(1+e)$, so $a=(r_p+r_a)/2$ and $e=(r_a-r_p)/(r_a+r_p)$. Inverting the equation for a given radius,

$$
\cos\theta=\frac1e\left[\frac{a(1-e^2)}{r}-1\right],
$$

gives two answers, $\theta$ and $360^\circ-\theta$; pick the one that matches the direction of motion (outbound towards apoapsis or inbound towards periapsis). Past papers use this for re-entering fragments (2023/24 B1) and for a spacecraft entering the Moon's sphere of influence (2022/23 B1).

![[ast_conic_sections.png|500]]

## Related

- [[SESA2024 02 - Kepler's Laws and the Orbit Equation#2. The ellipse in polar form|Geometric derivation]] · [[SESA2024 02 - Kepler's Laws and the Orbit Equation#Radial equation: the orbit equation|Derivation from Newton's laws]] · [[SESA2024 03 - Orbital Elements and Conic Sections#5. Conic sections|Conic sections]]
- [[Kepler's Laws]] · [[Keplerian Orbital Elements]] · [[Vis-Viva Equation]]
