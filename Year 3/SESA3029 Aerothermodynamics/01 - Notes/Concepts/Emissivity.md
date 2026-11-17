---
title: "Emissivity"
module: "SESA3029 Aerothermodynamics"
type: concept
stream: "Block 5: Heat transfer"
aliases: ["grey body", "gray body", "spectral emissivity", "monochromatic emissivity", "emission coefficient"]
tags: [sesa3029, concept, heat-transfer, radiation]
status: complete
parent_lectures: ["[[SESA3029 W09d - Thermal Radiation]]"]
related_concepts: ["[[Kirchhoff's Law of Thermal Radiation]]", "[[Stefan-Boltzmann Law]]", "[[Absorptance and Emittance]]"]
sources: ["02 - Sources/Lectures/Lecture5.6(1).pdf"]
---

# Emissivity

Emissivity is the ratio of the power a surface emits to the power a blackbody at the same temperature emits, $\epsilon=E/E_b$; it is 1 for a blackbody and less than 1 for every real surface.

It depends on the material, the surface condition, the temperature and the wavelength, so the full description is the spectral (monochromatic) emissivity $\epsilon_\lambda=E_\lambda/E_{b,\lambda}$. The total emissivity is $\epsilon_\lambda$ averaged with the blackbody spectrum as weight, $\epsilon=\int\epsilon_\lambda E_{b,\lambda}\,\mathrm d\lambda/(\sigma T^4)$.

A **grey body** has $\epsilon_\lambda$ independent of wavelength: its spectrum is the blackbody curve lowered by a constant proportion, and its emissive power is

$$
E=\epsilon E_b=\epsilon\sigma T^4\quad[\mathrm{W\,m^{-2}}].
$$

For a grey body [[Kirchhoff's Law of Thermal Radiation|Kirchhoff's law]] holds for the totals, $\alpha=\epsilon$, whatever the incident spectrum. It is the model meant whenever a problem gives a single $\epsilon$. At 600 K a grey surface with $\epsilon=0.6$ emits 4.41 kW/m² against 7.35 kW/m² for a blackbody. Polished metals have low emissivity (0.02–0.1), soot and matt black paint approach 1.

## Related

- Parent lecture: [[SESA3029 W09d - Thermal Radiation#7. Emissivity and grey bodies|W09d §7]]
- Related concepts: [[Kirchhoff's Law of Thermal Radiation]] · [[Stefan-Boltzmann Law]] · [[Planck's Law]] · [[Absorptance and Emittance]] (SESA2024 calls it emittance)

## Sources

- L5.6 slide 10; L5.5 slides 6–7.
