---
title: "SESA1016 T15 - Flow in Conduits"
module: "SESA1016 Thermofluids"
type: topic
stream: "Part E: Viscous Losses"
order: 15
tags: [sesa1016, pipe-flow, friction-factor, head-loss, pumps]
aliases: ["Pipe Flow", "Darcy-Weisbach"]
date: 2026-09-25
status: lectured
coverage: "Lecture of 8 May 2025 (ll. 115–597: minor losses and the loss coefficient, combined losses, pumps and the SFEE for a liquid, pump efficiency, type 1 and type 2 pipe problems); mock-exam solutions of 13 May 2025 (ll. 300–373: liquid-hydrogen pipeline); Chapter 15 §§15.1–15.6 (developing flow, Reynolds' experiment, head losses, Poiseuille flow, turbulent profiles, friction factor) from the lecture notes, as the lecture of 6 May 2025 was not recorded"
parent: ["[[SESA1016 Thermofluids Hub]]"]
prerequisites: ["[[SESA1016 T14 - Boundary Layers and the Origin of Drag]]"]
next_topics: []
key_concepts: ["[[Darcy Friction Factor]]", "[[Major and Minor Head Losses]]", "[[Reynolds Number]]"]
tutorial_sheets: ["[[SESA1016 Problem Sheet 11 - Flows in Conduits Solutions]]"]
sources: ["02 - Sources/Lectures/Chapter 15.pdf", "02 - Sources/Lectures/SESA1016 Lecture 2025-05-08.txt", "02 - Sources/Lectures/SESA1016 Lecture 2025-05-13.txt", "02 - Sources/Tutorial Sheets/Problem Sheet 11 - Flows in Conduits.pdf"]
---

# SESA1016 T15 - Flow in Conduits

> [!abstract] Summary
> After an entrance length, flow in a pipe becomes fully developed: the profile stops changing, and a force balance shows that the pressure falls steadily along the pipe to balance the wall shear, $\partial p/\partial x=-2\tau_w/R$. In laminar flow ($Re_D<2000$) the profile is the Poiseuille parabola, with mean velocity half the maximum and Darcy friction factor $f=64/Re_D$; turbulent profiles are fuller and $f$ comes from the Moody chart or Colebrook's equation, depending on $Re_D$ and the relative roughness $\epsilon/D$. The pressure drop of a pipe system is $\sum f\tfrac LD\tfrac12\rho\bar V^2+\sum K\tfrac12\rho\bar V^2$, and an ideal pump must supply power $\dot{\mathcal V}\Delta p$, or $\dot{\mathcal V}\Delta p/\eta_p$ for a real one.

