---
title: "FEEG2005 Exam 2020-21 Solutions"
aliases: ["FEEG2005 Exam 2020-21 Materials Solutions", "FEEG2005 Exam 2020-21 Structures Solutions"]
module: "SESA2028 Aerospace Materials & Structures"
type: exam-solution
year: "2020-21"
streams: ["Materials", "Structures"]
tags: [sesa2028, feeg2005, exam-solutions, materials, structures]
status: complete
parent: ["[[SESA2028 Past Paper Map]]"]
sources: ["03 - Exams & Past Papers/FEEG2005-202021-02-FEEG2005.pdf"]
---

# FEEG2005 Exam 2020-21 Solutions

> These are independent worked solutions, not an official mark scheme. Materials and structures are kept together in the order used by the paper.

## Materials

### MQ1 - Fan blades and G92 creep

#### (a)(i) Fan-blade service requirements and key properties [4]

**Service:**

- High **centrifugal** tensile stress (large, fast blades; the tip is the fastest-moving part).
- Aerodynamic bending and **vibration** (HCF, flutter) plus one major **LCF** cycle per flight.
- **Bird strike, hail and ice ingestion**: impact, and blade-off containment must be demonstrated.
- **Erosion** of the leading edge by dust, rain, snow and hail.
- Cold, wet air at altitude (−50 °C to ambient).
- Complex 3D wide-chord shape.

**Important properties:** **specific strength** and **specific stiffness** (low mass reduces disc, casing and containment loads, and keeps natural frequencies high); **toughness and impact resistance / damage tolerance**; **fatigue** strength (HCF and LCF); **erosion** resistance; **manufacturability** into thin, complex aerofoils; **inspectability and repairability**.

#### (a)(ii) Ti vs composite fan blade: challenges, benefits, recommendation [6]

| | Hollow Ti-6Al-4V (Rolls-Royce) | CFRP (GE90/GE9X tape lay-up; LEAP 3D-woven RTM) |
|---|---|---|
| Manufacture | three-sheet **diffusion bonding + superplastic forming** into a hollow blade with internal struts; mature, but costly high-temperature tooling | many plies laid up or 3D-woven and resin-injected; **hard to form thin, sharp 3D aerofoils**; slow; needs quality control of voids |
| Mass | heavier; needs a heavy Ti containment casing | **much lighter**; allows a **composite fan case**, so a large engine-level saving |
| Aerodynamics | **thinner sections**, so slightly better efficiency | thicker sections |
| Impact and erosion | tough, ductile; proven bird strike; damage visible | needs a **Ti leading edge** for bird strike and erosion; BVID is hard to see |
| Fatigue | good, but sensitive to FOD notches | excellent fatigue resistance; less maintenance |
| Repair | FOD blended or **rebuilt by additive manufacturing** | repair techniques still developing |

**Recommendation:** for a very large, high-bypass-ratio engine, a **CFRP blade with a titanium leading edge**, plus a composite casing. Mass savings grow with diameter, and it has excellent fatigue behaviour. Keep hollow Ti where thin aerofoils, proven impact behaviour and repairability matter more. See [[Bypass Ratio and Fan Pressure Ratio]].

#### (b)(i) G92 rupture times from the LMP, $\mathrm{LMP}=T(35.28+\log t_r)$ [5]

Read-offs from Fig. MQ1b (±200): standard G92: 250 MPa gives 31,000, 150 MPa gives 34,000. Optimised: 250 MPa gives 32,100, 150 MPa gives 34,600. Then $\log t_r=\mathrm{LMP}/T-35.28$, with $T$ in K.

*Example:* standard, 250 MPa, 525 °C: $\log t_r=31000/798.15-35.28=3.560$, so $t_r=3630$ h.

| $t_r$ (h) | 525 °C | 550 °C | 580 °C | 600 °C |
|---|---:|---:|---:|---:|
| **Standard**, 250 MPa | 3,630 | 240 | 11.4 | |
| **Standard**, 150 MPa | | | 37,350 | 4,565 |
| **Optimised**, 250 MPa | 86,700 | 5,210 | 221 | |
| **Optimised**, 150 MPa | | | 188,600 | 22,210 |

![[Figures/materials_g92_rupture_times.png]]

#### (b)(ii) Flight cycles to failure (creep Miner) [8]

Damage per flight cycle $=\sum t_i/t_{r,i}$:

| Step | $t_i$ | Standard $t_i/t_r$ | Optimised $t_i/t_r$ |
|---|---:|---:|---:|
| 525 °C / 250 MPa | 5 h | 0.00138 | 0.0000577 |
| 600 °C / 150 MPa | 6 h | 0.00131 | 0.000270 |
| 550 °C / 250 MPa | 10 h | **0.0417** | 0.00192 |
| 580 °C / 150 MPa | 5 h | 0.000134 | 0.0000265 |
| 580 °C / 250 MPa | 0.5 h | **0.0439** | 0.00226 |
| **Total per cycle** | | **0.0885** | **0.00453** |

