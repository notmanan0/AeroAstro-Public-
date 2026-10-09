---
title: "SESA2023 W01 - Thrust, Efficiency, Range and the ISA"
module: "SESA2023 Propulsion"
type: topic
stream: "Section 1: Introduction and Fundamentals"
order: 1
tags:
  - sesa2023
  - thrust
  - efficiency
  - breguet-range
  - isa
aliases: ["Propulsion fundamentals", "Thrust and efficiency"]
date: 2026-09-24
status: complete
parent: ["[[SESA2023 Propulsion Hub]]"]
prerequisites: []
next_topics: ["[[SESA2023 W02 - Thermodynamics, Mixtures, SFEE and Isentropic Efficiency]]"]
key_concepts: ["[[Thrust Equation]]", "[[Propulsive Efficiency]]", "[[Thermal and Overall Efficiency]]", "[[Thrust Specific Fuel Consumption]]", "[[Breguet Range Equation]]", "[[International Standard Atmosphere]]"]
tutorial_sheets: ["[[SESA2023 Problem Sheet 1 Solutions]]"]
sources: ["02 - Sources/Lectures/Week 01 - Introduction and Fundamentals.pdf"]
---

# SESA2023 W01 - Thrust, Efficiency, Range and the ISA

> [!abstract] Summary
> Thrust comes from a **momentum balance on a control volume**: momentum flux out minus momentum flux in, plus a pressure term at the exit. A rocket carries everything it expels, so it has no inlet momentum. An air-breather captures air at $V_0$ and throws it out at $V_j$. How well it does this is split into **thermal efficiency** (heat → jet kinetic energy) and **propulsive efficiency** (jet KE → useful work $FV_0$). The product is the **overall efficiency**, which, through **TSFC**, sets the aircraft's **Breguet range**. Engine conditions at altitude come from the **International Standard Atmosphere**.

## Key Concepts
- [[Thrust Equation]] · [[Propulsive Efficiency]] · [[Thermal and Overall Efficiency]] · [[Thrust Specific Fuel Consumption]] · [[Breguet Range Equation]] · [[International Standard Atmosphere]]

---

## 1. Module map (Lecture 1)

| Section | Weeks | Lecturer |
|---|---|---|
| Fundamentals: thermodynamics, gas dynamics | 1–4 | T. Grenga |
| Combustion | 5 | T. Grenga |
| Ramjets, gas turbines, turbojets, turbofans | 6–7 | E. Richardson |
| Turbomachinery (and propellers) | 8–9 | E. Richardson |
| Rockets | 10–11 | T. Grenga (with E. Richardson) |

**Assessment**: 80 % sit-down exam and 20 % coursework. The coursework is three quizzes (3 % each) and two labs (nozzle lab, propulsion/ramjet lab; 5.5 % each).

**Two families of propulsion**:
- **Rocket** (non-air-breathing): carries fuel **and oxidiser**. There is no momentum in, so all the momentum out is thrust.
- **Air-breathing**: captures air (free oxidiser and working fluid) and carries only fuel. The price is the **ram drag** $\dot m_aV_0$ of the captured air.

## 2. Thrust from momentum conservation

$$
\dot M_{x,out}-\dot M_{x,in} = \sum F_x
$$

Put the control volume around the engine, in the engine's frame, so the thrust is the force $F$ needed to hold it still.

**Rocket** (no inlet, uniform exhaust $V_j$, exit area $A_j$, exit pressure $P_j$, ambient $P_A$):

$$
F = \dot mV_j+A_j(P_j-P_A)
$$

**Jet engine** (air enters at $V_0$, fuel added so $\dot m_{out} = \dot m_a+\dot m_f$):

$$
F = (\dot m_a+\dot m_f)V_j-\dot m_aV_0+A_j(P_j-P_A) = \dot m_a\big[(1+f)V_j-V_0\big]+A_j(P_j-P_A),\qquad f = \frac{\dot m_f}{\dot m_a}
$$

- **Gross thrust** $\dot m_a(1+f)V_j$ minus **ram drag** $\dot m_aV_0$, plus **pressure thrust**.
- **Fully expanded** ($P_j = P_A$) and $f\ll1$ give $F = \dot m_a(V_j-V_0)$.
- Rocket thrust **rises with altitude** because $P_A$ falls. A fully expanded rocket at sea level gains $A_jP_A$ in vacuum. See [[SESA2023 Problem Sheet 1 Solutions]] Q1.1: 2000 kN becomes 2318 kN.

## 3. Breguet range equation (Lecture 2)
In steady cruise $F = D$ and $L = W$, so $W = F(L/D)$. Fuel burn reduces the weight: $dW/dt = -\dot m_fg_0 = -\text{TSFC}\cdot F\cdot g_0$. Then

$$
\frac{dW}{W} = -\frac{g_0\,\text{TSFC}}{L/D}dt = -\frac{g_0\,\text{TSFC}}{V_0(L/D)}ds
$$

Integrate from $W_1$ (start) to $W_2$ (end):

$$
\boxed{s = \frac{L}{D}\,\frac{V_0}{g_0\,\text{TSFC}}\ln\frac{W_1}{W_2}}\qquad\left(= \frac{C_L}{C_D}\frac{V_0}{g_0\,\text{TSFC}}\ln\frac{W_1}{W_2}\right)
$$

> [!example] Boeing 777-200 (lecture)
> MTOW 243 t, fuel burned 42 t, $V_0 = 248$ m/s (M 0.84), $L/D = 20$, sfc $= 1.614\times10^{-5}$ kg s⁻¹ N⁻¹:
>
> $$s = 20\times\frac{248}{9.81\times1.614\times10^{-5}}\ln\frac{243}{201} = 5944\text{ km}$$
>
> The published range at maximum payload is 6112 km.

