---
title: "Over- and Under-Expanded Jets"
module: "SESA3029 Aerothermodynamics"
type: concept
stream: "Block 3: Nozzles and the Method of Characteristics"
aliases: ["over-expanded jet", "under-expanded jet", "shock diamonds", "Mach diamonds", "lip shock", "jet barrel"]
tags: [sesa3029, concept, nozzle, jet]
status: complete
parent_lectures: ["[[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow]]"]
related_concepts: ["[[Converging-Diverging Nozzle Operating Regimes]]", "[[Slip Line]]", "[[Expansion Fan]]", "[[Mach Reflection]]"]
sources: ["02 - Sources/Lectures/Lecture2-7.pdf"]
---

# Over- and Under-Expanded Jets

A supersonic nozzle is **over-expanded** when its exit pressure is below ambient ($p_{b6}<p_b<p_{b5}$, so $p_e<p_\infty$) and **under-expanded** when it is above ($p_b<p_{b6}$, so $p_e>p_\infty$). Either way the jet has to adjust to $p_\infty$, and it does so through waves at the nozzle lip. These reflect back and forth off the constant-pressure jet boundary and give the familiar **shock diamonds**.

In the over-expanded case (Lecture 2.7, slides 3–4), oblique shocks at the lip recompress the jet to $p_\infty$ and turn the boundary inward. Where the two lip shocks cross, the pressure overshoots above $p_\infty$. The shocks then reflect off the boundary as expansion fans, the fans cross and push the pressure below $p_\infty$, the fans reflect as compressions, and the cycle repeats. The under-expanded jet (slides 5–6) runs through the same cycle, starting with fans at the lip instead of shocks.

The lip shock is sized from the pressure ratio it has to produce:

$$
M_{n1}=\sqrt{1+\frac{\gamma+1}{2\gamma}\left(\frac{p_\infty}{p_e}-1\right)}.
$$

For $M_e=2.2$ and $p_b/p_0=0.2$ this gives $\beta=39.7^\circ$ and $\theta=13.7^\circ$, and the shocks cross regularly. A lip fan turns the flow through $\nu(M_j)-\nu(M_e)$, where $M_j$ is set by $p_\infty/p_0$; for $p_b/p_0=0.05$ that is $9.7^\circ$.

If the lip shock's turn is more than the flow behind it can take ($\theta_{max}$ at that Mach number), the crossing cannot be regular and a Mach disc forms. The planar estimate for $M_e=2.2$ is $p_b/p_0>0.216$. See [[Mach Reflection]].

![[at_nozzle_jets.png|760]]

## Related

- [[Converging-Diverging Nozzle Operating Regimes]] (SESA2023) · [[Slip Line]] · [[Expansion Fan]] · [[Mach Reflection]] · [[Afterburning (Reheat)]]
- Detail: [[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow#5. Over-expanded jets: lip shocks and shock diamonds (Lecture 2.7, slides 3–4)|W04 §5–6]]
