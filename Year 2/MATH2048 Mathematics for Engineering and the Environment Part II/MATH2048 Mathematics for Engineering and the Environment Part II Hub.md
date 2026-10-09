---
title: "MATH2048 Mathematics for Engineering and the Environment Part II Hub"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: hub
tags: [math2048, hub, moc]
status: complete
---

# MATH2048 Mathematics for Engineering and the Environment Part II Hub

> [!abstract] Module at a glance
> This is the maths *behind* SESA2027 and SESA2029. It is examined *as maths*: derivations, proofs and full working.
>
> The five blocks build on one another:
> 1. **ODEs**: the solution toolkit.
> 2. **Fourier series**: expanding a function in eigenfunctions.
> 3. **Fourier and Laplace transforms**: solving ODEs with algebra.
> 4. **PDEs** (wave, heat, Laplace) by separation of variables. This is where Blocks 1–3 combine: an eigenproblem, then a time ODE, then a Fourier series fit to the initial data.
> 5. **Vector calculus**: grad, div, curl, line, surface and volume integrals, and the Gauss and Stokes theorems.
>
> Quick reference: [[MATH2048 Formula Sheet]] · Exam practice: [[MATH2048 Past Paper Solutions]]

> [!info] Exam format (2023/24–2025/26 papers, all with official solutions)
> 100 minutes, open book, with the official formula sheet FS/MATH2048 on Blackboard. You answer A1, A2, B1 and B2.
>
> | Question | Marks | Content |
> |---|---|---|
> | **A1** | 20 | Laplace: prove a property (derivative rule / $\delta$ / second shift theorem), then solve an IVP with $H$ or $\delta$ |
> | **A2** | 25 | PDE by separation of variables: eigenproblem (three cases), $T_n$, fit initial conditions by orthogonality |
> | **B1** | 15 | Fields: grad / div / curl, conservative test, potential, line integral |
> | **B2** | 20 | Surfaces and volumes: $d\mathbf S$, flux, Gauss's theorem, Jacobian for spherical coordinates |
>
> Section C is statistics for Civil Engineering only, so it is **not for us**. Fourier series and transforms are never examined on their own; they appear inside A2 (and are needed for its initial-condition fit).

## Topic map

### Block 1: Ordinary Differential Equations (L1–3)
1. [[MATH2048 ODE1 - Second-Order Linear ODEs with Constant Coefficients]]: the auxiliary equation, three root cases, damped oscillator
2. [[MATH2048 ODE2 - Euler Equations and Inhomogeneous ODEs]]: $y=x^n$, $t=\ln x$, CF + PI, the clash rule, resonance
3. [[MATH2048 ODE3 - Boundary Value and Eigenvalue Problems]]: unique / no / family of solutions, the three-case method, standard eigenproblem table

### Block 2: Fourier Series (L4–8)
4. [[MATH2048 FS1 - Fourier Series, Orthogonality and the Euler Formulae]]: orthogonality proofs, Euler formulae, sawtooth and tent, summing series
5. [[MATH2048 FS2 - Even and Odd Functions, Half-Range Series and Convergence]]: even/odd, three extensions, Dirichlet conditions, jumps
6. [[MATH2048 FS3 - Calculus with Fourier Series and Complex Fourier Series]]: when you may differentiate or integrate term by term; $c_n$

### Block 3: Fourier and Laplace Transforms (L9–13)
7. [[MATH2048 TR1 - Fourier Transforms]]: the $T\to\infty$ limit, properties with proofs, response function $G(\omega)$
8. [[MATH2048 TR2 - Laplace Transforms - Definition, Properties and Solving IVPs]]: the table from the definition, proofs, partial fractions
9. [[MATH2048 TR3 - Heaviside and Delta Functions and the Second Shift Theorem]]: $H$, $\delta$, the second shift theorem, impulse response

