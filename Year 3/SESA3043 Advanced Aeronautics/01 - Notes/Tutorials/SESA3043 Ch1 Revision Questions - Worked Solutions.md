---
title: "SESA3043 Ch1 Revision Questions - Worked Solutions"
module: "SESA3043 Advanced Aeronautics"
type: tutorial
stream: "Chapter 1: Conservation Laws"
tags: [sesa3043, tutorial-solutions, revision-questions, conservation-laws, potential-flow, boundary-layer]
sheet: "Chapter 1 Revision Questions"
theory_notes: ["[[SESA3043 1.1 - Mathematical Tools and Flow Description]]", "[[SESA3043 1.2 - Conservation Laws and Governing Equations]]", "[[SESA3043 1.3 - Potential-Flow Review]]", "[[SESA3043 1.3 - Complex Potential, Wedge Flows and Unsteady Bernoulli]]", "[[SESA3043 1.4 - Two-Dimensional Incompressible Boundary Layers]]"]
status: complete
sources: ["03 - Exams & Past Papers/Ch1_Revision_Questions.pdf"]
---

# SESA3043 Ch1 Revision Questions - Worked Solutions

> [!abstract] Sheet info
> Blackboard revision questions for Chapter 1 (updated 10 Sep 2026). In the 1 Oct lecture: *"have a look at revision questions… on blackboard for chapter one and let us know either by email or in discussion board which question… you would like us to go to"* in Friday's tutorial (L4, ll. 9–16). Short-answer questions are answered here in full; derivation questions link to the full derivation in the topic notes, with the key steps summarised.

> [!info] The 2 Oct tutorial (`02 October 2026 at 15_51_44.txt`)
> The only requests were **§1.3 Q2 and Q3** (ll. 3–5). The lecturer set Q2 up and left the class about 10 minutes to try it (ll. 11–36):
> - superpose the complex potentials of a **uniform flow with $\alpha=0$** and a **general doublet with $\nu=\pi$** (source placed upstream of the sink);
> - differentiate with respect to $z$ and split into real and imaginary parts to get $u$ and $v$;
> - the last part asks for $C_p(\theta)$, which should reproduce the real-plane result, $C_p=1-4\sin^2\theta$.
>
> The rest of the recording is inaudible group work. Solutions to all Chapter 1 revision questions were to be released after the tutorial (ll. 6–8). Our worked answers are below.

## 1.1 Introduction

**Q1. Specific quantities** (per unit mass, see [[Fluid Flow Rate, Flux and Specific Quantity]]).

| Quantity | Per unit volume | Specific (per unit mass) |
|---|---|---|
| mass | $\rho$ | $1$ |
| momentum | $\rho\mathbf u$ | $\mathbf u$ |
| internal energy | $\rho e$ | $e$ |
| kinetic energy | $\tfrac12\rho|\mathbf u|^2$ | $\tfrac12|\mathbf u|^2$ |
| total energy | $\rho E_T$ | $E_T=e+\tfrac12|\mathbf u|^2$ (+ $gz$ if included) |
| enthalpy | $\rho h$ | $h=e+p/\rho$ |
| volume | $1$ | $v=1/\rho$ (specific volume) |

A specific quantity is what you integrate against $\rho\,\mathrm dV$: any extensive property $B=\int\rho b\,\mathrm dV$ has specific value $b$. That is the form used in the [[Reynolds Transport Theorem]].

**Q2. Unit of shear stress.** Force per area: N m⁻² = Pa = kg m⁻¹ s⁻². (From $\tau=\mu\,\partial u/\partial y$: Pa s × s⁻¹ = Pa.)

**Q3. Scalars and vectors.**

- Scalars: $p$, $\rho$, $T$, $e$, $h$, $s$, $\mu$, $k$, $\phi$, $\psi$ (2-D).
- Vectors: $\mathbf u$, $\boldsymbol\omega$, $\mathbf g$, heat flux $\mathbf q$, force, momentum.
- Second-order tensors: stress $\tau_{ij}$, strain rate $S_{ij}$, velocity gradient $\partial u_i/\partial x_j$.

**Pressure is a scalar.** At a point it has the same value on a surface of any orientation (isotropic). The *force* it produces on a surface is a vector, $-p\,\mathbf n\,\mathrm dA$, whose direction comes from the surface normal, not from the pressure. In tensor terms, the pressure contributes $-p\,\delta_{ij}$ to the stress tensor ([[Newtonian Stress Tensor]]).

**Q4. Physical meaning.**

