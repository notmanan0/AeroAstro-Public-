---
title: "Agile Aerospace"
module: "SESA2024 Astronautics"
type: concept
stream: "Systems"
aliases: ["agile spacecraft development", "iterative design", "NewSpace development"]
tags: [sesa2024, concept, systems-engineering, newspace]
status: lectured
parent_lectures: ["[[SESA2024 01 - Systems Engineering and Spacecraft Design]]", "[[SESA2024 15 - Space Sustainability, Debris and NewSpace]]"]
related_concepts: ["[[Systems Engineering Design Phases]]"]
sources: ["02 - Sources/Lectures/SESA2024 Lecture Dr Deshpande Lecture - Planet Labs.txt"]
---

# Agile Aerospace

Agile aerospace is an iterative way of developing spacecraft, borrowed from software engineering: build a working system as early as possible, fly it, and improve it in frequent design revisions instead of fixing every requirement up front.

The guest lecture from Planet Labs contrasts it with the traditional waterfall process. The waterfall builds the wheels, then the axle and chassis, and only at the end has a car that moves. The agile route builds a skateboard first, because it already gets from A to B, then adds handlebars, pedals and an engine. Planet redesigned its 3U Dove satellite about fifteen times in seven years, using consumer batteries and electronics, and its downlink rate rose by a factor of about 10 000 over that period. Failures cost little because the mission is a constellation of many cheap satellites: three launch failures did not threaten it.

The method rests on an explicit objective function (pixels down per dollar for Planet), hard constraints that force decisions (the 3U form factor), requirements graded by criticality and confidence, and milestones defined by working hardware rather than by PDR and CDR documents. Its costs are unpredictable schedules, the need for strict configuration control and margin, and customers who may not like the uncertainty.

It suits missions where many cheap units and fast iteration are possible. It does not suit one-off flagship missions; the speaker's example is that the James Webb Space Telescope could not have been built this way, which is why the ECSS phased process remains the default.

## Related

- [[SESA2024 01 - Systems Engineering and Spacecraft Design#8. A different route: agile aerospace (Planet)|Planet guest lecture in the topic note]]
- [[Systems Engineering Design Phases]]
