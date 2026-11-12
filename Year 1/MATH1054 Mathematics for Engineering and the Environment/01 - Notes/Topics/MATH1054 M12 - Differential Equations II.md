---
title: "MATH1054 M12 - Differential Equations II"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: topic
stream: "Block 3: Differential Equations"
order: 12
tags:
  - math1054
  - odes
  - first-order-odes
  - integrating-factor
aliases: ["MATH1054 Module 12", "Differential Equations II"]
date: 2026-09-27
status: lectured
coverage: "Module Booklet Module 12 work scheme; James §10.5.5, §10.5.7, §10.5.9 (to Example 10.17), §10.2.2–10.2.3 and §10.7"
parent: ["[[MATH1054 Mathematics for Engineering and the Environment Hub]]"]
prerequisites: ["[[MATH1054 M06 - Differential Equations I]]", "[[MATH1054 M03 - Differentiation I]]"]
next_topics: ["[[MATH1054 M13 - Differential Equations III]]"]
key_concepts: ["[[Homogeneous First-Order ODEs]]", "[[Exact Differential Equations]]", "[[Integrating Factor Method]]"]
tutorial_sheets: ["[[MATH1054 M12 Solutions - Differential Equations II]]"]
sources: ["02 - Sources/Course Booklets & Solutions/Module Booklet.pdf (Module 12)", "02 - Sources/Modern Engineering Mathematics.pdf (§10.5.5, §10.5.7, §10.5.9, §10.2.2–10.2.3, §10.7)"]
---

# MATH1054 M12 - Differential Equations II

> [!abstract] Summary
> Three first-order equations that are not separable can still be solved exactly. An equation $\dot x=f(x/t)$ becomes separable under the substitution $x=ty$, because $\dot x=t\dot y+y$ by the product rule. An equation $p(t,x)\,\dot x+q(t,x)=0$ is exact, and has the implicit solution $h(t,x)=C$, precisely when $\partial p/\partial t=\partial q/\partial x$, a condition that comes from the equality of mixed partial derivatives. A linear equation $\dot x+p(t)x=r(t)$ is solved by multiplying by the integrating factor $g(t)=e^{\int p\,\mathrm dt}$, which turns the left-hand side into $\frac{\mathrm d}{\mathrm dt}(gx)$.

