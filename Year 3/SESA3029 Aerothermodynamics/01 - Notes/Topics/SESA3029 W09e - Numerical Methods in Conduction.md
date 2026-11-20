---
title: "SESA3029 W09e - Numerical Methods in Conduction"
module: "SESA3029 Aerothermodynamics"
type: topic
stream: "Block 5: Heat transfer"
order: 14
tags: [sesa3029, heat-transfer, conduction, heat-diffusion-equation, finite-difference, explicit, implicit, fourier-number, stability]
aliases: ["SESA3029 Lecture 5.7", "SESA3029 W09e", "Numerical methods in conduction"]
date: 2026-11-17
status: written-ahead
coverage: "Lecture 5.7 (all 20 slides) written ahead from the slides; no transcript yet"
parent: ["[[SESA3029 Aerothermodynamics Hub]]"]
prerequisites: ["[[SESA3029 W09a - Heat Conduction and Thermal Resistance]]", "[[SESA3029 W09d - Thermal Radiation]]", "[[Heat Equation]]", "[[Finite Difference Approximations]]", "[[Taylor and Maclaurin Series]]"]
next_topics: ["[[SESA3029 W09f - Heat Exchangers]]"]
key_concepts: ["[[Finite-Difference Form of the Heat Equation]]", "[[Thermal Diffusivity]]", "[[CFL and Fourier Numbers]]", "[[Explicit and Implicit Time Integration]]", "[[Truncation Error and Order of Accuracy]]"]
tutorial_sheets: ["[[SESA3029 Example Sheet 3 - Solutions]]"]
sources: ["02 - Sources/Lectures/Lecture5.7.pdf"]
---

# SESA3029 W09e - Numerical Methods in Conduction

> [!abstract] Summary
> An energy balance on a small element gives the heat diffusion equation $\nabla^2T+\dot g/k=(1/\alpha)\,\partial T/\partial t$, where $\alpha=k/\rho c_p$ is the thermal diffusivity. Real geometries have no analytical solution, so the equation is discretised on a mesh: Taylor series turn $\partial^2T/\partial x^2$ into $(T_{i+1}-2T_i+T_{i-1})/\Delta x^2$ with an error of order $\Delta x^2$. In time, the explicit scheme $T_i^{n+1}=T_i^n+\mathcal F(T_{i+1}^n-2T_i^n+T_{i-1}^n)$, with Fourier number $\mathcal F=\alpha\Delta t/\Delta x^2$, marches forward node by node but is stable only for $\mathcal F\le\tfrac12$; the implicit scheme solves a tridiagonal system each step and is stable for any $\mathcal F$. Both are first order in time and second order in space.

