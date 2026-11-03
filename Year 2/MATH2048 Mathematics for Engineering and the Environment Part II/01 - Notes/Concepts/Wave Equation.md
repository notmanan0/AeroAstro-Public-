---
title: "Wave Equation"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: concept
stream: "Block 4: Partial Differential Equations"
aliases: ["1D wave equation", "Vibrating string", "D'Alembert", "Damped wave equation"]
tags: [math2048, concept, pdes]
status: complete
parent_lectures: ["[[MATH2048 PDE1 - Classification of PDEs and the Wave Equation]]", "[[MATH2048 PDE2 - Separation of Variables for the Wave Equation]]"]
related_concepts: ["[[Separation of Variables]]", "[[PDE Classification]]", "[[Natural Frequencies and Mode Shapes]]"]
sources: ["02 - Sources/Lectures & Problem Sheets/PDEs/Lecture14_Hyperbolic1.pdf", "02 - Sources/Lectures & Problem Sheets/PDEs/Lecture16_Hyperbolic3.pdf", "02 - Sources/Lectures/MATH2048 Lecture 14.txt", "02 - Sources/Lectures/MATH2048 Lecture 15.txt", "02 - Sources/Lectures/MATH2048 Lecture 16.txt"]
---

# Wave Equation

The one-dimensional **wave equation** $y_{tt}=c^2y_{xx}$ is the prototype hyperbolic PDE. For a string of tension $T$ and mass per unit length $\rho$, Newton's second law on a short piece gives $c=\sqrt{T/\rho}$, the speed at which waves travel along it.

Dimensionally $c$ must be a speed, and a pulse splits into two halves moving left and right at that speed. On a finite string, separation of variables gives standing waves. With fixed ends the modes are $\sin\frac{n\pi x}L$, each oscillating at $\frac{n\pi c}L$, so the frequencies are integer multiples of a fundamental; with free (Neumann) ends they are $\cos\frac{n\pi x}L$, plus a constant mode whose time part $Gt+H$ lets the whole string drift. Each standing mode is two equal travelling waves, since $\sin kx\cos kct=\frac12[\sin k(x-ct)+\sin k(x+ct)]$.

The equation needs two initial conditions, the displacement and the velocity, which fix the cosine and sine coefficients of each mode through half-range Fourier series. Nothing damps the modes, so the motion goes on for ever. Adding damping, $u_{tt}+2\gamma u_t=u_{xx}$ (the 2025/26 exam), changes only the time equation, and each mode then decays as $e^{-\gamma t}$ while oscillating at $\sqrt{n^2-\gamma^2}$.

## Related

- [[MATH2048 PDE1 - Classification of PDEs and the Wave Equation]] · [[MATH2048 PDE2 - Separation of Variables for the Wave Equation]]
- [[Separation of Variables]] · [[PDE Classification]] · [[Half-Range Expansions]]
