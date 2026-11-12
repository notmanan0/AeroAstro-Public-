---
title: "Capacitance"
module: "FEEG1004 Electronics"
type: concept
stream: "Part A: Electrical Fundamentals and DC Circuits"
aliases: ["capacitor", "Q = CV", "i = C dv/dt", "parallel plate capacitor", "energy in a capacitor"]
tags: [feeg1004, concept, capacitor]
status: complete
parent_lectures: ["[[FEEG1004 A4 - Capacitors]]"]
related_concepts: ["[[RC and RL Transients]]", "[[Complex Impedance]]", "[[Capacitive Displacement Sensor]]"]
sources: ["02 - Sources/S1 Fundamentals/S1-W04-4 Capacitors - Recorded.pdf"]
---

# Capacitance

Capacitance $C$ is the charge a capacitor stores per volt across it, $Q=CV$. A capacitor stores energy in the electric field between its plates.

Differentiating $Q=CV$ gives the current–voltage law, and the parallel-plate geometry and stored energy complete the set:

$$
Q=CV,\qquad i=C\frac{dv}{dt},\qquad C=\frac{\varepsilon_0\varepsilon_rA}{d},\qquad E=\tfrac12CV^2.
$$

Because $i=C\,dv/dt$, the capacitor voltage is continuous: it cannot jump without an infinite current. In DC steady state $dv/dt=0$, so $i=0$ and the capacitor acts as an open circuit, while at switch-on from zero charge it acts as a short. In AC its impedance is $Z_C=1/j\omega C=-jX_C$, and the current leads the voltage by $90^\circ$ ([[Complex Impedance]]). Capacitances in parallel add; in series they combine like resistors in parallel.

Charging $5\ \mu\mathrm F$ with $1\ \mathrm{mA}$ for $5\ \mathrm s$ gives $1000\ \mathrm V$ and $2.5\ \mathrm J$. A steady-state divider that leaves $2\ \mathrm V$ on a $2\ \mu\mathrm F$ capacitor gives $Q=4\ \mu\mathrm C$. A smoothing capacitor sized by $C=I/(2f\Delta V)$ comes to $250\ \mu\mathrm F$ in Tutorial 3 Q6.

## Related

- [[FEEG1004 A4 - Capacitors]]
- [[RC and RL Transients]] · [[Rectification and Smoothing]] · [[Capacitive Displacement Sensor]] · [[Power Factor Correction]]
- Sources: Recorded lecture 4
