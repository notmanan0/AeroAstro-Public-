---
title: "SESA2028 M5 - Metal and Ceramic Matrix Composites and Hybrid Laminates"
module: "SESA2028 Aerospace Materials & Structures"
type: topic
stream: "Materials"
order: 5
tags: [sesa2028, materials, composites, mmc, cmc, fibre-metal-laminates, glare]
status: lectured
coverage: "Mini-lectures ML7a and ML7b"
date: 2026-10-30
parent: ["[[SESA2028 Aerospace Materials & Structures Hub]]"]
prerequisites: ["[[SESA2028 M4 - Polymer Matrix Composites]]"]
next_topics: ["[[SESA2028 M6 - Light Alloys - Aluminium, Magnesium, Beryllium and Titanium]]"]
key_concepts: ["[[MMC vs CMC]]", "[[Fibre Metal Laminates]]", "[[Rule of Mixtures]]"]
tutorial_sheets: ["[[SESA2028 Materials Tutorial MT3 - Lightweighting Solutions]]"]
sources: ["02 - Sources/Materials Lectures/Lightweighting 2025.pdf (lecture block 7)", "02 - Sources/Materials Lectures/mini lecture videos/ML7a Metal matrix composites_default.txt", "02 - Sources/Materials Lectures/mini lecture videos/ML7b Ceramic matrix composites_default.txt"]
---

# SESA2028 M5 - Metal and Ceramic Matrix Composites and Hybrid Laminates

> [!abstract] Summary
> A polymer matrix is easy to process precisely because it softens at low temperature, which also caps the composite's service temperature. A metal matrix (MMC) raises that cap and starts from better matrix properties; its main purpose is specific stiffness, with wear resistance and tailored thermal properties as other uses, not toughness. A ceramic matrix (CMC) goes hotter still, and there the ceramic fibres are not there to stiffen a matrix that is already stiff but to toughen it, by bridging cracks and pulling out. Both are made at high temperature, from expensive ingredients, with fibre–matrix reactions to manage, so they stay niche. Fibre metal laminates such as GLARE bond aluminium sheets with composite plies, so that intact fibres bridge a fatigue crack in the metal and its driving force falls instead of rising.

