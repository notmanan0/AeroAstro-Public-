---
title: "SESA1016 T11 - Conservation of Mass"
module: "SESA1016 Thermofluids"
type: topic
stream: "Part D: Control-volume Conservation Laws"
order: 11
tags: [sesa1016, continuity, mass-flow, control-volume]
aliases: ["Continuity", "Mass Conservation"]
date: 2026-09-25
status: lectured
coverage: "Lecture 22 (recorded 19 Mar 2025, ll. 1–429: volume flow rate for uniform, non-uniform and non-perpendicular flow, area-averaged velocity, mass flow rate, the control volume, the continuity equation, steady flow in a duct, no conservation of volume); Chapter 11 in full, with §11.4.2 (multiple ports) and the worked examples from the lecture notes"
parent: ["[[SESA1016 Thermofluids Hub]]"]
prerequisites: ["[[SESA1016 T10 - Euler and Bernoulli Equations]]"]
next_topics: ["[[SESA1016 T12 - Conservation of Momentum]]"]
key_concepts: ["[[Mass Flow Rate]]", "[[Control-volume Analysis Workflow]]", "[[Closed System vs Control Volume]]"]
tutorial_sheets: ["[[SESA1016 Problem Sheet 08 - Bernoulli and Mass Conservation Solutions]]"]
sources: ["02 - Sources/Lectures/Chapter 11.pdf", "02 - Sources/Lectures/SESA1016 Lecture 22.txt", "02 - Sources/Tutorial Sheets/Problem Sheet 08 - The Bernoulli Equation and Mass Conservation.pdf"]
---

# SESA1016 T11 - Conservation of Mass

> [!abstract] Summary
> The volume flow rate through a surface is the integral of the normal velocity over it, $\dot{\mathcal V}=\int_A\vec V\cdot\vec n\,dA$, which for any profile equals the area-averaged velocity times the area; the mass flow rate weights it by density, $\dot m=\int_A\rho\vec V\cdot\vec n\,dA$, reducing to $\rho VA$ for uniform flow. Applied to a fixed control volume with outward normal $\vec n$, conservation of mass says the rate of accumulation inside plus the net outflow through the surface is zero. For steady flow in a duct this gives $\dot m_1=\dot m_2$, or $\rho_1V_1A_1=\rho_2V_2A_2$; mass flow is conserved, volume flow only when the density is constant.

