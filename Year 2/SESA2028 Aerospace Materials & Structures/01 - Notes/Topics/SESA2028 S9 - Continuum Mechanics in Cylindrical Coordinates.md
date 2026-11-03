---
title: "SESA2028 S9 - Continuum Mechanics in Cylindrical Coordinates"
module: "SESA2028 Aerospace Materials & Structures"
type: topic
stream: "Structures"
order: 9
tags: [sesa2028, structures, continuum-mechanics, polar-coordinates]
date: 2026-10-30
status: lectured
coverage: "SL15 (2026-04-30, ll. 98–418) and SL16 parts 1–2 (2026-05-06)"
parent: ["[[SESA2028 Aerospace Materials & Structures Hub]]"]
prerequisites: ["[[SESA2028 S2 - Beam Deflection and Bending Design]]"]
next_topics: ["[[SESA2028 S10 - Thick Cylinders and Shrink Fits]]"]
key_concepts: ["[[Axisymmetric Equilibrium]]", "[[Polar Strain-Displacement Relations]]", "[[Strain Compatibility]]", "[[Lame Equations]]"]
tutorial_sheets: ["[[SESA2028 Structures Tutorial 5 - Continuum Mechanics Solutions]]"]
sources: ["02 - Sources/Structures Lectures/SL19 - Continuum Mechanics 1 - Review.pdf", "02 - Sources/Structures Lectures/SL20 - Continuum Mechanics 2 - Cylindrical Coords.pdf", "02 - Sources/Structures Lectures/SL21 - Continuum Mechanics 3 - Strain Compatibility.pdf", "02 - Sources/Lectures/SESA2028 Lecture 2026-04-30.txt", "02 - Sources/Lectures/SESA2028 Lecture 2026-05-06 - SL16 (Part 1) Continuum mechanics.txt", "02 - Sources/Lectures/SESA2028 Lecture 2026-05-06 - SL16 (Part 2) Continuum mechanics.txt"]
---

# SESA2028 S9 - Continuum Mechanics in Cylindrical Coordinates

> [!abstract] Summary
> Every point of a loaded body carries a full state of stress and strain, linked by equilibrium (forces balance on every element), compatibility (six strains come from only three displacements, so they must be related) and Hooke's law. For circular bodies such as pressure vessels, tanks and shafts, polar coordinates make these equations tractable; with axial symmetry the shear terms vanish, the strains reduce to $\varepsilon_r=du_r/dr$ and $\varepsilon_\theta=u_r/r$, and equilibrium and compatibility together give the Lamé solution $\sigma_{rr}=A-B/r^2$, $\sigma_{\theta\theta}=A+B/r^2$, with $A$ and $B$ fixed by the boundary conditions.

