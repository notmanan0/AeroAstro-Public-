---
title: "Newton's Laws of Motion"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part D: Dynamics"
aliases: ["F = ma", "Newton's second law", "inertial frame", "kinetic diagram", "equation of motion", "law of inertia", "Newtonian frame"]
tags: [feeg1002, concept, dynamics, kinetics]
status: complete
date: 2026-11-05
parent_lectures: ["[[FEEG1002 D1 - Linear Motion of Particles]]", "[[FEEG1002 D2 - Curvilinear Motion]]"]
related_concepts: ["[[Free Body Diagram and Equilibrium]]", "[[Kinematic Relations for Rectilinear Motion]]", "[[Coulomb Friction]]", "[[Principle of Linear Impulse and Momentum]]"]
sources: ["02 - Sources/Dynamics/Lectures/Lecture 01 - Linear Motion.pdf", "02 - Sources/Dynamics/Lectures/Lecture 02 - Curvilinear Motion.pdf"]
---

# Newton's Laws of Motion

Newton's laws relate the forces on a particle to its motion, and in the form used here they are:

1. A particle at rest, or moving in a straight line at constant velocity, stays so if the resultant force on it is zero.
2. A non-zero resultant force gives the particle an acceleration in the direction of the force, proportional to the force and inversely proportional to the mass: $\sum\mathbf F=m\mathbf a$.
3. The forces two particles exert on each other are equal, opposite and collinear.

The **mass** $m$ measures inertia, the resistance to a change of velocity, and is a property of the body; the weight $W=mg$ depends on where the body is. The second law holds only if $\mathbf a$ is measured in an **inertial** frame, one that is not itself accelerating. Near the ground the frame is fixed to the Earth with its rotation neglected; for satellites it is fixed to the stars. An observer riding in an accelerating vehicle would have to invent forces to explain what they see, and such fictitious forces never appear on a free-body diagram. In particular there is no centrifugal force: a particle on a curved path needs an unbalanced force towards the centre of curvature, $\sum F_n=mv^2/\rho$, and nothing pushes it outwards.

Every equation of motion is set up the same way: choose positive directions, draw the free-body diagram with every external force, draw the kinetic diagram with $m\mathbf a$ in the positive direction, and equate the two component by component. Whether the weight appears depends on the plane of the problem; in a top view it is balanced by the normal reaction and is left out. A rope holding a mass carries $T=mg$ at rest but $T=m(g+a)$ when the mass accelerates upwards.

The other principles of the dynamics stream are the second law rearranged. Integrating it along the path gives the work-energy principle, integrating it over time gives impulse and momentum, and taking its moment about a fixed point gives $\sum\mathbf M_O=\dot{\mathbf H}_O$. The third law is what makes internal forces cancel in pairs, so that a system's centre of mass moves as a particle under the external forces alone.

## Related

- [[FEEG1002 D1 - Linear Motion of Particles#4. Newton's laws and the equation of motion|D1 §4]] · [[FEEG1002 D1 - Linear Motion of Particles#Inertial frames|inertial frames]] · [[FEEG1002 D1 - Linear Motion of Particles#Ropes and cords|ropes and cords]] · [[FEEG1002 D2 - Curvilinear Motion#5. Equations of motion in n-t coordinates|n-t form in D2]] · [[FEEG1002 D4 - Linear Impulse and Momentum#Systems of particles|systems of particles]] · [[FEEG1002 D5 - Angular Impulse and Momentum#2. The moment equation|moment equation]] · [[FEEG1002 D8 - Kinetics of Rigid Bodies#General plane motion|rigid bodies]]
- [[Free Body Diagram and Equilibrium]] · [[Kinematic Relations for Rectilinear Motion]] · [[Normal and Tangential Coordinates]] · [[Coulomb Friction]] · [[Principle of Linear Impulse and Momentum]] · [[Work-Energy Principle]]
- Later: aircraft equations of motion in a rotating body frame, [[SESA2027 A1 - Dynamic Systems and Aircraft Equations of Motion]] · the [[Transport Theorem]] · control-volume momentum, [[SESA1016 T12 - Conservation of Momentum]]
