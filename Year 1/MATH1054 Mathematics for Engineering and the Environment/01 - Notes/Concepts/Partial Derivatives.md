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

The partial derivative $\partial f/\partial x$ of a function $f(x,y)$ is its derivative with respect to $x$ while $y$ is held constant, $\dfrac{\partial f}{\partial x}=\displaystyle\lim_{\Delta x\to0}\frac{f(x+\Delta x,y)-f(x,y)}{\Delta x}$, and $\partial f/\partial y$ is defined the same way with $x$ held constant.

Because the other variable is a constant during the differentiation, every one-variable rule applies unchanged: $\frac{\partial}{\partial y}e^{-xy}=-xe^{-xy}$, since $x$ is a constant multiplier of $y$, while $\frac{\partial}{\partial x}e^{-xy}=-ye^{-xy}$. The curly $\partial$ (or the subscript notation $f_x$, $f_y$) marks the derivative as partial. Geometrically, $f_x$ at $(x_0,y_0)$ is the slope of the surface $z=f(x,y)$ along the slice $y=y_0$, the slope in the $x$ direction. For $f=3x^2+2xy+y^3$ (James Example 9.24(a)), $f_x=6x+2y$ and $f_y=2x+3y^2$, so at $(1,1)$ the slopes along the two slices are $8$ and $5$; the difference quotients with a step of $0.01$ are $8.03$ and $5.0301$.

For a composite function $f(u)$ with $u=u(x,y)$, the chain rule reads $\dfrac{\partial f}{\partial x}=\dfrac{\mathrm df}{\mathrm du}\dfrac{\partial u}{\partial x}$: ordinary for $f$, which depends on $u$ alone, partial for $u$. So $\sin(x^2-3y)$ has $f_x=2x\cos(x^2-3y)$ and $f_y=-3\cos(x^2-3y)$. A product needs the product rule in each variable. For $f=(y^2+x)e^{-xy}$:

$$
\begin{aligned}
f_x&=e^{-xy}+(y^2+x)(-y)e^{-xy}=(1-xy-y^3)e^{-xy},\\
f_y&=2ye^{-xy}+(y^2+x)(-x)e^{-xy}=(2y-xy^2-x^2)e^{-xy}.
\end{aligned}
$$

For $f=(3x^2+y^2+2xy)^{1/2}$ (Exercise 39(c)), $f_x=(3x+y)/f$ and $f_y=(x+y)/f$.

Differentiating twice gives second partial derivatives, and for functions with continuous second partials the mixed ones are equal, $f_{xy}=f_{yx}$ (for $3x^2+2xy+y^3$ both are $2$). That equality is the basis of the exactness test for first-order ODEs ([[Exact Differential Equations]]) and of conservative fields in MATH2048, and the vector of first partials is the gradient $\nabla f=(f_x,f_y,f_z)$ ([[Gradient and Directional Derivative]]).

The common trap is differentiating the variable that is being held: $\dfrac{\partial}{\partial x}(x^2y^3)=2xy^3$, with $y^3$ carried along as a constant factor, not $2xy^3+3x^2y^2$. A second trap is splitting a log before checking the domain: $\ln(xy)$ is defined for $x,y<0$ as well, where $\ln x+\ln y$ is not, though $f_x=1/x$ and $f_y=1/y$ hold in both quadrants.

## Related

- Topics: [[MATH1054 M03 - Differentiation I]] (Section 6) · [[MATH1054 M12 - Differential Equations II]]
- Concepts: [[Derivative from First Principles]] · [[Product, Quotient and Chain Rules]] · [[Exact Differential Equations]] · [[Gradient and Directional Derivative]]
- Later: [[MATH2048 VC1 - Scalar and Vector Fields, Gradient and Directional Derivatives]] · [[MATH2048 PDE1 - Classification of PDEs and the Wave Equation]]
- Sources: James, *Modern Engineering Mathematics* (6th ed.) §9.6.2; MATH1054 Module Booklet, Module 3
