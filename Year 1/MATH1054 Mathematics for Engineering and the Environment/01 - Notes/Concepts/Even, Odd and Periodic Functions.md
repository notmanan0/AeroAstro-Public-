---
title: "Even, Odd and Periodic Functions"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 1: Calculus"
aliases: ["Even function", "Odd function", "Periodic function", "Symmetry"]
tags: [math1054, concept, functions]
status: complete
parent_lectures: ["[[MATH1054 M07 - Functions]]"]
related_concepts: ["[[Inverse Functions]]", "[[Half-Range Expansions]]", "[[Fourier Series]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §2.2.6", "MATH1054 Module Booklet, Module 7"]
---

# Even, Odd and Periodic Functions

A function is **even** if $f(-x)=f(x)$, so its graph is symmetric about the $y$-axis, and **odd** if $f(-x)=-f(x)$, so its graph is unchanged by a half-turn about the origin. It is **periodic** with period $P$ if $f(x+P)=f(x)$ for all $x$.

Even examples are $x^{2n}$, $\cos x$, $\cosh x$ and $|x|$; odd examples are $x^{2n+1}$, $\sin x$, $\tan x$, $\sinh x$ and $\tanh x$. Setting $x=0$ in the odd condition gives $f(0)=-f(0)$, so an odd function has $f(0)=0$ or is undefined there. Products follow the sign rule: even × even and odd × odd are even, even × odd is odd, so $x\sin x$ is even and $x^2\sin x$ is odd. Any function on a symmetric domain splits into an even part $\frac12[f(x)+f(-x)]$ and an odd part $\frac12[f(x)-f(-x)]$; for $e^x$ these are $\cosh x$ and $\sinh x$.

Symmetry halves integrals. Substituting $u=-x$ in $\int_{-a}^0f\,\mathrm dx$ turns it into $\int_0^af(-u)\,\mathrm du$, which is $-\int_0^af$ for odd $f$ and $+\int_0^af$ for even $f$. Hence

$$
\int_{-a}^{a}f(x)\,\mathrm dx=\begin{cases}0,&f\text{ odd},\\[2pt]2\displaystyle\int_0^af(x)\,\mathrm dx,&f\text{ even}.\end{cases}
$$

For instance $\int_{-1}^1x^3\cos x\,\mathrm dx=0$ with no integration, and $\int_{-2}^2x^2\,\mathrm dx=2\cdot\frac83=\frac{16}3$.

A periodic function is a row of identical strips of width $P$; its frequency is $\nu=1/P$ and its circular frequency $\omega=2\pi/P$, so $\sin3x$ has period $\frac{2\pi}3$. A function known only on $[0,L]$ can be extended in several ways: repeated with period $L$, reflected to an even function of period $2L$, or rotated to an odd function of period $2L$ (Example 2.12, below for a triangle on $[0,1]$). The even and odd extensions are the half-range cosine and sine series of [[Half-Range Expansions]].

![[m1054_periodic_extensions.png|900]]

Composites inherit symmetry and period from their parts: $\sin^{-1}(\sin x)$ is odd with period $2\pi$ and $\cos^{-1}(\cos x)$ is even with period $2\pi$ ([[Inverse Trigonometric Functions]]). $\frac{x^2+1}{\sqrt{x^2-1}}$ is even on its domain $|x|>1$ because only $x^2$ appears (Specimen Test 7, Q1).

The common trap is calling a function odd because it fails the even test. Most functions are neither: $e^x$ and a line $mx+c$ with $c\neq0$ fail both tests, and any function whose domain is not symmetric about $0$ is neither by definition.

## Related

- Topics: [[MATH1054 M07 - Functions]] · [[MATH2048 FS2 - Even and Odd Functions, Half-Range Series and Convergence]]
- Concepts: [[Inverse Functions]] · [[Hyperbolic Functions]] · [[Half-Range Expansions]] · [[Fourier Series]]
- Sources: James, *Modern Engineering Mathematics* (6th ed.) §2.2.6; MATH1054 Module Booklet, Module 7
