---
title: "FEEG2005 Exam 2018-19 Solutions"
aliases: ["FEEG2005 Exam 2018-19 Materials Solutions", "FEEG2005 Exam 2018-19 Structures Solutions"]
module: "SESA2028 Aerospace Materials & Structures"
type: exam-solution
year: "2018-19"
streams: ["Materials", "Structures"]
tags: [sesa2028, feeg2005, exam-solutions, materials, structures]
status: complete
parent: ["[[SESA2028 Past Paper Map]]"]
sources: ["03 - Exams & Past Papers/FEEG2005-201819-02-FEEG2005W1.pdf"]
---

# FEEG2005 Exam 2018-19 Solutions

> These are independent worked solutions, not an official mark scheme. Materials and structures are kept together in the order used by the paper.

## Materials

### A1 - Alloys and lightweight rod selection

#### (i) Microstructural features in wrought Al controlled by work and heat treatment [8]

- **Grain size and shape**: working stores dislocations; a recrystallisation anneal nucleates new fine grains. Dispersoids (Mn, Cr, Zr) pin boundaries and control grain growth. Worked grains are elongated (anisotropy). *Effect*: Hall-Petch strengthening plus better toughness.
- **Dislocation density**: cold work (H tempers). *Effect*: work hardening; lower ductility.
- **Precipitates**: solution treat → quench → age. Fine coherent precipitates are sheared; incoherent ones are bypassed (Orowan). Peak aged (T6) is the optimum spacing; over-aged is coarser (T7: better SCC and toughness). *Effect*: the dominant strengthening in 2xxx/6xxx/7xxx.
- **Solute in solution**: solid-solution strengthening.
- **Grain-boundary precipitates and precipitate-free zones** (quench rate and ageing): affect toughness and intergranular corrosion.
- **Texture** and **closure of casting porosity**; broken-up constituent particles: better ductility and fatigue.

#### (ii) Quench + temper plain-C steel [5]

See [[SESA2028 Materials Tutorial MT4 - Alloy Design Solutions]] Q3.

#### (iii) Lightweight rod: 450 kN, $\sigma\le0.5$ UTS, $A<9\times10^{-4}$ m², mass ≤ 2 kg/m [9]

CFRP at $V_f=0.5$, by the rule of mixtures:

$$
\rho_c=0.5(1800)+0.5(1200)=1500\ \mathrm{kg/m^3},\quad \sigma_c=0.5(3800)+0.5(70)=1935\ \text{MPa},\quad E_c=0.5(325)+0.5(3.1)=164\ \text{GPa}.
$$

Required area $A=F/(0.5\,\mathrm{UTS})$; mass per metre $=\rho A$.

| Material | Allowable $\sigma$ (MPa) | $A$ (cm²) | $d$ (mm) | Area < 9 cm²? | kg/m | ≤ 2 kg/m? |
|---|---:|---:|---:|:---:|---:|:---:|
| Ti alloy | 455 | 9.89 | 35.5 | ✗ | 4.37 | ✗ |
| Martensitic tempered steel | 610 | 7.38 | 30.6 | ✓ | 5.75 | ✗ |
| **CFRP (50 %)** | 968 | **4.65** | **24.3** | ✓ | **0.70** | ✓ |

![[Figures/materials_selection_rod_and_sheet.png]]

**Recommendation: CFRP** with fibres aligned along the rod axis. It is the only system that meets **both** the space and weight limits, with about a 3× margin on mass. It is also stiff (164 GPa axially). Caveats: design the end fittings and joints (load transfer into a composite), check compressive or buckling loads if the load reverses, impact damage, and moisture.

#### (iv) Service at 400-750 °C [3]

Extra properties needed: **creep** resistance (LMP data), **oxidation** resistance, strength and stiffness **retained at temperature**, thermal expansion and thermal-fatigue behaviour, and microstructural stability (no over-tempering or precipitate coarsening).

- **CFRP is ruled out**: the epoxy matrix degrades at about 200 °C.
- **Ti alloy**: good to about 500-600 °C (creep and oxidation, alpha case above that), and the lightest metal here. But it failed the area limit at room temperature and strength falls further when hot.
- **Martensitic steel**: $T_m$ 1460 °C, but it **over-tempers** (softens) above its tempering temperature (~550-650 °C) and oxidises without Cr, and it failed the mass limit.

**Recommendation:** for the lower part of the range (≤ 550-600 °C), a **Ti alloy** (near-$\alpha$ for creep), accepting a slightly larger section, or ideally a **Ti-SiC MMC**. For the full range up to 750 °C, none of the three is adequate: a **Ni superalloy** (or a heat-resistant martensitic Cr steel with LMP-verified creep life) would be needed, with the weight penalty accepted.

---

### A2 - Gas turbine: fatigue and creep

#### (i) Miner's rule: LCF + HCF [8]

Identical to MT2 Q2 ([[SESA2028 Materials Tutorial MT2 - Fatigue Lifing Solutions]]):

$$
\frac{550}{1360}+\frac{2.53\times10^6}{7.39\times10^6}=0.404+0.342=\boxed{0.747},\qquad
n=(1-0.747)\times1964=\boxed{498}\ \text{stop-starts at }\Delta\varepsilon=0.18.
$$

Recommend about 250 with SF 2, then inspect. Miner assumes linear, sequence-independent damage.

#### (ii) Blade root crack 3.3 mm, stop-starts twice per day [8]

34-195 MPa; $K_{Ic}=75$; $A=4.5\times10^{-11}$; $m=3.8$; $Q=1.2$.

$$
\Delta\sigma=161\ \text{MPa},\qquad a_c=\frac1\pi\left(\frac{75}{1.2\times195}\right)^2=32.7\ \text{mm}.
$$

