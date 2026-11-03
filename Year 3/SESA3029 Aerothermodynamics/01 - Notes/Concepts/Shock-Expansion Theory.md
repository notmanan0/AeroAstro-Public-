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

Shock-expansion theory gives the forces on a two-dimensional body made of flat faces in supersonic flow. Put an oblique shock at every compression corner and a Prandtl–Meyer fan at every expansion corner, treat the pressure on each face as uniform, and integrate to get $L$, $D$ and $M$. For inviscid flow it is exact, as long as no reflected wave comes back to hit the surface.

## Flat plate

For a flat plate at incidence $\alpha$,

$$
\Delta p=p_{lower}-p_{upper},
\qquad
C_l=\frac{\Delta p\cos\alpha}{q_\infty},
\qquad
C_d=\frac{\Delta p\sin\alpha}{q_\infty},
\qquad
C_{m,LE}=-\frac{\Delta p}{2q_\infty},
$$

with $q_\infty=\tfrac12\gamma p_\infty M_\infty^2$. The centre of pressure is at mid-chord and $L/D=\cot\alpha$. The Lecture 2.5 case, $M=2$ and $\alpha=10^\circ$, gives $C_l=0.4075$, $C_d=0.0719$ and $C_{m,LE}=-0.2069$.

The plate has drag even without viscosity (L2-5, ll. 149–213). In subsonic flow, suction at the leading edge cancels the $N\sin\alpha$ component of the normal force, which is d'Alembert's paradox. In supersonic flow nothing can wrap round the edge, so $N\sin\alpha$ survives as wave drag. The aerodynamic centre also moves, from the subsonic quarter chord to mid-chord, which is a static-margin headache for aircraft that fly in both regimes (ll. 243–257).

![[at_shock_expansion_plate.png|760]]

## Thick sections

On a section with thickness, each face's pressure force is normal to that face, so the inclined faces also push along the chord and $D\neq N\sin\alpha$. On the triangular wing in Tutorial 1 the shortcut misses a quarter of the drag, and $x_{ac}\approx0.49c$ ([[SESA3029 Tutorial Lecture 1 - Shock Reflection and a Triangular Wing#Forces: the chordwise term the shortcut misses|Tutorial 1]]). On a diamond aerofoil the face angles are $\pm\varepsilon\pm\alpha$, and the thickness produces wave drag even at zero lift ([[SESA3029 Example Sheet 1 - Solutions#Q6. Diamond aerofoil by shock-expansion theory|ES1 Q6]]).

The waves at the trailing edge set up a [[Slip Line]] downstream but do not change the surface pressures, because nothing travels upstream in supersonic flow.

## Linear limit

For small angles the method reduces to Ackeret theory, $C_p=2\theta/\sqrt{M^2-1}$, which gives $C_l=4\alpha/\beta$ and $C_d=4(\alpha^2+\varepsilon^2)/\beta$. Ackeret is within 1–2% of the exact method at $10^\circ$ and essentially exact at $2^\circ$.

## Related

- [[Theta-Beta-Mach Relation]] · [[Prandtl-Meyer Function]] · [[Slip Line]] · [[Aerodynamic Centre and Centre of Pressure]]
- Detail: [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method#6. The shock-expansion method|W03 §6]]
