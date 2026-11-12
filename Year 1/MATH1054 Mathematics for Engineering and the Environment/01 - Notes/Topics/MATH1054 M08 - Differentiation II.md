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
status: lectured
coverage: "Module Booklet Module 8 work scheme: stationary points and their nature, curve sketching with asymptotes and the factor theorem, optimisation (read only), parametric, implicit and logarithmic differentiation, second derivatives of parametric and implicit curves, Taylor and Maclaurin series; James §2.5.3, §8.3.14, §8.4.1, §8.5.1, §9.4.2"
parent: ["[[MATH1054 Mathematics for Engineering and the Environment Hub]]"]
prerequisites: ["[[MATH1054 M03 - Differentiation I]]", "[[MATH1054 M07 - Functions]]"]
next_topics: ["[[MATH1054 M20 - Further Calculus II]]"]
key_concepts: ["[[Implicit and Parametric Differentiation]]", "[[Logarithmic Differentiation]]", "[[Stationary Points and Inflection]]", "[[Taylor and Maclaurin Series]]"]
tutorial_sheets: ["[[MATH1054 M08 Solutions - Differentiation II]]"]
sources: ["02 - Sources/Course Booklets & Solutions/Module Booklet.pdf (Module 8)", "02 - Sources/Modern Engineering Mathematics.pdf (§2.5, §8.3.14, §8.4–8.5, §9.4)"]
---

# MATH1054 M08 - Differentiation II

> [!abstract] Summary
> The derivative is put to work on the shape of a curve: stationary points where $f'=0$, classified by the sign of $f'$ either side or by the sign of $f''$, inflections where $f''$ changes sign, and asymptotes, which together give a sketch or an optimum. Curves that are not written as $y=f(x)$ are differentiated with the chain rule: parametrically, $\frac{dy}{dx}=\dot y/\dot x$ and $\frac{d^2y}{dx^2}=\frac{d}{dt}\big(\frac{dy}{dx}\big)\big/\dot x$; implicitly, by differentiating every term with $y=y(x)$; and logarithmically, by differentiating $\ln y$. Repeated differentiation at one point rebuilds a function as its Maclaurin or Taylor series, with coefficients $f^{(n)}(a)/n!$.

> [!summary]- Exam use: quick path
> - **Use it when:** a question asks for stationary points and their nature, a sketch, the slope or tangent of a curve given parametrically or by an equation $F(x,y)=0$, the derivative of a variable power such as $(\sin x)^x$, or the first few terms of a Maclaurin series.
> - **Assumptions:** $f$ is differentiable where the tests are used (check points where $f'$ does not exist and the ends of the domain separately); $\dot x\neq0$ for parametric slopes; $y>0$ (or use $\ln|y|$) for logarithmic differentiation; angles in radians.
> - **Method:** 1. Differentiate, using the chain rule on every $y$ or $t$ dependence. 2. Solve $f'=0$, or rearrange for $y'$. 3. Classify with $f''$; if $f''=0$, use the sign of $f'$ either side. 4. For a sketch add intercepts (factor theorem), asymptotes and the behaviour as $x\to\pm\infty$. 5. For a series, tabulate $f^{(n)}(0)$ and divide by $n!$, or multiply known series.
> - **Common mistakes:** writing $\frac{d^2y}{dx^2}=\ddot y/\ddot x$; taking $f''(a)=0$ as proof of an inflection ($x^4$ has a minimum there).
> - **Practise:** [[#Parametric second derivative (Example 8.29(a))]] · [[MATH1054 M08 Solutions - Differentiation II#Part C: Specimen Test 8|Specimen Test 8]]

Where $f'=0$ the tangent to a graph is horizontal, and the sign of $f'$ either side, or the sign of $f''$ at the point, decides whether the point is a maximum, a minimum or a stationary inflection. Add the zeros of the function and its asymptotes and the graph can be sketched by hand. The same calculation finds the best design or the cheapest policy in an optimisation problem, once the cost or the material has been written as a function of one variable. Everything here runs on the product, quotient and chain rules of [[MATH1054 M03 - Differentiation I|Module 3]].

Many engineering curves are not given as $y=f(x)$. A trajectory or a point on a rolling wheel comes as a pair $x(t)$, $y(t)$; a conic, or a relation such as $y^4+\sin xy=0$, links $x$ and $y$ by an equation that cannot be solved for $y$. In both cases the chain rule still gives $dy/dx$, and a second application gives $d^2y/dx^2$, the quantity that decides concavity. Logarithmic differentiation is the same idea applied to $\ln y$, and turns a variable power or a long product into a sum.

Repeated differentiation also runs the other way: the values $f(0),f'(0),f''(0),\dots$ determine the coefficients of a power series for $f$. That series is how $\sin x$ is evaluated numerically, how small-angle approximations such as $\sin\theta\approx\theta$ are justified, and the starting point for the remainder estimates, sequences and series of [[MATH1054 M20 - Further Calculus II|Module 20]], the finite-difference error analysis of [[Truncation Error and Order of Accuracy|SESA2029]] and the Fourier series of [[MATH2048 FS1 - Fourier Series, Orthogonality and the Euler Formulae|MATH2048]].

---

## 1. Stationary points and their nature (James §8.5.1)

A point $x=a$ is a **stationary point** (also called a critical point) of a differentiable function $f$ when

$$
f'(a)=0,
$$

so the tangent there is horizontal. A stationary point is a local maximum, a local minimum or a stationary point of inflection. These are local statements: the largest or smallest value of $f$ on a domain may instead sit at an end point of the domain or at a point where $f'$ does not exist, so those are checked separately when the global optimum is wanted. The function $f(x)=x^{2/3}$ has its minimum at $x=0$, where $f'(x)=\frac23x^{-1/3}$ is undefined.

### The first-derivative (sign-change) test

Moving left to right through a stationary point $a$:

- if $f'$ changes from positive to negative, $f$ rises then falls, so $a$ is a local maximum;
- if $f'$ changes from negative to positive, $f$ falls then rises, so $a$ is a local minimum;
- if $f'$ has the same sign on both sides, $f$ keeps rising (or keeps falling) and $a$ is a stationary point of inflection.

The test needs only the sign of $f'$ near $a$, which comes straight from a factorised $f'$. It gives an answer whenever $f'$ keeps one sign on each side of $a$ (always so when $f'$ is a non-zero polynomial, which has finitely many zeros), which is why it is the fallback when the second-derivative test fails.

### The second-derivative test, derived

Suppose $f'(a)=0$ and $f''(a)$ exists. By the definition of the derivative applied to $f'$,

$$
f''(a)=\lim_{h\to0}\frac{f'(a+h)-f'(a)}{h}.
$$

With $f'(a)=0$ this reads

$$
f''(a)=\lim_{h\to0}\frac{f'(a+h)}{h}.
$$

If $f''(a)<0$, the quotient $f'(a+h)/h$ is negative for all small enough $|h|$, so

$$
f'(a+h)<0\ \text{for small } h>0,\qquad f'(a+h)>0\ \text{for small } h<0 .
$$

That is the sign pattern $+\to-$, so $a$ is a local maximum. The same argument with $f''(a)>0$ gives $-\to+$ and a local minimum. In summary,

$$
f'(a)=0,\ f''(a)<0\ \Rightarrow\ \text{local maximum};\qquad f'(a)=0,\ f''(a)>0\ \Rightarrow\ \text{local minimum}.
$$

Geometrically, $f''<0$ means the slope is decreasing, so the curve is concave down (bends below its tangent), and $f''>0$ means concave up.

If $f''(a)=0$ the limit above gives no sign, and the test says nothing. All three outcomes are possible:

| $f$ | $f'(0)$ | $f''(0)$ | sign of $f'$ through 0 | nature at 0 |
|---|---|---|---|---|
| $x^3$ | 0 | 0 | $+\to+$ | stationary inflection |
| $x^4$ | 0 | 0 | $-\to+$ | minimum |
| $-x^4$ | 0 | 0 | $+\to-$ | maximum |

![[m1054_m08_stationary_cases.png|900]]

| Test | Max | Min | Inconclusive |
|---|---|---|---|
| second derivative | $f''<0$ | $f''>0$ | $f''=0$: use the sign-change test |
| sign of $f'$ either side | $+\to-$ | $-\to+$ | same sign on both sides gives a stationary inflection |

Taylor's theorem sharpens this into a higher-derivative test: [[#Stationary points revisited with Taylor's theorem]].

### Points of inflection

A **point of inflection** is a point where the concavity changes, so the curve crosses its own tangent there. Since concavity is the sign of $f''$, at an inflection $f''$ changes sign, and if $f''$ is continuous that forces $f''=0$. Two consequences follow. An inflection need not be stationary: $f'$ can take any value there (a non-stationary inflection). And $f''(a)=0$ alone does not make $a$ an inflection, because $f''$ must also change sign; $x^4$ has $f''(0)=0$ and $f''=12x^2\geq0$ on both sides.

A **stationary point of inflection** therefore needs three things at $x_0$:

$$
f'(x_0)=0,\qquad f''(x_0)=0,\qquad f''\ \text{changes sign through } x_0 .
$$

The last condition is equivalent to $f'$ having the same sign on both sides of $x_0$, and a sufficient condition for it is $f'''(x_0)\neq0$.

### A cubic (Examples 8.30 and 8.31)

Take $f(x)=4x^3-21x^2+18x+6$.

$$
\begin{aligned}
f'(x)&=12x^2-42x+18\\
&=6(2x^2-7x+3)\\
&=6(2x-1)(x-3),
\end{aligned}
$$

which vanishes at $x=\tfrac12$ and $x=3$. The function values are

$$
f\big(\tfrac12\big)=\tfrac12-\tfrac{21}4+9+6=\tfrac{41}4=10.25,\qquad f(3)=108-189+54+6=-21 .
$$

Sign test (Example 8.30): just left of $\tfrac12$ both factors $2x-1$ and $x-3$ are negative, so $f'>0$; just right of $\tfrac12$, $2x-1>0$ and $x-3<0$, so $f'<0$. The pattern $+\to-$ makes $\big(\tfrac12,\tfrac{41}4\big)$ a local maximum. Through $x=3$, $x-3$ changes from negative to positive while $2x-1>0$, so $f'$ goes $-\to+$ and $(3,-21)$ is a local minimum.

Second-derivative test (Example 8.31): $f''(x)=24x-42$, so

| $x$ | $f''$ | nature | $f$ |
|---|---|---|---|
| $\tfrac12$ | $-30<0$ | local maximum | $\tfrac{41}4=10.25$ |
| $3$ | $+30>0$ | local minimum | $-21$ |

Also $f''=0$ at $x=\tfrac74$, with $f''<0$ to the left and $f''>0$ to the right, so $\big(\tfrac74,-\tfrac{43}8\big)$ is a point of inflection. It is not stationary, since $f'\big(\tfrac74\big)=6\cdot\tfrac52\cdot\big(-\tfrac54\big)=-\tfrac{75}4\neq0$.

### Specimen Test 8, Q1 and Q2

Q1: $x_0$ is a stationary point when $f'(x_0)=0$; it is a stationary inflection when, in addition, $f''(x_0)=0$ and $f''$ changes sign through $x_0$ (equivalently, $f'$ has the same sign on both sides).

