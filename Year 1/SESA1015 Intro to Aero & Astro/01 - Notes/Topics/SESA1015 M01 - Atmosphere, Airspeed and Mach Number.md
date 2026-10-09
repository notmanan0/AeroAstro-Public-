---
title: "SESA1015 M01 - Atmosphere, Airspeed and Mach Number"
module: "SESA1015 Intro to Aero & Astro"
type: topic
stream: "Mechanics of Flight"
order: 1
tags: [sesa1015, atmosphere, airspeed, mach]
aliases: ["SESA1015 Mechanics 1", "Atmosphere and Airspeed"]
date: 2026-09-27
status: complete
parent: ["[[SESA1015 Intro to Aero & Astro Hub]]"]
prerequisites: []
next_topics: ["[[SESA1015 M02 - Aircraft Geometry, Forces and Coefficients]]"]
key_concepts: ["[[Airspeed Measures]]", "[[Dynamic Pressure and Aerodynamic Coefficients]]"]
tutorial_sheets: ["[[SESA1015 T01 - Stall and Level-Flight Solutions]]"]
sources: ["02 - Sources/Mechanics of Flight/Mechanics of Flight - Course Notes.pdf", "02 - Sources/Mechanics of Flight/Mechanics of Flight - Lecture Slides version 2.pdf"]
---

# SESA1015 M01 - Atmosphere, Airspeed and Mach Number

> [!abstract] Summary
> An aircraft does not respond to speed alone: aerodynamic force is set by **dynamic pressure** $q=\tfrac12\rho V^2$. As altitude increases, density normally falls, so the same true speed produces less force. Equivalent airspeed packages $\rho V^2$ into one sea-level-referenced number, while true airspeed describes motion through the air mass and Mach number compares that speed with the local speed of sound. The ISA supplies a common reference atmosphere, not a weather forecast.

## Key concepts

- [[Airspeed Measures]]
- [[Dynamic Pressure and Aerodynamic Coefficients]]
- [[Wing Loading]]

## 1. The physical picture

Imagine holding lift fixed during a climb. Lower density means fewer air molecules cross the wing each second. The aircraft must either fly faster, increase $C_L$, or use more wing area. This one idea explains why TAS rises for a fixed indicated speed, why take-off distance grows at high density altitude, and why a ceiling appears when thrust or power can no longer cover the aerodynamic requirement.

![[mof_airspeed_density.png|760]]

## 2. Hydrostatic atmosphere and perfect gas

For a thin stationary layer,

$$dp=-\rho g\,dh.$$

Close the relation with the perfect-gas law,

$$p=\rho RT.$$

In the troposphere, approximate temperature with a constant lapse rate $L_T=dT/dh$:

$$T=T_0+L_Th.$$

Substituting $\rho=p/(RT)$ into hydrostatic balance and integrating gives

$$\boxed{\frac{p}{p_0}=\left(\frac{T}{T_0}\right)^{-g/(RL_T)}}.$$

Then $\rho=p/(RT)$. In an isothermal layer, the corresponding pressure law is exponential:

$$\frac{p}{p_b}=\exp\left[-\frac{g(h-h_b)}{RT_b}\right].$$

> [!warning] Geometric versus geopotential altitude
> Introductory questions normally supply the relation or permit the low-altitude ISA approximation. Do not silently mix actual weather, pressure altitude and geometric height.

## 3. Dynamic pressure is the aerodynamic currency

$$\boxed{q=\frac12\rho V^2}$$

Aerodynamic forces take the form $F=qSC_F$. If $C_F$ and $S$ are unchanged, equal $q$ means equal force. Hence a speed that preserves dynamic pressure preserves the incompressible aerodynamic loading.

### Equivalent and true airspeed

Define equivalent airspeed by

$$\frac12\rho_0V_{EAS}^2=\frac12\rho V_{TAS}^2.$$

Therefore

$$\boxed{V_{EAS}=V_{TAS}\sqrt{\sigma}},\qquad \boxed{V_{TAS}=\frac{V_{EAS}}{\sqrt\sigma}},\qquad \sigma\equiv\frac{\rho}{\rho_0}.$$

At altitude, $\sigma<1$, so TAS is greater than EAS for the same dynamic pressure.

### The airspeed chain

| Quantity | Meaning | Principal correction |
|---|---|---|
| IAS | instrument reading | raw measurement |
| CAS | IAS corrected for instrument/position error | installation effects |
| EAS | CAS corrected for compressibility | represents $q$ |
| TAS | actual speed relative to air | density correction |
| Ground speed | speed over Earth | add wind vector |

At low Mach in elementary problems, CAS and EAS are often treated as equal. State that approximation.

## 4. Speed of sound and Mach number

For a calorically perfect gas,

$$\boxed{a=\sqrt{\gamma RT}},\qquad \boxed{M=\frac{V}{a}}.$$

The speed of sound depends primarily on temperature, not directly on pressure. This means that TAS corresponding to a given Mach changes with atmospheric temperature.

| Regime | Useful course guide | Modelling implication |
|---|---:|---|
| Low-speed | $M\lesssim0.3$ | density change often neglected |
| Subsonic | $M<1$ | pressure information can travel upstream |
| Transonic | about $0.8$–$1.2$ | mixed local regimes and shocks possible |
| Supersonic | $M>1$ | compressible-wave structure essential |

## 5. Worked scaling check

Suppose an aircraft holds the same $C_L$ and lift at a density ratio $\sigma=0.64$. From $L=\tfrac12\rho V^2SC_L$,

$$\frac{V_2}{V_1}=\sqrt{\frac{\rho_1}{\rho_2}}=\frac{1}{\sqrt{0.64}}=1.25.$$

TAS must rise by 25%, while EAS is unchanged. If the local temperature is $250\ \mathrm K$, then

$$a=\sqrt{1.4(287.05)(250)}\approx316.9\ \mathrm{m,s^{-1}}$$

and Mach follows from the new TAS.

## 6. Problem-solving workflow

1. Identify which speed the question gives.
2. Use ISA or the supplied $p,T,\rho$ data; do not assume sea level.
3. Convert to dynamic pressure or TAS before applying force equations.
4. Calculate Mach from local $T$.
5. Check whether the incompressible assumption remains credible.

> [!failure] Common errors
> - Using $p/p_0$ where the equation needs $\rho/\rho_0$.
> - Correcting EAS to TAS in the wrong direction.
> - Using Celsius inside $a=\sqrt{\gamma RT}$.
> - Calling ISA the actual atmospheric state.

## Year 2 bridge

- [[SESA2023 W01 - Thrust, Efficiency, Range and the ISA]] makes the atmosphere–propulsion coupling explicit.
- [[SESA2023 W03 - Compressible Flow, Normal Shocks and Nozzles]] replaces the low-speed airspeed approximation with compressible-flow relations.
- [[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes]] later shows exactly what a Pitot system measures across subsonic and supersonic regimes.

