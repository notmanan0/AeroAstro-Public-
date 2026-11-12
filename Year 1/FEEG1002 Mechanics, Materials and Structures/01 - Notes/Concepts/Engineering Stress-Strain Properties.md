---
title: "Engineering Stress-Strain Properties"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part C: Materials"
aliases: ["tensile test", "yield strength", "0.2% offset", "proof stress", "ultimate tensile strength", "UTS", "ductility", "percent elongation", "reduction in area", "resilience", "toughness", "true stress", "true strain", "Poisson's ratio"]
tags: [feeg1002, concept, materials, mechanical-properties]
status: complete
date: 2026-11-05
parent_lectures: ["[[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation]]"]
related_concepts: ["[[Stress, Strain and Young's Modulus]]", "[[Dislocations and Slip Systems]]", "[[Strengthening Mechanisms in Metals]]"]
sources: ["02 - Sources/Materials/Lectures/Lecture 05 - Elastic and Plastic Mechanical Properties.pdf"]
---

# Engineering Stress-Strain Properties

The engineering stress–strain curve from a tensile test plots the load over the original area, $\sigma=F/A_0$, against the extension over the original length, $\varepsilon=\Delta L/L_0$; the properties read from it describe a material's stiffness, strength and ductility.

The initial straight part is elastic, with slope Young's modulus $E$, and the lateral contraction that goes with it is set by Poisson's ratio, $\nu=-\varepsilon_x/\varepsilon_z$. Most metals have no sharp end to the straight line, so the yield strength $\sigma_y$ is defined by the 0.2 % offset: draw a line of slope $E$ from a strain of 0.002 and read where it meets the curve. Low-carbon steel is the exception, with an upper and a lower yield point caused by carbon atoms pinning the dislocations. The curve then rises, because of work hardening, to a maximum, the ultimate tensile strength (UTS); beyond it a neck forms, the load falls and the specimen breaks. Ductility is the plastic strain at fracture, as percent elongation $\%EL=(L_f-L_0)/L_0\times100$ or percent reduction in area $\%RA=(A_0-A_f)/A_0\times100$.

![[m4_stress_strain_curve.png|900]]

Two energies per unit volume come from areas under the curve. Resilience is the elastic energy stored up to yield, $U_r=\sigma_y^2/2E$, the property wanted in a spring; toughness is the whole area up to fracture, which needs both strength and ductility. The engineering curve uses the original area throughout, so after necking it understates the stress actually carried. True stress and strain use the instantaneous area and length, and before necking (constant volume) they follow from the engineering values:

$$
\sigma_T=\sigma(1+\varepsilon),\qquad \varepsilon_T=\ln(1+\varepsilon)
$$

In design, $E$ sets deflections, $\sigma_y$ (divided by a safety factor) sets the working stress, and the UTS and ductility say how much warning there will be before failure.

## Related

- [[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation#1. Elastic deformation|elastic deformation]] · [[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation#True stress and strain|true stress and strain]] · [[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation#Yield strength and the 0.2 % offset|yield strength]] · [[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation#Upper and lower yield points|upper and lower yield points]] · [[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation#Ductility|ductility]] · [[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation#Resilience and toughness|resilience and toughness]] · [[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation#Using the properties in design|design]]
- [[FEEG1002 Materials Tutorial 2 - Mechanical Properties and Strengthening Solutions#Q2 - Properties from the aluminium tensile curve|Tutorial 2, Q2]]
- [[Stress, Strain and Young's Modulus]] · [[Dislocations and Slip Systems]] · [[Strengthening Mechanisms in Metals]]
