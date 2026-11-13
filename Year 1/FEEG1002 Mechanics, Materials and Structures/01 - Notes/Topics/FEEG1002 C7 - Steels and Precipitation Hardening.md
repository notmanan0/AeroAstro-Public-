---
title: "FEEG1002 C7 - Steels and Precipitation Hardening"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part C: Materials"
order: 22
tags: [feeg1002, materials, steel, iron-carbon, eutectoid, pearlite, precipitation-hardening, ageing]
aliases: ["Materials Lectures 9 and 10", "Iron-carbon diagram", "Age hardening"]
date: 2026-11-05
status: lectured
coverage: "Materials L9 (5 Nov 2024, ll. 1–715): austenite, ferrite, cementite and pearlite, phases against microconstituents, the Fe–Fe3C diagram, eutectic and eutectoid reactions, pearlite formation, hypo- and hypereutectoid microstructures, lever-rule calculations, properties against carbon content and Brinell hardness. Materials L10 (11 Nov 2024, ll. 1–868): precipitation hardening of Al–Cu (solution treatment, quench, ageing), GP zones and the θ″, θ′, θ sequence, cutting and bowing, the ageing curve, over-ageing in service, ageing time and temperature, choosing a suitable region on a phase diagram, and a recap of tie lines and microstructures. Slide decks 10 and 11 in full."
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: ["[[FEEG1002 C6 - Phase Diagrams]]", "[[FEEG1002 C5 - Strengthening Mechanisms and Annealing]]"]
next_topics: ["[[FEEG1002 C8 - Fracture - Brittle, Ductile and Fracture Mechanics]]"]
key_concepts: ["[[Iron-Carbon Phase Diagram]]", "[[Eutectic and Eutectoid Reactions]]", "[[Year 1/FEEG1002 Mechanics, Materials and Structures/01 - Notes/Concepts/Precipitation Hardening]]", "[[Tie Lines and Lever Rule]]"]
tutorial_sheets: ["[[FEEG1002 Materials Tutorial 3 - Phase Diagrams Solutions]]"]
sources: ["02 - Sources/Materials/Lectures/Lecture 10 - Steels.pdf", "02 - Sources/Materials/Lectures/Lecture 11 - Precipitation Hardening.pdf", "02 - Sources/Lectures/FEEG1002 Lecture 9 - Materials Steels.txt", "02 - Sources/Lectures/FEEG1002 Lecture 10.txt", "02 - Sources/Materials/Tutorials/Tutorial Sheet 03 - Phase Diagrams.pdf"]
---

# FEEG1002 C7 - Steels and Precipitation Hardening

> [!abstract] Summary
> Steel is iron with a little carbon, and its microstructure is read from the iron–iron carbide (Fe–Fe₃C) diagram. The key reaction is the eutectoid at 727 °C and 0.76 wt% C, where FCC austenite turns into BCC ferrite and hard cementite growing together as plates, the microconstituent pearlite. Steels with less carbon (hypoeutectoid) end as proeutectoid ferrite plus pearlite and those with more (hypereutectoid) as proeutectoid cementite plus pearlite, with the amounts given by the lever rule; more carbon means more strength and hardness and less ductility. Precipitation hardening uses a sloping solvus, as in Al–4 wt% Cu: solution treat into the single-phase field, quench to trap the solute, then age at a low temperature so that fine precipitates form inside the grains; strength peaks at an intermediate ageing time and falls if the alloy over-ages.

