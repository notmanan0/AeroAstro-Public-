---
title: "Absorptance and Emittance"
module: "SESA2024 Astronautics"
type: concept
stream: "Spacecraft Subsystems"
aliases: ["solar absorptance", "emittance", "emissivity", "alpha/epsilon", "surface finishes", "Kirchhoff's law"]
tags: [sesa2024, concept, thermal-control]
status: complete
parent_lectures: ["[[SESA2024 10 - Thermal Control]]"]
related_concepts: ["[[Blackbody Radiation]]", "[[Spacecraft Thermal Balance Equation]]", "[[Passive vs Active Thermal Control]]"]
sources: ["02 - Sources/Lectures/Chapter 10/2025 WEEK 8 - Chapter 10 - Thermal Control - Lecture slides - complete.pdf"]
---

# Absorptance and Emittance

## Definition

> [!note] Definition
> - Spectral **absorptance**: $\alpha_\lambda = q_a(\lambda)/q_i(\lambda)$. With reflectance $\rho$ and transmittance $\tau$, $\alpha+\rho+\tau = 1$; for opaque surfaces $\alpha+\rho = 1$.
> - **Solar absorptance**: $\alpha_S = \int\alpha_\lambda q_S\,d\lambda/\int q_S\,d\lambda$, about the 0.3–2.0 µm band (97 % of solar energy).
> - **Emittance**: $\varepsilon = q(T)/q_{BB}(T)\le1$, so $q = \varepsilon\sigma T^4$.

## Explanation
- $\alpha$ depends on **both the material and the source spectrum**. White paint absorbs little visible sunlight ($\alpha_S\approx0.2$) but is nearly black in the IR ($\varepsilon\approx0.9$).
- **Kirchhoff's law**: $\alpha_\lambda = \varepsilon_\lambda$ at each wavelength. So for IR from the ~290 K Earth, the IR absorptance equals $\varepsilon$.
- When sunlight dominates, **$T\propto(\alpha_S/\varepsilon)^{1/4}$**.

| Finish | $\alpha_S$ | $\varepsilon$ | $\alpha_S/\varepsilon$ | Effect |
|---|---|---|---|---|
| Second-surface mirror (SSM, OSR) | ~0.08 | ~0.8 | 0.1 | very cold (radiators) |
| White paint | 0.1–0.2 | 0.9 | ~0.2 | cold |
| Black paint | 0.9 | 0.9 | 1 | medium |
| Polished aluminium / gold | 0.1–0.3 | 0.03–0.05 | 3–6 | hot |
| SiO-Al "dark mirror" (exam table) | 0.90 | 0.03 | 30 | very hot |
| MLI outer layer (exam table) | 0.09 | 0.03 | 3 | warm; decoupled |

- UV and atomic oxygen raise $\alpha_S$ over the mission, so spacecraft **warm with age**.
- The ratio matters most for sunlit, low-dissipation bodies. In eclipse with $P = 0$, $\varepsilon$ cancels.

## Examples
- A spacecraft at L1 facing the Sun (2021/22 A5): use a low $\alpha_S/\varepsilon$ finish on the Sun face (white paint, OSR/SSM) to reject heat.
- Why $\alpha_S/\varepsilon$ matters for passive control (2022/23 A5, 3 marks).

![[ast_thermal_alpha_eps.png|540]]

## Related
- [[Blackbody Radiation]] · [[Spacecraft Thermal Balance Equation]] · [[Passive vs Active Thermal Control]]

## Sources
- Chapter 10 slides 9–14, 19, 25–26
