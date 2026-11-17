---
title: "Solid Angle"
module: "SESA3029 Aerothermodynamics"
type: concept
stream: "Block 5: Heat transfer"
aliases: ["steradian", "sr"]
tags: [sesa3029, concept, heat-transfer, radiation, geometry]
status: complete
parent_lectures: ["[[SESA3029 W09d - Thermal Radiation]]"]
related_concepts: ["[[Radiation Shape Factor]]"]
sources: ["02 - Sources/Lectures/Lecture5.6(1).pdf"]
---

# Solid Angle

A solid angle is the three-dimensional analogue of a plane angle: the area $S$ that a cone from the centre of a sphere cuts on the sphere, divided by the radius squared, $\omega=S/r^2$, measured in steradians (sr).

A plane angle is arc length over radius, so a whole circle is $2\pi$ rad; on a unit circle the arc length is the angle. In the same way a whole sphere subtends $4\pi r^2/r^2=4\pi$ sr, and on a unit sphere the area of a patch equals its solid angle. A hemisphere is $2\pi$ sr.

In spherical angles, with $\theta$ measured from a surface normal and $\phi$ around it, a patch of the sphere has sides $R\,\mathrm d\theta$ and $R\sin\theta\,\mathrm d\phi$, so $\mathrm d\omega=\sin\theta\,\mathrm d\theta\,\mathrm d\phi$. A surface element $\mathrm dA$ at distance $R$, tilted so that its normal makes angle $\theta$ with the line of sight, subtends $\mathrm d\omega=\mathrm dA\cos\theta/R^2$, its projected area over $R^2$. This is the step that turns geometry into the [[Radiation Shape Factor|shape factor]] integral. Seen from the Sun the Earth subtends $\pi R_E^2/d^2=5.7\times10^{-9}$ sr, a fraction $4.5\times10^{-10}$ of the full sphere.

## Related

- Parent lecture: [[SESA3029 W09d - Thermal Radiation#8. Solid angle|W09d §8]]
- Related concepts: [[Radiation Shape Factor]]

## Sources

- L5.6 slides 4–5.
