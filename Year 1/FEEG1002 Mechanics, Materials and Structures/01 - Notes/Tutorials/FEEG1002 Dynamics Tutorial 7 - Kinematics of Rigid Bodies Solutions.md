---
title: "FEEG1002 Dynamics Tutorial 7 - Kinematics of Rigid Bodies Solutions"
module: "FEEG1002 Mechanics, Materials and Structures"
type: tutorial
stream: "Part D: Dynamics"
tags: [feeg1002, tutorial-solutions, dynamics, rigid-body, kinematics, rolling, mechanisms]
sheet: "Dynamics Problem sheet 7 (kinematics of rigid bodies)"
theory_notes: ["[[FEEG1002 D7 - Kinematics of Rigid Bodies]]"]
key_concepts: ["[[Relative Velocity Equation for Rigid Bodies]]", "[[Instantaneous Centre of Rotation]]", "[[Rolling Without Slip]]"]
status: complete
sources: ["02 - Sources/Dynamics/Tutorials/Tutorial Sheet 07 - Kinematics of Rigid Bodies.pdf"]
---

# FEEG1002 Dynamics Tutorial 7 - Kinematics of Rigid Bodies Solutions

> [!abstract] Sheet Info
> Five problems:
> - fixed-axis rotation;
> - a rolling wheel;
> - absolute motion analysis (hydraulic window);
> - relative velocity (crank–slider).
>
> Every printed answer is reproduced ✔. The rolling-wheel accelerations differ slightly in the last digit: the sheet uses $\alpha = 3.14$, but the printed answers use exact $\pi$.

## Theory Links
- [[FEEG1002 D7 - Kinematics of Rigid Bodies]] · [[Relative Velocity Equation for Rigid Bodies]] · [[Instantaneous Centre of Rotation]] · [[Rolling Without Slip]]

---

## Q1: Cam, $\theta = t^3 - 4t^2 - 3t + 10$
$\omega = 3t^2 - 8t - 3$ and $\alpha = 6t - 8$.

| $t$ | $\theta$ (rad) | $\omega$ (rad/s) | $\alpha$ (rad/s²) |
|---|---|---|---|
| 0 | 10 | −3 | −8 ✔ |
| 2 s | −4 | −7 | 4 ✔ |
| 3 s ($\omega = 0$) | −8 | 0 | 10 ✔ |

The root of $3t^2 - 8t - 3 = 0$ with $t > 0$ is $t = 3$ s ✔.

## Q2: Plate from rest with constant $\alpha$; point B at radius $r$
- $\omega = \alpha t$, so $a_t = r\alpha$ and $a_n = r\omega^2 = r\alpha^2t^2$.
- $a = r\alpha\sqrt{1 + \alpha^2t^4}$ ✔
- The angle to the line AB (the normal direction) is $\gamma = \tan^{-1}(a_t/a_n) = \tan^{-1}\!\left(\dfrac1{\alpha t^2}\right)$ ✔
- As $t$ grows, the acceleration swings round to point at the centre.

## Q3: Wheel rolling without slip, $R = 0.5$ m, $\alpha = 3.14$ rad/s² clockwise, from rest; $t = 2$ s
At $t = 2$ s, $\omega = \alpha t = 6.28$ rad/s. A is the contact point and IC, B the centre, P the right-hand end of the horizontal diameter.
- **(a)** Every velocity is perpendicular to the line to A, with magnitude $\omega\times$ (distance to A):
  - **$v_A = 0$**;
  - **$v_B = \omega R = 3.14$ m/s** →;
  - **$v_P = \omega R\sqrt2 = 4.44$ m/s** at 45° below horizontal ✔.
- **(b)** The centre moves in a straight line, so $a_B = R\alpha$ = **1.57 m/s²** → ✔.
- **(c)** P traces a **cycloid**. By 2 s the wheel has turned $\tfrac12\alpha t^2 = 2\pi$: exactly one revolution, advancing $2\pi R = 3.14$ m. P dips to the ground once (cusp) and returns to wheel-centre height.
- **(d)** $\mathbf a_P = \mathbf a_B + \boldsymbol\alpha\times\mathbf r_{P/B} - \omega^2\mathbf r_{P/B}$:
  - Contact point: $\mathbf a_A = \omega^2R$ **upwards** = **19.7 m/s²**, even though $v_A = 0$.
  - $\mathbf a_P = (1.57 - 19.72,\,-1.57)$ m/s², so **18.2 m/s²** ✔ (19.74 and 18.24 with exact $\pi$).

![[d_t7_q3_rolling_wheel.png|920]]

## Q4: Hydraulic window, $l = 1$ m, $b = 2$ m, $\dot s = 0.5$ m/s constant, at $\theta = 30°$
- **Cosine rule**: $s^2 = b^2 + l^2 - 2bl\cos\theta$, so $s(30°) = 1.239$ m.
- **Differentiate once**: $2s\dot s = 2bl\sin\theta\,\dot\theta$, so $\dot\theta = \dfrac{s\dot s}{bl\sin\theta}$ = **0.620 rad/s** ✔
- **Differentiate again**: $\dot s^2 + s\ddot s = bl(\cos\theta\,\dot\theta^2 + \sin\theta\,\ddot\theta)$ with $\ddot s = 0$, so $\ddot\theta$ = **−0.415 rad/s²** ✔

**Design comment**:
- At $\theta\to0$, $\sin\theta\to0$ and $\dot\theta\to\infty$. The cylinder lies along the window, so it has **no leverage** to start opening it: the required force is unbounded.
- Also, $s$ runs only from 1 m to $\sqrt5 = 2.24$ m, so the cylinder needs 1.24 m of stroke from a closed length of 1 m.
- **Fixes**: mount A off the window's line (horizontal offset), or attach B lower down.

![[d_t7_q4_window.png|700]]

## Q5: Crank–slider, $r = 60$ mm, $l = 160$ mm, 1000 rpm anticlockwise
$\omega = 104.7$ rad/s and $v_B = r\omega = 6.28$ m/s perpendicular to AB. Use $\mathbf v_C = \mathbf v_B + \boldsymbol\omega_{CB}\times\mathbf r_{C/B}$ with $\mathbf v_C$ horizontal.

| $\theta$ | Geometry | $\boldsymbol\omega_{CB}$ | $\mathbf v_C$ |
|---|---|---|---|
| 0° | B on the line AC; $v_B$ vertical | $-r\omega/l$ = **−39.3k rad/s** | **0** (dead centre) ✔ |
| 90° | B at the top; $\mathbf v_B = -6.28\mathbf i$ | **0** (rod translates instantaneously) | **−6.28i m/s** ✔ |
| 180° | B on the line, other side | **+39.3k rad/s** | **0** ✔ |

At 90° the rod's two end velocities are parallel, so the IC is at infinity and the rod translates.

![[d_t7_q5_crank_slider.png|760]]

## Sources
- Dynamics Problem sheet 7 (answers printed on the sheet)
