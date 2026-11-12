---
title: "SESA1016 T13 - Conservation of Energy and Propulsion"
module: "SESA1016 Thermofluids"
type: topic
stream: "Part D: Control-volume Conservation Laws"
order: 13
tags: [sesa1016, sfee, energy, enthalpy, propulsion]
aliases: ["Steady-flow Energy Equation", "Jet Propulsion"]
date: 2026-09-25
status: lectured
coverage: "Lectures of 25 Mar 2025 (ll. 10–832: forms of energy, flow of energy, energy conservation for a control volume, shaft and flow work, total enthalpy and the SFEE, the three conservation laws side by side) and 27 Mar 2025 (ll. 4–525: thrust from momentum conservation, SFEE for a jet engine, propulsive efficiency, turbofans and bypass ratio, turbojet components and cycle); Chapter 13 in full. The component-by-component SFEE of §13.5.1 was not reached in the lecture and is written from the notes."
parent: ["[[SESA1016 Thermofluids Hub]]"]
prerequisites: ["[[SESA1016 T12 - Conservation of Momentum]]", "[[SESA1016 T5 - Ideal Heat Engine Models]]"]
next_topics: ["[[SESA1016 T14 - Boundary Layers and the Origin of Drag]]"]
key_concepts: ["[[Steady-flow Energy Equation]]", "[[Internal Energy and Enthalpy]]", "[[Control-volume Analysis Workflow]]"]
tutorial_sheets: ["[[SESA1016 Problem Sheet 09 - Momentum and Energy Conservation Solutions]]"]
sources: ["02 - Sources/Lectures/Chapter 13.pdf", "02 - Sources/Lectures/SESA1016 Lecture 2025-03-25.txt", "02 - Sources/Lectures/SESA1016 Lecture 2025-03-27.txt", "02 - Sources/Tutorial Sheets/Problem Sheet 09 - Momentum and Energy Conservation.pdf"]
---

# SESA1016 T13 - Conservation of Energy and Propulsion

> [!abstract] Summary
> A moving fluid carries kinetic, potential and internal energy, $e=\tfrac12V^2+gz+u$ per kilogram, through a surface at a rate $\dot E=\int_A\rho e\,\vec V\cdot\vec n\,dA$, or $\dot me$ for uniform flow. The first law for a control volume says heat in minus work out equals the rate of change of energy inside plus the net outflow. Splitting the work into shaft work and the flow work done by pressure at the ports, and absorbing the flow work into enthalpy, gives the steady-flow energy equation $\dot Q-\dot W_x=\dot m(h_{tot,out}-h_{tot,in})$ with $h_{tot}=\tfrac12V^2+gz+h$. With momentum conservation it explains how a jet engine makes thrust, $T=\dot m(V_j-V_\infty)$, why accelerating a large mass of air a little (a turbofan) is more efficient than a small mass a lot, and what each component of a turbojet does.

