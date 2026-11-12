---
title: "FEEG1002 Materials Tutorial 3 - Phase Diagrams Solutions"
module: "FEEG1002 Mechanics, Materials and Structures"
type: tutorial
stream: "Part C: Materials"
tags: [feeg1002, tutorial-solutions, materials, phase-diagrams, lever-rule, steel, precipitation]
sheet: "Materials Tutorial Sheet 3"
theory_notes: ["[[FEEG1002 C6 - Phase Diagrams]]", "[[FEEG1002 C7 - Steels and Precipitation Hardening]]"]
key_concepts: ["[[Tie Lines and Lever Rule]]", "[[Eutectic and Eutectoid Reactions]]", "[[Iron-Carbon Phase Diagram]]", "[[Year 1/FEEG1002 Mechanics, Materials and Structures/01 - Notes/Concepts/Precipitation Hardening]]"]
status: complete
date: 2026-11-05
sources: ["02 - Sources/Materials/Tutorials/Tutorial Sheet 03 - Phase Diagrams.pdf"]
---

# FEEG1002 Materials Tutorial 3 - Phase Diagrams Solutions

> [!abstract] Sheet info
> Four questions on the Ag–Cu and Al–Cu eutectic diagrams, steel microstructures and precipitation hardening. The sheet prints no answers. Temperatures and compositions marked on the diagrams (779 °C, 8.0, 71.9 and 91.2 wt% Ag; 727 °C, 0.022, 0.76 and 6.70 wt% C) are used as printed; the other readings (liquidus and solidus temperatures and compositions) were taken by digitising the diagrams on the sheet and are good to about ±5 °C and ±0.5 wt%. Q1–Q2 use [[FEEG1002 C6 - Phase Diagrams|C6]]; Q3–Q4 use [[FEEG1002 C7 - Steels and Precipitation Hardening|C7]].

## Q1 - Silver–copper, 20 wt% Ag

