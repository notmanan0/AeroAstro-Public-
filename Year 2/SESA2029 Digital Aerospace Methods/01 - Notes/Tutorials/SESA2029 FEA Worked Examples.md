---
title: "SESA2029 FEA Worked Examples"
module: "SESA2029 Digital Aerospace Methods"
type: tutorial
stream: "Part B: Finite Element Analysis"
tags: [sesa2029, tutorial-solutions, fea]
sheet: "Lecture worked examples and exam-style practice (FEA)"
theory_notes: ["[[SESA2029 B1 - Introduction to FEA and the Matrix Displacement Method]]", "[[SESA2029 B2 - Linear Elastic FE Analysis - Procedure, Boundary Conditions and Yield]]", "[[SESA2029 B3 - Principle of Minimum Total Potential Energy]]", "[[SESA2029 B4 - Rayleigh-Ritz Method and Shape Functions]]", "[[SESA2029 B5 - Euler-Bernoulli Beam Element]]", "[[SESA2029 B8 - Modal Analysis]]", "[[SESA2029 B9 - Nonlinear FE Analysis]]"]
key_concepts: ["[[Matrix Displacement Method]]", "[[Principle of Minimum Total Potential Energy]]", "[[Shape Functions]]", "[[Euler-Bernoulli Beam Element]]", "[[Participation Factor and Effective Mass]]", "[[Direct Substitution and Newton-Raphson]]"]
status: complete
sources: ["02 - Sources/FEM Lectures/", "02 - Sources/FEM Lectures/FEA.txt"]
---

# SESA2029 FEA Worked Examples

> [!abstract] Sheet Info
> These are exam-style problems taken from the lecture examples, including the Example Sheet 1 and 2 questions worked in lectures. Every number was checked in Python. The element stiffness matrices are **given** in the exam; the marks are for assembly, boundary conditions, algebra and interpretation.

## Theory Links
- Theory notes: [[SESA2029 B1 - Introduction to FEA and the Matrix Displacement Method]] · [[SESA2029 B3 - Principle of Minimum Total Potential Energy]] · [[SESA2029 B4 - Rayleigh-Ritz Method and Shape Functions]] · [[SESA2029 B5 - Euler-Bernoulli Beam Element]] · [[SESA2029 B8 - Modal Analysis]]
- Key concepts: [[Matrix Displacement Method]] · [[Global Stiffness Matrix Assembly]] · [[Boundary Conditions and Rigid Body Modes]]

## Q1: Two-bar structure clamped at both ends (Example Sheet 1 type)

*Two collinear bars of length $L$ and modulus $E$: bar 1 has area $2A$, bar 2 has area $A$. The outer ends are clamped and load $P$ acts at the junction. (i) Discretise into two 2-node bar elements, write the element matrices and assemble $\{F\} = [K]\{d\}$. (ii) State and apply the BCs. (iii) Find the junction displacement. (iv) Find the reactions and bar stresses.*

### Solution
(i) Sketch nodes 1–2–3 with one DOF each (axial $u$). The element stiffnesses are $k_1 = 2AE/L$ and $k_2 = AE/L$:

$$
\begin{Bmatrix}F_1\\F_2\\F_3\end{Bmatrix} = \begin{bmatrix}k_1&-k_1&0\\-k_1&k_1+k_2&-k_2\\0&-k_2&k_2\end{bmatrix}\begin{Bmatrix}u_1\\u_2\\u_3\end{Bmatrix} = \frac{AE}{L}\begin{bmatrix}2&-2&0\\-2&3&-1\\0&-1&1\end{bmatrix}\begin{Bmatrix}u_1\\u_2\\u_3\end{Bmatrix}
$$

The "3" is $2+1$: both elements share DOF 2.

(ii) $u_1 = u_3 = 0$ (clamps) and $F_2 = P$. $F_1 = R_1$ and $F_3 = R_3$ are unknown reactions. Strike rows and columns 1 and 3.

(iii) $P = \dfrac{3AE}{L}u_2\;\Rightarrow\;\boxed{u_2 = \dfrac{PL}{3AE}}$

(iv) Back-substitute into rows 1 and 3:
- $R_1 = -\dfrac{2AE}{L}u_2 = -\tfrac23P$;
- $R_3 = -\dfrac{AE}{L}u_2 = -\tfrac13P$.

The sum is $-P$ ✓ (equilibrium). The stiffer bar takes $\tfrac23$ of the load.

