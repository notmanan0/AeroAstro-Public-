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

> [!abstract] Use this as a map, not a substitute for a model
> Start every calculation with a free-body diagram, units and an explicit flight condition. Most mistakes in this module come from using the right equation for the wrong state: confusing mass with weight, TAS with EAS, degrees with radians, or maximum $L/D$ with minimum-power speed.

## Symbols and constants

| Symbol | Meaning | SI unit |
|---|---|---|
| $m,W=mg$ | mass, weight | kg, N |
| $V$ | true airspeed unless stated | m s$^{-1}$ |
| $S,b,\bar c$ | wing area, span, mean chord | m$^2$, m, m |
| $q=\tfrac12\rho V^2$ | dynamic pressure | Pa |
| $L,D,T$ | lift, drag, thrust | N |
| $C_L,C_D,C_m$ | lift, drag, pitching-moment coefficient | – |
| $W/S$ | wing loading | N m$^{-2}$ |
| $T/W$ | thrust loading | – |
| $g_0$ | standard gravity | $9.80665$ m s$^{-2}$ |
| $R$ | specific gas constant for air | $287.05$ J kg$^{-1}$ K$^{-1}$ |
| $\gamma$ | ratio of specific heats for air | about 1.4 |

## Atmosphere, speed and Mach

$$p=\rho RT,\qquad a=\sqrt{\gamma RT},\qquad M=\frac{V}{a}$$

Troposphere with lapse rate $L_T=-0.0065\ \mathrm{K,m^{-1}}$:

$$T=T_0+L_Th,qquad \frac{p}{p_0}=\left(\frac{T}{T_0}\right)^{-g_0/(RL_T)},\qquad \rho=\frac{p}{RT}$$

Equivalent airspeed preserves dynamic pressure relative to sea-level density $\rho_0$:

$$q=\frac12\rho V_{TAS}^2=\frac12\rho_0V_{EAS}^2,qquad V_{EAS}=V_{TAS}\sqrt{\frac{\rho}{\rho_0}}$$

At low Mach, calibrated airspeed is approximately equivalent airspeed. IAS additionally contains instrument/position error.

## Aerodynamic forces and moments

$$L=qSC_L,qquad D=qSC_D,qquad M_{ref}=qS\bar c\,C_m$$

$$AR=\frac{b^2}{S},\qquad C_L\approx C_{L_\alpha}(\alpha-\alpha_{L=0})$$

Parabolic drag polar:

$$\boxed{C_D=C_{D0}+kC_L^2},\qquad k=\frac{1}{\pi e AR}$$

Lift-to-drag ratio:

$$\frac{L}{D}=\frac{C_L}{C_D}$$

Moment transfer between reference points separated by $\Delta x=x_2-x_1$ (positive aft; check the course sign convention):

$$C_{m,2}=C_{m,1}+C_L\frac{\Delta x}{\bar c}$$

## Steady level flight and stall

$$L=W,qquad T=D,qquad C_L=\frac{W}{qS}=\frac{2W}{\rho V^2S}$$

$$\boxed{V_s=\sqrt{\frac{2W}{\rho S C_{L,max}}}=\sqrt{\frac{2(W/S)}{\rho C_{L,max}}}}$$

Useful scaling:

$$V_s\propto\sqrt{\frac{W/S}{\rho C_{L,max}}}$$

Substituting the polar into level flight:

$$\boxed{D(V)=\frac12\rho V^2SC_{D0}+\frac{2kW^2}{\rho V^2S}}$$

The first term is parasite drag; the second is induced drag.

## Minimum drag, maximum $L/D$ and minimum power

At minimum drag:

$$C_{L,MD}=\sqrt{\frac{C_{D0}}{k}},\qquad C_{D,MD}=2C_{D0}$$

$$\left(\frac{L}{D}\right)_{max}=\frac{1}{2\sqrt{kC_{D0}}},\qquad D_{min}=2W\sqrt{kC_{D0}}$$

$$V_{MD}=\sqrt{\frac{2W}{\rho S C_{L,MD}}}$$

Power required:

