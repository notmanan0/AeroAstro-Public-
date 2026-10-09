---
title: "SESA2028 M6 - Light Alloys - Aluminium, Magnesium, Beryllium and Titanium"
module: "SESA2028 Aerospace Materials & Structures"
type: topic
stream: "Materials"
order: 6
tags: [sesa2028, materials, aluminium, magnesium, beryllium, titanium, precipitation-hardening, light-alloys]
status: complete
parent: ["[[SESA2028 Aerospace Materials & Structures Hub]]"]
prerequisites: ["[[SESA2028 M4 - Polymer Matrix Composites]]"]
next_topics: ["[[SESA2028 M7 - Steels - Phase Transformations, Heat Treatment and Alloying]]"]
key_concepts: ["[[Hall-Petch Relation]]", "[[Precipitation Hardening]]", "[[Titanium Alloy Classes]]", "[[Specific Stiffness and Strength]]"]
tutorial_sheets: ["[[SESA2028 Materials Tutorial MT4 - Alloy Design Solutions]]"]
sources: ["02 - Sources/Materials Lectures/Lightweighting 2025.pdf (lectures 8-9)", "02 - Sources/Materials Lectures/Lightweighting 2026 SESA2028 ML8.pptx", "mini lectures ML8a, ML8b, ML8c, ML9a, ML9b, ML10a"]
---

# SESA2028 M6 - Light Alloys - Aluminium, Magnesium, Beryllium and Titanium

> [!abstract] Summary
> The "light metals" (Al, Mg, Ti, Be) are grouped only by low density; metallurgically they are very different. **Aluminium** gets its strength from **precipitation hardening** (solution treat, quench, age), plus grain size, solute and work hardening. Wrought alloys beat cast alloys because processing controls grain structure, precipitates **and defects**. **Magnesium** is HCP, so it is hard to work and mostly cast. **Beryllium** is superbly stiff but toxic and brittle. **Titanium** has an $\alpha$ (HCP) / $\beta$ (BCC) transformation that gives three alloy classes, each controlled by composition and heat treatment. That classification is examined almost every year.

## 1. The light metals as a group

| Metal | Density (g/cm³) | Structure | Headline |
|---|---:|---|---|
| Mg | 1.74 | HCP | lightest structural metal; castable; low stiffness; poor corrosion |
| Be | 1.85 | HCP | $E\approx300$ GPa, specific stiffness ~6× steel; toxic |
| Al | 2.70 | FCC | versatile, heat-treatable, conductive, coherent oxide |
| Ti | 4.51 | HCP ($\alpha$) / BCC ($\beta$) | high specific strength, temperature capability, corrosion, biocompatible |
| Fe (for comparison) | 7.87 | BCC/FCC | |

Polmear's chart of **comparative weight for equal-stiffness beams** shows a big drop from steel to Ti, Al, Mg and Be, which is lightest.

It is not just weight:

- **Corrosion**: Ti has an especially coherent oxide; Al is good too.
- **Electrical**: Al's excellent conductivity forms the lightning-strike cage in aircraft.
- **Manufacturing and supply chain**: light alloys are available and processable, unlike exotic CMCs.

## 2. Aluminium alloy series

| Series | Main alloying | Heat treatable? | Use |
|---|---|---|---|
| 1xxx | ≥ 99 % Al | no (work hardened) | food and chemical plant, heat exchangers, reflectors, conductors |
| 2xxx | **Cu** | yes | **aerospace**: damage-tolerant lower wing and fuselage (2024) |
| 3xxx | Mn | no | cans, roofing |
| 4xxx | Si | no | filler wire, brazing |
| 5xxx | Mg | no | marine, ship superstructures |
| 6xxx | Mg + Si | yes | **automotive and architectural** extrusions, trucks, rail, canoes, pipelines |
| 7xxx | **Zn + Mg** (+Cu) | yes | **aerospace high strength**: upper wing, spars (7075-T6 strongest) |
| 8xxx | misc. incl. **Li** | yes | aerospace Al-Li (lower density, higher $E$) |

