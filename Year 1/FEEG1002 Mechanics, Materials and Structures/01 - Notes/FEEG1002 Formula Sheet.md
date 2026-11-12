---
title: "FEEG1002 Formula Sheet"
module: "FEEG1002 Mechanics, Materials and Structures"
type: formula
aliases: ["FEEG1002 formulae", "Mechanics Materials and Structures formula sheet"]
tags: [feeg1002, formula, exam-prep]
status: complete
sources: ["01 - Notes/Topics", "02 - Sources"]
---

# FEEG1002 Formula Sheet

Everything on one page, organised by part. Each section links to its topic note.

> [!warning] Sign conventions used in FEEG1002 (Statics)
> - Deflection $v$ is positive **downwards**, $M$ is positive when **sagging**, and $EI\,v'' = -M$.
> - Shear force $Q$ is positive downwards on the left segment's cut face.
> - Mohr's circle: shear is plotted positive **downwards** and $\theta$ is positive anticlockwise.
> - Tensor shear strain is $\varepsilon_{xy} = \gamma_{xy}/2$.
>
> SESA2028 uses $EI\,v'' = M$ with its own axes; see the Year 2 bridges in each topic note.

## Part A: Statics 1

Conventions for the whole of Part A: bar forces and direct stresses are positive in tension; $Q$ is positive downwards on the right-hand face of the left part; $M$ is positive sagging; $v$ is positive downwards; $y$ is measured downwards from the neutral axis.

### Equilibrium, stress and strain ([[FEEG1002 A1 - Forces, Equilibrium, Stress and Strain]])

$$
\sum F_x=0,\quad\sum F_y=0,\quad\sum M_A=0\ \ \text{(any point A)}
$$

$$
\sigma=\frac FA,\qquad\tau=\frac FA\ \text{(force along the area)},\qquad\varepsilon=\frac{\Delta L}{L},\qquad\sigma=E\varepsilon,\qquad\tau=G\gamma
$$

$$
\Delta L=\frac{FL}{EA}\ \ \text{(bar as a spring, }k=EA/L),\qquad\varepsilon_{yy}=\varepsilon_{zz}=-\nu\,\varepsilon_{xx},\qquad G=\frac{E}{2(1+\nu)}
$$

$$
\sigma_{max,design}=\frac{\sigma_{max,material}}{K_{SF}},\qquad\sigma_{max}=K_T\,\sigma_{mean}\ \ (K_T=3\text{ for a small hole in a wide plate})
$$

- Lever rule for a load $F_G$ between two supports, $b$ from A and $c$ from B: $F_A=\dfrac{c}{b+c}F_G$, $F_B=\dfrac{b}{b+c}F_G$.
- Pin in double shear: $\tau=\dfrac{F/2}{\pi d^2/4}$. Punching a hole: $F=\tau\,\pi DH$.

### Trusses ([[FEEG1002 A2 - Pin-Jointed Trusses]])

- Counting test with $j$ joints, $m$ bars, $r$ reactions: $2j=m+r$ determinate, $2j>m+r$ mechanism, $2j<m+r$ indeterminate. Necessary, not sufficient.
- Method of joints: $\sum F_x=\sum F_y=0$ at each pin; start where at most two bars are unknown.
- Method of sections: cut at most three bars; take moments about the point where two of them meet.
- Zero-force members: an unloaded joint with two non-collinear bars, or with three bars of which two are collinear (the third is zero).
- Deformation: $\Delta L_i=F_iL_i/EA$; at a joint, $\mathbf u\cdot\mathbf e_i=\Delta L_i$ for each bar (displacement diagram).

### Shear force and bending moment ([[FEEG1002 A3 - Shear Force and Bending Moment Diagrams]])

$$
\frac{dQ}{dx}=-w,\qquad\frac{dM}{dx}=Q,\qquad M(x_2)-M(x_1)=\int_{x_1}^{x_2}Q\,dx
$$

- A point force makes $Q$ jump in its own direction; a clockwise applied couple makes $M$ jump up by the couple.
- $M$ has a turning point where $Q=0$, but the largest $|M|$ may be at a support, a point load or a couple.
- $M=0$ at pinned, roller and free ends with no applied couple.
- Linearly varying load, zero to $W_B$ on a simply supported span: $M_{max}=\dfrac{W_BL^2}{9\sqrt3}$ at $x=L/\sqrt3$.

### Bending ([[FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area]])

$$
\frac{M}{I_{zz}}=\frac{\sigma_{xx}}{y}=\frac{E}{R},\qquad\varepsilon_{xx}=\frac yR,\qquad\bar y=\frac{\sum A_iy_i}{\sum A_i}
$$

$$
I_{rect}=\frac{bd^3}{12},\qquad I_{circle}=\frac{\pi D^4}{64},\qquad I=I_c+Ah^2\ \ \text{(parallel axis, }h\text{ from the overall centroid)}
$$

- Rectangle: $\sigma_{max}=\dfrac{6M}{bd^2}$. Combined axial load and bending: $\sigma_{xx}=\dfrac PA+\dfrac{My}{I}$.
- One axis of symmetry: check the extreme fibre on each side, $y_{max}$ in tension and in compression.

### Deflection ([[FEEG1002 A5 - Beam Deflection and Macaulay's Method]], [[FEEG1002 A6 - Statically Indeterminate Beams]])

$$
\frac1R=\frac{M}{EI},\qquad EI\frac{d^2v}{dx^2}=-M
$$