Q2: the stationary points of three functions and their nature.

1. $f=x-x^2$: $f'=1-2x=0$ at $x=\tfrac12$; $f''=-2<0$, so a maximum with $f=\tfrac14$.
2. $f=x+e^x$: $f'=1+e^x>0$ for every $x$, so there are no stationary points.
3. $f=x^3-3x+3$: $f'=3(x^2-1)=0$ at $x=\pm1$ and $f''=6x$. At $x=-1$, $f''=-6<0$, a maximum with $f=5$; at $x=1$, $f''=6>0$, a minimum with $f=1$.

## 2. Optimisation (James §8.5)

An optimisation problem is a stationary-point problem with a model in front of it. Write the quantity to be minimised or maximised as a function of one variable (using any constraint to eliminate the others), set its derivative to zero and confirm the nature of the root. When the model has only one sensible root and the physical problem clearly has an optimum, that root is the optimum. Examples 8.34 to 8.36 are read-only (Module 8 work scheme, item 1).

### Economic lot size (Example 8.34)

A manufacturer supplies $N$ items a month at a uniform rate. Each production run costs $c_1$ to set up plus $c_2$ per item, and stored items cost $c_3$ each per month. The run size $q$ that minimises the monthly cost is wanted.

A run of $q$ items costs $c_1+c_2q$ and lasts $q/N$ months, so the monthly production cost is

$$
\frac{c_1+c_2q}{q/N}=\frac{c_1N}{q}+c_2N .
$$

Stock falls uniformly from $q$ to 0 during a run, so the average stock is $\tfrac12q$ and the monthly storage cost is $\tfrac12c_3q$. The total monthly cost is

$$
C(q)=\frac{c_1N}{q}+c_2N+\tfrac12c_3q .
$$

Differentiate and set to zero:

$$
\begin{aligned}
C'(q)&=-\frac{c_1N}{q^2}+\tfrac12c_3=0\\
q^2&=\frac{2c_1N}{c_3}\\
q^*&=\sqrt{\frac{2c_1N}{c_3}} .
\end{aligned}
$$

Since $C''(q)=2c_1N/q^3>0$ for $q>0$, this is a minimum. The value $q^*$ is the **economic lot size**.

### Milk carton (Example 8.35)

A carton of square cross-section $b\times b$ and height $h$ (mm) must hold two pints, $1.136$ litres $=1\,136\,000$ mm³. It is folded from a rectangular sheet: the width is four faces plus a 5 mm seam, $4b+5$, and the length is $h$ plus a flap of $\tfrac12b+5$ at the top and at the bottom, $h+b+10$. So

$$
A=(4b+5)(h+b+10),\qquad b^2h=1\,136\,000 .
$$

Eliminate $h$ with the constraint:

$$
A(b)=(4b+5)\left(\frac{1\,136\,000}{b^2}+b+10\right).
$$

By the product rule,

$$
\begin{aligned}
A'(b)&=4\left(\frac{1\,136\,000}{b^2}+b+10\right)+(4b+5)\left(1-\frac{2\,272\,000}{b^3}\right)\\
&=\frac{4\,544\,000}{b^2}+4b+40+4b+5-\frac{9\,088\,000}{b^2}-\frac{11\,360\,000}{b^3}\\
&=8b+45-\frac{4\,544\,000}{b^2}-\frac{11\,360\,000}{b^3}.
\end{aligned}
$$

Setting $A'(b)=0$ and multiplying by $b^3$ gives the quartic

$$
8b^4+45b^3-4\,544\,000\,b-11\,360\,000=0,
$$

whose positive root, found numerically, is $b=81.82$ mm. Then $h=1\,136\,000/b^2=169.70$ mm, and $A''(b)=25.4>0$ confirms a minimum:

$$
81.8\times81.8\times169.7\ \text{mm},\qquad A_{\min}\approx8.69\times10^4\ \text{mm}^2 .
$$

### Replacing a car (Example 8.36)

A car bought for £14 750 has second-hand value $e^{9.55-0.11t}$ pounds after $t$ years, and its running cost in year $r+1$ is $917+163r$ pounds. The quantity to minimise is the average cost per year, not the total, because the total always grows with $t$.

The running cost accumulated over $t$ years is an arithmetic series ([[Arithmetic and Geometric Series]]):

$$
\begin{aligned}
\sum_{r=0}^{t-1}(917+163r)&=917t+163\cdot\frac{(t-1)t}{2}\\
&=917t+81.5t^2-81.5t\\
&=(835.5+81.5t)\,t .
\end{aligned}
$$

Adding the depreciation $14\,750-e^{9.55-0.11t}$ and dividing by $t$ gives the average annual cost

