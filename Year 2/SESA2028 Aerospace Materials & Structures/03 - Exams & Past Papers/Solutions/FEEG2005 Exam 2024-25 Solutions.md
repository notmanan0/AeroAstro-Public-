---
title: "FEEG2005 Exam 2024-25 Solutions"
aliases: ["FEEG2005 Exam 2024-25 Materials Solutions", "FEEG2005 Exam 2024-25 Structures Solutions"]
module: "SESA2028 Aerospace Materials & Structures"
type: exam-solution
year: "2024-25"
streams: ["Materials", "Structures"]
tags: [sesa2028, feeg2005, exam-solutions, materials, structures]
status: complete
parent: ["[[SESA2028 Past Paper Map]]"]
sources: ["03 - Exams & Past Papers/FEEG2005-202425-02-FEEG2005.pdf"]
---

# FEEG2005 Exam 2024-25 Solutions

> These are independent worked solutions, not an official mark scheme. Materials and structures are kept together in the order used by the paper.

## Materials

### MQ1 - Mg and Ti alloys, TTT, fan-blade composites

#### (a) Why forge Mg hot; grain-size control [4]

- **Hot working:** Mg is **HCP**. At room temperature only **basal** slip is easy, which gives fewer than the five independent slip systems needed for general plastic deformation. So Mg has poor ductility and cracks when worked cold (it also has a ductile-brittle transition). At higher temperature, **non-basal (prismatic, pyramidal) slip is thermally activated** and twinning and recovery help, so large forging and rolling strains become possible.
- **Grain-size control:** working introduces a high **dislocation density** (stored energy). A subsequent **recrystallisation anneal** (or dynamic recrystallisation during hot working) nucleates new strain-free grains at the deformed sites. **More prior strain means more nuclei and finer grains.** Keep the anneal temperature and time low enough to avoid grain growth. **Zr** additions (e.g. ZK60A) act as grain refiners and pinning particles. Finer grains give a higher $\sigma_y$ (Hall-Petch, strong in HCP Mg) and better ductility.

#### (b) Other features set by heat treatment; two Mg alloys [5]

Heat treatment after working also controls **precipitates** (solution treat and age), **solute in solution**, the **remaining dislocation density** (recovery vs retained work hardening) and **texture**.

| Alloy (lecture table) | Composition | Condition | Mechanism | Strength |
|---|---|---|---|---|
| **AZ31B** | 3Al-1Zn-0.2Mn | extruded (wrought) | Al and Zn in **solid solution**; fine recrystallised grains; some retained work hardening. Mn controls Fe impurities (corrosion) | UTS 262 / YS 200 MPa, 15 % |
| **ZK60A** | 5.5Zn-0.45Zr | **artificially aged** (T5) | Zn precipitates as fine **Mg-Zn precipitates** on ageing; Zr **refines the grain** | **UTS 350 / YS 285 MPa**, 11 %: the highest, used for aircraft forgings |

(HK31A, 3Th-0.6Zr, strain hardened and partially annealed: Th gives stable precipitates and strength up to about 315 °C.) Higher alloy content that can be precipitated means greater age-hardening. Solute Al and Zn raise strength by solid solution. Grain refiners (Zr) add Hall-Petch strengthening.

#### (c) Martensite in Ti vs steel [5]

- **Similarities:** both are **diffusionless, displacive (shear)** transformations on rapid cooling from the high-temperature phase. They are athermal (between $M_s$ and $M_f$), give a metastable, supersaturated, fine lath or acicular structure, and can be tempered or aged afterwards.
- **Ti:** BCC **$\beta$ → HCP $\alpha'$** (or orthorhombic $\alpha''$), supersaturated in **substitutional** $\beta$ stabilisers (V, Mo).
- **Steel:** FCC $\gamma$ → **BCT** martensite supersaturated in **interstitial carbon**. The trapped C distorts the lattice severely, which is the source of the very high hardness and brittleness.
- **Effect on performance:** Ti $\alpha'$ is **only moderately harder** than equilibrium $\alpha$ and keeps reasonable ductility (no interstitial-C distortion). It raises strength in quenched $\alpha+\beta$ alloys and, crucially, **decomposes on ageing into fine $\alpha+\beta$**, giving high strength and a fine microstructure (STA Ti-6Al-4V). Too much untempered $\alpha'$ can reduce ductility and fatigue crack-growth resistance, so it is normally aged.

#### (d) Eutectoid TTT diagram [5]

![[Figures/materials_ttt_critical_cooling_rate.png]]

