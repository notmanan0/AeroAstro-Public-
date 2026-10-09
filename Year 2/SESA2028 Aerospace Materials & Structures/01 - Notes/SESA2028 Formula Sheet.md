---
title: "SESA2028 Formula Sheet"
aliases: ["SESA2028 Materials Formula Sheet", "SESA2028 Structures Formula Sheet"]
module: "SESA2028 Aerospace Materials & Structures"
type: formula-sheet
tags: [sesa2028, materials, structures, formula-sheet, revision]
status: complete
parent: ["[[SESA2028 Aerospace Materials & Structures Hub]]"]
---

# SESA2028 Formula Sheet

The structural and materials equations are collected here because exam design questions often move directly from a stress or stiffness calculation to failure, life or material selection. The topic notes contain the assumptions and derivations.

## Structural analysis

This sheet is deliberately compact. The topic notes explain assumptions and derivations.

### Section properties

$$
\bar y=\frac{\sum A_i y_i}{\sum A_i},\qquad
\bar z=\frac{\sum A_i z_i}{\sum A_i}
$$

$$
I_y=\int z^2dA,\qquad I_z=\int y^2dA,\qquad I_{yz}=\int yz\,dA
$$

$$
I_y=I_{y,c}+A(\Delta z)^2,\quad
I_z=I_{z,c}+A(\Delta y)^2,\quad
I_{yz}=I_{yz,c}+A\Delta y\Delta z
$$

$$
I_{1,2}=\frac{I_y+I_z}{2}
\pm\sqrt{\left(\frac{I_y-I_z}{2}\right)^2+I_{yz}^2}
$$

$$
\tan2\theta_p=\frac{2I_{yz}}{I_y-I_z}
$$

### Unsymmetrical bending

Let $\Delta=I_yI_z-I_{yz}^2$. Then

$$
\sigma_x=-\frac{M_zI_y+M_yI_{yz}}{\Delta}y
+\frac{M_yI_z+M_zI_{yz}}{\Delta}z
$$

Neutral axis: set $\sigma_x=0$. Always evaluate the resulting linear field at every boundary vertex.

### Beam curvature and standard deflections

$$
EI\frac{d^2v}{dx^2}=M(x)
$$

Cantilever, tip force:

$$
v_L=\frac{PL^3}{3EI},\qquad \theta_L=\frac{PL^2}{2EI}
$$

Cantilever, full UDL:

$$
v_L=\frac{wL^4}{8EI},\qquad \theta_L=\frac{wL^3}{6EI}
$$

Simply supported, centre load:

$$
v_{max}=\frac{PL^3}{48EI}
$$

### Shear flow

Symmetric uncoupled case:

$$
q=\frac{VQ}{I},\qquad \tau=\frac qt
$$

General open-section form:

$$
q(s)=\frac{(V_yI_y-V_zI_{yz})Q_y(s)
+(V_zI_z-V_yI_{yz})Q_z(s)}{\Delta}
$$

Free edge: $q=0$. At a branch junction: algebraic inflow equals algebraic outflow.

Shear centre from torque balance:

$$
Ve=\int_{wall} q(s)\,[y\,dz-z\,dy]
$$

### Torsion

Circular shaft:

$$
\tau=\frac{Tr}{J},\qquad \frac{d\phi}{dx}=\frac{T}{GJ}
$$

Open thin wall:

$$
J\simeq\frac13\sum b_it_i^3,\qquad
\tau_{max,i}\simeq\frac{Tt_i}{J}
$$

Single closed cell:

$$
q=\frac{T}{2A_m},\qquad \tau=\frac qt
$$

$$
\frac{d\phi}{dx}=
\frac{T}{4A_m^2}\oint\frac{ds}{Gt}
$$

Multi-cell:

$$
T=2\sum A_iq_i,
$$

with equal twist rate in every cell and $q_{common}=q_i-q_j$.

### Euler buckling

$$
P_E=\frac{\pi^2EI}{(KL)^2}
$$

| Ends | K |
|---|---:|
| pin-pin | 1.0 |
| fixed-free | 2.0 |
| fixed-pin | about 0.699 |
| fixed-fixed | 0.5 |

$$
\lambda=\frac{KL}{r_g},\qquad r_g=\sqrt{I/A},\qquad
\sigma_E=\frac{\pi^2E}{\lambda^2}
$$

Initial sine imperfection:

$$
a=\frac{a_0}{1-P/P_E}
$$

Eccentric pin-ended column:

$$
\sigma_{max}=\frac PA\left[1+\frac{ec}{r_g^2}
\sec\left(\frac{L}{2r_g}\sqrt{\frac{P}{EA}}\right)\right]
$$

### Plate buckling

$$
\sigma_{cr}=k\frac{\pi^2E}{12(1-\nu^2)}\left(\frac tb\right)^2
$$

For a simply supported rectangular plate in uniaxial compression,

$$
k=\frac{(m^2+n^2a^2/b^2)^2}{m^2a^2/b^2}
$$

and choose the admissible integers $m,n$ that minimise $\sigma_{cr}$.

### Strain energy

$$
U=\int\left(
\frac{N^2}{2EA}+\frac{M^2}{2EI}
+\frac{T^2}{2GJ}+\frac{\kappa V^2}{2GA}
\right)dx
$$

