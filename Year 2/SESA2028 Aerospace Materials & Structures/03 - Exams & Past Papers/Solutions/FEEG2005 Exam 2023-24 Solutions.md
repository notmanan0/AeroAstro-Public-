---
title: "FEEG2005 Exam 2023-24 Solutions"
aliases: ["FEEG2005 Exam 2023-24 Materials Solutions", "FEEG2005 Exam 2023-24 Structures Solutions"]
module: "SESA2028 Aerospace Materials & Structures"
type: exam-solution
year: "2023-24"
streams: ["Materials", "Structures"]
tags: [sesa2028, feeg2005, exam-solutions, materials, structures]
status: complete
parent: ["[[SESA2028 Past Paper Map]]"]
sources: ["03 - Exams & Past Papers/FEEG2005-202324-02-FEEG2005.pdf"]
---

# FEEG2005 Exam 2023-24 Solutions

> These are independent worked solutions, not an official mark scheme. Materials and structures are kept together in the order used by the paper.

## Materials

### MQ1 - Hip implant stem and neck

| | $E$ (GPa) | Yield (MPa) | UTS (MPa) | El (%) | $T_m$ (°C) | $\rho$ (g/cm³) |
|---|---:|---:|---:|---:|---:|---:|
| 316L (annealed; 18Cr-12Ni-2Mo) | 190 | 450 | 680 | 40 | 1400 | 8.00 |
| Ti-6Al-4V (annealed) | 120 | 877 | 947 | 14 | 1649 | 4.43 |
| Bone (hydroxyapatite + collagen) | 20 | 70 | 80 | 0.5-3 | | 1.35 |

#### (i) Service conditions and four properties to optimise [4]

**Service:**

- **Cyclic loading**, about $10^6$ cycles per year (walking, stairs), with peaks of several times body weight. **Highest peaks and variability when jogging**; high but steady during standing. Bending and torsion at the neck and stem.
- **Body fluid at 37 °C**: warm, **chloride-rich saline**, pH about 7.4 (lower with inflammation), with proteins.
- Contact with bone and cement; wear at the head-cup articulation; **fretting** at the modular taper.
- Expected life **15-25 years** with no inspection.

**Properties:**

1. **Fatigue strength** (HCF, high cycle count): a safe-life design.
2. **Corrosion resistance / biocompatibility**: no ion release, no pitting or crevice attack in chlorides (pits also start fatigue cracks).
3. **Stiffness close to bone**: a very stiff stem carries the load and "stress-shields" the bone, which then resorbs and the implant loosens.
4. **Strength and toughness**: yield strength to avoid permanent bending; toughness for damage tolerance. (Also wear resistance at bearing surfaces, and low density.)

#### (ii) Lifing approach for varying load cycles [3]

This is a **total-life (safe-life)** approach, because implants cannot be inspected in the body:

1. Measure load histories for each activity (walking, stairs, jogging, standing, cycling, knee bends) and **rainflow-count** them into stress-range blocks. Weight them by the expected daily activity mix. **Design for the high-activity patient.**
2. Get **S-N curves** for the implant material and surface finish in simulated body fluid at 37 °C, using ISO stem and neck test loading. Correct for mean stress (Goodman).
3. **Miner's rule** $\sum n_i/N_i$ per day, giving the life in years; apply a large safety factor.
4. Check damage tolerance: Paris-law growth from the largest defect that manufacturing inspection could miss (see part iv).

#### (iii) 316L vs Ti-6Al-4V: comparison table and recommendation [10]

