---
title: "SESA1015 M05 - Minimum Drag, Power and Performance Curves"
module: "SESA1015 Intro to Aero & Astro"
type: topic
stream: "Mechanics of Flight"
order: 5
tags:
  - sesa1015
  - mechanics-of-flight
  - minimum-drag
  - minimum-power
  - performance
aliases: ["SESA1015 Mechanics 5", "Minimum Drag and Power", "Power Required and Available"]
date: 2026-09-27
status: lectured
coverage: "Course notes §4.4–4.6 (minimum drag conditions, (L/D)max, power requirements); Slides v2 pp. 65–67 (air-breathing and rocket thrust from momentum, propeller power and power-specific consumption) and pp. 79–105 (minimum drag, thrust and power required and available, steady level flight rubric)"
parent: ["[[SESA1015 Intro to Aero & Astro Hub]]"]
prerequisites: ["[[SESA1015 M03 - Aerodynamic Characteristics and the Drag Polar]]", "[[SESA1015 M04 - Steady Level Flight and Stall]]"]
next_topics: ["[[SESA1015 M06 - Jet Aircraft Range and Endurance]]"]
key_concepts: ["[[Minimum Drag and Minimum Power]]", "[[Parabolic Drag Polar]]", "[[Maximum Lift-to-Drag Ratio]]", "[[Airspeed Measures]]"]
tutorial_sheets: ["[[SESA1015 T01 - Stall and Level-Flight Solutions]]"]
sources: ["02 - Sources/Mechanics of Flight/Mechanics of Flight - Course Notes.pdf (§4.4–4.6, pp. 22–24)", "02 - Sources/Mechanics of Flight/Mechanics of Flight - Lecture Slides version 2.pdf (pp. 65–67, 79–105)"]
---

# SESA1015 M05 - Minimum Drag, Power and Performance Curves

> [!abstract] Summary
> In steady level flight the drag is the sum of a profile part that grows as $V^2$ and an induced part that falls as $1/V^2$, so it has a minimum. At the minimum drag speed $V_{MD}=(B/A)^{1/4}$ the two parts are equal, $C_L=\sqrt{C_{D0}/K}$, and $D_{min}=2W\sqrt{KC_{D0}}$, which does not depend on altitude; $(L/D)_{max}=1/(2\sqrt{KC_{D0}})$. Power required is $DV$, and its minimum sits at the slower speed $V_{MP}=3^{-1/4}V_{MD}\approx0.76V_{MD}$, where induced drag is three times profile drag and $C_L=\sqrt{3}\,C_{L,MD}$. Comparing these requirement curves with thrust or power available gives the speed limits, the excess power for climb and the ceiling.

