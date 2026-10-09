---
title: "Manoeuvre Point and Manoeuvre Margin"
module: "SESA2022 Aerodynamics"
type: concept
stream: "Topic 6: Aircraft Aerodynamics and Static Stability"
aliases: ["manoeuvre point", "manoeuvre margin", "pull-up", "pitch damping", "mass parameter"]
tags: [sesa2022, concept, stability]
status: complete
parent_lectures: ["[[SESA2022 T6 - Aircraft Aerodynamics and Static Stability]]"]
related_concepts: ["[[Neutral Point and Static Margin]]", "[[Stick-Fixed vs Stick-Free Stability]]"]
sources: ["02 - Sources/Stability/Topic 6 Aircraft aerodynamics and static stability_v2.pdf"]
---

# Manoeuvre Point and Manoeuvre Margin

## Definition

> [!note] Definition
> The **manoeuvre point** $h_m$ is the CG position for neutral stability during a steady pull-up (load factor $n>1$, pitch rate $q = V/R$). The **manoeuvre margin** is $H_m = h_m-h$:
>
> $$h_m = h_0+K\frac{C_{L_{T,\alpha}}}{C_{L_\alpha}+C_{L_{T,\alpha}}\frac{S_T}{S}},\qquad C_{L_{T,\alpha}} = k\frac{1-\epsilon_\alpha+\Phi C_{L_\alpha}}{1-k\Phi\frac{S_T}{S}},\qquad \Phi = \frac{\rho Sl}{2m}$$

## Explanation
- In a pull-up the tail moves down through the air at $ql$. That adds incidence $\Delta\alpha_T = ql/V = (n-1)C_W\Phi$, a **pitch-damping** effect that resists rotation.
- Because $C_{L_{T,\alpha}}$ is larger in the manoeuvre, $h_m$ is **aft** of $h_n$. The aircraft is **more stable manoeuvring than in 1-g flight**.
- The effect scales with the **mass parameter** $\Phi\propto\rho$. It shrinks at altitude, where aircraft feel less stable and more "twitchy", and it is larger for light aircraft.
- **Load factor**: $n = L^*/W = 1+V^2/(gR)$.
- **Stick force per g** relates to $H_m$. Certification requires a minimum value to prevent inadvertent over-stressing.

## Examples
- [[SESA2022 Examples Sheet 6 - Static Stability Solutions]]
- [[SESA2022 Static Stability Past Paper Questions Solutions]]

## Related
- Parent lectures: [[SESA2022 T6 - Aircraft Aerodynamics and Static Stability]]
- Related concepts: [[Neutral Point and Static Margin]], [[Stick-Fixed vs Stick-Free Stability]]

## Sources
- `02 - Sources/Stability/Topic 6 Aircraft aerodynamics and static stability_v2.pdf`
