---
title: "SESA3043 Advanced Aeronautics Hub"
module: "SESA3043 Advanced Aeronautics"
type: hub
aliases: ["SESA3043 Advanced Aeronautics"]
tags: [sesa3043, hub, moc]
status: in-progress
coverage: "Chapters 1–3 (Ch1 and Ch2 fully lectured; Ch3 lectured 22 Oct–12 Nov through CH3-5, the momentum integral equation; CH3-6 written ahead from slides)"
---

# SESA3043 Advanced Aeronautics Hub

> [!abstract] Module at a glance
> Conservation laws and governing equations → potential flow (superposition, complex potential, conformal mapping) → lumped-vortex and panel methods → viscous boundary layers → rotor aerodynamics → environmental impact.
>
> Chapters 1 and 2 are fully lectured and written up with transcript line references (Chapter 2 by Dr Zhiwei Hu). Chapter 3 (Dr Dea Wangsawijaya) was written ahead from the slides and Blackboard notes; 3.1 and 3.2 are fully lectured (22–23 Oct, worked problem 5 Nov), 3.3 (5–6 Nov) and 3.4, transition (Fri 6 Nov), likewise; 3.5, the momentum integral equation, was lectured on Thu 12 Nov (BL6). CH3-6 (viscous–inviscid interaction) is still written ahead and is due on Fri 13 Nov, with a panel-method review and coursework questions in the same two-hour session (BL6, ll. 41–49).
>
> The coursework code (`dpan`, `ktreff`) was posted on 16 October and is tested in [[SESA3043 2.3 - Panel Methods#10. The Blackboard coursework code (dpan and ktreff)|2.3 §10]]. The Python `dpan.py` crashes on NumPy 2 and `ktreff.py` gives a bad point count for some $n$; fixed copies are in `04 - Labs & Coursework/Panel Method Coursework/`.
>
> **Coursework (20 %):** brief filed; due **Thu 3 Dec 2026 at 4 pm** on Blackboard, PDF report of at most 6 A4 pages ([[#Assessment and deadlines]]). Quick reference: [[SESA3043 Formula Sheet]].

## Current coverage

**Chapter 1: Conservation laws**

1. [[SESA3043 1.1 - Mathematical Tools and Flow Description]]
2. [[SESA3043 1.2 - Conservation Laws and Governing Equations]]
3. [[SESA3043 1.2b - Potential-Flow Review]] (Week 1)
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

**Chapter 3: Methods for boundary layers** (written ahead on 6 Oct; 3.1–3.2 lectured 22–23 Oct and 5 Nov; 3.3 on 5–6 Nov; 3.4 on 6 Nov; 3.5 on 12 Nov; 3.6 still written ahead)

9. [[SESA3043 3.1 - Boundary-Layer Concepts and Thickness Measures]] (**lectured Thu 22 Oct**, transcript folded in): $\delta_{99}$, $\delta^*$, $\theta$ (control-volume derivation of $D=\rho U_e^2\theta$), $C_f$, $H$. Also the laminar and turbulent profiles compared, the effective body as the answer to a Chapter 1 question, and slips flagged.
10. [[SESA3043 3.2 - Blasius and Falkner-Skan Similarity Solutions]] (**lectured Thu 22, Fri 23 Oct and Thu 5 Nov**): both derived in full, plus the course's tidy-up route and its series argument for integral B. Integrals A and B; the special cases and what "wedge angle $\beta\pi$" measures; the Falkner–Skan table recomputed; the bump picture (new figure); wedge $\beta=0.3$. The cylinder stagnation-point worked problem (slides 100–106, lectured 5 Nov, flagged as the typical exam question) and the slide 107 summary of governing equations.
11. [[SESA3043 3.3 - Pohlhausen Method and Pressure Gradients]] (**lectured Thu 5 and Fri 6 Nov**, BL3 and BL4): the Pohlhausen solution (a 4th-order polynomial) and $\lambda$; separation at $\lambda=-12$; $\lambda$ through $Re_\delta$ and $\mathrm dp_e/\mathrm dx$ and the four factors that favour separation; laminar vs turbulent separation and the pressure-drag against skin-friction trade on bluff bodies (sphere, golf ball with $Re$ checked, cricket-ball swing); BL4 slips.
12. [[SESA3043 3.4 - Transition to Turbulence]] (**lectured Fri 6 Nov**, BL4 and BL5): Reynolds' pipe experiment; factors and receptivity; the roadmap (TS waves, Λ-vortices, turbulent spots) and bypass; normal modes and the Orr–Sommerfeld equation (given on slide 24, derived in the note as an extension); spatial growth; reading the thumb plot; constant-frequency amplification curves, the envelope and $n_{crit}=9$ (the XFOIL/XFLR5 default); the method's limitations and PSE; pressure-gradient effects; BL4–BL5 slips.
13. [[SESA3043 3.5 - Momentum Integral Equation]] (**lectured Thu 12 Nov**, BL6): the MIE derived in six steps (matches the Blackboard handout equation for equation); one ODE in integral quantities, valid for laminar and turbulent layers; the closure problem (three unknowns; Thwaites named, outside the scope); the ship-fouling drag-penalty chart; the summary table of governing equations.
14. [[SESA3043 3.6 - Viscous-Inviscid Interaction]]: SDM and STM, $v_s=\mathrm d(U_e\delta^*)/\mathrm dx$; XFOIL; wind-tunnel VII example; **coursework** pointer.

**Worked solutions:** [[SESA3043 Ch1 Revision Questions - Worked Solutions]] · [[SESA3043 Ch2 Revision Questions - Worked Solutions]] · [[SESA3043 Ch3 Revision Questions - Worked Solutions]]

**Mock questions:** [[SESA3043 Mock Questions - Chapters 1-3]]: eight self-written, exam-style questions (20 marks each) on everything lectured up to 23 Oct, with full worked solutions checked in Python. They are not lecturer-set.

**Cambridge practice:** [[SESA3043 Cambridge Question Map]] sorts every question in the Cambridge 3A1 example and Tripos papers as in scope, partly in scope or out of scope against this syllabus, with when each becomes doable. Lifting-line and thin-aerofoil questions are listed separately as Year 2 revision.

**Cambridge practice by topic:** [[SESA3043 Cambridge Practice by Topic]] lists the same questions under each topic note, best ones first.

## Week 1 concept map

| Flow description | Conservation and constitutive laws | Reduced models |
|---|---|---|
| [[Eulerian and Lagrangian Flow Descriptions]] | [[Reynolds Transport Theorem]] | [[Incompressible Navier-Stokes Equations]] |
| [[Material Derivative]] | [[Continuity Equation in Conservation Form]] | [[Streamfunction and Velocity Potential]] |
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
| [[Kutta-Joukowski Theorem]] (SESA2022) | | [[Kutta Condition]] · [[Method of Images|Mirror image method]] (SESA2022) |

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
| Chapter 3.1 | Thickness measures, $H$, $C_f$ | **Complete** (lectured Thu 22 Oct, transcript) |
| Chapter 3.2 | Blasius and Falkner–Skan | **Complete** (lectured 22–23 Oct; worked problem Thu 5 Nov; transcripts) |
| Chapter 3.3 | Pohlhausen, pressure gradient, separation | **Complete** (lectured Thu 5 and Fri 6 Nov, transcripts) |
| Chapter 3.4 | Transition to turbulence | **Complete** (lectured Fri 6 Nov, two transcripts) |
| Chapter 3.5 | Momentum integral equation | **Lectured Thu 12 Nov** (BL6), slides 3–45 |
| Chapter 3.6 | Viscous–inviscid interaction | **Written ahead from slides** (6 Oct). Due Fri 13 Nov, after a panel-method review (BL6, ll. 33–49) |
| Later chapters | Rotor aerodynamics, environmental impact (Chapters 4–5) | Awaiting material; Chapters 4 and 5 start in the week of 16 Nov (BL6, ll. 23–25) |
| Revision | Tutorials, exam and practice questions | The last one or two weeks before the Christmas break, with tutorial solutions released afterwards (BL6, ll. 25–29) |

> [!info] Animated source decks
> The supplied PDFs contain a separate page for many PowerPoint animation states. Pages whose content is entirely contained in the next page were skipped automatically (CH1-3: 35 of 59 distinct; CH1-4: 19 of 41; panel explainer: 32 of 42; Ch2 deck: no builds).

## Assessment and deadlines

Assessment split (Week 1):

- **80%** two-hour closed-book final exam;
- **20%** coursework, released on Blackboard **Mon 9 Nov at 9 am** and due **Thu 3 Dec 2026 at 4 pm** through the link under the Blackboard Assessment tab, as a PDF report of at most six A4 pages (brief, p. 1; BL6, ll. 1–21; BL3, ll. 3–7 said the beginning of December; the Week 1 plan said Week 8 to the end of Week 11). Half is the inviscid panel method and half is viscous–inviscid interaction (BL6, ll. 29–35). Two codes are provided on Blackboard, the aerofoil generator and the panel-method code, in MATLAB and Python; any language may be used (BL6, ll. 6–18). Each student has a different aerofoil, and anyone without one should email Dr Hu (BL6, ll. 10–12). Ch2 slide 20: *"Part of the CW will be: generate KT aerofoil with given code and perform potential flow calculations"*; the KT generation is the first part (8 Oct, ll. 424–426; 9 Oct, l. 456). The code (MATLAB and Python) is on Blackboard under Chapter 2; use angles in radians. The coursework comes **after the viscous chapter**, with a dedicated session (2.3 PM2, ll. 612–623). **Python users:** the Blackboard `dpan.py` fails on NumPy 2, and `ktreff.py` can return a duplicate point, so use the fixed copies or the MATLAB files ([[SESA3043 2.3 - Panel Methods#10. The Blackboard coursework code (dpan and ktreff)|2.3 §10]]). Prepare with [[SESA3043 2.1 - Complex Functions and Conformal Mapping#5. The Kármán–Trefftz aerofoil (slides 19–20)|2.1 §5]] and [[SESA3043 2.3 - Panel Methods|2.3]];
- marks reward a complete method and clearly stated assumptions, not only the final number.

> [!important] Coursework brief: *Advanced Aeronautics Coursework* (Hu and Wangsawijaya, Oct 2026)
> File: `04 - Labs & Coursework/Panel Method Coursework/AdvAeronautics 2026-27 Coursework.pdf` (6 pages; pp. 2–5 are the class list of parameters, p. 6 the links to the NACA generator, XFOIL and XFLR5). Submit through Blackboard by **Thu 3 Dec 2026**: a report of **at most 6 A4 pages** opening with a 100–150-word executive summary for non-technical readers, then the technical analysis.
>
> **My KT aerofoil (Table 1):** $\varepsilon=0.07$, $\beta=0.06$, $\tau=0.2$ (radians; $p=2-\tau/\pi=1.936$).
>
> | Q | Task | Weight | Theory in the vault |
> |---|---|---:|---|
> | 1(a) | generate the KT aerofoil with the Blackboard code; find its maximum camber, its position and the maximum thickness (measured normal to the camber line), and the closest NACA 4-digit aerofoil; plot both | 10 % | [[SESA3043 2.1 - Complex Functions and Conformal Mapping#5. The Kármán–Trefftz aerofoil (slides 19–20)\|2.1 §5]], [[SESA3043 2.3 - Panel Methods#10. The Blackboard coursework code (dpan and ktreff)\|2.3 §10]] |
> | 1(b) | vary $\varepsilon$, then $\beta$ (e.g. 0–0.1), others fixed; how maximum thickness and camber change | 10 % | 2.1 §5 |
> | 2(a) | `dpan` at $\alpha=3^\circ$ with different panel numbers; order of accuracy from $C_L$ against the conformal-mapping value | 10 % | [[SESA3043 2.3 - Panel Methods#7. Validation against exact solutions\|2.3 §7]] and the §10 convergence table |
> | 2(b) | change the panel distribution (the $\theta$ distribution on the circle) and number; effect on accuracy | 10 % | 2.3 §10 (the commented alternatives in `ktreff`) |
> | 3 | XFOIL (or XFLR5), both aerofoils, $Re=10^5$ and $5\times10^6$, $\alpha$ from $-5^\circ$ to post-stall; BL thicknesses, shape factor, skin friction, separation, transition; effect of $Re$ | 40 % | [[SESA3043 3.1 - Boundary-Layer Concepts and Thickness Measures\|3.1]]–[[SESA3043 3.6 - Viscous-Inviscid Interaction\|3.6]] |
> | 4 | KT aerofoil at $Re=10^5$ with $n_{crit}=7$ and 5 (roughness, e.g. icing) against $n_{crit}=9$: transition and separation locations, lift and drag | 20 % | [[SESA3043 3.4 - Transition to Turbulence\|3.4]] ($e^n$ method), 3.6 |
>
> The *Coursework Code Explainer* is filed as `02 - Sources/Lectures/Ch2_Notes_CW Code Explainer.pdf`, with `MYKT.dat` (an 81-point KT aerofoil in XFOIL coordinate format, not my Table 1 aerofoil); its equations and three printed slips are in [[SESA3043 2.3 - Panel Methods#10. The Blackboard coursework code (dpan and ktreff)|2.3 §10]].

**Coursework tools** (CH3-6 slide 25): the *Coursework Code Explainer* (filed); use **XFOIL** or XFLR5. The theory is [[SESA3043 3.6 - Viscous-Inviscid Interaction|3.6]].

**Tutorial format** (L5, ll. 507–510): the second Friday lecture at the end of each chapter (five chapters) is a tutorial; work through the revision questions while the chapter is being taught and bring the ones you cannot do. For Chapter 2 the tutorial is **pushed back**, to allow time on the revision questions. Their solutions are withheld until then (9 Oct LVM lecture, ll. 436–444).

**Chapter 3 (BL2, 23 Oct):** no lectures in reading week (ll. 359–361). The **worked-problem session** for Blasius and Falkner–Skan was BL3 (Thu 5 Nov), which called reading $\eta_{99}$ from the Falkner–Skan table and doing the arithmetic a **typical exam problem** (BL3, ll. 149–152). The **mid-module survey** was at the BL2 break (ll. 355–357) and again at the start of BL3 (ll. 1–3).

**Other dates:** study-abroad information session **28 Oct, 10:00–12:30, Building 7 room 309** (L5, ll. 24–25; international placement year and summer schools).

From the 1 Oct lecture (L4, ll. 6–16): Friday 2 Oct second half is a **tutorial**; email or post on the discussion board which **Chapter 1 revision questions** you want covered. Equation booklets were handed out (one each).

Check Blackboard for authoritative dates and later changes.

## Exam skills

**Week 1**

- translate between vector, tensor/index and component notation;
- distinguish Eulerian and Lagrangian descriptions and connect them with the material derivative;
- derive local conservation equations from a control-volume statement;
- convert the conservation form to the non-conservation form;
- identify every force and flux in the momentum and energy equations;
- state the assumptions that reduce the compressible equations to incompressible Navier–Stokes, Euler, potential flow and Bernoulli;
- interpret $\phi$ and $\psi$, including why $\Delta\psi$ equals the volumetric flow rate per unit span.

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
- in ground effect, take only the image's velocity component **normal to the plate** (15 Oct, ll. 97–116); with camber, resolve the free stream normal to **each segment**, and use small-angle approximations so the equations stay solvable (16 Oct first lecture, `14_54_40`, ll. 77–84);
- derive the source, vortex and doublet panel influence formulae and their self-induced limits;
- describe both complete panel methods, their Kutta conditions, and how to get $C_L$ and $C_p$. The exam asks for the **process and logic**, not panel-by-panel calculation (16 Oct, ll. 376–394).

**Chapter 3**

- define $\delta_{99}$, $\delta^*$, $\theta$, $H$, $C_f$ with their mathematical **and** physical meanings, and derive $D=\rho U_e^2\theta$ and $\mathrm d\theta/\mathrm dx=C_f/2$ by control volume. A memory aid: $\delta^*$ → effective body, $\theta$ → drag (BL1, ll. 230–233). $\mathrm d\theta/\mathrm dx=C_f/2$ holds for a flat plate only (ll. 285–289);
- explain from normalised profiles why a turbulent layer is fuller and has more friction drag (BL1, ll. 82–88);
- evaluate them for an assumed profile (linear, Pohlhausen);
- derive the Blasius and Falkner–Skan equations from the stream-function BL equation; explain similarity and the guess-and-shooting method. Understand the route rather than memorising it (BL2, ll. 210–211): two PDEs → $\psi$ → one PDE → similarity variables → one nonlinear ODE;
- get $\delta^*$, $\theta$, $C_f$, $H$ from $\eta^*$, $\theta^*$, $f''(0)$, including $\theta^*=f''(0)$ by parts, with $f(1-f')\to0$ by the series argument; use the Falkner–Skan table for a wedge or a stagnation point (the cylinder $\delta_{99}$ problem is the typical exam question, BL3, ll. 149–152);
- say where $\delta_{99}/x=5.0/\sqrt{Re_x}$, $\delta^*/x=1.721/\sqrt{Re_x}$, $\theta/x=C_f=0.664/\sqrt{Re_x}$ come from, and their limits: laminar, zero pressure gradient (BL2, ll. 319–326);
- explain the sign of $\beta$ along a bump up to separation, and the effective body for a wedge (revision 3.2 Q4; BL2, ll. 636–673);
- derive the Pohlhausen profile and $\lambda$, and read it as flat plate plus a $\lambda$-weighted pressure-gradient term; derive separation at $\lambda=-12$ (set at BL3, ll. 343–345, and again at BL4, ll. 103–107); say what $H$ tells you about the pressure gradient; write $\lambda=-Re_\delta\frac{\delta}{\rho U_e^2}\frac{\mathrm dp_e}{\mathrm dx}$ and read off the factors that promote separation (BL4, ll. 255–290); explain why turbulence delays separation and lowers a bluff body's drag although skin friction rises (BL4, ll. 316–401);
- describe natural and bypass transition and receptivity; explain where the Orr–Sommerfeld equation comes from (decomposition, normal modes, linearisation, eigenvalue problem; the full derivation is further reading, BL4, ll. 1943–1962); read $\hat v e^{i(\alpha_rx-\omega t)}e^{-\alpha_ix}$ as shape, wave and growth; read a thumb plot along constant $F$ and constant $Re$, and keep $Re_{crit}$ apart from transition; apply the $e^n$ method with the envelope and $n_{crit}=9$; state its limitations (BL5);
- follow (SESA6087: reproduce) the MIE derivation (BL6, ll. 75–78); reduce it for a flat plate; say why it holds for laminar and turbulent layers and why it needs a closure (BL6, ll. 313–341);
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
- **Year 3 bridges (note level):** Reynolds transport theorem ([[SESA3043 1.1 - Mathematical Tools and Flow Description|1.1]]) against the *vector* transport theorem of [[SESA3047 2.1 - Vector Operations and the Transport Theorem|SESA3047 2.1]] (same name, different theorems) · conservation laws ([[SESA3043 1.2 - Conservation Laws and Governing Equations|1.2]]) in integral form across shocks ([[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes|SESA3029 W01]]) · wedge flow $U_e\propto s^m$ ([[SESA3043 1.3 - Complex Potential, Wedge Flows and Unsteady Bernoulli|1.3]]) feeding the Falkner–Skan edge velocity ([[SESA3043 3.2 - Blasius and Falkner-Skan Similarity Solutions|3.2]]) · Cauchy–Riemann ([[SESA3043 2.1 - Complex Functions and Conformal Mapping|2.1]]) against characteristics ([[SESA3029 W05a - Method of Characteristics|SESA3029 W05a]]) · LVM lift ([[SESA3043 2.2 - Lumped Vortex Method|2.2]]) against shock-expansion lift ([[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method|SESA3029 W03]]) and as the force input to [[SESA3047 4.2 - Translational Dynamics|SESA3047 4.2]].

## Sources

- `02 - Sources/SESA3043 Syllabus 2026-27.pdf` (official topic list, Chapters 1–5)
- `02 - Sources/Lectures/CH1-2 Governing Equations(1).pdf`
- `02 - Sources/Lectures/CH1-3 Potential Flow.pdf`
- `02 - Sources/Lectures/CH1-4 2D Incompressible BL(1).pdf`
- `02 - Sources/Lectures/Ch1_Notes_Unsteady Bernoulli Eqn.pdf`
- `02 - Sources/Lectures/Ch2 Exact Solution and methods for potential flow.pdf`
- `02 - Sources/Lectures/Ch2_Notes_LVM_Tandem Aerofoils.pdf`, `Ch2_Notes_LVM_Ground Effect.pdf`, `Ch2_Notes_LVM_Cambered Aerofoil.pdf`
- `02 - Sources/Lectures/Ch2_Notes_Panel Method.pdf`, `Ch2_Panel_Method_Explainer.pdf`
- Transcripts: `L1 - SESA3043.txt`, `L2 - SESA3043.txt`, `L3 - SESA3043.txt` (Week 1); `L4 - SESA3043.txt`; `02 October 2026 at 14_53_48.txt` (**L5**, CH1-4) and `02 October 2026 at 15_51_44.txt` (Ch1 tutorial); `08 October 2026 at 13_50_19.txt` (Ch2 L1, conformal mapping), `09 October 2026 at 14_57_18.txt` (Ch2 L2, Joukowski and KT), `09 October 2026 at 16_00_58.txt` (Ch2 L3, lumped vortex) and `09 October 2026 at 14_17_51.txt` (Joukowski demo recording); `15 October 2026 at 13_48_35.txt` (ground effect, camber); `16 October 2026 at 14_54_40.txt` and `16 October 2026 at 15_53_48.txt` (camber finished; panel method); `22 October 2026 at 13_51_55.txt` (**BL1**, CH3-1 and the start of CH3-2) and `23 October 2026 at 14_53_16.txt` (**BL2**, CH3-2 to slide 99); `05 November 2026 at 13_59_07.txt` (**BL3**, CH3-2 recap and worked problem, CH3-3 slides 1–26); `06 November 2026 at 14_52_55.txt` (**BL4**, Pohlhausen recap, CH3-3 slides 28–38, CH3-4 to the Orr–Sommerfeld equation) and `06 November 2026 at 15_54_41.txt` (**BL5**, CH3-4 thumb plot, $e^n$ method, pressure gradients); `12 November 2026 at 13_50_20.txt` (**BL6**, coursework and schedule, CH3-5 slides 3–45)
- Coursework code: `02 - Sources/Lectures/dpan.m`, `dpan.py`, `ktreff.m`, `ktreff.py` (posted 16 Oct); `Ch2_Notes_CW Code Explainer.pdf` and `MYKT.dat` (filed 11 Nov)
- Coursework brief: `04 - Labs & Coursework/Panel Method Coursework/AdvAeronautics 2026-27 Coursework.pdf` (filed 11 Nov)
- `02 - Sources/Lectures/CH3-1 Introduction(1).pdf`, `CH3-2 Blasius and Falkner-Skan(1).pdf`, `CH3-3 Pohlhausen.pdf`, `CH3-4 Transition to Turbulence(1).pdf`, `CH3-5 Momentum Integral Eqn(1).pdf`, `CH3-6 Viscous Inviscid Interaction.pdf`
- `02 - Sources/Lectures/Ch3_Notes_Blasius.pdf`, `Ch3_Notes_Falkner-Skan.pdf`, `Ch3_Notes_Pohlhausen.pdf`, `Ch3_Notes_Momentum Integral Eq.pdf` (filed 19 Oct)
- `03 - Exams & Past Papers/Ch3_Revision_Questions.pdf`
- `03 - Exams & Past Papers/Ch1_Revision_Questions.pdf`, `Ch2_Revision_Questions.pdf`

## Transcript and slide slips

> [!warning] Slips found in the sources (all flagged in the notes)
> CH1-3 slide 25: $\phi$ bracket should be $1+R^2/r^2$. Slides 21/37: vortex row mixes sign conventions. Unsteady-Bernoulli notes Eq. 1: missing $\times\mathbf u$. CH1-4 slide 37: "matching" means marching. Ch2 slide 5: $\varphi$ for $\psi$. Slide 10: missing signs in the circle map. Slide 17: circle centre shift dropped. Slide 28: control point is $x_T$, not $x_L$. LVM camber notes: $\Gamma_2$ distance at $T_2$ is $c/4$, not $3c/4$. Slide 47: $\sigma$ for $\mu$. Slide 51 and explainer p. 25: vortex $w$ sign and the rotation formula. Ch3 notes: Falkner–Skan boxed Eq. 8 has $f'f''$ for $ff''$; Pohlhausen p. 2 bracket has $+\eta^3$ for $-\eta^3$; Blasius $\eta_{99}$ read as 3.5 (exact 3.47, so $\delta_{99}/x=4.91$, not 5.0, $/\sqrt{Re_x}$). L5 (2 Oct): "matching" for marching again, and several spoken slips, flagged in [[SESA3043 1.4 - Two-Dimensional Incompressible Boundary Layers#Transcript slips (L5)|1.4]]. Ch2 lectures (8–9 Oct): $\mathrm d\Phi/\mathrm dx$ for $\mathrm d\Phi/\mathrm dz$, "$-2\pi$ to $2\pi$" for $\pm2a$, the dropped square root in $\sqrt{4a^2-y^2}$, the parallel component said as $U_\infty\sin\alpha$, and $L=U_\infty\Gamma$ without $\rho$. Flagged in [[SESA3043 2.1 - Complex Functions and Conformal Mapping#Transcript slips (L-a and L-b)|2.1]] and [[SESA3043 2.2 - Lumped Vortex Method#Transcript slips (LV)|2.2]]. 15–16 Oct: ground-effect $\Gamma/\Gamma_\infty$ said as $1+1/(4\bar h^2)$ (correct $1+1/(4\bar h)^2$); camber slope $-0.08$ for $-0.18$; panels numbered "anti-clockwise" against the code's clockwise. Flagged in [[SESA3043 2.2 - Lumped Vortex Method#Transcript slips (GE, PM1)|2.2]] and [[SESA3043 2.3 - Panel Methods#Transcript slips (PM1, PM2)|2.3]]. 22–23 Oct (Ch3):
> - the mass balance said with $\rho U_e^2$ for $\rho u$;
> - $D$ said as $\rho U_e^2$ "plus" the integral (a product);
> - the Falkner–Skan free-stream condition said as $f'(\infty)=0$ (correct: 1);
> - "$m=\beta=1$" said for the flat plate (correct: 0);
> - "wedge angle $\beta\pi$" applied to a single wall, which turns by $\beta\pi/2$;
> - the slide 68 heading reads "Displacement" for momentum thickness (the lecturer caught it).
>
> Flagged in [[SESA3043 3.1 - Boundary-Layer Concepts and Thickness Measures#Transcript slips (BL1)|3.1]] and [[SESA3043 3.2 - Blasius and Falkner-Skan Similarity Solutions#Transcript slips (BL1, BL2, BL3)|3.2]].
>
> 5 Nov (BL3): $U_e=U_\infty\sin\theta$ for the cylinder (corrected at once to $2U_\infty\sin\theta$); $\mathrm dp/\mathrm dx=0$ said for $\partial p/\partial y=0$; "$\mathrm dU_e/\mathrm dx>0$ means $\mathrm dp/\mathrm dx$ is zero" (it is negative); $\lambda=-a_2$ (correct: $-2a_2$); the fourth edge condition with $6a_3$ said twice. Flagged in [[SESA3043 3.2 - Blasius and Falkner-Skan Similarity Solutions#Transcript slips (BL1, BL2, BL3)|3.2]] and [[SESA3043 3.3 - Pohlhausen Method and Pressure Gradients#Transcript slips (BL3)|3.3]].
>
> 6 Nov (BL4, BL5): flat-plate $H$ said as "almost 2.6" (Pohlhausen 2.55); the sandpaper incident placed "in Australia" (Cape Town, 2018); "the critical Reynolds number equals 9" (it is $n_{crit}=9$), and the envelope crossing called the critical Reynolds number (it is the transition Reynolds number; slide 43 has the same label). Flagged in [[SESA3043 3.3 - Pohlhausen Method and Pressure Gradients#Transcript slips (BL4, ll. 1–630)|3.3]] and [[SESA3043 3.4 - Transition to Turbulence#Transcript slips (BL4 from l. 634, and BL5)|3.4]].
>
> 12 Nov (BL6): the shape factor $H$ said as "shear factor"; the ship chart's ordinate called $C_f$ (slide 44 plots the mean $\overline{C_f}$); the fouling height given as "0.3 millimeter" ($k_s=0.325$ mm); "FLCC" for VLCC. Flagged in [[SESA3043 3.5 - Momentum Integral Equation#Transcript and slide slips|3.5]].
