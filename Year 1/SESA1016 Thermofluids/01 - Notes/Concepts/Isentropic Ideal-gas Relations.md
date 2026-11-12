---
title: "Isentropic Ideal-gas Relations"
module: "SESA1016 Thermofluids"
type: concept
stream: "Thermodynamics"
aliases: ["isentropic relations", "Poisson relations"]
tags: [sesa1016, concept, isentropic]
status: complete
parent_lectures: ["[[SESA1016 T4 - Entropy and Isentropic Relations]]", "[[SESA1016 T5 - Ideal Heat Engine Models]]"]
related_concepts: ["[[Entropy Generation]]", "[[Ideal-gas Law]]", "[[Thermal Efficiency and COP]]"]
sources: ["02 - Sources/Lectures/Chapter 4.pdf"]
---

# Isentropic Ideal-gas Relations

The isentropic relations link $p$, $v$ and $T$ for an ideal gas with constant specific heats in a process at constant entropy, that is, a reversible adiabatic process.

They come from setting $ds=0$ in the entropy change of an ideal gas. With $s_2-s_1=c_v\ln(T_2/T_1)+R\ln(v_2/v_1)=0$ and $R/c_v=\gamma-1$, temperature and volume are linked; using the $c_p$ form, temperature and pressure; eliminating $T$ between them gives the pressure–volume form:

$$
\frac{T_2}{T_1}=\left(\frac{v_1}{v_2}\right)^{\gamma-1},\qquad
\frac{T_2}{T_1}=\left(\frac{p_2}{p_1}\right)^{(\gamma-1)/\gamma},\qquad
\frac{p_2}{p_1}=\left(\frac{v_1}{v_2}\right)^{\gamma}
$$

They model the compression and expansion strokes of the ideal Otto, Diesel and Brayton cycles, and give the efficiencies $1-r^{1-\gamma}$ (Otto) and $1-r_p^{(1-\gamma)/\gamma}$ (Brayton) directly.

Their limits are the assumptions behind them. A real adiabatic compressor has friction, generates entropy and ends hotter than the isentropic value for the same pressure ratio. A process with heat transfer is not isentropic even if it happens to follow $pv^n=\text{const}$. And $\gamma$ must be the value for the gas and temperature range in question; 1.4 is right for air near room temperature but falls in hot combustion gases.

## Related

- [[SESA1016 T4 - Entropy and Isentropic Relations#5. Isentropic relations|T4 §5]] · [[SESA1016 T2 - Work, Heat and the First Law#Adiabatic processes|adiabatic processes in T2]] · [[SESA1016 T4 - Entropy and Isentropic Relations#Worked example - isentropic compression of air|isentropic compression]] · [[SESA1016 T5 - Ideal Heat Engine Models#Otto efficiency|Otto efficiency]]
- [[Entropy Generation]] · [[Ideal-gas Law]] · [[Thermal Efficiency and COP]]