$$P_R=DV=\frac12\rho SC_{D0}V^3+\frac{2kW^2}{\rho SV}$$

At minimum power:

$$C_{L,MP}=\sqrt{\frac{3C_{D0}}{k}}=\sqrt3\,C_{L,MD},qquad V_{MP}=3^{-1/4}V_{MD}\approx0.760V_{MD}$$

> [!warning] Distinguish the optima
> Maximum $L/D$ = minimum drag = best still-air glide angle. Minimum power = minimum sink and, for a propeller aircraft with constant efficiency and BSFC, maximum endurance.

## Jet range and endurance

Let thrust-specific fuel consumption $c_T=-\dot W_f/T$ have units s$^{-1}$ when weight flow is used.

At constant $V$ and $L/D$:

$$\boxed{E_j=\frac{1}{c_T}\frac{L}{D}\ln\frac{W_i}{W_f}}$$

Constant-altitude Breguet range with constant $C_L$, $C_D$, $c_T$:

$$\boxed{R_j=\frac{2}{c_T}\sqrt{\frac{2}{\rho S}}\frac{\sqrt{C_L}}{C_D}\left(\sqrt{W_i}-\sqrt{W_f}\right)}$$

For a constant-$V$ cruise or cruise-climb idealisation:

$$\boxed{R_j=\frac{V}{c_T}\frac{L}{D}\ln\frac{W_i}{W_f}}$$

Jet optima for a parabolic polar:

$$E_{max}:\ \max\frac{C_L}{C_D}\Rightarrow C_L=\sqrt{\frac{C_{D0}}{k}}$$

$$R_{max}\text{ at constant altitude}:\ \max\frac{\sqrt{C_L}}{C_D}\Rightarrow C_L=\sqrt{\frac{C_{D0}}{3k}}$$

## Propeller range and endurance

With propeller efficiency $\eta_p$ and brake-specific fuel consumption expressed consistently as $c_P$:

$$P_A=\eta_p P_{shaft},\qquad P_R=DV$$

The useful structural forms are

$$\boxed{R_p\propto\frac{\eta_p}{c_P}\frac{L}{D}\ln\frac{W_i}{W_f}}$$

$$\boxed{E_p\propto\frac{\eta_p}{c_P}\frac{C_L^{3/2}}{C_D}\frac{1}{\sqrt{\rho S}}\left(\frac{1}{\sqrt{W_f}}-\frac{1}{\sqrt{W_i}}\right)}$$

Thus maximum propeller range occurs at maximum $L/D$ and maximum propeller endurance at minimum power. Always adapt the dimensional prefactor to whether the stated SFC is mass-based or weight-based.

## Glide and climb

Steady glide with thrust neglected:

$$L=W\cos\gamma,qquad D=W\sin\gamma,qquad \tan\gamma=\frac{D}{L}$$

$$\frac{\text{horizontal distance}}{\text{height lost}}=\frac{L}{D}$$

Steady climb:

$$T-D=W\sin\gamma$$

Small-angle approximation:

$$\sin\gamma\approx\gamma\approx\frac{T-D}{W},\qquad ROC=V\sin\gamma=\frac{P_A-P_R}{W}$$

Best climb angle maximises excess thrust; best rate of climb maximises excess power.

## Take-off ground run

Along the runway:

$$m\dot V=T-D-\mu(W-L)$$

Using approximately constant coefficients and defining

$$A=T-\mu W,qquad B=\frac12\rho S(C_D-\mu C_L),$$

gives

$$mV\frac{dV}{ds}=A-BV^2$$

and, for constant $T,C_L,C_D$,

$$\boxed{s_g=\frac{m}{2B}\ln\left(\frac{A}{A-BV_{LOF}^2}\right)}$$

with the $B\to0$ limit $s_g=V_{LOF}^2/(2A/m)$. A common certification-style assumption is $V_{LOF}\approx1.1$–$1.2V_s$; use the factor stated in the question.

Landing/stall comparisons follow directly from

$$\frac{C_{L,max,2}}{C_{L,max,1}}=\frac{(W/S)_2}{(W/S)_1}\frac{\rho_1}{\rho_2}\left(\frac{V_{s,1}}{V_{s,2}}\right)^2.$$

