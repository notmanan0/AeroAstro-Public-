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

A stationary point of $f$ is a point $x_0$ where $f'(x_0)=0$, so the tangent is horizontal; it is a local maximum, a local minimum or a stationary point of inflection. A point of inflection is a point where the concavity changes, that is, where $f''$ changes sign.

The nature of a stationary point follows from the sign of $f'$ on either side: $+\to-$ is a maximum, $-\to+$ a minimum, and the same sign on both sides a stationary inflection. The second-derivative test is a shortcut for the same thing. Since $f'(x_0)=0$, the definition of the derivative gives $f''(x_0)=\lim_{h\to0}f'(x_0+h)/h$; if $f''(x_0)<0$ then $f'(x_0+h)$ has the opposite sign to $h$ for small $h$, which is the pattern $+\to-$, a maximum. Likewise $f''(x_0)>0$ gives a minimum.

If $f''(x_0)=0$ the test fails, and anything can happen: $x^3$ has a stationary inflection at 0, $x^4$ a minimum and $-x^4$ a maximum, all with $f'(0)=f''(0)=0$. Fall back on the sign of $f'$, or on Taylor's theorem: if the first non-zero derivative at $x_0$ is $f^{(n)}$, then $f(x_0+h)-f(x_0)\approx\frac{h^n}{n!}f^{(n)}(x_0)$, which gives an extremum for even $n$ and a stationary inflection for odd $n$. So a stationary point of inflection needs $f'(x_0)=0$, $f''(x_0)=0$ and a sign change of $f''$; $f'''(x_0)\neq0$ is sufficient for the last. An inflection need not be stationary at all.

![[m1054_m08_stationary_cases.png|900]]

Stationary points are the core of curve sketching (with symmetry, intercepts by the factor theorem, vertical asymptotes at zeros of a denominator, horizontal or oblique asymptotes by polynomial division, and the behaviour as $x\to\pm\infty$) and of optimisation (model the quantity as a function of one variable, set its derivative to zero, check the nature and compare with end points and with points where $f'$ does not exist, such as the minimum of $x^{2/3}$ at 0).

Worked examples:

- $4x^3-21x^2+18x+6$: $f'=6(2x-1)(x-3)$, a maximum at $(\frac12,\frac{41}4)$ ($f''=-30$) and a minimum at $(3,-21)$ ($f''=30$), with a non-stationary inflection at $(\frac74,-\frac{43}8)$ (Examples 8.30–8.31).
- $x^2e^{-x}$: $f'=x(2-x)e^{-x}$, a minimum at $(0,0)$, a maximum at $(2,4e^{-2})$, and inflections at $2\pm\sqrt2$ (Exercise 80(c)).
- Economic lot size $q^*=\sqrt{2c_1N/c_3}$; the car-replacement average annual cost is least at $t=5.43$ years, about 5.4 years (Examples 8.34 and 8.36).

The common trap is to call every point with $f''=0$ an inflection: $x^4$ has $f''(0)=0$ and a minimum at 0, because $f''=12x^2$ does not change sign.

## Related

- Topics: [[MATH1054 M08 - Differentiation II]] (derivations, sketches and optimisation examples)
- Concepts: [[Implicit and Parametric Differentiation]] · [[Taylor and Maclaurin Series]] · [[Even, Odd and Periodic Functions]] · [[Direct Substitution and Newton-Raphson]]
- Sources: James, *Modern Engineering Mathematics* (6th ed.) §2.5, §8.5; MATH1054 Module Booklet, Module 8
