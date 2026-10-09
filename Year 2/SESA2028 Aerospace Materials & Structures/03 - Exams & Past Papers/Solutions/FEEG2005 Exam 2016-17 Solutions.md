---
title: "FEEG2005 Exam 2016-17 Solutions"
aliases: ["FEEG2005 Exam 2016-17 Materials Solutions", "FEEG2005 Exam 2016-17 Structures Solutions"]
module: "SESA2028 Aerospace Materials & Structures"
type: exam-solution
year: "2016-17"
streams: ["Materials", "Structures"]
tags: [sesa2028, feeg2005, exam-solutions, materials, structures]
status: complete
parent: ["[[SESA2028 Past Paper Map]]"]
sources: ["03 - Exams & Past Papers/FEEG2005-201617-02-FEEG2005W1.pdf"]
---

# FEEG2005 Exam 2016-17 Solutions

> These are independent worked solutions, not an official mark scheme. Materials and structures are kept together in the order used by the paper.

## Materials

### A1 - Composites and high-temperature materials

#### (i) CMCs vs MMCs [5]

| CMC advantages over MMC | CMC disadvantages |
|---|---|
| much higher temperature capability (> 1000 °C) | very low toughness even when reinforced; brittle, flaw-sensitive, statistical strength |
| lower density (SiC ~3.1 vs Ti ~4.4 g/cm³) | strength data often compressive; poor tensile and impact performance |
| higher stiffness, retained at temperature | slow, expensive processing (sintering, CVI, PIP cycles); porosity |
| chemical inertness; oxidation and creep resistance of the matrix | fibre-matrix interfaces are oxidation paths (a weak interface is needed for pull-out) |
| | hard to machine, join, inspect and certify |

See [[MMC vs CMC]].

#### (ii) $\mathrm{Al_2O_3}$-matrix hoop: fibre volume fraction [5]

