---
title: "SESA2028 M7 - Steels - Phase Transformations, Heat Treatment and Alloying"
module: "SESA2028 Aerospace Materials & Structures"
type: topic
stream: "Materials"
order: 7
tags: [sesa2028, materials, steels, martensite, ttt, jominy, stainless, heat-treatment]
status: lectured
coverage: "Mini-lectures ML11a, ML11b, ML12a, ML12b, ML13a, ML13b and the worked exam question ML13c"
date: 2026-10-30
parent: ["[[SESA2028 Aerospace Materials & Structures Hub]]"]
prerequisites: ["[[SESA2028 M6 - Light Alloys - Aluminium, Magnesium, Beryllium and Titanium]]"]
next_topics: ["[[SESA2028 M8 - High Temperature Materials - Creep, Oxidation and Superalloys]]"]
key_concepts: ["[[Martensite]]", "[[TTT and CCT Diagrams]]", "[[Hardenability and Jominy Test]]", "[[Tempering]]", "[[Stainless Steel Classes]]"]
tutorial_sheets: ["[[SESA2028 Materials Tutorial MT4 - Alloy Design Solutions]]"]
sources: ["02 - Sources/Materials Lectures/Ferrous materials 2025.pdf", "02 - Sources/Materials Lectures/mini lecture videos/ML11a Introduction and Review of Steels_default.txt", "02 - Sources/Materials Lectures/mini lecture videos/ML11b Effects of cooling in steels_default.txt", "02 - Sources/Materials Lectures/mini lecture videos/ML12a TTT and CCT curves_ the Jominy test_default_30272847.txt", "02 - Sources/Materials Lectures/mini lecture videos/ML12b Controlling steel properties_default.txt", "02 - Sources/Materials Lectures/mini lecture videos/ML13a Alloying in Steels_default.txt", "02 - Sources/Materials Lectures/mini lecture videos/ML13b Stainless steels_default.txt", "02 - Sources/Materials Lectures/mini lecture videos/ML13c Steels example problem_default.txt"]
---

# SESA2028 M7 - Steels - Phase Transformations, Heat Treatment and Alloying

> [!abstract] Summary
> Steel is versatile because iron changes crystal structure on cooling, FCC austenite to BCC ferrite, and the carbon that austenite holds must go somewhere when it does. Cooled slowly, the carbon diffuses out to form ferrite and cementite (pearlite), as the phase diagram predicts. Cooled fast, it cannot, and the lattice shears to body-centred tetragonal martensite with the carbon trapped: very hard and brittle. TTT and CCT diagrams add the missing time axis and show the cooling rate needed to miss the pearlite nose; the Jominy test measures how easily a given steel forms martensite through a section (hardenability); tempering then lets some carbon out as fine carbides to restore toughness. Alloying moves all of this: austenite stabilisers and carbide formers shift the transformation curves, micro-alloy carbides refine the grain, and over about 12 % chromium makes steel stainless.

