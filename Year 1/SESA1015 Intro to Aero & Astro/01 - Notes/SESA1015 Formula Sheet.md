---
title: "SESA1015 Formula Sheet"
module: "SESA1015 Intro to Aero & Astro"
type: formula-sheet
tags: [sesa1015, formula-sheet, mechanics-of-flight, astronautics]
aliases: ["SESA1015 Equations", "Mechanics of Flight Formula Sheet"]
date: 2026-09-27
status: complete
parent: ["[[SESA1015 Intro to Aero & Astro Hub]]"]
sources: ["02 - Sources/Mechanics of Flight/Mechanics of Flight - Course Notes.pdf", "02 - Sources/Mechanics of Flight/Mechanics of Flight - Lecture Slides version 2.pdf", "02 - Sources/Astronautics/Astronautics - Part 3 - Launch Vehicles.pdf"]
---

# SESA1015 Formula Sheet

Results by topic, in the notation of the Mechanics of Flight slides (version 2) and the Astronautics decks. Each section links to the topic note that derives them, states the assumptions and works an example. Unless stated otherwise, $V$ is true airspeed, $W=mg$ is weight in newtons, angles in formulas are in radians, and the flight is steady.

## Symbols and constants

| Symbol | Meaning | Value or unit |
|---|---|---|
| $\rho_{SL},\ p_{SL},\ T_{SL}$ | ISA sea-level density, pressure, temperature | $1.225$ kg m$^{-3}$, $101\,325$ Pa, $288.15$ K |
| $c_0$ | troposphere lapse rate | $6.5$ K km$^{-1}$ $=0.0065$ K m$^{-1}$ |
| $T_S$ | stratosphere temperature (11–20 km) | $216.65$ K |
| $R,\ \gamma$ | gas constant and ratio of specific heats for air | $287$ J kg$^{-1}$ K$^{-1}$, $1.4$ |
| $\sigma=\rho/\rho_{SL}$ | relative density | – |
| $q=\tfrac12\rho V^2$ | dynamic pressure | Pa |
| $S,\ b,\ AR,\ \bar{\bar c}$ | wing area, span, aspect ratio, mean aerodynamic chord | m$^2$, m, –, m |
| $C_{D0},\ K$ | zero-lift drag coefficient and induced-drag factor in $C_D=C_{D0}+KC_L^2$ | – |
| $W/S,\ T/W$ | wing loading, thrust-to-weight ratio | N m$^{-2}$, – |
| $c_t,\ c_p$ | thrust and power specific fuel consumption (fuel weight flow per unit thrust or power) | s$^{-1}$, m$^{-1}$ |
| $\mu_r$ | runway rolling-friction coefficient | – |
| $V_{ex}$ | rocket exhaust velocity | m s$^{-1}$ |

## Atmosphere, airspeed and Mach number

[[SESA1015 M01 - Atmosphere, Airspeed and Mach Number|M01]]

$$
\frac{dp}{dh}=-\rho g,\qquad p=\rho RT,\qquad \sigma=\frac{\delta}{\theta}\ \ \Big(\delta=\tfrac{p}{p_{SL}},\ \theta=\tfrac{T}{T_{SL}}\Big)
$$

Troposphere, $T=T_{SL}-c_0h$:

$$
\frac{p}{p_{SL}}=\left(\frac{T}{T_{SL}}\right)^{g/(c_0R)},\qquad \frac{\rho}{\rho_{SL}}=\left(\frac{T}{T_{SL}}\right)^{(g-c_0R)/(c_0R)}
$$

Stratosphere (isothermal at $T_S$):

$$
\frac{p_2}{p_1}=\frac{\rho_2}{\rho_1}=\exp\!\left[\frac{g}{RT_S}(h_1-h_2)\right]
$$

Pitot-static airspeed and Mach number:

$$
p_0-p=\tfrac12\rho V^2,\qquad V_E=\sqrt{\frac{2(p_0-p)}{\rho_{SL}}}=V\sqrt\sigma,\qquad a=\sqrt{\gamma RT},\qquad M=\frac Va,\qquad \frac{p_0-p}{\tfrac12\rho V^2}=1+\frac{M^2}{4}+\cdots
$$

## Forces, coefficients and wing geometry

[[SESA1015 M02 - Aircraft Geometry, Forces and Coefficients|M02]]

$$
L=\tfrac12\rho V^2SC_L,\qquad D=\tfrac12\rho V^2SC_D,\qquad M=\tfrac12\rho V^2S\bar{\bar c}\,C_M,\qquad Re=\frac{\rho Vl}{\mu}
$$

