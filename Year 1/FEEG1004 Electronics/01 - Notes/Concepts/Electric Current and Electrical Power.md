---
title: "Electric Current and Electrical Power"
module: "FEEG1004 Electronics"
type: concept
stream: "Part A: Electrical Fundamentals and DC Circuits"
aliases: ["current", "I = dQ/dt", "P = VI", "drift velocity", "conventional current"]
tags: [feeg1004, concept, current, power]
status: complete
parent_lectures: ["[[FEEG1004 A1 - Electrostatics, Potential and Current]]"]
related_concepts: ["[[Electric Potential and Voltage]]", "[[Ohm's Law and Resistivity]]"]
sources: ["02 - Sources/S1 Fundamentals/S1-W02-1ab Electrostatics and Electric Current - Recorded.pdf"]
---

# Electric Current and Electrical Power

Electric current is the rate at which charge passes a point, and electrical power is the rate at which an element absorbs or supplies energy, equal to the voltage across it times the current through it.

$$
I=\frac{dQ}{dt}\ [\mathrm A=\mathrm{C/s}],\qquad P=VI\ [\mathrm W],\qquad I=neAv_d.
$$

**Conventional current** is the direction positive charge would flow; the electrons in a metal move the opposite way. Their drift velocity $v_d$ is only centimetres per hour, yet a signal travels along a wire at close to the speed of light, because the electric field that drives the carriers is set up that fast.

For a resistor, combining $P=VI$ with Ohm's law gives $P=I^2R=V^2/R$. The sign of the power follows the passive convention: if the current enters an element's positive terminal, the element absorbs power (a resistor, or a battery being charged); if it leaves the positive terminal, the element supplies power.

A flow of $0.1\ \mathrm C$ of protons in $2\ \mathrm s$ is a current of $0.05\ \mathrm A$. In Tutorial 1 Q2(v), Sam's battery takes $40\ \mathrm A$ at $11\ \mathrm V$, which is $440\ \mathrm W$: $400\ \mathrm W$ goes into chemical storage and $40\ \mathrm W$ is lost as heat in $R_{ESR}$.

## Related

- [[FEEG1004 A1 - Electrostatics, Potential and Current]] · [[FEEG1004 A3 - DC Circuit Laws - Ohm, KCL, KVL and Dividers]]
- [[Ohm's Law and Resistivity]] · [[Active, Reactive and Apparent Power]]
- Cross-module: [[Power and Efficiency]]
- Sources: Recorded lecture 1b
