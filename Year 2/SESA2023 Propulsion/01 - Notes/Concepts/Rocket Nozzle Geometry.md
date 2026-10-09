---
title: "Rocket Nozzle Geometry"
module: "SESA2023 Propulsion"
type: concept
stream: "Section 5: Rockets"
aliases: ["conical nozzle", "bell nozzle", "divergence loss", "aerospike", "dual-bell", "contraction ratio"]
tags: [sesa2023, concept, rockets, nozzles]
status: complete
parent_lectures: ["[[SESA2023 W11 - Solid Propellants and Rocket Nozzle Design]]"]
related_concepts: ["[[Converging-Diverging Nozzle Operating Regimes]]", "[[Rocket Performance Parameters]]", "[[Solid Propellant Burning Rate]]"]
sources: ["02 - Sources/Lectures/Week 11 - Rockets.pdf"]
---
# Rocket Nozzle Geometry

## Definition

> [!note] Definition
> The full axisymmetric profile of a rocket nozzle: a convergent section, a throat, and a divergent section. Only the area matters in 1-D theory, but the **profile** controls losses, length and weight.

## Explanation
- **Convergent section**: subsonic with a favourable pressure gradient, so any smooth shape works.
  - Contraction ratio 1.5–4: a lower chamber Mach number means less $p_0$ loss during heat addition.
  - Half-angle 30–45° keeps it short.
- **Throat**: two tangent circular arcs (radius up to 2–3 $r_t$). A tight upstream curvature causes a vena contracta, which reduces the effective $A_t$ and $\dot m$. The throat sets the mass flow.
- **Conical divergent section**:
  - One parameter, the half-angle $\alpha$. Easy to make and reliable.
  - The wall area scales as $1/\sin\alpha$.
  - Divergence factor $\lambda = \dfrac{1+\cos\alpha}{2}$, from assuming radial (spherical-source) exit flow; exact calculations agree well.
  - $\alpha = 12$–18°. At 15°, $\lambda = 0.983$, a 1.7 % thrust loss.
- **Bell (contoured, e.g. Rao) nozzle**:
  - A 30–60° start that turns to 2–8° at the exit.
  - The contour is designed (method of characteristics, 2-D) so wall reflections cancel the expansion waves without creating compressions (shocks).
  - **Shorter and lighter, with lower divergence loss** than a 15° cone of the same area ratio.
  - **Not for solids**: two-phase Al₂O₃ particles erode the concave wall.
- **Altitude compensation**: a conventional nozzle has one design altitude.
  - Over-expansion with separation at sea level is unstable, so it is avoided.
  - **Plug/aerospike** and **expansion–deflection** nozzles let the ambient air set the effective area ratio.
  - **Dual-bell** and **dual-mode** nozzles have two design points.
  - **Extendible cones** and **separation control** are other options.
- **Real-nozzle losses**:
  - divergence;
  - contraction and $p_0$ loss;
  - boundary layer (0.5–1.5 %);
  - two-phase flow (up to 5 %);
  - chemical kinetics (frozen vs shifting equilibrium);
  - combustion instability, transients, and cooling (regenerative, film, ablative).

![[prop_rocket_nozzle.png|700]]

## Related
- [[Converging-Diverging Nozzle Operating Regimes]] · [[Rocket Performance Parameters]] · [[Solid Propellant Burning Rate]]

**Related (SESA2028 materials):** [[MMC vs CMC]] (C/C and C/SiC nozzle materials) · [[FEEG2005 Exam 2024-25 Solutions|2024-25 MQ2]]

## Sources
- Week 11 notes §11.4; Lecture 33
