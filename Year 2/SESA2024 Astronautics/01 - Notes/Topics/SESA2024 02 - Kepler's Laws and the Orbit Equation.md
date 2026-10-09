---
title: "SESA2024 02 - Kepler's Laws and the Orbit Equation"
module: "SESA2024 Astronautics"
type: topic
stream: "Mission Analysis"
order: 2
tags:
  - sesa2024
  - orbital-mechanics
  - kepler
aliases: ["Kepler's Laws", "Orbital motion", "Chapter 5 Lectures 1-3"]
date: 2026-09-25
status: complete
parent: ["[[SESA2024 Astronautics Hub]]"]
prerequisites: ["[[SESA2024 01 - Systems Engineering and Spacecraft Design]]"]
next_topics: ["[[SESA2024 03 - Orbital Elements and Conic Sections]]"]
key_concepts: ["[[Kepler's Laws]]", "[[Orbit Equation and Conic Sections]]", "[[Orbital Angular Momentum]]"]
tutorial_sheets: ["[[SESA2024 Workbook Ch5 - Mission Analysis Solutions]]"]
sources: ["02 - Sources/Lectures/Chapter 5/SESA2024 Astronautics - Chapter 5_Keplers Laws and the ellipse equation_2025-26_V5.pdf"]
---

# SESA2024 02 - Kepler's Laws and the Orbit Equation

> [!abstract] Summary
> Kepler's three empirical laws follow from Newton's law of gravitation and second law.
> - Writing $\mathbf F = m\mathbf a$ in rotating radial and transverse axes gives two equations.
> - The **transverse** equation says $h = r^2\dot\theta$ is constant (Kepler 2).
> - The **radial** equation, with $u = 1/r$, becomes $u''+u = \mu/h^2$, whose solution $r = (h^2/\mu)/(1+e\cos\theta)$ is a conic (Kepler 1).
> - The area rate $h/2$ and the ellipse area give $\tau = 2\pi\sqrt{a^3/\mu}$ (Kepler 3).
>
> *The derivation is examined only conceptually. The results, especially $\tau$, are used everywhere.*

