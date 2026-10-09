---
title: "SESA1016 T9 - Describing Flow and the Material Derivative"
module: "SESA1016 Thermofluids"
type: topic
stream: "Part C: Fluid Motion and Inviscid Flow"
order: 9
tags: [sesa1016, flow-kinematics, material-derivative, streamlines]
aliases: ["Describing Flow"]
date: 2026-09-25
status: complete
parent: ["[[SESA1016 Thermofluids Hub]]"]
prerequisites: ["[[SESA1016 T8 - Hydrostatics]]"]
next_topics: ["[[SESA1016 T10 - Euler and Bernoulli Equations]]"]
key_concepts: ["[[Material Derivative]]", "[[Streamline, Pathline and Streakline]]"]
tutorial_sheets: ["[[SESA1016 Problem Sheet 07 - Describing Flow and Euler Equation Solutions]]"]
sources: ["02 - Sources/Lectures/Chapter 9.pdf"]
---

# SESA1016 T9 - Describing Flow and the Material Derivative

> [!abstract] Summary
> The Lagrangian viewpoint follows individual fluid particles; the Eulerian viewpoint measures fields at fixed locations. The material derivative connects them: a particle experiences both local time variation and change caused by moving through a spatial gradient. Streamlines, pathlines and streaklines coincide only in steady flow.

## 1. Fluid particle and field descriptions

- **Lagrangian**: track $\mathbf x(t)$, $\mathbf V(t)$ and $T(t)$ for a tagged particle.
- **Eulerian**: specify $\mathbf V(\mathbf x,t)$, $p(\mathbf x,t)$ and $T(\mathbf x,t)$ throughout space.

Engineering analysis usually uses Eulerian fields because devices occupy fixed regions.

## 2. Material derivative

For a scalar field $\phi(\mathbf x,t)$ sampled by a moving particle:

$$
\boxed{\frac{D\phi}{Dt}=\frac{\partial\phi}{\partial t}+\mathbf V\cdot\nabla\phi}
$$

- $\partial\phi/\partial t$: **local** change at a fixed point;
- $\mathbf V\cdot\nabla\phi$: **convective** change from motion through a nonuniform field.

For velocity itself:

$$
\boxed{\mathbf a=\frac{D\mathbf V}{Dt}=\frac{\partial\mathbf V}{\partial t}+(\mathbf V\cdot\nabla)\mathbf V}.
$$

![[tf_flow_kinematics.png|700]]

### Steady does not mean zero acceleration

If $\partial\mathbf V/\partial t=0$ but velocity varies spatially, convective acceleration remains. Fluid accelerating through a steady nozzle is the standard example.

## 3. Flow visualisations

See [[Streamline, Pathline and Streakline]].

- **Streamline**: everywhere tangent to instantaneous velocity; in 2D $dy/dx=v/u$.
- **Pathline**: trajectory of one tagged particle.
- **Streakline**: current location of all particles that passed through a fixed release point.
- **Timeline**: particles marked simultaneously along a line.

In steady flow, streamline = pathline = streakline. In unsteady flow they need not agree.

## 4. Streamtubes

A streamtube is bounded by streamlines. No velocity crosses its side surface, so mass enters and leaves only through its end sections. It behaves like an imaginary duct and supports quasi-one-dimensional analysis.

## 5. Flow classifications

| Classification | Distinction |
|---|---|
| steady / unsteady | field at a point independent/dependent on time |
| uniform / nonuniform | no spatial variation / spatial variation |
| internal / external | wall-confined / flow around a body |
| 1D / 2D / 3D | number of coordinates needed |
| laminar / turbulent | ordered layers / fluctuating multi-scale motion |
| viscous / inviscid | shear important / negligible in modelled region |
| incompressible / compressible | density variation negligible / important |

These are modelling labels, not absolute fluid properties. The same air can be treated as incompressible at low Mach number and compressible at high Mach number.

## 6. Mach number

For a calorically perfect gas:

$$
a=\sqrt{\gamma RT},\qquad Ma=\frac Va.
$$

Density changes due to motion are often modest below $Ma\approx0.3$, but temperature/pressure variation may still matter for other reasons.

## Links

- Concepts: [[Material Derivative]] · [[Streamline, Pathline and Streakline]]
- Tutorial: [[SESA1016 Problem Sheet 07 - Describing Flow and Euler Equation Solutions]]
- Continues in CFD: [[SESA2029 A7 - Governing Equations - Euler and Navier-Stokes]]
- Next: [[SESA1016 T10 - Euler and Bernoulli Equations]]

## Sources

- `02 - Sources/Lectures/Chapter 9.pdf`, §§9.1-9.6.
