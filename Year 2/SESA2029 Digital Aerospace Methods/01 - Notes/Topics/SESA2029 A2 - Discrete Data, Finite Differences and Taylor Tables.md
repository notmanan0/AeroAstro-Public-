---
title: "SESA2029 A2 - Discrete Data, Finite Differences and Taylor Tables"
module: "SESA2029 Digital Aerospace Methods"
type: topic
stream: "Part A: Computational Fluid Dynamics"
order: 2
tags: [sesa2029, cfd, finite-differences, truncation-error, taylor-table]
aliases: ["Finite differences", "Taylor tables", "CFD Lecture 3"]
date: 2026-10-30
status: lectured
coverage: "Week 2 (2025-10-09)"
parent: ["[[SESA2029 Digital Aerospace Methods Hub]]"]
prerequisites: ["[[SESA2029 A1 - Digital Design and the Role of CFD and FEA]]"]
next_topics: ["[[SESA2029 A3 - Iterative Solution of the Steady Heat Equation]]"]
key_concepts: ["[[Finite Difference Approximations]]", "[[Truncation Error and Order of Accuracy]]", "[[Taylor Table Method]]"]
tutorial_sheets: ["[[SESA2029 CFD Worked Examples]]"]
sources: ["02 - Sources/CFD/All_lectures_as_delivered.pdf (L3)", "02 - Sources/Lectures/SESA2029 Lecture 2025-10-09.txt"]
---

# SESA2029 A2 - Discrete Data, Finite Differences and Taylor Tables

> [!abstract] Summary
> A computer stores a function only at grid points, so integrals become sums (the trapezoid rule) and derivatives become finite differences: forward, backward (upwind) or central. Expanding the neighbouring values in Taylor series shows that the one-sided differences have an error proportional to $h$ (first order) while the central difference's error is proportional to $h^2$ (second order), so halving the spacing halves or quarters the error. The Taylor-table method derives the most accurate scheme on any chosen set of points, and this machinery sits inside every CFD code.

