---
title: "FEEG1002 Dynamics Tutorial 1 - Linear Motion Solutions"
module: "FEEG1002 Mechanics, Materials and Structures"
type: tutorial
stream: "Part D: Dynamics"
tags: [feeg1002, tutorial-solutions, dynamics, kinematics, friction, pulleys, drag, buoyancy]
sheet: "Dynamics Problem sheet 1 (linear motion)"
theory_notes: ["[[FEEG1002 D1 - Linear Motion of Particles]]"]
key_concepts: ["[[Kinematic Relations for Rectilinear Motion]]", "[[Newton's Laws of Motion]]", "[[Coulomb Friction]]", "[[Dependent Motion and Pulley Constraints]]"]
status: complete
sources: ["02 - Sources/Dynamics/Tutorials/Tutorial Sheet 01 - Linear Motion.pdf"]
---

# FEEG1002 Dynamics Tutorial 1 - Linear Motion Solutions

> [!abstract] Sheet Info
> 14 problems, which are the whole toolkit of [[FEEG1002 D1 - Linear Motion of Particles]]:
> - differentiating $s(t)$;
> - integrating $a(t)$, $a(s)$ and $a(v)$;
> - friction on inclines;
> - pulley constraints;
> - buoyancy.
>
> **The sheet has no printed answers.** Every result below was worked by hand and checked numerically. Q12's figure was read from the sheet.

## Theory Links
- [[FEEG1002 D1 - Linear Motion of Particles]] · [[Kinematic Relations for Rectilinear Motion]] · [[Coulomb Friction]] · [[Dependent Motion and Pulley Constraints]]

---

## Q1: Boat, $s = 4t + 1.6t^2 - 0.08t^3$ ($2\le t\le10$ s)
$$v = 4 + 3.2t - 0.24t^2,\qquad a = 3.2 - 0.48t$$

- At $t = 4$ s: **$v = 12.96$ m/s**, **$a = 1.28$ m/s²**.
- $a = 0$ at $t = 6.67$ s, giving **$v_{max} = 14.7$ m/s**. The end values are 9.44 m/s and 12.0 m/s, so this is the global maximum.

![[d_t1_q1_boat_kinematics.png|640]]

## Q2: Rocket, $s = bt^2 - ct^4$, with $v = 229$ m/s and $a = 28.2$ m/s² at $t = 10$ s
$v = 2bt - 4ct^3$ and $a = 2b - 12ct^2$. At $t = 10$:
- $20b - 4000c = 229$;
- $2b - 1200c = 28.2$.

So $b = 10.125$ m/s² and $c = -6.625\times10^{-3}$ m/s⁴. Note $c < 0$: the "$-ct^4$" term actually adds height.

At $t = 5$ s: **$v = 104.6$ m/s**, **$a = 22.2$ m/s²**.

## Q3: 54 km/h (15 m/s), light 90 m ahead, 1 s reaction time
- The car covers 15 m during the reaction, leaving 75 m of braking: $0 = 15^2 - 2a(75)$, so **$a = 1.5$ m/s²** deceleration.
- Time $= 1 + 15/1.5$ = **11 s**.

## Q4: Car A at 60 mph passes police car B at 40 mph; B reaches 65 mph in 5 s
- Units: 1 mph = 0.4472 m/s, so $v_A = 26.83$ m/s. B accelerates from 17.89 to 29.07 m/s: $a_B = 2.236$ m/s².
- After 5 s: A has gone 134.2 m, B 117.4 m. The gap is 16.8 m, closing at $29.07 - 26.83 = 2.24$ m/s, which takes 7.5 s more.
- **Total: 12.5 s**.

## Q5: Bungee, 85 kg, 50 m, cord engages after 20 m
| Quantity | Result |
|---|---|
| (i) speed at 20 m | $\sqrt{2g(20)}$ = **19.8 m/s** |
| (iii) minimum $k$ (just touches the water, $v = 0$ at 50 m) | $mg(50) = \tfrac12k(30)^2$, so **$k = 92.7$ N/m** |
| (iv) $a = 0$ | $k(x - 20) = mg$, so **$x = 29.0$ m** |
| (iv) largest $|a|$ | at the bottom: $g - (k/m)(30)$ = **−22.9 m/s²** ($2.3g$) |
| (v) $v_{max}$ | at $x = 29$ m: **21.9 m/s**, not at 20 m |

