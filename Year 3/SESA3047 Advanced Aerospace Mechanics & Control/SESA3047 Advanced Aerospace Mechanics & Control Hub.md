---
title: "SESA3047 Advanced Aerospace Mechanics & Control Hub"
module: "SESA3047 Advanced Aerospace Mechanics & Control"
type: hub
aliases: ["SESA3047 Advanced Aerospace Mechanics & Control"]
tags: [sesa3047, hub, moc]
status: in-progress
coverage: "Chapters 1–4; Chapter 4 §§4.1.1–4.1.2 lectured in L11, rest written from the handout; Lab 1 filed"
---

# SESA3047 Advanced Aerospace Mechanics & Control Hub

> [!abstract] Module at a glance
> Chapter 1 establishes the language of advanced six-degree-of-freedom mechanics and control: **dynamic systems** → **control architectures** → **purpose-built models** → **states and model classes** → **kinematics, dynamics and reference frames**. Chapter 2 builds the kinematic toolkit: **dot and cross products** → **the transport theorem** → **direction cosine matrices** → **Euler angles and gimbal lock**.
>
> Chapter 3 turns the toolkit into the first state equations of the 6-DOF model: **Euler-angle rates from body rates** → **velocity and acceleration in moving frames** → **position from body velocity** → **angular momentum and the inertia matrix** → **the rotational dynamic equation**.
>
> Current vault coverage: **Chapters 1–4**. Chapters 1–2 are lectured (L2–L7); Chapter 3 is backfilled through L10, with the explicit derivative revisited in L11. **L11** continues into Chapter 4: full inertia expansion and principal axes (§§4.1.1–4.1.2). **The complete Chapter 4 handout is now written up**: aircraft symmetry, internal rotors, translational dynamics and the 12-state model. Beyond §4.1.2 is written ahead, awaiting transcripts. **Lab 1** is filed (see [[#Labs and coursework]]). Quick reference: [[SESA3047 Formula Sheet]].

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
   - gyroscopic coupling, imbalance and the intermediate-axis theorem; how the 6-DOF equations fit together.

8. [[SESA3047 4.1 - Inertia Models and Rotor Dynamics]] (Chapter 4 §4.1; full matrix and principal axes lectured in L11; aircraft/rotors written ahead)
   - full moment expansion, eigenvector interpretation, aircraft block inverse and internal rotor momentum;
   - symbolic algebra checks and suggested numerical examples; transcript corrections with line references.
9. [[SESA3047 4.2 - Translational Dynamics]] (Chapter 4 §4.2; written from handout, awaiting transcript)
   - rotating Earth, effective gravity, flat Earth and transport into body axes;
   - both force conventions and a checked numerical derivative.
10. [[SESA3047 4.3 - Complete Flat-Earth 6-DOF Model]] (Chapter 4 §4.3; written from handout, awaiting transcript)
   - all twelve states, solver evaluation, full derivative example and an exact ballistic integration check.

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

## Coverage boundary

The current sources are **Chapters 1–4**. L11 reaches the principal-axis case, Chapter 4 §4.1.2. The remaining Chapter 4 material is written from the lecture-note PDF with no matching transcript yet. Later material such as trim, linearisation, stability, controllability, observability and control design remains outside current coverage.

| Material | Vault status |
|---|---|
| Chapters 1–2 | **Complete**, lectured (L2–L7) |
| Chapter 3 §§3.1.1–3.1.3 | **Complete**, lectured in L7 (Mon 5 Oct) |
| Chapter 3 §§3.1.4–3.2 | **Complete**, lectured in L8–L9 (Thu 8 Oct); line references, slips and tasks folded in |
| Chapter 3 §3.3 | **Complete**, lectured in L10 (Mon 12 Oct); line references, slips and tasks folded in |
| Chapter 3 §3.4 | From the notes; not lectured as a separate item (L10 ended at Eq. 3.70) |
| Chapter 4 §§4.1.1–4.1.2 | **Complete**, lectured in L11; expansion, principal axes and slips backfilled |
| Chapter 4 §§4.1.3–4.3 | **Complete from the handout**, written ahead; aircraft symmetry, rotors, translation and 12-state model |
| Later chapters | Awaiting material |

> [!info] Build policy
> Covered chapter notes are marked complete. The hub and formula sheet remain in progress. Chapter 4 was written in full from the lecture-note handout on 19 Oct; L11 defines the lectured boundary at §4.1.2. Future transcripts should backfill line references, slips and tasks in 4.1–4.3. Any Thursday recording(s) beyond the supplied L11 are **to be picked up next run** when available; no later matching transcript is currently filed.

## Labs and coursework

> [!important] Lab 1: *Dynamic Analysis via Numerical Simulations* (MATLAB)
> File: `04 - Labs & Coursework/Lab 1/Lab_1.pdf` (6 pages, Dr Cristiano Martinelli). It feeds the **lab report, worth 20% of the module mark**. No submission date is printed on the sheet: check Blackboard. Aim to finish at least Exercises 1 and 2 in the session; demonstrators will check your plots.
>
> | Exercise | Task | Theory in the vault |
> |---|---|---|
> | 0 (intro) | MATLAB matrices, element-wise operators, `ode45` with a first-order state vector | [[SESA3047 1.1 - Dynamic Systems and Control Architectures\|1.1]] (state form) |
> | 1 | Build $\mathbf C_{FRD/NED}=\mathbf C_x\mathbf C_y\mathbf C_z$; transform north for $\psi=\pm30^\circ$; recover $(20^\circ,15^\circ,30^\circ)$ with atan2/arcsin; probe $\theta=89^\circ, 89.9^\circ, 90^\circ$ | [[SESA3047 2.2 - Direction Cosine Matrices and Euler Angles\|2.2]] §§6–10, [[Gimbal Lock]] |
> | 2 | Nonlinear (Duffing) oscillator $m\ddot x+c\dot x+kx+\mu x^3=f\cos\omega t$; linear vs nonlinear, small vs large amplitude, free and forced | [[SESA3047 1.2 - Dynamic Models, Frames and Earth Models\|1.2]], [[Linear, Nonlinear and Time-Varying Models]] |
> | 3 | Integrate the rotational dynamics with the Euler-angle kinematics (Eqs. 3.10–3.11, 3.63–3.71); interpret geometric and inertial coupling | [[SESA3047 3.1 - Rotational Kinematics and Euler-Angle Rates#The lecture's coupling example (L8, ll. 44–68)\|3.1 §7]], [[SESA3047 3.3 - Rigid-Body Rotational Dynamics\|3.3]] |
>
> The lecturer tied the coupling discussion to the lab: *"we will see how this affects the numerical simulations"* (L8, ll. 67–68). Lab 2 will use Simulink (Lab 1, p. 1).

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
- derive $\dot{\boldsymbol\omega}=\mathbf J^{-1}(\mathbf M-\tilde{\boldsymbol\omega}\mathbf J\boldsymbol\omega)$, reduce it to Euler's equations, and explain the gyroscopic term;
- list the 6-DOF state equations so far, and which are kinematics and which dynamics.

## Chapter 4 exam skills

The first two topics below are discussed in L11; the remaining topics are practice from the handout, not new lecturer-set exam requirements.

- expand the full inertia equation by finding momentum components first (L11 ll. 81–180);
- explain the eigenvector definition of principal axes and why FRD axes need not be principal (L11 ll. 181–228);
- derive the aircraft roll–yaw inverse and check its zero-product limit;
- include both the gyroscopic and spin-up contributions of rotor momentum;
- derive rotating-Earth and flat-Earth translational dynamics; distinguish effective gravity from gravitation;
- translate between gravity-excluding and gravity-including body-force conventions;
- assemble the twelve states in the handout's order and distinguish all four equation groups;
- explain solver evaluation order and check it against the yawing ballistic example.

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

## Sources

- Chapter_4.pdf (10 pages: inertia models, rotors, translational dynamics and complete 6-DOF state model).
- L11 - SESA3047.txt (232 lines: explicit derivative, full inertia expansion and principal axes; stops at §4.1.2).

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
