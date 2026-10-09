---
title: "SESA2023 Problem Sheet 7 Solutions"
module: "SESA2023 Propulsion"
type: tutorial
stream: "Section 3: Ramjets, Gas Turbines, Turbojets and Turbofans"
tags:
  - sesa2023
  - tutorial-solutions
  - cycle-analysis
  - brayton
sheet: "Exercises Week 7 (gas-turbine cycle)"
theory_notes: ["[[SESA2023 W06 - Jet Engine Cycle Analysis - Brayton, Ramjet, Turbojet and Reheat]]"]
key_concepts: ["[[Brayton Cycle]]", "[[Isentropic Efficiency]]", "[[Turbine Entry Temperature and Blade Cooling]]", "[[Adiabatic Flame Temperature]]"]
status: complete
sources: ["02 - Sources/Tutorial Sheets/Problem Sheet Week 07.pdf"]
---

# SESA2023 Problem Sheet 7 Solutions

> [!abstract] Sheet Info
> A gas-turbine cycle with cold air ($c_p = 1005$, $\gamma = 1.4$). It covers compressor and turbine work, thermal efficiency and net work at five operating points (take-off, hot day, climb, cruise, degraded), and a combustor fuel flow. All the printed answers are reproduced ✔. (The sheet says worked solutions are on Blackboard.)

## Theory Links
- [[SESA2023 W06 - Jet Engine Cycle Analysis - Brayton, Ramjet, Turbojet and Reheat]]
- [[Brayton Cycle]] · [[Isentropic Efficiency]] · [[Turbine Entry Temperature and Blade Cooling]] · [[Adiabatic Flame Temperature]]

---

## Q7.1: Compressor, $T_{02} = 288$ K, $p_{02} = 1$ bar, $r_p = 45$

$$
T_{03s} = 288(45)^{0.2857} = 288(2.9674) = \boxed{854.6\text{ K}}\ (\eta_c = 1)
$$

$$
T_{03} = 288+\frac{854.6-288}{0.9} = \boxed{917.5\text{ K}}\ (\eta_c = 0.9),\qquad w_c = 1.005(917.5-288) = \boxed{632\text{ kJ/kg}}\;✔
$$

## Q7.2: Turbine, $T_{04} = 1750$ K, pressure ratio 45, $\eta_t = 0.9$

$$
T_{05s} = \frac{1750}{2.9674} = 589.7\text{ K},\qquad w_t = 0.9(1.005)(1750-589.7) = \boxed{1049\text{ kJ/kg}}\;✔
$$

This is 1.66× the compressor work. The surplus is the net work.

## Q7.3: Thermal efficiency and net work, $\eta_{th} = (w_t-w_c)/[c_p(T_{04}-T_{03})]$

| Case | $T_{02}$ (K) | $T_{04}$ (K) | $r_p$ | $\eta_c = \eta_t$ | $T_{03}$ (K) | $w_c$ | $w_t$ | $\eta_{th}$ | $w_{net}$ (kJ/kg) |
|---|---|---|---|---|---|---|---|---|---|
| (a) SL take-off | 288 | 1750 | 45 | 0.90 | 917.5 | 632.7 | 1049.4 | **0.498** | **417** ✔ |
| (b) hot day | 308 | 1750 | 45 | 0.90 | 981.2 | 676.6 | 1049.4 | **0.483** | **373** ✔ |
| (c) top of climb | 245 | 1600 | 50 | 0.90 | 805.2 | 563.0 | 973.9 | **0.514** | **411** ✔ |
| (d) cruise | 245 | 1500 | 45 | 0.90 | 780.5 | 538.2 | 899.5 | **0.500** | **361** ✔ |
| (e) degraded cruise | 245 | 1500 | 45 | 0.85 | 812.0 | 569.9 | 849.5 | **0.404** | **280** ✔ |

**Discussion**:
- **Inlet temperature**, (a) vs (b): 20 K hotter at the inlet means more compressor work for the same turbine work, so 10 % less specific power. The real power loss is about 3.5 % more again, because the hotter air is less dense ($\dot m$ falls). Hot-day take-off is the critical case.
- **TET, relative to inlet temperature**: $T_{04}/T_{02}$ is 6.53 at top of climb against 6.12 at cruise. A higher ratio raises $\eta_{th}$ and raises $w_{net}$ even more.
- **Pressure ratio**: with irreversible machines, raising $r_p$ only helps if the TET rises with it. Case (c) uses 50 at the higher temperature ratio.
- **Component efficiency**, (d) vs (e): dropping $\eta$ by 5 points cuts $\eta_{th}$ by 10 points and $w_{net}$ by 22 %. The net work is a small difference of two large numbers, so it is very sensitive.
- These cycle efficiencies (≈ 50 %) exceed a good truck diesel's overall 40 %, but this is a thermal efficiency, not an overall one. Real power falls fast with altitude, because $\dot m\propto\rho$.

## Q7.4: Combustor fuel flow
Data: 30 kg/s of air at 800 K to 1500 K; fuel at 298 K; LCV 43 MJ/kg; $c_{p,air} = 1005$ and $c_{p,prod} = 1250$ J kg⁻¹ K⁻¹. The SFEE uses the three-step path (air cooled to 298 K, reaction, products heated):

$$
0 = \dot m_ac_{p,a}(298-800)-\dot m_fLCV+(\dot m_a+\dot m_f)c_{p,p}(1500-298)
$$

$$
f = \frac{c_{p,p}(1202)-c_{p,a}(502)}{LCV-c_{p,p}(1202)} = \frac{1.5025\times10^6-0.5045\times10^6}{43\times10^6-1.5025\times10^6} = 0.02405
$$

$$
\dot m_f = 30f = \boxed{0.721\text{ kg/s}}\;✔
$$

$f = 0.024$ is very lean against a stoichiometric $f_{st}\approx0.068$ ($\phi\approx0.35$). The temperature is also too low for significant dissociation, so assuming complete combustion is reasonable.

## Sources
- `02 - Sources/Tutorial Sheets/Problem Sheet Week 07.pdf`. All values checked in Python.
