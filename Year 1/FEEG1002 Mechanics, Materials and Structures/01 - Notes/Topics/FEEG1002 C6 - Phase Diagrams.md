---
title: "FEEG1002 C6 - Phase Diagrams"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part C: Materials"
order: 21
tags: [feeg1002, materials, phase-diagrams, lever-rule, tie-lines, eutectic, microstructure]
aliases: ["Materials Lectures 7 and 8", "Binary phase diagrams", "Lever rule"]
date: 2026-11-05
status: lectured
coverage: "Materials L7 (29 Oct 2024, ll. 1–746): phases, the phase diagram as an equilibrium temperature–composition map, solubility limits, complete solid solubility (Cu–Ni), liquidus and solidus, tie lines, the lever rule, equilibrium and non-equilibrium solidification, dendrites and coring. Materials L8 (4 Nov 2024, ll. 1–810): partial solubility, the Pb–Sn eutectic diagram, solvus lines, the eutectic reaction and stripy microstructure, hypo- and hypereutectic alloys, microstructure development on cooling, primary against total phase amounts, intermetallics (Al–Cu). Slide decks 08 and 09 in full."
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: ["[[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation]]", "[[FEEG1002 C3 - Diffusion]]"]
next_topics: ["[[FEEG1002 C7 - Steels and Precipitation Hardening]]"]
key_concepts: ["[[Tie Lines and Lever Rule]]", "[[Eutectic and Eutectoid Reactions]]"]
tutorial_sheets: ["[[FEEG1002 Materials Tutorial 3 - Phase Diagrams Solutions]]"]
sources: ["02 - Sources/Materials/Lectures/Lecture 08 - Phase Diagrams 1 - Solid Solubility.pdf", "02 - Sources/Materials/Lectures/Lecture 09 - Phase Diagrams 2 - Partial Solubility.pdf", "02 - Sources/Lectures/FEEG1002 Lecture 7 - Materials Solid Solution Phase Diagrams.txt", "02 - Sources/Lectures/FEEG1002 Lecture 8 - Materials Partial Solubility.txt", "02 - Sources/Materials/Tutorials/Tutorial Sheet 03 - Phase Diagrams.pdf"]
---

# FEEG1002 C6 - Phase Diagrams

> [!abstract] Summary
> A binary phase diagram is an equilibrium map of temperature against composition that shows which phases exist. In a two-phase field a horizontal tie line through the point of interest gives the composition of each phase where it meets the field boundaries, and the lever rule, derived from conservation of mass, gives the amount of each phase from the opposite segment of the tie line. Copper and nickel are completely soluble and freeze over a temperature range; lead and tin are only partly soluble, and at the eutectic point a liquid turns into two solids at once, giving a stripy eutectic microstructure. Following a vertical cooling line from the liquid and checking every boundary crossed gives the microstructure of any alloy.