$$
\theta=\alpha+\gamma,\qquad L'=N'\cos\alpha-A'\sin\alpha,\qquad D'=N'\sin\alpha+A'\cos\alpha
$$

$$
S=2\int_0^{s}c\,dy,\qquad AR=\frac{b^2}{S},\qquad \lambda=\frac{c_T}{c_0},\qquad \bar{\bar c}=\frac{\int c^2\,dy}{\int c\,dy}
$$

Straight-tapered wing: $S=\tfrac12c_0b(1+\lambda)$, $\bar{\bar c}=\tfrac23c_0\dfrac{1+\lambda+\lambda^2}{1+\lambda}$, $\bar y=\dfrac b6\dfrac{1+2\lambda}{1+\lambda}$. Elliptic wing: $S=\pi c_0b/4$, $\bar{\bar c}=8c_0/(3\pi)$.

## Lift curve, drag polar and pitching moment

[[SESA1015 M03 - Aerodynamic Characteristics and the Drag Polar|M03]]

$$
C_L=a(\alpha-\alpha_0),\qquad a_{rad}=\frac{180}{\pi}a_{deg},\qquad a=\frac{a_0}{1+\dfrac{a_0}{\pi AR}(1+\tau)}
$$

$$
C_D=C_{D0}+KC_L^2,\qquad K=\frac{1}{\pi eAR}
$$

Two-point fit from tunnel data: $K=\dfrac{C_{D2}-C_{D1}}{C_{L2}^2-C_{L1}^2}$, $C_{D0}=C_{D1}-KC_{L1}^2$.

$$
C_m=C_{mo}-hC_L,\qquad \frac{x_{AC}}{c}=\frac{dC_m}{dC_L}=-h\ \text{(AC forward of the reference axis)},\qquad \frac{x_{cp}}{c}=\frac{C_{mo}}{C_L}-h
$$

## Level flight and stall

[[SESA1015 M04 - Steady Level Flight and Stall|M04]]

$$
L=W,\qquad T=D,\qquad V_S=\sqrt{\frac{2(W/S)}{\rho C_{L\max}}},\qquad V_{E,S}=\sqrt{\frac{2(W/S)}{\rho_{SL}C_{L\max}}}
$$

$$
D=AV^2+\frac{B}{V^2},\qquad A=\tfrac12\rho SC_{D0},\qquad B=\frac{2KW^2}{\rho S}
$$

$$
V^2=\frac{T\pm\sqrt{T^2-4AB}}{2A}\quad\text{(real only if }T\ge D_{min}=2W\sqrt{KC_{D0}}\text{)}
$$

## Minimum drag and minimum power

[[SESA1015 M05 - Minimum Drag, Power and Performance Curves|M05]]

$$
V_{MD}=\left(\frac BA\right)^{1/4},\qquad C_{L,MD}=\sqrt{\frac{C_{D0}}{K}},\qquad C_{D,MD}=2C_{D0},\qquad D_{min}=2W\sqrt{KC_{D0}},\qquad \left(\frac LD\right)_{max}=\frac{1}{2\sqrt{KC_{D0}}}
$$

$$
P=DV=AV^3+\frac BV,\qquad C_{L,MP}=\sqrt{\frac{3C_{D0}}{K}},\qquad C_{D,MP}=4C_{D0},\qquad V_{MP}=3^{-1/4}V_{MD},\qquad P_{min}\propto\frac{1}{\sqrt\sigma}
$$

## Jet range and endurance

[[SESA1015 M06 - Jet Aircraft Range and Endurance|M06]]

$$
E=\frac{1}{c_t}\frac LD\ln\frac{W_1}{W_2}\qquad\text{(best at }(L/D)_{max}\text{)}
$$

$$
R=\frac{V}{c_t}\frac LD\ln\frac{W_1}{W_2}\qquad\text{(cruise-climb, constant }V\text{ and }C_L\text{)}
$$

$$
R=\frac{2}{c_t}\sqrt{\frac{2}{\rho S}}\,\frac{C_L^{1/2}}{C_D}\left(\sqrt{W_1}-\sqrt{W_2}\right)\qquad\text{(constant altitude and }C_L\text{)}
$$

Best constant-altitude range at maximum $C_L^{1/2}/C_D$: $C_L=\sqrt{C_{D0}/(3K)}$, $V=3^{1/4}V_{MD}$. Cruise-climb height gain in the stratosphere: $\Delta h=\dfrac{RT_S}{g}\ln\dfrac{W_1}{W_2}$.

## Propeller and battery aircraft

