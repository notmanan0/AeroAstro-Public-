---
title: "FEEG1002 Statics 1 Tutorial 3 - Shear Force and Bending Moment Solutions"
module: "FEEG1002 Mechanics, Materials and Structures"
type: tutorial
stream: "Part A: Statics 1"
tags: [feeg1002, tutorial-solutions, statics, beams, sfd, bmd]
sheet: "Statics-1 Tutorial problem sheet 3"
theory_notes: ["[[FEEG1002 A3 - Shear Force and Bending Moment Diagrams]]"]
key_concepts: ["[[Shear Force and Bending Moment Relations]]"]
status: complete
sources: ["02 - Sources/Statics 1/Tutorials/Tutorial Sheet 03 - Beams, w, SF and BM.pdf", "02 - Sources/Statics 1/Tutorials/Tutorial Sheet 03 - Beams, w, SF and BM - Solutions.pdf"]
---

# FEEG1002 Statics 1 Tutorial 3 - Shear Force and Bending Moment Solutions

> [!abstract] Sheet Info
> Six beams: three core and three extra. Every diagram below was computed with the singularity-function beam solver, not sketched, so the plotted values *are* the answers. The loading panel shows the reactions in red. All values match the official sheet ✔.
> **Convention** ([[FEEG1002 A3 - Shear Force and Bending Moment Diagrams]]): $Q$ is positive downwards on the left part's cut face; $M$ is positive when sagging.

## Theory Links
- [[FEEG1002 A3 - Shear Force and Bending Moment Diagrams]] · [[Shear Force and Bending Moment Relations]]

**Sketching toolkit**: $dQ/dx = -w$ and $dM/dx = Q$.
- A point force causes a SF jump in the same direction as the force.
- A couple causes a BM jump; a clockwise couple makes $M$ jump upwards.
- $M = 0$ at pinned, roller and free ends.
- A peak in $M$ occurs where $Q = 0$.

---

## Q1: Overhanging beam, supports at B ($x = 1$) and D ($x = 3$), 8 kN at C ($x = 2$), 3 kN at F ($x = 5$)
**Reactions** (moments about B, anticlockwise +): $-(1)(8) + 2R_D - (4)(3) = 0$, so $R_D = 10$ kN and $R_B = 11 - 10 = 1$ kN.

**Cutting region by region** (left part, moments about the cut face):

| Region | $Q$ (kN) | $M$ (kN m) |
|---|---|---|
| AB, $0\le x\le1$ | 0 | 0 |
| BC, $1\le x\le2$ | $+1$ | $x-1$ |
| CD, $2\le x\le3$ | $-7$ | $-7x+15$ |
| DF, $3\le x\le5$ | $+3$ | $3x-15$ |

$M_C = +1$ kN m (sagging) and $M_D = -6$ kN m (hogging over the support), which is the design moment.

**Shortcut.** With $w = 0$ everywhere, $Q$ is piecewise constant, jumping by each point force. $M$ is piecewise linear with slope $Q$, starting and ending at zero at the free ends.

![[s1_t3_q1.png|720]]

## Q2: 2 kN at A ($x = 0$), supports B ($x = 1$) and E ($x = 4$), 6 kN/m on B–E, 8 kN at F ($x = 5$)
**Reactions.** The UDL resultant is 18 kN at $x = 2.5$.
- Moments about B: $(2)(1) - (18)(1.5) + 3R_E - (8)(4) = 0$, so $R_E = 19$ kN.
- Vertical: $R_B = 28 - 19 = 9$ kN.

**Sketching**
1. SF starts at 0, jumps to $-2$ at A, stays flat, then jumps $+9$ to $+7$ at B.
2. It falls at 6 kN/m over 3 m to $-11$ at E, jumps $+19$ to $+8$, and returns to 0 at F.
3. $Q = 0$ at $x = 1 + 7/6 = 2\tfrac16$ m, so the BM peaks there.
4. BM: $M_B = -2$ kN m (area $-2\times1$).
   - $M_{max} = -2 + \tfrac12(7)(7/6) = \mathbf{+2.083}$ **kN m**.
   - $M_E = -8$ kN m. Easiest from the free end: 1 m × 8 kN of SF area.

![[s1_t3_q2.png|720]]

## Q3: Simply supported, $L = 6$ m, $w(x) = \tfrac83x - \tfrac49x^2$ kN/m
Integrate:
$$Q = -\int w\,dx = \tfrac{4}{27}x^3 - \tfrac43x^2 + C_1,\qquad M = \tfrac{1}{27}x^4 - \tfrac49x^3 + C_1x + C_2$$
- $M(0) = 0$ gives $C_2 = 0$; $M(6) = 0$ gives $C_1 = 8$.
- So $R_A = Q(0) = 8$ kN, and $R_B = 8$ kN by symmetry.
- $w$ is symmetric about $x = 3$, so $Q(3) = 0$ and $M_{max} = M(3) = 3 - 12 + 24 = \mathbf{15}$ **kN m**.
- Check: the total load is $\int_0^6 w\,dx = 48 - 32 = 16$ kN $= R_A + R_B$ ✔

![[s1_t3_q3.png|720]]

---

## Extra Q1: $L = 2$ m, $F = 9$ kN **upwards** at $L/3$ and **downwards** at $2L/3$
- Moments about A: $\tfrac13LF - \tfrac23LF + LR_b = 0$, so $R_b = F/3$ and $R_a = -F/3$. The left support pulls **down**.
- Cut at $x = L/2$: $Q + \tfrac13F = F$, so $Q = \tfrac23F = \mathbf{6}$ **kN** ✔
- $M(2L/3) = -\tfrac13F\cdot\tfrac23L + F\cdot\tfrac13L = \tfrac19FL = \mathbf{2}$ **kN m** ✔
- Antisymmetric loading gives an antisymmetric BMD, with $M = 0$ at midspan.

![[s1_t3_x1.png|700]]

## Extra Q2: Cantilever built in at the right ($x = 5$), 4 kN/m over the whole length, 16 kN at $x = 2$
- The SF falls linearly from 0 at a slope of 4 kN/m, jumps $-16$ at C, and reaches $-36$ kN at the wall. So $R = 36$ kN.
- The BM is quadratic, steepening after C: $M_C = -8$ kN m and $M_{wall} = -(16)(3) - (4)(5)(2.5) = \mathbf{-98}$ **kN m**, which is the wall's reaction moment.

![[s1_t3_x2.png|720]]

## Extra Q3: Simply supported, $L = 5$ m, 7 kN at $x = 1$, clockwise 8 kN m couple at $x = 3$
- Moments about A: $5R_F = 7(1) + 8$, so $R_F = 3$ kN and $R_A = 4$ kN. The couple **does** change the reactions.
- SF: $+4$ up to B, then $-3$. The couple has **no** effect on the SF.
- BM:
  - $M_B = 4$;
  - $M_{D^-} = 4 - 3(2) = -2$;
  - the **clockwise** couple makes $M$ jump **up** by 8, so $M_{D^+} = +6$;
  - then linear back to 0 at F ✔

![[s1_t3_x3.png|720]]

## Sources
- Source sheet and official solutions: Statics-1 Tutorial problem sheet 3
- Diagrams: `Figures/generate_statics1_figures.py` (`beam_cases`)
