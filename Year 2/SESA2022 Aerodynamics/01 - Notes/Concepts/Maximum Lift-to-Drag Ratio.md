---
title: "Maximum Lift-to-Drag Ratio"
module: "SESA2022 Aerodynamics"
type: concept
stream: "Topic 5: Finite Wing Theory"
aliases: ["(L/D)max", "L/D max", "best glide", "drag polar"]
tags: [sesa2022, concept, finite-wing-theory, performance]
status: complete
parent_lectures: ["[[SESA2022 T5 - Finite Wing Theory]]"]
related_concepts: ["[[Oswald Efficiency Factor]]", "[[Downwash and Induced Drag]]"]
sources: ["02 - Sources/Airfoils and Wings/Topic 5 Finite wing theory_v3_pdf.pdf", "02 - Sources/Lectures/SESA2022 Lecture 2025-11-06.txt … 2025-11-13.txt (2025-26 transcripts)"]
---

# Maximum Lift-to-Drag Ratio

With the parabolic drag polar $C_D = C_{D_0}+C_L^2/(\pi eAR)$, the lift-to-drag ratio is greatest when the induced drag equals the zero-lift drag:

$$
C_{D_i} = C_{D_0}\;\Rightarrow\;C_L^* = \sqrt{\pi eAR\,C_{D_0}},\qquad \left(\frac LD\right)_{max} = \frac12\sqrt{\frac{\pi eAR}{C_{D_0}}} .
$$

The condition comes from setting $\dfrac{d}{dC_L}\left(\dfrac{C_L}{C_{D_0}+kC_L^2}\right) = 0$, which gives $C_{D_0} = kC_L^2$. $(L/D)_{max}$ sets the best glide angle, $\tan\gamma_{min} = 1/(L/D)_{max}$, the maximum range of a propeller aircraft and the maximum endurance of a jet. Other flight conditions use other ratios: jet range uses $C_L^{1/2}/C_D$ and minimum power (propeller endurance) uses $C_L^{3/2}/C_D$. A high aspect ratio (sailplanes go above 30) and a low $C_{D_0}$ (laminar-flow sections, a clean design) both raise it, where $C_{D_0}$ is skin friction ($C_F$, from boundary-layer theory) plus form drag plus interference drag.

The optimum shifts if the design variable changes. If speed and chord are fixed and the span is chosen, the drag $D(b) = qbcC_{D_0}+W^2/(\pi qb^2)$ is smallest at $D_0 = 2D_i$, not $D_0 = D_i$ ([[SESA2022 Exam 2020-21 Solutions]] Part B Q5, which sizes a UAV span this way).

![[fwt_drag_polar.png|520]]

Other past-paper uses: $(C_L/C_D)_{max} = 12.52$ ([[SESA2022 Exam 2023-24 Solutions]] B Q4) and [[SESA2022 Static Stability Past Paper Questions Solutions]].

## Related

- Full derivation and worked examples: [[SESA2022 T5 - Finite Wing Theory#Maximum lift-to-drag ratio|T5 §6]]
- [[Oswald Efficiency Factor]] · [[Downwash and Induced Drag]]