| Performance criterion (why) | Ti-6Al-4V | 316L stainless |
|---|---|---|
| **1. Strength and fatigue** (cyclic loads over decades) | $\alpha+\beta$ alloy: **Al** ($\alpha$ stabiliser) and **V** ($\beta$ stabiliser) give **solid solution + two-phase** strengthening. Forged, then annealed in the $\alpha+\beta$ field for **fine equiaxed $\alpha$**, which resists fatigue initiation. Yield **877 MPa**; high fatigue strength | Austenitic FCC: Cr and Ni solid solution, **no transformation hardening**. Annealed yield only **450 MPa**; strength needs **cold work**, which lowers ductility. Lower fatigue strength |
| **2. Corrosion / biocompatibility** (37 °C chloride fluid) | spontaneous, adherent, **self-healing $\mathrm{TiO_2}$**: excellent; **bone grows onto it** (osseointegration) | Cr (18 %) passive $\mathrm{Cr_2O_3}$; Mo (2 %) for pitting; low C (L) to avoid sensitisation. But **susceptible to pitting, crevice and fretting corrosion** in chlorides; releases Ni ions (allergy) |
| **3. Stiffness match to bone** (stress shielding) | $E$ = **120 GPa**, 6× bone: less shielding | $E$ = **190 GPa**, about 10× bone: more shielding and loosening |
| **4. Density, wear and manufacture** | 4.43 g/cm³ (light). **Poor wear** (galling) and fretting, so use a CoCr or ceramic head. Harder and dearer to machine and forge | 8.0 g/cm³. Cheap, easy to form and machine, weldable. Ductile (40 %), so tolerant of overload |

**Recommendation: Ti-6Al-4V.** It is better on three of the four criteria: nearly **2× the yield and fatigue strength**, far superior **corrosion resistance and osseointegration**, and **stiffness closer to bone**. It is also lighter. Its poor wear is managed by using a CoCr or ceramic femoral head on the taper. 316L is cheaper, so it suits short-term or low-demand uses, such as temporary fracture fixation.

#### (iv) Stem neck defect 0.5 mm after 5 years: remaining life [8]

25-160 MPa, 650 cycles per day; $K_{Ic}=55$; $A=7.45\times10^{-12}$; $m=2.5$; $Q=1.2$ (body-condition data).

$$
\Delta\sigma=135\ \text{MPa},\qquad a_c=\frac1\pi\left(\frac{55}{1.2\times160}\right)^2=26.1\ \text{mm}.
$$

$$
N_f=\frac{0.02612^{-0.25}-0.0005^{-0.25}}{(-0.25)(7.45\times10^{-12})(1.2\times135\sqrt\pi)^{2.5}}
=\frac{2.488-6.687}{(-0.25)(7.45\times10^{-12})(1.397\times10^6)}=\frac{-4.200}{-2.602\times10^{-6}}=\boxed{1.61\times10^6\ \text{cycles}}.
$$

$$
\frac{1.61\times10^6}{650\times365}=\boxed{6.8\ \text{years}}\quad\Rightarrow\quad\text{SF 2: about 3.4 years}.
$$

**Recommendation:** similar patients (implanted at the same time, now 5 years in) should be **reviewed within about 3 years**, with imaging at routine follow-ups. **High-activity patients** (jogging gives higher $\Delta\sigma$) will have much shorter lives, because $N\propto\Delta\sigma^{-2.5}$.

**Caveats:**

- $a_c=26$ mm exceeds the neck diameter, so net-section failure comes much sooner. The real life is **shorter** than predicted.
- The Paris data assume long-crack growth; a 0.5 mm defect is near the short-crack regime.
- Fretting and corrosion at the taper accelerate growth; load spectra vary between patients.

---

### MQ2 - Composites, Jominy, tempering, Larson-Miller

#### (i)(a) Specific strength and modulus at $V_f=0.55$ [6]

Rule of mixtures on the given specific properties (an approximation, strictly valid only for equal densities, but it is what the question intends). Requirement: specific strength > 1 GPa and specific modulus > 80 GPa.

