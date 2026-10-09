---
title: "SESA2023 W10 - Rocket Performance, Staging and Power Cycles"
module: "SESA2023 Propulsion"
type: topic
stream: "Section 5: Rockets"
order: 10
tags:
  - sesa2023
  - rockets
  - specific-impulse
  - staging
  - power-cycles
aliases: ["Rockets I", "Rocket staging"]
date: 2026-09-24
status: complete
parent: ["[[SESA2023 Propulsion Hub]]"]
prerequisites: ["[[SESA2023 W03 - Compressible Flow, Normal Shocks and Nozzles]]"]
next_topics: ["[[SESA2023 W11 - Solid Propellants and Rocket Nozzle Design]]"]
key_concepts: ["[[Rocket Performance Parameters]]", "[[Tsiolkovsky Rocket Equation]]", "[[Rocket Staging]]", "[[Rocket Engine Power Cycles]]", "[[Critical Conditions and Choked Flow]]"]
tutorial_sheets: ["[[SESA2023 Problem Sheet 10 Rockets Solutions]]"]
sources: ["02 - Sources/Lectures/Week 10 - Rockets.pdf", "02 - Sources/Lectures/Week 10 - Rockets - Lecture Slides.pdf"]
---

# SESA2023 W10 - Rocket Performance, Staging and Power Cycles

> [!abstract] Summary
> A rocket carries all of its propellant, so the aim is to get the most impulse per kg: **maximise $V_j$**. That means high chamber stagnation temperature and pressure and a well-expanded nozzle.
>
> **Performance parameters**:
> - $I_{sp}$ and the effective exhaust velocity $c_e$;
> - $C^*$ (combustion performance);
> - $C_F$ (nozzle performance), with $c_e = C^*C_F$.
>
> The **Tsiolkovsky equation** $\Delta V = c_e\ln(m_0/m_{bo})$ shows why **staging** is essential: discarding dead weight lets the mass ratios multiply.
>
> **Solid** motors are simple but uncontrollable. **Liquid** engines need a feed system, and their **power cycles** (pressure-fed, expander, gas generator, staged combustion) trade complexity for chamber pressure.

## Key Concepts
- [[Rocket Performance Parameters]] · [[Tsiolkovsky Rocket Equation]] · [[Rocket Staging]] · [[Rocket Engine Power Cycles]]

---

## 1. Rocket thrust and the ideal jet velocity (Lecture 28)

$$
F = \dot mV_j+A_e(P_e-P_A)
$$

Unlike an air-breather, a rocket wants a **small $\dot m$ and a large $V_j$**.

Assume an adiabatic nozzle ($T_{0c} = T_{0e}$), isentropic flow and full expansion ($P_e = P_A$). The SFEE gives $\tfrac12V_e^2 = h_{0c}-h_e$, so

$$
\boxed{V_j = \sqrt{2c_pT_{0c}\left[1-\left(\frac{P_e}{P_{0c}}\right)^{\frac{\gamma-1}{\gamma}}\right]}}
$$

To raise $V_j$, raise $T_{0c}$ and $P_{0c}/P_e$, and choose a light exhaust. For a given $T$, a lower molar mass gives a larger $c_pT = \frac{\gamma}{\gamma-1}\frac{\bar R}{M}T$. Returns diminish in the pressure ratio.

In practice the nozzle is a **regenerative heat exchanger** (fuel cooling), so "adiabatic" is an approximation.

![[prop_rocket_nozzle.png|760]]

## 2. Performance parameters

| Parameter | Definition | Measures |
|---|---|---|
| Total impulse | $I_T = \int_0^tF\,dt$ | |
| Specific impulse | $I_{sp} = \dfrac{I_T}{g_0m_p} = \dfrac{F}{g_0\dot m}$ (s) | overall engine |
| Effective exhaust velocity | $c_e = F/\dot m = g_0I_{sp}$ | overall; includes pressure thrust and non-uniformity |
| Characteristic velocity | $C^* = \dfrac{P_cA_t}{\dot m}$ | **combustor** (set at the choked throat; independent of the diverging section) |
| Thrust coefficient | $C_F = \dfrac{F}{P_cA_t}$ | **nozzle** expansion |

