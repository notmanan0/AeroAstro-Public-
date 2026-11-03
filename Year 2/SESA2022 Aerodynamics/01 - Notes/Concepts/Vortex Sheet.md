---
title: "Vortex Sheet"
module: "SESA2022 Aerodynamics"
type: concept
stream: "Topic 4: Thin Aerofoil Theory"
aliases: ["vortex sheet strength", "gamma(x)", "delta Cp"]
tags: [sesa2022, concept, thin-aerofoil-theory]
status: complete
parent_lectures: ["[[SESA2022 T4 - Thin Aerofoil Theory]]"]
related_concepts: ["[[Kutta Condition]]", "[[Glauert Integrals]]", "[[Kutta-Joukowski Theorem]]"]
sources: ["02 - Sources/Airfoils and Wings/Topic 4 Thin airfoil theory_v3.pdf", "02 - Sources/Lectures/SESA2022 Lecture 2025-10-28.txt … 2025-11-05.txt (2025-26 transcripts)"]
---

# Vortex Sheet

A vortex sheet is a continuous line of infinitesimal vortices with strength $\gamma(s)$ per unit length. Across it the tangential velocity jumps by $\gamma$ while the normal velocity is continuous:

$$
\gamma = u_{upper}-u_{lower},\qquad d\Gamma = \gamma\,ds,\qquad \Gamma = \int\gamma\,ds .
$$

Thin aerofoil theory replaces the aerofoil with a vortex sheet on its chord line. Requiring the camber line to be a streamline gives the fundamental equation

$$
\frac{1}{2\pi}\int_0^c\frac{\gamma(\xi)\,d\xi}{x-\xi} = V_\infty\left(\alpha-\frac{dz}{dx}\right),
$$

whose solution is written as a Fourier series in $\theta$, with $\xi = \frac c2(1-\cos\theta)$:

$$
\gamma(\theta) = 2V_\infty\left(A_0\frac{1+\cos\theta}{\sin\theta}+\sum_{n\ge1}A_n\sin n\theta\right) .
$$

The $A_0$ term is singular at the leading edge, which is the leading-edge suction peak, and zero at the trailing edge, as the [[Kutta Condition]] requires. The pressure jump across the sheet is $\Delta C_p = C_{p,l}-C_{p,u} = 2\gamma/V_\infty$, so a plot of $\gamma$ is the chordwise load distribution. Integrating gives $\Gamma = \pi cV_\infty(A_0+A_1/2)$, and the [[Kutta-Joukowski Theorem]] then gives $c_l = \pi(2A_0+A_1)$.

![[tat_loading.png|520]]

Past-paper uses: $\gamma(\theta)$ and $\Delta C_p$ for a parabolic camber line ([[SESA2022 Exam 2022-23 Solutions]] Part B Q1); deriving $c_l$ from $\gamma$ ([[SESA2022 Exam 2014-15 Solutions]] Q3, [[SESA2022 Exam 2015-16 Solutions]] Q2).

## Related

- Full derivation and worked examples: [[SESA2022 T4 - Thin Aerofoil Theory#Vortex sheet and loading|T4 §2]]
- [[Kutta Condition]] · [[Glauert Integrals]] · [[Kutta-Joukowski Theorem]]
