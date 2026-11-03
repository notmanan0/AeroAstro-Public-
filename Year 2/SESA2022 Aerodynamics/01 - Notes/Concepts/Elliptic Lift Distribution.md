---
title: "Elliptic Lift Distribution"
module: "SESA2022 Aerodynamics"
type: concept
stream: "Topic 5: Finite Wing Theory"
aliases: ["ELD", "elliptic loading", "elliptic wing", "washout"]
tags: [sesa2022, concept, finite-wing-theory]
status: complete
parent_lectures: ["[[SESA2022 T5 - Finite Wing Theory]]"]
related_concepts: ["[[Downwash and Induced Drag]]", "[[Oswald Efficiency Factor]]", "[[Glauert Integrals]]"]
sources: ["02 - Sources/Airfoils and Wings/Topic 5 Finite wing theory_v3_pdf.pdf", "02 - Sources/Lectures/SESA2022 Lecture 2025-11-06.txt … 2025-11-13.txt (2025-26 transcripts)"]
---

# Elliptic Lift Distribution

The elliptic lift distribution is a spanwise circulation $\Gamma(y) = \Gamma_0\sqrt{1-(2y/b)^2}$, the case where only $B_1\ne0$. It produces uniform downwash and the minimum induced drag for a given lift and span.

$$
w = -\frac{\Gamma_0}{2b},\qquad \alpha_i = \frac{C_L}{\pi AR},\qquad L = \frac\pi4\rho V_\infty b\Gamma_0,\qquad C_L = \frac{\pi b\Gamma_0}{2V_\infty S} = \pi AR\,B_1,\qquad C_{D_i} = \frac{C_L^2}{\pi AR}
$$

The mean circulation is $\bar\Gamma = \frac\pi4\Gamma_0$. There are four ways to get the distribution. An untwisted elliptic planform (the Spitfire) has $c(y)\propto\Gamma(y)$, so $C_l$ is constant along the span. A rectangular planform with geometric washout runs its root section at a higher $C_l$, $C_l(0) = \frac4\pi C_L$. Aerodynamic twist varies the camber along the span instead. And a taper ratio of about 0.35–0.45 comes within about 1 % of $e = 1$.

For the rectangular wing, the washout needed is

$$
\Delta\alpha_{twist} = \frac{C_l(0)}{2\pi} = \frac{2C_L}{\pi^2},
$$

which doesn't depend on the aspect ratio, because $\alpha_i$ is uniform along the span and cancels. The root angle is $\alpha(0) = C_l(0)/(2\pi)+\alpha_{L=0}+\alpha_i$ and the tip angle $\alpha_{L=0}+\alpha_i$. The elliptic planform has two drawbacks: it is hard to build, and its uniform $C_l$ means the whole span stalls at once, with no warning and poor aileron authority at the stall.

Past-paper uses: the constant-downwash derivation and root angle ([[SESA2022 Exam 2018-19 Solutions]] Q3); twist independent of aspect ratio ([[SESA2022 Exam 2019-20 Solutions]] Q3); UAV root and tip angles ([[SESA2022 Exam 2020-21 Solutions]] B Q7); the centre-section angle ([[SESA2022 Exam 2022-23 Solutions]], [[SESA2022 Exam 2023-24 Solutions]]); the circulation halfway along the semi-span ([[SESA2022 Exam 2017-18 Solutions]] Q3).

## Related

- Full derivation and worked examples: [[SESA2022 T5 - Finite Wing Theory#4. Elliptic lift distribution (ELD)|T5 §4]]
- [[Downwash and Induced Drag]] · [[Oswald Efficiency Factor]] · [[Glauert Integrals]]
