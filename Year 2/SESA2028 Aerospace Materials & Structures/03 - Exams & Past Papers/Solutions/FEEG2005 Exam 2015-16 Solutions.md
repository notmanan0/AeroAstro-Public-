---
title: "FEEG2005 Exam 2015-16 Solutions"
aliases: ["FEEG2005 Exam 2015-16 Materials Solutions", "FEEG2005 Exam 2015-16 Structures Solutions"]
module: "SESA2028 Aerospace Materials & Structures"
type: exam-solution
year: "2015-16"
streams: ["Materials", "Structures"]
tags: [sesa2028, feeg2005, exam-solutions, materials, structures]
status: complete
parent: ["[[SESA2028 Past Paper Map]]"]
sources: ["03 - Exams & Past Papers/FEEG2005-201516-02-FEEG2005W1.pdf"]
---

# FEEG2005 Exam 2015-16 Solutions

> These are independent worked solutions, not an official mark scheme. Materials and structures are kept together in the order used by the paper.

## Structures

### A1 - Flat-bar bending, shear centre and multi-cell torsion

#### (i) Flat-bar stress reduction

For a flat rectangular bar aligned with centroidal $y,z$ axes, both axes are axes of symmetry, hence $I_{yz}=0$. Substitution into the general unsymmetrical-bending expression removes the coupling terms and gives

$$
\boxed{\sigma_x=-\frac{M_z}{I_z}y+\frac{M_y}{I_y}z}
$$

up to the stated positive-moment convention.

#### (ii) Shear centre of the open symmetric section

The section is symmetric about the horizontal axis, so its shear centre lies on that axis. Starting from each free edge, form

$$
q(s)=\frac{FQ(s)}{I_z}
$$

and integrate the torque of the wall flow about point D. With the thin-wall geometry shown,

$$
I_z=\frac{62+16\sqrt2}{3}\,ta^3.
$$

Moment equilibrium gives the shear-centre coordinate

$$
\boxed{z_S\approx-1.182a}
$$

measured from D, i.e. $1.182a$ to the left of D on the symmetry axis. This external location is typical of an open section whose wall flow produces a substantial twisting moment.

#### (iii) Multi-cell torsion

Assign a constant circulation $q_i$ to each cell. A common wall carries the algebraic difference $q_i-q_j$. Use one torque equation,

$$
T=2\sum A_iq_i,
$$

and equal-twist compatibility for all cells,

$$
\frac1{2A_iG}\oint_i\frac{q_{wall}}t\,ds
=\frac1{2A_jG}\oint_j\frac{q_{wall}}t\,ds.
$$

Finally calculate $\tau=q_{wall}/t$ on every distinct wall.

### A2 - Cantilever under a full-span UDL

For $w=3$ kN/m, $L=5$ m, $E=200$ GPa and $I=25\times10^6\ \mathrm{mm^4}$,

$$
EI=5.00\times10^6\ \mathrm{N\,m^2}.
$$

Using Castigliano or the unit-load method,

$$
\delta_B=\frac{wL^4}{8EI}
=\boxed{46.9\ \mathrm{mm}\ \text{downward}},
$$

$$
\theta_B=\frac{wL^3}{6EI}
=\boxed{0.0125\ \mathrm{rad}}.
$$

### A3 - Compound cylinder

#### (i) Equivalent monobloc cylinder

For $r_i=100$ mm, $r_o=150$ mm and $p_i=80$ MPa,

$$
A=64\ \mathrm{MPa},\qquad B=1.44\times10^6\ \mathrm{MPa\,mm^2}.
$$

Therefore

$$
\boxed{\sigma_\theta(100)=208\ \mathrm{MPa}},\qquad
\boxed{\sigma_\theta(150)=128\ \mathrm{MPa}}.
$$

#### (ii) Compound cylinder

The shrink pressure is 10 MPa at $r=125$ mm. It produces residual hoop stresses:

| Location | Inner tube residual | Outer tube residual |
|---|---:|---:|
| $r=100$ mm | $-55.56$ MPa | - |
| $r=125$ mm | $-45.56$ MPa | $+55.45$ MPa |
| $r=150$ mm | - | $+45.45$ MPa |

Because both tubes are the same material and remain in contact, the pressure-only field is the monobloc Lamé field. At $r=125$ mm it is $156.16$ MPa. Superposition gives

| Location | Resultant hoop stress |
|---|---:|
| bore, $r=100$ mm | $152.44$ MPa |
| inner side of junction | $110.60$ MPa |
| outer side of junction | $211.61$ MPa |
| outside, $r=150$ mm | $173.45$ MPa |

