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
sources: ["02 - Sources/Lectures & Problem Sheets/Fourier Series/Lecture6_FourierSeries3.pdf", "02 - Sources/Lectures & Problem Sheets/Fourier Series/Lecture7_FourierSeries4.pdf", "02 - Sources/Lectures/MATH2048 Lecture 6.txt", "02 - Sources/Lectures/MATH2048 Lecture 7.txt"]
---

# Fourier's Theorem

Fourier's theorem says when a Fourier series converges and to what. If $f$ satisfies the **Dirichlet conditions**, being bounded, periodic, and having finitely many maxima, minima and discontinuities per period, then its series converges to $f(x)$ wherever $f$ is continuous and to the average $\frac12[f(x^-)+f(x^+)]$ at a jump.

Jumps can hide at the ends of the period. If $f(-\ell^+)\neq f(\ell^-)$, the periodic extension jumps there even though $f$ looks smooth on the interval; $x$ and $e^x$ on $(-\pi,\pi)$ both do this. The sawtooth series at $x=\pi$ therefore gives $\frac12(\pi+(-\pi))=0$, and the $e^x$ series at $\pm\pi$ gives $\cosh\pi$ (PS3 Q1). Next to a jump the partial sums overshoot by about 9 % of the jump height however many terms are taken, the Gibbs phenomenon (not examinable).

The theorem also decides what calculus is allowed. Integrating a series term by term is always valid. Differentiating it term by term additionally needs $f$ to be continuous everywhere, including across the period ends, and piecewise smooth; without that the differentiated series diverges, as differentiating the sawtooth's series shows, with partial sums $2,0,2,0,\dots$ at $x=0$.

![[m2048_fs_sawtooth_gibbs.png|560]]

## Related

- [[MATH2048 FS2 - Even and Odd Functions, Half-Range Series and Convergence#4. When does a Fourier series converge? (L6)|FS2 §4]] · [[MATH2048 FS3 - Calculus with Fourier Series and Complex Fourier Series#2. Differentiating a Fourier series (L7)|FS3 §2]]
- [[Fourier Series]] · [[Half-Range Expansions]]
