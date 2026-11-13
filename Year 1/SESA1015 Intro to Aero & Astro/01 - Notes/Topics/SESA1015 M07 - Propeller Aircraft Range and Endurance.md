---
title: "SESA1015 M07 - Propeller Aircraft Range and Endurance"
module: "SESA1015 Intro to Aero & Astro"
type: topic
stream: "Mechanics of Flight"
order: 7
tags:
  - sesa1015
  - mechanics-of-flight
  - propeller
  - range
  - endurance
  - compressibility
aliases: ["SESA1015 Mechanics 7", "Propeller Range and Endurance", "Piston Range and Endurance"]
date: 2026-09-27
status: lectured
coverage: "Course notes §6.1–6.3 (effect of compressibility on range, range of a piston-engined aircraft, optimum cruise techniques for jet and piston aircraft); Slides v2 pp. 68, 107–110 and 123–130 (power-specific propulsion, battery-powered range, propeller range and endurance, compressibility, electric against fuel, cruise rubric)"
parent: ["[[SESA1015 Intro to Aero & Astro Hub]]"]
prerequisites: ["[[SESA1015 M05 - Minimum Drag, Power and Performance Curves]]", "[[SESA1015 M06 - Jet Aircraft Range and Endurance]]"]
next_topics: ["[[SESA1015 M08 - Glide and Climb Performance]]"]
key_concepts: ["[[Power Specific Fuel Consumption]]", "[[Breguet Range Equation]]", "[[Minimum Drag and Minimum Power]]", "[[Propulsive Efficiency]]"]
tutorial_sheets: ["[[SESA1015 T04 - Range and Endurance Solutions]]"]
sources: ["02 - Sources/Mechanics of Flight/Mechanics of Flight - Course Notes.pdf (§6.1–6.3, pp. 32–35)", "02 - Sources/Mechanics of Flight/Mechanics of Flight - Lecture Slides version 2.pdf (pp. 68, 107–110, 123–130)"]
---

# SESA1015 M07 - Propeller Aircraft Range and Endurance

> [!abstract] Summary
> A piston or turboprop engine burns fuel in proportion to the shaft power it delivers, and the propeller turns a fraction $\eta$ of that power into the thrust power $DV$. The fuel flow is therefore $c_pDV/\eta$, and the speed cancels from the range: $R=\frac{\eta}{c_p}\frac{L}{D}\ln\frac{W_1}{W_2}$, greatest at $(L/D)_{max}$, the minimum drag speed. Endurance follows the power instead: $E=\frac{\eta}{c_p}\frac{C_L^{3/2}}{C_D}\sqrt{2\rho S}\left(\frac{1}{\sqrt{W_2}}-\frac{1}{\sqrt{W_1}}\right)$, greatest at the minimum power speed and at low altitude. A battery aircraft does not lose weight, so its range is linear in the battery fraction rather than logarithmic. For jets, compressibility drag sets the real cruise: the best range comes from maximising $ML/D$, at a higher $C_L$ and altitude than the incompressible analysis gives.

