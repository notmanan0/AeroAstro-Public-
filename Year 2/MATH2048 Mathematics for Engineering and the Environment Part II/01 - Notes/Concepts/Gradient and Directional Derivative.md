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
sources: ["02 - Sources/Lectures & Problem Sheets/Vector Calculus/Lecture23_vector03.pdf"]
---

# Gradient and Directional Derivative

## Definition

> [!note] Definition
>
> $$\nabla\phi=\phi_x\mathbf i+\phi_y\mathbf j+\phi_z\mathbf k,\qquad \nabla_{\hat{\mathbf v}}\phi=\hat{\mathbf v}\cdot\nabla\phi .$$

## Explanation
- **Directional derivative**: it follows from the chain rule applied to $f(t)=\phi(\mathbf r_0+t\mathbf v)$. Always use a **unit** direction vector $\hat{\mathbf v}$.
- **Steepest ascent**: $\phi$ increases fastest along $\nabla\phi$, at rate $|\nabla\phi|$. It decreases fastest along $-\nabla\phi$.
- **Normal to level surfaces**: $\nabla\phi$ is normal to $\phi=c$. This gives:
  - the tangent plane $\nabla\phi(P)\cdot(\mathbf r-\mathbf r_P)=0$;
  - the angle between two surfaces, $\cos\theta=\dfrac{\mathbf n_1\cdot\mathbf n_2}{|\mathbf n_1||\mathbf n_2|}$.
- **Radial fields**: $\nabla f(r)=f'(r)\,\hat{\mathbf r}$. In particular $\nabla r=\hat{\mathbf r}$ and $\nabla(1/r)=-\hat{\mathbf r}/r^2$.
- **Rules**: $\nabla$ is linear, and it obeys the product rule $\nabla(\phi\psi)=\phi\nabla\psi+\psi\nabla\phi$.

## Examples
- $f=2x+3y^2+2xyz$ at $(1,2,1)$ in the direction $(2,2,1)$: the rate is $44/3$ (PS8 Q2b).
- The surfaces $x^2+y^2+z^2=9$ and $z=x^2+y^2-3$ meet at $(2,-1,2)$ at $\theta\approx54.4^\circ$.

![[m2048_vc_gradient_level_curves.png|440]]

## Related
- [[Divergence, Curl and the Laplacian]] · [[Conservative Vector Fields]] · [[Line Integrals]]

## Sources
- Lecture 23; Lecture Notes §8.1.4–8.1.7
