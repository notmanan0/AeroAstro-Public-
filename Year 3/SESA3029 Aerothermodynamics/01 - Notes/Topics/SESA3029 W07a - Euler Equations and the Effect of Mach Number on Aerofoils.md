---
title: "SESA3029 W07a - Euler Equations and the Effect of Mach Number on Aerofoils"
module: "SESA3029 Aerothermodynamics"
type: topic
stream: "Block 4: High-speed aerodynamics"
order: 7
tags: [sesa3029, compressible-flow, euler-equations, cfd, critical-mach-number, drag-divergence, transonic, supercritical-aerofoil]
aliases: ["SESA3029 Lecture 4.1", "SESA3029 Lecture 4.2", "SESA3029 W07a"]
date: 2026-11-02
status: lectured
coverage: "Lecture 4.1 lectured Mon 2 Nov (transcript, whole deck); Lecture 4.2 lectured Thu 5 Nov (repaired transcript, slides 1–16; the recording stops as slide 17 begins)"
parent: ["[[SESA3029 Aerothermodynamics Hub]]"]
prerequisites: ["[[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes]]", "[[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method]]", "[[SESA3043 1.2 - Conservation Laws and Governing Equations]]"]
next_topics: ["[[SESA3029 W07b - Compressible Potential Flow and the Prandtl-Glauert Transformation]]"]
key_concepts: ["[[Euler Equations]]", "[[Critical Mach Number]]", "[[Drag Divergence]]"]
tutorial_sheets: ["[[SESA3029 Example Sheet 2 - Solutions]]"]
sources: ["02 - Sources/Lectures/Lecture4-1.pdf", "02 - Sources/Lectures/Lecture4-1.txt", "02 - Sources/Lectures/Lecture4-2.pdf", "02 - Sources/Lectures/Lecture4-2.txt"]
---

# SESA3029 W07a - Euler Equations and the Effect of Mach Number on Aerofoils

> [!abstract] Summary
> External flow over aerofoils is governed by the 2D Euler equations: mass, two momentum components and energy for an inviscid compressible fluid. They follow from a small control volume and combine into one vector equation, the form CFD codes solve. Euler CFD on a 12 % aerofoil shows what happens as $M_\infty$ rises: a supersonic region appears at the critical Mach number $M_{crit}$, it ends in a shock, drag rises steeply (drag divergence), and above $M_\infty=1$ a bow shock and trailing-edge shocks form.

