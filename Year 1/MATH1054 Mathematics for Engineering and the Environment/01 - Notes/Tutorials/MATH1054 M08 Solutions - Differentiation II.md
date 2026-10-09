---
title: "MATH1054 M08 Solutions - Differentiation II"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: tutorial
stream: "Block 1: Calculus"
tags:
  - math1054
  - tutorial-solutions
  - differentiation
  - curve-sketching
  - maclaurin-series
sheet: "Module 08 work scheme: Examples 2.36, 2.37, 8.21–8.36, 9.10; Exercises 44, 47, 51, 52, 53, 58, 65, 79, 80; Booklet Exercises A, B; Specimen Test 8"
theory_notes: ["[[MATH1054 M08 - Differentiation II]]"]
key_concepts: ["[[Implicit and Parametric Differentiation]]", "[[Logarithmic Differentiation]]", "[[Stationary Points and Inflection]]", "[[Taylor and Maclaurin Series]]"]
status: complete
sources: ["tmp/md/module_08_differentiation_ii.md", "02 - Sources/Modern Engineering Mathematics.pdf (§2.5, §8.3.14, §8.4–8.5, §9.4)", "02 - Sources/Course Booklets & Solutions/Module Booklet.pdf (Module 8)"]
---

# MATH1054 M08 Solutions - Differentiation II

> [!abstract] Sheet Info
> The whole Module 08 work scheme plus Specimen Test 8. Checks:
> - implicit and parametric derivatives, stationary points and series: SymPy;
> - the two optimisation examples (8.35, 8.36): solved numerically with `brentq` and `minimize_scalar`.
>
> Curve sketches are plotted from the exact formulae.

## Theory Links
- [[MATH1054 M08 - Differentiation II]] · [[Implicit and Parametric Differentiation]] · [[Logarithmic Differentiation]] · [[Stationary Points and Inflection]] · [[Taylor and Maclaurin Series]]

---

# Part A: Worked examples

## Example 2.36: $y=\dfrac1{3-x}$ and the inequality $\dfrac1{3-x}<2$
**Sketch**:
- There is a vertical asymptote at $x=3$ and a horizontal asymptote $y=0$.
- For $x<3$, $y>0$ and $y$ increases to $+\infty$ as $x\to3^-$.
- For $x>3$, $y<0$.
- The $y$-intercept is $\frac13$.

**Inequality.** Don't multiply by $(3-x)$ without knowing its sign. Split into two cases.
- **Case $x<3$**: $3-x>0$, so $1<2(3-x)$, which gives $x<\tfrac52$.
- **Case $x>3$**: the left side is negative, so it is always $<2$. Every $x>3$ works.

$$\boxed{x<\tfrac52\quad\text{or}\quad x>3}$$

Graphically, these are the $x$ where the curve lies below the line $y=2$. They meet at $x=\frac52$.

![[m1054_curve_sketches_rational.png|800]]

## Example 2.37: $y=\dfrac{x^2-x-6}{x+1}$
- **Divide**: $x^2-x-6=(x+1)(x-2)-4$, so $y=x-2-\dfrac4{x+1}$.
- **Zeros**: $(x-3)(x+2)=0$ gives $x=3$ and $x=-2$. The $y$-intercept is $-6$.
- **Asymptotes**: vertical $x=-1$; oblique $y=x-2$, because $\frac4{x+1}\to0$.
- **Slope**: $y'=1+\dfrac4{(x+1)^2}>0$ everywhere, so there are **no turning points**. Each branch increases.
- **Sides of the oblique asymptote**: as $x\to+\infty$ the curve is below it ($-\frac4{x+1}<0$). As $x\to-\infty$ it is above.

## Example 8.21: $x=t^3$, $y=t^2$

$$\frac{\mathrm dy}{\mathrm dx}=\frac{\mathrm dy/\mathrm dt}{\mathrm dx/\mathrm dt}=\frac{2t}{3t^2}=\boxed{\frac2{3t}}\quad(t\neq0)$$

