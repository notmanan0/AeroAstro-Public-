---
title: "SESA1015 T08 - Constraint Analysis Solutions"
module: "SESA1015 Intro to Aero & Astro"
type: tutorial-solutions
stream: "Mechanics of Flight revision workbook"
order: 8
tags: [sesa1015, tutorial, constraint-analysis]
aliases: ["SESA1015 Revision Q35 Q36 Q37"]
date: 2026-09-27
status: complete
parent: ["[[SESA1015 Intro to Aero & Astro Hub]]"]
prerequisites: ["[[SESA1015 M12 - Aircraft Constraint Analysis]]"]
theory_notes: ["[[SESA1015 M12 - Aircraft Constraint Analysis]]", "[[SESA1015 M09 - Take-off and Landing Performance]]", "[[SESA1015 M10 - Turning Flight and Manoeuvre Performance]]", "[[SESA1015 M08 - Glide and Climb Performance]]"]
key_concepts: ["[[Aircraft Constraint Diagram]]", "[[Thrust-to-Weight Ratio]]", "[[Take-off Ground Run]]", "[[Parabolic Drag Polar]]"]
sources: ["04 - Labs & Coursework/Revision & Spreadsheets/SESA1015 - Revision Questions (Original).xlsx (sheets Question 35–37)", "02 - Sources/Mechanics of Flight/Calculator for Revision Questions.xlsx"]
---

# SESA1015 T08 - Constraint Analysis Solutions

> [!abstract] What these questions test
> Questions 35–37 set the same small, low-flying UAV problem three times: a take-off requirement against a turn, a climb and a cruise requirement. Each asks for the lowest wing loading at which the minimum required thrust to weight ratio is reached, which is the left crossing of the horizontal take-off line with the U-shaped manoeuvre curve. Answers: 33.1, 49.8 and 51.5 N/m².

All three use sea-level density $\rho=1.225$ kg/m³ and $g=9.81$ m/s², and the theory in [[SESA1015 M12 - Aircraft Constraint Analysis]]. Write $x=W/S$ in N/m².

The take-off constraint with lift and drag neglected on the ground run is horizontal:

$$
y_{TO}=\frac{V_2^2}{2gs_1}+\mu .
$$

The turn, climb and cruise constraints are all special cases of

$$
y=\frac{V_V}{V}+\frac{qC_{D0}}{x}+\frac{Kn^2}{q}\,x,\qquad q=\tfrac12\rho V^2,
$$

with $V_V=0$ for a level turn or cruise and $n=1$ for climb and cruise. To the left of their first crossing the manoeuvre curve lies above the take-off line and sizes the aircraft; to the right the take-off line does. The minimum required $T/W$ is therefore $y_{TO}$ itself, first reached at the left crossing. Setting $y=y_{TO}$ and multiplying through by $x$,

$$
\frac{Kn^2}{q}\,x^2-\left(y_{TO}-\frac{V_V}{V}\right)x+qC_{D0}=0,
$$

a quadratic $ax^2-bx+c=0$ whose smaller root

$$
x=\frac{b-\sqrt{b^2-4ac}}{2a}
$$

is the answer. The larger root, where the induced branch climbs back through the line, is in every case thousands of N/m², far beyond any realistic stall limit for a small UAV.

![[mof_m12_revision_crossings.png|900]]

The workbook sheets find the root with Excel's Solver from a guessed wing loading. Their input cells hold different (randomised) numbers from the wording; the wording is used below and the sheet values are compared at the end of each question.

## Question 35

A small UAV that flies at low altitude must take off on a runway of length 88 m and perform constant-velocity turns at 31 m/s, with

$$
C_D=0.024+0.057C_L^2 .
$$

$V_2$ is 21.6 m/s, the maximum load factor the structure can support in the turn is 2.0 and the rolling coefficient of friction is 0.17. Find the lowest wing loading that gives the minimum required thrust to weight ratio, to one decimal place in N/m².

Take-off line:

$$
\begin{aligned}
y_{TO}&=\frac{21.6^2}{2(9.81)(88)}+0.17\\
&=\frac{466.56}{1726.56}+0.17\\
&=0.27023+0.17=0.44023 .
\end{aligned}
$$

The turn is flown at the structural limit $n=2$, which needs the most thrust of any turn at this speed. The dynamic pressure is $q=\frac12(1.225)(31^2)=588.61$ Pa, so

$$
a=\frac{Kn^2}{q}=\frac{0.057\times4}{588.61}=3.8735\times10^{-4},\qquad b=0.44023,\qquad c=qC_{D0}=588.61\times0.024=14.127 .
$$

The discriminant:

$$
b^2-4ac=0.193798-4(3.8735\times10^{-4})(14.127)=0.193798-0.021888=0.171910 .
$$

The smaller root:

$$
x=\frac{0.44023-\sqrt{0.171910}}{2(3.8735\times10^{-4})}=\frac{0.44023-0.41462}{7.7470\times10^{-4}}=33.05\ \text{N/m}^2 .
$$

$$
\boxed{W/S=33.1\ \text{N/m}^2}
$$

> [!check] Substitution
> At $x=33.05$: $14.127/33.05+3.8735\times10^{-4}\times33.05=0.4274+0.0128=0.4402=y_{TO}$. The bottom of the turn curve is $2n\sqrt{KC_{D0}}=0.148$, well below the take-off line, so a crossing exists. The other root is 1103 N/m².

The workbook sheet holds $s_1=72$ m, $V=34$ m/s, $C_D=0.02+0.055C_L^2$, $V_2=20.6$ m/s, $n=2.2$ and $\mu=0.16$. These give $y_{TO}=0.4604$ and a lower root of 31.6 N/m². The sheet's stored wing loading of 37.51 is not a converged Solver result: its quadratic residual (F14) is $-0.0036$ rather than zero and its stored $T/W$ (F15, 0.392) does not equal the take-off value (F9, 0.460).

