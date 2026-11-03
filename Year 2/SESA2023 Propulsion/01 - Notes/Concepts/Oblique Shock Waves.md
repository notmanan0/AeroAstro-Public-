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

An oblique shock inclined at angle $\sigma$ to the flow turns it through $\delta$ towards the shock. The tangential velocity is unchanged, so it acts as a normal shock on the normal component:

$$
M_{n1} = M_1\sin\sigma,\quad M_{n2} = M_2\sin(\sigma-\delta),\quad \tan\delta = 2\cot\sigma\frac{M_1^2\sin^2\sigma-1}{M_1^2(\gamma+\cos2\sigma)+2} .
$$

The normal-shock tables therefore apply with $M_{n1}$ in place of $M_1$, giving the static ratios $p_2/p_1$, $T_2/T_1$ and $\rho_2/\rho_1$, which the tangential component doesn't affect, and then $M_2 = M_{n2}/\sin(\sigma-\delta)$. The density ratio can also be written $\rho_2/\rho_1 = \tan\sigma/\tan(\sigma-\delta)$. At $M_1 = 3$ and $\sigma = 50^\circ$, for example, $M_{n1} = 2.30$, $\delta = 28.9^\circ$, $M_{n2} = 0.534$ and $M_2 = 1.48$; from 101.3 kPa and 288 K that gives $p_2 = 607$ kPa and $T_2 = 560$ K.

For each $M_1$ the $\delta$–$\sigma$ curve has $\delta = 0$ both at the Mach angle ($\sigma = \mu$, a Mach wave) and at $\sigma = 90^\circ$ (a normal shock), with a maximum deflection $\delta_{max}$ in between. Below $\delta_{max}$ there are two solutions: the weak one, which forms on wedges and compression corners and is usually supersonic downstream, and the strong one, always subsonic downstream. Above $\delta_{max}$ the shock detaches into a curved bow shock, normal on the axis and weakening outwards; blunt bodies always have detached shocks. Supersonic flow past a wedge has straight streamlines, and because there is no upstream influence the field can be built up from upstream to downstream.

The design lesson is that oblique shocks are weaker and lose less stagnation pressure than a normal shock at the same $M_1$, which is the basis of external-compression intakes, and that deflections should be kept small (slender bodies).

![[prop_oblique_shock.png|640]]

## Related

- [[Normal Shock Waves]] · [[Intake Pressure Recovery]]
