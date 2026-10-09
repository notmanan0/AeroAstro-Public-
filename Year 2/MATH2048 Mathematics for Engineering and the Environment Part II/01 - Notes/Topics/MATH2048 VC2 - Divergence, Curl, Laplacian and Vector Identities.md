---
title: "MATH2048 VC2 - Divergence, Curl, Laplacian and Vector Identities"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: topic
stream: "Block 5: Vector Calculus"
order: 16
tags:
  - math2048
  - vector-calculus
  - divergence
  - curl
aliases: ["MATH2048 Lecture 24", "MATH2048 Lecture 25", "div", "curl", "Laplacian"]
date: 2026-09-24
status: complete
parent: ["[[MATH2048 Mathematics for Engineering and the Environment Part II Hub]]"]
prerequisites: ["[[MATH2048 VC1 - Scalar and Vector Fields, Gradient and Directional Derivatives]]"]
next_topics: ["[[MATH2048 VC3 - Line Integrals and Conservative Fields]]"]
key_concepts: ["[[Divergence, Curl and the Laplacian]]"]
tutorial_sheets: ["[[MATH2048 Problem Sheets 8-11 Solutions - Vector Calculus]]"]
sources: ["02 - Sources/Lectures & Problem Sheets/Vector Calculus/Lecture24_vector04.pdf", "02 - Sources/Lectures & Problem Sheets/Vector Calculus/Lecture25_vector05.pdf", "02 - Sources/Lectures & Problem Sheets/LectureNotesMATH2048.pdf (§8.1.8–8.1.11)"]
---

# MATH2048 VC2 - Divergence, Curl, Laplacian and Vector Identities

> [!abstract] Summary
> Treat $\nabla=\mathbf i\partial_x+\mathbf j\partial_y+\mathbf k\partial_z$ as a vector operator. There are three ways to apply it:
>
> | Operation | Acts on | Gives | Measures |
> |---|---|---|---|
> | $\nabla\phi$ (grad) | scalar | vector | slope |
> | $\nabla\cdot\mathbf F$ (div) | vector | scalar | spreading (sources and sinks) |
> | $\nabla\times\mathbf F$ (curl) | vector | vector | local rotation |
>
> Two combinations always vanish: $\nabla\times\nabla\phi=\mathbf 0$ and $\nabla\cdot(\nabla\times\mathbf F)=0$. The **Laplacian** is $\nabla^2\phi=\nabla\cdot\nabla\phi$.

