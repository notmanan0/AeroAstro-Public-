---
title: "Propulsive Efficiency"
module: "SESA2023 Propulsion"
type: concept
stream: "Section 1: Introduction and Fundamentals"
aliases: ["eta_P", "Froude efficiency"]
tags: [sesa2023, concept, efficiency]
status: complete
parent_lectures: ["[[SESA2023 W01 - Thrust, Efficiency, Range and the ISA]]", "[[SESA2023 W07 - Turbofan Architectures and Fan Pressure Ratio Selection]]"]
related_concepts: ["[[Thermal and Overall Efficiency]]", "[[Thrust Equation]]", "[[Bypass Ratio and Fan Pressure Ratio]]", "[[Actuator Disk Theory]]"]
sources: ["02 - Sources/Lectures/Week 01 - Introduction and Fundamentals.pdf", "02 - Sources/Lectures/Week 06-07 - Jet Engines.pdf"]
---

# Propulsive Efficiency

**Propulsive efficiency** is the fraction of the power put into the jet that reaches the aircraft as thrust power:

$$
\eta_P = \frac{FV_0}{\tfrac12\dot m_a\big[(1+f)V_j^2-V_0^2\big]}\;\xrightarrow{P_j = P_A,\ f\ll1}\;\frac{2}{1+V_j/V_0} .
$$

The kinetic energy left behind in the wake, $\tfrac12\dot m(V_j-V_0)^2$ per second seen from the ground, is wasted, so $\eta_P\to1$ as $V_j\to V_0$. But the thrust is $F = \dot m_a(V_j-V_0)$, which vanishes in the same limit, so high propulsive efficiency at a fixed thrust needs a large mass flow and a small velocity increase. That one idea drives turbofans and high bypass ratios, turboprops, open rotors, distributed electric fans and boundary-layer ingestion.

The derivation is asked in 2014-15 Q1(ii) and 2015-16 Q1(iv). The numerator is the useful thrust power, force times flight speed, and the denominator the rate of increase of the jet's kinetic energy; with $P_j = P_A$ and $f\ll1$, factorising $V_j^2-V_0^2 = (V_j-V_0)(V_j+V_0)$ gives the simple form. The fuel mass makes little difference: in PS1 Q1.4, $f = 0.0036$ changes $\eta_P$ by 0.15 percentage points, and the error grows by about 0.37 points per 0.01 of $f$. The Data Book's "fuel efficiency" $\eta_f$ is the thermal efficiency $\eta_{th}$ of these notes.

![[prop_propulsive_efficiency.png|640]]

Worked values: the PS8 Q8.2 turbojet, $V_j = 975$ m/s at $V = 231$ m/s, has $\eta_P = 0.38$; a turbofan at fpr 1.5 with $V_j = 340$ m/s reaches 0.81 ([[SESA2023 Problem Sheet 8 Turbofans Solutions]]); BPR 10 and fpr 1.5 at M 0.8 gives 0.816 ([[SESA2023 Exam 2021-22 Solutions]] Q3); the 2024-25 ramjet has 0.649.

## Related

- [[Thermal and Overall Efficiency]] · [[Thrust Equation]] · [[Bypass Ratio and Fan Pressure Ratio]] · [[Actuator Disk Theory]]