[[SESA1015 M07 - Propeller Aircraft Range and Endurance|M07]]

$$
R=\frac{\eta}{c_p}\frac LD\ln\frac{W_1}{W_2}\qquad\text{(best at }(L/D)_{max}\text{, i.e. }V_{MD}\text{)}
$$

$$
E=\frac{\eta}{c_p}\frac{C_L^{3/2}}{C_D}\sqrt{2\rho S}\left(W_2^{-1/2}-W_1^{-1/2}\right)\qquad\text{(best at }V_{MP}\text{)}
$$

$$
R=\eta_t\frac LD\frac{E^*}{g}\frac{m_{bat}}{m}\qquad\text{(battery, constant mass; }E^*\text{ = specific energy)}
$$

## Glide and climb

[[SESA1015 M08 - Glide and Climb Performance|M08]]

$$
\tan\theta=\frac DL,\qquad R_{glide}=h\frac LD,\qquad \theta_{min}\approx2\sqrt{KC_{D0}},\qquad -\dot h=\frac{DV}{W},\qquad -\dot h_{min}=1.755\sqrt{\frac{2W}{\rho S}}\left(C_{D0}K^3\right)^{1/4}
$$

$$
\frac{(T\cos\gamma-D)V}{W}=\frac{dh}{dt}+\frac Vg\frac{dV}{dt},\qquad \sin\theta=\frac{T\cos\gamma-D}{W}\ \text{(steady)},\qquad (\sin\theta)_{max}=\frac TW-\frac{1}{(L/D)_{max}}
$$

$$
C_{L,\dot h_{max}}=\frac{-(T/W)+\sqrt{(T/W)^2+12KC_{D0}}}{2K}
$$

## Take-off and landing

[[SESA1015 M09 - Take-off and Landing Performance|M09]]

$$
s_1=\frac{V_2^2}{2g\,(T/W-\mu_r)}=\frac{1.44}{\rho g}\,\frac WS\,\frac{1}{C_{L\max}}\,\frac{1}{T/W-\mu_r}\qquad(V_2\approx1.2V_S)
$$

$$
s_1=\frac{1}{2gb}\ln\frac{a}{a-bV_2^2}\qquad\text{(with lift and drag, }\ddot x/g=a-bV^2\text{)}
$$

Landing run with drag and friction only, $k=\rho SC_{D0}/(2W)$:

$$
x_{stop}=\frac{1}{2gk}\ln\!\left(1+\frac{kV_L^2}{\mu_r}\right),\qquad t_{stop}=\frac{1}{g\sqrt{\mu_rk}}\tan^{-1}\!\left(V_L\sqrt{\frac{k}{\mu_r}}\right)
$$

## Turning flight

[[SESA1015 M10 - Turning Flight and Manoeuvre Performance|M10]]

$$
n=\frac{1}{\cos\phi},\qquad R=\frac{V^2}{g\tan\phi}=\frac{V^2}{g\sqrt{n^2-1}},\qquad \omega=\frac{g\sqrt{n^2-1}}{V},\qquad V_{S,turn}=V_S\sqrt n
$$

Stall limit: $R_{min}=\dfrac{V^2}{g\sqrt{(V/V_S)^4-1}}$; corner speed $V^*=V_S\sqrt{n_{max}}$.

Thrust limit: $R_{min}=\left(\dfrac{2KW^2V^2}{\rho Sg^2}\right)^{1/2}\dfrac{1}{\sqrt{T_{max}-D_L}}$, with $D_L$ the level-flight drag at the same speed.

## Trim and static stability

[[SESA1015 M11 - Longitudinal Trim and Static Stability|M11]]

$$
C_{m_G}=C_{m0}+(h-h_0)C_L-\bar V C_{L_T},\qquad \bar V=\frac{S_Tl_T}{S\bar c},\qquad \alpha_T=\alpha\left(1-\frac{d\varepsilon}{d\alpha}\right)+\alpha_s
$$

$$
h_n=h_0+\bar V\frac{a_{1T}}{a_1}\left(1-\frac{d\varepsilon}{d\alpha}\right),\qquad K_n=h_n-h,\qquad \frac{dC_{m_G}}{d\alpha}=-a_1K_n
$$

$$
\delta_e=\frac{C_{M_0}+C_{m_\alpha}\alpha_{req}}{V_{HT}\,dC_{L_T}/d\delta_e},\qquad \frac{d\eta}{dV}=\frac{2C_LK_n}{V\bar Va_{2T}}
$$

## Constraint analysis

