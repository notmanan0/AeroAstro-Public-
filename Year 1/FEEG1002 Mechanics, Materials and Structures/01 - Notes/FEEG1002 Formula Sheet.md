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

### Equilibrium, stress and strain ([[FEEG1002 A1 - Forces, Equilibrium, Stress and Strain]])
$$
\sum F_x = 0,\quad \sum F_y = 0,\quad \sum M = 0;\qquad \sigma = \frac FA,\quad \varepsilon = \frac{\Delta L}{L},\quad \sigma = E\varepsilon,\quad \delta = \frac{FL}{AE},\quad \tau = \frac VA,\quad \tau = G\gamma
$$

### Trusses ([[FEEG1002 A2 - Pin-Jointed Trusses]])
- Static determinacy (2D): $m + r = 2j$.
- Method of joints: $\sum F_x = \sum F_y = 0$ at each joint.
- Method of sections: three unknowns, using moments about the intersection of two of the cut members.
- Member extension $e = FL/AE$, combined graphically in a Williot diagram.

### Shear force and bending moment ([[FEEG1002 A3 - Shear Force and Bending Moment Diagrams]])
$$
\frac{dQ}{dx} = -w,\qquad \frac{dM}{dx} = Q\ \ (\text{so }M_{max}\text{ where }Q = 0),\qquad \text{jump in }M = \text{applied couple}
$$

### Bending ([[FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area]])
$$
\frac MI = \frac\sigma y = \frac ER,\qquad I_{rect} = \frac{bd^3}{12},\quad I_{circle} = \frac{\pi D^4}{64},\quad I = I_G + Ad^2,\quad Z = \frac I{y_{max}}
$$

### Deflection ([[FEEG1002 A5 - Beam Deflection and Macaulay's Method]], [[FEEG1002 A6 - Statically Indeterminate Beams]])
$$
EI\frac{d^2v}{dx^2} = -M(x),\qquad \text{Macaulay: }\langle x - a\rangle^n = 0\text{ for }x < a,\ \text{integrate as }\frac{\langle x - a\rangle^{n+1}}{n+1}
$$

| Case | Maximum deflection | Maximum slope |
|---|---|---|
| Cantilever, tip load $P$ | $PL^3/3EI$ | $PL^2/2EI$ |
| Cantilever, UDL $w$ | $wL^4/8EI$ | $wL^3/6EI$ |
| Simply supported, central $P$ | $PL^3/48EI$ | $PL^2/16EI$ |
| Simply supported, UDL | $5wL^4/384EI$ | $wL^3/24EI$ |

- Propped cantilever with a UDL: prop reaction $3wL/8$.
- Fixed–fixed with a central $P$: end moments $PL/8$.

### Buckling ([[FEEG1002 A7 - Euler Buckling of Struts]])
$$
P_{cr} = \frac{\pi^2EI}{L_e^2},\qquad L_e = L\ (\text{pin–pin}),\ 2L\ (\text{fixed–free}),\ 0.5L\ (\text{fixed–fixed}),\ 0.7L\ (\text{fixed–pin});\qquad \sigma_{cr} = \frac{\pi^2E}{(L_e/k)^2}
$$

### Torsion ([[FEEG1002 A8 - Torsion of Circular Shafts]])
$$
\frac TJ = \frac\tau r = \frac{G\theta}L,\qquad J = \frac{\pi D^4}{32},\quad J_{hollow} = \frac{\pi(D_o^4 - D_i^4)}{32},\qquad P = T\omega
$$

### Shear stress in beams ([[FEEG1002 A9 - Shear Stresses in Beams]])
$$
\tau = \frac{QA'\bar y'}{Ib},\qquad \tau_{max,rect} = \frac32\frac QA,\qquad \tau_{max,circle} = \frac43\frac QA
$$

## Part B: Statics 2

### Pressure vessels ([[FEEG1002 B1 - Stress in Multiple Dimensions and Thin-Walled Pressure Vessels]])
$$
\sigma_{hoop} = \frac{pR}t,\qquad \sigma_{long} = \frac{pR}{2t}\ (\text{cylinder});\qquad \sigma = \frac{pR}{2t}\ (\text{sphere})
$$

### Strain and thermal strain ([[FEEG1002 B2 - Strain in Multiple Dimensions and Thermal Strain]])
$$
\varepsilon_{xx} = \frac{\partial u}{\partial x},\quad \varepsilon_{xy} = \frac12\left(\frac{\partial u}{\partial y} + \frac{\partial v}{\partial x}\right),\quad e_V = \varepsilon_{xx} + \varepsilon_{yy} + \varepsilon_{zz},\qquad \varepsilon_T = \alpha\Delta T,\quad \sigma_{restrained} = -E\alpha\Delta T
$$

