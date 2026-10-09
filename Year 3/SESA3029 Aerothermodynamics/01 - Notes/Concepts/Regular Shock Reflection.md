---
title: "Regular Shock Reflection"
module: "SESA3029 Aerothermodynamics"
type: concept
stream: "Block 2: Oblique Shocks and Expansions"
aliases: ["regular reflection", "shock reflection", "reflected shock", "shock reflection from a wall"]
tags: [sesa3029, concept, shock-reflection]
status: complete
parent_lectures: ["[[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method]]"]
related_concepts: ["[[Theta-Beta-Mach Relation]]", "[[Mach Reflection]]", "[[Slip Line]]"]
sources: ["02 - Sources/Lectures/Lecture2-3.pdf"]
---

# Regular Shock Reflection

## Definition

> [!note] Definition
> When an oblique shock (A) meets a solid wall, the flow behind it, which is turned by $\theta$ towards the wall, must be turned back parallel to the wall. A second oblique shock (B) does this, turning the zone-2 flow by the **same** $\theta$, now from $M_2$:
> $$\beta_B=\beta(\theta,M_2),\qquad \phi=\beta_B-\theta\ne\beta_A.$$

## How to solve it

1. Shock A: $\theta$–$\beta$–$M$ at $M_1$ gives $\beta_A$, $M_{n1}$, $p_2/p_1$ and $M_2$.
2. Shock B: the same $\theta$ at $M_2$, measured from $\mathbf V_2$, gives $\beta_B$, $p_3/p_2$ and $M_3$.
3. Chain the ratios: $p_3/p_1=(p_3/p_2)(p_2/p_1)$.

Lecture example: $M_1=3.6$, $\theta=10^\circ$, $p_1=40$ kPa gives $\beta_A=23.90^\circ$, $M_2=2.982$, $\beta_B=27.51^\circ$, $M_3=2.490$, $p_3=189.6$ kPa and $\phi=17.5^\circ$.

## Key points

- **Not specular.** $M_2<M_1$, so the same $\theta$ needs a steeper shock relative to $\mathbf V_2$, and the reflected shock leans closer to the wall ($\phi<\beta_A$).
- **Possible only while $\theta\le\theta_{max}(M_2)$.** Beyond that limit ($16.1^\circ$ at $M_1=2.3$, $24.3^\circ$ at $M_1=3.6$) the pattern becomes a [[Mach Reflection]].
- **Cancellation.** Turning the wall back by $\theta$ where B lands absorbs it.

## Related

- [[Theta-Beta-Mach Relation]] · [[Mach Reflection]] · [[Slip Line]]
- Detail: [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method#1. Regular shock reflection from a wall|W03 §1]] · Worked: [[SESA3029 Example Sheet 1 - Solutions#Q3. Ramp shock reflected from a wall|ES1 Q3]]
