---
title: "FEEG1002 C2 - Crystal Structures and Crystallography"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part C: Materials"
order: 17
tags: [feeg1002, materials, crystallography, fcc, bcc, hcp, miller-indices, polymorphism]
aliases: ["Materials Lecture 2", "Crystal structures, planes and directions", "Crystallography"]
date: 2026-11-05
status: lectured
coverage: "Materials L2 (14 Oct 2024, ll. 1–783): crystalline and amorphous solids, the unit cell, close-packed stacking (HCP, FCC), BCC, polymorphism of Fe, Sn and ZrO2, a TEM lattice-spacing case study, Miller indices of directions and planes in cubic cells, a past exam MCQ and a preview of slip systems; slide deck 03 in full. Atoms per cell, a(R) and APF were left to Tutorial Sheet 1 and are derived here."
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: ["[[FEEG1002 C1 - Atoms and Bonding]]"]
next_topics: ["[[FEEG1002 C3 - Diffusion]]"]
key_concepts: ["[[Crystal Structures and Atomic Packing Factor]]", "[[Miller Indices for Planes and Directions]]"]
tutorial_sheets: ["[[FEEG1002 Materials Tutorial 1 - Crystal Structures and Diffusion Solutions]]"]
sources: ["02 - Sources/Materials/Lectures/Lecture 03 - Crystals and Crystallography.pdf", "02 - Sources/Lectures/FEEG1002 Lecture 2 - Materials Crystal sand crsytallography Monday 1.txt", "02 - Sources/Materials/Tutorials/Tutorial Sheet 01 - Crystal Structures, Planes and Directions.pdf"]
---

# FEEG1002 C2 - Crystal Structures and Crystallography

> [!abstract] Summary
> Most metals and ceramics are crystalline: their atoms sit on a regular three-dimensional lattice built by repeating a small unit cell. Stacking close-packed layers of hard spheres in the sequence ABAB gives hexagonal close-packed (HCP) and ABCABC gives face-centred cubic (FCC), both filling 74 % of space; body-centred cubic (BCC) has close-packed directions but no close-packed planes and fills 68 %. Some materials change structure with temperature (polymorphism), with a change of volume. Miller indices name directions $[uvw]$ and planes $(hkl)$ in a cubic cell, and they are needed to describe the slip planes on which metals deform.

