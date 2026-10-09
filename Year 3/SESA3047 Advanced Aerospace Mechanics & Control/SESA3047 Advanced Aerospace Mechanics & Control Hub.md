---
title: "SESA3047 Advanced Aerospace Mechanics & Control Hub"
module: "SESA3047 Advanced Aerospace Mechanics & Control"
type: hub
aliases: ["SESA3047 Advanced Aerospace Mechanics & Control"]
tags: [sesa3047, hub, moc]
status: in-progress
coverage: "Chapters 1–3 (Ch3 §3.1 lectured in L7; §§3.2–3.4 written ahead)"
---

# SESA3047 Advanced Aerospace Mechanics & Control Hub

> [!abstract] Module at a glance
> Chapter 1 establishes the language of advanced six-degree-of-freedom mechanics and control: **dynamic systems** → **control architectures** → **purpose-built models** → **states and model classes** → **kinematics, dynamics and reference frames**. Chapter 2 builds the kinematic toolkit: **dot and cross products** → **the transport theorem** → **direction cosine matrices** → **Euler angles and gimbal lock**.
>
> Chapter 3 turns the toolkit into the first state equations of the 6-DOF model: **Euler-angle rates from body rates** → **velocity and acceleration in moving frames** → **position from body velocity** → **angular momentum and the inertia matrix** → **the rotational dynamic equation**.
>
> Current vault coverage: **Chapters 1–3.** Chapters 1–2 are lectured (L2–L6; L7 finished the §2.4.6 example). Chapter 3 §3.1 was lectured in **L7** (Mon 5 Oct, up to the rotational kinematic equation); §§3.1.4–3.4 are **written ahead** from `Chapter-3.pdf`, expected Thu 8 Oct. Quick reference: [[SESA3047 Formula Sheet]].

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
5. [[SESA3047 3.1 - Rotational Kinematics and Euler-Angle Rates]] (Chapter 3, §3.1; lectured in L7)
   - Euler rates vs body rates $p,q,r$; composing the three rotation rates;
   - $\mathbf E(\boldsymbol\Phi)$ multiplied out; $\mathbf H=\mathbf E^{-1}$ derived; $\det\mathbf E=\cos\theta$ and gimbal lock;
   - small-angle form; flat-Earth interpretation; level-turn and gyro examples.
6. [[SESA3047 3.2 - Translational Kinematics and Accelerations in Moving Frames]] (Chapter 3, §3.2; written ahead)
   - transport velocity; the five-term acceleration with Coriolis and centripetal terms;
   - rotating vs flat Earth, apparent forces and their size;
   - body-axis acceleration $[\dot u+qw-rv,\dots]^T$; translational kinematic equation $\dot{\mathbf p}=\mathbf C^T\mathbf v$.
7. [[SESA3047 3.3 - Rigid-Body Rotational Dynamics]] (Chapter 3, §§3.3–3.4; written ahead)
   - linear momentum; angular momentum and the inertia matrix derived;
   - rotational dynamic equation, Euler's equations, the $J_{xz}$ aircraft form;
   - gyroscopic coupling, imbalance and the intermediate-axis theorem; how the 6-DOF equations fit together.

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

## Coverage boundary

The current sources are Chapters 1–3 of the lecture notes. Chapter 3 ends by saying the **translational dynamics** will be introduced in the next chapter, completing the 12-state nonlinear 6-DOF model. **Chapter 4 has not been uploaded yet.** Expected later topics: translational dynamics, the full 6-DOF equations, trim and linearisation, state-space models, stability, controllability, observability and control design.

| Material | Vault status |
|---|---|
| Chapters 1–2 | **Complete**, lectured (L2–L7) |
| Chapter 3 §§3.1.1–3.1.3 | **Complete**, lectured in L7 (Mon 5 Oct) |
| Chapter 3 §§3.1.4–3.4 | **Written ahead** from the notes; expected Thu 8 Oct (L7, l. 118: *"translational kinematics and the rotational dynamics"*) |
| Chapter 4 onwards | Awaiting notes |

