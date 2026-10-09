---
title: "FEEG2005 Exam 2021-22 Solutions"
aliases: ["FEEG2005 Exam 2021-22 Materials Solutions", "FEEG2005 Exam 2021-22 Structures Solutions"]
module: "SESA2028 Aerospace Materials & Structures"
type: exam-solution
year: "2021-22"
streams: ["Materials", "Structures"]
tags: [sesa2028, feeg2005, exam-solutions, materials, structures]
status: complete
parent: ["[[SESA2028 Past Paper Map]]"]
sources: ["03 - Exams & Past Papers/FEEG2005-202122-02-FEEG2005.pdf"]
---

# FEEG2005 Exam 2021-22 Solutions

> These are independent worked solutions, not an official mark scheme. Materials and structures are kept together in the order used by the paper.

## Materials

### MQ1 - Turbine blades: Ni superalloy vs CMC

#### (a)(i) Service requirements and key properties [4]

The turbine blade sits in the hottest gas (> 1200 °C), spins at high speed and is cycled every flight. Required properties:

1. **Creep resistance** at high temperature and sustained **centrifugal** stress (limits blade stretch and tip clearance, and rupture).
2. **Oxidation and hot-corrosion resistance**: a protective, adherent scale; resistance to sulphidation from fuel and salt.
3. **Fatigue**: **LCF / thermo-mechanical fatigue** from start-stop thermal gradients, and **HCF** from vibration. Crack-growth resistance at the fir-tree root.
4. **High melting point and strength retained at temperature**, together with **low density** (centrifugal load ∝ $\rho$) and **toughness / impact resistance** (debris). Thermal conductivity and expansion matter for cooling and thermal stress.

#### (a)(ii) Manufacturing challenges and property benefits; recommendation [8]

| | Ni superalloy (SX, e.g. CMSX-4) + TBC | SiC/SiC CMC |
|---|---|---|
| **Property benefits** | coherent $\gamma'$ keeps strength to ~1100 °C; creep resistant (no boundaries, W/Re slow diffusion); FCC, **tough** and damage tolerant; mature lifing data; oxidation resistant with Al/Cr and coatings | ~1/3 the density (~3 vs 8.5 g/cm³), which cuts blade *and* disc loads; can run ~150-200 °C hotter with less cooling air, giving higher efficiency; high stiffness retained |
| **Limitations** | temperature ceiling near the $\gamma'$ solvus and incipient melting, so it relies heavily on cooling air (efficiency loss) and TBCs; heavy | **low toughness** (~3-5 MPa√m even with fibres); FOD vulnerability; interface oxidation and water-vapour recession (needs environmental barrier coatings); thermal-expansion mismatch at the metal disc attachment |
| **Manufacturing** | complex **investment casting** with ceramic cores, **directional solidification + grain selector** (stray-grain defects, low yield), solution + age, laser-drilled film-cooling holes, bond coat + EB-PVD YSZ; expensive but mature | fibre weaving and preforming, **CVI or PIP** (slow, many cycles, residual porosity), machining a hard brittle material, EBC coating; very expensive; difficult NDT and certification |

**Recommendation:** for current rotating HP turbine blades, **a cooled single-crystal Ni superalloy with a TBC**. It combines creep strength with the toughness and damage tolerance needed for a rotating, safety-critical part, and has a mature supply chain and lifing base. Introduce CMCs first in static or low-stress parts (shrouds, vanes, combustor liners, LP blades), where their temperature and weight benefits outweigh the low toughness.

#### (b) Ni superalloy vs stainless steel, and the role of each element [5]

**Advantages of Ni superalloys** in the hot section: they keep strength and creep resistance to about 0.8-0.9 $T_m$ (about 1000-1100 °C), whereas austenitic stainless is limited to about 600 °C. The difference is precipitation strengthening by stable $\gamma'$, plus better oxidation and corrosion resistance and no sensitisation-driven degradation.

| Element | In the Ni superalloy | In stainless steel |
|---|---|---|
| Ni | the base: FCC $\gamma$ matrix (tough, no DBT) | $\gamma$ stabiliser (austenitic grades) |
| Cr | $\mathrm{Cr_2O_3}$ oxidation and hot-corrosion resistance | **> 12 %: the passive film**; carbide former (sensitisation) |
| Al | forms **$\gamma'$ $\mathrm{Ni_3Al}$** and a protective $\mathrm{Al_2O_3}$ scale | minor (ferrite stabiliser; used in some PH grades) |
| Ti, Ta, Nb | strengthen $\gamma'$ | **stabilisers**: tie up C to prevent weld decay |
| W, Mo, Re, Co | solid solution; **slow diffusion** for creep | Mo improves pitting resistance; solid solution |
| C, B, Zr | grain-boundary carbides and borides pin boundary sliding (removed in SX) | C is **harmful** (sensitisation), so it is minimised (L grades) |

