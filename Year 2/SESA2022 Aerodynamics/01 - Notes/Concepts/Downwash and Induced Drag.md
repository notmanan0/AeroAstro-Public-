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
sources: ["02 - Sources/Airfoils and Wings/Topic 5 Finite wing theory_v3_pdf.pdf", "02 - Sources/Lectures/SESA2022 Lecture 2025-11-06.txt … 2025-11-13.txt (2025-26 transcripts)"]
---

# Downwash and Induced Drag

The trailing vortices of a finite wing induce a downward velocity $w$ at the wing, which tilts the local relative wind down by the **induced angle** $\alpha_i = -w/V_\infty$. Each section's lift is perpendicular to that local wind, so it has a rearward component, the **induced drag**:

$$
\alpha_{eff} = \alpha-\alpha_i,\qquad D_i' = L'\alpha_i,\qquad C_{D_i} = \frac{C_L^2}{\pi AR}(1+\delta) = \frac{C_L^2}{\pi eAR}.
$$

Induced drag is the price of producing lift with a finite span. Its energy goes into the kinetic energy of the trailing-vortex wake, and viscosity plays no part. With the circulation written as a Fourier series,

$$
\alpha_i(\theta) = \sum nB_n\frac{\sin n\theta}{\sin\theta},\qquad C_{D_i} = \pi AR\sum nB_n^2 .
$$

Because $C_{D_i}\propto C_L^2$, induced drag dominates at low speed and high $C_L$ (take-off, climb, loiter), while profile drag dominates at high speed. For a fixed lift, $D_i = L^2/(\pi qb^2e)$, which depends on the span rather than the area, so it is the span loading $L/b$ that matters. Induced drag is reduced by a larger span or aspect ratio, near-elliptic loading, winglets, and formation flight in another aircraft's upwash. The same downwash reaches the tailplane as $\epsilon = C_L/(\pi Ae)$, and its slope $\partial\epsilon/\partial\alpha$ reduces the tail's effective incidence ([[Neutral Point and Static Margin]]).

![[fwt_circulation.png|520]]

Past-paper uses: the power needed to overcome induced drag ([[SESA2022 Exam 2017-18 Solutions]] Q3, [[SESA2022 Exam 2021-22 Solutions]] B Q2, [[SESA2022 Exam 2024-25 Solutions]] Q4); the ratio of induced to total drag ([[SESA2022 Exam 2022-23 Solutions]] B Q2); and [[SESA2022 Examples Sheet 5 - Finite Wing Theory Solutions]].

## Related

- Full derivation and worked examples: [[SESA2022 T5 - Finite Wing Theory#2. Downwash, induced angle and induced drag (7 Nov lecture)|T5 §2]]
- [[Biot-Savart Law and Helmholtz Theorems]] · [[Elliptic Lift Distribution]] · [[Oswald Efficiency Factor]] · [[Maximum Lift-to-Drag Ratio]]
