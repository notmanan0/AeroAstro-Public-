---
title: "SESA1016 T12 - Conservation of Momentum"
module: "SESA1016 Thermofluids"
type: topic
stream: "Part D: Control-volume Conservation Laws"
order: 12
tags: [sesa1016, momentum, control-volume, thrust, forces]
aliases: ["Momentum Equation", "Linear Momentum Balance"]
date: 2026-09-25
status: lectured
coverage: "Lecture of 24 Mar 2025 (ll. 32–655: momentum of a fluid particle, momentum flow rate for uniform, inclined and general flow, momentum conservation for a control volume, the two-port form, deflecting-vane example); mock-exam solutions of 13 May 2025 (ll. 200–298: disc supported by a water jet); Chapter 12 in full, including the water jet pack (Example 12.3) from the lecture notes"
parent: ["[[SESA1016 Thermofluids Hub]]"]
prerequisites: ["[[SESA1016 T11 - Conservation of Mass]]"]
next_topics: ["[[SESA1016 T13 - Conservation of Energy and Propulsion]]"]
key_concepts: ["[[Momentum Flux]]", "[[Control-volume Analysis Workflow]]"]
tutorial_sheets: ["[[SESA1016 Problem Sheet 09 - Momentum and Energy Conservation Solutions]]"]
sources: ["02 - Sources/Lectures/Chapter 12.pdf", "02 - Sources/Lectures/SESA1016 Lecture 2025-03-24.txt", "02 - Sources/Lectures/SESA1016 Lecture 2025-05-13.txt", "02 - Sources/Tutorial Sheets/Problem Sheet 09 - Momentum and Energy Conservation.pdf"]
---

# SESA1016 T12 - Conservation of Momentum

> [!abstract] Summary
> Fluid crossing a surface carries momentum with it at a rate $\dot{\vec M}=\int_A\rho\vec V(\vec V\cdot\vec n)\,dA$, which for uniform flow is $\dot m\vec V$; each component can be positive, zero or negative. Newton's second law for a fixed control volume says the sum of the forces on the fluid inside equals the rate of change of momentum inside plus the net outflow of momentum. For steady flow with one inlet and one outlet this is $\sum\vec F=\dot m(\vec V_{out}-\vec V_{in})$, which gives the force on a deflecting vane, the load on a pipe bend, the thrust of a rocket or jet engine and the drag of a wing from a wake survey.

