---
title: "SESA1015 T01 - Stall and Level-Flight Solutions"
module: "SESA1015 Intro to Aero & Astro"
type: tutorial-solutions
stream: "Mechanics of Flight revision workbook"
order: 1
tags: [sesa1015, tutorial, stall, level-flight]
aliases: ["SESA1015 Revision Q1 Q2 Q4 Q14 Q15 Q30 Q42"]
date: 2026-09-27
status: complete
parent: ["[[SESA1015 Intro to Aero & Astro Hub]]"]
prerequisites: ["[[SESA1015 M01 - Atmosphere, Airspeed and Mach Number]]", "[[SESA1015 M04 - Steady Level Flight and Stall]]", "[[SESA1015 M05 - Minimum Drag, Power and Performance Curves]]"]
theory_notes: ["[[SESA1015 M04 - Steady Level Flight and Stall]]", "[[SESA1015 M05 - Minimum Drag, Power and Performance Curves]]"]
key_concepts: ["[[Stalling Speed]]", "[[Wing Loading]]", "[[Parabolic Drag Polar]]", "[[Minimum Drag and Minimum Power]]"]
sources: ["04 - Labs & Coursework/Revision & Spreadsheets/SESA1015 - Revision Questions (Original).xlsx (sheets Question 1, 2, 4, 14, 15, 30, 42)"]
---

# SESA1015 T01 - Stall and Level-Flight Solutions

> [!abstract] Sheet info
> Revision workbook Questions 1, 2, 4, 14, 15, 30 and 42: stalling speed and wing loading, induced drag in level flight, the minimum-drag and minimum-power speeds, cruise wing loading and the lift-to-drag ratio. Each solution uses the numbers in the question wording. The spreadsheet's input cells under several questions hold a different, randomised set of numbers; those are noted under each question with the answer they give. Constants: $g=9.81$ m/s², $\rho_0=1.225$ kg/m³, $\gamma=1.4$, $R=287$ J/(kg K), $T_0=288.15$ K. Every number was recomputed in Python.

Theory: [[SESA1015 M04 - Steady Level Flight and Stall]] (Questions 1, 2, 4, 30, 42) and [[SESA1015 M05 - Minimum Drag, Power and Performance Curves]] (Questions 14, 15).

## Question 1

An aircraft has $C_{L\max}=1.75$ (at stall) and a wing loading of 4981 N/m². (a) To reduce the stalling speed by 14%, what must the wing loading be changed to? (b) What is its true stalling speed at an altitude where $\sigma=0.75$?

(a) In level flight at the stall, $W=\tfrac12\rho V_S^2SC_{L\max}$, so

$$
\frac WS=\tfrac12\rho V_S^2C_{L\max}.
$$

At fixed density and $C_{L\max}$ the wing loading is proportional to $V_S^2$, and a 14% reduction means $V_{S,new}=0.86\,V_{S,old}$:

$$
\begin{aligned}
\frac{(W/S)_{new}}{(W/S)_{old}}&=\left(\frac{V_{S,new}}{V_{S,old}}\right)^2=0.86^2=0.7396,\\
(W/S)_{new}&=4981\times0.7396=3683.9\ \text{N/m}^2 .
\end{aligned}
$$

A 14% cut in stalling speed needs a 26% cut in wing loading, because the speed goes as the square root.

(b) The density is $\rho=\sigma\rho_0=0.75\times1.225=0.91875$ kg/m³. With the stated wing loading of 4981 N/m²,

$$
\begin{aligned}
V_S&=\left(\frac{2(W/S)}{\rho C_{L\max}}\right)^{1/2}=\left(\frac{2(4981)}{0.91875(1.75)}\right)^{1/2}\\
&=\sqrt{6195.9}=78.71\ \text{m/s}.
\end{aligned}
$$

At sea level the same aircraft stalls at $\sqrt{2(4981)/(1.225\times1.75)}=68.17$ m/s, which is also its equivalent stalling speed at every altitude: $78.71\sqrt{0.75}=68.17$ m/s. If part (b) is meant for the new wing loading, the answer is $0.86\times78.71=67.69$ m/s. The spreadsheet uses the original wing loading.

> [!note] Spreadsheet inputs
> The input cells hold $C_{L\max}=1.61$, $W/S=5370$ N/m², a 10% reduction and $\sigma=0.63$, which give 4349.7 N/m² and 92.97 m/s.

