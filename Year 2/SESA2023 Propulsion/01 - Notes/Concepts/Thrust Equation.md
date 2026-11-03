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

Thrust comes from a momentum balance on a control volume fixed to the engine, $\dot M_{x,out}-\dot M_{x,in} = \sum F_x$, which gives

$$
\text{Rocket: } F = \dot mV_j+A_j(P_j-P_A)\qquad\text{Air-breather: } F = \dot m_a\big[(1+f)V_j-V_0\big]+A_j(P_j-P_A) .
$$

$\dot m_a(1+f)V_j$ is the gross (momentum) thrust, $\dot m_aV_0$ the ram drag of the captured air, which a rocket doesn't have because it carries its oxidiser, and $A_j(P_j-P_A)$ the pressure thrust. The pressure thrust is zero for a fully expanded jet, positive when under-expanded and negative when over-expanded. Full expansion maximises the thrust for a given chamber state and mass flow, since $dF/dA_e = P_e-P_A$ vanishes at $P_e = P_A$, which is why nozzles are designed to expand fully at their design altitude. With $f\ll1$ and $P_j = P_A$, $F = \dot m_a(V_j-V_0)$, and the specific thrust is $V_j-V_0$. A rocket's thrust rises with altitude as $P_A\to0$; if the nozzle is choked, so its flow doesn't change, $F_{vac} = F_{sl}+A_eP_{A,sl}$.

For a two-stream turbofan the thrust is

$$
F = \dot m_c\big[(1+f)V_{jc}-V\big]+\dot m_b(V_{jb}-V)\;\Rightarrow\;\frac{F}{\dot m_c} = (1+f)V_{jc}+BPR\,V_{jb}-(1+BPR)V,
$$

the ideal turbofan specific thrust asked for in 2016-17 and 2018-19.

Worked values: an H₂/O₂ rocket giving 2000 kN at sea level gives 2318 kN in vacuum with $A_e = 3.14$ m² ([[SESA2023 Problem Sheet 1 Solutions]] Q1.1). A Boeing 777 in cruise has $F = 1295(299-251) = 62.2$ kN ([[SESA2023 W01 - Thrust, Efficiency, Range and the ISA]]). In [[SESA2023 Exam 2021-22 Solutions]] Q1(iii), a choked converging nozzle with 1 bar back pressure gets 1.46 kN of momentum thrust plus 0.87 kN of pressure thrust.

## Related

- [[Propulsive Efficiency]] · [[Rocket Performance Parameters]] · [[Converging-Diverging Nozzle Operating Regimes]]
