---
title: "Poles and Zeros"
module: "SESA2027 Aerospace Mechanics & Control"
type: concept
stream: "Part A: Dynamic Systems"
aliases: ["poles", "zeros", "pole-zero map", "ZPK form", "s-plane"]
tags: [sesa2027, concept, transfer-function]
status: complete
parent_lectures: ["[[SESA2027 A4 - Laplace Transforms, Transfer Functions and Step Response]]", "[[SESA2027 A5 - Frequency Response and Bode Plots]]", "[[SESA2027 B2 - Root Locus Method]]"]
related_concepts: ["[[Transfer Function]]", "[[Root Locus]]", "[[Bode Plot]]", "[[Characteristic Equation and Eigenvalues]]"]
sources: ["02 - Sources/Lectures/Lecture 1.07.pdf", "02 - Sources/Lectures/Lecture 1.08.pdf", "02 - Sources/Lectures/Lecture 2.04.pdf"]
---

# Poles and Zeros

In zero–pole–gain (ZPK) form a transfer function is

$$
G(s) = k\frac{(s-z_1)\cdots(s-z_m)}{(s-p_1)\cdots(s-p_n)},\qquad m\le n .
$$

The **poles** $p_i$ (plotted ×) are the roots of the denominator, which are the system's natural modes and the eigenvalues of its state matrix. The **zeros** $z_j$ (plotted ○) are the roots of the numerator, and they set how strongly each mode appears in the output.

The poles decide stability and the character of the response. For $p = \sigma\pm i\omega$, $|p| = \omega_n$ and $\zeta = -\sigma/\omega_n$ ([[Damping Ratio and Natural Frequency]]).

| Location | Response |
|---|---|
| Left half-plane, real | Exponential decay, $e^{pt}$ |
| Left half-plane, complex | Decaying oscillation |
| Imaginary axis | Sustained oscillation (marginal) |
| Right half-plane | Growth (unstable) |

Zeros don't affect stability, but they change the transient. A left-half-plane zero near the dominant poles speeds the response up and adds overshoot; a right-half-plane zero (non-minimum phase) makes the response start off in the wrong direction. Feedback moves the poles but leaves the zeros of $GC$ where they are, which is the idea behind the [[Root Locus]]. On a [[Bode Plot]] each real pole contributes −20 dB/dec and −90°, each real zero +20 dB/dec and +90°, and a complex pair ±40 dB/dec and ±180°. A physical system has $n$ poles and, in the lecture's convention, at most $n-1$ zeros (strictly proper).

The Part B plant has poles at $-0.4025\pm1.0784i$, a zero at $-0.306$ and gain $-1.39$ ([[SESA2027 B2 - Root Locus Method]]). In PS2 Q3 the poles are $-0.3723\pm4.312i$, stable with $\zeta = 0.086$, and the zero is at $-0.161$ ([[SESA2027 Practice Problems 2 Solutions]]).

## Related

- [[Transfer Function]] · [[Root Locus]] · [[Bode Plot]] · [[Characteristic Equation and Eigenvalues]]