Temper designations: **T4** = solution treated and **naturally** aged; **T6** = solution treated and **artificially** aged to peak strength.

## 3. How to strengthen a metal: make life hard for dislocations

All five mechanisms work through interactions between the **local stress/strain field of a dislocation** and a microstructural feature.

| Mechanism | Obstacle | Al alloys |
|---|---|---|
| **Grain size** | grain boundaries | yes |
| **Solid solution** | solute atoms | Cu, Zn, Mg, Si in $\alpha$-Al |
| **Work (strain) hardening** | other dislocations | Al cold-works easily |
| **Precipitation hardening** | precipitates | yes: the main mechanism in 2xxx/6xxx/7xxx |
| **Transformation hardening** | new phases (martensite) | **no**: that one belongs to steels (and Ti) |

### Grain size: Hall-Petch

A dislocation cannot cross a grain boundary (the lattice it lives in changes orientation), so dislocations **pile up** against it. The stress fields of the piled-up dislocations add together and eventually trigger slip in the next grain. Finer grains mean more barriers **and** shorter pile-ups, so a higher applied stress is needed:

$$
\sigma_y=\sigma_0+k_y\,d^{-1/2}.
$$

Grain refinement is the **only** mechanism that raises strength *and* toughness together. See [[Hall-Petch Relation]].

### Solid solution

A smaller substitutional atom (which puts the lattice around it in tension) sits on the compressive side of an edge dislocation; a larger one sits on the tensile side; interstitials sit in the core. Each **relaxes the strain field and pins the dislocation**, so extra stress is needed to pull it free.

### Work hardening

Dislocations multiply and tangle (the lecturer calls it a "dislocation party": like dislocations repel, opposite ones attract and annihilate). Reloading needs a higher stress, and elongation falls.

### Precipitation (age) hardening

- **Coherent** precipitates (lattice continuous with the matrix) must be **sheared** by the dislocation, which costs extra interface and ordering energy. Small ones are sheared easily.
- **Incoherent** precipitates are internal phase boundaries that dislocations cannot cut. The dislocation **bows out between them** (Orowan looping) and leaves a loop behind. The required stress $\propto 1/\text{spacing}$, so **the distribution and spacing matter more than the volume fraction**.

![[Figures/materials_ageing_curve.png]]

**The three-step treatment (Al-Cu):**

1. **Solution treat** at about 550 °C, in the single-phase $\alpha$ field: all the Cu dissolves.
2. **Quench** (water): no time to diffuse, giving a **supersaturated** solid solution.
3. **Age** at about 120 °C, inside the two-phase field: diffusion forms fine, metastable, coherent $\theta'$. Ageing speeds up diffusion but is below the solvus, so nothing re-dissolves.

The ageing curve rises through **under-aged** (fine, sheared precipitates), reaches **peak aged** (T6: optimum size and spacing), then falls into **over-aged**. Over-ageing is coarsening: small precipitates dissolve to feed larger ones, which lowers the total interfacial energy (area $\propto r^2$, volume $\propto r^3$). The spacing grows and the strength falls.

**TTT diagrams in Al** (for example AA7075, with the T6 route drawn on) show when each precipitate forms at each temperature. They are built by holding at temperature, sampling at intervals, and measuring 1 % and 99 % transformed. See [[Precipitation Hardening]].

### Key Al alloy systems

| | 2xxx (Al-Cu) | 7xxx (Al-Zn-Mg) | 8xxx (Al-Li) |
|---|---|---|---|
| Precipitates | $\theta'\to\theta\ (\mathrm{Al_2Cu})$ | $\eta'$, $\eta$, T | $\delta'$, $\delta$ |
| Character | ductile, formable, lower strength, **damage tolerant** | **highest strength** | lower density, higher stiffness |
| Aero use | lower wing skin, fuselage (tension, fatigue critical) | upper wing (compression, strength critical) | skins, stringers |

Transmission electron microscopy of 7xxx shows rod-like, blocky and fine precipitates, plus **precipitate-free zones (PFZs)** alongside grain boundaries. There, fast boundary diffusion drained the solute into coarse boundary precipitates. PFZs are soft and electrochemically different, which affects both toughness and corrosion.

