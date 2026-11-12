---
title: "Fick's Laws and Arrhenius Diffusion"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part C: Materials"
aliases: ["Fick's first law", "diffusion flux", "diffusion coefficient", "Arrhenius equation", "activation energy", "vacancy diffusion", "interstitial diffusion", "steady-state diffusion"]
tags: [feeg1002, concept, materials, diffusion]
status: complete
date: 2026-11-05
parent_lectures: ["[[FEEG1002 C3 - Diffusion]]"]
related_concepts: ["[[Annealing of Cold-Worked Metals]]", "[[Year 1/FEEG1002 Mechanics, Materials and Structures/01 - Notes/Concepts/Precipitation Hardening]]", "[[Creep]]"]
sources: ["02 - Sources/Materials/Lectures/Lecture 04 - Diffusion.pdf"]
---

# Fick's Laws and Arrhenius Diffusion

Fick's first law says that atoms diffuse down a concentration gradient at a rate proportional to it, and the Arrhenius equation says how the constant of proportionality, the diffusion coefficient $D$, rises with temperature.

$$
J=-D\frac{dC}{dx},\qquad D=D_0\exp\left(-\frac{Q}{RT}\right)
$$

$J$ is the flux, the mass (or number of atoms) crossing unit area per unit time; the minus sign makes the flow go from high to low concentration. At steady state the concentrations on the two faces of a plate are held fixed, the same flux must cross every slice, and so the profile through the plate is a straight line and $dC/dx=(C_A-C_B)/(x_A-x_B)$. This is the case used in the course, for example hydrogen purified by diffusing through a palladium membrane. Only the first law, at steady state, is covered; Fick's second law for changing profiles is not part of this module.

$D_0$ is a pre-exponential constant, $Q$ the activation energy per mole, $R=8.314$ J mol⁻¹ K⁻¹ and $T$ the absolute temperature, in kelvin. $Q$ is the energy barrier an atom must cross to jump from one site to the next, and $\exp(-Q/RT)$ is the fraction of attempts with enough thermal energy to cross it. That is why $D$ rises so steeply with temperature, and why the route matters: small interstitial atoms such as carbon in iron have a low $Q$ and diffuse far faster than substitutional atoms, which must wait for a vacancy, while grain boundaries and surfaces give easier paths than the bulk crystal.

![[m3_arrhenius_plot.png|900]]

Taking logarithms gives $\ln D=\ln D_0-(Q/R)(1/T)$, a straight line of slope $-Q/R$ against $1/T$. Two measurements are enough to find $Q$:

$$
Q=\frac{R\ln(D_2/D_1)}{1/T_1-1/T_2}
$$

and since the time for a given amount of diffusion scales as $1/D$, the same algebra trades heat-treatment time against temperature (carburising, recrystallisation and ageing all use it).

## Related

- [[FEEG1002 C3 - Diffusion#1. Diffusion mechanisms|diffusion mechanisms]] · [[FEEG1002 C3 - Diffusion#Activation energy and the structure of the path|activation energy and the path]] · [[FEEG1002 C3 - Diffusion#Fick's first law|Fick's first law]] · [[FEEG1002 C3 - Diffusion#The Arrhenius equation|the Arrhenius equation]] · [[FEEG1002 C3 - Diffusion#Working with the Arrhenius equation|working with it]] · [[FEEG1002 C3 - Diffusion#Time against temperature in heat treatment|time against temperature]]
- [[FEEG1002 Materials Tutorial 1 - Crystal Structures and Diffusion Solutions#Q8 - Diffusion|Tutorial 1, Q8]] · [[FEEG1002 Materials Tutorial 2 - Mechanical Properties and Strengthening Solutions#Q7 - Growth velocity of recrystallised grains|Tutorial 2, Q7]]
- [[Annealing of Cold-Worked Metals]] · [[Year 1/FEEG1002 Mechanics, Materials and Structures/01 - Notes/Concepts/Precipitation Hardening|Precipitation Hardening]] · [[Creep]]
