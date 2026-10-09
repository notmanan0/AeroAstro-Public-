---
title: "SESA2028 M7 - Steels - Phase Transformations, Heat Treatment and Alloying"
module: "SESA2028 Aerospace Materials & Structures"
type: topic
stream: "Materials"
order: 7
tags: [sesa2028, materials, steels, martensite, ttt, jominy, stainless, heat-treatment]
status: complete
parent: ["[[SESA2028 Aerospace Materials & Structures Hub]]"]
prerequisites: ["[[SESA2028 M6 - Light Alloys - Aluminium, Magnesium, Beryllium and Titanium]]", "[[Ductile-Brittle Transition]]"]
next_topics: ["[[SESA2028 M8 - High Temperature Materials - Creep, Oxidation and Superalloys]]"]
key_concepts: ["[[Martensite]]", "[[TTT and CCT Diagrams]]", "[[Hardenability and Jominy Test]]", "[[Tempering]]", "[[Stainless Steel Classes]]", "[[Sensitisation and Weld Decay]]"]
tutorial_sheets: ["[[SESA2028 Materials Tutorial MT4 - Alloy Design Solutions]]"]
sources: ["02 - Sources/Materials Lectures/Ferrous materials 2025.pdf (lectures 11-13)", "mini lectures ML11a, ML11b, ML12a, ML12b, ML13a, ML13b, ML13c"]
---

# SESA2028 M7 - Steels - Phase Transformations, Heat Treatment and Alloying

> [!abstract] Summary
> Steel is versatile because iron changes crystal structure ($\gamma$ FCC to $\alpha$ BCC) on cooling, and carbon dissolves well in one but not the other. **Slow cooling** lets C diffuse: ferrite and pearlite, soft and ductile. **Fast cooling** traps C, and the lattice **shears** into **martensite**: very hard, very brittle. **Tempering** lets C diffuse out into fine carbides, which buys back toughness while keeping most of the strength. TTT and CCT diagrams say how fast to cool; the **Jominy test** says whether a given steel and section will actually harden. Alloying shifts all of this, and at more than 12 % Cr it makes steel **stainless**. "Quench and temper, explain the phase changes" appears in almost every paper.

## 1. Why steel?

Ferrous alloys are the most widely used engineering materials because a **huge range of properties is available at modest cost**. That comes from a bulk supply chain and cheap raw materials. The families are plain carbon (low to high C), alloy steels, stainless steels and tool steels.

**Ship steels** show how far steel development has come ([[Ductile-Brittle Transition]]): grain-size control, low S and P (both segregate to grain boundaries and embrittle them), and higher Mn. Together these moved the Charpy 27 J transition from above room temperature (Titanic plate, Liberty ships) to about $-18$ °C (A36) and about $-35$ °C (1995 averages).

## 2. The Fe-C phase diagram: what you must be able to read

| Phase | Structure | Character |
|---|---|---|
| $\alpha$ ferrite | BCC; very low C solubility (≤ 0.022 %) | soft, ductile, **has a DBT** |
| $\gamma$ austenite | FCC; high C solubility (≤ 2.1 %) | ductile, more solid-solution strengthening, **no DBT** |
| $\mathrm{Fe_3C}$ cementite | intermetallic line compound, 6.67 % C | hard, brittle |
| Pearlite | eutectoid lamellae of $\alpha$ + $\mathrm{Fe_3C}$ (0.76 % C, 727 °C) | many phase boundaries, so strong, less ductile |

Invariant reactions: eutectic $\mathrm{L\to\gamma+Fe_3C}$; **eutectoid** $\gamma\to\alpha+\mathrm{Fe_3C}$; peritectic $\mathrm{L+\delta\to\gamma}$.

$\gamma\to\alpha$ on slow cooling is a **diffusional** transformation: carbon must diffuse away, because $\alpha$ cannot hold it.

- **Hypo-eutectoid** (< 0.76 % C): **pro-eutectoid ferrite** nucleates on the prior-austenite grain boundaries (disordered sites and fast diffusion paths), then the remaining austenite becomes pearlite.
- **Hyper-eutectoid** (> 0.76 % C): **pro-eutectoid cementite** forms on the grain boundaries (a brittle network), then pearlite.

