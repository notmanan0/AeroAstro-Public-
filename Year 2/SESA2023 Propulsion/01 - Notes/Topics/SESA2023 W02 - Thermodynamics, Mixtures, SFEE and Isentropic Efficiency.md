---
title: "SESA2023 W02 - Thermodynamics, Mixtures, SFEE and Isentropic Efficiency"
module: "SESA2023 Propulsion"
type: topic
stream: "Section 1: Introduction and Fundamentals"
order: 2
tags:
  - sesa2023
  - thermodynamics
  - sfee
  - entropy
  - isentropic-efficiency
aliases: ["Propulsion thermodynamics", "SFEE for a turbojet"]
date: 2026-09-24
status: complete
parent: ["[[SESA2023 Propulsion Hub]]"]
prerequisites: ["[[SESA2023 W01 - Thrust, Efficiency, Range and the ISA]]"]
next_topics: ["[[SESA2023 W03 - Compressible Flow, Normal Shocks and Nozzles]]"]
key_concepts: ["[[Two-Property Rule and Perfect Gas Model]]", "[[Gas Mixtures and Dalton's Law]]", "[[Steady Flow Energy Equation]]", "[[Entropy Change of a Perfect Gas]]", "[[Isentropic Efficiency]]"]
tutorial_sheets: ["[[SESA2023 Problem Sheet 2 Solutions]]"]
sources: ["02 - Sources/Lectures/Week 02 - Thermodynamics.pdf"]
---

# SESA2023 W02 - Thermodynamics, Mixtures, SFEE and Isentropic Efficiency