Requirement: $E\ge375$ GPa and strength ≥ 3.6 (the table's strength column is printed in "MPa" but is clearly GPa; use the same units as the table). Matrix $\mathrm{Al_2O_3}$: 300 GPa, 1.4.

| Fibre ($E$, $\sigma$) | $V_f$ for $E$ | $V_f$ for $\sigma$ | Required $V_f$ |
|---|---:|---:|---:|
| WC (600, 5.5) | $\frac{75}{300}=0.25$ | $\frac{2.2}{4.1}=0.537$ | **0.54** |
| TiC (410, 7.5) | $\frac{75}{110}=0.68$ | $\frac{2.2}{6.1}=0.36$ | **0.68** |
| C (550, 4.8) | $\frac{75}{250}=0.30$ | $\frac{2.2}{3.4}=0.65$ | **0.65** |

**Choice: WC**, which meets both requirements at the lowest fraction (0.54), within practical manufacturing limits. TiC (0.68) and C (0.65) are at or beyond what can be made.

**Other data needed:**

- **Density**: WC is about 15.6 g/cm³, very heavy for a spinning hoop (centrifugal stress ∝ $\rho$), which may rule it out.
- Fracture toughness and fibre-matrix interface behaviour.
- Thermal-expansion mismatch.
- **Oxidation**: C fibres oxidise above about 400 °C in air.
- Chemical compatibility and reactions during sintering; creep; cost and availability; manufacturability of continuous fibres.

#### (iii) Ni superalloy blade with a TBC: alloying and manufacture [9]

**Alloying:**

- FCC **$\gamma$** Ni matrix (tough, no DBT), solid-solution strengthened by Co, Mo, **W, Re** (which also slow diffusion, so better creep).
- **Al + Ti (Ta)** give about 60-70 % coherent, ordered **$\gamma'$ $\mathrm{Ni_3(Al,Ti)}$**, which resists coarsening and gets stronger with temperature. It blocks dislocation glide and climb.
- **Cr** and Al give $\mathrm{Cr_2O_3}$ / $\mathrm{Al_2O_3}$ oxidation and hot-corrosion resistance.
- In SX alloys, remove the boundary strengtheners (C, B, Zr), which lower the melting point.

**Manufacturing:**

1. **Investment casting** around ceramic cores to form internal cooling passages.
2. **Directional solidification** with a **spiral grain selector**, giving a **single crystal** with ⟨001⟩ along the blade: no grain boundaries to slide, cavitate or oxidise; low axial modulus for thermal fatigue.
3. **Solution heat treat + age** to optimise $\gamma'$ size and fraction.
4. Machine the fir-tree root; drill film-cooling holes (laser or EDM).
5. **Coat**: aluminide (CVD or pack) or MCrAlY bond coat, then a **YSZ top coat by EB-PVD** (columnar, strain tolerant). The bond coat grows a protective **$\mathrm{Al_2O_3}$ TGO**.

**Why it performs well:** $\gamma'$ + solid solution + no boundaries give **creep** resistance. Cr, Al, the TGO and bond coat give **oxidation** resistance. The TBC + cooling lower the metal temperature by about 100-150 °C, which slows diffusion, creep and oxidation (or allows a hotter gas for efficiency). The FCC matrix and ⟨001⟩ orientation help thermal-mechanical fatigue.

#### (iv) Ti alloy at 600 °C: varying stress (creep Miner) [6]

Data: 200 MPa 15,625 h; 300 MPa 1,372 h; 400 MPa 244 h; 500 MPa 64 h; 600 MPa 21.4 h.

**Method:** Miner's rule for creep, $\sum t_i/t_{r,i}=1$. Interpolate on a **log-log** plot of $t_r$ against $\sigma$ (the data fit $t_r=1.006\times10^{18}\sigma^{-6.00}$ exactly).

- 325 MPa (between 300 and 400): $t_r=848.6$ h, so $500/848.6=0.589$.
- 250 MPa (between 200 and 300): $t_r=4096$ h, so $1100/4096=0.269$.
- Used: $0.858$; remaining fraction: $0.142$.
- 650 MPa (extrapolated beyond 600): $t_r=1.006\times10^{18}\times650^{-6}=13.2$ h.

$$
t_{remaining}=0.142\times13.2=\boxed{1.9\ \text{h}}\quad(\text{SF 2: about 1 h}).
$$

**Comment:** this is an **extrapolation** beyond the data (650 > 600 MPa), and 650 MPa is probably close to yield at 600 °C, so the mechanism may change. In practice the blade should be retired, not run at 650 MPa.

![[Figures/materials_creep_stress_powerlaw_fits.png]]

---

### A2 - Steels and a failed mixer shaft

#### (i) 0.25 % C quench + temper, with a TTT diagram [5]

Sketch a **hypo-eutectoid** TTT diagram: an extra pro-eutectoid **ferrite** start curve above the pearlite curve, the nose (~550 °C) further **left** than eutectoid (a low-C plain steel has **low hardenability**), and $M_s$ higher (~400 °C) because the C is low. Draw the quench curve missing the nose.

- Austenitise (single-phase $\gamma$ above $A_3$, ~850 °C), then a **very fast water quench** past the nose, giving **lath martensite** (BCT, trapped C, high dislocation density). It is hard and brittle, though less hard than 0.4 % C martensite.
- **Temper at 580 °C for 1 h**: C diffuses into fine carbides; the laths recover. Strength falls somewhat; toughness and ductility rise markedly.
- For thick sections, a 0.25 % C plain steel may not through-harden (the core forms ferrite and bainite). Alloying (Cr, Mo, Ni) would help.

#### (ii) Ni, Cr and slow-cooling corrosion [8]

- **Ni**: stabilises $\gamma$ to room temperature (with ≥ 8 %), lowers $M_s$, and moves the curves right. It gives a fully **austenitic** stainless steel: FCC, tough, ductile, no DBT, non-magnetic, not hardenable by quenching.
- **Cr (> 12 %)**: a self-healing passive $\mathrm{Cr_2O_3}$ film (blocks ionic and electronic transport); a carbide former and ferrite stabiliser.
- **Slow cooling**: **sensitisation**. $\mathrm{Cr_{23}C_6}$ on grain boundaries at ~500-800 °C leaves Cr-depleted (< 12 %) boundary zones, which become active anodes next to passive grains: intergranular attack (**weld decay** in the HAZ). Prevent it with fast cooling or solution anneal + quench, low C (304L/316L), or Ti/Nb stabilisation. See [[Sensitisation and Weld Decay]].

#### (iii) Mixer shaft after a blade detached: loading and fracture sketch [4]

**Loading:** losing a blade leaves the rotor **unbalanced**. The out-of-balance and asymmetric fluid forces bend the shaft, and as it rotates each point on its surface passes through the tension side and then the compression side **once per revolution**: **rotating bending** (with the severe vibration recorded). Only 48 h passed before failure, which means **high-stress, high-frequency fatigue**.

**Expected fracture surface (sketch):**

- **Multiple origins round the circumference** (high stress, and perhaps a stress concentration at a shoulder or keyway), with **ratchet marks** between them.
- **Fatigue zones** grow inwards from the whole periphery: smooth, with a few **beach marks** (vibration changes), and crack fronts curving inwards.
- **Final fracture zone**: rough, with **shear lips**, **offset from the centre and rotated against the direction of rotation** (the rotating-bending signature). It is **relatively large** (high nominal stress: final area ≈ $\sigma_{max}/\sigma_{UTS}$) and, with multiple origins, roughly central.
- The size and shape of each region tell you the stress level (large final zone means high stress), the loading mode (offset and rotated means rotating bending), and the number of origins (the stress concentration).

See [[Fatigue Fracture Surface Features]].

#### (iv) Second mixer shaft, crack 1.5 mm [8]

$\Delta\sigma=295$ MPa; $a_c=7.43$ mm; $A=2.67\times10^{-10}$; $m=2.5$; $Q=1.2$.

$$
N_f=\frac{0.00743^{-0.25}-0.0015^{-0.25}}{(-0.25)(2.67\times10^{-10})(627.4)^{2.5}}=\frac{3.406-5.081}{-6.583\times10^{-4}}=\boxed{2545\ \text{revolutions}}.
$$

With SF 2, about 1,270 revolutions: minutes to hours of running. **Replace the shaft now**, rebalance the blades, and check the surface finish and stress concentrations. (MT2 Q5 uses $A=2.67\times10^{-11}$, giving 25,450 revolutions; see [[SESA2028 Materials Tutorial MT2 - Fatigue Lifing Solutions]].)

## Structures

### B1 - Unsymmetrical bending and shear centre

#### (i) Positive bending moments

On a cut face whose outward normal is (+x), the positive moments follow the right-hand rule: $M_y$ curls from (+z) towards (+x), and $M_z$ curls from (+x) towards (+y). A good exam sketch shows the (+x,+y,+z) triad on the cut face before adding the curved arrows.

#### (ii) Asymmetric channel under $M_z=2.0$ kNm

Treat the section as three non-overlapping rectangles: the $20\times150$ mm web, the $40\times20$ mm top extension and the $100\times20$ mm bottom extension. Measured from the outer top-left corner,

$$
A=5800\ \mathrm{mm^2},\qquad
\bar z=34.83\ \mathrm{mm},\qquad
\bar y=88.45\ \mathrm{mm}.
$$

The centroidal properties are

$$
I_z=16.499\times10^6\ \mathrm{mm^4},\quad
I_y=6.218\times10^6\ \mathrm{mm^4},\quad
I_{yz}=4.303\times10^6\ \mathrm{mm^4}.
$$

For $M_y=0$,

$$
\sigma_x=\frac{M_z(I_{yz}z-I_y y)}{I_yI_z-I_{yz}^2}.
$$

The neutral axis therefore satisfies

$$
\boxed{y=\frac{I_{yz}}{I_y}z=0.692z},
$$

where $y,z$ are measured from the centroid. Evaluating the linear field at every boundary vertex gives the two governing corners:

$$
\boxed{\sigma_{\max,t}\simeq+15.7\ \mathrm{MPa}}
$$

at the outer top-right corner, and

$$
\boxed{\sigma_{\max,c}\simeq-12.7\ \mathrm{MPa}}
$$

at the outer bottom-left corner. The fixed-end section is the critical section along the beam.

#### (iii) Shear centre of the inverted channel

Symmetry puts the shear centre on the vertical centreline. Using the median-line model ($t=20$ mm, top median length $130$ mm and leg median length $40$ mm), apply a unit horizontal shear and integrate

$$
q(s)=\frac{V_zQ_z(s)}{I_y},\qquad
M_x=\int q(s)(y\,dz-z\,dy).
$$

The wall-flow torque corresponds to an eccentricity of about (23.4) mm above the centroid. Since the centroid is (20.43) mm below the outer top face,

$$
\boxed{S\text{ lies on the symmetry axis about }3.0\ \mathrm{mm}
\text{ above the outer top face}.}
$$

The location outside the material is not an error; it is common for open channels.

### B2 - Beam with an internal hinge

The left span has a pin at A and an internal hinge at B. Taking moments about A for span AB gives the hinge force on the left span as (2.5) kN downward; hence

$$
\boxed{R_A=17.5\ \mathrm{kN}\ \text{upward}}.
$$

Joint equilibrium transfers (17.5) kN downward to the right-hand cantilever, so

$$
\boxed{R_C=17.5\ \mathrm{kN}\ \text{upward}},\qquad
\boxed{M_C=70.0\ \mathrm{kNm}}.
$$

The right span has flexural rigidity (2EI), where

$$
EI=(200\ \mathrm{GPa})(200\times10^6\ \mathrm{mm^4})
=40{,}000\ \mathrm{kNm^2}.
$$

Castigliano's theorem for a cantilever with tip force $P=17.5$ kN and length (4) m gives

$$
\delta_B=\frac{PL^3}{3(2EI)}
=\boxed{4.67\ \mathrm{mm}\ \text{downward}},
$$

and the rotation immediately to the right of the hinge is

$$
\theta_{B^+}=\frac{PL^2}{2(2EI)}
=\boxed{1.75\times10^{-3}\ \mathrm{rad}}.
$$

The slopes on the two sides of an ideal internal hinge need not be equal; only its translation is common to both members.

### What this paper is testing

- Do not use $My/I$ on an asymmetric section until $I_{yz}$ has been checked.
- A shear centre may be outside the section.
- An internal hinge kills bending moment, not shear or translation.

### Linked notes

- [[SESA2028 S1 - Section Properties and Unsymmetrical Bending]]
- [[SESA2028 S3 - Shear Flow and Shear Centre]]
- [[SESA2028 S8 - Virtual Work and Castigliano Theorems]]
