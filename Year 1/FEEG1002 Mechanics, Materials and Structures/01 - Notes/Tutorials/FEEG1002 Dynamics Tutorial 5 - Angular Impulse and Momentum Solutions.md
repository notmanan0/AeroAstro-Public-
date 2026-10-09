---
title: "FEEG1002 Dynamics Tutorial 5 - Angular Impulse and Momentum Solutions"
module: "FEEG1002 Mechanics, Materials and Structures"
type: tutorial
stream: "Part D: Dynamics"
tags: [feeg1002, tutorial-solutions, dynamics, angular-momentum, central-force, orbits]
sheet: "Dynamics Problem sheet 5 (angular impulse and momentum)"
theory_notes: ["[[FEEG1002 D5 - Angular Impulse and Momentum]]"]
key_concepts: ["[[Principle of Angular Impulse and Momentum]]", "[[Work-Energy Principle]]", "[[Orbital Angular Momentum]]"]
status: complete
sources: ["02 - Sources/Dynamics/Tutorials/Tutorial Sheet 05 - Angular Impulse and Momentum.pdf"]
---

# FEEG1002 Dynamics Tutorial 5 - Angular Impulse and Momentum Solutions

> [!abstract] Sheet Info
> Five problems. Each **combines** angular momentum with energy or with $\sum F_n = mv^2/r$.
> - Every printed numerical answer is reproduced ✔.
> - Q5(d) asks for discussion, which is supplied here.

## Theory Links
- [[FEEG1002 D5 - Angular Impulse and Momentum]] · [[Principle of Angular Impulse and Momentum]] · [[Work-Energy Principle]]

---

## Q1: 2 kg puck on an elastic cord ($k = 20$ N/m, $l_1 = 0.5$ m unstretched), $v_1 = 1.5$ m/s perpendicular to the cord
There are two conservation laws. The cord force is central (about O) and the plane is smooth:
- **Energy**: $\tfrac12mv_1^2 = \tfrac12mv_2^2 + \tfrac12k(0.2)^2$, so **$v_2 = 1.36$ m/s** ✔
- **Angular momentum**: $l_1mv_1 = l_2mv_{2\perp}$, so $v_{2\perp} = 0.5(1.5)/0.7 = 1.071$ m/s.
- The rest of $v_2$ is radial: $\dot l = \sqrt{1.360^2 - 1.071^2}$ = **0.838 m/s** ✔

## Q2: 5 kg block on a cord of fixed length $R = 1.2$ m, radial $F_1 = 10$ N outward, $F_2 = 35$ N at 30° to the tangent
Take moments about A.
- The cord tension and $F_1$ are radial, so they give no moment.
- The tangential parts, $F_2\cos30°$ and friction $\mu_kmg$, give the angular impulse:

$$
mRv_1 + \int_0^t(F_2\cos\theta - \mu_kmg)R\,dt = mRv\qquad\Rightarrow\qquad v = v_1 + \left(\frac{F_2\cos\theta}{m} - \mu_kg\right)t
$$

This is part (c) ✔. The normal direction then gives the tension, with $F_2$'s radial component acting outward as in the figure:

$$
T = \frac{mv^2}{R} + F_1 + F_2\sin\theta
$$

| Case | $\dot v$ | $T$ reached | $t$ | $v$ |
|---|---|---|---|---|
| (a) $\mu_k = 0.5$, $v_1 = 0.6$ m/s | 1.157 m/s² | 100 N | **3.09 s** ✔ | **4.17 m/s** ✔ |
| (b) smooth, from rest | 6.062 m/s² | 150 N (breaks) | **0.894 s** ✔ | **5.42 m/s** ✔ |

![[d_t5_q2_cord_tension.png|700]]

