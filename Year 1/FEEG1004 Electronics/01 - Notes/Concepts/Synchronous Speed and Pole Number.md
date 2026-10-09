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
sources: ["02 - Sources/S2 Machines/S2 Electric Machines Notes - Sharkh.pdf"]
---

# Synchronous Speed and Pole Number

## Definition

> [!note] Definition
> $$f = \frac{N_p}{2}\cdot\frac{\mathrm{rpm}}{60}\qquad\Longleftrightarrow\qquad \mathrm{rpm} = \frac{120f}{N_p}$$
> Each pole **pair** passing a coil gives one electrical cycle.

## Explanation
- A 2-pole machine gives one cycle per revolution. More poles give lower speed for the same frequency.
- Electrical angle = $(N_p/2)$ × mechanical angle.
- Slow prime movers (hydro, tidal, wind) need many poles or a gearbox. Steam and gas turbines use 2 or 4 poles.

![[ee_c2_poles_speed.png|640]]

## Examples
- 50 Hz: 2 poles run at 3000 rpm and 80 poles at 75 rpm.
- Tutorial 5 Q4: 24 poles at 150 rpm give 30 Hz.

## Related
- Topic notes: [[FEEG1004 C2 - AC Synchronous Generators and Three-Phase Systems]]
- Concepts: [[Motional EMF in Electric Machines]]

## Sources
- Sharkh notes §3.1; Machines 02–03 slides
