---
title: "SESA1015 M06 - Jet Aircraft Range and Endurance"
module: "SESA1015 Intro to Aero & Astro"
type: topic
stream: "Mechanics of Flight"
order: 6
tags:
  - sesa1015
  - mechanics-of-flight
  - jet
  - range
  - endurance
  - breguet
aliases: ["SESA1015 Mechanics 6", "Jet Range and Endurance", "Cruise-Climb"]
date: 2026-09-27
status: lectured
coverage: "Course notes §5 intro and §5.1–5.5 (jet endurance, Breguet range, range in the stratosphere, cruise-climb, maximising the Breguet range, effect of altitude on cruising speed), §6 intro (range at constant altitude and angle of attack) and §6.3.1; Slides v2 p. 72 (mission profiles, step climb, eVTOL profile), pp. 111–122 and 130 (thrust-specific propulsion, cruise schedules, worked examples)"
parent: ["[[SESA1015 Intro to Aero & Astro Hub]]"]
prerequisites: ["[[SESA1015 M05 - Minimum Drag, Power and Performance Curves]]", "[[SESA1015 M01 - Atmosphere, Airspeed and Mach Number]]"]
next_topics: ["[[SESA1015 M07 - Propeller Aircraft Range and Endurance]]"]
key_concepts: ["[[Breguet Range Equation]]", "[[Thrust Specific Fuel Consumption]]", "[[Cruise-Climb]]", "[[Minimum Drag and Minimum Power]]"]
tutorial_sheets: ["[[SESA1015 T04 - Range and Endurance Solutions]]"]
sources: ["02 - Sources/Mechanics of Flight/Mechanics of Flight - Course Notes.pdf (§5–§6 intro, pp. 25–32; §6.3.1, p. 35)", "02 - Sources/Mechanics of Flight/Mechanics of Flight - Lecture Slides version 2.pdf (pp. 69, 72, 111–122, 130)"]
---

# SESA1015 M06 - Jet Aircraft Range and Endurance

> [!abstract] Summary
> A jet engine burns fuel in proportion to its thrust, $dW/dt=-c_tT$, and in steady cruise $T=D=W\,C_D/C_L$, so the aircraft's weight decays at a rate set by $c_t$ and the lift-to-drag ratio. Integrating at constant angle of attack gives the endurance $E=\frac{1}{c_t}\frac{L}{D}\ln\frac{W_1}{W_2}$ (best at $(L/D)_{max}$) and, at constant speed, the Breguet range $R=\frac{V}{c_t}\frac{L}{D}\ln\frac{W_1}{W_2}$, which requires the aircraft to drift upwards as it burns fuel (the cruise-climb). Holding the altitude instead gives $R=\frac{2}{c_t}\sqrt{\frac{2}{\rho S}}\frac{C_L^{1/2}}{C_D}(\sqrt{W_1}-\sqrt{W_2})$, best at $V=3^{1/4}V_{MD}$; the cruise-climb at fixed engine setting is best at $V=2^{1/4}V_{MD}$. All three favour flying high, up to the drag-rise Mach number.

