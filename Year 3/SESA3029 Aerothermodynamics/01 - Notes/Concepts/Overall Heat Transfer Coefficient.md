---
title: "Overall Heat Transfer Coefficient"
module: "SESA3029 Aerothermodynamics"
type: concept
stream: "Block 5: Heat transfer"
aliases: ["overall heat transfer coefficient", "U-value", "overall conductance", "UA"]
tags: [sesa3029, concept, heat-transfer, heat-exchanger]
status: complete
parent_lectures: ["[[SESA3029 W09f - Heat Exchangers]]"]
related_concepts: ["[[Log Mean Temperature Difference]]", "[[Heat Exchanger Effectiveness and NTU]]", "[[Types of Heat Exchangers]]"]
sources: ["02 - Sources/Lectures/Lecture5.8(1).pdf", "02 - Sources/Lectures/Lecture5.10.pdf"]
---

# Overall Heat Transfer Coefficient

The overall heat transfer coefficient $U$ is the single coefficient that turns the whole chain of thermal resistances between two fluids into one Newton's-law expression, $\dot Q=UA_s\Delta T$.

Between the hot and cold fluids of a heat exchanger the heat crosses a convective film, the wall and a second convective film, three resistances in series ([[SESA3029 W09a - Heat Conduction and Thermal Resistance|W09a]]). For a tube of length $L$,

$$
\frac{1}{UA_s}=\frac{1}{U_iA_i}=\frac{1}{U_oA_o}=R_{\rm th}=\frac{1}{h_iA_i}+\frac{\ln(r_o/r_i)}{2\pi kL}+\frac{1}{h_oA_o}.
$$

Only the product $UA$ is unique; quoting $U$ means naming the area it goes with, the inner one ($U_i$) or the outer one ($U_o$). When the wall is thin and highly conducting, $R_{\rm wall}\approx0$ and $A_i\approx A_o=A_s$, which leaves the form used in every SESA3029 example:

$$
\frac1U\approx\frac{1}{h_i}+\frac{1}{h_o}\qquad(\text{thin wall}).
$$

Radiation effects are usually lumped into the two heat transfer coefficients. $U$ is always below the smaller $h$, and when the two differ greatly the smaller one controls it. In the concentric-tube oil–water exchanger of W09f §7, $h=2250$ W m⁻² K⁻¹ on the water side and $38.9$ on the oil side give $U=38.25$ W m⁻² K⁻¹, so the oil film carries 98 % of the resistance and that is the side to improve, with fins or a faster flow. In the power-plant condenser of the same section both films are good (7543 and 11 000 W m⁻² K⁻¹) and $U=4474$ W m⁻² K⁻¹.

In the ε–NTU method $U$ enters only through $\mathrm{NTU}=UA_s/C_{\min}$; in the LMTD method through $\dot Q=UA_s\Delta T_{\rm lm}$. Both assume $U$ is constant along the exchanger, which is why the fluid properties are evaluated at the mean temperature of each stream.

## Related

- Parent lecture: [[SESA3029 W09f - Heat Exchangers#1. The overall heat transfer coefficient|W09f §1]]
- Related concepts: [[Log Mean Temperature Difference]] · [[Heat Exchanger Effectiveness and NTU]] · [[Types of Heat Exchangers]]
- Resistances and convection coefficients: [[SESA3029 W09a - Heat Conduction and Thermal Resistance]] · [[SESA3029 W09b - Convective Heat Transfer and the Reynolds Analogy]]

## Sources

- `Lecture5.8(1).pdf`, slides 4–6; `Lecture5.10.pdf`, slides 5 and 9.
