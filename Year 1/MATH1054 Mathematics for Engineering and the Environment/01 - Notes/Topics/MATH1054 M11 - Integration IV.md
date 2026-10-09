---
title: "MATH1054 M11 - Integration IV"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: topic
stream: "Block 1: Calculus"
order: 11
tags:
  - math1054
  - multiple-integrals
  - polar-coordinates
aliases: ["MATH1054 Module 11", "Integration IV", "Double integrals"]
date: 2026-09-27
status: complete
parent: ["[[MATH1054 Mathematics for Engineering and the Environment Hub]]"]
prerequisites: ["[[MATH1054 M10 - Integration III]]", "[[MATH1054 M03 - Differentiation I]]"]
next_topics: ["[[MATH1054 M14 - Vectors I]]"]
key_concepts: ["[[Double Integrals and Change of Order]]", "[[Jacobian and Volume Elements]]"]
tutorial_sheets: ["[[MATH1054 M11 Solutions - Integration IV]]"]
sources: ["02 - Sources/Course Booklets & Solutions/Module Booklet.pdf (Module 11, pp.29–42)"]
---

# MATH1054 M11 - Integration IV

> [!abstract] Summary
> A **double integral** $\iint_Rf(x,y)\,\mathrm dx\,\mathrm dy$ is the limit of $\sum f_i\,\delta S_i$: the volume under the surface $z=f(x,y)$ above the region $R$. When $f\equiv1$, it gives the area of $R$.
>
> You evaluate it as two successive single integrals. **The hard part is always the limits.** Draw the region, choose the strip direction, and read off the limits from the sketch.
>
> Also covered: polar coordinates ($\mathrm dA=r\,\mathrm dr\,\mathrm d\theta$) and triple integrals. This module is booklet-only; James does not cover it.

## Key Concepts
- [[Double Integrals and Change of Order]] · [[Jacobian and Volume Elements]] (MATH2048 extends this to general coordinates)

---

## 1. Rectangular regions (Booklet §3)
$$
\int_{y=c}^{d}\Big(\int_{x=a}^{b}f(x,y)\,\mathrm dx\Big)\mathrm dy
$$
Do the inner integral with the outer variable held **constant**. Then integrate the result. For a rectangle you can swap the order freely, and the limits just swap. If $f=g(x)h(y)$ and the limits are constant, the integral factorises into a product of single integrals (Exercise G).

## 2. Non-rectangular regions (Booklet §4)
If $R$ lies between the curves $y=g_1(x)$ and $y=g_2(x)$ for $x_1\le x\le x_2$:
$$
\iint_Rf\,\mathrm dA=\int_{x_1}^{x_2}\Big(\int_{g_1(x)}^{g_2(x)}f(x,y)\,\mathrm dy\Big)\mathrm dx\qquad\text{(vertical strips)}
$$
If instead $R$ lies between $x=h_1(y)$ and $x=h_2(y)$ for $y_1\le y\le y_2$:
$$
\iint_Rf\,\mathrm dA=\int_{y_1}^{y_2}\Big(\int_{h_1(y)}^{h_2(y)}f\,\mathrm dx\Big)\mathrm dy\qquad\text{(horizontal strips)}
$$
- The **inner limits** may depend on the outer variable.
- The **outer limits** must be constants.

## 3. Changing the order of integration
1. Sketch $R$ from the given limits: draw all four boundary curves.
2. Re-describe $R$ with strips in the other direction.
3. Invert each boundary: for example, $y=\sqrt x$ becomes $x=y^2$.

**Why bother?**
- Sometimes the integral is **only** possible one way. $\int_0^1\!\int_{\sqrt x}^1e^{y^3}\,\mathrm dy\,\mathrm dx$ cannot be done as written. Reversed, it becomes $\int_0^1y^2e^{y^3}\,\mathrm dy=\frac{e-1}3$.
- Sometimes one order is simply shorter. In Exercise D, the order with $\frac1y$ constant inside is easier.

![[m1054_double_integral_regions.png|800]]

## 4. Polar coordinates (Booklet)
With $x=r\cos\theta$ and $y=r\sin\theta$, the area element is the small polar "rectangle" $r\,\mathrm d\theta\times\mathrm dr$:
$$
\iint_Rf\,\mathrm dx\,\mathrm dy=\iint_Rf(r\cos\theta,r\sin\theta)\,r\,\mathrm dr\,\mathrm d\theta
$$
**Don't forget the $r$.** It is the Jacobian $\partial(x,y)/\partial(r,\theta)$. For a curve $r=f(\theta)$, the area it encloses is $\frac12\int f(\theta)^2\,\mathrm d\theta$. For example, the cardioid $r=a(1-\cos\theta)$ encloses $\frac32\pi a^2$.

## 5. Triple integrals
$\iiint_Vf\,\mathrm dx\,\mathrm dy\,\mathrm dz$ is done as three nested integrals. With $f=1$ it gives the volume. With $f=\rho$ it gives the mass, and $\iiint x\,\mathrm dV/V=\bar x$ gives the centroid.

## Method checklist
1. **Sketch the region.** Always.
2. Pick the strip direction that gives the simplest limits and integrand. Each strip should cross the boundary only twice.
3. Inner limits are functions of the outer variable; outer limits are numbers.
4. Is the region circular, or does the integrand contain $x^2+y^2$? Switch to polar and add the factor $r$.
5. If the inner integral is impossible, reverse the order.

## Links
- Parent: [[MATH1054 Mathematics for Engineering and the Environment Hub]] · Solutions: [[MATH1054 M11 Solutions - Integration IV]]
- Prev: [[MATH1054 M10 - Integration III]]
- Next level: MATH2048 [[MATH2048 VC5 - Volume Integrals, the Divergence Theorem and Stokes' Theorem]], [[Jacobian and Volume Elements]]
- Engineering: second moments of area $I=\iint y^2\,\mathrm dA$ ([[Second Moments of Area]])

## Sources
- MATH1054 Module Booklet, Module 11 (Integration IV)