> [!summary]- Exam use: quick path
> - **Use it when:** a question asks for the phases or microconstituents in a steel, the microstructure after slow cooling, the amount of proeutectoid phase or pearlite, which region of a phase diagram allows precipitation hardening, the three-stage heat treatment, or why strength peaks with ageing time.
> - **Assumptions:** slow (equilibrium) cooling for steels; key compositions 0.022 wt% C (ferrite limit), 0.76 wt% C (eutectoid), 6.7 wt% C (cementite), eutectoid temperature 727 °C.
> - **Method:** 1. Hypo- (below 0.76) or hypereutectoid (above). 2. Proeutectoid amount just above 727 °C: hypo $f_{\alpha,pro}=(0.76-C_0)/(0.76-0.022)$; hyper $f_{Fe_3C,pro}=(C_0-0.76)/(6.7-0.76)$; pearlite is the rest. 3. Total ferrite and cementite just below 727 °C: tie line from 0.022 to 6.7. 4. Precipitation hardening needs a single-phase field crossing a solvus into a two-phase field on cooling. 5. Solution treat, quench, age; peak-aged is strongest; over-aged has fewer, larger, bowed-round precipitates.
> - **Common mistakes:** giving total ferrite when proeutectoid is asked (or the reverse); calling pearlite a phase (it is a microconstituent of two phases).
> - **Practise:** [[#Worked example - proeutectoid ferrite and total phases in a 0.5 wt% C steel]] · [[FEEG1002 Materials Tutorial 3 - Phase Diagrams Solutions]] Q3–Q4

Steel is the most widely used structural metal, and the reason is that the same two elements, iron and a fraction of a percent of carbon, can be made soft enough to draw into wire or hard enough to cut other steels, just by choosing the carbon content and the cooling. The phase diagram of [[FEEG1002 C6 - Phase Diagrams|C6]] is the map for doing it. The important changes in steel happen entirely in the solid: crystals of one structure turn into crystals of two others, without any liquid involved.

That change is driven by the polymorphism of iron ([[FEEG1002 C2 - Crystal Structures and Crystallography#4. Polymorphism|C2]]). FCC austenite, stable when hot, can dissolve a lot of carbon in its interstices; BCC ferrite, stable when cool, can dissolve hardly any ([[FEEG1002 Materials Tutorial 1 - Crystal Structures and Diffusion Solutions#Q9 - Carbon in a BCC interstitial site|Tutorial 1, Q9]]). When austenite cools and becomes ferrite, the carbon it held has to go somewhere, and it comes out as the hard compound cementite. How and where that happens decides the microstructure and so the properties.

Precipitation hardening uses the same logic on purpose: an alloying element is dissolved at high temperature, frozen in place by quenching, then allowed to come out of solution slowly as a fine dispersion of particles that block dislocations ([[FEEG1002 C5 - Strengthening Mechanisms and Annealing#4. Precipitation hardening|C5]]). It is the main way aircraft aluminium alloys are strengthened, and it relies on controlling diffusion through time and temperature, away from the equilibrium of the phase diagram.

---

## 1. The phases of steel

The iron–carbon system has three phases that matter here, and one microconstituent; their names and symbols need to be known.

**Austenite**, γ, is FCC iron with carbon in interstitial sites, a solid solution of carbon in iron. It is stable at elevated temperatures. Austenitic stainless steels are alloyed and heat-treated so that they stay austenitic at room temperature.

**Ferrite**, α, is BCC iron with carbon in interstitial sites, again a solid solution, stable at lower temperatures. It can hold at most 0.022 wt% C, so it is nearly pure iron: soft and ductile.

**Cementite**, Fe₃C, is an intermetallic compound of fixed composition, 6.7 wt% C. It forms to take up carbon that the iron cannot hold. It is hard and brittle, and raises hardness, wear resistance and yield strength.

**Pearlite** is a lamellar mixture of ferrite and cementite formed by the eutectoid reaction. Under the light microscope, after polishing and etching, its fine plates look like mother of pearl, which is where the name comes from.

### Phases and microconstituents

A **phase** is a homogeneous portion of a system with uniform physical and chemical characteristics, such as a single solid solution. A **microconstituent** is an identifiable element of the microstructure, which may consist of more than one phase. Pearlite is the standard example: it is a microconstituent, made of two phases, ferrite and cementite.

## 2. The iron–iron carbide diagram

![[m7_fe_fe3c.png|900]]

The diagram stops at 6.7 wt% C because that is the composition of cementite, a vertical line of fixed composition. It shows several reactions:

- A **eutectic** at 4.30 wt% C and 1147 °C, where a liquid turns into two solids, $L\rightarrow\gamma+\mathrm{Fe_3C}$. Austenite can dissolve up to 2.14 wt% C, at this temperature.
- A **eutectoid** at 0.76 wt% C and 727 °C, where a solid turns into two different solids, $\gamma\rightarrow\alpha+\mathrm{Fe_3C}$.
- A peritectic at the top left near 1493 °C, which is not covered.

The important reactions for steels all happen in the solid, so the useful part of the diagram is the region round the eutectoid.

### The eutectoid reaction

On cooling through 727 °C, austenite of eutectoid composition transforms:

$$
\gamma(0.76\ \text{wt\% C})\ \xrightarrow{\text{cooling, }727\,^\circ\text{C}}\ \alpha(0.022\ \text{wt\% C})+\mathrm{Fe_3C}(6.7\ \text{wt\% C})
$$

The word means "eutectic-like": it has the same shape on the diagram, a V of two lines meeting a horizontal isotherm, but the parent is a solid, not a liquid. The physical reason for it is that FCC austenite can hold 0.76 wt% C in solution at 727 °C, while the BCC ferrite that replaces it can hold only 0.022 wt%. The surplus carbon has to leave, and it forms cementite.

### How pearlite forms

The transformation happens in a solid, where diffusion is slow, so where and how it starts matters. Grain boundaries are regions of mismatch and atomic disorder, with high energy and many vacancies, where diffusion is fastest; the middle of a grain is a stable, low-energy arrangement. So the transformation nucleates at the austenite grain boundaries and grows into the grains. As before ([[FEEG1002 C6 - Phase Diagrams#The eutectic microstructure|C6]]), carbon atoms have to move by diffusion, out of the growing ferrite and into the growing cementite, and growing the two side by side as thin plates keeps the distance each atom has to travel short. Each nucleation event grows into a **pearlite colony** of parallel lamellae, a couple of microns apart. In a micrograph the etch picks out the ferrite–cementite boundaries and the colonies show their different orientations.

## 3. Microstructures of hypo- and hypereutectoid steels

Steels to the left of the eutectoid, with less than 0.76 wt% C, are **hypoeutectoid**; those to the right are **hypereutectoid**. The microstructure is found exactly as for a eutectic: start high in the single-phase austenite and work down, asking at each line what was there before and after.

![[m7_steel_microstructures.png|900]]

### Hypoeutectoid steel

A steel of, say, 0.4 wt% C cooled from the austenite field crosses the upper line into the α + γ field, where ferrite starts to nucleate on the austenite grain boundaries. This ferrite, which forms before the eutectoid, is **proeutectoid ferrite**; "proeutectoid" and "primary" mean the same. As the steel cools through α + γ the ferrite layers thicken, the tie-line segment that measures them growing, and the remaining austenite becomes richer in carbon, following the line down to the eutectoid point. Just above 727 °C the full amount of proeutectoid ferrite has formed and the remaining austenite has the eutectoid composition, 0.76 wt% C. Crossing 727 °C, the ferrite was there before and after, so it stays; the austenite was there before and not after, so it has transformed, into pearlite. The final microstructure is proeutectoid ferrite outlining the prior austenite grain boundaries, with pearlite inside. The ferrite inside the pearlite is **eutectoid ferrite**: the same phase as the proeutectoid ferrite, with the same 0.022 wt% C at 727 °C, distinguished only by when and where it formed.

### Hypereutectoid steel

A steel with, say, 1.0 wt% C crosses into the γ + Fe₃C field instead. **Proeutectoid cementite** forms on the austenite grain boundaries, and the remaining austenite becomes poorer in carbon, following the line down to the eutectoid. At 727 °C it transforms to pearlite. The final microstructure is a network of proeutectoid cementite along the prior austenite grain boundaries, enclosing pearlite colonies that have grown in from the boundaries.

### Amounts of each microconstituent

The lever rule gives the amounts, and as in [[FEEG1002 C6 - Phase Diagrams#Primary and total amounts|C6]] the question must be read for whether it asks for the proeutectoid (primary) amount or the total amount of a phase.

The proeutectoid amount is found just above 727 °C, where the tie line runs from the proeutectoid phase's boundary to the eutectoid composition. For a hypoeutectoid steel of composition $C_0$:

$$
f_{\alpha,pro}=\frac{0.76-C_0}{0.76-0.022}
$$

$$
f_{P}=\frac{C_0-0.022}{0.76-0.022}
$$

and for a hypereutectoid steel:

$$
f_{Fe_3C,pro}=\frac{C_0-0.76}{6.7-0.76}
$$

$$
f_{P}=\frac{6.7-C_0}{6.7-0.76}
$$

where $f_P$ is the pearlite fraction, equal to the fraction of austenite just above 727 °C. The total amounts of the two phases, ferrite and cementite, are found just below 727 °C from the tie line across the whole α + Fe₃C field, from 0.022 to 6.7 wt% C:

$$
f_{\alpha}=\frac{6.7-C_0}{6.7-0.022}
$$

$$
f_{Fe_3C}=\frac{C_0-0.022}{6.7-0.022}
$$

> [!tip] The opposite segment, again
> To get the amount of a phase, use the segment on the side of the point away from that phase. A check that never fails: on cooling into the two-phase field, the segment that measures the new phase is the one that grows as it forms.

## 4. Carbon content and properties

As carbon rises from zero to the eutectoid, the fraction of soft ferrite falls and the fraction of pearlite rises, from 0 to 100 %. Pearlite is strong because its lamellae give a very large area of ferrite–cementite boundary, and each boundary is a barrier to dislocations: they can glide in the ferrite but not through the cementite. So the tensile strength and the Brinell hardness rise steadily and the ductility (%EL) falls. Beyond the eutectoid there is no proeutectoid ferrite left, and the proeutectoid cementite on the grain boundaries makes the steel harder still but brittle: a crack can run along the continuous cementite network round the grains, an intergranular failure, so the tensile strength levels off and falls slightly.

![[m7_carbon_properties.png|900]]

The uses follow the properties. Low-carbon steels, mostly ferrite, are easily deformed and are used for rivets, wire, nails and chains. Medium-carbon structural steels go into beams, rails, axles, gears and shafts. High-carbon steels, at and beyond the eutectoid, are used for tools that must be harder than what they cut: chisels, drills, saws, knives and razors.

Hardness is measured by indentation. In a **Brinell hardness** test a hard sphere is pressed into the surface under a fixed load and held, and the size of the permanent indent is measured: a small indent means a hard material, a large one a soft material. Because the indent is made by plastic flow, hardness correlates with yield and tensile strength, which makes it a quick, nearly non-destructive check on a component.

## 5. Precipitation hardening

### Choosing the alloy from the phase diagram

**Precipitation hardening** (also called age hardening) is strengthening by the controlled formation of small, uniformly dispersed precipitates of a second phase inside the grains, where they impede dislocation movement. It brings together the phase diagram, diffusion, and the effect of microstructure on strength. The standard example is Al–4 wt% Cu.

The phase diagram must have a single-phase field that, on cooling, crosses a solvus into a two-phase field. On the aluminium-rich side of Al–Cu, α (copper dissolved in aluminium) can hold up to about 5.6 wt% Cu at 548 °C but very little at room temperature, so the α field narrows with falling temperature along a sloping solvus, and below it lies α + θ, where θ is the intermetallic CuAl₂. Only alloys in this range of composition, between the room-temperature solubility and the maximum solubility, can be precipitation hardened. A long, strongly sloping solvus is best, because it means a large amount of second phase can be precipitated.

![[m7_al_cu_precipitation.png|900]]

Slow cooling would not do. Followed down at equilibrium, an Al–4 wt% Cu alloy would cross the solvus and form θ as coarse particles on the α grain boundaries, where diffusion is fastest, which does little for strength. The heat treatment is designed to avoid this "perfect world" outcome.

### The three-stage heat treatment

The treatment has three steps:

1. Solution treatment at $T_0$, about 550 °C for Al–4 wt% Cu, inside the single-phase α field and below the solidus. All the copper dissolves into the aluminium lattice and any θ present dissolves: the copper is "got into solution".
2. Quench to $T_1$, essentially room temperature, by plunging into water or oil. Cooling is so fast that the copper atoms have no time to diffuse (diffusion is an Arrhenius process and stops when the temperature drops). The result is α **supersaturated** with copper: it holds more copper than its equilibrium solubility, a metastable state in which the copper atoms are under strain and would like to cluster.
3. Precipitation heat treatment, or **ageing**, at $T_2$, about 120 °C for this alloy, well below the solvus. The temperature is high enough for the copper atoms to diffuse short distances, but too low to dissolve them back into solution. Because the driving force is large and the mobility small, the copper atoms cluster with their near neighbours throughout the grains, forming a fine dispersion of submicroscopic precipitates inside the grains instead of coarse particles on the boundaries.

### The precipitation sequence

During ageing the copper does not form θ straight away. The sequence is:

$$
\alpha_{ss}\rightarrow\text{GP zones}\rightarrow\theta''\rightarrow\theta'\rightarrow\theta\ (\mathrm{CuAl_2})
$$

First, **GP zones** form: clusters of a few copper atoms, only a few atomic layers thick, that alter the local bond lengths. These grow into the coherent precipitate θ″ (theta double prime), whose lattice planes are continuous with the matrix. Further growth gives θ′ (theta prime), partly incoherent, and finally the equilibrium phase θ, CuAl₂, a large incoherent intermetallic particle with a structure quite unlike aluminium, more like a ceramic.

### Cutting and bowing

The dislocations interact with these particles in two ways, as in [[FEEG1002 C5 - Strengthening Mechanisms and Annealing#Coherent and incoherent precipitates|C5]]. Small coherent particles (GP zones and early θ″) are strained into the matrix and their stress fields resist the dislocation, but a dislocation pushed hard enough cuts through them. Incoherent particles cannot be cut; the dislocation is held at each particle and bows out between them, rejoins behind and moves on, leaving a ring of dislocation round each particle. Many small, closely spaced particles are like a pinboard full of pins: a line dragged through has to deal with every pin. A few large, widely spaced particles are easy to bow round.

### The ageing curve

Plotting yield strength against ageing time at a fixed temperature gives a curve with a maximum, and its shape comes from adding up the contributions:

- At the start, the supersaturated α is strengthened by the dissolved copper alone: solid-solution strengthening, which fades as the copper leaves solution.
- As GP zones and θ″ form, the coherency stresses and the stress to cut the particles rise.
- As the particles grow and become incoherent, the coherency stresses fall but the bowing stress takes over.
- The **peak** strength comes at the best combination of number, size, distribution and coherency of the precipitates.
- After the peak the particles keep growing and coarsening: fewer, larger, more widely spaced θ particles that are easy to bow round, so the strength falls.

An alloy aged for less than the peak time is **under-aged**; one aged beyond it is **over-aged**. At very long times the strength settles towards that of the equilibrium two-phase alloy, whose phase amounts follow from the tie line.

![[m7_ageing_curve.png|900]]

### Ageing temperature and time

Precipitation is a nucleation-and-growth process controlled by diffusion, so its rate follows the Arrhenius form $\text{rate}\propto\exp(-Q/RT)$, with an activation energy $Q$ that depends on the composition. A higher ageing temperature makes the atoms move more quickly, so the peak is reached sooner, but the precipitates grow fast and coarse and the peak strength is lower. A lower temperature gives a finer, better-distributed dispersion and a higher peak, but takes much longer. For an aluminium–copper alloy the peak is reached at about these times:

| Ageing temperature | Time to peak, $t_{ph}$ |
|---:|---|
| 260 °C | about 1 minute |
| 204 °C | about 1 hour |
| 149 °C | about 1 day |
| 121 °C | about 1 month |

A month in a furnace is not a viable industrial process; about a day is, and treatments of a few hours are common.

### Over-ageing in service

Because ageing is diffusion-controlled, it does not stop when the heat treatment ends; it continues wherever the part is warm enough. A part peak-aged to a yield strength of 400 MPa and designed for a service stress of 200 MPa has a factor of safety of 2. If it then runs warm, it keeps ageing, over-ages, and its yield strength falls, and the margin disappears. Ageing is cumulative: a part reheated continues from where it stopped. For high-temperature service the remedy is to over-age the alloy deliberately so that its properties are stable at the service temperature, or to use a different strengthening mechanism. The great practical advantage of precipitation hardening remains that an alloy can be formed and machined while soft and strengthened afterwards. It is the most efficient way of strengthening a wide range of alloys: Al–Cu, Al–Zn–Mg and nickel-based superalloys.

---

## Worked examples

### Worked example - proeutectoid ferrite and total phases in a 0.5 wt% C steel

For a steel of 0.5 wt% C, find the proeutectoid ferrite and pearlite just above 727 °C, and the total ferrite and cementite just below it.

The steel is hypoeutectoid. Just above 727 °C the tie line runs from ferrite (0.022 wt% C) to austenite of eutectoid composition (0.76 wt% C), and the proeutectoid ferrite uses the opposite segment:

$$
f_{\alpha,pro}=\frac{0.76-0.5}{0.76-0.022}=\frac{0.26}{0.738}=35.3\ \%
$$

$$
f_P=\frac{0.5-0.022}{0.76-0.022}=\frac{0.478}{0.738}=64.8\ \%
$$

Just below 727 °C, across the whole α + Fe₃C field:

$$
f_\alpha=\frac{6.7-0.5}{6.7-0.022}=\frac{6.2}{6.678}=92.8\ \%
$$

$$
f_{Fe_3C}=\frac{0.5-0.022}{6.7-0.022}=\frac{0.478}{6.678}=7.2\ \%
$$

Among the multiple-choice options (64.77 %, 35.3 %, 92.8 % and 7.2 %) every distractor is the answer to a different question, the pearlite fraction or one of the total phase fractions. The word "proeutectoid" in the question picks out the correct one.

### Worked example - proeutectoid cementite in a 1 wt% C steel

For a steel of 1.0 wt% C, how much proeutectoid cementite forms on cooling to 727 °C, and how much cementite is there in total below it?

The steel is hypereutectoid. Just above 727 °C the tie line runs from 0.76 wt% C (austenite) to 6.7 wt% C (cementite):

$$
f_{Fe_3C,pro}=\frac{1.0-0.76}{6.7-0.76}=\frac{0.24}{5.94}=4.0\ \%
$$

$$
f_P=\frac{6.7-1.0}{6.7-0.76}=\frac{5.7}{5.94}=96.0\ \%
$$

Only 4 % proeutectoid cementite, yet it forms a continuous network on the grain boundaries. The total cementite just below 727 °C is

$$
f_{Fe_3C}=\frac{1.0-0.022}{6.7-0.022}=\frac{0.978}{6.678}=14.6\ \%
$$

> [!check] Proeutectoid plus eutectoid cementite
> Pearlite has the eutectoid composition, so its own cementite fraction is fixed at $(0.76-0.022)/(6.7-0.022)=11.05\ \%$. The cementite in the pearlite is $0.960\times0.1105=0.106$, and adding the proeutectoid cementite gives $0.040+0.106=0.146$, the total from the long tie line.

### Worked example - activation energy from the ageing times

Use the peak-ageing times of about 1 minute at 260 °C and about 1 month at 121 °C to estimate the activation energy for precipitation, and predict the peak times at 149 °C and 204 °C.

The time to reach a given state is inversely proportional to the rate, so $t\propto\exp(Q/RT)$. With $t_1=720$ h at $T_1=394$ K and $t_2=1/60$ h at $T_2=533$ K:

$$
\ln\frac{t_1}{t_2}=\frac QR\left(\frac1{T_1}-\frac1{T_2}\right)
$$

$$
\ln\frac{720}{1/60}=\ln(43\,200)=10.67
$$

$$
\frac1{394.15}-\frac1{533.15}=6.61\times10^{-4}\ \mathrm{K^{-1}}
$$

$$
Q=\frac{8.314\times10.67}{6.61\times10^{-4}}=1.34\times10^5\ \mathrm{J/mol}=134\ \mathrm{kJ/mol}
$$

At 149 °C (422 K), working from the 121 °C point:

$$
t=720\exp\left[\frac{134\,000}{8.314}\left(\frac1{422.15}-\frac1{394.15}\right)\right]=720e^{-2.72}=48\ \mathrm h
$$

and at 204 °C, $t=720e^{-7.12}=0.58$ h, about 35 minutes. The quoted round numbers are a day and an hour, within a factor of two, which is as close as order-of-magnitude times allow. Going from 121 °C to 260 °C shortens the treatment by a factor of over 40 000.

---

## Links

- Parent: [[FEEG1002 Mechanics, Materials and Structures Hub]] · Previous: [[FEEG1002 C6 - Phase Diagrams]] · Next: [[FEEG1002 C8 - Fracture - Brittle, Ductile and Fracture Mechanics]]
- Concepts: [[Iron-Carbon Phase Diagram]] · [[Eutectic and Eutectoid Reactions]] · [[Year 1/FEEG1002 Mechanics, Materials and Structures/01 - Notes/Concepts/Precipitation Hardening|Precipitation Hardening]] · [[Tie Lines and Lever Rule]]
- Worked sheet: [[FEEG1002 Materials Tutorial 3 - Phase Diagrams Solutions]] (Q3–Q4) · Formula list: [[FEEG1002 Formula Sheet]]
- Year 2: [[SESA2028 M7 - Steels - Phase Transformations, Heat Treatment and Alloying]] (martensite, TTT diagrams, tempering) · [[SESA2028 M6 - Light Alloys - Aluminium, Magnesium, Beryllium and Titanium]] (aerospace aluminium alloys) · [[SESA2028 M8 - High Temperature Materials - Creep, Oxidation and Superalloys]] (precipitation-hardened superalloys)

## Sources

- `FEEG1002 Lecture 9 - Materials Steels.txt` (L9, 5 Nov 2024): phases of steel (ll. 47–140), the Fe–Fe₃C diagram (ll. 141–214), pearlite formation (ll. 215–313), hypoeutectoid cooling (ll. 314–420), the hypereutectoid quiz (ll. 421–482), lever-rule examples (ll. 483–562), properties against carbon and Brinell hardness (ll. 563–698), summary (ll. 699–715).
- `FEEG1002 Lecture 10.txt` (L10, 11 Nov 2024): principle and recap (ll. 1–94), the Al–Cu diagram (ll. 95–132), three-step treatment (ll. 133–289), precipitation sequence (ll. 290–357), cutting and bowing (ll. 358–393), the ageing curve (ll. 419–503), over-ageing in service (ll. 504–621), time and temperature (ll. 622–678), the Al–Mg exercise (ll. 692–733), applications (ll. 734–766), recap of phase-diagram skills (ll. 767–865).
- `Lecture 10 - Steels.pdf` (slide deck 10) and `Lecture 11 - Precipitation Hardening.pdf` (slide deck 11), including the Vevox questions and the peak-ageing table. Diagrams after Callister.
- `Tutorial Sheet 03 - Phase Diagrams.pdf`: Q3 (steels) and Q4 (precipitation hardening).

## Self-study tasks

### Core

- [ ] Tutorial 3, Q3a–c: phase against microconstituent, hypo- against hypereutectoid, eutectoid against proeutectoid ferrite. → [[#Phases and microconstituents]] · [[#3. Microstructures of hypo- and hypereutectoid steels]] · [[FEEG1002 Materials Tutorial 3 - Phase Diagrams Solutions#Q3 - Steels]]
- [ ] Tutorial 3, Q3d–e: proeutectoid ferrite and pearlite, then total ferrite and cementite at 500 °C, for 0.35 wt% C. Targets 55.6 % and 44.4 %; 95.0 % and 5.0 %. → [[#Amounts of each microconstituent]] · [[FEEG1002 Materials Tutorial 3 - Phase Diagrams Solutions#Q3 - Steels]]
- [ ] Tutorial 3, Q3f: microstructure of a 1.3 wt% C steel at 600 °C. → [[#Hypereutectoid steel]]
- [ ] Tutorial 3, Q4: choose a composition for precipitation hardening and explain the peak in strength. → [[#Choosing the alloy from the phase diagram]] · [[#The ageing curve]] · [[FEEG1002 Materials Tutorial 3 - Phase Diagrams Solutions#Q4 - Precipitation hardening]]
- [ ] The Al–Mg Vevox exercise: which regions A–F can be precipitation hardened (L10, ll. 692–727). Answer: B and F, each a single-phase solid solution crossing a solvus into a two-phase field. → [[#Choosing the alloy from the phase diagram]]

### Further practice

- [ ] The Z to Z′ microstructure quiz on a hypereutectoid steel: microstructures at A, B and C (L9, ll. 421–482). → [[#Hypereutectoid steel]]
- [ ] Explain why a peak-aged aluminium part can lose strength in warm service, and what to do about it (L10, ll. 504–561). → [[#Over-ageing in service]]

## Transcript and slide slips

> [!warning] Transcript and slide slips (L9, ll. 331, 417 and 570–583)
> Where: [[#3. Microstructures of hypo- and hypereutectoid steels]] · [[#4. Carbon content and properties]].
>
> At l. 331 the low-carbon side is called "hyper"; low carbon is hypoeutectoid and high carbon hypereutectoid (stated correctly at ll. 324–326). At l. 417 proeutectoid and eutectoid ferrite are "both FCC ferrite"; ferrite is BCC. The first properties slide gives the solubility of carbon in ferrite as 0.22 wt%; it is 0.022 wt%, as corrected in the lecture and on the second copy of the slide.

> [!warning] Transcript slips (L10, ll. 249–250 and 331–332)
> Where: [[#The precipitation sequence]].
>
> At ll. 249–250 the first precipitates are called "little incoherent precipitates"; the first ones (GP zones and θ″) are coherent, and incoherence comes with growth (as stated at ll. 317–327). The θ phase is first named "AlCu3", then corrected to CuAl₂; "Al Cu3" recurs at l. 413.

> [!warning] Slide slip (slide deck 11, "3 Step Heat Treatment")
> Where: [[#The three-stage heat treatment]].
>
> The phase field at the 120 °C ageing temperature is labelled "A" on the slide; it should be α (an autocorrection, L10, ll. 263–272).
