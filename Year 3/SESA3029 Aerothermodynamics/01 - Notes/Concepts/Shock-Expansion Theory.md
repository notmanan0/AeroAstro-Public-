---
title: "Shock-Expansion Theory"
module: "SESA3029 Aerothermodynamics"
type: concept
stream: "Block 2: Oblique Shocks and Expansions"
aliases: ["shock-expansion method", "shock expansion theory", "supersonic flat plate", "diamond aerofoil"]
tags: [sesa3029, concept, shock-expansion, supersonic-aerofoil]
status: complete
parent_lectures: ["[[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method]]"]
related_concepts: ["[[Theta-Beta-Mach Relation]]", "[[Prandtl-Meyer Function]]", "[[Slip Line]]", "[[Aerodynamic Centre and Centre of Pressure]]"]
sources: ["02 - Sources/Lectures/Lecture2-5.pdf", "02 - Sources/Lectures/Lecture 2-5 (2025-26 version).txt", "02 - Sources/Lectures/Tutorial Lecture #1.txt"]
---

# Shock-Expansion Theory

## Definition

> [!note] Definition
> For 2D bodies made of flat faces in supersonic flow:
> - put an **oblique shock** at every compression corner;
> - put a **Prandtl–Meyer fan** at every expansion corner;
> - take each face's pressure as **uniform**;
> - integrate for $L$, $D$ and $M$.
>
> The method is exact for inviscid flow as long as no reflected wave returns to the surface.

## Explanation

**Flat plate** at $\alpha$:

$$
\Delta p=p_{lower}-p_{upper},
\qquad
C_l=\frac{\Delta p\cos\alpha}{q_\infty},
\qquad
C_d=\frac{\Delta p\sin\alpha}{q_\infty},
\qquad
C_{m,LE}=-\frac{\Delta p}{2q_\infty},
$$

with $q_\infty=\tfrac12\gamma p_\infty M_\infty^2$. The centre of pressure is at mid-chord and $L/D=\cot\alpha$.

| Case | $C_l$ | $C_d$ | $C_{m,LE}$ |
|---|---:|---:|---:|
| Lecture 2.5: $M=2$, $\alpha=10^\circ$ | 0.4075 | 0.0719 | $-0.2069$ |

**Why supersonic plates have drag** (L2-5, ll. 149–213): in subsonic flow, leading-edge suction cancels $N\sin\alpha$ (d'Alembert). In supersonic flow nothing wraps round the edge, so $N\sin\alpha$ survives as **wave drag**. The plate's ac (and cp) sits at **mid-chord**, not the subsonic quarter chord: a static-margin problem for aircraft that fly both regimes (ll. 243–257).

**Thick sections** (Tutorial 1, triangular wing): each face's force is normal to **that face**, so inclined faces also push along the chord. Then $D\neq N\sin\alpha$. On the triangular wing the shortcut misses a quarter of the drag. See [[SESA3029 Tutorial Lecture 1 - Shock Reflection and a Triangular Wing#Forces: the chordwise term the shortcut misses|Tutorial 1]]; there $x_{ac}\approx0.49c$.

**Diamond:** the face angles are $\pm\varepsilon\pm\alpha$. Thickness produces wave drag even at zero lift. See [[SESA3029 Example Sheet 1 - Solutions#Q6. Diamond aerofoil by shock-expansion theory|ES1 Q6]].

**Linear limit (Ackeret):** $C_p=2\theta/\sqrt{M^2-1}$, giving $C_l=4\alpha/\beta$ and $C_d=4(\alpha^2+\varepsilon^2)/\beta$. Ackeret is within 1–2% of the exact method at $10^\circ$ and essentially exact at $2^\circ$.

**Trailing edge:** the waves there set a [[Slip Line]] but do not change the surface pressures, because nothing travels upstream.

![[at_shock_expansion_plate.png|760]]

## Related

- [[Theta-Beta-Mach Relation]] · [[Prandtl-Meyer Function]] · [[Slip Line]] · [[Aerodynamic Centre and Centre of Pressure]]
- Detail: [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method#6. The shock-expansion method|W03 §6]]
