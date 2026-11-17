---
title: "Wien's Displacement Law"
module: "SESA3029 Aerothermodynamics"
type: concept
stream: "Block 5: Heat transfer"
aliases: ["locus of maximum power", "peak wavelength", "lambda max T"]
tags: [sesa3029, concept, heat-transfer, radiation]
status: complete
parent_lectures: ["[[SESA3029 W09d - Thermal Radiation]]"]
related_concepts: ["[[Planck's Law]]", "[[Stefan-Boltzmann Law]]"]
sources: ["02 - Sources/Lectures/Lecture5.5(1).pdf"]
---

# Wien's Displacement Law

The wavelength at which a blackbody emits most strongly is inversely proportional to its absolute temperature:

$$
(\lambda T)_{max\ power}=2897.8\ \mathrm{\mu m\,K}.
$$

It follows from [[Planck's Law]]. With $x=C_2/\lambda T$ the spectrum is proportional to $x^5/(e^x-1)$, whose derivative vanishes where $5(e^x-1)=xe^x$, or $x=5(1-e^{-x})$. Iterating from $x=5$ converges to $x=4.96511$, so $\lambda_{max}T=C_2/4.96511=2897.8$ μm K with $C_2=14\,388$ μm K. Wien found the form from classical thermodynamics before Planck; Planck's law fixes the constant.

The Sun (about 5800 K) peaks at 0.50 μm, in the visible; a 300 K surface peaks at 9.66 μm, in the infrared, which is why people and room-temperature objects are invisible in the dark but bright on infrared cameras. A 600 K wall peaks at 4.83 μm. The law is also used backwards: the temperatures of stars come from the peaks of their spectra.

## Related

- Parent lecture: [[SESA3029 W09d - Thermal Radiation#5. Wien's displacement law|W09d §5]]
- Related concepts: [[Planck's Law]] · [[Stefan-Boltzmann Law]] · [[Blackbody Radiation]] (SESA2024)

## Sources

- L5.5 slides 10–11.
