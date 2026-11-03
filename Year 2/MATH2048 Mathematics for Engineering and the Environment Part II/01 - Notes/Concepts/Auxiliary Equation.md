---
title: "Auxiliary Equation"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: concept
stream: "Block 1: Ordinary Differential Equations"
aliases: ["Characteristic equation (ODE)", "Auxiliary equation", "Constant coefficient ODE"]
tags: [math2048, concept, odes]
status: complete
parent_lectures: ["[[MATH2048 ODE1 - Second-Order Linear ODEs with Constant Coefficients]]"]
related_concepts: ["[[Euler-Cauchy Equation]]", "[[ODE Eigenvalue Problems]]", "[[Characteristic Equation and Eigenvalues]]", "[[Damping Ratio and Natural Frequency]]"]
sources: ["02 - Sources/Lectures & Problem Sheets/ODEs/Lecture1_ODE.pdf", "02 - Sources/Lectures/MATH2048 Lecture 1.txt"]
---

# Auxiliary Equation

The **auxiliary equation** of a constant-coefficient ODE $ay''+by'+cy=0$ is the quadratic $a\lambda^2+b\lambda+c=0$, which comes from substituting $y=e^{\lambda x}$: the ODE becomes $(a\lambda^2+b\lambda+c)e^{\lambda x}=0$, and the exponential is never zero.

The guess works because differentiating an exponential just multiplies it by $\lambda$, so the differential equation collapses to a polynomial one. The sign of the discriminant then decides the form of the solution:

| $b^2-4ac$ | Roots | $y$ |
|---|---|---|
| $>0$ | $\lambda_1\neq\lambda_2$ real | $c_1e^{\lambda_1x}+c_2e^{\lambda_2x}$ |
| $=0$ | $\lambda$ repeated | $(c_1+c_2x)e^{\lambda x}$ |
| $<0$ | $\alpha\pm j\beta$ | $e^{\alpha x}(c_1\cos\beta x+c_2\sin\beta x)$ |

The repeated-root row needs a separate check. With $P(\lambda)=a\lambda^2+b\lambda+c$, substituting $xe^{\lambda x}$ gives $e^{\lambda x}[xP(\lambda)+P'(\lambda)]$, and both terms vanish only at a double root. The complex row comes from Euler's formula, $e^{(\alpha\pm j\beta)x}=e^{\alpha x}(\cos\beta x\pm j\sin\beta x)$, whose real combinations are the cosine and sine. The same polynomial evaluated at a forcing exponent $k$ decides whether a guess $Ce^{kx}$ clashes with the complementary function in the [[Method of Undetermined Coefficients]].

For example, $y''+4y'+13y=0$ has roots $-2\pm3j$ and $y=e^{-2x}(c_1\cos3x+c_2\sin3x)$, and the mass–spring–damper $\ddot y+\frac{2c}m\dot y+\omega_0^2y=0$ is under-damped, critical or over-damped according to whether $c$ is below, at or above $m\omega_0$.

## Related

- Derivations: [[MATH2048 ODE1 - Second-Order Linear ODEs with Constant Coefficients]]
- [[Euler-Cauchy Equation]] (the same polynomial after $t=\ln x$) · [[ODE Eigenvalue Problems]] · SESA2027: [[Characteristic Equation and Eigenvalues]], [[Damping Ratio and Natural Frequency]]
