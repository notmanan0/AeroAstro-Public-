---
title: "FEEG1002 Dynamics Tutorial 2 - Curvilinear Motion Solutions"
module: "FEEG1002 Mechanics, Materials and Structures"
type: tutorial
stream: "Part D: Dynamics"
tags: [feeg1002, tutorial-solutions, dynamics, projectiles, normal-tangential, banked-curve, relative-motion]
sheet: "Dynamics Problem sheet 2 (curvilinear motion)"
theory_notes: ["[[FEEG1002 D2 - Curvilinear Motion]]"]
key_concepts: ["[[Projectile Motion]]", "[[Normal and Tangential Coordinates]]", "[[Coulomb Friction]]"]
status: complete
sources: ["02 - Sources/Dynamics/Tutorials/Tutorial Sheet 02 - Curvilinear Motion.pdf"]
---

# FEEG1002 Dynamics Tutorial 2 - Curvilinear Motion Solutions

> [!abstract] Sheet Info
> 11 problems:
> - projectiles;
> - $n$–$t$ kinematics and kinetics (banked curves, rotor ride, swing, collar on a curved rod);
> - relative motion (mine car, aircraft, cars).
>
> **No printed answers.** The geometry was read from the sheet's figures. Every value was worked and checked numerically, and several match the textbook versions of these problems (Hibbeler/Meriam).

## Theory Links
- [[FEEG1002 D2 - Curvilinear Motion]] · [[Projectile Motion]] · [[Normal and Tangential Coordinates]]

---

## Q1: Projectile, $v_A = 150$ m/s on a 3-4-5 slope, landing 150 m below A
- Components: $v_x = 120$ m/s, $v_y = 90$ m/s.
- **Time of flight**: $-150 = 90t - 4.905t^2$, so **$t_{AB} = 19.89$ s**.
- **Range**: $R = 120t_{AB}$ = **2386 m**.
- **Trajectory**: $y = 0.75x - \dfrac{g}{2(120^2)}x^2 = 0.75x - 3.41\times10^{-4}x^2$.
- **Maximum height**: $v_y = 0$ at $t = 9.17$ s, giving $h = 90^2/2g$ = **413 m above A** (563 m above the ground).

![[d_t2_q1_projectile.png|860]]

## Q2: Circle of radius 0.5 m at 20 rpm (horizontal plane)
- **Angular velocity**: $\dot\theta = 20\times2\pi/60$ = **2.09 rad/s**.
- **$n$–$t$**: $s = r\theta$, $v = r\dot\theta$ = **1.05 m/s** along $\mathbf u_t$. $a_t = 0$ and $a_n = r\dot\theta^2$ = **2.19 m/s²** towards the centre.
- **Cartesian**, with $x = r\cos\theta$ and $y = r\sin\theta$, $\theta = \omega t$:
  - velocity $\dot x = -r\omega\sin\theta$, $\dot y = r\omega\cos\theta$;
  - acceleration $\ddot x = -r\omega^2\cos\theta$, $\ddot y = -r\omega^2\sin\theta$, i.e. $\mathbf a = -\omega^2\mathbf r$.
  - Same magnitudes, different bookkeeping.

## Q3: $\ddot\theta = 6t$ (0–1 s), then 6 rad/s² (1–2 s), from rest, $r = 0.5$ m
- **Angular velocity**: $\omega(1) = 3t^2|_1 = 3$ rad/s, then $\omega(2) = 3 + 6(1)$ = **9 rad/s**.
- **Angle**: $\theta(1) = t^3 = 1$ rad; the next second adds $3(1) + 3(1)^2 = 6$ rad. Total 7 rad, so the **distance is $r\theta$ = 3.5 m**.

## Q4: Rocket with $a_h = 3$ m/s² (thrust), $g = 9.3$ m/s², $v = 10^4$ km/h at 30° below horizontal
Resolve the two acceleration components onto $t$ (along the velocity) and $n$ (towards C):
- **(i)** $a_t = 3\cos30° + 9.3\sin30°$ = **7.25 m/s²** and $a_n = -3\sin30° + 9.3\cos30°$ = **6.55 m/s²**. So $\mathbf a = 7.25\mathbf u_t + 6.55\mathbf u_n$ m/s².
- **(ii)** $\rho = v^2/a_n = 2778^2/6.55$ = **1177 km**.
- **(iii)** $\dot v = a_t$ = **7.25 m/s²**.
- **(iv)** $\dot\beta = v/\rho$ = **2.36×10⁻³ rad/s**.

## Q5: Banked curve, $\rho = 120$ m, $\theta = 18°$, $m = 1200$ kg, $\mu_s = 0.8$
- **(i)** FBD: weight, normal force $N$ perpendicular to the bank, and friction $F$ along the bank. Kinetic diagram: $mv^2/\rho$ horizontal towards the centre. Vertical balance is $\sum F_b = 0$.
- **(ii)** With $F = 0$: $N\sin\theta = mv^2/\rho$ and $N\cos\theta = mg$, so $\tan\theta = v_0^2/\rho g$. **$v_0 = 19.6$ m/s** (70.4 km/h).
- **(iii)** In general (taking $F$ positive **down** the bank):

$$
F = m\left(\frac{v^2}{\rho}\cos\theta - g\sin\theta\right),\qquad N = m\left(g\cos\theta + \frac{v^2}{\rho}\sin\theta\right)
$$

| Speed | $F$ | $N$ | $F/N$ | OK? |
|---|---|---|---|---|
| $1.2v_0$ = 23.5 m/s | **+1601 N** (down the bank) | 12 898 N | 0.124 | yes, < 0.8 |
| $0.9v_0$ = 17.6 m/s | **−691 N** (up the bank) | 12 153 N | 0.057 | yes |

