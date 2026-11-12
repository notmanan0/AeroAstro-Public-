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

The trapezium and Simpson rules estimate $\int_a^bf(x)\,\mathrm dx$ from the ordinates $f_r=f(a+rh)$ at $n$ equal strips of width $h=\frac{b-a}n$, replacing the curve by straight chords (trapezium) or by parabolas through successive triples of points (Simpson, $n$ even).

$$
T(h)=h\Big[\tfrac12(f_0+f_n)+\sum_{r=1}^{n-1}f_r\Big],\qquad S=\frac h3\Big[f_0+f_n+4\sum_{\text{odd }r}f_r+2\sum_{\substack{\text{even }r\\0<r<n}}f_r\Big].
$$

The trapezium rule adds the strip areas $\frac12(f_r+f_{r+1})h$, so each interior ordinate, shared by two strips, gets weight $h$. Simpson's rule integrates the parabola through three points over a double strip, which gives $\frac h3(f_0+4f_1+f_2)$; adding the pairs gives the weights 1, 4, 2, 4, …, 4, 1. A Taylor expansion about the middle of each strip shows that the trapezium error is $T(h)-I\approx\frac{h^2}{12}[f'(b)-f'(a)]$ and Simpson's is $S-I\approx\frac{h^4}{180}[f'''(b)-f'''(a)]$, so halving $h$ cuts them by factors of about 4 and 16. Both derivations are in [[MATH1054 M04 - Integration I#7. The trapezium rule (James §8.10.1)|M04 §7–8]].

The $h^2$ law makes the trapezium rule self-checking. Halving the strip width reuses every old point, $T(h)=h\sum f_{\text{new}}+\frac12T(2h)$, and the two values give an error estimate, $T(h)-I\approx\frac13[T(2h)-T(h)]$, without knowing $I$. Subtracting that error gives the Richardson extrapolation $\frac13[4T(h)-T(2h)]$, and collecting its terms reproduces Simpson's rule exactly: Simpson's rule is extrapolated trapezium.

For $\int_1^2\frac{\mathrm dx}x=\ln2=0.693147$ (James Example 8.72), $T(0.25)=0.697024$ and $T(0.125)=0.694122$. The estimated error in $T(0.125)$ is $\frac13(0.697024-0.694122)=0.000967$, against a true error of $0.000975$, and the extrapolated value $0.694122-0.000967=0.69315$ is correct to 5 d.p.; the plain trapezium rule needs 128 strips to reach the same accuracy. For $\int_0^1\sqrt{1+x^3}\,\mathrm dx$, which has no elementary antiderivative, $h=0.1$ gives $S=1.111446$ and $T=1.112332$ (Exercise 142 and Booklet Exercise C), against the accurate value $1.111448$. With tabulated data the rules are the only option: Simpson's rule with 10 strips gives $7.3\times10^4$ m³ for the earth removed in a road cutting (James Example 8.74).

The common trap is applying Simpson's rule with an odd number of strips, or swapping the weights so that the even ordinates get 4. The first and last ordinates have weight 1, the odd-numbered ones 4 and the interior even-numbered ones 2. Both error laws also assume a smooth integrand: for $\sqrt x$ near $x=0$, where $f'$ is infinite, convergence is much slower than $h^2$.

![[m1054_trapezium_vs_simpson.png|900]]

## Related

- Topics: [[MATH1054 M04 - Integration I]] (derivations, error analysis and all set examples, §7–8)
- Concepts: [[Truncation Error and Order of Accuracy]] · [[Improper Integrals]]
- Sources: James, *Modern Engineering Mathematics* (6th ed.) §8.10.1–8.10.2 (formulae 8.47–8.49, Examples 8.72 and 8.74, Exercise 142); MATH1054 Module Booklet, Module 4 (work scheme items 9–10, Exercise C, Specimen Test 4 Q4); worked solutions in [[MATH1054 M04 Solutions - Integration I]].