## Key Concepts
- [[Divergence, Curl and the Laplacian]] · [[Laplace's Equation]] (for $\nabla^2\phi=0$) · [[Conservative Vector Fields]] (curl-free fields)

---

## 1. Divergence (L24, Notes §8.1.8)
$$
\nabla\cdot\mathbf F=\frac{\partial F_1}{\partial x}+\frac{\partial F_2}{\partial y}+\frac{\partial F_3}{\partial z} .
$$

This comes from two requirements: $\operatorname{div}(\phi\mathbf c)=\nabla\phi\cdot\mathbf c$ for any constant vector $\mathbf c$, and linearity.

**Physical meaning**: the rate at which a small volume carried by the flow expands.
- $\nabla\cdot\mathbf F>0$: a source.
- $\nabla\cdot\mathbf F<0$: a sink.
- $\nabla\cdot\mathbf F=0$: incompressible or solenoidal. This does *not* mean $\mathbf F$ is constant. For example, $\mathbf F=y^2z\,\mathbf i+xz\,\mathbf j-y^2\,\mathbf k$ has zero divergence.

Useful results:
- $\nabla\cdot\mathbf r=3$.
- Product rule: $\nabla\cdot(\phi\mathbf F)=\nabla\phi\cdot\mathbf F+\phi\nabla\cdot\mathbf F$.

## 2. Curl (L24, Notes §8.1.10)
$$
\nabla\times\mathbf F=\begin{vmatrix}\mathbf i&\mathbf j&\mathbf k\\\partial_x&\partial_y&\partial_z\\F_1&F_2&F_3\end{vmatrix}=\Big(\frac{\partial F_3}{\partial y}-\frac{\partial F_2}{\partial z}\Big)\mathbf i+\Big(\frac{\partial F_1}{\partial z}-\frac{\partial F_3}{\partial x}\Big)\mathbf j+\Big(\frac{\partial F_2}{\partial x}-\frac{\partial F_1}{\partial y}\Big)\mathbf k .
$$

> [!warning] The middle component
> The $\mathbf j$ term is $\partial_zF_1-\partial_xF_3$, the opposite order to what the pattern of the other two suggests. It comes from the $-$ sign in the cofactor expansion. This is the most common slip.

**Physical meaning**: $\nabla\times\mathbf F$ is twice the local angular velocity. A small paddle wheel placed in the flow spins about the axis of the curl.
- Rigid rotation $-y\mathbf i+x\mathbf j$ has curl $2\mathbf k$.
- A *shear* flow $y\mathbf i$ also has curl ($-\mathbf k$), even though its streamlines are straight.

![[m2048_vc_div_curl_fields.png|760]]

> [!example] Notes Example: $\mathbf F=xy^2\mathbf i+e^z\mathbf j+y\sin x\,e^z\mathbf k$
> - $\mathbf i$: $\partial_y(y\sin x\,e^z)-\partial_z(e^z)=\sin x\,e^z-e^z$.
> - $\mathbf j$: $\partial_z(xy^2)-\partial_x(y\sin x\,e^z)=-y\cos x\,e^z$.
> - $\mathbf k$: $\partial_x(e^z)-\partial_y(xy^2)=-2xy$.
>
> $$\nabla\times\mathbf F=(\sin x\,e^z-e^z)\,\mathbf i-y\cos x\,e^z\,\mathbf j-2xy\,\mathbf k .$$
> Every component carries a minus sign, which is easy to drop. This result was checked in SymPy.

## 3. The two "zero" theorems (prove them, $C^2$ fields)
**(a) $\nabla\times(\nabla\phi)=\mathbf 0$.** The $\mathbf i$ component is $\partial_y\phi_z-\partial_z\phi_y=\phi_{zy}-\phi_{yz}=0$, because mixed partial derivatives commute for $C^2$ functions. The same holds for every component.

**(b) $\nabla\cdot(\nabla\times\mathbf F)=0$.** Expanding,
$$\partial_x(\partial_yF_3-\partial_zF_2)+\partial_y(\partial_zF_1-\partial_xF_3)+\partial_z(\partial_xF_2-\partial_yF_1)=0 .$$
The six terms cancel in pairs.

Consequences:
- A gradient field is curl-free, so it is **conservative** (VC3).
- A curl field is divergence-free, so it has a **vector potential** (VC5).

## 4. The Laplacian (L25, Notes §8.1.9)
$$
\nabla^2\phi=\nabla\cdot(\nabla\phi)=\phi_{xx}+\phi_{yy}+\phi_{zz} .
$$
For a vector field it acts component-wise: $\nabla^2\mathbf F=(\nabla^2F_1,\nabla^2F_2,\nabla^2F_3)$.

> [!example] Notes Example: $\phi=e^xy^3\sin z$
> $\phi_{xx}=e^xy^3\sin z$, $\phi_{yy}=6e^xy\sin z$ and $\phi_{zz}=-e^xy^3\sin z$. The first and last cancel, so
> $$\nabla^2\phi=6e^xy\sin z .$$
> SymPy agrees ✔.

## 5. Vector identities (L25, Notes §8.1.11)
| # | Identity |
|---|---|
| 1 | $\nabla(\phi\psi)=\phi\nabla\psi+\psi\nabla\phi$ |
| 2 | $\nabla\cdot(\phi\mathbf F)=\nabla\phi\cdot\mathbf F+\phi\nabla\cdot\mathbf F$ |
| 3 | $\nabla\times(\phi\mathbf F)=\nabla\phi\times\mathbf F+\phi\nabla\times\mathbf F$ |
| 4 | $\nabla\cdot(\mathbf F\times\mathbf G)=\mathbf G\cdot(\nabla\times\mathbf F)-\mathbf F\cdot(\nabla\times\mathbf G)$ |
| 5 | $\nabla\times\nabla\phi=\mathbf 0$ |
| 6 | $\nabla\cdot(\nabla\times\mathbf F)=0$ |
| 7 | $\nabla\cdot\nabla\phi=\nabla^2\phi$ |
| 8 | $\nabla\times(\nabla\times\mathbf F)=\nabla(\nabla\cdot\mathbf F)-\nabla^2\mathbf F$ |

**Operators** (PS9):
- $(\mathbf F\cdot\nabla)=F_1\partial_x+F_2\partial_y+F_3\partial_z$ is a *scalar operator*. It acts on each component of $\mathbf G$.
- $(\mathbf F\times\nabla)\cdot\mathbf G=\mathbf F\cdot(\nabla\times\mathbf G)$. Expand both sides to see this.

**Check identity 8 with PS9 Q5(c)**: $\mathbf F=x^2\mathbf i+xy\,\mathbf j+xz\,\mathbf k$.
- Directly: $\nabla\times\mathbf F=(0,-z,y)$, so $\nabla\times(\nabla\times\mathbf F)=(2,0,0)$.
- Via identity 8: $\nabla\cdot\mathbf F=4x$, so $\nabla(\nabla\cdot\mathbf F)=(4,0,0)$, and $\nabla^2\mathbf F=(2,0,0)$. The difference is $(2,0,0)$ ✔.

## Links
- Parent: [[MATH2048 Mathematics for Engineering and the Environment Part II Hub]] · Previous: [[MATH2048 VC1 - Scalar and Vector Fields, Gradient and Directional Derivatives]] · Next: [[MATH2048 VC3 - Line Integrals and Conservative Fields]]
- Practice: [[MATH2048 Problem Sheets 8-11 Solutions - Vector Calculus]] (PS8 Q5–6, PS9)
- Aero link: vorticity $\boldsymbol\omega=\nabla\times\mathbf u$ and incompressibility $\nabla\cdot\mathbf u=0$ in SESA2022 and [[Navier-Stokes Equations]].

## Sources
- Lectures 24–25; Lecture Notes §8.1.8–8.1.11. Examples and identities verified in SymPy.
