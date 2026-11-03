---
title: "SESA2029 A11 - CFD Errors, Verification, Validation and Mesh Quality"
module: "SESA2029 Digital Aerospace Methods"
type: topic
stream: "Part A: Computational Fluid Dynamics"
order: 11
tags: [sesa2029, cfd, validation, mesh-quality]
aliases: ["CFD validation", "CFD V&V", "Beyond RANS", "CFD Lecture 12"]
date: 2026-10-30
status: lectured
coverage: "Week 6 (2025-11-07)"
parent: ["[[SESA2029 Digital Aerospace Methods Hub]]"]
prerequisites: ["[[SESA2029 A10 - Grids and Pressure-Based Solution Algorithms]]"]
next_topics: ["[[SESA2029 B1 - Introduction to FEA and the Matrix Displacement Method]]"]
key_concepts: ["[[Verification and Validation]]", "[[CFD Mesh Quality Metrics]]", "[[Mesh Convergence and Grid Independence]]", "[[DNS, LES and Scale-Resolving Simulation]]"]
tutorial_sheets: ["[[SESA2029 CFD Worked Examples]]"]
sources: ["02 - Sources/CFD/All_lectures_as_delivered.pdf (L12, pp. 165–183)", "02 - Sources/Lectures/SESA2029 Lecture 2025-11-07.txt"]
---

# SESA2029 A11 - CFD Errors, Verification, Validation and Mesh Quality

> [!abstract] Summary
> CFD results carry three kinds of error: modelling (the equations are not reality), discretisation (the grid and time step) and iteration (the residuals have not converged). Verification checks that the equations are solved correctly; validation checks against experiment that they are the right equations. Mesh quality is measured by skewness, aspect ratio and non-orthogonality, and a result is only credible once it is grid-independent. Scale-resolving methods remove the turbulence model step by step, but direct numerical simulation needs grid points rising as $Re^{9/4}$ and cost as $Re^3$, which keeps it out of reach at flight Reynolds numbers.