> [!summary]- Exam use: quick path
> - **Use it when:** a pressure drop, head loss, flow rate, wall shear stress or pump power is wanted for liquid or low-speed gas flow through pipes, valves and fittings.
> - **Assumptions:** steady, incompressible, fully developed flow (pipe long compared with the entrance length); round pipe or hydraulic diameter $D_h=4A/P$; $\rho$ and $\mu$ constant.
> - **Method:** 1. $\bar V=\dot{\mathcal V}/A$, then $Re_D=\bar VD/\nu$: laminar below 2000, turbulent above about 3000. 2. $f=64/Re_D$ (laminar), or Moody chart / Colebrook with $\epsilon/D$ (turbulent). 3. $\Delta p=\sum f\tfrac LD\tfrac12\rho\bar V^2+\sum K\tfrac12\rho\bar V^2$, plus $\rho g\Delta z$ for a rise. 4. Pump power $\dot W_p=\dot{\mathcal V}\Delta p/\eta_p$. 5. If $\Delta p$ is given and $\dot{\mathcal V}$ is not (type 2), guess $\bar V$ and iterate.
> - **Common mistakes:** using the Fanning friction factor ($\tau_w/\tfrac12\rho\bar V^2$, 4 times smaller) in the Darcy formula; using the maximum velocity instead of the bulk velocity.
> - **Practise:** [[#Worked example - pump for a water tank]] · [[SESA1016 Problem Sheet 11 - Flows in Conduits Solutions]] Q11.6, Q11.10

A boundary layer on a flat plate keeps growing for as long as the plate goes on. Inside a pipe it cannot: the layers growing from the wall all round meet on the axis within a short distance, and after that the velocity profile has nowhere left to develop. From then on every section of the pipe looks the same. That is what makes pipe flow simpler than external flow, and what makes it possible to tabulate the friction of a pipe once and for all.

Moving fluid through a pipe costs energy. Friction at the wall would slow the flow down unless the pressure behind it is higher than the pressure ahead, so the pressure falls steadily along the pipe, and a pump (or a head of water in a tank) has to supply the difference. How much pressure is lost depends on whether the flow is laminar or turbulent, which Osborne Reynolds showed in the 1880s depends on a single number, and in turbulent flow on how rough the pipe wall is.

Real pipe systems also have bends, valves, junctions and entrances, each of which loses a little more pressure in a short distance; those minor losses are added to the friction losses. The engineering question is then either how much pressure (and so pump power) a given flow rate needs, or how much flow a given pressure or pump will deliver; the second needs iteration, because the friction itself depends on the flow (8 May, ll. 455–590).

---

## 1. Developing and fully developed flow

Consider a long horizontal pipe fed from a large pressurised reservoir and discharging to atmosphere. At the entrance the velocity is nearly uniform across the section. Boundary layers start growing from the wall all round, and inside them the flow slows; in the central **potential core** outside them the flow is inviscid, and it speeds up to keep the flow rate constant. The boundary layers meet on the axis after an **entrance length** $L_e$. Beyond that the velocity profile $v_x(r)$ no longer changes with $x$: the flow is **fully developed**.

The wall shear stress behaves in the same way: large near the entrance, where the boundary layer is thin and the velocity gradient at the wall is steep, falling as the layer thickens, and then constant once the flow is fully developed, since the wall gradient no longer changes:

$$
\frac{\partial\tau_w}{\partial x}=0\qquad(x>L_e)
$$

Typical correlations for the entrance length are

$$
\frac{L_e}{D}\approx\begin{cases}0.06\,Re_D & \text{laminar}\\ 4.4\,Re_D^{1/6} & \text{turbulent}\end{cases}
$$

so for laminar flow at $Re_D=2000$, $L_e\approx120D$, while for turbulent flow at $Re_D=10^5$, $L_e\approx30D$. In most practical pipes the flow is turbulent and becomes fully developed quickly.

![[tf_pipe_profiles.png|900]]

## 2. Reynolds' experiment

Reynolds fed a glass pipe from a tank kept at constant level, controlled the flow rate with a valve at the outlet, and injected a thin stream of dye on the axis at the entrance. The flow is characterised by the **bulk velocity** (the area-averaged velocity of [[SESA1016 T11 - Conservation of Mass#The area-averaged velocity|T11]])

$$
\bar V=\frac{\dot{\mathcal V}}{A}
$$

At low speed the dye streak stays straight: the flow is laminar, every particle moves parallel to the axis, slowest near the wall and fastest on the centreline. Above a critical speed it becomes turbulent: the streak meanders and breaks up as particles move chaotically. The critical bulk velocity is not universal: a thinner pipe or a more viscous fluid (water mixed with glycerine) raises it. Dimensional analysis shows that the controlling parameter is the **pipe Reynolds number**

$$
\boxed{Re_D=\frac{\bar VD}{\nu}}
$$

| Regime | $Re_D$ | Character |
|---|---|---|
| laminar | below 2000 | smooth, ordered, parallel streamlines |
| transitional | 2000–3000 | unstable, intermittently turbulent |
| turbulent | above 3000 | chaotic, with eddies and mixing |

Two differences from the flat plate stand out. Above the critical value the flow is turbulent along the whole pipe, not only downstream of a transition point. And the length scale is the diameter, not the pipe length, because the viscous forces that damp disturbances come from the radial velocity gradient, which the diameter controls.

## 3. Pressure drop and wall shear

### Force balance on a pipe element

Take a fluid element filling a length $\Delta x$ of a round pipe of radius $R=D/2$, in fully developed flow. Apply the momentum equation of [[SESA1016 T12 - Conservation of Momentum|T12]] along the axis. The velocity profiles at the two ends are identical, so the momentum flowing in equals the momentum flowing out, and the net outflow is zero: the forces on the element must balance.

The wall exerts a shear stress against the flow. Writing $r$ from the axis, the velocity increases as $r$ decreases at the wall, so

$$
\tau_w=-\mu\left.\frac{\partial v_x}{\partial r}\right|_{r=R}
$$

with the minus sign making $\tau_w$ positive. Over the wetted wall area $\pi D\,\Delta x$ it gives a force $\tau_w\pi D\Delta x$ opposing the flow. For a horizontal pipe the only other axial force is the pressure difference between the ends, with the pressure uniform over each section. Taking forces in the flow direction as positive, with $A=\pi R^2$:

$$
pA-(p+\Delta p)A-\tau_w\,2\pi R\,\Delta x=0
$$

$$
-\Delta p\,\pi R^2=2\pi R\,\tau_w\Delta x
$$

Divide by $\pi R^2\Delta x$ and let $\Delta x\to0$:

$$
\boxed{\frac{\partial p}{\partial x}=-\frac{2}{R}\tau_w}
$$

The pressure must fall along the pipe to push the fluid against the wall friction; with no pressure difference across a pipe there is no flow through it. In fully developed flow $\tau_w$ is constant, so the pressure falls linearly, and over a length $L$, $\Delta p=2\tau_wL/R=4\tau_wL/D$.

![[tf_pipe_element_forces.png|900]]

A tank of liquid at depth $h$ feeding a horizontal pipe open to the atmosphere shows this directly: the inlet is at $p_{atm}+\rho gh$, the outlet at $p_{atm}$, and the pressure falls linearly between them, driving the flow; the deeper the water, the larger the flow.

### Head loss

In hydraulics the pressure drop is expressed as a height of the liquid,

$$
\Delta h=\frac{\Delta p}{\rho g}
$$

the **head lost** to friction over the length of conduit. It is the fall in total head along a pipe, the quantity that Bernoulli's head form ([[SESA1016 T10 - Euler and Bernoulli Equations#Heads|T10]]) would keep constant in inviscid flow.

![[tf_conduit_head_loss.png|900]]

## 4. Laminar flow: the Poiseuille profile

### Derivation of the velocity profile

Laminar flow in a round pipe (Hagen–Poiseuille flow) is one of the few exact solutions of the Navier–Stokes equations. All the fluid moves parallel to the axis. Take now a cylinder of fluid of radius $r<R$ and length $\Delta x$, coaxial with the pipe. The fluid outside it, moving more slowly, drags on its curved surface with a shear stress

$$
\tau(r)=-\mu\frac{\partial v_x}{\partial r}
$$

which varies with $r$: zero on the axis, where the profile is flat, and largest at the wall. Force balance on the cylinder, pressure on its ends against shear on its curved surface:

$$
p\,\pi r^2-(p+\Delta p)\pi r^2=\tau(r)\,2\pi r\,\Delta x
$$

$$
-\Delta p\,r=2\tau\,\Delta x
$$

Divide by $\Delta x$ and let it tend to zero:

$$
\tau(r)=-\frac{r}{2}\frac{\partial p}{\partial x}
$$

At $r=R$ this is the wall result of §3. Substitute $\tau=-\mu\,\partial v_x/\partial r$:

$$
\frac{\partial v_x}{\partial r}=\frac{\partial p/\partial x}{2\mu}\,r
$$

The pressure gradient is the same at every radius, so integrate in $r$:

$$
v_x(r)=\frac{\partial p/\partial x}{4\mu}r^2+C
$$

No-slip at the wall, $v_x(R)=0$, gives $C=-\dfrac{\partial p/\partial x}{4\mu}R^2$. With $\partial p/\partial x<0$, writing its magnitude:

$$
\boxed{v_x(r)=\frac{|\partial p/\partial x|}{4\mu}\left(R^2-r^2\right)}
$$

a parabola, with its maximum on the axis,

$$
V_{max}=\frac{|\partial p/\partial x|}{4\mu}R^2
$$

so that

$$
\boxed{v_x(r)=V_{max}\left(1-\frac{r^2}{R^2}\right)}
$$

For a given pressure gradient the centreline speed grows with the square of the radius and falls with the viscosity.

### Shear stress profile

Differentiate the profile:

$$
\tau(r)=-\mu\frac{\partial}{\partial r}\left[V_{max}\left(1-\frac{r^2}{R^2}\right)\right]=-\mu V_{max}\left(-\frac{2r}{R^2}\right)=2\mu V_{max}\frac{r}{R^2}
$$

and with $V_{max}$ from above this is $\tau=\tfrac12|\partial p/\partial x|\,r$. The velocity is parabolic and the shear stress linear, zero on the centreline and largest at the wall, $\tau_w=2\mu V_{max}/R$.

### Flow rate and mean velocity

The velocity is constant round a thin ring of radius $r$ and width $dr$, of area $dA=2\pi r\,dr$, so the flow through it is $v_x(r)\,2\pi r\,dr$ and

$$
\dot{\mathcal V}=\int_0^Rv_x(r)\,2\pi r\,dr=2\pi V_{max}\int_0^R\left(r-\frac{r^3}{R^2}\right)dr
$$

$$
\dot{\mathcal V}=2\pi V_{max}\left(\frac{R^2}{2}-\frac{R^2}{4}\right)=\frac{V_{max}}{2}\pi R^2
$$

so the bulk velocity is

$$
\boxed{\bar V=\tfrac12V_{max}}
$$

Substituting $V_{max}$ gives the **Hagen–Poiseuille law**:

$$
\dot{\mathcal V}=\frac{\pi R^4}{8\mu}\left|\frac{\partial p}{\partial x}\right|=\frac{\pi D^4}{128\mu}\frac{\Delta p}{L}
$$

The flow rate goes as the fourth power of the diameter, so halving a pipe's diameter cuts its laminar flow by a factor of 16 at the same pressure drop.

## 5. Turbulent velocity profiles

Turbulent pipe flow is unsteady and chaotic, so only the time-averaged profile is meaningful. Particles move across the pipe as well as along it, carrying fast fluid from the centre towards the wall and slow fluid back. This mixing flattens the profile: the centreline velocity is less than twice the bulk velocity, and the near-wall velocity, and so the wall shear stress, are higher than in laminar flow. No exact theory exists; an empirical **power law** is often used,

$$
\frac{v_x(r)}{V_{max}}=\left(\frac{R-r}{R}\right)^m
$$

with $m$ decreasing slowly as $Re_D$ rises:

| $Re_D$ | $4\times10^3$ | $2.3\times10^4$ | $1.1\times10^5$ | $1.1\times10^6$ | $3.2\times10^6$ |
|---|---|---|---|---|---|
| $m$ | 1/6.0 | 1/6.6 | 1/7.0 | 1/8.8 | 1/10.0 |
| $V_{max}/\bar V$ | 1.26 | 1.24 | 1.22 | 1.18 | 1.16 |

> [!check] The one-seventh-power profile
> With $m=1/7$ and $s=r/R$, $\bar V/V_{max}=2\int_0^1s(1-s)^{1/7}ds=2\times\tfrac{49}{120}=\tfrac{49}{60}$, so $V_{max}/\bar V=60/49=1.224$: the centreline is 22 % above the mean, matching the table at $Re_D=1.1\times10^5$ (Problem Sheet 11, Q11.1).

## 6. The friction factor

### Definition

The pressure loss is made dimensionless with the **Darcy** (Darcy–Weisbach) **friction factor**

$$
\boxed{f=\frac{|\partial p/\partial x|}{\tfrac12\rho\bar V^2}D_h}
$$

where $D_h=4A/P$ is the **hydraulic diameter**, area over perimeter, which for a round pipe is $4(\pi D^2/4)/(\pi D)=D$. Substituting $|\partial p/\partial x|=2\tau_w/R=4\tau_w/D$:

$$
f=\frac{4\tau_w}{\tfrac12\rho\bar V^2}
$$

so $f$ is four times a wall friction coefficient based on the bulk velocity. Some texts use the **Fanning** factor $\tau_w/(\tfrac12\rho\bar V^2)$, four times smaller; the Darcy factor is used throughout. For a pipe of length $L$ with a linear pressure fall, $|\partial p/\partial x|=\Delta p/L$ and

$$
\boxed{\Delta p=f\frac{L}{D}\tfrac12\rho\bar V^2}
$$

Dimensional analysis gives $f=f(Re_D,L/D)$ for a smooth pipe; for a long pipe, where the flow is fully developed, the pressure gradient does not depend on the length, so $f=f(Re_D)$ alone.

### Laminar flow

From §4, $\bar V=\tfrac12V_{max}=|\partial p/\partial x|R^2/(8\mu)$, so

$$
\left|\frac{\partial p}{\partial x}\right|=\frac{8\mu\bar V}{R^2}=\frac{32\mu\bar V}{D^2}
$$

Substitute into the definition of $f$:

$$
f=\frac{32\mu\bar V}{D^2}\cdot\frac{2D}{\rho\bar V^2}=\frac{64\mu}{\rho\bar VD}
$$

$$
\boxed{f=\frac{64}{Re_D}}\qquad\text{(laminar)}
$$

Raising $Re_D$ tenfold cuts $f$ tenfold, but that does not mean faster flow loses less pressure: from the line above, $|\partial p/\partial x|\propto\mu\bar V/D^2$, linear in the velocity, as expected for a viscous loss. The diameter matters more than $f=64/Re_D$ suggests.

### Turbulent flow and roughness

For turbulent flow in a smooth pipe the **Blasius** relation fits the data well:

$$
f=\frac{0.32}{Re_D^{1/4}}
$$

Most real pipes are rough, characterised by an **equivalent sand-grain roughness** $\epsilon$ (also written $k_s$), roughly the mean height of the roughness. The roughness enters through the **relative roughness** $\epsilon/D$, so $f=f(Re_D,\epsilon/D)$. Colebrook's implicit equation (1939), a fit to Nikuradse's measurements, gives it for $Re_D>4000$:

$$
\boxed{\frac{1}{\sqrt f}+2\log_{10}\left(\frac{\epsilon}{3.7D}+\frac{2.51}{\sqrt f\,Re_D}\right)=0}
$$

It cannot be solved for $f$ algebraically, so it is solved with a root finder, for example bisection (`scipy.optimize.bisect`) on the bracket $[10^{-8},1]$, or read from the **Moody chart**, which plots $f$ against $Re_D$ for the laminar line and a family of curves of constant $\epsilon/D$ (8 May; Chapter 15, §15.6).

![[tf_moody_chart.png|900]]

At high $Re_D$ each rough curve flattens: the flow is **fully rough**, $f$ depends only on $\epsilon/D$, and then $|\partial p/\partial x|=f\rho\bar V^2/(2D)\propto\bar V^2$, quadratic in the velocity, against linear in laminar flow. In between, the flow is turbulent but $f$ still depends on $Re_D$. Between 2000 and 3000 $f$ cannot be predicted reliably.

> [!check] Laminar against turbulent at the same Reynolds number
> At $Re_D=10^4$, laminar flow would have $f=64/10^4=0.0064$, while smooth-pipe turbulent flow has $f=0.031$ (Colebrook) or 0.032 (Blasius). Keeping the flow laminar would cut the friction by a factor of about 5, which is why controlling turbulence is an active research area.

## 7. Minor losses

### The loss coefficient

A component such as a partly open valve, a bend, a junction or a pipe entrance causes a local pressure drop on top of the steady fall along the pipe, because the flow through it separates, swirls and dissipates mechanical energy as heat (8 May, ll. 117–148). To characterise a component, force a range of known flow rates through it and measure $\Delta p$ across it. Plotted against $\dot{\mathcal V}$ the points curve; plotted against $\tfrac12\rho\bar V^2$ they fall on a straight line through the origin, because pressure changes in fluids scale with $\rho V^2$. Its slope (from `numpy.polyfit`, say) is the **minor loss coefficient**

$$
\boxed{K=\frac{\Delta p}{\tfrac12\rho\bar V^2}}
$$

with $\bar V$ the bulk velocity through the component (8 May, ll. 149–197). $K$ comes from experiment, tables or manufacturers' data. A partly closed valve has a large $K$, a fully open one a small $K$.

For a pipe entrance, $K$ depends on how rounded the edge is, $r/D$. A sharp edge ($r=0$) gives $K\approx0.5$, because the flow separates at the corner and the streamlines contract; a well-rounded entrance gives $K$ close to zero. For a sudden contraction, $K$ depends on the area ratio $A_2/A_1$, large when it is small and tending to zero as it approaches 1.

### Combined losses

The total pressure drop of a system is the sum over every straight pipe and every component, each with its own $L$, $D$, $\bar V$, $f$ or $K$:

$$
\boxed{\Delta p=\sum_{pipes}f\frac LD\tfrac12\rho\bar V^2+\sum_{components}K\tfrac12\rho\bar V^2}
$$

(8 May, ll. 198–217). A rise in elevation adds $\rho g\Delta z$.

## 8. Pumping power

### The SFEE for a pump

A pump (centrifugal, vane, gear, screw, piston) uses rotating blades, vanes or gears to raise the pressure of the fluid, which the pipe system then loses. To find the power it needs, apply the SFEE of [[SESA1016 T13 - Conservation of Energy and Propulsion|T13]] to a control volume round the pump (8 May, ll. 265–430):

$$
\dot Q-\dot W_x=\int_{CS}\rho\left(e+\frac p\rho\right)(\vec V\cdot\vec n)\,dA,\qquad e=\tfrac12V^2+gz+u
$$

For a liquid it is clearer to keep $u$ and $p/\rho$ apart rather than combine them into $h$, with $u=cT$, where $c$ is the liquid's specific heat (the same at constant pressure or volume). The simplifications are:

- the pump does work on the fluid, so $-\dot W_x=\dot W_p$, the power to drive the pump;
- heat loss from the casing is negligible, $\dot Q=0$;
- $\Delta(gz)$ across a small pump is negligible;
- the inlet and outlet pipes have the same diameter, so by continuity $\Delta(\tfrac12V^2)=0$;
- the flow is uniform at each port and the density the same at both.

So

$$
\dot W_p=\dot m\left[c\left(T_{out}-T_{in}\right)+\frac{p_{out}-p_{in}}{\rho}\right]
$$

and with $\dot m=\rho\dot{\mathcal V}$,

$$
\dot W_p=\dot{\mathcal V}\rho c\,\Delta T+\dot{\mathcal V}\Delta p
$$

The power goes into raising the pressure, which is the useful part, and into warming the liquid, which is waste from friction and turbulence inside the pump. An ideal pump has $\Delta T=0$:

$$
\boxed{\dot W_{p,ideal}=\dot{\mathcal V}\Delta p}
$$

the minimum power to push a volume flow rate $\dot{\mathcal V}$ through a pressure rise $\Delta p$. Manufacturers quote a **pump efficiency** $\eta_p=\dot{\mathcal V}\Delta p/\dot W_p$, the hydraulic power delivered over the power supplied, so

$$
\boxed{\dot W_p=\frac{\dot{\mathcal V}\Delta p}{\eta_p}}
$$

### Two types of problem

#### Type 1 - flow rate given

When the flow rate is given and the pressure drop and power are wanted, the calculation is explicit: compute $\bar V=\dot{\mathcal V}/A$, then $Re_D$ and the regime, then $f$ (formula or chart), then $\Delta p$ from the friction and minor-loss sum, then the ideal power $\dot{\mathcal V}\Delta p$ and, with the efficiency, the real power. This is the typical exam problem (8 May, ll. 572–579).

#### Type 2 - pressure drop given

When the pressure drop (or the pump power) is given and the flow rate is wanted, the unknown appears on both sides of $\Delta p=f(Re_D,\epsilon/D)\tfrac LD\tfrac12\rho\bar V^2$, because $f$ depends on $\bar V$ through $Re_D$; so $\bar V$ cannot be written explicitly. Iterate (8 May, ll. 464–570):

- guess $\bar V$;
- compute $Re_D$ and the regime;
- find $f$;
- compute $\Delta p$ for the guess and compare with the given value;
- if it is too low, increase the guess (say by 10 %); if too high, decrease it; repeat until they agree.

A root finder such as bisection does the same job automatically, and the same idea, iterating because the equations are non-linear and implicit, is what a CFD solver does when it runs (8 May, ll. 564–570).

![[tf_pump_power_iteration.png|900]]

---

## Worked examples

### Worked example - laminar or turbulent in a copper tube

Air at atmospheric pressure and 50 °C flows at $1.23\times10^{-4}$ kg/s in a copper tube of outer diameter 8 mm and wall thickness 0.8 mm. Is the flow laminar or turbulent? (Chapter 15, Example 15.1.) At 50 °C, $\nu=1.798\times10^{-5}$ m²/s.

The inner diameter is $8-2\times0.8=6.4$ mm. The density is $\rho=101\,325/(287\times323.15)=1.093$ kg/m³, so

$$
\bar V=\frac{\dot m}{\rho A}=\frac{1.23\times10^{-4}}{1.093\times\tfrac{\pi}{4}\times0.0064^2}=3.50\ \mathrm{m/s}
$$

$$
Re_D=\frac{\bar VD}{\nu}=\frac{3.50\times0.0064}{1.798\times10^{-5}}=1250
$$

laminar. The entrance length is then about $0.06\times1250\times6.4$ mm $=0.48$ m.

### Worked example - wall shear from a pressure drop

Water at 58 °C flows from a tank at 4800 Pa gauge through a 10 cm pipe 12 m long into the atmosphere. Find the wall shear stress and the velocity gradient at the wall (Problem Sheet 11, Q11.7, the sheet's worked solution).

The flow is steady and fully developed, so the momentum flows in and out cancel and the pressure force balances the wall shear:

$$
\Delta p\frac{\pi D^2}{4}-\tau_w\pi DL=0
$$

$$
\tau_w=\frac{\Delta p\,D}{4L}=\frac{4800\times0.1}{4\times12}=10.0\ \mathrm{Pa}
$$

With $\mu=4.804\times10^{-4}$ Pa s at 58 °C,

$$
\left|\frac{dv_x}{dy}\right|_w=\frac{\tau_w}{\mu}=\frac{10}{4.804\times10^{-4}}=2.08\times10^4\ \mathrm{s^{-1}}
$$

### Worked example - board sliding on an oil film

A 1 m × 1 m board weighing 25 N slides down a 20° ramp at a steady 2.0 cm/s on an oil film of viscosity 0.05 Pa s. Treating the film as Couette flow, find its thickness (Problem Sheet 11, Q11.3, the tutorial problem).

At steady speed the weight component down the slope balances the viscous drag $\tau A=\mu(U/h)A$:

$$
W\sin20°=\mu\frac{U}{h}A
$$

$$
h=\frac{\mu UA}{W\sin20°}=\frac{0.05\times0.02\times1}{25\times0.342}=1.17\times10^{-4}\ \mathrm m=0.117\ \mathrm{mm}
$$

### Worked example - poor man's rheometer

A tank of oil ($\rho=800$ kg/m³) is kept 300 mm above a horizontal outlet pipe of diameter 3 mm and length 150 mm. 50 cm³ flows out in 167 s. Assuming laminar flow, find the viscosity (Problem Sheet 11, Q11.8).

$\dot{\mathcal V}=50\times10^{-6}/167=2.99\times10^{-7}$ m³/s, driven by $\Delta p=\rho gh$. From Hagen–Poiseuille, $\dot{\mathcal V}=\pi D^4\Delta p/(128\mu L)$, so

$$
\mu=\frac{\pi D^4\rho gh}{128L\dot{\mathcal V}}=\frac{\pi\times0.003^4\times800\times9.81\times0.3}{128\times0.15\times2.99\times10^{-7}}=0.104\ \mathrm{Pa\,s}
$$

> [!check] Was the flow laminar?
> $\bar V=\dot{\mathcal V}/A=0.042$ m/s, so $Re_D=\rho\bar VD/\mu=800\times0.042\times0.003/0.104\approx1$, deeply laminar. The kinetic energy of the jet and the entrance losses are neglected, which is reasonable at such a low speed.

### Worked example - pump for a water tank

A 200 L tank is to be emptied in under a minute through a tube 5 m long, 20 mm in diameter, with roughness 0.2 mm. Find the minimum pumping power (Chapter 15, Example 15.3, a type 1 problem).

$$
\dot{\mathcal V}=\frac{0.2}{60}=3.33\times10^{-3}\ \mathrm{m^3/s},\qquad \bar V=\frac{\dot{\mathcal V}}{\pi D^2/4}=10.6\ \mathrm{m/s}
$$

$$
Re_D=\frac{10.6\times0.02}{10^{-6}}=2.12\times10^5
$$

turbulent, with $\epsilon/D=0.01$. Colebrook gives $f=0.038$; the Moody chart, where this point is nearly fully rough, gives just under 0.04, and 0.04 errs on the safe side:

$$
\Delta p=f\frac LD\tfrac12\rho\bar V^2=0.04\times\frac{5}{0.02}\times\tfrac12\times1000\times10.6^2=5.63\times10^5\ \mathrm{Pa}
$$

about 5.6 bar, so the fittings must be rated for it.

$$
\dot W_{p,ideal}=\dot{\mathcal V}\Delta p=3.33\times10^{-3}\times5.63\times10^5=1.88\ \mathrm{kW}
$$

### Worked example - liquid-hydrogen pipeline

Liquid hydrogen ($\rho=70.9$ kg/m³, $\mu=1.3\times10^{-5}$ Pa s) must flow at 2 L/s through a 1 km, well-insulated pipeline of diameter 20 mm and roughness 0.004 mm. Pumps deliver 1 kW each. How many are needed? (Mock exam, 13 May, ll. 300–373.)

$$
\bar V=\frac{0.002}{\tfrac\pi4\times0.02^2}=6.37\ \mathrm{m/s}
$$

$$
Re_D=\frac{\rho\bar VD}{\mu}=\frac{70.9\times6.37\times0.02}{1.3\times10^{-5}}=6.9\times10^5
$$

turbulent. With $\epsilon/D=0.004/20=2\times10^{-4}$ the Moody chart gives $f\approx0.015$ (Colebrook: 0.0150).

$$
\Delta p=0.015\times\frac{1000}{0.02}\times\tfrac12\times70.9\times6.37^2=1.08\times10^6\ \mathrm{Pa}
$$

about 10.8 bar, and the ideal power is $\dot{\mathcal V}\Delta p=0.002\times1.08\times10^6=2.2$ kW. Three 1 kW pumps are needed.

### Worked example - oil tanker discharge

Oil ($\rho=800$ kg/m³, $\mu=0.03$ Pa s) is discharged at 1250 m³/h through 500 m of smooth 300 mm pipe, with a pump efficiency of 60 %. Find the pump power for the horizontal pipe, and then with an extra 25 m vertical rise from the bottom of the tank through a 200 mm pipe. Use the friction-factor table below with linear interpolation (Problem Sheet 11, Q11.6).

| $Re$ | $3.5\times10^4$ | $4.0\times10^4$ | $4.5\times10^4$ | $5.0\times10^4$ | $5.5\times10^4$ | $6.0\times10^4$ |
|---|---|---|---|---|---|---|
| $f$ | 0.0234 | 0.0226 | 0.0220 | 0.0214 | 0.0209 | 0.0204 |

$\dot{\mathcal V}=0.347$ m³/s. In the 300 mm pipe, $\bar V=4.91$ m/s, $Re=3.93\times10^4$ and $f=0.0227$, so the head loss is

$$
h_1=f\frac LD\frac{\bar V^2}{2g}=0.0227\times\frac{500}{0.3}\times\frac{4.91^2}{2\times9.81}=46.6\ \mathrm m
$$

$$
\dot W_p=\frac{\rho g\dot{\mathcal V}h_1}{\eta_p}=\frac{800\times9.81\times0.347\times46.6}{0.6}=211\ \mathrm{kW}
$$

In the 200 mm riser, $\bar V=11.05$ m/s, $Re=5.89\times10^4$ and $f=0.0205$, so it adds the 25 m lift and its friction:

$$
h_2=25+0.0205\times\frac{25}{0.2}\times\frac{11.05^2}{2\times9.81}=41.0\ \mathrm m
$$

$$
\dot W_p=\frac{800\times9.81\times0.347\times(46.6+41.0)}{0.6}=398\ \mathrm{kW}
$$

### Worked example - fuel line, a type 2 problem

Fuel ($\rho=820$ kg/m³, $\mu=4\times10^{-4}$ Pa s) flows from 20 bar to 15 bar through a 2 m pipe of diameter 10 mm and roughness 0.05 mm, with negligible minor losses. Find the flow rate and the regime (Problem Sheet 11, Q11.10, the tutorial problem).

The pressure drop is fixed at $5\times10^5$ Pa, and $\bar V$ must satisfy

$$
\Delta p=f(Re_D,\epsilon/D)\frac LD\tfrac12\rho\bar V^2,\qquad Re_D=\frac{\rho\bar VD}{\mu},\qquad \frac{\epsilon}{D}=0.005
$$

Start from the suggested $\dot{\mathcal V}=10^{-3}$ m³/s, i.e. $\bar V=12.7$ m/s: $Re_D=2.6\times10^5$, Colebrook $f=0.0308$ and $\Delta p=4.1\times10^5$ Pa, too low, so increase $\bar V$. Converging (by hand, or with `brentq` on the residual):

$$
\bar V=14.09\ \mathrm{m/s},\qquad f=0.0307,\qquad \dot{\mathcal V}=1.107\times10^{-3}\ \mathrm{m^3/s},\qquad Re_D=2.89\times10^5
$$

turbulent. Since $f$ barely changes over the iteration (the pipe is nearly fully rough), a single correction $\bar V_{new}=\bar V\sqrt{\Delta p/\Delta p_{guess}}$ already lands close.

### Worked example - minor-loss coefficient of a valve

A valve in a 4.2 cm pipe carrying coolant ($\rho=1049$ kg/m³) is tested with piezometers either side. The head difference is 1.39, 4.53 and 8.79 cm at 1.2, 2.3 and 3.2 L/s. Find $K$ (Problem Sheet 11, Q11.9).

The pressure drop is $\rho gh$ and $K=\rho gh/(\tfrac12\rho\bar V^2)=2gh/\bar V^2$, independent of density. With $A=1.385\times10^{-3}$ m²:

| Test | $\bar V$ (m/s) | $K=2gh/\bar V^2$ |
|---|---|---|
| 1 | 0.866 | 0.364 |
| 2 | 1.660 | 0.322 |
| 3 | 2.310 | 0.323 |

The mean is $K=0.336$. The smallest reading (test 1) is the least certain; a least-squares line through the origin of $\Delta p$ against $\tfrac12\rho\bar V^2$, which weights the larger readings more, gives 0.324.

![[tf_q11_9_minor_loss.png|900]]

### Worked example - pump-limited flow

A 350 W pump drives water ($\nu=10^{-6}$ m²/s) through a horizontal pipe 115 m long, 2.54 cm in diameter, roughness 0.002 mm. Estimate the flow rate, assuming an ideal pump (Chapter 15, Example 15.4, a type 2 variant).

The power is $\dot{\mathcal V}\Delta p=\tfrac\pi4D^2\bar V\cdot f\tfrac LD\tfrac12\rho\bar V^2$, so the bulk velocity is a root of

$$
g(\bar V)=\dot W_p-f(\bar V)\frac{\pi}{8}\rho\bar V^3LD=0
$$

non-linear through $\bar V^3$ and through Colebrook. Plotting $g$ shows a root near 2.5 m/s; bisection on $[1,4]$ gives

$$
\bar V=2.47\ \mathrm{m/s},\qquad Re_D=6.3\times10^4,\qquad \dot{\mathcal V}=1.25\ \mathrm{L/s}
$$

an upper bound, since a real pump is less than 100 % efficient.

---

## Links

- Parent: [[SESA1016 Thermofluids Hub]] · Previous: [[SESA1016 T14 - Boundary Layers and the Origin of Drag]]
- Concepts: [[Darcy Friction Factor]] · [[Major and Minor Head Losses]] · [[Reynolds Number]] · [[Newtonian Fluid and Viscosity]] · [[Pressure and Head]]
- Worked sheet: [[SESA1016 Problem Sheet 11 - Flows in Conduits Solutions]] · Formula list: [[SESA1016 Formula Sheet]]
- Continues in: [[SESA2029 A8 - Turbulence, RANS and Turbulence Models]] (turbulent wall flows) · [[SESA2023 W04 - Friction, Heat Addition, Oblique Shocks and Intakes]] (friction in compressible duct flow)

## Sources

- `Chapter 15.pdf`: lecture notes Chapter 15, Flow in conduits, §§15.1–15.8, Examples 15.1–15.4, Tables 15.1–15.2, Figs 15.1–15.14.
- `SESA1016 Lecture 2025-05-08.txt` (8 May 2025): module feedback and exam format (ll. 1–113), minor losses (ll. 115–197), combined losses (ll. 198–234), pumps and the SFEE for a liquid (ll. 235–451), type 2 and type 1 problems (ll. 452–590).
- `SESA1016 Lecture 2025-05-13.txt` (13 May 2025): mock-exam solutions; the pipeline question (ll. 300–373) is used here, the Stirling engine in [[SESA1016 T5 - Ideal Heat Engine Models|T5]] and the water jet in [[SESA1016 T12 - Conservation of Momentum|T12]].
- The lecture of 6 May 2025 on §§15.1–15.6 was not recorded; those sections are written from the lecture notes.
- `Problem Sheet 11 - Flows in Conduits.pdf`: Q11.1–Q11.10, printed answers and the worked solution to Q11.7.

## Self-study tasks

### Core

- [ ] Work through the type 2 iteration by hand or in Python for a tank-fed pipe (set for the tutorial, 8 May, ll. 459–462). → [[#Two types of problem]] · [[#Worked example - fuel line, a type 2 problem]]
- [ ] Q11.1, the one-seventh-power profile. Target $V_{max}/\bar V=1.22$. → [[#5. Turbulent velocity profiles]]
- [ ] Q11.2, plane Poiseuille flow between plates: profiles, flow rate per unit width, wall shear. Targets $\tfrac43V_{max}h$ and $2\mu V_{max}/h$. → [[SESA1016 Problem Sheet 11 - Flows in Conduits Solutions]]
- [ ] Q11.3, board on an oil film (tutorial problem). Target 0.117 mm. → [[#Worked example - board sliding on an oil film]]
- [ ] Q11.4, sphere falling in a tube. Target 1.3 m/s. → [[SESA1016 Problem Sheet 11 - Flows in Conduits Solutions]]
- [ ] Q11.5, laminar or turbulent water flow. Answer: turbulent, $Re_D\approx10^4$. → [[#2. Reynolds' experiment]]
- [ ] Q11.6, oil tanker. Targets 211.4 kW and 397.5 kW. → [[#Worked example - oil tanker discharge]]
- [ ] Q11.7, force balance in a pipe (worked solution). Targets 10 Pa and $2.08\times10^4$ s⁻¹. → [[#Worked example - wall shear from a pressure drop]]
- [ ] Q11.8, poor man's rheometer. Target 0.104 Pa s. → [[#Worked example - poor man's rheometer]]
- [ ] Q11.9, minor-loss coefficient of a valve. Target 0.336. → [[#Worked example - minor-loss coefficient of a valve]]
- [ ] Q11.10, SAF fuel line (tutorial problem). Targets $1.107\times10^{-3}$ m³/s, $Re_D=2.89\times10^5$. → [[#Worked example - fuel line, a type 2 problem]]

### Further practice

- [ ] Derive the Poiseuille profile, $\bar V=\tfrac12V_{max}$ and $f=64/Re_D$ (Chapter 15, §§15.4, 15.6). → [[#Derivation of the velocity profile]] · [[#Laminar flow]]
- [ ] Use dimensional analysis to show $f=f(Re_D,L/D)$ for a smooth pipe (left as an exercise in the notes, §15.6). → [[#Definition]]
- [ ] Derive the pump power from the SFEE for a liquid and explain where the inefficiency goes (8 May, ll. 265–430). → [[#The SFEE for a pump]]

## Transcript and slide slips

> [!warning] Lecture-notes slip (Chapter 15, eq. 15.44)
> Where: [[#Combined losses]].
>
> The pipe-loss term was printed with $\tfrac12\rho\bar V$ instead of $\tfrac12\rho\bar V^2$; the error was pointed out in the lecture and fixed in the updated notes (8 May, ll. 219–230).

> [!warning] Lecture-notes slip (Chapter 15, §15.6, after Fig. 15.10)
> Where: [[#Turbulent flow and roughness]].
>
> "If one managed to control laminar flow at $Re_D=10^4$, the friction factor would be 330 times less than that produced by turbulent flow in the smooth wall case." At $Re_D=10^4$, laminar $f=0.0064$ and smooth turbulent $f\approx0.031$: a factor of about 5, not 330.

> [!warning] Lecture-notes rounding (Chapter 15, Example 15.3)
> Where: [[#Worked example - pump for a water tank]].
>
> The Colebrook friction factor is printed as $3.791\times10^{-2}$; solving eq. 15.41 at $Re_D=2.12\times10^5$, $\epsilon/D=0.01$ gives 0.0382. The example then uses the chart value 0.04, so the result is unchanged.

> [!warning] Problem-sheet slip (Problem Sheet 11, answers to Q11.7)
> Where: [[#Worked example - wall shear from a pressure drop]].
>
> The answer block lists "11.7 926 Pa", which matches neither part of the question; the worked solution's 10 Pa and $2.08\times10^4$ s⁻¹ follow from the data.
