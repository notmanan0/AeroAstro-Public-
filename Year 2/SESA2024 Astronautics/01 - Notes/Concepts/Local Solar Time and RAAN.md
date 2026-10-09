---
title: "Local Solar Time and RAAN"
module: "SESA2024 Astronautics"
type: concept
stream: "Remote Sensing Case Study"
aliases: ["LST", "local solar time", "node time", "dawn-dusk orbit", "noon-midnight orbit", "10:30 descending node"]
tags: [sesa2024, concept, remote-sensing]
status: complete
parent_lectures: ["[[SESA2024 13 - Calculating Orbital Elements for a Remote Sensing Mission]]"]
related_concepts: ["[[Sun-Synchronous Orbit]]", "[[Eclipse Duration]]", "[[Keplerian Orbital Elements]]"]
sources: ["02 - Sources/Lectures/Chapter 11/SESA2024 Astronautics - Chapter 11_Calculating Orbital Elements_Part 2_V1.pdf"]
---

# Local Solar Time and RAAN

## Definition

> [!note] Definition
> In a Sun-synchronous orbit, $\phi = \alpha_S-\Omega$ is fixed. $\phi$ sets the **LST at the nodes**: LST = 12:00 at $\phi = 0$, and 15° of $\phi$ is 1 hour. Hence
> $$\Omega_{launch} = \alpha_{S,launch}-\phi$$

## Explanation
| Node LST | $\phi$ | $\Omega$ at launch | Eclipse |
|---|---|---|---|
| 12:00 / 00:00 (noon–midnight) | 0° / 180° | $\alpha_S$ | longest, every orbit |
| 06:00 / 18:00 (dawn–dusk) | 90° / 270° | $\alpha_S-90^\circ$ | little or none (seasonal only) |
| 10:30 | 22.5° | $\alpha_S-22.5^\circ$ | intermediate |

- **Ascending and descending nodes are 12 h apart** in LST.
- At the spring equinox, $\alpha_S = 0^\circ$. At the summer solstice, 90°; autumn equinox, 180°; winter solstice, 270°.
- **European EO**: a descending node near **10:30 am** passes over Europe at 10:30–11:00, before afternoon convective cloud builds up (2015/16 Q1(vi)).
- **Consequences**: the LST sets the Sun angle for the payload and the eclipse length, which drives battery, array, array articulation, heater and radiator sizing.

![[ast_lst_orbit_planes.png|480]]

## Examples
- Lecture: a 10:30 **ascending** node at an equinox launch gives $\Omega$ = 337.5°. A 10:30 **descending** node gives **157.5°**.
- 2023/24 A7: 06:00 descending node, so 18:00 ascending.
- 2022/23 A7: descending node with the Sun on the far side of the Earth means **00:00 (midnight)**.
- 2024/25 B3: a 1:30 pm ascending node is 1:30 am descending ($\phi$ = −22.5°, "PM orbit", like Aqua and OCO-2).
- 2022/23 B3(iii): a 6 pm descending node is a 6 am ascending node, a dawn–dusk orbit. It flies along the terminator, so in principle there is no eclipse at the equinox.

## Related
- [[Sun-Synchronous Orbit]] · [[Eclipse Duration]] · [[Keplerian Orbital Elements]]

## Sources
- Chapter 11 "Calculating orbital elements part 2" and worked example part 2