> [!summary]- Exam use: quick path
> - **Use it when:** asked what a metal or ceramic matrix offers over a polymer, why MMCs have not reached their potential, how fibres toughen a ceramic, which fibre to put in a titanium or ceramic matrix, or why GLARE resists fatigue.
> - **Assumptions:** rule of mixtures for stiffness, strength and density; continuous aligned fibres; perfect bonding (for MMCs) or a deliberately weak interface (for CMCs).
> - **Method:** 1. Say what the matrix contributes: temperature, matrix properties, toughness. 2. Find $V_f$ for each requirement, $V_f=(P-P_m)/(P_f-P_m)$, and take the larger. 3. Composite density $\rho_c=V_f\rho_f+V_m\rho_m$. 4. Reject any $V_f$ above about 0.65 or any fibre that reacts with the matrix. 5. Weigh toughness, temperature limit, manufacture and cost.
> - **Common mistakes:** saying MMCs are used mainly for toughness (it is specific stiffness, ML7a, ll. 51–54); saying CMC toughness comes from the matrix (it comes from fibre bridging and pull-out, ML7b, ll. 75–87).
> - **Example:** [[#Fibre for a titanium MMC blade]]. **Exercise:** [[SESA2028 Materials Tutorial MT3 - Lightweighting Solutions]], Q4.

Polymer matrix composites have one weakness the fibres cannot fix: the matrix. Everything that makes a resin easy to use, low-temperature cure and room-temperature handling, also means it cannot work hot (ML7a, ll. 28–34). This note follows the obvious next steps. Replace the resin with a metal and the composite works at higher temperature from a stronger starting point; replace it with a ceramic and it goes higher still. And combine metal sheets with composite plies to get the best of both in fatigue.

The physical picture changes with the matrix. In a metal matrix the metal is already tough and ductile, and the stiff ceramic fibres or particles are added to raise stiffness per unit mass, even though a metallurgist normally spends a career getting brittle particles out of metals (ll. 43–54). In a ceramic matrix the matrix is stiff, hot-strong and inert but brittle, so a crack would run straight through it; the fibres, being finer and freer of defects, survive the crack and hold it shut. The right fibre–matrix bond is opposite in the two cases: strong in an MMC to transfer load, deliberately weak in a CMC so that fibres can debond and pull out.

## 1. Metal matrix composites

The reinforcement is usually a ceramic, as fibres or particles; the matrix could be any metal, but for lightweighting it is usually a light alloy of aluminium, magnesium or titanium (ML7a, ll. 4–22). The convention writes the matrix first and labels the reinforcement's form: Al–SiC$_f$ is aluminium with silicon carbide fibres, and a subscript $p$ means particles (ll. 23–27).

A metal matrix survives to higher temperature than a resin and starts with better mechanical properties (ll. 35–42). There is a tension, though: adding brittle ceramic particles to a metal is exactly what metallurgists usually try to avoid, because it raises strength while cutting toughness and ductility (ll. 43–50). So the main purpose of an MMC is specific stiffness, not toughness and not really strength (ll. 51–54). An aluminium alloy reinforced with titanium carbide particles shows it: a few per cent of TiC raises the yield stress a little, with a lot of scatter, while the elongation to failure falls sharply as the particles embrittle it (ll. 55–78). The same data show the aluminium's own yield stress rising with strain rate, because dislocations made to move faster need more stress, which matters for crash and impact loading (ll. 60–67).

Fibre-reinforced MMCs reach much higher properties (ll. 79–104). About 41 % carbon fibre in a 6061 aluminium matrix gives a longitudinal modulus of about 320 GPa and tensile strength of 620 MPa; boron fibre at a higher fraction gives less stiffness but much more strength; silicon carbide fibres give other combinations. The type of reinforcement, its chemistry and its volume fraction together set the density, stiffness and strength.

Light-alloy matrices are good at moderate temperatures, but the heat treatments that give them their microstructure stop working when it gets hotter, so the hottest MMCs use cobalt or nickel matrices and give up some lightness (ll. 105–117). Beyond structure, the hard reinforcement greatly improves wear resistance, which is where many MMC applications are, particularly in ground transport, and mixing insulator and metal lets the thermal properties be tuned, a major use in electronics (ll. 118–132).

### Disc, blisk and bling

Material choice can change a design completely (ll. 133–157). A conventional turbine disc carries separate blades in fir-tree slots at its rim, where the high stress, temperature and stress concentration invite creep and fatigue. A blisk makes the blades integral with the disc, removing the joint. With a metal matrix composite ring, the stiff, strong fibres wound round the hoop carry the rotational load, so most of the disc's bore material can be removed, giving a bladed ring, or bling. Putting the right properties in the right place can cut the mass dramatically, and such designs have long been discussed for aero engines.

![[materials_disc_blisk_bling.png|900]]

### Why MMCs have stayed niche

MMCs have limited, niche use because they are hard to make (ll. 158–244). Every route is at high temperature. In the solid state, metal powder, itself expensive because it is made by gas-atomising a stream of molten metal, is mixed with ceramic particles, pressed and sintered so the particles bond by diffusion; or fibres are sandwiched between metal foils and diffusion-bonded under heat and pressure (ll. 168–206). In the liquid or semi-solid state, particles or whiskers are stirred into a mushy alloy and the billet is extruded (stir casting), particles and metal are sprayed together, or molten metal is squeezed round a fibre preform (squeeze casting) (ll. 207–219). Nobody stands round a mould with a roller as in hand lay-up. And at these temperatures the molten metal can react with the ceramic reinforcement, so fibre–matrix reactions must be controlled (ll. 229–235).

The cost therefore comes from two directions: very high quality ingredients, continuous fibres or metal powders, and difficult, slow processes needing specialist equipment (ll. 236–244). The microstructures show the difficulties: extruded short carbon fibres in aluminium partly aligned, with matrix-rich regions and clusters; tungsten wire in copper made by vacuum diffusion bonding of foil; maraging-steel wire in plasma-sprayed aluminium; copper-coated carbon fibres pressed together or woven into a cross-ply (ll. 245–303). A composite-like microstructure can also be grown metallurgically, as in directionally solidified $\mathrm{Ni_3Al}$-based intermetallics (ll. 304–313). By use, ground transport dominates, with electronics and thermal management important and aerospace still a small share (ll. 314–325).

## 2. Fibre metal laminates

A **fibre metal laminate** is a hybrid of thin aluminium sheets and composite prepreg layers stacked like a club sandwich and cured together (ML7a, ll. 326–356). GLARE uses glass-fibre/epoxy plies between 2000-series aluminium sheets; ARALL uses aramid-fibre plies. They were developed for damage-tolerant aircraft structure: fuselage and wing skins (ll. 357–363).

A fatigue crack starts and grows in an aluminium layer in the normal way. When it reaches a composite layer, the interface delaminates locally, but the fibres stay intact and attached, holding the crack faces together behind the tip (ll. 364–384). In a monolithic sheet $\Delta K=Q\Delta\sigma\sqrt{\pi a}$ keeps rising as the crack grows; in the laminate the bridging fibres carry more and more of the load as the crack lengthens, so the stress field at the tip falls and the crack can arrest (ll. 385–401). Growth in the aluminium layers continues but is strongly retarded by delamination and crack bridging, which makes the laminate very damage tolerant.

![[materials_fibre_bridging.png|900]]

## 3. Ceramic matrix composites

At some temperature any metal matrix melts, so for the hottest applications the matrix must be a ceramic (ML7b, ll. 1–8). Ceramics are stiff, inert, insulating and strong in compression, but in tension any small defect is a stress concentration that nothing can relieve, because dislocations hardly move in ceramics and there is no plastic flow to blunt it (ll. 9–16). They are very notch sensitive and very brittle. In a CMC the fibres, typically carbon, silicon carbide or alumina made by high-quality processes, are there to improve the toughness of the surrounding ceramic, to resist the stress-concentrating effect of the flaws in it (ll. 23–27). The matrix is often the same chemistry as the fibre, put down separately, as in carbon–carbon or SiC–SiC composites (ll. 28–31).

Making the matrix is the hard part (ll. 31–67). In polymer infiltration and pyrolysis (PIP), a fibre preform is infiltrated with a pre-ceramic polymer such as polycarbosilane, giving what is at first an ordinary polymer composite; heating to 800–1300 °C pyrolyses the polymer to ceramic, leaving a porous matrix, so the infiltrate-and-pyrolyse loop is repeated four to ten times (ll. 32–48). Alternatively, ceramic whiskers or particles are blended with matrix powder, pressed and sintered under pressure; powder can be carried into a woven or braided preform as a slurry, the liquid burnt off and the matrix sintered; or the matrix can be deposited from vapour inside the preform, chemical vapour infiltration (ll. 49–66). CMCs are even harder and more expensive to make than MMCs (ll. 67–68).

The reward is a ceramic with real toughness (ll. 68–87). A sintered matrix still contains porosity, plenty of small stress concentrations, but cracks growing from them meet fibres that do not break, because the fibres are of higher quality. The fibres bridge the crack, adding a crack-growth resistance term; delamination and crack-front splitting absorb more energy; and when the fibres finally break, they pull out, leaving a fracture surface like a forest of fibres. Because pull-out is a toughening mechanism, the fibre–matrix interface is deliberately made weak. That has a cost: the interfaces are paths for oxidation, so a CMC can have poorer oxidation resistance than a monolithic ceramic (ll. 87–91).

A comparison of specific strength against temperature puts it in context (ll. 92–109): polymer composites lead on specific strength at low temperature, titanium matrix composites beat titanium alloys at slightly higher temperatures, intermetallics and nickel and cobalt alloys reach higher temperatures with lower specific strength, monolithic ceramics are poor because of their brittleness, and alumina in CMC form improves greatly. The uses are the hottest parts of aero engines, where higher temperature means higher efficiency, and rocket nozzles, which must hold their shape briefly at extreme temperature (ll. 109–114). Because CMCs are so expensive, it is worth asking whether the whole part needs to be ceramic or only its surface; a ceramic thermal barrier coating on a metal turbine blade is the other answer ([[Thermal Barrier Coatings]], ll. 115–121).

| | Polymer matrix | Metal matrix | Ceramic matrix |
|---|---|---|---|
| Service temperature | limited by the resin | higher; light alloys moderate, Ni and Co hottest | highest |
| Main purpose of the reinforcement | stiffness and strength | specific stiffness; also wear and thermal properties | toughness |
| Matrix toughness | moderate | high | very low |
| Interface wanted | strong | strong | weak, for pull-out |
| Manufacture | easiest, low temperature | high temperature, solid or liquid routes, reactions | hardest: PIP, sintering, CVI |
| Cost | moderate to high | high | highest |

See [[MMC vs CMC]].

## Worked examples

All numbers recomputed in Python. Neither mini-lecture set a calculation; these are the past-paper versions of the rule-of-mixtures design from [[SESA2028 M4 - Polymer Matrix Composites#Designing to a requirement|M4]], now with density.

### Fibre for a titanium MMC blade

2022-23 MQ2(iii): a compressor blade in a Ti-6Al-4V matrix ($E_m=120$ GPa, $\sigma_m=877$ MPa, $\rho_m=4.43$ g/cm³) must reach $E\ge220$ GPa and $\sigma_y\ge1250$ MPa. For SiC fibre (400 GPa, 3900 MPa, 3.0 g/cm³),

$$
V_f(E)=\frac{220-120}{400-120}=0.357,
\qquad
V_f(\sigma)=\frac{1250-877}{3900-877}=0.123,
$$

so stiffness governs at $V_f=0.357$, and

$$
\rho_c=0.357\times3.0+0.643\times4.43=3.92\text{ g/cm}^3.
$$

| Fibre ($E$ GPa, $\sigma$ MPa, $\rho$ g/cm³) | $V_f(E)$ | $V_f(\sigma)$ | $V_f$ | $\rho_c$ (g/cm³) |
|---|---:|---:|---:|---:|
| SiC (400, 3900, 3.0) | 0.357 | 0.123 | 0.357 | 3.92 |
| Al₂O₃ (379, 1380, 3.95) | 0.386 | 0.742 | 0.742 | 4.07 |
| C (500, 2000, 2.0) | 0.263 | 0.332 | 0.332 | 3.62 |
| W (407, 2890, 19.3) | 0.348 | 0.185 | 0.348 | 9.61 |

Carbon gives the lowest density on paper, but carbon reacts with titanium at processing temperature to form TiC, the reaction problem of ML7a (ll. 229–235), and oxidises in a hot compressor. Alumina needs an impractical fraction, and tungsten more than doubles the density. SiC is the choice: a moderate fraction, low density, and the fibre used in titanium MMC rings.

### MMC or CMC for a hoop

2017-18 A1(iii): a ring needs $E\ge280$ GPa and $\sigma\ge1025$ MPa. The fractions, from the solution note, are 0.55 for Ti/SiC, 0.89 for Ti/Al₂O₃ (impractical), 0.19 for SiC/SiC and 0.60 for SiC matrix with alumina fibre, with specific stiffnesses of 75.8, 73.2, 91.5 and 80.7 GPa·cm³/g. SiC/SiC wins on the numbers, but the ceramic "strengths" in such tables are compressive, the rule of mixtures overstates a brittle matrix in tension, and SiC/SiC has a fracture toughness of only a few MPa√m against about 75 for titanium. For a spinning hoop in tension below titanium's temperature limit, the tough Ti/SiC MMC is the safer answer. The full working is in [[FEEG2005 Exam 2017-18 Solutions]].

## Transcript slips

> [!warning] Mini-lectures ML7a and ML7b
> | Where | Transcript says | Correct |
> |---|---|---|
> | ML7a, l. 23 | "your enforcement" | your reinforcement |
> | ML7a, l. 25 | "or particular is P" | or particulate, subscript $p$ |
> | ML7a, l. 84 | "by the root of mixtures" | by the rule of mixtures |
> | ML7a, l. 85 | "just considering a line fibres" | aligned fibres |
> | ML7a, ll. 87–88 | boron has "a higher Young's modulus than the carbon" yet the composite is less stiff | the carbon in that table is a high-modulus fibre stiffer than boron (about 400 GPa); boron's advantage is strength |
> | ML7a, l. 109 | "this bit of electrical finishes" | this bit of lecture finishes |
> | ML7a, l. 136 | "ferteria fix" | fir-tree fixing |
> | ML7a, l. 163 | "polymetrous composites" | polymer matrix composites |
> | ML7a, l. 214 | "a composite bullet" | a composite billet |
> | ML7a, l. 266 | "microfiber coalescence" | microvoid coalescence |
> | ML7a, l. 306 | "NI3AL" | $\mathrm{Ni_3Al}$ |
> | ML7a, ll. 329, 351 | "glare and aryl" | GLARE and ARALL |
> | ML7a, l. 342 | GLARE "stands for glass laminate aluminium reinforced epoxy" | GLAss REinforced aluminium laminate |
> | ML7b, l. 81 | "stress initiation features" | stress concentration features |
> | ML7b, l. 85 | "energy absorbing turn" | energy-absorbing term |
> | ML7b, l. 104 | "etching up towards the ceramics" | edging up |
> | ML7b, l. 107 | CMC form improves "specific stiffness" | the chart is specific strength against temperature |

## Links

- Parent: [[SESA2028 Aerospace Materials & Structures Hub]]
- Previous: [[SESA2028 M4 - Polymer Matrix Composites]] · Next: [[SESA2028 M6 - Light Alloys - Aluminium, Magnesium, Beryllium and Titanium]]
- Concepts: [[MMC vs CMC]] · [[Fibre Metal Laminates]] · [[Rule of Mixtures]] · [[Specific Stiffness and Strength]]
- Related: [[Thermal Barrier Coatings]] · [[Paris Law]] (the monolithic crack growth that FMLs slow) · [[Spinning Disc Stress]] (the hoop stresses a bling ring carries)
- Tutorial: [[SESA2028 Materials Tutorial MT3 - Lightweighting Solutions]] · past papers: [[FEEG2005 Exam 2016-17 Solutions]] (A1) · [[FEEG2005 Exam 2017-18 Solutions]] (A1) · [[FEEG2005 Exam 2022-23 Solutions]] (MQ2) · [[FEEG2005 Exam 2024-25 Solutions]] (MQ2)

## Sources

- Lightweighting 2025 slides, lecture block 7
- Mini-lecture transcripts ML7a (metal matrix composites and hybrid laminates) and ML7b (ceramic matrix composites)
- Past-paper numbers recomputed in Python

## Self-study tasks

No problems were set in these two mini-lectures; the topic is examined through tutorial MT3 and the past papers below.

### Core

- [ ] Explain why a metal matrix is used and why MMCs have not taken off (ML7a, ll. 28–54, 158–244; MT3 Q4). → [[#1. Metal matrix composites]] · [[#Why MMCs have stayed niche]]
- [ ] Explain how fibres toughen a ceramic matrix and why the interface should be weak (ML7b, ll. 68–91). → [[#3. Ceramic matrix composites]]
- [ ] Fibre choice for the Ti MMC blade (2022-23 MQ2(iii)). → [[#Fibre for a titanium MMC blade]]

### Further practice

- [ ] Explain why a fatigue crack in GLARE slows down as it grows (ML7a, ll. 357–401). → [[#2. Fibre metal laminates]]
- [ ] MMC against CMC for a hoop (2017-18 A1(iii)). → [[#MMC or CMC for a hoop]]
