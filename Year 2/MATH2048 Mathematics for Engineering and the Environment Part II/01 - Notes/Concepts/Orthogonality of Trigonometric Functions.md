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
sources: ["02 - Sources/Lectures & Problem Sheets/Fourier Series/Lecture4_FourierSeries1.pdf", "02 - Sources/Lectures & Problem Sheets/Problem Sheets/Problem Sheet 2.pdf", "02 - Sources/Lectures/MATH2048 Lecture 4.txt"]
---

# Orthogonality of Trigonometric Functions

Sines and cosines of different integer frequencies are **orthogonal** over a period: with $k=\pi/\ell$ and integers $m,n\geq1$,

$$
\int_{-\ell}^{\ell}\cos mkx\cos nkx\,dx=\ell\delta_{mn},\quad\int_{-\ell}^{\ell}\sin mkx\sin nkx\,dx=\ell\delta_{mn},\quad\int_{-\ell}^{\ell}\cos mkx\sin nkx\,dx=0,
$$

with $\int_{-\ell}^{\ell}1\,dx=2\ell$ for the constant.

The proof uses the product-to-sum identities, such as $2\sin A\sin B=\cos(A-B)-\cos(A+B)$, which turn each product into single cosines of $(m\pm n)kx$; these integrate to sines of integer multiples of $\pi$, which vanish. The case $m=n$ has to be done separately because that step divides by $m-n$, using $\sin^2A=\frac12(1-\cos2A)$. Mixed sine–cosine products are odd and integrate to zero over the symmetric interval.

In the lecturer's analogy, the functions $1$, $\cos nkx$ and $\sin nkx$ behave like an orthogonal basis of vectors, with the integral $\int fg\,dx$ playing the part of the dot product, and the Fourier coefficients are the projections of $f$ onto that basis. They are orthogonal because they are the eigenfunctions of $y''+\lambda y=0$ with periodic conditions, and eigenfunctions with different eigenvalues are always orthogonal ([[ODE Eigenvalue Problems]]). Two variants come up constantly: the complex form $\int_{-\ell}^{\ell}e^{jmkx}e^{-jnkx}dx=2\ell\delta_{mn}$, and the half-range form $\int_0^L\sin\frac{m\pi x}L\sin\frac{n\pi x}L\,dx=\frac L2\delta_{mn}$, which is the one used to fit initial conditions in PDEs.

## Related

- Derivation: [[MATH2048 FS1 - Fourier Series, Orthogonality and the Euler Formulae#2. Orthogonality (L4)|FS1 §2]]
- [[Fourier Series]] · [[ODE Eigenvalue Problems]]