| Composite | Specific strength $0.55\sigma_f/\rho_f+0.45\sigma_m/\rho_m$ | Specific modulus | Meets both? |
|---|---:|---:|:---:|
| Glass/epoxy | $0.55(1.34)+0.45(0.056)=$ **0.76** | $0.55(28.1)+0.45(1.92)=$ **16.3** | ✗ ✗ |
| **Carbon/epoxy** | $0.55(2.1)+0.025=$ **1.18** | $0.55(181)+0.86=$ **100.4** | ✓ ✓ |
| Aramid/epoxy | $0.55(2.5)+0.025=$ **1.40** | $0.55(91)+0.86=$ **50.9** | ✓ ✗ |

**Recommend carbon/epoxy.** It is the only system that meets both requirements. Aramid is strong but not stiff enough (and weak in compression); glass fails both.

#### (i)(b) Carbon/epoxy vs an MMC: 2 advantages and 2 disadvantages [4]

- **Advantages:** (1) much **lower density**, so higher specific stiffness and strength than Al- or Ti-based MMCs; (2) **easier, lower-temperature manufacture** with the shape formed at the same time (no fibre-matrix reactions), plus excellent fatigue and corrosion resistance.
- **Disadvantages:** (1) **low service temperature** (epoxy about 120-180 °C; moisture lowers $T_g$), where an MMC keeps its properties to several hundred °C; (2) **poor transverse, through-thickness, compressive and impact** properties (delamination, BVID) and poor conductivity (lightning), where a ductile metal matrix is tough and isotropic.

#### (i)(c) Manufacturing route [2]

**Prepreg lay-up + vacuum bag + autoclave cure.** It gives the controlled, high $V_f$ (55 %), **< 1 % voids**, accurate fibre orientation and consistent, certifiable properties that aerospace needs. The cost is justified for high-value parts. (For complex shapes at higher volume, RTM is an alternative.)

#### (ii)(a) Jominy equivalence for a 50 mm oil-quenched bar [4]

![[Figures/materials_jominy_readoff_2023_24.png]]

| Position | Equivalent Jominy distance | Hardness |
|---|---:|---:|
| Surface | 7.0 mm | **53.5 HRC** |
| ¾R | 11.5 mm | **48.5 HRC** |
| ½R (mid-radius) | 14.0 mm | **45.5 HRC** |
| Centre | 15.5 mm | **43.5 HRC** |

(Read-offs ± about 0.5 mm and ± 1 HRC.) The surface cools fastest, so it has the most martensite and is hardest. Hardness falls towards the centre as mixed bainite and pearlite form.

#### (ii)(b) The lath microstructure at the surface [3]

**Lath martensite.** The steel is austenitised (FCC, C in solution), then the oil quench at the surface exceeds the critical cooling rate, so the pearlite and bainite noses are missed. Below $M_s$ the FCC lattice transforms by **diffusionless, coordinated shear** (Bain strain) to **body-centred tetragonal** martensite with **carbon trapped**. It forms as fine parallel **laths** (typical of low and medium C) in packets, with a very high dislocation density. The trapped C and dislocations make it very hard (53.5 HRC) and brittle.

#### (ii)(c) Making it more ductile [2]

**Temper**: reheat to about 400-650 °C. C diffuses out to form fine carbides, dislocations recover and quench stresses relax. Hardness falls a little; ductility and toughness rise substantially. A higher temperature or longer time gives more ductility. (Alternatively, use a slower quench or austempering to bainite.)

#### (ii)(d) Larson-Miller: $\mathrm{LMP}=T(20+\log t_r)\times10^{-3}$ [4]

From the fitted line in Fig. MQ2.4 (points 20.15 at 740 MPa and 25.5 at 110 MPa):

- **500 MPa at 700 °C** ($T=973$ K): LMP ≈ 22.2, so $\log t_r=22200/973-20=2.816$, giving $t_r\approx\boxed{655\ \text{h}}$.
- **250 MPa at 600 °C** ($T=873$ K): LMP ≈ 24.3, so $\log t_r=24300/873-20=7.835$, giving $t_r\approx\boxed{6.8\times10^7\ \text{h}}$.

