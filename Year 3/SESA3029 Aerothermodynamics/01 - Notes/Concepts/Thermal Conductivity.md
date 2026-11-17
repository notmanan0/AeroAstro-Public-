---
title: "Thermal Conductivity"
module: "SESA3029 Aerothermodynamics"
type: concept
stream: "Block 5: Heat transfer"
aliases: ["conductivity", "thermal conductivity k", "k (thermal conductivity)"]
tags: [sesa3029, concept, heat-transfer, conduction, material-property]
status: complete
parent_lectures: ["[[SESA3029 W09a - Heat Conduction and Thermal Resistance]]"]
related_concepts: ["[[Fourier's Law of Heat Conduction]]", "[[Thermal Resistance]]"]
sources: ["02 - Sources/Lectures/Lecture5.1.pdf", "02 - Sources/Lectures/Lecture5.2.pdf"]
---

# Thermal Conductivity

Thermal conductivity $k$ is the rate of heat transfer through a unit thickness of a material, per unit area, per unit temperature difference. It is the constant of proportionality in [[Fourier's Law of Heat Conduction|Fourier's law]], $k=-\dot Q/(A\,\mathrm dT/\mathrm dx)$, in W/(m K), and it measures a material's ability to conduct heat.

Values span several orders of magnitude. Iron has $k=80.2$ W/(m K) and water $0.607$ W/(m K), so iron conducts heat 132 times faster; metals are good conductors of heat for the same reason they conduct electricity, since free electrons carry energy as well as charge. Insulating materials sit near 0.02–0.05 W/(m K) and still air near 0.026 W/(m K), which is why a still air gap insulates well (the double-glazing example in [[SESA3029 W09a - Heat Conduction and Thermal Resistance#11. The Nusselt number|W09a §11]]).

$k$ is a property of the material, and in general it varies with temperature; the steady-conduction results of W09a assume it constant in each layer. It also appears in the Nusselt number $\text{Nu}=hL/k$, where it is the conductivity of the **fluid**, because heat enters a fluid at a wall by conduction. That distinguishes it from the heat transfer coefficient $h$, which depends on the flow and is not a material property.

## Related

- Parent lectures: [[SESA3029 W09a - Heat Conduction and Thermal Resistance#3. Thermal conductivity|W09a §3]]
- Related concepts: [[Fourier's Law of Heat Conduction]] · [[Thermal Resistance]] · [[SESA3029 W09b - Convective Heat Transfer and the Reynolds Analogy|W09b]] (the Nusselt number in use)

## Sources

- Sources: L5.1 slides 11–12; L5.2 slides 1, 17.
- Notes: written ahead from the slides, before the lecture.
