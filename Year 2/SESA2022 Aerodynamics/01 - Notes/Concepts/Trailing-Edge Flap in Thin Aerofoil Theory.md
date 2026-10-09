---
title: "Trailing-Edge Flap in Thin Aerofoil Theory"
module: "SESA2022 Aerodynamics"
type: concept
stream: "Topic 4: Thin Aerofoil Theory"
aliases: ["flap", "plain flap", "elevator effectiveness", "hinged flap TAT"]
tags: [sesa2022, concept, thin-aerofoil-theory, control-surfaces]
status: complete
parent_lectures: ["[[SESA2022 T4 - Thin Aerofoil Theory]]", "[[SESA2022 T6 - Aircraft Aerodynamics and Static Stability]]"]
related_concepts: ["[[Glauert Integrals]]", "[[Aerodynamic Centre and Centre of Pressure]]", "[[Stick-Fixed vs Stick-Free Stability]]"]
sources: ["02 - Sources/Airfoils and Wings/Topic 4 Thin airfoil theory_v3.pdf"]
---

# Trailing-Edge Flap in Thin Aerofoil Theory

## Definition

> [!note] Definition
> A plain flap of chord fraction $E$ deflected **down** by $\delta$ is modelled as a camber line with slope $0$ ahead of the hinge and $-\delta$ on the flap. The hinge is at $x_h = (1-E)c$, i.e. $\cos\theta_h = 1-2x_h/c$.

## Explanation
**Coefficients**:

$$
A_0 = \alpha+\frac\delta\pi(\pi-\theta_h),\qquad A_n = \frac{2\delta}{n\pi}\sin n\theta_h
$$

**Results**:

$$
C_l = 2\pi\alpha+2\left[(\pi-\theta_h)+\sin\theta_h\right]\delta,\qquad C_{m,c/4} = \frac\pi4(A_2-A_1) = -\frac{\delta}{2}\sin\theta_h(1-\cos\theta_h)
$$

**Flap effectiveness**: $\dfrac{\partial C_l}{\partial\delta} = 2(\pi-\theta_h+\sin\theta_h)$, which equals $a_2$ in the stability notation.

| Flap chord | $\theta_h$ | $\partial C_l/\partial\delta$ | $\partial C_{m,c/4}/\partial\delta$ | $\alpha_{L=0}/\delta$ |
|---|---|---|---|---|
| 20 % | 126.9° | 3.455 | −0.640 | −0.550 |
| 25 % | 120° | 3.826 | −0.650 | −0.609 |
| 30 % | 113.6° | 4.152 | −0.642 | −0.661 |

(Values checked numerically. $|\partial C_{m,c/4}/\partial\delta|$ peaks near a 25 % flap.)

- A down-flap **raises $C_l$ at every $\alpha$** (shifting $\alpha_{L=0}$ negative) and gives a **nose-down** $C_{m,c/4}$. The lift slope stays $2\pi$.
- TAT over-predicts flap effectiveness by about 20–40 %, because of viscous losses and the gap at the hinge.
- The same model gives elevator and rudder derivatives, and hinge moments, for stability work.

## Examples
- 25 % flap: [[SESA2022 Exam 2013-14 Solutions]] Q3, [[SESA2022 Exam 2018-19 Solutions]] Q2 and [[SESA2022 Exam 2023-24 Solutions]] B Q1.
- [[SESA2022 Examples Sheet 4 - Thin Aerofoil Theory Solutions]].

## Related
- Parent lectures: [[SESA2022 T4 - Thin Aerofoil Theory]], [[SESA2022 T6 - Aircraft Aerodynamics and Static Stability]]
- Related concepts: [[Glauert Integrals]], [[Aerodynamic Centre and Centre of Pressure]], [[Stick-Fixed vs Stick-Free Stability]]

## Sources
- `02 - Sources/Airfoils and Wings/Topic 4 Thin airfoil theory_v3.pdf`
