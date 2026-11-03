---
title: "Trailing-Edge Flap in Thin Aerofoil Theory"
module: "SESA2022 Aerodynamics"
type: concept
stream: "Topic 4: Thin Aerofoil Theory"
aliases: ["flap", "plain flap", "elevator effectiveness", "hinged flap TAT", "flap effectiveness"]
tags: [sesa2022, concept, thin-aerofoil-theory, control-surfaces]
status: complete
parent_lectures: ["[[SESA2022 T4 - Thin Aerofoil Theory]]", "[[SESA2022 T6 - Aircraft Aerodynamics and Static Stability]]"]
related_concepts: ["[[Glauert Integrals]]", "[[Aerodynamic Centre and Centre of Pressure]]", "[[Stick-Fixed vs Stick-Free Stability]]"]
sources: ["02 - Sources/Airfoils and Wings/Topic 4 Thin airfoil theory_v3.pdf", "02 - Sources/Lectures/SESA2022 Lecture 2025-10-28.txt … 2025-11-05.txt (2025-26 transcripts)"]
---

# Trailing-Edge Flap in Thin Aerofoil Theory

Thin aerofoil theory models a plain flap of chord fraction $E$, deflected down by $\delta$, as a camber line with zero slope ahead of the hinge and slope $-\delta$ on the flap. The hinge is at $x_h = (1-E)c$, so $\cos\theta_h = 1-2x_h/c$.

The Fourier coefficients are

$$
A_0 = \alpha+\frac\delta\pi(\pi-\theta_h),\qquad A_n = \frac{2\delta}{n\pi}\sin n\theta_h ,
$$

which give

$$
C_l = 2\pi\alpha+2\left[(\pi-\theta_h)+\sin\theta_h\right]\delta,\qquad C_{m,c/4} = \frac\pi4(A_2-A_1) = -\frac{\delta}{2}\sin\theta_h(1-\cos\theta_h) .
$$

The flap effectiveness $\partial C_l/\partial\delta = 2(\pi-\theta_h+\sin\theta_h)$ is the $a_2$ of the stability notation.

| Flap chord | $\theta_h$ | $\partial C_l/\partial\delta$ | $\partial C_{m,c/4}/\partial\delta$ | $\alpha_{L=0}/\delta$ |
|---|---|---|---|---|
| 20 % | 126.9° | 3.455 | −0.640 | −0.550 |
| 25 % | 120° | 3.826 | −0.650 | −0.609 |
| 30 % | 113.6° | 4.152 | −0.642 | −0.661 |

The values were checked numerically, and $|\partial C_{m,c/4}/\partial\delta|$ peaks near a 25 % flap. A down-going flap raises $C_l$ at every $\alpha$, shifting $\alpha_{L=0}$ negative, and gives a nose-down $C_{m,c/4}$, while the lift slope stays $2\pi$. Thin aerofoil theory over-predicts flap effectiveness by about 20–40 %, because of viscous losses and the gap at the hinge. The same model gives the elevator and rudder derivatives and hinge moments used in stability work.

Past-paper uses: a 25 % flap in [[SESA2022 Exam 2013-14 Solutions]] Q3, [[SESA2022 Exam 2018-19 Solutions]] Q2 and [[SESA2022 Exam 2023-24 Solutions]] B Q1; also [[SESA2022 Examples Sheet 4 - Thin Aerofoil Theory Solutions]].

## Related

- Full derivation and worked examples: [[SESA2022 T4 - Thin Aerofoil Theory#7. Trailing-edge flaps (31 Oct lecture)|T4 §7]]
- [[Glauert Integrals]] · [[Aerodynamic Centre and Centre of Pressure]] · [[Stick-Fixed vs Stick-Free Stability]]
