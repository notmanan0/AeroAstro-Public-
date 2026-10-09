---
title: "Characteristic Equation and Eigenvalues"
module: "SESA2027 Aerospace Mechanics & Control"
type: concept
stream: "Part A: Dynamic Systems"
aliases: ["characteristic polynomial", "stability quartic", "eigenvalues", "mode shape", "eigenvector"]
tags: [sesa2027, concept, stability]
status: complete
parent_lectures: ["[[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid]]"]
related_concepts: ["[[Damping Ratio and Natural Frequency]]", "[[Routh-Hurwitz Stability Criterion]]", "[[Poles and Zeros]]"]
sources: ["02 - Sources/Lectures/Lecture 1.05.pdf"]
---

# Characteristic Equation and Eigenvalues

## Definition

> [!note] Definition
> For $\dot{\mathbf x} = \mathbf A\mathbf x$, try $\mathbf x = \mathbf x_0e^{\lambda t}$. This gives $(\mathbf A-\lambda\mathbf I)\mathbf x_0 = 0$, and a non-trivial solution requires the **characteristic equation**
>
> $$\det(\lambda\mathbf I-\mathbf A) = 0$$
>
> Its roots $\lambda_i = \sigma_i\pm i\omega_i$ are the **eigenvalues**, and the corresponding eigenvectors are the **mode shapes**.

## Explanation
- **Stability**: every $\sigma_i<0$ means the system is stable. A single $\sigma_i>0$ makes it unstable. $\sigma = 0$ with $\omega\neq0$ is marginal (sustained oscillation).
- **Longitudinal aircraft**: a 4×4 matrix gives the **stability quartic** $A\lambda^4+B\lambda^3+C\lambda^2+D\lambda+E = 0$. It usually factors into two quadratics: the [[Short Period Oscillation]] (large $\omega_n$) and the [[Phugoid Mode]] (small $\omega_n$).
- The **eigenvalues of $\mathbf A$ equal the poles of every transfer function** from the same state space, since the denominator of $G(s)$ is $|s\mathbf I-\mathbf A|$.
- The **mode shape** (eigenvector) shows which states take part. For the F-4C SPO, the $w$ component has magnitude 0.9993 and $u$ only 0.035, which confirms constant speed.
- Stability can be checked without solving, using the [[Routh-Hurwitz Stability Criterion]].

## Examples
- L1.05: $\lambda^4+\lambda^3+2.01\lambda^2+0.01\lambda+0.01\approx(\lambda^2+\lambda+2)(\lambda^2+0.0025\lambda+0.005)$, giving the SPO $-0.5\pm1.32i$ and the phugoid $-0.00125\pm0.0707i$.
- PS1 Q1: $(\lambda^2+1.40\lambda+9.49)(\lambda^2-0.0016\lambda+0.0016)$ has an unstable phugoid with $\sigma = +8\times10^{-4}$ ([[SESA2027 Practice Problems 1 Solutions]]).

## Related
- [[Damping Ratio and Natural Frequency]] · [[Routh-Hurwitz Stability Criterion]] · [[Poles and Zeros]] · [[State-Space Representation]]

## Sources
- Lecture 1.05; MATH2048 (eigenvalue problems)
