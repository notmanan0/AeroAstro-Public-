---
title: "MATH1054 M04 - Integration I"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: topic
stream: "Block 1: Calculus"
order: 4
tags:
  - math1054
  - calculus
  - integration
  - numerical-integration
aliases: ["MATH1054 Module 4", "Integration I"]
date: 2026-09-27
status: lectured
coverage: "Module Booklet Module 4 work scheme (items 1–10, Exercises A–C, Specimen Test 4); James §8.7.1, §8.7.4–8.7.5, §8.8.1, §8.8.4, §8.8.10, §8.10.1–8.10.2"
parent: ["[[MATH1054 Mathematics for Engineering and the Environment Hub]]"]
prerequisites: ["[[MATH1054 M03 - Differentiation I]]"]
next_topics: ["[[MATH1054 M09 - Integration II]]"]
key_concepts: ["[[Integration by Parts]]", "[[Trigonometric Integrals and Power Reduction]]", "[[Trapezium and Simpson's Rules]]"]
tutorial_sheets: ["[[MATH1054 M04 Solutions - Integration I]]"]
sources: ["02 - Sources/Course Booklets & Solutions/Module Booklet.pdf (Module 4)", "02 - Sources/Modern Engineering Mathematics.pdf (§8.7–8.10)", "02 - Sources/Formulae & Reference/Integration Formulae.md"]
---

# MATH1054 M04 - Integration I

> [!abstract] Summary
> The definite integral $\int_a^bf(x)\,\mathrm dx$ is the limit of a sum of strip areas, so it measures signed area, and the fundamental theorem of calculus turns it into $F(b)-F(a)$ for any antiderivative $F$. Every standard integral is a derivative read backwards, a linear substitution handles $f(ax+b)$, product-to-sum and double-angle identities reduce trigonometric products and powers to single sines and cosines, and integration by parts, $\int uv'\,\mathrm dx=uv-\int u'v\,\mathrm dx$, handles products of unlike functions. When no antiderivative exists, or only a table of values does, the trapezium rule (error $\propto h^2$) and Simpson's rule (error $\propto h^4$) estimate the integral, and Simpson's rule is exactly the Richardson extrapolation of two trapezium values.

