---
title: "Griffith Criterion and Fracture Toughness"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part C: Materials"
aliases: ["Griffith criterion", "Griffith energy balance", "fracture toughness", "K_IC", "KIC", "stress intensity factor", "critical crack length", "plane strain fracture toughness", "fast fracture", "stress concentration"]
tags: [feeg1002, concept, materials, fracture]
status: complete
date: 2026-11-05
parent_lectures: ["[[FEEG1002 C8 - Fracture - Brittle, Ductile and Fracture Mechanics]]"]
related_concepts: ["[[Ductile-to-Brittle Transition]]", "[[Ceramic Flaw Sensitivity]]", "[[S-N Curves and Paris Law]]", "[[Griffith Energy Balance]]", "[[Stress Intensity Factor]]"]
sources: ["02 - Sources/Materials/Lectures/Lecture 12 - Failure of Materials 1 - Brittle vs Ductile and Griffiths.pdf", "02 - Sources/Materials/Lectures/Lecture 13 - Failure of Materials 2 - Fracture Mechanics.pdf"]
---

# Griffith Criterion and Fracture Toughness

The Griffith criterion says a crack in a brittle material grows when the elastic strain energy it would release by extending exceeds the surface energy needed to create the new crack faces; fracture toughness $K_c$ is the critical value of the stress intensity factor at which that happens.

Flaws concentrate stress. At the tip of an elliptical flaw of length $2a$ (or a surface flaw of length $a$) and tip radius $\rho_t$, the local stress is $\sigma_m=2\sigma_0(a/\rho_t)^{1/2}$, many times the remote stress $\sigma_0$ for a sharp crack. Griffith turned this into an energy balance for a crack of length $2a$ in a plate under stress $\sigma$: growing the crack costs surface energy $4a\gamma_s$ (two faces) but releases strain energy $\pi a^2\sigma^2/E$. The total has a maximum, and setting its derivative to zero gives the critical stress

$$
\sigma_c=\sqrt{\frac{2E\gamma_s}{\pi a}}
$$

Below it the crack is stable; above it every increment of growth releases more energy than it costs, and the crack runs.

![[m8_griffith_energy.png|900]]

Fracture mechanics puts the same idea in terms of the stress field at the crack tip, whose magnitude is the stress intensity factor $K=Y\sigma\sqrt{\pi a}$, with $Y$ a geometry factor ($Y=1$ for an internal crack in an infinite plate). Fast fracture happens when $K$ reaches the fracture toughness:

$$
K_c=Y\sigma_f\sqrt{\pi a_c}
$$

For an ideally brittle material the two approaches agree, $K_c=\sqrt{2E\gamma_s}$. $K_c$ measured on thin plates depends on thickness; thick enough to be in plane strain, it falls to a minimum, $K_{IC}$, which is a material property. The relation is used both ways in design: known flaws give the stress not to exceed, $\sigma=K_{IC}/Y\sqrt{\pi a}$, and a known service stress gives the largest flaw that can be tolerated, $a_c=\frac1\pi(K_{IC}/Y\sigma)^2$, which sets what inspection must detect. A tough material may yield before the crack runs; compare $\sigma_f$ with $\sigma_y$ to see which comes first.

## Related

- [[FEEG1002 C8 - Fracture - Brittle, Ductile and Fracture Mechanics#2. Stress concentrations|stress concentrations]] · [[FEEG1002 C8 - Fracture - Brittle, Ductile and Fracture Mechanics#3. The Griffith energy balance|the Griffith energy balance]] · [[FEEG1002 C8 - Fracture - Brittle, Ductile and Fracture Mechanics#4. The stress intensity factor|the stress intensity factor]] · [[FEEG1002 C8 - Fracture - Brittle, Ductile and Fracture Mechanics#KIC as a material property|KIC as a material property]] · [[FEEG1002 C8 - Fracture - Brittle, Ductile and Fracture Mechanics#The link to Griffith|the link to Griffith]] · [[FEEG1002 C8 - Fracture - Brittle, Ductile and Fracture Mechanics#Using fracture mechanics in design|design]] · [[FEEG1002 C8 - Fracture - Brittle, Ductile and Fracture Mechanics#Worked example - the pressure vessel question|pressure vessel example]]
- [[FEEG1002 Materials Tutorial 4 - Failure of Materials Solutions#Q2 - Griffith flaw size in fused silica|Tutorial 4, Q2]] · [[FEEG1002 Materials Tutorial 4 - Failure of Materials Solutions#Q3 - Fast fracture or general yield in a pressure-vessel plate|Q3]] · [[FEEG1002 Materials Tutorial 4 - Failure of Materials Solutions#Q4 - Safety factor for the pressure vessel|Q4]]
- [[Ductile-to-Brittle Transition]] · [[Ceramic Flaw Sensitivity]] · [[S-N Curves and Paris Law]]
- Year 2: [[Griffith Energy Balance]] · [[Stress Intensity Factor]] · [[Fracture Toughness and LEFM Validity]] · [[SESA2028 M1 - Fracture, Toughness and Fracture Mechanics]]
