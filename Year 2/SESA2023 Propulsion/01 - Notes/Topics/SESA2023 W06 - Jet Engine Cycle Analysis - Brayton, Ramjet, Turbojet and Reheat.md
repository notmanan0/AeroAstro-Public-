---
title: "SESA2023 W06 - Jet Engine Cycle Analysis - Brayton, Ramjet, Turbojet and Reheat"
module: "SESA2023 Propulsion"
type: topic
stream: "Section 3: Ramjets, Gas Turbines, Turbojets and Turbofans"
order: 6
tags:
  - sesa2023
  - cycle-analysis
  - brayton
  - ramjet
  - turbojet
  - afterburner
aliases: ["Cycle analysis", "Turbojet analysis", "Ramjet analysis"]
date: 2026-09-24
status: complete
parent: ["[[SESA2023 Propulsion Hub]]"]
prerequisites: ["[[SESA2023 W05 - Combustion, Stoichiometry and Chemical Equilibrium]]", "[[SESA2023 W04 - Friction, Heat Addition, Oblique Shocks and Intakes]]"]
next_topics: ["[[SESA2023 W07 - Turbofan Architectures and Fan Pressure Ratio Selection]]"]
key_concepts: ["[[Brayton Cycle]]", "[[Ramjet]]", "[[Turbojet]]", "[[Afterburning (Reheat)]]", "[[Turbine Entry Temperature and Blade Cooling]]", "[[Component Stagnation Pressure Ratios]]"]
tutorial_sheets: ["[[SESA2023 Problem Sheet 4 Solutions]]", "[[SESA2023 Problem Sheet 7 Solutions]]"]
sources: ["02 - Sources/Lectures/Week 06-07 - Jet Engines.pdf"]
---

# SESA2023 W06 - Jet Engine Cycle Analysis - Brayton, Ramjet, Turbojet and Reheat

> [!abstract] Summary
> All air-breathing jets approximate a **Brayton cycle**: compress, heat at constant pressure, expand.
> - A **ramjet** compresses by ram effect only.
> - A **turbojet** adds a turbo-compressor driven by a turbine ($w_t = w_c$).
>
> **Method**: start from the atmosphere; convert to stagnation properties; march component by component (intake, compressor, burner, turbine, nozzle) with the SFEE, isentropic relations and isentropic efficiencies; finish with specific thrust, TSFC and $\eta_P$, $\eta_{th}$, $\eta_O$.
>
> **Real engines** lose performance through $\eta_c,\eta_t<1$, stagnation-pressure losses ($\Gamma$), the rising $c_p$ of products and cooling air.
>
> **Levers for efficiency**: overall pressure ratio, $T_{04}/T_{02}$ (hence blade cooling) and component efficiencies.
>
> **Afterburning (reheat)** buys thrust at a large sfc penalty.

## Key Concepts
- [[Brayton Cycle]] · [[Ramjet]] · [[Turbojet]] · [[Afterburning (Reheat)]] · [[Turbine Entry Temperature and Blade Cooling]] · [[Component Stagnation Pressure Ratios]]

---

## 1. Design requirements (Lecture 16)
An engine must give enough **thrust** and **efficiency**, but it is also constrained by:
- **safety and reliability**: take-off after one engine failure, overwater operation, altitude relight, containment of failures;
- **life-cycle cost**: development, materials, fuel, maintenance;
- **operations**: runway length, noise, emissions.

**Aviation's climate impact**: about 2.5 % of CO₂ and 3.5 % of effective radiative forcing. CORSIA (2016) and the IATA/ICAO net-zero-by-2050 goals (2021–22) push towards higher efficiency and sustainable aviation fuels.

### Why different engines for different speeds

$$
\eta_O = \eta_P\,\eta_{th},\qquad \eta_P\approx\frac{2V}{V+V_j},\qquad F_N\approx\dot m_a(V_j-V)
$$

