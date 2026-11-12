---
title: "SESA2029 A5 - Numerical Stability - Von Neumann Analysis, Fourier and CFL Numbers"
module: "SESA2029 Digital Aerospace Methods"
type: topic
stream: "Part A: Computational Fluid Dynamics"
order: 5
tags: [sesa2029, cfd, stability, von-neumann, cfl]
aliases: ["Von Neumann analysis", "CFL condition", "Fourier number", "CFD Lecture 6"]
date: 2026-10-30
status: lectured
coverage: "Week 3 (2025-10-17)"
parent: ["[[SESA2029 Digital Aerospace Methods Hub]]"]
prerequisites: ["[[SESA2029 A4 - Time Marching - Explicit and Implicit Methods]]"]
next_topics: ["[[SESA2029 A6 - Higher-Order Time Integration, Runge-Kutta and the Blasius Equation]]"]
key_concepts: ["[[Von Neumann Stability Analysis]]", "[[CFL and Fourier Numbers]]", "[[Explicit and Implicit Time Integration]]"]
tutorial_sheets: ["[[SESA2029 CFD Worked Examples]]"]
sources: ["02 - Sources/CFD/All_lectures_as_delivered.pdf (L6)", "02 - Sources/Lectures/SESA2029 Lecture 2025-10-17.txt"]
---

# SESA2029 A5 - Numerical Stability - Von Neumann Analysis, Fourier and CFL Numbers

> [!abstract] Summary
> Stability is judged by the gain $G=|f^{n+1}/f^n|$: a scheme is unstable if some component grows from step to step. For the model equation $\mathrm df/\mathrm dt=\lambda f$, explicit Euler is stable only inside a unit circle centred at $\lambda\Delta t=-1$, while implicit Euler is stable everywhere outside a unit circle centred at $+1$. Von Neumann analysis applies the same test to a PDE by assuming a Fourier wave $e^{ikx_j}$; the shortest resolvable wave ($kh=\pi$) is the worst case, which gives $F=\alpha\Delta t/h^2\le\tfrac12$ for explicit diffusion and $C=c\Delta t/h\le1$ for explicit upwind convection.

