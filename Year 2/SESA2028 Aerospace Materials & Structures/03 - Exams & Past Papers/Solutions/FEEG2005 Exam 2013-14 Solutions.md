---
title: "FEEG2005 Exam 2013-14 Solutions"
aliases: ["FEEG2005 Exam 2013-14 Materials Solutions", "FEEG2005 Exam 2013-14 Structures Solutions"]
module: "SESA2028 Aerospace Materials & Structures"
type: exam-solution
year: "2013-14"
streams: ["Materials", "Structures"]
tags: [sesa2028, feeg2005, exam-solutions, materials, structures]
status: complete
parent: ["[[SESA2028 Past Paper Map]]"]
sources: ["03 - Exams & Past Papers/FEEG2005-201314-02-FEEG2005W1.pdf"]
---

# FEEG2005 Exam 2013-14 Solutions

> These are independent worked solutions, not an official mark scheme. Materials and structures are kept together in the order used by the paper.

## Structures

### A1 - Unsymmetrical bending of an angle section

#### (i) Assumptions

The derivation assumes a straight prismatic beam, homogeneous linear elasticity, small strain and rotation, plane sections remaining plane, stress normal to the section dominating, a centroidal $x$ axis, and Saint-Venant loading sufficiently far from load introduction. The section is not required to be symmetric.

#### (ii) Moment directions

On a cut face whose outward normal is $+x$, positive $M_y$ and $M_z$ follow the right-hand rule about the positive $y$ and $z$ axes.

#### (iii) Section-property check

Treat the angle as two $100\times10$ mm rectangles minus the duplicated $10\times10$ corner. The centroid lies $28.68$ mm from each outer edge. Applying the parallel-axis theorem gives

$$
I_y=I_z\approx1.80\times10^6\ \mathrm{mm^4},\qquad
I_{yz}\approx1.07\times10^6\ \mathrm{mm^4}.
$$

#### (iv) Stress field

With $M_z=800$ Nm and $M_y=0$,

$$
\sigma_x=\frac{M_zI_{yz}}{I_yI_z-I_{yz}^2}z
-\frac{M_zI_y}{I_yI_z-I_{yz}^2}y.
$$

Using millimetres and megapascals,

$$
\boxed{\sigma_x=0.4086z-0.6873y\ \mathrm{MPa}}.
$$

The neutral axis is

$$
0.4086z-0.6873y=0
\quad\Rightarrow\quad y=0.5945z.
$$

Checking the angle vertices gives the largest magnitude at the inner bottom corner $(y,z)=(71.3,18.7)$ mm:

$$
\boxed{\sigma_{x,min}\approx-41.4\ \mathrm{MPa}}.
$$

The largest tension is about $+31.5$ MPa at the outer top-right corner.

### A2 - Overhanging beam by energy methods

The supports are at $A$ and $B$, separated by $2a$, and the end load $P$ acts at $C$, $3a$ from A. Equilibrium gives

$$
R_A=-\frac P2,\qquad R_B=\frac{3P}{2}.
$$

Therefore

$$
M(x)=\begin{cases}-Px/2,&0<x<2a,\\P(x-3a),&2a<x<3a.\end{cases}
$$

The bending energy is

$$
U=\frac1{2EI}\left[\int_0^{2a}\frac{P^2x^2}{4}\,dx+
\int_{2a}^{3a}P^2(x-3a)^2\,dx\right]
=\frac{P^2a^3}{2EI}.
$$

Hence the downward displacement at C is

$$
\boxed{\delta_C=\frac{\partial U}{\partial P}=\frac{Pa^3}{EI}}.
$$

For the slope, apply a unit moment at C. Its virtual moment field is $m=x/(2a)$ for $0<x<2a$ and $m=1$ for $2a<x<3a$. Thus

$$
\theta_C=\int\frac{Mm}{EI}\,dx
=-\frac{7Pa^2}{6EI}.
$$

The magnitude is

$$
\boxed{|\theta_C|=\frac{7Pa^2}{6EI}}.
$$

### A3 - Eccentrically loaded tubular strut

#### (i) Governing equation

At a deflected section the moment is $M=P(e+v)$. With $M=-EIv''$ under a consistent sign convention,

