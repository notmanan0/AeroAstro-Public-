---
title: "MATH1054 M03 - Differentiation I"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: topic
stream: "Block 1: Calculus"
order: 3
tags:
  - math1054
  - calculus
  - differentiation
  - newton-raphson
  - partial-derivatives
aliases: ["MATH1054 Module 3", "Differentiation I"]
date: 2026-09-27
status: lectured
coverage: "Module Booklet Module 3 work scheme; James §8.2 (definition, tangents, rates), §8.3.1–8.3.12 (rules, powers, polynomials, rational functions, chain and inverse-function rules, circular, exponential and logarithmic functions), §8.4 to Example 8.27 (higher derivatives), §9.4.8 (Newton–Raphson), §9.6.2 (partial derivatives)"
parent: ["[[MATH1054 Mathematics for Engineering and the Environment Hub]]"]
prerequisites: []
next_topics: ["[[MATH1054 M04 - Integration I]]", "[[MATH1054 M08 - Differentiation II]]"]
key_concepts: ["[[Derivative from First Principles]]", "[[Product, Quotient and Chain Rules]]", "[[Direct Substitution and Newton-Raphson]]", "[[Partial Derivatives]]"]
tutorial_sheets: ["[[MATH1054 M03 Solutions - Differentiation I]]"]
sources: ["02 - Sources/Course Booklets & Solutions/Module Booklet.pdf (Module 3)", "02 - Sources/Modern Engineering Mathematics.pdf (§8.2–8.4, §9.4.8, §9.6)"]
---

# MATH1054 M03 - Differentiation I

> [!abstract] Summary
> The derivative of $f$ at $x$ is the limit of the chord slope $\big(f(x+\Delta x)-f(x)\big)/\Delta x$ as $\Delta x\to0$: the slope of the tangent to the graph and the instantaneous rate of change of $f$. The sum, product, quotient, chain and inverse-function rules, all derived from that limit, reduce the derivative of any elementary function to a short table of standard derivatives. Two applications follow: the Newton–Raphson iteration $x_{n+1}=x_n-f(x_n)/f'(x_n)$, which refines an approximate root of $f(x)=0$ by following the tangent to the axis, and partial derivatives of a function of two variables, taken with respect to one variable while the other is held constant.

