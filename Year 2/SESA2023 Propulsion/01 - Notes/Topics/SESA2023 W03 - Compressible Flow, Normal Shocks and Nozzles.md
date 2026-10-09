---
title: "SESA2023 W03 - Compressible Flow, Normal Shocks and Nozzles"
module: "SESA2023 Propulsion"
type: topic
stream: "Section 1: Introduction and Fundamentals"
order: 3
tags:
  - sesa2023
  - compressible-flow
  - normal-shock
  - nozzles
  - choked-flow
aliases: ["Gas dynamics I", "Nozzle flow"]
date: 2026-09-24
status: complete
parent: ["[[SESA2023 Propulsion Hub]]"]
prerequisites: ["[[SESA2023 W02 - Thermodynamics, Mixtures, SFEE and Isentropic Efficiency]]"]
next_topics: ["[[SESA2023 W04 - Friction, Heat Addition, Oblique Shocks and Intakes]]"]
key_concepts: ["[[Stagnation Properties]]", "[[Speed of Sound and Mach Number]]", "[[Critical Conditions and Choked Flow]]", "[[Normal Shock Waves]]", "[[Isentropic Nozzle Flow]]", "[[Converging-Diverging Nozzle Operating Regimes]]"]
tutorial_sheets: ["[[SESA2023 Problem Sheet 3 Solutions]]"]
sources: ["02 - Sources/Lectures/Week 03 - Gas Dynamics I - Compressible Flow, Shocks and Nozzles.pdf"]
---

# SESA2023 W03 - Compressible Flow, Normal Shocks and Nozzles

> [!abstract] Summary
> In compressible flow, density is tied to pressure and temperature by $p = \rho RT$, so mass, momentum and energy must be solved together. For steady, 1-D, inviscid, adiabatic flow they reduce to:
> - **stagnation properties** ($T_0$ is conserved without heat or work, $p_0$ is conserved if isentropic);
> - the **speed of sound** $a = \sqrt{\gamma RT}$ and **Mach number**;
> - **critical** (sonic) conditions;
> - **normal shocks**: supersonic → subsonic, $T_0$ conserved, $p_0$ lost;
> - the **area–velocity relation**, which explains why a converging nozzle can only reach $M = 1$ (choking) and why supersonic jets need a **converging–diverging** nozzle.

## Key Concepts
- [[Stagnation Properties]] · [[Speed of Sound and Mach Number]] · [[Critical Conditions and Choked Flow]] · [[Normal Shock Waves]] · [[Isentropic Nozzle Flow]] · [[Converging-Diverging Nozzle Operating Regimes]]

---

## 1. Simplified equations (Lecture 7)
Assume steady, 1-D, inviscid flow with no thermal diffusion and no viscous heating:

$$
\frac{d}{dx}(\rho U) = 0,\qquad U\frac{dU}{dx}+\frac1\rho\frac{dp}{dx} = 0,\qquad \frac{dh}{dx}+U\frac{dU}{dx} = 0,\qquad p = \rho RT
$$

Along a streamline:
- $\rho_1U_1 = \rho_2U_2$;
- $\tfrac12U_2^2+\int_1^2dp/\rho = \tfrac12U_1^2$ (the compressible Bernoulli equation);
- $h_1+\tfrac12U_1^2 = h_2+\tfrac12U_2^2$.

## 2. Stagnation properties

$$
h_0 = h+\tfrac12U^2,\qquad T_0 = T+\frac{U^2}{2c_p},\qquad \frac{T_0}{T} = 1+\frac{\gamma-1}{2}M^2
$$

$$
\frac{p_0}{p} = \left(\frac{T_0}{T}\right)^{\frac{\gamma}{\gamma-1}},\qquad \frac{\rho_0}{\rho} = \left(\frac{T_0}{T}\right)^{\frac{1}{\gamma-1}}
$$

- $T_0$ is constant in **adiabatic** flow with no work, even if the flow is irreversible.
- $p_0$ is constant only if the flow is also **isentropic**.
- "Pressure" with no qualifier means static pressure.
- Static and stagnation values coincide only when the fluid is at rest *in the chosen frame*.

## 3. Speed of sound and Mach number
A control volume on a weak wave gives $a^2 = \delta p/\delta\rho$. Taking the wave as isentropic, $p/\rho^\gamma$ = const, so

$$
a = \sqrt{\left(\frac{\partial p}{\partial\rho}\right)_s} = \sqrt{\gamma RT},\qquad M = \frac{U}{a}
$$

For an ideal gas, $a$ depends on **temperature only**.

> [!example] Same speed, different Mach number
> M 1.1 at 220 K gives $U = 1.1\sqrt{1.4\cdot287\cdot220} = 327$ m/s. The same speed at 300 K is M 0.94.

## 4. Critical properties (Mach 1)

$$
\frac{T^*}{T_0} = \frac{2}{\gamma+1} = 0.8333,\qquad \frac{p^*}{p_0} = \left(\frac{2}{\gamma+1}\right)^{\frac{\gamma}{\gamma-1}} = 0.5283,\qquad \frac{\rho^*}{\rho_0} = \left(\frac{2}{\gamma+1}\right)^{\frac{1}{\gamma-1}} = 0.6339\quad(\gamma = 1.4)
$$

## 5. Normal shocks (Lecture 8)
A shock is a finite, thin (~μm), **non-isentropic** disturbance. Its jump conditions are:
- mass: $\rho_1U_1 = \rho_2U_2$;
- momentum: $p_1+\rho_1U_1^2 = p_2+\rho_2U_2^2$;
- energy: $h_1+\tfrac12U_1^2 = h_2+\tfrac12U_2^2$;
- plus a perfect gas.

