---
title: "SESA1016 T9 - Describing Flow and the Material Derivative"
module: "SESA1016 Thermofluids"
type: topic
stream: "Part C: Fluid Motion and Inviscid Flow"
order: 9
tags: [sesa1016, kinematics, material-derivative, streamlines]
aliases: ["Describing Flow", "Flow Kinematics"]
date: 2026-09-25
status: lectured
coverage: "Lectures of 10 Mar 2025 (ll. 1–575: fluid particle, Lagrangian and Eulerian viewpoints, scalar and vector fields, steady and unsteady flow, partial derivatives, pathlines, streaklines, streamlines, stagnation points) and 11 Mar 2025 (ll. 104–690: streamtubes and flow classifications, Reynolds number, compressibility and Mach number); Chapter 9 in full. The material-derivative section joins Chapter 9 §9.4 to the acceleration of T10 and is not lectured under that name."
parent: ["[[SESA1016 Thermofluids Hub]]"]
prerequisites: ["[[SESA1016 T8 - Hydrostatics]]"]
next_topics: ["[[SESA1016 T10 - Euler and Bernoulli Equations]]"]
key_concepts: ["[[Material Derivative]]", "[[Streamline, Pathline and Streakline]]", "[[Reynolds Number]]"]
tutorial_sheets: ["[[SESA1016 Problem Sheet 07 - Describing Flow and Euler Equation Solutions]]"]
sources: ["02 - Sources/Lectures/Chapter 9.pdf", "02 - Sources/Lectures/SESA1016 Lecture 2025-03-10.txt", "02 - Sources/Lectures/SESA1016 Lecture 2025-03-11.txt", "02 - Sources/Tutorial Sheets/Problem Sheet 07 - Describing Flow and the Euler Equation.pdf"]
---

# SESA1016 T9 - Describing Flow and the Material Derivative

> [!abstract] Summary
> A moving fluid can be described by following individual fluid particles (Lagrangian) or by giving every flow quantity as a field over space and time (Eulerian), which is what CFD does. Fields are visualised as heat maps and contours (scalars) or quiver plots, pathlines, streaklines and streamlines (vectors); the three kinds of line coincide only in steady flow. Flows are then classified (steady, uniform, internal, quasi-1D, 2D, laminar or turbulent by Reynolds number, incompressible when $Ma<0.3$ because $\Delta\rho/\rho\sim Ma^2$). Following a particle through an Eulerian field gives the material derivative $D/Dt=\partial/\partial t+V\,\partial/\partial x$.

