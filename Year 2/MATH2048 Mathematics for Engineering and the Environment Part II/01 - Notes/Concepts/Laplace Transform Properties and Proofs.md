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
sources: ["02 - Sources/Lectures & Problem Sheets/Fourier and Laplace Transform/Lecture11_LaplaceTransform1.pdf", "02 - Sources/Lectures & Problem Sheets/Fourier and Laplace Transform/Lecture12_LaplaceTransform2.pdf", "02 - Sources/Lectures & Problem Sheets/Fourier and Laplace Transform/Lecture13_LaplaceTransform3.pdf"]
---

# Laplace Transform Properties and Proofs

> [!important] Exam pattern
> Part (a) of A1 is always a proof, worth 5 marks:
> - **2023/24**: the derivative rule, including stating the condition it needs.
> - **2025/26**: the second shift theorem.
>
> Each proof below is written the way it should look on the page.

## Definition

$$\tilde f(s)=\mathcal L[f(x)]=\int_0^\infty f(x)e^{-sx}dx .$$

If this exists, then $\lim_{x\to\infty}f(x)e^{-sx}=0$.

## Proofs

**1. Derivative.** $\mathcal L[f']=s\tilde f(s)-f(0)$, provided $f(x)e^{-sx}\to0$ as $x\to\infty$.
Integrate by parts with $u=e^{-sx}$ and $dv=f'dx$:

$$\mathcal L[f']=\big[f(x)e^{-sx}\big]_0^\infty-\int_0^\infty f(x)(-s)e^{-sx}dx=\Big(\lim_{x\to\infty}fe^{-sx}-f(0)\Big)+s\tilde f=s\tilde f-f(0).$$

Applying this rule to $f'$ gives $\mathcal L[f'']=s^2\tilde f-sf(0)-f'(0)$.

**2. First shift theorem.** $\mathcal L[e^{-ax}f]=\tilde f(s+a)$.

$$\int_0^\infty e^{-ax}fe^{-sx}dx=\int_0^\infty fe^{-(s+a)x}dx=\tilde f(s+a).$$

**3. Second shift theorem.** $\mathcal L[H(x-a)f(x-a)]=e^{-as}\tilde f(s)$ for $a\geq0$.
Because $H(x-a)=0$ for $x<a$, the integral starts at $x=a$. Then substitute $\tau=x-a$:

$$\int_a^\infty f(x-a)e^{-sx}dx=\int_0^\infty f(\tau)e^{-s(\tau+a)}d\tau=e^{-as}\tilde f(s).$$

Alternative form: $\mathcal L[f(x)H(x-a)]=e^{-as}\mathcal L[f(x+a)]$.

**4. Multiplication by $x$.** $\mathcal L[xf]=-\tilde f'(s)$.
Differentiate under the integral sign:

$$\frac{d}{ds}\int_0^\infty fe^{-sx}dx=-\int_0^\infty xfe^{-sx}dx .$$

Repeating this gives $\mathcal L[x^n]=n!/s^{n+1}$.

**5. Integral.** $\mathcal L\big[\int_0^xf\big]=\tilde f/s$.
Let $g=\int_0^xf$. Then $g'=f$ and $g(0)=0$, so the derivative rule gives $\tilde f=s\tilde g$.

**6. Parameter derivative.** $\mathcal L[\partial_af]=\partial_a\tilde f$, because the integral is over $x$, not $a$.

**7. Standard transforms.**
- $\mathcal L[H(x-a)]=\dfrac{e^{-as}}{s}$
- $\mathcal L[\delta(x-a)]=e^{-as}$ for $a>0$

## Table
| $f$ | $\tilde f$ | | $f$ | $\tilde f$ |
|---|---|---|---|---|
| $1$ | $1/s$ | | $\sin ax$ | $a/(s^2+a^2)$ |
| $x^n$ | $n!/s^{n+1}$ | | $\cos ax$ | $s/(s^2+a^2)$ |
| $e^{ax}$ | $1/(s-a)$ | | $\sinh ax$ | $a/(s^2-a^2)$ |
| $x^ne^{-ax}$ | $n!/(s+a)^{n+1}$ | | $\cosh ax$ | $s/(s^2-a^2)$ |
| $e^{-cx}\sin bx$ | $b/[(s+c)^2+b^2]$ | | $e^{-cx}\cos bx$ | $(s+c)/[(s+c)^2+b^2]$ |
| $x\cos ax$ | $(s^2-a^2)/(s^2+a^2)^2$ | | $x\sin ax$ | $2as/(s^2+a^2)^2$ |

## Related
- [[Laplace Transform]] · [[Partial Fractions for Inverse Laplace]] · [[Heaviside Step Function]] · [[Dirac Delta Function]]

## Sources
- Lectures 11–13; Laplace Appendix
