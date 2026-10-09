---
title: "Bypass Ratio and Fan Pressure Ratio"
module: "SESA2023 Propulsion"
type: concept
stream: "Section 3: Ramjets, Gas Turbines, Turbojets and Turbofans"
aliases: ["BPR", "fpr", "turbofan", "high bypass ratio", "specific thrust", "geared turbofan"]
tags: [sesa2023, concept, turbofan]
status: complete
parent_lectures: ["[[SESA2023 W07 - Turbofan Architectures and Fan Pressure Ratio Selection]]"]
related_concepts: ["[[Propulsive Efficiency]]", "[[Turbojet]]", "[[Thrust Equation]]", "[[Flow and Work Coefficients]]"]
sources: ["02 - Sources/Lectures/Week 06-07 - Jet Engines.pdf"]
---
# Bypass Ratio and Fan Pressure Ratio

## Definition

> [!note] Definition
> $$BPR = \frac{\dot m_{bypass}}{\dot m_{core}},\qquad fpr = \frac{p_{013}}{p_{02}}\ \text{(stagnation, bypass stream)}$$
> The fpr alone fixes the bypass jet velocity for a given flight condition. A fixed core then fixes the BPR through the LP-spool power balance.

## Explanation
**Bypass jet**:
$$T_{013} = T_{02}\Big(1+\frac{fpr^{(\gamma-1)/\gamma}-1}{\eta_f}\Big),\quad V_{jb} = \sqrt{2c_pT_{013}\big[1-(p_a/(fpr\,p_{02}))^{(\gamma-1)/\gamma}\big]}$$

**LP spool**: $(1+f)(h_{045}-h_{05}) = (h_{023}-h_{02})+BPR(h_{013}-h_{02})$.

**Choose $V_{jc} = V_{jb}$** to maximise $\eta_P$ and minimise noise. Iterate the LPT pressure ratio, then get the BPR.

**Trade-offs of lowering fpr (raising BPR)**:
- ✔ $\eta_P$ rises and bare sfc falls (1.8 → 1.5 gives −6 %); much less jet noise ($\propto V_j^8$).
- ✘ Specific thrust falls (+36 % $\dot m$ needed); a bigger fan, so **nacelle drag** ($F_{eff} = F_{bare}(1-9.25/X)$) and **weight** ($\propto d^{2.4}$); more LPT work (more stages, or a gearbox); ground clearance and transport limits.
- The installed optimum is **fpr ≈ 1.5**, which with OPR ≈ 45 means bpr ≈ 10–12 today.

**Geared turbofan**: a big fan must turn slowly to keep its tip below about M 1.6, which starves the LPT of blade speed ($\Delta h_0 = \psi U^2$). A gearbox lets a small, fast LPT drive the fan: far fewer LPT stages, lighter and shorter. The cost is the gearbox mass, heat rejection and reliability. See [[SESA2023 Exam 2020-21 Solutions]] Q4, where 23 LPT stages fall to 3.

**Specific thrust** $X = F_N/\dot m_{air} = V_j-V$ is a better descriptor than BPR.

![[prop_turbofan_fpr.png|700]]

## Examples
- PS8 Q8.3: fpr 1.4, 1.5, 1.6 give BPR 13.8, 11.2, 9.4 and $\eta_P$ 0.834, 0.810, 0.789.
- 2021-22 Q3: bpr 10, fpr 1.5 at M 0.8 gives $V_j = 343$ m/s and $\eta_P = 0.816$.
- 2013-14 Q3 (M 2, bpr 0.5): the cold jet is only 649 m/s against the 589 m/s flight speed, so the bypass stream gives very little thrust at supersonic speed.

## Related
- [[Propulsive Efficiency]] · [[Turbojet]] · [[Thrust Equation]] · [[Flow and Work Coefficients]]

**Related (SESA2028 materials):** [[SESA2028 M4 - Polymer Matrix Composites|SESA2028 M4 composites]] (Ti vs CFRP fan blades, [[FEEG2005 Exam 2020-21 Solutions|2020-21 MQ1]]) · [[Titanium Alloy Classes]]

## Sources
- Weeks 6–7 handout §7; Lectures 20–21