$$
EIv''+Pv=-Pe,\qquad \mu^2=\frac{P}{EI}.
$$

Applying $v(0)=v(L)=0$ gives the stated secant-column solution.

#### (ii) Euler load

$$
A=\frac\pi4(150^2-130^2)=4398.2\ \mathrm{mm^2},
$$

$$
I=\frac\pi{64}(150^4-130^4)=1.0831\times10^7\ \mathrm{mm^4}.
$$

$$
\boxed{P_E=\frac{\pi^2EI}{L^2}=2.494\ \mathrm{MN}}.
$$

Because $800$ kN $<P_E$, the ideal centrally loaded column does not Euler-buckle.

#### (iii) Stress at midspan for $e=10$ mm

$$
\mu L/2=0.8896,\qquad \sec(\mu L/2)=1.5880,
$$

$$
v_{max}=e(\sec-1)=5.88\ \mathrm{mm}.
$$

Direct compression:

$$
\boxed{\sigma_d=-P/A=-181.9\ \mathrm{MPa}}.
$$

The maximum bending moment is $P(e+v)=Pe\sec(\mu L/2)$, so at $c=75$ mm,

$$
\boxed{\sigma_b=\pm87.97\ \mathrm{MPa}}.
$$

The most compressed fibre therefore reaches

$$
\boxed{\sigma_{min}=-269.9\ \mathrm{MPa}}.
$$

## Materials

### B1 - Aircraft wing: fatigue lifing and environment

#### (i) Total life vs damage tolerance, and the data needed [5]

- **Total life**: predicts cycles to initiate *and* grow a crack in nominally defect-free material, using S-N (HCF) or $\varepsilon$-N (LCF) curves with Miner's rule for variable loading. It effectively designs against initiation, so it is very sensitive to surface finish. **Data**: S-N or $\varepsilon$-N curves for the material, surface condition, mean stress and environment; the service load spectrum (rainflow-counted); local stress concentrations.
- **Damage tolerance**: assumes a crack is present and predicts growth from $a_i$ to $a_c$ with the Paris law, then sets inspection intervals. **Data**: $a_i$ from NDT (size and position), $\Delta\sigma$ and $\sigma_{max}$, $K_{Ic}$, the Paris constants $A$ and $m$ for the service environment, and the geometry factor $Q$.

See [[Total Life vs Damage Tolerance]].

#### (ii) Remaining flights [10]

$a_i=3$ mm; 20-200 MPa once per flight; $K_{Ic}=45$; $A=2.67\times10^{-10}$; $m=3$; $Q=1.2$.

$$
\Delta\sigma=180\ \text{MPa},\qquad a_c=\frac1\pi\left(\frac{45}{1.2\times200}\right)^2=11.19\ \text{mm}.
$$

$$
N_f=\frac{a_c^{-1/2}-a_i^{-1/2}}{(-\tfrac12)A(1.2\times180\sqrt\pi)^3}
=\frac{9.453-18.257}{(-\tfrac12)(2.67\times10^{-10})(5.612\times10^7)}
=\frac{-8.804}{-7.492\times10^{-3}}=\boxed{1175\ \text{flights}}.
$$

**Recommendation:** with SF 2, allow about **590 flights**, then re-inspect. That is less than a year of short-haul flying, so plan a repair (blend out and re-inspect, or a doubler). The crack spends most of its life small, so re-inspecting early catches it with margin.

#### (iii) Humid and salty service: other problems [4]

- **Corrosion fatigue**: the aqueous and chloride environment raises $da/dN$ (effectively a larger $A$ and lower threshold) and removes any fatigue limit.
- **Pitting** (Al-alloy second-phase particles in chlorides) creates new stress concentrations and crack origins, so there is no initiation period.
- **Stress corrosion cracking**: 7xxx alloys are susceptible under sustained tensile stress (residual or ground load) in humid or salty conditions.
- Exfoliation and intergranular corrosion in 7xxx; galvanic attack at fasteners; crevices at joints.

**Effect on lifing:** the lab-air Paris constants are **unconservative**. Use environment-specific $A$ and $m$, allow for additional origins, and shorten inspection intervals.

#### (iv) Improving the service life [6]

