---
title: "SESA2024 07 - Spacecraft Propulsion"
module: "SESA2024 Astronautics"
type: topic
stream: "Spacecraft Subsystems"
order: 7
tags: [sesa2024, propulsion, specific-impulse, electric-propulsion, rocket-equation]
aliases: ["Propulsion subsystem", "Chapter 7"]
date: 2026-10-30
status: lectured
coverage: "Week 3 (pre-recorded Chapter 7 lecture; 2025-10-16, ll. 276–700)"
parent: ["[[SESA2024 Astronautics Hub]]"]
prerequisites: ["[[SESA2024 06 - Attitude Control]]"]
next_topics: ["[[SESA2024 02 - Kepler's Laws and the Orbit Equation]]", "[[SESA2024 08 - Electrical Power Subsystem]]"]
key_concepts: ["[[Tsiolkovsky Rocket Equation]]", "[[Rocket Performance Parameters]]", "[[Thrust Equation]]", "[[Chemical Propulsion Systems]]", "[[Electric Propulsion Sizing]]"]
tutorial_sheets: ["[[SESA2024 Workbook Ch7 - Propulsion Solutions]]"]
sources: ["02 - Sources/Lectures/Chapter 7/Chapter 7 - Propulsion - original slides(1)(1).pdf", "02 - Sources/Lectures/Chapter 7/2025 WEEK 3 Lecture 2 - Chapter 7 - Propulsion - complete.pdf", "02 - Sources/Lectures/SESA2024 Lecture Chapter 7 - Propulsion - prerecorded material.txt", "02 - Sources/Lectures/SESA2024 Lecture 2025-10-16.txt", "02 - Sources/Lectures/SESA2024 Lecture 2025-10-28 - Quiz 1 Worked Solutions - Drop In session.txt"]
---

# SESA2024 07 - Spacecraft Propulsion

> [!abstract] Summary
> A rocket pushes the spacecraft forward by throwing propellant backward, and its thrust is the mass flow rate times the exhaust velocity, plus a pressure term when it fires in an atmosphere. Specific impulse $I_{sp}=V_{ex}/g_0$ measures how efficiently propellant becomes momentum, and through the rocket equation it sets the propellant mass for a given ΔV. Chemical systems give high thrust at $I_{sp}$ of a few hundred seconds; electric systems give tiny thrust at thousands of seconds, but their power plant mass grows with $V_{ex}^2$, so their exhaust velocity has an optimum near the characteristic velocity $V_c=\sqrt{2\eta\beta t_b}$.

