---
title: "SESA2029 B4 - Rayleigh-Ritz Method and Shape Functions"
module: "SESA2029 Digital Aerospace Methods"
type: topic
stream: "Part B: Finite Element Analysis"
order: 15
tags:
  - sesa2029
  - fea
  - shape-functions
  - rayleigh-ritz
aliases: ["Rayleigh-Ritz", "Interpolation functions", "Shape function matrix"]
date: 2026-09-24
status: complete
parent: ["[[SESA2029 Digital Aerospace Methods Hub]]"]
prerequisites: ["[[SESA2029 B3 - Principle of Minimum Total Potential Energy]]"]
next_topics: ["[[SESA2029 B5 - Euler-Bernoulli Beam Element]]"]
key_concepts: ["[[Rayleigh-Ritz Method]]", "[[Shape Functions]]", "[[h- and p-Refinement]]"]
tutorial_sheets: ["[[SESA2029 FEA Worked Examples]]"]
sources: ["02 - Sources/FEM Lectures/Lecture_6_Rayleigh-Ritz_&_Shape_function_final.pdf", "02 - Sources/FEM Lectures/FEA.txt"]
---

# SESA2029 B4 - Rayleigh-Ritz Method and Shape Functions

> [!abstract] Summary
> A continuum has infinitely many DOF because $u(x)$ is unknown everywhere. The **Rayleigh–Ritz method** assumes a form for $u$: a polynomial with a few unknown coefficients chosen to satisfy the generalised boundary conditions. The PMPE then fixes those coefficients.
>
> The **FEM** applies Rayleigh–Ritz to each small element instead of the whole structure, and assembles the results. Rewriting the polynomial in terms of **nodal** displacements gives the **shape functions**, $u = [N]\{d\}$. Each $N_i$ equals 1 at its own node and 0 at the others.
>
> Two ways to improve accuracy:
> - **h-refinement**: smaller elements;
> - **p-refinement**: higher polynomial order (linear → quadratic → …).

## Key Concepts
- [[Rayleigh-Ritz Method]] · [[Shape Functions]] · [[h- and p-Refinement]] · [[Principle of Minimum Total Potential Energy]]

---

## 1. From energy density to strain energy (L6)
The strain energy density at any point of any elastic body is $\bar U = \tfrac12\sigma\varepsilon$. The total strain energy is

$$
U = \int_V\bar U\,dV
$$

which needs $\sigma$ and $\varepsilon$, and hence the displacement, **at every point**: infinitely many DOF. The Rayleigh–Ritz method reduces this to a finite number, by writing the displacement as a function of:
- the spatial coordinates $(x,y,z)$;
- a limited number of **unknown coefficients**, which become the DOF.

## 2. Rayleigh–Ritz on the 2-node bar (L6)
For a bar ($A$, $E$, $L$), use $\sigma = E\varepsilon$ and the 1D strain–displacement relation $\varepsilon = du/dx$:

$$
U = \frac A2\int_0^L\sigma\varepsilon\,dx = \frac{AE}{2}\int_0^L\left(\frac{du}{dx}\right)^2dx
$$

Now $U$ depends only on $u(x)$, which is unknown. So **assume its form**. Polynomials are the most common choice:

$$
u = a+bx\qquad\text{(linear)}
$$

Apply the generalised BCs: $u(0) = u_i$ gives $a = u_i$, and $u(L) = u_j$ gives $b = (u_j-u_i)/L$. So

$$
u = u_i+\frac{u_j-u_i}{L}x,\qquad\frac{du}{dx} = \frac{u_j-u_i}{L}\;\Rightarrow\;U = \frac{AE}{2L}(u_j-u_i)^2
$$

With $V = -F_iu_i-F_ju_j$ and $\partial\Pi/\partial u_i = \partial\Pi/\partial u_j = 0$, this recovers exactly the bar matrix $\frac{AE}{L}\begin{bmatrix}1&-1\\-1&1\end{bmatrix}$ from B1 and B3, now **derived** rather than assumed.

## 3. From Rayleigh–Ritz to finite elements (L6)
- Rayleigh–Ritz on a *whole* structure needs a single function valid everywhere that satisfies all the BCs. That is only possible for simple geometry and simple BCs.
- **FEM**: apply Rayleigh–Ritz to **simple, finite sub-volumes** (elements). Each element uses the same low-order polynomial, and the element models are **assembled** into the global model. That removes the geometry restriction.