> [!summary]- Exam use: quick path
> - **Use it when:** you must derive a finite-difference scheme, find its truncation error and order, or read the order off convergence data.
> - **Assumptions:** uniform spacing $h$; a smooth function, so the Taylor series converges.
> - **Method:** 1. Write the scheme with unknown coefficients plus an error $\varepsilon$; multiply by $h$ and move everything except $h\varepsilon$ to the left. 2. Expand each $f_{j+k}$ with $h\to kh$. 3. Tabulate coefficients against $f_j$, $hf'_j$, $\tfrac{h^2}{2}f''_j$, … 4. Set as many column sums to zero as there are unknowns and solve. 5. The next column gives $h\varepsilon$; divide by $h$, and the power of $h$ is the order.
> - **Common mistakes:** losing a sign when a term moves to the left-hand side; quoting the power of $h$ in $h\varepsilon$ rather than in $\varepsilon$.
> - **Practise:** [[#5. The Taylor-table method]] · [[SESA2029 CFD Worked Examples#Q2: Three-point one-sided schemes|CFD worked examples Q2]]

This lecture opens the five on numerical methods, which build the machinery that commercial CFD codes use internally to conserve mass, momentum and energy; the following five turn to the physics and the practical use of those codes (2025-10-09, ll. 1–30). Much of it may be revision from first-year maths, but it is done from scratch.

Suppose a smooth curve is known only at a row of points. Any derivative calculated from those points is the slope of some line drawn through them, and different choices of points give slightly different slopes. As the points crowd closer together, all the choices converge on the true slope, but at different rates, and the Taylor series is the tool that measures how fast.

## 1. Discrete data and the trapezoid rule

A continuous function $f(x)$ is stored as values $f_j=f(x_j)$ at grid points $x_j$, $j=0,1,\dots,N$: $N$ intervals and $N+1$ points, like arrays in Python (ll. 1–90). For the analysis the spacing is uniform, $x_j=jh$; on a non-uniform grid $h$ is replaced by the local $\Delta x_j$.

The trapezoid rule adds up the areas of the trapezia between neighbouring points, each the average height times the width:

$$
\int_{x_0}^{x_N}f\,dx\approx\sum_{j=0}^{N-1}\frac{f_j+f_{j+1}}{2}h=h\left[\frac{f_0+f_N}{2}+\sum_{j=1}^{N-1}f_j\right].
$$

The two forms are equal; Prof Sandham prefers the first because it carries straight over to non-uniform spacing by replacing $h$ with $\Delta x$ (ll. 61–90). In the coursework it integrates the boundary-layer velocity profiles from Fluent to give the displacement and momentum thicknesses and the shape factor ([[Displacement and Momentum Thickness]]). Higher-order quadrature such as Simpson's rule is not needed in this module.

## 2. Three ways to take a derivative

To estimate $f'$ at point $j$ there are three obvious choices (ll. 91–150). Looking forwards to the next point gives the forward difference, looking back gives the backward difference, and looking both ways gives the central difference:

$$
f'_j\approx\frac{f_{j+1}-f_j}{h},
\qquad
f'_j\approx\frac{f_j-f_{j-1}}{h},
\qquad
f'_j\approx\frac{f_{j+1}-f_{j-1}}{2h}.
$$

If the flow runs from left to right, the backward difference looks into the wind and is called upwind; the forward one is downwind. All three are straight-line slopes, and all three converge to the true derivative as $h\to0$.

The second derivative is the derivative of the first. Take the forward slope at $j+\tfrac12$ and the backward slope at $j-\tfrac12$, subtract, and divide by their separation $h$ (ll. 151–180):

$$
f''_j\approx\frac{\dfrac{f_{j+1}-f_j}{h}-\dfrac{f_j-f_{j-1}}{h}}{h}=\frac{f_{j-1}-2f_j+f_{j+1}}{h^2}.
$$

## 3. Accuracy from the Taylor series

The Taylor series about $x_j$ gives the value one step away (ll. 181–240):

$$
f_{j+1}=f_j+hf'_j+\frac{h^2}{2}f''_j+\frac{h^3}{6}f'''_j+\dots
$$

Replacing $h$ by $-h$ flips the sign of every odd term:

$$
f_{j-1}=f_j-hf'_j+\frac{h^2}{2}f''_j-\frac{h^3}{6}f'''_j+\dots
$$

Rearrange the first expansion for $f'_j$:

$$
hf'_j=f_{j+1}-f_j-\frac{h^2}{2}f''_j-\dots
\quad\Longrightarrow\quad
f'_j=\frac{f_{j+1}-f_j}{h}\underbrace{-\frac h2f''_j}_{\varepsilon}+\dots
$$

The first part is the forward difference; the rest is its truncation error $\varepsilon$, proportional to $h$ and to $f''$. The second expansion gives the backward difference with error $+\tfrac h2f''_j$ (ll. 241–270).

The two errors are equal and opposite, which suggests combining them. Subtract the second expansion from the first: the even terms cancel and the odd ones double,

$$
f_{j+1}-f_{j-1}=2hf'_j+\frac{h^3}{3}f'''_j+\dots
$$

Divide by $2h$:

$$
f'_j=\frac{f_{j+1}-f_{j-1}}{2h}-\frac{h^2}{6}f'''_j+\dots
$$

The central difference is second order: its error is proportional to $h^2$. With $h=10^{-3}$ that is $10^{-6}$, a thousand times smaller than a first-order error (ll. 301–330). Adding the two expansions in the same way gives the second-derivative formula with error $-\tfrac{h^2}{12}f''''_j$.

> [!warning] Lecture slip (2025-10-09, ll. 271–335)
> The central-difference error was first written as $-\tfrac{h^2}{2}f'''_j$; a student pointed out it should be $\tfrac{h^2}{6}$ ($\tfrac{h^3}{3}$ divided by $2h$), and Prof Sandham agreed.

A student asked why the extra Taylor terms count as error when more terms usually mean more accuracy (ll. 301–330). The answer: the scheme only has the values at the grid points, so the finite difference is all it can compute; everything else in the series is what it misses, and the leading missing term dominates for small $h$.

The error term carries two pieces of information. The power of $h$ is the order of accuracy. The derivative in it says what the scheme differentiates exactly: a first-order scheme's error contains $f''$, so it is exact for straight lines; the central scheme's contains $f'''$, so it is exact for quadratics (ll. 241–250).

## 4. Seeing the order in convergence data

Prof Sandham's Python demonstration differentiates $\sin2\pi x$ on $0\le x<1$ with $N$ periodic points and compares with the exact $2\pi\cos2\pi x$ (ll. 331–395). The RMS error divided by $2\pi$, recomputed:

| $N$ | First-order forward | Second-order central |
|---|---|---|
| 4 | 0.518 | 0.257 |
| 8 | 0.273 | 0.0705 |
| 16 | 0.138 | 0.0180 |
| 32 | 0.0694 | 0.00454 |
| 64 | 0.0347 | 0.00114 |
| 128 | 0.0174 | 0.000284 |
| 256 | 0.00868 | 0.0000710 |
| 512 | 0.00434 | 0.0000180 |

Doubling $N$ halves the first-order error and quarters the second-order error; on log–log axes the slopes are −1 and −2. A fourth-order scheme would fall sixteenfold per doubling. CFD should therefore be at least second order, though in Fluent it is sometimes necessary to start on first order just to get a solution, then switch back (ll. 361–390).

![[dam_fd_convergence.png|600]]

## 5. The Taylor-table method

The general problem (ll. 395–520): find the best approximation to $f'_j$ from the three points $f_{j-2}$, $f_{j-1}$, $f_j$, a one-sided upwind stencil. Write it with unknown coefficients and an error,

$$
f'_j=\frac{af_{j-2}+bf_{j-1}+cf_j}{h}+\varepsilon.
$$

Multiply by $h$ and move everything except the error to the left:

$$
hf'_j-af_{j-2}-bf_{j-1}-cf_j=h\varepsilon.
$$

The Taylor series for $f_{j-2}$ comes from replacing $h$ by $-2h$:

$$
f_{j-2}=f_j-2hf'_j+4\frac{h^2}{2}f''_j-8\frac{h^3}{6}f'''_j+\dots
$$

Now tabulate each term's coefficients against the Taylor terms:

| Term | $f_j$ | $hf'_j$ | $\frac{h^2}{2}f''_j$ | $\frac{h^3}{6}f'''_j$ |
|---|---|---|---|---|
| $hf'_j$ | 0 | 1 | 0 | 0 |
| $-af_{j-2}$ | $-a$ | $2a$ | $-4a$ | $8a$ |
| $-bf_{j-1}$ | $-b$ | $b$ | $-b$ | $b$ |
| $-cf_j$ | $-c$ | 0 | 0 | 0 |
| column sum | 0 | 0 | 0 | $h\varepsilon$ |

Three unknowns can zero three columns:

$$
a+b+c=0,\qquad1+2a+b=0,\qquad4a+b=0.
$$

Subtract the second equation from the third: $2a-1=0$, so $a=\tfrac12$. Then $b=-4a=-2$ and $c=-a-b=\tfrac32$. The fourth column is the error:

$$
h\varepsilon=(8a+b)\frac{h^3}{6}f'''_j=(4-2)\frac{h^3}{6}f'''_j
\quad\Longrightarrow\quad
\varepsilon=\frac{h^2}{3}f'''_j.
$$

So

$$
\boxed{f'_j=\frac{f_{j-2}-4f_{j-1}+3f_j}{2h}+\frac{h^2}{3}f'''_j}
$$

a second-order upwind scheme: halve $h$ and the error falls by four (ll. 511–520). Its mirror image is the second-order forward scheme $(-3f_j+4f_{j+1}-f_{j+2})/2h$ with error $-\tfrac{h^2}{3}f'''_j$.

> [!warning] Lecture slip (2025-10-09, ll. 481–490)
> The second column's equation was first written $1+2a-b=0$; Prof Sandham spotted that the $b$ entry should be $+b$, giving $1+2a+b=0$, before solving.

The method works for any stencil and any derivative. The general rule: $n$ unknown coefficients can zero $n$ columns, and the first non-zero column gives the leading error. Keep signs consistent: a term moved to the left with a minus sign carries the minus into its row.

## 6. Non-uniform grids

On a stretched grid the same ideas hold with local spacings:

$$
f'_j\approx\frac{f_{j+1}-f_j}{x_{j+1}-x_j},
\qquad
f''_j\approx\frac{\dfrac{f_{j+1}-f_j}{x_{j+1}-x_j}-\dfrac{f_j-f_{j-1}}{x_j-x_{j-1}}}{\tfrac12(x_{j+1}-x_{j-1})}.
$$

Abrupt stretching costs formal accuracy, one reason boundary-layer meshes grow their cells gradually ([[CFD Mesh Quality Metrics]]).

## Links

- Parent: [[SESA2029 Digital Aerospace Methods Hub]]
- Previous: [[SESA2029 A1 - Digital Design and the Role of CFD and FEA]]
- Next: [[SESA2029 A3 - Iterative Solution of the Steady Heat Equation]]
- Concepts: [[Finite Difference Approximations]] · [[Truncation Error and Order of Accuracy]] · [[Taylor Table Method]]
- The same Taylor logic for time derivatives: [[SESA2029 A6 - Higher-Order Time Integration, Runge-Kutta and the Blasius Equation]]; for face interpolation: [[SESA2029 A9 - Finite Volume Method]]
- FEA counterpart (interpolation within elements): [[Shape Functions]]

## Sources

- `All_lectures_as_delivered.pdf`, L3, with transcript `SESA2029 Lecture 2025-10-09.txt` (Prof N. Sandham)
- Convergence table recomputed in Python

## Self-study tasks

### Core

- [ ] Derive the forward, backward and central differences and their errors from the Taylor series (done on the board, 2025-10-09, ll. 211–330; "ideally you write this down", l. 340). → [[#3. Accuracy from the Taylor series]]
- [ ] Reproduce the Taylor-table derivation of the three-point upwind scheme (ll. 395–520). → [[#5. The Taylor-table method]] · [[SESA2029 CFD Worked Examples#Q2: Three-point one-sided schemes|Worked examples Q2]]
- [ ] Two-point forward difference by Taylor table (example sheet). → [[SESA2029 CFD Worked Examples#Q1: Two-point forward difference by Taylor table|Worked examples Q1]]
- [ ] Find the order of a scheme from convergence data (example sheet). → [[#4. Seeing the order in convergence data]] · [[SESA2029 CFD Worked Examples#Q3: Convergence rate from data|Worked examples Q3]]

### Further practice

- [ ] Use the trapezoid rule on your Fluent boundary-layer profile for $\delta^*$, $\theta$ and $H$ (coursework, ll. 91–110). → [[#1. Discrete data and the trapezoid rule]]
- [ ] Derive the second-derivative central difference and its error. → [[#2. Three ways to take a derivative]]
