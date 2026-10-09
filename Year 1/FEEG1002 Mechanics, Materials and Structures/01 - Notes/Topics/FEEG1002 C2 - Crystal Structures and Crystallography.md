---
title: "FEEG1002 C2 - Crystal Structures and Crystallography"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part C: Materials"
order: 17
tags: [feeg1002, materials, crystallography, fcc, bcc, hcp, miller-indices]
aliases: ["Materials Lecture 3", "FCC BCC HCP", "Crystal planes and directions"]
date: 2026-09-25
status: complete
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: ["[[FEEG1002 C1 - Atoms and Bonding]]"]
next_topics: ["[[FEEG1002 C3 - Diffusion]]"]
key_concepts: ["[[Crystal Structures and Atomic Packing Factor]]", "[[Miller Indices for Planes and Directions]]"]
tutorial_sheets: ["[[FEEG1002 Materials Tutorial 1 - Crystal Structures and Diffusion Solutions]]"]
sources: ["02 - Sources/Materials/Lectures/Lecture 03 - Crystals and Crystallography.pdf"]
---

# FEEG1002 C2 - Crystal Structures and Crystallography

> [!abstract] Summary
> Crystalline solids repeat a **unit cell**. The three metallic structures are FCC, BCC and HCP. FCC/HCP are close packed ($APF=0.74$); BCC is less densely packed ($APF=0.68$). Planes $(hkl)$ and directions $[uvw]$ provide the language for slip, diffusion, fracture and diffraction.

## Key Concepts
- [[Crystal Structures and Atomic Packing Factor]] · [[Miller Indices for Planes and Directions]]

---

## 1. Crystalline and amorphous solids
- A **crystal** has long-range periodic order; an **amorphous** solid has only local order.
- A lattice plus its atomic basis generates the crystal. The **unit cell** is the smallest repeating volume.
- Real engineering metals are normally polycrystalline: each grain is crystalline but neighbouring grains have different orientations.

## 2. Metallic unit cells

| Structure | Atoms per conventional cell | Contact relation | APF | Close packing / slip clue |
|---|---:|---|---:|---|
| FCC | $8(1/8)+6(1/2)=4$ | face diagonal: $a\sqrt2=4R$ | 0.740 | ABCABC; many close-packed $\{111\}\langle110\rangle$ systems |
| BCC | $8(1/8)+1=2$ | body diagonal: $a\sqrt3=4R$ | 0.680 | no close-packed plane; close-packed directions |
| HCP | 6 effective atoms in conventional cell | close packed | 0.740 | ABAB; fewer independent slip systems at low $T$ |

![[m2_crystal_structures.png|920]]

The atomic packing factor is

$$APF=\frac{\text{volume of atoms assigned to cell}}{\text{unit-cell volume}}$$

For FCC, $a=2\sqrt2R$ and $APF=\pi/(3\sqrt2)=0.740$. For BCC, $a=4R/\sqrt3$ and $APF=\pi\sqrt3/8=0.680$.

## 3. Stacking and polymorphism
- Close-packed layers can occupy A, B or C sites: HCP repeats **ABAB**, FCC repeats **ABCABC**.
- **Polymorphism/allotropy** means one material can adopt more than one crystal structure.
- Iron: $\alpha$-Fe (BCC) $\rightarrow$ $\gamma$-Fe (FCC) near 910°C $\rightarrow$ $\delta$-Fe (BCC) near 1395°C. This is central to [[FEEG1002 C7 - Steels and Precipitation Hardening]].
- Tin changes structure near 13.2°C with a large volume expansion (“tin pest”).

## 4. Directions
For a direction from one lattice point to another:
1. resolve the vector into lattice-coordinate components;
2. clear fractions to the smallest integers;
3. write $[uvw]$; place a bar over negative indices.

Examples: cube edge $[100]$, face diagonal $[110]$, body diagonal $[111]$. Symmetry-equivalent directions form $\langle uvw\rangle$.

## 5. Planes (Miller indices)
1. Find the plane intercepts with the $x,y,z$ axes in units of $a,b,c$.
2. Take reciprocals.
3. Clear fractions to the smallest integers.
4. Write $(hkl)$; an infinite intercept gives index 0.

- $(100)$ is a cube face; $(110)$ cuts $x$ and $y$ at one lattice spacing and is parallel to $z$.
- Parallel planes such as $(010)$ and $(020)$ have the same orientation but different spacing.
- A family of symmetry-equivalent planes is $\{hkl\}$.
- In a cubic crystal, the direction $[hkl]$ is normal to the plane $(hkl)$. Do not assume this for a general non-cubic lattice.

## 6. Why crystallography matters
- Slip follows favourable **planes and directions**, so crystal structure controls ductility and temperature sensitivity.
- X-ray diffraction identifies phases through interplanar spacings.
- Cleavage can prefer particular planes; diffusion and corrosion are often faster along grain boundaries.

> [!example] FCC-to-BCC volume change at fixed atomic radius
> Per-atom volumes are $V_{FCC}/4=4\sqrt2R^3$ and $V_{BCC}/2=32R^3/(3\sqrt3)$. Thus FCC $\rightarrow$ BCC expands by
>
> $$\frac{32/(3\sqrt3)}{4\sqrt2}-1=0.0887\approx8.9\%$$

> [!warning] Common traps
> - Count shared atoms: corner $1/8$, face $1/2$, body centre 1.
> - Direction indices come from vector components; plane indices come from reciprocal intercepts.
> - Packing factor compares occupied volume, not the number of atoms alone.

## Links
- Previous: [[FEEG1002 C1 - Atoms and Bonding]] · Next: [[FEEG1002 C3 - Diffusion]]
- Worked problems: [[FEEG1002 Materials Tutorial 1 - Crystal Structures and Diffusion Solutions]]

## Sources
- Materials Lecture 3; audited against [[FEEG1002 Materials L03 Contact Sheet.png]].

