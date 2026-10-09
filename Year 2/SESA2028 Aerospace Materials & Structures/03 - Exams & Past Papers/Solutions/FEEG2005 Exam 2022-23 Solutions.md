---
title: "FEEG2005 Exam 2022-23 Solutions"
aliases: ["FEEG2005 Exam 2022-23 Materials Solutions", "FEEG2005 Exam 2022-23 Structures Solutions"]
module: "SESA2028 Aerospace Materials & Structures"
type: exam-solution
year: "2022-23"
streams: ["Materials", "Structures"]
tags: [sesa2028, feeg2005, exam-solutions, materials, structures]
status: complete
parent: ["[[SESA2028 Past Paper Map]]"]
sources: ["03 - Exams & Past Papers/FEEG2005-202223-02-FEEG2005.pdf"]
---

# FEEG2005 Exam 2022-23 Solutions

> These are independent worked solutions, not an official mark scheme. Materials and structures are kept together in the order used by the paper.

## Materials

### MQ1 - Aero-engine vs industrial gas turbine (IGT) blades and discs

#### (i) Service conditions: aero vs IGT, and why they differ [4]

| | Aero-engine turbine blade | IGT turbine blade |
|---|---|---|
| Temperature and time | **peak 970-1120 °C** for about 300 h accumulated (take-off and climb); **cruise 720-870 °C** for 10,000+ h | **870-1020 °C for about 50,000 h** (long steady running) |
| Loading | high centrifugal stress; **one major thermal + mechanical cycle per flight** (LCF / thermo-mechanical fatigue, many thousands of cycles); vibration (HCF) | sustained centrifugal stress, so **creep and oxidation / hot corrosion dominate**; increasingly **cycled** (start-stops to balance renewables), adding LCF and thermal fatigue |
| Why different | thrust is needed **briefly** at take-off; weight is critical, so the engine is run hot and small, with short, intense peaks and maintenance every few thousand hours | designed for **efficiency and long life** at steady base or part load; weight unimportant, so a larger, cooler, longer-lived design; cheaper fuels bring hot corrosion |

#### (ii) Aero blade: properties, materials, alloying, manufacture, protection [9]

**Properties:** creep resistance, oxidation and hot-corrosion resistance, TMF/LCF and HCF resistance, high $T_m$, strength retained at temperature, toughness, reasonable density.

**Material: a single-crystal Ni-base superalloy** (e.g. CMSX-4):

- $\gamma$ FCC Ni matrix: tough, no DBT; solid-solution strengthened by Co, Cr, Mo, **W, Re** (slow diffusion, raise $T_m$).
- **Al + Ti + Ta** give about 60-70 % coherent, ordered **$\gamma'$ $\mathrm{Ni_3(Al,Ti)}$**, which resists coarsening and strengthens with temperature.
- **Cr and Al** give protective $\mathrm{Cr_2O_3}$ / $\mathrm{Al_2O_3}$.
- **No C, B, Zr** in SX (no boundaries to strengthen), so the melting point rises and a full solution heat treatment is possible.

**Manufacture:**

1. **Investment casting** with ceramic cores for cooling passages.
2. **Directional solidification + helical grain selector**, giving a single crystal along ⟨001⟩: no transverse boundaries for sliding, cavitation or oxidation; low axial modulus for TMF.
3. **Solution + ageing** heat treatment to optimise $\gamma'$.
4. Machine the fir-tree root; **shot peen** the root for fatigue; laser-drill film-cooling holes.

**Protection:** aluminide (Pt-modified) or MCrAlY **bond coat** plus a **YSZ TBC** by EB-PVD (columnar). The TGO $\mathrm{Al_2O_3}$ is the oxidation barrier. Together with internal and film cooling, this lowers the metal temperature by about 100-150 °C, slowing creep, oxidation and diffusion. See [[Single Crystal Casting]], [[Thermal Barrier Coatings]].

#### (iii) Where will fatigue cracks start in the disc? [2]

