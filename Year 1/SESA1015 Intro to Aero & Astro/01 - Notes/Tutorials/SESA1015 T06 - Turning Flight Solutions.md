---
title: "SESA1015 T06 - Turning Flight Solutions"
module: "SESA1015 Intro to Aero & Astro"
type: tutorial-solutions
stream: "Mechanics of Flight revision workbook"
order: 6
tags: [sesa1015, tutorial, turning-flight, load-factor]
aliases: ["SESA1015 Revision Q6 Q25 Q26 Q31", "Turning Flight Solutions"]
date: 2026-09-27
status: complete
parent: ["[[SESA1015 Intro to Aero & Astro Hub]]"]
prerequisites: ["[[SESA1015 M10 - Turning Flight and Manoeuvre Performance]]"]
sources: ["04 - Labs & Coursework/Revision & Spreadsheets/SESA1015 - Revision Questions (Original).xlsx (sheets Question 6, 25, 26, 31)", "02 - Sources/Mechanics of Flight/Mechanics of Flight - Course Notes.pdf (§7.4)"]
---

# SESA1015 T06 - Turning Flight Solutions

Worked solutions to the turning-flight questions of the revision workbook. The question wording is authoritative; where the workbook's input cells hold different (randomised) numbers, the spreadsheet's own answer is given as well so a mismatch can be recognised. All four questions use a level co-ordinated turn at sea level, $\rho=1.225$ kg/m³ and $g=9.81$ m/s². The theory is in [[SESA1015 M10 - Turning Flight and Manoeuvre Performance]].

## Question 6

A fighter performs a 6 g horizontal co-ordinated turn at 381 knots. The wing loading is 3709 N/m², the wing area 30 m², and $C_D=0.01+0.07C_L^2$. Find the thrust required, to the nearest newton.

"6 g" means a load factor $n=L/W=6$. The turn is steady, so the thrust must equal the drag in the turn, and the drag is found from the lift coefficient the turn needs.

Speed in SI units, with 1 kn $=0.514444$ m/s:

$$
V=381\times0.514444=196.00\ \text{m/s}.
$$

Dynamic pressure and weight:

$$
q=\tfrac12\rho V^2=\tfrac12\times1.225\times196.00^2=23\,531\ \text{Pa},\qquad W=\frac{W}{S}\,S=3709\times30=111\,270\ \text{N}.
$$

In the turn $L=nW$, so

$$
C_L=\frac{nW}{qS}=\frac{n\,(W/S)}{q}=\frac{6\times3709}{23\,531}=0.9457.
$$

The drag coefficient and the thrust:

$$
C_D=0.01+0.07\times0.9457^2=0.01+0.06261=0.07261,
$$

$$
T=D=qSC_D=23\,531\times30\times0.07261=\boxed{51\,257\ \text{N}}.
$$

Of this, the zero-lift drag is $qSC_{D0}=7059$ N and the induced drag 44 198 N. In level flight at the same speed $C_L=0.1576$ and the drag is only 8287 N, so the 6 g turn multiplies the induced drag by $n^2=36$. The turn radius is $196.0^2/(9.81\sqrt{35})=662$ m at a bank of 80.4°.

> [!check] Same answer through the thrust-limited radius formula
> The workbook computes the thrust as $(T-D_L)+D_L$, with $T-D_L$ from $R=\big(2KW^2V^2/\rho Sg^2\big)^{1/2}/\sqrt{T-D_L}$ and $R=V^2/(g\sqrt{n^2-1})$. That is the same physics, since $T-D_L=(KW^2/qS)(n^2-1)$: here $1227.7\times35=42\,970$ N, and $42\,970+8287=51\,257$ N.

The workbook's input cells use $n=7$, 356 kn, $W/S=3877$ N/m² and $S=31$ m², which give 84 166 N.

## Question 25

Calculate the minimum radius of turn for an aircraft at 82 m/s, assuming it is stall limited, where the stalling speed is 44 m/s. Give the answer to the nearest whole number.

At the stall limit the wing works at $C_{L,max}$, so the largest load factor at speed $V$ is $n=L_{max}/W=(V/V_S)^2$ (the level-flight stall speed $V_S$ is where $L_{max}=W$). Substituting into $R=V^2/(g\sqrt{n^2-1})$ gives the stall-limited radius:

$$
R_{min}=\frac{V^2}{g\sqrt{(V/V_S)^4-1}}.
$$

