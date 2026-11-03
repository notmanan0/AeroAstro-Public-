---
title: "Oblique-Shock Jump Relations"
module: "SESA3029 Aerothermodynamics"
type: concept
stream: "Block 2: Oblique Shocks and Expansions"
aliases: ["oblique-shock relations", "normal-component method", "M_n1 = M1 sin beta"]
tags: [sesa3029, concept, oblique-shock]
status: complete
parent_lectures: ["[[SESA3029 W02 - Oblique Shock Relations and Mach Waves]]"]
related_concepts: ["[[Normal-Shock Jump Relations]]", "[[Theta-Beta-Mach Relation]]", "[[Oblique Shock Waves]]"]
sources: ["02 - Sources/Lectures/Lecture2-1.pdf", "02 - Sources/Lectures/Lecture 2-1.txt"]
---

# Oblique-Shock Jump Relations

Across an oblique shock inclined at $\beta$ to the upstream velocity, the tangential velocity passes through unchanged and the normal component obeys the normal-shock equations. So every static jump, and $p_{02}/p_{01}$, is the [[Normal-Shock Jump Relations|normal-shock relation]] evaluated at

$$M_{n1}=M_1\sin\beta.$$

Written out:

$$
\frac{\rho_2}{\rho_1}=\frac{(\gamma+1)M_{n1}^2}{2+(\gamma-1)M_{n1}^2}=\frac{\tan\beta}{\tan(\beta-\theta)},
\qquad
\frac{p_2}{p_1}=1+\frac{2\gamma}{\gamma+1}\left(M_{n1}^2-1\right),
$$

$$
\frac{T_2}{T_1}=\frac{p_2/p_1}{\rho_2/\rho_1},
\qquad
M_{n2}^2=\frac{2+(\gamma-1)M_{n1}^2}{2\gamma M_{n1}^2-(\gamma-1)},
\qquad
M_2=\frac{M_{n2}}{\sin(\beta-\theta)}.
$$

## Why the normal-shock results carry over

There is no pressure difference along the shock, so tangential momentum gives $\dot m(U_{t2}-U_{t1})=0$ and $U_t$ is the same on both sides. In the energy equation $h+\tfrac12(U_n^2+U_t^2)=\text{const}$, the $\tfrac12U_t^2$ term then appears on both sides and cancels. What is left (mass, normal momentum and energy) is the normal-shock set with $U$ replaced by $U_n$.

The stagnation-pressure ratio also carries over, which is less obvious because $p_0$ includes the tangential kinetic energy. But $p_{02}/p_{01}=e^{-\Delta s/R}$, and $\Delta s$ depends only on the static ratios, so the table's $p_{02}/p_{01}$ at $M_{n1}$ is correct. Full derivation: [[SESA3029 W02 - Oblique Shock Relations and Mach Waves#3. Conservation laws across the oblique shock|W02 §§3–4]].

## Pitfalls

The table's "$M_2$" column gives $M_{n2}$; you still have to divide by $\sin(\beta-\theta)$ to get $M_2$. The isentropic ratios $T_0/T$ and $p_0/p$ at a station use the full $M$ there, not $M_n$. And a shock only exists if $M_{n1}>1$, which means $\beta>\mu=\sin^{-1}(1/M_1)$.

## Example

$M_1=2$, $\theta=15^\circ$, weak solution $\beta=45.34^\circ$: $M_{n1}=1.423$, $p_2/p_1=2.19$, $\rho_2/\rho_1=1.73$, $M_{n2}=0.730$, $M_2=1.45$, $p_{02}/p_{01}=0.952$.

## Related

- [[Normal-Shock Jump Relations]] · [[Theta-Beta-Mach Relation]] · [[Weak and Strong Oblique Shocks]]
