---
title: "SESA3043 Advanced Aeronautics Hub"
module: "SESA3043 Advanced Aeronautics"
type: hub
aliases: ["SESA3043 Advanced Aeronautics"]
tags: [sesa3043, hub, moc]
status: in-progress
coverage: "Chapters 1–3, all lectured (Ch3 22 Oct–13 Nov, ending with CH3-6 viscous–inviscid interaction and the coursework briefing on Fri 13 Nov); Chapter 4 (rotor aerodynamics) started Thu 19 Nov: 4.1 hover fully lectured (RL1 Thu 19 Nov, slides 1–22; RL2 Fri 20 Nov, slides 23–40); 4.2 axial flight lectured to slide 52 (RL2: climb, and descent to the existence of real roots), the rest of 4.2 and all of 4.3 written ahead from the slides on 17 Nov, awaiting lectures"
---

# SESA3043 Advanced Aeronautics Hub

> [!abstract] Module at a glance
> Conservation laws and governing equations → potential flow (superposition, complex potential, conformal mapping) → lumped-vortex and panel methods → viscous boundary layers → rotor aerodynamics → environmental impact.
>
> Chapters 1 and 2 are fully lectured and written up with transcript line references (Chapter 2 by Dr Zhiwei Hu). Chapter 3 (Dr Dea Wangsawijaya) was written ahead from the slides and Blackboard notes; 3.1 and 3.2 are fully lectured (22–23 Oct, worked problem 5 Nov), 3.3 (5–6 Nov) and 3.4, transition (Fri 6 Nov), likewise; 3.5, the momentum integral equation, was lectured on Thu 12 Nov, and 3.6, viscous–inviscid interaction, on Fri 13 Nov after a panel-method refresher, which completes Chapter 3. BL7 ended with the coursework briefing; a new chapter starts in the week of 16 Nov. Chapter 4, rotor aerodynamics (Dr Hu, about two weeks from Thu 19 Nov), is written ahead from the CH4 slides (filed 17 Nov) in [[SESA3043 4.1 - Rotor in Hover|4.1]] (hover), [[SESA3043 4.2 - Rotor in Axial Flight|4.2]] (axial flight) and [[SESA3043 4.3 - Rotor in Forward Flight|4.3]] (forward flight). RL1 (Thu 19 Nov) covered slides 1–22, from the introduction through actuator disc theory and annular wake division to the induced power factor; RL2 (Fri 20 Nov) finished hover (ground effect, blade element theory, figure of merit, with twist and annulus theory for awareness) and took axial flight through climb and into descent as far as the descent quadratic and its real roots for $V_D\geq2v_0$. 4.1 is now `lectured`; 4.2 stays `written-ahead` until the descent states are lectured, and 4.3 awaits its lectures (forward flight the week of 23 Nov). Chapter 5 (environmental impact) has no material yet.
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
   - Deep dive: [[SESA3043 Deep Dive - Joukowski and Kármán-Trefftz Aerofoils, Full Derivation]]: circle theorem, both maps and their trailing edges, $\Gamma$ from the Kutta condition, exact $C_p$ and $C_L$, and the exact $C_L=0.776$ reference for the coursework aerofoil at $\alpha=3^\circ$ (Q2(a)).
7. [[SESA3043 2.2 - Lumped Vortex Method]] (**lectured 9, 15 and 16 Oct**): flat plate, tandem (with an unequal-chord challenge solved), ground effect, camber, biplane; the exam's small-angle traps.
8. [[SESA3043 2.3 - Panel Methods]] (**lectured 16 Oct**): source/vortex/doublet panels, both complete methods, what is examinable (process, not arithmetic), the Blackboard code tested and fixed, validation.

**Chapter 3: Methods for boundary layers** (written ahead on 6 Oct; 3.1–3.2 lectured 22–23 Oct and 5 Nov; 3.3 on 5–6 Nov; 3.4 on 6 Nov; 3.5 on 12 Nov; 3.6 on 13 Nov)

