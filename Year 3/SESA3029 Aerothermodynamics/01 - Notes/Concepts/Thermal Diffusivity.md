---
title: "Thermal Diffusivity"
module: "SESA3029 Aerothermodynamics"
type: concept
stream: "Block 5: Heat transfer"
aliases: ["diffusivity", "k over rho cp"]
tags: [sesa3029, concept, heat-transfer, conduction]
status: complete
parent_lectures: ["[[SESA3029 W09e - Numerical Methods in Conduction]]"]
related_concepts: ["[[Heat Equation]]", "[[Finite-Difference Form of the Heat Equation]]", "[[CFL and Fourier Numbers]]", "[[Prandtl Number]]"]
sources: ["02 - Sources/Lectures/Lecture5.7.pdf"]
---

# Thermal Diffusivity

Thermal diffusivity is the ratio of a material's thermal conductivity to its heat capacity per unit volume, $\alpha=k/(\rho c_p)$ in m²/s; it measures how quickly the material's temperature responds to a change in its surroundings.

It is the coefficient of the heat diffusion equation, $\nabla^2T+\dot g/k=(1/\alpha)\,\partial T/\partial t$. A large $k$ passes heat on and a small $\rho c_p$ stores little of it, so either gives a large $\alpha$: the material would rather conduct than store. A disturbance spreads a distance of order $\sqrt{\alpha t}$ in time $t$, so the time for heat to cross a length $L$ is of order $L^2/\alpha$. Steady conduction depends on $k$ alone; transient conduction depends on $\alpha$.

Typical values near 300 K: copper $1.17\times10^{-4}$, aluminium $9.7\times10^{-5}$, stainless steel $4.0\times10^{-6}$, water $1.5\times10^{-7}$ m²/s. A 1 m copper bar takes of order $L^2/\alpha\approx8600$ s to respond end to end.

In a numerical scheme $\alpha$ enters through the Fourier number $\mathcal F=\alpha\Delta t/\Delta x^2$, which limits the explicit time step to $\Delta t\le\Delta x^2/(2\alpha)$ in 1-D. In a fluid the ratio of momentum diffusivity $\nu$ to thermal diffusivity is the [[Prandtl Number]], $\mathrm{Pr}=\nu/\alpha$. The same letter $\alpha$ is used for absorptivity in radiation.

## Related

- Parent lecture: [[SESA3029 W09e - Numerical Methods in Conduction#2. Thermal diffusivity|W09e §2]]
- Related concepts: [[Heat Equation]] · [[Finite-Difference Form of the Heat Equation]] · [[CFL and Fourier Numbers]] · [[Prandtl Number]] · [[Thermal Conductivity]]

## Sources

- L5.7 slides 6–7.
