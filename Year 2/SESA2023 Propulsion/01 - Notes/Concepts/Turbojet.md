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

## Definition

> [!note] Definition
> A gas turbine with an intake (1–2), a compressor (2–3), a burner (3–4), a turbine (4–5) that just drives the compressor, and a propelling nozzle (5–9). The core's excess pressure is used entirely to accelerate the jet.

## Explanation
**Standard exam recipe** (examined almost every year from 2013 to 2020, and again in 2024-25):
1. **Inlet**: $V = M\sqrt{\gamma RT_a}$; $T_{02} = T_a(1+0.2M^2)$; $p_{02} = \Gamma_dp_a(1+0.2M^2)^{3.5}$.
2. **Compressor**: $T_{03s} = T_{02}r_c^{0.2857}$; $T_{03} = T_{02}+(T_{03s}-T_{02})/\eta_c$; $p_{03} = r_cp_{02}$.
3. **Burner**: $f$ from the energy balance (see [[Adiabatic Flame Temperature]]); $p_{04} = (1-\Delta)p_{03}$.
4. **Turbine** (the spool balance): $c_{p,a}(T_{03}-T_{02}) = (1+f)c_{p,p}(T_{04}-T_{05})$, which gives $T_{05}$. Then $T_{05s} = T_{04}-(T_{04}-T_{05})/\eta_t$ and $p_{04}/p_{05} = (T_{04}/T_{05s})^{\gamma/(\gamma-1)}$.
5. **Nozzle**: $p_{09} = \Gamma_np_{05}$; $V_j = \sqrt{2c_pT_{05}[1-(p_a/p_{09})^{(\gamma-1)/\gamma}]}$ (fully expanded).
6. **Performance**: $F/\dot m_a = (1+f)V_j-V$; TSFC $= f/(F/\dot m_a)$; $\eta_O$, $\eta_P$, $\eta_{th}$.

**Choked convergent nozzle** instead of full expansion: $V_j = a^*$ and pressure thrust $A_9(p^*-p_a)$.

**$T$–$s$ diagrams** (ideal vs real; 2013-14, 2014-15, 2016-17, 2017-18):
- the real compressor and turbine lines lean to the right (entropy rise);
- the burner line falls in pressure ($\Delta p_0$);
- intake and nozzle losses reduce $p_0$;
- the real $T_{05}$ is higher than the ideal value for the same work.

**Arrangement**:
- single spool (Viper) or twin spool (Olympus 593) for starting and off-design operation;
- bearings: typically a thrust (ball) bearing per shaft at the compressor end, with roller bearings elsewhere to allow thermal growth;
- radial compressors are robust but have a large frontal area; axial ones are efficient and stackable.

![[prop_turbojet_Ts.png|600]]

## Examples
- Lecture: M 2 at 31,000 ft, $r_c = 30$, TET 1500 K: $F/\dot m = 341.2$ m/s, sfc 32.55 g/s/kN, $\eta_O = 43.1\%$.
- Exam specific thrusts (see [[SESA2023 Past Paper Map]]):

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

## Sources
- Weeks 6–7 handout §6.5, §7.2.1; Lecture 19
