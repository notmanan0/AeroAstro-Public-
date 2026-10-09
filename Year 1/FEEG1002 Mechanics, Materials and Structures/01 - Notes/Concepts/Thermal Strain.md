---
title: "Thermal Strain"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part B: Statics 2"
aliases: ["thermal expansion", "coefficient of thermal expansion", "thermal stress", "alpha Delta T"]
tags: [feeg1002, concept, statics-2, thermal-strain, thermal-stress]
status: complete
parent_lectures: ["[[FEEG1002 B2 - Strain in Multiple Dimensions and Thermal Strain]]"]
related_concepts: ["[[Strain Components and Volumetric Strain]]", "[[Generalised Hooke's Law]]", "[[Stress, Strain and Young's Modulus]]"]
sources: []
---

# Thermal Strain

## Definition

> [!note] Definition
> A temperature change produces an isotropic, stress-free strain:
>
> $$\varepsilon_T = \alpha(T - T_{ref}),\qquad \varepsilon_{xx} = \varepsilon_{yy} = \varepsilon_{zz} = \varepsilon_T,\quad \text{no thermal shear}$$
>
> Stress appears only if the expansion is constrained. Total strain = mechanical + thermal.

## Explanation

- **Fully restrained bar**: $\sigma = -E\alpha\Delta T$, independent of $L$ and $A$.
- **Fully restrained plate** (biaxial): $\sigma = -E\alpha\Delta T/(1-\nu)$, which is larger.
- **Superposition method**:
  1. let each part expand freely;
  2. add $FL/EA$ corrections;
  3. impose compatibility (gaps, bonded equal extension) and equilibrium (series: equal force; parallel: forces sum to zero).
- **Mismatch**: bonded materials with different $\alpha$ build internal stress. The higher-$\alpha$ part goes into compression on heating.
- Typical $\alpha$ (×10⁻⁶/K): steel 11.7, brass 20.9, aluminium 23.6, silicon/chip about 2.6.

## Examples

- Rail (L3): −38 MPa at 48 °C.
- Al shell and brass core: $\sigma_{Al} = -8.15$ MPa.
- Chip on a board: 37 N per solder joint.

![[s2_thermal_rail.png|760]]

## Related

- Topic notes: [[FEEG1002 B2 - Strain in Multiple Dimensions and Thermal Strain]]
- Concepts: [[Strain Components and Volumetric Strain]] · [[Generalised Hooke's Law]] · [[Stress, Strain and Young's Modulus]]
- Year 2: [[Shrink Fit]] ([[SESA2028 S10 - Thick Cylinders and Shrink Fits]]) · [[Thermal Barrier Coatings]] mismatch ([[SESA2028 M8 - High Temperature Materials - Creep, Oxidation and Superalloys]]) · spacecraft thermal cycling ([[Spacecraft Thermal Balance Equation]])

## Sources

- Statics 2 Lecture 3a–b; Statics 2 Tutorials 2 and 8
