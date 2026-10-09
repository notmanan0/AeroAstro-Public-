---
title: "SESA2028 M5 - Metal and Ceramic Matrix Composites and Hybrid Laminates"
module: "SESA2028 Aerospace Materials & Structures"
type: topic
stream: "Materials"
order: 5
tags: [sesa2028, materials, composites, mmc, cmc, glare, fibre-metal-laminates]
status: complete
parent: ["[[SESA2028 Aerospace Materials & Structures Hub]]"]
prerequisites: ["[[SESA2028 M4 - Polymer Matrix Composites]]"]
next_topics: ["[[SESA2028 M6 - Light Alloys - Aluminium, Magnesium, Beryllium and Titanium]]"]
key_concepts: ["[[MMC vs CMC]]", "[[Fibre Metal Laminates]]", "[[Rule of Mixtures]]"]
tutorial_sheets: ["[[SESA2028 Materials Tutorial MT3 - Lightweighting Solutions]]"]
sources: ["02 - Sources/Materials Lectures/Lightweighting 2025.pdf (lecture 7)", "mini lectures ML7a, ML7b"]
---

# SESA2028 M5 - Metal and Ceramic Matrix Composites and Hybrid Laminates

> [!abstract] Summary
> Polymer matrices are easy to process but **limit the service temperature**. A metal matrix (**MMC**) raises the temperature limit and gives better matrix properties; its main purpose is **specific stiffness**. A ceramic matrix (**CMC**) goes hotter still, and there the fibres are there to **toughen** a brittle matrix, not to stiffen it. Both are expensive and hard to make, so they stay niche. **Fibre metal laminates** (GLARE, ARALL) combine Al sheets with composite plies so that intact fibres bridge fatigue cracks in the metal and slow them dramatically.

## 1. Metal matrix composites

### Notation and purpose

MMCs are written matrix-reinforcement, with a subscript for the form: $\mathrm{Al\text{-}SiC_f}$ (fibre), $\mathrm{Al\text{-}SiC_p}$ (particulate).

Why use a metal matrix?

- Higher operating temperature and better intrinsic properties than a resin.
- **Specific stiffness** is the main gain. This is the answer the lecturer wants, not toughness and not really strength.
- A metallurgist's paradox: we usually spend a lot of effort *removing* brittle particles from metals, and an MMC puts them back in.
- Reinforcement also improves **wear resistance** (the majority of use is in ground transport: brake discs, cylinder liners) and gives **tailored thermal properties**. Low thermal expansion and high conductivity matter for electronics thermal management.

### Properties

- In $\mathrm{Al\text{-}TiC_p}$, yield stress rises with TiC content (1 → 20 wt%) and with strain rate, while **elongation falls dramatically**.
- Type, chemistry and volume fraction of the reinforcement control the properties. For example, 41 % C fibre in 6061 Al gives $E_L\approx320$ GPa and UTS $\approx620$ MPa. Boron fibre gives less stiffness but much higher strength.
- **Matrices**: light alloys (Al, Ti, Mg) for moderate temperatures. At very high $T$ you need Co or Co/Ni matrices, and the lightweighting benefit is lost.

### What MMCs could do: disc to blisk to bling

A conventional disc with fir-tree-rooted blades became the **blisk** (integrally bladed disc). The next step is the **bling** (bladed ring), a Ti MMC ring with continuous SiC fibres wound in the hoop direction. The fibres carry the hoop stress, so most of the heavy disc bore can be removed. Successful MMC design could "revolutionise" component design.

### Why they have not taken off (MT3 Q4, 2015-16 B2(iii))

| Problem | Detail |
|---|---|
| **Manufacture** | High melting point, so only high-temperature processes (no hand lay-up). **Solid state**: gas-atomised powders (expensive), press and sinter for particulates, foil-fibre-foil **diffusion bonding** for fibres. **Liquid state**: stir casting or semi-solid casting then hot extrusion, spray deposition (particulates), squeeze casting around fibres. |
| **Fibre-matrix reactions** | High processing temperatures cause reactions at the interface, forming brittle compounds and weakening the fibres |
| **Cost** | High-quality ingredients (continuous fibres, powders) plus slow, specialist processes |
| **Properties** | Ductility and toughness fall; anisotropy and clustering (hot-extruded short-carbon/Al is only partly aligned) |
| **Knowledge** | Joining, repair, inspection and lifing are less established |