> [!info] Build policy
> Covered chapter notes are marked complete. The module hub and formula sheet remain in progress so that later material can be added without restructuring the vault. By request (6 Oct), Chapter 3 was written up in full before all of it was lectured; when the Thursday 8 Oct recording arrives, add its line references to 3.1 §§7–9, 3.2 and 3.3, flag slips and convert suggested tasks to lecturer-set where appropriate.

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
- multiply out $\boldsymbol\omega=[\dot\phi,0,0]^T+\mathbf C_x(\phi)([0,\dot\theta,0]^T+\mathbf C_y(\theta)[0,0,\dot\psi]^T)$ to get $\mathbf E$, and invert it to $\mathbf H$; state $\det\mathbf E=\cos\theta$ and its link to gimbal lock;
- state and use the small-angle form, and say when it fails;
- derive $\mathbf v_{P/a}$ and the five-term $\mathbf a_{P/a}$ with the transport theorem; name every term; explain the factor 2;
- write Newton's law in a rotating Earth frame and identify centrifugal and Coriolis forces; justify the flat-Earth model;
- derive $[\dot u+qw-rv,\ \dot v+ru-pw,\ \dot w+pv-qu]^T$ and $\dot{\mathbf p}^{NED}=\mathbf C^T\mathbf v^{FRD}$;
- derive $\mathbf h=\mathbf J\boldsymbol\omega$ (cm term vanishes, $-\tilde{\mathbf r}^2$), define moments and products of inertia;
- derive $\dot{\boldsymbol\omega}=\mathbf J^{-1}(\mathbf M-\tilde{\boldsymbol\omega}\mathbf J\boldsymbol\omega)$, reduce it to Euler's equations, and explain the gyroscopic term;
- list the 6-DOF state equations so far, and which are kinematics and which dynamics.

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

- `02 - Sources/Lectures/Chapter 1.pdf`
- `02 - Sources/Lectures/L2 - SESA3047.txt`
- `02 - Sources/Lectures/L3 - SESA3047.txt`
- `02 - Sources/Lectures/Chapter 2.pdf`
- `02 - Sources/Lectures/L4 - SESA3047.txt` (end of Chapter 1 notation; dot and cross products)
- `02 - Sources/Lectures/L5 - SESA3047.txt` (centripetal example, angular velocity, transport theorem, DCM properties)
- `02 - Sources/Lectures/L6 - SESA3047.txt` (non-commutativity, Euler angles, extraction, gimbal lock; end of Chapter 2)
- `02 - Sources/Lectures/Chapter-3.pdf` (15 pages: rotational kinematics, translational kinematics, rigid-body rotational dynamics, appendix)
- `02 - Sources/Lectures/SESA3047 - L7.txt` (Mon 5 Oct: §2.4.6 worked example; §§3.1.1–3.1.3, ending at the rotational kinematic equation)

> [!warning] Slips found in the Chapter 2 recordings
> L5 l. 376 drops the $-\sin\theta$ in $\mathbf C_z$; L5 l. 380 says $x$ for $z$; L6 l. 205 drops the minus in $\theta=-\arcsin C_{13}$; L6 l. 208 gives $\psi=\mathrm{atan2}(C_{12},C_{12})$ for $\mathrm{atan2}(C_{12},C_{11})$. All are flagged in [[SESA3047 2.2 - Direction Cosine Matrices and Euler Angles|2.2]].
>
> L7: the §2.4.6 vector said as "one one zero" (l. 11; it is $[1,0,0]^T$), the rotation order muddled at ll. 163–166, and "acceleration" for rate at l. 180. Flagged in [[SESA3047 2.2 - Direction Cosine Matrices and Euler Angles|2.2]] and [[SESA3047 3.1 - Rotational Kinematics and Euler-Angle Rates#Transcript slips (L7)|3.1]].
