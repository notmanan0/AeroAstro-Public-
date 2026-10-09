---
title: "FEEG2005 Exam 2014-15 Solutions"
aliases: ["FEEG2005 Exam 2014-15 Materials Solutions", "FEEG2005 Exam 2014-15 Structures Solutions"]
module: "SESA2028 Aerospace Materials & Structures"
type: exam-solution
year: "2014-15"
streams: ["Materials", "Structures"]
tags: [sesa2028, feeg2005, exam-solutions, materials, structures]
status: complete
parent: ["[[SESA2028 Past Paper Map]]"]
sources: ["03 - Exams & Past Papers/FEEG2005-201415-02-FEEG2005W1.pdf"]
---

# FEEG2005 Exam 2014-15 Solutions

> These are independent worked solutions, not an official mark scheme. Materials and structures are kept together in the order used by the paper.

## Structures

### A1 - Shear flow and shear centre

The section is symmetric about the $z$ axis, hence $I_{yz}=0$ and the shear centre lies on that axis. With $b=100$ mm, $t=10$ mm,

$$
I_z=\frac{t(2b)^3}{12}+\frac{tb^3}{12}+\frac{(2b)t^3}{12}
=\boxed{7.51\times10^6\ \mathrm{mm^4}}.
$$

For $Q_y=10$ kN and coordinates $s_1,s_2$ measured upward from the lower free edges,

$$
\tau_1(s_1)=\frac{Q_y}{I_z}\left(bs_1-\frac{s_1^2}{2}\right),
\quad0\le s_1\le2b,
$$

$$
\tau_2(s_2)=\frac{Q_y}{I_z}\left(\frac b2s_2-\frac{s_2^2}{2}\right),
\quad0\le s_2\le b.
$$

Both are parabolic and zero at their free ends. The maxima occur at $s_1=b$ and $s_2=b/2$:

$$
\tau_{1,max}=6.65\ \mathrm{MPa},\qquad
\tau_{2,max}=1.66\ \mathrm{MPa}.
$$

Integrating the flows along each web gives approximately

$$
V_1=8.87\ \mathrm{kN},\qquad V_2=1.11\ \mathrm{kN}.
$$

Moment equilibrium about the left web gives

$$
Q_y e=V_2(2b),
$$

so the shear centre is

$$
\boxed{e\approx22.2\ \mathrm{mm}}
$$

to the right of the left-web centreline. Small differences result from retaining or neglecting the flange's own $t^3$ contribution consistently.

### A2 - Shrink-fit contact pressure

This is the same geometry as Green Book Tutorial 5 Q3.

**Geometry.** Inner tube: $a=25$ mm, $c=50$ mm (100 mm OD, 25 mm wall). Outer tube: $c=50$ mm, $b=75$ mm (100 mm ID, 25 mm wall). Radial interference $\delta=0.01$ mm; $E=208$ GPa for both tubes.

**Hoop stresses at the interface** (from Lamé, with contact pressure $p$):

- Inner tube, external pressure $p$:
$$
\sigma_{\theta,i}(c)=-p\,\frac{c^2+a^2}{c^2-a^2}=-p\,\frac{2500+625}{2500-625}=-1.667\,p.
$$
- Outer tube, internal pressure $p$:
$$
\sigma_{\theta,o}(c)=+p\,\frac{b^2+c^2}{b^2-c^2}=p\,\frac{5625+2500}{5625-2500}=+2.600\,p.
$$

**Compatibility.** The interference is taken up by the outer bore expanding plus the inner surface contracting. With $u=\frac cE(\sigma_\theta-\nu\sigma_r)$ and $\sigma_r=-p$ on both sides, the $\nu$ terms cancel for identical materials:

$$
\delta=u_o-u_i=\frac cE\left(\sigma_{\theta,o}-\sigma_{\theta,i}\right)
=\frac{50}{208\,000}(2.600+1.667)\,p=1.0256\times10^{-3}\,p\ \ [\text{mm, with }p\text{ in MPa}].
$$

$$
\boxed{p=\frac{0.01}{1.0256\times10^{-3}}=9.75\ \mathrm{MPa}}.
$$

**Check with the closed form** for one material: $\delta=\dfrac{2pc^3(b^2-a^2)}{E(c^2-a^2)(b^2-c^2)}=\dfrac{2p(125\,000)(5000)}{208\,000(1875)(3125)}=1.0256\times10^{-3}p$. ✓

See [[Shrink Fit]].

### A3 - Double-cell torsion

For any single cell,

$$
T=2A_mq,\qquad \tau=q/t,\qquad
\frac{d\phi}{dx}=\frac1{2A_mG}\oint\frac q t\,ds.
$$

For the two-cell section, let $q_1$ circulate in the semicircle and $q_2$ in the square. The common wall carries $q_1-q_2$. With

$$
A_1=\frac\pi2\ \mathrm{m^2},\qquad A_2=4\ \mathrm{m^2},\qquad t=0.01\ \mathrm m,
$$

torque equilibrium and equal twist give

$$
2A_1q_1+2A_2q_2=6\times10^6,
$$

