---
title: "SESA3029 Aerothermodynamics Hub"
module: "SESA3029 Aerothermodynamics"
type: hub
aliases: ["SESA3029 Aerothermodynamics"]
tags: [sesa3029, hub, moc]
status: in-progress
coverage: "Week 1; Lectures 2.1–2.7 and 3.1–3.4 lectured with transcripts (Chapter 3 MoC complete); Tutorial Lecture 1; Example Sheets 1–3; Tests 1–2"
---

# SESA3029 Aerothermodynamics Hub

> [!abstract] Module at a glance
> **Compressible-flow toolkit** → **oblique shocks and expansions** → **supersonic nozzles and the method of characteristics** → **high-speed aerodynamics** → **heat transfer**.
>
> Module lead: Prof. Jae-Wook Kim (Sections 1–4).
>
> **Current vault coverage:**
> - Week 1 complete.
> - Lectures 2.1–2.5 complete, with transcripts (2.3 on Fri 2 Oct, 2.4 on Mon 5 Oct, 2.5 on Thu 8 Oct; the 2.5 recording on Blackboard is last year's).
> - **Tutorial Lecture 1** (Fri 9 Oct): ES1 Q3 and a triangular wing, with the weekend homework solved.
> - **Lecture 2.6** (Laval nozzle, Mon 12 Oct) lectured and backfilled from `Lecture 2-6.txt`: the control-volume derivation with side walls, throat vs bulge, thrust, choking and $p^*/p_0=0.528$, and the $M_e=2.2$ example.
> - **Lecture 2.7** (jets, wind tunnels) lectured **Thu 15 Oct** and backfilled from `Lecture 2-7.txt`: the shock-diamond cycle, the slip line read as a duct wall, and the swallowing of the starting shock by a variable second throat.
> - **Lecture 3.1** (MoC theory, Fri 16 Oct, `Lecture 3-1.txt`): streamtube derivation, Eq. 1 and Eq. 2 in $\nu$ and $\theta$, and the Riemann invariants $R^\pm=\nu\mp\theta$.
> - **Lecture 3.2** (Mon 19 Oct, `Lecture 3-2.txt`), backfilled into W05:
>   - the eigenvalue route and zones of dependence;
>   - the unit process and why the characteristics bend;
>   - the slide 9 example worked live, with the point 3 coordinates set as homework.
> - **Lecture 3.3** (Thu 22 Oct, `Lecture 3-3.txt`), backfilled into W05:
>   - the three boundary conditions and the straightening section;
>   - the minimum-length nozzle, and reading $M_e$ from the throat angle;
>   - the $M_e=2.4$ table, which is the coursework procedure.
>
>   The recording stops at l. 303.
> - **Lecture 3.4** (Fri 23 Oct, `Lecture 3-4.txt`), backfilled into W05 §15:
>   - the symbolic table, with the past-paper hint (ll. 198–203);
>   - why point 3 cannot reflect: *"always think about the results, whether it makes sense or not"* (ll. 279–281);
>   - the inverse problem, $M_0=1.834$ and $\theta_w=5.014^\circ$;
>   - the **MoC coursework brief**, due **15 Nov** (ll. 361–418).
>
>   This completes the MoC block. Next week (w/c 26 Oct) is reading week.
> - Worked solutions to all three example sheets and to Blackboard Tests 1 and 2.
>
> Quick reference: [[SESA3029 Formula Sheet]].

> [!important] Deadlines
> - **Weekend homework (Tutorial 1, ll. 232–235):** triangular wing at a second $\alpha$, check $x_{ac}\approx c/2$. Solved: [[SESA3029 Tutorial Lecture 1 - Shock Reflection and a Triangular Wing#Weekend homework: the aerodynamic centre (ll. 228–235)|Tutorial 1]].
> - ~~Blackboard Test 1, due Sun 11 Oct, 23:59~~ (closed; L2-4, ll. 1–3). Worked: [[SESA3029 Test 1 - Solutions]].
> - **Test 2:** open since Mon 19 Oct, two attempts, closes **Sun 25 Oct, midnight** (L3-1, ll. 3–5; L3-2, ll. 2–8; L3-4, l. 6). Done; worked: [[SESA3029 Test 2 - Solutions]].
> - **MoC coursework (10 %): due 23:59, Sun 15 Nov** on Blackboard (brief; L3-4, ll. 415–418). This supersedes L3-2's *"end of week seven"* (Fri 6 Nov) and agrees with the module guide.
>   - Brief: `04 - Labs & Coursework/MoC Coursework/MoC Coursework 2026-27.pdf`.
>   - A minimum-length nozzle for $M_{des}=3.x$, where $x$ is the last digit of your student ID, for **CO₂ ($\gamma=1.289$), not air**, so the $\gamma=1.4$ tables cannot be used. Use five characteristics from $0.125^\circ$ to $\theta_{max}$ (20 points) and four significant figures.
>   - The report has sections i–vi (marks 5/15/10/25/20/25) in at most six A4 pages: summary, method, verified $\mu$ and $\nu$ code, template, steps for points 1, 2 and the last wall point, then the plot with an $A/A^*$ comparison and limitations.
>   - The method is the §14 table in [[SESA3029 W05 - Method of Characteristics and Minimum-Length Nozzle Design#14. Worked example: minimum-length nozzle for Me = 2.4 (3.3 slides 11–21)|W05]] (L3-3, ll. 132, 221–222). The brief and checks are in [[SESA3029 W05 - Method of Characteristics and Minimum-Length Nozzle Design#Announcements and deadlines|W05, announcements]].
> - **Reading week w/c 26 Oct**: no lectures (L3-4, ll. 4–5, 418).
> - Test 3: 29 Nov. Test 4: 13 Dec.

## Current coverage

1. [[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes]]
   - Mach number and flow regimes;
   - perfect-gas, isentropic and stagnation relations;
   - normal-shock derivation and jump relations;
   - table interpolation;
   - subsonic and supersonic Pitot measurements.
2. [[SESA3029 W02 - Oblique Shock Relations and Mach Waves]] (Lectures 2.1–2.2)
   - oblique-shock geometry and the normal-component method;
   - derivation of the θ–β–M relation;
   - the oblique-shock chart: weak/strong solutions, maximum deflection, detachment;
   - Mach waves, Mach angle and the moving-source picture;
   - **2.2 examples**: chart, interpolation and exact routes; the supersonic intake (normal vs oblique + normal vs isentropic); the bow shock containing every solution.
3. [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method]] (Lectures 2.3–2.5, all with transcripts)
   - regular and Mach reflection, and the regular-reflection limit; transcript slips flagged (e.g. $\phi$ said as 7.5°, correct 17.5°);
   - shock–shock interaction and slip lines (**last year's exam question**, L2-3, ll. 317–390);
   - entropy across a shock: why shocks compress and weak shocks are isentropic;
   - the Prandtl–Meyer function, derived and integrated; expansion fans;
   - the shock-expansion method for a flat plate and a diamond; which side gets which wave; leading-edge suction vs wave drag; the ac shift from $c/4$ to $c/2$ and its static-margin consequence (L2-5).
4. [[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow]] (Lectures 2.6 and 2.7 with transcripts, Mon 12 and Thu 15 Oct)
   - the area–velocity and area–Mach relations; choked mass flow;
   - back-pressure regimes and locating a normal shock in the nozzle;
   - over- and under-expanded jets, shock diamonds and the Mach disc;
   - supersonic wind-tunnel starting (second throat) and the Ludwieg tube.
5. [[SESA3029 W05 - Method of Characteristics and Minimum-Length Nozzle Design]] (Lectures 3.1–3.4 with transcripts, Fri 16, Mon 19, Thu 22 and Fri 23 Oct)
   - streamtube derivation: mass, $l$-momentum with homentropy, zero vorticity; the switch to $\nu$ and $\theta$;
   - compatibility conditions and Riemann invariants, and the same result by eigenvalues;
   - zones of dependence and influence, with the lecture's reversed-song aside qualified;
   - the unit process with averaged slopes, why the lines bend, and the slide 9 example (the coordinates were homework);
   - the three boundary conditions, "any two of $R^+,R^-,\nu,\theta$"; simple and uniform regions;
   - $\theta_{max}=\nu(M_e)/2$, and reading $M_e$ off the throat angle (sharp-corner nozzles only);
   - the $M_e=2.4$ minimum-length nozzle, all 14 points reproduced, converging to $A_e/A^*$;
   - the 3.4 generic example, the non-reflecting point 3, and the inverse problem; the past-paper hint;
   - the MoC coursework brief ($M_{des}=3.x$, CO₂ with $\gamma=1.289$, five lines from $0.125^\circ$, due 15 Nov), with general-$\gamma$ formulas and code-verification checks;
   - slips tables for L3-1 to L3-4.

### Example sheets (worked solutions)

- [[SESA3029 Example Sheet 1 - Solutions]]: normal and oblique shocks, reflection, shock-expansion, nozzle (Weeks 1–4).
- [[SESA3029 Tutorial Lecture 1 - Shock Reflection and a Triangular Wing]]: Fri 9 Oct tutorial. ES1 Q3 with the regular-reflection iteration, and an isosceles triangular wing at $M=1.7$ (drag shortcut corrected; $x_{ac}=0.49c$ homework).
- [[SESA3029 Example Sheet 2 - Solutions]]: eigenvectors, MoC, Ackeret, Prandtl–Glauert. Q2–Q3 are now also in the lecture's $R^\pm$ notation, and Q3 gets an averaged-slope check ($M_C=1.604$ vs the key's 1.558). Q4–Q6 are not yet lectured.
- [[SESA3029 Test 1 - Solutions]]: Blackboard Test 1 (stagnation temperature, Mach number, isentropic density, mass flow, Pitot with the static tapping behind the shock).
- [[SESA3029 Test 2 - Solutions]]: Blackboard Test 2 ($M_1$ from a 38.1 % $p_0$ loss, the supersonic Pitot test, reading the OSC backwards, a flat plate's upper surface, and the L2-3 slide 7 interaction at $M_1=3.1$: $\Delta\theta=5.815^\circ$).
- [[SESA3029 Example Sheet 3 - Solutions]]: heat transfer (Weeks 9–12, previewed). Discrepancies in the answer key are flagged for Q3, Q5 and Q6.

## Week 1 concept map

| Foundations from earlier modules | New SESA3029 concepts |
|---|---|
| [[Speed of Sound and Mach Number]] | [[Normal-Shock Jump Relations]] |
| [[Stagnation Properties]] | [[Shock-Table Interpolation]] |
| [[Isentropic Ideal-gas Relations]] | [[Compressible Pitot Probe]] |
| [[Normal Shock Waves]] | [[Rayleigh Pitot Formula]] |
| [[Aerodynamic Centre and Centre of Pressure]] | |

## Week 2 concept map

| Foundations | New SESA3029 concepts |
|---|---|
| [[Normal-Shock Jump Relations]] | [[Oblique-Shock Jump Relations]] |
| [[Oblique Shock Waves]] (SESA2023) | [[Theta-Beta-Mach Relation]] |
| [[Speed of Sound and Mach Number]] | [[Weak and Strong Oblique Shocks]] |
| [[Intake Pressure Recovery]] (SESA2023) | [[Mach Waves and Mach Angle]] |

## Week 3 concept map (Lectures 2.3–2.5)

| Foundations | New SESA3029 concepts |
|---|---|
| [[Theta-Beta-Mach Relation]] | [[Regular Shock Reflection]] · [[Mach Reflection]] |
| [[Oblique-Shock Jump Relations]] | [[Slip Line]] |
| [[Normal-Shock Jump Relations]] | [[Entropy Change Across a Shock]] |
| [[Mach Waves and Mach Angle]] | [[Prandtl-Meyer Function]] · [[Expansion Fan]] |
| [[Aerodynamic Centre and Centre of Pressure]] | [[Shock-Expansion Theory]] |

## Week 4 concept map (Lectures 2.6–2.7)

| Foundations (Year 2) | New SESA3029 concepts |
|---|---|
| [[Isentropic Nozzle Flow]] (SESA2022) | [[Over- and Under-Expanded Jets]] |
| [[Critical Conditions and Choked Flow]] (SESA2023) | [[Supersonic Wind Tunnel]] |
| [[Converging-Diverging Nozzle Operating Regimes]] (SESA2023) | uses [[Slip Line]], [[Expansion Fan]], [[Mach Reflection]] |
| [[Thrust Equation]] (SESA2023) | thrust from the lecture's control volume (2.6) |

## Week 5 concept map (Lectures 3.1–3.4)

| Foundations | New SESA3029 concepts |
|---|---|
| [[Prandtl-Meyer Function]] · [[Mach Waves and Mach Angle]] | [[Method of Characteristics]] |
| [[Entropy Change Across a Shock]] (why shock-free) | [[Homentropic Flow]] |
| [[Eigenvalues and Eigenvectors]] (MATH1054) | [[Riemann Invariants]] |
| [[Isentropic Nozzle Flow]] · W04 area–velocity relation | [[Minimum-Length Nozzle]] |

## Module roadmap

| Weeks | Block | Planned topics | Vault status |
|---|---|---|---|
| 1 | Basic toolkit | Isentropic flow, normal shocks, shock tables, Pitot probes | **Complete** |
| 2–3 | Oblique shocks and expansions | 2.1 oblique-shock relations; 2.2 chart and examples; 2.3 reflections, slip lines, shock interactions; 2.4 expansion waves and Prandtl–Meyer; 2.5 shock–expansion method; Tutorial 1 | **Complete** (transcripts; 2.3 on 2 Oct, 2.4 on 5 Oct, 2.5 on 8 Oct, Tutorial 1 on 9 Oct) |
| 4–5 | Nozzles and MoC | 2.6 Laval nozzle and back pressure; 2.7 under/over-expanded nozzles, supersonic wind tunnel; 3.1–3.4 method of characteristics, minimum-length nozzles | **Complete**: 2.6, 2.7 and 3.1–3.4 lectured (12, 15, 16, 19, 22 and 23 Oct, transcripts). MoC coursework due Sun 15 Nov |
| 6 | Reading week (w/c 26 Oct) | Consolidation, coursework | — |
| 7–8 | High-speed aerodynamics | Euler equations, wave drag, compressible potential flow, Prandtl–Glauert, Ackeret theory, optimum supersonic aerofoils | Awaiting lectures (ES2 Q4–Q6 preview it) |
| 9–12 | Heat transfer | Conduction, convection, boundary-layer heat transfer, radiation, numerical methods and heat exchangers | Awaiting lectures (ES3 solved in full) |

> [!info] Build policy
> By request, the filed decks for 2.3–2.7 and 3.2–3.4 were written up in full ahead of their recordings. 2.3–2.7 are now backfilled from their transcripts (line references, slips, lecturer-set tasks; 2.7 on 19 Oct), and 3.1 was written from `Lecture 3-1.txt`. 3.2 and 3.3 were backfilled into W05 §§8–14 on 22 Oct, and 3.4 into §15 on 23 Oct. Every filed deck is now lectured and backfilled.

## Assessment snapshot

The Week 1 module guide lists:

- **80%** in-person final examination;
- **10%** Method of Characteristics nozzle-design exercise;
- **10%** from four Blackboard tests at **2.5% each**, with up to two attempts and the highest mark counting.

Test due dates: Test 1 11 Oct, **Test 2 25 Oct**, Test 3 29 Nov, Test 4 13 Dec. The MoC coursework is due **Sun 15 Nov** (L3-4, ll. 415–418), as in the module guide; L3-2's "end of week seven" (6 Nov) is superseded. Exam questions say which method to use: nearest table value, the average of two lines, linear interpolation, or the exact equations (L2-2, ll. 74–80).

Always check Blackboard for any later change to dates or assessment rules.

## Week 1 exam skills

- decide whether a relation is **adiabatic**, **isentropic**, or valid **across a shock**;
- derive and use stagnation-property relations;
- apply mass, momentum and energy conservation to a normal shock;
- interpolate consistently in the isentropic-flow and normal-shock tables;
- identify the correct Pitot regime from the measured pressure ratio;
- keep station notation straight: upstream state 1, downstream state 2, and stagnation states $01$ and $02$.

## Week 2 exam skills (Lectures 2.1–2.2)

- define $\theta$ and $\beta$ from the upstream velocity and resolve $\mathbf V_1,\mathbf V_2$ into normal and tangential components;
- show from tangential momentum that $U_t$ is unchanged, and hence that normal-shock relations apply with $M_{n1}=M_1\sin\beta$;
- derive the θ–β–M relation from the two tangents, mass conservation and the density jump;
- read the oblique-shock chart; choose between weak and strong solutions; recognise detachment when $\theta>\theta_{max}$;
- recover the normal-shock and Mach-wave limits at $\theta=0$;
- derive $\mu=\sin^{-1}(1/M)$ from the moving-source picture;
- solve an oblique shock four ways: nearest value, average, interpolation, exact iteration;
- read the chart **backwards**: given $\theta$ and $\beta$, find $M_1$ by eye or from the closed form $M_1^2=2(\cot\beta+\tan\theta)/[\sin2\beta-\tan\theta(\gamma+\cos2\beta)]$ ([[SESA3029 Test 2 - Solutions#Q3. Mach number from the oblique-shock chart|Test 2 Q3]]);
- chain $p_0$ ratios through an intake shock system and explain why oblique shocks and isentropic ramps recover more.

## Week 3 exam skills (Lectures 2.3–2.5)

- solve a regular reflection (two θ–β–M solves) and test for Mach reflection, $\theta>\theta_{max}(M_2)$;
- state the slip-line conditions and iterate a shock–shock interaction; in last year's exam this was "given the first guess of $\Delta\theta$, make a second guess and interpolate" (L2-3, ll. 379–382);
- explain why a "shock" with $M_{n1}<1$ or a pressure drop is impossible, and why near-sonic Mach waves are isentropic (L2-3, ll. 416–442);
- derive $\Delta s(M_{n1})$, show $\mathrm ds/\mathrm dM_{n1}=0$ at $M_{n1}=1$, and argue that expansion shocks are impossible;
- derive $\mathrm d\nu=\sqrt{M^2-1}\,\mathrm dU/U$ and use $\nu(M_2)=\nu(M_1)+\theta$ with the isentropic ratios;
- apply the shock-expansion method to a flat plate or diamond: pressures, then $L$, $D$, $M_{LE}$ and $x_{cp}$;
- explain which surface gets a shock and which a fan from the streamline (duct) picture (L2-5, ll. 15–27);
- derive $C_{m,LE}=-\Delta p/(2q_\infty)$ with the nose-up convention, and $x_{cp}$ and $x_{ac}$; explain the $c/4\to c/2$ ac shift and why it threatens the static margin (L2-5, ll. 215–257);
- explain leading-edge suction and why supersonic inviscid flow has wave drag (L2-5, ll. 149–213);
- for a thick section, resolve each face's force (not $D=N\sin\alpha$), and estimate $x_{ac}$ from two angles of attack (Tutorial 1);
- find the regular-reflection limit by two guesses and interpolation (Tutorial 1, ll. 63–113).

## Week 4 exam skills (Lectures 2.6–2.7)

- derive $\mathrm dA/A=(M^2-1)\,\mathrm dU/U$ the lecture's way: a control volume including the side-wall force $(p+\tfrac12\mathrm dp)\,\mathrm dA$, then $p=C\rho^\gamma$ (L2-6, ll. 12–76);
- derive $A/A^*(M)$ (homework, L2-6, l. 153) and choked $\dot m$; quote $p^*/p_0=0.528$ and say what it applies to (L2-6, l. 223);
- explain why only a throat, never a bulge, can be sonic, and why exit velocity sets the thrust;
- find $p_{b3}$, $p_{b5}$ and $p_{b6}$ for a nozzle and place a given $p_b$ in its regime;
- locate a normal shock in the diverging section from $p_b$;
- size lip shocks and fans for over- and under-expanded jets and explain the shock diamonds;
- size a wind-tunnel second throat: $A_{t2}/A_{t1}=p_{01}/p_{02}$.

## Week 5 exam skills (Lectures 3.1–3.4)

- derive the streamtube relations: $\partial\theta/\partial n=\frac{1}{\Delta n}\partial\Delta n/\partial l$, mass, $l$-momentum with $(\partial p/\partial\rho)_s=a^2$, giving $(M^2-1)\frac1u u_l=\theta_n$, and $\theta_l-\frac1u u_n=0$ (L3-1);
- substitute $\mathrm du/u=\tan\mu\,\mathrm d\nu$ to get Eq. 1 and Eq. 2; add and subtract; interpret the brackets as derivatives along $\pm\mu$; state $R^\pm$ and Anderson's $K^\pm$;
- diagonalise $\underline A$ (eigenvalues $\pm\tan\mu$, eigenvectors $[1,-1]^T$ and $[1,1]^T$) and explain why $M>1$ is needed;
- explain why the eigenvector route is the general method, and why $\underline E^{-1}$ goes on the left (L3-2, ll. 16–19, 115–166);
- run the unit process with averaged slopes; reproduce $M_3=1.7039$, $(1.3591,\ 0.2814)$ (the coordinates were L3-2 homework); keep the calculator in degrees;
- explain why the characteristics bend: $\mu=\sin^{-1}(1/M)$ changes from point to point (L3-2, ll. 299–318);
- apply the reflecting-wall, cancelling-wall and symmetry conditions, with their coordinate rules; *"R minus is R plus plus two times the wall angle"* (L3-3, ll. 62–63); any two of $R^+,R^-,\nu,\theta$ fix the rest (ll. 32–36);
- derive $\theta_{max}=\nu(M_e)/2$ (with $\nu(1)=0$) and fill the minimum-length-nozzle template; check $y_e/r_a$ against $A_e/A^*$. This is the coursework (L3-3, ll. 132, 221–222);
- read $M_e$ off a sharp throat corner's angle, and know that it fails for gradual nozzles; do not confuse this $\theta_{max}$ with the oblique-shock one (L3-3, ll. 133–139, 204–214);
- work a symbolic MoC table (3.4) in under a minute (*"one of the questions in the past papers"*, L3-4, ll. 198–203), spot a non-reflecting wall point by checking the physics, not just the rules (ll. 206–281), and invert measured Mach numbers for $\theta_w$ and $M_0$ (ll. 298–348).

## All notes

```dataview
TABLE type, status, coverage, file.mtime AS "Updated"
FROM "Year 3/SESA3029 Aerothermodynamics"
WHERE type
SORT type ASC, file.name ASC
```

## Builds on / feeds into

- **From** [[SESA1016 Thermofluids Hub]]: perfect gases, entropy, control-volume conservation and Pitot measurements.
- **From** [[SESA2023 Propulsion Hub]]: [[Stagnation Properties]], [[Speed of Sound and Mach Number]], [[Normal Shock Waves]] and nozzle flow.
- **From** [[SESA2022 Aerodynamics Hub]]: force and moment coefficients, aerodynamic centre, low-speed aerofoil theory and [[Isentropic Nozzle Flow]].
- **Alongside** [[SESA3043 Advanced Aeronautics Hub]]: governing equations and low-speed external flow.

## Sources

- `02 - Sources/Lectures/Lecture1-1.pdf` and `Lecture 1-1.txt`
- `02 - Sources/Lectures/Lecture1-2.pdf` and `Lecture 1-2.txt`
- `02 - Sources/Lectures/Lecture1-3.pdf` and `Lecture 1-3.txt`
- `02 - Sources/Lectures/Lecture2-1.pdf` and `Lecture 2-1.txt`
- `02 - Sources/Lectures/Lecture2-2.pdf` and `Lecture 2-2.txt`
- `02 - Sources/Lectures/Lecture2-3.pdf` and `Lecture 2-3.txt` (Fri 2 Oct)
- `02 - Sources/Lectures/Lecture2-4.pdf` and `Lecture 2-4.txt` (Mon 5 Oct)
- `02 - Sources/Lectures/Lecture2-5.pdf` and `Lecture 2-5 (2025-26 version).txt` (lectured Thu 8 Oct; the transcript is last year's recording of the same deck)
- `02 - Sources/Lectures/Tutorial Lecture #1.txt` (Fri 9 Oct: ES1 Q3, triangular wing)
- `02 - Sources/Lectures/Lecture2-6.pdf` and `Lecture 2-6.txt` (Mon 12 Oct: Laval nozzle)
- `02 - Sources/Lectures/Lecture2-7.pdf` and `Lecture 2-7.txt` (Thu 15 Oct: under/over-expanded nozzles, wind tunnels)
- `02 - Sources/Lectures/Lecture3-1.pdf` and `Lecture 3-1.txt` (Fri 16 Oct: MoC theory, part A)
- `02 - Sources/Lectures/Lecture3-2.pdf` and `Lecture 3-2.txt` (Mon 19 Oct: MoC theory B, unit process)
- `02 - Sources/Lectures/Lecture3-3.pdf` and `Lecture 3-3.txt` (Thu 22 Oct: boundary conditions, minimum-length nozzle; recording cut off at the end)
- `02 - Sources/Lectures/Lecture3-4.pdf` and `Lecture 3-4.txt` (Fri 23 Oct: generic MoC example; MoC coursework announced)
- `04 - Labs & Coursework/MoC Coursework/MoC Coursework 2026-27.pdf` (the coursework brief)
- `02 - Sources/Lectures/Supplementary Note for MoC.pdf` (12 pages, including the axisymmetric appendix)
- Exam data sheets: `Aerothermodynamics Formula Sheet.pdf`, `IFT.pdf`, `NST.pdf`, `OSC.pdf` (summarised in [[SESA3029 Formula Sheet#What the exam formula sheet gives you]])
- `03 - Exams & Past Papers/aerothermo quiz questions - solved on ipad but write own solutions for completeness.txt` (Test 1 questions)
- `03 - Exams & Past Papers/aerothermo test 2 questions.txt` (Test 2 questions)
- `03 - Exams & Past Papers/ExamplesSheet1.pdf`, `ExamplesSheet2.pdf`, `ExampleSheet3(1).pdf`