> [!summary]- Exam use: quick path
> - **Use it when:** a force on a device that turns, speeds up or slows down a flow is wanted (vanes, bends, nozzles, jets, thrust reversers), or a force is to be inferred from measured velocities (wake surveys).
> - **Assumptions:** fixed control volume, steady flow, uniform properties over each port (otherwise integrate), weight of fluid neglected unless stated.
> - **Method:** 1. Draw the control volume through the ports, mark $\vec n$ outwards and choose $x$, $y$ axes. 2. Draw every force on the fluid: unknown device forces in the positive directions, gauge pressure times area on each port pushing inwards, weights. 3. Find $\dot m$ and port velocities from continuity, and port pressures from Bernoulli if needed. 4. For each axis write $\sum F=\sum_{out}\dot mV-\sum_{in}\dot mV$, keeping the sign of each velocity component. 5. A negative answer means the force acts the other way; the force on the device is equal and opposite to the force on the fluid.
> - **Common mistakes:** forgetting the pressure force at a port that is not at atmospheric pressure; giving every outflow a positive momentum, when an outflow moving in the $-y$ direction carries negative $y$-momentum.
> - **Practise:** [[#Worked example - jet deflected by a vane]] · [[SESA1016 Problem Sheet 09 - Momentum and Energy Conservation Solutions]] Q9.2–Q9.5

Air does not feel as though it has much momentum, but moving fast it carries plenty: enough to lift an aircraft through its wings and push it along through its engines. A water jet pack lifts a person on two downward jets; an F-35 hovers on its lift fan and nozzle. The forces on such devices are related to the momentum of the fluid passing through them (24 Mar, ll. 115–146).

For a single particle Newton's second law gives the relation: the net force equals the rate of change of momentum. Following every particle through a jet engine is impossible, so, as with mass ([[SESA1016 T11 - Conservation of Mass|T11]]), a control volume is drawn round the device and accounts are kept at its surface. If each kilogram leaves with a different velocity from the one it arrived with, something inside must have pushed it, and the force is the momentum carried out per second minus the momentum carried in per second (24 Mar, ll. 476–494). The details inside the box, the blades, flame and shock waves, never need to be known.

Momentum is a vector, so the accounts are kept separately in each direction, with care over signs: fluid leaving the box downwards carries negative $y$-momentum out, and fluid entering moving to the right brings positive $x$-momentum in, which counts negatively as an inflow.

---

## 1. Momentum of a fluid

A solid particle of mass $m$ and velocity $\vec V$ has linear momentum

$$
\vec M=m\vec V
$$

a vector with three components $M_x$, $M_y$, $M_z$. Newton's second law says the vector sum of the forces on it equals the rate of change of momentum:

$$
\sum\vec F=\frac{d\vec M}{dt}=\frac{d(m\vec V)}{dt}
$$

which for constant mass is $m\,d\vec V/dt$. It is a vector equation, so it holds in each of the three directions separately.

A fluid particle of mass $m$ and volume $\mathcal V$ has momentum defined in the same way; writing the mass as $\rho\mathcal V$,

$$
\vec M=m\vec V=\rho\mathcal V\vec V
$$

This is extensive. Two intensive versions appear constantly: dividing by the mass gives $\vec V$, so **velocity is momentum per unit mass**; dividing by the volume gives $\rho\vec V$, the **momentum per unit volume** (24 Mar, ll. 98–111). Wherever $\rho$ appears in a flow quantity it signals "per unit volume".

## 2. Flow of momentum

### Uniform flow along the axis

Take uniform flow at velocity $V_x$ out of a duct of area $A$ aligned with the $x$ axis (24 Mar, ll. 152–226). In a short time $dt$ a slab of fluid of length $dl=V_x\,dt$ leaves, of volume

$$
d\mathcal V=A\,dl=AV_x\,dt
$$

Its $x$-momentum is the momentum per unit volume times the volume:

$$
dM_x=\rho V_x\,d\mathcal V=\rho V_x^2A\,dt
$$

Dividing by $dt$ gives the **momentum flow rate** (momentum flux) in $x$:

$$
\boxed{\dot M_x=\rho V_x^2A=\dot mV_x}
$$

using $\dot m=\rho V_xA$. The second form reads as mass per unit time times momentum per unit mass, which leaves momentum per unit time. Since $\rho V^2$ has the dimensions of pressure, $\dot M_x$ has the dimensions of a force.

The $y$-momentum leaving in the same time is $\rho V_y\,d\mathcal V$, and since this fluid moves purely along $x$, $V_y=0$:

$$
\dot M_y=0
$$

There is a flow of mass but no flow of $y$-momentum, because the fluid crossing the section has no $y$-momentum to carry.

### Flow at an angle to the axes

With the duct tilted downwards and the axes fixed (24 Mar, ll. 249–285), the velocity has components $V_x$ and $V_y<0$, and the slab leaving in $dt$ has length $|\vec V|dt$ and volume $A|\vec V|dt$. Its momentum in each direction is $\rho V_x$ or $\rho V_y$ times that volume, so

$$
\dot M_x=\rho V_x|\vec V|A=\dot mV_x,\qquad \dot M_y=\rho V_y|\vec V|A=\dot mV_y
$$

with $\dot m=\rho|\vec V|A$. Here $\dot M_y<0$: fluid is flowing out, but it carries negative $y$-momentum. Unlike the outflow of mass, an outflow of momentum can be **positive, zero or negative**, matching the fact that the forces that change momentum can point any way.

### General case

For non-uniform flow at an angle to a surface, take an element $dA$ with unit normal $\vec n$. Only the normal velocity $V_n=\vec V\cdot\vec n$ carries fluid through it, so in time $dt$ a volume $d\mathcal V=dA\,V_n\,dt$ crosses. That fluid has mass $\rho\,d\mathcal V$ and moves with the full velocity $\vec V$ (tangential part included), so its momentum is

$$
d\vec M=\rho\vec V\,d\mathcal V=\rho\vec V(\vec V\cdot\vec n)\,dA\,dt
$$

with components

$$
dM_x=\rho V_x(\vec V\cdot\vec n)\,dA\,dt,\qquad dM_y=\rho V_y(\vec V\cdot\vec n)\,dA\,dt
$$

Divide by $dt$ and integrate over the surface:

$$
\boxed{\dot{\vec M}=\int_A\rho\vec V(\vec V\cdot\vec n)\,dA},\qquad \dot M_x=\int_A\rho V_x(\vec V\cdot\vec n)\,dA,\quad \dot M_y=\int_A\rho V_y(\vec V\cdot\vec n)\,dA
$$

Compared with the mass flow rate $\int_A\rho\vec V\cdot\vec n\,dA$ of T11 there is one extra $\vec V$, the momentum per unit mass. Always define the axes before resolving momentum.

### Special cases

For flow perpendicular to the surface, $\vec V\cdot\vec n=V=|\vec V|$, so $\dot M_x=\int_A\rho V_xV\,dA$. For uniform flow $\rho$ and $\vec V$ come out of the integral:

$$
\boxed{\dot M_x=\rho V_xVA=\dot mV_x,\qquad \dot M_y=\rho V_yVA=\dot mV_y}
$$

the forms used in almost every problem.

For a non-uniform profile the momentum flow is **not** $\dot m\bar V$. In the linear channel profile of [[SESA1016 T11 - Conservation of Mass#Worked example - triangular velocity profile|T11]], $v=Vy/h$ (Chapter 12, Example 12.1),

$$
\dot M_x=\int_0^h\rho\,v\,v\,w\,dy=\rho V^2\frac{w}{h^2}\int_0^hy^2\,dy=\tfrac13\rho V^2wh
$$

while $\dot m\bar V=\rho(V/2)(wh)(V/2)=\tfrac14\rho V^2wh$. The true momentum flux is 4/3 times the uniform-flow estimate, because squaring weights the faster fluid more heavily.

## 3. Conservation of momentum for a control volume

### The statement

For a fixed control volume (24 Mar, ll. 409–502; Chapter 12, eq. 12.19):

$$
\left\{\begin{matrix}\text{sum of forces on}\\\text{the fluid in the CV}\end{matrix}\right\}=\left\{\begin{matrix}\text{rate of change of}\\\text{momentum in the CV}\end{matrix}\right\}+\left\{\begin{matrix}\text{net outflow of momentum}\\\text{through the CS}\end{matrix}\right\}
$$

as a vector statement, so one equation per direction.

![[tf_control_volume_balances.png|900]]

### Forces on the fluid

Two kinds of force act on the fluid in the control volume, and both must be counted.

- **Forces from inside the CV**: a fan pushing the fluid along, the reaction of a body to its drag, the weight of the fluid. The drag $D$ on an aerofoil inside the CV acts downstream on the aerofoil, so the aerofoil pushes the fluid upstream with $D$; it is this force on the fluid that enters the equation (24 Mar, ll. 419–428).
- **Forces through the control surface**: pressure acting normally and viscous shear acting tangentially on the fluid at the boundary. Where the boundary cuts a pipe wall or a support, the force transmitted through it also counts.

Where the whole surface is surrounded by atmosphere, a uniform atmospheric pressure all round gives no net force, so pressures can be taken as gauge pressures.

### Accumulation and net outflow

The momentum inside the CV is the sum of the momenta of its volume elements,

$$
\vec M_{CV}=\int_{CV}\rho\vec V\,d\mathcal V
$$

In steady flow the density and velocity at each point do not change, so $\vec M_{CV}$ is constant and the accumulation term is zero. (These volume integrals are the basis of CFD codes, though they are not needed for hand calculation.)

The net outflow is the momentum flow summed over the whole control surface:

$$
\int_{CS}\rho\vec V(\vec V\cdot\vec n)\,dA
$$

The factor $\vec V\cdot\vec n$ decides inflow or outflow: positive where fluid leaves, negative where it enters, since $\vec n$ points outwards. The factor $\rho\vec V$ carries the sign of the momentum itself. So a contribution can be negative even at an outflow (fluid leaving with negative momentum), and positive at an inflow (fluid entering with negative momentum: two minus signs).

### Mathematical form

$$
\boxed{\sum\vec F=\frac{d}{dt}\int_{CV}\rho\vec V\,d\mathcal V+\int_{CS}\rho\vec V(\vec V\cdot\vec n)\,dA}
$$

which for steady flow is

$$
\sum\vec F=\int_{CS}\rho\vec V(\vec V\cdot\vec n)\,dA
$$

This is Newton's second law in Eulerian form: forces applied to a fluid change its momentum.

### One inlet, one outlet, uniform flow

For a two-port control volume with uniform properties over each port, the surface integral reduces to the momentum flows at the two ports, with the inflow negative and the outflow positive, and continuity makes $\dot m$ the same at both:

$$
\boxed{\sum\vec F=\dot{\vec M}_{out}-\dot{\vec M}_{in}=\dot m\left(\vec V_{out}-\vec V_{in}\right)}
$$

(24 Mar, ll. 540–565). Resolve it along each axis, keeping the sign of each velocity component. This is what makes the control-volume method powerful: the force a jet engine, vane or wing exerts follows from the flow at its inlet and outlet alone (24 Mar, ll. 566–573).

---

## Worked examples

### Worked example - jet deflected by a vane

A water jet of diameter 3 cm at 30 m/s is turned downwards through 60° by a fixed vane, leaving at the same speed. Find the force needed to hold the vane (Chapter 12, Example 12.2; 24 Mar, ll. 575–651).

![[tf_vane_deflection.png|900]]

Draw a control volume round the vane, with $x$ along the incoming jet and $y$ upwards. The direction of the holding force is not known, so draw its components $F_x$, $F_y$ positive; the force the vane exerts on the fluid equals the force applied to the vane, since the vane is held still. The jet is at atmospheric pressure everywhere, so pressure exerts no net force. The mass flow is

$$
\dot m=\rho AV=1000\times\frac{\pi}{4}\times0.03^2\times30=21.21\ \mathrm{kg/s}
$$

Inlet, flow along $+x$: an inflow, so $\dot M_x=-\dot mV$, and $\dot M_y=0$. Outlet, at $\theta=60°$ below the horizontal: $V_x=V\cos\theta$, $V_y=-V\sin\theta$, both outflows, so $\dot M_x=+\dot mV\cos\theta$ and $\dot M_y=-\dot mV\sin\theta$.

$x$-momentum:

$$
F_x=\dot mV\cos\theta-\dot mV=-\dot mV(1-\cos\theta)=-21.21\times30\times0.5=-318\ \mathrm N
$$

$y$-momentum:

$$
F_y=-\dot mV\sin\theta-0=-21.21\times30\times0.866=-551\ \mathrm N
$$

Both are negative: the vane must be pushed back against the jet and downwards. That makes sense. To give the water downward momentum the vane must push it down, and the water arrives with more $x$-momentum than it leaves with, so the vane must hold it back.

> [!check] Magnitude and direction
> $|F|=\sqrt{318^2+551^2}=636$ N, pointing 120° below the $+x$ axis, i.e. along the bisector of the reversed inlet and the outlet directions. For a lossless turn at constant speed, $|F|=2\dot mV\sin(\theta/2)=2\times21.21\times30\times0.5=636$ N.

### Worked example - model rocket on a test stand

A model rocket is fired horizontally on a stand. The exhaust has diameter 1 cm, speed 450 m/s and density 0.5 kg/m³, at atmospheric pressure. Find the force on the support (Problem Sheet 9, Q9.2).

The control volume surrounds the rocket; only the exhaust crosses it. The exhaust is at atmospheric pressure, so there is no pressure force. The mass flow is

$$
\dot m=0.5\times\frac{\pi}{4}\times0.01^2\times450=0.01767\ \mathrm{kg/s}
$$

and the only momentum flow is the exhaust outflow, $\dot mV$ rearwards. The support must supply the force that accelerates the gas, so the gas (and rocket) pushes the support forward with

$$
T=\dot mV=0.01767\times450=7.95\ \mathrm N
$$

### Worked example - jet through a plate with an orifice

A 10 cm water jet at 90 m/s strikes a plate on its axis. A 3.5 cm orifice in the plate lets a 3.5 cm jet through at 90 m/s; the rest spreads radially along the plate. Find the force to hold the plate (Problem Sheet 9, Q9.3).

Axial momentum in: $\dot m_DV$ with $\dot m_D=\rho V\pi D^2/4$. Axial momentum out: the jet through the orifice carries $\dot m_dV$; the radial sheet carries no axial momentum, and by symmetry no net radial momentum. Gauge pressure is zero everywhere on the free jets. So the force on the fluid is

$$
F=\dot m_dV-\dot m_DV=-\rho V^2\frac{\pi}{4}(D^2-d^2)
$$

$$
|F|=1000\times90^2\times\frac{\pi}{4}\times(0.10^2-0.035^2)=55.8\ \mathrm{kN}
$$

held against the jet.

### Worked example - thrust reverser

A jet engine with 68 kg/s of air takes air in at 90 m/s and exhausts at 425 m/s. A clamshell reverser turns the exhaust to leave at 20° to the vertical, at the same speed, half forwards above and half below. Find the thrust normally and with the reverser deployed, with the engine stationary (Problem Sheet 9, Q9.4).

Take $x$ in the direction of the exhaust. The force on the fluid is $\dot m(V_{x,out}-V_{x,in})$, and the thrust on the engine is equal and opposite. Normally:

$$
T=\dot m(V_o-V_i)=68\times(425-90)=22.8\ \mathrm{kN}
$$

forwards. With the reverser, each half leaves at 20° to the vertical with a forward $x$-component $V_{x,out}=-V_o\sin20°$, and the vertical components cancel by symmetry:

$$
\dot m(V_{x,out}-V_i)=68\times(-425\times0.342-90)=-16.0\ \mathrm{kN}
$$

The force on the fluid is now forwards, so the engine is pushed backwards: 16.0 kN of braking.

### Worked example - pipe bend and nozzle

Water flows horizontally along a 10 cm pipe in $+x$, turns through 90° to flow in $-y$, and leaves through a 3 cm nozzle as a free jet at 12 m/s. Find the gauge pressure at the flange and the force the flange bolts must carry (Problem Sheet 9, Q9.5, the tutorial problem).

![[tf_pipe_bend_cv.png|900]]

Continuity gives the inlet speed:

$$
V_1=V_2\left(\frac{D_2}{D_1}\right)^2=12\times0.09=1.08\ \mathrm{m/s}
$$

Bernoulli from the flange to the jet at $p_{atm}$ (horizontal, so no $\rho gz$ change in the plane of the bend) gives the inlet gauge pressure:

$$
p_{1g}=\tfrac12\rho(V_2^2-V_1^2)=\tfrac12\times1000\times(144-1.17)=71.4\ \mathrm{kPa}
$$

The mass flow is $\dot m=\rho A_2V_2=8.48$ kg/s. Draw the control volume round the water in the bend, cutting at the flange and the nozzle exit. Forces on the fluid: the bend's force $(F_x,F_y)$, transmitted through the bolts, and the inlet pressure force $p_{1g}A_1$ in $+x$ (the exit is at atmospheric pressure).

$x$: inflow at $V_1$ in $+x$, outflow with no $x$-velocity:

$$
F_x+p_{1g}A_1=0-\dot mV_1
$$

$$
F_x=-8.48\times1.08-71\,400\times\frac{\pi}{4}\times0.1^2=-9.2-560.9=-570\ \mathrm N
$$

$y$: no $y$-momentum in, outflow at $-V_2$:

$$
F_y=\dot m(-V_2)=-8.48\times12=-101.8\ \mathrm N
$$

The bolts must push the bend 570 N to the left (against the flow) and 101.8 N downwards. Almost all of the $x$-force comes from the pressure in the pipe, not from the momentum change.

### Worked example - wake survey on a wing

A wing of chord 0.8 m spans a wind tunnel of height 3 m at 12 m/s (standard air). Downstream, a Pitot traverse finds a 14 cm-deep wake in which the velocity is one third of the free stream. Find the velocity outside the wake, the pressure drop, the drag per unit span and the drag coefficient (Problem Sheet 9, Q9.1).

![[tf_wake_survey.png|900]]

Per unit width, continuity between an upstream plane (1) and a downstream plane (2) gives

$$
VH=\frac{V}{3}d+V_o(H-d)
$$

$$
V_o=V\frac{H-d/3}{H-d}=12\times\frac{2.9533}{2.86}=12.39\ \mathrm{m/s}
$$

Outside the wake the flow is inviscid, so Bernoulli along a streamline there gives the pressure drop between the planes:

$$
p_1-p_2=\tfrac12\rho(V_o^2-V^2)=\tfrac12\times1.225\times(12.39^2-12^2)=5.85\ \mathrm{Pa}
$$

Momentum in $x$ per unit width: the forces on the fluid are the pressure forces $p_1H$ and $-p_2H$ and the wing's reaction $-D'$ (the drag on the wing acts downstream, so the wing pushes the fluid upstream). The net outflow of $x$-momentum is the downstream flux minus the upstream flux:

$$
(p_1-p_2)H-D'=\rho\left[\left(\tfrac V3\right)^2d+V_o^2(H-d)\right]-\rho V^2H
$$

The momentum fluxes per unit width are $\rho(V/3)^2d=1.225\times4^2\times0.14=2.74$ N/m, $\rho V_o^2(H-d)=1.225\times12.39^2\times2.86=537.97$ N/m and $\rho V^2H=1.225\times12^2\times3=529.20$ N/m, so the net outflow is $2.74+537.97-529.20=11.51$ N/m and

$$
D'=(p_1-p_2)H-11.51=5.85\times3-11.51=6.04\ \mathrm{N/m}
$$

$$
C_D=\frac{D'}{\tfrac12\rho V^2c}=\frac{6.04}{\tfrac12\times1.225\times144\times0.8}=0.0856
$$

> [!tip] Where the drag shows up
> The momentum lost from the slow wake (the fluid that passed close to the wing) is more than made up by the faster fluid outside it, so without the pressure term the balance would give a negative drag. The tunnel walls force the outer flow to speed up and the pressure to fall; both effects must be in the balance. In free air, with no walls, the drag is the momentum deficit of the wake.

### Worked example - water jet pack

A jet pack is fed from below through a duct of area $A_0=0.02$ m² and issues water through two downward nozzles of area $A_j=A_0/\beta$. Find the feed velocity needed to support a mass $m$, then the mass flow for 90 kg and $\beta=64$ (Chapter 12, Example 12.3). Neglect the device's own mass; the jets are at atmospheric pressure.

Take $y$ upwards and a control volume round the device. Forces on the fluid in $y$: the person's weight $-mg$, transmitted through the internal channels, and the gauge pressure force at the feed, $+p_gA_0$. Momentum flows in $y$: each jet leaves downwards, $-\rho V_j^2A_j$ each; the feed enters moving upwards, an inflow of positive $y$-momentum, $-\rho V_0^2A_0$. So

$$
-mg+p_gA_0=-2\rho V_j^2A_j-\rho V_0^2A_0
$$

Continuity, $A_0V_0=2A_jV_j$, gives $V_j=\beta V_0/2$. Bernoulli from the feed to a jet gives

$$
(p_g+p_{atm})+\tfrac12\rho V_0^2=p_{atm}+\tfrac12\rho V_j^2
$$

$$
p_g=\tfrac12\rho V_0^2\left(\frac{\beta^2}{4}-1\right)
$$

Substitute, using $2\rho V_j^2A_j=2\rho(\beta V_0/2)^2A_0/\beta=\tfrac12\rho V_0^2A_0\beta$:

$$
mg=\rho V_0^2A_0\left[\frac{\beta^2}{8}-\frac12+\frac\beta2+1\right]=\frac{\rho V_0^2A_0}{8}\left(\beta^2+4\beta+4\right)
$$

$$
V_0=\sqrt{\frac{8mg}{\rho A_0(\beta^2+4\beta+4)}}=\sqrt{\frac{8mg}{\rho A_0}}\,\frac{1}{\beta+2}
$$

For $m=90$ kg and $\beta=64$:

$$
V_0=\sqrt{\frac{8\times90\times9.81}{1000\times0.02}}\times\frac{1}{66}=0.285\ \mathrm{m/s},\qquad \dot m=\rho V_0A_0=5.69\ \mathrm{kg/s}
$$

> [!check] Where the lift comes from
> With these numbers $p_g=41.5$ kPa, so the feed pressure pushes up with $p_gA_0=829$ N, while the two jets carry only 51.9 N of downward momentum flux and the feed 1.6 N. The weight, 883 N, is balanced mainly by the pressure in the feed hose; the momentum terms close the last 53.5 N.

### Worked example - disc held up by a water jet

Water is supplied through a 5 cm tube at 0.2 m/s and leaves upwards through a 1 cm nozzle. The jet supports a disc about 1 m above the nozzle, where it spreads out horizontally. Find the mass flow, the nozzle velocity, the jet speed just below the disc, the mass of the disc, and the height at which a 150 g disc would float (mock exam, 13 May, ll. 200–298).

$$
\dot m=\rho V_0\frac{\pi d_0^2}{4}=1000\times0.2\times\frac\pi4\times0.05^2=0.393\ \mathrm{kg/s},\qquad V_1=V_0\left(\frac{5}{1}\right)^2=5\ \mathrm{m/s}
$$

The jet is at atmospheric pressure all the way, so Bernoulli between the nozzle and height $H$ trades kinetic for potential energy:

$$
\tfrac12V_1^2=\tfrac12V_2^2+gH
$$

$$
V_2=\sqrt{V_1^2-2gH}=\sqrt{25-19.62}=2.32\ \mathrm{m/s}
$$

Take a control volume round the disc and the end of the jet, $y$ upwards. The only force is the disc's weight (pressure is atmospheric everywhere). The water arrives moving up at $V_2$ and leaves horizontally, with no $y$-momentum, so

$$
0-\dot mV_2=-Mg
$$

$$
M=\frac{\dot mV_2}{g}=\frac{0.393\times2.32}{9.81}=0.0928\ \mathrm{kg}
$$

For a 150 g disc the jet must arrive faster, $V_2=Mg/\dot m=3.75$ m/s, so it is caught lower:

$$
H=\frac{V_1^2-(Mg/\dot m)^2}{2g}=\frac{25-14.04}{19.62}=0.559\ \mathrm m
$$

The mass flow is the same at every height, so as the jet slows it widens slightly (13 May, ll. 527–545).

---

## Links

- Parent: [[SESA1016 Thermofluids Hub]] · Previous: [[SESA1016 T11 - Conservation of Mass]] · Next: [[SESA1016 T13 - Conservation of Energy and Propulsion]]
- Concepts: [[Momentum Flux]] · [[Control-volume Analysis Workflow]] · [[Mass Flow Rate]]
- Worked sheet: [[SESA1016 Problem Sheet 09 - Momentum and Energy Conservation Solutions]] (Q9.1–Q9.6) · Formula list: [[SESA1016 Formula Sheet]]
- Used again in: [[SESA1016 T13 - Conservation of Energy and Propulsion|T13]] (thrust of a jet engine) · [[SESA1016 T14 - Boundary Layers and the Origin of Drag|T14]] (drag from the momentum deficit) · [[SESA2023 W01 - Thrust, Efficiency, Range and the ISA]] · [[SESA2024 07 - Spacecraft Propulsion]]

## Sources

- `Chapter 12.pdf`: lecture notes Chapter 12, Conservation of momentum, §§12.1–12.6, Examples 12.1–12.3, Figs 12.1–12.5.
- `SESA1016 Lecture 2025-03-24.txt` (24 Mar 2025, recorded without a microphone): momentum of a particle and of a fluid particle (ll. 32–146), momentum flow for uniform and inclined flow (ll. 147–296), general case (ll. 297–398), conservation of momentum for a control volume (ll. 399–533), two-port form (ll. 534–573), vane example (ll. 574–651).
- `SESA1016 Lecture 2025-05-13.txt` (13 May 2025): mock-exam solutions, question 2 (ll. 200–298), the disc on a water jet.
- `Problem Sheet 09 - Momentum and Energy Conservation.pdf`: Q9.1–Q9.6, printed answers.

## Self-study tasks

### Core

- [ ] Put numbers into the vane example (left unevaluated at 24 Mar, ll. 578–580, 627–630). Targets −318 N and −551 N. → [[#Worked example - jet deflected by a vane]]
- [ ] Q9.1, wake-survey drag of a wing in a tunnel. Targets 12.39 m/s, 5.85 Pa, 6.04 N/m, 0.0856. → [[#Worked example - wake survey on a wing]]
- [ ] Q9.2, model-rocket thrust. Target 7.95 N. → [[#Worked example - model rocket on a test stand]]
- [ ] Q9.3, jet through a plate with an orifice. Target 55.8 kN. → [[#Worked example - jet through a plate with an orifice]]
- [ ] Q9.4, clamshell thrust reverser. Targets 22.8 kN and 16 kN. → [[#Worked example - thrust reverser]]
- [ ] Q9.5, pipe bend and nozzle (tutorial problem). Targets 570 N left, 101.8 N down. → [[#Worked example - pipe bend and nozzle]]
- [ ] Q9.6, jet impinging on a cone. → [[SESA1016 Problem Sheet 09 - Momentum and Energy Conservation Solutions]]

- [ ] Mock exam question 2: disc held up by a water jet (13 May, ll. 200–298). Targets 0.393 kg/s, 5 m/s, 2.32 m/s, 92.8 g, 0.559 m. → [[#Worked example - disc held up by a water jet]]

### Further practice

- [ ] Derive $\dot{\vec M}=\int_A\rho\vec V(\vec V\cdot\vec n)\,dA$ and reduce it to $\dot m\vec V$ for uniform flow (24 Mar, ll. 297–396). → [[#General case]]
- [ ] Show that the momentum flux of the linear channel profile is 4/3 of $\dot m\bar V$ (Chapter 12, Example 12.1). → [[#Special cases]]
- [ ] Rework the jet-pack example and check which force carries most of the weight (Chapter 12, Example 12.3). → [[#Worked example - water jet pack]]

## Transcript and slide slips

> [!warning] Lecture-notes slips (Chapter 12, §§12.1–12.2)
> Where: [[#1. Momentum of a fluid]] · [[#Uniform flow along the axis]].
>
> In §12.1 the sentence "Dividing the momentum of the fluid particle by its mass, we get $\vec V$…" is printed twice; the second should divide by the volume and give $\rho\vec V$, the momentum per unit volume, as the lecture states (24 Mar, ll. 103–105). In §12.2, "Assume that the density is also In both cases" is truncated; the intended assumption is that the density is uniform too.

> [!warning] Lecture-notes slip (Chapter 12, text after eq. 12.24)
> Where: [[#One inlet, one outlet, uniform flow]].
>
> "where $\dot m$ is the mass flow rate through the duct and $\dot m$ is the change in total enthalpy of the fluid across the control volume": the second clause is carried over from the energy chapter and does not belong here.

> [!warning] Lecture-notes rounding (Chapter 12, eq. 12.29)
> Where: [[#Worked example - jet deflected by a vane]].
>
> $F_x$ is printed as −318.5 N; with $\dot m=21.21$ kg/s, $-\dot mV(1-\cos60°)=-318.1$ N.

> [!warning] Transcript slip (13 May, l. 275)
> Where: [[#Worked example - disc held up by a water jet]].
>
> The disc mass is given as "92.8 grams, or 0.01928 kilograms". 92.8 g is 0.0928 kg, which is what $\dot mV_2/g$ gives.
