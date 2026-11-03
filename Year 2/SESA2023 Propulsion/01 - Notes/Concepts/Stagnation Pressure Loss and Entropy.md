---
title: "Stagnation Pressure Loss and Entropy"
module: "SESA2023 Propulsion"
type: concept
stream: "Section 1: Introduction and Fundamentals"
aliases: ["total pressure loss", "p0 loss", "Prandtl relation"]
tags: [sesa2023, concept, compressible-flow]
status: complete
parent_lectures: ["[[SESA2023 W03 - Compressible Flow, Normal Shocks and Nozzles]]", "[[SESA2023 W04 - Friction, Heat Addition, Oblique Shocks and Intakes]]", "[[SESA2023 W06 - Jet Engine Cycle Analysis - Brayton, Ramjet, Turbojet and Reheat]]"]
related_concepts: ["[[Stagnation Properties]]", "[[Entropy Change of a Perfect Gas]]", "[[Normal Shock Waves]]", "[[Component Stagnation Pressure Ratios]]", "[[Intake Pressure Recovery]]"]
sources: ["02 - Sources/Lectures/Week 03 - Gas Dynamics I - Compressible Flow, Shocks and Nozzles.pdf", "02 - Sources/Lectures/SESA2023 Lecture 2026-02-10.txt"]
---

# Stagnation Pressure Loss and Entropy

In any adiabatic process of a perfect gas that does no work, $T_0$ is constant, so the entropy change between the two stagnation states reduces to

$$
s_2-s_1 = -R\ln\frac{p_{02}}{p_{01}}\qquad\Longleftrightarrow\qquad \frac{p_{02}}{p_{01}} = e^{-\Delta s/R} .
$$

The entropy generated is the stagnation pressure lost.

The result comes from applying $s_2-s_1 = c_p\ln(T_{02}/T_{01})-R\ln(p_{02}/p_{01})$ to the imaginary stagnation states, which have the same entropies as the real ones; with $T_{02} = T_{01}$ the first term vanishes. It holds across a normal or oblique shock, through a duct with friction only, and in an adiabatic intake ($\Gamma_d$) or nozzle ($\Gamma_n$). It doesn't hold where heat is added, as in a combustor, where $T_0$ changes, or where work is done, in a compressor or turbine. Every component loss in the W06 cycle analysis can therefore be read as an entropy rise, and the second law forbids $p_{02}>p_{01}$ in these processes.

A normal shock at $M_1 = 2$ has $\Delta s/R = 0.327$, so $p_{02}/p_{01} = e^{-0.327} = 0.721$. At $M_1 = 3$ a normal shock retains only 0.328, whereas an oblique shock at $\sigma = 50^\circ$ in the same flow retains 0.584 ([[SESA2023 W04 - Friction, Heat Addition, Oblique Shocks and Intakes|W04]]). After a shock in a nozzle the flow behaves as if it came from a bigger throat, $A_2^* = A_t\,p_{01}/p_{02}$. Across a normal shock the Prandtl relation $U_1U_2 = a^{*2}$, with $a^*$ the critical sound speed of the common $T_0$, follows from mass, momentum and energy and gives $\rho_2/\rho_1 = M_1^{*2}$ directly ([[SESA2023 W03 - Compressible Flow, Normal Shocks and Nozzles#From the jump conditions to the Mach-number relations (the lecture skips this)|W03 derivation]]).

## Related

- [[Stagnation Properties]] · [[Entropy Change of a Perfect Gas]] · [[Normal Shock Waves]] · [[Component Stagnation Pressure Ratios]] · [[Intake Pressure Recovery]]
