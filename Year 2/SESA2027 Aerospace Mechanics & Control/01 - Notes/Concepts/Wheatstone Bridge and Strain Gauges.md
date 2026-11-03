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
sources: ["02 - Sources/Lectures/Lecture 3.02.pdf", "Bentley, Ch. 8–9"]
---

# Wheatstone Bridge and Strain Gauges

A **strain gauge** is a resistive element whose resistance $R = \rho L/A$ rises when it is stretched, $\Delta R/R = G\varepsilon$ with gauge factor $G\approx2$. The change is tiny, so it is read with a **Wheatstone bridge**:

$$
V_G = \left(\frac{R_2}{R_1+R_2}-\frac{R_4}{R_3+R_4}\right)V_s .
$$

With all four resistances equal the bridge is balanced and $V_G = 0$, which is what makes it so sensitive to changes. For a quarter bridge (one active gauge) and a small change, $\Delta R/R\approx4V_G/V_s$, so $V_G = \tfrac{V_s}{4}G\varepsilon$; the exact form with $R_3 = R_4$ is $R_2 = R_1(V_s-2V_G)/(V_s+2V_G)$. In PS C Q2, $V_s = 5$ V, $V_G = 3$ mV and $G = 2.1$ give $\Delta R/R = 2.40\times10^{-3}$ ($\Delta R = 0.288$ Ω on 120 Ω) and $\varepsilon = 1.14\times10^{-3}$ ([[SESA2027 Part C Problem Sheet Solutions]]).

What the gauge actually measures is resistance; the strain is inferred. It is a zeroth-order sensor, instantaneous and with no smoothing. It is also sensitive to temperature, since $\rho(T)$ and differential expansion produce false strain. A half bridge, with a second gauge in the adjacent arm, cancels the temperature change in the ratio, and if that second gauge is in compression on a bending beam the two strain signals add, doubling the sensitivity to $V_G\approx\tfrac{V_s}{2}G\varepsilon$. A full bridge with four active gauges gives four times the quarter-bridge sensitivity with full compensation. Typical aircraft uses are wing-root strain monitoring and load measurement during manoeuvres.

## Related

- Quarter and half bridges derived, with worked numbers: [[SESA2027 C1 - Sensing Systems, Sensor Principles and Sensor Fusion#4.1 Resistive: strain gauges and the Wheatstone bridge|C1 §4.1]]
- [[Measurement Chain]] · [[Sensor Dynamic Models]]
- Year 1: [[Gauge Factor]] · [[Strain Gauge Bridge Configurations]] · [[FEEG1004 E3 - Strain Gauges, Bridges, Pressure and Flow Sensors]]