$$
[x-a]^n=\begin{cases}0 & x<a\\(x-a)^n & x\ge a\end{cases},\qquad\int[x-a]^n\,dx=\frac{[x-a]^{n+1}}{n+1}
$$

- Macaulay terms in $M$ for the left part: upward force $+R[x-a]$; downward force $-F[x-a]$; UDL from $a$, $-w[x-a]^2/2$; UDL stopping at $b$, add $+w[x-b]^2/2$; anticlockwise couple $-M_0[x-a]^0$.

| Case | Maximum deflection | Maximum slope | Maximum moment |
|---|---|---|---|
| Cantilever, end load $F$ | $FL^3/3EI$ | $FL^2/2EI$ | $FL$ |
| Cantilever, UDL $w$ | $wL^4/8EI$ | $wL^3/6EI$ | $wL^2/2$ |
| Simply supported, central $F$ | $FL^3/48EI$ | $FL^2/16EI$ | $FL/4$ |
| Simply supported, UDL $w$ | $5wL^4/384EI$ | $wL^3/24EI$ | $wL^2/8$ |

- Simply supported, $F$ at $a$: $v(a)=\dfrac{Fa^2(L-a)^2}{3EIL}$; for $a>L/2$ the maximum is at $x_m=\sqrt{a(2L-a)/3}$.
- Indeterminate beams: unknowns minus two equations = number of extra kinematic conditions (propped cantilever 1, built in at both ends 2).
- Propped cantilever, UDL: $R_2=\tfrac38wL$, $R_1=\tfrac58wL$, $M_1=\tfrac18wL^2$. With the UDL on the half next to the wall: $\tfrac{57}{128}wL$, $\tfrac{7}{128}wL$, $\tfrac{9}{128}wL^2$.
- Built in at both ends, span $\ell$: end moments $W\ell/8$ for a central load, $w\ell^2/12$ for a UDL.

### Buckling ([[FEEG1002 A7 - Euler Buckling of Struts]])

$$
EI\frac{d^2v}{dx^2}=-Pv\ \Rightarrow\ \frac{d^2v}{dx^2}+n^2v=0,\quad n^2=\frac{P}{EI},\qquad P_{crit}=\frac{\pi^2EI}{L_e^2}
$$

| End conditions | $L_e$ | $P_{crit}$ |
|---|---|---|
| Built in, free | $2L$ | $\tfrac14P_E$ |
| Pinned, pinned | $L$ | $P_E=\pi^2EI/L^2$ |
| Built in, pinned | $0.699L$ | $2.05P_E$ |
| Built in, built in | $L/2$ | $4P_E$ |

- Use the smallest $I$ of the section: the strut buckles about its weakest axis.
- Higher pin-ended modes: $P=m^2P_E$; a lateral support at midspan forces the second mode, $4P_E$.

### Torsion ([[FEEG1002 A8 - Torsion of Circular Shafts]])

$$
\frac TJ=\frac\tau r=\frac{G\theta}{L},\qquad\gamma=\frac{r\theta}{L},\qquad J=\frac{\pi D^4}{32},\qquad J_{hollow}=\frac{\pi(D_o^4-D_i^4)}{32}
$$

- $\tau_{max}=TR/J$ at the outer surface; torsional stiffness $GJ/L$; $\theta$ in radians.
- Hollow shaft with $n=R_i/R_o$, same strength as a solid shaft of radius $R_s$: $R_o=R_s(1-n^4)^{-1/3}$; weight ratio $(R_o/R_s)^2(1-n^2)$ (0.51 at $n=0.8$).

### Shear stress in beams ([[FEEG1002 A9 - Shear Stresses in Beams]])

$$
\sigma_{yx}=\frac{Q}{b\,I}A_s\,y_c,\qquad\sigma_{yx\,av}=\frac QA,\qquad\sigma_{yx\,max}=K\,\sigma_{yx\,av}
$$

- $K=\tfrac32$ rectangle, $\tfrac43$ solid circle, 2 thin-walled tube.
- Rectangle: $\sigma_{yx}=\tfrac32\sigma_{yx\,av}\left(1-\dfrac{y^2}{(d/2)^2}\right)$, zero at the surfaces, largest on the neutral axis.
- Rectangular cantilever with an end load: $\sigma_{xx,max}/\sigma_{yx,max}=4L/d$.
- Joint along a beam: shear force per unit length $\sigma_{yx}b$; fastener spacing = fastener capacity / $(\sigma_{yx}b)$.

## Part B: Statics 2

Course conventions: $\sigma_{ij}$ acts in direction $i$ on the face with normal $j$; tension positive; $\sigma_{xy}$ positive when it points in $+x$ or $+y$ on a face with a positive normal (read it from the right-hand face); $\theta$ positive anticlockwise; Mohr's circle with shear positive downwards.

### Stress element and pressure vessels ([[FEEG1002 B1 - Stress in Multiple Dimensions and Thin-Walled Pressure Vessels]])

$$
\sigma_{xy}=\sigma_{yx},\qquad \frac{\partial\sigma_{xx}}{\partial x}+\frac{\partial\sigma_{xy}}{\partial y}=0\ \ (\text{no body force})
$$

$$
\text{cylinder: }\sigma_{yy}=\frac{pR}{t}\ (\text{hoop}),\quad \sigma_{xx}=\frac{pR}{2t}\ (\text{longitudinal});\qquad \text{sphere: }\sigma_{xx}=\sigma_{yy}=\frac{pR}{2t}
$$

- Valid for $t/R<0.1$; radial stress $\le t/R$ of the hoop stress, so the wall is in plane stress. Outer radius is the conservative choice.
- Bolted or welded joints: pressure on the projected area, $p\pi R^2$ or $p(2RL)$, against the joint forces.

