---
title: "Rocket Staging"
module: "SESA2023 Propulsion"
type: concept
stream: "Section 5: Rockets"
aliases: ["multistage rocket", "staging", "payload ratio", "serial staging", "parallel staging"]
tags: [sesa2023, concept, rockets]
status: complete
parent_lectures: ["[[SESA2023 W10 - Rocket Performance, Staging and Power Cycles]]"]
related_concepts: ["[[Tsiolkovsky Rocket Equation]]", "[[Rocket Performance Parameters]]"]
sources: ["02 - Sources/Lectures/Week 10 - Rockets.pdf"]
---

# Rocket Staging

Staging means discarding the empty structure of spent stages on the way up. Each stage carries the rest of the vehicle as its payload:

$$
(m_{pl})_i = (m_0)_{i+1},\qquad\lambda_i = e^{-\Delta V_i/c_{e,i}}-\delta_i,\qquad\lambda_0 = \prod\lambda_i,\qquad\Delta V_0 = \sum\Delta V_i .
$$

The calculation starts from the final payload and works down the stack with $(m_0)_i = (m_{pl})_i/\lambda_i$. Staging works because the rocket equation's penalty on dead weight is logarithmic and compounding, so dropping tanks and engines restores a high mass ratio for the next stage. The biggest gain is in going from one stage to two; further stages give diminishing returns and add complexity, cost and failure modes, and the optimum number depends on $\Delta V/c_e$ and $\delta$. In PS10 Q10.2 ($\Delta V = 14.3$ km/s, $c_e = 4115$ m/s, $\delta = 0.03$, 9 t payload) a single stage would need 9385 t ($\lambda = 0.00096$), but two equal stages need only 422.5 t. The Saturn V has $\Delta V_0 = 13{,}433$ m/s and $\lambda_0 = 0.0148$; as a single stage it would reach only 10.7 km/s, or need 5706 t for the same $\Delta V$.

The $\delta$ model needs care, though. Because $\delta$ is a fraction of each stage's initial mass, the gain can be small for a modest $\Delta V$. In 2024-25 Q2(iii), two stages at 2.5 km/s each ($\lambda_i = 0.4876$, $m_{02} = 4.10$ t, $m_{01} = 8.41$ t) need less propellant than one stage (5.41 t against 5.60 t) but have a slightly higher lift-off mass (8.41 t against 8.26 t), because of the extra structure.

Serial stages burn in sequence, while parallel strap-on boosters burn alongside the core at lift-off. The legacy question on choosing a launch vehicle (2015-16 Q2(ii)) expects payload mass and orbit ($\Delta V$), reliability and heritage, cost per kg, fairing size, launch site and inclination, schedule, the launch environment (g-loads, vibration, acoustics) and insurance.

![[prop_rocket_staging.png|600]]

## Related

- [[Tsiolkovsky Rocket Equation]] · [[Rocket Performance Parameters]]
