---
title: "SESA2028 S11 - Spinning Discs"
module: "SESA2028 Aerospace Materials & Structures"
type: topic
stream: "Structures"
order: 11
tags: [sesa2028, structures, spinning-disc, rotating]
status: complete
parent: ["[[SESA2028 Aerospace Materials & Structures Hub]]"]
prerequisites: ["[[SESA2028 S9 - Continuum Mechanics in Cylindrical Coordinates]]"]
key_concepts: ["[[Spinning Disc Stress]]", "[[Axisymmetric Equilibrium]]"]
sources: ["02 - Sources/Structures Lectures/SL24 - Continuum Mechanics 6 - Spinning Discs.pdf"]
---

# SESA2028 S11 - Spinning Discs

> [!abstract] Summary
> Rotation creates a distributed radial body force $\rho\omega^2r$. In a solid disc, radial and hoop stress are equal at the centre, radial stress falls to zero at the free rim, and hoop stress remains tensile there.

## 1. Equilibrium with rotation

For a thin axisymmetric disc of constant thickness,

$$
\frac{d\sigma_{rr}}{dr}+\frac{\sigma_{rr}-\sigma_{\theta\theta}}r+\rho\omega^2r=0.
$$

The body-force term grows with radius, but the inner material must transmit the centrifugal loading of everything outside it.

## 2. Uniform solid disc

With outer radius $R$ and a traction-free rim,

$$
\sigma_{rr}=\frac{3+\nu}{8}\rho\omega^2(R^2-r^2),
$$

$$
\sigma_{\theta\theta}=\frac{3+\nu}{8}\rho\omega^2
\left[R^2-\frac{1+3\nu}{3+\nu}r^2\right].
$$

At the centre,

$$
\sigma_{rr}(0)=\sigma_{\theta\theta}(0)
=\frac{3+\nu}{8}\rho\omega^2R^2.
$$

At the rim,

$$
\sigma_{rr}(R)=0,\qquad
\sigma_{\theta\theta}(R)=\frac{1-\nu}{4}\rho\omega^2R^2.
$$

![[Figures/structures_spinning_disc_stress.png]]

## 3. Annular and variable-thickness discs

A central bore changes the admissible displacement solution from the solid-disc case because the $C/r$ term no longer has to vanish at $r=0$. Apply radial traction boundary conditions at both radii.

For a variable-thickness disc, equilibrium includes the thickness distribution $t(r)$:

$$
\frac{d}{dr}[t(r)r\sigma_{rr}]-t(r)\sigma_{\theta\theta}
+\rho\omega^2r^2t(r)=0.
$$

This is why turbine discs are profiled rather than made as uniform plates: geometry can redistribute stress toward a more efficient field.

## 4. Scaling

All elastic rotational stresses scale as

$$
\sigma\propto\rho\omega^2R^2.
$$

Therefore:

- doubling speed quadruples stress;
- doubling radius quadruples stress at the same speed;
- lower density directly reduces stress;
- Poisson's ratio changes the distribution but not the dominant scaling.

## 5. Exam checks

1. Include the body-force term.
2. Enforce regularity at $r=0$ for a solid disc.
3. Apply $\sigma_{rr}=0$ at a free rim.
4. Confirm $\sigma_{rr}=\sigma_{\theta\theta}$ at the centre.
5. State whether the disc is treated as plane stress or plane strain.

## Year 1 foundation
- Centripetal acceleration $\omega^2r$ in [[FEEG1002 D2 - Curvilinear Motion]] and [[FEEG1002 D7 - Kinematics of Rigid Bodies]] supplies the body force $\rho\omega^2r$. The stress–strain relations are those of [[FEEG1002 B3 - Generalised Hooke's Law]].
