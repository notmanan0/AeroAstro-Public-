---
title: "SESA2029 B9 - Nonlinear FE Analysis"
module: "SESA2029 Digital Aerospace Methods"
type: topic
stream: "Part B: Finite Element Analysis"
order: 20
tags:
  - sesa2029
  - fea
  - nonlinear
aliases: ["Nonlinear FEA", "Geometric nonlinearity", "Newton-Raphson FEA"]
date: 2026-09-24
status: complete
parent: ["[[SESA2029 Digital Aerospace Methods Hub]]"]
prerequisites: ["[[SESA2029 B8 - Modal Analysis]]"]
next_topics: ["[[SESA2029 B10 - FE Verification, Validation and Model Updating]]"]
key_concepts: ["[[Sources of Nonlinearity in FEA]]", "[[Direct Substitution and Newton-Raphson]]"]
tutorial_sheets: ["[[SESA2029 FEA Worked Examples]]"]
sources: ["02 - Sources/FEM Lectures/Lecture_11_Nonlinear_FEA_final(1).pdf", "02 - Sources/FEM Lectures/FEA.txt"]
---

# SESA2029 B9 - Nonlinear FE Analysis

> [!abstract] Summary
> **Linear** means that stiffness and loads do not depend on displacement: $\{F\} = [K]\{d\}$, solved once. Real structures, especially light, flexible, net-zero-driven designs, are **nonlinear** in three ways:
> - **geometric**: large deflection and rotation; follower forces;
> - **material**: plasticity, creep, viscoelasticity, nonlinear elasticity;
> - **boundary/contact**: gaps, friction, impact, deformation-dependent loads.
>
> $[K]$ then depends on $\{d\}$, which gives amplitude-dependent stiffness, natural frequencies and mode shapes, and behaviours linear theory cannot predict: multiple equilibria, limit-cycle oscillations, chaos.
>
> Solve iteratively:
> - **direct substitution** (secant, linear convergence);
> - **Newton–Raphson** (tangent stiffness, quadratic convergence);
> - modified NR, incremental and quasi-Newton methods.
>
> A nonlinear solve costs 10–100× a linear one.

## Key Concepts
- [[Sources of Nonlinearity in FEA]] · [[Direct Substitution and Newton-Raphson]]

---

## 1. Why nonlinearity matters now (L11)
The drive to **net zero by 2050** pushes aircraft towards lightweight composites and new configurations:
- very high-aspect-ratio flexible wings;
- **folding wingtips**, which include a hinge;
- tiltrotors and VTOL;
- open rotors.

These show large deformations, material nonlinearity, friction interfaces and multi-physics coupling. Stiffness, frequencies and mode shapes then depend on amplitude, giving bistability, limit-cycle oscillation (LCO) and chaotic motion.

| | Linear problem | Nonlinear problem |
|---|---|---|
| Stiffness and forces | independent of displacement | functions of displacement |
| Solution | $\{d\} = [K]^{-1}\{F\}$ directly | iterate from a (linear) initial guess |
| Cost | 1× | 10–100× |

In practice nonlinear solutions are approximated by linear ones where possible (preliminary sizing is linear). Nonlinearity is added when fidelity demands it.

> [!example] Plastic hinge (L11)
> A rectangular beam ($b = 1$ in, $h = 2$ in, $I_z = bh^3/12 = 0.667$ in⁴; $E = 30\times10^6$ psi, $\nu = 0.3$, $\sigma_{yp} = 36\,000$ psi) is loaded in pure bending with an **elastic–perfectly-plastic** material.
>
> The linear run takes 4.4 s of CPU; the nonlinear run takes 13.3 s (about 3×). The displacements are **not equal**, and the axial plastic strain grows sharply once the section yields: a hinge forms. The same physics appears in a folding-wingtip hinge designed to relieve gust loads.

> [!example] Limit-cycle oscillation (L11)
> Linear flutter analysis gives a single **flutter speed**. With structural nonlinearity (e.g. tiltrotor whirl flutter) a **limit-cycle branch** appears **about 20% below** the linear flutter speed. This shrinks the flight envelope and causes early fatigue. Linear analysis alone is unconservative here.