The fit moves tensile demand away from the bore and creates a hoop-stress jump at the interface. With the specified 10 MPa contact pressure, the maximum is approximately $212$ MPa just outside the junction.

## Materials

### B1 - Fatigue: applications and an offshore weld

#### (i) One total-life application and one damage-tolerant application [9]

**Total life: a helicopter main-rotor shaft or hub (or a rotating machine shaft).**

- *Loads*: rotating bending and torsion once per revolution (HCF, about $10^8$-$10^9$ cycles), plus start-stop and manoeuvre loads.
- *Why total life*: a crack grows to failure in very few flight hours, and the part is not practically inspectable between flights. It must be designed so that cracks **never initiate**: a safe life with a scatter factor.
- *Data*: S-N curves for the actual material, surface finish and heat treatment (including notched and fretting data); a measured flight-load spectrum rainflow-counted into blocks; Goodman correction for mean stress; Miner summation with safety factors.

**Damage tolerant: an aircraft fuselage or lower wing skin.**

- *Loads*: one ground-air-ground (pressurisation and wing bending) cycle per flight, plus gust and manoeuvre cycles.
- *Why damage tolerance*: the structure is large, redundant and inspectable. Cracks from rivet holes or corrosion are expected and must be found before they reach critical size.
- *Data*: the NDT detectable crack size and position (the largest crack that could be missed); stress range and peak stress; $K_{Ic}$ (or $K_c$ for thin sheet); Paris $A$, $m$ for the alloy and environment; geometry factors. These give the crack-growth life and the inspection intervals.

#### (ii) Offshore welded joint: years remaining [10]

$a_i=5$ mm; 10-200 MPa, 30 storms per year; $K_{Ic}=38$; $A=2.05\times10^{-11}$; $m=3.5$; $Q=1.2$.

$$
\Delta\sigma=190\ \text{MPa},\qquad a_c=\frac1\pi\left(\frac{38}{240}\right)^2=7.98\ \text{mm}.
$$

$$
N_f=\frac{0.00798^{-0.75}-0.005^{-0.75}}{(-0.75)(2.05\times10^{-11})(1.2\times190\sqrt\pi)^{3.5}}
=\frac{37.45-53.18}{(-0.75)(2.05\times10^{-11})(1.327\times10^9)}=\frac{-15.73}{-0.0204}=\boxed{771\ \text{storms}},
$$

$$
\text{life}=\frac{771}{30}=\boxed{25.7\ \text{years}}\quad\Rightarrow\quad\text{SF 2: about 13 years, with re-inspection well before then}.
$$

The critical crack is only 3 mm deeper than the existing one, because weld metal has low toughness. Any extra-severe storm (higher $\sigma_{max}$) reduces $a_c$ sharply.

#### (iii) Other factors, and mitigation [6]

| Factor | Effect on the calculation |
|---|---|
| **Seawater corrosion fatigue** | higher $da/dN$ than air data; no fatigue limit |
| **Cathodic protection → hydrogen** | hydrogen embrittlement of weld and HAZ; lower $K_{Ic}$, faster growth |
| **Tensile weld residual stress** | raises mean stress and effective $\Delta K$ (closure removed); the whole cycle is effectively tensile |
| **Weld defects** (porosity, slag, lack of fusion, toe undercut) and HAZ microstructure | extra origins; locally low toughness; $Q$ larger at the weld toe |
| **Low temperature** (North Sea) | ferritic weld metal near its DBT, so $K_{Ic}$ may be lower |
| **Variable-amplitude storm spectrum** | needs rainflow + Miner, or block-by-block Paris; overloads |
| Marine growth, wave slamming | extra loads |

**Mitigation:** grind or TIG-dress weld toes; hammer or shot peen (compressive residual stress); post-weld heat treatment; coatings plus a properly controlled CP potential; a tougher, low-hydrogen weld consumable; more frequent NDT (ultrasonic, ACFM); repair by grinding out and re-welding.

---

### B2 - Aluminium, magnesium and composites

#### (i) Microstructural features in wrought Al [8]

See [[FEEG2005 Exam 2013-14 Solutions]] B2(ii): grain size and shape (working + recrystallisation, dispersoids); solute in solution; **precipitates** by solution treating, quenching and ageing (coherent → sheared, incoherent → Orowan; peak aged T6); dislocation density (cold work); texture; closure of casting defects. Each is linked to strength (Hall-Petch, solid solution, precipitation, work hardening) and to toughness and fatigue (fewer defects, fine grains).

#### (ii) When to choose Mg over Al [3]

