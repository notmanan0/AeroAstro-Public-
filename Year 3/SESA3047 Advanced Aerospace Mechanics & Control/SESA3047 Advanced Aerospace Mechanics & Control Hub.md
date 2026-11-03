---
title: "SESA3047 Advanced Aerospace Mechanics & Control Hub"
module: "SESA3047 Advanced Aerospace Mechanics & Control"
type: hub
aliases: ["SESA3047 Advanced Aerospace Mechanics & Control"]
tags: [sesa3047, hub, moc]
status: in-progress
coverage: "Chapters 1–4, all lectured (L2–L13); Chapter 5 §§5.1–5.2 and the §5.3 gravity terms lectured in L14 (Mon 2 Nov, Dr Sean Symon), the rest of Chapter 5 written ahead from the handout; Lab 1 filed; Coursework 1 submitted Thu 29 Oct"
---

# SESA3047 Advanced Aerospace Mechanics & Control Hub

> [!abstract] Module at a glance
> Chapter 1 sets up the language of six-degree-of-freedom mechanics and control (dynamic systems, control architectures, models, states and reference frames). Chapter 2 builds the kinematic toolkit: vector products, the transport theorem, direction cosine matrices and Euler angles. Chapter 3 turns it into the first state equations (Euler-angle rates, motion in moving frames, position from body velocity, the inertia matrix and the rotational dynamic equation), and Chapter 4 completes the 12-state flat-Earth model with inertia coupling, rotors and translational dynamics.
>
> Chapters 1–4 are all lectured (L2–L13, finishing in the Thu 22 Oct double) and written up from the transcripts. Chapter 5 (state-space models) is written up in full: 5.1 from L14 (Mon 2 Nov), the first lecture of **Dr Sean Symon**, who teaches the rest of the module; 5.2 partly lectured; 5.3–5.4 written ahead of Thursday's lecture. Lab 1 is filed, and Coursework 1 was submitted on Thu 29 October ([[#Labs and coursework]]). Quick reference: [[SESA3047 Formula Sheet]].
>
> Chapters 1–4 were taught by Dr Cristiano Martinelli; Chapter 5 onwards by Dr Sean Symon.

## Current coverage

1. [[SESA3047 1.1 - Dynamic Systems and Control Architectures]]
2. [[SESA3047 1.2 - Dynamic Models, Frames and Earth Models]]
3. [[SESA3047 2.1 - Vector Operations and the Transport Theorem]] (Chapter 2, §§2.1–2.2)
   - dot and cross products, with component derivations;
   - the cross-product (skew) matrix and triple products;
   - centripetal acceleration;
   - angular velocity and the transport theorem, derived two ways.
4. [[SESA3047 2.2 - Direction Cosine Matrices and Euler Angles]] (Chapter 2, §§2.3–2.4)
   - DCM definition, direction cosines and properties;
   - elementary rotations and the cyclic sign rule;
   - the 3-2-1 NED→FRD sequence multiplied out;
   - Euler-angle extraction, gimbal lock and small-angle rotations;
   - the §2.4.6 worked example (done on the board in L7).
