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
> Every point of a loaded body carries a full state of stress and strain, linked by equilibrium (forces balance on every element), compatibility (six strains come from only three displacements, so they must be related) and Hooke's law. For circular bodies such as pressure vessels, tanks and shafts, polar coordinates make these equations tractable. With axial symmetry the shear terms vanish, the strains reduce to $\varepsilon_{rr}=du_r/dr$ and $\varepsilon_{\theta\theta}=u_r/r$, and equilibrium and compatibility together give the Lamé solution $\sigma_{rr}=A-B/r^2$, $\sigma_{\theta\theta}=A+B/r^2$, with $A$ and $B$ fixed by the boundary conditions.

> [!summary]- Exam use: quick path
> - **Use it when:** a circular or annular body is loaded axisymmetrically and you need its radial and hoop stresses or its radial displacement.
> - **Assumptions:** linear elastic, isotropic, homogeneous, axisymmetric, plane stress or plane strain, body forces neglected (until the spinning disc of [[SESA2028 S11 - Spinning Discs|S11]]).
> - **Method:** 1. Write $\sigma_{rr}=A-B/r^2$, $\sigma_{\theta\theta}=A+B/r^2$. 2. Apply the radial stress at each free or loaded surface (a pressure $p$ means $\sigma_{rr}=-p$). 3. Solve for $A$, $B$. 4. Hooke's law for the strains, $u_r=r\varepsilon_{\theta\theta}$ for the displacement. 5. Axial stress from overall equilibrium if the ends are closed.
> - **Common mistakes:** a positive sign for an applied pressure; forgetting that plane stress allows $\varepsilon_{zz}$ and plane strain allows $\sigma_{zz}$.
> - **Practise:** [[#Worked example: a solid shaft and a hollow cylinder]] · [[SESA2028 Structures Tutorial 5 - Continuum Mechanics Solutions]]

Continuum mechanics analyses the stress and strain at every point of a body rather than the resultants on a beam section. It underlies pressure vessels, hydrogen and fuel tanks, shrink fits and rotating parts such as turbine discs.

The faces of a tiny cube cut from anywhere in a loaded body carry pushes, pulls and shears, and for it to stay put those must balance, which gives the equilibrium equations. The cube also has to fit with its neighbours after deforming, with no gaps or overlaps, which constrains how its stretches and shears can vary from point to point: compatibility. And the material decides how stress and stretch are related: Hooke's law. Those three sets of equations are the whole theory. A circular body is easiest to describe with a curved "cube" bounded by two radii and two arcs, and for a body that looks the same at every angle the equations collapse to one ordinary differential equation.

## 1. Stress, strain and Hooke's law in 3D

The Cauchy stress tensor collects the nine stress components at a point:

$$
\boldsymbol\sigma=\begin{pmatrix}\sigma_{xx}&\sigma_{xy}&\sigma_{xz}\\\sigma_{xy}&\sigma_{yy}&\sigma_{yz}\\\sigma_{xz}&\sigma_{yz}&\sigma_{zz}\end{pmatrix}.
$$

In $\sigma_{ij}$ the first index gives the direction of the stress and the second the plane it acts on. Moment equilibrium of a small cube makes the tensor symmetric, $\sigma_{ij}=\sigma_{ji}$, so six components are independent. The strains follow from the displacements $u_x$, $u_y$, $u_z$:

$$
\varepsilon_{xx}=\frac{\partial u_x}{\partial x},\qquad\varepsilon_{xy}=\frac12\left(\frac{\partial u_x}{\partial y}+\frac{\partial u_y}{\partial x}\right),\qquad\gamma_{xy}=2\varepsilon_{xy},
$$

and so on cyclically: the tensor shear strains are half the engineering ones. Both stress and strain transform between rotated axes as

$$
\boldsymbol\sigma'=\mathbf Q\boldsymbol\sigma\mathbf Q^T,
$$

with $\mathbf Q$ built from the direction cosines between the old and new axes.

Hooke's law for an isotropic material follows from superposing each normal stress's direct strain and its Poisson contraction in the other two directions:

$$
\varepsilon_{xx}=\frac1E\left[\sigma_{xx}-\nu\left(\sigma_{yy}+\sigma_{zz}\right)\right],\qquad\varepsilon_{yy}=\frac1E\left[\sigma_{yy}-\nu\left(\sigma_{zz}+\sigma_{xx}\right)\right],\qquad\varepsilon_{zz}=\frac1E\left[\sigma_{zz}-\nu\left(\sigma_{xx}+\sigma_{yy}\right)\right],
$$

with the shears uncoupled, $\varepsilon_{xy}=\sigma_{xy}/2G$ and cyclically, where $G=E/2(1+\nu)$. Inverted, these give the stresses in terms of the strains.

## 2. Equilibrium and compatibility in Cartesian form

### Equilibrium

On an element $dx\,dy\,dz$, the stress on the far $x$-face differs from that on the near one by $(\partial\sigma_{xx}/\partial x)\,dx$, and similarly for the shears on the $y$- and $z$-faces. Sum the $x$-forces, including a body force $f_x$ per unit volume (gravity, a magnetic force, or centrifugal force in a rotating part):

$$
\frac{\partial\sigma_{xx}}{\partial x}dx\,dy\,dz+\frac{\partial\sigma_{xy}}{\partial y}dy\,dx\,dz+\frac{\partial\sigma_{xz}}{\partial z}dz\,dx\,dy+f_x\,dx\,dy\,dz=0 .
$$

Divide by the volume:

$$
\frac{\partial\sigma_{xx}}{\partial x}+\frac{\partial\sigma_{xy}}{\partial y}+\frac{\partial\sigma_{xz}}{\partial z}+f_x=0,
$$

and likewise in $y$ and $z$. In 2D the $z$ terms drop out. Two 2D idealisations differ in what they release: in **plane stress** (a thin plate) the $z$ stresses vanish but $\varepsilon_{zz}$ need not; in **plane strain** (a long body restrained along $z$) the $z$ strains vanish but $\sigma_{zz}$ need not.

### Compatibility

Six strains derive from three displacements, so they cannot be independent: the compatibility equations, found by differentiating and combining the strain definitions, express that the material stays joined, with no cracks or overlaps ([[Strain Compatibility]]). In 2D, differentiate $\varepsilon_{xx}=\partial u_x/\partial x$ twice with respect to $y$ and $\varepsilon_{yy}=\partial u_y/\partial y$ twice with respect to $x$, and add:

$$
\frac{\partial^2\varepsilon_{xx}}{\partial y^2}+\frac{\partial^2\varepsilon_{yy}}{\partial x^2}=\frac{\partial^3u_x}{\partial x\,\partial y^2}+\frac{\partial^3u_y}{\partial x^2\,\partial y}=\frac{\partial^2}{\partial x\,\partial y}\left(\frac{\partial u_x}{\partial y}+\frac{\partial u_y}{\partial x}\right).
$$

The bracket is $\gamma_{xy}$, so

$$
\frac{\partial^2\varepsilon_{xx}}{\partial y^2}+\frac{\partial^2\varepsilon_{yy}}{\partial x^2}=\frac{\partial^2\gamma_{xy}}{\partial x\,\partial y}.
$$

Substituting Hooke's law and using equilibrium to eliminate the shear stress gives the 2D stress compatibility equation, which with no body forces is $\nabla^2(\sigma_{xx}+\sigma_{yy})=0$. The polar version of the same idea produces the Lamé solution in §5.

## 3. Equilibrium in polar coordinates

The element lies at $(r,\theta)$ between radii $r$ and $r+\delta r$ and angles $\theta$ and $\theta+\delta\theta$, with depth $\delta z$ and body forces $f_r$, $f_\theta$ per unit volume. By moment equilibrium $\sigma_{r\theta}=\sigma_{\theta r}$.

![[structures_s9_polar_element_and_lame.png|900]]

### Radial equilibrium

Collect the radial forces on the element. The inner curved face has area $r\,\delta\theta\,\delta z$ and the outer one $(r+\delta r)\,\delta\theta\,\delta z$, so the radial stresses give

$$
\left(\sigma_{rr}+\frac{\partial\sigma_{rr}}{\partial r}\delta r\right)(r+\delta r)\,\delta\theta\,\delta z-\sigma_{rr}\,r\,\delta\theta\,\delta z .
$$

The hoop stresses act on the two radial faces, each of area $\delta r\,\delta z$. The faces are inclined to each other by $\delta\theta$, so each hoop force has a component $\sin(\delta\theta/2)$ pointing towards the centre:

$$
-\sigma_{\theta\theta}\,\delta r\,\delta z\sin\frac{\delta\theta}{2}-\left(\sigma_{\theta\theta}+\frac{\partial\sigma_{\theta\theta}}{\partial\theta}\delta\theta\right)\delta r\,\delta z\sin\frac{\delta\theta}{2}.
$$

The shear stresses on the radial faces act radially, with a factor $\cos(\delta\theta/2)$:

$$
\left(\sigma_{r\theta}+\frac{\partial\sigma_{r\theta}}{\partial\theta}\delta\theta\right)\delta r\,\delta z\cos\frac{\delta\theta}{2}-\sigma_{r\theta}\,\delta r\,\delta z\cos\frac{\delta\theta}{2}.
$$

The body force contributes $f_r\,r\,\delta\theta\,\delta r\,\delta z$. Letting $\delta\theta\to0$ makes $\sin(\delta\theta/2)\to\delta\theta/2$ and $\cos(\delta\theta/2)\to1$, and products of three or more small quantities are dropped. The radial-stress terms leave $\sigma_{rr}\,\delta r\,\delta\theta\,\delta z+r\,\frac{\partial\sigma_{rr}}{\partial r}\delta r\,\delta\theta\,\delta z$; the hoop terms leave $-\sigma_{\theta\theta}\,\delta r\,\delta\theta\,\delta z$; the shear terms leave $\frac{\partial\sigma_{r\theta}}{\partial\theta}\delta\theta\,\delta r\,\delta z$. Divide everything by $r\,\delta r\,\delta\theta\,\delta z$:

$$
\frac{\partial\sigma_{rr}}{\partial r}+\frac1r\frac{\partial\sigma_{r\theta}}{\partial\theta}+\frac{\sigma_{rr}-\sigma_{\theta\theta}}{r}+f_r=0 .
$$

The term $(\sigma_{rr}-\sigma_{\theta\theta})/r$ has no Cartesian counterpart: it comes from the curvature of the element, the hoop forces pulling inwards and the outer face being larger than the inner one.

### Tangential equilibrium

A similar balance of tangential forces gives

$$
\frac1r\frac{\partial\sigma_{\theta\theta}}{\partial\theta}+\frac{\partial\sigma_{r\theta}}{\partial r}+\frac{2\sigma_{r\theta}}{r}+f_\theta=0 .
$$

### Equilibrium with axial symmetry

Rings, cylinders and circular discs are axially symmetric about $z$. Nothing then varies with $\theta$, so $\partial/\partial\theta=0$, and there is no shear stress, $\sigma_{r\theta}=0$. The tangential equation is satisfied identically, and the radial one becomes an ordinary differential equation in $r$ ([[Axisymmetric Equilibrium]]):

$$
\boxed{\frac{d\sigma_{rr}}{dr}+\frac{\sigma_{rr}-\sigma_{\theta\theta}}{r}+f_r=0}
$$

## 4. Strains in polar coordinates

### Radial strain

A radial fibre of length $\delta r$ has its inner end displaced $u_r$ and its outer end $u_r+(\partial u_r/\partial r)\,\delta r$:

$$
\varepsilon_{rr}=\frac{\left(u_r+\frac{\partial u_r}{\partial r}\delta r\right)-u_r}{\delta r}=\frac{\partial u_r}{\partial r}.
$$

### Hoop strain

Circumferentially there are two contributions. The direct change in tangential length, from the tangential displacements of the two ends of an arc $r\,\delta\theta$, gives

$$
\frac{\left(u_\theta+\frac{\partial u_\theta}{\partial\theta}\delta\theta\right)-u_\theta}{r\,\delta\theta}=\frac1r\frac{\partial u_\theta}{\partial\theta}.
$$

And moving the arc outward by $u_r$ increases its length from $r\,\delta\theta$ to $(r+u_r)\,\delta\theta$, because the circumference grows with radius:

$$
\frac{(r+u_r)\,\delta\theta-r\,\delta\theta}{r\,\delta\theta}=\frac{u_r}{r}.
$$

The total hoop strain is the sum:

$$
\varepsilon_{\theta\theta}=\frac1r\frac{\partial u_\theta}{\partial\theta}+\frac{u_r}{r}.
$$

### Shear strain

The shear strain is the sum of the changes in angle of the two adjacent sides. The radial side rotates by $\partial u_\theta/\partial r$, but part of that, $u_\theta/r$, is a rigid rotation about the origin and produces no strain; the tangential side rotates by $\frac1r\partial u_r/\partial\theta$. So

$$
\gamma_{r\theta}=\frac1r\frac{\partial u_r}{\partial\theta}+\frac{\partial u_\theta}{\partial r}-\frac{u_\theta}{r}.
$$

### Strains with axial symmetry

With axial symmetry $u_\theta=0$ and $u_r$ depends only on $r$, so ([[Polar Strain-Displacement Relations]])

$$
\varepsilon_{rr}=\frac{du_r}{dr},\qquad\varepsilon_{\theta\theta}=\frac{u_r}{r},\qquad\gamma_{r\theta}=0 .
$$

## 5. The Lamé solution

### Compatibility of the two strains

Two strains come from one displacement, so they are related. From the hoop strain, $u_r=r\varepsilon_{\theta\theta}$; substitute into the radial strain:

$$
\varepsilon_{rr}=\frac{d}{dr}\left(r\varepsilon_{\theta\theta}\right)=\varepsilon_{\theta\theta}+r\frac{d\varepsilon_{\theta\theta}}{dr}.
$$

### Substituting Hooke's law

In plane stress, $\varepsilon_{rr}=(\sigma_{rr}-\nu\sigma_{\theta\theta})/E$ and $\varepsilon_{\theta\theta}=(\sigma_{\theta\theta}-\nu\sigma_{rr})/E$. Multiply the compatibility equation by $E$:

$$
\sigma_{rr}-\nu\sigma_{\theta\theta}=\sigma_{\theta\theta}-\nu\sigma_{rr}+r\left(\frac{d\sigma_{\theta\theta}}{dr}-\nu\frac{d\sigma_{rr}}{dr}\right).
$$

Collect the undifferentiated terms on the left:

$$
(1+\nu)\left(\sigma_{rr}-\sigma_{\theta\theta}\right)=r\left(\frac{d\sigma_{\theta\theta}}{dr}-\nu\frac{d\sigma_{rr}}{dr}\right).
$$

Without body forces, equilibrium gives $\sigma_{rr}-\sigma_{\theta\theta}=-r\,d\sigma_{rr}/dr$. Substitute and divide by $r$:

$$
-(1+\nu)\frac{d\sigma_{rr}}{dr}=\frac{d\sigma_{\theta\theta}}{dr}-\nu\frac{d\sigma_{rr}}{dr}.
$$

The $\nu$ terms cancel:

$$
\frac{d}{dr}\left(\sigma_{rr}+\sigma_{\theta\theta}\right)=0\quad\Longrightarrow\quad\sigma_{rr}+\sigma_{\theta\theta}=2A,
$$

a constant. Plane strain gives the same result with $E$ and $\nu$ replaced by plane-strain values, which cancel in the same way.

### Solving

Put $\sigma_{\theta\theta}=2A-\sigma_{rr}$ into equilibrium:

$$
\frac{d\sigma_{rr}}{dr}+\frac{2\sigma_{rr}-2A}{r}=0 .
$$

Multiply by $r^2$; the left-hand side becomes an exact derivative:

$$
r^2\frac{d\sigma_{rr}}{dr}+2r\sigma_{rr}=2Ar\quad\Longleftrightarrow\quad\frac{d}{dr}\left(r^2\sigma_{rr}\right)=2Ar .
$$

Integrate, writing the constant of integration as $-B$:

$$
r^2\sigma_{rr}=Ar^2-B .
$$

Divide by $r^2$ and use $\sigma_{\theta\theta}=2A-\sigma_{rr}$:

$$
\boxed{\sigma_{rr}=A-\frac{B}{r^2},\qquad\sigma_{\theta\theta}=A+\frac{B}{r^2}}
$$

These are the Lamé equations ([[Lame Equations]]). Substituting back confirms them: $d\sigma_{rr}/dr=2B/r^3$ and $(\sigma_{rr}-\sigma_{\theta\theta})/r=-2B/r^3$, which sum to zero. The constants come from the boundary conditions, after which Hooke's law gives the strains and $u_r=r\varepsilon_{\theta\theta}$ the displacement. The assumptions are linear elasticity, an isotropic, homogeneous material, plane stress or plane strain, axial symmetry and negligible body forces.

### Boundary conditions

Boundary conditions are of two kinds: displacement conditions (a prescribed movement or restraint, such as the interference of a shrink fit) and traction conditions (prescribed surface forces). A pressure $p$ pushes on a surface, whereas the derivation took $\sigma_{rr}$ positive in tension, so a pressure means

$$
\sigma_{rr}=-p
$$

at that surface, and a free surface means $\sigma_{rr}=0$. [[SESA2028 S10 - Thick Cylinders and Shrink Fits|S10]] applies this to pressure vessels and shrink fits.

## Worked example: a solid shaft and a hollow cylinder

### Solid shaft under external pressure

At the centre of a solid shaft, $r=0$, the term $B/r^2$ would make the stress infinite, so $B=0$ and $\sigma_{rr}=\sigma_{\theta\theta}=A$ everywhere. An external pressure $p$ gives $\sigma_{rr}(R)=-p$, so $A=-p$: the shaft is uniformly compressed, $\sigma_{rr}=\sigma_{\theta\theta}=-p$, a state of equal biaxial compression with no stress gradient.

### Hollow cylinder under internal pressure

For a cylinder with internal pressure $p_i$ only, the boundary conditions are $\sigma_{rr}(r_i)=-p_i$ and $\sigma_{rr}(r_o)=0$:

$$
A-\frac{B}{r_i^2}=-p_i,\qquad A-\frac{B}{r_o^2}=0 .
$$

Subtract the first from the second:

$$
B\left(\frac{1}{r_i^2}-\frac{1}{r_o^2}\right)=p_i\quad\Longrightarrow\quad B=\frac{p_ir_i^2r_o^2}{r_o^2-r_i^2}.
$$

Then $A=B/r_o^2$. With $k=r_o/r_i$,

$$
A=\frac{p_i}{k^2-1},\qquad B=\frac{p_ir_o^2}{k^2-1},
$$

$$
\sigma_{rr}=\frac{p_i}{k^2-1}\left(1-\frac{r_o^2}{r^2}\right),\qquad\sigma_{\theta\theta}=\frac{p_i}{k^2-1}\left(1+\frac{r_o^2}{r^2}\right).
$$

Both are largest in magnitude at the bore:

$$
\sigma_{rr}(r_i)=-p_i,\qquad\sigma_{\theta\theta}(r_i)=p_i\frac{k^2+1}{k^2-1}.
$$

For $k=2$ the bore hoop stress is $5p_i/3$ and the outer one $2p_i/3$, so the material near the outside is under-used, the motivation for compound cylinders in S10.

> [!check] Force balance and the thin-wall limit
> Cut the cylinder along a diameter. Per unit length, the pressure pushes the halves apart with $2p_ir_i$, and the hoop stress across the two walls resists with $2\int_{r_i}^{r_o}\sigma_{\theta\theta}\,dr$. Integrating, $\int\sigma_{\theta\theta}\,dr=A(r_o-r_i)+B(1/r_i-1/r_o)=p_ir_i$, so the balance holds exactly and the wall-average hoop stress is $p_ir_i/t$. For a thin wall, $k=1+t/r_i$ with $t\ll r_i$, the bore value $(k^2+1)/(k^2-1)\approx r_i/t$, and $\sigma_{\theta\theta}\to p_ir/t$, the familiar thin-cylinder result.

## Links

- Parent: [[SESA2028 Aerospace Materials & Structures Hub]] · Previous: [[SESA2028 S8 - Virtual Work and Castigliano Theorems]] · Next: [[SESA2028 S10 - Thick Cylinders and Shrink Fits]]
- Concepts: [[Axisymmetric Equilibrium]] · [[Polar Strain-Displacement Relations]] · [[Strain Compatibility]] · [[Lame Equations]] · [[Lame Thick-Cylinder Solution]]
- Problems: [[SESA2028 Structures Tutorial 5 - Continuum Mechanics Solutions]] · Formulae: [[SESA2028 Formula Sheet]]
- Plane stress and strain in finite elements: [[Plane Stress and Plane Strain]]

## Sources

- Slides: `SL19 - Continuum Mechanics 1 - Review.pdf` (stress, strain, Hooke's law, Cartesian equilibrium and compatibility), `SL20 - Continuum Mechanics 2 - Cylindrical Coords.pdf` (polar equilibrium and strains) and `SL21 - Continuum Mechanics 3 - Strain Compatibility.pdf` (compatibility and the Lamé equations); the detailed compatibility derivations are in a separate file linked from the slides.
- Transcripts: `SESA2028 Lecture 2026-04-30.txt` (ll. 98–418) and both parts of `SESA2028 Lecture 2026-05-06 - SL16`; the start of part 2 was not recorded.
- The Lamé reduction and the force balance were checked with SymPy. Figure: `generate_structures_s9_figures.py`.

## Self-study tasks

### Core

- [ ] Derive the 2D Cartesian equilibrium equations and explain what compatibility means physically (2026-04-30, ll. 250–360). → [[#2. Equilibrium and compatibility in Cartesian form]]
- [ ] Derive the axisymmetric polar equilibrium equation and the polar strains (2026-05-06 part 1, ll. 20–160). → [[#3. Equilibrium in polar coordinates]] · [[#4. Strains in polar coordinates]]
- [ ] Derive the Lamé equations and apply them to a cylinder with internal pressure. → [[#5. The Lamé solution]] · [[#Hollow cylinder under internal pressure]]
- [ ] Structures tutorial 5. → [[SESA2028 Structures Tutorial 5 - Continuum Mechanics Solutions]]

### Further practice

- [ ] Work through the linked compatibility derivations in Cartesian and polar coordinates; you are expected to be able to reach them yourself (2026-05-06 part 1, ll. 160–180). → [[#Compatibility]] · [[#Compatibility of the two strains]]
- [ ] Show that the Lamé hoop stress integrates to $p_ir_i$ across the wall (suggested, not lecturer-set). → [[#Hollow cylinder under internal pressure]]

## Transcript and slide slips

> [!warning] Slide slip: Hooke's law (SL19; 2026-04-30, ll. 210–220)
> Where: [[#1. Stress, strain and Hooke's law in 3D]].
>
> The slide's $\varepsilon_{zz}$ equation omits $\sigma_{yy}$; it should read $\varepsilon_{zz}=[\sigma_{zz}-\nu(\sigma_{xx}+\sigma_{yy})]/E$.

> [!warning] Slide slip: element labels (SL20 slides 4–5)
> Where: [[#Radial equilibrium]].
>
> The element sketch labels the increased shear stress on the far radial face as $\sigma_{r\theta}+\frac{\partial\sigma_{\theta\theta}}{\partial\theta}\delta\theta$; it should be $\sigma_{r\theta}+\frac{\partial\sigma_{r\theta}}{\partial\theta}\delta\theta$, as the force balance on the same slide uses.