$$
N_{std}=\frac1{0.0885}=\boxed{11.3\ \text{cycles}},\qquad N_{opt}=\frac1{0.00453}=\boxed{221\ \text{cycles}}.
$$

With SF 2: about 5 and about 110 cycles.

**Approach:** LMP to get each $t_r$, then Miner's linear time-fraction sum. The optimised alloy is about 20× better. Nearly all the damage comes from the two short **high-stress (250 MPa) hot steps**, so life is extremely sensitive to those conditions and to the read-off: ±200 on the LMP gives 6.5 to 19.6 cycles for the standard alloy. The standard alloy is clearly unsuitable. Even the optimised one needs a design change (lower stress or cooling).

#### (b)(iii) Other service problems [2]

**Oxidation or steam oxidation** (9 % Cr is marginal above about 600 °C; spallation). **Creep-fatigue** and **thermal fatigue** from the repeated flight cycle (the heating and cooling transients are LCF cycles). Microstructural degradation (tempered martensite coarsening, Laves phase), so the LMP data may not reflect aged material.

---

### MQ2 - Stainless steel, martensite, pipe lifing, rod selection

#### (a) Alloying in stainless steel [1 + 2 + 3]

1. **Stabilise austenite to low temperature**: add $\gamma$ stabilisers, **Ni** (≥ 8 % with 18 % Cr), plus Mn, N, Cu, Co. They expand the $\gamma$ field and depress $M_s$, so the steel stays FCC down to cryogenic temperatures.
2. **Re-passivating surface**: **Cr > 12 %** forms a continuous, coherent, adherent $\mathrm{Cr_2O_3}$ film that blocks ion and electron transport and **re-forms instantly when scratched**, as long as the environment is oxidising (the cathodic line crosses the passive region). **Mo** (316) improves pitting and crevice resistance; Ni helps in reducing acids.
3. **Minimise weld decay**: **low C** (304L/316L, < 0.03 %), so few $\mathrm{Cr_{23}C_6}$ can form; **stabilise with Ti or Nb** (321, 347), stronger carbide formers that leave Cr in solution; solution anneal and **cool fast** through 500-800 °C after welding. See [[Sensitisation and Weld Decay]].

#### (b) What promotes martensite formation [5]

- **Higher austenitising temperature**: dissolves more carbides (more C and alloy in solution) and **coarsens the austenite grains**. Fewer grain-boundary nucleation sites for ferrite and pearlite shift the CCT curves **right**, so martensite forms at slower cooling rates (greater hardenability).
- **Austenite-stabilising elements** (Ni, Mn, C): slow the diffusional $\gamma\to\alpha$ + carbide reactions (curves shift right), so less severe quenches still give martensite. **But** they also lower $M_s$ and $M_f$; too much leaves retained austenite, or the steel becomes fully austenitic (18/8 stainless never forms martensite).
- **Rapid quench** (water, brine): the cooling curve misses the pearlite and bainite nose, so C cannot diffuse out and the FCC lattice must shear to BCT martensite below $M_s$. Cool below $M_f$ for completion.

#### (c) Stainless water pipe: weeks of use [8]

$a_i=1.8$ mm; 30-350 MPa, twice a day; $K_{Ic}=47$; $A=2.45\times10^{-11}$; $m=3$; $Q=1.2$.

$$
\Delta\sigma=320\ \text{MPa},\qquad a_c=\frac1\pi\left(\frac{47}{420}\right)^2=3.99\ \text{mm}.
$$

$$
N_f=\frac{0.003986^{-1/2}-0.0018^{-1/2}}{(-\tfrac12)(2.45\times10^{-11})(680.6)^3}=\frac{15.84-23.57}{-3.862\times10^{-3}}=\boxed{2002\ \text{cycles}}.
$$

That is $2002/2=1001$ days $=\boxed{143\ \text{weeks}}$. **Recommend about 70 weeks** (SF 2) before re-inspection. Note that $a_c$ is only 2.2 mm more than the current crack, and water-side corrosion (pitting, chloride SCC) could accelerate growth.

#### (d) Stiffness-limited rod: 500 mm, 250 kN, $\Delta L\le1$ mm [6]

Strain limit $\varepsilon=1/500=0.002$, so the allowable stress $\sigma=E\varepsilon$. GFRP at 50 %: $E=0.5(72)+0.5(3.1)=37.6$ GPa, UTS $=0.5(3500)+0.5(70)=1785$ MPa, $\rho=1500$.

| Material | $\sigma=E\varepsilon$ (MPa) | UTS / $\sigma$ | $A=F/\sigma$ (cm²) | $d$ (mm) | Rod mass (kg) |
|---|---:|---:|---:|---:|---:|
| Ti alloy | 240 | 3.8 | 10.4 | 36.4 | **2.30** |
| Martensitic steel | 400 | 3.0 | 6.25 | **28.2** | 2.44 |
| GFRP (50 %) | 75 | 24 | 33.3 | 65.1 | 2.50 |

**Stiffness, not strength, governs** (every material is far below its UTS), so mass ∝ $\rho/E$. The three are almost identical in $E/\rho$ (27, 26 and 25 GPa per g/cm³).

