---
title: "Thermal Efficiency and COP"
module: "SESA1016 Thermofluids"
type: concept
stream: "Thermodynamics"
aliases: ["thermal efficiency", "coefficient of performance", "COP"]
tags: [sesa1016, concept, heat-engine]
status: complete
parent_lectures: ["[[SESA1016 T3 - Heat Engines and the Second Law]]", "[[SESA1016 T5 - Ideal Heat Engine Models]]"]
related_concepts: ["[[Entropy Generation]]", "[[Isentropic Ideal-gas Relations]]", "[[Thermodynamic State and Process]]"]
sources: ["02 - Sources/Lectures/Chapter 3.pdf", "02 - Sources/Lectures/Chapter 5.pdf"]
---

# Thermal Efficiency and COP

Thermal efficiency is the fraction of the heat supplied to a heat engine that comes out as net work, $\eta_{th}=W_{net}/Q_{in}=1-Q_{out}/Q_{in}$; the coefficient of performance (COP) is the equivalent figure of merit for a heat pump or refrigerator, heat moved per unit work input.

Over a complete cycle the working fluid returns to its initial state, so $\Delta U=0$ and the first law gives $W_{net}=Q_{in}-Q_{out}$. The second law (Kelvin–Planck) says that some heat must always be rejected to a cold reservoir, so $\eta_{th}<1$. For a reversible engine taking $Q_H$ from a reservoir at $T_H$ and rejecting $Q_C$ to one at $T_C$, the entropy balance gives $Q_C/Q_H=T_C/T_H$, so the Carnot efficiency

$$
\eta_{Carnot}=1-\frac{T_C}{T_H}
$$

is the upper limit for any engine working between those temperatures, with $T$ in kelvin.

The ideal cycles of the course each have their own efficiency formula: $1-r^{1-\gamma}$ for the Otto cycle in terms of the compression ratio, and $1-r_p^{(1-\gamma)/\gamma}$ for the Brayton cycle in terms of the pressure ratio. They fall short of Carnot because heat is added and rejected over a range of temperatures rather than at the extremes.

Run backwards, a cycle uses work to move heat from cold to hot. For heating, $COP_{HP}=Q_H/W_{in}$; for cooling, $COP_R=Q_C/W_{in}$; and $COP_{HP}=COP_R+1$. A COP above 1 is normal: it measures heat moved per unit work, not energy converted.

![[tf_cycle_efficiency.png|760]]

## Related

- [[SESA1016 T3 - Heat Engines and the Second Law#2. Thermal efficiency|T3 efficiency]] · [[SESA1016 T3 - Heat Engines and the Second Law#Heat pumps|heat pumps]] · [[SESA1016 T5 - Ideal Heat Engine Models#Carnot efficiency|Carnot efficiency]] · [[SESA1016 T5 - Ideal Heat Engine Models#Brayton efficiency|Brayton efficiency]]
- [[Entropy Generation]] · [[Isentropic Ideal-gas Relations]] · [[Thermodynamic State and Process]]