> [!summary]- Exam use: quick path
> - **Use it when:** heat or shaft work is exchanged with a flowing fluid (heaters, heat exchangers, compressors, turbines, combustors, nozzles, intakes, pumps, dams), or a temperature or velocity at an outlet is wanted.
> - **Assumptions:** steady flow, uniform properties at each port, perfect gas ($\Delta h=c_p\Delta T$) or incompressible liquid ($\Delta h=c\Delta T$); $gz$ usually negligible for gases, kinetic energy often negligible in low-speed devices.
> - **Method:** 1. Draw the control volume through the ports and list what crosses it ($\dot Q$, $\dot W_x$, mass). 2. Write $\dot Q-\dot W_x=\sum_{out}\dot mh_{tot}-\sum_{in}\dot mh_{tot}$. 3. Strike out the terms that are zero or small (adiabatic, no moving parts, small $\Delta z$, small $V$). 4. Use continuity and $\rho=p/RT$ to get velocities; isentropic relations if a reversible adiabatic process links $p$ and $T$. 5. Check signs: $\dot W_x>0$ is work done **by** the fluid (turbine), negative for a compressor or pump.
> - **Common mistakes:** using $c_v\Delta T$ instead of $c_p\Delta T$ in a flow device (the flow work is already in $h$); forgetting the outlet kinetic energy when the outlet is fast.
> - **Practise:** [[#Worked example - hair dryer]] · [[SESA1016 Problem Sheet 09 - Momentum and Energy Conservation Solutions]] Q9.7–Q9.11

Energy, from an engineer's point of view, is the capacity of something to do work on its surroundings (25 Mar, ll. 14–25). Water behind a dam can be piped to a turbine; wind can turn a wind turbine's blades (and, in a storm, wreck them); fuel burnt in a jet engine heats gas that drives a turbine and then leaves the nozzle fast enough to push the aircraft. A fluid particle stores energy in three forms that matter here, kinetic, potential and internal, and it can convert between them; what the first law conserves is their total.

The closed-system first law, $\Delta U=Q-W$, follows one lump of gas. A jet engine has fresh air going through it continuously, so the relevant figure is not how many joules one lump receives but how many joules per second the engine handles. So, as for mass and momentum, the first law is rewritten for a control volume as a budget of energy rates: heat and work going in per second must show up as the difference between the energy carried out and carried in per second.

One subtlety appears at the ports. Pushing fluid into the control volume against the pressure behind it, and out against the pressure ahead of it, is work: flow work. It always accompanies the flow, so it is neater to fold it into the energy carried by the fluid, and that converts internal energy $u$ into enthalpy $h=u+p/\rho$. This is why enthalpy (first met in constant-pressure heating, [[SESA1016 T2 - Work, Heat and the First Law|T2]]) is the quantity used for every flow device.

---

## 1. Forms of energy for a fluid in motion

A fluid particle of mass $m$ and volume $\mathcal V$, at height $z$ above a reference, moving at speed $V$, with pressure $p$, density $\rho$ and temperature $T$, has three forms of energy:

| | Kinetic | Potential | Internal |
|---|---|---|---|
| Extensive (J) | $\tfrac12mV^2$ | $mgz$ | $U$ |
| Per unit mass (J/kg) | $\tfrac12V^2$ | $gz$ | $u$ |
| Per unit volume (J/m³) | $\tfrac12\rho V^2$ | $\rho gz$ | $\rho u$ |

Kinetic and potential energy (together, mechanical energy) belong to the particle's bulk motion and position; internal (thermal) energy belongs to the random motion of its molecules. Energy is a scalar, so only the speed matters, not the direction. The extensive forms depend on how much fluid is being tracked, so the intensive forms are more useful; "specific" means per unit mass. The **specific total energy** is

$$
\boxed{e=\tfrac12V^2+gz+u}
$$

(25 Mar, ll. 120–146). Other forms, chemical and electrical, are not needed here. For a gas flow the $gz$ term is usually negligible; for liquids it often matters.

## 2. Flow of energy through a surface

The energy crossing a surface per second is derived as for mass and momentum (25 Mar, ll. 152–214). Through an element $dA$ with unit normal $\vec n$, the volume crossing in time $dt$ is

$$
d\mathcal V=dA\,dx=dA\,(\vec V\cdot\vec n)\,dt
$$

with mass $dm=\rho\,d\mathcal V$. Each kilogram carries $e$, so the energy carried across is

$$
dE=e\,dm=\rho e\,(\vec V\cdot\vec n)\,dA\,dt
$$

Divide by $dt$ and integrate over the surface:

$$
\boxed{\dot E=\int_A\rho e\,(\vec V\cdot\vec n)\,dA}
$$

in J/s, i.e. watts. For flow perpendicular to the surface, $\dot E=\int_A\rho eV\,dA$. For uniform flow,

$$
\boxed{\dot E=\rho eVA=\dot me}
$$

the mass flow rate times the energy per unit mass, just as momentum flow is $\dot m\vec V$. Unlike momentum, the energy carried is never negative, so the only sign to watch is whether the flow is in or out.

## 3. Conservation of energy for a control volume

### From the closed system to rates

For a fixed mass the first law is $\Delta U=Q-W$, with $Q$ the heat into the gas and $W$ the work done by it. Divide by the time $\Delta t$ the process takes and let it be short:

$$
\frac{dU}{dt}=\dot Q-\dot W
$$

$\dot Q$ is the heat transfer rate (thermal power, positive into the fluid) and $\dot W$ the power delivered by the fluid to its surroundings, both in watts (25 Mar, ll. 292–336). Engines are rated in power, not joules per cycle.

### The control-volume statement

For a control volume (Chapter 13, eq. 13.29):

$$
\left\{\begin{matrix}\text{heat and work rates}\\\text{exchanged with the fluid in the CV}\end{matrix}\right\}=\left\{\begin{matrix}\text{rate of change of}\\\text{total energy in the CV}\end{matrix}\right\}+\left\{\begin{matrix}\text{net outflow of total}\\\text{energy through the CS}\end{matrix}\right\}
$$

Heat may cross the control surface ($\dot Q_{CS}$, from a hot wall) or be released inside it ($\dot Q_{CV}$, by combustion). Work includes the work of any moving device inside and the work done by pressure on the faces. The energy inside is

$$
E_{CV}=\int_{CV}\rho e\,d\mathcal V
$$

so mathematically

$$
\boxed{\dot Q-\dot W=\frac{d}{dt}\int_{CV}\rho e\,d\mathcal V+\int_{CS}\rho e\,(\vec V\cdot\vec n)\,dA}
$$

In steady flow $\rho$ and $e$ do not change with time at any point, so the accumulation term vanishes:

$$
\dot Q-\dot W=\int_{CS}\rho e\,(\vec V\cdot\vec n)\,dA
$$

Burning fuel inside the control volume ($\dot Q>0$) must show up as a positive net outflow of energy: the gas leaves hotter than it came in (25 Mar, ll. 413–435).

### Shaft work and flow work

The work splits into two parts (25 Mar, ll. 436–556):

$$
\dot W=\dot W_x+\dot W_{flow}
$$

**Shaft work** $\dot W_x$ is the work done by the fluid on any moving device inside: a turbine (positive), or a pump, fan or compressor doing work on the fluid (negative).

**Flow work** is the work done by pressure forces pushing fluid across the boundary. At the inlet, a slab of fluid of thickness $dx=V_{in}\,dt$ is about to enter, pushed in by the pressure $p_{in}$ of the fluid behind it. The fluid already inside is pushed back by this slab, so it does negative work on it:

$$
-p_{in}A_{in}\,dx=-p_{in}A_{in}V_{in}\,dt
$$

At the outlet, the fluid inside pushes a slab of thickness $V_{out}\,dt$ out against the pressure $p_{out}$ ahead of it, doing positive work $p_{out}A_{out}V_{out}\,dt$. Dividing by $dt$ and adding:

$$
\dot W_{flow}=p_{out}A_{out}V_{out}-p_{in}A_{in}V_{in}
$$

Multiply and divide each term by its density, and group $\rho AV=\dot m$, the same at both ports:

$$
\dot W_{flow}=\rho_{out}A_{out}V_{out}\frac{p_{out}}{\rho_{out}}-\rho_{in}A_{in}V_{in}\frac{p_{in}}{\rho_{in}}=\dot m\left(\frac p\rho\right)_{out}-\dot m\left(\frac p\rho\right)_{in}
$$

![[tf_flow_work.png|900]]

This looks like a flow of the quantity $p/\rho$, and for a general surface it is

$$
\dot W_{flow}=\int_{CS}\frac{p}{\rho}\,\rho(\vec V\cdot\vec n)\,dA
$$

### Total enthalpy and the SFEE

Substitute $\dot W=\dot W_x+\dot W_{flow}$ into the steady energy equation and move the flow work to the right, where it joins the energy flow as another surface integral:

$$
\dot Q-\dot W_x=\int_{CS}\rho e\,(\vec V\cdot\vec n)\,dA+\int_{CS}\frac{p}{\rho}\,\rho(\vec V\cdot\vec n)\,dA
$$

$$
\dot Q-\dot W_x=\int_{CS}\rho\left(\tfrac12V^2+gz+u+\frac p\rho\right)(\vec V\cdot\vec n)\,dA
$$

and $u+p/\rho=u+pv=h$, the enthalpy. For a perfect gas $u+p/\rho=c_vT+RT=c_pT$. Define the **specific total enthalpy**

$$
\boxed{h_{tot}=\tfrac12V^2+gz+h}
$$

Then the **steady-flow energy equation** (SFEE) is

$$
\boxed{\dot Q-\dot W_x=\int_{CS}\rho h_{tot}\,(\vec V\cdot\vec n)\,dA}
$$

The heat and shaft work exchanged with the fluid balance the net outflow of total enthalpy. Enthalpy has taken care of the flow work, which is why it, and not internal energy, appears in every flow calculation.

### Simplified forms

For two ports with uniform flow:

$$
\boxed{\dot Q-\dot W_x=\dot m\left(h_{tot,out}-h_{tot,in}\right)}
$$

and per unit mass, $q-w_x=\Delta h_{tot}$. For several ports:

$$
\dot Q-\dot W_x=\sum_{out}\dot m\,h_{tot,out}-\sum_{in}\dot m\,h_{tot,in}
$$

Not every term matters in every problem (25 Mar, ll. 683–773). Across a 1 m tall jet engine, $\Delta(gz)\approx10$ J/kg, while $c_p\Delta T\approx1000\times1000=10^6$ J/kg: drop $gz$ for gas flows, keep it for pumps and hydraulic systems. In a combustor the gas moves slowly for flame stability, so kinetic energy can be dropped there too.

### The three conservation laws together

Mass, momentum and energy conservation have the same structure (25 Mar, ll. 778–827). With uniform flow through one inlet and one outlet, in steady flow:

| Law | Net outflow (general) | Uniform, one in, one out | Balances |
|---|---|---|---|
| Mass | $\int_{CS}\rho\,(\vec V\cdot\vec n)\,dA$ | $\dot m_{out}-\dot m_{in}$ | 0 |
| Momentum | $\int_{CS}\rho\vec V(\vec V\cdot\vec n)\,dA$ | $\dot m(\vec V_{out}-\vec V_{in})$ | $\sum\vec F$ |
| Energy | $\int_{CS}\rho h_{tot}(\vec V\cdot\vec n)\,dA$ | $\dot m(h_{tot,out}-h_{tot,in})$ | $\dot Q-\dot W_x$ |

Each is used in one of two ways: knowing what is done to the fluid, find the outlet state; or knowing both states, find what was done to the fluid.

## 4. The Reynolds transport theorem

The three laws are special cases of one theorem. Each starts as a Lagrangian law for a closed system, $dB/dt$, for an extensive quantity $B$ with intensive (per unit mass) counterpart $b$:

| | Mass | Momentum | Energy |
|---|---|---|---|
| $B$ | $m$ | $m\vec V$ | $me$ |
| $dB/dt$ (closed system) | 0 | $\sum\vec F$ | $\dot Q-\dot W$ |
| $b$ | 1 | $\vec V$ | $e$ |
| flow, uniform | $\dot m$ | $\dot m\vec V$ | $\dot me$ |

The **Reynolds transport theorem** (RTT), stated without proof, links the closed-system rate to the control volume:

$$
\frac{dB}{dt}=\frac{d}{dt}\int_{CV}\rho b\,d\mathcal V+\int_{CS}\rho b\,(\vec V\cdot\vec n)\,dA
$$

For steady flow with uniform ports,

$$
\frac{dB}{dt}=\sum_{out}\dot m\,b_{out}-\sum_{in}\dot m\,b_{in}
$$

Putting $b=1$, $\vec V$ or $e$ recovers continuity, the momentum equation and the energy equation.

## 5. Jet propulsion

### Thrust from momentum conservation

In cruise the thrust of the engines balances the drag (induced plus parasitic) of the aircraft. Work in the aircraft's frame, so air approaches at $V_\infty$ (27 Mar, ll. 21–112). Draw a control volume round an engine, large enough that the pressure is atmospheric all over its surface. Air enters the streamtube feeding the engine at $V_\infty$ and leaves as a jet at $V_j$; outside the streamtube the velocity stays $V_\infty$ and contributes no net momentum change. The air mass flow is $\dot m_{air}$ and the fuel adds $\dot m_{fuel}$, but the fuel-to-air ratio is only 1–5 %, so $\dot m_{fuel}$ is neglected.

![[tf_jet_engine_cv.png|900]]

The net outflow of $x$-momentum is $\dot m_{air}V_j-\dot m_{air}V_\infty$. Pressure is atmospheric all round, so the only force on the fluid is the force $T$ from the engine's components:

$$
\boxed{T=\dot m_{air}(V_j-V_\infty)}
$$

With $V_j>V_\infty$, the engine pushes the air backwards; by Newton's third law the air pushes the engine forwards, and that reaction is the thrust. There are two ways to get a given thrust: accelerate a small mass flow a lot (large $V_j-V_\infty$), or a large mass flow a little (large $\dot m_{air}$) (27 Mar, ll. 128–151).

### Energy balance and propulsive efficiency

Apply the SFEE to the same control volume (27 Mar, ll. 155–222). Fuel burnt at $\dot m_{fuel}$ with calorific value $C_v$ releases $\dot Q=\dot m_{fuel}C_v$. The compressor and turbine are inside the control volume and are paid for by $\dot Q$, so no external shaft work crosses it, $\dot W_x=0$. With $\Delta h=c_p\Delta T$:

$$
\dot Q=\dot m_{air}\left[c_p(T_j-T_\infty)+\tfrac12\left(V_j^2-V_\infty^2\right)\right]
$$

The fuel energy ends up as hotter exhaust and faster exhaust. Efficiency is useful output over input. The input is $\dot Q$; the output is thrust at flight speed, the power needed to fly, $P=TV_\infty=DV_\infty$. The **propulsive efficiency** is defined as

$$
\eta_p=\frac{TV_\infty}{\dot Q}
$$

and substituting the two conservation results, with $\dot m_{air}$ cancelling,

$$
\boxed{\eta_p=\frac{(V_j-V_\infty)V_\infty}{c_p(T_j-T_\infty)+\tfrac12\left(V_j^2-V_\infty^2\right)}}
$$

(Propulsion in Part 2 calls this ratio of thrust power to fuel power the overall efficiency and reserves "propulsive efficiency" for thrust power over the kinetic-energy part of the denominator alone.)

How $\eta_p$ depends on $V_j/V_\infty$ needs a full cycle calculation for $T_j$, but the trend is clear from the kinetic-energy part of the denominator alone. Since $\dot Q$ is at least the kinetic-energy term,

$$
\eta_p\le\frac{(V_j-V_\infty)V_\infty}{\tfrac12(V_j^2-V_\infty^2)}=\frac{2V_\infty}{V_j+V_\infty}=\frac{2}{1+V_j/V_\infty}
$$

which falls as $V_j/V_\infty$ rises: wasting kinetic energy in a fast jet is expensive. Since $\dot Q=DV_\infty/\eta_p$, a lower $\eta_p$ means more fuel for the same aircraft. Accelerating a large mass of air by a little is more fuel-efficient (27 Mar, ll. 270–292).

![[tf_propulsive_efficiency.png|900]]

### Turbofans and bypass ratio

That is the principle of the **turbofan**. A large fan at the front drives most of the air through a cold bypass duct, $\dot m_f$, accelerating it only slightly to $V_f$ with a small temperature rise. A smaller core flow $\dot m_j$ passes through the hot section (a small turbojet that drives the fan) and leaves faster and hotter. The **bypass ratio** is

$$
\mathrm{BPR}=\frac{\dot m_f}{\dot m_j}
$$

up to 10–12 for modern airliners, and the thrust adds the two streams:

$$
T=\dot m_f(V_f-V_\infty)+\dot m_j(V_j-V_\infty)
$$

The fan's share can be 80–90 % of the total, giving the low fuel burn that keeps airliner tickets cheap (27 Mar, ll. 293–353). Military aircraft prioritise thrust-to-weight ratio, compactness, radar signature and speed, so they use low-bypass turbofans or turbojets and accept the higher fuel burn.

### Components of a turbojet

The core of a jet engine follows, loosely, the Brayton cycle of [[SESA1016 T5 - Ideal Heat Engine Models#The Brayton cycle|T5]], but as an open cycle: the exhaust is not cooled and returned to the compressor but thrown out, and the heat it carries away (the area under 6→1 on the $T$–$s$ diagram, $\dot m c_p(T_j-T_\infty)$) is real and lowers the efficiency (27 Mar, ll. 436–525). The stations are 1 (free stream), 2 (intake exit), 3 (compressor exit), 4 (turbine inlet), 5 (turbine exit) and 6 (nozzle exit). Each component is analysed with the SFEE on its own control volume, steady, with uniform ports and $gz$ dropped.

#### Intake

In the intake (1 to 2) the flow passes too quickly to exchange heat, and nothing moves, so $\dot Q=\dot W_x=0$ and

$$
\tfrac12V_1^2+h_1=\tfrac12V_2^2+h_2
$$

The total enthalpy is conserved (the flow is iso-enthalpic in total terms). A good intake turns kinetic energy into enthalpy: it slows the air, raising its temperature and pressure to give the compressor a good inflow. If the deceleration is smooth and lossless it is also isentropic, $T_1p_1^{(1-\gamma)/\gamma}=T_2p_2^{(1-\gamma)/\gamma}$, so the intake does a first stage of compression.

#### Compressor

In the compressor (2 to 3), rows of rotating blades (an axial compressor, with stator rows between) do work on the air; adiabatic, so $\dot Q=0$. The shaft work is negative (done on the fluid), so writing $\dot W_c=-\dot W_x$ for the power put in:

$$
\dot W_c=\dot m\left(h_{tot,3}-h_{tot,2}\right),\qquad w_c=c_p(T_3-T_2)+\tfrac12\left(V_3^2-V_2^2\right)
$$

The kinetic-energy term can matter in a high-speed flow device. An efficient compressor is close to isentropic.

#### Burner

In the burner (3 to 4), fuel burns in the compressed air at nearly constant pressure, with no moving parts, $\dot W_x=0$:

$$
\dot Q=\dot m\left(h_{tot,4}-h_{tot,3}\right),\qquad q=c_p(T_4-T_3)
$$

with kinetic energy dropped because combustor velocities are low. $T_4$, the turbine inlet temperature, is the highest in the engine, often above the melting point of the blade metal, so turbine blades are cooled by air bled from the compressor through internal channels. A high pressure ratio raises the Brayton efficiency but also raises $T_3$ and so $T_4$, which is a fundamental technological limit.

#### Turbine

In the turbine (4 to 5), the hot gas expands (falls in pressure and temperature) through the turbine blades and does work on them; adiabatic, so

$$
-\dot W_x=\dot m\left(h_{tot,5}-h_{tot,4}\right)
$$

and the turbine power is

$$
\dot W_t=\dot W_x=\dot m\left(h_{tot,4}-h_{tot,5}\right)
$$

In a turbojet this drives the compressor (on one, two or three shafts) and the on-board hydraulic and electrical systems.

#### Nozzle

The nozzle (5 to 6) is adiabatic and has no moving parts, so again the total enthalpy is conserved:

$$
\tfrac12V_5^2+h_5=\tfrac12V_6^2+h_6
$$

The nozzle does the opposite of the intake: it turns enthalpy into kinetic energy. For a perfect gas,

$$
V_6=\sqrt{V_5^2+2c_p(T_5-T_6)}
$$

and for a smooth, reversible expansion $T_6=T_5(p_6/p_5)^{(\gamma-1)/\gamma}$, so the pressure ratio fixes the jet speed. A subsonic nozzle converges and a subsonic diffuser diverges; in supersonic flow it is the other way round.

---

## Worked examples

### Worked example - power available at a dam

Water is drawn from 100 m below the surface of a reservoir and discharged through four outlet tubes of diameter 2.44 m. Estimate the power a turbine could extract (Chapter 13, Example 13.1).

The ideal turbine at the outlet level could extract the flow of kinetic energy, $\dot m\cdot\tfrac12V^2$; internal energy cannot be extracted by a turbine. For the greatest possible speed, take the flow as inviscid and apply Bernoulli from the surface (0, at rest, $z_0=100$ m) to the outlet (1, $z_1=0$), both at atmospheric pressure:

$$
\tfrac12\rho V_1^2=\rho gz_0
$$

$$
V_1=\sqrt{2gz_0}=\sqrt{2\times9.81\times100}=44.3\ \mathrm{m/s}
$$

Each tube has area $\pi\times2.44^2/4=4.676$ m², so

$$
\dot m=4\rho AV_1=4\times1000\times4.676\times44.3=8.28\times10^5\ \mathrm{kg/s}
$$

828 tonnes per second. Each kilogram carries $\tfrac12V_1^2=gz_0=981$ J, so

$$
\dot W_{max}=\dot m\,gz_0=8.28\times10^5\times981=0.81\ \mathrm{GW}
$$

The quick estimate $\dot W=\dot mgh$ is the quick estimate for hydroelectric schemes. The installed capacity of this dam is about 1.3 GW (from more water and more head than these four tubes).

### Worked example - energy leaving a GPU cooler

The outlet of a GPU cooler is 1.2 cm high and 18 cm wide. The temperature varies linearly from 400 K at the bottom to 350 K at the top, and the velocity is $V=V_{max}[1-(y/h)^2]$ with $V_{max}=1.2$ m/s. Which forms of energy matter, and what is the energy flow out? (Chapter 13, Example 13.2.)

Air enters at rest at 300 K and the device is about 10 cm high, so the changes in specific energy are

$$
\Delta\left(\tfrac12V^2\right)=0.72\ \mathrm{J/kg},\qquad \Delta(gz)=0.98\ \mathrm{J/kg},\qquad \Delta(c_vT)\approx718\times75=53\,850\ \mathrm{J/kg}
$$

so only internal energy matters. The flow is non-uniform but perpendicular, so with $dA=w\,dy$,

$$
\dot E\approx\int_0^h\rho(y)c_vT(y)V(y)w\,dy
$$

At atmospheric pressure $\rho=p_{atm}/(RT)$, so $\rho c_vT=p_{atm}c_v/R=p_{atm}/(\gamma-1)$, independent of temperature: hotter air is less dense, and the two effects cancel. Then

$$
\dot E=\frac{p_{atm}}{\gamma-1}\int_0^hV(y)w\,dy=\frac{p_{atm}}{\gamma-1}\dot{\mathcal V}
$$

$$
\dot{\mathcal V}=wV_{max}\frac{2h}{3}=0.18\times1.2\times\tfrac23\times0.012=1.728\times10^{-3}\ \mathrm{m^3/s}
$$

$$
\dot E=\frac{101\,325}{0.4}\times1.728\times10^{-3}=438\ \mathrm W
$$

> [!tip] An energy flow is only meaningful as a difference
> The 438 W counts internal energy from absolute zero, so on its own it is not the heat the cooler removes. What the first law uses is the difference between outflow and inflow. With the inlet at 300 K and enthalpy as the flowing quantity, $\int\rho Vc_p(T-300)w\,dy=130$ W is the heat the airstream actually carries away from the GPU.

### Worked example - air-water heat exchanger

Water at 2 L/s enters a building heat exchanger at 96 °C and leaves 20 °C cooler; air is heated from 18 °C to 46 °C. Kinetic energy is negligible. Find the air mass flow (Problem Sheet 9, Q9.7, the sheet's worked solution).

Apply the SFEE to each stream with no shaft work. Water side, $c=4200$ J kg⁻¹ K⁻¹, $\dot m_w=2$ kg/s:

$$
\dot Q_w=\dot m_wc(T_{out}-T_{in})=2\times4200\times(-20)=-168\ \mathrm{kW}
$$

negative because the water loses heat. The air gains the same 168 kW:

$$
\dot m_a=\frac{\dot Q}{c_p(T_{a,out}-T_{a,in})}=\frac{168\,000}{1005\times28}=5.97\ \mathrm{kg/s}
$$

### Worked example - hair dryer

A hair dryer has a 100 W fan and a 600 W heater. Air enters through a large inlet at 18 °C and 1 bar and leaves through a 30 mm outlet at 50 °C and 1 bar, with no heat loss from the casing. Find the densities, the enthalpy rise, the mass flow and the exit velocity, first neglecting kinetic energy and then including it (Problem Sheet 9, Q9.9, the tutorial problem).

Densities from $\rho=p/(RT)$:

$$
\rho_1=\frac{10^5}{287\times291.15}=1.197\ \mathrm{kg/m^3},\qquad \rho_2=\frac{10^5}{287\times323.15}=1.078\ \mathrm{kg/m^3}
$$

Enthalpy rise, with $c_p=1004.5$ J kg⁻¹ K⁻¹ (from $\gamma R/(\gamma-1)$):

$$
\Delta h=c_p(T_2-T_1)=1004.5\times32=32\,144\ \mathrm{J/kg}
$$

The control volume encloses the whole dryer: the heater supplies $\dot Q=600$ W and the fan does 100 W of work on the air, $\dot W_x=-100$ W, so $\dot Q-\dot W_x=700$ W. Neglecting kinetic energy:

$$
\dot m=\frac{700}{32\,144}=0.0218\ \mathrm{kg/s}
$$

$$
V_2=\frac{\dot m}{\rho_2A_2}=\frac{0.0218}{1.078\times\pi\times0.03^2/4}=28.6\ \mathrm{m/s}
$$

Including the outlet kinetic energy (the inlet is large, so $V_1\approx0$):

$$
700=\dot m\left[\Delta h+\tfrac12\left(\frac{\dot m}{\rho_2A_2}\right)^2\right]
$$

which solved numerically gives $\dot m=0.0215$ kg/s and $V_2=28.2$ m/s. The kinetic energy, about 400 J/kg against 32 kJ/kg of enthalpy, changes the answer by about 1.2 %: neglecting it was reasonable.

### Worked example - industrial gas turbine

Air at 15 °C enters the compressor of an industrial gas turbine with negligible kinetic energy and leaves at 316 kg/s, 12.56 bar and 395 °C through a 0.4 m² duct. The combustor raises it to 1162 °C (exit kinetic energy negligible), and the turbine exhausts at 522 °C (kinetic energy negligible at both ends). Find the compressor exit velocity and power, the heat input, the turbine power, the electrical power and the plant efficiency (Problem Sheet 9, Q9.10).

![[tf_gas_turbine_blocks.png|900]]

Compressor exit density and velocity:

$$
\rho_2=\frac{12.56\times10^5}{287\times668.15}=6.55\ \mathrm{kg/m^3},\qquad V_2=\frac{316}{6.55\times0.4}=120.6\ \mathrm{m/s}
$$

Compressor, adiabatic, exit kinetic energy kept:

$$
\dot W_x=-\dot m\left[c_p(T_2-T_1)+\tfrac12V_2^2\right]
$$

Combustor, no work, inlet kinetic energy kept and exit kinetic energy dropped:

$$
\dot Q=\dot m\left[c_p(T_3-T_2)-\tfrac12V_2^2\right]
$$

Turbine, $\dot W_t=\dot mc_p(T_3-T_4)$. The printed answers correspond to $c_p=1010$ J kg⁻¹ K⁻¹, a mean value for air over this temperature range:

$$
\dot W_x=-316\times\left[1010\times380+7273\right]=-123.6\ \mathrm{MW}
$$

$$
\dot Q=316\times\left[1010\times767-7273\right]=242.5\ \mathrm{MW}
$$

$$
\dot W_t=316\times1010\times640=204.3\ \mathrm{MW}
$$

The generator gets what the turbine does not spend on the compressor:

$$
\dot W_{el}=204.3-123.6=80.7\ \mathrm{MW},\qquad \eta=\frac{80.7}{242.5}=33.3\ \%
$$

With $c_p=1005$ J kg⁻¹ K⁻¹ the same method gives −123.0, 241.3, 203.3 and 80.3 MW and 33.3 %.

> [!check] Energy balance of the whole plant
> Around the whole plant: heat in 242.5 MW, electrical power out 80.7 MW, so the exhaust must carry away 161.8 MW more enthalpy than the intake air brought in. $\dot mc_p(T_4-T_1)=316\times1010\times507=161.8$ MW, matching the 161.8 MW above.

### Worked example - nozzle expansion

A converging nozzle with inlet diameter 0.8 m and outlet diameter 0.2 m receives hot gas at 1300 K and 1.4 bar and exhausts to 1 bar. It is well insulated, and the expansion is isentropic. Find the exit conditions, the mass flow and the exit Mach number (Problem Sheet 9, Q9.11). Take air properties, $c_p=1004.5$ J kg⁻¹ K⁻¹.

Isentropic exit temperature:

$$
T_2=1300\times\left(\frac{1}{1.4}\right)^{0.2857}=1180.8\ \mathrm K
$$

The inlet velocity is not negligible here, so continuity and the SFEE must be solved together. Continuity, with $\rho=p/RT$, gives $V_1=kV_2$ with

$$
k=\frac{\rho_2A_2}{\rho_1A_1}=\frac{p_2T_1}{p_1T_2}\left(\frac{0.2}{0.8}\right)^2=0.0491
$$

The SFEE with no heat or work, $c_pT_1+\tfrac12V_1^2=c_pT_2+\tfrac12V_2^2$, then gives

$$
V_2=\sqrt{\frac{2c_p(T_1-T_2)}{1-k^2}}=\sqrt{\frac{2\times1004.5\times119.2}{1-0.0491^2}}=489.9\ \mathrm{m/s}
$$

with $V_1=24.1$ m/s. The exit density is $\rho_2=10^5/(287\times1180.8)=0.295$ kg/m³, so

$$
\dot m=\rho_2A_2V_2=0.295\times0.0314\times489.9=4.54\ \mathrm{kg/s}
$$

and $Ma_2=V_2/\sqrt{\gamma RT_2}=489.9/688.8=0.711$, subsonic, consistent with a converging nozzle.

### Worked example - two ways to make 25 kN

An engine must give 25 kN at $V_\infty=250$ m/s. Option A accelerates 50 kg/s to 750 m/s; option B accelerates 250 kg/s to 350 m/s. Compare the kinetic energy each adds to the air (suggested example on §13.5).

Both give $T=\dot m(V_j-V_\infty)=25$ kN and the same thrust power $TV_\infty=6.25$ MW. The kinetic energy added per second is

$$
A:\ \tfrac12\times50\times(750^2-250^2)=12.5\ \mathrm{MW},\qquad B:\ \tfrac12\times250\times(350^2-250^2)=7.5\ \mathrm{MW}
$$

so even before any heat is lost in the hot exhaust, A cannot exceed $6.25/12.5=50$ % and B $6.25/7.5=83$ %, the values of $2/(1+V_j/V_\infty)$ at $V_j/V_\infty=3$ and 1.4. The turbofan's large, slow jet wastes far less energy.

---

## Links

- Parent: [[SESA1016 Thermofluids Hub]] · Previous: [[SESA1016 T12 - Conservation of Momentum]] · Next: [[SESA1016 T14 - Boundary Layers and the Origin of Drag]]
- Concepts: [[Steady-flow Energy Equation]] · [[Internal Energy and Enthalpy]] · [[Control-volume Analysis Workflow]] · [[Thermal Efficiency and COP]]
- Worked sheet: [[SESA1016 Problem Sheet 09 - Momentum and Energy Conservation Solutions]] (Q9.7–Q9.11) · Formula list: [[SESA1016 Formula Sheet]]
- Continues in Propulsion: [[SESA2023 W01 - Thrust, Efficiency, Range and the ISA]] (thrust, propulsive and overall efficiency) · [[SESA2023 W02 - Thermodynamics, Mixtures, SFEE and Isentropic Efficiency]] (SFEE station by station) · [[SESA2023 W07 - Turbofan Architectures and Fan Pressure Ratio Selection]]

## Sources

- `Chapter 13.pdf`: lecture notes Chapter 13, Conservation of energy, §§13.1–13.5, Examples 13.1–13.2, Tables 13.1–13.2, Figs 13.1–13.14.
- `SESA1016 Lecture 2025-03-25.txt` (25 Mar 2025): forms of energy (ll. 10–151), flow of energy (ll. 152–219), closed-system rates (ll. 220–336), control-volume statement (ll. 337–435), shaft and flow work (ll. 436–556), total enthalpy and the SFEE (ll. 557–681), which terms matter (ll. 683–773), the three laws together (ll. 774–831).
- `SESA1016 Lecture 2025-03-27.txt` (27 Mar 2025): thrust from momentum (ll. 4–127), two ways to make thrust (ll. 128–154), SFEE for the engine (ll. 155–226), propulsive efficiency (ll. 227–292), turbofans and bypass ratio (ll. 293–374), turbojet components and cycle (ll. 375–525).
- `Problem Sheet 09 - Momentum and Energy Conservation.pdf`: Q9.7–Q9.11, printed answers and the worked solution to Q9.7.

## Self-study tasks

### Core

- [ ] Q9.7, air-water heat exchanger (worked solution). Target 5.97 kg/s. → [[#Worked example - air-water heat exchanger]]
- [ ] Q9.8, heater with a pressure rise and a 10:1 area ratio. Targets 229.75 m/s and 9.19 m/s. → [[#Simplified forms]] · [[SESA1016 Problem Sheet 09 - Momentum and Energy Conservation Solutions]]
- [ ] Q9.9, hair dryer (tutorial problem). Targets 1.197, 1.078 kg/m³, 32 144 J/kg, 0.0218 kg/s, 28.57 m/s, 0.0215 kg/s. → [[#Worked example - hair dryer]]
- [ ] Q9.10, industrial gas turbine. Targets 120.6 m/s, −123.6 MW, 242.5 MW, 204.3 MW, 80.7 MW, 33.3 %. → [[#Worked example - industrial gas turbine]]
- [ ] Q9.11, isentropic nozzle. Targets 4.541 kg/s and 0.711. → [[#Worked example - nozzle expansion]]
- [ ] Rework Example 13.2 for a liquid-cooled GPU with the same profiles (left to you in the notes, Chapter 13, after eq. 13.26). → [[#Worked example - energy leaving a GPU cooler]]

### Further practice

- [ ] Derive the flow work at the two ports and show how it turns $u$ into $h$ in the SFEE (25 Mar, ll. 471–656). → [[#Shaft work and flow work]] · [[#Total enthalpy and the SFEE]]
- [ ] Derive $T=\dot m(V_j-V_\infty)$ and the propulsive efficiency, and explain why turbofans burn less fuel (27 Mar, ll. 54–292). → [[#Thrust from momentum conservation]] · [[#Energy balance and propulsive efficiency]]
- [ ] Write the SFEE for each turbojet component and say which terms vanish (Chapter 13, §13.5.1). → [[#Components of a turbojet]]

## Transcript and slide slips

> [!warning] Lecture-notes slip (Chapter 13, Example 13.1, eq. 13.13)
> Where: [[#Worked example - power available at a dam]].
>
> The maximum power is printed as 1.46 GW, and "about 730 thousand cyclists" follows from it. With the example's own numbers, $\dot m=828.5$ t/s and $\tfrac12V^2=981$ J/kg, the product is 0.813 GW (406 000 cyclists at 2 kW). The comparison with the 1.32 GW installed capacity still holds as an order of magnitude.

> [!warning] Lecture-notes unit slips (Chapter 13, Example 13.2, eqs. 13.17 and 13.26)
> Where: [[#Worked example - energy leaving a GPU cooler]].
>
> $\Delta(\tfrac12V^2)=0.5\times1.2^2$ is written with units of m/s; it is 0.72 J/kg (m²/s²). The energy flow is printed as 438.2 J/kg; it is a power, 438 W.

> [!warning] Lecture-notes slips (Chapter 13, §13.5)
> Where: [[#Energy balance and propulsive efficiency]] · [[#Components of a turbojet]].
>
> After eq. 13.51 the flight power is written $P=DV_j=TV_j$; eq. 13.51 itself, and the lecture (27 Mar, ll. 244–251), use $DV_\infty=TV_\infty$, which is correct. The caption of Fig. 13.12 ("Idealised flow through a turbine") belongs to the burner figure it sits under.

> [!warning] Transcript slips (25 Mar, ll. 609, 624 and 630; 27 Mar, l. 488)
> Where: [[#Total enthalpy and the SFEE]] · [[#Components of a turbojet]].
>
> "By definition of entropy" and "total entropy" are enthalpy and total enthalpy, as the board equations ($u+p/\rho=h$, $h_{tot}$) make clear. On 27 Mar the work collected by the turbine is described as the area $\int p\,dV$ under 4→5 on the $p$–$V$ diagram; for a flow device the shaft work per kilogram is $h_{tot,4}-h_{tot,5}$ from the SFEE, which for a reversible adiabatic turbine equals $-\int v\,dp$, the area to the left of the curve, not under it.
