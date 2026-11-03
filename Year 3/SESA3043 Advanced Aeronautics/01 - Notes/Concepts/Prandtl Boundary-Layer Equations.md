---
title: "Prandtl Boundary-Layer Equations"
module: "SESA3043 Advanced Aeronautics"
type: concept
stream: "Chapter 1: Conservation Laws"
aliases: ["boundary-layer equations", "BL equations", "Prandtl BL equations", "2-D BL equation", "reduced BL equation", "Prandtl's thin boundary layer theory", "boundary-layer approximation"]
tags: [sesa3043, concept, boundary-layer]
status: complete
parent_lectures: ["[[SESA3043 1.4 - Two-Dimensional Incompressible Boundary Layers]]"]
related_concepts: ["[[Order-of-Magnitude Analysis]]", "[[Displacement and Momentum Thickness]]", "[[Boundary Layer Separation]]"]
sources: ["02 - Sources/Lectures/CH1-4 2D Incompressible BL(1).pdf"]
---

# Prandtl Boundary-Layer Equations

For steady, two-dimensional, incompressible flow in a thin layer ($\delta\ll L$), the Navier–Stokes equations reduce to

$$\frac{\partial u}{\partial x}+\frac{\partial v}{\partial y}=0,\qquad u\frac{\partial u}{\partial x}+v\frac{\partial u}{\partial y}=U_e\frac{\mathrm dU_e}{\mathrm dx}+\nu\frac{\partial^2u}{\partial y^2},\qquad\frac{\partial p}{\partial y}=0,$$

with $u=v=0$ at $y=0$ and $u\to U_e(x)$ at the edge of the layer.

Two things are thrown away. The streamwise diffusion $\nu\,\partial^2u/\partial x^2$ is smaller than $\nu\,\partial^2u/\partial y^2$ by $(\delta/L)^2=Re^{-1}$. And every term in the $y$-momentum equation is $O(Re^{-1})$ apart from $\partial p/\partial y$, so the pressure change across the layer is only of order $\rho U_e^2Re^{-1}$. The pressure is therefore imposed from outside by the potential flow, $-\frac1\rho\frac{\mathrm dp}{\mathrm dx}=U_e\frac{\mathrm dU_e}{\mathrm dx}$, and the layer thickness scales as $\delta/L\sim Re^{-1/2}$ (Blasius gives $\delta_{99}=4.91\,x\,Re_x^{-1/2}$).

The equations are parabolic, so you can march downstream from an inflow profile, which is far cheaper than solving the elliptic Navier–Stokes equations. They break down at low Reynolds number, at the very tip of the leading edge, and at separation.

![[aa_bl_order_of_magnitude_derivation.png|700]]

## Related

- [[SESA3043 1.4 - Two-Dimensional Incompressible Boundary Layers]] · [[Order-of-Magnitude Analysis]] · [[SESA2022 T2 - Boundary Layers]] · [[Shooting Method and the Blasius Solution]]