$$
C(t)=\frac{14\,750-e^{9.55-0.11t}}{t}+835.5+81.5t .
$$

Write $E=e^{9.55-0.11t}$, so $E'=-0.11E$. By the quotient rule,

$$
\begin{aligned}
C'(t)&=\frac{0.11E\,t-(14\,750-E)}{t^2}+81.5=0\\
0.11Et-14\,750+E+81.5t^2&=0\\
e^{9.55-0.11t}(1+0.11t)+81.5t^2&=14\,750 .
\end{aligned}
$$

This is transcendental, so it is solved numerically: $t^*=5.43$ years, where $C=£2571$ per year. Replace the car after about 5.4 years, or $5\tfrac12$ years in round terms.

If the running cost is instead accumulated continuously, $\int_0^t(917+163\tau)\,d\tau=917t+81.5t^2$, then $C(t)$ gains the constant $917-835.5=81.5$. A constant does not change $C'$, so $t^*=5.43$ years is unchanged and the minimum average cost becomes £2653 per year.

> [!check] Solving the optimality condition by Newton–Raphson
> With $g(t)=e^{9.55-0.11t}(1+0.11t)+81.5t^2-14\,750$, differentiating gives $g'(t)=-0.0121\,t\,e^{9.55-0.11t}+163t$. [[Direct Substitution and Newton-Raphson|Newton–Raphson]], $t_{n+1}=t_n-g(t_n)/g'(t_n)$, from $t_0=5$ gives $5.4702,\ 5.4352,\ 5.43497,\ 5.43497$. The minimum is flat: $C(5)=2572.4$ and $C(6)=2573.0$ against $C(5.43)=2571.1$ (or $2653.9$, $2654.5$ and $2652.6$ with continuous running costs), so any age from 5 to 6 years costs within £2 a year of the optimum.

![[m1054_m08_optimisation.png|900]]

## 3. Curve sketching (James §2.5.3)

A sketch shows the major properties of a graph, each found by calculation. For $y=f(x)$:

1. look for a general property: even ($f(-x)=f(x)$), odd ($f(-x)=-f(x)$) or periodic (see [[Even, Odd and Periodic Functions]]);
2. find the stationary points and their nature (Section 1), and the inflections;
3. find the asymptotes and the behaviour of $f$ on both sides of each;
4. find $f(x)$ as $x\to\pm\infty$;
5. find where the graph meets the axes.

Each of these earns marks separately in an examination question, even when a calculator plot is available (Module 8 work scheme, item 3).

### Asymptotes of rational functions

A rational function $y=p(x)/q(x)$ usually has a **vertical asymptote** at each zero of the denominator $q$ that is not also a zero of $p$: as $x$ approaches such a point, $|y|\to\infty$. The sign of $y$ just left and just right of it comes from the factorised form.

The behaviour as $x\to\pm\infty$ comes from polynomial division, $p(x)=s(x)q(x)+r(x)$ with $\deg r<\deg q$, so that

$$
y=s(x)+\frac{r(x)}{q(x)},\qquad\frac{r(x)}{q(x)}\to0\ \text{as } x\to\pm\infty .
$$

The graph approaches $y=s(x)$: a **horizontal asymptote** if $s$ is a constant, an **oblique asymptote** if $s$ is linear. The sign of the remainder term $r/q$ for large positive and large negative $x$ says whether the curve approaches from above or below. [[Partial Fractions]] start with the same division.

### The factor theorem

If $f$ is a polynomial and $f(a)=0$, then $(x-a)$ is a factor: $f(x)=(x-a)g(x)$ with $g$ a polynomial of one lower degree. This finds the zeros of a cubic once one root has been spotted. For $f(x)=x^3-6x^2+11x-6$, $f(1)=1-6+11-6=0$, so

$$
x^3-6x^2+11x-6=(x-1)(x^2+bx+6),
$$

where the leading coefficient 1 and the constant 6 are fixed by inspection (the constant must give $(-1)(6)=-6$). Matching the $x^2$ coefficient, $b-1=-6$, gives $b=-5$, and

$$
x^3-6x^2+11x-6=(x-1)(x^2-5x+6)=(x-1)(x-2)(x-3).
$$

### A rectangular hyperbola and an inequality (Example 2.36)

$y=\dfrac1{3-x}$ has a vertical asymptote at $x=3$. As $x\to3^-$, $3-x\to0^+$ and $y\to+\infty$; as $x\to3^+$, $y\to-\infty$. As $x\to\pm\infty$, $y\to0$, so $y=0$ is a horizontal asymptote. The $y$-intercept is $\tfrac13$, and $y>0$ for $x<3$, $y<0$ for $x>3$.

To solve $\dfrac1{3-x}<2$, split by the sign of $3-x$.

For $x<3$, $3-x>0$, so multiplying by it keeps the direction of the inequality:

$$
\begin{aligned}
1&<2(3-x)\\
2x&<5\\
x&<\tfrac52 .
\end{aligned}
$$

For $x>3$, the left side is negative and so always less than 2: every $x>3$ works. The solution is

$$
x<\tfrac52\quad\text{or}\quad x>3,
$$

which is where the curve lies below the line $y=2$; they meet at $x=\frac52$.

> [!warning] Inequalities with rational functions
> Never multiply both sides of an inequality by an expression of unknown sign. Split into cases by the sign of the multiplier (here $x<3$ and $x>3$), or read the answer off the sketch.

### An oblique asymptote (Example 2.37)

$y=\dfrac{x^2-x-6}{x+1}$.

The zeros come from $x^2-x-6=(x-3)(x+2)=0$, so the graph crosses the $x$ axis at $x=3$ and $x=-2$; the $y$-intercept is $-6$. The denominator vanishes at $x=-1$, a vertical asymptote. Division gives

$$
x^2-x-6=(x+1)(x-2)-4\quad\Rightarrow\quad y=x-2-\frac4{x+1},
$$

so $y=x-2$ is an oblique asymptote. For large positive $x$, $-\frac4{x+1}<0$ and the curve approaches the asymptote from below; for large negative $x$ it approaches from above. In the factorised form $(x-3)(x+2)/(x+1)$, just left of $-1$ the signs are $(-)(+)/(-)$, so $y>0$ and $y\to+\infty$; just right they are $(-)(+)/(+)$, so $y\to-\infty$. Finally

$$
y'=1+\frac4{(x+1)^2}>0,
$$

so there are no turning points and each branch increases.

### Two rational functions (Exercise 44)

(a) $y=\dfrac{x^2-8x+15}{x}=x-8+\dfrac{15}x$. The zeros are $x=3$ and $x=5$; the asymptotes are $x=0$ and the oblique line $y=x-8$. Then

$$
y'=1-\frac{15}{x^2}=0\ \Rightarrow\ x=\pm\sqrt{15},\qquad y''=\frac{30}{x^3}.
$$

At $x=\sqrt{15}$, $y=2\sqrt{15}-8\approx-0.254$ and $y''>0$, a local minimum. At $x=-\sqrt{15}$, $y=-2\sqrt{15}-8\approx-15.75$ and $y''<0$, a local maximum. For $x>0$ the minimum also follows without calculus by completing the square,

$$
y=\Big(\sqrt x-\sqrt{15/x}\Big)^2+2\sqrt{15}-8\ \geq\ 2\sqrt{15}-8,
$$

with equality when $\sqrt x=\sqrt{15/x}$, that is $x=\sqrt{15}$.

(b) $y=\dfrac{x+1}{x-1}=1+\dfrac2{x-1}$. The asymptotes are $x=1$ and $y=1$, and the intercepts are $(-1,0)$ and $(0,-1)$. Since $y'=-\dfrac2{(x-1)^2}<0$, there are no turning points and both branches decrease: a rectangular hyperbola centred at $(1,1)$.

![[m1054_curve_sketches_rational.png|800]]

### A cubic and an exponential (Exercises 79(a) and 80(c))

79(a): $f(x)=2x^3-5x^2+4x-1$.

