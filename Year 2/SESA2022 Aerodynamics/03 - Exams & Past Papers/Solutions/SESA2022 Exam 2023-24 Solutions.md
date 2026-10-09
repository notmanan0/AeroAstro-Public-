---
title: "SESA2022 Exam 2023-24 Solutions"
module: "SESA2022 Aerodynamics"
type: exam-solution
year: "2023-24"
tags: [sesa2022, exam-solutions, past-papers, open-book]
topics: ["[[SESA2022 T2 - Boundary Layers]]", "[[SESA2022 T3 - Potential Flow]]", "[[SESA2022 T4 - Thin Aerofoil Theory]]", "[[SESA2022 T5 - Finite Wing Theory]]"]
status: complete
sources: ["03 - Exams & Past Papers/SESA2022-202324-01-SESA2022.pdf"]
---

# SESA2022 Exam 2023-24 Solutions

> [!info] Paper: online assessment.
> - **Part A** (answers to 2 d.p.) covers pitot BL data with riblets, and a dune for tidal power.
> - **Part B** (answers to 4 d.p.) covers flap TAT, an elliptic wing, $C_p$ data and a finite wing.
>
> Parameters depend on whether the student ID ends in an **even or odd** digit.

> [!warning] Missing data
> `file1_pressure.csv`/`file2_pressure.csv` (A Q1) and `0020Cpcomp.csv` (B Q3) are not in the vault.
> - A Q1(i)–(iv) is worked on an **illustrative pitot dataset**: a tripped turbulent BL at $U_\infty = 15$ m/s, built from Spalding's law plus a Coles wake.
> - B Q3 is answered as a method.
>
> Q1(v)–(vi) and everything else needs no data and is exact.

## Part A

### Q1: Pitot traverse at the trailing edge of a tripped plate ($p_s = 101325$ Pa)

#### (i) $\delta$ and $\delta^*$
First convert total pressure to velocity with Bernoulli: $U = \sqrt{2(P_0-p_s)/\rho}$. The freestream plateau gives $U_\infty = 15.00$ m/s.

$$
\delta_{99}\text{ by linear interpolation where }U = 0.99U_\infty:\quad\boxed{\delta = 28.93\text{ mm}}
$$

$$
\boxed{\delta^* = \int\left(1-\frac{U}{U_\infty}\right)dy = 4.72\text{ mm}},\qquad \theta = 3.41\text{ mm}\;(H = 1.39)
$$

Both integrals use the trapezium rule and include $(0,0)$ (see [[Displacement and Momentum Thickness]]).

#### (ii) Viscous drag, one side
The profile is at the trailing edge, so the momentum deficit equals the whole plate's drag (see [[Momentum Integral Equation]]):

$$
D' = \rho U_\infty^2\theta_{TE} = 1.225(15^2)(3.41\times10^{-3}) = \boxed{0.94\text{ N/m}}
$$

#### (iii) Inner-unit plot
This needs $u_\tau = U_\infty\sqrt{C_f/2}$. Take $C_f$ at $x = L$ from part (iv): $C_f = 0.00338$, so $u_\tau = 0.617$ m/s. Then $y^+ = yu_\tau/\nu$ and $u^+ = U/u_\tau$ (see [[Law of the Wall]]).

![[e2324_a_q1_inner_units.png|650]]

- **Viscous sub-layer**: $y^+<5$, where $u^+ = y^+$.
- **Log layer**: $30<y^+<0.2\delta^+\approx240$, where $u^+ = \frac1\kappa\ln y^++B$.
- Beyond that is the wake region.

The data sits slightly below the log law because the correlation-based $u_\tau$ is about 2 % high. A Clauser-chart fit (choosing $u_\tau$ to put the data on the log law) would refine it.

#### (iv) Plate length
Integrate $C_f = 0.059Re_x^{-1/5}$ along the plate and equate to the drag:

$$
D' = \int_0^L\tfrac12\rho U_\infty^2C_f\,dx = \tfrac12\rho U_\infty^2L\cdot\frac{0.059}{0.8}Re_L^{-1/5} = \rho U_\infty^2\theta
$$

$$
\frac\theta L = 0.036875\,Re_L^{-1/5}\;\Rightarrow\;\boxed{L = 1.61\text{ m}}\quad(\text{solved with brentq})
$$

#### (v) Riblet height, 10 wall units
$h = 10\nu/u_\tau$, with $u_\tau = U_0\sqrt{C_f(X)/2}$ and $C_f = 0.059(U_0X/\nu)^{-1/5}$.

