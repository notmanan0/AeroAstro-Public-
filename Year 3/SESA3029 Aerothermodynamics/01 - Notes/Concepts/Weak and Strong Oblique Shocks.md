---
title: "Weak and Strong Oblique Shocks"
module: "SESA3029 Aerothermodynamics"
type: concept
stream: "Block 2: Oblique Shocks and Expansions"
aliases: ["weak shock solution", "strong shock solution", "maximum deflection angle", "shock detachment", "detached shock"]
tags: [sesa3029, concept, oblique-shock]
status: complete
parent_lectures: ["[[SESA3029 W02 - Oblique Shock Relations and Mach Waves]]"]
related_concepts: ["[[Theta-Beta-Mach Relation]]", "[[Oblique-Shock Jump Relations]]", "[[Compressible Pitot Probe]]"]
sources: ["02 - Sources/Lectures/Lecture2-1.pdf", "02 - Sources/Lectures/Lecture 2-1.txt"]
---

# Weak and Strong Oblique Shocks

## Definition

> [!note] Definition
> For a given $M_1$ and deflection $0<\theta<\theta_{max}(M_1)$, the [[Theta-Beta-Mach Relation]] has two solutions. The **weak** solution has the smaller $\beta$. The **strong** solution has the larger $\beta$, closer to a normal shock.

## Comparison

| | Weak | Strong |
|---|---|---|
| $\beta$ | nearer $\mu$ | nearer $90^\circ$ |
| $M_{n1}=M_1\sin\beta$ | smaller | larger |
| $p_2/p_1$, $T_2/T_1$, entropy rise | smaller | larger |
| $M_2$ | usually $>1$ (subsonic only just below $\theta_{max}$) | always $<1$ |
| occurrence | the normal outcome on wedges and corners | only if forced by back pressure or geometry |

At $M_1=2$, $\theta=15^\circ$: weak $\beta=45.3^\circ$, $M_2=1.45$, $p_{02}/p_{01}=0.952$; strong $\beta=79.8^\circ$, $M_2=0.64$, $p_{02}/p_{01}=0.736$.

![[at_oblique_shock_strength.png|760]]

## Maximum deflection and detachment

The two branches meet at $\theta_{max}$, where $\mathrm d\theta/\mathrm d\beta=0$. If the wall turns the flow by more than $\theta_{max}$, no attached oblique shock satisfies the conservation laws. A curved, **detached** bow shock forms ahead of the body. It is normal on the axis and weakens further out. A blunt body, including a Pitot probe, is the limiting case.

| $M_1$ | 1.5 | 2 | 3 | 5 | $\infty$ |
|---|---:|---:|---:|---:|---:|
| $\theta_{max}$ | 12.1° | 23.0° | 34.1° | 41.1° | 45.6° |

## Related

- [[Theta-Beta-Mach Relation]] · [[Oblique-Shock Jump Relations]] · [[Intake Pressure Recovery]]
- Detail: [[SESA3029 W02 - Oblique Shock Relations and Mach Waves#6. The oblique-shock chart|W02 §6]]
