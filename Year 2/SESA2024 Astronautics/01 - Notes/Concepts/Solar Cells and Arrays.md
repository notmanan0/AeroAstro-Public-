---
title: "Solar Cells and Arrays"
module: "SESA2024 Astronautics"
type: concept
stream: "Spacecraft Subsystems"
aliases: ["solar array sizing", "photovoltaic", "solar cell efficiency", "BOL EOL", "degradation factor", "maximum power point"]
tags: [sesa2024, concept, power]
status: complete
parent_lectures: ["[[SESA2024 08 - Electrical Power Subsystem]]"]
related_concepts: ["[[Battery Sizing]]", "[[Spacecraft Power Sources]]", "[[Eclipse Duration]]"]
sources: ["02 - Sources/Lectures/Chapter 8/2025 WEEK 7 - Chapter 8 - Power - complete.pdf"]
---

# Solar Cells and Arrays

## Definition

> [!note] Definition
>
> $$A_{SA} = \frac{P_{EOL}}{S\cos\theta\;\eta\;\eta_p\;(1-D_0)},\qquad P_{EOL} = P_{load}+RV_A$$
>
> - $S$ ≈ 1350–1370 W/m² at 1 AU;
> - $\theta$ = maximum off-normal Sun angle;
> - $\eta$ = BOL cell efficiency (0.10–0.30);
> - $\eta_p$ = packing efficiency;
> - $D_0$ = lifetime degradation.

## Explanation
- **Photovoltaic effect** in a p–n junction. Si has a band gap of 1.1 eV, so it responds to $\lambda<1.1$ µm.
- A typical Si cell (30 °C): $V_{oc}\approx0.55$ V, $I_{sc}\approx35$ mA/cm², $P_{max}\approx14$ mW/cm².
- **Temperature**: power falls about 0.4 %/°C (Si). A cold array after eclipse gives a **power surge**.
- **Sun angle**: roughly a $\cos\theta$ law.
- **Radiation**: the main long-term degradation (lowers $V_{oc}$, $I_{sc}$ and $P$). Mitigated with cover glass and an n-on-p layout. Captured by $D_0$.
- **Series strings raise voltage; parallel strings raise current.**
- The **maximum power point** is the largest $VI$ rectangle under the $I$–$V$ curve. It is tracked by adjusting the load (shunt regulator).
- Body-mounted arrays (spinners) against deployed Sun-tracking wings (1 or 2 DoF).
- Output scales as $1/d^2$ from the Sun. Beyond about 5 AU, use RTGs.

## Examples
- Lecture (800 km, 1 kW): $P_A$ = 1660 W and $A$ = **13.2 m²** ($\eta$ = 11.5 %, $D_0$ = 0.1, 3°).
- Workbook GEO (8 kW): $P_{EOL}$ = 8488 W and $A$ ≈ **84 m²**.
- 2018/19 (350 W, 900 km, Li-ion): $R$ = 6.3 A, $P_{EOL}$ = 560 W, $A$ ≈ 3.4 m² ($\eta$ = 0.23, $\theta$ = 15°, $D_0$ = 0.4).
- **2024/25 A5** (body-mounted, 4 W EOL, 0.03 m²):

$$
P_{max} = 1360(0.03)(0.2)(0.8)(0.95) = 6.20\ \text{W}\ \Rightarrow\ \cos\theta_{max} = 4/6.20\ \Rightarrow\ \theta_{max} = \mathbf{49.8^\circ}
$$

- 2019/20 B2(iii): Si array at 8.5 % (50 °C) against 14 % (−70 °C). A cold array gives 65 % more power.

## Related
- [[Battery Sizing]] · [[Spacecraft Power Sources]] · [[Eclipse Duration]]

## Sources
- Chapter 8 slides 9–18, 36–38 (equations 8.1, 8.9–8.11)
