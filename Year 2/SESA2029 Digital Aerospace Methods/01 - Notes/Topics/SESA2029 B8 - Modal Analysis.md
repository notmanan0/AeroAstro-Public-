---
title: "SESA2029 B8 - Modal Analysis"
module: "SESA2029 Digital Aerospace Methods"
type: topic
stream: "Part B: Finite Element Analysis"
order: 19
tags:
  - sesa2029
  - fea
  - modal-analysis
  - vibration
aliases: ["FE modal analysis", "Natural frequencies", "Eigen analysis"]
date: 2026-09-24
status: complete
parent: ["[[SESA2029 Digital Aerospace Methods Hub]]"]
prerequisites: ["[[SESA2029 B7 - Meshing, Convergence and Mesh Checks]]"]
next_topics: ["[[SESA2029 B9 - Nonlinear FE Analysis]]"]
key_concepts: ["[[Natural Frequencies and Mode Shapes]]", "[[Participation Factor and Effective Mass]]", "[[Damping Ratio and Natural Frequency]]"]
tutorial_sheets: ["[[SESA2029 FEA Worked Examples]]"]
sources: ["02 - Sources/FEM Lectures/Lecture_10_Modal_Analysis_2_final(1).pdf", "02 - Sources/FEM Lectures/FEA.txt"]
---

# SESA2029 B8 - Modal Analysis

> [!abstract] Summary
> Aerospace structures feel time-varying loads: gusts, engine and rotor excitation, turbulence, separated flow. If an excitation matches a **natural frequency**, the response is amplified by **resonance**. That drives fatigue, noise, flutter and, at worst, failure (the Tacoma Narrows bridge).
>
> **Modal analysis** solves the undamped free-vibration eigenproblem
>
> $$([K]-\omega_i^2[M])\{\phi\}_i = 0$$
>
> The **eigenvalues** $\omega_i^2$ give the natural frequencies $f_i = \omega_i/2\pi$, and the **eigenvectors** $\{\phi\}_i$ are the **mode shapes**. Mode shapes have no physical amplitude: they are usually mass-normalised, and any "stresses" from them are only relative.
>
> - Frequencies scale with $\sqrt{K/M}$ and rise with stiffer boundary conditions.
> - **Participation factors** $\gamma_i = \{\phi\}_i^T[M]\{D\}$ and **effective masses** $\gamma_i^2$ show which modes a base excitation excites. They also tell you whether enough modes have been extracted: aim for > 90% of the total mass.

## Key Concepts
- [[Natural Frequencies and Mode Shapes]] · [[Participation Factor and Effective Mass]] · [[Damping Ratio and Natural Frequency]] · [[Characteristic Equation and Eigenvalues]]

---

## 1. Why dynamics matters (L10)
Examples:
- engine–wing interaction;
- **tail flutter**, a self-excited aeroelastic instability: above the flutter speed the net damping becomes negative and oscillations grow until failure;
- flexible wings showing limit-cycle oscillations;
- fan blades and rotors, where each shaft speed is an excitation frequency to avoid;
- spacecraft (launch random vibration, deployment, attitude manoeuvres);
- rotorcraft.

**Vibration** is oscillation about an equilibrium. Typical procedure: static analysis first, then dynamic loads on top. Lightweight (composite) structures are especially sensitive, because low mass means **dense, low natural-frequency spectra**. Closely spaced modes (e.g. bending and torsion) can **coalesce** as speed rises, which is the classic flutter mechanism.

Vibrations can also be *used*, for example energy harvesting at a tuned resonance.

## 2. Formulation (L10)
Assume a **linear elastic** structure (constant $[M]$ and $[K]$) with **no loads**, undergoing free, undamped vibration:

$$
[M]\{\ddot u\}+[K]\{u\} = 0
$$

Assume harmonic motion, $\{u\} = \{\phi\}_i\sin(\omega_it+\theta_i)$, with amplitude, angular frequency and phase. Then $\{\ddot u\} = -\omega_i^2\{\phi\}_i\sin(\omega_it+\theta_i)$, and substituting:

$$
\boxed{\left([K]-\omega_i^2[M]\right)\{\phi\}_i = 0}\qquad\Rightarrow\qquad\det([K]-\omega^2[M]) = 0
$$

- **Eigenvalues** $\omega_i^2$: natural circular frequencies $\omega_i$ in rad/s, with $f_i = \omega_i/2\pi$ in Hz and period $T_i = 1/f_i$.
- **Eigenvectors** $\{\phi\}_i$: the **mode shape**, the deformed pattern at frequency $f_i$.
- An $n$-DOF model has $n$ modes. Usually only the first few (default 6) matter for the dynamic response.

**Normalisation**. The amplitude is arbitrary, so it has to be fixed somehow:
- to the **mass matrix**, $\{\phi\}_i^T[M]\{\phi\}_i = 1$ (with orthogonality $\{\phi\}_i^T[M]\{\phi\}_j = 0$ for $i\neq j$). **ANSYS reports mass-normalised shapes.**
- or to **unity**: largest component = 1.

What matters is the *shape*: first bending, second bending, first torsion. Not the numbers.

**Estimate for the first mode**: $\omega_0\approx\sqrt{k/m}$ (SDOF), $f_0 = \omega_0/2\pi$.

