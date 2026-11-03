---
title: "SESA2029 B9 - Nonlinear FE Analysis"
module: "SESA2029 Digital Aerospace Methods"
type: topic
stream: "Part B: Finite Element Analysis"
order: 20
tags: [sesa2029, fea, nonlinear]
aliases: ["Nonlinear FEA", "Geometric nonlinearity", "Newton-Raphson FEA", "FEA Lecture 11"]
date: 2026-10-30
status: lectured
coverage: "FEA week 6 (2026-03-06 09:58)"
parent: ["[[SESA2029 Digital Aerospace Methods Hub]]"]
prerequisites: ["[[SESA2029 B8 - Modal Analysis]]"]
next_topics: ["[[SESA2029 B10 - FE Verification, Validation and Model Updating]]"]
key_concepts: ["[[Sources of Nonlinearity in FEA]]", "[[Direct Substitution and Newton-Raphson]]"]
tutorial_sheets: ["[[SESA2029 FEA Worked Examples]]"]
sources: ["02 - Sources/FEM Lectures/Lecture_11_Nonlinear_FEA_final(1).pdf", "02 - Sources/Lectures/SESA2029 Lecture 2026-03-06 - 0958.txt"]
---

# SESA2029 B9 - Nonlinear FE Analysis

> [!abstract] Summary
> A linear analysis has stiffness and loads independent of displacement, so $\{d\}=[K]^{-1}\{F\}$ in one step. Real structures, increasingly so with light, flexible, net-zero-driven designs, are nonlinear in their geometry (large deflections, follower forces), their material (plasticity, creep, viscoelasticity) or their boundaries (contact, friction, deformation-dependent loads). The stiffness then depends on the displacement, frequencies and mode shapes depend on amplitude, and new behaviour such as limit-cycle oscillation appears. The equations are solved iteratively from a linear first guess, by direct substitution (slow, linear convergence) or Newton–Raphson (quadratic convergence), at several times the cost of a linear run.

