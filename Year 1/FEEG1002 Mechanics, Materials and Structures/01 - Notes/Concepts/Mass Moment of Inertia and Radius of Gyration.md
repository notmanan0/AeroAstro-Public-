---
title: "Mass Moment of Inertia and Radius of Gyration"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part D: Dynamics"
aliases: ["mass moment of inertia", "MMI", "radius of gyration", "I = mk^2", "rotational inertia", "moment of inertia", "second moment of mass"]
tags: [feeg1002, concept, dynamics, rigid-body, inertia]
status: complete
date: 2026-11-05
parent_lectures: ["[[FEEG1002 D8 - Kinetics of Rigid Bodies]]", "[[FEEG1002 D9 - Work and Energy for Rigid Bodies]]"]
related_concepts: ["[[Parallel Axis Theorem]]", "[[Planar Rigid-Body Equations of Motion]]", "[[Kinetic Energy of a Rigid Body]]"]
sources: ["02 - Sources/Dynamics/Lectures/Lecture 08 - Kinetics of Rigid Bodies.pdf"]
---

# Mass Moment of Inertia and Radius of Gyration

The mass moment of inertia $I_O=\int r_O^2\,dm$ (kg m²) of a body about an axis is its resistance to angular acceleration about that axis, the rotational counterpart of mass in $\sum M_O=I_O\alpha$. The radius of gyration $k=\sqrt{I/m}$ is the radius at which all the mass could be concentrated without changing $I$.

The definition comes straight from Newton's law for the elements. An element $dm$ at distance $r_O$ from a fixed axis has tangential acceleration $r_O\alpha$, needs a tangential force $\alpha r_O\,dm$, and so a moment $\alpha r_O^2\,dm$ about the axis. Summing over the body, with the same $\alpha$ for every element and the internal forces cancelling in pairs, gives $\sum M_O=\alpha\int r_O^2\,dm$.

Integration gives the standard values about G: a thin disc or solid cylinder about its axis $\tfrac12mR^2$, a slender rod about a perpendicular axis $\tfrac1{12}mL^2$, a thin hoop $mR^2$, a solid sphere $\tfrac25mR^2$, and a thin plate $a\times b$ about its normal $\tfrac1{12}m(a^2+b^2)$. The parallel-axis theorem $I_O=I_G+md^2$ moves these to any parallel axis, so the rod about its end has $\tfrac13mL^2$ and $I_G$ is the smallest value over all parallel axes. For a composite body, find its G, move each part's $I_{Gi}$ to that G and add; moments of inertia add only when taken about the same axis.

The radius of gyration describes how far out the mass sits: $k_G=R/\sqrt2$ for a disc and $R$ for a hoop. Since a rolling body's acceleration and speed depend only on $k/r$, the hoop always loses a race against the disc, whatever their masses and sizes. Likewise a rod pivoted at its foot falls with $\alpha=(l_G/k_A^2)\,g\sin\theta$, independent of its mass, and a point mass fixed at $2L/3$ from the pivot leaves the ratio, and so the fall, unchanged.

For a uniform plate the mass moment of inertia is the density times the polar second moment of area used in torsion. The geometry is the same, but the area quantity is in m⁴ and belongs to stiffness, while $I$ here is in kg m² and belongs to inertia; confusing them is a units error.

![[d_mass_moment_of_inertia.png|760]]

## Related

- [[FEEG1002 D8 - Kinetics of Rigid Bodies#2. Mass moment of inertia|D8 §2]] · [[FEEG1002 D8 - Kinetics of Rigid Bodies#Disc and slender rod|disc and rod]] · [[FEEG1002 D8 - Kinetics of Rigid Bodies#Parallel-axis theorem|parallel-axis theorem]] · [[FEEG1002 D8 - Kinetics of Rigid Bodies#Radius of gyration|radius of gyration]] · [[FEEG1002 D8 - Kinetics of Rigid Bodies#Falling rods with and without a point mass|falling rods]] · [[FEEG1002 D9 - Work and Energy for Rigid Bodies#Rolling race down a slope|rolling race]]
- [[Parallel Axis Theorem]] · [[Planar Rigid-Body Equations of Motion]] · [[Kinetic Energy of a Rigid Body]] · [[Torsion of Circular Shafts]]
- Year 2: the 3D [[Inertia Matrix]] in [[SESA2024 06 - Attitude Control]] · aircraft inertias in [[SESA2027 A1 - Dynamic Systems and Aircraft Equations of Motion]] · the area analogue in [[SESA2028 S1 - Section Properties and Unsymmetrical Bending]]
