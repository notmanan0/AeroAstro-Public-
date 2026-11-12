---
title: "Inductance"
module: "FEEG1004 Electronics"
type: concept
stream: "Part A: Electrical Fundamentals and DC Circuits"
aliases: ["inductor", "v = L di/dt", "self-inductance", "energy in an inductor", "L = N^2/S"]
tags: [feeg1004, concept, inductor, magnetism]
status: complete
parent_lectures: ["[[FEEG1004 A5 - Inductors and Electrical Resonance]]"]
related_concepts: ["[[RC and RL Transients]]", "[[Faraday's Law and Lenz's Law]]", "[[Magnetomotive Force and Reluctance]]", "[[Flyback Diode]]"]
sources: ["02 - Sources/S1 Fundamentals/S1-W05-5abc Inductors and Resonance - Recorded.pdf", "02 - Sources/S2 Transducers/S2-W26-31 Transducers 02 - Displacement Sensors - Lecture Slides.pdf"]
---

# Inductance

Inductance $L$ is the flux linkage a coil produces per unit of its own current, $N\Phi = Li$. Through Faraday's law it sets the voltage needed to change that current.

$$
N\Phi = Li,\qquad v = L\frac{di}{dt},\qquad E = \tfrac{1}{2}LI^2,\qquad L = \frac{N^2}{\mathcal R} = \frac{N^2\mu_0\mu_rA}{l}
$$

An inductor stores energy in its magnetic field and behaves like inertia: $v = L\,di/dt$ has the same form as $F = m\,dv/dt$. A voltage sets the rate of change of current, not the current itself, so $4\ \mathrm V$ across $5\ \mathrm{mH}$ makes the current rise at $800\ \mathrm{A/s}$. For the same reason the inductor current is continuous. At the instant of switch-on an inductor acts as an open circuit, and in DC steady state it acts as a short. A $6\ \mathrm V$ step applied to $L$ in series with $R$, with initial $di/dt = 3000\ \mathrm{A/s}$ and final current $60\ \mathrm{mA}$, therefore gives $L = 6/3000 = 2\ \mathrm{mH}$ and $R = 6/0.06 = 100\ \Omega$.

Interrupting an inductor current forces a very large $L\,di/dt$. This produces switch arcs and ignition sparks and destroys driving transistors unless a [[Flyback Diode]] gives the current a path. In Tutorial 2 Q5, $60\ \mathrm A$ forced into $1\ \mathrm{M\Omega}$ would in theory give $60\ \mathrm{MV}$; in practice an arc forms long before that.

In AC analysis the inductor has impedance $Z_L = j\omega L$, and its current lags its voltage by $90^\circ$. The magnetic-circuit form $L = N^2/\mathcal R$ shows that changing the number of turns, the reluctance, an air gap or the position of a core changes $L$. That is the operating principle of inductive sensors ([[Linear Variable Differential Transformer]]).

## Related

- [[FEEG1004 A5 - Inductors and Electrical Resonance]] · [[FEEG1004 A7 - Thevenin, Superposition and Relays]]
- [[RC and RL Transients]] · [[Flyback Diode]] · [[Complex Impedance]] · [[Magnetomotive Force and Reluctance]]
- Sources: Recorded lecture 5a; Transducers lecture 2
