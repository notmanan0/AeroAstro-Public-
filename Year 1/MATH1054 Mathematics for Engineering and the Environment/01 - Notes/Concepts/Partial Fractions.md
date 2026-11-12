---
title: "Partial Fractions"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 1: Calculus"
aliases: ["Partial fraction decomposition", "Cover-up rule"]
tags: [math1054, concept, integration]
status: complete
parent_lectures: ["[[MATH1054 M10 - Integration III]]"]
related_concepts: ["[[Completing the Square]]", "[[Partial Fractions for Inverse Laplace]]", "[[Integration by Substitution]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) pp.114–119, §8.8", "MATH1054 Module Booklet, Module 10"]
---

# Partial Fractions

Partial fractions write a proper rational function $P(x)/Q(x)$ as a sum of simple fractions, one group for each factor of $Q$, so that each piece can be integrated (or inverse-Laplace-transformed) on its own.

A linear factor $(x-a)$ contributes $\dfrac{A}{x-a}$; a repeated factor $(x-a)^2$ contributes $\dfrac{A}{x-a}+\dfrac{B}{(x-a)^2}$, and $(x-a)^k$ one term for every power up to $k$; an irreducible quadratic $x^2+bx+c$ ($b^2<4c$) contributes $\dfrac{Bx+C}{x^2+bx+c}$. The number of unknowns always equals $\deg Q$. If $\deg P\ge\deg Q$ the fraction is improper and must be divided first, e.g. $\frac{2x^3}{x^3-1}=2+\frac{2}{x^3-1}$.

The forms come from one step repeated. If $Q=(x-a)R$ with $R(a)\ne0$ and $A=P(a)/R(a)$, then $P-AR$ vanishes at $x=a$, so $P-AR=(x-a)S$ and

$$
\frac{P}{(x-a)R}=\frac{A}{x-a}+\frac{S}{R},
$$

with $S/R$ still proper. The formula $A=P(a)/R(a)$ is the **cover-up rule**: cover the factor $(x-a)$ and substitute $x=a$ into what remains. Applied to $(x-a)^k$, the same step lowers the power by one each time, which is why every power from $1$ to $k$ appears and why cover-up gives only the top coefficient. An irreducible quadratic has complex roots $\alpha,\bar\alpha$; the two conjugate terms $\frac{A}{x-\alpha}+\frac{\bar A}{x-\bar\alpha}$ combine to $\frac{Bx+C}{x^2+bx+c}$ with real $B,C$, so the numerator must be linear. The constants the cover-up rule cannot reach come from comparing coefficients in the cleared identity, which holds for all $x$.

Each piece then integrates directly: $\int\frac{\mathrm dx}{x-a}=\ln|x-a|$, $\int\frac{\mathrm dx}{(x-a)^2}=-\frac{1}{x-a}$, and a quadratic term gives a logarithm plus an inverse tangent after writing $Bx+C=\frac B2(2x+b)+\big(C-\frac{Bb}{2}\big)$ and [[Completing the Square]].

For example (James Example 8.53(b)), $\frac{9}{(x-1)(x+2)^2}=\frac{A}{x-1}+\frac{B}{x+2}+\frac{C}{(x+2)^2}$. Cover-up gives $A=\frac{9}{9}=1$ and $C=\frac{9}{-3}=-3$, and the $x^2$ coefficients of $9=A(x+2)^2+B(x-1)(x+2)+C(x-1)$ give $B=-1$:

$$
\frac{9}{(x-1)(x+2)^2}=\frac{1}{x-1}-\frac{1}{x+2}-\frac{3}{(x+2)^2},\qquad\int=\ln\Big|\frac{x-1}{x+2}\Big|+\frac{3}{x+2}+C .
$$

Two more verified results: $\int_0^6\frac{\mathrm dx}{x^2+5x+6}=\big[\ln\frac{x+2}{x+3}\big]_0^6=\ln\frac43\approx0.2877$ (Example 8.53(c)), and $\frac{2x^3}{x^3-1}=2+\frac{2/3}{x-1}-\frac23\cdot\frac{x+2}{x^2+x+1}$ (Exercise 117(i)).

The common trap is giving a repeated factor a single term: $\frac{x}{(x+1)^2}$ is $\frac{1}{x+1}-\frac{1}{(x+1)^2}$, and no choice of $A$ makes $\frac{A}{(x+1)^2}$ equal to it. The second is a constant numerator over an irreducible quadratic, which leaves more equations than unknowns. The same algebra inverts Laplace transforms in Year 2 ([[Partial Fractions for Inverse Laplace]]).

## Related

- Topics: [[MATH1054 M10 - Integration III]] ([[MATH1054 M10 - Integration III#2. Why the partial-fraction forms are what they are|derivation of the forms]], [[MATH1054 M10 - Integration III#5. Worked examples: rational functions (James Examples 8.53 and 8.55)|worked examples]]) · [[MATH1054 M10 Solutions - Integration III]]
- Concepts: [[Completing the Square]] · [[Partial Fractions for Inverse Laplace]] · [[Integration by Substitution]]
- Sources: James, *Modern Engineering Mathematics* (6th ed.) §2.5.1 pp. 114–119 and §8.8.8–8.8.9; MATH1054 Module Booklet, Module 10.