| Measure | Failure mode addressed | Wing-design caveat |
|---|---|---|
| **Shot peening** holes and fillets; cold-expand fastener holes | fatigue initiation (compressive residual stress) | small weight cost; roughness |
| Generous **radii**, better detailing, lower $K_t$ | fatigue initiation | geometry and weight |
| Switch the lower skin to **damage-tolerant 2xxx** (2024-T3) or **GLARE** | fatigue crack growth (lower $da/dN$, higher $K_{Ic}$) | lower strength than 7xxx means a thicker skin |
| Over-age 7xxx (T73 / T76 instead of T6) | SCC and exfoliation | about 10-15 % strength loss |
| **Cladding / anodising + primer + sealant**, drainage, avoid crevices | corrosion, pitting | maintenance |
| Reduce stress (thicker skin locally) | all | weight: must stay light |
| Better NDT, more frequent inspection | catches cracks earlier | cost and downtime |

---

### B2 - Aluminium alloys and composites

#### (i) Why cast Al is worse than wrought [3]

Castings contain **defects**: interdendritic shrinkage porosity (poor liquid feeding), gas pores, oxide films and inclusions from turbulent filling. They also have a coarse, segregated dendritic structure with coarse brittle intermetallics. Each pore or oxide is a crack starter, so ductility, toughness and fatigue strength are low. Wrought processing closes pores, breaks up intermetallics and refines grains.

#### (ii) Microstructural features controlled in wrought Al [8]

| Feature | How it is controlled | Effect |
|---|---|---|
| **Grain size and shape** | working + recrystallisation anneal; dispersoids (Mn, Cr, Zr) pin boundaries | Hall-Petch strength *and* toughness; elongated grains give anisotropy |
| **Solute in solution** | composition (Cu, Mg, Zn, Si) + solution treatment + quench | solid-solution strengthening; the supersaturation needed for ageing |
| **Precipitates** (type, size, spacing, coherency) | composition + ageing time and temperature (T4/T6/T7) | the main strengthening (shearing or Orowan); over-ageing trades strength for SCC resistance |
| **Dislocation density** | cold work (H tempers) | work hardening |
| **Texture** | rolling and extrusion schedule | directional properties |
| **Defects and intermetallics** | hot working closes porosity and breaks up constituent particles | ductility, toughness, fatigue |
| **Grain-boundary precipitates and PFZs** | quench rate and ageing | toughness and corrosion |

Compared with cast alloys: fewer defects, finer and controlled grains, and optimised precipitation give higher strength, ductility, toughness and fatigue strength.

#### (iii) Peak-ageing sequence [4]

1. **Solution treat** (~500-550 °C) in the single-phase $\alpha$ field: all the Cu (or Zn, Mg) dissolves; one uniform solid solution.
2. **Water quench**: no time for diffusion, so a **supersaturated** $\alpha$ solid solution with vacancies retained.
3. **Artificial ageing** (~120-190 °C) in the two-phase field: solute clusters (GP zones), then coherent $\theta''$/$\theta'$ (or $\eta'$) precipitates, fine and closely spaced. Stop at **peak strength (T6)**, before coarsening to incoherent $\theta$ (over-ageing).

![[Figures/materials_ageing_curve.png]]

#### (iv) Vacuum impregnation vs hand lay-up [5]

**Why vacuum is better:** atmospheric (and autoclave) pressure consolidates the laminate, **squeezes out trapped air and excess resin**, and gives **low voids (< 1 %)**, higher and more uniform $V_f$, good wet-out, and properties that do not depend on operator skill. Hand lay-up relies on rolling by hand: high voids, resin-rich areas, variable quality.

**What restricts wider use:** cost (prepreg, frozen storage, consumables such as peel ply, breather and bag film; autoclave capital), **part size** limited by the autoclave, slow labour-intensive bagging, and one-sided moulds. It needs volume or high value to justify it.

#### (v) 60 % glass / 40 % resin: $E_L$ and $E_T$ [5]

$$
E_L=0.6(72.5)+0.4(4)=\boxed{45.1\ \text{GPa}},\qquad
E_T=\left(\frac{0.6}{72.5}+\frac{0.4}{4}\right)^{-1}=\boxed{9.24\ \text{GPa}}.
$$