> [!summary]- Exam use: quick path
> - **Use it when:** a question asks for the finite-difference equation at a node (interior, surface, corner, with convection or heat flux), for one or two explicit time steps, or for a stable time step.
> - **Assumptions:** constant $k$, $\rho$, $c_p$; uniform grid in each direction (check whether $\Delta x=\Delta y$: "equidistant" in a question can mean uniform in $x$ and uniform in $y$ with $\Delta x\neq\Delta y$, as in [[SESA3029 Past Paper 2019-20 - Solutions#(b) Stencils at nodes 5 and 11, and the check at node 8 [10 marks]|2019–20 Q4(iii)]]); unit depth in 2-D; explicit stability limits assume a uniform 1-D or 2-D grid with fixed-temperature ends.
> - **Method:** 1. Draw the node's control volume: half a cell in every direction that stays inside the solid. 2. Write each face's conduction as $k\times(\text{face length})\times(T_{nb}-T_P)/(\text{spacing})$, all counted into the node; add convection $h\times(\text{exposed length})\times(T_\infty-T_P)$, heat flux and generation. 3. Steady: set the sum to zero and solve for $T_P$. Transient explicit: set the sum equal to $\rho c_p\,(\text{volume})(T_P^{n+1}-T_P^n)/\Delta t$. 4. Check stability: every coefficient of an old temperature must be $\ge0$ ($\mathcal F\le\tfrac12$ interior in 1-D, $\le\tfrac14$ in 2-D, tighter at convective boundaries). 5. Check that the face flows sum to zero with the answer.
> - **Common mistakes:** assuming $\Delta x=\Delta y$ on a rectangular grid; giving a boundary face its full length instead of $\Delta x/2$; taking a time step with $\mathcal F>\tfrac12$ and getting oscillating, growing temperatures.
> - **Practise:** [[#Worked example: one explicit and one implicit step by hand|explicit and implicit steps by hand]] · [[SESA3029 Past Paper 2024-25 A - Solutions#Q5. Finite-difference stencil at an internal corner with boundary heat flux (10 marks)|2024–25 A Q5]] (internal-corner stencil)

The conduction results of [[SESA3029 W09a - Heat Conduction and Thermal Resistance|W09a]] cover a plane wall, a cylinder and a sphere, each steady and one-dimensional, where the heat rate comes from a closed-form thermal resistance such as $L/kA$ or $\ln(r_o/r_i)/2\pi kL$. A real object, such as a whole aircraft heated by its engines, the Sun and its own skin friction, has no such formula. Approximating it by a cylinder gives only a crude answer, and anything more needs a three-dimensional solution of the governing equation.

Numerical methods supply it. The object is divided into small elements (a mesh), the temperature is stored at the nodes, and every derivative in the heat equation is replaced by a difference between neighbouring nodal values. The partial differential equation becomes a set of algebraic equations, one per node, which a computer can solve for any shape. This is how thermal analysis software computes the temperature field over a vehicle. A transient problem adds time as a further coordinate to be stepped through, and the size of that step is limited by stability as well as accuracy. Exam questions mostly ask for node equations at boundaries and corners, which come from an energy balance on each node's own share of the solid (§5).

## 1. The heat conduction equation in 2-D

Fourier's law for 1-D conduction ([[SESA3029 W09a - Heat Conduction and Thermal Resistance|W09a]]) gives the heat rate through an area $A$ as

$$
\dot Q=-kA\frac{\mathrm dT}{\mathrm dx}.
$$

Take a rectangular element $\delta x\times\delta y$ of unit depth in a solid in which heat flows in both $x$ and $y$. Let $\dot q_x$ and $\dot q_y$ be the heat fluxes (W/m²) in the $x$ and $y$ directions, let heat be generated inside at a rate $\dot g$ per unit volume (W/m³), and let the element's temperature change with time.

![[at_w09e_control_volume_and_stencils.png|900]]

The energy balance on the element is

$$
\left(\begin{array}{c}\text{rate of heat}\\\text{conduction in}\end{array}\right)-\left(\begin{array}{c}\text{rate of heat}\\\text{conduction out}\end{array}\right)+\left(\begin{array}{c}\text{rate of heat}\\\text{generation}\end{array}\right)=\left(\begin{array}{c}\text{rate of change of}\\\text{energy content}\end{array}\right),
$$

$$
\dot Q_{in}-\dot Q_{out}+\dot Q_g=\dot Q_{st}.
$$

The heat enters through the faces at $x$ and $y$ and leaves through the faces at $x+\delta x$ and $y+\delta y$. Each flux acts over a face of length $\delta y$ or $\delta x$ (unit depth). The generation is $\dot g$ times the volume, and the stored energy changes at the rate

$$
\dot Q_{st}=\frac{\partial E}{\partial t}=mc_p\frac{\partial T}{\partial t}=\rho\,(\delta x\,\delta y\times1)\,c_p\frac{\partial T}{\partial t}.
$$

So

$$
\left(\dot q_x-\dot q_{x+\delta x}\right)\delta y+\left(\dot q_y-\dot q_{y+\delta y}\right)\delta x+\dot g\,\delta x\,\delta y=\rho c_p\frac{\partial T}{\partial t}\,\delta x\,\delta y .
$$

Divide by $\delta x\,\delta y$:

$$
\frac{\dot q_x-\dot q_{x+\delta x}}{\delta x}+\frac{\dot q_y-\dot q_{y+\delta y}}{\delta y}+\dot g=\rho c_p\frac{\partial T}{\partial t}.
$$

Let $\delta x\to0$ and $\delta y\to0$. Each difference quotient becomes a derivative, with a minus sign because it is "in minus out":

$$
\lim_{\delta x\to0}\frac{\dot q_x-\dot q_{x+\delta x}}{\delta x}=-\frac{\partial\dot q_x}{\partial x}
\quad\Rightarrow\quad
-\frac{\partial\dot q_x}{\partial x}-\frac{\partial\dot q_y}{\partial y}+\dot g=\rho c_p\frac{\partial T}{\partial t}.
$$

Fourier's law in each direction is $\dot q_i=-k\,\partial T/\partial x_i$. For constant $k$,

$$
-\frac{\partial\dot q_x}{\partial x}=-\frac{\partial}{\partial x}\left(-k\frac{\partial T}{\partial x}\right)=k\frac{\partial^2T}{\partial x^2},
$$

and the same in $y$, so

$$
k\left(\frac{\partial^2T}{\partial x^2}+\frac{\partial^2T}{\partial y^2}\right)+\dot g=\rho c_p\frac{\partial T}{\partial t}.
$$

Divide by $k$:

$$
\left(\frac{\partial^2T}{\partial x^2}+\frac{\partial^2T}{\partial y^2}\right)+\frac{\dot g}{k}=\frac{\rho c_p}{k}\frac{\partial T}{\partial t}.
$$

The group $\rho c_p/k$ is $1/\alpha$, where $\alpha$ is the thermal diffusivity (§2). This is the **heat diffusion equation**:

$$
\boxed{\frac{\partial^2T}{\partial x^2}+\frac{\partial^2T}{\partial y^2}+\frac{\dot g}{k}=\frac{1}{\alpha}\frac{\partial T}{\partial t}}\qquad(\text{constant }k,\ \rho,\ c_p).
$$

The same element in three dimensions adds a $z$ face pair and

$$
\frac{\partial^2T}{\partial x^2}+\frac{\partial^2T}{\partial y^2}+\frac{\partial^2T}{\partial z^2}+\frac{\dot g}{k}=\frac{1}{\alpha}\frac{\partial T}{\partial t}.
$$

In steady state with no generation it reduces to Laplace's equation $\nabla^2T=0$, and in 1-D to $\mathrm d^2T/\mathrm dx^2=0$, whose solution is the straight-line profile of the plane wall. The mathematics of this parabolic equation (separation of variables, eigenfunction series) is in [[Heat Equation]] (MATH2048). If $k$ varies with temperature or position, the step that took $k$ outside the derivative fails and the equation keeps the form $\partial(k\,\partial T/\partial x)/\partial x+\dots$.

## 2. Thermal diffusivity

$$
\alpha=\frac{k}{\rho c_p}\qquad[\mathrm{m^2/s}].
$$

The thermal conductivity $k$ says how well a material conducts heat, and the heat capacity per unit volume $\rho c_p$ says how much energy it stores per kelvin. A material with high conductivity or low heat capacity has a large thermal diffusivity: it passes heat on rather than storing it, so its temperature responds quickly to a change in its environment. Thermal diffusivity is therefore the property that sets the speed of transient conduction, while $k$ alone sets the steady heat flow.

| Material (about 300 K) | $k$ (W/(m K)) | $\rho$ (kg/m³) | $c_p$ (J/(kg K)) | $\alpha$ (m²/s) |
|---|---:|---:|---:|---:|
| Copper | 401 | 8933 | 385 | $1.17\times10^{-4}$ |
| Aluminium | 237 | 2702 | 903 | $9.71\times10^{-5}$ |
| Stainless steel (AISI 304) | 14.9 | 7900 | 477 | $3.95\times10^{-6}$ |
| Water | 0.613 | 997 | 4179 | $1.47\times10^{-7}$ |

A disturbance diffuses a distance of order $\sqrt{\alpha t}$ in time $t$, so the time for heat to cross a length $L$ is of order $L^2/\alpha$. For a 1 m copper bar this is $1/(1.17\times10^{-4})\approx8600$ s, a little over two hours; for stainless steel it is thirty times longer. The same letter $\alpha$ is absorptivity in [[SESA3029 W09d - Thermal Radiation|W09d]].

## 3. Boundary conditions

The heat diffusion equation is second order in space and first order in time, so a unique solution needs a condition on every boundary and an initial temperature field. The boundary conditions represent the physical constraints on the real system. Taking a 1-D solid occupying $x\ge0$, without generation, with its boundary at $x=0$:

| Condition | Equation at $x=0$ | Physical meaning |
|---|---|---|
| Constant temperature | $T(0,t)=T_s$ | surface held at a fixed temperature |
| Constant surface heat flux | $-k\left.\dfrac{\partial T}{\partial x}\right\vert_{x=0}=\dot q_x$ | heater supplying a known flux into the solid |
| Adiabatic or insulated surface | $\left.\dfrac{\partial T}{\partial x}\right\vert_{x=0}=0$ | no heat crosses; also a plane of symmetry |
| Convection | $-k\left.\dfrac{\partial T}{\partial x}\right\vert_{x=0}=h\left(T_\infty-T(0,t)\right)$ | Newton cooling to a fluid at $T_\infty$ ([[SESA3029 W09b - Convective Heat Transfer and the Reynolds Analogy\|W09b]]) |
| Radiation | $-k\left.\dfrac{\partial T}{\partial x}\right\vert_{x=0}=\epsilon\sigma\left(T_{surr}^4-T_0^4\right)$ | grey surface exchanging with large surroundings at $T_{surr}$ ([[SESA3029 W09d - Thermal Radiation\|W09d]]) |

Each flux condition is an energy balance on a surface of zero thickness: the conducted flux $-k\,\partial T/\partial x$, which is the heat flowing in the $+x$ direction into the solid, equals what is supplied to the surface from outside. With the solid on the other side ($x\le L$, boundary at $x=L$) the signs of the right-hand sides flip. Real boundaries often combine these, for example convection and radiation together, or a known flux on one face and a fixed temperature on another. The radiation condition is non-linear in $T$, which is one more reason for a numerical solution, and the temperatures in it must be in kelvin.

## 4. Discretising the heat equation

Take the 1-D steady case without a heat source,

$$
\frac{\mathrm d^2T}{\mathrm dx^2}=0,
$$

since the same procedure applies in 2-D and 3-D. Divide the solid into a mesh of nodes $i=0,1,\dots,I$ with a uniform step $\Delta x$, so $x_i=i\Delta x$ and $T_i=T(x_i)$.

A smooth function can be expanded in a Taylor series ([[Taylor and Maclaurin Series]]):

$$
f(x+\Delta x)=f(x)+\frac{\mathrm df}{\mathrm dx}\Delta x+\frac12\frac{\mathrm d^2f}{\mathrm dx^2}\Delta x^2+\frac{1}{3!}\frac{\mathrm d^3f}{\mathrm dx^3}\Delta x^3+\dots
$$

Keeping only the terms up to first order and rearranging gives the slope as a difference:

$$
\frac{\mathrm df}{\mathrm dx}\simeq\frac{f(x+\Delta x)-f(x)}{\Delta x}.
$$

Applied between neighbouring nodes, this gives the gradient at the half points between them, $i-\tfrac12$ and $i+\tfrac12$ (a difference over one step is centred on its midpoint):

$$
\left.\frac{\partial T}{\partial x}\right\vert_{i-1/2}\approx\frac{T_i-T_{i-1}}{\Delta x},\qquad
\left.\frac{\partial T}{\partial x}\right\vert_{i+1/2}\approx\frac{T_{i+1}-T_i}{\Delta x}.
$$

The second derivative at node $i$ is the change in slope across it, divided by the distance $\Delta x$ between the two half points:

$$
\left.\frac{\partial^2T}{\partial x^2}\right\vert_i\approx\frac{\left.\partial T/\partial x\right\vert_{i+1/2}-\left.\partial T/\partial x\right\vert_{i-1/2}}{\Delta x}.
$$

Substitute the two gradients:

$$
\left.\frac{\partial^2T}{\partial x^2}\right\vert_i\approx\frac{1}{\Delta x}\left(\frac{T_{i+1}-T_i}{\Delta x}-\frac{T_i-T_{i-1}}{\Delta x}\right)=\frac{T_{i+1}-2T_i+T_{i-1}}{\Delta x^2}.
$$

The steady heat equation at node $i$ becomes

$$
\boxed{\frac{T_{i+1}-2T_i+T_{i-1}}{\Delta x^2}=0}
\quad\Rightarrow\quad
T_i=\frac{T_{i+1}+T_{i-1}}{2}.
$$

This is the **finite difference form** of the heat equation; the set of nodes it uses ($i-1$, $i$, $i+1$) is called its stencil. Each interior node is the average of its two neighbours, and with the boundary values $T_0$ and $T_I$ the $I-1$ equations form a tridiagonal linear system ([[SESA2029 A3 - Iterative Solution of the Steady Heat Equation|SESA2029 A3]] solves such systems by Gaussian elimination, Jacobi and Gauss–Seidel iteration).

**In 2-D**, with $T_{i,j}$ on a grid $\Delta x\times\Delta y$, the same central difference in each direction turns $\nabla^2T+\dot g/k=0$ into

$$
\frac{T_{i+1,j}-2T_{i,j}+T_{i-1,j}}{\Delta x^2}+\frac{T_{i,j+1}-2T_{i,j}+T_{i,j-1}}{\Delta y^2}+\frac{\dot g_{i,j}}{k}=0 .
$$

Multiplying by $\Delta y^2$ and setting $s=(\Delta y/\Delta x)^2$ gives the general **non-square uniform grid** stencil (compass labels P for the node and E, W, N, S for its neighbours):

$$
s\left(T_E+T_W\right)+T_N+T_S-2(1+s)\,T_P+\frac{\dot g\,\Delta y^2}{k}=0
\quad\Rightarrow\quad
T_P=\frac{s\left(T_E+T_W\right)+T_N+T_S}{2(1+s)}+\frac{\dot g\,\Delta y^2}{2k(1+s)}.
$$

Do not assume $s=1$ when a question calls a rectangular mesh "equidistant": in [[SESA3029 Past Paper 2019-20 - Solutions#(b) Stencils at nodes 5 and 11, and the check at node 8 [10 marks]|2019–20 Q4(iii)]], $\Delta x=0.20$ m and $\Delta y=0.05$ m give $s=1/16$, so $T_P=[T_W+T_E+16(T_N+T_S)]/34$ rather than the four-neighbour average.

For a **square grid**, $\Delta x=\Delta y$ ($s=1$), this simplifies to

$$
T_E+T_W+T_N+T_S-4T_P+\frac{\dot g\,\Delta x^2}{k}=0
\quad\Rightarrow\quad
T_P=\frac{T_E+T_W+T_N+T_S}{4}+\frac{\dot g\,\Delta x^2}{4k}.
$$

Without generation each interior node is the average of its four neighbours.

## 5. Boundary and corner nodes by energy balance

The difference formulas of §4 need a neighbour on each side, which a node on a boundary does not have. The general way to get a node equation anywhere, and the one that past exam questions use, is an energy balance on the node's own control volume, as in §1 but with finite cells. The control volume around node P extends half a cell in every direction that stays inside the solid (dashed in the figure). Count every heat flow **into** it as positive:

- conduction from a neighbour across a face: $k\times(\text{face length})\times\dfrac{T_{nb}-T_P}{\text{node spacing}}$ (unit depth);
- convection through an exposed boundary: $h\times(\text{exposed length})\times(T_\infty-T_P)$;
- a prescribed heat flux $\dot q$ into the solid: $\dot q\times(\text{boundary length})$;
- generation: $\dot g\times(\text{control-volume area})$.

In steady state these sum to zero. For a transient explicit scheme they sum to $\rho c_p\times(\text{control-volume area})\times(T_P^{n+1}-T_P^n)/\Delta t$, with every right-hand temperature at level $n$ (§10 applies this to a 1-D convective end node).

![[at_w09e_boundary_nodes.png|900]]

**Interior node** (panel (a)), square grid. All four faces have full length $\Delta x$ and spacing $\Delta x$:

$$
k(T_E-T_P)+k(T_W-T_P)+k(T_N-T_P)+k(T_S-T_P)+\dot g\,\Delta x^2=0,
$$

which is the §4 stencil again: the energy balance and the Taylor-series route agree.

**Plane surface with convection** (panel (b)), surface facing $+x$, square grid. The control volume is a half cell $\Delta x/2$ wide and $\Delta y$ tall. The west face has length $\Delta y$; the north and south faces have length $\Delta x/2$; the exposed surface has length $\Delta y$:

$$
k\,\Delta y\,\frac{T_W-T_P}{\Delta x}+k\,\frac{\Delta x}{2}\,\frac{T_N-T_P}{\Delta y}+k\,\frac{\Delta x}{2}\,\frac{T_S-T_P}{\Delta y}+h\,\Delta y\,(T_\infty-T_P)=0 .
$$

With $\Delta x=\Delta y$, multiply by $2/k$ and write $\mathrm{Bi}=h\Delta x/k$ (a grid Biot number):

$$
2(T_W-T_P)+(T_N-T_P)+(T_S-T_P)+2\,\mathrm{Bi}\,(T_\infty-T_P)=0 .
$$

Collect $T_P$:

$$
\boxed{T_P=\frac{2T_W+T_N+T_S+2\,\mathrm{Bi}\,T_\infty}{4+2\,\mathrm{Bi}}}\qquad\left(\mathrm{Bi}=\frac{h\Delta x}{k}\right).
$$

An **insulated surface** is the case $h=0$: $T_P=(2T_W+T_N+T_S)/4$. That is the interior stencil with a mirror-image node $T_E=T_W$, which is why an insulated wall and a plane of symmetry are treated the same way.

**Exterior corner with convection on both faces** (panel (c)). The control volume is a quarter cell. The west face has length $\Delta y/2$, the south face $\Delta x/2$, and the exposed boundary is $\Delta x/2+\Delta y/2$:

$$
k\,\frac{\Delta y}{2}\,\frac{T_W-T_P}{\Delta x}+k\,\frac{\Delta x}{2}\,\frac{T_S-T_P}{\Delta y}+h\left(\frac{\Delta x}{2}+\frac{\Delta y}{2}\right)(T_\infty-T_P)=0 .
$$

With $\Delta x=\Delta y$, multiply by $2/k$:

$$
(T_W-T_P)+(T_S-T_P)+2\,\mathrm{Bi}\,(T_\infty-T_P)=0
\quad\Rightarrow\quad
T_P=\frac{T_W+T_S+2\,\mathrm{Bi}\,T_\infty}{2+2\,\mathrm{Bi}}.
$$

A heat-flux boundary replaces $h(T_\infty-T_P)$ by $\dot q$.

**Internal (re-entrant) corner with a prescribed heat flux** on both boundary edges. The solid fills three quadrants around P, so the control volume is an L-shaped three-quarter cell: the north face (length $\Delta x$) and west face (length $\Delta y$) are full, the east face (length $\Delta y/2$) and south face (length $\Delta x/2$) are half, and the flux $\dot q$ enters through both boundary segments ($\Delta x/2+\Delta y/2$):

$$
k\,\Delta x\,\frac{T_N-T_P}{\Delta y}+k\,\Delta y\,\frac{T_W-T_P}{\Delta x}+k\,\frac{\Delta y}{2}\,\frac{T_E-T_P}{\Delta x}+k\,\frac{\Delta x}{2}\,\frac{T_S-T_P}{\Delta y}+\dot q\left(\frac{\Delta x}{2}+\frac{\Delta y}{2}\right)=0 .
$$

With $\Delta x=\Delta y$, multiply by $2/k$ and collect $T_P$ ($2+2+1+1=6$):

$$
\boxed{6T_P=2T_N+2T_W+T_E+T_S+\frac{2\dot q\,\Delta x}{k}}
$$

(tested directly in [[SESA3029 Past Paper 2024-25 A - Solutions#Q5. Finite-difference stencil at an internal corner with boundary heat flux (10 marks)|2024–25 A Q5]] and [[SESA3029 Past Paper 2024-25 B - Solutions#Q5. Finite-difference stencils for 2D internal corner and 1D radial cylindrical conduction (16 marks)|2024–25 B Q5(i)]]).

**1-D radial cylindrical node** (steady, no generation). Place nodes at $r_i=i\,\Delta r$ ($i\ge1$); the control volume around node $i$ is an annular ring of unit axial length bounded by the mid-point radii $r_{i-1/2}=(i-\tfrac12)\Delta r$ and $r_{i+1/2}=(i+\tfrac12)\Delta r$. The radial heat flow per unit length is $\dot q_r=-2\pi k r\,\partial T/\partial r$, so steady state ($\dot q_{r,\,i-1/2}-\dot q_{r,\,i+1/2}=0$) gives

$$
-2\pi k\left(i-\tfrac12\right)\Delta r\,\frac{T_i-T_{i-1}}{\Delta r}+2\pi k\left(i+\tfrac12\right)\Delta r\,\frac{T_{i+1}-T_i}{\Delta r}=0 .
$$

Dividing by $2\pi k$ and solving for $T_i$:

$$
\left(i-\tfrac12\right)T_{i-1}-2i\,T_i+\left(i+\tfrac12\right)T_{i+1}=0
\quad\Rightarrow\quad
\boxed{T_i=\frac{\left(i-\tfrac12\right)T_{i-1}+\left(i+\tfrac12\right)T_{i+1}}{2i}}.
$$

The outer neighbour carries the larger weight because the outer cylindrical face has the larger area; far from the axis ($i\gg1$) both weights approach $\tfrac12$, recovering the planar average. Regrouping as $i(T_{i+1}-2T_i+T_{i-1})+\tfrac12(T_{i+1}-T_{i-1})=0$ and dividing by $i\,\Delta r^2$ with $r_i=i\,\Delta r$ gives $(T_{i+1}-2T_i+T_{i-1})/\Delta r^2+(1/r_i)(T_{i+1}-T_{i-1})/(2\Delta r)=0$, the second-order central-difference form of $\tfrac{1}{r}\frac{\mathrm d}{\mathrm dr}(r\frac{\mathrm dT}{\mathrm dr})=0$ (tested in [[SESA3029 Past Paper 2023-24 - Solutions#(ix) 1D radial cylindrical finite-difference equation [6 marks]|2023–24 Q1(ix)]] and [[SESA3029 Past Paper 2024-25 B - Solutions#Q5. Finite-difference stencils for 2D internal corner and 1D radial cylindrical conduction (16 marks)|2024–25 B Q5(ii)]]).

### Worked example: a surface node with convection

*A steel wall, $k=15$ W/(m K), on a square grid $\Delta x=\Delta y=0.01$ m, faces a fluid at $T_\infty=20$ °C with $h=100$ W/(m² K). A surface node has $T_W=80$, $T_N=90$ and $T_S=70$ °C. Find the steady $T_P$ (suggested, not lecturer-set).*

$\mathrm{Bi}=100\times0.01/15=0.0667$, so

$$
T_P=\frac{2(80)+90+70+2(0.0667)(20)}{4+2(0.0667)}=\frac{322.67}{4.1333}=78.06\ \text{°C}.
$$

> [!check] Face-by-face balance, per metre depth
> West: $15\times0.01\times(80-78.06)/0.01=+29.0$ W/m. North: $15\times0.005\times(90-78.06)/0.01=+89.5$ W/m. South: $15\times0.005\times(70-78.06)/0.01=-60.5$ W/m. Convection: $100\times0.01\times(20-78.06)=-58.1$ W/m. Sum $=0$ ✓.

## 6. Worked example: 1-D steady conduction

*A rod of length $L=1$ m has its left end held at $T_L=T(0,t)=50$ °C and its right end at $T_R=T(L,t)=100$ °C. Find the steady temperature distribution analytically and by finite differences.*

Analytically, $\mathrm d^2T/\mathrm dx^2=0$ integrates twice to $T=Ax+B$. The left boundary gives $B=T_L$ and the right gives $A=(T_R-T_L)/L$, so

$$
T(x)=T_L+\left(T_R-T_L\right)\frac{x}{L}=50+50x\quad(\text{°C},\ x\text{ in m}).
$$

Numerically, every interior node satisfies $T_i=(T_{i+1}+T_{i-1})/2$ with $T_0=50$ and $T_I=100$. The linear profile satisfies these equations exactly: $T_{i\pm1}=T_i\pm50\Delta x$, so the average of the neighbours is $T_i$. The finite-difference solution therefore lies on the analytical line at every node, for any $\Delta x$. That is the truncation error of §7 at work: it is proportional to $\partial^4T/\partial x^4$, which is zero for a straight line, so this example cannot show the error of the scheme. The transient example of §11 can.

## 7. Order of accuracy

The approximations above drop the higher terms of the Taylor series; what is dropped is the **truncation error**. For the forward difference, expand $T_{i+1}$ about node $i$:

$$
T_{i+1}=T_i+\left(\frac{\partial T}{\partial x}\right)_i\Delta x+\frac12\left(\frac{\partial^2T}{\partial x^2}\right)_i\Delta x^2+\frac{1}{3!}\left(\frac{\partial^3T}{\partial x^3}\right)_i\Delta x^3+\dots
$$

Subtract $T_i$, divide by $\Delta x$ and rearrange for the slope:

$$
\left(\frac{\partial T}{\partial x}\right)_i=\underbrace{\frac{T_{i+1}-T_i}{\Delta x}}_{\text{finite difference form}}\ \underbrace{-\left(\frac{\partial^2T}{\partial x^2}\right)_i\frac{\Delta x}{2}-\left(\frac{\partial^3T}{\partial x^3}\right)_i\frac{\Delta x^2}{3!}-\dots}_{\text{truncation error}}=\frac{T_{i+1}-T_i}{\Delta x}+\mathcal O(\Delta x).
$$

The leading error term is proportional to $\Delta x$, so the forward difference is **first-order** accurate.

For the second derivative, expand both neighbours to fourth order:

$$
T_{i+1}=T_i+T_i'\Delta x+\tfrac12T_i''\Delta x^2+\tfrac16T_i'''\Delta x^3+\tfrac1{24}T_i''''\Delta x^4+\dots
$$

$$
T_{i-1}=T_i-T_i'\Delta x+\tfrac12T_i''\Delta x^2-\tfrac16T_i'''\Delta x^3+\tfrac1{24}T_i''''\Delta x^4-\dots
$$

Add them. The odd terms cancel:

$$
T_{i+1}+T_{i-1}=2T_i+T_i''\Delta x^2+\tfrac1{12}T_i''''\Delta x^4+\dots
$$

Subtract $2T_i$ and divide by $\Delta x^2$:

$$
\left(\frac{\partial^2T}{\partial x^2}\right)_i=\frac{T_{i+1}-2T_i+T_{i-1}}{\Delta x^2}-\frac{\Delta x^2}{12}\left(\frac{\partial^4T}{\partial x^4}\right)_i-\dots=\frac{T_{i+1}-2T_i+T_{i-1}}{\Delta x^2}+\mathcal O(\Delta x^2).
$$

The symmetric (central) difference is **second-order** accurate, because the symmetry cancels the odd error terms. In general

$$
\text{Error}\sim\Delta x^p,
$$

with $\Delta x$ the grid size and $p$ the **order of accuracy**. Doubling the number of grid points halves $\Delta x$, so the error falls by $2^p$: a factor of 2 for a first-order method, 4 for second order and 16 for fourth order. Higher-order methods need fewer grid points for a given accuracy. The order $p$ is a property of the scheme, the same for every smooth function, but the size of the error also contains the derivative in the leading term ($T''$ or $T''''$), which does depend on the function: where that derivative is zero the scheme is exact.

![[at_w09e_order_of_accuracy.png|900]]

> [!check] Errors for $T=\sin x$ at $x=1$
> Forward difference for $T'$: errors $-0.0429$, $-0.0213$, $-0.0106$ at $\Delta x=0.1$, $0.05$, $0.025$, halving each time; the leading term $T''\Delta x/2=-0.0421\,\Delta x/0.1$ predicts them. Central difference for $T''$: errors $7.01\times10^{-4}$, $1.753\times10^{-4}$, $4.383\times10^{-5}$, falling by 4.00 each time, matching $T''''\Delta x^2/12$ to three figures. The slopes in the figure are 1 and 2.

Grid-convergence studies use this behaviour backwards. On three grids with constant refinement ratio $r$ (spacings $r^2h$, $rh$, $h$; commonly $r=2$, halving the spacing each time), the leading error $Ch^p$ makes successive differences shrink by $r^p$, giving the observed order $p$ and the **Richardson extrapolation** estimate of the grid-independent value:

$$
p=\frac{\ln\!\left[(T_{r^2h}-T_{rh})/(T_{rh}-T_h)\right]}{\ln r},
\qquad
\boxed{T_{\text{exact}}\approx T_h+\frac{T_h-T_{rh}}{r^p-1}}.
$$

When $p$ is already known (for example $p=2$ for a central-difference scheme), two grids ($rh$ and $h$) suffice for the second formula; with three grids the first formula checks that the meshes lie in the asymptotic range. Past papers test both: [[SESA3029 Past Paper 2019-20 - Solutions#(iv) Order of accuracy and extrapolation [6 marks]|2019–20 Q4(iv)]] finds $p\approx1.97$ from three grids with $r=2$ before extrapolating, and [[SESA3029 Past Paper 2021-22 - Solutions#Q3. Transient 1D rod cooling by explicit finite difference (30 marks)|2021–22 Q3]], [[SESA3029 Past Paper 2014-15 - Solutions#Q4. Laminar boundary-layer heat transfer, lunar re-entry and Richardson extrapolation (30 marks)|2014–15 Q4(iii)]], [[SESA3029 Past Paper 2015-16 - Solutions#Q4. Dimensionless heat-transfer numbers, laminar plate, lunar re-entry and CFD checks (30 marks)|2015–16 Q4(iv)]] ($p=3$) and [[SESA3029 Past Paper 2017-18 - Solutions#Q5. 1D isentropic Euler characteristics and Richardson extrapolation (16 marks)|2017–18 Q5(ii)]] apply the two-grid formula.

## 8. Accuracy in 2-D and 3-D

The 2-D stencil of §4 has error $\mathcal O(\Delta x^2,\Delta y^2)$, since each direction contributes its own central second difference with the error of §7. In 3-D on a cubic grid the interior equation adds the two $z$-neighbours, $T_P=\tfrac16\sum T_{nb}+\dot g\Delta x^2/(6k)$, with the same order. The 1-D analysis therefore carries over direction by direction.

## 9. Transient conduction: explicit and implicit schemes

In 1-D, for transient conduction without a heat source, the heat diffusion equation is

$$
\frac{\partial^2T}{\partial x^2}=\frac{1}{\alpha}\frac{\partial T}{\partial t}.
$$

Now the temperature must be discretised in time as well as space, with time levels $t^n=n\Delta t$ and $T_i^n=T(x_i,t^n)$. This makes a transient calculation more expensive than a steady one: the spatial problem is solved once per time step. The space–time grid is panel (b) of the figure in §1.

**Explicit scheme.** Evaluate the second derivative at the old time level $n$, where everything is known, and the time derivative by a forward difference from $n$ to $n+1$:

$$
\frac{T_{i+1}^n-2T_i^n+T_{i-1}^n}{\Delta x^2}=\frac{1}{\alpha}\,\frac{T_i^{n+1}-T_i^n}{\Delta t}.
$$

Multiply both sides by $\alpha\Delta t$:

$$
T_i^{n+1}-T_i^n=\frac{\alpha\Delta t}{\Delta x^2}\left(T_{i+1}^n-2T_i^n+T_{i-1}^n\right).
$$

The group on the right is the **Fourier number**,

$$
\mathcal F=\frac{\alpha\,\Delta t}{\Delta x^2},
$$

the time step measured in units of the diffusion time across one cell. The scheme becomes the iteration rule

$$
\boxed{T_i^{n+1}=T_i^n+\mathcal F\left(T_{i+1}^n-2T_i^n+T_{i-1}^n\right)}
$$

It is **explicit in time** because each new value is calculated directly from values at the previous time step, one node at a time, with no equations to solve. The future state comes from the current state. Collected by old temperatures it reads

$$
T_i^{n+1}=\mathcal F\,T_{i-1}^n+\left(1-2\mathcal F\right)T_i^n+\mathcal F\,T_{i+1}^n,
$$

which §10 uses for stability.

**Implicit scheme.** Evaluate the second derivative at the new time level $n+1$ instead:

$$
\frac{T_{i+1}^{n+1}-2T_i^{n+1}+T_{i-1}^{n+1}}{\Delta x^2}=\frac{1}{\alpha}\,\frac{T_i^{n+1}-T_i^n}{\Delta t}.
$$

Multiply by $\Delta x^2$ and use $\Delta x^2/(\alpha\Delta t)=1/\mathcal F$:

$$
T_{i+1}^{n+1}-2T_i^{n+1}+T_{i-1}^{n+1}=\frac{1}{\mathcal F}\left(T_i^{n+1}-T_i^n\right).
$$

Move the unknown $T_i^{n+1}$ term to the left:

$$
\boxed{T_{i+1}^{n+1}-\left(2+\frac{1}{\mathcal F}\right)T_i^{n+1}+T_{i-1}^{n+1}=-\frac{1}{\mathcal F}T_i^n}
$$

It is **implicit in time** because each equation contains the unknown new values at three nodes. The equations for all interior nodes have to be solved together as a tridiagonal system, by the Thomas algorithm or any linear solver, once per step. Each step costs more than an explicit step, but §10 shows the step can be much larger. The same two schemes for the model heat problem are in [[SESA2029 A4 - Time Marching - Explicit and Implicit Methods|SESA2029 A4]] and [[Explicit and Implicit Time Integration]].

**Order of accuracy.** The forward difference in time has the error of §7 with $t$ in place of $x$: expand $T_i^{n+1}$ about $t^n$,

$$
T_i^{n+1}=T_i^n+\left(\frac{\partial T}{\partial t}\right)_i^n\Delta t+\frac12\left(\frac{\partial^2T}{\partial t^2}\right)_i^n\Delta t^2+\dots
\quad\Rightarrow\quad
\left(\frac{\partial T}{\partial t}\right)_i^n=\frac{T_i^{n+1}-T_i^n}{\Delta t}+\mathcal O(\Delta t).
$$

With the $\mathcal O(\Delta x^2)$ spatial difference, the truncation error of either scheme is $\mathcal O(\Delta t,\Delta x^2)$: second order in space, first order in time, so first order overall. If $\mathcal F$ is held fixed while the grid is refined, $\Delta t\propto\Delta x^2$ and both parts of the error fall as $\Delta x^2$.

## 10. Stability of the explicit scheme

Nothing in §9 restricts the size of the time step, but the explicit scheme fails if it is too large. Two short arguments give the limit. Both assume a uniform grid, constant $\alpha$, no generation and fixed-temperature (or periodic) boundaries.

**Positive coefficients.** In the collected form

$$
T_i^{n+1}=\mathcal F\,T_{i-1}^n+\left(1-2\mathcal F\right)T_i^n+\mathcal F\,T_{i+1}^n,
$$

the three coefficients add up to $\mathcal F+1-2\mathcal F+\mathcal F=1$. If all three are non-negative, the new value is a weighted average of the three old values, so it cannot lie outside their range: no new maxima or minima can appear, and the solution stays bounded, as diffusion does physically. The middle coefficient is non-negative when

$$
1-2\mathcal F\ge0\quad\Rightarrow\quad\boxed{\mathcal F=\frac{\alpha\Delta t}{\Delta x^2}\le\frac12}\qquad(\text{1-D, explicit}).
$$

If $\mathcal F>\tfrac12$, the middle coefficient is negative: a node that is hotter than its neighbours becomes colder than them after one step, which is unphysical (heat would flow from cold to hot), and the overshoot grows each step.

**Von Neumann analysis.** Put a single Fourier mode into the explicit scheme, $T_i^n=G^n e^{\mathrm ik x_i}$, with $G$ the amplification factor per step. Using $e^{\mathrm ik\Delta x}+e^{-\mathrm ik\Delta x}=2\cos k\Delta x$,

$$
G=1+\mathcal F\left(2\cos k\Delta x-2\right)=1-4\mathcal F\sin^2\frac{k\Delta x}{2}.
$$

Stability needs $|G|\le1$ for every wavenumber. $G\le1$ always; the worst case for $G\ge-1$ is the sawtooth mode $k\Delta x=\pi$, where $G=1-4\mathcal F$, so again $\mathcal F\le\tfrac12$. The same analysis of the implicit scheme gives

$$
G=\frac{1}{1+4\mathcal F\sin^2(k\Delta x/2)},
$$

which lies between 0 and 1 for every $\mathcal F>0$: the implicit scheme is **unconditionally stable**. The full analysis is in [[SESA2029 A5 - Numerical Stability - Von Neumann Analysis, Fourier and CFL Numbers|SESA2029 A5]] and [[CFL and Fourier Numbers]].

![[at_w09e_stability.png|900]]

The left panel uses the rod of §11 with $\Delta x=0.05$ m. At $\mathcal F=0.40$ and $0.50$ the explicit solution lies on the exact one; at $\mathcal F=0.55$ a sawtooth appears after 22 steps and grows without limit. In 2-D on a square grid the explicit interior coefficient is $1-4\mathcal F$, so the limit is $\mathcal F\le\tfrac14$, and boundary nodes with convection are stricter still, as shown below. Because $\Delta t\le\Delta x^2/(2\alpha)$, halving the mesh size quarters the allowed time step, which is the price of the explicit scheme on fine grids. Stability is not accuracy: the implicit scheme gives a bounded answer at any $\mathcal F$, but a large $\Delta t$ still gives a large $\mathcal O(\Delta t)$ error.

**Explicit transient boundary node, 1-D, with convection.** Node 0 at a surface facing a fluid owns a half cell $\Delta x/2$ long (per unit cross-sectional area):

$$
\rho c_p\,\frac{\Delta x}{2}\,\frac{T_0^{n+1}-T_0^n}{\Delta t}=k\,\frac{T_1^n-T_0^n}{\Delta x}+h\left(T_\infty-T_0^n\right).
$$

Multiply by $2\Delta t/(\rho c_p\Delta x)$ and use $\mathcal F=\alpha\Delta t/\Delta x^2$, $\mathrm{Bi}=h\Delta x/k$:

$$
T_0^{n+1}-T_0^n=2\mathcal F\left(T_1^n-T_0^n\right)+2\mathcal F\,\mathrm{Bi}\left(T_\infty-T_0^n\right).
$$

Collect the old temperatures:

$$
T_0^{n+1}=2\mathcal F\,T_1^n+\left(1-2\mathcal F-2\mathcal F\,\mathrm{Bi}\right)T_0^n+2\mathcal F\,\mathrm{Bi}\,T_\infty .
$$

The coefficient of $T_0^n$ must be non-negative, so at this node

$$
\mathcal F\left(1+\mathrm{Bi}\right)\le\frac12 ,
$$

stricter than the interior limit $\mathcal F\le\tfrac12$. The time step for the whole mesh is set by the most restrictive node. A rod cooled along its length as well adds a side-convection term to every node; that is [[SESA3029 Past Paper 2021-22 - Solutions#Q3. Transient 1D rod cooling by explicit finite difference (30 marks)|2021–22 Q3]].

## 11. Worked example: 1-D transient conduction

*The rod of §6 ($L=1$ m) is initially at 50 °C throughout. From $t=0$ its left end stays at $T_L=50$ °C and its right end is held at $T_R=100$ °C. Find $T(x,t)$ analytically and by the explicit scheme with $\Delta x=0.025$ m and $\Delta t=2.5$ s.*

**Analytical solution.** Split $T$ into the steady profile of §6 and a transient part $u$ that decays:

$$
T(x,t)=T_L+\left(T_R-T_L\right)\frac xL+u(x,t).
$$

The steady part already satisfies both boundary values and the heat equation, so $u$ satisfies $u_{xx}=u_t/\alpha$ with $u(0,t)=u(L,t)=0$. Its initial value is the initial temperature minus the steady profile:

$$
u(x,0)=T_L-\left[T_L+\left(T_R-T_L\right)\frac xL\right]=-\left(T_R-T_L\right)\frac xL .
$$

Separation of variables with zero end values gives sine modes, each decaying at its own rate ([[Heat Equation]]):

$$
u(x,t)=\sum_{n=1}^\infty b_n\sin\left(\frac{n\pi x}{L}\right)e^{-\alpha\left(n\pi/L\right)^2t}.
$$

The coefficients are the Fourier sine coefficients of $u(x,0)$:

$$
b_n=\frac2L\int_0^L-\left(T_R-T_L\right)\frac xL\sin\left(\frac{n\pi x}{L}\right)\mathrm dx .
$$

Integrating by parts, $\int_0^Lx\sin(n\pi x/L)\,\mathrm dx=-L^2\cos(n\pi)/(n\pi)=(-1)^{n+1}L^2/(n\pi)$, so

$$
b_n=-\frac{2\left(T_R-T_L\right)}{L^2}\cdot\frac{(-1)^{n+1}L^2}{n\pi}=\frac{2\left(T_R-T_L\right)(-1)^n}{n\pi}.
$$

Hence

$$
\boxed{T(x,t)=T_L+\left(T_R-T_L\right)\frac xL+\sum_{n=1}^\infty\left[\frac{2\left(T_R-T_L\right)(-1)^n}{n\pi}\sin\left(\frac{n\pi x}{L}\right)e^{-\alpha\left(n\pi/L\right)^2t}\right]}
$$

At $t=0$ the series sums to $-(T_R-T_L)x/L$, so $T=T_L=50$ °C everywhere inside the rod, which confirms the initial condition (with 4000 terms the sum gives 50.00 °C at $x=0.2$, $0.5$ and $0.8$). The slowest mode, $n=1$, decays with time constant $L^2/(\pi^2\alpha)$.

**Numerical solution.** The diffusivity is not specified; take $\alpha=1.0\times10^{-4}$ m²/s, close to copper. Then

$$
\mathcal F=\frac{\alpha\Delta t}{\Delta x^2}=\frac{(1.0\times10^{-4})(2.5)}{0.025^2}=0.40\le\frac12 ,
$$

so the explicit scheme is stable. Marching $T_i^{n+1}=T_i^n+0.4(T_{i+1}^n-2T_i^n+T_{i-1}^n)$ from $T_i^0=50$ °C with the end values fixed reproduces the series solution to within 0.13 °C at $t=125$ s (50 steps), and as closely at later times (figure, panel (a)). The time constant of the slowest mode is $1/(\pi^2\times10^{-4})=1013$ s; by $t=5000$ s it has decayed to $e^{-4.93}=0.7\,\%$ of its initial size and the rod is at the steady straight line.

![[at_w09e_transient_example.png|900]]

Panel (b) shows why the initial condition must match. A numerical run started from 0 °C inside the rod, instead of 50 °C, gives a curve that falls to nearly 0 °C in the middle at $t=125$ s, 50 °C below the analytical one there. Nothing is wrong with the scheme in that case; it is solving a different problem. The heat has only diffused about $\sqrt{\alpha t}=0.11$ m in from each end, so the middle of the rod still remembers its initial temperature. A comparison of a numerical and an analytical solution is only a test of the scheme when both solve the same initial-boundary-value problem.

## Worked example: one explicit and one implicit step by hand

*Same rod, same $\alpha=1.0\times10^{-4}$ m²/s, but with only four intervals: $\Delta x=0.25$ m, nodes 0–4. Take $\mathcal F=0.4$. Find the temperatures after the first steps by the explicit and the implicit schemes, and compare with the series solution (suggested, not lecturer-set).*

The time step is $\Delta t=\mathcal F\Delta x^2/\alpha=0.4\times0.0625/10^{-4}=250$ s. At $t=0$: $T_0=50$, $T_1=T_2=T_3=50$, $T_4=100$ °C.

**Explicit.** $T_i^{n+1}=T_i^n+0.4(T_{i+1}^n-2T_i^n+T_{i-1}^n)$:

$$
T_1^1=50+0.4(50-100+50)=50,\qquad T_2^1=50+0.4(50-100+50)=50,\qquad T_3^1=50+0.4(100-100+50)=70 .
$$

Second step:

$$
T_1^2=50+0.4(50-100+50)=50,\quad T_2^2=50+0.4(70-100+50)=58,\quad T_3^2=70+0.4(100-140+50)=74 .
$$

A third step gives $53.2$, $61.2$ and $78.0$ °C at $t=750$ s. In the explicit scheme the heating front moves exactly one node per step: node 1 does not feel the hot end until the third step.

**Implicit.** With $1/\mathcal F=2.5$ each equation is $T_{i+1}^{n+1}-4.5\,T_i^{n+1}+T_{i-1}^{n+1}=-2.5\,T_i^n$, with the known end values moved to the right:

$$
\begin{aligned}
-4.5\,T_1+T_2&=-2.5(50)-50=-175,\\
T_1-4.5\,T_2+T_3&=-2.5(50)=-125,\\
T_2-4.5\,T_3&=-2.5(50)-100=-225.
\end{aligned}
$$

Solving gives $T_1^1=50.61$, $T_2^1=52.74$, $T_3^1=61.72$ °C. Every node feels the hot end within one step, as in the real solution, because the system couples all nodes at the new level. Further steps give $(51.70,\ 56.12,\ 68.98)$ at 500 s and $(53.02,\ 59.34,\ 73.73)$ at 750 s.

| $t$ (s) | Node | Explicit | Implicit | Series (exact) |
|---:|---|---:|---:|---:|
| 250 | 1, 2, 3 | 50.00, 50.00, 70.00 | 50.61, 52.74, 61.72 | 50.04, 51.27, 63.18 |
| 500 | 1, 2, 3 | 50.00, 58.00, 74.00 | 51.70, 56.12, 68.98 | 50.88, 55.69, 71.46 |
| 750 | 1, 2, 3 | 53.20, 61.20, 78.00 | 53.02, 59.34, 73.73 | 52.58, 59.83, 75.93 |

> [!check] Checks
> The implicit values satisfy the three equations to within $2\times10^{-4}$ (rounding). The series values are confirmed by an explicit run on a grid twenty times finer ($\Delta x=0.0125$ m, $\mathcal F=0.16$), which gives 52.58, 59.83, 75.93 at 750 s. On this coarse grid the explicit scheme runs ahead of the exact solution near the hot end and the implicit lags behind it: the two first-order time errors have opposite signs.

## Problem-solving workflow

1. Draw the grid and label each node by type: interior, surface (with what condition), corner (exterior or internal).
2. For each node type, draw its control volume and write the energy balance of §5; for interior nodes on a square grid, use the four-neighbour average directly.
3. Steady problems: collect into a linear system and solve (by hand for a few nodes, or by Gauss–Seidel iteration).
4. Transient problems: choose explicit or implicit. For explicit, find the largest $\mathcal F$ allowed by every node type ($\tfrac12$ interior 1-D, $\tfrac14$ interior 2-D, $\tfrac12(1+\mathrm{Bi})^{-1}$ at a 1-D convective end) and pick $\Delta t$ below it.
5. Check: face flows sum to zero (steady); temperatures stay within the boundary and initial values (diffusion cannot create new extremes); grid refinement changes the answer by the factor the order of accuracy predicts.

## Terminology and alternative names

| Course term | Also called | Where the course uses it | Note |
|---|---|---|---|
| heat diffusion equation | heat conduction equation; heat equation; diffusion equation | 5.7 slides 2–8 | MATH2048 note: [[Heat Equation]] |
| finite difference form | difference equation; discretised equation | 5.7 slide 11 | the set of nodes an equation uses is its stencil (a standard term, not the course's) |
| Fourier number $\mathcal F=\alpha\Delta t/\Delta x^2$ | mesh Fourier number; diffusion number; $r$ or $\lambda$ in numerical-analysis texts | 5.7 slide 15 | the physical Fourier number $\alpha t/L^2$ uses a body length and total time |
| explicit (in time) | forward-time centred-space (FTCS); forward Euler | 5.7 slides 14–15 | |
| implicit (in time) | backward-time centred-space (BTCS); backward (implicit) Euler; fully implicit | 5.7 slide 16 | |
| truncation error | discretisation error (strictly the global error it produces) | 5.7 slides 12, 17 | |
| adiabatic or insulated surface | zero-flux (Neumann) boundary; symmetry plane | 5.7 slide 8 | |
| constant temperature condition | Dirichlet boundary condition; boundary condition of the first kind | 5.7 slide 8 | |

## Links

- Parent: [[SESA3029 Aerothermodynamics Hub]]
- Previous: [[SESA3029 W09d - Thermal Radiation]] · Next: [[SESA3029 W09f - Heat Exchangers]]
- New concepts: [[Finite-Difference Form of the Heat Equation]] · [[Thermal Diffusivity]]
- Block 5: [[SESA3029 W09a - Heat Conduction and Thermal Resistance]] (Fourier's law, the analytical results) · [[SESA3029 W09b - Convective Heat Transfer and the Reynolds Analogy]] (the convection boundary condition)
- Earlier years: [[Heat Equation]] (MATH2048) · [[SESA2029 A2 - Discrete Data, Finite Differences and Taylor Tables]] · [[SESA2029 A3 - Iterative Solution of the Steady Heat Equation]] · [[SESA2029 A4 - Time Marching - Explicit and Implicit Methods]] · [[SESA2029 A5 - Numerical Stability - Von Neumann Analysis, Fourier and CFL Numbers]] · [[Finite Difference Approximations]] · [[Truncation Error and Order of Accuracy]] · [[Explicit and Implicit Time Integration]] · [[CFL and Fourier Numbers]]
- Past papers (finite-difference stencils): [[SESA3029 Past Paper 2019-20 - Solutions#Q4. High-temperature block convection, 2D finite difference and grid convergence (32 marks)|2019–20 Q4]] · [[SESA3029 Past Paper 2020-21 - Solutions#(ii) 2D finite-difference solve [15 marks]|2020–21 Q3(ii)]] · [[SESA3029 Past Paper 2021-22 - Solutions#Q3. Transient 1D rod cooling by explicit finite difference (30 marks)|2021–22 Q3]] · [[SESA3029 Past Paper 2023-24 - Solutions#(ix) 1D radial cylindrical finite-difference equation [6 marks]|2023–24 Q1(ix)]] · [[SESA3029 Past Paper 2024-25 A - Solutions#Q5. Finite-difference stencil at an internal corner with boundary heat flux (10 marks)|2024–25 A Q5]] · [[SESA3029 Past Paper 2024-25 B - Solutions#Q5. Finite-difference stencils for 2D internal corner and 1D radial cylindrical conduction (16 marks)|2024–25 B Q5]]

## Sources

- `Lecture5.7.pdf`: Lecture 5.7, Numerical methods in conduction, 20 slides: the 2-D heat conduction equation from an element energy balance (slides 2–6), thermal diffusivity (7), the heat diffusion equation and its boundary conditions (8), why numerical methods (9), discretising the heat equation (10–11), order of accuracy (12–13), transient conduction, explicit scheme and Fourier number (14–15), implicit scheme (16), order of accuracy in time (17), the 1-D steady example (18), the 1-D transient example with its series solution and an explicit-scheme animation (19–20).
- The deck is last year's file re-issued, with no lecturer named on it. The lecture is expected in early December 2026. This note is written from the slides alone, with no transcript yet, and will be reconciled with the transcript once the lecture has been given.
- Beyond the slides: the truncation error of the central second difference (§7), the series solution's derivation (§11), the stability limits (§10; the slides introduce the Fourier number but state no limit), the boundary and corner nodes (§5, which the past papers test), and both hand-worked examples. The value $\alpha=1.0\times10^{-4}$ m²/s in §11 is inferred by matching the plotted curves; the slides do not give it.
- Figures: `generate_aerothermo_w09de_figures.py` (`at_w09e_control_volume_and_stencils.png`, `at_w09e_order_of_accuracy.png`, `at_w09e_transient_example.png`, `at_w09e_stability.png`, `at_w09e_boundary_nodes.png`); every curve is computed, the series with 1500 terms.
- Çengel and Ghajar, *Heat and Mass Transfer*, Ch. 5 (numerical methods in heat conduction); Incropera et al., *Fundamentals of Heat and Mass Transfer*, §§4.4–4.5 and 5.10.

## Self-study tasks

No transcript yet; the tasks below cite the slide where each derivation or example appears. Tasks marked so are suggested, not lecturer-set.

### Core

- [ ] **(5.7 slides 4–6)** Derive the 2-D heat diffusion equation from the energy balance on a $\delta x\times\delta y$ element with generation. → [[#1. The heat conduction equation in 2-D|§1]]
- [ ] **(5.7 slides 10–11)** Derive $\partial^2T/\partial x^2\approx(T_{i+1}-2T_i+T_{i-1})/\Delta x^2$ from the half-point gradients, and show by Taylor series that its error is $\mathcal O(\Delta x^2)$. → [[#4. Discretising the heat equation|§4]] · [[#7. Order of accuracy|§7]]
- [ ] **(5.7 slides 14–16)** Derive the explicit iteration rule and the implicit equation in terms of $\mathcal F$. → [[#9. Transient conduction: explicit and implicit schemes|§9]]
- [ ] (suggested, not lecturer-set) Show that the explicit scheme needs $\mathcal F\le\tfrac12$, and find the limit at a convective end node. Answer $\mathcal F(1+\mathrm{Bi})\le\tfrac12$. → [[#10. Stability of the explicit scheme|§10]]
- [ ] **(past papers)** Internal-corner stencil with a heat flux: [[SESA3029 Past Paper 2024-25 A - Solutions#Q5. Finite-difference stencil at an internal corner with boundary heat flux (10 marks)|2024–25 A Q5]]. Answer $T_P=300$ °C.

### Further practice

- [ ] **(5.7 slide 19)** Derive the series solution of the transient rod and check that it gives 50 °C inside the rod at $t=0$. → [[#11. Worked example: 1-D transient conduction|§11]]
- [ ] **(5.7 slide 18)** Explain why the finite-difference solution of the steady rod is exact on any grid. → [[#6. Worked example: 1-D steady conduction|§6]]
- [ ] **(5.7 slide 13)** By how much does the error of a second-order scheme fall when the number of grid points is doubled? Of a fourth-order scheme? Answers 4, 16. → [[#7. Order of accuracy|§7]]
- [ ] (suggested, not lecturer-set) Three explicit and three implicit steps on the four-interval rod with $\mathcal F=0.4$. → [[#Worked example: one explicit and one implicit step by hand|worked example]]
- [ ] (suggested, not lecturer-set) Surface node with convection: $T_P=78.06$ °C. → [[#Worked example: a surface node with convection|worked example]]
- [ ] Past papers: transient rod by explicit FD with Richardson extrapolation, [[SESA3029 Past Paper 2021-22 - Solutions#Q3. Transient 1D rod cooling by explicit finite difference (30 marks)|2021–22 Q3]]; 2-D blocks, [[SESA3029 Past Paper 2019-20 - Solutions#Q4. High-temperature block convection, 2D finite difference and grid convergence (32 marks)|2019–20 Q4]] and [[SESA3029 Past Paper 2022-23 - Solutions|2022–23 Q4]]; radial stencil, [[SESA3029 Past Paper 2023-24 - Solutions#(ix) 1D radial cylindrical finite-difference equation [6 marks]|2023–24 Q1(ix)]].

## Transcript and slide slips

> [!warning] Numerical and analytical curves start from different temperatures (5.7 slide 20)
> Where: [[#11. Worked example: 1-D transient conduction]].
>
> The series on slide 19 starts the rod at 50 °C (it sums to $T_L$ at $t=0$), but the "Numerical" curve on slide 20 at $t=125$ s falls to about 0 °C mid-rod, which is the explicit scheme started from 0 °C. With $\alpha=1.0\times10^{-4}$ m²/s the 0 °C run gives 10.4 °C at $x=0.2$ and 20.8 °C at $x=0.8$, matching the plotted curve; started from 50 °C the same scheme agrees with the series to within 0.13 °C. The large gap on the slide is the initial condition, not the scheme.

> [!warning] "Minimal difference (~23 °C)" cannot be checked (5.7 slide 20)
> Where: [[#11. Worked example: 1-D transient conduction]].
>
> The slide states that the minimal difference, about 23 °C, occurs at $\Delta x=0.063$, $\Delta t=0.0391$. Neither $\alpha$ nor the measure of difference is given, and with the mismatched initial condition above the difference is dominated by the initial temperature, not by $\Delta x$ or $\Delta t$ (the mean absolute difference at 125 s is about 36 °C and the maximum about 50 °C on the 0.025/2.5 grid). The pair has $\Delta t/\Delta x^2=10.0$ s/m² (with $\Delta x=1/16$), so $\mathcal F=10\alpha$ with $\alpha$ in m²/s. To be settled from the lecture.

> [!warning] Order of accuracy and the function (5.7 slide 13)
> Where: [[#7. Order of accuracy]].
>
> "Does not depend on the function being approximated" holds for the order $p$, the rate at which the error falls. The size of the error does depend on the function through the derivative in the leading term ($T''''$ for the central second difference), and it is zero for the straight-line profile of the steady example.

> [!warning] Smaller points
> Where: [[#9. Transient conduction: explicit and implicit schemes]].
>
> Slide 17 is headed "Taylore series expansion" (Taylor). Slides 15–16 introduce the Fourier number without the stability limit $\mathcal F\le\tfrac12$ of the explicit scheme (§10). The same symbol $\alpha$ is thermal diffusivity here and absorptivity in Lecture 5.5.
