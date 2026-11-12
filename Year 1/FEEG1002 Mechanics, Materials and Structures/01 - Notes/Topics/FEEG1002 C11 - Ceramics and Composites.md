---
title: "FEEG1002 C11 - Ceramics and Composites"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part C: Materials"
order: 26
tags: [feeg1002, materials, ceramics, glass, composites, rule-of-mixtures, flaw-sensitivity]
aliases: ["Materials Lectures 17, 18 and 19", "Ceramics", "Composites", "Rule of mixtures"]
date: 2026-11-05
status: lectured
coverage: "Materials L17 (3 Dec 2024, ll. 1–780): ceramic bonding, cation-to-anion radius ratio and coordination number (NaCl, CaF2, SiO4), silicates and glasses, network modifiers, thermal behaviour and viscosity of glasses, bioglass, properties of ceramics, why dislocations cannot move in ionic solids, concrete and pre-stressing, strength scatter and statistical design, the Glasgow toilets case. Materials L18 (9 Dec 2024, ll. 1–909) and L19 (13 Dec 2024, a second delivery of the same lecture): reinforcement, matrix and interface, classification and material combinations, particle-reinforced examples, longitudinal (isostrain) and transverse (isostress) moduli of continuous aligned fibre composites, anisotropy and laminates, the in-class stiffness question, natural composites. Slide decks 18 and 19 in full."
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: ["[[FEEG1002 C1 - Atoms and Bonding]]", "[[FEEG1002 C8 - Fracture - Brittle, Ductile and Fracture Mechanics]]", "[[FEEG1002 C10 - Polymers - Structure and Mechanics]]"]
next_topics: []
key_concepts: ["[[Ceramic Flaw Sensitivity]]", "[[Composite Rule of Mixtures]]"]
tutorial_sheets: ["[[FEEG1002 Materials Tutorial 5 - Polymers, Ceramics and Composites Solutions]]"]
sources: ["02 - Sources/Materials/Lectures/Lecture 18 - Ceramics.pdf", "02 - Sources/Materials/Lectures/Lecture 19 - Composites.pdf", "02 - Sources/Lectures/FEEG1002 Lecture 17.txt", "02 - Sources/Lectures/FEEG1002 Lecture 18.txt", "02 - Sources/Lectures/FEEG1002 Lecture 19.txt", "02 - Sources/Materials/Tutorials/Tutorial Sheet 05 - Polymers Ceramics Composites.pdf"]
---

# FEEG1002 C11 - Ceramics and Composites

> [!abstract] Summary
> Ceramics are compounds of metals and non-metals held by ionic (sometimes covalent) bonds; their crystal structures are set by charge balance and by the ratio of cation to anion radius, which fixes the coordination number, and glasses are amorphous silica networks whose working temperatures fall as network modifiers break up the network. Their strong bonds make them hard, stiff, heat- and corrosion-resistant, but dislocations cannot move without bringing like charges together, so they are brittle, flaw-sensitive, weak in tension and scattered in strength, which forces a statistical approach to design. Composites combine a reinforcement with a matrix; for continuous aligned fibres, equal strain gives the longitudinal modulus $E_c=E_mV_m+E_fV_f$ and equal stress the much lower transverse modulus $E_c=E_mE_f/(E_fV_m+E_mV_f)$, so they are strongly anisotropic.