### Strain and thermal strain ([[FEEG1002 B2 - Strain in Multiple Dimensions and Thermal Strain]])

$$
\varepsilon_{xx}=\frac{du_x}{dx},\qquad \gamma_{xy}=\frac{du_x}{dy}+\frac{du_y}{dx},\qquad \varepsilon_{xy}=\frac12\gamma_{xy},\qquad \varepsilon_{vol}=\frac{\Delta V}{V_0}\approx\varepsilon_{xx}+\varepsilon_{yy}+\varepsilon_{zz}
$$

$$
\varepsilon_T=\alpha\,\Delta T,\qquad \delta_T=\alpha\,\Delta T\,L,\qquad \delta_F=\frac{FL}{EA},\qquad \text{bar between walls: }\sigma=-E\alpha\Delta T
$$

- Series between walls: $\delta_1+\delta_2=0$, $F_1=F_2$, so $F=-\Delta T(\alpha_1L_1+\alpha_2L_2)/(L_1/E_1A_1+L_2/E_2A_2)$.
- Bonded in parallel: $\delta_1=\delta_2$, $F_1+F_2=0$, so $F_1(1/E_1A_1+1/E_2A_2)=(\alpha_2-\alpha_1)\Delta T$.
- Take all forces as tensile and let the signs come out.

### Generalised Hooke's law ([[FEEG1002 B3 - Generalised Hooke's Law]])

$$
\varepsilon_{xx}=\frac1E\left[\sigma_{xx}-\nu(\sigma_{yy}+\sigma_{zz})\right]+\alpha\Delta T\ \ (\text{and cyclic}),\qquad \varepsilon_{xy}=\frac{1+\nu}{E}\sigma_{xy}=\frac{\sigma_{xy}}{2G}
$$

$$
G=\frac{E}{2(1+\nu)},\qquad K=\frac{E}{3(1-2\nu)},\qquad \varepsilon_{vol}=\frac{1-2\nu}{E}(\sigma_{xx}+\sigma_{yy}+\sigma_{zz}),\qquad -1<\nu<0.5
$$

Plane stress ($\sigma_{zz}=\sigma_{xz}=\sigma_{yz}=0$, but $\varepsilon_{zz}=-\frac\nu E(\sigma_{xx}+\sigma_{yy})\neq0$):

$$
\sigma_{xx}=\frac{E}{1-\nu^2}(\varepsilon_{xx}+\nu\varepsilon_{yy}),\qquad \sigma_{yy}=\frac{E}{1-\nu^2}(\varepsilon_{yy}+\nu\varepsilon_{xx}),\qquad \sigma_{xy}=\frac{E}{1+\nu}\varepsilon_{xy}
$$

Plane strain ($\varepsilon_{zz}=\varepsilon_{xz}=\varepsilon_{yz}=0$, but $\sigma_{zz}=\nu(\sigma_{xx}+\sigma_{yy})\neq0$):

$$
\varepsilon_{xx}=\frac{1+\nu}{E}\left[(1-\nu)\sigma_{xx}-\nu\sigma_{yy}\right]
$$

3D inverse:

$$
\sigma_{xx}=\frac{E}{(1+\nu)(1-2\nu)}\left[(1-\nu)\varepsilon_{xx}+\nu(\varepsilon_{yy}+\varepsilon_{zz})\right]
$$

- Plate restrained in both in-plane directions and heated: $\sigma=-E\alpha\Delta T/(1-\nu)$.

### Transformation and Mohr's circle ([[FEEG1002 B4 - Stress Transformation and Mohr's Circle]])

$$
\sigma_{x'x'}=\sigma_{xx}\cos^2\theta+\sigma_{yy}\sin^2\theta+2\sigma_{xy}\sin\theta\cos\theta=\frac{\sigma_{xx}+\sigma_{yy}}2+\frac{\sigma_{xx}-\sigma_{yy}}2\cos2\theta+\sigma_{xy}\sin2\theta
$$

$$
\sigma_{x'y'}=-(\sigma_{xx}-\sigma_{yy})\sin\theta\cos\theta+\sigma_{xy}(\cos^2\theta-\sin^2\theta)=-\frac{\sigma_{xx}-\sigma_{yy}}2\sin2\theta+\sigma_{xy}\cos2\theta
$$

$$
\sigma_{y'y'}=\sigma_{xx}\sin^2\theta+\sigma_{yy}\cos^2\theta-2\sigma_{xy}\sin\theta\cos\theta,\qquad \sigma_{x'x'}+\sigma_{y'y'}=\sigma_{xx}+\sigma_{yy}
$$

$$
\sigma_{average}=\frac{\sigma_{xx}+\sigma_{yy}}2,\qquad R=\sqrt{\left(\frac{\sigma_{xx}-\sigma_{yy}}2\right)^2+\sigma_{xy}^2},\qquad \sigma_{I,II}=\sigma_{average}\pm R,\qquad \sigma_{x'y'}^{max}=\pm R=\pm\frac{\sigma_I-\sigma_{II}}{2}
$$

$$
\cos2\theta_p=\frac{\sigma_{xx}-\sigma_{yy}}{2R},\qquad \sin2\theta_p=\frac{\sigma_{xy}}R,\qquad \tan2\theta_p=\frac{2\sigma_{xy}}{\sigma_{xx}-\sigma_{yy}}
$$

