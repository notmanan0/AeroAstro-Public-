---
title: "Principal Axes of Inertia"
module: "SESA3047 Advanced Aerospace Mechanics & Control"
type: concept
stream: "Chapter 4: Dynamic Equations and 6-DOF Model"
aliases: ["principal moments of inertia", "principal inertia axes"]
tags: [sesa3047, concept, inertia, eigenvectors]
status: complete
parent_lectures: ["[[SESA3047 4.1 - Inertia Models and Rotor Dynamics]]"]
related_concepts: ["[[Inertia Matrix]]", "[[Eigenvalues and Eigenvectors]]", "[[Rotational Dynamic Equation]]"]
sources: ["02 - Sources/Lectures/Chapter_4.pdf", "02 - Sources/Lectures/L11 - SESA3047.txt", "02 - Sources/Lectures/L12 - SESA3047.txt"]
---

# Principal Axes of Inertia

> [!note] Definition
> Principal axes through the centre of mass are eigenvector directions of the real symmetric inertia matrix. In this orthonormal basis its diagonal entries are the eigenvalues, or **principal moments**.

$$
\mathbf J\mathbf e_i=\lambda_i\mathbf e_i,\qquad
\mathbf Q=[\mathbf e_1\ \mathbf e_2\ \mathbf e_3],\qquad
\mathbf J_P=\mathbf Q^T\mathbf J_B\mathbf Q=\operatorname{diag}(\lambda_i).
$$

The columns of $\mathbf Q$ are principal directions expressed in the original basis. Select their signs to form a right-handed triad. Degenerate eigenvalues permit more than one choice of principal directions.

## Physical meaning

Spin about a principal direction and $\mathbf h=\mathbf J\boldsymbol\omega$ is parallel to $\boldsymbol\omega$. A general spin combines principal directions with different inertias, so the vectors need not be parallel.

Body-fixed coordinates are not automatically principal coordinates. An aircraft's symmetry about $y=0$ gives $J_{xy}=J_{yz}=0$, but may leave $J_{xz}\ne0$. Changing attitude relative to Earth does not alter inertia expressed in the same attached body axes.

![[amc_principal_axes.png|800]]

## Worked check and dynamics

For $\mathbf J=\begin{bmatrix}4&-1&0\\-1&4&0\\0&0&6\end{bmatrix}$ kg m², the principal moments are $3,5,6$, with directions $[1,1,0]/\sqrt2$, $[-1,1,0]/\sqrt2$ and $[0,0,1]$. The full eigenvalue calculation and Euler-equation derivation are in [[SESA3047 4.1 - Inertia Models and Rotor Dynamics#3. Principal axes and diagonal inertia (4.6–4.9)|4.1 §3]].

For the symmetric aircraft with $J_{xz}\neq0$, the principal $x$ axis is tilted about $y$ by $\varepsilon$, where $\tan2\varepsilon=2J_{xz}/(J_{zz}-J_{xx})$. With $J_{xx}=1285$, $J_{zz}=2667$ and $J_{xz}=100$ kg m², $\varepsilon=4.1^\circ$ nose-down, and the principal moments are $1277.8$ and $2674.2$ kg m² ([[SESA3047 4.1 - Inertia Models and Rotor Dynamics#Worked principal axes of the aircraft inertia (suggested)|4.1 §4]]).

> [!warning] Diagonal inertia still permits coupling
> For example, $J_{xx}\dot p=L+(J_{yy}-J_{zz})qr$. Principal axes remove products of inertia, not all products of angular rates. With no external moment and $q_0=0$, a body rolling and yawing still gains pitch rate at $\dot q=(J_{zz}-J_{xx})pr/J_{yy}$, and then all three rates change. Only a single-axis spin, or equal inertias, stays put (L12 ll. 22–119; simulated in [[SESA3047 4.1 - Inertia Models and Rotor Dynamics#Inertia coupling with no external moment (L12 ll. 22–119)|4.1 §3]]).

## Related

- [[Inertia Matrix]] · [[Rotational Dynamic Equation]] · [[Eigenvalues and Eigenvectors]]
- L11 ll. 181–228; L12 ll. 22–137; Chapter_4.pdf pp. 1–4.
