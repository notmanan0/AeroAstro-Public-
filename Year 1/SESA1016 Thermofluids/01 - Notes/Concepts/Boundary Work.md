---
title: "Boundary Work"
module: "SESA1016 Thermofluids"
type: concept
stream: "Thermodynamics"
aliases: ["p dV work", "piston work"]
tags: [sesa1016, concept, work]
status: complete
parent_lectures: ["[[SESA1016 T2 - Work, Heat and the First Law]]"]
related_concepts: ["[[Thermodynamic State and Process]]", "[[Internal Energy and Enthalpy]]", "[[Ideal-gas Law]]"]
sources: ["02 - Sources/Lectures/Chapter 2.pdf"]
---

# Boundary Work

Boundary work is the work a closed system does when its boundary moves against the pressure of the gas inside, $W=\int p\,dV$, positive when the system expands.

A gas at pressure $p$ pushing a piston of area $A$ through $dx$ does work $pA\,dx=p\,dV$. Summing over a quasi-equilibrium process, in which the pressure is uniform and well defined at every instant, gives

$$
W_{12}=\int_{V_1}^{V_2}p\,dV,
$$

which is the area under the process path on a $p$–$V$ diagram. Two processes between the same end states can enclose different areas, so work depends on the path and is not a property. That is also why a cycle can produce net work: the area enclosed by the loop.

For the standard ideal-gas processes the integral has closed forms. At constant volume $W=0$. At constant pressure $W=p(V_2-V_1)$. In an isothermal process $p=mRT/V$, so $W=mRT\ln(V_2/V_1)$. In a reversible adiabatic process $pV^\gamma=\text{const}$ and $W=(p_1V_1-p_2V_2)/(\gamma-1)$.

The sign convention follows the first law in the form $\Delta U=Q-W$: work done by the system is positive, so compression work is negative. In a flowing system the same $p\,dV$ idea appears as flow work $pv$ per unit mass, which is why enthalpy $h=u+pv$ is the natural property for open systems.

![[tf_work_paths.png|760]]

## Related

- [[SESA1016 T2 - Work, Heat and the First Law#2. Pressure–volume work|T2 §2]] · [[SESA1016 T2 - Work, Heat and the First Law#Worked example - three paths between the same two states|three paths example]]
- [[Thermodynamic State and Process]] · [[Internal Energy and Enthalpy]] · [[Ideal-gas Law]]