- **(iv)** The friction arrow points **down** the bank at the higher speed (the car wants to slide outwards) and **up** at the lower speed.
- **(v)** Impending slip outwards, $F = \mu_sN$:

$$
\frac{v^2}{\rho} = g\frac{\sin\theta + \mu_s\cos\theta}{\cos\theta - \mu_s\sin\theta}\quad\Rightarrow\quad v_{max} = \mathbf{42.3}\ \text{m/s}\ (152\ \text{km/h})
$$

There is no lower limit: $\tan18° < 0.8$, so the car can even stop on the bank.

![[d_t2_q5_banked_curve.png|720]]

## Q6: Rotor ride, $r = 12$ m, $\mu_s = 0.3$
- **(i)** FBD: weight down, friction up the wall, and the wall's normal force $N$ **towards the axis**. $N$ is the only horizontal force and supplies the centripetal acceleration.
- **(ii)** $N = m\omega^2r$ and $\mu_sN\ge mg$, so

$$
\omega\ge\sqrt{\frac{g}{\mu_sr}} = \mathbf{1.65}\ \text{rad/s} = 15.8\ \text{rpm}
$$

The answer is independent of the rider's mass.

## Q7: Boy (75 kg) on a 10 m swing arm at $\theta = 45°$, $v = 6$ m/s, $\dot v = 0.5$ m/s²
- $a_n = v^2/L = 3.6$ m/s² towards the pivot C, and $a_t = 0.5$ m/s² along the motion (up-left).
- In $x$–$y$: $m\mathbf a = 75[0.5(-0.707, 0.707) + 3.6(-0.707, -0.707)] = (-217, -164)$ N.
- The seat force $\mathbf R$ satisfies $\mathbf R + m\mathbf g = m\mathbf a$, so **$R_x = -217$ N** (towards C horizontally) and **$R_y = 571$ N** (up).

## Q8: 2.5 kg collar on the smooth rod $y = 2.4 - \tfrac53x^2$, at A ($x = 0.6$ m) with $v = 3$ m/s; spring $k = 150$ N/m, $l_0 = 0.9$ m, anchored at O
- **Geometry**: A = (0.6, 1.8) m. Slope $dy/dx = -2$ ($\theta = 63.4°$ below horizontal), $d^2y/dx^2 = -10/3$.
- **Curvature**: $\rho = (1 + 4)^{3/2}/(10/3)$ = **3.35 m**.
- **Spring**: length $\sqrt{0.6^2 + 1.8^2} = 1.897$ m, stretch 0.997 m, $F_s = 149.6$ N pulling A towards O.

Resolving along $\mathbf u_t = (1, -2)/\sqrt5$ and $\mathbf u_n = (-2, -1)/\sqrt5$ (towards the concave side):

$$
\sum F_t:\ 21.9 + 105.8 = 2.5a_t\ \Rightarrow\ a_t = \mathbf{51.1}\ \text{m/s}^2
$$

$$
\sum F_n:\ 11.0 + 105.8 + N = 2.5\frac{3^2}{3.35} = 6.7\ \Rightarrow\ N = \mathbf{-110}\ \text{N}
$$

- The rod pushes the collar **outwards** (away from the centre of curvature) with 110 N.
- $|\mathbf a| = \sqrt{51.1^2 + 2.68^2}$ = **51.2 m/s²**, dominated by the spring's pull along the rod.

![[d_t2_q8_collar.png|620]]

## Q9: Mine car (100 kg) hoisted up a 30° incline by an on-board motor, $a_{P/C} = 1.2$ m/s²
- From the figure, **three** cable strands run between the car and the wall pulleys. Hauling in cable at the motor shortens the car–wall distance at one third of the rate: $3a_C = a_{P/C}$, so **$a_C = 0.4$ m/s²**.
- Car: $3T - mg\sin30° = ma_C$, so **$T = 177$ N**.

## Q10: Aircraft A flies east at 800 km/h; B flies at 45° NE but appears to A to move away at 60°
- **(i)–(iii)** Attach a translating frame $x$–$y$ to A: $\mathbf r_B = \mathbf r_A + \mathbf r_{B/A}$ and $\mathbf v_B = \mathbf v_A + \mathbf v_{B/A}$.
- **(iv)** $\mathbf v_{B/A}$ points at 120° from east (60° back from the $-x$ axis). Components:
  - north: $v_B\sin45° = u\sin60°$;
  - east: $v_B\cos45° = 800 - u\cos60°$.
- Solving: $u = 800/(\sin60° + \cos60°)$ = 586 km/h and **$v_B = 717$ km/h at 45°**.

## Q11: Car A accelerates at 1.2 m/s² at 72 km/h; car B rounds a 150 m radius at a steady 54 km/h
Axes from the figure: $x$ along A's motion, $y$ across.
- $\mathbf v_A = (20, 0)$ m/s.
- B is on the curve at 30°, travelling tangentially: $\mathbf v_B = 15(0.5, -0.866)$ m/s. Its centripetal acceleration $v^2/\rho = 1.5$ m/s² points to the centre: $\mathbf a_B = (1.30, 0.75)$ m/s².

$$
\mathbf v_{B/A} = (-12.5,\,-13.0)\ \text{m/s}\ \Rightarrow\ \mathbf{18.0}\ \text{m/s};\qquad \mathbf a_{B/A} = (0.10,\,0.75)\ \text{m/s}^2\ \Rightarrow\ \mathbf{0.757}\ \text{m/s}^2
$$

![[d_t2_relative_velocity.png|880]]

## Sources
- Dynamics Problem sheet 2 (no official answers supplied). Solutions worked here and checked numerically.
