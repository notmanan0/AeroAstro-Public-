---
title: "Stick-Fixed vs Stick-Free Stability"
module: "SESA2022 Aerodynamics"
type: concept
stream: "Topic 6: Aircraft Aerodynamics and Static Stability"
aliases: ["stick free", "stick fixed", "elevator float", "trim tab", "hinge moment", "floating elevator"]
tags: [sesa2022, concept, stability]
status: complete
parent_lectures: ["[[SESA2022 T6 - Aircraft Aerodynamics and Static Stability]]"]
related_concepts: ["[[Neutral Point and Static Margin]]", "[[Trailing-Edge Flap in Thin Aerofoil Theory]]"]
sources: ["02 - Sources/Stability/Topic 6 Aircraft aerodynamics and static stability_v2.pdf", "02 - Sources/Lectures/SESA2022 Lecture 2025-11-14.txt … 2025-11-25.txt (2025-26 transcripts)"]
---

# Stick-Fixed vs Stick-Free Stability

Stick fixed, the pilot holds the elevator at a fixed angle $\eta$ against a non-zero hinge moment $C_{M_H}$. Stick free, the trim tab $\beta$ is set so that $C_{M_H} = 0$, and the elevator is then free to float as the tail incidence changes.

The tail lift and hinge moment are modelled as

$$
C_{L_T} = a_1\alpha_{T_{eff}}+a_2\eta+a_3\beta,\qquad C_{M_H} = b_1\alpha_{T_{eff}}+b_2\eta+b_3\beta,
$$

with $b_1$ and $b_2$ usually negative. Setting $C_{M_H} = 0$ gives the floating angle, $\eta = -(b_1\alpha_{T_{eff}}+b_3\beta)/b_2$. When a gust raises $\alpha_{T_{eff}}$ the elevator floats up ($\Delta\eta<0$), so the tail produces less extra lift than it would stick fixed:

$$
\bar a_1 = a_1-a_2\frac{b_1}{b_2}<a_1,\qquad \bar a_3 = a_3-a_2\frac{b_3}{b_2} .
$$

With $\bar k<k$, $C_{L_{T,\alpha}}$ is lower and the stick-free neutral point sits further forward, so $H_{s,free}<H_{s,fixed}$. A horn or aerodynamic balance reduces $|b_1|$ and $|b_2|$ and with them the stick forces, but over-balancing can drive $b_1$ to zero or positive, which is dangerous. The trim tab works by deflecting one way to create a hinge moment that drives the elevator the other way until $C_{M_H} = 0$, giving hands-off flight. To trim stick free, solve

$$
\begin{pmatrix}a_2&a_3\\b_2&b_3\end{pmatrix}\begin{pmatrix}\eta\\\beta\end{pmatrix} = \begin{pmatrix}C_{L_T}-a_1\alpha_{T_{eff}}\\-b_1\alpha_{T_{eff}}\end{pmatrix}.
$$

Practice: [[SESA2022 Examples Sheet 6 - Static Stability Solutions]] and [[SESA2022 Static Stability Past Paper Questions Solutions]].

## Related

- Full derivation and worked examples: [[SESA2022 T6 - Aircraft Aerodynamics and Static Stability#2. Trim: stick fixed and stick free|T6 §2]]
- [[Neutral Point and Static Margin]] · [[Trailing-Edge Flap in Thin Aerofoil Theory]] · [[Manoeuvre Point and Manoeuvre Margin]]
