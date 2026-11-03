---
title: "SESA2028 Formula Sheet"
aliases: ["SESA2028 Materials Formula Sheet", "SESA2028 Structures Formula Sheet"]
module: "SESA2028 Aerospace Materials & Structures"
type: formula-sheet
tags: [sesa2028, materials, structures, formula-sheet, revision]
status: lectured
date: 2026-10-30
parent: ["[[SESA2028 Aerospace Materials & Structures Hub]]"]
---

# SESA2028 Formula Sheet

The structural and materials equations are collected here because exam design questions often move directly from a stress or stiffness calculation to failure, life or material selection. The topic notes contain the assumptions and derivations.

## Structural analysis

Notation follows the structures lectures: $x$ along the beam, $\sigma_{xx}$ the bending stress, $Q_y$ and $Q_z$ the shear forces, and a positive $M_z$ giving tension at positive $y$ ([[SESA2028 S1 - Section Properties and Unsymmetrical Bending|S1]]). The topic notes hold the assumptions and derivations.

### Section properties

$$
\bar y=\frac{\sum A_i y_i}{\sum A_i},\qquad
\bar z=\frac{\sum A_i z_i}{\sum A_i}
$$

$$
I_z=\int y^2dA,\qquad I_y=\int z^2dA,\qquad I_{yz}=\int yz\,dA
$$

Parallel axes, with $\Delta y$, $\Delta z$ the offsets of each part's centroid from the section centroid:

$$
I_z=\sum\left(I_{z,c}+A\,\Delta y^2\right),\quad
I_y=\sum\left(I_{y,c}+A\,\Delta z^2\right),\quad
I_{yz}=\sum\left(I_{yz,c}+A\,\Delta y\,\Delta z\right)
$$

Principal axes ($\theta$ measured from $y$ towards $z$, as in S1):

$$
\tan2\theta_1=\frac{2I_{yz}}{I_z-I_y},\qquad
I_{1,2}=\frac{I_y+I_z}{2}\pm\sqrt{\left(\frac{I_z-I_y}{2}\right)^2+I_{yz}^2}
$$

Substitute $\theta_1$ back and confirm $I_{y'z'}=0$ before using the principal values.

### Unsymmetrical bending

$$
\sigma_{xx}=\frac{\left(M_zI_y-M_yI_{yz}\right)y+\left(M_yI_z-M_zI_{yz}\right)z}{I_yI_z-I_{yz}^2}
$$

The neutral axis is the line $\sigma_{xx}=0$ through the centroid; evaluate $\sigma_{xx}$ at every corner of the section, because the extreme values sit at the points furthest from that line. With $I_{yz}=0$ it reduces to $\sigma_{xx}=M_zy/I_z+M_yz/I_y$.

### Beam curvature and standard deflections

$$
EI\frac{d^2v}{dx^2}=M(x)\quad\text{(sign of }M\text{ fixed by the axis convention of the question)}
$$

| Case | Maximum deflection | End slope |
|---|---|---|
| Cantilever, tip load $P$ | $PL^3/3EI$ | $PL^2/2EI$ |
| Cantilever, UDL $w$ | $wL^4/8EI$ | $wL^3/6EI$ |
| Simply supported, central $P$ | $PL^3/48EI$ | $PL^2/16EI$ |
| Simply supported, UDL $w$ | $5wL^4/384EI$ | $wL^3/24EI$ |

### Shear flow

General thin-walled open section, $s$ measured from where the flow is $q_{out}$ (zero at a free edge):

$$
q(s)=q_{out}-\frac{Q_yI_y-Q_zI_{yz}}{I_yI_z-I_{yz}^2}\int_0^sty\,ds-\frac{Q_zI_z-Q_yI_{yz}}{I_yI_z-I_{yz}^2}\int_0^stz\,ds,\qquad \tau=\frac qt
$$

With $I_{yz}=0$ and $Q_z=0$ this is $q=Q_y\,\bar yA/I_z$ in magnitude. At a junction, flow in equals flow out. A closed cell is cut, analysed as open, and given a constant $q_0$ fixed by moment equilibrium. The shear centre is the point about which the wall forces have no net moment ([[SESA2028 S3 - Shear Flow and Shear Centre|S3]]).

### Torsion

Circular shaft:

$$
\tau=\frac{Tr}{J},\qquad \frac{d\phi}{dx}=\frac{T}{GJ},\qquad J=\frac\pi2\left(R_e^4-R_i^4\right)
$$

Closed thin wall (Bredt–Batho):

$$
q=\frac{T}{2A_m},\qquad \tau=\frac{q}{t},\qquad J=\frac{4A_m^2}{\oint ds/t}
$$

