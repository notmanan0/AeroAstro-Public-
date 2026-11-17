---
title: "Heat Capacity Rate"
module: "SESA3029 Aerothermodynamics"
type: concept
stream: "Block 5: Heat transfer"
aliases: ["heat capacity rate", "capacity rate", "thermal capacity rate", "capacity ratio", "heat capacity ratio", "C_min", "C_max"]
tags: [sesa3029, concept, heat-transfer, heat-exchanger]
status: complete
parent_lectures: ["[[SESA3029 W09f - Heat Exchangers]]"]
related_concepts: ["[[Heat Exchanger Effectiveness and NTU]]", "[[Log Mean Temperature Difference]]", "[[Steady-flow Energy Equation]]"]
sources: ["02 - Sources/Lectures/Lecture5.8(1).pdf", "02 - Sources/Lectures/Lecture5.9(1).pdf"]
---

# Heat Capacity Rate

The heat capacity rate of a fluid stream is $C=\dot mc_p$ (W K⁻¹), the rate of heat transfer needed to change the temperature of the stream by 1 °C.

It comes straight from the steady-flow energy balance on each stream of a heat exchanger with an insulated outer surface: $\dot Q=C_h(T_{h,\rm in}-T_{h,\rm out})=C_c(T_{c,\rm out}-T_{c,\rm in})$. Dividing the two forms shows that the temperature changes are in the inverse ratio of the capacity rates,

$$
\frac{T_{h,\rm in}-T_{h,\rm out}}{T_{c,\rm out}-T_{c,\rm in}}=\frac{C_c}{C_h},
$$

so a large-$C$ stream changes temperature little and a small-$C$ stream a lot. A condensing or boiling stream absorbs heat at constant temperature, the limit $C\to\infty$.

The smaller of the two, $C_{\min}$, sets the maximum possible heat transfer rate, $\dot Q_{\max}=C_{\min}(T_{h,\rm in}-T_{c,\rm in})$: only the $C_{\min}$ stream can change temperature by the whole inlet-to-inlet difference without the other overshooting the limit set by the opposite inlet. The **capacity ratio** $c=C_{\min}/C_{\max}$ (written $C_r$ in Bergman and Çengel) runs from 0, for a condenser or boiler, to 1, for balanced streams, and together with NTU fixes the effectiveness.

## Related

- Parent lecture: [[SESA3029 W09f - Heat Exchangers#3. Energy balance and the heat capacity rate|W09f §3]] · [[SESA3029 W09f - Heat Exchangers#5.1 Effectiveness and the maximum heat transfer rate|W09f §5.1]]
- Related concepts: [[Heat Exchanger Effectiveness and NTU]] · [[Log Mean Temperature Difference]] · [[Steady-flow Energy Equation]]

## Sources

- `Lecture5.8(1).pdf`, slides 9–10; `Lecture5.9(1).pdf`, slides 3–4 and 8.
