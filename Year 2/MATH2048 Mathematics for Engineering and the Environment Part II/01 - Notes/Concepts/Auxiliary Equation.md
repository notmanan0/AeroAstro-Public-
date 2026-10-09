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
sources: ["02 - Sources/Lectures & Problem Sheets/ODEs/Lecture1_ODE.pdf"]
---

# Auxiliary Equation

## Definition

> [!note] Definition
> For $ay''+by'+cy=0$ with $a,b,c$ constant, substituting $y=e^{\lambda x}$ gives $(a\lambda^2+b\lambda+c)e^{\lambda x}=0$. Since $e^{\lambda x}\neq0$, $\lambda$ must satisfy
>
> $$a\lambda^2+b\lambda+c=0 .$$

## Explanation
The ansatz works because $e^{\lambda x}$ is an eigenfunction of $d/dx$: differentiating just multiplies it by $\lambda$. So the ODE collapses to a polynomial equation.

| $b^2-4ac$ | Roots | $y$ |
|---|---|---|
| $>0$ | $\lambda_1\neq\lambda_2$ real | $c_1e^{\lambda_1x}+c_2e^{\lambda_2x}$ |
| $=0$ | $\lambda$ repeated | $(c_1+c_2x)e^{\lambda x}$ |
| $<0$ | $\alpha\pm j\beta$ | $e^{\alpha x}(c_1\cos\beta x+c_2\sin\beta x)$ |

- **Repeated root, why the $x$**: $L[xe^{\lambda x}]=e^{\lambda x}\big[x\,P(\lambda)+P'(\lambda)\big]$ with $P(\lambda)=a\lambda^2+b\lambda+c$. Both terms vanish only at a double root.
- **Complex roots, why cos/sin**: by Euler's formula, $e^{(\alpha\pm j\beta)x}=e^{\alpha x}(\cos\beta x\pm j\sin\beta x)$. Real combinations give cos and sin.
- The same polynomial evaluated at the forcing exponent $k$, $P(k)$, decides whether an undetermined-coefficient trial $Ce^{kx}$ clashes with the CF ([[Method of Undetermined Coefficients]]).

## Examples
- $y''+4y'+13y=0$ gives $-2\pm3j$, so $y=e^{-2x}(c_1\cos3x+c_2\sin3x)$.
- The mass–spring–damper $\ddot y+\tfrac{2c}m\dot y+\omega_0^2y=0$ is under-damped, critical or over-damped as $c\lessgtr m\omega_0$.

## Related
- [[Euler-Cauchy Equation]] (same polynomial after $t=\ln x$) · [[ODE Eigenvalue Problems]] · SESA2027: [[Characteristic Equation and Eigenvalues]], [[Damping Ratio and Natural Frequency]]

## Sources
- Lecture 1; Lecture Notes §1.1.1
