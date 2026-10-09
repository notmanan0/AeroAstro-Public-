---
title: "SESA2028 S9 - Continuum Mechanics in Cylindrical Coordinates"
module: "SESA2028 Aerospace Materials & Structures"
type: topic
stream: "Structures"
order: 9
tags: [sesa2028, structures, continuum-mechanics, cylindrical-coordinates]
status: complete
parent: ["[[SESA2028 Aerospace Materials & Structures Hub]]"]
prerequisites: ["[[SESA2028 S2 - Beam Deflection and Bending Design]]"]
next_topics: ["[[SESA2028 S10 - Thick Cylinders and Shrink Fits]]"]
key_concepts: ["[[Polar Strain-Displacement Relations]]", "[[Axisymmetric Equilibrium]]", "[[Strain Compatibility]]"]
sources: ["02 - Sources/Structures Lectures/SL10 - Continuum Mechanics 1 - Polar coords and compatibility equations.pdf", "02 - Sources/Structures Lectures/SL19 - Continuum Mechanics 1 - Review.pdf", "02 - Sources/Structures Lectures/SL20 - Continuum Mechanics 2 - Cylindrical Coords.pdf", "02 - Sources/Structures Lectures/SL21 - Continuum Mechanics 3 - Strain Compatibility.pdf"]
---

# SESA2028 S9 - Continuum Mechanics in Cylindrical Coordinates

> [!abstract] Summary
> Cylinders and discs are simplest in $(r,\theta,z)$ coordinates. Geometry creates terms such as $u_r/r$ and $(\sigma_{rr}-\sigma_{\theta\theta})/r$ that have no Cartesian analogue; leaving them out destroys compatibility or equilibrium.

## 1. Displacement and strain

For radial and circumferential displacements $u(r,\theta)$ and $v(r,\theta)$,

$$
\varepsilon_{rr}=\frac{\partial u}{\partial r},
$$

$$
\varepsilon_{\theta\theta}=\frac{u}{r}+\frac1r\frac{\partial v}{\partial\theta},
$$

$$
\gamma_{r\theta}=\frac1r\frac{\partial u}{\partial\theta}
+\frac{\partial v}{\partial r}-\frac vr.
$$

For axisymmetric radial deformation, $v=0$ and $\partial/\partial\theta=0$, so

$$
\varepsilon_{rr}=\frac{du}{dr},\qquad
\varepsilon_{\theta\theta}=\frac ur,\qquad
\gamma_{r\theta}=0.
$$

## 2. Axisymmetric equilibrium

For no radial body force,

$$
\frac{d\sigma_{rr}}{dr}+\frac{\sigma_{rr}-\sigma_{\theta\theta}}r=0.
$$

The second term represents the change in direction of radial tractions around a curved differential element.

## 3. Elastic constitutive relation

For plane stress,

$$
\varepsilon_{rr}=\frac1E(\sigma_{rr}-\nu\sigma_{\theta\theta}),\qquad
\varepsilon_{\theta\theta}=\frac1E(\sigma_{\theta\theta}-\nu\sigma_{rr}).
$$

For a long closed cylinder, the longitudinal stress $\sigma_{zz}$ must be included:

$$
\varepsilon_{rr}=\frac1E[\sigma_{rr}-\nu(\sigma_{\theta\theta}+\sigma_{zz})],
$$

$$
\varepsilon_{\theta\theta}=\frac1E[\sigma_{\theta\theta}-\nu(\sigma_{rr}+\sigma_{zz})].
$$

## 4. Compatibility

In the axisymmetric case, eliminating $u$ gives

$$
\frac{d\varepsilon_{\theta\theta}}{dr}
=\frac{\varepsilon_{rr}-\varepsilon_{\theta\theta}}r.
$$

Compatibility ensures that a proposed strain field comes from one continuous displacement field. Equilibrium alone cannot do this.

## 5. Solution pattern

Combining equilibrium, compatibility and isotropic elasticity produces

$$
u(r)=C_1r+\frac{C_2}{r},
$$

and therefore the Lamé stress form

$$
\sigma_{rr}=A-\frac{B}{r^2},\qquad
\sigma_{\theta\theta}=A+\frac{B}{r^2}.
$$

The constants come from traction boundary conditions. This same pattern underlies thick cylinders and each tube in a shrink-fit assembly.

## 6. Sign convention

Pressure $p>0$ acts as a compressive radial traction, so the boundary condition is

$$
\sigma_{rr}=-p.
$$

Confusing pressure magnitude with stress sign is the most common error in this part of the course.

## Year 1 foundation
- Cartesian stress and strain tensors, generalised Hooke's law and thermal strain: [[FEEG1002 B1 - Stress in Multiple Dimensions and Thin-Walled Pressure Vessels]], [[FEEG1002 B2 - Strain in Multiple Dimensions and Thermal Strain]], [[FEEG1002 B3 - Generalised Hooke's Law]].
