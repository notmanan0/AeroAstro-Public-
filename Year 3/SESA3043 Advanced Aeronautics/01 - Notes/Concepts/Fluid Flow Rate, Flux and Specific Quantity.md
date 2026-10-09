---
title: "Fluid Flow Rate, Flux and Specific Quantity"
module: "SESA3043 Advanced Aeronautics"
type: concept
stream: "Chapter 1: Conservation Laws"
aliases: ["flow rate and flux", "specific transported quantity"]
tags: [sesa3043, concept, flux]
status: complete
parent_lectures: ["[[SESA3043 1.1 - Mathematical Tools and Flow Description]]"]
related_concepts: ["[[Mass Flow Rate]]", "[[Momentum Flux]]", "[[Flux Integrals]]"]
sources: ["02 - Sources/Lectures/L1 - SESA3043.txt"]
---

# Fluid Flow Rate, Flux and Specific Quantity

## Definitions

- **Specific quantity** $b$: amount of an extensive property $B$ per unit mass, $b=B/m$.
- **Flux**: transport rate per unit area.
- **Flow rate**: flux integrated over a finite surface.

For surface normal $\mathbf n$,

$$
\dot B=\int_A\rho b(\mathbf u\cdot\mathbf n)\,\mathrm dA.
$$

| Property | $b$ | Advective flux |
|---|---|---|
| Mass | $1$ | $\rho u_n$ |
| Momentum | $\mathbf u$ | $\rho\mathbf u u_n$ |
| Total energy | $e_t$ | $\rho e_tu_n$ |

The sign comes from $u_n=\mathbf u\cdot\mathbf n$: positive is outward through the oriented surface.

## Related

- [[Mass Flow Rate]] · [[Momentum Flux]] · [[Reynolds Transport Theorem]]

