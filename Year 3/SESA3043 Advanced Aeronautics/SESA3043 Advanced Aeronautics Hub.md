---
title: "SESA3043 Advanced Aeronautics Hub"
module: "SESA3043 Advanced Aeronautics"
type: hub
aliases: ["SESA3043 Advanced Aeronautics"]
tags: [sesa3043, hub, moc]
status: in-progress
coverage: "Chapters 1–3 (Ch1 fully lectured, last on 2 Oct; Ch2 and Ch3 written ahead from slides)"
---

# SESA3043 Advanced Aeronautics Hub

> [!abstract] Module at a glance
> **Conservation laws and governing equations** → **potential flow** (superposition, complex potential, conformal mapping) → **lumped-vortex and panel methods** → **viscous boundary layers** → **rotor aerodynamics** → **environmental impact**.
>
> Vault coverage: **all of Chapters 1–3**. **Chapter 1 is fully lectured**: CH1-4 (boundary layers) was given on Fri 2 Oct, followed by the Chapter 1 tutorial. Chapter 2 and the whole of Chapter 3 (methods for boundary layers) were written **ahead of the lectures** from the slides and Blackboard notes; add lecture line references when the transcripts arrive. Quick reference: [[SESA3043 Formula Sheet]].

## Current coverage

**Chapter 1: Conservation laws**

1. [[SESA3043 1.1 - Mathematical Tools and Flow Description]]
2. [[SESA3043 1.2 - Conservation Laws and Governing Equations]]
3. [[SESA3043 1.3 - Potential-Flow Review]] (Week 1)
4. [[SESA3043 1.3 - Complex Potential, Wedge Flows and Unsteady Bernoulli]] (lectured 1 Oct)
   - cylinder by superposition (four steps) and the lifting cylinder;
   - complex potential, Cauchy–Riemann, complex potentials of all elementary flows;
   - general doublet; wedge and corner flows from $\Phi=-kz^{m+1}$;
   - unsteady Bernoulli (Blackboard notes), start-up and added-mass examples.
5. [[SESA3043 1.4 - Two-Dimensional Incompressible Boundary Layers]] (lectured 2 Oct, transcript folded in)
   - order-of-magnitude derivation of the BL equations; $\partial p/\partial y=0$; $\delta/L\sim Re^{-1/2}$; parabolic marching; Blasius check; lecture slips flagged.

**Chapter 2: Exact solutions and methods for potential flow** (written ahead)

6. [[SESA3043 2.1 - Complex Functions and Conformal Mapping]]: conformal maps, plate normal to a stream, Joukowski and Kármán–Trefftz aerofoils, Kutta condition.
7. [[SESA3043 2.2 - Lumped Vortex Method]]: flat plate, tandem, ground effect, camber, biplane.
8. [[SESA3043 2.3 - Panel Methods]]: source/vortex/doublet panels, both complete methods, code, validation.

**Chapter 3: Methods for boundary layers** (written ahead, 6 Oct)

9. [[SESA3043 3.1 - Boundary-Layer Concepts and Thickness Measures]]: $\delta_{99}$, $\delta^*$, $\theta$ (control-volume derivation of $D=\rho U_e^2\theta$), $C_f$, $H$.
10. [[SESA3043 3.2 - Blasius and Falkner-Skan Similarity Solutions]]: both derived in full; integrals A and B; Falkner–Skan table recomputed; cylinder stagnation example; wedge $\beta=0.3$.
11. [[SESA3043 3.3 - Pohlhausen Method and Pressure Gradients]]: the quartic and $\lambda$; separation at $\lambda=-12$; laminar vs turbulent separation (sphere, golf ball, cricket ball).
12. [[SESA3043 3.4 - Transition to Turbulence]]: roadmap, Orr–Sommerfeld derived, thumb plot, $e^n$ method.
13. [[SESA3043 3.5 - Momentum Integral Equation]]: the MIE derived in six steps; closures (Pohlhausen, Thwaites); ship-fouling example.
14. [[SESA3043 3.6 - Viscous-Inviscid Interaction]]: SDM and STM, $v_s=\mathrm d(U_e\delta^*)/\mathrm dx$; XFOIL; wind-tunnel VII example; **coursework** pointer.

**Worked solutions:** [[SESA3043 Ch1 Revision Questions - Worked Solutions]] · [[SESA3043 Ch2 Revision Questions - Worked Solutions]] · [[SESA3043 Ch3 Revision Questions - Worked Solutions]]