| Flight regime | Engine | Reason |
|---|---|---|
| Low subsonic | Turboprop, open rotor | Huge effective $\dot m$, tiny $\Delta V$; limited by propeller-tip Mach |
| High subsonic (M 0.8) | High-bypass turbofan | Large $\dot m$ at moderate $V_j$ |
| Supersonic to M ≈ 2–2.3 | Turbojet / low-bypass turbofan, with reheat | High $V_j$ now matches $V$; combustor-entry temperature limit |
| M ≈ 2.5–5 | **Ramjet** | Ram compression alone reaches the pressure ratio; a compressor would overheat the air |
| M > 5 | **Scramjet** | Decelerating to subsonic would exceed temperature limits, so combustion is supersonic |

The lecture's operating limits: turbojet combustion to M < 2.3, ramjet to M < 4.2, scramjet above.

## 2. Ideal Brayton cycle (Lecture 17)
Isentropic compression, isobaric heating, isentropic expansion and isobaric cooling of cold air ($c_p = 1005$, $\gamma = 1.4$):

$$
\eta_{th} = \frac{w_{net}}{q_{in}} = 1-\frac{1}{r_p^{(\gamma-1)/\gamma}}
$$

This depends **only on the pressure ratio**. For $r_p = 30$ it is 62.2 %.

**Why real engines differ from the ideal cycle**:
- pressure losses in the intake, combustor and nozzle;
- non-isentropic turbomachinery;
- $c_p$ and $\gamma$ that vary with $T$, with product $c_p$ above air $c_p$;
- internal combustion (the fuel adds mass through the turbine);
- an open cycle (the exhaust goes to atmosphere);
- inlet conditions set by altitude and Mach number;
- zero net shaft work per spool;
- a nozzle back pressure that may differ from ambient.

![[prop_brayton_trends.png|760]]

**Trends with irreversibility** ($\eta_c = \eta_t = 0.9$):
- An **optimum pressure ratio** now exists for efficiency, and it rises with $T_{04}/T_{02}$.
- **Maximum specific work** occurs at a much lower $r_p$ (about 8–16).
- So fighters, which want thrust, use $r_p\approx15$; civil turbofans, which want range, use $r_p\approx45$.
- Raising **TET** raises both efficiency and specific work. Irreversibility hurts more at high $r_p$.

## 3. Modelling assumptions and their effect (Lecture 19, Table 2)
Base case: $r_p = 30$, $T_{04} = 1500$ K, flight at M 0.8 and 31,000 ft.

| Model | $\eta$ | Change |
|---|---|---|
| Ideal Brayton, cold air | 62.2 % | |
| + 90 % turbomachinery | 47.9 % | −14.3 pts (more $w_c$, less $w_t$) |
| Turbojet in flight (open cycle) | 61.0 % | +13.1 pts (ram compression; isentropic nozzle does part of the expansion) |
| Combustion instead of heating (same $c_p$) | 61.1 % | only the extra fuel mass flow |
| Products $c_p = 1100$, $\gamma = 1.35$ | 58.4 % | −2.7 pts |
| GasTurb equilibrium, semi-perfect gas | 58.6 % | |
| + 4 % combustor $\Delta p_0$ | 57.8 % | −0.8 pts |
| + 10 % cooling air | 55.7 % | −2.1 pts |

The simple cold-air model gets the **trends** right, which is why it is used for hand calculations. It is not quantitatively accurate.

## 4. Turbojet worked example (Lecture 19)
The engine flies at M 2.0 and 31,000 ft, with $T_1 = 226.73$ K and $p_1 = 28.7$ kPa. Its parameters are:
- $r_c = 30$ and $\eta_c = 0.90$;
- fuel with LCV 43 MJ/kg, supplied at 298 K;
- 4 % combustor $\Delta p_0$ and $T_{04} = 1500$ K;
- $\eta_t = 0.90$;
- an ideal, fully expanded nozzle;
- air with $c_p = 1005$ and $\gamma = 1.40$, and products with $c_p = 1100$ and $\gamma = 1.33$.