> [!summary]- Exam use: quick path
> - **Use it when:** a propeller, piston or battery aircraft's range, endurance or fuel (or battery) needed is asked for, or the best speed for either; or a comparison of jet and propeller optima.
> - **Assumptions:** steady level cruise; constant power-specific fuel consumption $c_p$ (weight of fuel per unit time per unit power) and constant combined propeller and transmission efficiency $\eta$; constant $C_L$; parabolic polar; for endurance, constant altitude as well.
> - **Method:** 1. Convert $c_p$ to N s⁻¹ W⁻¹: a value in N/(kW h) is divided by $1000\times3600$. 2. For minimum fuel or maximum range use $C_L=\sqrt{C_{D0}/K}$, $(L/D)_{max}=1/(2\sqrt{KC_{D0}})$. 3. $R=\frac{\eta}{c_p}\frac LD\ln\frac{W_1}{W_2}$; solve for whichever quantity is unknown. 4. For endurance use $C_L=\sqrt{3C_{D0}/K}$ in the square-root formula. 5. Check the speed against stall.
> - **Common mistakes:** using the jet optimum $C_L^{1/2}/C_D$ for a propeller; forgetting the factor 1000 when the SFC is quoted per kilowatt hour.
> - **Practise:** [[#Minimum fuel for a 1112 km flight]] · [[SESA1015 T04 - Range and Endurance Solutions#Question 27]]

A jet engine produces thrust and burns fuel in proportion to it. A piston engine, a turboprop or an electric motor produces shaft power, and its fuel (or battery energy) use follows the power. The propeller converts that power into thrust, and in steady flight the useful power is the drag times the speed. Halving the speed at a fixed drag halves the power and so halves the fuel flow, which is the difference from the jet: for a propeller aircraft, speed costs fuel directly.

That single difference moves every optimum one step down the speed range compared with a jet. The fuel per second follows $DV$, so endurance is best at minimum power, $V_{MP}$. The fuel per metre follows $DV/V=D$, so range is best at minimum drag, $V_{MD}$. For a jet the same two quantities follow $D$ and $D/V$, which put endurance at $V_{MD}$ and range above it.

In practice the propeller's efficiency falls at high speed, as the blade tips approach the speed of sound, and real piston aircraft cruise at intermediate heights at speeds above $V_{MD}$. For jets the corresponding real-world limit is the compressibility drag rise of the wing, which decides the cruise Mach number and altitude of every jet transport.

---

## 1. Power-specific fuel consumption

For a piston engine the **specific fuel consumption** ($c_p$ in the slides, $s'$ in the course notes) is the weight of fuel used per unit time to produce unit power ([[Power Specific Fuel Consumption]]). Its units are newtons of fuel per second per watt, N s⁻¹ W⁻¹. It is usually quoted per kilowatt hour:

$$
c_p=2.7\ \frac{\text{N}}{\text{kW h}}=\frac{2.7}{1000\times3600}=7.5\times10^{-7}\ \text{N s}^{-1}\text{W}^{-1}.
$$

This is not the jet's thrust-specific $c_t$ of [[SESA1015 M06 - Jet Aircraft Range and Endurance|M06]], which has units s⁻¹; the two cannot be compared without a speed, since thrust power is thrust times speed.

The power needed to overcome the drag at speed $V$ is $P=DV$. The engine must deliver more than this, because the propeller and transmission lose some:

$$
P'=\frac{DV}{\eta},
$$

where $\eta$ is the combined efficiency of the transmission and propeller ($\eta_{tot}$ in the slides; it includes the [[Propulsive Efficiency]] of the propeller). The engine model of [[SESA1015 M05 - Minimum Drag, Power and Performance Curves|M05]], power available independent of speed, belongs to this kind of engine.

## 2. Range of a propeller aircraft

The rate of loss of weight is the specific fuel consumption times the engine power. With $D=(D/L)L=(D/L)W$ in steady level flight:

$$
\frac{dW}{dt}=-c_pP'=-\frac{c_p}{\eta}DV=-\frac{c_p}{\eta}\frac{D}{L}WV .
$$

Converting time to distance with $dW/dt=V\,dW/dx$:

$$
\begin{aligned}
V\frac{dW}{dx}&=-\frac{c_p}{\eta}\frac{D}{L}WV\\
\frac{dW}{dx}&=-\frac{c_p}{\eta}\frac{D}{L}W .
\end{aligned}
$$

The speed has cancelled. Separating,

$$
dx=-\frac{\eta}{c_p}\frac{L}{D}\frac{dW}{W},
$$

and with $c_p$, $\eta$ and $L/D$ constant, integrating from $x=0$, $W_1=W_s+W_f$ to $x=R$, $W_2=W_s$:

$$
\begin{aligned}
R&=-\frac{\eta}{c_p}\frac{L}{D}\ln\frac{W_2}{W_1},
\end{aligned}
$$

$$
\boxed{R=\frac{\eta}{c_p}\frac{L}{D}\ln\frac{W_1}{W_2}=\frac{\eta}{c_p}\frac{L}{D}\ln\left(1+\frac{W_f}{W_s}\right)} .
$$

This is the **Breguet range equation for piston-engined aircraft** ([[Breguet Range Equation]]). Since $c_p$ is a weight of fuel per joule of shaft work, $\eta/c_p$ is a length: the distance the aircraft would travel per unit weight-ratio of fuel at $L/D=1$.

The maximum range at given $\eta$ and $c_p$ needs maximum $L/D$, so the aircraft flies at $C_L=\sqrt{C_{D0}/K}$, the minimum drag speed. The speed and density appear nowhere, so at constant $C_L$ the range is the same at any height and in any cruise pattern: holding altitude and slowing down, or holding speed and climbing, give the same distance. And, as for the jet, the design levers are low $c_p$ and high $\eta$ (propulsion), high $L/D$ (aerodynamics) and high $W_f/W_s$ (structures).

In practice $\eta$ falls at higher speeds, because the propeller tip speed, the vector sum of the rotational and forward speeds, approaches the speed of sound and the blades suffer compressibility losses. The maximum range then moves below $V_{MD}$ only if $\eta/c_p$ falls off rapidly with speed. Piston aircraft usually cruise at intermediate heights (about 4–8 km) at speeds greater than $V_{MD}$, trading a little range for time.

## 3. Endurance of a propeller aircraft

For endurance the fuel flow per second matters. With $D=W\,C_D/C_L$ and $V=\sqrt{2W/(\rho SC_L)}$:

$$
\begin{aligned}
\frac{dW}{dt}&=-\frac{c_p}{\eta}\frac{C_D}{C_L}WV\\
&=-\frac{c_p}{\eta}\frac{C_D}{C_L}W\sqrt{\frac{2W}{\rho SC_L}}\\
&=-\frac{c_p}{\eta}\frac{C_D}{C_L^{3/2}}\sqrt{\frac{2}{\rho S}}\;W^{3/2}.
\end{aligned}
$$

For endurance the speed does not cancel, so the density must be fixed: take constant angle of attack and constant altitude. Separating,

$$
dt=-\frac{\eta}{c_p}\frac{C_L^{3/2}}{C_D}\sqrt{\frac{\rho S}{2}}\;\frac{dW}{W^{3/2}},
$$

and integrating from $t=0$, $W_1$ to $t=E$, $W_2$, using $\int W^{-3/2}dW=-2W^{-1/2}$:

$$
\begin{aligned}
E&=-\frac{\eta}{c_p}\frac{C_L^{3/2}}{C_D}\sqrt{\frac{\rho S}{2}}\left[-2W^{-1/2}\right]_{W_1}^{W_2}\\
&=\frac{\eta}{c_p}\frac{C_L^{3/2}}{C_D}\sqrt{\frac{\rho S}{2}}\cdot2\left(\frac{1}{\sqrt{W_2}}-\frac{1}{\sqrt{W_1}}\right),
\end{aligned}
$$

$$
\boxed{E=\frac{\eta}{c_p}\frac{C_L^{3/2}}{C_D}\sqrt{2\rho S}\left(\frac{1}{\sqrt{W_2}}-\frac{1}{\sqrt{W_1}}\right)} .
$$

This is the **Breguet endurance equation** for a propeller aircraft. Maximum endurance needs maximum $C_L^{3/2}/C_D$, which is the minimum power condition derived in [[SESA1015 M05 - Minimum Drag, Power and Performance Curves|M05]]:

$$
C_L=\sqrt{\frac{3C_{D0}}{K}}=\sqrt3\,C_{L,MD},\qquad V=V_{MP}=3^{-1/4}V_{MD}.
$$

The factor $\sqrt\rho$ means the endurance is greatest at the lowest altitude, where the minimum power is smallest ($P_{min}\propto1/\sqrt\sigma$). The other requirements are the same as for range: high $\eta$, low $c_p$ and as much fuel as possible.

## 4. Jet and propeller compared

The two engine models put fuel flow in proportion to different things, thrust for the jet and power for the propeller. Per second and per metre of flight, at a given weight and height, that gives:

| | fuel per second | best endurance | fuel per metre | best range |
|---|---|---|---|---|
| jet ($c_t$) | $c_tD$ | min $D$: max $C_L/C_D$, $V_{MD}$ | $c_tD/V$ | max $C_L^{1/2}/C_D$, $3^{1/4}V_{MD}$ (constant altitude) |
| propeller ($c_p$, $\eta$) | $c_pDV/\eta$ | min $DV$: max $C_L^{3/2}/C_D$, $3^{-1/4}V_{MD}$ | $c_pD/\eta$ | max $C_L/C_D$, $V_{MD}$ |

Each step along a row multiplies or divides by $V$, and multiplying by a power of $V$ at fixed weight and height is multiplying by a power of $C_L^{-1/2}$: that is the whole origin of the exponents 1/2, 1 and 3/2. The jet's cruise-climb at fixed engine setting is the one optimum not in the table ($C_L/C_D^{3/2}$, $2^{1/4}V_{MD}$; [[SESA1015 M06 - Jet Aircraft Range and Endurance|M06]]).

![[mof_m07_fuel_flow.png|900]]

## 5. Battery-powered aircraft

A battery aircraft is power-specific like a propeller aircraft, but its weight does not change in flight. The battery holds energy $m_{bat}E^*$, where $E^*$ is its specific energy (J/kg; called the power density and quoted in Wh/kg in the slides, $1\ \text{Wh}=3600$ J). The battery delivers $P_{bat}$, of which a fraction $\eta_t$ (total efficiency of motor, transmission and propeller) reaches the air as thrust power, $P_{req}=DV=\eta_tP_{bat}$. At constant speed and constant weight the flight time is the time to drain the battery,

$$
T_f=\frac{m_{bat}E^*}{P_{bat}},
$$

and the range is $R=VT_f$. With $D=W/(L/D)=mg/(L/D)$:

$$
\begin{aligned}
P_{bat}&=\frac{DV}{\eta_t}=\frac{mgV}{\eta_t(L/D)},\\
R&=V\frac{m_{bat}E^*}{P_{bat}}=V\,m_{bat}E^*\frac{\eta_t(L/D)}{mgV},
\end{aligned}
$$

$$
\boxed{R=\eta_t\,\frac{L}{D}\,\frac{E^*}{g}\,\frac{m_{bat}}{m}} .
$$

The speed cancels, as for the propeller. Range is linear in the battery mass fraction, $E^*$, $\eta_t$ and $L/D$; there is no logarithm because the aircraft lands as heavy as it took off.

Comparing like with like, a fuel with $c_p=g/E^*$ gives $R=\eta\frac{L}{D}\frac{E^*}{g}\ln(1+W_f/W_s)$, while the battery gives $\eta\frac{L}{D}\frac{E^*}{g}\frac{x}{1+x}$ with $x=W_{bat}/W_s$. For small $x$ both are $\approx x$, so at energy-store fractions up to about 10 % there is little difference; at larger fractions burning off the energy store wins (1.22 times the range at $x=0.5$). The real gap is in $E^*$: kerosene holds about 43 MJ/kg ([[Calorific Value]]) against a few hundred watt hours (about 1 MJ) per kilogram for current batteries, so electric aircraft need much lighter structures and better aerodynamics before they match fuel-burning ones over long ranges. Hybrid-electric aircraft combine the two.

![[mof_m07_battery_vs_fuel.png|900]]

## 6. Effect of compressibility on range

The jet analysis of [[SESA1015 M06 - Jet Aircraft Range and Endurance|M06]] uses a fixed parabolic polar and ignores compressibility drag. For a jet transport its optimum conditions give lift coefficients and cruise heights lower than those used in practice. Once the drag rise at high Mach number is included, the best policy is to keep climbing at almost constant Mach number until the drag is minimised. As the aircraft climbs the density falls, so the $C_L$ needed to support the weight rises; the practical optimum $C_L$ for range is therefore greater than the incompressible analysis indicates.

The quantity to maximise is the **specific range**, the distance per unit weight of fuel. From $dx/dW=-\frac{V}{c_t}\frac{L}{D}\frac1W$ for a jet,

$$
\frac{dx}{-dW}=\frac{V}{c_tW}\frac{L}{D}=\frac{a}{c_tW}\left(M\frac{L}{D}\right),
$$

so at a given weight and $c_t$ the specific range is proportional to $ML/D$. For a wide-body trijet, $L/D$ and $ML/D$ plotted against $C_L$ peak at different Mach numbers (from Shevell, *Fundamentals of Flight*). The best $L/D$, 16.4, occurs at $M=0.75$ and $C_L=0.46$, but the best $ML/D$, about 13, occurs at $M=0.825$ at the same $C_L$: range rewards speed as well as aerodynamic efficiency. Reducing $C_L$ to 0.405 costs only about 1 % of range; since for a given weight a change of $C_L$ is a change of altitude, the range is fairly insensitive to the cruise height near the optimum. Raising the Mach number to 0.85 costs about 3 % of range but 9 % of $L/D$, because the drag rise has begun.

The engine adds a further correction. The assumption of constant $c_t$ is good for turbojets, but the specific fuel consumption of a turbofan rises slightly with Mach number, which moves the best-range condition to a somewhat lower Mach number than constant $c_t$ would give.

> [!check] The M06 jet against the incompressible optimum
> The jet of [[SESA1015 M06 - Jet Aircraft Range and Endurance|M06]] cruising at $M=0.79$ in the stratosphere has $V_{MD}=225.8$ m/s ($M=0.77$) at its start weight. The incompressible optima $2^{1/4}V_{MD}=268$ m/s and $3^{1/4}V_{MD}=297$ m/s are $M=0.91$ and $M=1.01$, both well past any transport wing's drag rise. Its actual cruise $C_L=0.593$ is near $C_{L,MD}=0.632$, consistent with a practical optimum $C_L$ above the incompressible value.

## 7. Optimum cruise techniques

For jet-engined aircraft (turbojet and turbofan):

| Aim | Condition | Speed |
|---|---|---|
| maximum range at a fixed altitude | max $C_L^{1/2}/C_D$; angle of attack and altitude constant, speed falls as fuel is used | $3^{1/4}V_{MD}$ |
| maximum range, cruise-climb in the stratosphere | max $C_L/C_D^{3/2}$ (fixed engine setting) | $2^{1/4}V_{MD}$ |
| maximum endurance | max $L/D$ | $V_{MD}$ |

Both maximum range and maximum endurance of jets are achieved at high altitude: range because the optimum true airspeed rises as $1/\sqrt\sigma$ while the drag does not, endurance because $c_t$ improves with altitude. The drag-rise Mach number caps the speed.

For piston-engined (propeller) aircraft:

| Aim | Condition | Speed |
|---|---|---|
| maximum range | max $L/D$, unless $\eta/c_p$ falls off rapidly with speed | $V_{MD}$ |
| maximum endurance | max $C_L^{3/2}/C_D$, at low altitude | $V_{MP}=3^{-1/4}V_{MD}$ |

Every one of these speeds must also be checked against the stall speed ([[SESA1015 M04 - Steady Level Flight and Stall|M04]]): the minimum power condition in particular can demand a lift coefficient close to $C_{L,max}$.

## 8. Worked examples

### Minimum fuel for a 1112 km flight

A propeller-driven aircraft weighs 8000 N dry and must fly 1112 km. The propeller efficiency is 85 %, $c_p=2.7$ N/(kW h) and $C_D=0.025+0.07C_L^2$. Find the minimum weight of fuel.

The least fuel for a given distance is the same problem as the greatest distance for a given fuel, so the aircraft flies at $(L/D)_{max}$:

$$
C_L=\sqrt{\frac{0.025}{0.07}}=0.5976,\qquad C_D=2(0.025)=0.05,\qquad\left(\frac LD\right)_{max}=\frac{1}{2\sqrt{0.07\times0.025}}=11.952 .
$$

Converting the SFC, $c_p=2.7/(3.6\times10^6)=7.5\times10^{-7}$ N s⁻¹ W⁻¹. Rearranging the Breguet equation for the weight ratio:

$$
\begin{aligned}
\ln\left(1+\frac{W_f}{W_s}\right)&=\frac{Rc_p}{\eta\,(L/D)}=\frac{1\,112\,000\times7.5\times10^{-7}}{0.85\times11.952}=0.08209,\\
W_f&=8000\left(e^{0.08209}-1\right)=684.4\ \text{N}.
\end{aligned}
$$

The fuel is about 70 kg, 8.6 % of the dry weight.

### Endurance of a piston aircraft

The 1350 kg aircraft of [[SESA1015 M05 - Minimum Drag, Power and Performance Curves|M05]] ($W_1=13\,230$ N, $S=16.25$ m², $C_{D0}=0.028$, $K=0.04787$) is given a piston engine with $\eta=0.85$ and $c_p=7.5\times10^{-7}$ N s⁻¹ W⁻¹, and 1200 N of fuel ($W_2=12\,030$ N). Find the endurance at sea level ($\rho=1.225$ kg/m³) and compare the range at the two optimum speeds.

At minimum power, $C_L=\sqrt{3\times0.028/0.04787}=1.3247$, $C_D=4(0.028)=0.112$, and $C_L^{3/2}/C_D=13.614$:

$$
\begin{aligned}
E&=\frac{0.85}{7.5\times10^{-7}}\times13.614\times\sqrt{2\times1.225\times16.25}\left(\frac{1}{\sqrt{12\,030}}-\frac{1}{\sqrt{13\,230}}\right)\\
&=1.1333\times10^6\times13.614\times6.3097\times4.233\times10^{-4}\\
&=41\,210\ \text{s}=11.45\ \text{h}.
\end{aligned}
$$

At minimum drag ($C_L=0.7648$, $C_L^{3/2}/C_D=11.944$) the endurance would be 10.04 h, 12 % less. The range is best at minimum drag:

$$
R=\frac{0.85}{7.5\times10^{-7}}\times13.66\times\ln\frac{13\,230}{12\,030}=1472\ \text{km},
$$

against 1275 km at minimum power. At 3050 m ($\rho=0.9082$ kg/m³) the best endurance falls to $11.45\sqrt{0.9082/1.225}=9.86$ h, while the range is unchanged. The minimum power speed here is 31.7 m/s at the start and 30.2 m/s at the end, with $C_L=1.32$, which a light aircraft without flap may not reach before stalling; the stall check decides whether this endurance is available.

### Battery mass for a 100 km UAV

A battery-powered UAV has mass 10 kg, $S=0.25$ m², $AR=7$, $e=0.9$, $C_{D0}=0.03$ and cruises at 20 m/s for 100 km with total efficiency 0.75. Find the battery mass for $E^*=250$ Wh/kg (with $\rho=1.23$ kg/m³ and $g=9.8$ m/s²).

$$
\begin{aligned}
K&=\frac{1}{\pi(0.9)(7)}=0.05053,\qquad W=98\ \text{N},\\
D&=\tfrac12(1.23)(20)^2(0.25)(0.03)+\frac{2(0.05053)(98)^2}{1.23(20)^2(0.25)}=1.845+7.890=9.735\ \text{N},\\
\frac LD&=\frac{98}{9.735}=10.067,\qquad E^*=250\times3600=900\,000\ \text{J/kg}.
\end{aligned}
$$

Rearranging the range equation for the mass fraction:

$$
\frac{m_{bat}}{m}=\frac{Rg}{\eta_t(L/D)E^*}=\frac{100\,000\times9.8}{0.75\times10.067\times900\,000}=0.1442,\qquad m_{bat}=1.44\ \text{kg}.
$$

The cruise $C_L=98/(\tfrac12\times1.23\times400\times0.25)=1.59$ is high for a small UAV; at that $C_L$ the induced drag is 81 % of the total, well to the slow side of minimum drag ($C_{L,MD}=0.77$).

## Links

- Parent: [[SESA1015 Intro to Aero & Astro Hub]] · Solutions: [[SESA1015 T04 - Range and Endurance Solutions]]
- Previous: [[SESA1015 M06 - Jet Aircraft Range and Endurance]] · Next: [[SESA1015 M08 - Glide and Climb Performance]] (minimum sink at $V_{MP}$, best glide at $V_{MD}$)
- Builds on: [[SESA1015 M05 - Minimum Drag, Power and Performance Curves]] (the $C_L$ optima and the power model)
- Concepts: [[Power Specific Fuel Consumption]] · [[Breguet Range Equation]] · [[Minimum Drag and Minimum Power]] · [[Cruise-Climb]]
- Later in the degree: [[SESA2023 W01 - Thrust, Efficiency, Range and the ISA]] (range from overall efficiency and calorific value), [[Propulsive Efficiency]], [[Actuator Disk Theory]] (propeller efficiency), [[Calorific Value]]

## Sources

- Mechanics of Flight Course Notes (Keane, October 2020): §6.1 Effect of compressibility on range and Fig. 6.1 (pp. 32–33), §6.2 Range of a piston-engined aircraft (pp. 33–35), §6.3 Optimum cruise performance techniques (p. 35)
- Mechanics of Flight Lecture Slides version 2: power-specific propulsion (p. 68), battery-powered range and UAV example (pp. 108–110), propeller range (p. 124), propeller endurance (p. 125), minimum-fuel example (pp. 123, 126), compressibility (p. 127), electric against fuel-powered propulsion (p. 128), cruise rubric (p. 130)

## Self-study tasks

### Core

- [ ] Revision Q27: minimum fuel for a propeller aircraft to fly 969 nm. → [[SESA1015 T04 - Range and Endurance Solutions#Question 27]] · [[#Minimum fuel for a 1112 km flight]]
- [ ] Slides v2, p. 123: minimum fuel weight for the 8000 N aircraft over 1112 km, deriving the range equation. → [[#Minimum fuel for a 1112 km flight]]
- [ ] Derive the propeller endurance equation and show that it is greatest at $C_L=\sqrt{3C_{D0}/K}$. → [[#3. Endurance of a propeller aircraft]]
- [ ] Fill in the jet and propeller table from the fuel-flow expressions without looking. → [[#4. Jet and propeller compared]]

### Further practice

- [ ] Slides v2, p. 110: battery mass for the 100 km UAV. → [[#Battery mass for a 100 km UAV]]
- [ ] Endurance and range of the 1350 kg aircraft with a piston engine, at sea level and at 3050 m. → [[#Endurance of a piston aircraft]]
- [ ] Explain, using $ML/D$, why practical jet cruise $C_L$ and altitude exceed the incompressible optimum (course notes §6.1, Fig. 6.1). → [[#6. Effect of compressibility on range]]
