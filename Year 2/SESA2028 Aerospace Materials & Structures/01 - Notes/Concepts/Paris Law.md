---
title: "Paris Law"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
stream: "Materials"
tags: [sesa2028, materials, fatigue, damage-tolerance, crack-growth]
status: complete
parent: ["[[SESA2028 M2 - Fatigue - Fracture Surfaces, Mechanisms and Lifing]]"]
related: ["[[Stress Intensity Factor]]", "[[Total Life vs Damage Tolerance]]", "[[Fatigue Fracture Surface Features]]"]
---

# Paris Law

![[Figures/materials_paris_regimes_schematic.png]]

In **Stage II** (stable) fatigue crack growth, the growth per cycle is a power law in the stress-intensity range:

$$
\frac{da}{dN}=A\,(\Delta K)^m,\qquad \Delta K=Q\,\Delta\sigma\sqrt{\pi a}.
$$

On log-log axes this is a straight line of slope $m$ (typically 2-4 for metals) and intercept $\log A$. $A$ depends on the units: SESA2028 exams quote it for $\Delta K$ in $\mathrm{MPa\sqrt m}$ and $a$ in **m**.

Below the line is the **threshold** $\Delta K_{th}$ (Stage I, no growth or shear-mode growth). Above it is fast growth as $K_{max}\to K_c$.

## Integrating for life

Separate the variables and integrate from the measured defect $a_i$ to the critical size $a_c$:

$$
N_f=\frac{a_c^{\,1-m/2}-a_i^{\,1-m/2}}{\left(1-\tfrac m2\right)A\left(Q\Delta\sigma\sqrt\pi\right)^m}\qquad(m\ne2),
$$

$$
a_c=\frac1\pi\left(\frac{K_{Ic}}{Q\sigma_{max}}\right)^2,\qquad
\Delta\sigma=\sigma_{max}-\max(\sigma_{min},0).
$$

![[Figures/materials_paris_crack_growth_all_exams.png]]

## Key points

- Only the **tensile** part of the cycle counts (a closed crack does not grow).
- $da/dN\propto a^{m/2}$: most of the life is spent while the crack is **small**, so $N_f$ is very sensitive to $a_i$ (NDT resolution) and fairly insensitive to $a_c$.
- Apply a **safety factor of 2** on life, or inspect at $N_f/2$.
- **Invalid** for Stage I (shear, faceted) growth, short cracks near microstructural barriers, and composites (their damage is not a single crack).
- $A$ and $m$ depend on environment, temperature, frequency (oxidation and creep-fatigue) and $R$ ratio.
