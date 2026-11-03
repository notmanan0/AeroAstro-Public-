---
title: "S-N Curve and Basquin Law"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
stream: "Materials"
aliases: ["S-N curve", "Wohler curve", "Basquin's law", "Coffin-Manson law", "Fatigue limit", "Endurance limit"]
tags: [sesa2028, materials, fatigue, total-life]
status: lectured
parent: ["[[SESA2028 M2 - Fatigue - Fracture Surfaces, Mechanisms and Lifing]]"]
related: ["[[Goodman Relation]]", "[[Miner's Rule]]", "[[Total Life vs Damage Tolerance]]"]
---

# S-N Curve and Basquin Law

An S-N curve plots the stress amplitude applied to test specimens against the number of cycles they survive, and Basquin's law $\Delta\sigma/2=\sigma_f'(2N_f)^b$ is the power law fitted to its high-cycle part.

Lower amplitudes give longer lives because both initiation and growth slow down. Steels level off at a fatigue limit, below which a crack never successfully initiates and the life is in effect infinite. Aluminium alloys keep falling, so an endurance limit is quoted instead, the fatigue strength at a stated life such as $10^7$ or $10^8$ cycles. About $10^5$ cycles separates high-cycle fatigue (low, nominally elastic stress, life dominated by initiation; fuselages and wings under vibration) from low-cycle fatigue (cyclic plasticity, early initiation, life dominated by growth; turbine discs and blades through start-stop cycles).

![[materials_sn_curves.png|700]]

In high-cycle fatigue, Basquin's law uses the fatigue strength coefficient $\sigma_f'$ and the negative fatigue strength exponent $b$. Inverting it gives the life at an amplitude $\sigma_a$, $N_f=\tfrac12(\sigma_a/\sigma_f')^{1/b}$, and because $1/b$ is large and negative, a small cut in amplitude gives a large gain in life. In low-cycle fatigue, strain is the better measure, because once the material yields a small change in stress gives a large change in strain, and the Coffin–Manson law $\Delta\varepsilon_p/2=\varepsilon_f'(2N_f)^c$ uses the fatigue ductility coefficient and exponent.

An S-N curve belongs to a particular surface finish and mean stress. Electropolished specimens last much longer than machined ones because scratches shorten initiation, and a higher mean stress lowers the curve ([[Goodman Relation]]). Used with [[Miner's Rule]], S-N curves form the total-life approach ([[Total Life vs Damage Tolerance]]).

## Related

- Topic: [[SESA2028 M2 - Fatigue - Fracture Surfaces, Mechanisms and Lifing|M2]]
- Concepts: [[Goodman Relation]] · [[Miner's Rule]] · [[Total Life vs Damage Tolerance]]