Stresses:
- bar 1: $\sigma_1 = E(u_2-u_1)/L = P/3A$ (tension);
- bar 2: $\sigma_2 = E(u_3-u_2)/L = -P/3A$ (compression).

## Q2: Springs in series with a tip load

*Bar 1 ($k_1$) is fixed at node 1; bar 2 ($k_2$) runs from node 2 to node 3; force $F$ acts at node 3. Find $u_2$, $u_3$ and the reaction.*

### Solution
Strike row and column 1:

$$
\begin{Bmatrix}0\\F\end{Bmatrix} = \begin{bmatrix}k_1+k_2&-k_2\\-k_2&k_2\end{bmatrix}\begin{Bmatrix}u_2\\u_3\end{Bmatrix}
$$

Adding the rows: $k_1u_2 = F$, so $u_2 = F/k_1$ and $u_3 = F/k_1+F/k_2$. The reaction is $R_1 = -k_1u_2 = -F$.

## Q3: Bar equilibrium by the principle of minimum potential energy (Example Sheet 2 Q1)

*Using PMPE (not the MDM), show that a 2-node bar satisfies $\begin{Bmatrix}F_{xi}\\F_{xj}\end{Bmatrix} = \dfrac{AE}{L}\begin{bmatrix}1&-1\\-1&1\end{bmatrix}\begin{Bmatrix}u_{xi}\\u_{xj}\end{Bmatrix}$.*

### Solution
1. Stiffness $k = AE/L$; extension $\Delta L = u_{xj}-u_{xi}$.
2. Strain energy: $U = \tfrac12k\Delta L^2 = \tfrac12k(u_{xj}^2-2u_{xj}u_{xi}+u_{xi}^2)$.
3. Work potential: $V = -F_{xi}u_{xi}-F_{xj}u_{xj}$.
4. Total: $\Pi = U+V$.
5. Minimise:

$$
\frac{\partial\Pi}{\partial u_{xi}} = \tfrac12k(2u_{xi}-2u_{xj})-F_{xi} = 0,\qquad\frac{\partial\Pi}{\partial u_{xj}} = \tfrac12k(2u_{xj}-2u_{xi})-F_{xj} = 0
$$

6. So $F_{xi} = ku_{xi}-ku_{xj}$ and $F_{xj} = -ku_{xi}+ku_{xj}$, which in matrix form is the result. ∎

**Marks go for**: the explicit $U$ and $V$, differentiating with respect to **each** DOF, and stating that the stationary point is the equilibrium (a minimum).

## Q4: Quadratic bar shape functions (L6 exercise)

*A 3-node bar with the origin at the mid-node has $u = a+bx+cx^2$. Obtain $[N]$.*

### Solution
Generalised BCs, with nodes at $x = -L/2,\,0,\,L/2$:
- $u_1 = a-\tfrac{bL}{2}+\tfrac{cL^2}{4}$;
- $u_2 = a$;
- $u_3 = a+\tfrac{bL}{2}+\tfrac{cL^2}{4}$.

Adding and subtracting the first and third:
- $u_1+u_3 = 2a+\tfrac{cL^2}{2}$, so $c = \dfrac{2(u_1-2u_2+u_3)}{L^2}$;
- $u_3-u_1 = bL$, so $b = \dfrac{u_3-u_1}{L}$.

Substitute and collect terms:

$$
u = \underbrace{\left(\frac{2x^2}{L^2}-\frac xL\right)}_{N_1}u_1+\underbrace{\left(1-\frac{4x^2}{L^2}\right)}_{N_2}u_2+\underbrace{\left(\frac{2x^2}{L^2}+\frac xL\right)}_{N_3}u_3
$$

**Check**:
- $N_1(-L/2) = \tfrac12+\tfrac12 = 1$, $N_1(0) = 0$, $N_1(L/2) = \tfrac12-\tfrac12 = 0$ ✓;
- $N_1+N_2+N_3 = 1$ ✓.

## Q5: Propped cantilever with two beam elements (L7 worked example)

*A clamp at $x = 0$, a simple support at $x = 2$ m and 10 kN downward at the free end $x = 3$ m, with $EI = 10^4$ kN m². (i) Write the equilibrium equation in the 6 global DOF. (ii) Apply the BCs and reduce to the 3 unknowns. (iii) Solve, and find the reactions.*

### Solution
(i) Element 1 ($L = 2$) has $EI/L^3 = 1.25\times10^6$; element 2 ($L = 1$) has $EI/L^3 = 10^7$. In units of $1.25\times10^6$:

