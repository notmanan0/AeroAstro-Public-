---
title: "Aerofoil Geometry and NACA Four-Digit Sections"
module: "SESA1015 Intro to Aero & Astro"
type: concept
stream: "Mechanics of Flight"
aliases: ["Aerofoil geometry", "Airfoil nomenclature", "NACA 4-digit", "NACA four-digit aerofoil", "Camber line", "Thickness-to-chord ratio"]
tags: [sesa1015, concept, aerofoil, aircraft-geometry]
status: complete
parent_lectures: ["[[SESA1015 M02 - Aircraft Geometry, Forces and Coefficients]]"]
related_concepts: ["[[Wing Planform Geometry]]", "[[Dynamic Pressure and Aerodynamic Coefficients]]"]
sources: ["02 - Sources/Mechanics of Flight/Mechanics of Flight - Course Notes.pdf (§2.7, p. 10)", "02 - Sources/Mechanics of Flight/Mechanics of Flight - Lecture Slides version 2.pdf (pp. 36–37)", "02 - Sources/Mechanics of Flight/Aerodynamics - NACA 4-Digit Airfoil Generator.xlsx"]
---

# Aerofoil Geometry and NACA Four-Digit Sections

An aerofoil is the cross-section of a wing; its shape is described by the chord line joining the leading and trailing edges (length $c$), the mean camber line halfway between the upper and lower surfaces, the maximum camber, and the maximum thickness $t$, usually quoted as $t/c$.

The angle of attack of a section is measured from the free stream to the chord line. A symmetric section has its camber line on the chord line and gives no lift at zero angle of attack; camber shifts the lift curve so that lift is produced at zero incidence.

The NACA four-digit code MPXX gives the maximum camber M in percent of the chord, its position P in tenths of the chord from the leading edge, and the maximum thickness XX in percent of the chord. With $m=\text{M}/100$, $p=\text{P}/10$, $t=\text{XX}/100$ and $x$ a fraction of the chord, the camber line is

$$
y_c=\frac{m}{p^2}(2px-x^2)\ \ (x<p),\qquad y_c=\frac{m}{(1-p)^2}\big[(1-2p)+2px-x^2\big]\ \ (x\ge p),
$$

and the half-thickness, laid off perpendicular to the camber line, is

$$
y_t=\frac{t}{0.2}\left(0.2969\sqrt x-0.1260x-0.3516x^2+0.2843x^3-0.1015x^4\right),
$$

the equations of the course spreadsheet. Every four-digit section is thickest at $x\approx0.30c$.

![[mof_m02_naca4412.png|800]]

Worked example (Slides v2, p. 37): NACA 4412 with a 1 m chord has maximum camber $0.04c=0.04$ m at $0.4c=0.4$ m from the leading edge and maximum thickness $0.12c=0.12$ m. NACA 0012 is the symmetric 12% section.

The common trap is to read P as a percentage: in NACA 4412 the second 4 means 0.4 of the chord, not 4%.

## Related

- Topics: [[SESA1015 M02 - Aircraft Geometry, Forces and Coefficients]] (nomenclature, worked example)
- Concepts: [[Wing Planform Geometry]] · [[Dynamic Pressure and Aerodynamic Coefficients]] · [[Aerofoil Stall]]
- Later: [[SESA2022 T4 - Thin Aerofoil Theory]] (lift from camber and incidence)
