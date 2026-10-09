---
title: "SESA2024 04 - Orbital Energy and the Vis-Viva Equation"
module: "SESA2024 Astronautics"
type: topic
stream: "Mission Analysis"
order: 4
tags:
  - sesa2024
  - orbital-mechanics
  - energy-equation
aliases: ["Energy equation", "Vis-viva", "Chapter 5 Lectures 9-10"]
date: 2026-09-25
status: complete
parent: ["[[SESA2024 Astronautics Hub]]"]
prerequisites: ["[[SESA2024 03 - Orbital Elements and Conic Sections]]"]
next_topics: ["[[SESA2024 05 - Orbital Transfers and the Hohmann Transfer]]"]
key_concepts: ["[[Vis-Viva Equation]]", "[[Orbital Angular Momentum]]"]
tutorial_sheets: ["[[SESA2024 Workbook Ch5 - Mission Analysis Solutions]]"]
sources: ["02 - Sources/Lectures/Chapter 5/SESA2024 Astronautics - Chapter 5_Orbital energy_V1.pdf", "02 - Sources/Lectures/Chapter 5/SESA2024 Astronautics - Chapter 5_Orbital energy worked example_V1.pdf"]
---

# SESA2024 04 - Orbital Energy and the Vis-Viva Equation

> [!abstract] Summary
> Gravity is conservative, so the specific orbital energy $\varepsilon = V^2/2-\mu/r$ is constant along an orbit. Evaluating it at perigee and apogee, with $r_pV_p = r_aV_a$, gives $\varepsilon = -\mu/2a$. The result is the **energy (vis-viva) equation**
>
> $$\frac{V^2}{2}-\frac{\mu}{r} = -\frac{\mu}{2a}\quad\Leftrightarrow\quad V = \sqrt{\mu\Big(\frac2r-\frac1a\Big)}$$
>
> It gives the speed anywhere on any conic, and it is the workhorse for every ΔV calculation in the module.

## Key Concepts
- [[Vis-Viva Equation]] · [[Orbital Angular Momentum]]

---

## 1. Kinetic and potential energy
- $KE = \tfrac12mV^2$.
- $PE$ is zero at infinity. It is the work done by gravity bringing $m$ from ∞ to $r$:

$$
PE = -\int_\infty^r\frac{\mu m}{r^2}dr = -\frac{\mu m}{r}
$$

Per unit mass: $\varepsilon = \dfrac{V^2}{2}-\dfrac{\mu}{r}$ = constant.

## 2. Finding $\varepsilon$
Angular momentum is conserved, and at the apses $\mathbf r\perp\mathbf V$:

$$
r_pV_p = r_aV_a\ \Rightarrow\ \frac{V_p^2}{V_a^2} = \frac{r_a^2}{r_p^2} = \frac{\varepsilon+\mu/r_p}{\varepsilon+\mu/r_a}
$$

Solving: $\varepsilon = -\dfrac{\mu}{r_a+r_p} = -\dfrac{\mu}{2a}$. This holds for **all conics**: $\varepsilon<0$ bound, $=0$ parabolic, $>0$ hyperbolic ($a<0$). Full algebra in [[SESA2024 Workbook Ch5 - Mission Analysis Solutions|workbook Ch5 Q2]].

## 3. Special cases
| Case | Condition | Speed |
|---|---|---|
| Circular | $r = a$ | $V_c = \sqrt{\mu/r}$ |
| Escape (parabolic) | $a\to\infty$ | $V_{esc} = \sqrt{2\mu/r} = \sqrt2\,V_c$ |
| Perigee | $r = a(1-e)$ | $V_p = \sqrt{\dfrac{\mu}{a}\dfrac{1+e}{1-e}}$ |
| Apogee | $r = a(1+e)$ | $V_a = \sqrt{\dfrac{\mu}{a}\dfrac{1-e}{1+e}}$ |
| Ellipse in terms of $r_p$, $r_a$ | – | $V_p = \sqrt{\dfrac{2\mu r_a}{r_p(r_a+r_p)}}$ |

## 4. Worked example (L10): 200 km circle and a 200 × 40 000 km ellipse
$R_E$ = 6378 km, $\mu$ = 398 600 km³/s².

**(i) Circular at 200 km**: $V_1 = \sqrt{398\,600/6578}$ = **7.784 km/s**.

**(ii) Ellipse**: $r_p$ = 6578 and $r_a$ = 46 378 km, so $a$ = 26 478 km ($e$ = 0.752).

$$
V_p = \sqrt{\mu\Big(\frac{2}{6578}-\frac{1}{26\,478}\Big)} = \mathbf{10.302\ km/s},\qquad V_a = \sqrt{\mu\Big(\frac{2}{46\,378}-\frac{1}{26\,478}\Big)} = \mathbf{1.461\ km/s}
$$

Check: $r_pV_p = 6578(10.302) = 67\,767 = r_aV_a = 46\,378(1.461)$ ✔.

![[ast_visviva_speed.png|760]]

## 5. Quiz insight: which satellite is fastest?
- For circles $V\propto r^{-1/2}$: the **lower** satellite is faster.
- An ellipse with the same perigee radius $r_C$ as a circle, but $a_C\approx2r_C$:

$$
\frac{V_C^2}{2}-\frac{\mu}{r_C} = -\frac{\mu}{4r_C}\ \Rightarrow\ V_C = \sqrt{\frac{3\mu}{2r_C}} = 1.22\,V_{circ}
$$

- **At a common point, the larger orbit (larger $a$, higher energy) always has the higher speed.** This is why a tangential burn *raises* the opposite side of the orbit.

## 6. Using the energy equation to identify an orbit
From one measured pair $(r, V)$ you get $a$. With one apsis you also get $e$. See workbook Q4: an object at 1000 km apogee moving at 5.589 km/s has $a$ = 5189 km and $r_p$ = 3000 km < $R_E$, so it is a **ballistic missile**.

> [!example] Exam uses
> - 2023/24 B1: Starship at apogee 148 km, $V$ = 6760 m/s, gives $a$ = 5213 km, $e$ = 0.252, perigee **inside** the Earth (a suborbital failure).
> - 2024/25 B1: the asteroid's speed at aphelion, and the new period after the momentum kick.
> - 2021/22 B1: Apollo 9 de-orbit burn.

## 7. Link to the true anomaly
With $a$ and $e$ known, the orbit equation gives $\theta$ at any radius:

$$
\cos\theta = \frac{1}{e}\left[\frac{a(1-e^2)}{r}-1\right]
$$

Choose $\theta$ or $360^\circ-\theta$ from the direction of travel: inbound towards perigee means $\theta>180^\circ$. (Used in 2022/23 B1(v) and 2023/24 B1(ii).)

## Links
- Parent: [[SESA2024 Astronautics Hub]] · Previous: [[SESA2024 03 - Orbital Elements and Conic Sections]] · Next: [[SESA2024 05 - Orbital Transfers and the Hohmann Transfer]]
- Formula sheet: [[SESA2024 Formula Sheet]]

## Year 1 foundation
- Gravitational potential energy $-GMm/r$ ([[FEEG1002 D3 - Work, Energy and Power]]). The perigee/apogee example combining energy and angular momentum is in [[FEEG1002 D5 - Angular Impulse and Momentum]].

## Sources
- Chapter 5 Lecture 9 (orbital energy) and Lecture 10 (worked example)
