---
title: "Stefan-Boltzmann Law"
module: "SESA3029 Aerothermodynamics"
type: concept
stream: "Block 5: Heat transfer"
aliases: ["Stefan–Boltzmann law", "total emissive power", "sigma T^4", "Stefan-Boltzmann constant"]
tags: [sesa3029, concept, heat-transfer, radiation]
status: complete
parent_lectures: ["[[SESA3029 W09d - Thermal Radiation]]"]
related_concepts: ["[[Planck's Law]]", "[[Emissivity]]", "[[Radiation Shape Factor]]"]
sources: ["02 - Sources/Lectures/Lecture5.5(1).pdf", "02 - Sources/Lectures/Lecture5.6(1).pdf"]
---

# Stefan-Boltzmann Law

The total emissive power of a blackbody, the energy it emits per unit time and area over all wavelengths, is

$$
E_b(T)=\sigma T^4,\qquad\sigma=5.67\times10^{-8}\ \mathrm{W\,m^{-2}\,K^{-4}},
$$

with $T$ in kelvin. A black surface of area $A$ emits $\dot Q=\sigma AT^4$, and a grey one $\epsilon\sigma AT^4$.

It is the integral of [[Planck's Law]] over wavelength. Substituting $x=C_2/\lambda T$ pulls out $T^4$:

$$
E_b=\frac{C_1T^4}{C_2^4}\int_0^\infty\frac{x^3}{e^x-1}\,\mathrm dx=\frac{C_1T^4}{C_2^4}\cdot\frac{\pi^4}{15},
$$

so $\sigma=\pi^4C_1/(15C_2^4)$. Stefan found the $T^4$ law experimentally and Boltzmann derived it from thermodynamics before Planck.

$\sigma AT^4$ is what a surface emits, not its net loss. For a small body at $T_1$ in large surroundings at $T_2$ the net loss is $\epsilon\sigma A(T_1^4-T_2^4)$, and between two black surfaces it is $A_1F_{12}\sigma(T_1^4-T_2^4)$ with the [[Radiation Shape Factor|shape factor]] $F_{12}$. The fourth power makes radiation dominant at high temperature: a heat shield at 1919 K with $\epsilon=0.6$ radiates 461 kW/m² ([[SESA3029 Example Sheet 3 - Solutions#Q4. Meteor stagnation-point heating|ES3 Q4]]).

## Related

- Parent lecture: [[SESA3029 W09d - Thermal Radiation#6. The Stefan–Boltzmann law|W09d §6]]
- Related concepts: [[Planck's Law]] · [[Wien's Displacement Law]] · [[Emissivity]] · [[Radiation Shape Factor]] · [[Blackbody Radiation]] (SESA2024)

## Sources

- L5.5 slide 12; L5.6 slide 2.
