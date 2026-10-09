---
title: "SESA2028 Materials Tutorial MT3 - Lightweighting Solutions"
module: "SESA2028 Aerospace Materials & Structures"
type: tutorial-solution
stream: "Materials"
tags: [sesa2028, materials, tutorial, composites, lightweighting, rule-of-mixtures]
status: complete
parent: ["[[SESA2028 Aerospace Materials & Structures Hub]]"]
topics: ["[[SESA2028 M4 - Polymer Matrix Composites]]", "[[SESA2028 M5 - Metal and Ceramic Matrix Composites and Hybrid Laminates]]"]
sources: ["02 - Sources/SESA2028 green coursework book.pdf (MT3, p.28)"]
---

# SESA2028 Materials Tutorial MT3 - Lightweighting Solutions

> These are independent worked solutions, not an official mark scheme. Q5's table is the same as 2014-15 Table QB2.

---

## Q1 - What are specific properties and why do they matter? [3 marks]

Specific properties are properties **divided by density**: specific stiffness $E/\rho$ and specific strength $\sigma/\rho$.

- For anything that moves (aircraft, cars, rotating parts) mass costs fuel, payload, inertia and centrifugal load. What matters is the stiffness or strength you get **per kilogram**, not per unit volume.
- The right index depends on loading ([[Specific Stiffness and Strength]]): $E/\rho$ for a tie, $E^{1/2}/\rho$ for a strut or beam, $E^{1/3}/\rho$ for a panel.
- Example: steel, Al and Ti all have $E/\rho\approx25$-27 GPa·cm³/g, but CFRP reaches about 130 along the fibres. That is why composites dominate lightweight structures.

---

## Q2 - Which fibres give $E_L\ge55$ GPa and $\sigma_L\ge1.2$ GPa at $V_f=0.40$? [7 marks]

Aligned, continuous fibres loaded along their length, so use the **isostrain rule of mixtures** ([[Rule of Mixtures]]):

$$
E_L=V_fE_f+V_mE_m,\qquad \sigma_L\approx V_f\sigma_f+V_m\sigma_m,\qquad V_f=0.4,\ V_m=0.6.
$$

Epoxy contribution: $0.6\times3.1=1.86$ GPa to stiffness and $0.6\times0.07=0.042$ GPa to strength.

| Fibre | $E_L$ (GPa) | Meets 55? | $\sigma_L$ (GPa) | Meets 1.2? | Verdict |
|---|---:|:---:|---:|:---:|---|
| Aramid (124, 3.5) | $49.6+1.86=\mathbf{51.5}$ | ✗ | $1.40+0.042=\mathbf{1.44}$ | ✓ | fails stiffness |
| Glass (72, 3.5) | $28.8+1.86=\mathbf{30.7}$ | ✗ | $\mathbf{1.44}$ | ✓ | fails stiffness badly |
| Carbon (325, 3.8) | $130+1.86=\mathbf{131.9}$ | ✓ | $1.52+0.042=\mathbf{1.56}$ | ✓ | **only candidate** |

**Only carbon/epoxy works.** All three fibres are strong enough; stiffness is the discriminating requirement. Aramid is close (51.5 vs 55 GPa) and would need $V_f\ge(55-3.1)/(124-3.1)=0.43$, above the 40 % cap. Glass would need $V_f=0.75$, which is impractical.

---

## Q3 - A cheaper alternative to carbon/epoxy? [4 marks]

- **Hybrid carbon/glass (or carbon/aramid) lay-up**: put carbon only where stiffness is needed, e.g. in the outer plies or the load direction, and use cheap glass elsewhere. The hybrid rule of mixtures ($E=V_{C}E_C+V_GE_G+V_mE_m$) lets you find the minimum carbon fraction that still gives 55 GPa.
- **A cheaper grade of carbon fibre** (standard-modulus, large-tow) instead of high-modulus aerospace grade.
- **A cheaper manufacturing route**: RTM, pultrusion or filament winding (for suitable shapes) instead of prepreg and autoclave. Reduce waste, automate.
- **A cheaper matrix** (vinyl ester or polyester instead of epoxy), accepting lower properties, more shrinkage and more moisture uptake.
- **Optimise the design**: use geometry (sandwich panels, thicker sections) so that less high-performance material is needed.

