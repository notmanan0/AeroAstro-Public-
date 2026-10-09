---
title: "FEEG1002 Materials Tutorial 1 - Crystal Structures and Diffusion Solutions"
module: "FEEG1002 Mechanics, Materials and Structures"
type: tutorial
stream: "Part C: Materials"
tags: [feeg1002, tutorial-solutions, materials, crystallography, diffusion]
sheet: "Materials Tutorial Sheet 1"
theory_notes: ["[[FEEG1002 C2 - Crystal Structures and Crystallography]]", "[[FEEG1002 C3 - Diffusion]]"]
key_concepts: ["[[Crystal Structures and Atomic Packing Factor]]", "[[Miller Indices for Planes and Directions]]", "[[Fick's Laws and Arrhenius Diffusion]]"]
status: complete
sources: ["02 - Sources/Materials/Tutorials/Tutorial Sheet 01 - Crystal Structures, Planes and Directions.pdf"]
---

# FEEG1002 Materials Tutorial 1 - Crystal Structures and Diffusion Solutions

> [!abstract] Sheet Info
> Nine questions covering FCC/BCC/HCP cells, packing, Miller indices, diffusion and carbon interstitials. The sheet prints no answers; results below were derived and checked numerically.

## Theory Links
- [[FEEG1002 C2 - Crystal Structures and Crystallography]] · [[FEEG1002 C3 - Diffusion]]

---

## Q1: Sketch FCC, BCC and HCP
- **FCC**: atoms at 8 corners and 6 face centres.
- **BCC**: atoms at 8 corners plus one body centre.
- **HCP**: hexagonal prism with ABAB close-packed layers; conventional cell has atoms on the two hexagonal faces and a three-atom mid-plane.

![[m2_crystal_structures.png|900]]

Effective atom counts: FCC 4, BCC 2, conventional HCP 6.

## Q2: Packing layers
- FCC: **ABCABC...** stacking.
- HCP: **ABAB...** stacking.

Both have the maximum equal-sphere packing fraction 0.740; the different stacking sequence changes symmetry and slip-system availability.

## Q3: BCC unit-cell edge in terms of $R$
Atoms touch along the body diagonal. The diagonal spans corner radius + body-centre diameter + corner radius $=4R$:

$$a\sqrt3=4R\quad\Rightarrow\quad\boxed{a=\frac{4R}{\sqrt3}}$$

## Q4: Atoms per unit cell
- FCC: $8(1/8)+6(1/2)=\boxed4$.
- BCC: $8(1/8)+1=\boxed2$.

## Q5: Atomic packing factor
### FCC
Atoms touch on a face diagonal: $a\sqrt2=4R$, so $a=2\sqrt2R$.

$$APF_{FCC}=\frac{4(4\pi R^3/3)}{(2\sqrt2R)^3}=\boxed{\frac{\pi}{3\sqrt2}=0.740}$$

### BCC

$$APF_{BCC}=\frac{2(4\pi R^3/3)}{(4R/\sqrt3)^3}=\boxed{\frac{\pi\sqrt3}{8}=0.680}$$

FCC is higher because it is close packed; BCC contains more interstitial volume.

## Q6: Calcium FCC $\rightarrow$ BCC at $R=0.1969$ nm
Compare equal numbers of atoms, not equal numbers of cells.

$$v_{atom,FCC}=\frac{(2\sqrt2R)^3}{4}=4\sqrt2R^3$$

$$v_{atom,BCC}=\frac{(4R/\sqrt3)^3}{2}=\frac{32}{3\sqrt3}R^3$$

$$\frac{\Delta V}{V}=\frac{32/(3\sqrt3)}{4\sqrt2}-1=0.08866$$

So the transformation causes a **volume expansion of $\boxed{8.87\%}$** if the atomic radius is unchanged. (Density falls by $1-1/1.08866=8.14\%$.)

## Q7: Directions and planes

| Indices | Direction construction | Plane intercepts (one convenient translated member) |
|---|---|---|
| $[101]$, $(101)$ | one $+x$, zero $y$, one $+z$ | $x=a$, $y=\infty$, $z=a$ |
| $[1\bar10]$, $(1\bar10)$ | one $+x$, one $-y$, zero $z$ | $x=a$, $y=-a$, $z=\infty$ |
| $[2\bar12]$, $(2\bar12)$ | two $+x$, one $-y$, two $+z$; scale to fit cell | $x=a/2$, $y=-a$, $z=a/2$ |

In a **cubic** crystal, direction $[hkl]$ is normal to plane $(hkl)$. Negative intercepts can be drawn using a parallel translated plane inside/near the cell.

## Q8: Diffusion

### (a) H through steel or Si through Al?
Hydrogen through steel is much faster. H is very small and moves interstitially through many available sites; Si in Al is substitutional and normally requires a vacancy plus a larger atomic rearrangement.

### (b) Does doubling carburising temperature double carbon concentration at depth?
No. The coefficient follows

$$D=D_0e^{-Q/RT}$$

and the profile follows Fick's second law, with penetration distance scaling roughly as $\sqrt{Dt}$. Temperature must be in kelvin and the dependence is exponential, so the change is not linear and will normally be far greater than a factor of two over a large temperature increase.

## Q9: Carbon in a BCC face-centre interstitial
For BCC iron,

$$a=\frac{4R_{Fe}}{\sqrt3}=\frac{4(0.12)}{\sqrt3}=0.2771\ \text{nm}$$

The limiting nearest neighbours are the two body-centred Fe atoms on either side of the face centre, separated by $a/2$ from the interstitial centre:

$$R_{Fe}+r_i=\frac a2$$

$$r_i=\frac{2R_{Fe}}{\sqrt3}-R_{Fe}=0.01856\ \text{nm}$$

Thus the available site diameter is

$$\boxed{2r_i=0.0371\ \text{nm}}$$

Carbon has $r_C=0.08$ nm, far larger than $r_i$. It severely distorts the BCC lattice, so equilibrium carbon solubility in ferrite is low. The distortion also interacts strongly with dislocations, producing interstitial solid-solution strengthening and yield-point behaviour.

## Sources
- Materials Tutorial Sheet 1. Answers derived from the supplied geometry and cross-checked against Lectures 3–4.

