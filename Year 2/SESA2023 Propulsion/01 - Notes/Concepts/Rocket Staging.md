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

## Definition

> [!note] Definition
> Discarding the empty structure of spent stages. Stage $i$ carries the rest of the vehicle as its payload:
>
> $$(m_{pl})_i = (m_0)_{i+1},\qquad\lambda_i = e^{-\Delta V_i/c_{e,i}}-\delta_i,\qquad\lambda_0 = \prod\lambda_i,\qquad\Delta V_0 = \sum\Delta V_i$$

## Explanation
- **Procedure**: start from the final payload and work **down** the stack. Use $(m_0)_i = (m_{pl})_i/\lambda_i$.
- **Why it works**: the rocket equation's penalty on dead weight is logarithmic and compounding. Dropping tanks and engines restores a high mass ratio for the next stage.
- The biggest gain is **from 1 to 2 stages**. More stages give diminishing returns and add complexity, cost and failure modes. The optimum number depends on $\Delta V/c_e$ and $\delta$.
- **Caveat on the $\delta$ model**: $\delta$ is a fraction of each stage's *initial* mass, so for modest $\Delta V$ the gain can be small. In 2024-25 Q2, the two-stage version needs **less propellant** (5.41 t against 5.60 t) but has a slightly **higher** lift-off mass (8.41 t against 8.26 t), because of the extra structure.
- **Serial vs parallel**: serial stages burn in sequence. Parallel strap-on boosters burn alongside the core at lift-off.
- **Launch vehicle selection** (legacy 2015-16 Q2(ii)):
  - payload mass and orbit ($\Delta V$);
  - reliability and heritage;
  - cost per kg;
  - fairing size;
  - launch site and inclination;
  - schedule;
  - environment (g-loads, vibration, acoustics);
  - insurance.

![[prop_rocket_staging.png|600]]

## Examples
- **PS10 Q10.2**: $\Delta V = 14.3$ km/s, $c_e = 4115$ m/s, $\delta = 0.03$, 9 t payload. One stage needs **9385 t** ($\lambda = 0.00096$). Two equal stages need **422.5 t**.
- **Saturn V**: $\Delta V_0 = 13{,}433$ m/s, $\lambda_0 = 0.0148$. A single stage reaches only 10.7 km/s, or would need 5706 t for the same $\Delta V$.
- **2024-25 Q2(iii)**: two stages at 2.5 km/s each, $\lambda_i = 0.4876$, $m_{02} = 4.10$ t, $m_{01} = 8.41$ t, total propellant 5.41 t.

## Related
- [[Tsiolkovsky Rocket Equation]] · [[Rocket Performance Parameters]]

## Sources
- Week 10 notes §10.3.3; Lecture 29
