---
title: "FEEG1002 Statics 1 Tutorial 5 - Beam Deflection and Statically Indeterminate Beams Solutions"
module: "FEEG1002 Mechanics, Materials and Structures"
type: tutorial
stream: "Part A: Statics 1"
tags: [feeg1002, tutorial-solutions, statics, deflection, macaulay, statically-indeterminate]
sheet: "Statics-1 Tutorial problem sheet 5"
theory_notes: ["[[FEEG1002 A5 - Beam Deflection and Macaulay's Method]]", "[[FEEG1002 A6 - Statically Indeterminate Beams]]"]
key_concepts: ["[[Macaulay's Method]]", "[[Superposition for Indeterminate Beams]]", "[[Standard Beam Deflections]]"]
status: complete
sources: ["02 - Sources/Statics 1/Tutorials/Tutorial Sheet 05 - Beam Deflection and Statically Indeterminate Beams.pdf", "02 - Sources/Statics 1/Tutorials/Tutorial Sheet 05 - Beam Deflection and Statically Indeterminate Beams - Solutions.pdf"]
---

# FEEG1002 Statics 1 Tutorial 5 - Beam Deflection and Statically Indeterminate Beams Solutions

> [!abstract] Sheet info
> Macaulay deflections (Q1, Q2 and additional Q1–Q2) and the reactions of indeterminate beams (Q3 and additional Q3). All printed answers are reproduced. Additional Q3 only asks for the equations; they are solved to completion here. Every deflection curve was also computed numerically with the beam solver in the figure script.

Theory: [[FEEG1002 A5 - Beam Deflection and Macaulay's Method]] · [[FEEG1002 A6 - Statically Indeterminate Beams]] · [[Macaulay's Method]]

The course convention is used throughout: $v$ is positive downwards, $M$ is positive sagging, and $EI\,d^2v/dx^2=-M$. Macaulay brackets $[x-a]^n$ are zero when $x<a$ and are integrated as a whole, never expanded.

---

## Q1 - Cantilever with a load at midspan