## 4. Shape functions (L6)
**Interpolation** evaluates an unknown quantity anywhere in a domain from its values at known points. In FEM the known points are the nodes, and the interpolation equations are called **shape functions**.

**Linear 2-node bar** (nodes 1 at $x = 0$ and 2 at $x = L$):

$$
u = \left(1-\frac xL\right)u_1+\frac xLu_2 = \underbrace{\begin{bmatrix}N_1&N_2\end{bmatrix}}_{[N]}\begin{Bmatrix}u_1\\u_2\end{Bmatrix} = [N]\{d\},\qquad N_1 = 1-\frac xL,\quad N_2 = \frac xL
$$

**Properties**:
- **Kronecker delta**: $N_i = 1$ at its own node and 0 at every other node.
- **Partition of unity**: $\sum_iN_i = 1$, so a rigid-body translation is represented exactly.
- The infinite-DOF continuum bar becomes a **2-DOF** problem. Everything else is interpolated.

The shape-function equation $u = [N]\{d\}$ is given on the exam equation sheet.

**Strain–displacement matrix.** $\varepsilon = \dfrac{du}{dx} = \dfrac{d[N]}{dx}\{d\} = [B]\{d\}$ with $[B] = \begin{bmatrix}-\tfrac1L&\tfrac1L\end{bmatrix}$. Then

$$
[K]^e = \int_V[B]^TE[B]\,dV = \frac{AE}{L}\begin{bmatrix}1&-1\\-1&1\end{bmatrix}
$$

The same $\int[B]^T[D][B]\,dV$ formula builds the beam, plate, shell and solid matrices. See [[Shape Functions]].

## 5. Quadratic 3-node bar (L6 exercise)
Nodes 1, 2, 3 sit at $x = -L/2,\ 0,\ +L/2$, with the origin at the mid-node. Take $u = a+bx+cx^2$.

Generalised BCs:

$$
u_1 = a-\frac{bL}{2}+\frac{cL^2}{4},\qquad u_2 = a,\qquad u_3 = a+\frac{bL}{2}+\frac{cL^2}{4}
$$

Solving (3 equations, 3 unknowns):

$$
a = u_2,\qquad b = \frac{u_3-u_1}{L},\qquad c = \frac{2(u_1-2u_2+u_3)}{L^2}
$$

Collect the coefficients of each nodal displacement:

$$
[N] = \begin{bmatrix}\dfrac{2x^2}{L^2}-\dfrac xL&\;1-\dfrac{4x^2}{L^2}&\;\dfrac{2x^2}{L^2}+\dfrac xL\end{bmatrix}
$$

Check: at $x = -L/2$, $N_1 = \tfrac12+\tfrac12 = 1$, $N_2 = 0$ and $N_3 = \tfrac12-\tfrac12 = 0$. ✓

![[dam_bar_shape_functions.png|760]]

The quadratic functions are curved, and $N_1$ and $N_3$ dip slightly negative between the nodes, but each is still exactly 0 or 1 at every node. A 3-node element can represent **linearly varying strain**; a 2-node element has **constant strain** only.

## 6. h- and p-refinement (L6)
| Method | What changes | Where used |
|---|---|---|
| **h-method** | smaller element size $h$, same polynomial | mainstream codes (ANSYS, ABAQUS): the usual "mesh convergence study" |
| **p-method** | higher polynomial order $p$ (up to 8–9), same mesh | some CAD-embedded FE tools (e.g. SolidWorks-type) |

Both add DOF. In mainstream codes the element library offers a **linear** (lower-order) and a **quadratic** (higher-order) version of each element, e.g. BEAM188/189, PLANE182/183, SHELL181/281. Switching between them is a p-refinement. See [[h- and p-Refinement]].

## Links
- Parent: [[SESA2029 Digital Aerospace Methods Hub]] · Previous: [[SESA2029 B3 - Principle of Minimum Total Potential Energy]] · Next: [[SESA2029 B5 - Euler-Bernoulli Beam Element]]
- The CFD analogue of polynomial fitting (QUICK parabola, Taylor tables): [[Convective Interpolation Schemes]] · [[Taylor Table Method]]

## Sources
- FEA Lecture 6, `02 - Sources/FEM Lectures/Lecture_6_Rayleigh-Ritz_&_Shape_function_final.pdf`; transcript `FEA.txt`
