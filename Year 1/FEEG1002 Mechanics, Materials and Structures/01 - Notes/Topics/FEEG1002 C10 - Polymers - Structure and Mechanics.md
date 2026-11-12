---
title: "FEEG1002 C10 - Polymers - Structure and Mechanics"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part C: Materials"
order: 25
tags: [feeg1002, materials, polymers, glass-transition, crystallinity, viscoelasticity, stress-relaxation]
aliases: ["Materials Lectures 15 and 16", "Polymer structure and types", "Polymer mechanics"]
date: 2026-11-05
status: lectured
coverage: "Materials L15 (26 Nov 2024, ll. 1–639): polymer chains and side groups, van der Waals bonding between chains, entanglement, linear, branched, cross-linked and network architectures, number- and weight-average molecular weight, UHMWPE, amorphous and crystalline polymers, the glass transition, spherulites, elastomers and thermosets. Materials L16 (2 Dec 2024, ll. 1–870): stress–strain behaviour below Tg, between Tg and Tm and near Tm, stable neck growth and whitening, semi-crystalline deformation, elastomers and thermosets compared, creep and stress relaxation, the spring–dashpot model, the relaxation modulus against temperature, and damping. Slide decks 16 and 17 in full."
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: ["[[FEEG1002 C1 - Atoms and Bonding]]", "[[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation]]"]
next_topics: ["[[FEEG1002 C11 - Ceramics and Composites]]"]
key_concepts: ["[[Polymer Glass Transition and Viscoelasticity]]"]
tutorial_sheets: ["[[FEEG1002 Materials Tutorial 5 - Polymers, Ceramics and Composites Solutions]]"]
sources: ["02 - Sources/Materials/Lectures/Lecture 16 - Polymer Structure and Types.pdf", "02 - Sources/Materials/Lectures/Lecture 17 - Polymer Mechanics.pdf", "02 - Sources/Lectures/FEEG1002 Lecture 15.txt", "02 - Sources/Lectures/FEEG1002 Lecture 16.txt", "02 - Sources/Materials/Tutorials/Tutorial Sheet 05 - Polymers Ceramics Composites.pdf"]
---

# FEEG1002 C10 - Polymers - Structure and Mechanics

> [!abstract] Summary
> A polymer is made of very long chain molecules with strong covalent bonds along each chain but only weak van der Waals forces between chains, so its mechanical behaviour is governed by how easily the chains slide past each other. That depends on chain length, side groups, entanglement, branching, cross-linking and crystallinity, and above all on temperature: below the glass transition temperature $T_g$ chain sliding is prevented and the polymer is brittle, between $T_g$ and $T_m$ it yields and cold-draws with a stable neck, and near $T_m$ it flows. Because sliding takes time, thermoplastics are viscoelastic: they creep at constant stress and relax at constant strain, $\sigma(t)=\sigma_0e^{-t/\tau}$, and the lag between stress and strain gives them damping.

