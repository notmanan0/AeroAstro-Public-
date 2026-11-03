---
title: "SESA2028 M4 - Polymer Matrix Composites"
module: "SESA2028 Aerospace Materials & Structures"
type: topic
stream: "Materials"
order: 4
tags: [sesa2028, materials, composites, lightweighting, rule-of-mixtures, manufacturing]
status: lectured
coverage: "Mini-lectures ML5a, ML5b, ML5c, ML6a, ML6b and ML10b"
date: 2026-10-30
parent: ["[[SESA2028 Aerospace Materials & Structures Hub]]"]
prerequisites: ["[[SESA2028 M1 - Fracture, Toughness and Fracture Mechanics]]"]
next_topics: ["[[SESA2028 M5 - Metal and Ceramic Matrix Composites and Hybrid Laminates]]"]
key_concepts: ["[[Specific Stiffness and Strength]]", "[[Rule of Mixtures]]", "[[Critical Fibre Length]]", "[[Composite Manufacturing Routes]]"]
tutorial_sheets: ["[[SESA2028 Materials Tutorial MT3 - Lightweighting Solutions]]"]
sources: ["02 - Sources/Materials Lectures/Lightweighting 2025.pdf (lecture blocks 5-6)", "02 - Sources/Materials Lectures/mini lecture videos/ML5a Intro to lightweighting_default.txt", "02 - Sources/Materials Lectures/mini lecture videos/ML5b Composite Basics_default.txt", "02 - Sources/Materials Lectures/mini lecture videos/ML5c Composite Anisotropy_default.txt", "02 - Sources/Materials Lectures/mini lecture videos/ML6a Composites Manufacture_default.txt", "02 - Sources/Materials Lectures/mini lecture videos/ML6b Choosing Composites_default.txt", "02 - Sources/Materials Lectures/mini lecture videos/ML10b 3D evaluations of composite failures_default.txt"]
---

# SESA2028 M4 - Polymer Matrix Composites

> [!abstract] Summary
> Lightweighting means getting the stiffness or strength a moving structure needs for the least mass, so materials are compared on specific properties, $E/\rho$ and $\sigma/\rho$. Fibre composites win on those, but only along the fibres: the rule of mixtures gives the longitudinal stiffness as a volume-weighted average (equal strain) and the transverse stiffness as a weighted harmonic mean dominated by the soft matrix (equal stress). Short fibres carry load only once the matrix has sheared it into them over a critical length. The rest of the topic explains why composites are not used everywhere: they are made at the same time as the structure, so quality and cost depend on the manufacturing route, and their damage is a spread of ply cracks, splits and delaminations rather than one crack, so the fracture mechanics of [[SESA2028 M1 - Fracture, Toughness and Fracture Mechanics|M1]] and [[SESA2028 M2 - Fatigue - Fracture Surfaces, Mechanisms and Lifing|M2]] cannot life them.