Equivalently $y=x^{2/3}$ and $y'=\frac23x^{-1/3}$. There is a **cusp** at the origin, where the slope is infinite.

## Example 8.22: $x^2+y^2+xy=1$
Differentiate term by term. Here $y$ is a function of $x$, so $\frac{\mathrm d}{\mathrm dx}y^2=2yy'$ and $\frac{\mathrm d}{\mathrm dx}(xy)=y+xy'$:

$$2x+2yy'+y+xy'=0\ \Rightarrow\ \boxed{y'=-\frac{2x+y}{x+2y}}$$

## Example 8.23: Tangent and normal to $x^2+y^2-3xy+4=0$ at $(2,4)$
Differentiate implicitly:

$$2x+2yy'-3y-3xy'=0\ \Rightarrow\ y'=\frac{3y-2x}{2y-3x}$$

At $(2,4)$: $y'=\dfrac{12-4}{8-6}=4$.
- Tangent: $y-4=4(x-2)$, so $\boxed{y=4x-4}$.
- Normal: $y-4=-\frac14(x-2)$, so $\boxed{x+4y=18}$.

## Example 8.24: Slopes on the circle $x^2+y^2-2x+4y-20=0$
Differentiate implicitly:

$$2x+2yy'-2+4y'=0\ \Rightarrow\ y'=\frac{1-x}{y+2}$$

| Point | $y'$ |
|---|---|
| A$(1,3)$ | $0$ (horizontal tangent: the top of the circle) |
| B$(4,2)$ | $\frac{-3}4$ |
| C$(-2,-6)$ | $\frac{3}{-4}=-\frac34$ |

The circle is $(x-1)^2+(y+2)^2=25$, with centre $(1,-2)$. B and C are **diametrically opposite**, since their midpoint is the centre, so their tangents are parallel ✔.

## Example 8.25: $f=(\sin x)^x$ on $(0,\pi)$
A variable base *and* a variable exponent calls for logarithmic differentiation:

$$\ln f=x\ln\sin x\ \Rightarrow\ \frac{f'}{f}=\ln\sin x+x\cdot\frac{\cos x}{\sin x}$$

$$\boxed{f'(x)=(\sin x)^x\big(\ln\sin x+x\cot x\big)}$$

## Example 8.26: $y=\dfrac{(x-2)^3(x+3)^9}{\sqrt{x^2+1}}$
Take logs of the product and quotient:

$$\ln y=3\ln(x-2)+9\ln(x+3)-\tfrac12\ln(x^2+1)$$

$$\frac{y'}y=\frac3{x-2}+\frac9{x+3}-\frac{x}{x^2+1}$$

Putting everything over a common denominator:

$$y'=\frac{(x-2)^3(x+3)^9}{\sqrt{x^2+1}}\left[\frac{3}{x-2}+\frac9{x+3}-\frac x{x^2+1}\right]=\boxed{\frac{(x-2)^2(x+3)^8(11x^3-10x^2+18x-9)}{(x^2+1)^{3/2}}}$$

## Example 8.29: Second derivatives
**(a)** $y=t^2$, $x=t^3$. From Ex 8.21, $\dfrac{\mathrm dy}{\mathrm dx}=\dfrac{2}{3t}$. Then

$$\frac{\mathrm d^2y}{\mathrm dx^2}=\frac{\frac{\mathrm d}{\mathrm dt}\big(\frac2{3t}\big)}{\mathrm dx/\mathrm dt}=\frac{-\frac{2}{3t^2}}{3t^2}=\boxed{-\frac{2}{9t^4}}$$

> [!warning] The classic error
> $\dfrac{\mathrm d^2y}{\mathrm dx^2}\neq\dfrac{\mathrm d^2y/\mathrm dt^2}{\mathrm d^2x/\mathrm dt^2}$. Always differentiate $\frac{\mathrm dy}{\mathrm dx}$ with respect to $t$, then divide by $\frac{\mathrm dx}{\mathrm dt}$.

**(b)** $x^2+y^2-2x+4y-20=0$, with $y'=\dfrac{1-x}{y+2}$ (Ex 8.24). By the quotient rule:

$$y''=\frac{-(y+2)-(1-x)y'}{(y+2)^2}=-\frac{(y+2)^2+(1-x)^2}{(y+2)^3}$$

On the circle, $(x-1)^2+(y+2)^2=25$, so

$$\boxed{y''=-\frac{25}{(y+2)^3}}$$

## Example 8.31: The nature of the stationary points of $f=4x^3-21x^2+18x+6$
- $f'=12x^2-42x+18=6(2x-1)(x-3)=0$ gives $x=\tfrac12$ and $x=3$.
- $f''=24x-42$.

| $x$ | $f''$ | nature | $f$ |
|---|---|---|---|
| $\tfrac12$ | $-30<0$ | **local maximum** | $\tfrac{41}4=10.25$ |
| $3$ | $+30>0$ | **local minimum** | $-21$ |

## Example 8.34 (read only): Economic lot size
- One run of $q$ items costs $c_1+c_2q$ and lasts $q/N$ months. So the monthly production cost is $\dfrac{c_1N}{q}+c_2N$.
- The average stock is $\tfrac12q$, so the storage cost is $\tfrac12c_3q$.

$$C(q)=\frac{c_1N}{q}+c_2N+\tfrac12c_3q,\qquad C'(q)=-\frac{c_1N}{q^2}+\tfrac12c_3=0\ \Rightarrow\ \boxed{q^*=\sqrt{\frac{2c_1N}{c_3}}}$$

$C''=2c_1N/q^3>0$, so this is a minimum. It is the **economic lot size**.

## Example 8.35 (read only): Milk carton
- The carton is $b\times b\times h$ (mm). The sheet is $(4b+5)$ wide (four faces plus the 5 mm seam). Its length is $h+b+10$: a flap of $\frac b2+5$ at the top and at the bottom.
- The area is $A=(4b+5)(h+b+10)$, subject to $b^2h=1\,136\,000$ mm³.
- Substituting for $h$:

$$A(b)=(4b+5)\Big(\frac{1\,136\,000}{b^2}+b+10\Big)$$

- Setting $A'(b)=8b+45-\dfrac{4\,544\,000}{b^2}-\dfrac{11\,360\,000}{b^3}=0$ gives the quartic $8b^4+45b^3-4\,544\,000b-11\,360\,000=0$.
- Its root is $b=81.8$ mm (found with `brentq`), so $h=1\,136\,000/b^2=169.7$ mm.

$$\boxed{81.8\times81.8\times169.7\ \text{mm}},\qquad A_{\min}\approx8.69\times10^4\ \text{mm}^2$$

## Example 8.36 (read only): When to replace the car
Over $t$ years:
- **Depreciation**: $14\,750-e^{9.55-0.11t}$.
- **Accumulated running cost**: $\int_0^t(917+163\tau)\,\mathrm d\tau=917t+81.5t^2$.

The right quantity to minimise is the **average cost per year**:

$$C(t)=\frac{14\,750-e^{9.55-0.11t}+917t+81.5t^2}{t}$$

$C'(t)=0$ is equivalent to $tT'(t)=T(t)$, where $T$ is the numerator. This simplifies to

$$e^{9.55-0.11t}(1+0.11t)+81.5t^2=14\,750.$$

The root is $t\approx5.43$ years, where $C\approx£2653$ per year. Check: $C(5)=2653.9$ and $C(6)=2654.5$.

**Replace the car after about $5\tfrac12$ years.** The minimum is very flat, so anywhere from 5 to 6 years costs almost the same.

## Example 9.10: Maclaurin series of $e^x\sin x$
Differentiate repeatedly. Since $f^{(4)}=-4f$, the pattern repeats every four derivatives.

| $n$ | $f^{(n)}(x)$ | $f^{(n)}(0)$ |
|---|---|---|
| 0 | $e^x\sin x$ | 0 |
| 1 | $e^x(\sin x+\cos x)$ | 1 |
| 2 | $2e^x\cos x$ | 2 |
| 3 | $2e^x(\cos x-\sin x)$ | 2 |
| 4 | $-4e^x\sin x$ | 0 |
| 5 | $-4e^x(\sin x+\cos x)$ | −4 |

$$e^x\sin x=0+x+\frac{2x^2}{2!}+\frac{2x^3}{3!}+0-\frac{4x^5}{5!}+\dots=\boxed{x+x^2+\frac{x^3}3-\frac{x^5}{30}+\dots}$$

**Check** by multiplying the series: $\big(1+x+\frac{x^2}2+\frac{x^3}6\big)\big(x-\frac{x^3}6\big)=x+x^2+\big(\tfrac12-\tfrac16\big)x^3+\dots$ ✔

---

# Part B: Assigned exercises

## Booklet Exercise A: Maclaurin series of $e^x$
$f^{(n)}(x)=e^x$ for every $n$, so $f^{(n)}(0)=1$. Then

$$e^x=\sum_{n=0}^\infty\frac{f^{(n)}(0)}{n!}x^n=1+\frac{x}{1!}+\frac{x^2}{2!}+\frac{x^3}{3!}+\cdots\ ✔$$

## Booklet Exercise B: $(1+x)\sin x$
**(a) From the derivatives**:

| $n$ | $f^{(n)}$ | at 0 |
|---|---|---|
| 0 | $(1+x)\sin x$ | 0 |
| 1 | $\sin x+(1+x)\cos x$ | 1 |
| 2 | $2\cos x-(1+x)\sin x$ | 2 |
| 3 | $-3\sin x-(1+x)\cos x$ | −1 |
| 4 | $-4\cos x+(1+x)\sin x$ | −4 |

$$(1+x)\sin x=x+\frac{2x^2}{2!}-\frac{x^3}{3!}-\frac{4x^4}{4!}+\dots=\boxed{x+x^2-\frac{x^3}6-\frac{x^4}6+\dots}$$

**(b) By multiplication**:

$$(1+x)\Big(x-\frac{x^3}6+\frac{x^5}{120}-\dots\Big)=x+x^2-\frac{x^3}6-\frac{x^4}6+\dots\ ✔$$

The two methods agree, and (b) is much quicker.

## Exercise 44 (p.126): Sketches
**(a)** $y=\dfrac{x^2-8x+15}x=x-8+\dfrac{15}x$
- Zeros at $x=3$ and $x=5$. Asymptotes $x=0$ and $y=x-8$.
- $y'=1-\dfrac{15}{x^2}=0$ gives $x=\pm\sqrt{15}$. Here $y''=30/x^3$.
  - $x=\sqrt{15}$: $y=2\sqrt{15}-8\approx-0.254$. This is a **local minimum**, and it matches the hint's form $(\sqrt x-\sqrt{15/x})^2+2\sqrt{15}-8$.
  - $x=-\sqrt{15}$: $y=-2\sqrt{15}-8\approx-15.75$. This is a **local maximum**.

**(b)** $y=\dfrac{x+1}{x-1}=1+\dfrac2{x-1}$
- Asymptotes $x=1$ and $y=1$. Intercepts $(-1,0)$ and $(0,-1)$.
- $y'=-\dfrac2{(x-1)^2}<0$, so there are **no turning points**. Both branches decrease. The graph is a rectangular hyperbola centred at $(1,1)$.

## Exercise 47: Spiral $x=t\sin t$, $y=t\cos t$

$$\frac{\mathrm dy}{\mathrm dx}=\frac{\cos t-t\sin t}{\sin t+t\cos t}$$

## Exercise 51: Tangent to $y^3x+y+7x^4=4$ at $(0,4)$
Differentiate implicitly:

$$3y^2y'x+y^3+y'+28x^3=0\ \Rightarrow\ y'=-\frac{y^3+28x^3}{3xy^2+1}$$

At $(0,4)$: $y'=-64$. The tangent is $\boxed{y=4-64x}$.

## Exercise 52 (booklet-corrected curve): $x^3+y^3-xy-x=0$ at $(1,-1)$
The point is on the curve: $1-1+1-1=0$ ✔. Differentiate implicitly:

$$3x^2+3y^2y'-y-xy'-1=0\ \Rightarrow\ y'=\frac{1+y-3x^2}{3y^2-x}$$

At $(1,-1)$: $y'=\dfrac{1-1-3}{3-1}=\boxed{-\tfrac32}$.

## Exercise 53(a): $10^x$
$10^x=e^{x\ln10}$, so $\dfrac{\mathrm d}{\mathrm dx}10^x=\boxed{10^x\ln10}$. Equivalently, take logs: $\ln y=x\ln10$, so $y'/y=\ln10$.

## Exercise 58 (harder): Logarithmic differentiation
**(a)** $y=(\ln x)^x$:

$$\ln y=x\ln(\ln x)\ \Rightarrow\ \frac{y'}{y}=\ln(\ln x)+x\cdot\frac{1}{\ln x}\cdot\frac1x$$

$$\boxed{y'=(\ln x)^x\Big[\ln(\ln x)+\frac1{\ln x}\Big]}\qquad(x>1)$$

**(c)** $y=(1-x^2)^{1/2}(2x^2+3)^{-4/3}$:

$$\ln y=\tfrac12\ln(1-x^2)-\tfrac43\ln(2x^2+3)$$

$$\frac{y'}y=-\frac{x}{1-x^2}-\frac{16x}{3(2x^2+3)}=\frac{-3x(2x^2+3)-16x(1-x^2)}{3(1-x^2)(2x^2+3)}=\frac{5x(2x^2-5)}{3(1-x^2)(2x^2+3)}$$

$$\boxed{y'=\frac{5x(2x^2-5)}{3(1-x^2)^{1/2}(2x^2+3)^{7/3}}}$$

## Exercise 65: Cycloid $x=a(\theta-\sin\theta)$, $y=a(1-\cos\theta)$
First derivative, using half-angle identities:

$$\frac{\mathrm dy}{\mathrm dx}=\frac{a\sin\theta}{a(1-\cos\theta)}=\frac{2\sin\frac\theta2\cos\frac\theta2}{2\sin^2\frac\theta2}=\boxed{\cot\tfrac\theta2}$$

Second derivative:

$$\frac{\mathrm d^2y}{\mathrm dx^2}=\frac{\frac{\mathrm d}{\mathrm d\theta}\cot\frac\theta2}{\mathrm dx/\mathrm d\theta}=\frac{-\frac12\csc^2\frac\theta2}{a\cdot2\sin^2\frac\theta2}=\boxed{-\frac{1}{4a\sin^4\frac\theta2}=-\frac{1}{a(1-\cos\theta)^2}}$$

This is always negative, so the cycloid arches are concave down.

## Exercise 79(a): $f=2x^3-5x^2+4x-1$
- $f'=6x^2-10x+4=2(3x-2)(x-1)$, which is zero at $x=\tfrac23$ and $x=1$.
- $f''=12x-10$.
  - $x=\frac23$: $f''=-2$, so a **maximum**, with $f=\frac{16}{27}-\frac{20}9+\frac83-1=\boxed{\tfrac1{27}}$.
  - $x=1$: $f''=2$, so a **minimum**, with $f=\boxed0$.
- **Inflection** where $f''=0$: $x=\tfrac56$, $f=\tfrac1{54}$. $f''$ changes sign there ✔.
- **Sketch aids**: $f=(x-1)^2(2x-1)$, so the curve crosses the axis at $x=\frac12$ and touches it at $x=1$. The $y$-intercept is $-1$.

![[m1054_curve_sketches_stationary.png|800]]

## Exercise 80(c): $f=x^2e^{-x}$
- $f'=(2x-x^2)e^{-x}=x(2-x)e^{-x}=0$ gives $x=0$ and $x=2$.
- $f''=(x^2-4x+2)e^{-x}$.
  - $x=0$: $f''=2>0$, so a **minimum**, $f=0$.
  - $x=2$: $f''=-2e^{-2}<0$, so a **maximum**, $f=4e^{-2}\approx0.541$.
- Inflections at $x=2\pm\sqrt2$ (0.586 and 3.414).
- As $x\to\infty$, $f\to0^+$ because the exponential wins. As $x\to-\infty$, $f\to\infty$.

---

# Part C: Specimen Test 8

## Q1
**(i)** $x_0$ is a stationary point iff $f'(x_0)=0$.
**(ii)** For a **stationary point of inflection**, we need also $f''(x_0)=0$ **and** $f''$ must change sign through $x_0$. A sufficient condition is $f'''(x_0)\neq0$. Equivalently, $f'$ has the same sign on both sides of $x_0$. Note that $f''=0$ alone is not enough: $x^4$ has $f''(0)=0$ but a minimum at 0.

## Q2
**(i)** $f=x-x^2$: $f'=1-2x=0$ at $x=\frac12$. $f''=-2<0$, so it is a **maximum**, $f=\frac14$.
**(ii)** $f=x+e^x$: $f'=1+e^x>0$ for all $x$, so there are **no stationary points**.
**(iii)** $f=x^3-3x+3$: $f'=3(x^2-1)=0$ at $x=\pm1$, and $f''=6x$.
- $x=-1$: $f''<0$, so a **maximum**, $f=5$.
- $x=1$: $f''>0$, so a **minimum**, $f=1$.

## Q3: Sketch $y=x^3-3x^2+2$
- **Roots**: $y(1)=0$, so divide by $x-1$: $y=(x-1)(x^2-2x-2)$. The roots are $x=1$ and $1\pm\sqrt3\approx-0.732,\,2.732$.
- **Intercept**: $y(0)=2$.
- **Stationary points**: $y'=3x^2-6x=3x(x-2)$.
  - $x=0$: maximum, $y=2$.
  - $x=2$: minimum, $y=-2$.
- **Inflection**: $y''=6x-6=0$ at $x=1$, $y=0$. The curve has point symmetry about $(1,0)$.
- **End behaviour**: $y\to\pm\infty$ as $x\to\pm\infty$.

See the right panel of the figure above.

## Q4: $x=t^2$, $y=t^3$

$$\frac{\mathrm dy}{\mathrm dx}=\frac{3t^2}{2t}=\boxed{\frac{3t}2},\qquad\frac{\mathrm d^2y}{\mathrm dx^2}=\frac{\mathrm d(3t/2)/\mathrm dt}{\mathrm dx/\mathrm dt}=\frac{3/2}{2t}=\boxed{\frac3{4t}}$$

## Q5: Tangent to $x^3+y^2+xy-3=0$ at $(1,1)$
Differentiate implicitly:

$$3x^2+2yy'+y+xy'=0\ \Rightarrow\ y'=-\frac{3x^2+y}{2y+x}$$

At $(1,1)$: $y'=-\frac43$. The tangent is $y-1=-\frac43(x-1)$, i.e. $\boxed{4x+3y=7}$.

## Q6: Maclaurin series of $\sin x$
The derivatives cycle $\sin,\cos,-\sin,-\cos$, so at 0 they take the values $0,1,0,-1,0,1,\dots$ Then

$$\sin x=0+x+0-\frac{x^3}{3!}+0+\frac{x^5}{5!}-\dots=x-\frac{x^3}{3!}+\frac{x^5}{5!}-\cdots\ ✔$$

## Sources
- Transcribed problem statements: `tmp/md/module_08_differentiation_ii.md`
- James, *Modern Engineering Mathematics* (6th ed.) §2.5, §8.3.14–8.5, §9.4; MATH1054 Module Booklet, Module 8
