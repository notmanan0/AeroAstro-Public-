---
title: "SESA1016 T10 - Euler and Bernoulli Equations"
module: "SESA1016 Thermofluids"
type: topic
stream: "Part C: Fluid Motion and Inviscid Flow"
order: 10
tags: [sesa1016, euler-equation, bernoulli, pitot, pressure-coefficient]
aliases: ["Bernoulli Equation", "Euler Equation"]
date: 2026-09-25
status: lectured
coverage: "Lecture 21 (recorded 19 Mar 2025, ll. 1–482: Bernoulli equation and its energy meaning, heads, aerodynamic simplification, pressure taps, stagnation tube, Pitot-static tube, pressure coefficient); Chapter 10 §§10.1–10.2 (particle acceleration and the Euler equation) from the lecture notes, as that lecture was not recorded"
parent: ["[[SESA1016 Thermofluids Hub]]"]
prerequisites: ["[[SESA1016 T9 - Describing Flow and the Material Derivative]]"]
next_topics: ["[[SESA1016 T11 - Conservation of Mass]]"]
key_concepts: ["[[Bernoulli Equation]]", "[[Stagnation Pressure and Pitot Tube]]", "[[Pressure Coefficient]]"]
tutorial_sheets: ["[[SESA1016 Problem Sheet 07 - Describing Flow and Euler Equation Solutions]]", "[[SESA1016 Problem Sheet 08 - Bernoulli and Mass Conservation Solutions]]"]
sources: ["02 - Sources/Lectures/Chapter 10.pdf", "02 - Sources/Lectures/SESA1016 Lecture 21.txt", "02 - Sources/Tutorial Sheets/Problem Sheet 07 - Describing Flow and the Euler Equation.pdf", "02 - Sources/Tutorial Sheets/Problem Sheet 08 - The Bernoulli Equation and Mass Conservation.pdf"]
---

# SESA1016 T10 - Euler and Bernoulli Equations

> [!abstract] Summary
> A fluid particle accelerates along its path when the flow is unsteady (local acceleration) or when it moves into faster or slower fluid (convective acceleration), and across its path when the path curves (centripetal acceleration). Newton's second law for an inviscid particle gives the Euler equation $\rho a_l=-\partial p/\partial l$: particles accelerate towards lower pressure. Integrating it along a streamline for steady, incompressible, inviscid flow gives the Bernoulli equation, $p+\tfrac12\rho V^2+\rho gz=$ const, a statement of mechanical energy conservation. It underlies the stagnation tube, the Pitot-static tube ($V=\sqrt{2\Delta p/\rho}$) and the pressure coefficient, which can never exceed 1.

