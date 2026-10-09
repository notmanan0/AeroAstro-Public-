---
title: "MATH1054 M11 Solutions - Integration IV"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: tutorial
stream: "Block 1: Calculus"
tags:
  - math1054
  - tutorial-solutions
  - multiple-integrals
sheet: "Specimen Test 11 (booklet) + Module 11 booklet: Exercises A–G (double integrals, change of order, polar area, triple integral)"
theory_notes: ["[[MATH1054 M11 - Integration IV]]"]
key_concepts: ["[[Double Integrals and Change of Order]]", "[[Jacobian and Volume Elements]]"]
status: complete
sources: ["tmp/md/module_11_integration_iv.md", "02 - Sources/Course Booklets & Solutions/Module Booklet.pdf (Module 11, pp.29–42)"]
---

# MATH1054 M11 Solutions - Integration IV

> [!abstract] Sheet Info
> Module 11 is entirely self-contained in the Module Booklet (James does not cover multiple integrals), so all seven tasks are booklet exercises. Every answer was checked with SymPy iterated `integrate`.
>
> **Convention**: in $\int\!\!\int f\,\mathrm dx\,\mathrm dy$, the **inner** integral goes with the **inner** differential ($\mathrm dx$ here) and is done first, holding the other variable constant.

## Theory Links
- [[MATH1054 M11 - Integration IV]] · [[Double Integrals and Change of Order]] · [[Jacobian and Volume Elements]] (MATH2048)

![[m1054_double_integral_regions.png|800]]

---

## Exercise A: Evaluate directly
**(i)** $\displaystyle\int_0^2\!\!\int_0^1(y+e^x)\,\mathrm dx\,\mathrm dy$. The region is the rectangle $0\le x\le1$, $0\le y\le2$.
- **Inner** (in $x$, with $y$ fixed): $\big[xy+e^x\big]_{x=0}^{1}=y+e-1$.
- **Outer**:
$$\int_0^2(y+e-1)\,\mathrm dy=\Big[\tfrac12y^2+(e-1)y\Big]_0^2=2+2e-2=\boxed{2e\approx5.4366}$$

**(ii)** $\displaystyle\int_0^{\pi/2}\!\!\int_0^{\pi/4}\sin(2x-y)\,\mathrm dx\,\mathrm dy$.
- **Inner**: $\Big[-\tfrac12\cos(2x-y)\Big]_{x=0}^{\pi/4}=-\tfrac12\cos\big(\tfrac\pi2-y\big)+\tfrac12\cos y=\tfrac12(\cos y-\sin y)$.
- **Outer**:
$$\int_0^{\pi/2}\tfrac12(\cos y-\sin y)\,\mathrm dy=\tfrac12\big[\sin y+\cos y\big]_0^{\pi/2}=\tfrac12(1-1)=\boxed0$$

The zero means the positive and negative parts of $\sin(2x-y)$ cancel over this rectangle. As a volume, it is the net signed volume.

## Exercise B: A(i) with the order changed
The region is a rectangle, so the limits simply swap:
$$\int_0^1\!\!\int_0^2(y+e^x)\,\mathrm dy\,\mathrm dx=\int_0^1\Big[\tfrac12y^2+ye^x\Big]_{y=0}^2\mathrm dx=\int_0^1(2+2e^x)\,\mathrm dx=\big[2x+2e^x\big]_0^1=2+2e-2=\boxed{2e}\ ✔$$

## Exercise C: $\displaystyle\int_{x=0}^1\!\!\int_{y=x}^{\sqrt x}(x^2+y^2)\,\mathrm dy\,\mathrm dx$
**Region**: between the line $y=x$ (below) and the curve $y=\sqrt x$ (above), for $0\le x\le1$. The two meet at $(0,0)$ and $(1,1)$.
- **Inner** (in $y$):
$$\Big[x^2y+\tfrac13y^3\Big]_{y=x}^{\sqrt x}=x^{5/2}+\tfrac13x^{3/2}-x^3-\tfrac13x^3=x^{5/2}+\tfrac13x^{3/2}-\tfrac43x^3$$
- **Outer**:
$$\int_0^1\Big(x^{5/2}+\tfrac13x^{3/2}-\tfrac43x^3\Big)\mathrm dx=\tfrac27+\tfrac2{15}-\tfrac13=\frac{30+14-35}{105}=\boxed{\tfrac{3}{35}}$$