## Question 36

The same UAV must take off on a runway of 56 m and climb at 34 m/s, with

$$
C_D=0.022+0.056C_L^2 .
$$

$V_2$ is 18.6 m/s, the desired climb rate is 6.4 m/s and the rolling coefficient of friction is 0.19. Find the lowest wing loading that gives the minimum required thrust to weight ratio, to one decimal place in N/m².

Take-off line:

$$
\begin{aligned}
y_{TO}&=\frac{18.6^2}{2(9.81)(56)}+0.19\\
&=\frac{345.96}{1098.72}+0.19\\
&=0.31488+0.19=0.50488 .
\end{aligned}
$$

For the climb, $V_V/V=6.4/34=0.18824$ and $q=\frac12(1.225)(34^2)=708.05$ Pa. The climb term moves to the other side of the equation before the quadratic is formed, so $b$ is the take-off value minus the climb gradient:

$$
a=\frac kq=\frac{0.056}{708.05}=7.9091\times10^{-5},\qquad b=0.50488-0.18824=0.31664,\qquad c=708.05\times0.022=15.577 .
$$

$$
b^2-4ac=0.100261-4(7.9091\times10^{-5})(15.577)=0.100261-0.004928=0.095333 .
$$

$$
x=\frac{0.31664-\sqrt{0.095333}}{2(7.9091\times10^{-5})}=\frac{0.31664-0.30876}{1.58182\times10^{-4}}=49.81\ \text{N/m}^2 .
$$

$$
\boxed{W/S=49.8\ \text{N/m}^2}
$$

> [!check] Substitution
> At $x=49.81$: $0.18824+15.577/49.81+7.9091\times10^{-5}\times49.81=0.18824+0.31272+0.00394=0.50490\approx y_{TO}$ (0.50488 with unrounded values). Forgetting to subtract the climb term, i.e. using $b=0.50488$, gives 31.0 N/m², the most likely wrong answer.

The workbook sheet holds $s_1=70$ m, $V=30$ m/s, $C_D=0.024+0.058C_L^2$, $V_2=21.6$ m/s, climb rate 2.4 m/s and $\mu=0.18$. These give $y_{TO}=0.5197$ and a lower root of 30.31 N/m², which matches the sheet's Solver value of 30.3078 (F11).

## Question 37

The same UAV must take off on a runway of 98 m and cruise at 38 m/s, with

$$
C_D=0.021+0.057C_L^2 .
$$

$V_2$ is 19.8 m/s and the rolling coefficient of friction is 0.16. Find the lowest wing loading that gives the minimum required thrust to weight ratio, to one decimal place in N/m².

Take-off line:

$$
\begin{aligned}
y_{TO}&=\frac{19.8^2}{2(9.81)(98)}+0.16\\
&=\frac{392.04}{1922.76}+0.16\\
&=0.20389+0.16=0.36389 .
\end{aligned}
$$

For cruise $n=1$ and $V_V=0$, with $q=\frac12(1.225)(38^2)=884.45$ Pa:

$$
a=\frac kq=\frac{0.057}{884.45}=6.4447\times10^{-5},\qquad b=0.36389,\qquad c=884.45\times0.021=18.573 .
$$

$$
b^2-4ac=0.132419-4(6.4447\times10^{-5})(18.573)=0.132419-0.004788=0.127631 .
$$

$$
x=\frac{0.36389-\sqrt{0.127631}}{2(6.4447\times10^{-5})}=\frac{0.36389-0.35726}{1.28894\times10^{-4}}=51.51\ \text{N/m}^2 .
$$

$$
\boxed{W/S=51.5\ \text{N/m}^2}
$$

> [!check] Substitution
> At $x=51.51$: $18.573/51.51+6.4447\times10^{-5}\times51.51=0.36058+0.00332=0.36390=y_{TO}$. The small induced term shows that near the left crossing the curve is almost pure profile drag, $x\approx qC_{D0}/y_{TO}=51.04$; the quadratic adds the last 1 %.

The workbook sheet holds $s_1=96$ m, $V=37$ m/s, $C_D=0.022+0.059C_L^2$, $V_2=21.9$ m/s and $\mu=0.18$. These give $y_{TO}=0.4346$ and a lower root of 42.74 N/m², matching the sheet's Solver value of 42.7389 (F11).

## Answer summary

| Question | Pairing | $y_{TO}$ | $a$ | $b$ | $c$ | $W/S$ (N/m²) |
|---:|---|---:|---:|---:|---:|---:|
| 35 | take-off and 2 g turn | 0.4402 | $3.874\times10^{-4}$ | 0.4402 | 14.13 | 33.1 |
| 36 | take-off and climb | 0.5049 | $7.909\times10^{-5}$ | 0.3166 | 15.58 | 49.8 |
| 37 | take-off and cruise | 0.3639 | $6.445\times10^{-5}$ | 0.3639 | 18.57 | 51.5 |

Questions 38 and 39 of the workbook use the same UAV wording but ask only for the take-off $T/W$ and the approach-limited wing loading; they are solved in [[SESA1015 T02 - Take-off and Landing Solutions#Question 38]] and [[SESA1015 T02 - Take-off and Landing Solutions#Question 39]].

## Sources

- Revision workbook, sheets Question 35, 36 and 37 (wording in column A; Solver layouts in columns B–G)
- Theory: [[SESA1015 M12 - Aircraft Constraint Analysis]]; Slides v1, pp. 220–222 (turn, take-off and climb constraints); course notes §7.3, p. 40 (ground run)
- All numbers recomputed in Python; the crossing figure is drawn by `01 - Notes/Figures/generate_mof_m12_figures.py`
