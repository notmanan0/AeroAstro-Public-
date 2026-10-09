---
title: "FEEG1002 D4 - Linear Impulse and Momentum"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part D: Dynamics"
order: 4
tags: [feeg1002, dynamics, impulse, momentum, impact, restitution]
aliases: ["Dynamics Lecture 4", "Impulse and momentum", "Impacts", "Coefficient of restitution", "Galilean cannon"]
date: 2026-09-25
status: complete
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: ["[[FEEG1002 D3 - Work, Energy and Power]]"]
next_topics: ["[[FEEG1002 D5 - Angular Impulse and Momentum]]"]
key_concepts: ["[[Principle of Linear Impulse and Momentum]]", "[[Coefficient of Restitution]]"]
tutorial_sheets: ["[[FEEG1002 Dynamics Tutorial 4 - Linear Impulse and Momentum Solutions]]"]
sources: ["02 - Sources/Dynamics/Lectures/Lecture 04 - Linear Impulse and Momentum.pdf"]
---

# FEEG1002 D4 - Linear Impulse and Momentum

> [!abstract] Summary
> Integrating $\sum\mathbf F = m\,d\mathbf v/dt$ **over time** gives
>
> $$m\mathbf v_1 + \sum\int_{t_1}^{t_2}\mathbf F\,dt = m\mathbf v_2$$
>
> Initial momentum plus impulse equals final momentum. This is the natural tool when a problem involves **force, time and velocity**, especially short, violent **impulsive** forces during impacts.
> - For a system with no **external** impulse, total momentum is **conserved**.
> - Collisions need one extra piece of physics, the **coefficient of restitution** $e$: $e = 1$ elastic, $e = 0$ plastic.

## Key Concepts
- [[Principle of Linear Impulse and Momentum]] · [[Coefficient of Restitution]] · [[Work-Energy Principle]]

---

## 1. The principle (L4.1)
**Linear momentum** is $\mathbf L = m\mathbf v$, a vector along $\mathbf v$ with units kg m/s = N s. Newton's second law reads $\sum\mathbf F = \dot{\mathbf L}$.

**Linear impulse** is $\mathbf I = \int\mathbf F\,dt$ (N s): the area under the force–time curve. An **average force** is defined by equal area, $F_{avg}(t_2 - t_1) = \int\mathbf F\,dt$.

**Procedure**:
- Draw three diagrams: initial momentum + impulse diagram (an FBD with durations) = final momentum.
- Resolve into scalar components, $mv_{x1} + \sum\int F_x\,dt = mv_{x2}$.
- Forces that vary in time must be **integrated**.

![[d_impulse_force_time.png|920]]

> [!example] Tennis ball (L4): $m = 0.06$ kg, $v_1 = 6$ m/s down, trapezoidal pulse, $F_m = 160$ N
> - Impulse: $I = F_m(\Delta t_2 + \Delta t_1) = 160(0.004) = 0.64$ N s.
> - Taking up as positive, $-mv_1 + I = mv_2$ gives $v_2 = 4.67$ m/s up.
> - Average force: $F_{avg} = m(v_1 + v_2)/\Delta t = 128$ N.

**Impulsive vs non-impulsive forces**:
- During a collision lasting milliseconds, weight contributes $\int mg\,dt = mg\Delta t\approx0$ and is neglected.
- Over **seconds** it is not negligible. An example is a block pushed up a rough slope for 3 s: $3F - 3mg\sin\theta - 3\mu_kmg\cos\theta = mv_2$.

> [!warning] A rigid ground has "infinite mass"
> The ground's impulse on a bouncing ball is **external** to the ball. So you **cannot** use momentum conservation perpendicular to the ground. You need the impulse itself, or $e$.

## 2. Systems of particles and conservation (L4.1–4.2)
Summing over all particles, the internal forces cancel in pairs:

$$
\sum m_i\mathbf v_{i1} + \sum\int\mathbf F_i\,dt = \sum m_i\mathbf v_{i2},\qquad m\mathbf v_{G1} + \sum\int\mathbf F_{ext}\,dt = m\mathbf v_{G2}
$$

- Only the **external** impulses and the velocity of the **centre of mass** appear.
- With zero external impulse, $\sum m_i\mathbf v_{i1} = \sum m_i\mathbf v_{i2}$: **conservation of linear momentum**.

## 3. Central impacts and restitution (L4.2)
- **Line of impact**: through the two mass centres.
- **Plane of contact**: perpendicular to the line of impact.
- **Central impact**: the velocities lie along the line of impact.

During the impact the bodies deform then recover. The internal impulses cancel, so

$$
m_Av_{A1} + m_Bv_{B1} = m_Av_{A2} + m_Bv_{B2}
$$

This is one equation for two unknowns. The **coefficient of restitution** supplies the second:

$$
e = \frac{v_{B2} - v_{A2}}{v_{A1} - v_{B1}} = \frac{\text{relative speed of separation}}{\text{relative speed of approach}}
$$

