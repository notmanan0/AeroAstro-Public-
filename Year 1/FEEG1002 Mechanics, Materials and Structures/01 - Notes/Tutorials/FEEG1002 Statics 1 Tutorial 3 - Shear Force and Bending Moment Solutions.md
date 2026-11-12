---
title: "FEEG1002 Statics 1 Tutorial 3 - Shear Force and Bending Moment Solutions"
module: "FEEG1002 Mechanics, Materials and Structures"
type: tutorial
stream: "Part A: Statics 1"
tags: [feeg1002, tutorial-solutions, statics, beams, sfd, bmd]
sheet: "Statics-1 Tutorial problem sheet 3"
theory_notes: ["[[FEEG1002 A3 - Shear Force and Bending Moment Diagrams]]"]
key_concepts: ["[[Shear Force and Bending Moment Relations]]", "[[Free Body Diagram and Equilibrium]]"]
status: complete
sources: ["02 - Sources/Statics 1/Tutorials/Tutorial Sheet 03 - Beams, w, SF and BM.pdf", "02 - Sources/Statics 1/Tutorials/Tutorial Sheet 03 - Beams, w, SF and BM - Solutions.pdf"]
---

# FEEG1002 Statics 1 Tutorial 3 - Shear Force and Bending Moment Solutions

> [!abstract] Sheet info
> Six beams: three core questions and three additional problems. Every diagram below was computed with the singularity-function beam solver in the figure script rather than sketched, so the plotted values are the answers; the loading panel shows the reactions in red. All printed answers are reproduced.

Theory: [[FEEG1002 A3 - Shear Force and Bending Moment Diagrams]] · [[Shear Force and Bending Moment Relations]]

The course convention is used throughout: $Q$ is positive downwards on the right-hand face of the left part, and $M$ is positive when sagging. The sketching relations are $dQ/dx=-w$ and $dM/dx=Q$. A point force makes $Q$ jump in the direction of the force, a clockwise couple makes $M$ jump upwards, $M=0$ at pinned, roller and free ends, and $M$ has a turning point where $Q=0$.

---

## Q1 - Overhanging beam with two point loads