| Station | Working | Result |
|---|---|---|
| Inlet 1 | $V = M\sqrt{\gamma RT_1}$; $T_{01} = T_1(1+0.2M^2)$; $p_{01} = p_1(\cdot)^{3.5}$ | $V = 603.7$ m/s, $T_{01} = 408.1$ K, $p_{01} = 224.6$ kPa |
| Intake 1→2 | adiabatic, isentropic | $T_{02} = 408.1$ K, $p_{02} = 224.6$ kPa |
| Compressor 2→3 | $T_{03s} = T_{02}(30)^{0.2857}$; $T_{03} = T_{02}+(T_{03s}-T_{02})/\eta_c$ | $T_{03s} = 1078.5$ K, $T_{03} = 1153.0$ K, $p_{03} = 6736.9$ kPa, $w_c = 748.6$ kJ/kg |
| Burner 3→4 | $f = \dfrac{c_{p,a}(T_{ref}-T_{03})+c_{p,p}(T_{04}-T_{ref})}{LCV-c_{p,p}(T_{04}-T_{ref})}$ | $f = 0.01111$, $p_{04} = 6467.4$ kPa |
| Turbine 4→5 | $\dot m_ac_{p,a}(T_{03}-T_{02}) = (1+f)\dot m_ac_{p,p}(T_{04}-T_{05})$ | $T_{05} = 826.9$ K, $T_{05s} = 752.2$ K, $p_{05} = 400.4$ kPa |
| Nozzle 5→6 | $T_6 = T_{05}(p_a/p_{05})^{0.33/1.33}$; $V_j = \sqrt{2c_p(T_{05}-T_6)}$ | $T_6 = 430.0$ K, $V_j = 934.5$ m/s |

**Performance**:
- $F_N/\dot m_a = (1+f)V_j-V = 341.2$ m/s
- sfc $= f/(F_N/\dot m_a) = 32.55$ g s⁻¹ kN⁻¹
- $\eta_O = 43.1\%$, $\eta_{th} = 54.3\%$, $\eta_P = 79.4\%$

![[prop_turbojet_Ts.png|640]]

> [!tip] Exam technique (Lecture 19 summary)
> 1. State your assumptions.
> 2. Draw the schematic with station numbers.
> 3. Sketch the $T$–$s$ diagram.
> 4. Write the SFEE in full, then simplify it for each component.
> 5. Check that the real compressor and turbine exits are hotter than their isentropic values.

## 5. Turbine entry temperature and cooling
- TET is limited by turbine materials. Single-crystal Ni superalloys melt at about 1500 K, and creep, oxidation and thermal fatigue set the working limit lower.
- Typical high-bypass values: take-off 1750 K ($T_{04}/T_{02} = 6.07$), top of climb 1600 K (6.52; highest rotational speed), cruise 1500 K (6.11; sets engine life).
- **Cooling** uses compressor air at 800–900 K:
  - **convective** (internal passages);
  - **film** (holes and slots blanketing the surface);
  - **thermal barrier coatings**, worth about 100 K.
- 15–25 % of compressor air goes to cooling. It costs compression work and adds mixing and throttling losses, so there is an **optimum** between the TET gain and the cooling loss.

See [[Turbine Entry Temperature and Blade Cooling]].

## 6. Ramjet (Lecture 18)
A ramjet is a supersonic diffuser (normal or oblique shocks, then a subsonic diffuser to M ≈ 0.2–0.3), then a combustor, then a C–D nozzle.

**Pros**:
- simple, with a high thrust/weight ratio;
- runs at a higher combustor-exit temperature;
- reliable.

**Cons**:
- needs an initial speed (it is boosted);
- poor efficiency below M ≈ 2.5;
- thermal stress.

