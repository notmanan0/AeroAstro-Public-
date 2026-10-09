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

> [!abstract] Sheet Info
> Macaulay deflections (Q1, Q2, extras 1–2) and indeterminate reactions (Q3, extra 3). All printed answers are reproduced ✔.
> - Extra Q3 is left as "set up the equations" on the sheet; it is solved to completion here.
> - Every deflection curve was also computed numerically with the singularity-function solver.
>
> Convention: $v$ is downwards and $EIv'' = -M$.

## Theory Links
- [[FEEG1002 A5 - Beam Deflection and Macaulay's Method]] · [[FEEG1002 A6 - Statically Indeterminate Beams]] · [[Macaulay's Method]]

---

## Q1: Cantilever, load $F$ at $L/2$: tip deflection
- Reactions: $R_A = F$ and $M_A = FL/2$ (anticlockwise).
- Cut beyond the load: $M + M_A - R_Ax + F[x - L/2] = 0$, so $M = -\dfrac{FL}{2} + Fx - F[x - \tfrac L2]$.
- Integrate $EIv'' = -M$:
$$EIv' = \frac{FL}{2}x - \frac F2x^2 + \frac F2[x-\tfrac L2]^2 + C_1,\qquad EIv = \frac{FL}{4}x^2 - \frac F6x^3 + \frac F6[x-\tfrac L2]^3 + C_2$$
- A built-in end needs $v'(0) = 0$ and $v(0) = 0$, so $C_1 = C_2 = 0$.
$$v(L) = \frac{1}{EI}\left(\frac{FL^3}{4} - \frac{FL^3}{6} + \frac{FL^3}{48}\right) = \mathbf{\frac{5FL^3}{48EI}}\ ✔$$

The outer half has $M = 0$, so it is **straight**. The tip deflection is $v(L/2) + v'(L/2)\cdot L/2$.

![[s1_t5_q1.png|680]]

## Q2: Supports at $x = 1$ and $x = 3$, UDL 6 kN/m on $2\le x\le4$, $EI = 7$ MN m². Find $v(5)$.
- **Reactions**: the load resultant (12 kN at $x = 3$) passes through the right support, so $R_a = 0$ and $R_b = 12$ kN.
- **Macaulay moment**: the UDL stops at $x = 4$, so add an upward UDL from 4.
$$M = 12[x-3] - 3[x-2]^2 + 3[x-4]^2\ \text{kN m}$$
  Each UDL term is the resultant $w[x-a]$ times its lever arm $[x-a]/2$.
- **Integrate** (brackets kept intact):
$$EIv = -2[x-3]^3 + \frac{[x-2]^4}{4} - \frac{[x-4]^4}{4} + C_0x + C_1$$
- **Boundary conditions** (every bracket is zero when negative):
  - $v(1) = 0$ gives $C_0 + C_1 = 0$;
  - $v(3) = 0$ gives $\tfrac14 + 3C_0 + C_1 = 0$;
  - so $C_0 = -\tfrac18$ and $C_1 = \tfrac18$.
- **Evaluate**:
$$EIv(5) = -16 + \frac{81}{4} - \frac14 - \frac58 + \frac18 = 3.5\ \text{kN m}^3\;\Rightarrow\; v(5) = \frac{3.5\times10^3}{7\times10^6} = \mathbf{0.5}\ \text{mm (down)}\ ✔$$

![[s1_t5_q2.png|720]]

## Q3: Propped cantilever, UDL $w$ on the first half only
Three unknowns ($R_A$, $R_B$, $M_A$), two equilibrium equations:
- (1) $R_A + R_B = wL/2$;
- (2) moments about B: $-R_AL + M_A + \dfrac{wL}{2}\cdot\dfrac{3L}{4} = 0$.

Macaulay, with a cancelling UDL from $L/2$:
$$EIv'' = M_A - R_Ax + \frac{wx^2}{2} - \frac{w[x-\tfrac L2]^2}{2}$$
$$EIv = M_A\frac{x^2}{2} - R_A\frac{x^3}{6} + \frac{wx^4}{24} - \frac{w[x-\tfrac L2]^4}{24}\qquad(C_0 = C_1 = 0\ \text{from the built-in end})$$