## 3. Slow-cooling treatments

| Treatment | Route | Result |
|---|---|---|
| **Anneal** | heat above the upper critical temperature (fully $\gamma$), **furnace cool** very slowly | coarse pearlite; soft, ductile |
| **Normalise** | heat above the upper critical (also relieves manufacturing residual stress), **air cool** | finer grains and finer pearlite; harder and less ductile than annealed |

## 4. Fast cooling: martensite

When the cooling is too fast for carbon to diffuse:

- the FCC lattice transforms by coordinated **shear**, with no diffusion. The lecturer's image is "soldiers wheeling on a parade ground". It happens at close to the speed of sound;
- a **body-centred tetragonal (BCT)** cell forms inside two FCC cells, stretched along one axis (the **Bain strain**);
- **carbon is trapped** in solution, straining the lattice (the tetragonality grows with C);
- the result is fine **laths** (low C) or plates (high C) in alternating shear directions: **highly dislocated and highly distorted**, so **very hard and very brittle**.

**Athermal**: the transformation starts at $M_s$ and finishes at $M_f$. How much forms depends on **how low the temperature goes, not how long you hold**. Between $M_s$ and $M_f$ you have martensite plus retained austenite.

Martensite hardness rises steeply with C content, about 4× that of pearlite or spheroidite at the same C.

### Bainite

Bainite forms at intermediate cooling rates or hold temperatures (below the TTT nose). It is a **mixture of shear and diffusional** transformation:

- **upper bainite**: $\alpha'$ laths with carbides **between** them;
- **lower bainite**: carbides **within** the laths, closer to martensite.

It looks similar to martensite and is also hard.

See [[Martensite]].

## 5. TTT and CCT diagrams

![[Figures/materials_ttt_critical_cooling_rate.png]]

The phase diagram has **no time axis**, so a time-temperature-transformation (TTT) diagram is needed.

**Isothermal (TTT)**: austenitise, quench to a hold temperature, and measure the fraction transformed against time. Repeat at many temperatures. The results give the **start** (~1 %) and **finish** (~99 %) curves. Example: eutectoid steel at 705 °C starts pearlite at about 5.8 min and finishes at about 67 min.

**Why there is a nose (C-curve):**

- Just below the eutectoid temperature the **undercooling is small**, so the thermodynamic **driving force** for nucleation is small and the start is slow.
- Far below, the driving force is large but **atoms have too little thermal energy to diffuse**, so it is slow again.
- The fastest transformation, the **nose**, is where the two balance: about **540-550 °C** for eutectoid steel, at about 1 s.

**Products by temperature:** coarse pearlite (just below 727 °C), fine pearlite (near the nose), bainite (below the nose), and martensite (horizontal $M_s$ and $M_f$ lines, with $\gamma$ + M between them).

**Continuous cooling (CCT)** is more realistic, because parts are cooled continuously, not held. Its curves sit slightly lower and to the right of the TTT curves.

| Cooling | Product | Treatment |
|---|---|---|
| Furnace | coarse pearlite | anneal |
| Air | fine pearlite | normalise |
| Oil | fine pearlite + bainite + some martensite (plain C) | |
| Water (≥ **critical cooling rate**) | fully martensite | harden |

The **critical cooling rate** is the slowest cooling that just misses the nose.

> [!example] 2024-25 MQ1(d): reading the eutectoid TTT diagram
> **A** = austenite, **P** = pearlite, **B** = bainite, **M** = martensite. **Red** = transformation start, **green** = transformation finish, **solid orange** = $M_s$ (dashed = $M_{50}$, $M_{90}$).
> The nose at about 550 °C comes from the driving force vs diffusion competition above.
> From 700 °C you must reach about 540 °C in about 1 s or less, so roughly $(700-540)/0.8\approx$ **150-200 °C/s**, then carry on below $M_f$.
> A **prolonged hold at 780 °C** gives coarser austenite grains, which means fewer grain-boundary nucleation sites for ferrite and pearlite. The curves move **right**, so a **slower** rate still gives martensite.
> **More Ni** (a $\gamma$ stabiliser) also shifts the curves right (and lowers $M_s$), so a **slower** critical rate works.

