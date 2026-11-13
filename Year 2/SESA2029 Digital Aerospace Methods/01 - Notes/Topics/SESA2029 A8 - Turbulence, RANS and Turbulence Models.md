---
title: "SESA2029 A8 - Turbulence, RANS and Turbulence Models"
module: "SESA2029 Digital Aerospace Methods"
type: topic
stream: "Part A: Computational Fluid Dynamics"
order: 8
tags: [sesa2029, cfd, turbulence, rans]
aliases: ["RANS equations", "Turbulence modelling", "Closure problem", "CFD Lecture 9"]
date: 2026-10-30
status: lectured
coverage: "Week 5 (2025-10-30)"
parent: ["[[SESA2029 Digital Aerospace Methods Hub]]"]
prerequisites: ["[[SESA2029 A7 - Governing Equations - Euler and Navier-Stokes]]"]
next_topics: ["[[SESA2029 A9 - Finite Volume Method]]"]
key_concepts: ["[[Reynolds Averaging and the Closure Problem]]", "[[Eddy-Viscosity Turbulence Models]]", "[[First-Cell Height and y-plus]]", "[[Law of the Wall]]"]
tutorial_sheets: ["[[SESA2029 CFD Worked Examples]]"]
sources: ["02 - Sources/CFD/All_lectures_as_delivered.pdf (L9, pp. 113–129; L2 pp. 28–31)", "02 - Sources/Lectures/SESA2029 Lecture 2025-10-30.txt", "NASA Langley Turbulence Modeling Resource"]
---

# SESA2029 A8 - Turbulence, RANS and Turbulence Models

> [!abstract] Summary
> Splitting each flow variable into a time mean and a fluctuation and averaging the Navier–Stokes equations gives the Reynolds-averaged (RANS) equations, which contain new unknowns, the Reynolds stresses $\overline{u_i'u_j'}$. Four equations now hold ten unknowns, and writing more equations only adds more unknowns: this closure problem is why turbulence remains unsolved. Engineering models relate the Reynolds stresses to the mean strain through an eddy viscosity $\nu_t$ and then model $\nu_t$ with one equation (Spalart–Allmaras), two ($k$–$\varepsilon$, $k$–$\omega$, SST), or abandon it for seven (Reynolds-stress models).

