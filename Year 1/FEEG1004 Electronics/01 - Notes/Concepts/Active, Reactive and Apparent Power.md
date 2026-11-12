---
title: "Active, Reactive and Apparent Power"
module: "FEEG1004 Electronics"
type: concept
stream: "Part D: AC Circuit Analysis"
aliases: ["active power", "reactive power", "apparent power", "complex power", "S = VI*", "VAR", "VA", "power triangle", "power factor"]
tags: [feeg1004, concept, ac-circuits, power]
status: complete
parent_lectures: ["[[FEEG1004 D4 - AC Power and Power Factor]]"]
related_concepts: ["[[Power Factor Correction]]", "[[RMS Value]]"]
sources: ["02 - Sources/S2 AC Analysis/S2-W25 AC Analysis 04 - AC Power - Lecture Slides.pdf", "02 - Sources/S2 AC Analysis/S2 AC Analysis Lecture Notes 2021 - Niu.pdf"]
---

# Active, Reactive and Apparent Power

In a sinusoidal AC circuit the complex power $\mathbf S=\mathbf V\mathbf I^*=P+jQ$ splits into **active power** $P$, the average power actually delivered, and **reactive power** $Q$, the energy that surges back and forth between the source and the circuit's inductance and capacitance. Its magnitude $|\mathbf S|$ is the **apparent power**.

With rms magnitudes $V$ and $I$ and phase difference $\phi=\theta_v-\theta_i$,

$$
P=VI\cos\phi\ [\mathrm W],\qquad Q=VI\sin\phi\ [\mathrm{VAR}],\qquad |\mathbf S|=VI\ [\mathrm{VA}],\qquad \mathrm{pf}=\cos\phi=\frac{P}{|S|}.
$$

The active power is dissipated in resistance as $I^2R$. The reactive power is exchanged with inductors and capacitors every half-cycle and averages to zero: an inductor absorbs $Q=+I^2X_L$ and a capacitor generates, with $Q=-I^2X_C$. Both $P$ and $Q$ are conserved separately, so the totals for a circuit equal the sums over its elements. A **lagging** power factor indicates an inductive load and a **leading** one a capacitive load. The conjugate $\mathbf I^*$ in the definition matters: using $\mathbf I$ instead gives $Q$ with the wrong sign.

![[ee_d4_instantaneous_power.png|800]]

For example, $50\ \mathrm V$ across $6+j11.31\ \Omega$ gives $91.5\ \mathrm W$, $172.5\ \mathrm{VAR}$ and $195.3\ \mathrm{VA}$. The furnace in Tutorial 8 Q3 draws $45.7\ \mathrm{kW}$ and $71.8\ \mathrm{kVAR}$, a power factor of $0.54$.

## Related

- [[FEEG1004 D4 - AC Power and Power Factor]]
- [[Power Factor Correction]] · [[RMS Value]] · [[Three-Phase Star and Delta Connections]]
- Sources: AC Analysis 04 slides; Niu AC notes (Figs 27–35)
