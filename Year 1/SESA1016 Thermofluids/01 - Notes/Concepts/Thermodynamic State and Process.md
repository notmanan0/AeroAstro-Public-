---
title: "Thermodynamic State and Process"
module: "SESA1016 Thermofluids"
type: concept
stream: "Thermodynamics"
aliases: ["state", "process", "quasi-equilibrium"]
tags: [sesa1016, concept, thermodynamics]
status: complete
parent_lectures: ["[[SESA1016 T1 - Thermodynamic Systems, Properties and State]]"]
related_concepts: ["[[Ideal-gas Law]]", "[[Boundary Work]]", "[[Closed System vs Control Volume]]"]
sources: ["02 - Sources/Lectures/Chapter 1.pdf"]
---

# Thermodynamic State and Process

The state of a system is its condition as described by its properties (pressure, temperature, specific volume, internal energy and so on); a process is any change from one equilibrium state to another, and the path is the sequence of states it passes through.

The state postulate says that the state of a simple compressible substance is fixed by two independent intensive properties. For an ideal gas any two of $p$, $v$ and $T$ fix the third through $pv=RT$, and with it $u$, $h$ and $s$. Properties depend only on the state, so their changes between two states are independent of the path; work and heat are not properties, and depend on the path taken.

Properties are well defined only in equilibrium, when they are uniform through the system. A quasi-equilibrium (quasi-static) process is one carried out slowly enough that the system passes through a continuous sequence of equilibrium states, which is what allows it to be drawn as a line on a $p$–$v$ or $T$–$s$ diagram and its work to be computed as $\int p\,dV$. Real processes are faster, but the idealisation is accurate when the process is slow compared with the time the gas takes to even out, which is short for a gas.

Processes are named by what is held constant: isothermal ($T$), isobaric ($p$), isochoric ($v$), adiabatic (no heat transfer) and isentropic ($s$). A cycle is a sequence of processes that returns the system to its initial state, so every property change over a cycle is zero.

![[tf_state_paths.png|760]]

## Related

- [[SESA1016 T1 - Thermodynamic Systems, Properties and State#4. State, equilibrium and the state postulate|T1 §4]] · [[SESA1016 T1 - Thermodynamic Systems, Properties and State#6. Processes and state diagrams|processes and diagrams]] · [[SESA1016 T2 - Work, Heat and the First Law#4. Summary of the four processes|four processes]]
- [[Ideal-gas Law]] · [[Boundary Work]] · [[Closed System vs Control Volume]]
