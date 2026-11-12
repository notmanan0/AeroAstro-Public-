---
title: "SESA1015 T02 - Take-off and Landing Solutions"
module: "SESA1015 Intro to Aero & Astro"
type: tutorial-solutions
stream: "Mechanics of Flight revision workbook"
order: 2
tags: [sesa1015, tutorial, takeoff, landing]
aliases: ["SESA1015 Revision Q3 Q7 Q19 Q21 Q22 Q23 Q24 Q28 Q38 Q39 Q40", "Take-off and Landing Solutions"]
date: 2026-09-27
status: complete
parent: ["[[SESA1015 Intro to Aero & Astro Hub]]"]
prerequisites: ["[[SESA1015 M09 - Take-off and Landing Performance]]"]
sources: ["04 - Labs & Coursework/Revision & Spreadsheets/SESA1015 - Revision Questions (Original).xlsx (Questions 3, 7, 19, 21–24, 28, 38–40)"]
---

# SESA1015 T02 - Take-off and Landing Solutions

> [!abstract] Method used throughout
> Every take-off question here uses the ground-run model of [[SESA1015 M09 - Take-off and Landing Performance#3. Ground run with lift and drag neglected|M09 §3]]: level runway, still air, $T/W$ constant, lift and drag small during the run, acceleration stopping at lift-off so $V_2\approx V_{LOF}$. Integrating $g(T/W-\mu_r)\,dx=V\,dV$ from rest gives
>
> $$s_1=\frac{V_2^2}{2g\left(\frac TW-\mu_r\right)},\qquad V_s=\sqrt{\frac{2W}{\rho SC_{L_{max}}}},\qquad V_2=kV_s .$$
>
> The question wording is used for every number, with $g=9.81$ m s⁻² and $\rho_0=1.225$ kg m⁻³. Where the workbook's input cells hold different (randomised) values, the spreadsheet answer is noted after the solution.

## Question 3

Find the total thrust a twin-engined aircraft needs to take off within a level 1500 m runway ($s_1$) at sea level, given $V_2=1.2V_s$, span 41.2 m, aspect ratio 11.7, $C_{L_{max}}=2.26$, take-off mass 70 856 kg and $\mu_r=0.02$. Answer to the nearest newton.

The wing area and weight are

$$
S=\frac{b^2}{AR}=\frac{41.2^2}{11.7}=145.08\ \text{m}^2,\qquad W=mg=70\,856\times9.81=695\,097\ \text{N},
$$

so the wing loading is $W/S=4791.1$ N m⁻². The stall and screen speeds are

$$
V_s=\sqrt{\frac{2(W/S)}{\rho_0C_{L_{max}}}}=\sqrt{\frac{2\times4791.1}{1.225\times2.26}}=58.832\ \text{m s}^{-1},\qquad V_2=1.2V_s=70.598\ \text{m s}^{-1}.
$$

Rearranging the ground-run formula for the thrust ratio,

$$
\frac TW-\mu_r=\frac{V_2^2}{2gs_1}=\frac{70.598^2}{2\times9.81\times1500}=0.169354,
$$

$$
\frac TW=0.169354+0.02=0.189354,
$$

$$
T=0.189354\times695\,097=131\,619\ \text{N}.
$$

$$
\boxed{T=131\,619\ \text{N}\ \text{(total)}}
$$

Each engine supplies half, 65 810 N.

> [!note] Spreadsheet inputs
> The workbook's input cells use span 44.3 m, aspect ratio 11.4, $C_{L_{max}}=1.83$ and mass 72 301 kg, which give 141 753 N.

## Question 7

A large four-engined passenger aircraft in take-off configuration has $V_2=1.19V_s$, $C_{L,TO}=1.7$, span 51 m, aspect ratio 8, $T/W=0.22$ (four engines) and take-off weight 2763 kN. The take-off is at sea level in the ISA on a runway with friction coefficient 0.01. Find the unstick distance with all engines operating, to the nearest metre.

$$
S=\frac{51^2}{8}=325.125\ \text{m}^2,\qquad\frac WS=\frac{2\,763\,000}{325.125}=8498.3\ \text{N m}^{-2},
$$

$$
V_s=\sqrt{\frac{2\times8498.3}{1.225\times1.7}}=90.342\ \text{m s}^{-1},\qquad V_2=1.19\times90.342=107.506\ \text{m s}^{-1},
$$

$$
s_1=\frac{107.506^2}{2\times9.81\times(0.22-0.01)}=\frac{11\,557.6}{4.1202}=2805\ \text{m}.
$$

$$
\boxed{s_1=2805\ \text{m}}
$$

> [!note] Spreadsheet inputs
> The input cells use $V_2=1.23V_s$, $C_L=1.6$, span 44 m, $T/W=0.27$ and 2801 kN, giving 3503 m.

## Question 19

Assuming $V_2\approx V_{LOF}\approx1.2V_s$, find the ground run for a stall speed of 123 m s⁻¹, $T/W=0.35$ and rolling resistance coefficient 0.06.

The stall speed is given directly, so no geometry is needed:

$$
V_2=1.2\times123=147.6\ \text{m s}^{-1},
$$

$$
s_1=\frac{147.6^2}{2\times9.81\times(0.35-0.06)}=\frac{21\,785.8}{5.6898}=3828.9\ \text{m}.
$$

$$
\boxed{s_1=3829\ \text{m}}
$$

> [!note] Spreadsheet inputs
> The input cells use $V_s=131$ m s⁻¹, $T/W=0.54$ and $\mu_r=0.02$, giving 2422 m.

## Question 21

Find the lift coefficient a Boeing 747-400 needs to take off on a level 2834 m runway ($s_1$) at sea level, with $V_2=1.2V_s$, span 64.5 m, aspect ratio 8.14, $T/W=0.27$ (all four engines), take-off mass 396 890 kg and $\mu_r=0.02$, using $s_1=V_2^2/[2g(T/W-\mu_r)]$. Answer to 2 decimal places.

This is the ground-run problem run backwards: runway to $V_2$, $V_2$ to $V_s$, $V_s$ to $C_L$. First,

$$
V_2^2=2gs_1\left(\frac TW-\mu_r\right)=2\times9.81\times2834\times(0.27-0.02)=13\,900.8\ \text{m}^2\,\text{s}^{-2},
$$

$$
V_2=117.90\ \text{m s}^{-1},\qquad V_s=\frac{V_2}{1.2}=98.251\ \text{m s}^{-1}.
$$

The stall equation $W=\frac12\rho_0V_s^2SC_{L}$ then gives the lift coefficient:

$$
S=\frac{64.5^2}{8.14}=511.09\ \text{m}^2,\qquad\frac WS=\frac{396\,890\times9.81}{511.09}=7618.1\ \text{N m}^{-2},
$$

$$
C_L=\frac{2(W/S)}{\rho_0V_s^2}=\frac{2\times7618.1}{1.225\times98.251^2}=1.288 .
$$

$$
\boxed{C_{L,TO}=1.29}
$$

> [!note] Spreadsheet inputs
> The input cells use $s_1=2914$ m, giving 1.25.

## Question 22

Find the lift coefficient a twin-engined aircraft needs to take off on a level 2614 m runway ($s_1$) at sea level, with $V_2=1.2V_s$, wing area 367 m², $T/W=0.30$ (both engines), take-off mass 224 152 kg and $\mu_r=0.02$. Answer to 3 decimal places.

$$
V_2^2=2\times9.81\times2614\times(0.30-0.02)=14\,360.3\ \text{m}^2\,\text{s}^{-2},\qquad V_2=119.834\ \text{m s}^{-1},\qquad V_s=99.862\ \text{m s}^{-1},
$$

$$
\frac WS=\frac{224\,152\times9.81}{367}=5991.6\ \text{N m}^{-2},
$$

$$
C_L=\frac{2\times5991.6}{1.225\times99.862^2}=0.981 .
$$

$$
\boxed{C_{L,TO}=0.981}
$$

> [!note] Spreadsheet inputs
> The input cells use $s_1=2718$ m, $S=372$ m², $T/W=0.29$ and mass 331 024 kg, giving 1.425.

## Question 23

Find the lift coefficient an aircraft needs to take off on a 1774 m runway ($s_1$) at sea level, with $V_2=1.28V_s$, span 70.9 m, aspect ratio 9, $T/W=0.25$ (four engines), take-off weight 5472 kN and $\mu_r=0.02$.

$$
V_2^2=2\times9.81\times1774\times(0.25-0.02)=8005.4\ \text{m}^2\,\text{s}^{-2},\qquad V_2=89.473\ \text{m s}^{-1},\qquad V_s=\frac{89.473}{1.28}=69.900\ \text{m s}^{-1},
$$

$$
S=\frac{70.9^2}{9}=558.53\ \text{m}^2,\qquad\frac WS=\frac{5\,472\,000}{558.53}=9797.1\ \text{N m}^{-2},
$$

$$
C_L=\frac{2\times9797.1}{1.225\times69.900^2}=3.274 .
$$

$$
\boxed{C_{L,TO}=3.274}
$$

A take-off $C_L$ above 3 is beyond what slotted flaps and slats normally give (2–2.5 is typical for an airliner). The data combine a high wing loading with a short runway and modest $T/W$, so the high-lift requirement is extreme; the answer is still the one the model gives.

> [!note] Spreadsheet inputs
> The input cells use $s_1=1709$ m, $V_2=1.11V_s$, span 50 m, $T/W=0.26$ and 4776 kN, giving 4.298.

## Question 24

Find the lift coefficient an aircraft needs to take off on a level 1800 m runway ($s_1$) at sea level, deriving any equations used, with $V_2=1.2V_s$, span 82.7 m, aspect ratio 9.7, $T/W=0.33$ (four engines), take-off weight 4 701 690 N and $\mu_r=0.02$. Answer to 3 decimal places.

The derivation is [[SESA1015 M09 - Take-off and Landing Performance#3. Ground run with lift and drag neglected|M09 §3]]: with $T/W$ constant and $L/W$, $D/W$ small, $g(T/W-\mu_r)\,dx=V\,dV$ integrates to $s_1=V_2^2/[2g(T/W-\mu_r)]$, and the stall equation gives $C_{L_{max}}=2(W/S)/(\rho V_s^2)$. Then

$$
V_2^2=2\times9.81\times1800\times(0.33-0.02)=10\,948.0\ \text{m}^2\,\text{s}^{-2},\qquad V_2=104.632\ \text{m s}^{-1},\qquad V_s=87.194\ \text{m s}^{-1},
$$

$$
S=\frac{82.7^2}{9.7}=705.08\ \text{m}^2,\qquad\frac WS=\frac{4\,701\,690}{705.08}=6668.3\ \text{N m}^{-2},
$$

$$
C_L=\frac{2\times6668.3}{1.225\times87.194^2}=1.432 .
$$

$$
\boxed{C_{L,TO}=1.432}
$$

The workbook's input cells match the wording here.

## Question 28

Find the percentage difference in ground roll at sea level between winter (5 °C) and summer (46 °C), treating air as a perfect gas, for an aircraft with $V_2=1.2V_s$, $V_s=69.41$ m s⁻¹, span 82 m, aspect ratio 9, $T/W=0.28$ (four engines), take-off weight 4500 kN and $\mu_r=0.02$ in both seasons.

The aircraft, its configuration and $T/W$ are the same in both seasons; only the air density changes. In the form

$$
s_1=\frac{1.44}{\rho g}\left(\frac WS\right)\left(\frac{1}{C_{L_{max}}}\right)\frac{1}{\left(\frac TW-\mu_r\right)}
$$

every factor except $1/\rho$ is the same, so $s_1\propto1/\rho$. The quoted stall speed fixes $C_{L_{max}}$ at standard sea-level density; the true stall speed on the day rises as the density falls. At the same sea-level pressure $p$, the perfect-gas law $\rho=p/(RT)$ gives $s_1\propto T$, so

$$
\frac{s_{summer}-s_{winter}}{s_{winter}}=\frac{T_{summer}}{T_{winter}}-1=\frac{319.15}{278.15}-1=0.14740 .
$$

$$
\boxed{\text{the summer ground roll is }14.74\ \%\text{ longer}}
$$

With numbers: $S=82^2/9=747.11$ m², $W/S=6023.2$ N m⁻², $C_{L_{max}}=2\times6023.2/(1.225\times69.41^2)=2.041$; with $p=101\,325$ Pa and $R=287$ J kg⁻¹ K⁻¹, $\rho_{winter}=1.2693$ and $\rho_{summer}=1.1062$ kg m⁻³, so $s_1=1312.5$ m in winter and 1506.0 m in summer, the same 14.74 %.

> [!note] Spreadsheet inputs
> The input cells use a summer temperature of 43 °C (and span 83 m, $T/W=0.29$, $V_s=68.01$ m s⁻¹, which cancel), giving $316.15/278.15-1=13.66$ %.

## Question 38

A small UAV's constraint diagram is being built for take-off within 85 m to lift-off and constant-speed turns at 29 m s⁻¹, with $C_D=0.020+0.056C_L^2$. Considering only the take-off constraint, with $V_2=21.8$ m s⁻¹, maximum load factor 2.4 and $\mu_r=0.18$, find the minimum $T/W$ for take-off to 2 decimal places.

Only the take-off constraint is asked for, so the drag polar, turn speed and load factor are not used. Rearranging the ground-run formula,

$$
\frac TW=\mu_r+\frac{V_2^2}{2gs_1}=0.18+\frac{21.8^2}{2\times9.81\times85}=0.18+\frac{475.24}{1667.7}=0.18+0.2850=0.4650 .
$$

$$
\boxed{T/W=0.46}
$$

The high friction coefficient (grass) supplies almost 40 % of the requirement. The full constraint diagram is in [[SESA1015 M12 - Aircraft Constraint Analysis]].

> [!note] Spreadsheet inputs
> The input cells use $s_1=65$ m and $V_2=19$ m s⁻¹, giving 0.46 as well (0.4631).

## Question 39

For the same kind of UAV (runway 82 m, turns at 32 m s⁻¹, $C_D=0.023+0.059C_L^2$), the approach speed is 16.7 m s⁻¹ and the maximum $C_L$ in the landing configuration is 1.10. Find the maximum wing loading to 2 decimal places.

The landing constraint treats the approach speed as the lowest speed at which the wing can still support the weight, so at that speed $L=W$ with $C_L=C_{L_{max}}$:

$$
W=\tfrac12\rho_0V_A^2SC_{L_{max}}
$$

$$
\frac WS=\tfrac12\rho_0V_A^2C_{L_{max}}=\tfrac12\times1.225\times16.7^2\times1.10=170.820\times1.10=187.90\ \text{N m}^{-2}.
$$

$$
\boxed{W/S\le187.90\ \text{N m}^{-2}}
$$

Any higher wing loading would need a faster approach. On the constraint diagram this is a vertical line, independent of $T/W$.

> [!note] Spreadsheet inputs
> The input cells use $V_A=17.4$ m s⁻¹ and $C_{L_{max}}=1.03$, giving 191.00 N m⁻².

## Question 40

The question is an image: a table compares two airliners (A: take-off weight 69 t, wing loading 3077 N m⁻²; B: 59 t, 4306 N m⁻²; range, thrust, fuel and passengers also listed). Assuming the minimum landing speed of both is 63 m s⁻¹, by what percentage is the $C_{L_{max}}$ of B greater than that of A, to the nearest whole number?

At the minimum landing speed each wing is at $C_{L_{max}}$ with $L=W$:

$$
\frac WS=\tfrac12\rho V_s^2C_{L_{max}}\quad\Rightarrow\quad C_{L_{max}}=\frac{2(W/S)}{\rho V_s^2}.
$$

With the same $V_s$ and $\rho$ for both, $C_{L_{max}}\propto W/S$ and everything else in the table is irrelevant:

$$
\frac{C_{L_{max},B}}{C_{L_{max},A}}=\frac{4306}{3077}=1.3994 .
$$

$$
\boxed{C_{L_{max}}\text{ of B is }40\ \%\text{ greater}}
$$

At sea level the values are $C_{L_{max},A}=2\times3077/(1.225\times63^2)=1.266$ and $C_{L_{max},B}=1.771$.

> [!note] Spreadsheet inputs
> The sheet's own cells hold wing loadings 3194 and 4364 N m⁻² with 50 m s⁻¹, giving 36.6 %.

## Answer check

| Question | Answer |
|---:|---|
| 3 | $T=131\,619$ N total (65 810 N per engine) |
| 7 | $s_1=2805$ m |
| 19 | $s_1=3829$ m |
| 21 | $C_L=1.29$ |
| 22 | $C_L=0.981$ |
| 23 | $C_L=3.274$ |
| 24 | $C_L=1.432$ |
| 28 | summer 14.74 % longer |
| 38 | $T/W=0.46$ |
| 39 | $W/S=187.90$ N m⁻² |
| 40 | 40 % |

All values recomputed in Python from the question wording.

## Related

- Topic: [[SESA1015 M09 - Take-off and Landing Performance]] · Concepts: [[Take-off Ground Run]] · [[Wing Loading]] · [[Take-off Reference Speeds]]
- Constraint-diagram versions of Q38 and Q39: [[SESA1015 M12 - Aircraft Constraint Analysis]] · [[SESA1015 T08 - Constraint Analysis Solutions]]