### Generalised Hooke's law ([[FEEG1002 B3 - Generalised Hooke's Law]])
$$
\varepsilon_{xx} = \frac1E[\sigma_{xx} - \nu(\sigma_{yy} + \sigma_{zz})] + \alpha\Delta T,\qquad \varepsilon_{xy} = \frac{\sigma_{xy}}{2G},\qquad G = \frac E{2(1+\nu)},\quad K = \frac E{3(1-2\nu)}
$$

Plane stress: $\sigma_{xx} = \dfrac E{1-\nu^2}(\varepsilon_{xx} + \nu\varepsilon_{yy})$.

### Transformation and Mohr's circle ([[FEEG1002 B4 - Stress Transformation and Mohr's Circle]])
$$
\sigma_{x'x'} = \frac{\sigma_{xx} + \sigma_{yy}}2 + \frac{\sigma_{xx} - \sigma_{yy}}2\cos2\theta + \sigma_{xy}\sin2\theta,\qquad \sigma_{x'y'} = -\frac{\sigma_{xx} - \sigma_{yy}}2\sin2\theta + \sigma_{xy}\cos2\theta
$$

$$
\sigma_{I,II} = \frac{\sigma_{xx} + \sigma_{yy}}2\pm\sqrt{\left(\frac{\sigma_{xx} - \sigma_{yy}}2\right)^2 + \sigma_{xy}^2},\qquad \tan2\theta_p = \frac{2\sigma_{xy}}{\sigma_{xx} - \sigma_{yy}},\qquad \tau_{max} = R
$$

### Strain gauges ([[FEEG1002 B5 - Strain Measurement and Strain Rosettes]])
$$
\varepsilon_\theta = \varepsilon_{xx}\cos^2\theta + \varepsilon_{yy}\sin^2\theta + 2\varepsilon_{xy}\sin\theta\cos\theta
$$

- 0/45/90 rosette: $\varepsilon_{xy} = \varepsilon_{45} - \tfrac12(\varepsilon_0 + \varepsilon_{90})$.
- 0/60/120 rosette: $\varepsilon_{yy} = \tfrac13[2(\varepsilon_{60} + \varepsilon_{120}) - \varepsilon_0]$ and $\varepsilon_{xy} = (\varepsilon_{60} - \varepsilon_{120})/\sqrt3$.

### Yield ([[FEEG1002 B6 - Yield Criteria]])
$$
\text{Tresca: }\max|\sigma_i - \sigma_j| = \sigma_Y;\qquad \text{von Mises: }\sigma_{eq} = \sqrt{\sigma_{xx}^2 + \sigma_{yy}^2 - \sigma_{xx}\sigma_{yy} + 3\sigma_{xy}^2} = \sigma_Y
$$

## Part C: Materials

### Crystallography ([[FEEG1002 C2 - Crystal Structures and Crystallography]])

| Structure | Atoms/cell | Contact relation | APF | Stacking / easy slip |
|---|---:|---|---:|---|
| FCC | 4 | $a=2\sqrt2R$ | $\pi/(3\sqrt2)=0.740$ | ABCABC; $\{111\}\langle110\rangle$ |
| BCC | 2 | $a=4R/\sqrt3$ | $\pi\sqrt3/8=0.680$ | no close-packed plane |
| HCP | 6 conventional | close packed | 0.740 | ABAB |

Directions $[uvw]$: lattice-vector components. Planes $(hkl)$: reciprocals of lattice intercepts. Bars denote negative indices; $\langle uvw\rangle$ and $\{hkl\}$ are families. In cubic crystals, $[hkl]\perp(hkl)$.

### Diffusion ([[FEEG1002 C3 - Diffusion]])
$$
J=-D\frac{dC}{dx},\qquad \frac{\partial C}{\partial t}=D\frac{\partial^2C}{\partial x^2},\qquad D=D_0\exp\left(-\frac{Q}{RT}\right),\qquad x\sim\sqrt{Dt}
$$

### Tensile properties ([[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation]])
$$
\sigma=\frac{F}{A_0},\quad \varepsilon=\frac{\Delta L}{L_0},\quad E=\frac{d\sigma}{d\varepsilon},\quad \nu=-\frac{\varepsilon_t}{\varepsilon_a},\quad \sigma_T=\frac{F}{A},\quad \varepsilon_T=\ln\frac{L}{L_0}
$$
$$
U_r=\frac{\sigma_y^2}{2E};\qquad \%CW=\frac{A_0-A_f}{A_0}\times100\%;\qquad \sigma_y=\sigma_0+k_yd^{-1/2}\quad\text{(Hall-Petch)}
$$

