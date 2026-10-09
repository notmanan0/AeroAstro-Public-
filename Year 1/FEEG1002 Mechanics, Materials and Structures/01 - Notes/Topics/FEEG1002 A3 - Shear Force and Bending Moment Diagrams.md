---
title: "FEEG1002 A3 - Shear Force and Bending Moment Diagrams"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part A: Statics 1"
order: 3
tags: [feeg1002, statics, beams, shear-force, bending-moment, sfd, bmd]
aliases: ["Statics 1 Lecture 5", "Statics 1 Lecture 6", "SF and BM diagrams", "SFD and BMD"]
date: 2026-09-25
status: complete
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: ["[[FEEG1002 A1 - Forces, Equilibrium, Stress and Strain]]"]
next_topics: ["[[FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area]]"]
key_concepts: ["[[Shear Force and Bending Moment Relations]]", "[[Free Body Diagram and Equilibrium]]"]
tutorial_sheets: ["[[FEEG1002 Statics 1 Tutorial 3 - Shear Force and Bending Moment Solutions]]"]
sources: ["02 - Sources/Statics 1/Lectures/Lecture 05 - Beams, Shear Force and Bending Moment.pdf", "02 - Sources/Statics 1/Lectures/Lecture 06 - Beams, Relationship w, SF and BM.pdf"]
---

# FEEG1002 A3 - Shear Force and Bending Moment Diagrams

> [!abstract] Summary
> A beam is a laterally loaded member that is slender compared with its length. Cut it anywhere, and the kept part needs an internal **shear force** $Q$ and **bending moment** $M$ to stay in equilibrium. The SF and BM diagrams plot these along the beam; the peak $|M|$ sets the bending stress and the peak $|Q|$ the shear stress.
> Two differential relations let you sketch both diagrams almost by inspection:
> $$\frac{dQ}{dx} = -w(x),\qquad \frac{dM}{dx} = Q$$

## Key Concepts
- [[Shear Force and Bending Moment Relations]] · [[Free Body Diagram and Equilibrium]]

---

## 1. Beams, supports and loads (L5a)
- **Engineering questions**: at what load does it fail (strength)? If it doesn't fail, how far does it bend (stiffness)?
- **Supports**: pinned ($R_x$, $R_y$), roller ($R_y$), built-in ($R_x$, $R_y$, $M$). See [[FEEG1002 A1 - Forces, Equilibrium, Stress and Strain]]. Real supports are idealisations (friction, a non-rigid clamp), so bound the worst cases with engineering judgement.
- **Loads**:
  - concentrated force $F$;
  - uniform or varying distributed load $w(x)$ in N/m;
  - concentrated moment (couple) $M = Fd$.

## 2. Internal forces and the sign convention (L5b)
A bar with an offset axial load $F$ needs an internal $M = Fd$ at every cut. A cantilever with an end load of 1000 N needs $Q = 1000$ N everywhere and $M = 1000x$ growing towards the wall. A sign convention is essential:

![[s1_sign_convention.png|820]]

| Quantity | Positive when |
|---|---|
| Shear force $Q$ | it would rotate the segment **clockwise**: **downwards** on the right-hand face of the left part |
| Bending moment $M$ | it produces **sagging** (compression on top, tension underneath) |

With this convention, taking the **left** part and moments about the **cut face** (so $Q$ drops out):

$$
Q(x) = \sum(\text{upward forces left of }x) - \sum(\text{downward forces left of }x)
$$

$$
M(x) = \sum(\text{moments about the cut of all forces left of }x)\ \text{(clockwise positive)}
$$

## 3. Procedure (L5c–L6a)
1. Find the support reactions from the FBD. A distributed load can be replaced by its **resultant** at its centroid, **for the reactions only**.
2. Go back to the **original** loading. Working left to right, cut after every change in loading.
3. Insert positive $Q$ and $M$ on the cut face.
4. Vertical equilibrium gives $Q(x)$; moments about the cut face give $M(x)$.
5. Plot, and check that both return to zero at the right-hand end, or match the reactions there.