> [!summary]- Exam use: quick path
> - **Use it when:** a jet's cruise range, endurance, required fuel or required specific fuel consumption is asked for, or the best cruise speed or $C_L$ for range or endurance.
> - **Assumptions:** steady cruise ($L=W$, $T=D$); constant $c_t$ (weight of fuel per unit time per unit thrust); constant angle of attack ($C_L$, hence $L/D$); parabolic polar; climb, descent and reserves ignored; natural logarithms.
> - **Method:** 1. $S=b^2/AR$, $W_1=(W/S)S$, $W_2=W_1-W_f$. 2. $V=Ma$ with $a=\sqrt{\gamma RT}$; $C_L=2(W/S)/(\rho V^2)$; $C_D$ from the polar. 3. Convert $c_t$ to s⁻¹ (divide a per-hour figure by 3600). 4. Pick the formula for the cruise pattern: endurance, constant speed (log), or constant altitude (square roots). 5. Range in metres; nautical miles × 1852.
> - **Common mistakes:** adding the fuel to a weight that already includes it ($W_1$ from the start-of-cruise wing loading is the total); using the log formula for a cruise stated to be at constant altitude.
> - **Practise:** [[#Specific fuel consumption for a 7041 km cruise]] · [[SESA1015 T04 - Range and Endurance Solutions#Question 5]]

Range is the distance an aircraft can fly on its fuel; endurance is the time it can stay airborne. Both follow from the same weight balance. The aircraft's weight is its empty weight plus payload plus fuel, $W=W_e+W_p+W_f$; only the fuel changes in flight, so the weight falls at the rate the engines burn fuel. A turbojet or turbofan burns fuel roughly in proportion to the thrust it produces, almost independently of flight speed, and in steady cruise that thrust equals the drag. The drag in turn is the weight divided by $L/D$. So the fuel flow is proportional to the weight itself, and a heavy aircraft burns fuel faster than a light one. This is what makes the weight decay exponentially in time, and why the logarithm of the weight ratio appears in every result.

As fuel burns, lift must fall to match the weight. Since $L=\tfrac12\rho V^2SC_L$, something has to give: the density (the aircraft climbs), the speed (it slows) or the lift coefficient (it lowers its nose). Each choice is a different cruise pattern with a different range, and each has its own best speed. For endurance only the fuel flow per second matters, so the best condition is minimum drag. For range the fuel per metre matters, which is drag divided by speed, and that is least at a speed somewhat above $V_{MD}$.

Height helps a jet because the minimum drag does not change with altitude ([[SESA1015 M05 - Minimum Drag, Power and Performance Curves|M05]]) while the speed at which it is reached rises as $1/\sqrt\sigma$. The same drag, and the same fuel per second, carries the aircraft further per second. The limit is compressibility: a higher true airspeed in colder air is a higher Mach number, and beyond the drag rise the drag polar no longer holds.

---

## 1. Fuel consumption of a jet engine

The **specific fuel consumption** of a jet ($c_t$ in the slides, $s$ in the course notes) is the weight of fuel used per unit time to produce unit thrust. Its units are newtons of fuel per second per newton of thrust, N s⁻¹ N⁻¹, which reduces to s⁻¹. A figure quoted per hour is divided by 3600: 1.5 N of fuel per hour per N of thrust is $c_t=4.17\times10^{-4}$ s⁻¹. This is a thrust-specific measure; the power-specific consumption used for piston and propeller engines in [[SESA1015 M07 - Propeller Aircraft Range and Endurance|M07]] is a different quantity with different units. In SESA2023 the same idea is defined on a mass basis, [[Thrust Specific Fuel Consumption]] in kg s⁻¹ N⁻¹, so $c_t=g\times\text{TSFC}$.

For a turbojet $c_t$ is roughly independent of forward speed but varies with altitude; it is taken as constant through the cruise. The weight then falls at

$$
\frac{dW}{dt}=-c_tT,
$$

where $W(t)$ is the total weight at time $t$ and $T$ the total thrust.

## 2. Cruise equilibrium and the cruise patterns

In steady cruise $T=D$ and $L=W$, so

$$
\begin{aligned}
\frac{dW}{dt}&=-c_tD=-c_t\frac{D}{L}L\\
&=-c_t\frac{D}{L}W=-c_t\frac{C_D}{C_L}W .
\end{aligned}
$$

At constant angle of attack $C_L$ is constant, and so is $C_D=C_{D0}+KC_L^2$ and the ratio $L/D=C_L/C_D$. Lift must still fall with the weight, so with $C_L$ fixed either $\rho$ or $V$ (or both) must change:

| Cruise pattern | Held constant | Changes as fuel burns | Result |
|---|---|---|---|
| cruise-climb | $C_L$, $V$ (so $L/D$) | density falls: the aircraft climbs | log (Breguet) range, [[#4. Range at constant speed - the Breguet range equation]] |
| constant altitude | $C_L$, $\rho$ | speed falls as $\sqrt W$; thrust must be reduced | square-root range, [[#7. Range at constant altitude]] |
| constant speed and altitude | $V$, $\rho$ | $C_L$ falls; $L/D$ changes | not integrated in this module |

Constant angle of attack at constant altitude means the throttle must be eased back as the drag falls with the weight, and the speed drops through the flight, which is seldom acceptable for passenger flights. Since angle of attack is not normally displayed in the cockpit, pilots more often fly at constant speed or constant throttle setting (constant thrust).

## 3. Endurance

At constant $C_L$ the weight equation separates:

$$
\frac{dW}{W}=-c_t\frac{C_D}{C_L}\,dt .
$$

Integrate from the start of cruise ($t=0$, $W=W_1=W_s+W_f$) to time $t$, with $c_t$ and $C_D/C_L$ constant:

$$
\begin{aligned}
\int_{W_1}^{W}\frac{dW}{W}&=-c_t\frac{C_D}{C_L}\int_0^t dt\\
\ln\frac{W}{W_1}&=-c_t\frac{C_D}{C_L}\,t\\
t&=\frac{1}{c_t}\frac{C_L}{C_D}\ln\frac{W_1}{W}.
\end{aligned}
$$

Here $W_s$ is the dry weight (empty plus payload) and $W_f$ the fuel for the cruise. Burning all of it ends the cruise at $W=W_2=W_s$, and the **endurance** is

$$
\boxed{E=\frac{1}{c_t}\frac{L}{D}\ln\frac{W_1}{W_2}=\frac{1}{c_t}\frac{L}{D}\ln\left(1+\frac{W_f}{W_s}\right)} .
$$

The result does not contain the speed or the density, so at a given $C_L$ the endurance is the same at any height, apart from the variation of $c_t$. It separates the three design levers: low $c_t$ (propulsion), high $L/D$ (aerodynamics) and high $W_f/W_s$ (structures). Maximum endurance at a given $c_t$ needs maximum $L/D$:

$$
C_L=C_{L,MD}=\sqrt{\frac{C_{D0}}{K}},\qquad V=V_{MD}.
$$

Inverting the integral gives the weight history, $W(t)=W_1\exp\!\left(-c_t\frac{C_D}{C_L}t\right)$: an exponential decay with time constant $\frac{1}{c_t}\frac{L}{D}$.

## 4. Range at constant speed - the Breguet range equation

Distance $x$ and time are linked by $dx/dt=V$, so

$$
\frac{dW}{dt}=\frac{dW}{dx}\frac{dx}{dt}=V\frac{dW}{dx}.
$$

Equating this to $-c_t(D/L)W$:

$$
\frac{dW}{dx}=-\frac{c_t}{V}\frac{D}{L}W\quad\Rightarrow\quad dx=-\frac{V}{c_t}\frac{L}{D}\frac{dW}{W}.
$$

If $V$, $L/D$ and $c_t$ are all constant, integrate from $x=0$, $W=W_1$ to $x=R$, $W=W_2$:

$$
\begin{aligned}
R&=-\frac{V}{c_t}\frac{L}{D}\int_{W_1}^{W_2}\frac{dW}{W}\\
&=-\frac{V}{c_t}\frac{L}{D}\ln\frac{W_2}{W_1},
\end{aligned}
$$

$$
\boxed{R=\frac{V}{c_t}\frac{L}{D}\ln\frac{W_1}{W_2}=\frac{V}{c_t}\frac{L}{D}\ln\left(1+\frac{W_f}{W_s}\right)} .
$$

This is the **Breguet range equation** for a jet ([[Breguet Range Equation]]). It assumes the whole cruise is flown at constant $VL/D$; other cruise patterns give somewhat different ranges. Maximum range needs low $c_t$, high $W_f/W_s$ and maximum $VL/D$, not maximum $L/D$, so the speed for maximum range differs from the speed for maximum endurance.

The weight ratio enters through a logarithm, so range grows more slowly than the fuel carried. The first kilograms of fuel are burned while the aircraft is heavy, carrying the later fuel, so each extra unit of fuel buys less distance than the one before (figure in [[#Comparison with the cruise-climb]]).

## 5. Range in the stratosphere

In the lower stratosphere (11–20 km in the ISA) the temperature is constant at $T_s=216.65$ K, so the speed of sound $a=\sqrt{\gamma RT_s}=295.1$ m/s is constant. Constant true airspeed is then constant Mach number, $V=Ma$, and

$$
R=\frac{a}{c_t}\left(\frac{ML}{D}\right)\ln\frac{W_1}{W_2}.
$$

Range is greatest when $M\,L/D$ is greatest, which pushes the Mach number up until compressibility drag (shock waves forming on the wing) starts to cut $L/D$ faster than $M$ rises. For current jet transports this is around $M=0.82$ (see [[SESA1015 M07 - Propeller Aircraft Range and Endurance|M07]]).

## 6. Cruise-climb

### Why the aircraft climbs

The Breguet equation needs $V$ and $C_L$ constant while the weight falls. From

$$
W=L=\tfrac12\rho_{SL}\,\sigma V^2SC_L,
$$

with $V$, $S$ and $C_L$ fixed, $W\propto\sigma$: the relative density must fall in proportion to the weight, so the aircraft gains height. In the stratosphere the thrust of a jet at fixed throttle setting is roughly proportional to the relative density, $T_2/T_1=\sigma_2/\sigma_1$, ignoring any variation with speed. The drag $D=W\,C_D/C_L$ falls in proportion to $W$, and so in proportion to $\sigma$. Thrust and drag therefore fall together and stay equal without touching the throttle: the aircraft flies at constant Mach number and drifts up as it burns fuel. This is the **cruise-climb** ([[Cruise-Climb]]); air-traffic control allows it on the main long-haul routes, though not indefinitely.

![[mof_m06_cruise_modes.png|900]]

### Height gained

Since $\sigma\propto W$ at constant $V$ and $C_L$, the density history follows the weight history:

$$
\frac{\sigma_2}{\sigma_1}=\frac{W_2}{W_1}=\exp\!\left(-c_t\frac{C_D}{C_L}\,t\right).
$$

The same result follows by differentiating the lift balance in time. With $V$, $C_L$ fixed, $\frac{dW}{dt}=\tfrac12\rho_{SL}SV^2C_L\frac{d\sigma}{dt}$, and setting this equal to $-c_tD=-c_t\tfrac12\rho_{SL}\sigma SV^2C_D$:

$$
\begin{aligned}
C_L\frac{d\sigma}{dt}&=-c_tC_D\,\sigma\\
\frac{d\sigma}{\sigma}&=-c_t\frac{C_D}{C_L}\,dt\\
\ln\frac{\sigma_2}{\sigma_1}&=-c_t\frac{C_D}{C_L}(t_2-t_1).
\end{aligned}
$$

In the isothermal stratosphere the density falls exponentially with height, $\sigma=\sigma_{11}\exp[-g(h-h_{11})/(RT_s)]$ ([[SESA1015 M01 - Atmosphere, Airspeed and Mach Number|M01]]), so

$$
\Delta h=\frac{RT_s}{g}\ln\frac{\sigma_1}{\sigma_2}=\frac{RT_s}{g}\ln\frac{W_1}{W_2},
$$

with $RT_s/g=287\times216.65/9.81=6338$ m. Burning a quarter of the take-off weight ($W_1/W_2=1.33$) lifts the aircraft about 1.8 km.

In the troposphere, $\sigma=\theta^{\,n}$ with $\theta=T/T_{SL}=1-c_0h/T_{SL}$ and $n=g/(c_0R)-1$. Starting from sea level ($\sigma_1=1$) and solving for $h$:

$$
h=\frac{T_{SL}}{c_0}\left[1-\left(\frac{\sigma_2}{\sigma_1}\right)^{1/n}\right]=\frac{T_{SL}}{c_0}\left[1-\left(e^{-c_t(C_D/C_L)t}\right)^{c_0R/(g-c_0R)}\right].
$$

### Mission profiles and the step climb

The range and endurance results describe single segments of a flight. A simple mission profile is warm-up and take-off, climb, cruise, loiter and landing (Slides v2, p. 72). The Breguet and constant-altitude range equations cover the cruise. The loiter, a holding pattern flown while waiting to land, is an endurance segment, flown for least fuel per second at the minimum drag condition of [[#3. Endurance]]. Take-off, climb and descent are not part of these results ([[SESA1015 M08 - Glide and Climb Performance|M08]], [[SESA1015 M09 - Take-off and Landing Performance|M09]]).

Since the fuel each segment burns is proportional to the weight it starts with, segments are combined through their weight fractions, which multiply: $W_{end}/W_{start}=\prod_i W_i/W_{i-1}$. Rearranging the Breguet range and the endurance equation gives the fractions for a cruise of range $R$ and a loiter of duration $E$:

$$
\begin{aligned}
\ln\frac{W_1}{W_2}&=\frac{Rc_t}{V\,(L/D)}
&&\Rightarrow\quad\frac{W_2}{W_1}=\exp\!\left[-\frac{Rc_t}{V\,(L/D)}\right],\\
\ln\frac{W_1}{W_2}&=\frac{Ec_t}{L/D}
&&\Rightarrow\quad\frac{W_2}{W_1}=\exp\!\left[-\frac{Ec_t}{L/D}\right].
\end{aligned}
$$

> [!check] Cruise and loiter fractions
> For the aircraft of [[#Specific fuel consumption for a 7041 km cruise]] ($c_t=1.6338\times10^{-4}$ s⁻¹, $V=233.1$ m/s, $L/D=17.53$), a 5000 km cruise gives $W_2/W_1=\exp(-0.1999)=0.819$. A 30 minute loiter at $L/D=18$ gives $\exp(-0.0163)=0.984$. The product is 0.806, so the two segments burn 19.4 % of the weight at the start of the cruise.

Air-traffic control assigns fixed flight levels, so a long-haul jet seldom flies a true cruise-climb. It flies a **step climb** instead: a first climb to an initial cruise level, a cruise at constant altitude until enough fuel has burned that a higher level is nearer the optimum, a second climb, a final cruise and then the descent (Slides v2, p. 72). The staircase approximates the continuous cruise-climb, and its range lies between the constant-altitude and cruise-climb values of [[#Comparison with the cruise-climb]], closer to the cruise-climb the smaller the steps. Inverting the stratospheric height gain $\Delta h=(RT_s/g)\ln(W_1/W_2)$ of [[#Height gained]],

$$
\begin{aligned}
\frac{W_1}{W_2}&=\exp\!\left(\frac{g\,\Delta h}{RT_s}\right),\\
1-\frac{W_2}{W_1}&=1-\exp\!\left(-\frac{g\,\Delta h}{RT_s}\right).
\end{aligned}
$$

With $RT_s/g=6338$ m, a 2000 ft (609.6 m) step is due each time the aircraft burns 9.2 % of its current weight, and a 4000 ft step after 17.5 %.

An urban-air-mobility eVTOL (electric vertical take-off and landing) aircraft flies a different profile (Slides v2, p. 72): hover and vertical take-off, a forward transition to wing-borne flight above a transition height, a climb to the cruise height inside an air corridor, the cruise, a descent, a backward transition and a vertical landing. Hover and the transitions are carried by rotor thrust rather than wing lift and use energy unrelated to $L/D$, so the battery range equation of [[SESA1015 M07 - Propeller Aircraft Range and Endurance|M07]] applies only to the energy left for the wing-borne cruise.

## 7. Range at constant altitude

At constant altitude and constant angle of attack, $\rho$ and $C_L$ are fixed, $L/D$ is fixed, and the speed must fall as the weight falls:

$$
V=\sqrt{\frac{2W}{\rho SC_L}} .
$$

The range equation $dW/dx=-(c_t/V)(D/L)W$ now has $V$ depending on $W$:

$$
\begin{aligned}
\frac{dW}{dx}&=-\frac{c_t}{V}\frac{C_D}{C_L}W\\
&=-c_t\frac{C_D}{C_L}W\sqrt{\frac{\rho SC_L}{2W}}\\
&=-c_t\sqrt{\frac{\rho S}{2}}\,\frac{C_D}{C_L^{1/2}}\,W^{1/2}.
\end{aligned}
$$

Separating,

$$
dx=-\frac{1}{c_t}\sqrt{\frac{2}{\rho S}}\,\frac{C_L^{1/2}}{C_D}\,\frac{dW}{W^{1/2}},
$$

and integrating from $W_1$ to $W_2$ with $\int W^{-1/2}dW=2W^{1/2}$:

$$
\boxed{R=\frac{2}{c_t}\sqrt{\frac{2}{\rho S}}\,\frac{C_L^{1/2}}{C_D}\left(\sqrt{W_1}-\sqrt{W_2}\right)} .
$$

The aerodynamic factor is now $C_L^{1/2}/C_D$, not $C_L/C_D$, because the speed is not free: a lower $C_L$ means a faster cruise at the same height. The range also grows as $1/\sqrt\rho$, so higher is better here too. The end-of-cruise speed is $V_2=V_1\sqrt{W_2/W_1}$.

### Comparison with the cruise-climb

Start both patterns from the same state, speed $V_1=\sqrt{2W_1/(\rho_1SC_L)}$ and coefficient $C_L$. Writing $\sqrt{2/(\rho_1S)}\,C_L^{1/2}\sqrt{W_1}=V_1C_L$, the constant-altitude range becomes

$$
R_{alt}=\frac{2V_1}{c_t}\frac{C_L}{C_D}\left(1-\sqrt{\frac{W_2}{W_1}}\right),
$$

and dividing by the Breguet range $R_{cc}=\frac{V_1}{c_t}\frac{C_L}{C_D}\ln\frac{W_1}{W_2}$,

$$
\frac{R_{alt}}{R_{cc}}=\frac{2\left(1-\sqrt{W_2/W_1}\right)}{\ln(W_1/W_2)}<1 .
$$

Holding the height costs range because the aircraft slows down as it lightens, while the cruise-climb keeps the speed and lets the air thin instead. For small fuel fractions the two agree to first order; for a 24.5 % fuel fraction (the slide example) the constant-altitude cruise reaches 93.3 % of the cruise-climb range.

![[mof_m06_mass_ratio.png|900]]

## 8. Maximising the range

### Constant altitude

At a given height and weight the speed is set by $C_L$, and the range is greatest when $C_L^{1/2}/C_D$ is greatest. With $C_D=C_{D0}+KC_L^2$:

$$
\begin{aligned}
\frac{d}{dC_L}\left(\frac{C_L^{1/2}}{C_{D0}+KC_L^2}\right)&=\frac{\tfrac12C_L^{-1/2}(C_{D0}+KC_L^2)-C_L^{1/2}(2KC_L)}{(C_{D0}+KC_L^2)^2}\\
&=\frac{C_L^{-1/2}\left(\tfrac12C_{D0}+\tfrac12KC_L^2-2KC_L^2\right)}{C_D^2}\\
&=\frac{C_{D0}-3KC_L^2}{2C_L^{1/2}C_D^2}=0 .
\end{aligned}
$$

So the optimum has

$$
C_{D0}=3KC_L^2,\qquad C_L=\sqrt{\frac{C_{D0}}{3K}}=\frac{C_{L,MD}}{\sqrt3},\qquad C_D=\tfrac43C_{D0}:
$$

the profile drag is three times the induced drag. Since $V\propto C_L^{-1/2}$ at a given weight and density,

$$
V_{opt}=\left(\frac{C_{L,MD}}{C_L}\right)^{1/2}V_{MD}=3^{1/4}V_{MD}\approx1.316\,V_{MD}.
$$

The $L/D$ there is $\frac{\sqrt3}{2}(L/D)_{max}=0.866\,(L/D)_{max}$: some aerodynamic efficiency is traded for speed. As the weight falls, $V_{MD}$ falls with $\sqrt W$ and so does the cruise speed, keeping the ratio $3^{1/4}$ throughout.

### Cruise-climb - two ways to fix the speed

For the cruise-climb the factor to maximise is $VL/D=VC_L/C_D$, but how $V$ depends on $C_L$ depends on what else is held fixed (Slides v2, p. 120).

In the first schedule, height matching, the engine runs at a fixed setting, so the thrust-to-density ratio is fixed, $T/\sigma=T_{SL}$. Thrust equals drag:

$$
\begin{aligned}
T_{SL}\,\sigma&=\tfrac12\rho_{SL}\,\sigma V^2SC_D\\
V&=\sqrt{\frac{2T_{SL}}{\rho_{SL}SC_D}},
\end{aligned}
$$

so $V^2C_D$ is constant and $V\propto C_D^{-1/2}$. Then

$$
\frac{VC_L}{C_D}=\sqrt{\frac{2T_{SL}}{\rho_{SL}S}}\;\frac{C_L}{C_D^{3/2}},
$$

and the range is greatest when $C_L/C_D^{3/2}$ is greatest:

$$
\begin{aligned}
\frac{d}{dC_L}\left(\frac{C_L}{(C_{D0}+KC_L^2)^{3/2}}\right)&=\frac{(C_{D0}+KC_L^2)^{3/2}-C_L\cdot\tfrac32(C_{D0}+KC_L^2)^{1/2}(2KC_L)}{(C_{D0}+KC_L^2)^3}\\
&=\frac{(C_{D0}+KC_L^2)^{1/2}\left(C_{D0}+KC_L^2-3KC_L^2\right)}{(C_{D0}+KC_L^2)^3}\\
&=\frac{C_{D0}-2KC_L^2}{(C_{D0}+KC_L^2)^{5/2}}=0 .
\end{aligned}
$$

So $C_{D0}=2KC_L^2$ (profile drag twice induced drag), $C_L=C_{L,MD}/\sqrt2$, $C_D=\tfrac32C_{D0}$, and at the weight and density of the moment

$$
V_{opt}=2^{1/4}V_{MD}\approx1.189\,V_{MD}.
$$

This is the cruise-climb optimum (course notes §5.4 and §6.3.1(b)). Holding it means continually matching the throttle to the height, which is not always possible.

In the second schedule the speed is fixed at the start, from the initial weight and height: $V_1=\sqrt{2W_1/(\rho_1SC_L)}$. Then

$$
\frac{V_1C_L}{C_D}=\sqrt{\frac{2W_1}{\rho_1S}}\;\frac{C_L^{1/2}}{C_D},
$$

the same factor as at constant altitude, so the best start condition is $C_L=C_{L,MD}/\sqrt3$ and $V=3^{1/4}V_{MD}$.

The two answers differ because they compare different sets of flights. With the initial height fixed, a lower $C_L$ only means flying faster at that height. With the engine setting fixed, a lower $C_L$ also changes the height at which thrust balances drag, so speed and density change together.

![[mof_m06_range_factors.png|900]]

> [!warning] Which optimum the question wants
> Constant altitude and constant angle of attack: maximise $C_L^{1/2}/C_D$, $V=3^{1/4}V_{MD}$. Cruise-climb in the stratosphere at fixed engine setting: maximise $C_L/C_D^{3/2}$, $V=2^{1/4}V_{MD}$. Endurance: maximise $C_L/C_D$, $V=V_{MD}$. Reading the cruise pattern off the question decides the formula.

## 9. Effect of altitude on the optimum cruising speed

The minimum drag $D_{min}=2W\sqrt{KC_{D0}}$ is the same at every height, but $V_{MD}$ as a true airspeed rises as $1/\sqrt\sigma$ ([[SESA1015 M05 - Minimum Drag, Power and Performance Curves|M05]]), and the range-optimum speeds, being fixed multiples of $V_{MD}$, rise with it. The fuel burned per unit distance is $c_tD/V$, so at the optimum condition the fuel per kilometre falls as $\sqrt\sigma$: the same drag, and the same fuel per second, is spread over more kilometres.

For a business jet ($W=90$ kN, $C_D=0.02+0.045C_L^2$ as in the course notes, with $S=30$ m² assumed), $V_{MD}$ is 85.7 m/s at sea level and 157.3 m/s at 11 km. The cruise-climb optimum $2^{1/4}V_{MD}$ is then 101.9 m/s at sea level and 187.0 m/s at 11 km, which is $M=187.0/295.0=0.63$. At the higher altitude the aircraft covers 1.83 times the distance per kilogram of fuel at its optimum. A jet should therefore cruise as high as it can, at $2^{1/4}V_{MD}$ for the cruise-climb, provided the resulting Mach number stays below the drag rise; the speed of sound falls with temperature through the troposphere, so that limit tightens as the aircraft climbs. For a wing loading as high as a transport's, the incompressible optimum is beyond the drag rise, and compressibility, not the parabolic polar, sets the cruise Mach number ([[SESA1015 M07 - Propeller Aircraft Range and Endurance|M07]]).

## 10. Worked examples

### Specific fuel consumption for a 7041 km cruise

An aircraft with span 34.1 m, $AR=9.5$ and wing loading 5880 N/m² cruises at $M=0.79$ in the lower stratosphere, where $T=216.66$ K and $\rho=0.3648$ kg/m³. It carries 18 000 kg of fuel for the cruise and $C_D=0.018+0.045C_L^2$. Find the specific fuel consumption needed for a cruise of 7041 km at constant Mach number (Slides v2, pp. 114–116).

Geometry and weights, taking the wing loading as the start-of-cruise value so that it includes the fuel:

$$
\begin{aligned}
S&=\frac{34.1^2}{9.5}=122.40\ \text{m}^2,\qquad W_1=5880\times122.40=719\,718\ \text{N},\\
W_f&=18\,000\times9.81=176\,580\ \text{N},\qquad W_2=W_1-W_f=543\,138\ \text{N}.
\end{aligned}
$$

Speed and coefficients:

$$
\begin{aligned}
a&=\sqrt{1.4\times287\times216.66}=295.05\ \text{m/s},\qquad V=0.79\times295.05=233.09\ \text{m/s},\\
C_L&=\frac{2(5880)}{0.3648(233.09)^2}=0.5933,\qquad C_D=0.018+0.045(0.5933)^2=0.03384,\\
\frac LD&=17.53,\qquad\ln\frac{W_1}{W_2}=\ln1.3251=0.2815 .
\end{aligned}
$$

Constant Mach number in the stratosphere is constant speed, so the Breguet equation applies; rearranged for $c_t$,

$$
c_t=\frac{V}{R}\frac{L}{D}\ln\frac{W_1}{W_2}=\frac{233.09\times17.53\times0.2815}{7\,041\,000}=1.634\times10^{-4}\ \text{s}^{-1},
$$

that is 0.588 N of fuel per hour per newton of thrust. The aircraft climbs by $6338\ln1.3251=1784$ m during the cruise.

> [!check] Where this aircraft sits on its polar
> $C_{L,MD}=\sqrt{0.018/0.045}=0.632$, so the cruise $C_L=0.593$ is just below it and $L/D=17.53$ is within 0.2 % of $(L/D)_{max}=17.57$. The incompressible range optimum would need $C_L=0.632/\sqrt3=0.365$, a speed of $3^{1/4}\times225.8=297$ m/s, or $M=1.01$ at this height: far beyond the drag rise. The aircraft cruises as fast as compressibility allows and accepts a $C_L$ close to minimum drag.

### Endurance and constant-altitude range of the same aircraft

With the same fuel, $c_t$ and $C_L$, the endurance is

$$
E=\frac{1}{1.634\times10^{-4}}\times17.53\times0.2815=30\,210\ \text{s}=8.39\ \text{h},
$$

and at $(L/D)_{max}=17.57$ it would be 8.41 h. If instead the height is held at $\rho=0.3648$ kg/m³ with the same $C_L$ and starting speed,

$$
R=\frac{2}{1.634\times10^{-4}}\sqrt{\frac{2}{0.3648\times122.40}}\;\frac{0.5933^{1/2}}{0.03384}\left(\sqrt{719\,718}-\sqrt{543\,138}\right)=6568\ \text{km},
$$

ending at $233.09\sqrt{543\,138/719\,718}=202.5$ m/s. The ratio $6568/7041=0.933$ agrees with $2(1-\sqrt{0.7547})/\ln1.3251$.

### Height gained in one hour of cruise-climb

The same aircraft starts a cruise-climb at sea level with $C_L=0.593$ and $c_t=1.6319\times10^{-4}$ s⁻¹. Find its altitude after one hour (Slides v2, pp. 118–119).

$$
\begin{aligned}
C_D&=0.018+0.045(0.593)^2=0.03382,\qquad\frac{C_D}{C_L}=0.05704,\\
\frac{\sigma_2}{\sigma_1}&=\exp(-1.6319\times10^{-4}\times0.05704\times3600)=e^{-0.03351}=0.9670 .
\end{aligned}
$$

In the troposphere, with $T_{SL}=288$ K, $c_0=0.0065$ K/m and $n=4.253$:

$$
h=\frac{288}{0.0065}\left(1-0.9670^{1/4.253}\right)=44\,308\times0.007858=348\ \text{m}.
$$

The aircraft has burned 3.3 % of its weight and climbed about 350 m. A continuous climb of this kind can clash with the fixed flight levels of busy airspace, and it changes the cabin pressure schedule.

## Links

- Parent: [[SESA1015 Intro to Aero & Astro Hub]] · Solutions: [[SESA1015 T04 - Range and Endurance Solutions]]
- Previous: [[SESA1015 M05 - Minimum Drag, Power and Performance Curves]] · Next: [[SESA1015 M07 - Propeller Aircraft Range and Endurance]] (power-specific engines, compressibility, the summary of cruise techniques)
- Builds on: [[SESA1015 M01 - Atmosphere, Airspeed and Mach Number]] (stratosphere, speed of sound), [[SESA1015 M03 - Aerodynamic Characteristics and the Drag Polar]]
- Concepts: [[Cruise-Climb]] · [[Breguet Range Equation]] · [[Thrust Specific Fuel Consumption]] · [[Minimum Drag and Minimum Power]] · [[Parabolic Drag Polar]]
- Later in the degree: [[SESA2023 W01 - Thrust, Efficiency, Range and the ISA]] (the Breguet equation with overall efficiency and calorific value), [[Thermal and Overall Efficiency]], [[Propulsive Efficiency]], [[SESA2022 T5 - Finite Wing Theory]] (how aspect ratio raises $L/D$)

## Sources

- Mechanics of Flight Course Notes (Keane, October 2020): §5 introduction and endurance (pp. 25–26), §5.1 Range (pp. 26–27), §5.2 Range in the stratosphere (p. 27), §5.3 Cruise-climb (pp. 28–29), §5.4 Maximising the Breguet range (pp. 29–30), §5.5 Effect of altitude on optimum cruising speed (p. 30), §6 introduction, range at constant altitude and angle of attack (pp. 31–32), §6.3.1 (p. 35)
- Mechanics of Flight Lecture Slides version 2: thrust-specific propulsion (p. 69), mission profiles (p. 72), fuel bookkeeping and endurance (pp. 112–113), range and worked example (pp. 114–116), summary (p. 117), cruise-climb example (pp. 118–119), maximising cruise-climb range (pp. 120–121), cruise rubric (p. 130)

## Self-study tasks

### Core

- [ ] Revision Q5: jet range in the stratosphere with constant $L/D$. → [[SESA1015 T04 - Range and Endurance Solutions#Question 5]] · [[#4. Range at constant speed - the Breguet range equation]]
- [ ] Revision Q16: specific fuel consumption required for a 3899 nm cruise. → [[SESA1015 T04 - Range and Endurance Solutions#Question 16]] · [[#Specific fuel consumption for a 7041 km cruise]]
- [ ] Revision Q29: range at constant altitude (square-root formula). → [[SESA1015 T04 - Range and Endurance Solutions#Question 29]] · [[#7. Range at constant altitude]]
- [ ] Slides v2, p. 114: the specific fuel consumption for 7041 km, deriving the range equation first. → [[#Specific fuel consumption for a 7041 km cruise]]
- [ ] Slides v2, p. 118: height after one hour of cruise-climb from sea level. → [[#Height gained in one hour of cruise-climb]]

### Further practice

- [ ] Find the weight fraction for a 5000 km cruise followed by a 30 minute loiter for the 7041 km aircraft, and the fuel burned between 2000 ft steps of a step climb in the stratosphere (Slides v2, p. 72; suggested, not lecturer-set). → [[#Mission profiles and the step climb]]
- [ ] Revision Q20: flight-time difference at fixed Mach number between summer and winter temperatures. → [[SESA1015 T04 - Range and Endurance Solutions#Question 20]] · [[#5. Range in the stratosphere]]
- [ ] Derive both cruise-climb optima, $2^{1/4}V_{MD}$ at fixed engine setting and $3^{1/4}V_{MD}$ with the speed fixed at the start (Slides v2, pp. 120–121). → [[#Cruise-climb - two ways to fix the speed]]
- [ ] Show that the constant-altitude range is $2(1-\sqrt{W_2/W_1})/\ln(W_1/W_2)$ times the cruise-climb range from the same start, and expand it for a small fuel fraction. → [[#Comparison with the cruise-climb]]

## Transcript and slide slips

> [!warning] Slide slip (Slides v2, p. 116)
> Where: [[#Specific fuel consumption for a 7041 km cruise]].
>
> The slide's answer is $c_t=1.6319\times10^{-4}$ N s⁻¹ N⁻¹, and the same value is reused on p. 118. The slide's own intermediate values ($V=233.1$ m/s, $C_L=0.5933$, $C_D=0.03384$, $W_1=719\,718$ N, $W_s=543\,138$ N, $R=7\,041\,000$ m) give $c_t=1.6338\times10^{-4}$ s⁻¹. The difference (0.1 %) does not change the 350 m answer on p. 119.