### Binary phase diagrams ([[FEEG1002 C6 - Phase Diagrams]])
In an $\alpha+\beta$ field at overall composition $C_0$:
$$
f_\alpha=\frac{C_\beta-C_0}{C_\beta-C_\alpha},\qquad f_\beta=\frac{C_0-C_\alpha}{C_\beta-C_\alpha},\qquad f_\alpha+f_\beta=1
$$

- Eutectic: $L\rightarrow\alpha+\beta$.
- Steel eutectoid near 727°C, 0.76 wt% C: $\gamma\rightarrow\alpha+Fe_3C$ (pearlite); $C_{Fe_3C}=6.70$ wt% C.
- Precipitation hardening: solution treat $\rightarrow$ quench supersaturated solution $\rightarrow$ age to fine precipitates.

### Fracture ([[FEEG1002 C8 - Fracture - Brittle, Ductile and Fracture Mechanics]])
$$
\sigma_m\approx2\sigma_0\sqrt{\frac{a}{\rho_t}},\qquad \sigma_f=\sqrt{\frac{2E\gamma}{\pi a}},\qquad K_I=Y\sigma\sqrt{\pi a}
$$
$$
\text{fracture: }K_I=K_{IC};\qquad \sigma_f=\frac{K_{IC}}{Y\sqrt{\pi a}},\qquad a_c=\frac1\pi\left(\frac{K_{IC}}{Y\sigma}\right)^2
$$

### Fatigue, creep and corrosion ([[FEEG1002 C9 - Fatigue, Creep and Corrosion]])
$$
\Delta\sigma=\sigma_{max}-\sigma_{min},\quad \sigma_a=\frac{\Delta\sigma}{2},\quad \sigma_m=\frac{\sigma_{max}+\sigma_{min}}2,quad N_f=N_i+N_p
$$
$$
\Delta K=Y\Delta\sigma\sqrt{\pi a},\qquad \frac{da}{dN}=A(\Delta K)^m\quad\text{(Paris)}
$$
$$
\dot\varepsilon_s=K_2\sigma^n\exp\left(-\frac{Q_c}{RT}\right)
$$

Anode/oxidation: $M\rightarrow M^{n+}+ne^-$. Cathode/reduction example: $2H^++2e^-\rightarrow H_2$.

### Polymers ([[FEEG1002 C10 - Polymers - Structure and Mechanics]])
$$
M_n=\sum x_iM_i,\qquad M_w=\sum w_iM_i,qquad \sigma(t)=\sigma_0e^{-t/\tau},\qquad E_r(t)=\frac{\sigma(t)}{\varepsilon_0}
$$

- $T<T_g$: glassy/brittle; $T_g<T<T_m$: viscoelastic/rubbery; near $T_m$: viscous flow.
- Thermoplastic: linear/branched; elastomer: lightly crosslinked; thermoset: 3D covalent network.

### Continuous aligned composites ([[FEEG1002 C11 - Ceramics and Composites]])
$$
V_f+V_m=1;qquad E_L=V_fE_f+V_mE_m\quad(\varepsilon_f=\varepsilon_m);\qquad \frac1{E_T}=\frac{V_f}{E_f}+\frac{V_m}{E_m}\quad(\sigma_f=\sigma_m)
$$

## Part D: Dynamics

### Particle kinematics ([[FEEG1002 D1 - Linear Motion of Particles]], [[FEEG1002 D2 - Curvilinear Motion]])
$$
v = \dot s,\quad a = \dot v = v\frac{dv}{ds};\qquad v = v_0 + at,\quad s = s_0 + v_0t + \tfrac12at^2,\quad v^2 = v_0^2 + 2a\Delta s\ \ (a\text{ constant})
$$

