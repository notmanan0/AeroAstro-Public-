---
title: "FEEG1002 C1 - Atoms and Bonding"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part C: Materials"
order: 16
tags: [feeg1002, materials, atoms, bonding, valence, material-properties]
aliases: ["Materials Lectures 1 and 2", "Atomic bonding", "Atoms, Bonding and the Origins of Material Properties"]
date: 2026-11-05
status: lectured
coverage: "Materials L1 (11 Oct 2024, ll. 1–1081): course structure, electron shells, the periodic table and valence, EDX microanalysis, the bond force and energy curve, ionic, covalent, metallic and secondary bonding, and the properties of metals, polymers and ceramics traced to their bonding; slide decks 01 and 02 in full"
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: []
next_topics: ["[[FEEG1002 C2 - Crystal Structures and Crystallography]]"]
key_concepts: ["[[Atomic Bonding and Interatomic Potential]]"]
tutorial_sheets: []
sources: ["02 - Sources/Materials/Lectures/Lecture 01 - Introduction, Atoms and Bonding.pdf", "02 - Sources/Materials/Lectures/Lecture 02 - Atoms and Bonding.pdf", "02 - Sources/Lectures/FEEG1002 Lecture 2024-10-11.txt"]
---

# FEEG1002 C1 - Atoms and Bonding

> [!abstract] Summary
> The properties a designer looks up in a database (modulus, melting point, conductivity, ductility, corrosion resistance) start at the scale of atoms and the bonds between them. Two atoms attract at long range and repel at short range, and the two forces balance at an equilibrium spacing $r_0$ where the net energy has a minimum $-E_0$; $E_0$ is the bonding energy. A deeper well means a higher melting temperature, and a steeper force curve at $r_0$ means a higher Young's modulus. The three primary bonds (ionic, covalent, metallic) and the weak secondary bonds (van der Waals, hydrogen) explain most of the differences between metals, ceramics and polymers.