---

## Q4 - Why have MMCs not reached their potential? Give examples [7 marks]

**Why they attract interest:** higher service temperature than polymer composites; better matrix properties (toughness, shear, transverse strength); big gains in **specific stiffness**; wear resistance; tailored thermal expansion and conductivity. There are also radical design possibilities, such as the Ti-SiC bladed ring (bling) that removes the disc bore.

**Why uptake is limited:**

- **Manufacture**: the matrix melts at high temperature, so no hand lay-up is possible. Solid-state routes (powder metallurgy, foil-fibre-foil diffusion bonding) and liquid routes (stir casting, squeeze casting, spray deposition) are slow, specialised and hard to scale.
- **Fibre-matrix reactions** at processing temperatures form brittle interfacial compounds and weaken the fibres.
- **Cost**: continuous high-quality fibres and fine powders are expensive, on top of the difficult processes.
- **Properties**: ductility and toughness drop sharply (e.g. $\mathrm{Al\text{-}TiC_p}$: yield rises but elongation collapses); anisotropy and clustering; property scatter.
- **Knowledge and certification**: joining, machining (abrasive reinforcement wears tools), repair, NDT and lifing are less mature. A conservative industry needs a lot of data.
- **Competition** from improved monolithic alloys (Al-Li) and polymer composites.

**Examples:** $\mathrm{Al\text{-}SiC_p}$ brake discs and drums, and cylinder liners (automotive: wear); Al-SiC electronic packaging and heat sinks (low expansion, high conductivity); B-fibre/Al tubes (Space Shuttle frame); Ti-SiC$_f$ blings and actuator rods (aero-engines, R&D); C-fibre/6061 Al (stiff space structures); Cu-W electrical contacts.

---

## Q5 - Best material for a tension strut, and would compression change it? [5 marks]

| | UTS (MPa) | $E$ (GPa) | $\rho$ (g/cm³) | $\sigma/\rho$ | $E/\rho$ | $E^{1/2}/\rho$ |
|---|---:|---:|---:|---:|---:|---:|
| CFRP | 1500 | 220 | 1.7 | **882** | **129** | **8.72** |
| GFRP | 990 | 45 | 2.2 | 450 | 20.5 | 3.05 |
| Steel | 1000 | 207 | 7.8 | 128 | 26.5 | 1.84 |
| Al alloy | 550 | 71 | 2.8 | 196 | 25.4 | 3.01 |
| Ti alloy | 1100 | 120 | 4.5 | 244 | 26.7 | 2.43 |

(The printed Green Book table is misaligned: the densities are 1.7, 2.2, 7.8, 2.8 and 4.5 g/cm³, and the Al and Ti rows are 550/71 and 1100/120.)

**Tension strut:** the lightest tie for a given strength maximises $\sigma/\rho$, and for a given stiffness $E/\rho$. **CFRP wins on both by a wide margin**, with fibres aligned along the strut.

**Compression strut:** slender struts fail by **Euler buckling**, $P_{cr}=\pi^2EI/L^2$. For a solid section of area $A$, $I\propto A^2$, so the mass needed scales as $\rho/E^{1/2}$ and the index is $E^{1/2}/\rho$ ([[Euler Buckling]]). **CFRP still wins numerically** (8.7 vs 3.0 for Al).

**But** the choice changes in practice if the strut is short (crushing-controlled) or must survive impact, because:

- the **compressive** strength of CFRP is much lower than its tensile strength (fibre microbuckling and kinking, matrix-dominated), and it is vulnerable to impact damage and delamination;
- there is no ductility or warning;
- joining the ends is difficult.

So for compression **Al alloy is the next best choice** ($E^{1/2}/\rho=3.01$, about the same as GFRP but isotropic, tough, cheap and easy to join). Use **Ti** if temperature, space or strength-in-crushing matters. If CFRP is kept, use a tube with ±45° plies for shear and buckling resistance.
