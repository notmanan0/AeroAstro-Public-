---
title: "Trigonometric Integrals and Power Reduction"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 1: Calculus"
aliases: ["Product-to-sum", "Power reduction", "Trig integrals"]
tags: [math1054, concept, integration]
status: complete
parent_lectures: ["[[MATH1054 M04 - Integration I]]", "[[MATH1054 M09 - Integration II]]"]
related_concepts: ["[[Integration by Parts]]", "[[Integration by Substitution]]", "[[Orthogonality of Trigonometric Functions]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §8.8.10", "MATH1054 Module Booklet, Modules 4 and 9"]
---

# Trigonometric Integrals and Power Reduction

Products and powers of sines and cosines are integrated by first rewriting them, with the product-to-sum and double-angle identities, as sums of single sines and cosines of multiple angles, each of which integrates directly.

All the identities come from the compound-angle formulae $\sin(A\pm B)=\sin A\cos B\pm\cos A\sin B$ and $\cos(A\pm B)=\cos A\cos B\mp\sin A\sin B$. Adding or subtracting a pair cancels one product and doubles the other:

$$
\begin{aligned}
2\sin A\cos B&=\sin(A+B)+\sin(A-B),\\
2\cos A\cos B&=\cos(A+B)+\cos(A-B),\\
2\sin A\sin B&=\cos(A-B)-\cos(A+B).
\end{aligned}
$$

Setting $B=A$ in the last two gives the power-reduction formulae $\cos^2A=\frac12(1+\cos2A)$ and $\sin^2A=\frac12(1-\cos2A)$, which halve a power at the cost of doubling the angle.

| Integrand | Technique |
|---|---|
| $\sin^2x$, $\cos^2x$, $\cos^4x$ | power reduction, applied repeatedly |
| $\sin mx\cos nx$, $\cos mx\cos nx$, $\sin mx\sin nx$ | product-to-sum |
| $\sin^mx\cos^nx$ with one power odd | keep one factor of the odd-power function, convert the rest with $\sin^2x+\cos^2x=1$, substitute $u=\sin x$ or $u=\cos x$ |

Even powers need repeated reduction. For $\cos^4x$ (Module 4, Exercise A):

$$
\begin{aligned}
\cos^4x&=\tfrac14(1+\cos2x)^2\\
&=\tfrac14\big(1+2\cos2x+\tfrac12(1+\cos4x)\big)\\
&=\tfrac38+\tfrac12\cos2x+\tfrac18\cos4x,\\
\int\cos^4x\,\mathrm dx&=\tfrac38x+\tfrac14\sin2x+\tfrac1{32}\sin4x+C .
\end{aligned}
$$

Products of different frequencies become sums: $\int\cos7x\cos5x\,\mathrm dx=\frac12\int(\cos12x+\cos2x)\,\mathrm dx=\frac1{24}\sin12x+\frac14\sin2x+C$ (Exercise 119(b)). An odd power uses a substitution instead: $\int\sin^2x\cos^3x\,\mathrm dx=\int\sin^2x(1-\sin^2x)\cos x\,\mathrm dx=\frac13\sin^3x-\frac15\sin^5x+C$ (Exercise 122(b), Module 9).

Over $[0,\pi]$ the sine–sine identity gives **orthogonality**: for integers $m,n\ge1$, $\int_0^\pi\sin mx\sin nx\,\mathrm dx=0$ when $m\neq n$ and $\frac\pi2$ when $m=n$, because every term becomes a sine of an integer multiple of $\pi$. Thus $\int_0^\pi\sin5x\sin6x\,\mathrm dx=0$ and $\int_0^\pi\sin^25x\,\mathrm dx=\frac\pi2$ (Exercise 120). This is the property that isolates each coefficient of a Fourier series ([[Orthogonality of Trigonometric Functions]]).

Two traps recur. The sine–sine identity is misprinted in some versions of the Data Book; checking it at $B=A$, where it must give $2\sin^2A=1-\cos2A$, fixes the order of the two cosines. And orthogonality on $[0,\pi]$ holds for two sines or two cosines, not for a sine against a cosine: $\int_0^\pi\sin3x\cos2x\,\mathrm dx=\frac65$.

## Related

- Topics: [[MATH1054 M04 - Integration I]] (derivations and all set examples, §5) · [[MATH1054 M09 - Integration II]] (odd powers by substitution)
- Concepts: [[Integration by Parts]] · [[Integration by Substitution]] · [[Orthogonality of Trigonometric Functions]]
- Sources: James, *Modern Engineering Mathematics* (6th ed.) §8.8.10 (Example 8.56, Exercises 119–120); MATH1054 Module Booklet, Modules 4 (work scheme item 6, Exercise A) and 9; worked solutions in [[MATH1054 M04 Solutions - Integration I]].