> [!summary]- Exam use: quick path
> - **Use it when:** a circular or annular body is loaded axisymmetrically and you need its radial and hoop stresses.
> - **Assumptions:** linear elastic, isotropic, homogeneous, axisymmetric, plane stress or plane strain, body forces neglected.
> - **Method:** 1. Write $\sigma_{rr}=A-B/r^2$, $\sigma_{\theta\theta}=A+B/r^2$. 2. Apply the radial stress at each free or loaded surface (pressure is $\sigma_{rr}=-p$). 3. Solve for $A$, $B$. 4. Hooke's law for strains, $u_r=r\varepsilon_\theta$ for displacement. 5. Axial stress from overall equilibrium if needed.
> - **Common mistakes:** a positive sign for an applied pressure; forgetting that plane stress allows $\varepsilon_z$ and plane strain allows $\sigma_z$.
> - **Practise:** [[#Worked example: a solid shaft and a hollow cylinder]]

Continuum mechanics, the last structures topic, analyses the stress and strain at every point of a body rather than resultants on a beam section (2026-04-30, ll. 98–150). It underlies pressure vessels, hydrogen and fuel tanks, shrink fits and rotating parts (2026-05-06 part 1, ll. 1–20).

Take a tiny cube cut from anywhere in a loaded body. Its faces carry pushes, pulls and shears; for it to stay put those must balance, which gives the equilibrium equations. The cube also has to fit with its neighbours after deforming, with no gaps or overlaps, which constrains how its stretches and shears can vary; and the material decides how stress and stretch relate. That gives three sets of equations, and a circular body is easiest to describe with a curved "cube" bounded by radii and arcs.

## 1. Stress, strain and Hooke's law in 3D

The Cauchy stress tensor collects the nine stress components at a point; in $\sigma_{ij}$ the first index gives the direction of the stress and the second the plane it acts on (ll. 98–150). Strains follow from the displacements $u_x$, $u_y$, $u_z$:

$$
\varepsilon_{xx}=\frac{\partial u_x}{\partial x},
\qquad
\varepsilon_{xy}=\frac12\left(\frac{\partial u_x}{\partial y}+\frac{\partial u_y}{\partial x}\right),
\qquad
\gamma_{xy}=2\varepsilon_{xy},
$$

and so on: tensor shear strains are half the engineering ones. Both stress and strain transform between rotated axes as $\boldsymbol\sigma'=\mathbf Q\boldsymbol\sigma\mathbf Q^T$, with $\mathbf Q$ built from the direction cosines (ll. 150–250).

Hooke's law for an isotropic material follows from superposing each stress's direct strain and its Poisson contraction (ll. 200–250):

$$
\varepsilon_{xx}=\frac1E\left[\sigma_{xx}-\nu\left(\sigma_{yy}+\sigma_{zz}\right)\right],
\qquad
\varepsilon_{xy}=\frac{\sigma_{xy}}{2G},
$$

and cyclically; inverted, it gives the stresses in terms of the strains. A student noticed that the slide's $\varepsilon_{zz}$ equation omitted $\sigma_{yy}$, a typo the lecturer confirmed (ll. 210–220).

## 2. Equilibrium and compatibility in Cartesian form

On an element $dx\,dy\,dz$, the stress on the far face in $x$ differs from the near one by $(\partial\sigma_{xx}/\partial x)dx$, and similarly for the shears (ll. 250–300). Summing $x$-forces with a body force $f_x$ per unit volume (gravity, magnetic) and dividing by the volume:

$$
\frac{\partial\sigma_{xx}}{\partial x}+\frac{\partial\sigma_{xy}}{\partial y}+\frac{\partial\sigma_{xz}}{\partial z}+f_x=0,
$$

and likewise in $y$ and $z$. In 2D the $z$ terms drop out. In plane stress the $z$ stresses vanish but $\varepsilon_{zz}$ need not; in plane strain the $z$ strains vanish but $\sigma_{zz}$ need not (ll. 300–320).

Six strains derive from three displacements, so they cannot be independent: the six compatibility equations, found by differentiating and combining the strain definitions, express that the material stays joined, with no cracks or gaps (ll. 320–360; [[Strain Compatibility]]). In 2D,

$$
\frac{\partial^2\varepsilon_{xx}}{\partial y^2}+\frac{\partial^2\varepsilon_{yy}}{\partial x^2}=\frac{\partial^2\gamma_{xy}}{\partial x\,\partial y}.
$$

Substituting Hooke's law and using equilibrium to eliminate the shear stress gives the 2D stress compatibility equation, $\nabla^2(\sigma_{xx}+\sigma_{yy})=0$ with no body forces; asked what was missing from it, the class spotted that $\sigma_{xy}$ had been eliminated through equilibrium (ll. 360–398).

## 3. Equilibrium in polar coordinates

Take an element between radii $r$ and $r+dr$ and angles $\theta$ and $\theta+d\theta$, of unit depth (2026-05-06 part 1, ll. 20–70). Radially, the $\sigma_{rr}$ forces on the curved faces differ through both the stress and the arc length; the hoop stresses on the two radial faces each have a radial component $\sigma_{\theta\theta}dr\sin(d\theta/2)$ pointing inward; and the shear stresses contribute through $\cos(d\theta/2)$. With $\sin(d\theta/2)\approx d\theta/2$, $\cos\approx1$ and higher-order terms dropped, the radial equation is

$$
\frac{\partial\sigma_{rr}}{\partial r}+\frac1r\frac{\partial\sigma_{r\theta}}{\partial\theta}+\frac{\sigma_{rr}-\sigma_{\theta\theta}}{r}+R=0,
$$

and the tangential one

$$
\frac1r\frac{\partial\sigma_{\theta\theta}}{\partial\theta}+\frac{\partial\sigma_{r\theta}}{\partial r}+\frac{2\sigma_{r\theta}}{r}+\Theta=0 .
$$

For an axisymmetric body (rings, cylinders, discs), nothing varies with $\theta$ and $\sigma_{r\theta}=0$, leaving an ordinary differential equation ([[Axisymmetric Equilibrium]]):

$$
\frac{d\sigma_{rr}}{dr}+\frac{\sigma_{rr}-\sigma_{\theta\theta}}{r}=0 \quad\text{(no body force)}.
$$

## 4. Strains in polar coordinates

Radially, a fibre of length $dr$ has its ends move $u_r$ and $u_r+(\partial u_r/\partial r)dr$ (ll. 70–110), so

$$
\varepsilon_{rr}=\frac{\partial u_r}{\partial r}.
$$

Circumferentially there are two effects: the direct change $\frac1r\partial u_\theta/\partial\theta$, and the growth of the arc from $r\,d\theta$ to $(r+u_r)d\theta$ as the element moves outward:

$$
\varepsilon_{\theta\theta}=\frac1r\frac{\partial u_\theta}{\partial\theta}+\frac{u_r}{r}.
$$

The shear strain is the change of the right angle, minus the rigid rotation $u_\theta/r$ that one side undergoes (ll. 110–160):

$$
\gamma_{r\theta}=\frac1r\frac{\partial u_r}{\partial\theta}+\frac{\partial u_\theta}{\partial r}-\frac{u_\theta}{r}.
$$

With axial symmetry, $u_\theta=0$ and $u_r$ depends only on $r$, so ([[Polar Strain-Displacement Relations]])

$$
\varepsilon_{rr}=\frac{du_r}{dr},
\qquad
\varepsilon_{\theta\theta}=\frac{u_r}{r},
\qquad
\gamma_{r\theta}=0 .
$$

## 5. The Lamé solution

Eliminating $u_r$ between the two axisymmetric strains gives compatibility (ll. 160–200):

$$
\varepsilon_{rr}=\frac{d}{dr}\left(r\varepsilon_{\theta\theta}\right).
$$

Substituting Hooke's law and using the axisymmetric equilibrium equation reduces this, for plane stress or plane strain without body forces, to

$$
\frac{d}{dr}\left(\sigma_{rr}+\sigma_{\theta\theta}\right)=0
\quad\Longrightarrow\quad
\sigma_{rr}+\sigma_{\theta\theta}=2A .
$$

Put $\sigma_{\theta\theta}=2A-\sigma_{rr}$ into equilibrium:

$$
\frac{d\sigma_{rr}}{dr}+\frac{2\sigma_{rr}-2A}{r}=0
\quad\Longrightarrow\quad
\frac{d}{dr}\left(r^2\sigma_{rr}\right)=2Ar .
$$

Integrate:

$$
r^2\sigma_{rr}=Ar^2-B
\quad\Longrightarrow\quad
\sigma_{rr}=A-\frac{B}{r^2},
\qquad
\sigma_{\theta\theta}=A+\frac{B}{r^2}.
$$

These are the Lamé equations ([[Lame Equations]]; ll. 200–250); substituting confirms they satisfy the differential equation. The constants come from the boundary conditions, after which Hooke's law gives the strains and $u_r=r\varepsilon_\theta$ the displacement. The assumptions are linear elasticity, an isotropic, homogeneous material, plane stress or plane strain, and negligible body forces; the Cartesian and polar forms suit different shapes (ll. 250–284).

Boundary conditions are either displacement conditions (prescribed movement or restraint) or traction conditions (prescribed surface forces); a pressure $p$ on a surface means $\sigma_{rr}=-p$ there, since the derivation took $\sigma_{rr}$ positive in tension (2026-05-06 part 2, ll. 20–35, 90–100). [[SESA2028 S10 - Thick Cylinders and Shrink Fits|S10]] applies this to pressure vessels.

## Worked example: a solid shaft and a hollow cylinder

At the centre of a solid shaft, $r=0$, the term $B/r^2$ would make the stress infinite, so $B=0$ and $\sigma_{rr}=\sigma_{\theta\theta}=A$ everywhere: under an external pressure $p$, a solid shaft is uniformly compressed, $\sigma_{rr}=\sigma_{\theta\theta}=-p$ (2026-05-08, ll. 351–370). The class worked this out when asked what happens at $r=0$.

For a hollow cylinder with internal pressure $p_i$ only, the boundary conditions $\sigma_{rr}(r_i)=-p_i$ and $\sigma_{rr}(r_o)=0$ give

$$
A-\frac{B}{r_i^2}=-p_i,
\qquad
A-\frac{B}{r_o^2}=0 .
$$

Subtract and solve, with $k=r_o/r_i$:

$$
A=\frac{p_i}{k^2-1},
\qquad
B=\frac{p_ir_o^2}{k^2-1},
$$

$$
\sigma_{rr}=\frac{p_i}{k^2-1}\left(1-\frac{r_o^2}{r^2}\right),
\qquad
\sigma_{\theta\theta}=\frac{p_i}{k^2-1}\left(1+\frac{r_o^2}{r^2}\right).
$$

Both are largest in magnitude at the bore: $\sigma_{rr}=-p_i$ and $\sigma_{\theta\theta}=p_i(k^2+1)/(k^2-1)$. For $k=2$ the bore hoop stress is $5p_i/3$ and the outer one $2p_i/3$, so the material near the outside is under-used, the motivation for compound cylinders in S10.

## Links

- Parent: [[SESA2028 Aerospace Materials & Structures Hub]]
- Previous: [[SESA2028 S8 - Virtual Work and Castigliano Theorems]]
- Next: [[SESA2028 S10 - Thick Cylinders and Shrink Fits]]
- Concepts: [[Axisymmetric Equilibrium]] · [[Polar Strain-Displacement Relations]] · [[Strain Compatibility]] · [[Lame Equations]] · [[Lame Thick-Cylinder Solution]]
- Plane stress and strain in FEA: [[Plane Stress and Plane Strain]]

![[structures_thick_cylinder_lame_stress.png|700]]

## Sources

- Structures slides SL19–SL21 (continuum mechanics review, cylindrical coordinates, strain compatibility), with transcripts `SESA2028 Lecture 2026-04-30.txt` (ll. 98–418) and both parts of `SESA2028 Lecture 2026-05-06 - SL16`; the start of part 2 was not recorded ("I forgot to record")
- The detailed compatibility derivations are in a separate file linked from the slides

## Self-study tasks

### Core

- [ ] Derive the 2D Cartesian equilibrium equations and explain what compatibility means physically (2026-04-30, ll. 250–360). → [[#2. Equilibrium and compatibility in Cartesian form]]
- [ ] Derive the axisymmetric polar equilibrium equation and strains (2026-05-06 part 1, ll. 20–160). → [[#3. Equilibrium in polar coordinates]] · [[#4. Strains in polar coordinates]]
- [ ] Derive the Lamé equations and apply them to a cylinder with internal pressure. → [[#5. The Lamé solution]] · [[#Worked example: a solid shaft and a hollow cylinder]]

### Further practice

- [ ] Work through the linked compatibility derivations in Cartesian and polar coordinates ("you should know being an engineer how to reach at this derivation", part 1, ll. 160–180). → [[#2. Equilibrium and compatibility in Cartesian form]]