- **A** = austenite, **P** = pearlite, **B** = bainite, **M** = martensite.
- **Red** = transformation **start** (~1 %); **green** = transformation **finish** (~99 %); **solid orange** = $M_s$ (the dashed lines are $M_{50}$ and $M_{90}$).
- **Nose at about 550 °C:** close to 727 °C the undercooling (driving force for nucleation) is small, so it is slow. At low temperature the driving force is large but **diffusion** is slow. The fastest rate is where the two balance.
- **Critical cooling rate from 700 °C:** you must pass the nose (~540-550 °C at ~1 s) in about 0.8-1 s, so roughly $(700-540)/0.8\approx$ **150-200 °C/s**, and then continue below $M_f$ for full martensite.
- **Prolonged hold at 780 °C:** grain growth gives **coarser austenite grains**, so fewer grain-boundary nucleation sites for pearlite. The curves shift **right**, so a **lower** cooling rate is enough.
- **More Ni:** Ni is an **austenite stabiliser** that slows the diffusional transformation. The curves shift **right** (and $M_s$ is lowered), so a **lower** critical rate is needed, though retained austenite becomes more likely.

#### (e) Fan blade, $E=200$ GPa along the blade [6]

**Assumptions:** continuous fibres aligned **unidirectionally (0°) along the blade length**, because the maximum stress acts along the blade. Isostrain rule of mixtures for $E$, $\rho$ and $\sigma$. Perfect bonding. The epoxy strength is taken as printed (0.07). $V_f=(E_c-E_m)/(E_f-E_m)$.

| | Epoxy/$\mathrm{Al_2O_3}$ | Epoxy/SiC | Ti/$\mathrm{Al_2O_3}$ | Ti/SiC |
|---|---:|---:|---:|---:|
| $E_f$, $E_m$ (GPa) | 370, 3.1 | 220, 3.1 | 370, 114 | 220, 114 |
| **$V_f$** | **0.537** | **0.908** | **0.336** | **0.811** |
| $V_m$ | 0.463 | 0.092 | 0.664 | 0.189 |
| $\rho_f$, $\rho_m$ (g/cm³) | 3.9, 1.05 | 3.21, 1.05 | 3.9, 4.43 | 3.21, 4.43 |
| **$\rho_c$ (g/cm³)** | **2.58** | **3.01** | **4.25** | **3.44** |
| $\sigma_f$, $\sigma_m$ (MPa) | 2000, 0.07 | 1880, 0.07 | 2000, 880 | 1880, 880 |
| **$\sigma_c$ (MPa)** | **1073** | **1707** | **1256** | **1691** |
| **$\sigma_c/\rho_c$ (MPa·cm³/g)** | **416** | 567 | 295 | 492 |

**Choice:**

- Epoxy/SiC has the highest specific strength on paper, but needs **91 % fibre**: impossible to make (practical limit ~60-70 %).
- Ti/SiC (81 %) is also beyond practical MMC fractions.
- Of the **feasible** systems, **epoxy/$\mathrm{Al_2O_3}$** (54 %, 416 MPa·cm³/g, lowest density) beats Ti/$\mathrm{Al_2O_3}$ (34 %, 295).
- So choose **epoxy/$\mathrm{Al_2O_3}$** (fan temperatures are low enough for epoxy), with a Ti leading-edge guard.

**Other factors:** impact and **bird-strike toughness** (Ti matrix is far better); **erosion**; fatigue; off-axis loads (bending and torsion need ±45° plies, which lower $E_L$, so a higher $V_f$ is needed); moisture; manufacturability of thin 3D aerofoils; fibre-matrix reactions (Ti MMCs); cost; repair and inspection (BVID); containment and casing design.

---

### MQ2 - High-temperature materials and disc lifing

#### (a) Two high-temperature applications [4]

1. **Aero-engine HP turbine blades**: creep under centrifugal stress, oxidation and hot corrosion, thermo-mechanical fatigue, strength retained at > 1000 °C, low density, toughness.
2. **Rocket nozzles, throats and exits**: extreme temperature (> 2000 °C) for short burns, **thermal shock**, erosion by hot particle-laden gas, oxidation, low density, and strength retained or increased at temperature. See [[Rocket Nozzle Geometry]].

(Also: IGT blades, exhaust and afterburner structures, re-entry heat shields.)

#### (b) Ti MMC vs C-based CMC for a rocket nozzle [8]

