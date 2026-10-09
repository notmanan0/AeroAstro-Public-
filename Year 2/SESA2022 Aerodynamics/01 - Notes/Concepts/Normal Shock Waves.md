---
title: "Normal Shock Waves"
module: "SESA2022 Aerodynamics"
type: concept
stream: "Legacy syllabus: Compressible Flow (now SESA2023)"
aliases: ["normal shock", "Prandtl relation", "shock in nozzle", "stagnation pressure loss"]
tags: [sesa2022, sesa2023, concept, compressible-flow]
status: complete
parent_lectures: ["[[SESA2023 W03 - Compressible Flow, Normal Shocks and Nozzles]]"]
related_concepts: ["[[Isentropic Nozzle Flow]]"]
sources: ["03 - Exams & Past Papers (2013-14 to 2019-20)"]
---

# Normal Shock Waves

> [!info] Legacy SESA2022 content (papers up to 2019-20). It is now taught in SESA2023 Propulsion.

## Definition

> [!note] Definition
> A thin, irreversible, adiabatic discontinuity normal to the flow. Across it supersonic flow becomes subsonic, $p$, $\rho$ and $T$ rise, $T_0$ stays constant, and **$p_0$ falls** (entropy rises).
>
> $$M_2^2 = \frac{1+\frac{\gamma-1}2M_1^2}{\gamma M_1^2-\frac{\gamma-1}2},\qquad \frac{\rho_2}{\rho_1} = \frac{(\gamma+1)M_1^2}{2+(\gamma-1)M_1^2},\qquad \frac{p_2}{p_1} = 1+\frac{2\gamma}{\gamma+1}(M_1^2-1)$$

## Explanation
- **Prandtl relation**: $V_1V_2 = a^{*2} = \dfrac{2a_0^2}{\gamma+1}$, i.e. $M_1^*M_2^* = 1$. Derive it by dividing momentum by continuity and using the energy equation in $a^*$ form.
- **Stagnation-pressure ratio** $p_{02}/p_{01}<1$, from the tables. It measures the loss.
- **Shock in a C–D nozzle** (standard procedure):
  1. From $A_s/A^*$ (supersonic branch), find $M_1$.
  2. From the shock tables, find $M_2$ and $p_{02}/p_{01}$.
  3. The new sonic reference area is $A_2^* = A^*/(p_{02}/p_{01})$, because $\dot m\propto p_0A^*$ is conserved.
  4. From $A_e/A_2^*$ (subsonic branch), find $M_e$. Then $p_e = p_{02}(p/p_0)_{M_e}$.
- **Pitot probe in supersonic flow** (blunt nose): the probe reads $p_{02}$ behind a normal shock. For $M = 4$, $p_{02}/p_1 = 21.1$.

## Examples
- Missile nose at $M = 4$: [[SESA2022 Exam 2016-17 Solutions]] Q3(i) (repeated in 2017-18 and 2018-19).
- Prandtl relation: [[SESA2022 Exam 2014-15 Solutions]] and [[SESA2022 Exam 2015-16 Solutions]].
- Shock in a nozzle: [[SESA2022 Exam 2013-14 Solutions]], [[SESA2022 Exam 2014-15 Solutions]] and [[SESA2022 Exam 2019-20 Solutions]].

## SESA2023 usage
This note is shared with [[SESA2023 Propulsion Hub|SESA2023 Propulsion]], where normal shocks are taught in [[SESA2023 W03 - Compressible Flow, Normal Shocks and Nozzles]].
- Lecture example: $M_1 = 2$ at 250 K and 0.5 bar gives $M_2 = 0.577$, $p_2 = 2.25$ bar and $p_{02} = 2.82$ bar, with $T_0 = 450$ K conserved.
- Oblique shocks: use $M_1\sin\sigma$ in these relations. See [[Oblique Shock Waves]].
- Exams:
  - [[SESA2023 Exam 2020-21 Solutions]] Q1: argon, $\gamma = 1.67$.
  - [[SESA2023 Exam 2022-23 Solutions]] Q1: $M_1$ from the pressure ratio.
  - [[SESA2023 Exam 2024-25 Solutions]] Q1(iv): $M_2$ against $M_1$.
  - [[SESA2023 Problem Sheet 4 Solutions]] Q4.3: a ramjet inlet shock.

![[prop_normal_shock.png|640]]

## Related
- Related concepts: [[Isentropic Nozzle Flow]]
- Now taught in: [[SESA2023 Propulsion Hub|SESA2023 Propulsion]]

## Sources
- SESA2022 past papers 2013-14 to 2019-20
