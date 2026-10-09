---
title: "Partial Fractions for Inverse Laplace"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: concept
stream: "Block 3: Fourier and Laplace Transforms"
aliases: ["Partial fractions", "Cover-up rule", "Inverse Laplace transform"]
tags: [math2048, concept, transforms]
status: complete
parent_lectures: ["[[MATH2048 TR2 - Laplace Transforms - Definition, Properties and Solving IVPs]]"]
related_concepts: ["[[Laplace Transform Properties and Proofs]]"]
sources: ["02 - Sources/Lectures & Problem Sheets/Fourier and Laplace Transform/Lecture12_LaplaceTransform2.pdf", "02 - Sources/Lectures & Problem Sheets/Fourier and Laplace Transform/Lecture13_LaplaceTransform3.pdf"]
---

# Partial Fractions for Inverse Laplace

## Definition

> [!note] Definition
> MATH2048 has no inversion formula: $\mathcal L^{-1}$ is done by splitting the rational function $\tilde y(s)$ into terms that appear in the table.

## Explanation
| Factor in the denominator | Terms to write | Inverts to |
|---|---|---|
| $s-r$ | $\frac{A}{s-r}$ | $Ae^{rx}$ |
| $(s-r)^n$ | $\sum_{k=1}^{n}\frac{A_k}{(s-r)^k}$ | $A_k\frac{x^{k-1}}{(k-1)!}e^{rx}$ |
| $(s+c)^2+b^2$ | $\frac{B(s+c)+Cb}{(s+c)^2+b^2}$ | $e^{-cx}(B\cos bx+C\sin bx)$ |

**Methods for finding the coefficients**:
1. **Cover-up** (simple roots): the coefficient of $\frac1{s-r}$ equals the rest of the expression evaluated at $s=r$.
2. **Substitute convenient values of $s$** after multiplying through.
3. **Match powers of $s$**.

**Degree check**: if the numerator's degree is at least the denominator's, divide first.

**Exponentials**: keep each $e^{-as}$ factor aside and decompose only the rational part.

> [!example] Lecture 13 homework
> $\frac1{s(s^2+1)}=\frac As+\frac{Bs+C}{s^2+1}$ gives $1=A(s^2+1)+(Bs+C)s$.
> - Constant term: $A=1$.
> - $s$ term: $C=0$.
> - $s^2$ term: $A+B=0$, so $B=-1$.
>
> So $\frac1{s(s^2+1)}=\frac1s-\frac{s}{s^2+1}$, which inverts to $1-\cos x$.

## Examples
- $\frac{1+s+s^2}{s^2(s+1)^2(s+2)}=-\frac{3}{4s}+\frac{1}{2s^2}+\frac{1}{(s+1)^2}+\frac{3}{4(s+2)}$ (L12, verified with `apart`).
- $\frac1{(s^2+1)(s^2+4)}=\frac13\Big[\frac1{s^2+1}-\frac1{s^2+4}\Big]$ (PS5 Q3e). The trick is to treat $s^2$ as the variable.

## Related
- [[Laplace Transform Properties and Proofs]] · [[MATH2048 Problem Sheet 4-5 Solutions - Fourier and Laplace Transforms]]

## Sources
- Lectures 12–13
