---
title: "Internal Energy and Enthalpy"
module: "SESA1016 Thermofluids"
type: concept
stream: "Thermodynamics"
aliases: ["internal energy", "enthalpy"]
tags: [sesa1016, concept, energy]
status: complete
parent_lectures: ["[[SESA1016 T2 - Work, Heat and the First Law]]", "[[SESA1016 T13 - Conservation of Energy and Propulsion]]"]
related_concepts: ["[[Boundary Work]]", "[[Steady-flow Energy Equation]]", "[[Ideal-gas Law]]"]
sources: ["02 - Sources/Lectures/Chapter 2.pdf", "02 - Sources/Lectures/Chapter 13.pdf"]
---

# Internal Energy and Enthalpy

Internal energy $U$ is the energy stored in the random motion and interactions of a substance's molecules; enthalpy is the combination $H=U+pV$, per unit mass $h=u+pv$.

For an ideal gas both depend on temperature only. Heating at constant volume does no boundary work, so all the heat raises $u$ and $du=c_v\,dT$. Heating at constant pressure also does work $p\,dV$, and the heat then equals the change in enthalpy, $dh=c_p\,dT$. Differentiating $h=u+RT$ gives Mayer's relation $c_p=c_v+R$, and the ratio $\gamma=c_p/c_v$ is 1.4 for air.

$$
\Delta u=c_v\Delta T,\qquad \Delta h=c_p\Delta T,\qquad c_p-c_v=R
$$

These hold for any ideal-gas process, not only constant-volume or constant-pressure ones, because $u$ and $h$ are properties: once the end temperatures are known the changes are fixed, whatever the path.

Enthalpy is the natural property for flowing systems. Every kilogram pushed into a control volume brings its internal energy $u$ and also the flow work $pv$ done on it by the fluid behind; the two always appear together, so the [[Steady-flow Energy Equation]] is written in $h$, and in the total enthalpy $h_{tot}=h+\tfrac12V^2+gz$ once kinetic and potential energy are included.

## Related

- [[SESA1016 T2 - Work, Heat and the First Law#3. Heat, internal energy and the specific heats|T2 §3]] · [[SESA1016 T2 - Work, Heat and the First Law#Relations between the gas constants|gas constants]] · [[SESA1016 T13 - Conservation of Energy and Propulsion#Shaft work and flow work|flow work]] · [[SESA1016 T13 - Conservation of Energy and Propulsion#Total enthalpy and the SFEE|total enthalpy]]
- [[Boundary Work]] · [[Steady-flow Energy Equation]] · [[Ideal-gas Law]]
