---
title: "Glauert Integrals"
module: "SESA2022 Aerodynamics"
type: concept
stream: "Topic 4: Thin Aerofoil Theory"
aliases: ["Glauert integral", "standard integrals TAT", "theta transformation"]
tags: [sesa2022, concept, thin-aerofoil-theory, maths]
status: complete
parent_lectures: ["[[SESA2022 T4 - Thin Aerofoil Theory]]", "[[SESA2022 T5 - Finite Wing Theory]]"]
related_concepts: ["[[Vortex Sheet]]", "[[Elliptic Lift Distribution]]"]
sources: ["02 - Sources/Airfoils and Wings/Topic 4 Thin airfoil theory_v3.pdf", "02 - Sources/Lectures/SESA2022 Lecture 2025-10-28.txt … 2025-11-05.txt (2025-26 transcripts)"]
---

# Glauert Integrals

The Glauert integrals are the principal-value integrals that make thin-aerofoil and lifting-line theory solvable in closed form:

$$
\int_0^\pi\frac{\cos n\theta\,d\theta}{\cos\theta-\cos\theta_0} = \pi\frac{\sin n\theta_0}{\sin\theta_0},\qquad \int_0^\pi\frac{\sin n\theta\sin\theta\,d\theta}{\cos\theta-\cos\theta_0} = -\pi\cos n\theta_0 ,
$$

used together with the orthogonality relations $\int_0^\pi\sin m\theta\sin n\theta\,d\theta = \frac\pi2\delta_{mn}$ and $\int_0^\pi\cos m\theta\cos n\theta\,d\theta = \frac\pi2\delta_{mn}$ ($\pi$ if $m = n = 0$).

They work because of a change of variable. The substitution $x = \frac c2(1-\cos\theta_0)$ along the chord, or $y = -\frac b2\cos\theta$ along the span, maps the leading and trailing edges (or the two tips) to $\theta = 0$ and $\pi$, and turns the $1/(x-\xi)$ kernels into $1/(\cos\theta-\cos\theta_0)$.

For a camber line, write $dz/dx$ in terms of $\theta_0$ using $x/c = \frac12(1-\cos\theta_0)$, so that $1-2x/c = \cos\theta_0$. If $dz/dx$ is piecewise, as for flaps and NACA 4-digit or modified NACA lines, split every integral at the break angle $\theta_p = \cos^{-1}(1-2p)$. Then

$$
A_0 = \alpha-\frac1\pi\int_0^\pi\frac{dz}{dx}d\theta_0,\qquad A_n = \frac2\pi\int_0^\pi\frac{dz}{dx}\cos n\theta_0\,d\theta_0,\qquad \alpha_{L=0} = -\frac1\pi\int_0^\pi\frac{dz}{dx}(\cos\theta_0-1)\,d\theta_0 .
$$

Two results are worth remembering. Parabolic camber $z = \epsilon x(1-x/c)$ gives $A_1 = \epsilon$, $A_{n\ge2} = 0$ and $\alpha_{L=0} = -\epsilon/2$, and a flap hinged at $\theta_h$ gives $A_n = \frac{2\delta}{n\pi}\sin n\theta_h$.

Past-paper uses: a modified NACA line split at $\pi/3$ ([[SESA2022 Exam 2021-22 Solutions]] B Q1); a NACA 4-digit line split at $\theta_p$ ([[SESA2022 Exam 2020-21 Solutions]] B Q1); constant downwash for the elliptic distribution ([[SESA2022 Exam 2018-19 Solutions]] Q3(i)).

## Related

- Full derivation and worked examples: [[SESA2022 T4 - Thin Aerofoil Theory#Glauert integrals|T4 §3]]
- [[Vortex Sheet]] · [[Trailing-Edge Flap in Thin Aerofoil Theory]] · [[Elliptic Lift Distribution]]