**Examples in the lecture:** Al + short HM carbon (hot-extruded powder mix); Cu-W wire (vacuum diffusion bonded, the W necks); maraging-steel wire in Al (plasma-sprayed monolayers); Cu-coated C fibres (pull-out); B fibre (W core) in Al; directionally solidified $\mathrm{Ni_3Al}$ in-situ composites.

**Uses:** ground transportation (the majority, and growing), electronics and thermal management, aerospace (small but growing), industrial and consumer goods. Also extreme environments and space.

## 2. Ceramic matrix composites

### Why ceramics need fibres

Ceramics are stiff, chemically inert, electrical insulators and strong in compression. In tension, **dislocations cannot move**, so there is no plastic relief at flaws. They are notch-sensitive and brittle, "not at all damage tolerant" ([[SESA2028 M8 - High Temperature Materials - Creep, Oxidation and Superalloys|M8]]).

- **Fibres**: C, SiC, $\mathrm{Al_2O_3}$. They need high-quality manufacture and are often deposited on a precursor wire.
- **Matrix**: often the same chemistry, deposited differently (C/C, SiC/SiC, $\mathrm{Al_2O_3/Al_2O_3}$).
- **The role of the fibres is to TOUGHEN the matrix** against the stress-concentrating effect of its small flaws.

### Toughening mechanisms

The sintered matrix is porous and defective, but the fibres **bridge** cracks and add resistance to crack growth through:

- delamination and crack-front splitting;
- **fibre pull-out** (a "forest of fibres" on the fracture surface).

For pull-out to happen the **interface must be relatively weak**. A strong interface lets the crack run straight through the fibres, as in a monolithic ceramic. The downside is that the interfaces become **oxidation paths**, so a CMC's oxidation resistance can be *worse* than a monolithic ceramic's.

### Manufacture (even more expensive than MMCs)

- **Solid state**: blend whiskers or particles with matrix powder, press and sinter. Slurries carry the powders, and the carrier liquid must then be burnt off.
- **Slurry infiltration**: infiltrate a woven or braided fibre preform with slurry, dry, then pressure-sinter.
- **CVI** (chemical vapour infiltration): the matrix is deposited from a vapour inside the preform.
- **PIP** (polymer infiltration and pyrolysis): infiltrate with a pre-ceramic polymer (e.g. polycarbosilane) and pyrolyse at 800-1300 °C. The result is porous, so the cycle is repeated 4-10 times.

### Where they fit

On the lecturer's plot of specific strength against temperature: PMCs have the best specific strength but only at low $T$. Ti MMCs beat Ti alloys. Then come intermetallics, Ni/Co superalloys and Ni aluminides. Monolithic ceramics have poor specific strength (they are brittle); CMCs improve on them. Higher temperature capability means higher engine efficiency.

**Uses:** hot aero-engine sections, CMC **rocket nozzles**, C/C brakes, or ceramics simply as **coatings** (TBCs) on metal. They are high-value only, with long-term potential. See [[Rocket Nozzle Geometry]] (SESA2023).

## 3. MMC vs CMC vs PMC

| | PMC | MMC | CMC |
|---|---|---|---|
| Max service $T$ | ~120-200 °C (matrix $T_g$) | ~300-800 °C (Al, Ti matrix) | > 1000 °C |
| Main gain | specific stiffness **and** strength | **specific stiffness**, wear, thermal properties | **toughness** of a hot, stiff, oxidation-resistant material |
| Matrix toughness | moderate | high (ductile) | very low; fibres must toughen |
| Interface wanted | strong | strong | **weak** (for pull-out) |
| Manufacture | easiest (make shape and material together) | hard: high-$T$ solid or liquid routes; fibre reactions | hardest: sintering, CVI, PIP cycles |
| Cost | moderate to high | high | highest |
| Oxidation | n/a (polymer degrades) | matrix-dependent (Ti forms a protective $\mathrm{TiO_2}$) | interfaces are oxidation paths |

See [[MMC vs CMC]].

## 4. Composite design with metal or ceramic matrices

The same rule-of-mixtures logic as [[SESA2028 M4 - Polymer Matrix Composites|M4]] applies. Here $V_f$ is set by stiffness, strength *and* density.