## 4. Wrought vs cast aluminium

A favourite exam question. The lecturer's 2026 slide notes: "I do set exam questions on manufacturing", meaning casting pros and cons.

**Wrought**: cast as an ingot, then heavily worked into plate, sheet, foil, extrusions, tube, rod, bar and wire. Deformation, **recrystallisation** and heat treatment together control:

- **grain size and shape** (fine, or elongated and aligned along the working direction);
- **precipitate type, size and distribution** (solution treat, quench, age);
- **dislocation density** (work hardening, e.g. H tempers);
- **texture**;
- and they **close porosity and break up casting defects and coarse intermetallics**.

Aerospace funded this development: the balance of strength and toughness, damage tolerance, and corrosion resistance.

**Cast**: sand, die or investment moulds. A tapered sprue gives smooth, non-turbulent filling (turbulence entrains oxide, slag and gas), cores make internal cavities, and feeders supply metal to make up solidification shrinkage.

| Cast: advantages | Cast: disadvantages |
|---|---|
| near-net shape, so minimal machining ("metal bashing") | **defects**: shrinkage cavities, **interdendritic porosity** (poor liquid feeding between dendrites), oxide films, gas pores |
| complex shapes, internal passages | **coarse dendritic** microstructure; segregation; coarse brittle intermetallics |
| cheap at high volume (pistons) | **low elongation, toughness and fatigue strength**: defects initiate cracks |
| | cannot use work hardening to refine grains |

**Why cast is worse (2013-14 B2(i)):** the **defect population** (pores, oxides, shrinkage) plus a coarse, segregated structure. Every pore is a crack starter. So cast Al is used where the part is **not load-bearing** and does not need high toughness or fatigue strength, but benefits from a complex shape: housings, pump bodies, wheels.

## 5. Welding aluminium: the 2024 research case study (ML10a)

Airframes are usually **riveted**, because welding destroys the carefully engineered solution-treated, quenched and aged microstructure. Rivet holes are a fatigue concern of their own. Southampton, Cranfield and Airbus studied VPPA (variable-polarity plasma arc) and MIG welds.

| Zone | What happens |
|---|---|
| **Fusion zone** | a cast dendritic structure; solute rejected into brittle interdendritic intermetallics; **gas porosity** (gas is less soluble on cooling); **tensile residual stress** from contraction |
| **Partially melted zone** | coarse particles, grain-boundary decoration, incipient melting |
| **Heat-affected zone** | precipitates coarsen, or clusters dissolve and re-form, giving hardness peaks and troughs across the weld |

- Techniques: FEG-SEM, DSC (heats of phase formation and dissolution), TEM (phase identification), EDX (composition), EBSD (grains), hardness mapping, X-ray and neutron diffraction (residual stress).
- S-N results ($R=0.1$): parent plate beats both welds, especially at low stress range. **MIG** cracks started at fusion-zone **porosity**; **VPPA** cracks started in the **HAZ at residual-stress peaks**.
- A **short-crack model** used probabilistic defect sizes. Short cracks accelerate and decelerate at grain boundaries, then tend towards Paris behaviour. Coalescence of rows of cracks is the Aloha Airlines scenario. Life to a 1 mm crack was about 50 % of total MIG life, so residual stress must be included for accurate prediction.

## 6. Beryllium

- Extremely stiff ($E\approx300$ GPa), a third lighter than Al, specific stiffness about **6× steel**.
- **Why it is rare**: a niche supply chain, hard to make (powder metallurgy), **highly toxic** (health-and-safety cost), poor toughness.
- **Space**: light, very rigid deployable structures with good thermal properties (low distortion during launch). The JET fusion reactor lining is Be + W.
- **Functional uses**: transparent to X-rays; slows and reflects neutrons. It is mostly used as an **alloying addition** in Cu-Be (conductivity plus strength).

## 7. Magnesium

