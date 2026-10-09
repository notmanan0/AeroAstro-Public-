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
sources: ["02 - Sources/Airfoils and Wings/Topic 5 Finite wing theory_v3_pdf.pdf"]
---

# Maximum Lift-to-Drag Ratio

## Definition

> [!note] Definition
> With the parabolic drag polar $C_D = C_{D_0}+\dfrac{C_L^2}{\pi eAR}$, $L/D$ is maximised when **induced drag equals zero-lift drag**:
> $$C_{D_i} = C_{D_0}\;\Rightarrow\;C_L^* = \sqrt{\pi eAR\,C_{D_0}},\qquad \left(\frac LD\right)_{max} = \frac12\sqrt{\frac{\pi eAR}{C_{D_0}}}$$

## Explanation
- **Derivation**: $\dfrac{d}{dC_L}\left(\dfrac{C_L}{C_{D_0}+kC_L^2}\right) = 0$ gives $C_{D_0} = kC_L^2$.
- $(L/D)_{max}$ gives:
  - the **best glide angle**, $\tan\gamma_{min} = 1/(L/D)_{max}$;
  - **maximum range for propeller aircraft**;
  - **maximum endurance for jets**.

  Jet range uses $C_L^{1/2}/C_D$. Minimum power (propeller endurance) uses $C_L^{3/2}/C_D$.
- **Raise it with** a high $AR$ (sailplanes, above 30) and a low $C_{D_0}$ (laminar-flow sections, clean design).
- **Design subtlety**: if speed and chord are fixed and **span** is the design variable, $D(b) = qbcC_{D_0}+\frac{W^2}{\pi qb^2}$ is minimised at $D_0 = 2D_i$, not $D_0 = D_i$ ([[SESA2022 Exam 2020-21 Solutions]] Part B Q5).
- $C_{D_0}$ = skin friction ($C_F$, from BL theory) + form/pressure drag + interference.

![[fwt_drag_polar.png|520]]

## Examples
- UAV span for maximum efficiency: [[SESA2022 Exam 2020-21 Solutions]] B Q5.
- $(C_L/C_D)_{max} = 12.52$: [[SESA2022 Exam 2023-24 Solutions]] B Q4.
- [[SESA2022 Static Stability Past Paper Questions Solutions]].

## Related
- Parent lectures: [[SESA2022 T5 - Finite Wing Theory]]
- Related concepts: [[Oswald Efficiency Factor]], [[Downwash and Induced Drag]]

## Sources
- `02 - Sources/Airfoils and Wings/Topic 5 Finite wing theory_v3_pdf.pdf`