> [!summary]- Exam use: quick path
> - **Use it when:** a question asks for the speed or value of minimum drag or minimum power, $(L/D)_{max}$, the true or equivalent airspeed for either at a given height, or how these change with altitude or weight.
> - **Assumptions:** steady, straight, level flight ($L=W$, $T=D$); parabolic polar $C_D=C_{D0}+KC_L^2$ with constant $C_{D0}$ and $K$ (no compressibility); weight fixed for the calculation.
> - **Method:** 1. $K=1/(\pi eAR)$, $W=mg$. 2. $C_{L,MD}=\sqrt{C_{D0}/K}$ (or $C_{L,MP}=\sqrt{3C_{D0}/K}$). 3. $V=\sqrt{2W/(\rho SC_L)}$ with the true density; $V_e=V\sqrt\sigma$. 4. $D_{min}=2W\sqrt{KC_{D0}}$, $(L/D)_{max}=W/D_{min}$. 5. $P_{min}=\tfrac12\rho SV_{MP}^3(4C_{D0})$.
> - **Common mistakes:** taking minimum drag as minimum drag coefficient (it is maximum $C_L/C_D$); using the sea-level density for a true airspeed at altitude, or forgetting that $D_{min}$ does not change with height while $P_{min}$ does.
> - **Practise:** [[#Minimum drag and minimum power at two heights]] · [[SESA1015 T01 - Stall and Level-Flight Solutions#Question 14]]

An aircraft in level flight must make lift equal to its weight. Flying slowly, it needs a large lift coefficient, so it flies at a high angle of attack and pays a large induced drag, the drag that comes with producing lift. Flying fast, it needs only a small lift coefficient, but the profile drag (skin friction and pressure drag, the part present even at zero lift) grows with the dynamic pressure. Between these two regimes is a speed where the total drag is least. Thrust required is the same thing as drag, so that speed also needs the least thrust.

Power is force times speed, so the power required to overcome drag is $DV$. Slowing down a little below the minimum drag speed raises the drag only slightly while reducing $V$ in proportion, so the product $DV$ keeps falling for a while. The minimum power speed is therefore slower than the minimum drag speed. Which of the two matters depends on what the engine burns fuel in proportion to: a jet's fuel flow follows its thrust and a propeller engine's follows its power, which is why these two speeds are the endurance speeds of the two engine types ([[SESA1015 M06 - Jet Aircraft Range and Endurance|M06]], [[SESA1015 M07 - Propeller Aircraft Range and Endurance|M07]]).

Altitude changes the speeds but not the minimum drag. With less dense air the same lift needs a higher true airspeed, but the dynamic pressure, and so every force, is unchanged when the equivalent airspeed is unchanged. The minimum drag is reached at the same equivalent airspeed at every height, and at a higher true airspeed the higher the aircraft flies.

---

## 1. Drag in level flight as a function of speed

In steady level flight lift balances weight and thrust balances drag:

$$
L=W=\tfrac12\rho V^2SC_L,\qquad T=D=\tfrac12\rho V^2SC_D .
$$

The drag polar ([[Parabolic Drag Polar]], [[SESA1015 M03 - Aerodynamic Characteristics and the Drag Polar|M03]]) is

$$
C_D=C_{D0}+KC_L^2,\qquad K=\frac{1}{\pi eAR},
$$

where $C_{D0}$ is the zero-lift (profile) drag coefficient, $e$ the span efficiency factor and $AR$ the aspect ratio. In the course notes the same coefficient appears as $k=K/\pi A$, with $K$ there a planform factor (equal to $1/e$, exactly 1 for an elliptic wing) and $A$ the aspect ratio. From the lift equation, the lift coefficient needed at speed $V$ is

$$
C_L=\frac{2W}{\rho V^2S}.
$$

Substituting into the drag equation:

$$
\begin{aligned}
D&=\tfrac12\rho V^2S\left(C_{D0}+KC_L^2\right)\\
&=\tfrac12\rho V^2SC_{D0}+\tfrac12\rho V^2SK\left(\frac{2W}{\rho V^2S}\right)^2\\
&=\tfrac12\rho V^2SC_{D0}+\frac{2KW^2}{\rho V^2S}.
\end{aligned}
$$

At a fixed height and weight this is

$$
D=AV^2+\frac{B}{V^2},\qquad A=\tfrac12\rho SC_{D0},\qquad B=\frac{2KW^2}{\rho S}.
$$

The first term is the profile drag and the second the induced drag. (The course notes write the constants $A'$ and $B'$ so that $A$ stays free for the aspect ratio.) Both are constant only for a given height (through $\rho$) and weight (through $W$, which enters $B$ squared).

![[mof_m05_drag_components.png|900]]

## 2. Minimum drag speed and minimum drag

### Differentiating with respect to speed

At the minimum of $D(V)$ the slope is zero:

$$
\begin{aligned}
\frac{dD}{dV}&=2AV-\frac{2B}{V^3}=0\\
AV^4&=B\\
V_{MD}&=\left(\frac{B}{A}\right)^{1/4}.
\end{aligned}
$$

The second derivative, $d^2D/dV^2=2A+6B/V^4$, is positive for every $V$, so this stationary point is a minimum (and the only one for $V>0$). $V_{MD}$ is the **minimum drag speed**.

The condition $AV^4=B$ divided by $V^2$ reads $AV^2=B/V^2$: **at the minimum drag speed the profile drag equals the induced drag**. In coefficients, dividing $\tfrac12\rho V^2SC_{D0}=\tfrac12\rho V^2SKC_L^2$ by $\tfrac12\rho V^2S$,

$$
C_{D0}=KC_L^2 .
$$

Substituting the constants gives the speed in terms of the aircraft:

$$
\begin{aligned}
V_{MD}^4&=\frac{B}{A}=\frac{2KW^2/(\rho S)}{\tfrac12\rho SC_{D0}}=\left(\frac{2W}{\rho S}\right)^2\frac{K}{C_{D0}}\\
V_{MD}&=\sqrt{\frac{2W}{\rho S}}\left(\frac{K}{C_{D0}}\right)^{1/4}.
\end{aligned}
$$

### Minimum drag in terms of the aircraft

Substituting $V_{MD}^2=\sqrt{B/A}$ back into $D$:

$$
\begin{aligned}
D_{min}&=A\sqrt{\frac BA}+\frac{B}{\sqrt{B/A}}\\
&=\sqrt{AB}+\sqrt{AB}\\
&=2\sqrt{AB}.
\end{aligned}
$$

Each part is $\sqrt{AB}$, half the total. With the constants written out,

$$
\begin{aligned}
AB&=\tfrac12\rho SC_{D0}\cdot\frac{2KW^2}{\rho S}=KC_{D0}W^2\\
D_{min}&=2W\sqrt{KC_{D0}} .
\end{aligned}
$$

The density has cancelled: **the minimum drag does not depend on altitude**. It is proportional to weight, and it falls as $C_{D0}$ or $K$ falls; a cleaner aircraft or a longer span reduces it.

### Lift and drag coefficients at minimum drag

From $C_{D0}=KC_L^2$,

$$
C_{L,MD}=\sqrt{\frac{C_{D0}}{K}},\qquad C_{D,MD}=C_{D0}+KC_{L,MD}^2=2C_{D0}.
$$

The speed then follows from the lift equation with this coefficient,

$$
V_{MD}=\sqrt{\frac{2W}{\rho SC_{L,MD}}},
$$

which is the same expression as above, since $1/\sqrt{C_{L,MD}}=(K/C_{D0})^{1/4}$.

The same result comes from the coefficients alone. Since $D=W\,C_D/C_L$ with $W$ fixed, minimum drag means minimum $C_D/C_L$:

$$
\begin{aligned}
\frac{C_D}{C_L}&=\frac{C_{D0}}{C_L}+KC_L\\
\frac{d}{dC_L}\left(\frac{C_D}{C_L}\right)&=-\frac{C_{D0}}{C_L^2}+K=0\\
C_L^2&=\frac{C_{D0}}{K}.
\end{aligned}
$$

Minimum drag is therefore not the minimum drag coefficient. The smallest $C_D$ is $C_{D0}$, at zero lift, where the aircraft cannot fly level at all; minimum drag occurs at maximum $C_L/C_D$.

### The tangent to the drag polar

On a plot of $C_L$ against $C_D$, the ratio $C_L/C_D$ at any point is the slope of the line from the origin to that point. The steepest such line just touches the polar, so the tangent from the origin marks the minimum drag condition, with $C_L=C_{L,MD}$ and $C_D=2C_{D0}$. The other two optima marked on the figure, maximum $C_L^{1/2}/C_D$ and maximum $C_L^{3/2}/C_D$, are the jet-range and minimum-power conditions derived in [[#Minimum power through the lift coefficient]] and in [[SESA1015 M06 - Jet Aircraft Range and Endurance|M06]].

![[mof_m05_polar_tangent.png|900]]

## 3. Maximum lift-to-drag ratio

In level flight $L=W$, and $L/D=W/D$ is largest where $D$ is smallest:

$$
\begin{aligned}
\left(\frac LD\right)_{max}&=\frac{W}{D_{min}}=\frac{W}{2W\sqrt{KC_{D0}}}\\
&=\frac{1}{2\sqrt{KC_{D0}}}=\frac12\sqrt{\frac{\pi eAR}{C_{D0}}}.
\end{aligned}
$$

It depends only on the aerodynamic design: it rises with the square root of the aspect ratio and falls with the square root of the zero-lift drag. It is independent of weight, height and speed, although the speed at which it is reached depends on all three. Finite-wing theory gives the same result ([[Maximum Lift-to-Drag Ratio]], Year 2).

> [!tip] One number, several uses
> $(L/D)_{max}$ is the best still-air glide ratio ([[SESA1015 M08 - Glide and Climb Performance|M08]]), sets the jet endurance ([[SESA1015 M06 - Jet Aircraft Range and Endurance|M06]]) and the propeller range ([[SESA1015 M07 - Propeller Aircraft Range and Endurance|M07]]). Halving $C_{D0}$ raises it by a factor $\sqrt2$, as does doubling $\pi eAR$.

## 4. Effect of altitude on drag

The minimum drag speed is a true airspeed and depends on the density:

$$
V_{MD}=\sqrt{\frac{2W}{\rho SC_{L,MD}}}\propto\frac{1}{\sqrt\rho}.
$$

The equivalent airspeed ([[Airspeed Measures]], [[SESA1015 M01 - Atmosphere, Airspeed and Mach Number|M01]]) is $V_e=V\sqrt{\rho/\rho_{SL}}=V\sqrt\sigma$, so

$$
V_{e,MD}=\sqrt{\frac{2W}{\rho_{SL}SC_{L,MD}}},
$$

which contains no altitude at all. Writing the drag in terms of $V_e$ shows why: $\tfrac12\rho V^2=\tfrac12\rho_{SL}V_e^2$, so

$$
D=\tfrac12\rho_{SL}V_e^2SC_{D0}+\frac{2KW^2}{\rho_{SL}V_e^2S},
$$

one curve for all heights. On true-airspeed axes the drag curve keeps the same minimum value $D_{min}$ but slides to higher speeds as the aircraft climbs, by the factor $1/\sqrt\sigma$. A pilot who holds the indicated (equivalent) airspeed for minimum drag holds minimum drag at every height.

The figure shows a business jet of weight 90 kN with $C_D=0.02+0.045C_L^2$. The wing area is not specified; $S=30$ m² reproduces the sea-level minimum-drag speed of that example. The minimum drag is $2(90\,000)\sqrt{0.045\times0.02}=5400$ N at both heights, while $V_{MD}$ rises from 85.7 m/s at sea level to 157 m/s at 11 km ($\rho=0.3639$ kg/m³). The thrust available from a jet engine falls roughly in proportion to density, $T_{alt}=T_{SL}\,\sigma$, so at 11 km both curves are far lower.

![[mof_m05_altitude_drag.png|900]]

Since a jet's fuel flow is roughly proportional to its thrust, flying at a given true airspeed costs much less fuel at high altitude, where that speed lies near the minimum of the drag curve, than at sea level, where it lies far up the profile-drag branch. The gain stops at the drag-rise Mach number: the speed of sound falls with temperature as the aircraft climbs through the troposphere, so a fixed true airspeed is a rising Mach number, and beyond the drag rise the polar no longer holds. This is the reason jet transports cruise high and fast, taken further in [[SESA1015 M06 - Jet Aircraft Range and Endurance|M06]].

## 5. Power required

The power needed to overcome the drag is the rate of doing work against it, the drag force times the distance moved per unit time:

$$
P_R=DV=AV^3+\frac{B}{V}.
$$

### Minimum power speed

Setting the slope to zero:

$$
\begin{aligned}
\frac{dP_R}{dV}&=3AV^2-\frac{B}{V^2}=0\\
3AV^4&=B\\
V_{MP}&=\left(\frac{B}{3A}\right)^{1/4}=\frac{1}{3^{1/4}}\left(\frac BA\right)^{1/4}=\frac{V_{MD}}{3^{1/4}}\approx0.760\,V_{MD}.
\end{aligned}
$$

The second derivative $6AV+2B/V^3$ is positive, so this is the minimum. Dividing $3AV^4=B$ by $V^2$ gives $3AV^2=B/V^2$: **at the minimum power speed the induced drag is three times the profile drag**. The aircraft flies slower than $V_{MD}$, on the induced-drag side of the drag curve.

### Minimum power through the lift coefficient

Writing the power with $D=W\,C_D/C_L$ and $V=\sqrt{2W/(\rho SC_L)}$:

$$
\begin{aligned}
P_R&=W\frac{C_D}{C_L}\sqrt{\frac{2W}{\rho SC_L}}\\
&=\sqrt{\frac{2W^3}{\rho S}}\;\frac{C_D}{C_L^{3/2}} .
\end{aligned}
$$

For a given aircraft at a given weight and height, the power is least when $C_D/C_L^{3/2}$ is least, that is, when $C_L^{3/2}/C_D$ is greatest. With $C_D=C_{D0}+KC_L^2$, differentiate by the quotient rule:

$$
\begin{aligned}
\frac{d}{dC_L}\left(\frac{C_{D0}+KC_L^2}{C_L^{3/2}}\right)&=\frac{C_L^{3/2}(2KC_L)-(C_{D0}+KC_L^2)\tfrac32C_L^{1/2}}{C_L^3}\\
&=\frac{C_L^{1/2}\left(2KC_L^2-\tfrac32C_{D0}-\tfrac32KC_L^2\right)}{C_L^3}\\
&=\frac{KC_L^2-3C_{D0}}{2C_L^{5/2}}=0 .
\end{aligned}
$$

So

$$
KC_L^2=3C_{D0},\qquad C_{L,MP}=\sqrt{\frac{3C_{D0}}{K}}=\sqrt3\,C_{L,MD},\qquad C_{D,MP}=C_{D0}+3C_{D0}=4C_{D0}.
$$

$KC_L^2=3C_{D0}$ is the coefficient form of "induced drag is three times profile drag". Since $V\propto C_L^{-1/2}$ at fixed weight and density, $V_{MP}/V_{MD}=(C_{L,MD}/C_{L,MP})^{1/2}=3^{-1/4}$, as before.

The drag at minimum power is $D_{MP}=W\,C_{D,MP}/C_{L,MP}=W\cdot4C_{D0}\big/\sqrt{3C_{D0}/K}=\tfrac{4}{\sqrt3}W\sqrt{KC_{D0}}$, so

$$
D_{MP}=\frac{2}{\sqrt3}D_{min}\approx1.155\,D_{min},\qquad P_{min}=D_{MP}V_{MP}=\frac{2}{\sqrt3}\cdot\frac{1}{3^{1/4}}D_{min}V_{MD}\approx0.877\,D_{min}V_{MD}.
$$

Flying at $V_{MP}$ costs about 15 % more drag than at $V_{MD}$ but saves about 12 % of the power. A convenient form for numbers is

$$
P_{min}=\tfrac12\rho SV_{MP}^3\,C_{D,MP}=2\rho SV_{MP}^3C_{D0}.
$$

### Minimum power and altitude

Unlike the minimum drag, the minimum power depends on height. In $P_R=\sqrt{2W^3/(\rho S)}\,C_D/C_L^{3/2}$ the optimum coefficient ratio is fixed, so

$$
P_{min}\propto\frac{1}{\sqrt\rho},\qquad P_{min,alt}=\frac{P_{min,SL}}{\sqrt\sigma}.
$$

The drag at $V_{MP}$ is the same at every height, but it is overcome at a true airspeed that is higher by $1/\sqrt\sigma$. More generally, at the same equivalent airspeed the drag is the same and $P_{alt}=DV=DV_e/\sqrt\sigma=P_{SL}/\sqrt\sigma$, so plotting power against equivalent airspeed does not collapse the curves for different heights the way it does for drag.

On a plot of $P_R$ against $V$, the line from the origin to any point on the curve has slope $P_R/V=D$. The shallowest line that still touches the curve is the tangent from the origin, and it touches at minimum drag; its slope is $D_{min}$, which is the same at every height, so one tangent line serves both curves in the figure. The lowest point of each curve is $V_{MP}$.

![[mof_m05_power_curves.png|900]]

## 6. Thrust available and power available

The requirement curves describe the airframe. The engine supplies **thrust available** $T_A$ or **power available** $P_A$, and steady level flight is possible wherever the available curve is at or above the required curve. Two simple engine models are used throughout (origins: [[#Thrust as the rate of change of momentum]] and [[#Propeller and jet: power or thrust roughly constant]]).

A jet engine is modelled with thrust independent of speed at a given throttle setting and height, falling with density, $T_{alt}=T_{SL}\,\sigma$. Its power available $P_A=TV$ is then a straight line through the origin: zero speed means zero power. A propeller engine (piston, turboprop or electric) is modelled with power independent of speed, $P_A=\eta P_S$, where $P_S$ is the shaft power and $\eta$ the efficiency of the propeller and transmission. Its thrust $T=P_A/V$ then becomes very large at low speed.

For the jet, $T=AV^2+B/V^2$ gives a quadratic in $V^2$,

$$
AV^4-TV^2+B=0\quad\Rightarrow\quad V^2=\frac{T\pm\sqrt{T^2-4AB}}{2A},
$$

whose two roots are the minimum and maximum level-flight speeds at that thrust (the lower may be below the stall speed; derivation and examples: [[SESA1015 M04 - Steady Level Flight and Stall|M04]]). For the propeller, $P_A=AV^3+B/V$ gives the quartic $AV^4-P_AV+B=0$, solved numerically. In the right-hand panel above, the jet with $T=2500$ N meets the power-required curve at 18.7 and 92.7 m/s, and a propeller with $P_A=75$ kW meets it at 60.2 m/s (the other real root, 11.2 m/s, lies below any realistic stall speed).

The vertical gap between the curves is the margin for anything other than level flight. Excess thrust $T_A-D$ sets the climb angle and excess power $P_A-P_R$ sets the rate of climb, $\text{RoC}=(P_A-P_R)/W$ ([[SESA1015 M08 - Glide and Climb Performance|M08]]). Read gaps vertically at one speed, never horizontally.

As height increases, the jet's thrust falls as $\sigma$ while $D_{min}$ stays fixed, so the two speeds close in on each other. They meet when the maximum thrust equals $D_{min}$; above that height level flight is impossible. That height is the **absolute ceiling** for the jet model,

$$
\sigma_{ceiling}=\frac{D_{min}}{T_{SL}} .
$$

### Thrust as the rate of change of momentum

An air-breathing propulsion system, whether piston-propeller, turboprop, turbofan, turbojet or open rotor, has a power source (mechanical or electrical) and a propulsor (propeller, fan or the engine's own jet) that does work on the air passing through it and increases its momentum. The thrust is the rate of change of that momentum:

$$
T=\frac{d}{dt}(mV)=m\frac{dV}{dt}+V\frac{dm}{dt}.
$$

For an engine running steadily the usable form comes from a control volume ([[SESA1016 T12 - Conservation of Momentum#One inlet, one outlet, uniform flow]], [[Momentum Flux]]). Take a control volume fixed to the engine, so that air enters at the flight speed $V_0$ and leaves at the jet speed $V_e$. Assume a steady mass flow $\dot m$, uniform velocity across the inlet and the exit, an exit pressure equal to ambient so that the pressure forces on the control volume cancel, and a fuel mass flow small enough to neglect. The net force on the air in the direction of flow is the momentum flux out minus the momentum flux in:

$$
\begin{aligned}
F_{\text{on air}}&=\dot mV_e-\dot mV_0\\
&=\dot m\left(V_e-V_0\right).
\end{aligned}
$$

The engine pushes the air rearwards with this force, so by Newton's third law the air pushes the engine forwards with

$$
T=\dot m\left(V_e-V_0\right).
$$

In the product-rule form above this is the mass processed per second, $dm/dt=\dot m$, times the velocity it gains. The fuel's mass flow and a nozzle exit pressure above ambient add two further terms, $T=(\dot m_a+\dot m_f)V_e-\dot m_aV_0+(p_e-p_a)A_e$ ([[Thrust Equation]], [[SESA2023 W01 - Thrust, Efficiency, Range and the ISA]]).

The same thrust can come from a large mass flow given a small velocity increase (a propeller or a high-bypass fan) or from a small mass flow given a large one (a turbojet). The difference is efficiency. The useful power is the thrust times the flight speed, $TV_0$, while the power put into the air is the rate at which its kinetic energy rises, $\tfrac12\dot m(V_e^2-V_0^2)$. Their ratio is the propulsive efficiency ([[Propulsive Efficiency]]):

$$
\begin{aligned}
\eta_p&=\frac{TV_0}{\tfrac12\dot m\left(V_e^2-V_0^2\right)}\\
&=\frac{\dot m\left(V_e-V_0\right)V_0}{\tfrac12\dot m\left(V_e-V_0\right)\left(V_e+V_0\right)}\\
&=\frac{2V_0}{V_e+V_0}=\frac{2}{1+V_e/V_0}.
\end{aligned}
$$

For $T=2500$ N at $V_0=100$ m/s, a propeller moving 250 kg/s of air needs $V_e-V_0=10$ m/s and has $\eta_p=0.952$, putting 262.5 kW into the air; a jet moving 12.5 kg/s needs $V_e-V_0=200$ m/s and has $\eta_p=0.50$, putting in 500 kW. Both deliver the same 250 kW of thrust power; the rest is left behind as kinetic energy in the wake.

A rocket carries both its fuel and its oxidiser, as solid or liquid propellant, and takes in no air. The combustion products leave the nozzle at an exhaust velocity $V_e$ relative to the vehicle, and the propellant had no velocity relative to the vehicle before it was burned, so there is no intake momentum to subtract. With $V_e$ constant, the product-rule form reduces to

$$
T=V_e\frac{dm}{dt},
$$

with $dm/dt$ the propellant mass flow (plus the pressure term $(p_e-p_a)A_e$, which grows as the ambient pressure falls). Rocket thrust does not depend on flight speed and works in a vacuum. Launch vehicles burn in several stages (momentum balance and rocket equation: [[SESA1015 A04 - Rocket Equation and Launch Performance|A04]]; staging: [[SESA1015 A05 - Staging and Payload Fraction|A05]]).

### Propeller and jet: power or thrust roughly constant

A piston engine or electric motor delivers a shaft power set by its rotational speed and, for a piston engine, its throttle setting; to a first approximation this does not depend on the flight speed. The propeller turns a fraction $\eta$ of it into thrust power, so

$$
\begin{aligned}
T_AV&=\eta P_S\\
T_A&=\frac{\eta P_S}{V},
\end{aligned}
$$

and the thrust available falls as $1/V$. With the $P_A=75$ kW of the figure above, $T_A=2500$ N at 30 m/s, 1250 N at 60 m/s and 833 N at 90 m/s. At 30 m/s the propeller matches the 2500 N jet, which is where the two power-available lines cross; below that speed it gives more thrust, above it less. The $1/V$ law cannot hold down to zero speed, since the static thrust of a real propeller is finite ([[Actuator Disk Theory]]).

For a turbojet, $T=\dot m(V_e-V_0)$ with $V_e-V_0$ falling as the flight speed rises, while ram compression in the intake raises the mass flow; over the subsonic range the two effects roughly cancel, which is the basis of the constant-thrust model. A high-bypass turbofan, with its large mass flow and small velocity increase, behaves partly like a propeller and loses some thrust as speed rises.

Fuel consumption follows the same split. A jet burns fuel in proportion to its thrust, measured by the thrust-specific consumption $c_t$ in s⁻¹ ([[SESA1015 M06 - Jet Aircraft Range and Endurance|M06]]). A propeller engine burns fuel in proportion to its power, measured by the power-specific consumption $c_p$, the weight of fuel used per second per watt in N/(s W), and an electric aircraft draws on a battery of specific energy $E^*$ in Wh/kg ([[SESA1015 M07 - Propeller Aircraft Range and Endurance|M07]], [[Power Specific Fuel Consumption]]).

## 7. Worked examples

### Minimum drag and minimum power at two heights

An aircraft has mass 1350 kg, $S=16.25$ m², $AR=7$, $e=0.95$ and $C_{D0}=0.028$. Find $(L/D)_{max}$, $D_{min}$, and the true and equivalent airspeeds for minimum drag and minimum power at sea level and at 3050 m, and the minimum power at both heights. The values used are $g=9.8$ m/s², $\rho_{SL}=1.23$ kg/m³, $T_{SL}=288$ K and lapse rate $c_0=0.0065$ K/m.

The weight and induced-drag factor are

$$
W=1350\times9.8=13\,230\ \text{N},\qquad K=\frac{1}{\pi(0.95)(7)}=0.04787 .
$$

The aerodynamic optimum:

$$
\begin{aligned}
\left(\frac LD\right)_{max}&=\frac{1}{2\sqrt{0.04787\times0.028}}=13.66,\\
D_{min}&=\frac{13\,230}{13.66}=969\ \text{N},\\
C_{L,MD}&=\sqrt{\frac{0.028}{0.04787}}=0.7648 .
\end{aligned}
$$

At 3050 m in the troposphere, $T=288-0.0065\times3050=268.2$ K, and with exponent $g/(c_0R)-1=9.8/(0.0065\times287)-1=4.253$,

$$
\sigma=\left(\frac{268.2}{288}\right)^{4.253}=0.7383,\qquad\rho=0.7383\times1.23=0.9082\ \text{kg/m}^3 .
$$

The minimum drag speeds:

$$
\begin{aligned}
V_{MD,SL}&=\sqrt{\frac{2(13\,230)}{1.23(16.25)(0.7648)}}=41.60\ \text{m/s},\\
V_{MD,3050}&=\sqrt{\frac{2(13\,230)}{0.9082(16.25)(0.7648)}}=48.42\ \text{m/s},\qquad V_{e,MD}=48.42\sqrt{0.7383}=41.60\ \text{m/s}.
\end{aligned}
$$

The minimum power speeds are $3^{-1/4}=0.7598$ times these: $V_{MP}=31.61$ m/s at sea level and $36.79$ m/s at 3050 m, both $V_e=31.61$ m/s. The minimum power, with $C_{D,MP}=4C_{D0}=0.112$:

$$
\begin{aligned}
P_{min,SL}&=\tfrac12(1.23)(16.25)(31.61)^3(0.112)=35.36\ \text{kW},\\
P_{min,3050}&=\tfrac12(0.9082)(16.25)(36.79)^3(0.112)=41.15\ \text{kW}.
\end{aligned}
$$

> [!check] Three cross-checks
> The ratio $41.15/35.36=1.164=1/\sqrt{0.7383}$, as $P_{min}\propto1/\sqrt\sigma$ requires. The drag at minimum power is $35\,359/31.61=1118.5$ N at both heights, which is $1.155\times969$. And $P_{min}=0.877\,D_{min}V_{MD}=0.877\times969\times41.60=35.36$ kW at sea level.

### Absolute ceiling of the jet version

If the same aircraft has a jet giving 2500 N at sea level at all speeds, with $T_{alt}=T_{SL}\sigma$, the ceiling is where $T_{alt}=D_{min}$:

$$
\sigma=\frac{969}{2500}=0.3875,\qquad\theta=0.3875^{1/4.253}=0.8002,\qquad h=\frac{288(1-0.8002)}{0.0065}=8850\ \text{m}.
$$

At that height the only possible level-flight speed is $V_{MD}=41.60/\sqrt{0.3875}=66.8$ m/s true airspeed.

## Links

- Parent: [[SESA1015 Intro to Aero & Astro Hub]] · Solutions: [[SESA1015 T01 - Stall and Level-Flight Solutions]]
- Previous: [[SESA1015 M04 - Steady Level Flight and Stall]] · Next: [[SESA1015 M06 - Jet Aircraft Range and Endurance]]
- Builds on: [[SESA1015 M03 - Aerodynamic Characteristics and the Drag Polar]] (the polar), [[SESA1015 M01 - Atmosphere, Airspeed and Mach Number]] (density ratio, equivalent airspeed), [[SESA1016 T12 - Conservation of Momentum]] (control-volume momentum balance behind the thrust equation)
- Used in: [[SESA1015 M07 - Propeller Aircraft Range and Endurance]] (endurance at $V_{MP}$, range at $V_{MD}$), [[SESA1015 M08 - Glide and Climb Performance]] (best glide, minimum sink, excess power)
- Concepts: [[Minimum Drag and Minimum Power]] · [[Parabolic Drag Polar]] · [[Airspeed Measures]] · [[Wing Loading]] · [[Thrust Equation]] · [[Propulsive Efficiency]] · [[Momentum Flux]] · [[Power Specific Fuel Consumption]]
- Later in the degree: [[Maximum Lift-to-Drag Ratio]] and [[SESA2022 T5 - Finite Wing Theory]] (where $K=1/(\pi eAR)$ comes from); [[SESA2023 W01 - Thrust, Efficiency, Range and the ISA]] (real thrust and power available)

## Sources

- Mechanics of Flight Course Notes (Keane, October 2020): §4.4 Minimum drag conditions (pp. 22–23), §4.5 $(L/D)_{max}$ and §4.6 Power requirements (p. 24), business-jet drag and thrust figure (p. 24)
- Mechanics of Flight Lecture Slides version 2: propulsion systems (pp. 65–67: air-breathing thrust $T=d(mV)/dt$, rocket thrust $T=V\,dm/dt$, propeller power constant, power-specific consumption and battery specific energy), minimum drag (pp. 79–87), thrust required and available (pp. 89–96), power required and available (pp. 97–104), steady level flight rubric (p. 105)

## Self-study tasks

### Core

- [ ] Revision Q15: true airspeed for minimum drag at a given density and wing loading. → [[SESA1015 T01 - Stall and Level-Flight Solutions#Question 15]] · [[#Lift and drag coefficients at minimum drag]]
- [ ] Revision Q14: minimum power speed at $\sigma=0.43$. → [[SESA1015 T01 - Stall and Level-Flight Solutions#Question 14]] · [[#Minimum power through the lift coefficient]]
- [ ] Slides v2, p. 78: $(L/D)_{max}$, $D_{min}$ and the true and equivalent minimum-drag speeds of the 1350 kg aircraft at sea level and 3050 m, deriving every relation. → [[#Minimum drag and minimum power at two heights]]
- [ ] Slides v2, p. 99: minimum power speed and minimum power at both heights for the same aircraft. → [[#Minimum drag and minimum power at two heights]]
- [ ] Derive $V_{MP}=3^{-1/4}V_{MD}$ two ways, from $dP/dV=0$ and from maximising $C_L^{3/2}/C_D$. → [[#Minimum power speed]] · [[#Minimum power through the lift coefficient]]
- [ ] Derive $T=\dot m(V_e-V_0)$ from a control volume round an engine and $\eta_p=2/(1+V_e/V_0)$, then compare a propeller and a jet giving 2500 N at 100 m/s (Slides v2, p. 65; suggested, not lecturer-set). → [[#Thrust as the rate of change of momentum]]

### Further practice

- [ ] For a propeller with $\eta P_S=75$ kW, plot $T_A=\eta P_S/V$ on the thrust-required curve of the 1350 kg aircraft and find the speed above which the 2500 N jet has more thrust (Slides v2, p. 67; suggested, not lecturer-set). → [[#Propeller and jet: power or thrust roughly constant]]
- [ ] Slides v2, pp. 86 and 103: plot drag and power required against speed for the 1350 kg aircraft and confirm the minima numerically. → [[#Minimum power and altitude]] (figure script `generate_mof_m05_figures.py`)
- [ ] Find the absolute ceiling of the jet version of the slide aircraft ($T_{SL}=2500$ N, $T\propto\sigma$). → [[#Absolute ceiling of the jet version]]
- [ ] Show that $P_{min}=2\cdot3^{-3/4}D_{min}V_{MD}$ and check it against the slide numbers. → [[#Minimum power through the lift coefficient]]
- [ ] Cambridge 3A1 questions on the power to overcome drag. → [[SESA1015 Cambridge Part IIA Practice#Minimum Drag, Power and Performance Curves]]

## Transcript and slide slips

> [!warning] Slide slip (Slides v2, p. 85)
> Where: [[#Minimum drag and minimum power at two heights]].
>
> The slide gives $(C_L/C_D)_{max}=13.657$ (from the exact $K=0.04787$) and then evaluates $D_{min}=13\,230/13.63$. The value 13.63 comes from the rounded $K=0.048$; with 13.657 the minimum drag is $968.7$ N. Both round to the slide's 969 N, so only the intermediate figure is inconsistent.
