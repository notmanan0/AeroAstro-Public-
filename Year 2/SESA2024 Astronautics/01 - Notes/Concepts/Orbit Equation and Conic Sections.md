---
title: "Orbit Equation and Conic Sections"
module: "SESA2024 Astronautics"
type: concept
stream: "Mission Analysis"
aliases: ["ellipse equation", "polar equation of an orbit", "conic sections", "semi-latus rectum", "true anomaly equation"]
tags: [sesa2024, concept, orbital-mechanics]
status: complete
parent_lectures: ["[[SESA2024 02 - Kepler's Laws and the Orbit Equation]]", "[[SESA2024 03 - Orbital Elements and Conic Sections]]"]
related_concepts: ["[[Kepler's Laws]]", "[[Keplerian Orbital Elements]]", "[[Vis-Viva Equation]]"]
sources: ["02 - Sources/Lectures/Chapter 5/SESA2024 Astronautics - Chapter 5_orbital elements and conic sections_2025-26_V2.pdf"]
---

# Orbit Equation and Conic Sections

## Definition

> [!note] Definition
>
> $$r = \frac{a(1-e^2)}{1+e\cos\theta} = \frac{h^2/\mu}{1+e\cos\theta}$$
>
> Here $\theta$ is the **true anomaly**, measured from periapsis, and $p = a(1-e^2) = h^2/\mu$ is the semi-latus rectum.

## Explanation
| $e$ | conic | energy |
|---|---|---|
| 0 | circle | $\varepsilon<0$ |
| 0 < e < 1 | ellipse | $\varepsilon<0$ |
| 1 | parabola | $\varepsilon = 0$ |
| > 1 | hyperbola ($a<0$) | $\varepsilon>0$ |

- **Apsides**: $r_p = a(1-e)$ at $\theta = 0$; $r_a = a(1+e)$ at $\theta = 180^\circ$.
- So $a = (r_p+r_a)/2$ and $e = (r_a-r_p)/(r_a+r_p)$.
- **Inverting for $\theta$**:

$$\cos\theta = \frac1e\left[\frac{a(1-e^2)}{r}-1\right]$$

  Choose $\theta$ or $360^\circ-\theta$ from the direction of motion (outbound or inbound).
- Ellipse properties: $b = a\sqrt{1-e^2}$, area $\pi ab$, the focus lies $ae$ from the centre.

![[ast_conic_sections.png|420]]

## Examples
- Starship IFT-2 fragments at 90 km (2023/24 B1(ii)): with $a$ = 5213 km and $e$ = 0.252, $\theta$ = 193° (inbound, after apogee).
- OMOTENASHI entering the Moon's SOI at 281 000 km altitude (2022/23 B1(v)): $\theta$ from its 521 × 379 650 km orbit.
- ʻOumuamua: $e$ = 1.2, $a$ = −1.27 AU, a hyperbolic interstellar visitor.

## Related
- [[Kepler's Laws]] · [[Keplerian Orbital Elements]] · [[Vis-Viva Equation]]

## Sources
- Chapter 5 Lectures 1–4
