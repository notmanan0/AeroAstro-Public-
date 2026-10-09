---
title: "Wedge and Corner Flows"
module: "SESA3043 Advanced Aeronautics"
type: concept
stream: "Chapter 1: Conservation Laws"
aliases: ["flow over a wedge", "Phi = -k z^(m+1)", "Falkner-Skan edge velocity"]
tags: [sesa3043, concept, potential-flow, wedge]
status: complete
parent_lectures: ["[[SESA3043 1.3 - Complex Potential, Wedge Flows and Unsteady Bernoulli]]"]
related_concepts: ["[[Complex Velocity Potential]]", "[[Prandtl Boundary-Layer Equations]]"]
sources: ["02 - Sources/Lectures/CH1-3 Potential Flow.pdf"]
---

# Wedge and Corner Flows

## Definition

> [!note] Definition
> $\Phi=-kz^{m+1}$ gives $\psi=-kr^{m+1}\sin[(m+1)\theta]$. The walls $\psi=0$ are at $\theta=\pm\pi/(m+1)$, enclosing a wedge of angle
>
> $$\beta\pi=\frac{2m\pi}{m+1},\qquad\beta=\frac{2m}{m+1}.$$

## The family

| $m$ | Flow |
|---|---|
| 0 | uniform flow along a semi-infinite plate |
| $0<m<1$ | flow past a wedge of angle $\beta\pi$ |
| 1 | stagnation flow on a wall (Hiemenz) |
| $m>1$ | flow into a concave corner of angle $(2-\beta)\pi$ |
| $m<0$ | flow round a convex corner (one half used) |

## Wall velocity

$U_e(s)=k(m+1)s^m$, $\mathrm dU_e/\mathrm ds=mU_e/s$, $\mathrm dp/\mathrm ds=-\rho mU_e^2/s$: favourable for wedges ($m>0$), adverse for convex corners ($m<0$). This is the **Falkner–Skan** edge velocity for similar boundary layers.

![[aa_wedge_flow_family.png|700]]

## Related

- [[SESA3043 1.3 - Complex Potential, Wedge Flows and Unsteady Bernoulli#7. A mystery flow: wedges and corners]] · [[Prandtl Boundary-Layer Equations]]
