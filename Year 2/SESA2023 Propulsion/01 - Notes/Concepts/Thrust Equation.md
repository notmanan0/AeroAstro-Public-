---
title: "Thrust Equation"
module: "SESA2023 Propulsion"
type: concept
stream: "Section 1: Introduction and Fundamentals"
aliases: ["momentum thrust", "pressure thrust", "ram drag", "gross thrust", "net thrust"]
tags: [sesa2023, concept, thrust]
status: complete
parent_lectures: ["[[SESA2023 W01 - Thrust, Efficiency, Range and the ISA]]", "[[SESA2023 W10 - Rocket Performance, Staging and Power Cycles]]"]
related_concepts: ["[[Propulsive Efficiency]]", "[[Rocket Performance Parameters]]", "[[Converging-Diverging Nozzle Operating Regimes]]"]
sources: ["02 - Sources/Lectures/Week 01 - Introduction and Fundamentals.pdf", "02 - Sources/Lectures/Week 10 - Rockets.pdf"]
---
# Thrust Equation

## Definition

> [!note] Definition
> Thrust comes from a momentum balance on a control volume fixed to the engine: $\dot M_{x,out}-\dot M_{x,in} = \sum F_x$.
>
> $$\text{Rocket: } F = \dot mV_j+A_j(P_j-P_A)\qquad\text{Air-breather: } F = \dot m_a\big[(1+f)V_j-V_0\big]+A_j(P_j-P_A)$$

## Explanation
- $\dot m_a(1+f)V_j$ is the **gross (momentum) thrust**.
- $\dot m_aV_0$ is the **ram drag** of the captured air. A rocket has none, because it carries its oxidiser.
- $A_j(P_j-P_A)$ is the **pressure thrust**. It is zero for a **fully expanded** jet ($P_j = P_A$). It is positive when under-expanded and negative when over-expanded.
- Full expansion **maximises** the thrust for a given chamber state and mass flow. Differentiating, $dF/dA_e = (P_e-P_A)$, which is zero at $P_e = P_A$. So nozzles are designed for full expansion at their design altitude.
- With $f\ll1$ and $P_j = P_A$: $F = \dot m_a(V_j-V_0)$. The **specific thrust** is $F/\dot m_a = V_j-V_0$.
- Rocket thrust rises with altitude as $P_A\to0$. In vacuum $F_{vac} = F_{sl}+A_eP_{A,sl}$ if the nozzle flow is unchanged (the nozzle is choked).
- **Turbofan with two streams**:

  $$F = \dot m_c\big[(1+f)V_{jc}-V\big]+\dot m_b(V_{jb}-V)\;\Rightarrow\;\frac{F}{\dot m_c} = (1+f)V_{jc}+BPR\,V_{jb}-(1+BPR)V$$

  This is the "ideal turbofan specific thrust" asked for in 2016-17 and 2018-19.

## Examples
- H₂/O₂ rocket: 2000 kN at sea level becomes **2318 kN** in vacuum ($A_e = 3.14$ m²). See [[SESA2023 Problem Sheet 1 Solutions]] Q1.1.
- Boeing 777 cruise: $F = 1295(299-251) = 62.2$ kN ([[SESA2023 W01 - Thrust, Efficiency, Range and the ISA]]).
- Pressure thrust included: [[SESA2023 Exam 2021-22 Solutions]] Q1(iii). A choked converging nozzle at 1 bar back pressure gets 1.46 kN of momentum thrust plus 0.87 kN of pressure thrust.

## Related
- [[Propulsive Efficiency]] · [[Rocket Performance Parameters]] · [[Converging-Diverging Nozzle Operating Regimes]]

## Sources
- Week 1 notes §1.2; Week 10 notes §10.2
