---
title: "SESA3029 W07a - Euler Equations and the Effect of Mach Number on Aerofoils"
module: "SESA3029 Aerothermodynamics"
type: topic
stream: "Block 4: High-speed aerodynamics"
order: 7
tags: [sesa3029, compressible-flow, euler-equations, cfd, critical-mach-number, drag-divergence, transonic, supercritical-aerofoil]
aliases: ["SESA3029 Lecture 4.1", "SESA3029 Lecture 4.2", "SESA3029 W07a"]
date: 2026-11-02
status: written-ahead
coverage: "Lecture 4.1 lectured Mon 2 Nov (transcript, whole deck); Lecture 4.2 written ahead from the slides, awaiting its lecture"
parent: ["[[SESA3029 Aerothermodynamics Hub]]"]
prerequisites: ["[[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes]]", "[[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method]]", "[[SESA3043 1.2 - Conservation Laws and Governing Equations]]"]
next_topics: ["[[SESA3029 W07b - Compressible Potential Flow and the Prandtl-Glauert Transformation]]"]
key_concepts: ["[[Euler Equations]]", "[[Critical Mach Number]]", "[[Drag Divergence]]"]
tutorial_sheets: ["[[SESA3029 Example Sheet 2 - Solutions]]"]
sources: ["02 - Sources/Lectures/Lecture4-1.pdf", "02 - Sources/Lectures/Lecture4-1.txt", "02 - Sources/Lectures/Lecture4-2.pdf"]
---

# SESA3029 W07a - Euler Equations and the Effect of Mach Number on Aerofoils

> [!abstract] Summary
> Chapter 4 moves from internal flow (nozzles) to external flow over aerofoils. Lecture 4.1 derives the 2D Euler equations, which are mass, two momentum components and energy for an inviscid compressible fluid, from a small control volume, and writes them as one vector equation, the form CFD codes solve. Lecture 4.2 uses Euler CFD on a 12 % aerofoil to show what happens as $M_\infty$ rises: a supersonic region appears at the critical Mach number $M_{crit}$, it ends in a shock, drag rises steeply (drag divergence), and above $M_\infty=1$ a bow shock and trailing-edge shocks form.

