---
title: "SESA2028 S10 - Thick Cylinders and Shrink Fits"
module: "SESA2028 Aerospace Materials & Structures"
type: topic
stream: "Structures"
order: 10
tags: [sesa2028, structures, thick-cylinder, shrink-fit]
status: complete
parent: ["[[SESA2028 Aerospace Materials & Structures Hub]]"]
prerequisites: ["[[SESA2028 S9 - Continuum Mechanics in Cylindrical Coordinates]]"]
next_topics: ["[[SESA2028 S11 - Spinning Discs]]"]
key_concepts: ["[[Lame Equations]]", "[[Shrink Fit]]", "[[Compound Cylinder]]"]
tutorial_sheets: ["[[SESA2028 Structures Tutorial 5 - Continuum Mechanics Solutions]]"]
sources: ["02 - Sources/Structures Lectures/SL11 - Continuum Mechanics 2 - Thick walled cylinders and shrink fit.pdf", "02 - Sources/Structures Lectures/SL22 - Continuum Mechanics 4 - Thick Walled Cylinders.pdf", "02 - Sources/Structures Lectures/SL23 - Continuum Mechanics 5 - Shrink Fit Assembly.pdf", "02 - Sources/Structures Lectures/Structures Additional session - thick wall cylinders.pdf"]
---

# SESA2028 S10 - Thick Cylinders and Shrink Fits

> [!abstract] Summary
> A thick cylinder has a radial stress gradient that thin-wall pressure-vessel theory cannot represent. Lamé's solution separates a uniform part $A$ from a curvature-driven part $B/r^2$. Shrink fitting superposes a deliberately created residual stress field on the service-pressure field.

## 1. Lamé equations

For inner radius $r_i$, outer radius $r_o$, internal pressure $p_i$ and external pressure $p_o$,

$$
\sigma_{rr}=A-\frac{B}{r^2},\qquad
\sigma_{\theta\theta}=A+\frac{B}{r^2},
$$

where

$$
A=\frac{p_ir_i^2-p_or_o^2}{r_o^2-r_i^2},\qquad
B=\frac{(p_i-p_o)r_i^2r_o^2}{r_o^2-r_i^2}.
$$

The radial boundary conditions are

$$
\sigma_{rr}(r_i)=-p_i,\qquad
\sigma_{rr}(r_o)=-p_o.
$$

For attached closed ends,

$$
\sigma_{zz}=A.
$$

![[Figures/structures_thick_cylinder_lame_stress.png]]

## 2. Displacement

For an axisymmetric elastic cylinder with constant $\sigma_{zz}$,

$$
u(r)=\frac{1}{E}\left(\big[(1-\nu)A-\nu\sigma_{zz}\big]r
+(1+\nu)\frac Br\right).
$$

For open ends, $\sigma_{zz}=0$; for attached closed ends, $\sigma_{zz}=A$, so the coefficient of $Ar$ becomes $1-2\nu$. If a plane-strain assumption is specified, use the corresponding constitutive relation rather than silently recycling this expression.

The diameter change at a surface is $\Delta D=2u$.

## 3. Thin-wall limit

When $t=r_o-r_i\ll r_i$, the inner and outer hoop stresses become nearly equal and reduce to

$$
\sigma_\theta\approx\frac{pr}{t}.
$$

The thick-cylinder solution is essential when the wall is not small relative to the radius or when both internal and external pressure are significant.

## 4. Shrink fit

An interference fit is modelled as an unknown contact pressure $p_c$ acting:

- externally on the inner tube;
- internally on the outer tube.

Compute each tube's Lamé field and radial displacement at the mating radius $r_m$. Compatibility is

$$
\delta_r=u_{outer}(r_m)-u_{inner}(r_m),
$$

with signs handled so the original radial interference is removed by the assembly deformations. Solve this equation for $p_c$.

![[Figures/structures_shrink_fit_residual_stress.png]]

## 5. Superposition in service

Linear elasticity permits

$$
\boldsymbol\sigma_{total}
=\boldsymbol\sigma_{shrink}
+\boldsymbol\sigma_{pressure}.
$$

The shrink fit introduces compressive hoop stress in the inner tube and tensile hoop stress in the outer tube. Correctly chosen, it reduces the peak tensile hoop stress at the bore under service pressure and uses the material more uniformly.

## 6. Design checks

- radial stress is continuous at a perfectly bonded or contacting interface;
- hoop stress can jump because the material domain or Lamé constants change;
- check both assembly and service states against yield;
- state whether the quoted interference is radial or diametral;
- use consistent pressure and tensile-positive stress signs.

## Year 1 foundation
- Thin-walled cylinders ($\sigma_{hoop} = pR/t$) in [[FEEG1002 B1 - Stress in Multiple Dimensions and Thin-Walled Pressure Vessels]]. The Lamé solution tends to this as $t/R\to0$. Stress-state checks use [[FEEG1002 B6 - Yield Criteria]].
