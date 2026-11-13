---
title: "SESA1015 M01 - Atmosphere, Airspeed and Mach Number"
module: "SESA1015 Intro to Aero & Astro"
type: topic
stream: "Mechanics of Flight"
order: 1
tags:
  - sesa1015
  - mechanics-of-flight
  - atmosphere
  - airspeed
  - mach-number
aliases: ["SESA1015 Mechanics 1", "Atmosphere and Airspeed", "ISA and airspeed measurement"]
date: 2026-09-27
status: lectured
coverage: "Course notes §2.1–2.3 (International Standard Atmosphere, measurement of airspeed, Mach number); Slides v2 pp. 16–24 (hydrostatic derivation of the troposphere and lower-stratosphere relations, Bernoulli's equation, the compressible pitot relation, true, equivalent and indicated airspeed, worked examples at 1000 m)"
parent: ["[[SESA1015 Intro to Aero & Astro Hub]]"]
prerequisites: []
next_topics: ["[[SESA1015 M02 - Aircraft Geometry, Forces and Coefficients]]"]
key_concepts: ["[[Airspeed Measures]]", "[[Dynamic Pressure and Aerodynamic Coefficients]]", "[[International Standard Atmosphere]]", "[[Speed of Sound and Mach Number]]", "[[Stagnation Pressure and Pitot Tube]]"]
tutorial_sheets: ["[[SESA1015 T01 - Stall and Level-Flight Solutions]]", "[[SESA1015 T02 - Take-off and Landing Solutions]]", "[[SESA1015 T04 - Range and Endurance Solutions]]"]
sources: ["02 - Sources/Mechanics of Flight/Mechanics of Flight - Course Notes.pdf (§2.1–2.3, pp. 3–8)", "02 - Sources/Mechanics of Flight/Mechanics of Flight - Lecture Slides version 2.pdf (pp. 16–24)"]
---

# SESA1015 M01 - Atmosphere, Airspeed and Mach Number

> [!abstract] Summary
> The International Standard Atmosphere (ISA) fixes temperature, pressure and density against altitude so that aircraft performance can be compared. Hydrostatic balance and the perfect-gas law give $p/p_{SL}=(T/T_{SL})^{g/(c_0R)}$ in the troposphere, where the temperature falls at $c_0=6.5$ K/km, and an exponential decay in the isothermal lower stratosphere. A pitot-static tube measures $p_0-p=\tfrac12\rho V^2$; dividing by the sea-level density gives the equivalent airspeed $V_E=V\sqrt\sigma$, which fixes the aerodynamic loads, while the true airspeed $V$ and the local speed of sound $a=\sqrt{\gamma RT}$ give the Mach number $M=V/a$.

