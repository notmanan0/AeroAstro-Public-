---
title: "Precipitation Hardening"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
stream: "Materials"
tags: [sesa2028, materials, strengthening, aluminium, age-hardening]
status: complete
parent: ["[[SESA2028 M6 - Light Alloys - Aluminium, Magnesium, Beryllium and Titanium]]"]
related: ["[[Hall-Petch Relation]]", "[[Gamma Prime Strengthening]]", "[[Titanium Alloy Classes]]"]
---

# Precipitation Hardening

![[Figures/materials_ageing_curve.png]]

## The three steps (Al-Cu example)

1. **Solution treat** at about 550 °C, in the single-phase $\alpha$ field: all the solute (Cu) dissolves.
2. **Quench** (water): no time for diffusion, so the solid solution is **supersaturated**.
3. **Age** at about 120-190 °C, inside the two-phase field. Controlled diffusion precipitates fine, metastable, **coherent** particles (GP zones, then $\theta''$, then $\theta'$). Natural ageing at room temperature gives T4; artificial ageing gives T6.

## How the precipitates block dislocations

- **Coherent, small**: the dislocation must **shear** them (extra interface plus antiphase-boundary energy). Resistance rises as they grow.
- **Incoherent, large**: cannot be cut, so the dislocation **bows out between them (Orowan looping)**. The stress $\propto$ 1/(particle spacing), and it falls as they coarsen.

Peak strength is where the change from shearing to bowing happens. **Particle distribution and spacing matter more than volume fraction.**

## Ageing curve

**Under-aged** (fine, sheared, strength rising), then **peak aged (T6)**, then **over-aged** (coarsening: small particles dissolve to feed large ones, reducing the total interfacial energy; spacing grows and strength falls).

## Alloy systems

- 2xxx: $\theta'$ / $\theta$ ($\mathrm{Al_2Cu}$). Tough, damage tolerant; lower wing and fuselage.
- 7xxx: $\eta'$ / $\eta$ ($\mathrm{MgZn_2}$). Highest strength; upper wing.
- 6xxx: $\mathrm{Mg_2Si}$. Extrusions.
- Al-Li: $\delta'$ ($\mathrm{Al_3Li}$).

The same principle appears in $\beta$-Ti alloys (solution treat, quench, age to fine $\alpha$), PH stainless steels, Ni superalloys ($\gamma'$) and maraging steels.

## Limits

Precipitates coarsen or re-dissolve at high temperature, so aged Al alloys lose strength above about 150-200 °C. Welding destroys the microstructure in the heat-affected zone. **Precipitate-free zones** at grain boundaries lower toughness and promote corrosion.