**Comments:**

- Apply a safety factor.
- ±0.2 on the LMP read changes $t_r$ by a factor of about 1.6 (500 MPa case) to 1.7.
- The 250 MPa / 600 °C value (about 7,800 years) is a huge **extrapolation** beyond any test. Oxidation, over-tempering of the martensite and microstructural ageing would govern long before creep rupture.

## Structures

### SQ1 - Open symmetric section under eccentric shear

#### (i) Motion of the free-end section

Since the section is symmetric about $y$, $I_{yz}=0$. A vertical force therefore gives bending curvature only in the (x-y) plane:

$$
\kappa_z=\frac{M_z}{EI_z},\qquad
v_B=\frac{FL^3}{3EI_z}.
$$

The centroid moves vertically in the force direction. However, the load is applied at the bottom-left corner rather than on the shear-centre line, so it also generates torque. The end section rotates about the longitudinal axis while translating; the loaded corner moves by the vector sum of bending translation and twist.

#### (ii) Maximum shear stress

The load is 50 mm from the symmetry/shear-centre line, so

$$
T=200(50)=10{,}000\ \mathrm{N\,mm}.
$$

For the 3 mm open wall, whose total median-line length is approximately (260) mm,

$$
J\simeq\frac13(260)(3^3)=2340\ \mathrm{mm^4}.
$$

Thus the maximum open-section torsional stress is

$$
\tau_{t,\max}=\frac{Tt}{J}=12.82\ \mathrm{MPa}.
$$

The bending shear flow follows $q=VQ/I_z$. Walking from one upper free edge around the section gives a largest running first moment of about $2.87\times10^3\ \mathrm{mm^3}$, hence

$$
\tau_{b,\max}\simeq
\frac{200(2.87\times10^3)}{(297343)(3)}
=0.64\ \mathrm{MPa}.
$$

At the wall face where the two components reinforce,

$$
\boxed{\tau_{\max}\simeq13.5\ \mathrm{MPa}}.
$$

It occurs near the lower corner region at the fixed end. The opposite wall face has the torsional component reversed.

### SQ2 - Overhanging beam by virtual work

Equilibrium gives

$$
\boxed{R_A=-5.8\ \mathrm{kN}},\qquad
\boxed{R_B=11.8\ \mathrm{kN}}.
$$

With $x$ in metres from A, the real bending moment in kNm is

$$
M_1(x)=20-5.8x,\qquad 0\le x\le5,
$$

$$
M_2(x)=20-5.8x+11.8(x-5)-(x-5)^2,
\qquad5\le x\le8.
$$

For a unit vertical force at C, form the piecewise virtual diagram $m_F$ and evaluate

$$
v_C=\int_0^8\frac{Mm_F}{EI}dx.
$$

For a unit moment at C use $m_M$ and

$$
\theta_C=\int_0^8\frac{Mm_M}{EI}dx.
$$

The integrations reduce to

$$
v_C=-\frac{15.25}{EI},\qquad
\theta_C=-\frac{7.333}{EI},
$$

when $M$ is in kNm, $x$ in m and $EI$ in kNm$^2$. The scanned exponent is $I=8\times10^6\ \mathrm{mm^4}$, so with $E=200$ GPa,

$$
EI=1600\ \mathrm{kNm^2}.
$$

Therefore

$$
\boxed{v_C=-9.53\ \mathrm{mm}},\qquad
\boxed{\theta_C=-4.58\times10^{-3}\ \mathrm{rad}}.
$$

The minus signs mean downward displacement and clockwise rotation for the sign convention used here.

### Linked notes

- [[SESA2028 S3 - Shear Flow and Shear Centre]]
- [[SESA2028 S4 - Torsion of Thin-Walled Sections]]
- [[SESA2028 S8 - Virtual Work and Castigliano Theorems]]