$$
\frac{q_1(\pi+2)-2q_2}{2A_1}
=\frac{8q_2-2q_1}{2A_2}.
$$

Solving,

$$
q_1=4.853\times10^5\ \mathrm{N/m},\qquad
q_2=5.594\times10^5\ \mathrm{N/m}.
$$

Thus

$$
\boxed{\tau_{semicircle}=48.5\ \mathrm{MPa}},
$$

$$
\boxed{\tau_{square\ perimeter}=55.9\ \mathrm{MPa}},
$$

and the common wall carries

$$
\boxed{\tau_{common}=(q_1-q_2)/t=-7.41\ \mathrm{MPa}}.
$$

After removing the common wall, the combined area is $A=4+\pi/2$, so the single circulating flow gives

$$
\boxed{\tau=\frac{T}{2At}=53.85\ \mathrm{MPa}}.
$$

## Materials

### B1 - Pressure vessel: fatigue, service problems, Larson-Miller

#### (i) Miner's rule (total life) vs Paris law [5]

This is identical to MT2 Q1; see [[SESA2028 Materials Tutorial MT2 - Fatigue Lifing Solutions]]. Key points:

- Miner: $\sum n_i/N_i=1$ from S-N data; initiation-dominated, sensitive to surface finish, linear and order-independent damage.
- Paris: $da/dN=A\Delta K^m$ integrated from a known $a_i$ to $a_c$; growth-dominated; sets inspection intervals.

#### (ii) Remaining pressurisation cycles [10]

$a_i=4$ mm; 10-150 MPa; $K_{Ic}=65$; $A=1.58\times10^{-10}$; $m=3.5$; $Q=1.2$.

$$
\Delta\sigma=140\ \text{MPa},\qquad a_c=\frac1\pi\left(\frac{65}{180}\right)^2=41.5\ \text{mm},
$$

$$
N_f=\frac{0.04151^{-0.75}-0.004^{-0.75}}{(-0.75)(1.58\times10^{-10})(297.8)^{3.5}}=\frac{10.87-62.87}{-0.0540}=\boxed{963\ \text{cycles}}.
$$

**Recommend about 480 cycles** (SF 2) before re-inspection or repair. $a_c$ may exceed the wall thickness, in which case **leak-before-break** or net-section yield governs; state this.

#### (iii) Heated and held at temperature: other problems [4]

- **Creep** during the hot, constant-pressure hold: time-dependent strain and cavitation.
- **Creep-fatigue interaction**: hold periods (dwell) add time-dependent damage per cycle, so crack growth is faster per cycle at low frequency.
- **Oxidation** and **oxidation-assisted crack growth**: intergranular oxides at the crack tip.
- **Thermal stresses and thermal fatigue** from heat-up and cool-down gradients.
- Temperature-dependent $K_{Ic}$ (a DBT on cool-down for a ferritic steel) and changed $A$, $m$.
- Microstructural degradation (tempering, carbide coarsening).

**Effect:** room-temperature Paris data are unconservative. Use high-temperature, frequency- and dwell-dependent crack-growth data, add a creep damage term (Miner-type sum), and shorten inspection intervals.

#### (iv) Larson-Miller, Ni superalloy, 500 MPa at 700 °C [6]

