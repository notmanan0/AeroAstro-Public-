---
title: "Blackbody Radiation"
module: "SESA2024 Astronautics"
type: concept
stream: "Spacecraft Subsystems"
aliases: ["black body", "blackbody", "Planck's law", "Wien's displacement law", "Stefan-Boltzmann law", "grey body"]
tags: [sesa2024, concept, thermal-control]
status: lectured
parent_lectures: ["[[SESA2024 10 - Thermal Control]]"]
related_concepts: ["[[Absorptance and Emittance]]", "[[Spacecraft Thermal Balance Equation]]"]
sources: ["02 - Sources/Lectures/SESA2024 Lecture 2025-11-25.txt"]
---

# Blackbody Radiation

A black body absorbs all radiation falling on it, at every wavelength, and emits the maximum possible thermal radiation at its temperature; its emission spectrum depends on temperature alone.

Planck's law gives that spectrum. As temperature rises, the emission grows and its peak moves to shorter wavelengths, following Wien's displacement law $\lambda_{max}T=2898\ \mu$m K: the Sun, near 6000 K, peaks in the visible, while the Earth's peak near 10 μm corresponds to about 290 K. Integrating over all wavelengths gives the Stefan–Boltzmann law for the total emitted flux,

$$
Q_{BB}=\sigma T^4,\qquad\sigma=5.67\times10^{-8}\ \mathrm{W\,m^{-2}\,K^{-4}}.
$$

A grey body absorbs and emits a constant fraction of the black-body value at all wavelengths. Real surfaces vary with wavelength, which is what gives them colour, and is described by their absorptance and emittance. Because a spacecraft receives sunlight at short wavelengths but radiates its own heat in the infrared, the two properties can be chosen almost independently, and that is the basis of passive thermal control.

## Related

- [[SESA2024 10 - Thermal Control#2. Emission|Emission in the lecture note]]
- [[Absorptance and Emittance]] · [[Spacecraft Thermal Balance Equation]]
