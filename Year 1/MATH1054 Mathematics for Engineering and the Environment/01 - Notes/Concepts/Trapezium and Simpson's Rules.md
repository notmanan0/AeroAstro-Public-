---
title: "Trapezium and Simpson's Rules"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 1: Calculus"
aliases: ["Trapezium rule", "Trapezoidal rule", "Simpson's rule", "Numerical integration"]
tags: [math1054, concept, numerical-integration]
status: complete
parent_lectures: ["[[MATH1054 M04 - Integration I]]"]
related_concepts: ["[[Truncation Error and Order of Accuracy]]", "[[Improper Integrals]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §8.10", "MATH1054 Module Booklet, Module 4"]
---

# Trapezium and Simpson's Rules

## Definition

> [!note] Definition
> With $n$ strips of width $h$ and ordinates $f_r$:
> $$T=h\Big[\tfrac12(f_0+f_n)+\sum_{r=1}^{n-1}f_r\Big],\qquad S=\frac h3\Big[f_0+f_n+4\!\!\sum_{\text{odd }r}\!\!f_r+2\!\!\sum_{\text{even }r}\!\!f_r\Big]\ (n\text{ even})$$

## Explanation
- **Errors**: the trapezium error is $\propto h^2$ (straight-line tops); Simpson's error is $\propto h^4$ (parabolic tops).
- **Interval halving**: $T(h)=h\sum f_{\text{new}}+\tfrac12T(2h)$ reuses the old ordinates.
- **Error estimate**: $T(h)-I\approx\tfrac13[T(2h)-T(h)]$.
- **Richardson extrapolation**: $\tfrac13[4T(h)-T(2h)]$ **is** Simpson's rule.
- **When to use them**: when there is no closed form, or when only tabulated data exist (e.g. surveying volumes).

## Examples
- $\int_1^2\frac{\mathrm dx}x$: $T(0.125)=0.694122$. After extrapolation, $0.69315=\ln2$ (Ex 8.72).
- Road cutting: Simpson with 10 strips gives $7.3\times10^4$ m³ (Ex 8.74).
- $\int_0^1\sqrt{1+x^3}\,\mathrm dx$: $S=1.111446$ and $T=1.112332$ (Ex 142, Booklet Ex C).

## Related
- Topics: [[MATH1054 M04 - Integration I]]
- Concepts: [[Truncation Error and Order of Accuracy]] · [[Improper Integrals]]

## Sources
- James, Modern Engineering Mathematics (6th ed.) §8.10
- MATH1054 Module Booklet, Module 4