With $1-m/2=-0.9$:

$$
N_f=\frac{0.0327^{-0.9}-0.0033^{-0.9}}{(-0.9)(4.5\times10^{-11})(1.2\times161\sqrt\pi)^{3.8}}
=\frac{21.72-171.13}{(-0.9)(4.5\times10^{-11})(4.280\times10^9)}=\frac{-149.4}{-0.1733}=\boxed{862\ \text{stop-starts}}.
$$

That is $862/2=$ **431 days**. **Recommend about 430 stop-starts (~7 months)** with SF 2.

$a_c=32.7$ mm is probably larger than the blade root itself, so in reality failure (net-section yield or a leak of cooling air) would come earlier. The high-temperature environment (oxidation, creep-fatigue with dwell) would also accelerate growth beyond the lab Paris data. Both make this estimate unconservative.

#### (iii) Creep mechanisms; optimising a Ni superalloy blade [5]

Identical to MT5 Q1 ([[SESA2028 Materials Tutorial MT5 - High Temperature Materials Solutions]]). Mechanisms: dislocation creep (climb and recovery), grain-boundary sliding and diffusion with cavitation, bulk diffusion creep. Optimise with $\gamma'$, W and Re (slow diffusion), Cr and Al (oxidation), DS or **single-crystal** casting, heat treatment, cooling and TBC.

#### (iv) Using ceramics in turbine blades [4]

Identical to MT5 Q2. High $T_m$, low density and stiffness retained at temperature are attractive, but low $K_{Ic}$, flaw sensitivity, thermal shock and processing defects make monolithic ceramic blades impractical. So use them as **TBCs** on cooled SX superalloy blades, or as **SiC/SiC CMCs** (fibres toughen the matrix) in shrouds, liners and some LP blades.

## Structures

### B1 - T-section under a 1500 Nm bending moment

Use a $120\times8$ mm flange and a non-overlapping $8\times80$ mm web. Take $y=0$ on the web centreline and $z=0$ on the underside of the flange, with (+z) upward.

#### (i) Centroid

The total area is $1600\ \mathrm{mm^2}$. The centroid is

$$
\boxed{\bar y=12.0\ \mathrm{mm}\ \text{to the right of the web centreline}},
$$

$$
\boxed{\bar z=-13.6\ \mathrm{mm}},
$$

i.e. (21.6) mm below the top surface of the flange.

#### (ii) Second moments

The parallel-axis theorem gives

$$
\boxed{I_z=1.3090\times10^6\ \mathrm{mm^4}},
$$

$$
\boxed{I_y=1.0899\times10^6\ \mathrm{mm^4}},
$$

$$
\boxed{I_{yz}=0.3379\times10^6\ \mathrm{mm^4}}.
$$

#### (iii) Neutral axis and extreme stress

With $M_z=0$,

$$
\sigma_x=\frac{M_y(I_z z-I_{yz}y)}{I_yI_z-I_{yz}^2}.
$$

Therefore the neutral axis is

$$
\boxed{z=\frac{I_{yz}}{I_z}y=0.2581y}.
$$

Evaluating every exterior corner gives the largest magnitude at the lower-right corner of the web:

$$
\boxed{\sigma_{\max}\simeq-96.3\ \mathrm{MPa}}.
$$

The largest tensile value is approximately (+52.4) MPa at the upper-left flange corner. Changing the paper's moment sign reverses tension and compression but not the magnitudes or locations as a pair.

### B2 - Distributed torsion of a closed rectangular box

The mean enclosed area is

$$
A_m=(1000)(250)=250{,}000\ \mathrm{mm^2}.
$$

Let $x$ be measured from the free end. The distributed torque is $m_t=20\ \mathrm{N\,mm/mm}$, so

$$
T(x)=m_tx.
$$

#### (i) Maximum shear stress

Bredt-Batho gives

$$
q(x)=\frac{T(x)}{2A_m}.
$$

At the fixed end, $T_{\max}=20(2500)=50{,}000\ \mathrm{N\,mm}$, hence

$$
q_{\max}=0.100\ \mathrm{N/mm}.
$$

The thinnest walls are the 1.2 mm covers, so

$$
\boxed{\tau_{\max}=\frac{0.100}{1.2}=0.0833\ \mathrm{MPa}}
$$

at the fixed end in the top and bottom walls.

#### (ii) Twist distribution

For one closed cell,

$$
\frac{d\phi}{dx}
=\frac{T(x)}{4A_m^2}
\oint\frac{ds}{Gt}.
$$

Here

$$
\oint\frac{ds}{Gt}
=\frac{2(1000)}{18{,}000(1.2)}
+\frac{2(250)}{26{,}000(2.1)}
=0.10175\ \mathrm{MPa^{-1}}.
$$

With $\phi=0$ at the fixed end it is easiest to use $X$, measured from the fixed end. Then $T(X)=m_t(L-X)$ and

$$
\boxed{
\phi(X)=C m_t\left(LX-\frac{X^2}{2}\right)},\qquad
C=\frac{0.10175}{4A_m^2}.
$$

This is a concave-down parabola: zero at the clamp and maximum at the free end.

#### (iii) Maximum twist

At $X=L=2500$ mm,

$$
\boxed{\phi_{\max}=2.544\times10^{-5}\ \mathrm{rad}}
$$

$$
\boxed{\phi_{\max}=1.46\times10^{-3}\ ^\circ}.
$$

### Linked notes

- [[SESA2028 S1 - Section Properties and Unsymmetrical Bending]]
- [[SESA2028 S4 - Torsion of Thin-Walled Sections]]
