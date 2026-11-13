---
title: "SESA3029 Past Paper 2024-25 B - Solutions"
module: "SESA3029 Aerothermodynamics"
type: past-paper-solutions
tags: [sesa3029, past-paper, solutions, oblique-shock, shock-expansion, ackeret, prandtl-glauert, moc, heat-exchanger, finite-difference]
paper: "2024-25 Paper B (Open Book)"
theory_notes: ["[[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes]]", "[[SESA3029 W02 - Oblique Shock Relations and Mach Waves]]", "[[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method]]", "[[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow]]", "[[SESA3029 W05a - Method of Characteristics]]", "[[SESA3029 W05b - Minimum-Length Nozzle Design]]", "[[SESA3029 W07b - Compressible Potential Flow and the Prandtl-Glauert Transformation]]", "[[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils]]"]
status: complete
sources: ["03 - Exams & Past Papers/Past Papers/Southampton/SESA3029-202425-01-SESA3029-B.pdf"]
---

# SESA3029 Past Paper 2024-25 B - Solutions

> [!abstract] Paper info
> 2024-25 Paper B is the open-book version of [[SESA3029 Past Paper 2024-25 A - Solutions|Paper A]]: 120 minutes plus 30 minutes for upload, handwritten, with five questions worth 34, 14, 20, 16 and 16 marks. Full working must be shown and answers must come from formulas and charts. The front-page constants are the same as Paper A. Questions 1–4 and Q5(i) are word for word the same as Paper A; only the marks change, on Q2(ii) (6 instead of 8) and Q4(i)–(ii) (4 + 4 instead of 6 + 6). Their full working is in the Paper A note, and each section below links to it and lists the answers. Q5(ii) is new to this paper and repeats [[SESA3029 Past Paper 2023-24 - Solutions#Q1. Short-answer aerothermodynamics questions (40 marks)|2023-24 Q1(ix)]]; it is worked in full here. Questions 4 and 5 are heat transfer (Weeks 9–12, not yet lectured).

| Q | Marks | Topic | Theory |
|---|---:|---|---|
| 1 | 34 | Nozzle, shock reflection, shock-expansion, pitching moment, Ackeret | [[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes|W01]], [[SESA3029 W02 - Oblique Shock Relations and Mach Waves|W02]], [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method|W03]], [[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils|W07c]] |
| 2 | 14 | Prandtl–Glauert derivation and critical Mach number | [[SESA3029 W07b - Compressible Potential Flow and the Prandtl-Glauert Transformation|W07b]] |
| 3 | 20 | Method of Characteristics for an under-expanded nozzle jet | [[SESA3029 W05a - Method of Characteristics|W05a]] |
| 4 | 16 | Shell-and-tube heat exchanger ($\varepsilon$–NTU, Dittus–Boelter) | Heat transfer (Weeks 9–12, not yet lectured) |
| 5 | 16 | 2D internal-corner FD stencil and 1D radial cylindrical FD equation | Heat transfer (Weeks 9–12, not yet lectured) |

---

## Q1. Nozzle flow, wall shock reflection and half-diamond aerofoil (34 marks)

> The same question as [[SESA3029 Past Paper 2024-25 A - Solutions#Q1. Nozzle flow, wall shock reflection and half-diamond aerofoil (34 marks)|2024-25 Paper A Q1]]: $M_1=2.4$, $p_1=55\ \text{kPa}$, $T_1=170\ \text{K}$, half-diamond aerofoil with $l=0.2\ \text{m}$ and $\phi=12^\circ$, marks $4+10+8+4+8$.

![[at_pp_202425_q1_wave_reflection.png|900]]

The full working, with the θ–β–M trial tables, the NST and IFT interpolations and the derivation of the moment and linearised Mach-number formulas, is in the Paper A note, and the answers are listed below.

| Part | Quantity | Answer |
|---|---|---|
| (i) | reservoir $p_0$, $T_0$ | 804.1 kPa, 365.8 K |
| (i) | throat $p_t$, $T_t$ | 424.8 kPa, 304.9 K |
| (ii) | incident shock: $\beta_1$, $M_2$, $p_2$ | $35.01^\circ$, 1.918, 112.5 kPa |
| (ii) | reflected shock: $\beta_2$ (from the region-2 flow), angle to wall | $43.45^\circ$, $31.45^\circ$ |
| (ii) | after reflection: $M_3$, $p_3$ | 1.488, 209.6 kPa |
| (iii) | surface A: $M_A$, $p_A$ | 1.918, 112.5 kPa |
| (iii) | surface B: $M_B$, $p_B$ | 2.40, 55.0 kPa |
| (iii) | surface C ($24^\circ$ expansion): $M_C$, $p_C$ | 3.643, 8.62 kPa |
| (iv) | $M'_{\text{LE}}=\frac{l^2}{8}(4p_A-p_B-3p_C)$ | $+1845$ N m/m (nose-up) |
| (v) | Ackeret A: $p_A$, $M_A$ | 97.6 kPa, 1.90 |
| (v) | Ackeret B: $p_B$, $M_B$ | 55.0 kPa, 2.40 |
| (v) | Ackeret C: $p_C$, $M_C$ | $-30.2$ kPa (impossible), 3.39 |

Ackeret theory needs the pressure perturbation $\gamma M_\infty^2|\theta|/\sqrt{M_\infty^2-1}$ to be small compared with 1. It is 0.77 on A, where the pressure comes out 13 % low, and 1.55 on C, where the predicted drop exceeds the free-stream pressure.

---

## Q2. Prandtl-Glauert derivation and critical Mach number (14 marks)

> The same question as [[SESA3029 Past Paper 2024-25 A - Solutions#Q2. Prandtl-Glauert derivation and critical Mach number (16 marks)|2024-25 Paper A Q2]] ($C_{p,\min}=-1.2$), with marks $8+6$ instead of $8+8$.

![[at_pp_202425_q2_mcrit.png|900]]

The derivation in (i) and the trial table for (ii) are in the Paper A note. Part (i) ends at

$$
C_p=\frac{C_{p,0}}{\sqrt{1-M_\infty^2}},
$$

and part (ii) gives $M_{\text{crit}}=\boxed{0.575}$ (root 0.5748, where both sides equal $C_p=-1.4664$).

---

## Q3. Method of Characteristics for an under-expanded nozzle exit (20 marks)

> The same question as [[SESA3029 Past Paper 2024-25 A - Solutions#Q3. Method of Characteristics for an under-expanded nozzle exit (20 marks)|2024-25 Paper A Q3]] (marks $14+6$).

![[at_pp_202425_q3_moc_expansion.png|900]]

The table and the IFT interpolations are worked in the Paper A note. The completed table, with $R^+=\nu-\theta$ and $R^-=\nu+\theta$, is below.

| Point | $R^+$ | $R^-$ | $\theta$ | $\nu$ |
|---|---|---|---|---|
| a (line) | $\nu_a$ | $\nu_a$ | $0$ | $\nu_a$ |
| b (line) | $\nu_a$ | $2\nu_b-\nu_a$ | $\nu_b-\nu_a$ | $\nu_b$ |
| 1 | $\nu_a$ | $\nu_a$ | $0$ | $\nu_a$ |
| 2 | $\nu_a$ | $2\nu_b-\nu_a$ | $\nu_b-\nu_a$ | $\nu_b$ |
| 3 | $2\nu_b-\nu_a$ | $2\nu_b-\nu_a$ | $0$ | $2\nu_b-\nu_a$ |

The printed zeros in the $R^+$ column correspond to invariants measured from the exit state, $(\nu-\nu_a)\mp\theta$; see the Paper A slips. For part (ii), $p_0=200/0.2724=734.2$ kPa, $p_b/p_0=0.1360$ gives $M_b=1.96$ and $\nu_b=25.2711^\circ$, and $\nu_3=2\times25.2711^\circ-11.9052^\circ=38.637^\circ$, so $M_3=\boxed{2.48}$ and $p_3=\boxed{44.4\ \text{kPa}}$.

---

## Q4. Shell-and-tube heat exchanger (16 marks)

> The same question as [[SESA3029 Past Paper 2024-25 A - Solutions#Q4. Shell-and-tube heat exchanger (20 marks)|2024-25 Paper A Q4]], with marks $4+4+8$ instead of $6+6+8$.

This is heat transfer (Weeks 9–12, not yet lectured). The working is in the Paper A note, and the answers are listed below.

| Part | Quantity | Answer |
|---|---|---|
| (i) | $C_r$, NTU, $\epsilon$ | 0.18499, 1.8906, 0.818 |
| (ii) | $\dot Q$ | 760.6 kW |
| (ii) | $T_{h,\text{out}}$, $T_{c,\text{out}}$ | $48.6^\circ$C, $43.0^\circ$C |
| (iii) | $Re_D$, $Nu_D$ | 5736, 47.30 |
| (iii) | $h_i$ | 2320 W/(m² K) |

---

## Q5. Finite-difference stencils for 2D internal corner and 1D radial cylindrical conduction (16 marks)

This is heat transfer (Weeks 9–12, not yet lectured); check the notation against those lectures when they are written up.

### (i) Internal corner with boundary heat flux [10 marks]

> The same question as [[SESA3029 Past Paper 2024-25 A - Solutions#Q5. Finite-difference stencil at an internal corner with boundary heat flux (10 marks)|2024-25 Paper A Q5]].

![[at_pp_202425_q5_internal_corner.png|750]]

The face-by-face energy balance on the three-quarter control volume is in the Paper A note. It gives the stencil

$$
6T_P=2T_N+2T_W+T_E+T_S+\frac{2\dot q\,\Delta x}{k},
$$

and with $2\dot q\,\Delta x/k=2\times50\times0.04/0.05=80$ K,

$$
T_P=\frac{2\times240+2\times250+360+380+80}{6}=\frac{1800}{6}=\boxed{300^\circ\text{C}}.
$$

### (ii) 1D radial cylindrical finite-difference equation [6 marks]

> Consider steady 1D radial heat conduction with no volumetric generation. Using the radial heat flux $\dot q_r=-2\pi k r\,\dfrac{\partial T}{\partial r}$, derive the finite-difference equation for $T_i$ at an interior node $i$ of the equidistant radial grid in Figure Q5.2, where $r_i=i\,\Delta r$.

Because of the $2\pi r$ factor, $\dot q_r$ is the heat flow per unit axial length through a cylinder of radius $r$, in W/m. The control volume around node $i$ is the annulus between the faces midway to the neighbouring nodes,

$$
r_{i-1/2}=\left(i-\tfrac12\right)\Delta r,\qquad r_{i+1/2}=\left(i+\tfrac12\right)\Delta r.
$$

In steady state with no generation, the heat flowing in through the inner face equals the heat flowing out through the outer face,

$$
\dot q_{r,\,i-1/2}-\dot q_{r,\,i+1/2}=0.
$$

The temperature gradient at each face is the central difference between the nodes on either side of it. At the inner face,

$$
\dot q_{r,\,i-1/2}=-2\pi k\left(i-\tfrac12\right)\Delta r\,\frac{T_i-T_{i-1}}{\Delta r}=-2\pi k\left(i-\tfrac12\right)(T_i-T_{i-1}).
$$

At the outer face,

$$
\dot q_{r,\,i+1/2}=-2\pi k\left(i+\tfrac12\right)\Delta r\,\frac{T_{i+1}-T_i}{\Delta r}=-2\pi k\left(i+\tfrac12\right)(T_{i+1}-T_i).
$$

Substituting both into the balance,

$$
-2\pi k\left(i-\tfrac12\right)(T_i-T_{i-1})+2\pi k\left(i+\tfrac12\right)(T_{i+1}-T_i)=0.
$$

Dividing by $2\pi k$,

$$
-\left(i-\tfrac12\right)(T_i-T_{i-1})+\left(i+\tfrac12\right)(T_{i+1}-T_i)=0.
$$

Expanding the brackets,

$$
\left(i-\tfrac12\right)T_{i-1}-\left(i-\tfrac12\right)T_i-\left(i+\tfrac12\right)T_i+\left(i+\tfrac12\right)T_{i+1}=0.
$$

The two $T_i$ coefficients add to $2i$,

$$
\left(i-\tfrac12\right)T_{i-1}-2i\,T_i+\left(i+\tfrac12\right)T_{i+1}=0.
$$

Solving for $T_i$,

$$
\boxed{T_i=\frac{\left(i-\tfrac12\right)T_{i-1}+\left(i+\tfrac12\right)T_{i+1}}{2i}}.
$$

The outer neighbour has the larger weight because the outer face has the larger area. Far from the axis ($i\gg1$) the weights approach $\tfrac12$ each and the equation becomes the planar result $T_i=(T_{i-1}+T_{i+1})/2$.

> [!check] Consistency with the differential equation
> Regrouping the balance as $i\,(T_{i+1}-2T_i+T_{i-1})+\tfrac12(T_{i+1}-T_{i-1})=0$ and dividing by $i\,\Delta r^2$ with $r_i=i\,\Delta r$ gives $\dfrac{T_{i+1}-2T_i+T_{i-1}}{\Delta r^2}+\dfrac{1}{r_i}\dfrac{T_{i+1}-T_{i-1}}{2\Delta r}=0$. This is the second-order central-difference form of $\dfrac{1}{r}\dfrac{\mathrm{d}}{\mathrm{d}r}\left(r\dfrac{\mathrm{d}T}{\mathrm{d}r}\right)=\dfrac{\mathrm{d}^2T}{\mathrm{d}r^2}+\dfrac{1}{r}\dfrac{\mathrm{d}T}{\mathrm{d}r}=0$.

---

## Paper slips and ambiguities

- Q3(i) and Q4(i) have the same issues as Paper A: the printed $R^+=0$ entries, and a double-pass exchanger paired with the counterflow effectiveness relation. See [[SESA3029 Past Paper 2024-25 A - Solutions#Paper slips and ambiguities|2024-25 Paper A]].
- Q5(ii): the question calls $\dot q_r=-2\pi kr\,\partial T/\partial r$ a heat flux, but the $2\pi r$ factor makes it a heat flow per unit length (W/m). That is what makes $\dot q_r$ the same through every radius in steady state, so the derivation uses it directly.
- Corrections to the earlier draft: the Q4(iii) intermediate values are $Re_D^{0.8}=1016.0$ and $\text{Pr}^{0.4}=2.0243$ ($Nu_D=47.30$ was right), and the Ackeret validity test is now the pressure-perturbation ratio rather than $M_\infty|\theta|\ll1$; see the Paper A slips.
