---
title: "SESA1015 T05 - Climb and Glide Solutions"
module: "SESA1015 Intro to Aero & Astro"
type: tutorial-solutions
stream: "Mechanics of Flight revision workbook"
order: 5
tags: [sesa1015, tutorial, climb, glide]
aliases: ["SESA1015 Revision Q17 Q18", "Climb and Glide Solutions"]
date: 2026-09-27
status: complete
parent: ["[[SESA1015 Intro to Aero & Astro Hub]]"]
prerequisites: ["[[SESA1015 M08 - Glide and Climb Performance]]"]
sources: ["04 - Labs & Coursework/Revision & Spreadsheets/SESA1015 - Revision Questions (Original).xlsx (Questions 17, 18)"]
---

# SESA1015 T05 - Climb and Glide Solutions

> [!abstract] Method used throughout
> Both workbook questions use the steady-climb balance of [[SESA1015 M08 - Glide and Climb Performance#4. Steady climbing flight|M08 §4]], with climb angle $\theta$ and thrust vector angle $\gamma$:
>
> $$T\cos\gamma-D=W\sin\theta,\qquad\frac{dh}{dt}=V\sin\theta=\frac{V\,(T\cos\gamma-D)}{W}.$$
>
> Speeds in knots are converted with 1 kn = 0.5144 m s⁻¹ (Slides v2, p. 132); sea-level density $\rho_0=1.225$ kg m⁻³. The glide examples (minimum glide angle, glide distance, minimum sink) are worked in M08 itself: [[SESA1015 M08 - Glide and Climb Performance#Engine-out glide after a bird strike|bird-strike glide]] and [[SESA1015 M08 - Glide and Climb Performance#Best glide and minimum sink of a 15-tonne jet|15-tonne jet glide]].

## Question 17

An aircraft must climb steadily at 7 m s⁻¹ from sea level. Its wing loading is 5228 N m⁻², span 8 m, aspect ratio 3, speed 452 kn and $C_D=0.015+0.057C_L^2$. Find the thrust needed with a thrust angle of 9°, to the nearest newton.

The geometry, weight and speed are

$$
S=\frac{b^2}{AR}=\frac{8^2}{3}=21.333\ \text{m}^2,\qquad W=\frac WS\,S=5228\times21.333=111\,531\ \text{N},
$$

$$
V=452\times0.5144=232.51\ \text{m s}^{-1},\qquad q=\tfrac12\rho_0V^2=\tfrac12\times1.225\times232.51^2=33\,112\ \text{Pa}.
$$

The climb is shallow ($\sin\theta=7/232.51=0.0301$, $\theta=1.73^\circ$), so the lift coefficient comes from $L\approx W$:

$$
C_L=\frac{W/S}{q}=\frac{5228}{33\,112}=0.15789,
$$

$$
C_D=0.015+0.057\times0.15789^2=0.016421,
$$

$$
D=qSC_D=33\,112\times21.333\times0.016421=11\,600\ \text{N}.
$$

The along-path balance with $\sin\theta=(dh/dt)/V$ gives the thrust component along the path:

$$
T\cos\gamma=D+W\,\frac{1}{V}\frac{dh}{dt}=11\,600+111\,531\times\frac{7}{232.51}=11\,600+3358=14\,957\ \text{N}.
$$

Only the component $T\cos\gamma$ acts along the path, so the engine must supply

$$
T=\frac{14\,957}{\cos9^\circ}=\frac{14\,957}{0.98769}=15\,144\ \text{N}.
$$

$$
\boxed{T=15\,144\ \text{N}}
$$

With the exact conversion 1 kn = 0.514444 m s⁻¹ the answer is 15 145 N. Neglecting the thrust angle would give 14 957 N.

> [!check] Numerical check
> The inclined thrust also carries part of the weight: the normal balance is $L=W\cos\theta-T\sin\gamma\approx111\,480-2362=109\,118$ N once iterated, 2.2 % below $W$. Using this lift lowers $C_L$ to 0.1545, $D$ to 11 556 N and $T$ to 15 100 N, a 0.3 % change. The $L\approx W$ step is adequate here.

> [!note] Spreadsheet inputs
> The input cells use wing loading 4591 N m⁻², 472 kn, $C_D=0.019+0.042C_L^2$, climb rate 8 m s⁻¹ and angle 8°, and the sheet's formula $(\text{rate}\times W+VD)/V$ leaves out the $\cos\gamma$ division, giving 18 386 N (18 566 N with it).

## Question 18

An aircraft in a steady climb has thrust 45 770 N, wing loading 4793 N m⁻², span 14 m, wing area 72 m², speed 412 kn and drag 35 537 N. Find the climb rate, to 2 decimal places, if it uses its maximum thrust-vectoring capability of 79°.

The weight and speed are

$$
W=\frac WS\,S=4793\times72=345\,096\ \text{N},\qquad V=412\times0.5144=211.93\ \text{m s}^{-1}.
$$

The thrust component along the flight path is

$$
T\cos\gamma=45\,770\times\cos79^\circ=45\,770\times0.19081=8733\ \text{N},
$$

and the steady-climb result gives

$$
\frac{dh}{dt}=\frac{V\,(T\cos\gamma-D)}{W}=\frac{211.93\times(8733-35\,537)}{345\,096}=-16.46\ \text{m s}^{-1}.
$$

$$
\boxed{\frac{dh}{dt}=-16.46\ \text{m s}^{-1}\ \text{(a descent)}}
$$

With the thrust turned 79° from the flight path, its component along the path is far smaller than the drag, so no steady climb is possible: the aircraft descends at 16.46 m s⁻¹ along a path $\sin^{-1}(16.46/211.93)=4.5^\circ$ below the horizontal. The workbook carries a warning that thrust angles above about 35° give nonsense answers, and the angle in its input cells is 7°. With 7° the same formula gives

$$
\frac{dh}{dt}=\frac{211.93\times(45\,770\cos7^\circ-35\,537)}{345\,096}=\frac{211.93\times(45\,429-35\,537)}{345\,096}=6.07\ \text{m s}^{-1}
$$

(6.08 m s⁻¹ with 1 kn = 0.514444 m s⁻¹), which is the sensible climb this aircraft can achieve. The span is not needed.

> [!note] Spreadsheet inputs
> The input cells use $T=48\,198$ N, wing loading 4718 N m⁻², wing area 73 m², 409 kn, drag 36 036 N and 7°, giving 7.21 m s⁻¹.

## Answer check

| Question | Answer |
|---:|---|
| 17 | $T=15\,144$ N (15 145 N with the exact knot) |
| 18 | $-16.46$ m s⁻¹ as worded (79°); 6.07 m s⁻¹ with the workbook's 7° |

All values recomputed in Python from the question wording.

## Related

- Topic: [[SESA1015 M08 - Glide and Climb Performance]] · Concepts: [[Specific Excess Power and Rate of Climb]] · [[Glide Angle and Rate of Descent]] · [[Parabolic Drag Polar]]
