---
title: "MATH1054 M08 - Differentiation II"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: topic
stream: "Block 1: Calculus"
order: 8
tags:
  - math1054
  - differentiation
  - curve-sketching
  - optimisation
  - maclaurin-series
aliases: ["MATH1054 Module 8", "Differentiation II"]
date: 2026-09-27
status: complete
parent: ["[[MATH1054 Mathematics for Engineering and the Environment Hub]]"]
prerequisites: ["[[MATH1054 M03 - Differentiation I]]", "[[MATH1054 M07 - Functions]]"]
next_topics: ["[[MATH1054 M20 - Further Calculus II]]"]
key_concepts: ["[[Implicit and Parametric Differentiation]]", "[[Logarithmic Differentiation]]", "[[Stationary Points and Inflection]]", "[[Taylor and Maclaurin Series]]"]
tutorial_sheets: ["[[MATH1054 M08 Solutions - Differentiation II]]"]
sources: ["02 - Sources/Course Booklets & Solutions/Module Booklet.pdf (Module 8)", "02 - Sources/Modern Engineering Mathematics.pdf (§2.5, §8.3.14, §8.4–8.5, §9.4)"]
---

# MATH1054 M08 - Differentiation II

> [!abstract] Summary
> Techniques for curves that are not given in the form $y=f(x)$:
> - **parametric** curves: $x(t)$, $y(t)$;
> - **implicit** curves: $F(x,y)=0$;
> - awkward products and powers, handled by **logarithmic differentiation**.
>
> Then the payoff: **stationary points and inflections** for curve sketching and optimisation, and the **Maclaurin series**, which rebuilds a function from its derivatives at 0.

## Key Concepts
- [[Implicit and Parametric Differentiation]] · [[Logarithmic Differentiation]] · [[Stationary Points and Inflection]] · [[Taylor and Maclaurin Series]]

---

## 1. Parametric differentiation (James §8.3.14, 8.4)

$$
\frac{\mathrm dy}{\mathrm dx}=\frac{\dot y}{\dot x},\qquad\frac{\mathrm d^2y}{\mathrm dx^2}=\frac{\frac{\mathrm d}{\mathrm dt}\Big(\frac{\mathrm dy}{\mathrm dx}\Big)}{\dot x}\ \ \Big(\neq\frac{\ddot y}{\ddot x}\Big)
$$

Cycloid: $x=a(\theta-\sin\theta)$, $y=a(1-\cos\theta)$ gives $y'=\cot\frac\theta2$ and $y''=-\dfrac{1}{a(1-\cos\theta)^2}$.

## 2. Implicit differentiation
Differentiate every term with respect to $x$, treating $y=y(x)$. Chain-rule each $y$ term:
- $\dfrac{\mathrm d}{\mathrm dx}y^n=ny^{n-1}y'$
- $\dfrac{\mathrm d}{\mathrm dx}(xy)=y+xy'$

Then collect the $y'$ terms and solve for $y'$. A useful shortcut is

$$
y'=-\frac{F_x}{F_y}
$$

using the partial derivatives from [[MATH1054 M03 - Differentiation I|M03]]. For $y''$, differentiate $y'$ again, substitute $y'$, and simplify **using the curve's own equation**. For the circle in Ex 8.29(b), this collapses $y''$ to $-25/(y+2)^3$.

## 3. Logarithmic differentiation (James §8.3.14)
Use it when:
- the variable is in **both the base and the exponent**: $(\sin x)^x$, $(\ln x)^x$, $a^x$;
- there are long **products and quotients of powers**: $\dfrac{(x-2)^3(x+3)^9}{\sqrt{x^2+1}}$.

$$
\ln y=\sum\ln(\text{factors})\ \Rightarrow\ \frac{y'}y=\sum\frac{(\text{factor})'}{\text{factor}}\ \Rightarrow\ y'=y\times(\cdots)
$$

## 4. Curve sketching (James §2.5, 8.5)
1. Domain and symmetry (even or odd?).
2. Intercepts, by factorising.
3. Asymptotes:
   - **vertical** where the denominator is zero;
   - **horizontal or oblique** from polynomial division, e.g. $\frac{x^2-x-6}{x+1}=x-2-\frac4{x+1}$.
4. Stationary points ($f'=0$) and their nature.
5. Inflections ($f''=0$ **and** changes sign).
6. End behaviour and which side of each asymptote the curve lies on.

![[m1054_curve_sketches_rational.png|800]]

### Nature of stationary points
| Test | Max | Min | Inconclusive |
|---|---|---|---|
| second derivative | $f''<0$ | $f''>0$ | $f''=0$: use the sign-change test |
| sign of $f'$ either side | $+\to-$ | $-\to+$ | same sign on both sides gives a stationary inflection |

![[m1054_curve_sketches_stationary.png|800]]

> [!warning] Inequalities with rational functions
> Never multiply both sides by an expression of unknown sign. Split into cases (Ex 2.36: $x<3$ and $x>3$), or read the answer off the sketch.

## 5. Optimisation (James §8.5)
Build the model $C(q)$, set $C'=0$, then check that it is a minimum. The three textbook examples:
- **Economic lot size**: $q^*=\sqrt{2c_1N/c_3}$.
- **Milk carton**: $81.8\times81.8\times169.7$ mm.
- **Car replacement**: minimise the *average cost per year*, not the total; the answer is about 5.4 years.

When the optimality condition is transcendental, solve it numerically, e.g. with [[Direct Substitution and Newton-Raphson|Newton–Raphson]].

## 6. Maclaurin series (James §9.4)

$$
f(x)=f(0)+f'(0)x+\frac{f''(0)}{2!}x^2+\frac{f'''(0)}{3!}x^3+\cdots=\sum_{n=0}^\infty\frac{f^{(n)}(0)}{n!}x^n
$$

| $f$ | series |
|---|---|
| $e^x$ | $1+x+\frac{x^2}{2!}+\frac{x^3}{3!}+\cdots$ |
| $\sin x$ | $x-\frac{x^3}{3!}+\frac{x^5}{5!}-\cdots$ |
| $\cos x$ | $1-\frac{x^2}{2!}+\frac{x^4}{4!}-\cdots$ |

**Shortcut**: products of known series can simply be multiplied. For example, $(1+x)\sin x=x+x^2-\frac{x^3}6-\frac{x^4}6+\cdots$. Convergence and the remainder term follow in [[MATH1054 M20 - Further Calculus II|M20]].

## Links
- Parent: [[MATH1054 Mathematics for Engineering and the Environment Hub]] · Solutions: [[MATH1054 M08 Solutions - Differentiation II]]
- Prev: [[MATH1054 M07 - Functions]] · Next: [[MATH1054 M20 - Further Calculus II]] (sequences, series, the remainder, L'Hôpital)

## Sources
- MATH1054 Module Booklet, Module 8; James §2.5, §8.3.14–8.5, §9.4
