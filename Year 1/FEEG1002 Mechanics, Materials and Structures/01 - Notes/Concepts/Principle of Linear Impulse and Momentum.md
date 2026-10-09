---
title: "Principle of Linear Impulse and Momentum"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part D: Dynamics"
aliases: ["impulse", "linear momentum", "conservation of linear momentum", "impulse-momentum"]
tags: [feeg1002, concept, dynamics, momentum]
status: complete
parent_lectures: ["[[FEEG1002 D4 - Linear Impulse and Momentum]]"]
related_concepts: ["[[Coefficient of Restitution]]", "[[Principle of Angular Impulse and Momentum]]", "[[Newton's Laws of Motion]]"]
sources: []
---

# Principle of Linear Impulse and Momentum

## Definition

> [!note] Definition
>
> $$m\mathbf v_1 + \sum\int_{t_1}^{t_2}\mathbf F\,dt = m\mathbf v_2,\qquad \mathbf L = m\mathbf v,\quad \mathbf I = \int\mathbf F\,dt\ [\text{N s}]$$
>
> For a system, $m\mathbf v_{G1} + \sum\int\mathbf F_{ext}\,dt = m\mathbf v_{G2}$. With no external impulse, total momentum is conserved.

## Explanation

- Use it for problems involving **force, time and velocity**.
- The impulse is the area under $F(t)$. The **average force** has equal area; the **peak** force needs the pulse shape.
- **Impulsive forces** (contact, explosions) dominate short events. Weight is non-impulsive over milliseconds but not over seconds.
- Conservation can be applied **component by component**: e.g. horizontally for a cannon free to roll, but not vertically, where the ground pushes.
- A "rigid ground" supplies an external impulse, so momentum is not conserved normal to it.

## Examples

- **Tutorial 4 Q2**: half-sine pulse, $I = 2At_0/\pi = 0.732$ N s, so the ball leaves at 5.2 m/s.
- **Tutorial 4 Q4**: a cannon on wheels recoils at 0.48 m/s.

![[d_impulse_force_time.png|760]]

## Related

- Topic notes: [[FEEG1002 D4 - Linear Impulse and Momentum]]
- Concepts: [[Coefficient of Restitution]] · [[Principle of Angular Impulse and Momentum]] · [[Newton's Laws of Motion]]
- Year 2: Rocket equation, [[Tsiolkovsky Rocket Equation]] · control-volume momentum, [[SESA1016 T12 - Conservation of Momentum]] and [[Momentum Flux]] · impulse-excited vibration, [[FEEG1002 D6 - Single Degree of Freedom Vibration]]

## Sources

- Dynamics Lecture 4.1–4.2
