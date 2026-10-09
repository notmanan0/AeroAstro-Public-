---
title: "SESA2028 Materials Tutorial MT5 - High Temperature Materials Solutions"
module: "SESA2028 Aerospace Materials & Structures"
type: tutorial-solution
stream: "Materials"
tags: [sesa2028, materials, tutorial, creep, superalloys, ceramics, turbine-blade]
status: complete
parent: ["[[SESA2028 Aerospace Materials & Structures Hub]]"]
topics: ["[[SESA2028 M8 - High Temperature Materials - Creep, Oxidation and Superalloys]]"]
sources: ["02 - Sources/SESA2028 green coursework book.pdf (MT5, p.29)"]
---

# SESA2028 Materials Tutorial MT5 - High Temperature Materials Solutions

> These are independent worked solutions, not an official mark scheme. Q1 = 2015-16 B3(v) = 2018-19 A2(iii). Q2 = 2018-19 A2(iv).

---

## Q1 - Creep mechanisms and optimising a Ni superalloy blade [6 marks]

### Mechanisms (above about $0.4T_m$)

| Mechanism | Conditions | How strain happens |
|---|---|---|
| **Dislocation creep** | high stress, high $T$ | dislocations glide until blocked; **vacancy diffusion lets edge dislocations climb** past obstacles; recovery balances work hardening (steady state) |
| **Grain-boundary diffusion and sliding** | intermediate $T$ and stress | fast diffusion along disordered boundaries lets grains **slide** under shear; **cavities** form at triple points and boundaries and link up, causing intergranular creep rupture |
| **Bulk (lattice) diffusion creep** | high $T$, low stress | atoms diffuse through the grains from faces in compression to faces in tension, so grains elongate |

Secondary creep rate: $\dot\varepsilon=A\sigma^ne^{-Q/RT}$ ($Q$ ≈ self-diffusion), so life is very sensitive to temperature.

### Optimising a Ni superalloy blade

**Composition:**

- Ni-based **FCC $\gamma$ matrix**: high $T_m$, no DBT, tough, many slip systems.
- **Al + Ti** form a high volume fraction of **$\gamma'$ $\mathrm{Ni_3(Al,Ti)}$**: ordered, **coherent**, low interfacial energy so it hardly coarsens, and stronger as temperature rises. It pins dislocations and blocks climb and recovery.
- **W, Mo, Re (Ta)**: solid-solution strengthen $\gamma$ and **slow diffusion** (raise $Q$), slowing climb and diffusion creep. W also raises $T_m$.
- **Co**: solid solution; lowers the stacking-fault energy.
- **Cr (and Al)**: protective $\mathrm{Cr_2O_3}$ / $\mathrm{Al_2O_3}$ scales against oxidation and hot corrosion.
- For polycrystals only: C, B, Zr, Hf for boundary carbides and borides that pin sliding.

**Manufacture and microstructure:**

- **Investment casting with directional solidification**: columnar grains **parallel to the centrifugal stress**, so no transverse boundaries to slide or cavitate.
- **Single crystal** (spiral grain selector): **no grain boundaries**. The boundary elements that lower the melting point can be removed, allowing a higher solution heat treatment and **more, finer $\gamma'$**. The ⟨001⟩ growth direction gives low modulus along the blade, which helps thermal fatigue.
- **Heat treatment**: solution treat, then age to optimise $\gamma'$ size and fraction.
- **Protection**: internal and film cooling (cast-in cores) plus a **TBC** (bond coat + TGO + YSZ) to lower the metal temperature, and therefore the diffusion rate.

---

## Q2 - Using ceramics in turbine blades [4 marks]

**Why ceramics are attractive:**

- Very high melting points (SiC about 2700 °C, $\mathrm{Al_2O_3}$ about 2070 °C), so higher gas temperatures and efficiency, less cooling air.
- Low density (about 3-4 g/cm³ vs about 8.5 for Ni alloys), so lower centrifugal stress in the blade *and* the disc.
- High stiffness retained at temperature; excellent creep and oxidation or chemical stability (many are already oxides); hard.

**Why monolithic ceramic blades are a problem:**

- Very **low $K_{Ic}$** (about 2-5 vs about 20-100 $\mathrm{MPa\sqrt m}$ for metals). There is no dislocation plasticity to blunt flaws, so they are catastrophically brittle and **flaw sensitive**. Strength is statistical (Weibull) and set by processing porosity (10 % porosity roughly halves strength).
- Poor **thermal shock** resistance and low conductivity, so large thermal stresses.
- Poor impact / foreign-object-damage resistance; hard to machine, join to a metal disc, or inspect.
- Stronger in compression than tension, while blades see tension and bending.

**How to use them:**

1. As **coatings**: a **YSZ thermal barrier** on a cooled single-crystal superalloy blade. You get the temperature capability of the ceramic while the tough metal carries the load. This is the current standard.
2. As **CMCs** (SiC/SiC): fibres bridge cracks and pull out, raising toughness. They are now used in shrouds, combustor liners and some LP-turbine blades. Drawbacks: cost, oxidation of the fibre-matrix interface (needs environmental barrier coatings), and certification.
3. In **low-stress static parts** (vanes, shrouds) before rotating blades.
