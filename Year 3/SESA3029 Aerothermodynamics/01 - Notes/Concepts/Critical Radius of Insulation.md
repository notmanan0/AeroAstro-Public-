---
title: "Critical Radius of Insulation"
module: "SESA3029 Aerothermodynamics"
type: concept
stream: "Block 5: Heat transfer"
aliases: ["critical radius of insulation", "critical thickness of insulation", "critical radius", "r_cr = k/h"]
tags: [sesa3029, concept, heat-transfer, conduction, convection, insulation]
status: complete
parent_lectures: ["[[SESA3029 W09c - Critical Thickness of Insulation and Fins]]"]
related_concepts: ["[[Newton's Law of Cooling]]", "[[Fin Equation]]"]
sources: ["02 - Sources/Lectures/Lecture5.4(1).pdf"]
---

# Critical Radius of Insulation

The critical radius of insulation is the outer radius at which insulation round a cylinder gives the greatest heat loss, $r_{cr}=k/h$, with $k$ the conductivity of the insulation and $h$ the outside heat transfer coefficient.

Insulation round a pipe or wire puts two resistances in series per length $L$: conduction $\ln(r_o/r_i)/(2\pi kL)$, which grows only logarithmically with the outer radius, and convection $1/(2\pi r_oLh)$, which falls as $1/r_o$ because the outer surface area grows linearly with radius. Setting $\mathrm d\dot Q/\mathrm dr_o=0$ gives $1/(kr_o)=1/(hr_o^2)$, so $r_o=k/h$, and the second derivative shows the total resistance is a minimum there, so the heat rate is a maximum.

Consequences:

- if the bare radius already exceeds $k/h$, every layer of insulation reduces the heat loss (the normal case for pipes: $k\approx0.04$, $h\approx10$ gives 4 mm);
- if the bare radius is smaller, insulation first increases the heat loss, up to a maximum at $r_{cr}$, and only falls below the bare value at a much larger radius. A 1 mm wire with a $k=0.15$ sheath in air at $h=10$ has $r_{cr}=15$ mm and loses four times as much heat at that radius as bare.

A thicker layer of insulation therefore does not always reduce the heat transfer rate. For a sphere the same argument gives $r_{cr}=2k/h$.

![[at_w09c_critical_radius.png|760]]

## Related

- Parent lectures: [[SESA3029 W09c - Critical Thickness of Insulation and Fins#1. Critical thickness of insulation|W09c §1]]
- Related concepts: [[Newton's Law of Cooling]] · [[Fin Equation]] · cylindrical conduction resistance in [[SESA3029 W09a - Heat Conduction and Thermal Resistance]]

## Sources

- L5.4 slides 2–5.
