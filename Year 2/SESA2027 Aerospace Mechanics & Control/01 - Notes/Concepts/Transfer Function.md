---
title: "Transfer Function"
module: "SESA2027 Aerospace Mechanics & Control"
type: concept
stream: "Part A: Dynamic Systems"
aliases: ["TF", "G(s)", "plant transfer function", "sensor transfer function"]
tags: [sesa2027, concept, transfer-function]
status: complete
parent_lectures: ["[[SESA2027 A2 - Longitudinal State-Space Model and Aerodynamic Derivatives]]", "[[SESA2027 A4 - Laplace Transforms, Transfer Functions and Step Response]]", "[[SESA2027 B1 - Control System Fundamentals and PID Control]]", "[[SESA2027 C2 - Sensor Characteristics, Dynamics and Design]]"]
related_concepts: ["[[Laplace Transform]]", "[[Poles and Zeros]]", "[[State-Space Representation]]", "[[Closed-Loop Transfer Function]]"]
sources: ["02 - Sources/Lectures/Lecture 1.07.pdf", "02 - Sources/Lectures/Lecture 1.11.pdf", "02 - Sources/Lectures/Lecture 3.05.pdf"]
---

# Transfer Function

## Definition

> [!note] Definition
> The ratio of the Laplace transforms of output and input, with zero initial conditions:
> $$G(s) = \frac{Y(s)}{U(s)} = \frac{B(s)}{A(s)} = \mathbf C(s\mathbf I-\mathbf A)^{-1}\mathbf B+\mathbf D$$
> It describes the input–output behaviour of an LTI system **independently of the input**.

## Explanation
- The denominator $A(s) = |s\mathbf I-\mathbf A|$ is the characteristic polynomial, so its roots are the **poles** (the eigenvalues). The numerator's roots are the **zeros**. See [[Poles and Zeros]].
- It is **causal** (proper): the degree of $B$ is at most the degree of $A$.
- **Standard second-order form**: $G = \dfrac{K\omega_n^2}{s^2+2\zeta\omega_ns+\omega_n^2}$, or $\dfrac{K(s+z)}{s^2+2\zeta\omega_ns+\omega_n^2}$ with a zero.
- **Frequency response**: substitute $s = i\omega$ ([[Frequency Response Function]]).
- **Block algebra**:
  - series blocks multiply;
  - feedback gives $\dfrac{G}{1+GH}$ ([[Closed-Loop Transfer Function]]).
- **Sensors** are usually identified experimentally as TFs (a black box) from sine sweeps or noise and a spectrum analyser ([[Sensor Dynamic Models]]).

## Examples
- Part B plant (SPO pitch rate): $G = \dfrac{-1.39(s+0.306)}{s^2+0.805s+1.325}$.
- PS2 Q3: $G = \dfrac{-4.888(s+0.1609)}{s^2+0.7446s+18.73}$ ([[SESA2027 Practice Problems 2 Solutions]]).
- First-order sensor or RC filter: $\dfrac{K}{\tau s+1}$.
- Pure delay: $e^{-sT_d}$.

## Related
- [[Laplace Transform]] · [[Poles and Zeros]] · [[State-Space Representation]] · [[Closed-Loop Transfer Function]] · [[Frequency Response Function]]

## Sources
- Lectures 1.07, 1.11, 3.05
