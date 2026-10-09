---
title: "SESA2028 Materials Tutorial MT4 - Alloy Design Solutions"
module: "SESA2028 Aerospace Materials & Structures"
type: tutorial-solution
stream: "Materials"
tags: [sesa2028, materials, tutorial, aluminium, titanium, steels, heat-treatment]
status: complete
parent: ["[[SESA2028 Aerospace Materials & Structures Hub]]"]
topics: ["[[SESA2028 M6 - Light Alloys - Aluminium, Magnesium, Beryllium and Titanium]]", "[[SESA2028 M7 - Steels - Phase Transformations, Heat Treatment and Alloying]]"]
sources: ["02 - Sources/SESA2028 green coursework book.pdf (MT4, p.28)"]
---

# SESA2028 Materials Tutorial MT4 - Alloy Design Solutions

> These are independent worked solutions, not an official mark scheme. Q2 is 2014-15 B2(ii). Q3 is repeated in 2013-14 B3(i), 2015-16 B3(ii), 2016-17 A2(i) and 2018-19 A1(ii).

---

## Q1 - Raising the specific strength and specific stiffness of Al [8 marks]

Density hardly changes with ordinary alloying, so raising **specific strength** means raising **yield strength**: making it harder for dislocations to move. Each mechanism and how processing controls it:

| Mechanism | Obstacle | How alloying or processing controls it |
|---|---|---|
| **Grain refinement** (Hall-Petch, $\sigma_y=\sigma_0+kd^{-1/2}$) | grain boundaries: pile-ups, barriers | working followed by recrystallisation anneal; grain refiners (Ti, B) in casting; dispersoids (Mn, Cr, Zr) that pin boundaries |
| **Solid solution** | solute strain fields pin dislocations | Cu, Mg, Zn, Si dissolved in $\alpha$-Al (5xxx relies on Mg) |
| **Work hardening** | dislocation tangles | cold rolling or drawing (H tempers) of non-heat-treatable 1xxx/3xxx/5xxx |
| **Precipitation hardening** | coherent precipitates (sheared) or incoherent ones (Orowan bowing) | **solution treat** (~550 °C, single phase) → **quench** (supersaturated) → **age** (~120-190 °C) to peak (T6) in 2xxx/6xxx/7xxx. The alloy chosen sets the precipitates: $\theta'$ in Al-Cu, $\eta'$ in Al-Zn-Mg |

**Thermomechanical processing** (wrought route) combines these: it controls grain size and shape, precipitate distribution, dislocation density and texture, and closes casting porosity. That is why wrought alloys outperform cast ones. 7xxx-T6 gives the highest specific strength (about 570 MPa / 2.8 g/cm³).

**Specific stiffness** ($E/\rho$) is **not** changed by heat treatment or precipitation, because $E$ depends on bonding and barely moves. To raise it:

- **Add lithium** (8xxx Al-Li): each 1 wt% Li **lowers density by about 3 % and raises $E$ by about 6 %**.
- **Reinforce it**: make an MMC with SiC or $\mathrm{Al_2O_3}$ particles or fibres (e.g. Al-SiC$_p$, B/Al). $E$ follows the rule of mixtures ([[SESA2028 M5 - Metal and Ceramic Matrix Composites and Hybrid Laminates|M5]]).
- (Or use geometry: sandwich construction and stiffened panels.)

---

## Q2 - The three Ti alloy classes; control by composition and heat treatment; best fatigue resistance [9 marks]

Ti is **$\alpha$ (HCP)** at low temperature and **$\beta$ (BCC)** above the transus. Composition moves the transus:

- **$\alpha$ stabilisers**: Al, O, N, C (Ga, Ge).
- **$\beta$ stabilisers**: V, Mo, Nb, Ta, Fe, Cr, Mn (Co, Ni, Cu, Si).

| Class | Composition | Phases | Strengthening | Heat treatment |
|---|---|---|---|---|
| **$\alpha$ / near-$\alpha$** (CP Ti, Ti-5Al-2.5Sn) | $\alpha$ stabilisers (Al, Sn, O) | single-phase $\alpha$ (+ a little $\beta$ in near-$\alpha$) | **solid solution** (substitutional Al, Sn; interstitial O) + grain size | not heat-treatable for strength; anneal or recrystallise to control grain size |
| **$\alpha+\beta$** (Ti-6Al-4V) | both types | $\alpha$ + $\beta$ | solid solution + phase boundaries + $\alpha$ morphology; can be solution treated and aged | slow cool from $\beta$ gives **lamellar basket-weave**; anneal in $\alpha+\beta$ gives **equiaxed $\alpha$** + transformed $\beta$; fast cool gives $\alpha'$ martensite, later aged |
| **$\beta$ / metastable $\beta$** (Ti-10V-2Fe-3Al) | enough $\beta$ stabiliser to keep $\beta$ on quenching | $\beta$ (+ precipitated $\alpha$) | solid solution + **precipitation** of fine $\alpha$ | **solution treat in $\beta$ → quench → age**, like Al; formable (BCC) before ageing |

**Properties trade-off:**

- $\alpha$: thermally stable (no precipitates to coarsen), so the **best creep resistance** and weldable, but lower strength and poor formability (HCP).
- $\beta$: **highest strength**, formable, but denser (7-10 %), prone to segregation, and unstable at high temperature.
- $\alpha+\beta$: the balance, and the most widely used.

**Highest fatigue resistance: $\alpha+\beta$ alloys (Ti-6Al-4V)**, because the microstructure can be tuned to resist both stages:

- **fine equiaxed $\alpha$** (anneal in $\alpha+\beta$): small grains restrict slip-band length, so **initiation** is delayed and HCF strength is high;
- **lamellar / basket-weave $\alpha$** (slow cool from $\beta$): colonies deflect and branch the crack, giving a tortuous path that resists **propagation** (damage tolerance).

A bimodal structure gives both. Fatigue-critical parts like fan blades and discs therefore use $\alpha+\beta$ or near-$\alpha$ alloys.

---

## Q3 - Quenching plain-carbon steel: why hard and brittle, and how to fix it [5 marks]

**1. Austenitise** (e.g. 875 °C for 0.4 % C): single-phase **austenite** (FCC $\gamma$), with all the carbon in interstitial solid solution (FCC dissolves a lot of C).

**2. Fast quench** (water, faster than the critical cooling rate; sketch a TTT/CCT with the cooling curve missing the pearlite nose):

- there is no time for C to diffuse out, so the diffusional products (ferrite + cementite, pearlite, bainite) are **suppressed**;
- below $M_s$ the FCC lattice **shears** (diffusionless, displacive, athermal) into **martensite**: a **BCT** cell with carbon **trapped**, which distorts the lattice;
- the transformation strains create a **very high dislocation density** and fine laths, so slip is blocked;
- result: **very hard and strong, but brittle**, with residual stresses (quench cracks are possible).

**3. Temper** (reheat to about 400-650 °C, e.g. 580 °C for 1 h, then cool):

- carbon diffuses out of the supersaturated BCT lattice and precipitates as a **fine dispersion of carbides** ($\mathrm{Fe_3C}$); the matrix relaxes towards BCC ferrite; dislocations recover; residual stresses relax;
- **tempered martensite**: hardness and strength fall **slightly**, while ductility and toughness **rise substantially**.

This quench-and-temper route mostly keeps the strength while restoring ductility. The tempering temperature and time set the balance (higher means tougher and softer).

See [[Martensite]], [[Tempering]], [[TTT and CCT Diagrams]].
