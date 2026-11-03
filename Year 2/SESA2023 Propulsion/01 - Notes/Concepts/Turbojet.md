---
title: "Turbojet"
module: "SESA2023 Propulsion"
type: concept
stream: "Section 3: Ramjets, Gas Turbines, Turbojets and Turbofans"
aliases: ["turbojet cycle analysis", "gas turbine", "specific thrust", "spool balance"]
tags: [sesa2023, concept, turbojet, cycle-analysis]
status: complete
parent_lectures: ["[[SESA2023 W06 - Jet Engine Cycle Analysis - Brayton, Ramjet, Turbojet and Reheat]]", "[[SESA2023 W07 - Turbofan Architectures and Fan Pressure Ratio Selection]]"]
related_concepts: ["[[Brayton Cycle]]", "[[Isentropic Efficiency]]", "[[Afterburning (Reheat)]]", "[[Adiabatic Flame Temperature]]", "[[Steady Flow Energy Equation]]"]
sources: ["02 - Sources/Lectures/Week 06-07 - Jet Engines.pdf", "02 - Sources/Lectures/Week 06-07 - Jet Engines.pdf"]
---

# Turbojet

A **turbojet** is a gas turbine with an intake (stations 1–2), a compressor (2–3), a burner (3–4), a turbine (4–5) that just drives the compressor, and a propelling nozzle (5–9). The excess pressure of the core is used entirely to accelerate the jet.

The cycle calculation has been examined almost every year from 2013 to 2020, and again in 2024-25. It runs through the engine station by station:

1. Inlet: $V = M\sqrt{\gamma RT_a}$, $T_{02} = T_a(1+0.2M^2)$ and $p_{02} = \Gamma_dp_a(1+0.2M^2)^{3.5}$.
2. Compressor: $T_{03s} = T_{02}r_c^{0.2857}$, $T_{03} = T_{02}+(T_{03s}-T_{02})/\eta_c$ and $p_{03} = r_cp_{02}$.
3. Burner: $f$ from the energy balance ([[Adiabatic Flame Temperature]]) and $p_{04} = (1-\Delta)p_{03}$.
4. Turbine: the spool balance $c_{p,a}(T_{03}-T_{02}) = (1+f)c_{p,p}(T_{04}-T_{05})$ gives $T_{05}$; then $T_{05s} = T_{04}-(T_{04}-T_{05})/\eta_t$ and $p_{04}/p_{05} = (T_{04}/T_{05s})^{\gamma/(\gamma-1)}$.
5. Nozzle: $p_{09} = \Gamma_np_{05}$ and, fully expanded, $V_j = \sqrt{2c_pT_{05}[1-(p_a/p_{09})^{(\gamma-1)/\gamma}]}$.
6. Performance: $F/\dot m_a = (1+f)V_j-V$, TSFC $= f/(F/\dot m_a)$, and $\eta_O$, $\eta_P$ and $\eta_{th}$.

If the nozzle is a choked convergent one rather than fully expanded, $V_j = a^*$ and there is a pressure thrust $A_9(p^*-p_a)$. The lecture example, M 2 at 31,000 ft with $r_c = 30$ and a turbine entry temperature of 1500 K, gives $F/\dot m = 341.2$ m/s, an sfc of 32.55 g/s/kN and $\eta_O = 43.1\%$.

The $T$–$s$ diagram comparing the ideal and real cycles was asked in 2013-14, 2014-15, 2016-17 and 2017-18. In the real cycle the compressor and turbine lines lean to the right as entropy rises, the burner line falls in pressure, the intake and nozzle losses reduce $p_0$, and the real $T_{05}$ is higher than the ideal value for the same work.

![[prop_turbojet_Ts.png|600]]

Turbojets are built single-spool (Viper) or twin-spool (Olympus 593), the latter for starting and off-design operation. Each shaft typically has a thrust (ball) bearing at the compressor end and roller bearings elsewhere to allow for thermal growth. Radial compressors are robust but have a large frontal area; axial ones are efficient and can be stacked.

Specific thrusts in past papers ([[SESA2023 Past Paper Map]]):

| Paper | $F/\dot m$ (N s/kg) |
|---|---|
| 2013-14 | 944 |
| 2014-15 | 1041 |
| 2015-16 | 798 |
| 2017-18 | 1071 |
| 2018-19 (real, with $\Gamma$) | 781 |
| 2020-21 dry | 831 |

## Related

- [[Brayton Cycle]] · [[Isentropic Efficiency]] · [[Afterburning (Reheat)]] · [[Adiabatic Flame Temperature]] · [[Steady Flow Energy Equation]]
