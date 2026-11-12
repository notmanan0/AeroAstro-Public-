---
title: "SESA1015 M04 - Steady Level Flight and Stall"
module: "SESA1015 Intro to Aero & Astro"
type: topic
stream: "Mechanics of Flight"
order: 4
tags:
  - sesa1015
  - mechanics-of-flight
  - level-flight
  - stall
  - performance
aliases: ["SESA1015 Mechanics 4", "Level Flight and Stall", "Steady Level Flight"]
date: 2026-09-27
status: lectured
coverage: "Course notes §4.1–4.3 (equilibrium of forces and moments, stalling speed, level flight speeds and the quadratic in V squared); Lecture Slides v2 pp. 73–76 (equilibrium, stall speed, aerodynamic and flight stall), 78 (drag in level flight), 88–94 (thrust required and available, minimum and maximum speeds, effect of altitude, worked example)"
parent: ["[[SESA1015 Intro to Aero & Astro Hub]]"]
prerequisites: ["[[SESA1015 M01 - Atmosphere, Airspeed and Mach Number]]", "[[SESA1015 M03 - Aerodynamic Characteristics and the Drag Polar]]"]
next_topics: ["[[SESA1015 M05 - Minimum Drag, Power and Performance Curves]]"]
key_concepts: ["[[Stalling Speed]]", "[[Wing Loading]]", "[[Parabolic Drag Polar]]", "[[Airspeed Measures]]"]
tutorial_sheets: ["[[SESA1015 T01 - Stall and Level-Flight Solutions]]"]
sources: ["02 - Sources/Mechanics of Flight/Mechanics of Flight - Course Notes.pdf (§4.1–4.3, pp. 19–22)", "02 - Sources/Mechanics of Flight/Mechanics of Flight - Lecture Slides version 2.pdf (pp. 73–94)", "04 - Labs & Coursework/Revision & Spreadsheets/SESA1015 - Revision Questions (Original).xlsx (Q1, Q2, Q4, Q30, Q40, Q42)"]
---

# SESA1015 M04 - Steady Level Flight and Stall

> [!abstract] Summary
> In steady level flight lift balances weight and thrust balances drag. Lift balance fixes the lift coefficient at each speed, $C_L=2W/\rho V^2S$, so the slowest possible level speed is the stalling speed $V_S=\sqrt{2W/\rho SC_{L\max}}$, which rises with wing loading and altitude (in true airspeed) but is constant in equivalent airspeed. Substituting the parabolic polar gives the drag as $D=AV^2+B/V^2$, and setting $T=D$ gives a quadratic in $V^2$ whose two roots are the minimum and maximum level speeds for that thrust; there is no root when the thrust is below the minimum drag, which fixes the ceiling.