> [!summary]- Exam use: quick path
> - **Use it when:** asked where the Reynolds stresses come from, why there is a closure problem, what an eddy viscosity is, or how a given model closes the equations.
> - **Assumptions:** statistically steady flow, averaging time long compared with the eddy time scale; incompressible Navier–Stokes from [[SESA2029 A7 - Governing Equations - Euler and Navier-Stokes|A7]].
> - **Method:** 1. Write $u=\bar u+u'$ for every variable. 2. Substitute into each term and average, using $\overline{u'}=0$ and $\overline{\bar u v'}=0$. 3. Keep $\overline{u'v'}$, which is not zero. 4. Count equations against unknowns. 5. Close with $-\overline{u'v'}=\nu_t\,\partial\bar u/\partial y$ and a model for $\nu_t$.
> - **Common mistakes:** setting $\overline{u'v'}=0$ as if the fluctuations were uncorrelated; putting the first cell in the buffer layer, $5<y_1^+<30$.
> - **Practise:** [[#4. The closure problem]] · [[#Near-wall cells and the eddy viscosity]]

The coursework report draws on the earlier numerical methods: the grid studies use the order of accuracy from the Taylor-series work of [[SESA2029 A2 - Discrete Data, Finite Differences and Taylor Tables|A2]], the Fluent residual is the imbalance of the discrete equations from the iterative methods of [[SESA2029 A3 - Iterative Solution of the Steady Heat Equation|A3]], and the boundary-layer lab compares a laminar Navier–Stokes solution with Blasius and with a turbulence model. Turbulence is the biggest limitation of CFD, because there is no agreed way to model it; CFD therefore still needs an expert user rather than being a push-button tool.

In Fluent, the wing lab uses the inviscid model (Euler, slip walls, no boundary layers), the laminar boundary-layer lab the laminar model (the full steady Navier–Stokes equations), and the turbulent lab Spalart–Allmaras, one of the models below.

The physical picture of turbulence is an energy cascade. Energy is fed in at the largest scales, the width of a jet or the thickness of a boundary layer, by the mean shear working on the flow. Large eddies interact, set up strain fields and stretch vorticity into smaller eddies, which interact again to form smaller ones still, until at the Kolmogorov microscales viscosity turns the motion into heat. A dye released in a jet shows the result: separated at first, then folded and mixed by eddies of every size until it is a uniform pale distribution downstream.

## 1. The turbulent boundary layer in wall units

The near-wall scaling is that of [[SESA2029 A1 - Digital Design and the Role of CFD and FEA|A1]]. The wall shear stress $\tau_w=\mu\,(\partial u/\partial y)_w$ defines a friction velocity and wall units:

$$
u_\tau=\sqrt{\frac{\tau_w}{\rho}},
\qquad
u^+=\frac{u}{u_\tau},
\qquad
y^+=\frac{y\,u_\tau}{\nu}.
$$

In these variables, profiles measured at different stations, and even in different pressure gradients, collapse on one curve near the wall. That is an empirical fact from experiments, a way of collapsing the data rather than a theory. Close to the wall is the viscous sublayer, $u^+=y^+$; further out is the log law

$$
u^+=2.5\ln y^++5.24,
$$

where $2.5=1/\kappa$ with the von Kármán constant $\kappa=0.4$ (the constants vary slightly between sources); between them is a buffer layer, and the outer part of the profile depends on the pressure gradient ([[Law of the Wall]]).

![[dam_law_of_the_wall_y1plus.png|640]]

The position of the first grid point in these units, $y_1^+$, decides how the model must treat the wall. A wall-resolved calculation puts it in the sublayer, below 5 and ideally near 1, so the profile is captured by the grid. A wall-function model assumes the first point lies on the log law and needs $30<y_1^+\lesssim200$; even then 15 to 20 points are needed inside the boundary layer, which is what sets the upper limit. In the buffer layer between (8 to 30 in the course convention, from about 5 in many references) neither assumption holds and the answer will be wrong. In the lab, plot $y_1^+$ after solving and refine if needed ([[First-Cell Height and y-plus]]).

## 2. Reynolds averaging

A turbulent signal, for example from a hot-wire probe in a boundary layer, fluctuates about a mean. Define the average over a sample time $T$, long compared with the eddy time scale,

$$
\bar\phi(x_i)=\frac1T\int_0^T\phi(x_i,t)\,dt,
$$

and split the signal into the mean and the fluctuation:

$$
\phi(x_i,t)=\bar\phi(x_i)+\phi'(x_i,t).
$$

In a simulation the average can also be taken over a periodic direction in space. (A hot wire is a very thin heated wire in a Wheatstone bridge; its out-of-balance voltage, once calibrated, gives the velocity.)

![[dam_reynolds_decomposition.png|680]]

The averaging rules follow from the integral. The mean $\bar\phi$ does not depend on $t$, so averaging it changes nothing:

$$
\bar{\bar\phi}=\frac1T\int_0^T\bar\phi\,\mathrm dt=\bar\phi\,\frac1T\int_0^T\mathrm dt=\bar\phi.
$$

Average the decomposition $\phi=\bar\phi+\phi'$ term by term:

$$
\bar\phi=\bar{\bar\phi}+\overline{\phi'}=\bar\phi+\overline{\phi'}
\quad\Longrightarrow\quad
\overline{\phi'}=0.
$$

A constant comes outside the integral, $\overline{c\phi}=c\bar\phi$, and the integral of a sum is the sum of the integrals, $\overline{\phi+\psi}=\bar\phi+\bar\psi$. A product of two means is a constant, so $\overline{\bar\phi\bar\psi}=\bar\phi\bar\psi$. A mean times a fluctuation averages to zero, because the mean comes outside: $\overline{\bar\phi\psi'}=\bar\phi\,\overline{\psi'}=0$. Differentiation and averaging commute, $\overline{\partial\phi/\partial s}=\partial\bar\phi/\partial s$, whether $s$ is a space coordinate (the integral is over $t$, so $\partial/\partial x$ passes through it) or time (in the limit $T\to\infty$ of a statistically steady flow). The exception is the product of two fluctuations: $\overline{\phi'\psi'}$ is zero only if $\phi'$ and $\psi'$ are uncorrelated, and in turbulence they are not ([[#Reynolds averaging of hot-wire samples]]).

## 3. The Reynolds stresses

Reynolds substituted the decomposition into the Navier–Stokes equations and averaged them. The term $\partial(uv)/\partial y$ matters in boundary layers:

$$
\overline{\frac{\partial(uv)}{\partial y}}=\frac{\partial}{\partial y}\overline{(\bar u+u')(\bar v+v')}.
$$

Multiply out the four products and average each one:

$$
=\frac{\partial}{\partial y}\left(\overline{\bar u\bar v}+\overline{\bar u v'}+\overline{u'\bar v}+\overline{u'v'}\right).
$$

The first is $\bar u\bar v$; the middle two are a mean times a fluctuation and vanish:

$$
=\frac{\partial(\bar u\bar v)}{\partial y}+\frac{\partial\,\overline{u'v'}}{\partial y}.
$$

Now do every term of the 2D $x$-momentum equation. The time derivative and the pressure gradient are linear, so the fluctuation parts average away:

$$
\overline{\frac{\partial(\bar u+u')}{\partial t}}=\frac{\partial\bar u}{\partial t}+\frac{\partial\overline{u'}}{\partial t}=\frac{\partial\bar u}{\partial t},
\qquad
\overline{\frac1\rho\frac{\partial(\bar p+p')}{\partial x}}=\frac1\rho\frac{\partial\bar p}{\partial x}.
$$

The viscous terms are linear too, giving $\nu(\partial^2\bar u/\partial x^2+\partial^2\bar u/\partial y^2)$. The other convective term is quadratic in the same way as $\partial(uv)/\partial y$:

$$
\overline{\frac{\partial(uu)}{\partial x}}=\frac{\partial}{\partial x}\left(\bar u\bar u+2\overline{\bar uu'}+\overline{u'u'}\right)=\frac{\partial(\bar u\bar u)}{\partial x}+\frac{\partial\,\overline{u'u'}}{\partial x}.
$$

Collecting the terms, and moving the two fluctuation products to the right-hand side, reproduces the original equation with bars on everything, plus two extra terms:

$$
\frac{\partial\bar u}{\partial t}+\frac{\partial(\bar u\bar u)}{\partial x}+\frac{\partial(\bar u\bar v)}{\partial y}+\frac1\rho\frac{\partial\bar p}{\partial x}
=\nu\left(\frac{\partial^2\bar u}{\partial x^2}+\frac{\partial^2\bar u}{\partial y^2}\right)-\frac{\partial\,\overline{u'u'}}{\partial x}-\frac{\partial\,\overline{u'v'}}{\partial y}.
$$

The new terms are averages of the fluctuations, and the mean flow does not determine them. The average $\overline{u'v'}$ would vanish only if $u'$ and $v'$ were uncorrelated random numbers; turbulence has organised structure, so it does not. Multiplied by $-\rho$ they have units of stress, hence Reynolds stresses.

## 4. The closure problem

In 3D the $x$ equation also gains $\overline{u'w'}$, and the $y$ and $z$ equations three terms each; since $\overline{u'v'}=\overline{v'u'}$ and so on, there are six independent Reynolds stresses. The count is now:

| | Equations | Unknowns |
|---|---|---|
| Laminar Navier–Stokes | 4 (continuity, 3 momentum) | 4 ($u$, $v$, $w$, $p$) |
| Reynolds-averaged | 4 | 10 ($\bar u$, $\bar v$, $\bar w$, $\bar p$ and 6 stresses) |

Exact transport equations can be derived for the Reynolds stresses, but they contain triple products of fluctuations, giving of the order of a hundred unknowns, and the next level adds more again. No number of derived equations closes the system, so at some point a physical guess, a model, has to be made. This is the turbulence closure problem, and it is why engineering CFD has no exact treatment of turbulence. Calibrating against direct numerical simulation or using machine learning to tune or choose models does not remove the closure step; only solving the original equations directly would, perhaps on a quantum computer, which is not expected any time soon.

## 5. The eddy-viscosity hypothesis

The most common approach copies the Newtonian fluid of [[SESA2029 A7 - Governing Equations - Euler and Navier-Stokes|A7]]: suppose the Reynolds stress is proportional to the mean strain rate, as if eddies were large molecules. For the boundary-layer stress,

$$
-\overline{u'v'}=\nu_t\frac{\partial\bar u}{\partial y},
$$

so the extra term in the momentum equation becomes

$$
-\frac{\partial\,\overline{u'v'}}{\partial y}=\frac{\partial}{\partial y}\left(\nu_t\frac{\partial\bar u}{\partial y}\right),
$$

which looks like the viscous term with $\nu$ replaced by the kinematic eddy viscosity $\nu_t$. This solves nothing on its own, since $\nu_t$ is unknown and is a property of the flow, not of the fluid. It is the framework for most models: they differ only in how they find $\nu_t$ ([[Eddy-Viscosity Turbulence Models]]).

## 6. The models in the Fluent menu

The coefficients of every model were calibrated together against a set of standard flows, documented on the NASA Langley Turbulence Modeling Resource. Fluent allows the coefficients to be changed, but they should be left alone, because the model would then no longer work for the flat plate, the jet and the other cases it was calibrated on.

Spalart–Allmaras (Boeing, early 1990s) adds a single transport equation for a modified eddy viscosity $\tilde\nu$, with terms that produce, destroy and move it around. It grew out of boundary-layer models that worked well in external aerodynamics and was calibrated on the flows round commercial aircraft: leading edges, pressure gradients, wing–fuselage junctions. It was built systematically, starting from simple flows, with each new term (a compressibility or curvature correction, say) made to vanish in the cases the model already handled. It is robust, cheap because it has only one extra unknown, and good for attached flows and simple separation, but it struggles with free shear layers and reattachment. $\tilde\nu$ was designed to vary nearly linearly near the wall, so SA tolerates $y_1^+<5$; some implementations add a wall function for $y_1^+>30$.

$k$–$\varepsilon$ (Launder and Spalding, Imperial College, late 1960s) was the first practical model and long the most common. The turbulence kinetic energy

$$
k=\tfrac12\left(\overline{u'^2}+\overline{v'^2}+\overline{w'^2}\right)
$$

has an exact transport equation with production, diffusion and dissipation terms; a second equation for the dissipation rate $\varepsilon$ completes it, and

$$
\nu_t=C_\mu\frac{k^2}{\varepsilon},
\qquad
C_\mu=0.09.
$$

The $k$ equation can be derived exactly from the Navier–Stokes equations (its unknown terms are then modelled), but the $\varepsilon$ equation is essentially postulated, and that is where the weakness lies. It is recommended only for flows without strong pressure gradients, streamline curvature or separation. It came from automotive, nuclear and general engineering rather than aerodynamics, but works reasonably for aerodynamics, and is often used with a wall function when the grid cannot reach the wall: first point at $y_1^+>30$ and not beyond a few hundred.

$k$–$\omega$ (1980s) replaces $\varepsilon$ by the specific dissipation rate $\omega\propto\varepsilon/k$. It is better behaved near the wall, needs $y_1^+\approx1$ or below, and is less good away from it; in particular its predictions are sensitive to the assumed free-stream $\omega$, whereas $k$–$\varepsilon$ is not.

SST (Menter) blends the two with a switching function: $k$–$\omega$ near the wall, $k$–$\varepsilon$ in the free stream. It has had the most development of any model over the last twenty years. For aerodynamic work the choice is Spalart–Allmaras or $k$–$\omega$ SST.

Reynolds-stress models abandon the eddy viscosity and solve six equations for the stresses plus one for the dissipation rate. That makes ten stored variables against four for SA ($u$, $v$, $w$ and $\tilde\nu$), with slow convergence and a tendency to blow up in parts of the flow, but they can give better results in flows with strong streamline curvature or swirl, where two-equation models fail. In practice they have not become robust enough for general engineering use.

Two further families are transition models, recent additions that can just about compute a laminar layer followed by transition, which work in high-disturbance turbomachinery but poorly in external aerodynamics because they do not model the physics of transition; and unsteady scale-resolving methods (LES, DES), covered in [[SESA2029 A11 - CFD Errors, Verification, Validation and Mesh Quality|A11]].

| Model | Extra equations | Eddy viscosity from | Wall treatment |
|---|---|---|---|
| Spalart–Allmaras | 1 ($\tilde\nu$) | $\tilde\nu$ | $y_1^+<5$ (wall function versions $>30$) |
| $k$–$\varepsilon$ | 2 ($k$, $\varepsilon$) | $0.09k^2/\varepsilon$ | wall function, $30<y_1^+\lesssim200$ |
| $k$–$\omega$ | 2 ($k$, $\omega$) | $k/\omega$ | $y_1^+\lesssim1$ |
| SST | 2 (blended) | blended | $y_1^+\lesssim1$ |
| Reynolds stress | 7 | none: stresses solved directly | wall-resolved |

### What you need to know

The examinable points: the Reynolds decomposition and how it produces the Reynolds stresses; why no number of derived equations closes the system; the eddy viscosity for a simple boundary layer; and how the various models try to close the system. No model is perfect, and different models give different answers for the same flow, which you may see in the turbulent boundary-layer lab. Turbulence and transition modelling are the two big physical unknowns in predicting the flow round aircraft and rockets, so CFD needs an expert user who can tell when grid refinement will help and when the model is the limit.

## Worked examples

### Reynolds averaging of hot-wire samples

*(Suggested, not lecturer-set.)* Eight simultaneous samples of $u$ and $v$ (m/s) from an X-wire probe in a boundary layer, at equal time intervals:

| Sample | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 |
|---|---|---|---|---|---|---|---|---|
| $u$ | 11.0 | 9.4 | 10.6 | 8.8 | 11.4 | 9.6 | 10.2 | 9.0 |
| $v$ | −0.4 | 0.5 | −0.2 | 0.6 | −0.5 | 0.3 | −0.1 | 0.6 |

The discrete average replaces the integral: $\bar u=80.0/8=10.0$ m/s and $\bar v=0.8/8=0.10$ m/s. The fluctuations are

$$
u'=(1.0,-0.6,0.6,-1.2,1.4,-0.4,0.2,-1.0),
\qquad
v'=(-0.5,0.4,-0.3,0.5,-0.6,0.2,-0.2,0.5),
$$

each summing to zero, as $\overline{\phi'}=0$ requires. Their products are

$$
u'v'=(-0.50,-0.24,-0.18,-0.60,-0.84,-0.08,-0.04,-0.50),
$$

every one negative, so

$$
\overline{u'v'}=\frac{-2.98}{8}=-0.3725\ \mathrm{m^2/s^2}.
$$

With $\rho=1.2$ kg/m³ the Reynolds shear stress is $-\rho\overline{u'v'}=0.447$ Pa. The physics is in the signs: fluid moving up from the wall ($v'>0$) brings slow fluid ($u'<0$), and fluid moving down brings fast fluid, so the product is negative in every sample here (in general only the average need be negative). That is momentum being carried towards the wall by the eddies, which is what a shear stress is. If the mean gradient at the probe is $\partial\bar u/\partial y=200\ \mathrm s^{-1}$, the eddy viscosity defined in [[#5. The eddy-viscosity hypothesis]] is

$$
\nu_t=\frac{-\overline{u'v'}}{\partial\bar u/\partial y}=\frac{0.3725}{200}=1.86\times10^{-3}\ \mathrm{m^2/s}\approx124\,\nu.
$$

> [!check] Not zero, and not small
> The correlation coefficient of $u$ and $v$ in these samples is $-0.99$. Uncorrelated fluctuations would give $\overline{u'v'}\approx0$; these give a stress of 0.45 Pa, comparable to the wall stress of the plate below, 1.75 Pa, rather than negligible.

### Near-wall cells and the eddy viscosity

*(Suggested, not lecturer-set.)* The flat plate is that of [[SESA2029 A1 - Digital Design and the Role of CFD and FEA#First-cell height for a turbulent flat plate|A1]]: air at 30 m/s, $x=1$ m, $\nu=1.5\times10^{-5}$ m²/s, $\rho=1.2$ kg/m³. Then $Re_x=2\times10^6$, $C_f=0.059Re_x^{-1/5}=0.00324$, $\tau_w=1.75$ Pa, $u_\tau=1.21$ m/s and $\delta=21$ mm. The first-cell heights, from $y_1=y_1^+\nu/u_\tau$, are:

| $y_1^+$ | $y_1$ | Strategy |
|---|---|---|
| 1 | 0.012 mm | resolved (SA, SST) |
| 30 | 0.37 mm | lower limit for wall functions |
| 200 | 2.48 mm | upper limit: already 12 % of $\delta$ |

In the log layer the eddy viscosity that reproduces the log law follows from the near-wall stress balance. The total shear stress is nearly constant at $\tau_w$, and the turbulent part dominates, so

$$
\rho\,\nu_t\frac{d\bar u}{dy}\approx\rho u_\tau^2.
$$

The log law $u^+=\kappa^{-1}\ln y^++C$ has slope

$$
\frac{d\bar u}{dy}=\frac{u_\tau}{\kappa y}.
$$

Substituting gives

$$
\nu_t=\kappa u_\tau y,
\qquad
\frac{\nu_t}{\nu}=\kappa y^+.
$$

At $y^+=100$ ($y=1.24$ mm) the eddy viscosity is already $0.4\times100=40$ times the molecular viscosity, and at the edge of the log region, about $0.15\delta=3.1$ mm or $y^+=250$, it is 100 times. That is why the molecular term is negligible across most of a turbulent boundary layer and why the model for $\nu_t$ controls the answer.

## Links

- Parent: [[SESA2029 Digital Aerospace Methods Hub]]
- Previous: [[SESA2029 A7 - Governing Equations - Euler and Navier-Stokes]]
- Next: [[SESA2029 A9 - Finite Volume Method]]
- Concepts: [[Reynolds Averaging and the Closure Problem]] · [[Eddy-Viscosity Turbulence Models]] · [[First-Cell Height and y-plus]] · [[Law of the Wall]]
- Boundary layers: [[SESA2022 T2 - Boundary Layers]] · [[Boundary Layer Separation]]
- Scale-resolving methods: [[DNS, LES and Scale-Resolving Simulation]]

## Sources

- `All_lectures_as_delivered.pdf`, L9, pp. 113–129 (and L2, pp. 28–31, on $y^+$), with transcript `SESA2029 Lecture 2025-10-30.txt` (Prof N. Sandham)
- NASA Langley Turbulence Modeling Resource, for the standard model forms
- Worked examples recomputed in Python. Figures: `01 - Notes/Figures/generate_dam_a8_figures.py`

## Self-study tasks

### Core

- [ ] Derive the extra terms in the averaged $x$-momentum equation, starting from $\partial(uv)/\partial y$ (2025-10-30, ll. 211–245, listed as need-to-know at ll. 451–460). → [[#3. The Reynolds stresses]]
- [ ] Explain the closure problem by counting equations and unknowns (ll. 251–275). → [[#4. The closure problem]]
- [ ] Define the eddy viscosity for a simple boundary layer and say how SA, $k$–$\varepsilon$, $k$–$\omega$/SST and Reynolds-stress models find it (ll. 276–455). → [[#5. The eddy-viscosity hypothesis]] · [[#6. The models in the Fluent menu]]
- [ ] Turbulent boundary-layer lab: compare your profile with the log law, check $y_1^+$, and try a second turbulence model if time allows (ll. 76–80, 141–150, 495–500). → [[#1. The turbulent boundary layer in wall units]]
- [ ] Short explain-questions on turbulence (example sheet). → [[SESA2029 CFD Worked Examples#Q14: Short explain-questions (model answers)|Worked examples Q14]]

### Further practice

- [ ] Prove the averaging rules from the definition of the average, including $\overline{\bar\phi\psi'}=0$. → [[#2. Reynolds averaging]]
- [ ] Find the first-cell heights for $y_1^+=1$, 30 and 200 on a flat plate and show $\nu_t/\nu=\kappa y^+$ in the log layer (suggested, not lecturer-set). → [[#Near-wall cells and the eddy viscosity]]
- [ ] Average a set of $u$, $v$ samples and find the Reynolds shear stress and the eddy viscosity (suggested, not lecturer-set). → [[#Reynolds averaging of hot-wire samples]]

## Transcript and slide slips

> [!warning] Lecture slip (2025-10-30, ll. 201–205)
> Where: [[#3. The Reynolds stresses]].
>
> Reynolds is said to have done this "from 1889 when he was doing the pipe experiments". The pipe-flow experiments that separated laminar from turbulent flow were published in 1883; the averaged equations came in his 1895 paper.

> [!warning] Slide slips: model variables (L9 slides 9 and 13)
> Where: [[#6. The models in the Fluent menu]].
>
> Slide 9 describes the Spalart–Allmaras variable $\tilde\nu$ as "the molecular dynamic viscosity". It is a modified kinematic eddy viscosity, the model's own transport variable, from which $\nu_t$ is computed; the molecular viscosity is a fluid property and needs no equation. Slide 13 writes the $k$–$\omega$ eddy viscosity as $\mu_t=k/\omega$; with $k$ in m²/s² and $\omega$ in s⁻¹ that has the units of a kinematic viscosity, so it is $\nu_t=k/\omega$ (or $\mu_t=\rho k/\omega$).