> [!summary]- Exam use: quick path
> - **Use it when:** you need thrust, specific impulse, propellant mass for a ΔV, the electrical power for an EP thruster, or a choice between propulsion types.
> - **Assumptions:** exhaust velocity lumps in the pressure thrust (vacuum, or ideally expanded); no gravity or drag losses in the rocket equation; constant mass flow rate over an EP burn.
> - **Method:** 1. $V_{ex}=g_0I_{sp}$ with $g_0=9.81\ \mathrm{m/s^2}$. 2. Propellant: $M_e/M_0=1-e^{-\Delta V/V_{ex}}$. 3. Thrust and flow: $T=\dot m V_{ex}$. 4. EP power: $W=TV_{ex}/(2\eta)$. 5. EP sizing: from the payload fraction read the optimum $V_{ex}/V_c$ and $\Delta V/V_c$, then $V_c$, $\beta=V_c^2/(2\eta t_b)$, $M_e=(M_0-M_p)/(1+x^2)$, $M_W=x^2M_e$.
> - **Common mistakes:** thinking high $I_{sp}$ means high thrust; dividing total impulse by propellant mass instead of propellant weight when finding $I_{sp}$ (Quiz 1).
> - **Practise:** [[#Power for a 50 mN thruster]] · [[SESA2024 Workbook Ch7 - Propulsion Solutions#Q12. Pluto orbiter by electric propulsion|Workbook Q12, the Pluto orbiter]]

Every spacecraft propulsion system works by momentum transfer: "effectively we're trying to throw out mass as efficiently as possible behind us and that's what pushes us forwards" (2025-10-16, ll. 326–340). Two numbers describe how well it does that. The thrust says how hard it pushes, and so how quickly a manoeuvre is done. The specific impulse says how much push you get from each kilogram of propellant, and so how much propellant a manoeuvre costs. Chemical rockets are good at the first, electric thrusters at the second, and the trade between them runs through the rest of the module, from the Hohmann transfer to station-keeping against drag.

The type of propulsion available also limits what missions are possible at all: "the type of propulsion that we have available to us is what dictates what it is that we can do in terms of in our solar system" (ll. 326–335). Dr Sykulska-Lawrence treated this chapter as an overview; SESA2023 Propulsion covers the engines in depth.

## 1. Types of propulsion

The slides classify propulsion first by principle (2025-10-16, ll. 300–330): rockets (thermal, electric or nuclear, and thermal rockets subdivided into chemical, nuclear, solar and laser heating), photon ejection, solar sails using the momentum of sunlight, and technologies not yet developed. In practice spacecraft use chemical rockets and, increasingly, electric propulsion.

They are also classified by job (ll. 335–425):

- Primary propulsion is the high-thrust kind: launch vehicles and spacecraft orbit transfers, with thrust from hundreds of newtons upwards and burns of roughly 100–500 s. A burn of a minute or more still counts as impulsive because it is short compared with the orbital period. An electric thruster doing the same manoeuvre would burn for hours or longer.
- Secondary propulsion is attitude and orbit control: thrust from millinewtons to about 10 N, short and often pulsed burns.

| Type | Thrust | Burn | Use | Development |
|---|---|---|---|---|
| Chemical liquid | very high | seconds to minutes | primary and secondary | very well developed |
| Chemical solid | very high | seconds to minutes | primary | very well developed |
| Chemical hybrid | high | seconds to minutes | primary | flown, maturing |
| Electric | very low | hours to years | mainly secondary, some primary (BepiColombo) | flown widely |
| Nuclear thermal | high | minutes to hours | primary | NERVA cancelled in 1973 |
| Solar sail | very low | continuous | primary and secondary | experimental |

## 2. Thrust, impulse and specific impulse

### The thrust equation

The pre-recorded lecture recalls the Year 1 momentum analysis of a rocket (ll. 1–25). Over a short time $dt$ the rocket ejects mass $dm_e$ at exhaust velocity $V_{ex}$ relative to itself. Applying Newton's second law to the rocket and its exhaust and taking the limit gives the momentum thrust

$$
T=\dot m\,V_{ex},
$$

where $\dot m$ is the propellant mass flow rate (the slides also write it $\sigma$). When the engine fires in an atmosphere, the exhaust leaves at pressure $p_e$ over the exit area $A_e$ while the ambient pressure is $p_a$, which adds a pressure thrust:

$$
T=\dot m\,V_{ex}+(p_e-p_a)A_e.
$$

If $p_a>p_e$ the nozzle is over-expanded and the pressure thrust is negative; the Shuttle lost about 20 % of its thrust this way at sea level. If $p_e>p_a$ it is under-expanded: the pressure term is positive, but less of the exhaust's energy has gone into velocity, so the net effect is still a loss. The ideal is $p_e=p_a$, which a launcher cannot hold as it climbs (ll. 1–35). For the rest of the chapter the pressure term is lumped into an effective exhaust velocity, which is exact in a vacuum with the right nozzle.

### Total impulse

Real thrust rises, wobbles and falls rather than switching on and off, so what matters is the area under the thrust–time curve, the total impulse (ll. 26–70):

$$
I=\int_0^{t_b}T\,dt.
$$

Substitute $T=\dot mV_{ex}$ and $\dot m=-dM/dt$, where $M$ is the rocket's mass:

$$
I=\int_0^{t_b}-\frac{dM}{dt}V_{ex}\,dt=-V_{ex}\int_{M_0}^{M_b}dM.
$$

So

$$
I=V_{ex}(M_0-M_b)=M_eV_{ex},
$$

where $M_e=M_0-M_b$ is the propellant mass. Propulsion engineers use subscript $e$ for expellant.

### Specific impulse

Specific impulse is the impulse per unit weight of propellant (ll. 51–100):

$$
I_{sp}=\frac{I}{M_eg_0}=\frac{M_eV_{ex}}{M_eg_0}=\frac{V_{ex}}{g_0},
$$

with $g_0=9.81\ \mathrm{m/s^2}$. It has units of seconds. Equivalently, it is thrust divided by the weight flow rate:

$$
I_{sp}=\frac{T}{\dot m g_0}.
$$

The Quiz 1 walk-through stressed the weight: a true-or-false question defining it per unit mass was false (ll. 1–25, 51–80).

> [!warning] Transcript slip (2025-10-16, l. 497)
> The recap says "the exhaust velocity is equal to this specific impulse". It is $V_{ex}=g_0I_{sp}$; the two differ by the factor 9.81.

High specific impulse does not mean high thrust. Electric thrusters reach thousands of seconds with millinewtons of thrust; chemical engines reach 300–450 s and get their high thrust from a high mass flow rate (ll. 76–100; 2025-10-16, ll. 500–520). The textbook relates specific impulse to the chemistry: it rises with the combustion chamber temperature and falls with the mean molecular weight of the exhaust, roughly $I_{sp}\propto\sqrt{T_c/\bar M}$, which is why hydrogen fuels score well.

### The rocket equation and propellant mass

With no gravity or drag losses, the rocket equation from Year 1 is

$$
\Delta V=V_{ex}\ln\frac{M_0}{M_b}=g_0I_{sp}\ln\frac{M_0}{M_0-M_e}.
$$

Invert it for the propellant fraction (pre-recorded lecture, ll. 101–125):

$$
\frac{M_0}{M_0-M_e}=e^{\Delta V/V_{ex}}
\quad\Longrightarrow\quad
\boxed{\frac{M_e}{M_0}=1-e^{-\Delta V/V_{ex}}}
$$

As $\Delta V/V_{ex}$ grows the fraction approaches 1 asymptotically, because a rocket cannot be made entirely of propellant. This is how chemical systems are sized: the mission analysis gives ΔV, the propellant choice gives $I_{sp}$, and the equation gives the propellant mass.

![[ast_rocket_equation.png|650]]

## 3. Chemical propulsion

### Liquid monopropellants

A single liquid is decomposed exothermically on a catalyst bed and expanded through a nozzle (pre-recorded lecture, ll. 126–170). Hydrazine is the standard: it decomposes into ammonia, nitrogen and hydrogen. An optional electric heater raises the specific impulse from about 240 s to about 290 s at the cost of power. Thrust is 1–10 N, so monopropellants are used for secondary propulsion (attitude control thrusters), not primary. Hydrazine is carcinogenic, and there is a move to "green" propellants, but the industry's handling procedures are built around hydrazine and its performance is hard to match.

### Liquid bipropellants

A fuel and an oxidiser meet in a combustion chamber (ll. 170–205). Hydrogen with oxygen, or with fluorine for about 410 s, gives the highest performance, but both oxidisers are cryogenic (boiling points about 90 K and 85 K) and fluorine is highly corrosive. Hypergolic pairs ignite on contact with no spark, so they must never meet before they are wanted. Monomethylhydrazine with nitrogen tetroxide is hypergolic and storable (boiling point about 294 K), which makes it the usual choice for spacecraft. A bipropellant system needs a pressurant (helium), separate fuel and oxidiser tanks, and two feed lines to every thruster: with twelve attitude thrusters, redundant spares and a main engine, the plumbing gets complicated. Thrust is 1–400 N and specific impulse a little over 300 s.

A spacecraft dropped in its final low orbit by the launcher may need no primary engine at all. A GEO satellite is dropped in GTO and needs its own engine to circularise (ll. 201–215).

### Solids

A solid motor is a firework: once ignited it burns to completion and cannot be stopped (ll. 201–250). The propellant is cast like dough, and the grain geometry sets the thrust curve: burning from the end like a cigarette gives constant thrust, a star-shaped bore gives high thrust that falls, and burning from the inside out gives rising thrust. Solids give high thrust from a high mass flow rate and a smooth start, which suits first stages (the Shuttle and SLS boosters, built from stacked segments burning outwards from the bore). A small solid motor can serve as a satellite's one-shot apogee motor, removing the need for bipropellant feed lines; the lecture's example gives 60 kN for tens of seconds at just under 300 s. Workbook Q9 asks why solids are not used for attitude control.

### Hybrids and cold gas

A hybrid keeps one component solid and the other liquid, easing storage while keeping some throttle and restart ability; they have matured over the last 10–15 years (ll. 251–260). A cold-gas thruster simply releases stored inert gas: low thrust and finite, but clean, with no contaminating exhaust near delicate sensors, which suits fine pointing (ll. 251–275).

### Two architectures for a GEO spacecraft

| Monopropellant with a solid apogee motor | Bipropellant (unified) system |
|---|---|
| simpler: one feed line per thruster | two feed lines everywhere |
| easier storage and handling | more hazardous handling |
| better structure-to-mass ratio | worse dry-to-wet ratio |
| lower overall $I_{sp}$ | higher $I_{sp}$ |
| apogee motor cannot be throttled or restarted | throttle and restart |

Both are flown; the choice depends on the mission drivers (pre-recorded lecture, ll. 276–300).

## 4. Electric propulsion

### The thruster types

Electric propulsion (EP) uses electrical power to accelerate the propellant (2025-10-16, ll. 526–660). The three classes are:

- Electrothermal: the propellant is heated and expanded through a nozzle. A resistojet heats it with a resistive element to about 1600–2500 °C, giving 5 mN to 0.5 N at up to about 700 s with an efficiency of about 0.9; it is simple and cheap and Surrey Satellite Technology uses it on small satellites, with propellants such as xenon, water or butane. An arcjet heats the propellant with an electric arc between anode and cathode, giving 0.5–5 N at 450–1500 s, but the hundreds of amps erode the electrodes, and the efficiency is only about 0.3.
- Electromagnetic: crossed electric and magnetic fields give a Lorentz force that accelerates a plasma. High accelerations, but short lifetimes, so rarely used.
- Electrostatic: the gridded ion thruster ionises the propellant, accelerates the positive ions through a grid potential, and fires electrons from a neutraliser so the spacecraft does not charge up. It is the most propellant-efficient and is used for GEO station-keeping and deep space (Deep Space 1, BepiColombo's twin thrusters). Its life is limited by grid erosion and the neutraliser cathode.

### Power for a given thrust

The power in the exhaust jet is its kinetic energy flow:

$$
W_{jet}=\tfrac12\dot mV_{ex}^2.
$$

Since $T=\dot mV_{ex}$, this is $W_{jet}=\tfrac12TV_{ex}$. The electrical power needed, with conversion efficiency $\eta$, is

$$
W=\frac{W_{jet}}{\eta}=\frac{TV_{ex}}{2\eta}=\frac{Tg_0I_{sp}}{2\eta}.
$$

For a fixed thrust, power rises in proportion to specific impulse, so the most efficient thrusters are the most power-hungry. That is why an EP spacecraft needs a large power subsystem.

### Sizing an EP spacecraft: the characteristic velocity

The pre-recorded lecture derives the sizing equations (ll. 300–450), skipping some algebra, which is filled in here. Split the spacecraft into propellant (expellant) $M_e$, power plant $M_W$ and everything else, the payload $M_p$:

$$
M_0=M_e+M_W+M_p.
$$

Define the specific power of the power plant, $\beta=W/M_W$ in W/kg. Equate the jet power to the electrical power times the efficiency, and assume a constant mass flow rate over the burn time $t_b$, so $\dot m=M_e/t_b$:

$$
\tfrac12\frac{M_e}{t_b}V_{ex}^2=\eta\beta M_W.
$$

Solve for the power plant mass:

$$
M_W=M_e\frac{V_{ex}^2}{2\eta\beta t_b}.
$$

The group $2\eta\beta t_b$ has units of velocity squared. Define the characteristic velocity

$$
V_c=\sqrt{2\eta\beta t_b},
\qquad\text{so}\qquad
M_W=M_e\left(\frac{V_{ex}}{V_c}\right)^2.
$$

Write $x=V_{ex}/V_c$ and substitute into the mass breakdown:

$$
M_0=M_e+x^2M_e+M_p
\quad\Longrightarrow\quad
\boxed{M_e=\frac{M_0-M_p}{1+x^2}},
\qquad
\boxed{M_W=\frac{x^2(M_0-M_p)}{1+x^2}}.
$$

> [!warning] Transcript slip (pre-recorded lecture, ll. 326–330)
> The lecture defines β as "my mass of my power plant divided by my unit mass", and later as "the specific power of my power plant mass". It is the power per unit power-plant mass, $\beta=W/M_W$ in W/kg; only that reading makes $V_c$ a velocity.

Now the rocket equation. The burnout mass is $M_0-M_e$, so

$$
\Delta V=V_{ex}\ln\frac{M_0}{M_0-M_e}=V_{ex}\ln\frac{1}{1-M_e/M_0}.
$$

Write $p=M_p/M_0$, so $M_e/M_0=(1-p)/(1+x^2)$:

$$
1-\frac{M_e}{M_0}=\frac{1+x^2-(1-p)}{1+x^2}=\frac{x^2+p}{1+x^2}.
$$

Divide by $V_c$:

$$
\boxed{\frac{\Delta V}{V_c}=x\ln\frac{1+x^2}{x^2+p}}
$$

![[ast_ep_optimisation.png|650]]

For a chemical rocket, raising the exhaust velocity always raises the ΔV. Here it does not: each curve has a peak (ll. 400–430). Below the peak the rocket equation starves the vehicle of propellant; above it the power plant, whose mass grows as $V_{ex}^2$, eats into everything else. An EP system must therefore be optimised. The peaks, found numerically:

| $M_p/M_0$ | optimum $V_{ex}/V_c$ | peak $\Delta V/V_c$ |
|---|---|---|
| 0.1 | 0.633 | 0.651 |
| 0.25 | 0.737 | 0.491 |
| 0.5 | 0.849 | 0.291 |

So the optimum exhaust velocity is of the order of the characteristic velocity (the lecture says "around 1", and the curves put it at 0.6–0.85). A large $V_c$ needs a high efficiency, which cannot exceed 1, a high specific power, which is physically limited, or a long burn time. The burn time is the free variable, which is why EP missions thrust for months or years at low thrust (ll. 430–450). For $p=0.1$ the peak happens to have $\Delta V/V_c\approx V_{ex}/V_c\approx0.65$; the Quiz 1 walk-through called the equality "just a coincidence" that confuses people (ll. 251–276).

## 5. Impact on the spacecraft

The propulsion choice constrains the mass budget most of all: the rocket equation means large ΔVs carry large propellant penalties (2025-10-16, ll. 651–690). It affects the ACS through burn stabilisation, thrust misalignment and the number of manoeuvres ([[SESA2024 06 - Attitude Control#External disturbance torques|thrust misalignment as a disturbance]]). It needs thermal control of tanks, valves and lines, and a heat sink away from the main engine. EP adds a large power demand, and with it array area, mass and, in low orbit, drag.

> [!warning] Transcript slip (2025-10-16, l. 676)
> The thruster-as-disturbance-torque discussion is attributed to "Chapter 3". It was Chapter 6, attitude control.

## Worked examples

### Power for a 50 mN thruster

The lecture quoted a resistojet giving 50 mN at 700 s with an efficiency of 0.9 as needing "about 200 watts" (2025-10-16, ll. 576–580); Workbook Q10 extends it to the arcjet and ion thruster. With $g_0=9.81$:

| Thruster | $I_{sp}$ (s) | $\eta$ | $V_{ex}$ (m/s) | $\dot m$ (kg/s) | $W=TV_{ex}/2\eta$ |
|---|---|---|---|---|---|
| Resistojet | 700 | 0.9 | 6867 | $7.28\times10^{-6}$ | 191 W |
| Arcjet | 1500 | 0.3 | 14 715 | $3.40\times10^{-6}$ | 1226 W |
| Ion | 5000 | 0.75 | 49 050 | $1.02\times10^{-6}$ | 1635 W |

The ion thruster's "roughly 1.6 kilowatts" in the lecture (ll. 626–635) matches.

### Pluto orbiter by electric propulsion

The pre-recorded lecture and the 2025-10-16 lecture (ll. 513–540) set this up and leave it as Workbook Q12: ΔV = 17 km/s to orbit Pluto, payload fraction 0.1, efficiency 1, burn time 2 years, $M_0=3000$ kg.

A chemical system with $V_{ex}\approx3$ km/s would need $M_e/M_0=1-e^{-17/3}=0.9965$: almost the entire spacecraft would be propellant. With EP, read the optimum at $p=0.1$: $x=0.633$ and $\Delta V/V_c=0.651$. Then

$$
V_c=\frac{17\,000}{0.651}=26\,110\ \mathrm{m/s},
\qquad
V_{ex}=0.633\,V_c=16\,530\ \mathrm{m/s},
\qquad
I_{sp}=\frac{16\,530}{9.81}=1685\ \mathrm s,
$$

which is beyond an arcjet, so an ion thruster. The burn time is $t_b=2\times365.25\times86\,400=6.312\times10^7$ s (the quiz walk-through warns not to drop the quarter day, ll. 201–226), so

$$
\beta=\frac{V_c^2}{2\eta t_b}=\frac{26\,110^2}{2\times6.312\times10^7}=5.40\ \mathrm{W/kg},
$$

a low specific power that suits an RTG far from the Sun. The masses:

$$
M_e=\frac{3000-300}{1+0.633^2}=1928\ \mathrm{kg},
\qquad
M_W=0.633^2\times1928=772\ \mathrm{kg},
$$

and the performance:

$$
W=\beta M_W=4.17\ \mathrm{kW},
\qquad
\dot m=\frac{M_e}{t_b}=3.05\times10^{-5}\ \mathrm{kg/s},
\qquad
T=\dot mV_{ex}=0.50\ \mathrm N.
$$

Reading the graph as 0.65 for both ratios, as the workbook does, gives $V_{ex}=17$ km/s, $M_e=1898$ kg, $M_W=802$ kg and $W=4.3$ kW: graph-reading precision is all that separates the two.

## Links

- Parent: [[SESA2024 Astronautics Hub]]
- Previous: [[SESA2024 06 - Attitude Control]]
- Next: [[SESA2024 02 - Kepler's Laws and the Orbit Equation]] (next lecture, 2025-10-21) and [[SESA2024 08 - Electrical Power Subsystem]] (next subsystem)
- Concepts: [[Tsiolkovsky Rocket Equation]] · [[Rocket Performance Parameters]] · [[Thrust Equation]] (SESA2023) · [[Chemical Propulsion Systems]] · [[Electric Propulsion Sizing]]
- Workbook: [[SESA2024 Workbook Ch7 - Propulsion Solutions]]
- Where ΔV comes from: [[SESA2024 05 - Orbital Transfers and the Hohmann Transfer]] · [[SESA2024 14 - Orbit Control, Drag and Payload Data Rate]]
- In depth: [[SESA2023 Propulsion Hub]]

## Sources

- `Chapter 7 - Propulsion - original slides(1)(1).pdf` with the pre-recorded transcript `SESA2024 Lecture Chapter 7 - Propulsion - prerecorded material.txt` (performance parameters, chemical systems, EP sizing)
- `2025 WEEK 3 Lecture 2 - Chapter 7 - Propulsion - complete.pdf` with `SESA2024 Lecture 2025-10-16.txt`, ll. 276–700 (Dr H. Sykulska-Lawrence: classification, EP thruster types, system impacts)
- `SESA2024 Lecture 2025-10-28 - Quiz 1 Worked Solutions - Drop In session.txt`
- Fortescue, Stark and Swinerd, *Spacecraft Systems Engineering*, Ch. 6 (propulsion)

## Self-study tasks

### Core

- [ ] Show that $I_{sp}=V_{ex}/g_0$ and explain why it matters (Workbook Ch7 Q1; Quiz 1 true/false on "unit mass"). → [[#Specific impulse]] · [[SESA2024 Workbook Ch7 - Propulsion Solutions#Q1. Show that specific impulse is exhaust velocity over g0, and why it matters|Workbook Q1]]
- [ ] Quiz 1: find the specific impulse of a chemical system from the propellant used for a ΔV (walk-through, ll. 51–100); sanity check that the answer is a few hundred seconds. → [[#The rocket equation and propellant mass]]
- [ ] Quiz 1: electrical power for an ion thruster of given thrust, $I_{sp}$ and efficiency (walk-through, ll. 176–200). → [[#Power for a given thrust]] · [[#Power for a 50 mN thruster]]
- [ ] Power for a 50 mN thrust from a resistojet, arcjet and ion thruster (Workbook Ch7 Q10). → [[#Power for a 50 mN thruster]] · [[SESA2024 Workbook Ch7 - Propulsion Solutions#Q10. Power for a 50 mN thrust (Table 1)|Workbook Q10]]
- [ ] The Pluto orbiter by EP ("I'm not going to go through it in detail", 2025-10-16, ll. 513–540; Workbook Ch7 Q12; Quiz 1's hardest question). → [[#Pluto orbiter by electric propulsion]] · [[SESA2024 Workbook Ch7 - Propulsion Solutions#Q12. Pluto orbiter by electric propulsion|Workbook Q12]]

### Further practice

- [ ] Derive the EP sizing equations and $\Delta V/V_c$ (algebra left to you, pre-recorded lecture, ll. 351–400), then plot it for $M_p/M_0$ = 0.1 and 0.5 and explain the maximum (Workbook Ch7 Q11). → [[#Sizing an EP spacecraft: the characteristic velocity]]
- [ ] How a hydrazine monopropellant thruster works; what "hypergolic" means (Workbook Ch7 Q2, Q4). → [[#3. Chemical propulsion]]
- [ ] Two advantages and two disadvantages of each system, and why solids are not used for attitude control (Workbook Ch7 Q6, Q9). → [[#3. Chemical propulsion]] · [[SESA2024 Workbook Ch7 - Propulsion Solutions#Q9. Why solids are not used for attitude control, and one exception|Workbook Q9]]
- [ ] The two GEO propulsion architectures compared. → [[#Two architectures for a GEO spacecraft]]
- [ ] Read the EP number in 2024/25 A2 off the optimisation graph. → [[SESA2024 2024-25 Exam Solutions#Section A|2024/25 A2]]
