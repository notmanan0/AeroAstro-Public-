---
title: "Entropy Generation"
module: "SESA1016 Thermofluids"
type: concept
stream: "Thermodynamics"
aliases: ["irreversibility", "S_gen"]
tags: [sesa1016, concept, entropy]
status: complete
parent_lectures: ["[[SESA1016 T3 - Heat Engines and the Second Law]]", "[[SESA1016 T4 - Entropy and Isentropic Relations]]"]
related_concepts: ["[[Thermal Efficiency and COP]]", "[[Isentropic Ideal-gas Relations]]", "[[Thermodynamic State and Process]]"]
sources: ["02 - Sources/Lectures/Chapter 4.pdf"]
---

# Entropy Generation

Entropy generation $S_{gen}$ is the entropy created inside a system by irreversibilities, defined by $dS=dQ/T+dS_{gen}$ with $dS_{gen}\ge0$; it is zero only for a reversible process.

The entropy of a system can change for two reasons: heat crossing the boundary carries entropy $dQ/T$ in or out, and irreversible processes inside create more. The second law is the statement that the second part is never negative. Friction, mixing, unrestrained expansion and heat transfer across a finite temperature difference all generate entropy.

The cleanest example is heat $Q$ flowing from a reservoir at $T_H$ to one at $T_C$. The hot reservoir loses $Q/T_H$ of entropy, the cold one gains $Q/T_C$, and since $T_C<T_H$ the total rises:

$$
S_{gen}=Q\left(\frac1{T_C}-\frac1{T_H}\right)>0
$$

Reversing the flow would make $S_{gen}$ negative, which is why heat does not flow from cold to hot unaided. The larger the temperature difference, the more entropy is generated per joule transferred.

Entropy generation is the measure of lost work. A reversible engine between two reservoirs generates no entropy and reaches the Carnot efficiency; every irreversibility in a real engine generates entropy, forces more heat to be rejected and lowers the efficiency. An adiabatic process is isentropic only if it is also reversible: an adiabatic compressor with friction ends at a higher entropy and temperature than the isentropic one.

## Related

- [[SESA1016 T4 - Entropy and Isentropic Relations#2. Entropy generation|T4 §2]] · [[SESA1016 T4 - Entropy and Isentropic Relations#Worked example - which heat transfer is more irreversible|which transfer is more irreversible]] · [[SESA1016 T4 - Entropy and Isentropic Relations#Worked example - adiabatic but not isentropic|adiabatic but not isentropic]] · [[SESA1016 T5 - Ideal Heat Engine Models#Why nothing beats Carnot|why nothing beats Carnot]]
- [[Thermal Efficiency and COP]] · [[Isentropic Ideal-gas Relations]] · [[Thermodynamic State and Process]]