5. [[SESA3047 3.1 - Rotational Kinematics and Euler-Angle Rates]] (Chapter 3, §3.1; lectured in L7–L8)
   - Euler rates vs body rates $p,q,r$; composing the three rotation rates;
   - $\mathbf E(\boldsymbol\Phi)$ multiplied out; $\mathbf H=\mathbf E^{-1}$ derived; $\det\mathbf E=\cos\theta$ and gimbal lock;
   - geometric coupling (L8's $\phi=45^\circ$ example, integrated); small-angle form; flat vs rotating Earth; level-turn and gyro examples.
6. [[SESA3047 3.2 - Translational Kinematics and Accelerations in Moving Frames]] (Chapter 3, §3.2; lectured in L8–L9)
   - transport velocity; the five-term acceleration with Coriolis and centripetal terms;
   - rotating vs flat Earth, apparent forces and their size;
   - body-axis acceleration $[\dot u+qw-rv,\dots]^T$; translational kinematic equation $\dot{\mathbf p}=\mathbf C^T\mathbf v$.
7. [[SESA3047 3.3 - Rigid-Body Rotational Dynamics]] (Chapter 3, §§3.3–3.4; L10, with explicit derivative revisited in L11)
   - linear momentum; angular momentum and the inertia matrix derived;
   - why the cm term vanishes (by definition, not symmetry) and why $\dot{\mathbf J}=\mathbf 0$ needs rigidity, not just constant mass;
   - rotational dynamic equation, Euler's equations, the $J_{xz}$ aircraft form;
   - inertia coupling, imbalance and the intermediate-axis theorem; how the 6-DOF equations fit together.

8. [[SESA3047 4.1 - Inertia Models and Rotor Dynamics]] (Chapter 4 §4.1; L11, then L12 and the start of L13)
   - full moment expansion, eigenvector interpretation, aircraft block inverse and internal rotor momentum;
   - **inertia coupling with no external moment**: the three L12 cases, simulated;
   - the $x$–$z$ symmetry argument, and what L12 said to remember;
   - $\dot{\boldsymbol\omega}_{base}+\dot{\boldsymbol\omega}_{add}$; the aircraft rotor terms multiplied out; the diagonal (quadcopter) form;
   - symbolic algebra checks and suggested numerical examples; transcript slips for L11–L13.
9. [[SESA3047 4.2 - Translational Dynamics]] (Chapter 4 §4.2; L13 ll. 88–309)
   - rotating Earth, flat Earth and transport into body axes; the gravity rotation the lecturer nearly forgot;
   - the lecture's four-move derivation; "inertial" terminology flagged;
   - effective gravity and the $X,Y,Z$ convention (handout only); a checked numerical derivative.
10. [[SESA3047 4.3 - Complete Flat-Earth 6-DOF Model]] (Chapter 4 §4.3; end of L13, shown from the notes)
11. [[SESA3047 5.1 - State-Space Form and Linearisation]] (Chapter 5 §§5.1–5.2; **lectured**, L14 Mon 2 Nov)
   - $\mathbf A,\mathbf B,\mathbf C,\mathbf D$ and their sizes; $\mathbf C=\mathbf I$ in this module, $\mathbf D$ unused;
   - linearising $\sin x$ about $0$ and $\pi$; the $\epsilon$ bookkeeping ($\epsilon^0$ = equilibrium, $\epsilon^2$ dropped);
   - the force equations linearised about straight flight (Eq. 5.7, flagged as exam material); Eq. 5.8 derived in full, with the rotor exception.
12. [[SESA3047 5.2 - Longitudinal State-Space Model]] (Chapter 5 §5.3 and appendix; **written ahead**, gravity part lectured in L14)
   - longitudinal–lateral split and its three conditions; gravity linearised about $\gamma_0$ ($\theta$ vs $\gamma$ flagged);
   - aerodynamic derivatives, Eqs. 5.17–5.18, $\mathbf A=\mathbf E^{-1}\mathbf A'$ written out; dimensional derivatives with units.
13. [[SESA3047 5.3 - Building State-Space Models from ODEs, Transfer Functions and Block Diagrams]] (Chapter 5 §§5.4–5.6; **written ahead**)
   - the satellite–instrument model used in Lab 2, its transfer function by hand, and why its double pole at the origin is not marginally stable;
   - transfer functions to state space (chain of integrators); block diagrams to state space; handout slips in Eqs. 5.21d and 5.32.
14. [[SESA3047 5.4 - Time-Domain Solution and Stability]] (Chapter 5 §5.7; **written ahead**)
   - $e^{\mathbf At}$ from its series; diagonalisation and modes; stability from eigenvalues, with the zero-real-part cases.
15. [[SESA3047 Chapter 5 Practice Problems - Solutions]]: all five §5.8 problems worked and checked (Problem 1 pointed to in L14 as a former exam question).
   - all twelve states and the 6 + 6 split, solver evaluation, full derivative example and an exact ballistic integration check.

## Week 1 concept map

| Systems and control | Modelling | Mechanics and frames |
|---|---|---|
| [[Dynamic System, Plant and Model]] | [[State, Input, Output and Parameter]] | [[Kinematics and Dynamics]] |
| [[Passive and Active Control]] | [[Model Fidelity and Validity]] | [[Reference Frames and Coordinate Systems]] |
| [[Open-Loop, Feedback and Feedforward Control]] | [[Linear, Nonlinear and Time-Varying Models]] | [[Flat-Earth Model]] |
| | | [[NED and FRD Coordinates]] |

## Chapter 2 concept map

| Foundations | Vector kinematics | Attitude |
|---|---|---|
| [[Scalar (Dot) Product]] (MATH1054) | [[Cross-Product Matrix]] | [[Direction Cosine Matrix]] |
| [[Vector (Cross) Product]] (MATH1054) | [[Angular Velocity Vector]] | [[Aerospace 3-2-1 Euler Sequence]] |
| [[Euler Angles and Rotation Matrices]] (SESA2027) | [[Transport Theorem]] | [[Gimbal Lock]] |

## Chapter 3 concept map

| Kinematics | Moving frames | Dynamics |
|---|---|---|
| [[Rotational Kinematic Equation]] | [[Coriolis and Centripetal Acceleration]] | [[Inertia Matrix]] (SESA2024) |
| [[Translational Kinematic Equation]] | [[Transport Theorem]] (Ch. 2) | [[Rotational Dynamic Equation]] |
| [[Gimbal Lock]] (Ch. 2) | [[Flat-Earth Model]] (Ch. 1) | [[Momentum Bias and Gyroscopic Rigidity]] (SESA2024) |

## Chapter 4 concept map

| Inertia and rotation | Translation | Complete model |
|---|---|---|
| [[Principal Axes of Inertia]] | [[Translational Dynamic Equation]] | [[Six-Degree-of-Freedom State Model]] |
| [[Rotor Angular Momentum]] | [[Flat-Earth Model]] | [[State, Input, Output and Parameter]] |
| [[Rotational Dynamic Equation]] | [[Translational Kinematic Equation]] | [[Gimbal Lock]] |

## Chapter 5 concept map

| Linearisation | Aircraft model | State-space tools |
|---|---|---|
| [[Linearisation about an Equilibrium Point]] | [[Longitudinal and Lateral Dynamics]] | [[Transfer Function to State-Space Conversion]] |
| [[Small Perturbation Linearisation]] (SESA2027) | [[Aerodynamic Stability Derivatives]] (SESA2027) | [[Matrix Exponential and Modal Solution]] |
| [[State-Space Representation]] (SESA2027) | [[Rotational Dynamic Equation]] (Ch. 3) | [[Characteristic Equation and Eigenvalues]] (SESA2027) |

## Coverage boundary

The current sources are **Chapters 1–4**. L13 (Thu 22 Oct) ends with the assembled 12-state model, Eq. 4.42, so **Chapter 4 is fully lectured**. A few handout equations were not lectured: Eq. 4.25 (changing rotor momentum), Eq. 4.31 (effective gravity), and Eqs. 4.38–4.40 (the $X,Y,Z$ convention). They are marked "handout only" in the notes. Chapter 5 (state-space models, Dr Sean Symon) started in L14 (Mon 2 Nov), which covered §§5.1–5.2 and the gravity terms of §5.3. The rest of Chapter 5 is written ahead from the handout, marked `written-ahead`, and will be reconciled with Thursday's lecture. Controllability, observability and control design (Chapters 6–8 by L14's description) remain outside current coverage.