> [!summary]- Exam use: quick path
> - **Use it when:** a question gives an altitude, a relative density $\sigma$, a temperature or a pitot reading and asks for $\rho$, $V$, $V_E$, $a$ or $M$; or when any later performance formula needs the air density at altitude.
> - **Assumptions:** ISA with $g$ constant; troposphere 0–11 km with $T=T_{SL}-c_0h$; lower stratosphere 11–20 km at constant $T_S=216.5$ K; perfect gas $p=\rho RT$, $R=287$ J/(kg K), $\gamma=1.4$; incompressible Bernoulli for the airspeed formulae ($M\lesssim0.3$); temperatures in kelvin.
> - **Method:** 1. Find $T$ at the altitude. 2. Get $p$ from the layer formula, then $\rho=p/(RT)$ or $\sigma=(T/T_{SL})^{g/(c_0R)-1}$. 3. Convert speeds with $V=V_E/\sqrt\sigma$. 4. Find $a=\sqrt{\gamma RT}$ and $M=V/a$ from the true airspeed. 5. Check that $M$ is low enough for the incompressible pitot formula.
> - **Common mistakes:** dividing by $\sqrt\sigma$ the wrong way (true airspeed is the larger one above sea level); using $^\circ$C, or the sea-level temperature, in $a=\sqrt{\gamma RT}$.
> - **Practise:** [[#True and equivalent airspeed at 1000 m]] · [[SESA1015 T04 - Range and Endurance Solutions#Question 20|Revision Q20]]

An aircraft flies through air whose density and temperature change by large factors between take-off and cruise. At 11 km the density is about 30% of its sea-level value, so a wing at a fixed angle of attack must move through the air about $1/\sqrt{0.3}\approx1.8$ times faster to produce the same lift. The temperature is about 70 K lower, so the speed of sound, and with it the Mach number at which compressibility matters, changes too. Engines are affected in the same way, since the mass of air they swallow each second scales with density.

The real atmosphere varies with the weather, the season and the latitude, so performance is quoted against a standard model, the ISA. It is built from two physical laws: the weight of each slab of air is carried by the pressure difference across it, and air behaves as a perfect gas. A third relation, the temperature profile, closes the problem. Most aircraft fly between sea level and 20 km, so only the bottom two layers are needed: the troposphere, where the temperature falls linearly, and the lower stratosphere, where it is constant.

The speed that matters for the aerodynamic forces is the speed relative to the air, and the instrument that measures it, the pitot-static tube, actually measures a pressure difference equal to $\tfrac12\rho V^2$. Since $\rho$ is not measured, the airspeed indicator is calibrated with the sea-level density and so shows the equivalent airspeed. That is not a defect: the forces depend on $\tfrac12\rho V^2$, so a pilot holding a fixed equivalent airspeed holds fixed aerodynamic loads at any altitude.

---

## 1. The atmosphere and the International Standard Atmosphere

### Layers and standard values

The ISA gives the mean pressure, density, temperature and speed of sound as functions of height above sea level. Up to 90 km the temperature profile is a chain of straight lines. In the **troposphere**, from sea level to the **tropopause** at 11 km, the temperature falls at the **lapse rate** $c_0=6.5$ K/km. From 11 to 20 km, the lower **stratosphere**, it is constant at $-56.5\,^\circ$C. Above 20 km it rises again, at 1 K/km and then 2.8 K/km, to about $-2.5\,^\circ$C near 50 km, and falls through the mesosphere to about $-86\,^\circ$C. The aircraft in this course stay below 20 km.

![[mof_m01_isa_temperature.png|900]]

The ISA sea-level values are rounded differently in different places: $\rho_{SL}=1.225$ kg/m³ (workbook), $1.226$ (course notes) and $1.23$ (slides); any of them is accepted, but one value should be used throughout a calculation.

| Quantity | Slides v2 | ISA | Note |
|---|---|---|---|
| $T_{SL}$ | 288 K | 288.15 K | 15 °C |
| $p_{SL}$ | $1.013\times10^5$ Pa | 101 325 Pa | |
| $\rho_{SL}$ | 1.23 kg/m³ | 1.225 kg/m³ | notes: 1.226 |
| $c_0$ | 0.0065 K/m | 0.0065 K/m | 6.5 K/km |
| $T_S$ (11–20 km) | 216.5 K | 216.65 K | $T_{SL}-11c_0$ in each case |
| $R$ | 287 (or 287.05) J/(kg K) | 287.05 J/(kg K) | |
| $\gamma$ | 1.4 | 1.4 | |
| $g$ | 9.8 m/s² | 9.80665 m/s² | taken constant with height |

Taking $g$ constant means the altitude in these formulae is strictly the geopotential altitude; the difference from geometric height is about 19 m at 11 km and is ignored in this course.

### Hydrostatic balance and the perfect-gas law

A thin horizontal slab of still air of area $A$ between heights $h$ and $h+dh$ has the pressure $p$ pushing up on its lower face and $p+dp$ pushing down on its upper face, and its weight is $\rho gA\,dh$.

![[mof_m01_hydrostatic_element.png|700]]

For equilibrium in the vertical direction,

$$
pA-(p+dp)A-\rho gA\,dh=0 .
$$

Cancelling $pA$ and dividing by $A\,dh$ gives the **hydrostatic equation**

$$
\frac{dp}{dh}=-\rho g .
$$

Air is treated as a perfect gas,

$$
p=\rho RT ,
$$

with $R=287$ J/(kg K) for air. These are two equations in three unknowns, $p$, $\rho$ and $T$, so a third relation is needed: the ISA temperature profile $T(h)$. Eliminating $\rho$ with the gas law gives the form that is integrated in each layer:

$$
\frac{dp}{dh}=-\frac{pg}{RT}\quad\Rightarrow\quad\frac{dp}{p}=-\frac{g}{RT}\,dh .
$$

The same equation and a falling pressure appear for a liquid in [[SESA1016 T8 - Hydrostatics]]; the difference here is that $\rho$ itself falls with $p$.

### The troposphere: constant lapse rate

From sea level to 11 km,

$$
T=T_{SL}-c_0h .
$$

Substituting into the separated hydrostatic equation,

$$
\frac{dp}{p}=-\frac{g}{R}\,\frac{dh}{T_{SL}-c_0h} .
$$

Integrate from sea level ($p_{SL}$, $h=0$) to altitude $h$. The right-hand side has the antiderivative $\frac{g}{c_0R}\ln(T_{SL}-c_0h)$, because $\frac{d}{dh}\ln(T_{SL}-c_0h)=-\frac{c_0}{T_{SL}-c_0h}$. Hence

$$
\begin{aligned}
\ln\frac{p}{p_{SL}}&=\frac{g}{c_0R}\Big[\ln(T_{SL}-c_0h)-\ln T_{SL}\Big]\\
&=\frac{g}{c_0R}\ln\frac{T}{T_{SL}},
\end{aligned}
$$

and taking exponentials,

$$
\boxed{\frac{p}{p_{SL}}=\left(\frac{T}{T_{SL}}\right)^{g/(c_0R)}} .
$$

The density follows from the gas law written as a ratio, $\dfrac{\rho}{\rho_{SL}}=\dfrac{p}{p_{SL}}\dfrac{T_{SL}}{T}$:

$$
\begin{aligned}
\frac{\rho}{\rho_{SL}}&=\left(\frac{T}{T_{SL}}\right)^{g/(c_0R)}\left(\frac{T}{T_{SL}}\right)^{-1}\\
&=\left(\frac{T}{T_{SL}}\right)^{g/(c_0R)-1}=\left(\frac{T}{T_{SL}}\right)^{(g-c_0R)/(c_0R)} .
\end{aligned}
$$

$$
\boxed{\frac{\rho}{\rho_{SL}}=\left(\frac{T}{T_{SL}}\right)^{(g-c_0R)/(c_0R)}}
$$

With the course constants, $g/(c_0R)=9.8/(0.0065\times287)=5.253$, so the density exponent is $4.253$ (ISA values give 5.256 and 4.256). The two lines above are the working for the density result.

### The lower stratosphere: constant temperature

From 11 to 20 km, $T=T_S=216.5$ K. The separated equation now has a constant on the right:

$$
\frac{dp}{p}=-\frac{g}{RT_S}\,dh .
$$

Integrating from $h_1$ (pressure $p_1$) to $h_2$ (pressure $p_2$),

$$
\begin{aligned}
\ln\frac{p_2}{p_1}&=-\frac{g}{RT_S}(h_2-h_1)\\
&=\frac{g}{RT_S}(h_1-h_2),
\end{aligned}
$$

so

$$
\boxed{\frac{p_2}{p_1}=\frac{\rho_2}{\rho_1}=\exp\left[\frac{g}{RT_S}(h_1-h_2)\right]} .
$$

Density follows pressure exactly because $\rho=p/(RT_S)$ with $T_S$ fixed. The quantity $RT_S/g=287\times216.5/9.8=6340$ m is the **scale height**: every 6.34 km of climb in this layer divides $p$ and $\rho$ by $e$. In practice $h_1=11$ km and $p_1$, $\rho_1$ come from the troposphere formula at the tropopause.

### Relative density, pressure and temperature

Performance formulae use the ratios to the sea-level values,

$$
\sigma=\frac{\rho}{\rho_{SL}},\qquad\delta=\frac{p}{p_{SL}},\qquad\theta=\frac{T}{T_{SL}} ,
$$

where $\sigma$ is the **relative density**. Dividing $p=\rho RT$ by $p_{SL}=\rho_{SL}RT_{SL}$ gives

$$
\sigma=\frac{\delta}{\theta} ,
$$

so any two of the ratios fix the third. Density falls more slowly than pressure in the troposphere, because the temperature falls as well and $\sigma=\delta/\theta$.

| $h$ (km) | $T$ (K) | $p$ (Pa) | $\rho$ (kg/m³) | $\sigma$ | $a$ (m/s) |
|---|---|---|---|---|---|
| 0 | 288.15 | 101 325 | 1.2250 | 1.000 | 340.3 |
| 1 | 281.65 | 89 874 | 1.1117 | 0.908 | 336.4 |
| 2 | 275.15 | 79 495 | 1.0065 | 0.822 | 332.5 |
| 3.05 | 268.32 | 69 664 | 0.9045 | 0.738 | 328.4 |
| 5 | 255.65 | 54 020 | 0.7361 | 0.601 | 320.5 |
| 8 | 236.15 | 35 599 | 0.5252 | 0.429 | 308.1 |
| 11 | 216.65 | 22 632 | 0.3639 | 0.297 | 295.1 |
| 15 | 216.65 | 12 044 | 0.1937 | 0.158 | 295.1 |
| 20 | 216.65 | 5 475 | 0.0880 | 0.072 | 295.1 |

The table uses exact ISA constants; the course constants change the fourth significant figure at most (at 11 km they give $p=22\,623$ Pa, $\rho=0.3654$ kg/m³, $\sigma=0.297$).

![[mof_m01_isa_ratios.png|900]]

On a non-standard day the ISA formulae do not apply, and the density comes straight from the gas law with the actual pressure and temperature. At sea-level pressure and 35 °C, $\rho=101\,325/(287\times308.15)=1.146$ kg/m³, $\sigma=0.935$, which lengthens the take-off run (Revision Q28 compares a 5 °C and a 46 °C day).

### ISA at 1000 m

With the course constants:

$$
T=288-0.0065\times1000=281.5\ \text{K},
$$

$$
p=1.013\times10^5\left(\frac{281.5}{288}\right)^{5.253}=89\,852\ \text{Pa},
$$

$$
\rho=1.23\left(\frac{281.5}{288}\right)^{4.253}=1.116\ \text{kg/m}^3,\qquad\sigma=0.907 .
$$

> [!check] The course constants are not exactly consistent
> The gas law with $p=89\,852$ Pa and $T=281.5$ K gives $\rho=89\,852/(287\times281.5)=1.112$ kg/m³, 0.4% below the 1.116 from the density ratio. The gap is inherited from sea level, where $p_{SL}/(RT_{SL})=101\,300/(287\times288)=1.2256$, not 1.23. Either value is acceptable; quoting three significant figures hides the difference.

## 2. Measuring airspeed with a pitot-static tube

### Bernoulli's equation along a streamline

For steady flow of an inviscid fluid, Newton's second law along a streamline, with gravity negligible for a gas, gives Euler's equation ([[SESA1016 T10 - Euler and Bernoulli Equations]]):

$$
dp+\rho V\,dV=0 .
$$

If the density is constant, this integrates directly:

$$
\begin{aligned}
p+\rho\int V\,dV&=\text{const}\\
p+\tfrac12\rho V^2&=\text{const}=p_0 .
\end{aligned}
$$

This is **Bernoulli's equation**: static pressure plus dynamic pressure equals the **total pressure** $p_0$, constant along a streamline. The term

$$
q=\tfrac12\rho V^2
$$

is the **dynamic pressure**. The constant-density assumption holds for air only at low Mach number (the size of the error is in [[#The compressible pitot reading]]).

### The pitot-static tube

A **pitot-static tube** has a forward-facing open central tube and a sealed outer annulus with small holes drilled through its wall some distance behind the nose. On the streamline that meets the nose the air is brought to rest ($V=0$) at the stagnation point, so the central tube senses the **pitot pressure** $p_0$. The side holes face across the flow and sense the **static pressure** $p$ of the surrounding air. Alternatively a single pitot tube measures $p_0$, and $p$ is taken from a static vent on the fuselage at a point where the pressure is close to free-stream. For the oncoming streamline, Bernoulli between the free stream and the stagnation point gives

$$
p+\tfrac12\rho V^2=p_0+0\quad\Rightarrow\quad\boxed{p_0-p=\tfrac12\rho V^2} .
$$

![[mof_m01_pitot_static.png|900]]

Connecting the two tubes across a differential gauge measures $p_0-p$ directly. With a liquid manometer of density $\rho_\ell$ the reading is $p_0-p=\rho_\ell g\,\Delta h$; in the aircraft a sensitive pressure gauge calibrated in knots is used instead. See also [[Stagnation Pressure and Pitot Tube]].

### True airspeed

Solving for $V$,

$$
\boxed{V=\sqrt{\frac{2(p_0-p)}{\rho}}} .
$$

This is the **true airspeed**: the speed of the aircraft relative to the air. Using it needs the local density $\rho$, which the pressure gauge does not measure and which falls with height.

### Equivalent airspeed

Instead, the gauge is calibrated with the constant sea-level density $\rho_{SL}$, which defines the **equivalent airspeed**

$$
\boxed{V_E=\sqrt{\frac{2(p_0-p)}{\rho_{SL}}}} .
$$

Both formulae use the same measured $p_0-p$, so

$$
\tfrac12\rho V^2=p_0-p=\tfrac12\rho_{SL}V_E^2 .
$$

Cancelling $\tfrac12$ and dividing by $\rho_{SL}$,

$$
V_E^2=\frac{\rho}{\rho_{SL}}V^2=\sigma V^2 ,
$$

and taking the positive root,

$$
\boxed{V_E=V\sqrt\sigma,\qquad V=\frac{V_E}{\sqrt\sigma}} .
$$

Above sea level in the ISA $\sigma<1$, so the true airspeed exceeds the equivalent airspeed, by a factor $1/\sqrt{0.297}=1.83$ at the tropopause. At sea level in the ISA the two are equal. On a hot day at a low-lying airfield $\sigma<1$ too; only air denser than the standard sea-level value ($\sigma>1$, a cold day at sea level) makes $V<V_E$.

The equivalent airspeed is the useful one for loads and handling, because it is the dynamic pressure in disguise. Lift is $L=\tfrac12\rho V^2SC_L=\tfrac12\rho_{SL}V_E^2SC_L$, so an aircraft stalls at the same $V_E$ at every altitude, and the structural limits are set in $V_E$. The true airspeed is the one that sets distance covered, flight time and Mach number.

![[mof_m01_tas_eas.png|800]]

### Indicated airspeed and instrument errors

The airspeed indicator shows $V_E$ only if it is fed the true pitot and static pressures. The pitot pressure is easy to measure accurately, but the static pressure sensed depends on where the holes or vents are on the aircraft, on the angle of attack and on the configuration (flaps up or down). The reading without allowance for these errors, and for errors in the instrument itself, is the **indicated airspeed** $V_{ind}$. In this course $V_{ind}$ and $V_E$ are taken as equal unless a correction is given. Industry inserts calibrated airspeed between the two (full chain: [[Airspeed Measures]]).

### True and equivalent airspeed at 1000 m

An aircraft flies at 1000 m and the measured total pressure is $p_0=95\,435$ Pa. From [[#ISA at 1000 m]], $p=89\,852$ Pa and $\rho=1.116$ kg/m³, so

$$
p_0-p=95\,435-89\,852=5583\ \text{Pa}.
$$

The true airspeed is

$$
V=\sqrt{\frac{2\times5583}{1.116}}=100.0\ \text{m/s},
$$

and the equivalent airspeed, with $\rho_{SL}=1.23$ kg/m³,

$$
V_E=\sqrt{\frac{2\times5583}{1.23}}=95.28\ \text{m/s}.
$$

> [!check] Consistency
> $V\sqrt\sigma=100.02\times\sqrt{1.116/1.23}=100.02\times0.9526=95.28$ m/s, the same $V_E$. At 1000 m the true airspeed is only 5% higher; the gap grows to 83% at 11 km.

## 3. Speed of sound and Mach number

### The speed of a weak pressure wave

The **speed of sound** $a$ is the speed at which a weak pressure wave travels through still air. In a frame moving with the wave, the wave is stationary: air enters it at speed $a$ with $p$, $\rho$, and leaves at $a-dV$ with $p+dp$, $\rho+d\rho$ (the wave compresses and slows the air slightly). Per unit area of the wave, conservation of mass gives

$$
\begin{aligned}
\rho a&=(\rho+d\rho)(a-dV)\\
\rho a&=\rho a-\rho\,dV+a\,d\rho-d\rho\,dV ,
\end{aligned}
$$

and dropping the product of two small changes,

$$
a\,d\rho=\rho\,dV .
$$

The net pressure force on the air passing through equals its mass flow $\rho a$ times its change of velocity:

$$
\begin{aligned}
p-(p+dp)&=\rho a\big[(a-dV)-a\big]\\
dp&=\rho a\,dV .
\end{aligned}
$$

Dividing the momentum result by the mass result eliminates $dV$:

$$
\frac{dp}{d\rho}=\frac{\rho a\,dV}{\rho\,dV/a}=a^2 .
$$

The changes in a weak wave are small and fast, with negligible friction or heat transfer, so they are isentropic, $p=K\rho^\gamma$. Then

$$
\frac{dp}{d\rho}=\gamma K\rho^{\gamma-1}=\gamma\frac{p}{\rho},
$$

and with the gas law,

$$
\boxed{a=\sqrt{\frac{\gamma p}{\rho}}=\sqrt{\gamma RT}} .
$$

The speed of sound depends on temperature only. At $T=288$ K it is $\sqrt{1.4\times287\times288}=340.2$ m/s, and in the isothermal stratosphere ($T=216.5$ K) it is a constant $294.9$ m/s, so $a/a_{SL}=\sqrt\theta$ ([[Speed of Sound and Mach Number]]).

### Mach number and compressibility

The **Mach number** is the ratio of the true airspeed to the local speed of sound,

$$
\boxed{M=\frac{V}{a}} .
$$

It must be built from the true airspeed and the temperature at the aircraft's altitude, not from $V_E$ or sea-level values. Two thresholds are used. Above $M\approx0.3$ the flow is treated as compressible: the isentropic relation $\rho_0/\rho=\big(1+\tfrac{\gamma-1}{2}M^2\big)^{1/(\gamma-1)}$ gives a density change of 4.6% between free stream and stagnation at $M=0.3$, and the constant-density Bernoulli equation starts to lose accuracy. Above $M\approx0.8$ compressibility is important: locally supersonic flow and shock waves appear on the wing, which is the transonic regime ([[SESA2023 W03 - Compressible Flow, Normal Shocks and Nozzles]]).

### The compressible pitot reading

For compressible isentropic flow brought to rest, the total-to-static pressure ratio is

$$
\frac{p_0}{p}=\left(1+\frac{\gamma-1}{2}M^2\right)^{\gamma/(\gamma-1)} .
$$

With $\gamma=1.4$ the exponent is 3.5 and $\frac{\gamma-1}{2}=0.2$. The binomial series $(1+x)^n=1+nx+\frac{n(n-1)}{2}x^2+\frac{n(n-1)(n-2)}{6}x^3+\cdots$ with $x=0.2M^2$, $n=3.5$ gives

$$
\frac{p_0}{p}=1+0.7M^2+0.175M^4+0.0175M^6+\cdots
$$

The dynamic pressure in terms of $M$ follows from $a^2=\gamma p/\rho$:

$$
\tfrac12\rho V^2=\tfrac12\rho a^2M^2=\tfrac12\gamma pM^2=0.7pM^2 .
$$

Dividing $p_0-p$ by it,

$$
\begin{aligned}
\frac{p_0-p}{\tfrac12\rho V^2}&=\frac{0.7M^2+0.175M^4+0.0175M^6+\cdots}{0.7M^2}\\
&=1+\frac{M^2}{4}+\frac{M^4}{40}+\cdots
\end{aligned}
$$

The leading 1 is the incompressible result $p_0-p=\tfrac12\rho V^2$; the $M^2/4$ term is the first compressibility correction. The pitot reading is 0.25% high at $M=0.1$, 2.3% high at $M=0.3$ and 17% high at $M=0.8$, so a speed taken from the incompressible formula overestimates by about half these percentages. For the supersonic pitot problem, with a shock ahead of the probe, see [[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes]].

![[mof_m01_pitot_compressibility.png|800]]

### Local Mach number on an aerofoil

An aerofoil flies at 1000 m with a free stream of 100 m/s; at a point on its upper surface the flow is at 150 m/s. The local Mach number, the total pressure and the static pressure at that point are wanted.

The free-stream conditions are those of [[#ISA at 1000 m]]: $T=281.5$ K, $p=89\,852$ Pa, $\rho=1.116$ kg/m³. The speed of sound is

$$
a=\sqrt{1.4\times287\times281.5}=336.3\ \text{m/s},
$$

so at the point on the surface

$$
M=\frac{150}{336.3}=0.446\approx0.45 .
$$

The total pressure follows from the free stream, where $p$ and $V$ are both known:

$$
p_0=p+\tfrac12\rho V_\infty^2=89\,852+\tfrac12\times1.116\times100^2=95\,433\ \text{Pa}.
$$

The total pressure is the same on every streamline that starts in the uniform free stream, so at the 150 m/s point

$$
p_{150}=p_0-\tfrac12\rho\,(150)^2=95\,433-12\,557=82\,876\ \text{Pa}.
$$

> [!check] How good are the incompressible assumptions here?
> The calculation uses the free-stream temperature for $a$ and a constant density. Allowing for compressibility, the static temperature at the 150 m/s point is $T_0-V^2/(2c_p)=286.5-11.2=275.3$ K, giving $a=332.6$ m/s and $M=0.451$, so the Mach number hardly changes. At $M\approx0.45$ the constant-density pressure is a few hundred pascals out, consistent with treating $M>0.3$ as compressible.

### Cruise at Mach 0.8 at 11 km

An airliner cruises at $M=0.8$ at the tropopause, where (course constants) $T=216.5$ K, $\rho=0.3654$ kg/m³ and $\sigma=0.297$. Then

$$
a=\sqrt{1.4\times287\times216.5}=294.9\ \text{m/s},\qquad V=0.8\times294.9=235.9\ \text{m/s},
$$

$$
V_E=V\sqrt\sigma=235.9\times\sqrt{0.297}=128.6\ \text{m/s},\qquad q=\tfrac12\rho V^2=\tfrac12\times0.3654\times235.9^2=10.17\ \text{kPa}.
$$

The wing therefore carries the loads it would carry at 128.6 m/s (250 knots) at sea level while covering ground at 235.9 m/s. A pitot tube at this Mach number reads $p_0-p=p\big[(1+0.2M^2)^{3.5}-1\big]=11.86$ kPa, 16.6% above $q$; an indicator using the incompressible formula would show 138.9 m/s, not 128.6 m/s. Correcting for this is the compressibility correction in the airspeed chain of [[Airspeed Measures]].

## 4. Which speed goes where

| Speed | Definition | Used for |
|---|---|---|
| true airspeed $V$ | speed relative to the air, $\sqrt{2(p_0-p)/\rho}$ | Mach number, distance and time, kinematics of climb and turn |
| equivalent airspeed $V_E$ | $\sqrt{2(p_0-p)/\rho_{SL}}=V\sqrt\sigma$ | dynamic pressure, loads, stall speed, comparison across altitudes |
| indicated airspeed $V_{ind}$ | instrument reading, before static-pressure and instrument corrections | cockpit; taken as $V_E$ in this course |
| Mach number $M$ | $V/a$ with $a=\sqrt{\gamma RT}$ at altitude | compressibility, cruise speed of jets |

Any formula of the form $\tfrac12\rho V^2$ can be evaluated either with the local density and the true airspeed or with $\rho_{SL}$ and the equivalent airspeed; mixing the two pairs is the commonest error in this topic.

## Links

- Parent: [[SESA1015 Intro to Aero & Astro Hub]] · Next: [[SESA1015 M02 - Aircraft Geometry, Forces and Coefficients]]
- Concepts: [[Airspeed Measures]] · [[Dynamic Pressure and Aerodynamic Coefficients]] · [[International Standard Atmosphere]] · [[Speed of Sound and Mach Number]] · [[Stagnation Pressure and Pitot Tube]] · [[Bernoulli Equation]] · [[Wing Loading]]
- Builds on: [[SESA1016 T8 - Hydrostatics]] (the hydrostatic equation) · [[SESA1016 T10 - Euler and Bernoulli Equations]] (Bernoulli along a streamline) · [[SESA1016 T1 - Thermodynamic Systems, Properties and State]] (perfect gas)
- Used in: the stall, level-flight and range calculations of [[SESA1015 M04 - Steady Level Flight and Stall]], [[SESA1015 M05 - Minimum Drag, Power and Performance Curves]] and [[SESA1015 M06 - Jet Aircraft Range and Endurance]], and the seasonal take-off runs of [[SESA1015 M09 - Take-off and Landing Performance]]
- Later in the degree: [[SESA2023 W01 - Thrust, Efficiency, Range and the ISA]] (ISA tables and engine performance) · [[SESA2023 W03 - Compressible Flow, Normal Shocks and Nozzles]] (isentropic relations) · [[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes]] (subsonic and supersonic pitot probes) · [[Compressible Pitot Probe]]

## Sources

- *Mechanics of Flight Course Notes* (Prof. A. Keane, October 2020), §2.1 The Atmosphere (pp. 3–5, Figs 2.1 and 2.2), §2.2 Measurement of Airspeed (pp. 5–7), §2.3 Mach Number (p. 7)
- *Mechanics of Flight Lecture Slides* version 2: pp. 16–18 (atmosphere derivations), p. 19 (Bernoulli, Mach number, compressible pitot relation), p. 20 (aerofoil example), pp. 22–24 (pitot probe, true, equivalent and indicated airspeed, example), p. 69 (formula summary)
- Revision workbook: `04 - Labs & Coursework/Revision & Spreadsheets/SESA1015 - Revision Questions (Original).xlsx`, Questions 1, 20, 28, 30, 42

## Self-study tasks

There is no lecturer-set problem list for this topic; the tasks are the revision-workbook questions that use it and the worked examples in the slides.

### Core

- [ ] Rework the ISA state at 1000 m, then the true and equivalent airspeed from $p_0=95\,435$ Pa (Slides v2, pp. 20 and 24). → [[#ISA at 1000 m]] · [[#True and equivalent airspeed at 1000 m]]
- [ ] Revision Q1(b): true stalling speed at relative density $\sigma=0.75$. → [[SESA1015 T01 - Stall and Level-Flight Solutions#Question 1]]
- [ ] Revision Q20: seasonal flight-time difference at fixed Mach number from the cruise temperature. → [[SESA1015 T04 - Range and Endurance Solutions#Question 20]]
- [ ] Revision Q30: cruise wing loading from Mach number, density ratio and temperature ratio. → [[SESA1015 T01 - Stall and Level-Flight Solutions#Question 30]]
- [ ] Local Mach number and surface pressure on an aerofoil (Slides v2, p. 20). → [[#Local Mach number on an aerofoil]]

### Further practice

- [ ] Derive the density ratio $\rho/\rho_{SL}=(T/T_{SL})^{(g-c_0R)/(c_0R)}$ from the pressure ratio (left as an exercise on Slides v2, p. 18), then $p$ and $\rho$ at 15 km from the stratosphere formula (answer: 12 038 Pa, 0.194 kg/m³ with the course constants). → [[#The troposphere: constant lapse rate]] · [[#The lower stratosphere: constant temperature]]
- [ ] Revision Q28: sea-level density on a 5 °C and a 46 °C day from the gas law, and the effect on the take-off run. → [[SESA1015 T02 - Take-off and Landing Solutions#Question 28]]
- [ ] Revision Q42: lift-to-drag ratio at relative density $\sigma=0.81$. → [[SESA1015 T01 - Stall and Level-Flight Solutions#Question 42]]
- [ ] Show that $(p_0-p)/\tfrac12\rho V^2=1+M^2/4+\cdots$ and find the Mach number at which the pitot reading exceeds $\tfrac12\rho V^2$ by 1% (suggested, not lecturer-set; answer $M\approx0.2$). → [[#The compressible pitot reading]]

## Transcript and slide slips

> [!warning] Slide slip (Slides v2, p. 16)
> Where: [[#Layers and standard values]].
>
> The constants box gives the lapse rate as $c_0=6.5$ K/m. It is 6.5 K/km, that is $0.0065$ K/m, as pp. 18, 20 and 24 have it.

> [!warning] Slide slip (Slides v2, p. 24)
> Where: [[#True and equivalent airspeed at 1000 m]].
>
> The question gives $p_0=95\,435$ Pa, but the working substitutes $92\,435-89\,852$ and drops the factor 2 under both square roots; as printed it would give 48.2 and 45.8 m/s. The answers $V=100.02$ m/s and $V_E=95.28$ m/s are right for $p_0-p=95\,435-89\,852=5583$ Pa with the factor 2, and the true airspeed needs $\rho=1.116$ kg/m³ (the value on the same slide), not the 1.11 written under the root, which gives 100.30 m/s.

> [!warning] Slide slip (Slides v2, p. 20)
> Where: [[#Local Mach number on an aerofoil]].
>
> The speed of sound is computed as 336.31 m/s but divided as 336.13 m/s in $M=150/336.13$. Both round to $M=0.45$ (more precisely 0.446).

> [!warning] Slide slip (Slides v2, p. 23)
> Where: [[#Equivalent airspeed]].
>
> "True airspeed is always higher than equivalent airspeed" holds only where $\sigma<1$, which is everywhere above sea level in the ISA. At ISA sea level the two are equal, and in air denser than $\rho_{SL}$ (a cold day at sea level) the true airspeed is the lower.