## Turning flight

Coordinated, level turn:

$$L\cos\phi=W,qquad L\sin\phi=\frac{mV^2}{R}$$

$$\boxed{n=\frac{L}{W}=\frac{1}{\cos\phi}},\qquad \boxed{R=\frac{V^2}{g\tan\phi}=\frac{V^2}{g\sqrt{n^2-1}}}$$

$$\boxed{\dot\psi=\frac{g\tan\phi}{V}=\frac{g\sqrt{n^2-1}}{V}}$$

Accelerated stall speed:

$$\boxed{V_{s,n}=V_s\sqrt n}$$

If thrust limits the turn, solve $T_A=D(V,n)$ together with the load-factor relation rather than assuming any bank angle is achievable.

## Trim and static stability

Trim requires

$$\sum F_z=0,\qquad \sum M_{CG}=0.$$

Linear pitching moment:

$$C_m=C_{m0}+C_{m_\alpha}\alpha+C_{m_{\delta_e}}\delta_e$$

Trim angle at a stated elevator setting:

$$\alpha_{trim}=-\frac{C_{m0}+C_{m_{\delta_e}}\delta_e}{C_{m_\alpha}}$$

Longitudinal static stability:

$$\boxed{C_{m_\alpha}<0}$$

Tail volume coefficient and static margin:

$$V_H=\frac{S_Tl_T}{S\bar c},\qquad SM=\frac{x_{NP}-x_{CG}}{\bar c}$$

$$SM>0\ \text{is statically stable},\qquad C_{m_\alpha}\approx-C_{L_\alpha}SM$$

## Constraint analysis

Use wing loading $x=W/S$ on the horizontal axis and thrust loading $y=T/W$ on the vertical axis.

Level-flight/speed constraint:

$$\boxed{\frac{T}{W}=\frac{qC_{D0}}{W/S}+\frac{k(W/S)}{q}}$$

Stall/landing constraint:

$$\boxed{\frac{W}{S}\le\frac12\rho V_s^2C_{L,max}}$$

Climb-gradient constraint (simple jet model):

$$\boxed{\frac{T}{W}\ge\frac{D}{W}+\sin\gamma}$$

The feasible design region lies on the safe side of **every** boundary; the design point is a trade, not an automatic curve intersection.

## Rocket propulsion and launch performance

Rocket thrust:

$$\boxed{T=\dot m v_e+(p_e-p_a)A_e}$$

Effective exhaust velocity and specific impulse:

$$c=T/\dot m,qquad \boxed{I_{sp}=\frac{T}{\dot m g_0}=\frac{c}{g_0}}$$

Ideal rocket equation:

$$\boxed{\Delta v=c\ln\frac{m_0}{m_f}=g_0I_{sp}\ln\frac{m_0}{m_f}}$$

Mass fractions:

$$m_0=m_p+m_s+m_L,qquad \epsilon=\frac{m_s}{m_s+m_p},\qquad \lambda=\frac{m_L}{m_0}$$

Real ascent budget:

$$\Delta v_{propulsive}=\Delta v_{mission}+\Delta v_{gravity}+\Delta v_{drag}+\Delta v_{steering}+\Delta v_{residuals}$$

For ideal sequential stages:

$$\boxed{\Delta v_{total}=\sum_i c_i\ln\frac{m_{0,i}}{m_{f,i}}}$$

The discarded dry mass of a spent stage no longer has to be accelerated, which is the central benefit of staging.

## Fast dimensional checks

- $q$, $W/S$, pressure and stress all have units N m$^{-2}$.
- $c_T$ for a jet is typically inverse time only after the fuel-flow convention is made explicit.
- Angles inside calculus and small-angle formulae must be in radians.
- A logarithm must have a dimensionless argument.
- $I_{sp}$ is quoted in seconds; $g_0I_{sp}$ is a velocity.
- If a result predicts $V_s$ falling when $W/S$ rises, or range increasing when $L/D$ falls, stop and find the sign or inversion error.

