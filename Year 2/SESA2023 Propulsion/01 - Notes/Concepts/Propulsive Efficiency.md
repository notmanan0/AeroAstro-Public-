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

## Definition

> [!note] Definition
> $$\eta_P = \frac{\text{power to aircraft}}{\text{power to jet}} = \frac{FV_0}{\tfrac12\dot m_a\big[(1+f)V_j^2-V_0^2\big]}\;\xrightarrow{P_j = P_A,\ f\ll1}\;\frac{2}{1+V_j/V_0}$$

## Explanation
- The kinetic energy left behind in the wake, $\tfrac12\dot m(V_j-V_0)^2$ per second (seen from the ground), is **wasted**. So $\eta_P\to1$ as $V_j\to V_0$.
- But $F = \dot m_a(V_j-V_0)$, so as $V_j\to V_0$ the thrust vanishes. **High $\eta_P$ at fixed thrust needs a large $\dot m_a$ and a small $\Delta V$.** This single idea drives turbofans, high bypass ratio, turboprops, open rotors, distributed electric fans and boundary-layer ingestion.
- A derivation is required in 2014-15 Q1(ii) and 2015-16 Q1(iv):
  - The numerator is the **useful** thrust power, force × flight speed.
  - The denominator is the **rate of increase of jet KE**.
  - Then set $P_j = P_A$ and $f\ll1$, and factorise $V_j^2-V_0^2 = (V_j-V_0)(V_j+V_0)$.
- The effect of $f$ is small. In PS1 Q1.4 ($f = 0.0036$) the error is 0.15 percentage points, and it grows by about 0.37 points per 0.01 of $f$.
- The data book's "fuel efficiency" $\eta_f$ is the same as the thermal efficiency $\eta_{th}$ in these notes.

![[prop_propulsive_efficiency.png|640]]

## Examples
- Turbojet PS8 Q8.2: $V_j = 975$ m/s at $V = 231$ m/s gives $\eta_P = 0.38$.
- Turbofan fpr 1.5: $V_j = 340$ m/s gives $\eta_P = 0.81$ ([[SESA2023 Problem Sheet 8 Turbofans Solutions]]).
- Turbofan bpr 10, fpr 1.5 at M 0.8: $\eta_P = 0.816$ ([[SESA2023 Exam 2021-22 Solutions]] Q3).
- Ramjet 2024-25: $\eta_P = 0.649$.

## Related
- [[Thermal and Overall Efficiency]] · [[Thrust Equation]] · [[Bypass Ratio and Fan Pressure Ratio]] · [[Actuator Disk Theory]]

## Sources
- Week 1 notes §1.4.1; Lectures 3, 16, 20
