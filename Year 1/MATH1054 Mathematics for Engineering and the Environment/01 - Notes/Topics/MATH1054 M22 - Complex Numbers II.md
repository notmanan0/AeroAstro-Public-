---
title: "MATH1054 M22 - Complex Numbers II"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: topic
stream: "Block 2: Complex Numbers"
order: 22
tags:
  - math1054
  - complex-numbers
  - de-moivre
  - loci
aliases: ["MATH1054 Module 22", "Complex Numbers II"]
date: 2026-09-27
status: complete
parent: ["[[MATH1054 Mathematics for Engineering and the Environment Hub]]"]
prerequisites: ["[[MATH1054 M05 - Complex Numbers I]]", "[[MATH1054 M07 - Functions]]"]
next_topics: ["[[MATH1054 M24 - Statistics I]]"]
key_concepts: ["[[De Moivre's Theorem and Roots of Complex Numbers]]", "[[Complex Functions - Trig, Hyperbolic and Logarithm]]", "[[Loci in the Complex Plane]]"]
tutorial_sheets: ["[[MATH1054 M22 Solutions - Complex Numbers II]]"]
sources: ["02 - Sources/Course Booklets & Solutions/Module Booklet.pdf (Module 22)", "02 - Sources/Modern Engineering Mathematics.pdf (§3.2.9–3.2.12)"]
---

# MATH1054 M22 - Complex Numbers II

> [!abstract] Summary
> Euler's formula lets every elementary function be extended to complex arguments:
> - $\sin$, $\cos$, $\sinh$ and $\cosh$ become closely linked, and $\cos z=2$ has solutions;
> - $\ln z$ becomes **multi-valued**;
> - **De Moivre's theorem** gives powers, and the $n$ distinct **$n$th roots** sit evenly spaced on a circle;
> - equations in $z$ describe curves (**loci**) in the Argand plane: lines, circles, and circles of Apollonius.

## Key Concepts
- [[De Moivre's Theorem and Roots of Complex Numbers]] · [[Complex Functions - Trig, Hyperbolic and Logarithm]] · [[Loci in the Complex Plane]] · [[Euler's Formula]]

---

## 1. Complex elementary functions (James §3.2.9–3.2.10)
Putting $\theta=\mathrm jy$ into Euler's formula gives the bridges between trig and hyperbolic functions:
$$
\cos\mathrm jy=\cosh y,\qquad\sin\mathrm jy=\mathrm j\sinh y,\qquad\cosh\mathrm jy=\cos y,\qquad\sinh\mathrm jy=\mathrm j\sin y
$$
With the addition formulae, for $z=x+\mathrm jy$:
$$
\sin z=\sin x\cosh y+\mathrm j\cos x\sinh y,\qquad\cos z=\cos x\cosh y-\mathrm j\sin x\sinh y
$$
- $|\sin z|$ and $|\cos z|$ are **unbounded**, so $\sin z=2$ and $\cos z=2$ have solutions, e.g. $z=\frac\pi2+2k\pi\pm1.317\mathrm j$.
- **Method**: equate real and imaginary parts, kill the imaginary equation by choosing the right factor to be zero, then solve the real one.

**Logarithm**. Since $e^{z+2k\pi\mathrm j}=e^z$, the log is multi-valued:
$$
\ln z=\ln|z|+\mathrm j(\operatorname{Arg}z+2k\pi),\qquad\text{principal value: }k=0,\ -\pi<\operatorname{Arg}z\le\pi
$$

## 2. De Moivre's theorem and roots (James §3.2.11)
$$
(\cos\theta+\mathrm j\sin\theta)^n=\cos n\theta+\mathrm j\sin n\theta\quad\Longleftrightarrow\quad(re^{\mathrm j\theta})^n=r^ne^{\mathrm jn\theta}
$$
**$n$th roots**: $z^{1/n}$ has exactly $n$ distinct values:
$$
z^{1/n}=r^{1/n}\exp\Big(\mathrm j\,\frac{\theta+2k\pi}{n}\Big),\qquad k=0,1,\dots,n-1
$$
They lie on a circle of radius $r^{1/n}$, spaced $\frac{2\pi}n$ apart, forming a regular $n$-gon. For a rational power $z^{p/q}$ in lowest terms, there are $q$ distinct values.

![[m1054_complex_roots.png|800]]

**Quadratics with complex coefficients**: use the usual formula. Find $\sqrt\Delta$ by solving $(a+b\mathrm j)^2=\Delta$, using the extra equation $a^2+b^2=|\Delta|$. Check with Vieta: the sum of the roots is $-b/a$ and their product is $c/a$.

## 3. Loci (James §3.2.12)
| Equation | Locus |
|---|---|
| $\lvert z-z_0\rvert=r$ | circle, centre $z_0$, radius $r$ |
| $\lvert z-a\rvert=\lvert z-b\rvert$ | perpendicular bisector of $a$ and $b$ |
| $\lvert z-a\rvert=k\lvert z-b\rvert$, $k\neq1$ | **circle of Apollonius** |
| $\arg(z-z_0)=\alpha$ | half-line from $z_0$ (excluding $z_0$) |
| $\operatorname{Re}z=c$, $\operatorname{Im}(az)=c$ | straight lines |
| $\operatorname{Re}$ or $\operatorname{Im}$ of $\dfrac{z-a}{z-b}=0$ | circle or line through $a$ and $b$, **minus** the point $b$ |

**Method**: substitute $z=x+\mathrm jy$. For $|\cdot|$, square both sides. For $\operatorname{Re}$ or $\operatorname{Im}$ of a quotient, multiply by the conjugate of the denominator. Then complete the square. Always check for excluded points where a denominator vanishes.

![[m1054_complex_loci.png|800]]

## Links
- Parent: [[MATH1054 Mathematics for Engineering and the Environment Hub]] · Solutions: [[MATH1054 M22 Solutions - Complex Numbers II]]
- Prev: [[MATH1054 M05 - Complex Numbers I]]
- Applied: [[Phasor Representation]], [[Complex Impedance]]; later [[Poles and Zeros]] and [[Root Locus]] (SESA2027) live in the complex plane

## Sources
- MATH1054 Module Booklet, Module 22; James §3.2.9–3.2.12
