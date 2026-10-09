---
title: "Half-Range Expansions"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: concept
stream: "Block 2: Fourier Series"
aliases: ["Half range series", "Fourier sine series", "Fourier cosine series", "Even extension", "Odd extension"]
tags: [math2048, concept, fourier-series, pdes]
status: complete
parent_lectures: ["[[MATH2048 FS2 - Even and Odd Functions, Half-Range Series and Convergence]]"]
related_concepts: ["[[Fourier Series]]", "[[Fourier's Theorem]]"]
sources: ["02 - Sources/Lectures & Problem Sheets/Fourier Series/Lecture6_FourierSeries3.pdf"]
---

# Half-Range Expansions

## Definition

> [!note] Definition
> A function known only on $0\leq x<L$ can be expanded in three ways:
> - **Sine series** (odd extension, period $2L$): $\sum b_n\sin\frac{n\pi x}L$ with $b_n=\frac2L\int_0^Lf\sin\frac{n\pi x}L\,dx$.
> - **Cosine series** (even extension, period $2L$): $\frac12a_0+\sum a_n\cos\frac{n\pi x}L$ with $a_n=\frac2L\int_0^Lf\cos\frac{n\pi x}L\,dx$.
> - **Full series** (periodic extension, period $L$).

## Explanation
- All three represent $f$ on $(0,L)$. They differ outside that interval and at its endpoints.
- If $f$ is continuous, its even extension is continuous too, so the cosine series converges fastest. The odd extension jumps at $x=L$ unless $f(L)=0$.
- **In PDEs**: Dirichlet boundary conditions ($u=0$ at the ends) give sine eigenfunctions, so the initial data are expanded as a **sine** series. Neumann conditions ($u_x=0$) give a **cosine** series.

## Examples
- $f=x$ on $[0,\pi]$:
  - Periodic extension: $\frac\pi2-\sum\frac{\sin2nx}n$
  - Even extension: $\frac\pi2-\frac4\pi\sum_{\text{odd}}\frac{\cos nx}{n^2}$
  - Odd extension: $\sum\frac{2(-1)^{n+1}}n\sin nx$
- PS3 Q2: the cosine series of $x$ on $[0,1]$ is $\frac12-\frac4{\pi^2}\sum_{\text{odd}}\frac{\cos n\pi x}{n^2}$.

![[m2048_fs_half_range_extensions.png|560]]

## Related
- [[Fourier Series]] · [[Fourier's Theorem]]

## Sources
- Lecture 6
