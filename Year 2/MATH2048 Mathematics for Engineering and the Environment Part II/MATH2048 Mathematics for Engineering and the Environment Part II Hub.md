---
title: "MATH2048 Mathematics for Engineering and the Environment Part II Hub"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: hub
tags: [math2048, hub, moc]
status: complete
coverage: "All 30 lectures of the 2024-25 series (Ian Hawke, 30 Sep - 9 Dec 2024), rebuilt from the transcripts in October 2026, plus the PDE recap lecture of 13 Nov 2024."
---

# MATH2048 Mathematics for Engineering and the Environment Part II Hub

> [!abstract] Module at a glance
> This is the maths behind SESA2027 and SESA2029, examined as maths: derivations, proofs and full working. Its five blocks build on one another. ODEs give the solution toolkit; Fourier series expand a function in eigenfunctions; Fourier and Laplace transforms turn ODEs into algebra; PDEs (wave, heat, Laplace) combine all three, since separation of variables is an eigenvalue problem, then a time ODE, then a Fourier series fitted to the initial data; and vector calculus covers grad, div, curl, line, surface and volume integrals and the Gauss and Stokes theorems.
>
> Quick reference: [[MATH2048 Formula Sheet]] · Exam practice: [[MATH2048 Past Paper Solutions]]

Every topic note was rebuilt in October 2026 from the recordings of the 2024-25 lectures, given by Ian Hawke, and is at `status: lectured`. Each one follows what was said in the room, with full derivations of anything skipped, worked examples checked in SymPy, the relevant past-paper questions worked through, and a table of transcript slips with line references. Material from the printed lecture notes that wasn't lectured, such as d'Alembert's solution and the vector potential, is mentioned where relevant but not developed. The transcripts are listed in the [[MATH2048 Transcript Index]].

> [!info] Exam format (2023/24–2025/26 papers, all with official solutions)
> 100 minutes, open book, with the official formula sheet FS/MATH2048 on Blackboard. You answer A1, A2, B1 and B2; Section C is statistics for Civil Engineering only.
>
> | Question | Marks | Content |
> |---|---|---|
> | A1 | 20 | Laplace: prove a property (derivative rule or second shift theorem), then solve an IVP with $H$ or $\delta$ |
> | A2 | 25 | PDE by separation of variables: eigenproblem in three cases, $T_n$, fit the initial conditions |
> | B1 | 15 | Fields: grad, div, curl, conservative test, potential, line integral |
> | B2 | 20 | Surfaces and volumes: $d\mathbf S$, flux, Gauss's theorem, the spherical Jacobian |
>
> Fourier series and transforms are never examined on their own; they appear inside A2, in fitting the initial data.

## Topic map

### Block 1: Ordinary differential equations (L1–3)
1. [[MATH2048 ODE1 - Second-Order Linear ODEs with Constant Coefficients]]: the auxiliary equation, three root cases, the damped oscillator
2. [[MATH2048 ODE2 - Euler Equations and Inhomogeneous ODEs]]: $y=x^n$, $t=\ln x$, complementary function plus particular integral, resonance
3. [[MATH2048 ODE3 - Boundary Value and Eigenvalue Problems]]: unique, no or infinitely many solutions; the three-case method

### Block 2: Fourier series (L4–8)
4. [[MATH2048 FS1 - Fourier Series, Orthogonality and the Euler Formulae]]: orthogonality proofs, Euler formulae, sawtooth and tent, summing series
5. [[MATH2048 FS2 - Even and Odd Functions, Half-Range Series and Convergence]]: even and odd, three extensions, Dirichlet conditions, jumps
6. [[MATH2048 FS3 - Calculus with Fourier Series and Complex Fourier Series]]: when term-by-term calculus is allowed; $c_n$

### Block 3: Fourier and Laplace transforms (L9–13)
7. [[MATH2048 TR1 - Fourier Transforms]]: the limit of the complex series, properties with proofs, the response function
8. [[MATH2048 TR2 - Laplace Transforms - Definition, Properties and Solving IVPs]]: the table from the definition, shift and derivative rules, partial fractions
9. [[MATH2048 TR3 - Heaviside and Delta Functions and the Second Shift Theorem]]: $H$, $\delta$, the second shift theorem, a hammer-struck pendulum

