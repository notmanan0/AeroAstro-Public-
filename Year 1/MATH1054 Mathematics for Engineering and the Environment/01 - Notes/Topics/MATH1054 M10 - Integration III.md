---
title: "MATH1054 M10 - Integration III"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: topic
stream: "Block 1: Calculus"
order: 10
tags:
  - math1054
  - integration
  - partial-fractions
  - improper-integrals
aliases: ["MATH1054 Module 10", "Integration III"]
date: 2026-09-27
status: lectured
coverage: "Module Booklet Module 10 work scheme (completing the square, integration of rational functions by partial fractions, improper integrals) and Specimen Test 10; James §2.5.1 (pp. 114–119), §8.8.3 Exercises 105–106, §8.8.8 Examples 8.53–8.55, §8.8.9 Exercise 117, §9.2.1–9.2.3"
parent: ["[[MATH1054 Mathematics for Engineering and the Environment Hub]]"]
prerequisites: ["[[MATH1054 M09 - Integration II]]"]
next_topics: ["[[MATH1054 M11 - Integration IV]]"]
key_concepts: ["[[Partial Fractions]]", "[[Completing the Square]]", "[[Improper Integrals]]"]
tutorial_sheets: ["[[MATH1054 M10 Solutions - Integration III]]"]
sources: ["02 - Sources/Course Booklets & Solutions/Module Booklet.pdf (Module 10)", "02 - Sources/Modern Engineering Mathematics.pdf (pp.114–119, §8.8, §9.2)"]
---

# MATH1054 M10 - Integration III

> [!abstract] Summary
> Every rational function $P(x)/Q(x)$ can be integrated in closed form: divide if the fraction is improper, split $Q$ into partial fractions, and each piece integrates to a logarithm, a negative power or an inverse tangent, the last after completing the square. Completing the square also reduces $\int\mathrm dx/\sqrt{\text{quadratic}}$ to an inverse sine or inverse hyperbolic function. An improper integral, over an infinite range or of an integrand that is unbounded on the range, is defined as a limit of ordinary integrals; the benchmark is $\int x^{-p}\,\mathrm dx$, which converges at infinity only for $p>1$ and at $0$ only for $p<1$.

