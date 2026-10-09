---
title: "CFD Boundary Conditions"
module: "SESA2029 Digital Aerospace Methods"
type: concept
stream: "Part A: Computational Fluid Dynamics"
aliases: ["Dirichlet boundary condition", "Neumann boundary condition", "no-slip", "symmetry plane", "pressure outlet", "ghost cells"]
tags: [sesa2029, concept, finite-volume, boundary-conditions]
status: complete
parent_lectures: ["[[SESA2029 A9 - Finite Volume Method]]", "[[SESA2029 A4 - Time Marching - Explicit and Implicit Methods]]"]
related_concepts: ["[[Finite Volume Method]]", "[[Navier-Stokes Equations]]", "[[Boundary Conditions and Rigid Body Modes]]"]
sources: ["02 - Sources/CFD/All_lectures_as_delivered.pdf (L5, L10)", "02 - Sources/CFD/CFD.txt"]
---

# CFD Boundary Conditions

## Definition

> [!note] Definition
> Conditions on the domain boundary that make the discrete problem well posed:
> - **Dirichlet** conditions fix a value (e.g. $T = 1200$ K; $u = 0$);
> - **Neumann** conditions fix a gradient (e.g. adiabatic $\partial T/\partial n = 0$; zero-gradient outflow).
>
> In finite volumes they are imposed through the **face fluxes**, often with **ghost cells** extrapolated from the interior.

## Explanation

| Boundary | Velocity | Other |
|---|---|---|
| Inflow | prescribed (convective flux given) | turbulence quantities specified |
| **No-slip wall** (viscous) | $u = v = w = 0$; no convective flux; normal viscous flux $= 0$ from continuity | wall shear from the gradient |
| **Slip / inviscid wall** | $v_n = 0$; $\partial u_t/\partial n = 0$ | same as symmetry |
| **Symmetry** | normal component $= 0$; normal gradients of the tangential components $= 0$ | zero-gradient scalars |
| **Pressure outlet** | extrapolated | static pressure specified |
| **Viscous free stream** | zero stress | |

- Discretise Neumann conditions with one-sided differences, e.g. $T_N = T_{N-1}$ for an adiabatic wall.
- **Far-field placement matters**: an inviscid far-field boundary behaves like a wall. If it is too close it constrains the flow and changes lift. Test the sensitivity to domain size.
- Symmetry halves a model (e.g. a half-span wing) without constraining the physics, provided the flow really is symmetric.

## Examples

- Heat equation: Dirichlet $T_0 = 1200$ K at the hot skin and Neumann $\partial T/\partial x = 0$ at the insulated inner wall.
- Flat-plate CFD: velocity inlet, no-slip plate, symmetry upstream of the leading edge, pressure outlet, and a zero-stress top boundary.

## Related

- Parent lectures: [[SESA2029 A9 - Finite Volume Method]] · [[SESA2029 A4 - Time Marching - Explicit and Implicit Methods]]
- Related concepts: [[Finite Volume Method]] · [[Navier-Stokes Equations]] · [[Boundary Conditions and Rigid Body Modes]]

## Sources

- 02 - Sources/CFD/All_lectures_as_delivered.pdf (L5, L10)
- 02 - Sources/CFD/CFD.txt