> [!example] L6 example: 5 kN at $x = 1$, supports at $x = 0$ and $5$, 5 kN/m UDL on the overhang $5\le x\le7$
> Reactions: $R_{Ay} = 2$ kN and $R_{By} = 13$ kN. By region:
>
> | Region | $Q$ (kN) | $M$ (kN m) |
> |---|---|---|
> | $0\le x\le1$ | $2000$ | $2000x$ |
> | $1\le x\le5$ | $-3000$ | $5000-3000x$ |
> | $5\le x\le7$ | $35000-5000x$ | $-2500x^2+35000x-122500$ |
>
> The peaks are $M = +2$ kN m at the load and $M = -10$ kN m over support B.

![[s1_sfd_bmd_lecture_example.png|760]]

## 4. Relations between $w$, $Q$ and $M$ (L6b)
Equilibrium of a slice $dx$ carrying load $w(x)\,dx$ gives:
- **vertical**: $Q + dQ + w\,dx = Q$, so $\dfrac{dQ}{dx} = -w$;
- **moments about the right face** (dropping the $(dx)^2$ term): $\dfrac{dM}{dx} = Q$.

Consequences, used to sketch by inspection:

| Feature on the beam | Effect on the SFD | Effect on the BMD |
|---|---|---|
| No load ($w = 0$) | horizontal | straight line |
| UDL $w$ | straight line, slope $-w$ | parabola |
| Linearly varying $w$ | parabola | cubic |
| Point force $F$ | **jump** of $F$, in the direction of $F$ | kink (slope changes) |
| Point couple $C$ | no effect | **jump** of $C$ (a clockwise couple gives an upward jump) |
| $Q = 0$ | – | local max or min of $M$ |
| Pinned, roller or free end | – | $M = 0$ unless a couple is applied there |

- $M(x_2) - M(x_1) = \displaystyle\int_{x_1}^{x_2} Q\,dx$: the **change** in BM equals the **area** under the SFD.

![[s1_standard_beam_cases.png|940]]

## 5. Using the relations mathematically (L6c)
For a load that varies from 0 at $x = 0$ to $W_B$ at $x = L$, $w = W_Bx/L$. The resultant $W_BL/2$ acts at $2L/3$, so $R_A = W_BL/6$ and $R_B = W_BL/3$. Integrating:

$$
Q = \frac{W_BL}{6} - \frac{W_B}{2L}x^2 \qquad M = \frac{W_BL}{6}x - \frac{W_B}{6L}x^3\quad(M(0) = M(L) = 0)
$$

$Q = 0$ at $x = L/\sqrt3 = 0.577L$, where $M_{max} = \dfrac{W_BL^2}{9\sqrt3}$.

![[s1_triangular_load_sfd_bmd.png|700]]

> [!warning] The mathematical maximum is not always the largest moment
> $dM/dx = 0$ finds a **local** extremum. Check the ends, support points and jump locations too. Take a 2 m cantilever carrying 4 kN/m plus a 2 kN upward end load: there is a local maximum inside the span, but the largest $|M|$ is at the wall.

## Worked tutorial diagrams
Full solutions are in [[FEEG1002 Statics 1 Tutorial 3 - Shear Force and Bending Moment Solutions]]:

![[s1_t3_q2.png|700]]

![[s1_t3_x3.png|700]]

## Year 2 bridge
- [[SESA2028 S2 - Beam Deflection and Bending Design]] uses the same chain $dV/dx = -w$, $dM/dx = V$ but writes the shear force as $V$. SESA2028 lets you choose the moment/deflection sign convention and asks only for **consistency**. FEEG1002 fixes $M$ sagging-positive with $v$ downwards.
- The BMD feeds the bending stress $\sigma = My/I$ ([[FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area]]), which becomes the coupled $\sigma_x(y,z)$ of [[SESA2028 S1 - Section Properties and Unsymmetrical Bending]]. The SFD feeds the shear flow $q$ in [[SESA2028 S3 - Shear Flow and Shear Centre]].
- In energy methods ([[SESA2028 S8 - Virtual Work and Castigliano Theorems]]) you write $M(x)$ for the real load and for a unit load. Deriving $M(x)$ by cutting and taking moments about the cut face is exactly the skill practised here.

## Links
- Previous: [[FEEG1002 A2 - Pin-Jointed Trusses]] · Next: [[FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area]]

## Sources
- Statics 1 Lectures 5a–c (supports and loads; SF and BM; procedure) and 6a–c (worked example; $w$–$Q$–$M$ relations; mathematical example)