$$
c_e = C^*C_F,\qquad I_{sp} = \frac{C^*C_F}{g_0}
$$

For an ideal choked throat, $C^* = \sqrt{RT_{0c}/\gamma}\,\big(\tfrac{\gamma+1}{2}\big)^{\frac{\gamma+1}{2(\gamma-1)}}$, which depends only on the combustion products.

> [!example] Saturn V F-1: $T_c = 3600$ K, $P_c = 70$ bar, $A_e/A_t = 16$, $F = 7.7$ MN, $I_{sp} = 305$ s ($\gamma = 1.24$, $R = 356.8$, $c_p = 1844$)
> - Theoretical $V_j$ expanding to 24 km ($P_A = 2.97$ kPa) is 3213 m/s, against the effective $c_e = 9.81(305) = 2992$ m/s.
> - $\dot m = F/(g_0I_{sp}) = 2573$ kg/s. The choked-flow formula gives $A_t = 0.635$ m² ($D_t = 0.90$ m) and $A_e = 10.16$ m² ($D_e = 3.6$ m).
>
> ⚠ **Inconsistency on the slide.** An isentropic expansion through $A_e/A_t = 16$ at $\gamma = 1.24$ only reaches $M_e = 3.76$ and $p_e = 42$ kPa, which is a design altitude of about 7 km, not 24 km. The 3213 m/s is therefore an *upper bound* for this nozzle.

## 3. Mass ratios and the rocket equation (Lecture 29)

$$
m_0 = m_{pl}+m_p+m_{dw},\quad m_{bo} = m_{pl}+m_{dw},\quad MR = \frac{m_0}{m_{bo}} = \frac{1}{\lambda+\delta},\quad \lambda = \frac{m_{pl}}{m_0},\ \delta = \frac{m_{dw}}{m_0}
$$

The thrust is $F = \dot mc_e$ with $\dot m = -dm/dt$, so $m\,dV/dt = -c_e\,dm/dt$. Integrating:

$$
\boxed{\Delta V_{ideal} = c_e\ln\frac{m_0}{m_{bo}} = c_e\ln\frac{1}{\lambda+\delta}}\qquad\Delta V = \Delta V_{ideal}-\int_0^tg\sin\psi\,dt-\int_0^t\frac{D}{m}dt
$$

**Losses**:
- **Drag** $D = \tfrac12\rho V^2SC_D$ favours a slow, vertical climb out of the dense air.
- **Gravity loss** favours high acceleration and a small $\psi$.

The compromise is to lift off vertically and slowly (the vehicle is heavy anyway), then pitch over in a **gravity turn**.

## 4. Staging
Stage $i$'s payload is the whole upper stack, $(m_{pl})_i = (m_0)_{i+1}$. Then

$$
\lambda_i = \exp\!\left(-\frac{\Delta V_i}{c_{e,i}}\right)-\delta_i,\qquad (m_0)_i = \frac{(m_{pl})_i}{\lambda_i},\qquad \lambda_0 = \prod\lambda_i,\qquad \Delta V_0 = \sum\Delta V_i
$$

**Work from the top stage down.** The biggest gain comes from going from one to two stages; more stages give diminishing returns and add complexity.

![[prop_rocket_staging.png|640]]

> [!example] Saturn V (payload 43.5 t)
>
> | Stage | $m_0$ (t) | $\lambda$ | $\delta$ | $c_e$ (m/s) | $\Delta V$ (m/s) |
> |---|---|---|---|---|---|
> | 1 | 2942.5 | 0.218 | 0.0445 | 2991 | 3996 |
> | 2 | 642.5 | 0.253 | 0.0560 | 4129 | 4850 |
> | 3 | 162.5 | 0.268 | 0.0615 | 4129 | 4587 |
>
> $\Delta V_0 = 13{,}433$ m/s and $\lambda_0 = 0.0148$.
>
> A **single stage** with the same $\lambda_0$ and $\delta_0 = 0.06$ reaches only 10,706 m/s. To reach 13,433 m/s it would need $m_0 = 5706$ t, nearly twice the actual 2942.5 t.

