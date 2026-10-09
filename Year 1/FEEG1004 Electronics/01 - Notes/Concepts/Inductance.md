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

## Definition

> [!note] Definition
>
> $$N\Phi = Li,\qquad v = L\frac{di}{dt},\qquad E = \tfrac{1}{2}LI^2,\qquad L = \frac{N^2}{\mathcal R} = \frac{N^2\mu_0\mu_rA}{l}$$

## Explanation
- An inductor stores energy in its **magnetic field**. It behaves like **inertia**: $V = L\,di/dt$ ↔ $F = m\,dv/dt$.
- $i_L$ is **continuous**. At DC steady state an inductor is a **short**; at switch-on it is momentarily an **open circuit**.
- Interrupting inductor current forces a large $L\,di/dt$: arcs, ignition sparks and killed transistors. The remedy is a flyback diode.
- In AC, $Z_L = j\omega L$ and the current **lags** by 90°.
- Changing $N$, the reluctance, the gap or the core position changes $L$: the principle of **inductive sensors** ([[Linear Variable Differential Transformer]]).

## Examples
- 4 V across 5 mH gives 800 A/s.
- A 6 V step into $L$ + $R$ with initial $di/dt$ = 3000 A/s and 60 mA final means $L$ = 2 mH and $R$ = 100 Ω.
- Tutorial 2 Q5: 60 A interrupted into 1 MΩ gives 60 MV in theory; in practice an arc forms.

## Related
- Topic notes: [[FEEG1004 A5 - Inductors and Electrical Resonance]] · [[FEEG1004 A7 - Thevenin, Superposition and Relays]]
- Concepts: [[RC and RL Transients]] · [[Flyback Diode]] · [[Complex Impedance]] · [[Magnetomotive Force and Reluctance]]

## Sources
- Recorded lecture 5a; Transducers lecture 2
