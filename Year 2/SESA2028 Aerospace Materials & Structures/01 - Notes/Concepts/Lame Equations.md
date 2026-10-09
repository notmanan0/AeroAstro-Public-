---
title: "Lame Equations"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
stream: "Structures"
tags: [sesa2028, structures, thick-cylinders]
status: complete
parent: ["[[SESA2028 S10 - Thick Cylinders and Shrink Fits]]"]
---

# Lame Equations

**What it is:** the general solution of the axisymmetric elasticity problem with no body force. It is the starting point for every thick-cylinder and shrink-fit question. For how to *use* the result, see [[Lame Thick-Cylinder Solution]].

## Derivation (plane stress, $\sigma_z=0$)

1. **Equilibrium** ([[Axisymmetric Equilibrium]]): $\dfrac{d\sigma_r}{dr}+\dfrac{\sigma_r-\sigma_\theta}{r}=0$.
2. **Compatibility** ([[Polar Strain-Displacement Relations]]): $\varepsilon_r=\dfrac{du}{dr}$, $\varepsilon_\theta=\dfrac ur$.
3. **Hooke's law:**
$$
\sigma_r=\frac{E}{1-\nu^2}(\varepsilon_r+\nu\varepsilon_\theta),\qquad
\sigma_\theta=\frac{E}{1-\nu^2}(\varepsilon_\theta+\nu\varepsilon_r).
$$
4. Substituting into equilibrium gives the displacement equation
$$
\frac{d^2u}{dr^2}+\frac1r\frac{du}{dr}-\frac{u}{r^2}=0
\quad\Longleftrightarrow\quad
\frac{d}{dr}\left[\frac1r\frac{d}{dr}(ru)\right]=0,
$$
so $u=C_1r+\dfrac{C_2}{r}$.
5. Back into Hooke's law:
$$
\boxed{\sigma_r=A-\frac{B}{r^2},\qquad \sigma_\theta=A+\frac{B}{r^2}},\qquad A=\frac{EC_1}{1-\nu},\ B=\frac{EC_2}{1+\nu}.
$$

## Properties worth remembering

- $\sigma_r+\sigma_\theta=2A$ is **constant** through the wall, so the axial strain is uniform and plane sections stay plane.
- The two constants come from two boundary conditions: $\sigma_r=-p$ on each loaded surface (pressure is compressive), or $\sigma_r=0$ on a free surface.
- For a **solid** body the $B/r^2$ term must vanish (finite stress at $r=0$).
- With closed ends, the axial stress from end thrust is $\sigma_z=\dfrac{p_ia^2-p_ob^2}{b^2-a^2}=A$.