- **At the bore**: temperature is lower (~300-400 °C), but the **hoop stress is highest** there ([[Spinning Disc Stress]]). Every flight is a large LCF cycle, and cracks start from inclusions, pores or machining damage.
- **At the rim fir-tree slots**: stress is lower, but there are **severe stress concentrations** at the slot fillets, **fretting** with the blade roots, and the **highest disc temperature (> 650 °C)**, where oxidation-assisted and dwell (creep-fatigue) crack growth occur.

Most likely: **the fir-tree slot fillets** (stress concentration + temperature + oxidation). The bore is critical because of its high stress, and a bore burst is uncontainable.

#### (iv) Disc crack 1.5 mm, one cycle per flight [10]

25-550 MPa; $K_{Ic}=125$ MPa√m; $A=7.35\times10^{-11}$; $m=2.5$; $Q=1.2$ (data at service temperature).

$$
\Delta\sigma=525\ \text{MPa},\qquad a_c=\frac1\pi\left(\frac{125}{1.2\times550}\right)^2=11.4\ \text{mm}.
$$

$$
N_f=\frac{0.01142^{-0.25}-0.0015^{-0.25}}{(-0.25)(7.35\times10^{-11})(1.2\times525\sqrt\pi)^{2.5}}
=\frac{3.059-5.081}{(-0.25)(7.35\times10^{-11})(4.167\times10^7)}=\frac{-2.022}{-7.656\times10^{-4}}=\boxed{2641\ \text{flights}}.
$$

**Recommend about 1,300 flights** (SF 2), or remove the disc now. Aero-engine discs are safety-critical ("retirement for cause"), so a found crack normally means the disc is retired at the next shop visit.

**Assumptions and caveats:**

- $Q$ constant; a semi-elliptical surface crack.
- Paris data at the right temperature, but they may not include **dwell and oxidation** effects (hold at maximum take-off).
- Short-crack and Stage I growth ignored.
- $K_{Ic}$ at temperature; possible overloads.
- Residual stresses from shot peening are not included.

---

### MQ2 - Titanium alloys and a Ti-MMC compressor blade

| Alloy | Heat treatment | Yield (MPa) | UTS (MPa) | El (%) | $\rho$ (g/cm³) |
|---|---|---:|---:|---:|---:|
| CP Ti | annealed | 414 | 484 | 25 | 4.51 |
| Ti-5Al-2.5Sn | annealed | 784 | 826 | 16 | 4.48 |
| Ti-6Al-4V | annealed | 877 | 947 | 14 | 4.43 |
| Ti-10V-2Fe-3Al | solution + aged | 1150 | 1223 | 10 | 4.65 |

#### (i) Phases, strengthening, heat treatment, and one application each [8]

| Alloy | (a) Phases | (b) Main strengthening | (c) Link to heat treatment | (d) Application and why |
|---|---|---|---|---|
| **CP Ti** | $\alpha$ (HCP) | interstitial **O** solid solution; grain size | annealed (recrystallised grains, no phase change) | chemical and marine plant, airframe skins, implants: best **corrosion** resistance and ductility (25 %) |
| **Ti-5Al-2.5Sn** | $\alpha$ | **substitutional** solid solution (Al, Sn are $\alpha$ stabilisers) | annealed; not age-hardenable; microstructure **thermally stable** | **engine casings and rings to ~480 °C**: good creep, weldable |
| **Ti-6Al-4V** | $\alpha+\beta$ | solid solution + two-phase microstructure (V stabilises $\beta$); morphology (equiaxed or lamellar) | annealed in $\alpha+\beta$ gives equiaxed $\alpha$ + transformed $\beta$ (can also be STA) | fan blades, airframe, **hip implants**: best all-round strength, fatigue, toughness and biocompatibility |
| **Ti-10V-2Fe-3Al** | metastable $\beta$ (BCC) + fine $\alpha$ precipitates | solid solution (V, Fe) + **precipitation** of fine $\alpha$ | **solution treat → quench (retain $\beta$) → age** (like Al) | **landing gear and high-strength airframe forgings**: highest strength (1150 MPa); formable before ageing, though denser |