It was used in the SR-71's J58 (turbo-ramjet, M 3.2).

**Ideal ramjet** ($\Gamma_d = \Gamma_c = \Gamma_n = 1$, fully expanded): $p_{04} = p_{01}$ and $p_4 = p_1$, so $T_{04}/T_4 = T_{01}/T_1$ and **$M_e = M_0$**.

$$
V_e = M_0\sqrt{\gamma RT_{03}/(1+\tfrac{\gamma-1}{2}M_0^2)},\qquad \frac{F}{\dot m_a} = (1+f)V_e-V_0 = M_0\sqrt{\gamma RT_a}\left[(1+f)\sqrt{\frac{T_{03}}{T_{02}}}-1\right]
$$

> [!example] Ramjet at 51,000 ft, M 3, $T_{03} = 1800$ K, LCV 41 MJ/kg at 298 K
> - $V = 885.1$ m/s, $T_{01} = 606.2$ K, $p_{01} = 4.077$ bar.
> - $f = \dfrac{1800-606.2}{41\times10^6/1005-(1800-298)} = 0.03037$.
> - $V_j = 1525.1$ m/s, so $F/\dot m_a = 686.3$ m/s.

![[prop_ramjet_performance.png|760]]

**Real ramjet**:
- stagnation-pressure ratios $\Gamma_d = p_{02}/p_{01}$, $\Gamma_c = p_{03}/p_{02}$, $\Gamma_n = p_{04}/p_{03}$;
- combustion efficiency $\eta_b = LCV_{eff}/LCV$.

Then $p_{04}/p_a = \Gamma_d\Gamma_c\Gamma_n\,p_{01}/p_a$, and the jet expands through a smaller pressure ratio, giving less thrust. See [[Component Stagnation Pressure Ratios]].

> [!warning] Which energy balance for $f$?
> - **Lecture form** (fuel at $T_{ref}$): $f = \dfrac{T_{03}-T_{02}}{LCV/c_p-(T_{03}-T_{ref})}$.
> - **PS4 and the pre-2020 papers** effectively set $T_{ref}$ = 0: $(1+f)c_pT_{03} = c_pT_{02}+f\,LCV$.
>
> The difference is only about 1 %. State whichever you use.

## 7. Reheat (afterburning)
- Burn extra fuel downstream of the turbine (stations 6–7) so $T_{06}\uparrow$ gives a bigger $V_j$.
- It needs a **variable-area nozzle**: for a choked nozzle $\dot m\propto A_8p_{06}/\sqrt{T_{06}}$, so $A_8\propto\sqrt{T_{06}}$ to hold the engine operating point.
- The heat is added at **lower pressure** than in the main combustor, so the effective pressure ratio is lower and efficiency worse. That is why it is used only briefly (take-off, intercept, transonic acceleration).
- If more thrust is needed all mission, a bigger dry engine is more efficient.

See [[Afterburning (Reheat)]] and [[SESA2023 Exam 2020-21 Solutions]] Q3 ($A_8$ increases by 24 %).

## Links
- Parent: [[SESA2023 Propulsion Hub]] · Previous: [[SESA2023 W05 - Combustion, Stoichiometry and Chemical Equilibrium]] · Next: [[SESA2023 W07 - Turbofan Architectures and Fan Pressure Ratio Selection]]
- Worked sheets: [[SESA2023 Problem Sheet 4 Solutions]] (ramjets), [[SESA2023 Problem Sheet 7 Solutions]] (cycle trends, combustor fuel flow)
- Exam staples: turbojet specific thrust (2013-14, 2014-15, 2015-16, 2016-17, 2017-18, 2018-19, 2020-21, 2024-25) and ideal ramjet flight speed (2013-14 to 2017-18). See [[SESA2023 Past Paper Map]].

## Sources
- Weeks 6–7 handout (E. Richardson) §6 and Lectures 16–19
