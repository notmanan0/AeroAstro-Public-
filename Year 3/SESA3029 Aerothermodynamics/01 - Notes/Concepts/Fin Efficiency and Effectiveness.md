---
title: "Fin Efficiency and Effectiveness"
module: "SESA3029 Aerothermodynamics"
type: concept
stream: "Block 5: Heat transfer"
aliases: ["fin efficiency", "fin effectiveness", "eta_fin", "epsilon_fin"]
tags: [sesa3029, concept, heat-transfer, fins, extended-surfaces]
status: complete
parent_lectures: ["[[SESA3029 W09c - Critical Thickness of Insulation and Fins]]"]
related_concepts: ["[[Fin Equation]]", "[[Newton's Law of Cooling]]"]
sources: ["02 - Sources/Lectures/Lecture5.4(1).pdf"]
---

# Fin Efficiency and Effectiveness

Fin efficiency $\eta_{\mathrm{fin}}=\dot Q_{\mathrm{fin}}/\dot Q_{\mathrm{fin,max}}$ compares a fin with an ideal fin of the same surface held entirely at the base temperature; fin effectiveness $\epsilon_{\mathrm{fin}}=\dot Q_{\mathrm{fin}}/\dot Q_{\mathrm{no\ fin}}$ compares it with the bare base area it covers.

The ideal fin has infinite conductivity, so $\dot Q_{\mathrm{fin,max}}=hA_{\mathrm{fin}}(T_b-T_\infty)$ with $A_{\mathrm{fin}}=pL$; the bare base gives $\dot Q_{\mathrm{no\ fin}}=hA_b(T_b-T_\infty)$ with $A_b=A_c$. With the heat rates from the [[Fin Equation]]:

| | Efficiency | Effectiveness |
|---|---|---|
| long fin | $1/(aL)$ | $\sqrt{kp/(hA_c)}$ |
| insulated tip | $\tanh(aL)/aL$ | $\sqrt{kp/(hA_c)}\,\tanh aL$ |

and in general $\epsilon_{\mathrm{fin}}=(A_{\mathrm{fin}}/A_b)\,\eta_{\mathrm{fin}}$. The long-fin efficiency exceeds 1 for $aL<1$, so it applies only to genuinely long fins.

The two are easy to swap. Efficiency is at most 1 and falls as a fin is made longer; effectiveness should be well above 1 (a fin with $\epsilon<1$ acts as insulation) and is what decides whether a fin is worth fitting. The effectiveness relation gives the design rules: high $k$ (metal fins), high $p/A_c$ (thin, slender fins) and low $h$ (gases and free convection, not liquids). A 5 mm aluminium pin fin 50 mm long in air at $h=20$ has $\eta=0.94$ and $\epsilon=37.5$.

![[at_w09c_fin_performance.png|760]]

## Related

- Parent lectures: [[SESA3029 W09c - Critical Thickness of Insulation and Fins#6. Fin efficiency|W09c §§6–8]]
- Related concepts: [[Fin Equation]] · [[Newton's Law of Cooling]]

## Sources

- L5.4 slides 19–25.
