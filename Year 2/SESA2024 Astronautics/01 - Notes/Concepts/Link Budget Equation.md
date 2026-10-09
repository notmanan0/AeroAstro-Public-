---
title: "Link Budget Equation"
module: "SESA2024 Astronautics"
type: concept
stream: "Spacecraft Subsystems"
aliases: ["link budget", "C/N0", "free-space loss", "carrier to noise density", "noise temperature"]
tags: [sesa2024, concept, communications]
status: complete
parent_lectures: ["[[SESA2024 09 - Communications]]"]
related_concepts: ["[[EIRP and G-T]]", "[[Bit Error Rate and Eb-N0]]", "[[Antenna Gain and Beamwidth]]", "[[Decibels]]"]
sources: ["02 - Sources/Lectures/Chapter 9/2025 Chapter 9 - Communications - Lecture slides.pdf"]
---

# Link Budget Equation

## Definition

> [!note] Definition
> $$10\log\frac{C}{N_0} = 10\log(P_TG_T)+10\log\frac{G_R}{T_R}-20\log\frac{4\pi\rho}{\lambda}-10\log L_A-10\log k$$
> In words, $C/N_0$ = EIRP + $G/T$ − free-space loss − other losses + 228.6 dB.

## Explanation
**Derivation**:
1. The flux from an isotropic source at range $\rho$ is $P_T/4\pi\rho^2$. With gain $G_T$ it becomes $P_TG_T/4\pi\rho^2$.
2. The received power is flux × $A_{eff,R}$, with $A_{eff,R} = G_R\lambda^2/4\pi$:
$$P_R = \frac{P_TG_TG_R}{(4\pi\rho/\lambda)^2} = \frac{P_TG_TG_R}{L_{FS}}$$
3. Add other losses $L_A$: atmosphere, rain, depointing, circuits.
4. Set $C = P_R$ and $N_0 = kT_R$ (noise, with $N = kTB$ over bandwidth $B$).
5. Take $10\log$.

**Using it**: $C/N_0 = (E_b/N_0)+10\log R_b$. The standard unknowns are EIRP, $R_b$, $G_R$ or $\rho$.

**Deep space**: $L_{FS}\propto\rho^2$ is enormous (about 300 dB at 40 AU). Compensate with a huge $G_R$ (70 m DSN), a low $T_R$ (cryogenic receivers at 4–28 K), a high EIRP and a low $R_b$.

## Examples
| Case | Key numbers | Result |
|---|---|---|
| Pluto (workbook) | EIRP 65, $G/T$ 58.35, $L_{FS}$ 306.53 | $R_b$ = 3483 bps; 2 Gbit in 6.6 days |
| Voyager at Saturn (2017/18) | EIRP 61.2, 70 m at 25 K, $L_A$ 3 dB, 9.5 AU, 8.5 GHz | $C/N_0$ = 51.6 dB-Hz, $R_b$ = 14.4 kbps, 0.5 Gbit in 9.6 h |
| Phobos (2015/16) | 140 kbps, 7.5 GHz, 4 × 10⁸ km, 70 m at 4 K, $L_A$ 5 dB | **EIRP = 54.1 dBW**; $P_TD^2\approx83$ W m² (the paper quotes 81) |
| GEO TV (lecture) | 92 Mbps, 0.4 m dish, 150 K, 5 dB | EIRP ≈ 62 dBW |
| GPS 12 h (2024/25) | 180 kbps, $G/T$ −21.7, 1.575 GHz | EIRP = 38.2 dBW; $P_T$ ≈ 151 W, so **≈ 303 W** electrical |
| C-band (2023/24) | 150 Mbps, $E_b/N_0$ 9, $G/T$ −16, 36 800 km, 6 dB | EIRP = 80.2 dBW |

![[ast_link_budget_pluto.png|560]]

## Related
- [[EIRP and G-T]] · [[Bit Error Rate and Eb-N0]] · [[Antenna Gain and Beamwidth]] · [[Decibels]]

## Sources
- Chapter 9 slides 22–27 (equation 9.6); workbook Ch9 Q5, Q9
