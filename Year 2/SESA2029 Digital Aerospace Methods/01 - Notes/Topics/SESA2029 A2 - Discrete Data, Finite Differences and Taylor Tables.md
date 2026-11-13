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
> A computer stores a function only at grid points, so integrals become sums (the trapezoid rule) and derivatives become finite differences: forward, backward (upwind) or central. Expanding the neighbouring values in Taylor series shows that the one-sided differences have an error proportional to $h$ (first order) while the central difference's error is proportional to $h^2$ (second order), so halving the spacing halves or quarters the error. The Taylor-table method derives the most accurate scheme on any chosen set of points; on $f_{j-2},f_{j-1},f_j$ it gives the second-order upwind scheme $f'_j\approx(f_{j-2}-4f_{j-1}+3f_j)/2h$.

> [!summary]- Exam use: quick path
> - **Use it when:** you must derive a finite-difference scheme, find its truncation error and order, or read the order off convergence data.
> - **Assumptions:** uniform spacing $h$; a smooth function, so the Taylor series converges.
> - **Method:** 1. Write the scheme with unknown coefficients plus an error $\varepsilon$; multiply by $h$ and move everything except $h\varepsilon$ to the left. 2. Expand each $f_{j+k}$ by replacing $h$ with $kh$. 3. Tabulate coefficients against $f_j$, $hf'_j$, $\tfrac{h^2}{2}f''_j$, … 4. Set as many column sums to zero as there are unknowns and solve. 5. The next column gives $h\varepsilon$; divide by $h$, and the power of $h$ is the order.
> - **Common mistakes:** losing a sign when a term moves to the left-hand side; quoting the power of $h$ in $h\varepsilon$ rather than in $\varepsilon$.
> - **Practise:** [[#5. The Taylor-table method]] · [[#Four schemes at one point]] · [[SESA2029 CFD Worked Examples#Q2: Three-point one-sided schemes|CFD worked examples Q2]]

The numerical methods of A2 to A6 are what commercial CFD codes use internally to conserve mass, momentum and energy. The finite-difference formulae below are built from first-year calculus and Taylor series.

Suppose a smooth curve is known only at a row of points. Any derivative calculated from those points is the slope of some line drawn through them, and different choices of points give slightly different slopes. As the points crowd closer together, every choice converges on the true slope, but at different rates, and the Taylor series is the tool that measures how fast. The rate matters in practice: a scheme whose error falls as $h^2$ reaches a given accuracy with far fewer points than one whose error falls as $h$, and in three dimensions the number of points is cubed.

## 1. Discrete data and the trapezoid rule

A continuous function $f(x)$ is stored as values $f_j=f(x_j)$ at grid points $x_j$, $j=0,1,\dots,N$: $N$ intervals and $N+1$ points, like arrays in Python. For the analysis the spacing is uniform, $x_j=jh$; on a non-uniform grid $h$ is replaced by the local $\Delta x_j$.

The trapezoid rule adds up the areas of the trapezia between neighbouring points. The panel between points 1 and 2 has average height $\tfrac12(f_1+f_2)$ and width $h$, so

$$
A_{12}=\frac{f_1+f_2}{2}h.
$$

Summing over all $N$ panels,

$$
A=\sum_{j=0}^{N-1}\frac{f_j+f_{j+1}}{2}h.
$$

Every interior value appears in two neighbouring panels, each time with weight $\tfrac12$, while $f_0$ and $f_N$ appear once each. Collecting terms,

$$
A=h\left[\frac{f_0+f_N}{2}+\sum_{j=1}^{N-1}f_j\right].
$$

The two forms are equal; the first is the more useful because it carries straight over to non-uniform spacing by replacing $h$ with $x_{j+1}-x_j$ inside the sum. In the coursework it integrates the boundary-layer velocity profiles from Fluent to give the displacement and momentum thicknesses and the shape factor ([[Displacement and Momentum Thickness]]); see [[#Trapezoid rule on a boundary-layer profile]].

## 2. Three ways to take a derivative

To estimate $f'$ at point $j$ there are three obvious choices. Looking forwards to the next point gives the forward difference, looking back gives the backward difference, and looking both ways gives the central difference:

$$
f'_j\approx\frac{f_{j+1}-f_j}{h},
\qquad
f'_j\approx\frac{f_j-f_{j-1}}{h},
\qquad
f'_j\approx\frac{f_{j+1}-f_{j-1}}{2h}.
$$

If the flow runs from left to right, the backward difference looks into the wind and is called upwind; the forward one is downwind. All three are straight-line slopes through grid values, and the figure shows how each misses the true tangent of a curved function by a different amount.

![[dam_fd_slopes.png|900]]

The second derivative is the derivative of the first. Take the forward slope as the first derivative at the half point $j+\tfrac12$ and the backward slope as the first derivative at $j-\tfrac12$; these are a distance $h$ apart, so

$$
f''_j\approx\frac{f'_{j+1/2}-f'_{j-1/2}}{h}.
$$

Substitute the two slopes:

$$
f''_j\approx\frac{1}{h}\left[\frac{f_{j+1}-f_j}{h}-\frac{f_j-f_{j-1}}{h}\right].
$$

Collect the terms over $h^2$:

$$
f''_j\approx\frac{f_{j-1}-2f_j+f_{j+1}}{h^2}.
$$

## 3. Accuracy from the Taylor series

The Taylor series about $x_j$ gives the value one step away:

$$
f_{j+1}=f_j+hf'_j+\frac{h^2}{2}f''_j+\frac{h^3}{6}f'''_j+\frac{h^4}{24}f''''_j+\dots
$$

Replacing $h$ by $-h$ flips the sign of every odd term:

$$
f_{j-1}=f_j-hf'_j+\frac{h^2}{2}f''_j-\frac{h^3}{6}f'''_j+\frac{h^4}{24}f''''_j-\dots
$$

### Forward difference

Move $f_j$ to the left of the first expansion:

$$
f_{j+1}-f_j=hf'_j+\frac{h^2}{2}f''_j+\frac{h^3}{6}f'''_j+\dots
$$

Divide by $h$:

$$
\frac{f_{j+1}-f_j}{h}=f'_j+\frac h2f''_j+\dots
$$

Rearrange for $f'_j$:

$$
f'_j=\frac{f_{j+1}-f_j}{h}\underbrace{-\frac h2f''_j-\frac{h^2}{6}f'''_j-\dots}_{\varepsilon}
$$

The first part is the forward difference; the rest is its truncation error $\varepsilon$, led by a term proportional to $h$ and to $f''$.

### Backward difference

Do the same with the second expansion. Move $f_j$ to the left and change sign:

$$
f_j-f_{j-1}=hf'_j-\frac{h^2}{2}f''_j+\frac{h^3}{6}f'''_j-\dots
$$

Divide by $h$ and rearrange:

$$
f'_j=\frac{f_j-f_{j-1}}{h}+\frac h2f''_j-\frac{h^2}{6}f'''_j+\dots
$$

The leading error is $+\tfrac h2f''_j$, equal and opposite to the forward difference's.

### Central difference

Because the two leading errors are equal and opposite, combine the expansions. Subtract the second from the first: $f_j$ cancels, the even-derivative terms cancel, and the odd ones double:

$$
f_{j+1}-f_{j-1}=2hf'_j+\frac{2h^3}{6}f'''_j+\dots
$$

Simplify $2/6$:

$$
f_{j+1}-f_{j-1}=2hf'_j+\frac{h^3}{3}f'''_j+\dots
$$

Divide by $2h$:

$$
\frac{f_{j+1}-f_{j-1}}{2h}=f'_j+\frac{h^2}{6}f'''_j+\dots
$$

Rearrange:

$$
\boxed{f'_j=\frac{f_{j+1}-f_{j-1}}{2h}-\frac{h^2}{6}f'''_j+\dots}
$$

The central difference is second order. With $h=10^{-3}$ its error scales as $10^{-6}$, a thousand times smaller than a first-order error.

### Second derivative

Adding the two expansions instead, the odd terms cancel and the even ones double:

$$
f_{j+1}+f_{j-1}=2f_j+h^2f''_j+\frac{2h^4}{24}f''''_j+\dots
$$

Move $2f_j$ to the left:

$$
f_{j-1}-2f_j+f_{j+1}=h^2f''_j+\frac{h^4}{12}f''''_j+\dots
$$

Divide by $h^2$ and rearrange:

$$
\boxed{f''_j=\frac{f_{j-1}-2f_j+f_{j+1}}{h^2}-\frac{h^2}{12}f''''_j+\dots}
$$

The three-point second derivative is second order too.

### What the error term tells you

The extra Taylor terms count as error even though more terms usually mean more accuracy, because the scheme only has the values at the grid points. The finite difference is all it can compute; everything else in the series is what it misses, and the leading missing term dominates for small $h$.

The leading error term carries two pieces of information. The power of $h$ is the order of accuracy. The derivative in it says which functions the scheme differentiates exactly: a first-order scheme's error contains $f''$, so it is exact for straight lines; the central scheme's contains $f'''$, so it is exact for quadratics, since their third derivative is zero.

## 4. Seeing the order in convergence data

Differentiating $\sin2\pi x$ on $0\le x<1$ with $N$ periodic points and comparing with the exact $2\pi\cos2\pi x$ gives the following RMS error divided by $2\pi$:

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

Doubling $N$ halves the first-order error and quarters the second-order error; on log–log axes the slopes are $-1$ and $-2$. The order can be read off any two rows. If $\varepsilon\propto h^p$ and $h$ halves,

$$
\frac{\varepsilon(h)}{\varepsilon(h/2)}=2^p
\quad\Longrightarrow\quad
p=\log_2\frac{\varepsilon(h)}{\varepsilon(h/2)}.
$$

For the central column between $N=256$ and $512$, $p=\log_2(7.10\times10^{-5}/1.80\times10^{-5})=\log_23.94=1.98$. A fourth-order scheme would fall sixteenfold per doubling.

![[dam_fd_convergence.png|900]]

The figure adds the three-point upwind scheme of [[#5. The Taylor-table method]]. It is also second order, but its curve sits a factor of 2 above the central one, which is exactly the ratio of the leading error coefficients, $\tfrac{h^2}{3}$ against $\tfrac{h^2}{6}$. Order sets the slope; the coefficient sets the height.

CFD should therefore be at least second order. In Fluent it is sometimes necessary to start on first order just to get a solution, then switch to second order for the final answer.

## 5. The Taylor-table method

The general problem: find the best approximation to $f'_j$ from the three points $f_{j-2}$, $f_{j-1}$, $f_j$, a one-sided upwind stencil. Write it as approximation plus error, with unknown coefficients:

$$
f'_j=\frac{af_{j-2}+bf_{j-1}+cf_j}{h}+\varepsilon.
$$

Multiply by $h$:

$$
hf'_j=af_{j-2}+bf_{j-1}+cf_j+h\varepsilon.
$$

Move everything except the error to the left:

$$
hf'_j-af_{j-2}-bf_{j-1}-cf_j=h\varepsilon.
$$

The Taylor series for $f_{j-2}$ comes from replacing $h$ by $-2h$, so each term picks up $(-2)^n$:

$$
f_{j-2}=f_j-2hf'_j+4\frac{h^2}{2}f''_j-8\frac{h^3}{6}f'''_j+\dots
$$

Each left-hand term's coefficients are tabulated against the Taylor terms. The row for $-af_{j-2}$ is $-a$ times the expansion above, and the row for $-bf_{j-1}$ is $-b$ times the expansion of $f_{j-1}$:

| Term | $f_j$ | $hf'_j$ | $\frac{h^2}{2}f''_j$ | $\frac{h^3}{6}f'''_j$ |
|---|---|---|---|---|
| $hf'_j$ | 0 | 1 | 0 | 0 |
| $-af_{j-2}$ | $-a$ | $2a$ | $-4a$ | $8a$ |
| $-bf_{j-1}$ | $-b$ | $b$ | $-b$ | $b$ |
| $-cf_j$ | $-c$ | 0 | 0 | 0 |
| column sum | 0 | 0 | 0 | $h\varepsilon$ |

Three unknowns can zero three columns. The first three column sums give

$$
-a-b-c=0\ \Rightarrow\ a+b+c=0,
$$

$$
1+2a+b=0,
$$

$$
-4a-b=0\ \Rightarrow\ 4a+b=0.
$$

Subtract the second equation from the third:

$$
(4a+b)-(1+2a+b)=0\ \Rightarrow\ 2a-1=0\ \Rightarrow\ a=\tfrac12.
$$

Back-substitute into the third:

$$
b=-4a=-2.
$$

And into the first:

$$
c=-a-b=-\tfrac12+2=\tfrac32.
$$

The fourth column is no longer zero; it is the error:

$$
h\varepsilon=(8a+b)\frac{h^3}{6}f'''_j=\left(4-2\right)\frac{h^3}{6}f'''_j=\frac{h^3}{3}f'''_j.
$$

Divide by $h$:

$$
\varepsilon=\frac{h^2}{3}f'''_j.
$$

So

$$
\boxed{f'_j=\frac{f_{j-2}-4f_{j-1}+3f_j}{2h}+\frac{h^2}{3}f'''_j}
$$

a second-order upwind scheme: halve $h$ and the error falls by four. Its mirror image, found the same way on $f_j,f_{j+1},f_{j+2}$, is the second-order forward scheme $(-3f_j+4f_{j+1}-f_{j+2})/2h$ with the same error term $+\tfrac{h^2}{3}f'''_j$, because the error is even in $h$.

> [!check] The scheme is exact for a quadratic
> Its error contains $f'''$, so it should differentiate $f=x^2$ exactly. At $x_j=0$ with $h=1$: $f_{j-2}=4$, $f_{j-1}=1$, $f_j=0$, so $(4-4\times1+0)/2=0=f'(0)$. At $x_j=1$: $f=1,0,1$ at $x=-1,0,1$, giving $(1-0+3)/2=2=f'(1)$. Both exact.

The method works for any stencil and any derivative. With $n$ unknown coefficients, $n$ columns can be zeroed, and the first non-zero column gives the leading error. Keep signs consistent: a term moved to the left with a minus sign carries the minus into every entry of its row.

## 6. Non-uniform grids

On a stretched grid the same ideas hold with local spacings:

$$
f'_j\approx\frac{f_{j+1}-f_j}{x_{j+1}-x_j},
\qquad
f''_j\approx\frac{\dfrac{f_{j+1}-f_j}{x_{j+1}-x_j}-\dfrac{f_j-f_{j-1}}{x_j-x_{j-1}}}{\tfrac12(x_{j+1}-x_{j-1})}.
$$

The second formula is the half-point construction of [[#2. Three ways to take a derivative]] with the two slopes now a distance $\tfrac12(x_{j+1}-x_{j-1})$ apart. For its Taylor analysis write $h_+=x_{j+1}-x_j$ and $h_-=x_j-x_{j-1}$. The forward slope expands as $f'_j+\tfrac{h_+}{2}f''_j+\tfrac{h_+^2}{6}f'''_j+\dots$ and the backward slope as $f'_j-\tfrac{h_-}{2}f''_j+\tfrac{h_-^2}{6}f'''_j-\dots$. Their difference is

$$
\frac{h_++h_-}{2}f''_j+\frac{h_+^2-h_-^2}{6}f'''_j+\dots
$$

Divide by $\tfrac12(h_++h_-)$ and use $h_+^2-h_-^2=(h_+-h_-)(h_++h_-)$:

$$
f''_j\approx f''_j+\frac{h_+-h_-}{3}f'''_j+\dots
$$

The leading error is proportional to the jump in spacing, $h_+-h_-$. It vanishes on a uniform grid, recovering second order, but an abrupt change of cell size drops the scheme to first order locally. That is one reason boundary-layer meshes grow their cells gradually ([[CFD Mesh Quality Metrics]]).

## Worked examples

### Four schemes at one point

*(Suggested, not lecturer-set.)* The function $f=\sin2\pi x$ is differentiated at $x_j=0.1$ with $h=0.05$, the stencil in the figure of [[#2. Three ways to take a derivative]]. The grid values are

$$
f_{j-2}=\sin0=0,\quad f_{j-1}=\sin0.1\pi=0.309017,\quad f_j=\sin0.2\pi=0.587785,\quad f_{j+1}=\sin0.3\pi=0.809017.
$$

The exact derivative is $2\pi\cos0.2\pi=5.083204$. The forward difference is

$$
\frac{0.809017-0.587785}{0.05}=4.424635,
$$

the backward difference is

$$
\frac{0.587785-0.309017}{0.05}=5.575365,
$$

the central difference is

$$
\frac{0.809017-0.309017}{0.1}=5.000000,
$$

and the three-point upwind scheme is

$$
\frac{0-4\times0.309017+3\times0.587785}{0.1}=\frac{0.527288}{0.1}=5.272878.
$$

The second derivative from the three-point formula is $(0.309017-1.175571+0.809017)/0.0025=-23.0146$, against the exact $-(2\pi)^2\sin0.2\pi=-23.2048$.

| Scheme | Value | Actual error $\varepsilon$ | Predicted leading term | Ratio when $h$ halves |
|---|---|---|---|---|
| forward | 4.4246 | $+0.659$ | $-\tfrac h2f''=+0.580$ | 2.12 |
| backward | 5.5754 | $-0.492$ | $+\tfrac h2f''=-0.580$ | 1.83 |
| central | 5.0000 | $+0.0832$ | $-\tfrac{h^2}{6}f'''=+0.0836$ | 3.99 |
| 3-point upwind | 5.2729 | $-0.190$ | $\tfrac{h^2}{3}f'''=-0.167$ | 4.21 |
| $f''$ central | $-23.015$ | $-0.190$ | $-\tfrac{h^2}{12}f''''=-0.191$ | 3.99 |

Here $\varepsilon$ is exact minus scheme, matching the convention $f'_j=\text{scheme}+\varepsilon$. The last column repeats the calculation with $h=0.025$.

> [!check] Predicted against actual error
> The leading terms predict the central and second-derivative errors to within 0.5 %, because the next neglected terms are $O(h^4)$. The one-sided schemes are off by about 15 %, because their next terms are only one power of $h$ smaller, and the forward and backward errors are unequal for the same reason; their average is the central value. The halving ratios, about 2 and about 4, confirm first and second order.

### Trapezoid rule on a boundary-layer profile

*(Suggested, not lecturer-set; the coursework uses the same steps on Fluent data.)* For the parabolic profile $u/U_e=2\eta-\eta^2$ with $\eta=y/\delta$, the displacement thickness is $\delta^*/\delta=\int_0^1(1-u/U_e)\,\mathrm d\eta=\int_0^1(1-\eta)^2\,\mathrm d\eta=\tfrac13$ exactly. With $N=4$ ($h=0.25$) the integrand values are

$$
(1-\eta)^2=1,\ 0.5625,\ 0.25,\ 0.0625,\ 0\quad\text{at }\eta=0,0.25,0.5,0.75,1.
$$

The trapezoid rule gives

$$
\frac{\delta^*}{\delta}\approx0.25\left[\frac{1+0}{2}+0.5625+0.25+0.0625\right]=0.25\times1.375=0.34375.
$$

The error is $0.0104$. With $N=8$ the result is $0.33594$ (error $0.0026$) and with $N=16$ it is $0.33398$ (error $0.00065$). Each doubling quarters the error, so the trapezoid rule is second order too. The same three grids give the momentum thickness $\theta/\delta=\int_0^1\tfrac{u}{U_e}(1-\tfrac{u}{U_e})\,\mathrm d\eta$ as $0.1230$, $0.1307$ and $0.1327$ against the exact $2/15=0.1333$, so the shape factor $H=\delta^*/\theta$ converges from 2.79 to 2.52 towards the exact $2.5$. A coarse profile overestimates $H$ noticeably; use every point Fluent gives.

## Links

- Parent: [[SESA2029 Digital Aerospace Methods Hub]]
- Previous: [[SESA2029 A1 - Digital Design and the Role of CFD and FEA]]
- Next: [[SESA2029 A3 - Iterative Solution of the Steady Heat Equation]]
- Concepts: [[Finite Difference Approximations]] · [[Truncation Error and Order of Accuracy]] · [[Taylor Table Method]]
- The same Taylor logic for time derivatives: [[SESA2029 A6 - Higher-Order Time Integration, Runge-Kutta and the Blasius Equation]]; for face interpolation: [[SESA2029 A9 - Finite Volume Method]]
- FEA counterpart (interpolation within elements): [[Shape Functions]]

## Sources

- `All_lectures_as_delivered.pdf`, L3 (slides 1–11), with transcript `SESA2029 Lecture 2025-10-09.txt` (Prof N. Sandham)
- Convergence table, worked-example values and trapezoid results recomputed in Python. Figures: `01 - Notes/Figures/generate_dam_a2_figures.py`

## Self-study tasks

### Core

- [ ] Derive the forward, backward and central differences and their errors from the Taylor series (done on the board, 2025-10-09, ll. 211–330; "know how to use Taylor series to analyse these schemes", L3 slide 11). → [[#3. Accuracy from the Taylor series]]
- [ ] Reproduce the Taylor-table derivation of the three-point upwind scheme (L3 slides 8–10; 2025-10-09, ll. 395–520). → [[#5. The Taylor-table method]] · [[SESA2029 CFD Worked Examples#Q2: Three-point one-sided schemes|Worked examples Q2]]
- [ ] Two-point forward difference by Taylor table (example sheet). → [[SESA2029 CFD Worked Examples#Q1: Two-point forward difference by Taylor table|Worked examples Q1]]
- [ ] Find the order of a scheme from convergence data (example sheet). → [[#4. Seeing the order in convergence data]] · [[SESA2029 CFD Worked Examples#Q3: Convergence rate from data|Worked examples Q3]]
- [ ] Taylor analysis of the non-uniform second derivative (examples sheet, L3 slide 11). → [[#6. Non-uniform grids]]

### Further practice

- [ ] Evaluate the four schemes for $\sin2\pi x$ at $x=0.1$ with $h=0.05$ and $0.025$ and confirm the orders (suggested, not lecturer-set). → [[#Four schemes at one point]]
- [ ] Derive the second-derivative central difference and its error. → [[#Second derivative]]
- [ ] Use the trapezoid rule on your Fluent boundary-layer profile for $\delta^*$, $\theta$ and $H$ (coursework). → [[#Trapezoid rule on a boundary-layer profile]]

## Transcript and slide slips

> [!warning] Slide slip: central difference on the summary slide (L3 slide 11)
> Where: [[#3. Accuracy from the Taylor series]].
>
> The summary slide prints the central difference as $f'_j\approx(f_{j+1}-f_{j-1})/h$. The denominator must be $2h$, the distance between the two points, as on slides 5 and 6; with $h$ alone the estimate is twice the true slope.

> [!warning] Lecture slip: central-difference error coefficient (2025-10-09, ll. 271–335)
> Where: [[#Central difference]].
>
> The central-difference error was first written on the board as $-\tfrac{h^2}{2}f'''_j$ and corrected in the lecture to $-\tfrac{h^2}{6}f'''_j$: the subtraction leaves $\tfrac{h^3}{3}f'''_j$, and dividing by $2h$ gives $\tfrac{h^2}{6}$.

> [!warning] Lecture slip: Taylor-table column equation (2025-10-09, ll. 481–490)
> Where: [[#5. The Taylor-table method]].
>
> The second column's equation was first written $1+2a-b=0$ and corrected before solving: the $-bf_{j-1}$ row has $+b$ in the $hf'_j$ column, so the equation is $1+2a+b=0$.
