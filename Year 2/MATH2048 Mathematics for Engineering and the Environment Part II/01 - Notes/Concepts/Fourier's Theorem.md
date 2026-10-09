---
title: "Fourier's Theorem"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: concept
stream: "Block 2: Fourier Series"
aliases: ["Dirichlet conditions", "Convergence of Fourier series", "Gibbs phenomenon", "Term-by-term differentiation"]
tags: [math2048, concept, fourier-series]
status: complete
parent_lectures: ["[[MATH2048 FS2 - Even and Odd Functions, Half-Range Series and Convergence]]", "[[MATH2048 FS3 - Calculus with Fourier Series and Complex Fourier Series]]"]
related_concepts: ["[[Fourier Series]]"]
sources: ["02 - Sources/Lectures & Problem Sheets/Fourier Series/Lecture6_FourierSeries3.pdf", "02 - Sources/Lectures & Problem Sheets/Fourier Series/Lecture7_FourierSeries4.pdf"]
---

# Fourier's Theorem

## Definition

> [!note] Definition
> Suppose $f$ satisfies the **Dirichlet conditions**:
> 1. it is bounded;
> 2. it is $2\ell$-periodic;
> 3. it has finitely many extrema and discontinuities per period.
>
> Then its Fourier series converges to $f(x)$ wherever $f$ is continuous, and to $\frac12[f(x^-)+f(x^+)]$ at a jump.

## Explanation
- **Hidden jumps**: always check the ends of the period. If $f(-\ell^+)\neq f(\ell^-)$, the periodic extension jumps there. Examples: $x$ and $e^x$ on $(-\pi,\pi)$.
- **Gibbs phenomenon** (not examinable): next to a jump, the partial sums overshoot by about 8.95% of the jump height, however many terms you take.
- **Integration**: term-by-term integration is always valid.
- **Differentiation**: term-by-term differentiation additionally needs:
  - $f$ continuous everywhere, *including* across the period ends;
  - $f'$ piecewise smooth.

  Without these the differentiated series diverges. Differentiating the sawtooth series gives partial sums $2,0,2,0,\dots$

## Examples
- The sawtooth series at $x=\pi$ gives $\frac12(\pi+(-\pi))=0$.
- The $e^x$ series at $x=\pm\pi$ gives $\cosh\pi$ (PS3 Q1).

![[m2048_fs_sawtooth_gibbs.png|560]]

## Related
- [[Fourier Series]] · [[Half-Range Expansions]]

## Sources
- Lectures 6–7
