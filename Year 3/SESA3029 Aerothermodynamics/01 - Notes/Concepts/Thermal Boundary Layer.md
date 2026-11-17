---
title: "Thermal Boundary Layer"
module: "SESA3029 Aerothermodynamics"
type: concept
stream: "Block 5: Heat transfer"
aliases: ["thermal boundary layer", "temperature boundary layer", "thermal boundary layer thickness", "delta_t"]
tags: [sesa3029, concept, heat-transfer, convection, boundary-layer]
status: complete
parent_lectures: ["[[SESA3029 W09b - Convective Heat Transfer and the Reynolds Analogy]]"]
related_concepts: ["[[Prandtl Number]]", "[[Newton's Law of Cooling]]", "[[Boundary-layer Thickness Measures]]", "[[Reynolds Analogy]]"]
sources: ["02 - Sources/Lectures/Lecture5.3.pdf"]
---

# Thermal Boundary Layer

The thermal boundary layer is the region next to a heated or cooled surface in which the fluid temperature changes from the wall value $T_s$ to the free-stream value $T_\infty$. Its thickness $\delta_t$ is the distance from the surface at which $T-T_s=0.99\,(T_\infty-T_s)$.

It forms for the same reason as the velocity boundary layer: the fluid touching the wall takes the wall temperature, it exchanges energy with the layer above, and so on outwards, while the flow carries the heated or cooled fluid downstream. $\delta_t$ grows in the flow direction, so the heat transfer coefficient, which scales roughly as $k/\delta_t$, is largest at the leading edge and falls downstream ($h\propto x^{-1/2}$ on a laminar flat plate).

On a heated or cooled surface in a moving fluid both layers develop together, and their relative thickness is set by the [[Prandtl Number]]. For a laminar flat plate $\delta_t/\delta\approx\mathrm{Pr}^{-1/3}$: the thermal layer is a little thicker than the velocity layer in air ($\mathrm{Pr}=0.72$, ratio 1.12) and about half as thick in water ($\mathrm{Pr}=7$). At $\mathrm{Pr}=1$ the dimensionless temperature and velocity profiles coincide, which is the basis of the [[Reynolds Analogy]].

![[at_w09b_boundary_layers.png|760]]

## Related

- Parent lectures: [[SESA3029 W09b - Convective Heat Transfer and the Reynolds Analogy#2. The thermal boundary layer|W09b §2]]
- Related concepts: [[Prandtl Number]] · [[Newton's Law of Cooling]] · [[Reynolds Analogy]] · [[Boundary-layer Thickness Measures]] · [[SESA3043 3.1 - Boundary-Layer Concepts and Thickness Measures|the velocity boundary layer (SESA3043 3.1)]]

## Sources

- L5.3 slides 4–5.
