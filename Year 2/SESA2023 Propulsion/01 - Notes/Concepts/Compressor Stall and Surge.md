---
title: "Compressor Stall and Surge"
module: "SESA2023 Propulsion"
type: concept
stream: "Section 4: Turbomachinery and Propellers"
aliases: ["rotating stall", "surge", "surge margin", "compressor instability"]
tags: [sesa2023, concept, turbomachinery]
status: complete
parent_lectures: ["[[SESA2023 W08 - Turbomachinery Principles - Euler Equation and Velocity Triangles]]", "[[SESA2023 W09 - Turbomachinery Characteristics - Coefficients, Similarity and Maps]]"]
related_concepts: ["[[Compressor and Turbine Characteristics]]", "[[Velocity Triangles]]", "[[Flow and Work Coefficients]]"]
sources: ["02 - Sources/Lectures/Week 08 - Turbomachinery Principles.pdf", "02 - Sources/Lectures/Week 09 - Turbomachinery Characteristics.pdf"]
---
# Compressor Stall and Surge

## Definition

> [!note] Definition
> - **Stall**: large-scale boundary-layer separation on compressor blades at high positive incidence (low flow or high speed). The pressure rise is lost.
> - **Rotating stall**: stalled cells travel around the annulus.
> - **Surge**: a system-wide instability. The whole compressor flow oscillates violently, and can even reverse.

## Explanation
- **Why compressors are prone**:
  - Turning the flow towards axial diffuses it (an adverse $dp/dx$).
  - The suction-surface boundary layer thickens and separates if the incidence or loading is too high.
  - Turbines, with accelerating flow, are much more robust.
- **Throttling at constant speed** (2021-22 Q4(vi)): restricting the outlet reduces the mass flow and $V_x$, so $\phi$ falls and the incidence rises.
  - At first the pressure ratio *rises* towards the peak of the speed line and the efficiency passes its peak.
  - Then the blades separate: rotating stall, a drop in pressure ratio and efficiency, noise and vibration.
  - Then **surge**: large oscillations of pressure and mass flow, possible flow reversal and flame-out.
- **Mitigation** (2015-16 Q1(iii), 2018-19 Q1(iv)):
  - multi-spool layouts, so each compressor runs near its design speed;
  - **variable inlet guide vanes and stators** to reset incidence at part speed;
  - **handling or bleed valves** to dump flow at start-up;
  - lower stage loading with more stages or blades;
  - casing treatment;
  - an adequate **surge margin** on the working line;
  - careful fuel scheduling during accelerations.

## Related
- [[Compressor and Turbine Characteristics]] · [[Velocity Triangles]] · [[Flow and Work Coefficients]]

## Sources
- Week 8 handout §8.6; Week 9 handout §9.6.1
