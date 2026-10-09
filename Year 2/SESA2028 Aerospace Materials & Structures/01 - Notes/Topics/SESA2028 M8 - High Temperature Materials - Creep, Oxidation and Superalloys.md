---
title: "SESA2028 M8 - High Temperature Materials - Creep, Oxidation and Superalloys"
module: "SESA2028 Aerospace Materials & Structures"
type: topic
stream: "Materials"
order: 8
tags: [sesa2028, materials, creep, larson-miller, oxidation, superalloys, ceramics, coatings, turbine-blade]
status: complete
parent: ["[[SESA2028 Aerospace Materials & Structures Hub]]"]
prerequisites: ["[[SESA2028 M7 - Steels - Phase Transformations, Heat Treatment and Alloying]]", "[[SESA2028 M5 - Metal and Ceramic Matrix Composites and Hybrid Laminates]]"]
next_topics: ["[[SESA2028 Materials Selection and Comparison Tables]]"]
key_concepts: ["[[Creep Curve and Mechanisms]]", "[[Larson-Miller Parameter]]", "[[Creep Miner's Rule]]", "[[Oxidation Rate Laws]]", "[[Gamma Prime Strengthening]]", "[[Thermal Barrier Coatings]]", "[[Single Crystal Casting]]"]
tutorial_sheets: ["[[SESA2028 Materials Tutorial MT5 - High Temperature Materials Solutions]]"]
sources: ["02 - Sources/Materials Lectures/High temperature materials 2025.pdf (lectures 14-16)", "mini lectures ML14a, ML14b, ML14c, ML15a, ML15b, ML16a, ML16b, ML16c, ML16d"]
---

# SESA2028 M8 - High Temperature Materials - Creep, Oxidation and Superalloys

> [!abstract] Summary
> Above about $0.4T_m$ metals **creep**: they deform permanently with time under constant load, through dislocation climb and recovery, diffusion, and grain-boundary sliding, ending in cavitation and rupture. Life is predicted from secondary creep. **Larson-Miller** collapses stress, temperature and time onto one curve, and **Miner's rule** adds up time fractions over a duty cycle. Hot surfaces also **oxidise**, and only coherent $\mathrm{Cr_2O_3}$ and $\mathrm{Al_2O_3}$ scales protect. The answer for turbine blades is a **Ni superalloy** strengthened by coherent $\gamma'$, cast as a **single crystal**, cooled internally and protected by a **TBC**. Numerical creep questions (LMP read-off or creep Miner) appear on every paper; "optimise a Ni blade" and "ceramics in blades" are the recurring essays.

## 1. What a high-temperature material needs

The lecturer's brainstorm:

- **not to melt**: a high $T_m$;
- **high-temperature strength**: the strengthening mechanism must survive at temperature. Al and Ti precipitates re-dissolve or coarsen, which is why they fail here;
- high-temperature **toughness** and **fatigue** resistance;
- **oxidation** resistance: a coherent oxide that stops thickening;
- **creep** resistance;
- **manufacturability**: it is hard to shape something that is designed not to soften or melt;
- cost ("cheap-ish"; NASA pays more).

## 2. Creep

### The creep curve

![[Figures/materials_creep_curve.png]]

Under **constant stress** at $T\gtrsim0.4T_m$ (homologous temperature: 200 °C does nothing to Ni but a great deal to lead):

1. **Instantaneous elastic** strain on loading.
2. **Primary**: the rate decreases. Work hardening beats recovery.
3. **Secondary (steady state)**: constant rate. **Work hardening rate = recovery rate.** This stage dominates life and is the design stage (for example, blade elongation eating into tip clearance).
4. **Tertiary**: the rate accelerates as damage (cavities, necking, microstructural degradation) builds up, ending in rupture.

The curve is sigmoidal, but that has nothing to do with the Paris curve.

**Secondary creep rate (power law + Arrhenius):**

$$
\dot\varepsilon_{ss}=A\,\sigma^n\exp\!\left(-\frac{Q}{RT}\right),
$$

where $Q$ is the **activation energy for self-diffusion**. Since rupture time scales inversely with the rate,

$$
t_r=A'\sigma^{-n}\exp\!\left(+\frac{Q}{RT}\right).
$$

Small changes in $T$ or $\sigma$ give **large** changes in life. At 650 °C, stresses of 1034, 1010 and 984 MPa give very different creep curves, and so do 630, 640 and 650 °C at 1034 MPa.

