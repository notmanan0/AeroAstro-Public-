---
title: "Entropy Change of a Perfect Gas"
module: "SESA2023 Propulsion"
type: concept
stream: "Section 1: Introduction and Fundamentals"
aliases: ["TdS equations", "entropy", "second law"]
tags: [sesa2023, concept, thermodynamics, entropy]
status: complete
parent_lectures: ["[[SESA2023 W02 - Thermodynamics, Mixtures, SFEE and Isentropic Efficiency]]", "[[SESA2023 W03 - Compressible Flow, Normal Shocks and Nozzles]]"]
related_concepts: ["[[Isentropic Efficiency]]", "[[Normal Shock Waves]]", "[[Two-Property Rule and Perfect Gas Model]]"]
sources: ["02 - Sources/Lectures/Week 02 - Thermodynamics.pdf", "02 - Sources/Lectures/Week 03 - Gas Dynamics I - Compressible Flow, Shocks and Nozzles.pdf"]
---

# Entropy Change of a Perfect Gas

For a perfect gas the Gibbs equations $T\,ds = du+p\,dv = dh-v\,dp$ integrate to

$$
s_2-s_1 = c_p\ln\frac{T_2}{T_1}-R\ln\frac{p_2}{p_1} = c_v\ln\frac{T_2}{T_1}+R\ln\frac{v_2}{v_1} = c_v\ln\frac{p_2}{p_1}+c_p\ln\frac{v_2}{v_1} .
$$

Entropy is a state property, so $\Delta s$ can be evaluated along any convenient reversible path between the same end states. Setting $\Delta s = 0$ gives the isentropic relations, $T/p^{(\gamma-1)/\gamma}$, $pv^\gamma$ and $Tv^{\gamma-1}$ constant. In stagnation form, $s_2-s_1 = c_p\ln(T_{02}/T_{01})-R\ln(p_{02}/p_{01})$, and in adiabatic flow, where $T_0$ is constant, $\Delta s = -R\ln(p_{02}/p_{01})$: a loss of stagnation pressure is entropy generation. For a normal shock at $M_1 = 2$, $\Delta s/R = 0.327$, so $p_{02}/p_{01} = e^{-0.327} = 0.721$.

On a $T$–$s$ diagram isobars have slope $dT/ds = T/c_p$, so they diverge at high temperature. Expanding hot gas through a pressure ratio therefore gives a bigger $\Delta T$ than compressing cold gas through the same ratio, and that surplus is the net work of a gas turbine. The second law also rules out expansion shocks ($\Delta s<0$ for $M_1<1$), marks the inaccessible branches of Fanno and Rayleigh flow, and explains why real compressor and turbine exits are hotter than isentropic ones.

In [[SESA2023 Problem Sheet 2 Solutions]] Q2.1, rejecting 100 kJ/kg isothermally at 300 K gives $\Delta s = -0.333$ kJ kg⁻¹ K⁻¹, so $p_2 = p_1e^{0.333/0.287} = 3.19$ bar.

## Related

- [[Isentropic Efficiency]] · [[Normal Shock Waves]] · [[Two-Property Rule and Perfect Gas Model]]