[[SESA1015 M12 - Aircraft Constraint Analysis|M12]]

$$
C_L=\frac{n(W/S)}{q},\qquad \frac TW=\frac{qC_{D0}}{W/S}+\frac{Kn^2}{q}\frac WS+\frac{V_V}{V}
$$

$$
\frac WS\le\tfrac12\rho V_S^2C_{L\max}\ \text{(stall/approach)},\qquad \frac TW=\frac{V_2^2}{2gs_1}+\mu\ \text{(simple take-off)}
$$

$$
\frac TW=\frac{V_2^2}{2gs_1}+\mu+\left(C_{D,TO}-\mu C_{L,TO}\right)\frac{\bar q}{W/S}\ \text{(refined take-off)}
$$

Bottom of a manoeuvre curve: $(W/S)^*=\dfrac qn\sqrt{\dfrac{C_{D0}}{K}}$, $(T/W)_{min}=2n\sqrt{KC_{D0}}$. Crossing of take-off line $y_{TO}$ and a manoeuvre curve: $\dfrac{Kn^2}{q}x^2-\left(y_{TO}-\dfrac{V_V}{V}\right)x+qC_{D0}=0$, lower root.

## Orbits and missions

[[SESA1015 A01 - Astronautics Foundations, Missions and Applications|A01]]

$$
V=\sqrt{\frac{\mu}{r}},\qquad T=2\pi\sqrt{\frac{r^3}{\mu}},\qquad r_{GEO}=\left(\frac{\mu T_{sid}^2}{4\pi^2}\right)^{1/3}=42\,164\ \mathrm{km},\qquad \mu=3.986\times10^{14}\ \mathrm{m^3\,s^{-2}}
$$

## Space environment

[[SESA1015 A02 - Space Environment|A02]]

$$
H_i=\frac{RT}{M_ig},\qquad \rho_i=\rho_{i0}\,e^{-(h-h_0)/H_i},\qquad F_0=n_{AO}Vt,\qquad \Delta a_{rev}=-2\pi\frac{C_DA}{m}\rho a^2,\qquad 100\ \text{rad}=1\ \mathrm{J\,kg^{-1}}
$$

## Launch environment

[[SESA1015 A03 - Launch Environment|A03]]

$$
n=\frac{T-D}{Mg_0},\qquad n_{bo}=n_0\frac{M_0}{M_{bo}},\qquad g_{RMS}=\sqrt{\int G(f)\,df}
$$

$$
L_p=20\log_{10}\frac{p_{rms}}{2\times10^{-5}\ \mathrm{Pa}},\qquad \text{OASPL}=10\log_{10}\sum_i10^{L_i/10}
$$

## Rocket equation and launch performance

[[SESA1015 A04 - Rocket Equation and Launch Performance|A04]]

$$
T=\dot mV_{ex},\qquad \Delta V=V_{ex}\ln\frac{M_0}{M_b},\qquad \Delta V=\Delta V_{ideal}-\Delta V_g-\Delta V_D
$$

$$
\Delta V_g=\int g\sin\gamma\,dt,\qquad \Delta V_D=\int\frac DM\,dt,\qquad V_{circ}=\sqrt{\frac{\mu}{r}}\ (=7.78\text{ km/s at 200 km})
$$

## Staging and payload fraction

[[SESA1015 A05 - Staging and Payload Fraction|A05]]

With payload ratio $p=M_p/M_0$ and structural ratio $s=M_s/M_f$ (structure over propellant):

$$
\frac{M_0}{M_b}=\frac{1+s}{p+s},\qquad \Delta V_{ideal}=\sum_iV_{ex,i}\ln\frac{1+s_i}{p_i+s_i},\qquad P=\prod_ip_i
$$

$N$ identical stages: $\dfrac{\Delta V}{V_{ex}}=N\ln\dfrac{1+s}{P^{1/N}+s}\ \to\ \dfrac{\ln(1/P)}{1+s}$ as $N\to\infty$; best split $p_i=P^{1/N}$.

## Dimensional checks

| Quantity | Check |
|---|---|
| $W/(\tfrac12\rho V^2S)$ | dimensionless ($C_L$) |
| $\sqrt{2(W/S)/(\rho C_L)}$ | m s$^{-1}$ |
| $c_t$ (N of fuel per N of thrust per s) | s$^{-1}$, so $V/c_t$ is a length and $1/c_t$ a time |
| $c_p$ (N of fuel per W per s) | m$^{-1}$, so $\eta/c_p$ is a length |
| $V_{ex}\ln(M_0/M_b)$ | m s$^{-1}$ |
