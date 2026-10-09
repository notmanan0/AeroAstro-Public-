---
title: "Elementary Potential Flows"
module: "SESA2022 Aerodynamics"
type: concept
stream: "Topic 3: Potential Flow"
aliases: ["LEGO bricks", "source", "sink", "doublet", "vortex", "uniform flow"]
tags: [sesa2022, concept, potential-flow]
status: complete
parent_lectures: ["[[SESA2022 T3 - Potential Flow]]"]
related_concepts: ["[[Streamfunction and Velocity Potential]]", "[[Flow Past a Cylinder]]", "[[Rankine Oval]]", "[[Method of Images]]"]
sources: ["02 - Sources/PF/Topic 3 Potential Flow.pdf"]
---

# Elementary Potential Flows

## Definition

> [!note] Definition
> The building blocks ("LEGO bricks") of 2D potential flow. Each satisfies Laplace's equation, so any sum of them is also a valid flow.

| Element | $\psi$ | $\phi$ | Velocity |
|---|---|---|---|
| Uniform flow $V_\infty$ | $V_\infty r\sin\theta$ | $V_\infty r\cos\theta$ | $u = V_\infty$ |
| Source/sink $\Lambda$ (+ source) | $\dfrac{\Lambda}{2\pi}\theta$ | $\dfrac{\Lambda}{2\pi}\ln r$ | $u_r = \dfrac{\Lambda}{2\pi r}$ |
| Vortex $\Gamma$ (+ **clockwise**, course convention) | $\dfrac{\Gamma}{2\pi}\ln r$ | $-\dfrac{\Gamma}{2\pi}\theta$ | $u_\theta = -\dfrac{\Gamma}{2\pi r}$ |
| Doublet $\kappa$ | $-\dfrac{\kappa}{2\pi}\dfrac{\sin\theta}{r}$ | $\dfrac{\kappa}{2\pi}\dfrac{\cos\theta}{r}$ | dipole field |
| Corner/wedge flow | $U r^n\sin n\theta$ | $U r^n\cos n\theta$ | flow in a wedge of angle $\pi/n$ |

## Explanation
- **Sign conventions matter.** The course formula sheets define $\Gamma>0$ as **clockwise**, which gives positive lift $L' = \rho V_\infty\Gamma$ for flow from left to right. Some years write $\phi_{doublet}$ with the opposite sign. Always check the rubric.
- An element at $(x_0,y_0)$ uses $r^2 = (x-x_0)^2+(y-y_0)^2$ and $\theta = \tan^{-1}\frac{y-y_0}{x-x_0}$. A useful identity: $\frac{\Lambda}{2\pi}\ln r = \frac{\Lambda}{4\pi}\ln r^2$.
- **Free vortex**: $V_\theta = K/r$ is irrotational everywhere except the core, so Bernoulli holds *across* streamlines. Examples are a channel bend or a bathtub drain.
- **Recipe for a problem**:
  1. Superpose the elements.
  2. Find stagnation points ($u = v = 0$).
  3. Evaluate $\psi$ there, which gives the dividing streamline (the body).
  4. Get the pressure from Bernoulli: $C_p = 1-|\mathbf V|^2/V_\infty^2$.

## Examples
- Source plus sink in a stream: [[SESA2022 Exam 2014-15 Solutions]] Q2.
- Free-vortex channel bend: [[SESA2022 Exam 2017-18 Solutions]] Q1.
- Corner flow: [[SESA2022 Exam 2019-20 Solutions]] Q1. Corner plus source: [[SESA2022 Exam 2024-25 Solutions]] Q2.
- [[SESA2022 Tutorial 3 - Potential Flow Solutions]].

## Related
- Parent lectures: [[SESA2022 T3 - Potential Flow]]
- Related concepts: [[Streamfunction and Velocity Potential]], [[Flow Past a Cylinder]], [[Rankine Oval]], [[Method of Images]]

## Sources
- `02 - Sources/PF/Topic 3 Potential Flow.pdf`
