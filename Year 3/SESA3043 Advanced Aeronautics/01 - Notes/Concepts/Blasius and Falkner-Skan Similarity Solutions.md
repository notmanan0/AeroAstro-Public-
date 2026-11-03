---
title: "Blasius and Falkner-Skan Similarity Solutions"
module: "SESA3043 Advanced Aeronautics"
type: concept
stream: "Chapter 3: Methods for Boundary Layers"
aliases: ["Blasius solution", "Blasius equation", "Falkner-Skan equation", "similarity solution", "wedge boundary layer", "guess-and-shooting method", "shooting method", "similarity variables", "integral type A", "integral type B", "reduced BL equation", "Hartree parameter", "generalised laminar BLs"]
tags: [sesa3043, concept, boundary-layer]
status: complete
parent_lectures: ["[[SESA3043 3.2 - Blasius and Falkner-Skan Similarity Solutions]]"]
related_concepts: ["[[Shooting Method and the Blasius Solution]]", "[[Wedge and Corner Flows]]", "[[Displacement and Momentum Thickness]]", "[[Pohlhausen Method]]"]
sources: ["02 - Sources/Lectures/CH3-2 Blasius and Falkner-Skan(1).pdf", "02 - Sources/Lectures/Ch3_Notes_Blasius.pdf", "02 - Sources/Lectures/Ch3_Notes_Falkner-Skan.pdf", "02 - Sources/Lectures/23 October 2026 at 14_53_16.txt"]
---

# Blasius and Falkner-Skan Similarity Solutions

For an outer flow $U_e=cx^m$, which is flow past a wedge of included angle $\beta\pi$, the variables $\xi=\sqrt{2\nu x/((m+1)U_e)}$, $\eta=y/\xi$ and $\psi=U_e\xi f(\eta)$ reduce the boundary-layer equations to one ODE:

$$f'''+ff''+\beta(1-f'^2)=0,\qquad\beta=\frac{2m}{m+1},\qquad f(0)=f'(0)=0,\ f'(\infty)=1,$$

with $u/U_e=f'(\eta)$. The flat plate is $\beta=0$, the **Blasius** equation $f'''+ff''=0$.

It works because neither a semi-infinite plate nor a wedge has a length scale, so the velocity profiles at different $x$ are stretched copies of each other. The stretching length $\xi\propto\sqrt{\nu x/U_e}$ is the diffusion length found by order of magnitude in 1.4, and with it $x$ drops out of the equations. The equation is solved by shooting: adjust $f''(0)$ until $f'(\infty)=1$ ([[Shooting Method and the Blasius Solution]]).

## Results in the course scaling

| | Blasius ($\beta=0$) | stagnation ($\beta=1$) | separation ($\beta=-0.19884$) |
|---|---:|---:|---:|
| $f''(0)$ | 0.4696 | 1.2326 | 0 |
| $\eta^*=\int(1-f')$ | 1.217 | 0.648 | 2.359 |
| $\theta^*=\int f'(1-f')$ | 0.4696 | 0.292 | 0.585 |
| $H$ | 2.59 | 2.22 | 4.03 |

On a flat plate, $\delta_{99}/x=4.91/\sqrt{Re_x}$, $\delta^*/x=1.721/\sqrt{Re_x}$ and $\theta/x=C_f=0.664/\sqrt{Re_x}$. In general $\delta^*=\xi\eta^*$, $\theta=\xi\theta^*$ and $C_f=2\nu f''(0)/(U_e\xi)$.

SESA2029 and 1.4 use a different scaling, $\eta_o=y\sqrt{U/\nu x}$ with $f_o'''+\frac12f_of_o''=0$ and $f_o''(0)=0.332$. It is the same solution: $\eta_o=\sqrt2\eta$ and $f_o=\sqrt2f$, so $f''(0)=\sqrt2\times0.332=0.4696$. Check which scaling a question uses before quoting numbers.

## What β means

$\beta$ labels the pressure gradient. Positive $\beta$ is an accelerating (favourable) outer flow with a fuller profile; negative $\beta$ is decelerating (adverse) with an emptier one. At $\beta=-0.19884$ ($m=-0.0904$) the wall shear vanishes and the layer separates. Since $\beta\pi$ is the included angle of a symmetric wedge, a single wall turned away by $\delta_w$ has $\beta=-2\delta_w/\pi$, so separation needs only $17.9^\circ$ of turn.

Over a bump, $\beta$ runs positive on the front, through zero at the crest, then negative towards separation. That is a local-similarity picture rather than an exact solution (lectured 23 Oct; [[SESA3043 3.2 - Blasius and Falkner-Skan Similarity Solutions#What β means physically: a boundary layer over a bump (slide 97)|3.2]]).

## Related

- [[SESA3043 3.2 - Blasius and Falkner-Skan Similarity Solutions]] (full derivations, examples)
- [[Wedge and Corner Flows]] · [[Displacement and Momentum Thickness]] · [[Pohlhausen Method]] · [[Boundary Layer Separation]]