- The lowest density of any structural metal.
- **HCP**: only the basal plane is close-packed. At room temperature there are too few slip systems, and non-basal slip is **thermally activated**. So yield stress depends on temperature, there is a DBT, formability is poor, and **wrought alloys are limited**.
- **Good for casting**: a low melting point allows precision **die-casting** in permanent tool-steel moulds.
- **Low stiffness** ($E\approx45$ GPa), so there is little specific-stiffness gain over Al. Relatively **poor corrosion** (it is very anodic).
- Used where a **low-strength, thick but light** part is needed: geometric spacers, casings.

**Designations and alloys** (lecture table, after Callister). Mg is mostly alloyed with **Al, Mn and Zn**, plus Zr (grain refiner), rare earths and Th (creep resistance).

| Alloy | Composition | Condition | UTS/YS (MPa), %El | Use |
|---|---|---|---|---|
| AZ31B | 3Al 1Zn 0.2Mn | extruded (wrought) | 262/200, 15 | structures and tubing, cathodic-protection anodes |
| HK31A | 3Th 0.6Zr | strain hardened, partially annealed | 255/200, 9 | high strength up to ~315 °C |
| ZK60A | 5.5Zn 0.45Zr | artificially aged (wrought) | 350/285, 11 | maximum-strength aircraft forgings |
| AZ91D | 9Al 0.7Zn 0.15Mn | as cast | 230/150, 3 | die-cast automotive, luggage, electronics |
| AM60A | 6Al 0.13Mn | as cast | 220/130, 6 | automotive wheels |
| AS41A | 4.3Al 1Si 0.35Mn | as cast | 210/140, 6 | creep-resistant die castings |

**Wrought** alloys have higher yield strength and ductility. **Cast** alloys have more Al and lower yield strength and elongation, because of casting defects. Applications are where low weight is critical and structural demands are modest: gearbox casings, steering wheels, wheels, laptop cases.

> [!example] 2024-25 MQ1(a,b): why forge Mg hot, and how is grain size controlled?
> - **Hot working**: at room temperature only basal slip operates. That is fewer than the 5 independent slip systems needed for general plasticity, so Mg cracks. Heating thermally activates non-basal (prismatic, pyramidal) slip, above the DBT, so large strains become possible.
> - **Grain size**: working stores dislocations (stored energy). A subsequent anneal (or dynamic recrystallisation during hot working) nucleates new strain-free grains. More prior strain gives more nuclei and a **finer** grain size. Anneal time and temperature must be limited to stop grain growth. Zr (in ZK60A, HK31A) is a potent **grain refiner**.
> - **Other features the heat treatment sets**: precipitates (ZK60A is **artificially aged**, forming fine Zn-rich precipitates that give the highest strength, 350 MPa); solute in solution (Al and Zn in AZ31B give solid-solution strengthening, and the extruded condition keeps some work hardening); recovery of dislocation density; texture.
> - Strength then comes from Hall-Petch + solid solution + precipitates (+ retained work hardening).

## 8. Titanium alloys

### Phases and stabilisers

Ti transforms from **$\beta$ (BCC)** at high temperature to **$\alpha$ (HCP)** on cooling. Alloying moves the boundary between them:

- **$\alpha$ stabilisers**: Al, Ga, Ge, C, O, N. They raise the transus.
- **$\beta$ stabilisers**: Mo, V, Ta, Nb, Mn, Fe, Cr, Co, Ni, Cu, Si. They lower it.

On a generic phase diagram against $\beta$-stabiliser content, rapid cooling from $\beta$ gives **$\alpha'$ martensite** below the $M_s$/$M_f$ lines. This is a diffusionless shear transformation to a metastable phase, the same idea as in steel (2024-25 MQ1(c)). The difference is that steel martensite is hard because of **trapped interstitial carbon** distorting a BCT lattice. Ti $\alpha'$ is an HCP phase supersaturated with substitutional $\beta$ stabilisers, so it is only moderately harder. Its value is as a fine, metastable structure that can later be aged or decomposed into fine $\alpha+\beta$ for strength.

### The classes

