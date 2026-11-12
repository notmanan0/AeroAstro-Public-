---
title: "FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part C: Materials"
order: 19
tags: [feeg1002, materials, tensile-test, youngs-modulus, yield-strength, dislocations, slip, solid-solution]
aliases: ["Materials Lectures 4 and 5", "Tensile properties", "Plastic deformation", "Dislocations and slip"]
date: 2026-11-05
status: lectured
coverage: "Materials L4 (21 Oct 2024, ll. 1–615): elastic and plastic deformation, engineering and true stress and strain, Young's modulus, Poisson's ratio, yield by the 0.2 % offset, upper and lower yield points, UTS and necking, design use and safety factors, ductility, resilience and toughness. Materials L5 (22 Oct 2024, ll. 1–696): point, line and volume defects, edge and screw dislocations, slip and slip systems in FCC, BCC and HCP, temperature dependence of yield, twinning, dislocation stress fields, alloying rules and solid-solution strengthening, carbon pinning. Slide decks 05 and 06 in full."
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: ["[[FEEG1002 C1 - Atoms and Bonding]]", "[[FEEG1002 C2 - Crystal Structures and Crystallography]]", "[[FEEG1002 A1 - Forces, Equilibrium, Stress and Strain]]"]
next_topics: ["[[FEEG1002 C5 - Strengthening Mechanisms and Annealing]]"]
key_concepts: ["[[Engineering Stress-Strain Properties]]", "[[Dislocations and Slip Systems]]", "[[Strengthening Mechanisms in Metals]]"]
tutorial_sheets: ["[[FEEG1002 Materials Tutorial 2 - Mechanical Properties and Strengthening Solutions]]"]
sources: ["02 - Sources/Materials/Lectures/Lecture 05 - Elastic and Plastic Mechanical Properties.pdf", "02 - Sources/Materials/Lectures/Lecture 06 - Plastic Deformation and Alloying.pdf", "02 - Sources/Lectures/FEEG1002 Lecture 4 - Materials Mechanical Properties 1.txt", "02 - Sources/Lectures/FEEG1002 Lecture 5 - Materials Plastic Deformation 1.txt", "02 - Sources/Materials/Tutorials/Tutorial Sheet 02 - Plastic Deformation-Mechanical Properties Strengthening.pdf"]
---

# FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation

> [!abstract] Summary
> A tensile test turns load and extension into a stress–strain curve, and from it come the properties every structural calculation needs: Young's modulus $E$ (the initial slope), Poisson's ratio, the yield strength (by the 0.2 % offset), the ultimate tensile strength, the ductility and the energy absorbed. Elastic deformation is the stretching of atomic bonds and is fully recovered; plastic deformation is permanent, and in a crystalline metal it happens by the movement of line defects called dislocations on particular slip planes and directions. Because FCC metals have many close-packed slip systems they are ductile and insensitive to temperature, while BCC and HCP metals become harder to deform in the cold. Anything that obstructs dislocations raises the yield strength, and dissolving solute atoms in the lattice (solid-solution strengthening) is the first way of doing it.

