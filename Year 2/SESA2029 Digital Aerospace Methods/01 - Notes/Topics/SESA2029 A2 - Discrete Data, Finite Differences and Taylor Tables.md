---
title: "SESA2029 A2 - Discrete Data, Finite Differences and Taylor Tables"
module: "SESA2029 Digital Aerospace Methods"
type: topic
stream: "Part A: Computational Fluid Dynamics"
order: 2
tags:
  - sesa2029
  - cfd
  - numerical-methods
  - finite-differences
aliases: ["Numerical differentiation", "Finite difference schemes"]
date: 2026-09-24
status: complete
parent: ["[[SESA2029 Digital Aerospace Methods Hub]]"]
prerequisites: ["[[SESA2029 A1 - Digital Design and the Role of CFD and FEA]]"]
next_topics: ["[[SESA2029 A3 - Iterative Solution of the Steady Heat Equation]]"]
key_concepts: ["[[Finite Difference Approximations]]", "[[Truncation Error and Order of Accuracy]]", "[[Taylor Table Method]]"]
tutorial_sheets: ["[[SESA2029 CFD Worked Examples]]"]
sources: ["02 - Sources/CFD/All_lectures_as_delivered.pdf (L3, pp. 33–43)", "02 - Sources/CFD/CFD.txt"]
---

# SESA2029 A2 - Discrete Data, Finite Differences and Taylor Tables

> [!abstract] Summary
> A computer stores a function only at grid points, $f_j = f(x_j)$ with $x_j = jh$. Derivatives are approximated by **finite differences**: forward, backward (the upwind side) and central.
>
> Expanding each neighbour in a **Taylor series** shows the **truncation error**. Forward and backward differences are $O(h)$ (first order); the central difference is $O(h^2)$ (second order). Halving $h$ halves a first-order error and quarters a second-order one.
>
> The **Taylor-table method** is a general recipe for deriving the best scheme on any stencil. This machinery is buried inside every CFD code.

## Key Concepts
- [[Finite Difference Approximations]] · [[Truncation Error and Order of Accuracy]] · [[Taylor Table Method]]

---

## 1. Discrete representation and integration (L3)
**Grid**: $j = 0,1,\dots,N$, so $N$ intervals and $N+1$ points. $h$ is the uniform spacing; on a non-uniform grid replace $h$ with $\Delta x_j$.

**Trapezoid rule** (the only quadrature needed here):

$$
\int_{x_0}^{x_N}f\,dx\approx\sum_{j=0}^{N-1}\frac{f_j+f_{j+1}}{2}\,h = h\left[\frac{f_0+f_N}{2}+\sum_{j=1}^{N-1}f_j\right]
$$

The first form carries over directly to non-uniform spacing. Use it to integrate CFD velocity profiles for displacement and momentum thickness and the shape factor (see [[Displacement and Momentum Thickness]]).

## 2. Three ways to take a derivative (L3)
Looking from grid point $j$, with flow from left to right:

| Scheme | Formula | Direction | Order |
|---|---|---|---|
| Forward | $f'_j\approx\dfrac{f_{j+1}-f_j}{h}$ | downwind | 1 |
| Backward | $f'_j\approx\dfrac{f_j-f_{j-1}}{h}$ | **upwind** | 1 |
| Central | $f'_j\approx\dfrac{f_{j+1}-f_{j-1}}{2h}$ | both sides | 2 |
| 2nd derivative (central) | $f''_j\approx\dfrac{f_{j-1}-2f_j+f_{j+1}}{h^2}$ | both sides | 2 |

The second derivative is "the difference of two differences": $\big[(f_{j+1}-f_j)/h-(f_j-f_{j-1})/h\big]/h$, i.e. the first derivatives at $j\pm\tfrac12$.

## 3. Accuracy from the Taylor series (L3)

$$
f_{j\pm1} = f_j\pm hf'_j+\frac{h^2}{2}f''_j\pm\frac{h^3}{6}f'''_j+\dots
$$

Rearranging each expansion gives

$$
f'_j = \frac{f_{j+1}-f_j}{h}\;\underbrace{-\frac h2f''_j}_{\text{leading error}}+\dots,\qquad f'_j = \frac{f_j-f_{j-1}}{h}+\frac h2f''_j+\dots,\qquad f'_j = \frac{f_{j+1}-f_{j-1}}{2h}-\frac{h^2}{6}f'''_j+\dots
$$

In the central difference the $\pm\tfrac h2f''$ errors of the forward and backward schemes cancel exactly. That is why it is second order.

For the second derivative: $f''_j = (f_{j-1}-2f_j+f_{j+1})/h^2-\tfrac{h^2}{12}f''''_j+\dots$

> [!note] Reading an error term
> - The **power of $h$** in the leading error is the **order of accuracy**.
> - The **derivative** in it says which functions are differentiated exactly. A first-order scheme's error contains $f''$, so it is exact for straight lines. A second-order central scheme's contains $f'''$, so it is exact for quadratics.
>
> If $h = 10^{-3}$, then $h^2 = 10^{-6}$: the second-order scheme is about 1000× more accurate for the same grid.