- (a) $\boldsymbol\Omega=\nabla\times\mathbf u$ is the **vorticity**: twice the local angular velocity of a fluid element about its own axis. Zero in potential flow. Irrotational does not mean "not going round": a parcel in a point vortex circulates but does not spin (L4, ll. 66–70; [[SESA3043 1.1 - Mathematical Tools and Flow Description#Curl and vorticity|1.1]]).
- (b) $\mathbf u\times\boldsymbol\omega$ is the **Lamb vector** (vortex force per unit mass). It is the rotational part of the convective acceleration: $(\mathbf u\cdot\nabla)\mathbf u=\nabla\left(\tfrac12|\mathbf u|^2\right)-\mathbf u\times\boldsymbol\omega$. It is perpendicular to both the velocity and the vorticity, and it vanishes in irrotational flow. That is why Bernoulli holds everywhere there, not just along streamlines ([[SESA3043 1.3 - Complex Potential, Wedge Flows and Unsteady Bernoulli#8. The unsteady Bernoulli equation|1.3 §8]]).

**Q5. Direction of a cross product.** Right-hand rule: curl the fingers of the right hand from the first vector to the second through the smaller angle; the thumb gives the direction. The result is perpendicular to both, with magnitude $|\mathbf a||\mathbf b|\sin\alpha$.

**Q6.** No: $\mathbf u\times\boldsymbol\omega=-\boldsymbol\omega\times\mathbf u$. The cross product is anti-commutative.

**Q7. The Laplace operator is linear:** $\nabla^2(a\phi_1+b\phi_2)=a\nabla^2\phi_1+b\nabla^2\phi_2$ for constants $a,b$, because differentiation is linear. Hence the principle of superposition for potential flow (L4, ll. 88–95). (The *Navier–Stokes* equations are nonlinear because of $(\mathbf u\cdot\nabla)\mathbf u$, so solutions cannot be superposed.)

**Q8 (extended).** Yes. $\dfrac{\partial u_i}{\partial x_i}=\dfrac{\partial u_j}{\partial x_j}=\dfrac{\partial u_1}{\partial x_1}+\dfrac{\partial u_2}{\partial x_2}+\dfrac{\partial u_3}{\partial x_3}=\nabla\cdot\mathbf u$. A repeated (dummy) index is summed and can be renamed freely; only free indices must match on both sides ([[SESA3043 1.1 - Mathematical Tools and Flow Description#3. Einstein summation and free indices|1.1 §3]]).

## 1.2 Governing equations

**Q1. Material derivative.** $\dfrac{\mathrm D}{\mathrm Dt}=\dfrac{\partial}{\partial t}+\mathbf u\cdot\nabla$: the rate of change following a fluid particle equals the local (Eulerian, fixed-point) rate plus the convective rate from moving into a region with different values. → [[SESA3043 1.1 - Mathematical Tools and Flow Description#6. Eulerian and Lagrangian descriptions|1.1 §6]]

**Q2. Net x-momentum flow rate into the CV.** For a cube $\delta x\,\delta y\,\delta z$, the $x$-momentum carried through the faces normal to $x_j$ is $\rho u u_j$ per unit area. Taylor-expanding to the opposite faces and summing over the three pairs gives a net inflow of $-\dfrac{\partial(\rho uu_j)}{\partial x_j}\delta x\,\delta y\,\delta z$. → [[SESA3043 1.2 - Conservation Laws and Governing Equations#Where each local momentum term comes from|1.2 §3]]

**Q3. Conservative → non-conservative.** Expand $\dfrac{\partial(\rho u_i)}{\partial t}+\dfrac{\partial(\rho u_iu_j)}{\partial x_j}=u_i\left[\dfrac{\partial\rho}{\partial t}+\dfrac{\partial(\rho u_j)}{\partial x_j}\right]+\rho\left[\dfrac{\partial u_i}{\partial t}+u_j\dfrac{\partial u_i}{\partial x_j}\right]$. The first bracket is zero by continuity, leaving $\rho\,\mathrm Du_i/\mathrm Dt$. → [[SESA3043 1.2 - Conservation Laws and Governing Equations#Material form|1.2 §3]]

**Q4. Viscous term for incompressible flow** (derivation). Newtonian stress with $\nabla\cdot\mathbf u=0$ (the bulk term drops):

$$
\tau_{ij}=\mu\left(\frac{\partial u_i}{\partial x_j}+\frac{\partial u_j}{\partial x_i}\right).
$$

Take the divergence (constant $\mu$):

$$
\frac1\rho\frac{\partial\tau_{ij}}{\partial x_j}=\nu\left(\frac{\partial^2u_i}{\partial x_j\partial x_j}+\frac{\partial^2u_j}{\partial x_i\partial x_j}\right)=\nu\frac{\partial^2u_i}{\partial x_j\partial x_j}+\nu\frac{\partial}{\partial x_i}\underbrace{\left(\frac{\partial u_j}{\partial x_j}\right)}_{=0}=\nu\frac{\partial^2u_i}{\partial x_j\partial x_j}.
$$

(Order of differentiation swapped in the second term, allowed for smooth fields.) → [[SESA3043 1.2 - Conservation Laws and Governing Equations#7. Incompressible reduction|1.2 §7]]

**Q5. Meaning of each term** in $\rho\left(\dfrac{\partial u_i}{\partial t}+u_j\dfrac{\partial u_i}{\partial x_j}\right)=\rho f_i-\dfrac{\partial p}{\partial x_i}+\dfrac{\partial\tau_{ij}}{\partial x_j}$:

| Term | Meaning |
|---|---|
| $\rho\,\partial u_i/\partial t$ | local (unsteady) acceleration at a fixed point |
| $\rho u_j\,\partial u_i/\partial x_j$ | convective acceleration: change from moving to a new position |
| $\rho f_i$ | body force per unit volume (gravity) |
| $-\partial p/\partial x_i$ | net pressure force per unit volume (flow is pushed from high to low $p$) |
| $\partial\tau_{ij}/\partial x_j$ | net viscous (shear and normal) stress force per unit volume |

**Q6 (extended).** Energy equation from the first law applied to a CV: the rate of change of total energy equals the heat added (conduction) plus the work done by body, pressure and viscous forces. → [[SESA3043 1.2 - Conservation Laws and Governing Equations#5. Conservation of total energy|1.2 §5]]

## 1.3 Potential flow

- **Q1** Complex potentials of uniform flow, source/sink and point vortex (doublet done in lecture). → [[SESA3043 1.3 - Complex Potential, Wedge Flows and Unsteady Bernoulli#4. Complex potentials of the elementary flows (revision 1.3 Q1)]]
- **Q2** Cylinder from uniform flow + doublet, velocity field and $C_p=1-4\sin^2\theta$. → [[SESA3043 1.3 - Complex Potential, Wedge Flows and Unsteady Bernoulli#6. The cylinder again, in one line (revision 1.3 Q2)]]
- **Q3** Wall velocity $U_e=k(m+1)s^m$ and gradient $mU_e/s$ for wedge flow. → [[SESA3043 1.3 - Complex Potential, Wedge Flows and Unsteady Bernoulli#Velocity and its gradient along the wall (revision 1.3 Q3)]]
- **Q4** (extended) Plot $\phi$ and $\psi$ contours: see the generator function `cylinder_flow_derivation` in `generate_aero_ch1b_figures.py`. → ![[aa_cylinder_flow_derivation.png|500]]
- **Q5** (extended) Lifting cylinder: $\Phi=U(z+R^2/z)-\dfrac{i\Gamma}{2\pi}\ln z$, $\sin\theta_s=\Gamma/4\pi UR$, $L'=\rho U|\Gamma|$. → [[SESA3043 1.3 - Complex Potential, Wedge Flows and Unsteady Bernoulli#Lifting cylinder: uniform flow plus doublet plus point vortex (revision 1.3 Q5)]]

## 1.4 Two-dimensional incompressible boundary layers

All six are answered in [[SESA3043 1.4 - Two-Dimensional Incompressible Boundary Layers]]:

- **Q1** scales; **Q2** order-of-magnitude derivation → [[SESA3043 1.4 - Two-Dimensional Incompressible Boundary Layers#3. Order-of-magnitude analysis, step by step]]
- **Q3** $\partial p/\partial y=0$: pressure imposed by the outer flow → [[SESA3043 1.4 - Two-Dimensional Incompressible Boundary Layers#Step 3: y-momentum (slides 25–31)]]
- **Q4** $-\tfrac1\rho\,\mathrm dp/\mathrm dx=U_e\,\mathrm dU_e/\mathrm dx$ → [[SESA3043 1.4 - Two-Dimensional Incompressible Boundary Layers#Step 4: Bernoulli at the edge (slides 33–37; revision §1.4 Q4)]]
- **Q5** $\delta/L\sim Re^{-1/2}$ → [[SESA3043 1.4 - Two-Dimensional Incompressible Boundary Layers#Step 2: x-momentum, term by term (slides 17–24)]]
- **Q6** parabolic, marching solution → [[SESA3043 1.4 - Two-Dimensional Incompressible Boundary Layers#Why parabolic matters (revision §1.4 Q6)]]

## Links

- Parent: [[SESA3043 Advanced Aeronautics Hub]]
- Chapter 2 sheet: [[SESA3043 Ch2 Revision Questions - Worked Solutions]]
