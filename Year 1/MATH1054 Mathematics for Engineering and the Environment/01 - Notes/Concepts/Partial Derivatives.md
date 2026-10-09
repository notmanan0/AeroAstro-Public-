---
title: "Partial Derivatives"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 1: Calculus"
aliases: ["Partial differentiation", "∂f/∂x"]
tags: [math1054, concept, partial-derivatives]
status: complete
parent_lectures: ["[[MATH1054 M03 - Differentiation I]]", "[[MATH1054 M12 - Differential Equations II]]"]
related_concepts: ["[[Derivative from First Principles]]", "[[Exact Differential Equations]]", "[[Gradient and Directional Derivative]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §9.6", "MATH1054 Module Booklet, Module 3"]
---

# Partial Derivatives

## Definition

> [!note] Definition
> For $f(x,y)$, $\dfrac{\partial f}{\partial x}$ is the derivative with respect to $x$, holding $y$ **constant**:
> $$\frac{\partial f}{\partial x}=\lim_{\Delta x\to0}\frac{f(x+\Delta x,y)-f(x,y)}{\Delta x}$$

## Explanation
- All the single-variable rules apply. The other variable just behaves like a number: $\frac{\partial}{\partial y}e^{-xy}=-xe^{-xy}$.
- **Geometrically**, it is the slope of the surface $z=f(x,y)$ along the $x$-direction.
- **Mixed partials commute** for smooth functions: $f_{xy}=f_{yx}$. This is the basis of the **exactness test** for ODEs ([[Exact Differential Equations]]) and of conservative fields in MATH2048.
- The vector of partials is the gradient, $\nabla f=(f_x,f_y,f_z)$ ([[Gradient and Directional Derivative]]).

## Examples
- $f=(y^2+x)e^{-xy}$: $f_x=(1-xy-y^3)e^{-xy}$ and $f_y=(2y-xy^2-x^2)e^{-xy}$ (Ex 9.24).
- $f=(3x^2+y^2+2xy)^{1/2}$: $f_x=\dfrac{3x+y}{f}$ and $f_y=\dfrac{x+y}{f}$ (Ex 39(c)).

## Related
- Topics: [[MATH1054 M03 - Differentiation I]] · [[MATH1054 M12 - Differential Equations II]]
- Concepts: [[Derivative from First Principles]] · [[Exact Differential Equations]] · [[Gradient and Directional Derivative]]

## Sources
- James, Modern Engineering Mathematics (6th ed.) §9.6
- MATH1054 Module Booklet, Module 3
