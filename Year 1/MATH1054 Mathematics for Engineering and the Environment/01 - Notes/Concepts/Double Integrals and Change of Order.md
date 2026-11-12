---
title: "Double Integrals and Change of Order"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 1: Calculus"
aliases: ["Double integral", "Repeated integral", "Change of order of integration", "Polar area element"]
tags: [math1054, concept, multiple-integrals]
status: complete
parent_lectures: ["[[MATH1054 M11 - Integration IV]]"]
related_concepts: ["[[Jacobian and Volume Elements]]", "[[Centroids and Solids of Revolution]]", "[[Second Moments of Area]]"]
sources: ["MATH1054 Module Booklet, Module 11 (booklet-only topic)"]
---

# Double Integrals and Change of Order

A double integral $\iint_R f\,\mathrm dS$ is the limit of $\sum f_i\,\delta S_i$ over small elements of a plane region $R$: the volume under $z=f(x,y)$ above $R$ when $f\geq0$, and the area of $R$ when $f=1$. It is evaluated as an iterated (repeated) integral, two single integrals done in turn.

Adding the elements column by column gives

$$
\iint_R f\,\mathrm dS=\int_{x_1}^{x_2}\Big(\int_{g_1(x)}^{g_2(x)}f(x,y)\,\mathrm dy\Big)\mathrm dx ,
$$

where $R$ lies between the lower curve $y=g_1(x)$ and the upper curve $y=g_2(x)$ for $x_1\leq x\leq x_2$. The inner integral, with $x$ held constant, is the area of the cross-section of the solid at that $x$; multiplying by $\mathrm dx$ gives a thin slice, and the outer integral adds the slices. Adding row by row instead gives $\int_{y_1}^{y_2}\!\int_{h_1(y)}^{h_2(y)}f\,\mathrm dx\,\mathrm dy$, with the same boundary curves solved for $x$. For continuous $f$ both orders add the same elements and give the same value. The inner limits may depend on the outer variable; the outer limits must be constants.

Changing the order means describing the same region with strips in the other direction: sketch $R$ from all four limits, find where a strip of the new kind enters and leaves $R$, and invert the boundary curves. If a strip crosses the boundary more than twice, $R$ has to be split. One order is often far easier than the other, and sometimes it is the only one possible. $\int_0^1\!\int_{\sqrt x}^1e^{y^3}\,\mathrm dy\,\mathrm dx$ cannot be done as written, since $e^{y^3}$ has no elementary antiderivative. The region is also $0\leq x\leq y^2$, $0\leq y\leq1$, so

$$
\int_0^1\!\!\int_0^{y^2}e^{y^3}\,\mathrm dx\,\mathrm dy=\int_0^1y^2e^{y^3}\,\mathrm dy=\Big[\tfrac13e^{y^3}\Big]_0^1=\tfrac13(e-1)\approx0.5728 .
$$

Over the triangle with vertices $(1,1)$, $(1,2)$, $(2,2)$, $\iint\frac xy\,\mathrm dS=\tfrac34-\tfrac12\ln2\approx0.4034$ both ways, but the order with $x$ inner keeps $\frac1y$ as a constant factor and avoids integration by parts.

In polar coordinates the element between radii $r$, $r+\delta r$ and angles $\theta$, $\theta+\delta\theta$ has area $\tfrac12(r+\delta r)^2\delta\theta-\tfrac12r^2\delta\theta=r\,\delta r\,\delta\theta+\tfrac12\delta r^2\,\delta\theta$, and dropping the higher-order term gives $\mathrm dS=r\,\mathrm dr\,\mathrm d\theta$. The $r$ is the Jacobian $\partial(x,y)/\partial(r,\theta)$ ([[Jacobian and Volume Elements]]). The area inside $r=f(\theta)$ is then $\tfrac12\int f(\theta)^2\,\mathrm d\theta$; for the cardioid $r=a(1-\cos\theta)$ it is $\tfrac32\pi a^2$. With $f=\rho$, $x\rho$ or $y^2\rho$ the same integrals give the mass, centre of mass and moment of inertia of a lamina, and triple integrals extend all of this to solids.

The common trap is to swap the differentials and carry the old limits across unchanged. In $\int_0^1\!\int_0^{1-x}xy^2\,\mathrm dy\,\mathrm dx=\tfrac1{60}$, the reversed form is $\int_0^1\!\int_0^{1-y}xy^2\,\mathrm dx\,\mathrm dy$, read from the triangle; writing $\int_0^{1-x}\!\int_0^1\dots\,\mathrm dx\,\mathrm dy$ leaves an outer limit containing a variable that has already been integrated out. The second trap is dropping the $r$ in polar coordinates.

## Related

- Topics: [[MATH1054 M11 - Integration IV]] · [[MATH2048 VC5 - Volume Integrals, the Divergence Theorem and Stokes' Theorem]]
- Concepts: [[Jacobian and Volume Elements]] · [[Centroids and Solids of Revolution]] · [[Second Moments of Area]]
- Sources: MATH1054 Module Booklet, Module 11 (booklet-only topic; not in James)
