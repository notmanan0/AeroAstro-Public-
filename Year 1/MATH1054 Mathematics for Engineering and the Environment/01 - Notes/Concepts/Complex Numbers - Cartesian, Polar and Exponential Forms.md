---
title: "Complex Numbers - Cartesian, Polar and Exponential Forms"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 2: Complex Numbers"
aliases: ["Complex number forms", "Polar form", "Modulus and argument", "Exponential form"]
tags: [math1054, concept, complex-numbers]
status: complete
parent_lectures: ["[[MATH1054 M05 - Complex Numbers I]]", "[[MATH1054 M22 - Complex Numbers II]]"]
related_concepts: ["[[Argand Diagram]]", "[[Euler's Formula]]", "[[De Moivre's Theorem and Roots of Complex Numbers]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §3.2", "MATH1054 Module Booklet, Module 5"]
---

# Complex Numbers - Cartesian, Polar and Exponential Forms

## Definition

> [!note] Definition
>
> $$z=x+\mathrm jy=r(\cos\theta+\mathrm j\sin\theta)=re^{\mathrm j\theta},\qquad r=|z|=\sqrt{x^2+y^2},\quad\theta=\arg z$$
>
> The **principal argument** lies in $(-\pi,\pi]$.

## Explanation
- **Cartesian** is best for $+$, $-$ and equating parts. **Polar/exponential** is best for $\times$, $\div$, powers and roots.
- **Quadrant rule**: with $\alpha=\tan^{-1}|y/x|$, the argument is $\theta=\alpha$ (Q1), $\pi-\alpha$ (Q2), $-(\pi-\alpha)$ (Q3), $-\alpha$ (Q4).
- **Division**: multiply the top and bottom by the conjugate. $\frac{z_1}{z_2}=\frac{z_1z_2^*}{|z_2|^2}$.
- **Products**: moduli multiply and arguments add. Reduce the result to $(-\pi,\pi]$.
- **Equality** $z_1=z_2$ gives **two** real equations.

## Examples
- $-\sqrt6-\mathrm j\sqrt2=2\sqrt2\angle(-\frac{5\pi}6)$ (Ex 3.10(d)).
- $\frac{(1+2\mathrm j)^2(4-3\mathrm j)^3}{(3+4\mathrm j)^4(2-\mathrm j)^3}$ has modulus $\frac{\sqrt5}{25}$ and argument $-2.034$ (Ex 3.14).
- $e^{2+\mathrm j\pi/3}=3.695+6.399\mathrm j$ (Ex 3.16).

## Related
- Topics: [[MATH1054 M05 - Complex Numbers I]] · [[MATH1054 M22 - Complex Numbers II]]
- Concepts: [[Argand Diagram]] · [[Euler's Formula]] · [[De Moivre's Theorem and Roots of Complex Numbers]]

## Sources
- James, Modern Engineering Mathematics (6th ed.) §3.2
- MATH1054 Module Booklet, Module 5
