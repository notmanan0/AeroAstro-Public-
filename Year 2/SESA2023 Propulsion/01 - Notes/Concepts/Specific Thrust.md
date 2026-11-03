---
title: "Specific Thrust"
module: "SESA2023 Propulsion"
type: concept
stream: "Section 3: Ramjets, Gas Turbines, Turbojets and Turbofans"
aliases: ["X", "net thrust per unit air flow", "specific net thrust"]
tags: [sesa2023, concept, performance]
status: complete
parent_lectures: ["[[SESA2023 W06 - Jet Engine Cycle Analysis - Brayton, Ramjet, Turbojet and Reheat]]", "[[SESA2023 W07 - Turbofan Architectures and Fan Pressure Ratio Selection]]"]
related_concepts: ["[[Thrust Equation]]", "[[Propulsive Efficiency]]", "[[Thrust Specific Fuel Consumption]]", "[[Bypass Ratio and Fan Pressure Ratio]]"]
sources: ["02 - Sources/Lectures/Week 06-07 - Jet Engines.pdf", "02 - Sources/Lectures/SESA2023 Lecture 18.txt", "02 - Sources/Lectures/SESA2023 Lecture 21.txt"]
---

# Specific Thrust

**Specific thrust** is the net thrust per unit mass flow of air entering the engine, written $X$ in the course (L19, l. 297):

$$
X = \frac{F_N}{\dot m_a} = (1+f)V_j-V\quad(\text{fully expanded}).
$$

Its units are N s kg⁻¹, which is m/s, not N (L18, l. 299 corrects the slide). For a turbofan with matched jets and $f\ll1$, per kilogram of total air, $X\approx V_j-V$, which is why the lecture describes it as the effective velocity increase through the engine (L18, ll. 299–302).

A high $X$ means a compact engine for its thrust but a low propulsive efficiency; a low $X$ means a high $\eta_P$ but a large air flow for the same thrust, $\dot m_a = F_N/X$. Fuel consumption ties to it directly, $\mathrm{sfc} = f/X$. The lecture argues it describes an engine better than the bypass ratio does: the RB211 kept its bypass ratio while its fan pressure ratio, thrust and $X$ all rose (L21, ll. 152–174). Low-$X$ engines also pay the biggest installation penalty, because nacelle drag scales as $kV\,F_N/X$, giving $F_{N,eff} = F_N(1-kV/X)$.

| Engine (course example) | $X$ (m/s) |
|---|---|
| Ideal ramjet, M 3, 51,000 ft, $T_{03}=1800$ K | 686 |
| Turbojet, M 2, 31,000 ft (L19) | 341 |
| PS8 turbofan, fpr 1.5, M 0.78 | 109 |
| RB211 at cruise (L21, ll. 269–270) | about 100 |
| Modern turbofan (L18, ll. 303–306) | below 100 (about 80) |

## Related

- [[Thrust Equation]] · [[Propulsive Efficiency]] · [[Thrust Specific Fuel Consumption]] · [[Bypass Ratio and Fan Pressure Ratio]]
- [[SESA2023 W06 - Jet Engine Cycle Analysis - Brayton, Ramjet, Turbojet and Reheat]] · [[SESA2023 W07 - Turbofan Architectures and Fan Pressure Ratio Selection]]