The FBDs have two regimes:
- $x < 20$ m: weight only, $a = g$;
- $x > 20$ m: weight down and cord force $k(x - 20)$ up.

With $v\,dv = a\,dx$, the speed keeps rising past 20 m for as long as $mg > k(x - 20)$.

![[d_t1_q5_bungee.png|860]]

## Q6: Falling with drag $F_D = cv^2$, $y$ up
- **Acceleration**: $a = -g + \dfrac cmv^2$. While falling, drag acts up.
- **Speed**: with $v\,dv/dy = a$ and $w = v^2$, $\tfrac12dw/dy = -g + (c/m)w$. Integrating from rest at $y_0$:

$$
v^2 = \frac{mg}{c}\left(1 - e^{-2c(y_0 - y)/m}\right)
$$

As the fall distance grows, $|v|\to\sqrt{mg/c}$, the terminal speed.

![[d_drag_terminal_velocity.png|860]]

## Q7: Rocket sled, $m = 100$ kg
**(i)–(ii) FBDs and acceleration** in each phase:
- **Acceleration phase**: thrust $F = 3000 + 200t$, so $a = 30 + 2t$.
- **Brake phase**: drag $0.3v^2$ backwards, so $a = -0.003v^2$.

**(iii) Time**:
- Phase 1: $v = 30t + t^2 = 400$ gives **$t_1 = 10.0$ s**.
- Phase 2: $\int dv/v^2 = -0.003\int dt$ gives $t_2 = \frac1{0.003}\left(\frac1{100} - \frac1{400}\right)$ = **2.50 s**.
- Total: **12.5 s**.

**(iv) Distance**:
- Phase 1: $s_1 = 15t^2 + t^3/3$ = **1833 m**.
- Phase 2: $v\,dv/ds = -0.003v^2$ gives $s_2 = \ln(4)/0.003$ = **462 m**.
- Total: **2295 m**.

![[d_t1_q7_rocket_sled.png|860]]

## Q8: Radial fall from GEO ($r_{geo} = 42164$ km) at $v = \sqrt{2\mu/r_{geo}}$
The initial speed is exactly the **escape speed**, so the specific energy $\tfrac12v^2 - \mu/r = 0$ throughout and $v = \sqrt{2\mu/r}$ at every radius.
- **Entry at $r_a = 6478$ km**: $v = \sqrt{2(398600)/6478}$ = **11.09 km/s**.
- **Time**: $dt = -dr/v = -\sqrt{r/2\mu}\,dr$, so

$$
t = \frac{2}{3\sqrt{2\mu}}\left(r_{geo}^{3/2} - r_a^{3/2}\right) = \mathbf{6075\ s}\ (1.69\ \text{h})
$$

## Q9: 50 kg block sliding down 10 m of 15° slope, $\mu_k = 0.3$, $v_A = 4$ m/s
- Down the slope: $a = g(\sin15° - 0.3\cos15°) = -0.304$ m/s². It is **decelerating**, because $\tan15° < \mu_k$.
- $v_B = \sqrt{16 + 2(-0.304)(10)}$ = **3.15 m/s**.
- $t = (v_B - v_A)/a$ = **2.80 s**.

## Q10: 50 kg on a 15° incline, $\mu_s = 0.4$, $\mu_k = 0.3$, pushed up by $F$
- **(i)** $\tan15° = 0.268 < \mu_s$, so without $F$ the block **stays put**. Friction $mg\sin15° = 127$ N acts up the slope.
- **(ii)** As $F$ grows, the friction needed shrinks, passes through zero when $F = mg\sin\theta$, then reverses to act **down** the slope.
- **(iii)** Impending motion up the slope: $F_0 = mg(\sin15° + \mu_s\cos15°)$ = **316.5 N**.
- **(v)** With $F = F_0 + 60t$ and kinetic friction once sliding: $ma = mg(\mu_s - \mu_k)\cos15° + 60t$, so $a = 0.948 + 1.2t$. Then **$v(2) = 4.30$ m/s**.
- **(vi)** $s(2) = 0.474t^2 + 0.2t^3$ = **3.50 m**.