> [!summary]- Exam use: quick path
> - **Use it when:** a question asks for a coordination number from ionic radii, why soda-lime glass works at lower temperatures than silica, why ceramics are strong in compression but weak in tension and scattered in strength, or for the modulus of a continuous aligned composite along or across the fibres, or the share of the load the fibres carry.
> - **Assumptions:** for composites, continuous aligned fibres, perfect bonding, no voids ($V_f+V_m=1$), both phases linear elastic; isostrain along the fibres, isostress across them.
> - **Method:** 1. $r_C/r_A$ and the radius-ratio bands give the coordination number. 2. Longitudinal: $E_L=E_mV_m+E_fV_f$. 3. Transverse: $E_T=E_mE_f/(E_fV_m+E_mV_f)$. 4. Load sharing along the fibres: $\varepsilon=\sigma_c/E_L$, $\sigma_f=E_f\varepsilon$, $\sigma_m=E_m\varepsilon$, $F=\sigma\times VA$. 5. For ceramics, design to a low failure probability, not the mean strength, and keep them in compression.
> - **Common mistakes:** inverting the transverse sum term by term instead of over a common denominator; quoting the average strength of a ceramic as a design value.
> - **Practise:** [[#Worked example - stiffness of a carbon–epoxy ply]] · [[FEEG1002 Materials Tutorial 5 - Polymers, Ceramics and Composites Solutions]] Q4–Q7

Ceramics and composites are two classes of material that engineers increasingly use in place of metals. Ceramics are the strongly bonded compounds of [[FEEG1002 C1 - Atoms and Bonding#3. Primary bonds|C1]]: hard enough to make bearings and hip joints that hardly wear, stable enough to sit in a jet engine, but unable to deform plastically, so that a single flaw can bring them down at a fraction of their potential strength (L17, ll. 1–42). Designing with them means designing with statistics and keeping them in compression wherever possible.

Composites solve the ceramic problem from the other direction. A strong, stiff but brittle material made into fibres or particles small enough to be nearly flawless is embedded in a tougher matrix that holds them together, passes load between them and protects them. The result can be stiffer and stronger per kilogram than any metal, which is why aircraft wings and fan blades are now made of carbon-fibre composite (L18, ll. 5–57). The drawback is anisotropy: a fibre composite is very stiff along its fibres and barely stiffer than the matrix across them.

Bone, wood and feathers are natural composites, with fibres laid in the directions that the loads demand.

---

## 1. Ceramic bonding and structure

### Ionic bonding and charge balance

Ceramics are compounds of metallic and non-metallic elements, mostly ionically bonded and sometimes covalently, often a blend (slide "Structure and Bonding"; L17, ll. 43–81). The metallic atoms give up their valence electrons and become positively charged **cations** (Na⁺, Mg²⁺); the non-metallic atoms accept them and become negatively charged **anions** (O²⁻, F⁻, Cl⁻). Both end up with full outer shells, and the ionic bonds between them are very strong. Ceramics such as alumina and zirconia are oxides.

Two things decide which crystal structure forms. First, the crystal must be electrically neutral, so the ratio of the ions is fixed by their charges: NaCl has one Na⁺ for each Cl⁻, CaF₂ two F⁻ for each Ca²⁺. Second, the relative sizes of the ions matter. Cations, having lost electrons, are small; anions, having gained them, are large. This is quite different from metals, where all the atoms are nearly the same size (within the 15 % rule of [[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation#Alloying and solid solutions|C4]]).

### Radius ratio and coordination number

A ceramic crystal structure is stable when the anions surrounding each cation are all in contact with it (slide "Relative Size"; L17, ll. 82–133). The number of anions in contact with a cation is its **coordination number**, and it depends on the ratio of the ionic radii, $r_C/r_A$. A tiny cation has room for only a few anions around it; a larger one can be surrounded by more. The usual bands are:

| $r_C/r_A$ | Coordination number | Geometry |
|---|---:|---|
| below 0.155 | 2 | linear |
| 0.155–0.225 | 3 | triangular |
| 0.225–0.414 | 4 | tetrahedral |
| 0.414–0.732 | 6 | octahedral |
| 0.732–1.0 | 8 | cubic |

![[m11_radius_ratio.png|900]]

Two salts show the rule at work (slide "Examples"; L17, ll. 134–160). In NaCl, $r_C=0.102$ nm and $r_A=0.181$ nm, so $r_C/r_A=0.563$ and the coordination number is 6: each Na⁺ is surrounded by six Cl⁻, and the structure is two interpenetrating FCC lattices. In CaF₂, $r_C=0.100$ nm and $r_A=0.133$ nm, so $r_C/r_A=0.752$ and the coordination number is 8: each Ca²⁺ sits at the centre of a simple cube of eight F⁻. The structures themselves are found by diffraction.

### Silicates and glasses

The basic unit of the silicates is the SiO₄⁴⁻ **tetrahedron**: silicon ($r_C=0.040$ nm) and oxygen ($r_A=0.140$ nm) give $r_C/r_A=0.286$ and a coordination number of 4, so each Si sits at the centre of a tetrahedron of four oxygens (slide "Silicates"; L17, ll. 161–226). The properties depend on how the tetrahedra pack and link through shared oxygens, and on additions of other metal oxides. Silica can be crystalline, in three polymorphs (quartz, cristobalite and tridymite); in clays and other sheet silicates the tetrahedra form sheets, where three oxygens of each tetrahedron are shared.

**Glasses** are built from the same silica tetrahedra in a non-crystalline, amorphous structure, with no long-range order (slide "Glass formation"). In pure silica glass, fused silica, every oxygen is a **bridging oxygen**, shared between two tetrahedra, so the network is fully connected: it has a high melting temperature and a very high viscosity. **Network modifiers**, oxides of metals such as sodium (Na₂O) and calcium (CaO), are added to break up the network while keeping it charge-neutral. Each modifier cation satisfies the charge on an oxygen that is then bonded to only one silicon, a **non-bridging oxygen**, so the network is cut (L17, ll. 227–262). The more modifier, the less connected the network: the glass softens at lower temperatures and its $T_g$ falls.

### Thermal behaviour and working temperatures

Glasses behave on heating and cooling like amorphous polymers ([[FEEG1002 C10 - Polymers - Structure and Mechanics#Specific volume and the two transitions|C10]]) (slide "Thermal behaviour of glasses"; L17, ll. 263–313). A crystalline ceramic shows a sudden drop in specific volume at its melting temperature. A glass instead cools as a supercooled liquid, its viscosity rising steadily, until at the glass transition temperature $T_g$ the slope of its specific volume changes and it becomes a rigid glass. Glassmakers mark the viscosity curve at fixed viscosities: the strain point (about $3\times10^{13}$ Pa s, below which the glass fractures before it deforms), the annealing point (about $10^{12}$ Pa s, where internal stresses relax in minutes), the softening point (about $4\times10^6$ Pa s) and the working point ($10^3$ Pa s). Going from fused silica to 96 % silica glass, borosilicate glass (with boron oxide added) and soda-lime glass (with sodium and calcium oxides), all of these temperatures fall, because each step adds more modifier and leaves a less connected network. Borosilicate is used for laboratory glassware; soda-lime, the easiest to work, for windows and bottles.

![[m11_glass_viscosity.png|900]]

Bioglass takes this to an extreme. With enough sodium, calcium and phosphorus in the network, the glass dissolves in water and releases calcium and phosphate, which form hydroxyapatite, the mineral of bone and teeth. In toothpaste it plugs the exposed dentinal tubules that cause sensitive teeth (L17, ll. 314–377).

## 2. Properties of ceramics

### What ceramics are good at

Ceramics are hard and wear-resistant, because their strong bonds make dislocation motion difficult (slide "Properties of Ceramics"; L17, ll. 378–415). Silicon carbide bearings and the ceramic heads of hip replacements rely on this: a hip ceramic can be polished to a surface roughness of 5–8 nm and keeps it in service, so its surfaces barely touch. Ceramics also resist high temperature, oxidation and corrosion, because their bonds are chemically stable and many of them are already oxides: there is nothing further to oxidise.

### Why ceramics are brittle

In a metal, slipping one plane of atoms over the next brings like atoms side by side, which the metallic bond does not mind. In an ionic ceramic, sliding a plane of ions by one ionic spacing would bring cations next to cations and anions next to anions, and like charges repel strongly (slide "Dislocation Motion in Ionic Ceramics"; L17, ll. 469–514). So dislocations can move only in a very few directions that avoid this, the slip systems are very limited, and in practice slip happens only at very high temperatures. In service a ceramic cannot deform plastically: when the stress gets too high it breaks.

### Strong in compression, weak in tension

The consequences follow directly (L17, ll. 416–468). There is no plastic deformation to relieve the stress concentration at a flaw ([[FEEG1002 C8 - Fracture - Brittle, Ductile and Fracture Mechanics#2. Stress concentrations|C8]]), so in tension a flaw raises the local stress to the fracture stress and the ceramic fails suddenly. In compression flaws are pushed shut and do not grow, so ceramics are very strong in compression, often ten times stronger than in tension. A sports car of 1430 kg can be balanced on four porcelain teacups. The design rule is to keep ceramics in compression and watch out for stress concentrations, flaws and tensile loads.

### Concrete and pre-stressing

Concrete is a ceramic composite: gravel and sand aggregate in a cement matrix, with two particle sizes for high density and good contact between them, and a water content that is critical for the properties (slide "Concrete"; L17, ll. 515–560). Like other ceramics it is strong in compression and weak in tension, so steel reinforcing bars are added to carry tension. **Pre-stressed concrete** goes further. The steel is tensioned first, the concrete is cast round it, and when the concrete has set the steel is released; as the steel tries to contract it squeezes the concrete, leaving it in residual compression. Any tensile service load must first cancel that compression before the concrete goes into tension at all, so the margin before tensile fracture is greatly increased (L17, ll. 561–614). Dental crowns use the same idea: porcelain fired onto a zirconia core, with matched thermal expansion and controlled cooling, is left in compression; cooled too quickly, the residual stresses at the interface crack the porcelain off.

### Scatter in strength and statistical design

Because a ceramic's strength is set by its largest flaw, and flaw sizes vary from piece to piece, the measured fracture strengths of nominally identical specimens scatter widely: for one typical ceramic an average of 660 MPa, with individual results from 390 to 800 MPa (slide "Strength of Ceramics"; L17, ll. 615–695). A specimen with a big flaw fails near 390 MPa; a nearly flawless one survives to near 800 MPa. A larger component is more likely to contain a big flaw, so it is weaker on average. Removing all flaws is very expensive, so instead:

1. Accept that a ceramic part cannot be designed for zero failures; describe the strengths statistically (Weibull analysis) as a probability of failure against stress.
2. Decide on an acceptable probability of failure.
3. From the service stress and the fracture toughness, find the critical flaw size, $a_c=\frac1\pi\left(K_{IC}/Y\sigma\right)^2$.
4. Inspect every part at the end of the production line and reject any with flaws larger than that.

Better manufacturing narrows the distribution. Metals, which can yield at their flaws, have a much narrower spread of strength. Ceramics can also fail by fatigue and slow crack growth. Victorian porcelain toilets in Glasgow collapsed under ordinary users after a century or so in service: cracks had grown slowly until the stress from a person's weight brought $K_I$ up to $K_{IC}$, and the porcelain fractured (L17, ll. 696–743).

![[m11_ceramic_strength.png|900]]

## 3. Composites

### Reinforcement, matrix and interface

A **composite** is a multiphase material made of two or more dissimilar constituents, combined to give properties better than either alone (slide "Component Phases"; L18, ll. 58–158). It has two roles to fill.

The **reinforcement** is generally the expensive, high-quality, flaw-free phase that gives the property wanted, such as carbon fibres or hard tungsten carbide particles. It may carry a coating to improve its bonding to the matrix; flaw-free carbon fibre is now relatively cheap, and much of the cost of a high-performance fibre is in its surface treatment, because the composite only works if the fibre is well bonded.

The **matrix** is not a filler. It bonds the reinforcement together and transfers load between the fibres, so that they act in unison instead of independently; it protects the brittle reinforcement from surface damage and impact, generally absorbing the damage in service; and it protects it from the environment. Steel reinforcement in concrete is usually not stainless, because the concrete protects it; epoxy does the same for carbon fibre (L19, ll. 102–138).

The properties of a composite depend on the materials, how much of each there is, how the reinforcement is distributed (40 % fibres all on one side of a badly laid-up part will fail early), the design and the processing route.

### Classification

Composites fall into three main groups (L18, ll. 159–220). **Particle-reinforced** composites are either large-particle composites such as concrete or dispersion-strengthened ones, which are taken to include precipitation-hardened alloys, with hard precipitates in a metal matrix ([[FEEG1002 C7 - Steels and Precipitation Hardening#5. Precipitation hardening|C7]]). **Fibre-reinforced** composites may have continuous and aligned fibres, for high-performance structures with fibres laid along the stresses; discontinuous and aligned fibres, such as extruded fibre-filled polymers; or discontinuous and randomly oriented fibres, such as chopped-strand mats, which are cheaper and less efficient. **Structural** composites are laminates, such as plywood or stacked fibre plies, and sandwich panels, with stiff skins on a light core such as aluminium foam.

The constituents can come from any of the material classes (slide "Composite Classification"): metal–metal (boron–aluminium), metal–ceramic (silicon carbide fibres in titanium), metal–polymer (steel cords in tyre rubber), ceramic–polymer (glass fibre in polyester), ceramic–ceramic (silicon carbide fibres in silicon carbide) and polymer–polymer (aramid fibre in epoxy, as in Kevlar body armour). By convention the more expensive filler material, the reinforcement, is named first: carbon-fibre-reinforced polymer.

### Particle-reinforced examples

Tungsten carbide (WC) is a very hard ceramic, ideal for cutting, but like any ceramic it is notch-sensitive, and cutting is a repeated impact (slide "Particle Reinforced Examples"; L18, ll. 270–326). Broken into small particles, each WC grain is effectively flaw-free and does not fracture; embedded in a cobalt matrix, the composite gains the ductility and impact resistance of the metal, which also holds the particles in. The composite is less hard than solid WC, but one flaw no longer ruins the tool. Car-tyre rubber is reinforced with carbon-black particles about 0.2 µm across, which raise its stiffness and wear resistance. The two examples differ in scale by orders of magnitude.

## 4. Moduli of continuous aligned fibre composites

The simplest composite to analyse is a ply of continuous fibres all aligned in one direction, perfectly bonded to the matrix (slides "Fibre Reinforced Composite Mechanics", "Property Approximations"; L18, ll. 353–641). Subscripts $c$, $m$ and $f$ mean composite, matrix and fibre; $V_f$ and $V_m$ are the volume fractions, with $V_f+V_m=1$ for a composite with no voids. On its own the fibre is stiff and linear elastic up to a brittle fracture at high stress, while the matrix is far less stiff and yields and fails at a much larger strain but a much lower stress. The composite lies between, and the **rule of mixtures** estimates its properties from those of its constituents.

![[m11_isostrain_isostress.png|900]]

### Longitudinal modulus from equal strain

Load the ply along the fibres. Because fibres and matrix are perfectly bonded side by side and run the full length, they must stretch by the same amount: the strain is the same in each, the **isostrain** condition,

$$
\varepsilon_c=\varepsilon_f=\varepsilon_m
$$

The force on the composite is shared between matrix and fibres:

$$
F_c=F_m+F_f
$$

Write each force as stress times area, $F=\sigma A$:

$$
\sigma_cA_c=\sigma_mA_m+\sigma_fA_f
$$

Divide through by the area of the composite:

$$
\sigma_c=\sigma_m\frac{A_m}{A_c}+\sigma_f\frac{A_f}{A_c}
$$

The fibres run the full length with the same cross-section everywhere, so the area fractions equal the volume fractions:

$$
\sigma_c=\sigma_mV_m+\sigma_fV_f
$$

Divide each term by its strain; all three strains are equal, so this divides the whole equation by one number:

$$
\frac{\sigma_c}{\varepsilon_c}=\frac{\sigma_m}{\varepsilon_m}V_m+\frac{\sigma_f}{\varepsilon_f}V_f
$$

and each ratio of stress to strain is a modulus:

$$
\boxed{E_c=E_mV_m+E_fV_f}
$$

The longitudinal modulus is the volume-weighted average of the two moduli, and since $E_f\gg E_m$ it is dominated by the fibres. Fewer fibres put more weight on the much less stiff matrix and lower the modulus. Composites deliver their stiffness only when loaded along the fibres (L18, ll. 412–549).

### Load carried by the fibres

The same isostrain argument shows how the load is shared. With equal strains, $\sigma_f=E_f\varepsilon$ and $\sigma_m=E_m\varepsilon$, so

$$
\frac{F_f}{F_m}=\frac{\sigma_fA_f}{\sigma_mA_m}=\frac{E_f\varepsilon\,V_fA_c}{E_m\varepsilon\,V_mA_c}=\frac{E_fV_f}{E_mV_m}
$$

and the fraction of the total load carried by the fibres is

$$
\frac{F_f}{F_c}=\frac{E_fV_f}{E_mV_m+E_fV_f}=\frac{E_fV_f}{E_c}
$$

In practice, with a stiff fibre, nearly all the load goes through the fibres. This is what Tutorial Sheet 5, Q4b asks for.

### Transverse modulus from equal stress

With the ply loaded at 90° to the fibres, the fibres and matrix no longer stretch together; the matrix between the fibres is not protected by them, and the two act more like layers stacked one on top of another across the load path. The same load passes through each layer over the same area normal to the load, so each carries the same stress: the **isostress** condition,

$$
\sigma_c=\sigma_m=\sigma_f
$$

The total extension across the ply is the sum of the extensions of the matrix and fibre layers, each proportional to its share of the thickness, which is its volume fraction:

$$
\varepsilon_c=\varepsilon_mV_m+\varepsilon_fV_f
$$

Substitute $\varepsilon=\sigma/E$ for each:

$$
\frac{\sigma_c}{E_c}=\frac{\sigma_m}{E_m}V_m+\frac{\sigma_f}{E_f}V_f
$$

The stresses are all equal, so they cancel:

$$
\frac{1}{E_c}=\frac{V_m}{E_m}+\frac{V_f}{E_f}
$$

The right-hand side cannot be turned upside down term by term. Put it over the common denominator $E_mE_f$, multiplying the first fraction top and bottom by $E_f$ and the second by $E_m$:

$$
\frac{1}{E_c}=\frac{V_mE_f}{E_mE_f}+\frac{V_fE_m}{E_mE_f}=\frac{V_mE_f+V_fE_m}{E_mE_f}
$$

and now invert:

$$
\boxed{E_c=\frac{E_mE_f}{E_fV_m+E_mV_f}}
$$

The transverse modulus is dominated by the matrix: the compliant layer takes most of the extension, and the stiff fibres contribute little (L18, ll. 550–641; L19, ll. 651–652).

![[m11_composite_moduli.png|900]]

The rule of mixtures can be used, approximately, for other properties such as strength and yield strength, but not for fracture toughness (L18, ll. 642–663). It also only covers continuous aligned fibres; short fibres, fibre length and interface area need more advanced treatments.

### Anisotropy and laminates

Because the longitudinal modulus is so much larger than the transverse modulus, a unidirectional composite is strongly **anisotropic**: its properties differ with direction. An **isotropic** material has the same properties in every direction (slide "Composite Anisotropy"; L18, ll. 664–710). Where loads come from several directions, plies are stacked at different angles into a **laminate**: 0° and 90° plies for loads along two axes, ±45° plies to carry shear. Cross-ply laminates approach isotropic behaviour in the plane. For lightweight design, though, the fibres are laid along the known load paths, so that the material is put where the stresses are; any load the lay-up does not allow for can cause early failure.

### Choosing the stiffest combination

A table of fibre and matrix moduli for a 60 % fibre, 40 % matrix composite asks which combination is stiffest, first along the fibres and then across them (in-class question, L18, ll. 711–776). No calculation is needed if one option has both the stiffest fibre and the stiffest matrix, because both formulas increase with $E_f$ and with $E_m$: longitudinally $\partial E_c/\partial E_f=V_f>0$ and $\partial E_c/\partial E_m=V_m>0$, and transversely $1/E_c=V_m/E_m+V_f/E_f$ falls as either modulus rises. The same option wins in both directions. An exam question may be set so that no single option is best in both, in which case the two formulas have to be evaluated.

### Natural composites

Bone, wood and feathers are composites with the reinforcement laid along the loads (slide "Nature and Composites"; L18, ll. 777–897; L19). Bone is made of collagen fibres with crystals of hydroxyapatite mineral between them; in cortical bone these form concentric rings round a central blood vessel (osteons), with the fibres in successive rings at different orientations, while cancellous bone is a lightweight cellular solid whose struts follow the stress. Bone also repairs itself and remodels to suit its loads, which no engineering material yet does. Wood has cell walls built of layers with fibres at different angles. A feather shaft is β-keratin fibres in a β-keratin matrix, with fibres both along and around the shaft to resist bending and shear.

---

## Worked examples

### Worked example - coordination numbers from ionic radii

Predict the coordination number of the cation in NaCl, CaF₂, MgO and SiO₂, using $r_{Na^+}=0.102$ nm, $r_{Cl^-}=0.181$ nm, $r_{Ca^{2+}}=0.100$ nm, $r_{F^-}=0.133$ nm, $r_{Mg^{2+}}=0.072$ nm, $r_{Si^{4+}}=0.040$ nm and $r_{O^{2-}}=0.140$ nm.

$$
\mathrm{NaCl:}\ \frac{0.102}{0.181}=0.563\ \Rightarrow\ \text{CN }6
$$

$$
\mathrm{CaF_2:}\ \frac{0.100}{0.133}=0.752\ \Rightarrow\ \text{CN }8
$$

$$
\mathrm{MgO:}\ \frac{0.072}{0.140}=0.514\ \Rightarrow\ \text{CN }6
$$

$$
\mathrm{SiO_2:}\ \frac{0.040}{0.140}=0.286\ \Rightarrow\ \text{CN }4
$$

MgO takes the same rock-salt structure as NaCl, and silicon sits in the tetrahedron that builds every silicate and glass.

### Worked example - stiffness of a carbon–epoxy ply

A unidirectional ply has 60 % by volume of carbon fibre ($E_f=230$ GPa) in epoxy ($E_m=3.5$ GPa). Find its longitudinal and transverse moduli, the share of a longitudinal load carried by the fibres, and the stresses in each phase when the ply carries 500 MPa along the fibres.

$$
E_L=E_mV_m+E_fV_f=3.5\times0.4+230\times0.6=1.4+138=139.4\ \mathrm{GPa}
$$

$$
E_T=\frac{E_mE_f}{E_fV_m+E_mV_f}=\frac{3.5\times230}{230\times0.4+3.5\times0.6}=\frac{805}{94.1}=8.55\ \mathrm{GPa}
$$

The ply is 16 times stiffer along its fibres than across them. The fibres carry

$$
\frac{F_f}{F_c}=\frac{E_fV_f}{E_L}=\frac{138}{139.4}=0.99
$$

99 % of a longitudinal load. At $\sigma_c=500$ MPa the common strain is

$$
\varepsilon=\frac{\sigma_c}{E_L}=\frac{500}{139\,400}=3.59\times10^{-3}
$$

$$
\sigma_f=E_f\varepsilon=230\,000\times3.59\times10^{-3}=825\ \mathrm{MPa},\qquad\sigma_m=E_m\varepsilon=3500\times3.59\times10^{-3}=12.6\ \mathrm{MPa}
$$

> [!check] Stresses add back to the applied stress
> $\sigma_mV_m+\sigma_fV_f=12.6\times0.4+825\times0.6=5.0+495=500$ MPa, the stress applied. Across the fibres the same ply is little stiffer than the matrix, because the soft epoxy layers take nearly all the extension: of the transverse compliance $1/E_T=0.4/3.5+0.6/230=0.1143+0.0026$ GPa⁻¹, 98 % comes from the matrix.

### Worked example - pre-stressed concrete

Concrete with a tensile strength of 3 MPa is pre-stressed so that it carries a residual compression of 5 MPa. What applied tensile stress can it take before it cracks?

The applied tension must first cancel the residual compression and then reach the tensile strength:

$$
\sigma_{applied}=5+3=8\ \mathrm{MPa}
$$

nearly three times the 3 MPa that un-stressed concrete could take.

---

## Links

- Parent: [[FEEG1002 Mechanics, Materials and Structures Hub]] · Previous: [[FEEG1002 C10 - Polymers - Structure and Mechanics]]
- Concepts: [[Ceramic Flaw Sensitivity]] · [[Composite Rule of Mixtures]] · [[Griffith Criterion and Fracture Toughness]]
- Worked sheet: [[FEEG1002 Materials Tutorial 5 - Polymers, Ceramics and Composites Solutions]] (Q4–Q7) · Formula list: [[FEEG1002 Formula Sheet]]
- Statics: [[FEEG1002 B3 - Generalised Hooke's Law]] (isotropic elasticity, which a unidirectional ply is not) · [[Equivalent Spring Stiffness]] (isostrain and isostress are springs in parallel and in series)
- Year 2: [[SESA2028 M4 - Polymer Matrix Composites]] · [[SESA2028 M5 - Metal and Ceramic Matrix Composites and Hybrid Laminates]] · [[Rule of Mixtures]] · [[Critical Fibre Length]]

## Sources

- `FEEG1002 Lecture 17.txt` (L17, 3 Dec 2024): bonding (ll. 43–81), radius ratio and coordination (ll. 82–160), silicates and glasses (ll. 161–262), thermal behaviour and viscosity (ll. 263–313), bioglass (ll. 314–377), useful properties (ll. 378–415), compression and tension (ll. 416–468), why dislocations cannot move (ll. 469–514), concrete and pre-stressing (ll. 515–614), strength scatter and statistical design (ll. 615–695), the Glasgow toilets (ll. 697–743), summary (ll. 744–780).
- `FEEG1002 Lecture 18.txt` (L18, 9 Dec 2024): reinforcement, matrix and interface (ll. 58–158), classification and combinations (ll. 159–269), particle-reinforced examples (ll. 270–326), the rule of mixtures, isostrain (ll. 353–549), isostress (ll. 550–663), anisotropy (ll. 664–710), the in-class question (ll. 711–776), natural composites (ll. 777–897).
- `FEEG1002 Lecture 19.txt` (L19, 13 Dec 2024): a second delivery of the same composites lecture, used here for its clearer statement of the common-denominator step in the transverse derivation (ll. 651–652), the concrete-and-rebar example of matrix protection and the fuller description of bone.
- `Lecture 18 - Ceramics.pdf` (slide deck 18) and `Lecture 19 - Composites.pdf` (slide deck 19). Figures after Callister. The radius-ratio bands are Callister's.
- `Tutorial Sheet 05 - Polymers Ceramics Composites.pdf`: Q4–Q7.

## Self-study tasks

### Core

- [ ] Tutorial 5, Q4: longitudinal and transverse moduli of a 40 % glass–polyester composite, and the loads carried by fibres and matrix at 50 MPa over 250 mm². Targets 29.6 and 5.49 GPa; 11.6 and 0.86 kN. → [[#4. Moduli of continuous aligned fibre composites]] · [[FEEG1002 Materials Tutorial 5 - Polymers, Ceramics and Composites Solutions#Q4 - Glass–polyester composite]]
- [ ] Tutorial 5, Q5: why ceramics are strong but have low impact toughness. → [[#Why ceramics are brittle]] · [[FEEG1002 Materials Tutorial 5 - Polymers, Ceramics and Composites Solutions#Q5 - Strong but not tough]]
- [ ] Tutorial 5, Q6: why soda-lime glass has a lower $T_g$ and melting point than 96 % silica glass. → [[#Silicates and glasses]] · [[FEEG1002 Materials Tutorial 5 - Polymers, Ceramics and Composites Solutions#Q6 - Soda-lime against silica glass]]
- [ ] Tutorial 5, Q7: why Portland cement strengths are scattered, and why the average is not a design value. → [[#Scatter in strength and statistical design]] · [[FEEG1002 Materials Tutorial 5 - Polymers, Ceramics and Composites Solutions#Q7 - Strength distribution of Portland cement]]
- [ ] The in-class stiffness question: which fibre–matrix pair is stiffest along and across the fibres (L18, ll. 711–776). → [[#Choosing the stiffest combination]]

### Further practice

- [ ] Derive both rule-of-mixtures moduli from the isostrain and isostress conditions, including the common-denominator step. → [[#Longitudinal modulus from equal strain]] · [[#Transverse modulus from equal stress]]
- [ ] Explain, with the radius ratio, why NaCl has six neighbours round each sodium and CaF₂ eight round each calcium (suggested, not lecturer-set). → [[#Worked example - coordination numbers from ionic radii]]

## Transcript and slide slips

> [!warning] Transcript slips (L17, ll. 108, 111–117, 184–185, 278 and 539–546)
> Where: [[#Radius ratio and coordination number]] · [[#Silicates and glasses]] · [[#Concrete and pre-stressing]].
>
> A very small "anion in the middle" is said to give a coordination number of 2; the central ion is the cation. The silicates are called "tetragonal-style structures"; the SiO₄ unit is tetrahedral (tetragonal is a crystal system). The list of coordination numbers jumps to "five, six", skipping 3; the standard bands are 2, 3, 4, 6 and 8. Coordination 8 "looks like a body-centred cubic"; with two different ions the arrangement is a simple cube of anions round the cation, as stated for CaF₂. Fused silica is twice called "crystalline"; it is amorphous, and quartz is the crystalline form. Cement is described as a gypsum that dissolves and recrystallises; Portland cement sets by the hydration of calcium silicates, and gypsum is only a minor additive (the dissolve-and-regrow picture fits plaster of Paris).

> [!warning] Transcript and slide slips (L17, l. 416; slide "Properties of Ceramics")
> Where: [[#Strong in compression, weak in tension]].
>
> Ceramics are said to have a "high shear strength (dislocation motion again) hence strong in compression". The strength in compression comes from flaws being pushed closed rather than opened; it is the absence of dislocation motion that makes them hard and stops them yielding.

> [!warning] Transcript slips (L18, ll. 579–582 and 620–622)
> Where: [[#Transverse modulus from equal stress]].
>
> Isostress is justified by fibres and matrix having "the same cross-sectional area"; the reason is that the same load passes through each layer in series over the same area normal to the load. The common-denominator step is garbled ("multiply both sides by $E_F$ … by $E_M$"); the correct step, as stated in L19, ll. 651–652, multiplies each fraction top and bottom by the other modulus.
