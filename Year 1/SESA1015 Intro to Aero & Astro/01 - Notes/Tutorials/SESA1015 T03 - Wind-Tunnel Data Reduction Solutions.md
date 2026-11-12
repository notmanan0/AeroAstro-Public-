---
title: "SESA1015 T03 - Wind-Tunnel Data Reduction Solutions"
module: "SESA1015 Intro to Aero & Astro"
type: tutorial-solutions
stream: "Mechanics of Flight revision workbook"
order: 3
tags: [sesa1015, tutorial, wind-tunnel, data-reduction]
aliases: ["SESA1015 Revision Q9 Q10 Q11 Q12 Q41"]
date: 2026-09-27
status: complete
parent: ["[[SESA1015 Intro to Aero & Astro Hub]]"]
prerequisites: ["[[SESA1015 M02 - Aircraft Geometry, Forces and Coefficients]]", "[[SESA1015 M03 - Aerodynamic Characteristics and the Drag Polar]]"]
theory_notes: ["[[SESA1015 M03 - Aerodynamic Characteristics and the Drag Polar]]", "[[SESA1015 M02 - Aircraft Geometry, Forces and Coefficients]]"]
key_concepts: ["[[Lift-Curve Slope]]", "[[Parabolic Drag Polar]]", "[[Dynamic Pressure and Aerodynamic Coefficients]]", "[[Reynolds Number]]"]
sources: ["04 - Labs & Coursework/Revision & Spreadsheets/SESA1015 - Revision Questions (Original).xlsx (sheets Question 9, 10, 11, 12, 41)"]
---

# SESA1015 T03 - Wind-Tunnel Data Reduction Solutions

> [!abstract] Sheet info
> Revision workbook Questions 9 to 12 and 41. A full-scale UAV is tested in a wind tunnel under standard sea-level conditions ($\rho=1.225$ kg/m³) and the balance measures the vertical force (lift) and horizontal force (drag) at two angles of attack. Each reading is turned into a coefficient with $qS=\tfrac12\rho V^2S$; two lift coefficients fix the lift line $C_L=a(\alpha-\alpha_0)$, and two lift and drag pairs fix the polar $C_D=C_{D0}+KC_L^2$. Question 41 is a model-scaling problem. The solutions use the numbers in the question wording; the spreadsheet's input cells hold a different randomised set, noted under each question. Every number was recomputed in Python.

