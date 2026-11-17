---
title: "Stanton Number"
module: "SESA3029 Aerothermodynamics"
type: concept
stream: "Block 5: Heat transfer"
aliases: ["St", "Stanton number"]
tags: [sesa3029, concept, heat-transfer, convection, dimensionless-numbers]
status: complete
parent_lectures: ["[[SESA3029 W09b - Convective Heat Transfer and the Reynolds Analogy]]"]
related_concepts: ["[[Nusselt Number]]", "[[Reynolds Analogy]]", "[[Prandtl Number]]"]
sources: ["02 - Sources/Lectures/Lecture5.3.pdf"]
---

# Stanton Number

The Stanton number is the ratio of the heat transferred to a fluid to the heat capacity of the fluid stream, $\mathrm{St}=h/(\rho Vc_p)$.

Multiplying top and bottom by the temperature difference shows the meaning: $h\,\Delta T$ is the wall heat flux and $\rho Vc_p\,\Delta T$ is the enthalpy flux a stream of speed $V$ would carry if its whole temperature changed by $\Delta T$. It contains no length, which makes it the natural partner of the skin friction coefficient. Writing out the product of the groups and cancelling $\rho V$, $c_p$ and $\mu$ gives

$$
\mathrm{St}=\frac{\mathrm{Nu}}{\mathrm{Re}\,\mathrm{Pr}}.
$$

The [[Reynolds Analogy]] states $\mathrm{St}=c_f/2$ for $\mathrm{Pr}=1$ and $\mathrm{St}\,\mathrm{Pr}^{2/3}=c_f/2$ (Chilton–Colburn) for gases and liquids with $0.6<\mathrm{Pr}<60$. On a laminar flat plate this gives $\mathrm{St}_x=0.332\,\mathrm{Re}_x^{-1/2}\mathrm{Pr}^{-2/3}$.

## Related

- Parent lectures: [[SESA3029 W09b - Convective Heat Transfer and the Reynolds Analogy#4. Nusselt and Stanton numbers|W09b §4]] · [[SESA3029 W09b - Convective Heat Transfer and the Reynolds Analogy#7. The Reynolds analogy|W09b §7]]
- Related concepts: [[Nusselt Number]] · [[Reynolds Analogy]] · [[Prandtl Number]]

## Sources

- L5.3 slide 6.
