---
title: "Ramjet"
module: "SESA2023 Propulsion"
type: concept
stream: "Section 3: Ramjets, Gas Turbines, Turbojets and Turbofans"
aliases: ["ramjet", "scramjet", "ideal ramjet", "SR-71 J58", "turbo-ramjet"]
tags: [sesa2023, concept, ramjet, cycle-analysis]
status: complete
parent_lectures: ["[[SESA2023 W06 - Jet Engine Cycle Analysis - Brayton, Ramjet, Turbojet and Reheat]]"]
related_concepts: ["[[Intake Pressure Recovery]]", "[[Component Stagnation Pressure Ratios]]", "[[Adiabatic Flame Temperature]]", "[[Turbojet]]"]
sources: ["02 - Sources/Lectures/Week 06-07 - Jet Engines.pdf"]
---
# Ramjet

## Definition

> [!note] Definition
> A ramjet has no turbomachinery. Ram compression in a supersonic diffuser raises the pressure, fuel burns at low subsonic speed, and a C–D nozzle expands the flow. A **scramjet** keeps the combustor flow supersonic.

## Explanation
**Ideal ramjet** ($\Gamma = 1$, fully expanded):
- $p_{04} = p_{01}$ and $p_4 = p_a$, so the exit temperature ratio equals the inlet one and **$M_e = M_0$**.
- $V_e = M_0\sqrt{\gamma RT_{03}/(1+\tfrac{\gamma-1}{2}M_0^2)}$.
- Specific thrust:

  $$\frac{F}{\dot m_a} = (1+f)V_e-V_0 = M_0\sqrt{\gamma RT_a}\left[(1+f)\sqrt{\frac{T_{03}}{T_a(1+\frac{\gamma-1}{2}M_0^2)}}-1\right]$$

  This derivation is asked in 2018-19 Q4(ii).

**"Given $f$ and $T_{max}$, find the flight speed"** (a classic 2013–18 question):
1. The energy balance gives $T_{02}$: $T_{02} = (1+f)T_{03}-f\,LCV/c_p$.
2. $M_0 = \sqrt{(T_{02}/T_a-1)/0.2}$.
3. $V_0 = M_0\sqrt{\gamma RT_a}$.
4. $M_e = M_0$, and $V_e = M_0\sqrt{\gamma RT_{03}/(T_{02}/T_a)}$.

**Real ramjet**: $p_{04}/p_a = \Gamma_d\Gamma_c\Gamma_np_{01}/p_a$ and $LCV_{eff} = \eta_bLCV$ (see [[Component Stagnation Pressure Ratios]]).

**Pros and cons**:
- Pros: simple, light, cheap, high thrust/weight, can run hotter.
- Cons: **needs to be boosted** to speed, very poor below M ≈ 2.5, thermal stress.

**Mach limits**:
- Lower: too little ram compression.
- Upper: decelerating to subsonic heats the air so much that the combustor-entry temperature approaches the material and dissociation limits. The lecture gives ramjet combustion up to M 4.2, and scramjets above that.

**Performance with Mach** (fixed $T_{03}$): the specific thrust peaks around M 2–2.5 and then falls to zero when $T_{02}\to T_{03}$. TSFC has a broad minimum near M 3–4.

**Runaway** (2016-17 Q4(iv), 2015-16 Q4(ii)): if the fuel flow, and hence $T_{03}$, is *not* held, more fuel gives more thrust, the aircraft accelerates, and ram compression and captured $\dot m\propto\rho V$ both rise. That gives more thrust again, a **positive feedback**. The SR-71 pilot must throttle back hard.

**SR-71 J58**:
- a translating spike and bypass doors position the shocks;
- above about M 2.2, bleed from the 4th compressor stage bypasses the core into the afterburner, so it runs as a turbo-ramjet;
- at M 3.2 most of the thrust comes from the inlet and ejector.

**Scramjet** (X-43A, M 9.6):
- supersonic combustion avoids the static-temperature rise;
- the challenges are mixing and ignition in milliseconds, thermal loads and thermal choking;
- it needs a boost (Pegasus launched from a B-52).

![[prop_ramjet_performance.png|700]]

## Examples
- Lecture: M 3 at 51,000 ft, $T_{03} = 1800$ K: $f = 0.0304$, $V_j = 1525$ m/s, $F/\dot m = 686$ m/s.
- PS4 Q4.1: 10 km, $f = 0.04$, 2400 K: **M 3.79, 1135 m/s**; $V_e = 1891$ m/s; $F/\dot m = 832$ m/s.
- Real ramjet PS4 Q4.2: $f = 0.0521$, $F/\dot m = 877$ m/s, $\dot m_a = 55.9$ kg/s, $\eta_O = 43.5\%$.

## Related
- [[Intake Pressure Recovery]] · [[Component Stagnation Pressure Ratios]] · [[Adiabatic Flame Temperature]] · [[Turbojet]]

## Sources
- Weeks 6–7 handout; Lectures 16, 18