## Week 1 concept map

| Flow description | Conservation and constitutive laws | Reduced models |
|---|---|---|
| [[Eulerian and Lagrangian Flow Descriptions]] | [[Reynolds Transport Theorem]] | [[Incompressible Navier-Stokes Equations]] |
| [[Material Derivative]] | [[Continuity Equation in Conservative Form]] | [[Streamfunction and Velocity Potential]] |
| [[Fluid Flow Rate, Flux and Specific Quantity]] | [[Newtonian Stress Tensor]] | [[Elementary Potential Flows]] |
| [[Flux Integrals]] | [[Compressible Navier-Stokes Conservation Form]] | [[Bernoulli Equation]] |

## Chapter 1 (second half) and Chapter 2 concept map

| Potential-flow toolkit | Viscous layer | Numerical and exact methods |
|---|---|---|
| [[Complex Velocity Potential]] | [[Prandtl Boundary-Layer Equations]] | [[Conformal Mapping]] |
| [[General Doublet]] | [[Order-of-Magnitude Analysis]] | [[Joukowski Transformation]] |
| [[Wedge and Corner Flows]] | [[Displacement and Momentum Thickness]] (SESA2022) | [[Kármán–Trefftz Transformation]] |
| [[Unsteady Bernoulli Equation]] | [[Boundary Layer Separation]] (SESA2022) | [[Lumped Vortex Method]] |
| [[Flow Past a Cylinder]] (SESA2022) | | [[Panel Method]] |
| [[Kutta-Joukowski Theorem]] (SESA2022) | | [[Kutta Condition]] · [[Method of Images]] (SESA2022) |

## Chapter 3 concept map

| Describing a layer | Solving it | Using it |
|---|---|---|
| [[Displacement and Momentum Thickness]] (SESA2022) | [[Blasius and Falkner-Skan Similarity Solutions]] | [[Viscous-Inviscid Interaction]] |
| [[Boundary-layer Thickness Measures]] (SESA1016) | [[Pohlhausen Method]] | [[Panel Method]] |
| [[Boundary Layer Separation]] (SESA2022) | [[Momentum Integral Equation]] (SESA2022) | [[Linear Stability and Transition Prediction]] |
| [[Prandtl Boundary-Layer Equations]] | [[Shooting Method and the Blasius Solution]] (SESA2029) | [[Law of the Wall]] (SESA2022) |

## Module roadmap

| Block | Material | Vault status |
|---|---|---|
| Chapter 1.1–1.2 | Notation, Eulerian/Lagrangian, mass, momentum and energy equations | **Complete** (lectured) |
| Chapter 1.3 | Potential-flow review, complex potential, general doublet, wedge flows | **Complete** (lectured, last 1 Oct) |
| Chapter 1.4 | 2-D incompressible boundary layers | **Complete** (lectured Fri 2 Oct, then the Ch1 tutorial on revision Q 1.3.2–1.3.3) |
| Chapter 2.1 | Conformal mapping, Joukowski, Kármán–Trefftz | **Written ahead** |
| Chapter 2.2 | Lumped vortex method | **Written ahead** |
| Chapter 2.3 | Panel methods | **Written ahead** |
| Chapter 3.1–3.6 | Methods for boundary layers: thickness measures, Blasius, Falkner–Skan, Pohlhausen, transition, MIE, VII | **Written ahead from slides** (6 Oct), after Chapter 2 in the lecture order |
| Later chapters | Rotor aerodynamics, environmental impact (Chapters 4–5) | Awaiting material |

> [!info] Animated source decks
> The supplied PDFs contain a separate page for many PowerPoint animation states. Pages whose content is entirely contained in the next page were skipped automatically (CH1-3: 35 of 59 distinct; CH1-4: 19 of 41; panel explainer: 32 of 42; Ch2 deck: no builds).

## Assessment and deadlines

The Week 1 lecture states:

