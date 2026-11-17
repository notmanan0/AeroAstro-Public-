---
title: "Prandtl Number"
module: "SESA3029 Aerothermodynamics"
type: concept
stream: "Block 5: Heat transfer"
aliases: ["Pr", "Prandtl number", "momentum diffusivity"]
tags: [sesa3029, concept, heat-transfer, dimensionless-numbers]
status: complete
parent_lectures: ["[[SESA3029 W09b - Convective Heat Transfer and the Reynolds Analogy]]"]
related_concepts: ["[[Thermal Boundary Layer]]", "[[Nusselt Number]]", "[[Stanton Number]]", "[[Reynolds Analogy]]", "[[Reynolds Number]]"]
sources: ["02 - Sources/Lectures/Lecture5.3.pdf"]
---

# Prandtl Number

The Prandtl number is the ratio of the momentum diffusivity to the thermal diffusivity of a fluid, $\mathrm{Pr}=\nu/\alpha=\mu c_p/k$, with $\nu=\mu/\rho$ and $\alpha=k/(\rho c_p)$.

It is a property of the fluid alone, not of the flow: about 0.7 for air and most gases, about 7 for water at room temperature, 0.01–0.03 for liquid metals and hundreds or more for oils. It measures how fast momentum spreads through the fluid compared with heat, and so sets the relative thickness of the velocity and [[Thermal Boundary Layer|thermal boundary layers]]:

- $\mathrm{Pr}<1$: momentum diffuses more slowly, so the thermal boundary layer is thicker than the velocity one;
- $\mathrm{Pr}>1$: momentum diffuses faster, so the velocity boundary layer is thicker;
- $\mathrm{Pr}\approx1$: the two layers have similar thickness.

On a laminar flat plate $\delta_t/\delta\approx\mathrm{Pr}^{-1/3}$, which is where the $\mathrm{Pr}^{1/3}$ in the Nusselt correlations comes from. Pr also links the conductivity to the viscosity, $k=\mu c_p/\mathrm{Pr}$, which is how $k$ is found in [[SESA3029 Example Sheet 3 - Solutions#Q4. Meteor stagnation-point heating|ES3 Q4]].

## Related

- Parent lectures: [[SESA3029 W09b - Convective Heat Transfer and the Reynolds Analogy#3. The Prandtl number|W09b §3]]
- Related concepts: [[Thermal Boundary Layer]] · [[Nusselt Number]] · [[Stanton Number]] · [[Reynolds Analogy]] · [[Reynolds Number]]

## Sources

- L5.3 slides 5–6.