See [[TTT and CCT Diagrams]].

## 6. Hardenability and the Jominy test

**Hardenability** is how easily a steel forms martensite **through its section**. It is **not the same as hardness** (that depends mainly on C). It is controlled by composition and austenite grain size.

**Jominy end-quench test (standardised):**

1. Austenitise a standard bar (25 mm diameter × 100 mm).
2. Quench **one end** with a water jet, so the cooling rate falls from about 225 °C/s at the quenched end to about 2 °C/s at the far end.
3. Grind a flat along the bar (to get below the decarburised skin) and measure hardness against distance from the quenched end.

A steep drop means low hardenability (plain C); a flat curve means high hardenability (alloy steel).

**Using it.** Each Jominy distance corresponds to a cooling rate, and charts link it to positions in real bars. For example, **9.8 mm from the quenched end has the same cooling rate as the centre of a 28 mm oil-quenched bar**. If the Jominy bar is fully martensitic at 9.8 mm, a 28 mm bar can be through-hardened in oil. Similarly, the centre of a 75 mm bar corresponds to 25 mm Jominy distance.

![[Figures/materials_jominy_readoff_2023_24.png]]

> [!example] 2023-24 MQ2(ii)(a): 50 mm oil-quenched bar
> | Position | Jominy distance | Hardness |
> |---|---:|---:|
> | Surface | 7.0 mm | 53.5 HRC |
> | ¾R | 11.5 mm | 48.5 HRC |
> | ½R | 14.0 mm | 45.5 HRC |
> | Centre | 15.5 mm | 43.5 HRC |
> The surface is hardest (fastest cooling, most martensite). The lath microstructure at the surface is **lath martensite**. To make it more ductile, **temper** it.

**Uses of Jominy data:** quality control (composition consistency between batches); choosing steel, section size and quench medium together with CCT curves; avoiding very fast quenches of large parts, which cause residual stress, distortion and cracking.

**Quench media:** water is fastest, but a steam blanket forms and makes cooling uneven. Brine behaves differently. **Oil** is slower but **more controlled** (lower conductivity, no steam), so it gives less distortion and cracking. Forced air is slowest. Thick sections always cool slower in the core. A large component ends up with a martensitic surface and a bainitic or pearlitic core.

See [[Hardenability and Jominy Test]].

## 7. Tempering: making martensite useful

Reheat quenched martensite below the eutectoid temperature (typically 200-650 °C). Carbon diffuses out of the strained BCT lattice into a **fine dispersion of carbides**.

- About 200 °C: slight softening, big reduction in brittleness.
- About 400 °C: tempered martensite.
- About 600 °C: heavily tempered; laths break down and carbides spheroidise, giving the toughest and softest condition.

Strength and hardness fall; **ductility and toughness rise**. Time and temperature are roughly interchangeable (both are diffusion). **Mo** slows softening, and at high Mo content causes **secondary hardening**: fine alloy carbides that do not coarsen, so strength is kept while brittleness is lost.

See [[Tempering]].

## 8. Alloying

**Why alloy?** Hardenability; grain-size control (fine carbides pin grain boundaries); precipitation and solid-solution strengthening; corrosion resistance; phase stabilisation; wear resistance (hard surface carbides); high-temperature use (creep, oxidation); machinability; weldability.

| Role | Elements | Effect |
|---|---|---|
| **Carbide formers** | Cr, Mn, Nb, Mo, Ti, W, V | stable carbides harder than $\mathrm{Fe_3C}$ |
| **Graphitisers** | Ni, Al, Si | destabilise carbides (so balance them with carbide formers) |
| **$\gamma$ stabilisers** (often FCC themselves) | Ni, Mn, Co, Cu | expand the $\gamma$ field; enough gives austenitic at room temperature |
| **$\alpha$ stabilisers** (often BCC) | Cr, Mo, W, Si, V | shrink the $\gamma$ loop; enough gives ferritic at all temperatures |

The effects **interact** and are not additive, so thermodynamic software is used in practice.

**Carbon** is the key element. As C rises, hardness and UTS go up and elongation goes down (UTS dips at very high C because of brittle cementite). Applications move from wire, rivets and chains, through RSJs and structural steel, axles, gears, shafts and rails, high-tensile wire and rope, chisels and shear blades, drills, taps and dies, to knives, saws and razors.