| Case | Extra equation | Result |
|---|---|---|
| Elastic, $e = 1$ | KE conserved | $v_{A2} = \frac{m_A - m_B}{m_A + m_B}v_{A1} + \frac{2m_B}{m_A + m_B}v_{B1}$, etc. |
| Plastic, $e = 0$ | common velocity | $v_2 = \frac{m_Av_{A1} + m_Bv_{B1}}{m_A + m_B}$ |
| General $e$ | the definition of $e$ | $v_{A2} = \frac{m_A - em_B}{m_A + m_B}v_{A1} + \frac{m_B(1 + e)}{m_A + m_B}v_{B1}$<br>$v_{B2} = \frac{m_A(1 + e)}{m_A + m_B}v_{A1} + \frac{m_B - em_A}{m_A + m_B}v_{B1}$ |

- The elastic-case energy equation is quadratic. Its second root is the particles "passing through each other"; discard it.
- In practice $e$ comes from experiment and depends on speed, size and shape.

![[d_restitution_sweep.png|920]]

The lecture example uses $m_A = 2m$, $m_B = m$ and 1 m/s approach speeds:

| $e$ | $v_{A2}$ | $v_{B2}$ |
|---|---|---|
| 1 | $-1/3$ | $5/3$ |
| 0 | $1/3$ | $1/3$ |
| 0.4 | $1/15$ | $13/15$ |

The fraction of KE lost rises from 0 at $e = 1$ to a maximum at $e = 0$. Momentum is conserved throughout.

**Newton's cradle**: with equal masses and $e = 1$, each ball passes its momentum on and stops.

### Galilean cannon (L4 in-class experiment)
A small ball B sits on a big ball A and both are dropped from $h_0$. A rebounds from the ground with $v_{A2} = e\sqrt{2gh_0}$ and meets B still falling at $\sqrt{2gh_0}$. With $m_B\ll m_A$:

$$
v_{B3} = (1 + e)v_{A2} - ev_{B2} = e(e + 2)\sqrt{2gh_0}\qquad\Rightarrow\qquad h_4 = [e(e + 2)]^2h_0
$$

- For $e = 1$: **$h_4 = 9h_0$**.

> [!warning] Slide 37 error: $e = 0.5$ gives $h_4 = 1.56h_0$, not $6.25h_0$
> The slide writes "$h_4 = [e(e+2)^2]h_0$" and quotes $6.25h_0$ for $e = 0.5$. But squaring $v_{B3} = e(e + 2)\sqrt{2gh_0}$ gives $[e(e+2)]^2 = (0.5\times2.5)^2 = $ **1.56**. The slide's 6.25 is just $(e + 2)^2$.
>
> Physically, a lossy bounce ($e = 0.5$ at both contacts) cannot give 6× the drop height when a perfect bounce gives 9×.

![[d_galilean_cannon.png|720]]

For finite mass ratios, $v_{B3} = [e(1+e) + (e - m_B/m_A)]\sqrt{2gh_0}/(1 + m_B/m_A)$. At $m_B = 3m_A$ with $e = 1$ the top ball does not rise at all. That answers the lecture's "what happens when $m_B = 3m_A$?".

## 4. Oblique impacts (L4.3, optional, not assessed)
**Smooth ground**:
- Momentum parallel to the plane of contact is conserved: $v_{2x} = v_{1x}$.
- $e$ acts on the normal components: $v_{2y} = ev_{1y}$.

**Rough ground** adds a tangential impulse, so extra information is needed.

**Two smooth particles** give four equations:
- total momentum along the line of impact;
- each particle's momentum along the plane of contact (two equations);
- $e$ along the line of impact.

Tutorial 4 Q7 (billiards) uses this:

![[d_t4_q7_billiards.png|560]]

## Year 2 bridge
- **Rockets**: throwing bricks off a wagon (Tutorial 4 Q6) is a discrete rocket. Making the mass loss continuous gives $\Delta v = v_e\ln(m_0/m_f)$, the [[Tsiolkovsky Rocket Equation]] ([[SESA2023 W10 - Rocket Performance, Staging and Power Cycles]], [[SESA2024 07 - Spacecraft Propulsion]]).
- **Fluid momentum**: $\sum F = \dot m(v_2 - v_1)$ for a control volume ([[SESA1016 T12 - Conservation of Momentum]], [[Momentum Flux]]) is this principle applied to a flowing stream. It is how thrust is computed.
- **Impact loading in structures**: an impulse applied to an elastic structure produces free vibration. The pigeon striking the speed camera in [[FEEG1002 D6 - Single Degree of Freedom Vibration]] is impulse–momentum ($J = m\dot x_0$) followed by vibration. Collisions are also the typical source of the dynamic stresses and damage in [[SESA2028 M1 - Fracture, Toughness and Fracture Mechanics]].

## Links
- Previous: [[FEEG1002 D3 - Work, Energy and Power]] · Next: [[FEEG1002 D5 - Angular Impulse and Momentum]]
- Worked problems: [[FEEG1002 Dynamics Tutorial 4 - Linear Impulse and Momentum Solutions]]

## Sources
- Dynamics Lecture 4: 4.1 principle of linear impulse and momentum; 4.2 conservation and central impacts (Newton's cradle, Galilean cannon); 4.3 oblique impacts (optional)
