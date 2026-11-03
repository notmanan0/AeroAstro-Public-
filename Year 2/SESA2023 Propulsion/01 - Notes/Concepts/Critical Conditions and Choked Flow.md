---
title: "Critical Conditions and Choked Flow"
module: "SESA2023 Propulsion"
type: concept
stream: "Section 1: Introduction and Fundamentals"
aliases: ["choked flow", "sonic conditions", "critical pressure ratio", "mass flow parameter", "p*"]
tags: [sesa2023, concept, compressible-flow, nozzles]
status: complete
parent_lectures: ["[[SESA2023 W03 - Compressible Flow, Normal Shocks and Nozzles]]", "[[SESA2023 W10 - Rocket Performance, Staging and Power Cycles]]"]
related_concepts: ["[[Isentropic Nozzle Flow]]", "[[Converging-Diverging Nozzle Operating Regimes]]", "[[Rocket Performance Parameters]]"]
sources: ["02 - Sources/Lectures/Week 03 - Gas Dynamics I - Compressible Flow, Shocks and Nozzles.pdf", "02 - Sources/Lectures/Week 10 - Rockets.pdf"]
---

# Critical Conditions and Choked Flow

Critical, or starred, conditions are the flow conditions at $M = 1$:

$$
\frac{T^*}{T_0} = \frac{2}{\gamma+1},\qquad\frac{p^*}{p_0} = \left(\frac{2}{\gamma+1}\right)^{\frac{\gamma}{\gamma-1}},\qquad\frac{\rho^*}{\rho_0} = \left(\frac{2}{\gamma+1}\right)^{\frac{1}{\gamma-1}} .
$$

A nozzle is **choked** when its throat reaches $M = 1$, and its mass flow is then the largest possible,

$$
\dot m_{max} = \frac{A_tp_0}{\sqrt{T_0}}\sqrt{\frac{\gamma}{R}}\left(\frac{2}{\gamma+1}\right)^{\frac{\gamma+1}{2(\gamma-1)}} .
$$

| $\gamma$ | $T^*/T_0$ | $p^*/p_0$ | Note |
|---|---|---|---|
| 1.4 | 0.833 | 0.528 | $\dot m = 0.0404\,A_tp_0/\sqrt{T_0}$ |
| 1.33 | 0.858 | 0.540 | |
| 1.22 | 0.901 | 0.561 | |

A converging duct can only accelerate subsonic flow up to $M = 1$ at its exit. Once $p_b\le p^*$, pressure signals can't travel upstream through the sonic throat, so the upstream flow no longer responds to $p_b$, and the mass flow and the upstream $T$, $p$, $\rho$ and $U$ are all fixed. Several results follow. For fixed $(p_0,T_0)$ only the throat area changes $\dot m$. A rocket nozzle that runs supersonic has a mass flow independent of altitude, a point asked in 2022-23 Q2(i) and 2024-25 Q2(iv). At fixed $T_0$, $\dot m\propto p_0$, which is why throttling a choked steam turbine (PS9 Q9.5) gives $\dot m$ proportional to the downstream pressure with a constant volume flow. And an afterburner, which raises $T_{06}$, needs a choked nozzle to open its throat, $A_8\propto\dot m\sqrt{T_{06}}/p_{06}$.

The general isentropic mass flow at a local pressure $p$ (lecture eq. 3.79) is

$$
\frac{\dot m}{\rho_0\sqrt{2c_pT_0}} = A\left(\frac{p}{p_0}\right)^{1/\gamma}\left[1-\left(\frac{p}{p_0}\right)^{\frac{\gamma-1}{\gamma}}\right]^{1/2},
$$

and setting $p = p^*$ recovers the choked form.

Worked values: a reservoir at 10 bar and 400 K with $A_t = 0.1$ m² passes 202 kg/s; a rocket at 60 bar and 2800 K ($\gamma = 1.22$, $R = 397$) passing 50 kg/s needs $A_t = 0.0135$ m² ([[SESA2023 Problem Sheet 10 Rockets Solutions]]); a CO₂/N₂ mixture at 10 bar and 1000 K through 0.002 m² gives $p^* = 5.33$ bar, $T^* = 843$ K and $\dot m = 2.62$ kg/s ([[SESA2023 Exam 2021-22 Solutions]] Q1).

## Related

- [[Isentropic Nozzle Flow]] · [[Converging-Diverging Nozzle Operating Regimes]] · [[Rocket Performance Parameters]]
