---
title: "Converging-Diverging Nozzle Operating Regimes"
module: "SESA2023 Propulsion"
type: concept
stream: "Section 1: Introduction and Fundamentals"
aliases: ["de Laval nozzle", "over-expanded", "under-expanded", "shock diamonds", "back pressure"]
tags: [sesa2023, concept, compressible-flow, nozzles]
status: complete
parent_lectures: ["[[SESA2023 W03 - Compressible Flow, Normal Shocks and Nozzles]]", "[[SESA2023 W11 - Solid Propellants and Rocket Nozzle Design]]"]
related_concepts: ["[[Isentropic Nozzle Flow]]", "[[Normal Shock Waves]]", "[[Critical Conditions and Choked Flow]]", "[[Rocket Nozzle Geometry]]"]
sources: ["02 - Sources/Lectures/Week 03 - Gas Dynamics I - Compressible Flow, Shocks and Nozzles.pdf", "02 - Sources/Lectures/Week 11 - Rockets.pdf"]
---
# Converging-Diverging Nozzle Operating Regimes

## Definition

> [!note] Definition
> The flow pattern in a C–D nozzle with fixed $p_0$ depends on the back pressure $p_b$. There are eight regimes (1–8), running from no flow, through choked flow with internal shocks, to design and under-expanded operation.

## Explanation
Numbers follow Week 3 notes Fig. 3.9, with $p_b$ decreasing.

| Regime | Condition | Flow |
|---|---|---|
| 1 | $p_b = p_0$ | no flow |
| 2 | $p_b$ below $p_0$ but not low enough to choke | subsonic throughout, with a pressure minimum at the throat (a venturi) |
| 3 | just choked | $M = 1$ at the throat only, subsonic diffusion after it. From here on, $\dot m$ and the converging-section flow are **frozen** |
| 4 | | supersonic after the throat, then a **normal shock inside** the diverging section, then subsonic diffusion to $p_b$. The shock moves downstream as $p_b$ falls |
| 5 | | normal shock **at the exit plane** |
| 6 | $p_e<p_b<p_{e5}$ | **over-expanded**: supersonic exit, oblique shocks outside (shock diamonds) |
| 7 | $p_b = p_e$ | **design**: fully supersonic, shock-free, maximum thrust for this area ratio |
| 8 | $p_b<p_e$ | **under-expanded**: expansion fans outside |

**Locating an internal shock**:
1. The supersonic branch of $A/A^*$ gives $M_1$ at the shock.
2. The shock tables give $M_2$ and $p_{02}/p_{01}$.
3. $\dot m\propto p_0A^*$, so the new $A_2^* = A^*/(p_{02}/p_{01})$.
4. The subsonic branch at $A_e/A_2^*$ gives $M_e$ and $p_e = p_{02}(p/p_0)_{M_e}$.

**Rockets**: a fixed nozzle has one design altitude. It is over-expanded below it and under-expanded above it. Severe over-expansion causes separation, which is unstable and not acceptable. Hence altitude-adaptive designs (aerospike, dual-bell) in W11.

![[prop_cd_nozzle_regimes.png|640]]

## Examples
- Lecture: $A_e = 0.7$, $A_t = 0.2$ m², $p_0 = 400$ kPa, shock at $M_1 = 2.44$ ($A = 0.499$ m²). This gives $M_e = 0.34$ and $p_e = 193$ kPa.
- Descriptive questions: [[SESA2023 Exam 2020-21 Solutions]] Q1(i) (9 marks) and [[SESA2023 Exam 2024-25 Solutions]] Q1(iii).

## Related
- [[Isentropic Nozzle Flow]] · [[Normal Shock Waves]] · [[Critical Conditions and Choked Flow]] · [[Rocket Nozzle Geometry]]

## Sources
- Week 3 notes §3.5.2; Lectures 9–11