**Stress relaxation** is the same mechanism under a different boundary condition. At constant strain, the initial stress decays because creep converts elastic strain into plastic strain:

$$
-\frac{d\sigma}{dt}\propto\sigma\;\Rightarrow\;\sigma=\sigma_0e^{-t/\tau},\qquad \ln\frac\sigma{\sigma_0}=-\frac t\tau.
$$

It is faster at higher $T$ and higher initial stress. Bolted flanges lose preload this way.

### Mechanisms

A **deformation-mechanism map** (normalised shear stress $\tau/\mu$ against $T/T_m$, at a fixed grain size, with strain-rate contours from $10^{-10}$ to $1\ \mathrm{s^{-1}}$) shows which mechanism dominates:

| Regime | Mechanism |
|---|---|
| High stress | **Dislocation plasticity** |
| Intermediate-high $T$, high stress | **Dislocation (power-law) creep**: vacancies diffuse to an edge dislocation's extra half-plane, so it **climbs** over obstacles such as precipitates and then glides on. Recovery (annihilation, sub-cells) balances hardening. BCC and HCP slip is thermally activated anyway |
| High $T$, low stress | **Bulk (lattice) diffusion creep** (Nabarro-Herring): atoms diffuse to the grain faces under tension (vacancies go the other way), so grains elongate |
| Lower $T$, higher stress than N-H | **Grain-boundary diffusion** (much faster along disordered boundaries), giving **grain-boundary sliding** under resolved shear. Far more deformation than bulk diffusion |

Grain-boundary sliding opens **cavities at triple points and boundaries**. They grow and coalesce into **intergranular creep rupture** (tertiary creep). Microstructure also degrades: recovery cells, recrystallisation, precipitate coarsening or dissolution.

See [[Creep Curve and Mechanisms]].

### Designing against creep

Remove or slow each mechanism:

1. A **stable microstructure** at the service temperature: precipitates that neither coarsen nor dissolve (stay in the two-phase field), and grain growth pinned by boundary carbides.
2. A **high melting point**, which lowers $T/T_m$.
3. Solutes that **raise the self-diffusion activation energy** (W, Mo, Re in Ni).
4. **Limit grain boundaries**: large grains, **columnar grains aligned with the stress** (no resolved shear across them) from directional solidification, or **no boundaries at all** (single crystals).
5. **Pin dislocations** with precipitates and dispersoids to minimise recovery.

### Is creep ever useful? Superplasticity

With very fine grains (made by high-pressure torsion or equal-channel angular pressing, and prevented from recovering or growing) and slow strain rates, grain-boundary sliding gives elongations of 335-604 %. **Superplastic forming** blow-forms complex shapes in one step. It is combined with diffusion bonding to make hollow Ti fan blades.

## 3. Creep lifing

Tests longer than $10^5$ h (11.4 years) are rare; long-term data come from government and nuclear labs. So **extrapolation** is unavoidable and needs a safety factor.

### Larson-Miller parameter

At fixed stress, take logs of $t_r=A'\exp(Q/RT)$:

$$
\ln t_r=\ln A'+\frac Q{RT}\;\Rightarrow\;T\,(\ln t_r-\ln A')=\frac QR=\text{const}.
$$

In base-10 form:

$$
\boxed{\mathrm{LMP}=T\,(C+\log_{10}t_r)},\qquad T\text{ in K},\ t_r\text{ in h},\ C\approx20.
$$

$t$ can be the rupture time or the time to a set strain (1 %, 2 %). A single master curve of stress (log scale) against LMP collapses all temperatures for one alloy. Typical values are 20-28 ×10³ for Ti, C-steel, CrMo and stainless steels.

**Method:** read the LMP at the service stress, then $\log t_r=\mathrm{LMP}/T-C$.

![[Figures/materials_lmp_rupture_time_map.png]]

| Question | $\sigma$, $T$ | LMP read | $t_r$ |
|---|---|---:|---:|
| Lecture: S-590 iron | 140 MPa, 800 °C | 24.0 | 233 h |
| 2014-15 B1(iv) Ni superalloy | 500 MPa, 700 °C | 26.4 | $1.35\times10^7$ h |
| 2015-16 B3(iv) Alloy 738 | 300 MPa, 785 °C | 25.0 | 4,261 h (**−1 mark without a safety factor**) |
| 2023-24 MQ2(ii)(d) steel bar | 500 MPa, 700 °C / 250 MPa, 600 °C | 22.2 / 24.3 | 655 h / $6.8\times10^7$ h |
| 2020-21 MQ1(b) G92 ($C=35.28$) | see exam note | 31-34.6 | 11 to 190,000 h |

