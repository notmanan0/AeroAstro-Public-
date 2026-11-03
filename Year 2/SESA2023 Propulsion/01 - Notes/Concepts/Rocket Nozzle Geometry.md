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

A rocket nozzle's geometry is its full axisymmetric profile, a convergent section, a throat and a divergent section. One-dimensional theory only cares about the area, but the profile controls the losses, the length and the weight.

The convergent section is subsonic with a favourable pressure gradient, so any smooth shape works; a contraction ratio of 1.5–4 keeps the chamber Mach number, and so the loss of $p_0$ during heat addition, low, and a half-angle of 30–45° keeps it short. The throat is formed from two tangent circular arcs, with radius up to 2–3 $r_t$. Too tight an upstream curvature causes a vena contracta that reduces the effective throat area and the mass flow, which the throat sets.

A conical divergent section has one parameter, its half-angle $\alpha$, and is easy to make and reliable. Its wall area scales as $1/\sin\alpha$, and assuming radial (spherical-source) exit flow gives the divergence factor $\lambda = (1+\cos\alpha)/2$, which agrees well with exact calculations. Half-angles of 12–18° are typical; at 15°, $\lambda = 0.983$, a 1.7 % thrust loss. A bell (contoured, for example Rao) nozzle starts at 30–60° and turns to 2–8° at the exit, with the contour designed by the method of characteristics so that wall reflections cancel the expansion waves without forming compressions. It is shorter and lighter than a 15° cone of the same area ratio and has a lower divergence loss, but it isn't used for solid motors, because two-phase Al₂O₃ particles erode the concave wall.

A conventional nozzle has a single design altitude, and over-expansion with separation at sea level is unstable, so it is avoided. Plug (aerospike) and expansion–deflection nozzles let the ambient air set the effective area ratio, dual-bell and dual-mode nozzles have two design points, and extendible cones and separation control are other options. The losses in a real nozzle come from divergence, contraction and $p_0$ loss, the boundary layer (0.5–1.5 %), two-phase flow (up to 5 %), chemical kinetics (frozen against shifting equilibrium), and combustion instability, transients and cooling (regenerative, film or ablative).

![[prop_rocket_nozzle.png|700]]

## Related

- [[Converging-Diverging Nozzle Operating Regimes]] · [[Rocket Performance Parameters]] · [[Solid Propellant Burning Rate]]
- SESA2028 materials: [[MMC vs CMC]] (C/C and C/SiC nozzle materials) · [[FEEG2005 Exam 2024-25 Solutions|2024-25 MQ2]]
