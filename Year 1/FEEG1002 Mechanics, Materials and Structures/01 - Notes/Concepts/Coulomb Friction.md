---
title: "Coulomb Friction"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part D: Dynamics"
aliases: ["static friction", "kinetic friction", "dry friction", "mu_s N", "mu_k N", "impending motion", "sliding friction", "coefficient of friction"]
tags: [feeg1002, concept, dynamics, friction]
status: complete
date: 2026-11-05
parent_lectures: ["[[FEEG1002 D1 - Linear Motion of Particles]]", "[[FEEG1002 D3 - Work, Energy and Power]]", "[[FEEG1002 D8 - Kinetics of Rigid Bodies]]", "[[FEEG1002 D9 - Work and Energy for Rigid Bodies]]"]
related_concepts: ["[[Newton's Laws of Motion]]", "[[Rolling Without Slip]]", "[[Work-Energy Principle]]"]
sources: ["02 - Sources/Dynamics/Lectures/Lecture 01 - Linear Motion.pdf", "02 - Sources/Dynamics/Lectures/Lecture 08 - Kinetics of Rigid Bodies.pdf"]
---

# Coulomb Friction

Coulomb friction is the standard model of dry friction between unlubricated surfaces: while they do not slide, the friction force is whatever equilibrium or the equation of motion requires, up to a limit $\mu_sN$; once they slide, it is $\mu_kN$ and opposes the sliding.

$$
F_s\le\mu_sN\quad\text{(no sliding)},\qquad F_k=\mu_kN\quad\text{(sliding)}
$$

Here $N$ is the normal reaction and in general $\mu_k<\mu_s$. The coefficients are taken as independent of contact area, load and speed. As the applied force on a block rises from zero, friction follows it with slope 1 up to $\mu_sN$, the point of impending sliding, then drops to the constant $\mu_kN$ once the block moves. The model does not describe a rolling tyre on a road.

The inequality cannot be used to calculate the static friction force. That force comes from equilibrium (or from the equations of motion of a body that is not sliding at the contact) and is then checked against $\mu_sN$. Writing $F_s=\mu_sN$ into an equation of motion is the most common error, and the same holds for a wheel assumed to roll without slip. The procedure is to assume no slip, solve for the friction needed, and check it. For the lawn roller of D8 the no-slip solution needs 94.3 N but only $\mu_sN=81.0$ N is available, so the roller slips and the friction becomes $\mu_kN=67.5$ N, directed against the sliding at the contact.

The direction of static friction on a wheel depends on the drive: a wheel turned by a torque at its axle gets forward friction, while one pulled at its centre gets backward friction, which is what makes it turn.

Kinetic friction always does negative work, $-\mu_kNs$ over a sliding distance $s$, and is non-conservative; for a slipping wheel the distance is the slippage distance at the contact. Static friction usually does no work because its point of application does not move relative to the surface. A crate carried by an accelerating lorry is the exception: friction does positive work on the crate and equal negative work on the lorry, none for the pair.

![[d_coulomb_friction.png|760]]

## Related

- [[FEEG1002 D1 - Linear Motion of Particles#Dry friction|dry friction in D1]] · [[FEEG1002 D1 - Linear Motion of Particles#Block pulled through a pulley|block at impending sliding]] · [[FEEG1002 D3 - Work, Energy and Power#Work of friction|work of friction]] · [[FEEG1002 D3 - Work, Energy and Power#Block sliding down a rough incline|rough incline]] · [[FEEG1002 D3 - Work, Energy and Power#Friction and heat|friction and heat]] · [[FEEG1002 D8 - Kinetics of Rigid Bodies#Rolling with and without slip|rolling with and without slip]] · [[FEEG1002 D8 - Kinetics of Rigid Bodies#Lawn roller pushed along the ground|lawn roller]] · [[FEEG1002 D9 - Work and Energy for Rigid Bodies#Rolling wheels|work on rolling wheels]]
- [[Newton's Laws of Motion]] · [[Rolling Without Slip]] · [[Work-Energy Principle]]
- Year 2: friction and wear of surfaces in [[SESA2028 M3 - Corrosion, Wear and Surface Engineering]]
