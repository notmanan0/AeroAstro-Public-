---
title: "Lorentz Force"
module: "FEEG1004 Electronics"
type: concept
stream: "Part A: Electrical Fundamentals and DC Circuits"
aliases: ["Lorentz force", "F = BIL", "F = q(E + v x B)", "Fleming's left-hand rule", "motor effect"]
tags: [feeg1004, concept, magnetism, force]
status: complete
parent_lectures: ["[[FEEG1004 A2 - Magnetism, Induction and the Lorentz Force]]", "[[FEEG1004 C1 - Magnetic Circuits, Faraday's Law and Force on Conductors]]"]
related_concepts: ["[[Back EMF and Torque Constants]]", "[[Faraday's Law and Lenz's Law]]"]
sources: ["02 - Sources/S1 Fundamentals/S1-W03-2ab Magnetism and Induction - Recorded.pdf"]
---

# Lorentz Force

The Lorentz force is the force on a charge $q$ moving with velocity $\mathbf v$ through electric and magnetic fields. For a straight wire carrying current $I$ across a field, it reduces to $F = BIL$.

$$
\mathbf F = q(\mathbf E + \mathbf v\times\mathbf B),\qquad F = BIL\ \ \text{(straight wire, }\mathbf B\perp\mathbf L)
$$

The magnetic part of the force is perpendicular to both the velocity and the field. It bends the path of a free charge but does no work on it. Particle tracks in a field pointing out of the page therefore curve one way for positive charges and the other way for negative ones, which reveals the sign of each particle's charge.

For a wire, the moving charges in a length $L$ give $q\mathbf v = I\mathbf L$, which turns the charge formula into $\mathbf F = I\mathbf L\times\mathbf B$ and, for a wire perpendicular to the field, $F = BIL$. In Tutorial 5 Q3, $1\ \mathrm{kA}$ over $10\ \mathrm m$ in $10^{-4}\ \mathrm T$ gives a vertical force of $1\ \mathrm N$. The direction follows Fleming's left-hand rule (first finger field, second finger current, thumb motion) for a positive charge or conventional current; for negative charges the force reverses. Two parallel currents attract and two antiparallel currents repel.

![[ee_c1_motor_generator_effect.png|640]]

The same force drives an electric motor. Each armature conductor feels $F = BIL$, and multiplying by the radius $D/2$ gives its contribution to the torque ([[Back EMF and Torque Constants]]).

## Related

- [[FEEG1004 A2 - Magnetism, Induction and the Lorentz Force]] · [[FEEG1004 C5 - DC Motors - Torque, Back EMF and Efficiency]]
- [[Motional EMF in Electric Machines]] · [[Electric and Magnetic Loading]]
- Cross-module: magnetorquers, [[Attitude Sensors and Torquers]]
- Sources: Recorded lecture 2b; Sharkh machines notes §2.2
