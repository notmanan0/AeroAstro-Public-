---
title: "Kirchhoff's Law of Thermal Radiation"
module: "SESA3029 Aerothermodynamics"
type: concept
stream: "Block 5: Heat transfer"
aliases: ["absorptivity equals emissivity", "alpha equals epsilon", "Kirchhoff's radiation law"]
tags: [sesa3029, concept, heat-transfer, radiation]
status: complete
parent_lectures: ["[[SESA3029 W09d - Thermal Radiation]]"]
related_concepts: ["[[Emissivity]]", "[[Planck's Law]]", "[[Absorptance and Emittance]]"]
sources: ["02 - Sources/Lectures/Lecture5.5(1).pdf", "02 - Sources/Lectures/Lecture5.6(1).pdf"]
---

# Kirchhoff's Law of Thermal Radiation

At thermal equilibrium a surface's absorptivity equals its emissivity, $\alpha=\epsilon$: a good absorber is an equally good emitter.

The proof puts a body at temperature $T$ inside an isothermal enclosure at the same $T$, with a vacuum between them. The enclosure fills with blackbody radiation, so the body receives $\sigma T^4$ per unit area and absorbs $\alpha\sigma T^4A$. It emits $\epsilon\sigma T^4A$. Equal temperatures mean no net heat flow, otherwise the body would heat itself above its surroundings, so $\alpha\sigma T^4A=\epsilon\sigma T^4A$ and $\alpha=\epsilon$.

Repeated with a filter that passes one wavelength band, the argument gives the spectral form $\alpha_\lambda=\epsilon_\lambda$, which holds generally. The total values agree only for a grey surface, or when the incident radiation has the spectrum of a blackbody at the surface's own temperature. Sunlight on a room-temperature surface breaks the second condition, which is why white paint can absorb only about 20 % of sunlight yet emit 90 % of the blackbody value in the infrared.

Applied to the Earth, a grey Earth with $\alpha=\epsilon$ has the same steady temperature as a black one (278.75 K); only reflection of sunlight at different wavelengths from its own emission changes it.

## Related

- Parent lecture: [[SESA3029 W09d - Thermal Radiation#3. Kirchhoff's law of thermal radiation|W09d §3]]
- Related concepts: [[Emissivity]] · [[Planck's Law]] · [[Stefan-Boltzmann Law]] · [[Absorptance and Emittance]] (SESA2024, spacecraft surfaces)

## Sources

- L5.5 slide 6; L5.6 slide 10.
