---
title: "Vis-Viva Equation"
module: "SESA2024 Astronautics"
type: concept
stream: "Mission Analysis"
aliases: ["orbital energy equation", "energy equation", "vis-viva", "specific orbital energy", "escape velocity", "circular velocity"]
tags: [sesa2024, concept, orbital-mechanics]
status: lectured
parent_lectures: ["[[SESA2024 04 - Orbital Energy and the Vis-Viva Equation]]"]
related_concepts: ["[[Orbital Angular Momentum]]", "[[Hohmann Transfer]]", "[[Kepler's Laws]]"]
sources: ["02 - Sources/Lectures/Chapter 5/SESA2024 Astronautics - Chapter 5_Orbital energy_V1.pdf"]
---

# Vis-Viva Equation

The vis-viva equation, which the course calls the orbital energy equation, gives the speed of an orbiting body at radius $r$ on an orbit of semi-major axis $a$:

$$
\frac{V^2}{2}-\frac{\mu}{r}=-\frac{\mu}{2a}
\qquad\Longleftrightarrow\qquad
V=\sqrt{\mu\left(\frac2r-\frac1a\right)}.
$$

The left-hand side is the specific orbital energy $\varepsilon$, kinetic plus potential energy per unit mass with the potential taken as zero at infinity. Gravity is conservative, so $\varepsilon$ is constant along the orbit. Evaluating it at periapsis and apoapsis, where $r_pV_p=r_aV_a$, gives $\varepsilon=-\mu/(r_p+r_a)=-\mu/2a$: the energy, like the period, depends only on $a$.

It holds on every conic. Bound orbits have $a>0$ and $\varepsilon<0$, a parabola has $a\to\infty$ and $\varepsilon=0$, and a hyperbola has $a<0$ and $\varepsilon>0$. Its special cases are the circular speed $V_c=\sqrt{\mu/r}$ (put $a=r$), the escape speed $V_{esc}=\sqrt{2\mu/r}=\sqrt2V_c$ (let $a\to\infty$), and the apsis speeds $V_p=\sqrt{(\mu/a)(1+e)/(1-e)}$ and $V_a=\sqrt{(\mu/a)(1-e)/(1+e)}$.

Used the other way round, one measured pair $(r,V)$ gives $1/a=2/r-V^2/\mu$, which identifies an unknown object: an apogee of 1000 km at 5.589 km/s gives a perigee inside the Earth, so a missile rather than a satellite. At any shared point, the orbit with the larger $a$ is the faster one, which is why a forward burn raises the far side of the orbit. Every ΔV in the module, including both Hohmann burns, is a difference between two speeds from this equation.

![[ast_visviva_speed.png|600]]

## Related

- [[SESA2024 04 - Orbital Energy and the Vis-Viva Equation#2. The value of ε|Derivation in the lecture note]] · [[SESA2024 04 - Orbital Energy and the Vis-Viva Equation#Worked examples|Worked examples]]
- [[Orbital Angular Momentum]] · [[Hohmann Transfer]] · [[Kepler's Laws]]