> [!summary]- Exam use: quick path
> - **Use it when:** comparing materials for a lightweight part, estimating a composite's stiffness or strength, finding the fibre fraction needed for a requirement, or discussing manufacture and why aerospace adopts composites cautiously.
> - **Assumptions:** perfect bonding, fibres and matrix linear elastic; continuous aligned fibres (or fibres at least about $15l_c$ long) for the rule of mixtures.
> - **Method:** 1. Choose the index for the loading: $E/\rho$ or $\sigma/\rho$ for a tie, $E^{1/2}/\rho$ for a buckling strut. 2. $E_L=V_fE_f+V_mE_m$ along the fibres. 3. $1/E_T=V_f/E_f+V_m/E_m$ across them. 4. For a requirement $P$, $V_f=(P-P_m)/(P_f-P_m)$ for each property; take the larger. 5. Comment on manufacture, compression, damage and cost.
> - **Common mistakes:** using the longitudinal rule for transverse stiffness; forgetting that $V_f$ above about 0.65 is hard to make.
> - **Example:** [[#Stiffness of a glass composite along and across the fibres]]. **Exercise:** [[SESA2028 Materials Tutorial MT3 - Lightweighting Solutions]], Q2.

Lightweighting is a transport problem (ML5a, ll. 8–17). Whatever moves needs fuel to move it, so a lifeboat, an airframe or a Formula One car needs structures that carry their loads with the least mass. Some of the gain comes from geometry, the subject of the structures half of the module, and some from choosing and controlling the material. Composites are the materials case in point, because they let a designer put stiff, strong fibres exactly where the loads go.

The physical picture to hold is a bundle of very stiff, very strong but brittle fibres held in a soft polymer. Pull along the fibres and they take almost all the load, because to stretch with the matrix they must carry stress in proportion to their much higher modulus. Pull across them and the load has to pass through the soft matrix between fibres, which stretches easily, so the composite is barely stiffer than the resin alone. Every strength and weakness of these materials follows from that picture: the directional properties, the need to lay plies at several angles, the importance of the fibre–matrix bond, and failure by many small cracks between and through plies.

## 1. Why lightweight, and with what

The marine examples come first (ML5a, ll. 30–65). Sailing dinghies, racing yachts and the America's Cup work of Southampton's Wolfson Unit use composites because they are light and do not corrode like metals, though water can be absorbed into the matrix. Mine-hunter hulls, such as those built by Vosper, are composite because a non-metallic hull is harder to detect and does not trigger magnetic mines.

The automotive story is a lesson in prediction (ll. 66–133). A 1980s forecast of the car of 2000 assumed aluminium in places, a little plastic and mostly high-strength low-alloy steel; nobody foresaw the small electric city car or the fashion for large SUVs. The market and society's priorities, now including the green agenda, set the performance envelope as much as engineering does. Lightweighting has also driven steels: modern high-strength steels are so strong that a thin section is competitive on specific strength, and they are cheap at enormous scale. The Reliant Robin relied on a composite body, the Sinclair C5 was a lightweight electric vehicle that never took off, and the carbon bonnet of an Aston Martin DB9 is more marketing than structure, since a bonnet is essentially a lid.

Aircraft are where composites have taken over major structure (ll. 134–162). Very large aircraft such as the A380 and the Dreamliner could only be made to fly with composite wings and other large composite parts. On the A380, carbon fibre composite is used in the outer wing, nacelle cowlings, tail, stabiliser, tail cone, central torsion box, radome and fairings, with aluminium alloys still joined to it, so hybrid metal–composite joints are a challenge in their own right.

### Specific properties

When mass matters, the property to compare is the property per unit density (ML5a, ll. 52–58):

$$
\text{specific stiffness}=\frac{E}{\rho},
\qquad
\text{specific strength}=\frac{\sigma_{UTS}}{\rho}.
$$

Which combination to maximise depends on how the part is loaded; this is used in the tutorial and past papers. For a tie of length $L$ carrying force $F$, the area needed for strength is $A=F/\sigma$, so the mass is

$$
m=\rho AL=FL\,\frac{\rho}{\sigma},
$$

and the lightest tie maximises $\sigma/\rho$. For a stiffness limit, the extension $\delta=FL/(AE)$ must not exceed a set value, so $A=FL/(E\delta)$ and

$$
m=\frac{FL^2}{\delta}\,\frac{\rho}{E},
$$

which is minimised by maximising $E/\rho$. A slender strut fails by Euler buckling, $P=\pi^2EI/L^2$. For a solid circular section $I=\pi r^4/4$ and $A=\pi r^2$, so

$$
I=\frac{A^2}{4\pi}.
$$

Substituting,

$$
P=\frac{\pi^2E}{L^2}\,\frac{A^2}{4\pi}=\frac{\pi EA^2}{4L^2},
$$

so the area needed is

$$
A=\sqrt{\frac{4PL^2}{\pi E}}=2L\sqrt{\frac{P}{\pi E}},
$$

and the mass is

$$
m=\rho AL=2L^2\sqrt{\frac{P}{\pi}}\,\frac{\rho}{E^{1/2}}.
$$

The lightest strut maximises $E^{1/2}/\rho$. The square root rewards low density more than high stiffness, which favours light materials more strongly still. See [[Specific Stiffness and Strength]].

## 2. What a composite is

A **composite** is a system of two or more constituents that differ greatly in form and chemistry, are essentially insoluble in each other, and have been physically put together (ML5b, ll. 10–21). A precipitation-hardened alloy can achieve similar strengthening, but its second phase grew out of solid solution, so it counts as an engineered alloy rather than a composite. The reinforcement is the expensive, high-quality part that must be as free of defects as possible; the matrix surrounds and holds it (ll. 22–27).

The reinforcement can be continuous fibre, whose alignment is fully controlled; chopped strand, as in glass-fibre dinghy hulls, which is cheaper and easier to shape but whose alignment cannot be controlled; or particles, which give smaller but isotropic gains at low cost (ll. 28–40).

Glass fibres have been used since the 1920s; carbon fibres since the 1970s, now the fastest-growing tonnage because of the large-aircraft programmes, with properties that can be tailored by how they are made; and aramid (Kevlar) fibres since the 1970s, which unlike brittle glass and carbon are relatively ductile, necking and splitting into tendrils, and so suit body armour (ll. 43–64). Natural fibres such as jute and hemp are attractive for "green" composites but vary in quality and depend strongly on moisture (ll. 65–76). For metal and ceramic matrices, high-temperature ceramic fibres are needed: a boron fibre, for example, is made by depositing boron onto a tungsten wire core, which reacts to form a boride core (ll. 77–91).

The lecturer's advice on property tables is not to memorise them but to interrogate them (ll. 95–125). Whiskers, short single crystals with very few defects, have the highest strength and modulus but are short. Drawn or deposited fibres are a little lower but long, which gives far more freedom in design. Metal wires such as high-strength steel, molybdenum and tungsten are strong but dense, so their specific strength is unimpressive. Specific properties are what count in lightweighting.

The matrix does much more than glue (ll. 126–162). It holds the reinforcement in shape, transfers load into it, and protects it. It is also the weak link: the fibres keep their properties to high temperature, but a low-melting matrix sets the composite's maximum service temperature, which is the reason for the metal and ceramic matrices of [[SESA2028 M5 - Metal and Ceramic Matrix Composites and Hybrid Laminates|M5]]. It largely sets the fire behaviour, and absorbed moisture changes its glass transition and so its properties. And because a composite's material is made at the same moment as its structure, the matrix decides how the part can be manufactured and much of its cost.

The two common thermoset resins compare as follows (ll. 163–177): polyester is about ten times cheaper than epoxy, but has poorer mechanical properties, shrinks more on cure (so holds tolerances less well) and absorbs more moisture. Epoxy is used for high-quality, high-value structures such as aircraft parts; chopped-strand glass in polyester is the cheap, ubiquitous choice for many marine shapes.

## 3. Anisotropy and the rule of mixtures

Unidirectional composites are extremely directional (ML5c, ll. 1–12). At 50 % fibre by volume, glass–polyester has a tensile strength of about 700 MPa along the fibres but only 20 MPa across them; high-modulus carbon–epoxy about 1000 MPa against 35 MPa; Kevlar–epoxy about 1200 MPa against 20 MPa. Steel ranges from about 300 to 1000 MPa, comparable along the fibres, but at about three times the density, so the composite's specific strength along the fibres is far higher.

The properties depend on the fibre, the matrix, how much of each, and how they are laid up (ll. 13–15). The rule of mixtures, revised from Part 1, also works for density and electrical resistivity, but not for toughness, because composite failure mechanisms are far too complicated (ll. 16–20). The lecturer flags it as an "exam top tip": the rules of mixtures are asked for often (l. 21).

![[materials_isostrain_isostress.png|900]]

### Along the fibres: equal strain

Loaded along the fibres, fibres and matrix stay bonded, so they stretch by the same amount (ll. 23–34):

$$
\varepsilon_f=\varepsilon_m=\varepsilon_c .
$$

The load is shared, so the force on a section is the sum of the forces in fibre and matrix. Dividing by the total area $A$, with $V_f=A_f/A$ and $V_m=A_m/A=1-V_f$,

$$
\sigma_cA=\sigma_fA_f+\sigma_mA_m
\quad\Longrightarrow\quad
\sigma_c=V_f\sigma_f+V_m\sigma_m .
$$

Each constituent is elastic, so $\sigma=E\varepsilon$ with the common strain:

$$
E_L\varepsilon_c=V_fE_f\varepsilon_c+V_mE_m\varepsilon_c,
$$

and cancelling $\varepsilon_c$,

$$
E_L=V_fE_f+V_mE_m .
$$

The ratio of the loads carried shows why the fibres do the work:

$$
\frac{P_f}{P_m}=\frac{\sigma_fA_f}{\sigma_mA_m}=\frac{E_f\varepsilon V_f}{E_m\varepsilon V_m}=\frac{V_fE_f}{V_mE_m}.
$$

To stretch a stiff fibre by the same strain takes far more stress than the matrix needs, so the load is partitioned to the fibres (ll. 30–33).

### Across the fibres: equal stress

Loaded across the fibres, the load passes through fibre and matrix in series, so each carries the same stress (ll. 35–44):

$$
\sigma_f=\sigma_m=\sigma_c .
$$

The extensions add instead. Over a gauge length made up of fractions $V_f$ of fibre and $V_m$ of matrix, the composite strain is

$$
\varepsilon_c=V_f\varepsilon_f+V_m\varepsilon_m .
$$

Writing each strain as stress over modulus with the common stress,

$$
\frac{\sigma_c}{E_T}=V_f\frac{\sigma_c}{E_f}+V_m\frac{\sigma_c}{E_m},
$$

and cancelling $\sigma_c$,

$$
\frac{1}{E_T}=\frac{V_f}{E_f}+\frac{V_m}{E_m}.
$$

Because $E_m\ll E_f$, the second term dominates and $E_T$ is only a little above the matrix modulus: the improvement across the fibres is very poor (l. 43).

![[materials_rule_of_mixtures.png|800]]

### Designing to a requirement

Past papers often ask for the fibre fraction that just meets a stiffness or strength requirement $P$. Setting $P=V_fP_f+(1-V_f)P_m$ and solving,

$$
P=P_m+V_f\left(P_f-P_m\right)
\quad\Longrightarrow\quad
V_f=\frac{P-P_m}{P_f-P_m}.
$$

Do it for each requirement and take the larger fraction. Above about 0.65 is hard to manufacture.

![[materials_required_fibre_fractions.png|800]]

### Laminates, fabrics and hybrids

The strength of composites is that a lay-up can put the properties in the directions the loads need (ll. 47–63). They are rarely used unidirectionally; plies are stacked in a laminate. A 0/90 lay-up is good along both ply directions but weak at 45°, so if the part sees shear, ±45° plies are added (ll. 64–72). The choice depends on knowing the stresses in the structure, which is where the structures lectures feed in (ll. 73–76). The lay-up must also suit manufacture: when the resin cures and the part cools, plies contract differently along and across their fibres, so the stacking must balance those contractions to avoid distortion, residual stress and lost tolerance (ll. 77–85). Woven fabrics, including carbon–Kevlar hybrids and robot-knitted three-dimensional shapes, give a ready-made fibre architecture that is much easier to handle than loose fibres (ll. 86–94). A hybrid of two fibres follows the rule of mixtures with an extra term, $E=V_{f1}E_{f1}+V_{f2}E_{f2}+V_mE_m$ (ll. 61–63). Laminate theory itself is left to later specialist modules (ll. 58–60).

## 4. Short fibres and the critical length

The rule of mixtures assumes continuous fibres, and short fibres are "nearly all end" (ML5c, ll. 95–102). Chopped fibres are cheaper and flow into shapes easily, but give smaller benefits. At a fibre end there is no fibre to carry stress, so the fibre stress is zero there; load is fed in from the matrix by shear along the interface, the shear-lag model, so the fibre stress builds up from each end and peaks at the middle (ll. 103–111).

The **critical fibre length** $l_c$ is the shortest fibre whose midpoint can reach the fibre's breaking stress $\sigma_f^*$ (ll. 112–121). The lecture describes it qualitatively, as set by the load transfer between matrix and fibre (ll. 131–133); the usual force balance gives its value. Take a fibre of diameter $d$ and let the interface carry a shear stress $\tau$ (its shear strength, or the matrix yield stress in shear). Over a length $x$ from the end, the shear force on the fibre surface is $\tau\pi dx$, and it must equal the tensile force in the fibre at $x$:

$$
\sigma(x)\,\frac{\pi d^2}{4}=\tau\,\pi d\,x .
$$

So the stress builds up linearly from the end:

$$
\sigma(x)=\frac{4\tau x}{d}.
$$

The fibre just reaches $\sigma_f^*$ at its midpoint, $x=l_c/2$, when

$$
\sigma_f^*=\frac{4\tau}{d}\cdot\frac{l_c}{2}=\frac{2\tau l_c}{d},
$$

which gives

$$
l_c=\frac{\sigma_f^*d}{2\tau}.
$$

![[materials_critical_fibre_length.png|900]]

At exactly $l_c$ the stress profile is a triangle, so the average stress along the fibre is only half the peak (ll. 124–126). A longer fibre breaks in the middle and its pieces line up as a series of critical lengths (ll. 120–123). A fibre shorter than $l_c$ can never be loaded to its breaking stress: it pulls out instead (l. 131). For a fibre of length $l>l_c$ the build-up zones at each end total $l_c$, so the average stress is

$$
\bar\sigma=\sigma_f^*\left(1-\frac{l_c}{2l}\right),
$$

which reaches 97 % of $\sigma_f^*$ at $l=15l_c$, the rule of thumb above which end effects are negligible and the rule of mixtures can be used (ll. 127–128). Even then, short fibres are hard to align, because they are flowed into the shape (ll. 129–130).

## 5. Manufacturing composites

The manufacturing route decides a composite's quality, its defects and its cost, and cost here means the raw materials, expensive equipment, time and skilled labour, and the disposal or recycling cost at end of life (ML6a, ll. 23–36). A composite is made in situ: the material and the structure are made at the same time (ML5b, ll. 154–158; ML6a, ll. 36–37). The detail is in a third-year module, and the extra videos posted are not examinable (ML6a, ll. 8–23).

Hand lay-up is the craft route (ll. 37–94). A gel coat is laid in the mould to give a good outer surface and stop stray fibres; dry reinforcement cloth is laid on; resin is poured on and spread with a roller, which also drives out trapped air; excess resin is scraped away. People are flexible and can make complex shapes a production line cannot, and the South Coast has many small composite firms built on that skill, but the process is slow, operator-dependent and not very reproducible, and the part has high void content and resin-rich areas. It is cheap, simple and easy to change. A tennis-racket handle shows a semi-automated version: strips of graphite and glass are rolled round a tube, placed in a heated mould and inflated against it (ll. 55–72).

Pultrusion is automated and fast (ll. 95–106): fibres from creels are pulled through a resin bath and then through a heated die that sets the cross-section, giving well-aligned fibres but only constant sections such as pipes and I-beams. Resin transfer moulding injects mixed resin into a dry preform held in a closed two-part mould, with an outlet for the excess, and cures it there, possibly with some heat (ll. 106–128). The controlled pressure and flow give better infiltration and quality and large parts, but the moulds are expensive, so it needs enough production volume; a dinghy hull is a typical use.

Autoclave moulding is the aerospace route (ll. 128–151). Prepreg, cloth already impregnated with partially cured resin and stored in a freezer so the cure does not advance, is laid up on a one-part mould and covered by release and breather layers and a sealed vacuum bag. In the autoclave, heat completes the cure while vacuum and pressure squeeze out gas and excess resin, giving void contents below 1 %. Compression moulding uses heated, closed two-part moulds instead, for parts such as helicopter or wind-turbine blades; it consolidates well with low voids but costs more than the one-part vacuum-bag mould (ll. 151–161). Filament winding draws resin-wet fibre helically, circumferentially or round the poles of a mandrel, quickly and with high fibre fraction and low voids (ll. 161–192). It makes pipes and pressure vessels, such as carbon wound over a thin aluminium liner for compressed natural gas, high-pressure hydrogen or breathing-apparatus oxygen, but the shapes are limited and the mandrel can be hard to remove.

Across all routes the quality problems are voids and resin-rich areas of locally low fibre fraction, and the fibre–matrix interface, controlled by the fibre "sizing" treatment that manufacturers keep to themselves (ll. 193–209). See [[Composite Manufacturing Routes]].

## 6. Choosing composites, and why aerospace is cautious

A hockey stick can be made from wood, a natural composite of cellulose and lignin machined from a block; from aluminium, cast and then heat-treated; or from strips of graphite and glass rolled into a tube and moulded and cured (ML6b, ll. 2–13). All three can work; the choice is about cost, processing and recycling as much as properties.

Aerospace is conservative, heavily regulated and safety-conscious, and the hardest thing for regulators to accept about composites was how their failure could be monitored (ll. 14–16). A damaged laminate does not grow one crack. It develops transverse cracks through plies, delaminations between them and, at failure, extensive fibre breakage and pull-out, with interfacial energy absorbed all along (ll. 17–26). The damage-tolerant Paris-law lifing used in the tutorials and exams depends on one crack growing predictably, and $K$ assumes a simple crack-tip field; neither applies (ll. 27–32). The result has been under-confidence: large safety factors, structures thicker than they need be, and composites over-engineered and not used to their full potential (ll. 33–37). A small coupon test cannot predict a large, complex structure with varying load paths (ll. 38–42), and decisions about where and from what an aircraft is made are partly political, since governments support the industry (ll. 44–52).

Much composite damage is also internal. **Barely visible impact damage** leaves a mark that looks trivial while ply cracks and delaminations spread underneath (ll. 69–71). X-ray computed tomography, in which Southampton's μ-VIS centre specialises, shows it in three dimensions (ll. 72–90).

Very large parts need new routes: the A380's rear pressure bulkhead in one piece of CFRP was too big and too expensive for prepreg and an autoclave, so resin film infusion was developed (ll. 91–95). Sandwich panels get round the poor through-thickness properties of laminates: thin composite skins on a thick, light core of aluminium or Nomex honeycomb or foam give very high bending stiffness for little mass, with the core's compression and shear resistance set by its cell density and geometry (ll. 96–119). Natural structures such as shells and insect wings use the same ideas economically, and engineers copy them, biomimetics (ll. 120–137).

## 7. Seeing inside composites

The ML10b research talk shows why composites need a different approach from metals (ML10b). X-ray CT rotates a sample in front of a fixed high-energy source, takes a series of radiographs and reconstructs a three-dimensional image whose contrast comes from density and chemistry; in-situ loading during scanning gives time-resolved "4D" studies, down to tens of nanometres (ll. 12–68).

Two composite examples stand out. A filament-wound pressure vessel, an aluminium liner with a composite overwrap for a firefighter's breathing apparatus or for hydrogen storage, was dropped and looked almost undamaged, but CT showed cracking in the composite and a dent in the liner, which then flexes and fatigues each time the vessel is filled (ll. 86–103). And because a metal coupon can predict how the metal behaves in an airframe while a composite coupon cannot, composites are tested through a pyramid of scales: coupons, elements such as a stiffener, stiffened panels, sub-components and often the whole wing, at great expense (ll. 103–118).

![[materials_composite_test_pyramid.png|750]]

CT lets researchers validate damage models at each level instead. A notched coupon loaded to 30 % of its strength shows ply cracks, then a 0° split and delamination as the load rises (ll. 142–153); individual fibre breaks can be counted and compared with statistical models of fibre strength (ll. 155–165); and large glass-fibre wind-turbine laminates are full of voids, from which cracks grow and turn into delaminations (ll. 166–175). Burst tests of the pressure vessels, monitored by acoustic emission, located fibre breaks in the inner hoop wrap and delamination in the helical wrap (ll. 176–193). Barely visible impact damage from dropped tools, lightning or bird strike matters most for strength in compression after impact (ll. 194–198).

## Worked examples

All numbers recomputed in Python.

### Stiffness of a glass composite along and across the fibres

2013-14 B2(v): 60 % glass fibres ($E_f=72.5$ GPa) in a resin with $E_m=4$ GPa. Along the fibres,

$$
E_L=0.6\times72.5+0.4\times4=43.5+1.6=45.1\text{ GPa}.
$$

Across them,

$$
\frac{1}{E_T}=\frac{0.6}{72.5}+\frac{0.4}{4}=0.00828+0.1000=0.1083\text{ GPa}^{-1},
$$

$$
E_T=9.24\text{ GPa}.
$$

The fibres carry $P_f/P_m=0.6\times72.5/(0.4\times4)=27$ times the matrix load, 96 % of the total. 2014-15 B2(iii) repeats it with 55 % carbon (325 GPa) in epoxy (3.1 GPa): $E_L=180$ GPa and $E_T=6.81$ GPa, a ratio of 26. A cross-ply, quasi-isotropic lay-up or woven fabric would trade some of $E_L$ for more balanced properties.

### Fibre fraction for a dinghy keel

2015-16 B2(iv): the keel needs $E\ge63$ GPa and $\sigma\ge1.45$ GPa, with an epoxy of 3.1 GPa and 0.07 GPa.

| Fibre ($E_f$ GPa, $\sigma_f$ GPa) | $V_f$ for stiffness | $V_f$ for strength | Governs |
|---|---:|---:|---|
| Aramid (124, 3.5) | 0.495 | 0.402 | 0.50 |
| Glass (72, 3.5) | 0.869 | 0.402 | 0.87, impractical |
| Carbon (325, 3.8) | 0.186 | 0.370 | 0.37, strength governs |

For carbon, for example, $V_f=(63-3.1)/(325-3.1)=0.186$ for stiffness and $(1.45-0.07)/(3.8-0.07)=0.370$ for strength. Carbon needs the lowest fraction and gives the lightest, stiffest keel. Aramid is feasible but weak in compression, which matters for a keel in bending.

### Choosing a tie or a strut

MT3 Q5 (the same as 2014-15 Table QB2), with the Green Book's misprinted rows corrected:

| | UTS (MPa) | $E$ (GPa) | $\rho$ (g/cm³) | $\sigma/\rho$ | $E/\rho$ | $E^{1/2}/\rho$ |
|---|---:|---:|---:|---:|---:|---:|
| CFRP | 1500 | 220 | 1.7 | 882 | 129 | 8.72 |
| GFRP | 990 | 45 | 2.2 | 450 | 20.5 | 3.05 |
| Steel | 1000 | 207 | 7.8 | 128 | 26.5 | 1.84 |
| Al alloy | 550 | 71 | 2.8 | 196 | 25.4 | 3.01 |
| Ti alloy | 1100 | 120 | 4.5 | 244 | 26.7 | 2.43 |

CFRP wins as a tie on both indices and as a buckling strut. Steel, aluminium and titanium have almost the same $E/\rho$, so among metals lightweighting is about strength, toughness and temperature, not stiffness. The catch for CFRP in compression is that its compressive strength, limited by fibre microbuckling and delamination, is well below its tensile strength.

![[materials_specific_property_map.png|700]]

### How long must a chopped fibre be?

Illustrative, not lecturer-set: a carbon fibre with $d=7$ μm and $\sigma_f^*=3.5$ GPa in a matrix whose interface carries $\tau=50$ MPa has

$$
l_c=\frac{3.5\times10^9\times7\times10^{-6}}{2\times50\times10^6}=0.245\text{ mm},
$$

so fibres need to be about $15l_c\approx3.7$ mm long before they behave like continuous ones.

## Transcript slips

> [!warning] Mini-lectures ML5a–ML6b and ML10b
> | Where | Transcript says | Correct |
> |---|---|---|
> | ML5a, ll. 37–38 | "Wilson Unit Maritime Technology … WMTIA" | Wolfson Unit for Marine Technology and Industrial Aerodynamics (WUMTIA) |
> | ML5a, l. 65 | "radar and lines" | radar and mines |
> | ML5a, l. 85 | "sports UV cars" | SUVs |
> | ML5a, l. 127 | "Aston Monat DB9 … made by Guret" | Aston Martin DB9; the bonnet maker is Gurit |
> | ML5b, l. 86 | "tungsten boroid carbide substrate" | a tungsten boride core, formed where the boron reacts with the tungsten wire |
> | ML5b, l. 92 | carbon fibres "made by a physical vapor deposition or chemical vapor deposition process" | carbon fibres are made by pyrolysing a precursor fibre (PAN or pitch); vapour deposition is the boron-fibre route just described |
> | ML5b, l. 161 | "fire redundancy" | fire retardancy |
> | ML5b, l. 176 | "chopped stram" | chopped strand |
> | ML5b, ll. 181–187 | unrelated sentences | transcription noise after the lecture ends |
> | ML5c, l. 39 | "will save you the same stress" | will see the same stress |
> | ML5c, l. 45 | "Feature 05" | FEEG2005 |
> | ML5c, l. 117 | "longer than that effective fibre length" | longer than the critical fibre length |
> | ML6a, ll. 95, 101, 104, 197 | "pole trusion", "protruding" | pultrusion, pultruding |
> | ML6a, l. 103 | "the links that you actually want" | the lengths |
> | ML6a, l. 126 | "dinghy hole … any of you that sell" | dinghy hull … any of you that sail |
> | ML6a, ll. 138–141 | the peel ply "absorbs any excess resin" | the peel ply is a release layer that peels off cleanly; the bleeder/breather layers above it absorb resin and let air out |
> | ML6b, l. 28 | "parasol lifing" | Paris-law lifing |
> | ML6b, l. 98 | "summage panels" | sandwich panels |
> | ML6b, l. 137 | "bianimetic" | biomimetic |
> | ML10b, l. 3 | "turban machinery" | turbomachinery |
> | ML10b, l. 31 | "transparent to them like brilliant" | like beryllium |
> | ML10b, l. 160 | "a viable statistics assumption" | Weibull statistics |
> | ML10b, l. 189 | "acoustic admission" | acoustic emission |

## Links

- Parent: [[SESA2028 Aerospace Materials & Structures Hub]]
- Previous: [[SESA2028 M3 - Corrosion, Wear and Surface Engineering]] · Next: [[SESA2028 M5 - Metal and Ceramic Matrix Composites and Hybrid Laminates]]
- Concepts: [[Specific Stiffness and Strength]] · [[Rule of Mixtures]] · [[Critical Fibre Length]] · [[Composite Manufacturing Routes]]
- Tutorial: [[SESA2028 Materials Tutorial MT3 - Lightweighting Solutions]] · [[SESA2028 Materials Selection and Comparison Tables]]
- Structures: [[Euler Buckling]] (the strut index) · [[SESA2028 S10 - Thick Cylinders and Shrink Fits]] (wound pressure vessels)
- Past papers: [[FEEG2005 Exam 2013-14 Solutions]] (B2) · [[FEEG2005 Exam 2014-15 Solutions]] (B2) · [[FEEG2005 Exam 2015-16 Solutions]] (B2)

## Sources

- Lightweighting 2025 slides, lecture blocks 5 and 6
- Mini-lecture transcripts ML5a (intro to lightweighting), ML5b (composite basics), ML5c (composite anisotropy), ML6a (composites manufacture), ML6b (choosing composites), ML10b (3D evaluations of composite failures)
- Worked numbers from the MT3 tutorial and past papers, recomputed in Python

## Self-study tasks

No problems were set in these mini-lectures. ML5c (l. 21) flags the rule of mixtures as an exam favourite and ML5c (ll. 44–46) points back to the Part 1 video on it; the rest is exercised in tutorial MT3.

### Core

- [ ] Derive both rules of mixtures and the load-sharing ratio (ML5c, ll. 21–44). → [[#3. Anisotropy and the rule of mixtures]]
- [ ] Longitudinal and transverse stiffness of the 60 % glass composite (2013-14 B2(v)). → [[#Stiffness of a glass composite along and across the fibres]]
- [ ] Fibre fraction for the dinghy keel (2015-16 B2(iv)). → [[#Fibre fraction for a dinghy keel]]
- [ ] Tutorial MT3 Q2 and Q5. → [[SESA2028 Materials Tutorial MT3 - Lightweighting Solutions]]

### Further practice

- [ ] Derive the critical fibre length and explain why short fibres pull out (ML5c, ll. 95–133). → [[#4. Short fibres and the critical length]]
- [ ] Compare hand lay-up, RTM, autoclave and filament winding for quality, cost and shape (ML6a). → [[#5. Manufacturing composites]]
- [ ] Explain why composites cannot be lifed with $K$ and the Paris law, and how they are tested instead (ML6b, ll. 14–42; ML10b, ll. 103–118). → [[#6. Choosing composites, and why aerospace is cautious]] · [[#7. Seeing inside composites]]