> [!summary]- Exam use: quick path
> - **Use it when:** you are asked to derive a conservation equation from a control volume, write the Euler equations in vector form, or describe and explain the flow regimes on an aerofoil as $M_\infty$ rises.
> - **Assumptions:** inviscid (no viscous stress, no heat conduction), 2D Cartesian, unit span, no body forces; perfect gas for $e=c_vT$.
> - **Method:** 1. Draw the CV $\delta x\times\delta y$ and the quantity inside it. 2. Flux in on the left and bottom faces, out on the right and top with a first-order Taylor increment. 3. Add the force (momentum) or pressure work (energy). 4. Expand, cancel, divide by $\delta x\,\delta y$. 5. Collect into $\partial\mathbf Q/\partial t+\partial\mathbf F/\partial x+\partial\mathbf G/\partial y=\mathbf 0$.
> - **Common mistakes:** leaving the slide 4 "$=0$" on the mass balance (a typo); putting $p$ in the wrong flux (it goes with the $x$-derivative in $x$-momentum and the $y$-derivative in $y$-momentum).
> - **Practise:** [[#4. Energy conservation (4.1 slides 10–11)|energy derivation]] · [[#Self-study tasks|L4-1 homework: the mass derivation on paper]]

Wing sweep and the area rule in §9 are from slide 17 alone.

External flow has the aerofoil or wing as its only boundary, unlike the nozzles, wind tunnels and method of characteristics of the earlier chapters, which all sit inside walls. Two strands run through it. One is the set of equations an inviscid compressible flow must satisfy (the Euler equations); these are what CFD codes solve, and the compressible aerofoil theories of 4.3–4.6 start from them. The other is what those equations predict for a real aerofoil as the Mach number goes up, which the linear theories then explain.

The Euler equations are the Navier–Stokes equations with viscosity and heat conduction removed (L4-1, ll. 26–29). They appear earlier in [[SESA2029 A7 - Governing Equations - Euler and Navier-Stokes|SESA2029 A7]] for incompressible CFD, and in [[SESA3043 1.2 - Conservation Laws and Governing Equations|SESA3043 1.2]] in full 3D conservation form. The 2D compressible version follows by the same flux-balance argument, and the result is short enough to memorise.

## 1. The control volume and the balance statement

![[at_euler_control_volume.png|900]]

Take a small rectangular control volume of sides $\delta x$ and $\delta y$ and unit depth (slide 4). Every conservation law here follows the same sentence (L4-1, ll. 45–51, 115, 138, 150):

$$
\text{rate of increase inside}=\text{flux in}-\text{flux out}\;(+\text{force or work}).
$$

Fluxes enter through the left face (area $\delta y$) and the bottom face (area $\delta x$). On the opposite faces each flux has changed by its gradient times the distance, a first-order Taylor expansion: a flux $F$ at $x$ becomes $F+(\partial F/\partial x)\,\delta x$ at $x+\delta x$. Everything is per unit span. The derivation is 2D for simplicity; the 3D version adds a $z$-flux with the same pattern.

## 2. Mass conservation (4.1 slides 4–5)

The mass inside is $\rho\,\delta x\,\delta y$ (l. 40). Mass flux is $\rho u$ through the left face and $\rho v$ through the bottom face:

$$
\frac{\partial}{\partial t}(\rho\,\delta x\,\delta y)
=\rho u\,\delta y+\rho v\,\delta x
-\left(\rho u+\frac{\partial(\rho u)}{\partial x}\delta x\right)\delta y
-\left(\rho v+\frac{\partial(\rho v)}{\partial y}\delta y\right)\delta x .
$$

The right-hand side is the net inflow, not zero (see the slips section for slide 4).

Expand the brackets. The $\rho u\,\delta y$ terms cancel, and so do the $\rho v\,\delta x$ terms (l. 70):

$$
\frac{\partial\rho}{\partial t}\,\delta x\,\delta y=-\frac{\partial(\rho u)}{\partial x}\,\delta x\,\delta y-\frac{\partial(\rho v)}{\partial y}\,\delta x\,\delta y .
$$

The volume is fixed, so $\delta x\,\delta y$ comes out of the time derivative. Divide by $\delta x\,\delta y$:

$$
\boxed{\frac{\partial\rho}{\partial t}+\frac{\partial(\rho u)}{\partial x}+\frac{\partial(\rho v)}{\partial y}=0}
$$

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

The specific energy $e_t$ is per unit **mass**; $\rho e_t$ is the energy per unit volume.

Energy also changes through work done on the control volume (ll. 163–181). Rate of work is force times velocity, and force is pressure times area, so the left face does work $pu\,\delta y$ on the CV and the bottom face $pv\,\delta x$. On the right and top faces the CV pushes the surrounding fluid, so it loses energy at $(pu+\partial(pu)/\partial x\,\delta x)\,\delta y$ and $(pv+\partial(pv)/\partial y\,\delta y)\,\delta x$:

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

The four boxed equations stack into one vector equation (slide 12):

$$
\frac{\partial}{\partial t}\begin{bmatrix}\rho\\ \rho u\\ \rho v\\ \rho e_t\end{bmatrix}
+\frac{\partial}{\partial x}\begin{bmatrix}\rho u\\ \rho u^2+p\\ \rho uv\\ (\rho e_t+p)u\end{bmatrix}
+\frac{\partial}{\partial y}\begin{bmatrix}\rho v\\ \rho uv\\ \rho v^2+p\\ (\rho e_t+p)v\end{bmatrix}
=\vec 0 .
$$

The first column is the *vector of "conservative" variables*; the other two are the *flux vectors* (slide 12; L4-1, ll. 206–208). Writing them as $\mathbf Q$, $\mathbf F$, $\mathbf G$, the usual CFD shorthand, gives $\partial\mathbf Q/\partial t+\partial\mathbf F/\partial x+\partial\mathbf G/\partial y=\mathbf 0$.

Four equations, but five unknowns ($\rho,u,v,p,e_t$, or $T$). The perfect-gas equation of state $p=\rho RT$ with $e=c_vT$ closes the set; slide 10's $e_t=c_vT+\tfrac12(u^2+v^2)$ is where the gas model enters.

The equations are nonlinear (products such as $\rho u^2$) and coupled, so apart from very simple geometries and boundary conditions there are no general analytical solutions (L4-1, ll. 213–216). CFD solvers discretise them over a grid and in time (slide 12). Being conservation laws in this flux form, they also capture shock waves and expansion fans (slide 3): across a shock the fluxes $\mathbf F$ balance, which is exactly the normal-shock derivation of W01 §5 done numerically. If the flow is incompressible, $\partial\rho/\partial t=0$, $\rho$ is constant and can be divided out (ll. 210–212).

In a time-resolved simulation of a supercritical aerofoil at $M_\infty=0.8$ and $\alpha=7^\circ$ (slide 13), the flow is supersonic inside the sonic line (red contour). A pure Euler solution has no boundary layer; the turbulent boundary layer in that simulation comes from adding the viscous terms. The shocks are not fixed: they move back and forth, and several can appear. This is **shock buffeting**. The oscillating shocks make lift and drag fluctuate, which shakes the wing and threatens both stability and structural integrity.

## 6. Euler CFD of an aerofoil at rising Mach number (4.2 slides 1–4)

An Euler solver, which solves exactly the equations of §5, run on one aerofoil at a series of free-stream Mach numbers from transonic to supersonic, shows what compressibility does to aerofoil flow (L4-2, ll. 16–25). The typical transonic picture (title slide) has a supersonic region (red) on the upper surface, bounded by the sonic line (yellow) and ended by a normal shock that brings the flow back to subsonic speed before it leaves the trailing edge (ll. 26–38). Only steady, fully converged solutions are used. The shock buffeting of §5 is unsteady and involves the boundary layer, so it is left out; a pure Euler solution has no boundary layer anyway (slide 2; ll. 39–50).

The aerofoil is a 12 % thick Kármán–Trefftz section on an O-type grid of $51\times101$ points, so called because the grid lines wrap round the aerofoil in circles (slide 3; ll. 52–60). The grid comes from a conformal mapping, the one in [[Kármán–Trefftz Transformation]] (SESA3043 2.1), used here to wrap grid lines round the aerofoil instead of to compute the flow. It is the same kind of set-up as the CFD exercise of [[SESA2029 A9 - Finite Volume Method|SESA2029 A9]].

The solver starts from a guessed initial condition, which can be any non-physical flow field, and iterates towards the physically correct solution (slide 4; ll. 64–68). The **residual** measures how much the solution changes from one time step to the next, averaged over the grid, and the iteration continues until that change is negligible (ll. 69–78). In the run of slide 4 it falls from about $10^3$ to about $10^{-1}$, roughly four orders of magnitude, in close to 3000 iterations, oscillating on the way, which is about what a converged inviscid aerofoil solution needs (ll. 79–88). A viscous solver needs many more (l. 89). In practice the iteration stops when the residual has fallen by several orders and the lift and drag no longer change.

## 7. Flow regimes and the critical Mach number (4.2 slides 5–12)

![[at_mach_regimes_aerofoil.png|900]]

The aerofoil is symmetric and at zero incidence in these snapshots, so every solution is symmetric between the upper and lower surfaces (ll. 91–94).

At $M_\infty=0.6$ (slide 5) the flow is subsonic everywhere and behaves much like an incompressible flow (ll. 96–99). The plot shows $-C_p$, so up means lower pressure and faster flow (ll. 99–103). At the leading-edge stagnation point $C_p$ is close to 1 (exactly 1 in incompressible flow; the isentropic value at $M_\infty=0.6$ is 1.09), so $-C_p$ starts near $-1$ (ll. 105–118). It then rises steeply to its peak, where the flow is fastest, and falls back towards zero at the trailing edge; it does not reach zero exactly, because the flow at the trailing edge is not quite at the free-stream speed (ll. 119–124). In ambient flow $C_p=0$, and with strong acceleration the minimum can go below $-1$ or even $-2$ (ll. 110–115). The surface Mach number follows the same shape: zero at the stagnation point, a peak near 0.75, then a slow fall (ll. 125–127).

At $M_\infty=0.8$ (slide 6) the picture is very different. The fastest point is no longer near the leading edge but near mid-chord, and there the surface Mach number exceeds 1, reaching about 1.2 (ll. 129–133). As in an over-expanded nozzle, the pressure downstream is not low enough to keep the flow supersonic, so a shock forms and the pressure jumps up steeply; behind it $-C_p$ follows a near-incompressible curve again (ll. 134–142).

A change of only 0.2 in $M_\infty$ separates these two cases, so somewhere between them there is a free-stream Mach number at which the local Mach number first reaches 1.0, at a single point on the surface and not over a region. That free-stream value is the **critical Mach number** $M_{crit}$ (slide 7; ll. 143–162). The definition refers to the free stream: the flow is sonic at one point on the surface while $M_\infty<1$. Raising $M_\infty$ from 0.6 in small steps (0.61, 0.62, …) until a sonic point appears locates it. Just above $M_{crit}$ a small supersonic region appears with no obvious shock; well above it the region is large and ends in a shock (ll. 163–166). See [[Critical Mach Number]]; [[SESA3029 W07b - Compressible Potential Flow and the Prandtl-Glauert Transformation|4.4]] shows how to estimate it.

At $M_\infty=1.0$ (slide 8) the supersonic region covers almost the whole aerofoil: apart from the subsonic flow near the leading edge, the flow is supersonic all the way to the trailing edge, at about $M=1.3$–1.4 there (ll. 173–180). There is no shock at the front yet, but there is one at the trailing edge, where the flow must come back to the free-stream $M=1$ (ll. 178–182). Between $M_\infty=0.8$ and 1.0 the shock that stood near mid-chord moves steadily back until it reaches the trailing edge (ll. 184–186).

At $M_\infty=1.2$ and $1.4$ (slides 9–10) a second shock appears in front of the leading edge: a **bow shock**, detached from the aerofoil, while oblique shocks remain at the trailing edge (ll. 187–189). The bow shock has to be there because the stagnation point has $M=0$, so the flow just ahead of the leading edge must be subsonic, and a supersonic stream that has to slow to rest is normally brought down by a shock (ll. 190–193).

### Why there are oblique shocks at the trailing edge

The trailing-edge shocks of slides 9–10 have three causes (L4-3, ll. 6–34). The supersonic flow leaving the surfaces has to slow towards the free-stream state, and its pressure has to return to the free-stream pressure. The cause that fixes their form is the Kutta condition at the sharp trailing edge. The streams from the upper and lower surfaces must leave in the same direction, separated by a slip line, and the pressure must be the same on both sides of it. Near the trailing edge of a symmetric aerofoil the upper surface runs slightly downhill and the lower surface slightly uphill, so each stream has to be turned through the local surface angle onto the slip line, which is horizontal at $\alpha=0$ by symmetry.

A supersonic stream turns either through an oblique shock (a compressive turn, into itself) or through an expansion fan (turning away from itself), as in [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method|W03]]. Here both turns are compressive, so both sides carry an oblique shock. At incidence the two turning angles differ, so the slip line is inclined and the two shocks generally differ in strength.

![[at_trailing_edge_shocks.png|900]]

The figure uses a schematic wedge for the rear of the aerofoil. With a local $M_1=1.6$ and a turn of $\theta=6^\circ$ the weak solution is $\beta=45.3^\circ$ from the incoming flow, which is $39.3^\circ$ from the slip line, with $M_2=1.39$ and $p_2/p_1=1.34$ behind it ($\gamma=1.4$, computed in the figure script).

### Why a bow shock and not an oblique shock

![[at_bow_shock_centreline.png|900]]

On the centre line through the stagnation point, the θ–β–M chart of [[SESA3029 W02 - Oblique Shock Relations and Mach Waves|W02]] lists the possible shocks (L4-2, ll. 194–247). The streamline is horizontal before the shock and horizontal after it, so the turning angle is $\theta=0$. At $M_1=1.2$ the $\theta=0$ line meets the curve twice. The lower point is $\beta=\mu=\arcsin(1/1.2)=56.4^\circ$, the weak solution, which is just a Mach wave; the flow behind it stays supersonic. The upper point is $\beta=90^\circ$, the strong solution, a normal shock with

$$
M_2=\sqrt{\frac{1+\tfrac{\gamma-1}{2}M_1^2}{\gamma M_1^2-\tfrac{\gamma-1}{2}}}=\sqrt{\frac{1+0.2(1.44)}{1.4(1.44)-0.2}}=0.842\qquad(\gamma=1.4).
$$

The flow ahead of the stagnation point must be subsonic, so on the centre line the shock must be normal. An oblique shock attached to the leading edge would be the weak branch, which leaves the flow supersonic, so it cannot do the job.

Away from the centre line the bow shock curves back and weakens, and it passes through every solution on the θ–β–M curve (ll. 252–255, 317–335; [[SESA3029 W02 - Oblique Shock Relations and Mach Waves#10.4 Detachment and the bow shock: every solution on one curve|W02 §10.4]]). Point A on the centre line is the normal shock. Between A and B the shock is strong and the flow behind it subsonic. B is the maximum turning angle. Just below it, C is where $M_2=1$ exactly; on the CFD picture this is where the sonic (yellow) contour meets the shock. D is a weak shock with small turning and small shock angle, and far from the aerofoil the bow shock decays into a Mach wave.

At $M_\infty=1.4$ the bow shock sits closer to the leading edge and leans further back: at the same height above the aerofoil its angle is lower, roughly $70^\circ$ against roughly $80^\circ$ at $M_\infty=1.2$ (ll. 256–263, readings from the slides). The chart explains it. For a fixed turning angle, a higher $M_1$ gives a lower $\beta$ on the weak branch: at $\theta=5^\circ$, $\beta=47.9^\circ$ for $M_1=1.5$ and $34.3^\circ$ for $M_1=2.0$ (ll. 264–272; computed, $\gamma=1.4$). At $M_1=1.2$ the $5^\circ$ line misses the curve altogether, because $\theta_{max}=3.94^\circ$ there. A CFD picture alone explains little; the theory of the earlier chapters says why each feature is there (ll. 272–275).

The regimes at $\alpha=0$ (slide 11) apply at other incidences too (ll. 276–279):

| Free stream | What the aerofoil sees |
|---|---|
| $M_\infty<M_{crit}$ | subsonic flow throughout |
| $M_\infty=M_{crit}$ | $M=1$ at one point on the surface |
| $M_{crit}<M_\infty<1$ | a supersonic region appears, terminated by a shock |
| $M_\infty>1$ | a bow shock and trailing-edge shocks; the only subsonic flow is in front of the leading edge, behind the bow shock |

At incidence ($\alpha=5.7^\circ$, slide 12) the symmetry is broken. At $M_\infty=0.8$ the upper surface carries a large supersonic region ended by a shock, as at zero incidence, while the lower surface stays subsonic (ll. 281–286). The asymmetry is what produces lift; at $\alpha=0$ the symmetric aerofoil has drag but no lift (ll. 286–289). At $M_\infty=1.4$ the bow shock is tilted and there is a large expansion over the upper surface.

## 8. Lift, drag and the mechanism of drag divergence (4.2 slides 13–15)

The lift and drag coefficients of the same aerofoil at $\alpha=0.1$ rad vary with $M_\infty$ as in slide 13. Their trends are not the trends of lift and drag themselves (ll. 289–295). The lift per unit span is

$$
L'=\tfrac12\rho_\infty U_\infty^2\,c\,C_L=\tfrac12\gamma p_\infty M_\infty^2\,c\,C_L ,
$$

using $\rho U^2=\rho a^2M^2=\gamma pM^2$ for a perfect gas. At a fixed altitude ($p_\infty$ fixed) the lift therefore scales with $C_LM_\infty^2$, so a slowly falling $C_L$ can still mean a rising lift (ll. 296–301).

For this aerofoil:

- $C_L$ rises through the subsonic range, peaks in the transonic range (near $M_\infty\approx0.85$ on the chart), drops sharply, then falls slowly in the supersonic range (ll. 296–305);
- the subsonic rise is predicted well by Prandtl–Glauert theory ([[SESA3029 W07b - Compressible Potential Flow and the Prandtl-Glauert Transformation|4.4]]), the dashed red line (ll. 306–307);
- the supersonic fall is approximated at high $M_\infty$ by Ackeret theory ([[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils|4.5]]), the dash-dot line. These two theories are the main pillars of compressible aerofoil theory (ll. 308–311);
- $C_D$ is nearly constant up to about $M_\infty\approx0.6$, then rises steeply, peaks in the transonic range and levels off to a plateau for $M_\infty>1$ (ll. 312–313).

The steep rise is called **drag divergence** (see [[Drag Divergence]]; ll. 315–316). The converging–diverging nozzle of [[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow|W04]] explains it (slides 14–15; ll. 336–346). The flow between a streamline well above the aerofoil, nearly horizontal, and the dividing streamline that runs into the stagnation point, along the surface and off the trailing edge, is a duct. From the leading edge (a) to the crest (b) the duct converges, so in subsonic flow the velocity rises and the pressure falls; behind the crest it diverges, the flow slows and the pressure recovers towards the trailing edge (c). The pressure minimum is at the crest, and flipped over, this is the $-C_p$ curve of slide 5.

![[at_drag_divergence_cp.png|900]]

Above the critical Mach number the free stream is still subsonic, but the flow reaches $M=1$ at the crest, which now acts as the throat of a choked nozzle (ll. 347–351). Behind it the duct diverges, and supersonic flow in a diverging duct **accelerates**, from the area–velocity relation of W04,

$$
\frac{\mathrm dA}{A}=(M^2-1)\frac{\mathrm dU}{U}.
$$

So instead of recovering, the pressure keeps falling between the throat and the shock at (b'), where it jumps back to the subsonic value and then follows the subsonic curve (ll. 351–355). The red curve on slide 15 therefore has lower pressure than the blue subsonic curve over the supersonic region, while the lower surface hardly changes (ll. 355–362).

That extra suction acts on the upper surface, so it pulls the aerofoil upwards and increases the lift. It also acts behind the thickest point, where the surface faces backwards, so it pulls the aerofoil rearwards too, which is extra drag (ll. 363–367). This is the inviscid mechanism of both drag divergence and the transonic rise in $C_L$ on slide 13, explained by nozzle theory alone (ll. 366–370).

> [!tip] Why the subsonic $C_p$ curve gives no drag
> In inviscid subsonic flow the suction on the backward-facing part of the surface is balanced by the high pressure near the leading edge and the pressure recovery at the trailing edge, so the net streamwise force is zero (d'Alembert). The supersonic region breaks that balance: the extra suction behind the crest is not recovered, because the shock jumps the pressure instead of the flow decelerating smoothly. The lost recovery is wave drag.

## 9. Drag reduction strategies (4.2 slides 16–17)

The supercritical section is the popular answer for high subsonic flight (slide 16; ll. 371–376). Its upper surface is flatter than a low-speed aerofoil's, a flat rooftop, so the flow over it is less sharply accelerated and the shock that ends the supersonic region forms further back and is weaker. The lift is spread more smoothly along the chord, and although the section can have a small supersonic region and shock on its underside too, the overall drag is lower. On slide 16 a NACA 64₂-A215 at $M_\infty=0.69$ has a relatively strong shock, while a 13.5 % supercritical section at $M_\infty=0.79$ has a relatively weak one. The flat top also reduces $C_l$, which does not matter at high speed: in level flight $L'=W=\tfrac12\rho U^2cC_l$, and a large $U$ needs only a small $C_l$. The aerofoil in slide 13 of 4.1 is a supercritical section, which is why its lower surface near the trailing edge looks unusual (L4-1, ll. 219–220).

**Wing sweep** (slide 17). The effective oncoming Mach number seen by the aerofoil section is $M_\infty\cos\Lambda$, where $\Lambda$ is the leading-edge sweep angle. Sweep is used in both transonic and supersonic flight to reduce the Mach number the section sees. The F-111 (slide 17) varies its sweep in flight.

> [!check] Sweep numbers (simple sweep theory: an infinite swept wing, so only the normal component matters)
> At $M_\infty=0.85$ and $\Lambda=30^\circ$, the section sees $0.85\cos30^\circ=0.736$. That is below the $M_{crit}=0.747$ found in [[SESA3029 W07b - Compressible Potential Flow and the Prandtl-Glauert Transformation#Worked example: Cp0,min = −0.4 (4.4 slides 8–9 and 11)|4.4's worked example]] for an aerofoil with $C_{p0,min}=-0.4$, so that section stays subcritical on the swept wing but not on a straight one.

**Area rule** (slide 17). A supersonic aircraft reduces its wave drag by keeping the streamwise variation of its total cross-sectional area (wings plus fuselage) smooth. The F-106 (slide 17) has the waisted fuselage this produces.

## Terminology and alternative names

| Course term | Also called | Where the course uses it | Note |
|---|---|---|---|
| vector of "conservative" variables | conserved variables; state vector; solution vector $\mathbf U$ or $\mathbf Q$ | 4.1 slide 12; L4-1, l. 207 | The slide puts "conservative" in quotes |
| flux vectors | inviscid fluxes; convective fluxes $\mathbf F$, $\mathbf G$ (or $\mathbf E$, $\mathbf F$) | 4.1 slide 12 | |
| shock buffeting | transonic buffet; shock buffet; shock oscillation | L4-1, ll. 226–232 (spoken only) | |
| drag divergence | drag rise; transonic drag rise; Mach drag divergence (at $M_{dd}$) | 4.2 slides 13–15 | |
| critical Mach number $M_{crit}$ | $M_{cr}$; first critical Mach number | 4.2 slide 7; 4.4 slides 7–9 | |
| bow shock | detached shock | 4.2 slides 7, 9–11; L4-2, ll. 167–189 | |
| oblique shock chart | θ–β–M chart; shock polar diagram (strictly a different plot) | L4-2, ll. 199, 252, 264 (spoken); Lecture 2.2 | |
| supercritical sections | supercritical aerofoils (Whitcomb); flat-rooftop aerofoils | 4.2 slide 16 | |
| leading-edge sweep angle $\beta$ | sweep angle $\Lambda$ | 4.2 slide 17 | Written $\Lambda$ in these notes, to avoid a clash with the shock angle $\beta$ of W02 and §7 and the Prandtl–Glauert $\beta$ of 4.4 (§9) |
| area rule | Whitcomb area rule; transonic/supersonic area rule | 4.2 slide 17 | |

## Links

- Parent: [[SESA3029 Aerothermodynamics Hub]]
- Previous: [[SESA3029 W05b - Minimum-Length Nozzle Design]] · Next: [[SESA3029 W07b - Compressible Potential Flow and the Prandtl-Glauert Transformation]]
- Earlier: [[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes#5. Normal shock from conservation laws|W01 §5]] (the same conservation laws across a shock) · [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method#6. The shock-expansion method|W03 §6]] (the duct picture, wave drag) · [[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow|W04]] (area–velocity relation)
- New concepts: [[Euler Equations]] · [[Critical Mach Number]] · [[Drag Divergence]]
- Earlier years and other modules: [[SESA3043 1.2 - Conservation Laws and Governing Equations|SESA3043 1.2]] and [[Compressible Navier-Stokes Conservation Form]] (3D, with viscosity) · [[SESA2029 A7 - Governing Equations - Euler and Navier-Stokes|SESA2029 A7]] · [[Conservation Form of the Governing Equations]] · [[Finite Volume Method]] · [[Kármán–Trefftz Transformation]] (the 4.2 grid)
- Formulae: [[SESA3029 Formula Sheet#Euler equations and compressible aerofoils (Lectures 4.1–4.6)|Formula sheet: Chapter 4]]

## Sources

- `Lecture4-1.pdf`: 4.1 Euler Equations (the basis of CFD and compressible aerofoil theories), 13 slides including the survey QR code. Lectured Mon 2 Nov.
- `Lecture4-1.txt`: the Mon 2 Nov recording (253 lines).
- `Lecture4-2.pdf`: 4.2 Effect of Mach Number on Aerofoil Flow, 17 slides. Lectured Thu 5 Nov.
- `Lecture4-2.txt`: the Thu 5 Nov recording (378 lines), repaired from the raw Whisper output by re-transcribing the garbled stretches from the audio and checking every technical word against the slides. Two stretches are unrecoverable (ll. 251 and 280, about 30 s and 20 s), and the recording ends mid-sentence at 43:41 (l. 378). Details in `Lecture4-2 transcript repair report.md`.
- `06 November 2026 at 16_57_37.txt` (L4-3, Fri 6 Nov): ll. 6–34 answer the 4.2 question on the trailing-edge oblique shocks; the rest of the recording is Lecture 4.3 ([[SESA3029 W07b - Compressible Potential Flow and the Prandtl-Glauert Transformation|W07b]]).
- Figures: `generate_aerothermo_w07_figures.py` (`at_euler_control_volume.png`, `at_mach_regimes_aerofoil.png`, `at_bow_shock_centreline.png`, `at_trailing_edge_shocks.png`, `at_drag_divergence_cp.png`). The regime and $C_p$ figures are schematics redrawn from slides 7 and 15, not CFD output; the θ–β–M curves are computed ($\gamma=1.4$).
- Anderson, *Modern Compressible Flow*, §§2.3–2.8 (integral and differential conservation laws) and §11.6 (critical Mach number, drag divergence, supercritical aerofoils, area rule).

## Self-study tasks

Tasks citing `L4-1` come from the Mon 2 Nov lecture and `L4-2` from the Thu 5 Nov lecture. L4-2 set no homework; its tasks below are questions posed in it, and the rest are *suggested, not lecturer-set*.

### Core

- [ ] **(L4-1, ll. 76–78)** Derive mass conservation on pen and paper from the control volume (set as homework). → [[#2. Mass conservation (4.1 slides 4–5)|§2]]
- [ ] **(L4-1, ll. 135–140)** Derive $y$-momentum yourself by swapping $x$ and $y$ in the $x$-momentum balance. → [[#y-momentum|§3]]
- [ ] **(L4-1, ll. 143–204)** Derive the energy equation, explaining which faces gain and which lose pressure work. → [[#4. Energy conservation (4.1 slides 10–11)|§4]]
- [ ] **(L4-1, l. 202)** Memorise the vector form and be able to say what each row and column is. → [[#5. Vector form and what CFD does with it (4.1 slides 12–13)|§5]]
- [ ] **(L4-2, ll. 336–370)** Explain drag divergence and the transonic lift rise with the converging–diverging nozzle picture: why the pressure keeps falling behind the crest, and why that suction is both lift and drag. → [[#8. Lift, drag and the mechanism of drag divergence (4.2 slides 13–15)|§8]]

### Further practice

- [ ] **(L4-2, ll. 194–247)** Why is the shock ahead of the leading edge a bow shock and not an attached oblique shock? Answer with the θ–β–M chart at $M_1=1.2$, $\theta=0$. → [[#Why a bow shock and not an oblique shock]]
- [ ] **(L4-2 question, answered L4-3, ll. 6–34)** Why are there oblique shocks at the trailing edge at $M_\infty=1.2$? Name the slip line and the Kutta condition, and say why the turns are compressive on both sides. → [[#Why there are oblique shocks at the trailing edge]]
- [ ] **(L4-2, ll. 256–272)** Explain why the bow shock at $M_\infty=1.4$ is closer to the leading edge and leans further back than at 1.2. → [[#Why a bow shock and not an oblique shock]]
- [ ] **(L4-2, ll. 105–118)** State $C_p$ at the stagnation point and in the free stream, and say why $-C_p$ is not exactly zero at the trailing edge. → [[#7. Flow regimes and the critical Mach number (4.2 slides 5–12)|§7]]
- [ ] **(L4-2, ll. 289–301)** Show that at fixed altitude $L'\propto C_LM_\infty^2$, and explain why a falling $C_L$ above $M_\infty=1$ need not mean falling lift. → [[#8. Lift, drag and the mechanism of drag divergence (4.2 slides 13–15)|§8]]

- [ ] *(Suggested)* Show that slide 12's $\rho u(e_t+p)$ is dimensionally inconsistent and that $(\rho e_t+p)u=\rho u h_t$. → [[#5. Vector form and what CFD does with it (4.1 slides 12–13)|§5]]
- [ ] *(Suggested)* Sketch the four flow regimes of slide 11 from memory and say where each shock is. → [[#7. Flow regimes and the critical Mach number (4.2 slides 5–12)|§7]]
- [ ] *(Suggested)* Explain why a supercritical section has a weaker shock, and why the lower $C_l$ does not matter at cruise. → [[#9. Drag reduction strategies (4.2 slides 16–17)|§9]]

## Transcript and slide slips

> [!warning] Slide 12's energy flux
> Where: [[#5. Vector form and what CFD does with it (4.1 slides 12–13)]].
>
> Slide 12 prints the energy fluxes as $\rho u(e_t+p)$ and $\rho v(e_t+p)$, but slide 11 derives $(\rho e_t+p)u$. The two are different: $\rho u(e_t+p)=\rho e_tu+\rho pu$, which is not even dimensionally consistent. Slide 11 is right. If you want to factor out $\rho u$, write $\rho u\,(e_t+p/\rho)=\rho u\,h_t$.

> [!note] Slide 3 says "steady flow"
> Where: [[#5. Vector form and what CFD does with it (4.1 slides 12–13)]].
>
> The objective slide says the equations will be derived *"for steady flow"*, but slides 4–12 keep $\partial/\partial t$ throughout, as above. The steady form ($\partial/\partial t=0$) is taken in [[SESA3029 W07b - Compressible Potential Flow and the Prandtl-Glauert Transformation#1. Steady Euler equations in non-conservative form (4.3 slides 2–3)|4.3 slide 2]].

### Transcript slips

Whisper renders several words consistently wrongly in `Lecture4-1.txt`: "air force" and "airfoil" for aerofoil, "blaze" for blades, "rho U" for $\rho u$, "CFP" for CFD, "viscocid batch" for the viscous part. These are not listed below.

> [!warning] Slips in `Lecture4-1.txt` (Mon 2 Nov)
> | Line | Said | Correct |
> |---|---|---|
> | ll. 64–67 | *"disregard equals to zero here. That is a typo."* | The lecturer's own correction to slide 4: the mass balance has no "$=0$" at the end |
> | l. 104 | *"rho U plus the slight increment of rho U U by delta Y"* | the top-face $x$-momentum flux is $\rho uv+\partial(\rho uv)/\partial y\,\delta y$, times $\delta x$ |
> | l. 145 | *"specific energy, which is power volume"* | $e_t$ is per unit mass; $\rho e_t$ is per unit volume |
> | l. 210 | *"partial by partial rho by partial t is zero"* | $\partial\rho/\partial t=0$ |
> | l. 222 | *"from laminar, sorry, there's no laminar boundary layer in Euler cases"* | right as corrected: the slide 13 picture includes viscous effects, so it is not a pure Euler solution |

> [!warning] Slips and gaps in `Lecture4-2.txt` (Thu 5 Nov)
> The raw Whisper output ended in a loop of repeated "so" and garbled several stretches; the filed transcript is the repaired version (see Sources). The recording ends mid-sentence at l. 377, as slide 17 (wing sweep, area rule) begins, and ll. 251 and 280 are unrecoverable.
>
> | Line | Said | Correct |
> |---|---|---|
> | l. 29 | title picture *"close to Mach probably [0.9?]"* | the title-slide field matches slide 12's $M_\infty=0.8$, $\alpha=5.7^\circ$ case; the number is unclear in the audio |
> | l. 228 | *"about 57 degrees"* | $\mu=\arcsin(1/1.2)=56.4^\circ$, as the chart reading |
> | ll. 262–263 | bow-shock angles *"close to 80"* and *"like 70"* | readings off the CFD pictures, not computed values |
> | l. 292 | *"Lift is product of CL times U squared"* | $L'=\tfrac12\rho U^2cC_L$, so lift is proportional to $C_LU^2$ at fixed density |
> | l. 297 | $C_L$ *"peaks at somewhere 0.8"* | the slide 13 peak is nearer $M_\infty\approx0.85$ |
> | l. 317 | *"this oblique, no, sorry, bow shock case"* | bow shock, as corrected |
> | l. 374 | shock weaker than *"in the [upstream?] case"* | than on the conventional aerofoil of slide 16(a) |
