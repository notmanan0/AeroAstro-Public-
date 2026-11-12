---
title: "Coefficient of Restitution"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part D: Dynamics"
aliases: ["restitution", "elastic impact", "plastic impact", "e", "central impact", "oblique impact", "Newton's law of restitution", "coefficient of rebound"]
tags: [feeg1002, concept, dynamics, momentum, impact]
status: complete
date: 2026-11-05
parent_lectures: ["[[FEEG1002 D4 - Linear Impulse and Momentum]]"]
related_concepts: ["[[Principle of Linear Impulse and Momentum]]", "[[Work-Energy Principle]]"]
sources: ["02 - Sources/Dynamics/Lectures/Lecture 04 - Linear Impulse and Momentum.pdf"]
---

# Coefficient of Restitution

The coefficient of restitution $e$ of a central impact is the ratio of the relative velocity of separation to the relative velocity of approach of the two bodies, measured along the line of impact with all velocities positive in the same direction.

$$
e=\frac{v_{B2}-v_{A2}}{v_{A1}-v_{B1}}
$$

It is needed because conservation of momentum for the colliding pair, $m_Av_{A1}+m_Bv_{B1}=m_Av_{A2}+m_Bv_{B2}$, is one equation with two unknown final velocities. The coefficient comes from experiment: it depends on the materials, the shapes and sizes and the impact speed, and lies between 0 and 1. At $e=1$ the impact is **elastic** and kinetic energy is conserved; at $e=0$ it is **plastic**, the bodies move off together and the energy lost is the greatest possible.

Substituting $v_{B2}=v_{A2}+e(v_{A1}-v_{B1})$ into the momentum equation gives

$$
v_{A2}=\frac{(m_A-em_B)v_{A1}+m_B(1+e)v_{B1}}{m_A+m_B},\qquad v_{B2}=\frac{m_A(1+e)v_{A1}+(m_B-em_A)v_{B1}}{m_A+m_B}
$$

which cover both limits. The kinetic energy lost is $\tfrac12\,\frac{m_Am_B}{m_A+m_B}(1-e^2)(v_{A1}-v_{B1})^2$, a fraction $1-e^2$ of the energy of the relative motion. With equal masses and $e=1$ the bodies swap velocities, which is how Newton's cradle works.

In the Galilean cannon a light ball dropped on a heavy one from $h_0$ leaves at $v_{B3}=(1+e)v_{A2}-ev_{B2}$ in the limit of a vanishing mass ratio. With the same $e$ for the ground bounce and the ball-on-ball collision, $v_{B3}=e(e+2)\sqrt{2gh_0}$ and the top ball rises to $h_4=[e(e+2)]^2h_0$: $9h_0$ for $e=1$ and $1.56h_0$ for $e=0.5$.

The common slip is a sign error: both differences must be taken with velocities positive in one stated direction, so that a rebound enters as a negative velocity. For an oblique impact $e$ applies only to the components along the line of impact, while each body keeps its own momentum along the plane of contact (not assessed in this module).

![[d_restitution_sweep.png|760]]

## Related

- [[FEEG1002 D4 - Linear Impulse and Momentum#Coefficient of restitution|definition in D4]] · [[FEEG1002 D4 - Linear Impulse and Momentum#Velocities after a central impact|velocities after impact]] · [[FEEG1002 D4 - Linear Impulse and Momentum#Energy lost in an impact|energy lost]] · [[FEEG1002 D4 - Linear Impulse and Momentum#Collisions of a 2m and an m particle|2m and m example]] · [[FEEG1002 D4 - Linear Impulse and Momentum#Galilean cannon|Galilean cannon]] · [[FEEG1002 D4 - Linear Impulse and Momentum#3. Oblique impact|oblique impact]]
- [[Principle of Linear Impulse and Momentum]] · [[Work-Energy Principle]]
- Year 2: energy absorbed in impact and dynamic toughness in [[SESA2028 M1 - Fracture, Toughness and Fracture Mechanics]]