Taught in: [[FEEG1002 A5 - Beam Deflection and Macaulay's Method#4. Macaulay's method|A5, Macaulay's method]] · [[FEEG1002 A5 - Beam Deflection and Macaulay's Method#Procedure|A5, procedure]]

A cantilever of length $L$ is built in at $x=0$ and carries $F$ at $x=L/2$. The wall reactions are $R_A=F$ upwards and $M_A=FL/2$, anticlockwise.

**Bending moment.** Cut beyond the load and take moments about the cut for the left part:

$$
M+M_A-R_Ax+F[x-\tfrac L2]=0
$$

$$
M=-\frac{FL}{2}+Fx-F[x-\tfrac L2]
$$

**Integrate** $EIv''=-M$:

$$
EIv''=\frac{FL}{2}-Fx+F[x-\tfrac L2]
$$

$$
EIv'=\frac{FL}{2}x-\frac F2x^2+\frac F2[x-\tfrac L2]^2+C_1
$$

$$
EIv=\frac{FL}{4}x^2-\frac F6x^3+\frac F6[x-\tfrac L2]^3+C_1x+C_2
$$

The built-in end has $v'(0)=0$ and $v(0)=0$, so $C_1=C_2=0$. At the tip:

$$
v(L)=\frac{1}{EI}\left(\frac{FL^3}{4}-\frac{FL^3}{6}+\frac{FL^3}{48}\right)=\frac{5FL^3}{48EI}
$$

The outer half carries no moment, so it stays straight; the same answer follows from $v(L/2)+v'(L/2)\cdot L/2=\dfrac{FL^3}{24EI}+\dfrac{FL^2}{8EI}\cdot\dfrac L2$.

![[s1_t5_q1.png|680]]

## Q2 - Partial UDL and an overhang

Taught in: [[FEEG1002 A5 - Beam Deflection and Macaulay's Method#Worked example - partial UDL with an overhang|A5, partial UDL with an overhang]] · [[FEEG1002 A5 - Beam Deflection and Macaulay's Method#Writing the bending moment for other loads|A5, writing M for other loads]]

The supports are at $x=1$ and $x=3$ m, a UDL of 6 kN/m acts over $2\le x\le4$, the free end is at $x=5$ and $EI=7$ MN m².

**Reactions.** The load resultant, 12 kN at $x=3$, passes through the right support, so $R_a=0$ and $R_b=12$ kN.

**Macaulay moment.** A Macaulay UDL term runs to the end of the beam once switched on, so the load that stops at $x=4$ is written as a downward UDL from $x=2$ plus an upward UDL from $x=4$. Each UDL term is the resultant $w[x-a]$ times its lever arm $[x-a]/2$:

$$
M=12[x-3]-3[x-2]^2+3[x-4]^2\ \mathrm{kN\,m}
$$

**Integrate** $EIv''=-M$ twice, keeping the brackets intact:

$$
EIv=-2[x-3]^3+\frac{[x-2]^4}{4}-\frac{[x-4]^4}{4}+C_0x+C_1
$$

**Boundary conditions**, with every bracket zero when its argument is negative. $v(1)=0$ gives $C_0+C_1=0$, and $v(3)=0$ gives $\tfrac14+3C_0+C_1=0$, so $C_0=-\tfrac18$ and $C_1=\tfrac18$.

**Evaluate** at $x=5$:

$$
EIv(5)=-16+\frac{81}{4}-\frac14-\frac58+\frac18=3.5\ \mathrm{kN\,m^3}
$$

$$
v(5)=\frac{3.5\times10^3}{7\times10^6}=0.5\ \mathrm{mm}\ \text{(down)}
$$

![[s1_t5_q2.png|720]]

## Q3 - Propped cantilever with a half-length UDL

Taught in: [[FEEG1002 A6 - Statically Indeterminate Beams#Worked example - propped cantilever with a half-length load|A6, half-length load]] · [[FEEG1002 A6 - Statically Indeterminate Beams#2. The double integration method|A6, double integration method]]

A beam of length $L$ is built in at A ($x=0$) and simply supported at B ($x=L$), with a UDL $w$ from the wall to midspan. There are three unknowns, $R_A$, $R_B$ and $M_A$ (anticlockwise), and two equilibrium equations:

$$
R_A+R_B=\frac{wL}{2}\tag{1}
$$

$$
-R_AL+M_A+\frac{wL}{2}\cdot\frac{3L}{4}=0\tag{2}
$$

the second from moments about B. The third equation comes from deformation. Writing the load as a UDL from 0 with a cancelling upward UDL from $L/2$:

$$
EIv''=M_A-R_Ax+\frac{wx^2}{2}-\frac{w[x-\tfrac L2]^2}{2}
$$

$$
EIv=M_A\frac{x^2}{2}-R_A\frac{x^3}{6}+\frac{wx^4}{24}-\frac{w[x-\tfrac L2]^4}{24}
$$

with both constants zero from the built-in end. The prop gives $v(L)=0$; dividing by $L^2/2$,

$$
M_A-R_A\frac L3+\frac{15}{192}wL^2=0\tag{3}
$$

From (2), $M_A=R_AL-\tfrac38wL^2$. Substituting into (3), $\tfrac23R_AL=\tfrac{57}{192}wL^2$, so

$$
R_A=\frac{57}{128}wL,\qquad R_B=\frac{7}{128}wL,\qquad M_A=\frac{9}{128}wL^2
$$

With the load concentrated near the wall, the prop carries only 7/64 of it, about 11%.

![[s1_t5_q3.png|720]]

---

## Extra Q1 - Linearly varying load

Taught in: [[FEEG1002 A5 - Beam Deflection and Macaulay's Method#Solving by integration|A5, solving by integration]] · [[FEEG1002 A3 - Shear Force and Bending Moment Diagrams#6. Using the relations mathematically|A3, using the relations mathematically]]

A simply supported beam of length 6 m carries $w=x+6$ kN/m. Integrating $dQ/dx=-w$ and $dM/dx=Q$:

$$
Q=-\tfrac12x^2-6x+C_1,\qquad M=-\tfrac16x^3-3x^2+C_1x+C_2
$$

$M(0)=0$ gives $C_2=0$ and $M(6)=0$ gives $C_1=24$, so $R_A=24$ kN and $R_B=54-24=30$ kN. Then

$$
EIv''=-M=\tfrac16x^3+3x^2-24x
$$

$$
EIv=\tfrac{1}{120}x^5+\tfrac14x^4-4x^3+C_3x+C_4
$$

$v(0)=0$ gives $C_4=0$, and $v(6)=0$ gives $64.8+324-864+6C_3=0$, so $C_3=79.2$:

$$
v=\frac{1}{EI}\left(\frac{x^5}{120}+\frac{x^4}{4}-4x^3+\frac{396}{5}x\right)
$$

The largest moment is where $Q=0$, at $x=-6+\sqrt{84}=3.17$ m, where $M=40.6$ kN m; it sits right of centre because the load is heavier on the right.

![[s1_t5_x1.png|720]]

## Extra Q2 - Deflection of the Tutorial 3 Q2 beam

Taught in: [[FEEG1002 A5 - Beam Deflection and Macaulay's Method#Writing the bending moment for other loads|A5, writing M for other loads]] · [[FEEG1002 Statics 1 Tutorial 3 - Shear Force and Bending Moment Solutions#Q2 - UDL between supports with overhang loads|Tutorial 3 Q2]]

This is the beam of Tutorial 3 Q2 (reactions 9 kN at B and 19 kN at E) with $EI=1$ MN m². For a cut beyond E:

$$
M+2x-9[x-1]+3[x-1]^2-19[x-4]-3[x-4]^2=0
$$

Integrating $EIv''=-M$ twice:

$$
EIv=\frac{x^3}{3}-\frac32[x-1]^3+\frac{[x-1]^4}{4}-\frac{19}{6}[x-4]^3-\frac{[x-4]^4}{4}+C_0x+C_1
$$

$v(1)=0$ gives $C_0+C_1=-\tfrac13$ and $v(4)=0$ gives $4C_0+C_1=-1.0833$, so $C_0=-0.25$ and $C_1=-0.0833$. At F:

$$
v(5)=\frac{4.917\times10^3}{10^6}=4.92\ \mathrm{mm}\ \text{(down)}
$$

The free left end A rises by 0.083 mm ($v(0)=C_1/EI$), because the UDL between the supports rotates the left overhang upwards.

![[s1_t5_x2.png|720]]

## Extra Q3 - Fixed-fixed beam

Taught in: [[FEEG1002 A6 - Statically Indeterminate Beams#2. The double integration method|A6, double integration method]] · [[FEEG1002 A6 - Statically Indeterminate Beams#Counting reactions|A6, counting reactions]]

A beam of span $2L$ is built in at both ends and carries a UDL $w$ along its length and $W$ at midspan. Draw both wall moments $M_A$ and $M_B$ anticlockwise. Equilibrium gives two equations, the second from moments about A:

$$
R_A+R_B=W+2wL\tag{1}
$$

$$
M_A+M_B-WL-2wL^2+2R_BL=0\tag{2}
$$

The bending moment for the left part is $M=R_Ax-M_A-\tfrac12wx^2-W[x-L]$, so

$$
EIv''=M_A-R_Ax+\frac{wx^2}{2}+W[x-L]
$$

$v(0)=v'(0)=0$ make both integration constants zero, and $v'(2L)=0$ and $v(2L)=0$ give

$$
-2R_AL^2+2LM_A+\frac{WL^2}{2}+\frac43wL^3=0\tag{3}
$$

$$
-\frac43R_AL^3+2M_AL^2+\frac{WL^3}{6}+\frac23wL^4=0\tag{4}
$$

The sheet stops here. From (3), $M_A=R_AL-\tfrac23wL^2-\tfrac14WL$; substituting into (4) gives $\tfrac23R_AL^3=\tfrac23wL^4+\tfrac13WL^3$, so

$$
R_A=R_B=\frac W2+wL,\qquad M_A=\frac{WL}{4}+\frac{wL^2}{3}
$$

and (2) then gives $M_B=-M_A$. The two wall moments have the same size and opposite senses, anticlockwise at A and clockwise at B, both hogging. With $\ell=2L$ this is the standard fixed-end moment $W\ell/8+w\ell^2/12$. The midspan moment is $M(L)=WL/4+wL^2/6$ sagging: for the point load it equals the end moment, and for the UDL it is half of it.

![[s1_t5_x3.png|720]]

## Sources

- Tutorial Sheet 05 and its official solutions: Q1 pp. 1–2, Q2 pp. 3–4, Q3 pp. 5–6, additional Q1 p. 7, additional Q2 pp. 8–9, additional Q3 pp. 10–11.
- Reactions and deflections checked numerically with the beam solver in `Figures/generate_statics1_figures.py`.
- The official solution to Q2 (p. 3) has "Fee Body Diagram" for free body diagram.
