---
title: "Stationary Points and Inflection"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 1: Calculus"
aliases: ["Stationary point", "Turning point", "Point of inflection", "Maxima and minima"]
tags: [math1054, concept, curve-sketching]
status: complete
parent_lectures: ["[[MATH1054 M08 - Differentiation II]]"]
related_concepts: ["[[Implicit and Parametric Differentiation]]", "[[Taylor and Maclaurin Series]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §2.5, §8.5", "MATH1054 Module Booklet, Module 8"]
---

# Stationary Points and Inflection

## Definition

> [!note] Definition
> - A **stationary point** is where $f'(x_0)=0$. It is a local **max** if $f''(x_0)<0$ and a local **min** if $f''(x_0)>0$.
> - A **point of inflection** is where $f''$ changes sign. At a stationary inflection, $f'=0$ as well.

## Explanation
- If $f''(x_0)=0$, the second-derivative test fails. Use the **sign of $f'$ on either side** instead: $+\to-$ is a max, $-\to+$ is a min, and the same sign on both sides is an inflection. For example, $x^4$ has $f''(0)=0$ but a minimum at 0.
- **Optimisation**: model the quantity, set $C'=0$, check the nature, and compare with the endpoint values.
- **Curve-sketching checklist**:
  1. domain and symmetry;
  2. intercepts;
  3. asymptotes (vertical, horizontal or oblique by polynomial division);
  4. stationary points;
  5. inflections;
  6. end behaviour.

## Examples
- $4x^3-21x^2+18x+6$: a max at $(\frac12,\frac{41}4)$ and a min at $(3,-21)$ (Ex 8.31).
- $x^2e^{-x}$: a min at $(0,0)$, a max at $(2,4e^{-2})$, and inflections at $2\pm\sqrt2$ (Ex 80(c)).
- Economic lot size $q^*=\sqrt{2c_1N/c_3}$; car replacement at about 5.4 years (Ex 8.34, 8.36).

## Related
- Topics: [[MATH1054 M08 - Differentiation II]]
- Concepts: [[Implicit and Parametric Differentiation]] · [[Taylor and Maclaurin Series]]

## Sources
- James, Modern Engineering Mathematics (6th ed.) §2.5, §8.5
- MATH1054 Module Booklet, Module 8
