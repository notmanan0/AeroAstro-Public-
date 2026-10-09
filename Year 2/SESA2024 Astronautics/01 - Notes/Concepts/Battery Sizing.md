---
title: "Battery Sizing"
module: "SESA2024 Astronautics"
type: concept
stream: "Spacecraft Subsystems"
aliases: ["depth of discharge", "DoD", "battery capacity", "energy density", "NiCd", "NiH2", "Li-ion", "charge rate"]
tags: [sesa2024, concept, power]
status: complete
parent_lectures: ["[[SESA2024 08 - Electrical Power Subsystem]]"]
related_concepts: ["[[Eclipse Duration]]", "[[Solar Cells and Arrays]]", "[[Spacecraft Power Sources]]"]
sources: ["02 - Sources/Lectures/Chapter 8/2025 WEEK 7 - Chapter 8 - Power - complete.pdf"]
---

# Battery Sizing

## Definition

> [!note] Definition
> $$C = \frac{P_{EOL}\,t_e}{\text{DoD}\cdot V_B}\ (\text{A·h}),\qquad\mathcal E = CV_B\ (\text{W·h}),\qquad M_{batt} = \frac{\mathcal E}{\bar\varepsilon},\qquad R = \frac{\text{DoD}\cdot C}{t_s}\ (\text{A})$$
> Here $V_B$ = number of cells in series × cell voltage, chosen to match the bus voltage.

## Explanation
- **DoD** is the fraction of capacity used per discharge. The **cycle life falls as DoD rises**, so the number of eclipses (cycles) sets the allowable DoD. This is the key parameter for battery life.
- Number of cycles = lifetime ÷ orbit period (worst case: an eclipse every orbit).
- Cell counts: a 28 V bus needs **22 NiCd cells** (1.25 V, giving 27.5 V) or **7 Li-ion cells** (4.1 V, giving 28.7 V).

| | NiCd | NiH₂ | Li-ion |
|---|---|---|---|
| $\bar\varepsilon$ (W·h/kg) | 25–30 | 50–80 | 120–150 |
| Cell $V$ | 1.25 | 1.30 | 4.1 |
| Notes | obsolete; compact rectangular cells | deeper DoD for the same life; bulky pressure vessels | today's choice |

- The charge rate $R$ feeds the array sizing: $P_{array} = P_{load}+RV_A$.

## Examples
| Case | $t_e$ | DoD | $C$ | Mass |
|---|---|---|---|---|
| Lecture 800 km, 1 kW, NiCd | 0.6 h | 30 % | 72.7 A·h | 67 kg |
| Workbook GEO, 8 kW, NiCd | 1.157 h | 40 % | 841 A·h | 771 kg |
| 2018/19, 900 km, 350 W, Li-ion (7 cells) | 0.584 h | 20 % | 35.6 A·h | 7.9 kg |
| 2018/19, same, NiCd (22 cells) | 0.584 h | 20 % | 37.1 A·h | 34 kg |
| 2023/24, GEO, 10 kW, NiCd / NiH₂ | 1.157 h | 40 / 60 % | 1052 / 701 A·h | 964 / 386 kg |
| 2014/15, ISS 200 kW, NiCd / NiH₂ | 0.605 h | 10 / 30 % | 43 250 / 14 420 A·h | 40.4 / 8.1 t |

- Li-ion wins on mass by about 4×.
- NiH₂ is about 2.5× lighter than NiCd but about 1.5× bulkier per W·h (2023/24 B2).

## Related
- [[Eclipse Duration]] · [[Solar Cells and Arrays]] · [[Spacecraft Power Sources]]

## Sources
- Chapter 8 equations 8.4–8.9; workbook Ch8 Q8–Q10
