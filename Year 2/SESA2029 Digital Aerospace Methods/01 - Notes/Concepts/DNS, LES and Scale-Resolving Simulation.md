---
title: "DNS, LES and Scale-Resolving Simulation"
module: "SESA2029 Digital Aerospace Methods"
type: concept
stream: "Part A: Computational Fluid Dynamics"
aliases: ["DNS", "LES", "DES", "detached eddy simulation", "large-eddy simulation", "direct numerical simulation", "URANS", "Kolmogorov scale"]
tags: [sesa2029, concept, turbulence]
status: complete
parent_lectures: ["[[SESA2029 A11 - CFD Errors, Verification, Validation and Mesh Quality]]"]
related_concepts: ["[[Reynolds Averaging and the Closure Problem]]", "[[Eddy-Viscosity Turbulence Models]]"]
sources: ["02 - Sources/CFD/All_lectures_as_delivered.pdf (L12)", "02 - Sources/CFD/CFD.txt"]
---

# DNS, LES and Scale-Resolving Simulation

## Definition

> [!note] Definition
> **Scale-resolving methods** compute turbulent eddies directly instead of modelling them all:
> - **DNS** resolves every scale down to the Kolmogorov scale $\eta = (\nu^3/\varepsilon)^{1/4}$;
> - **LES** resolves the large eddies and models the small ones;
> - **hybrid RANS–LES** (e.g. DES) uses RANS in attached boundary layers and LES in separated regions.

## Explanation

- **Cost hierarchy**, from cheapest to most expensive, with reliance on modelling decreasing in the same order: panel/boundary-element → Euler → steady RANS → URANS → DES → LES → DNS.
- **DNS cost**: equilibrium $P\sim U^3/\Lambda = \varepsilon$ gives $\Lambda/\eta\propto Re^{3/4}$. So the points per direction scale as $Re^{3/4}$, the 3D grid as $Re^{9/4}$, and the cost (with time steps) as about $Re^3$. Each 10× in Reynolds number costs about 1000× in compute.
- LES cuts the spectrum in the $-5/3$ inertial range at $k_c$ and models the rest with a subgrid model.
- **URANS** captures large-scale shedding (a Kármán street) but looks laminar. **DES** on a fine grid captures multi-scale wake turbulence. It is increasingly used industrially for stalled configurations and unsteady loads.
- Compute growth (Moore's law, via parallel CPUs and now GPUs) closes the gap slowly, and power consumption is a growing constraint.

## Examples

![[dam_dns_cost_scaling.png|480]]

- Circular-cylinder wake: RANS is steady, URANS is regular shedding, and DES resolves turbulent fine structure ([[Flow Past a Cylinder]]).

## Related

- Parent lectures: [[SESA2029 A11 - CFD Errors, Verification, Validation and Mesh Quality]]
- Related concepts: [[Reynolds Averaging and the Closure Problem]] · [[Eddy-Viscosity Turbulence Models]]

## Sources

- 02 - Sources/CFD/All_lectures_as_delivered.pdf (L12)
- 02 - Sources/CFD/CFD.txt
