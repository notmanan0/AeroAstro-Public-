---
title: "Blackbody Radiation"
module: "SESA2024 Astronautics"
type: concept
stream: "Spacecraft Subsystems"
aliases: ["blackbody", "Planck's law", "Wien's law", "Stefan-Boltzmann"]
tags: [sesa2024, concept, thermal-control]
status: complete
parent_lectures: ["[[SESA2024 10 - Thermal Control]]"]
related_concepts: ["[[Absorptance and Emittance]]", "[[Spacecraft Thermal Balance Equation]]"]
sources: ["02 - Sources/Lectures/Chapter 10/2025 WEEK 8 - Chapter 10 - Thermal Control - Lecture slides - complete.pdf"]
---

# Blackbody Radiation

## Definition

> [!note] Definition
> A **blackbody** absorbs **all** radiation incident on it ($\alpha_\lambda = 1$, $\rho_\lambda = 0$ at every $\lambda$), and at any temperature emits the **maximum possible** thermal radiation. It is a useful theoretical ideal.

## Explanation
- **Planck's law**:
$$q_\lambda = \frac{2\pi hc^2}{\lambda^5\left[\exp\left(\dfrac{ch}{k\lambda T}\right)-1\right]}\ (\text{W m}^{-2}\,\mu\text{m}^{-1})$$
  with $h$ = 6.625 × 10⁻³⁴ J s, $k$ = 1.380 × 10⁻²³ J/K, $c$ = 3 × 10⁸ m/s.
- **Wien's displacement law**: $\lambda_{max}T = 2.898\times10^{-3}$ m K.
  - The Sun at 5800 K peaks at 0.5 µm (visible), so we use $\alpha_S$.
  - The Earth and spacecraft at about 290 K peak at about **10 µm** (IR), so we use $\varepsilon$.
- **Stefan–Boltzmann**: $q_{BB} = \int_0^\infty q_\lambda\,d\lambda = \sigma T^4$, with $\sigma$ = 5.669 × 10⁻⁸ W m⁻² K⁻⁴.
- Real surfaces: $q = \varepsilon\sigma T^4$.
- Because solar and thermal spectra barely overlap, a surface can have independent $\alpha_S$ and $\varepsilon$. That is what makes passive thermal control possible.

## Examples
- 2016/17 Q3(i): "Explain what is meant by a blackbody" (3 marks).
- A sphere with $\alpha_S = \varepsilon$ at 1 AU: $T = (1370/4\sigma)^{1/4}$ = 278 K ≈ 5 °C.

## Related
- [[Absorptance and Emittance]] · [[Spacecraft Thermal Balance Equation]]

## Sources
- Chapter 10 slides 10–18 (equations 10.1–10.6)
