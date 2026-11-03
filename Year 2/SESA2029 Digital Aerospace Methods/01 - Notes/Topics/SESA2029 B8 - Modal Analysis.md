---
title: "SESA2029 B8 - Modal Analysis"
module: "SESA2029 Digital Aerospace Methods"
type: topic
stream: "Part B: Finite Element Analysis"
order: 19
tags: [sesa2029, fea, modal-analysis, vibration]
aliases: ["FE modal analysis", "Natural frequencies", "Eigen analysis", "FEA Lecture 10"]
date: 2026-10-30
status: lectured
coverage: "FEA week 5 (2026-02-27 10:55)"
parent: ["[[SESA2029 Digital Aerospace Methods Hub]]"]
prerequisites: ["[[SESA2029 B7 - Meshing, Convergence and Mesh Checks]]"]
next_topics: ["[[SESA2029 B9 - Nonlinear FE Analysis]]"]
key_concepts: ["[[Natural Frequencies and Mode Shapes]]", "[[Participation Factor and Effective Mass]]", "[[Damping Ratio and Natural Frequency]]", "[[Characteristic Equation and Eigenvalues]]"]
tutorial_sheets: ["[[SESA2029 FEA Worked Examples]]"]
sources: ["02 - Sources/FEM Lectures/Lecture_10_Modal_Analysis_2_final(1).pdf", "02 - Sources/Lectures/SESA2029 Lecture 2026-02-27 - 1055.txt"]
---

# SESA2029 B8 - Modal Analysis

> [!abstract] Summary
> Aerospace structures carry time-varying loads from gusts, engines and separated flow, and when an excitation frequency matches a natural frequency the response is amplified by resonance. Modal analysis solves the undamped free-vibration eigenproblem $([K]-\omega_i^2[M])\{\phi\}_i=0$: the eigenvalues give the natural frequencies $f_i=\omega_i/2\pi$ and the eigenvectors the mode shapes, whose amplitude is arbitrary. Participation factors $\gamma_i=\{\phi\}_i^T[M]\{D\}$ and effective masses $\gamma_i^2$ (for mass-normalised modes) show which modes a base excitation drives and whether enough modes have been extracted.

