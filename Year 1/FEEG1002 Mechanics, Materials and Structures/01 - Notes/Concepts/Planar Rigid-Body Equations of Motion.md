---
title: "Planar Rigid-Body Equations of Motion"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part D: Dynamics"
aliases: ["sum M_G = I_G alpha", "rigid body kinetics", "sum M_O = I_O alpha", "kinetic diagram rigid body"]
tags: [feeg1002, concept, dynamics, rigid-body, kinetics]
status: complete
parent_lectures: ["[[FEEG1002 D8 - Kinetics of Rigid Bodies]]"]
related_concepts: ["[[Mass Moment of Inertia and Radius of Gyration]]", "[[Newton's Laws of Motion]]", "[[Principle of Angular Impulse and Momentum]]"]
sources: []
---

# Planar Rigid-Body Equations of Motion

## Definition

> [!note] Definition
>
> $$\sum F_x = ma_{Gx},\qquad \sum F_y = ma_{Gy},\qquad \sum M_G = I_G\alpha\quad\text{or}\quad\sum M_P = (\bar r\times m\mathbf a_G)_P + I_G\alpha$$
>
> For rotation about a fixed axis O: $\sum F_n = mr_G\omega^2$, $\sum F_t = mr_G\alpha$ and $\sum M_O = I_O\alpha$.

## Explanation

- The centre of mass moves as if all the external forces acted on a particle there.
- Taking moments about a point P where unknown reactions act eliminates them. But then include the moment of $m\mathbf a_G$ from the kinetic diagram.
- **Translation**: $\alpha = 0$, so $\sum M_G = 0$.
- **Tipping and slip**: make the simplest assumption (no tipping, no slip), solve, then **verify** ($N\ge0$, $F\le\mu_sN$).
- **Released from rest**: $\omega = 0$ initially, so the normal pin reaction $mr_G\omega^2$ vanishes.

## Examples

- **Handcart** (Lecture 8): $N_A = 765$ N and $N_B = 1240$ N.
- **Released rod**: $\alpha = 16.35$ rad/s² and $R_t = 110.4$ N.
- **Hoisting drums** (Tutorial 8 Q4): $a = 1.03$ m/s², $T = 3252$ N.

![[d_pinned_rod_released.png|620]]

## Related

- Topic notes: [[FEEG1002 D8 - Kinetics of Rigid Bodies]]
- Concepts: [[Mass Moment of Inertia and Radius of Gyration]] · [[Newton's Laws of Motion]] · [[Principle of Angular Impulse and Momentum]]
- Year 2: Euler's rigid-body equations, the pitch equation $M = I_{yy}\dot q$ in [[SESA2027 A1 - Dynamic Systems and Aircraft Equations of Motion]] · attitude dynamics in [[SESA2024 06 - Attitude Control]]

## Sources

- Dynamics Lecture 8.2
