---
title: "Streamline, Pathline and Streakline"
module: "SESA1016 Thermofluids"
type: concept
stream: "Flow Kinematics"
aliases: ["streamline", "pathline", "streakline"]
tags: [sesa1016, concept, visualisation]
status: complete
parent_lectures: ["[[SESA1016 T9 - Describing Flow and the Material Derivative]]"]
related_concepts: ["[[Material Derivative]]"]
sources: ["02 - Sources/Lectures/Chapter 9.pdf"]
---

# Streamline, Pathline and Streakline

A streamline is a curve everywhere tangent to the velocity field at one instant; a pathline is the trajectory of one fluid particle over time; a streakline is the locus, at one instant, of all particles that have passed through a fixed point, such as dye injected continuously from a nozzle.

Streamlines are found from the velocity field at a fixed time by requiring the curve's slope to equal the velocity direction, $dy/dx=v/u$. No flow crosses a streamline, so a bundle of streamlines forms a streamtube that behaves like a duct with impermeable walls. Pathlines are found by integrating the particle's motion, $dx/dt=u$, $dy/dt=v$, from its starting point, and are what a long-exposure photograph of a tracer particle shows. Streaklines are what smoke and dye visualisations show.

In steady flow the three coincide: the velocity field does not change, so a particle moves along the streamline it starts on, and every later particle from the same point follows the same path. In unsteady flow they differ, and a dye streak can look nothing like the instantaneous streamlines. A flow can be steady in one frame and unsteady in another, so the lines also depend on the observer; the flow round a moving car is steady to the driver and unsteady to someone at the roadside.

![[tf_path_streak_lines.png|760]]

## Related

- [[SESA1016 T9 - Describing Flow and the Material Derivative#4. Lines that visualise a flow|T9 §4]] · [[SESA1016 T9 - Describing Flow and the Material Derivative#When the lines coincide|when they coincide]] · [[SESA1016 T9 - Describing Flow and the Material Derivative#Streamtubes|streamtubes]] · [[SESA1016 T9 - Describing Flow and the Material Derivative#Worked example - streamlines near a corner|corner-flow example]]
- [[Material Derivative]]