#### (c) Problems welding austenitic stainless [3]

- **Sensitisation / weld decay**: the HAZ passes through about 500-800 °C, so $\mathrm{Cr_{23}C_6}$ forms and the boundaries are Cr-depleted. Use **low-C (L)** or **Ti/Nb-stabilised** grades; minimise heat input; solution anneal.
- **Hot (solidification) cracking** in fully austenitic weld metal: use fillers that give a few % δ-ferrite; keep S and P low.
- **Distortion and tensile residual stress** (high expansion, low conductivity) promote chloride **SCC**: low heat input, stress relief.

#### (d) CM247LC at 750 °C: time to 1 % strain [1 + 4]

(i) **Miner's rule** on time fractions to 1 % strain, $\sum t_i/t_{1\%,i}=1$. Interpolate the data on a log-log plot.

(ii) The data fit $t_{1\%}=1.353\times10^{18}\sigma^{-6.00}$ exactly (log-log straight line, $n=6$).

- 250 MPa (data point): $t=5530$ h, so $500/5530=0.090$.
- 210 MPa (between 190 and 250): $t=5530\,(250/210)^6=15{,}740$ h, so $5000/15740=0.318$.
- Used: $0.408$; remaining: $0.592$.
- 475 MPa (between 400 and 525): $t=330\,(400/475)^6=117.6$ h.

$$
t_{remaining}=0.592\times117.6=\boxed{69.6\ \text{h}}\ \text{before 1 \% strain}\quad(\text{SF 2: about 35 h}).
$$