$$
f'(x)=6x^2-10x+4=2(3x-2)(x-1),\qquad f''(x)=12x-10 .
$$

At $x=\tfrac23$, $f''=-2<0$: a maximum with $f=\tfrac{16}{27}-\tfrac{20}9+\tfrac83-1=\tfrac1{27}$. At $x=1$, $f''=2>0$: a minimum with $f=0$. The inflection is at $f''=0$, $x=\tfrac56$, $f=\tfrac1{54}$, and $f''$ changes sign there. The factor theorem with $f(1)=0$ gives $f=(x-1)^2(2x-1)$: the curve crosses the axis at $x=\tfrac12$ and touches it at the double root $x=1$; the $y$-intercept is $-1$.

80(c): $f(x)=x^2e^{-x}$. By the product rule,

$$
\begin{aligned}
f'(x)&=2xe^{-x}-x^2e^{-x}=x(2-x)e^{-x},\\
f''(x)&=(2-2x)e^{-x}-(2x-x^2)e^{-x}=(x^2-4x+2)e^{-x}.
\end{aligned}
$$

At $x=0$, $f''=2>0$: a minimum, $f=0$ (and since $f\geq0$ everywhere it is the global minimum). At $x=2$, $f''=-2e^{-2}<0$: a maximum, $f=4e^{-2}\approx0.541$. The inflections are at $x^2-4x+2=0$, $x=2\pm\sqrt2$ ($0.586$ and $3.414$, where $f=0.191$ and $0.384$). As $x\to\infty$, $f\to0^+$ because the exponential decays faster than any power grows; as $x\to-\infty$, $f\to\infty$.

### Specimen Test 8, Q3

Sketch $y=x^3-3x^2+2$. Since $y(1)=0$, $(x-1)$ is a factor:

$$
y=(x-1)(x^2-2x-2),
$$

and the quadratic gives the other roots $x=1\pm\sqrt3\approx-0.732,\ 2.732$. The $y$-intercept is $2$. Then $y'=3x^2-6x=3x(x-2)$ and $y''=6x-6$: at $x=0$, $y''=-6$, a maximum with $y=2$; at $x=2$, $y''=6$, a minimum with $y=-2$. The inflection is at $x=1$, $y=0$, and $y(1+h)+y(1-h)=0$ for every $h$, so the curve has point symmetry about $(1,0)$. As $x\to\pm\infty$, $y\to\pm\infty$.

![[m1054_curve_sketches_stationary.png|800]]

## 4. Parametric differentiation (James §8.3.14)

A curve is given **parametrically** when both coordinates are functions of a parameter, $x=x(t)$, $y=y(t)$. Dots denote $t$-derivatives, $\dot x=dx/dt$. Where the curve is locally the graph of a differentiable function $y=f(x)$, write $y(t)=f(x(t))$ and apply the chain rule:

$$
\frac{dy}{dt}=\frac{dy}{dx}\,\frac{dx}{dt}.
$$

Dividing by $dx/dt$, which is allowed where $\dot x\neq0$,

$$
\frac{dy}{dx}=\frac{dy/dt}{dx/dt}=\frac{\dot y}{\dot x}.
$$

Where $\dot x=0$ and $\dot y\neq0$ the tangent is vertical; where both vanish the curve may have a cusp and needs a closer look.

### The semicubical parabola (Example 8.21)

$x=t^3$, $y=t^2$. Then $\dot x=3t^2$, $\dot y=2t$, and

$$
\frac{dy}{dx}=\frac{2t}{3t^2}=\frac2{3t}\qquad(t\neq0).
$$

Eliminating $t$ gives $y=x^{2/3}$, and direct differentiation agrees: $y'=\tfrac23x^{-1/3}$. In terms of $x$ and $y$ together, $y'=2y/(3x)$. At the origin both $\dot x$ and $\dot y$ vanish, the slope tends to $\pm\infty$ from the two sides, and the curve has a cusp: there is no well-defined tangent and $f$ is not differentiable at $x=0$.

### A spiral (Exercise 47)

$x=t\sin t$, $y=t\cos t$. By the product rule $\dot x=\sin t+t\cos t$ and $\dot y=\cos t-t\sin t$, so

$$
\frac{dy}{dx}=\frac{\cos t-t\sin t}{\sin t+t\cos t}.
$$

![[m1054_m08_parametric_curves.png|900]]

## 5. Implicit differentiation (James §8.3.14)

An equation $F(x,y)=0$ links $x$ and $y$ **implicitly**. It often cannot be solved for $y$ (for example $y^4+\sin xy=0$), but near most points it still defines $y$ as a differentiable function of $x$. Treat $y$ as $y(x)$ and differentiate every term with respect to $x$. A term $g(y)$ is a composite function of $x$, so the chain rule gives

$$
\frac{d}{dx}g(y)=\frac{dg}{dy}\,\frac{dy}{dx},
$$

for example

$$
\frac{d}{dx}y^n=ny^{n-1}y',\qquad\frac{d}{dx}\sin y=\cos y\;y',
$$

and a product of $x$ and $y$ needs the product rule as well:

$$
\frac{d}{dx}(xy)=y+xy'.
$$

The result is linear in $y'$, so collect the $y'$ terms and solve.

The same calculation in general form uses partial derivatives ([[Partial Derivatives]], [[MATH1054 M03 - Differentiation I|Module 3]]). Differentiating $F(x,y(x))=0$ with the two-variable chain rule gives

$$
F_x+F_y\,y'=0\quad\Rightarrow\quad y'=-\frac{F_x}{F_y}\qquad(F_y\neq0).
$$

For $y^3=x^2$ (Example 8.21 with $t$ eliminated), $3y^2y'=2x$, so $y'=\dfrac{2x}{3y^2}=\dfrac{2y}{3x}$ after substituting $y^3=x^2$, as before.

The tangent at a point $(x_1,y_1)$ with slope $m=y'(x_1,y_1)$ is $y-y_1=m(x-x_1)$, and the normal has slope $-1/m$. Check first that the point lies on the curve.

### A conic (Example 8.22)

$x^2+y^2+xy=1$. Differentiating term by term,

$$
\begin{aligned}
2x+2yy'+(y+xy')&=0\\
(2y+x)\,y'&=-(2x+y)\\
y'&=-\frac{2x+y}{x+2y}.
\end{aligned}
$$

The shortcut agrees: $F_x=2x+y$, $F_y=2y+x$.

### Tangent and normal (Example 8.23)

The tangent and normal to $x^2+y^2-3xy+4=0$ at $(2,4)$. The point is on the curve: $4+16-24+4=0$. Differentiating,

$$
\begin{aligned}
2x+2yy'-3y-3xy'&=0\\
(2y-3x)\,y'&=3y-2x\\
y'&=\frac{3y-2x}{2y-3x}.
\end{aligned}
$$

At $(2,4)$, $y'=\dfrac{12-4}{8-6}=4$. The tangent is

$$
y-4=4(x-2)\quad\Rightarrow\quad y=4x-4,
$$

and the normal, with slope $-\tfrac14$, is

$$
y-4=-\tfrac14(x-2)\quad\Rightarrow\quad x+4y=18 .
$$

### Slopes on a circle (Example 8.24)

The slopes of the tangents to $x^2+y^2-2x+4y-20=0$ at A$(1,3)$, B$(4,2)$ and C$(-2,-6)$. Differentiating,

$$
\begin{aligned}
2x+2yy'-2+4y'&=0\\
(y+2)\,y'&=1-x\\
y'&=\frac{1-x}{y+2}\qquad(y\neq-2).
\end{aligned}
$$

| Point | $y'$ |
|---|---|
| A$(1,3)$ | $0$ (horizontal tangent: the top of the circle) |
| B$(4,2)$ | $\frac{-3}4$ |
| C$(-2,-6)$ | $\frac{3}{-4}=-\frac34$ |

