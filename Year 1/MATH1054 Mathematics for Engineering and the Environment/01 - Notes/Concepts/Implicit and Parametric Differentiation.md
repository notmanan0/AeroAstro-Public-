---
title: "Implicit and Parametric Differentiation"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 1: Calculus"
aliases: ["Implicit differentiation", "Parametric differentiation"]
tags: [math1054, concept, differentiation]
status: complete
parent_lectures: ["[[MATH1054 M08 - Differentiation II]]"]
related_concepts: ["[[Product, Quotient and Chain Rules]]", "[[Partial Derivatives]]", "[[Logarithmic Differentiation]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §8.3.14, §8.4", "MATH1054 Module Booklet, Module 8"]
---

# Implicit and Parametric Differentiation

Parametric and implicit differentiation find $dy/dx$ for a curve that is not written as $y=f(x)$: either both coordinates are given in terms of a parameter, $x(t)$ and $y(t)$, or $x$ and $y$ are linked by an equation $F(x,y)=0$. Both are the chain rule applied with $y$ treated as a function of $x$.

For a parametric curve, $y(t)=f(x(t))$, so the chain rule gives $\dot y=\frac{dy}{dx}\dot x$, and dividing by $\dot x$ (where $\dot x\neq0$):

$$
\frac{dy}{dx}=\frac{\dot y}{\dot x}.
$$

The second derivative needs the chain rule once more, because $dy/dx$ is a function of $t$:

$$
\frac{d^2y}{dx^2}=\frac{d}{dt}\Big(\frac{dy}{dx}\Big)\frac{dt}{dx}=\frac{\frac{d}{dt}(dy/dx)}{\dot x}=\frac{\dot x\ddot y-\dot y\ddot x}{\dot x^3}.
$$

For an implicit curve, differentiate every term with respect to $x$. Each function of $y$ picks up a factor $y'$ by the chain rule, $\frac{d}{dx}y^n=ny^{n-1}y'$, and products need the product rule, $\frac{d}{dx}(xy)=y+xy'$. The result is linear in $y'$, so it can be solved for $y'$. In general form, differentiating $F(x,y(x))=0$ with the two-variable chain rule gives $F_x+F_yy'=0$, so $y'=-F_x/F_y$ wherever $F_y\neq0$ ([[Partial Derivatives]]). For $y''$, differentiate the equation for $y'$ again, substitute $y'$, and simplify with the curve's own equation.

A tangent at $(x_1,y_1)$ is $y-y_1=m(x-x_1)$ with $m=y'(x_1,y_1)$, and the normal has slope $-1/m$. Check that the point actually lies on the curve first: the curve printed in James Exercise 52, $x^3-y^3-xy-x=0$, does not pass through the given point $(1,-1)$, and the Module 8 work scheme corrects it to $x^3+y^3-xy-x=0$.

Worked examples:

- $x^2+y^2-3xy+4=0$ at $(2,4)$: $y'=\frac{3y-2x}{2y-3x}=4$, so the tangent is $y=4x-4$ and the normal is $x+4y=18$ (Example 8.23).
- The cycloid $x=a(\theta-\sin\theta)$, $y=a(1-\cos\theta)$: $y'=\cot\frac\theta2$ and $y''=-\frac1{a(1-\cos\theta)^2}$, negative everywhere, so each arch is concave down (Exercise 65).
- $x=t^2$, $y=t^3$: $y'=\frac{3t}2$ and $y''=\frac{3/2}{2t}=\frac3{4t}$ (Specimen Test 8, Q4).
- The circle $x^2+y^2-2x+4y-20=0$: $y'=\frac{1-x}{y+2}$ and, using the equation, $y''=-\frac{25}{(y+2)^3}$ (Examples 8.24 and 8.29).

The common trap is $\dfrac{d^2y}{dx^2}=\dfrac{\ddot y}{\ddot x}$, which is wrong. For $x=t^3$, $y=t^2$ it gives $\frac1{3t}$, while the correct value is $-\frac2{9t^4}$. Always differentiate $dy/dx$ with respect to $t$ and then divide by $dx/dt$. Points where $\dot x=\dot y=0$, such as the origin on $x=t^3$, $y=t^2$, can be cusps with no tangent.

## Related

- Topics: [[MATH1054 M08 - Differentiation II]] (derivations and all worked examples) · [[MATH1054 M03 - Differentiation I]]
- Concepts: [[Product, Quotient and Chain Rules]] · [[Partial Derivatives]] · [[Logarithmic Differentiation]] · [[Stationary Points and Inflection]]
- Sources: James, *Modern Engineering Mathematics* (6th ed.) §8.3.14, §8.4; MATH1054 Module Booklet, Module 8