9. [[SESA3043 3.1 - Boundary-Layer Concepts and Thickness Measures]] (**lectured Thu 22 Oct**, transcript folded in): $\delta_{99}$, $\delta^*$, $\theta$ (control-volume derivation of $D=\rho U_e^2\theta$), $C_f$, $H$. Also the laminar and turbulent profiles compared, the effective body as the answer to a Chapter 1 question, and slips flagged.
10. [[SESA3043 3.2 - Blasius and Falkner-Skan Similarity Solutions]] (**lectured Thu 22, Fri 23 Oct and Thu 5 Nov**): both derived in full, plus the course's tidy-up route and its series argument for integral B. Integrals A and B; the special cases and what "wedge angle $\beta\pi$" measures; the Falkner–Skan table recomputed; the bump picture (new figure); wedge $\beta=0.3$. The cylinder stagnation-point worked problem (slides 100–106, lectured 5 Nov, flagged as the typical exam question) and the slide 107 summary of governing equations.
    - Deep dive: [[SESA3043 Deep Dive - Falkner-Skan Similarity, Full Derivation]]: every step from the BL equations with $U_e=cx^m$, why only a power law is similar, the wedge link, $f'''(0)=-\beta$, the similarity-form MIE $f''(0)=(1+\beta)\theta^*+\beta\eta^*$, and the slide 96 table reproduced by shooting.
11. [[SESA3043 3.3 - Pohlhausen Method and Pressure Gradients]] (**lectured Thu 5 and Fri 6 Nov**, BL3 and BL4): the Pohlhausen solution (a 4th-order polynomial) and $\lambda$; separation at $\lambda=-12$; $\lambda$ through $Re_\delta$ and $\mathrm dp_e/\mathrm dx$ and the four factors that favour separation; laminar vs turbulent separation and the pressure-drag against skin-friction trade on bluff bodies (sphere, golf ball with $Re$ checked, cricket-ball swing); BL4 slips.
12. [[SESA3043 3.4 - Transition to Turbulence]] (**lectured Fri 6 Nov**, BL4 and BL5): Reynolds' pipe experiment; factors and receptivity; the roadmap (TS waves, Λ-vortices, turbulent spots) and bypass; normal modes and the Orr–Sommerfeld equation (given on slide 24, derived in the note as an extension); spatial growth; reading the thumb plot; constant-frequency amplification curves, the envelope and $n_{crit}=9$ (the XFOIL/XFLR5 default); the method's limitations and PSE; pressure-gradient effects; BL4–BL5 slips.
    - Deep dive: [[SESA3043 Deep Dive - Linear Stability and the Orr-Sommerfeld Equation]]: decomposition, linearisation, normal modes and the Orr–Sommerfeld derivation line by line; the Blasius neutral curve computed ($Re_{\delta^*,crit}=519$) and the $e^n$ envelope for $n_{crit}=9$, 7 and 5.
13. [[SESA3043 3.5 - Momentum Integral Equation]] (**lectured Thu 12 Nov**, BL6): the MIE derived in six steps (matches the Blackboard handout equation for equation); one ODE in integral quantities, valid for laminar and turbulent layers; the closure problem (three unknowns; Thwaites named, outside the scope); the ship-fouling drag-penalty chart; the summary table of governing equations.
    - Deep dive (with 3.3): [[SESA3043 Deep Dive - Momentum Integral Equation and Pohlhausen Method]]: the MIE derived in full, the Pohlhausen quartic and its integrals as functions of $\lambda$, the coupled Kármán–Pohlhausen march, and separation predicted for Howarth's retarded flow and the cylinder against Thwaites and exact values.
14. [[SESA3043 3.6 - Viscous-Inviscid Interaction]] (**lectured Fri 13 Nov**, BL7): SDM and STM, $v_s=\mathrm d(U_e\delta^*)/\mathrm dx$; XFOIL's closures (compressible MIE with Thwaites, Falkner–Skan laminar closure, $e^n$ transition); why VII fails at separation and stall; wind-tunnel VII example; the coursework methods (camber-normal thickness, order of accuracy from a log–log fit, new figure); BL7 slips. The first hour of BL7, a panel-method refresher, is folded into [[SESA3043 2.3 - Panel Methods|2.3]].

**Chapter 4: Rotor aerodynamics** (written ahead from the CH4 slides on 17 Nov; lectured from Thu 19 Nov, hover complete Fri 20 Nov)

15. [[SESA3043 4.1 - Rotor in Hover]] (**lectured** Thu 19 Nov, RL1, slides 1–22, and Fri 20 Nov, RL2, slides 23–40): actuator disc theory from Bernoulli, mass and momentum ($v_2=2v_i$, $v_0=\sqrt{T/2\rho A}$, $P_i=Tv_0$, wake contraction to $A/2$, energy check); disc loading across vehicles; $\lambda_i$, $C_T$ and $C_{P_i}$ in the course's convention with $\tfrac12$; the Westland Lynx example; annular wake division and $k_i=(n+1)^{3/2}/(1+3n/2)\geq1$; ground effect, wake recirculation and brownout; blade element theory (thrust, torque, induced and profile power), $C_T/sa$, $C_P$ and the figure of merit; linear twist and the three-quarter-radius result; annulus theory and ideal twist; a blade-element estimate for the Lynx with assumed blade data; RL1 and RL2 slips.
16. [[SESA3043 4.2 - Rotor in Axial Flight]] (**partly lectured** Fri 20 Nov, RL2, slides 41–52: climb in full, descent to the real-root condition; slides 52–68 written ahead): climb and descent actuator disc theory, both quadratics and their physical roots, the gap $0<V_D<2v_0$ where momentum theory has no solution, the working states (normal working, vortex ring, turbulent wake, windmill brake), axial power, autorotation ($\bar V_D\approx1.7$–$1.8$ and $2/\sqrt{C_D}$); Lynx climb, descent and autorotation examples.
17. [[SESA3043 4.3 - Rotor in Forward Flight]] (**written ahead**, CH4 slides 69–90): co-ordinate system and disc tilt, advancing and retreating blades and the reverse-flow circle, the forward-flight induced velocity with mass flow $\rho AV'$ and its hover, axial and high-speed limits, Newton–Raphson, the level-flight force balance, induced, parasite and profile power and the power bucket; the Lynx at 60 m/s with an assumed drag area.

**Worked solutions:** [[SESA3043 Ch1 Revision Questions - Worked Solutions]] · [[SESA3043 Ch2 Revision Questions - Worked Solutions]] · [[SESA3043 Ch3 Revision Questions - Worked Solutions]]

**Mock questions:** [[SESA3043 Mock Questions - Chapters 1-3]]: eight self-written, exam-style questions (20 marks each) on everything lectured up to 23 Oct, with full worked solutions checked in Python. They are not lecturer-set.

**Cambridge practice:** [[SESA3043 Cambridge Question Map]] sorts every question in the Cambridge 3A1 example and Tripos papers as in scope, partly in scope or out of scope against this syllabus, with when each becomes doable. Lifting-line and thin-aerofoil questions are listed separately as Year 2 revision.

**Cambridge practice by topic:** [[SESA3043 Cambridge Practice by Topic]] lists the same questions under each topic note, best ones first.

**Cambridge worked solutions:** [[SESA3043 Cambridge Solutions - 1.2b-1.4 Potential Flow, Vortices and Boundary-Layer Equations|1.2b-1.4 Potential Flow, Vortices and Boundary-Layer Equations]] · [[SESA3043 Cambridge Solutions - 1.3 and 2.1 Complex Potential and Conformal Mapping|1.3 and 2.1 Complex Potential and Conformal Mapping]] · [[SESA3043 Cambridge Solutions - 2.2-3.1 Lumped Vortex, Panels and Thickness Measures|2.2-3.1 Lumped Vortex, Panels and Thickness Measures]] · [[SESA3043 Cambridge Solutions - 3.2-3.3 Similarity Solutions and Pohlhausen|3.2-3.3 Similarity Solutions and Pohlhausen]] · [[SESA3043 Cambridge Solutions - 3.5 Momentum Integral and Thwaites|3.5 Momentum Integral and Thwaites]] · [[SESA3043 Cambridge Solutions - Potential Flows from the Incompressible Example Paper|Potential Flows from the Incompressible Example Paper]] · [[SESA3043 Cambridge Solutions - Images, Tunnel Walls and 3D Sources|Images, Tunnel Walls and 3D Sources]] · [[SESA3043 Cambridge Solutions - Sheared Inflow, Exact Viscous Solutions and Diffusing Vortices|Sheared Inflow, Exact Viscous Solutions and Diffusing Vortices]] · [[SESA3043 Cambridge Solutions - Jets, Wakes, Stokes Problems and Channel Flows|Jets, Wakes, Stokes Problems and Channel Flows]] · [[SESA3043 Cambridge Solutions - Vortex Pairs, Waves and Unsteady Potential Flow|Vortex Pairs, Waves and Unsteady Potential Flow]] · [[SESA3043 Cambridge Solutions - Moving Bodies, Bubbles and Deep-Water Waves|Moving Bodies, Bubbles and Deep-Water Waves]] · [[SESA3043 Cambridge Solutions - Vorticity Dynamics, Kelvin's Theorem and Secondary Flow|Vorticity Dynamics, Kelvin's Theorem and Secondary Flow]] · [[SESA3043 Cambridge Solutions - Turbulent Profiles, Transition and Integral Boundary Layers|Turbulent Profiles, Transition and Integral Boundary Layers]] · [[SESA3043 Cambridge Solutions - Boundary-Layer State, Heat-Transfer Analogy and Separation|Boundary-Layer State, Heat-Transfer Analogy and Separation]] · [[SESA3043 Cambridge Solutions - Bluff-Body Drag, Diffusers and Road Vehicles|Bluff-Body Drag, Diffusers and Road Vehicles]] · [[SESA3043 Cambridge Solutions - Lumped Models, Ground Effect and Wing Stall|Lumped Models, Ground Effect and Wing Stall]]. Together these solve all 170 in-scope and partly-in-scope 3A1 questions in the map; off-syllabus parts are solved and flagged. No 3A1 question covers Chapter 4 (rotors).

**Southampton past paper:** [[SESA3043-202425-01-SESA3043SESA6087.pdf|SESA3043-202425-01-SESA3043SESA6087]]

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

## Chapter 4 concept map

Written ahead from the slides. The hover rows (4.1) were lectured on Thu 19 and Fri 20 Nov, and 4.2 as far as the descent quadratic on Fri 20 Nov; the rest await lectures.

| Builds on | New concept |
|---|---|
| [[Actuator Disk Theory]] (SESA2023) · [[Bernoulli Equation]] | [[Hover Induced Velocity and Disc Loading]] · [[Rotor Thrust and Power Coefficients]] |
| [[Hover Induced Velocity and Disc Loading]] | [[Induced Power Factor]] |
| [[Method of Images]] (SESA2022) · [[SESA3043 2.2 - Lumped Vortex Method\|2.2]] | [[Rotor Ground Effect]] |
| aerofoil lift slope and drag (SESA2022) | [[Blade Element Theory]] · [[Figure of Merit]] · [[Blade Twist and Annulus Theory]] |
| [[Hover Induced Velocity and Disc Loading]] · [[Momentum Flux]] | [[Induced Velocity in Axial Flight]] |
| [[Induced Velocity in Axial Flight]] | [[Rotor Working States in Axial Flight]] · [[Vortex Ring State]] · [[Windmill Brake State]] · [[Autorotation]] |
| [[Downwash and Induced Drag]] (SESA2022) · [[Direct Substitution and Newton-Raphson]] (SESA2029) | [[Disc Tilt]] · [[Induced Velocity in Forward Flight]] |
| [[Blade Element Theory]] · [[Minimum Drag and Minimum Power]] (SESA1015) | [[Rotor Power Consumption]] |

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
| Chapter 3.6 | Viscous–inviscid interaction | **Complete** (lectured Fri 13 Nov, BL7, after a panel-method refresher; coursework briefing) |
| Chapter 4.1 | Rotor in hover: actuator disc, annular wake, ground effect, blade element theory, figure of merit, twist | **Complete** (lectured Thu 19 Nov, RL1, slides 1–22, and Fri 20 Nov, RL2, slides 23–40; twist and annulus theory for awareness) |
| Chapter 4.2 | Rotor in axial flight | **Partly lectured** Fri 20 Nov (RL2): slides 41–52, climb, and descent to the condition $V_D\geq2v_0$ for real roots; slides 52–68 (physical descent root, working states, autorotation) written ahead, awaiting the next lecture |
| Chapter 4.3 | Rotor in forward flight | **Written ahead** from CH4 slides 69–90 (17 Nov); lectures from the week of 23 Nov |
| Chapter 5 | Environmental impact: introduction, fundamental acoustics, propagation of sound waves (syllabus) | Awaiting material |
| Revision | Tutorials, exam and practice questions | The last one or two weeks before the Christmas break, with tutorial solutions released afterwards |

> [!info] Animated source decks
> The supplied PDFs contain a separate page for many PowerPoint animation states. Pages whose content is entirely contained in the next page were skipped automatically (CH1-3: 35 of 59 distinct; CH1-4: 19 of 41; panel explainer: 32 of 42; Ch2 deck: no builds).

## Assessment and deadlines

Assessment split (Week 1):

- **80%** two-hour closed-book final exam;
- **20%** coursework, released on Blackboard **Mon 9 Nov at 9 am** and due **Thu 3 Dec 2026 at 4 pm** through the link under the Blackboard Assessment tab, as a PDF report of at most six A4 pages (brief, p. 1; earlier estimates were the beginning of December and, in the Week 1 plan, Week 8 to the end of Week 11). Half is the inviscid panel method and half is viscous–inviscid interaction. Two codes are provided on Blackboard, the aerofoil generator and the panel-method code, in MATLAB and Python; any language may be used. Each student has a different aerofoil, and anyone without one should email Dr Hu. Ch2 slide 20: *"Part of the CW will be: generate KT aerofoil with given code and perform potential flow calculations"*; the KT generation is the first part. The code (MATLAB and Python) is on Blackboard under Chapter 2; use angles in radians. The coursework comes **after the viscous chapter**, with a dedicated session. **Python users:** the Blackboard `dpan.py` fails on NumPy 2, and `ktreff.py` can return a duplicate point, so use the fixed copies or the MATLAB files ([[SESA3043 2.3 - Panel Methods#10. The Blackboard coursework code (dpan and ktreff)|2.3 §10]]). Prepare with [[SESA3043 2.1 - Complex Functions and Conformal Mapping#5. The Kármán–Trefftz aerofoil|2.1 §5]] and [[SESA3043 2.3 - Panel Methods|2.3]];
- marks reward a complete method and clearly stated assumptions, not only the final number.

> [!important] Coursework brief: *Advanced Aeronautics Coursework* (Hu and Wangsawijaya, Oct 2026)
> File: `04 - Labs & Coursework/Panel Method Coursework/AdvAeronautics 2026-27 Coursework.pdf` (6 pages; pp. 2–5 are the class list of parameters, p. 6 the links to the NACA generator, XFOIL and XFLR5). Submit through Blackboard by **Thu 3 Dec 2026**: a report of **at most 6 A4 pages** opening with a 100–150-word executive summary for non-technical readers, then the technical analysis.
>
> **My KT aerofoil (Table 1):** $\varepsilon=0.07$, $\beta=0.06$, $\tau=0.2$ (radians; $p=2-\tau/\pi=1.936$).
>
> | Q | Task | Weight | Theory in the vault |
> |---|---|---:|---|
> | 1(a) | generate the KT aerofoil with the Blackboard code; find its maximum camber, its position and the maximum thickness (measured normal to the camber line), and the closest NACA 4-digit aerofoil; plot both | 10 % | [[SESA3043 2.1 - Complex Functions and Conformal Mapping#5. The Kármán–Trefftz aerofoil\|2.1 §5]], [[SESA3043 2.3 - Panel Methods#10. The Blackboard coursework code (dpan and ktreff)\|2.3 §10]] |
> | 1(b) | vary $\varepsilon$, then $\beta$ (e.g. 0–0.1), others fixed; how maximum thickness and camber change | 10 % | 2.1 §5 |
> | 2(a) | `dpan` at $\alpha=3^\circ$ with different panel numbers; order of accuracy from $C_L$ against the conformal-mapping value | 10 % | [[SESA3043 2.3 - Panel Methods#7. Validation against exact solutions\|2.3 §7]] and the §10 convergence table |
> | 2(b) | change the panel distribution (the $\theta$ distribution on the circle) and number; effect on accuracy | 10 % | 2.3 §10 (the commented alternatives in `ktreff`) |
> | 3 | XFOIL (or XFLR5), both aerofoils, $Re=10^5$ and $5\times10^6$, $\alpha$ from $-5^\circ$ to post-stall; BL thicknesses, shape factor, skin friction, separation, transition; effect of $Re$ | 40 % | [[SESA3043 3.1 - Boundary-Layer Concepts and Thickness Measures\|3.1]]–[[SESA3043 3.6 - Viscous-Inviscid Interaction\|3.6]] |
> | 4 | KT aerofoil at $Re=10^5$ with $n_{crit}=7$ and 5 (roughness, e.g. icing) against $n_{crit}=9$: transition and separation locations, lift and drag | 20 % | [[SESA3043 3.4 - Transition to Turbulence\|3.4]] ($e^n$ method), 3.6 |
>
> The *Coursework Code Explainer* is filed as `02 - Sources/Lectures/Ch2_Notes_CW Code Explainer.pdf`, with `MYKT.dat` (an 81-point KT aerofoil in XFOIL coordinate format, not my Table 1 aerofoil); its equations and three printed slips are in [[SESA3043 2.3 - Panel Methods#10. The Blackboard coursework code (dpan and ktreff)|2.3 §10]].

**Coursework tools** (CH3-6 slide 25): the *Coursework Code Explainer* (filed); use **XFOIL** or XFLR5. The theory is [[SESA3043 3.6 - Viscous-Inviscid Interaction|3.6]].

**Coursework briefing** (Fri 13 Nov): submission link under Assessment, *Coursework Instruction and Supporting Materials*, due 3 Dec at 4 pm. Keep the methods and geometry brief within the six pages; export XFOIL/XFLR5 data and plot it in MATLAB or Python rather than pasting screenshots; choose two or three angles of attack to show the boundary-layer trends rather than every result; include an executive summary; no code needs attaching. Measure thickness normal to the camber line and report the error against the closest NACA section; the alternative cosine distribution in `ktreff` does not work for every aerofoil. The order of accuracy is the slope of a log–log fit of the $C_L$ error against $N$, limited to its straight-line range, in double precision. Both methods are worked in [[SESA3043 3.6 - Viscous-Inviscid Interaction#6. Coursework: thickness and order of accuracy|3.6 §6]]. Extensions go through Student Hub.

**Tutorial format**: the second Friday lecture at the end of each chapter (five chapters) is a tutorial; work through the revision questions while the chapter is being taught and bring the ones you cannot do. For Chapter 2 the tutorial is **pushed back**, to allow time on the revision questions. Their solutions are withheld until then.

**Chapter 3 (23 Oct):** no lectures in reading week. The **worked-problem session** for Blasius and Falkner–Skan was BL3 (Thu 5 Nov), which called reading $\eta_{99}$ from the Falkner–Skan table and doing the arithmetic a **typical exam problem**. The **mid-module survey** was at the BL2 break and again at the start of BL3.

**Chapter 4 (19–20 Nov):** the chapter runs for about two weeks: hover took two lectures, axial flight finishes in the next lecture, and forward (edgewise) flight follows the week of 23 Nov. The Lynx hover example is left for self-study; it and the Chapter 4 revision questions are gone through in the Chapter 4 tutorial. The revision questions are not filed in the vault yet. Work the example in [[SESA3043 4.1 - Rotor in Hover#7. Worked example: Westland Lynx in hover|4.1 §7]]. Before the next lecture, work through the axial-flight mathematics and decide which parts of the descent solution are physical ([[SESA3043 4.2 - Rotor in Axial Flight#The roots, when they exist and which is physical|4.2 §4]]).

**Other dates:** study-abroad information session **28 Oct, 10:00–12:30, Building 7 room 309** (international placement year and summer schools).

From the 1 Oct lecture: Friday 2 Oct second half is a **tutorial**; email or post on the discussion board which **Chapter 1 revision questions** you want covered. Equation booklets were handed out (one each).

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
- derive the BL equations by order of magnitude; explain $\partial p/\partial y=0$, $\delta\sim Re^{-1/2}$ and parabolic marching; explain why the BL equations are written with $U_e\,\mathrm dU_e/\mathrm dx$ rather than $\mathrm dp/\mathrm dx$.

**Chapter 2**

- explain why an analytic map preserves angles and carries potential flows;
- **by hand** (stated as examinable, 9 Oct): flow onto a finite plate and flow along a plate by mapping, transforming geometry then solution, to $u$, $v$ and $C_p$;
- **logic only, no calculation** (same lines): the steps that turn a cylinder into a Joukowski or KT aerofoil (shift left for thickness, up for camber, through $\bar z=b$ for a sharp TE); derive $b/c$ and $\Gamma$ from the Kutta condition;
- set up and solve lumped-vortex problems (tandem, ground effect, camber, biplane) and explain why $c/4$ and $3c/4$; write every induced velocity as a downwash;
- in ground effect, take only the image's velocity component **normal to the plate**; with camber, resolve the free stream normal to **each segment**, and use small-angle approximations so the equations stay solvable;
- derive the source, vortex and doublet panel influence formulae and their self-induced limits;
- describe both complete panel methods, their Kutta conditions, and how to get $C_L$ and $C_p$. The exam asks for the **process and logic**, not panel-by-panel calculation.

**Chapter 3**

- define $\delta_{99}$, $\delta^*$, $\theta$, $H$, $C_f$ with their mathematical **and** physical meanings, and derive $D=\rho U_e^2\theta$ and $\mathrm d\theta/\mathrm dx=C_f/2$ by control volume. A memory aid: $\delta^*$ → effective body, $\theta$ → drag. $\mathrm d\theta/\mathrm dx=C_f/2$ holds for a flat plate only;
- explain from normalised profiles why a turbulent layer is fuller and has more friction drag;
- evaluate them for an assumed profile (linear, Pohlhausen);
- derive the Blasius and Falkner–Skan equations from the stream-function BL equation; explain similarity and the guess-and-shooting method. Understand the route rather than memorising it: two PDEs → $\psi$ → one PDE → similarity variables → one nonlinear ODE;
- get $\delta^*$, $\theta$, $C_f$, $H$ from $\eta^*$, $\theta^*$, $f''(0)$, including $\theta^*=f''(0)$ by parts, with $f(1-f')\to0$ by the series argument; use the Falkner–Skan table for a wedge or a stagnation point (the cylinder $\delta_{99}$ problem is the typical exam question);
- say where $\delta_{99}/x=5.0/\sqrt{Re_x}$, $\delta^*/x=1.721/\sqrt{Re_x}$, $\theta/x=C_f=0.664/\sqrt{Re_x}$ come from, and their limits: laminar, zero pressure gradient;
- explain the sign of $\beta$ along a bump up to separation, and the effective body for a wedge (revision 3.2 Q4);
- derive the Pohlhausen profile and $\lambda$, and read it as flat plate plus a $\lambda$-weighted pressure-gradient term; derive separation at $\lambda=-12$ (set twice as an exercise); say what $H$ tells you about the pressure gradient; write $\lambda=-Re_\delta\frac{\delta}{\rho U_e^2}\frac{\mathrm dp_e}{\mathrm dx}$ and read off the factors that promote separation; explain why turbulence delays separation and lowers a bluff body's drag although skin friction rises;
- describe natural and bypass transition and receptivity; explain where the Orr–Sommerfeld equation comes from (decomposition, normal modes, linearisation, eigenvalue problem; the full derivation is further reading); read $\hat v e^{i(\alpha_rx-\omega t)}e^{-\alpha_ix}$ as shape, wave and growth; read a thumb plot along constant $F$ and constant $Re$, and keep $Re_{crit}$ apart from transition; apply the $e^n$ method with the envelope and $n_{crit}=9$; state its limitations;
- follow (SESA6087: reproduce) the MIE derivation; reduce it for a flat plate; say why it holds for laminar and turbulent layers and why it needs a closure;
- compare SDM and STM; derive $v_s=\mathrm d(U_e\delta^*)/\mathrm dx$; iterate a simple VII problem; explain why VII (and XFOIL) is unreliable once the layer separates.

**Chapter 4** (the hover bullets lectured on 19–20 Nov, and the climb and descent derivation on 20 Nov; the rest written ahead from the slides, to be checked against the lectures)

- the Chapter 4 equations are in the equation booklet: they need not be memorised, but each must be understood (what it assumes and what every term means);
- draw the actuator-disc streamtube with its key parameters ($A$, $A_2$, $v_i$, $v_2$, $p_\infty$, $\rho$, $p_u$, $p_l$); with Bernoulli and a momentum balance it gives every ADT result. State the six actuator-disc assumptions and derive $T=\tfrac12\rho v_2^2A$ (Bernoulli above and below the disc, not across it), $v_2=2v_i$, $v_0=\sqrt{T/2\rho A}$ and $P_i=Tv_0$; sketch velocity and pressure along the axis and the contracting wake ($A_2=A/2$);
- explain why low disc loading means efficient hover ($T/P_i=1/v_0$, not dimensionless); non-dimensionalise with $V_T=\Omega R$ and $A=\pi R^2$ in the course's convention with $\tfrac12$: $\lambda_i=\sqrt{C_T}/2$, $C_{P_i}=C_T^{3/2}/2$; work the Lynx example;
- integrate the annular-wake thrust and power for $v_i\propto(r/R)^n$ and derive $k_i$, and explain why a uniform downwash needs the least power;
- describe ground effect, wake recirculation and brownout;
- draw the two blade-element diagrams (element on the disc; velocities, angles and forces on the section) and derive the thrust, torque and power (induced plus profile), $C_T/sa=\theta_0/3-\lambda_i/2$, $C_P=C_T\lambda_i+sC_{D0}/4$ and FM (0.7–0.8 for most rotors); know what linear twist ($-\kappa/4$) and annulus theory add;
- derive the climb and descent quadratics from Bernoulli and the streamtube momentum balance, normalise by $v_0$, and justify the physical root in each (sign of the mass flow in climb, direction of the far wake in descent);
- say why momentum theory has no solution for $0<V_D<2v_0$ and name the working states across the range of $\bar V_C$; compute $P=T(V_C+v_i)$ and $T(-V_D+v_i)$; explain why ideal autorotation lies outside momentum theory and derive $\bar V_D=2/\sqrt{C_D}$;
- resolve $V$ into $V_x$ and $V_z$ with the disc tilt and get $\gamma$ and $T$ from the level-flight force balance; derive $v_i=(T/2\rho A)/\sqrt{V_x^2+(V_z+v_i)^2}$, solve it by Newton–Raphson and check its hover, axial and high-speed limits;
- split the forward-flight power into induced, parasite ($TV_z=DV$) and profile parts and sketch the power-against-speed bucket.

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
- Transcripts: `L1 - SESA3043.txt`, `L2 - SESA3043.txt`, `L3 - SESA3043.txt` (Week 1); `L4 - SESA3043.txt`; `02 October 2026 at 14_53_48.txt` (**L5**, CH1-4) and `02 October 2026 at 15_51_44.txt` (Ch1 tutorial); `08 October 2026 at 13_50_19.txt` (Ch2 L1, conformal mapping), `09 October 2026 at 14_57_18.txt` (Ch2 L2, Joukowski and KT), `09 October 2026 at 16_00_58.txt` (Ch2 L3, lumped vortex) and `09 October 2026 at 14_17_51.txt` (Joukowski demo recording); `15 October 2026 at 13_48_35.txt` (ground effect, camber); `16 October 2026 at 14_54_40.txt` and `16 October 2026 at 15_53_48.txt` (camber finished; panel method); `22 October 2026 at 13_51_55.txt` (**BL1**, CH3-1 and the start of CH3-2) and `23 October 2026 at 14_53_16.txt` (**BL2**, CH3-2 to slide 99); `05 November 2026 at 13_59_07.txt` (**BL3**, CH3-2 recap and worked problem, CH3-3 slides 1–26); `06 November 2026 at 14_52_55.txt` (**BL4**, Pohlhausen recap, CH3-3 slides 28–38, CH3-4 to the Orr–Sommerfeld equation) and `06 November 2026 at 15_54_41.txt` (**BL5**, CH3-4 thumb plot, $e^n$ method, pressure gradients); `12 November 2026 at 13_50_20.txt` (**BL6**, coursework and schedule, CH3-5 slides 3–45); `13 November 2026 at 14_46_13.txt` (**BL7**, panel-method refresher, CH3-6, coursework briefing); `19 November 2026 at 13_51_11.txt` (**RL1**, first Chapter 4 lecture, CH4 slides 1–22, introduction to the induced power factor); `20 November 2026 at 14_51_19.txt` (**RL2**, CH4 slides 23–52: ground effect, blade element theory, figure of merit, climb and descent to the real-root condition)
- Coursework code: `02 - Sources/Lectures/dpan.m`, `dpan.py`, `ktreff.m`, `ktreff.py` (posted 16 Oct); `Ch2_Notes_CW Code Explainer.pdf` and `MYKT.dat` (filed 11 Nov)
- Coursework brief: `04 - Labs & Coursework/Panel Method Coursework/AdvAeronautics 2026-27 Coursework.pdf` (filed 11 Nov)
- `02 - Sources/Lectures/CH3-1 Introduction(1).pdf`, `CH3-2 Blasius and Falkner-Skan(1).pdf`, `CH3-3 Pohlhausen.pdf`, `CH3-4 Transition to Turbulence(1).pdf`, `CH3-5 Momentum Integral Eqn(1).pdf`, `CH3-6 Viscous Inviscid Interaction.pdf`
- `02 - Sources/Lectures/Ch3_Notes_Blasius.pdf`, `Ch3_Notes_Falkner-Skan.pdf`, `Ch3_Notes_Pohlhausen.pdf`, `Ch3_Notes_Momentum Integral Eq.pdf` (filed 19 Oct)
- `02 - Sources/Lectures/CH4 Rotor Aerodynamics.pdf` (Hu and Wangsawijaya, Nov 2026; 90 slides, filed 17 Nov: 4.1 hover slides 4–40, 4.2 axial flight 41–68, 4.3 forward flight 69–90; slides 57–63 and 65 are from Dr S.J.I. Walker's *Powered Lift*; slides 1–22 lectured 19 Nov, RL1; slides 23–52 lectured 20 Nov, RL2) → [[SESA3043 4.1 - Rotor in Hover|4.1]], [[SESA3043 4.2 - Rotor in Axial Flight|4.2]], [[SESA3043 4.3 - Rotor in Forward Flight|4.3]]
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
>
> 13 Nov (BL7): the refresher repeated the explainer's two rotation slips and said $y_c\sin\theta$ for $y_c\sin\alpha$ in the free-stream potential; both methods abbreviated "STM"; the coursework Reynolds numbers called "a decade apart" (the brief's $10^5$ and $5\times10^6$ are a factor of 50). Flagged in [[SESA3043 2.3 - Panel Methods#Transcript slips (BL7 refresher)|2.3]] and [[SESA3043 3.6 - Viscous-Inviscid Interaction#Transcript slips (BL7)|3.6]].
>
> 19 Nov (RL1): annular wake division said to vary "along the axial direction" (radial, as said later and on slide 17); ADT described as a "potential flow or viscous flow method" (inviscid only); $\rho Av_i$ first called the momentum flow rate (corrected to mass flow rate); slide 20's "$T_s=1$" repeated. CH4 slides 20–21 also drop the $\mathrm dr$ in the middle integrals. Flagged in [[SESA3043 4.1 - Rotor in Hover#Transcript slips (RL1)|4.1]].
>
> 20 Nov (RL2): one slip of substance, the minus-sign descent root said to be possibly negative (both descent roots are positive for $\bar V_D\geq2$); three slips corrected on the spot (the negative climb root and the climb and induced power curves first pointed to wrongly, the hover streamtube first called the ascending one). Speech-recognition errors only, e.g. "figure of Murray", "split element theory", "v2 equals 5 v8". Flagged in [[SESA3043 4.1 - Rotor in Hover#Transcript slips (RL2, ll. 1–390)|4.1]] and [[SESA3043 4.2 - Rotor in Axial Flight#Transcript slips (RL2, ll. 391–604)|4.2]].