Here $V/V_S=82/44=1.8636$, so $n=3.473$ and $(V/V_S)^4=12.063$:

$$
R_{min}=\frac{82^2}{9.81\sqrt{12.063-1}}=\frac{6724}{9.81\times3.3261}=\boxed{206\ \text{m}}\quad(206.08\ \text{m}).
$$

The bank angle is $\cos^{-1}(1/3.473)=73.3°$. The workbook's input cells use $V=103$ m/s and $V_S=59$ m/s, which give 375.6 m.

## Question 26

Calculate the minimum radius of turn, in metres to one decimal place, for an aircraft at 106 m/s, assuming it is stall (lift) limited, where the stalling speed is 60 m/s.

The same formula as [[#Question 25]]. With $V/V_S=106/60=1.7667$, $n=3.1211$ and $(V/V_S)^4=9.7414$:

$$
R_{min}=\frac{106^2}{9.81\sqrt{9.7414-1}}=\frac{11\,236}{9.81\times2.9566}=\boxed{387.4\ \text{m}}.
$$

The bank angle is 71.3°. The workbook's input cells use $V=103$ m/s with $V_S=60$ m/s, which give 390.1 m.

> [!tip] Why the stall-limited radius barely changes with speed
> Both questions sit well above the stall speed, where the stall-limited radius is already close to its floor $V_S^2/g$ (197 m for Q25, 367 m for Q26). Doubling the speed from there hardly changes the radius, because the extra lift available grows as $V^2$ just as fast as the centripetal force needed.

## Question 31

An aircraft has 534 N of excess thrust over that needed for steady level flight at low altitude and 109 m/s. Its weight is 5322 N, its wing area 14 m², and $C_D=0.024+0.057C_L^2$. What is the thrust-limited minimum radius of turn, to the nearest metre?

The turn is held at the same speed, so the zero-lift drag $qSC_{D0}$ is unchanged and the excess thrust $T-D_L$ must pay for the extra induced drag. From [[SESA1015 M10 - Turning Flight and Manoeuvre Performance#Derivation|the derivation in M10]],

$$
R_{min}=\left(\frac{2KW^2V^2}{\rho Sg^2}\right)^{1/2}\frac{1}{\sqrt{T-D_L}},
$$

with $K=0.057$ and $T-D_L=534$ N. The first factor:

$$
\frac{2KW^2V^2}{\rho Sg^2}=\frac{2\times0.057\times5322^2\times109^2}{1.225\times14\times9.81^2}=\frac{3.8363\times10^{10}}{1650.4}=2.3244\times10^{7},
$$

whose square root is 4821.2 (units N$^{1/2}$ m). Then

$$
R_{min}=\frac{4821.2}{\sqrt{534}}=\frac{4821.2}{23.108}=\boxed{209\ \text{m}}\quad(208.63\ \text{m}).
$$

The value of $C_{D0}$ is not needed, because the question gives the excess thrust directly.

> [!check] Load factor in this turn
> From $(KW^2/qS)(n^2-1)=T-D_L$: the level-flight induced drag is $KW^2/(qS)=15.85$ N, so $n^2-1=534/15.85=33.70$ and $n=5.89$. Then $R=V^2/(g\sqrt{n^2-1})=109^2/(9.81\times5.805)=208.6$ m, the same radius. The induced drag in level flight is tiny at this speed, which is why 534 N buys almost 6 g; a real airframe would need checking against its stall and structural limits.

The workbook's input cells use 405 N, 103 m/s, $W=5288$ N, $S=11$ m² and $K=0.059$, which give 258.2 m.

## Answer summary

| Question | Topic | Answer (wording) | Spreadsheet inputs give |
|---:|---|---:|---:|
| 6 | thrust in a 6 g turn | 51 257 N | 84 166 N |
| 25 | stall-limited radius | 206 m | 375.6 m |
| 26 | stall-limited radius | 387.4 m | 390.1 m |
| 31 | thrust-limited radius | 209 m | 258.2 m |

## Related

- Theory: [[SESA1015 M10 - Turning Flight and Manoeuvre Performance]] · [[Load Factor and Turn Performance]]
- Workbook index: [[SESA1015 Revision Workbook Coverage]]
- Turn constraint in a constraint diagram: [[SESA1015 T08 - Constraint Analysis Solutions]]
