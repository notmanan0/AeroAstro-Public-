---
title: "SESA2029 B3 - Principle of Minimum Total Potential Energy"
module: "SESA2029 Digital Aerospace Methods"
type: topic
stream: "Part B: Finite Element Analysis"
order: 14
tags:
  - sesa2029
  - fea
  - energy-methods
aliases: ["PMPE", "Minimum potential energy", "Weak form"]
date: 2026-09-24
status: complete
parent: ["[[SESA2029 Digital Aerospace Methods Hub]]"]
prerequisites: ["[[SESA2029 B1 - Introduction to FEA and the Matrix Displacement Method]]"]
next_topics: ["[[SESA2029 B4 - Rayleigh-Ritz Method and Shape Functions]]"]
key_concepts: ["[[Principle of Minimum Total Potential Energy]]", "[[Strong and Weak Forms]]", "[[Stress Concentration Factor and Factor of Safety]]"]
tutorial_sheets: ["[[SESA2029 FEA Worked Examples]]"]
sources: ["02 - Sources/FEM Lectures/Lecture_5_Mimimum_Potnetial_Energy.pdf", "02 - Sources/FEM Lectures/FEA.txt"]
---

# SESA2029 B3 - Principle of Minimum Total Potential Energy

> [!abstract] Summary
> The **strong form** of equilibrium (e.g. Navier–Cauchy PDEs in displacement) needs continuous second derivatives everywhere, which is impossible to satisfy for real geometry. **Weak (integral) forms** only need equilibrium *on average* and only first derivatives.
>
> **Weighted-residual (Galerkin)** and **energy** methods are both variational. The **principle of minimum total potential energy (PMPE)** says that, of all displacement fields satisfying the displacement BCs, the equilibrium one minimises
>
> $$\Pi = U+V$$
>
> where $U$ is the strain energy and $V = -W$ is the work potential of the loads. Setting $\partial\Pi/\partial d_i = 0$ for every DOF gives $\{F\} = [K]\{d\}$: the same element matrices as the MDM, by a route that generalises to any element.

## Key Concepts
- [[Principle of Minimum Total Potential Energy]] · [[Strong and Weak Forms]] · [[Stress Concentration Factor and Factor of Safety]]

---

## 1. Strong vs weak form (L5)
- Real physics is governed by ODEs/PDEs with **boundary conditions** (and initial conditions for dynamics). Structural equilibrium is written first in derivatives of stress, then (via the strain–displacement and stress–strain laws) as **second-order** PDEs in displacement. These are the Navier–Cauchy equations.
- **Strong form**: the PDE must hold at *every* point, which needs $\partial^2u/\partial x^2$ to exist and be continuous everywhere. That is usually impossible except for the simplest configurations.
- **Weak form**: restate equilibrium as **integral** equations that hold only **in an averaged (weighted) sense**.
  - Weighted-residual methods such as **Galerkin** multiply the residual by weight functions and integrate to zero.
  - An approximate **trial displacement** is assumed, and the error is minimised in a weighted-average sense.
- **Finite element approximation of the weak form**:
  - interpolate the displacement between a finite number of nodes using shape functions;
  - this turns infinitely many unknowns into a finite set of algebraic equations.

  Accuracy drops slightly (strong → weak → FE), but speed and generality increase enormously.

The weighted-residual and minimum potential energy methods both belong to the **variational** family. **Variational calculus** studies small variations $\delta$ of **functionals** (functions of functions) to find stationary values. See [[Strong and Weak Forms]].

## 2. Why use energy (L5)
The exact (strong-form) solution also **minimises the total potential energy**. The benefits:
- far less demanding than the strong form;
- **only first derivatives** need to be finite;
- **force BCs are satisfied automatically**: they enter through the work term;
- the admissible displacement only needs to satisfy the **displacement** BCs.

## 3. Work, strain energy and virtual work (L5)
For a bar with force $F = ku$:
- work done in extending it by $du$ is $dW = F\,du = ku\,du$;
- total work is $W = \int_0^uku\,du = \tfrac12ku^2$;
- linear elasticity is **conservative**, so this is stored as **strain energy** $U = \tfrac12ku^2$.

Per unit volume ($V = AL$), the **strain energy density** is

$$
\bar U = \tfrac12\sigma\varepsilon
$$

the area under the stress–strain line. For a general body, $U = \int_V\tfrac12\{\sigma\}^T\{\varepsilon\}\,dV$.

**Virtual work.** Perturb the equilibrium position by a small **virtual displacement** $\delta u$. The load does virtual work $\delta W = F\,\delta u$, with the force effectively constant during the tiny displacement. In a conservative system this is stored as strain energy: $\delta U = \delta W$.

Treat the work done by the loads as a **loss of potential**, $\delta V = -\delta W$. Then

$$
\delta U+\delta V = \delta(U+V) = 0,\qquad\Pi = U+V
$$

$\Pi$, the **total potential energy**, is a functional of the displacement field.

