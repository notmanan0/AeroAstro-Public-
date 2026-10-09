---
title: "FEEG2005 Exam 2017-18 Solutions"
aliases: ["FEEG2005 Exam 2017-18 Materials Solutions", "FEEG2005 Exam 2017-18 Structures Solutions"]
module: "SESA2028 Aerospace Materials & Structures"
type: exam-solution
year: "2017-18"
streams: ["Materials", "Structures"]
tags: [sesa2028, feeg2005, exam-solutions, materials, structures]
status: complete
parent: ["[[SESA2028 Past Paper Map]]"]
sources: ["03 - Exams & Past Papers/FEEG2005-201718-02-FEEG2005W1.pdf"]
---

# FEEG2005 Exam 2017-18 Solutions

> These are independent worked solutions, not an official mark scheme. Materials and structures are kept together in the order used by the paper.

## Materials

### A1 - CMC compressor blade, composites and Ti creep

#### (i) SiC/SiC vs Ti blade: 3 advantages and 3 disadvantages [6]

| Advantages of SiC/SiC | Disadvantages |
|---|---|
| **~30 % lower density** (3.05-3.1 vs 4.42): lower centrifugal stress in blade *and* disc, lighter engine | **Toughness 2.5-4.6 vs 75 MPa√m**: brittle, flaw sensitive; foreign-object and bird-strike damage is a serious risk for a compressor blade |
| **Much higher $T_m$** (2730 vs 1649 °C) and stiffness retained at temperature: can run hotter stages, no creep or oxidation limit at compressor temperatures | Strengths are **compressive**; tensile strength (which the centrifugal load needs) is much lower and statistical (Weibull) |
| **Higher stiffness** (250-410 vs 120 GPa): high specific stiffness, so higher blade natural frequencies and less flutter | Expensive, slow manufacture (CVI, PIP), porosity, hard to machine and attach (fir-tree root contact stresses), hard to inspect and certify. Also thermal-expansion mismatch with a metal disc, and interface oxidation |

#### (ii) Why is matrix SiC weaker than fibre SiC? [2]

The **matrix** is formed by sintering or infiltration of powder or vapour, so it contains **porosity, larger grains, inclusions and other flaws**. The **fibres** are drawn or deposited under tightly controlled conditions as thin filaments with **far fewer and smaller flaws**. A brittle ceramic's strength (and apparent stiffness) is controlled by its largest flaw (Griffith: $\sigma_f\propto1/\sqrt a$), and a small fibre volume is statistically less likely to contain a critical flaw (Weibull).

#### (iii) $V_f$ for $E\ge280$ GPa **and** $\sigma\ge1025$ MPa [6]

$V_f=(P_{req}-P_m)/(P_f-P_m)$; take the larger value; $\rho_c=V_f\rho_f+(1-V_f)\rho_m$.

| System | $V_f(E)$ | $V_f(\sigma)$ | **$V_f$** | $\rho_c$ | $E_c/\rho_c$ |
|---|---:|---:|---:|---:|---:|
| Ti / $\mathrm{SiC_f}$ | $\frac{160}{290}=0.552$ | $\frac{115}{290}=0.397$ | **0.55** | 3.69 | 75.8 |
| Ti / $\mathrm{Al_2O_3f}$ | $\frac{160}{180}=0.889$ | $\frac{115}{190}=0.605$ | **0.89** ✗ | 3.82 | 73.2 |
| $\mathrm{SiC_m}$ / $\mathrm{SiC_f}$ | $\frac{30}{160}=0.188$ | $\frac{25}{200}=0.125$ | **0.19** | **3.06** | **91.5** |
| $\mathrm{SiC_m}$ / $\mathrm{Al_2O_3f}$ | $\frac{30}{50}=0.60$ | $\frac{25}{100}=0.25$ | **0.60** | 3.47 | 80.7 |

- **On the numbers**, SiC/SiC needs the least fibre and is the lightest and stiffest per unit mass. Ti/$\mathrm{Al_2O_3}$ is impractical (89 %).
- **But** the rule of mixtures here uses **compressive** ceramic strengths, which overstate the tensile capacity of a hoop in **tension**. SiC/SiC also has very low toughness.
- **Recommendation: Ti / $\mathrm{SiC_f}$ MMC** at about 55 %. The ductile, tough Ti matrix makes the ring damage tolerant under hoop tension (the proven "bling" concept). SiC/SiC is only worth it if the operating temperature exceeds Ti's limit (~600 °C). Check fibre-matrix reactions (use coated SiC), density and cost.

#### (iv) Why Ti has good oxidation resistance [3]

Ti forms a thin, **coherent, adherent, stable $\mathrm{TiO_2}$** film spontaneously. It has few defects, so ion transport through it is very slow, and oxidation follows a slow logarithmic or parabolic law. The film **self-heals** if scratched (like stainless steel). Above about 550-600 °C the oxide thickens and oxygen dissolves into the metal (an embrittled "alpha case"), which limits the use temperature.

#### (v) Ti alloy creep at 550 °C: graphical fit and Miner [8]