Theory: [[SESA1015 M03 - Aerodynamic Characteristics and the Drag Polar#Two-point reduction of a lift curve]] and [[SESA1015 M03 - Aerodynamic Characteristics and the Drag Polar#Two-point reduction of a drag polar]].

## Question 9

A small UAV has a gross wing area of 1.1 m² and the tunnel speed is 22 m/s. At $0.5^\circ$ and $6^\circ$ the vertical forces are 29.7 and 190.4 N and the horizontal forces 2.98 and 19.37 N. What is the slope of the lift-coefficient curve? (Three decimal places.)

The force-to-coefficient factor is

$$
qS=\tfrac12(1.225)(22)^2(1.1)=326.10\ \text{N},
$$

so

$$
C_{L1}=\frac{29.7}{326.10}=0.09108,\qquad C_{L2}=\frac{190.4}{326.10}=0.58388 .
$$

Both points lie on $C_L=a(\alpha-\alpha_0)$; subtracting one from the other removes $\alpha_0$:

$$
a=\frac{C_{L2}-C_{L1}}{\alpha_2-\alpha_1}=\frac{0.58388-0.09108}{6.0-0.5}=\frac{0.49280}{5.5}=0.0896\ \text{per degree}.
$$

To three decimal places the slope is $0.090$ per degree, or $0.0896\times57.30=5.13$ per radian, close to the typical $0.09$ per degree. The drag readings are not needed. The no lift angle from the same data is $\alpha_0=0.5-0.09108/0.0896=-0.52^\circ$.

> [!note] Spreadsheet inputs
> The input cells hold $S=1.2$ m², $V=21$ m/s, angles $0.4^\circ$ and $6.3^\circ$ and lifts 30.5 and 181.3 N, which give $0.079$ per degree (the sheet's answer, 0.0789).

## Question 10

A small UAV has a gross wing area of 1.0 m² and the tunnel speed is 21 m/s. At $0.1^\circ$ and $6.3^\circ$ the vertical forces are 28.2 and 188.7 N and the horizontal forces 3.03 and 18.39 N. At what angle is $C_L$ zero? (Three decimal places.)

Here

$$
qS=\tfrac12(1.225)(21)^2(1.0)=270.11\ \text{N},
$$

so

$$
C_{L1}=\frac{28.2}{270.11}=0.104401,\qquad C_{L2}=\frac{188.7}{270.11}=0.698598,
$$

and the slope is

$$
a=\frac{0.698598-0.104401}{6.3-0.1}=\frac{0.594197}{6.2}=0.0958382\ \text{per degree}.
$$

The zero-lift angle is where the line meets the $\alpha$ axis. From $C_{L1}=a(\alpha_1-\alpha_0)$,

$$
\begin{aligned}
\alpha_0&=\alpha_1-\frac{C_{L1}}{a}\\
&=0.1-\frac{0.104401}{0.0958382}=0.1-1.08935\\
&=-0.989^\circ .
\end{aligned}
$$

The negative value is what a positively cambered wing gives: it already lifts at zero angle of attack. Using the second point instead, $6.3-0.698598/0.0958382=-0.989^\circ$, as it must.

> [!note] Spreadsheet inputs
> The input cells hold $S=1.1$ m², $V=20$ m/s, angles $0.8^\circ$ and $6.4^\circ$ and lifts 30.5 and 194.2 N, which give $-0.243^\circ$. The sheet finds the intercept as $c=|\alpha_2a-C_{L2}|$ and then $\alpha_0=-c/a$; the absolute value happens to give the right sign for these inputs but would give the wrong one for a wing with $\alpha_0>0$. Use $\alpha_0=\alpha_1-C_{L1}/a$.

## Question 11

A small UAV has a gross wing area of 1.3 m² and the tunnel speed is 22 m/s. At $0.9^\circ$ and $6.3^\circ$ the vertical forces are 29.7 and 193.1 N and the horizontal forces 9.60 and 17.73 N. What is the profile drag coefficient? (Three decimal places.)

Here

$$
qS=\tfrac12(1.225)(22)^2(1.3)=385.39\ \text{N},
$$

and the coefficients are

| point | $C_L$ | $C_D$ |
|---|---|---|
| 1 ($0.9^\circ$) | $29.7/385.39=0.077066$ | $9.60/385.39=0.024910$ |
| 2 ($6.3^\circ$) | $193.1/385.39=0.501057$ | $17.73/385.39=0.046006$ |

Both points satisfy $C_D=C_{D0}+KC_L^2$. Subtracting the first from the second removes $C_{D0}$:

$$
\begin{aligned}
K&=\frac{C_{D2}-C_{D1}}{C_{L2}^2-C_{L1}^2}\\
&=\frac{0.046006-0.024910}{0.251058-0.005939}=\frac{0.021096}{0.245119}=0.08606 .
\end{aligned}
$$

Back-substituting in the first equation,

$$
\begin{aligned}
C_{D0}&=C_{D1}-KC_{L1}^2\\
&=0.024910-0.08606(0.005939)\\
&=0.024399\approx0.024 .
\end{aligned}
$$

> [!warning] Not the drag coefficient at the first angle
> The spreadsheet notes that the first angle is small, so the profile drag could be taken as $C_D$ there. That gives $0.0249$, which rounds to $0.025$, not $0.024$: at $0.9^\circ$ the wing still has $C_L=0.077$, and the induced part $KC_L^2=0.0005$ changes the third decimal place.

> [!note] Spreadsheet inputs
> The input cells hold $S=1.2$ m², $V=20$ m/s, lifts 30.4 and 187.8 N and drags 9.08 and 17.28 N, which give $C_{D0}=0.030$ ($K=0.070$).

## Question 12

A small UAV has a gross wing area of 1.2 m² and the tunnel speed is 20 m/s. At $0.0^\circ$ and $6.2^\circ$ the vertical forces are 30.8 and 182.6 N and the horizontal forces 9.52 and 15.86 N. (a) What is the constant of the induced drag term in the drag coefficient equation (written $k=K/\pi A$ in the workbook, with $K$ a planform factor; it is the induced drag factor $K$ of the slides)? (b) What is the profile drag coefficient? (Three decimal places.)

Here

$$
qS=\tfrac12(1.225)(20)^2(1.2)=294.0\ \text{N},
$$

and

| point | $C_L$ | $C_D$ |
|---|---|---|
| 1 ($0.0^\circ$) | $30.8/294=0.104762$ | $9.52/294=0.032381$ |
| 2 ($6.2^\circ$) | $182.6/294=0.621088$ | $15.86/294=0.053946$ |

(a) Subtracting the two polar equations,

$$
\begin{aligned}
K&=\frac{C_{D2}-C_{D1}}{C_{L2}^2-C_{L1}^2}\\
&=\frac{0.053946-0.032381}{0.385750-0.010975}=\frac{0.021565}{0.374775}\\
&=0.0575\approx0.058 .
\end{aligned}
$$

(b) Back-substituting,

$$
\begin{aligned}
C_{D0}&=C_{D1}-KC_{L1}^2\\
&=0.032381-0.05754(0.010975)\\
&=0.031749\approx0.032 .
\end{aligned}
$$

At $\alpha=0$ the cambered wing still gives $C_L=0.105$, so $C_{D1}=0.0324$ is not exactly the profile drag; here the difference does not change the answer to three decimal places. The two-point fit is plotted in [[SESA1015 M03 - Aerodynamic Characteristics and the Drag Polar#Two-point reduction of a drag polar]]. The lift data also give $a=0.0833$ per degree and $\alpha_0=-1.26^\circ$.

> [!note] Spreadsheet inputs
> The input cells hold $S=1.1$ m², $V=21$ m/s, angles $0.7^\circ$ and $6^\circ$, lifts 29.8 and 185.1 N and drags 10.85 and 15.19 N. The sheet takes $C_{D0}$ as $C_D$ at the first angle, $0.0365$, and $K=0.0386$; the two-equation method gives $C_{D0}=0.0361$.

## Question 41

A large UAV with wing area 8.9 m², aspect ratio 7.0 and mass 312 kg is to have its landing performance measured in a wind tunnel using a model of span 2.15 m. The design landing speed is 15.8 m/s, but to keep boundary-layer similarity the test speed must be increased by the model scale factor. What force must the lift load cell be able to read? (One decimal place.)

The full-scale span is

$$
b_f=\sqrt{AS_f}=\sqrt{7.0\times8.9}=7.893\ \text{m},
$$

so the length scale factor is

$$
\lambda=\frac{b_f}{b_m}=\frac{7.893}{2.15}=3.671 .
$$

Boundary-layer similarity in the same air needs the same Reynolds number, $\rho V_mc_m/\mu=\rho V_fc_f/\mu$. With $c_m=c_f/\lambda$, the model speed is

$$
V_m=\lambda V_f=3.671\times15.8=58.0\ \text{m/s}.
$$

A geometrically similar model has $S_m=S_f/\lambda^2=0.660$ m². The model and the aircraft are at the same angle and Reynolds number, so they have the same $C_L$, and the model lift is

$$
\begin{aligned}
L_m&=\tfrac12\rho V_m^2S_mC_L=\tfrac12\rho(\lambda V_f)^2\frac{S_f}{\lambda^2}C_L\\
&=\tfrac12\rho V_f^2S_fC_L=L_f .
\end{aligned}
$$

The model carries exactly the full-scale lift. At the design landing condition the aircraft is in level flight at 15.8 m/s, so $L_f=W$:

$$
L_m=mg=312\times9.81=3060.7\ \text{N}.
$$

The landing lift coefficient is $C_L=2W/\rho V_f^2S_f=2.25$, a flapped value, and the test speed of 58 m/s is about Mach 0.17, low enough for compressibility not to spoil the similarity. In practice a load of 3 kN on a 2 m model also tests the model's strength and the tunnel balance; that is why Reynolds-number matching by raising the speed is rarely done at full scale. See [[Reynolds Number]].

> [!note] Spreadsheet inputs
> The input cells hold $m=341$ kg (and other geometry that does not affect the answer), which gives 3345.2 N.

## Answer check

| Question | Answer |
|---:|---|
| 9 | $a=0.090$ per degree (5.13 per radian) |
| 10 | $\alpha_0=-0.989^\circ$ |
| 11 | $C_{D0}=0.024$ |
| 12 | $K=0.058$, $C_{D0}=0.032$ |
| 41 | 3060.7 N |

## Sources

- Revision workbook `SESA1015 - Revision Questions (Original).xlsx`, sheets Question 9, 10, 11, 12 and 41 (wording in column A; input cells noted where they differ)
- Theory: [[SESA1015 M03 - Aerodynamic Characteristics and the Drag Polar]], [[SESA1015 M02 - Aircraft Geometry, Forces and Coefficients]]
