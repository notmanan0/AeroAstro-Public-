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

## Definition

> [!note] Definition
> Across an oblique shock at angle $\beta$ to the upstream velocity, the tangential velocity is unchanged ($U_{t1}=U_{t2}$). The normal component obeys exactly the normal-shock equations. All static jumps, and $p_{02}/p_{01}$, are therefore the [[Normal-Shock Jump Relations]] evaluated at
>
> $$M_{n1}=M_1\sin\beta.$$

## Relations

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

## Why it works

- **Tangential momentum:** there is no pressure difference along the shock, so $\dot m(U_{t2}-U_{t1})=0$.
- **Energy:** $\tfrac12U_t^2$ appears on both sides of $h+\tfrac12(U_n^2+U_t^2)=\text{const}$ and cancels.
- The remaining mass, normal-momentum and energy equations are the normal-shock set with $U\to U_n$.
- $p_{02}/p_{01}=e^{-\Delta s/R}$, and $\Delta s$ depends only on the static ratios. So the table's $p_{02}/p_{01}$ at $M_{n1}$ is correct.

Full derivation: [[SESA3029 W02 - Oblique Shock Relations and Mach Waves#3. Conservation laws across the oblique shock|W02 §§3–4]].

## Pitfalls

- The table's "$M_2$" is $M_{n2}$. Always divide by $\sin(\beta-\theta)$.
- $T_0/T$ and $p_0/p$ at a station use the **full** $M$, not $M_n$.
- A shock needs $M_{n1}>1$, i.e. $\beta>\mu=\sin^{-1}(1/M_1)$.

## Example

$M_1=2$, $\theta=15^\circ$, weak $\beta=45.34^\circ$: $M_{n1}=1.423$, $p_2/p_1=2.19$, $\rho_2/\rho_1=1.73$, $M_{n2}=0.730$, $M_2=1.45$, $p_{02}/p_{01}=0.952$.

## Related

- [[Normal-Shock Jump Relations]] · [[Theta-Beta-Mach Relation]] · [[Weak and Strong Oblique Shocks]]
