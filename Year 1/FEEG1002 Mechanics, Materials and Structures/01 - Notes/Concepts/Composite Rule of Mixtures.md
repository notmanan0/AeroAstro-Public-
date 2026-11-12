---
title: "Composite Rule of Mixtures"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part C: Materials"
aliases: ["rule of mixtures", "inverse rule of mixtures", "isostrain", "isostress", "longitudinal modulus", "transverse modulus", "fibre load fraction", "anisotropy", "laminate"]
tags: [feeg1002, concept, materials, composites]
status: complete
date: 2026-11-05
parent_lectures: ["[[FEEG1002 C11 - Ceramics and Composites]]"]
related_concepts: ["[[Equivalent Spring Stiffness]]", "[[Rule of Mixtures]]", "[[Critical Fibre Length]]", "[[Ceramic Flaw Sensitivity]]"]
sources: ["02 - Sources/Materials/Lectures/Lecture 19 - Composites.pdf"]
---

# Composite Rule of Mixtures

The rule of mixtures estimates the modulus of a ply of continuous, aligned fibres perfectly bonded to a matrix: along the fibres the fibre and matrix strain equally and the moduli add in proportion to their volume fractions; across the fibres they carry equal stress and the compliances add instead.

Loaded along the fibres, the two constituents must stretch together (isostrain). The load is shared, $F_c=F_f+F_m$, and dividing by the composite area and strain gives

$$
E_{cl}=E_fV_f+E_mV_m
$$

the volume-weighted average, an upper bound. The fraction of the load in the fibres is $F_f/F_c=E_fV_f/(E_fV_f+E_mV_m)$, which for a stiff fibre is nearly all of it. Loaded across the fibres, the layers sit in series along the load path and each carries the same stress (isostress), while the strains add, $\varepsilon_c=V_f\varepsilon_f+V_m\varepsilon_m$, so

$$
\frac{1}{E_{ct}}=\frac{V_f}{E_f}+\frac{V_m}{E_m},\qquad E_{ct}=\frac{E_mE_f}{E_fV_m+E_mV_f}
$$

which is dominated by the compliant matrix. Both moduli are written $E_c$ in the slides; the subscripts $l$ and $t$ here only keep them apart. These are the same two combinations as springs in parallel and springs in series.

![[m11_composite_moduli.png|900]]

For glass fibres ($E_f=69$ GPa) in polyester ($E_m=3.4$ GPa) at $V_f=0.4$ the ply is 29.6 GPa along the fibres and only 5.5 GPa across them. That anisotropy is why plies are stacked at different angles into laminates where loads come from several directions. The rule of mixtures can be used approximately for strength, but not for fracture toughness, and only for continuous aligned fibres; short fibres need the treatments of later years.

## Related

- [[FEEG1002 C11 - Ceramics and Composites#3. Composites|composites]] · [[FEEG1002 C11 - Ceramics and Composites#Longitudinal modulus from equal strain|longitudinal modulus]] · [[FEEG1002 C11 - Ceramics and Composites#Load carried by the fibres|load carried by the fibres]] · [[FEEG1002 C11 - Ceramics and Composites#Transverse modulus from equal stress|transverse modulus]] · [[FEEG1002 C11 - Ceramics and Composites#Anisotropy and laminates|anisotropy and laminates]] · [[FEEG1002 C11 - Ceramics and Composites#Choosing the stiffest combination|choosing the stiffest combination]] · [[FEEG1002 C11 - Ceramics and Composites#Worked example - stiffness of a carbon–epoxy ply|carbon–epoxy example]]
- [[FEEG1002 Materials Tutorial 5 - Polymers, Ceramics and Composites Solutions#Q4 - Glass–polyester composite|Tutorial 5, Q4]]
- [[Equivalent Spring Stiffness]] · [[Ceramic Flaw Sensitivity]]
- Year 2: [[Rule of Mixtures]] · [[Critical Fibre Length]] · [[SESA2028 M4 - Polymer Matrix Composites]]