## 5. Solid vs liquid (Lecture 30)
- **Solid**: the propellant (fuel + oxidiser) is also the combustion chamber, so there is no feed system. It is simple and storable. But it cannot be controlled or stopped once lit, so the thrust–time profile is designed into the **grain** shape (the burning area). Its $I_{sp}$ is lower. See [[SESA2023 W11 - Solid Propellants and Rocket Nozzle Design]].
- **Liquid**: needs pumps or pressurisation and mixing. It is complex, heavy, costly and harder to store (cryogenics). But it can be **throttled and restarted**, and it has a higher $I_{sp}$. Fuels: LH₂, RP-1/kerosene. Oxidisers: LOX, N₂O₄.

**Engine classes**:

| Class | Thrust | Burn time | Notes |
|---|---|---|---|
| **Boosters** (solid or liquid) | 3000–8000 kN | < 150 s | |
| **Core engines** | 1000–2000 kN | ~600 s | higher $I_{sp}$; also run as boosters at lift-off |
| **Upper stages** | 30–150 kN | 600–1100 s | need **vacuum ignition** |

## 6. Liquid-rocket power cycles
The job of the cycle is to raise the **chamber pressure**.

| Cycle | Turbine drive | Pros | Cons | Examples |
|---|---|---|---|---|
| **Pressure-fed** | none: tanks pressurised (He or self-pressurisation) | simplest, light, cheap, no start-up | tank strength caps $P_c$, so low thrust; upper stages and thrusters | Aestus |
| **Expander** | fuel heated in the nozzle/chamber jacket drives the turbine (closed; a *bleed* variant dumps turbine fuel for a larger turbine pressure ratio) | simple; clean fuel on the turbine means less wear | turbine power is limited by the heat picked up (area ∝ size², volume ∝ size³), so it is size-limited; **not self-starting** | Vinci, RL10 |
| **Gas generator (GG)** | separate small combustor; its exhaust is dumped | high turbine power, high $P_c$; throttleable | complex; GG propellant is wasted (lower $I_{sp}$); hot-gas turbine wear | F-1, Merlin 1D, Vulcain 2 |
| **Staged combustion (SC)** | **all** fuel (or oxidiser) through a pre-burner with a little oxidiser; the rich turbine exhaust goes into the main chamber | highest $P_c$ (SSME > 200 bar); nothing dumped | harshest turbine conditions; most complex | SSME, RD-253 (the Week 10 notes also list Vulcain here, but Vulcain is a gas-generator engine, as the slides say) |
| **Full-flow SC** (legacy exams) | fuel-rich and oxidiser-rich pre-burners drive separate pumps | all propellant through the turbines; cooler turbines; no inter-propellant seal | even more complex | RD-270, Raptor |

## Links
- Parent: [[SESA2023 Propulsion Hub]] · Previous: [[SESA2023 W09 - Turbomachinery Characteristics - Coefficients, Similarity and Maps]] · Next: [[SESA2023 W11 - Solid Propellants and Rocket Nozzle Design]]
- Worked sheet: [[SESA2023 Problem Sheet 10 Rockets Solutions]] (identical to the older Sheet 6)
- Exams: [[SESA2023 Exam 2022-23 Solutions]] Q2, [[SESA2023 Exam 2024-25 Solutions]] Q2, [[SESA2023 Exam 2021-22 Solutions]] Q1 (nozzle as a rocket), plus legacy power-cycle and SSTO essays (2014-15 to 2018-19)

## Sources
- Week 10 notes (Peters, Grenga, Richardson) and Lectures 28–30; Sutton, *Rocket Propulsion Elements*; Hill & Peterson (1992)