- Uniaxial bar: $\sigma_{x'x'}=\sigma_{xx}\cos^2\theta$, $\sigma_{x'y'}=-\sigma_{xx}\sin\theta\cos\theta$; shear peaks at $\sigma_{xx}/2$ at $\pm45^\circ$.
- $\theta$ is measured from $x$ to the normal of the plane, not to the plane (weld at 60° to the axis: $\theta=30^\circ$).
- On the circle: $x$-face point $(\sigma_{xx},\sigma_{xy})$, $y$-face point opposite; rotation $\theta$ on the element is $2\theta$ the same way on the circle; maximum-shear planes carry $\sigma_{average}$.

### Strain gauges and rosettes ([[FEEG1002 B5 - Strain Measurement and Strain Rosettes]])

$$
\frac{\Delta R}{R}=k\varepsilon,\qquad V_G=\left(\frac{R_2}{R_1+R_2}-\frac{R_x}{R_x+R_3}\right)V_S\approx-\frac{V_S}{4}k\varepsilon,\qquad \text{balance: }R_x=\frac{R_2}{R_1}R_3
$$

$$
\varepsilon_{x'x'}=\varepsilon_{xx}\cos^2\theta+\varepsilon_{yy}\sin^2\theta+2\varepsilon_{xy}\sin\theta\cos\theta\qquad(\text{use }\varepsilon_{xy}=\gamma_{xy}/2)
$$

- 0/45/90 rosette (A at 0°, C at 45°, B at 90°): $\varepsilon_{xx}=\varepsilon_A$, $\varepsilon_{yy}=\varepsilon_B$, $\varepsilon_{xy}=\varepsilon_C-\tfrac12(\varepsilon_A+\varepsilon_B)$.
- 0/60/120 rosette (A, B, C at 0°, 60°, 120°): $\varepsilon_{xx}=\varepsilon_A$, $\varepsilon_{yy}=\tfrac13[2(\varepsilon_B+\varepsilon_C)-\varepsilon_A]$, $\varepsilon_{xy}=(\varepsilon_B-\varepsilon_C)/\sqrt3$.
- Strain circle: centre $(\varepsilon_{xx}+\varepsilon_{yy})/2$, radius $\sqrt{((\varepsilon_{xx}-\varepsilon_{yy})/2)^2+\varepsilon_{xy}^2}$; principal strains share the principal-stress directions.
- Shaft in torsion: gauges at $\pm45^\circ$ read $\pm\varepsilon_{xy}$, so $\varepsilon_{xy}=(\varepsilon_I-\varepsilon_{II})/2$.

### Yield criteria and safety factor ([[FEEG1002 B6 - Yield Criteria]])

$$
\text{Tresca: }\max\left(|\sigma_I-\sigma_{II}|,|\sigma_I-\sigma_{III}|,|\sigma_{II}-\sigma_{III}|\right)<\sigma_Y\quad(\tau_{max}<\sigma_Y/2)
$$

- Plane stress ($\sigma_{III}=0$): same signs, $\max(|\sigma_I|,|\sigma_{II}|)<\sigma_Y$; opposite signs, $|\sigma_I-\sigma_{II}|<\sigma_Y$.

$$
\text{von Mises: }\sigma_{eq}=\sqrt{\tfrac12\left[(\sigma_I-\sigma_{II})^2+(\sigma_I-\sigma_{III})^2+(\sigma_{II}-\sigma_{III})^2\right]}<\sigma_Y
$$

$$
\text{plane stress: }\sigma_{eq}=\sqrt{\sigma_I^2+\sigma_{II}^2-\sigma_I\sigma_{II}}=\sqrt{\sigma_{xx}^2+\sigma_{yy}^2-\sigma_{xx}\sigma_{yy}+3\sigma_{xy}^2}
$$

$$
SF=\frac{\sigma_Y}{\sigma_{eq}}=\frac{F_{max}}{F}>1,\qquad F_{max}=\frac{\sigma_Y}{\sigma_{eq}}F\ \ (\text{linear elastic})
$$

- Pure shear yield: $0.5\sigma_Y$ (Tresca), $\sigma_Y/\sqrt3=0.577\sigma_Y$ (von Mises).
- Axial stress plus torsion: von Mises $\sigma^2+3\sigma_{xy}^2=\sigma_Y^2$, Tresca $\sigma^2+4\sigma_{xy}^2=\sigma_Y^2$.
- Cylinder wall: von Mises $\sigma_{eq}=\frac{\sqrt3}{2}\frac{pR}{t}$; Tresca $\sigma_{eq}=\frac{pR}{t}$ (out-of-plane shear governs).
- Hydrostatic stress alone never causes yield.

## Part C: Materials

All temperatures in Arrhenius-type expressions are in kelvin; $R=8.314$ J mol⁻¹ K⁻¹.

### Bonding ([[FEEG1002 C1 - Atoms and Bonding]])

$$
E_N(r)=-\frac{A}{r^m}+\frac{B}{r^n}\ (n>m),\qquad F_N=\frac{dE_N}{dr},\qquad F_N(r_0)=0,\qquad E_N(r_0)=-E_0
$$

$$
S_0=\left.\frac{d^2E_N}{dr^2}\right|_{r_0},\qquad E\approx\frac{S_0}{r_0}\approx\frac{mn\,E_0}{r_0^3}
$$

Deep well ($E_0$ large): high melting temperature. Narrow, steep well (large $S_0$): high Young's modulus.

### Crystallography ([[FEEG1002 C2 - Crystal Structures and Crystallography]])