> [!summary]- Exam use: quick path
> - **Use it when:** asked to classify an error, define verification and validation, judge a mesh, plan a grid study or explain why DNS of an aircraft is unaffordable.
> - **Assumptions:** a converged solution for the discretisation question; equilibrium turbulence (production equals dissipation) for the DNS scaling.
> - **Method:** 1. Name the error: model, grid or iterations. 2. Verification for the last two, validation for the first. 3. Check skewness < 0.9, orthogonal quality > 0.2, average aspect ratio < 5. 4. Run three grids with large steps in cell count and plot each output against cells. 5. For DNS, $\Lambda/\eta\sim Re^{3/4}$, points $\sim Re^{9/4}$, cost $\sim Re^3$.
> - **Common mistakes:** grid studies with small increments (300k, 400k, 500k); calling an Euler-versus-experiment discrepancy a discretisation error.
> - **Practise:** [[#Worked example: the cost of DNS]] · [[SESA2029 CFD Worked Examples#Q13: Cost of DNS|CFD worked examples Q13]]

By the time of this lecture most students had good Blasius comparisons and good lift, pitching-moment and aerodynamic-centre results for the wing, but drag that did not match lifting-line theory (2025-11-07, ll. 1–20). Prof Sandham calls that a useful outcome, "because we don't want you going away believing everything about CFD": a pretty picture from pushing a button is not necessarily correct. The lecture sets out what can go wrong, how to check, and what lies beyond RANS. The mesh-quality section was given by a teaching assistant, introduced in the transcript as Chang Chang (ll. 131–300).

The picture to keep in mind is a chain of approximations between the real flow and the numbers on the screen. Reality is replaced by a mathematical model, which the code may or may not implement correctly; the model is replaced by discrete equations on a grid; and the discrete equations are solved only approximately by iteration. Each link can be checked separately, and the tests differ: comparing with experiment probes the first link, refining the grid the second, and watching the residuals and outputs the third.

## 1. Sources of error

| Error | What it is | How to reduce it |
|---|---|---|
| Modelling | the exact solution of the equations differs from reality, classically because the turbulence model is inadequate | better physics, checked by validation |
| Discretisation | the discrete solution differs from the exact solution of the equations | grid study: if a grid twice as fine in every direction gives the same answer, the result is grid-independent |
| Iteration | the iterations have not converged to the discrete solution | watch the residuals and, better, the outputs ($C_L$, $C_D$) until they stop changing |

(ll. 21–45). A grid-independent solution is "really all we can expect to achieve in a CFD simulation".

Two underlying sources feed these (ll. 46–60). Round-off comes from finite precision: double precision, which the labs should use, gives about $10^{-16}$; single precision about $10^{-8}$, which may affect results; quad precision is almost never needed in fluid mechanics. Truncation is the part of the Taylor series a scheme drops, so a first-order method halves the error when the grid spacing is halved and a second-order method quarters it ([[Truncation Error and Order of Accuracy]]).

## 2. Verification and validation

The distinction is not always clear-cut, but verification asks whether the equations are being solved correctly, without bugs, and validation asks whether the results match reality (ll. 56–95; [[Verification and Validation]]).

Verification compares the code with exact solutions of the Navier–Stokes equations, of which there are few, or uses the method of manufactured solutions: invent a solution, substitute it into the equations to find the source term it would need, add that source to the code, and check the code converges to the invented solution. With a commercial code such as Fluent or STAR-CCM+ you cannot see the source, so you are trusting the vendor's verification; an open-source code at least lets you check, for example, the turbulence-model implementation (ll. 71–78).

Validation compares with experiment. The lecture's example is the RAE 2822 aerofoil at $M=0.729$, where an Euler solution puts the shock in the wrong place (ll. 79–95). That is a modelling error, not discretisation or truncation: at that Reynolds number the right equations are at least RANS with a turbulence model. Experiments are not the absolute truth either: they have errors of their own and often unknown boundary conditions, so validation is frequently a comparison of two imperfect approaches. The coursework compares lifting-line theory, which reduces the wing to a line, with an inviscid CFD wing, each with its own assumptions (ll. 489–500).

Before blaming the CFD for a wrong drag coefficient, check that the normal and tangential force coefficients have been resolved into lift and drag with the correct sines and cosines of $\alpha$ (ll. 101–110).

### The life-cycle of a simulation

The Workbench workflow runs geometry (DesignModeler or imported CAD), mesh, set-up (equations, boundary conditions), solution (ll. 111–130). Around it are two loops. The inner loop checks mesh quality and remeshes until it is acceptable, then runs the solver and adjusts its settings (boundary conditions, turbulence model) while checking the results. If the validation is still poor, the outer loop goes back to the mesh, adds cells, checks its quality again and reruns, possibly several times. Much of the effort in CFD goes into meshing.

## 3. Mesh quality

Mesh quality affects both accuracy and stability: a poor mesh can make the simulation diverge, or run but give poor results (ll. 131–145). Three metrics are standard ([[CFD Mesh Quality Metrics]]).

Skewness is the difference between a cell's shape and that of an equilateral cell of the same volume, zero being ideal (ll. 146–160). For a hexahedron that means vertex angles of 90°, for a tetrahedron 60°. A cell with a maximum vertex angle above 140° or a minimum below 40° significantly reduces accuracy and can make the run diverge.

Aspect ratio is the longest edge divided by the shortest, a measure of stretching (ll. 161–185). Avoid ratios above about 5 in the main flow; up to about 10 is acceptable in boundary-layer regions, and in important regions such as separations or vortices it should stay below 20 to 100. Inside a boundary layer large aspect ratios are an advantage, because the velocity varies mainly in one direction: below about 200 for a steady solver and 20 for an unsteady one.

Non-orthogonality is the angle between the line joining two adjacent cell centres and the normal of their shared face, from 0° (ideal) to 90° (worst) (ll. 186–195). It is recommended below 60°, and above 85° the simulation is likely to diverge outright. Software often rescales it to 0–1 through the cosine of the angle, as Fluent's orthogonal quality, where 1 is ideal.

The examples shown in the lecture were a mesh with high aspect ratio away from the wall, one with non-perpendicular grid lines, and one with strongly skewed cells at the back (ll. 196–225). In ANSYS Meshing, the Statistics group of the mesh object gives node and element counts (a named selection restricts them to the wing), and the Quality group plots a histogram and the minimum, maximum, average and standard deviation of element quality, aspect ratio, skewness and orthogonal quality (ll. 231–290). Extreme minimum or maximum values often sit at a sharp leading or trailing edge, so the average gives the overall picture. The recommended limits are maximum skewness below 0.9, minimum orthogonal quality above 0.2, maximum aspect ratio below 200 and average aspect ratio below 5. These are general recommendations, not guarantees (ll. 291–295). The report should record the element counts of the coarse, medium and fine meshes; quality metrics are optional extras if space allows.

## 4. Mesh independence

Every CFD study should use several grids and check that the outputs are grid-independent (ll. 300–365; [[Mesh Convergence and Grid Independence]]). The increments in cell count should be large: from the default of about 80,000 cells, to a few hundred thousand, to 800,000 to a million. Steps of 300,000, 400,000 and 500,000 "really [are] not going to tell you properly the mesh sensitivity". Plot each output against the number of cells, on a linear or logarithmic scale, or against the cube root of the cell count, which approximates the number of cells in each direction, and look for the curve to flatten.

Different outputs converge at different rates. In the wing lab the lift converges well, while the drag should at least trend towards a value that more cells would refine. The slide's transonic wing needed 8 to 12 million cells to settle the third decimal place of its coefficients, against the coursework's million or so, so imperfect drag is no surprise; in the coursework the first two decimal places are the target. The aerodynamic centre can also be checked on each grid: Fluent's origin sits at the leading edge of the wing root with the moment about the $y$-axis, so the slope of $C_{m,LE}$ against $C_L$ gives $x_{ac}$, which should be near a quarter of the root chord ([[SESA2029 A10 - Grids and Pressure-Based Solution Algorithms#Aerodynamic centre from three CFD cases|A10]]; ll. 336–360).

## 5. Beyond RANS

The hierarchy of methods runs from boundary-element methods (XFOIL, XFLR5) through Euler, steady RANS, unsteady RANS (URANS), hybrid RANS–LES (most famously detached eddy simulation, DES), and large eddy simulation (LES), to direct numerical simulation (DNS), which solves the full Navier–Stokes equations at every scale of turbulence (ll. 366–390). Going up the list, the reliance on turbulence models falls and the cost rises.

### Why DNS is so expensive

Turbulence in the atmosphere spans storms hundreds of kilometres across down to eddies of millimetres that lift a leaf off the ground, and DNS has to resolve all of them (ll. 386–400). The smallest scale is the Kolmogorov microscale, set by the dissipation rate $\varepsilon$ and the viscosity; dimensional analysis gives

$$
\eta=\left(\frac{\nu^3}{\varepsilon}\right)^{1/4}.
$$

If the turbulence is in equilibrium, dissipation equals production, and production scales with the large-scale velocity $U$ and length $\Lambda$, such as the edge velocity and thickness of a boundary layer (ll. 401–410):

$$
\varepsilon\sim\frac{U^3}{\Lambda}.
$$

Substitute into $\eta$:

$$
\eta\sim\left(\frac{\nu^3\Lambda}{U^3}\right)^{1/4}.
$$

Divide $\Lambda$ by it:

$$
\frac{\Lambda}{\eta}\sim\Lambda\left(\frac{U^3}{\nu^3\Lambda}\right)^{1/4}=\left(\frac{U^3\Lambda^3}{\nu^3}\right)^{1/4}=Re^{3/4}.
$$

That is the number of points needed in one direction. In three dimensions the number of grid points goes as $(Re^{3/4})^3=Re^{9/4}$, and with the time steps the cost goes roughly as $Re^3$, so each doubling of Reynolds number costs eight times more (ll. 411–425). Transonic wing flows at $Re\approx10^6$ can be done properly; matching laboratory experiments needs $3\times10^6$, and flight $3\times10^7$, another factor of 10 in Reynolds number and of 1000 in computing power (ll. 426–435).

> [!warning] Lecture slip (2025-11-07, ll. 499–505)
> The closing summary says the "number of grid points going like Reynolds number cubed". The derivation a few minutes earlier (ll. 411–420) gives $Re^{9/4}$ for the grid points; it is the cost, with the time steps included, that goes as $Re^3$.

![[dam_dns_cost_scaling.png|560]]

Moore's law has helped (ll. 441–465). Gordon Moore's observation in the 1960s was that the number of transistors on a chip doubles at a regular interval (the lecture recalls every two years, his 1975 revision). When it seemed to be ending 15 to 20 years ago, computing went massively parallel, and now GPUs carry it further. But the power consumption of the largest machines is now a problem in itself, to the point of needing a power station next to the supercomputer and asking whether the CO₂ of a wing-optimisation run is justified.

### LES and DES

Large eddy simulation resolves the large, energy-carrying eddies of the turbulent spectrum and models the smallest scales, which is cheaper than DNS (ll. 466–470). For a circular cylinder the lecture compares four results (ll. 466–490). Steady RANS gives a steady wake with no vortex shedding at all, missing the key physics. URANS picks up the Kármán vortex street but no smaller scales, so it looks laminar. DES runs RANS in the attached boundary layer on the cylinder and switches to LES in the wake, picking up multiple scales. A fine-grid LES resolves still more and starts to look like reality, with large-scale shedding and small-scale turbulence. DES and LES are increasingly used in industry, particularly for fully stalled flows where unsteady loads on the stalled parts of an aircraft matter ([[DNS, LES and Scale-Resolving Simulation]]; [[Flow Past a Cylinder]]).

### What you need to know and the exam

The examinable points are the sources of error (modelling, discretisation, iteration), the mesh metrics as a check, verification against validation (bearing in mind that experiments have errors and unknown boundary conditions), and the limits computers place on scale-resolving methods at high Reynolds number (ll. 486–505). Further CFD is in the fourth-year Applications of CFD module (low speed) and SESA6082 Computational Aerodynamics (compressible).

The module's exam was described at the end (ll. 511–567). It is a one-hour, in-person exam worth 40 % of the module, with Section A on CFD and Section B on FEA, probably about ten short questions in each: short analyses, facts and physical explanations, such as the need for grid independence; no coding. Everything in the lectures, example sheet and coursework is examinable in principle. There are no past papers, because the module is new (the accrediting bodies, the RAeS and IMechE, wanted CFD and FEA compulsory, and a former third-year module moved into the second year), so a mock paper will be released around April, with revision lectures in May.

## Worked example: the cost of DNS

Take the turbulent boundary layer of [[SESA2029 A8 - Turbulence, RANS and Turbulence Models|A8]] at $x=1$ m: $U=30$ m/s, $\Lambda=\delta=20.9$ mm, $\nu=1.5\times10^{-5}$ m²/s. Then

$$
Re_\Lambda=\frac{U\Lambda}{\nu}=\frac{30\times0.0209}{1.5\times10^{-5}}=4.18\times10^4.
$$

The scale ratio is

$$
\frac{\Lambda}{\eta}\sim Re_\Lambda^{3/4}=2.9\times10^3,
$$

so $\eta\approx20.9\text{ mm}/2900\approx7\ \mu$m: "micron scale in a boundary layer", as the lecture says (ll. 436–440). Resolving just a cube of side $\delta$ needs $(2.9\times10^3)^3\approx2.5\times10^{10}$ points. Scaling up the Reynolds number, recomputed in Python:

| From | To | Grid points ($\times Re^{9/4}$) | Cost ($\times Re^3$) |
|---|---|---|---|
| $10^6$ | $3\times10^6$ (wind tunnel) | 12 | 27 |
| $3\times10^6$ | $3\times10^7$ (flight) | 178 | 1000 |
| $10^6$ | $3\times10^7$ | 2100 | 27,000 |

## Links

- Parent: [[SESA2029 Digital Aerospace Methods Hub]]
- Previous: [[SESA2029 A10 - Grids and Pressure-Based Solution Algorithms]]
- Next: [[SESA2029 B1 - Introduction to FEA and the Matrix Displacement Method]]
- Concepts: [[Verification and Validation]] · [[CFD Mesh Quality Metrics]] · [[Mesh Convergence and Grid Independence]] · [[DNS, LES and Scale-Resolving Simulation]] · [[Residual vs Solution Error]]
- FEA counterpart: [[SESA2029 B10 - FE Verification, Validation and Model Updating]]

## Sources

- `All_lectures_as_delivered.pdf`, L12, pp. 165–183 (LES/DES images after the Strelets group), with transcript `SESA2029 Lecture 2025-11-07.txt` (Prof N. Sandham; mesh-quality section by a teaching assistant)
- Worked example recomputed in Python

## Self-study tasks

### Core

- [ ] Classify errors as modelling, discretisation or iteration, using the RAE 2822 Euler example (2025-11-07, ll. 21–95). → [[#1. Sources of error]] · [[#2. Verification and validation]]
- [ ] Check your own coursework meshes' skewness, orthogonal quality and aspect ratio in ANSYS Meshing (ll. 231–300). → [[#3. Mesh quality]]
- [ ] Wing report: grid study with large increments, $C_L$, $C_D$, $C_m$ and $x_{ac}/c_{root}$ against cell count (ll. 300–365). → [[#4. Mesh independence]]
- [ ] Derive $\Lambda/\eta\sim Re^{3/4}$ and the $Re^{9/4}$ and $Re^3$ scalings (ll. 391–425). → [[#Why DNS is so expensive]] · [[SESA2029 CFD Worked Examples#Q13: Cost of DNS|Worked examples Q13]]
- [ ] Short explain-questions, the exam format (ll. 556–567). → [[SESA2029 CFD Worked Examples#Q14: Short explain-questions (model answers)|Worked examples Q14]]

### Further practice

- [ ] Estimate the Kolmogorov scale and DNS grid for your own boundary-layer lab conditions (suggested, not lecturer-set). → [[#Worked example: the cost of DNS]]
