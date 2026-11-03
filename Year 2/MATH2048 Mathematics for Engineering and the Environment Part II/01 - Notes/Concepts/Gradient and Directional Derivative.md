---
title: "Gradient and Directional Derivative"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: concept
stream: "Block 5: Vector Calculus"
aliases: ["grad", "Nabla phi", "Steepest ascent", "Normal to level surface", "Tangent plane"]
tags: [math2048, concept, vector-calculus]
status: complete
parent_lectures: ["[[MATH2048 VC1 - Scalar and Vector Fields, Gradient and Directional Derivatives]]"]
related_concepts: ["[[Divergence, Curl and the Laplacian]]", "[[Conservative Vector Fields]]"]
sources: ["02 - Sources/Lectures & Problem Sheets/Vector Calculus/Lecture23_vector03.pdf", "02 - Sources/Lectures/MATH2048 Lecture 23.txt"]
---

# Gradient and Directional Derivative

The **gradient** of a scalar field is the vector field $\nabla f=\frac{\partial f}{\partial x}\mathbf i+\frac{\partial f}{\partial y}\mathbf j+\frac{\partial f}{\partial z}\mathbf k$. The **directional derivative** in the direction of a unit vector $\hat{\mathbf n}$ is the rate of change of $f$ per unit distance that way, $\frac{\partial f}{\partial n}=\hat{\mathbf n}\cdot\nabla f$.

The second formula follows from the chain rule applied to $f(\mathbf x_0+h\hat{\mathbf n})$, and it is why $\hat{\mathbf n}$ must be a unit vector: along $\mathbf i$ it has to give $\partial f/\partial x$, not a multiple of it. Since $\hat{\mathbf n}\cdot\nabla f=|\nabla f|\cos\theta$, the rate of change is at most $|\nabla f|$, reached along $\nabla f$, the direction of steepest ascent; $-\nabla f$ is steepest descent. Along a level surface $f$ doesn't change, so $\nabla f$ is perpendicular to every tangent direction: it is the normal to the surface $f=c$, which is how tangent planes and angles between surfaces are found.

The gradient is linear and obeys the product rule $\nabla(fg)=f\nabla g+g\nabla f$, both checked component by component. For a field depending only on $r=|\mathbf r|$, $\nabla f(r)=f'(r)\hat{\mathbf r}$. The gradient is also the building block of the other derivatives of vector calculus: the [[Divergence, Curl and the Laplacian|divergence and curl]] are made from it with a dot or cross product.

![[m2048_vc_gradient_level_curves.png|440]]

## Related

- Derivation: [[MATH2048 VC1 - Scalar and Vector Fields, Gradient and Directional Derivatives]]
- [[Divergence, Curl and the Laplacian]] · [[Conservative Vector Fields]]
