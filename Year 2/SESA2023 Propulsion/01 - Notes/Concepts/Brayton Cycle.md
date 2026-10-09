---
title: "Brayton Cycle"
module: "SESA2023 Propulsion"
type: concept
stream: "Section 3: Ramjets, Gas Turbines, Turbojets and Turbofans"
aliases: ["Joule cycle", "gas turbine cycle", "cycle efficiency", "specific work", "optimum pressure ratio"]
tags: [sesa2023, concept, cycle-analysis]
status: complete
parent_lectures: ["[[SESA2023 W06 - Jet Engine Cycle Analysis - Brayton, Ramjet, Turbojet and Reheat]]"]
related_concepts: ["[[Turbojet]]", "[[Isentropic Efficiency]]", "[[Turbine Entry Temperature and Blade Cooling]]", "[[Thermal and Overall Efficiency]]"]
sources: ["02 - Sources/Lectures/Week 06-07 - Jet Engines.pdf"]
---
# Brayton Cycle

## Definition

> [!note] Definition
> The ideal cold-air-standard **Brayton (Joule) cycle** is isentropic compression, isobaric heating, isentropic expansion and isobaric cooling of a perfect gas ($c_p = 1005$, $\gamma = 1.4$):
>
> $$\eta_{th} = \frac{w_{net}}{q_{in}} = 1-\frac{1}{r_p^{(\gamma-1)/\gamma}}$$

## Explanation
- **Ideal cycle**: the efficiency depends **only on $r_p$**, not on the turbine entry temperature. At $r_p = 30$ it is 62.2 %; at 45 it is 66.3 %.
- **Irreversible cycle** ($\eta_c,\eta_t<1$):
  - Efficiency now **depends on $T_{04}/T_{02}$** and has an **optimum $r_p$** that rises with the temperature ratio.
  - The net specific work, $w_t-w_c$, peaks at a much **lower** $r_p$, near $\sqrt{(T_{04}/T_{02})^{\gamma/(\gamma-1)}}$ for the ideal cycle.
  - So fighters, which prioritise thrust, use $r_p\approx15$. Airliners, which prioritise sfc, use about 45.
- Raising **$T_{04}/T_{02}$** improves both $\eta$ and $w_{net}$. Irreversibility penalties are worst at high $r_p$, because more lossy compression and expansion is needed per unit of net work.
- **Open-cycle jets**: there is no net shaft work per spool. The "net work" appears as jet kinetic energy. Ram compression adds to the cycle pressure ratio, and part of the expansion happens in the (isentropic) nozzle, which is why a flying turbojet beats the closed irreversible cycle in Table 2.
- **Where reality departs**: pressure losses, variable $c_p$, product $c_p$, fuel mass, cooling air and power off-takes. See [[SESA2023 W06 - Jet Engine Cycle Analysis - Brayton, Ramjet, Turbojet and Reheat]] §3.

![[prop_brayton_trends.png|700]]

## Examples
PS7 Q7.3, with $\eta_c = \eta_t = 0.9$:

| Case | $T_{02}$ (K) | $T_{04}$ (K) | $r_p$ | $\eta_{th}$ | $w_{net}$ (kJ/kg) |
|---|---|---|---|---|---|
| (a) sea level | 288 | 1750 | 45 | 0.498 | 417 |
| (b) hot day | 308 | 1750 | 45 | 0.483 | 373 |
| (c) top of climb | 245 | 1600 | 50 | 0.514 | 411 |
| (d) cruise | 245 | 1500 | 45 | 0.500 | 361 |
| (e) $\eta = 0.85$ | 245 | 1500 | 45 | 0.404 | 280 |

2022-23 Q3 power gas turbine: $T_{03} = 1650$ K, $T_{04} = 900$ K and $\eta = 0.9$ give $r_p = 17.0$ and $T_{02} = 687$ K.

## Related
- [[Turbojet]] · [[Isentropic Efficiency]] · [[Turbine Entry Temperature and Blade Cooling]] · [[Thermal and Overall Efficiency]]

## Sources
- Weeks 6–7 handout §6.4, §6.6–6.7; Lecture 17
