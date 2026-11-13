---
title: "MATH1054 M09 - Integration II"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: topic
stream: "Block 1: Calculus"
order: 9
tags:
  - math1054
  - integration
  - substitution
  - applications-of-integration
aliases: ["MATH1054 Module 9", "Integration II"]
date: 2026-09-27
status: lectured
coverage: "Module Booklet Module 9 work scheme (substitution: recognising f(g(x))g'(x), root and trigonometric/hyperbolic substitutions, changing the limits; applications: volume of revolution, centroid of a plane area, centre of gravity of a solid of revolution, mean and RMS values, arc length and surface area) and Specimen Test 9; James §8.8.6, §8.8.12, §8.9.1–8.9.6"
parent: ["[[MATH1054 Mathematics for Engineering and the Environment Hub]]"]
prerequisites: ["[[MATH1054 M04 - Integration I]]", "[[MATH1054 M07 - Functions]]"]
next_topics: ["[[MATH1054 M10 - Integration III]]"]
key_concepts: ["[[Integration by Substitution]]", "[[Centroids and Solids of Revolution]]", "[[RMS Value]]"]
tutorial_sheets: ["[[MATH1054 M09 Solutions - Integration II]]"]
sources: ["02 - Sources/Course Booklets & Solutions/Module Booklet.pdf (Module 9)", "02 - Sources/Modern Engineering Mathematics.pdf (§8.8–8.9)", "02 - Sources/Formulae & Reference/Integration Formulae.md"]
---

# MATH1054 M09 - Integration II

> [!abstract] Summary
> Integration by substitution is the chain rule read backwards: $\int f(g(x))\,g'(x)\,\mathrm dx=\int f(u)\,\mathrm du$ with $u=g(x)$, and in a definite integral the limits change to $g(a)$ and $g(b)$. The same idea run the other way, $x=g(t)$, removes roots such as $\sqrt{1-x}$ or $\sqrt{a^2-x^2}$ through $\cos^2\theta+\sin^2\theta=1$ or $\cosh^2u-\sinh^2u=1$. Slicing a region into thin strips then turns integrals into engineering quantities: area, the centroid of a lamina, the volume and centre of gravity of a solid of revolution, mean and RMS values, arc length and surface area.