$\log_{10}500=2.699$, which reads to **LMP ≈ 26.4×10³** on Fig. QB1 (the lecturer's read). With $T=973$ K and $C=20$:

$$
\log t_r=\frac{26\,400}{973}-20=7.13,\qquad t_r=\boxed{1.35\times10^7\ \text{h}}.
$$

**Apply a safety factor** and note the sensitivity: ±200 on the LMP read changes $t_r$ from about $8.5\times10^6$ to $2.2\times10^7$ h. The life is also well beyond any test duration, so this is an extrapolation.

---

### B2 - Lightweighting and titanium

#### (i) Two lightweighting applications [4]

1. **Aircraft wing and fuselage structure**: mass drives fuel burn, CO₂, payload and range. It needs high specific stiffness and strength, fatigue and damage tolerance, and corrosion resistance.
2. **Automotive body and chassis (EVs)**: battery mass must be offset for range, and mass reduces handling and braking performance. Cost, high volume, crashworthiness and recyclability dominate.

(Alternatives: high-performance boats, rotating aero-engine parts where centrifugal load ∝ $\rho$, and space structures where launch cost per kg is huge.)

#### (ii) Pros and cons of the Table QB2 materials for one application (aircraft wing) [7]

| | $\sigma/\rho$ | $E/\rho$ | Advantages | Disadvantages |
|---|---:|---:|---|---|
| CFRP | 882 | 129 | best specific stiffness and strength; fatigue resistant; no corrosion | anisotropic; poor compressive and impact (BVID) performance; hard to inspect, repair and join; cost; conservative certification; lightning (low conductivity) |
| GFRP | 450 | 20.5 | cheap, tough fibre, good specific strength | low stiffness (20 GPa·cm³/g); moisture |
| Steel | 128 | 26.5 | cheap, tough, high $E$, easy to join | heavy: poor specific strength; corrosion |
| Al alloy | 196 | 25.4 | established, damage tolerant (2xxx), inspectable, conductive, cheap to manufacture | fatigue and corrosion; lower strength |
| Ti alloy | 244 | 26.7 | high specific strength, corrosion, temperature | expensive, hard to machine; similar $E/\rho$ to Al |

**Recommendation:** CFRP for the wing box and skins (as on the 787 and A350), with Al or Ti at fittings and joints. Al-Li or 2xxx/7xxx remain competitive where damage tolerance, inspection and cost matter.

#### (ii) [second part] The three Ti alloy classes; best fatigue resistance [9]

Same as MT4 Q2; see [[SESA2028 Materials Tutorial MT4 - Alloy Design Solutions]] and [[Titanium Alloy Classes]].

- $\alpha$ (Al, O, Sn: solid solution; creep resistant, weldable).
- $\alpha+\beta$ (Ti-6Al-4V: microstructure set by heat treatment; lamellar resists growth, equiaxed resists initiation).
- $\beta$ (V, Mo: solution treat, quench, age; highest strength).
- **Best fatigue: $\alpha+\beta$**, because the microstructure can be tailored (bimodal).

#### (iii) 55 % carbon / epoxy: $E_L$, $E_T$ [5]

$$
E_L=0.55(325)+0.45(3.1)=\boxed{180\ \text{GPa}},\qquad
E_T=\left(\frac{0.55}{325}+\frac{0.45}{3.1}\right)^{-1}=\boxed{6.81\ \text{GPa}}.
$$

Anisotropy ratio about 26. **Less anisotropic:** 0/90 or quasi-isotropic (0/±45/90) symmetric lay-ups, woven fabrics, or chopped fibre. This gives up peak axial stiffness for balance.

---

### B3 - Steels and superalloys

#### (i) Factors controlling martensite formation (TTT) [5]

Sketch a eutectoid TTT diagram with the start and finish curves, the nose (~540 °C, ~1 s), pearlite and bainite fields, and horizontal $M_s$ and $M_f$ lines ([[TTT and CCT Diagrams]]).

- The **cooling rate** must exceed the critical rate so the curve misses the nose; otherwise diffusional pearlite or bainite forms.
- It must cool **below $M_f$** for complete transformation. Martensite is athermal: the amount depends on temperature, not time.
- **Composition**: C raises martensite hardness and lowers $M_s$; alloying (Mn, Cr, Mo, Ni) shifts the nose right, so martensite forms at slower rates (hardenability).
- **Austenite grain size**: coarser grains mean fewer nucleation sites, so the curves shift right.
- **Section size and quench medium** set the actual cooling rate (Jominy equivalence).

#### (ii) Why martensite is hard and brittle, and how to exploit it [6]

**Hard and brittle:** diffusionless shear traps C in a strained **BCT** lattice (solid-solution strain) with a **very high dislocation density** and fine laths, so dislocations cannot move. Quench also leaves residual stress.

**Exploiting it:**

- **Temper** to get tempered martensite: fine carbides, keeping most of the strength with much better toughness (Q&T 4340 landing gear, shafts, springs).
- **Surface hardening** (carburise, nitride, induction or flame harden): a hard wear- and fatigue-resistant **martensitic case** on a **tough core**, which arrests cracks (gears, cams).
- **Alloy for hardenability** so large sections through-harden with a gentle **oil** quench (less distortion and cracking).
- Secondary-hardening tool steels (Mo, V, W carbides) for cutting tools.

#### (iii) Ni and Cr in steel [4]

- **Ni** stabilises austenite and **lowers $M_s$**. It shifts the transformation curves right (more hardenable, so martensite at slower rates in low-alloy steels). At high levels (> 8 % with 18 % Cr) it suppresses martensite altogether, giving fully austenitic stainless steel that stays FCC.
- **Cr**: above 12 %, a passive $\mathrm{Cr_2O_3}$ film gives corrosion and oxidation resistance. It is also a carbide former (hardenability, tempering resistance, wear) and a ferrite stabiliser.

#### (iv) Ni superalloys: elements, microstructure, why for turbines [5]

**$\gamma$** (FCC Ni: Co, Cr, Mo, W solid solution) + a high fraction of coherent **$\gamma'$ $\mathrm{Ni_3(Al,Ti)}$** cuboids. Cr and Al give oxidation and corrosion resistance ($\mathrm{Cr_2O_3}$, $\mathrm{Al_2O_3}$). W, Mo and Re raise $T_m$ and slow diffusion. C, B and Zr strengthen boundaries in polycrystals.

**Why for discs and blades:** strength is retained to about 0.8 $T_m$, because $\gamma'$ does not coarsen and its strength rises with temperature. They have excellent creep, oxidation and hot-corrosion resistance, FCC toughness and fatigue resistance (discs), and can be cast as DS or single-crystal blades. See [[Gamma Prime Strengthening]].

#### (v) Coatings and single crystals [5]

Same as 2013-14 B3(v): a YSZ TBC on an aluminide or MCrAlY bond coat (TGO), with cooling. Single crystals remove the grain boundaries that slide, cavitate and oxidise, and allow a higher solution heat treatment. See [[FEEG2005 Exam 2013-14 Solutions]] and [[Thermal Barrier Coatings]].
