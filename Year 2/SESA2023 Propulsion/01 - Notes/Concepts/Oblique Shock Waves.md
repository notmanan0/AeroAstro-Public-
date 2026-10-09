---
title: "Oblique Shock Waves"
module: "SESA2023 Propulsion"
type: concept
stream: "Section 1: Introduction and Fundamentals"
aliases: ["oblique shock", "shock angle", "deflection angle", "theta-beta-M", "detached shock"]
tags: [sesa2023, concept, compressible-flow, shocks]
status: complete
parent_lectures: ["[[SESA2023 W04 - Friction, Heat Addition, Oblique Shocks and Intakes]]"]
related_concepts: ["[[Normal Shock Waves]]", "[[Intake Pressure Recovery]]"]
sources: ["02 - Sources/Lectures/Week 04 - Gas Dynamics II - Friction, Heat Transfer, Oblique Shocks and Intakes.pdf"]
---
# Oblique Shock Waves

## Definition

> [!note] Definition
> A shock inclined at angle $\sigma$ to the flow turns it through $\delta$ towards the shock. The **tangential** velocity is unchanged, so it is a normal shock in the normal component:
> $$M_{n1} = M_1\sin\sigma,\quad M_{n2} = M_2\sin(\sigma-\delta),\quad \tan\delta = 2\cot\sigma\frac{M_1^2\sin^2\sigma-1}{M_1^2(\gamma+\cos2\sigma)+2}$$

## Explanation
- **Method**: use the normal-shock tables with $M_{n1}$ in place of $M_1$. That gives $p_2/p_1$, $T_2/T_1$ and $\rho_2/\rho_1$ (static ratios only, which are unaffected by the tangential component). Then $M_2 = M_{n2}/\sin(\sigma-\delta)$.
- $\rho_2/\rho_1 = \tan\sigma/\tan(\sigma-\delta)$.
- **The $\delta$–$\sigma$–$M$ curves**:
  - For each $M_1$, $\delta = 0$ at $\sigma = \mu$ (a Mach wave) and at $\sigma = 90^\circ$ (a normal shock).
  - There is a **maximum deflection** $\delta_{max}$.
  - For $\delta<\delta_{max}$ there are two solutions. The **weak** one forms on wedges and compression corners, and is usually supersonic downstream. The **strong** one is always subsonic downstream.
  - For $\delta>\delta_{max}$ the shock **detaches**: a curved bow shock, normal (strong) on the axis and weakening outwards. Blunt bodies always have detached shocks.
- Supersonic flow past a wedge has **straight** streamlines. No upstream influence makes the field easy to build downstream.
- **Design lesson**: oblique shocks are weaker, so they lose less $p_0$ than a normal shock at the same $M_1$. That is the basis of external-compression intakes. Keep deflections small (slender bodies).

![[prop_oblique_shock.png|640]]

## Examples
- $M_1 = 3$, $\sigma = 50^\circ$: $M_{n1} = 2.30$, $\delta = 28.9^\circ$, $M_{n2} = 0.534$, $M_2 = 1.48$. From 101.3 kPa and 288 K: $p_2 = 607$ kPa, $T_2 = 560$ K.

## Related
- [[Normal Shock Waves]] · [[Intake Pressure Recovery]]

## Sources
- Week 4 notes §3.3; Lectures 10–11; NACA Report 1135
