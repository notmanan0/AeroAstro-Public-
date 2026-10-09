---
title: "FEEG1002 Dynamics Tutorial 3 - Work, Energy and Power Solutions"
module: "FEEG1002 Mechanics, Materials and Structures"
type: tutorial
stream: "Part D: Dynamics"
tags: [feeg1002, tutorial-solutions, dynamics, work-energy, springs, power, pendulum]
sheet: "Dynamics Problem sheet 3 (work, energy, power)"
theory_notes: ["[[FEEG1002 D3 - Work, Energy and Power]]"]
key_concepts: ["[[Work-Energy Principle]]", "[[Conservative Forces and Potential Energy]]", "[[Power and Efficiency]]"]
status: complete
sources: ["02 - Sources/Dynamics/Tutorials/Tutorial Sheet 03 - Work, Energy and Power.pdf"]
---

# FEEG1002 Dynamics Tutorial 3 - Work, Energy and Power Solutions

> [!abstract] Sheet Info
> 11 problems. Every printed answer is reproduced ✔.
> - Q8 has no printed answer; it is derived here.
> - Q9 gets an extra "regime map" figure.
> - The pulley geometry in Q4 and Q11 was read from the sheet's figures.

## Theory Links
- [[FEEG1002 D3 - Work, Energy and Power]] · [[Work-Energy Principle]] · [[Conservative Forces and Potential Energy]] · [[Power and Efficiency]]

---

## Q1: Lunar lander, safe at $\le5$ m/s, $g = 1.62$ m/s²
$v_2^2 = v_1^2 + 2gh$ with $v_2 = 5$ m/s:
- (a) $v_1 = 0$: $h = 25/3.24$ = **7.7 m** ✔
- (b) and (c) $v_1 = 2$ m/s **up or down**: $h = 21/3.24$ = **6.5 m** ✔

The direction does not matter. A lander moving up at 2 m/s comes back down through the same height at 2 m/s: energy cannot tell the difference.

## Q2: 60 kg bungee jumper, 40 m bridge, $l_0 = 15$ m, $k = 150$ N/m
Energy from rest to the lowest point, with stretch $x$: $mg(15 + x) = \tfrac12kx^2$, so $75x^2 - 588.6x - 8829 = 0$ and $x = 15.46$ m.
- (a) Height above the water: $40 - 30.46$ = **9.54 m** ✔
- (b) $F_{max} = kx$ = **2319 N** ✔ (about $4g$ on the jumper)

## Q3: 40 kg hammer, two springs ($k = 1500$ N/m, $l_0 = 0.2$ m), falling $b = 0.4$ m
- Position 1: each spring is $\sqrt{0.3^2 + 0.4^2} = 0.5$ m long, stretched 0.3 m.
- Position 2: each is 0.3 m long (horizontal), stretched 0.1 m.
- Energy:

$$
mg(0.4) + 2\cdot\tfrac12(1500)(0.3^2 - 0.1^2) = \tfrac12(40)v_2^2\ \Rightarrow\ 157.0 + 120.0 = 20v_2^2\ \Rightarrow\ v_2 = \mathbf{3.72}\ \text{m/s}\ ✔
$$

## Q4: Two 50 kg blocks on a frictionless floor, $F = 500$ N on A, A moves 3 m
- **Cord** (from the figure): anchored to B, round a pulley on A, round a pulley on B, then to a fixed post. Its length is $2s_A + 3s_B$ = const, so $v_B = \tfrac23v_A$ (in magnitude).
- **Energy** (cord tensions are internal and cancel):

$$
500(3) = \tfrac12(50)v_A^2\left(1 + \tfrac49\right)\ \Rightarrow\ v_A = \mathbf{6.45}\ \text{m/s},\quad v_B = \mathbf{4.30}\ \text{m/s}\ ✔
$$

## Q5: Truck reaches 72 km/h in 75 m; 80 kg crate on the bed
The truck's acceleration is $a = 20^2/(2\times75) = 2.67$ m/s².
- **(a) $\mu_s = 0.3$**: the crate needs $F = ma = 213$ N, which is below $\mu_smg = 235$ N, so there is **no slip**. Static friction does work over the truck's 75 m: $U = 213\times75$ = **16 000 J** ✔. That equals the crate's final KE, $\tfrac12(80)(20^2)$.
- **(b) $\mu_s = 0.25$**: the limit $\mu_sg = 2.45$ m/s² is less than 2.67 m/s², so it **slips**.
  - Kinetic friction $0.2(80g) = 157$ N accelerates the crate at 1.96 m/s² for the truck's 7.5 s.
  - The crate moves 55.2 m, so $U = 157\times55.2$ = **8660 J** ✔.

Static friction doing positive work is the exception flagged in the lecture: its point of application moves with the truck.