## Q11: Block A (150 kg) and log D (250 kg, $\mu_k = 0.5$) on a 30° ramp
- **(ii)** The cord runs A → over B → round pulley C on the log → back to B. So $s_A + 2s_C$ = const and **$v_A = -2v_C$, $a_A = 2a_D$** in magnitude.
- **(iii)** Equations of motion:
  - A: $m_Ag - T = 2m_Aa_D$;
  - D: $2T - m_Dg(\sin30° + 0.5\cos30°) = m_Da_D$.
  - Solving: **$a_D = 0.770$ m/s²**, **$a_A = 1.54$ m/s²**, **$T = 1240$ N**.
- **(iv)** Over 6 m: $v_A = \sqrt{2(1.54)(6)}$ = **4.30 m/s**.
- **(v)** Pulley B: one strand down to A, two strands down the ramp at 30°. $R_x = 2T\cos30° = 2148$ N and $R_y = T + 2T\sin30° = 2481$ N, so **$R_B = 3282$ N**.

![[d_t1_q11_log_and_block_fbds.png|880]]

## Q12: A (5 kg, $\mu_k = 0.2$) on a ledge, B (10 kg) on a movable pulley; $v_{A0} = 0.6$ m/s
- The cord is anchored at the ceiling, so $s_A + 2s_B$ = const and $v_B = v_A/2$.
- Work–energy for the system (tension is internal to the cord and cancels):

$$
\tfrac12(5)(0.6^2) + \tfrac12(10)(0.3^2) + (10g)(0.6) - 0.2(5g)(1.2) = \tfrac12(5)v_A^2 + \tfrac12(10)(v_A/2)^2
$$

$$
1.35 + 58.86 - 11.77 = 3.75v_A^2\quad\Rightarrow\quad v_A = \mathbf{3.59}\ \text{m/s}
$$

## Q13: Arm guided at 60°, object 90 kg on the horizontal platform, $\mu_s = 0.2$
The platform accelerates with magnitude $a$ along the 60° guide. The object needs:
- horizontal friction $F = ma\cos60°$;
- normal force $N = m(g\mp a\sin60°)$, with $-$ when accelerating downwards.

**Downward acceleration**: $a\cos60° \le \mu_s(g - a\sin60°)$, so
$$a_{max} = \frac{\mu_sg}{\cos60° + \mu_s\sin60°} = \mathbf{2.91}\ \text{m/s}^2,\qquad N = \mathbf{656}\ \text{N}$$

**Upward acceleration**: $a\cos60° \le \mu_s(g + a\sin60°)$, so
$$a_{max} = \frac{\mu_sg}{\cos60° - \mu_s\sin60°} = \mathbf{6.00}\ \text{m/s}^2,\qquad N = \mathbf{1351}\ \text{N}$$

Accelerating downwards unloads the contact (smaller $N$, less friction available), so the downward limit is lower.

## Q14: Floating cylinder ($D = 3$ m, $L = 1.2$ m, $\rho_m = 500$ kg/m³) released with $l_0 = 0.7$ m submerged
- **Equilibrium draught**: $\rho_mL/\rho_f = 0.6$ m. At 0.7 m the body is over-buoyant and rises.
- **(i)** With $y$ the rise from the start, $F_B = \rho_fgA(0.7 - y)$ and $m = \rho_mAL = 4241$ kg:

$$
a = g\left(\frac{0.7 - y}{0.6} - 1\right) = -\frac{g}{0.6}(y - 0.1)
$$

- **(ii)** $v\,dv = a\,dy$ gives $v^2 = \dfrac g{0.6}(0.2y - y^2)$.
- **(iii)** **$y_{max} = 0.2$ m**.
- **(iv)** **$v_{max} = 0.404$ m/s** at $y = 0.1$ m.
- **(v)** **Simple harmonic motion** about $y = 0.1$ m with $\omega = \sqrt{g/0.6} = 4.04$ rad/s and period 1.55 s, oscillating for ever without drag. It is the SDOF oscillator of [[FEEG1002 D6 - Single Degree of Freedom Vibration]], with buoyancy stiffness $k = \rho_fgA$.

![[d_t1_q14_buoyant_cylinder.png|860]]

## Sources
- Dynamics Problem sheet 1 (no official answers supplied). Solutions worked here and checked numerically.
