---
title: "SESA2029 A1 - Digital Design and the Role of CFD and FEA"
module: "SESA2029 Digital Aerospace Methods"
type: topic
stream: "Part A: Computational Fluid Dynamics"
order: 1
tags: [sesa2029, cfd, digital-design, boundary-layer, y-plus]
aliases: ["Digital design environment", "Role of CFD and FEA", "CFD Lectures 1-2"]
date: 2026-10-30
status: lectured
coverage: "Week 1 (2025-10-02 introduction; 2025-10-03 coursework background) plus the three CW1 videos"
parent: ["[[SESA2029 Digital Aerospace Methods Hub]]"]
prerequisites: []
next_topics: ["[[SESA2029 A2 - Discrete Data, Finite Differences and Taylor Tables]]"]
key_concepts: ["[[Digital Twin and Digital Thread]]", "[[Verification and Validation]]", "[[First-Cell Height and y-plus]]"]
tutorial_sheets: ["[[SESA2029 CFD Worked Examples]]"]
sources: ["02 - Sources/CFD/All_lectures_as_delivered.pdf (L1–L2)", "02 - Sources/Lectures/SESA2029 Lecture 2025-10-02 - 1600.txt", "02 - Sources/Lectures/SESA2029 Lecture 2025-10-03.txt", "02 - Sources/Lectures/SESA2029 Lecture 2025-10-02 - CW1_video1_OpenVSP.txt", "02 - Sources/Lectures/SESA2029 Lecture 2025-09-28 - CW1_video2_Domain_setup.txt", "02 - Sources/Lectures/SESA2029 Lecture 2025-09-28 - CW1_video3_Meshing.txt"]
---

# SESA2029 A1 - Digital Design and the Role of CFD and FEA

> [!abstract] Summary
> Aircraft design is a loop of synthesis, analysis and decision, and since about 1980 computation has steadily replaced wind-tunnel and flight testing in the analysis step: CFD for the fluid, FEA for the structure, and the two coupled for aeroelastics. Digital twins (the current state of each vehicle) and digital threads (its whole history) extend this through manufacture and service. The coursework applies a commercial CFD workflow to an inviscid wing, judged against lifting-line theory, and to laminar and turbulent boundary layers, whose meshes need the first cell at a controlled $y^+$.

