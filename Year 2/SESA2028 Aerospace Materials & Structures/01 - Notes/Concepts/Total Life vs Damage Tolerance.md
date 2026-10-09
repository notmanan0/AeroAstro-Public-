---
title: "Total Life vs Damage Tolerance"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
stream: "Materials"
tags: [sesa2028, materials, fatigue, lifing, design-philosophy]
status: complete
parent: ["[[SESA2028 M2 - Fatigue - Fracture Surfaces, Mechanisms and Lifing]]"]
related: ["[[Miner's Rule]]", "[[Paris Law]]", "[[S-N Curve and Basquin Law]]"]
---

# Total Life vs Damage Tolerance

Two philosophies for lifing against fatigue.

## Total life (safe life)

- Predicts the cycles to **initiate** a crack in a nominally defect-free part **plus** to grow it to failure: $N_f=N_i+N_g$.
- Uses S-N (HCF) or $\varepsilon$-N (LCF) curves, Goodman mean-stress correction and **Miner's rule** for spectra.
- Because $N_i$ usually dominates and depends heavily on **surface finish**, this approach effectively **designs against initiation**.
- **Data needed**: S-N or $\varepsilon$-N curves for the right material, surface condition, environment and mean stress; the service load spectrum (rainflow counted); stress-concentration factors or FEA hot-spot stresses.
- **Suited to**: parts that must not crack, or cannot be inspected in service. Rotating shafts, springs, gears, bolts, some engine components; the lecturer's example is steam-turbine blade roots.

## Damage tolerance

- **Assumes a crack already exists**: the largest found by NDT, or the largest that could be *missed*.
- Uses fracture mechanics: $\Delta K$, the Paris law to grow the crack from $a_i$ to $a_c$, and $K_{Ic}$ for $a_c$.
- Designs against **growth**; sets **inspection intervals** so a crack is found before it reaches $a_c$.
- **Data needed**: $a_i$ (size **and** position, from dye penetrant, magnetic particle, eddy current, ultrasound or X-ray); $\Delta\sigma$ and $\sigma_{max}$; $K_{Ic}$; $A$, $m$ in the service environment; the geometry factor $Q$.
- **Suited to**: inspectable, redundant structures. Airframes (wings, fuselage), pressure vessels, offshore welds, turbine discs (retirement-for-cause).

## Contrast in one line

Total life asks "how long until a crack appears and grows?"; damage tolerance asks "given this crack, how long until it is dangerous, and when must I look again?"

See [[Miner's Rule]] and [[Paris Law]].