## Exercise D: $I=\iint_\Delta\dfrac xy\,\mathrm dx\,\mathrm dy$ over the triangle bounded by $x=1$, $y=2$, $y=x$
**Region**: the vertices are $(1,1)$, $(1,2)$ and $(2,2)$. It can be described in two ways:
- horizontal strips: $1\le x\le y$, with $1\le y\le2$;
- vertical strips: $x\le y\le2$, with $1\le x\le2$.

**First way** ($x$ inner):
$$I=\int_1^2\!\!\int_1^y\frac xy\,\mathrm dx\,\mathrm dy=\int_1^2\frac1y\cdot\frac{y^2-1}2\,\mathrm dy=\int_1^2\Big(\frac y2-\frac1{2y}\Big)\mathrm dy=\Big[\frac{y^2}4-\frac12\ln y\Big]_1^2=\Big(1-\tfrac12\ln2\Big)-\tfrac14$$

**Second way** ($y$ inner):
$$I=\int_1^2\!\!\int_x^2\frac xy\,\mathrm dy\,\mathrm dx=\int_1^2x(\ln2-\ln x)\,\mathrm dx$$
- $\ln2\displaystyle\int_1^2x\,\mathrm dx=\tfrac32\ln2$.
- By parts, $\displaystyle\int_1^2x\ln x\,\mathrm dx=\Big[\tfrac{x^2}2\ln x-\tfrac{x^2}4\Big]_1^2=2\ln2-\tfrac34$.

So $I=\tfrac32\ln2-2\ln2+\tfrac34$.

Both routes give
$$\boxed{I=\tfrac34-\tfrac12\ln2\approx0.4034}\ ✔$$
The first order is easier, because $\frac1y$ is a constant factor for the inner integration.

## Exercise E: $\displaystyle\int_0^1\!\!\int_{\sqrt x}^1e^{y^3}\,\mathrm dy\,\mathrm dx$
As written, it **cannot** be done: $\int e^{y^3}\,\mathrm dy$ has no elementary antiderivative. So **change the order**.

**Region**: $\sqrt x\le y\le1$ and $0\le x\le1$. Equivalently, $0\le x\le y^2$ and $0\le y\le1$ (the region to the left of the parabola $x=y^2$).
$$\int_0^1\!\!\int_0^{y^2}e^{y^3}\,\mathrm dx\,\mathrm dy=\int_0^1y^2e^{y^3}\,\mathrm dy=\Big[\tfrac13e^{y^3}\Big]_0^1=\boxed{\tfrac13(e-1)\approx0.5728}$$
The $x$-integration produced exactly the factor $y^2$ needed for the substitution $u=y^3$.

## Exercise F: Area of the cardioid $r=a(1-\cos\theta)$
In polar coordinates $\mathrm dA=r\,\mathrm dr\,\mathrm d\theta$. For each $\theta$, $r$ runs from $0$ to $a(1-\cos\theta)$:
$$A=\int_0^{2\pi}\!\!\int_0^{a(1-\cos\theta)}r\,\mathrm dr\,\mathrm d\theta=\int_0^{2\pi}\tfrac12a^2(1-\cos\theta)^2\,\mathrm d\theta=\tfrac12a^2\int_0^{2\pi}\big(1-2\cos\theta+\cos^2\theta\big)\mathrm d\theta$$
Over a full period, $\int\cos\theta\,\mathrm d\theta=0$ and $\int\cos^2\theta\,\mathrm d\theta=\pi$. So
$$A=\tfrac12a^2(2\pi-0+\pi)=\boxed{\tfrac32\pi a^2}$$
This is six times the area of the circle of radius $a/2$ that rolls to generate the cardioid.

