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

The **bypass ratio** is the mass flow through the bypass duct divided by the core flow, and the **fan pressure ratio** is the stagnation pressure ratio across the fan in the bypass stream:

$$
BPR = \frac{\dot m_{bypass}}{\dot m_{core}},\qquad fpr = \frac{p_{013}}{p_{02}} .
$$

For a given flight condition the fpr alone fixes the bypass jet velocity, and with a fixed core the LP-spool power balance then fixes the BPR.

The bypass jet follows from the fan's isentropic efficiency and an expansion to ambient,

$$
T_{013} = T_{02}\Big(1+\frac{fpr^{(\gamma-1)/\gamma}-1}{\eta_f}\Big),\qquad V_{jb} = \sqrt{2c_pT_{013}\big[1-(p_a/(fpr\,p_{02}))^{(\gamma-1)/\gamma}\big]},
$$

and the LP spool balances as $(1+f)(h_{045}-h_{05}) = (h_{023}-h_{02})+BPR(h_{013}-h_{02})$. Choosing $V_{jc} = V_{jb}$ maximises $\eta_P$ and minimises noise; in practice you iterate on the LPT pressure ratio and then read off the BPR. Specific thrust, $X = F_N/\dot m_{air} = V_j-V$, describes the engine better than the BPR does.

Lowering the fpr (raising the BPR) raises $\eta_P$ and cuts the bare sfc (going from 1.8 to 1.5 saves 6 %), and it makes far less jet noise: the lectures quote noise $\propto V_j^7$, the handout Lighthill's $V_j^8$ for acoustic power. Against that, specific thrust falls, so 36 % more mass flow is needed, and the bigger fan brings nacelle drag ($F_{eff} = F_{bare}(1-9.25/X)$), weight (roughly $\propto d^{2.4}$), more LPT work (more stages or a gearbox), and ground-clearance and transport limits. The installed optimum is around fpr 1.5, which with an overall pressure ratio of about 45 means a bypass ratio of 10–12 today.

The geared turbofan is a response to the LPT problem. A big fan must turn slowly to keep its tip below about M 1.6, which starves the LPT of blade speed, since $\Delta h_0 = \psi U^2$. A gearbox lets a small, fast LPT drive the fan with far fewer stages, at the cost of the gearbox's mass, heat rejection and reliability; in [[SESA2023 Exam 2020-21 Solutions]] Q4, 23 LPT stages fall to 3.

![[prop_turbofan_fpr.png|700]]

Worked values: in PS8 Q8.3, fpr 1.4, 1.5 and 1.6 give BPR 13.8, 11.2 and 9.4 and $\eta_P$ 0.834, 0.810 and 0.789. In 2021-22 Q3, BPR 10 and fpr 1.5 at M 0.8 give $V_j = 343$ m/s and $\eta_P = 0.816$. In 2013-14 Q3, at M 2 with BPR 0.5, the cold jet is only 649 m/s against a flight speed of 589 m/s, so the bypass stream gives very little thrust at supersonic speed.

## Related

- [[Propulsive Efficiency]] · [[Turbojet]] · [[Thrust Equation]] · [[Flow and Work Coefficients]]
- SESA2028 materials: [[SESA2028 M4 - Polymer Matrix Composites|SESA2028 M4 composites]] (Ti against CFRP fan blades, [[FEEG2005 Exam 2020-21 Solutions|2020-21 MQ1]]) · [[Titanium Alloy Classes]]
