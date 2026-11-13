---
title: "Spinning Disc Stress"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
tags: [sesa2028, structures, spinning-discs]
status: written-ahead
---

# Spinning Disc Stress

Rotation creates the radial body force $\rho\omega^2r$. Equilibrium is

$$
\frac{d\sigma_r}{dr}+\frac{\sigma_r-\sigma_\theta}{r}
+\rho\omega^2r=0.
$$

Use an axisymmetric radial displacement $u(r)$, express strains as

$$
\varepsilon_r=\frac{du}{dr},\qquad
\varepsilon_\theta=\frac ur,
$$

and combine them with the appropriate plane-stress constitutive law. For a solid disc, reject any (1/r) displacement term because the centre must remain finite. At a free outer radius, impose $\sigma_r=0$.

![[structures_spinning_disc_stress.png|700]]

The result, for a thin uniform disc in plane stress, is

$$
\sigma_r=A-\frac{B}{r^2}-\frac{3+\nu}{8}\rho\omega^2r^2,\qquad
\sigma_\theta=A+\frac{B}{r^2}-\frac{1+3\nu}{8}\rho\omega^2r^2 .
$$

The hoop stress is tensile throughout a uniform solid disc and largest at the centre, where both stresses equal $\tfrac{3+\nu}{8}\rho\omega^2r_o^2$. A central hole with a free edge raises the peak to the bore hoop stress $\tfrac{\rho\omega^2}{4}[(3+\nu)r_o^2+(1-\nu)r_i^2]$, which tends to twice the solid-disc value as the hole shrinks: even a pinhole doubles it. The topic was not lectured in 2025–26.

See [[SESA2028 S11 - Spinning Discs]].

Related (SESA2028 materials): [[FEEG2005 Exam 2022-23 Solutions|2022-23 MQ1]] (disc bore vs rim crack sites) · [[Paris Law]]

## Related

- Topic: [[SESA2028 M2 - Fatigue - Fracture Surfaces, Mechanisms and Lifing|M2]]
- Topic: [[SESA2028 M8 - High Temperature Materials - Creep, Oxidation and Superalloys|M8]]
- Topic: [[SESA2028 S11 - Spinning Discs|S11]]
- Concepts: [[Paris Law]]
- Elsewhere: [[FEEG2005 Exam 2022-23 Solutions]]