> [!summary]- Exam use: quick path
> - **Use it when:** the integrand contains a function together with its derivative, or a root of a linear or quadratic expression; or the question asks for an area, centroid, volume of revolution, centre of gravity, mean or RMS value, arc length or surface area.
> - **Assumptions:** the substitution $u=g(x)$ has a continuous derivative on the interval (and is monotonic when you substitute for $x$ itself); for applications, $y=f(x)\geq0$ on $[a,b]$ or the upper and lower curves are known; uniform density for a centre of gravity; angles in radians.
> - **Method:** 1. Sketch the region, or spot the inner function. 2. Choose $u$, write $\mathrm du$ and convert every $x$, including $\mathrm dx$. 3. Change the limits with the variable. 4. For applications, write the strip quantity (area $y\,\mathrm dx$, moment $xy\,\mathrm dx$ or $\tfrac12y^2\,\mathrm dx$, disc $\pi y^2\,\mathrm dx$) and integrate, then divide moments by $A$ or $V$. 5. Check by symmetry, dimensions or a limiting case.
> - **Common mistakes:** keeping the old $x$-limits after changing to $u$; dropping the $\tfrac12$ in $\bar y=\frac1{2A}\int y^2\,\mathrm dx$, or confusing the area centroid with the solid's centre of gravity (they differ: 3.8 against 4 in Example 8.65).
> - **Practise:** [[#Area, centroid, volume and centre of gravity (Example 8.65)]] · [[MATH1054 M09 Solutions - Integration II#Part C: Specimen Test 9|Specimen Test 9]]

Most integrals met in engineering are not on the table of standard forms as written, but become standard after a change of variable. The chain rule says that differentiating $F(g(x))$ produces $F'(g(x))\,g'(x)$, so whenever an integrand has that shape, an inner function multiplied by its own derivative, the antiderivative is $F(g(x))$. Substitution does this automatically: rename the inner function $u$, and the factor $g'(x)\,\mathrm dx$ becomes $\mathrm du$. When no inner function is visible, the change can run the other way: put $x=\sin\theta$ or $x=\sinh u$, chosen so that a Pythagorean identity collapses a square root into a single term.

The applications to geometry and physics all come from one picture: cut the region into vertical strips of width $\delta x$, write down the area, moment or volume that one strip contributes, add the strips, and let $\delta x\to0$ so the sum becomes an integral. A strip of height $y$ has area $y\,\delta x$, its own centroid at height $y/2$, and when rotated about the $x$-axis it sweeps a disc of volume $\pi y^2\,\delta x$. Area, centroid, volume of revolution and centre of gravity all follow from these three facts. Mean and RMS values are averages of a continuously varying quantity, and arc length and surface area come from the hypotenuse of a small triangle on the curve.

These results are used across the degree: centroids and first moments of area in structures ([[First Moment of Area]]), RMS current and voltage in electronics ([[RMS Value]]), mass properties of rotating parts ([[Mass Moment of Inertia and Radius of Gyration]]), and the mean of a continuous random variable in [[MATH1054 M24 - Statistics I|M24]]. Partial fractions and improper integrals are in [[MATH1054 M10 - Integration III|M10]], and the double integrals of [[MATH1054 M11 - Integration IV|M11]] give the same centroids with $\mathrm dA=\mathrm dx\,\mathrm dy$.

---

## 1. Substitution as the chain rule in reverse

### Indefinite integrals

Let $F$ be an antiderivative of $f$, so $F'=f$, and let $g$ be differentiable with a continuous derivative on the interval of interest. The chain rule ([[Product, Quotient and Chain Rules]]) gives

$$
\frac{\mathrm d}{\mathrm dx}F\big(g(x)\big)=F'\big(g(x)\big)\,g'(x)
$$

$$
\phantom{\frac{\mathrm d}{\mathrm dx}F\big(g(x)\big)}=f\big(g(x)\big)\,g'(x).
$$

Reading this as an integration statement,

$$
\int f\big(g(x)\big)\,g'(x)\,\mathrm dx=F\big(g(x)\big)+C.
$$

The right-hand side is $\int f(u)\,\mathrm du=F(u)+C$ evaluated at $u=g(x)$. So the rule can be carried out mechanically: set $u=g(x)$, replace $g'(x)\,\mathrm dx$ by $\mathrm du$ (from $\mathrm du/\mathrm dx=g'(x)$), integrate in $u$, and substitute back,

$$
\int f\big(g(x)\big)\,g'(x)\,\mathrm dx=\int f(u)\,\mathrm du\,\bigg|_{u=g(x)}.
$$

The choice of $g$ is not unique (choices that differ by a constant work equally well), and every $x$ in the integrand, not only $\mathrm dx$, has to be converted before integrating in $u$.

### Definite integrals and changing the limits

By the fundamental theorem of calculus,

$$
\int_a^b f\big(g(x)\big)\,g'(x)\,\mathrm dx=\Big[F\big(g(x)\big)\Big]_a^b
$$

$$
=F\big(g(b)\big)-F\big(g(a)\big)
$$

$$
=\Big[F(u)\Big]_{g(a)}^{g(b)}
$$

$$
=\int_{g(a)}^{g(b)}f(u)\,\mathrm du.
$$

The limits travel with the variable: $x=a$ becomes $u=g(a)$ and $x=b$ becomes $u=g(b)$. Once the limits are changed there is no need to substitute back (Example 8.62, Exercise 115). In this direction $g$ need not be monotonic; the derivation uses only the chain rule and the fundamental theorem.

### Two patterns to recognise on sight

When the integrand is a power of a function times the function's derivative, $u=f(x)$ gives, for $n\neq-1$,

$$
\int f'(x)\,\big[f(x)\big]^n\,\mathrm dx=\int u^n\,\mathrm du
$$

$$
=\frac{u^{n+1}}{n+1}+C
$$

$$
=\frac{\big[f(x)\big]^{n+1}}{n+1}+C.
$$

The excluded case $n=-1$ is a quotient whose numerator is the derivative of its denominator. For $u>0$, $\frac{\mathrm d}{\mathrm du}\ln u=\frac1u$; for $u<0$, $\frac{\mathrm d}{\mathrm du}\ln(-u)=\frac{-1}{-u}=\frac1u$. Hence $\int\frac{\mathrm du}u=\ln|u|+C$ on any interval avoiding $u=0$, and

$$
\int\frac{f'(x)}{f(x)}\,\mathrm dx=\ln\big|f(x)\big|+C.
$$

With practice both can be written down without naming $u$. A numerator that is a constant multiple of the denominator's derivative only needs that constant pulled out first.

### A product and a quotient (Example 8.52)

(a) $\int2x\sqrt{x^2+3}\,\mathrm dx$. The factor $2x$ is the derivative of $x^2+3$, so put $u=x^2+3$, $\mathrm du=2x\,\mathrm dx$:

$$
\int2x\sqrt{x^2+3}\,\mathrm dx=\int u^{1/2}\,\mathrm du
$$

$$
=\tfrac23u^{3/2}+C
$$

$$
=\tfrac23\big(x^2+3\big)^{3/2}+C.
$$

(b) $\int\frac{x+1}{x^2+2x+2}\,\mathrm dx$. The derivative of the denominator is $2x+2=2(x+1)$, so the numerator is half of it:

$$
\int\frac{x+1}{x^2+2x+2}\,\mathrm dx=\frac12\int\frac{2x+2}{x^2+2x+2}\,\mathrm dx
$$

$$
=\tfrac12\ln\big(x^2+2x+2\big)+C.
$$

No modulus is needed, because $x^2+2x+2=(x+1)^2+1>0$ for every $x$ ([[Completing the Square]]).

### Exercise A: recognising the inner function

| | Integral | Substitution or pattern | Result |
|---|---|---|---|
| (a) | $\int x^2(1+x^3)^4\,\mathrm dx$ | $u=1+x^3$, $\mathrm du=3x^2\,\mathrm dx$ | $\tfrac1{15}(1+x^3)^5+C$ |
| (b) | $\int\cos x\sin^3x\,\mathrm dx$ | $u=\sin x$, $\mathrm du=\cos x\,\mathrm dx$ | $\tfrac14\sin^4x+C$ |
| (c) | $\int x\cos(x^2)\,\mathrm dx$ | $u=x^2$, $\mathrm du=2x\,\mathrm dx$ | $\tfrac12\sin(x^2)+C$ |
| (d) | $\int\frac{\cosh x}{\sinh x}\,\mathrm dx$ | $f'/f$ with $f=\sinh x$ | $\ln\lvert\sinh x\rvert+C$ |
| (e) | $\int\frac{2x}{1+x^2}\,\mathrm dx$ | $f'/f$ with $f=1+x^2>0$ | $\ln(1+x^2)+C$ |
| (f) | $\int\frac{\cos x-\sin x}{\sin x+\cos x}\,\mathrm dx$ | $f'/f$, since $(\sin x+\cos x)'=\cos x-\sin x$ | $\ln\lvert\sin x+\cos x\rvert+C$ |
| (g) | $\int\frac{\ln x}{x}\,\mathrm dx$ | $u=\ln x$, $\mathrm du=\mathrm dx/x$ | $\tfrac12(\ln x)^2+C$ |

For (a), $\mathrm dx=\mathrm du/(3x^2)$, so the $x^2$ cancels:

$$
\int x^2u^4\,\frac{\mathrm du}{3x^2}=\frac13\int u^4\,\mathrm du=\frac13\cdot\frac{u^5}5+C=\frac1{15}(1+x^3)^5+C.
$$

Specimen Test 9, Q1 uses the same two patterns. For (a), the numerator is half the derivative of $1+x^2$:

$$
\int\frac{x}{1+x^2}\,\mathrm dx=\frac12\int\frac{2x}{1+x^2}\,\mathrm dx=\tfrac12\ln(1+x^2)+C.
$$

For (b), $u=\cos x$ gives $\mathrm du=-\sin x\,\mathrm dx$:

$$
\int\cos^4x\sin x\,\mathrm dx=-\int u^4\,\mathrm du=-\tfrac15\cos^5x+C.
$$

Exercise 112(h) is the same idea with a negative power: $u=4-x^2$, $\mathrm du=-2x\,\mathrm dx$, so

$$
\int\frac{x}{\sqrt{4-x^2}}\,\mathrm dx=-\frac12\int u^{-1/2}\,\mathrm du=-u^{1/2}+C=-\sqrt{4-x^2}+C.
$$

### Odd powers of sine or cosine (Exercise 122(b))

In $\int\sin^mx\cos^nx\,\mathrm dx$ with $n$ odd, save one $\cos x$ to be the $\mathrm du$ of $u=\sin x$, and convert the remaining even power with $\cos^2x=1-\sin^2x$:

$$
\int\sin^2x\cos^3x\,\mathrm dx=\int\sin^2x\,\big(1-\sin^2x\big)\cos x\,\mathrm dx
$$

$$
=\int\big(u^2-u^4\big)\,\mathrm du
$$

$$
=\tfrac13u^3-\tfrac15u^5+C
$$

$$
=\tfrac13\sin^3x-\tfrac15\sin^5x+C.
$$

With $m$ odd, the same works with $u=\cos x$. With both powers even, use the power-reduction formulae instead ([[Trigonometric Integrals and Power Reduction]]).

### Definite integrals with changed limits

Specimen Test 9, Q2: $\int_0^1\frac{x^2}{(1+x^3)^2}\,\mathrm dx$. Put $u=1+x^3$, $\mathrm du=3x^2\,\mathrm dx$; $x=0\to u=1$ and $x=1\to u=2$:

$$
\int_0^1\frac{x^2}{(1+x^3)^2}\,\mathrm dx=\frac13\int_1^2u^{-2}\,\mathrm du
$$

$$
=\frac13\Big[-\frac1u\Big]_1^2
$$

$$
=\frac13\Big(-\frac12+1\Big)=\frac16.
$$

Exercise 115(b): $\int_0^{\sqrt3}\frac{\tan^{-1}x}{1+x^2}\,\mathrm dx$ with $u=\tan^{-1}x$, so $\mathrm du=\frac{\mathrm dx}{1+x^2}$, and $x=0\to u=0$, $x=\sqrt3\to u=\frac\pi3$:

$$
\int_0^{\pi/3}u\,\mathrm du=\frac12\Big(\frac\pi3\Big)^2=\frac{\pi^2}{18}\approx0.5483.
$$

Exercise 115(d): $\int_1^4\frac{e^{\sqrt x}}{\sqrt x}\,\mathrm dx$ with $u=\sqrt x$, so $\mathrm du=\frac{\mathrm dx}{2\sqrt x}$, i.e. $\frac{\mathrm dx}{\sqrt x}=2\,\mathrm du$, and $x=1\to u=1$, $x=4\to u=2$:

$$
\int_1^4\frac{e^{\sqrt x}}{\sqrt x}\,\mathrm dx=2\int_1^2e^u\,\mathrm du
$$

$$
=2\big(e^2-e\big)\approx9.342.
$$

> [!warning] Change the limits or substitute back, not both
> After $u=\sqrt x$ the limits are $1$ and $2$, not $1$ and $4$. Evaluating $2\big[e^u\big]$ between the old $x$-limits gives $2(e^4-e)\approx103.8$ instead of $9.342$. Either change the limits and finish in $u$, or return to $x$ first and use the original limits.

## 2. Substituting for x to remove a root

### The rule read the other way

The identity of Section 1 can also be used from right to left. Let $x=g(t)$, where $g$ has a continuous derivative and is strictly monotonic on the $t$-interval, so that it has an inverse $t=g^{-1}(x)$. If $F'=f$, the chain rule gives

$$
\frac{\mathrm d}{\mathrm dt}F\big(g(t)\big)=f\big(g(t)\big)\,g'(t),
$$

so an antiderivative $H(t)$ of $f(g(t))\,g'(t)$ equals $F(g(t))$ up to a constant. Evaluating at $t=g^{-1}(x)$ recovers $F(x)$:

$$
\int f(x)\,\mathrm dx=\int f\big(g(t)\big)\,g'(t)\,\mathrm dt\,\bigg|_{t=g^{-1}(x)}.
$$

Monotonicity is what makes the return to $x$ possible. For a definite integral, with $g(t_a)=a$ and $g(t_b)=b$,

$$
\int_a^bf(x)\,\mathrm dx=\int_{t_a}^{t_b}f\big(g(t)\big)\,g'(t)\,\mathrm dt.
$$

In practice the substitution is often written as $t=h(x)$, for example $t=\sqrt{1-x}$, and inverted to $x=1-t^2$ to find $\mathrm dx$.

### A root in the denominator (Example 8.59)

Find $\int\frac{\mathrm dx}{2+\sqrt{1-x}}$. The root causes the difficulty, so put $t=\sqrt{1-x}$ ($t\geq0$, $x\leq1$). Then

$$
x=1-t^2,
$$

$$
\mathrm dx=-2t\,\mathrm dt,
$$

and the integral becomes

$$
\int\frac{\mathrm dx}{2+\sqrt{1-x}}=\int\frac{-2t}{2+t}\,\mathrm dt.
$$

The new integrand is a quotient of polynomials of equal degree. Add and subtract 2 in the numerator so that it divides:

$$
-\frac{2t}{2+t}=-2\,\frac{(2+t)-2}{2+t}
$$

$$
=-2\Big(1-\frac2{2+t}\Big)
$$

$$
=2\Big(\frac2{2+t}-1\Big).
$$

Integrating term by term ($2+t>0$),

$$
\int\frac{-2t}{2+t}\,\mathrm dt=4\ln(2+t)-2t+C
$$

$$
=4\ln\big(2+\sqrt{1-x}\big)-2\sqrt{1-x}+C.
$$

Improper rational functions like this one are treated systematically by polynomial division in [[MATH1054 M10 - Integration III|M10]].

### A root substitution with new limits (Example 8.62)

Evaluate $\int_{-2}^2\frac{\sqrt{x+2}}{x+6}\,\mathrm dx$ with $u=\sqrt{x+2}$. Then $u^2=x+2$, so

$$
x=u^2-2,\qquad\mathrm dx=2u\,\mathrm du,\qquad x+6=u^2+4,
$$

and the limits become $x=-2\to u=0$, $x=2\to u=2$:

$$
\int_{-2}^2\frac{\sqrt{x+2}}{x+6}\,\mathrm dx=\int_0^2\frac{u}{u^2+4}\,2u\,\mathrm du=\int_0^2\frac{2u^2}{u^2+4}\,\mathrm du.
$$

Again the degrees are equal, so add and subtract 4:

$$
\frac{2u^2}{u^2+4}=2\,\frac{(u^2+4)-4}{u^2+4}=2\Big(1-\frac4{u^2+4}\Big).
$$

With $\int\frac{\mathrm du}{u^2+4}=\frac12\tan^{-1}\frac u2$ (Section 3),

$$
\int_0^2\frac{2u^2}{u^2+4}\,\mathrm du=2\Big[u-2\tan^{-1}\frac u2\Big]_0^2
$$

$$
=2\Big(2-2\cdot\frac\pi4\Big)
$$

$$
=4-\pi\approx0.8584.
$$

### Specimen Test 9, Q3

Use $u^2=1+x^2$ to evaluate $\int_0^1\frac{x^3}{\sqrt{x^2+1}}\,\mathrm dx$. Differentiating the substitution implicitly,

$$
2u\,\mathrm du=2x\,\mathrm dx\quad\Longrightarrow\quad x\,\mathrm dx=u\,\mathrm du,
$$

and $x^2=u^2-1$, $\sqrt{x^2+1}=u$ (taking $u>0$). The limits are $x=0\to u=1$ and $x=1\to u=\sqrt2$. Split $x^3\,\mathrm dx=x^2\cdot x\,\mathrm dx$:

$$
\int_0^1\frac{x^2\cdot x\,\mathrm dx}{\sqrt{x^2+1}}=\int_1^{\sqrt2}\frac{(u^2-1)\,u\,\mathrm du}{u}
$$

$$
=\int_1^{\sqrt2}\big(u^2-1\big)\,\mathrm du
$$

$$
=\Big[\frac{u^3}3-u\Big]_1^{\sqrt2}
$$

$$
=\Big(\frac{2\sqrt2}3-\sqrt2\Big)-\Big(\frac13-1\Big)
$$

$$
=\frac{2-\sqrt2}3\approx0.1953.
$$

## 3. Trigonometric and hyperbolic substitutions (James §8.8.12, Figure 8.61)

A square root of a quadratic is removed by a substitution that turns the quadratic into a perfect square through one of the identities

$$
1-\sin^2\theta=\cos^2\theta,\qquad1+\tan^2\theta=\sec^2\theta,\qquad1+\sinh^2u=\cosh^2u,\qquad\cosh^2u-1=\sinh^2u.
$$

The range of the new variable has to be chosen so that the root is taken of a non-negative quantity and comes out with the right sign. The constant $a>0$ scales the substitution; it is 1 in the simplest cases.

| If the integrand contains | Try | Then | Range used |
|---|---|---|---|
| $\sqrt{a^2-x^2}$ | $x=a\sin\theta$ (or $x=a\tanh u$) | $\sqrt{a^2-x^2}=a\cos\theta$ | $-\frac\pi2\leq\theta\leq\frac\pi2$ |
| $\sqrt{a^2+x^2}$ or $a^2+x^2$ | $x=a\sinh u$ or $x=a\tan\theta$ | $\sqrt{a^2+x^2}=a\cosh u$; $a^2+x^2=a^2\sec^2\theta$ | all $u$; $-\frac\pi2<\theta<\frac\pi2$ |
| $\sqrt{x^2-a^2}$ | $x=a\cosh u$ (or $x=a\sec\theta$) | $\sqrt{x^2-a^2}=a\sinh u$ | $u\geq0$, i.e. $x\geq a$ |

### The inverse-function integrals from first principles

$\int\frac{\mathrm dx}{\sqrt{1-x^2}}$ for $-1<x<1$: put $x=\sin\theta$ with $-\frac\pi2<\theta<\frac\pi2$, where $\cos\theta>0$. Then $\mathrm dx=\cos\theta\,\mathrm d\theta$ and

$$
\int\frac{\mathrm dx}{\sqrt{1-x^2}}=\int\frac{\cos\theta\,\mathrm d\theta}{\sqrt{1-\sin^2\theta}}
$$

$$
=\int\frac{\cos\theta}{\cos\theta}\,\mathrm d\theta
$$

$$
=\theta+C=\sin^{-1}x+C.
$$

$\int\frac{\mathrm dx}{\sqrt{1+x^2}}$: put $x=\sinh u$, valid for all $x$, with $\cosh u>0$. Then $\mathrm dx=\cosh u\,\mathrm du$ and

$$
\int\frac{\mathrm dx}{\sqrt{1+x^2}}=\int\frac{\cosh u\,\mathrm du}{\sqrt{1+\sinh^2u}}
$$

$$
=\int\frac{\cosh u}{\cosh u}\,\mathrm du
$$

$$
=u+C=\sinh^{-1}x+C.
$$

Exercise B(a), $\int\frac{\mathrm dx}{\sqrt{x^2-1}}$ for $x>1$ with $x=\cosh u$, $u>0$: $\mathrm dx=\sinh u\,\mathrm du$, and $\sqrt{\cosh^2u-1}=\sinh u$, which is positive for $u>0$:

$$
\int\frac{\mathrm dx}{\sqrt{x^2-1}}=\int\frac{\sinh u}{\sinh u}\,\mathrm du=u+C=\cosh^{-1}x+C.
$$

The logarithmic form follows by solving $x=\cosh u=\frac12(e^u+e^{-u})$ for $u$. Multiplying by $2e^u$,

$$
e^{2u}-2x\,e^u+1=0,
$$

a quadratic in $e^u$ with roots

$$
e^u=x\pm\sqrt{x^2-1}.
$$

The branch $u\geq0$ needs $e^u\geq1$, which is the plus sign (the two roots multiply to 1), so

$$
\cosh^{-1}x=\ln\big(x+\sqrt{x^2-1}\big),\qquad\int\frac{\mathrm dx}{\sqrt{x^2-1}}=\ln\big(x+\sqrt{x^2-1}\big)+C.
$$

Exercise B(b), $\int\frac{\mathrm dx}{1+x^2}$ with $x=\tan\theta$, $-\frac\pi2<\theta<\frac\pi2$: $\mathrm dx=\sec^2\theta\,\mathrm d\theta$ and $1+\tan^2\theta=\sec^2\theta$, so

$$
\int\frac{\mathrm dx}{1+x^2}=\int\frac{\sec^2\theta}{\sec^2\theta}\,\mathrm d\theta=\theta+C=\tan^{-1}x+C.
$$

With a general $a>0$ the same substitutions scaled by $a$ give the Formula Sheet entries. For example, $x=a\tan\theta$ gives $\mathrm dx=a\sec^2\theta\,\mathrm d\theta$ and $a^2+x^2=a^2\sec^2\theta$, so

$$
\int\frac{\mathrm dx}{a^2+x^2}=\int\frac{a\sec^2\theta}{a^2\sec^2\theta}\,\mathrm d\theta=\frac\theta a+C=\frac1a\tan^{-1}\frac xa+C,
$$

and in the same way $\int\frac{\mathrm dx}{\sqrt{a^2-x^2}}=\sin^{-1}\frac xa+C$, $\int\frac{\mathrm dx}{\sqrt{a^2+x^2}}=\sinh^{-1}\frac xa+C$ and $\int\frac{\mathrm dx}{\sqrt{x^2-a^2}}=\cosh^{-1}\frac xa+C$ ([[Integration Formulae]], [[Hyperbolic Functions]]).

### The upper unit semicircle (Example 8.60)

Find $\int\sqrt{1-x^2}\,\mathrm dx$ for $0\leq x\leq1$. The direct choice $u=\sqrt{1-x^2}$ gives $\mathrm dx=-\frac ux\,\mathrm du$ and the integral $-\int\frac{u^2}{\sqrt{1-u^2}}\,\mathrm du$, which is harder than the original. Instead put $x=\sin\theta$ with $0\leq\theta\leq\frac\pi2$, so $\cos\theta\geq0$, $\sqrt{1-x^2}=\cos\theta$ and $\mathrm dx=\cos\theta\,\mathrm d\theta$:

$$
\int\sqrt{1-x^2}\,\mathrm dx=\int\cos\theta\cdot\cos\theta\,\mathrm d\theta=\int\cos^2\theta\,\mathrm d\theta.
$$

From $\cos2\theta=2\cos^2\theta-1$, $\cos^2\theta=\frac12(1+\cos2\theta)$, which was integrated in [[MATH1054 M04 - Integration I|M04]]:

$$
\int\cos^2\theta\,\mathrm d\theta=\frac12\int\big(1+\cos2\theta\big)\,\mathrm d\theta
$$

$$
=\tfrac12\theta+\tfrac14\sin2\theta+C
$$

$$
=\tfrac12\theta+\tfrac12\sin\theta\cos\theta+C.
$$

Back-substitute $\theta=\sin^{-1}x$, $\sin\theta=x$, $\cos\theta=\sqrt{1-x^2}$:

$$
\int\sqrt{1-x^2}\,\mathrm dx=\tfrac12\sin^{-1}x+\tfrac12x\sqrt{1-x^2}+C.
$$

> [!check] A quarter of the unit circle
> $\int_0^1\sqrt{1-x^2}\,\mathrm dx=\tfrac12\cdot\frac\pi2+0-0=\frac\pi4\approx0.7854$, the area of a quarter of the unit disc, as it must be since $y=\sqrt{1-x^2}$ is the upper unit semicircle.

### A hyperbolic substitution for arc lengths

Arc lengths of parabolas (Section 9) lead to $\int\sqrt{1+k^2u^2}\,\mathrm du$ with $k>0$. Put $ku=\sinh t$, so $k\,\mathrm du=\cosh t\,\mathrm dt$ and $\sqrt{1+k^2u^2}=\sqrt{1+\sinh^2t}=\cosh t$:

$$
\int\sqrt{1+k^2u^2}\,\mathrm du=\frac1k\int\cosh^2t\,\mathrm dt.
$$

The hyperbolic double-angle formula follows from the exponentials,

$$
\cosh^2t=\tfrac14\big(e^{2t}+2+e^{-2t}\big)=\tfrac12\big(1+\cosh2t\big),
$$

so, with $\sinh2t=2\sinh t\cosh t$,

$$
\frac1k\int\cosh^2t\,\mathrm dt=\frac1{2k}\Big(t+\tfrac12\sinh2t\Big)+C
$$

$$
=\frac1{2k}\big(t+\sinh t\cosh t\big)+C.
$$

Back-substituting $\sinh t=ku$, $\cosh t=\sqrt{1+k^2u^2}$, $t=\sinh^{-1}(ku)$:

$$
\int\sqrt{1+k^2u^2}\,\mathrm du=\frac u2\sqrt{1+k^2u^2}+\frac1{2k}\sinh^{-1}(ku)+C.
$$

## 4. Area between curves and the mean value

### Area

Let $f$ and $g$ be continuous with $g(x)\leq f(x)$ on $[a,b]$. A vertical strip at $x$ of width $\delta x$ has height $f(x)-g(x)$, so its area is $\delta A\approx\big[f(x)-g(x)\big]\delta x$. Summing the strips and letting the widest strip shrink to zero,

$$
A=\lim_{\delta x\to0}\sum\big[f(x_r^*)-g(x_r^*)\big]\,\delta x_r=\int_a^b\big[f(x)-g(x)\big]\,\mathrm dx.
$$

With $g=0$ (the region between $y=f(x)\geq0$ and the $x$-axis) this is $A=\int_a^by\,\mathrm dx$. Where the curve dips below the axis, $\int_a^bf\,\mathrm dx$ counts that part negatively, so split the interval at the crossings before computing a geometric area.

Specimen Test 9, Q5(i): the area under $y=\sin x$ on $[0,\pi]$ is

$$
A=\int_0^\pi\sin x\,\mathrm dx=\big[-\cos x\big]_0^\pi=1+1=2.
$$

### Mean value

Divide $[a,b]$ into $n$ strips of equal width $h=(b-a)/n$ and sample $f$ at the midpoint $x_k^*$ of each. The ordinary average of these samples is

$$
\frac1n\sum_{k=0}^{n-1}f(x_k^*)=\frac1{b-a}\sum_{k=0}^{n-1}f(x_k^*)\,h,
$$

using $\frac1n=\frac h{b-a}$. As $n\to\infty$ the sum on the right becomes an integral, which defines the mean value of $f$ on $[a,b]$:

$$
\bar f=\frac1{b-a}\int_a^bf(x)\,\mathrm dx.
$$

Rearranged, $\bar f\,(b-a)=\int_a^bf\,\mathrm dx$: the rectangle of height $\bar f$ on $[a,b]$ has the same area as the region under the curve, so the parts of the curve above the line $y=\bar f$ enclose the same area as the gaps below it.

### Exercise 131: average resistance

The resistance of a rheostat is $R=38(1+0.004\theta)\ \Omega$ at temperature $\theta\ ^\circ$C. Its mean as $\theta$ varies uniformly from $10$ to $40\ ^\circ$C is

$$
\bar R=\frac1{40-10}\int_{10}^{40}38\big(1+0.004\theta\big)\,\mathrm d\theta
$$

$$
=\frac{38}{30}\Big[\theta+0.002\theta^2\Big]_{10}^{40}
$$

$$
=\frac{38}{30}\Big[(40+3.2)-(10+0.2)\Big]
$$

$$
=\frac{38}{30}\times33=41.8\ \Omega.
$$

Because $R$ is linear in $\theta$, its mean equals its value at the midpoint, $\theta=25\ ^\circ$C: $38\times1.1=41.8\ \Omega$, which confirms the integral.

> [!warning] The mean is not the average of the end values
> For a linear function the mean equals the average of the first and last values, which is why Exercise 131 gives the same answer either way. For anything else it does not: $\sin x$ on $[0,\pi]$ has end values $0$ and $0$, but mean $\frac1\pi\int_0^\pi\sin x\,\mathrm dx=\frac2\pi\approx0.637$. Integrate.

## 5. Root mean square value

The mean of an alternating quantity over a whole cycle is zero, yet an alternating current heats a resistor as surely as a direct one. The useful measure is the root mean square: square the function, take the mean of the square, and take the square root,

$$
f_{\text{rms}}^2=\frac1{b-a}\int_a^b\big[f(x)\big]^2\,\mathrm dx,\qquad f_{\text{rms}}=\sqrt{\frac1{b-a}\int_a^b\big[f(x)\big]^2\,\mathrm dx}.
$$

For a current $i(t)$ in a resistance $R$, the instantaneous power is $Ri^2$, so the mean power is $R\,\overline{i^2}=R\,i_{\text{rms}}^2$. The RMS current is therefore the steady current that dissipates the same mean power, which is why mains voltages and currents are quoted as RMS values ([[RMS Value]]). RMS values also appear as the standard deviation of a continuous random variable and as the radius of gyration in mechanics.

### RMS of a sinusoidal current (Example 8.67)

The current $i=I\sin\theta$, with $I$ constant, over $0\leq\theta\leq2\pi$. Using $\sin^2\theta=\frac12(1-\cos2\theta)$,

$$
i_{\text{rms}}^2=\frac1{2\pi}\int_0^{2\pi}I^2\sin^2\theta\,\mathrm d\theta
$$

$$
=\frac{I^2}{2\pi}\int_0^{2\pi}\tfrac12\big(1-\cos2\theta\big)\,\mathrm d\theta
$$

$$
=\frac{I^2}{4\pi}\Big[\theta-\tfrac12\sin2\theta\Big]_0^{2\pi}
$$

$$
=\frac{I^2}{4\pi}\cdot2\pi=\frac{I^2}2,
$$

so

$$
i_{\text{rms}}=\frac I{\sqrt2}\approx0.707\,I.
$$

The mean of $i$ itself over the same cycle is $\frac1{2\pi}\int_0^{2\pi}I\sin\theta\,\mathrm d\theta=0$. The same factor $1/\sqrt2$ holds over any whole number of half-cycles, because $\sin^2\theta$ averages to $\frac12$ over every interval of length $\pi$. Read the other way, the 230 V RMS mains supply has a peak of $230\sqrt2\approx325$ V.

![[m1054_m09_mean_rms.png|800]]

## 6. Volume of a solid of revolution

Rotate the region under $y=f(x)\geq0$, $a\leq x\leq b$, through a full turn about the $x$-axis. The vertical strip at $x_r^*$ of width $\delta x_r$ sweeps a thin disc of radius $f(x_r^*)$ and thickness $\delta x_r$, whose volume is

$$
\delta V_r=\pi\big[f(x_r^*)\big]^2\,\delta x_r.
$$

Adding the discs and letting the thickest one shrink to zero,

$$
V=\lim_{\delta x\to0}\sum_r\pi\big[f(x_r^*)\big]^2\,\delta x_r=\pi\int_a^b\big[f(x)\big]^2\,\mathrm dx=\pi\int_a^by^2\,\mathrm dx.
$$

If the region lies between $y_l=g(x)$ and $y_u=f(x)$ with $0\leq g\leq f$, each strip sweeps a washer with outer radius $f$ and inner radius $g$, of volume $\pi\big(f^2-g^2\big)\,\delta x$, so

$$
V=\pi\int_a^b\Big(\big[f(x)\big]^2-\big[g(x)\big]^2\Big)\,\mathrm dx.
$$

This is not $\pi\int(f-g)^2\,\mathrm dx$: squaring the strip height would rotate a strip touching the axis, not one at height $g$ to $f$.

![[m1054_m09_strip_and_disc.png|900]]

### Specimen Test 9, Q4

The region under $y=x^2+\frac1x$ between $x=1$ and $x=2$ is rotated about the $x$-axis. Expanding the square,

$$
y^2=\Big(x^2+\frac1x\Big)^2=x^4+2x+\frac1{x^2},
$$

so

$$
V=\pi\int_1^2\Big(x^4+2x+\frac1{x^2}\Big)\,\mathrm dx
$$

$$
=\pi\Big[\frac{x^5}5+x^2-\frac1x\Big]_1^2
$$

$$
=\pi\Big[\Big(\frac{32}5+4-\frac12\Big)-\Big(\frac15+1-1\Big)\Big]
$$

$$
=\pi\Big(\frac{99}{10}-\frac{2}{10}\Big)=\frac{97\pi}{10}\approx30.47.
$$

> [!check] The sphere and the spherical cap
> Rotating the semicircle $y=\sqrt{r^2-x^2}$, $-r\leq x\leq r$, gives $V=\pi\int_{-r}^r(r^2-x^2)\,\mathrm dx=\pi\big[r^2x-\tfrac13x^3\big]_{-r}^r=\tfrac43\pi r^3$, the volume of a sphere. Keeping only $r-h\leq x\leq r$ gives a cap of height $h$ (James Example 8.66): $\pi\big[r^2x-\tfrac13x^3\big]_{r-h}^r=\tfrac13\pi h^2(3r-h)$, which equals $\tfrac23\pi r^3$ at $h=r$ (a hemisphere) and $\tfrac43\pi r^3$ at $h=2r$.

## 7. Centroid of a plane area

The centroid $(\bar x,\bar y)$ of a lamina of area $A$ is the point at which the whole area, concentrated, has the same first moments about the axes as the lamina itself:

$$
A\,\bar x=M_y=\int x\,\mathrm dA,\qquad A\,\bar y=M_x=\int y\,\mathrm dA.
$$

$M_y$ is the first moment of area about the $y$-axis (each element of area times its distance $x$ from that axis), and $M_x$ the first moment about the $x$-axis. For a uniform thin plate the centroid is the centre of gravity ([[First Moment of Area]]).

Take the region between $y=g(x)$ and $y=f(x)$, $g\leq f$, on $[a,b]$. The strip at $x_r^*$ is a thin rectangle of area $\delta A_r=\big[f(x_r^*)-g(x_r^*)\big]\delta x_r$. Its centroid is at its centre: horizontally at $x_r^*$, vertically at mid-height $\tfrac12\big[f(x_r^*)+g(x_r^*)\big]$. Its moment about the $y$-axis is therefore

$$
\delta M_{y,r}=x_r^*\big[f(x_r^*)-g(x_r^*)\big]\,\delta x_r,
$$

and summing and taking the limit,

$$
A\,\bar x=\int_a^bx\big[f(x)-g(x)\big]\,\mathrm dx.
$$

Its moment about the $x$-axis is the strip area times the height of its centroid:

$$
\delta M_{x,r}=\tfrac12\big[f(x_r^*)+g(x_r^*)\big]\cdot\big[f(x_r^*)-g(x_r^*)\big]\,\delta x_r
$$

$$
=\tfrac12\Big(\big[f(x_r^*)\big]^2-\big[g(x_r^*)\big]^2\Big)\,\delta x_r,
$$

so

$$
A\,\bar y=\frac12\int_a^b\Big(\big[f(x)\big]^2-\big[g(x)\big]^2\Big)\,\mathrm dx.
$$

For the region between $y=f(x)\geq0$ and the $x$-axis ($g=0$), with $A=\int_a^by\,\mathrm dx$,

$$
\bar x=\frac1A\int_a^bxy\,\mathrm dx,\qquad\bar y=\frac1{2A}\int_a^by^2\,\mathrm dx.
$$

The $\frac12$ in $\bar y$ comes from the strip's own centroid being at half its height: the moment of a strip of height $y$ about the $x$-axis is $(y\,\delta x)(y/2)$. The same results follow from the double integrals of [[MATH1054 M11 - Integration IV|M11]] by integrating $\mathrm dA=\mathrm dy\,\mathrm dx$ over $y$ first.

### Specimen Test 9, Q5(ii)

For the area under $y=\sin x$ on $[0,\pi]$, $A=2$ from Section 4. Integrating by parts ([[Integration by Parts]]),

$$
\int_0^\pi x\sin x\,\mathrm dx=\big[-x\cos x\big]_0^\pi+\int_0^\pi\cos x\,\mathrm dx=\pi+\big[\sin x\big]_0^\pi=\pi,
$$

so

$$
\bar x=\frac\pi2.
$$

This agrees with the symmetry of $\sin x$ about $x=\frac\pi2$. Using $\sin^2x=\frac12(1-\cos2x)$,

$$
\int_0^\pi\sin^2x\,\mathrm dx=\frac12\Big[x-\tfrac12\sin2x\Big]_0^\pi=\frac\pi2,
$$

so

$$
\bar y=\frac1{2A}\int_0^\pi\sin^2x\,\mathrm dx=\frac14\cdot\frac\pi2=\frac\pi8,
$$

and the centroid is $\big(\frac\pi2,\frac\pi8\big)\approx(1.571,\ 0.393)$.

> [!tip] Symmetry first
> If the region is symmetric about a vertical line, $\bar x$ lies on that line and only $\bar y$ needs integrating; for a solid of revolution about the $x$-axis, $\bar y=\bar z=0$ automatically. A sketch catches most remaining slips: the centroid of a convex region lies inside it, and nearer its wider or taller part.

## 8. Centre of gravity of a solid of revolution

Take the solid generated by rotating $y=f(x)\geq0$, $a\leq x\leq b$, about the $x$-axis, and assume uniform density so that the centre of gravity is the centroid of the volume. The solid is symmetric about the $x$-axis, so its centre of gravity lies on that axis:

$$
\bar Y=\bar Z=0.
$$

Each disc of Section 6 is itself symmetric about its own centre, which lies on the axis at $x_r^*$. Its moment about the plane $x=0$ is its volume times $x_r^*$:

$$
\delta M_r=x_r^*\cdot\pi\big[f(x_r^*)\big]^2\,\delta x_r.
$$

Summing and taking the limit gives $V\bar X=\pi\int_a^bx\big[f(x)\big]^2\,\mathrm dx$, so

$$
\bar X=\frac\pi V\int_a^bxy^2\,\mathrm dx,\qquad V=\pi\int_a^by^2\,\mathrm dx.
$$

For a solid generated by the region between $g$ and $f$, each washer has volume $\pi(f^2-g^2)\,\delta x$ and centre at $x$, so $\bar X=\frac\pi V\int_a^bx\big(f^2-g^2\big)\,\mathrm dx$.

> [!warning] The solid's centre of gravity is not the area's centroid
> The area centroid weights each strip by its area $y\,\delta x$; the solid weights the disc it sweeps by $\pi y^2\,\delta x$, so the wide end counts for more. For the region under $y=\sqrt{x-2}$ on $[2,5]$, $\bar x=3.8$ for the area but $\bar X=4$ for the solid. Rotating the area centroid does not give the solid's centre of gravity.

## 9. Arc length and surface area of revolution

### Arc length

Divide the curve $y=f(x)$, $a\leq x\leq b$, at points $P_0,P_1,\dots,P_n$. Between $P_k$ and $P_{k+1}$ the curve is close to its chord, the hypotenuse of a triangle with sides $\delta x$ and $\delta y$. If the chord makes an angle $\psi$ with the $x$-axis,

$$
\delta s\approx\sqrt{\delta x^2+\delta y^2}=\sec\psi\,\delta x.
$$

For a curve that is concave upwards, the true arc length between $P_k$ and $P_{k+1}$ lies between $\delta x\sec\psi_k$ and $\delta x\sec\psi_{k+1}$, where $\psi_k$ and $\psi_{k+1}$ are the tangent angles at the two ends. Summing and letting $\max\delta x\to0$, both bounds tend to the same integral, so

$$
s=\int_a^b\sec\psi\,\mathrm dx.
$$

A concave-downwards curve gives the same result. Since $\tan\psi=\frac{\mathrm dy}{\mathrm dx}$ and $\sec^2\psi=1+\tan^2\psi$, with $s$ increasing with $x$ ($\sec\psi>0$),

$$
s=\int_a^b\sqrt{1+\Big(\frac{\mathrm dy}{\mathrm dx}\Big)^2}\,\mathrm dx.
$$

![[m1054_m09_arc_element.png|700]]

### Surface area of revolution

When the element $\delta s$ is rotated about the $x$-axis it sweeps a narrow band, a slice of a cone, whose mean radius is the average $\bar y_k$ of $y$ between $P_k$ and $P_{k+1}$. Unrolled, the band is approximately a strip of length $2\pi\bar y_k$ and width $\delta s_k$, so $\delta S_k\approx2\pi\bar y_k\,\delta s_k$. Summing and taking the limit, with $y\geq0$,

$$
S=2\pi\int_a^by\sqrt{1+\Big(\frac{\mathrm dy}{\mathrm dx}\Big)^2}\,\mathrm dx.
$$

The surface area uses $\delta s$, not $\delta x$: replacing $\sqrt{1+y'^2}$ by 1 would give the area of a stack of cylinders and underestimate any sloping surface.

### The parabolic reflector (Example 8.68)

The reflector is formed by rotating $y=\sqrt x$, $0\leq x\leq1$, about the $x$-axis. With $y'=\frac1{2\sqrt x}$,

$$
1+y'^2=1+\frac1{4x},
$$

so

$$
S=2\pi\int_0^1\sqrt x\sqrt{1+\frac1{4x}}\,\mathrm dx
$$

$$
=2\pi\int_0^1\sqrt{x+\tfrac14}\,\mathrm dx
$$

$$
=2\pi\cdot\frac23\Big[\big(x+\tfrac14\big)^{3/2}\Big]_0^1
$$

$$
=\frac{4\pi}3\Big(\frac{5\sqrt5}8-\frac18\Big)
$$

$$
=\frac\pi6\big(5\sqrt5-1\big)\approx5.330.
$$

Equivalently, $\sqrt x\sqrt{1+\frac1{4x}}=\frac12\sqrt{4x+1}$, and $u=4x+1$ turns $\int_0^1\sqrt{4x+1}\,\mathrm dx$ into $\frac14\int_1^5u^{1/2}\,\mathrm du=\frac16\big(5\sqrt5-1\big)$.

### The suspension-bridge cable (Example 8.69)

The cable of a bridge of span $2l$ hangs on $y=\frac{hx^2}{l^2}-\frac{2hx}l+h$, with $x$ measured from one end and $h$ the height of the supports above the lowest point. Completing the square,

$$
y=\frac h{l^2}\big(x^2-2lx+l^2\big)=\frac h{l^2}(x-l)^2,
$$

$$
\frac{\mathrm dy}{\mathrm dx}=\frac{2h}{l^2}(x-l).
$$

Put $u=x-l$ and $k=\frac{2h}{l^2}$, so $\mathrm du=\mathrm dx$ and the limits $x=0,\,2l$ become $u=-l,\,l$:

$$
L=\int_0^{2l}\sqrt{1+\Big(\frac{\mathrm dy}{\mathrm dx}\Big)^2}\,\mathrm dx=\int_{-l}^{l}\sqrt{1+k^2u^2}\,\mathrm du.
$$

The integrand depends only on $u^2$, so it is even and

$$
L=2\int_0^l\sqrt{1+k^2u^2}\,\mathrm du.
$$

Using the result of Section 3,

$$
L=2\Big[\frac u2\sqrt{1+k^2u^2}+\frac1{2k}\sinh^{-1}(ku)\Big]_0^l
$$

$$
=l\sqrt{1+k^2l^2}+\frac1k\sinh^{-1}(kl).
$$

With $kl=\frac{2h}l$ and $\frac1k=\frac{l^2}{2h}$, and $l\sqrt{1+\frac{4h^2}{l^2}}=\sqrt{l^2+4h^2}$,

$$
L=\sqrt{l^2+4h^2}+\frac{l^2}{2h}\sinh^{-1}\frac{2h}l.
$$

> [!check] Numbers and the flat-cable limit
> For a span of 200 m ($l=100$ m) with sag $h=20$ m: $\sqrt{10000+1600}+\frac{10000}{40}\sinh^{-1}0.4=107.70+250\times0.39004=205.21$ m, which matches direct numerical integration of $\int_0^{200}\sqrt{1+y'^2}\,\mathrm dx$. As $h\to0$, $\sinh^{-1}(2h/l)\approx2h/l$, so $L\to l+l=2l$, the span.

### Summary of the strip formulae

For the region under $y=f(x)\geq0$ on $[a,b]$, rotated where needed about the $x$-axis:

| Quantity | Formula |
|---|---|
| Area | $A=\int_a^by\,\mathrm dx$ |
| Centroid of the area | $\bar x=\dfrac1A\int_a^bxy\,\mathrm dx$, $\bar y=\dfrac1{2A}\int_a^by^2\,\mathrm dx$ |
| Volume of revolution (discs) | $V=\pi\int_a^by^2\,\mathrm dx$ |
| Centre of gravity of the solid | $\bar X=\dfrac\pi V\int_a^bxy^2\,\mathrm dx$, $\bar Y=\bar Z=0$ |
| Mean value | $\bar f=\dfrac1{b-a}\int_a^bf\,\mathrm dx$ |
| RMS value | $f_{\text{rms}}=\sqrt{\dfrac1{b-a}\int_a^bf^2\,\mathrm dx}$ |
| Arc length | $s=\int_a^b\sqrt{1+y'^2}\,\mathrm dx$ |
| Surface of revolution | $S=2\pi\int_a^by\sqrt{1+y'^2}\,\mathrm dx$ |

Between two curves $y_l\leq y\leq y_u$, the strip height is $y_u-y_l$, the area moment about the $x$-axis uses $\frac12\big(y_u^2-y_l^2\big)$, and the volume is a washer, $\pi\big(y_u^2-y_l^2\big)$. A dimensional check catches many slips: $A$ is a length squared, $V$ and $\int xy\,\mathrm dx$ a length cubed, and $\bar x$, $\bar X$ and $s$ lengths.

## Worked examples

### Area, centroid, volume and centre of gravity (Example 8.65)

The region between $y=\sqrt{x-2}$, the $x$-axis and the ordinates $x=2$ and $x=5$ is rotated through $2\pi$ about the $x$-axis.

(a) The area:

$$
A=\int_2^5(x-2)^{1/2}\,\mathrm dx=\tfrac23\Big[(x-2)^{3/2}\Big]_2^5=\tfrac23\cdot3\sqrt3=2\sqrt3\approx3.464.
$$

For $\bar x$, put $u=x-2$, so $x=u+2$ and the limits become $0$ and $3$:

$$
\int_2^5x\sqrt{x-2}\,\mathrm dx=\int_0^3(u+2)\,u^{1/2}\,\mathrm du
$$

$$
=\Big[\tfrac25u^{5/2}+\tfrac43u^{3/2}\Big]_0^3
$$

$$
=\tfrac25\cdot9\sqrt3+\tfrac43\cdot3\sqrt3=\frac{18\sqrt3}5+4\sqrt3=\frac{38\sqrt3}5,
$$

$$
\bar x=\frac{38\sqrt3/5}{2\sqrt3}=\frac{19}5=3.8.
$$

For $\bar y$, $y^2=x-2$:

$$
\bar y=\frac1{2A}\int_2^5(x-2)\,\mathrm dx=\frac1{4\sqrt3}\Big[\tfrac12(x-2)^2\Big]_2^5=\frac{9/2}{4\sqrt3}=\frac{3\sqrt3}8\approx0.650.
$$

(b) The volume and centre of gravity:

$$
V=\pi\int_2^5(x-2)\,\mathrm dx=\frac{9\pi}2\approx14.14,
$$

$$
\int_2^5x(x-2)\,\mathrm dx=\Big[\frac{x^3}3-x^2\Big]_2^5=\Big(\frac{125}3-25\Big)-\Big(\frac83-4\Big)=\frac{50}3+\frac43=18,
$$

$$
\bar X=\frac\pi V\cdot18=\frac29\cdot18=4.
$$

By symmetry $\bar Y=\bar Z=0$, so the centre of gravity is $(4,0,0)$.

### Exercise 132, the region under a parabola

The region between the $x$-axis, $y=x(2-x)=2x-x^2$ and the ordinates $x=1$ and $x=2$, rotated about the $x$-axis.

(a) Area and centroid:

$$
A=\int_1^2\big(2x-x^2\big)\,\mathrm dx=\Big[x^2-\frac{x^3}3\Big]_1^2=\frac43-\frac23=\frac23,
$$

$$
\int_1^2xy\,\mathrm dx=\int_1^2\big(2x^2-x^3\big)\,\mathrm dx=\Big[\tfrac23x^3-\tfrac14x^4\Big]_1^2=\frac43-\frac5{12}=\frac{11}{12},
$$

$$
\bar x=\frac{11/12}{2/3}=\frac{11}8.
$$

With $y^2=4x^2-4x^3+x^4$,

$$
\int_1^2y^2\,\mathrm dx=\Big[\tfrac43x^3-x^4+\tfrac15x^5\Big]_1^2=\frac8{15},
$$

$$
\bar y=\frac{8/15}{2\cdot\frac23}=\frac25.
$$

(b) Volume and centre of gravity:

$$
V=\pi\cdot\frac8{15}=\frac{8\pi}{15}\approx1.676,
$$

$$
\int_1^2xy^2\,\mathrm dx=\Big[x^4-\tfrac45x^5+\tfrac16x^6\Big]_1^2=\frac7{10},
$$

$$
\bar X=\frac{\pi\cdot\frac7{10}}{\frac{8\pi}{15}}=\frac7{10}\cdot\frac{15}8=\frac{21}{16}.
$$

The centre of gravity is $\big(\frac{21}{16},0,0\big)$. The parabola falls from $y=1$ at $x=1$ to $0$ at $x=2$, so the solid's centre of gravity ($1.3125$) sits further towards the wide end than the area's centroid ($1.375$).

### Exercise 135, the region between two curves

Find the centroid of the area bounded by $y^2=4x$ and $y=2x$, and the centroid of the volume obtained by rotating it about the $x$-axis. The curves meet where $4x=4x^2$, i.e. at $x=0$ and $x=1$. On $[0,1]$ the upper curve is $y_u=2\sqrt x$ (the upper branch of the parabola) and the lower is $y_l=2x$.

Area and centroid, using strips of height $y_u-y_l$:

$$
A=\int_0^1\big(2\sqrt x-2x\big)\,\mathrm dx=\frac43-1=\frac13,
$$

$$
\bar x=\frac1A\int_0^1x\big(2\sqrt x-2x\big)\,\mathrm dx=3\Big(\frac45-\frac23\Big)=\frac25,
$$

$$
\bar y=\frac1{2A}\int_0^1\big(y_u^2-y_l^2\big)\,\mathrm dx=\frac32\int_0^1\big(4x-4x^2\big)\,\mathrm dx=\frac32\cdot\frac23=1.
$$

The centroid of the area is $\big(\frac25,1\big)$. As a check on $\bar y$, horizontal strips run from $x=y^2/4$ to $x=y/2$ for $0\leq y\leq2$, and $\bar y=\frac1A\int_0^2y\big(\frac y2-\frac{y^2}4\big)\,\mathrm dy=3\big(\frac43-1\big)=1$.

The solid is generated by washers of outer radius $y_u$ and inner radius $y_l$:

$$
V=\pi\int_0^1\big(4x-4x^2\big)\,\mathrm dx=\frac{2\pi}3,
$$

$$
\bar X=\frac\pi V\int_0^1x\big(4x-4x^2\big)\,\mathrm dx=\frac32\Big(\frac43-1\Big)=\frac12.
$$

The centroid of the volume is $\big(\frac12,0,0\big)$.

![[m1054_centroid_regions.png|900]]

## Terminology and alternative names

| Term used here | Also called | Note |
|---|---|---|
| Chain rule | Composite-function rule (James) | Read backwards, it is integration by substitution |
| Integration by substitution | Change of variable, $u$-substitution | Generalised to multiple integrals by the Jacobian ([[Jacobian and Volume Elements]]) |
| Centre of gravity of a solid | Centroid of the volume, centre of mass | The same point for a uniform solid in a uniform field |
| RMS value | Root mean square, effective value | James writes r.m.s.; electronics notes write $V_{\text{rms}}$, $I_{\text{rms}}$ |
| Arc length | Arclength (James) | |

## Links

- Parent: [[MATH1054 Mathematics for Engineering and the Environment Hub]] · Solutions: [[MATH1054 M09 Solutions - Integration II]]
- Previous: [[MATH1054 M08 - Differentiation II]] · Next: [[MATH1054 M10 - Integration III]]
- Earlier: [[MATH1054 M04 - Integration I]] (the fundamental theorem, standard integrals, power reduction); [[MATH1054 M07 - Functions]] (hyperbolic and inverse functions); [[Product, Quotient and Chain Rules]]
- Later in MATH1054: [[MATH1054 M10 - Integration III]] (partial fractions for the rational integrands left by root substitutions); [[MATH1054 M11 - Integration IV]] (centroids and volumes as double integrals); [[MATH1054 M24 - Statistics I]] (the mean of a continuous random variable is a weighted mean value)
- Year 2: [[Jacobian and Volume Elements]] (change of variable in two and three dimensions); [[Line Integrals]] (integration along a curve with the element $\mathrm ds$)
- Other modules: [[RMS Value]] and [[FEEG1004 D1 - AC Waveforms, RMS and Phasors]] (FEEG1004); [[First Moment of Area]] and [[Second Moments of Area]] (SESA2028); [[Mass Moment of Inertia and Radius of Gyration]] (FEEG1002)
- Concepts: [[Integration by Substitution]] · [[Centroids and Solids of Revolution]] · [[Hyperbolic Functions]] · [[Trigonometric Integrals and Power Reduction]] · [[Integration Formulae]]

## Sources

- MATH1054 Module Booklet, Module 9: work scheme (PDF pp. 22–24) and Specimen Test 9 (PDF p. 25).
- James, *Modern Engineering Mathematics* (6th ed.): §8.8.6 and Example 8.52 (pp. 649–650); §8.8.12, Examples 8.59, 8.60, 8.62 and Figure 8.61 (pp. 656–661); §8.9.1–8.9.6 and Examples 8.65–8.69 (pp. 665–675); Exercises 112, 115 (pp. 650–651), 122 (p. 664), 131, 132, 135 (pp. 678–679).
- [[Integration Formulae]] (module formula reference).

## Self-study tasks

### Core

- [ ] Exercise A (a)–(g), recognising the inner function (Module 09 work scheme). → [[MATH1054 M09 Solutions - Integration II#Booklet Exercise A: Recognise the inner function]] · [[#Exercise A: recognising the inner function]]
- [ ] Exercises 115(b) and (d), definite integrals with changed limits (Module 09 work scheme). → [[MATH1054 M09 Solutions - Integration II#Exercise 115]] · [[#Definite integrals with changed limits]]
- [ ] Exercise 132, area, centroid, volume and centre of gravity under $y=x(2-x)$ (Module 09 work scheme). → [[#Exercise 132, the region under a parabola]] · [[MATH1054 M09 Solutions - Integration II#Part B: Assigned exercises|solutions, Part B]]
- [ ] Exercise 135, centroids for the region between $y^2=4x$ and $y=2x$ (Module 09 work scheme). → [[#Exercise 135, the region between two curves]] · [[MATH1054 M09 Solutions - Integration II#Part B: Assigned exercises|solutions, Part B]]
- [ ] Specimen Test 9, Q3–Q5, timed. → [[MATH1054 M09 Solutions - Integration II#Part C: Specimen Test 9]]

### Further practice

- [ ] Exercise B (a) and (b), inverse-function integrals from first principles (Module 09 work scheme). → [[MATH1054 M09 Solutions - Integration II#Booklet Exercise B: From first principles with the given substitution]] · [[#The inverse-function integrals from first principles]]
- [ ] Exercises 112(h) and 122(b) (Module 09 work scheme). → [[MATH1054 M09 Solutions - Integration II#Part B: Assigned exercises|solutions, Part B]] · [[#Odd powers of sine or cosine (Exercise 122(b))]]
- [ ] Exercise 131, average resistance (Module 09 work scheme). → [[MATH1054 M09 Solutions - Integration II#Exercise 131: Average resistance]] · [[#Exercise 131: average resistance]]
- [ ] Specimen Test 9, Q1–Q2. → [[MATH1054 M09 Solutions - Integration II#Part C: Specimen Test 9]]
- [ ] Rework Examples 8.59, 8.62 and 8.69 without notes (Module 09 work scheme, items 2, 4 and 9). → [[#A root in the denominator (Example 8.59)]] · [[#A root substitution with new limits (Example 8.62)]] · [[#The suspension-bridge cable (Example 8.69)]]

## Transcript and slide slips

> [!warning] Module Booklet (Module 9) and James slips
> Where: [[#A product and a quotient (Example 8.52)]] and [[#8. Centre of gravity of a solid of revolution]].
>
> | Where | Printed | Correct |
> |---|---|---|
> | Booklet, Module 9 work scheme, item 1 (PDF p. 22) | the numerator $x+1$ of Example 8.52(b) is a multiple of the derivative of the denominator $x^2+2x+1$ | the denominator is $x^2+2x+2$, as in James and above; with $(x+1)^2$ the integral would be $\ln\lvert x+1\rvert+C$ |
> | James §8.9.3 (p. 668) | the solid of revolution "shown in Figure 8.60" | Figure 8.63 (Figure 8.60 is the storage tank of Example 8.61) |
