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

## Definition

> [!note] Definition
> In zero–pole–gain (ZPK) form,
>
> $$G(s) = k\frac{(s-z_1)\cdots(s-z_m)}{(s-p_1)\cdots(s-p_n)},\qquad m\le n$$
>
> - The **poles** $p_i$ (plotted ×) are the roots of the denominator: the system's natural modes and eigenvalues.
> - The **zeros** $z_j$ (plotted ○) are the roots of the numerator: they shape how strongly each mode appears in the output.

## Explanation
- **Poles decide stability and the character of the response.** Pole position in the s-plane:

| Location | Response |
|---|---|
| Left half-plane, real | Exponential decay, $e^{pt}$ |
| Left half-plane, complex | Decaying oscillation |
| Imaginary axis | Sustained oscillation (marginal) |
| Right half-plane | Growth (unstable) |

- For $p = \sigma\pm i\omega$: $|p| = \omega_n$ and $\zeta = -\sigma/\omega_n$ ([[Damping Ratio and Natural Frequency]]).
- **Zeros do not affect stability** but change the transient:
  - a left-half-plane zero near the dominant poles adds overshoot or speeds the response;
  - a **right-half-plane zero** (non-minimum phase) gives an initial response in the wrong direction.
- **Closed loop**: feedback moves the poles; the zeros of $GC$ stay. That is the idea behind the [[Root Locus]].
- **Bode plot** contributions:
  - each real pole gives −20 dB/dec and −90°;
  - each real zero gives +20 dB/dec and +90°;
  - a complex pair gives ±40 dB/dec and ±180° ([[Bode Plot]]).
- **Causality**: $n$ poles and at most $n-1$ zeros in the lecture's convention (strictly proper).

## Examples
- Part B plant: poles $-0.4025\pm1.0784i$, zero $-0.306$, gain $-1.39$ ([[SESA2027 B2 - Root Locus Method]]).
- PS2 Q3: poles $-0.3723\pm4.312i$ (stable, $\zeta = 0.086$), zero $-0.161$ ([[SESA2027 Practice Problems 2 Solutions]]).

## Related
- [[Transfer Function]] · [[Root Locus]] · [[Bode Plot]] · [[Characteristic Equation and Eigenvalues]]

## Sources
- Lectures 1.07, 1.08, 2.04