> [!summary]- Exam use: quick path
> - **Use it when:** asked for the natural frequencies and modes of a small spring–mass or beam model, what controls them, or which mode a base excitation excites.
> - **Assumptions:** linear elastic, constant $[M]$ and $[K]$, no applied loads, no damping, harmonic motion.
> - **Method:** 1. Assemble $[M]$ and $[K]$. 2. Solve $\det([K]-\omega^2[M])=0$ for $\omega^2$. 3. Back-substitute for each mode shape and mass-normalise. 4. $\gamma=\Phi^T[M]\{D\}$ with $\{D\}$ a unit vector in the excitation direction. 5. $M_{\mathrm{eff},i}=\gamma_i^2$; extract modes until their sum passes 90 % of the total mass.
> - **Common mistakes:** reading physical deflections or stresses from a mode shape; forgetting density, so $[M]=0$ and no modes appear.
> - **Practise:** [[#Worked example: a two-DOF spring–mass system]]

Most of the class had not met vibration before, so this lecture builds it from the start; the aircraft structures course next year goes further with one- and two-DOF systems, while here FE is the tool that extends modal analysis to complex structures (2026-02-27 10:55, ll. 1–20).

Disturb a guitar string or a diving board and it vibrates at a few particular frequencies, each with its own shape: the board's tip bobbing, a node half-way along, a twist. Those frequencies and shapes belong to the structure, fixed by its stiffness and mass, not by whatever disturbed it. Push the structure periodically at one of them and every push adds to the motion, which is resonance; push it away from them and little happens. Modal analysis finds those frequencies and shapes so the design can keep the excitation away from them.

## 1. Why dynamics matters in aerospace

Videos opened the lecture (ll. 21–35): an engine shaking its wing, because a rotating engine has a wide range of excitation frequencies; tail flutter, a self-excited flow–structure interaction in which, above the flutter speed, the system's damping becomes negative and the oscillation grows until the structure fails; and a highly flexible wing in a wind tunnel settling into limit-cycle oscillations because of nonlinearity.

Aerospace structures see time-varying loads from gusts, from engines whose rotation speed sets the excitation frequency, and from turbulence and flow separation (ll. 36–60). Vibration is oscillation about an equilibrium, so the usual procedure is a static analysis for the equilibrium, then the dynamic loads on top. When an excitation frequency matches a natural frequency, a large response occurs that affects fatigue life, noise, performance and safety. The Tacoma Narrows bridge, which tore itself apart in a steady 35 mph wind in 1940, is the classic example; the destructive motion was a torsional mode, probably the third rather than the first (ll. 61–100). For a fan blade, the natural frequencies are computed first and the operating speeds chosen so that the excitation does not match any of them (ll. 76–90).

Modal analysis has two aims: the natural frequencies at which the structure tends to vibrate, and the mode shapes, the deformed shape at each (ll. 86–100). Two modes close together, such as a bending and a torsion mode, are dangerous for aeroelastic stability, and lightweight composite structures make this common, because low mass makes the natural-frequency spectrum dense (ll. 101–110). Vibration can also be put to use, as in energy harvesters tuned to vibrate at a chosen frequency (ll. 111–120).

## 2. The eigenvalue problem

Assume a linear elastic structure, so $[M]$ and $[K]$ are constant, with no applied loads, in free, undamped vibration (ll. 121–130):

$$
[M]\{\ddot u\}+[K]\{u\}=\{0\}.
$$

For two DOF, $[M]$ is $2\times2$ with the masses on the diagonal, and $[K]$ is the stiffness matrix of the static analyses. Assume harmonic motion with amplitude vector $\{\phi\}_i$, circular frequency $\omega_i$ and phase $\theta_i$ (ll. 131–140):

$$
\{u\}=\{\phi\}_i\sin(\omega_it+\theta_i).
$$

Differentiate twice:

$$
\{\ddot u\}=-\omega_i^2\{\phi\}_i\sin(\omega_it+\theta_i).
$$

Substitute both into the equation of motion:

$$
\left(-\omega_i^2[M]\{\phi\}_i+[K]\{\phi\}_i\right)\sin(\omega_it+\theta_i)=\{0\}.
$$

This must hold at all times, so the bracket vanishes:

$$
\boxed{\left([K]-\omega_i^2[M]\right)\{\phi\}_i=\{0\}}
$$

A non-zero $\{\phi\}_i$ requires the matrix to be singular, $\det([K]-\omega^2[M])=0$. The eigenvalues are the squares of the natural circular frequencies, in rad/s; the natural frequency and period are

$$
f_i=\frac{\omega_i}{2\pi}\ \text{(Hz)},
\qquad
T_i=\frac1{f_i}
$$

(ll. 136–150). A model with $n$ DOF has $n$ natural frequencies, but usually only the first few, typically six, matter because they represent most of the dynamic motion. The eigenvector $\{\phi\}_i$ is the mode shape at $f_i$ ([[Natural Frequencies and Mode Shapes]]). MATLAB and Python libraries solve the problem directly, and Dr Yuan extracts FE matrices to do so in his research, using the modes for control, vibration mitigation and reduced-order models (ll. 151–165).

The eigenvector's amplitude is arbitrary, so it is normalised (ll. 166–185): to the mass matrix, $\{\phi\}_i^T[M]\{\phi\}_i=1$, which is what ANSYS reports, or to unity, with the largest component set to one. What matters is the shape, first bending, second bending or torsion, not the numbers. A first estimate of the lowest frequency treats the structure as a single spring and mass, $\omega_0\approx\sqrt{k/m}$ (ll. 211–215).

The slides' appendix (slides 22–25, not presented in the lecture) recaps the damped single-DOF system $m\ddot x+c\dot x+kx=f(t)$, written as $\ddot x+2\zeta\omega_0\dot x+\omega_0^2x=0$ with $\omega_0=\sqrt{k/m}$ and damping ratio $\zeta=c/(2m\omega_0)$ (the slides use $\varepsilon$); for $\zeta<1$ the roots are $-\zeta\omega_0\pm i\omega_0\sqrt{1-\zeta^2}$, with damped natural frequency $\omega_d=\omega_0\sqrt{1-\zeta^2}$, and the pair $(\omega_0,\zeta)$ is the system's modal model ([[Damping Ratio and Natural Frequency]]).

## 3. What controls the natural frequencies

Natural frequencies and mode shapes depend on stiffness, mass and boundary conditions (ll. 246–270). Stiffness depends on geometry and material, so changing a beam's section or material changes its frequencies, and higher stiffness means higher frequencies. More mass means lower frequencies; for the first mode it is the ratio $k/m$ that counts. Lightweight structures have little inertia and dense, low spectra, which is why modal analysis is so important for modern aircraft and spacecraft. A clamped support restrains more than a simple support, which still allows rotation, so a clamped structure is stiffer and has higher natural frequencies, as the lab 1 beam models can show.

The lecture's research example is a highly flexible wing built with third-year individual-project students: an aluminium plate spar, a 3D-printed aerofoil shell and tip rods, mounted on an optical table for ground vibration testing (ll. 186–215). The FE model of the assembly gives:

| Mode | Frequency (Hz) |
|---|---|
| 1st bending | 4.2 |
| 2nd bending | 28.5 (slide) |
| 1st torsion | 40.7 |
| 3rd bending | 82.3 |

For aeroelasticity the second bending and first torsion modes matter most: as the airspeed increases, aerodynamic stiffness and damping move their frequencies together until they merge and the overall damping becomes negative, and flutter starts. The linear modal properties must be right and validated first.

Validation uses vibration tests (ll. 221–250). In a hammer test, the structure is struck at many points, the response is transformed by FFT into a spectrum whose peaks are the resonances, and the responses at the different points are joined into the experimental mode shapes. In a shaker test, a signal generator drives an electrodynamic shaker through a sweep of frequencies, and the wing visibly resonates at each mode. If test and FE differ, the model is updated ([[Model Updating]]; [[SESA2029 B10 - FE Verification, Validation and Model Updating|B10]]).

## 4. Participation factor and effective mass

The participation factor measures how strongly a mode contributes to the response in a given direction (ll. 266–280; [[Participation Factor and Effective Mass]]):

$$
\gamma_i=\{\phi\}_i^T[M]\{D\},
$$

where $\{D\}$ is a unit displacement in one global direction, a translation along $x$, $y$ or $z$ or a rotation about an axis. A large value means that mode is readily excited by forces or base motion in that direction. The effective mass is

$$
M_{\mathrm{eff},i}=\frac{\gamma_i^2}{\{\phi\}_i^T[M]\{\phi\}_i},
$$

which is just $\gamma_i^2$ for mass-normalised modes (ll. 306–315). Modes with a high effective mass are readily excited by base excitation, and summed over all modes the effective masses equal the total mass. That answers how many modes to extract: a structure with 200 DOF has 200 modes, but extraction can stop once the cumulative effective mass exceeds about 90 % of the total (ll. 316–330).

The uses are in design (ll. 281–310). For spacecraft, the participation factors identify the modes most likely to be excited, by launch random vibration from engines and shock waves, by deployment actuators, or by micro-vibration from attitude manoeuvres, and changing the geometry, boundary conditions or mass distribution can reduce them. For aero-engines, the modes most likely to radiate noise can be identified and their participation reduced to make the engine quieter.

> [!warning] Lecture slip (2026-02-27 10:55, ll. 306–315 and 346–355)
> The effective mass is described as "a ratio between the participation factor and the normalised mass", and for mass-normalised modes as "equal to the participation factor". It is the square of the participation factor over the modal mass, and equal to $\gamma_i^2$ when the modes are mass-normalised, as the slide's formula shows.

## 5. Modal analysis in ANSYS

Change the analysis type from static to modal (`ANTYPE,MODAL`) and set the number of modes to extract and expand, or a frequency range, in the pop-up window; six modes is the usual choice (ll. 356–375). The output needs care (ll. 371–390). Mode-shape displacements are not real deflections, only the shape matters. Stresses and strains can be computed from a mode, but they show only the relative stress distribution, not real values. No modal result predicts the response to a specific load, since none is applied; that needs a forced (harmonic or transient) analysis built on the modes, which also feed reduced-order models. The material density must be defined, otherwise the mass matrix is zero and there are no modes ([[SESA2029 C4 - APDL Workflow - Shell Wing Static and Modal (SHELL181 and SHELL281)|C4]]).

## Worked example: a two-DOF spring–mass system

The lecture's example (slide 16; ll. 331–355): $m_1=2$ kg is connected to the ground by $k_1=1000$ N/m, $m_2=1$ kg to the ground by $k_2=2000$ N/m, and $k_3=3000$ N/m connects the two masses. The lecture gives the mode shapes and leaves the matrices; here they are derived. The mass matrix is diagonal, and the coupling spring appears off the diagonal of the stiffness matrix:

$$
[M]=\begin{bmatrix}2&0\\0&1\end{bmatrix},
\qquad
[K]=\begin{bmatrix}k_1+k_3&-k_3\\-k_3&k_2+k_3\end{bmatrix}=\begin{bmatrix}4000&-3000\\-3000&5000\end{bmatrix}.
$$

With $\lambda=\omega^2$, the characteristic equation is

$$
(4000-2\lambda)(5000-\lambda)-3000^2=0.
$$

Expand:

$$
2\lambda^2-14\,000\lambda+2\times10^7-9\times10^6=0
\quad\Longrightarrow\quad
\lambda^2-7000\lambda+5.5\times10^6=0.
$$

Solve:

$$
\lambda=3500\pm\sqrt{3500^2-5.5\times10^6}=3500\pm2598.1,
$$

so $\lambda_1=901.9$ and $\lambda_2=6098.1$ s⁻², giving $\omega_1=30.03$ and $\omega_2=78.09$ rad/s, or $f_1=4.78$ Hz and $f_2=12.43$ Hz.

For mode 1, the first row gives $(4000-2\times901.9)\phi_1=3000\phi_2$, so $\phi_2/\phi_1=0.732$. Mass-normalise, $2\phi_1^2+\phi_2^2=1$:

$$
\phi_1^2(2+0.536)=1
\quad\Longrightarrow\quad
\{\phi\}_1=\{0.6280\ \ 0.4597\}^T,
$$

both masses moving together, in phase. For mode 2, $\phi_2/\phi_1=(4000-12\,196)/3000=-2.732$, and normalising gives $\{\phi\}_2=\{-0.3251\ \ 0.8881\}^T$, the masses moving against each other, out of phase.

For base excitation in the direction of motion, $\{D\}=\{1\ \ 1\}^T$:

$$
\gamma=\Phi^T[M]\{D\}=\begin{bmatrix}0.6280&0.4597\\-0.3251&0.8881\end{bmatrix}\begin{Bmatrix}2\\1\end{Bmatrix}=\begin{Bmatrix}1.7157\\-0.2379\end{Bmatrix}.
$$

The effective masses are the squares, 2.9436 kg and 0.0566 kg, summing to 3 kg, the total mass, because this system has only two modes. Mode 1 carries 98 % of the mass and dominates any base-excited response. All values were recomputed with SciPy's `eigh`, which returns the same shapes up to sign.

![[dam_modal_2dof.png|600]]

## Links

- Parent: [[SESA2029 Digital Aerospace Methods Hub]]
- Previous: [[SESA2029 B7 - Meshing, Convergence and Mesh Checks]]
- Next: [[SESA2029 B9 - Nonlinear FE Analysis]]
- Concepts: [[Natural Frequencies and Mode Shapes]] · [[Participation Factor and Effective Mass]] · [[Damping Ratio and Natural Frequency]] · [[Characteristic Equation and Eigenvalues]]
- Eigenvalues and modes in flight dynamics: [[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid]] · [[Frequency Response Function]]
- Free-free modal check for model verification: [[FE Model Verification Checks]]
- The wing in the lab: [[SESA2029 C4 - APDL Workflow - Shell Wing Static and Modal (SHELL181 and SHELL281)]]

## Sources

- FEA Lecture 10 slides, `Lecture_10_Modal_Analysis_2_final(1).pdf` (2-DOF example on slide 16; SDOF appendix on slides 22–25), with transcript `SESA2029 Lecture 2026-02-27 - 1055.txt` (Dr J. Yuan)
- Worked example recomputed with SciPy `eigh`

## Self-study tasks

### Core

- [ ] Derive the eigenvalue problem from the free, undamped equation of motion (2026-02-27 10:55, ll. 121–150). → [[#2. The eigenvalue problem]]
- [ ] Explain how stiffness, mass and boundary conditions change the natural frequencies (ll. 246–270). → [[#3. What controls the natural frequencies]]
- [ ] Compute the participation factors and effective masses for the 2-DOF system (ll. 331–355). → [[#Worked example: a two-DOF spring–mass system]]
- [ ] Lab 3: modal analysis of the wing; watch the video first, and finish the lab 2 report and example sheet 2 (ll. 401–410). → [[SESA2029 C4 - APDL Workflow - Shell Wing Static and Modal (SHELL181 and SHELL281)]]

### Further practice

- [ ] Find the natural frequencies of the 2-DOF system by hand from the characteristic equation, then check the mode shapes are mass-orthogonal. → [[#Worked example: a two-DOF spring–mass system]]
- [ ] Change the lab 1 beam from clamped to simply supported and compare its first natural frequency (suggested in the lecture, ll. 266–270). → [[#3. What controls the natural frequencies]]
