---
title: "Paris Law"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
stream: "Materials"
aliases: ["Paris-Erdogan law", "Fatigue crack growth law", "Paris lifing"]
tags: [sesa2028, materials, fatigue, damage-tolerance, crack-growth]
status: lectured
parent: ["[[SESA2028 M2 - Fatigue - Fracture Surfaces, Mechanisms and Lifing]]"]
related: ["[[Stress Intensity Factor]]", "[[Total Life vs Damage Tolerance]]", "[[Fatigue Fracture Surface Features]]"]
---

# Paris Law

The Paris law $da/dN=A(\Delta K)^m$ describes stable fatigue crack growth: the crack advance per cycle is a power of the stress intensity factor range $\Delta K=Q\Delta\sigma\sqrt{\pi a}$.

On log–log axes of $da/dN$ against $\Delta K$ the central part of the data is a straight line with slope $m$ (typically 2–4 for metals) and intercept $\log A$. It holds for stage II growth, where the crack runs perpendicular to the maximum opening stress and leaves striations. It does not describe stage I growth along slip bands, very short cracks, growth near the threshold, or the rapid acceleration as $K_{max}$ approaches $K_c$. Only the tensile part of the cycle counts, because a closed crack does not grow. The exam papers quote $A$ for $\Delta K$ in MPa√m and $a$ in metres.

![[materials_paris_regimes_and_growth.png|800]]

Because $\Delta K$ rises with crack length, the growth rate is not constant and the life must be integrated. Separating variables and integrating from the inspected crack $a_i$ to the critical crack $a_c=\frac1\pi(K_{Ic}/Q\sigma_{max})^2$ gives, for $m\neq2$,

$$
N_f=\frac{a_c^{\,1-m/2}-a_i^{\,1-m/2}}{\left(1-\frac m2\right)A\left(Q\Delta\sigma\sqrt\pi\right)^m},
$$

with the full derivation in [[SESA2028 M2 - Fatigue - Fracture Surfaces, Mechanisms and Lifing#7. Damage tolerance: integrating the Paris law|M2]]. Since $da/dN$ grows as $a^{m/2}$, most of the life is spent while the crack is small: the life is very sensitive to $a_i$, and so to inspection resolution, and much less sensitive to $a_c$ and $K_{Ic}$. Answers should end with a safety factor of 2 or an inspection interval at half the predicted life, and a note that $A$ and $m$ were measured in laboratory air and change with environment, temperature and frequency.

![[materials_paris_crack_growth_all_exams.png|800]]

## Related

- Topic: [[SESA2028 M2 - Fatigue - Fracture Surfaces, Mechanisms and Lifing|M2]]
- Concepts: [[Stress Intensity Factor]] · [[Total Life vs Damage Tolerance]] · [[Fatigue Fracture Surface Features]] · [[Fracture Toughness and LEFM Validity]]