> [!summary]- Exam use: quick path
> - **Use it when:** a question asks for the stress–strain curve of a polymer at a given temperature relative to $T_g$ and $T_m$, why a neck propagates stably, the difference between thermoplastics, elastomers and thermosets, how crystallinity changes properties, or a stress-relaxation calculation.
> - **Assumptions:** chain sliding is the deformation mechanism; below $T_g$ it is treated as prevented; stress relaxation is a single exponential with one relaxation time $\tau$.
> - **Method:** 1. Place the test temperature relative to $T_g$ and $T_m$. 2. Below $T_g$: linear elastic to brittle fracture. Between $T_g$ and $T_m$: yield, stable neck, cold drawing, then fracture. Near $T_m$: viscous flow at low stress. 3. For relaxation, $\ln(\sigma/\sigma_0)=-t/\tau$: one data pair gives $\tau$, then any other time or stress follows. 4. $E_r(t)=\sigma(t)/\varepsilon_0$. 5. Crystallinity raises stiffness, strength and $T_m$; cross-linking turns a thermoplastic into an elastomer (light) or a thermoset (full).
> - **Common mistakes:** treating $\tau$ as the time for complete relaxation (it is the time to fall to $1/e$, 37 %); asking for "the" modulus of a polymer without a time and temperature.
> - **Practise:** [[#Worked example - stress relaxation in a polymer seal]] · [[FEEG1002 Materials Tutorial 5 - Polymers, Ceramics and Composites Solutions]] Q1–Q3

Polymers behave so differently from metals that the dislocation picture does not apply. There are no crystal planes to slip on, or at least none that matter; a thermoplastic deforms by whole molecules sliding past one another, and what resists them is the weak secondary bonding between chains from [[FEEG1002 C1 - Atoms and Bonding#4. Secondary bonding|C1]], not the strong covalent bonds along each chain (L15, ll. 80–102). The chains are strong along their length, but the solid holds together only because they are tangled and weakly bonded to each other, so pulling one drags its neighbours along.

Everything about polymer mechanics follows from how hard it is to make those chains slide. Long chains tangle more. Side groups on the chain change how strongly neighbouring chains attract. Lining chains up side by side, crystallinity, makes them attract much more strongly. Tying them together with covalent cross-links stops sliding altogether. And temperature changes the strength of the van der Waals forces themselves, which is why the same polymer can be brittle in the cold, tough at room temperature and runny when hot.

Sliding also takes time. A weight left on a plastic shelf makes it sag a little more each week, and a rubber band stretched round a parcel slowly loses tension. This time dependence is viscoelasticity, and it is what makes polymers good at damping vibration.

---

## 1. Polymer chains

### Monomers and the backbone

A **polymer** is made of very long chain molecules, mostly hydrocarbons, built by joining many small repeat units, the **monomers** (slide "Linear Molecules"; L15, ll. 20–58). Along the chain the carbon atoms of the **backbone** are joined by strong covalent C–C bonds, with hydrogen (or other atoms) covalently bonded to the sides. Polyethylene, the simplest, is a chain of CH₂ units: food wrap and bottles. Other linear polymers replace some hydrogen atoms with other atoms or **side groups** (L15, ll. 59–79):

- replacing every H with F gives polytetrafluoroethylene, **PTFE**;
- replacing one H per monomer with Cl gives polyvinyl chloride, **PVC** (electrical tape);
- replacing one H per monomer with a methyl group, CH₃, gives polypropylene, **PP**.

The side groups change how strongly neighbouring chains interact, and so change the properties.

### Chain shape and entanglement

Each carbon atom bonds tetrahedrally, so successive C–C bonds meet at about 109°, and each bond can rotate around a cone at that angle (slide "Polymer Chains"; L15, ll. 103–142). A long chain therefore does not lie straight; it wanders in three dimensions, and in the solid the chains are long, tortuous and entangled. An **amorphous** polymer is this tangle, with no long-range order. Entanglement and the van der Waals forces between chains together resist sliding, and the longer the chains, the more they tangle and the harder sliding becomes.

### Chain architecture

Chains can be arranged in four ways, each restricting sliding more than the last (slide "Polymer chain types"; L15, ll. 143–175). **Linear** chains are the usual thermoplastics. **Branched** chains have side chains growing off the main chain, which add entanglement and hinder sliding. **Cross-linked** chains are joined to their neighbours at intervals by covalent bonds, and light cross-linking gives an elastomer. **Network** polymers, the thermosets, are joined in a complete three-dimensional covalent network in which nothing can slide.

![[m10_chain_architectures.png|900]]

### Molecular weight

A polymerisation reaction does not make chains all of one length. The chain lengths follow a skewed, bell-shaped distribution with a long tail of very long chains (slide "Chain Length, Molecule Weight"; L15, ll. 176–239). Two averages describe it. Divide the chains into size ranges, with $M_i$ the mean molecular weight of range $i$. The **number-average molecular weight** weights each range by the number fraction $x_i$ of chains in it:

$$
\bar M_n=\sum x_iM_i
$$

The **weight-average molecular weight** weights each range by the weight fraction $w_i$ of the material in it:

$$
\bar M_w=\sum w_iM_i
$$

A chain's share of the weight is proportional to its number times its molecular weight, $w_i=x_iM_i/\sum x_jM_j$, so heavy chains count for more in $\bar M_w$, which is always at least $\bar M_n$. A few very long chains barely move the number average but drag the weight average up a long way, because they are a small share of the molecules but a large share of the mass.

Longer chains mean more entanglement, more resistance to deformation, a higher tensile strength and a higher melting temperature (L15, ll. 240–272). Ultra-high molecular weight polyethylene, **UHMWPE**, with chains of well over 100 000 repeat units, is so wear resistant that it is used for the bearing surface of joint replacements, running against a hard metal or ceramic counterface.

## 2. Crystallinity and the glass transition

### Polymer crystallinity

A polymer can never form a simple crystal like a metal, but segments of chains can line up side by side and pack in a regular way: **polymer crystallinity** (slides "Polymer Crystallinity"; L15, ll. 273–333, 402–487). The chains in a crystalline region are packed much more closely, so the van der Waals bonding between them is much stronger. Because chains have different lengths and are tangled, they can never all pack completely, so crystallisation is only partial: a **semi-crystalline** polymer has small crystalline regions in an amorphous matrix. Small, regular chains crystallise most easily. Crystalline regions raise the stiffness, the strength and the melting temperature, because sliding there is much harder. The usual crystalline structure is the **spherulite**: from a nucleus, ribbons of chain-folded lamellar crystallites grow outwards like spokes, with amorphous polymer between them, until neighbouring spherulites meet, rather like grains in a metal. Under crossed polarised light each spherulite shows a Maltese-cross pattern.

### Specific volume and the two transitions

The specific volume (volume per unit mass) of a polymer cooled from the melt separates the three structures (slide "Polymer Crystallinity"; L15, ll. 293–333). A crystalline polymer shows a sudden drop in volume at the melting temperature $T_m$, as the chains pack into ordered regions. An amorphous polymer shows no step at $T_m$; it contracts steadily, and at a lower temperature, the **glass transition temperature** $T_g$, the slope of the curve decreases, as the chains stop moving. A semi-crystalline polymer shows both: a smaller drop at $T_m$ and a change of slope at $T_g$.

![[m10_specific_volume.png|900]]

### The glass transition

The glass transition is the key temperature for amorphous and semi-crystalline thermoplastics (slide "Tg: Glass Transition Temperature"; L15, ll. 334–401). Van der Waals forces are weak electrostatic forces that increase as the temperature falls: as a polymer cools, its chains vibrate less and contract closer together, and the attraction between them grows. Below $T_g$ it is strong enough to prevent chain sliding. With little chain sliding there is little plastic deformation and little energy is absorbed on impact, so below $T_g$ a thermoplastic is brittle; above it, sliding is possible and the polymer can deform. The change is gradual as $T_g$ is approached, rather like the ductile-to-brittle transition in BCC metals ([[FEEG1002 C8 - Fracture - Brittle, Ductile and Fracture Mechanics#5. The ductile-to-brittle transition|C8]]).

The leading edges of wind-turbine blades in northern Canada show why it matters. The protective coating had a $T_g$ of about −8 °C, but the blades ran at −30 to −40 °C, so the coating was glassy and brittle; it could not absorb the impacts of ice particles at the high tip speeds and eroded rapidly. The fix was a coating with a much lower $T_g$. Blending polymers is one way to tune $T_g$.

## 3. Thermoplastics, elastomers and thermosets

**Thermoplastics** are made of linear (or branched) chains that are not cross-linked. They deform by chain sliding, which is easier at higher temperatures, and they soften on heating and can be remelted, moulded and recycled (slide "Chain Length, Molecule Weight"; L15, ll. 88–92).

**Elastomers** are lightly cross-linked, so chain sliding, and therefore deformation, is still possible, but the relative positions of the chains are lightly pinned (slide "Elastomers"; L15, ll. 488–562). Their chains prefer to be coiled, because a coiled chain can adopt far more arrangements than a straight one: it has higher entropy. Stretching straightens the chains easily at first, then the cross-links stop further extension; release the load and the chains coil up again and the elastomer returns to its original shape. Rubbers are effectively **entropy springs**, storing energy as they are stretched.

**Thermosets** (thermosetting plastics) are made by mixing a resin with a hardener, which drives cross-linking into a three-dimensional network of covalent bonds (slide "Thermosetting Plastics"; L15, ll. 563–612). The chains cannot slide, so thermosets have higher stiffness and strength than thermoplastics and good dimensional stability, creeping very little. For the same reason they are brittle with poor impact properties, and they cannot be remelted: heated enough, the network is destroyed and they burn. That makes them hard to recycle, a problem for glass-fibre wind-turbine blades. Epoxies (the matrix of many composites) and Bakelite are thermosets.

## 4. Stress–strain behaviour and temperature

### Three regimes

Because chain sliding depends so strongly on temperature, the tensile behaviour of an amorphous or semi-crystalline thermoplastic depends on where the test temperature sits relative to $T_g$ and $T_m$ (slides "Polymers and Temperature", "Thermoplastic Deformation"; L16, ll. 38–209). Below $T_g$ chain sliding is largely prevented: the polymer is linear elastic, as the bonds and chains stretch, up to brittle fracture at low strain (some, such as PVC at 20 °C, still yield and cold-draw). Between $T_g$ and $T_m$, the normal service range, chain sliding is possible once a yield stress has overcome the inter-chain bonding, and the polymer yields, necks and **cold-draws** to large strains before failing. Close to but below $T_m$ the van der Waals forces are very weak, and the chains flow viscously at very low stress to very large strains; this is the regime used for vacuum forming, injection moulding and recycling.

![[m10_stress_strain_temperature.png|900]]

Time matters as well as temperature: slow loading gives the chains more time to rearrange and slip, so plastic flow is easier, and a slow test looks like a hotter one.

### Stable neck growth and cold drawing

In the cold-drawing regime the neck behaves quite differently from a metal's (slide "PVC deformation at 20 °C"; L16, ll. 210–354). The sequence is:

1. Elastic deformation, from stretching bonds and uncoiling chains.
2. Yield, when chains start to slide; this is not dislocation motion on crystal planes.
3. A neck forms. In the neck the tangled amorphous chains straighten out and align along the load, packing closer together.
4. Closer-packed chains attract more strongly, so the neck becomes stiffer and stronger than the material next to it. The load is transmitted effectively to the unnecked portion, whose tangled chains have a lower yield stress, so the shoulder of the neck yields next.
5. The neck therefore propagates along the specimen at roughly constant load, a **stable neck**, until the whole gauge length has been drawn; then the stress rises to fracture.

A metal neck keeps thinning in one place until it breaks; a polymer neck spreads. As the chains straighten, small voids open between them and the drawn region turns white and opaque, **stress whitening**: a polymer component that starts to go white is deforming plastically.

A semi-crystalline polymer follows the same overall curve at a higher stress (slide "Deformation Chain Behaviour, Semi-Crystalline"; L16, ll. 355–395). Its amorphous regions take the elastic stretch; at yield the crystalline lamellae break up into smaller crystalline blocks linked by amorphous tie regions, and these then align along the load and lock up until failure.

### Elastomers and thermosets compared

An elastomer stretches to very large strains at very low stress, stiffening as its chains straighten, until the cross-links lock and the stress rises sharply. A thermoset behaves like a thermoplastic below $T_g$: linear elastic to brittle fracture, generally at a higher stress (L16, ll. 434–471). The area under each curve is the energy absorbed per unit volume, and for an elastomer most of it is stored and returned when it springs back.

## 5. Viscoelasticity

### Creep and stress relaxation

Thermoplastics show **viscoelastic**, time-dependent deformation, which appears in two forms (slide "Viscoelastic Deformation"; L16, ll. 489–551): **creep**, increasing strain at constant load or stress, and **stress relaxation**, decreasing stress at constant strain. Both result from chain sliding, not diffusion as in the creep of metals ([[FEEG1002 C9 - Fatigue, Creep and Corrosion#2. Creep|C9]]). At the scale of the chains the stress is not uniform: where one chain curls round another the local stress is high, a van der Waals bond there breaks, the chain slides a little, and the load passes to another spot, which then gives in turn. Under constant load that sequence adds up to increasing strain; at constant strain it lets the stress fall.

### The stress-relaxation equation

A polymer held at a fixed strain relaxes in stress because chains slide, and the driving force for sliding is the stress itself; as the stress falls, so does the rate at which it falls (L16, ll. 552–571). Writing the rate as proportional to the current stress, with a constant $1/\tau$:

$$
\frac{d\sigma}{dt}=-\frac{\sigma}{\tau}
$$

Separate the variables:

$$
\frac{d\sigma}{\sigma}=-\frac{dt}{\tau}
$$

Integrate from $\sigma_0$ at $t=0$ to $\sigma(t)$ at time $t$:

$$
\int_{\sigma_0}^{\sigma(t)}\frac{d\sigma}{\sigma}=-\frac1\tau\int_0^tdt
$$

$$
\ln\frac{\sigma(t)}{\sigma_0}=-\frac{t}{\tau}
$$

$$
\boxed{\sigma(t)=\sigma_0\exp\left(-\frac{t}{\tau}\right)}
$$

where $\sigma_0$ is the original stress, $\sigma(t)$ the stress at time $t$ and $\tau$ the **relaxation time** (slide "Viscoelastic Deformation"). After a time $\tau$ the stress has fallen to $1/e$, 37 %, of its original value; after $2\tau$ to 13.5 %. The stress never reaches zero, so $\tau$ is a time constant, not the time for complete relaxation. The logarithmic form gives $\tau$ directly from one measurement: $\tau=-t/\ln(\sigma/\sigma_0)$.

![[m10_stress_relaxation.png|900]]

### The spring–dashpot model

Viscoelastic behaviour is modelled with springs and dashpots (L16, ll. 572–645). A spring is elastic: it extends at once in proportion to the load and springs back. A **dashpot** is a piston in a cylinder of viscous fluid, like the plunger of a cafetière: under a fixed stress it moves at a steady rate, and when the stress is removed it stops where it is. The model combines springs with a dashpot. Under a fixed stress the springs give an instantaneous elastic strain; then the stretched spring slowly drives the dashpot and the strain keeps growing with time, which is creep. When the stress is removed the elastic strain is recovered at once; then the spring slowly pulls the dashpot back, a delayed **viscoelastic recovery**.

![[m10_creep_recovery.png|900]]

### The relaxation modulus

Since the stress at constant strain depends on time, so does the apparent stiffness. The **relaxation modulus** is

$$
E_r(t)=\frac{\sigma(t)}{\varepsilon_0}
$$

where $\sigma(t)$ is the measured time-dependent stress and $\varepsilon_0$ the strain held constant (slide "Stress Relaxation: Relaxation Modulus"; L16, ll. 646–672). It is not a material constant like Young's modulus: it depends on the time at which it is measured and, strongly, on temperature, since heating speeds up relaxation.

Plotting $\log E_r$ at a fixed time (say 10 s) against temperature maps out the behaviour of an amorphous thermoplastic in five regions (slide "Relaxation modulus vs. Temperature"; L16, ll. 673–755). Below $T_g$ the polymer is **glassy**, with no molecular sliding, and $E_r$ is high, about that of a glass. Around $T_g$ it is **leathery**: deformation is viscoelastic and time-dependent, and $E_r$ falls steeply. Many polymers are used here. Above the transition the curve levels out in the **rubbery** region, where the polymer behaves like an elastomer but is held only by entanglements rather than cross-links. Heating further gives **rubbery flow**, with elastic and viscous components both present, and finally **viscous flow**, with independent chain motion, rotation and vibration, in which $E_r$ falls to very low values.

A highly crystalline polymer keeps a high $E_r$ up to a higher melting temperature, with only a small dip at $T_g$ from its remaining amorphous regions, because its crystalline regions block chain sliding: crystalline polymers are stiffer and stronger.

![[m10_relaxation_modulus.png|900]]

### Damping

Because strain lags behind stress in a viscoelastic material, part of the energy put in on each loading cycle is dissipated rather than returned. This time-dependent, **anelastic** behaviour gives polymers their **damping** capacity (slides "Damping Properties", "Damping in Polymers"; L16, ll. 756–835). A spring returns all its energy; a viscoelastic material keeps moving after the load has gone, and the offset turns vibration into heat. A road surfaced with asphalt, whose bituminous binder is viscoelastic, is noticeably quieter than a concrete one.

Damping needs mobile chains. Thermosets, with their rigid three-dimensional networks, have low damping. Thermoplastics have high damping between $T_g$ and $T_m$, where the chains are mobile, and it peaks around $T_g$. The temperature range of high damping can be widened by mixing amorphous polymers with different values of $T_g$, or by copolymerising suitable monomers.

---

## Worked examples

### Worked example - number and weight averages

A polyethylene has chains in six size ranges with mean molecular weights $M_i=5$, 15, 25, 35, 45 and 55 kg/mol and number fractions $x_i=0.05$, 0.16, 0.22, 0.27, 0.20 and 0.10. Find $\bar M_n$ and $\bar M_w$, then see what happens if 1 % of the chains (by number) are replaced by very long chains of 1000 kg/mol.

$$
\bar M_n=\sum x_iM_i=0.05(5)+0.16(15)+0.22(25)+0.27(35)+0.20(45)+0.10(55)=32.1\ \mathrm{kg/mol}
$$

The weight fractions are $w_i=x_iM_i/\bar M_n$: 0.008, 0.075, 0.171, 0.294, 0.280, 0.171 (summing to 1). Then

$$
\bar M_w=\sum w_iM_i=37.8\ \mathrm{kg/mol}
$$

With the 1 % of very long chains added (and the others scaled to 99 %), $\bar M_n$ rises to 41.8 kg/mol, but $\bar M_w$ jumps to 268 kg/mol, because those few chains now hold 24 % of the weight. The number average follows the typical chain; the weight average is dragged by the heavy tail.

> [!check] Number of repeat units
> A polyethylene repeat unit, C₂H₄, has a molar mass of 28 g/mol, so the original $\bar M_n=32.1$ kg/mol corresponds to about $32\,100/28=1100$ repeat units per chain. UHMWPE, at several million g/mol, has over 100 000.

### Worked example - stress relaxation in a polymer seal

A thermoplastic seal is compressed to a fixed strain of 0.02, giving an initial stress of 6 MPa, and its relaxation time at the service temperature is 500 h. Find the stress and the relaxation modulus after 1000 h, and when the stress falls to half its initial value.

$$
\sigma(1000)=6\exp\left(-\frac{1000}{500}\right)=6e^{-2}=0.81\ \mathrm{MPa}
$$

$$
E_r(0)=\frac{6}{0.02}=300\ \mathrm{MPa},\qquad E_r(1000\ \mathrm h)=\frac{0.81}{0.02}=41\ \mathrm{MPa}
$$

For half the initial stress, $\sigma/\sigma_0=0.5$:

$$
t=-\tau\ln0.5=500\times0.693=347\ \mathrm h
$$

After about two weeks the seal pushes back with only half its original force, and after six weeks with 13.5 %, which is why polymer seals and bolted polymer joints lose their preload and leak. A seal that runs hotter has a shorter $\tau$ and loses its force sooner.

---

## Links

- Parent: [[FEEG1002 Mechanics, Materials and Structures Hub]] · Previous: [[FEEG1002 C9 - Fatigue, Creep and Corrosion]] · Next: [[FEEG1002 C11 - Ceramics and Composites]]
- Concept: [[Polymer Glass Transition and Viscoelasticity]] · [[Atomic Bonding and Interatomic Potential]]
- Worked sheet: [[FEEG1002 Materials Tutorial 5 - Polymers, Ceramics and Composites Solutions]] (Q1–Q3) · Formula list: [[FEEG1002 Formula Sheet]]
- Used again in: [[FEEG1002 C11 - Ceramics and Composites|C11]] (thermoset and thermoplastic matrices) · [[FEEG1002 D6 - Single Degree of Freedom Vibration|D6]] (damping in vibrating systems)
- Year 2: [[SESA2028 M4 - Polymer Matrix Composites]]

## Sources

- `FEEG1002 Lecture 15.txt` (L15, 26 Nov 2024): chains and side groups (ll. 20–102), chain shape and entanglement (ll. 103–142), architectures (ll. 143–175), molecular weight (ll. 176–272), crystallinity and specific volume (ll. 273–333), the glass transition and the wind-turbine case (ll. 334–401), spherulites (ll. 402–487), elastomers (ll. 488–562), thermosets (ll. 563–612), summary (ll. 613–639).
- `FEEG1002 Lecture 16.txt` (L16, 2 Dec 2024): chain sliding and temperature (ll. 38–98), the three regimes (ll. 99–209), PVC and stable neck growth (ll. 210–354), semi-crystalline deformation (ll. 355–433), elastomers and thermosets (ll. 434–488), creep and stress relaxation (ll. 489–571), the spring–dashpot model (ll. 572–645), the relaxation modulus (ll. 646–755), damping (ll. 756–835).
- `Lecture 16 - Polymer Structure and Types.pdf` (slide deck 16) and `Lecture 17 - Polymer Mechanics.pdf` (slide deck 17). Figures after Callister and Ashby and Jones.
- `Tutorial Sheet 05 - Polymers Ceramics Composites.pdf`: Q1–Q3 on this note (Q4–Q7 belong to [[FEEG1002 C11 - Ceramics and Composites|C11]]).
- The derivation of $\sigma(t)$ from $d\sigma/dt=-\sigma/\tau$ makes the lecture's argument (the rate falls as the stress falls) quantitative. The molecular-weight distribution and the seal are illustrative numbers.

## Self-study tasks

### Core

- [ ] Tutorial 5, Q1: stress–strain curves of amorphous PP ($T_g=-10$ °C, $T_m=175$ °C) at −60, 21 and 120 °C, and why the neck is stable at 21 °C. → [[#4. Stress–strain behaviour and temperature]] · [[FEEG1002 Materials Tutorial 5 - Polymers, Ceramics and Composites Solutions#Q1 - Polypropylene at three temperatures]]
- [ ] Tutorial 5, Q2: why time matters, and how much longer a rubber takes to relax from 0.15 to 0.10 MPa. Target 33.8 h. → [[#The stress-relaxation equation]] · [[FEEG1002 Materials Tutorial 5 - Polymers, Ceramics and Composites Solutions#Q2 - Time dependence and stress relaxation]]
- [ ] Tutorial 5, Q3: how $E_r(t)$ varies with temperature for amorphous and more crystalline polymers. → [[#The relaxation modulus]] · [[FEEG1002 Materials Tutorial 5 - Polymers, Ceramics and Composites Solutions#Q3 - Relaxation modulus and crystallinity]]
- [ ] Explain the glass transition and why it matters in service, flagged as essential (L15, ll. 334, 357–363, 395–396). → [[#The glass transition]]

### Further practice

- [ ] Stretch an elastic band and explain what the chains are doing at each stage (L15, l. 552). → [[#3. Thermoplastics, elastomers and thermosets]]
- [ ] Work out $\bar M_n$ and $\bar M_w$ for a distribution with a heavy tail (suggested, not lecturer-set). → [[#Worked example - number and weight averages]]

## Transcript and slide slips

> [!warning] Transcript slips (L15, ll. 78, 108 and 587)
> Where: [[#Monomers and the backbone]] · [[#Chain shape and entanglement]] · [[#3. Thermoplastics, elastomers and thermosets]].
>
> Polypropylene is made by adding "a methane group"; it is a methyl group, CH₃. The C–C bond angle is first given as "190 degrees", then corrected to 109° (l. 136). Thermosets are said to show no creep (also on the slide, "No creep"); they creep far less than thermoplastics, but not at all is an overstatement.

> [!warning] Transcript slips (L16, ll. 213–218, 568–571, 692, 729–731 and 806–807)
> Where: [[#Stable neck growth and cold drawing]] · [[#The stress-relaxation equation]] · [[#The relaxation modulus]] · [[#Damping]].
>
> PVC at 20 °C is said to be "nicely between" $T_g$ and $T_m$; rigid PVC has a $T_g$ of about 80–87 °C, so at 20 °C it is below $T_g$, although it still yields and cold-draws, as the video shows. The relaxation time is described as "the time [it is] going to take to completely … relax"; it is the time constant for the stress to fall to $1/e$ of its starting value. The glassy region is said to have "very high stress relaxation"; it has a very high relaxation modulus, meaning very little relaxation. The colours on the $E_r$ plot are swapped at ll. 729–731: red is amorphous and green crystalline. On the M3, the road is said to be quieter on the concrete side; it is quieter on the asphalt side (as said at ll. 792–798).

> [!warning] Below Tg, "no chain sliding" (slides 16 and 17; L15, l. 617; L16, l. 85)
> Where: [[#The glass transition]].
>
> The course states that chain sliding is prevented below $T_g$. That is the working model; strictly, chain mobility is drastically reduced rather than zero, which is why glassy polymers still creep slowly. Use the course's statement in answers.