> [!example] 2022-23 MQ2(iii): Ti MMC compressor blade ($E\ge220$ GPa, $\sigma_y\ge1250$ MPa)
> With a Ti-6Al-4V matrix (120 GPa, 877 MPa, 4.43 g/cm³):
> | Fibre | $V_f(E)$ | $V_f(\sigma_y)$ | $V_f$ | $\rho_c$ (g/cm³) |
> |---|---:|---:|---:|---:|
> | SiC (400, 3900, 3.0) | 0.357 | 0.123 | **0.357** | **3.92** |
> | $\mathrm{Al_2O_3}$ (379, 1380, 3.95) | 0.386 | 0.742 | 0.742 | 4.07 |
> | C (500, 2000, 2.0) | 0.263 | 0.332 | 0.332 | 3.62 |
> | W (407, 2890, 19.3) | 0.348 | 0.185 | 0.348 | 9.61 |
> Carbon gives the lowest density, but C fibres **react with Ti** at processing temperatures (forming TiC) and oxidise at 550 °C. **SiC is the recommendation**: a moderate $V_f$, low density, proven in Ti MMCs (the bling). W is far too dense and $\mathrm{Al_2O_3}$ needs an impractical $V_f$.

> [!example] 2017-18 A1(iii): hoop ring, $E\ge280$ GPa and $\sigma\ge1025$ MPa
> | System | $V_f$ | $\rho_c$ | $E_c/\rho_c$ |
> |---|---:|---:|---:|
> | Ti / $\mathrm{SiC_f}$ | 0.552 | 3.69 | 75.8 |
> | Ti / $\mathrm{Al_2O_3f}$ | 0.889 | 3.82 | 73.2 |
> | $\mathrm{SiC_m}$ / $\mathrm{SiC_f}$ | **0.188** | **3.06** | **91.5** |
> | $\mathrm{SiC_m}$ / $\mathrm{Al_2O_3f}$ | 0.600 | 3.47 | 80.7 |
> SiC/SiC needs the least fibre and is lightest and stiffest per unit mass. **But the ceramic UTS values are compressive**, so the tensile rule of mixtures overstates a ceramic matrix. SiC/SiC also has very low $K_{Ic}$ (2.5-4.6 vs 75 for Ti). For a spinning hoop in tension, **Ti/SiC** is the safer, damage-tolerant choice.

The 2016-17 $\mathrm{Al_2O_3}$-matrix ring and the 2024-25 epoxy/Ti fan-blade table are worked in their exam notes; see [[SESA2028 Past Paper Map]].

## 5. Fibre metal laminates (GLARE, ARALL)

- **GLARE**: GLAss REinforced aluminium. Thin 2024-T3 Al sheets bonded with glass-fibre/epoxy prepreg.
- **ARALL**: ARamid ALuminium Laminate.
- Developed for **damage-tolerant** fuselage skins (GLARE is used in the A380 upper fuselage).

**Mechanism:** a fatigue crack starts and grows in an **Al layer**. When it reaches a fibre ply:

1. the Al/composite interface **delaminates** locally;
2. the **intact fibres bridge** the crack wake and "stitch" it closed.

The effective crack-tip driving force therefore **falls** as the crack gets longer, the opposite of a monolithic metal where $\Delta K\propto\sqrt a$ grows. Growth is severely retarded and can self-arrest. You also keep the metal's impact resistance, fire resistance and ease of inspection. See [[Fibre Metal Laminates]].

## 6. Exam checklist

- [ ] MMC's main purpose is **specific stiffness** (plus wear and thermal properties); CMC fibres are there to **toughen**.
- [ ] Explain the **weak interface** requirement for CMC pull-out, and the oxidation penalty that comes with it.
- [ ] List manufacturing routes with at least one limitation each.
- [ ] Rule-of-mixtures $V_f$: check stiffness and strength, compute density, then comment on reactions, compressive-only data, toughness and cost.
- [ ] For GLARE, explain *why* crack growth slows (bridging plus delamination) rather than just stating that it does.

## Related

- [[SESA2028 M4 - Polymer Matrix Composites]], [[Rule of Mixtures]].
- [[SESA2028 M8 - High Temperature Materials - Creep, Oxidation and Superalloys]]: ceramics, TBCs, turbine-blade materials.
- [[Titanium Alloy Classes]]: choosing the MMC matrix (2022-23 MQ2(ii)).
