---
title: "Axisymmetric Equilibrium"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
stream: "Structures"
tags: [sesa2028, structures, continuum-mechanics]
status: lectured
parent: ["[[SESA2028 S9 - Continuum Mechanics in Cylindrical Coordinates]]"]
---

# Axisymmetric Equilibrium

Radial force balance on a small element of an axisymmetric body (a cylinder or disc) whose stresses depend only on $r$.

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

One equation, two unknown stresses ($\sigma_r,\sigma_\theta$): the problem is statically indeterminate. [[Strain Compatibility]] ($\varepsilon_r=du/dr$, $\varepsilon_\theta=u/r$) and Hooke's law supply the missing relation, and together they produce the Lamé and spinning-disc solutions.

The $(\sigma_r-\sigma_\theta)/r$ term is purely geometric: because the side faces are not parallel, the hoop stress has a radial component. If $\sigma_r=\sigma_\theta$ at every radius, the term vanishes and $d\sigma_r/dr=-b_r$, so with no body force the stress is uniform. That happens in a solid shaft under external pressure $p$ and in a tube with the same pressure $p$ on both surfaces ($B=0$, $\sigma_r=\sigma_\theta=-p$). Otherwise the two stresses differ through the wall; in a spinning disc they are equal only at the centre of a solid disc.

## Related

- Topic: [[SESA2028 S9 - Continuum Mechanics in Cylindrical Coordinates|S9]]
- Topic: [[SESA2028 S11 - Spinning Discs|S11]]
- Concepts: [[Lame Thick-Cylinder Solution]] · [[Spinning Disc Stress]] · [[Strain Compatibility]]
