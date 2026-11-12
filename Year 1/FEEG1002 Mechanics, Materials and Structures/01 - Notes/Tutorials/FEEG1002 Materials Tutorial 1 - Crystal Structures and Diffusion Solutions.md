---
title: "FEEG1002 Materials Tutorial 1 - Crystal Structures and Diffusion Solutions"
module: "FEEG1002 Mechanics, Materials and Structures"
type: tutorial
stream: "Part C: Materials"
tags: [feeg1002, tutorial-solutions, materials, crystallography, miller-indices, diffusion]
sheet: "Materials Tutorial Sheet 1"
theory_notes: ["[[FEEG1002 C2 - Crystal Structures and Crystallography]]", "[[FEEG1002 C3 - Diffusion]]"]
key_concepts: ["[[Crystal Structures and Atomic Packing Factor]]", "[[Miller Indices for Planes and Directions]]", "[[Fick's Laws and Arrhenius Diffusion]]"]
status: complete
date: 2026-11-05
sources: ["02 - Sources/Materials/Tutorials/Tutorial Sheet 01 - Crystal Structures, Planes and Directions.pdf"]
---

# FEEG1002 Materials Tutorial 1 - Crystal Structures and Diffusion Solutions

> [!abstract] Sheet info
> Nine questions on the three metallic unit cells, packing, Miller indices and diffusion. The sheet prints no answers, so every result below was worked independently and the numbers were checked in Python. Q1–Q7 use [[FEEG1002 C2 - Crystal Structures and Crystallography|C2]]; Q8–Q9 use [[FEEG1002 C3 - Diffusion|C3]].

## Q1 and Q2 - Unit cells and stacking

