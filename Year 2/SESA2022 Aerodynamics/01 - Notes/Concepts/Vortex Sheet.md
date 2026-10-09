---
title: "Vortex Sheet"
module: "SESA2022 Aerodynamics"
type: concept
stream: "Topic 4: Thin Aerofoil Theory"
aliases: ["vortex sheet strength", "gamma(x)"]
tags: [sesa2022, concept, thin-aerofoil-theory]
status: complete
parent_lectures: ["[[SESA2022 T4 - Thin Aerofoil Theory]]"]
related_concepts: ["[[Kutta Condition]]", "[[Glauert Integrals]]", "[[Kutta-Joukowski Theorem]]"]
sources: ["02 - Sources/Airfoils and Wings/Topic 4 Thin airfoil theory_v3.pdf"]
---

# Vortex Sheet

## Definition

> [!note] Definition
> A continuous distribution of infinitesimal vortices along a line, with strength $\gamma(s)$ per unit length. Across the sheet the **tangential velocity jumps** by $\gamma$ while the normal velocity is continuous:
>
> $$\gamma = u_{upper}-u_{lower},\qquad d\Gamma = \gamma\,ds,\qquad \Gamma = \int\gamma\,ds$$

## Explanation
- In TAT the aerofoil is replaced by a vortex sheet on its **chord line**. The requirement that the camber line be a streamline gives the fundamental equation:

$$
\frac{1}{2\pi}\int_0^c\frac{\gamma(\xi)\,d\xi}{x-\xi} = V_\infty\left(\alpha-\frac{dz}{dx}\right)
$$

- The solution is written as a Fourier series in $\theta$ (with $\xi = \frac c2(1-\cos\theta)$):

$$
\gamma(\theta) = 2V_\infty\left(A_0\frac{1+\cos\theta}{\sin\theta}+\sum_{n\ge1}A_n\sin n\theta\right)
$$

  The $A_0$ term is singular at the LE (the leading-edge suction peak) and zero at the TE ([[Kutta Condition]]).
- **Pressure jump**: $\Delta C_p = C_{p,l}-C_{p,u} = 2\gamma/V_\infty$. So the plot of $\gamma$ *is* the chordwise load distribution.
- **Lift**: $\Gamma = \int\gamma\,d\xi = \pi cV_\infty(A_0+A_1/2)$, which gives $c_l = \pi(2A_0+A_1)$ via [[Kutta-Joukowski Theorem]].

![[tat_loading.png|520]]

## Examples
- $\gamma(\theta)$ and $\Delta C_p$ for a parabolic camber line: [[SESA2022 Exam 2022-23 Solutions]] Part B Q1.
- Deriving $c_l$ from $\gamma$: [[SESA2022 Exam 2014-15 Solutions]] Q3 and [[SESA2022 Exam 2015-16 Solutions]] Q2.

## Related
- Parent lectures: [[SESA2022 T4 - Thin Aerofoil Theory]]
- Related concepts: [[Kutta Condition]], [[Glauert Integrals]], [[Kutta-Joukowski Theorem]]

## Sources
- `02 - Sources/Airfoils and Wings/Topic 4 Thin airfoil theory_v3.pdf`
