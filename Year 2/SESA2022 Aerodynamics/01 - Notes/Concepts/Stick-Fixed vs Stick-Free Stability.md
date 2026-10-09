---
title: "Stick-Fixed vs Stick-Free Stability"
module: "SESA2022 Aerodynamics"
type: concept
stream: "Topic 6: Aircraft Aerodynamics and Static Stability"
aliases: ["stick free", "stick fixed", "elevator float", "trim tab", "hinge moment"]
tags: [sesa2022, concept, stability]
status: complete
parent_lectures: ["[[SESA2022 T6 - Aircraft Aerodynamics and Static Stability]]"]
related_concepts: ["[[Neutral Point and Static Margin]]", "[[Trailing-Edge Flap in Thin Aerofoil Theory]]"]
sources: ["02 - Sources/Stability/Topic 6 Aircraft aerodynamics and static stability_v2.pdf"]
---

# Stick-Fixed vs Stick-Free Stability

## Definition

> [!note] Definition
> - **Stick fixed**: the pilot holds the elevator at a fixed angle $\eta$ against the hinge moment $C_{M_H}\ne0$.
> - **Stick free**: the trim tab $\beta$ is set so that $C_{M_H} = 0$. The elevator is then free to **float** in response to changes in tail incidence.

## Explanation
**Models**:

$$
C_{L_T} = a_1\alpha_{T_{eff}}+a_2\eta+a_3\beta,\qquad C_{M_H} = b_1\alpha_{T_{eff}}+b_2\eta+b_3\beta
$$

$b_1$ and $b_2$ are usually negative.

**Floating.** Setting $C_{M_H} = 0$ gives $\eta = -(b_1\alpha_{T_{eff}}+b_3\beta)/b_2$. When a gust raises $\alpha_{T_{eff}}$, the elevator floats **up** ($\Delta\eta<0$), so the tail generates less extra lift:

$$
\bar a_1 = a_1-a_2\frac{b_1}{b_2}<a_1,\qquad \bar a_3 = a_3-a_2\frac{b_3}{b_2}
$$

**Consequences**:
- $\bar k<k$, so $C_{L_{T,\alpha}}$ is lower and the **stick-free neutral point is further forward**: $H_{s,free}<H_{s,fixed}$.
- A **horn balance** or aerodynamic balance reduces $|b_1|$ and $|b_2|$, which reduces stick forces. Over-balancing can make $b_1\to0$ or positive, which is dangerous.
- **Trim tab principle**: deflect the tab one way to create a hinge moment that drives the elevator the other way until $C_{M_H} = 0$, giving hands-off flight.

**Trim algorithm (stick free)**. Solve

$$
\begin{pmatrix}a_2&a_3\\b_2&b_3\end{pmatrix}\begin{pmatrix}\eta\\\beta\end{pmatrix} = \begin{pmatrix}C_{L_T}-a_1\alpha_{T_{eff}}\\-b_1\alpha_{T_{eff}}\end{pmatrix}
$$

## Examples
- [[SESA2022 Examples Sheet 6 - Static Stability Solutions]]
- [[SESA2022 Static Stability Past Paper Questions Solutions]]

## Related
- Parent lectures: [[SESA2022 T6 - Aircraft Aerodynamics and Static Stability]]
- Related concepts: [[Neutral Point and Static Margin]], [[Trailing-Edge Flap in Thin Aerofoil Theory]], [[Manoeuvre Point and Manoeuvre Margin]]

## Sources
- `02 - Sources/Stability/Topic 6 Aircraft aerodynamics and static stability_v2.pdf`
