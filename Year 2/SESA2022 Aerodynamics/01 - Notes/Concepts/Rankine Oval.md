---
title: "Rankine Oval"
module: "SESA2022 Aerodynamics"
type: concept
stream: "Topic 3: Potential Flow"
aliases: ["Rankine body", "source-sink pair in uniform flow"]
tags: [sesa2022, concept, potential-flow]
status: complete
parent_lectures: ["[[SESA2022 T3 - Potential Flow]]"]
related_concepts: ["[[Elementary Potential Flows]]", "[[Flow Past a Cylinder]]"]
sources: ["02 - Sources/PF/Topic 3 Potential Flow.pdf"]
---

# Rankine Oval

## Definition

> [!note] Definition
> A uniform flow $V_\infty$ plus an **equal-strength** source ($+\Lambda$ at $x = -b$) and sink ($-\Lambda$ at $x = +b$). The dividing streamline $\psi = 0$ closes into an oval body:
>
> $$\psi = V_\infty r\sin\theta+\frac{\Lambda}{2\pi}(\theta_1-\theta_2)$$

## Explanation
- **Stagnation points** on the axis, at $u = 0$:

$$
x_s = \pm\sqrt{b^2+\frac{\Lambda b}{\pi V_\infty}}
$$

   In dimensionless form ($b = 1$, $\sigma = \Lambda/(2\pi V_\infty)$), $x_s = \pm\sqrt{1+2\sigma}$.
- **Half-thickness** $h$ comes from $\psi(0,h) = 0$. The equation is transcendental ($h = \sigma(\pi-2\tan^{-1}h)$). The slender-body approximation gives $h\approx\pi\sigma/(1+2\sigma)$.
- The **maximum velocity** is at the top: $u = V_\infty\left(1+\dfrac{2\sigma}{1+h^2}\right)$ in unit-$b$ form. That gives the minimum $C_p$.
- As $b\to0$ with $\Lambda b$ fixed, the source–sink pair becomes a **doublet**, and the oval becomes a circle ([[Flow Past a Cylinder]]).
- **Unequal strengths** don't close. With a stronger sink, the dividing streamline is open and the sink swallows a stream of half-width $|\Lambda_1+\Lambda_2|/(2V_\infty)$.
- Replacing the source–sink pair by a counter-rotating **vortex pair** gives an oval of recirculating fluid ([[SESA2022 Exam 2013-14 Solutions]] Q2).

![[pf_rankine_oval.png|520]]

## Examples
- Dimensionless oval, slender-body $y_{top} = 0.5$, $C_p = -0.887$: [[SESA2022 Exam 2015-16 Solutions]] Q1.
- Unequal source and sink: [[SESA2022 Exam 2014-15 Solutions]] Q2.

## Related
- Parent lectures: [[SESA2022 T3 - Potential Flow]]
- Related concepts: [[Elementary Potential Flows]], [[Flow Past a Cylinder]]

## Sources
- `02 - Sources/PF/Topic 3 Potential Flow.pdf`
