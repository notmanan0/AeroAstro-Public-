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

## Definition

> [!note] Definition
>
> $$T\,ds = du+p\,dv = dh-v\,dp\;\Rightarrow\; s_2-s_1 = c_p\ln\frac{T_2}{T_1}-R\ln\frac{p_2}{p_1} = c_v\ln\frac{T_2}{T_1}+R\ln\frac{v_2}{v_1} = c_v\ln\frac{p_2}{p_1}+c_p\ln\frac{v_2}{v_1}$$

## Explanation
- Entropy is a **state property**. Evaluate $\Delta s$ along any convenient reversible path between the same end states.
- The **isentropic relations** follow from $\Delta s = 0$: $T/p^{(\gamma-1)/\gamma}$ = const, $pv^\gamma$ = const, $Tv^{\gamma-1}$ = const.
- **Stagnation form**: $s_2-s_1 = c_p\ln(T_{02}/T_{01})-R\ln(p_{02}/p_{01})$. For adiabatic flow ($T_0$ constant), $\Delta s = -R\ln(p_{02}/p_{01})$. **Stagnation-pressure loss is entropy generation.**
- **$T$–$s$ geometry**: isobars have slope $dT/ds = T/c_p$, so they **diverge** at high $T$. Expanding hot gas over a pressure ratio gives a bigger $\Delta T$ than compressing cold gas over the same ratio. That surplus is the net work of a gas turbine.
- **Second-Law uses**:
  - it rules out expansion shocks ($\Delta s<0$ for $M_1<1$);
  - it gives the "inaccessible" branches of Fanno and Rayleigh flow;
  - it explains why real compressor and turbine exits are hotter than isentropic.

## Examples
- Isothermal heat rejection of 100 kJ/kg at 300 K: $\Delta s = -0.333$ kJ kg⁻¹ K⁻¹, so $p_2 = p_1e^{0.333/0.287} = 3.19$ bar ([[SESA2023 Problem Sheet 2 Solutions]] Q2.1).
- Normal shock at $M_1 = 2$: $\Delta s/R = 0.327$, so $p_{02}/p_{01} = e^{-0.327} = 0.721$.

## Related
- [[Isentropic Efficiency]] · [[Normal Shock Waves]] · [[Two-Property Rule and Perfect Gas Model]]

## Sources
- Week 2 notes §2.5; Data Book p. 7