> [!summary]- Exam use: quick path
> - **Use it when:** asked what a heat treatment does to a steel, why a part cracked on quenching, how to get martensite through a thick section, how to read a TTT or Jominy curve, what an alloying element does, or which stainless steel to use.
> - **Assumptions:** equilibrium phase diagram for slow cooling only; TTT for isothermal holds, CCT for continuous cooling; martensite forms by shear, athermally, between $M_s$ and $M_f$.
> - **Method:** 1. Find the phase at the starting temperature from the Fe–C diagram. 2. Place the cooling path on the CCT/TTT diagram: pearlite, bainite or martensite. 3. For a real section, convert positions to Jominy distances and read the hardness. 4. Temper to trade hardness for toughness. 5. If the quench is too severe, raise hardenability (alloying, larger austenite grains) and use a gentler quench, or harden only the surface.
> - **Common mistakes:** treating hardenability as hardness (it is the ease of forming martensite); saying martensite formation depends on hold time (it depends on how far below $M_s$ you go).
> - **Example:** [[#A quench-cracked component]]. **Exercise:** [[SESA2028 Materials Tutorial MT4 - Alloy Design Solutions]], Q3.

Steels are everywhere because a huge range of properties is available cheaply: steel is made in bulk, with established supply chains, so even sophisticated grades are affordable, whereas niche materials are expensive to obtain. The range runs from low-carbon structural steel through high-strength low-alloy and quenched-and-tempered steels to tool steels and stainless steels. The phase diagram explains the equilibrium structures, but most of steel's versatility comes from heat treatment.

The Titanic's steel and the Liberty ships rushed out in the Second World War were low-quality, with sulphur and phosphorus that segregate to grain boundaries and embrittle them. Charpy tests show the difference: the temperature at which the impact energy falls to 27 J is about 42 °C longitudinally and 61 °C transversely for Titanic plate, about 23 °C for Liberty-ship steel, around −10 °C for steels of 1955–1980, about −35 °C on average for 1995 steels, and −18 °C for modern A36 ship plate. Grain-size control, low sulphur and phosphorus, and manganese to tie up the sulphur made the improvement ([[Ductile-Brittle Transition]]).

At high temperature iron is FCC and holds plenty of carbon in solution; at low temperature its stable structure is BCC, which holds almost none. Given time, carbon atoms diffuse out and gather into cementite. Denied time, the iron atoms make the change anyway by a sudden cooperative shear, with the carbon still inside, and the lattice is jammed into a strained, distorted shape. Quenching, hardenability, tempering and alloying all control that race between diffusion and cooling.

## 1. The iron–carbon diagram

A phase diagram is a temperature–composition map of the phases that are thermodynamically stable. The phases at the steel end are $\alpha$ ferrite, BCC, holding very little carbon (at most about 0.02 %), soft and ductile and, being BCC, subject to a ductile–brittle transition; $\gamma$ austenite, FCC, holding up to about 2 % carbon in solution, ductile and without a transition; and cementite, $\mathrm{Fe_3C}$, an intermetallic of fixed composition (6.67 % C), hard and brittle. The eutectoid reaction at 0.76 % C and 727 °C turns austenite into **pearlite**, alternating lamellae of ferrite and cementite; its many phase boundaries block dislocations, giving reasonable strength and lowish ductility. There is also a eutectic, liquid to $\gamma+\mathrm{Fe_3C}$, and a peritectic, liquid plus $\delta$ to $\gamma$, which goes from two phases to one.

![[materials_fe_c_eutectoid.png|850]]

The diagram assumes slow cooling, because the $\gamma\to\alpha$ change is a diffusional transformation: the carbon has to move out of the forming ferrite. A hypo-eutectoid steel (below 0.76 % C) cooled from the austenite field enters the $\alpha+\gamma$ field and forms pro-eutectoid ferrite first, on the austenite grain boundaries, which are disordered, energetically favourable sites and fast diffusion paths for the carbon being pushed out. The remaining austenite is enriched in carbon until, at 727 °C, it has the eutectoid composition and transforms to pearlite. The result is ferrite outlining the prior-austenite grains, with pearlite inside. A hyper-eutectoid steel forms pro-eutectoid cementite on the grain boundaries instead, then pearlite. The lever rule gives the amounts (not needed in Part 2 calculations; worked below to show the numbers).

## 2. Slow cooling: annealing and normalising

Annealing heats a steel above its upper critical temperature, into the single-phase austenite field, and then cools it very slowly, as happens in a very large component. That is the closest approach to the phase diagram: very slow cooling gives coarse pearlite and a soft, ductile steel. Normalising also heats above the upper critical temperature, often to relieve residual stresses from manufacturing, but then lets the part cool in air. The faster cooling gives finer grains and finer pearlite, so the steel is harder and less ductile than annealed.

## 3. Fast cooling: martensite

When a blacksmith plunges a hot blade into water and the cooling is fast enough, carbon has no time to diffuse, yet the iron still needs a structure suited to low temperature. It gets one by **coordinated shear**: the atoms move together at close to the speed of sound. Two FCC unit cells side by side contain a body-centred cell; squashing it along one axis makes a body-centred tetragonal (BCT) cell, the lattice of **martensite**, $\alpha'$. The carbon is trapped in solution, distorting the lattice further.

Many small shears in alternating directions accommodate the shape change, giving a very fine structure of laths, and the transformation strains generate many dislocations. So martensite is highly distorted, highly dislocated and full of trapped carbon: very hard and very brittle. It starts forming at the martensite-start temperature $M_s$ and is complete at $M_f$. The transformation is **athermal**: once triggered it happens at once, with no diffusion and no dependence on holding time; how much of the steel becomes martensite depends on how far below $M_s$ it is taken. Between $M_s$ and $M_f$ the steel is a mixture of martensite and untransformed austenite.

At intermediate cooling rates **bainite** forms, by a mixture of shear and limited diffusion. Upper bainite has $\alpha'$ laths with carbides between them, because the carbon had time to leave the laths; lower bainite, formed faster, has the carbides within the laths and is closer to martensite. Bainite looks similar to martensite and is also hard.

Quenching makes an enormous difference to hardness. At the same carbon content, martensite is roughly four times as hard as pearlite or a spheroidised carbide structure, and its hardness rises steeply with carbon because the carbon is all in solution. Above about 0.6 % C, though, so much carbon makes martensite hard to complete; austenite is retained and the hardness falls.

![[materials_martensite_hardness_tempering.png|900]]

## 4. TTT and CCT diagrams

The phase diagram has no time axis, so it cannot say what a given cooling rate will produce. A **time–temperature–transformation** (TTT) diagram, for one composition, adds it. Austenitise samples, quench them to a fixed temperature, hold, and measure how much has transformed after various times. For a eutectoid steel held at 705 °C, pearlite starts after about 5.8 minutes and is complete at about 67 minutes. Repeating at many temperatures and joining the start points and the finish points gives two C-shaped curves on a log-time axis.

![[materials_ttt_critical_cooling_rate.png|800]]

The curves have a nose because two effects compete. Just below 727 °C the undercooling is small, so the thermodynamic driving force to nucleate the new phases is weak and transformation is slow to start, though diffusion is fast. Far below, the driving force is large but there is too little thermal energy for diffusion, so transformation is slow again, and below the nose the product changes to bainite. The fastest transformation, the nose, lies between. Coarse pearlite forms just below the eutectoid temperature, fine pearlite near the nose, bainite below it; at the bottom, horizontal lines mark $M_s$ and $M_f$, with austenite plus martensite between them.

A TTT diagram describes holds at constant temperature, and a cooling curve can only be approximated on it as a staircase of short holds. The **continuous cooling transformation** (CCT) diagram is measured instead by cooling samples at fixed rates, which is what real parts experience. Furnace cooling (annealing) crosses the pearlite start and finish lines early and gives coarse pearlite. Air cooling (normalising) crosses them later, at lower temperature, and gives fine pearlite, because the diffusion distances are shorter. An oil quench may clip the pearlite and bainite regions and give a mixture of fine pearlite, bainite and some martensite. The **critical cooling rate** is the slowest that just misses the noses; a water quench faster than it gives fully martensitic steel.

## 5. Hardenability and the Jominy test

**Hardenability** is how easily a steel forms martensite all the way through a component; it is not hardness, nor work hardening, but the ability to transform fully. It depends on composition, through the effect of the alloying elements on the transformation curves.

The **Jominy end-quench test** measures it on the production line. A standard bar is heated to austenite and one end is quenched with a jet of water, so the cooling rate falls along the bar from about 225 °C/s at the quenched end to about 2 °C/s at the far end. A flat is ground along the bar to remove the decarburised skin, and hardness is measured against distance from the quenched end. One test thus samples a whole range of cooling rates. Look-up charts then relate each Jominy distance to positions in real bars: 9.8 mm from the quenched end has the same cooling rate as the centre of a 28 mm bar quenched in oil, so a steel that is fully martensitic at 9.8 mm on the Jominy bar can be through-hardened in a 28 mm bar in oil. The centre of a 75 mm bar corresponds to 25 mm on the Jominy bar, which is also the half-radius of a 100 mm bar. The surface of any bar cools faster than its centre, and thinner bars cool faster than thicker ones.

![[materials_jominy_readoff_2023_24.png|800]]

The quench medium matters as well. Oil is used more than water although it cools more slowly, because its cooling is more controlled and it avoids the steam that forms round a part quenched in water; salt water, plain water, oil and forced air all cool at different rates. With a CCT diagram, Jominy data show whether the core of a large part will be martensitic or bainitic. Very fast quenching of a large part is not just difficult but harmful, because it causes residual stress and distortion; the job is to choose a steel composition and quench medium together that give the properties needed.

## 6. Tempering: making martensite useful

As-quenched martensite is usually too brittle to use. **Tempering** reheats it to a temperature such as 200, 400 or 600 °C, low enough to stay below the eutectoid, so that the trapped carbon diffuses out and forms a fine dispersion of carbides. Lightly tempered, the laths remain with fine carbides; heavily tempered, the laths break down and the carbides spheroidise. Hardness and strength fall, but brittleness falls much more, and toughness rises. Temperature and time are interchangeable to a degree, because both drive diffusion.

Molybdenum changes the picture. Without it, carbides coarsen steadily and the hardness falls with tempering temperature. A little molybdenum slows the softening. More gives an initial softening and then a rise as a fine dispersion of alloy carbides forms that does not coarsen, so strength is kept while brittleness is relieved: secondary hardening. See [[Tempering]].

## 7. What alloying elements do

Each alloying element works by changing which phase is stable, so it moves the phase-diagram boundaries and the TTT curves. The effects include hardenability; grain-size control, where micro-alloy carbides pin grain boundaries during annealing and normalising; precipitation and solid-solution strengthening; corrosion resistance, by changing the surface oxide; wear resistance from hard surface phases; high-temperature properties; machinability; and weldability.

The elements fall into groups by what they promote:

| Group | Elements (course list) | Effect |
|---|---|---|
| Carbide formers | Cr, Mn, Nb, Mo, Ti, W, V | stable carbides, harder than $\mathrm{Fe_3C}$, often finely dispersed |
| Graphitisers | Ni, Al, Si | make carbides unstable, favouring free carbon |
| Austenite ($\gamma$) stabilisers | Co, Cu, Ni, Mn (often FCC themselves) | widen the austenite field; enough keeps austenite down to room temperature |
| Ferrite ($\alpha$) stabilisers | Cr, Mo, W, Si, V (often BCC themselves) | shrink the austenite field; enough keeps ferrite up to high temperature |

Some elements appear twice: chromium both forms carbides and stabilises ferrite, nickel both graphitises and stabilises austenite. The effects interact rather than adding, so in practice thermodynamic software predicts the phases.

Carbon is the most important element. In slowly cooled steel, more carbon means more pearlite, then pearlite with cementite; Brinell hardness and tensile strength rise and elongation falls, with the tensile strength dropping again at very high carbon because of brittle cementite. The applications follow the carbon: wire, rivets, chains and stampings at low carbon; structural steel and beams; axles, gears, shafts and rails; high-tensile wire and rope; then shear blades and chisels, drills, taps and dies, and finally knives, saws and razors.

### Raising hardenability

To get martensite the quench must beat the diffusional formation of ferrite and pearlite, so anything that slows that transformation raises hardenability. Carbon, manganese, nickel and vanadium retard the ferrite transformation, and molybdenum and chromium do the same through their effect on diffusion; together they shift the ferrite and pearlite curves to the right and down, so martensite forms at slower cooling rates. A higher austenitising temperature also helps. Holding hotter grows the austenite grains, and since austenite grain boundaries are where ferrite and pearlite nucleate, fewer boundaries means slower diffusional transformation and easier martensite; the Jominy curve stays hard further from the quenched end.

## 8. Classes of steel

High-strength low-alloy (HSLA) steels have low carbon, 0.05–0.25 %, with up to 2 % manganese and very small amounts of copper, nickel, niobium, vanadium, chromium, molybdenum, titanium or zirconium. Manganese is a getter for sulphur: it forms manganese sulphide inclusions, which roll out into stringers, instead of leaving a monatomic layer of sulphur on the grain boundaries that would give easy intergranular fracture. The micro-alloying elements form a very fine dispersion of carbides whose main job is to keep the grain size very fine during thermomechanical processing, with a little precipitation strengthening besides. The result is a yield strength of 250–590 MPa from very little alloying, so a structural member can be 20–30 % lighter than one in plain carbon steel of the same strength; they are used in cars, trucks, cranes, bridges and roller coasters.

Medium-carbon steels are used quenched and tempered. Plain carbon grades give yield strengths of about 430–585 MPa and tensile strengths of 480–980 MPa depending on the tempering; alloy grades reach much higher strengths, with lower elongation, for springs, hand tools, bushings, aircraft tubing, shafts, pistons and gears. Plain carbon steels have low hardenability and must be quenched very fast; chromium, nickel and molybdenum improve hardenability by shifting the nose right and down, and also set what carbides form on tempering.

High-carbon tool steels, from just below the eutectoid composition to well above it, are used hardened and tempered: a martensitic matrix with a large volume of very hard carbides of chromium, vanadium, tungsten or molybdenum gives wear resistance and an edge that holds.

### Surface hardening

The surface can be hardened alone. Nitriding diffuses nitrogen in to form a hard nitride layer; carburising diffuses carbon in to raise the surface carbon; either way the extra solute makes the martensite formed on quenching harder still. Induction or flame hardening heats only the surface and quenches it, giving a martensitic case on a softer pearlitic core. A fractured flame-hardened sample shows brittle cracking in the hard case and a tougher core. The hardness profiles differ: induction hardening gives a hard layer with a step to the core, nitriding a thin, very hard skin, carburising a gradual fall that follows the carbon diffusion profile. Each gives a wear-resistant surface over a tough interior.

## 9. Stainless steels

Stainless steel was found in Sheffield in 1913 when Harry Brearley noticed that some of his gun-barrel steels would not rust; the ones that resisted had more than a certain amount of chromium. With about 12 % chromium or more, a coherent, protective chromium oxide, $\mathrm{Cr_2O_3}$, forms in preference to the other oxides, and once formed it blocks the transport of both ions and electrons needed for further oxidation; with less, the oxide is a mixed, non-protective one. The chromium is in effect alloying the oxide rather than the metal. Nickel, an austenite stabiliser, decides the matrix.

![[materials_stainless_cr_ni_map.png|800]]

- Austenitic stainless steels (FCC) usually have at least 16 % chromium and 6 % nickel; 304, "18/8", is the basic grade, and 316L adds molybdenum with low carbon to resist weld decay. They account for about 70 % of stainless use: best corrosion resistance, good at high temperature, and, being FCC, no ductile–brittle transition, so they stay tough at cryogenic temperatures, as in space applications. They are largely non-magnetic, useful in satellites.
- Ferritic stainless steels (BCC) contain only chromium, 10.5–18 %, with low carbon, so they cannot be strengthened by heat treatment; they are less ductile and harder to form and weld.
- Martensitic stainless steels have higher carbon and about 12 % chromium (410, 416, 420, 440A/B/C) and are quenched and tempered for hardness; 431 reaches about 16 % chromium but stays martensitic because 2 % nickel keeps austenite stable to a low enough temperature to quench.
- Duplex stainless steels, with high chromium and some nickel, are a mixture of austenite and ferrite. They resist stress corrosion cracking much better than austenitic grades (though not as well as ferritic), have toughness between the two, much higher strength because of the many phase boundaries, and corrosion resistance like austenitic. Below about −50 °C the ferrite becomes so brittle that the austenite cannot rescue it, and above about 300 °C they also lose toughness, so they are used between those limits, for example in pipelines.

Compared with plain carbon steel, stainless steels work-harden faster, are stronger and harder, keep strength when hot, resist corrosion, stay tough at cryogenic temperatures (austenitic), are non-magnetic (austenitic), and keep a corrosion-resistant surface after machining. The weld-decay problem of the austenitic grades is in [[SESA2028 M3 - Corrosion, Wear and Surface Engineering#Intergranular corrosion and weld decay|M3]]. See [[Stainless Steel Classes]].

## Worked examples

### A quench-cracked component

This is an old exam question. A component of complex shape, with some 1 mm radii, some unradiused grooves, and both large and small sections, is made from 0.4 % plain carbon steel, water-quenched from 875 °C and tempered at 580 °C for an hour.

The first part asks for the purpose of the heat treatment. At 875 °C a 0.4 % C steel is single-phase austenite, FCC, with all its carbon in solution. A water quench beats the critical cooling rate, so on a CCT diagram it misses the pearlite and bainite noses (furnace cooling would give pearlite and oil perhaps pearlite and bainite) and the austenite shears to BCT martensite, highly dislocated and distorted, with the carbon trapped. Tempering at 580 °C lets the carbon diffuse out as a fine dispersion of carbides: the strength and hardness fall somewhat, the ductility and toughness rise a lot. In an open-notes exam this bookwork earns fewer marks than it once did.

The second part, worth more, is to troubleshoot cracking found after final heat treatment and machining. The cause is the quench itself. A large component cools much faster at its surface and in thin features than in its core. The surface cools, contracts and stops while the core is still hot and still contracting and transforming, so differential contraction and different microstructures leave residual stress and distortion. The stresses are highest where the stress concentrations are worst and the section changes most, at the sharp, unradiused grooves and large changes of diameter, where thin parts cool much faster than the bulk. Quality control should inspect there, straight after quenching and before machining, because machining relieves and redistributes the stresses.

The solutions trade cost against risk. A more hardenable alloy steel, with chromium, molybdenum, manganese, nickel or vanadium, shifts the nose so martensite still forms under a gentler, more controllable oil quench, with less distortion and residual stress, at higher material cost; at 0.4 % C the carbon is below the 0.6 % at which more carbon hinders martensite. A higher austenitising temperature, say 950 °C, grows the austenite grains and raises hardenability, at the cost of more heating. Or question the requirement: if the martensite is there for wear, a slower cool giving a ferrite–pearlite core followed by carburising or nitriding would give a hard case without quench cracking, at the cost of an extra process. There is no single model answer; the marks are for a reasoned engineering judgement.

### How much ferrite in a 0.4 % C steel?

Illustrative, using the lever rule just above 727 °C. The lever rule is a carbon balance. A steel of overall carbon content $C_0$ is a mixture of ferrite (carbon $C_\alpha$, mass fraction $W_\alpha$) and austenite (carbon $C_\gamma$, mass fraction $1-W_\alpha$), and the carbon in the two phases must add up to the carbon in the steel:

$$
C_0=W_\alpha C_\alpha+\left(1-W_\alpha\right)C_\gamma .
$$

Collect the $W_\alpha$ terms:

$$
C_0-C_\gamma=W_\alpha\left(C_\alpha-C_\gamma\right)\quad\Longrightarrow\quad W_\alpha=\frac{C_\gamma-C_0}{C_\gamma-C_\alpha}.
$$

Just above 727 °C the pro-eutectoid ferrite contains about $C_\alpha=0.022$ % C and the remaining austenite $C_\gamma=0.76$ %, so for $C_0=0.4$ %

$$
W_\alpha=\frac{0.76-0.4}{0.76-0.022}=0.488,
$$

and the fraction that becomes pearlite is $1-0.488=0.512$. Within pearlite itself the cementite fraction is

$$
\frac{0.76-0.022}{6.67-0.022}=0.111,
$$

which is why pearlite is mostly ferrite with thin cementite lamellae. A 1.2 % C steel forms $(1.2-0.76)/(6.67-0.76)=0.074$ of pro-eutectoid cementite, as a brittle network on the grain boundaries.

> [!check] The carbon adds back up
> $0.488\times0.022+0.512\times0.76=0.0107+0.389=0.400$ % C, the steel's composition. For the whole 0.4 % C steel the total cementite fraction is $(0.4-0.022)/(6.67-0.022)=0.057$, which equals the cementite carried in its pearlite, $0.512\times0.111=0.057$: all the cementite in a hypo-eutectoid steel is inside the pearlite.

### Reading a TTT diagram for the cooling rate

2024-25 MQ1(d): on the eutectoid TTT diagram the nose is at about 540 °C and about 1 s. Cooling from 700 °C, the steel must pass the nose temperature in under about 1 s, so the cooling rate must be roughly

$$
\frac{700-540}{1.0}=160\text{ °C/s}
$$

or more (200 °C/s if the nose is at 0.8 s), and must continue below $M_f$ for full martensite. A longer hold at the austenitising temperature, which grows the austenite grains, or more nickel would move the curves right and allow a slower rate.

### A 50 mm bar from Jominy data

2023-24 MQ2(ii)(a): a 50 mm bar quenched in oil. The look-up chart gives Jominy distances of 7.0 mm at the surface, 11.5 mm at three-quarter radius, 14.0 mm at half radius and 15.5 mm at the centre, which on the steel's Jominy curve read as 53.5, 48.5, 45.5 and 43.5 HRC. The surface, cooled fastest, is hardest and lath martensitic; tempering would improve its ductility. The full solution is in [[FEEG2005 Exam 2023-24 Solutions]].

## Links

- Parent: [[SESA2028 Aerospace Materials & Structures Hub]]
- Previous: [[SESA2028 M6 - Light Alloys - Aluminium, Magnesium, Beryllium and Titanium]] · Next: [[SESA2028 M8 - High Temperature Materials - Creep, Oxidation and Superalloys]]
- Concepts: [[Martensite]] · [[TTT and CCT Diagrams]] · [[Hardenability and Jominy Test]] · [[Tempering]] · [[Stainless Steel Classes]] · [[Ductile-Brittle Transition]] · [[Sensitisation and Weld Decay]]
- Related: [[Titanium Alloy Classes]] (titanium $\alpha'$ martensite) · [[Hall-Petch Relation]]
- Tutorial: [[SESA2028 Materials Tutorial MT4 - Alloy Design Solutions]] · past papers: [[FEEG2005 Exam 2014-15 Solutions]] (B3) · [[FEEG2005 Exam 2020-21 Solutions]] (MQ2) · [[FEEG2005 Exam 2023-24 Solutions]] (MQ2(ii)) · [[FEEG2005 Exam 2024-25 Solutions]] (MQ1(d))

## Sources

- Ferrous materials 2025 slides
- Mini-lecture transcripts ML11a (introduction and review of steels), ML11b (effects of cooling), ML12a (TTT and CCT curves, the Jominy test), ML12b (controlling steel properties), ML13a (alloying in steels), ML13b (stainless steels), ML13c (steels example problem)
- Numbers recomputed in Python

## Self-study tasks

ML13c is itself the set exercise: a past exam question on a quench-cracked component, worked through as an example of an open-ended answer. ML12a (l. 195) says Jominy read-offs will be practised in a tutorial.

### Core

- [ ] Explain the purpose of each step of the water quench from 875 °C and temper at 580 °C for 0.4 % C steel (ML13c, ll. 21–152). → [[#A quench-cracked component]]
- [ ] Explain the quench cracking and propose solutions with their pros and cons (ML13c, ll. 153–739). → [[#A quench-cracked component]]
- [ ] Explain how a TTT diagram is built and why it has a nose (ML12a, ll. 1–68). → [[#4. TTT and CCT diagrams]]
- [ ] Read Jominy data for a real bar (ML12a, ll. 156–195; 2023-24 MQ2(ii)(a)). → [[#5. Hardenability and the Jominy test]] · [[#A 50 mm bar from Jominy data]]
- [ ] MT4 Q3 (quenching plain-carbon steel). → [[SESA2028 Materials Tutorial MT4 - Alloy Design Solutions]]

### Further practice

- [ ] Explain why martensite is hard, and what tempering and molybdenum do (ML11b, ll. 47–106; ML12b, ll. 1–38). → [[#3. Fast cooling: martensite]] · [[#6. Tempering: making martensite useful]]
- [ ] Compare the four stainless steel families and choose one for a cryogenic tank and for a seawater pipeline (ML13b; suggested, not lecturer-set). → [[#9. Stainless steels]]

## Transcript and slide slips

### Transcript slips

> [!warning] Mini-lectures ML11a–ML13c
> | Where | Transcript says | Correct |
> |---|---|---|
> | ML11a, ll. 37–39 | "minus 20 joules … 25 joules … 27 joules" | the lecturer settles on 27 J, the usual Charpy criterion |
> | ML11a, l. 52 | "Sharpie 27 joule point" | Charpy |
> | ML11a, l. 62 | "The Liberty ships in 1920" | the 1920 steels; the Liberty ships were the Second World War steels (l. 65) |
> | ML11a, ll. 161 on | "perlite" | pearlite |
> | ML11a, l. 232 | "the leave rule" | the lever rule |
> | ML11a, l. 285 | "these white phases are the perlite" | the white phase is the pro-eutectoid ferrite; the mixed black-and-white phase is the pearlite (l. 286) |
> | ML11a, l. 305 | "6.678%" | 6.67 % |
> | ML11b, l. 75 | "high ramification" | high magnification |
> | ML11b, l. 102 | athermal means "sort of separate from temperature" | independent of time: the amount transformed depends on temperature, not hold time (ll. 103–106) |
> | ML11b, l. 121 | "Martensite tends to look very similar to martensite" | bainite looks very similar to martensite |
> | ML12a, l. 4 | "TT curve" | TTT curve |
> | ML12a, ll. 6, 7 | "Jomini test", "Martin's site" | Jominy test, martensite |
> | ML12a, l. 24 | "there is no austenite" | there is only austenite (corrected at l. 25) |
> | ML12a, l. 30 | "from my alpha to my coarse perlite" | from austenite to coarse pearlite |
> | ML12a, l. 37 | "the fusion is fast" | diffusion is fast |
> | ML12a, ll. 46, 50 | "displacer transformation" | displacive transformation |
> | ML12a, l. 79 | "the austenite housing temperature" | the austenitising temperature |
> | ML12a, l. 108 | "a politic structure" | a pearlitic structure |
> | ML12a, l. 155 | "in a particular crunch" | in a particular quench |
> | ML12b, l. 2 | "seal properties" | steel properties |
> | ML12b, l. 24 | "nitrogen carbides" | molybdenum (alloy) carbides |
> | ML12b, l. 28 | "tempering you out on the site" | tempering martensite |
> | ML12b, l. 137 | "Brunel hardness" | Brinell hardness |
> | ML12b, l. 146 | "phoretic, politic steels" | ferritic–pearlitic steels |
> | ML12b, l. 154 | "brooches" | broaches |
> | ML13a, l. 26 | "integrating fracture" | intergranular fracture |
> | ML13a, l. 76 | "question tempered medium comes deals" | quenched and tempered medium-carbon steels |
> | ML13a, l. 81; ML13c, ll. 440–454 | chromium, nickel and molybdenum "all stabilise the austenite" | nickel stabilises austenite, but chromium and molybdenum are ferrite stabilisers (ML12b, l. 114); all three raise hardenability by slowing the diffusional ferrite and pearlite transformation |
> | ML13a, l. 96 | "libidin" | molybdenum |
> | ML13a, l. 117 | "weather resistance" | wear resistance |
> | ML13b, ll. 7, 33, 67 | "phoretic", "phloritic", "fritic" | ferritic |
> | ML13b, ll. 13, 17 | "gum barrels" | gun barrels |
> | ML13b, l. 77 | "the fileroid" | the filler rod |
> | ML13b, l. 108 | "Martin Sidic" | martensitic |
> | ML13c, l. 18 | "first quarter quench" | first water quenched |
> | ML13c, l. 47 | "ferret and cementite" | ferrite and cementite |
> | ML13c, ll. 247, 519 | "geometry curves", "germany curve" | Jominy curves |
> | ML13c, l. 418 | "monidium" | molybdenum |
