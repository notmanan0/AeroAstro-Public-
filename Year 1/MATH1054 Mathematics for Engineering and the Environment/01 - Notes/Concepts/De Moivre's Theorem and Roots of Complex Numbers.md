---
title: "De Moivre's Theorem and Roots of Complex Numbers"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 2: Complex Numbers"
aliases: ["De Moivre", "nth roots", "Roots of unity"]
tags: [math1054, concept, complex-numbers]
status: complete
parent_lectures: ["[[MATH1054 M22 - Complex Numbers II]]"]
related_concepts: ["[[Euler's Formula]]", "[[Complex Numbers - Cartesian, Polar and Exponential Forms]]", "[[Argand Diagram]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §3.2.11", "MATH1054 Module Booklet, Module 22"]
---

# De Moivre's Theorem and Roots of Complex Numbers

## Definition

> [!note] Definition
>
> $$(\cos\theta+\mathrm j\sin\theta)^n=\cos n\theta+\mathrm j\sin n\theta,\qquad z^{1/n}=r^{1/n}\,e^{\mathrm j(\theta+2k\pi)/n},\ k=0,\dots,n-1$$

## Explanation
- Powers: raise the modulus to the power $n$, and multiply the argument by $n$.
- **$n$ distinct roots**, equally spaced by $\frac{2\pi}n$ on the circle of radius $r^{1/n}$.
- **Rational powers** $z^{p/q}$ in lowest terms have $q$ distinct values.
- **Complex quadratics**: find $\sqrt\Delta$ from $(a+b\mathrm j)^2=\Delta$ together with $a^2+b^2=|\Delta|$. Check with Vieta.

## Examples
- $(1-\mathrm j)^{12}=64e^{-3\pi\mathrm j}=-64$ (Ex 3.19).
- $(8+8\mathrm j)^{1/3}$: modulus $2^{7/6}$, arguments $15°,135°,255°$ (Ex 37).
- $z^2+(2\mathrm j-3)z+5-\mathrm j=0$ gives $z=1+\mathrm j$ or $2-3\mathrm j$ (Ex 3.22).

## Related
- Topics: [[MATH1054 M22 - Complex Numbers II]]
- Concepts: [[Euler's Formula]] · [[Complex Numbers - Cartesian, Polar and Exponential Forms]] · [[Argand Diagram]]

## Sources
- James, Modern Engineering Mathematics (6th ed.) §3.2.11
- MATH1054 Module Booklet, Module 22
