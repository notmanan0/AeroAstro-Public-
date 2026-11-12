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

In a DC machine the back EMF is proportional to the rotor speed and the electromagnetic torque is proportional to the armature current. The two constants of proportionality, $K_E$ and $K_T$, are equal:

$$
E=K_E\omega,\qquad T=K_Ti,\qquad K_E=K_T=\frac{ZN_p\Phi}{2\pi a}\ \ [\mathrm{V\,s/rad}=\mathrm{N\,m/A}],
$$

where $Z$ is the number of armature conductors, $a$ the number of parallel paths, $N_p$ the number of poles and $\Phi$ the flux per pole.

The equality is energy conservation. The electrical power converted, $Ei$, must equal the mechanical power $T\omega$, and substituting both relations gives $K_E\omega i=K_Ti\omega$. In steady state the armature is modelled as the EMF in series with its resistance, $V=E\pm iR_a$, with the plus sign for a motor and the minus sign for a generator. Power then flows through a motor as $Vi$ in, $i^2R_a$ lost in the armature, $Ei=T\omega$ converted, and that less the rotational losses delivered to the shaft.

$K_E$ is measured on open circuit: spin the machine at a known $\omega$ and read the terminal voltage, which then equals $E$.

![[ee_c5_dc_machine_circuits.png|700]]

In Tutorial 6 Q1, $10\ \mathrm V$ at $1000\ \mathrm{rpm}$ gives $K_E=0.0955\ \mathrm{V\,s/rad}$. In the Sharkh example, $K=1$, $230\ \mathrm V$, $20\ \mathrm A$ and $R_a=0.5\ \Omega$ give $220\ \mathrm{rad/s}$, $20\ \mathrm{N\,m}$ and, with $200\ \mathrm W$ of rotational loss, an efficiency of $91\ \%$.

## Related

- [[FEEG1004 C5 - DC Motors - Torque, Back EMF and Efficiency]]
- [[Torque-Speed Characteristics of DC Motors]] · [[Electric and Magnetic Loading]]
- Cross-module: [[Reaction Wheels and Momentum Dumping]]
- Sources: Sharkh notes §4.1–4.3; Machines 05–07 slides