> [!summary]- Exam use: quick path
> - **Use it when:** a first-order ODE for $x(t)$ is to be classified or solved, and it is not obviously separable, as in Specimen Test 12.
> - **Assumptions:** $t>0$ wherever $\ln t$ or division by $t$ appears; the functions in the exactness test have continuous partial derivatives; the integrating-factor method needs the coefficient of $\dot x$ to be 1 first.
> - **Method:** 1. Test in the order separable, linear, $f(x/t)$, exact. 2. Linear: $g=e^{\int p\,\mathrm dt}$, then $(gx)'=gr$. 3. $f(x/t)$: put $x=ty$, separate $\int\frac{\mathrm dy}{f(y)-y}=\ln t+C$. 4. Exact: check $p_t=q_x$, integrate $p$ in $x$ with an unknown $C_1(t)$, match $h_t=q$. 5. Apply initial conditions last and pick the root that fits them.
> - **Common mistakes:** finding the integrating factor before dividing through by the coefficient of $\dot x$; writing the exact-equation "constant" of $x$-integration as a number instead of a function of $t$.
> - **Practise:** [[#Solving ẋ + tx = t (Example 10.17)]] · [[MATH1054 M12 Solutions - Differential Equations II#Part C: Specimen Test 12|Specimen Test 12]]

Most first-order equations do not separate into $G(x)\,\mathrm dx=F(t)\,\mathrm dt$ as they stand ([[MATH1054 M06 - Differential Equations I|Module 6]] solves those that do), but three further types can still be solved exactly. Each method turns the equation into something already solvable: a substitution makes it separable, a recognised total derivative makes it integrate in one step, or a multiplying factor creates such a total derivative. None of the three is new calculus. The substitution rests on the product rule, the exact method on the chain rule for a function of two variables, and the integrating factor on the product rule again.

The linear equation $\dot x+p(t)x=r(t)$ matters most in engineering. It is the model of anything that relaxes towards an equilibrium at a rate proportional to its distance from it: a capacitor charging through a resistor, the water in an insulated tank heated by a coil, the flow in a long pipe after a valve moves, a first-order sensor following its input. The integrating factor solves every such equation for which the integrals can be done, and its solution already splits into a decaying transient plus a forced response, which is the complementary function plus particular integral structure of second-order equations in [[MATH1054 M13 - Differential Equations III|Module 13]].

The exact method is the two-variable case of finding a potential. The solution curves of an exact equation are the contours of a function $h(t,x)$, and constructing $h$ from its two partial derivatives is the same calculation as finding the potential of a conservative vector field in MATH2048 ([[Conservative Vector Fields]]). Only mixed second derivatives and the two-variable chain rule are needed here; partial derivatives in general are treated in Module 19.

Throughout, $x$ is the dependent variable and $t$ the independent one, and $\dot x=\mathrm dx/\mathrm dt$. Data-book formulae written in $y$ and $x$ have to be translated into $x$ and $t$.

---

## 1. Equations of the form dx/dt = f(x/t) (James §10.5.5)

### Recognising the form

The right-hand side of $\dot x=F(t,x)$ is a function of $x/t$ alone when it is unchanged by scaling both variables by the same factor:

$$
F(\lambda t,\lambda x)=F(t,x)\quad\text{for every }\lambda>0 .
$$

If that holds, choose $\lambda=1/t$ (with $t>0$):

$$
\begin{aligned}
F(t,x)&=F\!\left(\tfrac1t\cdot t,\ \tfrac1t\cdot x\right)\\
&=F\!\left(1,\ \tfrac xt\right),
\end{aligned}
$$

which depends on $x/t$ only, so $F(t,x)=f(x/t)$ with $f(y)=F(1,y)$. For a ratio of polynomials the test reduces to checking that every term in the numerator and the denominator has the same total degree in $x$ and $t$. In $\dfrac{x^2+xt}{t^2}$ every term has degree 2; in $t^2-\dfrac xt$ the first term has degree 2 and the second degree 0, so that equation is not of this form.

These equations are sometimes called homogeneous equations. That use of "homogeneous" is unrelated to a homogeneous linear equation (one with zero forcing, James §10.3.4), so the course name is "equations of the form $\mathrm dx/\mathrm dt=f(x/t)$".

### The substitution x = ty, derived

Define a new dependent variable $y(t)=x/t$, so that

$$
x=ty .
$$

Differentiate with respect to $t$ by the product rule:

$$
\dot x=t\,\dot y+1\cdot y=t\,\dot y+y .
$$

Substitute into $\dot x=f(x/t)=f(y)$:

$$
t\,\dot y+y=f(y).
$$

Subtract $y$:

$$
t\,\dot y=f(y)-y .
$$

Divide by $t\,\big(f(y)-y\big)$, assuming $t>0$ and $f(y)\neq y$:

$$
\frac{1}{f(y)-y}\,\frac{\mathrm dy}{\mathrm dt}=\frac1t ,
$$

which is separable. Integrate both sides with respect to $t$:

$$
\int\frac{\mathrm dy}{f(y)-y}=\ln t+C ,
$$

and finally replace $y$ by $x/t$. Many books write the same substitution as $x=vt$; the Module 12 Specimen Test uses $x=yt$.

> [!warning] Solutions lost in the division
> Dividing by $f(y)-y$ discards every constant $y_0$ with $f(y_0)=y_0$. For each such root, $y=y_0$ satisfies $t\dot y=f(y)-y=0$, so the straight line $x=y_0t$ is a solution that the general formula may not contain. In Example 10.14 below $f(y)-y=y^2$, so $x=0$ is a solution outside the family $x=t/(A-\ln t)$.

![[m1054_m12_homogeneous_rays.png|900]]

The direction field shows why the substitution works. Along each ray $x=yt$ through the origin the slope is the same number $f(y)$, so the field is unchanged by stretching the picture away from the origin, and only the angle of a point, measured by $y=x/t$, matters. The ray $x=0$ is itself a solution, as the warning above predicts.

### Solving t²ẋ = x² + xt (Example 10.14)

Solve $t^2\dot x=x^2+xt$ for $t>0$, $x\neq0$.

Divide by $t^2$:

$$
\dot x=\left(\frac xt\right)^2+\frac xt ,
$$

so $f(y)=y^2+y$. With $x=ty$ and $\dot x=t\dot y+y$:

$$
\begin{aligned}
t\dot y+y&=y^2+y\\
t\dot y&=y^2\\
\int\frac{\mathrm dy}{y^2}&=\int\frac{\mathrm dt}{t}\\
-\frac1y&=\ln t+C\\
y&=-\frac{1}{\ln t+C}.
\end{aligned}
$$

Multiply by $t$ and write $A=-C$:

$$
x=\frac{-t}{\ln t+C}=\frac{t}{A-\ln t}.
$$

Substituting back, $\dot x=\dfrac{(A-\ln t)+1}{(A-\ln t)^2}$, so $t^2\dot x=\dfrac{t^2(A-\ln t+1)}{(A-\ln t)^2}$, and $x^2+xt=\dfrac{t^2}{(A-\ln t)^2}+\dfrac{t^2(A-\ln t)}{(A-\ln t)^2}$ is the same. Each solution blows up at $t=e^A$, where the denominator vanishes. Specimen Test 12 Q3 is this equation with the substitution $x=yt$ given.

### Exercise 18(b)

Solve $x^2\dot x=\dfrac{t^3+x^3}{t}$.

Divide by $x^2$:

$$
\dot x=\frac{t^2}{x^2}+\frac xt=\frac1{y^2}+y ,
$$

so $f(y)-y=1/y^2$. Then

$$
\begin{aligned}
t\dot y&=\frac{1}{y^2}\\
\int y^2\,\mathrm dy&=\int\frac{\mathrm dt}{t}\\
\tfrac13y^3&=\ln t+c\\
\frac{x^3}{t^3}&=3\ln t+C\qquad(C=3c)\\
x^3&=t^3\,(3\ln t+C),
\end{aligned}
$$

that is, $x=t\,(3\ln t+C)^{1/3}$, taking the real cube root.

### Exercise 20(d)

Solve $t\dot x=x+t\tan(x/t)$.

Divide by $t$: $\dot x=y+\tan y$, so $f(y)-y=\tan y$. Then

$$
\begin{aligned}
t\dot y&=\tan y\\
\int\cot y\,\mathrm dy&=\int\frac{\mathrm dt}{t}\\
\ln|\sin y|&=\ln t+c\\
\sin y&=At\qquad(A=\pm e^{c}),
\end{aligned}
$$

so

$$
x=t\sin^{-1}(At),
$$

on the interval where $|At|<1$ (at $|At|=1$, $y=\pm\tfrac12\pi$ and $\tan y$ is undefined). The value $A=0$ recovers the solution $x=0$, one of the lines $x=n\pi t$ lost when dividing by $\tan y$.

### Exercise 21(b), an initial-value problem

Solve $xt\,\dot x=2(x^2+t^2)$ with $x(2)=-1$.

Divide by $xt$:

$$
\dot x=\frac{2x}{t}+\frac{2t}{x}=2y+\frac2y ,
$$

so $f(y)-y=y+\dfrac2y=\dfrac{y^2+2}{y}$. Then

$$
\begin{aligned}
t\dot y&=\frac{y^2+2}{y}\\
\int\frac{y\,\mathrm dy}{y^2+2}&=\int\frac{\mathrm dt}{t}\\
\tfrac12\ln(y^2+2)&=\ln t+c\\
y^2+2&=At^2\qquad(A=e^{2c})\\
x^2&=At^4-2t^2 .
\end{aligned}
$$

Apply $x(2)=-1$:

$$
\begin{aligned}
(-1)^2&=16A-8\\
A&=\tfrac{9}{16}.
\end{aligned}
$$

The square root has two signs, and $x(2)<0$ selects the negative one:

$$
x=-t\sqrt{\tfrac{9}{16}t^2-2}=-\frac t4\sqrt{9t^2-32},
$$

valid for $t>\sqrt{32}/3=4\sqrt2/3\approx1.886$, where the root is real and $x\neq0$.

> [!check] Numerical integration
> A fourth-order Runge–Kutta integration of $\dot x=2(x^2+t^2)/(xt)$ from $x(2)=-1$ with step $10^{-4}$ gives $x(3)=-5.250000$. The formula gives $-\tfrac34\sqrt{81-32}=-\tfrac34\cdot7=-5.25$.

## 2. Exact equations (James §10.5.7)

### Mixed partial derivatives and the two-variable chain rule

Second partial derivatives are taken one variable at a time, holding the other fixed. For $f(x,y)=x^2y^2$,

$$
\frac{\partial f}{\partial x}=2xy^2,\qquad\frac{\partial f}{\partial y}=2x^2y,
$$

$$
\frac{\partial^2f}{\partial x^2}=\frac{\partial}{\partial x}\left(2xy^2\right)=2y^2,
$$

$$
\frac{\partial^2f}{\partial x\,\partial y}=\frac{\partial}{\partial x}\left(\frac{\partial f}{\partial y}\right)=\frac{\partial}{\partial x}\left(2x^2y\right)=4xy,
$$

$$
\frac{\partial^2f}{\partial y\,\partial x}=\frac{\partial}{\partial y}\left(\frac{\partial f}{\partial x}\right)=\frac{\partial}{\partial y}\left(2xy^2\right)=4xy .
$$

The two mixed derivatives agree. They agree for every function whose second partial derivatives are continuous (Schwarz's or Clairaut's theorem), and that equality is the whole basis of the exactness test.

Integrating a partial derivative works in reverse. The equation $\partial h/\partial x=x$ has the general solution

$$
h=\tfrac12x^2+c(t),
$$

because $t$ is held fixed during $x$-differentiation, so any function of $t$ alone has zero $x$-derivative. The constant of integration becomes an arbitrary function of the other variable.

The second tool is the chain rule for $h(t,x)$ when $x=x(t)$ is itself a function of $t$. Split the change in $h$ over a step $\Delta t$ into a change in $x$ at fixed $t+\Delta t$ and a change in $t$ at fixed $x$:

$$
\begin{aligned}
\Delta h&=h(t+\Delta t,\,x+\Delta x)-h(t,x)\\
&=\big[h(t+\Delta t,\,x+\Delta x)-h(t+\Delta t,\,x)\big]+\big[h(t+\Delta t,\,x)-h(t,x)\big]\\
&\approx\frac{\partial h}{\partial x}\,\Delta x+\frac{\partial h}{\partial t}\,\Delta t .
\end{aligned}
$$

Divide by $\Delta t$ and let $\Delta t\to0$:

$$
\frac{\mathrm dh}{\mathrm dt}=\frac{\partial h}{\partial x}\,\frac{\mathrm dx}{\mathrm dt}+\frac{\partial h}{\partial t}.
$$

### Exact equations and the test, derived

Write the first-order equation in the form

$$
p(t,x)\,\dot x+q(t,x)=0 . \tag{10.17}
$$

Suppose a function $h(t,x)$ exists with

$$
\frac{\partial h}{\partial x}=p(t,x),\qquad\frac{\partial h}{\partial t}=q(t,x). \tag{10.18}
$$

Then by the chain rule the left-hand side of (10.17) is

$$
p\,\dot x+q=\frac{\partial h}{\partial x}\,\dot x+\frac{\partial h}{\partial t}=\frac{\mathrm d}{\mathrm dt}\,h\big(t,x(t)\big),
$$

so (10.17) says $\mathrm dh/\mathrm dt=0$, and integrating once gives the solution

$$
h(t,x)=C .
$$

An equation for which such an $h$ exists is called **exact**. Whether $h$ exists is decided without finding it. If (10.18) holds, differentiate the first equation with respect to $t$ and the second with respect to $x$:

$$
\begin{aligned}
\frac{\partial p}{\partial t}&=\frac{\partial^2h}{\partial t\,\partial x},\\
\frac{\partial q}{\partial x}&=\frac{\partial^2h}{\partial x\,\partial t}.
\end{aligned}
$$

The mixed partials of $h$ are equal, so an exact equation must satisfy

$$
\frac{\partial p}{\partial t}=\frac{\partial q}{\partial x}. \tag{10.19}
$$

If (10.19) fails, no $h$ exists and the method does not apply.

### Constructing h

The test is also sufficient, on a rectangle in the $(t,x)$-plane where $p$, $q$ and their partial derivatives are continuous, and the proof is the construction used in every example. Integrate the first condition of (10.18) with respect to $x$, holding $t$ fixed:

$$
h(t,x)=P(t,x)+C_1(t),\qquad\text{where }P=\int p\,\mathrm dx,\ \text{so }\frac{\partial P}{\partial x}=p .
$$

Differentiate with respect to $t$ and impose the second condition:

$$
\begin{aligned}
\frac{\partial h}{\partial t}=\frac{\partial P}{\partial t}+C_1'(t)&=q\\
C_1'(t)&=q-\frac{\partial P}{\partial t}.
\end{aligned}
$$

The left side depends on $t$ only, so this can be solved for $C_1$ only if the right side has zero $x$-derivative. It does, by the test:

$$
\begin{aligned}
\frac{\partial}{\partial x}\left(q-\frac{\partial P}{\partial t}\right)&=\frac{\partial q}{\partial x}-\frac{\partial}{\partial t}\left(\frac{\partial P}{\partial x}\right)\\
&=\frac{\partial q}{\partial x}-\frac{\partial p}{\partial t}\\
&=0 .
\end{aligned}
$$

So the method is:

1. Check $\partial p/\partial t=\partial q/\partial x$.
2. Integrate $p$ with respect to $x$, adding an unknown function $C_1(t)$.
3. Differentiate the result with respect to $t$, set it equal to $q$, and solve for $C_1'(t)$; every $x$ must cancel, and if one does not, there is an algebra slip.
4. Integrate to find $C_1(t)$ and write $h(t,x)=C$, usually leaving the solution implicit.

An equivalent route (James §10.5.7) integrates both conditions separately, $h=\int p\,\mathrm dx+C_1(t)$ and $h=\int q\,\mathrm dt+C_2(x)$, and then reads off one function consistent with both. Terms that appear in both integrals are counted once, not twice.

> [!tip] Solutions are contours
> Because $h(t,x)=C$, each solution curve of an exact equation is a contour of the surface $h$, and the equation $p\dot x+q=0$ says the curve moves so that $h$ never changes. This is the same as following an equipotential of a conservative field, and constructing $h$ from $p$ and $q$ is finding that potential ([[Conservative Vector Fields]]).

### Solving 2xtẋ + x² − 2t = 0 (Example 10.15)

Solve $2xt\,\dot x+x^2-2t=0$.

Here $p=2xt$ and $q=x^2-2t$, so $\partial p/\partial t=2x=\partial q/\partial x$ and the equation is exact. Integrate $p$ in $x$:

$$
h=\int2xt\,\mathrm dx=x^2t+C_1(t).
$$

Match $\partial h/\partial t$ to $q$:

$$
\begin{aligned}
x^2+C_1'(t)&=x^2-2t\\
C_1'(t)&=-2t\\
C_1(t)&=-t^2 .
\end{aligned}
$$

The solution is $x^2t-t^2=C$, and for $t>0$ it can be made explicit as $x=\pm\sqrt{t+C/t}$.

### An implicit cubic solution with an initial condition (Example 10.16)

Solve $(\ln\sin t-3x^2)\,\dot x+x\cot t+4t=0$, on an interval where $\sin t>0$.

Here $p=\ln\sin t-3x^2$ and $q=x\cot t+4t$. The test:

$$
\frac{\partial p}{\partial t}=\frac{\cos t}{\sin t}=\cot t,\qquad\frac{\partial q}{\partial x}=\cot t ,
$$

so the equation is exact. Integrate $p$ in $x$:

$$
h=x\ln\sin t-x^3+C_1(t).
$$

Match $\partial h/\partial t$ to $q$:

$$
\begin{aligned}
x\cot t+C_1'(t)&=x\cot t+4t\\
C_1'(t)&=4t\\
C_1(t)&=2t^2 .
\end{aligned}
$$

The general solution is

$$
x\ln\sin t-x^3+2t^2=C ,
$$

a cubic in $x$ with coefficients that depend on $t$, so it is left implicit. With the initial condition $x(\tfrac12\pi)=3$, and $\ln\sin\tfrac12\pi=\ln1=0$,

$$
\begin{aligned}
C&=3\cdot0-3^3+2\left(\tfrac{\pi}{2}\right)^2\\
&=\tfrac{\pi^2}{2}-27\approx-22.065,
\end{aligned}
$$

so the particular solution is $x\ln\sin t-x^3+2t^2=\tfrac{\pi^2}{2}-27$, or $x^3-x\ln\sin t-2t^2+\tfrac{\pi^2}{2}-27=0$. At $t=\tfrac12\pi$, $x=3$ the left-hand side of the second form is $27-0-\tfrac{\pi^2}{2}+\tfrac{\pi^2}{2}-27=0$. The $2t^2$ term is evaluated at $t=\tfrac12\pi$, not at $t=0$ (see [[#Transcript and slide slips]]).

### Exercises 23(e) and 24(d)

Exercise 23(e) is $(x-t)\,\dot x-x+t-1=0$, with $p=x-t$ and $q=-x+t-1$. Then $\partial p/\partial t=-1=\partial q/\partial x$, so it is exact.

$$
\begin{aligned}
h&=\int(x-t)\,\mathrm dx=\tfrac12x^2-tx+C_1(t)\\
\frac{\partial h}{\partial t}&=-x+C_1'(t)=-x+t-1\\
C_1(t)&=\tfrac12t^2-t .
\end{aligned}
$$

So $h=\tfrac12x^2-tx+\tfrac12t^2-t=\tfrac12(x-t)^2-t$. Setting $h=C$ and writing $A=2C$:

$$
(x-t)^2=2t+A\quad\Longleftrightarrow\quad x=t\pm\sqrt{2t+A}.
$$

![[m1054_m12_exact_level_curves.png|900]]

The contours of $h=\tfrac12(x-t)^2-t$ are sideways parabolas, and the slope segments of $\dot x=1+1/(x-t)$ lie along them. Each contour has a vertical tangent where it crosses $x=t$, because the coefficient $p=x-t$ of $\dot x$ vanishes there; the $\pm$ in the explicit solution picks one half of a parabola.

Exercise 24(d) is $\cos t\,\dot x-x\sin t+1=0$ with $x(0)=2$. Here $p=\cos t$ and $q=-x\sin t+1$, so $\partial p/\partial t=-\sin t=\partial q/\partial x$. The first two terms are already $\frac{\mathrm d}{\mathrm dt}(x\cos t)$.

$$
\begin{aligned}
h&=x\cos t+C_1(t)\\
\frac{\partial h}{\partial t}&=-x\sin t+C_1'(t)=-x\sin t+1\\
C_1(t)&=t .
\end{aligned}
$$

So $x\cos t+t=C$. At $t=0$: $2\cdot1+0=C$, so $C=2$ and

$$
x=\frac{2-t}{\cos t},\qquad-\tfrac{\pi}{2}<t<\tfrac{\pi}{2}.
$$

Substituting back: $\dot x=\dfrac{-\cos t+(2-t)\sin t}{\cos^2t}$, so $\cos t\,\dot x=-1+x\sin t$ and the equation holds.

### Exercise 25(b), a non-exact equation

For $\sqrt t\,\dot x-xt=0$, $p=\sqrt t$ and $q=-xt$:

$$
\frac{\partial p}{\partial t}=\frac{1}{2\sqrt t},\qquad\frac{\partial q}{\partial x}=-t .
$$

These differ, so the equation is not exact. It is still solvable, since it separates:

$$
\begin{aligned}
\frac{\dot x}{x}&=\sqrt t\\
\ln|x|&=\tfrac23t^{3/2}+c\\
x&=Ae^{\frac23t^{3/2}}.
\end{aligned}
$$

Multiplying the original equation by $1/(x\sqrt t)$ gives $\dfrac1x\,\dot x-\sqrt t=0$, which has $p=1/x$, $q=-\sqrt t$ and $\partial p/\partial t=0=\partial q/\partial x$, so it is exact with $h=\ln|x|-\tfrac23t^{3/2}$. A multiplier that makes an equation exact is an **integrating factor**, and Section 3 builds one for every linear equation.

### Specimen Test 12, Q4

The condition for $p(x,t)\,\dot x+q(x,t)=0$ to be exact is $\partial p/\partial t=\partial q/\partial x$. For $(t+e^x)\,\dot x+2\cos t+x=0$, $\partial(t+e^x)/\partial t=1$ and $\partial(2\cos t+x)/\partial x=1$, so it is exact.

$$
\begin{aligned}
h&=\int(t+e^x)\,\mathrm dx=tx+e^x+C_1(t)\\
\frac{\partial h}{\partial t}&=x+C_1'(t)=2\cos t+x\\
C_1(t)&=2\sin t ,
\end{aligned}
$$

so the general solution is $tx+e^x+2\sin t=C$.

## 3. Linear equations and the integrating factor (James §10.5.9)

### The integrating factor, derived from the product rule

The most general first-order linear equation is

$$
\dot x+p(t)\,x=r(t). \tag{10.20}
$$

Multiply through by a function $g(t)>0$, to be chosen:

$$
g\,\dot x+g\,p\,x=g\,r .
$$

The product rule gives

$$
\frac{\mathrm d}{\mathrm dt}(g\,x)=g\,\dot x+\dot g\,x .
$$

The left-hand side above equals this derivative, for every solution $x$, exactly when

$$
\dot g=g\,p .
$$

That is a separable equation for $g$:

$$
\begin{aligned}
\frac{1}{g}\frac{\mathrm dg}{\mathrm dt}&=p(t)\\
\ln g&=\int p(t)\,\mathrm dt\\
g(t)&=e^{k(t)},\qquad k(t)=\int p(t)\,\mathrm dt .
\end{aligned}
$$

With this $g$, the equation becomes

$$
\frac{\mathrm d}{\mathrm dt}\big(g\,x\big)=g\,r .
$$

Integrate with respect to $t$:

$$
g\,x=\int g\,r\,\mathrm dt+C ,
$$

and divide by $g$:

$$
x=e^{-k(t)}\left[\int e^{k(t)}\,r(t)\,\mathrm dt+C\right]. \tag{10.22}
$$

No constant is needed in $k=\int p\,\mathrm dt$: replacing $k$ by $k+c_0$ multiplies $g$ by $e^{c_0}$, which multiplies both sides of $(gx)'=gr$ and cancels. Logarithms simplify through $e^{a\ln t}=t^{a}$ for $t>0$, so $e^{\ln t}=t$, $e^{-\ln t}=1/t$ and $e^{2\ln t}=t^2$.

### The same factor from the exactness test

The exactness test of Section 2 leads to the same $g$. Write $g\,\dot x+g\,(p\,x-r)=0$ in the form (10.17), with coefficient $g(t)$ of $\dot x$ and remainder $g(t)\big(p(t)x-r(t)\big)$. The exactness test (10.19) requires

$$
\begin{aligned}
\frac{\partial}{\partial t}\big(g\big)&=\frac{\partial}{\partial x}\big(g\,p\,x-g\,r\big)\\
\dot g&=g\,p ,
\end{aligned}
$$

the same equation for $g$. The integrating factor is the multiplier that makes a linear equation exact, which is the origin of the name: $\dot x+px$ is not the derivative of anything simple, but $g\dot x+gpx$ is.

### The four-step method

1. Write the equation in the form (10.20), with coefficient of $\dot x$ equal to 1, and read off $p(t)$.
2. Calculate $g(t)=e^{\int p\,\mathrm dt}$.
3. Multiply the equation by $g$ and write the left-hand side as $\frac{\mathrm d}{\mathrm dt}\big(x\,g(t)\big)$; the right-hand side is $g(t)\,r(t)$.
4. Integrate with respect to $t$, including the constant, and divide by $g$.

> [!warning] Standard form before the factor
> The factor $e^{\int p\,\mathrm dt}$ is derived for an equation whose $\dot x$ coefficient is 1. For $t\dot x+2x=t\cos t$, dividing by $t$ first gives $\dot x+\frac2tx=\cos t$, so $p=2/t$ and $g=t^2$; reading $p=2$ from the unnormalised equation gives the wrong factor $e^{2t}$. The right-hand side must be divided too.

### Solving ẋ + tx = t (Example 10.17)

Solve $\dot x+tx=t$.

The equation is already in standard form with $p(t)=t$ and $r(t)=t$:

$$
k(t)=\int t\,\mathrm dt=\tfrac12t^2,\qquad g(t)=e^{t^2/2}.
$$

Multiply through:

$$
e^{t^2/2}\,\dot x+t\,e^{t^2/2}\,x=t\,e^{t^2/2},
$$

and the left-hand side is a perfect derivative:

$$
\frac{\mathrm d}{\mathrm dt}\left(x\,e^{t^2/2}\right)=t\,e^{t^2/2}.
$$

Integrate, with $u=\tfrac12t^2$ and $\mathrm du=t\,\mathrm dt$ on the right:

$$
\begin{aligned}
x\,e^{t^2/2}&=\int e^{u}\,\mathrm du=e^{t^2/2}+C\\
x&=1+Ce^{-t^2/2}.
\end{aligned}
$$

Substituting back: $\dot x=-Cte^{-t^2/2}$ and $tx=t+Cte^{-t^2/2}$, which add to $t$. The equation is also separable, $\dot x=t(1-x)$, and gives the same answer.

![[m1054_m12_linear_family.png|900]]

Every member of the family approaches the equilibrium $x=1$ as $|t|$ grows, because the term $Ce^{-t^2/2}$ dies away. The constant $C$ only sets how far the curve strays from $x=1$ near $t=0$, where the slope segments are flattest.

### Exercises 31(c), 32(c) and 33(c)

Exercise 31(c) is $\dot x+2x=e^{-4t}$. Here $g=e^{2t}$:

$$
\begin{aligned}
\frac{\mathrm d}{\mathrm dt}\left(x\,e^{2t}\right)&=e^{2t}e^{-4t}=e^{-2t}\\
x\,e^{2t}&=-\tfrac12e^{-2t}+C\\
x&=Ce^{-2t}-\tfrac12e^{-4t}.
\end{aligned}
$$

With $x_p=-\tfrac12e^{-4t}$, $\dot x_p+2x_p=2e^{-4t}-e^{-4t}=e^{-4t}$, as required.

Exercise 32(c) is $\dot x-\dfrac xt=t^2-3$ with $x(1)=-1$, for $t>0$. Here $p=-1/t$, so $k=-\ln t$ and $g=e^{-\ln t}=1/t$:

$$
\begin{aligned}
\frac{\mathrm d}{\mathrm dt}\left(\frac xt\right)&=\frac{t^2-3}{t}=t-\frac3t\\
\frac xt&=\tfrac12t^2-3\ln t+C .
\end{aligned}
$$

At $t=1$: $-1=\tfrac12-0+C$, so $C=-\tfrac32$ and

$$
x=\tfrac12t^3-3t\ln t-\tfrac32t .
$$

Exercise 33(c) is $\dot x+\dfrac{2x}{t}=\cos t$, for $t>0$. Here $g=e^{2\ln t}=t^2$:

$$
\frac{\mathrm d}{\mathrm dt}\left(t^2x\right)=t^2\cos t .
$$

The right-hand side needs integration by parts twice:

$$
\begin{aligned}
\int t^2\cos t\,\mathrm dt&=t^2\sin t-\int2t\sin t\,\mathrm dt\\
&=t^2\sin t-\left(-2t\cos t+\int2\cos t\,\mathrm dt\right)\\
&=t^2\sin t+2t\cos t-2\sin t .
\end{aligned}
$$

So $t^2x=t^2\sin t+2t\cos t-2\sin t+C$, and dividing by $t^2$,

$$
x=\sin t+\frac{2\cos t}{t}-\frac{2\sin t}{t^2}+\frac{C}{t^2}.
$$

### Specimen Test 12, Q2, and Example 10.18

Specimen Test 12 Q2 is $\dot x+\dfrac2tx=t$ with $x=\tfrac14$ at $t=1$. Here $g=e^{\int2/t\,\mathrm dt}=t^2$:

$$
\begin{aligned}
\frac{\mathrm d}{\mathrm dt}\left(t^2x\right)&=t^3\\
t^2x&=\tfrac14t^4+C .
\end{aligned}
$$

At $t=1$: $\tfrac14=\tfrac14+C$, so $C=0$ and $x=\tfrac14t^2$.

Example 10.18, $\dot x+\dfrac1tx=t$ with $x(2)=\tfrac13$, has $g=e^{\ln t}=t$:

$$
\begin{aligned}
\frac{\mathrm d}{\mathrm dt}(tx)&=t^2\\
tx&=\tfrac13t^3+C\\
x&=\tfrac13t^2+\frac Ct .
\end{aligned}
$$

At $t=2$: $\tfrac13=\tfrac43+\tfrac C2$, so $C=-2$ and $x=\tfrac13t^2-\dfrac2t$.

### Structure of the solution

Expanding (10.22) separates the solution into two parts:

$$
x=\underbrace{Ce^{-k(t)}}_{\text{solves }\dot x+px=0}+\underbrace{e^{-k(t)}\int e^{k(t)}r(t)\,\mathrm dt}_{\text{one particular solution}} .
$$

The first term is the general solution of the unforced equation $\dot x+px=0$, equation (10.21), and the only place the arbitrary constant appears; when $k\to\infty$, as for $p$ a positive constant, it is a decaying transient. The second term is one solution of the forced equation. This is the complementary function plus particular integral split that [[MATH1054 M13 - Differential Equations III|Module 13]] uses for second-order equations, and it holds because the equation is linear ([[Linear Differential Operators and Superposition]]).

## 4. Choosing a method

Some first-order equations fall into more than one category. Test them in the order

$$
\text{separable},\quad\text{linear},\quad\frac{\mathrm dx}{\mathrm dt}=f\!\left(\frac xt\right),\quad\text{exact},
$$

and solve by the method of the first category that fits, which is usually the easiest. Apply initial conditions only after the general solution is found, and where the algebra produces $\pm$ (a square root, or a sign from $|x|$), choose the branch that matches the data, as in [[#Exercise 21(b), an initial-value problem]]. Many first-order equations fit none of the four categories and have no closed-form solution; they are solved numerically (James §10.6), which this module does not cover.

### One equation, four methods

The equation $t\,\dot x+x=0$ (with $t>0$) is in all four categories, and each method gives the same family.

Separable: $\dfrac{\dot x}{x}=-\dfrac1t$, so $\ln|x|=-\ln t+c$ and

$$
x=\frac Ct .
$$

Linear: in standard form $\dot x+\dfrac1tx=0$, so $p=1/t$, $r=0$, $g=t$, and

$$
\frac{\mathrm d}{\mathrm dt}(tx)=0\ \Rightarrow\ tx=C .
$$

Of the form $f(x/t)$: $\dot x=-x/t$, so $f(y)=-y$. With $x=ty$,

$$
\begin{aligned}
t\dot y&=f(y)-y=-2y\\
\int\frac{\mathrm dy}{y}&=-2\int\frac{\mathrm dt}{t}\\
y&=\frac{C}{t^2}\\
x&=ty=\frac Ct .
\end{aligned}
$$

Exact: $p=t$ and $q=x$, so $\partial p/\partial t=1=\partial q/\partial x$. Then $h=\int t\,\mathrm dx=tx+C_1(t)$, and $\partial h/\partial t=x+C_1'(t)=x$ forces $C_1$ to be constant, so $tx=C$. Here the left-hand side is visibly $\frac{\mathrm d}{\mathrm dt}(tx)$.

### Specimen Test 12, Q1

Classify $t\,\dot x+x=t^3$ under the headings separable, $\dot x=f(x/t)$, exact and linear.

Rewrite it as $\dot x=t^2-\dfrac xt$.

| Heading | Verdict | Reason |
|---|---|---|
| Separable | no | $t^2-x/t$ is not a product $F(t)G(x)$: the ratio of its values at two different $x$ changes with $t$ |
| $\dot x=f(x/t)$ | no | scaling $t\to\lambda t$, $x\to\lambda x$ turns $t^2$ into $\lambda^2t^2$, so the right-hand side is not a function of $x/t$ |
| Exact | yes | as $p\dot x+q=0$, $p=t$ and $q=x-t^3$, so $\partial p/\partial t=1=\partial q/\partial x$; indeed $t\dot x+x=\frac{\mathrm d}{\mathrm dt}(tx)$ |
| Linear | yes | $\dot x+\frac1tx=t^2$ |

The question asks only for the classification. Solving it as a linear equation, $(tx)'=t^3$ gives $x=\tfrac14t^3+C/t$.

## 5. Applications (James §10.2.2, §10.2.3, §10.7)

Each of the models below is a linear first-order equation with constant coefficients, so each is also separable when its input is constant, and each relaxes exponentially to an equilibrium with a time constant set by its coefficients.

### Hot-water tank

A well-mixed tank of volume $V$ at temperature $T_w$ is heated by water entering a coil at $T_{\mathrm{in}}$ with speed $U$ through a tube of cross-section $A$. The heat balance, with the coil's temperature drop modelled as $T_{\mathrm{in}}-T_{\mathrm{out}}=\alpha(T_{\mathrm{in}}-T_w)$, is

$$
V\frac{\mathrm dT_w}{\mathrm dt}+AU\alpha\,T_w=AU\alpha\,T_{\mathrm{in}} . \tag{10.6}
$$

It is linear in $T_w$, and separable when $T_{\mathrm{in}}$ is constant. It is not of the form $f(T_w/t)$, and as written it is not exact, since $\partial V/\partial t=0$ while $\partial\big(AU\alpha(T_w-T_{\mathrm{in}})\big)/\partial T_w=AU\alpha$.

Divide by $V$ and write $\tau=V/(AU\alpha)$:

$$
\dot T_w+\frac1\tau T_w=\frac{T_{\mathrm{in}}}{\tau}.
$$

With $g=e^{t/\tau}$ and constant $T_{\mathrm{in}}$:

$$
\begin{aligned}
\frac{\mathrm d}{\mathrm dt}\left(T_we^{t/\tau}\right)&=\frac{T_{\mathrm{in}}}{\tau}e^{t/\tau}\\
T_we^{t/\tau}&=T_{\mathrm{in}}e^{t/\tau}+C\\
T_w&=T_{\mathrm{in}}+Ce^{-t/\tau}.
\end{aligned}
$$

With $T_w(0)=T_0$, $C=T_0-T_{\mathrm{in}}$, so $T_w=T_{\mathrm{in}}+(T_0-T_{\mathrm{in}})e^{-t/\tau}$. Solving for the time to reach a temperature $T$:

$$
t=\tau\ln\frac{T_{\mathrm{in}}-T_0}{T_{\mathrm{in}}-T}.
$$

For a tank starting at $10\,^\circ$C with $T_{\mathrm{in}}=80\,^\circ$C (James §10.5.11, Exercise 35), the times to reach $60$, $70$ and $75\,^\circ$C are $\tau\ln\frac{70}{20}=1.253\tau$, $\tau\ln7=1.946\tau$ and $\tau\ln14=2.639\tau$, in the ratio $1:1.553:2.107$. Each further halving of the remaining temperature gap costs the same extra time, $\tau\ln2=0.693\tau$.

### Hydro-electric conduit

Water flows from a dam through a conduit of length $d$ and cross-section $A$, a generator and a control valve. The pressure drops are $Q/\alpha$ along the conduit, $\beta Q$ across the generator and $\gamma Q$ across the valve, and the excess of $\rho gh$ over them accelerates the mass $\rho Ad$ of water in the conduit. With $Q=vA$ this gives

$$
\frac{\rho d}{A}\,\frac{\mathrm dQ}{\mathrm dt}+\left(\frac1\alpha+\beta+\gamma\right)Q=\rho gh . \tag{10.7}
$$

It is linear with constant coefficients, and separable. Exactly as for the tank, its solution is

$$
Q=Q_\infty+(Q_0-Q_\infty)\,e^{-t/\tau},\qquad Q_\infty=\frac{\rho gh}{1/\alpha+\beta+\gamma},\qquad\tau=\frac{\rho d}{A\,(1/\alpha+\beta+\gamma)} .
$$

Opening the valve lowers $\gamma$, which raises the final flow $Q_\infty$ and also lengthens $\tau$, so the new flow is approached more slowly.

### RC circuit charging

A capacitor charged through a resistor from a constant source $V_0$ obeys $RC\,\dot v+v=V_0$. Divide by $RC$: $\dot v+\dfrac{1}{RC}v=\dfrac{V_0}{RC}$, so $g=e^{t/RC}$ and

$$
\begin{aligned}
\frac{\mathrm d}{\mathrm dt}\left(v\,e^{t/RC}\right)&=\frac{V_0}{RC}e^{t/RC}\\
v\,e^{t/RC}&=V_0e^{t/RC}+C\\
v&=V_0+Ce^{-t/RC}.
\end{aligned}
$$

With $v(0)=0$, $C=-V_0$ and $v=V_0\left(1-e^{-t/RC}\right)$. The circuit side is in [[RC and RL Transients]] (FEEG1004).

### Damper test rig

A carriage of mass $m$ hits a damper at speed $U$; time is measured from impact and $x$ is the compression. If the damper force is $kv$,

$$
m\dot v=-kv,\qquad v(0)=U \tag{10.27}
$$

separates to $v=Ue^{-\lambda t}$ with $\lambda=k/m$, and integrating once more with $x(0)=0$ gives $x=\dfrac U\lambda\left(1-e^{-\lambda t}\right)$. The carriage never stops in finite time and the compression only approaches $U/\lambda$, which does not match tests in which the carriage stops after a short, finite time.

Adding a constant friction force $b$ in the damper gives

$$
m\dot v=-kv-b,\qquad v(0)=U . \tag{10.30}
$$

Divide by $m$: $\dot v+\lambda v=-b/m$, so $g=e^{\lambda t}$ and

$$
\begin{aligned}
\frac{\mathrm d}{\mathrm dt}\left(v\,e^{\lambda t}\right)&=-\frac bm\,e^{\lambda t}\\
v\,e^{\lambda t}&=-\frac{b}{m\lambda}\,e^{\lambda t}+C=-\frac bk\,e^{\lambda t}+C\\
v&=Ce^{-\lambda t}-\frac bk .
\end{aligned}
$$

At $t=0$, $C=U+b/k$, so

$$
v=Ue^{-\lambda t}-\frac bk\left(1-e^{-\lambda t}\right). \tag{10.31}
$$

Integrate from 0 to $t$ with $x(0)=0$:

$$
x=\frac1\lambda\left(U+\frac bk\right)\left(1-e^{-\lambda t}\right)-\frac bk\,t . \tag{10.32}
$$

The carriage stops when $v=0$:

$$
\begin{aligned}
\left(U+\frac bk\right)e^{-\lambda t_s}&=\frac bk\\
t_s&=\frac1\lambda\ln\frac{kU+b}{b}=\frac1\lambda\ln\frac{b+\lambda Um}{b}. 
\end{aligned}\tag{10.33}
$$

At that moment $1-e^{-\lambda t_s}=\dfrac{kU}{kU+b}$ and $U+\dfrac bk=\dfrac{kU+b}{k}$, so their product is $U$ and

$$
x_s=\frac U\lambda-\frac{b}{k\lambda}\ln\frac{kU+b}{b}=\frac U\lambda-\frac{b}{m\lambda^2}\ln\frac{b+\lambda Um}{b}. \tag{10.34}
$$

For a test with $m=2$ kg, $U=1.5$ m s$^{-1}$, $k=25$ N s m$^{-1}$ and $b=1.5$ N, so $\lambda=12.5$ s$^{-1}$ and $kU/b=25$:

$$
\begin{aligned}
t_s&=\frac{\ln26}{12.5}=0.2606\ \text{s},\\
x_s&=0.12-0.0048\ln26=0.1044\ \text{m}.
\end{aligned}
$$

![[m1054_m12_damper_response.png|900]]

> [!check] Damper numbers
> Substituting (10.31) back into $m\dot v+kv+b$ gives zero, and $v(0)=U$. At $t_s=0.2606$ s the frictionless model still has $v=1.5e^{-12.5t_s}=0.0577$ m s$^{-1}$ and $x=0.1154$ m, against $U/\lambda=0.12$ m in the limit.

A damper whose damping constant $k(1+at)$ grows during the stroke obeys $m\dot v=-k(1+at)v-b$ (10.35). It is still linear, with integrating factor $e^{\lambda(t+at^2/2)}$, but $\int e^{\lambda(t+at^2/2)}\,\mathrm dt$ has no elementary form (completing the square in the exponent turns it into the imaginary error function $\operatorname{erfi}$), so the solution is computed numerically.

## Terminology and alternative names

| Course term | Also called | Note |
|---|---|---|
| equation of the form $\mathrm dx/\mathrm dt=f(x/t)$ | homogeneous equation, homogeneous-type equation | unrelated to a homogeneous linear equation (zero forcing) |
| substitution $y=x/t$, $x=ty$ | $x=vt$ | Stroud and many books use $v$ |
| $p(t,x)\,\dot x+q(t,x)=0$, solution $h(t,x)=C$ | $f\dot x+g=0$ with $F(x,t)=C$ (solutions note, formula sheet); potential function | the letters differ, the test $p_t=q_x$ is the same |
| integrating factor $g(t)$ | $\mu(t)$, IF | $g=e^{\int p\,\mathrm dt}$ |
| $\dot x+p(t)x=r(t)$ | $\dot x+P(t)x=Q(t)$ | Stroud and the formula sheet use $P$ and $Q$ |

## Links

- Parent: [[MATH1054 Mathematics for Engineering and the Environment Hub]] · Solutions: [[MATH1054 M12 Solutions - Differential Equations II]]
- Previous: [[MATH1054 M11 - Integration IV]] · Next: [[MATH1054 M13 - Differential Equations III]]
- Builds on: [[MATH1054 M06 - Differential Equations I]] (separable equations, [[Separable First-Order ODEs]], [[Classification of Differential Equations]]), [[MATH1054 M03 - Differentiation I]] (product and chain rules, [[Product, Quotient and Chain Rules]]), [[MATH1054 M04 - Integration I]] (first partial derivatives, [[Partial Derivatives]]) and [[Integration by Parts]]
- Concepts: [[Homogeneous First-Order ODEs]] · [[Exact Differential Equations]] · [[Integrating Factor Method]] · [[Linear Differential Operators and Superposition]]
- Later: [[MATH1054 M13 - Differential Equations III]] (CF + PI for second-order equations); [[MATH2048 ODE2 - Euler Equations and Inhomogeneous ODEs]]; [[MATH2048 VC3 - Line Integrals and Conservative Fields]] and [[Conservative Vector Fields]] (potentials, the vector form of exactness); [[MATH2048 PDE3 - The Heat Equation]] (first-order time equations from separation of variables)
- Engineering uses: [[RC and RL Transients]] (FEEG1004); first-order sensor lag in [[SESA2027 C2 - Sensor Characteristics, Dynamics and Design]] and [[Sensor Dynamic Models]]

## Sources

- MATH1054 Module Booklet, Module 12 work scheme and Specimen Test 12 (PDF pp. 43–47).
- James, *Modern Engineering Mathematics* (6th ed.): §10.5.5 (pp. 812–813, Example 10.14), §10.5.6 Exercises (p. 814), §10.5.7 (pp. 814–817, Examples 10.15–10.16), §10.5.8 Exercises (pp. 817–818), §10.5.9 (pp. 818–822, Examples 10.17–10.18), §10.5.11 Exercises (pp. 824–825), §10.2.2–10.2.3 (pp. 792–794) and §10.7 (pp. 834–838). Bernoulli equations (§10.5.10) are not in the Module 12 work scheme.
- Stroud (6th ed.), Programme 24, frames 27–64, covers the same material except exact equations.

## Self-study tasks

### Core

- [ ] Exercises 18(b), 20(d), 21(b) on p. 814 (Module 12 work scheme, item 2). → [[#1. Equations of the form dx/dt = f(x/t) (James §10.5.5)]] · [[MATH1054 M12 Solutions - Differential Equations II#Part B: Assigned exercises|solutions]]
- [ ] Exercises 23(e), 25(b), 24(d) on pp. 817–818 (Module 12 work scheme, item 4). → [[#2. Exact equations (James §10.5.7)]] · [[MATH1054 M12 Solutions - Differential Equations II#Part B: Assigned exercises|solutions]]
- [ ] Exercises 31(c), 33(c), 32(c) on pp. 824–825 (Module 12 work scheme, item 5). → [[#Exercises 31(c), 32(c) and 33(c)]] · [[MATH1054 M12 Solutions - Differential Equations II#Part B: Assigned exercises|solutions]]
- [ ] Solve $t\dot x+x=0$ by all four methods and check that they agree (Module 12 work scheme, item 6). → [[#One equation, four methods]]
- [ ] Specimen Test 12, Q1–Q4. → [[MATH1054 M12 Solutions - Differential Equations II#Part C: Specimen Test 12|solutions]] · [[#Specimen Test 12, Q1]]

### Further practice

- [ ] Work through Examples 10.14, 10.16 and 10.17 (Module 12 work scheme, items 2, 4 and 5). → [[MATH1054 M12 Solutions - Differential Equations II#Part A: Worked examples|solutions]] · [[#An implicit cubic solution with an initial condition (Example 10.16)]]
- [ ] Classify Equations 10.6 and 10.7 and read §10.7 on the damper (Module 12 work scheme, item 7). → [[#5. Applications (James §10.2.2, §10.2.3, §10.7)]]
- [ ] James §10.5.11 Exercise 35: the hot-water tank time ratios (suggested, not set). → [[#Hot-water tank]]
- [ ] Reproduce $t_s=0.2606$ s and $x_s=0.1044$ m for the damper with friction (suggested, not set). → [[#Damper test rig]]

## Transcript and slide slips

> [!warning] James, Example 10.16, p. 816
> Where: [[#An implicit cubic solution with an initial condition (Example 10.16)]].
>
> Imposing $x(\tfrac12\pi)=3$, the printed solution evaluates the $2t^2$ term as $2\times0^2$ and obtains $C=-27$ and $x^3-x\ln\sin t-2t^2-27=0$. At $t=\tfrac12\pi$ the term is $2(\tfrac12\pi)^2=\tfrac12\pi^2$, so $C=\tfrac12\pi^2-27\approx-22.065$ and the particular solution is $x^3-x\ln\sin t-2t^2+\tfrac12\pi^2-27=0$.
>
> On the same page, "as in Example 10.14" (an obvious $h$) and "as in Example 10.15" (two integrations compared) should read Example 10.15 and Example 10.16.

Module Booklet, Module 12 work scheme (PDF p. 44), the note on Example 10.16 (where: [[#An implicit cubic solution with an initial condition (Example 10.16)]]): $q(x,t)$ is printed as $x\cos t+4t$. The equation has $x\cot t+4t$, and only with $\cot t$ does $\partial p/\partial t=\partial q/\partial x$ hold.
