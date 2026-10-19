---
title: "SESA3043 Advanced Aeronautics Hub"
module: "SESA3043 Advanced Aeronautics"
type: hub
aliases: ["SESA3043 Advanced Aeronautics"]
tags: [sesa3043, hub, moc]
status: in-progress
coverage: "Chapters 1–3 (Ch1 and Ch2 fully lectured, the last on 16 Oct; Ch3 written ahead from slides, lectures from w/c 19 Oct)"
---

# SESA3043 Advanced Aeronautics Hub

> [!abstract] Module at a glance
> **Conservation laws and governing equations** → **potential flow** (superposition, complex potential, conformal mapping) → **lumped-vortex and panel methods** → **viscous boundary layers** → **rotor aerodynamics** → **environmental impact**.
>
> Vault coverage: **all of Chapters 1–3**. **Chapter 1 is fully lectured**: CH1-4 (boundary layers) was given on Fri 2 Oct, followed by the Chapter 1 tutorial.
>
> **Chapter 2 is complete** (Dr Zhiwei Hu), and every note is backfilled with line references:
> - Thu 8 Oct and Fri 9 Oct (first half): all of conformal mapping, §2.1, plus a Blackboard demo recording.
> - Fri 9 Oct (second half): the lumped vortex method up to the tandem example, §2.2.
> - **Thu 15 Oct:** ground effect by mirror images, racing-car front wings, and the camber extension (§2.2).
> - **Fri 16 Oct:** the camber example finished, $C_L=2\pi(\alpha+0.12)$; then the whole panel method, both lectures (§2.3).
> - **The coursework code** (`dpan`, `ktreff`) was posted on 16 Oct and is tested in [[SESA3043 2.3 - Panel Methods#10. The Blackboard coursework code (dpan and ktreff)|2.3 §10]]. The Python `dpan.py` **crashes on NumPy 2**, and `ktreff.py` gives a bad point count for some $n$. Fixed copies are in `04 - Labs & Coursework/Panel Method Coursework/`.
>
> **Next:** Chapter 3 (viscous flow) with Dr Dea Wangsawijaya from the week of 19 Oct (2.3 PM2, l. 623). All of Chapter 3 is **written ahead** from the slides and Blackboard notes, including the new MIE handout. Add line references when the transcripts arrive. Quick reference: [[SESA3043 Formula Sheet]].

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

**Chapter 2: Exact solutions and methods for potential flow**

6. [[SESA3043 2.1 - Complex Functions and Conformal Mapping]] (**lectured 8–9 Oct**, transcripts folded in): conformal maps, plates normal to and along a stream, Joukowski and Kármán–Trefftz aerofoils, Kutta condition, the demo sweep, and what the exam can ask.
7. [[SESA3043 2.2 - Lumped Vortex Method]] (**lectured 9, 15 and 16 Oct**): flat plate, tandem (with an unequal-chord challenge solved), ground effect, camber, biplane; the exam's small-angle traps.
8. [[SESA3043 2.3 - Panel Methods]] (**lectured 16 Oct**): source/vortex/doublet panels, both complete methods, what is examinable (process, not arithmetic), the Blackboard code tested and fixed, validation.

**Chapter 3: Methods for boundary layers** (written ahead, 6 Oct)

9. [[SESA3043 3.1 - Boundary-Layer Concepts and Thickness Measures]]: $\delta_{99}$, $\delta^*$, $\theta$ (control-volume derivation of $D=\rho U_e^2\theta$), $C_f$, $H$.
10. [[SESA3043 3.2 - Blasius and Falkner-Skan Similarity Solutions]]: both derived in full; integrals A and B; Falkner–Skan table recomputed; cylinder stagnation example; wedge $\beta=0.3$.
11. [[SESA3043 3.3 - Pohlhausen Method and Pressure Gradients]]: the quartic and $\lambda$; separation at $\lambda=-12$; laminar vs turbulent separation (sphere, golf ball, cricket ball).
12. [[SESA3043 3.4 - Transition to Turbulence]]: roadmap, Orr–Sommerfeld derived, thumb plot, $e^n$ method.
13. [[SESA3043 3.5 - Momentum Integral Equation]]: the MIE derived in six steps (matches the new Blackboard handout equation for equation); closures (Pohlhausen, Thwaites); ship-fouling example.
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
| Chapter 2.1 | Conformal mapping, Joukowski, Kármán–Trefftz | **Complete** (lectured Thu 8 and Fri 9 Oct, transcripts) |
| Chapter 2.2 | Lumped vortex method | **Complete** (lectured Fri 9, Thu 15 and Fri 16 Oct, transcripts) |
| Chapter 2.3 | Panel methods | **Complete** (lectured Fri 16 Oct, two transcripts; coursework code tested) |
| Chapter 3.1–3.6 | Methods for boundary layers: thickness measures, Blasius, Falkner–Skan, Pohlhausen, transition, MIE, VII | **Written ahead from slides** (6 Oct; MIE handout added 19 Oct); lectures by Dr Wangsawijaya from w/c 19 Oct |
| Later chapters | Rotor aerodynamics, environmental impact (Chapters 4–5) | Awaiting material |

> [!info] Animated source decks
> The supplied PDFs contain a separate page for many PowerPoint animation states. Pages whose content is entirely contained in the next page were skipped automatically (CH1-3: 35 of 59 distinct; CH1-4: 19 of 41; panel explainer: 32 of 42; Ch2 deck: no builds).

## Assessment and deadlines

The Week 1 lecture states:

- **80%** two-hour closed-book final exam;
- **20%** coursework, released around the start of **Week 8** and due before the end of **Week 11**. Ch2 slide 20: *"Part of the CW will be: generate KT aerofoil with given code and perform potential flow calculations"*. Confirmed in the 8 Oct lecture (ll. 424–426): the KT generation is *"the first part of your coursework"* (9 Oct, l. 456). The code (MATLAB and Python) is on Blackboard under Chapter 2; use angles in radians. On 16 Oct the lecture added that the coursework comes **after the viscous chapter**, with a dedicated session (2.3 PM2, ll. 612–623). **Python users:** the Blackboard `dpan.py` fails on NumPy 2, and `ktreff.py` can return a duplicate point, so use the fixed copies or the MATLAB files ([[SESA3043 2.3 - Panel Methods#10. The Blackboard coursework code (dpan and ktreff)|2.3 §10]]). Prepare with [[SESA3043 2.1 - Complex Functions and Conformal Mapping#5. The Kármán–Trefftz aerofoil (slides 19–20)|2.1 §5]] and [[SESA3043 2.3 - Panel Methods|2.3]];
- marks reward a complete method and clearly stated assumptions, not only the final number.

**Coursework tools** (CH3-6 slide 25): see the *Coursework Code Explainer* on Blackboard; use **XFOIL** or XFLR5. The theory is [[SESA3043 3.6 - Viscous-Inviscid Interaction|3.6]].

**Tutorial format** (L5, ll. 507–510): the second Friday lecture at the end of each chapter (five chapters) is a tutorial; work through the revision questions while the chapter is being taught and bring the ones you cannot do. For Chapter 2 the tutorial is being **pushed back** at the class's request, to allow time on the revision questions. Their solutions are withheld until then (9 Oct LVM lecture, ll. 436–444).

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
- **by hand** (stated as examinable, 9 Oct, ll. 486–495): flow onto a finite plate and flow along a plate by mapping, transforming geometry then solution, to $u$, $v$ and $C_p$;
- **logic only, no calculation** (same lines): the steps that turn a cylinder into a Joukowski or KT aerofoil (shift left for thickness, up for camber, through $\bar z=b$ for a sharp TE); derive $b/c$ and $\Gamma$ from the Kutta condition;
- set up and solve lumped-vortex problems (tandem, ground effect, camber, biplane) and explain why $c/4$ and $3c/4$; write every induced velocity as a downwash (9 Oct LVM, ll. 358–369);
- in ground effect, take only the image's velocity component **normal to the plate** (15 Oct, ll. 97–116); with camber, resolve the free stream normal to **each segment**, and use small-angle approximations so the equations stay solvable (16 Oct, ll. 77–84);
- derive the source, vortex and doublet panel influence formulae and their self-induced limits;
- describe both complete panel methods, their Kutta conditions, and how to get $C_L$ and $C_p$. The exam asks for the **process and logic**, not panel-by-panel calculation (16 Oct, ll. 376–394).

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
- Transcripts: `L1 - SESA3043.txt`, `L2 - SESA3043.txt`, `L3 - SESA3043.txt` (Week 1); `L4 - SESA3043.txt`; `02 October 2026 at 14_53_48.txt` (**L5**, CH1-4) and `02 October 2026 at 15_51_44.txt` (Ch1 tutorial); `08 October 2026 at 13_50_19.txt` (Ch2 L1, conformal mapping), `09 October 2026 at 14_57_18.txt` (Ch2 L2, Joukowski and KT), `09 October 2026 at 16_00_58.txt` (Ch2 L3, lumped vortex) and `09 October 2026 at 14_17_51.txt` (Joukowski demo recording); `15 October 2026 at 13_48_35.txt` (ground effect, camber); `16 October 2026 at 14_54_40.txt` and `16 October 2026 at 15_53_48.txt` (camber finished; panel method)
- Coursework code: `02 - Sources/Lectures/dpan.m`, `dpan.py`, `ktreff.m`, `ktreff.py` (posted 16 Oct)
- `02 - Sources/Lectures/CH3-1 Introduction(1).pdf`, `CH3-2 Blasius and Falkner-Skan(1).pdf`, `CH3-3 Pohlhausen.pdf`, `CH3-4 Transition to Turbulence(1).pdf`, `CH3-5 Momentum Integral Eqn(1).pdf`, `CH3-6 Viscous Inviscid Interaction.pdf`
- `02 - Sources/Lectures/Ch3_Notes_Blasius.pdf`, `Ch3_Notes_Falkner-Skan.pdf`, `Ch3_Notes_Pohlhausen.pdf`, `Ch3_Notes_Momentum Integral Eq.pdf` (filed 19 Oct)
- `03 - Exams & Past Papers/Ch3_Revision_Questions.pdf`
- `03 - Exams & Past Papers/Ch1_Revision_Questions.pdf`, `Ch2_Revision_Questions.pdf`

> [!warning] Slips found in the sources (all flagged in the notes)
> CH1-3 slide 23: $\phi$ bracket should be $1+R^2/r^2$. Slides 21/37: vortex row mixes sign conventions. Unsteady-Bernoulli notes Eq. 1: missing $\times\mathbf u$. CH1-4 slide 37: "matching" means marching. Ch2 slide 5: $\varphi$ for $\psi$. Slide 10: missing signs in the circle map. Slide 17: circle centre shift dropped. Slide 28: control point is $x_T$, not $x_L$. LVM camber notes: $\Gamma_2$ distance at $T_2$ is $c/4$, not $3c/4$. Slide 47: $\sigma$ for $\mu$. Slide 51 and explainer p. 25: vortex $w$ sign and the rotation formula. Ch3 notes: Falkner–Skan boxed Eq. 8 has $f'f''$ for $ff''$; Pohlhausen p. 2 bracket has $+\eta^3$ for $-\eta^3$; Blasius $\eta_{99}$ read as 3.5 (exact 3.47, so $\delta_{99}/x=4.91$, not 5.0, $/\sqrt{Re_x}$). L5 (2 Oct): "matching" for marching again, and several spoken slips, flagged in [[SESA3043 1.4 - Two-Dimensional Incompressible Boundary Layers#Transcript slips (L5)|1.4]]. Ch2 lectures (8–9 Oct): $\mathrm d\Phi/\mathrm dx$ for $\mathrm d\Phi/\mathrm dz$, "$-2\pi$ to $2\pi$" for $\pm2a$, the dropped square root in $\sqrt{4a^2-y^2}$, the parallel component said as $U_\infty\sin\alpha$, and $L=U_\infty\Gamma$ without $\rho$. Flagged in [[SESA3043 2.1 - Complex Functions and Conformal Mapping#Transcript slips (L-a and L-b)|2.1]] and [[SESA3043 2.2 - Lumped Vortex Method#Transcript slips (LV)|2.2]]. 15–16 Oct: ground-effect $\Gamma/\Gamma_\infty$ said as $1+1/(4\bar h^2)$ (correct $1+1/(4\bar h)^2$); camber slope $-0.08$ for $-0.18$; panels numbered "anti-clockwise" against the code's clockwise. Flagged in [[SESA3043 2.2 - Lumped Vortex Method#Transcript slips (GE, PM1)|2.2]] and [[SESA3043 2.3 - Panel Methods#Transcript slips (PM1, PM2)|2.3]].