| Material | Vault status |
|---|---|
| Chapters 1–2 | **Complete**, lectured (L2–L7) |
| Chapter 3 §§3.1.1–3.1.3 | **Complete**, lectured in L7 (Mon 5 Oct) |
| Chapter 3 §§3.1.4–3.2 | **Complete**, lectured in L8–L9 (Thu 8 Oct); line references, slips and tasks folded in |
| Chapter 3 §3.3 | **Complete**, lectured in L10 (Mon 12 Oct); line references, slips and tasks folded in |
| Chapter 3 §3.4 | From the notes; not lectured as a separate item (L10 ended at Eq. 3.70) |
| Chapter 4 §§4.1.1–4.1.2 | **Complete**, lectured in L11 (Mon 19 Oct); expansion, principal axes and slips backfilled |
| Chapter 4 inertia coupling, §§4.1.3–4.1.4 | **Complete**, lectured in L12 and L13 ll. 1–86 (Thu 22 Oct); Eq. 4.25 handout only |
| Chapter 4 §4.2 | **Complete**, lectured in L13 ll. 88–309; Eqs. 4.31, 4.38–4.40 handout only |
| Chapter 4 §4.3 | **Complete**, shown from the notes at the end of L13 (ll. 310–344) |
| Chapter 5 §§5.1–5.2 | **Complete**, lectured in L14 (Mon 2 Nov) ll. 28–342 → [[SESA3047 5.1 - State-Space Form and Linearisation\|5.1]] |
| Chapter 5 §5.3 gravity (5.9–5.15) | Lectured in L14 ll. 373–509 → [[SESA3047 5.2 - Longitudinal State-Space Model\|5.2]] §2 |
| Chapter 5 §5.3 aerodynamics, 5.16–5.18, appendix | Written ahead from the handout; awaiting Thu 5 Nov → 5.2 §§3–6 |
| Chapter 5 §§5.4–5.6 | Written ahead; awaiting Thu 5 Nov (the Lab 2 example) → [[SESA3047 5.3 - Building State-Space Models from ODEs, Transfer Functions and Block Diagrams\|5.3]] |
| Chapter 5 §5.7 | Written ahead; awaiting lecture → [[SESA3047 5.4 - Time-Domain Solution and Stability\|5.4]] |
| Chapter 5 §5.8 practice problems | Solved → [[SESA3047 Chapter 5 Practice Problems - Solutions]] |
| Later chapters | Awaiting material (B matrix in Chapters 7–8, L14 ll. 154–155) |

Chapter 4 was written from the lecture-note handout on 19 October and updated from L12–L13 on 23 October. Chapter 5 was written on 3 November from the handout (released Sat 31 Oct) and L14; the Thursday 5 Nov lecture will be backfilled in the next weekly run.

## Labs and coursework