> [!summary]- Exam use: quick path
> - **Use it when:** a question asks for a derivative of an explicit function, a tangent or normal, a velocity or acceleration, a better approximation to a root of $f(x)=0$, or $\partial f/\partial x$ and $\partial f/\partial y$.
> - **Assumptions:** angles in radians; $\ln x$ needs $x>0$ and $\sqrt{\cdot}$ a non-negative argument; Newton–Raphson needs $f'(x_n)\neq0$ and a start near a simple root.
> - **Method:** 1. Simplify first: roots as powers, log laws, expand short products. 2. Name the outermost operation (sum, product, quotient or function of a function). 3. Apply its rule and work inwards until only standard derivatives remain. 4. Factor the result. 5. For a root, write the equation as $f(x)=0$, tabulate $x_n$, $f(x_n)$, $f'(x_n)$ and stop when successive iterates agree to the accuracy asked for.
> - **Common mistakes:** dropping the derivative of the inside function ($\frac{\mathrm d}{\mathrm dx}\cos x^4=-4x^3\sin x^4$, not $-\sin x^4$); applying Newton–Raphson to $g(x)=C$ without first subtracting $C$.
> - **Practise:** [[#A product of powers (Example 8.16(c))]] · [[MATH1054 M03 Solutions - Differentiation I#Q2: Differentiate|Specimen Test 3, Q2]]

A derivative measures how fast one quantity changes as another changes. The distance a vehicle has travelled is a function $s(t)$ of time; its velocity is the rate $\mathrm ds/\mathrm dt$ and its acceleration the rate of that rate. The deflection of a beam, the temperature along a fin and the lift on a wing against angle of attack are all functions whose slopes matter as much as their values. Geometrically the derivative at a point is the slope of the tangent to the graph there, the line that the curve looks like under enough magnification.

The definition as a limit is used directly only a few times: to find the derivatives of $x^n$, $\sin x$ and $e^x$, and to prove the rules for combining functions. After that, differentiation is mechanical. A function such as $e^{-2x}\sin2x$ or $\sqrt{2x+1}/(x^2+1)^3$ is built from a handful of standard functions by adding, multiplying, dividing and nesting, and each of those operations has a rule. Reading the structure of the function correctly, so that the right rule is applied in the right order, is most of the work.

The tangent line is also a tool. Replacing a curve by its tangent near a point turns a hard equation $f(x)=0$ into a linear one, and solving that repeatedly is the Newton–Raphson method, used whenever an equation such as $x\tan x=4$ has no closed-form solution. The same equation, $\lambda\tan\lambda=\mathrm{Bi}$, fixes the eigenvalues for transient heat conduction in a slab with convective faces, and Newton–Raphson in matrix form solves the nonlinear equations of finite element analysis. Most engineering quantities depend on several variables, for example temperature $T(x,y,z,t)$, and the partial derivative isolates the dependence on one of them.

The reverse of differentiation is integration ([[MATH1054 M04 - Integration I|M04]]). Inverse and hyperbolic functions and their derivatives are in [[MATH1054 M07 - Functions|M07]]; implicit, parametric and logarithmic differentiation, stationary points and Maclaurin series are in [[MATH1054 M08 - Differentiation II|M08]]. Checking that a function satisfies a differential equation (Section 4) leads into [[MATH1054 M06 - Differential Equations I|M06]]; partial derivatives are used in the exactness test of [[MATH1054 M12 - Differential Equations II|M12]] and in the gradient and PDEs of MATH2048.

---

## 1. The derivative as a limit (James §8.2)

### Chord slope and tangent slope

Take two points on the graph of $y=f(x)$, at $x$ and $x+\Delta x$. The chord joining them rises by $\Delta y=f(x+\Delta x)-f(x)$ over a run of $\Delta x$, so its slope is the **difference quotient**

$$
\frac{\Delta y}{\Delta x}=\frac{f(x+\Delta x)-f(x)}{\Delta x}.
$$

As $\Delta x$ shrinks, the second point slides along the curve onto the first and the chord turns into the tangent. The **derivative** is the limiting slope:

$$
f'(x)=\frac{\mathrm df}{\mathrm dx}=\lim_{\Delta x\to0}\frac{f(x+\Delta x)-f(x)}{\Delta x}.
$$

The notations $f'(x)$, $\dfrac{\mathrm dy}{\mathrm dx}$ and, for a function of time, $\dot y$ all mean the same thing. The limit exists only if the quotient approaches the same value whether $\Delta x$ is positive or negative.

![[m1054_m03_chord_to_tangent.png|820]]

The figure uses $f(x)=25x-5x^2$ from Example 8.2. From $P(1,20)$, chords with $\Delta x=2,\ 1,\ 0.5$ have slopes $5,\ 10,\ 12.5$. The general chord slope is $15-5\Delta x$ (derived below), which tends to the tangent slope $15$.

### First principles: worked cases

Finding a derivative from the definition is called working **from first principles**. The method is the same each time: expand $f(x+\Delta x)$, subtract $f(x)$ so that every term without a $\Delta x$ cancels, divide by $\Delta x$, and let $\Delta x\to0$.

For $f(x)=x^2$ (Example 8.1(a)):

$$
\begin{aligned}
f(x+\Delta x)-f(x)&=(x+\Delta x)^2-x^2\\
&=x^2+2x\,\Delta x+(\Delta x)^2-x^2\\
&=2x\,\Delta x+(\Delta x)^2,\\
\frac{f(x+\Delta x)-f(x)}{\Delta x}&=2x+\Delta x,\\
f'(x)&=\lim_{\Delta x\to0}(2x+\Delta x)=2x.
\end{aligned}
$$

For $f(x)=x^2-2$ (Exercise 1(c)) the constant cancels in the subtraction, $(x+\Delta x)^2-2-(x^2-2)=2x\,\Delta x+(\Delta x)^2$, and the derivative is again $2x$. This is why a constant differentiates to zero. For $f(x)=mx+c$ (Example 8.1(c)) the difference is $m\,\Delta x$, the quotient is exactly $m$ for every $\Delta x$, and $f'(x)=m$: a straight line has constant slope.

For $f(x)=1/x$ with $x\neq0$ (Example 8.1(b)), put the two fractions over a common denominator:

$$
\begin{aligned}
f(x+\Delta x)-f(x)&=\frac1{x+\Delta x}-\frac1x\\
&=\frac{x-(x+\Delta x)}{x(x+\Delta x)}\\
&=\frac{-\Delta x}{x(x+\Delta x)},\\
\frac{f(x+\Delta x)-f(x)}{\Delta x}&=\frac{-1}{x(x+\Delta x)},\\
f'(x)&=-\frac1{x^2}.
\end{aligned}
$$

For $f(x)=2x^2$ (Specimen Test 3, Q1(ii)):

$$
\begin{aligned}
f(x+\Delta x)-f(x)&=2(x+\Delta x)^2-2x^2\\
&=4x\,\Delta x+2(\Delta x)^2,\\
\frac{f(x+\Delta x)-f(x)}{\Delta x}&=4x+2\Delta x,\\
f'(x)&=4x.
\end{aligned}
$$

For $f(x)=25x-5x^2$ (Example 8.2(a)):

$$
\begin{aligned}
f(x+\Delta x)-f(x)&=25\,\Delta x-5\big[(x+\Delta x)^2-x^2\big]\\
&=25\,\Delta x-10x\,\Delta x-5(\Delta x)^2,\\
\frac{f(x+\Delta x)-f(x)}{\Delta x}&=25-10x-5\Delta x,\\
f'(x)&=25-10x.
\end{aligned}
$$

At $x=1$ the quotient is $15-5\Delta x$, the chord slope in the figure.

### Where a derivative does not exist

A function is **differentiable** at $x$ when the limit exists there. Roughly, the graph must have no break and no corner. For $f(x)=|x|$ at $x=0$ the difference quotient is $|\Delta x|/\Delta x$, which equals $+1$ for every $\Delta x>0$ and $-1$ for every $\Delta x<0$. The one-sided limits disagree, so $|x|$ has no derivative at $0$, although it is continuous there. Differentiability is the stronger condition: a differentiable function is continuous, because $f(x+\Delta x)-f(x)=\Delta x\cdot\frac{\Delta f}{\Delta x}\to0\cdot f'(x)=0$.

### Tangents, normals and rates of change

The tangent at $(x_0,y_0)$ has slope $m=f'(x_0)$ and passes through the point, so

$$
y-y_0=f'(x_0)(x-x_0).
$$

The **normal** is the line through the same point perpendicular to the tangent. Two lines with slopes $m_1$ and $m_2$ have direction vectors $(1,m_1)$ and $(1,m_2)$, which are perpendicular when their dot product vanishes:

$$
\begin{aligned}
(1,m_1)\cdot(1,m_2)&=0\\
1+m_1m_2&=0\\
m_2&=-\frac1{m_1}.
\end{aligned}
$$

So the normal is $y-y_0=-\dfrac1{f'(x_0)}(x-x_0)$, provided $f'(x_0)\neq0$; where the tangent is horizontal the normal is the vertical line $x=x_0$.

For Example 8.2, $f'(1)=25-10=15$ is the rate of change at $x=1$, and $f(1)=20$. The tangent at $(1,20)$ is

$$
\begin{aligned}
y-20&=15(x-1)\\
y&=15x+5,
\end{aligned}
$$

and the normal, with slope $-\tfrac1{15}$, is

$$
\begin{aligned}
y-20&=-\tfrac1{15}(x-1)\\
15y-300&=-x+1\\
x+15y&=301.
\end{aligned}
$$

A derivative with respect to time is a rate. For a displacement $s(t)$ the velocity is $v=\dot s$ and the acceleration is $a=\dot v=\ddot s$. In Example 8.12, $s=2t^3-1.5t^2-6t+12$ m, so

$$
\begin{aligned}
v&=\frac{\mathrm ds}{\mathrm dt}=6t^2-3t-6,& v(2)&=24-6-6=12\ \text{m s}^{-1},\\
a&=\frac{\mathrm dv}{\mathrm dt}=12t-3,& a(2)&=24-3=21\ \text{m s}^{-2}.
\end{aligned}
$$

## 2. The rules of differentiation (James §8.3.1, §8.3.6, §8.3.7)

Throughout, $u=u(x)$ and $v=v(x)$ are differentiable, and $\Delta u=u(x+\Delta x)-u(x)$, $\Delta v=v(x+\Delta x)-v(x)$.

### Constant multiple and sum

For a constant $k$, the difference quotient of $ku$ is $k\,\Delta u/\Delta x$, and the limit of a constant times a quotient is the constant times the limit. For $u+v$ the quotient is $\Delta u/\Delta x+\Delta v/\Delta x$, and the limit of a sum is the sum of the limits. Hence

$$
(ku)'=ku',\qquad(u\pm v)'=u'\pm v'.
$$

Together these say that differentiation is linear, so a polynomial is differentiated term by term. Example 8.11: $y=2x^4-2x^3-x^2+3x-2$ gives $y'=8x^3-6x^2-2x+3$.

### Product rule

Let $y=uv$. Add and subtract $u(x)v(x+\Delta x)$ in the increment:

$$
\begin{aligned}
\Delta y&=u(x+\Delta x)v(x+\Delta x)-u(x)v(x)\\
&=u(x+\Delta x)v(x+\Delta x)-u(x)v(x+\Delta x)+u(x)v(x+\Delta x)-u(x)v(x)\\
&=\big[u(x+\Delta x)-u(x)\big]v(x+\Delta x)+u(x)\big[v(x+\Delta x)-v(x)\big]\\
&=\Delta u\;v(x+\Delta x)+u(x)\,\Delta v,\\
\frac{\Delta y}{\Delta x}&=\frac{\Delta u}{\Delta x}\,v(x+\Delta x)+u(x)\,\frac{\Delta v}{\Delta x}.
\end{aligned}
$$

As $\Delta x\to0$, $v(x+\Delta x)\to v(x)$ because $v$ is differentiable and therefore continuous, so

$$
(uv)'=u'v+uv'.
$$

### Quotient rule

Let $y=u/v$ with $v\neq0$. Then $u=yv$, and the product rule gives

$$
\begin{aligned}
u'&=y'v+yv'\\
y'v&=u'-yv'\\
y'v&=u'-\frac uv\,v'\\
y'&=\frac{u'v-uv'}{v^2}.
\end{aligned}
$$

The order in the numerator matters: derivative of the top times the bottom comes first. A quotient can also be differentiated as the product $u\cdot v^{-1}$ using the chain rule below; the two routes give the same answer.

### Chain rule

Let $y=f(z)$ with $z=g(x)$, so $y=f(g(x))$ is a function of a function. An increment $\Delta x$ produces $\Delta z=g(x+\Delta x)-g(x)$, which in turn produces $\Delta y=f(z+\Delta z)-f(z)$. While $\Delta z\neq0$,

$$
\frac{\Delta y}{\Delta x}=\frac{\Delta y}{\Delta z}\cdot\frac{\Delta z}{\Delta x}.
$$

As $\Delta x\to0$, $\Delta z\to0$ because $g$ is continuous, so each factor tends to a derivative:

$$
\frac{\mathrm dy}{\mathrm dx}=\frac{\mathrm dy}{\mathrm dz}\cdot\frac{\mathrm dz}{\mathrm dx}=f'\big(g(x)\big)\,g'(x).
$$

The argument needs $\Delta z\neq0$ for small $\Delta x$, which holds when $g'(x)\neq0$; a more careful proof removes that restriction, and the rule holds for all differentiable $f$ and $g$. In words: differentiate the outer function with the inside left untouched, then multiply by the derivative of the inside. With several layers, repeat once per layer.

### Inverse-function rule

If $y=f^{-1}(x)$ then $x=f(y)$. For increments related by the inverse function, $\Delta y/\Delta x=1\big/(\Delta x/\Delta y)$, and $\Delta y\to0$ as $\Delta x\to0$ because the inverse of a continuous function on an interval is continuous. Hence

$$
\frac{\mathrm dy}{\mathrm dx}=\frac1{\mathrm dx/\mathrm dy},\qquad\frac{\mathrm dx}{\mathrm dy}\neq0.
$$

This rule gives the derivatives of $\ln x$ and the inverse trigonometric functions in Section 3, and of the inverse hyperbolic functions in [[MATH1054 M07 - Functions|M07]].

> [!tip] Simplify before you differentiate
> $\left(\sqrt x+\frac1{\sqrt x}\right)^2=x+2+x^{-1}$ needs no product or chain rule, and its derivative is $1-x^{-2}$ (Exercise 33(b)). $\ln\frac{x-2}{x-3}=\ln(x-2)-\ln(x-3)$ needs no quotient rule. $4x^7(x^2-3x)=4x^9-12x^8$ differentiates to $36x^8-96x^7=12x^7(3x-8)$ (Example 8.10(c)). Each rewrite removes a rule application and a chance to slip.

### Worked examples of the rules

#### Product of two polynomials (Example 8.10(b))

With $u=2x^2+5$, $u'=4x$, $v=x^2+3x+1$, $v'=2x+3$:

$$
\begin{aligned}
f'&=u'v+uv'\\
&=4x(x^2+3x+1)+(2x^2+5)(2x+3)\\
&=4x^3+12x^2+4x+4x^3+6x^2+10x+15\\
&=8x^3+18x^2+14x+15.
\end{aligned}
$$

#### Quotients (Example 8.10(e) and Example 8.14(a))

For $f=\sqrt x/(x+1)$, $x>0$, with $u=x^{1/2}$, $u'=\frac1{2\sqrt x}$, $v=x+1$, $v'=1$:

$$
\begin{aligned}
f'&=\frac{\frac1{2\sqrt x}(x+1)-\sqrt x}{(x+1)^2}\\
&=\frac{(x+1)-2x}{2\sqrt x\,(x+1)^2}\\
&=\frac{1-x}{2\sqrt x\,(x+1)^2}.
\end{aligned}
$$

The second line multiplies numerator and denominator by $2\sqrt x$. For $f=(3x+2)/(2x^2+1)$:

$$
\begin{aligned}
f'&=\frac{3(2x^2+1)-(3x+2)(4x)}{(2x^2+1)^2}\\
&=\frac{6x^2+3-12x^2-8x}{(2x^2+1)^2}\\
&=\frac{3-8x-6x^2}{(2x^2+1)^2}.
\end{aligned}
$$

A rational function whose denominator is a single power is easier term by term. Example 8.14(c) has $f=x^3+2x^2-x^{-1}+x^{-2}+3$ once divided out, so $f'=3x^2+4x+x^{-2}-2x^{-3}$.

#### Powers of a function (Examples 8.15 and 8.16)

For $y=(5x^2+11)^9$, put $z=5x^2+11$ so that $y=z^9$:

$$
\frac{\mathrm dy}{\mathrm dx}=\frac{\mathrm dy}{\mathrm dz}\cdot\frac{\mathrm dz}{\mathrm dx}=9z^8\cdot10x=90x(5x^2+11)^8.
$$

The general pattern is $\dfrac{\mathrm d}{\mathrm dx}u^n=nu^{n-1}u'$. For $y=(5x^2-2)^{-7}$ it gives $y'=-7(5x^2-2)^{-8}\cdot10x=-70x/(5x^2-2)^8$, and for $y=\sqrt{3x^2+1}$ it gives $y'=\frac12(3x^2+1)^{-1/2}\cdot6x=3x/\sqrt{3x^2+1}$.

#### A product of powers (Example 8.16(c))

For $y=(x^2+1)^3\sqrt{x-1}$, $x>1$, the outermost operation is a product, and each factor needs the chain rule:

$$
\begin{aligned}
u&=(x^2+1)^3,& u'&=3(x^2+1)^2\cdot2x=6x(x^2+1)^2,\\
v&=(x-1)^{1/2},& v'&=\tfrac12(x-1)^{-1/2}.
\end{aligned}
$$

Then

$$
\begin{aligned}
y'&=6x(x^2+1)^2\sqrt{x-1}+\frac{(x^2+1)^3}{2\sqrt{x-1}}\\
&=\frac{(x^2+1)^2\big[12x(x-1)+(x^2+1)\big]}{2\sqrt{x-1}}\\
&=\frac{(x^2+1)^2(13x^2-12x+1)}{2\sqrt{x-1}}.
\end{aligned}
$$

The second line puts both terms over $2\sqrt{x-1}$ and takes out the common factor $(x^2+1)^2$, which is the step that keeps the answer compact.

#### A quotient of powers (Example 8.16(d))

For $y=\sqrt{2x+1}/(x^2+1)^3$, $x>-\tfrac12$, take $u=(2x+1)^{1/2}$, $u'=(2x+1)^{-1/2}$, $v=(x^2+1)^3$, $v'=6x(x^2+1)^2$:

$$
\begin{aligned}
y'&=\frac{(2x+1)^{-1/2}(x^2+1)^3-(2x+1)^{1/2}\,6x(x^2+1)^2}{(x^2+1)^6}\\
&=\frac{(x^2+1)-6x(2x+1)}{\sqrt{2x+1}\,(x^2+1)^4}\\
&=\frac{1-6x-11x^2}{\sqrt{2x+1}\,(x^2+1)^4}.
\end{aligned}
$$

The second line multiplies top and bottom by $(2x+1)^{1/2}$ and cancels $(x^2+1)^2$.

## 3. Derivatives of the standard functions (James §8.3.2, §8.3.9, §8.3.12)

### Powers of x

For a positive integer $n$, the binomial theorem gives

$$
\begin{aligned}
(x+\Delta x)^n-x^n&=nx^{n-1}\Delta x+\binom n2x^{n-2}(\Delta x)^2+\dots+(\Delta x)^n,\\
\frac{(x+\Delta x)^n-x^n}{\Delta x}&=nx^{n-1}+\binom n2x^{n-2}\Delta x+\dots+(\Delta x)^{n-1},\\
\frac{\mathrm d}{\mathrm dx}x^n&=nx^{n-1},
\end{aligned}
$$

since every term after the first carries at least one factor of $\Delta x$. The result holds for every real power $r$ (derived below, after $e^x$ and $\ln x$): $\dfrac{\mathrm d}{\mathrm dx}x^r=rx^{r-1}$. To use it, rewrite roots and reciprocals as powers first (Example 8.9):

$$
\frac{\mathrm d}{\mathrm dx}\sqrt x=\tfrac12x^{-1/2}=\frac1{2\sqrt x},\qquad\frac{\mathrm d}{\mathrm dx}\frac1{x^5}=-5x^{-6},\qquad\frac{\mathrm d}{\mathrm dx}\frac1{\sqrt[3]x}=-\tfrac13x^{-4/3}.
$$

### Sine and cosine

The sum-to-product identity $\sin A-\sin B=2\cos\frac{A+B}2\sin\frac{A-B}2$ with $A=x+\Delta x$, $B=x$ gives

$$
\begin{aligned}
\sin(x+\Delta x)-\sin x&=2\cos\!\big(x+\tfrac12\Delta x\big)\sin\!\big(\tfrac12\Delta x\big),\\
\frac{\sin(x+\Delta x)-\sin x}{\Delta x}&=\cos\!\big(x+\tfrac12\Delta x\big)\cdot\frac{\sin\frac12\Delta x}{\frac12\Delta x}.
\end{aligned}
$$

As $\Delta x\to0$ the first factor tends to $\cos x$ and the second to $1$, using $\lim_{\theta\to0}(\sin\theta)/\theta=1$ for $\theta$ in radians. So $\dfrac{\mathrm d}{\mathrm dx}\sin x=\cos x$. The identity $\cos A-\cos B=-2\sin\frac{A+B}2\sin\frac{A-B}2$ gives in the same way

$$
\frac{\cos(x+\Delta x)-\cos x}{\Delta x}=-\sin\!\big(x+\tfrac12\Delta x\big)\cdot\frac{\sin\frac12\Delta x}{\frac12\Delta x}\ \longrightarrow\ -\sin x .
$$

> [!warning] Radians only
> The limit $(\sin\theta)/\theta\to1$ holds only when $\theta$ is in radians: $\sin(0.1)/0.1=0.998334$ and $\sin(0.01)/0.01=0.999983$. With $x$ in degrees, $\sin x^\circ=\sin(\pi x/180)$ and the chain rule gives $\frac{\mathrm d}{\mathrm dx}\sin x^\circ=\frac{\pi}{180}\cos x^\circ=0.017453\cos x^\circ$. Every trigonometric derivative in this module assumes radians.

### Tangent, secant, cosecant and cotangent

These follow from $\sin$ and $\cos$ with the quotient and chain rules. For $\tan x=\sin x/\cos x$:

$$
\begin{aligned}
\frac{\mathrm d}{\mathrm dx}\tan x&=\frac{\cos x\cdot\cos x-\sin x\cdot(-\sin x)}{\cos^2x}\\
&=\frac{\cos^2x+\sin^2x}{\cos^2x}\\
&=\frac1{\cos^2x}=\sec^2x.
\end{aligned}
$$

For $\sec x=(\cos x)^{-1}$:

$$
\frac{\mathrm d}{\mathrm dx}\sec x=-(\cos x)^{-2}(-\sin x)=\frac{\sin x}{\cos^2x}=\sec x\tan x .
$$

In the same way $\dfrac{\mathrm d}{\mathrm dx}\operatorname{cosec}x=-(\sin x)^{-2}\cos x=-\operatorname{cosec}x\cot x$, and for $\cot x=\cos x/\sin x$ the quotient rule gives $\dfrac{-\sin^2x-\cos^2x}{\sin^2x}=-\operatorname{cosec}^2x$. These four are on the formula sheet; the derivatives of $\sin$ and $\cos$, with the minus sign in the right place, have to be known.

### Exponential and logarithm

Factor $e^x$ out of the increment and use the series $e^{\Delta x}=1+\Delta x+\frac{(\Delta x)^2}{2!}+\frac{(\Delta x)^3}{3!}+\dots$:

$$
\begin{aligned}
\frac{e^{x+\Delta x}-e^x}{\Delta x}&=e^x\,\frac{e^{\Delta x}-1}{\Delta x}\\
&=e^x\Big(1+\frac{\Delta x}{2}+\frac{(\Delta x)^2}{6}+\dots\Big),\\
\frac{\mathrm d}{\mathrm dx}e^x&=e^x.
\end{aligned}
$$

Numerically, $(e^{0.01}-1)/0.01=1.005017$. The exponential is its own derivative, and the chain rule gives $\frac{\mathrm d}{\mathrm dx}e^{ax}=ae^{ax}$.

For $y=\ln x$, $x>0$, the inverse function is $x=e^y$:

$$
\begin{aligned}
\frac{\mathrm dx}{\mathrm dy}&=e^y=x,\\
\frac{\mathrm dy}{\mathrm dx}&=\frac1{\mathrm dx/\mathrm dy}=\frac1x .
\end{aligned}
$$

Neither result is on the formula sheet.

### Real powers

For $x>0$ and any real $r$, write $x^r=e^{r\ln x}$ and use the chain rule:

$$
\begin{aligned}
\frac{\mathrm d}{\mathrm dx}x^r&=\frac{\mathrm d}{\mathrm dx}e^{r\ln x}\\
&=e^{r\ln x}\cdot\frac rx\\
&=x^r\cdot\frac rx=rx^{r-1}.
\end{aligned}
$$

### Inverse trigonometric functions

These are treated fully in [[MATH1054 M07 - Functions|M07]] ([[Inverse Trigonometric Functions]]); the derivatives come straight from the inverse-function rule. Let $y=\sin^{-1}x$ for $|x|<1$, so $x=\sin y$ with $y$ on the principal branch $[-\tfrac\pi2,\tfrac\pi2]$:

$$
\begin{aligned}
\frac{\mathrm dx}{\mathrm dy}&=\cos y=+\sqrt{1-\sin^2y}=\sqrt{1-x^2},\\
\frac{\mathrm dy}{\mathrm dx}&=\frac1{\sqrt{1-x^2}}.
\end{aligned}
$$

The positive root is taken because $\cos y\geq0$ on that branch. For $y=\cos^{-1}x$, $x=\cos y$ with $y\in[0,\pi]$, where $\sin y\geq0$, so $\mathrm dx/\mathrm dy=-\sin y=-\sqrt{1-x^2}$ and $\mathrm dy/\mathrm dx=-1/\sqrt{1-x^2}$. For $y=\tan^{-1}x$, $\mathrm dx/\mathrm dy=\sec^2y=1+\tan^2y=1+x^2$, so $\mathrm dy/\mathrm dx=1/(1+x^2)$ for every real $x$.

### Table and chain-rule forms

| $f(x)$ | $f'(x)$ | $f(x)$ | $f'(x)$ |
|---|---|---|---|
| $x^r$ ($r\in\mathbb R$) | $rx^{r-1}$ | $\sin^{-1}x$ | $\dfrac1{\sqrt{1-x^2}}$ |
| $e^{ax}$ | $ae^{ax}$ | $\cos^{-1}x$ | $-\dfrac1{\sqrt{1-x^2}}$ |
| $\ln x$ | $\dfrac1x$ | $\tan^{-1}x$ | $\dfrac1{1+x^2}$ |
| $\sin x$ | $\cos x$ | $\sec x$ | $\sec x\tan x$ |
| $\cos x$ | $-\sin x$ | $\operatorname{cosec}x$ | $-\operatorname{cosec}x\cot x$ |
| $\tan x$ | $\sec^2x$ | $\cot x$ | $-\operatorname{cosec}^2x$ |

With the chain rule each entry generalises to a function $u(x)$:

$$
\frac{\mathrm d}{\mathrm dx}u^n=nu^{n-1}u',\quad\frac{\mathrm d}{\mathrm dx}e^u=u'e^u,\quad\frac{\mathrm d}{\mathrm dx}\ln u=\frac{u'}u,\quad\frac{\mathrm d}{\mathrm dx}\sin u=u'\cos u,\quad\frac{\mathrm d}{\mathrm dx}\cos u=-u'\sin u .
$$

### Worked examples with standard functions

Examples 8.17(a)–(e) and 8.19, each a single rule applied once:

| $y$ | rule | $\dfrac{\mathrm dy}{\mathrm dx}$ |
|---|---|---|
| $\sin(2x+3)$ | chain | $2\cos(2x+3)$ |
| $x^2\cos x$ | product | $2x\cos x-x^2\sin x$ |
| $\dfrac{\sin2x}{x^2+2}$ | quotient | $\dfrac{2(x^2+2)\cos2x-2x\sin2x}{(x^2+2)^2}$ |
| $\sec6x$ | chain | $6\sec6x\tan6x$ |
| $x\tan2x$ | product | $\tan2x+2x\sec^22x$ |
| $x^2e^x$ | product | $x(x+2)e^x$ |
| $3e^{-2x}$ | chain | $-6e^{-2x}$ |
| $\dfrac{\ln x}{x^2}$ | quotient | $\dfrac{1-2\ln x}{x^3}$ |
| $\ln(x^2+1)$ | chain | $\dfrac{2x}{x^2+1}$ |
| $e^{-x}(\sin x+\cos x)$ | product | $-2e^{-x}\sin x$ |

The last entry simplifies because the cosines cancel: $-e^{-x}(\sin x+\cos x)+e^{-x}(\cos x-\sin x)=-2e^{-x}\sin x$.

#### Three layers (Example 8.18(a))

$y=\sin^2(x^2+1)=\big[\sin(x^2+1)\big]^2$ has a square outside, a sine in the middle and $x^2+1$ inside, so three factors appear:

$$
\begin{aligned}
y'&=2\sin(x^2+1)\cdot\cos(x^2+1)\cdot2x\\
&=2x\cdot2\sin(x^2+1)\cos(x^2+1)\\
&=2x\sin\big(2(x^2+1)\big),
\end{aligned}
$$

using $2\sin A\cos A=\sin2A$ in the last line.

#### Inverse trigonometric compositions (Examples 8.17(f)–(h) and 8.18(b))

$\frac{\mathrm d}{\mathrm dx}\sin^{-1}6x=\dfrac{6}{\sqrt{1-36x^2}}$ and $\frac{\mathrm d}{\mathrm dx}\big(x^2\cos^{-1}x\big)=2x\cos^{-1}x-\dfrac{x^2}{\sqrt{1-x^2}}$. For $y=\tan^{-1}u$ with $u=\dfrac{2x}{1+x^2}$, $y'=u'/(1+u^2)$:

$$
\begin{aligned}
u'&=\frac{2(1+x^2)-2x\cdot2x}{(1+x^2)^2}=\frac{2(1-x^2)}{(1+x^2)^2},\\
1+u^2&=\frac{(1+x^2)^2+4x^2}{(1+x^2)^2}=\frac{x^4+6x^2+1}{(1+x^2)^2},\\
y'&=\frac{2(1-x^2)}{x^4+6x^2+1}.
\end{aligned}
$$

For $y=\cos^{-1}u$ with $u=\sqrt{1-x^2}$ and $0<|x|<1$, $u'=-x/\sqrt{1-x^2}$ and $1-u^2=x^2$:

$$
\begin{aligned}
y'&=-\frac{u'}{\sqrt{1-u^2}}\\
&=\frac{x}{\sqrt{x^2}\,\sqrt{1-x^2}}\\
&=\frac{x}{|x|\sqrt{1-x^2}}=\begin{cases}\dfrac1{\sqrt{1-x^2}},&0<x<1,\\[2mm]-\dfrac1{\sqrt{1-x^2}},&-1<x<0.\end{cases}
\end{aligned}
$$

> [!warning] The square root of a square is a modulus
> $\sqrt{x^2}=|x|$, not $x$. Writing $x$ in the last example gives $1/\sqrt{1-x^2}$ everywhere, which is wrong for $x<0$: at $x=-0.3$ the derivative is $-1.048285$. For $0<x<1$ the function equals $\sin^{-1}x$, which is why the two derivatives agree there.

## 4. Higher derivatives (James §8.4)

Differentiating $f'$ gives the **second derivative** $f''=\dfrac{\mathrm d^2f}{\mathrm dx^2}=\dfrac{\mathrm d}{\mathrm dx}\Big(\dfrac{\mathrm df}{\mathrm dx}\Big)$, and so on to $f^{(n)}$. Acceleration is the second derivative of displacement, and the sign of $f''$ decides the shape of a stationary point in [[MATH1054 M08 - Differentiation II|M08]].

For $y=\dfrac{x}{x^2+1}$ (Example 8.27(b)), the quotient rule gives $y'=\dfrac{(x^2+1)-2x^2}{(x^2+1)^2}=\dfrac{1-x^2}{(x^2+1)^2}$. Differentiate again with $u=1-x^2$, $u'=-2x$, $v=(x^2+1)^2$, $v'=4x(x^2+1)$:

$$
\begin{aligned}
y''&=\frac{-2x(x^2+1)^2-(1-x^2)\cdot4x(x^2+1)}{(x^2+1)^4}\\
&=\frac{-2x(x^2+1)-4x(1-x^2)}{(x^2+1)^3}\\
&=\frac{-2x^3-2x-4x+4x^3}{(x^2+1)^3}\\
&=\frac{2x(x^2-3)}{(x^2+1)^3}.
\end{aligned}
$$

Cancelling the common factor $(x^2+1)$ before expanding, as in the second line, is the step that keeps a second derivative manageable. The other parts of Example 8.27 follow the same pattern: $y=e^{-x}\sin2x$ has $y'=e^{-x}(2\cos2x-\sin2x)$ and $y''=-e^{-x}(4\cos2x+3\sin2x)$, and $y=\dfrac{\ln x}{x}$ has $y'=\dfrac{1-\ln x}{x^2}$ and $y''=\dfrac{2\ln x-3}{x^3}$. Exercise 60(a), $y=x^3\sqrt{1+x^2}$, gives $y'=\dfrac{4x^4+3x^2}{\sqrt{1+x^2}}$ and $y''=\dfrac{x(12x^4+19x^2+6)}{(1+x^2)^{3/2}}$.

### Checking a solution of a differential equation (Exercise 62)

Show that $y=3e^{2x}\cos(2x-3)$ satisfies $y''-4y'+8y=0$. Write $c=\cos(2x-3)$ and $s=\sin(2x-3)$, so $c'=-2s$ and $s'=2c$:

$$
\begin{aligned}
y&=3e^{2x}c,\\
y'&=6e^{2x}c+3e^{2x}(-2s)=6e^{2x}(c-s),\\
y''&=12e^{2x}(c-s)+6e^{2x}(-2s-2c)\\
&=e^{2x}(12c-12s-12s-12c)=-24e^{2x}s,\\
y''-4y'+8y&=e^{2x}\big[-24s-24c+24s+24c\big]=0 .
\end{aligned}
$$

This is a preview of [[MATH1054 M06 - Differential Equations I|M06]]: the auxiliary equation $r^2-4r+8=0$ has roots $r=2\pm2j$, so every solution has the form $e^{2x}(A\cos2x+B\sin2x)=Re^{2x}\cos(2x+\phi)$, and the given $y$ is the case $R=3$, $\phi=-3$.

## 5. Newton–Raphson iteration (James §9.4.8)

### The iteration from the tangent line

Let $x_n$ be an approximation to a root $x=a$ of $f(x)=0$. The tangent to $y=f(x)$ at $x_n$ is

$$
y=f(x_n)+f'(x_n)(x-x_n).
$$

The next approximation $x_{n+1}$ is where this tangent crosses the axis. Set $y=0$ and solve:

$$
\begin{aligned}
0&=f(x_n)+f'(x_n)(x_{n+1}-x_n)\\
x_{n+1}-x_n&=-\frac{f(x_n)}{f'(x_n)}\\
x_{n+1}&=x_n-\frac{f(x_n)}{f'(x_n)},\qquad n=0,1,2,\dots
\end{aligned}
$$

This formula is on the formula sheet (the Data Book calls it Newton's method). It cannot be used when $f'(x_n)=0$, because the tangent is then parallel to the axis.

![[m1054_newton_raphson.png|560]]

### Why convergence is fast near a simple root

Let $e_n=x_n-a$ be the error, and suppose $f'(a)\neq0$ (a simple root). Expand $f$ and $f'$ about the root with Taylor's theorem ([[Taylor and Maclaurin Series]]), using $f(a)=0$:

$$
\begin{aligned}
f(x_n)&=f'(a)e_n+\tfrac12f''(a)e_n^2+\dots,\\
f'(x_n)&=f'(a)+f''(a)e_n+\dots
\end{aligned}
$$

Subtract $a$ from both sides of the iteration and write $k=f''(a)/f'(a)$:

$$
\begin{aligned}
e_{n+1}&=e_n-\frac{f'(a)e_n+\frac12f''(a)e_n^2}{f'(a)+f''(a)e_n}\\
&=e_n-e_n\,\frac{1+\frac12ke_n}{1+ke_n}\\
&\approx e_n-e_n\big(1+\tfrac12ke_n\big)\big(1-ke_n\big)\\
&\approx e_n-e_n\big(1-\tfrac12ke_n\big)\\
&=\frac{f''(a)}{2f'(a)}\,e_n^2 .
\end{aligned}
$$

The error is squared at each step, so near a simple root the number of correct digits roughly doubles per iteration. This is **quadratic** (second-order) convergence.

> [!check] The error ratio for the cube root of 7
> For $f=x^3-7$, $a=\sqrt[3]7=1.912931$ and $f''(a)/2f'(a)=6a/6a^2=1/a=0.5228$. From $x_0=2$ the errors are $e_0=0.087069$, $e_1=0.003735$, $e_2=7.28\times10^{-6}$, and the ratios $e_1/e_0^2=0.4927$ and $e_2/e_1^2=0.5214$ approach $0.5228$ as the iterates close in.

### Choosing the equation and the starting value

The method needs the equation in the form $f(x)=0$. An equation $g(x)=C$ becomes $f(x)=g(x)-C=0$ first: $x^3=7$ becomes $x^3-7=0$, and $x\tan x=4$ becomes $x\tan x-4=0$. Among equivalent forms, choose one that is smooth near the root; multiplying $x\tan x-4$ by $\cos x$, which is nonzero on $(0,\tfrac\pi2)$, gives $x\sin x-4\cos x=0$ with the same roots there and no asymptote.

When no starting value is given, tabulate $f$ at convenient points and look for a sign change. A continuous $f$ that changes sign between two points has a root between them. Start at the end of the bracket nearer the root, or where $|f|$ is smaller, and away from any point where $f'$ is close to zero. Stop when two successive iterates agree to the accuracy required, and quote the root to that accuracy.

### When the iteration fails

The iteration fails, or finds the wrong root, in three ways. If $f'(x_n)=0$ the formula divides by zero. If $f'(x_n)$ is small the correction $f(x_n)/f'(x_n)$ is large and the next iterate is thrown far away, possibly to a different root. If the curve bends sharply between $x_n$ and the root, as near an asymptote, the tangent overshoots. A repeated root, where $f'(a)=0$ as well, slows convergence to first order.

> [!warning] Starting next to a stationary point
> In Exercise 26 below, $f'(x)=4(x-4)(x-1)(x+2)$. Starting at $x_0=4$, an obvious guess between the sign change at 3 and 5, gives $f'(4)=0$ and no $x_1$. Starting at $x_0=1.5$ gives $x_1=3.8179$, then $x_2=0.8978$, close to the stationary point $x=1$ where $f'(0.8978)=3.67$ is small, so $x_3=-11.30$; the iteration then converges to the negative root $-2.8730$, not to either positive root.

### The cube root of 7 (Booklet Example A)

Given that $x^3=7$ has the approximate root $x=2$, find three further approximations to 4 d.p. With $f=x^3-7$ and $f'=3x^2$:

$$
\begin{aligned}
x_{n+1}&=x_n-\frac{x_n^3-7}{3x_n^2}\\
&=\frac{3x_n^3-x_n^3+7}{3x_n^2}\\
&=\frac{2x_n^3+7}{3x_n^2}.
\end{aligned}
$$

| $n$ | $x_n$ | $f(x_n)$ | $f'(x_n)$ |
|---|---|---|---|
| 0 | 2 | 1 | 12 |
| 1 | 1.916667 | 0.041088 | 11.0208 |
| 2 | 1.912938 | 0.0000799 | 10.9780 |
| 3 | 1.912931 | | |

So $x_1=23/12=1.9167$, $x_2=1.9129$ and $x_3=1.9129$, and $\sqrt[3]7=1.912931$.

### The square root of 5 (Specimen Test 3, Q3)

With $f=x^2-5$ and $f'=2x$, the iteration is $x_{n+1}=x_n-\dfrac{x_n^2-5}{2x_n}=\dfrac12\Big(x_n+\dfrac5{x_n}\Big)$, the average of $x_n$ and $5/x_n$. From $x_0=2$:

$$
\begin{aligned}
x_1&=\tfrac12(2+2.5)=2.25,\\
x_2&=\tfrac12\Big(2.25+\frac5{2.25}\Big)=\frac{161}{72}=2.2361,
\end{aligned}
$$

already correct to 4 d.p., since $\sqrt5=2.236068$.

### x tan x = 4 in two forms (Example 9.17)

Find the root near $x=1$ (radians). In the form $f(x)=x\tan x-4$, $f'(x)=\tan x+x\sec^2x$:

| $n$ | $x_n$ | $f(x_n)$ | $f'(x_n)$ |
|---|---|---|---|
| 0 | 1.000000 | −2.4426 | 4.9829 |
| 1 | 1.490192 | 14.4478 | 242.24 |
| 2 | 1.430551 | 6.1334 | 80.294 |
| 3 | 1.354164 | 2.1529 | 33.855 |
| 4 | 1.290572 | 0.4843 | 20.347 |
| 5 | 1.266769 | 0.0375 | 17.322 |
| 6 | 1.264607 | 0.00026 | 17.082 |
| 7 | 1.264592 | | |

The first step overshoots to $1.4902$, close to the asymptote of $\tan x$ at $\tfrac\pi2=1.5708$, because the tangent at $x_0=1$ is much shallower than the curve beyond the root. The iteration then creeps back from the high side and settles at $x=1.2646$. Starting at $x_0=1.2$ instead gives $1.277995$, $1.265171$, $1.264593$, correct to 4 d.p. in three steps.

In the form James uses, $g(x)=x\sin x-4\cos x$, $g'(x)=x\cos x+\sin x+4\sin x=x\cos x+5\sin x$, and from $x_0=1$ the iterates are $1.277977$, $1.264601$, $1.264592$: four figures after two steps, nine decimal places after four. The roots of $x\tan x=4$ lie in $(n\pi,n\pi+\tfrac\pi2)$, which is a good guide for choosing $x_0$ for the higher roots.

![[m1054_m03_newton_two_forms.png|900]]

### A quartic near 0.8 (Example 9.18)

Find the root of $8x^4+0.45x^3-4.544x-0.1136=0$ near $x=0.8$ to 4 s.f. Here $f'(x)=32x^3+1.35x^2-4.544$:

| $n$ | $x_n$ | $f(x_n)$ | $f'(x_n)$ | $-f(x_n)/f'(x_n)$ |
|---|---|---|---|---|
| 0 | 0.8 | −0.241600 | 12.7040 | 0.019018 |
| 1 | 0.819018 | 0.011681 | 13.9420 | −0.000838 |
| 2 | 0.818180 | 0.000023 | 13.8863 | −0.000002 |
| 3 | 0.818178 | | | |

$x_2$ and $x_3$ agree to 4 s.f., so $x=0.8182$. The corrections fall from $2\times10^{-2}$ to $8\times10^{-4}$ to $2\times10^{-6}$, roughly squaring each time. Keeping the iteration in the form "approximation minus correction", rather than combining it into one fraction, keeps the size of each correction visible.

### The positive roots of a quartic (Exercise 26, p.731)

Find the two positive roots of $f(x)=x^4-4x^3-12x^2+32x+28=0$. No starting values are given, so tabulate:

| $x$ | 0 | 1 | 2 | 3 | 4 | 5 | 6 |
|---|---|---|---|---|---|---|---|
| $f(x)$ | 28 | 45 | 28 | −11 | −36 | 13 | 220 |

The sign changes put the roots in $(2,3)$ and $(4,5)$. With $f'(x)=4x^3-12x^2-24x+32$, start each iteration at the end with the smaller $|f|$:

| Root in $(2,3)$, $x_0=3$ | $x_n$ | Root in $(4,5)$, $x_0=5$ | $x_n$ |
|---|---|---|---|
| $x_1=3-\frac{-11}{-40}$ | 2.725000 | $x_1=5-\frac{13}{112}$ | 4.883929 |
| $x_2$ | 2.732051 | $x_2$ | 4.873075 |
| $x_3$ | 2.732051 | $x_3$ | 4.872983 |

The positive roots are $x=2.7321$ and $x=4.8730$ (4 d.p.). The quartic factorises as $(x^2-2x-2)(x^2-2x-14)$, so the exact roots are $1\pm\sqrt3$ and $1\pm\sqrt{15}$; the positive ones are $1+\sqrt3=2.732051$ and $1+\sqrt{15}=4.872983$, and the others, $-0.7321$ and $-2.8730$, are negative.

![[m1054_m03_quartic_roots.png|860]]

## 6. Partial derivatives (James §9.6)

### Definition and notation

For a function $f(x,y)$ of two independent variables, the **partial derivative** with respect to $x$ is the ordinary derivative with respect to $x$ while $y$ is held constant:

$$
\frac{\partial f}{\partial x}=\lim_{\Delta x\to0}\frac{f(x+\Delta x,y)-f(x,y)}{\Delta x},\qquad\frac{\partial f}{\partial y}=\lim_{\Delta y\to0}\frac{f(x,y+\Delta y)-f(x,y)}{\Delta y}.
$$

The curly $\partial$ marks a partial derivative and distinguishes it from the ordinary $\mathrm d$; the subscript forms $f_x$ and $f_y$ mean the same. Because the other variable is a constant during the differentiation, every one-variable rule applies unchanged. For example $\dfrac{\partial}{\partial y}e^{-xy}=-xe^{-xy}$, since $x$ is a constant multiplier of $y$ in the exponent, while $\dfrac{\partial}{\partial x}e^{-xy}=-ye^{-xy}$. The same definition extends to $f(x,y,z,t)$, with all variables but one held fixed.

### Geometric meaning

The graph of $f(x,y)$ is a surface $z=f(x,y)$. Holding $y=y_0$ cuts the surface along a curve $z=f(x,y_0)$, and $\partial f/\partial x$ at $(x_0,y_0)$ is the slope of that curve, the slope of the surface in the $x$ direction. Likewise $\partial f/\partial y$ is the slope along the slice $x=x_0$.

![[m1054_m03_partial_slices.png|900]]

For $f=3x^2+2xy+y^3$ (Example 9.24(a)), holding $y$ constant makes $2xy$ a constant times $x$ and $y^3$ a constant, and holding $x$ constant makes $3x^2$ a constant:

$$
\frac{\partial f}{\partial x}=6x+2y,\qquad\frac{\partial f}{\partial y}=2x+3y^2 .
$$

At $(1,1)$, $f=6$, $f_x=8$ and $f_y=5$, the slopes of the two slices in the figure.

> [!check] Difference quotients at (1, 1)
> $\big(f(1.01,1)-f(1,1)\big)/0.01=8.03$ and $\big(f(1,1.01)-f(1,1)\big)/0.01=5.0301$, against $f_x=8$ and $f_y=5$. With a step of $0.1$ the quotients are $8.3$ and $5.31$; the error shrinks in proportion to the step.

Differentiating again gives second partial derivatives. Here $\dfrac{\partial}{\partial y}\Big(\dfrac{\partial f}{\partial x}\Big)=2$ and $\dfrac{\partial}{\partial x}\Big(\dfrac{\partial f}{\partial y}\Big)=2$; for functions with continuous second partials the mixed derivatives are always equal, $f_{xy}=f_{yx}$. That equality is the basis of the exactness test in [[MATH1054 M12 - Differential Equations II|M12]] and of conservative fields in MATH2048.

### Composite functions

When $f=f(u)$ depends on one variable $u$, and $u=u(x,y)$ on two, the chain rule reads

$$
\frac{\partial f}{\partial x}=\frac{\mathrm df}{\mathrm du}\,\frac{\partial u}{\partial x},\qquad\frac{\partial f}{\partial y}=\frac{\mathrm df}{\mathrm du}\,\frac{\partial u}{\partial y}.
$$

The derivative of $f$ with respect to $u$ is ordinary, because $f$ depends on $u$ alone; the derivatives of $u$ are partial, because $u$ depends on both $x$ and $y$. For $f=\sin(x^2-3y)$ (Example 9.25(b)), $u=x^2-3y$:

$$
\frac{\partial f}{\partial x}=\cos(x^2-3y)\cdot2x=2x\cos(x^2-3y),\qquad\frac{\partial f}{\partial y}=\cos(x^2-3y)\cdot(-3)=-3\cos(x^2-3y).
$$

### Worked examples of partial derivatives

#### A product with an exponential (Example 9.24(b))

$f=(y^2+x)e^{-xy}$. For $\partial f/\partial x$, the factors have $\partial_x(y^2+x)=1$ and $\partial_x e^{-xy}=-ye^{-xy}$:

$$
\begin{aligned}
\frac{\partial f}{\partial x}&=1\cdot e^{-xy}+(y^2+x)(-y)e^{-xy}\\
&=(1-xy-y^3)e^{-xy}.
\end{aligned}
$$

For $\partial f/\partial y$, $\partial_y(y^2+x)=2y$ and $\partial_y e^{-xy}=-xe^{-xy}$:

$$
\begin{aligned}
\frac{\partial f}{\partial y}&=2ye^{-xy}+(y^2+x)(-x)e^{-xy}\\
&=(2y-xy^2-x^2)e^{-xy}.
\end{aligned}
$$

#### Polynomials and powers (Example 9.25(a) and Exercise 39)

$f=xy^2+3xy-x+2$ gives $f_x=y^2+3y-1$ and $f_y=2xy+3x$. In Exercise 39, $f=x^3y+2x^2+9y^2+xy+10$ gives $f_x=3x^2y+4x+y$ and $f_y=x^3+18y+x$; $f=(x+y^2)^3$ gives $f_x=3(x+y^2)^2$ and $f_y=3(x+y^2)^2\cdot2y=6y(x+y^2)^2$. For a square root, $f=(3x^2+y^2+2xy)^{1/2}$:

$$
\begin{aligned}
f_x&=\tfrac12(3x^2+y^2+2xy)^{-1/2}(6x+2y)=\frac{3x+y}{\sqrt{3x^2+y^2+2xy}},\\
f_y&=\tfrac12(3x^2+y^2+2xy)^{-1/2}(2y+2x)=\frac{x+y}{\sqrt{3x^2+y^2+2xy}}.
\end{aligned}
$$

#### Specimen Test 3, Q4

For $f=x^2y^2+xy-x^2+y^2-5x$, $f_x=2xy^2+y-2x-5$ and $f_y=2x^2y+x+2y$. For $f=\ln(xy)$, defined where $xy>0$, the chain rule gives

$$
\frac{\partial f}{\partial x}=\frac{1}{xy}\cdot y=\frac1x,\qquad\frac{\partial f}{\partial y}=\frac{1}{xy}\cdot x=\frac1y .
$$

Splitting first as $\ln x+\ln y$ gives the same answer but is valid only for $x,y>0$; the chain-rule route also covers the quadrant where both are negative, for instance $f_x=-1$ at $(-1,-2)$.

## Worked examples

### Specimen Test 3, Q2 in full

Differentiate with respect to $x$.

(i) $6x^{1/4}$ gives $6\cdot\tfrac14x^{-3/4}=\tfrac32x^{-3/4}$. (ii) $2/x^3=2x^{-3}$ gives $-6x^{-4}=-6/x^4$. (iii) $(x^2+x+1)^3$ gives $3(x^2+x+1)^2(2x+1)$. (iv) $5+\cos(x^4)$ gives $-\sin(x^4)\cdot4x^3=-4x^3\sin(x^4)$. (vii) $\ln(2+\sin x)$ gives $\dfrac{\cos x}{2+\sin x}$.

(v) $e^{-2x}\sin2x$ is a product:

$$
\begin{aligned}
y'&=-2e^{-2x}\sin2x+e^{-2x}\cdot2\cos2x\\
&=2e^{-2x}(\cos2x-\sin2x).
\end{aligned}
$$

(vi) $\dfrac{x}{\sqrt{x^2+1}}$ is a quotient with $u=x$, $v=(x^2+1)^{1/2}$, $v'=x(x^2+1)^{-1/2}$:

$$
\begin{aligned}
y'&=\frac{\sqrt{x^2+1}-x\cdot\dfrac{x}{\sqrt{x^2+1}}}{x^2+1}\\
&=\frac{(x^2+1)-x^2}{(x^2+1)^{3/2}}\\
&=\frac1{(x^2+1)^{3/2}}.
\end{aligned}
$$

(viii) $\sin^2(x^3+1)$ has three layers, like Example 8.18(a):

$$
\begin{aligned}
y'&=2\sin(x^3+1)\cdot\cos(x^3+1)\cdot3x^2\\
&=3x^2\sin\big(2(x^3+1)\big).
\end{aligned}
$$

### A chain inside a product (Exercise 27(d))

$f=(x^2+x+1)^2(x^3+2x^2+1)^4$. Write $P=x^2+x+1$ and $Q=x^3+2x^2+1$, so $f=P^2Q^4$:

$$
\begin{aligned}
f'&=2P(2x+1)\,Q^4+P^2\cdot4Q^3(3x^2+4x)\\
&=2PQ^3\big[(2x+1)Q+2P(3x^2+4x)\big].
\end{aligned}
$$

The bracket expands to $(2x^4+5x^3+2x^2+2x+1)+(6x^4+14x^3+14x^2+8x)=8x^4+19x^3+16x^2+10x+1$, so

$$
f'=2(x^2+x+1)(x^3+2x^2+1)^3(8x^4+19x^3+16x^2+10x+1).
$$

Taking out the lowest power of each repeated factor before expanding is what keeps the final expression factorised.

## Terminology and alternative names

| Course term (James, booklet) | Also called | Note |
|---|---|---|
| Newton–Raphson procedure | Newton's method (Data Book) | Same iteration, $x_{n+1}=x_n-f(x_n)/f'(x_n)$ |
| $\sin^{-1}x$, $\cos^{-1}x$, $\tan^{-1}x$ | $\arcsin x$, $\arccos x$, $\arctan x$ | Not reciprocals: $\sin^{-1}x\neq1/\sin x$ |
| $\operatorname{cosec}x$ | $\csc x$ | $1/\sin x$ |
| $\partial f/\partial x$ | $f_x$, "curly dee" | Partial: other variables held constant |
| Composite-function rule | Chain rule, function-of-a-function rule | James Rule 5 |
| $\dfrac{\mathrm dy}{\mathrm dx}$, $f'(x)$ | $\dot y$ when the variable is time | Newton's dot notation |

## Links

- Parent: [[MATH1054 Mathematics for Engineering and the Environment Hub]] · Solutions: [[MATH1054 M03 Solutions - Differentiation I]] · Formula sheet: [[MATH1054 Formula Sheet]]
- Next: [[MATH1054 M04 - Integration I]] (the reverse operation) · [[MATH1054 M07 - Functions]] (inverse, inverse trigonometric and hyperbolic functions) · [[MATH1054 M08 - Differentiation II]] (implicit, parametric and logarithmic differentiation, stationary points, Maclaurin series)
- Later in MATH1054: [[MATH1054 M06 - Differential Equations I]] (checking and finding solutions of ODEs) · [[MATH1054 M12 - Differential Equations II]] (exact equations from partial derivatives) · [[MATH1054 M20 - Further Calculus II]] (L'Hôpital's rule)
- Concepts: [[Derivative from First Principles]] · [[Product, Quotient and Chain Rules]] · [[Partial Derivatives]] · [[Inverse Trigonometric Functions]] · [[Taylor and Maclaurin Series]]
- Year 2: [[MATH2048 VC1 - Scalar and Vector Fields, Gradient and Directional Derivatives]] and [[Gradient and Directional Derivative]] (the vector of partial derivatives) · [[MATH2048 PDE1 - Classification of PDEs and the Wave Equation]] (equations in partial derivatives) · [[SESA2029 A2 - Discrete Data, Finite Differences and Taylor Tables]] (the difference quotient with a finite step) · [[Direct Substitution and Newton-Raphson]] and [[SESA2029 B9 - Nonlinear FE Analysis]] (Newton–Raphson for nonlinear finite element equations)

## Sources

- MATH1054 Module Booklet, Module 3 (pp. 1–4): work scheme based on James, Booklet Example A, Specimen Test 3
- James, *Modern Engineering Mathematics* (6th ed.): §8.2 (pp. 544–552), §8.3.1–8.3.12 (pp. 561–591), §8.4 to Example 8.27 (pp. 597–601), §9.4.8 (pp. 728–731), §9.6 introduction and §9.6.2 (pp. 737–747; Exercise 39 on p.747)
- Worked solutions to every set example and exercise: [[MATH1054 M03 Solutions - Differentiation I]]

## Self-study tasks

### Core

- [ ] Exercises 25(e),(f), 26(a),(e), 27(d), 32(a),(e), 33(b),(d) (Module 03 work scheme, item 10): product, quotient and chain rules. → [[MATH1054 M03 Solutions - Differentiation I#Exercise 25 (p.572)]] · [[MATH1054 M03 Solutions - Differentiation I#Exercises 26, 27, 32, 33 (p.579): Chain rule]]
- [ ] Exercises 34(c),(f), 38(b),(e), 39(b),(c) (Module 03 work scheme, item 13): trigonometric, exponential and logarithmic functions. → [[MATH1054 M03 Solutions - Differentiation I#Exercise 34 (p.586)]] · [[MATH1054 M03 Solutions - Differentiation I#Exercises 38, 39 (p.591)]]
- [ ] Booklet Example A and Exercise 26 on p.731 (Module 03 work scheme, item 15): Newton–Raphson with and without a given start. → [[#The cube root of 7 (Booklet Example A)]] · [[#The positive roots of a quartic (Exercise 26, p.731)]]
- [ ] Exercise 39 on p.747 (Module 03 work scheme, item 17): partial derivatives. → [[MATH1054 M03 Solutions - Differentiation I#Exercise 39 (p.747): Partial derivatives]]
- [ ] Specimen Test 3, Q1–Q4, timed, without notes. → [[MATH1054 M03 Solutions - Differentiation I#Part C: Specimen Test 3]]

### Further practice

- [ ] Exercise 1(c) on p.552 (Module 03 work scheme, item 4): $x^2-2$ from first principles. → [[#First principles: worked cases]]
- [ ] Exercises 60(a), 62 on p.601 (Module 03 work scheme, item 14): second derivatives and an ODE check. → [[MATH1054 M03 Solutions - Differentiation I#Exercises 60(a), 62 (p.601)]]
- [ ] Examples 8.14 and 8.16 (Module 03 work scheme, items 8–9): rework without looking. → [[MATH1054 M03 Solutions - Differentiation I#Example 8.14: Rational functions]] · [[MATH1054 M03 Solutions - Differentiation I#Example 8.16]]
- [ ] Example 9.17 in both forms, $x\tan x-4$ and $x\sin x-4\cos x$, from $x_0=1$ (Module 03 work scheme, item 15). → [[#x tan x = 4 in two forms (Example 9.17)]]
- [ ] Examples 9.24 and 9.25 (Module 03 work scheme, item 17). → [[MATH1054 M03 Solutions - Differentiation I#Example 9.24: Partial derivatives]] · [[MATH1054 M03 Solutions - Differentiation I#Example 9.25]]
