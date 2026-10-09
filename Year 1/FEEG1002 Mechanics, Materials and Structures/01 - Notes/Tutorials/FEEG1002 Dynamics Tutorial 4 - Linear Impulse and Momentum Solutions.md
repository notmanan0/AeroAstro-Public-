---
title: "FEEG1002 Dynamics Tutorial 4 - Linear Impulse and Momentum Solutions"
module: "FEEG1002 Mechanics, Materials and Structures"
type: tutorial
stream: "Part D: Dynamics"
tags: [feeg1002, tutorial-solutions, dynamics, impulse, momentum, impact, recoil]
sheet: "Dynamics Problem sheet 4 (linear impulse and momentum)"
theory_notes: ["[[FEEG1002 D4 - Linear Impulse and Momentum]]"]
key_concepts: ["[[Principle of Linear Impulse and Momentum]]", "[[Coefficient of Restitution]]", "[[Work-Energy Principle]]"]
status: complete
sources: ["02 - Sources/Dynamics/Tutorials/Tutorial Sheet 04 - Linear Impulse and Momentum.pdf"]
---

# FEEG1002 Dynamics Tutorial 4 - Linear Impulse and Momentum Solutions

> [!abstract] Sheet Info
> Seven problems:
> - average impact forces;
> - a half-sine contact pulse;
> - cannon firing, fixed and free to recoil;
> - an embedded meteor;
> - rocket-like brick throwing;
> - an elastic oblique billiard impact.
>
> Every printed answer is reproduced ✔. Q6 depends on a convention that is stated explicitly below.

## Theory Links
- [[FEEG1002 D4 - Linear Impulse and Momentum]] · [[Principle of Linear Impulse and Momentum]] · [[Coefficient of Restitution]]

---

## Q1: 1500 kg car hits a barrier at 3 m/s and rebounds at 1 m/s in 0.4 s
- (a) Taking the rebound direction as positive: $-mv_1 + F_{avg}\Delta t = mv_2$, so $F_{avg} = 1500(3 + 1)/0.4$ = **15 kN** ✔
- (b) $a_{avg} = F_{avg}/m$ = **10 m/s²** ✔ (−10 m/s² in the approach direction).
- (c) **No.** Impulse fixes only the **area** under $F(t)$. The peak depends on the pulse shape, which is not given. A triangular pulse would peak at twice the average.

## Q2: 60 g tennis ball dropped 2.5 m, half-sine pulse, $A = 230$ N, $t_0 = 5$ ms
- (a) $v_1 = \sqrt{2g(2.5)}$ = **7.0 m/s** (down) ✔
- (b) Impulse $I = \int_0^{t_0}A\sin(\pi t/t_0)\,dt = 2At_0/\pi = 0.732$ N s. With weight neglected during contact, $v_2 = I/m - v_1$ = **5.2 m/s** (up) ✔
- (c) $F_{avg} = I/t_0$ = **146.4 N** ✔. That is 250 times the ball's weight, so neglecting weight is justified.
- (d) $a_{peak} = A/m$ = **3.83 km/s²** and $a_{avg} = F_{avg}/m$ = **2.44 km/s²** ✔ (390$g$ and 250$g$).

The rebound height is $5.2^2/2g = 1.38$ m, which implies $e = 5.2/7.0 = 0.74$. Air drag and ball rotation are ignored.

![[d_impulse_force_time.png|880]]

## Q3: Cannon (2000 kg) **fixed** to the ground, 5 kg shell, spring $k = 10^6$ N/m compressed 0.5 m, $\theta = 30°$
- (a) The cannon cannot move, so all the spring energy goes to the shell: $\tfrac12k\Delta l^2 = \tfrac12m_sv_s^2$, so $v_s = \Delta l\sqrt{k/m_s}$ = **223.6 m/s** ✔
- (b) The ground supplies the shell's whole momentum $m_sv_s = 1118$ N s: **$I_x = 968.2$ N s** and **$I_y = 559.0$ N s** ✔
- (c) Over 4 ms: **$F_x = 242.0$ kN** and **$F_y = 139.8$ kN** ✔