Data: 200 MPa 41,700 h; 300 MPa 8,230 h; 400 MPa 2,600 h; 500 MPa 1,070 h; 600 MPa 514 h; 700 MPa 278 h.

**Relationship:** plot $\log t_r$ against $\log\sigma$. It is a straight line of slope $-4$ (power law):

$$
t_r=B\sigma^{-n},\qquad n=\frac{\log(41700/278)}{\log(700/200)}=4.00,\qquad B=6.65\times10^{13}\ (\text{h, MPa}).
$$

**Miner:**

- 425 MPa: $t_r=6.65\times10^{13}\times425^{-4}=2044$ h, so $750/2044=0.367$.
- 150 MPa (**extrapolated** below 200): $t_r=131{,}700$ h, so $21100/131700=0.160$.
- Used: 0.527; remaining: 0.473.
- 825 MPa (**extrapolated** above 700): $t_r=144$ h.

$$
t_{remaining}=0.473\times144=\boxed{68\ \text{h}}\quad(\text{SF 2: about 34 h}).
$$

Both ends of the calculation are extrapolated, and 825 MPa is near or above yield at 550 °C, so the uncertainty is large.

**Two ways to improve creep resistance:**

1. **Microstructure and alloy**: use a **near-$\alpha$ alloy** (Al, Sn, Zr, plus Si for fine silicides pinning dislocations), which is thermally stable. Use a **coarse lamellar ($\beta$-processed) structure** (fewer boundaries, more resistance to boundary sliding) instead of fine equiaxed grains.
2. **Reinforce** with continuous $\mathrm{SiC_f}$ (a Ti MMC) aligned with the centrifugal stress. Or **lower the stress and temperature**: cooling, coatings to limit oxygen pick-up, blade redesign.

---

### A2 - Brewery pressure vessel

#### (i) Three service conditions and the properties they need [3]

1. **Cyclic pressurisation** (gas build-up and release): **fatigue** strength, fatigue crack growth resistance, $K_{Ic}$ (damage tolerance), yield strength for wall thickness.
2. **Mildly acidic to alkaline liquids**: **corrosion resistance** (general, pitting, crevice, SCC), cleanability and food safety (no contamination).
3. **5-100 °C thermal cycling**: toughness at the cold end (no DBT near 5 °C), thermal-fatigue resistance, stable properties; **weldability** and formability to fabricate the vessel.

#### (ii) Martensitic plain-C steel vs stainless [6]

| | Martensitic (Q&T) plain-C steel | Stainless (e.g. austenitic 316L) |
|---|---|---|
| Strength | **high** (thinner wall, lower mass) | lower in the annealed condition (thicker wall) |
| Fatigue | good smooth-specimen fatigue, but corrosion pits destroy it | good; passive surface resists pit initiation |
| Corrosion and hygiene | **poor**: rusts across the pH range, contaminates product; needs lining or coating | **excellent** passive film across the pH range; hygienic, easy to clean |
| Toughness at 5 °C | BCC, so a possible DBT; tempered martensite is moderately tough | FCC, **no DBT**, tough |
| Weldability | **poor**: HAZ martensite, hydrogen cracking, needs pre-heat and PWHT | good (with L grades) |
| Cost | cheaper | more expensive |
| Risks | corrosion fatigue | chloride pitting and SCC; sensitisation on welding |

**Recommend 316L austenitic stainless**: food-grade corrosion resistance, toughness and weldability outweigh the cost and strength penalty (standard brewery practice).

#### (iii) Microstructural changes next to the weld [8]

**Martensitic plain-C steel:**

- HAZ heated above $A_3$ re-austenitises. On fast cooling (the cold plate acts as a heat sink) it forms **fresh, untempered martensite**: very hard, brittle, susceptible to **hydrogen-induced cold cracking**. Near the fusion line, **grain coarsening** (lower toughness, though higher hardenability).
- Regions heated between $A_1$ and $A_3$: partial transformation, giving a mixed microstructure.
- Regions heated below $A_1$: **over-tempered** (softened) martensite, a soft band that lowers strength and fatigue resistance.
- **Tensile residual stresses** from contraction.
- *Effect*: hard, brittle zones next to soft zones, crack initiation, lower fatigue and toughness. Needs pre-heat, low-hydrogen consumables and post-weld tempering.

**Austenitic stainless:**

- No martensitic transformation, so no hardening. But the band heated to about **500-800 °C sensitises**: $\mathrm{Cr_{23}C_6}$ on grain boundaries, Cr depletion below 12 %, giving **weld decay** (intergranular attack) in acidic brews.
- Grain growth near the fusion line; some δ-ferrite in the weld metal; high thermal expansion and low conductivity give **distortion and tensile residual stress**, which promotes **SCC** with chlorides.
- *Mitigation*: 316L or Ti/Nb-stabilised grades, low heat input, solution anneal, stress relief, passivation of the weld.

#### (iv) Weld crack 1.35 mm: days of use [8]

$\sigma$ 15-225 MPa once per day; $K_{Ic}=38$; $A=2.2\times10^{-11}$; $m=4.5$; $Q=1.2$.