> [!important] Lab 1: *Dynamic Analysis via Numerical Simulations* (MATLAB)
> File: `04 - Labs & Coursework/Lab 1/Lab_1.pdf` (6 pages, Dr Cristiano Martinelli). It feeds the **lab report, worth 20% of the module mark**. No submission date is printed on the sheet: check Blackboard. Aim to finish at least Exercises 1 and 2 in the session; demonstrators will check your plots.
>
> | Exercise | Task | Theory in the vault |
> |---|---|---|
> | 0 (intro) | MATLAB matrices, element-wise operators, `ode45` with a first-order state vector | [[SESA3047 1.1 - Dynamic Systems and Control Architectures\|1.1]] (state form) |
> | 1 | Build $\mathbf C_{FRD/NED}=\mathbf C_x\mathbf C_y\mathbf C_z$; transform north for $\psi=\pm30^\circ$; recover $(20^\circ,15^\circ,30^\circ)$ with atan2/arcsin; probe $\theta=89^\circ, 89.9^\circ, 90^\circ$ | [[SESA3047 2.2 - Direction Cosine Matrices and Euler Angles\|2.2]] §§6–10, [[Gimbal Lock]] |
> | 2 | Nonlinear oscillator (textbooks: Duffing oscillator) $m\ddot x+c\dot x+kx+\mu x^3=f\cos\omega t$; linear vs nonlinear, small vs large amplitude, free and forced | [[SESA3047 1.2 - Dynamic Models, Frames and Earth Models\|1.2]], [[Linear, Nonlinear and Time-Varying Models]] |
> | 3 | Integrate the rotational dynamics with the Euler-angle kinematics (Eqs. 3.10–3.11, 3.63–3.71); interpret geometric and inertial coupling | [[SESA3047 3.1 - Rotational Kinematics and Euler-Angle Rates#The lecture's coupling example (L8, ll. 44–68)\|3.1 §7]], [[SESA3047 3.3 - Rigid-Body Rotational Dynamics\|3.3]] |
>
> The lecturer tied the coupling discussion to the lab: *"we will see how this affects the numerical simulations"* (L8, ll. 67–68). Lab 2 will use Simulink (Lab 1, p. 1).

> [!warning] Lab 1 Exercise 2: three wording traps on the sheet
> - **Equilibrium (p. 5).** *"The origin $(x,\dot x)=(0,0)$ is an equilibrium for both the linear and nonlinear models"* is true only of the **unforced** models ($f=0$). With $f\cos\omega t\neq0$, $\ddot x(0)=f/m\neq0$ at the origin, so it is not a fixed point of the forced system. Linearising about the origin (as in [[SESA3047 1.2 - Dynamic Models, Frames and Earth Models#5. Linear and nonlinear models|1.2 §5]]) is a statement about the unforced dynamics; see the trim-condition warning there.
> - **Forcing hint.** The hint says to add *"f/m\*cos(omega\*t))/m"* to a line that already ends in `/m`. Read literally, that divides by $m$ twice. From $m\ddot x+c\dot x+kx+\mu x^3=f\cos\omega t$, the acceleration is $\ddot x=(f\cos\omega t-c\dot x-kx-\mu x^3)/m$: **one** division. `exercise2_2.m` (ll. 13–14) does this correctly. With $m=1$ kg the two readings give the same numbers, which is exactly why the slip would go unnoticed in the lab and then break with any other mass.
> - **Units in Table 1** are shifted down a row in the PDF: they should read $k$ in N/m, $\mu$ in N/m³ and $f$ in N.

> [!todo] Lab 1 report checklist
> - [ ] **Ex. 1, DCM round trip:** build $\mathbf C_{FRD/NED}$, extract $(\phi,\theta,\psi)$, check $\mathbf C\mathbf C^T=\mathbf I$ and $\det\mathbf C=1$, rebuild $\mathbf C$ from the extracted angles. → [[SESA3047 2.2 - Direction Cosine Matrices and Euler Angles|2.2]]
> - [ ] **Ex. 1, singularity:** run `exercise1_3.m` at $89^\circ$, $89.9^\circ$, $90^\circ$; explain why MATLAB returns $\phi=\psi=0$ at exactly $90^\circ$ and why only $\phi-\psi$ is recoverable. → [[SESA3047 2.2 - Direction Cosine Matrices and Euler Angles#8. The singularity: gimbal lock (§2.4.5)|2.2 §8]]
> - [ ] **Ex. 2, free response:** small vs large amplitude, linear vs nonlinear, $f=0$ (`exercise2_1.m`); relate the frequency shift to $k_{\text{eff}}=k+3\mu x_0^2$. → [[SESA3047 1.2 - Dynamic Models, Frames and Earth Models|1.2 §5]]
> - [ ] **Ex. 2, forced response:** same models with $f\cos\omega t$ (`exercise2_2.m`), single division by $m$; say explicitly that the origin is no longer an equilibrium.
> - [ ] **Ex. 2, restoring force:** plot $kx$ and $kx+\mu x^3$ on $|x|\le0.12$ m (`exercise2_3.m`); $\mu x^3$ reaches 10% of $kx$ at $|x|=\sqrt{0.1k/\mu}=0.1$ m.
> - [ ] **Ex. 3, coupling:** separate **geometric** coupling (Euler-angle kinematics, $\mathbf H(\boldsymbol\Phi)$) from **inertial** coupling ($\boldsymbol\omega\times\mathbf J\boldsymbol\omega$) in `exercise3_1.m`. → [[SESA3047 3.1 - Rotational Kinematics and Euler-Angle Rates|3.1 §7]], [[SESA3047 4.1 - Inertia Models and Rotor Dynamics#Inertia coupling with no external moment (L12 ll. 22–119)|4.1]]
> - [ ] **Ex. 3, feedback vs none:** `exercise3_2.m` runs $\mathbf M=-\mathbf K_P(\boldsymbol\Phi-\boldsymbol\Phi_{ref})-\mathbf K_D\boldsymbol\omega$ and then $\mathbf M=\mathbf 0$ from the same start, as the sheet asks. Interpret with care: the controller feeds back **Euler angles** but applies **body** moments. That is a fair PD attitude loop only near small angles, where $\dot{\boldsymbol\Phi}\approx\boldsymbol\omega$; at large angles $\mathbf H(\boldsymbol\Phi)$ mixes the axes, and near $\theta=\pm90^\circ$ the feedback inherits the singularity.

> [!important] Lab 2 (Simulink): to be released by Fri 6 Nov
> Announced in L14: *"lab two is going to be about Simulink. My plan is to release lab two, hopefully, by the end of the week … before you do the lab next week"* (ll. 532–537). Thursday's lecture example is *"directly used in the lab"* (l. 535), and the handout says the satellite state-space model of §5.4 is the one used in Lab 2: see [[SESA3047 5.3 - Building State-Space Models from ODEs, Transfer Functions and Block Diagrams#1. Second-order equations as first-order states (5.19–5.24)|5.3 §1]], including the $T_c/J_1$ slip in Eq. 5.21d. Not yet filed.

> [!important] Coursework 1: submitted Thu 29 Oct
> Submitted on time as a 14-page handwritten scan: [[SESA3047 Coursework 1 Submission.pdf]]. The folder `04 - Labs & Coursework/Coursework 1/` holds the submission at the top level, with `Brief/` (brief, template, guide), `Working Notes/` (typed draft and explainers), `MATLAB/` (`cw1_q1a_ode45.m`, `cw1_figures.m`) and `Figures/`.
> - Working notes: [[SESA3047 CW1 Report Draft]] (typed draft), [[SESA3047 CW1 Q1a Physical Interpretation Explained|Q1a interpretation]], [[SESA3047 CW1 Q1b Coupling Paragraph Rewrite|Q1b coupling]], [[SESA3047 CW1 Q1c Decoupled Case Explained|Q1c decoupled case]], [[SESA3047 CW1 Q1d How To Do It Step by Step|Q1d method]], [[SESA3047 CW1 Q1d Wind Components Explained|Q1d wind components]], [[SESA3047 CW1 Q1d c and s Shorthand|Q1d shorthand]] and [[SESA3047 CW1 Runge-Kutta for the Euler-Angle Rates|Runge–Kutta for the Euler-angle rates]].
>
> Announced before the L12 break: *"I have uploaded the coursework … in blackboard you can find the instructions as well. Under assessment, coursework one. And the coursework is due by the 29th of October at 11 p.m."* (L12 ll. 352–357).
>
> File: `04 - Labs & Coursework/Coursework 1/Brief/Coursework_1.pdf` (2 pages). It is a **separate piece from the Lab 1 report**: two problems, **20 marks, 10 % of the module**.
> - **Submission**: a single PDF through *Assessments → Coursework 1*. Photographed handwritten work is fine.
> - **Rules**: *"show a sufficient number of steps … no credit will be given to correct answers by themselves"*. Late penalty **2 marks per day**. Individual work.
> - **Templates**: `Coursework 1/Brief/SESA3047 Coursework 1 Report Template.docx` (8 pages, one box per part, figure slots and results tables) and `SESA3047 Coursework 1 Guide.docx` (not submitted: inputs, page plan, guidance, equations, checks).
>
> | Part | Task | Marks | Theory in the vault |
> |---|---|---:|---|
> | 1(a) | Euler angles for 5 s of constant $p$, $q$ ($r=0$) from level flight heading north; integrate with `ode45` or equivalent; final roll, pitch and yaw in degrees | 3 | [[SESA3047 3.1 - Rotational Kinematics and Euler-Angle Rates\|3.1]] §§5–6 (the kinematic equation); Lab 1 Ex. 3 (`ode45`) |
> | 1(b) | write the integral explicitly, non-matrix; show what depends on time; coupled or not, and why | 3 | [[SESA3047 3.1 - Rotational Kinematics and Euler-Angle Rates#4. Multiplying it out, one step at a time (Appendix §3.4.1, L7 ll. 200–300)\|3.1 §4]] and §6 |
> | 1(c) | repeat with $q=0$; what changes, and are the angles coupled | 2 | [[SESA3047 3.1 - Rotational Kinematics and Euler-Angle Rates#The lecture's coupling example (L8, ll. 44–68)\|3.1 §7, coupling example]] |
> | 1(d) | wind $\mathbf v_w^{NED}=[8,4,0]^T$ into FRD through $\mathbf C_{FRD/NED}$ at the final attitude; interpret the signs | 2 | [[SESA3047 2.2 - Direction Cosine Matrices and Euler Angles\|2.2]] §6 (3-2-1 DCM, both directions) |
> | 2(a) | flat-Earth translational and rotational equations, coordinate systems, assumptions | 2 | [[SESA3047 4.2 - Translational Dynamics\|4.2]] §§2–3, [[SESA3047 4.3 - Complete Flat-Earth 6-DOF Model\|4.3]] |
> | 2(b) | gravity in FRD for $\Phi=\mathbf 0$ | 2 | [[SESA3047 2.2 - Direction Cosine Matrices and Euler Angles#Gravity in body axes (derivation)\|2.2, gravity in body axes]] |
> | 2(c) | $\dot u,\dot v,\dot w$ with the cross-product matrix; why thrust and weight cancelling does not make $\dot w=0$ | 3 | [[SESA3047 4.2 - Translational Dynamics#3. Derive the body-velocity equation (4.33–4.37)\|4.2 §3]], [[Cross-Product Matrix]] |
> | 2(d) | $\dot p,\dot q,\dot r$ with principal $\mathbf J$ and $\mathbf M=\mathbf 0$; coupling; the case $J_x=J_y=J_z$ | 3 | [[SESA3047 4.1 - Inertia Models and Rotor Dynamics#Inertia coupling with no external moment (L12 ll. 22–119)\|4.1, inertia coupling]] |
>
> **Ambiguity:** 1(d) says *"using the final attitude angles from question B"*, but there is no question B, and part (b) produces equations, not angles. It most likely means the final angles of 1(a); possibly 1(c). The submission used the 1(a) angles ($\phi=0.5269$, $\theta=0.3825$, $\psi=0.1043$ rad).

## Tutorials and mock questions

No tutorial or revision questions had been set for SESA3047 by 22 Oct 2026, and `03 - Exams & Past Papers` is empty.

> [!important] Exam announcements (L14, Mon 2 Nov)
> - The exam paper is written and with the external examiner (University of Surrey) (ll. 9–10).
> - The **exam formula sheet** will go on Blackboard in about two weeks (mid-November); it includes Taylor series. Report any mistakes (ll. 11–16, 136).
> - A **mock paper** will be put up (l. 18).
> - Past papers of **SESA2025** (the old second-year flight mechanics module) cover *"quite a bit"* of the remaining six weeks, though they assess slightly different things (ll. 19–23). The Chapter 5 practice Problem 1 *"used to be an exam question"* for SESA3030 (ll. 230–234).

- [[SESA3047 Chapter 5 Practice Problems - Solutions]]: **lecturer-set** (handout §5.8), five problems with my worked solutions; no answer key issued.

- [[SESA3047 Mock Questions - Chapters 1-4]]: **self-written, not lecturer-set**. Ten exam-style questions (118 marks) with timed full solutions and Python-checked numbers, covering classification and linearisation, frames and flat Earth, the transport theorem, DCMs and gimbal lock, Euler-angle rates, Coriolis acceleration, principal axes, rotor angular momentum and the 12-state model. Its data deliberately differ from Lab 1 and Coursework 1.

## Week 1 exam skills

- identify the plant, reference, error, controller, actuator, sensor, feedback and disturbance in a physical system;
- distinguish passive/active control and open-loop/feedback/feedforward arrangements;
- state what a model includes, what it omits, and the operating range in which it remains credible;
- classify a model as linear/nonlinear, time invariant/time varying, static/dynamic and lumped/continuum;
- identify variables, parameters, inputs, outputs and a minimum state set;
- distinguish kinematics from dynamics;
- distinguish a physical vector, its coordinate components and the observer's reference frame;
- state the flat-Earth assumptions and choose NED or FRD coordinates for a quantity.

## Chapter 2 exam skills

- compute dot and cross products in components and interpret them geometrically (projection, perpendicularity, area);
- write and use the cross-product matrix $\tilde{\mathbf u}$, and apply BAC−CAB, e.g. to show $\boldsymbol\omega\times(\boldsymbol\omega\times\mathbf r)=-\omega^2\mathbf r$;
- state and derive the transport theorem, and apply its special cases (vector fixed in the body, e.g. the nose direction);
- state the properties of angular velocity, and explain why angular accelerations do not simply add;
- derive an elementary DCM, and state and justify orthogonality, composition, $\det=+1$ and non-commutativity;
- build $\mathbf C_{FRD/NED}=\mathbf C_x(\phi)\mathbf C_y(\theta)\mathbf C_z(\psi)$, transform vectors both ways, and write gravity in body axes;
- extract Euler angles from a DCM and explain gimbal lock at $\theta=\pm90^\circ$;
- explain why atan2 (two arguments, four quadrants) is used rather than arctan of a ratio (L6 question);
- use the full sub/superscript notation: point/frame (right subscript), coordinates (right superscript), derivative frame (left superscript).

## Chapter 3 exam skills

- explain why $\dot{\boldsymbol\Phi}\neq\boldsymbol\omega^{FRD}$, and which rotations each Euler rate passes through (L7, ll. 160–194);
- show the geometric coupling with a reduced case, e.g. $r=0$, $\theta=0$, $\phi=45^\circ$ gives $\dot\theta=\dot\psi=q/\sqrt2$ (L8, ll. 44–55);
- state the flat-Earth assumptions behind each equation, and what changes on a rotating Earth ($\boldsymbol\omega_{b/r}=\boldsymbol\omega_{b/i}-\boldsymbol\omega_{r/i}$; L8 ll. 121–153);
- multiply out $\boldsymbol\omega=[\dot\phi,0,0]^T+\mathbf C_x(\phi)([0,\dot\theta,0]^T+\mathbf C_y(\theta)[0,0,\dot\psi]^T)$ to get $\mathbf E$, and invert it to $\mathbf H$; state $\det\mathbf E=\cos\theta$ and its link to gimbal lock;
- state and use the small-angle form, and say when it fails;
- derive $\mathbf v_{P/a}$ and the five-term $\mathbf a_{P/a}$ with the transport theorem; name every term; explain the factor 2;
- write Newton's law in a rotating Earth frame and identify centrifugal and Coriolis forces; justify the flat-Earth model;
- derive $[\dot u+qw-rv,\ \dot v+ru-pw,\ \dot w+pv-qu]^T$ and $\dot{\mathbf p}^{NED}=\mathbf C^T\mathbf v^{FRD}$;
- derive $\mathbf h=\mathbf J\boldsymbol\omega$ (cm term vanishes, $-\tilde{\mathbf r}^2$), define moments and products of inertia (L10, ll. 60–247); say **why** the cm term vanishes (definition of the cm, not symmetry) and why $\dot{\mathbf J}=\mathbf 0$ (a rigid body, not just constant mass);
- derive $\dot{\boldsymbol\omega}=\mathbf J^{-1}(\mathbf M-\tilde{\boldsymbol\omega}\mathbf J\boldsymbol\omega)$, reduce it to Euler's equations, and explain the $\tilde{\boldsymbol\omega}\mathbf J\boldsymbol\omega$ term and the inertia coupling it causes;
- list the 6-DOF state equations so far, and which are kinematics and which dynamics.

## Chapter 4 exam skills

All of Chapter 4 is now lectured (L11–L13). Items marked *handout only* were not covered in the recordings.

- expand the full inertia equation by finding momentum components first (L11 ll. 81–180);
- explain the eigenvector definition of principal axes and why FRD axes need not be principal (L11 ll. 181–228);
- explain inertia coupling with no external moment: two non-zero rates first drive only the third, then generically all three change; $J_{xx}=J_{zz}$ removes the $\dot q$ coupling (a counterexample to "always"); a single-axis spin is steady (L12 ll. 22–119). *"The case that I would generally remember"* is the diagonal one (L12 ll. 182–187);
- explain why an $x$–$z$ symmetry plane gives $J_{xy}=J_{yz}=0$, and contrast this with the cm integral, which needs no symmetry (L12 ll. 128–137);
- derive the aircraft roll–yaw inverse and check its zero-product limit (shown but not multiplied out in L12 ll. 142–171);
- explain why the matrix form is kept for numerical work (L12 ll. 192–208);
- derive $\dot{\boldsymbol\omega}=\dot{\boldsymbol\omega}_{base}+\dot{\boldsymbol\omega}_{add}$ for a rotor with constant body-frame momentum, and say why the rigid-body equations still hold for axisymmetric rotors (L12 ll. 222–349);
- multiply out the rotor terms for the aircraft and diagonal $\mathbf J$ (L13 ll. 9–86); the spin-up term is *handout only*;
- derive flat-Earth translational dynamics in four moves: Newton, rotating Earth (centrifugal + Coriolis), flat Earth, body-frame derivative. Then rotate $\mathbf g$ into FRD (L13 ll. 104–309);
- effective gravity vs gravitation, and the gravity-including $X,Y,Z$ convention (*handout only*);
- assemble the twelve states in the handout's order, explain *"6 states for the dynamics, and 6 for the kinematics"*, and distinguish all four equation groups (L13 ll. 310–340);
- explain why the model is integrated numerically and check solver evaluation order against the yawing ballistic example (L13 ll. 318–325).

## Chapter 5 exam skills

5.1 is lectured (L14); the rest is written ahead and marked.

- say what $\mathbf A,\mathbf B,\mathbf C,\mathbf D$ are, their sizes, and why $\mathbf A$ must be square (L14 ll. 152–162);
- linearise a one-variable function about a stated equilibrium, and explain why the point matters ($\sin x$ about $0$ and $\pi$; L14 ll. 79–131);
- find all equilibria of a nonlinear system and linearise it, by $\epsilon$ expansion or Jacobian (Practice problem 1; L14 ll. 230–234);
- linearise Eqs. 5.3 about straight flight, showing every $\epsilon$ power, and explain why $rU$ survives but $qW$ does not; flagged *"it's on there"* (L14 ll. 164–165, 236–317);
- derive Eq. 5.8 and say when gyroscopic terms survive (rotor, rotating trim);
- linearise gravity about $\gamma_0$, checking that the $\epsilon^0$ terms are trim (L14 ll. 438–509);
- *written ahead:* assemble Eqs. 5.17–5.18, form $\mathbf A=\mathbf E^{-1}\mathbf A'$, convert dimensionless derivatives; derive the lateral model (Problem 3);
- *written ahead:* convert second-order ODEs, transfer functions and block diagrams to state space (Problems 2, 4);
- *written ahead:* solve $\dot{\mathbf x}=\mathbf A\mathbf x$ with $e^{\mathbf At}$ and diagonalisation; judge stability from eigenvalues, including zero-real-part and defective cases (Problem 5).

## All notes

```dataview
TABLE type, status, coverage, file.mtime AS "Updated"
FROM "Year 3/SESA3047 Advanced Aerospace Mechanics & Control"
WHERE type
SORT type ASC, file.name ASC
```

## Builds on / feeds into

- **From** [[SESA2027 Aerospace Mechanics & Control Hub]]: dynamic systems, state-space models, feedback, stability, sensors and actuators, and body axes with $\mathbf R_{BE}$ ([[Euler Angles and Rotation Matrices]]).
- **From** [[SESA2022 Aerodynamics Hub]]: static stability and aerodynamic forces/moments.
- **From** Year 1 vectors and rigid-body dynamics: [[MATH1054 M15 - Vectors II]], [[FEEG1002 D7 - Kinematics of Rigid Bodies]].
- **Alongside** [[SESA3043 Advanced Aeronautics Hub]]: both modules distinguish a physical system from a deliberately simplified mathematical model. SESA3043's [[Reynolds Transport Theorem]] is a different "transport theorem" (system versus control volume).
- **Year 3 bridges (note level):** the transport theorem of [[SESA3047 2.1 - Vector Operations and the Transport Theorem|2.1]] against the Reynolds transport theorem of [[SESA3043 1.1 - Mathematical Tools and Flow Description|SESA3043 1.1]] (different theorems, same name) · body-axis force equation ([[SESA3047 4.2 - Translational Dynamics|4.2]]): $\boldsymbol\omega\times\mathbf v$ plays the role of the convective acceleration in [[SESA3043 1.2 - Conservation Laws and Governing Equations|SESA3043 1.2]], and the aerodynamic $X$, $Z$ come from the lift and drag of [[SESA3043 2.2 - Lumped Vortex Method|SESA3043 2.2]].

## Sources

- Chapter_4.pdf (10 pages: inertia models, rotors, translational dynamics and complete 6-DOF state model).
- L11 - SESA3047.txt (Mon 19 Oct; 232 lines: explicit derivative, full inertia expansion and principal axes; stops at §4.1.2).
- L12 - SESA3047.txt (Thu 22 Oct, first half; 360 lines: inertia coupling, aircraft symmetry, rotors to Eq. 4.20; Coursework 1 announced).
- L13 - SESA3047.txt (Thu 22 Oct, second half; 344 lines: aircraft rotor terms, translational dynamics, the 12-state model; end of Chapter 4).
- Chapter_5.pdf (10 pages, Dr Sean Symon, released Sat 31 Oct: state-space form, linearisation, longitudinal model, satellite example, transfer functions and block diagrams to state space, matrix exponential and stability, practice problems, aerodynamic-derivative appendix). Filed from Downloads on 3 Nov.
- `02 November 2026 at 11_53_51.txt` = **L14** (Mon 2 Nov; 538 lines; Dr Symon's first lecture: announcements, linearisation, Eqs. 5.7–5.8, gravity terms) → [[SESA3047 5.1 - State-Space Form and Linearisation|5.1]], [[SESA3047 5.2 - Longitudinal State-Space Model|5.2]].

- `02 - Sources/Lectures/Chapter 1.pdf`
- `02 - Sources/Lectures/L2 - SESA3047.txt`
- `02 - Sources/Lectures/L3 - SESA3047.txt`
- `02 - Sources/Lectures/Chapter 2.pdf`
- `02 - Sources/Lectures/L4 - SESA3047.txt` (end of Chapter 1 notation; dot and cross products)
- `02 - Sources/Lectures/L5 - SESA3047.txt` (centripetal example, angular velocity, transport theorem, DCM properties)
- `02 - Sources/Lectures/L6 - SESA3047.txt` (non-commutativity, Euler angles, extraction, gimbal lock; end of Chapter 2)
- `02 - Sources/Lectures/Chapter-3.pdf` (15 pages: rotational kinematics, translational kinematics, rigid-body rotational dynamics, appendix)
- `02 - Sources/Lectures/SESA3047 - L7.txt` (Mon 5 Oct: §2.4.6 worked example; §§3.1.1–3.1.3, ending at the rotational kinematic equation)
- `02 - Sources/Lectures/L8 - SESA3047.txt` (Thu 8 Oct, first half: coupling, flat vs rotating Earth, velocity and acceleration in moving frames)
- `02 - Sources/Lectures/L9 - SESA3047.txt` (Thu 8 Oct, second half: transport and Coriolis accelerations, Earth models, position state equation; stopped before the dynamics)
- `02 - Sources/Lectures/L10 - SESA3047.txt` (Mon 12 Oct: §3.3 rotational dynamics, from linear momentum to Eq. 3.70)
- `04 - Labs & Coursework/Lab 1/Lab_1.pdf` (Lab 1, MATLAB: DCMs and gimbal lock, nonlinear oscillator, rotational dynamics and kinematics)
- `04 - Labs & Coursework/Coursework 1/Brief/Coursework_1.pdf` (Coursework 1: attitude kinematics and wind components; flat-Earth rigid-body dynamics; due 29 Oct)
- `04 - Labs & Coursework/Coursework 1/SESA3047 Coursework 1 Submission.pdf` (my submitted answers, handwritten, 14 pages, 29 Oct)

> [!warning] Slips found in the Chapter 2 recordings
> L5 l. 376 drops the $-\sin\theta$ in $\mathbf C_z$; L5 l. 380 says $x$ for $z$; L6 l. 205 drops the minus in $\theta=-\arcsin C_{13}$; L6 l. 208 gives $\psi=\mathrm{atan2}(C_{12},C_{12})$ for $\mathrm{atan2}(C_{12},C_{11})$. All are flagged in [[SESA3047 2.2 - Direction Cosine Matrices and Euler Angles|2.2]].
>
> L7: the §2.4.6 vector said as "one one zero" (l. 11; it is $[1,0,0]^T$), the rotation order muddled at ll. 163–166, and "acceleration" for rate at l. 180. Flagged in [[SESA3047 2.2 - Direction Cosine Matrices and Euler Angles|2.2]] and [[SESA3047 3.1 - Rotational Kinematics and Euler-Angle Rates#Transcript slips (L7)|3.1]].
>
> L8–L9: "just p" for the reduced Euler-rate set (L8 l. 47; only the first row reduces), "reference frame P" for B in the transport theorem (L8 l. 224), "a" used for both acceleration and frame (L8 ll. 348–413), and $\mathbf C^T$ described as "FRD to NED to NED" (L9 ll. 245–246). Flagged in [[SESA3047 3.1 - Rotational Kinematics and Euler-Angle Rates#Transcript slips (L8)|3.1]] and [[SESA3047 3.2 - Translational Kinematics and Accelerations in Moving Frames#Transcript slips (L8 and L9)|3.2]].
>
> L10: "$J_x$ is the integral of y plus z square" (l. 227; $y^2+z^2$), $\tilde{\mathbf r}^2$ read as "R squared" (l. 212), and two loose justifications: the cm integral vanishing "because of plus and minus" (ll. 161–164), and $\dot{\mathbf J}=\mathbf 0$ "because the mass is fixed" (ll. 283–284; it needs rigidity). Flagged in [[SESA3047 3.3 - Rigid-Body Rotational Dynamics#Transcript slips (L10)|3.3]].

> [!warning] L11 recording slips
> Repeated acceleration components in ll. 91–92, garbled matrix dimensions in ll. 113–115 and recording artefacts including “11 pm” in ll. 198–201. The corrected algebra and exact scope are in [[SESA3047 4.1 - Inertia Models and Rotor Dynamics#Transcript slips and source qualifications|4.1]]. No new recoverable deadline is announced.

> [!warning] L14 recording slips
> *"Newton's third law"* for the second (l. 45); the tangent at $\pi$ given as *"y equals minus x"* (l. 94; it is $y=\pi-x$); *"epsilon squared W1"* said for both products of the $X$ equation (ll. 238–239); $X_g$ without its $m$ (l. 401); *"double angle formulas"* for the compound-angle ones (ll. 444, 497); $\theta$ and $\gamma$ called *"the same thing"* (l. 485; only at trim). Flagged in [[SESA3047 5.1 - State-Space Form and Linearisation#Transcript slips (L14)|5.1]] and [[SESA3047 5.2 - Longitudinal State-Space Model#Transcript slips (L14, gravity part)|5.2]]. Handout slips (Eqs. 5.21d, 5.32, 5.45) are in 5.3 and 5.4.

> [!warning] L12–L13 recording slips
> - L12: *"L, M, M"* and *"L, M, L"* for $L,M,N$ (ll. 23, 160); *"F, D, and R"* for FRD (l. 125); *"sum of the external momentum"* for moments (ll. 259, 312). The rotor momentum *"doesn't change in time"* (ll. 295–297) means only in the body frame.
> - Handout Eq. 4.10 reads *"$J_{xz}=J_{xz}$"* for $J_{xy}=J_{yz}=0$.
> - These are flagged in [[SESA3047 4.1 - Inertia Models and Rotor Dynamics#Transcript slips and source qualifications|4.1]].
> - L13: $\mathbf F/m+\mathbf G$ called *"the inertial forces"* (ll. 188–189); the true inertial forces are centrifugal and Coriolis. Flagged in [[SESA3047 4.2 - Translational Dynamics#Transcript slips (L13)|4.2]].
> - L13: *"on the right side, they have a derivative in time"* (ll. 318–319); the derivatives are on the left. Flagged in [[SESA3047 4.3 - Complete Flat-Earth 6-DOF Model#Transcript slips (L13 ll. 310–344)|4.3]].