**Recommendation:** the **Ti alloy** gives the lightest rod (2.30 kg). The **martensitic steel** gives the most compact rod (28 mm diameter) for only 6 % more mass and much lower cost. GFRP is the worst here: low $E$ makes it bulky (65 mm) and no lighter. Choose Ti if weight is the priority, steel if space or cost is. (Carbon fibre would change the answer, since it has 4× glass's $E$.)

## Structures

### SQ3 - Open crane section

The pallet load is

$$
F=550g=\boxed{5.396\ \mathrm{kN}}.
$$

#### (a) Section properties

Using median lines with $t=6$ mm, put the long horizontal wall at vertical coordinate zero. The two side legs extend to (-100) mm and the middle stem to (+100) mm. The centroid is 10 mm below the horizontal wall. Direct integration of $t\int y^2ds$ and $t\int z^2ds$ gives

$$
\boxed{I_{zz}=5.70\times10^6\ \mathrm{mm^4}},\qquad
\boxed{I_{yy}=16.0\times10^6\ \mathrm{mm^4}},
$$

and symmetry gives

$$
\boxed{I_{yz}=0}.
$$

#### (b) Bending shear flow

For load through the shear centre,

$$
q=\frac{FQ}{I_{zz}},\qquad \tau=\frac qt.
$$

Start from each free edge, where $q=0$, and integrate towards the nearest junction. At the lower end of either side leg, the flow is zero and increases towards the top junction. The running first moment at that junction has magnitude

$$
|Q|=t\left|\int_{-100}^{0}(y+10)dy\right|
=24{,}000\ \mathrm{mm^3}.
$$

The middle stem has

$$
|Q|=t\int_0^{100}(y+10)dy=36{,}000\ \mathrm{mm^3}.
$$

Consequently the largest wall flow occurs at the base of the middle stem:

$$
q_{\max}=\frac{5395.5(36{,}000)}{5.70\times10^6}
=34.08\ \mathrm{N/mm},
$$

$$
\boxed{\tau_{\max,bending}=5.68\ \mathrm{MPa}}.
$$

Flows at the three-way junction must be drawn with directions satisfying nodal equilibrium; simply continuing one scalar $q(s)$ through a branched section is incorrect.

#### (c) Torsional shear

Symmetry places the shear centre on the middle-stem centreline. The real load acts 100 mm away, so

$$
T=F(100)=539{,}550\ \mathrm{N\,mm}.
$$

For this open, constant-thickness section,

$$
J\simeq\frac13\sum bt^3
=\frac13(200+3\times100)(6^3)
=36{,}000\ \mathrm{mm^4}.
$$

The maximum St Venant torsional stress is

$$
\boxed{\tau_{\max,torsion}=\frac{Tt}{J}=89.9\ \mathrm{MPa}}.
$$

#### (d) Better design choices

Move the hoist onto the shear-centre line first; that removes the torque without adding mass. If off-centre pickup is unavoidable, close the section to create a cell, increase the enclosed median area, or add a torsion box/diaphragm near the pickup. Merely thickening the same open section is much less mass-efficient than closing it.

### SQ4 - Bent CFRP control rod

For $D=10$ mm and $d=8$ mm,

$$
A=\frac\pi4(D^2-d^2)=28.274\ \mathrm{mm^2},
$$

$$
I=\frac\pi{64}(D^4-d^4)=289.812\ \mathrm{mm^4}.
$$

#### (a) Compression

The horizontal member carries axial force $F$ and constant bending moment $Fs$. Thus

$$
\sigma_{c,\max}=\frac FA+\frac{Fs(D/2)}I
=\boxed{145.1\ \mathrm{MPa}}.
$$

The transverse displacement of B from the constant moment is

$$
v_B=\frac{FsL^2}{2EI}
=\boxed{24.54\ \mathrm{mm}}.
$$

#### (b) Maximum bent length at safety factor 2

The allowable compression is $600/2=300$ MPa. Hence

$$
s_{\max}=\frac{(300-F/A)I}{F(D/2)}
=\boxed{84.9\ \mathrm{mm}}.
$$

#### (c) Horizontal tensile displacement at A

Using Castigliano with axial energy in the horizontal member and bending energy in both legs,

$$
u_x=\frac{FL}{EA}
+\frac{Fs^2L}{EI}
+\frac{Fs^3}{3EI}.
$$

For the stated data,

$$
\boxed{u_x=5.10\ \mathrm{mm}}.
$$

#### (d) Vertical tensile displacement at A

Only the horizontal member's constant moment contributes to the vertical displacement at the corner/tip:

$$
u_y=\frac{FsL^2}{2EI}
=\boxed{24.54\ \mathrm{mm}},
$$

with the sign set by the tensile-force direction.

### Linked notes

- [[SESA2028 S3 - Shear Flow and Shear Centre]]
- [[SESA2028 S4 - Torsion of Thin-Walled Sections]]
- [[SESA2028 S8 - Virtual Work and Castigliano Theorems]]