## 4. The principle (L5)
> [!note] PMPE
> Of all the deformations an elastic body can take that satisfy its displacement boundary conditions, the **equilibrium** one makes the total potential energy $\Pi = U+V$ **stationary**. For stable equilibrium this stationary point is a **minimum**.
>
> $$\delta\Pi = \delta U+\delta V = 0$$

**1-DOF spring**:

$$
\Pi(u) = \tfrac12ku^2-Fu,\qquad\frac{d\Pi}{du} = ku-F = 0\;\Rightarrow\;F = ku
$$

![[dam_total_potential_energy.png|560]]

**$n$ DOF.** $\Pi = \Pi(d_1,\dots,d_n)$. Minimise with respect to *each* DOF:

$$
\frac{\partial\Pi}{\partial d_i} = 0,\quad i = 1,\dots,n\;\;\Rightarrow\;\;n\text{ linear equations}\;\;\Rightarrow\;\;\{F\} = [K]\{d\}
$$

This is an alternative, and much more general, way to obtain element equilibrium equations.

## 5. The 2-node bar by PMPE (L5)
Here $k = AE/L$ and the extension is $\Delta L = u_{xj}-u_{xi}$.

$$
U = \tfrac12k(u_{xj}-u_{xi})^2 = \tfrac12k\left(u_{xj}^2-2u_{xj}u_{xi}+u_{xi}^2\right),\qquad V = -F_{xi}u_{xi}-F_{xj}u_{xj}
$$

$$
\frac{\partial\Pi}{\partial u_{xi}} = \tfrac12k(2u_{xi}-2u_{xj})-F_{xi} = 0,\qquad\frac{\partial\Pi}{\partial u_{xj}} = \tfrac12k(2u_{xj}-2u_{xi})-F_{xj} = 0
$$

$$
\begin{Bmatrix}F_{xi}\\F_{xj}\end{Bmatrix} = \frac{AE}{L}\begin{bmatrix}1&-1\\-1&1\end{bmatrix}\begin{Bmatrix}u_{xi}\\u_{xj}\end{Bmatrix}
$$

This is identical to the MDM result. This derivation is a stated exam skill; see [[SESA2029 FEA Worked Examples]] for the step-by-step version.

## 6. Stress concentration factor (L5)
Local discontinuities (holes, steps, sharp corners) amplify stress. The amplification depends on:
- the global structural configuration;
- the discontinuity's location;
- its geometry and size.

The more abrupt the change, the larger the amplification. Fillets reduce it; uniaxial $F/A$ theory cannot predict it.

$$
K_t = \frac{\sigma_{max}}{\sigma_{bulk}}
$$

$\sigma_{bulk}$ (nominal) is the stress **far from** the raiser. $K_t$ can come from FEA, experiment or elasticity solutions.

**Elliptical hole in an infinite plate** (semi-axis $a$ perpendicular to the load, $b$ parallel):

$$
K_t = 1+\frac{2a}{b}
$$

A circle ($a = b$) gives $K_t = 3$. With $a = 2b$, $K_t = 5$. An FE model with $\sigma_{bulk} = 100$ MPa gave $\sigma_{max} = 503.7$ MPa, so $K_t = 5.037$: an excellent check. The analytic value assumes an infinite plate; a hole near an edge or a finite width needs FE. See [[Stress Concentration Factor and Factor of Safety]] and the Kirsch distribution:

![[dam_kirsch_hole_stress.png|740]]

> [!warning] Choosing $\sigma_{bulk}$
> Use the **nominal far-field stress**. That is the applied traction, or the value read at nodes on the loaded edge well away from the hole. By force equilibrium, a plate pulled by 120 MPa has a bulk stress of 120 MPa. It is **not** the minimum stress anywhere in the plate: the low-stress "shadow" beside a hole would badly inflate $K_t$.

**Factor of safety against yield**: $FoS = \sigma_{yield}/\sigma_{max}$. Design codes typically require 1.5–2.0. If it is too low, reduce the raiser, thicken the part or reduce the load.

## Links
- Parent: [[SESA2029 Digital Aerospace Methods Hub]] · Previous: [[SESA2029 B2 - Linear Elastic FE Analysis - Procedure, Boundary Conditions and Yield]] · Next: [[SESA2029 B4 - Rayleigh-Ritz Method and Shape Functions]]
- APDL plate-with-hole workflow: [[SESA2029 C3 - APDL Workflow - Plate with a Hole (PLANE182 and PLANE183)]]
- Aeroelastic equations of motion (why weak forms matter for dynamics): [[SESA2029 B8 - Modal Analysis]]

## Sources
- FEA Lecture 5, `02 - Sources/FEM Lectures/Lecture_5_Mimimum_Potnetial_Energy.pdf`; transcript `FEA.txt`
- Kirsch (1898) solution for a circular hole; Pilkey, *Peterson's Stress Concentration Factors*
