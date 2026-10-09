---
title: "Product, Quotient and Chain Rules"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 1: Calculus"
aliases: ["Product rule", "Quotient rule", "Chain rule", "Differentiation rules"]
tags: [math1054, concept, differentiation]
status: complete
parent_lectures: ["[[MATH1054 M03 - Differentiation I]]"]
related_concepts: ["[[Derivative from First Principles]]", "[[Implicit and Parametric Differentiation]]", "[[Logarithmic Differentiation]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §8.3", "MATH1054 Module Booklet, Module 3"]
---

# Product, Quotient and Chain Rules

## Definition

> [!note] Definition
>
> $$(uv)'=u'v+uv',\qquad\Big(\frac uv\Big)'=\frac{u'v-uv'}{v^2},\qquad\frac{\mathrm dy}{\mathrm dx}=\frac{\mathrm dy}{\mathrm du}\frac{\mathrm du}{\mathrm dx}$$

## Explanation
- **Chain rule**: differentiate the outer function (leaving the inside untouched), then multiply by the derivative of the inside. Repeat once per layer: $\frac{\mathrm d}{\mathrm dx}\sin^2(x^2+1)=2\sin(x^2+1)\cos(x^2+1)\cdot2x$.
- **Generalised standard forms**: $\frac{\mathrm d}{\mathrm dx}u^n=nu^{n-1}u'$, $\frac{\mathrm d}{\mathrm dx}e^u=u'e^u$, $\frac{\mathrm d}{\mathrm dx}\ln u=\frac{u'}u$, $\frac{\mathrm d}{\mathrm dx}\sin u=u'\cos u$.
- **Inverse-function rule**: $\frac{\mathrm dy}{\mathrm dx}=1\big/\frac{\mathrm dx}{\mathrm dy}$.
- **Simplify first**:
  - expand a product of polynomials;
  - split logs: $\ln\frac{x-2}{x-3}=\ln(x-2)-\ln(x-3)$;
  - rewrite roots as powers.
- A quotient can always be done as a product, $u\cdot v^{-1}$, if you prefer.

## Examples
- $(x^2+1)^3\sqrt{x-1}$ gives $\dfrac{(x^2+1)^2(13x^2-12x+1)}{2\sqrt{x-1}}$ (Ex 8.16(c)).
- $\dfrac{3x+2}{2x^2+1}$ gives $\dfrac{3-8x-6x^2}{(2x^2+1)^2}$ (Ex 8.14(a)).
- $\tan^{-1}\dfrac{2x}{1+x^2}$ gives $\dfrac{2(1-x^2)}{x^4+6x^2+1}$ (Ex 8.17(h)).

## Related
- Topics: [[MATH1054 M03 - Differentiation I]]
- Concepts: [[Derivative from First Principles]] · [[Implicit and Parametric Differentiation]] · [[Logarithmic Differentiation]]

## Sources
- James, Modern Engineering Mathematics (6th ed.) §8.3
- MATH1054 Module Booklet, Module 3
