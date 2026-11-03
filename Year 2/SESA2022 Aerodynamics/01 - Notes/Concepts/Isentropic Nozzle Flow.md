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

Isentropic nozzle flow is steady, quasi-one-dimensional, adiabatic and inviscid duct flow of a perfect gas, governed by

$$
\frac{dA}{A} = (M^2-1)\frac{dV}{V},\qquad \frac{T_0}{T} = 1+\frac{\gamma-1}{2}M^2,\qquad \frac{p_0}{p} = \left(\frac{T_0}{T}\right)^{\frac{\gamma}{\gamma-1}},\qquad \frac{A}{A^*} = \frac1M\left[\frac{2}{\gamma+1}\left(1+\frac{\gamma-1}{2}M^2\right)\right]^{\frac{\gamma+1}{2(\gamma-1)}} .
$$

This material appears in SESA2022 papers up to 2019-20 and is now taught in SESA2023 Propulsion.

The area–velocity relation comes from continuity, Euler's equation $dp = -\rho V\,dV$ and isentropy $dp = a^2d\rho$. Subsonic flow accelerates in a converging duct and supersonic flow in a diverging one, so $M = 1$ can occur only at a throat, and reaching supersonic speed needs a converging–diverging nozzle. $A/A^*$ is double-valued, with one subsonic and one supersonic Mach number for each area ratio, so the branch has to be chosen from the physics; the design exit Mach number comes from $A_e/A^*$ on the supersonic branch. Once the throat is at $M = 1$ the nozzle is choked,

$$
\dot m = \frac{p_0A^*}{\sqrt{T_0}}\sqrt{\frac\gamma R\left(\frac{2}{\gamma+1}\right)^{\frac{\gamma+1}{\gamma-1}}}\quad(=0.0404\,p_0A^*/\sqrt{T_0}\text{ for air}),
$$

and lowering the back pressure can't increase the mass flow. A shock inside the nozzle is covered in [[Normal Shock Waves]].

![[prop_area_mach.png|600]]

SESA2022 past-paper uses: the $A = 1+x^2$ nozzle ([[SESA2022 Exam 2013-14 Solutions]], [[SESA2022 Exam 2014-15 Solutions]] Q4); the choked-flow derivation ([[SESA2022 Exam 2015-16 Solutions]] Q3(ii)); the area–velocity derivation ([[SESA2022 Exam 2016-17 Solutions]] Q3(ii)); a nozzle with a shock ([[SESA2022 Exam 2019-20 Solutions]] Q4(i)).

In SESA2023 the topic is taught in [[SESA2023 W03 - Compressible Flow, Normal Shocks and Nozzles]], with the eight back-pressure regimes in [[Converging-Diverging Nozzle Operating Regimes]], choking in [[Critical Conditions and Choked Flow]] and rocket nozzles in [[SESA2023 W10 - Rocket Performance, Staging and Power Cycles]]. Worked practice: [[SESA2023 Problem Sheet 3 Solutions]], [[SESA2023 Exam 2021-22 Solutions]] Q1 and [[SESA2023 Exam 2022-23 Solutions]] Q2.

## Related

- [[Normal Shock Waves]] · [[SESA2023 Propulsion Hub|SESA2023 Propulsion]]
