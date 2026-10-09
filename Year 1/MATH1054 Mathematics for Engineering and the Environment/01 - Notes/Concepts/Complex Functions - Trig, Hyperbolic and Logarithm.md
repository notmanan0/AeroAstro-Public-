---
title: "Complex Functions - Trig, Hyperbolic and Logarithm"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 2: Complex Numbers"
aliases: ["Complex logarithm", "Complex sine", "sin z", "ln z"]
tags: [math1054, concept, complex-numbers]
status: complete
parent_lectures: ["[[MATH1054 M22 - Complex Numbers II]]"]
related_concepts: ["[[Euler's Formula]]", "[[Hyperbolic Functions]]", "[[De Moivre's Theorem and Roots of Complex Numbers]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §3.2.9–3.2.10", "MATH1054 Module Booklet, Module 22"]
---

# Complex Functions - Trig, Hyperbolic and Logarithm

## Definition

> [!note] Definition
> For $z=x+\mathrm jy$:
>
> $$\sin z=\sin x\cosh y+\mathrm j\cos x\sinh y,\quad\cos z=\cos x\cosh y-\mathrm j\sin x\sinh y,\quad\ln z=\ln|z|+\mathrm j(\operatorname{Arg}z+2k\pi)$$

## Explanation
- $\sin z$ and $\cos z$ are **unbounded** for complex $z$. So equations like $\sin z=2$ have solutions.
- **Solving $f(z)=c$**: equate real and imaginary parts. Choose the factor that kills the imaginary equation, then solve the real one.
- The **log is multi-valued**; the principal value takes $k=0$. For example, $\ln(-1)=\mathrm j\pi$.

## Examples
- $\cos z=2$ gives $z=2k\pi\pm\mathrm j\ln(2+\sqrt3)$ (Ex 3.17(d)). $\sin z=2$ gives $z=\frac\pi2+2k\pi\pm1.317\mathrm j$ (Ex 30(a)).
- $\ln(-3+4\mathrm j)=1.609+\mathrm j(2.214+2k\pi)$ (Ex 3.18).

## Related
- Topics: [[MATH1054 M22 - Complex Numbers II]]
- Concepts: [[Euler's Formula]] · [[Hyperbolic Functions]] · [[De Moivre's Theorem and Roots of Complex Numbers]]

## Sources
- James, Modern Engineering Mathematics (6th ed.) §3.2.9–3.2.10
- MATH1054 Module Booklet, Module 22