> [!summary]- Exam use: quick path
> - **Use it when:** you must find the stability limit of a scheme, the largest stable time step, or explain the Courant or Fourier number.
> - **Assumptions:** linear equation with constant coefficients; uniform grid; periodic or long domain, so Fourier waves are valid.
> - **Method:** 1. Write the update $f_j^{n+1}=\dots$. 2. Substitute $f_j=e^{ikx_j}$, so $f_{j\pm1}=f_je^{\pm ikh}$. 3. Divide by $f_j^n$ to get the amplification factor; $G$ is its modulus. 4. Use $e^{ikh}+e^{-ikh}=2\cos kh$ and check the worst $kh$ (usually $\pi$). 5. Set $G=1$ for the limit.
> - **Common mistakes:** squaring the $i$ when taking a modulus (square the real and imaginary parts); differencing downwind, which is unconditionally unstable.
> - **Practise:** [[#2. Von Neumann analysis of the heat equation]] · [[#Largest stable step for the F-4C short-period mode]] · [[SESA2029 CFD Worked Examples#Q6: Von Neumann analysis of a new scheme|CFD worked examples Q6]]

In the numerical experiments of [[SESA2029 A4 - Time Marching - Explicit and Implicit Methods|A4]], the explicit heat-equation scheme becomes unstable above a Fourier number of about 0.5, while the implicit one never does. Von Neumann analysis explains why, with simple theory that tests stability before anything is run.

Any error pattern on the grid can be decomposed into sines and cosines of different wavelengths. If the scheme multiplies even one of those waves by more than 1 each step, that wave grows exponentially and eventually swamps the solution: the saw-tooth seen in the experiments is the shortest wave the grid can carry, growing. Stability analysis computes the multiplier for every wave and finds the worst. For an ODE there is only one "wave", the solution itself, and the same idea reduces to asking whether one step multiplies the solution by more than the exact solution would.

## 1. Stability of the model equation

The model equation is $\mathrm df/\mathrm dt=\lambda f$ with exact solution $f=f_0e^{\lambda t}$ and $\lambda=\sigma+i\omega$ a growth rate and a frequency (L6 slide 3). The F-4C's short-period response to a sudden pitch-up follows it with $\lambda=-0.5+1.3i$, a decaying oscillation; it covers every dynamic mode in flight mechanics, which is why it is a fair test.

### Explicit Euler

Use a forward difference with the right-hand side at level $n$ (L6 slide 4):

$$
\frac{f^{n+1}-f^n}{\Delta t}=\lambda f^n.
$$

Multiply by $\Delta t$ and collect:

$$
f^{n+1}=f^n+\lambda\Delta t\,f^n=(1+\lambda\Delta t)f^n.
$$

Define the gain as the change in amplitude over one step:

$$
G=\left|\frac{f^{n+1}}{f^n}\right|=|1+\lambda\Delta t|.
$$

$G>1$ is unstable, $G<1$ stable and $G=1$ neutral. Find the boundary by setting $G=1$ and splitting $\lambda\Delta t$ into its real and imaginary parts:

$$
1=\left|(1+\sigma\Delta t)+i\,\omega\Delta t\right|.
$$

The modulus of a complex number is the length of a vector in the complex plane, so square the real part and the imaginary part, not the $i$:

$$
1^2=(1+\sigma\Delta t)^2+(\omega\Delta t)^2.
$$

That is a circle of radius 1 centred at $(\sigma\Delta t,\omega\Delta t)=(-1,0)$. At its centre $G=0$, inside it $G<1$, outside it $G>1$. Explicit Euler is stable only inside the circle; too large a time step pushes $\lambda\Delta t$ along a ray from the origin and out of it.

### Implicit Euler

Put the right-hand side at $n+1$:

$$
\frac{f^{n+1}-f^n}{\Delta t}=\lambda f^{n+1}.
$$

Multiply by $\Delta t$ and collect the unknowns:

$$
f^{n+1}-\lambda\Delta t\,f^{n+1}=f^n
\quad\Longrightarrow\quad
(1-\lambda\Delta t)f^{n+1}=f^n.
$$

So

$$
G=\left|\frac{f^{n+1}}{f^n}\right|=\frac{1}{|1-\lambda\Delta t|}.
$$

$G=1$ when $|1-\lambda\Delta t|=1$, that is

$$
1=(1-\sigma\Delta t)^2+(\omega\Delta t)^2,
$$

a unit circle centred at $(+1,0)$, where $G$ is infinite. Implicit Euler has $G<1$ everywhere outside that circle (L6 slide 5).

![[dam_euler_stability_circles.png|900]]

The correct, real-world answer is $G<1$ exactly when $\sigma<0$, the left half-plane. Neither method reproduces that. Explicit Euler has a small region of stability and computes some physically decaying modes as growing; implicit Euler is stable for every decaying mode whatever the time step, and also damps some physically growing modes in the right half-plane, which is stability without correctness. Neither is accurate in time, since both are first order. On the imaginary axis (pure oscillation, $\sigma=0$) explicit Euler is never stable: $G^2=1+(\omega\Delta t)^2>1$. That motivates the Runge–Kutta schemes of [[SESA2029 A6 - Higher-Order Time Integration, Runge-Kutta and the Blasius Equation|A6]].

## 2. Von Neumann analysis of the heat equation

For a PDE the analysis is called von Neumann's method. The explicit heat scheme is (L6 slide 6)

$$
T_j^{n+1}=T_j^n+F\left(T_{j-1}^n-2T_j^n+T_{j+1}^n\right),\qquad F=\frac{\alpha\Delta t}{h^2}.
$$

A representative solution shape is a single Fourier wave of wavenumber $k=2\pi/\lambda_w$, where $\lambda_w$ is the wavelength (long waves have small $k$):

$$
T_j=e^{ikx_j}.
$$

Since $x_{j\pm1}=x_j\pm h$,

$$
T_{j+1}=e^{ik(x_j+h)}=e^{ikx_j}e^{ikh}=T_je^{ikh},
\qquad
T_{j-1}=T_je^{-ikh}.
$$

Any error distribution on the grid is a sum of such waves, and for a linear scheme each wave evolves independently, so testing one wavenumber at a time is general. Substitute into the scheme:

$$
T_j^{n+1}=T_j^n+F\left(T_j^ne^{-ikh}-2T_j^n+T_j^ne^{ikh}\right).
$$

Factor out $T_j^n$:

$$
T_j^{n+1}=T_j^n\left[1+F\left(e^{-ikh}-2+e^{ikh}\right)\right].
$$

With $e^{ikh}=\cos kh+i\sin kh$ and $e^{-ikh}=\cos kh-i\sin kh$, the imaginary parts cancel and the sum is $2\cos kh$:

$$
T_j^{n+1}=T_j^n\left[1+F(2\cos kh-2)\right].
$$

Divide by $T_j^n$ and take the modulus:

$$
G=\left|1-2F(1-\cos kh)\right|.
$$

The factor $1-\cos kh$ lies between 0 and 2, so the bracket lies between $1$ (at $kh=0$) and $1-4F$ (at $kh=\pi$). The worst case, which sets the stability limit, is $kh=\pi$, the shortest wave the grid can represent: two points per wavelength, a saw-tooth that alternates in sign from point to point; anything shorter cannot be resolved. There $\cos kh=-1$ and (L6 slide 7)

$$
G=|1-4F|.
$$

$G=1$ at $F=\tfrac12$ (where $1-4F=-1$), and $G>1$ for $F>\tfrac12$. Hence the stability requirement for explicit Euler with second-order central differences is

$$
\boxed{F=\frac{\alpha\Delta t}{h^2}\le\frac12}
$$

which matches the Python experiments: $F=0.448$ gives $G=0.792$ and is stable, $F=0.576$ gives $G=1.304$ and blows up.

### The implicit heat scheme

The same substitution into the implicit scheme $-FT_{j-1}^{n+1}+(1+2F)T_j^{n+1}-FT_{j+1}^{n+1}=T_j^n$ gives

$$
T_j^{n+1}\left[-Fe^{-ikh}+1+2F-Fe^{ikh}\right]=T_j^n.
$$

Use $e^{ikh}+e^{-ikh}=2\cos kh$:

$$
T_j^{n+1}\left[1+2F(1-\cos kh)\right]=T_j^n,
$$

so

$$
G=\frac{1}{1+2F(1-\cos kh)}\le1\quad\text{for every }F>0\text{ and every }kh.
$$

The implicit scheme is unconditionally stable, as the A4 runs showed even at $F=4.6$. At $kh=\pi$, $G=1/(1+4F)$: the saw-tooth is damped, never amplified.

## 3. Von Neumann analysis of the convection equation

The convection equation

$$
\frac{\partial f}{\partial t}+c\frac{\partial f}{\partial x}=0
$$

has the general solution $f(x,t)=f_0(x-ct)$, a fixed initial shape $f_0(x)$ moving from left to right at speed $c$ without change (L6 slide 8). It is the model for the convective left-hand side of the Euler and Navier–Stokes equations, as the heat equation models their viscous right-hand side.

Discretise with explicit Euler in time and an upwind difference in space, which for $c>0$ is the backward difference:

$$
\frac{f_j^{n+1}-f_j^n}{\Delta t}+c\frac{f_j^n-f_{j-1}^n}{h}=0.
$$

Multiply by $\Delta t$ and rearrange, with the Courant (CFL, for Courant–Friedrichs–Lewy) number $C=c\Delta t/h$:

$$
f_j^{n+1}=f_j^n-C\left(f_j^n-f_{j-1}^n\right).
$$

Substitute $f_{j-1}=f_je^{-ikh}$ and divide by $f_j^n$ (L6 slide 9):

$$
\frac{f_j^{n+1}}{f_j^n}=1-C\left(1-e^{-ikh}\right).
$$

Expand $e^{-ikh}$:

$$
\frac{f_j^{n+1}}{f_j^n}=1-C(1-\cos kh)-iC\sin kh.
$$

At the worst case $kh=\pi$, $\sin kh=0$ and $\cos kh=-1$, so

$$
G=|1-2C|.
$$

A small $C$ is stable; $C=\tfrac12$ gives $G=0$; $C=1$ gives $|{-1}|=1$, the boundary; $C=2$ gives 3. To check every wavenumber, not just $kh=\pi$, square the real and imaginary parts:

$$
G^2=\left[1-C(1-\cos kh)\right]^2+C^2\sin^2kh.
$$

Expand the first square:

$$
G^2=1-2C(1-\cos kh)+C^2(1-\cos kh)^2+C^2\sin^2kh.
$$

Use $(1-\cos kh)^2+\sin^2kh=1-2\cos kh+\cos^2kh+\sin^2kh=2(1-\cos kh)$:

$$
G^2=1-2C(1-\cos kh)+2C^2(1-\cos kh).
$$

Factor:

$$
G^2=1-2C(1-C)(1-\cos kh).
$$

Since $1-\cos kh\ge0$, $G\le1$ for every wave exactly when $C(1-C)\ge0$, that is $0\le C\le1$:

$$
\boxed{C=\frac{c\Delta t}{h}\le1}
$$

The physical meaning is that information must not travel more than one cell per time step, or the stencil cannot see where the solution came from. At exactly $C=1$ the upwind update is $f_j^{n+1}=f_{j-1}^n$, which shifts the solution exactly one cell per step, the exact answer. Below 1 it damps the short waves, which appears as numerical diffusion ([[Convective Interpolation Schemes]]).

![[dam_von_neumann_gain.png|900]]

The direction of the stencil matters as much as its order. Differencing against the flow, with the forward (downwind) difference when $c>0$, gives $f_j^{n+1}=f_j^n-C(f_{j+1}^n-f_j^n)$. The same steps give

$$
G^2=\left[1+C(1-\cos kh)\right]^2+C^2\sin^2kh=1+2C(1+C)(1-\cos kh)>1
$$

for every $C>0$ and every $kh\ne0$: unconditionally unstable. The explicit central difference, $f_j^{n+1}=f_j^n-\tfrac C2(f_{j+1}^n-f_{j-1}^n)$, gives $G^2=1+C^2\sin^2kh$, also greater than 1 for every time step; its worst wave is $kh=\pi/2$, not $\pi$.

## 4. What the limits mean for CFD

| Equation | Parameter | Explicit limit |
|---|---|---|
| Convection $f_t+cf_x=0$, upwind | $C=c\Delta t/h$ | $\le1$ |
| Diffusion $T_t=\alpha T_{xx}$, central | $F=\alpha\Delta t/h^2$ | $\le\tfrac12$ |
| Viscous momentum ($\nu$ in place of $\alpha$) | $\mathrm{CFL}_\nu=\nu\Delta t/h^2$ | $\le\tfrac12$ by analogy |

These three dimensionless numbers are the key parameters for a stable explicit solution of a PDE (L6 slide 10). Because the diffusive limit scales with $h^2$, halving the grid spacing cuts the allowable explicit time step by four, which makes explicit schemes very expensive on fine near-wall meshes; that is a major reason steady solvers are implicit. Time-accurate unsteady runs in Fluent still expose the Courant number as a control, and explicit time-accurate work typically needs $C\lesssim1$.

## Worked examples

### Largest stable step for the F-4C short-period mode

*(Suggested, not lecturer-set; it uses the L6 slide 3 eigenvalue.)* For $\lambda=-0.5+1.3i$, find the largest explicit Euler step that is stable. Set $G=1$:

$$
(1-0.5\Delta t)^2+(1.3\Delta t)^2=1.
$$

Expand:

$$
1-\Delta t+0.25\Delta t^2+1.69\Delta t^2=1.
$$

Cancel the 1 and divide by $\Delta t$:

$$
-1+1.94\Delta t=0
\quad\Longrightarrow\quad
\Delta t_{\max}=\frac{1}{1.94}=0.515\ \mathrm s.
$$

In general $\Delta t_{\max}=-2\sigma/|\lambda|^2$ for a decaying mode. The figure in [[#Implicit Euler]] marks three steps:

| $\Delta t$ (s) | Explicit $G$ | Implicit $G$ | Exact $e^{\sigma\Delta t}$ |
|---|---|---|---|
| 0.1 | 0.959 | 0.945 | 0.951 |
| 0.3 | 0.935 | 0.823 | 0.861 |
| 0.5 | 0.992 | 0.710 | 0.779 |
| 0.6 | 1.048 | 0.660 | 0.741 |

> [!check] Explicit too weak, implicit too strong
> The exact decay per step is $e^{-0.5\Delta t}$. At every step size explicit Euler damps too little and implicit Euler damps too much, and both errors shrink as $\Delta t\to0$; at $\Delta t=0.1$ s they bracket the exact 0.951. At $\Delta t=0.6$ s explicit Euler turns a stable aircraft mode into a growing one, which is the instability, while implicit Euler is still stable but decays 11 % per step too fast.

### Explicit time-step limits on a CFD mesh

*(Suggested, not lecturer-set; the numbers come from A1.)* Air with $\nu=1.5\times10^{-5}$ m²/s at $U_\infty=30$ m/s, on a mesh whose first wall cell is $h=12.4\ \mu$m (the $y_1^+=1$ cell of [[SESA2029 A1 - Digital Design and the Role of CFD and FEA#First-cell height for a turbulent flat plate|A1]]) and whose cells away from the wall are 1 mm.

Viscous limit at the wall:

$$
\Delta t\le\frac{h^2}{2\nu}=\frac{(1.24\times10^{-5})^2}{2\times1.5\times10^{-5}}=\frac{1.54\times10^{-10}}{3\times10^{-5}}=5.1\times10^{-6}\ \mathrm s.
$$

Convective limit in the 1 mm cells:

$$
\Delta t\le\frac{h}{U_\infty}=\frac{10^{-3}}{30}=3.3\times10^{-5}\ \mathrm s.
$$

Viscous limit in the 1 mm cells: $h^2/2\nu=10^{-6}/(3\times10^{-5})=0.033$ s, irrelevant there. The tiny wall cells set a step six times smaller than convection does elsewhere, and a flow-through time of a 1 m plate, 0.033 s, would need about 6500 explicit steps. That is why the steady solvers used in the coursework are implicit.

## Links

- Parent: [[SESA2029 Digital Aerospace Methods Hub]]
- Previous: [[SESA2029 A4 - Time Marching - Explicit and Implicit Methods]]
- Next: [[SESA2029 A6 - Higher-Order Time Integration, Runge-Kutta and the Blasius Equation]]
- Concepts: [[Von Neumann Stability Analysis]] · [[CFL and Fourier Numbers]] · [[Explicit and Implicit Time Integration]]
- The same $\sigma\pm i\omega$ plane is the control engineer's s-plane: [[Poles and Zeros]] · [[Characteristic Equation and Eigenvalues]]

## Sources

- `All_lectures_as_delivered.pdf`, L6 (slides 1–10), with transcript `SESA2029 Lecture 2025-10-17.txt` (Prof N. Sandham)
- The general-$kh$ gains were checked symbolically in SymPy; gains, step limits and the F-4C table recomputed in Python. Figures: `01 - Notes/Figures/generate_dam_a5_figures.py`

## Self-study tasks

### Core

- [ ] Derive the stability regions of explicit and implicit Euler for $\mathrm df/\mathrm dt=\lambda f$ (L6 slides 4–5; 2025-10-17, ll. 71–245). → [[#1. Stability of the model equation]]
- [ ] Von Neumann analysis of the explicit heat scheme, showing $F\le\tfrac12$ (L6 slides 6–7; ll. 246–385). → [[#2. Von Neumann analysis of the heat equation]]
- [ ] Von Neumann analysis of explicit upwind convection, showing $C\le1$ (L6 slides 8–9; ll. 386–520). → [[#3. Von Neumann analysis of the convection equation]]
- [ ] Von Neumann analysis of a new scheme (example sheet). → [[SESA2029 CFD Worked Examples#Q6: Von Neumann analysis of a new scheme|Worked examples Q6]]

### Further practice

- [ ] Time-step limits for given $c$, $\alpha$ and $h$ (example sheet). → [[#Explicit time-step limits on a CFD mesh]] · [[SESA2029 CFD Worked Examples#Q7: Time-step limits|Worked examples Q7]]
- [ ] Largest stable explicit step for the F-4C short-period eigenvalue (suggested, not lecturer-set). → [[#Largest stable step for the F-4C short-period mode]]
- [ ] Show that the implicit heat scheme is unconditionally stable (suggested, not lecturer-set). → [[#The implicit heat scheme]]
- [ ] Show that downwind and explicit central differencing of the convection equation are unconditionally unstable (suggested, not lecturer-set). → [[#3. Von Neumann analysis of the convection equation]]

## Transcript and slide slips

> [!warning] Slide slip: the real-world stability region (L6 slide 5)
> Where: [[#Implicit Euler]].
>
> The note under the two circles reads "the correct (real world) solution is that $G<1$ for $\sigma<1$ (i.e. in the left half plane)". The left half-plane is $\sigma<0$; the exact gain per step is $e^{\sigma\Delta t}$, which is below 1 exactly when $\sigma<0$.

> [!warning] Slide slip: "backward Euler" for the space difference (L6 slide 9)
> Where: [[#3. Von Neumann analysis of the convection equation]].
>
> The slide describes the scheme as "explicit Euler time advance and upwind (backward Euler) spatial discretisation". Backward Euler is the implicit time scheme; the upwind space difference is a backward difference, as slide 8 says.

> [!warning] Lecture slip: sign of the gain (2025-10-17, ll. 135–140)
> Where: [[#Explicit Euler]].
>
> The gain is said to be "less than zero inside the circle, and bigger than zero outside". A gain is a modulus and is never negative; the boundary is $G=1$, with $G<1$ inside and $G>1$ outside.

> [!warning] Lecture slip: the substitution (2025-10-17, l. 465)
> Where: [[#3. Von Neumann analysis of the convection equation]].
>
> The substitution is read as "$e^{ikh}$ is cos minus i sine"; it is $e^{-ikh}=\cos kh-i\sin kh$, as the next line uses.
