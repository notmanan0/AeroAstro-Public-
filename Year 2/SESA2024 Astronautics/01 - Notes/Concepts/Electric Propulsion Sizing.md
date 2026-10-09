---
title: "Electric Propulsion Sizing"
module: "SESA2024 Astronautics"
type: concept
stream: "Spacecraft Subsystems"
aliases: ["electric propulsion", "characteristic velocity", "ion thruster", "resistojet", "arcjet", "specific power", "EP optimisation"]
tags: [sesa2024, concept, propulsion, electric-propulsion]
status: complete
parent_lectures: ["[[SESA2024 07 - Spacecraft Propulsion]]"]
related_concepts: ["[[Chemical Propulsion Systems]]", "[[Tsiolkovsky Rocket Equation]]", "[[Spacecraft Power Sources]]"]
sources: ["02 - Sources/Lectures/Chapter 7/Chapter 7 - Propulsion - original slides(1)(1).pdf"]
---

# Electric Propulsion Sizing

## Definition

> [!note] Definition
> EP is **power-limited**. With $M_0 = M_p+M_W+M_e$, jet power $\tfrac12\sigma V_{ex}^2 = \eta W$, specific power $\beta = W/M_W$ and $\sigma = M_e/t_b$:
>
> $$V_c = \sqrt{2\eta\beta t_b},\qquad M_e = \frac{M_0-M_p}{1+(V_{ex}/V_c)^2},\qquad \frac{\Delta V}{V_c} = x\ln\frac{1+x^2}{M_p/M_0+x^2},\ \ x = \frac{V_{ex}}{V_c}$$

## Explanation
- The power plant mass grows with $V_{ex}^2$, so ΔV has a **maximum** in $V_{ex}$. Operate near the optimum:

| $M_p/M_0$ | $x^*$ | $(\Delta V/V_c)_{max}$ |
|---|---|---|
| 0.1 | 0.63 (≈ 0.65) | 0.65 |
| 0.25 | 0.74 | 0.49 |
| 0.5 | 0.85 | 0.29 |

- **Design rule**: for maximum payload, $V_{ex}\approx V_c = \sqrt{2\eta\beta t_b}$. This needs a **long burn time** and **high specific power**.
- **Thruster power**: $W = TV_{ex}/(2\eta)$. At 50 mN:

| Thruster | $I_{sp}$ | $\eta$ | Power |
|---|---|---|---|
| Resistojet | 700 s | 0.9 | 190 W |
| Arcjet | 1500 s | 0.3 | 1230 W |
| Ion | 5000 s | 0.75 | 1640 W |

- **Categories**: electrothermal (resistojet, arcjet), electromagnetic (MPD, Hall; Lorentz force; kiloamps; Xe), electrostatic (ion).

![[ast_ep_optimisation.png|560]]

## Examples
- **Pluto orbiter** (workbook Ch7 Q12): 17 km/s, $M_p/M_0$ = 0.1, 2 years, 3000 kg.
  - $V_c$ = 26.2 km/s; $V_{ex}$ = 17 km/s ($I_{sp}$ = 1733 s → ion);
  - $\beta$ = 5.4 W/kg (RTG);
  - $M_e$ = 1900 kg, $M_W$ = 800 kg, $W$ = 4.3 kW, $T$ = 0.5 N.
- **2024/25 A2**: optimised, $M_p/M_0$ = 0.1, $I_{sp}$ = 1200 s. $V_{ex}$ = 11.77 km/s, so $V_c = V_{ex}/0.65$ = 18.1 km/s and **ΔV ≈ 0.65 $V_c$ ≈ 11.8 km/s**.

## Related
- [[Chemical Propulsion Systems]] · [[Tsiolkovsky Rocket Equation]] · [[Spacecraft Power Sources]]

## Sources
- Chapter 7 lecture slides 31–47, equations 7.7–7.16