$$
\begin{Bmatrix}F_1\\M_1\\F_2\\M_2\\F_3\\M_3\end{Bmatrix} = 1.25\times10^6\begin{bmatrix}12&12&-12&12&0&0\\12&16&-12&8&0&0\\-12&-12&108&36&-96&48\\12&8&36&48&-48&16\\0&0&-96&-48&96&-48\\0&0&48&16&-48&32\end{bmatrix}\begin{Bmatrix}v_1\\\theta_1\\v_2\\\theta_2\\v_3\\\theta_3\end{Bmatrix}
$$

(ii) $v_1 = \theta_1 = v_2 = 0$. The loads are $M_2 = 0$, $F_3 = -10^4$ N and $M_3 = 0$. Delete rows and columns 1–3:

$$
\begin{Bmatrix}0\\-10^4\\0\end{Bmatrix} = 1.25\times10^6\begin{bmatrix}48&-48&16\\-48&96&-48\\16&-48&32\end{bmatrix}\begin{Bmatrix}\theta_2\\v_3\\\theta_3\end{Bmatrix}
$$

(iii) Solution:
- $\theta_2 = -5.0\times10^{-4}$ rad;
- $v_3 = -8.33\times10^{-4}$ m $= -0.833$ mm;
- $\theta_3 = -1.0\times10^{-3}$ rad.

Reactions from rows 1–3: $F_1 = -7.5$ kN, $M_1 = -5.0$ kN m, $F_2 = +17.5$ kN.

**Statics check**:
- vertical: $-7.5+17.5-10 = 0$ ✓;
- moments about the clamp: $-5+17.5\times2-10\times3 = 0$ ✓.

The span between the supports lifts: the prop acts as a pivot.

![[dam_beam_example_deflection.png|560]]

## Q6: Yield pressure from one linear run (L4)

*A nozzle made of material with $\sigma_Y = 340$ MPa is analysed at 2.5 MPa internal pressure, giving a peak von Mises stress of 238.6 MPa and a peak Tresca stress intensity of 256.1 MPa. Find the pressure at first yield for each criterion, and the allowable pressure with FoS = 1.5.*

### Solution
Linear analysis means stress ∝ pressure:
- von Mises: $P_Y = 2.5\times340/238.6 = 3.56$ MPa;
- Tresca: $P_Y = 2.5\times340/256.1 = 3.32$ MPa. This is the lower, conservative value. The slide prints 3.20, which is an arithmetic slip.

With FoS = 1.5 on Tresca: $P_{allow} = 3.32/1.5 = 2.21$ MPa.

## Q7: Stress concentration

*(a) An elliptical hole with $a = 2b$ ($a$ perpendicular to the load), under bulk stress 100 MPa: give $K_t$ and the peak. (b) A 400 mm wide plate with a 160 mm central hole under 120 MPa gross: estimate the peak, and the FoS for $\sigma_Y = 460$ MPa.*

### Solution
(a) $K_t = 1+2a/b = 5$, so the peak is 500 MPa. The FE result of 503.7 MPa gives $K_t = 5.04$ ✓.

(b) $d/W = 0.4$:
- Heywood: $K_{t,net}\approx2+0.6^3 = 2.216$;
- net stress $= 120\times400/240 = 200$ MPa, so $\sigma_{max}\approx443$ MPa;
- FoS $= 460/443\approx1.04$. That is below 1.5–2, so it is unacceptable: enlarge the plate, reduce the hole or the load, or use a stronger material.

## Q8: 2-DOF modal analysis, participation factor and effective mass (L10)

*$m_1 = 2$ kg is joined to ground by $k_1 = 1000$ N/m; $m_2 = 1$ kg is joined to ground by $k_2 = 2000$ N/m; $k_3 = 3000$ N/m couples the masses. Find the natural frequencies, mass-normalised modes, participation factors and effective masses for base motion.*

### Solution
$$
[M] = \begin{bmatrix}2&0\\0&1\end{bmatrix},\qquad[K] = \begin{bmatrix}4000&-3000\\-3000&5000\end{bmatrix}
$$

Characteristic equation, with $\lambda = \omega^2$:

$$
\det([K]-\lambda[M]) = (4000-2\lambda)(5000-\lambda)-9\times10^6 = 0\;\Rightarrow\;\lambda^2-7000\lambda+5.5\times10^6 = 0
$$

$\lambda = 901.9$ and $6098.1$, so $\omega = 30.03$ and $78.09$ rad/s: **$f_1 = 4.78$ Hz and $f_2 = 12.43$ Hz**.