> [!summary]- Exam use: quick path
> - **Use it when:** a question asks where CFD and FEA fit in design, what a digital twin or thread is, or where to put the first grid point for a boundary layer.
> - **Assumptions:** flat-plate correlations for the skin friction; air with $\nu\approx1.5\times10^{-5}\ \mathrm{m^2/s}$ unless given.
> - **Method:** 1. $Re_x=U_\infty x/\nu$. 2. $C_f=0.664Re_x^{-1/2}$ (laminar) or $0.059Re_x^{-1/5}$ (turbulent). 3. $\tau_w=\tfrac12C_f\rho U_\infty^2$, $u_\tau=\sqrt{\tau_w/\rho}$. 4. $y_1=y_1^+\nu/u_\tau$ with $y_1^+\approx1$ (resolved) or $>30$ (wall function). 5. Check 10–20 cells inside $\delta$.
> - **Common mistakes:** comparing the half-wing aspect ratio with lifting-line theory, which needs the full span (a factor of 2); putting the first cell in the buffer layer.
> - **Practise:** [[#First-cell height for a turbulent flat plate]] · [[SESA2029 CFD Worked Examples#Q9: Blasius boundary-layer numbers|CFD worked examples Q9]]

Prof Sandham opened with a simulation from his own research: the full compressible Navier–Stokes equations solved for transonic flow over an aerofoil, with a shock wave sitting on a turbulent boundary layer and oscillating back and forth (2025-10-02, ll. 1–60). That oscillation, buffet, makes the lift fluctuate and, if it couples into the structure, shakes the wing, so it marks the edge of the transonic flight envelope. The calculation needed billions of grid points on a supercomputer and still only covered part of a wing section at wind-tunnel conditions. It made the point of the module: computation is powerful enough to change how aircraft are designed, and still too expensive to be used without simplifications whose trustworthiness engineers have to judge.

The module is split by discipline. The first semester, taught by Prof Sandham, covers computational fluid dynamics with finite-difference and finite-volume methods; the second, taught by Dr Ji Yuan, covers finite element analysis of structures. Each half has a coursework worth 30 % and the final exam is worth 40 % (ll. 391–450).

## 1. The design cycle and what changed around 1980

A design starts with brainstorming concepts to meet the customer's requirements, moves through preliminary designs tested against those requirements, and ends with decisions about performance, cost, manufacture and schedule (ll. 61–120). The module concerns the analysis step, and specifically its two halves: fluids and solids, and the coupling between them.

The time spent testing aircraft rose from the first flights to a peak around 1980 and has fallen since (ll. 91–150). Wind-tunnel programmes are very expensive: large facilities such as the European Transonic Wind Tunnel, stiff instrumented models, and long run times. What changed was computer-based analysis, aerodynamics and structures coupled and fed into an optimiser, at first a human looking at results and now increasingly automated. Design offices went from rows of drawing boards to screens, and the trend continues towards certification largely on the computer.

Digitalisation is used in three ways (ll. 121–180). It can simply replace tests, running CFD on the design variants that would once have gone into the tunnel, insofar as the CFD is trusted. It can drive multidisciplinary design optimisation, with aerodynamics and structures inside an automatic optimiser. And it can improve operations, for example by predicting when an engine needs maintenance. Full Navier–Stokes simulation of a whole aircraft is, like fusion, perpetually "50 years away", so practical CFD uses simplified models, and the engineer has to decide when the numbers are good enough and when a physical test is needed, typically when something new is being done (ll. 151–175).

The slides' optimisation loop runs from requirements to an initial design, a feasibility check, and then a parametric geometry fed to the disciplines: aerodynamics (surface pressure and skin friction, hence loads and performance), structures (deflections and strength), their coupling in aeroelasticity, and manufacturing cost (ll. 181–240). The results form large databases from which the optimum parameters are chosen. This module supplies the discipline tools; the third-year design modules do the optimisation.

## 2. Digital twin and digital thread

A digital twin is a digital replica of one particular aircraft or engine in its current state: its full geometry, the wear on each engine part, even a dent left by a supply truck (ll. 211–245). It is used to predict when that vehicle needs inspection or overhaul, and to learn how designs behave in service.

A digital thread follows a product through time: from the original design through manufacture to service, all stored in one system (ll. 241–270). If one aircraft needs more maintenance than expected, or one batch is more efficient than another that was nominally identical, the thread lets engineers trace the cause back through manufacturing tolerances to the design. The twin is the present state; the thread is the history. Lessons learned feed back to the early stages of design.

## 3. The CFD workflow used in the coursework

The coursework follows a typical commercial workflow (2025-10-03, ll. 1–150; CW1 videos). A Python program generates each student's own wing from their student number: a half-span aspect ratio, a taper ratio and a NACA four-digit aerofoil, all with a mean chord of 1 m, so that across the cohort there are some 250 different wings. In the first lab the wing is built in OpenVSP, NASA's open-source preliminary-design CAD tool, using a symmetry plane so that only half the wing is meshed. ANSYS DesignModeler then puts a bounding box around it to form the computational domain, which must extend far enough for free-stream conditions at its boundaries, and ANSYS Meshing generates three unstructured meshes (coarse, medium and fine). In the second lab, ANSYS Fluent solves the inviscid (Euler) flow at three angles of attack. The third lab is a separate study of laminar and turbulent boundary layers on a flat plate, on a structured mesh, compared with the Blasius solution derived in [[SESA2029 A6 - Higher-Order Time Integration, Runge-Kutta and the Blasius Equation|A6]].

The workbench shows the steps as Geometry, Mesh, Setup and Solution, each gaining a green tick when complete (ll. 121–150). Structured meshes, such as a C-mesh wrapped round an aerofoil, are organised in regular rows; unstructured meshes are made of triangles or tetrahedra (2025-10-02, ll. 271–300; [[SESA2029 A10 - Grids and Pressure-Based Solution Algorithms|A10]]).

## 4. Background aerodynamics to judge the CFD

A CFD answer needs an independent check, and for a wing the benchmark is lifting-line theory, derived later in SESA2022 ([[SESA2022 T5 - Finite Wing Theory]]). The coursework's nomenclature (2025-10-03, ll. 145–240): span $b$, semi-span $s=b/2$, mean chord $\bar c$, wing area $S=b\bar c$, full aspect ratio $AR=b/\bar c$, and half-wing aspect ratio $AR_s=s/\bar c$; taper ratio $\lambda=c_{tip}/c_{root}$; sweep measured on the quarter-chord line. OpenVSP works with the half-wing value, but lifting-line theory needs the full one, $AR=2AR_s$: "try not to get out by a factor of 2" (ll. 151–165).

In a NACA four-digit section such as the 2412, the last two digits are the thickness (12 % of chord), the first is the maximum camber (2 %) and the second its position (40 % of chord) (ll. 166–185). The two-dimensional lift curve is a straight line of slope $a_0$ up to stall, with $a_0=2\pi$ per radian from thin aerofoil theory and a zero-lift angle that the Python program provides (ll. 185–210). For a finite wing,

$$
a=\frac{dC_L}{d\alpha}=\frac{a_0}{1+\dfrac{a_0}{\pi AR}(1+\tau)},
\qquad
C_{D_i}=\frac{C_L^2}{\pi eAR},
\qquad
e=\frac{1}{1+\delta},
$$

where $\tau$ and $\delta$ are small corrections for the spanwise loading. Both say the same thing: a higher aspect ratio gives more lift slope and less induced drag, which is why designers push span up to the limit set by structure and airport gates, and why folding wingtips are being tried (ll. 205–240). The Python program solves the discretised lifting-line equation as a matrix system, more accurately as the number of terms increases. Even an inviscid CFD solution has induced drag, because the wing sheds trailing vortices.

An inviscid CFD solution on a reasonable grid usually reproduces the lift slope and aerodynamic centre within a few per cent, since both depend only on the pressure field. Induced drag is much harder, because it depends on resolving the trailing vortex wake, where an automatically generated mesh puts few cells; a mismatch with lifting-line theory is something to discuss with a grid study, not automatically an error ([[Mesh Convergence and Grid Independence]]).

## 5. Resolving a boundary layer

A boundary layer is thin: a few centimetres on a 10 m chord, and less on the coursework's 1 m plate. Seeing how thin, by zooming right in on the mesh, is one of the aims of lab 3 (2025-10-03, ll. 270–310). Capturing it needs enough cells inside it, typically 10–20, packed towards the wall with a strongly stretched mesh.

Prof Sandham rebuilt the wall scaling from the shear stress at the wall (ll. 301–420). For a Newtonian fluid the wall shear stress is proportional to the velocity gradient there:

$$
\tau_w=\mu\left.\frac{\partial u}{\partial y}\right|_w.
$$

Dividing by density, with the kinematic viscosity $\nu=\mu/\rho$ in m²/s,

$$
\frac{\tau_w}{\rho}=\nu\left.\frac{\partial u}{\partial y}\right|_w,
$$

which has units of velocity squared. That defines the friction velocity and a viscous length scale:

$$
u_\tau=\sqrt{\frac{\tau_w}{\rho}},
\qquad
\ell_\tau=\frac{\nu}{u_\tau}.
$$

The wall variables are then

$$
u^+=\frac{u}{u_\tau},
\qquad
y^+=\frac{y\,u_\tau}{\nu}.
$$

Plotted as $u^+$ against $\log y^+$, measured turbulent boundary layers collapse on to one universal curve near the wall, with a straight logarithmic region from $y^+\approx30$ out to about 15 % of the boundary-layer thickness (ll. 421–450). The collapse, found in Göttingen around 1930, is why turbulent boundary layers are predictable even though turbulence has no closed-form solution, and it underlies the design of CFD grids.

There are two ways to treat the wall (ll. 451–480). Most modern turbulence models resolve the viscous sublayer and need the first cell centre at $y_1^+\approx1$ (certainly below 5); "the standard requirement would be to get $y^+$ equal to 1 everywhere". Wall-function models put the first cell in the log layer, $y_1^+>30$, and impose the log law there as a boundary condition, which is cheaper but fails when the log law fails, for example in separated flow near stall. The buffer region between is to be avoided.

To estimate the first-cell height before running, use flat-plate skin-friction correlations (ll. 481–510):

$$
\text{laminar (Blasius): }C_f=0.664\,Re_x^{-1/2},
\qquad
\text{turbulent: }C_f=0.059\,Re_x^{-1/5},
$$

then $\tau_w=\tfrac12C_f\rho U_\infty^2$, $u_\tau=\sqrt{\tau_w/\rho}$ and

$$
y_1=\frac{y_1^+\,\nu}{u_\tau}.
$$

The thicknesses for comparison are $\delta=4.91x\,Re_x^{-1/2}$ (laminar) and $\delta\approx0.38x\,Re_x^{-1/5}$ (turbulent). In the lab the procedure is trial and error: mesh, run, read off $y_1^+$, refine and repeat.

## Worked examples

### First-cell height for a turbulent flat plate

*(Suggested, not lecturer-set; it follows the procedure at the end of the 2025-10-03 lecture.)* Air with $\nu=1.5\times10^{-5}\ \mathrm{m^2/s}$ flows at $U_\infty=30$ m/s. At $x=1$ m,

$$
Re_x=\frac{30\times1}{1.5\times10^{-5}}=2\times10^6,
$$

turbulent. Then

$$
C_f=0.059\times(2\times10^6)^{-0.2}=3.24\times10^{-3},
\qquad
\frac{\tau_w}{\rho}=\tfrac12\times3.24\times10^{-3}\times30^2=1.46\ \mathrm{m^2/s^2},
$$

$$
u_\tau=\sqrt{1.46}=1.21\ \mathrm{m/s},
\qquad
y_1=\frac{1\times1.5\times10^{-5}}{1.21}=12\ \mu\mathrm m
$$

for $y_1^+=1$. The boundary layer is $\delta=0.38\times(2\times10^6)^{-0.2}=21$ mm thick, so the first cell is about $1/1700$ of it, which needs an inflation layer growing by a factor of about 1.1–1.2 per cell. Recomputed in Python.

## Links

- Parent: [[SESA2029 Digital Aerospace Methods Hub]]
- Next: [[SESA2029 A2 - Discrete Data, Finite Differences and Taylor Tables]]
- Concepts: [[Digital Twin and Digital Thread]] · [[Verification and Validation]] · [[First-Cell Height and y-plus]]
- Aerodynamics: [[SESA2022 T5 - Finite Wing Theory]] · [[Law of the Wall]] · [[Displacement and Momentum Thickness]]
- Turbulence models and wall treatment: [[SESA2029 A8 - Turbulence, RANS and Turbulence Models]]
- The structural side of the loop: [[SESA2029 B1 - Introduction to FEA and the Matrix Displacement Method]]

## Sources

- `All_lectures_as_delivered.pdf`, L1 (introduction) and L2 (coursework background), with transcripts `SESA2029 Lecture 2025-10-02 - 1600.txt` and `SESA2029 Lecture 2025-10-03.txt` (Prof N. Sandham); `CFD.txt` holds the same recordings
- CW1 videos: `SESA2029 Lecture 2025-10-02 - CW1_video1_OpenVSP.txt`, `SESA2029 Lecture 2025-09-28 - CW1_video2_Domain_setup.txt`, `SESA2029 Lecture 2025-09-28 - CW1_video3_Meshing.txt`
- Reading list on Blackboard: Chapra and Canale, *Numerical Methods for Engineers*; Ferziger, Perić and Street, *Computational Methods for Fluid Dynamics*

## Self-study tasks

Nothing numerical was set in the first two lectures. The tasks below prepare for the coursework and the exam, which can ask about both lectures and coursework (2025-10-02, ll. 421–450).

### Core

- [ ] Before lab 1: run the wing-generator program, note your wing's aspect ratio, taper ratio and aerofoil, and watch the three CW1 videos (2025-10-02, ll. 481–500; 2025-10-03, ll. 61–90). → [[#3. The CFD workflow used in the coursework]]
- [ ] Explain the difference between a digital twin and a digital thread (lecture summary, 2025-10-02, ll. 511–520). → [[#2. Digital twin and digital thread]]
- [ ] Estimate the first-cell height for $y_1^+=1$ on a turbulent flat plate. → [[#First-cell height for a turbulent flat plate]] · [[First-Cell Height and y-plus]]

### Further practice

- [ ] Explain why induced drag from inviscid CFD may differ from lifting-line theory when the lift slope agrees. → [[#4. Background aerodynamics to judge the CFD]]
- [ ] Derive the units of $\mu$, $\nu$, $u_\tau$ and $\ell_\tau$ (done on the board, 2025-10-03, ll. 321–400). → [[#5. Resolving a boundary layer]]
- [ ] Blasius boundary-layer numbers (CFD worked examples Q9). → [[SESA2029 CFD Worked Examples#Q9: Blasius boundary-layer numbers|solution]]