> [!summary]- Exam use: quick path
> - **Use it when:** you must identify FCC, BCC or HCP and its stacking, find atoms per cell, the lattice parameter $a$ in terms of the atomic radius $R$, or the atomic packing factor, predict the volume change of a polymorphic transformation, or read the Miller indices of a direction or plane from a sketch.
> - **Assumptions:** hard-sphere atoms of fixed radius that touch along the close-packed direction; cubic unit cells for Miller indices (HCP needs a four-index system, not covered).
> - **Method:** 1. Count atoms per cell: corner $\tfrac18$, face $\tfrac12$, body centre 1. 2. Find where atoms touch: face diagonal $a\sqrt2=4R$ (FCC), body diagonal $a\sqrt3=4R$ (BCC). 3. APF = (atoms × $\tfrac43\pi R^3$)/$a^3$. 4. Direction: (end − start)/$a$, cleared to integers, in $[\ ]$. 5. Plane: intercepts in units of $a$, reciprocals, integers, in $(\ )$; move the origin if the plane passes through it.
> - **Common mistakes:** for a direction, using the plane rule (reciprocals) or forgetting to move the origin to the tail of the arrow; comparing volumes per unit cell instead of per atom when a material changes structure.
> - **Practise:** [[#Worked example - the past exam question]] · [[FEEG1002 Materials Tutorial 1 - Crystal Structures and Diffusion Solutions]] Q3–Q7

Atoms in a solid want to sit at the spacing $r_0$ where their bond energy is lowest ([[FEEG1002 C1 - Atoms and Bonding|C1]]). In most solids the way to give every atom that comfortable spacing is to arrange them in a regular, repeating pattern: a crystal. Some solids never get organised, and stay **amorphous** (glasses, many polymers, and even some metals cooled very fast), but metals and ceramics are normally crystalline, and the particular arrangement matters a great deal.

A very small change in structure changes the behaviour. When layers of balls are stacked as tightly as possible, the third layer can go in one of two places. One choice gives hexagonal close packing, found in magnesium and titanium alloys, which are relatively hard to deform; the other gives face-centred cubic, found in aluminium, copper and austenitic steels, which are soft and ductile. The difference is the number and orientation of the close-packed planes on which layers of atoms can slide, and Miller indices name those planes.

A crystal structure is also not fixed. Iron is BCC at room temperature and FCC above about 910 °C, and the change of packing changes its volume: a hot iron wire visibly shortens as it passes through the transformation. Polymorphism of this kind returns with the phase diagrams of steel in [[FEEG1002 C7 - Steels and Precipitation Hardening|C7]].

---

## 1. Crystals and the unit cell

A **crystalline** solid has its atoms arranged in a regularly ordered, repeating three-dimensional lattice. A non-crystalline or **amorphous** solid has no such long-range order. The **crystal structure** is the particular spatial arrangement of the atoms. The **unit cell** is the smallest group of atoms that shows the whole pattern, so that the crystal can be built by repeating it in three directions, in the same way that a wall of patterned tiles needs a few tiles before the repeat becomes visible. For cubic cells the edge length is the **lattice parameter** $a$.

The atoms are treated as hard spheres that touch their nearest neighbours. Three unit cells cover most metals: face-centred cubic (FCC), body-centred cubic (BCC) and hexagonal close-packed (HCP).

![[m2_unit_cells.png|900]]

## 2. Building solids by stacking close-packed layers

### The close-packed layer

Identical balls pushed together in a tray settle into a layer in which each ball touches six others, arranged hexagonally. This is a **close-packed plane**, the densest possible arrangement of spheres in a plane. The positions of the balls in this first layer are the A sites. The layer leaves two sets of hollows between the balls, each hollow sitting over three balls: the B sites and C sites.

The second layer drops into one set of hollows, say the B sites. It cannot use both sets at once, because neighbouring B and C hollows are too close together for two balls. The second layer in turn leaves hollows over the A sites and over the C sites, and the third layer has a choice.

![[m2_stacking.png|900]]

### HCP: ABAB stacking

If the third layer goes directly above the first, in the A sites, the sequence is ABABAB. Its smallest repeating unit is the **hexagonal close-packed** cell, with close-packed planes at the top (A), the middle (B) and the bottom (A) of the hexagonal prism. These are the only close-packed planes in the cell, and they are all parallel, which limits how the structure can deform. Magnesium alloys and titanium alloys are HCP.

### FCC: ABCABC stacking

If the third layer goes into the C sites, over neither of the first two, the sequence is ABCABC. Tilt the stack and its smallest repeating unit is a cube with an atom at each corner and one at the centre of each face: **face-centred cubic**. The close-packed layers now run diagonally through the cube, as the $\{111\}$ planes. Because the cube is highly symmetrical, there are close-packed planes in four different orientations, and wherever the load is applied some of them are well placed to slip. Aluminium, copper, nickel and austenitic iron are FCC.

### BCC: not close-packed

The **body-centred cubic** cell has an atom at each corner and one at the centre of the cube. Its atoms cannot be laid out in a close-packed layer: the densest plane in BCC, $\{110\}$, has gaps. The atoms touch only along the body diagonals of the cube, so BCC has **close-packed directions** but no close-packed planes. Ferritic iron and steel, chromium and tungsten are BCC. Being able to recognise all three structures and their stacking, and that BCC is the one that is not close-packed, is required.

## 3. Counting atoms and packing

### Atoms per unit cell

An atom on a corner of a cube is shared by the eight cubes that meet there, so only $\tfrac18$ of it belongs to any one cell. An atom on a face is shared by two cells ($\tfrac12$ each), and an atom in the body of the cell belongs to it entirely. For a cubic cell with $N_c$ corner, $N_f$ face and $N_i$ interior atoms,

$$
n=\tfrac18N_c+\tfrac12N_f+N_i
$$

For FCC, eight corners and six faces:

$$
n_{FCC}=8\times\tfrac18+6\times\tfrac12=1+3=4
$$

For BCC, eight corners and one body centre:

$$
n_{BCC}=8\times\tfrac18+1=2
$$

BCC has half as many atoms per cell as FCC (Tutorial Sheet 1, Q4). The conventional HCP prism holds 6 atoms: 12 corners shared by six cells, 2 face centres shared by two, and 3 inside, $12\times\tfrac16+2\times\tfrac12+3=6$.

### Lattice parameter in terms of the atomic radius

The hard spheres touch along the close-packed direction, and that fixes $a$ in terms of the atomic radius $R$.

In FCC the atoms touch along a face diagonal: a corner atom, the face-centre atom and the opposite corner atom lie in a line. The diagonal therefore spans $R+2R+R=4R$. By Pythagoras on a face of side $a$, the face diagonal is $\sqrt{a^2+a^2}=a\sqrt2$, so

$$
a\sqrt2=4R
$$

$$
a_{FCC}=\frac{4R}{\sqrt2}=2\sqrt2\,R
$$

In BCC the atoms touch along a body diagonal: corner, body centre, opposite corner, again $4R$. The body diagonal of a cube is $\sqrt{a^2+a^2+a^2}=a\sqrt3$, so

$$
a\sqrt3=4R
$$

$$
a_{BCC}=\frac{4R}{\sqrt3}
$$

This is Tutorial Sheet 1, Q3.

![[m2_apf_geometry.png|900]]

### Atomic packing factor

The **atomic packing factor** is the fraction of the unit-cell volume occupied by atoms:

$$
\mathrm{APF}=\frac{\text{volume of atoms in the cell}}{\text{volume of the cell}}=\frac{n\cdot\tfrac43\pi R^3}{a^3}
$$

For FCC, with $n=4$ and $a=2\sqrt2R$:

$$
\mathrm{APF}_{FCC}=\frac{4\cdot\tfrac43\pi R^3}{(2\sqrt2R)^3}
$$

$$
\mathrm{APF}_{FCC}=\frac{\tfrac{16}{3}\pi R^3}{16\sqrt2\,R^3}
$$

$$
\mathrm{APF}_{FCC}=\frac{\pi}{3\sqrt2}=0.740
$$

For BCC, with $n=2$ and $a=4R/\sqrt3$:

$$
\mathrm{APF}_{BCC}=\frac{2\cdot\tfrac43\pi R^3}{(4R/\sqrt3)^3}
$$

$$
\mathrm{APF}_{BCC}=\frac{\tfrac83\pi R^3}{64R^3/(3\sqrt3)}
$$

$$
\mathrm{APF}_{BCC}=\frac{8\pi\cdot3\sqrt3}{3\cdot64}=\frac{\pi\sqrt3}{8}=0.680
$$

FCC (and HCP, which is built from the same close-packed layers) has the highest packing factor possible for equal spheres, 0.74. BCC, with no close-packed planes, leaves more empty space, 32 % against 26 %. This is Tutorial Sheet 1, Q5.

| Structure | Stacking | Atoms per cell | $a$ in terms of $R$ | APF | Examples |
|---|---|---:|---|---:|---|
| FCC | ABCABC | 4 | $2\sqrt2R$ | 0.74 | Al, Cu, Ni, austenite |
| BCC | not close-packed | 2 | $4R/\sqrt3$ | 0.68 | ferrite, Cr, W |
| HCP | ABAB | 6 | – | 0.74 | Mg, Ti |

> [!tip] Compare per atom, not per cell
> When a material changes structure the number of atoms does not change, but the number of unit cells does: four atoms make one FCC cell but two BCC cells. To find a volume change, compare the volume per atom, $a^3/n$, never the volume of one cell of each.

## 4. Polymorphism

**Polymorphism** (called **allotropy** for a pure element) is the ability of a material to exist in more than one crystal structure.

Iron is BCC (ferrite) at room temperature, changes to FCC (austenite) at about 910 °C, and returns to BCC at about 1395 °C before it melts; the first temperature moves with carbon content. Because FCC is close-packed and BCC is not, the iron contracts as it becomes FCC. A taut iron wire heated with a blowtorch tightens as it passes 910 °C, then slackens again on cooling.

Tin changes from body-centred tetragonal (white tin) to a diamond-like cubic structure (grey tin) when it cools below 13.2 °C, with a 27 % increase in volume. The expansion crumbles the metal ("tin pest"), which destroyed tin organ pipes in cold churches; the story that it destroyed the buttons of Napoleon's army in Russia has little evidence behind it.

Zirconia ceramics exploit a transformation on purpose. Zirconia stabilised in its tetragonal form transforms to the monoclinic form when the high stress at a crack tip triggers it; the monoclinic cell is larger, so the transformation squeezes the crack shut and raises the fracture toughness. This **transformation toughening** gives zirconias better toughness than most ceramics ([[FEEG1002 C11 - Ceramics and Composites|C11]]).

Crystal structure can also be measured directly. In a transmission electron microscope individual columns of atoms in a 10 nm chromium oxide particle from a worn hip replacement show as rows of dots, and their spacing, 0.266 nm, identifies the compound.

## 5. Miller indices

Plastic deformation happens by atoms slipping over each other on particular planes and in particular directions, so the planes and directions in a crystal need names. In a cubic cell they are given **Miller indices**, worked out relative to a corner of the cell taken as the origin, with axes $x$, $y$, $z$ along the cube edges and lengths measured in units of $a$. HCP needs a fourth axis and is not covered.

### Directions

A **direction** is a vector. To index it:

1. Choose the origin at the tail of the arrow (moving it if necessary).
2. Find where the arrow leaves the unit cell and write the coordinates of that point relative to the origin.
3. Divide by $a$ and clear any fractions to the smallest integers.
4. Write the result in square brackets, $[uvw]$, with $x$ first, and put a bar over any negative index.

An arrow from the origin to the point $(a,a,0)$ has components $1,1,0$, so it is $[110]$. From the origin to $(0,a,a)$ it is $[011]$, and to $(a,0,a)$ it is $[101]$. An arrow that goes $-a$ in $x$ and $+a$ in $y$ is $[\bar110]$. A direction index of 2 means travelling two cell lengths, out into the neighbouring cell.

![[m2_miller_directions.png|900]]

Because the cube is symmetrical, $[110]$, $[011]$, $[101]$ and the other face diagonals are all equivalent. Together they form a **family** of directions, written in angle brackets: $\langle110\rangle$.

### Planes

A **plane** is indexed from where it cuts the axes, not from where it leaves the cell:

1. Choose an origin that does not lie in the plane (move it to another corner if the plane passes through the origin).
2. Find the intercepts of the plane on the $x$, $y$ and $z$ axes in units of $a$; a plane parallel to an axis has intercept $\infty$.
3. Take the reciprocals ($1/\infty=0$).
4. Clear fractions to integers and write them in round brackets, $(hkl)$.

Plane A cuts $y$ at $a$ and is parallel to $x$ and $z$. Its intercepts are $\infty,1,\infty$, the reciprocals $0,1,0$, and the plane is $(010)$. All six cube faces are equivalent and form the family $\{100\}$, written with curly braces. Plane B is parallel to $(010)$ but cuts $y$ halfway across the cell, at $a/2$: intercepts $\infty,\tfrac12,\infty$, reciprocals $0,2,0$, plane $(020)$. A plane one third of the way across is $(030)$. For planes, fractional intercepts give the larger indices.

![[m2_miller_planes.png|900]]

> [!warning] Directions use end points, planes use reciprocals
> The two procedures look alike and are easily mixed up. A direction index of 2 sends the arrow into the next cell; a plane index of 2 puts the plane halfway across this cell. The brackets carry the meaning too: $[uvw]$ a direction, $\langle uvw\rangle$ a family of directions, $(hkl)$ a plane, $\{hkl\}$ a family of planes.

In a cubic crystal, the direction $[hkl]$ is perpendicular to the plane $(hkl)$ with the same indices. The plane $(hkl)$ with intercepts $1/h$, $1/k$, $1/l$ satisfies $hx+ky+lz=1$, and the normal to the plane $hx+ky+lz=\text{const}$ is the vector $(h,k,l)$. This is the relationship asked for in Tutorial Sheet 1, Q7. It holds only for cubic cells, where the three axes are at right angles and the same length.

### Close-packed planes and slip systems

The planes and directions that matter most are the close-packed ones. In FCC the close-packed planes are $\{111\}$, each containing three close-packed $\langle110\rangle$ directions; with four distinct $\{111\}$ planes that gives $4\times3=12$ **slip systems**. In BCC the densest planes are $\{110\}$, each with two close-packed $\langle111\rangle$ directions, again 12 systems but on planes that are not close-packed. That is why FCC metals such as aluminium are soft and ductile whatever the direction of loading ([[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation#Slip systems|C4]]).

---

## Worked examples

### Worked example - the past exam question

A past MCQ shows a cubic cell with a shaded plane that cuts the $x$ axis at $a$ and the $y$ axis at $a$ and runs parallel to $z$. Direction D1 runs along the plane from the point $(a,0,0)$ to the point $(0,a,0)$; direction D2 runs straight up, parallel to $z$. Identify the plane and the two directions.

The plane has intercepts $1,1,\infty$. The reciprocals are $1,1,0$, so the plane is $(110)$.

For D1, move the origin to the tail of the arrow at $(a,0,0)$. The head is at $(0,a,0)$, so the components are

$$
(0-a,\ a-0,\ 0-0)=(-a,\ a,\ 0)
$$

and dividing by $a$ gives $-1,1,0$: D1 is $[\bar110]$. D2 has components $(0,0,a)$, so it is $[001]$. The step that solves the question is moving the origin to the tail of each arrow.

> [!check] Both directions lie in the plane
> A direction $[uvw]$ lies in the plane $(hkl)$ when $hu+kv+lw=0$, because it is then perpendicular to the plane normal $[hkl]$. For D1, $1\times(-1)+1\times1+0\times0=0$; for D2, $1\times0+1\times0+0\times1=0$. Both lie in $(110)$, as the sketch shows.

### Worked example - the shrinking iron wire

Estimate the change in volume when iron transforms from BCC to FCC at about 910 °C, assuming the atomic radius stays the same.

Work per atom. For BCC, $a=4R/\sqrt3$ and two atoms share the cell:

$$
v_{BCC}=\frac{(4R/\sqrt3)^3}{2}=\frac{64R^3}{2\times3\sqrt3}=6.158R^3
$$

For FCC, $a=2\sqrt2R$ and four atoms share the cell:

$$
v_{FCC}=\frac{(2\sqrt2R)^3}{4}=\frac{16\sqrt2R^3}{4}=5.657R^3
$$

The fractional change on going from BCC to FCC is

$$
\frac{\Delta V}{V}=\frac{v_{FCC}-v_{BCC}}{v_{BCC}}=\frac{5.657-6.158}{6.158}=-0.081
$$

an 8.1 % contraction, or about 2.8 % in length. The ratio of the two volumes is just the ratio of the packing factors, $0.680/0.740$.

> [!check] What the hard-sphere model leaves out
> Measured lattice parameters of iron at 912 °C are about 0.290 nm for BCC and 0.365 nm for FCC, giving 0.01225 and 0.01213 nm³ per atom: a real contraction of about 1 %, not 8 %. The atoms are not quite hard spheres of fixed size; the apparent radius grows from 0.126 nm to 0.129 nm when each atom gains four more nearest neighbours in FCC. The direction of the change, a contraction, is right, which is what the wire shows. Tutorial Sheet 1, Q6 asks the same question for calcium going from FCC to BCC, where the answer is an 8.9 % expansion.

---

## Links

- Parent: [[FEEG1002 Mechanics, Materials and Structures Hub]] · Previous: [[FEEG1002 C1 - Atoms and Bonding]] · Next: [[FEEG1002 C3 - Diffusion]]
- Concepts: [[Crystal Structures and Atomic Packing Factor]] · [[Miller Indices for Planes and Directions]] · [[Dislocations and Slip Systems]]
- Worked sheet: [[FEEG1002 Materials Tutorial 1 - Crystal Structures and Diffusion Solutions]] (Q1–Q7) · Formula list: [[FEEG1002 Formula Sheet]]
- Used again in: [[FEEG1002 C3 - Diffusion|C3]] (interstitial sites in BCC and FCC) · [[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation|C4]] (slip systems) · [[FEEG1002 C7 - Steels and Precipitation Hardening|C7]] (ferrite and austenite) · [[SESA2028 M6 - Light Alloys - Aluminium, Magnesium, Beryllium and Titanium]] (HCP titanium and magnesium alloys in Year 2)

## Sources

- `FEEG1002 Lecture 2 - Materials Crystal sand crsytallography Monday 1.txt` (L2, 14 Oct 2024): crystallinity and the unit cell (ll. 33–80), close-packed stacking, HCP and FCC (ll. 81–211), BCC (ll. 212–264), polymorphism of Fe, Sn and ZrO₂ (ll. 265–355), TEM case study (ll. 356–373), Miller indices of directions (ll. 399–550), of planes (ll. 551–649), the past exam MCQ (ll. 650–719), brackets (ll. 720–740), slip systems preview (ll. 741–770).
- `Lecture 03 - Crystals and Crystallography.pdf` (slide deck 03, "Lecture 2 Crystal structures, Planes and Directions"): stacking diagrams, polymorphism data (Fe 910 °C and 1395 °C, Sn 13.2 °C and 27 %), lattice-spacing case study, direction and plane examples, the exam question with three Vevox polls, slip systems. Figures after Callister.
- `Tutorial Sheet 01 - Crystal Structures, Planes and Directions.pdf`: Q1–Q7 on this note (Q8–Q9 belong to [[FEEG1002 C3 - Diffusion|C3]]).

## Self-study tasks

### Core

- [ ] Tutorial 1, Q1–Q2: sketch the FCC, BCC and HCP cells and label the stacking layers. → [[#2. Building solids by stacking close-packed layers]] · [[FEEG1002 Materials Tutorial 1 - Crystal Structures and Diffusion Solutions#Q1 and Q2 - Unit cells and stacking]]
- [ ] Tutorial 1, Q3–Q5: $a$ in terms of $R$ for BCC, atoms per cell, and the APF of FCC and BCC, left to the tutorial (L2, ll. 228–232). Targets $4R/\sqrt3$, 4 and 2, 0.74 and 0.68. → [[#3. Counting atoms and packing]]
- [ ] Tutorial 1, Q6: volume change of calcium going from FCC to BCC. Target +8.9 %. → [[#Worked example - the shrinking iron wire]] · [[FEEG1002 Materials Tutorial 1 - Crystal Structures and Diffusion Solutions#Q6 - Calcium changing from FCC to BCC]]
- [ ] Tutorial 1, Q7: draw $[101]$, $[1\bar10]$, $[2\bar12]$ and the planes with the same indices, and state their relationship. → [[#5. Miller indices]] · [[FEEG1002 Materials Tutorial 1 - Crystal Structures and Diffusion Solutions#Q7 - Directions and planes]]
- [ ] The past exam MCQ: identify the plane and directions D1 and D2 (L2, ll. 650–719). Targets $(110)$, $[\bar110]$, $[001]$. → [[#Worked example - the past exam question]]

### Further practice

- [ ] Index the in-lecture directions A to D and planes A and B from scratch, then check the bracket conventions (L2, ll. 426–649). → [[#Directions]] · [[#Planes]]
- [ ] Show that the volume change of a polymorphic transformation at constant $R$ equals the ratio of the packing factors (suggested, not lecturer-set). → [[#Worked example - the shrinking iron wire]]

## Transcript and slide slips

> [!warning] Transcript slips (L2, ll. 304–351)
> Where: [[#4. Polymorphism]].
>
> At ll. 304–306 the tin transformation is called "a massive temperature increase"; it is a volume increase of about 27 %, on cooling below 13.2 °C (as the slide says). At l. 330 the change is described as "going from the grey to the white"; on cooling, white tin becomes grey tin. At ll. 344–351 the zirconia transformation is described the wrong way round ("stop in monoclinic", then switch to "octagonal"): transformation toughening keeps zirconia in the metastable tetragonal form and the crack-tip stress turns it monoclinic, which expands.

> [!warning] Transcript slips (L2, ll. 756–761)
> Where: [[#Close-packed planes and slip systems]].
>
> BCC slip systems are said to "only exist at higher temperatures because we have these sort of changes". No change of crystal structure is involved: slip on the non-close-packed BCC planes needs more stress, and that stress falls as the temperature rises, which is why BCC metals become less ductile in the cold ([[FEEG1002 C8 - Fracture - Brittle, Ductile and Fracture Mechanics|C8]]).

> [!warning] Plane indices (020) and (030) (L2, ll. 612–649; slide "Crystal Planes 2")
> Where: [[#Planes]].
>
> The indices $(020)$ and $(030)$ are kept here for planes cutting $y$ at $a/2$ and $a/3$. Many textbooks, Callister among them, reduce Miller indices to the smallest integers, which would make both of these $(010)$, the same family of parallel planes. Both conventions appear in practice ($(020)$ is meaningful in diffraction as the set of planes spaced $a/2$ apart); the unreduced indices are kept for a plane drawn at a fractional intercept.