The extra condition $v(L) = 0$ gives (3) $M_A - R_A\dfrac L3 + \dfrac{15}{192}wL^2 = 0$. Solving (1)–(3):

$$
R_A = \mathbf{\tfrac{57}{128}wL},\qquad R_B = \mathbf{\tfrac{7}{128}wL},\qquad M_A = \mathbf{\tfrac{9}{128}wL^2}\ ✔
$$

With the load concentrated near the wall, the prop carries only 7/128 of it, i.e. 11% of $wL/2$.

![[s1_t5_q3.png|720]]

---

## Extra Q1: Simply supported, $L = 6$ m, $w = x + 6$ kN/m. Find $v(x)$.
- $Q = -\tfrac12x^2 - 6x + C_1$ and $M = -\tfrac16x^3 - 3x^2 + C_1x + C_2$.
- $M(0) = M(6) = 0$ gives $C_2 = 0$ and $C_1 = 24$, so $R_A = 24$ kN and $R_B = 54 - 24 = 30$ kN.
- $EIv'' = \tfrac16x^3 + 3x^2 - 24x$ integrates to $EIv = \tfrac1{120}x^5 + \tfrac14x^4 - 4x^3 + C_3x + C_4$.
- $v(0) = 0$ gives $C_4 = 0$; $v(6) = 0$ gives $C_3 = 79.2$.

$$v = \frac{1}{EI}\left(\frac{x^5}{120} + \frac{x^4}{4} - 4x^3 + \frac{396}{5}x\right)$$

The maximum moment is $M = 40.6$ kN m at $x = -6 + \sqrt{84} = 3.17$ m. It sits right of centre, because the load is heavier on the right.

![[s1_t5_x1.png|720]]

## Extra Q2: The Tutorial 3 Q2 beam with $EI = 1$ MN m². Find the deflection of F.
- $M$ for the cut past E: $M + 2x - 9[x-1] + 3[x-1]^2 - 19[x-4] - 3[x-4]^2 = 0$.
- $EIv = \dfrac{x^3}{3} - \dfrac32[x-1]^3 + \dfrac{[x-1]^4}{4} - \dfrac{19}{6}[x-4]^3 - \dfrac{[x-4]^4}{4} + C_0x + C_1$.
- $v(1) = 0$ gives $C_0 + C_1 = -\tfrac13$; $v(4) = 0$ gives $4C_0 + C_1 = -1.0833$. So $C_0 = -0.25$ and $C_1 = -0.0833$.
$$v(5) = \frac{4.917\times10^3}{10^6} = \mathbf{4.92}\ \text{mm (down)}\ ✔$$
The free left end A **rises** by 0.083 mm: the UDL between the supports rotates the overhang upwards.

![[s1_t5_x2.png|720]]

## Extra Q3: Fixed–fixed beam, span $2L$, UDL $w$ plus $W$ at midspan
- Equilibrium: (1) $R_A + R_B = W + 2wL$ and (2) $M_A + M_B - WL - 2wL^2 + 2R_BL = 0$.
- Four kinematic conditions: $v(0) = v'(0) = 0$ fix $C_0 = C_1 = 0$, and $v(2L) = v'(2L) = 0$ give:
  - (3) $-\tfrac43R_AL^3 + 2M_AL^2 + \tfrac{W L^3}{6} + \tfrac23wL^4 = 0$;
  - (4) $-2R_AL^2 + 2LM_A + \tfrac{WL^2}{2} + \tfrac43wL^3 = 0$.
- Solving (the sheet stops at setting up the equations):
$$R_A = R_B = \frac W2 + wL,\qquad M_A = M_B = \frac{WL}{4} + \frac{wL^2}{3}$$
This is the textbook fixed-end result $W\ell/8 + w\ell^2/12$ with $\ell = 2L$. The midspan moment is $WL/4 + wL^2/6$ sagging, only half the end moment for the UDL part.

![[s1_t5_x3.png|720]]

## Sources
- Source sheet and official solutions: Statics-1 Tutorial problem sheet 5
- Numerical check: singularity-function solver in `Figures/feeg1002_style.py` (reactions agree to 3 s.f.)
