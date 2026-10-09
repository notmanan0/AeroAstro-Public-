---
title: "Repeat Ground Track"
module: "SESA2024 Astronautics"
type: concept
stream: "Remote Sensing Case Study"
aliases: ["Earth-synchronous orbit", "Earth-synchronism", "ground track repeat", "n m parameters", "revisit"]
tags: [sesa2024, concept, remote-sensing, orbital-mechanics]
status: complete
parent_lectures: ["[[SESA2024 12 - Sun- and Earth-Synchronous Orbits]]", "[[SESA2024 13 - Calculating Orbital Elements for a Remote Sensing Mission]]"]
related_concepts: ["[[Sun-Synchronous Orbit]]", "[[Swath Width and Push-Broom Imaging]]", "[[Orbit Control Cycle]]"]
sources: ["02 - Sources/Lectures/Chapter 11/SESA2024 Astronautics - Chapter 11_Calculating Orbital Elements_V1.pdf"]
---

# Repeat Ground Track

## Definition

> [!note] Definition
> An **Earth-synchronous** orbit's ground track repeats exactly after $n$ orbits in $m$ days: $n\Delta\lambda = m\cdot360^\circ$. If it is also Sun-synchronous:
> $$\tau = \frac{m}{n}\,86\,400\ \text{s}$$

## Explanation
- Westward shift per orbit: $\Delta\lambda = 360^\circ(\tau/\tau_E-\tau/\tau_Y)$ (Earth rotation minus nodal regression).
- Substituting gives $\tau = (m/n)\tau_E/(1-\tau_E/\tau_Y) = (m/n)86400$. The SSO plane follows the Sun, so the relevant day is the **solar** day.
- **Why**: the same viewing geometry at a known, fixed revisit interval (change detection).
- **Coverage**: $n\ge2\pi R_E/d$, so that swaths touch or overlap at the equator.
- **Choose $m$ to be an integer close to $n\tau/86400$.** Adjust $n$ by ±1 to bring $\tau$ into band ($n$ is the fine tuning).
- $n/m$ should be in lowest terms. Otherwise the true repeat is shorter.
- Only discrete $(h, i)$ solutions exist.
- Other bodies: Mars $\tau = (m/n)$ 88 509.62 s (derived from the sol and the Mars year), Jupiter $\tau = (m/n)$ 35 733 s.

![[ast_repeat_groundtrack_solutions.png|560]]

## Examples
| Case | $(n,m)$ | $h$ | $i$ |
|---|---|---|---|
| Lecture | (98, 7) | 893.9 km | 99.01° |
| Workbook civil | (89, 6) | 619.0 km | 97.86° |
| 2024/25 A6 | (16, 1) | 274.6 km | 96.59° |
| 2023/24 A6 | (15, 1) | 567.0 km | – |
| 2024/25 B3 (2-day revisit, 700 ± 35 km) | (29, 2) | 725.8 km | 98.30° |
| 2022/23 B3 (daily repeat near 567 km) | (15, 1) | 567.0 km | 97.66° |

## Related
- [[Sun-Synchronous Orbit]] · [[Swath Width and Push-Broom Imaging]] · [[Orbit Control Cycle]]

## Sources
- Chapter 11 lectures (Earth-synchronism, calculating orbital elements)