## 2. Sources of nonlinearity (L11)
| Source | Physical origin | Mathematical origin | Aerospace examples |
|---|---|---|---|
| **Geometric** | the geometry change during deformation enters the strain–displacement and equilibrium equations | $\{\varepsilon\} = [B(\{d\})]\{d\}$ | large wing-tip deflection (B787-class wings); a fishing rod under a big fish (linear for a small load, quadratic or cubic stiffening for a large one); cables and inflatable membranes; **follower forces**, where aerodynamic pressure stays normal to the deforming skin |
| **Material** | the response depends on the current deformation and its history | nonlinear $\sigma(\varepsilon)$; history and rate dependence | plasticity (time-independent), **creep** (time-dependent, hot turbine blades), **viscoelastic** damping patches (frequency- and temperature-dependent), rubbers and functional materials; signs include necking, local yielding, permanent set, shear bands, near-melting temperatures |
| **Force BC** | applied loads depend on the deformation | tractions and body forces are functions of $\{d\}$ | aerodynamic and hydrostatic pressure; twist changing the angle of attack changes the load |
| **Displacement BC / contact** | constraints depend on the deformation | gaps open and close; stick–slip | bolted and clamped joints with micro-slip, **friction dampers** in turbines (under-platform, ring, mid-span), impact, blade–casing rubs, crack faces |

Contact nonlinearity can exist while both bodies remain perfectly linear-elastic: all of it comes from the contact law (e.g. the Coulomb friction jump).

**Aero-engine case study (lecturer's research)**:
- **material**: composite fan blades and viscoelastic damping patches;
- **boundary**: friction dampers and bolted joints;
- **geometric**: large deformation of big fan blades at high speed, where modes interact (bending picks up extension), risking tip rubs.

## 3. Solving nonlinear equations (L11)
**Model problem**: a spring with $k = k_0+k_N(u)$ under load $P$. Find $u$ from $(k_0+k_N(u))\,u = P$.
- $k_N>0$ is **hardening**; $k_N<0$ is **softening**.

**Direct substitution** (secant stiffness):
1. Start with $k_N = 0$: $u_1 = k_0^{-1}P_A$.
2. Update the stiffness, $k = k_0+k_N(u_1)$.
3. Iterate $u_{i+1} = \left(k_0+k_{N}(u_i)\right)^{-1}P_A$ until $|u_{i+1}-u_i|$ is small.

It is simple, but converges linearly (slowly), and can fail for strongly nonlinear problems. **Relaxation** (as in SOR) can help.

**Newton–Raphson** (tangent stiffness). Define the residual $R(u) = k(u)\,u-P$ and the tangent $K_T = dR/du$:

$$
u_{i+1} = u_i-\frac{R(u_i)}{K_T(u_i)}\qquad\left(\text{matrix form: }[K_T]\{\Delta d\} = \{F\}-\{F_{int}(\{d\})\}\right)
$$

It converges **quadratically**: the number of correct digits roughly doubles each iteration. Each iteration needs a new tangent matrix and a factorisation.

**Variants**:
- **modified NR** reuses the old tangent to save factorisations, at the price of slower convergence;
- **incremental** loading applies the load in steps, each converged, to follow a path;
- **quasi-Newton** (e.g. inverse Broyden) approximates the tangent update.

All of these are optimisation-type methods.

> [!example] Softening spring, $k = 100-50u$, $P_A = 40$
> The exact solution is $u = 0.552786$.
>
> | Iteration | 1 | 2 | 3 | 4 | 5 |
> |---|---|---|---|---|---|
> | Direct substitution | 0.4000 | 0.5000 | 0.5333 | 0.5455 | 0.5500 |
> | Newton–Raphson | 0.4000 | 0.5333 | 0.552381 | 0.5527862 | 0.552786405 |
>
> The first step is identical, because $K_T(0) = k(0) = 100$. After that NR reaches machine precision in 5 iterations, while direct substitution is still at $3\times10^{-3}$ error. Details in [[Direct Substitution and Newton-Raphson]].

![[dam_nonlinear_solvers.png|780]]

**In ANSYS**:
- switch on large-deflection effects (`NLGEOM,ON`);
- set **Solution Controls**: substeps and load increments, the NR option (`NROPT`), convergence criteria (`CNVTOL`), line search;
- plot the convergence history to diagnose a stalled solve.

## Links
- Parent: [[SESA2029 Digital Aerospace Methods Hub]] · Previous: [[SESA2029 B8 - Modal Analysis]] · Next: [[SESA2029 B10 - FE Verification, Validation and Model Updating]]
- Iterative solution of *linear* systems (the CFD side): [[Jacobi, Gauss-Seidel and SOR Iteration]]
- Flutter and aeroelasticity: SESA3047-level topics; SPO/phugoid eigenvalues in [[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid]]

## Sources
- FEA Lecture 11, `02 - Sources/FEM Lectures/Lecture_11_Nonlinear_FEA_final(1).pdf` (plastic hinge after ANSYS verification manual VM24; LCO from McGurk & Yuan, IFASD 2022); transcript `FEA.txt`
- Spring example computed in Python (`scripts/make_figures.py`)
