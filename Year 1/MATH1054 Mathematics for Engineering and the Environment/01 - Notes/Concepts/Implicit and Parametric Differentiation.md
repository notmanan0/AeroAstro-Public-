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

## Definition

> [!note] Definition
> - **Parametric**: $\dfrac{\mathrm dy}{\mathrm dx}=\dfrac{\dot y}{\dot x}$ and $\dfrac{\mathrm d^2y}{\mathrm dx^2}=\dfrac{\frac{\mathrm d}{\mathrm dt}(\mathrm dy/\mathrm dx)}{\dot x}$.
> - **Implicit** ($F(x,y)=0$): differentiate every term with respect to $x$, chain-ruling the $y$ terms. Equivalently, $y'=-F_x/F_y$.

## Explanation
- $\frac{\mathrm d}{\mathrm dx}y^n=ny^{n-1}y'$ and $\frac{\mathrm d}{\mathrm dx}(xy)=y+xy'$.
- **For $y''$**: differentiate $y'$ again, substitute $y'$, then use the original equation to simplify.
- **Common error**: $\frac{\mathrm d^2y}{\mathrm dx^2}\neq\frac{\ddot y}{\ddot x}$.
- **Tangent and normal** at a point: evaluate $y'$ there. Check that the point actually lies on the curve first (as with the booklet's correction of Ex 52).

## Examples
- $x^2+y^2-3xy+4=0$ at $(2,4)$: $y'=4$. The tangent is $y=4x-4$ and the normal is $x+4y=18$ (Ex 8.23).
- Cycloid: $y'=\cot\frac\theta2$ and $y''=-\frac1{a(1-\cos\theta)^2}$ (Ex 65).
- $x=t^2$, $y=t^3$: $y'=\frac{3t}2$ and $y''=\frac3{4t}$ (Specimen Test 8, Q4).

## Related
- Topics: [[MATH1054 M08 - Differentiation II]]
- Concepts: [[Product, Quotient and Chain Rules]] · [[Partial Derivatives]] · [[Logarithmic Differentiation]]

## Sources
- James, Modern Engineering Mathematics (6th ed.) §8.3.14, §8.4
- MATH1054 Module Booklet, Module 8
