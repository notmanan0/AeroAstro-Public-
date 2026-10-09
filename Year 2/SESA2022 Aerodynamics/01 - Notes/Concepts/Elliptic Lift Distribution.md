---
title: "Elliptic Lift Distribution"
module: "SESA2022 Aerodynamics"
type: concept
stream: "Topic 5: Finite Wing Theory"
aliases: ["ELD", "elliptic loading", "elliptic wing"]
tags: [sesa2022, concept, finite-wing-theory]
status: complete
parent_lectures: ["[[SESA2022 T5 - Finite Wing Theory]]"]
related_concepts: ["[[Downwash and Induced Drag]]", "[[Oswald Efficiency Factor]]", "[[Glauert Integrals]]"]
sources: ["02 - Sources/Airfoils and Wings/Topic 5 Finite wing theory_v3_pdf.pdf"]
---

# Elliptic Lift Distribution

## Definition

> [!note] Definition
> A spanwise circulation of elliptic shape, $\Gamma(y) = \Gamma_0\sqrt{1-(2y/b)^2}$ (only $B_1\ne0$). It produces **uniform downwash** and the **minimum induced drag** for a given lift and span.

## Explanation
**Key results**:

$$
w = -\frac{\Gamma_0}{2b},\qquad \alpha_i = \frac{C_L}{\pi AR},\qquad L = \frac\pi4\rho V_\infty b\Gamma_0,\qquad C_L = \frac{\pi b\Gamma_0}{2V_\infty S} = \pi AR\,B_1,\qquad C_{D_i} = \frac{C_L^2}{\pi AR}
$$

- **Mean circulation**: $\bar\Gamma = \frac\pi4\Gamma_0$.
- **How to get it**:
  1. An **elliptic planform** with no twist: $c(y)\propto\Gamma(y)$, so $C_l$ is constant along the span (Spitfire).
  2. A **rectangular planform with geometric washout**: the root section runs at a higher $C_l$, with $C_l(0) = \frac4\pi C_L$.
  3. **Aerodynamic twist**: vary the camber along the span.
  4. **Taper**: a taper ratio of about 0.35–0.45 comes within about 1 % of $e = 1$.
- **Washout for a rectangular ELD wing**:

$$
\Delta\alpha_{twist} = \frac{C_l(0)}{2\pi} = \frac{2C_L}{\pi^2}
$$

  This is **independent of $AR$**, because $\alpha_i$ is uniform and cancels. The root angle is $\alpha(0) = \frac{C_l(0)}{2\pi}+\alpha_{L=0}+\alpha_i$ and the tip angle is $\alpha_{L=0}+\alpha_i$.
- **Drawbacks**: an elliptic planform is hard to build. Its uniform $C_l$ means the whole span stalls at once, with no warning and poor aileron authority at the stall.

## Examples
- Constant downwash derivation and root angle: [[SESA2022 Exam 2018-19 Solutions]] Q3.
- Twist independent of $AR$: [[SESA2022 Exam 2019-20 Solutions]] Q3.
- UAV root and tip angles: [[SESA2022 Exam 2020-21 Solutions]] B Q7.
- Centre-section angle: [[SESA2022 Exam 2022-23 Solutions]] and [[SESA2022 Exam 2023-24 Solutions]].
- Circulation halfway along the semi-span: [[SESA2022 Exam 2017-18 Solutions]] Q3.

## Related
- Parent lectures: [[SESA2022 T5 - Finite Wing Theory]]
- Related concepts: [[Downwash and Induced Drag]], [[Oswald Efficiency Factor]], [[Glauert Integrals]]

## Sources
- `02 - Sources/Airfoils and Wings/Topic 5 Finite wing theory_v3_pdf.pdf`
