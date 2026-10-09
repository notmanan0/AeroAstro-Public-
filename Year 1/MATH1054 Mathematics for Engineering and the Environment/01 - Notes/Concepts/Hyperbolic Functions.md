---
title: "Hyperbolic Functions"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 1: Calculus"
aliases: ["sinh", "cosh", "tanh", "Inverse hyperbolic functions", "Osborn's rule"]
tags: [math1054, concept, hyperbolic-functions]
status: complete
parent_lectures: ["[[MATH1054 M07 - Functions]]", "[[MATH1054 M22 - Complex Numbers II]]"]
related_concepts: ["[[Inverse Trigonometric Functions]]", "[[Euler's Formula]]", "[[Integration by Substitution]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §2.7.4–2.7.5, §8.3.12", "MATH1054 Module Booklet, Module 7"]
---

# Hyperbolic Functions

## Definition

> [!note] Definition
>
> $$\cosh x=\frac{e^x+e^{-x}}2,\qquad\sinh x=\frac{e^x-e^{-x}}2,\qquad\tanh x=\frac{\sinh x}{\cosh x}$$

## Explanation
- **Identities**:
  - $\cosh^2x-\sinh^2x=1$
  - $\cosh x\pm\sinh x=e^{\pm x}$
  - $\sinh2x=2\sinh x\cosh x$
- **Osborn's rule**: turn a trig identity into a hyperbolic one by swapping the functions and changing the sign of every product of two sines.
- **Derivatives**: $(\sinh x)'=\cosh x$ and $(\cosh x)'=\sinh x$ (no minus sign). $(\tanh x)'=\mathrm{sech}^2x$.
- **Inverses, in log form**:
  - $\sinh^{-1}x=\ln(x+\sqrt{x^2+1})$
  - $\cosh^{-1}x=\ln(x+\sqrt{x^2-1})$
  - $\tanh^{-1}x=\frac12\ln\frac{1+x}{1-x}$
- **Link to trig**: $\cosh\mathrm jx=\cos x$ and $\sinh\mathrm jx=\mathrm j\sin x$ ([[Euler's Formula]]).
- **Where they appear**: catenary cables; solutions $A\cosh kx+B\sinh kx$ of $y''=k^2y$; $\int\frac{\mathrm dx}{\sqrt{x^2\pm a^2}}$.

## Examples
- $5\cosh x+3\sinh x=4$ becomes $(2e^x-1)^2=0$, so $x=-\ln2$ (Ex 2.59).
- $\sinh x=-\frac5{12}$ gives $\cosh x=\frac{13}{12}$ and $\tanh x=-\frac5{13}$ (Specimen Test 7, Q4).
- $\frac{\mathrm d}{\mathrm dx}e^{-3x}\sinh3x=3e^{-6x}$ (Ex 8.20(c)).

## Related
- Topics: [[MATH1054 M07 - Functions]] · [[MATH1054 M22 - Complex Numbers II]]
- Concepts: [[Inverse Trigonometric Functions]] · [[Euler's Formula]] · [[Integration by Substitution]]

## Sources
- James, Modern Engineering Mathematics (6th ed.) §2.7.4–2.7.5, §8.3.12
- MATH1054 Module Booklet, Module 7
