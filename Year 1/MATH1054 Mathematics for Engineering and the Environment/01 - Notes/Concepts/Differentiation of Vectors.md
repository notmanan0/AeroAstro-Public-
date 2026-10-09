---
title: "Differentiation of Vectors"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 4: Vectors and Matrices"
aliases: ["Vector functions", "Velocity and acceleration vectors", "Polar unit vectors"]
tags: [math1054, concept, vector-calculus]
status: complete
parent_lectures: ["[[MATH1054 M15 - Vectors II]]"]
related_concepts: ["[[Vector Algebra and Components]]", "[[Normal and Tangential Coordinates]]", "[[Projectile Motion]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §9.5", "MATH1054 Module Booklet, Module 15"]
---

# Differentiation of Vectors

## Definition

> [!note] Definition
> For $\mathbf r(t)=(x(t),y(t),z(t))$, differentiate and integrate **componentwise**: $\dot{\mathbf r}=(\dot x,\dot y,\dot z)$ is the velocity and $\ddot{\mathbf r}$ the acceleration.

## Explanation
- The product rules hold for $\cdot$ and $\times$. Keep the order in cross products.
- If $|\mathbf a|$ is constant, then $\mathbf a\perp\dot{\mathbf a}$, because $\frac{\mathrm d}{\mathrm dt}(\mathbf a\cdot\mathbf a)=0$.
- $|\dot{\mathbf r}|$ (speed) $\neq\frac{\mathrm d}{\mathrm dt}|\mathbf r|$.
- **Polar components**:

$$\dot{\mathbf r}=\dot r\hat{\mathbf r}+r\dot\theta\hat{\boldsymbol\theta},\qquad\ddot{\mathbf r}=(\ddot r-r\dot\theta^2)\hat{\mathbf r}+(2\dot r\dot\theta+r\ddot\theta)\hat{\boldsymbol\theta}$$

## Examples
- A projectile follows $z=\frac vux-\frac{g}{2u^2}x^2$ (Ex 9.21).
- $\ddot{\mathbf r}=(\cos t,\sin t,0)$ gives the helix $\mathbf r=(-\cos t,-\sin t,t)$ (M15 Booklet Ex A).

## Related
- Topics: [[MATH1054 M15 - Vectors II]]
- Concepts: [[Vector Algebra and Components]] · [[Normal and Tangential Coordinates]] · [[Projectile Motion]]

## Sources
- James, Modern Engineering Mathematics (6th ed.) §9.5
- MATH1054 Module Booklet, Module 15
