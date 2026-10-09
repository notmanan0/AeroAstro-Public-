---
title: "Downwash and Induced Drag"
module: "SESA2022 Aerodynamics"
type: concept
stream: "Topic 5: Finite Wing Theory"
aliases: ["induced drag", "downwash", "induced angle of attack", "lift-induced drag", "vortex drag"]
tags: [sesa2022, concept, finite-wing-theory]
status: complete
parent_lectures: ["[[SESA2022 T5 - Finite Wing Theory]]", "[[SESA2022 T6 - Aircraft Aerodynamics and Static Stability]]"]
related_concepts: ["[[Biot-Savart Law and Helmholtz Theorems]]", "[[Elliptic Lift Distribution]]", "[[Oswald Efficiency Factor]]"]
sources: ["02 - Sources/Airfoils and Wings/Topic 5 Finite wing theory_v3_pdf.pdf"]
---

# Downwash and Induced Drag

## Definition

> [!note] Definition
> The trailing vortices of a finite wing induce a downward velocity $w$ at the wing. This tilts the local relative wind down by the **induced angle** $\alpha_i = -w/V_\infty$. The section's lift, perpendicular to the *local* wind, therefore has a rearward component: the **induced drag**.
> $$\alpha_{eff} = \alpha-\alpha_i,\qquad D_i' = L'\alpha_i,\qquad C_{D_i} = \frac{C_L^2}{\pi AR}(1+\delta) = \frac{C_L^2}{\pi eAR}$$

## Explanation
- Induced drag is the price of producing lift with a finite span. The energy goes into the kinetic energy of the trailing vortex wake. It is **not** caused by viscosity.
- From the Fourier series:

$$
\alpha_i(\theta) = \sum nB_n\frac{\sin n\theta}{\sin\theta},\qquad C_{D_i} = \pi AR\sum nB_n^2
$$

- $C_{D_i}\propto C_L^2$, so it dominates at **low speed / high $C_L$** (take-off, climb, loiter), whereas profile drag dominates at high speed.
- For fixed lift, $D_i = \dfrac{L^2}{\pi qb^2e}$. It depends on **span**, not area, so span loading $L/b$ is what matters.
- **Reducing it**: larger span or $AR$, near-elliptic loading, winglets, and formation flight (flying in another aircraft's upwash).
- **Downwash on the tail**: $\epsilon = \dfrac{C_L}{\pi Ae}$, so $\partial\epsilon/\partial\alpha = \epsilon_\alpha$ reduces the tail's effective incidence (see [[Neutral Point and Static Margin]]).

![[fwt_circulation.png|520]]

## Examples
- Power to overcome induced drag: [[SESA2022 Exam 2017-18 Solutions]] Q3, [[SESA2022 Exam 2021-22 Solutions]] B Q2 and [[SESA2022 Exam 2024-25 Solutions]] Q4.
- Ratio of induced to total drag: [[SESA2022 Exam 2022-23 Solutions]] B Q2.
- [[SESA2022 Examples Sheet 5 - Finite Wing Theory Solutions]].

## Related
- Parent lectures: [[SESA2022 T5 - Finite Wing Theory]], [[SESA2022 T6 - Aircraft Aerodynamics and Static Stability]]
- Related concepts: [[Biot-Savart Law and Helmholtz Theorems]], [[Elliptic Lift Distribution]], [[Oswald Efficiency Factor]], [[Maximum Lift-to-Drag Ratio]]

## Sources
- `02 - Sources/Airfoils and Wings/Topic 5 Finite wing theory_v3_pdf.pdf`