**SDOF recap**: $m\ddot x+c\dot x+kx = f(t)$, i.e. $\ddot x+2\zeta\omega_0\dot x+\omega_0^2x = 0$ with $\omega_0 = \sqrt{k/m}$ and $\zeta = c/(2m\omega_0)$. Underdamped roots are $\lambda = -\zeta\omega_0\pm i\omega_0\sqrt{1-\zeta^2}$, the damped natural frequency being $\omega_d = \omega_0\sqrt{1-\zeta^2}$. The pair $(\omega_0,\zeta)$ is the **modal model**. See [[Damping Ratio and Natural Frequency]].

## 3. What controls the modes (L10)
- **Stiffness** (geometry + material): stiffer means higher frequencies.
- **Mass**: more mass means lower frequencies. Only the **ratio $K/M$** matters.
- **Boundary conditions**: clamped supports restrain more than simple supports, so the structure is stiffer and its frequencies are higher.

> [!example] Highly flexible wing (research example, L10)
> An aluminium-plate spar with a 3D-printed aerofoil shell was mounted for a ground vibration test. The FE predictions were:
>
> | Mode | Frequency |
> |---|---|
> | 1st bending | 4.2 Hz |
> | 2nd bending | 28.5 Hz |
> | 1st torsion | 40.7 Hz |
> | 3rd bending | 82.3 Hz |
>
> For flutter, the **second bending and first torsion** matter. Aerodynamic stiffness and damping pull them together as airspeed rises, until the total damping goes negative.

**Experimental validation**:
- **Hammer test**: impact excitation at many points; the response spectra (FRFs) show peaks at the resonances. Combining the points gives the experimental mode shapes.
- **Shaker test**: a signal generator drives an electrodynamic shaker through a frequency sweep, and the structure resonates as each mode is reached.

Compare frequencies (typically within 5%) and mode shapes (**MAC** > about 0.8), and update the model if they differ ([[Model Updating]]).

## 4. Participation factor and effective mass (L10)

$$
\gamma_i = \{\phi\}_i^T[M]\{D\},\qquad M_{\mathrm{eff},i} = \frac{\gamma_i^2}{\{\phi\}_i^T[M]\{\phi\}_i} = \gamma_i^2\quad(\text{mass-normalised})
$$

$\{D\}$ is a unit displacement spectrum in one global direction (translation in $x$, $y$ or $z$, or rotation about an axis).
- A **large $\gamma_i$** in a direction means that mode is readily excited by forces or **base motion** in that direction.
- $\sum_iM_{\mathrm{eff},i}$ → total mass as all modes are included. **Stop extracting modes when the cumulative effective mass exceeds about 90% of the total.**

**Uses**:
- **Spacecraft**: identify the modes most excited by launch or base loads, then change geometry, BCs or mass distribution to reduce their participation and improve stability.
- **Aero-engines**: identify modes that radiate noise and reduce their participation to make the engine quieter.

> [!example] 2-DOF spring–mass (L10)
> $m_1 = 2$ kg is joined to ground by $k_1 = 1000$ N/m, $m_2 = 1$ kg is joined to ground by $k_2 = 2000$ N/m, and $k_3 = 3000$ N/m couples the two masses:
>
> $$[M] = \begin{bmatrix}2&0\\0&1\end{bmatrix},\quad[K] = \begin{bmatrix}k_1+k_3&-k_3\\-k_3&k_2+k_3\end{bmatrix} = \begin{bmatrix}4000&-3000\\-3000&5000\end{bmatrix}$$
>
> - Eigen-solution: $f_1 = 4.78$ Hz with $\{\phi\}_1 = \{0.6280,\ 0.4597\}$ (**in phase**), and $f_2 = 12.43$ Hz with $\{\phi\}_2 = \{-0.3251,\ 0.8881\}$ (**out of phase**).
> - Participation: $\gamma = \Phi^TMD = \{1.7157,\ -0.2379\}$.
> - Effective mass: $M_{\mathrm{eff}} = \{2.9436,\ 0.0566\}$ kg, summing to **3 kg**, the total mass (only two modes exist).
>
> Mode 1 carries 98% of the mass, so it dominates base-excited response. Full working in [[SESA2029 FEA Worked Examples]].

![[dam_modal_2dof.png|600]]

## 5. Modal analysis in ANSYS (L10)
- Analysis type **Modal** (`ANTYPE,MODAL`). Extraction by Block Lanczos (`MODOPT,LANB,n`).
- Number of modes: the first $N$ (default 6), or the first $N$ in a frequency range. Expand the modes to get shapes and element results (`MXPAND`).
- **Density must be defined**. With $\rho = 0$, $[M] = 0$ and there are no frequencies. This is the classic "I can't see any mode shapes" error.
- **Output caveats**:
  - mode-shape displacements are not real deflections;
  - modal "stresses" only show the **relative** distribution, not real values;
  - none of it predicts the response to a specific load. That needs harmonic, transient or spectrum analysis, built on these modes (they also feed reduced-order models).

APDL recipe: [[SESA2029 C4 - APDL Workflow - Shell Wing Static and Modal (SHELL181 and SHELL281)]].

## Links
- Parent: [[SESA2029 Digital Aerospace Methods Hub]] · Previous: [[SESA2029 B7 - Meshing, Convergence and Mesh Checks]] · Next: [[SESA2029 B9 - Nonlinear FE Analysis]]
- Eigenvalue problems and modes in flight dynamics: [[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid]] · [[Frequency Response Function]]
- Free-free modal check for model verification: [[FE Model Verification Checks]]

## Sources
- FEA Lecture 10, `02 - Sources/FEM Lectures/Lecture_10_Modal_Analysis_2_final(1).pdf`; transcript `FEA.txt`
- 2-DOF example re-solved with SciPy `eigh`
