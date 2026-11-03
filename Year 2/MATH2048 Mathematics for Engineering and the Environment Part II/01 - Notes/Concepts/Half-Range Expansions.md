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
sources: ["02 - Sources/Lectures & Problem Sheets/Fourier Series/Lecture6_FourierSeries3.pdf", "02 - Sources/Lectures/MATH2048 Lecture 6.txt"]
---

# Half-Range Expansions

A **half-range expansion** is a Fourier series for a function known only on $0\leq x<L$, made by first inventing its values elsewhere. The odd extension gives a sine series, $\sum b_n\sin\frac{n\pi x}L$ with $b_n=\frac2L\int_0^Lf\sin\frac{n\pi x}L\,dx$; the even extension gives a cosine series, $\frac12a_0+\sum a_n\cos\frac{n\pi x}L$ with $a_n=\frac2L\int_0^Lf\cos\frac{n\pi x}L\,dx$; and the plain periodic extension with period $L$ gives a full series.

All three represent $f$ on $(0,L)$ and differ outside it and at its ends. If $f$ is continuous its even extension is continuous too, so the cosine series converges fastest; the odd extension jumps at $x=L$ unless $f(L)=0$.

In a PDE the boundary conditions choose the extension. A zero value at both ends (Dirichlet) gives sine eigenfunctions, so the initial data are expanded as a sine series, and a zero slope (Neumann) gives a cosine series. The recorded lecture states this pairing the wrong way round (L6, ll. 197–202), as flagged in FS2.

For $f=x$ on $[0,\pi]$ the three expansions are $\frac\pi2-\sum\frac{\sin2nx}n$ (periodic), $\frac\pi2-\frac4\pi\sum_{\text{odd}}\frac{\cos nx}{n^2}$ (even) and $\sum\frac{2(-1)^{n+1}}n\sin nx$ (odd). PS3 Q2's cosine series of $x$ on $[0,1]$ is $\frac12-\frac4{\pi^2}\sum_{\text{odd}}\frac{\cos n\pi x}{n^2}$.

![[m2048_fs_half_range_extensions.png|560]]

## Related

- Derivation: [[MATH2048 FS2 - Even and Odd Functions, Half-Range Series and Convergence]]
- [[Fourier Series]] · [[Fourier's Theorem]]