Open thin wall:

$$
J=\frac13\sum b_it_i^3,\qquad \tau_{max}=\frac{Tt_{max}}{J}
$$

$A_m$ is the area enclosed by the wall midline. Multi-cell sections ($T=2\sum A_iq_i$, equal twist rate in every cell) are on the slides but were not lectured in 2025–26.

### Euler buckling

$$
P_{cr}=\frac{\pi^2EI}{L_e^2},\qquad
\sigma_{cr}=\frac{\pi^2E}{\left(L_e/r\right)^2},\qquad r=\sqrt{I/A}
$$

| Ends | $L_e/L$ |
|---|---:|
| pinned–pinned | 1 |
| fixed–free | 2 |
| fixed–pinned | 0.699 |
| fixed–fixed | 0.5 |

Use the smaller $I$ unless the end conditions differ about the two axes; then check both.

### Imperfect columns and beam-columns

Initial sine crookedness $a_0$, pin ends:

$$
a=\frac{a_0}{1-P/P_{cr}},\qquad \sigma_{max}=\frac PA+\frac{Pac}{I}
$$

Eccentric load $e$, pin ends (secant formula):

$$
\sigma_{max}=\frac PA\left[1+\frac{ec}{r^2}
\sec\left(\frac{L_e}{2r}\sqrt{\frac{P}{EA}}\right)\right]
$$

Plate buckling, $\sigma_{cr}=k\pi^2E(t/b)^2/12(1-\nu^2)$, is on the slides but was not lectured in 2025–26.

### Strain energy and energy methods

$$
U=\int\left(
\frac{N^2}{2EA}+\frac{M^2}{2EI}
+\frac{T^2}{2GJ}\right)dx\quad(+\text{ a shear term, usually negligible for slender members})
$$

Castigliano's second theorem and the unit load method:

$$
u_j=\frac{\partial U}{\partial F_j},\qquad
\delta=\int\left(
\frac{Nn}{EA}+\frac{Mm}{EI}+\frac{Tt}{GJ}
\right)dx
$$

where $n$, $m$, $t$ are the internal actions from a unit load at the point and in the direction of $\delta$ ([[SESA2028 S7 - Strain Energy and Conservation of Energy|S7]], [[SESA2028 S8 - Virtual Work and Castigliano Theorems|S8]]).

### Thick cylinders and shrink fits

Axisymmetric equilibrium (no body force) and the Lamé solution:

$$
\frac{d\sigma_{rr}}{dr}+\frac{\sigma_{rr}-\sigma_{\theta\theta}}{r}=0,\qquad
\sigma_{rr}=A-\frac{B}{r^2},\qquad
\sigma_{\theta\theta}=A+\frac{B}{r^2}
$$

With $\sigma_{rr}(r_i)=-p_i$ and $\sigma_{rr}(r_o)=-p_o$:

$$
A=\frac{p_ir_i^2-p_or_o^2}{r_o^2-r_i^2},\qquad
B=\frac{(p_i-p_o)r_i^2r_o^2}{r_o^2-r_i^2}
$$

Axial stress: open ends $\sigma_{zz}=0$; closed ends $\sigma_{zz}=A$ (internal pressure only); fixed between rigid supports $\sigma_{zz}=\nu(\sigma_{rr}+\sigma_{\theta\theta})=2\nu A$. Radial displacement $u_r=r\varepsilon_{\theta\theta}$ with $\varepsilon_{\theta\theta}=[\sigma_{\theta\theta}-\nu(\sigma_{rr}+\sigma_{zz})]/E$.

Shrink fit at interface radius $r_m$ (radial interference $\delta$, contact pressure $p$ common to both parts):

$$
\delta=u^{o}_r(r_m)-u^{i}_r(r_m)=r_m\left(\varepsilon^{o}_{\theta\theta}-\varepsilon^{i}_{\theta\theta}\right)
$$

Check whether a question gives radial or diametral interference. Tresca at the bore uses $(\sigma_{\theta\theta}-\sigma_{rr})/2$ because $\sigma_{zz}$ is the intermediate stress ([[SESA2028 S10 - Thick Cylinders and Shrink Fits|S10]]).

### Spinning discs (not lectured in 2025–26)

$$
\sigma_{rr}=A-\frac{B}{r^2}-\frac{3+\nu}{8}\rho\omega^2r^2,\qquad
\sigma_{\theta\theta}=A+\frac{B}{r^2}-\frac{1+3\nu}{8}\rho\omega^2r^2
$$

Solid disc $B=0$; a central hole doubles the peak hoop stress ([[SESA2028 S11 - Spinning Discs|S11]]).

### Linked notes

