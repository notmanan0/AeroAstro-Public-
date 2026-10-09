---
title: "Prandtl Boundary-Layer Equations"
module: "SESA3043 Advanced Aeronautics"
type: concept
stream: "Chapter 1: Conservation Laws"
aliases: ["boundary-layer equations", "BL equations", "Prandtl BL equations"]
tags: [sesa3043, concept, boundary-layer]
status: complete
parent_lectures: ["[[SESA3043 1.4 - Two-Dimensional Incompressible Boundary Layers]]"]
related_concepts: ["[[Order-of-Magnitude Analysis]]", "[[Displacement and Momentum Thickness]]", "[[Boundary Layer Separation]]"]
sources: ["02 - Sources/Lectures/CH1-4 2D Incompressible BL(1).pdf"]
---

# Prandtl Boundary-Layer Equations

## Definition

> [!note] Definition
> Steady, 2-D, incompressible, thin layer ($\delta\ll L$):
>
> $$\frac{\partial u}{\partial x}+\frac{\partial v}{\partial y}=0,\qquad u\frac{\partial u}{\partial x}+v\frac{\partial u}{\partial y}=U_e\frac{\mathrm dU_e}{\mathrm dx}+\nu\frac{\partial^2u}{\partial y^2},\qquad\frac{\partial p}{\partial y}=0.$$
>
> Boundary conditions: $u=v=0$ at $y=0$; $u\to U_e(x)$ at the edge.

## What was dropped, and why

- $\nu\,\partial^2u/\partial x^2$: smaller than $\nu\,\partial^2u/\partial y^2$ by $(\delta/L)^2=Re^{-1}$.
- the whole $y$-momentum equation except $\partial p/\partial y$: every term is $O(Re^{-1})$, so $\Delta p$ across the layer $\sim\rho U_e^2Re^{-1}$.

## Key points

- $\delta/L\sim Re^{-1/2}$; Blasius gives $\delta_{99}=4.91\,x\,Re_x^{-1/2}$.
- The pressure is imposed by the outer potential flow: $-\frac1\rho\frac{\mathrm dp}{\mathrm dx}=U_e\frac{\mathrm dU_e}{\mathrm dx}$.
- **Parabolic**: march downstream from an inflow profile; far cheaper than elliptic N–S.
- Fails at low $Re$, at the leading-edge tip, and at separation.

![[aa_bl_order_of_magnitude_derivation.png|700]]

## Related

- [[SESA3043 1.4 - Two-Dimensional Incompressible Boundary Layers]] · [[Order-of-Magnitude Analysis]] · [[SESA2022 T2 - Boundary Layers]] · [[Shooting Method and the Blasius Solution]]
