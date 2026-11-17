---
title: "Nusselt Number"
module: "SESA3029 Aerothermodynamics"
type: concept
stream: "Block 5: Heat transfer"
aliases: ["Nu", "Nusselt number", "dimensionless heat transfer coefficient", "local Nusselt number", "Nusselt correlation"]
tags: [sesa3029, concept, heat-transfer, convection, dimensionless-numbers]
status: complete
parent_lectures: ["[[SESA3029 W09b - Convective Heat Transfer and the Reynolds Analogy]]"]
related_concepts: ["[[Newton's Law of Cooling]]", "[[Stanton Number]]", "[[Prandtl Number]]", "[[Reynolds Analogy]]", "[[Reynolds Number]]"]
sources: ["02 - Sources/Lectures/Lecture5.3.pdf"]
---

# Nusselt Number

The Nusselt number is the dimensionless heat transfer coefficient, $\mathrm{Nu}=hL/k$, with $L$ a characteristic length and $k$ the conductivity of the fluid. It is the ratio of the heat transferred by convection to the heat that pure conduction would carry across a fluid layer of thickness $L$ under the same temperature difference.

$\mathrm{Nu}=1$ would mean the flow adds nothing to conduction; large Nu means the motion multiplies the heat transfer many times. With $L=x$, the distance from a leading edge, it becomes the local value $\mathrm{Nu}_x=hx/k$. It is related to the other groups by

$$
\mathrm{Nu}=\mathrm{St}\times\mathrm{Re}\times\mathrm{Pr}.
$$

Nu is found from correlations, most of them of the form $\mathrm{Nu}_x=C\,\mathrm{Re}_x^n\mathrm{Pr}^m$ (called the Reynolds analogy in this module). The standard set is:

| Flow | Uniform wall heat flux | Uniform wall temperature |
|---|---|---|
| Laminar pipe flow, $\mathrm{Re}<2000$ | 4.364 | 3.658 |
| Laminar flat plate, $\mathrm{Re}<3\times10^5$ | $0.453\,\mathrm{Re}_x^{1/2}\mathrm{Pr}^{1/3}$ | $0.332\,\mathrm{Re}_x^{1/2}\mathrm{Pr}^{1/3}$ |
| Turbulent pipe flow | $0.023\,\mathrm{Re}^{4/5}\mathrm{Pr}^n$ ($n=0.3$ cooling, 0.4 heating) | (same) |
| Turbulent flat plate, $\mathrm{Re}>3\times10^5$ | $0.0308\,\mathrm{Re}_x^{4/5}\mathrm{Pr}^{1/3}$ | $0.0296\,\mathrm{Re}_x^{4/5}\mathrm{Pr}^{1/3}$ |

The flat-plate correlations are local; averaged over a laminar plate, $\overline{\mathrm{Nu}}_L=0.664\,\mathrm{Re}_L^{1/2}\mathrm{Pr}^{1/3}$. A cylinder in cross-flow uses $\overline{\mathrm{Nu}}=0.027\,\mathrm{Re}_D^{0.805}\mathrm{Pr}^{1/3}$ ($4\times10^4<\mathrm{Re}_D<4\times10^5$). Then $h=\mathrm{Nu}\,k/L$.

## Related

- Parent lectures: [[SESA3029 W09b - Convective Heat Transfer and the Reynolds Analogy#5. Correlations for the Nusselt number|W09b §§4–5]]
- Related concepts: [[Newton's Law of Cooling]] · [[Stanton Number]] · [[Prandtl Number]] · [[Reynolds Analogy]] · [[Reynolds Number]]

## Sources

- L5.3 slides 6–8, 10–15.