## 4. Convergence rate (L3)
Differentiating $\sin 2\pi x$ on $0\le x<1$ (periodic, $N$ points). The table gives the RMS error in $f'$ divided by $2\pi$, recomputed in Python and matching the lecture table:

| $N$ | 1st-order forward | 2nd-order central |
|---|---|---|
| 4 | 0.5183 | 0.2569 |
| 8 | 0.2730 | 0.0705 |
| 16 | 0.1382 | 0.0180 |
| 32 | 0.0693 | 0.00453 |
| 64 | 0.0347 | 0.00114 |
| 128 | 0.0174 | 0.00028 |
| 256 | 0.00868 | 0.000071 |
| 512 | 0.00434 | 0.000018 |

- **1st order**: the error halves for every doubling of $N$. The slope is $-1$ on log–log axes.
- **2nd order**: the error falls by 4× per doubling (slope $-2$). A 4th-order scheme would fall by 16×.

![[dam_fd_convergence.png|600]]

Rule of thumb: CFD should be **at least second order**. Sometimes a first-order scheme is needed to get a solution started, before switching back to second order (see [[SESA2029 A9 - Finite Volume Method]]).

## 5. General construction: the Taylor-table method (L3)
**Problem.** Find the best 3-point approximation to $f'_j$ that uses $f_{j-2}, f_{j-1}, f_j$ (a one-sided "upwind" stencil).

1. Write the unknown scheme with an error: $f'_j = \dfrac{af_{j-2}+bf_{j-1}+cf_j}{h}+\varepsilon$.
2. Multiply by $h$ and move everything except the error to the left: $hf'_j-af_{j-2}-bf_{j-1}-cf_j = h\varepsilon$.
3. Expand every term about $j$ and write the coefficients in a table (columns are the Taylor terms):

| LHS term | $f_j$ | $hf'_j$ | $\frac{h^2}{2}f''_j$ | $\frac{h^3}{6}f'''_j$ |
|---|---|---|---|---|
| $hf'_j$ | 0 | 1 | 0 | 0 |
| $-af_{j-2}$ | $-a$ | $2a$ | $-4a$ | $8a$ |
| $-bf_{j-1}$ | $-b$ | $b$ | $-b$ | $b$ |
| $-cf_j$ | $-c$ | 0 | 0 | 0 |
| **column sum** | 0 | 0 | 0 | $h\varepsilon$ |

4. Zero as many column sums as there are unknowns:
   - $a+b+c = 0$;
   - $1+2a+b = 0$;
   - $4a+b = 0$.

   Subtracting the second equation from the third gives $a = \tfrac12$, then $b = -2$ and $c = \tfrac32$.
5. The first non-zero column is the error: $h\varepsilon = (8a+b)\dfrac{h^3}{6}f'''_j$, so $\varepsilon = \dfrac{h^2}{3}f'''_j$.

$$
\boxed{f'_j = \frac{f_{j-2}-4f_{j-1}+3f_j}{2h}+\frac{h^2}{3}f'''_j}\qquad\text{(second-order backward / upwind)}
$$

Its mirror image is the second-order forward scheme $f'_j\approx(-3f_j+4f_{j+1}-f_{j+2})/(2h)$, with error $-\tfrac{h^2}{3}f'''_j$. More worked Taylor tables are in [[SESA2029 CFD Worked Examples]] and [[Taylor Table Method]].

> [!tip] Exam technique
> 1. Use the general Taylor series and replace $h$ by $-h$ or $-2h$ to get $f_{j-1}$ and $f_{j-2}$.
> 2. Keep the sign convention consistent: if you move a term to the left with a minus sign, the table row carries the minus too.
> 3. $n$ unknown coefficients zero $n$ columns. The next column gives the leading error.
> 4. **The order is the power of $h$ in $\varepsilon$ after dividing by $h$.**

## 6. Non-uniform grids
$$
f'_j\approx\frac{f_{j+1}-f_j}{x_{j+1}-x_j},\qquad f''_j\approx\frac{\dfrac{f_{j+1}-f_j}{x_{j+1}-x_j}-\dfrac{f_j-f_{j-1}}{x_j-x_{j-1}}}{\tfrac12(x_{j+1}-x_{j-1})}
$$

Stretched grids (e.g. boundary-layer meshes) lose some formal accuracy if the stretching is abrupt. This is one reason to grow cells gradually (see [[CFD Mesh Quality Metrics]]).

## Links
- Parent: [[SESA2029 Digital Aerospace Methods Hub]] · Previous: [[SESA2029 A1 - Digital Design and the Role of CFD and FEA]] · Next: [[SESA2029 A3 - Iterative Solution of the Steady Heat Equation]]
- The same Taylor-series logic reappears for time derivatives in [[SESA2029 A6 - Higher-Order Time Integration, Runge-Kutta and the Blasius Equation]] and for face interpolation in [[SESA2029 A9 - Finite Volume Method]]
- FEA counterpart (polynomial interpolation within elements): [[Shape Functions]]

## Sources
- CFD Lecture 3, `02 - Sources/CFD/All_lectures_as_delivered.pdf` pp. 33–43; transcript `CFD.txt`
- Convergence table recomputed with `scripts/make_figures.py`
