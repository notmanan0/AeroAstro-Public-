---
title: "Generalised Hooke's Law"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part B: Statics 2"
aliases: ["3D Hooke's law", "plane stress Hooke's law", "bulk modulus", "isotropic linear elasticity", "constitutive law"]
tags: [feeg1002, concept, statics-2, hookes-law, elasticity]
status: complete
parent_lectures: ["[[FEEG1002 B3 - Generalised Hooke's Law]]", "[[FEEG1002 B5 - Strain Measurement and Strain Rosettes]]"]
related_concepts: ["[[Stress, Strain and Young's Modulus]]", "[[Plane Stress and Plane Strain]]", "[[Thin-Walled Pressure Vessels]]", "[[Strain Gauge Rosettes]]", "[[Thermal Strain]]"]
sources: ["02 - Sources/Statics 2/Lectures/Lecture 04 - Generalised Hooke's Law.pdf"]
---

# Generalised Hooke's Law

The generalised Hooke's law relates all the strain components to all the stress components in a homogeneous, isotropic, linear elastic solid: each normal strain is a direct term from its own stress minus Poisson terms from the other two, $\varepsilon_{xx}=\frac1E[\sigma_{xx}-\nu(\sigma_{yy}+\sigma_{zz})]$, and each shear strain depends only on its own shear stress, $\varepsilon_{xy}=\frac{1+\nu}{E}\sigma_{xy}$.

It is built by superposition. A stress $\sigma_{xx}$ alone stretches the material by $\sigma_{xx}/E$ along $x$ and contracts it by $\nu\sigma_{xx}/E$ in $y$ and $z$; adding the effects of the three normal stresses gives the three normal-strain equations. Shear stresses only change angles and normal stresses only change lengths, a decoupling that holds because the material is isotropic. Only two constants are independent: $G=E/2(1+\nu)$, which can be proved by looking at pure shear in its principal axes, and the bulk modulus $K=E/3(1-2\nu)$, which relates the volumetric strain to a hydrostatic stress, $\varepsilon_{vol}=\sigma_H/K$. Requiring $G$ and $K$ to be positive limits Poisson's ratio to $-1<\nu<0.5$, with $\nu=0.5$ meaning an incompressible material such as rubber.

Two reduced forms cover most problems. In plane stress ($\sigma_{zz}=0$, thin plates and vessel walls) the in-plane law is $\varepsilon_{xx}=(\sigma_{xx}-\nu\sigma_{yy})/E$, the plate still thins with $\varepsilon_{zz}=-\frac\nu E(\sigma_{xx}+\sigma_{yy})$, and the inverse is

$$
\sigma_{xx}=\frac{E}{1-\nu^2}\left(\varepsilon_{xx}+\nu\varepsilon_{yy}\right),\qquad \sigma_{yy}=\frac{E}{1-\nu^2}\left(\varepsilon_{yy}+\nu\varepsilon_{xx}\right),\qquad \sigma_{xy}=\frac{E}{1+\nu}\varepsilon_{xy}
$$

which is how measured gauge strains are turned into stresses. In plane strain ($\varepsilon_{zz}=0$, long dams and tunnels) a stress $\sigma_{zz}=\nu(\sigma_{xx}+\sigma_{yy})$ is needed to hold the length, and the in-plane law becomes $\varepsilon_{xx}=\frac{1+\nu}{E}[(1-\nu)\sigma_{xx}-\nu\sigma_{yy}]$. A temperature change adds $\alpha\Delta T$ to each normal strain.

Ignoring the Poisson terms is the commonest error. In the acrylic submersible hull of Tutorial 3 the axial strain is $-313\ \mu\varepsilon$ with them and $-1204\ \mu\varepsilon$ without, because the hoop compression makes the hull try to lengthen.

![[s2_elastic_constants.png|700]]

## Related

- [[FEEG1002 B3 - Generalised Hooke's Law#2. Plane stress|plane stress]] · [[FEEG1002 B3 - Generalised Hooke's Law#3. Hooke's law in three dimensions|3D law]] · [[FEEG1002 B3 - Generalised Hooke's Law#4. Volume change and the bulk modulus|bulk modulus]] · [[FEEG1002 B3 - Generalised Hooke's Law#5. Plane strain|plane strain]] · [[FEEG1002 B5 - Strain Measurement and Strain Rosettes#7. From strain to stress|stresses from rosettes]]
- [[Stress, Strain and Young's Modulus]] · [[Plane Stress and Plane Strain]] · [[Thin-Walled Pressure Vessels]] · [[Strain Gauge Rosettes]] · [[Thermal Strain]]
- Year 2: element material matrices in [[SESA2029 B6 - 2D and 3D Elements]] · the law in cylindrical coordinates in [[SESA2028 S9 - Continuum Mechanics in Cylindrical Coordinates]]