| | Even: $U_0 = 15$ m/s, $X = 3$ m | Odd: $U_0 = 20$ m/s, $X = 6$ m |
|---|---|---|
| $Re_X$ | $3.0\times10^6$ | $8.0\times10^6$ |
| $C_f$ | 0.002988 | 0.002456 |
| $u_\tau$ | 0.580 m/s | 0.701 m/s |
| $h$ | $\mathbf{258.70\ \mu m}$ | $\mathbf{214.02\ \mu m}$ |

#### (vi) Height along $0.5X\to X$
$u_\tau\propto x^{-0.1}$, so $h(x) = h(X)(x/X)^{0.1}$. The height grows only about 7 % over the region: 241.4 → 258.7 µm (even) and 199.7 → 214.0 µm (odd). Because the friction velocity falls slowly downstream, riblets must get slightly taller.

![[e2324_a_q1_riblets.png|620]]

### Q2: Dune from cylinder flow ($U_\infty = 1$, $\kappa = 2\pi$, so $R = 1$ m)

#### (i) Dune streamline
Uniform flow plus doublet (see [[Flow Past a Cylinder]]):

$$
\psi = U_\infty z\left(1-\frac{R^2}{x^2+z^2}\right)
$$

Through $(0,aR)$: $\psi_d = U_\infty R\left(a-\frac1a\right)$. The dune is the streamline

$$
\boxed{z\left(1-\frac{1}{x^2+z^2}\right) = a-\frac1a}\quad\begin{cases}a = 1.2: & \psi_d = 0.3667\\ a = 1.5: & \psi_d = 0.8333\end{cases}
$$

Far from the dune it tends to the flat bed height $z\to\psi_d$.

#### (ii)–(iv) Plots and $\Delta C_P$
On the axis $x = 0$: $u = \partial\psi/\partial z = 1+1/z^2$ and $w = 0$. At the crest $z = a$:

| | $a = 1.2$ (even) | $a = 1.5$ (odd) |
|---|---|---|
| $U_{crest}/U_\infty = 1+1/a^2$ | 1.6944 | 1.4444 |
| **(iii)** $\Delta C_P = (U/U_\infty)^3-1$ at crest | $\mathbf{3.86}$ | $\mathbf{2.01}$ |
| worst $\Delta C_P$ (foot of dune) | $-0.56$ at $x = \pm1.61$ m | $-0.28$ at $x = \pm2.20$ m |

- **(iii)** At the crest the flow is accelerated by 69 % (even case), so a turbine there would extract about **4.9×** the freestream power ($\Delta C_P = 3.86$), because power scales as $U^3$.
- **(iv) Best** is the crest. **Worst** is the upstream and downstream feet, where the flow decelerates below $U_\infty$ (the fluid is still turning around the cylinder-like shape). $\Delta C_P\to0$ far away.

![[e2324_a_q2_dune.png|700]]

**Validity for real flows**
- The potential solution is symmetric and inviscid.
- In reality the river-bed boundary layer thickens against the adverse gradient on the lee side and may **separate**, giving a recirculating wake with low, unsteady velocity. The downstream foot would then be far worse than predicted, and the crest speed-up would be somewhat lower.
- Free-surface effects, turbulence and the turbine's own blockage are also ignored.
- The upstream half and the crest are reasonably predicted. See [[Boundary Layer Separation]].

## Part B

### Q1: NACA0020 with a 25 % flap

#### (i) Camber slope
Hinge at $x_h = 0.75c$. Since $\cos\theta_h = 1-2(0.75) = -0.5$, $\theta_h = 2\pi/3$.

$$
\frac{dz}{dx} = \begin{cases}0 & 0\le x<0.75c\;\;(0\le\theta_0<2\pi/3)\\ -\delta & 0.75c<x\le c\;\;(2\pi/3<\theta_0\le\pi)\end{cases}
$$

See [[Trailing-Edge Flap in Thin Aerofoil Theory]].

#### (ii) Flap angle for $C_l = 0.957$ at $\alpha = 5^\circ$
$A_0 = \alpha+\frac\delta3$, $A_1 = \frac{\sqrt3}{\pi}\delta$ and $A_2 = -\frac{\sqrt3}{2\pi}\delta$, so

$$
C_l = 2\pi\alpha+\left(\frac{2\pi}3+\sqrt3\right)\delta = 0.5483+3.8264\,\delta = 0.957
$$

