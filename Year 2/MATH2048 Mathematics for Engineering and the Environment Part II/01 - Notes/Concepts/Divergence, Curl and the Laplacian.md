---
title: "Divergence, Curl and the Laplacian"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: concept
stream: "Block 5: Vector Calculus"
aliases: ["div", "curl", "Laplacian", "Vector identities", "Solenoidal", "Irrotational"]
tags: [math2048, concept, vector-calculus]
status: complete
parent_lectures: ["[[MATH2048 VC2 - Divergence, Curl, Laplacian and Vector Identities]]"]
related_concepts: ["[[Gradient and Directional Derivative]]", "[[Divergence Theorem]]", "[[Stokes' Theorem]]", "[[Laplace's Equation]]"]
sources: ["02 - Sources/Lectures & Problem Sheets/Vector Calculus/Lecture24_vector04.pdf", "02 - Sources/Lectures & Problem Sheets/Vector Calculus/Lecture25_vector05.pdf"]
---

# Divergence, Curl and the Laplacian

## Definition

> [!note] Definition
> $$\nabla\cdot\mathbf F=\partial_xF_1+\partial_yF_2+\partial_zF_3,\qquad \nabla\times\mathbf F=\begin{vmatrix}\mathbf i&\mathbf j&\mathbf k\\\partial_x&\partial_y&\partial_z\\F_1&F_2&F_3\end{vmatrix},\qquad \nabla^2\phi=\nabla\cdot\nabla\phi .$$

## Explanation
- **Divergence** measures net outflow per unit volume, i.e. sources and sinks. By Gauss's theorem it is the flux through a small closed surface divided by its volume. A field with $\nabla\cdot\mathbf F=0$ is **solenoidal** (incompressible).
- **Curl** measures local rotation, and equals twice the angular velocity of a small paddle wheel. By Stokes's theorem, $\hat{\mathbf n}\cdot(\nabla\times\mathbf F)$ is the circulation per unit area. A field with $\nabla\times\mathbf F=\mathbf 0$ is **irrotational**, and in a simply connected region it is conservative.
- **Middle component of the curl**: $(\nabla\times\mathbf F)_y=\partial_zF_1-\partial_xF_3$.
- **Always zero** (for $C^2$ fields): $\nabla\times\nabla\phi=\mathbf 0$ and $\nabla\cdot(\nabla\times\mathbf F)=0$. Both follow because mixed partial derivatives commute.

**Identities**:
- $\nabla\cdot(\phi\mathbf F)=\nabla\phi\cdot\mathbf F+\phi\nabla\cdot\mathbf F$
- $\nabla\times(\phi\mathbf F)=\nabla\phi\times\mathbf F+\phi\nabla\times\mathbf F$
- $\nabla\cdot(\mathbf F\times\mathbf G)=\mathbf G\cdot\nabla\times\mathbf F-\mathbf F\cdot\nabla\times\mathbf G$
- $\nabla\times(\nabla\times\mathbf F)=\nabla(\nabla\cdot\mathbf F)-\nabla^2\mathbf F$

**Standard results**:
- $\nabla\cdot\mathbf r=3$ and $\nabla\times\mathbf r=\mathbf 0$.
- $\nabla\cdot(-y,x,0)=0$ and $\nabla\times(-y,x,0)=2\mathbf k$.

## Examples
- $\nabla^2(e^xy^3\sin z)=6e^xy\sin z$.
- $\nabla\times\nabla\times(x^2,\,xy,\,xz)=2\mathbf i$ (PS9 Q5c).

![[m2048_vc_div_curl_fields.png|640]]

## Related
- [[Gradient and Directional Derivative]] · [[Divergence Theorem]] · [[Stokes' Theorem]] · [[Laplace's Equation]] · SESA2022 vorticity and [[Streamfunction and Velocity Potential]]

## Sources
- Lectures 24–25; PS9
