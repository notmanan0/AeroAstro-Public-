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
sources: ["02 - Sources/Stability/Topic 6 Aircraft aerodynamics and static stability_v2.pdf", "02 - Sources/Lectures/SESA2022 Lecture 2025-11-14.txt … 2025-11-25.txt (2025-26 transcripts)"]
---

# Manoeuvre Point and Manoeuvre Margin

The **manoeuvre point** $h_m$ is the CG position that gives neutral stability in a steady pull-up, with load factor $n>1$ and pitch rate $q = V/R$. The **manoeuvre margin** is $H_m = h_m-h$:

$$
h_m = h_0+K\frac{C_{L_{T,\alpha}}}{C_{L_\alpha}+C_{L_{T,\alpha}}\frac{S_T}{S}},\qquad C_{L_{T,\alpha}} = k\frac{1-\epsilon_\alpha+\Phi C_{L_\alpha}}{1-k\Phi\frac{S_T}{S}},\qquad \Phi = \frac{\rho Sl}{2m}.
$$

In a pull-up the tail moves down through the air at $ql$, which adds an incidence $\Delta\alpha_T = ql/V = (n-1)C_W\Phi$. This is a pitch-damping effect that resists the rotation, and it makes $C_{L_{T,\alpha}}$ larger in the manoeuvre, so $h_m$ lies aft of the neutral point $h_n$: an aircraft is more stable when manoeuvring than in 1-g flight. The size of the effect scales with the mass parameter $\Phi\propto\rho$, so it is larger for light aircraft and shrinks at altitude, where aircraft feel less stable and more twitchy. The load factor is $n = L^*/W = 1+V^2/(gR)$, and the stick force per g, which is related to $H_m$, has a certified minimum to stop pilots over-stressing the aircraft by accident.

Practice: [[SESA2022 Examples Sheet 6 - Static Stability Solutions]] and [[SESA2022 Static Stability Past Paper Questions Solutions]].

## Related

- Full derivation and worked examples: [[SESA2022 T6 - Aircraft Aerodynamics and Static Stability#4. Manoeuvre stability (20 Nov lecture)|T6 §4]]
- [[Neutral Point and Static Margin]] · [[Stick-Fixed vs Stick-Free Stability]]