### Block 4: Partial differential equations (L14–20)
10. [[MATH2048 PDE1 - Classification of PDEs and the Wave Equation]]: the three types and their data, $b^2-ac$, the Tricomi equation, the string derivation
11. [[MATH2048 PDE2 - Separation of Variables for the Wave Equation]]: the six steps, fixed and free ends, standing as travelling waves
12. [[MATH2048 PDE3 - The Heat Equation]]: the random-walk derivation, exponential decay, the insulated rod
13. [[MATH2048 PDE4 - Inhomogeneous PDEs and Inhomogeneous Boundary Conditions]]: eigenfunction expansion, subtracting a boundary function
14. [[MATH2048 PDE5 - Laplace's Equation]]: the static limit, $\sinh$ in $y$, the maximum principle

### Block 5: Vector calculus (L21–30)
15. [[MATH2048 VC1 - Scalar and Vector Fields, Gradient and Directional Derivatives]]: fields, curves, steepest ascent, normals
16. [[MATH2048 VC2 - Divergence, Curl, Laplacian and Vector Identities]]: div and curl built from the gradient, vorticity, the two zero identities
17. [[MATH2048 VC3 - Line Integrals and Conservative Fields]]: the work integral, path dependence, $\mathbf F=-\nabla\phi$, finding $\phi$
18. [[MATH2048 VC4 - Surfaces, Surface Area and Flux Integrals]]: $\mathbf r_s\times\mathbf r_t$, $dA$, flux, the helicoid
19. [[MATH2048 VC5 - Volume Integrals, the Divergence Theorem and Stokes' Theorem]]: Jacobians, Gauss, Stokes, weak and strong forms

## Concept notes

| ODEs | Fourier series | Transforms | PDEs | Vector calculus |
|---|---|---|---|---|
| [[Auxiliary Equation]] | [[Fourier Series]] | [[Fourier Transform]] | [[PDE Classification]] | [[Gradient and Directional Derivative]] |
| [[Euler-Cauchy Equation]] | [[Orthogonality of Trigonometric Functions]] | [[Laplace Transform Properties and Proofs]] | [[Separation of Variables]] | [[Divergence, Curl and the Laplacian]] |
| [[Method of Undetermined Coefficients]] | [[Half-Range Expansions]] | [[Partial Fractions for Inverse Laplace]] | [[Wave Equation]] | [[Line Integrals]] |
| [[Resonance]] | [[Fourier's Theorem]] | [[Heaviside Step Function]] | [[Heat Equation]] | [[Conservative Vector Fields]] |
| [[Boundary Value Problems]] | [[Complex Fourier Series]] | [[Dirac Delta Function]] | [[Laplace's Equation]] | [[Flux Integrals]] |
| [[ODE Eigenvalue Problems]] | | [[Laplace Transform]] (SESA2027) | [[Eigenfunction Expansion Method]] | [[Jacobian and Volume Elements]] |
| | | | | [[Divergence Theorem]] |
| | | | | [[Stokes' Theorem]] |

## Problem sheets (full worked solutions)

| Solutions note | Covers | Notes |
|---|---|---|
| [[MATH2048 Problem Sheets 1-2 Solutions - ODEs]] | PS1, PS2 Q1–3 | PS2 Q2(c) fails because $\lambda=\frac14$ is an eigenvalue of Q3(b) |
| [[MATH2048 Problem Sheets 2-4 Solutions - Fourier Series]] | PS2 Fourier page, PS3, PS4 Q1–2 | $\sum\frac{(-1)^n}{1+n^2}=\frac12(1+\pi/\sinh\pi)$, checked numerically |
| [[MATH2048 Problem Sheet 4-5 Solutions - Fourier and Laplace Transforms]] | PS4 FT page, PS5 | Q4 closed form $k_1=2e^{\gamma\tau^*/2}$ |
| [[MATH2048 Problem Sheets 6-7 Solutions - PDEs]] | PS6, PS7 | Every answer printed on the sheets is reproduced |
| [[MATH2048 Problem Sheets 8-11 Solutions - Vector Calculus]] | PS8–PS11 | All integrals checked by explicit parametrisation |
| [[MATH2048 Past Paper Solutions]] | 2023/24, 2024/25, 2025/26 (A and B) | All agree with the official solutions |

> [!warning] Errors in the sources
> The lectures' own slips are tabulated at the end of each topic note. The most consequential: Lecture 6 pairs Dirichlet and Neumann conditions with the wrong extensions ([[MATH2048 FS2 - Even and Odd Functions, Half-Range Series and Convergence|FS2]]); Lecture 22 gives $-\frac{323}7\approx-6.6$ when it is $-46.1$ ([[MATH2048 VC3 - Line Integrals and Conservative Fields|VC3]]); Lecture 30's "paraboloid" parametrisation is a cone, which still gives $18\pi$ by Stokes ([[MATH2048 VC5 - Volume Integrals, the Divergence Theorem and Stokes' Theorem|VC5]]). In the printed lecture notes, line-integral Example 1b is printed as $6$ (correct: $-\frac{79}2$), Example 1a loses its minus sign ($-\frac{323}7$), the paraboloid Stokes example gives $18$ for $18\pi$, and in §4.7.3 the spherical-wave denominator should be $as+c$, not $a^2s+c$. The 2024/25 published solution to A2 writes $\dot T$ and $\partial u/\partial x$ where it means $\ddot T$ and $\partial u/\partial t$.

## Exam strategy

For A1, know the derivative-rule and second-shift proofs with their conditions, and practise the full cycle: rewrite each source as $f(x-a)H(x-a)$, transform, partial fractions, invert with both shift theorems, naming each theorem as you use it. For A2, write the separated ODEs and justify why both sides are constant, do all three cases of $\lambda$ including zero, keep the course's sign convention $X''-\lambda X=0$ so that $\lambda_n=-n^2$, and fit the initial data by inspection with trig identities before reaching for Euler formulae. For B1, compute the curl first: if it is zero, find $\phi$ and use the endpoints; otherwise parametrise and integrate. For B2, expect Gauss plus spherical coordinates, derive the Jacobian in full, and use symmetry and shifts of origin to avoid repeating integrals.

## All notes
```dataview
TABLE type, status, file.mtime AS "Updated"
FROM "Year 2/MATH2048 Mathematics for Engineering and the Environment Part II"
WHERE type
SORT type ASC, file.name ASC
```

## Builds on / feeds into
- Into [[SESA2027 Aerospace Mechanics & Control Hub]]: ODEs, the characteristic equation ([[Damping Ratio and Natural Frequency]]), Laplace transforms ([[Laplace Transform]]), the frequency response ([[Frequency Response Function]]).
- Into [[SESA2029 Digital Aerospace Methods Hub]]: the heat equation and the Fourier number ([[CFL and Fourier Numbers]]), mode shapes ([[Natural Frequencies and Mode Shapes]]).
- Into [[SESA2022 Aerodynamics Hub]]: Laplace's equation in potential flow ([[Streamfunction and Velocity Potential]]), circulation via Stokes ([[Kelvin's Circulation Theorem]], [[Kutta-Joukowski Theorem]]), vorticity as the curl.