> [!summary]- Exam use: quick path
> - **Use it when:** a question gives a phase diagram, an alloy composition $C_0$ and a temperature, and asks which phases are present, their compositions, their amounts, the freezing range, or the microstructure after slow cooling.
> - **Assumptions:** equilibrium (slow cooling, diffusion complete); binary alloy; compositions in wt%.
> - **Method:** 1. Mark the point $(C_0,T)$ and name the field. 2. Two-phase field: draw the horizontal tie line to both boundaries and read the phase compositions straight down. 3. Amount of a phase = opposite segment ÷ whole tie line. 4. "Primary" amount: tie line at the eutectic temperature from the solid's limit to the eutectic composition; "total" amount: tie line across the whole α + β field. 5. Microstructure: start in the liquid, work down, and at each line ask what was there before and after.
> - **Common mistakes:** using the near segment instead of the opposite one; drawing separate α and β grains for an alloy that passed through the eutectic, when it should be primary α in a stripy eutectic.
> - **Practise:** [[#Worked example - primary and total phases in a lead–tin alloy]] · [[FEEG1002 Materials Tutorial 3 - Phase Diagrams Solutions]] Q1–Q2

An alloy of two metals rarely behaves like either. Its melting point shifts, it may freeze over a range of temperature instead of at one point, and in the solid it may split into two different crystals, each rich in one of the metals. A phase diagram records all of this on a single chart, and reading it is a skill that the tutorials and quizzes test directly.

The diagrams describe equilibrium. They show what would exist if the alloy were cooled so slowly that diffusion had time to move every atom to where it belongs. Real casting and heat treatment are faster, and the differences from equilibrium, such as coring, matter; but the equilibrium map is the reference against which everything else is judged, and in [[FEEG1002 C7 - Steels and Precipitation Hardening|C7]] it is the starting point for designing heat treatments of steels and aluminium alloys.

Two geometric tools do almost all of the work. A horizontal tie line through the point of interest tells you what each phase is made of, and the lengths of its two segments tell you how much of each there is. Applying them to a cooling alloy means following it down the diagram one line at a time.

---

## 1. Phases and phase diagrams

### What a phase is

In everyday terms a phase is a state of matter: gas, liquid or solid. The difference between them is the arrangement of the atoms. In a solid the atoms can also be packed in different ways, FCC, BCC or HCP, so a solid alloy can contain several different solid phases, each with its own crystal structure and composition, such as precipitates of one phase in a matrix of another. An **intermetallic** compound, with a fixed ratio of atoms and a structure more like a ceramic than a metal, is a phase too.

### What a phase diagram is

A **phase diagram** is a temperature–composition map. It shows which phases would exist, ideally and under **equilibrium** conditions, for each composition and temperature. It is based on thermodynamics and is found experimentally by cooling slowly. Only **binary** alloys of two elements are treated, so the diagram is two-dimensional: temperature on the vertical axis and composition on the horizontal axis. Two things to watch: the temperature axis often does not start at zero, and the composition axis runs from 0 to 100 wt% of one element, with the other element making up the rest; diagrams such as the iron–carbon one are cut off well before the far end. Many diagrams carry a second composition scale in atomic percent along the top; the weight percent (wt%) scale at the bottom is used throughout.

### Solubility limits

Sugar dissolves in tea up to a limit, the **solubility limit**, beyond which extra sugar sits undissolved at the bottom, and hot tea dissolves more than cold. Metals behave the same way in the solid state. Depending on how similar the two elements are (the alloying rules of [[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation#Alloying and solid solutions|C4]]), a binary system shows one of three behaviours. With **complete solid solubility**, one solid phase forms across the whole composition range. With **partial** (or no) **solid solubility**, two solid phases exist, with distinct crystal structures, depending on the composition. With **intermetallic compounds**, additional phases form.

## 2. Complete solid solubility: copper–nickel

Copper and nickel have atoms of almost the same size, both are FCC, and they have similar electronegativity and valency, so they mix in any proportion: atoms of either can sit on any lattice site. Their diagram is the simplest kind.

![[m6_cu_ni_tie_line.png|900]]

The left edge is pure copper and the right edge pure nickel, and the two pure metals melt at single temperatures, 1085 °C and 1455 °C. Between them the single melting point splits into two lines. Above the upper line, the **liquidus**, the alloy is entirely liquid, L. Below the lower line, the **solidus**, it is entirely solid, a single FCC solid solution called α. Between them is the two-phase field α + L, a mush of growing crystals in remaining liquid. So unlike a pure metal, an alloy freezes over a range of temperature, starting at the liquidus and finishing at the solidus. Adding nickel raises the melting range, because nickel has the stronger bonds.

### Tie lines give the compositions

At a point in the α + L field, say point B at 1250 °C in an alloy of overall composition $C_0=35$ wt% Ni, both phases are present, each with its own composition. To find them, draw a **tie line**: a horizontal line through the point, across the two-phase field, to the boundaries on either side. Where it meets the liquidus, read straight down to the composition axis: that is the composition of the liquid, $C_L=32$ wt% Ni. Where it meets the solidus, read down again: that is the composition of the solid, $C_\alpha=43$ wt% Ni. In each phase the rest is copper. The solid is richer in nickel than the liquid, because the higher-melting element solidifies preferentially.

### The lever rule gives the amounts

The tie line also gives how much of each phase there is. Let $f$ be the mass fraction of solid, so $1-f$ is the fraction of liquid. Nothing is created or lost when the alloy is part-solidified, so the nickel in the solid plus the nickel in the liquid must equal the nickel in the alloy:

$$
fC_\alpha+(1-f)C_L=C_0
$$

Expand the bracket:

$$
fC_\alpha+C_L-fC_L=C_0
$$

Collect the terms in $f$:

$$
f(C_\alpha-C_L)=C_0-C_L
$$

$$
\boxed{f=\frac{C_0-C_L}{C_\alpha-C_L}}
$$

and the fraction of liquid is

$$
1-f=\frac{(C_\alpha-C_L)-(C_0-C_L)}{C_\alpha-C_L}
$$

$$
\boxed{1-f=\frac{C_\alpha-C_0}{C_\alpha-C_L}}
$$

This is the **lever rule**. The two segments of the tie line are labelled $R=C_0-C_L$ (between the liquidus and the point) and $S=C_\alpha-C_0$ (between the point and the solidus), so the fraction of solid is $R/(R+S)$ and the fraction of liquid is $S/(R+S)$. In words:

$$
\text{amount of phase}=\frac{\text{opposite length}}{\text{overall length}}
$$

The segment that gives the amount of a phase is the one on the far side of the point from that phase's boundary.

For point B:

$$
f=\frac{35-32}{43-32}=\frac{3}{11}=27.3\ \%\ \text{solid}
$$

$$
1-f=\frac{43-35}{43-32}=\frac{8}{11}=72.7\ \%\ \text{liquid}
$$

> [!tip] Checking which segment is which
> Down the alloy's vertical cooling line, the alloy is 100 % liquid at the liquidus, and the segment between the liquidus and the point has zero length. As it cools, that segment grows, and so does the amount of solid. The segment next to the liquidus therefore measures the solid, the opposite phase. Exam questions are set with answers like 48 % and 52 % so that a guess by eye cannot tell them apart; this check can.

Compositions and amounts are separate readings. The tie line's end points give compositions; its segment lengths give amounts.

### Microstructure on equilibrium cooling

A 35 wt% Ni alloy cooled slowly from the liquid reaches the liquidus at about 1260 °C. The first specks of solid nucleate there, with the composition at the solidus end of the tie line, about 46 wt% Ni. As the temperature falls, both ends of the tie line slide down their lines: the solid forming becomes poorer in nickel (43 wt% at 1250 °C) and so does the remaining liquid (32 wt% at 1250 °C), while the amount of solid grows. At equilibrium, solid-state diffusion keeps every crystal at the current solid composition. At the solidus the last liquid freezes and the whole alloy is solid α of 35 wt% Ni. The crystals grow as **dendrites**, tree-like branches, because atoms attach preferentially along particular crystallographic directions; the dendrites meet and become the grains of the solid. Because every grain is a solid solution of two different-sized atoms, the alloy is stronger than either pure metal (solid-solution strengthening).

### Non-equilibrium cooling: coring

Diffusion in a solid is slow. If the alloy cools quickly there is not enough time for nickel to diffuse out of the first, nickel-rich solid, so each grain ends up with a nickel-rich centre and nickel-poor outer layers, a condition called **coring**. The composition differences set up small galvanic cells between the centre and edge of each grain, which can cause pitting corrosion ([[FEEG1002 C9 - Fatigue, Creep and Corrosion#The standard emf series and cell voltage|C9]]). Heating the casting to let the atoms diffuse back to equilibrium, an annealing treatment, removes it.

## 3. Partial solubility: the lead–tin eutectic

### Why partial solubility

If the two elements differ more in atomic size or structure, only a limited amount of one can be dissolved in the crystal of the other before the lattice is too disrupted. Beyond that limit a second phase must form. The alloy then has two solid solutions: α, rich in the first element with a little of the second dissolved in it, and β, rich in the second element with a little of the first. In lead–tin, α is lead with some tin dissolved and β is tin with some lead dissolved. This is also the origin of precipitation hardening ([[FEEG1002 C7 - Steels and Precipitation Hardening|C7]]).

![[m6_pb_sn_eutectic.png|900]]

### Reading the lead–tin diagram

Pure lead melts at 327 °C and pure tin at 232 °C. The diagram has the same lines as Cu–Ni, and some new ones:

- the **liquidus**, above which all is liquid;
- two mush fields, α + L on the lead side and β + L on the tin side, because two different solids can form;
- the **solidus**, below which there is no liquid;
- the **solvus** lines, which give the limit of solubility of one element in the other: the left solvus is the most tin that α can hold, and the right solvus the most lead that β can hold;
- a large α + β field in the middle.

The solubility of tin in lead is greatest at 183 °C, 18.3 wt% Sn; the solubility of lead in tin is greatest at the same temperature, 2.2 wt% Pb (β at 97.8 wt% Sn). Below 183 °C both solubilities fall, like sugar in cooling tea: at 100 °C the α boundary is at about 5 wt% Sn and the β boundary at about 98 wt% Sn.

### The eutectic point and reaction

The two liquidus lines come down from the pure-metal melting points and meet at a single point, the **eutectic point** $E$: 61.9 wt% Sn and 183 °C. At that composition the alloy melts and freezes at one temperature, like a pure metal, with no mush, and at a temperature lower than either pure metal. Cooling through it, the liquid transforms into two different solids at the same time, the **eutectic reaction**:

$$
L(61.9\ \text{wt\% Sn})\ \xrightarrow{\text{cooling, }183\,^\circ\text{C}}\ \alpha(18.3\ \text{wt\% Sn})+\beta(97.8\ \text{wt\% Sn})
$$

The horizontal line at 183 °C, from 18.3 to 97.8 wt% Sn, is the **eutectic isotherm**; any alloy whose cooling line crosses it undergoes the eutectic reaction in its remaining liquid. A low, sharp melting point suits a solder, so lead–tin solders were made near the eutectic composition.

Compositions to the left of the eutectic (less of the element on the horizontal axis, here tin) are **hypoeutectic**; those to the right are **hypereutectic**.

### The eutectic microstructure

At the eutectic temperature the liquid, with 61.9 wt% Sn, must split into α with 18.3 wt% Sn and β with 97.8 wt% Sn. Tin atoms must move into the β and lead atoms into the α, and since it all happens at one temperature there is no time for atoms to diffuse far. The way to keep the diffusion distances short is to grow α and β side by side in thin, alternating plates, so that each atom only has to move sideways by about a plate thickness. The result is a **lamellar**, or stripy, microstructure, with plates about 1 µm thick. Stripes in a micrograph are the signature of a eutectic (or, in the solid state, a eutectoid, [[FEEG1002 C7 - Steels and Precipitation Hardening|C7]]). You should be able to find eutectic points on a diagram and say that cooling through one gives a stripy microstructure.

## 4. Microstructure development on cooling

### The method

Microstructures develop as the alloy cools, so they must be worked out from the top down:

1. Start in a single-phase field (normally the liquid) on the vertical line at the alloy's composition, above the temperature asked about.
2. Follow the line down, stopping at every boundary you cross.
3. A phase present before and after a line is still there, as with primary α that survives crossing the eutectic.
4. A phase present before but absent after has converted into whatever the new field contains; on crossing the eutectic isotherm, any remaining liquid becomes both α and β.
5. A phase absent before and present after has just started to form.

Starting halfway down gives a wrong result.

![[m6_eutectic_microstructures.png|900]]

### A lead-rich alloy crossing the solvus

An alloy with less than 18.3 wt% Sn, say 10 wt% Sn, crosses the liquidus, and primary α nucleates as dendrites; it crosses the solidus and becomes all α, exactly as in Cu–Ni. On further cooling it crosses the solvus into the α + β field. The α is still there, but it can no longer hold all its tin, so β must form. Atoms diffuse fastest along grain boundaries ([[FEEG1002 C3 - Diffusion#Activation energy and the structure of the path|C3]]), so the β appears as small particles on the α grain boundaries. If such a grain-boundary phase is brittle it gives an easy crack path, which matters in steels.

### A hypoeutectic alloy

Take 40 wt% Sn. It crosses the liquidus and primary α forms as dendrites in the liquid; this first solid is the **primary** phase. Through the α + L field the α grows and the remaining liquid becomes richer in tin, following the liquidus down, until at 183 °C it reaches exactly the eutectic composition, 61.9 wt% Sn. Crossing the eutectic isotherm, the α was there before and is there after, so the primary α stays; the liquid was there before and not after, so it has turned into α + β by the eutectic reaction. The final microstructure is primary α dendrites surrounded by stripy eutectic. The remaining liquid behaves exactly as if it were an alloy of eutectic composition. Drawing separate grains of α and β for an alloy like this, because it ends in the α + β field, is the classic wrong answer.

The closer $C_0$ is to the eutectic composition, the less primary α forms first; at exactly 61.9 wt% Sn the whole alloy is eutectic, with no primary phase. A hypereutectic alloy behaves in mirror image: primary β dendrites form first, and the rest becomes eutectic. The α in the eutectic is called eutectic α, to distinguish it from primary α; the two are the same phase, labelled differently only to say where they formed.

### Primary and total amounts

Questions may ask for the amount of a primary phase or for the total amount of a phase, and the two are found with different tie lines.

The **primary** phase stops forming at the eutectic temperature, because all the remaining liquid then becomes eutectic. Its amount is found just above 183 °C, with the tie line from the α limit (18.3 wt% Sn) to the eutectic composition (61.9 wt% Sn), the liquid end. For a hypoeutectic alloy:

$$
f_{\alpha,primary}=\frac{C_E-C_0}{C_E-C_\alpha}
$$

$$
f_{eutectic}=\frac{C_0-C_\alpha}{C_E-C_\alpha}
$$

where the eutectic fraction equals the fraction of liquid just above the eutectic temperature. Once formed, the primary amount does not change on further cooling.

The **total** amount of α, counting primary and eutectic α together, is found below 183 °C with the tie line across the whole α + β field:

$$
f_{\alpha,total}=\frac{C_\beta-C_0}{C_\beta-C_\alpha}
$$

$$
f_\beta=\frac{C_0-C_\alpha}{C_\beta-C_\alpha}
$$

If the question says "primary", stay between the solid limit and the eutectic; if it asks for the total, go all the way across. Totals at lower temperatures use the solvus end points at that temperature; in an exam these will either be easy to read or be given.

## 5. Intermetallic compounds and general rules

In aluminium–copper alloys the second phase is θ, the intermetallic compound CuAl₂. An intermetallic with a fixed ratio of atoms (stoichiometric) appears on the diagram as a vertical line, or a very narrow field, rather than a broad range of composition. The Al–Cu diagram is drawn only up to about 54 wt% Cu. Its α is a solid solution of copper in aluminium, and its eutectic, $L\rightarrow\alpha+\theta$, is at 33 wt% Cu and 548 °C. A 20 wt% Cu alloy is hypoeutectic, ending as primary α plus eutectic; a 45 wt% Cu alloy is hypereutectic, ending as primary θ plus eutectic. This diagram is the basis of precipitation hardening in [[FEEG1002 C7 - Steels and Precipitation Hardening#5. Precipitation hardening|C7]].

A few rules hold on every binary diagram:

- On heating, melting starts at the solidus and finishes at the liquidus.
- Pure metals and stoichiometric intermetallics (such as Fe₃C) are vertical lines of fixed composition, with a unique melting point; alloys solidify over a range.
- Single-phase fields are always separated by a two-phase field.
- Three phases can coexist only at a single temperature, such as the eutectic temperature, and so a tie line in a two-phase field never meets more than two phases.

---

## Worked examples

### Worked example - the lever rule in copper–nickel

A 32 wt% Ni alloy is held at 1225 °C, where the tie line meets the liquidus at 25 wt% Ni and the solidus at 35 wt% Ni. What fractions are solid and liquid?

The whole tie line is $35-25=10$ wt%. The solid fraction uses the segment opposite the solidus, on the liquid side of the point:

$$
f=\frac{C_0-C_L}{C_\alpha-C_L}=\frac{32-25}{35-25}=\frac{7}{10}=70\ \%
$$

$$
1-f=\frac{C_\alpha-C_0}{C_\alpha-C_L}=\frac{35-32}{35-25}=\frac{3}{10}=30\ \%
$$

70 % solid, 30 % liquid. For a 44 wt% Ni alloy at 1275 °C, reading the ends of the tie line gives liquid at about 38 wt% Ni and solid at 50 wt% Ni. Its amounts would be $f=(44-38)/(50-38)=0.50$, an even split.

### Worked example - primary and total phases in a lead–tin alloy

For a lead–tin alloy of 35 wt% Sn (alloy $C_2$), find the amounts of primary α and eutectic just above 183 °C, and the total amounts of α and β just below it.

Just above 183 °C the tie line runs from the α limit, 18.3 wt% Sn, to the liquid at the eutectic composition, 61.9 wt% Sn:

$$
f_{\alpha,primary}=\frac{61.9-35}{61.9-18.3}=\frac{26.9}{43.6}=61.7\ \%
$$

$$
f_{eutectic}=\frac{35-18.3}{61.9-18.3}=\frac{16.7}{43.6}=38.3\ \%
$$

Just below 183 °C the tie line runs across the whole α + β field, from 18.3 to 97.8 wt% Sn:

$$
f_{\alpha,total}=\frac{97.8-35}{97.8-18.3}=\frac{62.8}{79.5}=79.0\ \%
$$

$$
f_\beta=\frac{35-18.3}{97.8-18.3}=\frac{16.7}{79.5}=21.0\ \%
$$

> [!check] Primary plus eutectic α equals total α
> The eutectic itself has the eutectic composition, so its own split into α and β is fixed: $(97.8-61.9)/(97.8-18.3)=45.2\ \%$ α. The eutectic α in the alloy is therefore $0.383\times0.452=0.173$, and primary plus eutectic α is $0.617+0.173=0.790$, the total found from the long tie line.

### Worked example - a hypereutectic alloy

For an alloy of 85 wt% Sn ($C_3$), find the primary β at 183 °C, then the total α and β at 100 °C, where the α boundary is at 5 wt% Sn and the β boundary at 98 wt% Sn.

Primary β uses the tie line from the eutectic composition to the β limit:

$$
f_{\beta,primary}=\frac{C_0-C_E}{C_\beta-C_E}=\frac{85-61.9}{97.8-61.9}=\frac{23.1}{35.9}=64.3\ \%
$$

and the eutectic is the remaining 35.7 %. At 100 °C, across the whole α + β field:

$$
f_\alpha=\frac{98-85}{98-5}=\frac{13}{93}=14.0\ \%
$$

$$
f_\beta=\frac{85-5}{98-5}=\frac{80}{93}=86.0\ \%
$$

---

## Links

- Parent: [[FEEG1002 Mechanics, Materials and Structures Hub]] · Previous: [[FEEG1002 C5 - Strengthening Mechanisms and Annealing]] · Next: [[FEEG1002 C7 - Steels and Precipitation Hardening]]
- Concepts: [[Tie Lines and Lever Rule]] · [[Eutectic and Eutectoid Reactions]] · [[Iron-Carbon Phase Diagram]]
- Worked sheet: [[FEEG1002 Materials Tutorial 3 - Phase Diagrams Solutions]] (Q1–Q2) · Formula list: [[FEEG1002 Formula Sheet]]
- Year 2: [[SESA2028 M7 - Steels - Phase Transformations, Heat Treatment and Alloying]] (non-equilibrium cooling and TTT curves) · [[SESA2028 M6 - Light Alloys - Aluminium, Magnesium, Beryllium and Titanium]]

## Sources

- `FEEG1002 Lecture 7 - Materials Solid Solution Phase Diagrams.txt` (L7, 29 Oct 2024): phases (ll. 56–104), axes and equilibrium (ll. 105–159), sugar in tea and solubility (ll. 160–242), the Cu–Ni diagram (ll. 243–348), tie lines (ll. 349–434), the lever rule and its check (ll. 435–533), Vevox questions (ll. 534–650), microstructure and dendrites (ll. 651–714), coring (ll. 714–733).
- `FEEG1002 Lecture 8 - Materials Partial Solubility.txt` (L8, 4 Nov 2024): partial solubility (ll. 49–132), the Pb–Sn diagram (ll. 133–239), the eutectic (ll. 240–351), hypo- and hypereutectic (ll. 352–371), microstructure method (ll. 372–631), the hypereutectic question (ll. 632–704), primary and total amounts (ll. 705–796), Al–Cu (ll. 797–810).
- `Lecture 08 - Phase Diagrams 1 - Solid Solubility.pdf` (slide deck 08) and `Lecture 09 - Phase Diagrams 2 - Partial Solubility.pdf` (slide deck 09), including the lever-rule examples and Vevox questions with solutions. Diagrams after Callister.
- `Tutorial Sheet 03 - Phase Diagrams.pdf`: Q1 (Ag–Cu) and Q2 (Al–Cu) on this note; Q3–Q4 belong to [[FEEG1002 C7 - Steels and Precipitation Hardening|C7]].

## Self-study tasks

### Core

- [ ] Tutorial 3, Q1: Ag–Cu, 20 wt% Ag: solidification range, compositions of primary α at the start and end, amount of primary α. Target 81.2 %. → [[#Primary and total amounts]] · [[FEEG1002 Materials Tutorial 3 - Phase Diagrams Solutions#Q1 - Silver–copper, 20 wt% Ag]]
- [ ] Tutorial 3, Q2: Al–Cu, 20 wt% Cu: first α, liquid compositions, microstructure at 500 °C. → [[#A hypoeutectic alloy]] · [[FEEG1002 Materials Tutorial 3 - Phase Diagrams Solutions#Q2 - Aluminium–copper, 20 wt% Cu]]
- [ ] The two Cu–Ni Vevox questions: fractions at 1225 °C and compositions at 1275 °C (L7, ll. 534–650). → [[#Worked example - the lever rule in copper–nickel]]
- [ ] The Pb–Sn lever-rule exercise left for self-study, with its solution on the slides (L8, ll. 784–793). → [[#Worked example - primary and total phases in a lead–tin alloy]] · [[#Worked example - a hypereutectic alloy]]

### Further practice

- [ ] Derive the lever rule from the mass balance $fC_\alpha+(1-f)C_L=C_0$ (on the slide, not derived in the lecture). → [[#The lever rule gives the amounts]]
- [ ] Sketch the microstructures at A and B on the hypoeutectic and hypereutectic Vevox slides by the before-and-after method (L8, ll. 632–702). → [[#4. Microstructure development on cooling]]

## Transcript and slide slips

> [!warning] Transcript slips (L7, ll. 124, 393–399 and 585)
> Where: [[#What a phase diagram is]] · [[#The lever rule gives the amounts]].
>
> The iron–carbon diagram is said to stop at "16.7 %"; it stops at 6.7 wt% C, the composition of cementite. The mass balance behind the lever rule is described in a garbled way; the slide's $fC_\alpha+(1-f)C_L=C_0$ is correct. In the first Vevox solution the liquid fraction is read out as "35 over 32"; it is $(35-32)/(35-25)=30\ \%$.

> [!warning] Transcript slips (L8, ll. 317 and 716)
> Where: [[#The eutectic microstructure]] · [[#Primary and total amounts]].
>
> As a hypothetical example, α is called HCP and β FCC; in lead–tin, α (lead-rich) is FCC and β (tin-rich) is body-centred tetragonal. The eutectic temperature is transcribed as "100 %, 83 degrees C"; it is 183 °C.

> [!warning] Slide slips (slide decks 08 and 09)
> Where: [[#The lever rule gives the amounts]] · [[#Worked example - a hypereutectic alloy]].
>
> On the second "Lever Rule" slide the liquid fraction is written $(43-35)/(34-32)$; the denominator is $43-32=11$, as the result $8/11=72.7\ \%$ shows. In the 100 °C solution for the 85 wt% Sn alloy the α fraction is computed as $(97.8-85)/(98-5)=13.8\ \%$, mixing the 183 °C β limit (97.8) with the 100 °C one (98); with the 100 °C end points throughout it is $(98-85)/(98-5)=14.0\ \%$, and β is 86.0 %. The total-phase slide for $C_2$ has a denominator printed as $98-18.3$ where $97.8-18.3=79.5$ is meant, as its result shows.
