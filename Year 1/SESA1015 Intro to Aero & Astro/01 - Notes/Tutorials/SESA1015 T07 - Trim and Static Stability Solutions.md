---
title: "SESA1015 T07 - Trim and Static Stability Solutions"
module: "SESA1015 Intro to Aero & Astro"
type: tutorial-solutions
stream: "Mechanics of Flight revision workbook"
order: 7
tags: [sesa1015, tutorial, trim, static-stability, tailplane]
aliases: ["SESA1015 Revision Q8 Q13", "Trim and Static Stability Solutions"]
date: 2026-09-27
status: complete
parent: ["[[SESA1015 Intro to Aero & Astro Hub]]"]
prerequisites: ["[[SESA1015 M11 - Longitudinal Trim and Static Stability]]"]
sources: ["04 - Labs & Coursework/Revision & Spreadsheets/SESA1015 - Revision Questions (Original).xlsx (sheets Question 8, 13)", "02 - Sources/Mechanics of Flight/Mechanics of Flight - Course Notes.pdf (§8.1–8.2)"]
---

# SESA1015 T07 - Trim and Static Stability Solutions

Worked solutions to the trim and static-stability questions of the revision workbook. The question wording is authoritative; where the workbook's input cells hold different (randomised) numbers, the spreadsheet's own answer is given too. The theory, with the notation of the course notes ($h$, $h_0$, $\bar V$, $a_1$, $a_{1T}$) and the slides ($h_{ac}$, $V_{HT}$, $a$, $a_T$), is in [[SESA1015 M11 - Longitudinal Trim and Static Stability]].

## Question 8

A small UAV has a conventional tail with symmetrical sections, 0.93 m aft of the main wing (between aerodynamic centres). The wing has $C_L=4.92(\alpha+2/57.3)$ and the tailplane $C_{L_T}=5.02\alpha_T$, with $\alpha$ in radians. The CG is at 0.51 of the mean chord behind the wing leading edge. The wing has aspect ratio 7.0 and area 1.39 m², and generates downwash $d\varepsilon/d\alpha=0.21$. The aerodynamic centres are at the quarter chord. Find the tailplane area for a static margin of 0.18, to three decimal places.

The static margin fixes where the neutral point has to be, the neutral-point formula then fixes the tail volume coefficient, and the geometry turns that into an area.

The CG is at $h=0.51$ and the margin is $K_n=h_n-h=0.18$, so

$$
h_n=0.51+0.18=0.69 .
$$

The neutral point (stick fixed) is

$$
h_n=h_0+\bar V\,\frac{a_{1T}}{a_1}\left(1-\frac{d\varepsilon}{d\alpha}\right),
$$

with $h_0=0.25$, $a_1=4.92$ and $a_{1T}=5.02$ per radian. The constant $2/57.3$ in the wing's lift equation only sets its zero-lift angle ($-2°$) and does not affect the slope, so it plays no part. Solve for $\bar V$:

$$
\bar V=(h_n-h_0)\,\frac{a_1}{a_{1T}}\,\frac{1}{1-d\varepsilon/d\alpha}=0.44\times\frac{4.92}{5.02}\times\frac{1}{0.79}=0.44\times0.98008\times1.26582=0.54587 .
$$

The mean chord is the area divided by the span. With $A=b^2/S$, $b=\sqrt{AS}$ and

$$
\bar c=\frac{S}{b}=\sqrt{\frac{S}{A}}=\sqrt{\frac{1.39}{7.0}}=0.44561\ \text{m},\qquad S\bar c=1.39\times0.44561=0.61940\ \text{m}^3 .
$$

From $\bar V=S_Tl_T/(S\bar c)$,

$$
S_T=\bar V\,\frac{S\bar c}{l_T}=0.54587\times\frac{0.61940}{0.93}=\boxed{0.364\ \text{m}^2}\quad(0.36356\ \text{m}^2).
$$