- [[SESA2028 Aerospace Materials & Structures Hub]]
- [[SESA2028 Past Paper Map]]

## Materials, failure and selection

Everything numerical that the materials half examines, on one page. Each block links to the note with the derivation.

### Fracture mechanics ([[SESA2028 M1 - Fracture, Toughness and Fracture Mechanics|M1]])

$$
K=Q\sigma\sqrt{\pi a}\qquad(a\text{ in m; surface crack depth or half internal length})
$$

$$
\text{fast fracture: }K=K_{Ic},\qquad a_c=\frac1\pi\left(\frac{K_{Ic}}{Q\sigma_{max}}\right)^2
$$

$$
\text{Griffith: }\sigma_f=\sqrt{\frac{EG_c}{\pi a}},\quad G_c=2(\gamma_e+\gamma_p),\quad K_c=\sqrt{EG_c}
$$

$$
K_t=1+2\sqrt{\frac{b}{r}}\ (\text{notch depth }b,\ \text{root radius }r),\quad K_t=3\ (\text{circular hole})
$$

$$
\text{Griffith (centre crack }2a\text{, plane stress): }U_e=\frac{\pi a^2\sigma^2}{E},\ U_s=4a\gamma,\quad G=\frac{\pi a\sigma^2}{E}
$$

$$
\text{plane strain: }\varepsilon_{33}=0\Rightarrow\sigma_{33}=\nu\left(\sigma_{11}+\sigma_{22}\right)
\qquad
\text{Charpy: IE}=mg\left(h_0-h_1\right)
$$

$$
\text{torsion (pure shear }\tau\text{): }\sigma_n(\theta)=\tau\sin2\theta,\ \text{maximum opening at }45^\circ
$$

LEFM is valid if the plastic zone ≲ 1/50 of the crack length, the ligament and the thickness.

### Fatigue ([[SESA2028 M2 - Fatigue - Fracture Surfaces, Mechanisms and Lifing|M2]])

$$
\Delta\sigma=\sigma_{max}-\sigma_{min},\quad\sigma_a=\tfrac{\Delta\sigma}2,\quad\sigma_m=\tfrac{\sigma_{max}+\sigma_{min}}2,\quad R=\tfrac{\sigma_{min}}{\sigma_{max}}
$$

$$
\text{Basquin (HCF): }\frac{\Delta\sigma}2=\sigma_f'(2N_f)^b\qquad
\text{Coffin-Manson (LCF): }\frac{\Delta\varepsilon_p}2=\varepsilon_f'(2N_f)^c
$$