Taught in: [[FEEG1002 A3 - Shear Force and Bending Moment Diagrams#4. Procedure for shear force and bending moment diagrams|A3, procedure]] · [[FEEG1002 A3 - Shear Force and Bending Moment Diagrams#Worked example - overhanging beam by sketching|A3, overhanging beam by sketching]]

The beam runs from a free end A at $x=0$ to a free end F at $x=5$ m, with supports at B ($x=1$) and D ($x=3$), 8 kN down at C ($x=2$) and 3 kN down at F.

**Reactions.** Moments about B, anticlockwise positive:

$$
-(1)(8)+2R_D-(4)(3)=0\quad\Rightarrow\quad R_D=10\ \mathrm{kN}
$$

and vertically $R_B=11-10=1$ kN.

**Cutting region by region**, keeping the left part and taking moments about the cut:

| Region | $Q$ (kN) | $M$ (kN m) |
|---|---|---|
| AB, $0\le x\le1$ | 0 | 0 |
| BC, $1\le x\le2$ | $+1$ | $x-1$ |
| CD, $2\le x\le3$ | $-7$ | $-7x+15$ |
| DF, $3\le x\le5$ | $+3$ | $3x-15$ |

So $M_C=+1$ kN m (sagging) and $M_D=-6$ kN m (hogging over the support), and $|M_D|$ is the design moment. With $w=0$ everywhere the shortcut works just as well: $Q$ is piecewise constant, jumping at each point force, and $M$ is piecewise linear with slope $Q$, starting and ending at zero at the free ends.

![[s1_t3_q1.png|720]]

## Q2 - UDL between supports with overhang loads

Taught in: [[FEEG1002 A3 - Shear Force and Bending Moment Diagrams#Procedure for sketching|A3, procedure for sketching]] · [[FEEG1002 A3 - Shear Force and Bending Moment Diagrams#Consequences|A3, consequences of the relations]]

2 kN acts down at the free end A ($x=0$), the supports are at B ($x=1$) and E ($x=4$), 6 kN/m acts over B–E and 8 kN acts down at the free end F ($x=5$).

**Reactions.** The UDL resultant is 18 kN at $x=2.5$. Moments about B:

$$
(2)(1)-(18)(1.5)+3R_E-(8)(4)=0\quad\Rightarrow\quad R_E=19\ \mathrm{kN}
$$

and vertically $R_B=28-19=9$ kN.

**Sketching the shear force.** $Q$ starts at 0, jumps to $-2$ at A and stays flat, then jumps by $+9$ to $+7$ at B. It falls at 6 kN/m over 3 m to $-11$ at E, jumps by $+19$ to $+8$, and returns to 0 at F. It crosses zero at $x=1+7/6=2\tfrac16$ m, where $M$ has its maximum.

**Sketching the bending moment** from the areas under the SFD. $M_B=-2\times1=-2$ kN m. Adding the triangle from B to the zero crossing:

$$
M_{max}=-2+\tfrac12(7)\left(\tfrac76\right)=+2.083\ \mathrm{kN\,m}
$$

$M_E=-8$ kN m, most easily from the free end F: 1 m of shear force at 8 kN.

![[s1_t3_q2.png|720]]

## Q3 - Parabolic distributed load

Taught in: [[FEEG1002 A3 - Shear Force and Bending Moment Diagrams#6. Using the relations mathematically|A3, using the relations mathematically]] · [[FEEG1002 A3 - Shear Force and Bending Moment Diagrams#Example: linearly varying load|A3, linearly varying load]]

A simply supported beam of length 6 m carries $w(x)=\tfrac83x-\tfrac49x^2$ kN/m. Integrating $dQ/dx=-w$:

$$
Q=-\int w\,dx=\tfrac{4}{27}x^3-\tfrac43x^2+C_1
$$

and $dM/dx=Q$:

$$
M=\tfrac{1}{27}x^4-\tfrac49x^3+C_1x+C_2
$$

$M(0)=0$ gives $C_2=0$. $M(6)=0$ gives $48-96+6C_1=0$, so $C_1=8$. Then $R_A=Q(0)=8$ kN, and $R_B=8$ kN by symmetry. Since $w$ is symmetric about $x=3$, $Q(3)=4-12+8=0$ and

$$
M_{max}=M(3)=3-12+24=15\ \mathrm{kN\,m}
$$

> [!check] Total load
> $\int_0^6w\,dx=\tfrac43(36)-\tfrac{4}{27}(216)=48-32=16$ kN, equal to $R_A+R_B$.

![[s1_t3_q3.png|720]]

---

## Extra Q1 - Equal and opposite loads

Taught in: [[FEEG1002 A3 - Shear Force and Bending Moment Diagrams#4. Procedure for shear force and bending moment diagrams|A3, procedure]]

A simply supported beam of length $L=2$ m carries $F=9$ kN upwards at $L/3$ and downwards at $2L/3$. Moments about A:

$$
\tfrac13LF-\tfrac23LF+LR_b=0\quad\Rightarrow\quad R_b=\tfrac F3
$$

and vertically $R_a=-F/3$, so the left support pulls down. Cutting at $x=L/2$ and balancing the left part vertically, $Q+\tfrac13F=F$, so

$$
Q=\tfrac23F=6\ \mathrm{kN}
$$

At $x=2L/3$:

$$
M=-\tfrac13F\cdot\tfrac23L+F\cdot\tfrac13L=\tfrac19FL=2\ \mathrm{kN\,m}
$$

The loading is antisymmetric about midspan, so the BMD is too, with $M=0$ at $x=L/2$.

![[s1_t3_x1.png|700]]

## Extra Q2 - Cantilever with UDL and point load

Taught in: [[FEEG1002 A3 - Shear Force and Bending Moment Diagrams#Example: a cantilever with an end load|A3, cantilever with an end load]] · [[FEEG1002 A3 - Shear Force and Bending Moment Diagrams#Procedure for sketching|A3, procedure for sketching]]

The cantilever is free at $x=0$ and built in at $x=5$ m, with 4 kN/m over the whole length and 16 kN down at C ($x=2$). Starting from the free end, $Q$ falls linearly from 0 at 4 kN/m, jumps by $-16$ at C and reaches $-36$ kN at the wall, so the wall reaction is 36 kN. $M$ is quadratic and steepens after C, with $M_C=-\tfrac12(4)(2^2)=-8$ kN m and

$$
M_{wall}=-(16)(3)-(4)(5)(2.5)=-98\ \mathrm{kN\,m}
$$

which is also the reaction moment at the wall.

![[s1_t3_x2.png|720]]

## Extra Q3 - Point load and applied couple

Taught in: [[FEEG1002 A3 - Shear Force and Bending Moment Diagrams#3. The sign convention|A3, sign convention]] · [[FEEG1002 A3 - Shear Force and Bending Moment Diagrams#Consequences|A3, consequences of the relations]]

A simply supported beam of length 5 m carries 7 kN down at $x=1$ and a clockwise couple of 8 kN m at $x=3$. Moments about A give $5R_F=7(1)+8$, so $R_F=3$ kN and $R_A=4$ kN; the couple changes the reactions even though it adds no vertical force. The SFD is $+4$ kN up to B and $-3$ kN after it, with no change at the couple. For the BMD, $M_B=4$ kN m and $M_{D^-}=4-3(2)=-2$ kN m. The clockwise couple makes $M$ jump up by 8, so $M_{D^+}=+6$ kN m, and $M$ then falls linearly to 0 at F.

![[s1_t3_x3.png|720]]

## Sources

- Tutorial Sheet 03 and its official solutions: Q1 pp. 1–3, Q2 pp. 4–5, Q3 p. 6, additional Q1 pp. 7–8, additional Q2 p. 9, additional Q3 p. 10.
- Diagrams from the beam solver in `Figures/generate_statics1_figures.py`.
- The problem sheet's Q3 has a typo, "caries" for carries.