Written with overall efficiency (since $\text{TSFC} = V_0/(\eta_O\,LCV)$):

$$
s = \eta_O\frac{LCV}{g_0}\frac{L}{D}\ln\frac{W_1}{W_2}
$$

Range is maximised by high $\eta_O$ (engine), high $L/D$ (aerodynamics) and a high fuel fraction (structures). Range is **inversely proportional to TSFC**. This appears in exam derivations in 2014-15, 2016-17 and 2023-24. See [[Breguet Range Equation]].

## 4. Efficiencies (Lecture 3)
The energy chain is: fuel heat $\dot Q_{in} = \dot m_fLCV$ → **(thermal)** → jet power $\dot W_{jet}$ → **(propulsive)** → aircraft power $FV_0$.

$$
\eta_O = \eta_P\times\eta_{th}
$$

| Efficiency | Definition | Simplified ($P_j = P_A$, $f\ll1$) |
|---|---|---|
| Propulsive | $\eta_P = \dfrac{FV_0}{\tfrac12\dot m_a[(1+f)V_j^2-V_0^2]}$ | $\dfrac{2}{1+V_j/V_0}$ |
| Thermal | $\eta_{th} = \dfrac{\tfrac12\dot m_a[(1+f)V_j^2-V_0^2]}{\dot m_fLCV}$ | $\dfrac{V_j^2-V_0^2}{2f\,LCV}$ |
| Overall | $\eta_O = \dfrac{FV_0}{\dot m_fLCV}$ | $\dfrac{V_0(V_j-V_0)}{f\,LCV} = \dfrac{V_0}{\text{TSFC}\cdot LCV}$ |

The **LCV** (lower calorific value) is the enthalpy released at 298.15 K and 1 bar with water left as **vapour**.

![[prop_propulsive_efficiency.png|700]]

**The design dilemma**:
- $\eta_P\to1$ as $V_j\to V_0$, but $F = \dot m_a(V_j-V_0)\to0$.
- The only way to keep thrust at low jet velocity is a **large air mass flow**, hence ever-bigger fans (Jumo 004 → GE90), with costs in drag, weight and ground clearance.
- $\eta_{th}$ is improved by raising the **overall pressure ratio** (from about 15 to over 40 in 40 years) and the **turbine entry temperature** (from about 1000 K to about 1800 K, made possible by blade cooling).
- Current engines have $\eta_P\approx0.6$–0.7 and $\eta_{th}\approx0.5$–0.6, so $\eta_O\approx0.3$–0.4.

> [!example] Boeing 777 cruise (lecture numbers)
> $\dot m_a = 1295$ kg/s, $V_0 = 251$ m/s, $V_j = 299$ m/s, $\dot m_f = 0.58$ kg/s, $LCV = 44.65$ MJ/kg:
> - $F = 1295(299-251) = 62.2$ kN
> - $f = 4.48\times10^{-4}$
> - $\eta_P = 2/(1+299/251) = 91\%$
> - $\eta_{th} = (299^2-251^2)/(2f\,LCV) = 66\%$
> - $\eta_O = FV_0/(\dot m_fLCV) = 60\% = 0.91\times0.66$ ✔
>
> These numbers are illustrative only. A real cruise $\eta_O$ is about 35 %; the slide's fuel flow and jet velocity are too low.

## 5. International Standard Atmosphere
Tables give ratios to sea level: $\delta = p/p_{ref}$, $\theta = T/T_{ref}$, $\sigma = \rho/\rho_{ref}$. The reference values are $p_{sl} = 101.325$ kPa, $T_{sl} = 288.15$ K and $\rho_{sl} = 1.225$ kg/m³.
- **Troposphere** (0–11 km): $T = 288.15-6.5h$ [km].
- **Lower stratosphere** (11–20 km): $T = 216.65$ K. Pressure falls exponentially.

The data book gives **Table 24** (selected altitudes in ft) and **Table 25** (every km).

![[prop_isa.png|640]]

| Altitude | $T$ (K) | $p$ (kPa) | Used in |
|---|---|---|---|
| 2 km | 275.15 | 79.50 | PS2 Q2.3 |
| 6 km | 249.19 | 47.22 | intake exercise (W04) |
| 10 km | 223.26 | 26.50 | PS4 Q4.1 |
| 31,000 ft | 226.73 | 28.7 | turbojet worked example, 2020-21 Q3 |
| 35,000 ft | 218.81 | 23.8 | turbofan exercises (W07), 2020-21 Q4 |
| 15 km | 216.66 | 12.11 | 2024-25 Q1 |
| 20 km | 216.66 | 5.53 | 2021-22 Q2, 2023-24 Q1–Q2 |
| 51,000 ft | 216.65 | 11.1 | ramjet lecture example |

See [[International Standard Atmosphere]].

## Links
- Parent: [[SESA2023 Propulsion Hub]] · Next: [[SESA2023 W02 - Thermodynamics, Mixtures, SFEE and Isentropic Efficiency]]
- Thermofluids foundation: [[SESA1016 T12 - Conservation of Momentum]] · [[SESA1016 T13 - Conservation of Energy and Propulsion]]
- Worked sheet: [[SESA2023 Problem Sheet 1 Solutions]]
- Reused in every engine calculation: [[SESA2023 W06 - Jet Engine Cycle Analysis - Brayton, Ramjet, Turbojet and Reheat]]

## Sources
- Week 1 notes (I. Peters, T. Grenga) and Lectures 1–3 slides; Mattingly, *Elements of Propulsion*, App. A (altitude tables)
