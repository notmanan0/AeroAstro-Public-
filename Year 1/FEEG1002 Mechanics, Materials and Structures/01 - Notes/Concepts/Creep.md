---
title: "Creep"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part C: Materials"
aliases: ["steady-state creep", "steady state creep", "creep rate", "primary creep", "secondary creep", "tertiary creep", "creep rupture", "power-law creep"]
tags: [feeg1002, concept, materials, creep]
status: complete
date: 2026-11-05
parent_lectures: ["[[FEEG1002 C9 - Fatigue, Creep and Corrosion]]"]
related_concepts: ["[[Fick's Laws and Arrhenius Diffusion]]", "[[Polymer Glass Transition and Viscoelasticity]]", "[[Creep Curve and Mechanisms]]"]
sources: ["02 - Sources/Materials/Lectures/Lecture 15 - Failure of Materials 4 - Creep and Corrosion.pdf"]
---

# Creep

Creep is time-dependent deformation under a constant stress, normally at elevated temperature; in metals it matters above about 0.3–0.4 of the absolute melting temperature $T_m$, and in ceramics above about 0.4–0.5 $T_m$.

The melting temperature sets the threshold because creep is controlled by diffusion, which becomes significant at a similar fraction of $T_m$. A creep test holds a specimen at constant load and temperature and records strain against time. Loading gives an instantaneous elastic strain. In primary creep the rate falls, as the material work-hardens. In secondary, steady-state creep the rate is constant and the curve is a straight line; most of the service life is spent here. In tertiary creep the rate accelerates as the section shrinks and internal damage grows, ending in rupture. Higher stress or temperature gives a faster steady-state rate and a shorter life.

![[m9_creep_curve.png|900]]

The steady-state creep rate is the design parameter:

$$
\dot\varepsilon_s=K_2\sigma^n\exp\left(-\frac{Q_c}{RT}\right)
$$

with $K_2$ a material constant, $Q_c$ the activation energy for creep, $T$ in kelvin, and a stress exponent $n$ between about 1 and 9 that depends on the mechanism (vacancy diffusion through the grains or along their boundaries, dislocation climb, grain-boundary sliding). The exponential is the same Arrhenius factor as for diffusion. Two tests at the same temperature and different stresses give $n$ from the ratio of rates; a ratio between two conditions gives the effect of changing both, $\dot\varepsilon_2/\dot\varepsilon_1=(\sigma_2/\sigma_1)^n\exp[-(Q_c/R)(1/T_2-1/T_1)]$.

Creep resistance comes from a high melting temperature, a high modulus and large grains, since grain boundaries slide and give fast diffusion paths. That is the opposite of the fine grains wanted for strength at room temperature, and it is why turbine blades went from equiaxed castings to directionally solidified and then single-crystal blades.

## Related

- [[FEEG1002 C9 - Fatigue, Creep and Corrosion#2. Creep|creep]] · [[FEEG1002 C9 - Fatigue, Creep and Corrosion#The three stages|the three stages]] · [[FEEG1002 C9 - Fatigue, Creep and Corrosion#Steady-state creep rate|steady-state creep rate]] · [[FEEG1002 C9 - Fatigue, Creep and Corrosion#Designing against creep|designing against creep]] · [[FEEG1002 C9 - Fatigue, Creep and Corrosion#Worked example - sensitivity of creep to temperature and stress|worked example]] · [[FEEG1002 C10 - Polymers - Structure and Mechanics#Creep and stress relaxation|creep in polymers]]
- [[FEEG1002 Materials Tutorial 4 - Failure of Materials Solutions#Q6 - Steady-state creep|Tutorial 4, Q6]]
- [[Fick's Laws and Arrhenius Diffusion]] · [[Polymer Glass Transition and Viscoelasticity]]
- Year 2: [[Creep Curve and Mechanisms]] · [[SESA2028 M8 - High Temperature Materials - Creep, Oxidation and Superalloys]]