Castigliano:

$$
\delta_i=\frac{\partial U}{\partial P_i},\qquad
\theta_i=\frac{\partial U}{\partial M_i}
$$

Unit-load/virtual work:

$$
\delta=\int\left(
\frac{Nn}{EA}+\frac{Mm}{EI}+\frac{Tt}{GJ}
\right)dx
$$

### Axisymmetric cylinders

Equilibrium:

$$
\frac{d\sigma_r}{dr}+\frac{\sigma_r-\sigma_\theta}{r}=0
$$

Lamé solution:

$$
\sigma_r=A-\frac{B}{r^2},\qquad
\sigma_\theta=A+\frac{B}{r^2}
$$

For $\sigma_r(a)=-p_i, \sigma_r(b)=-p_o$:

$$
A=\frac{p_ia^2-p_ob^2}{b^2-a^2},\qquad
B=\frac{(p_i-p_o)a^2b^2}{b^2-a^2}
$$

General radial displacement:

$$
u(r)=\frac1E\left(
[(1-\nu)A-\nu\sigma_z]r+(1+\nu)\frac Br
\right)
$$

Open ends: $\sigma_z=0$. Closed ends carrying the end thrust: $\sigma_z=A$ (the Lamé constant).

Shrink-fit compatibility at $r=c$:

$$
\delta=u_{outer\ surface\ of\ inner}(c)
-u_{inner\ surface\ of\ outer}(c)
$$

### Spinning discs

Radial equilibrium with body force:

$$
\frac{d\sigma_r}{dr}+\frac{\sigma_r-\sigma_\theta}{r}
+\rho\omega^2r=0
$$

Use the displacement constitutive relation, solve for $u(r)$, then impose finite displacement at $r=0$ for a solid disc and radial-traction conditions at free radii.

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
K_t=1+\frac{2a}{b}\ (\text{elliptical hole}),\quad K_t=3\ (\text{circular hole})
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
\text{Goodman: }\sigma_a=\sigma_{a0}\left(1-\frac{\sigma_m}{\sigma_{TS}}\right)\qquad
\text{Miner: }\sum\frac{n_i}{N_i}=1
$$

**Paris lifing:**

$$
\frac{da}{dN}=A(\Delta K)^m,\quad\Delta K=Q\Delta\sigma\sqrt{\pi a},\quad\Delta\sigma=\sigma_{max}-\max(\sigma_{min},0)
$$

$$
\boxed{N_f=\frac{a_c^{\,1-m/2}-a_i^{\,1-m/2}}{\left(1-\frac m2\right)A\left(Q\Delta\sigma\sqrt\pi\right)^m}}\quad(m\ne2)
$$

For $m=2$: $N_f=\dfrac{\ln(a_c/a_i)}{A(Q\Delta\sigma)^2\pi}$. **Apply SF 2** on life (inspect at $N_f/2$).

Rule of thumb: the final-fracture area fraction ≈ $\sigma_{max}/\sigma_{UTS}$.

### Corrosion ([[SESA2028 M3 - Corrosion, Wear and Surface Engineering|M3]])

$$
\Delta G=-nFE,\quad F=96\,485\ \mathrm{C/mol}
$$

$$
\text{Nernst: }E=E^0+\frac{0.0592}{n}\log_{10}[\mathrm{M^{n+}}]
$$

$$
\text{Faraday: }w=\frac{MIt}{nF},\quad\text{rate}\propto\frac IA
$$

$$
\mathrm{CR\,[mm/yr]}=3.27\frac{MI}{n\rho A},\quad
\mathrm{CR\,[g\,m^{-2}day^{-1}]}=8.95\frac{MI}{nA}\quad(I\ \text{mA},\ A\ \text{cm}^2)
$$

Zn-Cu cell: $|{-0.76}-0.34|=1.10$ V. **The more negative metal is the anode.** Stainless needs Cr > 12 %.

### Composites and lightweighting ([[SESA2028 M4 - Polymer Matrix Composites|M4]], [[SESA2028 M5 - Metal and Ceramic Matrix Composites and Hybrid Laminates|M5]])

$$
E_L=V_fE_f+V_mE_m,\quad\sigma_L\approx V_f\sigma_f+V_m\sigma_m,\quad\rho_c=V_f\rho_f+V_m\rho_m
$$

$$
\frac1{E_T}=\frac{V_f}{E_f}+\frac{V_m}{E_m}\qquad V_f=\frac{P_{req}-P_m}{P_f-P_m}\ (\text{take the larger of }E\text{ and }\sigma)
$$

$$
l_c=\frac{\sigma_f^*d}{2\tau};\quad l\ge15l_c\approx\text{continuous}
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

Densities (g/cm³): Mg 1.74, Be 1.85, Al 2.70, Ti 4.51, Fe 7.87.

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

Creep matters above about $0.4T_m$. $10^5$ h = 11.4 years.

### Units and traps

- $a$ in **metres** in every $K$ and Paris calculation; $K$ in $\mathrm{MPa\sqrt m}$.
- Temperature in **kelvin** in LMP and Arrhenius (add 273).
- Compressive part of the cycle: ignore it in $\Delta\sigma$.
- Ceramic "UTS" in tables is often **compressive**.
- The rule of mixtures on specific properties is only approximate.