#### (ii) Matrix for a 550 °C compressor MMC [3]

**Ti-5Al-2.5Sn** (an $\alpha$ alloy). Single-phase $\alpha$ is **thermally stable**: no precipitates to coarsen or dissolve, and the best creep resistance (HCP, lower diffusivity) and oxidation resistance of the four at 550 °C. It is also weldable and diffusion-bondable for MMC processing. The fibres provide most of the stiffness and strength, so the matrix mainly needs temperature stability.

Ti-6Al-4V loses creep strength above about 400-450 °C. The $\beta$ alloy's precipitates are unstable at temperature and it is denser. CP Ti is too weak.

#### (iii) Choosing the reinforcement: $E\ge220$ GPa, $\sigma_y\ge1250$ MPa [6]

Approach: the blade length is fixed and loading is along the blade, so continuous aligned fibres along the blade axis, with the isostrain rule of mixtures. For each fibre, find $V_f$ for stiffness and for strength, take the larger, then compare **density** (weight drives efficiency and disc load). Matrix Ti-6Al-4V: $E=120$, $\sigma_y=877$, $\rho=4.43$. (With Ti-5Al-2.5Sn, $\sigma_y=784$, the strength $V_f$ values rise slightly and the choice is unchanged.)

| Fibre ($E$, $\sigma_y$, $\rho$) | $V_f(E)$ | $V_f(\sigma_y)$ | $V_f$ | $\rho_c$ (g/cm³) | Comment |
|---|---:|---:|---:|---:|---|
| SiC (400, 3900, 3.0) | 0.357 | 0.123 | **0.36** | **3.92** | feasible, light |
| $\mathrm{Al_2O_3}$ (379, 1380, 3.95) | 0.386 | 0.742 | 0.74 | 4.07 | too high $V_f$ (strength limited) |
| C (500, 2000, 2.0) | 0.263 | 0.332 | 0.33 | 3.62 | lightest, but **reacts with Ti** (TiC) during processing and **oxidises** at 550 °C |
| W (407, 2890, 19.3) | 0.348 | 0.185 | 0.35 | 9.61 | far too dense |

**Recommendation: SiC fibre**, at a moderate 36 % with low density (about 12 % lighter than monolithic Ti-6-4). It is chemically compatible with Ti when carbon-coated and proven in Ti MMCs (blings). Carbon's lower density is outweighed by interfacial reaction and oxidation.

#### (iv) Tempered martensitic stainless steel for an IGT LP steam blade (200-300 °C) [4]

- About **12-13 % Cr** gives a passive film, enough for wet steam at 200-300 °C (corrosion and water-droplet erosion). Enough C, and Ni in some grades, to allow a martensitic transformation.
- **Quench** gives martensite (high strength). **Temper** gives fine carbides: tough, good **fatigue** resistance (HCF from blade vibration) with residual strength. Mo and V give tempering resistance (secondary hardening), keeping strength at operating temperature.
- Moderate temperature means creep is not an issue.
- Cheaper and easier to machine and forge than Ti or Ni alloys. Magnetic and weldable enough for repair.
- (Watch pitting and SCC in contaminated steam; shot peen or erosion-shield the leading edges.)

#### (v) Tempered martensitic stainless at 450 MPa: creep [1 + 3]

**(a)** The life falls **non-linearly** (exponentially) with temperature because creep is **thermally activated**: $t_r\propto\exp(Q/RT)$. So interpolate linearly in **$\log t_r$** (against $T$ or $1/T$) between neighbouring data points, never linearly in $t_r$.

**(b)** Miner's rule, interpolating $\log t_r$ linearly in $T$:

