---
title: "MATH1054 Formula Sheet"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: formula
aliases: ["MATH1054 formulae"]
tags: [math1054, formula, exam-prep]
status: complete
sources: ["01 - Notes/Topics", "02 - Sources/Course Booklets & Solutions/Module Booklet.pdf", "02 - Sources/Modern Engineering Mathematics.pdf", "02 - Sources/Formulae & Reference"]
---

# MATH1054 Formula Sheet

Results by block and module, in the order of the hub's topic map. Each section links to its topic note, which has the derivations and worked examples. The longer tables of volumes, centroids and trigonometric identities are in [[Integration Formulae]] and [[Useful Trigonometry Identities and stuff]].

Conventions throughout: angles in radians; $\mathrm j^2=-1$; the principal argument lies in $-\pi<\theta\le\pi$; in the ODE modules $x(t)$ is the unknown and $t$ the independent variable (the Data Book uses $y(x)$); every indefinite integral carries $+C$.

## Block 1: Calculus

### Differentiation I ([[MATH1054 M03 - Differentiation I|M03]])

$$
f'(x)=\lim_{\Delta x\to0}\frac{f(x+\Delta x)-f(x)}{\Delta x}
$$

$$
(uv)'=u'v+uv',\qquad\Big(\frac uv\Big)'=\frac{u'v-uv'}{v^2},\qquad\frac{\mathrm dy}{\mathrm dx}=\frac{\mathrm dy}{\mathrm du}\,\frac{\mathrm du}{\mathrm dx},\qquad\frac{\mathrm dy}{\mathrm dx}=\frac1{\mathrm dx/\mathrm dy}
$$

| $f(x)$ | $f'(x)$ | $f(x)$ | $f'(x)$ | $f(x)$ | $f'(x)$ |
|---|---|---|---|---|---|
| $x^r$ ($r\in\mathbb R$) | $rx^{r-1}$ | $\sin x$ | $\cos x$ | $\sin^{-1}x$ | $\dfrac1{\sqrt{1-x^2}}$ |
| $e^{ax}$ | $ae^{ax}$ | $\cos x$ | $-\sin x$ | $\cos^{-1}x$ | $-\dfrac1{\sqrt{1-x^2}}$ |
| $\ln x$ ($x>0$) | $\dfrac1x$ | $\tan x$ | $\sec^2x$ | $\tan^{-1}x$ | $\dfrac1{1+x^2}$ |
| $a^x$ ($a>0$) | $a^x\ln a$ | $\sec x$ | $\sec x\tan x$ | $\operatorname{cosec}x$ | $-\operatorname{cosec}x\cot x$ |
| | | $\cot x$ | $-\operatorname{cosec}^2x$ | | |

