---
title: "SESA2028 S11 - Spinning Discs"
module: "SESA2028 Aerospace Materials & Structures"
type: topic
stream: "Structures"
order: 11
tags: [sesa2028, structures, spinning-disc, continuum-mechanics]
date: 2026-10-30
status: draft
coverage: "Not lectured in 2025–26: slides SL24 only (rotating parts were mentioned as a later topic, 2026-05-06 part 1, l. 12, but the course ended with shrink fits)"
parent: ["[[SESA2028 Aerospace Materials & Structures Hub]]"]
prerequisites: ["[[SESA2028 S10 - Thick Cylinders and Shrink Fits]]"]
next_topics: []
key_concepts: ["[[Spinning Disc Stress]]", "[[Axisymmetric Equilibrium]]"]
tutorial_sheets: []
sources: ["02 - Sources/Structures Lectures/SL24 - Continuum Mechanics 6 - Spinning Discs.pdf"]
---

# SESA2028 S11 - Spinning Discs

> [!abstract] Summary
> A rotating disc is loaded by its own inertia, a radial body force $\rho\omega^2r$ per unit volume, so the axisymmetric equilibrium equation gains a body-force term and the Lamé solution gains an $r^2$ term. For a thin disc in plane stress, $\sigma_{rr}=A-B/r^2-\frac{3+\nu}{8}\rho\omega^2r^2$ and $\sigma_{\theta\theta}=A+B/r^2-\frac{1+3\nu}{8}\rho\omega^2r^2$. A central hole doubles the peak hoop stress compared with a solid disc. This topic has slides in the module folder but was not lectured in 2025–26, so it is outside this year's examined scope.

> [!summary]- Exam use: quick path
> - **Use it when:** a disc, rotor or flywheel spins and its stresses or burst speed are needed (not examinable this year).
> - **Assumptions:** thin disc (plane stress), uniform thickness, linear elastic, isotropic.
> - **Method:** 1. Write the solution with the $\rho\omega^2r^2$ terms. 2. Solid disc: $B=0$; disc with hole: $\sigma_{rr}=0$ at $r_i$. 3. $\sigma_{rr}(r_o)=0$. 4. Peak stress: centre (solid) or bore hoop (hole). 5. Yield check.
> - **Common mistakes:** keeping $B$ in a solid disc; using rev/min instead of rad/s.
> - **Practise:** [[#Worked example: a DVD at full speed]]

Rotating parts, turbine discs above all, are loaded by their own inertia, which grows with the square of the speed. Every element of a spinning disc has to be pulled inward to stay on its circle, and that pull has to come from the material itself, as hoop tension, largest where the disc is most stretched round its circumference.

## 1. Governing equation and solution

Adding the radial body force $\rho\omega^2r$ to the axisymmetric equilibrium equation of [[SESA2028 S9 - Continuum Mechanics in Cylindrical Coordinates|S9]]:

$$
\frac{d\sigma_{rr}}{dr}+\frac{\sigma_{rr}-\sigma_{\theta\theta}}{r}+\rho\omega^2r=0 .
$$

With $\varepsilon_{rr}=du/dr$, $\varepsilon_{\theta\theta}=u/r$ and plane-stress Hooke's law, the displacement satisfies

$$
\frac{d}{dr}\left[\frac1r\frac{d}{dr}(ru)\right]=-\frac{(1-\nu^2)\rho\omega^2r}{E},
$$

whose solution, converted back to stresses, is

$$
\sigma_{rr}=A-\frac{B}{r^2}-\frac{3+\nu}{8}\rho\omega^2r^2,
\qquad
\sigma_{\theta\theta}=A+\frac{B}{r^2}-\frac{1+3\nu}{8}\rho\omega^2r^2 .
$$

## 2. Solid disc and disc with a hole

A solid disc of radius $r_o$ needs $B=0$ for finite stress at the centre, and $\sigma_{rr}(r_o)=0$ gives $A=\frac{3+\nu}{8}\rho\omega^2r_o^2$. The peak, at the centre, is

$$
\sigma_{rr}=\sigma_{\theta\theta}=\frac{3+\nu}{8}\rho\omega^2r_o^2 .
$$

A disc with a central hole of radius $r_i$ has $\sigma_{rr}=0$ at both edges, which gives

$$
A=\frac{3+\nu}{8}\rho\omega^2\left(r_o^2+r_i^2\right),
\qquad
B=\frac{3+\nu}{8}\rho\omega^2r_o^2r_i^2,
$$

and the peak is the hoop stress at the bore:

$$
\sigma_{\theta\theta}(r_i)=\frac{\rho\omega^2}{4}\left[(3+\nu)r_o^2+(1-\nu)r_i^2\right].
$$

As $r_i\to0$ this tends to twice the solid-disc value: even a pinhole doubles the stress, a stress-concentration factor of 2 ([[Spinning Disc Stress]]).

![[structures_spinning_disc_stress.png|700]]

## Worked example: a DVD at full speed

The SL24 example: a polycarbonate DVD ($\rho=1200$ kg/m³, $E=3$ GPa, $\nu=0.32$, $\sigma_Y=60$ MPa), 120 mm across with a 15 mm hole and 1.2 mm thick, spins at 1600 rev/min; find the safety factor against yield by von Mises. Here $\omega=1600\times2\pi/60=167.6$ rad/s. At the bore $\sigma_{rr}=0$, so the von Mises stress equals the hoop stress:

$$
\sigma_{\theta\theta}(r_i)=\frac{1200\times167.6^2}{4}\left[3.32\times0.06^2+0.68\times0.0075^2\right]=0.101\text{ MPa},
$$

a safety factor of about 590 (Python). A DVD is in no danger from its own rotation; the same formula for a 0.3 m titanium disc ($\rho=4500$ kg/m³) with a small bore at 10 000 rev/min gives about 90 MPa, rising with the square of speed and radius, which is why turbine discs are thickest at the bore.

## Links

- Parent: [[SESA2028 Aerospace Materials & Structures Hub]]
- Previous: [[SESA2028 S10 - Thick Cylinders and Shrink Fits]]
- Concepts: [[Spinning Disc Stress]] · [[Axisymmetric Equilibrium]]
- Materials for hot discs: [[SESA2028 M8 - High Temperature Materials - Creep, Oxidation and Superalloys]]

## Sources

- Structures slides `SL24 - Continuum Mechanics 6 - Spinning Discs.pdf` (example on slide 16); not lectured in 2025–26
- Example recomputed in Python

## Self-study tasks

No tasks were set because the topic was not lectured.

### Further practice

- [ ] Derive the disc solution from the equilibrium equation with body force (suggested, not lecturer-set). → [[#1. Governing equation and solution]]
- [ ] The DVD safety factor (slide 16, suggested). → [[#Worked example: a DVD at full speed]]