- **80%** two-hour closed-book final exam;
- **20%** coursework, released around the start of **Week 8** and due before the end of **Week 11**. Ch2 slide 20: *"Part of the CW will be: generate KT aerofoil with given code and perform potential flow calculations"*. Prepare with [[SESA3043 2.1 - Complex Functions and Conformal Mapping#5. The Kármán–Trefftz aerofoil (slides 19–20)|2.1 §5]] and [[SESA3043 2.3 - Panel Methods|2.3]];
- marks reward a complete method and clearly stated assumptions, not only the final number.

**Coursework tools** (CH3-6 slide 25): see the *Coursework Code Explainer* on Blackboard; use **XFOIL** or XFLR5. The theory is [[SESA3043 3.6 - Viscous-Inviscid Interaction|3.6]].

**Tutorial format** (L5, ll. 507–510): the second Friday lecture at the end of each chapter (five chapters) is a tutorial; work through the revision questions while the chapter is being taught and bring the ones you cannot do.

**Other dates:** study-abroad information session **28 Oct, 10:00–12:30, Building 7 room 309** (L5, ll. 24–25; international placement year and summer schools).

From the 1 Oct lecture (L4, ll. 6–16): Friday 2 Oct second half is a **tutorial**; email or post on the discussion board which **Chapter 1 revision questions** you want covered. Equation booklets were handed out (one each).

Check Blackboard for authoritative dates and later changes.

## Exam skills

**Week 1**

- translate between vector, tensor/index and component notation;
- distinguish Eulerian and Lagrangian descriptions and connect them with the material derivative;
- derive local conservation equations from a control-volume statement;
- convert conservative to non-conservative form;
- identify every force and flux in the momentum and energy equations;
- state the assumptions that reduce the compressible equations to incompressible Navier–Stokes, Euler, potential flow and Bernoulli;
- interpret $\phi$ and $\psi$, including why $\Delta\psi$ equals volume flow per unit span.

**Chapter 1 (second half)**

- build a body by superposition: superpose, set $\psi=$ const, find the geometry, differentiate, apply Bernoulli;
- derive $\mathrm d\Phi/\mathrm dz=u-iv$ from Cauchy–Riemann, and write $\Phi$ for every elementary flow (state the vortex sign convention);
- derive the general doublet from a source–sink pair with a Taylor expansion;
- find the body and velocity for $\Phi=-kz^{m+1}$ and interpret $m$;
- derive unsteady Bernoulli and use the $\partial\phi/\partial t$ term;
- derive the BL equations by order of magnitude; explain $\partial p/\partial y=0$, $\delta\sim Re^{-1/2}$ and parabolic marching; explain why the BL equations are written with $U_e\,\mathrm dU_e/\mathrm dx$ rather than $\mathrm dp/\mathrm dx$ (L5, ll. 377–388).

**Chapter 2**

- explain why an analytic map preserves angles and carries potential flows;
- solve flow onto a finite plate by mapping, including $C_p$;
- construct Joukowski aerofoils, derive $b/c$, and derive $\Gamma$ from the Kutta condition;
- set up and solve lumped-vortex problems (tandem, ground effect, camber, biplane) and explain why $c/4$ and $3c/4$;
- derive the source, vortex and doublet panel influence formulae and their self-induced limits;
- describe both complete panel methods, their Kutta conditions, and how to get $C_L$ and $C_p$.

**Chapter 3**

- define $\delta_{99}$, $\delta^*$, $\theta$, $H$, $C_f$ and derive $D=\rho U_e^2\theta$ and $\mathrm d\theta/\mathrm dx=C_f/2$ by control volume;
- evaluate them for an assumed profile (linear, Pohlhausen);
- derive the Blasius and Falkner–Skan equations from the stream-function BL equation; explain similarity and guess-and-shoot;
- get $\delta^*$, $\theta$, $C_f$, $H$ from $\eta^*$, $\theta^*$, $f''(0)$, including $\theta^*=f''(0)$ by parts; use the Falkner–Skan table for a wedge or a stagnation point;
- derive the Pohlhausen profile and $\lambda$; state separation at $\lambda=-12$; discuss the factors that promote separation and how to delay it;
- describe natural and bypass transition; derive the Orr–Sommerfeld equation; read a thumb plot; apply the $e^n$ method;
- follow (SESA6087: reproduce) the MIE derivation; reduce it for a flat plate;
- compare SDM and STM; derive $v_s=\mathrm d(U_e\delta^*)/\mathrm dx$; iterate a simple VII problem.

## All notes

```dataview
TABLE type, status, coverage, file.mtime AS "Updated"
FROM "Year 3/SESA3043 Advanced Aeronautics"
WHERE type
SORT type ASC, file.name ASC
```

## Builds on / feeds into

- **From** [[SESA1016 Thermofluids Hub]]: [[Material Derivative]], [[Mass Flow Rate]], [[Momentum Flux]], [[Bernoulli Equation]].
- **From** [[MATH2048 Mathematics for Engineering and the Environment Part II Hub]]: vector calculus and [[Flux Integrals]]; **from** MATH1054: [[Complex Numbers - Cartesian, Polar and Exponential Forms]].
- **From** [[SESA2022 Aerodynamics Hub]]: [[SESA2022 T3 - Potential Flow]], [[SESA2022 T4 - Thin Aerofoil Theory]], [[SESA2022 T2 - Boundary Layers]].
- **From** [[SESA2029 Digital Aerospace Methods Hub]]: [[Navier-Stokes Equations]], the computational conservation form, and the Blasius shooting method.
- **Alongside** [[SESA3029 Aerothermodynamics Hub]]: compressible flow; supersonic aerodynamic centre at $c/2$.

## Sources

- `02 - Sources/Lectures/CH1-2 Governing Equations(1).pdf`
- `02 - Sources/Lectures/CH1-3 Potential Flow.pdf`
- `02 - Sources/Lectures/CH1-4 2D Incompressible BL(1).pdf`
- `02 - Sources/Lectures/Ch1_Notes_Unsteady Bernoulli Eqn.pdf`
- `02 - Sources/Lectures/Ch2 Exact Solution and methods for potential flow.pdf`
- `02 - Sources/Lectures/Ch2_Notes_LVM_Tandem Aerofoils.pdf`, `Ch2_Notes_LVM_Ground Effect.pdf`, `Ch2_Notes_LVM_Cambered Aerofoil.pdf`
- `02 - Sources/Lectures/Ch2_Notes_Panel Method.pdf`, `Ch2_Panel_Method_Explainer.pdf`
- Transcripts: `L1 - SESA3043.txt`, `L2 - SESA3043.txt`, `L3 - SESA3043.txt` (Week 1); `L4 - SESA3043.txt`; `02 October 2026 at 14_53_48.txt` (**L5**, CH1-4) and `02 October 2026 at 15_51_44.txt` (Ch1 tutorial)
- `02 - Sources/Lectures/CH3-1 Introduction(1).pdf`, `CH3-2 Blasius and Falkner-Skan(1).pdf`, `CH3-3 Pohlhausen.pdf`, `CH3-4 Transition to Turbulence(1).pdf`, `CH3-5 Momentum Integral Eqn(1).pdf`, `CH3-6 Viscous Inviscid Interaction.pdf`
- `02 - Sources/Lectures/Ch3_Notes_Blasius.pdf`, `Ch3_Notes_Falkner-Skan.pdf`, `Ch3_Notes_Pohlhausen.pdf`
- `03 - Exams & Past Papers/Ch3_Revision_Questions.pdf`
- `03 - Exams & Past Papers/Ch1_Revision_Questions.pdf`, `Ch2_Revision_Questions.pdf`

> [!warning] Slips found in the sources (all flagged in the notes)
> CH1-3 slide 23: $\phi$ bracket should be $1+R^2/r^2$. Slides 21/37: vortex row mixes sign conventions. Unsteady-Bernoulli notes Eq. 1: missing $\times\mathbf u$. CH1-4 slide 37: "matching" means marching. Ch2 slide 5: $\varphi$ for $\psi$. Slide 10: missing signs in the circle map. Slide 17: circle centre shift dropped. Slide 28: control point is $x_T$, not $x_L$. LVM camber notes: $\Gamma_2$ distance at $T_2$ is $c/4$, not $3c/4$. Slide 47: $\sigma$ for $\mu$. Slide 51 and explainer p. 25: vortex $w$ sign and the rotation formula. Ch3 notes: Falkner–Skan boxed Eq. 8 has $f'f''$ for $ff''$; Pohlhausen p. 2 bracket has $+\eta^3$ for $-\eta^3$; Blasius $\eta_{99}$ read as 3.5 (exact 3.47, so $\delta_{99}/x=4.91$, not 5.0, $/\sqrt{Re_x}$). L5 (2 Oct): "matching" for marching again, and several spoken slips, flagged in [[SESA3043 1.4 - Two-Dimensional Incompressible Boundary Layers#Transcript slips (L5)|1.4]].
