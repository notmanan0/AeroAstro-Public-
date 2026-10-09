---
title: "FEEG1002 Dynamics Tutorial 9 - Work and Energy for Rigid Bodies Solutions"
module: "FEEG1002 Mechanics, Materials and Structures"
type: tutorial
stream: "Part D: Dynamics"
tags: [feeg1002, tutorial-solutions, dynamics, rigid-body, work-energy, rolling, instantaneous-centre]
sheet: "Dynamics Tutorial sheet 9 (work and energy for rigid bodies)"
theory_notes: ["[[FEEG1002 D9 - Work and Energy for Rigid Bodies]]"]
key_concepts: ["[[Kinetic Energy of a Rigid Body]]", "[[Instantaneous Centre of Rotation]]", "[[Rolling Without Slip]]", "[[Work-Energy Principle]]"]
status: complete
sources: ["02 - Sources/Dynamics/Tutorials/Tutorial Sheet 09 - Work and Energy for Rigid Bodies.pdf"]
---

# FEEG1002 Dynamics Tutorial 9 - Work and Energy for Rigid Bodies Solutions

> [!abstract] Sheet Info
> Four problems that combine $KE = \tfrac12I_{IC}\omega^2$ with correctly identifying **which forces do work**. Every printed answer is reproduced ✔.
> - Q3 is the key one: A is **not** the instantaneous centre.

## Theory Links
- [[FEEG1002 D9 - Work and Energy for Rigid Bodies]] · [[Kinetic Energy of a Rigid Body]] · [[Instantaneous Centre of Rotation]] · [[Rolling Without Slip]]

---

## Q1: 30 kg rod ($L = 1.5$ m) pinned at O; spring $k = 80$ N/m from A to a support 2 m along the ceiling; released from horizontal
- Spring length at $\theta = 0$: $2 - 1.5 = 0.5$ m, and it is unstretched there.
- At $\theta = 30°$, A = $(1.299, -0.75)$ m, so the spring length is $\sqrt{0.701^2 + 0.75^2} = 1.027$ m and the stretch is 0.527 m.
- Energy, with the pin doing no work and $I_O = \tfrac13mL^2 = 22.5$ kg m²:

$$
\underbrace{mg\tfrac L2\sin30°}_{110.4\ \text{J}} - \underbrace{\tfrac12k(0.527)^2}_{11.1\ \text{J}} = \tfrac12I_O\omega_2^2\ \Rightarrow\ \omega_2 = \mathbf{2.97}\ \text{rad/s}\ ✔
$$

## Q2: 75 kg spool ($k_O = 0.675$ m, $R_i = 0.6$ m, $R_e = 0.9$ m), $P = 200$ N on a cord leaving the top of the core; rolls without slip
- **IC** = contact point A. The cord's tangent point is $R_e + R_i = 1.5$ m from A, so it moves $1.5/0.9 = 5/3$ times as far as O. For $s_O = 3$ m, the cord end moves 5 m and $U_P = 1000$ J.
- The friction at A does no work (rolling without slip). The normal force and weight do no work either.
- $I_A = m(k_O^2 + R_e^2) = 94.9$ kg m², so $1000 = \tfrac12(94.9)\omega^2$ and **$\omega = 4.59$ rad/s** ✔

## Q3: 60 kg spool ($k_G = 0.3$ m, $R_i = 0.3$ m, $R_e = 0.5$ m) on a 30° incline, cord from the core anchored up-slope, released from rest; target $\omega_2 = 6$ rad/s
- **IC**: the cord is fixed and inextensible, so its **tangent point on the core** is at rest. The IC is on the incline side of G, a distance $R_i$ from it. Hence $v_G = \omega R_i$.
- The rim contact A is $R_e - R_i = 0.2$ m from the IC. So A **slides** at $v_A = \tfrac23v_G$, and the slip distance is $\tfrac23d$ when G descends a distance $d$.
- **(a) Smooth incline**:

$$
mgd\sin30° = \tfrac12m(k_G^2 + R_i^2)\omega_2^2\ \Rightarrow\ d = \frac{0.5(0.18)(36)}{9.81(0.5)} = \mathbf{0.661}\ \text{m}\ ✔
$$

- **(b) $\mu_k = 0.2$ at A**: $N = mg\cos30° = 510$ N and friction $0.2N = 102$ N does work $-102\times\tfrac23d$:

$$
(294.3 - 68.0)d = 194.4\ \Rightarrow\ d = \mathbf{0.859}\ \text{m}\ ✔
$$

Assuming A were the IC would get both parts wrong. The cord constraint, not the ground, fixes the IC.

![[d_t9_spools_ic.png|880]]

## Q4: Diver (75 kg, $k_G = 0.36$ m, $r_G = 0.45$ m) rotates about the toes from upright to horizontal, then falls 10 m
- **On the board**: G drops by $r_G$. Energy about the fixed point A:

$$
mgr_G = \tfrac12m(k_G^2 + r_G^2)\omega^2\ \Rightarrow\ \omega = 5.16\ \text{rad/s},\quad v_G = \omega r_G = 2.32\ \text{m/s (down)}
$$

- **In the air**: only gravity acts, through G, so there is no moment and **$\omega$ stays constant**. G falls 10 m: $10 = 2.32t + 4.905t^2$, so $t = 1.21$ s.
- **Revolutions**: $0.25$ (on the board) $+\ \omega t/2\pi = 0.25 + 0.99$ = **1.24 rev** ✔

This is the lecture's point about translational vs rotational energy: in flight, gravitational PE feeds only the translational part of the KE.

![[d_t9_q4_diver.png|880]]

## Sources
- Dynamics Tutorial sheet 9 (answers printed on the sheet)