Taught in: [[FEEG1002 C2 - Crystal Structures and Crystallography#2. Building solids by stacking close-packed layers]].

The FCC cell has an atom at each of the eight corners of a cube and one at the centre of each of the six faces. The BCC cell has an atom at each corner and one at the centre of the cube. The HCP cell is a hexagonal prism with an atom at each of the twelve corners, one at the centre of each hexagonal face, and three inside, halfway up.

![[m2_unit_cells.png|900]]

Both FCC and HCP are built from close-packed layers. HCP stacks them ABAB…, the third layer sitting directly over the first, so that the cell has close-packed planes at its top (A), middle (B) and bottom (A). FCC stacks them ABCABC…, the third layer going into the hollows over neither of the first two, and the close-packed layers run diagonally through the cube as the $\{111\}$ planes. Both have the same, maximum, packing of equal spheres; BCC is not close-packed at all.

![[m2_stacking.png|900]]

## Q3 - Lattice parameter of BCC

Taught in: [[FEEG1002 C2 - Crystal Structures and Crystallography#Lattice parameter in terms of the atomic radius]].

In BCC the atoms touch along the body diagonal of the cube: corner atom, body-centre atom, opposite corner atom. The diagonal therefore spans $R+2R+R=4R$. By Pythagoras in three dimensions the body diagonal of a cube of side $a$ is $\sqrt{a^2+a^2+a^2}=a\sqrt3$, so

$$
a\sqrt3=4R
$$

$$
\boxed{a=\frac{4R}{\sqrt3}}
$$

## Q4 - Atoms per unit cell

Taught in: [[FEEG1002 C2 - Crystal Structures and Crystallography#Atoms per unit cell]].

A corner atom is shared by eight cells, a face atom by two, and a body atom belongs to one cell only.

$$
n_{FCC}=8\times\tfrac18+6\times\tfrac12=\boxed4
$$

$$
n_{BCC}=8\times\tfrac18+1=\boxed2
$$

## Q5 - Atomic packing factor

Taught in: [[FEEG1002 C2 - Crystal Structures and Crystallography#Atomic packing factor]].

The volume of the atoms in a cell is $n\times\tfrac43\pi R^3$; the volume of the cell is $a^3$.

For FCC the atoms touch along a face diagonal, $a\sqrt2=4R$, so $a=2\sqrt2R$ and $a^3=16\sqrt2R^3$:

$$
\mathrm{APF}_{FCC}=\frac{4\times\tfrac43\pi R^3}{16\sqrt2R^3}=\frac{16\pi/3}{16\sqrt2}=\frac{\pi}{3\sqrt2}=\boxed{0.740}
$$

For BCC, $a=4R/\sqrt3$ and $a^3=64R^3/(3\sqrt3)$:

$$
\mathrm{APF}_{BCC}=\frac{2\times\tfrac43\pi R^3}{64R^3/(3\sqrt3)}=\frac{8\pi\times3\sqrt3}{3\times64}=\frac{\pi\sqrt3}{8}=\boxed{0.680}
$$

FCC has the higher packing factor because it is built from close-packed layers, the densest way of stacking equal spheres. BCC has no close-packed planes, so it leaves more empty space: 32 % against 26 %.

![[m2_apf_geometry.png|900]]

## Q6 - Calcium changing from FCC to BCC

Taught in: [[FEEG1002 C2 - Crystal Structures and Crystallography#Worked example - the shrinking iron wire]].

The number of atoms is fixed, so compare the volume per atom, $a^3/n$, not the volume per cell. With $R=0.1969$ nm unchanged:

$$
a_{FCC}=2\sqrt2R=0.5569\ \mathrm{nm},\qquad v_{FCC}=\frac{a_{FCC}^3}{4}=\frac{0.17273}{4}=0.043183\ \mathrm{nm^3}
$$

$$
a_{BCC}=\frac{4R}{\sqrt3}=0.4547\ \mathrm{nm},\qquad v_{BCC}=\frac{a_{BCC}^3}{2}=\frac{0.09402}{2}=0.047012\ \mathrm{nm^3}
$$

$$
\frac{\Delta V}{V}=\frac{v_{BCC}-v_{FCC}}{v_{FCC}}=\frac{0.047012-0.043183}{0.043183}=\boxed{+0.0887}
$$

There is an **expansion** of 8.9 % in volume, about 2.9 % in each linear dimension. It is an expansion because the calcium goes from a close-packed structure (APF 0.74) to a more open one (0.68); the ratio of the volumes per atom is just $0.740/0.680=1.089$. In reality the atomic radius changes slightly with the number of neighbours, so the measured change is smaller (for iron, about 1 % instead of 8 %, as the topic note shows), but the sign is right.

## Q7 - Directions and planes

Taught in: [[FEEG1002 C2 - Crystal Structures and Crystallography#5. Miller indices]].

For a direction $[uvw]$ the arrow runs from the origin to the point $(u,v,w)$, scaled to stay in the cell; for a plane $(hkl)$ the intercepts are $1/h$, $1/k$, $1/l$, with $1/0=\infty$.

| Indices | Direction (from origin, scaled into the cell) | Plane intercepts |
|---|---|---|
| $[101]$, $(101)$ | to $(1,0,1)$, a face diagonal of the $y=0$ face | $x=1$, $y=\infty$, $z=1$: the plane $x+z=1$ |
| $[1\bar10]$, $(1\bar10)$ | to $(1,-1,0)$, which leaves the cell; move the origin to $(0,1,0)$ and draw from there to $(1,0,0)$ | $x=1$, $y=-1$, $z=\infty$: the plane $x-y=1$ touches the cell only along an edge, so draw the parallel member $x-y=0$, the diagonal plane through the $z$ axis and the edge at $(1,1,z)$ |
| $[2\bar12]$, $(2\bar12)$ | to $(1,-\tfrac12,1)$ after halving; from the shifted origin $(0,1,0)$ to $(1,\tfrac12,1)$ | $x=\tfrac12$, $y=-1$, $z=\tfrac12$: the plane $2x-y+2z=1$, which cuts the cell in a quadrilateral through $(\tfrac12,0,0)$, $(1,1,0)$, $(0,1,1)$ and $(0,0,\tfrac12)$ |

![[m2_t1_q7_directions_planes.png|900]]

The relationship: in a cubic crystal, the direction $[hkl]$ is perpendicular to the plane $(hkl)$ with the same indices. The plane with intercepts $1/h$, $1/k$, $1/l$ is $hx+ky+lz=1$, whose normal is the vector $(h,k,l)$. This holds only for cubic cells, with equal axes at right angles.

## Q8 - Diffusion

Taught in: [[FEEG1002 C3 - Diffusion#1. Diffusion mechanisms]] and [[FEEG1002 C3 - Diffusion#Working with the Arrhenius equation]].

**(a)** Hydrogen through steel is much faster. A hydrogen atom is tiny and diffuses interstitially, hopping between the gaps in the iron lattice, of which there are always plenty, so it never has to wait for a vacancy, and the BCC lattice of ferrite is relatively open (APF 0.68). Silicon in aluminium is a substitutional solute of similar size to the host atoms, so it can only move by jumping into a vacancy next to it, a much higher activation energy and a rate limited by the number of vacancies. Interstitial diffusion is always faster than substitutional (vacancy) diffusion; the slide data for carbon against iron in α-iron at 500 °C differ by a factor of about $10^9$.

**(b)** No. The diffusion coefficient follows $D=D_0\exp(-Q/RT)$ with $T$ in kelvin, so it depends exponentially on $1/T$, not linearly on $T$. "Doubling" a temperature in °C does not even double the absolute temperature: 450 °C to 900 °C is 723 K to 1173 K, a factor of 1.62. Over that range $D$ for carbon in iron rises by a factor of the order of 100 or more (165 for carbon in α-iron with $Q=80$ kJ/mol). The carbon concentration at a given depth does not scale with $D$ either: it depends on how far the carbon has spread, which grows with $\sqrt{Dt}$ (the only length that can be made from $D$ and $t$), and it is bounded by the surface concentration. So the concentration at a fixed depth after a fixed time increases, often greatly, but not by a factor of two, and not in proportion to anything simple. (Also, carburising is done in the austenite range, where the structure, and so $D$, changes again.)

## Q9 - Carbon in a BCC interstitial site

Taught in: [[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation#Interstitial carbon and the yield point of steel]].

The site at the middle of a cube face of BCC iron, $(\tfrac12,\tfrac12,0)$, has six iron neighbours: the two body-centre atoms of the cells above and below, each a distance $a/2$ away, and the four corner atoms of the face, each $a/\sqrt2$ away. The nearer pair, at $a/2$, limits the size of the site. For a snug fit, the iron radius plus the interstitial radius equals $a/2$:

$$
R_{Fe}+r_i=\frac a2
$$

With $a=4R_{Fe}/\sqrt3$:

$$
r_i=\frac{2R_{Fe}}{\sqrt3}-R_{Fe}=R_{Fe}\left(\frac{2}{\sqrt3}-1\right)=0.1547R_{Fe}
$$

For $R_{Fe}=0.12$ nm, $a=0.2771$ nm and

$$
r_i=0.0186\ \mathrm{nm},\qquad\boxed{2r_i=0.037\ \mathrm{nm}}
$$

A carbon atom has $r_C=0.08$ nm, more than four times the radius of the site (diameter 0.16 nm against 0.037 nm). It does not fit: each carbon atom forces the iron atoms around it apart and badly strains the lattice. So very little carbon can dissolve in ferrite, only 0.022 wt% at most ([[FEEG1002 C7 - Steels and Precipitation Hardening#1. The phases of steel|C7]]), and the carbon that does dissolve is drawn to the stretched region below an edge dislocation, where it pins the dislocation and gives the upper and lower yield points of steel.

## Sources

- `Tutorial Sheet 01 - Crystal Structures, Planes and Directions.pdf`: Q1–Q9. No solutions are provided; all answers here were worked independently and checked numerically. The Q7 sketches are drawn with the usual convention of moving the origin to keep each direction and plane inside one cell.
