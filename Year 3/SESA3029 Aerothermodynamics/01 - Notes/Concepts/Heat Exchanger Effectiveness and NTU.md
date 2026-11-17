---
title: "Heat Exchanger Effectiveness and NTU"
module: "SESA3029 Aerothermodynamics"
type: concept
stream: "Block 5: Heat transfer"
aliases: ["effectiveness", "heat exchanger effectiveness", "thermal effectiveness", "NTU", "number of heat transfer units", "number of transfer units", "effectiveness-NTU method", "ε-NTU method", "epsilon-NTU method", "NTU method"]
tags: [sesa3029, concept, heat-transfer, heat-exchanger, ntu]
status: complete
parent_lectures: ["[[SESA3029 W09f - Heat Exchangers]]"]
related_concepts: ["[[Heat Capacity Rate]]", "[[Log Mean Temperature Difference]]", "[[Overall Heat Transfer Coefficient]]", "[[Types of Heat Exchangers]]"]
sources: ["02 - Sources/Lectures/Lecture5.9(1).pdf", "02 - Sources/Lectures/Lecture5.10.pdf"]
---

# Heat Exchanger Effectiveness and NTU

The effectiveness $\epsilon=\dot Q/\dot Q_{\max}$ is the fraction of the maximum possible heat transfer rate that a heat exchanger achieves, and the number of heat transfer units $\mathrm{NTU}=UA_s/C_{\min}$ is the dimensionless size of the exchanger that, with the capacity ratio $c=C_{\min}/C_{\max}$, determines it.

The maximum rate is $\dot Q_{\max}=C_{\min}(T_{h,\rm in}-T_{c,\rm in})$: only the stream with the smaller [[Heat Capacity Rate|heat capacity rate]] can change temperature by the full inlet-to-inlet difference. Since only the inlet temperatures enter, the method gives $\dot Q=\epsilon C_{\min}(T_{h,\rm in}-T_{c,\rm in})$ and then the outlets without any iteration, which is its advantage over the [[Log Mean Temperature Difference|LMTD method]] when the outlets are unknown. NTU is proportional to the surface area for given $U$ and $C_{\min}$.

Integrating the element energy balance and writing the outlets in terms of $\epsilon$ gives, for the two concentric-tube arrangements,

$$
\epsilon_{\text{parallel-flow}}=\frac{1-\exp\left[-\mathrm{NTU}(1+c)\right]}{1+c},\qquad
\epsilon_{\text{counter-flow}}=\frac{1-\exp\left[-\mathrm{NTU}(1-c)\right]}{1-c\exp\left[-\mathrm{NTU}(1-c)\right]} ,
$$

independent of which fluid is $C_{\min}$. The limits carry the physics. With $c=0$ (a condensing or boiling stream) every arrangement gives $\epsilon=1-e^{-\mathrm{NTU}}$. Balanced counter flow, $c=1$, makes the formula $0/0$, but direct integration with a constant temperature difference gives $\epsilon=\mathrm{NTU}/(1+\mathrm{NTU})$. As $\mathrm{NTU}\to\infty$ parallel flow saturates at $1/(1+c)$ while counter flow tends to 1; as $\mathrm{NTU}\to0$ both give $\epsilon\approx\mathrm{NTU}$.

Effectiveness rises steeply at small NTU and slowly at large NTU, so the last few per cent cost a disproportionate amount of area. For a given NTU and $c$ counter flow is the most effective arrangement and parallel flow the least. Worked values from W09f: the rating example has $\mathrm{NTU}=1.093$, $c=0.5$, $\epsilon=0.593$; the condenser has $\mathrm{NTU}=0.759$, $c=0$, $\epsilon=0.532$.

![[at_w09f_effectiveness_ntu.png|760]]

## Related

- Parent lecture: [[SESA3029 W09f - Heat Exchangers#5. Effectiveness and the number of heat transfer units|W09f §5]] · [[SESA3029 W09f - Heat Exchangers#Worked example: shell-and-tube condenser|the condenser example]]
- Related concepts: [[Heat Capacity Rate]] · [[Log Mean Temperature Difference]] · [[Overall Heat Transfer Coefficient]] · [[Types of Heat Exchangers]]
- Practice: [[SESA3029 Example Sheet 3 - Solutions#Q5. Parallel-flow heat exchanger|ES3 Q5]] · [[SESA3029 Past Paper 2023-24 - Solutions#Q4. Steam-condensing shell-and-tube heat exchanger (20 marks)|2023–24 Q4]]

## Sources

- `Lecture5.9(1).pdf`, slides 2–17; `Lecture5.10.pdf`, slides 9–10.
