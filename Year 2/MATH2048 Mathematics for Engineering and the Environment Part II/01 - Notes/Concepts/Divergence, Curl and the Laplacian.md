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
sources: ["02 - Sources/Lectures & Problem Sheets/Vector Calculus/Lecture24_vector04.pdf", "02 - Sources/Lectures & Problem Sheets/Vector Calculus/Lecture25_vector05.pdf", "02 - Sources/Lectures/MATH2048 Lecture 24.txt", "02 - Sources/Lectures/MATH2048 Lecture 25.txt"]
---

# Divergence, Curl and the Laplacian

The **divergence** $\nabla\cdot\mathbf F=\partial_xF_1+\partial_yF_2+\partial_zF_3$ turns a vector field into a scalar field, the **curl** $\nabla\times\mathbf F$, the determinant with rows $(\mathbf i,\mathbf j,\mathbf k)$, $(\partial_x,\partial_y,\partial_z)$ and $(F_1,F_2,F_3)$, turns it into another vector field, and the **Laplacian** $\nabla^2f=\nabla\cdot\nabla f=f_{xx}+f_{yy}+f_{zz}$ is a second derivative.

MATH2048 builds the first two from the gradient by requiring linearity and the product rule $\nabla\cdot(f\mathbf c)=\nabla f\cdot\mathbf c$ or $\nabla\times(f\mathbf c)=\nabla f\times\mathbf c$ for constant vectors; the constant Cartesian basis then forces the formulas. The divergence measures expansion: positive at a source, negative at a sink, and by the continuity equation $\frac{D\rho}{Dt}=-\rho\nabla\cdot\mathbf v$ it is the rate at which a fluid element's volume grows. A field with zero divergence is solenoidal, which does not make it constant, for example $y^2z\,\mathbf i+xz\,\mathbf j-y^2\,\mathbf k$. The curl measures local rotation; for a velocity field it is the vorticity, and a shear flow such as $y\,\mathbf i$ has curl even though its streamlines are straight.

Because mixed partial derivatives commute, $\nabla\times\nabla f=\mathbf 0$ and $\nabla\cdot(\nabla\times\mathbf F)=0$; the first is the test for [[Conservative Vector Fields]]. Other identities on the formula sheet include $\nabla\times(\nabla\times\mathbf F)=\nabla(\nabla\cdot\mathbf F)-\nabla^2\mathbf F$, where the Laplacian of a vector field acts on each component. The Laplacian appears in the wave, heat and Laplace equations and as the viscous term of Navier–Stokes.

![[m2048_vc_div_curl_fields.png|640]]

## Related

- Derivation: [[MATH2048 VC2 - Divergence, Curl, Laplacian and Vector Identities]]
- [[Gradient and Directional Derivative]] · [[Divergence Theorem]] · [[Stokes' Theorem]] · [[Laplace's Equation]]