The composite is about 5× stiffer along the fibres. **Less anisotropic:** use a 0/90 cross-ply or quasi-isotropic 0/±45/90 lay-up, woven fabric, or random chopped-strand mat. This lowers peak $E_L$ but balances the in-plane properties. (The question says "epoxy" and then "polyester"; the answer is the same.)

---

### B3 - Steels and high-temperature materials

#### (i) Quench + temper 0.4 % C steel [5]

Fast quench from austenite (FCC, C in solution) goes past the pearlite nose, so C cannot diffuse out. The lattice shears to **BCT martensite** with C trapped: highly strained and dislocated, so very hard and brittle. Heating to **580 °C for 1 h tempers** it: C diffuses to form a **fine carbide dispersion** and the lattice relaxes. Strength falls slightly; ductility and toughness improve greatly. Full answer: [[SESA2028 Materials Tutorial MT4 - Alloy Design Solutions]] (Q3).

#### (ii) Roles of Ni and Cr [5]

- **Ni**: an **austenite ($\gamma$) stabiliser**. It expands the $\gamma$ field and lowers the $\gamma\to\alpha$ transformation and $M_s$, so with about 8 % Ni (18/8) the steel stays **FCC austenite at room temperature**. It is then non-magnetic, tough, has no DBT and is formable, and cannot be hardened by quenching.
- **Cr**: above **12 %** it forms a thin, coherent, adherent, self-healing $\mathrm{Cr_2O_3}$ **passive film** that blocks ion and electron transport ([[Evans Diagram and Passivation]]). It is also a ferrite stabiliser and carbide former.

#### (iii) Intergranular attack after slow cooling [5]

Slow cooling through about 500-800 °C lets **$\mathrm{Cr_{23}C_6}$ precipitate on grain boundaries**, depleting the adjacent zone **below 12 % Cr**. That zone cannot passivate, so it becomes a narrow **anode** next to large passive grain **cathodes**: rapid intergranular corrosion (weld decay). **Avoid it by:** cooling rapidly (or solution annealing and quenching); **low-C "L" grades** (304L/316L); or **stabilising with Ti or Nb**, stronger carbide formers that leave Cr in solution. See [[Sensitisation and Weld Decay]].

#### (iv) SRR99 creep life by Miner's rule [6]

Data at 400 MPa: 700 °C 100,000 h; 800 °C 10,000 h; 900 °C 1,050 h; 1000 °C 200 h; 1100 °C 15 h.

**Method:** assume each temperature uses life in proportion $t_i/t_{r,i}$; failure when $\sum t_i/t_{r,i}=1$. Rupture lives are exponential in temperature, so **interpolate on a log scale**.

$$
t_r(850)\approx3163\text{-}3240\ \text{h},\qquad t_r(750)\approx31{,}623\ \text{h}.
$$

(The lecturer reads 3,163 h from a log-log plot; interpolating $\log t_r$ linearly against $T$ gives 3,240 h.)

$$
\frac{500}{3163}+\frac{2100}{31623}=0.158+0.066=0.224,
$$

$$
t_{remaining}(1000\ ^\circ\text{C})=(1-0.224)\times200=\boxed{155\ \text{h}}.
$$

**Recommendation:** with SF 2, about **78 h**. Note the sensitivity to the interpolation method and to the steep temperature dependence.

![[Figures/materials_creep_interpolation_temperature.png]]

#### (v) Coatings and single crystals [4]

- **Coatings:** a **thermal barrier coating**: low-conductivity **YSZ** top coat (EB-PVD columnar for strain tolerance) on an **aluminide or MCrAlY bond coat**, which grows a protective $\mathrm{Al_2O_3}$ TGO. Combined with internal and film cooling, this gives a large temperature drop, so the metal runs cooler.
- **Single crystal:** no grain boundaries, so no **boundary sliding, cavitation or boundary oxidation** (the main creep-rupture paths). Boundary-strengthening elements (C, B, Zr), which lower the melting point, can be removed, allowing a higher solution temperature and more, finer $\gamma'$. Growth along ⟨001⟩ gives a low axial modulus, so better thermal fatigue. See [[Single Crystal Casting]].
