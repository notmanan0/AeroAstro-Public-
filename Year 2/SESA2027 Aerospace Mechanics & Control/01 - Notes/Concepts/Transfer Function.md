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

A transfer function is the ratio of the Laplace transforms of output and input with zero initial conditions,

$$
G(s) = \frac{Y(s)}{U(s)} = \frac{B(s)}{A(s)} = \mathbf C(s\mathbf I-\mathbf A)^{-1}\mathbf B+\mathbf D,
$$

and it describes an LTI system's input–output behaviour independently of the input applied.

The denominator $A(s) = |s\mathbf I-\mathbf A|$ is the characteristic polynomial, so its roots, the poles, are the eigenvalues of the state matrix; the numerator's roots are the zeros ([[Poles and Zeros]]). A physical system is causal, or proper, meaning the degree of $B$ is at most that of $A$. Substituting $s = i\omega$ gives the [[Frequency Response Function]]. Blocks in series multiply, and a feedback loop gives $G/(1+GH)$ ([[Closed-Loop Transfer Function]]).

The standard second-order form is $K\omega_n^2/(s^2+2\zeta\omega_ns+\omega_n^2)$, or $K(s+z)/(s^2+2\zeta\omega_ns+\omega_n^2)$ with a zero. The Part B plant, the SPO pitch-rate response, is $G = -1.39(s+0.306)/(s^2+0.805s+1.325)$, and PS2 Q3 gives $G = -4.888(s+0.1609)/(s^2+0.7446s+18.73)$ ([[SESA2027 Practice Problems 2 Solutions]]). A first-order sensor or RC filter is $K/(\tau s+1)$, and a pure delay is $e^{-sT_d}$. Sensors are usually identified experimentally as black-box transfer functions, from sine sweeps or noise and a spectrum analyser ([[Sensor Dynamic Models]]).

## Related

- [[Laplace Transform]] · [[Poles and Zeros]] · [[State-Space Representation]] · [[Closed-Loop Transfer Function]] · [[Frequency Response Function]]