| Criterion | Ti-based MMC (e.g. Ti-6-4 / SiC$_f$) | C-based CMC (C/C or C/SiC) |
|---|---|---|
| **1. Temperature capability and strength at temperature** | strength and creep resistance limited to about **500-600 °C** (matrix softening, $\alpha$ case) | strength kept **above 2000 °C** (C/C strength even rises with temperature) |
| **2. Thermal shock / thermal stress** | metal matrix is ductile; moderate conductivity and expansion; tolerant | very **low expansion**, high conductivity (C/C), and fibre bridging gives excellent thermal-shock resistance |
| **3. Oxidation / environment** | $\mathrm{TiO_2}$ protects to about 550 °C; oxygen embrittlement above that | **oxidises above about 400-500 °C** in oxidising gas; needs SiC or EBC coatings; fine for short burns or inert environments |
| **Also: toughness** | ductile matrix, **damage tolerant**, high $K_{Ic}$ | pseudo-ductile (pull-out) but far lower toughness |
| **4. Manufacturing** | foil-fibre-foil diffusion bonding or powder routes at high temperature; **fibre-matrix reactions**; expensive | CVI / PIP densification over **weeks to months**; porosity; very expensive; machining |

**Recommendation for the nozzle: a C-based CMC** (C/C with an SiC coating, or C/SiC). It is the only option that survives nozzle temperatures. It is light and shock resistant, and burns are short enough to manage oxidation. The Ti MMC suits cooler, load-bearing structure (casings, struts < 550 °C).

#### (c) CMSX-4 at 600 MPa [6]

Data: 600 °C 36,644 h; 700 °C 18,953 h; 900 °C 7,104 h; 1000 °C 4,882 h; 1100 °C 3,544 h.

**Expected temperature dependence:** creep is thermally activated, $t_r\propto\exp(Q/RT)$, with $Q$ close to Ni self-diffusion (about 280 kJ/mol), so the life should fall **exponentially** with temperature.

**Does the data agree?** A fit of $\ln t_r$ against $1/T$ gives an apparent $Q\approx$ **47 kJ/mol**, far below self-diffusion. Life falls only about 10× from 600 to 1100 °C, much **more gently than Arrhenius predicts**. So the data do **not** follow a single Arrhenius law. Possible reasons: $\gamma'$ strength increasing with temperature at intermediate $T$; a change of mechanism across the range; data scatter or orientation effects. Interpolate locally, not with one global fit.

**Miner's rule** (interpolate $\log t_r$ linearly in $T$):

- 1500 h at 1100 °C: $1500/3544=0.423$.
- 2000 h at 700 °C: $2000/18953=0.106$.
- Used: $0.529$; remaining: $0.471$.
- 800 °C (between 700 and 900 °C): $t_r=11{,}600$ h.

$$
t_{remaining}=0.471\times11{,}600=\boxed{5470\ \text{h}}\quad(\text{SF 2: about 2,700 h}).
$$

![[Figures/materials_creep_interpolation_temperature.png]]

#### (d) Turbine disc with a 1.5 mm scratch [7]

30-450 MPa once per flight; $K_{Ic}=95$; $A=2.45\times10^{-12}$; $m=3$; $Q=1.2$ (lab air, 650 °C).

$$
\Delta\sigma=420\ \text{MPa},\qquad a_c=\frac1\pi\left(\frac{95}{1.2\times450}\right)^2=9.85\ \text{mm}.
$$

$$
N_f=\frac{0.009852^{-1/2}-0.0015^{-1/2}}{(-\tfrac12)(2.45\times10^{-12})(1.2\times420\sqrt\pi)^3}
=\frac{10.075-25.820}{(-\tfrac12)(2.45\times10^{-12})(7.129\times10^8)}=\frac{-15.745}{-8.733\times10^{-4}}=\boxed{18{,}030\ \text{flights}}.
$$

**Inspection interval:** with SF 2, re-inspect at **≤ about 9,000 flights**. Better: choose the interval so that a crack just below the NDT detection limit cannot reach $a_c$ before the next inspection. Given the uncertainties below, a more conservative interval (a few thousand flights, aligned with engine shop visits) is sensible, or blend out the scratch now.

**Potential errors:**

- $A$, $m$ were measured in **lab air at constant 650 °C**. The real disc sees a **temperature gradient** (cooler bore, hotter rim), **dwell** at take-off (creep-fatigue and oxidation-assisted growth is frequency dependent), and engine gas chemistry. The real $da/dN$ could be much faster.
- **$K_{Ic}$ varies with temperature**: at the start of a flight the disc is cold but the stress is high.
- A **scratch** is a long, shallow, sharp notch, not a semi-circular crack. $Q$ may exceed 1.2, and the local notch plasticity and residual stress from the tool impact are unknown.
- **Short-crack** behaviour at 1.5 mm (faster growth, microstructure-sensitive); Stage I growth in disc alloys.
- Load spectrum: overspeed, vibration and HCF superimposed; $\sigma_{max}$ and $\sigma_{min}$ uncertainty; NDT sizing error in $a_i$.

## Structures

### SQ1 - L-section: full stress and reserve factors

At the wall clamp,

$$
M_z=FL=50(1200)=60{,}000\ \mathrm{N\,mm}.
$$

