---
title: "Spacecraft Thermal Balance Equation"
module: "SESA2024 Astronautics"
type: concept
stream: "Spacecraft Subsystems"
aliases: ["thermal balance", "equilibrium temperature", "albedo", "Earth IR", "heat inputs and outputs"]
tags: [sesa2024, concept, thermal-control]
status: complete
parent_lectures: ["[[SESA2024 10 - Thermal Control]]"]
related_concepts: ["[[Absorptance and Emittance]]", "[[Blackbody Radiation]]", "[[Passive vs Active Thermal Control]]", "[[Eclipse Duration]]"]
sources: ["02 - Sources/Lectures/Chapter 10/2025 WEEK 8 - Chapter 10 - Thermal Control - Lecture slides - complete.pdf"]
---

# Spacecraft Thermal Balance Equation

## Definition

> [!note] Definition
>
> $$\underbrace{q_S\alpha_SA_S^{proj}}_{\text{Sun}}+\underbrace{aq_S\alpha_SA_E^{proj}\cos\phi\,\beta F}_{\text{albedo}}+\underbrace{q_E\varepsilon A_E^{proj}F}_{\text{Earth IR}}+\underbrace{P}_{\text{dissipation}} = \underbrace{\varepsilon\sigma T^4A_{surf}}_{\text{emission}},\qquad F = \Big(\frac{R_E}{R_{orb}}\Big)^2$$

## Explanation
- **Constants**: $q_S\approx1350$–1400 W/m², $a\approx0.34$, $q_E\approx240$ W/m², $\sigma = 5.67\times10^{-8}$ W m⁻² K⁻⁴.
- **$\phi$** is the Earth-centred angle between the spacecraft and the subsolar point. $\beta = 1$ on the dayside ($|\phi|<90^\circ$), otherwise 0. **Albedo is zero at the terminator and on the nightside.**
- **$A^{proj}$**: projected area towards the Sun or Earth. **$A_{surf}$**: total radiating area.
- **Kirchhoff**: the Earth's IR is absorbed with $\alpha_{IR} = \varepsilon$.
- **Assumptions**: isothermal; area-weighted effective $\alpha_S$ and $\varepsilon$; simplified view factor $F$; equilibrium (steady state).
- **Standard cases**:
  1. **Noon** (subsolar): Sun + albedo ($\phi = 0$) + IR.
  2. **Terminator**: Sun + IR (albedo zero).
  3. **Eclipse**: IR + $P$ only.
- **Decoupled planar array** (both faces radiate): output $= \sigma T^4(\varepsilon_f+\varepsilon_b)A$. Sunlight falls on the front ($\alpha_{sf}$). Earth hits the back at noon and the front at midnight.
- **Eclipse, $P = 0$**: $T^4 = q_EA_E^{proj}F/(\sigma A_{surf})$, independent of $\varepsilon$ and $\alpha$.

## Examples
- Workbook Ch10 Q7 (= 2022/23 B2): at 18 000 km, noon 49 °C, midnight 46 °C, terminator 44 °C.
- 2024/25 B3(v): a 1 m × 2 m cylinder at 725.8 km with its axis to nadir, 82 W heater in eclipse, window 10–38 °C.

| Finish | $\alpha_S$ / $\varepsilon$ | eclipse | sunlit (side-on to Sun) |
|---|---|---|---|
| Black paint | 0.90 / 0.90 | −120 °C | +10 °C |
| White paint | 0.09 / 0.90 | −120 °C | −98 °C |
| SiO-Al dark mirror | 0.90 / 0.03 | +11 °C | +380 °C |
| **MLI** | 0.09 / 0.03 | **+11 °C** | **+39 °C** (end-on at noon); +96 °C side-on |

  MLI is the only candidate near the window, so it is the best choice. (It sits at the edge: the result depends on the attitude assumption.)
- 2023/24 B3(iv) (Jupiter): the 1.25 m cube with 75 W, window 10–30 °C. With the sunlit case evaluated at the synchronous altitude (about 7000 km), **SiO-Al** gives about −11 °C in eclipse and +9 °C in sunlight, the closest to the window. See the past-paper solutions.

## Related
- [[Absorptance and Emittance]] · [[Blackbody Radiation]] · [[Passive vs Active Thermal Control]] · [[Eclipse Duration]]

## Sources
- Chapter 10 slides 20–25 (equations 10.7–10.9)
