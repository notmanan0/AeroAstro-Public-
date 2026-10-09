---
title: "Isentropic Nozzle Flow"
module: "SESA2022 Aerodynamics"
type: concept
stream: "Legacy syllabus: Compressible Flow (now SESA2023)"
aliases: ["area-velocity relation", "choked flow", "converging-diverging nozzle", "A/A*"]
tags: [sesa2022, sesa2023, concept, compressible-flow]
status: complete
parent_lectures: ["[[SESA2023 W03 - Compressible Flow, Normal Shocks and Nozzles]]", "[[SESA2023 W10 - Rocket Performance, Staging and Power Cycles]]"]
related_concepts: ["[[Normal Shock Waves]]"]
sources: ["03 - Exams & Past Papers (2013-14 to 2019-20)"]
---

# Isentropic Nozzle Flow

> [!info] This compressible-flow material appears in SESA2022 papers up to 2019-20. It is now taught in SESA2023 Propulsion.

## Definition

> [!note] Definition
> Steady, quasi-1D, adiabatic, inviscid (isentropic) duct flow of a perfect gas, governed by
>
> $$\frac{dA}{A} = (M^2-1)\frac{dV}{V},\qquad \frac{T_0}{T} = 1+\frac{\gamma-1}{2}M^2,\qquad \frac{p_0}{p} = \left(\frac{T_0}{T}\right)^{\frac{\gamma}{\gamma-1}},\qquad \frac{A}{A^*} = \frac1M\left[\frac{2}{\gamma+1}\left(1+\frac{\gamma-1}{2}M^2\right)\right]^{\frac{\gamma+1}{2(\gamma-1)}}$$

## Explanation
- **Area–velocity relation**: derived from continuity, Euler ($dp = -\rho V\,dV$) and isentropy ($dp = a^2d\rho$).
  - Subsonic flow accelerates in a converging duct.
  - Supersonic flow accelerates in a diverging duct.
  - $M = 1$ only at a throat.
  - A C–D nozzle is needed to reach supersonic speed.
- **$A/A^*$** is double-valued. There is one subsonic and one supersonic Mach number for each area ratio, so choose the branch from the physics.
- **Choked mass flow** (throat at $M = 1$):

$$
\dot m = \frac{p_0A^*}{\sqrt{T_0}}\sqrt{\frac\gamma R\left(\frac{2}{\gamma+1}\right)^{\frac{\gamma+1}{\gamma-1}}}\quad(=0.0404\,p_0A^*/\sqrt{T_0}\text{ for air})
$$

  Lowering the back pressure can't increase it.
- **Design exit**: $A_e/A^*$ with the supersonic branch gives $M_e$. With a shock inside the nozzle, see [[Normal Shock Waves]].

## Examples
- $A = 1+x^2$ nozzle: [[SESA2022 Exam 2013-14 Solutions]] and [[SESA2022 Exam 2014-15 Solutions]] Q4.
- Choked-flow derivation: [[SESA2022 Exam 2015-16 Solutions]] Q3(ii).
- Area–velocity derivation: [[SESA2022 Exam 2016-17 Solutions]] Q3(ii).
- Nozzle with a shock: [[SESA2022 Exam 2019-20 Solutions]] Q4(i).

## SESA2023 usage
This note is shared with [[SESA2023 Propulsion Hub|SESA2023 Propulsion]], taught in [[SESA2023 W03 - Compressible Flow, Normal Shocks and Nozzles]].
- The eight back-pressure regimes: [[Converging-Diverging Nozzle Operating Regimes]].
- Choking and mass flow: [[Critical Conditions and Choked Flow]].
- Rocket nozzles: [[SESA2023 W10 - Rocket Performance, Staging and Power Cycles]].
- Worked sheets and exams: [[SESA2023 Problem Sheet 3 Solutions]], [[SESA2023 Exam 2021-22 Solutions]] Q1, [[SESA2023 Exam 2022-23 Solutions]] Q2.

![[prop_area_mach.png|600]]

## Related
- Related concepts: [[Normal Shock Waves]]
- Now taught in: [[SESA2023 Propulsion Hub|SESA2023 Propulsion]]

## Sources
- SESA2022 past papers 2013-14 to 2019-20