## Question 2

The wording is identical to Question 1, so the answers are the same: $(W/S)_{new}=3683.9$ N/m² and $V_S=78.71$ m/s at $\sigma=0.75$ ([[#Question 1]]).

> [!note] Spreadsheet inputs
> This sheet's input cells hold $C_{L\max}=1.61$, $W/S=4564$ N/m², a 14% reduction and $\sigma=0.67$, which give 3375.5 N/m² and 83.11 m/s.

## Question 4

An aircraft in steady level flight at 57 m/s and $9^\circ$ angle of attack speeds up to 103 m/s. $C_L$ is proportional to angle of attack and equals 1.0 at $9^\circ$. What is the new induced drag divided by the original? (Three decimal places.)

In level flight $L=W$ at both speeds, at the same density, so

$$
C_L=\frac{2W}{\rho V^2S}\quad\Rightarrow\quad\frac{C_{L2}}{C_{L1}}=\left(\frac{V_1}{V_2}\right)^2 .
$$

The induced drag is $D_i=\tfrac12\rho V^2S\,KC_L^2$. Substituting $C_L$,

$$
\begin{aligned}
D_i&=\tfrac12\rho V^2S\,K\,\frac{4W^2}{\rho^2V^4S^2}\\
&=\frac{2KW^2}{\rho S}\,\frac1{V^2},
\end{aligned}
$$

so at fixed weight and density $D_i\propto1/V^2$:

$$
\frac{D_{i2}}{D_{i1}}=\left(\frac{V_1}{V_2}\right)^2=\left(\frac{57}{103}\right)^2=0.306 .
$$

The induced drag falls to 30.6% of its original value, a reduction of 69.4%. The angle-of-attack data are not needed for the ratio; they show that the new lift coefficient is $1.0\times0.3062=0.306$, at $\alpha=9\times0.3062=2.76^\circ$.

> [!note] Spreadsheet inputs
> The input cells use 55 and 91 m/s, which give $(55/91)^2=0.365$.

## Question 14

An aircraft of mass 8207 kg has a wing area of 30 m² and flies where $\sigma=0.43$, with $C_D=0.02+0.044C_L^2$. What is the minimum power speed? (m/s, two decimal places.)

The power required is $P=DV$. With $D=W\,C_D/C_L$ and $V=\sqrt{2W/\rho SC_L}$,

$$
P=W\,\frac{C_D}{C_L}\left(\frac{2W}{\rho SC_L}\right)^{1/2}=\left(\frac{2W^3}{\rho S}\right)^{1/2}\frac{C_D}{C_L^{3/2}},
$$

so minimum power needs the minimum of $C_D/C_L^{3/2}=C_{D0}C_L^{-3/2}+KC_L^{1/2}$. Differentiating and setting to zero,

$$
\begin{aligned}
-\tfrac32C_{D0}C_L^{-5/2}+\tfrac12KC_L^{-1/2}&=0\\
KC_L^2&=3C_{D0}\\
C_{L,MP}&=\sqrt{\frac{3C_{D0}}{K}} .
\end{aligned}
$$

Here $C_{L,MP}=\sqrt{3(0.02)/0.044}=1.1677$. With $W=8207\times9.81=80\,511$ N and $\rho=0.43\times1.225=0.52675$ kg/m³,

$$
V_{MP}=\left(\frac{2W}{\rho SC_{L,MP}}\right)^{1/2}=\left(\frac{2(80\,511)}{0.52675(30)(1.1677)}\right)^{1/2}=93.41\ \text{m/s}.
$$

As a check, $V_{MP}=V_{MD}/3^{1/4}$: $V_{MD}=122.94$ m/s and $122.94/1.3161=93.41$ m/s. See [[SESA1015 M05 - Minimum Drag, Power and Performance Curves]].

> [!note] Spreadsheet inputs
> The input cells hold $m=8052$ kg, $\sigma=0.52$, $S=31$ m² and $K=0.052$, which give 86.30 m/s.

## Question 15

An aircraft weighing 82 151 N flies where $\rho=0.68$ kg/m³. Its wing loading is 4586 N/m² and $C_D=0.022+0.045C_L^2$. At what true airspeed should it fly to minimise its drag? (m/s, one decimal place.)

In level flight $D=W\,C_D/C_L$, so at fixed weight the drag is least where $C_D/C_L=C_{D0}/C_L+KC_L$ is least:

$$
\begin{aligned}
\frac{d}{dC_L}\left(\frac{C_{D0}}{C_L}+KC_L\right)&=-\frac{C_{D0}}{C_L^2}+K=0\\
C_{L,MD}&=\sqrt{\frac{C_{D0}}{K}}=\sqrt{\frac{0.022}{0.045}}=0.6992 .
\end{aligned}
$$

The speed follows from the lift balance written with the wing loading:

$$
V_{MD}=\left(\frac{2(W/S)}{\rho C_{L,MD}}\right)^{1/2}=\left(\frac{2(4586)}{0.68(0.6992)}\right)^{1/2}=138.9\ \text{m/s}.
$$

The weight itself is not needed once the wing loading is given; it fixes $S=82\,151/4586=17.9$ m². At this speed $C_D=2C_{D0}=0.044$ and $L/D=15.9$.

> [!note] Spreadsheet inputs
> The input cells hold $W=86\,515$ N, $\rho=0.59$, $W/S=4809$ N/m², $C_{D0}=0.021$ and $K=0.046$, which give 155.3 m/s.

## Question 30

What is the wing loading of an aircraft designed to cruise at Mach 0.61 at 11 000 m (density ratio 0.297, temperature ratio 0.75) with a cruise lift coefficient of 0.23? (Units N m⁻².)

The local temperature, density and speed of sound are

$$
\begin{aligned}
T&=0.75\times288.15=216.11\ \text{K},\\
\rho&=0.297\times1.225=0.36383\ \text{kg/m}^3,\\
a&=\sqrt{\gamma RT}=\sqrt{1.4(287)(216.11)}=294.68\ \text{m/s},
\end{aligned}
$$

so $V=Ma=0.61\times294.68=179.75$ m/s. In level flight $W=\tfrac12\rho V^2SC_L$, so

$$
\begin{aligned}
\frac WS&=\tfrac12\rho V^2C_L=\tfrac12(0.36383)(179.75)^2(0.23)\\
&=5877.8\times0.23=1351.9\ \text{N m}^{-2}.
\end{aligned}
$$

The dynamic pressure at the cruise point is 5878 Pa; any wing loading above $5878\,C_{L\max}$ could not be carried at this speed and height. See [[Wing Loading]].

> [!note] Spreadsheet inputs
> The input cells hold $M=0.6$ and $C_L=0.46$, which give 2615.8 N m⁻².

## Question 42

What is the lift-to-drag ratio of an aircraft flying at 25 m/s where $\sigma=0.81$, with a wing span of 2.2 m, aspect ratio 7.1, mass 27 kg and drag coefficient 0.084? (Two decimal places.)

The wing area and density are

$$
S=\frac{b^2}{AR}=\frac{2.2^2}{7.1}=0.68169\ \text{m}^2,\qquad\rho=0.81\times1.225=0.99225\ \text{kg/m}^3 .
$$

In level flight $L=W=27\times9.81=264.87$ N, and the dynamic pressure is $q=\tfrac12(0.99225)(25)^2=310.08$ Pa, so

$$
C_L=\frac{W}{qS}=\frac{264.87}{310.08\times0.68169}=1.2531 .
$$

Lift and drag share the factor $qS$, so

$$
\frac LD=\frac{C_L}{C_D}=\frac{1.2531}{0.084}=14.92 .
$$

The drag is $D=qSC_D=17.76$ N, and $264.87/17.76=14.92$ again.

> [!note] Spreadsheet inputs
> The input cells hold $V=26$ m/s, $b=2.3$ m, $AR=8.2$, $m=15$ kg and $C_D=0.099$, which give 6.87.

## Answer check

| Question | Answer |
|---:|---|
| 1 | 3683.9 N/m²; 78.71 m/s |
| 2 | as Question 1 |
| 4 | 0.306 |
| 14 | 93.41 m/s |
| 15 | 138.9 m/s |
| 30 | 1351.9 N m⁻² |
| 42 | 14.92 |

## Sources

- Revision workbook `SESA1015 - Revision Questions (Original).xlsx`, sheets Question 1, 2, 4, 14, 15, 30 and 42 (wording in column A; input cells noted where they differ)
- Theory: [[SESA1015 M04 - Steady Level Flight and Stall]], [[SESA1015 M05 - Minimum Drag, Power and Performance Curves]], [[SESA1015 M01 - Atmosphere, Airspeed and Mach Number]]