The 2020-21 G92 question compares a standard and an optimised alloy over a five-step flight cycle (LMP + Miner combined): about 11 flight cycles vs about 220. A small shift in the LMP curve changes life by more than an order of magnitude.

![[Figures/materials_g92_rupture_times.png]]

> [!warning] Sensitivity
> $t_r$ is exponential in LMP. A read-off error of ±200 on LMP (about 1 %) changes $t_r$ by a factor of about 1.6 at 700 °C. Always state the read-off uncertainty and apply a safety factor.

See [[Larson-Miller Parameter]].

### Miner's rule for creep

Each (stress, temperature) condition uses up a time fraction of life:

$$
\boxed{\sum_i\frac{t_i}{t_{r,i}}=1.}
$$

The procedure:

1. **Interpolate** the rupture data at each service condition. Rupture life is exponential in $T$ and a power law in $\sigma$, so interpolate **linearly in $\log t_r$** (the lecturer uses a log-log plot). Never interpolate linearly in $t_r$.
2. Add up the fractions used so far.
3. Remaining life at the new condition $=(1-\sum)\,t_{r,new}$.
4. Apply a safety factor and comment on sensitivity.

![[Figures/materials_creep_interpolation_temperature.png]]

![[Figures/materials_creep_stress_powerlaw_fits.png]]

The stress-varying exam data sets are **exact power laws** ($n=6$ for Ti at 600 °C, $n=4$ for Ti at 550 °C, $n=6$ for CM247LC; $R^2=1$). That makes the global fit $t=B\sigma^{-n}$ a legitimate way to extrapolate beyond the data, but say that you are extrapolating.

| Question | Conditions used | Life used | Remaining at final condition |
|---|---|---:|---:|
| 2013-14 B3(iv) SRR99, 400 MPa | 500 h @ 850 °C, 2100 h @ 750 °C | 0.22 | **155 h @ 1000 °C** (lecturer) |
| 2016-17 A1(iv) Ti, 600 °C | 500 h @ 325, 1100 h @ 250 MPa | 0.86 | **1.9 h @ 650 MPa** (extrapolated) |
| 2017-18 A1(v) Ti, 550 °C | 750 h @ 425, 21100 h @ 150 MPa | 0.53 | **68 h @ 825 MPa** (extrapolated) |
| 2021-22 MQ1(d) CM247LC, 750 °C, 1 % strain | 500 h @ 250, 5000 h @ 210 MPa | 0.41 | **70 h @ 475 MPa** |
| 2022-23 MQ2(v) mart. stainless, 450 MPa | 85,000 h @ 625 °C | 0.54 | **39,900 h @ 680 °C** |
| 2024-25 MQ2(c) CMSX-4, 600 MPa | 1500 h @ 1100 °C, 2000 h @ 700 °C | 0.53 | **5,470 h @ 800 °C** |

![[Figures/materials_creep_miner_budgets.png]]