> [!summary]- Exam use: quick path
> - **Use it when:** the integrand is a ratio of polynomials, has a quadratic (or the square root of one) in the denominator, or the integral has an infinite limit or an integrand that blows up somewhere on the range.
> - **Assumptions:** real coefficients; logarithms of quantities that may be negative are written $\ln|\cdot|$; $k>0$ in the standard forms; for improper integrals $f$ is continuous except at the points named.
> - **Method:** 1. If $\deg P\ge\deg Q$, divide first. 2. Factorise $Q$ and write one term per power of each linear factor and $(Bx+C)$ over each irreducible quadratic. 3. Cover-up for the top power of each linear factor, compare coefficients for the rest. 4. Integrate: $\ln$, negative power, or split the numerator and complete the square for $\tan^{-1}$. 5. For an improper integral, replace each bad limit by $\varepsilon$ or $R$, integrate, take the limit, and split the range at every interior singularity.
> - **Common mistakes:** giving a repeated factor $(x-a)^2$ only one term; evaluating an antiderivative straight across a singularity inside the range, as in $\int_{-1}^1x^{-2}\,\mathrm dx\ne-2$.
> - **Practise:** [[#James Example 8.53, three factor types]] · [[MATH1054 M10 Solutions - Integration III#Exercise 117: Partial fractions|Exercise 117]]

Substitution and integration by parts ([[MATH1054 M04 - Integration I|M04]], [[MATH1054 M09 - Integration II|M09]]) work when the integrand happens to have the right shape. Rational functions are the one large class with a guaranteed method. Any proper fraction $P/Q$ is a sum of simple fractions, one group for each factor of $Q$, and each simple fraction has a known integral. The algebra that produces the split is the same algebra that inverts Laplace transforms: a system's transfer function is a ratio of polynomials in $s$, and its time response is read off term by term from the partial fractions ([[Partial Fractions for Inverse Laplace]]).

Completing the square is the tool for the irreducible quadratics that partial fractions cannot split. Shifting $x$ to the vertex of the parabola turns $x^2+bx+c$ into $u^2+k^2$, $u^2-k^2$ or $k^2-u^2$, and those three shapes give the inverse tangent, the logarithm and the inverse sine. The same identity finds the centre and radius of a circle written as $x^2+y^2+Dx+Ey+F=0$.

An improper integral asks for the area under a curve that runs off to infinity, sideways or upwards. Such areas can be finite: the work needed to lift a spacecraft from the Earth's surface to infinity is $\int_{R_E}^\infty GMm/r^2\,\mathrm dr$, which is finite and gives the escape speed. The Laplace transform $\int_0^\infty e^{-st}f(t)\,\mathrm dt$, the normalisation of a probability density over $(-\infty,\infty)$ and the period of a pendulum released from a large angle are all improper integrals. James calls a point where the integrand is unbounded an infinite discontinuity; singularity is the more common name.

---

## 1. Proper and improper rational functions (James §2.5.1)

A rational function $P(x)/Q(x)$ is **proper** when $\deg P<\deg Q$ and **improper** otherwise. Partial fractions apply only to proper fractions, so an improper one is divided first: polynomial long division gives a quotient $r(x)$ and a remainder $s(x)$ with $\deg s<\deg Q$,

$$
\frac{P(x)}{Q(x)}=r(x)+\frac{s(x)}{Q(x)} .
$$

For $\dfrac{2x^3}{x^3-1}$, write the numerator as a multiple of the denominator plus what is left:

$$
\begin{aligned}
2x^3&=2(x^3-1)+2,\\
\frac{2x^3}{x^3-1}&=2+\frac{2}{x^3-1}.
\end{aligned}
$$

The same move handles $\dfrac{x^2}{x^2+1}$:

$$
\frac{x^2}{x^2+1}=\frac{(x^2+1)-1}{x^2+1}=1-\frac{1}{x^2+1}.
$$

When the leading terms do not cancel in one step, divide properly. For $\dfrac{3x^2}{(x-1)(x+2)}$ (James Example 2.35), the denominator is $x^2+x-2$:

$$
\begin{aligned}
3x^2&=3(x^2+x-2)-3x+6,\\
\frac{3x^2}{(x-1)(x+2)}&=3+\frac{6-3x}{(x-1)(x+2)} .
\end{aligned}
$$

The remainder then splits by cover-up into $\frac{1}{x-1}-\frac{4}{x+2}$. An alternative to dividing first is to include the polynomial part as extra unknowns in the partial-fraction form, of degree $\deg P-\deg Q$: here $\frac{3x^2}{(x-1)(x+2)}=r+\frac{A}{x-1}+\frac{B}{x+2}$ with a constant $r$, found with the other constants by comparing the $x^2$ coefficients ($r=3$). Both routes give the same answer.

## 2. Why the partial-fraction forms are what they are

Each factor of $Q$ contributes its own terms:

| Factor of $Q$ | Terms |
|---|---|
| linear $(x-a)$ | $\dfrac{A}{x-a}$ |
| repeated $(x-a)^2$ | $\dfrac{A}{x-a}+\dfrac{B}{(x-a)^2}$ |
| repeated $(x-a)^k$ | $\dfrac{A_1}{x-a}+\dfrac{A_2}{(x-a)^2}+\dots+\dfrac{A_k}{(x-a)^k}$ |
| irreducible quadratic $x^2+bx+c$ ($b^2<4c$) | $\dfrac{Bx+C}{x^2+bx+c}$ |

The number of unknown constants always equals $\deg Q$. Clearing denominators gives a polynomial identity of degree below $\deg Q$, so comparing coefficients gives exactly $\deg Q$ linear equations for $\deg Q$ unknowns.

### Distinct linear factors and the cover-up rule

Let $Q(x)=(x-a)R(x)$ with $R(a)\ne0$, and let $P/Q$ be proper. Define the number

$$
A=\frac{P(a)}{R(a)} .
$$

Subtract $A/(x-a)$ from the fraction over the common denominator:

$$
\frac{P(x)}{(x-a)R(x)}-\frac{A}{x-a}=\frac{P(x)-A\,R(x)}{(x-a)R(x)} .
$$

At $x=a$ the new numerator is $P(a)-A\,R(a)=0$, so by the factor theorem it contains the factor $(x-a)$:

$$
P(x)-A\,R(x)=(x-a)S(x).
$$

Cancel the common factor:

$$
\frac{P(x)}{(x-a)R(x)}=\frac{A}{x-a}+\frac{S(x)}{R(x)} .
$$

Since $\deg P\le\deg R$, the numerator $P-AR$ has degree at most $\deg R$, so $\deg S\le\deg R-1$ and $S/R$ is again proper. Repeating the step on $S/R$ peels off one linear factor at a time, which proves the first row of the table.

The formula $A=P(a)/R(a)$ is the **cover-up rule**: delete ("cover") the factor $(x-a)$ in the denominator and substitute $x=a$ into what is left. For $\dfrac{6}{(x-4)(x+2)}$, covering $(x-4)$ and putting $x=4$ gives $A=\frac{6}{4+2}=1$; covering $(x+2)$ and putting $x=-2$ gives $B=\frac{6}{-2-4}=-1$.

### Repeated linear factors

Let $Q(x)=(x-a)^kR(x)$ with $R(a)\ne0$. The same subtraction with $A_k=P(a)/R(a)$ gives

$$
\begin{aligned}
\frac{P(x)}{(x-a)^kR(x)}-\frac{A_k}{(x-a)^k}&=\frac{P(x)-A_kR(x)}{(x-a)^kR(x)}\\
&=\frac{(x-a)S(x)}{(x-a)^kR(x)}\\
&=\frac{S(x)}{(x-a)^{k-1}R(x)} .
\end{aligned}
$$

The power of $(x-a)$ has dropped by one, and the remainder is still proper. Repeating $k$ times produces

$$
\frac{P(x)}{(x-a)^kR(x)}=\frac{A_k}{(x-a)^k}+\frac{A_{k-1}}{(x-a)^{k-1}}+\dots+\frac{A_1}{x-a}+\frac{T(x)}{R(x)},
$$

so every power from $1$ to $k$ appears. Cover-up on the original fraction gives only the top coefficient $A_k$; the lower ones come from comparing coefficients or substituting other values of $x$.

A single term $A/(x-a)^2$ is not enough because the lower power is genuinely present. For $\dfrac{x}{(x+1)^2}$, rewrite the numerator in powers of $(x+1)$:

$$
\frac{x}{(x+1)^2}=\frac{(x+1)-1}{(x+1)^2}=\frac{1}{x+1}-\frac{1}{(x+1)^2} .
$$

![[m1054_m10_partial_fraction_terms.png|900]]

The figure shows $\dfrac{9}{(x-1)(x+2)^2}=\dfrac{1}{x-1}-\dfrac{1}{x+2}-\dfrac{3}{(x+2)^2}$ (James Example 8.53(b)). Near the double pole $x=-2$ the function goes to $-\infty$ on both sides, which only the squared term can do, while the $-1/(x+2)$ term changes sign across the pole and corrects the shape away from it.

### Irreducible quadratic factors

A quadratic $x^2+bx+c$ with $b^2<4c$ has no real roots, so there is no real $x$ to cover up. Over the complex numbers it factorises as $(x-\alpha)(x-\bar\alpha)$, and the linear-factor argument still works, giving two terms $A/(x-\alpha)$ and $A'/(x-\bar\alpha)$. Writing $Q=(x-\alpha)R$ gives $Q'(\alpha)=R(\alpha)$, so the cover-up values are $A=P(\alpha)/Q'(\alpha)$ and $A'=P(\bar\alpha)/Q'(\bar\alpha)$. Because $P$ and $Q$ have real coefficients, $A'=\overline{P(\alpha)/Q'(\alpha)}=\bar A$. Combine the conjugate pair:

$$
\begin{aligned}
\frac{A}{x-\alpha}+\frac{\bar A}{x-\bar\alpha}&=\frac{A(x-\bar\alpha)+\bar A(x-\alpha)}{(x-\alpha)(x-\bar\alpha)}\\
&=\frac{(A+\bar A)\,x-(A\bar\alpha+\bar A\alpha)}{x^2+bx+c}\\
&=\frac{2\,\mathrm{Re}(A)\,x-2\,\mathrm{Re}(A\bar\alpha)}{x^2+bx+c} .
\end{aligned}
$$

Both coefficients are real, so the pair is $\dfrac{Bx+C}{x^2+bx+c}$ with real $B$ and $C$: an irreducible quadratic needs a **linear** numerator, not a constant. For $\frac{2}{x^3-1}$, with $\alpha=-\frac12+\frac{\sqrt3}{2}\mathrm i$, this gives $A=-\frac13+\frac{\sqrt3}{3}\mathrm i$, hence $B=-\frac23$ and $C=-\frac43$, the same values found by real algebra in [[#Exercise 117]].

A constant numerator fails the unknown count. Trying $\frac{2}{(x-1)(x^2+x+1)}=\frac{A}{x-1}+\frac{C}{x^2+x+1}$ means $2=A(x^2+x+1)+C(x-1)$; the $x^2$ coefficients give $A=0$, then the $x$ coefficients give $C=0$, and the constants give $0=2$. Two unknowns cannot satisfy three equations.

### Finding the constants in practice

Multiply through by $Q(x)$. The result is an identity between polynomials, true for every $x$, including the roots of $Q$ where the original fractions are undefined (both sides are continuous polynomials). Three tools then find the constants:

1. cover-up, or equivalently substituting $x=a$, for the top-power coefficient of each linear factor;
2. comparing coefficients of equal powers of $x$, legitimate because two polynomials equal for all $x$ have equal coefficients; the highest power and the constant term are usually quickest;
3. substituting any other convenient value of $x$.

The cover-up rule is fast but covers only some of the constants, and for a fraction with several repeated or quadratic factors the general route (clear denominators, then compare coefficients) is not much slower.

> [!check] A spot value
> Check a decomposition at a value of $x$ not used to find the constants. For James Example 2.32, $\frac{2x+1}{(x-2)(x+1)(x-3)}=-\frac{5/3}{x-2}-\frac{1/12}{x+1}+\frac{7/4}{x-3}$, and at $x=1$ both sides equal $\frac34$.

## 3. Integrating each partial fraction (James §8.8.8)

A simple linear term integrates to a logarithm. With $u=x-a$,

$$
\int\frac{\mathrm dx}{x-a}=\int\frac{\mathrm du}{u}=\ln|x-a|+C .
$$

The modulus is needed because the fraction is defined on both sides of $a$: for $u<0$, $\frac{\mathrm d}{\mathrm du}\ln(-u)=\frac{-1}{-u}=\frac1u$, so $\ln|u|$ is an antiderivative on each side. A term from a repeated factor integrates by the power rule, for $n\ge2$:

$$
\int\frac{\mathrm dx}{(x-a)^n}=\frac{(x-a)^{1-n}}{1-n}+C=-\frac{1}{(n-1)(x-a)^{n-1}}+C,
$$

so in particular $\int\frac{\mathrm dx}{(x-a)^2}=-\frac{1}{x-a}+C$.

A quadratic term $\dfrac{Bx+C}{x^2+bx+c}$ is split so that one part has the derivative of the denominator, $2x+b$, on top:

$$
Bx+C=\frac B2(2x+b)+\Big(C-\frac{Bb}{2}\Big).
$$

The first part is of the form $f'/f$ and gives a logarithm; no modulus is needed because $x^2+bx+c>0$ when $b^2<4c$. The second part is a constant over the quadratic, which [[#4. Completing the square and the standard forms]] turns into an inverse tangent. With $k^2=c-\frac{b^2}{4}>0$,

$$
\int\frac{Bx+C}{x^2+bx+c}\,\mathrm dx=\frac B2\ln(x^2+bx+c)+\frac{C-\frac{Bb}{2}}{k}\tan^{-1}\frac{x+\frac b2}{k}+\text{const}.
$$

For example (Module 10 work scheme, §3), $\int\frac{2x}{x^2+2x+5}\,\mathrm dx$ has $2x=(2x+2)-2$:

$$
\begin{aligned}
\int\frac{2x}{x^2+2x+5}\,\mathrm dx&=\int\frac{2x+2}{x^2+2x+5}\,\mathrm dx-2\int\frac{\mathrm dx}{(x+1)^2+2^2}\\
&=\ln|x^2+2x+5|-2\cdot\frac12\tan^{-1}\frac{x+1}{2}+c\\
&=\ln|x^2+2x+5|-\tan^{-1}\frac{x+1}{2}+c .
\end{aligned}
$$

The first integral uses the substitution $u=x^2+2x+5$, $\mathrm du=(2x+2)\,\mathrm dx$; the second is the integral evaluated in [[#Worked examples: completing the square]].

## 4. Completing the square and the standard forms

### The identity

Take out the leading coefficient, then add and subtract the square of half the new $x$ coefficient:

$$
\begin{aligned}
ax^2+bx+c&=a\Big[x^2+\frac bax+\frac ca\Big]\\
&=a\Big[\Big(x+\frac b{2a}\Big)^2-\frac{b^2}{4a^2}+\frac ca\Big]\\
&=a\Big[\Big(x+\frac b{2a}\Big)^2+\frac{4ac-b^2}{4a^2}\Big].
\end{aligned}
$$

With $u=x+\frac{b}{2a}$ the quadratic is $a(u^2+k^2)$ when $b^2<4ac$, with $k^2=\frac{4ac-b^2}{4a^2}$, and $a(u^2-k^2)$ when $b^2>4ac$. A negative leading coefficient gives $k^2-u^2$ after taking out $-1$: for example

$$
3+2x-x^2=-\big(x^2-2x-3\big)=-\big[(x-1)^2-4\big]=4-(x-1)^2 .
$$

![[m1054_m10_completing_square.png|900]]

The vertex of the parabola is at $x=-\frac{b}{2a}$, so completing the square is a shift of origin to the vertex. The figure shows the three outcomes for quadratics from the work scheme: no real roots ($\tan^{-1}$), a downward parabola positive between its roots (a square root of it gives $\sin^{-1}$), and two real roots, where the quadratic factorises and partial fractions give logarithms.

### The standard integrals, derived

Each form is reduced to a basic integral by a substitution matched to an identity; throughout $k>0$.

For $u^2+k^2$, put $u=k\tan\theta$ with $-\frac\pi2<\theta<\frac\pi2$, so $\mathrm du=k\sec^2\theta\,\mathrm d\theta$ and $u^2+k^2=k^2\sec^2\theta$:

$$
\begin{aligned}
\int\frac{\mathrm du}{u^2+k^2}&=\int\frac{k\sec^2\theta}{k^2\sec^2\theta}\,\mathrm d\theta\\
&=\frac{\theta}{k}+C\\
&=\frac1k\tan^{-1}\frac uk+C .
\end{aligned}
$$

For $\sqrt{k^2-u^2}$, defined for $|u|<k$, put $u=k\sin\theta$ with $-\frac\pi2\le\theta\le\frac\pi2$, where $\cos\theta\ge0$, so $\sqrt{k^2-u^2}=k\cos\theta$ and $\mathrm du=k\cos\theta\,\mathrm d\theta$:

$$
\int\frac{\mathrm du}{\sqrt{k^2-u^2}}=\int\frac{k\cos\theta}{k\cos\theta}\,\mathrm d\theta=\theta+C=\sin^{-1}\frac uk+C .
$$

For $u^2-k^2$ without a square root, the quadratic factorises and cover-up gives $\frac{1}{(u-k)(u+k)}=\frac{1/(2k)}{u-k}-\frac{1/(2k)}{u+k}$, so

$$
\int\frac{\mathrm du}{u^2-k^2}=\frac{1}{2k}\ln\Big|\frac{u-k}{u+k}\Big|+C .
$$

For $\sqrt{u^2+k^2}$, put $u=k\sinh t$, so $\mathrm du=k\cosh t\,\mathrm dt$ and $\sqrt{k^2\sinh^2t+k^2}=k\cosh t$ (positive). The integrand becomes $1$, and

$$
\int\frac{\mathrm du}{\sqrt{u^2+k^2}}=t+C=\sinh^{-1}\frac uk+C=\ln\big(u+\sqrt{u^2+k^2}\big)+C' .
$$

For $\sqrt{u^2-k^2}$ with $u>k$, put $u=k\cosh t$ with $t>0$, so $\sqrt{u^2-k^2}=k\sinh t$, and the same steps give $\cosh^{-1}\frac uk+C$.

| Form after completing the square | Integral |
|---|---|
| $\dfrac1{u^2+k^2}$ | $\dfrac1k\tan^{-1}\dfrac uk$ |
| $\dfrac1{u^2-k^2}$ | $\dfrac1{2k}\ln\Big\lvert\dfrac{u-k}{u+k}\Big\rvert$ |
| $\dfrac1{\sqrt{k^2-u^2}}$ | $\sin^{-1}\dfrac uk$ |
| $\dfrac1{\sqrt{u^2+k^2}}$ | $\sinh^{-1}\dfrac uk$ |
| $\dfrac1{\sqrt{u^2-k^2}}$ | $\cosh^{-1}\dfrac uk$ |

The formula sheet writes $a$ for $k$. Where only the $k=1$ form $\int\frac{\mathrm dv}{1+v^2}=\tan^{-1}v$ is available, the substitution $u=kv$ rescales the denominator to a multiple of $1+v^2$. For $\int\frac{\mathrm dx}{x^2+16}$, put $x=4v$, $\mathrm dx=4\,\mathrm dv$:

$$
\int\frac{4\,\mathrm dv}{16v^2+16}=\frac14\int\frac{\mathrm dv}{v^2+1}=\frac14\tan^{-1}v+c=\frac14\tan^{-1}\frac x4+c .
$$

### Worked examples: completing the square

In $\int\frac{\mathrm dx}{x^2+2x+5}$ (Module 10 work scheme, §1), the quadratic has $b^2-4ac=4-20<0$, so

$$
x^2+2x+5=x^2+2x+1+4=(x+1)^2+2^2 .
$$

Put $x+1=2u$, $\mathrm dx=2\,\mathrm du$:

$$
\begin{aligned}
\int\frac{\mathrm dx}{(x+1)^2+2^2}&=\int\frac{2\,\mathrm du}{(2u)^2+2^2}\\
&=\int\frac{2\,\mathrm du}{2^2(u^2+1)}\\
&=\frac12\tan^{-1}u+c=\frac12\tan^{-1}\frac{x+1}{2}+c .
\end{aligned}
$$

Exercise 105(e), $\int_0^2\frac{\mathrm dx}{\sqrt{3+2x-x^2}}$, uses $3+2x-x^2=4-(x-1)^2$, which is positive for $-1<x<3$ and so on the whole range. With $u=x-1$ and $k=2$:

$$
\begin{aligned}
\int_0^2\frac{\mathrm dx}{\sqrt{4-(x-1)^2}}&=\Big[\sin^{-1}\frac{x-1}{2}\Big]_0^2\\
&=\sin^{-1}\tfrac12-\sin^{-1}\big(-\tfrac12\big)\\
&=\frac\pi6+\frac\pi6=\frac\pi3 .
\end{aligned}
$$

Exercise 106(f) has $2x-x^2=1-(x-1)^2$, so for $0<x<2$

$$
\int\frac{\mathrm dx}{\sqrt{2x-x^2}}=\int\frac{\mathrm dx}{\sqrt{1-(x-1)^2}}=\sin^{-1}(x-1)+C .
$$

Exercise 106(l) has $x^2+6x+13=(x+3)^2+4$, so with $u=x+3$ and $k=2$

$$
\int\frac{\mathrm dx}{x^2+6x+13}=\frac12\tan^{-1}\frac{x+3}{2}+C .
$$

Specimen Test 10, Q1 has a leading coefficient that is a perfect square, which suggests completing the square in $2x$:

$$
4x^2+4x+2=(2x)^2+2(2x)+1+1=(2x+1)^2+1 .
$$

With $u=2x+1$, $\mathrm du=2\,\mathrm dx$:

$$
\int\frac{\mathrm dx}{4x^2+4x+2}=\frac12\int\frac{\mathrm du}{u^2+1}=\frac12\tan^{-1}(2x+1)+C .
$$

## 5. Worked examples: rational functions (James Examples 8.53 and 8.55)

### James Example 8.53, three factor types

(a) $\int\frac{6}{x^2-2x-8}\,\mathrm dx$. The denominator factorises as $(x-4)(x+2)$, and cover-up gave $A=1$, $B=-1$ in [[#Distinct linear factors and the cover-up rule]]:

$$
\int\Big(\frac{1}{x-4}-\frac{1}{x+2}\Big)\mathrm dx=\ln|x-4|-\ln|x+2|+C=\ln\Big|\frac{x-4}{x+2}\Big|+C .
$$

(b) $\int\frac{9}{(x-1)(x+2)^2}\,\mathrm dx$. The repeated factor needs both powers:

$$
\frac{9}{(x-1)(x+2)^2}=\frac{A}{x-1}+\frac{B}{x+2}+\frac{C}{(x+2)^2},
$$

$$
9=A(x+2)^2+B(x-1)(x+2)+C(x-1).
$$

Cover-up at $x=1$ gives $A=\frac{9}{(1+2)^2}=1$, and at $x=-2$ (covering the whole $(x+2)^2$) gives $C=\frac{9}{-2-1}=-3$. Compare the $x^2$ coefficients: $0=A+B$, so $B=-1$. Then

$$
\begin{aligned}
\int\Big(\frac{1}{x-1}-\frac{1}{x+2}-\frac{3}{(x+2)^2}\Big)\mathrm dx&=\ln|x-1|-\ln|x+2|+\frac{3}{x+2}+C\\
&=\ln\Big|\frac{x-1}{x+2}\Big|+\frac{3}{x+2}+C .
\end{aligned}
$$

(c) $\int_0^6\frac{\mathrm dx}{x^2+5x+6}$. Here $\frac{1}{(x+2)(x+3)}=\frac{1}{x+2}-\frac{1}{x+3}$ by cover-up. Both factors are positive on $[0,6]$, so the moduli can be dropped:

$$
\begin{aligned}
\int_0^6\frac{\mathrm dx}{x^2+5x+6}&=\Big[\ln\frac{x+2}{x+3}\Big]_0^6\\
&=\ln\frac89-\ln\frac23\\
&=\ln\Big(\frac89\cdot\frac32\Big)=\ln\frac43\approx0.2877 .
\end{aligned}
$$

### Exercise 117

(a) $\frac{x}{x^2-3x-4}=\frac{x}{(x-4)(x+1)}$. Cover-up gives $A=\frac{4}{4+1}=\frac45$ at $x=4$ and $B=\frac{-1}{-1-4}=\frac15$ at $x=-1$:

$$
\int\frac{x}{x^2-3x-4}\,\mathrm dx=\frac45\ln|x-4|+\frac15\ln|x+1|+C .
$$

(d) $\frac{x}{x^2+2x+1}=\frac{x}{(x+1)^2}$ is the repeated-factor example of [[#Repeated linear factors]], $\frac{1}{x+1}-\frac{1}{(x+1)^2}$:

$$
\int\frac{x}{(x+1)^2}\,\mathrm dx=\ln|x+1|+\frac{1}{x+1}+C .
$$

(f) $\frac{1}{x^2(x-1)}=\frac Ax+\frac{B}{x^2}+\frac{C}{x-1}$, so $1=Ax(x-1)+B(x-1)+Cx^2$. Then $x=0$ gives $B=-1$; $x=1$ gives $C=1$; the $x^2$ coefficients give $0=A+C$, so $A=-1$:

$$
\int\Big(-\frac1x-\frac{1}{x^2}+\frac{1}{x-1}\Big)\mathrm dx=\ln\Big|\frac{x-1}{x}\Big|+\frac1x+C .
$$

(i) $\frac{2x^3}{x^3-1}$ is improper; [[#1. Proper and improper rational functions (James §2.5.1)]] gave $2+\frac{2}{x^3-1}$. Factorise $x^3-1=(x-1)(x^2+x+1)$; the quadratic has $b^2-4c=-3<0$, so it takes a linear numerator:

$$
\frac{2}{(x-1)(x^2+x+1)}=\frac{A}{x-1}+\frac{Bx+C}{x^2+x+1},
$$

$$
2=A(x^2+x+1)+(Bx+C)(x-1).
$$

At $x=1$, $2=3A$, so $A=\frac23$. The $x^2$ coefficients give $0=A+B$, so $B=-\frac23$. The constants give $2=A-C$, so $C=-\frac43$. The quadratic term is therefore $-\frac23\cdot\frac{x+2}{x^2+x+1}$. Split its numerator around $2x+1$ and complete the square, $x^2+x+1=(x+\frac12)^2+\frac34$:

$$
\begin{aligned}
x+2&=\tfrac12(2x+1)+\tfrac32,\\
\int\frac{x+2}{x^2+x+1}\,\mathrm dx&=\frac12\ln(x^2+x+1)+\frac32\int\frac{\mathrm dx}{(x+\frac12)^2+\frac34}\\
&=\frac12\ln(x^2+x+1)+\frac32\cdot\frac{2}{\sqrt3}\tan^{-1}\frac{x+\frac12}{\sqrt3/2}\\
&=\frac12\ln(x^2+x+1)+\sqrt3\tan^{-1}\frac{2x+1}{\sqrt3} .
\end{aligned}
$$

Multiply by $-\frac23$ and add the other terms:

$$
\int\frac{2x^3}{x^3-1}\,\mathrm dx=2x+\frac23\ln|x-1|-\frac13\ln(x^2+x+1)-\frac{2}{\sqrt3}\tan^{-1}\frac{2x+1}{\sqrt3}+C .
$$

So the full decomposition is $\frac{2x^3}{x^3-1}=2+\frac{2/3}{x-1}-\frac23\cdot\frac{x+2}{x^2+x+1}$.

> [!check] SymPy
> `apart` reproduces every decomposition in this section, and differentiating each antiderivative returns the integrand exactly, including the long one for 117(i).

### Specimen Test 10, Q2 and Q3

Q2(i): $\frac{2x+1}{(x+2)(x+1)}=\frac{A}{x+2}+\frac{B}{x+1}$. Cover-up gives $A=\frac{-4+1}{-2+1}=3$ and $B=\frac{-2+1}{-1+2}=-1$:

$$
\int\frac{2x+1}{(x+2)(x+1)}\,\mathrm dx=3\ln|x+2|-\ln|x+1|+C .
$$

Q2(ii): write the numerator in powers of $(x+2)$, $x+3=(x+2)+1$:

$$
\int\frac{x+3}{(x+2)^2}\,\mathrm dx=\int\Big(\frac{1}{x+2}+\frac{1}{(x+2)^2}\Big)\mathrm dx=\ln|x+2|-\frac{1}{x+2}+C .
$$

Q3: the fraction is improper, and $\frac{x^2}{x^2+1}=1-\frac{1}{x^2+1}$:

$$
\int\frac{x^2}{x^2+1}\,\mathrm dx=x-\tan^{-1}x+C .
$$

### Every factor type at once (James Example 8.55)

Evaluate $\int_0^1\frac{2}{(1+x)^2(1+x^2)}\,\mathrm dx$. The form is

$$
\frac{2}{(1+x)^2(1+x^2)}=\frac{A}{1+x}+\frac{B}{(1+x)^2}+\frac{Cx+D}{1+x^2},
$$

$$
2=A(1+x)(1+x^2)+B(1+x^2)+(Cx+D)(1+x)^2 .
$$

At $x=-1$, $2=2B$, so $B=1$ (the cover-up value $\frac{2}{1+1}$). Expand and compare coefficients:

$$
\begin{aligned}
x^3&:\quad A+C=0,\\
x^1&:\quad A+C+2D=0,\\
x^0&:\quad A+B+D=2 .
\end{aligned}
$$

The first two give $D=0$, then $A=2-B=1$ and $C=-1$. The $x^2$ equation, $A+B+2C+D=0$, checks. Integrate, with every argument positive on $[0,1]$:

$$
\begin{aligned}
\int_0^1\Big(\frac{1}{1+x}+\frac{1}{(1+x)^2}-\frac{x}{1+x^2}\Big)\mathrm dx&=\Big[\ln(1+x)-\frac{1}{1+x}-\frac12\ln(1+x^2)\Big]_0^1\\
&=\Big(\ln2-\frac12-\frac12\ln2\Big)-(0-1-0)\\
&=\frac12+\frac12\ln2\approx0.8466 .
\end{aligned}
$$

## 6. Improper integrals as limits (James §9.2)

The definite integral $\int_a^bf\,\mathrm dx$ of [[MATH1054 M04 - Integration I|M04]] assumes a finite range and a bounded, piecewise-continuous integrand. An **improper integral** breaks one of these: the integrand is unbounded at some point of the range (a singularity), or the range is infinite. Either way it is defined as a limit of proper integrals, and it **converges** if the limit exists and is finite, and **diverges** (is not defined) otherwise.

For a singularity at the lower limit $a$ only, and similarly at the upper limit $b$ only,

$$
\int_a^bf\,\mathrm dx=\lim_{\varepsilon\to0^+}\int_{a+\varepsilon}^bf\,\mathrm dx,\qquad\int_a^bf\,\mathrm dx=\lim_{\varepsilon\to0^+}\int_a^{b-\varepsilon}f\,\mathrm dx .
$$

For example, with $f$ unbounded at $0$, $\int_0^1f\,\mathrm dx=\lim_{\varepsilon\to0^+}\int_\varepsilon^1f\,\mathrm dx$. For a singularity at an interior point $c$, $a<c<b$, split the range there and require both pieces to converge separately:

$$
\int_a^bf\,\mathrm dx=\lim_{\varepsilon\to0^+}\int_a^{c-\varepsilon}f\,\mathrm dx+\lim_{\delta\to0^+}\int_{c+\delta}^bf\,\mathrm dx .
$$

For an infinite range,

$$
\int_a^\infty f\,\mathrm dx=\lim_{R\to\infty}\int_a^Rf\,\mathrm dx,\qquad\int_{-\infty}^bf\,\mathrm dx=\lim_{R\to\infty}\int_{-R}^bf\,\mathrm dx,
$$

and a doubly infinite integral is split at any convenient point $c$, $\int_{-\infty}^\infty=\int_{-\infty}^c+\int_c^\infty$, with both halves required to converge. The two limits are independent: $\lim_{R\to\infty}\int_{-R}^{R}x\,\mathrm dx=0$, yet $\int_{-\infty}^\infty x\,\mathrm dx$ diverges because neither half converges.

A singularity can sit inside a perfectly physical quantity. The period of a simple pendulum of length $l$ released from rest at angle $\alpha$ is

$$
T(\alpha)=2\sqrt{\frac lg}\int_0^\alpha\frac{\mathrm d\theta}{\sqrt{\sin^2\frac\alpha2-\sin^2\frac\theta2}},
$$

whose integrand is infinite at $\theta=\alpha$, the turning point, yet the integral converges; for $\alpha=\frac\pi3$ it is $T=6.743\sqrt{l/g}$, about 7% above the small-angle value $2\pi\sqrt{l/g}$ (James Example 9.3).

### Standard limits

Three limits recur when the bad end is taken to its limit.

The product $\varepsilon\ln\varepsilon$ is of the form $0\times(-\infty)$. Rewrite it as $\infty/\infty$ and apply [[L'Hôpital's Rule]]:

$$
\lim_{\varepsilon\to0^+}\varepsilon\ln\varepsilon=\lim_{\varepsilon\to0^+}\frac{\ln\varepsilon}{1/\varepsilon}=\lim_{\varepsilon\to0^+}\frac{1/\varepsilon}{-1/\varepsilon^2}=\lim_{\varepsilon\to0^+}(-\varepsilon)=0 .
$$

For a positive integer $n$, $R^ne^{-R}=R^n/e^R$ is $\infty/\infty$; L'Hôpital $n$ times reduces the numerator to $n!$ while the denominator stays $e^R$:

$$
\lim_{R\to\infty}\frac{R^n}{e^R}=\lim_{R\to\infty}\frac{nR^{n-1}}{e^R}=\dots=\lim_{R\to\infty}\frac{n!}{e^R}=0 .
$$

Finally $\tan\theta\to\infty$ as $\theta\to\frac\pi2^-$, so $\tan^{-1}R\to\frac\pi2$ as $R\to\infty$.

## 7. The p-integrals and convergence

The integrals of $x^{-p}$ are the reference cases for both kinds. For $p\ne1$, on an infinite range,

$$
\begin{aligned}
\int_1^Rx^{-p}\,\mathrm dx&=\Big[\frac{x^{1-p}}{1-p}\Big]_1^R\\
&=\frac{R^{1-p}-1}{1-p} .
\end{aligned}
$$

If $p>1$ the exponent $1-p$ is negative, $R^{1-p}\to0$, and the integral converges to $\frac{1}{p-1}$. If $p<1$, $R^{1-p}\to\infty$ and it diverges. If $p=1$, $\int_1^R\frac{\mathrm dx}{x}=\ln R\to\infty$, which also diverges.

Near the origin the inequalities reverse. For $p\ne1$,

$$
\begin{aligned}
\int_\varepsilon^1x^{-p}\,\mathrm dx&=\Big[\frac{x^{1-p}}{1-p}\Big]_\varepsilon^1\\
&=\frac{1-\varepsilon^{1-p}}{1-p} .
\end{aligned}
$$

If $p<1$, $\varepsilon^{1-p}\to0$ and the integral converges to $\frac{1}{1-p}$. If $p>1$, $\varepsilon^{1-p}\to\infty$ and it diverges. If $p=1$, $\int_\varepsilon^1\frac{\mathrm dx}{x}=-\ln\varepsilon\to\infty$.

| Integral | Converges iff | Value when it converges |
|---|---|---|
| $\displaystyle\int_1^\infty\frac{\mathrm dx}{x^p}$ | $p>1$ | $\dfrac{1}{p-1}$ |
| $\displaystyle\int_0^1\frac{\mathrm dx}{x^p}$ | $p<1$ | $\dfrac{1}{1-p}$ |

So $p=1$, the logarithm, diverges at both ends, and no single power converges at both ends.

![[m1054_improper_integrals.png|760]]

> [!tip] What the p-test measures
> At infinity the tail has to fall faster than $1/x$; at a singularity the spike has to be milder than $1/x$. A positive integrand that is smaller than a convergent benchmark converges too, because its partial integrals increase and are bounded: $0\le e^{-x}|\sin x|\le e^{-x}$ on $[0,\infty)$, for instance. Comparison is not part of the Module 10 work scheme, but it is the quickest way to predict convergence before integrating.

## 8. Worked examples: improper integrals

### James Example 9.1, singular endpoints

(a) $\int_0^1x^{-2/3}\,\mathrm dx$ is singular at $0$, with $p=\frac23<1$:

$$
\int_\varepsilon^1x^{-2/3}\,\mathrm dx=\big[3x^{1/3}\big]_\varepsilon^1=3-3\varepsilon^{1/3}\to3 .
$$

(b) $\int_0^1\frac{\mathrm dx}{\sqrt{1-x^2}}$ is singular at the upper limit $x=1$:

$$
\int_0^{1-\varepsilon}\frac{\mathrm dx}{\sqrt{1-x^2}}=\sin^{-1}(1-\varepsilon)\to\sin^{-1}1=\frac\pi2 .
$$

(c) $\int_0^1\ln x\,\mathrm dx$ is singular at $0$. By parts with $u=\ln x$, $v'=1$, $\int\ln x\,\mathrm dx=x\ln x-x$:

$$
\begin{aligned}
\int_\varepsilon^1\ln x\,\mathrm dx&=\big[x\ln x-x\big]_\varepsilon^1\\
&=(0-1)-(\varepsilon\ln\varepsilon-\varepsilon)\\
&\to-1,
\end{aligned}
$$

using $\varepsilon\ln\varepsilon\to0$. The value is negative because $\ln x<0$ on $(0,1)$.

(d) $\int_0^1x^{-2}\,\mathrm dx$, with $p=2\ge1$:

$$
\int_\varepsilon^1x^{-2}\,\mathrm dx=\Big[-\frac1x\Big]_\varepsilon^1=-1+\frac1\varepsilon\to\infty,
$$

so the integral diverges and is not defined. With $\varepsilon=0.1$, $0.01$ and $0.001$ the partial integrals are $9$, $99$ and $999$.

### James Example 9.2, an interior singularity

$\int_{-1}^1x^{-2}\,\mathrm dx$ has its singularity at the interior point $x=0$, so split there:

$$
\int_{-1}^1x^{-2}\,\mathrm dx=\lim_{\varepsilon\to0^+}\int_{-1}^{-\varepsilon}x^{-2}\,\mathrm dx+\lim_{\delta\to0^+}\int_\delta^1x^{-2}\,\mathrm dx .
$$

The second piece diverges by Example 9.1(d), and the first is its mirror image, $\big[-\frac1x\big]_{-1}^{-\varepsilon}=\frac1\varepsilon-1\to\infty$. Neither limit exists, so the integral is not defined.

![[m1054_m10_interior_singularity.png|900]]

> [!warning] Interior singularities
> Split at every point where the integrand blows up. Ignoring the singularity gives $\big[-\frac1x\big]_{-1}^{1}=-1-1=-2$, a negative answer for a positive integrand, so it is obviously wrong. The fundamental theorem needs an antiderivative that is continuous on the whole range, and $-1/x$ jumps through infinity at $0$.

### James Example 9.4, infinite ranges

(a) $\int_1^\infty x^{-3/2}\,\mathrm dx$, with $p=\frac32>1$:

$$
\int_1^Rx^{-3/2}\,\mathrm dx=\Big[-2x^{-1/2}\Big]_1^R=2-\frac{2}{\sqrt R}\to2 .
$$

(b) $\int_0^\infty\frac{\mathrm dx}{1+x^2}$:

$$
\int_0^R\frac{\mathrm dx}{1+x^2}=\tan^{-1}R-\tan^{-1}0=\tan^{-1}R\to\frac\pi2 .
$$

(c) $\int_0^\infty e^{-x}\sin x\,\mathrm dx$. Let $I=\int e^{-x}\sin x\,\mathrm dx$ and integrate by parts twice, integrating $e^{-x}$ each time:

$$
\begin{aligned}
I&=-e^{-x}\sin x+\int e^{-x}\cos x\,\mathrm dx\\
&=-e^{-x}\sin x-e^{-x}\cos x-\int e^{-x}\sin x\,\mathrm dx\\
&=-e^{-x}(\sin x+\cos x)-I,
\end{aligned}
$$

so $I=-\frac12e^{-x}(\sin x+\cos x)$, the cyclic by-parts result of [[MATH1054 M04 - Integration I|M04]]. Then

$$
\int_0^Re^{-x}\sin x\,\mathrm dx=\Big[-\tfrac12e^{-x}(\sin x+\cos x)\Big]_0^R=\frac12-\frac12e^{-R}(\sin R+\cos R)\to\frac12 .
$$

The limit of $\sin R+\cos R$ does not exist, but it is bounded ($|\sin R+\cos R|\le\sqrt2$) and multiplied by $e^{-R}\to0$.

(d) $\int_{-\infty}^\infty e^{3x}\exp(-e^x)\,\mathrm dx$. Let $u=e^x$, so $\mathrm du=e^x\,\mathrm dx$ and $e^{3x}\,\mathrm dx=u^2\,\mathrm du$. As $x\to-\infty$, $u\to0^+$; as $x\to\infty$, $u\to\infty$:

$$
\int_{-\infty}^\infty e^{3x}\exp(-e^x)\,\mathrm dx=\int_0^\infty u^2e^{-u}\,\mathrm du .
$$

By parts twice, $\int u^2e^{-u}\,\mathrm du=-u^2e^{-u}-2ue^{-u}-2e^{-u}=-e^{-u}(u^2+2u+2)$, so

$$
\int_0^Ru^2e^{-u}\,\mathrm du=\Big[-e^{-u}(u^2+2u+2)\Big]_0^R=2-e^{-R}(R^2+2R+2)\to2,
$$

using $R^ne^{-R}\to0$. This is $\Gamma(3)=2!$.

> [!check] Splitting the doubly infinite range
> Strictly the integral splits at a finite point, say $x=0$ ($u=1$). The two halves are $\int_0^1u^2e^{-u}\,\mathrm du=0.1606$ and $\int_1^\infty u^2e^{-u}\,\mathrm du=1.8394$, both finite, with sum $2$.

### Exercises 1(e) and 1(g), substitution removes the singularity

Exercise 1(e) (§9.2.3): $\int_0^1x^2(1-x^3)^{-1/2}\,\mathrm dx$ is singular at $x=1$. Let $u=1-x^3$, $\mathrm du=-3x^2\,\mathrm dx$; $x=0$ gives $u=1$ and $x=1$ gives $u=0$:

$$
\int_0^1x^2(1-x^3)^{-1/2}\,\mathrm dx=\frac13\int_0^1u^{-1/2}\,\mathrm du=\frac13\big[2u^{1/2}\big]_0^1=\frac23 .
$$

The $u$-integral is a p-integral at $0$ with $p=\frac12<1$, so it converges; doing the substitution on $[0,1-\varepsilon]$ and then letting $\varepsilon\to0$ gives the same result.

Exercise 1(g): $\int_0^{\pi/2}\frac{\sin x}{\sqrt{\cos x}}\,\mathrm dx$ is singular at $x=\frac\pi2$, where $\cos x=0$. Let $u=\cos x$, $\mathrm du=-\sin x\,\mathrm dx$; $x=0$ gives $u=1$ and $x=\frac\pi2$ gives $u=0$:

$$
\int_0^{\pi/2}\frac{\sin x}{\sqrt{\cos x}}\,\mathrm dx=\int_0^1u^{-1/2}\,\mathrm du=2 .
$$

### Specimen Test 10, Q4

$\int_1^\infty\frac{\mathrm dx}{\sqrt x}$:

$$
\int_1^Rx^{-1/2}\,\mathrm dx=\big[2x^{1/2}\big]_1^R=2\sqrt R-2\to\infty .
$$

The integral diverges, so it is not defined. This agrees with the p-test: $p=\frac12\le1$ on an infinite range.

### Escape speed from the Earth

The gravitational force on a mass $m$ at distance $r$ from the Earth's centre is $GMm/r^2$, an inverse-square law, so $p=2>1$ and the work to move $m$ from the surface $r=R_E$ to infinity is finite. Per unit mass,

$$
\begin{aligned}
\frac Wm=\int_{R_E}^\infty\frac{GM}{r^2}\,\mathrm dr&=\lim_{R\to\infty}\Big[-\frac{GM}{r}\Big]_{R_E}^R\\
&=\lim_{R\to\infty}\Big(\frac{GM}{R_E}-\frac{GM}{R}\Big)=\frac{GM}{R_E} .
\end{aligned}
$$

With $GM=3.986\times10^{14}\ \mathrm{m^3\,s^{-2}}$ and $R_E=6.371\times10^6$ m, $W/m=6.26\times10^7$ J/kg. Setting the kinetic energy per unit mass $\frac12v^2$ equal to it gives the escape speed

$$
v=\sqrt{\frac{2GM}{R_E}}=1.119\times10^4\ \mathrm{m/s}\approx11.2\ \mathrm{km/s}.
$$

## Links

- Parent: [[MATH1054 Mathematics for Engineering and the Environment Hub]] · Solutions: [[MATH1054 M10 Solutions - Integration III]]
- Previous: [[MATH1054 M09 - Integration II]] · Next: [[MATH1054 M11 - Integration IV]]
- Concepts: [[Partial Fractions]] · [[Completing the Square]] · [[Improper Integrals]]
- Earlier tools: [[MATH1054 M04 - Integration I]] and [[Integration by Parts]] (cyclic by parts, $\int\ln x$); [[Integration by Substitution]]; [[Inverse Trigonometric Functions]] and [[Hyperbolic Functions]] (the standard forms); [[L'Hôpital's Rule]] (the standard limits); [[Complex Numbers - Cartesian, Polar and Exponential Forms]] (the conjugate-pair argument)
- Later in the module: [[MATH1054 M24 - Statistics I]] and [[Random Variables, PDF and CDF]] (densities integrated over infinite ranges); [[Convergence Tests for Series]]
- Year 2: the Laplace transform $\int_0^\infty e^{-st}f(t)\,\mathrm dt$ is an improper integral and its inversion is partial fractions ([[MATH2048 TR2 - Laplace Transforms - Definition, Properties and Solving IVPs]], [[Partial Fractions for Inverse Laplace]]) and transfer functions in SESA2027 ([[Laplace Transform]]); Fourier transforms are improper integrals over $(-\infty,\infty)$ ([[MATH2048 TR1 - Fourier Transforms]])

## Sources

- MATH1054 Module Booklet, Module 10 (PDF pp. 26–28): work scheme §§1–5, the Stroud work scheme example $\int\mathrm dx/(x^2+16)$, and Specimen Test 10.
- James, *Modern Engineering Mathematics* (6th ed.): §2.5.1 pp. 114–119 (Examples 2.31–2.35 and the summary of method); §8.8.3 Exercises 105(e), 106(f),(l) p. 645; §8.8.8 Examples 8.53–8.55 pp. 651–653; §8.8.9 Exercise 117 p. 654; §9.2 pp. 702–707 (Examples 9.1–9.4, Exercises 9.2.3).
- Every decomposition, antiderivative and value in this note was checked with SymPy (`apart`, `integrate`, differentiation of each antiderivative, and limits).

## Self-study tasks

### Core

- [ ] Exercises 117(a),(d),(f),(i) (Module 10 work scheme, §4). → [[MATH1054 M10 Solutions - Integration III#Exercise 117: Partial fractions]]
- [ ] Exercises 105(e), 106(f),(l) (Module 10 work scheme, §1). → [[MATH1054 M10 Solutions - Integration III#Part B: Assigned exercises]]
- [ ] Examples 9.1 and 9.2 (Module 10 work scheme, §5). → [[MATH1054 M10 Solutions - Integration III#Example 9.1: Improper integrals where the integrand is unbounded at an endpoint]]
- [ ] Example 9.4 (Module 10 work scheme, §5). → [[MATH1054 M10 Solutions - Integration III#Example 9.4: Infinite ranges]]
- [ ] Specimen Test 10, Q1–Q4. → [[MATH1054 M10 Solutions - Integration III#Part C: Specimen Test 10]]

### Further practice

- [ ] Example 8.53(a)–(c) (Module 10 work scheme, §4). → [[MATH1054 M10 Solutions - Integration III#Example 8.53: Partial fractions]]
- [ ] Exercises 1(e),(g) on p. 707 (Module 10 work scheme, §5). → [[MATH1054 M10 Solutions - Integration III#Exercise 1 (§9.2.3): Improper integrals]]
- [ ] James Example 8.55, $\int_0^1\frac{2}{(1+x)^2(1+x^2)}\,\mathrm dx$ (suggested, not set in the work scheme). → [[#Every factor type at once (James Example 8.55)]]

## Transcript and slide slips

> [!warning] James Example 9.3 (p. 706)
> Where: [[#6. Improper integrals as limits (James §9.2)]].
>
> James evaluates the pendulum period for $\alpha=\frac\pi3$ as $T=8\sqrt{l/g}\int_0^{\pi/2}\frac{\mathrm d\phi}{\sqrt{3+\cos^2\phi}}$ and prints $13.4864\sqrt{l/g}$. The integral is $0.84288$, so $T=6.7430\sqrt{l/g}$; the four-interval trapezium rule James quotes also gives $6.7430$. The printed value is twice too large, as the comparison with the small-angle period $2\pi\sqrt{l/g}=6.283\sqrt{l/g}$ shows. The example is not set in the Module 10 work scheme.