> [!abstract] Summary
> This week refreshes Part 1 thermodynamics with a propulsion slant:
> - equilibrium, the **two-property rule**, and the First Law;
> - ideal versus **perfect** gas (constant $c_p$, $c_v$);
> - gas **mixtures** (mass and mole fractions, Dalton's law, mass-weighted properties);
> - the **SFEE** applied component by component to a turbojet;
> - **entropy** changes, and **isentropic efficiency** to handle real compressors and turbines.

## Key Concepts
- [[Two-Property Rule and Perfect Gas Model]] · [[Gas Mixtures and Dalton's Law]] · [[Steady Flow Energy Equation]] · [[Entropy Change of a Perfect Gas]] · [[Isentropic Efficiency]]

---

## 1. Fundamentals (Lecture 4)
- **Thermodynamic equilibrium** requires thermal, mechanical, phase and chemical equilibrium, all on a macroscopic scale.
- **Zeroth Law**: if A and B are each in thermal equilibrium with C, then they are in equilibrium with each other.
- **Property types**:
  - intensive (independent of the amount): $T$, $p$;
  - extensive: $U$, $H$, $S$, $V$;
  - specific, i.e. per kg, lower case: $u$, $h$, $s$, $v$. Specific properties are intensive.
- **Warning**: $c_p$ is sometimes written $C_p$. Always check the units.
- **Two-property rule (state postulate)**: the state of a *simple compressible* system is fixed by **two independent intensive** properties. For an ideal gas $u = u(T)$ and $h = h(T)$, so $(T,h)$ are *not* independent. During a phase change $(p,T)$ are not independent either.
- **First Law**: $\Delta U = Q-W$, where $Q>0$ is heat added and $W>0$ is work done *by* the system. $Q$ and $W$ depend on the path; $\Delta U$ does not.
- **Model processes**:
  - isothermal ($\Delta u = 0$ for an ideal gas);
  - isobaric;
  - isochoric ($W = 0$);
  - adiabatic ($Q = 0$);
  - **isentropic** (adiabatic *and* reversible);
  - isenthalpic.
  
  Isobaric and isentropic are the ones that matter in propulsion.

> [!example] Adiabatic work on air
> Air at 300 K receives 100 kJ/kg of work adiabatically. As a perfect gas, $c_v(T_2-T_1) = -w_{12}$, so $T_2 = 300+100/0.718 = 439$ K.

### Ideal vs perfect gas
- **Ideal gas**: $p = \rho RT$, with $R = \bar R/M$ ($\bar R = 8.3145$ kJ kmol⁻¹ K⁻¹). $u$ and $h$ depend on $T$ only, and so do $c_v(T)$ and $c_p(T)$. It fails near phase changes and at $p$ approaching $p_{crit}$ (38 bar for air). At 20 bar the density error is still only about 1 %.
- **Perfect gas**: $c_p$ and $c_v$ are **constant**, so $\Delta h = c_p\Delta T$ and $\Delta u = c_v\Delta T$. This is good for small $\Delta T$ and monatomic gases. It is poor across a combustor, where air $c_p$ rises from 1005 to about 1200 J kg⁻¹ K⁻¹ by 1500 K. Hence the separate "product" $c_p$ used in later weeks.
- $c_p-c_v = R$ and $\gamma = c_p/c_v$. For air: $R = 287$, $c_p = 1005$, $\gamma = 1.4$.

## 2. Mixtures (Lecture 5)

$$
x_i = \frac{m_i}{m},\quad y_i = \frac{n_i}{n},\quad M = \sum y_iM_i = \Big(\sum\frac{x_i}{M_i}\Big)^{-1},\quad x_i = y_i\frac{M_i}{M}
$$

**Dalton's law** for ideal gases:

$$
\frac{p_i}{p} = \frac{V_i}{V} = \frac{n_i}{n} = y_i
$$

**Properties**: extensive properties add. Specific properties are **mass-weighted**:

$$
c_p = \sum x_ic_{p,i},\qquad h = \sum x_ih_i,\qquad s = \sum x_is_i
$$

> [!example] H₂/O₂ rocket mixture (PS1 data)
> 1 kg H₂ with 7.94 kg O₂:
> - $x_{H_2} = 1/8.94 = 0.112$;
> - $n_{H_2} = 0.5$ kmol and $n_{O_2} = 0.248$ kmol, so $y_{H_2} = 0.668$;
> - at 20 bar, $p_{H_2} = 13.36$ bar and $p_{O_2} = 6.64$ bar.

> [!example] $c_p$ of air
> $c_p = 0.232(0.92)+0.768(1.03) = 1.00$ kJ kg⁻¹ K⁻¹. Here 23.2 % O₂ and 76.8 % atmospheric N₂* are **mass** fractions; by volume air is 21/79.

## 3. Steady Flow Energy Equation (Lecture 6)

$$
\dot Q-\dot W_x = \sum_{out}\dot m\Big(h+\tfrac12V^2+gz\Big)-\sum_{in}\dot m\Big(h+\tfrac12V^2+gz\Big)
$$

Per unit mass, for a single stream (neglecting $gz$): $q-w_x = \Delta h+\Delta\tfrac12V^2 = \Delta h_0$.

**Turbojet components** (stations 1 intake, 2 compressor inlet, 3 burner inlet, 4 turbine inlet, 5 nozzle inlet, 6 exit):

| Component | Assumptions | SFEE result |
|---|---|---|
| Diffuser 1→2 | $q = w = 0$, exit KE ≈ 0 | $h_2 = h_1+\tfrac12V_1^2$ |
| Compressor 2→3 | adiabatic, KE negligible | $w_c = h_3-h_2$ |
| Burner 3→4 | constant $p$, no work | $q_{34} = h_4-h_3$ |
| Turbine 4→5 | adiabatic | $w_t = h_4-h_5 = w_c$ (turbine drives compressor) |
| Nozzle 5→6 | $q = w = 0$, inlet KE ≈ 0 | $\tfrac12V_6^2 = h_5-h_6$ |

With a perfect gas and reversible adiabatic processes, $T_2/T_1 = (p_2/p_1)^{(\gamma-1)/\gamma}$.

> [!example] Intake temperature rise
> Flight at 200 m/s, 250 K, 50 kPa:
> - $T_2 = 250+200^2/(2\times1005) = 270$ K;
> - $p_2 = 50(270/250)^{3.5} = 65$ kPa.

## 4. Entropy
$dS = \delta Q_{rev}/T$. Combining it with the First Law gives the **TdS equations**:

$$
T\,dS = dU+p\,dV,\qquad T\,dS = dH-V\,dp
$$

For a perfect gas:

$$
s_2-s_1 = c_p\ln\frac{T_2}{T_1}-R\ln\frac{p_2}{p_1} = c_v\ln\frac{T_2}{T_1}+R\ln\frac{v_2}{v_1} = c_v\ln\frac{p_2}{p_1}+c_p\ln\frac{v_2}{v_1}
$$

Irreversibilities (friction, turbulence, shocks) generate entropy. On a $T$–$s$ diagram, isobars **diverge** with temperature ($dT/ds|_p = T/c_p$). That is why a hot turbine expansion yields more work than a cold compression over the same pressure ratio, which is the whole reason a gas turbine produces net work.

## 5. Isentropic efficiency

$$
\eta_c = \frac{w_{c,s}}{w_c} = \frac{T_{2s}-T_1}{T_2-T_1},\qquad \eta_t = \frac{w_t}{w_{t,s}} = \frac{T_1-T_2}{T_1-T_{2s}}
$$

**Sanity checks**:
- $\eta<1$;
- the real exit is **hotter** than the isentropic exit in *both* machines;
- $w_c>w_{c,s}$;
- $w_t<w_{t,s}$.

![[prop_isentropic_efficiency_Ts.png|760]]

> [!example] Turbine: 30 bar, 1500 K → 1 bar, $\eta_t = 0.85$
> - $T_{5s} = 1500(1/30)^{0.4/1.4} = 567.6$ K
> - $T_5 = 1500-0.85(1500-567.6) = 707.5$ K
> - $w_t = 1.005(1500-707.5) = 796.5$ kJ/kg

## Links
- Parent: [[SESA2023 Propulsion Hub]] · Previous: [[SESA2023 W01 - Thrust, Efficiency, Range and the ISA]] · Next: [[SESA2023 W03 - Compressible Flow, Normal Shocks and Nozzles]]
- Thermofluids foundation: [[SESA1016 T4 - Entropy and Isentropic Relations]] · [[SESA1016 T5 - Ideal Heat Engine Models]] · [[SESA1016 T13 - Conservation of Energy and Propulsion]]
- Worked sheet: [[SESA2023 Problem Sheet 2 Solutions]] (includes the Mars compressor mixture question)
- Applied to whole engines: [[SESA2023 W06 - Jet Engine Cycle Analysis - Brayton, Ramjet, Turbojet and Reheat]]

## Sources
- Week 2 notes and Lectures 4–6; Thermofluids Data Book pp. 7–9, 14–16