## Key Concepts
- [[Kepler's Laws]] · [[Orbit Equation and Conic Sections]] · [[Orbital Angular Momentum]]

---

## 1. Kepler's laws of planetary motion
1. **First law (1609)**: the orbit of each planet is an **ellipse with the Sun at one focus**.
2. **Second law (1609)**: the line joining planet and Sun **sweeps out equal areas in equal times**, so the planet is fastest at perihelion.
3. **Third law (1619)**: the **square of the period is proportional to the cube of the mean distance** from the Sun.

Kepler found these from Tycho Brahe's observations. Newton (*Principia*, 1687) proved with calculus that they follow from an **inverse-square** gravitational force.

## 2. The ellipse in polar form (focus-centred)
In Cartesian form (centre $C$): $x^2/a^2+y^2/b^2 = 1$, with $b^2 = a^2(1-e^2)$ and the focus at distance $ae$ from the centre.

Write the point $P$ in polar coordinates $(r,\theta)$ about the focus $F$:
- $r\cos\theta = h\cos\alpha+ae$ and $r\sin\theta = h\sin\alpha$;
- substitute, then solve the quadratic in $r$, keeping the positive root for $0\le e<1$.

Measuring $\theta$ from the **closest point** (periapsis):

$$
\boxed{r = \frac{a(1-e^2)}{1+e\cos\theta}}
$$

## 3. Acceleration in rotating (radial/transverse) axes
Compare the velocity components at two nearby points $P$ and $Q$ (small-angle approximations). The four velocity-change components are:
- radial: $\Delta\dot r-r\dot\theta\Delta\theta$;
- transverse: $\dot r\Delta\theta+r\Delta\dot\theta+\Delta r\dot\theta$.

Divide by $\Delta t$ and take the limit:

$$
a_r = \ddot r-r\dot\theta^2,\qquad a_\theta = 2\dot r\dot\theta+r\ddot\theta
$$

(A 2019/20 exam asked for the circular case: $v = r\dot\theta$ constant, so $a_c = r\dot\theta^2$.)

## 4. Equations of motion
With only gravity acting (central, radial):

$$
\text{radial: }-\frac{GMm}{r^2} = m(\ddot r-r\dot\theta^2),\qquad \text{transverse: }0 = m(2\dot r\dot\theta+r\ddot\theta)
$$

### Transverse: angular momentum is conserved
Using $\dfrac1r\dfrac{d}{dt}(r^2\dot\theta) = 2\dot r\dot\theta+r\ddot\theta = 0$:

$$
h = r^2\dot\theta = rV\sin\alpha = |\mathbf r\times\mathbf V| = \text{constant}
$$

- $\mathbf h$ is the **orbital moment of momentum per unit mass**. It is normal to both $\mathbf r$ and $\mathbf V$, so the **orbit plane is fixed**.
- See [[Orbital Angular Momentum]].

### Radial: the orbit equation
With $\mu = GM$:

$$
\ddot r-r\dot\theta^2 = -\frac{\mu}{r^2}
$$

Substitute $u = 1/r$. By the chain rule:
- $\dot r = -h\,du/d\theta$;
- $\ddot r = -h^2u^2\,d^2u/d\theta^2$;
- $r\dot\theta^2 = h^2u^3$.

$$
\frac{d^2u}{d\theta^2}+u = \frac{\mu}{h^2}\quad\Rightarrow\quad u = A\cos\theta+B\sin\theta+\frac{\mu}{h^2}
$$

Apply the boundary conditions (the $\theta$ datum at periapsis):

$$
r = \frac{h^2/\mu}{1+e\cos\theta}
$$

Compare with the ellipse:

$$
\boxed{a(1-e^2) = \frac{h^2}{\mu} = p\ \text{(semi-latus rectum)}}
$$

**Orbits are conics with the attracting body at the focus, so Kepler 1 is proved.** (Wolfram-Alpha check suggested in the slides: $u''+u = \mu/h^2$.)

## 5. Kepler 2
The area of the thin triangle $SPR$ is $\Delta A\approx\tfrac12r(r\Delta\theta)$, so

$$
\dot A = \tfrac12r^2\dot\theta = \tfrac12h = \text{constant}
$$

Equal areas in equal times, **so the body is faster when closer** ($r_pV_p = r_aV_a$).

## 6. Kepler 3
Ellipse area $A = \pi ab = \pi a^2\sqrt{1-e^2}$. The time for one sweep is

$$
\tau = \frac{A}{\dot A} = \frac{\pi a^2\sqrt{1-e^2}}{\tfrac12\sqrt{\mu a(1-e^2)}} = 2\pi\sqrt{\frac{a^3}{\mu}}\qquad\Rightarrow\qquad \boxed{\tau^2 = \frac{4\pi^2}{\mu}a^3}
$$

- **The period depends only on $a$ and $\mu$**, not on $e$.
- $G = 6.674\times10^{-11}$ m³ kg⁻¹ s⁻² (Cavendish, 1798, measured $6.74\times10^{-11}$).
- $\mu_{Sun} = 1.327\times10^{20}$ m³/s² and $\mu_E = 3.986\times10^{14}$ m³/s².

> [!example] Kepler 3 activity (lecture 3)
> - GEO: $\tau$ = 23 h 56 min = 86 164 s gives $a = [\mu(\tau/2\pi)^2]^{1/3}$ = **42 164 km** (6.611 $R_E$).
> - ISS: $a$ = 6780 km gives $\tau$ = 5556 s, so **15.55 orbits/day**.

> [!example] Using Kepler 3 as a ratio (2024/25 B1)
> An asteroid makes 6 orbits while Earth makes 5, so $\tau_A = \tfrac56\tau_E$ and $a_A = a_E(5/6)^{2/3} = 0.886$ AU. No $\mu$ is needed.

## Links
- Parent: [[SESA2024 Astronautics Hub]] · Previous: [[SESA2024 01 - Systems Engineering and Spacecraft Design]] · Next: [[SESA2024 03 - Orbital Elements and Conic Sections]]
- Exam derivation questions: 2018/19 Q2(i) (Kepler 2 from $h$); 2019/20 B1 (centripetal acceleration → GEO radius); 2015/16 Q2(i) (state the laws)
- Maths: polar coordinates and linear ODEs (MATH2048)

## Year 1 foundation
- Conservation of angular momentum under a central force ([[FEEG1002 D5 - Angular Impulse and Momentum]]) and centripetal acceleration $v^2/r$ ([[FEEG1002 D2 - Curvilinear Motion]]).

## Sources
- Chapter 5 Lectures 1–3 (C. Ryan, after H. Lewis); Fortescue, Stark & Swinerd, Ch. 4
