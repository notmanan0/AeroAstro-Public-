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

For a free linear system $\dot{\mathbf x} = \mathbf A\mathbf x$, the **characteristic equation** $\det(\lambda\mathbf I-\mathbf A) = 0$ gives the eigenvalues $\lambda_i = \sigma_i\pm i\omega_i$, which set how each mode grows or decays and oscillates. The matching eigenvectors are the mode shapes.

It comes from trying a solution $\mathbf x = \mathbf x_0e^{\lambda t}$. Substituting gives $(\mathbf A-\lambda\mathbf I)\mathbf x_0 = 0$, and a non-zero $\mathbf x_0$ exists only if the determinant vanishes. The system is stable when every $\sigma_i<0$; a single $\sigma_i>0$ makes it unstable, and $\sigma = 0$ with $\omega\neq0$ is marginal, a sustained oscillation. The [[Routh-Hurwitz Stability Criterion]] answers the stability question from the coefficients without solving for the roots.

For the longitudinal aircraft, $\mathbf A$ is 4×4 and the characteristic equation is the stability quartic $A\lambda^4+B\lambda^3+C\lambda^2+D\lambda+E = 0$. It usually factors into two quadratics, the [[Short Period Oscillation]] (large $\omega_n$) and the [[Phugoid Mode]] (small $\omega_n$). In L1.05,

$$
\lambda^4+\lambda^3+2.01\lambda^2+0.01\lambda+0.01\approx(\lambda^2+\lambda+2)(\lambda^2+0.0025\lambda+0.005),
$$

giving the SPO at $-0.5\pm1.32i$ and the phugoid at $-0.00125\pm0.0707i$. In PS1 Q1 the factors are $(\lambda^2+1.40\lambda+9.49)(\lambda^2-0.0016\lambda+0.0016)$, and the phugoid is unstable with $\sigma = +8\times10^{-4}$ ([[SESA2027 Practice Problems 1 Solutions]]).

The same eigenvalues turn up as the poles of every transfer function built from that state space, because the denominator of $G(s)$ is $|s\mathbf I-\mathbf A|$. The eigenvector says which states take part in a mode: for the F-4C SPO the $w$ component has magnitude 0.9993 and $u$ only 0.035, which is the constant-speed assumption of the SPO approximation confirmed.

## Related

- [[Damping Ratio and Natural Frequency]] · [[Routh-Hurwitz Stability Criterion]] · [[Poles and Zeros]] · [[State-Space Representation]]
- Eigenvalue problems in maths: MATH2048
