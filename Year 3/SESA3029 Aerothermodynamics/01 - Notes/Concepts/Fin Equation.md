---
title: "Fin Equation"
module: "SESA3029 Aerothermodynamics"
type: concept
stream: "Block 5: Heat transfer"
aliases: ["fin equation", "fins", "extended surfaces", "extended surface", "infinitely long fin", "insulated fin tip", "adiabatic fin tip", "fin parameter"]
tags: [sesa3029, concept, heat-transfer, fins, extended-surfaces]
status: complete
parent_lectures: ["[[SESA3029 W09c - Critical Thickness of Insulation and Fins]]"]
related_concepts: ["[[Fin Efficiency and Effectiveness]]", "[[Newton's Law of Cooling]]", "[[Critical Radius of Insulation]]"]
sources: ["02 - Sources/Lectures/Lecture5.4(1).pdf"]
---

# Fin Equation

The fin equation governs the temperature along a fin of constant cross-section: $\mathrm d^2\theta/\mathrm dx^2-a^2\theta=0$, with $\theta=T-T_\infty$ and $a^2=hp/(kA_c)$, where $p$ is the perimeter and $A_c$ the cross-sectional area.

It comes from a steady energy balance on a slice $\Delta x$ of the fin: conduction in at $x$ equals conduction out at $x+\Delta x$ plus convection $hp\,\Delta x\,(T-T_\infty)$ from the slice's sides. With Fourier's law $\dot Q=-kA_c\,\mathrm dT/\mathrm dx$ and constant $k$, $A_c$ and $p$, the limit $\Delta x\to0$ gives the equation. It assumes the temperature is uniform over each cross-section (a thin fin) and constant $h$.

The general solution is $\theta=C_1e^{ax}+C_2e^{-ax}$, with $\theta(0)=\theta_b=T_b-T_\infty$ at the base and one of two tip conditions:

| Tip | Temperature | Heat rate |
|---|---|---|
| infinitely long fin, $\theta\to0$ | $\theta/\theta_b=e^{-ax}$ | $\sqrt{hpkA_c}\,\theta_b$ |
| insulated tip, $\mathrm d\theta/\mathrm dx=0$ at $x=L$ | $\theta/\theta_b=\cosh a(L-x)/\cosh aL$ | $\sqrt{hpkA_c}\,\theta_b\tanh aL$ |

The heat rate is the conduction through the base, $-kA_c\,\mathrm d\theta/\mathrm dx$ at $x=0$, which equals the integrated convection from the sides. Since $\tanh aL=0.99$ at $aL=2.65$, a fin with $aL$ above about 2.65 behaves as infinitely long; below that, the long-fin result overestimates the heat rate.

![[at_w09c_fin_temperature.png|760]]

## Related

- Parent lectures: [[SESA3029 W09c - Critical Thickness of Insulation and Fins#2. Fins: the energy balance|W09c §§2–5]]
- Related concepts: [[Fin Efficiency and Effectiveness]] · [[Newton's Law of Cooling]] · [[Critical Radius of Insulation]]

## Sources

- L5.4 slides 6–18.
