---
title: "SESA2028 Materials Selection and Comparison Tables"
module: "SESA2028 Aerospace Materials & Structures"
type: comparison
stream: "Materials"
tags: [sesa2028, materials, materials-selection, comparison, revision]
status: complete
parent: ["[[SESA2028 Aerospace Materials & Structures Hub]]"]
---

# SESA2028 Materials Selection and Comparison Tables

The lecturer repeatedly says "make your own comparison tables" and "intelligently interrogate data". These are those tables, followed by a map from **component → service conditions → failure modes → material choice**. That is how most MQ essay questions are framed.

## 1. Component → failure mode → material

| Component | Service conditions | Limiting failure modes | Typical material and why | Exam |
|---|---|---|---|---|
| **Fan blade** | centrifugal, bird strike and FOD, HCF flutter, erosion, cold | impact, fatigue, erosion | hollow **Ti-6Al-4V** (SPF/DB) or **CFRP with a Ti leading edge** (lighter, composite casing) | 2020-21 MQ1, 2024-25 MQ1(e) |
| **Compressor blade / disc** | up to ~550-650 °C, centrifugal, LCF | creep, fatigue, oxidation | near-$\alpha$ / $\alpha$ **Ti** (creep stable); future Ti-SiC MMC (bling) | 2017-18 A1, 2022-23 MQ2 |
| **HP turbine blade** | > 1000 °C metal, centrifugal, TMF, oxidation | **creep**, oxidation, TMF | **SX Ni superalloy** ($\gamma'$) + cooling + TBC; CMC in future | 2013-14 B3, 2016-17 A1, 2021-22 MQ1, 2022-23 MQ1 |
| **Turbine disc** | bore high stress ~300-400 °C; rim > 650 °C, fir-tree slots | LCF from bore inclusions, fir-tree fatigue, oxidation-assisted crack growth | **polycrystalline Ni superalloy** (powder metallurgy or cast and wrought), shot-peened slots; damage-tolerant lifing | 2022-23 MQ1, 2024-25 MQ2 |
| **Lower wing skin** | tension, one GAG cycle per flight, humid and salt | fatigue crack growth, corrosion | **2xxx** (2024-T3) damage tolerant, or **GLARE**; CFRP | 2013-14 B1 |
| **Upper wing skin** | compression | buckling, strength | **7xxx-T6/T76** (highest strength); CFRP | |
| **Fuselage** | pressurisation cycles, damage tolerance | fatigue at rivet holes | 2xxx, **GLARE**, CFRP (787/A350) | |
| **Landing gear** | high static + impact loads | fatigue, SCC, toughness | **Q&T 4340 / 300M** tempered martensite; $\beta$-Ti (Ti-10-2-3) | |
| **Pressure vessel** | cyclic pressure, possibly heat | fatigue, fracture (leak before break), creep | **HSLA** or Q&T steel; stainless for corrosive or food use | 2014-15 B1, 2017-18 A2, 2021-22 MQ2 |
| **Offshore weld** | storm cycles, seawater, CP | corrosion fatigue, weld defects, H embrittlement | structural steel; toe dressing, peening, CP | 2015-16 B1 |
| **Hip implant** | ~$10^6$ cycles per year, 37 °C saline, bone contact | fatigue, corrosion, stress shielding, wear | **Ti-6Al-4V** stem + CoCr or ceramic head | 2023-24 MQ1 |
| **Rocket nozzle** | > 2000 °C, short burn, thermal shock, erosion | melting, thermal shock, oxidation | **C/C or C/SiC CMC** | 2024-25 MQ2 |
| **Satellite structure** | launch loads, thermal distortion | stiffness, dimensional stability | **Be**, CFRP, Al honeycomb sandwich | |
| **EV chassis / car body** | cost, volume, crash, stiffness | stiffness, cost | HSLA/AHSS, Al, CFRP (niche) | 2021-22 MQ2 |
| **IGT LP steam blade** | 200-300 °C wet steam, vibration | corrosion fatigue, erosion | **tempered martensitic 12 % Cr stainless** | 2022-23 MQ2 |
| **Ship hull** | cold seawater, impact | DBT (Titanic, Liberty ships), corrosion | fine-grained, low-S/P, higher-Mn steel; coatings + CP | lecture (ML11a) |

## 2. Aluminium alloy series

| Series | Alloying | Heat treatable | Strengthening | Use |
|---|---|---|---|---|
| 1xxx | ≥ 99 % Al | no | work hardening | chemical, food, conductors |
| 2xxx | Cu | **yes** | $\theta'$ ppts | lower wing, fuselage (damage tolerant) |
| 3xxx | Mn | no | SS + work | cans, roofing |
| 4xxx | Si | no | | filler wire |
| 5xxx | Mg | no | SS + work | marine |
| 6xxx | Mg + Si | **yes** | $\mathrm{Mg_2Si}$ ppts | extrusions, automotive |
| 7xxx | Zn + Mg (+Cu) | **yes** | $\eta'$ ppts | upper wing, highest strength |
| 8xxx | Li etc. | **yes** | $\delta'$ ppts | low density, high $E$ |

## 3. Wrought vs cast Al

| | Wrought | Cast |
|---|---|---|
| Route | cast ingot → hot/cold work → recrystallise → solution treat + age | pour into mould (sand, die, investment) → optional heat treatment |
| Microstructure | fine, controlled grains; controlled precipitates; defects closed | coarse dendrites, segregation, **porosity**, oxides, coarse intermetallics |
| Properties | high strength, ductility, toughness, fatigue | lower ductility, toughness, fatigue |
| Strengths | performance, tailorable | near-net complex shapes, cheap at volume |
| Use | primary structure | housings, wheels, pump bodies (non-critical) |

## 4. Titanium alloy classes

| | CP / $\alpha$ | $\alpha+\beta$ | $\beta$ |
|---|---|---|---|
| Stabilisers | Al, O, Sn | Al + V | V, Mo, Fe, Cr |
| Strengthening | solid solution | solid solution + two-phase morphology | solid solution + **$\alpha$ precipitation** |
| Heat treatment | anneal only | anneal or STA; lamellar vs equiaxed | solution treat + quench + **age** |
| Strength | low-moderate | high | **highest** |
| Creep / stability | **best** (stable) | good to ~400 °C | poorer (ppts coarsen) |
| Formability | poor (HCP) | moderate | **good** (BCC, before ageing) |
| Density | 4.51 | 4.43 | ~4.65 |
| Use | chemical plant, engine casings | fan blades, airframe, implants | landing gear, airframe forgings |

## 5. Steel families

| Family | C % | Microstructure | Key property | Use |
|---|---|---|---|---|
| Low-C / mild | < 0.25 | ferrite + pearlite | ductile, weldable, cheap | structures, sheet |
| HSLA | 0.05-0.25 | fine ferrite + micro-alloy carbides | strength via **grain refinement** | cranes, bridges, cars, pipelines |
| Q&T medium-C | 0.3-0.6 | tempered martensite | strength + toughness | shafts, gears, landing gear (4340) |
| High-C / tool | 0.6-1.4 | tempered martensite + alloy carbides | hardness, wear | tools, dies |
| Surface-hardened | case high C/N | martensitic case, tough core | wear + fatigue | gears, cams |

## 6. Stainless classes

| | Austenitic | Ferritic | Martensitic | Duplex |
|---|---|---|---|---|
| Composition | ≥ 16 Cr, ≥ 6 Ni | 10.5-18 Cr | 12-17 Cr + C | 22-23 Cr, 4-5 Ni |
| Structure | FCC | BCC | BCT | FCC + BCC |
| Corrosion | **best** | moderate | moderate | very good (pitting > 316) |
| SCC | susceptible | **best** | moderate | good |
| DBT | **none** (cryogenic) | yes | yes | below -50 °C |
| Hardenable | no (cold work only) | no | **Q&T** | no |
| Weldability | good (L grades) | poor | poor | good |
| Magnetic | no | yes | yes | yes |

## 7. Composite families

| | PMC | MMC | CMC | FML |
|---|---|---|---|---|
| Example | CFRP, GFRP | Al-SiC$_p$, Ti-SiC$_f$ | SiC/SiC, C/C | GLARE |
| Main gain | specific $E$ and $\sigma$ | specific $E$, wear, thermal properties | toughness at high $T$ | fatigue crack retardation |
| Max $T$ | ~150 °C | ~300-800 °C | > 1000 °C | as Al |
| Interface | strong | strong | **weak** | bonded |
| Processing | lay-up, RTM, autoclave | PM, diffusion bonding, casting | CVI, PIP, sintering | laminating + autoclave |
| Weakness | transverse, compression, impact, $T$ | cost, reactions, ductility | brittleness, oxidation, cost | cost, forming |

## 8. Composite manufacturing routes

See [[Composite Manufacturing Routes]] for the full table. Summary: **hand lay-up** (cheap, poor), **pultrusion** (constant section), **filament winding** (bodies of revolution, pressure vessels), **RTM** (closed mould, volume), **compression moulding** (blades), **autoclave prepreg** (best, aerospace), **RFI** (very large parts).

## 9. Coating processes

| Process | Type | Pros | Cons | Use |
|---|---|---|---|---|
| Pack / CVD aluminising | diffusion | uniform, non-line-of-sight | small batches, cost | bond coats, blade aluminide |
| PVD / EB-PVD | overlay | clean; columnar YSZ is strain tolerant | composition control, capital cost | TBC top coat |
| Plasma spray / HVOF | overlay | any composition, fast, cheap | line of sight; porous, rough (fatigue) | wear coats, APS TBC |
| Hot-dip galvanising | metallic | sacrificial protection | thick | structural steel |
| Anodising | conversion | thick protective oxide | brittle, thin | Al, Ti parts |
| Carburising / nitriding | diffusion | hard case, tough core | extra process step | gears, shafts |

## 10. High-temperature material classes

| Class | Useful $T$ | Strengthening | Pros | Cons |
|---|---|---|---|---|
| Austenitic stainless | ≤ ~600 °C | solid solution, carbides | cheap, oxidation resistant | sensitisation, creep weakness |
| Ti alloys | ≤ ~550-600 °C | solid solution, $\alpha$ | light | oxygen embrittlement (alpha case) |
| Ni superalloys | ≤ ~1100 °C (metal) | **$\gamma'$** + solid solution | creep, tough, mature | dense, needs cooling and coatings |
| Intermetallics (TiAl) | ~700-800 °C | ordered structure | light, oxidation resistant | brittle at room $T$ |
| Ceramics | > 1200 °C | covalent / ionic bonds | $T_m$, $E$, light | brittle, flaw sensitive |
| CMCs | > 1200 °C | fibre toughening | hot + light | cost, oxidation, toughness |

## Related

[[SESA2028 Aerospace Materials & Structures Hub]] · [[SESA2028 Formula Sheet]] · [[SESA2028 Past Paper Map]]