Mg is about 35 % less dense (1.74 vs 2.70 g/cm³) but has lower stiffness (~45 GPa), lower strength, poorer corrosion resistance and poor room-temperature formability (HCP). So choose Mg where **mass is critical but loads are modest** and the part can be **cast** (thin-walled die castings): gearbox and transmission housings, steering wheels and columns, seat frames, wheels, laptop, camera and phone cases, helicopter gearbox casings. The environment should be dry or protected.

#### (iii) MMCs vs PMCs [5]

| MMC advantages | MMC disadvantages |
|---|---|
| higher service temperature (no polymer $T_g$ limit) | higher density than PMCs |
| better transverse, shear and compressive properties (strong metal matrix) | difficult, expensive high-temperature processing (powder, diffusion bonding, squeeze casting) |
| higher toughness and impact resistance, ductile matrix | fibre-matrix reactions |
| no moisture uptake; fire resistant; conductive (lightning) | lower ductility than the unreinforced metal |
| wear resistance, tailored thermal expansion and conductivity | less mature data, joining and repair; cost |

#### (iv) Dinghy keel: $V_f$ for $E\ge63$ GPa and $\sigma\ge1.45$ GPa [5]

$V_f=(P_{req}-P_m)/(P_f-P_m)$, epoxy $E_m=3.1$ GPa, $\sigma_m=0.07$ GPa:

| Fibre | $V_f$ (stiffness) | $V_f$ (strength) | **Required $V_f$** |
|---|---:|---:|---:|
| Aramid (124, 3.5) | $\frac{63-3.1}{124-3.1}=0.495$ | $\frac{1.45-0.07}{3.5-0.07}=0.402$ | **0.50** |
| Glass (72, 3.5) | $\frac{59.9}{68.9}=0.869$ | 0.402 | **0.87**: impractical |
| Carbon (325, 3.8) | $\frac{59.9}{321.9}=0.186$ | $\frac{1.38}{3.73}=0.370$ | **0.37** |

#### (v) Choice, and reducing anisotropy [4]

**Carbon/epoxy**: the lowest $V_f$ (0.37, easily manufactured), the lightest and stiffest keel, and no corrosion. Glass is impossible (needs 87 %). Aramid is feasible (50 %) but has poor compressive strength, which matters in a keel under bending (one face is in compression), and it absorbs moisture. Carbon costs more, but a keel is small. Watch galvanic coupling with any metal fittings in seawater.

**Less anisotropic:** add ±45° plies (torsion and shear from side loads), a 0/90 woven fabric, or a quasi-isotropic symmetric lay-up. That needs a slightly higher $V_f$ to keep 63 GPa along the keel.

---

### B3 - Steels and creep

#### (i) Roles of Ni and Cr in stainless steel [5]

See [[FEEG2005 Exam 2013-14 Solutions]] B3(ii).

- **Cr > 12 %**: a self-healing, coherent $\mathrm{Cr_2O_3}$ passive film (corrosion and oxidation resistance); a ferrite stabiliser and carbide former.
- **Ni**: an austenite stabiliser, giving FCC at room temperature: tough, no DBT (cryogenic use), ductile, formable, weldable, non-magnetic; improves corrosion resistance in reducing acids.

#### (ii) Quench then temper [5]

See [[SESA2028 Materials Tutorial MT4 - Alloy Design Solutions]] Q3: austenite → (fast quench) → BCT martensite with trapped C, which is hard and brittle → (temper) → fine carbides, giving tough tempered martensite.

#### (iii) Grain-boundary attack after slow cooling [5]

Sensitisation: $\mathrm{Cr_{23}C_6}$ on the boundaries leaves a Cr-depleted zone (< 12 %) that cannot passivate. A small anode against large passive grains gives intergranular attack. Prevent it with rapid cooling or a solution anneal and quench, low-C (L) grades, or Ti/Nb stabilisation. See [[Sensitisation and Weld Decay]].

#### (iv) Alloy 738, 300 MPa at 785 °C [5]

From Fig. Q3B, 300 MPa gives $P\approx25.0$ (×10³). With $P=(T+273)(20+\log t_r)\times10^{-3}$:

$$
25.0=1.058(20+\log t_r)\;\Rightarrow\;\log t_r=\frac{25.0}{1.058}-20=3.629,\qquad t_r=\boxed{4261\ \text{h}}.
$$

**The lecturer deducts a mark for no safety factor.** With SF 2, operate for about **2,100 h** before inspection or replacement. ±0.2 on the read-off gives about 2,800-6,600 h.

#### (v) Creep mechanisms and optimising a Ni blade [5]

This is identical to MT5 Q1; see [[SESA2028 Materials Tutorial MT5 - High Temperature Materials Solutions]].