## Q3: Four 2.5 kg spheres on a light crossbar at $R = 0.18$ m, $M = 1.5(0.5t + 0.8)$ N m from rest
- (a) $\int_0^tM\,dt = 4mRv$, i.e. $1.5(0.25t^2 + 0.8t) = 1.8v$, so $v = 0.2083t^2 + 0.667t$.
- (b) $v(4)$ = **6.0 m/s** ✔
- (c) Arc length $s = \int v\,dt = 0.0694t^3 + 0.333t^2 = 9.78$ m after 4 s. That is $9.78/(2\pi\times0.18)$ = **8.6 revolutions** ✔

## Q4: 700 kg satellite, free-flight path, $v_A = 10$ km/s at $r_A = 15\times10^6$ m, $\phi_A = 70°$ from the radial line
- $GM_e = 3.988\times10^{14}$ m³/s².
- Because $\mathbf v_A$ is **not** perpendicular to $\mathbf r_A$, use $h = r_Av_A\sin\phi_A = 1.4095\times10^{11}$ m²/s.
- At closest approach B the velocity is perpendicular to $\mathbf r_B$, so $r_Bv_B = h$.
- Energy: $\tfrac12v_A^2 - GM/r_A = \tfrac12v_B^2 - GMv_B/h$. This is a quadratic in $v_B$:

$$
v_B = \mathbf{10.2}\ \text{km/s},\qquad r_B = h/v_B = \mathbf{13.8\times10^6}\ \text{m}\ ✔
$$

The specific energy is positive ($+2.3\times10^7$ J/kg), so the path is a hyperbola. That is why the sheet calls it a free-flight trajectory "NOT an orbit".

## Q5: Game with a 0.25 kg mass, elastic cord ($L = 0.2$ m, $k = 1500$ N/m), inner rough circle $R = 0.2$ m ($\mu_k = 0.8$), start OA = 0.3 m
- **(a)** The bat's impulse adds $0.5/0.25 = 2$ m/s in $+y$, so the speed goes from 1 to **3 m/s** (along $y$, perpendicular to OA). $\Delta KE = \tfrac12(0.25)(9 - 1)$ = **1 J** ✔
- **(b)** From A to B:
  - **Energy**: the cord releases $\tfrac12(1500)(0.1)^2 = 7.5$ J, so $v_B = \sqrt{9 + 2(7.5)/0.25}$ = **8.31 m/s** ✔
  - **Angular momentum**: the cord force is central and the outer surface frictionless, so $H_O$ is conserved. $0.3(3) = d\,(8.31)$, so **$OC = d = 10.83$ cm** ✔. This $d$ is the perpendicular distance from O to the (straight) path once the cord is slack inside $R$: the closest approach, C.
- **(c)** Inside the circle the cord is slack and the mass moves in a straight chord of length $2\sqrt{0.2^2 - 0.1083^2} = 0.336$ m. Friction removes $\mu_kmg(0.336) = 0.66$ J:

$$
v_D = \sqrt{8.31^2 - 2(0.8)(9.81)(0.336)} = \mathbf{7.98}\ \text{m/s}\ ✔\qquad\text{so it exits the circle.}
$$

- **(d) Design changes**:
  - **A rougher mass**: more friction inside only, which helps a little. The mass is going far too fast (about 8 m/s over 0.34 m) for $\mu_k$ to stop it; you would need $\mu_k\approx10$.
  - **A heavier mass**: the same 0.5 N s impulse gives a smaller speed change, and the fixed 7.5 J of cord energy gives less speed, so $v_B$ drops sharply. With $m = 1$ kg: $v_A = 1.5$ m/s and $v_B = \sqrt{1.5^2 + 15} = 4.15$ m/s.
    - The stopping distance $v_B^2/2\mu_kg$ falls from 4.4 m to 1.1 m. That helps, but it is still longer than the 0.34 m chord.
    - $d = 0.3v_A/v_B$ hardly changes (10.8 → 10.8 cm).
    - More playable, but not enough on its own.
  - **An inextensible 0.3 m cord**: the mass simply circles at $r = 0.3$ m and **never** enters the inner circle. Unplayable.

## Sources
- Dynamics Problem sheet 5 (answers printed on the sheet; discussion in (d) added)
