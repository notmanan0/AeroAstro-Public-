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

A **ramjet** has no turbomachinery: ram compression in a supersonic diffuser raises the pressure, fuel burns at low subsonic speed, and a converging–diverging nozzle expands the flow. A **scramjet** keeps the combustor flow supersonic.

In the ideal ramjet, with no losses and full expansion, $p_{04} = p_{01}$ and $p_4 = p_a$, so the exit temperature ratio equals the inlet one and the exit Mach number equals the flight Mach number, $M_e = M_0$. Then $V_e = M_0\sqrt{\gamma RT_{03}/(1+\tfrac{\gamma-1}{2}M_0^2)}$, and the specific thrust, derived in 2018-19 Q4(ii), is

$$
\frac{F}{\dot m_a} = (1+f)V_e-V_0 = M_0\sqrt{\gamma RT_a}\left[(1+f)\sqrt{\frac{T_{03}}{T_a(1+\frac{\gamma-1}{2}M_0^2)}}-1\right] .
$$

A classic question from 2013–18 gives $f$ and $T_{max}$ and asks for the flight speed. The energy balance gives $T_{02} = (1+f)T_{03}-f\,LCV/c_p$, so $M_0 = \sqrt{(T_{02}/T_a-1)/0.2}$ and $V_0 = M_0\sqrt{\gamma RT_a}$, and then $M_e = M_0$ with $V_e = M_0\sqrt{\gamma RT_{03}/(T_{02}/T_a)}$. In PS4 Q4.1, 10 km, $f = 0.04$ and 2400 K give M 3.79 and 1135 m/s, with $V_e = 1891$ m/s and $F/\dot m = 832$ m/s. A real ramjet adds the losses, $p_{04}/p_a = \Gamma_d\Gamma_c\Gamma_np_{01}/p_a$ and $LCV_{eff} = \eta_bLCV$ ([[Component Stagnation Pressure Ratios]]); PS4 Q4.2 gives $f = 0.0521$, $F/\dot m = 877$ m/s, $\dot m_a = 55.9$ kg/s and $\eta_O = 43.5\%$. The lecture example, M 3 at 51,000 ft with $T_{03} = 1800$ K, has $f = 0.0304$, $V_j = 1525$ m/s and $F/\dot m = 686$ m/s.

A ramjet is simple, light and cheap, has a high thrust-to-weight ratio and can run hotter than a turbojet, but it has to be boosted up to speed, performs very poorly below about M 2.5, and suffers thermal stress. Its lower Mach limit comes from too little ram compression. Its upper limit comes from the heating caused by decelerating to subsonic speed, which takes the combustor entry temperature towards the material and dissociation limits; the lecture gives ramjet combustion up to M 4.2, with scramjets above that. At fixed $T_{03}$ the specific thrust peaks around M 2–2.5 and falls to zero as $T_{02}\to T_{03}$, while TSFC has a broad minimum near M 3–4.

If the fuel flow, and with it $T_{03}$, isn't held, a ramjet runs away (2016-17 Q4(iv), 2015-16 Q4(ii)): more fuel gives more thrust, the aircraft accelerates, ram compression and the captured mass flow $\propto\rho V$ both rise, and the thrust rises again. That positive feedback is why the SR-71 pilot had to throttle back hard. The SR-71's J58 used a translating spike and bypass doors to position the shocks, and above about M 2.2 bled air from the fourth compressor stage round the core into the afterburner, running as a turbo-ramjet; at M 3.2 most of its thrust came from the inlet and ejector. The X-43A scramjet reached M 9.6. Supersonic combustion avoids the static-temperature rise, but mixing and ignition have to happen in milliseconds, and thermal loads and thermal choking are hard problems; it too needed a boost, from a Pegasus launched from a B-52.

![[prop_ramjet_performance.png|700]]

## Related

- [[Intake Pressure Recovery]] · [[Component Stagnation Pressure Ratios]] · [[Adiabatic Flame Temperature]] · [[Turbojet]]