## Exercise G: $\displaystyle\int_0^3\!\!\int_0^2\!\!\int_0^1x\,\mathrm dx\,\mathrm dy\,\mathrm dz$
The limits are constant and the integrand depends only on $x$, so the integral factorises:
$$\Big(\int_0^1x\,\mathrm dx\Big)\Big(\int_0^2\mathrm dy\Big)\Big(\int_0^3\mathrm dz\Big)=\tfrac12\cdot2\cdot3=\boxed3$$
**Interpretation**: the box $[0,1]\times[0,2]\times[0,3]$ has volume 6 and centroid $\bar x=\frac12$. So $\iiint x\,\mathrm dV=\bar xV=3$ ✔.

---

# Part C: Specimen Test 11

> [!note] Source
> Transcribed from the MATH1054 Module Booklet (the final page of Module 11), then solved and checked with SymPy, NumPy or SciPy.

## Q1: Double integrals
**(i)**
$$\int_1^2\!\!\int_2^3xy^2\,\mathrm dx\,\mathrm dy=\int_1^2y^2\Big[\frac{x^2}2\Big]_2^3\mathrm dy=\frac52\Big[\frac{y^3}3\Big]_1^2=\frac52\cdot\frac73=\boxed{\tfrac{35}6}$$

**(ii)**
$$\int_0^1\!\!\int_{x^2}^1y\,\mathrm dy\,\mathrm dx=\int_0^1\tfrac12(1-x^4)\,\mathrm dx=\tfrac12\Big(1-\tfrac15\Big)=\boxed{\tfrac25}$$

## Q2: Describing the region between $y=x$ and $x=y^2$
The curves meet at $(0,0)$ and $(1,1)$. The curve $x=y^2$ is the upper boundary $y=\sqrt x$.
- **(i) $x$ fixed**: $x\le y\le\sqrt x$, with $0\le x\le1$.
- **(ii) $y$ fixed**: $y^2\le x\le y$, with $0\le y\le1$.

## Q3: $I=\int_{x=0}^1\!\int_{y=0}^{1-x^2}xy\,\mathrm dy\,\mathrm dx$
**(i)** The region is under the parabola $y=1-x^2$, above the $x$-axis, and to the right of the $y$-axis. It is a curved triangle with vertices $(0,0)$, $(1,0)$ and $(0,1)$ (see the figure).

**(ii)** Integrating $y$ first:
$$I=\int_0^1\frac{x(1-x^2)^2}{2}\,\mathrm dx=\frac12\int_0^1(x-2x^3+x^5)\,\mathrm dx=\frac12\Big(\frac12-\frac12+\frac16\Big)=\boxed{\tfrac1{12}}$$

**(iii)** For fixed $y$, $x$ runs from $0$ to $\sqrt{1-y}$:
$$I=\int_{y=0}^{1}\!\int_{x=0}^{\sqrt{1-y}}xy\,\mathrm dx\,\mathrm dy$$

**(iv)** Integrating $x$ first:
$$I=\int_0^1y\cdot\frac{1-y}{2}\,\mathrm dy=\frac12\Big(\frac12-\frac13\Big)=\boxed{\tfrac1{12}}\ ✔$$

![[m1054_spec11_regions.png|700]]

## Q4: Polar coordinates
**(i)** $\mathrm dA=r\,\mathrm dr\,\mathrm d\theta$.

**(ii)** The integral separates into a $\theta$ part and an $r$ part:
$$\int_0^\pi\!\!\int_0^a\sin\theta\,r\,\mathrm dr\,\mathrm d\theta=\Big[-\cos\theta\Big]_0^\pi\Big[\frac{r^2}2\Big]_0^a=2\cdot\frac{a^2}2=\boxed{a^2}$$

## Sources
- Transcribed problem statements: `tmp/md/module_11_integration_iv.md`
- MATH1054 Module Booklet, Module 11 (Integration IV, booklet pp.29–42)