> [!summary]- Exam use: quick path
> - **Use it when:** a question asks which bond type a material has, why one material has a higher melting point or modulus than another, or why metals conduct and bend while ceramics insulate and shatter.
> - **Assumptions:** the two-atom picture (net force $F_N=F_A+F_R$, net energy $E_N=E_A+E_R$); the trends compare bonds of the same kind of material, not exact predictions.
> - **Method:** 1. Identify the bond from the elements: metal + non-metal is ionic, non-metal + non-metal is covalent, metal + metal is metallic, and the forces between molecules or polymer chains are secondary. 2. Rank by bonding energy $E_0$. 3. Higher $E_0$ means higher melting point and (generally) higher modulus. 4. Bound electrons mean an insulator; delocalised electrons mean a conductor. 5. Bonds that let atoms slide past each other mean ductility; bonds that do not mean brittleness.
> - **Common mistakes:** saying covalent bonding transfers electrons (it shares them; transfer is ionic); taking the net **force** at $r_0$ as the bond strength, when it is zero there and the bonding energy is the depth of the energy well.
> - **Practise:** [[#Worked example - reading the bonding energy table]] · [[#Self-study tasks]]

What happens to a component in service is decided by what its atoms are doing. When a wing spar flexes, the bonds between its atoms stretch slightly and spring back. When it bends permanently, atoms (or rather defects in the arrangement of atoms) have moved to new positions. When a turbine blade creeps, atoms diffuse. Choosing the right material, and later processing it to get the properties wanted, needs that picture (L1, ll. 348–362).

The starting point is the atom itself and its outer electrons, because they decide how an atom bonds to its neighbours. Atoms bond to reach a stable, full outer shell. They can do this by handing electrons over (ionic), by sharing them between neighbours (covalent), or by giving them up to a common pool shared by the whole solid (metallic). The type of bond then explains a long list of properties at once: a sea of free electrons makes a metal conduct electricity and heat and lets its atoms slide over one another, while electrons locked into ionic or covalent bonds make a ceramic an insulator that is hard but cannot deform plastically.

The size of the bond matters as well as its type. Pulling two atoms apart takes energy; that energy, the bonding energy, sets how much heat is needed to melt the solid, and the steepness of the force between the atoms near their equilibrium spacing sets how stiff the solid is. These two links are the first places where an atomic-scale quantity turns into an engineering property.

---

## 1. Atoms and electron shells

An atom is a small, dense nucleus of protons (positive) and neutrons (no charge), surrounded by electrons. The electrons are not scattered at random. They occupy energy levels, or shells, each made of sub-shells: the first level holds two electrons (1s); the second holds two in 2s and six in 2p, eight in all; the third level starts again with 3s and 3p (L1, ll. 376–411). Electrons in outer shells have higher energy than those in inner shells.

The **atomic number** $Z$ is the number of protons in the nucleus. It is what distinguishes one element from another, and in a neutral atom it also equals the number of electrons. The **atomic weight** printed on a periodic-table tile is not a whole number, because an element is a mixture of **isotopes** (atoms with the same number of protons but different numbers of neutrons), and the tabulated value is the weighted average of the isotope masses in their natural abundance. Isotope ratios differ between sources of an element, which is why they can be used forensically, for example to tell natural from industrial lead (L1, ll. 438–458). The electrons contribute almost nothing to the mass.

### Electron configurations used in this part

Writing out configurations shows how many electrons an atom has spare or needs:

| Element | $Z$ | Configuration | Outer shell |
|---|---:|---|---|
| H | 1 | 1s¹ | one electron, needs two for a full 1s |
| C | 6 | 1s² 2s² 2p² | four outer electrons, needs eight |
| Na | 11 | 1s² 2s² 2p⁶ 3s¹ | one spare electron |
| Cl | 17 | 1s² 2s² 2p⁶ 3s² 3p⁵ | needs one more to fill 3p |

### The periodic table and valence

The periodic table is ordered by electron configuration, so its layout is a map of reactivity. Down the far left (lithium, sodium) each atom has a single outer electron that is easily given away, so these elements are very reactive. The second column has two outer electrons. On the far right, the noble gases (helium, neon, argon) have full shells and are very unreactive; just before them, oxygen needs two electrons and chlorine one, so they readily take electrons (L1, ll. 459–532, 616–629). Elements from opposite sides react strongly with each other, and reactivity falls towards the middle of the table. This count of electrons available for bonding, the **valence**, is what decides which bond forms.

### Electron shells as a fingerprint: EDX

The shell structure has a direct use in materials analysis. In a scanning electron microscope the primary beam can knock an electron out of an inner shell of an atom in the specimen. An electron from a higher-energy outer shell drops into the vacancy and releases the energy difference as an X-ray. Because the shell energies are different for every element, the X-ray energy identifies the element (L1, ll. 554–574). Mapping X-ray counts across the surface gives element maps. Two examples: corrosion debris from a cobalt-chrome hip replacement on a titanium stem turned out to be mostly chromium with phosphorus (chromium ions released by corrosion had reacted with phosphate from the body), and the oxide around a crack in a nickel superalloy from the hot end of a jet engine showed where the chromium, cobalt and aluminium had gone (L1, ll. 575–611). The technique is **energy-dispersive X-ray spectroscopy (EDX)**. It identifies which elements are present; it says nothing directly about how they are bonded or arranged.

## 2. The bond force and energy curve

### Two atoms brought together

Between two isolated atoms brought closer, two kinds of force act (L1, ll. 650–693). At long range the outer electrons of each atom are attracted to the positive nucleus of the other: an **attractive force** $F_A$, whose origin depends on the type of bond. At short range the electron clouds overlap and repel strongly: a **repulsive force** $F_R$, which rises very steeply as the atoms are pushed together. The net force is the sum,

$$
F_N=F_A+F_R
$$

The sign convention is Callister's: attraction is plotted positive and repulsion negative. Far apart, attraction wins and pulls the atoms together; very close, repulsion wins and pushes them apart. In between there is one spacing where they balance:

$$
F_A+F_R=0\quad\text{at}\quad r=r_0
$$

$r_0$ is the **equilibrium spacing**, about 0.3 nm for most atoms. If the atoms are pulled slightly apart the net force is attractive, pulling them back; if they are pushed slightly together it is repulsive, pushing them back. The equilibrium is stable, which is why a solid has a definite size.

![[m1_bond_force_energy.png|900]]

### From force to energy

Energy and force are linked by work. With this sign convention (attraction positive), the potential energy of the pair at separation $r$ is the work needed to bring the atoms in from infinity, where the energy is zero:

$$
E_N(r)=\int_\infty^rF_N\,dr
$$

so, differentiating,

$$
F_N=\frac{dE_N}{dr}
$$

and the energy splits in the same way as the force, $E_N=E_A+E_R$, with the attractive energy $E_A$ negative and the repulsive energy $E_R$ positive. At $r_0$ the force is zero, so $dE_N/dr=0$ there: the equilibrium spacing is the bottom of a well in the energy curve. The depth of the well is the **bonding energy** $E_0$, the energy that must be supplied to separate the two atoms completely (slide "Why? Atomic Bonding"):

$$
E_N(r_0)=-E_0
$$

The net force at $r_0$ is zero, so the force does not measure how strongly the atoms are bonded. It is the energy minimum, $E_0$, that does (L1, ll. 694–711).

### Why the curve sets melting point and stiffness

Two engineering properties can be read off the curve.

Melting separates atoms from their fixed neighbours, so the energy needed to melt a solid scales with the depth of the well. A larger $E_0$ means a higher melting temperature (L1, ll. 899–908).

Stiffness is the resistance of the bonds to a small stretch. For a small stretch $x=r-r_0$ of the pair from equilibrium, expanding the force about $r_0$, where $F_N(r_0)=0$, gives:

$$
F_N(r_0+x)\approx F_N(r_0)+\left.\frac{dF_N}{dr}\right|_{r_0}x
$$

$$
F_N(r_0+x)\approx\left.\frac{dF_N}{dr}\right|_{r_0}x
$$

The bond behaves as a linear spring of stiffness

$$
S_0=\left.\frac{dF_N}{dr}\right|_{r_0}=\left.\frac{d^2E_N}{dr^2}\right|_{r_0}
$$

the slope of the force curve, or the curvature of the energy curve, at $r_0$. (The restoring force is attractive when $x>0$, which is positive in this convention, so $S_0>0$.) Over a solid, each atom is treated as occupying a cube of side $r_0$, so one bond carries the load on an area $r_0^2$ and stretches over a length $r_0$. A force $F$ per bond gives a stress

$$
\sigma=\frac{F}{r_0^2}
$$

and an extension $x$ gives a strain

$$
\varepsilon=\frac{x}{r_0}
$$

Divide the two and use $F=S_0x$:

$$
E=\frac{\sigma}{\varepsilon}=\frac{S_0x/r_0^2}{x/r_0}
$$

$$
\boxed{E\approx\frac{S_0}{r_0}}
$$

Young's modulus is the bond stiffness divided by the atomic spacing. Elastic deformation is the stretching of these springs, which is why it is fully recovered when the load is removed. Plastic deformation is different in kind: atoms move to new neighbours (L1, ll. 712–737; [[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation|C4]]).

### Linking well depth to stiffness

A deep well is usually also a narrow, steep-sided one, so strong bonds give stiff solids. A simple model shows why. Many bonds are described by an energy of the form

$$
E_N(r)=-\frac{A}{r^m}+\frac{B}{r^n},\qquad n>m
$$

where the first term is the attraction and the second the short-range repulsion (for an ionic bond $m=1$, the Coulomb attraction, and $n$ is about 8). At equilibrium the slope is zero:

$$
\left.\frac{dE_N}{dr}\right|_{r_0}=\frac{mA}{r_0^{m+1}}-\frac{nB}{r_0^{n+1}}=0
$$

$$
B=\frac{m}{n}Ar_0^{\,n-m}
$$

Substitute into the energy at $r_0$:

$$
E_N(r_0)=-\frac{A}{r_0^m}+\frac{m}{n}\frac{A}{r_0^m}
$$

$$
E_0=-E_N(r_0)=\frac{A}{r_0^m}\left(1-\frac mn\right)=\frac{A(n-m)}{n\,r_0^m}
$$

Differentiate the energy twice and evaluate at $r_0$:

$$
\left.\frac{d^2E_N}{dr^2}\right|_{r_0}=-\frac{m(m+1)A}{r_0^{m+2}}+\frac{n(n+1)B}{r_0^{n+2}}
$$

$$
S_0=\frac{A}{r_0^{m+2}}\left[-m(m+1)+n(n+1)\frac mn\right]
$$

$$
S_0=\frac{A\,m(n-m)}{r_0^{m+2}}
$$

Using $A(n-m)/r_0^m=nE_0$ from the line above:

$$
S_0=\frac{mn\,E_0}{r_0^2}
$$

and with $E\approx S_0/r_0$,

$$
\boxed{E\approx\frac{mn\,E_0}{r_0^3}}
$$

For bonds of the same form, the modulus scales with the bonding energy divided by the cube of the spacing. Bonding energy, melting temperature and Young's modulus therefore rise together across the bond types tabulated below.

![[m1_well_depth_stiffness.png|900]]

## 3. Primary bonds

Atoms bond so as to reach full, stable outer shells. There are three classical ways of doing it (slide "Primary Bonding"; L1, ll. 738–758).

### Ionic bonding

In an **ionic bond** electrons are transferred from one atom to another, creating charged ions that attract each other electrostatically (Coulombic attraction). Sodium has one electron too many (3s¹) and chlorine one too few (3p⁵). Sodium gives its 3s electron to chlorine, leaving Na⁺ and Cl⁻, both with full shells, and the oppositely charged ions hold together (L1, ll. 759–791). The transferred electrons stay bound to the chlorine; they are not free to move through the solid. Ionic bonds form between elements from opposite sides of the periodic table, a metal and a non-metal, and they are strong: 640 kJ/mol for NaCl and 1000 kJ/mol for MgO. Many ceramics are compounds of this kind; others are covalent or mixed.

### Covalent bonding

In a **covalent bond** electrons are shared between neighbouring atoms and stay firmly localised between them. Methane is the standard example (L1, ll. 799–821). Carbon (1s² 2s² 2p²) has four outer electrons and needs eight; hydrogen (1s¹) has one and needs two. No atom will give up four electrons, so instead carbon shares one electron pair with each of four hydrogens: each hydrogen then has a share in two electrons and the carbon a share in eight. Because the shared electrons sit in particular places, covalent bonds are directional, and parts of a molecule can carry a slight charge. Covalent bonds range from modest to extremely strong: diamond, a three-dimensional covalent network of carbon, has a bonding energy of 713 kJ/mol, melts above 3550 °C and has a modulus above 1000 GPa (L1, ll. 912–935).

### Metallic bonding

In a **metallic bond** the outer (valence) electrons leave their atoms and are shared by the whole solid, delocalised over large distances. What remains is an array of positive ion cores in a "sea" of valence electrons that holds them together (L1, ll. 823–839). Because no electron belongs to a particular pair of atoms, the bond is non-directional, and an atom can move to a new set of neighbours without breaking the bonding. That single fact underlies the ductility, the conductivity and the alloying behaviour of metals.

## 4. Secondary bonding

**Secondary bonds** are much weaker attractions that exist between atoms or molecules which already have full shells (slide "Secondary Bonding"; L1, ll. 840–888). They arise from dipoles: separations of positive and negative charge.

A **fluctuating dipole** appears because the electron cloud of an atom is not evenly spread at every instant. The cloud is momentarily lopsided, so one side of the atom is slightly negative and the other slightly positive, and this induces an opposite dipole in a neighbour. The resulting attraction is a **van der Waals** force. It is what holds argon together as a solid at −189 °C.

A **permanent dipole** exists in a polar molecule, where the bonding electrons sit closer to one atom than the other; in HCl the hydrogen end is slightly positive. Polar molecules attract each other and induce dipoles in their neighbours. The strongest secondary bond is the **hydrogen bond**, between a hydrogen atom bonded to a strongly electronegative atom (O, N, F) and a neighbouring molecule, as in water.

Secondary bonds matter most in polymers. A polymer chain has a strong covalent backbone, but the chains are held to each other only by van der Waals forces. When a polymer deforms, chains slide past one another, so it is the weak secondary bonds, not the strong backbone, that control its stiffness, strength and softening temperature (L1, ll. 876–888). The same applies in [[FEEG1002 C10 - Polymers - Structure and Mechanics|C10]].

## 5. Bonding energy and properties

Bonding energies, melting temperatures and moduli for each type of bond (slide "Bonding Energy Influence"):

| Bonding type | Substance | Bonding energy (kJ/mol) | Melting temperature (°C) | Young's modulus (GPa) |
|---|---|---:|---:|---:|
| Ionic | NaCl | 640 | 801 | 39.98 |
| Ionic | MgO | 1000 | 2800 | 249 |
| Covalent | Si | 450 | 1410 | 179 |
| Covalent | C (diamond) | 713 | >3550 | 1050–1210 |
| Metallic | Hg | 68 | −39 | – |
| Metallic | Al | 324 | 660 | 68 |
| Metallic | Fe | 406 | 1538 | 204–212 |
| Metallic | W | 849 | 3410 | 340 |
| Van der Waals | Ar | 7.7 | −189 | – |
| Van der Waals | Cl₂ | 31 | −101 | – |
| Hydrogen | NH₃ | 35 | −78 | – |
| Hydrogen | H₂O | 51 | 0 | – |

Within each class, a stronger bond gives a higher melting temperature and a higher modulus: mercury, aluminium, iron and tungsten differ in melting point and stiffness purely because their bonding energies differ (L1, ll. 936–945). Secondary bonds are so weak that most such substances are liquids or gases at room temperature, so a modulus has no meaning for them (L1, ll. 946–950).

![[m1_bond_energy_melting.png|900]]

The trend is strong but not exact. Silicon and iron have similar bonding energies (450 and 406 kJ/mol) but iron melts about 130 °C higher, and tungsten has a lower modulus than diamond despite a higher bonding energy. The bonding energy per mole does not settle it alone; the spacing $r_0$ and the number of bonds each atom makes (set by the crystal structure, [[FEEG1002 C2 - Crystal Structures and Crystallography|C2]]) matter too, as $E\approx mnE_0/r_0^3$ already suggests.

## 6. Bonding explains the three material classes

The same bond types explain the familiar properties of the three main classes of engineering material (slides "Properties of Metals", "Properties of Polymers", "Properties of Ceramics"; L1, ll. 951–1037).

Metals are held by metallic bonds. The sea of free electrons carries charge and heat, so metals are good electrical and thermal conductors, and it reflects light, so they are shiny. The non-directional bond allows atoms (more precisely, dislocations, [[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation|C4]]) to move, so metals are ductile and can be worked into shape. Their melting points vary with bond strength, from mercury to tungsten. Because every metal atom bonds the same way, metals mix readily to form alloys, and some (iron, nickel, cobalt) are magnetic.

Polymers have strong covalent bonds along their chains but only van der Waals and hydrogen bonds between chains. The electrons are bound in covalent bonds, so polymers are electrical and thermal insulators. Long, tangled molecules pack loosely, so polymers have low density. Because the bonds between chains are weak, polymers have low melting points, low strength and high flexibility.

Ceramics are held by ionic or covalent bonds, or a mixture. With electrons bound, they are insulators. Their strong bonds give high melting points and make them hard, difficult to deform even elastically. The same bonds stop atoms moving, so ceramics cannot deform plastically: they are brittle, and when they fail they fail suddenly (L1, ll. 1010–1023). Many ceramics are already oxides (alumina is aluminium oxide, zirconia is zirconium oxide), and corrosion of a metal is essentially its oxidation, so ceramics have excellent resistance to their environment (L1, ll. 1028–1036).

> [!tip] Reading a property chart
> Material-selection charts (Granta EduPack) plot one property against another. On a chart of Young's modulus against electrical resistivity, ceramics sit at high modulus and high resistivity, metals at high modulus and low resistivity, and polymers at low modulus and high resistivity. On tensile strength against fracture toughness, metals are both strong and tough, ceramics strong but with low toughness, and polymers lower in both (L1, ll. 1038–1074). Each cluster is the bonding showing through.

---

## Worked examples

### Worked example - reading the bonding energy table

Express the bonding energies of argon, aluminium and tungsten in electronvolts per atom, and compare the ratio of melting temperature (in kelvin) to bonding energy.

One mole contains $N_A=6.022\times10^{23}$ atoms and $1\ \mathrm{eV}=1.602\times10^{-19}$ J. For aluminium:

$$
E_0=\frac{324\times10^3\ \mathrm{J/mol}}{6.022\times10^{23}\ \mathrm{mol^{-1}}}
$$

$$
E_0=5.38\times10^{-19}\ \mathrm J=\frac{5.38\times10^{-19}}{1.602\times10^{-19}}\ \mathrm{eV}=3.36\ \mathrm{eV}
$$

In the same way argon is 0.080 eV and tungsten 8.80 eV. Converting the melting temperatures to kelvin: argon 84 K, aluminium 933 K, tungsten 3683 K. Tungsten's bonding energy is 2.6 times aluminium's and its absolute melting temperature 3.9 times; argon's bonding energy is a fortieth of aluminium's and its melting point an eleventh. Across the twelve substances in the table, the correlation between bonding energy and melting temperature in kelvin is 0.91, a strong but imperfect link.

> [!check] Thermal energy at room temperature
> The thermal energy of an atom is of order $kT$. At 293 K, $kT=1.38\times10^{-23}\times293/1.602\times10^{-19}=0.025$ eV, a third of argon's bonding energy but less than 1 % of aluminium's. That is why argon is a gas at room temperature while aluminium is a solid with 640 K to spare before it melts.

### Worked example - modulus ratio from the bond model

Use $E\approx mnE_0/r_0^3$ to predict the ratio of the moduli of tungsten and aluminium, given $r_0=0.274$ nm for W and 0.286 nm for Al (twice the atomic radius), and compare with the table.

Both are metals, so assume the same $m$ and $n$, which cancel in the ratio:

$$
\frac{E_W}{E_{Al}}=\frac{E_{0,W}}{E_{0,Al}}\left(\frac{r_{0,Al}}{r_{0,W}}\right)^3
$$

$$
\frac{E_W}{E_{Al}}=\frac{849}{324}\times\left(\frac{0.286}{0.274}\right)^3=2.62\times1.137=2.98
$$

The table gives $340/68=5.0$. The model gets the direction and the order of magnitude right (tungsten is several times stiffer) but not the factor, because it treats one bond in isolation and ignores how many neighbours each atom bonds to. It is a scaling argument and nothing more: stronger bonds, stiffer material.

---

## Links

- Parent: [[FEEG1002 Mechanics, Materials and Structures Hub]] · Previous (Statics 2): [[FEEG1002 B6 - Yield Criteria]] · Next: [[FEEG1002 C2 - Crystal Structures and Crystallography]]
- Concept: [[Atomic Bonding and Interatomic Potential]]
- Where the bonding returns: [[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation|C4]] (modulus as bond stretching, slip in metals) · [[FEEG1002 C9 - Fatigue, Creep and Corrosion|C9]] (corrosion as oxidation) · [[FEEG1002 C10 - Polymers - Structure and Mechanics|C10]] (van der Waals forces between chains) · [[FEEG1002 C11 - Ceramics and Composites|C11]] (ionic and covalent ceramics)
- Statics link: the $E$ used in every stress calculation of [[FEEG1002 A1 - Forces, Equilibrium, Stress and Strain|A1]] is the bond stiffness of §2.
- Formula list: [[FEEG1002 Formula Sheet]]

## Sources

- `FEEG1002 Lecture 2024-10-11.txt` (L1, 11 Oct 2024): course structure and assessment (ll. 31–70), why materials (ll. 274–375), atomic structure and shells (ll. 376–458), periodic table and valence (ll. 459–532, 616–635), EDX case studies (ll. 533–615), the bond force and energy picture (ll. 636–737), ionic, covalent and metallic bonds (ll. 738–839), secondary bonds (ll. 840–888), bond energy and properties (ll. 889–950), properties of the three classes and property charts (ll. 951–1074).
- `Lecture 01 - Introduction, Atoms and Bonding.pdf` (slide deck 01) and `Lecture 02 - Atoms and Bonding.pdf` (slide deck 02, the bonding slides of deck 01 repeated): learning outcomes, the elements, periodic organisation against valence, EDX maps, "Why? Atomic Bonding", primary and secondary bonding, the bonding energy table, properties of metals, polymers and ceramics. Figures after Callister, *Materials Science and Engineering: An Introduction*.
- The derivations of $E\approx S_0/r_0$ and $E\approx mnE_0/r_0^3$ go beyond the slides; they make the statement that the modulus comes from the bonding energy quantitative.

## Self-study tasks

### Core

No tutorial question or homework was set on this lecture; the first materials tutorial sheet starts with crystal structures. Suggested, not lecturer-set:

- [ ] Write out the electron configurations of Na, Cl, C and H and use them to explain why NaCl is ionic and CH₄ covalent (suggested, not lecturer-set). → [[#Electron configurations used in this part]] · [[#3. Primary bonds]]
- [ ] Sketch the force and energy curves for two atoms, marking $r_0$ and $E_0$, and explain which feature sets the melting point and which sets the modulus (suggested, not lecturer-set). → [[#Why the curve sets melting point and stiffness]]

### Further practice

- [ ] Derive $E\approx mnE_0/r_0^3$ for the potential $E_N=-A/r^m+B/r^n$ and use it to compare tungsten and aluminium (suggested, not lecturer-set). → [[#Linking well depth to stiffness]] · [[#Worked example - modulus ratio from the bond model]]

## Transcript and slide slips

> [!warning] Transcript slips (L1, ll. 697–708 and 822)
> Where: [[#From force to energy]] · [[#Covalent bonding]].
>
> At ll. 697–708 the balance at the equilibrium spacing is first called an "overall attractive force", then corrected to "attractive energy". At $r_0$ the net force is zero (as stated at l. 683); it is the net energy that has its minimum, $-E_0$. At l. 822 covalent bonding is summed up as "the handing over" of electrons; it is the sharing of electrons, and handing over is ionic bonding (stated correctly at ll. 746–751).

> [!warning] Slide slips (slide decks 01 and 02)
> Where: [[#1. Atoms and electron shells]] · [[#5. Bonding energy and properties]].
>
> The slide "The Elements" says four elements were "added in 2006"; elements 113, 115, 117 and 118 were confirmed in December 2015 and named in 2016 (repeated at L1, l. 419). The same slide gives the atomic weight as "Protons + Neutrons + Electrons"; its second bullet, the weighted average of the isotope masses, is the correct definition, and the electrons' share is negligible. The table gives 340 GPa for the modulus of tungsten; most data books give about 400–410 GPa. The summary slide lists covalent bonding as "electron exchange"; it is electron sharing.
