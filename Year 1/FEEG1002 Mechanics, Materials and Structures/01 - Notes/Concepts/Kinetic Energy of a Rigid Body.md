---
title: "Kinetic Energy of a Rigid Body"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part D: Dynamics"
aliases: ["rotational kinetic energy", "1/2 I omega^2", "KE = 1/2 m vG^2 + 1/2 IG omega^2", "translational kinetic energy", "König's theorem"]
tags: [feeg1002, concept, dynamics, rigid-body, energy]
status: complete
date: 2026-11-05
parent_lectures: ["[[FEEG1002 D9 - Work and Energy for Rigid Bodies]]"]
related_concepts: ["[[Work-Energy Principle]]", "[[Instantaneous Centre of Rotation]]", "[[Mass Moment of Inertia and Radius of Gyration]]", "[[Rolling Without Slip]]"]
sources: ["02 - Sources/Dynamics/Lectures/Lecture 09 - Work and Energy for Rigid Bodies.pdf"]
---

# Kinetic Energy of a Rigid Body

The kinetic energy of a rigid body in plane motion is the translational kinetic energy of its centre of mass plus the rotational kinetic energy about G.

$$
KE=\tfrac12mv_G^2+\tfrac12I_G\omega^2
$$

It comes from adding $\tfrac12v^2\,dm$ over the body with each element's velocity written as $\mathbf v=\mathbf v_G+\boldsymbol\omega\times\boldsymbol\rho$, where $\boldsymbol\rho$ is the element's position from G. Squaring gives $v_G^2$, a cross term $2\mathbf v_G\cdot(\boldsymbol\omega\times\boldsymbol\rho)$ and $\omega^2\rho^2$. The cross term integrates to zero because $\int\boldsymbol\rho\,dm=\mathbf 0$ about the centre of mass, and $\int\rho^2\,dm=I_G$. The split works only about G; writing $\tfrac12mv_P^2+\tfrac12I_P\omega^2$ for some other point P is wrong.

The general form reduces in the special cases. A translating body has $\tfrac12mv_G^2$. A body rotating about a fixed axis O has $v_G=r_G\omega$, so $KE=\tfrac12(I_G+mr_G^2)\omega^2=\tfrac12I_O\omega^2$, which packages translation and rotation together. In general plane motion the same step about the instantaneous centre gives $\tfrac12I_{IC}\omega^2$, valid only at the instant considered. For connected bodies the energies add.

The energy equation gives only the total, and the split comes from kinematics or from a second equation such as $\sum M_G=I_G\alpha$. A body rolling without slip has $v=r\omega$, so

$$
KE=\tfrac12mv^2\left(1+\frac{k^2}{r^2}\right)
$$

and the share in translation is $1/(1+k^2/r^2)$: 2/3 for a solid cylinder and 1/2 for a thin hollow one, which is why the hollow cylinder loses a race down a slope. A bar thrown upwards while spinning has $\sum M_G=0$, so its spin and rotational energy stay constant and G rises exactly as high as for a bar without spin. Forgetting the rotational term of a rolling wheel is the usual mistake.

For the 30 kg disc of radius 0.2 m pinned at its centre, $I_O=0.6$ kg m² and at 20 rad/s it holds $KE=120$ J, supplied by a 5 N m couple and a 10 N cord pull over 2.73 revolutions.

## Related

- [[FEEG1002 D9 - Work and Energy for Rigid Bodies#1. Kinetic energy of a rigid body|D9 §1]] · [[FEEG1002 D9 - Work and Energy for Rigid Bodies#General plane motion and the IC|about the IC]] · [[FEEG1002 D9 - Work and Energy for Rigid Bodies#Systems of bodies|systems of bodies]] · [[FEEG1002 D9 - Work and Energy for Rigid Bodies#Disc turned by a couple and a cord|disc example]] · [[FEEG1002 D9 - Work and Energy for Rigid Bodies#Rolling race down a slope|rolling race]] · [[FEEG1002 D8 - Kinetics of Rigid Bodies#Radius of gyration|radius of gyration]]
- [[Work-Energy Principle]] · [[Instantaneous Centre of Rotation]] · [[Mass Moment of Inertia and Radius of Gyration]] · [[Rolling Without Slip]]
- Year 2: energy stored in spinning wheels, [[Reaction Wheels and Momentum Dumping]]