## Q4: The same cannon, now **free to roll** horizontally
- Horizontal momentum is conserved: $m_sv_s\cos30° = m_Cv_C$.
- Energy: $\tfrac12k\Delta l^2 = \tfrac12m_sv_s^2 + \tfrac12m_Cv_C^2$.

$$
v_s = \sqrt{\frac{k\Delta l^2}{m_s + m_C(m_s\cos30°/m_C)^2}} = \mathbf{223.4}\ \text{m/s},\qquad v_C = \mathbf{0.48}\ \text{m/s}\ ✔
$$

- (a) Slightly less than 223.6 m/s: 0.1% of the spring energy goes into recoil.
- (c) The vertical ground impulse is $m_sv_s\sin30°$ = **558.5 N s** ✔. The horizontal ground impulse is **zero** (smooth surface).
- (d) $F_y = 558.5/0.004$ = **139.6 kN** ✔

## Q5: 400 kg satellite at 7 km/s absorbs a 2 kg meteor at 12 km/s at 135° to its path
Plastic impact, so momentum is conserved (in kg km/s):

$$
402\,\mathbf v = 400(7,\,0) + 2(12)(-\cos45°,\,-\sin45°) = (2783.0,\,-16.97)
$$

**$|\mathbf v| = 6.92$ km/s**, deflected by **0.35°** ✔.

The satellite loses about 80 m/s and changes direction slightly: an unplanned orbit change, plus damage. The KE lost, $9.944 - 9.634 = 0.31$ GJ (about 310 MJ), goes into the impact.

## Q6: Boy (36 kg) and wagon (9 kg) with three 4.5 kg bricks thrown backwards at 3 m/s **relative to the wagon**
The printed answers take the 3 m/s **relative to the wagon's velocity just before each throw**. Each throw then adds $\Delta v = m_bv_b'/M_{after}$, where $M_{after}$ is the mass remaining.
- (a) One at a time: $\tfrac{13.5}{54} + \tfrac{13.5}{49.5} + \tfrac{13.5}{45} = 0.250 + 0.273 + 0.300$ = **0.823 m/s** ✔
- (b) All at once: $\Delta v = 3(13.5)/45$ = **0.900 m/s** ✔

> [!note] The other convention
> If the throwing speed is measured relative to the wagon **after** release (the usual rocket-exhaust convention), each step is $\Delta v = m_bv_b'/M_{before}$. That gives 0.753 m/s one at a time and 0.692 m/s all at once. Under that convention, throwing one at a time wins, which is why rockets stage. Under the printed convention the ordering reverses. Know which one an exam intends.

![[d_t4_q6_boy_and_bricks.png|660]]

## Q7: Equal billiard balls, cue ball A at 2 m/s in $+y$, B knocked along the 45° line to the pocket, elastic
- The contact impulse acts along the **line of impact**, $\mathbf u = (-1, 1)/\sqrt2$.
- A's velocity component along it is $2\mathbf j\cdot\mathbf u = \sqrt2$ m/s. With equal masses and $e = 1$, A passes all of it to B: $\mathbf v_{B2} = \sqrt2\,\mathbf u$ = **$(-\mathbf i + \mathbf j)$ m/s**.
- A keeps the perpendicular component: $\mathbf v_{A2} = 2\mathbf j - (-\mathbf i + \mathbf j)$ = **$(\mathbf i + \mathbf j)$ m/s** ✔.
- Check momentum: $(1 - 1,\ 1 + 1) = (0, 2)$ ✔. Check energy: $2 + 2 = 4$ ✔.
- The two velocities are at 90° to each other, the classic snooker result.

![[d_t4_q7_billiards.png|540]]

## Sources
- Dynamics Problem sheet 4 (answers printed on the sheet)
