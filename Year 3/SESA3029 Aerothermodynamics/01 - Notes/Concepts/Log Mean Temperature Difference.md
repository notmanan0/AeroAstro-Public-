---
title: "Log Mean Temperature Difference"
module: "SESA3029 Aerothermodynamics"
type: concept
stream: "Block 5: Heat transfer"
aliases: ["LMTD", "log mean temperature difference", "log-mean temperature difference", "LMTD method", "logarithmic mean temperature difference"]
tags: [sesa3029, concept, heat-transfer, heat-exchanger, lmtd]
status: complete
parent_lectures: ["[[SESA3029 W09f - Heat Exchangers]]"]
related_concepts: ["[[Overall Heat Transfer Coefficient]]", "[[Heat Exchanger Effectiveness and NTU]]", "[[Types of Heat Exchangers]]", "[[Heat Capacity Rate]]"]
sources: ["02 - Sources/Lectures/Lecture5.8(1).pdf", "02 - Sources/Lectures/Lecture5.10.pdf"]
---

# Log Mean Temperature Difference

The log mean temperature difference is the mean hot-to-cold temperature difference that makes $\dot Q=UA_s\Delta T_{\rm lm}$ exact for a parallel- or counter-flow heat exchanger with constant $U$ and capacity rates:

$$
\Delta T_{\rm lm}=\frac{\Delta T_1-\Delta T_2}{\ln(\Delta T_1/\Delta T_2)} .
$$

$\Delta T_1$ and $\Delta T_2$ are the hot-minus-cold differences at the two ends of the exchanger. In parallel flow $\Delta T_1=T_{h,\rm in}-T_{c,\rm in}$ and $\Delta T_2=T_{h,\rm out}-T_{c,\rm out}$; in counter flow the hot inlet faces the cold outlet, so $\Delta T_1=T_{h,\rm in}-T_{c,\rm out}$ and $\Delta T_2=T_{h,\rm out}-T_{c,\rm in}$. The formula is symmetric in the two, so either end may be called 1.

It comes from an energy balance on an element $\mathrm dA_s$: $\delta\dot Q=U(T_h-T_c)\,\mathrm dA_s$ with $\mathrm dT_h=-\delta\dot Q/C_h$ and $\mathrm dT_c=\pm\delta\dot Q/C_c$ (+ in parallel flow, − in counter flow when $A_s$ runs from the hot inlet). Then $\mathrm d(T_h-T_c)/(T_h-T_c)$ is a constant times $\mathrm dA_s$, so the difference varies exponentially along the exchanger, and eliminating the capacity rates with the overall energy balance gives the same $\Delta T_{\rm lm}$ for both arrangements.

The log mean always lies below the arithmetic mean of the end differences and tends to $\Delta T$ when $\Delta T_1=\Delta T_2$ (balanced counter flow, or two constant-temperature streams). For the same four terminal temperatures counter flow has the larger LMTD and needs less area: 73.19 K against 54.61 K, 10.06 m² against 13.48 m², in the W09f sizing example. The method suits sizing, when all four temperatures are known or follow from the energy balance; when only the inlets are known, the [[Heat Exchanger Effectiveness and NTU|effectiveness–NTU method]] avoids iteration.

![[at_w09f_lmtd_vs_mean.png|760]]

## Related

- Parent lecture: [[SESA3029 W09f - Heat Exchangers#4. The log mean temperature difference method|W09f §4]]
- Related concepts: [[Overall Heat Transfer Coefficient]] · [[Heat Exchanger Effectiveness and NTU]] · [[Types of Heat Exchangers]] · [[Heat Capacity Rate]]
- Past paper: [[SESA3029 Past Paper 2022-23 - Solutions#Q5. Counterflow oil-water heat exchanger via LMTD (18 marks)|2022–23 Q5]]

## Sources

- `Lecture5.8(1).pdf`, slides 11–19; `Lecture5.10.pdf`, slides 5–6 and 11.
