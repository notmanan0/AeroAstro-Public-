---
title: "Laplace Transform Properties and Proofs"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: concept
stream: "Block 3: Fourier and Laplace Transforms"
aliases: ["First shift theorem", "Second shift theorem", "Laplace derivative rule", "Laplace table"]
tags: [math2048, concept, transforms, exam-prep]
status: complete
parent_lectures: ["[[MATH2048 TR2 - Laplace Transforms - Definition, Properties and Solving IVPs]]", "[[MATH2048 TR3 - Heaviside and Delta Functions and the Second Shift Theorem]]"]
related_concepts: ["[[Laplace Transform]]", "[[Partial Fractions for Inverse Laplace]]", "[[Heaviside Step Function]]", "[[Dirac Delta Function]]"]
sources: ["02 - Sources/Lectures & Problem Sheets/Fourier and Laplace Transform/Lecture11_LaplaceTransform1.pdf", "02 - Sources/Lectures & Problem Sheets/Fourier and Laplace Transform/Lecture12_LaplaceTransform2.pdf", "02 - Sources/Lectures & Problem Sheets/Fourier and Laplace Transform/Lecture13_LaplaceTransform3.pdf", "02 - Sources/Lectures/MATH2048 Lecture 11.txt", "02 - Sources/Lectures/MATH2048 Lecture 12.txt", "02 - Sources/Lectures/MATH2048 Lecture 13.txt"]
---

# Laplace Transform Properties and Proofs

The Laplace transform $\tilde f(s)=\int_0^\infty f(x)e^{-sx}\,dx$ exists for those $s$ at which $f(x)e^{-sx}\to0$ as $x\to\infty$, and every property used in MATH2048 follows from that definition in a line or two. Part (a) of exam question A1 asks for one of these proofs, worth 5 marks: the derivative rule with the condition it needs in 2023/24, and the second shift theorem in 2025/26.

The derivative rule comes from integrating by parts with the exponential differentiated:

$$
\mathcal L[f']=\big[f(x)e^{-sx}\big]_0^\infty+s\int_0^\infty f(x)e^{-sx}\,dx=s\tilde f-f(0),
$$

where the upper limit vanishes because the transform of $f$ exists. That is the condition to state. Applying the rule to $f'$ gives $\mathcal L[f'']=s^2\tilde f-sf(0)-f'(0)$, which is how the initial conditions enter an IVP. The first shift theorem is a one-line rearrangement of the exponent, $\int_0^\infty e^{-ax}f\,e^{-sx}\,dx=\tilde f(s+a)$. The second shift theorem, $\mathcal L[f(x-a)H(x-a)]=e^{-as}\tilde f(s)$ for $a>0$, needs two moves: the Heaviside function raises the lower limit to $a$, and the substitution $\tau=x-a$ brings it back to zero and releases a factor $e^{-sa}$.

Differentiating under the integral sign gives $\mathcal L[xf]=-\frac{d\tilde f}{ds}$, and repeating it from $\mathcal L[1]=\frac1s$ gives $\mathcal L[x^n]=\frac{n!}{s^{n+1}}$. Writing $g=\int_0^xf$, so that $g'=f$ and $g(0)=0$, the derivative rule gives $\mathcal L[g]=\tilde f/s$. A derivative with respect to a parameter, or another coordinate, passes straight through the transform, which is how a Laplace transform in one variable reduces a PDE to an ODE. Linearity holds, but the transform of a product is not the product of transforms: $\mathcal L[1\cdot1]=\frac1s\neq\frac1{s^2}$.

| $f$ | $\tilde f$ | | $f$ | $\tilde f$ |
|---|---|---|---|---|
| $1$ | $1/s$ | | $\sin ax$ | $a/(s^2+a^2)$ |
| $x^n$ | $n!/s^{n+1}$ | | $\cos ax$ | $s/(s^2+a^2)$ |
| $e^{ax}$ | $1/(s-a)$, $s>a$ | | $\sinh ax$ | $a/(s^2-a^2)$ |
| $x^ne^{-ax}$ | $n!/(s+a)^{n+1}$ | | $\cosh ax$ | $s/(s^2-a^2)$ |
| $e^{-cx}\sin bx$ | $b/[(s+c)^2+b^2]$ | | $e^{-cx}\cos bx$ | $(s+c)/[(s+c)^2+b^2]$ |
| $H(x-a)$ | $e^{-as}/s$ | | $\delta(x-a)$ | $e^{-as}$, $a>0$ |

## Related

- Derivations: [[MATH2048 TR2 - Laplace Transforms - Definition, Properties and Solving IVPs]] · [[MATH2048 TR3 - Heaviside and Delta Functions and the Second Shift Theorem#Proof|TR3, proof of the second shift theorem]]
- [[Partial Fractions for Inverse Laplace]] · [[Heaviside Step Function]] · [[Dirac Delta Function]] · [[Fourier Transform]] · SESA2027 [[Laplace Transform]]