$$
\text{Basquin inverted: }N_f=\frac12\left(\frac{\sigma_a}{\sigma_f'}\right)^{1/b}
$$

$$
\text{Goodman: }\sigma_a=\sigma_{a0}\left(1-\frac{\sigma_m}{\sigma_{ts}}\right)\qquad
\text{Miner: }\sum\frac{n_i}{N_i}=1
$$

Paris lifing:

$$
\frac{da}{dN}=A(\Delta K)^m,\quad\Delta K=Q\Delta\sigma\sqrt{\pi a},\quad\Delta\sigma=\sigma_{max}-\max(\sigma_{min},0)
$$

$$
\boxed{N_f=\frac{a_c^{\,1-m/2}-a_i^{\,1-m/2}}{\left(1-\frac m2\right)A\left(Q\Delta\sigma\sqrt\pi\right)^m}}\quad(m\ne2)
$$

For $m=2$: $N_f=\dfrac{\ln(a_c/a_i)}{A(Q\Delta\sigma)^2\pi}$. Apply SF 2 on life (inspect at $N_f/2$).

Rule of thumb: the final-fracture area fraction ≈ $\sigma_{max}/\sigma_{UTS}$.

### Corrosion ([[SESA2028 M3 - Corrosion, Wear and Surface Engineering|M3]])

$$
\Delta G=-nFE,\quad F=96\,485\ \mathrm{C/mol}
$$

$$
\text{Nernst: }E=E^0+\frac{0.0592}{n}\log_{10}[\mathrm{M^{n+}}]\quad(25^\circ\text{C; the slide's }0.592\text{ and minus sign are slips})
$$

$$
\text{Faraday: }w=\frac{MIt}{nF},\quad\text{rate}\propto\frac IA,\quad\frac{dx}{dt}=\frac{Mi}{nF\rho},\quad\text{penetration}\propto\frac{A_{cathode}}{A_{anode}}
$$

$$
\mathrm{CR\,[mm/yr]}=3.27\frac{MI}{n\rho A},\quad
\mathrm{CR\,[g\,m^{-2}day^{-1}]}=8.95\frac{MI}{nA}\quad(I\ \text{mA},\ A\ \text{cm}^2)
$$

Zn-Cu cell: $E_{cell}=E_{cathode}-E_{anode}=0.34-(-0.76)=+1.10$ V (the lecture writes −1.1 V, "most negative minus least negative"). The more negative metal is the anode. Stainless needs Cr > 12 %.

### Composites and lightweighting ([[SESA2028 M4 - Polymer Matrix Composites|M4]], [[SESA2028 M5 - Metal and Ceramic Matrix Composites and Hybrid Laminates|M5]])

$$
E_L=V_fE_f+V_mE_m,\quad\sigma_L\approx V_f\sigma_f+V_m\sigma_m,\quad\rho_c=V_f\rho_f+V_m\rho_m
$$

$$
\frac1{E_T}=\frac{V_f}{E_f}+\frac{V_m}{E_m}\qquad V_f=\frac{P_{req}-P_m}{P_f-P_m}\ (\text{take the larger of }E\text{ and }\sigma)
$$

$$
\frac{P_f}{P_m}=\frac{V_fE_f}{V_mE_m}\qquad
l_c=\frac{\sigma_f^*d}{2\tau},\quad\bar\sigma_f=\sigma_f^*\left(1-\frac{l_c}{2l}\right)\ (l\ge l_c);\quad l\ge15l_c\approx\text{continuous}
$$

| Index to maximise | Tie | Beam / strut (buckling) | Panel |
|---|---|---|---|
| Stiffness | $E/\rho$ | $E^{1/2}/\rho$ | $E^{1/3}/\rho$ |
| Strength | $\sigma/\rho$ | $\sigma^{2/3}/\rho$ | $\sigma^{1/2}/\rho$ |

Rod or sheet sizing: $\varepsilon=\Delta L/L=\sigma/E$, $A=F/\sigma_{allow}$, mass $=\rho AL$.

### Light alloys and steels ([[SESA2028 M6 - Light Alloys - Aluminium, Magnesium, Beryllium and Titanium|M6]], [[SESA2028 M7 - Steels - Phase Transformations, Heat Treatment and Alloying|M7]])

$$
\text{Hall-Petch: }\sigma_y=\sigma_0+k_yd^{-1/2}
$$

$$
\text{precipitate interface area (volume }V\text{, radius }r\text{): }A=\frac{3V}{r}\quad(\text{coarsening lowers it: over-ageing})
$$

$$
\text{lever rule, pro-eutectoid ferrite: }W_\alpha=\frac{0.76-C_0}{0.76-0.022}
$$

Densities (g/cm³): Mg 1.74, Be 1.85, Al 2.70, Ti 4.51, Fe 7.87. Specific stiffness about 26 GPa·cm³/g for steel, Al, Mg and Ti; about 160 for Be.

Eutectoid: 0.76 % C at 727 °C. TTT nose ≈ 540-550 °C at ≈ 1 s. Critical rate from 700 °C ≈ 150-200 °C/s.

Jominy: about 225 °C/s → 2 °C/s along the bar; 9.8 mm = centre of a 28 mm oil-quenched bar.

### Creep and oxidation ([[SESA2028 M8 - High Temperature Materials - Creep, Oxidation and Superalloys|M8]])

$$
\dot\varepsilon_{ss}=A\sigma^ne^{-Q/RT},\qquad t_r=A'\sigma^{-n}e^{Q/RT}
$$

$$
\boxed{\mathrm{LMP}=T(C+\log_{10}t_r)},\quad T\text{ in K},\ C\approx20\ (\text{use the given }C),\quad\log t_r=\frac{\mathrm{LMP}}T-C
$$

$$
\text{Creep Miner: }\sum\frac{t_i}{t_{r,i}}=1\quad(\text{interpolate }\log t_r)
$$

$$
\text{Stress relaxation: }\sigma=\sigma_0e^{-t/\tau}
$$

$$
\text{Oxidation: }w=k_Lt\ (\text{linear}),\quad w^2=k_pt+C\ (\text{parabolic}),\quad w=k_e\log(Ct+A)\ (\text{logarithmic})
$$

$$
\text{parabolic from diffusion control: }\frac{dx}{dt}=\frac kx\ \Rightarrow\ x^2=2kt+x_0^2
$$

Creep matters above about $0.4T_m$. $10^5$ h = 11.4 years.

### Units and traps

- $a$ in metres in every $K$ and Paris calculation; $K$ in $\mathrm{MPa\sqrt m}$.
- Temperature in kelvin in LMP and Arrhenius (add 273).
- Compressive part of the cycle: ignore it in $\Delta\sigma$.
- Ceramic "UTS" in tables is often compressive.
- The rule of mixtures on specific properties is only approximate.
