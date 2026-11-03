---
title: "Elementary Potential Flows"
module: "SESA2022 Aerodynamics"
type: concept
stream: "Topic 3: Potential Flow"
aliases: ["LEGO bricks", "source", "sink", "doublet", "vortex", "uniform flow", "elementary flows"]
tags: [sesa2022, concept, potential-flow]
status: complete
parent_lectures: ["[[SESA2022 T3 - Potential Flow]]"]
related_concepts: ["[[Streamfunction and Velocity Potential]]", "[[Flow Past a Cylinder]]", "[[Rankine Oval]]", "[[Method of Images]]"]
sources: ["02 - Sources/PF/Topic 3 Potential Flow.pdf", "02 - Sources/Lectures/SESA2022 Lecture 11.txt … Lecture 16.txt (2025-26 transcripts)"]
---

# Elementary Potential Flows

The elementary potential flows are the building blocks, the lecture's "LEGO bricks", of two-dimensional potential flow. Each satisfies Laplace's equation, so any sum of them is also a valid flow.

| Element | $\psi$ | $\phi$ | Velocity |
|---|---|---|---|
| Uniform flow $V_\infty$ | $V_\infty r\sin\theta$ | $V_\infty r\cos\theta$ | $u = V_\infty$ |
| Source/sink $\Lambda$ (+ source) | $\dfrac{\Lambda}{2\pi}\theta$ | $\dfrac{\Lambda}{2\pi}\ln r$ | $u_r = \dfrac{\Lambda}{2\pi r}$ |
| Vortex $\Gamma$ (+ clockwise, course convention) | $\dfrac{\Gamma}{2\pi}\ln r$ | $-\dfrac{\Gamma}{2\pi}\theta$ | $u_\theta = -\dfrac{\Gamma}{2\pi r}$ |
| Doublet $\kappa$ | $-\dfrac{\kappa}{2\pi}\dfrac{\sin\theta}{r}$ | $\dfrac{\kappa}{2\pi}\dfrac{\cos\theta}{r}$ | dipole field |
| Corner/wedge flow | $U r^n\sin n\theta$ | $U r^n\cos n\theta$ | flow in a wedge of angle $\pi/n$ |

The sign conventions need care. The course formula sheets take $\Gamma>0$ as clockwise, which gives positive lift $L' = \rho V_\infty\Gamma$ for flow from left to right, and some years write $\phi_{doublet}$ with the opposite sign, so check the rubric. An element placed at $(x_0,y_0)$ uses $r^2 = (x-x_0)^2+(y-y_0)^2$ and $\theta = \tan^{-1}[(y-y_0)/(x-x_0)]$, and the identity $\frac{\Lambda}{2\pi}\ln r = \frac{\Lambda}{4\pi}\ln r^2$ saves a square root. The free vortex, $V_\theta = K/r$, is irrotational everywhere except at its core, so Bernoulli holds across streamlines as well as along them; a channel bend and a bathtub drain are the standard examples.

A problem is solved the same way each time: superpose the elements, find the stagnation points where $u = v = 0$, evaluate $\psi$ there to get the dividing streamline (the body surface), and get the pressure from Bernoulli, $C_p = 1-|\mathbf V|^2/V_\infty^2$.

Past-paper uses: a source plus sink in a stream ([[SESA2022 Exam 2014-15 Solutions]] Q2); a free-vortex channel bend ([[SESA2022 Exam 2017-18 Solutions]] Q1); corner flow ([[SESA2022 Exam 2019-20 Solutions]] Q1) and corner flow plus a source ([[SESA2022 Exam 2024-25 Solutions]] Q2); and [[SESA2022 Tutorial 3 - Potential Flow Solutions]].

## Related

- Full derivation and worked examples: [[SESA2022 T3 - Potential Flow#4. The LEGO bricks|T3 §4]]
- [[Streamfunction and Velocity Potential]] · [[Flow Past a Cylinder]] · [[Rankine Oval]] · [[Method of Images]]