With $I_y=I_z=24761.7\ \mathrm{mm^4}$, $I_{yz}=14810.3\ \mathrm{mm^4}$ and $M_y=0$,

$$
\sigma_x=\frac{M_z(I_{yz}z-I_yy)}{I_yI_z-I_{yz}^2}.
$$

Evaluating all vertices gives

$$
\boxed{\sigma_{\max,t}=90.7\ \mathrm{MPa}},\qquad
\boxed{\sigma_{\max,c}=-64.8\ \mathrm{MPa}}.
$$

They occur at the clamp: tension at the upper inner-side corner of the vertical leg and compression at the lower outer re-entrant corner, for the load sense drawn.

The force acts at $z=20-10.74=9.26$ mm from the centroid, so

$$
T=50(9.26)=463\ \mathrm{N\,mm}.
$$

For the open 2 mm L-wall,

$$
J\simeq\frac13\sum bt^3\simeq208\ \mathrm{mm^4},
$$

which gives about (4.45) MPa of peak torsional shear. The bending-shear calculation gives about (0.8) MPa, and the conservative reinforcing-face sum is

$$
\boxed{\tau_{\max}\simeq5.2\ \mathrm{MPa}}.
$$

The component reserve factors are therefore

$$
\boxed{RF_t=150/90.7=1.65},
$$

$$
\boxed{RF_c=150/64.8=2.32},
$$

$$
\boxed{RF_s\simeq70/5.2=13.5}.
$$

The final reserve factor is the minimum:

$$
\boxed{RF_{final}=1.65\quad\text{(tensile bending governs)}.}
$$

### SQ2 - Eccentric fixed-free column

For the $50\times50$ mm square,

$$
A=2500\ \mathrm{mm^2},\qquad
I=\frac{50^4}{12}=520833\ \mathrm{mm^4},\qquad c=25\ \mathrm{mm}.
$$

The secant-form maximum compressive stress for a fixed-free column is

$$
\sigma_{\max}=\frac PA+
\frac{Pec}{I}\sec\left(L\sqrt{\frac{P}{EI}}\right).
$$

#### (a) Maximum eccentricity

For $P=2700$ N and $E=5$ GPa,

$$
P_E=\frac{\pi^2EI}{4L^2}=2.856\ \mathrm{kN}.
$$

Setting $\sigma_{max}=50$ MPa gives

$$
\boxed{e_{\max}=16.4\ \mathrm{mm}}.
$$

The closeness of $P$ to $P_E$ is why a modest eccentricity produces a large moment magnification.

#### (b) Material choice at 5100 N

For material 1, $E=5$ GPa and $P_E=2.856$ kN. Since $5.1>P_E$, the column is elastically unstable even though its strength is 100 MPa.

For birch, $E=10$ GPa and

$$
P_E=5.712\ \mathrm{kN}>5.1\ \mathrm{kN}.
$$

At the worst allowed $e=10$ mm, the secant formula gives approximately (7.2) MPa, below 50 MPa. Therefore

$$
\boxed{\text{choose birch: stiffness and buckling, not material strength, govern.}}
$$

### SQ3 - Thick pressure cylinder

With $p_i=1000$ bar ($=100$ MPa), $r_i=125$ mm and $r_o=250$ mm,

$$
A=\frac{p_ir_i^2}{r_o^2-r_i^2}=33.333\ \mathrm{MPa},
$$

$$
B=\frac{p_ir_i^2r_o^2}{r_o^2-r_i^2}
=2.0833\times10^6\ \mathrm{MPa\,mm^2}.
$$

Hence

$$
\boxed{\sigma_r(r)=33.333-\frac{2.0833\times10^6}{r^2}\ \mathrm{MPa}},
$$

$$
\boxed{\sigma_\theta(r)=33.333+\frac{2.0833\times10^6}{r^2}\ \mathrm{MPa}}.
$$

At the bore,

$$
\sigma_r=-100\ \mathrm{MPa},\qquad
\boxed{\sigma_\theta=166.7\ \mathrm{MPa}},
$$

and at the outside,

$$
\sigma_r=0,\qquad \sigma_\theta=66.7\ \mathrm{MPa}.
$$

The maximum normal stress is the bore hoop stress. The outer material is under-used because hoop stress falls sharply through the wall. More efficient choices include shrink-fitting/compound construction, autofrettage to introduce beneficial residual compression, or geometry/material grading; simply adding more outer radius gives diminishing benefit at the bore.

### Linked notes

- [[SESA2028 S1 - Section Properties and Unsymmetrical Bending]]
- [[SESA2028 S6 - Imperfect Columns, Beam-Columns and Plate Buckling]]
- [[SESA2028 S10 - Thick Cylinders and Shrink Fits]]