> [!check] Back-substitution
> $\bar V=0.36356\times0.93/0.61940=0.54587$, and $h_n=0.25+0.54587\times(5.02/4.92)\times0.79=0.25+0.44000=0.69000$, so $K_n=0.18$.

The same method is the Slides v2 p. 211 example, which gives 0.268 m² ([[SESA1015 M11 - Longitudinal Trim and Static Stability#Tail area for a given static margin (Slides v2 p. 211)]]). The workbook sheet carries the note that a static-margin question will be in the exam (cell J15).

> [!warning] Spreadsheet input cell disagrees with the wording
> The sheet's inputs are $h=0.46$, $A=9.8$, $S=1.1$ m², $d\varepsilon/d\alpha=0.17$, $K_n=0.16$, $a_1=5.01$, $a_{1T}=5.07$, $l_T=1.03$ m, and the cell labelled "quarter chord" holds 0.46 instead of 0.25. The sheet therefore uses $h_n-h_0=0.16$ and returns $S_T=0.0682$ m². With $h_0=0.25$ the same inputs give $\bar V=0.4405$ and $S_T=0.158$ m². Check the "quarter chord" cell before trusting the sheet's answer.

## Question 13

An aircraft flies level and trimmed with its CG at the aerodynamic centre of the wing/fuselage. The pitching moment coefficient of the wing/fuselage about its aerodynamic centre is $-0.094$. The symmetric horizontal stabiliser has a gross area 0.22 times the wing area and its aerodynamic centre is 4.7 main-wing chords behind the CG. The stabiliser's lift-curve slope is 0.088 per degree. Find its trim angle, to two decimal places.

Start from the moment about the CG with a tailplane,

$$
C_{m_G}=C_{m0}+(h-h_0)\,C_L-\bar V\,C_{L_T}.
$$

The CG is at the wing/fuselage AC, so $h=h_0$ and the wing lift has no moment arm; the moment arm of the tail, measured from the AC, is then also its distance from the CG, $l_T=4.7\bar c$. The tail volume coefficient is

$$
\bar V=\frac{S_T}{S}\,\frac{l_T}{\bar c}=0.22\times4.7=1.034 .
$$

Trim needs $C_{m_G}=0$:

$$
0=C_{m0}-\bar V\,C_{L_T}\quad\Rightarrow\quad C_{L_T}=\frac{C_{m0}}{\bar V}=\frac{-0.094}{1.034}=-0.09091 .
$$

The stabiliser has a symmetric section, so its lift is zero at zero angle of attack and $C_{L_T}=a_T\alpha_T$:

$$
\alpha_T=\frac{C_{L_T}}{a_T}=\frac{-0.09091}{0.088}=\boxed{-1.03°}\quad(-1.0331°).
$$

The wing/fuselage moment is nose down ($C_{m0}<0$), so the tail must push down to balance it: negative tail lift at a negative angle of attack, which makes a nose-up moment $-\bar VC_{L_T}=+0.094$. The total lift is then slightly less than the wing lift, so the wing has to carry the weight plus the 0.0909 × 0.22 = 0.0200 of $C_L$ the tail takes away (trim drag).

The workbook's input cells match the wording and give $-1.0331°$.

## Answer summary

| Question | Topic | Answer (wording) | Spreadsheet gives |
|---:|---|---:|---:|
| 8 | tail area for $K_n=0.18$ | 0.364 m² | 0.0682 m² (wrong $h_0$ cell) |
| 13 | stabiliser trim angle | $-1.03°$ | $-1.03°$ |

## Related

- Theory: [[SESA1015 M11 - Longitudinal Trim and Static Stability]] · [[Static Margin and Tail Volume]] · [[Elevator Angle to Trim]]
- Workbook index: [[SESA1015 Revision Workbook Coverage]]
- Later: [[SESA2022 Examples Sheet 6 - Static Stability Solutions]]