> [!summary]- Exam use: quick path
> - **Use it when:** you are asked to derive a conservation equation from a control volume, write the Euler equations in vector form, or describe and explain the flow regimes on an aerofoil as $M_\infty$ rises.
> - **Assumptions:** inviscid (no viscous stress, no heat conduction), 2D Cartesian, unit span, no body forces; perfect gas for $e=c_vT$.
> - **Method:** 1. Draw the CV $\delta x\times\delta y$ and the quantity inside it. 2. Flux in on the left and bottom faces, out on the right and top with a first-order Taylor increment. 3. Add the force (momentum) or pressure work (energy). 4. Expand, cancel, divide by $\delta x\,\delta y$. 5. Collect into $\partial\mathbf Q/\partial t+\partial\mathbf F/\partial x+\partial\mathbf G/\partial y=\mathbf 0$.
> - **Common mistakes:** leaving the slide 4 "$=0$" on the mass balance (a typo); putting $p$ in the wrong flux (it goes with the $x$-derivative in $x$-momentum and the $y$-derivative in $y$-momentum).
> - **Practise:** [[#4. Energy conservation (4.1 slides 10–11)|energy derivation]] · [[#Self-study tasks|L4-1 homework: the mass derivation on paper]]

> [!info] Where this was lectured
> Lecture 4.1 was given on Mon 2 Nov (`Lecture4-1.txt`, 253 lines), straight after the mid-module survey (ll. 1–8). It covered the whole 4.1 deck: the chapter's aim (ll. 9–34), mass (ll. 35–78), $x$- and $y$-momentum (ll. 79–142), energy (ll. 143–204), the vector form (ll. 205–216) and the CFD picture of shock buffeting on a supercritical aerofoil (ll. 217–242). *"The game begins on Thursday"* (l. 245): transonic and supersonic aerofoils from 4.2 onwards.
>
> §§5–9 (Lecture 4.2) are **written ahead from the slides** and have not been lectured yet. They will be reconciled with the transcript when it arrives.

Up to reading week the module was about internal flow: nozzles, wind tunnels and the method of characteristics, all inside walls. Chapter 4 turns to external flow, where the only boundary is the aerofoil or wing itself. The lecturer calls it *"kind of pinnacle of this module"* (L4-1, l. 21). The plan has two strands. First, write down the equations an inviscid compressible flow must satisfy (the Euler equations); these are what CFD codes solve, and they are where the compressible aerofoil theories of 4.3–4.6 start. Second, look at what those equations predict for a real aerofoil as the Mach number goes up, before building the linear theories that explain it.

The Euler equations are the Navier–Stokes equations with viscosity and heat conduction removed (L4-1, ll. 26–29). You have met them twice already: in [[SESA2029 A7 - Governing Equations - Euler and Navier-Stokes|SESA2029 A7]] for incompressible CFD, and in [[SESA3043 1.2 - Conservation Laws and Governing Equations|SESA3043 1.2]] in full 3D conservation form. Lecture 4.1 does the 2D compressible version by the same flux-balance argument, and the result is short enough to memorise.

## 1. The control volume and the bookkeeping rule

![[at_euler_control_volume.png|900]]

Take a small rectangular control volume of sides $\delta x$ and $\delta y$ and unit depth (slide 4). Every conservation law in this lecture follows the same sentence (L4-1, ll. 45–51, 115, 138, 150):

$$
\text{rate of increase inside}=\text{flux in}-\text{flux out}\;(+\text{force or work}).
$$

Fluxes enter through the left face (area $\delta y$) and the bottom face (area $\delta x$). On the opposite faces each flux has changed by its gradient times the distance, a first-order Taylor expansion: a flux $F$ at $x$ becomes $F+(\partial F/\partial x)\,\delta x$ at $x+\delta x$. Everything is per unit span. The lecture works in 2D for simplicity; the 3D version adds a $z$-flux with the same pattern (ll. 38–39).

## 2. Mass conservation (4.1 slides 4–5)

The mass inside is $\rho\,\delta x\,\delta y$ (l. 40). Mass flux is $\rho u$ through the left face and $\rho v$ through the bottom face:

$$
\frac{\partial}{\partial t}(\rho\,\delta x\,\delta y)
=\rho u\,\delta y+\rho v\,\delta x
-\left(\rho u+\frac{\partial(\rho u)}{\partial x}\delta x\right)\delta y
-\left(\rho v+\frac{\partial(\rho v)}{\partial y}\delta y\right)\delta x .
$$

The slide ends this line with "$=0$". That is a typo, and the lecturer said so (L4-1, ll. 64–67): the right-hand side is the net inflow, not zero.

Expand the brackets. The $\rho u\,\delta y$ terms cancel, and so do the $\rho v\,\delta x$ terms (l. 70):

$$
\frac{\partial\rho}{\partial t}\,\delta x\,\delta y=-\frac{\partial(\rho u)}{\partial x}\,\delta x\,\delta y-\frac{\partial(\rho v)}{\partial y}\,\delta x\,\delta y .
$$

The volume is fixed, so $\delta x\,\delta y$ comes out of the time derivative. Divide by $\delta x\,\delta y$:

$$
\boxed{\frac{\partial\rho}{\partial t}+\frac{\partial(\rho u)}{\partial x}+\frac{\partial(\rho v)}{\partial y}=0}
$$

The lecturer skipped the pen-and-paper version (*"try and do so in your own time"*, ll. 76–78); the lines above are that version.

## 3. Momentum conservation (4.1 slides 6–9)

### x-momentum

The $x$-momentum inside is $\rho u\,\delta x\,\delta y$. It is carried in by the flow: $\rho u$ (momentum per volume) times $u\,\delta y$ (volume flow through the left face), and $\rho u$ times $v\,\delta x$ through the bottom face (ll. 87–97). The only external force in inviscid flow is pressure, $p\,\delta y$ on the left face pushing in $+x$ and $(p+\partial p/\partial x\,\delta x)\,\delta y$ on the right face pushing in $-x$ (ll. 107–113):

$$
\begin{aligned}
\frac{\partial(\rho u\,\delta x\,\delta y)}{\partial t}
&=\rho u^2\delta y+\rho uv\,\delta x-\left(\rho u^2+\frac{\partial(\rho u^2)}{\partial x}\delta x\right)\delta y\\
&\quad-\left(\rho uv+\frac{\partial(\rho uv)}{\partial y}\delta y\right)\delta x+p\,\delta y-\left(p+\frac{\partial p}{\partial x}\delta x\right)\delta y .
\end{aligned}
$$

Cancel $\rho u^2\delta y$, $\rho uv\,\delta x$ and $p\,\delta y$ (ll. 119–123):

$$
\frac{\partial(\rho u)}{\partial t}\,\delta x\,\delta y=-\frac{\partial(\rho u^2)}{\partial x}\,\delta x\,\delta y-\frac{\partial(\rho uv)}{\partial y}\,\delta x\,\delta y-\frac{\partial p}{\partial x}\,\delta x\,\delta y .
$$

Divide by $\delta x\,\delta y$ and put the two $x$-derivatives together:

$$
\boxed{\frac{\partial(\rho u)}{\partial t}+\frac{\partial(\rho u^2+p)}{\partial x}+\frac{\partial(\rho uv)}{\partial y}=0}
$$

Pressure joins the $x$-derivative because only the pressure on the left and right faces pushes in $x$ (ll. 128–132). The pressures on the top and bottom faces push in $y$.

### y-momentum

Swap the roles of $x$ and $y$ (l. 136). The $y$-momentum $\rho v$ is carried in at $u\,\delta y$ and $v\,\delta x$, and pressure now acts on the top and bottom faces:

$$
\begin{aligned}
\frac{\partial(\rho v\,\delta x\,\delta y)}{\partial t}
&=\rho vu\,\delta y+\rho v^2\delta x-\left(\rho vu+\frac{\partial(\rho vu)}{\partial x}\delta x\right)\delta y\\
&\quad-\left(\rho v^2+\frac{\partial(\rho v^2)}{\partial y}\delta y\right)\delta x+p\,\delta x-\left(p+\frac{\partial p}{\partial y}\delta y\right)\delta x .
\end{aligned}
$$

Cancel and divide in the same way:

$$
\boxed{\frac{\partial(\rho v)}{\partial t}+\frac{\partial(\rho uv)}{\partial x}+\frac{\partial(\rho v^2+p)}{\partial y}=0}
$$

## 4. Energy conservation (4.1 slides 10–11)

Energy is a scalar, so there is one equation with contributions from both directions (ll. 157–158). The energy in the CV is $\rho e_t\,\delta x\,\delta y$, where $e_t$ is the total specific energy (per unit mass):

$$
e_t=e+\tfrac12(u^2+v^2)=c_vT+\tfrac12(u^2+v^2)\qquad(\text{perfect gas}).
$$

The lecturer said *"specific energy, which is power volume"* (l. 145). It is per unit **mass**; $\rho e_t$ is the energy per unit volume.

The new ingredient is work (ll. 163–181). Rate of work is force times velocity, and force is pressure times area, so the left face does work $pu\,\delta y$ on the CV and the bottom face $pv\,\delta x$. On the right and top faces the CV pushes the surrounding fluid, so it loses energy at $(pu+\partial(pu)/\partial x\,\delta x)\,\delta y$ and $(pv+\partial(pv)/\partial y\,\delta y)\,\delta x$:

$$
\begin{aligned}
\frac{\partial(\rho e_t\,\delta x\,\delta y)}{\partial t}
&=\rho e_tu\,\delta y+\rho e_tv\,\delta x-\left(\rho e_tu+\frac{\partial(\rho e_tu)}{\partial x}\delta x\right)\delta y-\left(\rho e_tv+\frac{\partial(\rho e_tv)}{\partial y}\delta y\right)\delta x\\
&\quad+pu\,\delta y+pv\,\delta x-\left(pu+\frac{\partial(pu)}{\partial x}\delta x\right)\delta y-\left(pv+\frac{\partial(pv)}{\partial y}\delta y\right)\delta x .
\end{aligned}
$$

Cancel the four pairs and divide by $\delta x\,\delta y$:

$$
\frac{\partial(\rho e_t)}{\partial t}+\frac{\partial(\rho e_tu)}{\partial x}+\frac{\partial(\rho e_tv)}{\partial y}=-\frac{\partial(pu)}{\partial x}-\frac{\partial(pv)}{\partial y}.
$$

Move the work terms to the left and group by derivative (l. 198):

$$
\boxed{\frac{\partial(\rho e_t)}{\partial t}+\frac{\partial[(\rho e_t+p)u]}{\partial x}+\frac{\partial[(\rho e_t+p)v]}{\partial y}=0}
$$

The combination $\rho e_t+p=\rho\,(e_t+p/\rho)=\rho h_t$ is the density times the total enthalpy. In steady flow the energy equation therefore says that $h_t=h+\tfrac12V^2$ is carried unchanged along streamlines, which is the stagnation-enthalpy result of [[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes#4. Stagnation properties|W01 §4]].

## 5. Vector form and what CFD does with it (4.1 slides 12–13)

Stack the four boxed equations (slide 12):

$$
\frac{\partial}{\partial t}\begin{bmatrix}\rho\\ \rho u\\ \rho v\\ \rho e_t\end{bmatrix}
+\frac{\partial}{\partial x}\begin{bmatrix}\rho u\\ \rho u^2+p\\ \rho uv\\ \rho u(e_t+p)\end{bmatrix}
+\frac{\partial}{\partial y}\begin{bmatrix}\rho v\\ \rho uv\\ \rho v^2+p\\ \rho v(e_t+p)\end{bmatrix}
=\vec 0 .
$$

The first column is the *vector of "conservative" variables*; the other two are the *flux vectors* (slide 12; L4-1, ll. 206–208). Writing them as $\mathbf Q$, $\mathbf F$, $\mathbf G$ gives $\partial\mathbf Q/\partial t+\partial\mathbf F/\partial x+\partial\mathbf G/\partial y=\mathbf 0$. The slides do not use these letters; they are the usual CFD shorthand.

> [!warning] Slide 12's energy flux
> Slide 12 prints the energy fluxes as $\rho u(e_t+p)$ and $\rho v(e_t+p)$, but slide 11 derives $(\rho e_t+p)u$. The two are different: $\rho u(e_t+p)=\rho e_tu+\rho pu$, which is not even dimensionally consistent. Slide 11 is right. If you want to factor out $\rho u$, write $\rho u\,(e_t+p/\rho)=\rho u\,h_t$.

Four equations, but five unknowns ($\rho,u,v,p,e_t$, or $T$). The perfect-gas equation of state $p=\rho RT$ with $e=c_vT$ closes the set; slide 10's $e_t=c_vT+\tfrac12(u^2+v^2)$ is where the gas model enters.

The equations are nonlinear (products such as $\rho u^2$) and coupled, so apart from very simple geometries and boundary conditions there are no general analytical solutions (L4-1, ll. 213–216). CFD solvers discretise them over a grid and in time (slide 12). Being conservation laws in this flux form, they also capture shock waves and expansion fans (slide 3): across a shock the fluxes $\mathbf F$ balance, which is exactly the normal-shock derivation of W01 §5 done numerically. If the flow is incompressible, $\partial\rho/\partial t=0$, $\rho$ is constant and can be divided out (ll. 210–212).

The slide 13 picture is a time-resolved simulation of a supercritical aerofoil at $M_\infty=0.8$ and $\alpha=7^\circ$ (ll. 218–221). The red contour is the sonic line, with supersonic flow inside it (ll. 237–240). The lecturer points out that a pure Euler solution has no boundary layer; the turbulent boundary layer in the picture comes from adding the viscous terms (ll. 222–223). The shocks are not fixed: they move back and forth, and several can appear. This is **shock buffeting** (ll. 224–232). The oscillating shocks make lift and drag fluctuate, which shakes the wing and threatens both stability and structural integrity. It is one of the lecturer's research topics (l. 233).

> [!note] Slide 3 says "steady flow"
> The objective slide says the equations will be derived *"for steady flow"*, but slides 4–12 keep $\partial/\partial t$ throughout, as above. The steady form ($\partial/\partial t=0$) is taken in [[SESA3029 W07b - Compressible Potential Flow and the Prandtl-Glauert Transformation#1. Steady Euler equations in non-conservative form (4.3 slides 2–3)|4.3 slide 2]].

## 6. Euler CFD of an aerofoil at rising Mach number (4.2 slides 1–4)

*Written ahead from the slides; not yet lectured.*

Lecture 4.2 takes an Euler solver and runs it on one aerofoil at a series of free-stream Mach numbers. The solutions are converged to a steady state and contain no viscous (boundary-layer) effects (slide 2). The aerofoil is a 12 % thick Kármán–Trefftz section on an O-type grid of $51\times101$ points, generated by a conformal mapping (slide 3). The mapping is the one in [[Kármán–Trefftz Transformation]] (SESA3043 2.1), here used to wrap grid lines round the aerofoil instead of to compute the flow.

The solver starts from a non-physical initial flow field and iterates until the residual error goes to zero (slide 4). The slide's residual history falls by about five orders of magnitude in roughly 3000 iterations, oscillating on the way. *How many iterations do we need?* is the slide's question; in practice you stop when the residual has fallen several orders and the lift and drag no longer change. Compare the iteration and time-marching ideas of [[SESA2029 A9 - Finite Volume Method|SESA2029 A9]].

## 7. Flow regimes and the critical Mach number (4.2 slides 5–12)

![[at_mach_regimes_aerofoil.png|900]]

The four snapshots at $\alpha=0$ tell one story.

At $M_\infty=0.6$ (slide 5) the flow is subsonic everywhere. The surface Mach number peaks near $0.75$ and the $-C_p$ distribution is smooth.

At $M_\infty=0.8$ (slide 6) a region of supersonic flow sits on each surface near maximum thickness, and the surface Mach number reaches about 1.2. The $-C_p$ curve drops sharply at about $x/c=0.5$: that is a shock wave terminating the supersonic region.

Between these two cases there is a free-stream Mach number at which the local Mach number first reaches 1.0 at some point on the surface. That free-stream value is the **critical Mach number** $M_{crit}$ (slide 7). The definition refers to the free stream, not the local flow: the local flow is sonic at one point, and $M_\infty<1$. See [[Critical Mach Number]]; 4.4 shows how to estimate it.

At $M_\infty=1.0$ (slide 8) the supersonic regions have grown to cover the rear of the aerofoil and the shocks have moved to the trailing edge. At $M_\infty=1.2$ and $1.4$ (slides 9–10) a bow shock stands in front of the leading edge, closer to it as $M_\infty$ increases, and oblique trailing-edge shocks form.

Slide 11 summarises the regimes at $\alpha=0$:

| Free stream | What the aerofoil sees |
|---|---|
| $M_\infty<M_{crit}$ | subsonic flow throughout |
| $M_\infty=M_{crit}$ | $M=1$ at one point on the surface |
| $M_{crit}<M_\infty<1$ | a supersonic region appears, terminated by a shock |
| $M_\infty>1$ | a bow shock and trailing-edge shocks; the only subsonic flow is in front of the leading edge, behind the bow shock |

At incidence ($\alpha=5.7^\circ$, slide 12) the picture is asymmetric. At $M_\infty=0.8$ the upper surface carries a large supersonic region and a strong shock, while the lower surface stays nearly subsonic. At $M_\infty=1.4$ the bow shock is tilted and there is a large expansion over the upper surface.

## 8. Lift, drag and the mechanism of drag divergence (4.2 slides 13–15)

Slide 13 plots $C_L$ and $C_D$ against $M$ for the same aerofoil at $\alpha=0.1$ rad. For this case:

- lift rises in the subsonic range, and the rise is well predicted by Prandtl–Glauert theory ([[SESA3029 W07b - Compressible Potential Flow and the Prandtl-Glauert Transformation|4.4]]);
- lift falls in the supersonic range, approximated by Ackeret theory ([[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils|4.5]]) at higher $M_\infty$;
- drag starts to rise at around $M_\infty\approx0.6$ for this aerofoil at this incidence;
- wave drag rises steeply and peaks in the transonic range, then levels off to a plateau for $M_\infty>1$.

The steep rise is called **drag divergence** (see [[Drag Divergence]]). Slides 14–15 explain it with the duct picture from the shock-expansion method ([[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method#6. The shock-expansion method|W03 §6]]). The region between the aerofoil's upper surface and a streamline above it behaves like a converging–diverging duct. Ahead of the crest (b) the duct converges, so in subsonic flow $U$ rises and $p$ falls; behind it the duct diverges and $U$ falls again (slide 14). The pressure minimum is at the crest.

![[at_drag_divergence_cp.png|900]]

At a transonic speed the flow reaches $M=1$ at the crest (b). Behind it the duct diverges, and supersonic flow in a diverging duct **accelerates** (the area–velocity relation of [[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow|W04]], $\mathrm dA/A=(M^2-1)\,\mathrm dU/U$). So instead of recovering, the pressure keeps falling until a shock at (b') brings it back up (slide 15). Behind the crest the surface faces backwards. Extra suction acting on a backward-facing surface pulls the aerofoil rearwards, which is a drag force: *"suction force in the drag direction: drag divergence"*. The same suction acts upwards too, so it also increases the lift (slide 15), which is the transonic lift peak on slide 13.

> [!tip] Why the subsonic $C_p$ curve gives no drag
> In inviscid subsonic flow the suction on the backward-facing part of the surface is balanced by the high pressure near the leading edge and the pressure recovery at the trailing edge, so the net streamwise force is zero (d'Alembert). The supersonic region breaks that balance: the extra suction behind the crest is not recovered, because the shock jumps the pressure instead of the flow decelerating smoothly. The lost recovery is wave drag.

## 9. Drag reduction strategies (4.2 slides 16–17)

**Supercritical sections**, for high subsonic flight (slide 16). A flat-rooftop upper surface lets the flow reach the supersonic region at a lower local Mach number, so the terminating shock is weaker. The slide compares a NACA 64₂-A215 at $M_\infty=0.69$, with a strong shock, against a 13.5 % supercritical section at $M_\infty=0.79$, with a weak one. The flat top also reduces $C_l$, which is not a problem at high speed: in level flight $L'=W=\tfrac12\rho U^2cC_l$, and a large $U$ needs only a small $C_l$. The aerofoil in slide 13 of 4.1 is a supercritical section, which is why its lower surface near the trailing edge looks unusual (L4-1, ll. 219–220).

**Wing sweep** (slide 17). The effective oncoming Mach number seen by the aerofoil section is $M_\infty\cos\Lambda$, where $\Lambda$ is the leading-edge sweep angle. The slide writes the sweep angle as $\beta$; this note uses $\Lambda$ to avoid a clash with the shock angle $\beta$ of W02 and the Prandtl–Glauert $\beta$ of 4.4. Sweep is used in both transonic and supersonic flight to reduce the Mach number the section sees. The F-111 on the slide varies its sweep in flight.

> [!check] Sweep numbers (simple sweep theory: an infinite swept wing, so only the normal component matters)
> At $M_\infty=0.85$ and $\Lambda=30^\circ$, the section sees $0.85\cos30^\circ=0.736$. That is below the $M_{crit}=0.747$ found in [[SESA3029 W07b - Compressible Potential Flow and the Prandtl-Glauert Transformation#Worked example: Cp0,min = −0.4 (4.4 slides 8–9 and 11)|4.4's worked example]] for an aerofoil with $C_{p0,min}=-0.4$, so that section stays subcritical on the swept wing but not on a straight one.

**Area rule** (slide 17). A supersonic aircraft reduces its wave drag by keeping the streamwise variation of its total cross-sectional area (wings plus fuselage) smooth. The F-106 on the slide has the waisted fuselage this produces.

## Transcript slips

Whisper renders several words consistently wrongly in `Lecture4-1.txt`: "air force" and "airfoil" for aerofoil, "blaze" for blades, "rho U" for $\rho u$, "CFP" for CFD, "viscocid batch" for the viscous part. These are not listed below.

> [!warning] Slips in `Lecture4-1.txt` (Mon 2 Nov)
> | Line | Said | Correct |
> |---|---|---|
> | ll. 64–67 | *"disregard equals to zero here. That is a typo."* | The lecturer's own correction to slide 4: the mass balance has no "$=0$" at the end |
> | l. 104 | *"rho U plus the slight increment of rho U U by delta Y"* | the top-face $x$-momentum flux is $\rho uv+\partial(\rho uv)/\partial y\,\delta y$, times $\delta x$ |
> | l. 145 | *"specific energy, which is power volume"* | $e_t$ is per unit mass; $\rho e_t$ is per unit volume |
> | l. 210 | *"partial by partial rho by partial t is zero"* | $\partial\rho/\partial t=0$ |
> | l. 222 | *"from laminar, sorry, there's no laminar boundary layer in Euler cases"* | right as corrected: the slide 13 picture includes viscous effects, so it is not a pure Euler solution |

## Terminology and alternative names

| Course term | Also called | Where the course uses it | Note |
|---|---|---|---|
| vector of "conservative" variables | conserved variables; state vector; solution vector $\mathbf U$ or $\mathbf Q$ | 4.1 slide 12; L4-1, l. 207 | The slide puts "conservative" in quotes |
| flux vectors | inviscid fluxes; convective fluxes $\mathbf F$, $\mathbf G$ (or $\mathbf E$, $\mathbf F$) | 4.1 slide 12 | |
| shock buffeting | transonic buffet; shock buffet; shock oscillation | L4-1, ll. 226–232 (spoken only) | |
| drag divergence | drag rise; transonic drag rise; Mach drag divergence (at $M_{dd}$) | 4.2 slides 13–15 | |
| critical Mach number $M_{crit}$ | $M_{cr}$; first critical Mach number | 4.2 slide 7; 4.4 slides 7–9 | |
| supercritical sections | supercritical aerofoils (Whitcomb); flat-rooftop aerofoils | 4.2 slide 16 | |
| leading-edge sweep angle $\beta$ | sweep angle $\Lambda$ | 4.2 slide 17 | This note writes $\Lambda$ (see §9) |
| area rule | Whitcomb area rule; transonic/supersonic area rule | 4.2 slide 17 | |

## Links

- Parent: [[SESA3029 Aerothermodynamics Hub]]
- Previous: [[SESA3029 W05b - Minimum-Length Nozzle Design]] · Next: [[SESA3029 W07b - Compressible Potential Flow and the Prandtl-Glauert Transformation]]
- Earlier this module: [[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes#5. Normal shock from conservation laws|W01 §5]] (the same conservation laws across a shock) · [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method#6. The shock-expansion method|W03 §6]] (the duct picture, wave drag) · [[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow|W04]] (area–velocity relation)
- New concepts: [[Euler Equations]] · [[Critical Mach Number]] · [[Drag Divergence]]
- Earlier years and other modules: [[SESA3043 1.2 - Conservation Laws and Governing Equations|SESA3043 1.2]] and [[Compressible Navier-Stokes Conservation Form]] (3D, with viscosity) · [[SESA2029 A7 - Governing Equations - Euler and Navier-Stokes|SESA2029 A7]] · [[Conservation Form of the Governing Equations]] · [[Finite Volume Method]] · [[Kármán–Trefftz Transformation]] (the 4.2 grid)
- Formulae: [[SESA3029 Formula Sheet#Euler equations and compressible aerofoils (Lectures 4.1–4.6)|Formula sheet: Chapter 4]]

## Sources

- `Lecture4-1.pdf`: 4.1 Euler Equations (the basis of CFD and compressible aerofoil theories), 13 slides including the survey QR code. Lectured Mon 2 Nov.
- `Lecture4-1.txt`: the Mon 2 Nov recording (253 lines).
- `Lecture4-2.pdf`: 4.2 Effect of Mach Number on Aerofoil Flow, 17 slides. Not yet lectured.
- Figures: `generate_aerothermo_w07_figures.py` (`at_euler_control_volume.png`, `at_mach_regimes_aerofoil.png`, `at_drag_divergence_cp.png`). The regime and $C_p$ figures are schematics redrawn from slides 7 and 15, not CFD output.
- Anderson, *Modern Compressible Flow*, §§2.3–2.8 (integral and differential conservation laws) and §11.6 (critical Mach number, drag divergence, supercritical aerofoils, area rule).

## Self-study tasks

Tasks citing `L4-1` come from the Mon 2 Nov lecture. Lecture 4.2 has not been given yet, so its tasks are *suggested, not lecturer-set*, until the transcript arrives.

### Core

- [ ] **(L4-1, ll. 76–78)** Derive mass conservation on pen and paper from the control volume, *"in your own time"*. → [[#2. Mass conservation (4.1 slides 4–5)|§2]]
- [ ] **(L4-1, ll. 135–140)** Derive $y$-momentum yourself by swapping $x$ and $y$ in the $x$-momentum balance. → [[#y-momentum|§3]]
- [ ] **(L4-1, ll. 143–204)** Derive the energy equation, explaining which faces gain and which lose pressure work. → [[#4. Energy conservation (4.1 slides 10–11)|§4]]
- [ ] **(L4-1, l. 202)** Memorise the vector form and be able to say what each row and column is. → [[#5. Vector form and what CFD does with it (4.1 slides 12–13)|§5]]
- [ ] *(Suggested, not lecturer-set)* Explain drag divergence with the duct picture: why the pressure keeps falling behind the crest at transonic speed. → [[#8. Lift, drag and the mechanism of drag divergence (4.2 slides 13–15)|§8]]

### Further practice

- [ ] *(Suggested)* Show that slide 12's $\rho u(e_t+p)$ is dimensionally inconsistent and that $(\rho e_t+p)u=\rho u h_t$. → [[#5. Vector form and what CFD does with it (4.1 slides 12–13)|§5]]
- [ ] *(Suggested)* Sketch the four flow regimes of slide 11 from memory and say where each shock is. → [[#7. Flow regimes and the critical Mach number (4.2 slides 5–12)|§7]]
- [ ] *(Suggested)* Explain why a supercritical section has a weaker shock, and why the lower $C_l$ does not matter at cruise. → [[#9. Drag reduction strategies (4.2 slides 16–17)|§9]]