> [!summary]- Exam use: quick path
> - **Use it when:** asked what makes an FE problem nonlinear, to classify a nonlinearity, or to explain how a nonlinear solver works.
> - **Assumptions:** a known stiffness law $k(u)$ for the model problem; load applied in one step (or in increments for strong nonlinearity).
> - **Method:** 1. Linear first guess $u_1=P/k_0$. 2. Direct substitution: $u_{i+1}=P/k(u_i)$. 3. Newton–Raphson: residual $R=k(u)u-P$, tangent $K_T=dR/du$, $u_{i+1}=u_i-R/K_T$. 4. Stop when the change is small. 5. In ANSYS, turn on large deflection and set the solution controls.
> - **Common mistakes:** using a linear analysis for a large-deflection or contact problem; confusing time-independent plasticity with time-dependent creep.
> - **Practise:** [[#Worked example: a softening spring]]

The last week of Part B has two lectures: nonlinear FEA, as an introduction to its importance and consequences rather than a skill to practise, and verification and validation in [[SESA2029 B10 - FE Verification, Validation and Model Updating|B10]] (2026-03-06 09:58, ll. 11–30).

With a small fish on the line, a fishing rod's tip deflection is proportional to the pull, and one stiffness describes the rod. With a big fish, the rod bends so far that its own shape changes how it carries the load, and it gets stiffer as it bends: the stiffness depends on the deflection, which depends on the stiffness. There is no single matrix to invert, so the answer has to be found by guessing a deflection, working out the stiffness for that shape, and correcting the guess until the two agree.

## 1. Why nonlinearity matters now

Everything so far, static or dynamic, assumed linear material properties and small deformations, an idealisation; essentially all engineering problems are nonlinear to some degree (ll. 11–30). The pressure to meet net-zero targets is making nonlinearity unavoidable in aerospace: composites replacing aluminium in wings and fan blades, very high-aspect-ratio wings with large deflections, folding wingtips to reduce induced drag and fuel burn, and vertical take-off configurations with multi-physics coupling, gaps and cubic-spring nonlinearities (ll. 26–40).

The consequences are both static and dynamic (ll. 41–60). The stiffness matrix is no longer fixed but depends on the amplitude of deformation, so a dynamic analysis built on it has amplitude-dependent natural frequencies and mode shapes, and new behaviours appear: instability, chaotic motion, and bistability, two stable equilibria where a linear model has one. Mathematically, the linear equation $\{F\}=[K]\{d\}$ becomes

$$
\{F(\{d\})\}=[K(\{d\})]\{d\},
$$

with the stiffness, and sometimes the force, depending on the displacement (ll. 61–80). Aerodynamic loads are the typical case: as a wing deforms, the pressure stays normal to the moving surface and twist changes the angle of attack. The matrix cannot simply be inverted, so special algorithms are needed, and they are expensive. Preliminary sizing therefore assumes linearity, and nonlinearity is brought in as the design matures and higher fidelity is needed.

| | Linear | Nonlinear |
|---|---|---|
| Stiffness and forces | independent of displacement | functions of displacement |
| Solution | $\{d\}=[K]^{-1}\{F\}$ directly | iterate, starting from the linear solution |
| Cost | 1× | several times to orders of magnitude more |

Two examples show the consequences (ll. 81–110). A rectangular beam in pure bending with elastic–perfectly-plastic material (slide: $b=1$ in, $h=2$ in, $E=30\times10^6$ psi, $\nu=0.3$, $\sigma_{yp}=36\,000$ psi) forms a plastic hinge, the same mechanism designed into a folding wingtip to relieve gust loads. The linear run gives a maximum nodal displacement of 0.09 in 4.4 s of CPU time; the nonlinear run gives significantly different deformation and takes about three times as long (13.3 s). Dynamically, linear flutter analysis gives a single flutter speed, the limit of the flight envelope; with structural nonlinearity, as in a tiltrotor's whirl flutter, a limit-cycle oscillation branch appears starting about 20 % below the linear flutter speed, shrinking the envelope and causing early fatigue. Flutter itself is next year's aircraft structures course.

## 2. Sources of nonlinearity

There are three main types ([[Sources of Nonlinearity in FEA]]).

Geometric nonlinearity comes from large deformations and rotations (ll. 111–120, 176–205). The change of geometry is taken into account in the strain–displacement and equilibrium equations, so $\{\varepsilon\}=[B(\{d\})]\{d\}$ with a $[B]$ matrix that depends on the displacement. It occurs in slender aerospace, civil and mechanical structures and in tension structures such as cables and inflatable membranes. A Boeing 787 wing deflects visibly where an aluminium wing would not. The fishing rod is linear under a small load but follows a quadratic or cubic curve under a large one; such stiffness laws are identified from nonlinear static analysis or experiment. The follower force is another geometric effect: with small deformations the aerodynamic load keeps its original direction, but with large ones it stays perpendicular to the deformed surface and so changes direction with the deformation.

Material nonlinearity arises when stress and strain are not linearly related, for example beyond a yield point, and the behaviour depends on the current state of deformation and possibly its history (ll. 118–135, 201–225). It includes nonlinear elasticity, as in rubbers and functional or metamaterials designed to be nonlinear; plasticity, which is time-independent; creep, which is time-dependent, as in turbine blades and high-pressure compressors held at high temperature, where the properties degrade with time; and viscoelastic and viscoplastic behaviour, whose properties depend on frequency and temperature, so a linear property valid at one condition is wrong across the operating range. Warning signs are cracks, necking and thinning, distortion of open-section beams, buckling and local yielding, stress beyond the linear limit, permanent deformation after unloading, shear bands, and temperatures close to melting.

Boundary nonlinearity comes in two forms (ll. 136–150, 221–245). Force boundary conditions can depend on the deformation: hydrostatic, aerodynamic and hydrodynamic pressures change magnitude and direction as a lightweight structure deforms and twists. Displacement boundary conditions can depend on it too, through contact: clamped and bolted joints micro-slip under deformation, Coulomb friction jumps between stick and slip, and impacts such as a bird strike produce force spikes. In turbomachinery, friction dampers (under-platform, mid-span, ring dampers) and tip shrouds rely on contact friction to dissipate vibration energy, behaviour no linear simulation can capture. The bodies themselves can stay perfectly linear elastic; the nonlinearity is entirely in the contact law.

The lecturer's aero-engine research has all three (ll. 151–175): material nonlinearity in composite fan blades and the frequency- and temperature-dependent viscoelastic patches added to damp them; boundary nonlinearity in friction dampers and bolted joints; and geometric nonlinearity in large fan blades at high speed, where modes interact (a first bending mode picks up extension), which can cause blade-tip rubs on the casing and, in the worst case, a fan-blade-off event.

## 3. Solving nonlinear equations

Several methods exist: direct substitution with or without relaxation, Newton–Raphson (the basis of most nonlinear solvers, including the dynamic solvers Dr Yuan develops), modified Newton–Raphson, incremental methods and quasi-Newton methods, all related to optimisation (ll. 241–255; [[Direct Substitution and Newton-Raphson]]). The lecture does not derive them, but says to understand a method's limitations before choosing it in software.

The model problem is a spring pulled by a force $P$ whose stiffness has a constant part and a displacement-dependent part (ll. 256–285):

$$
\left(k_0+k_N(u)\right)u=P .
$$

$k_N>0$ means the spring hardens, $k_N<0$ that it softens, as with many geometric nonlinearities.

Direct substitution starts from the linear spring, $u_1=P/k_0$, the initial guess. It then updates the stiffness with the current displacement and solves again,

$$
u_{i+1}=\frac{P}{k_0+k_N(u_i)},
$$

repeating until $|u_{i+1}-u_i|$ is small. Graphically, each step follows a secant from the origin to the force–displacement curve.

The lecture mentions that the same problem can be formulated for Newton–Raphson by defining a residual (ll. 271–280); the formulation is as follows. Define

$$
R(u)=k(u)\,u-P,
$$

which is zero at the solution. Expand it about the current estimate to first order:

$$
R(u_i+\Delta u)\approx R(u_i)+K_T(u_i)\,\Delta u,
\qquad
K_T=\frac{dR}{du}.
$$

Set the expansion to zero:

$$
\Delta u=-\frac{R(u_i)}{K_T(u_i)},
$$

so

$$
u_{i+1}=u_i-\frac{R(u_i)}{K_T(u_i)}.
$$

$K_T$ is the tangent stiffness, the local slope of the force–displacement curve. In matrix form each iteration solves $[K_T]\{\Delta d\}=\{F\}-\{F_{int}(\{d\})\}$, which needs a new tangent matrix and factorisation each time; modified Newton–Raphson reuses an old tangent to save that cost, converging more slowly. Newton–Raphson converges quadratically near the solution, roughly doubling the number of correct digits each iteration, whereas direct substitution converges linearly.

In ANSYS, nonlinear static analysis is set up through Solution Controls: large-deflection effects on, the number of substeps (load increments), the Newton–Raphson option, convergence criteria and the equation solver (ll. 281–295). It is not required in this module's labs.

![[dam_nonlinear_solvers.png|780]]

## 4. Lab 3 questions

The end of the lecture answered frequent lab 3 questions (ll. 301–360; [[SESA2029 C4 - APDL Workflow - Shell Wing Static and Modal (SHELL181 and SHELL281)|C4]]):

- The stress increases as the mesh is refined because the wing root has a sharp corner, a singularity ([[SESA2029 B7 - Meshing, Convergence and Mesh Checks|B7]]), so the stress there should not be used for the convergence study.
- The software crashes on fine meshes either because the DOF count exceeds memory or the student-licence limit, or because refinement has created distorted elements (aspect ratio above 5 or 6), usually at the sharp trailing edge, from which no valid stiffness matrix can be formed. Check the elements before solving.
- The deformation looks wrong under surface pressures because a pressure acts along the surface normal; turn on the pressure symbols (PlotCtrls → Symbols) to check the direction, and use a negative pressure to reverse it.
- If a closed job will not reopen, start ANSYS with a new job name and load the `.db` file from inside the program.
- No natural frequencies appear in the modal analysis because the density was not defined, so the mass matrix is zero ([[SESA2029 B8 - Modal Analysis|B8]]).

The report is due on 16 March, within the 10-page template.

## Worked example: a softening spring

Take $k(u)=100-50u$ (N/mm, $u$ in mm) and $P=40$ N. The exact solution solves $100u-50u^2=40$, a quadratic,

$$
u^2-2u+0.8=0
\quad\Longrightarrow\quad
u=1-\sqrt{0.2}=0.552786\text{ mm}.
$$

Direct substitution starts with $u_1=40/100=0.4$, then $k=100-20=80$ gives $u_2=0.5$, then $k=75$ gives $u_3=0.5333$, and so on.

For Newton–Raphson, $R(u)=100u-50u^2-40$ and $K_T=100-100u$. From $u_0=0$: $R=-40$, $K_T=100$, so $u_1=0.4$, the same first step since $K_T(0)=k(0)$. Then $R(0.4)=-8$, $K_T=60$, so $u_2=0.4+8/60=0.5333$. Then $R(0.5333)=-0.889$, $K_T=46.67$, so $u_3=0.552381$. Recomputed in Python:

| Iteration | 1 | 2 | 3 | 4 | 5 |
|---|---|---|---|---|---|
| Direct substitution | 0.4000 | 0.5000 | 0.5333 | 0.5455 | 0.5500 |
| Newton–Raphson | 0.4000 | 0.5333 | 0.552381 | 0.5527862 | 0.552786405 |

After five iterations Newton–Raphson has reached machine precision, while direct substitution is still $3\times10^{-3}$ short, because each secant step uses a stiffness that is too high for a softening spring.

## Links

- Parent: [[SESA2029 Digital Aerospace Methods Hub]]
- Previous: [[SESA2029 B8 - Modal Analysis]]
- Next: [[SESA2029 B10 - FE Verification, Validation and Model Updating]]
- Concepts: [[Sources of Nonlinearity in FEA]] · [[Direct Substitution and Newton-Raphson]]
- Iterative solution of linear systems on the CFD side: [[Jacobi, Gauss-Seidel and SOR Iteration]]
- The linear assumptions this lecture relaxes: [[SESA2029 B2 - Linear Elastic FE Analysis - Procedure, Boundary Conditions and Yield]]

## Sources

- FEA Lecture 11 slides, `Lecture_11_Nonlinear_FEA_final(1).pdf` (plastic hinge after ANSYS verification manual VM24; limit-cycle example after McGurk and Yuan, IFASD 2022), with transcript `SESA2029 Lecture 2026-03-06 - 0958.txt` (Dr J. Yuan)
- Worked example recomputed in Python; figure from the module's `scripts/make_figures.py`

## Self-study tasks

### Core

- [ ] Explain the difference between a linear and a nonlinear FE problem and why nonlinear analysis is used later in design (2026-03-06 09:58, ll. 41–80). → [[#1. Why nonlinearity matters now]]
- [ ] Classify nonlinearities as geometric, material or boundary, with an aerospace example of each (ll. 111–245). → [[#2. Sources of nonlinearity]]
- [ ] Describe the direct substitution method for a nonlinear spring (ll. 256–285). → [[#3. Solving nonlinear equations]]
- [ ] Lab 3: check the convergence location, element distortion, pressure direction and density before submitting on 16 March (ll. 301–360). → [[#4. Lab 3 questions]]

### Further practice

- [ ] Repeat the spring example for a hardening spring $k=100+50u$ by both methods (suggested, not lecturer-set). → [[#Worked example: a softening spring]]
