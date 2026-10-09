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

## Definition

> [!note] Definition
> $\iint_Rf\,\mathrm dA=\lim\sum f_i\,\delta S_i$: the volume under $z=f(x,y)$ above the region $R$. It is evaluated as repeated single integrals, e.g.
>
> $$\iint_Rf\,\mathrm dA=\int_{x_1}^{x_2}\!\!\int_{g_1(x)}^{g_2(x)}f\,\mathrm dy\,\mathrm dx$$

## Explanation
- **Always sketch $R$.** The inner limits may depend on the outer variable; the outer limits must be constants.
- **Changing the order**: re-describe $R$ with strips in the other direction, and invert the boundary curves. Sometimes only one order is integrable, e.g. $\int e^{y^3}\,\mathrm dy$ is impossible until the order is reversed.
- **Polar coordinates**: $\mathrm dA=r\,\mathrm dr\,\mathrm d\theta$. The $r$ is the Jacobian ([[Jacobian and Volume Elements]]).
- $\iint_R1\,\mathrm dA$ is the area of $R$; triple integrals give volume and mass.

## Examples
- $\iint_\Delta\frac xy\,\mathrm dA=\frac34-\frac12\ln2$, done both ways (M11 Ex D).
- $\int_0^1\!\int_{\sqrt x}^1e^{y^3}\,\mathrm dy\,\mathrm dx=\frac{e-1}3$ after reversing the order (Ex E).
- The cardioid $r=a(1-\cos\theta)$ has area $\frac32\pi a^2$ (Ex F).

## Related
- Topics: [[MATH1054 M11 - Integration IV]]
- Concepts: [[Jacobian and Volume Elements]] · [[Centroids and Solids of Revolution]] · [[Second Moments of Area]]

## Sources
- MATH1054 Module Booklet, Module 11 (booklet-only topic)
