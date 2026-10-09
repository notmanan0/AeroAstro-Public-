---
title: "Back EMF and Torque Constants"
module: "FEEG1004 Electronics"
type: concept
stream: "Part C: Electric Machines"
aliases: ["K_T", "K_E", "back EMF", "torque constant", "EMF constant", "KT = KE", "DC motor equivalent circuit"]
tags: [feeg1004, concept, machines, dc-motor]
status: complete
parent_lectures: ["[[FEEG1004 C4 - DC Generators and the Commutator]]", "[[FEEG1004 C5 - DC Motors - Torque, Back EMF and Efficiency]]"]
related_concepts: ["[[Commutator]]", "[[Torque-Speed Characteristics of DC Motors]]", "[[Lorentz Force]]"]
sources: ["02 - Sources/S2 Machines/S2 Electric Machines Notes - Sharkh.pdf"]
---

# Back EMF and Torque Constants

## Definition

> [!note] Definition
> $$E = K_E\omega,\qquad T = K_Ti,\qquad K_E = K_T = \frac{ZN_p\Phi}{2\pi a}\ \ [\mathrm{V\,s/rad} = \mathrm{N\,m/A}]$$
> Steady equivalent circuit: $V = E\pm iR_a$ (+ for a motor, − for a generator).

## Explanation
- $Z$ = conductors, $a$ = parallel paths, $N_p$ = poles, $\Phi$ = flux per pole.
- $K_T = K_E$ is energy conservation: $Ei = T\omega$.
- **Measure** $K_E$ on open circuit: spin at a known ω and read the voltage.
- **Motor power flow**: $Vi$ → $i^2R_a$ lost → $Ei = T\omega$ → minus rotational losses → shaft.

![[ee_c5_dc_machine_circuits.png|700]]

## Examples
- Tutorial 6 Q1: 10 V at 1000 rpm gives $K_E$ = 0.0955 V s/rad.
- Sharkh example: $K$ = 1, 230 V, 20 A, $R_a$ = 0.5 Ω gives 220 rad/s, 20 N m, η = 91 %.

## Related
- Topic notes: [[FEEG1004 C5 - DC Motors - Torque, Back EMF and Efficiency]]
- Concepts: [[Torque-Speed Characteristics of DC Motors]] · [[Electric and Magnetic Loading]]
- Cross-module: [[Reaction Wheels and Momentum Dumping]]

## Sources
- Sharkh notes §4.1–4.3; Machines 05–07 slides