### Improving hardenability

- **Mo, Mn, Cr, Ni, (V, B)** shift the ferrite and pearlite curves **right** (and down), so martensite forms at slower cooling rates.
- **C** helps up to about 0.6 %. Beyond that it retards martensite completion (lowers $M_f$), leaving retained austenite and lower hardness.
- **Higher austenitising temperature** gives bigger $\gamma$ grains, fewer grain-boundary nucleation sites and more hardenability. The Jominy curve extends further.

## 9. Steel classes

| Class | Composition | Microstructure and strengthening | Uses |
|---|---|---|---|
| **HSLA** | 0.05-0.25 % C, ≤ 2 % Mn + Cu, Ni, Nb, V, Cr, Mo, Ti, Zr | Mn ties up S as ductile **MnS** stringers (an atomic layer of S on boundaries is very embrittling); micro-alloy carbides (Nb, V, Ti) **refine the grain size** during thermomechanical processing (the main effect) plus some precipitation | cars, trucks, cranes, bridges, roller coasters. $\sigma_y$ 250-590 MPa, **20-30 % lighter** than an equal-strength C steel |
| **Quenched & tempered medium-C** | 0.3-0.6 % C; plain or Cr-Ni-Mo alloy (4340) | tempered martensite; alloying gives hardenability for thick sections and sets the tempering carbides | crankshafts, bolts, springs, hand tools, **aircraft tubing, landing gear (4340)**, shafts, gears |
| **High-C / tool** | 0.6-1.4 % C + Cr, V, W, Mo | hardened + tempered martensite + very hard alloy carbides | cutting tools, drills, dies: wear and edge retention |
| **Stainless** | > 12 % Cr (+Ni, Mo...) | see below | corrosion and temperature |

Plain-C Q&T steels: $\sigma_y$ 430-585 MPa, UTS 480-980 MPa. Alloy Q&T steels reach $\sigma_y$ of about 1570 MPa (4340) and UTS of about 2380 MPa (4065).

### Surface hardening

**Carburising** (diffuse in C) and **nitriding** (diffuse in N, forming nitrides) cause solid-solution lattice distortion and **make the surface martensite harder**. Induction or flame hardening quenches only the surface. The result is a **hard, wear-resistant case over a tough core**: a crack starting in the brittle case is arrested by the core.

## 10. Stainless steels

Harry Brearley (Sheffield, 1913) found that some of his gun-barrel steel did not rust, and started the cutlery trade.

- **More than 12 % Cr** makes $\mathrm{Cr_2O_3}$ form preferentially. It is coherent, adherent and nearly defect-free, and blocks **both ion and electron** transport ([[Evans Diagram and Passivation]]). Below 12 % you get a defective mixed oxide that may oxidise *faster* than no Cr at all.
- **Ni** stabilises FCC $\gamma$ down to room temperature and below.

![[Figures/materials_passivation_curve.png]]

| Class | Composition | Structure | Properties | Examples and uses |
|---|---|---|---|---|
| **Austenitic** | ≥ 16 % Cr, ≥ 6 % Ni (304 = 18/8); 316 + Mo; 316L low C | FCC | best corrosion; **no DBT, so cryogenic use**; non-magnetic; high work hardening; formable; weldable (L grades); **~70 % of stainless use** | chemical and food plant, cryogenics, satellites (non-magnetic) |
| **Ferritic** | 10.5-18 % Cr only (430, 409); low C | BCC | moderate corrosion; poor formability and weldability; **not heat treatable**; **best SCC resistance** | exhausts, trim |
| **Martensitic** | ~12 % Cr + higher C (410, 416, 420, 440A/B/C); 431 = 16 % Cr + 2 % Ni | BCT after Q&T | hardenable; moderate corrosion; strong | cutlery, turbine blades (steam LP), valves, surgical tools |
| **Duplex** | 2304 (23Cr-4Ni), 2205 (22Cr-5Ni) | $\gamma+\alpha$ | about 2× the strength of annealed austenitic; SCC resistance near ferritic; pitting better than 316; **usable only -50 to 300 °C** | pipelines, offshore |
| **Precipitation hardening** | Cr-Ni + Cu, Al, Ti | martensite or austenite + precipitates | high strength with corrosion resistance | aerospace fittings |