> [!summary]- Exam use: quick path
> - **Use it when:** an antiderivative or a definite integral of a polynomial, exponential, trigonometric or logarithmic expression is needed, or an integral has no closed form or is given only as a table of values.
> - **Assumptions:** angles in radians; $f$ continuous on $[a,b]$; $\ln\lvert x\rvert$ only on a range that excludes $x=0$; Simpson's rule needs an even number of strips.
> - **Method:** 1. Simplify first: expand, divide out, or apply a trigonometric identity. 2. Match a standard integral, dividing by $a$ if the inner function is $ax+b$. 3. For a product of unlike functions integrate by parts, with $u$ the factor that simplifies on differentiation; for $e^{ax}\sin bx$ do it twice and solve for $I$. 4. With no closed form or only data, apply the trapezium or Simpson rule with the prescribed $h$. 5. Differentiate the answer back to check it.
> - **Common mistakes:** forgetting the $\frac1a$ in a linear substitution ($\int\cos4x\,\mathrm dx=\frac14\sin4x$, not $\sin4x$); in Simpson's rule, using an odd number of strips or swapping the weights 4 (odd ordinates) and 2 (even ordinates).
> - **Practise:** [[#The cyclic case (Example 8.51(c))]] · [[MATH1054 M04 Solutions - Integration I#Exercises 110, 111(a) (p.649): Integration by parts|Exercises 110 and 111(a)]]

Integration adds up a quantity that varies. The distance travelled by a vehicle is the area under its velocity–time graph, the volume of earth in a road cutting is the integral of the cross-sectional area along the road, and the work done by a varying force is the integral of force over distance. In each case the interval is cut into thin strips, each strip contributes (height) × (width), and the integral is the limit of that sum as the strips get thinner. That definition is also the starting point of the numerical rules at the end of the topic, which stop the limit at a finite strip width and estimate the error made.

The fundamental theorem of calculus links this summing process to differentiation: the rate at which the area grows as the right-hand end moves is the height of the curve there. So every derivative from [[MATH1054 M03 - Differentiation I|Module 3]], read backwards, is an integral, and the product rule read backwards becomes integration by parts. What the theorem does not supply is a method that always works. Differentiation is mechanical, but integration is pattern matching: rearrange the integrand until it becomes a sum of standard forms. Some integrands, such as $e^{-x^2}$ or $\sqrt{1+x^3}$, have no antiderivative in elementary functions at all, and for those, or for measured data, the integral has to be computed numerically.

General substitution and applications (areas, volumes, centroids, mean values) are in [[MATH1054 M09 - Integration II|Module 9]], partial fractions and improper integrals in [[MATH1054 M10 - Integration III|Module 10]], and double integrals in [[MATH1054 M11 - Integration IV|Module 11]]. The cyclic integration by parts of §6 and the trigonometric product integrals of §5 are the two calculations behind every Fourier coefficient in MATH2048.

---

## 1. The definite integral as a signed area (James §8.7.1)

Divide $[a,b]$ into $n$ strips at the points $a=x_0<x_1<\dots<x_n=b$, with widths $\Delta x_{r-1}=x_r-x_{r-1}$, and pick any point $x_r^*$ in the $r$th strip. A strip of height $f(x_r^*)$ has area $f(x_r^*)\,\Delta x_{r-1}$, so the area under the graph is approximately $\sum f(x_r^*)\,\Delta x_{r-1}$. The **definite integral** is the limit of this sum as the number of strips grows and the widest strip shrinks to zero:

$$
\int_a^bf(x)\,\mathrm dx=\lim_{\substack{n\to\infty\\ \Delta x\to0}}\sum_{r=1}^{n}f(x_r^*)\,\Delta x_{r-1},\qquad\Delta x=\max_r\Delta x_{r-1}.
$$

For a continuous $f$ the limit is the same for every way of subdividing $[a,b]$ and every choice of the points $x_r^*$. The function $f$ is the **integrand**, $a$ and $b$ are the **limits of integration**, and $\int$ is an elongated S for "sum".

Each term is a height times a positive width. Where $f(x)<0$ the height is negative, so the term is negative: area below the $x$-axis counts as negative. The integral is therefore a **signed area**. To find the geometric area enclosed between the curve and the axis, split the range at the zeros of $f$, integrate over each piece, and add the absolute values.

### Signed area of x + 3 (Example 8.38)

The line $y=x+3$ crosses the axis at $x=-3$. On $[-5,-3]$ it lies below the axis and bounds a triangle of base 2 and height 2; on $[-3,5]$ it lies above and bounds a triangle of base 8 and height 8.

$$
\begin{aligned}
A_1&=-\tfrac12(2)(2)=-2,\\
A_2&=+\tfrac12(8)(8)=+32,\\
\int_{-5}^{5}(x+3)\,\mathrm dx&=A_1+A_2\\
&=30.
\end{aligned}
$$

The geometric area between the line and the axis is $\lvert A_1\rvert+A_2=34$, not 30.

![[m1054_m04_signed_area.png|700]]

## 2. Indefinite integrals and the fundamental theorem (James §8.7.4–8.7.5)

Fix the lower limit at $a$ and let the upper limit vary. The area from $a$ to $x$ is then a function of $x$,

$$
F(x)=\int_a^xf(t)\,\mathrm dt,
$$

where the dummy variable $t$ is renamed so that it does not clash with the limit $x$. A different lower limit $c$ gives a function $G(x)=\int_c^xf(t)\,\mathrm dt$ that differs from $F$ only by a constant, because the two areas differ by the fixed area between $a$ and $c$:

$$
\begin{aligned}
F(x)-G(x)&=\int_a^xf(t)\,\mathrm dt-\int_c^xf(t)\,\mathrm dt\\
&=\int_a^cf(t)\,\mathrm dt.
\end{aligned}
$$

For example, $\int_1^x(t^2-1)\,\mathrm dt=\frac13x^3-x+\frac23$ and $\int_2^x(t^2-1)\,\mathrm dt=\frac13x^3-x-\frac23$. Every such function has the form $\frac13x^3-x+c$, and the **indefinite integral** is written with an arbitrary constant of integration, $\int(x^2-1)\,\mathrm dx=\frac13x^3-x+c$. An indefinite integral is a function; a definite integral is a number.

### The fundamental theorem of calculus

If $f$ is continuous, then $F(x)=\int_a^xf(t)\,\mathrm dt$ is differentiable and $F'(x)=f(x)$.

The proof uses only the area picture. Take $h>0$. The difference $F(x+h)-F(x)$ is the area of the thin strip from $x$ to $x+h$:

$$
F(x+h)-F(x)=\int_x^{x+h}f(t)\,\mathrm dt.
$$

Let $m_h$ and $M_h$ be the smallest and largest values of $f$ on $[x,x+h]$, which exist because $f$ is continuous. The strip lies between a rectangle of height $m_h$ and one of height $M_h$, both of width $h$:

$$
h\,m_h\le\int_x^{x+h}f(t)\,\mathrm dt\le h\,M_h .
$$

Divide by $h$:

$$
m_h\le\frac{F(x+h)-F(x)}{h}\le M_h .
$$

As $h\to0$, both $m_h$ and $M_h$ tend to $f(x)$ by continuity, so the quotient in the middle is squeezed to the same limit:

$$
F'(x)=f(x).
$$

The case $h<0$ is the same with the inequalities written for $[x+h,x]$.

### Evaluating a definite integral

Let $G$ be any antiderivative of $f$, so $G'=f$. Then $(F-G)'=f-f=0$, so $F-G$ is a constant $C$:

$$
\begin{aligned}
F(x)&=G(x)+C,\\
F(a)=0\ &\Rightarrow\ C=-G(a),\\
\int_a^bf(x)\,\mathrm dx=F(b)&=G(b)-G(a).
\end{aligned}
$$

This is written $\big[G(x)\big]_a^b$. The constant of integration cancels in the subtraction, so it is left out of definite integrals. For example,

$$
\int_1^5(x^2-1)\,\mathrm dx=\Big[\tfrac13x^3-x\Big]_1^5=\Big(\tfrac{125}3-5\Big)-\Big(\tfrac13-1\Big)=\tfrac{112}3=37\tfrac13 .
$$

As a check on §1, $\int_{-5}^5(x+3)\,\mathrm dx=\big[\frac12x^2+3x\big]_{-5}^5=(12.5+15)-(12.5-15)=30$.

## 3. Standard integrals and the linearity rules (James §8.8.1)

Every derivative in [[MATH1054 M03 - Differentiation I|Module 3]], read backwards, gives an integral. For example, $\frac{\mathrm d}{\mathrm dx}\big(-\frac1a\cos ax\big)=\sin ax$, so $\int\sin ax\,\mathrm dx=-\frac1a\cos ax+C$. The table collects the forms used in this module; James Fig. 8.56 lists the cases with $a=1$, and the formula sheet and Data Book have the full list.

| $f(x)$ | $\int f\,\mathrm dx$ | $f(x)$ | $\int f\,\mathrm dx$ |
|---|---|---|---|
| $x^n$ ($n\neq-1$) | $\dfrac{x^{n+1}}{n+1}$ | $\sec^2x$ | $\tan x$ |
| $\dfrac1x$ ($x\neq0$) | $\ln\lvert x\rvert$ | $\dfrac{1}{\sqrt{a^2-x^2}}$ ($\lvert x\rvert<a$) | $\sin^{-1}\dfrac xa$ |
| $e^{ax}$ | $\dfrac1ae^{ax}$ | $\dfrac1{a^2+x^2}$ | $\dfrac1a\tan^{-1}\dfrac xa$ |
| $\sin ax$ | $-\dfrac1a\cos ax$ | $\dfrac{1}{\sqrt{x^2+a^2}}$ | $\sinh^{-1}\dfrac xa$ |
| $\cos ax$ | $\dfrac1a\sin ax$ | $\dfrac{1}{\sqrt{x^2-a^2}}$ ($x>a$) | $\cosh^{-1}\dfrac xa$ |

Each entry carries $+C$. The power rule fails at $n=-1$, where it would divide by zero, and the logarithm fills the gap. The modulus in $\ln\lvert x\rvert$ comes from the case $x<0$, where the chain rule gives

$$
\frac{\mathrm d}{\mathrm dx}\ln(-x)=\frac{-1}{-x}=\frac1x ,
$$

so $\ln(-x)$ is an antiderivative of $1/x$ on $x<0$, just as $\ln x$ is on $x>0$. A definite integral of $1/x$ must not cross $x=0$. The derivatives of $\sin^{-1}x$, $\tan^{-1}x$, $\sinh^{-1}x$ and $\cosh^{-1}x$ (see [[MATH1054 M07 - Functions|Module 7]] and [[MATH1054 M08 - Differentiation II|Module 8]]) give the standard forms with $a=1$; the versions with $a$ follow from the substitution $x=au$ in §4.

Two rules extend the table, both inherited from the linearity of differentiation. A constant factor comes outside, $\int kf\,\mathrm dx=k\int f\,\mathrm dx$, and a sum integrates term by term, $\int(f\pm g)\,\mathrm dx=\int f\,\mathrm dx\pm\int g\,\mathrm dx$. There is no corresponding product rule: $\int fg\,\mathrm dx$ is not $\int f\,\mathrm dx\int g\,\mathrm dx$, which is why §5 and §6 exist. Two further rules are the linear composite rule (§4) and an inverse-function rule, $\int f^{-1}(x)\,\mathrm dx=xy-\int f(y)\,\mathrm dy$ with $y=f^{-1}(x)$, which is rarely used.

### Indefinite integrals by the rules (Example 8.43)

(a) Term by term:

$$
\int\Big(6x^4+4x-\frac3x\Big)\mathrm dx=\tfrac65x^5+2x^2-3\ln\lvert x\rvert+C .
$$

(b) Expand first, since there is no rule for a product. The square root restricts the domain to $x\ge0$.

$$
\begin{aligned}
(2-x)\sqrt x&=2x^{1/2}-x^{3/2},\\
\int(2-x)\sqrt x\,\mathrm dx&=2\cdot\tfrac23x^{3/2}-\tfrac25x^{5/2}+C\\
&=\tfrac43x^{3/2}-\tfrac25x^{5/2}+C .
\end{aligned}
$$

(c) $\int\sqrt{5x+2}\,\mathrm dx=\frac2{15}(5x+2)^{3/2}+C$ for $x\ge-\frac25$, worked in §4.

(d) Divide out:

$$
\int\frac{x+1}x\,\mathrm dx=\int\Big(1+\frac1x\Big)\mathrm dx=x+\ln\lvert x\rvert+C\quad(x\neq0).
$$

### Definite integrals (Example 8.44)

(a)

$$
\begin{aligned}
\int_1^2(x^4+6x^2-4)\,\mathrm dx&=\Big[\tfrac{x^5}5+2x^3-4x\Big]_1^2\\
&=\big(\tfrac{32}5+16-8\big)-\big(\tfrac15+2-4\big)\\
&=\tfrac{72}5+\tfrac95\\
&=\tfrac{81}5 .
\end{aligned}
$$

(b) Expand $\frac{(x^2-1)^2}{x^2}=x^2-2+x^{-2}$:

$$
\begin{aligned}
\int_1^2\frac{(x^2-1)^2}{x^2}\,\mathrm dx&=\Big[\tfrac{x^3}3-2x-\tfrac1x\Big]_1^2\\
&=\big(\tfrac83-4-\tfrac12\big)-\big(\tfrac13-2-1\big)\\
&=-\tfrac{11}6+\tfrac83\\
&=\tfrac56 .
\end{aligned}
$$

(c)

$$
\int_{-2}^44e^x\,\mathrm dx=4\big[e^x\big]_{-2}^4=4(e^4-e^{-2})=217.85\ \text{(2 d.p.)}
$$

(d)

$$
\begin{aligned}
\int_0^{\pi/6}(\cos3x+2\sin3x)\,\mathrm dx&=\Big[\tfrac13\sin3x-\tfrac23\cos3x\Big]_0^{\pi/6}\\
&=\big(\tfrac13\sin\tfrac\pi2-\tfrac23\cos\tfrac\pi2\big)-\big(0-\tfrac23\big)\\
&=\tfrac13+\tfrac23\\
&=1 .
\end{aligned}
$$

Specimen Test 4 Q2(i) is the same kind of calculation: $\int_0^1(x^2+1)^2\,\mathrm dx=\int_0^1(x^4+2x^2+1)\,\mathrm dx=\frac15+\frac23+1=\frac{28}{15}$.

## 4. Linear substitutions (James §8.8.1)

If $F'=f$, the chain rule gives

$$
\frac{\mathrm d}{\mathrm dx}F(ax+b)=aF'(ax+b)=af(ax+b),
$$

so, for a constant $a\neq0$,

$$
\int f(ax+b)\,\mathrm dx=\frac1aF(ax+b)+C .
$$

James calls this the linear composite rule. It is easier to remember as a substitution. Put $u=ax+b$; then $\frac{\mathrm du}{\mathrm dx}=a$, so $\mathrm dx=\frac{\mathrm du}a$, and

$$
\int f(ax+b)\,\mathrm dx=\int f(u)\,\frac{\mathrm du}a=\frac1aF(u)+C=\frac1aF(ax+b)+C .
$$

Treating $\mathrm du$ and $\mathrm dx$ as separate quantities here is justified by the chain rule above. The general substitution method is in [[Integration by Substitution]] (Module 9).

### Worked substitutions

For Example 8.43(c), put $u=5x+2$, so $\mathrm dx=\frac{\mathrm du}5$:

$$
\begin{aligned}
\int\sqrt{5x+2}\,\mathrm dx&=\int u^{1/2}\,\frac{\mathrm du}5\\
&=\frac15\cdot\frac{u^{3/2}}{3/2}+C\\
&=\tfrac2{15}(5x+2)^{3/2}+C .
\end{aligned}
$$

For $\cos4x$, put $u=4x$, so $\mathrm dx=\frac{\mathrm du}4$ and $\int\cos4x\,\mathrm dx=\frac14\int\cos u\,\mathrm du=\frac14\sin4x+C$.

For $\dfrac1{1+4x^2}$, put $u=2x$, so the denominator is $1+u^2$ and $\mathrm dx=\frac{\mathrm du}2$:

$$
\int\frac{\mathrm dx}{1+4x^2}=\int\frac{\mathrm du/2}{1+u^2}=\tfrac12\tan^{-1}u+C=\tfrac12\tan^{-1}2x+C .
$$

For $\dfrac1{4+x^2}$, take the 4 out first, $4+x^2=4\big(1+\frac{x^2}4\big)$, then put $u=\frac x2$, so $\mathrm dx=2\,\mathrm du$:

$$
\begin{aligned}
\int\frac{\mathrm dx}{4+x^2}&=\int\frac{2\,\mathrm du}{4(1+u^2)}\\
&=\tfrac12\tan^{-1}u+C\\
&=\tfrac12\tan^{-1}\frac x2+C .
\end{aligned}
$$

The same steps with a general $a>0$ give the table entry. Put $x=au$, so $\mathrm dx=a\,\mathrm du$ and $a^2+x^2=a^2(1+u^2)$:

$$
\begin{aligned}
\int\frac{\mathrm dx}{a^2+x^2}&=\int\frac{a\,\mathrm du}{a^2(1+u^2)}\\
&=\frac1a\tan^{-1}u+C\\
&=\frac1a\tan^{-1}\frac xa+C .
\end{aligned}
$$

Specimen Test 4 Q1(vi) is the case $a=3$: $\int\frac{\mathrm dx}{9+x^2}=\frac13\tan^{-1}\frac x3+C$. The $\sin^{-1}$, $\sinh^{-1}$ and $\cosh^{-1}$ entries follow the same way, since $\sqrt{a^2-x^2}=a\sqrt{1-u^2}$ and the factor $a$ cancels the $a$ in $\mathrm dx$. Each of these answers can be checked by differentiating it with the chain rule.

### Changing the limits

In a definite integral the limits belong to the variable of integration, so they change with the substitution. For $\int_0^1(2x+1)^3\,\mathrm dx$, put $u=2x+1$, so $\mathrm dx=\frac{\mathrm du}2$; $x=0$ gives $u=1$ and $x=1$ gives $u=3$:

$$
\begin{aligned}
\int_0^1(2x+1)^3\,\mathrm dx&=\int_1^3u^3\,\frac{\mathrm du}2\\
&=\Big[\frac{u^4}8\Big]_1^3\\
&=\tfrac18(81-1)\\
&=10 .
\end{aligned}
$$

### Set exercises on standard forms

The work-scheme exercises and the first Specimen Test question use only the table and linear substitutions:

| Integrand | Result | Set as |
|---|---|---|
| $3x^{2/3}$ | $\tfrac95x^{5/3}+C$ | Ex 104(a) |
| $\sqrt{2x}=\sqrt2\,x^{1/2}$ | $\tfrac{2\sqrt2}3x^{3/2}+C$ | Ex 104(b) |
| $2x^3-2x^2+\tfrac1x-2$ | $\tfrac12x^4-\tfrac23x^3+\ln\lvert x\rvert-2x+C$ | Ex 104(c) |
| $2e^x+3\cos2x$ | $2e^x+\tfrac32\sin2x+C$ | Ex 104(d) |
| $(2x+1)^3$ | $\tfrac18(2x+1)^4+C$ | Ex 104(f) |
| $(x+1)^{-1/3}$ | $\tfrac32(x+1)^{2/3}+C$ | Ex 106(b) |
| $x^{-2}$ | $-\dfrac1x+C$ | Spec. Test 4 Q1(i) |
| $\dfrac1{x+4}$ | $\ln\lvert x+4\rvert+C$ | Spec. Test 4 Q1(ii) |
| $e^{2x+1}$ | $\tfrac12e^{2x+1}+C$ | Spec. Test 4 Q1(iii) |
| $\sin(1+4x)$ | $-\tfrac14\cos(1+4x)+C$ | Spec. Test 4 Q1(iv) |

Exercise 105(c) is a definite integral:

$$
\begin{aligned}
\int_1^2\Big(x^{3/2}-\frac1{x^2}\Big)\mathrm dx&=\Big[\tfrac25x^{5/2}+\tfrac1x\Big]_1^2\\
&=\Big(\tfrac25\cdot4\sqrt2+\tfrac12\Big)-\Big(\tfrac25+1\Big)\\
&=\tfrac{8\sqrt2}5-\tfrac9{10}\\
&\approx1.3627 .
\end{aligned}
$$

## 5. Products and powers of sines and cosines (James §8.8.10)

Sines and cosines of a single angle $kx+c$ integrate directly. Products such as $\sin5x\cos x$ and powers such as $\cos^4x$ do not, so they are first rewritten as sums of single sines and cosines.

### Product-to-sum identities, derived

Start from the compound-angle formulae:

$$
\begin{aligned}
\sin(A+B)&=\sin A\cos B+\cos A\sin B,\\
\sin(A-B)&=\sin A\cos B-\cos A\sin B,\\
\cos(A+B)&=\cos A\cos B-\sin A\sin B,\\
\cos(A-B)&=\cos A\cos B+\sin A\sin B .
\end{aligned}
$$

Adding the first two cancels the $\cos A\sin B$ terms; adding the last two cancels the $\sin A\sin B$ terms; subtracting the third from the fourth cancels the $\cos A\cos B$ terms:

$$
\begin{aligned}
2\sin A\cos B&=\sin(A+B)+\sin(A-B),\\
2\cos A\cos B&=\cos(A+B)+\cos(A-B),\\
2\sin A\sin B&=\cos(A-B)-\cos(A+B).
\end{aligned}
$$

### Power reduction, derived

Put $B=A$ in $\cos(A+B)$ and use $\sin^2A+\cos^2A=1$ to remove one function or the other:

$$
\begin{aligned}
\cos2A&=\cos^2A-\sin^2A\\
&=2\cos^2A-1\\
&=1-2\sin^2A .
\end{aligned}
$$

Rearranging gives the two power-reduction formulae,

$$
\cos^2A=\tfrac12(1+\cos2A),\qquad\sin^2A=\tfrac12(1-\cos2A),
$$

which are also the cases $B=A$ of the product-to-sum identities. Each application halves the power and doubles the angle.

> [!warning] Sign of the sine–sine identity
> Some versions of the Data Book (p. 3-8) misprint two of these identities. The correct forms are $2\sin A\sin B=\cos(A-B)-\cos(A+B)$ and $\sin A+\sin B=2\sin\frac12(A+B)\cos\frac12(A-B)$. A quick test of the first: with $B=A$ it must reduce to $2\sin^2A=1-\cos2A$, which is positive, so the $\cos(A-B)=1$ term comes first.

### Squares of sine and cosine (Example 8.56(a))

$$
\begin{aligned}
\int\cos^2x\,\mathrm dx&=\tfrac12\int(1+\cos2x)\,\mathrm dx\\
&=\tfrac12x+\tfrac14\sin2x+C,\\
\int\sin^2x\,\mathrm dx&=\tfrac12\int(1-\cos2x)\,\mathrm dx\\
&=\tfrac12x-\tfrac14\sin2x+C .
\end{aligned}
$$

Specimen Test 4 Q2(ii) uses the second:

$$
\int_0^\pi\sin^2x\,\mathrm dx=\tfrac12\Big[x-\tfrac12\sin2x\Big]_0^\pi=\frac\pi2 .
$$

### Products with shifted angles (Example 8.56(b))

The identities hold for any angles, not only multiples of $x$. With $A=5x+1$ and $B=x+2$:

$$
\begin{aligned}
\sin(5x+1)\cos(x+2)&=\tfrac12\big[\sin(6x+3)+\sin(4x-1)\big],\\
\int\sin(5x+1)\cos(x+2)\,\mathrm dx&=-\tfrac1{12}\cos(6x+3)-\tfrac18\cos(4x-1)+C .
\end{aligned}
$$

Exercise 119(b) and Specimen Test 4 Q1(v) use the cosine–cosine identity:

$$
\begin{aligned}
\int\cos7x\cos5x\,\mathrm dx&=\tfrac12\int(\cos12x+\cos2x)\,\mathrm dx=\tfrac1{24}\sin12x+\tfrac14\sin2x+C,\\
\int\cos2x\cos4x\,\mathrm dx&=\tfrac12\int(\cos6x+\cos2x)\,\mathrm dx=\tfrac1{12}\sin6x+\tfrac14\sin2x+C .
\end{aligned}
$$

### Fourth power of cosine (Exercise A)

Reduce the power twice, the second time with $2x$ in place of $x$:

$$
\begin{aligned}
\cos^4x&=\big(\cos^2x\big)^2\\
&=\tfrac14(1+\cos2x)^2\\
&=\tfrac14\big(1+2\cos2x+\cos^22x\big)\\
&=\tfrac14\big(1+2\cos2x+\tfrac12(1+\cos4x)\big)\\
&=\tfrac38+\tfrac12\cos2x+\tfrac18\cos4x .
\end{aligned}
$$

Integrate term by term:

$$
\int\cos^4x\,\mathrm dx=\tfrac38x+\tfrac14\sin2x+\tfrac1{32}\sin4x+C .
$$

An odd power is handled differently: keep one factor of $\cos x$ (or $\sin x$) and convert the rest with $\sin^2x+\cos^2x=1$, which leaves a polynomial in $\sin x$ times $\cos x$. For example $\int\sin^2x\cos^3x\,\mathrm dx=\int\sin^2x(1-\sin^2x)\cos x\,\mathrm dx=\frac13\sin^3x-\frac15\sin^5x+C$, using the substitution $u=\sin x$ from Module 9.

### Orthogonality over a half-period (Exercise 120)

For 120(a), the sine–sine identity gives $\sin5x\sin6x=\frac12(\cos x-\cos11x)$:

$$
\begin{aligned}
\int_0^\pi\sin5x\sin6x\,\mathrm dx&=\tfrac12\Big[\sin x-\tfrac1{11}\sin11x\Big]_0^\pi\\
&=0 .
\end{aligned}
$$

For 120(b), $\sin^25x=\frac12(1-\cos10x)$:

$$
\begin{aligned}
\int_0^\pi\sin^25x\,\mathrm dx&=\tfrac12\Big[x-\tfrac1{10}\sin10x\Big]_0^\pi\\
&=\frac\pi2 .
\end{aligned}
$$

The same steps for any integers $m,n\ge1$ give $\sin mx\sin nx=\frac12[\cos(m-n)x-\cos(m+n)x]$, and every term integrates to a sine of an integer multiple of $\pi$, so

$$
\int_0^\pi\sin mx\sin nx\,\mathrm dx=\begin{cases}0,&m\neq n,\\[2pt]\dfrac\pi2,&m=n.\end{cases}
$$

The case $m=n$ is separate because the general step divides by $m-n$. This **orthogonality** of sines is what makes Fourier series work: multiplying a sum of sines by one of them and integrating picks out a single coefficient ([[Orthogonality of Trigonometric Functions]], MATH2048).

![[m1054_m04_trig_products.png|900]]

> [!warning] Sine against cosine on 0 to π
> The orthogonality above is for two sines (or two cosines). A sine against a cosine does not integrate to zero over $[0,\pi]$: $\int_0^\pi\sin3x\cos2x\,\mathrm dx=\frac65$. Sine–cosine products vanish over a full period such as $[-\pi,\pi]$, not over the half-period.

## 6. Integration by parts (James §8.8.4)

### The formula, derived

Start from the product rule for two differentiable functions $u(x)$ and $v(x)$:

$$
\frac{\mathrm d}{\mathrm dx}(uv)=\frac{\mathrm du}{\mathrm dx}v+u\frac{\mathrm dv}{\mathrm dx}.
$$

Move the first term to the other side:

$$
u\frac{\mathrm dv}{\mathrm dx}=\frac{\mathrm d}{\mathrm dx}(uv)-v\frac{\mathrm du}{\mathrm dx}.
$$

Integrate both sides with respect to $x$. The integral of a derivative is the function itself:

$$
\int u\frac{\mathrm dv}{\mathrm dx}\,\mathrm dx=uv-\int v\frac{\mathrm du}{\mathrm dx}\,\mathrm dx .
$$

This is **integration by parts**. One factor of the integrand is called $u$ and is differentiated; the other is called $\frac{\mathrm dv}{\mathrm dx}$ and is integrated to give $v$. The method pays off when $\int v\,u'\,\mathrm dx$ is simpler than the original.

No constant is needed when $v$ is found from $\frac{\mathrm dv}{\mathrm dx}$. Using $v+k$ instead of $v$ changes the right-hand side by $ku-\int ku'\,\mathrm dx=ku-ku=0$.

For a definite integral, the same argument with limits gives

$$
\int_a^bu\frac{\mathrm dv}{\mathrm dx}\,\mathrm dx=\big[uv\big]_a^b-\int_a^bv\frac{\mathrm du}{\mathrm dx}\,\mathrm dx .
$$

### Choosing u

Choose $u$ as the factor that gets simpler when differentiated and $\frac{\mathrm dv}{\mathrm dx}$ as a factor that can be integrated. A common ordering for $u$ is **LIATE**: logarithms, inverse trigonometric functions, algebraic (powers of $x$), trigonometric, exponential. Logarithms and inverse trigonometric functions come first because they are hard to integrate but differentiate to algebraic functions; a power $x^n$ comes before a sine or exponential because differentiating lowers the power, and $n$ applications remove it. Exponentials and sines never simplify, so they are the natural $\frac{\mathrm dv}{\mathrm dx}$.

### A log times a power (Example 8.51(a) and Exercise 110(c))

For $\int x\ln x\,\mathrm dx$ take $u=\ln x$ and $\frac{\mathrm dv}{\mathrm dx}=x$, so $\frac{\mathrm du}{\mathrm dx}=\frac1x$ and $v=\frac12x^2$ ($x>0$):

$$
\begin{aligned}
\int x\ln x\,\mathrm dx&=\tfrac12x^2\ln x-\int\tfrac12x^2\cdot\tfrac1x\,\mathrm dx\\
&=\tfrac12x^2\ln x-\tfrac12\int x\,\mathrm dx\\
&=\tfrac12x^2\ln x-\tfrac14x^2+C .
\end{aligned}
$$

Specimen Test 4 Q3 puts limits on it:

$$
\begin{aligned}
\int_1^2x\ln x\,\mathrm dx&=\Big[\tfrac12x^2\ln x-\tfrac14x^2\Big]_1^2\\
&=(2\ln2-1)-\big(0-\tfrac14\big)\\
&=2\ln2-\tfrac34\\
&\approx0.6363 .
\end{aligned}
$$

Exercise 110(c) is the same with $\frac{\mathrm dv}{\mathrm dx}=x^3$, so $v=\frac14x^4$:

$$
\begin{aligned}
\int x^3\ln x\,\mathrm dx&=\tfrac14x^4\ln x-\int\tfrac14x^4\cdot\tfrac1x\,\mathrm dx\\
&=\tfrac14x^4\ln x-\tfrac1{16}x^4+C\\
&=\tfrac1{16}x^4(4\ln x-1)+C .
\end{aligned}
$$

The logarithm on its own is integrated by parts with $u=\ln x$ and $\frac{\mathrm dv}{\mathrm dx}=1$, so $v=x$:

$$
\int\ln x\,\mathrm dx=x\ln x-\int x\cdot\tfrac1x\,\mathrm dx=x\ln x-x+C .
$$

### A power times a sine or exponential (Exercises 110(a) and 110(b))

$$
\begin{aligned}
\int x\sin x\,\mathrm dx&=x(-\cos x)-\int(-\cos x)(1)\,\mathrm dx\\
&=-x\cos x+\sin x+C,\\[4pt]
\int xe^{3x}\,\mathrm dx&=\tfrac13xe^{3x}-\int\tfrac13e^{3x}\,\mathrm dx\\
&=\tfrac13xe^{3x}-\tfrac19e^{3x}+C\\
&=\tfrac19e^{3x}(3x-1)+C .
\end{aligned}
$$

### Repeated parts (Example 8.51(b) and Exercise 111(a))

For $\int x^2\cos x\,\mathrm dx$, take $u=x^2$ and $\frac{\mathrm dv}{\mathrm dx}=\cos x$, so $v=\sin x$:

$$
\int x^2\cos x\,\mathrm dx=x^2\sin x-2\int x\sin x\,\mathrm dx .
$$

The remaining integral is Exercise 110(a), one more application of parts with $u=x$:

$$
\begin{aligned}
\int x^2\cos x\,\mathrm dx&=x^2\sin x-2(-x\cos x+\sin x)+C\\
&=x^2\sin x+2x\cos x-2\sin x+C .
\end{aligned}
$$

Exercise 111(a) is the definite version with the roles of sine and cosine swapped. The boundary terms are evaluated as they appear:

$$
\begin{aligned}
\int_0^{\pi/2}x^2\sin x\,\mathrm dx&=\big[-x^2\cos x\big]_0^{\pi/2}+2\int_0^{\pi/2}x\cos x\,\mathrm dx\\
&=0+2\big[x\sin x+\cos x\big]_0^{\pi/2}\\
&=2\big(\tfrac\pi2+0\big)-2(0+1)\\
&=\pi-2\approx1.1416 .
\end{aligned}
$$

### The cyclic case (Example 8.51(c))

For $I=\int e^x\sin2x\,\mathrm dx$ neither factor simplifies on differentiation. Integrating by parts twice, differentiating the trigonometric factor both times, brings $I$ back, and the resulting equation is solved for $I$. Take $u=\sin2x$ and $\frac{\mathrm dv}{\mathrm dx}=e^x$:

$$
I=e^x\sin2x-2\int e^x\cos2x\,\mathrm dx .
$$

Taking $u=\cos2x$ and $\frac{\mathrm dv}{\mathrm dx}=e^x$ in the new integral gives

$$
\int e^x\cos2x\,\mathrm dx=e^x\cos2x+2\int e^x\sin2x\,\mathrm dx=e^x\cos2x+2I .
$$

Substitute back and collect the $I$ terms:

$$
\begin{aligned}
I&=e^x\sin2x-2\big(e^x\cos2x+2I\big)\\
&=e^x\sin2x-2e^x\cos2x-4I,\\
5I&=e^x(\sin2x-2\cos2x),\\
I&=\tfrac15e^x(\sin2x-2\cos2x)+C .
\end{aligned}
$$

The constant is added at the end, because both sides of the equation for $I$ contain the same indefinite integral.

> [!warning] Keep the same choice on the second pass
> On the second application, differentiate the same type of factor as on the first (here the trigonometric one). Swapping roles, so that $u=e^x$ the second time, undoes the first step and returns the identity $I=I$.

### The general cyclic formulas

The same calculation with general constants gives a general formula. Let $C=\int e^{ax}\cos bx\,\mathrm dx$ and $S=\int e^{ax}\sin bx\,\mathrm dx$ with $a\neq0$. Integrating by parts with $\frac{\mathrm dv}{\mathrm dx}=e^{ax}$, so $v=\frac1ae^{ax}$, each integral gives the other:

$$
\begin{aligned}
C&=\tfrac1ae^{ax}\cos bx+\tfrac baS,\\
S&=\tfrac1ae^{ax}\sin bx-\tfrac baC .
\end{aligned}
$$

Substitute the second into the first and solve for $C$:

$$
\begin{aligned}
C&=\tfrac1ae^{ax}\cos bx+\tfrac b{a^2}e^{ax}\sin bx-\tfrac{b^2}{a^2}C,\\
\Big(1+\tfrac{b^2}{a^2}\Big)C&=\frac{e^{ax}(a\cos bx+b\sin bx)}{a^2},\\
C&=\frac{e^{ax}(a\cos bx+b\sin bx)}{a^2+b^2}.
\end{aligned}
$$

Then the second line gives $S$:

$$
\begin{aligned}
S&=\tfrac1ae^{ax}\sin bx-\tfrac ba\cdot\frac{e^{ax}(a\cos bx+b\sin bx)}{a^2+b^2}\\
&=\frac{e^{ax}\big[(a^2+b^2)\sin bx-ab\cos bx-b^2\sin bx\big]}{a(a^2+b^2)}\\
&=\frac{e^{ax}(a\sin bx-b\cos bx)}{a^2+b^2}.
\end{aligned}
$$

So, with $+C$ on each,

$$
\int e^{ax}\cos bx\,\mathrm dx=\frac{e^{ax}(a\cos bx+b\sin bx)}{a^2+b^2},\qquad\int e^{ax}\sin bx\,\mathrm dx=\frac{e^{ax}(a\sin bx-b\cos bx)}{a^2+b^2}.
$$

The quickest route to both is the complex exponential of [[Euler's Formula]] (Module 5): $e^{ax}(\cos bx+j\sin bx)=e^{(a+jb)x}$ integrates to $\frac{e^{(a+jb)x}}{a+jb}=\frac{e^{ax}(\cos bx+j\sin bx)(a-jb)}{a^2+b^2}$, whose real and imaginary parts are the two formulas.

### Cyclic integrals set as exercises (Exercise 110(d) and Exercise B)

For Exercise 110(d), $I=\int e^{-2x}\sin3x\,\mathrm dx$. Take $u=\sin3x$ and $v=-\frac12e^{-2x}$:

$$
I=-\tfrac12e^{-2x}\sin3x+\tfrac32\int e^{-2x}\cos3x\,\mathrm dx .
$$

Again with $u=\cos3x$:

$$
\int e^{-2x}\cos3x\,\mathrm dx=-\tfrac12e^{-2x}\cos3x-\tfrac32I .
$$

Substitute back and solve:

$$
\begin{aligned}
I&=-\tfrac12e^{-2x}\sin3x-\tfrac34e^{-2x}\cos3x-\tfrac94I,\\
\tfrac{13}4I&=-\tfrac14e^{-2x}(2\sin3x+3\cos3x),\\
I&=-\tfrac1{13}e^{-2x}(2\sin3x+3\cos3x)+C .
\end{aligned}
$$

The general formula with $a=-2$, $b=3$ gives $\frac{e^{-2x}(-2\sin3x-3\cos3x)}{13}$, the same.

For Exercise B, $I=\int e^{2x}\cos x\,\mathrm dx$. Take $u=\cos x$ and $v=\frac12e^{2x}$:

$$
I=\tfrac12e^{2x}\cos x+\tfrac12\int e^{2x}\sin x\,\mathrm dx .
$$

Again with $u=\sin x$:

$$
\int e^{2x}\sin x\,\mathrm dx=\tfrac12e^{2x}\sin x-\tfrac12I .
$$

Substitute back and solve:

$$
\begin{aligned}
I&=\tfrac12e^{2x}\cos x+\tfrac14e^{2x}\sin x-\tfrac14I,\\
\tfrac54I&=\tfrac14e^{2x}(2\cos x+\sin x),\\
I&=\tfrac15e^{2x}(2\cos x+\sin x)+C .
\end{aligned}
$$

> [!check] Differentiating back
> $\frac{\mathrm d}{\mathrm dx}\big[\frac15e^{2x}(2\cos x+\sin x)\big]=\frac15e^{2x}\big[2(2\cos x+\sin x)+(-2\sin x+\cos x)\big]=\frac15e^{2x}(5\cos x)=e^{2x}\cos x$. The general formula with $a=2$, $b=1$ gives the same answer.

## 7. The trapezium rule (James §8.10.1)

### The rule, derived

Divide $[a,b]$ into $n$ strips of equal width $h=\frac{b-a}n$, with points $x_r=a+rh$ and ordinates $f_r=f(x_r)$ for $r=0,1,\dots,n$. Replace the curve across each strip by the chord joining its end points. The $r$th strip becomes a trapezium of area $\frac12(f_r+f_{r+1})h$, and summing gives

$$
\begin{aligned}
\int_a^bf(x)\,\mathrm dx&\approx\sum_{r=0}^{n-1}\tfrac12(f_r+f_{r+1})h\\
&=\tfrac12h\big[(f_0+f_1)+(f_1+f_2)+\dots+(f_{n-1}+f_n)\big]\\
&=h\big[\tfrac12(f_0+f_n)+f_1+f_2+\dots+f_{n-1}\big].
\end{aligned}
$$

Every interior ordinate appears in two neighbouring trapezia, so it carries weight $h$; the two end ordinates carry $\frac12h$. The estimate with strip width $h$ is written $T(h)$.

### Interval halving

Halving $h$ keeps every old point and adds a new one in the middle of each old strip. With $n$ strips of width $h$ ($n$ even), the even-numbered points $f_0,f_2,\dots,f_n$ are the points of $T(2h)$:

$$
\begin{aligned}
T(h)&=h\big[\tfrac12(f_0+f_n)+f_1+f_2+\dots+f_{n-1}\big],\\
T(2h)&=2h\big[\tfrac12(f_0+f_n)+f_2+f_4+\dots+f_{n-2}\big].
\end{aligned}
$$

Split $T(h)$ into its odd and even ordinates; the even part is half of $T(2h)$:

$$
\begin{aligned}
T(h)&=h(f_1+f_3+\dots+f_{n-1})+h\big[\tfrac12(f_0+f_n)+f_2+\dots+f_{n-2}\big]\\
&=h(f_1+f_3+\dots+f_{n-1})+\tfrac12T(2h).
\end{aligned}
$$

Only the new (odd) ordinates have to be evaluated at each halving.

### Why the error is proportional to h squared

For one strip of width $h$ with midpoint $m$, write $x=m+t$, $-\frac h2\le t\le\frac h2$. Assume $f$ has a continuous second derivative and expand in a Taylor series about $m$:

$$
f(m+t)=f(m)+tf'(m)+\tfrac12t^2f''(m)+\dots
$$

Integrate over the strip. The odd term $t f'(m)$ integrates to zero over the symmetric range:

$$
\int_{-h/2}^{h/2}f(m+t)\,\mathrm dt=hf(m)+\tfrac12f''(m)\cdot\frac{2}{3}\Big(\frac h2\Big)^3+\dots=hf(m)+\frac{h^3}{24}f''(m)+\dots
$$

The trapezium uses the two end values, where $t=\pm\frac h2$; the $f'$ terms cancel again:

$$
\tfrac h2\Big[f\big(m-\tfrac h2\big)+f\big(m+\tfrac h2\big)\Big]=hf(m)+\frac{h^3}{8}f''(m)+\dots
$$

Subtract to get the error on one strip:

$$
\text{(trapezium)}-\text{(exact)}=\Big(\frac18-\frac1{24}\Big)h^3f''(m)+\dots=\frac{h^3}{12}f''(m)+\dots
$$

There are $n=\frac{b-a}h$ strips, and $\sum hf''(m_r)\approx\int_a^bf''\,\mathrm dx=f'(b)-f'(a)$, so

$$
T(h)-\int_a^bf\,\mathrm dx\approx\frac{h^2}{12}\big[f'(b)-f'(a)\big].
$$

The error is proportional to $h^2$: halving $h$ divides it by about 4. It is positive when $f''>0$, because the chords of a curve that bends upwards lie above it.

### Estimating the error and Richardson extrapolation

Write the error as $T(h)-I\approx Ah^2$, where $I$ is the exact integral and $A$ stays roughly constant as $h$ shrinks. Then $T(2h)-I\approx4Ah^2$. Subtracting eliminates the unknown $I$:

$$
\begin{aligned}
T(2h)-T(h)&\approx3Ah^2,\\
T(h)-I\approx Ah^2&\approx\tfrac13\big[T(2h)-T(h)\big].
\end{aligned}
$$

So two trapezium values give an estimate of the error in the better one, without knowing $I$. Subtracting that estimated error from $T(h)$ gives an improved value, **Richardson extrapolation**:

$$
\begin{aligned}
I&\approx T(h)-\tfrac13\big[T(2h)-T(h)\big]\\
&=\tfrac13\big[4T(h)-T(2h)\big].
\end{aligned}
$$

This removes the $h^2$ term of the error. The usual practice is to keep halving until two successive extrapolated values agree to the accuracy required.

### The integral of 1/x from 1 to 2 (Example 8.72)

The exact value is $\ln2=0.693147$, which makes this a test of the method. With $n=4$, $h=0.25$, the ordinates are $f_0=1$, $f_1=0.8$, $f_2=0.666667$, $f_3=0.571429$, $f_4=0.5$:

$$
T(0.25)=0.25\big[\tfrac12(1+0.5)+0.8+0.666667+0.571429\big]=0.697024 .
$$

Halving to $h=0.125$ needs only the four new ordinates at $x=1.125,1.375,1.625,1.875$, which are $0.888889$, $0.727273$, $0.615385$, $0.533333$:

$$
\begin{aligned}
T(0.125)&=0.125(0.888889+0.727273+0.615385+0.533333)+\tfrac12(0.697024)\\
&=0.345610+0.348512\\
&=0.694122 .
\end{aligned}
$$

Continuing the halving:

| $n$ | $h$ | $T(h)$ | error $T(h)-\ln2$ | estimate $\tfrac13[T(2h)-T(h)]$ | $\tfrac{h^2}{12}[f'(2)-f'(1)]=\tfrac{h^2}{16}$ |
|---|---|---|---|---|---|
| 1 | 1 | 0.750000 | 0.05685 | | 0.06250 |
| 2 | 0.5 | 0.708333 | 0.01519 | 0.01389 | 0.01563 |
| 4 | 0.25 | 0.697024 | 0.00388 | 0.00377 | 0.00391 |
| 8 | 0.125 | 0.694122 | 0.00098 | 0.00097 | 0.00098 |
| 16 | 0.0625 | 0.693391 | 0.00024 | 0.00024 | 0.00024 |
| 32 | 0.03125 | 0.693208 | 0.00006 | 0.00006 | 0.00006 |
| 64 | 0.015625 | 0.693162 | 0.000015 | 0.000015 | 0.000015 |
| 128 | 0.0078125 | 0.693151 | 0.000004 | 0.000004 | 0.000004 |

For $f=1/x$, $f'=-1/x^2$, so $f'(2)-f'(1)=-\frac14+1=\frac34$ and the predicted error is $\frac{h^2}{16}$, the last column. The error falls by a factor of about 4 at each halving, and the plain trapezium rule needs $n=128$ strips before the error drops below $5\times10^{-6}$, the requirement for 5 d.p.

Extrapolation gets there far sooner. From $T(0.25)$ and $T(0.125)$, the estimated error in $T(0.125)$ is $\frac13(0.697024-0.694122)=0.000967$, so

$$
I\approx0.694122-0.000967=0.69315,
$$

correct to 5 d.p. with eight strips. From $T(0.125)$ and $T(0.0625)$, $\frac13[4T(0.0625)-T(0.125)]=0.6931477$. The extrapolated values have an error proportional to $h^4$, so the same idea applied to them, $\frac1{15}\big[16R(h)-R(2h)\big]$, gives $0.6931472$, which is $\ln2$ to 7 d.p.

$$
\int_1^2\frac{\mathrm dx}x=0.69315\ \text{(5 d.p.)}=\ln2 .
$$

![[m1054_m04_rule_errors.png|800]]

In the test the number of strips is normally prescribed and only the straightforward rule is needed (work scheme item 9); halving and extrapolation are the efficient way to organise a longer hand or computer calculation. Convergence is slower when the integrand changes slope rapidly, as $\sqrt x$ does near $x=0$, where $f'(0)$ is infinite and the $h^2$ error law fails.

## 8. Simpson's rule (James §8.10.2)

### The rule from a parabola

For two strips, from $x_0$ to $x_2$ with midpoint $x_1$, write $x=x_1+t$ for $-h\le t\le h$ and fit the parabola $p(t)=\alpha+\beta t+\gamma t^2$ through the three points $(x_0,f_0)$, $(x_1,f_1)$, $(x_2,f_2)$. The odd term $\beta t$ integrates to zero over the symmetric range:

$$
\int_{-h}^{h}p(t)\,\mathrm dt=2\alpha h+\tfrac23\gamma h^3 .
$$

The fitting conditions give $\alpha$ and $\gamma h^2$ directly, without solving for $\beta$:

$$
\begin{aligned}
p(0)=f_1\ &\Rightarrow\ \alpha=f_1,\\
p(h)+p(-h)=f_2+f_0\ &\Rightarrow\ 2\alpha+2\gamma h^2=f_0+f_2,\\
&\Rightarrow\ \gamma h^2=\tfrac12(f_0+f_2-2f_1).
\end{aligned}
$$

Substitute:

$$
\begin{aligned}
\int_{x_0}^{x_2}f\,\mathrm dx&\approx2hf_1+\tfrac h3(f_0+f_2-2f_1)\\
&=\tfrac h3\big(f_0+4f_1+f_2\big).
\end{aligned}
$$

### The composite rule

Divide $[a,b]$ into an **even** number $n$ of strips, so that they pair up into $\frac n2$ double strips, and apply the basic formula to each pair:

$$
\int_a^bf\,\mathrm dx\approx\tfrac h3\big[f_0+4f_1+f_2\big]+\tfrac h3\big[f_2+4f_3+f_4\big]+\dots+\tfrac h3\big[f_{n-2}+4f_{n-1}+f_n\big].
$$

Each even interior ordinate is shared by two pairs, so it appears twice:

$$
S=\frac h3\Big[f_0+f_n+4(f_1+f_3+\dots+f_{n-1})+2(f_2+f_4+\dots+f_{n-2})\Big].
$$

In words: one third of the strip width, times the sum of the first and last ordinates, four times the odd ordinates and twice the even ordinates.

![[m1054_trapezium_vs_simpson.png|900]]

### Simpson's rule is extrapolated trapezium

The same formula comes out of Richardson extrapolation. Write $T(h)$ and $T(2h)$ for $n$ strips ($n$ even) and form $4T(h)-T(2h)$:

$$
\begin{aligned}
4T(h)&=h\big[2f_0+2f_n+4(f_1+f_3+\dots+f_{n-1})+4(f_2+\dots+f_{n-2})\big],\\
T(2h)&=h\big[f_0+f_n+2(f_2+\dots+f_{n-2})\big],\\
4T(h)-T(2h)&=h\big[f_0+f_n+4(f_1+f_3+\dots+f_{n-1})+2(f_2+\dots+f_{n-2})\big],\\
\tfrac13\big[4T(h)-T(2h)\big]&=S .
\end{aligned}
$$

So Simpson's rule removes the $h^2$ error of the trapezium rule. For the hand calculation it is convenient, but on its own it gives no error estimate; a second trapezium value or a second Simpson value with $2h$ supplies one.

### Why the error is proportional to h to the fourth

Expand $f(x_1+t)$ in a Taylor series about the middle point. Simpson's formula integrates $1$ and $t^2$ exactly, because it is exact for any parabola, and it integrates $t$ and $t^3$ exactly because both the true integral and the formula give zero by symmetry ($-h^3+h^3=0$ for $t^3$). The first term it gets wrong is $\frac1{24}f''''(x_1)t^4$:

$$
\begin{aligned}
\tfrac h3\big[(-h)^4+4\cdot0+h^4\big]&=\tfrac23h^5,\\
\int_{-h}^{h}t^4\,\mathrm dt&=\tfrac25h^5,\\
\text{(Simpson)}-\text{(exact)}&=\tfrac1{24}f''''(x_1)\Big(\tfrac23-\tfrac25\Big)h^5=\frac{h^5}{90}f''''(x_1).
\end{aligned}
$$

Summing over the $\frac{b-a}{2h}$ pairs, with $\sum2h\,f''''\approx\int_a^bf''''\,\mathrm dx$, gives

$$
S-\int_a^bf\,\mathrm dx\approx\frac{h^4}{180}\big[f'''(b)-f'''(a)\big],
$$

so halving $h$ divides Simpson's error by about 16. It needs $f''''$ to be continuous.

### Specimen Test 4 Q4: the integral of 1/x by Simpson

| $x$ | 1.00 | 1.25 | 1.50 | 1.75 | 2.00 |
|---|---|---|---|---|---|
| $1/x$ | 1.000000 | 0.800000 | 0.666667 | 0.571429 | 0.500000 |

With $h=0.25$ and $n=4$:

$$
\begin{aligned}
S&=\frac{0.25}3\Big[1+0.5+4(0.8+0.571429)+2(0.666667)\Big]\\
&=\frac{0.25}3\big[1.5+5.485716+1.333334\big]\\
&=\frac{0.25}3(8.319048)\\
&=0.693254 .
\end{aligned}
$$

The error is $0.693254-0.693147=1.1\times10^{-4}$ with four strips, against $3.9\times10^{-3}$ for the trapezium rule with the same points. The $h^4$ formula predicts $\frac{0.25^4}{180}\big[f'''(2)-f'''(1)\big]=\frac{0.25^4}{180}\big(-\frac6{16}+6\big)=1.2\times10^{-4}$, since $f'''=-6/x^4$.

### The integral of the square root of 1 + x cubed (Exercise 142 and Exercise C)

$\sqrt{1+x^3}$ has no elementary antiderivative, so $\int_0^1\sqrt{1+x^3}\,\mathrm dx$ can only be evaluated numerically. With $h=0.1$:

| $x$ | 0 | 0.1 | 0.2 | 0.3 | 0.4 | 0.5 | 0.6 | 0.7 | 0.8 | 0.9 | 1.0 |
|---|---|---|---|---|---|---|---|---|---|---|---|
| $f$ | 1.000000 | 1.000500 | 1.003992 | 1.013410 | 1.031504 | 1.060660 | 1.102724 | 1.158879 | 1.229634 | 1.314914 | 1.414214 |

The sums are $f_0+f_{10}=2.414214$, odd ordinates $f_1+f_3+f_5+f_7+f_9=5.548363$, and even ordinates $f_2+f_4+f_6+f_8=4.367854$. Simpson's rule (Exercise 142):

$$
\begin{aligned}
S&=\frac{0.1}3\big[2.414214+4(5.548363)+2(4.367854)\big]\\
&=\frac{0.1}3\big[2.414214+22.193453+8.735708\big]\\
&=1.111446 .
\end{aligned}
$$

The trapezium rule with the same points (Exercise C):

$$
\begin{aligned}
T(0.1)&=0.1\big[\tfrac12(2.414214)+5.548363+4.367854\big]\\
&=0.1\times11.123324\\
&=1.112332 .
\end{aligned}
$$

A single Simpson value carries no information about its own accuracy. A second trapezium value, from the even points alone, supplies it:

$$
\begin{aligned}
T(0.2)&=0.2\big[\tfrac12(2.414214)+4.367854\big]=1.114992,\\
T(0.1)-I&\approx\tfrac13\big[T(0.2)-T(0.1)\big]=0.000887,\\
\tfrac13\big[4T(0.1)-T(0.2)\big]&=1.111446 .
\end{aligned}
$$

The trapezium value is about $9\times10^{-4}$ too large, and the extrapolated value is the Simpson value, as the algebra above requires.

> [!check] Against a high-accuracy value
> Adaptive quadrature gives $\int_0^1\sqrt{1+x^3}\,\mathrm dx=1.1114480$. The Simpson value is in error by $-2.2\times10^{-6}$ and the trapezium value by $+8.8\times10^{-4}$. The $h^2$ formula predicts $\frac{0.1^2}{12}\big[f'(1)-f'(0)\big]=\frac{0.01}{12}\cdot\frac3{2\sqrt2}=8.8\times10^{-4}$, since $f'(x)=\frac{3x^2}{2\sqrt{1+x^3}}$.

### Volume of a road cutting (Example 8.74)

A straight horizontal road 10 m wide is cut through rough ground 2 km long. The sides of the cutting and of the embankments slope at 2 horizontal to 1 vertical. The height $h$ of the ground above the road level (the datum PQ) is known every 200 m, and the net volume of earth removed is required.

The ground is sliced into thin slabs of thickness $\delta x$ across the road. A slab whose average cross-sectional area is $A$ has volume $A\,\delta x$; summing the slabs and letting $\delta x\to0$ gives

$$
V=\int_0^{2000}A(x)\,\mathrm dx .
$$

For a cutting ($h>0$) the cross-section is a trapezium of height $h$. Each sloping side runs $2h$ horizontally, so the top width is $10+4h$:

$$
\begin{aligned}
A&=\tfrac12\big[10+(10+4h)\big]h\\
&=(10+2h)h .
\end{aligned}
$$

For an embankment ($h<0$) the same shape, of height $\lvert h\rvert$, is filled in rather than removed, so it counts negative: $A=-(10+2\lvert h\rvert)\lvert h\rvert$. Both cases are $A=(10+2\lvert h\rvert)h$, so fill on site is netted off automatically.

![[m1054_m04_road_section.png|900]]

| $x$ (m) | 0 | 200 | 400 | 600 | 800 | 1000 | 1200 | 1400 | 1600 | 1800 | 2000 |
|---|---|---|---|---|---|---|---|---|---|---|---|
| $h$ (m) | 0 | 3.0 | 7.0 | 6.3 | 1.3 | −2.6 | −1.3 | 1.7 | 2.8 | −0.5 | 0 |
| $A$ (m²) | 0 | 48.0 | 168.0 | 142.4 | 16.4 | −39.5 | −16.4 | 22.8 | 43.7 | −5.5 | 0 |

The integrand is known only as a table, so it can only be integrated numerically. Simpson's rule with 10 strips of width 200 m:

$$
\begin{aligned}
\text{odd ordinates}&=48.0+142.4-39.5+22.8-5.5=168.2,\\
\text{even ordinates}&=168.0+16.4-16.4+43.7=211.7,\\
V&\approx\frac{200}3\big[0+0+4(168.2)+2(211.7)\big]\\
&=\frac{200}3(672.8+423.4)\\
&=\frac{200}3(1096.2)\\
&=73\,080\ \text{m}^3\approx7.3\times10^4\ \text{m}^3 .
\end{aligned}
$$

The trapezium rule with the same data gives $200\times(168.2+211.7)=75\,980$ m³. The heights are given to about 2 significant figures, so the volume is quoted as $7.3\times10^4$ m³; a better estimate needs more survey points, not more arithmetic.

![[m1054_m04_road_area.png|900]]

> [!check] Simpson from two trapezium values
> With $h=400$ m the trapezium rule uses only the even ordinates: $T(400)=400\times211.7=84\,680$ m³. Then $\frac13\big[4T(200)-T(400)\big]=\frac13(303\,920-84\,680)=73\,080$ m³, the Simpson value exactly.

## 9. Choosing a method

For an integral that is not obviously standard, work through these in order:

1. Simplify first: expand a product of polynomials, divide out a fraction such as $\frac{x+1}x$, or use a log law.
2. Check whether it is standard, or standard after a linear substitution $u=ax+b$ (§3, §4).
3. If it is a trigonometric power or product, apply the identities of §5.
4. If it is a product of two unlike functions, integrate by parts (§6), with $u$ chosen by LIATE.
5. If there is no closed form, or only data, use the trapezium or Simpson rule (§7, §8) and estimate the error.
6. Check an indefinite integral by differentiating it back.

## Terminology and alternative names

| Term used here | Also called | Note |
|---|---|---|
| Trapezium rule | trapezoidal rule | US usage, and the name in `np.trapz` and MATLAB `trapz` |
| Indefinite integral | antiderivative, primitive | James uses "antiderivative" in §8.8.1 |
| Linear substitution | linear composite rule (James Rule 3) | $\int f(ax+b)\,\mathrm dx=\frac1aF(ax+b)$ |
| Richardson extrapolation | extrapolated trapezium rule; repeated, it is Romberg integration | one extrapolation of $T(h)$ is Simpson's rule |
| $\sin^{-1}x$, $\tan^{-1}x$ | $\arcsin x$, $\arctan x$ | the booklet and James use the $^{-1}$ notation |

## Links

- Parent: [[MATH1054 Mathematics for Engineering and the Environment Hub]] · Solutions: [[MATH1054 M04 Solutions - Integration I]] · Formula sheet: [[MATH1054 Formula Sheet]] · Reference table: [[Integration Formulae]]
- Previous: [[MATH1054 M03 - Differentiation I]] (the derivatives read backwards here, and the product and chain rules behind parts and substitution: [[Product, Quotient and Chain Rules]])
- Next: [[MATH1054 M09 - Integration II]] (general substitution, applications) → [[MATH1054 M10 - Integration III]] (partial fractions, improper integrals) → [[MATH1054 M11 - Integration IV]] (multiple integrals)
- Concepts: [[Integration by Parts]] · [[Trigonometric Integrals and Power Reduction]] · [[Trapezium and Simpson's Rules]] · [[Integration by Substitution]] · [[Improper Integrals]] · [[Inverse Trigonometric Functions]] · [[Euler's Formula]]
- Later use: every Fourier coefficient in MATH2048 is an integration by parts plus the orthogonality of §5 ([[MATH2048 FS1 - Fourier Series, Orthogonality and the Euler Formulae]], whose $e^x$ series in [[MATH2048 FS1 - Fourier Series, Orthogonality and the Euler Formulae#The exponential, e to the x (PS3 Q1)|the exponential example]] is the cyclic case; [[Orthogonality of Trigonometric Functions]]). The $h^2$ and $h^4$ error orders are the idea of [[Truncation Error and Order of Accuracy]] in SESA2029, and boundary-layer thicknesses are integrated by the trapezium rule in [[SESA2022 T2 - Boundary Layers]].

## Sources

- MATH1054 Module Booklet, Module 4 (Integration I), pp. 1–4 of the module (PDF pp. 5–8): work scheme items 1–10 based on James, Exercises A–C, and Specimen Test 4. The Data Book corrections in §5 are from work scheme item 6.
- James, *Modern Engineering Mathematics* (6th ed.): §8.7.1 (definition, Example 8.38), §8.7.4–8.7.5 (indefinite integrals, Theorem 8.1), §8.8.1 (Fig. 8.56, Rules 1–4, Examples 8.43–8.44), §8.8.4 (Example 8.51), §8.8.10 (Example 8.56), §8.10.1 (formulae 8.47–8.48, Example 8.72), §8.10.2 (formula 8.49, Example 8.74). Exercises 104–106 (§8.8.3, p. 645), 110–111 (§8.8.5, p. 649), 119–120 (§8.8.11, p. 656), 142 (§8.10.3, p. 688).
- Worked solutions to every set item: [[MATH1054 M04 Solutions - Integration I]].

## Self-study tasks

### Core

- [ ] Exercises 110(a)–(d) and 111(a) (Module 04 work scheme): integration by parts, including the cyclic 110(d). → [[MATH1054 M04 Solutions - Integration I#Exercises 110, 111(a) (p.649): Integration by parts]] · [[#6. Integration by parts (James §8.8.4)]]
- [ ] Exercise B, harder (Module 04 work scheme): $\int e^{2x}\cos x\,\mathrm dx$ by parts twice. → [[#Cyclic integrals set as exercises (Exercise 110(d) and Exercise B)]] · [[MATH1054 M04 Solutions - Integration I|solutions note, Booklet Exercise B]]
- [ ] Exercise A and Exercises 119(b), 120(a), 120(b) (Module 04 work scheme): trigonometric powers and products. → [[#Fourth power of cosine (Exercise A)]] · [[MATH1054 M04 Solutions - Integration I#Exercises 119(b), 120 (p.656): Product-to-sum]]
- [ ] Exercise 142 and Exercise C (Module 04 work scheme): Simpson and trapezium for $\int_0^1\sqrt{1+x^3}\,\mathrm dx$ with $h=0.1$. → [[#The integral of the square root of 1 + x cubed (Exercise 142 and Exercise C)]] · [[MATH1054 M04 Solutions - Integration I|solutions note, Exercise 142 and Booklet Exercise C]]
- [ ] Specimen Test 4, Q1–Q4. → [[MATH1054 M04 Solutions - Integration I#Part C: Specimen Test 4]]

### Further practice

- [ ] Exercises 104(a), (b), (c), (d), (f), 105(c) and 106(b) (Module 04 work scheme): standard integrals. → [[MATH1054 M04 Solutions - Integration I#Exercise 104 (p.645)]] · [[MATH1054 M04 Solutions - Integration I#Exercise 105(c), 106(b) (p.645)]]
- [ ] Examples 8.43(a), (b), (d) and 8.44 (Module 04 work scheme, items 3–4): rules 1 and 2 and definite integrals. → [[MATH1054 M04 Solutions - Integration I#Example 8.43: Indefinite integrals]] · [[MATH1054 M04 Solutions - Integration I#Example 8.44: Definite integrals]]
- [ ] Example 8.56 (Module 04 work scheme, item 6): $\cos^2x$ and $\sin(5x+1)\cos(x+2)$. → [[MATH1054 M04 Solutions - Integration I#Example 8.56: Trigonometric integrals]]
- [ ] Example 8.72 (Module 04 work scheme, item 9): trapezium rule with interval halving and extrapolation for $\int_1^2\frac{\mathrm dx}x$. → [[#The integral of 1/x from 1 to 2 (Example 8.72)]]
- [ ] Example 8.74 (Module 04 work scheme, item 10): road-cutting volume by Simpson's rule. → [[MATH1054 M04 Solutions - Integration I#Example 8.74: Earth removed for a road cutting]] · [[#Volume of a road cutting (Example 8.74)]]

## Transcript and slide slips

> [!warning] James Example 8.74, p. 687: cross-sectional area for an embankment
> Where: [[#Volume of a road cutting (Example 8.74)]]
>
> James gives $A=(2h+10)h$ for every section, but the negative entries in his table (−39.5, −16.4 and −5.5 m² at $h=-2.6,-1.3,-0.5$ m) come from $A=-(2\lvert h\rvert+10)\lvert h\rvert$, the embankment of the same shape. The printed formula with negative $h$ would give −12.5, −9.6 and −4.5 m². The table, and so the answer $7.3\times10^4$ m³, is correct; the formula holds only for $h\ge0$, and $A=(10+2\lvert h\rvert)h$ covers both cases.