> [!summary]- Exam use: quick path
> - **Use it when:** pressure and velocity at two points on a streamline are linked (tanks draining, contractions, Pitot readings, flow round bodies), or a pressure gradient must be deduced from an acceleration (nozzle, vortex).
> - **Assumptions:** for Bernoulli, steady, incompressible ($Ma<0.3$), inviscid, along one streamline; for Euler, inviscid only. Drop $\rho gz$ for gas flows, keep it for liquids.
> - **Method:** 1. Pick points 1 and 2 on one streamline where most quantities are known (free surfaces at $p_{atm}$, stagnation points with $V=0$, large reservoirs with $V\approx0$). 2. Write $p_1+\tfrac12\rho V_1^2+\rho gz_1=p_2+\tfrac12\rho V_2^2+\rho gz_2$. 3. Use hydrostatics for any manometer or piezometer reading. 4. Use continuity ([[SESA1016 T11 - Conservation of Mass|T11]]) if a second velocity is unknown. 5. Solve, then check $C_p\le1$.
> - **Common mistakes:** applying Bernoulli across a pump, a turbine or a region of separated, lossy flow; mixing up the fluid density (in $\tfrac12\rho V^2$) with the manometer liquid density (in $\rho_mgh$).
> - **Practise:** [[#Worked example - Pitot-static flow meter]] · [[SESA1016 Problem Sheet 08 - Bernoulli and Mass Conservation Solutions]] Q8.1–Q8.3, Q8.7

The kinematics of a moving fluid ([[SESA1016 T9 - Describing Flow and the Material Derivative|T9]]) say nothing about its cause, which is force. A fluid particle that speeds up, slows down or changes direction must have a net force on it, and if viscosity is negligible the only forces are pressure (and gravity). So wherever particles accelerate, the pressure must vary in space, higher behind them and lower ahead. That is the Euler equation: particles are pushed from high pressure towards low pressure.

Adding up the pushes on one particle along a streamline gives a conserved quantity. The particle's kinetic energy, its potential energy and the work done on it by pressure are traded between each other but their total stays fixed. That is the Bernoulli equation. Where the flow is fast the pressure is low; where it is brought to rest against a body the pressure is highest, at the stagnation pressure. A wing generates lift because the flow over its upper surface is faster than under it.

Turned around, the same equation lets velocity be measured with pressure gauges. A tube facing into the flow feels the stagnation pressure; a hole in the side of a body feels the static pressure; the difference is the dynamic pressure $\tfrac12\rho V^2$, from which $V$ follows. Every aircraft carries Pitot tubes for this purpose.

---

## 1. Acceleration of a fluid particle

### Three kinds of acceleration

The acceleration of a particle is defined as in mechanics,

$$
\vec a=\frac{d\vec V}{dt}
$$

and it changes the velocity's magnitude, its direction, or both. Three flows show the possibilities:

- steady flow along the axis of a contracting duct: the speed increases as the duct narrows, so particles accelerate along their path, even though the velocity at each fixed point never changes;
- a pipe of constant section discharging from a high-pressure reservoir just after a valve is opened: all the fluid in the pipe speeds up together, like the cars of a train starting (not like cars at a traffic light), so the acceleration comes entirely from the flow being unsteady; once the discharge settles, it stops;
- a vortex: particles circle at constant speed, but their direction changes continuously, so there is a centripetal acceleration towards the centre.

### Acceleration along and across the path

Let $s$ measure distance along the particle's path, $\vec u_t$ be the unit vector tangent to the path and $\vec u_n$ the unit normal pointing towards the centre of curvature. The velocity is along the path, with a magnitude that depends on position and, in unsteady flow, on time:

$$
\vec V=V(s,t)\,\vec u_t
$$

Differentiate with the product rule, since both the magnitude and the direction change:

$$
\vec a=\frac{dV}{dt}\vec u_t+V\frac{d\vec u_t}{dt}
$$

For the first term, $V$ depends on $s$ and $t$, and $s$ itself changes with time as the particle moves, $ds/dt=V$. The chain rule gives

$$
\frac{dV}{dt}=\frac{\partial V}{\partial s}\frac{ds}{dt}+\frac{\partial V}{\partial t}=V\frac{\partial V}{\partial s}+\frac{\partial V}{\partial t}
$$

This is the material derivative of [[SESA1016 T9 - Describing Flow and the Material Derivative#Following a particle - the material derivative|T9]] applied to the speed. For the second term, a unit vector moving along a curve of local radius $r$ at speed $V$ turns at rate $V/r$, so, as in circular motion,

$$
\frac{d\vec u_t}{dt}=\frac{V}{r}\vec u_n
$$

Putting the two together:

$$
\boxed{\vec a=\left(V\frac{\partial V}{\partial s}+\frac{\partial V}{\partial t}\right)\vec u_t+\frac{V^2}{r}\vec u_n}
$$

The three terms match the three examples. $V\,\partial V/\partial s$ is the **convective acceleration**, present whenever the speed varies along the path, even in steady flow; it points along the motion if the flow speeds up and against it if the flow slows down. $\partial V/\partial t$ is the **local acceleration**, non-zero only in unsteady flow. Their sum is the acceleration along the path (called the Lagrangian acceleration in the notes). $V^2/r$ is the **centripetal acceleration**, present whenever the path curves (for a straight path, $r=\infty$ and it vanishes).

## 2. The Euler equation

### Statement of the Euler equation

Apply Newton's second law to a particle, assuming the flow is **inviscid**, so viscous forces are negligible and, for now, ignoring gravity as is usual for aerodynamic flows. Then only pressure acts, and along any direction $l$ (not necessarily the flow direction)

$$
\boxed{\rho a_l=-\frac{\partial p}{\partial l}}
$$

where $a_l$ is the component of acceleration along $l$ and $\partial p/\partial l$ the pressure gradient in that direction. No assumption about steadiness or compressibility is needed.

### Derivation of the Euler equation

Take a small cylindrical particle with its axis along $l$, end area $dA$ and length $dl$, so its mass is

$$
m=\rho\,dA\,dl
$$

The pressure on the rear face is $p$, on the front face $p+dp$, and pressures on the curved side have no component along $l$. The net pressure force along $l$ is

$$
F_l=p\,dA-(p+dp)\,dA=-dp\,dA
$$

Newton's second law along $l$, $F_l=ma_l$:

$$
-dp\,dA=\rho\,dA\,dl\,a_l
$$

Divide by $dA$ and by $dl$:

$$
-\frac{dp}{dl}=\rho a_l
$$

which is the Euler equation, with the partial derivative indicating that $p$ is a field differentiated along one direction.

### Reading pressure from acceleration

The minus sign says particles accelerate towards lower pressure. If the pressure is uniform the fluid does not accelerate: it is at rest or moving at constant velocity. So the Euler equation lets the pressure field be sketched from the motion.

Along the dividing streamline approaching the front of a sphere, particles slow down, $a_x<0$, so $\partial p/\partial x>0$: the pressure rises towards the body and peaks at the stagnation point, where the particle's front face is pushed harder than its back. In a vortex, particles circling at speed $v_\theta$ accelerate centripetally towards the core, so with $l$ taken radially outwards, $a_r=-v_\theta^2/r$ and

$$
\frac{\partial p}{\partial r}=\rho\frac{v_\theta^2}{r}>0
$$

The pressure increases away from the core. Each particle is pushed slightly harder on its outer side than its inner side, and that net inward force keeps it on its circular path. Vortex cores are regions of low pressure, which is why moist air condenses in wing-tip vortices ([[#Worked example - pressure in a tip-vortex core]]).

## 3. The Bernoulli equation

### Statement of the Bernoulli equation

The Euler equation is local. To link pressure and velocity at different places, integrate it along a streamline (Lecture 21, ll. 20–27). Assume the flow is

- steady, $\partial/\partial t=0$, so the streamline is also the particle's pathline;
- incompressible, $\rho$ constant along the motion;
- inviscid, so only pressure and gravity act.

Then along the motion,

$$
\boxed{p+\tfrac12\rho V^2+\rho gz=\text{const}}
$$

The particle's speed, pressure and height can all vary in complicated ways, but this sum, the **Bernoulli constant** or Bernoulli integral, stays fixed along its streamline (L21, ll. 56–65). The terms are named:

- $\tfrac12\rho V^2$, the **dynamic pressure**, often written $q$;
- $p$, the **static pressure**, the thermodynamic pressure of T1 and T8;
- $\rho gz$, the **piezometric** (hydrostatic) pressure term, a name from hydraulics.

### Derivation of the Bernoulli equation

A cylindrical particle on a streamline with end area $dA$ and length $ds$ has mass

$$
dm=\rho\,dA\,ds
$$

The path is inclined at angle $\alpha$ to the horizontal. Along the path the forces are the net pressure force $-dp\,dA$ (as in the Euler derivation) and the component of the weight $-dm\,g\sin\alpha$. The flow is steady, so the acceleration along the path is purely convective, $V\,dV/ds$. Newton's second law along the streamline:

$$
-dp\,dA-\rho g\,dA\,ds\,\sin\alpha=\rho\,dA\,ds\,V\frac{dV}{ds}
$$

Along the path, $ds\sin\alpha=dz$, the rise in height. Divide by $dA\,ds$:

$$
-\frac{dp}{ds}-\rho g\frac{dz}{ds}=\rho V\frac{dV}{ds}
$$

By the chain rule $V\,dV/ds=d(\tfrac12V^2)/ds$. Move everything to one side:

$$
\rho\frac{d}{ds}\left(\tfrac12V^2\right)+\frac{dp}{ds}+\rho g\frac{dz}{ds}=0
$$

With $\rho$ and $g$ constant they can go inside the derivative:

$$
\frac{d}{ds}\left(\tfrac12\rho V^2+p+\rho gz\right)=0
$$

so the bracket does not change along $s$, which is the Bernoulli equation. Each assumption entered at a definite point: steady (no $\partial V/\partial t$ term in the acceleration), incompressible (taking $\rho$ inside the derivative) and inviscid (no shear forces in the force balance).

### Energy interpretation

All three terms have the dimensions of pressure, but also of energy per unit volume, J/m³ = N/m² (L21, ll. 81–116). A mass $m$ moving at $V$ has kinetic energy $\tfrac12mV^2$; per unit volume that is $\tfrac12\rho V^2$. Likewise $\rho gz$ is gravitational potential energy per unit volume. The static pressure $p$ is best read as the work done on the particle by pressure forces per unit volume. The Bernoulli equation then says that pressure forces do work on the particle, and that work shows up as a change in its kinetic plus potential energy: it is a statement of **conservation of mechanical energy**. A particle that speeds up must lose pressure or height.

### Heads

Dividing by $\rho g$ gives the hydraulic form used in civil engineering, dams and hydroelectric plant (L21, ll. 117–131):

$$
\frac{V^2}{2g}+\frac{p}{\rho g}+z=\text{const}
$$

Each term is now a length: the **velocity head**, **pressure head** and **elevation head**, and their sum, the **total head**, is constant along a streamline. In a pipe, friction makes the total head fall along the flow ([[SESA1016 T15 - Flow in Conduits|T15]]).

### Fluid at rest

With $V=0$ the equation reduces to $p+\rho gz=$ const, which is Stevin's law integrated for a liquid ([[SESA1016 T8 - Hydrostatics#Integrating Stevin's law|T8]]). Hydrostatics is the special case of Bernoulli with no motion.

### When to keep the gravity term

For aerodynamic flows the changes in $\rho gz$ are tiny compared with the changes in $\tfrac12\rho V^2$ and $p$. Air of density 1.2 kg/m³ falling 1 m changes $\rho gz$ by about 12 Pa, while air at 100 m/s brought to rest changes $\tfrac12\rho V^2$ by 6000 Pa (L21, ll. 153–169). For gas flows, then,

$$
p+\tfrac12\rho V^2=\text{const}
$$

For liquids, dense and usually slow, the piezometric term matters and dropping it gives large errors.

![[tf_bernoulli_contraction.png|900]]

## 4. Measuring pressure and velocity

### Pressure taps and static pressure

The **static pressure** is the pressure in the moving fluid measured without disturbing it. A small hole drilled in a surface, connected by a tube to a manometer or a pressure sensor, is a **pressure tap**; it barely disturbs the flow over it and reads the static pressure there. An aerofoil model may have dozens of taps, each piped to a pressure scanner, to measure the pressure distribution and hence the lift (L21, ll. 177–204). In a liquid-filled pipe a vertical tube on the tap (a **piezometer**) rises to a height that measures $p+\rho gz$ at the tap.

### The stagnation tube

A **stagnation tube** (total-pressure probe) is a tube bent through 90°, with its open end facing upstream and the other end closed by a manometer, so no fluid flows through it (L21, ll. 205–258). One streamline, starting at A far upstream, ends on the tube's mouth at B, where the fluid is brought to rest. Apply Bernoulli from A to B, dropping $\rho gz$:

$$
p_A+\tfrac12\rho V_A^2=p_B+\tfrac12\rho V_B^2
$$

With $V_B=0$:

$$
\boxed{p_B=p_A+\tfrac12\rho V_A^2=p_0}
$$

The tube reads the static pressure plus the dynamic pressure: the **stagnation pressure** or total pressure, $p_0$. It is the highest pressure anywhere in the flow, because a particle that has given up all its kinetic energy has nothing left to convert into pressure. It depends only on free-stream conditions, not on the shape of the body.

![[tf_pitot_static.png|900]]

A stagnation tube alone cannot give the velocity, because its reading contains the unknown $p_A$ as well as $V_A$ (L21, ll. 263–270).

### The Pitot-static tube

The **Pitot-static tube** (Pitot tube for short, after Henri Pitot) puts two tubes one inside the other (L21, ll. 271–336). The inner tube is open at the tip and reads the stagnation pressure $p_B=p_A+\tfrac12\rho V_A^2$. The outer tube has a ring of small holes in its side a few diameters behind the tip, where the flow has recovered from the disturbance of the tip and $V_C\approx V_A$, so by Bernoulli $p_C\approx p_A$: they act as pressure taps and read the static pressure. Connecting the two to a differential gauge, or to the two limbs of a U-tube manometer, gives

$$
\Delta p=p_B-p_C=\left(p_A+\tfrac12\rho V_A^2\right)-p_A=\tfrac12\rho V_A^2
$$

stagnation minus static equals dynamic. So

$$
\boxed{V_A=\sqrt{\frac{2\Delta p}{\rho}}}
$$

The density comes from a barometer and a thermometer via $\rho=p/(RT)$; this is how wind-tunnel speeds are measured in air.

This analysis needs incompressible flow. At $Ma=0.5$ density changes of order $Ma^2\approx25$ % make Bernoulli invalid (L21, ll. 337–346). Aircraft Pitot tubes, often heated to prevent icing, use a compressible-flow theory that gives airspeed and Mach number from the same two pressures through a different formula.

## 5. Aerodynamic flows and the pressure coefficient

### Pressure and velocity round an aerofoil

Consider steady, inviscid, incompressible flow past an aerofoil at incidence, with free-stream speed $V_\infty$, pressure $p_\infty$ and density $\rho$ (L21, ll. 364–427). The dividing streamline ends at the stagnation point B on the lower surface near the leading edge, where Bernoulli gives $p_B=p_\infty+\tfrac12\rho V_\infty^2$: high pressure where the flow has been slowed. A neighbouring streamline that curves up round the leading edge must speed up sharply to get round it; at its fastest point B′ Bernoulli,

$$
p_\infty+\tfrac12\rho V_\infty^2=p_{B'}+\tfrac12\rho V_{B'}^2
$$

forces the pressure to be low. Higher pressure below, lower above: that is lift. Pressure and velocity are coupled, neither causing the other; together they satisfy Bernoulli along each streamline and the Euler equation everywhere, with pressure gradients providing the convective and centripetal accelerations.

### The pressure coefficient

Surface pressures are reported in dimensionless form. Subtract a reference, usually the free-stream pressure, so the sign says whether the local pressure is above or below free stream, and divide by the free-stream dynamic pressure, since Bernoulli says pressure differences scale with it:

$$
\boxed{C_p=\frac{p-p_\infty}{\tfrac12\rho V_\infty^2}}
$$

For flow obeying Bernoulli from the free stream, $p-p_\infty=\tfrac12\rho(V_\infty^2-V^2)$, so

$$
C_p=\frac{\tfrac12\rho(V_\infty^2-V^2)}{\tfrac12\rho V_\infty^2}
$$

$$
\boxed{C_p=1-\left(\frac{V}{V_\infty}\right)^2}
$$

This makes the special cases immediate (L21, ll. 443–473):

- undisturbed flow, $V=V_\infty$: $C_p=0$;
- stagnation point, $V=0$: $C_p=1$, its maximum possible value, since no pressure exceeds the stagnation pressure;
- flow slower than free stream: $0<C_p<1$;
- flow faster than free stream: $C_p<0$, and since there is no upper limit to the speed there is no lower limit to $C_p$; values of −10 or −15 are possible.

![[tf_cylinder_cp.png|900]]

---

## Worked examples

### Worked example - convective acceleration in a nozzle

The steady axial velocity in a propulsion nozzle is $V(x)=V_0/(1-0.5x/L)$, with $V_0=100$ m/s and $L=0.5$ m. Find the acceleration of a particle halfway along (Problem Sheet 7, Q7.2, the sheet's worked solution).

The flow is steady, so $\partial V/\partial t=0$, and the axis is straight, so $r=\infty$. Only the convective term is left. Differentiate:

$$
\frac{dV}{dx}=\frac{V_0\cdot0.5/L}{(1-0.5x/L)^2}
$$

$$
a=V\frac{dV}{dx}=\frac{0.5V_0^2/L}{(1-0.5x/L)^3}
$$

At $x/L=0.5$:

$$
a=\frac{0.5\times100^2/0.5}{0.75^3}=2.37\times10^4\ \mathrm{m/s^2}
$$

about 2400 $g$, in a flow that is steady. By the Euler equation the pressure must fall along the nozzle at $\partial p/\partial x=-\rho a$.

### Worked example - pressure in a tip-vortex core

In a tip vortex the tangential velocity inside the core is $V_\theta=4V_{max}(r_0-r)r/r_0^2$ for $0<r<r_0$ and the flow is still outside. With $V_{max}=46$ m/s and standard air, find the core pressure relative to atmospheric (Problem Sheet 7, Q7.3, the tutorial problem).

![[tf_vortex_core_pressure.png|900]]

The radial Euler equation gives $dp/dr=\rho V_\theta^2/r$. Integrate from the centre, where $p=p_{core}$, to $r_0$, where $p=p_{atm}$:

$$
p_{atm}-p_{core}=\int_0^{r_0}\rho\frac{V_\theta^2}{r}\,dr
$$

$$
p_{atm}-p_{core}=\frac{16\rho V_{max}^2}{r_0^4}\int_0^{r_0}(r_0-r)^2r\,dr
$$

Expand and integrate:

$$
\int_0^{r_0}\left(r_0^2r-2r_0r^2+r^3\right)dr=\frac{r_0^4}{2}-\frac{2r_0^4}{3}+\frac{r_0^4}{4}=\frac{r_0^4}{12}
$$

so the core radius cancels:

$$
p_{atm}-p_{core}=\frac{16}{12}\rho V_{max}^2=\frac43\times1.225\times46^2=3456\ \mathrm{Pa}
$$

The core is 3.46 kPa below atmospheric. The air there is correspondingly cooler, and in humid conditions the water vapour condenses and makes the core visible.

### Worked example - stagnation tube in a channel

A thin tube with a 90° bend faces upstream in a uniform flow of water in an open channel, its mouth at depth $d$. The water in the tube rises 9.7 cm above the free surface. Find the speed, and say whether the reading depends on $d$ or on $p_{atm}$ (Chapter 10, Example 10.1).

Bernoulli from a point A upstream to the mouth B, at the same depth:

$$
p_B=p_A+\tfrac12\rho V_A^2
$$

Hydrostatics in the channel gives $p_A=p_{atm}+\rho gd$, and in the tube $p_B=p_{atm}+\rho g(h+d)$. Substitute:

$$
p_{atm}+\rho g(h+d)=p_{atm}+\rho gd+\tfrac12\rho V_A^2
$$

$p_{atm}$ and $\rho gd$ cancel:

$$
\rho gh=\tfrac12\rho V_A^2
$$

$$
V_A=\sqrt{2gh}=\sqrt{2\times9.81\times0.097}=1.38\ \mathrm{m/s}
$$

Neither the depth nor the atmospheric pressure affects $h=V_A^2/(2g)$: the rise is the velocity head.

### Worked example - Pitot-static flow meter

An air flow meter has a static tap at station A and a stagnation probe at station B, where the velocity is 1.5 times that at A. A water manometer between them reads 10 cm. Find the velocity at B, for steady, inviscid, incompressible flow and standard air (Problem Sheet 8, Q8.7, a tutorial problem).

The total pressure is the same everywhere on the streamline, so the probe at B reads $p_{0}=p_A+\tfrac12\rho_aV_A^2$. The manometer reads $p_0-p_A$:

$$
\rho_wgh=\tfrac12\rho_aV_A^2
$$

$$
V_A=\sqrt{\frac{2\rho_wgh}{\rho_a}}=\sqrt{\frac{2\times1000\times9.81\times0.10}{1.225}}=40.0\ \mathrm{m/s}
$$

and $V_B=1.5V_A=60.0$ m/s. The two densities are different fluids: water in the manometer, air in the dynamic pressure.

> [!check] Compressibility
> At 60 m/s, $Ma\approx0.18$ and $Ma^2\approx0.03$: density changes of about 3 %, so the incompressible Bernoulli equation is justified.

### Worked example - draining tank and sluice

Water drains from a large open tank through a small port a height $H$ below the free surface. Find the jet speed for $H=10$ m (Problem Sheet 8, Q8.1). Then find the speed of water falling 0.7 m over a sluice at 0.7 m/s (Chapter 10, Example 10.2).

Bernoulli from the free surface (1) to the jet (2), both at $p_{atm}$, with $V_1\approx0$ because the tank is large:

$$
p_{atm}+\rho gH=p_{atm}+\tfrac12\rho V_2^2
$$

$$
V_2=\sqrt{2gH}=\sqrt{2\times9.81\times10}=14.0\ \mathrm{m/s}
$$

independent of the density. For the sluice, a free-surface streamline is at $p_{atm}$ throughout, so

$$
\tfrac12V_1^2+gz_1=\tfrac12V_2^2+g(z_1-\Delta z)
$$

$$
V_2=\sqrt{V_1^2+2g\Delta z}=\sqrt{0.7^2+2\times9.81\times0.7}=3.77\ \mathrm{m/s}
$$

valid only within the smooth falling sheet; the turbulent froth below dissipates the energy and Bernoulli no longer applies there.

### Worked example - flow round a cylinder

The fastest flow round a circular cylinder, at the top and bottom, is twice the approach speed. In a 40 m/s wind, find the difference between the highest and lowest pressures, and $C_p$ at the fastest point (Problem Sheet 8, Q8.2).

The highest pressure is at the front stagnation point, $p_0=p_\infty+\tfrac12\rho V_0^2$. At the top, $V=2V_0$, so $p_{min}=p_\infty+\tfrac12\rho(V_0^2-4V_0^2)$. Subtract:

$$
p_{max}-p_{min}=\tfrac12\rho(4V_0^2)=2\rho V_0^2=2\times1.2\times40^2=3.84\ \mathrm{kPa}
$$

and $C_p=1-(2V_0/V_0)^2=-3$. With $\rho=1.225$ kg/m³ the difference is 3.92 kPa; the printed answer uses 1.2 kg/m³.

---

## Links

- Parent: [[SESA1016 Thermofluids Hub]] · Previous: [[SESA1016 T9 - Describing Flow and the Material Derivative]] · Next: [[SESA1016 T11 - Conservation of Mass]]
- Concepts: [[Bernoulli Equation]] · [[Stagnation Pressure and Pitot Tube]] · [[Pressure Coefficient]] · [[Pressure and Head]] · [[Material Derivative]]
- Worked sheets: [[SESA1016 Problem Sheet 07 - Describing Flow and Euler Equation Solutions]] (Q7.2–Q7.3) · [[SESA1016 Problem Sheet 08 - Bernoulli and Mass Conservation Solutions]] (Q8.1–Q8.3, Q8.7–Q8.8) · Formula list: [[SESA1016 Formula Sheet]]
- Continues in: [[SESA2022 T3 - Potential Flow]] (cylinder $C_p$, lift from pressure) · [[SESA2023 W03 - Compressible Flow, Normal Shocks and Nozzles]] (compressible Pitot and stagnation quantities)

## Sources

- `Chapter 10.pdf`: lecture notes Chapter 10, The Bernoulli equation, §§10.1–10.6, Derivations 10.1–10.3, Examples 10.1–10.2, Figs 10.1–10.11.
- `SESA1016 Lecture 21.txt` (recorded lecture, 19 Mar 2025, cited as L21): Bernoulli statement and terms (ll. 12–80), energy meaning (ll. 81–116), heads and the fluid at rest (ll. 117–143), dropping $\rho gz$ (ll. 144–176), pressure taps (ll. 177–204), stagnation tube (ll. 205–270), Pitot-static tube (ll. 271–364), aerofoil flow and $C_p$ (ll. 364–473).
- The Euler-equation lecture of the previous week was not recorded; §§1–2 are written from the lecture notes.
- `Problem Sheet 07` (Q7.2–Q7.3) and `Problem Sheet 08` (Q8.1–Q8.3, Q8.7–Q8.8), with printed answers and the worked solutions to Q7.2 and Q8.3.

## Self-study tasks

### Core

- [ ] Q7.2, convective acceleration in a nozzle (worked solution). Target $2.37\times10^4$ m/s². → [[#Worked example - convective acceleration in a nozzle]]
- [ ] Q7.3, pressure in a tip-vortex core (tutorial problem). Target −3456 Pa. → [[#Worked example - pressure in a tip-vortex core]]
- [ ] Q8.1, water draining from a tank. Target 14 m/s. → [[#Worked example - draining tank and sluice]]
- [ ] Q8.2, highest and lowest pressures round a cylinder. Targets 3.84 kPa, $C_p=-3$. → [[#Worked example - flow round a cylinder]]
- [ ] Q8.3, piezometers on a vertical contraction (worked solution). Target 3.46 m/s. → [[#Heads]] · [[SESA1016 Problem Sheet 08 - Bernoulli and Mass Conservation Solutions]]
- [ ] Q8.7, stagnation-probe flow meter (tutorial problem). Target 60.03 m/s. → [[#Worked example - Pitot-static flow meter]]
- [ ] Q8.8, force on a hand out of a car window at 55 and 164 mph. Targets about 7 N and 60 N. → [[#The stagnation tube]] · [[SESA1016 Problem Sheet 08 - Bernoulli and Mass Conservation Solutions]]

### Further practice

- [ ] Work through the Bernoulli derivation in the notes (skipped in the lecture, L21, ll. 48–55). → [[#Derivation of the Bernoulli equation]]
- [ ] Derive the three acceleration components of a particle on a curved path (Chapter 10, Derivation 10.1). → [[#Acceleration along and across the path]]
- [ ] Show that $C_p=1-(V/V_\infty)^2$ and that $C_p\le1$ everywhere. → [[#The pressure coefficient]]

## Transcript and slide slips

> [!warning] Lecture-notes slips (Chapter 10, eq. 10.19 and the line above it)
> Where: [[#Derivation of the Bernoulli equation]].
>
> The net pressure force in eq. 10.19 is printed $-p\,dA$; it should be $-dp\,dA$, the difference between the two faces, as in eq. 10.14 and the next line, eq. 10.20. The weight component along the path is written $dW_t=dm\sin\alpha$, missing $g$; eq. 10.19 itself uses $\rho g\,dA\,ds\sin\alpha$, which is correct.

> [!warning] Lecture-notes slip (Chapter 10, §10.1)
> Where: [[#Three kinds of acceleration]].
>
> The third example is introduced as a particle in a circular vortex, but the discussion of it after eq. 10.9 refers to "the fluid particle travelling around the sphere". It means the vortex; the centripetal-acceleration result is the same.