| Class | Microstructure and strengthening | Heat treatment | Properties | Typical use |
|---|---|---|---|---|
| **CP Ti** (effectively Ti-O) | $\alpha$; interstitial O solid solution | annealed | low strength, very ductile, excellent corrosion | shrouds, airframe skins, chemical and marine plant |
| **$\alpha$** (Ti-5Al-2.5Sn) | $\alpha$; Al and Sn substitutional solid solution | annealed | moderate strength, **thermally stable** (no precipitates to coarsen), **good creep**, poor formability (HCP) | engine casings and rings to ~480 °C |
| **Near-$\alpha$** | mostly $\alpha$ + a little $\beta$ (may form $\alpha'$) | complex thermomechanical | creep plus strength | forged compressor discs, blades |
| **$\alpha+\beta$** (Ti-6Al-4V, the workhorse) | $\alpha$ + $\beta$; microstructure set by heat treatment | annealed or STA | the best-balanced alloy | implants, airframe, fan blades, chemical plant |
| **$\beta$ / metastable $\beta$** (Ti-10V-2Fe-3Al) | $\beta$ matrix + fine $\alpha$ precipitates | **solution treat, quench, age** (like Al) | **highest strength** (solid solution + precipitates), formable in the solution-treated BCC state, creep resistant to intermediate $T$ | high-strength airframe forgings, landing gear |

$\beta$ alloys have drawbacks: 7-10 % **denser** than Ti-6-4, ingot **segregation** (high alloy content, dendritic), and they are **not thermally stable** at high temperature because the precipitates coarsen.

### Ti-6Al-4V: same composition, different microstructures

1. **Slow cool from the $\beta$ field**: $\alpha$ laths form in a **"basket-weave"** (Widmanstätten) pattern. The crack path is tortuous, so it resists **crack propagation**. It is tough and damage tolerant.
2. **Anneal in the $\alpha+\beta$ field**: **equiaxed $\alpha$** + transformed $\beta$ ($\alpha'$). Small grains confine slip and resist **crack initiation**, giving the best HCF resistance.

**Which Ti alloys have the best fatigue resistance?** $\alpha+\beta$ alloys (Ti-6-4), because the microstructure can be tailored: fine equiaxed $\alpha$ against initiation, lamellar or bimodal against propagation. See [[Titanium Alloy Classes]].

### Strength-toughness trade-off

Alloy development has run from 1960s Ti-6-4, through **$\beta$-annealed** (basket-weave, tougher) grades in the 1980s, to high-strength forgings. **Improving toughness at high strength is very difficult**, the same trade-off as in [[SESA2028 M1 - Fracture, Toughness and Fracture Mechanics|M1]].

### Why titanium?

High **specific strength**; temperature capability up to about 500-600 °C; **corrosion resistance** from an adherent $\mathrm{TiO_2}$ film; **biocompatibility** (bone grows onto it); non-magnetic. Uses: hip implants, dental posts, spinal implants; F1 rocker arms; golf clubs; 3D-printed bicycles; **wide-chord hollow fan blades** (superplastic forming + diffusion bonding of three sheets with internal bridging struts); anodised jewellery, where the colour is set by oxide thickness.

## 9. Exam checklist

- [ ] For "how does alloying/processing raise specific strength of Al" (MT4 Q1): **name each mechanism, the obstacle, and how processing controls it**.
- [ ] For "raise specific stiffness of Al": Li additions (lower $\rho$, higher $E$: 8xxx) or particulate or fibre reinforcement (MMC). **Heat treatment does not change $E$.**
- [ ] Describe the solution-treat, quench, age sequence with **what the microstructure is at each stage**.
- [ ] Cast vs wrought: defects + coarse structure vs worked, recrystallised, controlled precipitates.
- [ ] Ti: three classes, stabilisers, and **one application each, justified by properties**.

## Related

- [[SESA2028 Materials Tutorial MT4 - Alloy Design Solutions]].
- [[SESA2028 M7 - Steels - Phase Transformations, Heat Treatment and Alloying]]: transformation hardening and martensite.
- [[SESA2028 M5 - Metal and Ceramic Matrix Composites and Hybrid Laminates]]: Ti as an MMC matrix.
- [[Bypass Ratio and Fan Pressure Ratio]] (SESA2023): hollow Ti vs CFRP fan blades.