These give the **Rankine–Hugoniot** relations:

$$
M_2^2 = \frac{(\gamma-1)M_1^2+2}{2\gamma M_1^2-(\gamma-1)},\quad \frac{\rho_2}{\rho_1} = \frac{(\gamma+1)M_1^2}{(\gamma-1)M_1^2+2},\quad \frac{p_2}{p_1} = 1+\frac{2\gamma}{\gamma+1}(M_1^2-1)
$$

$$
\frac{T_2}{T_1} = 1+\frac{2(\gamma-1)}{(\gamma+1)^2}\frac{\gamma M_1^2+1}{M_1^2}(M_1^2-1),\qquad \frac{\Delta s}{R} = \frac{\gamma}{\gamma-1}\ln\frac{T_2}{T_1}-\ln\frac{p_2}{p_1}
$$

**Properties of a normal shock**:
- $\Delta s<0$ for $M_1<1$, so shocks only go **supersonic → subsonic** (the Second Law).
- $M_2\to0.378$ and $\rho_2/\rho_1\to6$ as $M_1\to\infty$.
- $T_0$ is **unchanged** (adiabatic, no work). $p_0$ **falls**.

![[prop_normal_shock.png|760]]

> [!example] Shock at $U_1 = 634$ m/s, $T_1 = 250$ K, $p_1 = 0.5$ bar
> $M_1 = 2.0$.
> - Before the shock: $T_{01} = 450$ K, $p_{01} = 3.91$ bar.
> - After the shock: $M_2 = 0.577$, $T_2 = 422$ K, $p_2 = 2.25$ bar, $U_2 = 238$ m/s, $T_{02} = 450$ K, $p_{02} = 2.82$ bar ($p_{02}/p_{01} = 0.721$).

## 6. Duct flow and nozzles (Lecture 9)
Assume a quasi-1D, steady, frictionless, adiabatic, isentropic duct (except across shocks). Combining continuity with momentum and $dp = a^2d\rho$ gives

$$
\boxed{\frac{1}{A}\frac{dA}{dx} = \frac1U\frac{dU}{dx}\left(M^2-1\right)}
$$

- **Subsonic** flow accelerates in a converging duct. **Supersonic** flow accelerates in a *diverging* duct.
- $M = 1$ can only occur at a **throat**.

**Converging nozzle**:
- If $p_b\ge p^*$, then $p_e = p_b$.
- If $p_b<p^*$, then $p_e = p^*$, $M_e = 1$, and the flow is **choked**. The mass flow and everything upstream no longer depend on $p_b$.

**Converging–diverging (de Laval) nozzle**: eight regimes as $p_b$ falls. See [[Converging-Diverging Nozzle Operating Regimes]].

![[prop_cd_nozzle_regimes.png|680]]

### Mass flow

$$
\frac{\dot m}{\rho_0(2c_pT_0)^{1/2}} = A\left(\frac{p}{p_0}\right)^{1/\gamma}\left[1-\left(\frac{p}{p_0}\right)^{\frac{\gamma-1}{\gamma}}\right]^{1/2}
$$

At a **choked** throat ($p = p^*$):

$$
\frac{\dot m}{\rho_0(2c_pT_0)^{1/2}} = A_t\left(\frac{2}{\gamma+1}\right)^{\frac{1}{\gamma-1}}\left(\frac{\gamma-1}{\gamma+1}\right)^{1/2}\quad\Leftrightarrow\quad \dot m = \frac{A_tp_0}{\sqrt{T_0}}\sqrt{\frac\gamma R}\left(\frac{2}{\gamma+1}\right)^{\frac{\gamma+1}{2(\gamma-1)}}
$$

For air this is $\dot m = 0.0404\,A_tp_0/\sqrt{T_0}$. With the reservoir fixed, **only the throat area** changes a choked mass flow.

> [!example] Isentropic nozzle: $p_0 = 10$ bar, $T_0 = 400$ K, $M_e = 2$, $A_t = 0.1$ m²
> - Exit state: $T_e = 400/1.8 = 222$ K and $p_e = 10/7.824 = 1.28$ bar.
> - $U_e = 2\sqrt{\gamma R\cdot222} = 598$ m/s.
> - $\rho_0 = 8.71$ kg/m³ and $\dot m = 202$ kg/s.
> - Thrust: $F = \dot mU_e = 121$ kN.

![[prop_area_mach.png|620]]

## Links
- Parent: [[SESA2023 Propulsion Hub]] · Previous: [[SESA2023 W02 - Thermodynamics, Mixtures, SFEE and Isentropic Efficiency]] · Next: [[SESA2023 W04 - Friction, Heat Addition, Oblique Shocks and Intakes]]
- Shared with SESA2022 legacy content: [[Normal Shock Waves]] · [[Isentropic Nozzle Flow]]
- Worked sheet: [[SESA2023 Problem Sheet 3 Solutions]] · Exams: [[SESA2023 Exam 2020-21 Solutions]] Q1, [[SESA2023 Exam 2021-22 Solutions]] Q1, [[SESA2023 Exam 2022-23 Solutions]] Q1, [[SESA2023 Exam 2024-25 Solutions]] Q1(iii–iv)
- Used for rockets: [[SESA2023 W10 - Rocket Performance, Staging and Power Cycles]]

## Sources
- Week 3 notes and Lectures 7–9; Data Book pp. 11–12 and gas flow Tables 19–22
