---
title: "Electric and Magnetic Loading"
module: "FEEG1004 Electronics"
type: concept
stream: "Part C: Electric Machines"
aliases: ["torque per unit volume", "T = 2BAV", "electric loading", "magnetic loading", "machine sizing", "gearbox argument"]
tags: [feeg1004, concept, machines, sizing]
status: complete
parent_lectures: ["[[FEEG1004 C5 - DC Motors - Torque, Back EMF and Efficiency]]"]
related_concepts: ["[[Back EMF and Torque Constants]]"]
sources: ["02 - Sources/S2 Machines/S2 Electric Machines Notes - Sharkh.pdf", "02 - Sources/S2 Machines/S2-W18-21 Electric Machines 07 - DC Motors Characteristics - Lecture Slides.pdf"]
---

# Electric and Magnetic Loading

The magnetic loading $B$ of an electric machine is the average air-gap flux density, and the electric loading $A$ is the armature current per unit length of rotor circumference. Together they set the torque a rotor of given volume can produce:

$$
T=2\,B\,A\,V_R,\qquad A=\frac{Zi_c}{\pi D},\qquad V_R=\frac{\pi D^2L}{4},
$$

where $Z$ is the number of conductors, $i_c$ the conductor current, and $D$ and $L$ the rotor diameter and length.

Both loadings are much the same for machines of any size. $B$ is about $0.5$–$0.8\ \mathrm T$, limited by saturation of the steel, and $A$ is about $20$–$70\ \mathrm{kA/m}$, limited by cooling. Torque is therefore proportional to rotor volume, and since $P=T\omega$, the volume is proportional to $P/\omega$: high-speed machines are small for their power.

A motor driving a slow load therefore runs fast and drives it through a step-down gearbox, with ratios up to about $1000{:}1$, and slow wind and tidal turbines drive their generators through step-up gearboxes. Delivering $1\ \mathrm{kW}$ at $10\ \mathrm{rad/s}$ needs $100\ \mathrm{N\,m}$, while at $100\ \mathrm{rad/s}$ it needs only $10\ \mathrm{N\,m}$ and about a tenth of the volume. Tutorial 6 Q4 derives $T=2BAV_R$, and Q5 asks why gearboxes are used.

## Related

- [[FEEG1004 C5 - DC Motors - Torque, Back EMF and Efficiency]]
- Cross-module: [[Specific Speed]] · [[Dimensional Analysis of Turbomachines]]
- Sources: Sharkh notes §4.4; Machines 07 slides
