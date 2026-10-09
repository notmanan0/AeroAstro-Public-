---
title: "SESA1016 T7 - Fluid Properties and Viscosity"
module: "SESA1016 Thermofluids"
type: topic
stream: "Part B: Similarity and Fluid Fundamentals"
order: 7
tags: [sesa1016, fluid-properties, viscosity, newtonian-fluid]
aliases: ["Properties of Fluids"]
date: 2026-09-25
status: complete
parent: ["[[SESA1016 Thermofluids Hub]]"]
prerequisites: ["[[SESA1016 T6 - Dimensional Analysis and Similarity]]"]
next_topics: ["[[SESA1016 T8 - Hydrostatics]]"]
key_concepts: ["[[Newtonian Fluid and Viscosity]]", "[[Reynolds Number]]"]
tutorial_sheets: ["[[SESA1016 Problem Sheet 06 - Fluid Properties and Hydrostatics Solutions]]"]
sources: ["02 - Sources/Lectures/Chapter 7.pdf"]
---

# SESA1016 T7 - Fluid Properties and Viscosity

> [!abstract] Summary
> A fluid cannot sustain a static shear stress: however small the applied shear, it continues deforming. Density measures mass per volume, bulk modulus measures resistance to compression, and viscosity relates shear stress to deformation rate. In a Newtonian fluid the relationship is linear, $\tau=\mu,du/dy$.

## 1. Solid versus fluid

A solid can support a shear stress through a finite deformation. A fluid responds to shear stress with a continuing rate of deformation. Fluid mechanics therefore describes velocity gradients rather than a fixed shear strain.

## 2. Density and specific volume

$$
\rho=\frac{m}{V},\qquad v=\frac1\rho
$$

Liquids are often treated as incompressible because their density varies little under ordinary pressure changes. Gases generally require a thermodynamic state relation.

## 3. Bulk modulus

$$
K=-V\frac{dp}{dV}=\rho\frac{dp}{d\rho}
$$

The minus sign makes $K>0$: increasing pressure decreases volume. A large $K$ means weak compressibility.

## 4. Dynamic viscosity

For simple parallel shear in a Newtonian fluid:

$$
\boxed{\tau_{xy}=\mu\frac{du}{dy}}
$$

- $\mu$: dynamic viscosity, $\mathrm{Pa\,s}$;
- $du/dy$: shear rate, $\mathrm{s^{-1}}$;
- $\tau$: shear stress, Pa.

Viscosity is momentum diffusion: faster molecular layers exchange momentum with slower neighbours.

See [[Newtonian Fluid and Viscosity]].

## 5. Kinematic viscosity

$$
\nu=\frac\mu\rho\qquad[\nu]=\mathrm{m^2/s}
$$

$\mu$ measures resistance to shear; $\nu$ compares momentum diffusion with the fluid's inertia per unit volume. Reynolds number can be written $Re=VL/\nu$.

## 6. Newtonian and non-Newtonian fluids

| Behaviour | $\tau$ versus shear rate | Example |
|---|---|---|
| Newtonian | straight line through origin | air, water, light oils |
| Shear-thinning | effective viscosity decreases | paint, blood |
| Shear-thickening | effective viscosity increases | dense starch suspension |
| Yield-stress | finite stress before flow | toothpaste, some slurries |

The rest of SESA1016 assumes Newtonian fluids unless stated otherwise.

## 7. Temperature dependence

- **Liquids**: viscosity normally decreases as temperature rises because cohesive molecular forces become easier to overcome.
- **Gases**: viscosity normally increases as temperature rises because faster molecules transfer more momentum between layers.

This opposite trend is a common conceptual question.

## 8. Wall shear and no slip

At a stationary solid wall, the adjacent fluid satisfies $u=0$. The wall shear is

$$
\tau_w=\mu\left.\frac{\partial u}{\partial n}\right|_w.
$$

A steep near-wall velocity gradient therefore produces a large friction force.

## Links

- Previous: [[SESA1016 T6 - Dimensional Analysis and Similarity]]
- Concept: [[Newtonian Fluid and Viscosity]]
- Tutorial: [[SESA1016 Problem Sheet 06 - Fluid Properties and Hydrostatics Solutions]]
- Continues in CFD: [[SESA2029 A7 - Governing Equations - Euler and Navier-Stokes]] · [[Newtonian Fluid and Strain-Rate Tensor]]
- Next: [[SESA1016 T8 - Hydrostatics]]

## Sources

- `02 - Sources/Lectures/Chapter 7.pdf`, §§7.1-7.5.
