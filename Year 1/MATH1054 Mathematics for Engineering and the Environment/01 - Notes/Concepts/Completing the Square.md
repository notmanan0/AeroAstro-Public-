---
title: "Completing the Square"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 1: Calculus"
aliases: ["Complete the square"]
tags: [math1054, concept, integration]
status: complete
parent_lectures: ["[[MATH1054 M10 - Integration III]]"]
related_concepts: ["[[Partial Fractions]]", "[[Integration by Substitution]]", "[[Inverse Trigonometric Functions]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §8.8", "MATH1054 Module Booklet, Module 10"]
---

# Completing the Square

Completing the square rewrites a quadratic as a constant multiple of a perfect square plus a constant, $ax^2+bx+c=a\big[(x+\frac{b}{2a})^2+\frac{4ac-b^2}{4a^2}\big]$, which is a shift of origin to the vertex of the parabola.

The identity follows by taking out $a$ and then adding and subtracting the square of half the new $x$ coefficient:

$$
\begin{aligned}
ax^2+bx+c&=a\Big[x^2+\frac bax+\frac ca\Big]\\
&=a\Big[\Big(x+\frac b{2a}\Big)^2-\frac{b^2}{4a^2}+\frac ca\Big]\\
&=a\Big[\Big(x+\frac b{2a}\Big)^2+\frac{4ac-b^2}{4a^2}\Big].
\end{aligned}
$$

With $u=x+\frac{b}{2a}$, the sign of $b^2-4ac$ decides the shape: $u^2+k^2$ when it is negative, $u^2-k^2$ when it is positive, and $k^2-u^2$ after taking out $-1$ when $a<0$. Each shape matches a standard integral, found by the substitution shown ($k>0$):

| After completing the square | Integral | Substitution |
|---|---|---|
| $\frac1{u^2+k^2}$ | $\frac1k\tan^{-1}\frac uk$ | $u=k\tan\theta$ |
| $\frac1{u^2-k^2}$ | $\frac1{2k}\ln\big\lvert\frac{u-k}{u+k}\big\rvert$ | partial fractions |
| $\frac1{\sqrt{k^2-u^2}}$ | $\sin^{-1}\frac uk$ | $u=k\sin\theta$ |
| $\frac1{\sqrt{u^2+k^2}}$ | $\sinh^{-1}\frac uk$ | $u=k\sinh t$ |
| $\frac1{\sqrt{u^2-k^2}}$ | $\cosh^{-1}\frac uk$ | $u=k\cosh t$ |

For instance $u=k\tan\theta$ gives $\mathrm du=k\sec^2\theta\,\mathrm d\theta$ and $u^2+k^2=k^2\sec^2\theta$, so the integrand collapses to $1/k$ and the integral is $\theta/k$. If only the $k=1$ form is to hand, the substitution $u=kv$ rescales to it: $\int\frac{\mathrm dx}{x^2+16}=\frac14\tan^{-1}\frac x4$ with $x=4v$.

Worked example (Exercise 105(e)): $3+2x-x^2=-\big[(x-1)^2-4\big]=4-(x-1)^2$, so with $u=x-1$ and $k=2$,

$$
\int_0^2\frac{\mathrm dx}{\sqrt{3+2x-x^2}}=\Big[\sin^{-1}\frac{x-1}{2}\Big]_0^2=\frac\pi6+\frac\pi6=\frac\pi3 .
$$

Similarly $x^2+6x+13=(x+3)^2+4$ gives $\int\frac{\mathrm dx}{x^2+6x+13}=\frac12\tan^{-1}\frac{x+3}2+C$ (Exercise 106(l)), and $4x^2+4x+2=(2x+1)^2+1$ gives $\frac12\tan^{-1}(2x+1)+C$ (Specimen Test 10, Q1).

The common trap is the leading coefficient. With $a\ne1$ it must be taken out before halving the $x$ coefficient, and with $a<0$ the sign must be carried through, otherwise $3+2x-x^2$ wrongly becomes $(x-1)^2+\dots$ and the inverse sine turns into an inverse hyperbolic function. The second trap is forgetting the factor $1/k$ (or the Jacobian of $u=2x+1$) after the shift.

Completing the square also locates circles in the complex-number loci: $x^2+y^2-4x-6y+9=0$ becomes $(x-2)^2+(y-3)^2=4$, a circle of centre $(2,3)$ and radius $2$ ([[Loci in the Complex Plane]]). The same move puts an irreducible quadratic from the Laplace domain into the shifted form $(s+c)^2+b^2$ in Year 2.

## Related

- Topics: [[MATH1054 M10 - Integration III]] ([[MATH1054 M10 - Integration III#4. Completing the square and the standard forms|completing the square and the standard forms]]) · [[MATH1054 M10 Solutions - Integration III]]
- Concepts: [[Partial Fractions]] · [[Integration by Substitution]] · [[Inverse Trigonometric Functions]] · [[Hyperbolic Functions]] · [[Loci in the Complex Plane]]
- Sources: James, *Modern Engineering Mathematics* (6th ed.) §8.8 (Exercises 105–106); MATH1054 Module Booklet, Module 10 work scheme §1 and the Stroud work scheme.
