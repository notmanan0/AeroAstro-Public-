---
title: "Thermal Resistance"
module: "SESA3029 Aerothermodynamics"
type: concept
stream: "Block 5: Heat transfer"
aliases: ["electrical analogy", "electrical resistance analogy", "thermal resistance network", "thermal circuit", "convection resistance", "conduction resistance", "area-specific thermal resistance", "R-value"]
tags: [sesa3029, concept, heat-transfer, conduction, convection, electrical-analogy]
status: complete
parent_lectures: ["[[SESA3029 W09a - Heat Conduction and Thermal Resistance]]"]
related_concepts: ["[[Fourier's Law of Heat Conduction]]", "[[Thermal Conductivity]]", "[[Radial Conduction in Cylinders and Spheres]]"]
sources: ["02 - Sources/Lectures/Lecture5.1.pdf", "02 - Sources/Lectures/Lecture5.2.pdf"]
---

# Thermal Resistance

A thermal resistance is the temperature difference needed to drive unit heat rate through a component in steady state, $R_\text{th}=\Delta T/\dot Q$ in K/W. Writing steady conduction and convection this way makes heat flow the analogue of current and temperature difference the analogue of voltage, so $\dot Q=\Delta T/R_\text{total}$ is Ohm's law.

For steady, one-dimensional transfer with constant properties and no heat generation, the resistances used in the course are

$$
\underbrace{\frac{L}{kA}}_{\text{plane wall}},\qquad
\underbrace{\frac{\ln(r_o/r_i)}{2\pi kL}}_{\text{long cylinder}},\qquad
\underbrace{\frac1{4\pi k}\left(\frac1{r_i}-\frac1{r_o}\right)}_{\text{spherical shell}},\qquad
\underbrace{\frac1{hA_s}}_{\text{convection}},
$$

where in the cylinder $L$ is its length, not a thickness. All four are on the exam formula sheet.

Components that carry the same heat one after another are in series and their resistances add, $R_\text{total}=R_1+R_2+\dots$; the temperature drop across each is $\dot QR_j$, which gives the interface temperatures. Components that share the same temperature difference side by side are in parallel and their reciprocals add, $1/R_\text{total}=1/R_1+1/R_2+\dots$, provided the paths do not exchange heat sideways. A small high-conductivity path in parallel with insulation, such as steel bolts through a wall, can carry a large share of the heat ([[SESA3029 Example Sheet 3 - Solutions#Q1. Composite wall pierced by steel bolts|ES3 Q1]]).

For plane layers of a common area it is convenient to use the area-specific resistance $R''=RA=L/k$ (m² K/W), known as the R-value in building insulation; then $\dot q=\Delta T/R''$. For tubes and spheres each layer and each convecting surface has its own area, so the resistances must be kept in K/W. The largest resistance in a chain carries the largest temperature drop, and it is the one worth reducing (or, for insulation, increasing).

![[at_w09a_insulated_block.png|760]]

## Related

- Parent lectures: [[SESA3029 W09a - Heat Conduction and Thermal Resistance#5. The electrical analogy and thermal resistance|W09a §5]] (plane walls) · [[SESA3029 W09a - Heat Conduction and Thermal Resistance#10. Walls and tubes with convection on both sides|W09a §10]] (convection boundaries)
- Related concepts: [[Fourier's Law of Heat Conduction]] · [[Thermal Conductivity]] · [[Radial Conduction in Cylinders and Spheres]]
- Used later in [[SESA3029 W09c - Critical Thickness of Insulation and Fins|W09c]] (critical thickness of insulation) and [[SESA3029 W09f - Heat Exchangers|W09f]] (overall heat transfer coefficient)

## Sources

- Sources: L5.1 slides 13–17; L5.2 slides 4–7 and 14–16.
- Notes: written ahead from the slides, before the lecture.