$$
\Delta\sigma=210\ \text{MPa},\qquad a_c=\frac1\pi\left(\frac{38}{270}\right)^2=6.31\ \text{mm}.
$$

With $1-m/2=-1.25$:

$$
N_f=\frac{0.006305^{-1.25}-0.00135^{-1.25}}{(-1.25)(2.2\times10^{-11})(446.7)^{4.5}}
=\frac{562.8-3864.4}{(-1.25)(2.2\times10^{-11})(8.412\times10^{11})}=\frac{-3301.6}{-23.13}=\boxed{143\ \text{days}}.
$$

**Recommend about 70 days** (SF 2) before repair or re-inspection. In practice, grind out and re-weld now; weld metal toughness is low, and brewery corrosion would accelerate growth.

## Structures

### B1 - Thin-walled Z-section

Let the web median line have length $h$, each flange length (h/2), and every wall have thickness $t$. Put the origin at the centre of the web.

#### (i) Shear centre

The section has 180-degree rotational symmetry. Its centroid and shear centre therefore coincide at the centre of the web:

$$
\boxed{S=C}.
$$

This is point symmetry, not mirror symmetry; the product of inertia is still non-zero.

#### (ii) Section properties

Using $dA=t\,ds$ and neglecting local $t^3$ terms,

$$
\boxed{I_z=\frac{th^3}{3}},\qquad
\boxed{I_y=\frac{th^3}{12}},\qquad
\boxed{I_{yz}=\frac{th^3}{8}}.
$$

The determinant needed in every coupled calculation is

$$
\Delta=I_yI_z-I_{yz}^2=\frac{7t^2h^6}{576}.
$$

#### (iii) Shear flow under a vertical shear $Q_y$

Start at the upper free edge and walk continuously around the wall. Define the running first moments

$$
Q_y^{(A)}(s)=\int_0^s ty\,ds,\qquad
Q_z^{(A)}(s)=\int_0^s tz\,ds.
$$

Then, up to the sign set by the chosen cut-face convention,

$$
\boxed{q(s)=\frac{Q_y}{\Delta}
\left[I_yQ_y^{(A)}(s)-I_{yz}Q_z^{(A)}(s)\right]}.
$$

For $a=h/2$, the running first moments are:

| Wall segment | Coordinate and limits | $Q_y^{(A)}/t$ | $Q_z^{(A)}/t$ |
|---|---|---:|---:|
| top flange | $y=-a, -a\le z\le0$ | (-a(z+a)) | $(z^2-a^2)/2$ |
| web | $z=0, -a\le y\le a$ | $y^2/2-3a^2/2$ | $-a^2/2$ |
| bottom flange | $y=a, 0\le z\le a$ | $-a^2+az$ | $(-a^2+z^2)/2$ |

Substitution gives the complete piecewise distribution. The required checks are:

- $q=0$ at both free edges;
- $q$ is continuous at both corners;
- flange flows are quadratic and the web flow is quadratic;
- the integrated wall forces reproduce $Q_y$, and their torque about $C=S$ is zero.

### B2 - Compound cylinder

The radii are $a=60$ mm, $c=80$ mm and $b=100$ mm. Use

$$
\sigma_r=A-\frac{B}{r^2},\qquad
\sigma_\theta=A+\frac{B}{r^2}.
$$

#### (i) Residual hoop stress from the 8 MPa shrink pressure

| Position | Residual hoop stress |
|---|---:|
| inner bore, $r=60$ mm | (-36.57) MPa |
| inner tube at junction, $r=80^-$ mm | (-28.57) MPa |
| outer tube at junction, $r=80^+$ mm | (+36.44) MPa |
| outside, $r=100$ mm | (+28.44) MPa |

The inner tube is put into hoop compression and the outer tube into hoop tension.

#### (ii) Stress due to the 60 MPa internal pressure alone

Because both cylinders have the same elastic constants and remain in contact, the pressure-only increment is the monobloc field for $a=60$ mm and $b=100$ mm:

$$
A=33.75\ \mathrm{MPa},\qquad B=337{,}500\ \mathrm{MPa\,mm^2}.
$$

Hence

| Radius | Pressure-only hoop stress |
|---|---:|
| (60) mm | (127.50) MPa |
| (80) mm | (86.48) MPa |
| (100) mm | (67.50) MPa |

#### (iii) Resultant field

Superpose the two elastic solutions:

| Position | Resultant hoop stress |
|---|---:|
| bore | (+90.93) MPa |
| junction, inner side | (+57.91) MPa |
| junction, outer side | (+122.93) MPa |
| outside | (+95.94) MPa |

The shrink fit has reduced the dangerous tensile hoop stress at the bore, but the price is a stress jump and a new maximum just outside the junction.

### Linked notes

- [[SESA2028 S1 - Section Properties and Unsymmetrical Bending]]
- [[SESA2028 S3 - Shear Flow and Shear Centre]]
- [[SESA2028 S10 - Thick Cylinders and Shrink Fits]]
