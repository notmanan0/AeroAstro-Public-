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
> Aircraft design is a loop of synthesis, analysis and decision, and since about 1980 computation has steadily replaced wind-tunnel and flight testing in the analysis step: CFD for the fluid, FEA for the structure, and the two coupled for aeroelastics. Digital twins (the current state of each vehicle) and digital threads (its whole history) extend this through manufacture and service. The coursework applies a commercial CFD workflow to an inviscid wing, judged against lifting-line theory, and to laminar and turbulent boundary layers, whose meshes need the first cell at a controlled $y^+$; the first-cell height follows in closed form as $y_1=y_1^+x/(Re_x\sqrt{C_f/2})$.

> [!summary]- Exam use: quick path
> - **Use it when:** a question asks where CFD and FEA fit in design, what a digital twin or thread is, or where to put the first grid point for a boundary layer.
> - **Assumptions:** zero-pressure-gradient flat-plate correlations for the skin friction; air with $\nu\approx1.5\times10^{-5}\ \mathrm{m^2/s}$ unless given; full-span aspect ratio in lifting-line formulae.
> - **Method:** 1. $Re_x=U_\infty x/\nu$. 2. $C_f=0.664Re_x^{-1/2}$ (laminar) or $0.059Re_x^{-1/5}$ (turbulent). 3. $\tau_w/\rho=\tfrac12C_fU_\infty^2$, $u_\tau=\sqrt{\tau_w/\rho}$. 4. $y_1=y_1^+\nu/u_\tau$ with $y_1^+\approx1$ (resolved sublayer) or $>30$ (wall function). 5. Check 10–20 cells fit inside $\delta$.
> - **Common mistakes:** comparing the half-wing aspect ratio with lifting-line theory, which needs the full span (a factor of 2); putting the first cell in the buffer layer, $8<y_1^+<30$.
> - **Practise:** [[#First-cell height for a turbulent flat plate]] · [[SESA2029 CFD Worked Examples#Q9: Blasius boundary-layer numbers|CFD worked examples Q9]]

Research simulations now solve the full compressible Navier–Stokes equations for transonic flow over an aerofoil, with a shock wave sitting on a turbulent boundary layer and oscillating back and forth. That oscillation, buffet, makes the lift fluctuate and, if it couples into the structure, shakes the wing, so it marks the edge of the transonic flight envelope. The largest such calculations use around ten billion grid points on a supercomputer and still only cover part of a wing section at wind-tunnel conditions. Computation is powerful enough to change how aircraft are designed, and still too expensive to be used without simplifications whose trustworthiness the engineer has to judge.

SESA2029 covers computational fluid dynamics with finite-difference and finite-volume methods in Part A and finite element analysis of structures in Part B. Each part has a coursework worth 30 % and the one-hour, short-question final exam is worth 40 %. Lecture and coursework material are both examinable.

## 1. The design cycle and what changed around 1980

A design starts with synthesis: brainstorming concepts to meet the customer's requirements, drawing on knowledge, experience and some bias. Analysis then tests the concepts against the requirements, collects information about each and weighs their pros and cons, traditionally with wind-tunnel and flight tests. Decision making closes the loop on cost, schedule, performance and the alternatives. CFD and FEA belong to the analysis step, in its two halves of fluids and solids, and the coupling between them.

The time spent testing aircraft in wind tunnels rose from the first flights to a peak around 1980 and has fallen since. Wind-tunnel programmes are very expensive: large facilities such as the European Transonic Wind Tunnel, stiff instrumented models, and long run times. What changed was computer-based analysis. Aerodynamics and structures are computed, coupled and fed to an optimiser, which was once a designer looking at results and is now increasingly an algorithm (as in an aerostructural optimisation loop). Design offices went from rows of drawing boards to screens, and the trend continues towards certification largely on the computer.

Digitalisation is used in three ways. It can support the traditional approach, running CFD on the design variants that would once have gone into the tunnel, insofar as the CFD is trusted. It can create new approaches, such as multidisciplinary design optimisation with aerodynamics and structures inside an automatic optimiser. And it can improve operations and maintenance, for example by predicting when an engine needs attention. Full Navier–Stokes simulation of a whole aircraft is still out of reach for routine design, so practical CFD uses simplified models, and the engineer decides when the numbers are good enough and when a physical test is needed, typically when something new is being tried.

The digital design environment has six parts: the geometry, pre-processing (discretisation into a mesh), links to the analyses of each discipline, coupling between those analyses, a search method such as an optimiser, and post-processing. The disciplines in the loop are aerodynamics (surface pressure and skin friction, hence loads and performance), structures (deflections and strength), their coupling in aeroelasticity, and manufacturing cost. The results form large databases from which the best parameters are chosen. CFD and FEA supply the discipline tools; the optimisation itself is outside this module.

## 2. Digital twin and digital thread

A **digital twin** is a digital model of an intended or actual physical product, system or process that is, for practical purposes, indistinguishable from it, and is used for simulation, integration, testing, monitoring and maintenance. For an aircraft that means one particular airframe or engine in its current state: its full geometry, the wear on each engine part, even a dent left by a supply truck. Each vehicle has its own twin, used to predict when it needs inspection or overhaul and to learn how the design behaves in service.

A **digital thread** is the record of a product's lifetime from creation to removal. It follows the design through manufacture to service in one system, so that if one aircraft needs more maintenance than expected, or one batch is more efficient than another that was nominally identical, engineers can trace the cause back through manufacturing tolerances to the design. The twin is the present state; the thread is the history, and lessons learned along it feed back to the early stages of the next design ([[Digital Twin and Digital Thread]]).

## 3. The CFD workflow used in the coursework

The coursework follows a typical commercial workflow (CW1 videos). A Python program, `CW2025.py`, generates each student's own wing from their student number: a half-span aspect ratio $s/\bar c$, a taper ratio and a NACA four-digit aerofoil, all with mean chord $\bar c=1$ m, so that across the cohort there are some 250 different wings. The example student number 12345678 gives $s/\bar c=6$, $TR=0.7$ and a NACA 2412 section.

The wing is built in OpenVSP, NASA's open-source preliminary-design CAD tool, as a half wing on a symmetry plane, so only half the flow needs to be meshed (lab 1). ANSYS DesignModeler puts a bounding box round it to form the computational domain, which must extend far enough for free-stream conditions to hold at its boundaries, and ANSYS Meshing generates three unstructured meshes (coarse, medium and fine) for a grid study. ANSYS Fluent then solves the inviscid (Euler) flow at three angles of attack, enough to test whether the lift curve really is straight (lab 2). A separate study of laminar and turbulent boundary layers on a flat plate, on a structured mesh, is compared with the Blasius solution derived in [[SESA2029 A6 - Higher-Order Time Integration, Runge-Kutta and the Blasius Equation|A6]].

The Workbench shows the steps as Geometry, Mesh, Setup and Solution, each gaining a green tick when complete; all the post-processing needed is done inside the Fluent solution step. Structured meshes, such as a C-mesh wrapped round an aerofoil, are organised in regular rows; unstructured meshes are made of triangles or tetrahedra ([[SESA2029 A10 - Grids and Pressure-Based Solution Algorithms|A10]]).

## 4. Background aerodynamics to judge the CFD

A CFD answer needs an independent check, and for a wing the benchmark is lifting-line theory, derived in SESA2022 ([[SESA2022 T5 - Finite Wing Theory]]). The coursework's nomenclature is span $b$, semi-span $s=b/2$, mean chord $\bar c$, wing area $S=b\bar c$, full aspect ratio $AR=b/\bar c$, half-wing aspect ratio $AR_s=s/\bar c$, and taper ratio $TR=c_t/c_r$; sweep is measured on the quarter-chord line.

![[dam_wing_nomenclature.png|900]]

OpenVSP works with the half-wing value, but lifting-line theory needs the full one. Since $b=2s$,

$$
AR=\frac{b}{\bar c}=\frac{2s}{\bar c}=2AR_s,
$$

and mixing the two puts the comparison out by a factor of 2 in the aspect ratio. For a trapezoidal half wing the root and tip chords follow from the mean chord. The area of the half wing is $s\bar c$ and also $\tfrac12(c_r+c_t)s$, so

$$
\bar c=\tfrac12(c_r+c_t)=\tfrac12c_r(1+TR),
$$

$$
c_r=\frac{2\bar c}{1+TR}=\frac{2\times1}{1.7}=1.176\ \mathrm m,
\qquad
c_t=TR\,c_r=0.824\ \mathrm m.
$$

In a NACA four-digit section such as the 2412, the last two digits are the maximum thickness (12 % of chord), the first is the maximum camber (2 %) and the second its chordwise position (40 % of chord). The two-dimensional lift curve is a straight line of slope $a_0$ up to stall, with $a_0=2\pi$ per radian from thin aerofoil theory and a zero-lift angle $\alpha_{L=0}$ supplied by the Python program. For a finite wing,

$$
a=\frac{\mathrm dC_L}{\mathrm d\alpha}=\frac{a_0}{1+\dfrac{a_0}{\pi AR}(1+\tau)},
\qquad
C_{D_i}=\frac{C_L^2}{\pi eAR},
\qquad
e=\frac{1}{1+\delta}\le1,
$$

where $\tau$ and $\delta$ are small corrections for a non-elliptic spanwise loading; $\delta$ is the span efficiency factor and $e$ the Oswald efficiency factor. The lift slope is always below $a_0$ and tends to it only as $AR\to\infty$. Both results say the same thing: a higher aspect ratio gives more lift slope and less induced drag, which is why designers push the span up to the limit set by the structure and by airport gates, and why folding wingtips are being tried. Even an inviscid CFD solution has induced drag, because the wing sheds trailing vortices.

The Python program solves the lifting-line equation discretised at $N$ spanwise stations,

$$
\sum_{n=1}^{N}B_n\sin(n\theta_{0,j})\left[\frac{4b}{a_0c(\theta_{0,j})}+\frac{n}{\sin\theta_{0,j}}\right]
=\alpha(\theta_{0,j})-\alpha_{L=0}(\theta_{0,j}),
\qquad j=1,\dots,N,
$$

with $y_0=-\tfrac b2\cos\theta_0$, as an $N\times N$ matrix system for the coefficients $B_n$; a larger $N$ gives a more accurate answer. The lift coefficient is $C_L=\pi AR\,B_1$ and $\delta=\sum_{n\ge2}n(B_n/B_1)^2$.

An inviscid CFD solution on a reasonable grid usually reproduces the lift slope within a few per cent, since it depends only on the pressure field. Induced drag is harder, because it depends on resolving the trailing vortex wake, where an automatically generated mesh puts few cells. A mismatch with lifting-line theory is therefore something to discuss with the grid study, not automatically an error ([[Mesh Convergence and Grid Independence]]).

## 5. Resolving a boundary layer

A boundary layer is thin: a few centimetres on a 10 m chord, and less on the coursework's plate (lab 3). Capturing it needs enough cells inside it, at least 10–20, packed towards the wall with a strongly stretched mesh.

### Wall units from the wall shear stress

For a Newtonian fluid the wall shear stress is proportional to the velocity gradient at the wall, with the viscosity as the constant of proportionality:

$$
\tau_w=\mu\left.\frac{\partial u}{\partial y}\right|_w.
$$

The units fix what each quantity is. A stress is a force per area, and a newton is a kilogram metre per second squared, so

$$
[\tau_w]=\mathrm{N\,m^{-2}}=\mathrm{kg\,m\,s^{-2}\,m^{-2}}=\mathrm{kg\,m^{-1}s^{-2}}.
$$

The velocity gradient is a strain rate:

$$
\left[\frac{\partial u}{\partial y}\right]=\frac{\mathrm{m\,s^{-1}}}{\mathrm m}=\mathrm s^{-1}.
$$

So the viscosity must carry the rest:

$$
[\mu]=\frac{[\tau_w]}{[\partial u/\partial y]}=\frac{\mathrm{kg\,m^{-1}s^{-2}}}{\mathrm s^{-1}}=\mathrm{kg\,m^{-1}s^{-1}}=\mathrm{N\,s\,m^{-2}}.
$$

Divide the stress law by density and write $\nu=\mu/\rho$ for the kinematic viscosity:

$$
\frac{\tau_w}{\rho}=\nu\left.\frac{\partial u}{\partial y}\right|_w,
\qquad
[\nu]=\frac{\mathrm{kg\,m^{-1}s^{-1}}}{\mathrm{kg\,m^{-3}}}=\mathrm{m^2s^{-1}}.
$$

The left side therefore has units $\mathrm{m^2s^{-1}}\times\mathrm s^{-1}=\mathrm{m^2s^{-2}}$, a velocity squared. Its square root defines the friction velocity, and dividing $\nu$ by it gives a length:

$$
u_\tau=\sqrt{\frac{\tau_w}{\rho}}\ \ [\mathrm{m\,s^{-1}}],
\qquad
\ell_\tau=\frac{\nu}{u_\tau}\ \ \left[\frac{\mathrm{m^2s^{-1}}}{\mathrm{m\,s^{-1}}}=\mathrm m\right].
$$

Neither is a physical velocity or length in the flow; they are the reference scales set by the wall friction, different on an A320 wing and on a laboratory plate. Scaling with them gives the dimensionless wall variables

$$
u^+=\frac{u}{u_\tau},
\qquad
y^+=\frac{y}{\ell_\tau}=\frac{y\,u_\tau}{\nu}.
$$

### The law of the wall and the two ways to treat it

Plotted as $u^+$ against $\log y^+$, measured turbulent boundary layers collapse on to one universal curve near the wall. The viscous sublayer, $y^+<8$ in the course convention, has $u^+=y^+$; a logarithmic region runs from $y^+\approx30$ out to about 15 % of the boundary-layer thickness; the buffer layer lies between. The collapse, found in Göttingen around 1930, is why turbulent boundary layers are predictable even though turbulence has no closed-form solution, and it underlies the design of CFD grids.

![[dam_law_of_the_wall_y1plus.png|900]]

There are two ways to capture the wall. If the first cell is in the viscous sublayer, $y_1^+<8$, the sublayer is resolved; depending on the turbulence model $y_1^+<5$ or $y_1^+<1$ may be needed, and the standard industrial target is $y_1^+=1$ everywhere on the surface. If the first cell is in the log layer, $y_1^+>30$, the software may switch to a wall function, which imposes the log law there as a boundary condition. That is cheaper, but it fails where the log law fails, for example in separated flow near stall. The buffer layer, $8<y_1^+<30$, is to be avoided, because neither treatment is valid there.

### First-cell height before running

Before any calculation, flat-plate correlations give an estimate of where the first cell should be:

$$
\text{laminar: }\ \delta=4.91\,x\,Re_x^{-1/2},\quad C_f=0.664\,Re_x^{-1/2};
\qquad
\text{turbulent: }\ \delta=0.38\,x\,Re_x^{-1/5},\quad C_f=0.059\,Re_x^{-1/5}.
$$

The laminar pair comes from the Blasius solution; the turbulent pair is empirical. Chain the definitions together to see what controls $y_1$. The skin friction coefficient defines the wall stress:

$$
\tau_w=\tfrac12C_f\rho U_\infty^2.
$$

Divide by $\rho$ and take the square root:

$$
u_\tau=\sqrt{\tfrac12C_fU_\infty^2}=U_\infty\sqrt{\frac{C_f}{2}}.
$$

Invert the definition of $y^+$ at the first cell:

$$
y_1=\frac{y_1^+\nu}{u_\tau}=\frac{y_1^+\nu}{U_\infty\sqrt{C_f/2}}.
$$

Write $\nu/U_\infty=x/Re_x$:

$$
\boxed{y_1=\frac{y_1^+\,x}{Re_x\sqrt{C_f/2}}}
$$

For the laminar correlation, $\sqrt{C_f/2}=\sqrt{0.332}\,Re_x^{-1/4}$, so

$$
y_1=\frac{y_1^+\,x}{\sqrt{0.332}}\,Re_x^{-3/4}=1.736\,y_1^+\,x\,Re_x^{-3/4}.
$$

For the turbulent correlation, $\sqrt{C_f/2}=\sqrt{0.0295}\,Re_x^{-1/10}$, so

$$
y_1=\frac{y_1^+\,x}{\sqrt{0.0295}}\,Re_x^{-9/10}=5.822\,y_1^+\,x\,Re_x^{-9/10}.
$$

Dividing the thickness by the first-cell height shows how hard the mesh must be stretched. In the laminar case

$$
\frac{\delta}{y_1}=\frac{4.91\,x\,Re_x^{-1/2}}{1.736\,y_1^+x\,Re_x^{-3/4}}=\frac{2.83}{y_1^+}Re_x^{1/4},
$$

and in the turbulent case

$$
\frac{\delta}{y_1}=\frac{0.38\,x\,Re_x^{-1/5}}{5.822\,y_1^+x\,Re_x^{-9/10}}=\frac{0.0653}{y_1^+}Re_x^{7/10}.
$$

The turbulent ratio grows much faster with Reynolds number, which is why a resolved turbulent boundary layer needs a far more strongly stretched wall mesh than a laminar one at the same speed.

![[dam_first_cell_height.png|900]]

The procedure is iterative: mesh, run, read off the actual $y_1^+$ along the plate, adjust the first-cell height and repeat. The estimate only gives the starting mesh.

## Worked examples

### First-cell height for a turbulent flat plate

*(Suggested, not lecturer-set.)* Air with $\nu=1.5\times10^{-5}\ \mathrm{m^2/s}$ flows at $U_\infty=30$ m/s over a flat plate. Find the first-cell height for $y_1^+=1$ at $x=1$ m, assuming a turbulent boundary layer.

The Reynolds number is

$$
Re_x=\frac{U_\infty x}{\nu}=\frac{30\times1}{1.5\times10^{-5}}=2.0\times10^6.
$$

The skin friction coefficient is

$$
C_f=0.059\times(2.0\times10^6)^{-0.2}=0.059\times0.05493=3.241\times10^{-3}.
$$

The kinematic wall stress is

$$
\frac{\tau_w}{\rho}=\tfrac12\times3.241\times10^{-3}\times30^2=1.458\ \mathrm{m^2/s^2}.
$$

The friction velocity is

$$
u_\tau=\sqrt{1.458}=1.208\ \mathrm{m/s}.
$$

The first-cell height is

$$
y_1=\frac{1\times1.5\times10^{-5}}{1.208}=1.24\times10^{-5}\ \mathrm m=12.4\ \mu\mathrm m.
$$

The boundary layer is

$$
\delta=0.38\times1\times0.05493=0.0209\ \mathrm m=20.9\ \mathrm{mm},
$$

so the first cell is about $1/1680$ of the boundary-layer thickness. With a geometric inflation layer growing by a ratio $r$ per cell, the $n$th cell top sits at $y_1(r^n-1)/(r-1)$, taking $y_1$ as the thickness of the first cell; with $r=1.2$, $r^n=1+0.2\times1680=337$ gives $n=\ln337/\ln1.2\approx32$ cells to reach $\delta$, so the 10–20-cell minimum is met comfortably.

> [!check] Two independent routes agree
> The closed form gives $y_1=5.822\times1\times(2\times10^6)^{-0.9}=1.24\times10^{-5}$ m, the same as the step-by-step chain. The velocity at the first cell, from $u^+=y^+$ in the sublayer, is $u_1=u_\tau=1.21$ m/s, about 4 % of $U_\infty$: the first cell sits deep in the near-wall region, as it should.

### First-cell height for a laminar flat plate

*(Suggested, not lecturer-set.)* The same air at $x=0.1$ m has $Re_x=2.0\times10^5$, well inside the laminar range. The Blasius skin friction is

$$
C_f=0.664\times(2.0\times10^5)^{-1/2}=0.664\times2.236\times10^{-3}=1.485\times10^{-3}.
$$

Then

$$
\frac{\tau_w}{\rho}=\tfrac12\times1.485\times10^{-3}\times900=0.668\ \mathrm{m^2/s^2},
\qquad
u_\tau=0.817\ \mathrm{m/s},
$$

$$
y_1=\frac{1.5\times10^{-5}}{0.817}=18.4\ \mu\mathrm m,
\qquad
\delta=4.91\times0.1\times2.236\times10^{-3}=1.10\ \mathrm{mm}.
$$

Here $\delta/y_1=60$, against $1680$ for the turbulent plate. A laminar boundary layer has no viscous sublayer in the turbulent sense, so $y^+$ is just a convenient way to size the wall cell here; the real requirement is 10–20 points across the 1.1 mm.

### Lifting-line benchmark for the example wing

*(Suggested, not lecturer-set; it reproduces what `CW2025.py` returns.)* The example wing has $AR_s=6$, $TR=0.7$ and a NACA 2412 section. Thin aerofoil theory gives $\alpha_{L=0}=-2.08^\circ$ for the 2412. Solving the lifting-line system above with $N=40$ terms for the full wing, $AR=12$, gives $\tau=0.144$ and $\delta=0.053$, so

$$
a=\frac{2\pi}{1+\dfrac{2\pi}{\pi\times12}(1.144)}=\frac{6.283}{1.1907}=5.277\ \mathrm{rad^{-1}}=0.0921\ \mathrm{deg^{-1}}.
$$

At $\alpha=5^\circ$,

$$
C_L=a(\alpha-\alpha_{L=0})=5.277\times\frac{(5+2.08)\pi}{180}=5.277\times0.1236=0.652,
$$

$$
C_{D_i}=\frac{C_L^2(1+\delta)}{\pi AR}=\frac{0.652^2\times1.053}{\pi\times12}=0.0119.
$$

If $AR_s=6$ were used by mistake, the same solver gives $a=4.609\ \mathrm{rad^{-1}}$, $C_L=0.569$ and $C_{D_i}=0.0176$: a 13 % lower lift slope and 48 % more induced drag, an error large enough to make a good CFD result look wrong.

> [!check] Limits of the lift-slope formula
> An elliptic wing has $\tau=0$; at $AR=12$ that gives $a=2\pi/(1+1/6)=5.386\ \mathrm{rad^{-1}}$, 2 % above the tapered wing's 5.277, as it should be since the ellipse is the most efficient loading. As $AR\to\infty$, $a\to2\pi$.

## Links

- Parent: [[SESA2029 Digital Aerospace Methods Hub]]
- Next: [[SESA2029 A2 - Discrete Data, Finite Differences and Taylor Tables]]
- Concepts: [[Digital Twin and Digital Thread]] · [[Verification and Validation]] · [[First-Cell Height and y-plus]]
- Aerodynamics: [[SESA2022 T5 - Finite Wing Theory]] · [[Law of the Wall]] · [[Displacement and Momentum Thickness]]
- Turbulence models and wall treatment: [[SESA2029 A8 - Turbulence, RANS and Turbulence Models]]
- The structural side of the loop: [[SESA2029 B1 - Introduction to FEA and the Matrix Displacement Method]]

## Sources

- `All_lectures_as_delivered.pdf`, L1 (introduction, slides 1–17) and L2 (coursework briefing, slides 1–15), with transcripts `SESA2029 Lecture 2025-10-02 - 1600.txt` and `SESA2029 Lecture 2025-10-03.txt` (Prof N. Sandham); `CFD.txt` holds the same recordings
- CW1 videos: `SESA2029 Lecture 2025-10-02 - CW1_video1_OpenVSP.txt`, `SESA2029 Lecture 2025-09-28 - CW1_video2_Domain_setup.txt`, `SESA2029 Lecture 2025-09-28 - CW1_video3_Meshing.txt`
- Reading list (L1 slide 15): Chapra and Canale, *Numerical Methods for Engineers*; Ferziger, Perić and Street, *Computational Methods for Fluid Dynamics*
- Numbers in the worked examples recomputed in Python (flat-plate correlations; Glauert lifting-line solve with $N=40$; thin-aerofoil $\alpha_{L=0}$ for the NACA 2412). Figures: `01 - Notes/Figures/generate_dam_a1_figures.py`; the law-of-the-wall figure comes from `generate_dam_a8_figures.py`.

## Self-study tasks

Nothing numerical was set in the first two lectures. The need-to-know list (L1 slide 17) and the coursework preparation (L2 slide 15) are the tasks below.

### Core

- [ ] Before lab 1: run the wing-generator program, note your wing's aspect ratio, taper ratio and aerofoil, and watch the three CW1 videos (L2 slides 4 and 15). → [[#3. The CFD workflow used in the coursework]]
- [ ] Explain the role of CFD and FEA in the design environment (L1 slide 17). → [[#1. The design cycle and what changed around 1980]]
- [ ] Explain the difference between a digital twin and a digital thread (L1 slide 17; 2025-10-02, l. 519). → [[#2. Digital twin and digital thread]]
- [ ] Estimate the first-cell height for $y_1^+=1$ on a turbulent flat plate (L2 slide 14). → [[#First-cell height for a turbulent flat plate]] · [[First-Cell Height and y-plus]]

### Further practice

- [ ] Derive the units of $\mu$, $\nu$, $u_\tau$ and $\ell_\tau$ (done on the board, 2025-10-03, ll. 320–400). → [[#Wall units from the wall shear stress]]
- [ ] Derive the closed forms $y_1\propto Re_x^{-3/4}$ (laminar) and $Re_x^{-9/10}$ (turbulent), and explain why the turbulent mesh must be stretched harder (suggested, not lecturer-set). → [[#First-cell height before running]]
- [ ] Compute the lift slope and induced drag of your own wing with $AR$ and with $AR_s$, and explain the difference (suggested, not lecturer-set). → [[#Lifting-line benchmark for the example wing]]
- [ ] Explain why induced drag from inviscid CFD may differ from lifting-line theory when the lift slope agrees. → [[#4. Background aerodynamics to judge the CFD]]
- [ ] Blasius boundary-layer numbers (CFD worked examples Q9). → [[SESA2029 CFD Worked Examples#Q9: Blasius boundary-layer numbers|solution]]

## Transcript and slide slips

> [!warning] Transcript slips (2025-10-03)
> Where: [[#The law of the wall and the two ways to treat it]] and [[#Wall units from the wall shear stress]].
>
> | Line | Transcript says | Correct |
> |---|---|---|
> | l. 314 | "a few record-start record-amazing things" | speech-to-text noise; the board work is the wall-stress law $\tau_w=\mu\,\partial u/\partial y$ |
> | ll. 427–428 | "experiments around 1930 in Goettingen by Nicaragua, Prandtl and von Kármán" | Nikuradse, Prandtl and von Kármán (Göttingen) |
> | ll. 463–466 | the first cell should be at "y1 plus less than 5 or y1 plus less than 1" | consistent with L2 slide 13, which also gives the wider sublayer bound $y_1^+<8$ and the buffer layer $8<y_1^+<30$ |
