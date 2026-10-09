---
title: "Blasius and Falkner-Skan Similarity Solutions"
module: "SESA3043 Advanced Aeronautics"
type: concept
stream: "Chapter 3: Methods for Boundary Layers"
aliases: ["Blasius solution", "Blasius equation", "Falkner-Skan equation", "similarity solution", "wedge boundary layer"]
tags: [sesa3043, concept, boundary-layer]
status: complete
parent_lectures: ["[[SESA3043 3.2 - Blasius and Falkner-Skan Similarity Solutions]]"]
related_concepts: ["[[Shooting Method and the Blasius Solution]]", "[[Wedge and Corner Flows]]", "[[Displacement and Momentum Thickness]]", "[[Pohlhausen Method]]"]
sources: ["02 - Sources/Lectures/CH3-2 Blasius and Falkner-Skan(1).pdf", "02 - Sources/Lectures/Ch3_Notes_Blasius.pdf", "02 - Sources/Lectures/Ch3_Notes_Falkner-Skan.pdf"]
---

# Blasius and Falkner-Skan Similarity Solutions

## Statement

> [!note] Definition
> For $U_e=cx^m$ (flow past a wedge of angle $\beta\pi$), the variables $\xi=\sqrt{2\nu x/((m+1)U_e)}$, $\eta=y/\xi$, $\psi=U_e\xi f(\eta)$ reduce the BL equations to
>
> $$f'''+ff''+\beta(1-f'^2)=0,\qquad\beta=\frac{2m}{m+1},\qquad f(0)=f'(0)=0,\ f'(\infty)=1,$$
>
> with $u/U_e=f'(\eta)$. $\beta=0$ is **Blasius** (flat plate): $f'''+ff''=0$.

## Key results (course scaling)

| | Blasius ($\beta=0$) | stagnation ($\beta=1$) | separation ($\beta=-0.19884$) |
|---|---:|---:|---:|
| $f''(0)$ | 0.4696 | 1.2326 | 0 |
| $\eta^*=\int(1-f')$ | 1.217 | 0.648 | 2.359 |
| $\theta^*=\int f'(1-f')$ | 0.4696 | 0.292 | 0.585 |
| $H$ | 2.59 | 2.22 | 4.03 |

Flat plate: $\delta_{99}/x=4.91/\sqrt{Re_x}$, $\delta^*/x=1.721/\sqrt{Re_x}$, $\theta/x=C_f=0.664/\sqrt{Re_x}$. In general $\delta^*=\xi\eta^*$, $\theta=\xi\theta^*$, $C_f=2\nu f''(0)/(U_e\xi)$.

## Why it works

There is no length scale in a semi-infinite plate or a wedge, so the profiles at different $x$ are stretched copies of one another. The scaling $\xi\propto\sqrt{\nu x/U_e}$ is the diffusion length found by order of magnitude in 1.4; with it, $x$ cancels from the equations.

## Scaling warning

SESA2029 and 1.4 use $\eta_o=y\sqrt{U/\nu x}$ and $f_o'''+\frac12f_of_o''=0$, $f_o''(0)=0.332$. Same solution: $\eta_o=\sqrt2\eta$, $f_o=\sqrt2f$, so $f''(0)=\sqrt2\times0.332=0.4696$.

## Solving

Guess-and-shoot on $f''(0)$ until $f'(\infty)=1$. See [[Shooting Method and the Blasius Solution]].

## Related

- [[SESA3043 3.2 - Blasius and Falkner-Skan Similarity Solutions]] (full derivations, examples)
- [[Wedge and Corner Flows]] · [[Displacement and Momentum Thickness]] · [[Pohlhausen Method]] · [[Boundary Layer Separation]]