> [!note] 2024-25: "what temperature dependence do you expect, and does the data support it?"
> You would expect Arrhenius behaviour, $t_r\propto\exp(Q/RT)$, with $Q$ close to Ni self-diffusion (about 280 kJ/mol). Fitting $\ln t_r$ against $1/T$ to the CMSX-4 data gives an apparent $Q$ of only **about 47 kJ/mol**: the lives fall far more gently with temperature than Arrhenius predicts. The mechanism probably changes over 600-1100 °C (for example, $\gamma'$ strengthening becomes stronger with temperature at intermediate $T$, then rafting and dissolution take over). Interpolate locally in $\log t_r$ rather than trusting one global Arrhenius fit.

See [[Creep Miner's Rule]].

## 4. Oxidation

### Mechanism

Oxidation is measured by **thermogravimetry** (weight **gain** as oxygen is added; a weight *loss* means the oxide is volatile).

- **Anode** at the metal/oxide interface: $\mathrm{M\to M^{n+}+ne^-}$.
- **Cathode** at the oxide/gas interface: $\mathrm{O_2+4e^-\to2O^{2-}}$.
- The oxide sits **between** the reactants, so it acts as the barrier. Ions and electrons must cross it.
- **Thermodynamics** depends on metal reactivity. **Kinetics** depends on temperature, $\mathrm O_2$ supply and **oxide structure** (defects), and kinetics dominates. The ranking of metals by time to grow 100 µm of oxide at $0.7T_m$ is similar to, but not the same as, the electrochemical series: Au never; Ag, Al, $\mathrm{Si_3N_4}$, SiC very long; Ta, Nb, U, Mo, W very short.

| Oxide defect type | What moves | Where new oxide grows |
|---|---|---|
| **Cation-defective** (cation vacancies) | $\mathrm{M^{n+}}$ diffuses **out** | at the **outer** (oxide/gas) surface; an inert marker ends up buried |
| **Anion-defective** (anion vacancies) | $\mathrm{O^{2-}}$ diffuses **in** | at the **metal/oxide** interface; a marker is pushed outwards |

### Rate laws

![[Figures/materials_oxidation_rate_laws.png]]

| Law | Form | When | Examples |
|---|---|---|---|
| **Linear** | $w=k_Lt$ | porous or cracked scale; reaction-controlled; **worst** | K, Ta |
| **Parabolic** | $w^2=k_pt+C$ | thick, coherent, adherent scale; growth limited by diffusion through a thickening layer | Cu, Fe |
| **Logarithmic** | $w=k_e\log(Ct+A)$ | fast at first, then nearly stops; **very protective** | Fe, Cu, Al at elevated $T$; $\mathrm{Al_2O_3}$, $\mathrm{Cr_2O_3}$ |

Oxides are ceramics: mismatch in thermal expansion and lattice spacing causes **cracking and spallation**, and the fresh metal underneath then oxidises again.

**Why Cr and Al protect.** $\mathrm{Cr_2O_3}$ and $\mathrm{Al_2O_3}$ are coherent, adherent and almost **defect-free**, so neither cations nor anions can get through. A **low** Cr level gives a mixed, defective oxide that can oxidise **faster** than with no Cr at all. More than **12 % Cr** gives a continuous protective scale. See [[Oxidation Rate Laws]].

> [!example] Lecturer's marking notes: why does oxidation matter for a turbine blade, and how do you reduce it? [5 marks]
> - **Significance**: it "eats" load-bearing metal (the section shrinks); the surface roughens (aerodynamic losses); **spalled oxide** is ingested and erodes parts downstream; grain-boundary oxides initiate and accelerate fatigue cracks.
> - **Reduce it**: Cr (and Al) so that a coherent scale forms; a **lower metal temperature** (internal cooling channels, film cooling, TBCs); **protective coatings** (aluminide diffusion coatings, MCrAlY overlays); pre-grow a protective oxide.

## 5. Interactions with fatigue

- **Oxidation-fatigue**: oxide forms along grain boundaries ahead of the crack, cracks, **initiates** fatigue cracks and **accelerates** $da/dN$. It takes time, so the effect is **frequency dependent**: worse at low frequency and with dwell periods. A turbine-disc alloy at 725 °C cracked intergranularly and much faster in air than in vacuum. EBSD shows crack paths depend on grain orientation.
- **Creep-fatigue**: creep damage (grain-boundary sliding, cavitation) adds to fatigue. It is also time-dependent. Creep *can* relax crack-tip stress, but it generally **accelerates** fatigue.

So Paris constants measured at a fixed frequency in lab air may be **unconservative** in service (2024-25 MQ2(d)).

## 6. Alloys for high temperature

### Stainless steels at temperature

- Higher Cr keeps them oxidation resistant, but they are good only to about 500 °C for load-bearing use.
- Long high-temperature exposure causes **sensitisation** ($\mathrm{Cr_{23}C_6}$), so use 316L, or Ti/Nb stabilised grades.
- **Grain-boundary engineering**: fewer boundaries (single crystals), aligned boundaries (DS columnar grains with the load along them), or boundaries pinned and serrated by fine carbides. Boundaries are both creep paths and **oxidation paths**.

### Ni-base superalloys

Ni superalloys **grew out of austenitic stainless steel**: add more and more Ni, remove the Fe.

| Constituent | Role |
|---|---|
| **$\gamma$ matrix** | FCC Ni (no DBT, many slip systems, tough). Solid solution strengthened by **Co, Mo, W** (plus Re, Ta) |
| **Cr** | oxidation and hot-corrosion resistance ($\mathrm{Cr_2O_3}$) |
| **Al** (+Cr) | $\mathrm{Al_2O_3}$ scale; also forms $\gamma'$ |
| **W** (Mo, Re) | raise the melting point and **lower self-diffusion**, so better creep |
| **$\gamma'$ = $\mathrm{Ni_3(Al,Ti)}$** | **the main strengthener**: ordered FCC ($L1_2$), **coherent** cuboids (the "Giant's Causeway" microstructure) at high volume fraction, with fine secondary $\gamma'$ between. Al + Ti content sets the fraction. The solvus is close to $T_m$, and coherence means low interfacial energy, so there is **little drive to coarsen**. Its strength **rises with temperature** (anomalous yield) |
| C, B, Zr, Hf | boundary carbides and borides that pin grain boundaries (in polycrystalline and DS alloys) |

At high temperature, dislocations stay in the softer $\gamma$ channels because the $\gamma'$ is so strong.

**Degradation (rafting):** long exposure to stress and temperature coarsens $\gamma'$ **directionally** into plates. Dislocations then move easily through the continuous $\gamma$ channels, giving an easy crack path.

See [[Gamma Prime Strengthening]].

### Intermetallics

Ordered compounds of dissimilar elements ($\mathrm{Fe_3C}$ is one).

- **Pros**: complex slip, so hard and strong; strong bonds give $T_m$ of 1140-2130 °C; open packing gives low density; good oxidation and corrosion resistance, high-temperature strength, creep resistance and stiffness.
- **Cons**: **brittle**, with poor low-temperature ductility (no stress redistribution, so notch sensitive); poor ductility may have several causes (environment, impurities). Some have **poor thermal conductivity**, giving hot spots that affect neighbouring parts (a system-level cascade) and thermal stresses.

**Uses** are all **controlled** high-temperature applications:

- $\mathrm{Ni_3Al}$: glass-making moulds, hot forging dies, furnace parts, hydroturbines;
- $\mathrm{Fe_3Al}$: exhausts, heating elements, steam-turbine discs;
- **TiAl** (+ $\mathrm{Ti_3Al}$) is the only real aerospace candidate (LP turbine blades). Lamellar microstructure gives toughness and creep resistance; equiaxed gives ductility.

### Ceramics

| Property | Ceramic vs metal |
|---|---|
| Density | lower |
| $T_m$ | much higher |
| $E$ | 2-3× steel, retained at high $T$ |
| Yield stress / yield strain | up to 10× steel (in compression) |
| $K_{Ic}$ | **much lower** |
| Thermal expansion | lower (open packing vs close-packed FCC metals) |

Ionic and covalent bonding in low-symmetry crystals (HCP, monoclinic, orthorhombic) gives **few slip systems**. Dislocations need very high temperatures to move (bond breaking), so there is no plastic flow: very hard and very brittle. They are chemically stable (many are already oxides), are insulators or semiconductors, and are prone to **thermal shock** (hot ovenware plunged into cold water).

**Powder processing:** powder + binder (van der Waals forces, water, polymer) is pressed into a "green" compact and **sintered** at high temperature and pressure; the binder burns off.

1. **Initial stage**: necks form at particle contacts (diffusion reduces surface energy), creating grain boundaries.
2. **Intermediate stage**: grains grow; pores stay continuous along the boundaries.
3. **Final stage**: more grain growth; pores **pinch off** and become closed.

**HIP** achieves full density. **Liquid-phase sintering** leaves a glassy boundary phase (vitrification) with a low melting point, which allows boundary sliding and creep at high $T$.

**Flaws control strength:** porosity (**10 % porosity roughly halves strength**; the distribution matters as much as the volume fraction, and one large pore is worse than many fine ones), inclusions, cracked grains (from anisotropic thermal contraction or multiphase mismatch on cooling), surface damage, and slip-initiated flaws at intermediate $T$.

**To strengthen:** reduce porosity **and** grain size. If pores are smaller than the grain size $d$, grain size controls strength; if pores are larger, porosity controls it. Toughness also depends on the crack path, which is the CMC principle ([[SESA2028 M5 - Metal and Ceramic Matrix Composites and Hybrid Laminates|M5]]). In practice ceramics are used mostly as **coatings**, cutting tools (WC) and chemical or thermal barriers.

## 7. Coatings

| Type | Description |
|---|---|
| **Diffusion coating** | substrate and coating interdiffuse, e.g. Al into Ni gives a NiAl aluminide with a composition gradient |
| **Overlay coating** | a physically separate layer deposited on top (MCrAlY, TBC top coat) |

| Process | Advantages | Disadvantages |
|---|---|---|
| **CVD** (chemical reaction at the surface) | thin, clean functional layers | small batches, defects, high capital cost |
| **PVD** (e.g. sputtering or evaporating a target) | clean; EB-PVD gives a strain-tolerant **columnar** TBC | **poor composition control**: elements with different vapour pressures deposit at different rates (e.g. Cr-enriched vs the target); expensive |
| **Plasma spray / HVOF** (powder partly melted and sprayed as "splats", "like mud thrown at a wall") | any composition, quick, low cost, can be done at low pressure | **line of sight** (needs robot manipulation); **porous, rough finish**, which is a fatigue concern. Pre-roughen by light glass-bead peening for keying, then polish afterwards |

## 8. Case study: the turbine blade

**Service conditions:** the aerofoil tip is hottest (creep, oxidation). The **fir-tree root** has notches (fatigue, fretting) and sits at a moderate temperature. The blade sees centrifugal stress, thermal cycling (LCF, thermo-mechanical fatigue), vibration (HCF), and hot corrosion and erosion.

**History:** Whittle's engine needed a blade to survive **650 °C at about 200 MPa** in creep. Stainless could not, so **Nichrome** (80Ni-20Cr), the ancestor of the superalloys, was developed. Gas temperatures now exceed **1200 °C**, *above the alloy's melting point*, thanks to three developments together:

1. **Cooling**: solid blades, then convection cooling holes, then film-cooling passages. See [[Turbine Entry Temperature and Blade Cooling]] (SESA2023).
2. **Alloys and manufacturing**: equiaxed, then **directionally solidified** (columnar grains parallel to the centrifugal stress, so no transverse boundaries), then **single crystal** (no boundaries at all, so boundary-strengthening elements such as C and B can be removed, the melting point goes up, and a higher solution-treatment temperature gives more $\gamma'$).
3. **Coatings**: TBCs.

Higher gas temperature means higher cycle efficiency ([[SESA2023 W06 - Jet Engine Cycle Analysis - Brayton, Ramjet, Turbojet and Reheat|Brayton cycle]]).

**Investment ("lost wax") casting:**

1. Make a detailed wax pattern around ceramic (silica) cores that will form the cooling channels.
2. Assemble a wax "tree" with runners.
3. Dip repeatedly in ceramic slurry and stucco to build a shell.
4. Melt the wax out in a furnace.
5. Pour the alloy.
6. **Withdraw slowly from the furnace** to get directional solidification. A **"pigtail" helical grain selector** (a "multiple-turn constriction") lets only one grain through, giving a **single crystal**.
7. Leach the cores out chemically.

See [[Single Crystal Casting]].

**The TBC stack** (from substrate outwards):

1. **SX Ni superalloy** substrate, internally air-cooled.
2. **Bond coat**: an intermetallic (aluminide by CVD, or MCrAlY), a metal-ceramic composite that **grades the thermal-expansion mismatch** through thermal cycling.
3. **Thermally grown oxide (TGO)**: $\mathrm{Al_2O_3}$ grown on the bond coat; the real oxidation barrier.
4. **YSZ top coat**, 100-400 µm, by EB-PVD (columnar, strain tolerant) or APS or HVOF. Low conductivity gives a **large temperature drop** across it.

See [[Thermal Barrier Coatings]].

## 9. Exam checklist

- [ ] Creep mechanisms: **name each one, and say at what stress and temperature it dominates**. Then map each design measure onto a mechanism (SX removes boundary sliding; $\gamma'$ pins dislocations; W slows diffusion).
- [ ] LMP: **T in kelvin**, check $C$, and show $\log t_r=\mathrm{LMP}/T-C$. State the read-off uncertainty and a **safety factor**.
- [ ] Creep Miner: interpolate in $\log t_r$, show each fraction, give the remaining time **and** a safety factor, and flag any extrapolation.
- [ ] Oxidation: significance for the part, plus Cr and Al, cooling, coatings.
- [ ] "Ceramics in blades?": high $T_m$, low density and $E$ retained at temperature, **but** low $K_{Ic}$, flaw sensitivity, thermal shock and processing defects. So use them **as TBCs**, or as CMCs (SiC/SiC) where fibres toughen the matrix, and accept inspection and cost penalties.

## Related

- [[SESA2028 Materials Tutorial MT5 - High Temperature Materials Solutions]].
- [[Turbine Entry Temperature and Blade Cooling]], [[SESA2023 W08 - Turbomachinery Principles - Euler Equation and Velocity Triangles]], [[SESA2023 W11 - Solid Propellants and Rocket Nozzle Design]] (C/C and CMC nozzles).
- [[Spinning Disc Stress]]: disc bore vs rim stress (2022-23 MQ1(iii)).
