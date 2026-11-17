---
title: "Radial Conduction in Cylinders and Spheres"
module: "SESA3029 Aerothermodynamics"
type: concept
stream: "Block 5: Heat transfer"
aliases: ["heat conduction in radial systems", "heat conduction in cylindrical systems", "heat conduction in spherical systems", "conduction through a hollow cylinder", "conduction through a spherical shell", "cylindrical thermal resistance", "spherical thermal resistance"]
tags: [sesa3029, concept, heat-transfer, conduction, cylinder, sphere]
status: complete
parent_lectures: ["[[SESA3029 W09a - Heat Conduction and Thermal Resistance]]"]
related_concepts: ["[[Fourier's Law of Heat Conduction]]", "[[Thermal Resistance]]", "[[Thermal Conductivity]]"]
sources: ["02 - Sources/Lectures/Lecture5.2.pdf"]
---

# Radial Conduction in Cylinders and Spheres

In a long hollow cylinder or a spherical shell whose surfaces are each at a uniform temperature, the temperature depends on radius alone and heat flows radially. Because the area for heat flow grows with radius, the steady temperature profile is logarithmic in a cylinder and varies as $1/r$ in a sphere, not linear as in a plane wall.

In steady conduction without heat generation, an energy balance on a thin shell shows that the same total $\dot Q_r$ crosses every radius, so the flux $\dot Q_r/A_r$ falls as the area grows. Fourier's law with $A_r=2\pi rL$ (cylinder of length $L$) or $A_r=4\pi r^2$ (sphere) then separates and integrates between $T_i$ at $r_i$ and $T_o$ at $r_o$:

$$
\text{cylinder: }\ \dot Q_r=\frac{2\pi kL(T_i-T_o)}{\ln(r_o/r_i)},\qquad
\text{sphere: }\ \dot Q_r=\frac{4\pi k(T_i-T_o)}{1/r_i-1/r_o},
$$

with the profiles $T=T_i-(T_i-T_o)\ln(r/r_i)/\ln(r_o/r_i)$ and $T=T_i-(T_i-T_o)(1/r_i-1/r)/(1/r_i-1/r_o)$. The corresponding [[Thermal Resistance|thermal resistances]] are $\ln(r_o/r_i)/2\pi kL$ and $\frac{1}{4\pi k}(1/r_i-1/r_o)$, and layers wrapped round each other add in series.

For a thin wall ($t=r_o-r_i\ll r_i$) both reduce to the plane-wall $t/kA$. With the inner area the cylinder estimate is 10 % high at $r_o/r_i=1.2$; with the mean-radius area it is 0.3 % low. Aerospace examples are the layered insulation and casing round the propellant of a solid rocket motor (cylinder) and the multi-layer insulation of a near-spherical cryogenic propellant tank, which limits boil-off (sphere).

![[at_w09a_radial_profiles.png|760]]

## Related

- Parent lectures: [[SESA3029 W09a - Heat Conduction and Thermal Resistance#6. Radial conduction in a long hollow cylinder|W09a §6]] (cylinder) · [[SESA3029 W09a - Heat Conduction and Thermal Resistance#8. Conduction in a spherical shell|W09a §8]] (sphere)
- Related concepts: [[Fourier's Law of Heat Conduction]] · [[Thermal Resistance]] · [[Thermal Conductivity]]
- The insulated tube, and why insulating a thin pipe can increase its heat loss: [[SESA3029 W09c - Critical Thickness of Insulation and Fins|W09c]]; the radial finite-difference stencil: [[SESA3029 W09e - Numerical Methods in Conduction|W09e]]

## Sources

- Sources: L5.2 slides 3–8 and 16.
- Notes: written ahead from the slides, before the lecture.
