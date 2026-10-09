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

## Definition

> [!note] Definition
> **Critical** (starred) conditions are those at $M = 1$:
>
> $$\frac{T^*}{T_0} = \frac{2}{\gamma+1},\qquad\frac{p^*}{p_0} = \left(\frac{2}{\gamma+1}\right)^{\frac{\gamma}{\gamma-1}},\qquad\frac{\rho^*}{\rho_0} = \left(\frac{2}{\gamma+1}\right)^{\frac{1}{\gamma-1}}$$
>
> A nozzle is **choked** when its throat reaches $M = 1$. Its mass flow is then the maximum possible:
>
> $$\dot m_{max} = \frac{A_tp_0}{\sqrt{T_0}}\sqrt{\frac{\gamma}{R}}\left(\frac{2}{\gamma+1}\right)^{\frac{\gamma+1}{2(\gamma-1)}}$$

## Explanation
- **Critical values**:

  | $\gamma$ | $T^*/T_0$ | $p^*/p_0$ | Note |
  |---|---|---|---|
  | 1.4 | 0.833 | **0.528** | $\dot m = 0.0404\,A_tp_0/\sqrt{T_0}$ |
  | 1.33 | 0.858 | 0.540 | |
  | 1.22 | 0.901 | 0.561 | |

- **Why it chokes**: a converging duct can accelerate subsonic flow only up to $M = 1$ at the exit. Once $p_b\le p^*$, pressure signals can't travel upstream through the sonic throat, so the upstream flow no longer "knows" about $p_b$. $\dot m$, and $T$, $p$, $\rho$ and $U$ upstream, are fixed.
- **Consequences**:
  - For fixed $(p_0,T_0)$, only $A_t$ changes $\dot m$.
  - The mass flow is **independent of altitude** (back pressure) for any rocket nozzle that runs supersonic. This is asked in 2022-23 Q2(i) and 2024-25 Q2(iv).
  - $\dot m\propto p_0$ at fixed $T_0$. This is PS9 Q9.5: throttling a choked steam turbine gives $\dot m\propto$ the downstream pressure, with constant volume flow.
  - An afterburner raises $T_{06}$, so a choked nozzle must open its throat: $A_8\propto\dot m\sqrt{T_{06}}/p_{06}$.
- **General isentropic mass flow** at local pressure $p$ (lecture eq. 3.79):

  $$\frac{\dot m}{\rho_0\sqrt{2c_pT_0}} = A\left(\frac{p}{p_0}\right)^{1/\gamma}\left[1-\left(\frac{p}{p_0}\right)^{\frac{\gamma-1}{\gamma}}\right]^{1/2}$$

  Setting $p = p^*$ gives the choked form.

## Examples
- Reservoir at 10 bar and 400 K, $A_t = 0.1$ m²: **202 kg/s**.
- Rocket at 60 bar and 2800 K ($\gamma = 1.22$, $R = 397$), 50 kg/s: $A_t = 0.0135$ m² ([[SESA2023 Problem Sheet 10 Rockets Solutions]]).
- CO₂/N₂* mixture at 10 bar and 1000 K, $A = 0.002$ m²: $p^* = 5.33$ bar, $T^* = 843$ K, $\dot m = 2.62$ kg/s ([[SESA2023 Exam 2021-22 Solutions]] Q1).

## Related
- [[Isentropic Nozzle Flow]] · [[Converging-Diverging Nozzle Operating Regimes]] · [[Rocket Performance Parameters]]

## Sources
- Week 3 notes §3.3.2, §3.5.3; Lectures 7, 9; Data Book p. 12
