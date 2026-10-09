---
title: "L'Hôpital's Rule"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 5: Series and Statistics"
aliases: ["L'Hopital's rule", "Indeterminate forms"]
tags: [math1054, concept, limits]
status: complete
parent_lectures: ["[[MATH1054 M20 - Further Calculus II]]"]
related_concepts: ["[[Taylor and Maclaurin Series]]", "[[Derivative from First Principles]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §9.4", "MATH1054 Module Booklet, Module 20"]
---

# L'Hôpital's Rule

## Definition

> [!note] Definition
> If $\frac{f(x)}{g(x)}\to\frac00$ (or $\frac\infty\infty$) as $x\to a$, then
> $$\lim_{x\to a}\frac{f(x)}{g(x)}=\lim_{x\to a}\frac{f'(x)}{g'(x)}$$
> provided the right-hand limit exists.

## Explanation
- Repeat it while the form stays indeterminate.
- **Stop** as soon as it is not. Applying it to a determinate form gives wrong answers.
- **Cross-check with series**: $\sin x-x=-\frac{x^3}6+\cdots$, so $\frac{\sin x-x}{x^3}\to-\frac16$.

## Examples
- $\lim_{x\to0}\frac{x\cos x-\sin x}{x^3}=-\frac13$ (Ex 19(e)).
- $\lim_{x\to\pi}\frac{\sin3x}{\sin2x}=-\frac32$ (Ex 19(c)).

## Related
- Topics: [[MATH1054 M20 - Further Calculus II]]
- Concepts: [[Taylor and Maclaurin Series]] · [[Derivative from First Principles]]

## Sources
- James, Modern Engineering Mathematics (6th ed.) §9.4
- MATH1054 Module Booklet, Module 20