- 625 °C (between 600 °C: 212,843 h and 650 °C: 118,044 h): $t_r=158{,}500$ h, so $85{,}000/158{,}500=0.536$.
- 680 °C (between 650 and 700 °C: 69,558 h): $t_r=85{,}950$ h.

$$
t_{remaining}=(1-0.536)\times85{,}950=\boxed{39{,}900\ \text{h}}\quad(\approx4.5\ \text{years};\ \text{SF 2: about 20,000 h}).
$$

**Assumptions:** linear, order-independent damage; constant stress; no oxidation or microstructural ageing (over-tempering). Interpolation is only valid inside the data range.

![[Figures/materials_creep_interpolation_temperature.png]]

## Structures

### SQ1 - Rotated channel cantilever

The principal properties supplied are

$$
I_1=150{,}744.1\ \mathrm{mm^4},\qquad
I_2=896{,}933.3\ \mathrm{mm^4},\qquad I_{12}=0.
$$

#### (i) Best orientation

For a cantilever tip force,

$$
\delta=\frac{WL^3}{3EI_{\text{bending axis}}}.
$$

The load must therefore bend about axis 2, the strong axis. This is option (ii), where the global $z$-axis is aligned with principal axis 2:

$$
\boxed{\text{option (ii) minimises the downward deflection}.}
$$

#### (ii) Maximum weight for option (i)

Option (i) bends about the weak axis $I_1$. The allowable normal stress is

$$
\sigma_{allow}=240/3=80\ \mathrm{MPa}.
$$

The furthest material is at the upper free edges, $c=50-5.37=44.63$ mm from the centroid. Since $M=WL$,

$$
80=\frac{W(1500)(44.63)}{150{,}744.1}.
$$

Thus

$$
\boxed{W_{\max}=180\ \mathrm{N}}.
$$

The governing normal stresses occur at the wall clamp and at the two upper free-edge corners of the channel.

#### (iii) Shear stress for option (ii), $W=300$ N

Walk from either free edge around the open wall and use

$$
q(s)=\frac{VQ(s)}{I_2},\qquad \tau=q/t.
$$

The flow is zero at both free edges. Using side-wall median coordinate $x\simeq49$ mm and median height (47.5) mm, the running first moment at a side-to-base corner is

$$
|Q|\simeq(2)(47.5)(49)=4655\ \mathrm{mm^3}.
$$

Therefore

$$
|q|=\frac{300(4655)}{896933.3}=1.557\ \mathrm{N/mm},
$$

and in the 2 mm side wall

$$
\boxed{\tau_{\max}\simeq0.78\ \mathrm{MPa}}.
$$

The bottom-wall centre has larger flow but also the larger 5 mm thickness, giving about (0.71) MPa. Hence the maximum is at the two lower corner regions in the 2 mm side walls. It is constant along the beam away from the small load-introduction zone because the internal shear $V=300$ N is constant.

### SQ2 - Portal frame under an end couple

The applied end couple produces the same bending moment magnitude $M$ throughout all three members.

#### (i) Rotation at D by Castigliano

The strain energy is

$$
U=\sum\int\frac{M^2}{2EI_z}ds
=\frac{M^2}{2EI_z}(2H+L).
$$

Therefore

$$
\boxed{\theta_D=\frac{\partial U}{\partial M}
=\frac{M(2H+L)}{EI_z}}.
$$

#### (ii) Horizontal displacement of C by virtual work

Apply a unit horizontal load at C. Only member AB has a virtual bending field; measured upward from A,

$$
m(y)=H-y.
$$

The real field is $M$, hence

$$
\delta_{C,x}=\int_0^H\frac{Mm(y)}{EI_z}dy
=\boxed{\frac{MH^2}{2EI_z}}.
$$

The sign follows the sense of $M$ and the chosen positive unit load.

### Linked notes

- [[SESA2028 S2 - Beam Deflection and Bending Design]]
- [[SESA2028 S3 - Shear Flow and Shear Centre]]
- [[SESA2028 S8 - Virtual Work and Castigliano Theorems]]
