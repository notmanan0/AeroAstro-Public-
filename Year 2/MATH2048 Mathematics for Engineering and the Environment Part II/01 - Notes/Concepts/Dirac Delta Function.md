---
title: "Dirac Delta Function"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: concept
stream: "Block 3: Fourier and Laplace Transforms"
aliases: ["Delta function", "Impulse", "Sifting property", "Impulse response"]
tags: [math2048, concept, transforms]
status: complete
parent_lectures: ["[[MATH2048 TR3 - Heaviside and Delta Functions and the Second Shift Theorem]]"]
related_concepts: ["[[Heaviside Step Function]]", "[[Laplace Transform Properties and Proofs]]"]
sources: ["02 - Sources/Lectures & Problem Sheets/Fourier and Laplace Transform/Lecture13_LaplaceTransform3.pdf"]
---

# Dirac Delta Function

## Definition

> [!note] Definition
> $\delta(x-c)$ is the generalised function defined by the **sifting property**:
>
> $$\int_a^b\delta(x-c)f(x)\,dx=\begin{cases}f(c)&c\in(a,b)\\0&\text{otherwise}\end{cases}$$
>
> Its Laplace transform is $\mathcal L[\delta(x-a)]=e^{-as}$ for $a>0$.

## Explanation
- It is the limit of a rectangle of unit area whose width tends to zero. Physically, it models an instantaneous impulse such as a hammer blow: finite momentum delivered in zero time.
- It is not a true function, so only use it inside integrals and transforms.
- $g(x)\delta(x-a)=g(a)\delta(x-a)$.
- $\delta=H'$.
- **Impulse response**: for $ay''+by'+cy=\delta(x-a)$ with zero initial conditions, $\tilde y=e^{-as}/(as^2+bs+c)$. So $y=H(x-a)\,h(x-a)$, where $h=\mathcal L^{-1}[1/(as^2+bs+c)]$. At $x=a$, $y$ stays continuous but $y'$ jumps by $1/a$ (the reciprocal of the $y''$ coefficient).

## Examples
- $y''+2y'+2y=\delta(x-13)$ gives $y=H(x-13)e^{-(x-13)}\sin(x-13)$ (2025/26 exam).
- $\ddot y+y=\sum\delta(t-n\pi)$ gives $y=\sum H(t-n\pi)\sin(t-n\pi)$ (L13).
- PS5 Q4: the kick $k$ needed for a peak of 2 is $k=2e^{\gamma\tau^*/2}$.

## Related
- [[Heaviside Step Function]] · [[Laplace Transform Properties and Proofs]]

## Sources
- Lecture 13; PS5
