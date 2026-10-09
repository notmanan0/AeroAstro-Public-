---
title: "FEEG1002 A6 - Statically Indeterminate Beams"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part A: Statics 1"
order: 6
tags: [feeg1002, statics, beams, statically-indeterminate, superposition, compatibility]
aliases: ["Statics 1 Lecture 11", "Propped cantilever", "Indeterminate beams"]
date: 2026-09-25
status: complete
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: ["[[FEEG1002 A5 - Beam Deflection and Macaulay's Method]]"]
next_topics: ["[[FEEG1002 A7 - Euler Buckling of Struts]]"]
key_concepts: ["[[Superposition for Indeterminate Beams]]", "[[Macaulay's Method]]", "[[Standard Beam Deflections]]"]
tutorial_sheets: ["[[FEEG1002 Statics 1 Tutorial 5 - Beam Deflection and Statically Indeterminate Beams Solutions]]"]
sources: ["02 - Sources/Statics 1/Lectures/Lecture 11 - Statically Indeterminate Beams.pdf"]
---

# FEEG1002 A6 - Statically Indeterminate Beams

> [!abstract] Summary
> A 2D beam supplies only **two** useful equilibrium equations for vertical loads (vertical force and moment). With three or four unknown reactions (a propped cantilever, a fixed–fixed beam) statics alone cannot say how the load is shared. **How the load divides depends on how the beam bends.**
> - **Double integration**: carry the unknown reactions through Macaulay's method, then use the *extra* kinematic boundary conditions as the missing equations.
> - **Superposition**: remove a redundant support, compute the deflection there from standard cases, and choose the redundant force to cancel it (**compatibility**).

## Key Concepts
- [[Superposition for Indeterminate Beams]] · [[Macaulay's Method]] · [[Standard Beam Deflections]]

---

## 1. Determinate vs indeterminate (L11a)

| Beam | Unknown reactions | Equilibrium equations | Degree of indeterminacy |
|---|---|---|---|
| Simply supported | 2 | 2 | 0 |
| Propped cantilever (fixed + roller) | 3 ($R_1$, $R_2$, $M_1$) | 2 | 1 |
| Fixed–fixed | 4 ($R_A$, $R_B$, $M_A$, $M_B$) | 2 | 2 |

The missing equations come from **deformation**: known deflections and slopes at the supports.

## 2. Double integration method (L11b)
1. Replace the supports by unknown reactions and write the equilibrium equations.
2. Write $M(x)$ with Macaulay brackets, keeping the reactions as unknown symbols.
3. Integrate $EIv'' = -M$ twice.
4. Apply **all** the kinematic boundary conditions. They fix both integration constants and supply the extra reaction equations.
5. Solve the system, then back-substitute.

> [!example] L11: propped cantilever with a full UDL (built in at $x = 0$, roller at $x = L$)
> - Equilibrium: $R_1 + R_2 = wL$ and $R_1L = M_1 + wL^2/2$.
> - $M = -M_1 - \dfrac{wx^2}{2} + R_1x$, so $EIv'' = M_1 + \dfrac{wx^2}{2} - R_1x$.
> - $v'(0) = 0\Rightarrow C_0 = 0$ and $v(0) = 0\Rightarrow C_1 = 0$.
> - The extra condition $v(L) = 0$ gives $M_1\dfrac{L^2}{2} + \dfrac{wL^4}{24} - R_1\dfrac{L^3}{6} = 0$.
> - Solving: $R_1 = \tfrac58wL$, $R_2 = \tfrac38wL$, $M_1 = \tfrac18wL^2$ (hogging at the wall).
>
> $$v = \frac{1}{EI}\left[\frac{wL^2}{16}x^2 + \frac{w x^4}{24} - \frac{5wL}{48}x^3\right]$$
>
> The maximum sagging moment is $\tfrac{9}{128}wL^2$ at $x = \tfrac58L$, where $Q = 0$.

![[s1_propped_cantilever_udl.png|720]]

> [!note] $M(L) = 0$ is not a new equation
> Zero moment at the roller is the same statement as moments about the right-hand end. It is already in the equilibrium equations, so the independent extra equation must come from $v(L) = 0$.

## 3. Superposition method (L11c)
Split the indeterminate beam into **determinate standard cases** whose end deflections you already know:

$$
\underbrace{\text{cantilever + UDL}}_{v'(L) = \frac{wL^4}{8EI}} \;+\; \underbrace{\text{cantilever + upward tip force }F}_{v''(L) = -\frac{FL^3}{3EI}} \quad\text{with}\quad v'(L) + v''(L) = 0
$$

$$
\frac{wL^4}{8EI} - \frac{FL^3}{3EI} = 0\;\Rightarrow\; F = R_2 = \frac38wL
$$

The other reactions then follow from equilibrium: $R_1 = \tfrac58wL$ and $M_1 = \tfrac18wL^2$.

![[s1_superposition_propped_cantilever.png|700]]

> [!tip] Choosing a method
> - **Superposition** is fastest when the loads match tabulated cases ([[Standard Beam Deflections]]).
> - **Double integration** handles any loading, e.g. Tutorial 5 Q3, where the UDL stops at midspan. There $R_A = \tfrac{57}{128}wL$, $R_B = \tfrac{7}{128}wL$ and $M_A = \tfrac{9}{128}wL^2$.

![[s1_t5_q3.png|700]]

### Fixed–fixed beam (Tutorial 5 extra Q3)
There are four unknowns ($R_A$, $M_A$, $R_B$, $M_B$), two equilibrium equations, and four kinematic conditions: $v = v' = 0$ at both ends.
- Two of the kinematic conditions fix the integration constants; the other two close the system.
- For a UDL $w$ over the length $2L$ plus $W$ at midspan, symmetry gives $R_A = R_B = W/2 + wL$ and

$$
M_A = M_B = \frac{W(2L)}{8} + \frac{w(2L)^2}{12} = \frac{WL}{4} + \frac{wL^2}{3}
$$

![[s1_t5_x3.png|700]]

## 4. Why build indeterminate structures?
- They are **stiffer** and have **lower peak moments** (compare $wL^2/8$ for simply supported with $wL^2/12$ at the ends of a fixed–fixed beam).
- They are **redundant**: a load path survives if one support fails. That is fail-safe design.
- The costs: support settlement, temperature change and fit-up errors all induce stresses, because the structure cannot deform freely.

## Year 2 bridge
- [[SESA2028 S8 - Virtual Work and Castigliano Theorems]] (§5) solves the same problems with energy. Remove the redundant $R$, write $U(R)$, and impose $\partial U/\partial R = 0$ ([[Castigliano Second Theorem]]). That is exactly the compatibility equation above, obtained without the elastic curve.
- [[Principle of Virtual Work]] and [[Maxwell-Betti Reciprocity]] generalise superposition of unit-load cases.
- In FEA ([[SESA2029 B1 - Introduction to FEA and the Matrix Displacement Method]]), indeterminacy disappears as a special case: the stiffness method solves for displacements first, so the number of redundants never matters.

## Links
- Previous: [[FEEG1002 A5 - Beam Deflection and Macaulay's Method]] · Next: [[FEEG1002 A7 - Euler Buckling of Struts]]
- Worked problems: [[FEEG1002 Statics 1 Tutorial 5 - Beam Deflection and Statically Indeterminate Beams Solutions]]

## Sources
- Statics 1 Lecture 11a–c (statically indeterminate beams; double integration method; superposition method)