$$
\boxed{\delta = 0.1068\text{ rad} = 6.1196^\circ}
$$

#### (iii) Flap angle for $C_{m,LE} = -0.2271$

$$
C_{m,LE} = -\frac\pi2\left(A_0+A_1-\frac{A_2}{2}\right) = -\frac\pi2\alpha-\left(\frac\pi6+\frac{5\sqrt3}{8}\right)\delta = -0.1371-1.6061\,\delta
$$

With $\alpha = 5^\circ$: $-0.1371-1.6061\delta = -0.2271$, so $\boxed{\delta = 0.0560\text{ rad} = 3.2114^\circ}$.

> [!warning] The question is over-specified
> $C_l$, $\alpha$ and $C_{m,LE}$ can't all be held. With $\alpha = 5^\circ$ and $\delta = 3.21^\circ$, $C_l = 0.7628$, not 0.957. The flap angle from (ii) gives $C_{m,LE} = -0.3086$. If instead $C_l = 0.957$ is held and $\alpha$ is allowed to change ($C_{m,LE} = C_{m,c/4}-C_l/4 = -0.6495\delta-0.2393$), you get $\delta = -1.07^\circ$ (flap *up*). State the assumption. The fixed-$\alpha$ answer above is the most natural reading.

### Q2: Elliptic wing, $AR = 10$, $C_L = 0.5$, $a_0 = 6.1$ rad⁻¹

- **(i)** $C_{D_i} = \dfrac{C_L^2}{\pi AR} = \dfrac{0.25}{10\pi} = \boxed{0.0080}$ (0.007958).
- **(ii)** $C_L = \dfrac{2\bar\Gamma}{V\bar c}$ and $c_l(0) = \dfrac{2\Gamma_0}{Vc}$. For a constant-chord (rectangular) planform, $c_l(0) = C_L\dfrac{\Gamma_0}{\bar\Gamma} = \dfrac{0.5}{0.85} = \boxed{0.5882}$. A true ellipse has $\bar\Gamma = \frac\pi4\Gamma_0 = 0.785\Gamma_0$; the paper states 0.85, so use it.
- **(iii)** $\alpha(0) = \dfrac{c_l(0)}{a_0}+\dfrac{C_L}{\pi AR} = 0.09643+0.01592 = 0.1123\text{ rad} = \boxed{6.4370^\circ}$ (symmetric section).
- **(iv)** Elliptic lift distribution.
- **(v)** Constant downwash along the span.

### Q3: $C_p$ data for NACA0020 with a flap (method; data not in the vault)
1. Load the CSV and plot $C_p$ against $x/c$ for all six $\alpha$ on one axis, with the $y$-axis **inverted** (suction up). Label the suction (upper) and pressure (lower) branches, and shade or mark the flap hinge at $x/c = 0.75$. Expect a secondary suction spike at the hinge, where the flow turns onto the deflected flap.
2. For each $\alpha$, take the most negative $C_p$ on the suction side ("$C_{p,max}$" suction) and plot it against $\alpha$. It grows roughly linearly while the flow is attached. A plateau or collapse at high $\alpha$ signals the loss of the leading-edge suction peak, i.e. stall (see [[Aerofoil Stall]]).

### Q4: Finite wing, $AR = 8$, $\tau = \delta = 0.055$, $dC_L/d\alpha = 0.08$/deg, $C_{D_i} = 0.009$, $C_D = 0.047$

- **(i)** $a = 0.08\times\frac{180}{\pi} = \boxed{4.5837\text{ rad}^{-1}}$
- **(ii)** $C_{D_0} = 0.047-0.009 = \boxed{0.0380}$
- **(iii)** $e = 1/(1+\delta) = 0.9479$ and $\left(\dfrac{C_L}{C_D}\right)_{max} = \dfrac12\sqrt{\dfrac{\pi eAR}{C_{D_0}}} = \boxed{12.5191}$ (see [[Maximum Lift-to-Drag Ratio]])
- **(iv)** $a_0 = \dfrac{a}{1-\frac{a(1+\tau)}{\pi AR}} = \dfrac{4.5837}{1-0.1924} = \boxed{5.6757\text{ rad}^{-1}}$

## Sources
- `03 - Exams & Past Papers/SESA2022-202324-01-SESA2022.pdf`. Numbers verified in Python.
- A Q1(i)–(iv) uses illustrative pitot data because the CSVs aren't in the vault.