- Chain-rule forms: $(u^n)'=nu^{n-1}u'$, $(e^u)'=u'e^u$, $(\ln u)'=u'/u$, $(\sin u)'=u'\cos u$, $(\cos u)'=-u'\sin u$.
- Tangent at $(x_1,y_1)$: $y-y_1=m(x-x_1)$ with $m=f'(x_1)$; the normal has slope $-1/m$.
- Newton–Raphson for $f(x)=0$ (write $g(x)=C$ as $g(x)-C=0$ first; needs $f'(x_n)\neq0$):

$$
x_{n+1}=x_n-\frac{f(x_n)}{f'(x_n)},\qquad e_{n+1}\approx\frac{f''(a)}{2f'(a)}\,e_n^2\quad\text{near a simple root }a
$$

- Partial derivatives, the other variable held constant: $\dfrac{\partial f}{\partial x}=\lim\limits_{\Delta x\to0}\dfrac{f(x+\Delta x,y)-f(x,y)}{\Delta x}$, and likewise in $y$. For $f(u)$ with $u(x,y)$: $\dfrac{\partial f}{\partial x}=\dfrac{\mathrm df}{\mathrm du}\dfrac{\partial u}{\partial x}$. Mixed partials agree, $f_{xy}=f_{yx}$, when the second partials are continuous.

### Integration I ([[MATH1054 M04 - Integration I|M04]])

$$
\int_a^bf(x)\,\mathrm dx=F(b)-F(a)\quad(F'=f,\ f\text{ continuous on }[a,b]),\qquad\int f(ax+b)\,\mathrm dx=\frac1aF(ax+b)
$$

| $f(x)$ | $\int f\,\mathrm dx$ | $f(x)$ | $\int f\,\mathrm dx$ |
|---|---|---|---|
| $x^n$ ($n\neq-1$) | $\dfrac{x^{n+1}}{n+1}$ | $\sec^2x$ | $\tan x$ |
| $\dfrac1x$ (range avoids $0$) | $\ln\lvert x\rvert$ | $\dfrac1{a^2+x^2}$ | $\dfrac1a\tan^{-1}\dfrac xa$ |
| $e^{ax}$ | $\dfrac1ae^{ax}$ | $\dfrac1{\sqrt{a^2-x^2}}$ ($\lvert x\rvert<a$) | $\sin^{-1}\dfrac xa$ |
| $\sin ax$ | $-\dfrac1a\cos ax$ | $\dfrac1{\sqrt{x^2+a^2}}$ | $\sinh^{-1}\dfrac xa$ |
| $\cos ax$ | $\dfrac1a\sin ax$ | $\dfrac1{\sqrt{x^2-a^2}}$ ($x>a$) | $\cosh^{-1}\dfrac xa$ |

- Product to sum and power reduction (each halves the power and doubles the angle):

$$
2\sin A\cos B=\sin(A+B)+\sin(A-B),\qquad2\cos A\cos B=\cos(A+B)+\cos(A-B),\qquad2\sin A\sin B=\cos(A-B)-\cos(A+B)
$$

$$
\cos^2A=\tfrac12(1+\cos2A),\qquad\sin^2A=\tfrac12(1-\cos2A)
$$

- An odd power of $\sin$ or $\cos$: keep one factor and convert the rest with $\sin^2x+\cos^2x=1$, then substitute $u=\cos x$ or $u=\sin x$.
- Integration by parts, $u$ the factor that simplifies on differentiation (LIATE); for $e^{ax}\sin bx$ apply it twice and solve for the integral:

$$
\int uv'\,\mathrm dx=uv-\int u'v\,\mathrm dx
$$

$$
\int e^{ax}\cos bx\,\mathrm dx=\frac{e^{ax}(a\cos bx+b\sin bx)}{a^2+b^2},\qquad\int e^{ax}\sin bx\,\mathrm dx=\frac{e^{ax}(a\sin bx-b\cos bx)}{a^2+b^2}
$$

- Numerical integration ([[Trapezium and Simpson's Rules]]): $n$ strips of width $h=\frac{b-a}n$, ordinates $f_r=f(a+rh)$.

$$
T(h)=h\Big[\tfrac12(f_0+f_n)+\sum_{r=1}^{n-1}f_r\Big],\qquad T(h)-I\approx\frac{h^2}{12}\big[f'(b)-f'(a)\big]
$$

$$
S=\frac h3\Big[f_0+f_n+4(f_1+f_3+\dots+f_{n-1})+2(f_2+f_4+\dots+f_{n-2})\Big]\ \ (n\text{ even}),\qquad S-I\approx\frac{h^4}{180}\big[f'''(b)-f'''(a)\big]
$$

- Halving $h$ divides the errors by about 4 (trapezium) and 16 (Simpson). Error estimate and Richardson extrapolation: $T(h)-I\approx\frac13\big[T(2h)-T(h)\big]$ and $\frac13\big[4T(h)-T(2h)\big]=S$. Repeating on these extrapolated values $R(h)$, whose error is of order $h^4$, gives $\frac1{15}\big[16R(h)-R(2h)\big]$.

### Functions ([[MATH1054 M07 - Functions|M07]])

- A function is a rule with a domain; $f^{-1}$ exists only if $f$ is one-to-one. To invert, solve $y=f(x)$ for $x$ and swap letters; the domain of $f^{-1}$ is the range of $f$, and the graph is the reflection in $y=x$.
- Even $f(-x)=f(x)$, odd $f(-x)=-f(x)$; even × even and odd × odd are even, even × odd is odd. Any $f$ on a symmetric domain is $\tfrac12[f(x)+f(-x)]+\tfrac12[f(x)-f(-x)]$ (even + odd).

$$
\int_{-a}^af\,\mathrm dx=0\ \ (f\text{ odd}),\qquad\int_{-a}^af\,\mathrm dx=2\int_0^af\,\mathrm dx\ \ (f\text{ even})
$$

- Periodic: $f(x+P)=f(x)$; frequency $\nu=1/P$, circular frequency $\omega=2\pi/P$; $\sin\omega x$ has period $2\pi/\omega$.
- Principal ranges: $\sin^{-1}x\in[-\frac\pi2,\frac\pi2]$, $\cos^{-1}x\in[0,\pi]$, $\tan^{-1}x\in(-\frac\pi2,\frac\pi2)$; $\sin^{-1}(\sin x)=x$ only for $x\in[-\frac\pi2,\frac\pi2]$. Also $\sin^{-1}x+\cos^{-1}x=\frac\pi2$ for $-1\le x\le1$.
- Logarithms, where every log is defined: $\log_a(xy)=\log_ax+\log_ay$, $\log_a\frac xy=\log_ax-\log_ay$, $\log_ax^n=n\log_ax$, $\log_ax=\dfrac{\log_bx}{\log_ba}$, $a^x=e^{x\ln a}$.
- Hyperbolic functions:

$$
\cosh x=\frac{e^x+e^{-x}}2,\quad\sinh x=\frac{e^x-e^{-x}}2,\quad\tanh x=\frac{\sinh x}{\cosh x},\quad\operatorname{sech}x=\frac1{\cosh x},\quad\operatorname{cosech}x=\frac1{\sinh x},\quad\coth x=\frac{\cosh x}{\sinh x}
$$

$$
\cosh^2x-\sinh^2x=1,\qquad1-\tanh^2x=\operatorname{sech}^2x,\qquad\coth^2x-1=\operatorname{cosech}^2x
$$

$$
\sinh(x\pm y)=\sinh x\cosh y\pm\cosh x\sinh y,\qquad\cosh(x\pm y)=\cosh x\cosh y\pm\sinh x\sinh y
$$

$$
\sinh2x=2\sinh x\cosh x,\qquad\cosh2x=\cosh^2x+\sinh^2x=1+2\sinh^2x=2\cosh^2x-1
$$

- $\cosh x\ge1$; $\cosh$ is even, $\sinh$ and $\tanh$ odd. Osborn's rule: a trigonometric identity becomes hyperbolic by changing the sign of every product (or implied product, as in $\tan^2$) of two sines. Link: $\cos\mathrm jx=\cosh x$, $\sin\mathrm jx=\mathrm j\sinh x$.
- A hyperbolic equation: substitute the exponentials, solve the quadratic in $e^x$, reject $e^x\le0$.
- Inverse hyperbolic functions:

$$
\sinh^{-1}x=\ln\big(x+\sqrt{x^2+1}\big),\qquad\cosh^{-1}x=\ln\big(x+\sqrt{x^2-1}\big)\ (x\ge1),\qquad\tanh^{-1}x=\tfrac12\ln\frac{1+x}{1-x}\ (\lvert x\rvert<1)
$$

| $f$ | $f'$ | $f$ | $f'$ |
|---|---|---|---|
| $\sinh x$ | $\cosh x$ | $\operatorname{sech}x$ | $-\operatorname{sech}x\tanh x$ |
| $\cosh x$ | $\sinh x$ | $\operatorname{cosech}x$ | $-\operatorname{cosech}x\coth x$ |
| $\tanh x$ | $\operatorname{sech}^2x$ | $\coth x$ | $-\operatorname{cosech}^2x$ |
| $\sinh^{-1}x$ | $\dfrac1{\sqrt{1+x^2}}$ | $\cosh^{-1}x$ ($x>1$) | $\dfrac1{\sqrt{x^2-1}}$ |
| $\tanh^{-1}x$ ($\lvert x\rvert<1$) | $\dfrac1{1-x^2}$ | | |

### Differentiation II ([[MATH1054 M08 - Differentiation II|M08]])

- Stationary points: $f'(a)=0$. $f''(a)<0$ gives a maximum, $f''(a)>0$ a minimum; if $f''(a)=0$, use the sign of $f'$ either side. An inflection is where $f''$ changes sign ($f''=0$ alone is not enough: $x^4$ has a minimum at $0$).
- Curve sketch (each step earns marks): symmetry or periodicity; stationary points and their nature; asymptotes and the behaviour either side; $f(x)$ as $x\to\pm\infty$; intercepts with the axes (factor theorem: $f(a)=0\Rightarrow(x-a)$ is a factor).
- Asymptotes of $y=p/q$: vertical at zeros of $q$ that are not zeros of $p$; dividing, $p=sq+r$ with $\deg r<\deg q$, the curve approaches $y=s(x)$ (horizontal if $s$ is constant, oblique if linear).
- Parametric ($\dot x\neq0$) and implicit ($F_y\neq0$):

$$
\frac{\mathrm dy}{\mathrm dx}=\frac{\dot y}{\dot x},\qquad\frac{\mathrm d^2y}{\mathrm dx^2}=\frac{\frac{\mathrm d}{\mathrm dt}\big(\frac{\mathrm dy}{\mathrm dx}\big)}{\dot x}=\frac{\dot x\ddot y-\dot y\ddot x}{\dot x^3}\ \ \Big(\text{not }\frac{\ddot y}{\ddot x}\Big),\qquad\frac{\mathrm dy}{\mathrm dx}=-\frac{F_x}{F_y}
$$

- Implicitly, differentiate every term with $y=y(x)$: $\frac{\mathrm d}{\mathrm dx}g(y)=g'(y)\,y'$, $\frac{\mathrm d}{\mathrm dx}(xy)=y+xy'$; for $y''$ differentiate again and substitute $y'$.
- Logarithmic differentiation ($y>0$, or use $\ln\lvert y\rvert$): $y'=y\,\frac{\mathrm d}{\mathrm dx}\ln y$. For $y=u^v$, $\dfrac{y'}y=v'\ln u+v\dfrac{u'}u$; for $y=\prod u_k^{a_k}$, $\dfrac{y'}y=\sum a_k\dfrac{u_k'}{u_k}$.
- Inverse function: $\dfrac{\mathrm d^2x}{\mathrm dy^2}=-\dfrac{y''}{(y')^3}$.
- Taylor and Maclaurin series ($a=0$), valid only where the remainder tends to zero:

$$
f(x)=\sum_{n=0}^\infty\frac{f^{(n)}(a)}{n!}(x-a)^n,\qquad f(a+x)=\sum_{k=0}^{n}\frac{x^k}{k!}f^{(k)}(a)+\frac{x^{n+1}}{(n+1)!}f^{(n+1)}(a+\theta x),\ \ 0<\theta<1
$$

| Series | Valid for |
|---|---|
| $\dfrac1{1-x}=1+x+x^2+\cdots$, $\dfrac1{1+x}=1-x+x^2-\cdots$ | $-1<x<1$ |
| $(1+x)^r=1+rx+\dfrac{r(r-1)}{2!}x^2+\dfrac{r(r-1)(r-2)}{3!}x^3+\cdots$ | $-1<x<1$ (all $x$ if $r\in\mathbb N$) |
| $e^x=1+x+\dfrac{x^2}{2!}+\dfrac{x^3}{3!}+\cdots$ | all $x$ |
| $\sin x=x-\dfrac{x^3}{3!}+\dfrac{x^5}{5!}-\cdots$, $\cos x=1-\dfrac{x^2}{2!}+\dfrac{x^4}{4!}-\cdots$ | all $x$ (radians) |
| $\sinh x=x+\dfrac{x^3}{3!}+\dfrac{x^5}{5!}+\cdots$, $\cosh x=1+\dfrac{x^2}{2!}+\dfrac{x^4}{4!}+\cdots$ | all $x$ |
| $\ln(1+x)=x-\dfrac{x^2}2+\dfrac{x^3}3-\cdots$ | $-1<x\le1$ |
| $\ln(1-x)=-x-\dfrac{x^2}2-\dfrac{x^3}3-\cdots$ | $-1\le x<1$ |
| $\tan x=x+\dfrac{x^3}3+\dfrac{2x^5}{15}+\cdots$ | $-\frac\pi2<x<\frac\pi2$ |

Known series may be added, multiplied and substituted within their common interval.

### Integration II ([[MATH1054 M09 - Integration II|M09]])

$$
\int f\big(g(x)\big)g'(x)\,\mathrm dx=\int f(u)\,\mathrm du\ \ (u=g(x)),\qquad\int_a^b\to\int_{g(a)}^{g(b)}
$$

$$
\int f'(x)\big[f(x)\big]^n\,\mathrm dx=\frac{[f(x)]^{n+1}}{n+1}\ (n\neq-1),\qquad\int\frac{f'(x)}{f(x)}\,\mathrm dx=\ln\lvert f(x)\rvert
$$

| Integrand contains | Substitute | Then | Range |
|---|---|---|---|
| $\sqrt{a^2-x^2}$ | $x=a\sin\theta$ | $\sqrt{a^2-x^2}=a\cos\theta$ | $-\frac\pi2\le\theta\le\frac\pi2$ |
| $\sqrt{a^2+x^2}$ or $a^2+x^2$ | $x=a\sinh u$ or $x=a\tan\theta$ | $a\cosh u$; $a^2\sec^2\theta$ | all $u$; $-\frac\pi2<\theta<\frac\pi2$ |
| $\sqrt{x^2-a^2}$ | $x=a\cosh u$ | $\sqrt{x^2-a^2}=a\sinh u$ | $u\ge0$ ($x\ge a$) |

For the region under $y=f(x)\ge0$ on $[a,b]$, rotated about the $x$-axis where a solid is meant (uniform density for a centre of gravity):

| Quantity | Formula |
|---|---|
| Area | $A=\int_a^by\,\mathrm dx$ |
| Centroid of the area | $\bar x=\dfrac1A\int_a^bxy\,\mathrm dx$, $\bar y=\dfrac1{2A}\int_a^by^2\,\mathrm dx$ |
| Volume of revolution (discs) | $V=\pi\int_a^by^2\,\mathrm dx$ |
| Centre of gravity of the solid | $\bar X=\dfrac\pi V\int_a^bxy^2\,\mathrm dx$, $\bar Y=\bar Z=0$ |
| Mean value | $\bar f=\dfrac1{b-a}\int_a^bf\,\mathrm dx$ |
| RMS value | $f_{\text{rms}}=\sqrt{\dfrac1{b-a}\int_a^bf^2\,\mathrm dx}$; $I\sin\theta$ has $I/\sqrt2$ over whole half-cycles |
| Arc length | $s=\int_a^b\sqrt{1+y'^2}\,\mathrm dx$ |
| Surface of revolution | $S=2\pi\int_a^by\sqrt{1+y'^2}\,\mathrm dx$ |

Between $y_l\le y\le y_u$: strip height $y_u-y_l$, moment about the $x$-axis $\frac12(y_u^2-y_l^2)$, washer $\pi(y_u^2-y_l^2)$. The solid's $\bar X$ is not the area's $\bar x$.

### Integration III ([[MATH1054 M10 - Integration III|M10]])

- If $\deg P\ge\deg Q$, divide first. Partial-fraction terms for each factor of $Q$ (real coefficients):

| Factor of $Q$ | Terms | Integral of each term |
|---|---|---|
| $(x-a)$ | $\dfrac A{x-a}$ (cover-up) | $A\ln\lvert x-a\rvert$ |
| $(x-a)^n$ | $\dfrac{A_1}{x-a}+\dots+\dfrac{A_n}{(x-a)^n}$ | $\displaystyle\int\frac{\mathrm dx}{(x-a)^n}=-\frac1{(n-1)(x-a)^{n-1}}$ ($n\ge2$) |
| $x^2+bx+c$, $b^2<4c$ | $\dfrac{Bx+C}{x^2+bx+c}$ | below |

$$
\int\frac{Bx+C}{x^2+bx+c}\,\mathrm dx=\frac B2\ln(x^2+bx+c)+\frac{C-\frac{Bb}2}{k}\tan^{-1}\frac{x+\frac b2}{k},\qquad k^2=c-\frac{b^2}4>0
$$

- Completing the square: $ax^2+bx+c=a\Big[\big(x+\frac b{2a}\big)^2+\frac{4ac-b^2}{4a^2}\Big]$. With $u=x+\frac b{2a}$ and $k>0$:

| Form | Integral | Form | Integral |
|---|---|---|---|
| $\dfrac1{u^2+k^2}$ | $\dfrac1k\tan^{-1}\dfrac uk$ | $\dfrac1{\sqrt{k^2-u^2}}$ | $\sin^{-1}\dfrac uk$ |
| $\dfrac1{u^2-k^2}$ | $\dfrac1{2k}\ln\Big\lvert\dfrac{u-k}{u+k}\Big\rvert$ | $\dfrac1{\sqrt{u^2+k^2}}$ | $\sinh^{-1}\dfrac uk=\ln\big(u+\sqrt{u^2+k^2}\big)$ |
| | | $\dfrac1{\sqrt{u^2-k^2}}$ ($u>k$) | $\cosh^{-1}\dfrac uk$ |

- Improper integrals are limits: $\int_a^\infty f=\lim\limits_{R\to\infty}\int_a^Rf$; at a singular end $\int_0^bf=\lim\limits_{\varepsilon\to0^+}\int_\varepsilon^bf$; split the range at every interior singularity ($\int_{-1}^1x^{-2}\,\mathrm dx$ diverges, it is not $-2$).

| Integral | Converges iff | Value |
|---|---|---|
| $\displaystyle\int_1^\infty\frac{\mathrm dx}{x^p}$ | $p>1$ | $\dfrac1{p-1}$ |
| $\displaystyle\int_0^1\frac{\mathrm dx}{x^p}$ | $p<1$ | $\dfrac1{1-p}$ |

- Standard limits: $\varepsilon\ln\varepsilon\to0$ ($\varepsilon\to0^+$), $R^ne^{-R}\to0$ ($R\to\infty$), $\tan^{-1}R\to\frac\pi2$.

### Integration IV ([[MATH1054 M11 - Integration IV|M11]])

- Sketch $R$ first. Inner limits may depend on the outer variable; outer limits are constants. Reversing the order means re-describing $R$, not swapping the limits.

$$
\iint_Rf\,\mathrm dS=\int_{x_1}^{x_2}\!\!\int_{y=g_1(x)}^{g_2(x)}f\,\mathrm dy\,\mathrm dx=\int_{y_1}^{y_2}\!\!\int_{x=h_1(y)}^{h_2(y)}f\,\mathrm dx\,\mathrm dy
$$

- Polar ($r\ge0$, $\theta$ in radians): $x=r\cos\theta$, $y=r\sin\theta$, $\mathrm dS=r\,\mathrm dr\,\mathrm d\theta$. Area inside $r=f(\theta)$, $\alpha\le\theta\le\beta$: $A=\frac12\int_\alpha^\beta f(\theta)^2\,\mathrm d\theta$.
- Triple integral: $\iiint_Vf\,\mathrm dV$, $\mathrm dV=\mathrm dx\,\mathrm dy\,\mathrm dz$, limits found slice by slice from the outside in.
- Lamina of density $\rho(x,y)$ (per unit area); solids likewise with $\mathrm dV$:

$$
A=\iint_R\mathrm dS,\quad V=\iint_Rf\,\mathrm dS,\quad M=\iint_R\rho\,\mathrm dS,\quad\bar x=\frac1M\iint_Rx\rho\,\mathrm dS,\quad\bar y=\frac1M\iint_Ry\rho\,\mathrm dS
$$

$$
I_x=\iint_Ry^2\rho\,\mathrm dS,\qquad I_y=\iint_Rx^2\rho\,\mathrm dS,\qquad I_0=\iint_R(x^2+y^2)\rho\,\mathrm dS=I_x+I_y,\qquad I_z=\iiint(x^2+y^2)\rho\,\mathrm dV
$$

## Block 2: Complex numbers

### Complex Numbers I ([[MATH1054 M05 - Complex Numbers I|M05]])

$$
z=x+\mathrm jy=r(\cos\theta+\mathrm j\sin\theta)=re^{\mathrm j\theta},\qquad r=\lvert z\rvert=\sqrt{x^2+y^2},\qquad x=r\cos\theta,\ y=r\sin\theta
$$

$$
z^*=x-\mathrm jy,\qquad zz^*=\lvert z\rvert^2,\qquad\frac{z_1}{z_2}=\frac{z_1z_2^*}{\lvert z_2\rvert^2}
$$

- Equal complex numbers have equal real parts and equal imaginary parts.
- Argument from $\alpha=\tan^{-1}\lvert y/x\rvert$ and the quadrant (sketch first; a calculator's $\tan^{-1}(y/x)$ is right only in quadrants 1 and 4):

| Quadrant | 1 $(+,+)$ | 2 $(-,+)$ | 3 $(-,-)$ | 4 $(+,-)$ |
|---|---|---|---|---|
| $\operatorname{Arg}z$ | $\alpha$ | $\pi-\alpha$ | $-(\pi-\alpha)$ | $-\alpha$ |

- Products and quotients: $\lvert z_1z_2\rvert=\lvert z_1\rvert\lvert z_2\rvert$, $\arg(z_1z_2)=\arg z_1+\arg z_2$; $\lvert z_1/z_2\rvert=\lvert z_1\rvert/\lvert z_2\rvert$, $\arg(z_1/z_2)=\arg z_1-\arg z_2$; then bring the argument back into $(-\pi,\pi]$ by $\pm2\pi$. Multiplying by $\mathrm j$ rotates by $+\frac\pi2$.
- Euler's formula and its consequences:

$$
e^{\mathrm j\theta}=\cos\theta+\mathrm j\sin\theta,\qquad\cos\theta=\frac{e^{\mathrm j\theta}+e^{-\mathrm j\theta}}2,\qquad\sin\theta=\frac{e^{\mathrm j\theta}-e^{-\mathrm j\theta}}{2\mathrm j}
$$

- Roots of $ax^2+bx+c=0$ are complex when $b^2<4ac$; a polynomial of degree $n$ has $n$ roots counted with multiplicity, and with real coefficients its non-real roots come in conjugate pairs.

### Complex Numbers II ([[MATH1054 M22 - Complex Numbers II|M22]])

With $z=x+\mathrm jy$:

$$
\cos\mathrm jy=\cosh y,\qquad\sin\mathrm jy=\mathrm j\sinh y,\qquad\cosh\mathrm jy=\cos y,\qquad\sinh\mathrm jy=\mathrm j\sin y
$$

$$
\begin{aligned}
\sin z&=\sin x\cosh y+\mathrm j\cos x\sinh y, & \cos z&=\cos x\cosh y-\mathrm j\sin x\sinh y,\\
\sinh z&=\sinh x\cos y+\mathrm j\cosh x\sin y, & \cosh z&=\cosh x\cos y+\mathrm j\sinh x\sin y,
\end{aligned}
$$

$$
\lvert\sin z\rvert^2=\sin^2x+\sinh^2y,\qquad\lvert\cos z\rvert^2=\cos^2x+\sinh^2y,\qquad\tan z=\frac{\sin2x+\mathrm j\sinh2y}{\cos2x+\cosh2y}
$$

- $\sin z$ and $\cos z$ are unbounded; solve $f(z)=c$ by equating real and imaginary parts.
- Logarithm (infinitely many values; $k=0$ gives the principal value):

$$
\ln z=\ln\lvert z\rvert+\mathrm j(\operatorname{Arg}z+2k\pi),\qquad k=0,\pm1,\pm2,\dots
$$

- De Moivre and $n$th roots ($n$ distinct roots on the circle of radius $r^{1/n}$, spaced $\frac{2\pi}n$, summing to zero for $n\ge2$):

$$
(re^{\mathrm j\theta})^n=r^ne^{\mathrm jn\theta},\qquad z^{1/n}=r^{1/n}e^{\mathrm j(\theta+2k\pi)/n},\quad k=0,1,\dots,n-1
$$

- A rational power $z^{m/n}=(z^{1/n})^m$ ($m/n$ in lowest terms) has $n$ values, $k=0,1,\dots,n-1$.
- For $z=\cos\theta+\mathrm j\sin\theta$ and any integer $n$: $z^n+z^{-n}=2\cos n\theta$, $z^n-z^{-n}=2\mathrm j\sin n\theta$ (powers of $\cos\theta$ to multiple angles, e.g. $\cos^3\theta=\frac14(\cos3\theta+3\cos\theta)$).
- Quadratic with complex coefficients: the formula still holds; find $\sqrt{c+\mathrm jd}=a+\mathrm jb$ from $a^2-b^2=c$, $2ab=d$.
- Loci (substitute $z=x+\mathrm jy$, square moduli, remove excluded points):

| Condition | Locus |
|---|---|
| $\lvert z-z_0\rvert=r$ | circle, centre $z_0$, radius $r$ |
| $\lvert z-a\rvert=\lvert z-b\rvert$ | perpendicular bisector of $a$ and $b$ |
| $\lvert z-a\rvert=k\lvert z-b\rvert$, $k>0$, $k\neq1$ | circle of Apollonius, centre $\dfrac{a-k^2b}{1-k^2}$, radius $\dfrac{k\lvert a-b\rvert}{\lvert1-k^2\rvert}$ |
| $\arg(z-z_0)=\alpha$ | half-line from $z_0$ at angle $\alpha$, excluding $z_0$ |
| $\operatorname{Re}\frac{z-a}{z-b}=0$ | circle on diameter $ab$, minus $b$ |
| $\operatorname{Im}\frac{z-a}{z-b}=0$ | line through $a$ and $b$, minus $b$ |

## Block 3: Differential equations

### Differential Equations I ([[MATH1054 M06 - Differential Equations I|M06]])

- Classify by order, linear or nonlinear ($x$ and its derivatives appear only to the first power, multiplied by functions of $t$), homogeneous ($f(t)=0$) or inhomogeneous. An $n$th-order ODE has $n$ arbitrary constants; each independent initial or boundary condition fixes one.
- Direct integration: $x^{(n)}=f(t)$, integrate $n$ times.
- Separable $\dot x=f(t)g(x)$, for $g(x)\neq0$; each root $x_0$ of $g$ is a separate solution $x\equiv x_0$:

$$
\int\frac{\mathrm dx}{g(x)}=\int f(t)\,\mathrm dt+C
$$

- One solution through $(t_0,x_0)$ is guaranteed when the right-hand side and its $x$-derivative are continuous there; otherwise there may be two (or the solution may blow up in finite time).
- $a\ddot x+b\dot x+cx=0$ ($a\neq0$): try $x=e^{mt}$, auxiliary equation $am^2+bm+c=0$:

| $b^2-4ac$ | Roots | General solution |
|---|---|---|
| $>0$ | $m_1\neq m_2$ real | $x=Ae^{m_1t}+Be^{m_2t}$ |
| $=0$ | $m=k$ repeated | $x=(A+Bt)e^{kt}$ |
| $<0$ | $\alpha\pm\mathrm j\beta$ | $x=e^{\alpha t}(A\cos\beta t+B\sin\beta t)$ |

### Differential Equations II ([[MATH1054 M12 - Differential Equations II|M12]])

Test first-order equations in the order separable, linear, $\dot x=f(x/t)$, exact; apply initial conditions last and pick the branch that fits them.

- $\dot x=f(x/t)$, which holds when $F(\lambda t,\lambda x)=F(t,x)$ (every term of the same total degree). Put $x=ty$, so $\dot x=t\dot y+y$ ($t>0$); each $y_0$ with $f(y_0)=y_0$ gives a lost solution $x=y_0t$:

$$
t\dot y=f(y)-y,\qquad\int\frac{\mathrm dy}{f(y)-y}=\ln t+C,\qquad y=\frac xt
$$

- Exact: $p(t,x)\,\dot x+q(t,x)=0$ is exact iff $\dfrac{\partial p}{\partial t}=\dfrac{\partial q}{\partial x}$. Then $h(t,x)=C$ with $h_x=p$, $h_t=q$: integrate $p$ in $x$ adding $C_1(t)$, then match $h_t=q$ (every $x$ must cancel).
- Linear $\dot x+p(t)x=r(t)$, after dividing by the coefficient of $\dot x$:

$$
g(t)=e^{\int p\,\mathrm dt},\qquad\frac{\mathrm d}{\mathrm dt}(gx)=gr,\qquad x=\frac1g\Big[\int g\,r\,\mathrm dt+C\Big]
$$

The term $C/g$ solves $\dot x+px=0$ (complementary function); the rest is one particular solution.

### Differential Equations III ([[MATH1054 M13 - Differential Equations III|M13]])

- $\mathrm L$ is linear if $\mathrm L[ax_1+bx_2]=a\mathrm L[x_1]+b\mathrm L[x_2]$. The general solution of $\mathrm L[x]=f$ is CF (general solution of $\mathrm L[x]=0$) + PI (any one solution); for $f=f_1+f_2$ add the PIs. Apply conditions to the full CF + PI.
- Constant coefficients, any order: $x=e^{mt}$ gives $P(m)=0$.

| Root of $P(m)$ | Contribution to the CF |
|---|---|
| real $m$, simple | $Ae^{mt}$ |
| real $m$, multiplicity $k$ | $(A_0+A_1t+\dots+A_{k-1}t^{k-1})e^{mt}$ |
| $\alpha\pm\mathrm j\beta$ | $e^{\alpha t}(A\cos\beta t+B\sin\beta t)$ |
| $\alpha\pm\mathrm j\beta$, multiplicity $k$ | $e^{\alpha t}\big[(A_0+\dots+A_{k-1}t^{k-1})\cos\beta t+(B_0+\dots+B_{k-1}t^{k-1})\sin\beta t\big]$ |

| Forcing $f(t)$ | Trial PI |
|---|---|
| polynomial of degree $n$ | full polynomial of degree $n$ |
| $e^{kt}$ | $Ce^{kt}$, $C=1/P(k)$ if $P(k)\neq0$ |
| $\cos\omega t$ or $\sin\omega t$ | $a\cos\omega t+b\sin\omega t$ (both terms) |
| a sum | the sum of the trials |
| trial already in the CF | trial $\times\,t^s$, $s$ = multiplicity of the root |

- Clash shortcuts for $e^{kt}$ forcing: $x_p=\dfrac{te^{kt}}{P'(k)}$ (simple root), $x_p=\dfrac{t^se^{kt}}{P^{(s)}(k)}$ (root of multiplicity $s$). Undamped resonance: $\ddot x+\omega^2x=F\cos\omega t$ gives $x_p=\dfrac{Ft\sin\omega t}{2\omega}$; $F\sin\omega t$ gives $x_p=-\dfrac{Ft\cos\omega t}{2\omega}$.
- Standard form (divide by the coefficient of $\ddot x$ first), natural frequency $\omega$ and damping parameter $\zeta$:

$$
\ddot x+2\zeta\omega\dot x+\omega^2x=0,\qquad m=-\zeta\omega\pm\omega\sqrt{\zeta^2-1}
$$

| $\zeta$ | Regime | Solution |
|---|---|---|
| $\zeta>1$ | over-damped | $Ae^{-(\zeta-\sqrt{\zeta^2-1})\omega t}+Be^{-(\zeta+\sqrt{\zeta^2-1})\omega t}$ |
| $\zeta=1$ | critically damped | $(A+Bt)e^{-\omega t}$ |
| $0<\zeta<1$ | under-damped | $e^{-\zeta\omega t}(A\cos\omega_dt+B\sin\omega_dt)$, $\omega_d=\omega\sqrt{1-\zeta^2}$ |

- Decay time $T=1/(\zeta\omega)$: about 5% left after $3T$, 1% after $4.5T$. Step-response overshoots: $\exp\big(-n\pi\zeta/\sqrt{1-\zeta^2}\big)$ for the $n$th.
- Forced, $\ddot x+2\zeta\omega\dot x+\omega^2x=F\cos\Omega t$ with $\zeta>0$: the CF is the transient and the PI the steady state, at the forcing frequency $\Omega$:

$$
x_p=F\,A(\Omega)\cos(\Omega t-\delta),\qquad A(\Omega)=\frac1{\sqrt{(\omega^2-\Omega^2)^2+4\zeta^2\omega^2\Omega^2}},\qquad\tan\delta=\frac{2\zeta\omega\Omega}{\omega^2-\Omega^2},\ 0\le\delta\le\pi
$$

- Resonance peak for $\zeta<1/\sqrt2$ at $\Omega_r=\omega\sqrt{1-2\zeta^2}$, with $\dfrac{A_{\max}}{A(0)}=\dfrac1{2\zeta\sqrt{1-\zeta^2}}$ and $A(0)=1/\omega^2$; $\delta=90^\circ$ at $\Omega=\omega$.

## Block 4: Vectors and matrices

### Vectors I ([[MATH1054 M14 - Vectors I|M14]])

Right-handed axes, $\mathbf i\times\mathbf j=\mathbf k$; $\theta\in[0,\pi]$ is the angle between two vectors.

- $\lvert\mathbf a\rvert=\sqrt{a_1^2+a_2^2+a_3^2}$, $\hat{\mathbf a}=\mathbf a/\lvert\mathbf a\rvert$, $\overrightarrow{\mathrm{AB}}=\mathbf b-\mathbf a$; a force of magnitude $F$ along $\mathbf d$ is $F\mathbf d/\lvert\mathbf d\rvert$. Direction cosines $l=x/r$, $m=y/r$, $n=z/r$ with $l^2+m^2+n^2=1$.

$$
\mathbf a\cdot\mathbf b=\lvert\mathbf a\rvert\lvert\mathbf b\rvert\cos\theta=a_1b_1+a_2b_2+a_3b_3,\qquad\mathbf a\perp\mathbf b\iff\mathbf a\cdot\mathbf b=0
$$

- Component of $\mathbf F$ along $\mathbf u$: $\mathbf F\cdot\mathbf u/\lvert\mathbf u\rvert$; vector part $(\mathbf F\cdot\hat{\mathbf u})\hat{\mathbf u}$. Work by a constant force: $W=\mathbf F\cdot\mathbf d$.

$$
\mathbf a\times\mathbf b=\begin{vmatrix}\mathbf i&\mathbf j&\mathbf k\\a_1&a_2&a_3\\b_1&b_2&b_3\end{vmatrix}=(a_2b_3-a_3b_2)\mathbf i-(a_1b_3-a_3b_1)\mathbf j+(a_1b_2-a_2b_1)\mathbf k,\qquad\lvert\mathbf a\times\mathbf b\rvert=\lvert\mathbf a\rvert\lvert\mathbf b\rvert\sin\theta
$$

- $\mathbf b\times\mathbf a=-\mathbf a\times\mathbf b$, $\mathbf a\times\mathbf a=\mathbf0$; $\mathbf a\times\mathbf b$ is normal to both (check by dotting). Parallel iff $\mathbf a\times\mathbf b=\mathbf0$.
- Unit normal to the plane of $\mathbf a,\mathbf b$: $\pm\dfrac{\mathbf a\times\mathbf b}{\lvert\mathbf a\times\mathbf b\rvert}$. Parallelogram area $\lvert\overrightarrow{\mathrm{AB}}\times\overrightarrow{\mathrm{AD}}\rvert$, triangle half of it.
- Moment about A of $\mathbf F$ acting at P, and velocity of P on a body turning about an axis through A (order fixed in both):

$$
\mathbf M_{\mathrm A}=\mathbf r\times\mathbf F,\quad\lvert\mathbf M_{\mathrm A}\rvert=\lvert\mathbf F\rvert d;\qquad\mathbf v=\boldsymbol\omega\times\mathbf r;\qquad\mathbf r=\overrightarrow{\mathrm{AP}}
$$

- Not associative: $\mathbf a\times(\mathbf b\times\mathbf c)=(\mathbf a\cdot\mathbf c)\mathbf b-(\mathbf a\cdot\mathbf b)\mathbf c$.

### Vectors II ([[MATH1054 M15 - Vectors II|M15]])

$$
[\mathbf a,\mathbf b,\mathbf c]=\mathbf a\cdot(\mathbf b\times\mathbf c)=\begin{vmatrix}a_1&a_2&a_3\\b_1&b_2&b_3\\c_1&c_2&c_3\end{vmatrix},\qquad V_{\text{parallelepiped}}=\lvert[\mathbf a,\mathbf b,\mathbf c]\rvert
$$

- Cyclic order keeps the sign, a swap changes it; $[\mathbf a,\mathbf b,\mathbf c]=0$ iff the vectors are coplanar.
- Vector functions of $t$ (fixed $\mathbf i,\mathbf j,\mathbf k$), differentiated and integrated component by component; one constant vector per integration:

$$
\frac{\mathrm d}{\mathrm dt}(\lambda\mathbf v)=\dot\lambda\mathbf v+\lambda\dot{\mathbf v},\qquad\frac{\mathrm d}{\mathrm dt}(\mathbf u\cdot\mathbf v)=\dot{\mathbf u}\cdot\mathbf v+\mathbf u\cdot\dot{\mathbf v},\qquad\frac{\mathrm d}{\mathrm dt}(\mathbf u\times\mathbf v)=\dot{\mathbf u}\times\mathbf v+\mathbf u\times\dot{\mathbf v}
$$

- $\lvert\mathbf a\rvert$ constant $\Rightarrow\mathbf a\cdot\dot{\mathbf a}=0$. Rate of change of distance from O: $\frac{\mathrm d}{\mathrm dt}\lvert\mathbf r\rvert=\hat{\mathbf r}\cdot\dot{\mathbf r}$ (not the speed $\lvert\dot{\mathbf r}\rvert$).
- Plane polar coordinates, $\omega=\dot\theta$, $\hat{\mathbf r}=\cos\theta\,\mathbf i+\sin\theta\,\mathbf j$, $\hat{\boldsymbol\theta}=-\sin\theta\,\mathbf i+\cos\theta\,\mathbf j$:

$$
\dot{\mathbf r}=\dot r\,\hat{\mathbf r}+r\omega\,\hat{\boldsymbol\theta},\qquad\ddot{\mathbf r}=(\ddot r-r\omega^2)\,\hat{\mathbf r}+(2\dot r\omega+r\dot\omega)\,\hat{\boldsymbol\theta}
$$

- Line through A with direction $\mathbf d$: $\mathbf r=\mathbf a+t\mathbf d$, or $\dfrac{x-a_1}{d_1}=\dfrac{y-a_2}{d_2}=\dfrac{z-a_3}{d_3}$ (a zero $d_i$ means that coordinate is fixed). Angle between lines from $\mathbf d_1\cdot\mathbf d_2$. Two lines meet only if all three components agree.
- Plane with normal $\mathbf n$ through A: $\mathbf r\cdot\mathbf n=\mathbf a\cdot\mathbf n=p$, i.e. $n_1x+n_2y+n_3z=p$; through A, B, C: $\mathbf n=(\mathbf b-\mathbf a)\times(\mathbf c-\mathbf a)$. Distance of the plane from O is $\lvert p\rvert/\lvert\mathbf n\rvert$.
- Line meets plane at $t=\dfrac{p-\mathbf a\cdot\mathbf n}{\mathbf d\cdot\mathbf n}$ ($\mathbf d\cdot\mathbf n=0$: parallel). Two planes meet along $\mathbf d=\mathbf n_1\times\mathbf n_2$.
- Distances (component of a joining vector along the common unit normal):

$$
D_{\text{skew lines}}=\frac{\lvert(\mathbf a_2-\mathbf a_1)\cdot(\mathbf d_1\times\mathbf d_2)\rvert}{\lvert\mathbf d_1\times\mathbf d_2\rvert},\qquad D_{\text{point–plane}}=\frac{\lvert\mathbf p_0\cdot\mathbf n-p\rvert}{\lvert\mathbf n\rvert}=\frac{\lvert n_1x_0+n_2y_0+n_3z_0-p\rvert}{\sqrt{n_1^2+n_2^2+n_3^2}}
$$

### Matrices I ([[MATH1054 M16 - Matrices I|M16]])

- $\mathbf A\pm\mathbf B$ needs equal orders; $\mathbf{AB}$ needs (columns of $\mathbf A$) = (rows of $\mathbf B$), and an $m\times n$ times $n\times p$ is $m\times p$:

$$
(\mathbf{AB})_{ij}=\sum_ka_{ik}b_{kj},\qquad(\mathbf{AB})^{\mathrm T}=\mathbf B^{\mathrm T}\mathbf A^{\mathrm T}
$$

- Associative and distributive, but in general $\mathbf{AB}\neq\mathbf{BA}$, and $\mathbf{AB}=\mathbf0$ does not imply $\mathbf A=\mathbf0$ or $\mathbf B=\mathbf0$.
- $\mathbf A=\frac12(\mathbf A+\mathbf A^{\mathrm T})+\frac12(\mathbf A-\mathbf A^{\mathrm T})$ (symmetric + skew-symmetric); a quadratic form $\mathbf X^{\mathrm T}\mathbf A\mathbf X$ depends only on the symmetric part.
- Axes rotated anticlockwise by $\theta$: $x'=x\cos\theta+y\sin\theta$, $y'=-x\sin\theta+y\cos\theta$.
- Determinants: $\begin{vmatrix}a&b\\c&d\end{vmatrix}=ad-bc$; minor $M_{ij}$, cofactor $A_{ij}=(-1)^{i+j}M_{ij}$ (chessboard of signs from $+$ at top left); expand along any row or column, $\lvert\mathbf A\rvert=\sum_ja_{ij}A_{ij}=\sum_ia_{ij}A_{ij}$.

| Operation | Effect on $\lvert\mathbf A\rvert$ |
|---|---|
| swap two rows (or columns) | changes sign |
| multiply one row by $\lambda$ | multiplies by $\lambda$ (so $\lvert\lambda\mathbf A\rvert=\lambda^n\lvert\mathbf A\rvert$ for $n\times n$) |
| add a multiple of one row to another | none |
| transpose | none |
| two equal or proportional rows | $\lvert\mathbf A\rvert=0$ |
| triangular matrix | product of the diagonal |
| product | $\lvert\mathbf{AB}\rvert=\lvert\mathbf A\rvert\lvert\mathbf B\rvert$ |

- Adjoint (transpose of the cofactor matrix) and the adjoint theorem; alien cofactors sum to zero:

$$
\operatorname{adj}\mathbf A=\big[A_{ij}\big]^{\mathrm T},\qquad\mathbf A(\operatorname{adj}\mathbf A)=(\operatorname{adj}\mathbf A)\mathbf A=\lvert\mathbf A\rvert\,\mathbf I
$$

### Matrices II ([[MATH1054 M17 - Matrices II|M17]])

$$
\mathbf A^{-1}=\frac1{\lvert\mathbf A\rvert}\operatorname{adj}\mathbf A\ \ (\lvert\mathbf A\rvert\neq0),\qquad\begin{bmatrix}a&b\\c&d\end{bmatrix}^{-1}=\frac1{ad-bc}\begin{bmatrix}d&-b\\-c&a\end{bmatrix},\qquad(\mathbf{AB})^{-1}=\mathbf B^{-1}\mathbf A^{-1},\qquad(\mathbf A^{\mathrm T})^{-1}=(\mathbf A^{-1})^{\mathrm T}
$$

| $\mathbf{AX}=\mathbf b$, $\mathbf A$ square | $\mathbf b\neq\mathbf0$ | $\mathbf b=\mathbf0$ (homogeneous) |
|---|---|---|
| $\lvert\mathbf A\rvert\neq0$ | unique, $\mathbf X=\mathbf A^{-1}\mathbf b$ | only $\mathbf X=\mathbf0$ |
| $\lvert\mathbf A\rvert=0$ | none or infinitely many | infinitely many non-trivial |

- $\mathbf{AX}=\mathbf0$ has a non-trivial solution iff $\lvert\mathbf A\rvert=0$ (the condition for a parameter $\alpha$).
- Cramer's rule, $\mathbf A_i$ = $\mathbf A$ with column $i$ replaced by $\mathbf b$: $x_i=\lvert\mathbf A_i\rvert/\lvert\mathbf A\rvert$ ($\lvert\mathbf A\rvert\neq0$).
- Gaussian elimination: reduce $[\mathbf A\,|\,\mathbf b]$ to upper-triangular form with row operations on whole rows, then back-substitute. A row $0=0$ gives a free parameter; a row $0=c\neq0$ means no solution. Inverse by elimination: $[\mathbf A\,|\,\mathbf I]\to[\mathbf I\,|\,\mathbf A^{-1}]$. Partial pivoting puts the largest entry of the column on the diagonal.
- Ill-conditioned: a determinant small relative to the entries (nearly parallel lines), so small changes in the coefficients move the solution a long way.

### Matrices III ([[MATH1054 M18 - Matrices III|M18]])

- $\operatorname{rank}\mathbf A$ = number of non-zero rows in echelon form = order of the largest non-zero minor; $\operatorname{rank}\mathbf A\le\min(m,n)$; for square $\mathbf A$, $\operatorname{rank}\mathbf A=n\iff\lvert\mathbf A\rvert\neq0$.
- Consistency of $\mathbf{AX}=\mathbf b$, $n$ unknowns, any shape (count the rows of $\mathbf A$ with the last column covered):

| Ranks | Solutions |
|---|---|
| $\operatorname{rank}\mathbf A<\operatorname{rank}[\mathbf A\vert\mathbf b]$ | none |
| $\operatorname{rank}\mathbf A=\operatorname{rank}[\mathbf A\vert\mathbf b]=n$ | exactly one |
| $\operatorname{rank}\mathbf A=\operatorname{rank}[\mathbf A\vert\mathbf b]=r<n$ | infinitely many, $n-r$ free parameters |

- $\mathbf{AX}=\mathbf0$ always has $\mathbf X=\mathbf0$, and non-trivial solutions iff $\operatorname{rank}\mathbf A<n$.
- Eigenvalue method ($\mathbf X\neq\mathbf0$, each eigenvector only up to a non-zero constant):

$$
\mathbf{AX}=\lambda\mathbf X\ \Rightarrow\ (\mathbf A-\lambda\mathbf I)\mathbf X=\mathbf0,\qquad\lvert\mathbf A-\lambda\mathbf I\rvert=0
$$

$$
2\times2:\ \lambda^2-(\operatorname{tr}\mathbf A)\lambda+\lvert\mathbf A\rvert=0;\qquad\lambda_1+\dots+\lambda_n=\operatorname{tr}\mathbf A,\qquad\lambda_1\lambda_2\cdots\lambda_n=\lvert\mathbf A\rvert
$$

- Then solve $(\mathbf A-\lambda_i\mathbf I)\mathbf X=\mathbf0$ for each $\lambda_i$ and check $\mathbf{AX}=\lambda\mathbf X$. Normalised: $\hat{\mathbf e}=\mathbf e/\lvert\mathbf e\rvert$. Triangular matrix: eigenvalues are the diagonal entries. Distinct eigenvalues give independent eigenvectors.
- Real symmetric matrix: real eigenvalues, and eigenvectors of distinct eigenvalues orthogonal, $\mathbf e_i^{\mathrm T}\mathbf e_j=0$. A rotation such as $\begin{bmatrix}0&-1\\1&0\end{bmatrix}$ has complex eigenvalues $\pm\mathrm j$.

## Block 5: Series and statistics

### Further Calculus II ([[MATH1054 M20 - Further Calculus II|M20]])

$$
\text{AP: }a_k=a+(k-1)d,\quad S_n=\frac n2\big[2a+(n-1)d\big]=\frac n2(\text{first}+\text{last})
$$

$$
\text{GP: }a_k=ar^{k-1},\quad S_n=\frac{a(1-r^n)}{1-r}\ (r\neq1),\quad S_\infty=\frac a{1-r}\ (\lvert r\rvert<1)
$$

- Limits of sequences: divide by the highest power of $n$; $1/n^p\to0$ ($p>0$); $r^n\to0$ ($\lvert r\rvert<1$); $x^n/n!\to0$ (any fixed $x$); $(1+1/n)^n\to e$.
- $\sum u_k$ converges when its partial sums $S_n$ tend to a limit. $n$th-term test: $u_n\not\to0\Rightarrow$ diverges ($u_n\to0$ proves nothing: the harmonic series $\sum1/k$ diverges, $\sum1/k^2$ converges).
- Comparison: $0\le u_k\le c_k$ and $\sum c_k$ converges $\Rightarrow\sum u_k$ converges. D'Alembert's ratio test, positive terms (use $\lvert u_k\rvert$ otherwise; absolute convergence implies convergence):

$$
\ell=\lim_{n\to\infty}\frac{u_{n+1}}{u_n}:\quad\ell<1\text{ converges},\quad\ell>1\text{ diverges},\quad\ell=1\text{ no conclusion}
$$

- Power series $\sum a_nx^n$ converges for $\lvert x\rvert<R$ and diverges for $\lvert x\rvert>R$, endpoints checked separately; standard series in the M08 section above:

$$
R=\lim_{n\to\infty}\left\lvert\frac{a_n}{a_{n+1}}\right\rvert
$$

- Rolle: $f$ continuous on $[a,b]$, differentiable on $(a,b)$, $f(a)=f(b)\Rightarrow f'(c)=0$ for some $c\in(a,b)$. Mean value theorems, $a<c<b$:

$$
f(c)=\frac1{b-a}\int_a^bf\,\mathrm dx,\qquad f'(c)=\frac{f(b)-f(a)}{b-a},\qquad f(a+h)=f(a)+hf'(a+\theta h)\ (0<\theta<1)
$$

- Maclaurin's theorem with the Lagrange remainder ($f^{(n+1)}$ exists between $0$ and $x$; $\theta$ unknown, so bound $\lvert f^{(n+1)}\rvert$ over $0<\theta<1$); $R_n$ follows the $x^n$ term:

$$
f(x)=f(0)+xf'(0)+\frac{x^2}{2!}f''(0)+\dots+\frac{x^n}{n!}f^{(n)}(0)+R_n(x),\qquad R_n(x)=\frac{x^{n+1}}{(n+1)!}f^{(n+1)}(\theta x),\ 0<\theta<1
$$

- L'Hôpital, for $\frac00$ (or $\frac\infty\infty$), provided the right-hand limit exists; differentiate top and bottom separately and recheck the form before repeating:

$$
\lim_{x\to a}\frac{f(x)}{g(x)}=\lim_{x\to a}\frac{f'(x)}{g'(x)}
$$

### Statistics I ([[MATH1054 M24 - Statistics I|M24]])

- Equally likely outcomes: $P(E)=\lvert E\rvert/\lvert S\rvert$. $P(\bar A)=1-P(A)$; $P(A\cap\bar B)=P(A)-P(A\cap B)$.

$$
P(A\cup B)=P(A)+P(B)-P(A\cap B),\qquad P(B\mid A)=\frac{P(A\cap B)}{P(A)}\ (P(A)>0),\qquad P(A\cap B)=P(A)P(B\mid A)
$$

- Independent iff $P(A\cap B)=P(A)P(B)$ (then probabilities of several independent events multiply). Exclusive events ($P(A\cap B)=0$) add; independent events multiply; "at least one" $=1-P(\text{none})$.
- Total probability and Bayes, for a partition $A_1,\dots,A_n$ of $S$:

$$
P(F)=\sum_iP(A_i)P(F\mid A_i),\qquad P(A_j\mid F)=\frac{P(A_j)P(F\mid A_j)}{\sum_iP(A_i)P(F\mid A_i)}
$$

- Counting: $n!$ orderings; ${}^nP_r=\dfrac{n!}{(n-r)!}$ ordered selections; $\dbinom nr=\dfrac{n!}{r!\,(n-r)!}$ unordered.
- Discrete $X$: $p_X(x)=P(X=x)\ge0$, $\sum_kp_X(v_k)=1$, $F_X(x)=P(X\le x)=\sum_{v_k\le x}p_X(v_k)$. Continuous $X$: $f_X=F_X'\ge0$, $F_X(x)=\int_{-\infty}^xf_X$, $\int_{-\infty}^\infty f_X\,\mathrm dx=1$, $P(X=x)=0$ ($f_X$ is not a probability and may exceed 1). Both: $P(a<X\le b)=F_X(b)-F_X(a)$.

$$
\mu_X=E[X]=\sum_kv_kp_X(v_k)\ \text{ or }\int_{-\infty}^\infty xf_X\,\mathrm dx,\qquad E[h(X)]=\sum h(v_k)p_X(v_k)\ \text{ or }\int h(x)f_X\,\mathrm dx
$$

$$
\sigma_X^2=\operatorname{Var}X=E\big[(X-\mu_X)^2\big]=E[X^2]-\mu_X^2,\qquad\sigma_X=\sqrt{\operatorname{Var}X}
$$

- Median $F_X(m_X)=\frac12$ (discrete: first value where $F_X$ reaches $\frac12$); quartiles $F_X(Q_1)=\frac14$, $F_X(Q_3)=\frac34$, IQR $=Q_3-Q_1$; mode where $p_X$ or $f_X$ is largest.
- Exponential, rate $\lambda>0$:

$$
f_X=\lambda e^{-\lambda x}\ (x\ge0),\quad F_X=1-e^{-\lambda x},\quad\mu=\sigma=\frac1\lambda,\quad q_p=-\frac{\ln(1-p)}\lambda,\quad\text{median}=\frac{\ln2}\lambda
$$

### Statistics II ([[MATH1054 M25 - Statistics II|M25]])

- Independent $X,Y$: $P(X=u_i,Y=v_j)=P(X=u_i)P(Y=v_j)$; a row or column sum of the joint table gives the marginal distribution.

$$
E(X+Y)=E(X)+E(Y)\ \text{(always)},\qquad\operatorname{Var}(X+Y)=\operatorname{Var}X+\operatorname{Var}Y\ \text{(independent)}
$$

$$
E(X+c)=\mu_X+c,\quad\operatorname{Var}(X+c)=\sigma_X^2,\quad E(cX)=c\mu_X,\quad\operatorname{Var}(cX)=c^2\sigma_X^2
$$

- Sample mean of $n$ independent observations: $E(\bar X)=\mu_X$, $\operatorname{Var}\bar X=\sigma_X^2/n$, standard error $\sigma_{\bar X}=\sigma_X/\sqrt n$.
- Sample statistics (divisor $n-1$ in this module):

$$
\bar x=\frac1n\sum x_i,\qquad s^2=\frac1{n-1}\sum(x_i-\bar x)^2=\frac{\sum x_i^2-n\bar x^2}{n-1}
$$

- Binomial $Y\sim\mathrm{Bin}(n,p)$: fixed $n$, independent trials, constant $p$, $q=1-p$; "at least $k$" via $1-P(Y\le k-1)$.

$$
P(Y=k)=\binom nkp^k(1-p)^{n-k},\ k=0,\dots,n,\qquad E(Y)=np,\qquad\operatorname{Var}Y=np(1-p)
$$

- Normal $X\sim N(\mu,\sigma^2)$, second parameter the variance:

$$
f_X=\frac1{\sigma\sqrt{2\pi}}\exp\Big[-\frac12\Big(\frac{x-\mu}\sigma\Big)^2\Big],\qquad Z=\frac{X-\mu}\sigma\sim N(0,1),\qquad P(a<X\le b)=\Phi\Big(\frac{b-\mu}\sigma\Big)-\Phi\Big(\frac{a-\mu}\sigma\Big)
$$

- $\Phi(-z)=1-\Phi(z)$; inverse problems $x=\mu+z\sigma$; $P(\lvert Z\rvert\le z)=2\Phi(z)-1$.

| Central coverage | $\Phi(z)$ | $z$ | One tail beyond $z$ |
|---|---|---|---|
| 68.3% | 0.8413 | 1 | 15.9% |
| 90% | 0.95 | 1.645 | 5% |
| 95% | 0.975 | 1.96 | 2.5% |
| 99% | 0.995 | 2.58 | 0.5% |

- Central limit theorem: $Z=\dfrac{\bar X-\mu}{\sigma/\sqrt n}$ is exactly $N(0,1)$ for a normal parent, approximately for $n\ge30$ whatever the parent; for $n\ge30$ an unknown $\sigma$ may be replaced by $s$ (for $n<30$ with $s$ the $t$-distribution applies, not in this module).
- Confidence interval for $\mu$, and the sample size for a margin $E$:

$$
\bar x\pm z\frac\sigma{\sqrt n},\quad z=1.645\ (90\%),\ 1.96\ (95\%),\ 2.58\ (99\%);\qquad n\ge\Big(\frac{z\sigma}E\Big)^2\ \text{rounded up}
$$

- Test of $H_0:\mu=\mu_0$; choose one or two tails from the wording before computing:

$$
Z=\frac{\bar x-\mu_0}{\sigma/\sqrt n}
$$

| $H_1$ | Reject $H_0$ when | 5% | 1% |
|---|---|---|---|
| $\mu>\mu_0$ | $Z>z_\alpha$ | $Z>1.645$ | $Z>2.326$ |
| $\mu<\mu_0$ | $Z<-z_\alpha$ | $Z<-1.645$ | $Z<-2.326$ |
| $\mu\neq\mu_0$ | $\lvert Z\rvert>z_{\alpha/2}$ | $\lvert Z\rvert>1.96$ | $\lvert Z\rvert>2.58$ |

- $P(\text{type I error})=\alpha$; type II (accepting a false $H_0$) is not fixed by the test. p-value: $P(Z\ge z_{\text{obs}})$ one-tailed, $2P(Z\ge\lvert z_{\text{obs}}\rvert)$ two-tailed; reject when $p<\alpha$. A two-tailed 5% test accepts $\mu_0$ exactly when it lies in the 95% interval.