**Compared with mild steel**, stainless has a higher work-hardening rate, ductility, strength and hardness, hot strength, corrosion resistance and cryogenic toughness, and lower magnetic response (austenitic only). It also keeps a corrosion-resistant finished surface after machining.

**Weld decay / sensitisation** is covered in [[SESA2028 M3 - Corrosion, Wear and Surface Engineering|M3]] and [[Sensitisation and Weld Decay]]. In short: $\mathrm{Cr_{23}C_6}$ on grain boundaries leaves the zone next to them below 12 % Cr. Fix it with fast cooling, **low C (L grades)**, or **Ti/Nb stabilisation**.

See [[Stainless Steel Classes]].

## 11. The lecturer's worked ferrous exam question (ML13c)

> [!example] A 0.4 % C plain-carbon component: water quench from 875 °C, temper at 580 °C for 1 h
> **(i) Purpose of the heat treatment [10 marks].**
> At 875 °C the steel is **single-phase austenite** (above $A_3$ for 0.4 % C): FCC, with all the C in solid solution.
> A **water quench** exceeds the critical cooling rate (sketch a CCT diagram with the furnace, air and oil curves crossing the pearlite and bainite fields and the water curve missing the nose). The FCC lattice shears to **BCT martensite** with C trapped: highly dislocated and distorted, **very hard and brittle**. Contrast this with the diffusional $\alpha$ + $\mathrm{Fe_3C}$ you would get by slow cooling.
> **Tempering at 580 °C**: C diffuses out to form a **fine carbide dispersion** (tempered martensite). Strength and hardness fall somewhat; **ductility and toughness rise a lot**.
> **(ii) Cracking found after heat treatment and finish machining [15 marks].**
> (a) **Cause.** Section-size differences mean the surface and thin features cool and contract first while the core is still hot and expanding (martensite forms with a volume increase). The **thermal and transformation strain mismatch** produces **residual stress and distortion**, which peak at **sharp, unradiused grooves** and the **largest changes of diameter**. Quench cracking follows.
> (b) **Inspect** straight after quenching, **before machining** (machining redistributes the residual stresses and can open or hide cracks). Check distortion. Focus on sharp features and section changes.
> (c) **Solutions, with pros and cons:**
> - **Oil quench** plus a **more hardenable alloy steel** (Cr, Mo, Mn, Ni, V shift the nose right). Martensite still forms at a slower, more controlled cooling rate, with less distortion and thermal stress. *But* the alloy costs more and may change other properties such as weldability and machinability.
> - A **higher austenitising temperature** increases hardenability through larger $\gamma$ grains. *But* it costs more energy and coarse grains lower toughness.
> - **Ask whether full martensite is really needed** (is it for wear?). A slower cool gives a ferrite-pearlite core, followed by **carburising or nitriding** for a hard case. *But* that adds a process step and cost.
> - **Add radii** to the grooves if the design allows.

## 12. Exam checklist

- [ ] "Why is quenched steel hard and brittle?" C is trapped in BCT, giving lattice strain plus a high dislocation density. Diffusionless shear. Athermal.
- [ ] "What treatment keeps strength but restores ductility?" **Temper**, and explain the carbide precipitation.
- [ ] Always sketch a **TTT or CCT diagram** with the cooling path and label A, P, B, M, $M_s$, $M_f$ and the nose.
- [ ] Ni means austenite stability, a lower $M_s$ and curves shifted right. Cr means passivation (> 12 %) and a carbide former.
- [ ] Hardenability ≠ hardness.

## Related

- [[SESA2028 Materials Tutorial MT4 - Alloy Design Solutions]] (Q3).
- [[SESA2028 M3 - Corrosion, Wear and Surface Engineering]]: passivation and weld decay.
- [[SESA2028 M8 - High Temperature Materials - Creep, Oxidation and Superalloys]]: stainless at temperature, and how Ni superalloys grew out of austenitic stainless.
- [[Heat Equation]] (MATH2048): why the core of a thick bar cools more slowly (Jominy equivalence is a transient-conduction result).