| Structure | Stacking | Atoms/cell | Contact relation | APF | Examples |
|---|---|---:|---|---:|---|
| FCC | ABCABC | 4 | $a\sqrt2=4R$, $a=2\sqrt2R$ | $\pi/(3\sqrt2)=0.740$ | Al, Cu, Ni, austenite |
| BCC | not close-packed | 2 | $a\sqrt3=4R$, $a=4R/\sqrt3$ | $\pi\sqrt3/8=0.680$ | ferrite, Cr, W |
| HCP | ABAB | 6 | close-packed | 0.740 | Mg, Ti |

$$
\mathrm{APF}=\frac{n\cdot\tfrac43\pi R^3}{a^3},\qquad \text{corner }\tfrac18,\ \text{face }\tfrac12,\ \text{body centre }1
$$

Directions $[uvw]$: head minus tail in units of $a$, cleared to integers. Planes $(hkl)$: reciprocals of the intercepts (origin off the plane), cleared to integers. Bars for negative indices; $\langle uvw\rangle$ and $\{hkl\}$ are families. In cubic crystals $[hkl]\perp(hkl)$, and $[uvw]$ lies in $(hkl)$ when $hu+kv+lw=0$. FCC slip: $\{111\}\langle110\rangle$, 12 systems.

### Diffusion ([[FEEG1002 C3 - Diffusion]])

$$
J=-D\frac{dC}{dx},\qquad \frac{dC}{dx}=\frac{C_A-C_B}{x_A-x_B}\ \text{(steady state)},\qquad M=JAt
$$

$$
D=D_0\exp\left(-\frac{Q}{RT}\right),\qquad Q=\frac{R\ln(D_2/D_1)}{1/T_1-1/T_2},\qquad D_2=D_1\exp\left[-\frac QR\left(\frac1{T_2}-\frac1{T_1}\right)\right]
$$

Same extent of diffusion: $D_1t_1=D_2t_2$. Only Fick's first law at steady state is lectured.

### Tensile properties ([[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation]])

$$
\sigma=\frac{F}{A_0},\quad \varepsilon=\frac{\Delta L}{L_0},\quad \sigma=E\varepsilon,\quad \nu=-\frac{\varepsilon_x}{\varepsilon_z}
$$

$$
\sigma_T=\frac{F}{A_i}=\sigma(1+\varepsilon),\qquad \varepsilon_T=\ln\frac{L_i}{L_0}=\ln(1+\varepsilon)\quad\text{(before necking)}
$$

$$
\%EL=\frac{L_f-L_0}{L_0}\times100,\qquad \%RA=\frac{A_0-A_f}{A_0}\times100,\qquad U_r=\frac{\sigma_y^2}{2E}
$$

Yield strength by the 0.2 % offset (line of slope $E$ from $\varepsilon=0.002$). Toughness = whole area under the curve.

### Strengthening and annealing ([[FEEG1002 C5 - Strengthening Mechanisms and Annealing]])

$$
\%CW=\frac{A_0-A_d}{A_0}\times100,\qquad \sigma_y=\sigma_0+k_yd^{-1/2}\ \text{(Hall–Petch)},\qquad k_y=\frac{\sigma_2-\sigma_1}{d_2^{-1/2}-d_1^{-1/2}}
$$

$$
r=A\exp\left(-\frac{Q}{RT}\right),\qquad t\propto\frac1r\qquad\text{(recovery, recrystallisation, grain growth; anneal at }T\approx0.5T_m)
$$

### Phase diagrams ([[FEEG1002 C6 - Phase Diagrams]])

Tie line end points give the phase compositions; the lever rule gives the amounts. In an $\alpha+L$ field (slide notation $R=C_0-C_L$, $S=C_\alpha-C_0$):

$$
f_\alpha=\frac{C_0-C_L}{C_\alpha-C_L}=\frac{R}{R+S},\qquad f_L=\frac{C_\alpha-C_0}{C_\alpha-C_L}=\frac{S}{R+S}
$$

The same form across any two-phase field, e.g. $f_\alpha=(C_\beta-C_0)/(C_\beta-C_\alpha)$ in $\alpha+\beta$.

- Pb–Sn eutectic: $L(61.9)\rightarrow\alpha(18.3)+\beta(97.8)$ wt% Sn at 183 °C.
- Primary phase and eutectic: tie line just above the eutectic temperature, from the $\alpha$ (or $\beta$) limit to the eutectic composition. Total $\alpha$ and $\beta$: tie line just below it, across the whole $\alpha+\beta$ field.

### Steels and precipitation hardening ([[FEEG1002 C7 - Steels and Precipitation Hardening]])

$$
\gamma(0.76)\ \xrightarrow{727\,^\circ\text{C}}\ \alpha(0.022)+\mathrm{Fe_3C}(6.7)\quad\text{wt\% C (eutectoid, pearlite)}
$$

Eutectic $L(4.30)\rightarrow\gamma(2.14)+\mathrm{Fe_3C}$ at 1147 °C. Just above 727 °C:

$$
\text{hypo: } f_{\alpha,pro}=\frac{0.76-C_0}{0.76-0.022},\quad f_P=\frac{C_0-0.022}{0.76-0.022};\qquad \text{hyper: } f_{Fe_3C,pro}=\frac{C_0-0.76}{6.7-0.76},\quad f_P=\frac{6.7-C_0}{6.7-0.76}
$$

Just below 727 °C: total $f_\alpha=(6.7-C_0)/(6.7-0.022)$, $f_{Fe_3C}=(C_0-0.022)/(6.7-0.022)$.

