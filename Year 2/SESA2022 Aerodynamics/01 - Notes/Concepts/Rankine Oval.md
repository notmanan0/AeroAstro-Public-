---
title: "Rankine Oval"
module: "SESA2022 Aerodynamics"
type: concept
stream: "Topic 3: Potential Flow"
aliases: ["Rankine body", "source-sink pair in uniform flow", "Rankine half-body", "slender oval"]
tags: [sesa2022, concept, potential-flow]
status: complete
parent_lectures: ["[[SESA2022 T3 - Potential Flow]]"]
related_concepts: ["[[Elementary Potential Flows]]", "[[Flow Past a Cylinder]]"]
sources: ["02 - Sources/PF/Topic 3 Potential Flow.pdf", "02 - Sources/Lectures/SESA2022 Lecture 11.txt … Lecture 16.txt (2025-26 transcripts)"]
---

# Rankine Oval

A uniform flow $V_\infty$ plus an equal-strength source ($+\Lambda$ at $x = -b$) and sink ($-\Lambda$ at $x = +b$) gives a closed oval body, the **Rankine oval**, whose surface is the dividing streamline $\psi = 0$:

$$
\psi = V_\infty r\sin\theta+\frac{\Lambda}{2\pi}(\theta_1-\theta_2) .
$$

The stagnation points lie on the axis where $u = 0$,

$$
x_s = \pm\sqrt{b^2+\frac{\Lambda b}{\pi V_\infty}},
$$

or, in dimensionless form with $b = 1$ and $\sigma = \Lambda/(2\pi V_\infty)$, $x_s = \pm\sqrt{1+2\sigma}$. The half-thickness $h$ comes from $\psi(0,h) = 0$, which is transcendental, $h = \sigma(\pi-2\tan^{-1}h)$; the slender-body approximation gives $h\approx\pi\sigma/(1+2\sigma)$. The fastest flow is at the top of the oval, $u = V_\infty[1+2\sigma/(1+h^2)]$ in unit-$b$ form, which gives the minimum $C_p$.

Three variations are worth knowing. As $b\to0$ with $\Lambda b$ fixed, the source–sink pair becomes a doublet and the oval becomes a circle ([[Flow Past a Cylinder]]). Unequal strengths don't close: with a stronger sink the dividing streamline stays open and the sink swallows a stream of half-width $|\Lambda_1+\Lambda_2|/(2V_\infty)$ ([[SESA2022 Exam 2014-15 Solutions]] Q2). And replacing the source–sink pair with a counter-rotating vortex pair gives an oval of recirculating fluid ([[SESA2022 Exam 2013-14 Solutions]] Q2).

![[pf_rankine_oval.png|520]]

[[SESA2022 Exam 2015-16 Solutions]] Q1 works the dimensionless oval, with a slender-body $y_{top} = 0.5$ and $C_p = -0.887$.

## Related

- Full derivation and worked examples: [[SESA2022 T3 - Potential Flow#8. Example 3: Rankine oval (uniform flow + source at −b + sink at +b)|T3 §8]]
- [[Elementary Potential Flows]] · [[Flow Past a Cylinder]]