### Block 4: Partial Differential Equations (L14–20)
10. [[MATH2048 PDE1 - Classification of PDEs and the Wave Equation]]: $b^2-ac$, string derivation, d'Alembert
11. [[MATH2048 PDE2 - Separation of Variables for the Wave Equation]]: the six steps, Dirichlet and Neumann examples
12. [[MATH2048 PDE3 - The Heat Equation]]: random-walk derivation, exponential decay, insulated rod
13. [[MATH2048 PDE4 - Inhomogeneous PDEs and Inhomogeneous Boundary Conditions]]: eigenfunction expansion, subtracting $y_P$
14. [[MATH2048 PDE5 - Laplace's Equation]]: maximum principle, $\sinh$ in $y$, superposition of sides

### Block 5: Vector Calculus (L21–30)
15. [[MATH2048 VC1 - Scalar and Vector Fields, Gradient and Directional Derivatives]]: steepest ascent, normals, tangent planes
16. [[MATH2048 VC2 - Divergence, Curl, Laplacian and Vector Identities]]: physical meaning, the two zero theorems, identities
17. [[MATH2048 VC3 - Line Integrals and Conservative Fields]]: the recipe, path (in)dependence, four equivalences, finding $\phi$
18. [[MATH2048 VC4 - Surfaces, Surface Area and Flux Integrals]]: $\mathbf r_s\times\mathbf r_t$, $dA$, flux, orientation
19. [[MATH2048 VC5 - Volume Integrals, the Divergence Theorem and Stokes' Theorem]]: Jacobians, Gauss, Stokes, Green

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
| [[MATH2048 Problem Sheets 1-2 Solutions - ODEs]] | PS1, PS2 Q1–3 | PS2 Q2(c) fails *because* $\lambda=\frac14$ is an eigenvalue of Q3(b) |
| [[MATH2048 Problem Sheets 2-4 Solutions - Fourier Series]] | PS2 Fourier page, PS3, PS4 Q1–2 | $\sum\frac{(-1)^n}{1+n^2}=\frac12(1+\pi/\sinh\pi)$, checked numerically |
| [[MATH2048 Problem Sheet 4-5 Solutions - Fourier and Laplace Transforms]] | PS4 FT page, PS5 | Q4 closed form $k_1=2e^{\gamma\tau^*/2}$ |
| [[MATH2048 Problem Sheets 6-7 Solutions - PDEs]] | PS6, PS7 | Every answer printed on the sheets is reproduced |
| [[MATH2048 Problem Sheets 8-11 Solutions - Vector Calculus]] | PS8–PS11 | All integrals checked by explicit parametrisation |
| [[MATH2048 Past Paper Solutions]] | 2023/24, 2024/25, 2025/26 (A and B) | All agree with the official solutions |

> [!warning] Source errata found while verifying (corrected in these notes)
> Most of these are in the *text* of the Lecture Notes, some possibly only as extraction artefacts:
> - **Line-integral Example 1b**: printed as $6$. That is Example 2's integrand; the correct value is $-\tfrac{79}{2}$.
> - **Line-integral Example 1a**: the minus sign is lost; it should be $-\tfrac{323}{7}$.
> - **Paraboloid Stokes example**: both sides are $18\pi$, not $18$.
> - **Lecture 6**: the periodic-extension coefficient has its sign lost; it is $b_n=-1/n$.
> - **Lecture Notes §4.7.3, spherical wave via Laplace**: the denominator should be $as+c$, not $a^2s+c$.
> - **Stokes orientation**: the notes' wording, "clockwise relative to $\mathbf n$", means the right-hand rule. It is anticlockwise when viewed from the tip of $\mathbf n$.

## Exam strategy
1. **A1**: memorise the three proofs (derivative rule, $\delta$, second shift theorem) together with their conditions. Practise the full cycle: rewrite the source as $f(t-a)H(t-a)$, transform, partial fractions, invert with both shift theorems.
2. **A2**:
   - Write the separated ODEs and **justify** the separation constant.
   - Do all **three** $\lambda$ cases, including $\lambda=0$.
   - Watch the sign convention: the exams use $X''-\lambda X=0$, giving $\lambda_n=-n^2$.
   - Fit the initial data **by orthogonality** (trig identities first).
3. **B1**: curl first. If it is zero, find $\phi$ and use the endpoints. If it is non-zero, parametrise and integrate.
4. **B2**: Gauss plus spherical coordinates. Derive the Jacobian in full, and use symmetry and shifts to avoid extra integrals.

## All notes
```dataview
TABLE type, status, file.mtime AS "Updated"
FROM "Year 2/MATH2048 Mathematics for Engineering and the Environment Part II"
WHERE type
SORT type ASC, file.name ASC
```

## Builds on / feeds into
- **Into** [[SESA2027 Aerospace Mechanics & Control Hub]]: ODEs, the characteristic equation ([[Damping Ratio and Natural Frequency]]), Laplace transforms ([[Laplace Transform]]), the frequency response ([[Frequency Response Function]]).
- **Into** [[SESA2029 Digital Aerospace Methods Hub]]: the heat equation and the Fourier number ([[CFL and Fourier Numbers]]), mode shapes ([[Natural Frequencies and Mode Shapes]]).
- **Into** [[SESA2022 Aerodynamics Hub]]: Laplace's equation in potential flow ([[Streamfunction and Velocity Potential]]), circulation via Stokes ([[Kelvin's Circulation Theorem]], [[Kutta-Joukowski Theorem]]), vorticity as the curl.
