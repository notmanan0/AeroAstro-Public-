---
title: "Thin-Walled Pressure Vessels"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part B: Statics 2"
aliases: ["hoop stress", "longitudinal stress", "pR/t", "pR/2t", "thin cylinder", "thin sphere"]
tags: [feeg1002, concept, statics-2, pressure-vessels]
status: complete
parent_lectures: ["[[FEEG1002 B1 - Stress in Multiple Dimensions and Thin-Walled Pressure Vessels]]", "[[FEEG1002 B3 - Generalised Hooke's Law]]"]
related_concepts: ["[[Stress Tensor and Stress Element]]", "[[Generalised Hooke's Law]]", "[[Lame Thick-Cylinder Solution]]"]
sources: []
---

# Thin-Walled Pressure Vessels

## Definition

> [!note] Definition
> For internal gauge pressure $p$, mean radius $R$ and wall thickness $t$, with $t/R < 0.1$:
> $$\text{cylinder: } \sigma_{hoop} = \frac{pR}{t},\quad \sigma_{long} = \frac{pR}{2t};\qquad \text{sphere: } \sigma = \frac{pR}{2t}\ \text{(all directions)}$$
> The radial stress (of order $p$) is neglected, so the wall is in plane stress.

## Explanation

- **Derivation**: free bodies cutting the vessel **and its contents**.
  - hoop: $p(2RL) = \sigma(2tL)$;
  - longitudinal: $p\pi R^2 = \sigma(2\pi Rt)$.
  - The end-cap shape is irrelevant, because only the projected area counts.
- In a cylinder the hoop stress is twice the longitudinal, so cylinders fail **lengthwise**. A sphere has half the peak stress, and so is the most efficient pressure container.
- **Strains** from [[Generalised Hooke's Law]]:
  - cylinder: $\varepsilon_{hoop} = \frac{pR}{tE}(1-\tfrac\nu2)$ and $\varepsilon_{long} = \frac{pR}{2tE}(1-2\nu)$;
  - sphere: $\varepsilon = \frac{pR}{2tE}(1-\nu)$.
- Under **external** pressure the stresses are compressive, and buckling must be checked.
- For $t/R\gtrsim0.1$, use Lamé ([[Lame Thick-Cylinder Solution]]).

## Examples

- Statics 2 Tutorial 1: sphere with $D = 400$ mm, $t = 6$ mm, 180 MPa gives $p = 10.8$ MPa; the bolts carry 222 MPa.
- Statics 2 Tutorial 8 Q3: LH₂ tank with SF = 3 and von Mises $\sigma_{eq} = \frac{\sqrt3}{2}\frac{pR}{t}$ gives $p = 7.26$ bar.

![[s2_pressure_vessel_stresses.png|760]]

## Related

- Topic notes: [[FEEG1002 B1 - Stress in Multiple Dimensions and Thin-Walled Pressure Vessels]] · [[FEEG1002 B3 - Generalised Hooke's Law]]
- Concepts: [[Stress Tensor and Stress Element]] · [[Generalised Hooke's Law]] · [[Lame Thick-Cylinder Solution]]
- Year 2: [[SESA2028 S10 - Thick Cylinders and Shrink Fits]] (Lamé; thin-wall is the $t\to0$ limit) · fuselage and propellant tanks

## Sources

- Statics 2 Lecture 1c