> [!summary]- Exam use: quick path
> - **Use it when:** a question asks for a stalling speed, the $C_L$ or angle needed at a speed, the effect of weight, wing loading, altitude or flaps on stall, or the level-flight speeds for a given thrust.
> - **Assumptions:** steady, level, unaccelerated flight; thrust along the flight path; all forces through the CG; parabolic polar $C_D=C_{D0}+KC_L^2$; jet thrust independent of speed at a fixed altitude and, if needed, proportional to $\sigma$.
> - **Method:** 1. Weight in newtons, $\rho=\sigma\rho_0$. 2. $C_L=2W/\rho V^2S$, or $V_S$ with $C_{L\max}$. 3. $A=\tfrac12\rho SC_{D0}$, $B=2KW^2/\rho S$. 4. $V^2=\big(T\pm\sqrt{T^2-4AB}\big)/2A$. 5. Reject a root below $V_S$; for EAS multiply true speeds by $\sqrt\sigma$.
> - **Common mistakes:** using the mass in kg as $W$; reporting the low-speed root without checking it against the stalling speed.
> - **Practise:** [[#Minimum and maximum level speeds of a light jet (Slides v2, pp. 90–94)]] · [[SESA1015 T01 - Stall and Level-Flight Solutions#Question 1]]

Steady level flight is the reference condition of aircraft performance: the cruise of almost every flight is close to it, and climb, glide, turns and take-off are all departures from it. The aircraft moves at constant speed and height, so there is no acceleration and the forces balance. Treating the aircraft as a point mass at the CG, four forces act: lift up, weight down, thrust forward and drag back, and for the aircraft not to pitch the moment about the CG must also be zero.

The vertical balance carries most of the content. For a given weight, wing area and air density, the speed alone decides how large the lift coefficient must be, and the lift coefficient decides the angle of attack through the lift curve of [[SESA1015 M03 - Aerodynamic Characteristics and the Drag Polar|M03]]. Flying more slowly needs more angle, and the angle cannot rise past the stall, so the maximum lift coefficient sets the slowest speed at which level flight is possible. The horizontal balance then says the engine must supply the drag at that speed; drag falls and then rises with speed, so a given thrust can usually hold level flight at two speeds.

---

## 1. Equilibrium of forces and moments

For steady level flight at speed $V$, with thrust aligned with the flight path and all forces acting through the CG (Notes §4.1, p. 19), equilibrium gives

$$
L=W,\qquad T=D,\qquad M_{CG}=0,
$$

with $M_{CG}$ positive nose up. The first two are used below; for the third, trim, see [[SESA1015 M11 - Longitudinal Trim and Static Stability|M11]].

![[mof_m04_level_flight_forces.png|800]]

With $L=\tfrac12\rho V^2SC_L$, where $S$ is the reference (gross wing) area, the lift balance reads

$$
\tfrac12\rho V^2SC_L=W .
$$

Read one way, this fixes the lift coefficient needed at speed $V$:

$$
C_L=\frac{2W}{\rho V^2S}.
$$

For a given weight and wing area at constant height, the speed determines $C_L$, and since $C_L$ is largely a function of angle of attack alone, the speed also determines $\alpha$. Read the other way, it gives the level-flight speed for a chosen $C_L$:

$$
\begin{aligned}
V^2&=\frac{2W}{\rho SC_L}\\
V&=\left(\frac{2W}{\rho SC_L}\right)^{1/2}=\left(\frac{2w}{\rho C_L}\right)^{1/2},
\end{aligned}
$$

where

$$
w=\frac WS
$$

is the **wing loading** (N/m²; [[Wing Loading]]). Larger $C_L$ means lower speed.

Dividing the thrust balance by the lift balance gives a useful ratio (Slides v2, p. 74):

$$
\frac TW=\frac DL=\frac{\tfrac12\rho V^2SC_D}{\tfrac12\rho V^2SC_L}=\frac{C_D}{C_L}.
$$

To stay airborne at a steady speed the thrust-to-weight ratio must equal the drag-to-lift ratio at the operating point.

![[mof_m04_cl_required_speed.png|850]]

The figure shows $C_L=2w/\rho V^2$ for $w=5000$ N/m². Each curve falls as $1/V^2$, and at altitude, where $\rho$ is smaller, the same $C_L$ needs a higher true airspeed. The cruise sits at $C_L$ of 0.2 to 0.5; the approach to land sits just below the landing-flap $C_{L\max}$ line. The DC-9-30 data (Notes p. 20) follow the same curves: a landing stall at about 50 m/s at sea level with 50° flap and slats, and a clean stall near 135 m/s at 9000 m.

## 2. Stalling speed

The **stalling speed** is the minimum speed at which the aircraft can fly level. It occurs where the lift coefficient needed for $L=W$ reaches its maximum, $C_L=C_{L\max}$ (Notes §4.2, pp. 19–20). Putting $C_L=C_{L\max}$ and $V=V_S$ in the lift balance,

$$
\begin{aligned}
W&=\tfrac12\rho V_S^2SC_{L\max}\\
V_S^2&=\frac{2W}{\rho SC_{L\max}}\\
V_S&=\left(\frac{2W}{\rho SC_{L\max}}\right)^{1/2}=\left(\frac{2w}{\rho C_{L\max}}\right)^{1/2}.
\end{aligned}
$$

This holds for steady level flight only: in a turn or pull-up the wing must carry more than $W$ and stalls at a higher speed ([[SESA1015 M10 - Turning Flight and Manoeuvre Performance|M10]]). See [[Stalling Speed]].

### Aerodynamic stall and flight stall

Aerodynamically, the stall is an angle-of-attack event: past $C_{L\max}$ the flow separates and $C_L$ falls as $\alpha$ rises, and that can happen at any speed if the angle is large enough. In flight terms the aircraft "stalls" when it can no longer produce $L=W$. The stalling speed links the two by assuming the pilot can hold the aircraft at the angle for $C_{L\max}$ (Slides v2, pp. 75–76). Operating there is costly: $C_{L\max}$ comes with high drag, and predicting $C_{L\max}$ reliably is difficult, which is why the measured stalling speed is the figure quoted in a pilot's manual.

### How the stalling speed scales

Every dependence follows from $V_S\propto\sqrt{w/\rho C_{L\max}}$, with the other quantities held fixed.

Weight: $V_S\propto\sqrt W$, so if the weight falls from $W_1$ to $W_2$ during a flight as fuel is burned,

$$
\frac{V_{S1}}{V_{S2}}=\sqrt{\frac{W_1}{W_2}} .
$$

Wing loading: $V_S\propto\sqrt w$. Two aircraft with the same stalling speed at the same density need $C_{L\max}$ in proportion to their wing loadings (Revision Q40, [[SESA1015 T02 - Take-off and Landing Solutions#Question 40]]):

$$
\frac{C_{L\max,B}}{C_{L\max,A}}=\frac{w_B}{w_A}.
$$

Configuration: $V_S\propto1/\sqrt{C_{L\max}}$. In the clean configuration, used in the cruise where low drag matters, $C_{L\max}\approx1.2$. For landing, the lowest possible speed is wanted together with high drag, so all high-lift devices are deployed fully, which can more than double $C_{L\max}$. Take-off uses partial deployment as a compromise between high lift and low drag (Notes §4.2, p. 20). Doubling $C_{L\max}$ cuts the stalling speed by a factor $\sqrt2$, about 29%.

Altitude: $V_S\propto1/\sqrt\rho$ in true airspeed, so the true stalling speed rises with altitude. In equivalent airspeed it does not change. From [[SESA1015 M01 - Atmosphere, Airspeed and Mach Number|M01]], $\rho V^2=\rho_0V_e^2$ ([[Airspeed Measures]]), so applying this at the stall,

$$
\begin{aligned}
\rho V_S^2&=\rho_0V_{e,S}^2\\
V_{e,S}&=V_S\sqrt{\frac{\rho}{\rho_0}}=\left(\frac{2W}{\rho SC_{L\max}}\cdot\frac{\rho}{\rho_0}\right)^{1/2}\\
&=\left(\frac{2W}{\rho_0SC_{L\max}}\right)^{1/2},
\end{aligned}
$$

which contains no altitude-dependent quantity. The airspeed indicator reads close to EAS at low Mach number, so a pilot sees the same stalling speed at every height for a given weight and configuration (Notes §4.2, p. 20; Slides v2, p. 75).

> [!tip] Stalling speed is a dynamic-pressure limit
> At fixed weight and configuration the stall occurs at a fixed dynamic pressure, $q_S=\tfrac12\rho V_S^2=w/C_{L\max}$. The true stalling speed therefore rises with altitude to keep $q$ fixed, while EAS, which measures $q$ directly, does not move.

## 3. Level flight speeds

### Drag as a function of speed

With the parabolic polar of [[SESA1015 M03 - Aerodynamic Characteristics and the Drag Polar|M03]],

$$
C_D=C_{D0}+KC_L^2,\qquad K=\frac{1}{\pi eAR},
$$

the drag in level flight is

$$
D=\tfrac12\rho V^2S\,C_D=\tfrac12\rho V^2S\left(C_{D0}+KC_L^2\right).
$$

The lift coefficient is not free: level flight fixes it at $C_L=2W/\rho V^2S$, so

$$
C_L^2=\frac{4W^2}{\rho^2V^4S^2}.
$$

Substituting and multiplying out,

$$
\begin{aligned}
D&=\tfrac12\rho V^2SC_{D0}+\tfrac12\rho V^2S\,K\,\frac{4W^2}{\rho^2V^4S^2}\\
&=\tfrac12\rho SC_{D0}\,V^2+\frac{2KW^2}{\rho S}\,\frac1{V^2}\\
&=AV^2+\frac{B}{V^2},
\end{aligned}
$$

with constants, for flight at a fixed altitude and weight (Notes §4.3, p. 21),

$$
A=\tfrac12\rho SC_{D0},\qquad B=\frac{2KW^2}{\rho S}=\frac{2W^2}{\pi eAR\,\rho S}.
$$

The term $AV^2$ is the profile drag, which rises with $V^2$; $B/V^2$ is the induced drag, which falls as $1/V^2$ because a faster aircraft needs a smaller $C_L$. Their sum, the total drag, is U-shaped with a minimum at the **minimum drag speed** $V_{MD}$ where the two parts are equal (finding $V_{MD}$ and $D_{min}$: [[SESA1015 M05 - Minimum Drag, Power and Performance Curves|M05]]). In steady level flight this drag is also the **thrust required**, since any excess thrust would accelerate the aircraft (Slides v2, p. 88).

### Thrust equals drag: a quadratic in the square of the speed

For a jet engine at a fixed altitude and r.p.m. setting the thrust is almost independent of speed (Notes §4.3, p. 21). Setting $T=D$,

$$
T=AV^2+\frac{B}{V^2}.
$$

Multiplying through by $V^2$ and rearranging,

$$
\begin{aligned}
TV^2&=AV^4+B\\
AV^4-TV^2+B&=0,
\end{aligned}
$$

which is a quadratic in $x=V^2$: $Ax^2-Tx+B=0$. The quadratic formula gives

$$
V^2=\frac{T\pm\sqrt{T^2-4AB}}{2A} .
$$

The two positive roots are the level-flight speeds $V_i$ (minus sign) and $V_{ii}$ (plus sign) for the chosen thrust. Both roots of $x$ are positive when they are real, because their product $B/A$ and their sum $T/A$ are both positive. The higher root $V_{ii}$ is the maximum level speed at that thrust. The lower root $V_i$ is the minimum speed, but it may be less than the stalling speed, in which case it is not attainable and the real minimum is $V_S$ (Notes §4.3, p. 21; Slides v2, p. 91).

![[mof_m04_thrust_drag_speeds.png|900]]

### When there is no solution

The roots are real only if the discriminant is not negative:

$$
T^2-4AB\ge0\quad\Longleftrightarrow\quad T\ge2\sqrt{AB} .
$$

Substituting the constants,

$$
\begin{aligned}
4AB&=4\cdot\tfrac12\rho SC_{D0}\cdot\frac{2KW^2}{\rho S}\\
&=4KC_{D0}W^2,\\
2\sqrt{AB}&=2W\sqrt{KC_{D0}} .
\end{aligned}
$$

This is the minimum drag $D_{min}$ derived in M05. Three cases follow: with $T>D_{min}$ there are two level speeds, one each side of $V_{MD}$; with $T=D_{min}$ the thrust line just touches the drag curve and the only level speed is $V_{MD}$; with $T<D_{min}$ the aircraft cannot fly level at any speed and must descend. Since $D_{min}$ is independent of density, the condition $T=D_{min}$ fixes the ceiling once the thrust is known as a function of height.

> [!check] The same roots from the lift coefficient
> Dividing $T=D$ by $W=L$ gives $T/W=C_D/C_L=(C_{D0}+KC_L^2)/C_L$, a quadratic in $C_L$: $KC_L^2-(T/W)C_L+C_{D0}=0$. Its roots are the lift coefficients at $V_{ii}$ and $V_i$, and its discriminant $(T/W)^2-4KC_{D0}\ge0$ is the same condition divided by $W^2$. For the light jet below it gives $C_L=0.154$ and $3.789$, and $V=\sqrt{2W/\rho SC_L}$ returns 92.84 and 18.74 m/s.

## 4. Effect of altitude and weight

### Altitude

At a fixed true airspeed, $A\propto\rho$ and $B\propto1/\rho$, so the drag curve moves with height: towards higher true speeds, with the same minimum value. In equivalent airspeed it does not move. Substituting $\rho V^2=\rho_0V_e^2$ in each term,

$$
\begin{aligned}
AV^2&=\tfrac12SC_{D0}\,\rho V^2=\tfrac12\rho_0SC_{D0}\,V_e^2,\\
\frac{B}{V^2}&=\frac{2KW^2}{S}\cdot\frac{1}{\rho V^2}=\frac{2KW^2}{\rho_0S}\cdot\frac1{V_e^2},
\end{aligned}
$$

so

$$
D=\tfrac12\rho_0SC_{D0}V_e^2+\frac{2KW^2}{\rho_0SV_e^2},
$$

which contains no altitude-dependent quantity. Plotted against EAS, one drag curve serves every altitude (Slides v2, pp. 91–92). The stalling speed in EAS is also fixed, so only the thrust changes with height. The simple model for a jet is that the available thrust falls in proportion to density (Slides v2, p. 91),

$$
T_{alt}=T_{SL}\,\frac{\rho}{\rho_{SL}}=T_{SL}\,\sigma .
$$

As the aircraft climbs, the thrust line drops down the fixed EAS drag curve: $V_{e,i}$ rises, $V_{e,ii}$ falls, and they meet at $V_{MD}$ when $T_{SL}\sigma=D_{min}$. That height is the **ceiling** for this simple model. Converting the EAS roots back to true airspeed with $V=V_e/\sqrt\sigma$ returns to the aerodynamic and propulsion picture (Slides v2, p. 93).

![[mof_m04_flight_envelope.png|800]]

### Weight

$A$ does not depend on weight and $B\propto W^2$. A heavier aircraft has more induced drag at every speed, a higher minimum drag ($D_{min}\propto W$), a higher minimum drag speed and a higher stalling speed (both $\propto\sqrt W$). For a jet with fixed thrust, the gap between $V_i$ and $V_{ii}$ narrows as weight grows, and the speed range and ceiling widen as fuel is burned.

## Worked examples

### Stalling speed of a light aircraft at two heights

A light aircraft has $m=1350$ kg and $S=16.25$ m². Taking $C_{L\max}=1.5$ (an assumed value for illustration), $W=1350\times9.81=13\,244$ N and $w=815.0$ N/m². At sea level,

$$
V_S=\left(\frac{2(13\,244)}{1.225(16.25)(1.5)}\right)^{1/2}=\sqrt{887.0}=29.78\ \text{m/s}.
$$

At 3050 m in the ISA, $\sigma=0.7382$, so

$$
V_S=\frac{29.78}{\sqrt{0.7382}}=34.67\ \text{m/s TAS},\qquad V_{e,S}=34.67\sqrt{0.7382}=29.78\ \text{m/s}.
$$

The true stalling speed is 16% higher at altitude and the equivalent stalling speed is unchanged. After burning fuel equal to 10% of the weight, $V_S$ at sea level falls by the factor $\sqrt{0.9}=0.9487$ to $28.26$ m/s.

### Minimum and maximum level speeds of a light jet (Slides v2, pp. 90–94)

The same aircraft has aspect ratio 7, $e=0.95$ and $C_{D0}=0.028$, and its jet engine gives 2500 N at sea level at all speeds. The maximum and minimum equivalent speeds at sea level and at 3050 m are wanted.

The induced drag factor is

$$
K=\frac{1}{\pi eAR}=\frac{1}{\pi(0.95)(7)}=0.04787 .
$$

At sea level the drag constants are

$$
\begin{aligned}
A&=\tfrac12(1.225)(16.25)(0.028)=0.2787\ \text{kg/m},\\
B&=\frac{2(0.04787)(13\,244)^2}{1.225(16.25)}=8.435\times10^5\ \text{N m}^2/\text{s}^2 .
\end{aligned}
$$

The discriminant is

$$
T^2-4AB=2500^2-9.403\times10^5=5.310\times10^6,\qquad\sqrt{\cdot}=2304.3\ \text{N},
$$

so

$$
\begin{aligned}
V_i^2&=\frac{2500-2304.3}{2(0.2787)}=351.1\ \Rightarrow\ V_i=18.74\ \text{m/s},\\
V_{ii}^2&=\frac{2500+2304.3}{2(0.2787)}=8619\ \Rightarrow\ V_{ii}=92.84\ \text{m/s}.
\end{aligned}
$$

At sea level these are also the equivalent airspeeds. The low root needs $C_L=2W/\rho V_i^2S=3.79$, far beyond any clean $C_{L\max}$, so it lies below the stall and the practical minimum is the stalling speed (29.8 m/s with the assumed $C_{L\max}=1.5$).

At 3050 m, $\sigma=0.7382$, $\rho=0.9043$ kg/m³ and $T=2500\sigma=1845.5$ N. Then $A=0.2057$, $B=1.1426\times10^6$ and

$$
\begin{aligned}
T^2-4AB&=1845.5^2-9.403\times10^5=2.465\times10^6,\qquad\sqrt{\cdot}=1570.2,\\
V_i^2&=\frac{1845.5-1570.2}{2(0.2057)}=669.1\ \Rightarrow\ V_i=25.87\ \text{m/s},\\
V_{ii}^2&=\frac{1845.5+1570.2}{2(0.2057)}=8302\ \Rightarrow\ V_{ii}=91.11\ \text{m/s}.
\end{aligned}
$$

In equivalent airspeed, $V_e=V\sqrt\sigma$:

$$
V_{e,i}=25.87\sqrt{0.7382}=22.22\ \text{m/s},\qquad V_{e,ii}=91.11\sqrt{0.7382}=78.28\ \text{m/s}.
$$

The product $4AB=4KC_{D0}W^2$ is the same at both heights, as Section 3 predicts. The maximum true speed has hardly changed, but the maximum EAS has fallen from 92.8 to 78.3 m/s, because the thrust has fallen while the EAS drag curve has not moved.

The ceiling follows from $T_{SL}\sigma=D_{min}=2W\sqrt{KC_{D0}}$:

$$
D_{min}=2(13\,244)\sqrt{0.04787(0.028)}=969.7\ \text{N},\qquad\sigma=\frac{969.7}{2500}=0.3879,
$$

which in the ISA troposphere is at about 8840 m.

> [!check] Recomputed
> Python with $g=9.81$, $\rho_0=1.225$ and the ISA $\sigma(3050)=0.73818$ gives $V_i=18.739$, $V_{ii}=92.841$ m/s at sea level and $25.866$, $91.113$ m/s TAS (22.224, 78.282 m/s EAS) at 3050 m; solving directly in EAS, with $\rho_0$ and $T=1845.45$ N, gives the same 22.224 and 78.282 m/s. Ceiling: $\sigma=0.38787$, $h=8839$ m. Rounded inputs as on Slides v2, p. 94 ($g=9.8$, $\rho=1.23$ and 0.91, $K=0.048$, $T=1850$ N) give the same answers to within 0.2%.

## Terminology and alternative names

| Course term | Also called | Note |
|---|---|---|
| stalling speed $V_S$ | stall speed, $V_{Stall}$, 1-g stall speed | valid for $L=W$ only |
| wing loading $w=W/S$ | | in N/m², weight not mass |
| thrust required | drag in level flight | $T_R=D$ |
| $V_i$, $V_{ii}$ | $V_{min}$, $V_{max}$ (Slides) | the two roots of $T=D$ |
| drag constants $A$, $B$ in $D=AV^2+B/V^2$ | $A'$, $B'$ (course notes) | the course notes keep $A$ for the aspect ratio |

## Links

- Parent: [[SESA1015 Intro to Aero & Astro Hub]] · Solutions: [[SESA1015 T01 - Stall and Level-Flight Solutions]]
- Previous: [[SESA1015 M03 - Aerodynamic Characteristics and the Drag Polar]] · Next: [[SESA1015 M05 - Minimum Drag, Power and Performance Curves]]
- Builds on: [[SESA1015 M01 - Atmosphere, Airspeed and Mach Number]] (density ratio, EAS)
- Used in: [[SESA1015 M09 - Take-off and Landing Performance]] ($V_2=1.2V_S$), [[SESA1015 M10 - Turning Flight and Manoeuvre Performance]] (stall in a turn), [[SESA1015 M12 - Aircraft Constraint Analysis]] (wing loading from the landing speed)
- Concepts: [[Stalling Speed]] · [[Wing Loading]] · [[Parabolic Drag Polar]] · [[Airspeed Measures]] · [[Minimum Drag and Minimum Power]] · [[Aerofoil Stall]]
- Later in the degree: [[SESA2022 T2 - Boundary Layers]] and [[Boundary Layer Separation]] (why $C_{L\max}$ exists), [[SESA2023 W01 - Thrust, Efficiency, Range and the ISA]] (real thrust variation with speed and height), [[SESA2027 A1 - Dynamic Systems and Aircraft Equations of Motion]] (equations of motion without the steady assumption)

## Sources

- Mechanics of Flight Course Notes (Keane, October 2020), §4.1–4.3, pp. 19–22, including the DC-9-30 lift-coefficient plot (p. 20) and the thrust and drag diagram (p. 22)
- Lecture Slides version 2: pp. 73–76 (equilibrium, stall speed, aerodynamic and flight stall), 78 (drag in level flight), 85–86 (drag-against-speed exercise), 88–94 (thrust required and available, minimum and maximum speeds, altitude, worked example)
- Revision workbook, Questions 1, 2, 4, 30, 42 ([[SESA1015 T01 - Stall and Level-Flight Solutions]]) and 40 ([[SESA1015 T02 - Take-off and Landing Solutions]])
- Every number in this note was recomputed in Python.

## Self-study tasks

### Core

- [ ] Revision Q1: new wing loading for a 14% lower stalling speed, and the true stalling speed at $\sigma=0.75$. → [[SESA1015 T01 - Stall and Level-Flight Solutions#Question 1]] · [[#How the stalling speed scales]]
- [ ] Revision Q40: required $C_{L\max}$ ratio for two wing loadings at the same stalling speed. → [[SESA1015 T02 - Take-off and Landing Solutions#Question 40]]
- [ ] Revision Q30: cruise wing loading from Mach number, density ratio and $C_L$. → [[SESA1015 T01 - Stall and Level-Flight Solutions#Question 30]]
- [ ] Revision Q42: lift-to-drag ratio from the lift balance. → [[SESA1015 T01 - Stall and Level-Flight Solutions#Question 42]]
- [ ] Minimum and maximum level speeds at sea level and 3050 m (Slides v2, pp. 90–94), deriving the quadratic first. → [[#Minimum and maximum level speeds of a light jet (Slides v2, pp. 90–94)]]

### Further practice

- [ ] Revision Q4: change in induced drag when the speed rises from 57 to 103 m/s. → [[SESA1015 T01 - Stall and Level-Flight Solutions#Question 4]]
- [ ] Revision Q2 (same wording as Q1, different spreadsheet inputs). → [[SESA1015 T01 - Stall and Level-Flight Solutions#Question 2]]
- [ ] Plot drag against speed for the light jet and check $V_{MD}$ and the two roots graphically (Slides v2, pp. 85–86 and 94). → [[#3. Level flight speeds]]

## Transcript and slide slips

> [!warning] Slide slip (Slides v2, p. 94)
> Where: [[#Minimum and maximum level speeds of a light jet (Slides v2, pp. 90–94)]].
>
> With the slide's own inputs ($W=13\,230$ N, $\rho=1.23$ kg/m³, $K=0.048$, $T=2500$ N) the quadratic gives $V_{min}=18.708$ m/s and $V_{max}=92.651$ m/s, against the printed 18.681 and 92.656 m/s; at altitude ($\rho=0.91$, $T=1850$ N) it gives 25.758 and 90.954 m/s against 25.779 and 90.937 m/s. The differences are in the third decimal place, which the question asks for.
