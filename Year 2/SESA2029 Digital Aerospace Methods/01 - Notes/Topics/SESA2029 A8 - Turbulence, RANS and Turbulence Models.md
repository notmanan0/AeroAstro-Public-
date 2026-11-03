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
> - **Practise:** [[#4. The closure problem]] · [[#Worked example: near-wall cells and the eddy viscosity]]

This lecture opened with a reply to a class survey that the lectures felt disconnected from the labs (2025-10-30, ll. 1–70). Prof Sandham's answer is that the lectures are a short course in numerical analysis, with its own exam (Part A of the summer paper, with FEA as Part B), and that the coursework report is where the two meet: the grid studies need the order of accuracy from the Taylor-series lectures, the Fluent residual is the imbalance of the discrete equations from the iterative-methods lecture, and the boundary-layer lab compares a laminar Navier–Stokes solution with Blasius. Turbulence is the biggest limitation of CFD, because nobody knows for sure how it should be modelled, which is also why expert engineers will still be needed to run CFD for decades.

In Fluent terms, the wing lab ticks inviscid (Euler, slip walls, no boundary layers), the laminar boundary-layer lab ticks laminar (the full steady Navier–Stokes equations), and the turbulent lab ticks Spalart–Allmaras, one of the models below (ll. 71–95).

The physical picture of turbulence is an energy cascade. Energy is fed in at the largest scales, the width of a jet or the thickness of a boundary layer, by the mean shear working on the flow. Large eddies interact, set up strain fields and stretch vorticity into smaller eddies, which interact again to form smaller ones still, until at the Kolmogorov microscales viscosity turns the motion into heat (ll. 96–120). A dye released in a jet shows the result: separated at first, then folded and mixed by eddies of every size until it is a uniform pale distribution downstream.

## 1. The turbulent boundary layer in wall units

This repeats the near-wall scaling from [[SESA2029 A1 - Digital Design and the Role of CFD and FEA|A1]] (ll. 116–160). The wall shear stress $\tau_w=\mu\,(\partial u/\partial y)_w$ defines a friction velocity and wall units:

$$
u_\tau=\sqrt{\frac{\tau_w}{\rho}},
\qquad
u^+=\frac{u}{u_\tau},
\qquad
y^+=\frac{y\,u_\tau}{\nu}.
$$

In these variables, profiles measured at different stations, and even in different pressure gradients, collapse on one curve near the wall. That is an empirical fact from experiments, "not really a theory, just a way of collapsing the data" (ll. 131–140). Close to the wall is the viscous sublayer, $u^+=y^+$; further out is the log law

$$
u^+=2.5\ln y^++5.24,
$$

where $2.5=1/\kappa$ with the von Kármán constant $\kappa=0.4$ (the constants vary slightly between sources); between them is a buffer layer, and the outer part of the profile depends on the pressure gradient ([[Law of the Wall]]).

![[dam_law_of_the_wall_y1plus.png|640]]

The position of the first grid point in these units, $y_1^+$, decides how the model must treat the wall (ll. 146–160, 341–355, 391–400). A wall-resolved calculation puts it in the sublayer, below 5 and ideally near 1, so the profile is captured by the grid. A wall-function model assumes the first point lies on the log law and needs $30<y_1^+\lesssim200$; even then 15 to 20 points are needed inside the boundary layer, which is what sets the upper limit. Between 5 and 30 neither assumption holds and "you're going to get the wrong answer". In the lab, plot $y_1^+$ after solving and refine if needed ([[First-Cell Height and y-plus]]).

## 2. Reynolds averaging

A turbulent signal, for example from a hot-wire probe in a boundary layer, fluctuates about a mean (ll. 156–180). Define the average over a sample time $T$, long compared with the eddy time scale,

$$
\bar\phi(x_i)=\frac1T\int_0^T\phi(x_i,t)\,dt,
$$

and split the signal into the mean and the fluctuation:

$$
\phi(x_i,t)=\bar\phi(x_i)+\phi'(x_i,t).
$$

In a simulation the average can also be taken over a periodic direction in space. (A hot wire is a very thin heated wire in a Wheatstone bridge; its out-of-balance voltage, once calibrated, gives the velocity. The fourth-year experimental aerodynamics module covers it.)

![[dam_reynolds_decomposition.png|680]]

The averaging rules follow from the integral (ll. 181–200). Averaging the decomposition gives $\bar{\bar\phi}+\overline{\phi'}=\bar\phi$, and since an average of an average is the average itself, $\overline{\phi'}=0$. A constant comes outside the integral, $\overline{c\phi}=c\bar\phi$; averages of sums separate, $\overline{\phi+\psi}=\bar\phi+\bar\psi$; a product of averages is unchanged, $\overline{\bar\phi\bar\psi}=\bar\phi\bar\psi$; and differentiation and averaging commute, $\overline{\partial\phi/\partial s}=\partial\bar\phi/\partial s$. A mean times a fluctuation averages to zero, $\overline{\bar\phi\psi'}=\bar\phi\,\overline{\psi'}=0$. The exception is the product of two fluctuations: $\overline{\phi'\psi'}$ is not zero in general.

## 3. The Reynolds stresses

Reynolds substituted the decomposition into the Navier–Stokes equations and averaged them (ll. 201–210). Take the term $\partial(uv)/\partial y$, which matters in boundary layers (ll. 211–240):

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

Doing the same to every term of the 2D $x$-momentum equation reproduces the original equation with bars on everything, plus two extra terms (ll. 236–245):

$$
\frac{\partial\bar u}{\partial t}+\frac{\partial(\bar u\bar u)}{\partial x}+\frac{\partial(\bar u\bar v)}{\partial y}+\frac1\rho\frac{\partial\bar p}{\partial x}
=\nu\left(\frac{\partial^2\bar u}{\partial x^2}+\frac{\partial^2\bar u}{\partial y^2}\right)-\frac{\partial\,\overline{u'u'}}{\partial x}-\frac{\partial\,\overline{u'v'}}{\partial y}.
$$

The new terms are averages of the turbulence, and nobody knows what they are. A student asked whether $\overline{u'v'}$ is zero: only if $u'$ and $v'$ were uncorrelated random numbers, and turbulence has organised structure, so it is not (ll. 245–255). Multiplied by $-\rho$ they have units of stress, hence Reynolds stresses (ll. 271–275).

> [!warning] Lecture slip (2025-10-30, ll. 201–205)
> Reynolds is said to have done this "from 1889 when he was doing the pipe experiments". The pipe-flow experiments that separated laminar from turbulent flow were published in 1883; the averaged equations came in his 1895 paper.

## 4. The closure problem

In 3D the $x$ equation also gains $\overline{u'w'}$, and the $y$ and $z$ equations three terms each; since $\overline{u'v'}=\overline{v'u'}$ and so on, there are six independent Reynolds stresses (ll. 251–260). The count is now:

| | Equations | Unknowns |
|---|---|---|
| Laminar Navier–Stokes | 4 (continuity, 3 momentum) | 4 ($u$, $v$, $w$, $p$) |
| Reynolds-averaged | 4 | 10 ($\bar u$, $\bar v$, $\bar w$, $\bar p$ and 6 stresses) |

Exact transport equations can be derived for the Reynolds stresses, but they contain triple products of fluctuations, giving of the order of a hundred unknowns, and the next level adds more again (ll. 261–275). You can never derive enough equations to close the system, so at some point a physical guess, a model, has to be made. This is the turbulence closure problem, and it is why engineering CFD has no exact treatment of turbulence. Calibrating against direct numerical simulation or using machine learning to tune or choose models does not remove the closure step; only solving the original equations directly would, perhaps on a quantum computer, and "no one's holding their breath" (ll. 476–495).

## 5. The eddy-viscosity hypothesis

The most common approach copies the Newtonian fluid of [[SESA2029 A7 - Governing Equations - Euler and Navier-Stokes|A7]]: suppose the Reynolds stress is proportional to the mean strain rate, as if eddies were large molecules (ll. 276–295). For the boundary-layer stress,

$$
-\overline{u'v'}=\nu_t\frac{\partial\bar u}{\partial y},
$$

so the extra term in the momentum equation becomes

$$
-\frac{\partial\,\overline{u'v'}}{\partial y}=\frac{\partial}{\partial y}\left(\nu_t\frac{\partial\bar u}{\partial y}\right),
$$

which looks like the viscous term with $\nu$ replaced by the kinematic eddy viscosity $\nu_t$. This solves nothing on its own, since $\nu_t$ is unknown and is a property of the flow, not of the fluid. It is the framework for most models: they differ only in how they find $\nu_t$ ([[Eddy-Viscosity Turbulence Models]]).

## 6. The models in the Fluent menu

The coefficients of every model were calibrated together against a set of standard flows, documented on the NASA Langley Turbulence Modeling Resource. Fluent lets you change them, but "you should really never change those constants": the model would then no longer work for the flat plate, the jet and the other cases it was calibrated on (ll. 301–315).

Spalart–Allmaras (Boeing, early 1990s) adds a single transport equation for a modified eddy viscosity $\tilde\nu$, with terms that produce, destroy and move it around (ll. 291–355). It grew out of boundary-layer models that worked well in external aerodynamics and was calibrated on the flows round commercial aircraft: leading edges, pressure gradients, wing–fuselage junctions. It was built systematically, starting from simple flows, with each new term (a compressibility or curvature correction, say) made to vanish in the cases the model already handled. It is robust, cheap because it has only one extra unknown, and good for attached flows and simple separation, but it struggles with free shear layers and reattachment. $\tilde\nu$ was designed to vary nearly linearly near the wall, so SA tolerates $y_1^+<5$; some implementations add a wall function for $y_1^+>30$.

$k$–$\varepsilon$ (Launder and Spalding, Imperial College, late 1960s) was the first practical model and long the most common (ll. 356–400). The turbulence kinetic energy

$$
k=\tfrac12\left(\overline{u'^2}+\overline{v'^2}+\overline{w'^2}\right)
$$

has an exact transport equation with production, diffusion and dissipation terms; a second equation for the dissipation rate $\varepsilon$ completes it, and

$$
\nu_t=C_\mu\frac{k^2}{\varepsilon},
\qquad
C_\mu=0.09.
$$

The $k$ equation is sound, but the $\varepsilon$ equation is "just made up", and that is where the weakness lies. It came from automotive, nuclear and general engineering rather than aerodynamics, but works reasonably for aerodynamics, and is often used with a wall function when the grid cannot reach the wall: first point at $y_1^+>30$ and not beyond a few hundred.

$k$–$\omega$ (1980s) replaces $\varepsilon$ by the specific dissipation rate $\omega\propto\varepsilon/k$ (ll. 400–410). It is better behaved near the wall, needs $y_1^+\approx1$ or below, and is less good away from it; in particular its predictions are sensitive to the assumed free-stream $\omega$, whereas $k$–$\varepsilon$ is not.

SST (Menter) blends the two with a switching function: $k$–$\omega$ near the wall, $k$–$\varepsilon$ in the free stream (ll. 411–425). It has had the most development of any model over the last twenty years. For aerodynamic work the choice is Spalart–Allmaras or $k$–$\omega$ SST.

Reynolds-stress models abandon the eddy viscosity and solve six equations for the stresses plus one for the dissipation rate (ll. 421–455). That makes ten stored variables against four for SA ($u$, $v$, $w$ and $\tilde\nu$ in the lecturer's count), with slow convergence and a tendency to blow up in parts of the flow, but they can handle strongly swirling flows where two-equation models fail. They have "never been made to work properly" for general use.

Two other entries are mentioned for later (ll. 436–450): transition models, recent additions that can just about compute a laminar layer followed by transition, which work in high-disturbance turbomachinery but poorly in external aerodynamics because they do not model the physics of transition; and unsteady scale-resolving methods (LES, DES), covered in [[SESA2029 A11 - CFD Errors, Verification, Validation and Mesh Quality|A11]].

| Model | Extra equations | Eddy viscosity from | Wall treatment |
|---|---|---|---|
| Spalart–Allmaras | 1 ($\tilde\nu$) | $\tilde\nu$ | $y_1^+<5$ (wall function versions $>30$) |
| $k$–$\varepsilon$ | 2 ($k$, $\varepsilon$) | $0.09k^2/\varepsilon$ | wall function, $30<y_1^+\lesssim200$ |
| $k$–$\omega$ | 2 ($k$, $\omega$) | $k/\omega$ | $y_1^+\lesssim1$ |
| SST | 2 (blended) | blended | $y_1^+\lesssim1$ |
| Reynolds stress | 7 | none: stresses solved directly | wall-resolved |

### What you need to know

The lecture closes with the examinable points (ll. 451–495): the Reynolds decomposition and how it produces the Reynolds stresses; why the closure problem means you can never derive enough equations; the eddy viscosity for a simple boundary layer; and how the various models try to close the system. No model is perfect, and different models give different answers for the same flow, which you may see in the turbulent boundary-layer lab. Turbulence and transition modelling are the two big physical unknowns in predicting the flow round aircraft and rockets, so CFD needs an expert user who can tell when grid refinement will help and when the model is the limit.

## Worked example: near-wall cells and the eddy viscosity

Use the flat plate of [[SESA2029 A1 - Digital Design and the Role of CFD and FEA#First-cell height for a turbulent flat plate|A1]]: air at 30 m/s, $x=1$ m, $\nu=1.5\times10^{-5}$ m²/s, $\rho=1.2$ kg/m³. Then $Re_x=2\times10^6$, $C_f=0.059Re_x^{-1/5}=0.00324$, $\tau_w=1.75$ Pa, $u_\tau=1.21$ m/s and $\delta=21$ mm. The first-cell heights, from $y_1=y_1^+\nu/u_\tau$, are:

| $y_1^+$ | $y_1$ | Strategy |
|---|---|---|
| 1 | 0.012 mm | resolved (SA, SST) |
| 30 | 0.37 mm | lower limit for wall functions |
| 200 | 2.48 mm | upper limit: already 12 % of $\delta$ |

In the log layer, what eddy viscosity reproduces the log law? This step is not in the lecture. Near the wall the total shear stress is nearly constant at $\tau_w$, and the turbulent part dominates, so

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

At $y^+=100$ ($y=1.24$ mm) the eddy viscosity is already $0.4\times100=40$ times the molecular viscosity, recomputed in Python. That is why the molecular term is negligible across most of a turbulent boundary layer and why the model for $\nu_t$ controls the answer.

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
- Worked example recomputed in Python

## Self-study tasks

### Core

- [ ] Derive the extra terms in the averaged $x$-momentum equation, starting from $\partial(uv)/\partial y$ (2025-10-30, ll. 211–245, listed as need-to-know at ll. 451–460). → [[#3. The Reynolds stresses]]
- [ ] Explain the closure problem by counting equations and unknowns (ll. 251–275). → [[#4. The closure problem]]
- [ ] Define the eddy viscosity for a simple boundary layer and say how SA, $k$–$\varepsilon$, $k$–$\omega$/SST and Reynolds-stress models find it (ll. 276–455). → [[#5. The eddy-viscosity hypothesis]] · [[#6. The models in the Fluent menu]]
- [ ] Turbulent boundary-layer lab: compare your profile with the log law, check $y_1^+$, and try a second turbulence model if time allows (ll. 76–80, 141–150, 495–500). → [[#1. The turbulent boundary layer in wall units]]
- [ ] Short explain-questions on turbulence (example sheet). → [[SESA2029 CFD Worked Examples#Q14: Short explain-questions (model answers)|Worked examples Q14]]

### Further practice

- [ ] Prove the averaging rules from the definition of the average, including $\overline{\bar\phi\psi'}=0$. → [[#2. Reynolds averaging]]
- [ ] Find the first-cell heights for $y_1^+=1$, 30 and 200 on a flat plate and show $\nu_t/\nu=\kappa y^+$ in the log layer (suggested, not lecturer-set). → [[#Worked example: near-wall cells and the eddy viscosity]]
