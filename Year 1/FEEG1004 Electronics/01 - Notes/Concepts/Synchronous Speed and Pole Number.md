---
title: "Synchronous Speed and Pole Number"
module: "FEEG1004 Electronics"
type: concept
stream: "Part C: Electric Machines"
aliases: ["synchronous speed", "rpm = 120 f / Np", "number of poles", "electrical frequency"]
tags: [feeg1004, concept, machines, ac]
status: complete
parent_lectures: ["[[FEEG1004 C2 - AC Synchronous Generators and Three-Phase Systems]]"]
related_concepts: ["[[Motional EMF in Electric Machines]]", "[[Three-Phase Star and Delta Connections]]"]
sources: ["02 - Sources/S2 Machines/S2 Electric Machines Notes - Sharkh.pdf", "Sharkh notes §3.1", "02 - Sources/S2 Machines/S2-W18-21 Electric Machines 02 - AC Synchronous Generators - Lecture Slides.pdf", "02 - Sources/S2 Machines/S2-W18-21 Electric Machines 03 - Turbo Generators EMF - Lecture Slides.pdf"]
---

# Synchronous Speed and Pole Number

The synchronous speed of an AC machine is the shaft speed at which a rotor with $N_p$ poles generates, or follows, a supply of frequency $f$. Each pole **pair** passing a coil gives one electrical cycle, so

$$
f = \frac{N_p}{2}\cdot\frac{\mathrm{rpm}}{60}\qquad\Longleftrightarrow\qquad \mathrm{rpm} = \frac{120f}{N_p}
$$

A 2-pole machine gives one electrical cycle per revolution, and in general the electrical angle is $N_p/2$ times the mechanical angle. More poles therefore mean a lower speed for the same frequency. On a 50 Hz grid a 2-pole machine runs at 3000 rpm and an 80-pole machine at 75 rpm.

The pole number is chosen to suit the prime mover. Steam and gas turbines run fast and use 2 or 4 poles, while slow prime movers such as hydro, tidal and wind turbines need many poles or a gearbox. In Tutorial 5 Q4 a 24-pole generator at 150 rpm gives 30 Hz.

![[ee_c2_poles_speed.png|640]]

## Related

- [[FEEG1004 C2 - AC Synchronous Generators and Three-Phase Systems]]
- [[Motional EMF in Electric Machines]] · [[Three-Phase Star and Delta Connections]]
- Sources: Sharkh notes §3.1; Machines 02–03 slides