Completing the square, the curve is $(x-1)^2+(y+2)^2=25$, the circle with centre $(1,-2)$ and radius 5. The midpoint of B and C is the centre, so B and C are diametrically opposite and their tangents are parallel, as the equal slopes show. The derivative is undefined at $y=-2$, which on the circle means $(x-1)^2=25$, so $x=-4$ or $x=6$: at $(-4,-2)$ and $(6,-2)$ the tangent is vertical. Elsewhere the equation defines $y$ as a function of $x$ only locally, on the upper or the lower half of the circle.

![[m1054_m08_implicit_curves.png|900]]

### Tangents to implicit curves (Exercises 51 and 52, Specimen Test 8 Q5)

Exercise 51: the tangent to $y^3x+y+7x^4=4$ at $(0,4)$. The point lies on the curve ($0+4+0=4$). Differentiating, with the product rule on $y^3x$,

$$
\begin{aligned}
3y^2y'\,x+y^3+y'+28x^3&=0\\
(3xy^2+1)\,y'&=-(y^3+28x^3)\\
y'&=-\frac{y^3+28x^3}{3xy^2+1}.
\end{aligned}
$$

At $(0,4)$, $y'=-64$, and the tangent is $y=4-64x$.

Exercise 52, on the curve $x^3+y^3-xy-x=0$ at $(1,-1)$: the point is on it, $1-1+1-1=0$. Differentiating,

$$
\begin{aligned}
3x^2+3y^2y'-(y+xy')-1&=0\\
(3y^2-x)\,y'&=1+y-3x^2\\
y'&=\frac{1+y-3x^2}{3y^2-x},
\end{aligned}
$$

so at $(1,-1)$, $y'=\dfrac{1-1-3}{3-1}=-\tfrac32$. The curve as printed in James, $x^3-y^3-xy-x=0$, does not pass through $(1,-1)$ (its left side is 2 there); the Module 8 work scheme sets the corrected curve.

Specimen Q5: the tangent to $x^3+y^2+xy-3=0$ at $(1,1)$. Differentiating,

$$
\begin{aligned}
3x^2+2yy'+y+xy'&=0\\
y'&=-\frac{3x^2+y}{2y+x},
\end{aligned}
$$

so $y'=-\tfrac43$ at $(1,1)$ and the tangent is $y-1=-\tfrac43(x-1)$, that is $4x+3y=7$.

## 6. Logarithmic differentiation (James §8.3.14)

Logarithmic differentiation is implicit differentiation applied to $\ln y$. For $y=f(x)>0$, take logarithms and differentiate both sides, using the chain rule on $\ln y$:

$$
\begin{aligned}
\ln y&=\ln f(x)\\
\frac1y\,\frac{dy}{dx}&=\frac{d}{dx}\ln f(x)\\
\frac{dy}{dx}&=y\,\frac{d}{dx}\ln f(x).
\end{aligned}
$$

If $f$ can be negative, use $\ln|y|$ instead: $\frac{d}{dx}\ln|y|=y'/y$ for $y\neq0$ of either sign, so the result is the same wherever $y\neq0$. The method pays off in two situations.

The first is a variable in both the base and the exponent, $u(x)^{v(x)}$, which no single rule of Module 3 covers. Taking logs turns the power into a product:

$$
\ln y=v\ln u\quad\Rightarrow\quad\frac{y'}y=v'\ln u+v\,\frac{u'}u .
$$

The second is a long product or quotient of powers, $y=u_1^{a_1}u_2^{a_2}\cdots u_n^{a_n}$. The log laws turn it into a sum, which differentiates term by term:

$$
\ln y=\sum_k a_k\ln u_k\quad\Rightarrow\quad\frac{y'}{y}=\sum_k a_k\frac{u_k'}{u_k}.
$$

A constant base is the simplest case of the first kind: for $y=a^x$ with $a>0$, $\ln y=x\ln a$, so $y'=a^x\ln a$. The same follows from $a^x=e^{x\ln a}$.

### Variable base and exponent (Example 8.25)

$f(x)=(\sin x)^x$ on $(0,\pi)$, where $\sin x>0$:

$$
\begin{aligned}
\ln f&=x\ln\sin x\\
\frac{f'}{f}&=\ln\sin x+x\cdot\frac{\cos x}{\sin x}\\
f'(x)&=(\sin x)^x\big(\ln\sin x+x\cot x\big).
\end{aligned}
$$

The same steps give $\dfrac{d}{dx}x^x=x^x(\ln x+1)$ for $x>0$. This vanishes only at $x=1/e$, where the second derivative is positive ($1.88$), so $x^x$ has its minimum value $(1/e)^{1/e}=0.6922$ there.

### A product of powers (Example 8.26)

$$
y=\frac{(x-2)^3(x+3)^9}{\sqrt{x^2+1}}.
$$

Taking logs (with $\ln|\cdot|$ the result holds for all $x\neq2,-3$):

$$
\ln y=3\ln(x-2)+9\ln(x+3)-\tfrac12\ln(x^2+1).
$$

Differentiating,

$$
\begin{aligned}
\frac{y'}y&=\frac3{x-2}+\frac9{x+3}-\frac{x}{x^2+1}\\
&=\frac{3(x+3)(x^2+1)+9(x-2)(x^2+1)-x(x-2)(x+3)}{(x-2)(x+3)(x^2+1)}\\
&=\frac{11x^3-10x^2+18x-9}{(x-2)(x+3)(x^2+1)}.
\end{aligned}
$$

Multiplying by $y$ cancels one power of each factor:

$$
y'=\frac{(x-2)^2(x+3)^8(11x^3-10x^2+18x-9)}{(x^2+1)^{3/2}}.
$$

### Variable powers and products (Exercises 53(a) and 58)

53(a): $\dfrac{d}{dx}10^x=10^x\ln10$, from $\ln y=x\ln10$.

58(a): $y=(\ln x)^x$ for $x>1$, so that $\ln x>0$:

$$
\begin{aligned}
\ln y&=x\ln(\ln x)\\
\frac{y'}{y}&=\ln(\ln x)+x\cdot\frac{1}{\ln x}\cdot\frac1x\\
y'&=(\ln x)^x\Big[\ln(\ln x)+\frac1{\ln x}\Big].
\end{aligned}
$$

58(c): $y=(1-x^2)^{1/2}(2x^2+3)^{-4/3}$ for $|x|<1$:

$$
\begin{aligned}
\ln y&=\tfrac12\ln(1-x^2)-\tfrac43\ln(2x^2+3)\\
\frac{y'}y&=-\frac{x}{1-x^2}-\frac{16x}{3(2x^2+3)}\\
&=\frac{-3x(2x^2+3)-16x(1-x^2)}{3(1-x^2)(2x^2+3)}\\
&=\frac{10x^3-25x}{3(1-x^2)(2x^2+3)}=\frac{5x(2x^2-5)}{3(1-x^2)(2x^2+3)}.
\end{aligned}
$$

Multiplying by $y$,

$$
y'=\frac{5x(2x^2-5)}{3(1-x^2)^{1/2}(2x^2+3)^{7/3}}.
$$

## 7. Second derivatives of parametric and implicit curves (James §8.4.1)

The concavity of a parametric or implicit curve, and hence the nature of its stationary points, needs $d^2y/dx^2$. The rule is to differentiate $dy/dx$ with respect to $x$, using the chain rule whenever $dy/dx$ is expressed in another variable.

For a parametric curve, $dy/dx$ is a function of $t$, so

$$
\begin{aligned}
\frac{d^2y}{dx^2}&=\frac{d}{dx}\Big(\frac{dy}{dx}\Big)\\
&=\frac{d}{dt}\Big(\frac{dy}{dx}\Big)\,\frac{dt}{dx}\\
&=\frac{\dfrac{d}{dt}\Big(\dfrac{dy}{dx}\Big)}{dx/dt}.
\end{aligned}
$$

Expanding $\frac{d}{dt}(\dot y/\dot x)$ by the quotient rule gives the general formula:

$$
\frac{d}{dt}\Big(\frac{\dot y}{\dot x}\Big)=\frac{\ddot y\,\dot x-\dot y\,\ddot x}{\dot x^2}\quad\Rightarrow\quad\frac{d^2y}{dx^2}=\frac{\dot x\,\ddot y-\dot y\,\ddot x}{\dot x^3}.
$$

> [!warning] The classic error
> $\dfrac{d^2y}{dx^2}\neq\dfrac{d^2y/dt^2}{d^2x/dt^2}$. For $x=t^3$, $y=t^2$ the wrong quotient gives $\ddot y/\ddot x=2/(6t)=1/(3t)$, while the correct value is $-2/(9t^4)$. Always differentiate $\frac{dy}{dx}$ with respect to $t$, then divide by $\frac{dx}{dt}$.

For an implicit curve, differentiate the equation for $y'$ once more with respect to $x$, remembering that $y'$ is itself a function of $x$ ($\frac{d}{dx}y'=y''$, $\frac{d}{dx}(y')^2=2y'y''$), then substitute the known $y'$, and finally simplify using the curve's own equation.

The same chain-rule care gives the second derivative of an inverse function. Since $\dfrac{dx}{dy}=1\Big/\dfrac{dy}{dx}$,

$$
\begin{aligned}
\frac{d^2x}{dy^2}&=\frac{d}{dy}\Big(\frac{dy}{dx}\Big)^{-1}\\
&=\frac{d}{dx}\Big(\frac{dy}{dx}\Big)^{-1}\,\frac{dx}{dy}\\
&=-\Big(\frac{dy}{dx}\Big)^{-2}\frac{d^2y}{dx^2}\cdot\Big(\frac{dy}{dx}\Big)^{-1}\\
&=-\frac{d^2y/dx^2}{(dy/dx)^3},
\end{aligned}
$$

which is not $1\big/\frac{d^2y}{dx^2}$. General formulae like this need not be memorised, but the calculation in a particular case is examinable (Module 8 work scheme, item 7).

### Parametric second derivative (Example 8.29(a))

$y=t^2$, $x=t^3$. From Example 8.21, $\dfrac{dy}{dx}=\dfrac{2}{3t}$, so

$$
\begin{aligned}
\frac{d^2y}{dx^2}&=\frac{\frac{d}{dt}\big(\frac2{3t}\big)}{dx/dt}\\
&=\frac{-\frac{2}{3t^2}}{3t^2}\\
&=-\frac{2}{9t^4}.
\end{aligned}
$$

The general formula agrees: $\dfrac{3t^2\cdot2-2t\cdot6t}{(3t^2)^3}=\dfrac{-6t^2}{27t^6}=-\dfrac2{9t^4}$. So does direct differentiation of $y=x^{2/3}$: $y''=-\frac29x^{-4/3}=-\frac2{9t^4}$. The curve is concave down on both sides of the cusp.

### Implicit second derivative (Example 8.29(b))

$x^2+y^2-2x+4y-20=0$, with $(y+2)y'+x-1=0$ from Example 8.24. Differentiating this once more, with the product rule on $(y+2)y'$,

$$
\begin{aligned}
y'\cdot y'+(y+2)\,y''+1&=0\\
y''&=-\frac{1+(y')^2}{y+2}.
\end{aligned}
$$

Substituting $y'=\dfrac{1-x}{y+2}$,

$$
\begin{aligned}
y''&=-\frac{(y+2)^2+(1-x)^2}{(y+2)^3}\\
&=-\frac{x^2+y^2-2x+4y+5}{(y+2)^3}.
\end{aligned}
$$

On the circle, $(x-1)^2+(y+2)^2=25$, so

$$
y''=-\frac{25}{(y+2)^3}\qquad(y\neq-2).
$$

On the upper half ($y>-2$) $y''<0$, concave down; on the lower half $y''>0$, concave up, as a circle should be.

### The cycloid (Exercise 65)

$x=a(\theta-\sin\theta)$, $y=a(1-\cos\theta)$ is the path of a point on the rim of a wheel of radius $a$ rolling along the $x$ axis. The first derivative, using $\sin\theta=2\sin\frac\theta2\cos\frac\theta2$ and $1-\cos\theta=2\sin^2\frac\theta2$:

$$
\begin{aligned}
\frac{dy}{dx}&=\frac{a\sin\theta}{a(1-\cos\theta)}\\
&=\frac{2\sin\frac\theta2\cos\frac\theta2}{2\sin^2\frac\theta2}\\
&=\cot\tfrac\theta2 .
\end{aligned}
$$

The second derivative:

$$
\begin{aligned}
\frac{d^2y}{dx^2}&=\frac{\frac{d}{d\theta}\cot\frac\theta2}{dx/d\theta}\\
&=\frac{-\frac12\csc^2\frac\theta2}{a\cdot2\sin^2\frac\theta2}\\
&=-\frac{1}{4a\sin^4\frac\theta2}=-\frac{1}{a(1-\cos\theta)^2}.
\end{aligned}
$$

This is negative wherever it is defined, so every arch is concave down; at $\theta=2\pi k$ the point touches the ground, $\dot x=\dot y=0$, and the curve has a cusp. At $\theta=2\pi/3$ with $a=1$, the slope is $\cot\frac\pi3=0.577$ and $y''=-1/(3/2)^2=-0.444$.

### Specimen Test 8, Q4

$x=t^2$, $y=t^3$:

$$
\frac{dy}{dx}=\frac{3t^2}{2t}=\frac{3t}2,\qquad\frac{d^2y}{dx^2}=\frac{\frac{d}{dt}(3t/2)}{dx/dt}=\frac{3/2}{2t}=\frac3{4t}\qquad(t\neq0).
$$

## 8. Taylor and Maclaurin series (James §9.4.2)

A **Maclaurin series** writes a function as a power series in $x$ whose coefficients come from the derivatives at $x=0$:

$$
f(x)=f(0)+f'(0)x+\frac{f''(0)}{2!}x^2+\frac{f'''(0)}{3!}x^3+\cdots=\sum_{n=0}^\infty\frac{f^{(n)}(0)}{n!}x^n .
$$

### The coefficients, derived

Suppose $f$ has a power series that can be differentiated term by term:

$$
f(x)=c_0+c_1x+c_2x^2+c_3x^3+c_4x^4+\cdots
$$

Setting $x=0$ removes every term but the first, so $c_0=f(0)$. Differentiate once:

$$
f'(x)=c_1+2c_2x+3c_3x^2+4c_4x^3+\cdots
$$

and $x=0$ gives $c_1=f'(0)$. Differentiate again:

$$
f''(x)=2c_2+3\cdot2\,c_3x+4\cdot3\,c_4x^2+\cdots
$$

so $f''(0)=2c_2$, that is $c_2=f''(0)/2!$. After $n$ differentiations the term $c_nx^n$ has become the constant $n(n-1)\cdots1\cdot c_n=n!\,c_n$, every lower power has been differentiated away and every higher power still carries a factor of $x$. Hence

$$
f^{(n)}(0)=n!\,c_n\quad\Rightarrow\quad c_n=\frac{f^{(n)}(0)}{n!}.
$$

The same argument at $x=a$ with powers of $(x-a)$ gives the **Taylor series** about $x=a$:

$$
f(x)=\sum_{n=0}^\infty\frac{f^{(n)}(a)}{n!}(x-a)^n .
$$

With $x$ replaced by $a+x$ and the series stopped after the $x^n$ term, Taylor's theorem gives the exact statement

$$
f(a+x)=f(a)+xf'(a)+\frac{x^2}{2!}f''(a)+\cdots+\frac{x^n}{n!}f^{(n)}(a)+R_n(x),\qquad R_n(x)=\frac{x^{n+1}}{(n+1)!}f^{(n+1)}(a+\theta x),\ 0<\theta<1 .
$$

The finite sum is the Taylor polynomial of degree $n$, and $R_n$ (Lagrange's form of the remainder) is its exact error. The infinite series represents $f$ only for those $x$ at which $R_n(x)\to0$ as $n\to\infty$, so each series comes with an interval of validity. A Maclaurin series is the Taylor series with $a=0$. Bounds on $R_n$ and convergence tests are in [[MATH1054 M20 - Further Calculus II|Module 20]].

### Standard series

These follow from the coefficient formula; for $e^x$, every derivative is $e^x$ and equals 1 at $x=0$, and for $\sin x$ the derivatives cycle $\sin,\cos,-\sin,-\cos$.

| $f(x)$ | Maclaurin series | Valid for |
|---|---|---|
| $(1+x)^r$ | $1+rx+\frac{r(r-1)}{2!}x^2+\frac{r(r-1)(r-2)}{3!}x^3+\cdots$ | $-1<x<1$ |
| $e^x$ | $1+x+\frac{x^2}{2!}+\frac{x^3}{3!}+\cdots$ | all $x$ |
| $\sin x$ | $x-\frac{x^3}{3!}+\frac{x^5}{5!}-\cdots$ | all $x$ |
| $\cos x$ | $1-\frac{x^2}{2!}+\frac{x^4}{4!}-\cdots$ | all $x$ |
| $\ln(1+x)$ | $x-\frac{x^2}2+\frac{x^3}3-\frac{x^4}4+\cdots$ | $-1<x\leq1$ |
| $\tan x$ | $x+\frac{x^3}3+\frac{2x^5}{15}+\frac{17x^7}{315}+\cdots$ | $-\frac\pi2<x<\frac\pi2$ |
| $\sinh x$ | $x+\frac{x^3}{3!}+\frac{x^5}{5!}+\cdots$ | all $x$ |
| $\cosh x$ | $1+\frac{x^2}{2!}+\frac{x^4}{4!}+\cdots$ | all $x$ |

Within their common interval of validity, known series can be added, multiplied and substituted into each other. That is usually much faster than differentiating repeatedly; the direct method is the definition and the check.

### The series for e to the x times sin x (Example 9.10)

$f(x)=e^x\sin x$. The product rule gives

$$
f'(x)=e^x(\sin x+\cos x).
$$

By the addition formula, $\sqrt2\sin\big(x+\frac\pi4\big)=\sqrt2\big(\sin x\cdot\frac1{\sqrt2}+\cos x\cdot\frac1{\sqrt2}\big)=\sin x+\cos x$, so

$$
f'(x)=\sqrt2\,e^x\sin\big(x+\tfrac\pi4\big).
$$

The same step applies to $e^x\sin(x+\varphi)$ for any phase $\varphi$, so each differentiation multiplies by $\sqrt2$ and adds $\frac\pi4$ to the argument:

$$
f^{(k)}(x)=(\sqrt2)^k\,e^x\sin\big(x+\tfrac{k\pi}4\big),\qquad f^{(k)}(0)=(\sqrt2)^k\sin\tfrac{k\pi}4 .
$$

In particular $f^{(4)}=4e^x\sin(x+\pi)=-4f$, so the pattern repeats every four derivatives with a factor $-4$.

| $n$ | $f^{(n)}(x)$ | $f^{(n)}(0)$ |
|---|---|---|
| 0 | $e^x\sin x$ | 0 |
| 1 | $e^x(\sin x+\cos x)$ | 1 |
| 2 | $2e^x\cos x$ | 2 |
| 3 | $2e^x(\cos x-\sin x)$ | 2 |
| 4 | $-4e^x\sin x$ | 0 |
| 5 | $-4e^x(\sin x+\cos x)$ | −4 |
| 6 | $-8e^x\cos x$ | −8 |

Substituting into the Maclaurin formula,

$$
\begin{aligned}
e^x\sin x&=0+x+\frac{2x^2}{2!}+\frac{2x^3}{3!}+\frac{0\cdot x^4}{4!}-\frac{4x^5}{5!}-\frac{8x^6}{6!}+\cdots\\
&=x+x^2+\frac{x^3}3-\frac{x^5}{30}-\frac{x^6}{90}+\cdots
\end{aligned}
$$

The series is valid for all $x$, because the series for $e^x$ and $\sin x$ are. Multiplying the known series checks it:

$$
\begin{aligned}
\Big(1+x+\frac{x^2}2+\frac{x^3}6+\frac{x^4}{24}\Big)\Big(x-\frac{x^3}6+\frac{x^5}{120}\Big)&=x+x^2+\Big(\frac12-\frac16\Big)x^3+\Big(\frac16-\frac16\Big)x^4\\
&\quad+\Big(\frac1{120}-\frac1{12}+\frac1{24}\Big)x^5+\cdots\\
&=x+x^2+\frac{x^3}3-\frac{x^5}{30}+\cdots
\end{aligned}
$$

### Series for e to the x and (1+x) sin x (Booklet Exercises A and B)

Exercise A: $f^{(n)}(x)=e^x$ for every $n$, so $f^{(n)}(0)=1$ and

$$
e^x=\sum_{n=0}^\infty\frac{x^n}{n!}=1+\frac{x}{1!}+\frac{x^2}{2!}+\frac{x^3}{3!}+\cdots
$$

Exercise B: the first four non-zero terms of $(1+x)\sin x$.

(a) From the derivatives, using the product rule each time:

| $n$ | $f^{(n)}$ | at 0 |
|---|---|---|
| 0 | $(1+x)\sin x$ | 0 |
| 1 | $\sin x+(1+x)\cos x$ | 1 |
| 2 | $2\cos x-(1+x)\sin x$ | 2 |
| 3 | $-3\sin x-(1+x)\cos x$ | −1 |
| 4 | $-4\cos x+(1+x)\sin x$ | −4 |

$$
(1+x)\sin x=x+\frac{2x^2}{2!}-\frac{x^3}{3!}-\frac{4x^4}{4!}+\cdots=x+x^2-\frac{x^3}6-\frac{x^4}6+\cdots
$$

(b) By multiplication:

$$
(1+x)\Big(x-\frac{x^3}6+\frac{x^5}{120}-\cdots\Big)=x+x^2-\frac{x^3}6-\frac{x^4}6+\cdots
$$

The two methods agree, and (b) takes one line.

### Specimen Test 8, Q6

For $f=\sin x$ the derivatives cycle $\sin x,\cos x,-\sin x,-\cos x$, so at 0 they take the values $0,1,0,-1,0,1,\dots$ and

$$
\sin x=0+x+0-\frac{x^3}{3!}+0+\frac{x^5}{5!}-\cdots=x-\frac{x^3}{3!}+\frac{x^5}{5!}-\cdots
$$

Only odd powers appear because $\sin$ is odd; likewise $\cos$, which is even, has only even powers.

> [!check] Partial sums of the sine series
> At $x=0.5$ rad the partial sums are $0.5$, $0.4791667$ and $0.4794271$, against $\sin0.5=0.4794255$. Each extra term cuts the error by a factor of about 100 here, because the next term $x^{2n+1}/(2n+1)!$ shrinks quickly for $|x|<1$. Far from 0 many more terms are needed (figure below).

![[m1054_m08_maclaurin_sin.png|900]]

### A Taylor series about a point other than zero

Expanding about a point near where $f$ is wanted converges much faster than expanding about 0. For $f(x)=\sqrt x$ about $a=4$:

$$
f(4)=2,\quad f'(x)=\tfrac12x^{-1/2}\Rightarrow f'(4)=\tfrac14,\quad f''(x)=-\tfrac14x^{-3/2}\Rightarrow f''(4)=-\tfrac1{32},\quad f'''(x)=\tfrac38x^{-5/2}\Rightarrow f'''(4)=\tfrac3{256}.
$$

With $x=4+h$,

$$
\begin{aligned}
\sqrt{4+h}&\approx2+\frac{h}{4}-\frac{1}{2!}\cdot\frac{h^2}{32}+\frac1{3!}\cdot\frac{3h^3}{256}\\
&=2+\frac h4-\frac{h^2}{64}+\frac{h^3}{512}.
\end{aligned}
$$

At $h=0.1$ this gives $\sqrt{4.1}\approx2.0248457$, in error by $3.0\times10^{-8}$. ($\sqrt x$ has no Maclaurin series at all, since $f'(0)$ does not exist.)

### Stationary points revisited with Taylor's theorem

Taylor's theorem justifies the tests of Section 1 and extends them. Suppose $f'(a)=f''(a)=\cdots=f^{(n-1)}(a)=0$ and $f^{(n)}(a)\neq0$. Then the remainder form above, with $h$ in place of $x$ and the polynomial stopped at degree $n-1$, gives

$$
f(a+h)-f(a)=\frac{h^n}{n!}f^{(n)}(a+\theta h),
$$

and for small $|h|$ the factor $f^{(n)}(a+\theta h)$ has the sign of $f^{(n)}(a)$ (for continuous $f^{(n)}$). If $n$ is even, $h^n>0$ on both sides, so $f(a+h)-f(a)$ has one sign: a minimum if $f^{(n)}(a)>0$, a maximum if $f^{(n)}(a)<0$. If $n$ is odd, $h^n$ changes sign with $h$, so $f$ is above $f(a)$ on one side and below on the other: a stationary inflection. With $n=2$ this is the second-derivative test. For $x^3$ the first non-zero derivative at 0 is $f'''=6$ ($n=3$, inflection); for $x^4$ it is $f^{(4)}=24$ ($n=4$, minimum); for $-x^4$ it is $-24$ (maximum). The Specimen Test condition $f'''(x_0)\neq0$ for a stationary inflection is the case $n=3$.

The first-order Taylor polynomial also gives Newton–Raphson: setting $g(t_n+\delta)\approx g(t_n)+\delta\,g'(t_n)=0$ gives the correction $\delta=-g(t_n)/g'(t_n)$ used in [[#Replacing a car (Example 8.36)]].

## Terminology and alternative names

| Term here | Also called | Note |
|---|---|---|
| stationary point | critical point; turning point (max or min only) | a stationary inflection is stationary but not a turning point |
| Maclaurin series | Taylor series about $x=0$ | James (9.13) |
| $\dot x$, $\dot y$ | $dx/dt$, $dy/dt$ | dot notation for parameter derivatives |

## Links

- Parent: [[MATH1054 Mathematics for Engineering and the Environment Hub]] · Solutions: [[MATH1054 M08 Solutions - Differentiation II]]
- Previous: [[MATH1054 M07 - Functions]] · Next: [[MATH1054 M20 - Further Calculus II]] (sequences, series, the remainder, L'Hôpital's rule)
- Builds on: [[MATH1054 M03 - Differentiation I]] (product, quotient and chain rules, Newton–Raphson, partial derivatives)
- Concepts: [[Stationary Points and Inflection]] · [[Implicit and Parametric Differentiation]] · [[Logarithmic Differentiation]] · [[Taylor and Maclaurin Series]] · [[Product, Quotient and Chain Rules]] · [[Partial Derivatives]] · [[Arithmetic and Geometric Series]] · [[Direct Substitution and Newton-Raphson]]
- Later: Taylor series give the finite-difference formulae and their errors in [[Finite Difference Approximations]], [[Taylor Table Method]] and [[Truncation Error and Order of Accuracy]] (SESA2029), the linearised aircraft equations in [[Small Perturbation Linearisation]] (SESA2027), and the comparison with Fourier series in [[MATH2048 FS1 - Fourier Series, Orthogonality and the Euler Formulae]].

## Sources

- MATH1054 Module Booklet, Module 8 (PDF pp. 19–21): work scheme items 1–8, Exercises A and B, Specimen Test 8
- James, *Modern Engineering Mathematics* (6th ed.): §2.5.3 (asymptotes, Examples 2.36–2.37, Exercise 44), §8.3.14–8.3.15 (parametric, implicit and logarithmic differentiation, Examples 8.21–8.26, Exercises 47–58), §8.4.1–8.4.2 (Example 8.29, the second derivative of an inverse function, Exercise 65), §8.5.1–8.5.2 (Examples 8.30–8.31 and 8.34–8.36, Exercises 79–80), §9.4.2 (equations (9.11)–(9.13), Example 9.10, Figure 9.6)
- Worked solutions: [[MATH1054 M08 Solutions - Differentiation II]]

## Self-study tasks

### Core

- [ ] Exercises 79(a) and 80(c), p. 616 (Module 08 work scheme, item 3): stationary values, inflections and sketches. → [[#A cubic and an exponential (Exercises 79(a) and 80(c))]] · [[MATH1054 M08 Solutions - Differentiation II#Part B: Assigned exercises|solutions]]
- [ ] Exercises 44(a),(b), p. 126 (Module 08 work scheme, item 3): rational functions with asymptotes. → [[#Two rational functions (Exercise 44)]] · [[MATH1054 M08 Solutions - Differentiation II#Exercise 44 (p.126): Sketches|solution]]
- [ ] Exercises 51, 52 (for $x^3+y^3-xy-x=0$) and 58(a),(c), pp. 596–597 (Module 08 work scheme, item 6). → [[#Tangents to implicit curves (Exercises 51 and 52, Specimen Test 8 Q5)]] · [[#Variable powers and products (Exercises 53(a) and 58)]] · [[MATH1054 M08 Solutions - Differentiation II#Exercise 58 (harder): Logarithmic differentiation|solution to 58]]
- [ ] Exercise 65, p. 601 (Module 08 work scheme, item 7): first and second derivatives of the cycloid. → [[#The cycloid (Exercise 65)]] · [[MATH1054 M08 Solutions - Differentiation II#Part B: Assigned exercises|solutions]]
- [ ] Specimen Test 8, Q1–Q6 (Module 8 booklet), timed. → [[MATH1054 M08 Solutions - Differentiation II#Part C: Specimen Test 8|solutions]]

### Further practice

- [ ] Booklet Exercises A and B (Module 08 work scheme, item 8): Maclaurin series of $e^x$ and of $(1+x)\sin x$ two ways. → [[#Series for e to the x and (1+x) sin x (Booklet Exercises A and B)]] · [[MATH1054 M08 Solutions - Differentiation II#Part B: Assigned exercises|solutions]]
- [ ] Exercises 47 and 53(a), p. 596 (Module 08 work scheme, item 6). → [[#A spiral (Exercise 47)]] · [[#Variable powers and products (Exercises 53(a) and 58)]]
- [ ] Rework Example 8.29(a),(b) without looking (Module 08 work scheme, item 7). → [[#Implicit second derivative (Example 8.29(b))]] · [[MATH1054 M08 Solutions - Differentiation II#Example 8.29: Second derivatives|solution]]
- [ ] Read Examples 8.34–8.36 and re-derive the car-replacement optimality condition (Module 08 work scheme, item 1, read only). → [[#Replacing a car (Example 8.36)]] · [[MATH1054 M08 Solutions - Differentiation II#Example 8.36 (read only): When to replace the car|solution]]
- [ ] Example 9.10 by both routes, derivatives and series multiplication (Module 08 work scheme, item 8). → [[#The series for e to the x times sin x (Example 9.10)]]

## Transcript and slide slips

> [!warning] James slips (§8.5, Examples 8.35 and 8.36)
> Where: [[#Replacing a car (Example 8.36)]] and [[#Milk carton (Example 8.35)]].
>
> | Where | James gives | Correct |
> |---|---|---|
> | Example 8.36 | $t=5.3$ years as the root of $e^{9.55-0.11t}=(14\,750-81.5t^2)/(1+0.11t)$ | $t=5.43$ years; at $t=5.3$ the residual $e^{9.55-0.11t}(1+0.11t)+81.5t^2-14\,750$ is $-49.9$, not zero |
> | Example 8.35 | carton height $169.8$ mm | $169.70$ mm from the unrounded root $b=81.818$ mm; $169.8$ is $1\,136\,000/81.8^2=169.77$ from the rounded base |