Precipitation hardening (Al–4 wt% Cu): solution treat at $T_0\approx550$ °C (single-phase $\alpha$) → quench to $T_1$ (supersaturated $\alpha$) → age at $T_2\approx120$ °C. Sequence $\alpha_{ss}\rightarrow$ GP zones $\rightarrow\theta''\rightarrow\theta'\rightarrow\theta$ (CuAl₂). Peak-ageing time follows $t\propto\exp(Q/RT)$.

### Fracture ([[FEEG1002 C8 - Fracture - Brittle, Ductile and Fracture Mechanics]])

Internal crack length $2a$; surface crack length $a$.

$$
\sigma_m=2\sigma_0\left(\frac{a}{\rho_t}\right)^{1/2},\qquad \sigma_c=\sqrt{\frac{2E\gamma_s}{\pi a}}\ \text{(Griffith)},\qquad K_c=\sqrt{2E\gamma_s}
$$

$$
K=Y\sigma\sqrt{\pi a},\qquad K_{IC}=Y\sigma_f\sqrt{\pi a_c},\qquad \sigma_f=\frac{K_{IC}}{Y\sqrt{\pi a}},\qquad a_c=\frac1\pi\left(\frac{K_{IC}}{Y\sigma}\right)^2
$$

$Y=1$ for an infinite plate. Compare $\sigma_f$ with $\sigma_y$: the lower one governs. DBTT: $\sigma_y(T)$ of BCC crosses $\sigma_f$; work, precipitation and solution hardening raise the DBTT, grain refinement lowers it.

### Fatigue, creep and corrosion ([[FEEG1002 C9 - Fatigue, Creep and Corrosion]])

$$
\Delta\sigma=\sigma_{max}-\sigma_{min},\qquad \sigma_a=\frac{\Delta\sigma}{2},\qquad N_f=N_i+N_p
$$

$$
\Delta K=Y\Delta\sigma\sqrt{\pi a}\quad(\sigma_{min}<0\Rightarrow\text{take }\sigma_{min}=0),\qquad \frac{da}{dN}=A(\Delta K)^m
$$

$$
N_f=\frac{2}{(m-2)\,A\,Y^m\Delta\sigma^m\pi^{m/2}}\left(a_0^{(2-m)/2}-a_c^{(2-m)/2}\right)\quad(m\neq2),\qquad a_c=\frac1\pi\left(\frac{K_{IC}}{Y\sigma_{max}}\right)^2
$$

S–N curve: fatigue limit (stress for infinite life; steels, Ti alloys), fatigue life (cycles at a given stress), fatigue strength (stress for a given number of cycles, e.g. $10^7$, for Al alloys).

$$
\dot\varepsilon_s=K_2\sigma^n\exp\left(-\frac{Q_c}{RT}\right),\qquad \frac{\dot\varepsilon_2}{\dot\varepsilon_1}=\left(\frac{\sigma_2}{\sigma_1}\right)^n\exp\left[-\frac{Q_c}{R}\left(\frac1{T_2}-\frac1{T_1}\right)\right]
$$

Creep matters above about $0.3$–$0.4\,T_m$ (metals), $0.4$–$0.5\,T_m$ (ceramics).

Anode (oxidation, corrodes): $\mathrm M\rightarrow\mathrm M^{n+}+ne^-$. Cathode (reduction): e.g. $2\mathrm H^++2e^-\rightarrow\mathrm H_2$.

$$
E_{cell}=E_{cathode}-E_{anode}\qquad\text{(more negative standard potential = anode)}
$$

Cu²⁺/Cu +0.340, H⁺/H₂ 0.000, Fe²⁺/Fe −0.440, Zn²⁺/Zn −0.763, Mg²⁺/Mg −2.38 V.

### Polymers ([[FEEG1002 C10 - Polymers - Structure and Mechanics]])

$$
\bar M_n=\sum x_iM_i,\qquad \bar M_w=\sum w_iM_i,\qquad w_i=\frac{x_iM_i}{\sum x_jM_j}
$$

$$
\sigma(t)=\sigma_0\exp\left(-\frac{t}{\tau}\right),\qquad \tau=-\frac{t}{\ln(\sigma/\sigma_0)},\qquad E_r(t)=\frac{\sigma(t)}{\varepsilon_0}
$$

- $T<T_g$: linear elastic, brittle. $T_g<T<T_m$: yield, stable neck, cold drawing. Near $T_m$: viscous flow.
- Thermoplastic: linear or branched; elastomer: lightly cross-linked; thermoset: 3D covalent network.
- $E_r$ against $T$ (amorphous): glassy, leathery, rubbery, rubbery flow, viscous flow.

### Ceramics and composites ([[FEEG1002 C11 - Ceramics and Composites]])

| $r_C/r_A$ | < 0.155 | 0.155–0.225 | 0.225–0.414 | 0.414–0.732 | 0.732–1.0 |
|---|---|---|---|---|---|
| Coordination number | 2 (linear) | 3 (triangular) | 4 (tetrahedral) | 6 (octahedral) | 8 (cubic) |

Statistical design of ceramics: pick an acceptable failure probability, find $a_c=\frac1\pi(K_{IC}/Y\sigma)^2$, reject parts with larger flaws.

Continuous aligned fibres, perfect bonding, $V_f+V_m=1$:

$$
E_c=E_fV_f+E_mV_m\quad\text{(longitudinal, isostrain)},\qquad \frac{F_f}{F_c}=\frac{E_fV_f}{E_fV_f+E_mV_m}
$$

$$
\frac1{E_c}=\frac{V_f}{E_f}+\frac{V_m}{E_m},\quad E_c=\frac{E_mE_f}{E_fV_m+E_mV_f}\quad\text{(transverse, isostress)}
$$

