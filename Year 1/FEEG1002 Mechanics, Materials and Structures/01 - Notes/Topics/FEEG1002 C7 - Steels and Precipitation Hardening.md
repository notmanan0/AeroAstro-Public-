---
title: "FEEG1002 C7 - Steels and Precipitation Hardening"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part C: Materials"
order: 22
tags: [feeg1002, materials, steel, iron-carbon, eutectoid, precipitation-hardening]
aliases: ["Materials Lectures 10 and 11", "Iron carbon diagram", "Age hardening"]
date: 2026-09-25
status: complete
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: ["[[FEEG1002 C6 - Phase Diagrams]]", "[[FEEG1002 C5 - Strengthening Mechanisms and Annealing]]"]
next_topics: ["[[FEEG1002 C8 - Fracture - Brittle, Ductile and Fracture Mechanics]]"]
key_concepts: ["[[Iron-Carbon Phase Diagram]]", "[[Precipitation Hardening]]", "[[Eutectic and Eutectoid Reactions]]"]
tutorial_sheets: ["[[FEEG1002 Materials Tutorial 3 - Phase Diagrams Solutions]]"]
sources: ["02 - Sources/Materials/Lectures/Lecture 10 - Steels.pdf", "02 - Sources/Materials/Lectures/Lecture 11 - Precipitation Hardening.pdf"]
---

# FEEG1002 C7 - Steels and Precipitation Hardening

> [!abstract] Summary
> In steel, carbon solubility and iron's FCC/BCC transformation create the eutectoid reaction $\gamma\rightarrow\alpha+Fe_3C$. Below 727°C, hypoeutectoid steel is proeutectoid ferrite + pearlite; hypereutectoid steel is proeutectoid cementite + pearlite. Precipitation hardening uses a phase diagram plus diffusion kinetics to form a fine obstacle distribution inside a matrix.

## Key Concepts
- [[Iron-Carbon Phase Diagram]] · [[Precipitation Hardening]] · [[Eutectic and Eutectoid Reactions]]

---

## 1. Phases and microconstituents in steel

| Name | Meaning | Key property |
|---|---|---|
| austenite $\gamma$ | interstitial C solution in FCC Fe | high-temperature phase; high C solubility |
| ferrite $\alpha$ | interstitial C solution in BCC Fe | soft/ductile; very low C solubility |
| cementite $Fe_3C$ | fixed 6.70 wt% C intermetallic | hard and brittle |
| pearlite | lamellae of $\alpha+Fe_3C$ | **microconstituent**, not a phase |

The eutectoid reaction near 727°C and 0.76 wt% C is

$$\gamma\rightarrow\alpha+Fe_3C$$

![[m7_steel_eutectoid.png|800]]

## 2. Microstructure on slow cooling
- **Eutectoid steel**: austenite remains single phase until 727°C, then transforms entirely to pearlite.
- **Hypoeutectoid** ($C_0<0.76\%$): proeutectoid ferrite nucleates first at prior-austenite grain boundaries; the remaining austenite enriches to 0.76% C and becomes pearlite.
- **Hypereutectoid** ($C_0>0.76\%$): proeutectoid cementite forms first at the boundaries; remaining austenite becomes pearlite.
- Pearlite is lamellar because carbon must partition into cementite while ferrite rejects it; short diffusion paths enable rapid cooperative growth.

> [!example] 0.35 wt% C steel just below 727°C
> With $C_{\alpha E}=0.022$ and $C_E=0.76$ wt% C:
>
> $$f_{proeutectoid\ \alpha}=\frac{0.76-0.35}{0.76-0.022}=0.556,qquad f_P=0.444$$

At 500°C the **total phase** fractions use $C_\alpha=0.015$ and $C_{Fe_3C}=6.70$:

$$f_\alpha=\frac{6.70-0.35}{6.70-0.015}=0.950,qquad f_{Fe_3C}=0.050$$

## 3. Precipitation-hardening requirements
Choose a composition with:
- appreciable solubility at a high solution-treatment temperature;
- much lower solubility at the ageing temperature;
- a second phase that can precipitate inside the matrix.

The three-stage treatment (e.g. Al-Cu) is:
1. **solution treat** in the single-$\alpha$ field to dissolve solute;
2. **quench** to retain a supersaturated solid solution;
3. **age** below the solvus so fine precipitates nucleate and grow.

## 4. Under-ageing, peak ageing and over-ageing
- early clusters/coherent precipitates are small and often shearable;
- an optimum size/spacing/coherency gives peak strength;
- prolonged or hot ageing causes coarsening, loss of coherency and larger obstacle spacing: **over-ageing**.

![[m7_ageing_curve.png|760]]

Because the process is diffusion controlled, higher temperature reaches the peak much faster but can give a lower peak strength. The lecture data range from roughly one month at 121°C to one minute at 260°C.

> [!warning] Common traps
> - Quenching is not the strengthening step by itself; it preserves supersaturation for ageing.
> - Pearlite is not a phase.
> - “Primary” or “proeutectoid” fraction and “total phase” fraction are different lever-rule calculations.
> - Operating temperature can unintentionally over-age or dissolve strengthening precipitates.

## Year 2 bridge
- This equilibrium treatment omits time-temperature-transformation and continuous-cooling-transformation kinetics, martensite and tempering, developed in [[SESA2028 M7 - Steels - Phase Transformations, Heat Treatment and Alloying]].

## Links
- Previous: [[FEEG1002 C6 - Phase Diagrams]] · Next: [[FEEG1002 C8 - Fracture - Brittle, Ductile and Fracture Mechanics]]
- Worked problems: [[FEEG1002 Materials Tutorial 3 - Phase Diagrams Solutions]]

## Sources
- Materials Lectures 10–11; audited against [[FEEG1002 Materials L10 Contact Sheet.png]] and [[FEEG1002 Materials L11 Contact Sheet.png]].