> [!summary]- Exam use: quick path
> - **Use it when:** a velocity field is given and you must sketch or find streamlines, decide whether the flow is steady, compare path-, streak- and streamlines, or judge from $Re$ and $Ma$ whether the flow is laminar or turbulent, compressible or not.
> - **Assumptions:** continuum; for streamlines from $dy/dx=v_y/v_x$, a 2D field at a fixed instant.
> - **Method:** 1. Write the components $v_x(x,y,t)$, $v_y(x,y,t)$; if $t$ appears, the flow is unsteady. 2. For streamlines solve $dy/dx=v_y/v_x$ at fixed $t$. 3. For pathlines solve $d\vec x_P/dt=\vec V(\vec x_P,t)$ from a start point. 4. For classification compute $Re=\rho VL/\mu$ and $Ma=V/c$ with sensible scales. 5. Read speed from streamline spacing: converging streamlines mean faster flow (incompressible).
> - **Common mistakes:** calling a flow with zero $\partial V/\partial t$ "stationary" (it may move steadily); treating smoke lines in unsteady flow as pathlines (they are streaklines).
> - **Practise:** [[#Worked example - streamlines near a corner]] · [[SESA1016 Problem Sheet 07 - Describing Flow and Euler Equation Solutions]] Q7.1, Q7.5, Q7.6

Mechanics describes a projectile by following it: its position, velocity and acceleration as functions of time, driven by the forces on it. A fluid could be described the same way, by tagging small blobs of it and following each, but there are effectively infinitely many blobs, and each one stretches and twists as it moves. Leonhard Euler suggested looking at the problem differently: stop following the fluid and instead say, at each point in space and each instant, what the temperature, pressure and velocity are there. That is a field, and fields are what fluid dynamicists, experimenters and CFD codes all work with.

Fields need ways of being seen. A temperature field is a single number at each point and can be drawn as colours or contour lines; a velocity field is a vector at each point and needs arrows, or lines that follow the flow. There are three natural lines (the path of one particle, the trail of smoke from one point, and the curve the velocity is tangent to) and in a steady flow they are the same, but in an unsteady one they are not, which matters when interpreting any flow-visualisation photograph.

Flows are also classified, because the right model depends on the class: steady or unsteady, inside a duct or around a body, effectively one- or two-dimensional, laminar or turbulent, compressible or not. The last two are decided by the Reynolds and Mach numbers ([[SESA1016 T6 - Dimensional Analysis and Similarity|T6]], [[SESA1016 T7 - Fluid Properties and Viscosity|T7]]).

---

## 1. The fluid particle

A **fluid particle** is a small quantity of fluid with a fixed identity: it is always made of the same molecules, as if they had been tagged, so its mass is fixed, but its shape and volume may change as it moves and its pressure, density and temperature change (10 Mar, ll. 42–80). Its size $dl$ is small compared with any length scale of the flow (the size of the vortices shed by an aerofoil scale with the chord $c$, say), so properties are uniform across it. But it is still much larger than the mean free path $\ell$, so it contains enough molecules for the continuum averages of [[SESA1016 T1 - Thermodynamic Systems, Properties and State#3. The continuum assumption|T1]] to make sense:

$$
\ell\ll dl\ll c
$$

## 2. Lagrangian and Eulerian viewpoints

In the **Lagrangian** viewpoint (after Lagrange) the flow is divided into many fluid particles, each is tracked, and its properties are recorded along its path: a particle might be at 25 °C at time $t_0$ and at 40 °C at $t_1$ further along. This is the approach of particle mechanics. It is useful in some measurements, such as Lagrangian particle tracking, which follows thousands of tracer particles, but a complete description of a flow this way is impractical (10 Mar, ll. 83–142).

In the **Eulerian** viewpoint (after Euler) the particles are forgotten. Every quantity is given as a field over a fixed region of space, such as $T(x,y)$, the temperature at each point $(x,y)$. Different particles may occupy the same point at different times; that does not matter. CFD works this way: the domain is divided into many small cells (billions, for complex flows) and the temperature, velocity and pressure are solved for in each, so finer cells resolve finer detail (10 Mar, ll. 143–192).

### Scalar fields

Temperature, pressure and density are **scalar fields**: one number at each point. They are visualised as a **heat map** (colour map), where each colour stands for a value read from a colour bar, or as a **contour plot**, where each line joins points with the same value, often labelled or coloured (10 Mar, ll. 193–214).

### Vector fields

Velocity needs both a magnitude and a direction. In the Lagrangian view a particle at position $\vec x_P(t)=x_P(t)\vec i+y_P(t)\vec j$ has velocity

$$
\vec V_P(t)=\frac{d\vec x_P}{dt}
$$

the ordinary kinematics of a point mass. In the Eulerian view the velocity is a **vector field**, given by its components, each of which is itself a scalar field:

$$
\vec V(x,y)=v_x(x,y)\,\vec i+v_y(x,y)\,\vec j
$$

The **velocity magnitude** (speed) is a scalar field, from Pythagoras:

$$
V(x,y)=|\vec V|=\sqrt{v_x^2+v_y^2}
$$

It says how fast particles move through each point, but not in which direction.

A vector field is drawn as a **quiver plot** (vector plot): an arrow at each point of a grid, pointing along the flow, with length proportional to the speed. The arrows can be coloured by speed or another quantity, and heat maps of $v_x$ or $v_y$ alone show, for example, where fluid moves up and where down (10 Mar, ll. 275–304).

### Steady and unsteady flow

Measure the speed $V_A(t)$ at a point A near an aerofoil. At a small angle of attack it does not change with time: every particle passing A has the same velocity. That is **steady** flow,

$$
\frac{\partial V_A}{\partial t}=0
$$

at every point. Steady does not mean at rest: a fluid at rest has $V=0$, while a steady flow can be fast. At a large angle of attack the aerofoil stalls, vortices are shed and $V_A$ fluctuates: the flow is **unsteady**, and the velocity field depends on time as well as position, $\vec V(x,y,t)$ (10 Mar, ll. 306–352).

## 3. Rates of change in space and time

A field such as the temperature in a nozzle during engine start-up, $T(x,t)$, can change with position and with time, so its rates of change are partial derivatives, written with $\partial$ (10 Mar, ll. 354–412).

Put one thermometer at a fixed $x$ and read it at $t$ and $t+\Delta t$. The **local rate of change** is

$$
\frac{\partial T}{\partial t}\approx\frac{T(x,t+\Delta t)-T(x,t)}{\Delta t}
$$

The two readings may belong to different particles passing the same point. A flow is steady when $\partial/\partial t$ of every quantity is zero everywhere.

Put two thermometers a small distance $\Delta x$ apart and read them at the same instant. The **spatial gradient** is

$$
\frac{\partial T}{\partial x}\approx\frac{T(x+\Delta x,t)-T(x,t)}{\Delta x}
$$

again involving different particles, now at the same time.

### Following a particle - the material derivative

Neither of these is the rate of change felt by a particle. A particle is at $x_P(t)$ and moves with the local velocity, $dx_P/dt=V$. The temperature it feels is $T(x_P(t),t)$. Over a short time $\Delta t$ the particle moves $\Delta x=V\Delta t$, and its temperature changes by

$$
\Delta T=T(x+V\Delta t,\,t+\Delta t)-T(x,t)
$$

To first order in small changes,

$$
\Delta T\approx\frac{\partial T}{\partial t}\Delta t+\frac{\partial T}{\partial x}V\Delta t
$$

Divide by $\Delta t$ and let it tend to zero. This is the **material derivative**, the rate of change following the particle:

$$
\boxed{\frac{DT}{Dt}=\frac{\partial T}{\partial t}+V\frac{\partial T}{\partial x}}
$$

The first term is the local change at a fixed point; the second, the **convective** change, comes from the particle being carried into a region with a different temperature. In a steady flow the first term vanishes but the second need not: a particle carried at 10 m/s along a duct whose wall heating gives a steady gradient of 50 K/m warms at $DT/Dt=10\times50=500$ K/s, though no thermometer fixed in the duct sees any change.

The same operator applied to the velocity itself gives the acceleration of a particle, $DV/Dt=\partial V/\partial t+V\,\partial V/\partial x$, the local plus convective acceleration along a streamline used in [[SESA1016 T10 - Euler and Bernoulli Equations|T10]]. In two or three dimensions the convective part has one term per direction, $D/Dt=\partial/\partial t+v_x\partial/\partial x+v_y\partial/\partial y$.

![[tf_flow_kinematics.png|900]]

## 4. Lines that visualise a flow

### Pathlines

A **pathline** is the trajectory of one fluid particle. Experimentally, seed the flow with neutrally buoyant tracer particles and take a long-exposure photograph: each particle draws its path, just as stars draw trails across a long-exposure photograph of the night sky. A short exposure shows only dots (10 Mar, ll. 416–440).

To compute one, start a particle at $\vec x_{P0}$ at time $t_0$ and solve the initial value problem

$$
\frac{d\vec x_P}{dt}=\vec V(\vec x_P(t),t),\qquad \vec x_P(t_0)=\vec x_{P0}
$$

which says the particle moves with the local flow velocity. Given the velocity field it can be integrated numerically, for example with the forward Euler method, $\vec x_P^{\,n+1}=\vec x_P^{\,n}+\Delta t\,\vec V(\vec x_P^{\,n},t_n)$. In unsteady flow, particles passing the same point at different times can follow different paths, and pathlines can cross: a particle can come back to where it was, or two particles from different places can arrive at the same point later.

### Streaklines

A **streakline** joins all the particles that have passed through one fixed point. Inject smoke or dye continuously at a point: at any instant the smoke trail is a streakline. The particle furthest from the source was released earliest. A single ordinary photograph shows it, because it is the set of particles at one instant (10 Mar, ll. 466–487). Smoke lines in a wind tunnel are streaklines.

### Streamlines

A **streamline** is a curve everywhere tangent to the velocity vector at one instant. Along it the flow direction is the tangent direction, so in 2D, a streamline $y(x)$ satisfies

$$
\frac{dy}{dx}=\frac{v_y}{v_x}
$$

with the field frozen at the chosen time. In unsteady flow the streamline picture changes from instant to instant, and streamlines do not then show where a particle will go.

Streamlines cannot cross. At a crossing point the velocity would have two directions at once. The only exception is where the velocity is exactly zero. Near the front of an aerofoil the **dividing streamline** separates fluid passing over the upper surface from fluid passing below; it ends on the surface at the **stagnation point**, where the fluid has been brought to rest, since it cannot pass through the surface (10 Mar, ll. 541–560).

### When the lines coincide

In **steady** flow all three are the same. Every particle released from a point follows the same trajectory, so the streakline from that point coincides with the pathline; and a particle always moves along the local velocity, which does not change, so the pathline is also a streamline. In **unsteady** flow they differ: particles released at different times follow different pathlines, and the streakline joining them looks like none of them (10 Mar, ll. 503–532).

![[tf_path_streak_lines.png|900]]

The figure shows this for a simple unsteady flow, $v_x=U$, $v_y=V_0\cos\omega t$: a uniform stream swinging up and down. At any instant the streamlines are parallel straight lines. Each pathline is a sine wave, $y=(V_0/\omega)\left[\sin\omega t-\sin\omega t_0\right]$ with $x=U(t-t_0)$. The streakline from the origin at time $t$, made of particles released at times $\tau=t-x/U$, is $y=(V_0/\omega)\left[\sin\omega t-\sin\omega(t-x/U)\right]$, a third, different curve.

### Streamtubes

A **streamtube** is a region bounded by streamlines (in 2D, the strip between two of them). No fluid crosses its walls, because the flow is everywhere tangent to them, so it behaves like a virtual pipe: all the fluid that enters it leaves through its far end (11 Mar, ll. 118–138).

That makes streamlines a speedometer. For incompressible flow (liquids, or gases at low Mach number), the velocity in a streamtube varies inversely with its cross-section, ([[SESA1016 T11 - Conservation of Mass|T11]]): where streamlines converge the fluid speeds up, where they spread out it slows down. Around an aerofoil, streamtubes narrow sharply over the leading edge of the suction side, where the speed peaks, and widen towards the stagnation point, where it falls to zero (11 Mar, ll. 139–212). For supersonic flow the relationship reverses.

## 5. Classifying flows

### Uniform and non-uniform

In **uniform** flow the velocity (magnitude and direction), and also the density, pressure and temperature if they are mentioned, is the same throughout a region: far upstream of an aerofoil, or across the inlet of an engine intake. Viscous flow in a thin pipe or a syringe needle is **non-uniform**: no-slip makes the velocity zero at the wall and largest on the axis (11 Mar, ll. 217–250).

### Internal and external

**Internal** flow is confined: intake ducts, rocket nozzles, flow through engine components and fuel systems, and in motorsport the brake-cooling ducts and side-pod intakes. **External** flow is around a body: wings, race cars, helmets.

### One-dimensional and quasi-one-dimensional

In a straight duct with parallel walls the velocity can be exactly along the axis, with no transverse component: **one-dimensional** (parallel) flow, which may still be non-uniform across the section. In a gently converging or diverging duct the velocity near the walls tilts with them, so $v_y\ne0$, but $v_y\ll v_x$. Neglecting $v_y$ and keeping only the axial velocity, while still allowing it to change along the duct as the area changes, is the **quasi-one-dimensional** assumption used for nozzles and intakes (11 Mar, ll. 274–308). It fails where the area changes abruptly.

### Two- and three-dimensional

Real flows are three-dimensional, like the flow round a golf ball, where $v_x$, $v_y$ and $v_z$ all matter. For a long slender body, such as a high-aspect-ratio wing, a tall building or a marine riser, the flow over most of the span (away from the tips) hardly varies in the spanwise direction $z$ and $v_z$ is small, so it can be treated as **two-dimensional**: the aerofoil section problem, as solved by XFOIL (11 Mar, ll. 309–361).

### Laminar and turbulent

In **laminar** flow the fluid moves in smooth layers (Latin *laminae*) sliding over each other. It is typically steady, mass, momentum and heat move between layers only by slow molecular diffusion, and many laminar flows have exact analytical solutions, Couette flow among them. A slowly pouring jet of thick oil is laminar. Lubrication, blood flow, microfluidics and laminar-flow wings depend on it.

In **turbulent** flow the motion is disordered and always unsteady, with eddies over a wide range of sizes. Turbulence mixes heat, mass and momentum very effectively: stirring milk into tea quickly makes turbulence and mixes them fast, stirring slowly does not (11 Mar, ll. 463–475). It is rarely tractable analytically and is studied by experiment and simulation. Most flows of interest in aerospace are turbulent.

Which one occurs is decided by the **Reynolds number**,

$$
\boxed{Re=\frac{\rho VL}{\mu}=\frac{VL}{\nu}}
$$

with $V$ and $L$ characteristic scales of the problem: usually the free-stream speed, and the diameter of a sphere or the chord of an aerofoil. Only the order of magnitude matters. It is the combination, not $V$, $L$ or $\nu$ separately, that decides the flow. Flow past a sphere is steady and laminar only for $Re<200$. Small, slow or very viscous flows are laminar; large, fast flows of low-viscosity gases are turbulent.

The Reynolds number compares inertia with viscous forces. The inertial force needed to change the momentum of fluid moving at $V$ over a region of size $L$ scales as $\rho V^2L^2$ (dynamic pressure times area), and the viscous force as shear stress times area, $\mu(V/L)L^2=\mu VL$ (compare $F=\mu AV/h$ in T7). Their ratio is

$$
\frac{\rho V^2L^2}{\mu VL}=\frac{\rho VL}{\mu}=Re
$$

When $Re$ is small, viscosity is strong enough to damp disturbances and the flow stays smooth; when it is large, viscosity cannot kill the small eddies and the flow becomes turbulent (11 Mar, ll. 581–615).

### Viscous and inviscid

In a **viscous** flow, viscous forces are important to the motion; this is always true in thin pipes, narrow channels and next to solid surfaces, laminar or turbulent. In an **inviscid** flow, viscosity hardly affects the motion. High-speed flow round streamlined bodies such as wings and fuselages can often be treated as inviscid for computing lift, which is the basis of second-year aerodynamics. [[SESA1016 T10 - Euler and Bernoulli Equations|T10]] makes this assumption.

### Compressible and incompressible

In **incompressible** flow a fluid particle may stretch, rotate and deform, but its volume, and so its density, stays constant. In **compressible** flow its volume and density change. The distinction belongs to the flow, set by its speed, not to the fluid: all fluids are compressible to some extent.

At low speed the relative change in density is set by the **Mach number** $Ma=V_\infty/c$:

$$
\frac{\Delta\rho}{\rho}\sim Ma^2
$$

The derivation starts from $\rho v=1$, since density and specific volume are reciprocals. Perturb both slightly:

$$
(\rho+\Delta\rho)(v+\Delta v)=1
$$

$$
\rho v+v\Delta\rho+\rho\Delta v+\Delta\rho\Delta v=1
$$

Use $\rho v=1$ and drop the product of two small perturbations:

$$
v\Delta\rho+\rho\Delta v\approx0
$$

$$
\frac{\Delta v}{v}=-\frac{\Delta\rho}{\rho}
$$

The bulk modulus is $E_v=-\Delta p/(\Delta v/v)$, so

$$
\frac{\Delta\rho}{\rho}=\frac{\Delta p}{E_v}
$$

Flow brought to rest in front of an obstacle changes its pressure by an amount of order the dynamic pressure, $\Delta p\sim\rho V_\infty^2$ (made precise by Bernoulli in [[SESA1016 T10 - Euler and Bernoulli Equations|T10]]), and from T7, $E_v=\rho c^2$. Therefore

$$
\frac{\Delta\rho}{\rho}\sim\frac{\rho V_\infty^2}{\rho c^2}=\frac{V_\infty^2}{c^2}=Ma^2
$$

Accepting density changes of up to 10 % means $Ma^2\le0.1$, $Ma\le0.3$. This is the usual threshold below which a flow is treated as incompressible: about 100 m/s in air at sea level. A Formula 1 car at 360 km/h (100 m/s) is right at that limit, with density changes of about 9 % round its wings (11 Mar, ll. 671–679).

---

## Worked examples

### Worked example - streamlines near a corner

The steady 2D field $\vec V=2x\,\vec i-2y\,\vec j$ models flow into a corner. Sketch the velocity vectors and find the streamlines (Problem Sheet 7, Q7.1).

At (1, 4), $\vec V=(2,-8)$ m/s, speed 8.2 m/s, pointing steeply down; at (4, 1), $\vec V=(8,-2)$, pointing mostly right. At the origin the velocity is zero: a stagnation point. Streamlines satisfy

$$
\frac{dy}{dx}=\frac{v_y}{v_x}=\frac{-2y}{2x}=-\frac{y}{x}
$$

Separate the variables:

$$
\frac{dy}{y}=-\frac{dx}{x}
$$

$$
\ln y=-\ln x+C
$$

$$
\boxed{xy=\text{const}}
$$

rectangular hyperbolae with the axes as asymptotes. Fluid comes down near the $y$ axis, turns, and leaves along the $x$ axis, speeding up as the streamlines crowd together near the wall $y=0$.

![[tf_corner_flow_streamlines.png|900]]

> [!check] Pathline by forward Euler
> The flow is steady, so a pathline must lie on a streamline. Starting at (1, 4) with $xy=4$ and integrating $d\vec x/dt=\vec V$ by forward Euler to $t=0.5$ s: with $\Delta t=0.1$ s the particle ends with $xy=3.26$, with $\Delta t=0.01$ s at $xy=3.92$ and with $\Delta t=10^{-4}$ s at $xy=3.999$. The exact solution is $x=e^{2t}$, $y=4e^{-2t}$, with $xy=4$ exactly. The error is first order in $\Delta t$, as expected for forward Euler.

### Worked example - Mach number at altitude

An aircraft cruises at 250 m/s at 10 000 m, where the air is at −50 °C. Find the speed of sound and Mach number, the Mach number at the same speed at sea level (15 °C), and the speed needed to go supersonic at altitude (Problem Sheet 7, Q7.6).

From [[SESA1016 T7 - Fluid Properties and Viscosity#Speed of sound|T7]], $c=\sqrt{\gamma RT}$:

$$
c_{10\,km}=\sqrt{1.4\times287\times223.15}=299.4\ \mathrm{m/s},\qquad Ma=\frac{250}{299.4}=0.835
$$

$$
c_{SL}=\sqrt{1.4\times287\times288.15}=340.3\ \mathrm{m/s},\qquad Ma=\frac{250}{340.3}=0.735
$$

The same airspeed is a lower Mach number at sea level because the speed of sound grows with $\sqrt T$. At 10 km the aircraft is supersonic above 299 m/s.

### Worked example - laminar or turbulent

Estimate the Reynolds numbers of a golf ball in flight and of a volcanic plume (golf ball set as a task at 11 Mar, ll. 573–580; volcano at ll. 537–566).

Golf ball: diameter 42.7 mm, speed about 70 m/s, $\nu=1.5\times10^{-5}$ m²/s:

$$
Re=\frac{VL}{\nu}=\frac{70\times0.0427}{1.5\times10^{-5}}=2\times10^5
$$

a thousand times the laminar limit of 200 for a sphere: the wake is turbulent.

Volcano: say gas leaving at 50 m/s through a 50 m vent, with $\nu$ of order $10^{-5}$–$5\times10^{-5}$ m²/s for gas at a few hundred °C:

$$
Re=\frac{50\times50}{10^{-5}\text{ to }5\times10^{-5}}\approx5\times10^7\text{ to }2.5\times10^8
$$

enormous, and the plume is violently turbulent. Only the order of magnitude matters here.

### Worked example - emptying tank

A tank drains through a long narrow pipe in its base, its level falling from $h_0$ to $h_1$ over a few minutes. Is the pipe flow steady? (Problem Sheet 7, Q7.5.)

The pressure driving the flow is the hydrostatic head $\rho gh$ at the pipe entry, and $h$ falls with time. So the velocity at any fixed point in the pipe falls with time, $\partial V/\partial t\ne0$, and the flow is unsteady. It can be treated as quasi-steady (steady at each instant, with the current $h$) only if the level changes slowly compared with the time fluid takes to pass through the pipe.

---

## Links

- Parent: [[SESA1016 Thermofluids Hub]] · Previous: [[SESA1016 T8 - Hydrostatics]] · Next: [[SESA1016 T10 - Euler and Bernoulli Equations]]
- Concepts: [[Material Derivative]] · [[Streamline, Pathline and Streakline]] · [[Reynolds Number]]
- Worked sheet: [[SESA1016 Problem Sheet 07 - Describing Flow and Euler Equation Solutions]] (Q7.1, Q7.4–Q7.6) · Formula list: [[SESA1016 Formula Sheet]]
- Continues in: [[SESA2029 A7 - Governing Equations - Euler and Navier-Stokes]] (Eulerian conservation laws in CFD) · [[SESA2022 T3 - Potential Flow]] (streamlines and stagnation points)

## Sources

- `Chapter 9.pdf`: lecture notes Chapter 9, Describing flow, §§9.1–9.6, Derivation 9.1, Figs 9.1–9.18.
- `SESA1016 Lecture 2025-03-10.txt` (10 Mar 2025): fluid particle (ll. 42–80), Lagrangian and Eulerian (ll. 81–192), scalar and vector fields (ll. 193–304), steady and unsteady (ll. 305–352), partial derivatives (ll. 353–412), pathlines (ll. 413–465), streaklines (ll. 466–487), streamlines and stagnation (ll. 488–560).
- `SESA1016 Lecture 2025-03-11.txt` (11 Mar 2025): lab-report notices (ll. 1–103), streamtubes (ll. 104–213), uniform, internal, 1D and 2D flows (ll. 214–361), laminar and turbulent flow and the Reynolds number (ll. 362–615), compressibility (ll. 620–688).
- `Problem Sheet 07 - Describing Flow and the Euler Equation.pdf`: Q7.1, Q7.4–Q7.6 (Q7.2–Q7.3 belong to [[SESA1016 T10 - Euler and Bernoulli Equations|T10]]), printed answers.

## Self-study tasks

### Core

- [ ] Estimate the Reynolds number of a struck golf ball and decide whether its flow is laminar (set at 11 Mar, ll. 573–580). → [[#Worked example - laminar or turbulent]]
- [ ] Q7.1, streamlines of the corner flow $\vec V=2x\vec i-2y\vec j$. → [[#Worked example - streamlines near a corner]]
- [ ] Q7.4, the vector-field Jupyter notebook: quiver plots, speed, and pathlines by forward Euler (tutorial problem; set at 10 Mar, ll. 455–461). → [[#Pathlines]] · [[SESA1016 Problem Sheet 07 - Describing Flow and Euler Equation Solutions]]
- [ ] Q7.5, emptying tank: steady or unsteady? → [[#Worked example - emptying tank]]
- [ ] Q7.6, speed of sound and Mach number at 10 km and at sea level. Targets 299.3 m/s, 0.835, 0.735. → [[#Worked example - Mach number at altitude]]

### Further practice

- [ ] Explain why pathlines, streaklines and streamlines coincide in steady flow but not in unsteady flow, and sketch all three for an oscillating stream. → [[#When the lines coincide]]
- [ ] Derive $\Delta\rho/\rho\sim Ma^2$ from $\rho v=1$, the bulk modulus and $\Delta p\sim\rho V^2$ (Chapter 9, Derivation 9.1). → [[#Compressible and incompressible]]
- [ ] Show that $Re$ is the ratio of inertial to viscous forces (11 Mar, ll. 581–615). → [[#Laminar and turbulent]]

## Transcript and slide slips

> [!warning] Lecture-notes slip (Chapter 9, eq. 9.2)
> Where: [[#Vector fields]].
>
> The field is printed $\vec V=v_x(x,y)\vec i+v_j(x,y)\vec j$; the second component is $v_y(x,y)$.

> [!warning] Transcript slip (11 Mar, ll. 554–566)
> Where: [[#Worked example - laminar or turbulent]].
>
> The volcano estimate uses 50 m/s, 50 m and $\nu\approx10^{-5}$ m²/s, which gives $2.5\times10^8$, then quotes "about 50 million, say 100 million". The order of magnitude, the point of the example, is right; $5\times10^7$ corresponds to $\nu=5\times10^{-5}$ m²/s, more typical of gas at a few hundred °C.

> [!warning] Problem-sheet rounding (Problem Sheet 7, Q7.6)
> Where: [[#Worked example - Mach number at altitude]].
>
> The printed speed of sound at 10 km is 299.3 m/s; with $T=223.15$ K it is 299.4 m/s (299.3 m/s corresponds to 223 K). The Mach numbers are unaffected to three figures.