## Part D: Dynamics

Signs: state a positive direction in every problem; in plane rigid-body problems $\mathbf k$ is out of the page and counter-clockwise is positive. Angles in radians wherever $s=r\theta$ or $\omega=\dot\theta$ appear.

### Rectilinear motion ([[FEEG1002 D1 - Linear Motion of Particles]])

$$
v=\frac{ds}{dt},\qquad a=\frac{dv}{dt}=v\frac{dv}{ds}
$$

$$
a(t):\ v=v_0+\int_0^ta\,dt;\qquad a(s):\ \tfrac12v^2-\tfrac12v_0^2=\int_{s_0}^{s}a\,ds;\qquad a(v):\ s-s_0=\int_{v_0}^{v}\frac{v\,dv}{a},\quad t=\int_{v_0}^{v}\frac{dv}{a}
$$

$$
\text{constant }a_c\text{ only:}\quad v=v_0+a_ct,\quad s=s_0+v_0t+\tfrac12a_ct^2,\quad v^2=v_0^2+2a_c(s-s_0)
$$

### Forces ([[FEEG1002 D1 - Linear Motion of Particles]])

$$
\sum F=ma\ (\text{inertial frame});\qquad F_g=G\frac{m_1m_2}{r^2},\quad g(y)=g_0\frac{R_e^2}{(R_e+y)^2},\quad v_{esc}=\sqrt{2g_0R_e}=11.2\ \text{km/s}
$$

$$
F_s\le\mu_sN\ (\text{check only}),\quad F_k=\mu_kN;\qquad F_e=k(l-l_0);\qquad F_D=\tfrac12\rho_fSC_Dv^2=Cv^2;\qquad F_B=\rho_fV_sg
$$

Terminal velocity: quadratic drag $v_t=\sqrt{mg/C}$, $v=v_t\tanh(gt/v_t)$; linear drag $F-bv=m\dot v$ gives $v=\frac Fb(1-e^{-bt/m})$. Pulleys: cord length from fixed datums is constant; differentiate for $v$ and $a$; a pulley carrying $n$ strands gives $nT$.

### Curvilinear motion ([[FEEG1002 D2 - Curvilinear Motion]])

$$
\text{projectile: }x=x_0+v_0\cos\theta_0\,t,\quad y=y_0+v_0\sin\theta_0\,t-\tfrac12gt^2;\qquad\text{equal heights: }t_f=\frac{2v_0\sin\theta_0}g,\quad R=\frac{v_0^2\sin2\theta_0}{g}
$$

$$
\mathbf v=v\mathbf u_t,\quad\mathbf a=\dot v\,\mathbf u_t+\frac{v^2}\rho\mathbf u_n;\qquad\rho=\frac{\left[1+(dy/dx)^2\right]^{3/2}}{|d^2y/dx^2|};\qquad\sum F_t=ma_t,\ \sum F_n=\frac{mv^2}\rho,\ \sum F_b=0
$$

Circle: $v=R\omega$, $a_t=R\alpha$, $a_n=R\omega^2$; constant $\alpha$: $\omega=\omega_0+\alpha t$, $\theta=\theta_0+\omega_0t+\tfrac12\alpha t^2$, $\omega^2=\omega_0^2+2\alpha(\theta-\theta_0)$. Relative motion (translating axes): $\mathbf v_B=\mathbf v_A+\mathbf v_{B/A}$, $\mathbf a_B=\mathbf a_A+\mathbf a_{B/A}$. Pendulum: $T=mg(3\cos\theta-2\cos\theta_0)$, small swings $T_{period}=2\pi\sqrt{L/g}$.

### Work, energy, power ([[FEEG1002 D3 - Work, Energy and Power]])

$$
U_{1-2}=\int\mathbf F\cdot d\mathbf r=\int F_t\,ds;\qquad KE_1+V_{g1}+V_{e1}+\sum U_{1-2}^{nc}=KE_2+V_{g2}+V_{e2},\quad KE=\tfrac12mv^2
$$

$$
V_g=mgy\ \ \text{or}\ \ -\frac{Gm_1m_2}{r};\qquad V_e=\tfrac12k(l-l_0)^2;\qquad U_{friction}=-\mu_kNs;\qquad P=\mathbf F\cdot\mathbf v,\quad\eta=\frac{P_o}{P_i}
$$

Loop of radius $R$: $v_{top}\ge\sqrt{gR}$, so $v_{bottom}\ge\sqrt{5gR}$.

### Linear impulse and momentum ([[FEEG1002 D4 - Linear Impulse and Momentum]])

$$
m\mathbf v_1+\sum\int_{t_1}^{t_2}\mathbf F\,dt=m\mathbf v_2;\qquad F_{avg}=\frac{\int F\,dt}{\Delta t};\qquad\text{no external impulse: }\sum m_i\mathbf v_{i1}=\sum m_i\mathbf v_{i2}
$$

$$
e=\frac{v_{B2}-v_{A2}}{v_{A1}-v_{B1}};\qquad v_{A2}=\frac{(m_A-em_B)v_{A1}+m_B(1+e)v_{B1}}{m_A+m_B},\quad v_{B2}=\frac{m_A(1+e)v_{A1}+(m_B-em_A)v_{B1}}{m_A+m_B}
$$

$$
\Delta KE=\tfrac12\frac{m_Am_B}{m_A+m_B}(1-e^2)(v_{A1}-v_{B1})^2;\qquad\text{Galilean cannon: }h\le9h_0\ (e=1,\ m_B\ll m_A),\quad h=[e(e+2)]^2h_0
$$

