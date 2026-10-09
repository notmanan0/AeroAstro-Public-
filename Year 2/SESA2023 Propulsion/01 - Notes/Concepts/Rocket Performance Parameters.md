---
title: "Rocket Performance Parameters"
module: "SESA2023 Propulsion"
type: concept
stream: "Section 5: Rockets"
aliases: ["specific impulse", "Isp", "effective exhaust velocity", "characteristic velocity", "C*", "thrust coefficient", "CF"]
tags: [sesa2023, concept, rockets]
status: complete
parent_lectures: ["[[SESA2023 W10 - Rocket Performance, Staging and Power Cycles]]", "[[SESA2023 W11 - Solid Propellants and Rocket Nozzle Design]]"]
related_concepts: ["[[Tsiolkovsky Rocket Equation]]", "[[Critical Conditions and Choked Flow]]", "[[Thrust Equation]]", "[[Rocket Nozzle Geometry]]"]
sources: ["02 - Sources/Lectures/Week 10 - Rockets.pdf", "02 - Sources/Lectures/Week 11 - Rockets.pdf"]
---
# Rocket Performance Parameters

## Definition

> [!note] Definition
>
> $$I_{sp} = \frac{I_T}{g_0m_p} = \frac{F}{g_0\dot m},\quad c_e = \frac{F}{\dot m} = g_0I_{sp},\quad C^* = \frac{P_cA_t}{\dot m},\quad C_F = \frac{F}{P_cA_t},\quad c_e = C^*C_F$$

## Explanation
- **$I_{sp}$** (s): impulse per unit *weight* of propellant, so it is the same number in SI and imperial units.
- **$c_e$**: the equivalent uniform exhaust velocity, including pressure thrust: $c_e = V_j+A_e(P_e-P_A)/\dot m$.
- **$C^*$**: a figure of merit for the **combustion chamber and propellants**. It is set at the choked throat, independent of the diverging section. Ideally

  $$C^* = \frac{\sqrt{\gamma RT_c}}{\gamma}\Big(\frac{\gamma+1}{2}\Big)^{\frac{\gamma+1}{2(\gamma-1)}},$$

  which is high for high $T_c$ and low molar mass.
- **$C_F$**: a figure of merit for the **nozzle expansion**, typically 1.3–1.9. Ideally

  $$C_F = \sqrt{\frac{2\gamma^2}{\gamma-1}\Big(\frac{2}{\gamma+1}\Big)^{\frac{\gamma+1}{\gamma-1}}\Big[1-\Big(\frac{P_e}{P_c}\Big)^{\frac{\gamma-1}{\gamma}}\Big]}+\frac{P_e-P_A}{P_c}\frac{A_e}{A_t}$$

- **Isp derivation** (2013-14 and 2014-15 Q4(ii)):
  - Assume steady flow, an adiabatic isentropic nozzle, full expansion and a uniform exit.
  - The SFEE gives $V_j = \sqrt{2c_pT_{02}[1-(p_e/p_{02})^{(\gamma-1)/\gamma}]}$, so

  $$I_{sp} = \frac{1}{g_0}\sqrt{2c_pT_{02}\left[1-\left(\frac{p_e}{p_{02}}\right)^{\frac{\gamma-1}{\gamma}}\right]}$$

  - Hence high $T_c$, a high $P_c/P_e$ (large expansion ratio) and a light exhaust (large $c_p = \frac{\gamma}{\gamma-1}\frac{\bar R}{M}$).
- **Altitude**: $\dot m$ is fixed by the choked throat and is independent of altitude. $F$, $c_e$, $I_{sp}$ and $C_F$ all rise as $P_A$ falls.
- **Typical $I_{sp}$**:

  | Propellant | $I_{sp}$ (s) |
  |---|---|
  | Double-base solid | ≈ 220 (sea level) |
  | Composite solid | ≈ 250–270 |
  | LOX/RP-1 | ≈ 300–350 |
  | LOX/LH₂ | ≈ 450 (vacuum) |
  | Ion (legacy) | thousands |

## Examples
- PS10 Q10.3 (60 bar, 2800 K, $\gamma = 1.22$, 50 kg/s): $A_t = 0.0135$ m², $C^* = 1616$, $c_e = 2537$ m/s, $C_F = 1.57$, $I_{sp} = 258.6$ s, $F = 126.9$ kN.
- 2022-23 Q2 (50 bar, 5000 K, cold air, $A_t = 0.05$, $I_{sp} = 306$ s): $\dot m = 142.9$ kg/s, $C^* = 1749$ m/s, $C_F = 1.716$, $F = 0.429$ MN.
- F-1: $c_e = 2992$ m/s against 3213 m/s theoretical.

## Related
- [[Tsiolkovsky Rocket Equation]] · [[Critical Conditions and Choked Flow]] · [[Thrust Equation]] · [[Rocket Nozzle Geometry]]

## Sources
- Week 10 notes §10.2; Lecture 28; Data Book p. 17