Taught in: [[FEEG1002 C6 - Phase Diagrams#Primary and total amounts]] and [[FEEG1002 C6 - Phase Diagrams#A hypoeutectic alloy]].

![[m6_t3_q1_ag_cu.png|900]]

**(a) Solidification range.** On the diagram the liquidus on the copper side is a straight line from pure copper at 1085 °C to the eutectic at 71.9 wt% Ag and 779 °C, so at 20 wt% Ag it is at

$$
T_L=1085-(1085-779)\times\frac{20}{71.9}=1085-85=1000\ ^\circ\mathrm C
$$

(the digitised diagram gives the same). The alloy contains more silver than α can dissolve (8.0 wt% at most), so it never crosses the solidus; its last liquid freezes by the eutectic reaction at 779 °C. Solidification runs from about $\boxed{1000\ ^\circ\mathrm C\text{ to }779\ ^\circ\mathrm C}$.

**(b) Composition of the primary α.** The first solid to form, at about 1000 °C, has the composition at the solidus end of the tie line: about $\boxed{5.5\ \text{wt\% Ag}}$ (read from the diagram; 5–6 wt% is a fair reading). As the alloy cools the α follows the solidus, and just above 779 °C it has the maximum solubility, $\boxed{8.0\ \text{wt\% Ag}}$ (point B, $C_{\alpha E}$).

**(c) Amount of primary α.** Primary α stops forming when the remaining liquid reaches the eutectic composition, so use the tie line just above 779 °C, from α (8.0 wt% Ag) to liquid (71.9 wt% Ag):

$$
f_{\alpha,primary}=\frac{C_E-C_0}{C_E-C_\alpha}=\frac{71.9-20}{71.9-8.0}=\frac{51.9}{63.9}=\boxed{0.812}
$$

81.2 % primary α; the other 18.8 % is liquid that becomes eutectic α + β at 779 °C.

## Q2 - Aluminium–copper, 20 wt% Cu

Taught in: [[FEEG1002 C6 - Phase Diagrams#Tie lines give the compositions]], [[FEEG1002 C6 - Phase Diagrams#A hypoeutectic alloy]] and [[FEEG1002 C6 - Phase Diagrams#5. Intermetallic compounds and general rules]].

**(a) First α.** The 20 wt% Cu line meets the liquidus at about $\boxed{600\ ^\circ\mathrm C}$ (digitised: 601 °C).

**(b) Liquid composition at that temperature.** At the instant the first solid appears, essentially all the alloy is still liquid, so the liquid has the overall composition, $\boxed{20\ \text{wt\% Cu}}$. (The tiny amount of first α has the composition at the other end of the tie line, about 3 wt% Cu.)

**(c) Liquid composition at the eutectic temperature.** As primary α forms, the liquid becomes richer in copper, following the liquidus down. At the eutectic temperature, 548 °C, it has the eutectic composition, $\boxed{\approx33\ \text{wt\% Cu}}$.

**(d) Microstructure at 500 °C.** Start in the liquid. Crossing the liquidus, primary α (aluminium-rich) dendrites form. Crossing the eutectic isotherm at 548 °C, the α stays, and the remaining liquid becomes eutectic α + θ, where θ is the intermetallic CuAl₂. At 500 °C the structure is primary α dendrites (cells) surrounded by stripy (lamellar) eutectic of α and θ. Just above 548 °C the primary α is $(33-20)/(33-5.65)=48\ \%$ of the alloy, taking the α limit as 5.65 wt% Cu, so roughly half primary α and half eutectic. It is not a mixture of separate α and θ grains.

## Q3 - Steels

Taught in: [[FEEG1002 C7 - Steels and Precipitation Hardening#Phases and microconstituents]] and [[FEEG1002 C7 - Steels and Precipitation Hardening#3. Microstructures of hypo- and hypereutectoid steels]].

![[m7_fe_fe3c.png|900]]

**(a) Phase and microconstituent.** A phase is a homogeneous portion of the system with uniform physical and chemical characteristics, such as ferrite or cementite. A microconstituent is an identifiable element of the microstructure that may consist of more than one phase. Pearlite is a microconstituent made of two phases, ferrite and cementite, in alternating plates.

**(b) Hypo- and hypereutectoid.** A hypoeutectoid steel has less carbon than the eutectoid composition (below 0.76 wt% C) and ends as proeutectoid ferrite plus pearlite. A hypereutectoid steel has more (0.76 to 2.14 wt% C) and ends as proeutectoid cementite plus pearlite.

**(c) Eutectoid and proeutectoid ferrite.** Proeutectoid ferrite forms from austenite above 727 °C, while the steel cools through the α + γ field, nucleating on the austenite grain boundaries. Eutectoid ferrite forms at 727 °C by the eutectoid reaction, as the plates of ferrite inside pearlite, alongside the cementite. Both are the same phase, α, and at 727 °C both contain $\boxed{0.022\ \text{wt\% C}}$, the maximum solubility of carbon in ferrite.

**(d) Proeutectoid ferrite and pearlite in 0.35 wt% C.** Just above 727 °C the tie line runs from ferrite (0.022) to austenite of eutectoid composition (0.76):

$$
f_{\alpha,pro}=\frac{0.76-0.35}{0.76-0.022}=\frac{0.41}{0.738}=\boxed{0.556}
$$

$$
f_P=\frac{0.35-0.022}{0.76-0.022}=\frac{0.328}{0.738}=\boxed{0.444}
$$

55.6 % proeutectoid ferrite and 44.4 % pearlite.

**(e) Ferrite and cementite at 500 °C in 0.35 wt% C.** Now the total amounts of the two phases are asked for, across the whole α + Fe₃C field, with the given solubility of 0.015 wt% C at 500 °C:

$$
f_\alpha=\frac{6.70-0.35}{6.70-0.015}=\frac{6.35}{6.685}=\boxed{0.950}
$$

$$
f_{Fe_3C}=\frac{0.35-0.015}{6.70-0.015}=\frac{0.335}{6.685}=\boxed{0.050}
$$

95.0 % ferrite (proeutectoid and eutectoid together) and 5.0 % cementite.

**(f) 1.3 wt% C at 600 °C.** Start in austenite. Crossing the boundary into γ + Fe₃C (at about 900 °C for this composition), proeutectoid cementite nucleates on the austenite grain boundaries; at 727 °C the remaining austenite, now 0.76 wt% C, transforms to pearlite. At 600 °C the microstructure is pearlite colonies enclosed by a continuous network of proeutectoid cementite along the prior austenite grain boundaries. The proeutectoid cementite is

$$
f_{Fe_3C,pro}=\frac{1.3-0.76}{6.70-0.76}=\frac{0.54}{5.94}=0.091
$$

about 9 %, with 91 % pearlite.

![[m7_steel_microstructures.png|900]]

## Q4 - Precipitation hardening

Taught in: [[FEEG1002 C7 - Steels and Precipitation Hardening#Choosing the alloy from the phase diagram]] and [[FEEG1002 C7 - Steels and Precipitation Hardening#The ageing curve]].

**(a) Choice of composition.** The diagram is the aluminium–copper diagram drawn back to front, with element A (copper) increasing to the left and the α field on the right. Choose an alloy on the α side whose vertical line passes through the single-phase α field at high temperature and crosses the sloping solvus into α + θ on cooling: between nearly 0 and about 5.6 wt% A, the maximum solubility of A in α at the eutectic temperature (548 °C). Around **4 wt% A** is a good choice, the classic Al–4Cu alloy. The reason is the three-step treatment it allows: solution treatment at about 550 °C puts all of A into solution in α (below the solidus, so nothing melts); a quench traps it as supersaturated α; ageing at a low temperature, inside α + θ, then precipitates a fine dispersion of θ-type particles inside the grains. An alloy above about 5.6 wt% A cannot be fully dissolved, and one with almost no A has too little to precipitate.

**(b) Why strength peaks.** During ageing the precipitates pass from GP zones through coherent θ″ to partly coherent θ′ and finally to incoherent θ. Early on (under-aged) the particles are small and coherent, and dislocations can cut through them; the strength rises as more form. At the peak the combination of number, size, spacing and coherency is the best: many fine particles that must be cut at high stress or, where they are incoherent, bowed round at close spacing. With longer ageing (over-aged) the particles coarsen: fewer, larger, more widely spaced incoherent θ particles that dislocations bow round easily, so the strength falls. The yield strength is the sum of falling solid-solution strengthening, rising then falling coherency and cutting stresses, and rising bowing stress, and that sum has a maximum at an intermediate time.

![[m7_ageing_curve.png|900]]

## Sources

- `Tutorial Sheet 03 - Phase Diagrams.pdf`: Q1–Q4, with the Ag–Cu, Al–Cu, Fe–Fe₃C and reversed Al–Cu diagrams. No solutions are provided. Values printed on the diagrams were used as given; the liquidus and solidus readings in Q1 and Q2 were digitised from the sheet's figures. The least certain answer is Q1(b), the composition of the first α (about 5.5 wt% Ag), because the solidus is steep there.
