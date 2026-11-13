---
title: "Wing Planform Geometry"
module: "SESA1015 Intro to Aero & Astro"
type: concept
stream: "Mechanics of Flight"
aliases: ["Mean aerodynamic chord", "MAC", "Standard mean chord", "SMC", "Aspect ratio", "Taper ratio", "Gross wing area", "Net wing area", "Wetted area"]
tags: [sesa1015, concept, aircraft-geometry, wing]
status: complete
parent_lectures: ["[[SESA1015 M02 - Aircraft Geometry, Forces and Coefficients]]"]
related_concepts: ["[[Dynamic Pressure and Aerodynamic Coefficients]]", "[[Aerofoil Geometry and NACA Four-Digit Sections]]", "[[Wing Loading]]"]
sources: ["02 - Sources/Mechanics of Flight/Mechanics of Flight - Course Notes.pdf (§2.5–2.6, pp. 9–10)", "02 - Sources/Mechanics of Flight/Mechanics of Flight - Lecture Slides version 2.pdf (pp. 38–43)"]
---

# Wing Planform Geometry

The planform of a wing is its shape seen from above, described by the span $b=2s$, the chord distribution $c(y)$ and the derived quantities: gross area $S=\int_{-s}^{s}c\,dy$, aspect ratio $AR=b^2/S$, taper ratio $\lambda=c_T/c_0$, sweep $\Lambda$, standard mean chord $\bar c=S/b$ and mean aerodynamic chord $\bar{\bar c}=\int c^2dy\big/\int c\,dy$.

The reference area is the gross wing area $S_G$, the projected planform with the leading and trailing edges carried in to the centreline through the fuselage. The net area $S_N$ counts only the exposed wings, and the wetted area $S_W>2S_N$ is the real upper-plus-lower surface area on which skin friction acts.

The two mean chords serve different purposes. The standard mean chord is the chord of the rectangular wing with the same span and area and describes the geometry; with it $AR=b/\bar c$. The mean aerodynamic chord weights each strip by its chord because a strip's pitching moment scales with $c^2$; it is the reference length for $C_M$ and for locating the CG and the aerodynamic centre. It is never smaller than the SMC, and equals it only for a rectangular wing. Its spanwise station is the half-wing area centroid, $\bar y=\int_0^s cy\,dy\big/\int_0^s c\,dy$.

| Planform | $S$ | $\bar c$ | $\bar{\bar c}$ | $\bar y$ | $AR$ |
|---|---|---|---|---|---|
| rectangular, chord $c$ | $bc$ | $c$ | $c$ | $s/2$ | $b/c$ |
| straight taper, root $c_0$ | $\tfrac12c_0b(1+\lambda)$ | $\tfrac12c_0(1+\lambda)$ | $\tfrac23c_0\dfrac{1+\lambda+\lambda^2}{1+\lambda}$ | $\dfrac b6\dfrac{1+2\lambda}{1+\lambda}$ | $\dfrac{2b}{c_0(1+\lambda)}$ |
| elliptic, root $c_0$ | $\tfrac14\pi c_0b$ | $\tfrac14\pi c_0$ | $\dfrac{8c_0}{3\pi}$ | $\dfrac{4s}{3\pi}$ | $\dfrac{4b}{\pi c_0}$ |

Sweep differs from one chord line to another on a tapered wing: the line a fraction $n$ of the chord behind the leading edge has $\tan\Lambda_n=\tan\Lambda_{LE}-n\,c_0(1-\lambda)/s$, so the quarter-chord line is less swept than the leading edge. Twist along the span is washout (tip nose-down) or washin (tip nose-up).

![[mof_m02_planform.png|900]]

Worked examples: the elliptic wing with $c_0=0.25$ m and $b=1.1$ m has $S=0.216$ m², $AR=5.60$ and $\bar{\bar c}=0.212$ m; the straight-tapered wing with $b=11$ m, $c_0=2$ m, $\lambda=0.5$ has $S=16.5$ m², $AR=7.33$, $\bar{\bar c}=1.556$ m at $\bar y=2.444$ m.

The common trap is to mix span and semi-span: $S=2\int_0^s c\,dy$, and $AR=b^2/S=4s^2/S$.

## Related

- Topics: [[SESA1015 M02 - Aircraft Geometry, Forces and Coefficients]] (derivations of the table, worked examples)
- Concepts: [[Dynamic Pressure and Aerodynamic Coefficients]] · [[Aerofoil Geometry and NACA Four-Digit Sections]] · [[Wing Loading]] · [[Static Margin and Tail Volume]]
- Later: [[SESA2022 T5 - Finite Wing Theory]] (aspect ratio and induced drag)