$$
\text{Projectile: }y = y_0 + \tan\theta_0\,x - \frac{gx^2}{2v_0^2\cos^2\theta_0},\quad R = \frac{v_0^2\sin2\theta_0}g;\qquad \mathbf a = \dot v\mathbf u_t + \frac{v^2}\rho\mathbf u_n,\quad \rho = \frac{[1 + y'^2]^{3/2}}{|y''|}
$$

Circular path: $v = r\omega$, $a_t = r\alpha$, $a_n = r\omega^2$.

### Forces ([[FEEG1002 D1 - Linear Motion of Particles]])
$$
F_g = \frac{Gm_1m_2}{r^2},\quad g(y) = g_0\frac{R_e^2}{(R_e + y)^2},\quad F_s\le\mu_sN,\quad F_k = \mu_kN,\quad F_e = k\Delta l,\quad F_D = \tfrac12\rho SC_Dv^2,\quad F_B = \rho_fV_sg
$$

Terminal velocity: $v_t = \sqrt{mg/c}$. Pulleys: total cord length = const, differentiated for $v$ and $a$.

### Work, energy, power ([[FEEG1002 D3 - Work, Energy and Power]])
$$
U = \int\mathbf F\cdot d\mathbf r,\quad U_M = \int M\,d\theta;\qquad KE_1 + V_1 + \sum U^{nc} = KE_2 + V_2;\qquad V_g = mgy\ \text{or}\ -\frac{GMm}r,\quad V_e = \tfrac12k\Delta l^2
$$

$$
P = \mathbf F\cdot\mathbf v = M\omega,\qquad \eta = \frac{P_{out}}{P_{in}}
$$

### Impulse and momentum ([[FEEG1002 D4 - Linear Impulse and Momentum]], [[FEEG1002 D5 - Angular Impulse and Momentum]])
$$
m\mathbf v_1 + \sum\int\mathbf F\,dt = m\mathbf v_2;\qquad e = \frac{v_{B2} - v_{A2}}{v_{A1} - v_{B1}};\qquad \mathbf H_O = \mathbf r\times m\mathbf v,\quad (H_O)_1 + \sum\int M_O\,dt = (H_O)_2
$$

$$
v_{A2} = \frac{m_A - em_B}{m_A + m_B}v_{A1} + \frac{m_B(1+e)}{m_A + m_B}v_{B1},\qquad v_{B2} = \frac{m_A(1+e)}{m_A + m_B}v_{A1} + \frac{m_B - em_A}{m_A + m_B}v_{B1}
$$

Central force: $r_1v_{1\perp} = r_2v_{2\perp}$.

### SDOF vibration ([[FEEG1002 D6 - Single Degree of Freedom Vibration]])
$$
m\ddot x + c\dot x + kx = f(t),\qquad \omega_n = \sqrt{\frac km} = \sqrt{\frac g{\delta_{st}}},\quad f_n = \frac{\omega_n}{2\pi},\quad \zeta = \frac c{2\sqrt{km}},\quad \omega_d = \omega_n\sqrt{1 - \zeta^2}
$$

$$
x = x_0\cos\omega_nt + \frac{\dot x_0}{\omega_n}\sin\omega_nt;\qquad x = Xe^{-\zeta\omega_nt}\cos(\omega_dt - \phi);\qquad \Delta = \frac1n\ln\frac{x_1}{x_{n+1}}\approx2\pi\zeta
$$

$$
\frac XF = \frac1{k - \omega^2m + j\omega c}\quad(\approx1/k,\ 1/j\omega c,\ -1/\omega^2m);\qquad \text{unbalance: }f = m_\varepsilon\varepsilon\omega^2e^{j\omega t}
$$

Equivalent springs: $EA/L$, $3EI/L^3$, $GJ/L$, $Gd^4/8D^3n$; parallel $k_1 + k_2$; series $(1/k_1 + 1/k_2)^{-1}$.

### Rigid bodies ([[FEEG1002 D7 - Kinematics of Rigid Bodies]], [[FEEG1002 D8 - Kinetics of Rigid Bodies]], [[FEEG1002 D9 - Work and Energy for Rigid Bodies]])
$$
\mathbf v_B = \mathbf v_A + \boldsymbol\omega\times\mathbf r_{B/A},\quad \mathbf a_B = \mathbf a_A + \boldsymbol\alpha\times\mathbf r_{B/A} - \omega^2\mathbf r_{B/A},\quad v_P = \omega r_{P/IC};\quad \text{no slip: }v_G = r\omega,\ a_G = r\alpha
$$

$$
\sum\mathbf F = m\mathbf a_G,\quad \sum M_G = I_G\alpha,\quad \sum M_O = I_O\alpha\ (\text{fixed axis});\qquad I_O = I_G + md^2,\quad I = mk^2
$$

- $I_G$: rod $\tfrac1{12}mL^2$ (end $\tfrac13mL^2$); disc $\tfrac12mr^2$; hoop $mr^2$; sphere $\tfrac25mr^2$; plate $\tfrac1{12}m(a^2 + b^2)$.
- Kinetic energy: $KE = \tfrac12mv_G^2 + \tfrac12I_G\omega^2 = \tfrac12I_{IC}\omega^2$.
- Rolling on an incline needs $\mu_s\ge\tan\theta\,\dfrac{k^2}{k^2 + r^2}$.
