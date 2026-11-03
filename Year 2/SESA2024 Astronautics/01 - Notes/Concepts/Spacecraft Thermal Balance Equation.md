---
title: "Spacecraft Thermal Balance Equation"
module: "SESA2024 Astronautics"
type: concept
stream: "Spacecraft Subsystems"
aliases: ["thermal balance", "equilibrium temperature", "albedo", "Earth infrared", "height factor"]
tags: [sesa2024, concept, thermal-control]
status: lectured
parent_lectures: ["[[SESA2024 10 - Thermal Control]]"]
related_concepts: ["[[Absorptance and Emittance]]", "[[Blackbody Radiation]]", "[[Eclipse Duration]]"]
sources: ["02 - Sources/Lectures/Chapter 10/2025 WEEK 8 - Chapter 10 - Thermal Control - Lecture slides - complete.pdf"]
---

# Spacecraft Thermal Balance Equation

The thermal balance equation sets a spacecraft's equilibrium temperature by equating the radiation it absorbs plus its internal dissipation to the radiation it emits:

$$
\alpha_SQ_SA_S+\alpha_SQ_SA_a\,a\,F\cos\phi\,\beta+\varepsilon Q_EA_EF+P=\varepsilon\sigma A_{surf}T^4.
$$

The inputs are direct sunlight ($Q_S\approx1350\text{–}1400\ \mathrm{W/m^2}$) on the Sun-facing projected area; albedo, the Earth's reflected sunlight (average $a=0.34$), on the Earth-facing projected area, scaled by $\cos\phi$ (the geocentric angle between spacecraft and Sun), switched off over the night side by $\beta$, and reduced with altitude by $F=(R_E/R_{orb})^2$; Earth infrared ($Q_E\approx240\ \mathrm{W/m^2}$), absorbed with $\alpha_{IR}=\varepsilon$ by Kirchhoff's law; and internal dissipation $P$. The output is emission from the total surface area. Radiation is the only significant exchange, since conduction cannot reach space and convection has no gas.

Dividing through gives $T^4$, with the solar terms multiplied by $\alpha_S/\varepsilon$, which is why the finish controls the temperature in sunlight. In eclipse with $P=0$ only the Earth term remains and $\varepsilon$ cancels. The equation is a static snapshot, evaluated at the hot (subsolar, sunlit) and cold (eclipse) extremes in design.

## Related

- [[SESA2024 10 - Thermal Control#3. The spacecraft thermal balance equation|Derivation in the lecture note]] · [[SESA2024 10 - Thermal Control#A painted sphere in low Earth orbit|Worked example]]
- [[Absorptance and Emittance]] · [[Blackbody Radiation]] · [[Eclipse Duration]]