### Angular impulse and momentum ([[FEEG1002 D5 - Angular Impulse and Momentum]])

$$
\mathbf H_O=\mathbf r\times m\mathbf v,\quad H_O=mvd=mv'r;\qquad\sum\mathbf M_O=\dot{\mathbf H}_O\ (\text{O fixed});\qquad(\mathbf H_O)_1+\sum\int\mathbf M_O\,dt=(\mathbf H_O)_2
$$

Central force about its centre: $r_1v_1'=r_2v_2'$. Orbit (apses): $v_Ar_A=v_Br_B$ with $\tfrac12v^2-GM/r$ constant, giving $v_B=\dfrac{2GM}{v_Ar_A}-v_A$.

### SDOF vibration ([[FEEG1002 D6 - Single Degree of Freedom Vibration]])

$$
m\ddot x+c\dot x+kx=f(t),\qquad\omega_n=\sqrt{\frac km}=\sqrt{\frac g\delta},\quad f_n=\frac{\omega_n}{2\pi},\quad c_{crit}=2\sqrt{km},\quad\zeta=\frac{c}{c_{crit}},\quad\omega_d=\omega_n\sqrt{1-\zeta^2}
$$

$$
x=x_0\cos\omega_nt+\frac{\dot x_0}{\omega_n}\sin\omega_nt\ \ (\dot x_0=J/m);\qquad\zeta<1:\ x=e^{-\zeta\omega_nt}(A_1\cos\omega_dt+A_2\sin\omega_dt)
$$

$$
\zeta=1:\ x=(A_1+A_2t)e^{-\omega_nt};\qquad\zeta>1:\ x=A_1e^{s_1t}+A_2e^{s_2t},\ s_{1,2}=-\omega_n\left(\zeta\mp\sqrt{\zeta^2-1}\right)
$$

$$
\Delta=\frac1n\ln\frac{x_1}{x_{n+1}}=\frac{2\pi\zeta}{\sqrt{1-\zeta^2}}\approx2\pi\zeta
$$

$$
\frac XF=\frac{1}{k-\omega^2m+j\omega c}\approx\frac1k\ (\omega\ll\omega_n),\ \ \frac{1}{j\omega c}\ (\omega\approx\omega_n),\ \ -\frac{1}{\omega^2m}\ (\omega\gg\omega_n);\qquad f=m_\varepsilon\varepsilon\omega^2e^{j\omega t}
$$

Equivalent springs: $EA/L$, $3EI/L^3$ (cantilever tip), $48EI/L^3$ (simply supported, midspan), $192EI/L^3$ (fixed-fixed, midspan), $GA/L$, $GJ/L$, $Gd^4/8D^3n$; parallel $k_1+k_2$, series $(1/k_1+1/k_2)^{-1}$. Resonance frequency (peak of $|X/F|$) is slightly below $\omega_n$.

### Rigid-body kinematics ([[FEEG1002 D7 - Kinematics of Rigid Bodies]])

$$
v=\omega r,\quad a_t=\alpha r,\quad a_n=\omega^2r;\qquad\mathbf v_B=\mathbf v_A+\boldsymbol\omega\times\mathbf r_{B/A};\qquad v_P=\omega r_{P/IC}
$$

Rolling without slip: $s_G=r\theta$, $v_G=r\omega$, $a_G=r\alpha$; contact point $v=0$, $a=r\omega^2$ towards the centre. Relative acceleration (not assessed): $\mathbf a_B=\mathbf a_A+\boldsymbol\alpha\times\mathbf r_{B/A}-\omega^2\mathbf r_{B/A}$.

### Rigid-body kinetics ([[FEEG1002 D8 - Kinetics of Rigid Bodies]])

$$
\sum F_x=m(a_G)_x,\quad\sum F_y=m(a_G)_y,\quad\sum M_G=I_G\alpha;\qquad\sum M_P=\bar{\mathbf r}\times m\mathbf a_G+I_G\alpha;\qquad\sum M_O=I_O\alpha\ (\text{fixed axis})
$$

$$
I=\int r^2\,dm,\qquad I_O=I_G+md^2,\qquad I=mk^2
$$

- $I_G$: slender rod $\tfrac1{12}mL^2$ (about an end $\tfrac13mL^2$); disc or solid cylinder $\tfrac12mR^2$; hoop $mR^2$; sphere $\tfrac25mR^2$; plate $\tfrac1{12}m(a^2+b^2)$.
- Rolling: assume no slip ($a_G=r\alpha$), solve, check $F\le\mu_sN$; if it fails use $F=\mu_kN$ with $a_G\ne r\alpha$.
- Impulse and momentum: $H_G=I_G\omega$, $H_P=\bar{\mathbf r}\times m\mathbf v_G+I_G\omega$, $H_O=I_O\omega$ (fixed axis); $(H_P)_1+\sum\int M_P\,dt=(H_P)_2$ with P at G or a fixed point.

### Rigid-body work and energy ([[FEEG1002 D9 - Work and Energy for Rigid Bodies]])

$$
KE=\tfrac12mv_G^2+\tfrac12I_G\omega^2=\tfrac12I_O\omega^2\ (\text{fixed axis})=\tfrac12I_{IC}\omega^2;\qquad U_M=\int M\,d\theta;\qquad U_{slip}=-F_k|x_G-R\theta|
$$

No work: pin reactions at fixed axes, normal forces, friction on a wheel rolling without slip. Rolling race: $v=\sqrt{2gh/(1+k^2/r^2)}$.