Modes:
- Mode 1: $(4000-1803.8)\phi_1 = 3000\phi_2$ gives $\phi_2/\phi_1 = 0.732$. Mass-normalising, $2\phi_1^2+\phi_2^2 = 1$, gives $\{0.6280,\ 0.4597\}$ (**in phase**).
- Mode 2: $\phi_2/\phi_1 = -2.732$, giving $\{-0.3251,\ 0.8881\}$ (**out of phase**).

Participation, with $\{D\} = \{1,1\}$:
- $\gamma_1 = 2(0.6280)+0.4597 = 1.7157$;
- $\gamma_2 = 2(-0.3251)+0.8881 = 0.2379$ (the sign depends on the mode's sign convention).

Effective masses: $M_{\mathrm{eff}} = \gamma^2 = 2.9436$ and $0.0566$ kg. The sum is $3.000$ kg, the total mass ✓. Mode 1 carries 98%, so it dominates the base-excited response.

![[dam_modal_2dof.png|520]]

## Q9: Nonlinear spring by direct substitution and Newton–Raphson

*A softening spring has $k(u) = 100-50u$ under $P = 40$. Do three iterations of each method from $u_0 = 0$.*

### Solution
Exact: $50u^2-100u+40 = 0$, so $u = 0.552786$.

**Direct substitution**, $u_{i+1} = P/k(u_i)$:
- $u_1 = 40/100 = 0.4000$;
- $u_2 = 40/80 = 0.5000$;
- $u_3 = 40/75 = 0.5333$.

It converges linearly (0.5528 after about 10 iterations).

**Newton–Raphson**, with $R = (100-50u)u-40$ and $K_T = 100-100u$:
- $u_1 = 0+40/100 = 0.4000$;
- $R(0.4) = -8$, $K_T = 60$, so $u_2 = 0.4+8/60 = 0.5333$;
- $R = -0.889$, $K_T = 46.67$, so $u_3 = 0.55238$.

Then $u_4 = 0.5527862$: quadratic convergence. See [[Direct Substitution and Newton-Raphson]].

## Q10: Boundary conditions and rigid-body modes

*A 2D block rests on the ground under a downward pressure on top. Critique the supports: (a) $u_y = 0$ on all bottom nodes; (b) $u_x = u_y = 0$ on all bottom nodes; (c) propose a correct set.*

### Solution
(a) This removes $y$-translation and rotation, but **not** $x$-sliding. The model has a rigid-body mode, so $[K]$ is singular (zero pivot).

(b) There is no rigid-body motion, but it is **over-constrained**. The base cannot expand laterally (Poisson), giving spurious corner stresses instead of the uniform $\sigma_y = -p$.

(c) Use $u_y = 0$ on the bottom and $u_x = 0$ at **one** bottom node. Or model half the block with a symmetry condition ($u_x = 0$ on the centreline). Three rigid-body modes are removed with nothing extra.

## Q11: Short explain-questions (model answers)
- **What is interpolation / a shape function?** Shape functions define the displacement anywhere in an element from the nodal DOF, $u = [N]\{d\}$. Each $N_i$ is 1 at its node and 0 at the others. This reduces infinitely many DOF to a finite number.
- **h vs p refinement?** h makes the elements smaller; p raises the polynomial order (linear → quadratic). Both add DOF.
- **Why shells for wing skins, not solids?** $t\ll L$. Shells capture bending and membrane action with few DOF. Solids need at least 3 linear (or 2 quadratic) layers through the thickness to bend correctly.
- **Stress keeps rising with refinement: why?** A singularity (sharp corner, point load or constraint). Converge away from it, add fillets, or distribute the loads.
- **Modal analysis gives no frequencies: why?** No density, so $[M] = 0$.
- **Three sources of nonlinearity?** Geometric (large deflection, follower loads); material (plasticity, creep, viscoelasticity); boundary/contact (friction, gaps, deformation-dependent loads).
- **Free–free check?** Run a modal solve with no constraints. Expect exactly 6 zero-frequency modes; more means a part is disconnected.
- **Verification vs validation?** Verification: is the model solved correctly (units, mesh, BCs, maths checks)? Validation: does it match reality (tests), updated if necessary?

## Sources
- Source: FEA lectures L3–L12 worked examples (including Example Sheet 1 and 2 questions worked in lecture), `02 - Sources/FEM Lectures/`; transcript `FEA.txt`
- Calculation notes: all numbers reproduced in Python (NumPy `solve`, SciPy `eigh`)
