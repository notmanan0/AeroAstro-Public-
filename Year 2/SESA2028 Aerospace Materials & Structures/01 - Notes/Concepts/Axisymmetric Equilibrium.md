---
title: "Axisymmetric Equilibrium"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
stream: "Structures"
tags: [sesa2028, structures, continuum-mechanics]
status: complete
parent: ["[[SESA2028 S9 - Continuum Mechanics in Cylindrical Coordinates]]"]
---

# Axisymmetric Equilibrium

**What it is:** radial force balance on a small element of an axisymmetric body (a cylinder or disc) whose stresses depend only on $r$.

## Derivation

Take an element between $r$ and $r+dr$, subtending $d\theta$, of unit thickness. The forces in the radial direction are:

- radial stress on the outer face: $(\sigma_r+d\sigma_r)(r+dr)\,d\theta$;
- radial stress on the inner face: $-\sigma_r\,r\,d\theta$;
- hoop stress on the two side faces, each inclined at $d\theta/2$: $-2\sigma_\theta\,dr\sin(d\theta/2)\approx-\sigma_\theta\,dr\,d\theta$;
- body force: $b_r\,r\,dr\,d\theta$.

Summing, dividing by $r\,dr\,d\theta$ and dropping second-order terms gives

$$
\boxed{\frac{d\sigma_r}{dr}+\frac{\sigma_r-\sigma_\theta}{r}+b_r=0.}
$$

## Cases

| Problem | Body force $b_r$ |
|---|---|
| Pressurised thick cylinder ([[Lame Thick-Cylinder Solution]]) | $0$ |
| Spinning disc ([[Spinning Disc Stress]]) | $\rho\omega^2r$ (centrifugal) |

## Why it is not enough on its own

One equation, two unknown stresses ($\sigma_r,\sigma_\theta$): the problem is **statically indeterminate**. Close it with [[Strain Compatibility]] ($\varepsilon_r=du/dr$, $\varepsilon_\theta=u/r$) and Hooke's law. That combination produces the Lamé and spinning-disc solutions.

The $(\sigma_r-\sigma_\theta)/r$ term is purely geometric: because the side faces are not parallel, the hoop stress has a radial component. This is why radial and hoop stresses cannot generally be equal through a thick wall (except at the centre of a solid disc).
