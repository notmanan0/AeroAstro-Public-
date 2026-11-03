---
title: "Two-Property Rule and Perfect Gas Model"
module: "SESA2023 Propulsion"
type: concept
stream: "Section 1: Introduction and Fundamentals"
aliases: ["state postulate", "ideal gas", "perfect gas", "specific heats"]
tags: [sesa2023, concept, thermodynamics]
status: complete
parent_lectures: ["[[SESA2023 W02 - Thermodynamics, Mixtures, SFEE and Isentropic Efficiency]]"]
related_concepts: ["[[Gas Mixtures and Dalton's Law]]", "[[Steady Flow Energy Equation]]", "[[Entropy Change of a Perfect Gas]]"]
sources: ["02 - Sources/Lectures/Week 02 - Thermodynamics.pdf"]
---

# Two-Property Rule and Perfect Gas Model

The state postulate says the state of a simple compressible system is fixed by two independent intensive properties. An **ideal gas** obeys $p = \rho RT$, with $u$, $h$, $c_v$ and $c_p$ depending on temperature only; a **perfect gas** is an ideal gas with constant $c_p$ and $c_v$, so $\Delta h = c_p\Delta T$ and $\Delta u = c_v\Delta T$.

The word "independent" matters. For an ideal gas, $T$ and $h$ (or $T$ and $u$) are not independent, and during a phase change $p$ and $T$ are not, so a third property such as $p$ or $v$ is needed. The ideal-gas model assumes elastic collisions, negligible molecular volume and intermolecular forces, and translational kinetic energy only. It breaks down near a phase change and as $p$ approaches the critical pressure (38 bar for air), although at 20 bar the error in $\rho$ is only about 1 %. The perfect-gas model is accurate for small temperature changes and for monatomic gases such as argon, but for air $c_p$ climbs noticeably above about 600 K and combustion products have a higher $c_p$ still. That is why cycle calculations use a cold-air $c_p = 1005$ J/kg K upstream of the burner and a product $c_p$ of 1100–1250 downstream. The relations between the properties are $c_p-c_v = R$, $\gamma = c_p/c_v$, $c_p = \gamma R/(\gamma-1)$ and $R = \bar R/M$ with $\bar R = 8.3145$ kJ kmol⁻¹ K⁻¹.

PS2 Q2.4 checks the model against real-gas data from CoolProp. A 10:1 compressor from 300 K gives 579.2 K as a perfect gas and 574.5 K as a real gas, while a burner adding 500 kJ/kg at 600 K gives 1097.5 K and 1052.6 K: the perfect-gas model is excellent for compression and noticeably wrong for large heating. Typical values are $R = 287$, $c_p = 1005$ and $\gamma = 1.40$ for air, $c_p = 1100$–1150 and $\gamma = 1.33$ for combustion products, and $\gamma = 1.22$–1.24 with $R\approx360$–400 J kg⁻¹ K⁻¹ for rocket exhaust.

## Related

- [[Gas Mixtures and Dalton's Law]] · [[Steady Flow Energy Equation]] · [[Entropy Change of a Perfect Gas]]
