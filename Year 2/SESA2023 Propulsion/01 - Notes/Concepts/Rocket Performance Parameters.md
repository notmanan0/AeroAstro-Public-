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

Rocket performance is described by four linked parameters, the specific impulse, the effective exhaust velocity, the characteristic velocity and the thrust coefficient:

$$
I_{sp} = \frac{I_T}{g_0m_p} = \frac{F}{g_0\dot m},\quad c_e = \frac{F}{\dot m} = g_0I_{sp},\quad C^* = \frac{P_cA_t}{\dot m},\quad C_F = \frac{F}{P_cA_t},\quad c_e = C^*C_F .
$$

$I_{sp}$, in seconds, is the impulse per unit weight of propellant, which makes it the same number in SI and imperial units. $c_e$ is the equivalent uniform exhaust velocity including the pressure thrust, $c_e = V_j+A_e(P_e-P_A)/\dot m$. $C^*$ is a figure of merit for the combustion chamber and propellants, set at the choked throat and independent of the diverging section; ideally

$$
C^* = \frac{\sqrt{\gamma RT_c}}{\gamma}\Big(\frac{\gamma+1}{2}\Big)^{\frac{\gamma+1}{2(\gamma-1)}},
$$

which is high for a hot chamber and a light exhaust. $C_F$ is a figure of merit for the nozzle expansion, typically 1.3–1.9; ideally

$$
C_F = \sqrt{\frac{2\gamma^2}{\gamma-1}\Big(\frac{2}{\gamma+1}\Big)^{\frac{\gamma+1}{\gamma-1}}\Big[1-\Big(\frac{P_e}{P_c}\Big)^{\frac{\gamma-1}{\gamma}}\Big]}+\frac{P_e-P_A}{P_c}\frac{A_e}{A_t} .
$$

The derivation of $I_{sp}$ (2013-14 and 2014-15 Q4(ii)) assumes steady flow, an adiabatic isentropic nozzle, full expansion and a uniform exit. The steady-flow energy equation then gives $V_j = \sqrt{2c_pT_{02}[1-(p_e/p_{02})^{(\gamma-1)/\gamma}]}$, so

$$
I_{sp} = \frac{1}{g_0}\sqrt{2c_pT_{02}\left[1-\left(\frac{p_e}{p_{02}}\right)^{\frac{\gamma-1}{\gamma}}\right]},
$$

and a high specific impulse needs a hot chamber, a large expansion ratio $P_c/P_e$ and a light exhaust, with a large $c_p = \frac{\gamma}{\gamma-1}\frac{\bar R}{M}$. With altitude, $\dot m$ stays fixed by the choked throat, while $F$, $c_e$, $I_{sp}$ and $C_F$ all rise as $P_A$ falls.

| Propellant | $I_{sp}$ (s) |
|---|---|
| Double-base solid | ≈ 220 (sea level) |
| Composite solid | ≈ 250–270 |
| LOX/RP-1 | ≈ 300–350 |
| LOX/LH₂ | ≈ 450 (vacuum) |
| Ion (legacy) | thousands |

Worked values: PS10 Q10.3 (60 bar, 2800 K, $\gamma = 1.22$, 50 kg/s) gives $A_t = 0.0135$ m², $C^* = 1616$ m/s, $c_e = 2537$ m/s, $C_F = 1.57$, $I_{sp} = 258.6$ s and $F = 126.9$ kN. 2022-23 Q2 (50 bar, 5000 K, cold air, $A_t = 0.05$ m², $I_{sp} = 306$ s) gives $\dot m = 142.9$ kg/s, $C^* = 1749$ m/s, $C_F = 1.716$ and $F = 0.429$ MN. The F-1 achieved $c_e = 2992$ m/s against 3213 m/s in theory.

## Related

- [[Tsiolkovsky Rocket Equation]] · [[Critical Conditions and Choked Flow]] · [[Thrust Equation]] · [[Rocket Nozzle Geometry]]
