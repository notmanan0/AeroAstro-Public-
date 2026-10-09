---
title: "Wheatstone Bridge and Strain Gauges"
module: "SESA2027 Aerospace Mechanics & Control"
type: concept
stream: "Part C: Sensing Systems"
aliases: ["Wheatstone bridge", "strain gauge", "gauge factor", "quarter bridge", "half bridge"]
tags: [sesa2027, concept, sensors, structures]
status: complete
parent_lectures: ["[[SESA2027 C1 - Sensing Systems, Sensor Principles and Sensor Fusion]]"]
related_concepts: ["[[Measurement Chain]]", "[[Sensor Dynamic Models]]"]
sources: ["02 - Sources/Lectures/Lecture 3.02.pdf"]
---

# Wheatstone Bridge and Strain Gauges

## Definition

> [!note] Definition
> A **strain gauge** is a resistive element whose resistance, $R = \rho L/A$, rises when it is stretched: $\Delta R/R = G\varepsilon$, where $G\approx2$ is the gauge factor. The small $\Delta R$ is read with a **Wheatstone bridge**:
>
> $$V_G = \left(\frac{R_2}{R_1+R_2}-\frac{R_4}{R_3+R_4}\right)V_s$$
>
> For a quarter bridge with a small change: $\dfrac{\Delta R}{R}\approx\dfrac{4V_G}{V_s}$, so $V_G = \dfrac{V_s}{4}G\varepsilon$.

## Explanation
- **Balanced bridge** (all resistances equal): $V_G = 0$. The bridge measures *changes* very sensitively.
- **Quarter bridge** exact form: $R_2 = \dfrac{V_s-2V_G}{V_s+2V_G}R_1$ when $R_3 = R_4$.
- **We measure resistance, not strain**; the strain is inferred. A zeroth-order sensor: instantaneous, with no smoothing.
- **Temperature sensitivity**: $\rho(T)$ and differential expansion produce false strain.
- **Half bridge**: a second gauge in the adjacent arm. Temperature changes cancel in the ratio. With the second gauge in compression on a bending beam, the strain signals add, giving $V_G\approx\frac{V_s}{2}G\varepsilon$ (double the sensitivity).
- **Full bridge**: four active gauges give four times the quarter-bridge sensitivity, with full compensation.

## Examples
- PS C Q2: $V_s = 5$ V, $V_G = 3$ mV, $G = 2.1$ gives $\Delta R/R = 2.40\times10^{-3}$ ($\Delta R = 0.288$ Ω on 120 Ω) and $\varepsilon = 1.14\times10^{-3}$ ([[SESA2027 Part C Problem Sheet Solutions]]).
- Wing-root strain monitoring and load measurement during manoeuvres.

## Related
- [[Measurement Chain]] · [[Sensor Dynamic Models]]
- Year 1: [[Gauge Factor]] · [[Strain Gauge Bridge Configurations]] · [[FEEG1004 E3 - Strain Gauges, Bridges, Pressure and Flow Sensors]]

## Sources
- Lecture 3.02; Bentley, Ch. 8–9