**Assumptions:** linear, order-independent accumulation (primary creep at each new stress is ignored); strain accumulation equated with "life fraction"; constant temperature; no oxidation or microstructural ageing (e.g. $\gamma'$ rafting).

---

### MQ2 - Reactor pressure vessel and an EV chassis sheet

#### (a) HSLA reactor pressure vessel

Data: $K_{Ic}=73\pm3$ MPa√m; controlled thermal cycling $\Delta\sigma=350$ MPa twice a week; $a_i=1.4$ mm ± 10 %; $A=2.45\times10^{-11}$, $m=3.2$, $Q=1.2$; loss-of-coolant accident (LOCA) peak $\sigma_{max}=550$ MPa.

**(i) Safe crack depth [3].** The vessel must survive a LOCA at *any* time, so the critical crack is set by the **LOCA stress** and the **worst-case toughness** (70 MPa√m):

$$
a_c=\frac1\pi\left(\frac{70}{1.2\times550}\right)^2=\boxed{3.58\ \text{mm}}\qquad(\text{nominal }K_{Ic}=73:\ 3.89\ \text{mm}).
$$

**(ii) Remaining years [9].** Grow the crack under the normal cycling ($\Delta\sigma=350$ MPa) from $a_i$ to 3.58 mm. With $1-m/2=-0.6$:

$$
N=\frac{a_c^{-0.6}-a_i^{-0.6}}{(-0.6)(2.45\times10^{-11})(1.2\times350\sqrt\pi)^{3.2}}.
$$

Worst case ($a_i=1.54$ mm, $K_{Ic}=70$):

$$
N=\frac{29.35-48.70}{(-0.6)(2.45\times10^{-11})(1.548\times10^9)}=\frac{-19.34}{-0.02276}=850\ \text{cycles}=\frac{850}{2\times52.2}=8.1\ \text{years}.
$$

| $K_{Ic}$ \ $a_i$ | 1.26 mm | 1.40 mm | 1.54 mm |
|---|---:|---:|---:|
| 70 | 10.8 yr | 9.4 yr | **8.1 yr** |
| 73 | 11.4 yr | 10.0 yr | 8.8 yr |
| 76 | 11.9 yr | 10.5 yr | 9.3 yr |

**Recommendation:** base it on the worst case, 8.1 years, with **SF 2: keep in service for about 4 years**, then re-inspect (NDT at every scheduled outage, trending crack size).

**Justification:**

- Life is much more sensitive to $a_i$ (±10 % gives about ±15 % life) than to $K_{Ic}$, so improving NDT sizing matters most.
- $K_{Ic}$ is taken at room temperature, which is correct for a LOCA quench. But **neutron irradiation embrittlement** raises the DBT of ferritic HSLA steel over time, so $K_{Ic}$ will fall with service. That argues for even more conservatism and a surveillance programme.
- The environment (hot pressurised water) may raise $da/dN$ above the lab constants.

#### (b) EV chassis sheet: 0.7 m × 1.2 m, load along the 1.2 m length, 50 kN, $t\le4$ mm, $\Delta L\le1$ mm

**(i) Stiffness limit [1].**

$$
\varepsilon_{max}=\frac{\Delta L}{L}=\frac{1}{1200}=8.33\times10^{-4}=\frac\sigma E,\quad \sigma=\frac F{wt}
\;\Rightarrow\; t_{stiff}=\frac{F}{w\,E\,\varepsilon_{max}}=\frac{F\,L}{w\,E\,\Delta L}.
$$

**(ii) Strength limit [1].**

$$
t_{str}=\frac F{w\,(0.75\,\mathrm{UTS})}.
$$

**(iii) Compare the three systems [7].** CFRP at $V_f=0.3$ (maximum): $E=0.3(550)+0.7(3.1)=167$ GPa; UTS $=0.3(3200)+0.7(70)=1009$ MPa; $\rho=0.3(1750)+0.7(1200)=1365\ \mathrm{kg/m^3}$. Assume UD fibres along the load, isotropic Mg and Al, linear elasticity, and $w=0.7$ m.

| Material | $t_{stiff}$ (mm) | $t_{str}$ (mm) | $t$ used | ≤ 4 mm? | Mass (kg) |
|---|---:|---:|---:|:---:|---:|
| Mg alloy | 2.04 | 0.36 | 2.04 | ✓ | 3.03 |
| Al alloy | 1.22 | 0.20 | 1.22 | ✓ | 2.79 |
| **CFRP UD (30 %)** | **0.51** | 0.09 | 0.51 | ✓ | **0.59** |

**Stiffness governs** for all three. Everything meets the 4 mm limit. **UD CFRP is by far the lightest** (about 1/5 of Al). Mg is *heavier* than Al here, because its specific stiffness is slightly lower ($42/1.77=23.7$ vs $70/2.71=25.8$).

![[Figures/materials_selection_rod_and_sheet.png]]

**(iv) If the load became biaxial [4].** A UD sheet loaded **across** its fibres has $E_T=\left(\frac{0.3}{550}+\frac{0.7}{3.1}\right)^{-1}=4.4$ GPa. For the 0.7 m direction ($\varepsilon=1/700$) that needs $t\approx6.6$ mm, which **fails the 4 mm limit**. So the lay-up must change:

- a **0/90 cross-ply** gives $E\approx86$ GPa in both directions, so $t\approx1.0$ mm (governed by the 1.2 m direction) and mass about 1.15 kg. That is still about 2.4× lighter than Al (2.79 kg), because Al and Mg are isotropic and unchanged by biaxial load;
- a quasi-isotropic lay-up if shear or off-axis loads exist.

**Recommendation:** still CFRP, but cross-ply or quasi-isotropic.

**Manufacturing and other considerations:**

- Cost and cycle time for automotive volumes (RTM or compression moulding rather than autoclave).
- Joining to metal parts (adhesive, galvanic C/Al couple), crash energy absorption, repairability and inspection (BVID).
- Recyclability at end of life.
- Al and Mg sheet is cheap to stamp and weld at volume. Mg brings corrosion and formability issues (HCP, needs warm forming).

## Structures

### SQ3 - Asymmetric T-section cantilever

The flange is $100\times5$ mm and the web is $100\times2$ mm, so $A=700\ \mathrm{mm^2}$. The centroid is (17.5) mm below the top surface and (55.714) mm from the left edge.

#### (a) Section properties

Using two non-overlapping rectangles and the parallel-axis theorem gives

$$
\boxed{I_{zz}=5.615\times10^5\ \mathrm{mm^4}},
$$

$$
\boxed{I_{yy}=4.739\times10^5\ \mathrm{mm^4}},
$$

$$
\boxed{I_{yz}=1.500\times10^5\ \mathrm{mm^4}}.
$$

The principal minimum is $I_{\min}=3.614\times10^5\ \mathrm{mm^4}$, showing how much stiffness is hidden by the coupling term.

#### (b) Extreme bending stresses

Resolve $F=1$ kN at 30 degrees from (+y):

$$
F_y=866.0\ \mathrm{N},\qquad F_z=500\ \mathrm{N}.
$$

At the clamp, $M_z=1.732\times10^6\ \mathrm{N\,mm}$ and $M_y=-1.000\times10^6\ \mathrm{N\,mm}$. Use

$$
\sigma_x=-\frac{M_zI_y+M_yI_{yz}}{\Delta}y
+\frac{M_yI_z+M_zI_{yz}}{\Delta}z.
$$

Checking all external vertices gives, for the force sense drawn,

$$
\boxed{\sigma_{\max,t}\approx+117\ \mathrm{MPa}}
$$

at the left edge of the upper flange, and

$$
\boxed{\sigma_{\max,c}\approx-260\ \mathrm{MPa}}
$$

at the lower-right edge of the web. Both occur at the fixed end. Reversing the force reverses the stress signs.

#### (c) Shear centre and local through-thickness stress

For this ideal open T, the shear centre is at the intersection of the flange and web median lines, 70 mm from the flange's left edge. The load is applied at the left edge, so its vertical component creates

$$
T=(70)(866.0)=60.62\times10^3\ \mathrm{N\,mm}.
$$

The local shear at A and B is the superposition of:

1. bending shear flow, obtained on each branch from

   $$
   q_b(s)=\frac{1}{\Delta}
   \left[(V_yI_y-V_zI_{yz})Q_y(s)
   +(V_zI_z-V_yI_{yz})Q_z(s)\right],
   $$

2. open-section St Venant torsion, with $J\simeq\sum bt^3/3$ and a linear through-thickness stress.

At A, the running first moments from the left flange free edge are

$$
Q_y=-3750\ \mathrm{mm^3},\qquad
Q_z=-7679\ \mathrm{mm^3},
$$

which give

$$
q_A=-9.92\ \mathrm{N/mm},\qquad
\tau_{b,A}=q_A/5=-1.98\ \mathrm{MPa}.
$$

At B, integrating upward from the web free edge gives

$$
Q_y=6250\ \mathrm{mm^3},\qquad
Q_z=1429\ \mathrm{mm^3},
$$

so

$$
q_B=9.49\ \mathrm{N/mm},\qquad
\tau_{b,B}=q_B/2=4.75\ \mathrm{MPa}.
$$

The open-section torsion constant is

$$
J\simeq\frac13[100(5^3)+100(2^3)]
=4433\ \mathrm{mm^4}.
$$

The bending component is nearly uniform through each thin wall, while torsion changes sign across the wall. Thus

$$
\boxed{\tau(n)=\frac{q_b}{t}+\frac{2Tn}{J}},\qquad -t/2\le n\le t/2.
$$

At A the torsional surface value is ±68.37 MPa, giving face stresses

$$
\boxed{\tau_A=+66.4\ \mathrm{MPa}\quad\text{and}\quad-70.4\ \mathrm{MPa}}.
$$

At B the torsional surface value is ±27.35 MPa, giving

$$
\boxed{\tau_B=+32.1\ \mathrm{MPa}\quad\text{and}\quad-22.6\ \mathrm{MPa}}.
$$

These are the endpoints of the requested straight-line through-thickness diagrams; their directions reverse between opposite wall faces.

#### (d) Quick shear estimate

Torsion dominates, so ignore the much smaller bending-shear offset and use only the thickest wall in the open-section torsion formula:

$$
\tau_{max}\approx\frac{Tt_{max}}J
=\boxed{68.4\ \mathrm{MPa}}.
$$

The full part (c) result is 70.4 MPa, so the error is

$$
\boxed{\frac{70.4-68.4}{70.4}\times100\%=2.8\%}.
$$

The important inputs are the load eccentricity, vertical force component, wall thicknesses and $J$. The beam length and Young's modulus do not affect this local shear-stress estimate.

#### (e) End displacement direction

Because $I_{yz}\ne0$, a load in one geometric direction creates curvature in both $y$ and $z$. The free-end centroid therefore does not move exactly parallel to $F$. In matrix form,

$$
\begin{bmatrix}\kappa_y\\\kappa_z\end{bmatrix}
=
\begin{bmatrix}I_y&-I_{yz}\\-I_{yz}&I_z\end{bmatrix}^{-1}
\begin{bmatrix}M_y\\M_z\end{bmatrix}.
$$

The offset load also twists the cross-section about its shear centre.

#### (f) Centric compression, fixed-free

The question asks for buckling in the coordinate planes while ignoring coupling, so use the smaller coordinate second moment $I_{yy}$ and $K=2$:

$$
P_E=\frac{\pi^2EI_{yy}}{(2L)^2}
=\boxed{20.46\ \mathrm{kN}}.
$$

Crushing would require $A\sigma_{allow}=210$ kN, so Euler buckling governs.

#### (g) Initial curvature, pin-pin at 75 kN

For the same weak coordinate direction but pin-ended,

$$
P_E=\frac{\pi^2EI_{yy}}{L^2}=81.85\ \mathrm{kN}.
$$

For sinusoidal initial amplitude $a_0$, the total amplitude is $a=a_0/(1-P/P_E)$. Setting

$$
\frac PA+\frac{Pac}{I_{yy}}=300\ \mathrm{MPa},
$$

with $c=55.714$ mm gives

$$
\boxed{a_{0,\max}=1.83\ \mathrm{mm}}.
$$

### Linked notes

- [[SESA2028 S1 - Section Properties and Unsymmetrical Bending]]
- [[SESA2028 S3 - Shear Flow and Shear Centre]]
- [[SESA2028 S6 - Imperfect Columns, Beam-Columns and Plate Buckling]]