> [!summary]- Exam use: quick path
> - **Use it when:** you are given a load, dimensions and properties and asked for a stress, strain, extension or change of diameter; asked to read $E$, yield, UTS or ductility off a curve; or asked why a metal yields, why FCC differs from BCC and HCP, or how alloying strengthens.
> - **Assumptions:** engineering stress and strain (original dimensions); linear elasticity up to yield; uniaxial load; $z$ is the loading axis and $x$ lateral.
> - **Method:** 1. $\sigma=F/A_0$, $\varepsilon=\Delta L/L_0$. 2. Elastic: $\sigma=E\varepsilon$, $\varepsilon_x=-\nu\varepsilon_z$, $\Delta d=\varepsilon_xd_0$. 3. From a curve: $E$ = initial slope; yield where a line of slope $E$ from $\varepsilon=0.002$ cuts the curve; UTS at the maximum. 4. Unloading from a point on the curve is a line of slope $E$, so the permanent strain is $\varepsilon_{total}-\sigma/E$. 5. Design: working stress at most $\sigma_y/2$ (a third for high-consequence parts); never design to the UTS.
> - **Common mistakes:** using the total strain at fracture as the percentage elongation without removing the elastic part; forgetting that $\nu$ carries a minus sign, so a rod in tension gets thinner.
> - **Practise:** [[#Worked example - sizing a steel tie]] · [[FEEG1002 Materials Tutorial 2 - Mechanical Properties and Strengthening Solutions]] Q1–Q4

In statics a material is characterised by a Young's modulus and a yield stress ([[FEEG1002 A1 - Forces, Equilibrium, Stress and Strain|A1]]); the internal structure of the metal accounts for both. A metal bar stretched a little springs back, like an elastic band, because the bonds between its atoms have stretched without any atom changing its neighbours (L4, ll. 42–80). Stretched further, it stays deformed: atoms have moved permanently. The tensile test measures where that change happens and how the material behaves on either side of it.

Metals yield at stresses far below those that sliding one whole plane of atoms over another at once would need, which are hundreds of times larger than measured yield strengths. Crystals are full of defects, and one kind, the dislocation, lets a plane slip one row of atoms at a time, which takes far less effort (L5, ll. 169–211). The crystal structures of [[FEEG1002 C2 - Crystal Structures and Crystallography|C2]] set the available slip systems: dislocations glide most easily on close-packed planes in close-packed directions, and the number of such slip systems explains why aluminium is soft, why titanium is hard to machine, and why steel can turn brittle in the cold while aluminium does not.

If yielding is dislocations moving, then making a metal stronger means getting in their way. That idea underlies every strengthening mechanism; the first, alloying, is in [[#Solid-solution strengthening]] (L5, ll. 442–459).

---

## 1. Elastic deformation

Apply a load to a metal bar and remove it: if the bar returns exactly to its original length the deformation was **elastic**. At the atomic scale the bonds stretch but the atoms keep their positions relative to each other, and on unloading they return to their original spacing (slide "Elastic Deformation"). Elastic means reversible. The restoring force is the net bonding force of [[FEEG1002 C1 - Atoms and Bonding#Why the curve sets melting point and stiffness|C1]]: pulling atoms beyond $r_0$ is resisted by a growing net attraction, and that resistance is what a tensile test measures as the modulus (L4, ll. 52–80).

### Engineering stress and strain

In a tensile test a cylindrical specimen of original cross-sectional area $A_0$ and gauge length $L_0$ is pulled at each end by a force $F$. The **engineering stress** is the force divided by the original area,

$$
\sigma=\frac{F}{A_0}
$$

in N/m² (Pa), usually quoted in MPa. The **engineering strain** is the change in length divided by the original length,

$$
\varepsilon=\frac{L_i-L_0}{L_0}=\frac{\Delta L}{L_0}
$$

where $L_i$ is the instantaneous length. Strain is dimensionless and is often quoted as a percentage, $100\varepsilon$ (L4, ll. 81–114). Engineering values are what are almost always reported and used.

### True stress and strain

As a bar is stretched it also gets thinner (and in compression, fatter), but engineering stress keeps dividing by the original area. **True stress** divides by the instantaneous area $A_i$:

$$
\sigma_T=\frac{F}{A_i}
$$

and **true strain** adds up each small increment of length relative to the length at that moment:

$$
\varepsilon_T=\int_{L_0}^{L_i}\frac{dL}{L}=\ln\frac{L_i}{L_0}
$$

(slide "Stress and strain"; L4, ll. 115–142). Up to the start of necking the volume of a metal stays essentially constant during plastic flow, so $A_0L_0=A_iL_i$. Then

$$
A_i=A_0\frac{L_0}{L_i}=\frac{A_0}{1+\varepsilon}
$$

and the two kinds of stress and strain are related by

$$
\sigma_T=\frac{F}{A_0}(1+\varepsilon)=\sigma(1+\varepsilon)
$$

$$
\varepsilon_T=\ln(1+\varepsilon)
$$

For small strains the two are the same to within $\varepsilon$; the difference matters only at large plastic strains.

### Hooke's law and Young's modulus

For metals and ceramics the first part of the stress–strain curve is a straight line, because over the small range of stretch involved the bond force is proportional to the stretch. In this region stress is proportional to strain, **Hooke's law**:

$$
\sigma=E\varepsilon
$$

and the constant of proportionality $E$ is **Young's modulus**, also called the elastic modulus or stiffness. It is the gradient of the initial linear part of a tensile or compressive stress–strain curve (slide "Elastic Deformation"; L4, ll. 143–183). Exam questions expect the relations to be rearranged: given $E$ and a strain, find the stress; given the dimensions, go on to the force (L4, ll. 175–183).

Not every material is linear. Bone, which is viscoelastic, has a curved loading line from the start. For such materials a **tangent modulus** (the slope of the tangent at a chosen stress) or a **secant modulus** (the slope of the line from the origin to a chosen point) is reported instead. The deformation is still recovered, just not linearly (L4, ll. 184–216).

### Poisson's ratio

A rod pulled along its axis gets longer and thinner; pushed, it gets shorter and fatter. With $z$ the loading axis and $x$ (equivalently $y$, for a cylinder) the lateral direction, **Poisson's ratio** is the ratio of lateral to axial strain:

$$
\nu=-\frac{\varepsilon_x}{\varepsilon_z}=-\frac{\varepsilon_y}{\varepsilon_z}
$$

(slide "Elastic Deformation"; L4, ll. 217–249). The minus sign makes $\nu$ positive for ordinary materials, since a positive axial strain goes with a negative lateral one. Here $z$ is the loading axis, which differs from the convention in the Statics notes. **Auxetic** materials, usually specially designed foam-like or printed lattices, have a negative Poisson's ratio: they get fatter when pulled. They are of interest for impact protection, though they do not yet work well at impact strain rates.

### Typical values

The modulus follows the bonding ([[FEEG1002 C1 - Atoms and Bonding|C1]]): ceramics around $10^3$ GPa at the top, metals around $10^2$ GPa, and polymers around $10^1$ GPa or less, with elastomers lower still (slide "Elastic Property Ranges"; L4, ll. 250–298). Poisson's ratio is about 0.33 for metals, about 0.25 for ceramics and about 0.40 for polymers. A modulus that comes out as $10^5$ GPa means a slipped decimal place.

## 2. Plastic deformation and the tensile curve

At sufficiently high stress atoms slip past each other and the deformation becomes permanent: **plastic deformation** (slide "Plastic deformation"; L4, ll. 299–316). Load past this point and unload, and the bar springs back along a line parallel to the original elastic slope but does not return to zero strain. The strain that remains is the permanent set.

![[m4_stress_strain_curve.png|900]]

### Yield strength and the 0.2 % offset

The **yield strength** is the stress at which noticeable plastic deformation has occurred (slide "Yield Strength"). The departure from the straight line is gradual in most metals, so a standard amount of plastic strain is agreed: 0.2 %, a strain of 0.002. The procedure is (L4, ll. 317–362):

1. Convert the load–extension record to stress and strain using the specimen dimensions.
2. From $\varepsilon=0.002$ on the strain axis, draw a line with the same slope $E$ as the elastic loading line.
3. Where this line cuts the curve, read off the stress: that is the yield strength $\sigma_y$.

The value is also called the **0.2 % proof stress**. The standard dates from the days of graph paper, when judging where a curve left the straight line was a matter of eye; computers fit the line better now, but the 0.2 % figure remains the one reported (L4, ll. 321–347). "Yield stress" and "yield strength" mean the same thing: a strength is a stress.

### Upper and lower yield points

Some steels show a sharp yield instead. The stress rises to an **upper yield point**, drops suddenly to a **lower yield point**, and the bar then extends at a roughly constant stress before work hardening begins (slide "Yield Strength"; L4, ll. 363–384). The cause is small carbon atoms dissolved in the iron, which collect at dislocations and pin them; extra stress is needed to tear the dislocations free, and once they are moving they keep going at the lower stress ([[#Interstitial carbon and the yield point of steel]]). For design, use the lower yield point.

![[m4_yield_point.png|900]]

### Ultimate tensile strength and necking

The **ultimate tensile strength** (UTS) is the maximum engineering stress in the test, the highest point of the curve (slide "Ultimate Tensile Strength"; L4, ll. 385–418). Up to the UTS the specimen thins uniformly along its length. At the UTS deformation localises in one place, the **neck**, where the cross-section shrinks rapidly until the bar breaks. The engineering stress falls after the UTS, not because the material gets weaker but because the load the shrinking neck can carry falls while the stress is still being divided by the original area. True stress, based on the area of the neck, keeps rising to fracture.

### Ductility

**Ductility** is the amount of plastic deformation a material can undergo before it fails (slide "Ductility"; L4, ll. 533–550). It is expressed either as the **percentage elongation**,

$$
\%EL=\frac{L_f-L_0}{L_0}\times100
$$

where $L_f$ is the length after fracture (the pieces fitted back together, so the elastic strain has been recovered), or as the **percentage reduction in area**,

$$
\%RA=\frac{A_0-A_f}{A_0}\times100
$$

where $A_f$ is the area at the fracture. A material with less than 5 % elongation at failure is classed as **brittle**.

### Resilience and toughness

The area under a stress–strain curve is an energy per unit volume: stress (N/m²) times strain (dimensionless) is J/m³ (slide "Resilience and Toughness"; L4, ll. 551–596).

**Resilience** is the capacity of a material to absorb energy while it deforms elastically, and the **modulus of resilience** $U_r$ is the area under the curve up to yield. For a linear elastic material,

$$
U_r=\int_0^{\varepsilon_y}\sigma\,d\varepsilon=\int_0^{\varepsilon_y}E\varepsilon\,d\varepsilon
$$

$$
U_r=\frac12E\varepsilon_y^2
$$

and substituting $\varepsilon_y=\sigma_y/E$,

$$
\boxed{U_r=\frac{\sigma_y^2}{2E}}
$$

the area of the elastic triangle. A spring material wants a high yield strength and a low modulus.

**Toughness** is the ability of a material to absorb energy up to fracture, the whole area under the curve. A brittle material stores elastic energy, breaks, and gives the energy back as the broken ends recoil; a ductile material absorbs far more energy in plastic deformation before it fails. Toughness is not the same as **fracture toughness**, the resistance to the growth of a crack ([[FEEG1002 C8 - Fracture - Brittle, Ductile and Fracture Mechanics|C8]]).

![[m4_resilience_toughness.png|900]]

### Using the properties in design

Most structural assessments rest on $E$, $\sigma_y$ and the UTS (slide "Design Considerations"; L4, ll. 439–532). $E$ sets the elastic deflection under service loads, such as clearances in machinery, a ship's hull flexing over waves or the bending of an aircraft wing. The yield strength is the safety limit, because beyond it a part is permanently deformed. Service conditions never match the design case exactly, so a ductile part is designed with its working stress well below yield, normally at most half of it: a steel with a yield strength of 240 MPa would be designed never to see more than 120 MPa. Where failure would be catastrophic, such as a nuclear pressure vessel, the margin is larger, a third of the yield strength. The UTS is the ultimate limit, past which the structure collapses, and a ductile part is never designed to it. A brittle material has no yield point, only a UTS, so it is designed against the UTS, with a large margin. Stress concentrations, which raise the local stress above $F/A$, are in [[FEEG1002 C8 - Fracture - Brittle, Ductile and Fracture Mechanics#2. Stress concentrations|C8]].

## 3. Defects in crystals

Most solids are not single crystals, and most crystals are not perfect (slide "Defects in Solids"; L5, ll. 31–110). A piece of metal is **polycrystalline**: many crystals, or grains, packed together. Within each grain there are three classes of defect.

**Point defects** are disturbances at a single lattice site. A **vacancy** is a missing atom, left when a site is not filled as the crystal grows from the melt. A **self-interstitial** is a host atom squeezed into a place where it does not fit. Atoms of another element can also be dissolved directly into the crystal: as **interstitial atoms** in the gaps between the host atoms (carbon in iron) or as **substitutional atoms** replacing host atoms on lattice sites (chromium in iron). Dissolving atoms in this way is one form of alloying.

**Line defects** are **dislocations**, defects that run along a line through the crystal. They are the ones that make plastic deformation possible.

**Volume defects** include **grain boundaries** (the interfaces between differently oriented crystals), particle **inclusions** (second phases or contaminants with a different structure, acting as internal boundaries), and cracks, voids and porosity from processing or service.

Defects are what make metals deform as they do, and controlling them is how their behaviour is controlled.

## 4. Dislocations and slip

### Edge and screw dislocations

An **edge dislocation** is an extra half plane of atoms inserted into the crystal, ending part-way through it (slide "Line Defects: Dislocations"; L5, ll. 111–150). The line along which the half plane ends is the dislocation line, which runs straight through the crystal. Around it the lattice is distorted. The size and direction of that distortion is described by the **Burgers vector** $\mathbf b$: the step needed to close a circuit of atom-to-atom jumps drawn round the dislocation, which would close exactly in a perfect crystal. The larger the Burgers vector, the larger the stresses and strains in the crystal round the dislocation. For an edge dislocation $\mathbf b$ is perpendicular to the dislocation line.

A **screw dislocation** is a spiral defect, made by shearing one part of the crystal one atomic spacing relative to the other along a line, so that the atomic planes wind round the line like the thread of a screw. Its Burgers vector is parallel to the dislocation line (slide "Dislocation: Line Defects"; L5, ll. 151–168). Real dislocations are usually mixtures of the two. Dislocations are present in any crystal, and plastic deformation creates more of them.

### Slip

Under a shear stress above the elastic limit, the extra half plane of an edge dislocation does not need to move far. The bonds of the row of atoms just below the end of the half plane break and re-form with the half plane, which becomes complete, while the neighbouring plane is left as the new extra half plane. The dislocation has moved one atomic spacing. Repeat this, one row at a time, and the dislocation glides right across the crystal and out of the side, leaving a step one Burgers vector high, about 0.2 nm, on the surface: a **unit step of slip** (slide "Plastic deformation: Dislocation Motion"; L5, ll. 169–211). This motion of dislocations is **slip**.

![[m4_edge_dislocation_slip.png|900]]

One step of 0.2 nm is tiny, but a bar contains enormous numbers of dislocations, and the macroscopic plastic strain is the sum of all their steps. The reason metals deform this way is energy. Slip by a dislocation breaks and re-forms the bonds of one row of atoms at a time; slipping a perfect plane would mean breaking every bond across it at once, which needs far more energy. A rucked carpet is moved more easily by pushing the ruck along it than by dragging the whole carpet.

### Slip systems

Dislocations do not glide on any plane in any direction. They move most easily on the most densely packed planes, in the most densely packed directions within them, because there the atoms have the shortest distance to move between comfortable positions (L5, ll. 212–267). A slip plane together with a slip direction in it is a **slip system** (L5, ll. 371–375).

FCC metals slip on the close-packed $\{111\}$ planes in the close-packed $\langle110\rangle$ directions. There are four distinct $\{111\}$ planes, each containing three $\langle110\rangle$ directions, so FCC has $4\times3=12$ slip systems, and because the cube is so symmetrical these are spread in every orientation (slide "Dislocations and Mechanical Properties"). Whatever the direction of the applied stress, some slip system is close to well aligned with it. This is why FCC metals such as aluminium and copper are soft and ductile.

BCC metals have no close-packed planes. They slip on the densest planes available, $\{110\}$, in the close-packed $\langle111\rangle$ directions, but on planes that are not close-packed the atoms have further to move and slip needs a higher stress. HCP metals have close-packed planes, but only one set of them, the parallel basal planes, so they have few easy slip systems; much of their slip has to happen on other, non-close-packed planes. HCP metals such as titanium and magnesium alloys are therefore less ductile than iron, copper or aluminium, which is one reason titanium machines badly (L5, ll. 379–397).

Evidence for all this can be seen directly. Electron backscatter diffraction (EBSD) maps show each grain of a polycrystal as the same FCC cube rotated to a different orientation. Scratch the surface with a fine diamond tip and, in grains where a slip system is well aligned, slip steps appear beside the scratch along the traces of the $\{111\}$ planes; in badly oriented grains the material is just pushed aside. Thin foils in a transmission electron microscope (TEM) show the dislocations themselves (L5, ll. 268–319).

### Temperature and the yield stress

The number of slip systems also decides how the yield stress changes with temperature (slide "Effect of Temperature on Yield Stress"; L5, ll. 398–437).

FCC metals (copper) have a yield stress that is nearly independent of temperature, because slip on close-packed planes is easy whatever the temperature, until close to melting.

BCC metals (iron) have a yield stress that rises steeply as the temperature falls. With no close-packed planes, slip has to be helped along by thermal vibration (it is thermally activated), so in the cold it becomes difficult.

HCP metals (magnesium) are also temperature-dependent, because their limited close-packed systems force much of the slip onto non-close-packed planes.

This matters for cryogenic, polar and space applications. Liquid-nitrogen carriers are made of aluminium rather than steel: dropped or knocked, the FCC aluminium deforms, while BCC steel at −196 °C would shatter (L5, ll. 258–264). The same contrast reappears as the ductile-to-brittle transition in [[FEEG1002 C8 - Fracture - Brittle, Ductile and Fracture Mechanics#5. The ductile-to-brittle transition|C8]].

![[m4_yield_temperature.png|900]]

### Twinning

**Mechanical twinning** is a second way for a crystal to deform plastically (slide "Mechanical Twinning"; L5, ll. 320–370). Above a certain stress a block of the crystal shears homogeneously so that it becomes a mirror image of the untwinned crystal across a plane, the twin plane. Atoms move by less than one spacing each and no bonds are broken; the repositioning produces the strain. The stress for twinning is generally higher, and less sensitive to temperature, than the stress for slip, and twinning occurs in BCC and HCP metals at low temperatures but rarely in FCC metals. It is sudden and energetic: bending a bar of tin produces an audible crackle, the "tin cry", as the twins form. In cobalt-chromium-molybdenum alloys twinning takes over once slip has been exhausted by tangled dislocations.

## 5. Stopping dislocations

The yield point is the point at which dislocation motion starts. To raise the yield strength, stop the dislocations moving (slide "Increasing the yield strength"; L5, ll. 442–459).

### The stress field of an edge dislocation

The extra half plane crowds the atoms above the slip plane together, so the region round the end of the half plane, on its side, is in **compression**. Below the slip plane, where the half plane is missing, the bonds are stretched and the lattice is in **tension** (L5, ll. 460–497). A dislocation therefore carries a region of compression and a region of tension with it as it moves. Anything else in the crystal that has its own stress field (a solute atom, another dislocation, a particle) interacts with these fields, and that interaction is what strengthening mechanisms use.

![[m4_dislocation_stress_field.png|900]]

### Alloying and solid solutions

**Alloying** is adding atoms of other elements to a metal: carbon to iron gives steel; chromium and carbon to iron give stainless steel; silicon, magnesium, copper or zinc are added to aluminium (L5, ll. 498–513). The major element is the **solvent** and the added element the **solute**. If the solute atoms dissolve into the crystal of the solvent, on substitutional or interstitial sites, the result is a **solid solution**: one solid dissolved in another.

A solute dissolves well substitutionally when four conditions are met (slide "Alloying: Solid Solutions"; L5, ll. 514–556):

1. Atomic size: the radii differ by less than about 15 %.
2. Crystal structure: solvent and solute have the same structure.
3. Electronegativity: similar, otherwise the elements tend to react to form a compound instead.
4. Valency: a metal dissolves more readily in a metal of higher valency than in one of lower valency.

### Solid-solution strengthening

Even within the 15 % rule, a solute atom is a different size from the host atoms, so it distorts the lattice around it (L5, ll. 557–616). A smaller substitutional atom pulls its neighbours in, putting the surrounding lattice in tension; a larger one pushes them out, putting it in compression. A solute atom near a dislocation can relieve part of the dislocation's strain: a small solute atom fits comfortably in the compressed region above the slip plane, and a large one in the stretched region below it (slide "Alloying: Solid Solution Strengthening"). Solute atoms therefore gather where they relieve the dislocation's strain field, and to move the dislocation away from them, or past other solute atoms whose fields add to its own, needs extra stress. The lattice distortions scattered through the alloy impede dislocation motion and raise the yield strength. This is **solid-solution strengthening**.

### Interstitial carbon and the yield point of steel

Carbon in iron is an interstitial solute, and it does not fit: the interstitial sites in BCC iron are far smaller than a carbon atom (Tutorial Sheet 1, Q9), so each carbon atom strains the iron around it heavily (slide "Steel: Interstitial Solution Strengthening"; L5, ll. 617–670). The one place with spare room is the tension region just below the extra half plane of an edge dislocation, so carbon atoms diffuse there, which relieves their strain and pins the dislocation in place. To start the dislocation moving, extra stress is needed to pull it away from its carbon atmosphere: that is the upper yield point. Once free, the dislocations keep moving at a lower stress, the lower yield point, and the bar extends along a plateau at roughly constant stress. This is the origin of the curve in [[#Upper and lower yield points]] and Tutorial Sheet 2, Q4.

---

## Worked examples

### Worked example - sizing a steel tie

A steel tie rod 1.2 m long must carry a tensile load of 8 kN. The steel has $\sigma_y=240$ MPa, $E=207$ GPa and $\nu=0.30$. Using the design rule of a working stress no more than half the yield strength, choose a diameter, then find the stress, the extension and the change in diameter.

The allowable stress is

$$
\sigma_{allow}=\frac{\sigma_y}{2}=\frac{240}{2}=120\ \mathrm{MPa}
$$

so the minimum area is

$$
A_{min}=\frac{F}{\sigma_{allow}}=\frac{8000}{120\times10^6}=6.67\times10^{-5}\ \mathrm{m^2}=66.7\ \mathrm{mm^2}
$$

and the minimum diameter

$$
d_{min}=\sqrt{\frac{4A_{min}}{\pi}}=\sqrt{\frac{4\times66.7}{\pi}}=9.21\ \mathrm{mm}
$$

Take $d=10$ mm. Then $A_0=\pi\times10^2/4=78.5$ mm² and

$$
\sigma=\frac{8000}{78.5\times10^{-6}}=101.9\ \mathrm{MPa}
$$

$$
\varepsilon_z=\frac{\sigma}{E}=\frac{101.9\times10^6}{207\times10^9}=4.92\times10^{-4}
$$

$$
\Delta L=\varepsilon_zL_0=4.92\times10^{-4}\times1200=0.59\ \mathrm{mm}
$$

The lateral strain is

$$
\varepsilon_x=-\nu\varepsilon_z=-0.30\times4.92\times10^{-4}=-1.48\times10^{-4}
$$

$$
\Delta d=\varepsilon_xd_0=-1.48\times10^{-4}\times10=-1.48\times10^{-3}\ \mathrm{mm}
$$

The rod lengthens by 0.59 mm and its diameter shrinks by about 1.5 µm. The actual safety factor on yield is $240/101.9=2.36$.

> [!check] Stay elastic
> The calculation used $\sigma=E\varepsilon$, which holds only below yield. At 101.9 MPa the rod is well inside the elastic range, so the extension is fully recovered when the load comes off. With a 6 mm rod the stress would be 283 MPa, above yield, and the elastic formulas would no longer give the extension.

### Worked example - resilience of steel and an aluminium alloy

Compare the modulus of resilience of a steel ($\sigma_y=240$ MPa, $E=207$ GPa) with that of an aluminium alloy ($\sigma_y=276$ MPa, $E=69$ GPa).

$$
U_{r,steel}=\frac{\sigma_y^2}{2E}=\frac{(240\times10^6)^2}{2\times207\times10^9}=1.39\times10^5\ \mathrm{J/m^3}
$$

$$
U_{r,Al}=\frac{(276\times10^6)^2}{2\times69\times10^9}=5.52\times10^5\ \mathrm{J/m^3}
$$

The aluminium alloy stores four times as much elastic energy per unit volume before yielding, even though its yield strength is only 15 % higher, because its lower modulus lets it stretch three times as far ($\varepsilon_y=0.0040$ against 0.0012).

### Worked example - true stress at the UTS

An aluminium specimen of diameter 12.8 mm (Tutorial Sheet 2, Q2) reaches its UTS of 369 MPa at an engineering strain of 0.087, before necking. Find the maximum load, the true stress and the true strain at that point.

$$
A_0=\frac{\pi\times12.8^2}{4}=128.7\ \mathrm{mm^2}
$$

$$
F_{max}=\sigma_{UTS}A_0=369\times128.7=47.4\ \mathrm{kN}
$$

Up to the UTS the deformation is uniform and the volume constant, so

$$
\sigma_T=\sigma(1+\varepsilon)=369\times1.087=401\ \mathrm{MPa}
$$

$$
\varepsilon_T=\ln(1+\varepsilon)=\ln1.087=0.083
$$

The true stress is 9 % above the engineering value because the area has shrunk to $128.7/1.087=118.4$ mm².

---

## Links

- Parent: [[FEEG1002 Mechanics, Materials and Structures Hub]] · Previous: [[FEEG1002 C3 - Diffusion]] · Next: [[FEEG1002 C5 - Strengthening Mechanisms and Annealing]]
- Concepts: [[Engineering Stress-Strain Properties]] · [[Dislocations and Slip Systems]] · [[Strengthening Mechanisms in Metals]] · [[Stress, Strain and Young's Modulus]]
- Worked sheet: [[FEEG1002 Materials Tutorial 2 - Mechanical Properties and Strengthening Solutions]] (Q1–Q4) · Formula list: [[FEEG1002 Formula Sheet]]
- Statics: [[FEEG1002 A1 - Forces, Equilibrium, Stress and Strain]] (stress, strain, Hooke's law) · [[FEEG1002 B3 - Generalised Hooke's Law]] (Poisson's ratio in two and three dimensions) · [[FEEG1002 B6 - Yield Criteria]] (yield under combined stress)
- Year 2: [[SESA2028 M6 - Light Alloys - Aluminium, Magnesium, Beryllium and Titanium]] (FCC aluminium against HCP titanium and magnesium)

## Sources

- `FEEG1002 Lecture 4 - Materials Mechanical Properties 1.txt` (L4, 21 Oct 2024): elastic deformation (ll. 42–80), engineering and true stress and strain (ll. 81–142), Hooke's law and non-linear elasticity (ll. 143–216), Poisson's ratio and auxetics (ll. 217–249), property ranges (ll. 250–298), plastic deformation and the 0.2 % offset (ll. 299–362), upper and lower yield (ll. 363–384), UTS and necking (ll. 385–438), design and safety factors (ll. 439–532), ductility (ll. 533–550), energy, resilience and toughness (ll. 551–596).
- `FEEG1002 Lecture 5 - Materials Plastic Deformation 1.txt` (L5, 22 Oct 2024): defects (ll. 31–110), dislocations and the Burgers vector (ll. 111–168), slip (ll. 169–211), slip systems and evidence (ll. 212–319), twinning (ll. 320–370), slip systems and temperature (ll. 371–441), stopping dislocations (ll. 442–459), stress field (ll. 460–497), alloying rules (ll. 498–556), solid-solution strengthening (ll. 557–616), carbon pinning (ll. 617–670).
- `Lecture 05 - Elastic and Plastic Mechanical Properties.pdf` (slide deck 05) and `Lecture 06 - Plastic Deformation and Alloying.pdf` (slide deck 06). Figures after Callister.
- `Tutorial Sheet 02 - Plastic Deformation-Mechanical Properties Strengthening.pdf`: Q1–Q4 on this note (Q5–Q7 belong to [[FEEG1002 C5 - Strengthening Mechanisms and Annealing|C5]]).

## Self-study tasks

### Core

- [ ] Tutorial 2, Q1: elongation and change of diameter of a copper rod at 276 MPa, the rearrangement exercise flagged at L4, ll. 175–184. Targets 0.765 mm and −8.5 µm. → [[#Worked example - sizing a steel tie]] · [[FEEG1002 Materials Tutorial 2 - Mechanical Properties and Strengthening Solutions#Q1 - Elastic deformation of a copper rod]]
- [ ] Tutorial 2, Q2: read $E$, the 0.2 % proof stress, UTS, elongation, maximum load and the permanent set after loading to 340 MPa from the aluminium curve. → [[#Yield strength and the 0.2 % offset]] · [[FEEG1002 Materials Tutorial 2 - Mechanical Properties and Strengthening Solutions#Q2 - Properties from the aluminium tensile curve]]
- [ ] Tutorial 2, Q3: why solute atoms, other dislocations, grain boundaries and precipitates hinder dislocations. → [[#5. Stopping dislocations]] · [[FEEG1002 Materials Tutorial 2 - Mechanical Properties and Strengthening Solutions#Q3 - Obstacles to dislocation motion]]
- [ ] Tutorial 2, Q4: why steel shows upper and lower yield points. → [[#Interstitial carbon and the yield point of steel]] · [[FEEG1002 Materials Tutorial 2 - Mechanical Properties and Strengthening Solutions#Q4 - Upper and lower yield points in steel]]

### Further practice

- [ ] Explain, using slip systems, why an FCC metal stays ductile in liquid nitrogen while a BCC steel does not, the demonstration planned for the second-semester lab (L5, ll. 258–264, 411–425). → [[#Temperature and the yield stress]]
- [ ] Derive $U_r=\sigma_y^2/2E$ and $\sigma_T=\sigma(1+\varepsilon)$ (suggested, not lecturer-set). → [[#Resilience and toughness]] · [[#True stress and strain]]

## Transcript and slide slips

> [!warning] Transcript slips (L4, ll. 230, 285 and 375–377)
> Where: [[#Poisson's ratio]] · [[#Upper and lower yield points]].
>
> Poisson's ratio is described as "the ratio between the lateral and the axial strains" without the minus sign; the slide has $\nu=-\varepsilon_x/\varepsilon_z$. Polymers are said to "expand more", meaning they have higher Poisson's ratios (they contract more sideways when stretched). At ll. 375–377 the upper yield point is where the dislocations "get moving" and the lower one where they "actually start moving"; the upper yield point is the stress to free the pinned dislocations, and the lower yield point the lower stress at which they keep moving.

> [!warning] Transcript slips (L5, ll. 162–164, 244, 404–405 and 419)
> Where: [[#Edge and screw dislocations]] · [[#Temperature and the yield stress]].
>
> The Burgers vector of a screw dislocation is first said to be "parallel to it rather than not parallel to it", a muddled sentence: it is parallel to the line for a screw dislocation and perpendicular for an edge. BCC slip is said to involve "a slight diffusional process" (also on the slide, "an element of diffusion in the atom movement"); slip is thermally activated, but no diffusion is involved in dislocation glide. FCC yield is called "temperature independent"; it is nearly so, with no ductile-to-brittle transition. At l. 419 the BCC yield stress "will increase … with temperature"; it increases as the temperature falls, as the lines around it make clear.

> [!warning] Transcript slip (L5, ll. 568–586)
> Where: [[#Solid-solution strengthening]].
>
> A smaller substitutional atom is said to put "a compressive stress" round it and a larger one "a tensile stress field". In the convention of the slides (Callister's), a smaller solute atom puts the surrounding lattice in tension and sits in the compressed region of a dislocation, while a larger one puts its surroundings in compression and sits in the tensile region. The strengthening argument, that like stress fields interact and impede the dislocation, is unaffected.

> [!warning] Slide slip (slide deck 05, "Design Considerations")
> Where: [[#Using the properties in design]].
>
> The slide gives "a safety factor of 20–400 % used". The lecture's working rule is a factor of 2 on yield (working stress at most half of $\sigma_y$), and 3 for high-consequence parts (L4, ll. 493–513).