> [!summary]- Exam use: quick path
> - **Use it when:** a velocity, area or density is unknown at one section of a duct, nozzle, junction or tank and known elsewhere; or a flow rate must be found from a velocity profile.
> - **Assumptions:** fixed control volume; steady flow unless a level or mass inside changes; uniform $\rho$ and $V$ over each port unless a profile is given.
> - **Method:** 1. Draw the control volume, cutting the flow at right angles where it is known or wanted, and mark $\vec n$ outwards. 2. Decide whether mass accumulates inside (a tank filling) or not (steady). 3. Write $\dot m=\rho\bar VA$ for each port, or integrate $\rho V$ over a non-uniform port. 4. Set $\sum\dot m_{out}-\sum\dot m_{in}=-dm_{CV}/dt$. 5. Solve, and use $\rho=p/RT$ if a gas is heated or compressed.
> - **Common mistakes:** equating volume flow rates for a gas whose density changes; using the maximum velocity of a profile instead of its mean.
> - **Practise:** [[#Worked example - industrial heater]] · [[SESA1016 Problem Sheet 08 - Bernoulli and Mass Conservation Solutions]] Q8.4–Q8.6, Q8.10

Measuring how much water comes out of a tap is easy: time how long it takes to fill a bucket. Doing it inside a pipe, where the flow is faster in the middle than at the walls, or through a vent where it leaves at an angle, needs a little more care. The area is cut into small pieces, the flow through each is taken, and the contributions are added up; in the limit this sum is the flow-rate integral. Only the velocity across a surface carries fluid through it; flow sliding along the surface carries none.

A fixed lump of gas in a cylinder is a Lagrangian, closed-system view. In a jet engine, a nozzle or a radiator duct the fluid is continuously replaced, and following each particle is hopeless. A fixed box (a control volume) is drawn round the device instead, and what crosses its surface is tallied. Mass is the first quantity tallied; momentum and energy ([[SESA1016 T12 - Conservation of Momentum|T12]], [[SESA1016 T13 - Conservation of Energy and Propulsion|T13]]) are treated in the same way.

The answer for a steady duct is short: whatever enters each second must leave each second, so the mass flow rate is the same at every section. If five tonnes of oil per hour go into one end of a pipeline, five tonnes per hour come out of the other, whatever has happened to the velocity and density along the way.

---

## 1. Volume flow rate

### Uniform flow

The **volume flow rate** $\dot{\mathcal V}$ is the volume of fluid crossing a surface per unit time, in m³/s (1 m³ = 1000 litres). The dot borrows Newton's notation for a rate.

In uniform flow at speed $V$ through a duct of cross-section $A$, the fluid that was at the section moves on by $dx=V\,dt$ in a short time $dt$, so the volume that has crossed is a slab of length $dx$:

$$
d\mathcal V=A\,dx=AV\,dt
$$

Dividing by $dt$:

$$
\boxed{\dot{\mathcal V}=VA}
$$

valid whenever the velocity is uniform over the section. It grows with both the area and the velocity, as it should.

### Non-uniform flow

In a pipe the velocity is zero at the wall (no-slip) and largest on the axis, with a laminar or turbulent profile ([[SESA1016 T15 - Flow in Conduits|T15]]). Divide the section into small elements $dA$, over each of which the local velocity $V$ is effectively uniform. Through one element the flow rate is

$$
d\dot{\mathcal V}=V\,dA
$$

using the local velocity, and the total is the sum of all of them:

$$
\boxed{\dot{\mathcal V}=\int_AV\,dA}
$$

### The area-averaged velocity

It is convenient to have a single velocity that, multiplied by the area, gives the right flow rate even for a non-uniform profile. Solve $\dot{\mathcal V}=\bar VA$ for $\bar V$:

$$
\boxed{\bar V=\frac{1}{A}\int_AV\,dA}
$$

the **area-averaged** or **mean velocity**, which is just the general definition of the average of a function, integrated and divided by the size of the region. Multiplying and dividing $\int_AV\,dA$ by $A$ then gives

$$
\dot{\mathcal V}=A\left(\frac1A\int_AV\,dA\right)=\bar VA
$$

for any profile. A laminar and a turbulent profile in the same pipe look very different, but if their mean velocities are equal, so are their flow rates. For the parabolic laminar profile in a round pipe, $V=V_{max}(1-r^2/R^2)$, the mean is exactly $V_{max}/2$.

![[tf_flow_rate_profiles.png|900]]

### Flow at an angle to the surface

If the flow leaves a vent at an angle $\theta$ to the unit normal $\vec n$ of the outlet surface, split the local velocity into a tangential component $V_t$, along the surface, and a normal component $V_n$, across it. The tangential component carries no fluid through the surface; only $V_n$ does. It is given by the dot product,

$$
V_n=\vec V\cdot\vec n=|\vec V||\vec n|\cos\theta=|\vec V|\cos\theta
$$

since $|\vec n|=1$. In time $dt$ the fluid crossing an element $dA$ fills a slanted slab of volume $dA\,V_n\,dt$, so

$$
\boxed{\dot{\mathcal V}=\int_A\vec V\cdot\vec n\,dA}
$$

the most general form. The earlier results are special cases: perpendicular flow ($\vec V\cdot\vec n=V$) and uniform flow ($V$ out of the integral).

## 2. Mass flow rate

The **mass flow rate** $\dot m$ is the mass crossing a surface per unit time, in kg/s. The volume $dA\,V_n\,dt$ crossing an element in time $dt$ has mass

$$
dm=\rho\,dA\,V_n\,dt
$$

where $\rho$ is the local density, which may vary across the surface. Divide by $dt$ and sum over the surface:

$$
\boxed{\dot m=\int_A\rho\,\vec V\cdot\vec n\,dA}
$$

This is the formula to remember, together with its special cases. For flow perpendicular to the surface, $\vec V\cdot\vec n=V$, so $\dot m=\int_A\rho V\,dA$, which is still an integral if $\rho$ or $V$ varies. At constant density (incompressible flow), $\rho$ comes outside: $\dot m=\rho\int_AV\,dA=\rho\bar VA=\rho\dot{\mathcal V}$. For uniform flow, $\rho$ and $V$ both come out, and

$$
\boxed{\dot m=\rho VA}
$$

the form used most often.

## 3. The control volume

A **control volume** (CV) is an imaginary region of space with a definite boundary, the **control surface** (CS). It encloses the device being studied (a nozzle, intake, pump, combustor or electric heater) and can have any shape; good choices make the problem easy, bad ones make it hard. In this module it is fixed in space, which makes it an Eulerian idea. Unlike the boundary of a closed system, the control surface is permeable: fluid crosses it freely, so the fluid inside keeps changing, and the analysis tracks the mass, momentum and energy crossing the boundary rather than any particular fluid.

At every point of the control surface the unit normal $\vec n$ points **outwards**. This fixes the signs: at an outflow $\vec V$ and $\vec n$ point the same way, the angle between them is under 90° and $\vec V\cdot\vec n>0$; at an inflow the angle exceeds 90° and $\vec V\cdot\vec n<0$. So in every conservation law in this module, **outflows count positive and inflows negative**.

![[tf_cv_normal_sign.png|900]]

Two examples show the idea. A tank refilled from the top while it drains through a side hole is enclosed by a control volume round the tank, and the problem becomes the rates of mass in and out through its surface. The sidepod of a Formula 1 car, with air entering at the intake, passing through the radiator and leaving at the rear, is enclosed by a control volume following the sidepod walls; mass crosses only at the intake and outlet, and the heat from the radiator crosses as $\dot Q$. The same box also accounts for momentum and energy.

## 4. Conservation of mass

### Closed system and control volume

For a closed system the mass is fixed:

$$
\frac{d(m_{system})}{dt}=0
$$

For a control volume, in words:

$$
0=\{\text{rate of change of mass inside the CV}\}+\{\text{net rate of mass flow out through the CS}\}
$$

The first term is the **accumulation** term: the mass inside may increase (a glass being filled), decrease or stay constant. The second is the **net outflow**, summed over every part of the surface with the sign convention above. Both have units of kg/s.

The mass inside is the sum of the masses of its volume elements, each with its own density:

$$
m_{CV}=\int_{CV}\rho\,d\mathcal V
$$

and the net outflow is the mass flow rate over the whole control surface, with $\vec V\cdot\vec n$ carrying the sign. So

$$
\boxed{0=\frac{d}{dt}\int_{CV}\rho\,d\mathcal V+\int_{CS}\rho\,\vec V\cdot\vec n\,dA}
$$

the general form of the **continuity equation**.

### Steady flow in a duct

If the flow is steady, the density and velocity at each point do not change, so the mass inside the control volume is constant (different fluid at different times, but the same amount) and the accumulation term vanishes:

$$
\int_{CS}\rho\,\vec V\cdot\vec n\,dA=0
$$

Whatever enters each second leaves each second. This also holds for a liquid that completely fills a pipe or channel.

Apply it to a duct whose area changes from $A_1$ at the inlet to $A_2$ at the outlet, with a control volume whose end faces lie across sections 1 and 2 and whose sides follow the walls. Nothing crosses the walls, so only the two ends contribute:

$$
\int_{A_1}\rho_1\vec V_1\cdot\vec n\,dA+\int_{A_2}\rho_2\vec V_2\cdot\vec n\,dA=0
$$

At the inlet the flow enters, $\vec V_1\cdot\vec n=-V_1$; at the outlet it leaves, $\vec V_2\cdot\vec n=+V_2$:

$$
-\int_{A_1}\rho_1V_1\,dA+\int_{A_2}\rho_2V_2\,dA=0
$$

Each integral is the mass flow rate through that section, so

$$
\boxed{\dot m_1=\dot m_2}
$$

and for uniform flow at each section,

$$
\boxed{\rho_1V_1A_1=\rho_2V_2A_2}
$$

the **pipe-flow form** of the continuity equation. Sections 1 and 2 were arbitrary, so the mass flow rate is the same at every section of the duct.

### Mass is conserved, volume is not

The statement $\dot{\mathcal V}_1=\dot{\mathcal V}_2$, or $V_1A_1=V_2A_2$, is in general false: if the fluid is heated or compressed between the two sections its density changes, and the same mass then occupies a different volume. Only when $\rho_1=\rho_2$, in incompressible flow, does continuity reduce to equal volume flow rates. Remember $\dot m_1=\dot m_2$ and derive the volume form when it applies. This is the result that makes streamtubes behave as virtual pipes in [[SESA1016 T9 - Describing Flow and the Material Derivative#Streamtubes|T9]]: in incompressible flow the speed varies inversely with the streamtube's area.

### Several inlets and outlets

A device with more than one port, such as two inlets and one outlet, gives one term per port in the surface integral. With inflows negative and outflows positive, the steady-flow continuity equation becomes

$$
\boxed{\sum\dot m_{out}-\sum\dot m_{in}=0}
$$

and if mass accumulates, $\sum\dot m_{in}-\sum\dot m_{out}=dm_{CV}/dt$.

---

## Worked examples

### Worked example - triangular velocity profile

Flow in a channel of depth $h$ and width $w$ has the linear profile $v(y)=Vy/h$. Find the volume flow rate (Chapter 11, Example 11.1).

A strip of height $dy$ across the width has area $dA=w\,dy$, and the flow through it is $d\dot{\mathcal V}=(Vy/h)w\,dy$. Integrating over the depth:

$$
\dot{\mathcal V}=\int_0^h\frac{Vy}{h}w\,dy=\frac{wV}{h}\cdot\frac{h^2}{2}=\frac{wVh}{2}
$$

Quicker: the mean of a triangle rising from 0 to $V$ is $V/2$, and $\dot{\mathcal V}=\bar VA=(V/2)(wh)$.

### Worked example - half-uniform, half-linear profile

The velocity is $V/2$ in the bottom half of a channel of depth $h$ and width $w$, and rises linearly from $V/2$ to $V$ in the top half. Find the volume flow rate (Chapter 11, Example 11.2).

The mean over the bottom half is $V/2$ (a rectangle). Over the top half the profile is a trapezium, with mean $(V/2+V)/2=3V/4$. The two halves have equal area, so the overall mean is

$$
\bar V=\tfrac12\left(\frac V2+\frac{3V}{4}\right)=\frac{5V}{8}
$$

$$
\dot{\mathcal V}=\frac{5}{8}Vwh
$$

> [!check] Numerical integration
> Integrating the profile numerically on a fine grid gives a mean of $0.625V$, which is $5V/8$.

### Worked example - stratified channel

A channel 0.6 m wide carries a layer of salt water ($\rho_s=1030$ kg/m³, 0.34 m deep) under a layer of fresh water ($\rho_f=1000$ kg/m³, 0.12 m deep), both at 1.2 m/s. Find the volume and mass flow rates (Chapter 11, Example 11.3).

The velocity is uniform, so

$$
\dot{\mathcal V}=V(h_f+h_s)w=1.2\times0.46\times0.6=0.3312\ \mathrm{m^3/s}
$$

The density is not uniform, so $\dot m=\rho VA$ cannot be used for the whole section. It is uniform within each layer, so the integral splits into two pieces:

$$
\dot m_f=\rho_fVh_fw=1000\times1.2\times0.12\times0.6=86.4\ \mathrm{kg/s}
$$

$$
\dot m_s=\rho_sVh_sw=1030\times1.2\times0.34\times0.6=252.1\ \mathrm{kg/s}
$$

$$
\dot m=338.5\ \mathrm{kg/s}
$$

### Worked example - filling tank

A tank of cross-section $A$ is filled at $\dot m_{in}$ and drains at $\dot m_{out}$. Find the rate at which the level $h$ changes (Chapter 11, Example 11.4).

Draw the control volume round the tank. The water has constant density, so the mass inside is

$$
m_{CV}=\int_{CV}\rho\,d\mathcal V=\rho Ah
$$

and its rate of change is $\rho A\,dh/dt$. The net inflow is $\dot m_{in}-\dot m_{out}$, so

$$
\rho A\frac{dh}{dt}=\dot m_{in}-\dot m_{out}
$$

For a 1 m² tank of water filled at 2 kg/s and drained at 1.5 kg/s, $dh/dt=0.5/1000=0.5$ mm/s.

### Worked example - industrial heater

An industrial heater consists of a 120 cm diameter pipe followed by a 60 cm pipe. A heating element raises the air from 21 °C at inlet 1 to 140 °C at outlet 2, both at 101 325 Pa. The mean inlet velocity is 2 m/s. Find the outlet velocity with the heater on and off (Problem Sheet 8, Q8.5, the tutorial problem).

Steady flow, so $\rho_1V_1A_1=\rho_2V_2A_2$:

$$
V_2=V_1\frac{A_1}{A_2}\frac{\rho_1}{\rho_2}
$$

The area ratio is $(120/60)^2=4$. At equal pressure the ideal-gas law gives $\rho_1/\rho_2=T_2/T_1$. With the heater on:

$$
V_2=2\times4\times\frac{413.15}{294.15}=11.24\ \mathrm{m/s}
$$

With it off, $\rho_1=\rho_2$ and $V_2=2\times4=8.0$ m/s. Heating makes the air less dense, so the same mass flow ($\dot m=\rho_1V_1A_1=2.71$ kg/s) needs 40 % more speed. Equating volume flow rates would have missed this.

### Worked example - numerical mass flow in an intercooler

Air in an intercooler channel 2.5 cm high and 9.7 cm wide, at 3.4 bar, has the measured profiles below; the flow is 2D. Compute $\dot m=\int_A\rho V\,dA$ with the trapezoidal rule (Problem Sheet 8, Q8.10).

| $y$ (cm) | 0 | 0.4 | 0.8 | 1.2 | 1.7 | 2.1 | 2.5 |
|---|---|---|---|---|---|---|---|
| $T$ (K) | 572 | 532 | 494 | 455 | 415 | 376 | 337 |
| $V$ (m/s) | 0 | 39 | 61 | 74 | 67 | 38 | 0 |
| $\rho=p/RT$ (kg/m³) | 2.071 | 2.227 | 2.398 | 2.604 | 2.855 | 3.151 | 3.515 |
| $\rho V$ (kg m⁻² s⁻¹) | 0 | 86.9 | 146.3 | 192.7 | 191.3 | 119.7 | 0 |

With no variation across the width, $dA=b\,dy$ and $\dot m=b\int_0^H\rho V\,dy$. The trapezoidal rule on the unevenly spaced points (`numpy.trapezoid(rho*V, y)`) gives $\int\rho V\,dy=3.139$ kg m⁻¹ s⁻¹, so

$$
\dot m=0.097\times3.139=0.304\ \mathrm{kg/s}
$$

The density varies by 70 % across the channel, so it must stay inside the integral; using the mean density times the volume flow rate gives 0.309 kg/s, 1.6 % high.

![[tf_q8_10_intercooler.png|900]]

### Worked example - tee junction

Water enters a tee at A (4 m diameter, 6 m/s); a 2 m branch C leaves at 2 m/s; the rest leaves through B (4 m diameter). Find the mean velocity in B (Problem Sheet 8, Q8.4).

Steady, incompressible, one inlet and two outlets:

$$
\rho V_AA_A=\rho V_BA_B+\rho V_CA_C
$$

$$
V_B=\frac{V_AA_A-V_CA_C}{A_B}=6-2\times\left(\frac{2}{4}\right)^2=5.5\ \mathrm{m/s}
$$

### Worked example - water cannon

A piston of diameter $D=10$ cm pushes water at 1.8 m/s out of a nozzle of diameter $d=5$ cm. Find the jet speed and the piston force, for inviscid flow without friction (Problem Sheet 8, Q8.6).

Continuity: $V_jd^2=V_pD^2$, so

$$
V_j=1.8\times\left(\frac{10}{5}\right)^2=7.2\ \mathrm{m/s}
$$

Bernoulli from the cylinder to the jet at $p_{atm}$ (steady, since the piston speed is constant) gives the gauge pressure in the cylinder:

$$
p_g=\tfrac12\rho(V_j^2-V_p^2)=\tfrac12\times1000\times(7.2^2-1.8^2)=24.3\ \mathrm{kPa}
$$

$$
F=p_g\frac{\pi D^2}{4}=24\,300\times\frac{\pi\times0.1^2}{4}=191\ \mathrm N
$$

---

## Links

- Parent: [[SESA1016 Thermofluids Hub]] · Previous: [[SESA1016 T10 - Euler and Bernoulli Equations]] · Next: [[SESA1016 T12 - Conservation of Momentum]]
- Concepts: [[Mass Flow Rate]] · [[Control-volume Analysis Workflow]] · [[Closed System vs Control Volume]]
- Worked sheet: [[SESA1016 Problem Sheet 08 - Bernoulli and Mass Conservation Solutions]] (Q8.4–Q8.6, Q8.9–Q8.11) · Formula list: [[SESA1016 Formula Sheet]]
- Used again in: [[SESA1016 T12 - Conservation of Momentum|T12]] and [[SESA1016 T13 - Conservation of Energy and Propulsion|T13]] (same control-volume bookkeeping) · [[SESA2023 W03 - Compressible Flow, Normal Shocks and Nozzles]] (continuity with varying density in nozzles)

## Sources

- `Chapter 11.pdf`: lecture notes Chapter 11, Conservation of mass, §§11.1–11.4, Examples 11.1–11.4, Figs 11.1–11.9.
- `SESA1016 Lecture 22.txt` (recorded lecture, 19 Mar 2025, cited as L22): volume flow rate (ll. 7–136), mass flow rate (ll. 137–188), the control volume (ll. 189–241), conservation of mass and the sign of $\vec V\cdot\vec n$ (ll. 242–334), steady duct flow (ll. 335–415), no conservation of volume (ll. 416–428).
- `Problem Sheet 08 - The Bernoulli Equation and Mass Conservation.pdf`: Q8.4–Q8.6, Q8.9–Q8.11, printed answers.

## Self-study tasks

### Core

- [ ] Example 11.2, flow rate for a half-uniform, half-linear profile (left to the reader in the notes). Target $5Vwh/8$. → [[#Worked example - half-uniform, half-linear profile]]
- [ ] Q8.4, tee junction. Target 5.5 m/s. → [[#Worked example - tee junction]]
- [ ] Q8.5, industrial heater (tutorial problem). Targets 11.24 m/s and 8 m/s. → [[#Worked example - industrial heater]]
- [ ] Q8.6, water cannon. Targets 7.2 m/s and 191 N. → [[#Worked example - water cannon]]
- [ ] Q8.9, mass flow rate through a constriction from $p_1-p_2$ (Venturi meter), with assumptions. → [[#Steady flow in a duct]] · [[SESA1016 Problem Sheet 08 - Bernoulli and Mass Conservation Solutions]]
- [ ] Q8.10, intercooler mass flow by the trapezoidal rule. Target 0.30 kg/s. → [[#Worked example - numerical mass flow in an intercooler]]
- [ ] Q8.11, three pistons on a hydraulic housing. Answer: C moves up. → [[#Several inlets and outlets]] · [[SESA1016 Problem Sheet 08 - Bernoulli and Mass Conservation Solutions]]

### Further practice

- [ ] Derive $\dot m_1=\dot m_2$ from the general continuity equation for a steady duct, keeping track of the sign of $\vec V\cdot\vec n$ (L22, ll. 335–415). → [[#Steady flow in a duct]]
- [ ] Show that the mean velocity of a parabolic pipe profile is half its maximum (suggested, not lecturer-set). → [[#The area-averaged velocity]]
- [ ] Explain when $V_1A_1=V_2A_2$ is valid and give an example where it fails (L22, ll. 416–427). → [[#Mass is conserved, volume is not]]

## Transcript and slide slips

> [!warning] Lecture-notes slips (Chapter 11, §§11.1.2, 11.3 and 11.4)
> Where: [[#Non-uniform flow]] · [[#3. The control volume]] · [[#Closed system and control volume]].
>
> Eq. 11.5 ends with a stray "/" after $\int_AV\,dA$. In §11.3 the sentence "In many engineering applications, however, this Lagrangian concept is not powerful enough…" is printed twice across the page break. After eq. 11.26 the net flow through the boundary is said to be positive "if the inlet mass flow rate is larger than the outlet flow rate"; eq. 11.26 defines it as the net flow **out**, which is positive when the outlet flow is larger, consistent with the sign convention of eq. 11.28.

> [!warning] Lecture-notes slip (Chapter 11, §11.4.1, after eq. 11.37)
> Where: [[#Steady flow in a duct]].
>
> "It can also be expressed more concisely as which is always valid" is missing its equation; from the context it is $\dot m=$ const along the duct, i.e. eq. 11.36.
