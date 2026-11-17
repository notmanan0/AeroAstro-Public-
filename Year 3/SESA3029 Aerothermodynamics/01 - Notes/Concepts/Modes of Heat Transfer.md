---
title: "Modes of Heat Transfer"
module: "SESA3029 Aerothermodynamics"
type: concept
stream: "Block 5: Heat transfer"
aliases: ["heat transfer mechanisms", "modes of heat transfer", "conduction, convection and radiation", "heat flux", "heat transfer rate"]
tags: [sesa3029, concept, heat-transfer, conduction, convection, radiation]
status: complete
parent_lectures: ["[[SESA3029 W09a - Heat Conduction and Thermal Resistance]]"]
related_concepts: ["[[Fourier's Law of Heat Conduction]]", "[[Thermal Resistance]]", "[[Blackbody Radiation]]"]
sources: ["02 - Sources/Lectures/Lecture5.1.pdf"]
---

# Modes of Heat Transfer

Heat is transferred in three ways: conduction through a medium by interactions between its particles, convection between a surface and a moving fluid, and radiation as electromagnetic waves, which needs no medium. In every mode the net transfer is from the higher temperature to the lower one, and it stops when the two temperatures are equal.

A re-entry capsule at $M\approx20$, with a surface near 1600 °C on average and 3000 °C at its hottest, shows all three at once. Heat conducts through the heat-shield wall from the hot outside to the cooler inside. It reaches the outer surface from the hot gas by convection, which is conduction at the wall combined with the motion of the fluid in the boundary layer; without bulk fluid motion the same fluid transfers heat by conduction alone. The hot surface and gas also radiate. Everyday examples are a pan heating on a hot plate (conduction), a cup of tea cooling (convection) and the Sun's heat reaching the Earth (radiation).

The **heat transfer rate** $\dot Q$ is in watts and the **heat flux** $\dot q=\dot Q/A$ in W/m². Each mode has its own rate law: [[Fourier's Law of Heat Conduction|Fourier's law]] $\dot Q=-kA\,\mathrm dT/\mathrm dx$ for conduction, Newton's law of cooling $\dot Q=hA_s(T_s-T_\infty)$ for convection ([[SESA3029 W09b - Convective Heat Transfer and the Reynolds Analogy|W09b]]), and the Stefan–Boltzmann law for radiation ([[SESA3029 W09d - Thermal Radiation|W09d]]). In steady problems the first two can be written as [[Thermal Resistance|thermal resistances]] and combined in a network.

![[at_w09a_modes.png|760]]

## Related

- Parent lectures: [[SESA3029 W09a - Heat Conduction and Thermal Resistance#1. Modes of heat transfer|W09a §1]]
- Related concepts: [[Fourier's Law of Heat Conduction]] · [[Thermal Resistance]] · [[Blackbody Radiation]] (SESA2024) · [[SESA1016 T2 - Work, Heat and the First Law]]

## Sources

- Sources: L5.1 slides 2–8; L5.2 slides 9–12.
- Notes: written ahead from the slides, before the lecture.
