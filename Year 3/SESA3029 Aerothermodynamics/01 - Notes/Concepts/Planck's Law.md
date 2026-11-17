---
title: "Planck's Law"
module: "SESA3029 Aerothermodynamics"
type: concept
stream: "Block 5: Heat transfer"
aliases: ["Planck's blackbody radiation", "Planck distribution", "spectral blackbody emissive power", "ultraviolet catastrophe"]
tags: [sesa3029, concept, heat-transfer, radiation]
status: complete
parent_lectures: ["[[SESA3029 W09d - Thermal Radiation]]"]
related_concepts: ["[[Wien's Displacement Law]]", "[[Stefan-Boltzmann Law]]", "[[Blackbody Radiation]]"]
sources: ["02 - Sources/Lectures/Lecture5.5(1).pdf"]
---

# Planck's Law

Planck's law gives the power a blackbody emits per unit area per unit wavelength, the spectral blackbody emissive power:

$$
E_{b,\lambda}(\lambda,T)=\frac{C_1}{\lambda^5\left[\exp(C_2/\lambda T)-1\right]}\quad[\mathrm{W\,m^{-2}\,\mu m^{-1}}],
$$

with $\lambda$ in μm, $T$ in K, $C_1=2\pi hc_0^2=3.742\times10^8$ W μm⁴ m⁻² and $C_2=hc_0/k_B=1.439\times10^4$ μm K.

Classical statistical mechanics predicted a spectrum that grows as $\lambda^{-4}$ at short wavelength, which is the long-wavelength limit of Planck's law, $E_{b,\lambda}\simeq C_1T/(C_2\lambda^4)$; its integral is infinite, the ultraviolet catastrophe. Planck fitted the measured spectrum of an isothermal cavity by assuming that radiation is emitted in quanta of energy $E=h\nu$. At short wavelengths the factor $\exp(-C_2/\lambda T)$ then suppresses the emission and the curve turns over.

In terms of $x=C_2/\lambda T$ the law is $E_{b,\lambda}=(C_1T^5/C_2^5)\,x^5/(e^x-1)$: every temperature gives the same curve, scaled by $T^5$ in height and $1/T$ in wavelength. The peak of that curve gives [[Wien's Displacement Law]] and its integral gives the [[Stefan-Boltzmann Law]]. A hotter blackbody emits more at every wavelength, so the curves never cross, and no real surface emits more than a blackbody at any wavelength.

## Related

- Parent lecture: [[SESA3029 W09d - Thermal Radiation#4. The blackbody and Planck's law|W09d §4]]
- Related concepts: [[Wien's Displacement Law]] · [[Stefan-Boltzmann Law]] · [[Emissivity]] · [[Blackbody Radiation]] (SESA2024)

## Sources

- L5.5 slides 7–10, 13.
