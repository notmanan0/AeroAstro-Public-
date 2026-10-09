---
title: "Orthogonality of Trigonometric Functions"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: concept
stream: "Block 2: Fourier Series"
aliases: ["Orthogonality relations", "Kronecker delta", "Inner product of functions"]
tags: [math2048, concept, fourier-series]
status: complete
parent_lectures: ["[[MATH2048 FS1 - Fourier Series, Orthogonality and the Euler Formulae]]"]
related_concepts: ["[[Fourier Series]]", "[[ODE Eigenvalue Problems]]"]
sources: ["02 - Sources/Lectures & Problem Sheets/Fourier Series/Lecture4_FourierSeries1.pdf", "02 - Sources/Lectures & Problem Sheets/Problem Sheets/Problem Sheet 2.pdf"]
---

# Orthogonality of Trigonometric Functions

## Definition

> [!note] Definition
> For integers $m,n\geq1$ and $k=\pi/\ell$:
> $$\int_{-\ell}^{\ell}\cos mkx\cos nkx\,dx=\ell\delta_{mn},\quad\int_{-\ell}^{\ell}\sin mkx\sin nkx\,dx=\ell\delta_{mn},\quad\int_{-\ell}^{\ell}\cos mkx\sin nkx\,dx=0 .$$
> The exception is $\int_{-\ell}^{\ell}1\,dx=2\ell$.

## Explanation
**The proof uses four facts**:
1. The product-to-sum identities: $2\cos A\cos B=\cos(A-B)+\cos(A+B)$, $2\sin A\sin B=\cos(A-B)-\cos(A+B)$ and $2\sin A\cos B=\sin(A-B)+\sin(A+B)$.
2. $\int_{-\ell}^{\ell}\cos pkx\,dx=0$ for any integer $p\neq0$.
3. When $m=n$: $\cos^2A=\frac12(1+\cos2A)$ and $\sin^2A=\frac12(1-\cos2A)$.
4. Mixed products are odd × even, which is odd, so they integrate to zero.

**Interpretation**: with the inner product $\langle f,g\rangle=\int fg$, the functions $\{1,\cos nkx,\sin nkx\}$ form an orthogonal basis. The Fourier coefficients are the projections of $f$ onto this basis.

**Why it holds**: these functions are the eigenfunctions of $y''+\lambda y=0$ with periodic BCs. Eigenfunctions with distinct eigenvalues are orthogonal ([[ODE Eigenvalue Problems]]).

**Complex form**: $\int_{-\ell}^{\ell}e^{jmkx}e^{-jnkx}dx=2\ell\delta_{mn}$.

**Half-range form**: $\int_0^L\sin\frac{m\pi x}L\sin\frac{n\pi x}Ldx=\frac L2\delta_{mn}$. This is the one used to fit initial conditions in PDEs.

## Related
- [[Fourier Series]] · [[ODE Eigenvalue Problems]]

## Sources
- Lectures 4–5; PS2 (FS) Q1