## Q6: 10 kg slider up a 30° guide, $F = 250$ N via a pulley B, spring $k = 60$ N/m (stretch 0.6 m at A), A to C is 1.2 m
From the figure, B sits $b = 0.9$ m from the guide, perpendicular to the guide at C.
- Cord from B to the slider: $\sqrt{1.2^2 + 0.9^2} = 1.5$ m at A, 0.9 m at C. The force's point moves 0.6 m, so $U_F = 250(0.6) = 150$ J.
- Spring: stretch 0.6 → 1.8 m, so $U_e = -\tfrac12(60)(1.8^2 - 0.6^2) = -86.4$ J.
- Gravity: $-10g(1.2\sin30°) = -58.9$ J.
- Net 4.74 J = $\tfrac12(10)v_C^2$, so **$v_C = 0.974$ m/s** ✔

The constant force $F$ does work equal to $F$ times the change in cord length, not $F$ times the slider's displacement.

## Q7: Elliptical loop, $R_1 = 3$ m, $R_2 = 4$ m, $m = 200$ kg, $N_B = 0.2mg$
- At the top, $\rho_B = R_1^2/R_2 = 2.25$ m. Then $N + mg = mv_B^2/\rho_B$ gives $v_B^2 = 1.2g\rho_B$, so **$v_B = 5.15$ m/s** ✔
- Energy from A to B, climbing $2R_2 = 8$ m: $v_A^2 = v_B^2 + 2g(8)$, so **$v_A = 13.54$ m/s** ✔, and $v_C = v_A$.
- Braking $F_B = cs^2$: $\int_0^{s_{CD}}cs^2\,ds = cs_{CD}^3/3 = \tfrac12mv_C^2$, so **$s_{CD} = 10.0$ m** ✔

![[d_t3_q7_elliptical_loop.png|860]]

## Q8: Simple pendulum released from rest at $\theta_0$
- Energy: $v = \sqrt{2gL(\cos\theta - \cos\theta_0)}$. It is fastest at the bottom, $\sqrt{2gL(1 - \cos\theta_0)}$.
- **Work done by the tension** for any $\Delta\theta$: **zero**. $T$ always acts along the cord, perpendicular to the circular path ($\mathbf T\cdot d\mathbf r = 0$).

## Q9: Pendulum given $v_0$ at the bottom
- **(a)** FBD: $T$ towards O and $mg$ down. Kinetic diagram: $mv^2/L$ towards O and $m\dot v$ tangential.
- **(b)** $v = \sqrt{v_0^2 - 2gL(1 - \cos\theta)}$ ✔
- The normal direction gives the tension: $T - mg\cos\theta = mv^2/L$, so $T/mg = v_0^2/gL - 2 + 3\cos\theta$.
- **(c)** A full revolution needs $T\ge0$ at the top ($\theta = 180°$): $v_0^2/gL - 5\ge0$, so **$v_{0,min} = \sqrt{5gL}$** ✔
- **(d)** At $\theta = 0$ with $v_{0,min}$: $a = a_n = v_0^2/L$ = **$5g$** ✔ ($a_t = 0$ there).
- **(e)** $T = 0$ at **$\theta_L = \cos^{-1}\!\left(\tfrac23 - \tfrac{v_0^2}{3gL}\right)$** ✔

The regimes:
- **$v_0\le\sqrt{2gL}$**: it swings back and the cord never goes slack.
- **Between $\sqrt{2gL}$ and $\sqrt{5gL}$**: the cord goes slack above the horizontal and the bob falls inwards.
- **$\ge\sqrt{5gL}$**: full loops.

![[d_t3_q9_pendulum_regimes.png|700]]

## Q10: 1500 kg car, 50 → 80 km/h in 400 m, rolling resistance 2% of the weight
- $a = (22.2^2 - 13.9^2)/800 = 0.376$ m/s².
- Driving force $F = ma + 0.02mg = 564 + 294 = 859$ N.
- (a) Power is greatest at the highest speed: $P = Fv = 859\times22.2$ = **19.07 kW** ✔
- (b) Steady 80 km/h: $P = 294\times22.2$ = **6.54 kW** ✔

![[d_t3_q10_car_power.png|660]]

## Q11: Lift with counterweight C (on a movable pulley) and car D (300 kg each), motor at P
- **Rope 1**: ceiling → round C's pulley → over a fixed pulley → attached to D. Its tension is $T_1$, and C moves at half D's speed in the opposite direction.
- **Rope 2**: D → over a second fixed pulley → motor. Its tension is $T_2$, and the motor rope moves at $v_D$.
- **(a) Constant speed**: $T_1 = mg/2 = 1472$ N and $T_2 = mg - T_1 = 1472$ N, so **$P = T_2v_D = 7.36$ kW** ✔
- **(b) $a_D = 0.75$ m/s²** (up), so $a_C = 0.375$ m/s² (down):
  - C: $mg - 2T_1 = m(0.375)$, so $T_1 = 1415$ N;
  - D: $T_1 + T_2 - mg = m(0.75)$, so $T_2 = 1753$ N;
  - **$P = 8.76$ kW** ✔

## Sources
- Dynamics Problem sheet 3 (answers printed on the sheet)
