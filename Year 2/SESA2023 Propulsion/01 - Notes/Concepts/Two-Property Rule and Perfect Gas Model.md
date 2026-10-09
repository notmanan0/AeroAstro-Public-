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

## Definition

> [!note] Definition
> - **State postulate**: the state of a simple compressible system is fixed by two **independent** intensive properties.
> - **Ideal gas**: $p = \rho RT$, and $u$, $h$, $c_v$, $c_p$ depend on $T$ only.
> - **Perfect gas**: an ideal gas with **constant** $c_p$ and $c_v$, so $\Delta h = c_p\Delta T$ and $\Delta u = c_v\Delta T$.

## Explanation
- **Independence traps**: for an ideal gas, $T$ and $h$ (or $T$ and $u$) are not independent. During a phase change, $p$ and $T$ are not independent. You need a third property such as $p$ or $v$.
- **Ideal-gas assumptions**: elastic collisions, negligible molecular volume and intermolecular forces, translational KE only. It breaks down near phase change and as $p\to p_{crit}$ (38 bar for air). At 20 bar the error in $\rho$ is only about 1 %.
- **Perfect gas**: accurate for small $\Delta T$ and monatomic gases (Ar). For air, $c_p$ climbs noticeably above about 600 K, and combustion products have a still higher $c_p$. Hence the practice of a "cold air" $c_p = 1005$ upstream of the burner and a "product" $c_p = 1100$–1250 downstream.
- Relations: $c_p-c_v = R$, $\gamma = c_p/c_v$, $c_p = \gamma R/(\gamma-1)$, $R = \bar R/M$ with $\bar R = 8.3145$ kJ kmol⁻¹ K⁻¹.
- **Real-gas checks** with CoolProp (PS2 Q2.4): a 10:1 compressor from 300 K gives 579.2 K as a perfect gas and 574.5 K as a real gas. A burner adding 500 kJ/kg at 600 K gives 1097.5 K as a perfect gas and 1052.6 K as a real gas. The perfect-gas model is excellent for compression and noticeably wrong for large heating.

## Examples
- Air: $R = 287$, $c_p = 1005$, $\gamma = 1.40$. Products (typical): $c_p = 1100$–1150, $\gamma = 1.33$.
- Rocket exhaust: $\gamma = 1.22$–1.24, $R\approx360$–400 J kg⁻¹ K⁻¹.

## Related
- [[Gas Mixtures and Dalton's Law]] · [[Steady Flow Energy Equation]] · [[Entropy Change of a Perfect Gas]]

## Sources
- Week 2 notes §2.2; Lecture 4
