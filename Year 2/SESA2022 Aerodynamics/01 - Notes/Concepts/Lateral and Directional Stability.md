---
title: "Lateral and Directional Stability"
module: "SESA2022 Aerodynamics"
type: concept
stream: "Topic 6: Aircraft Aerodynamics and Static Stability"
aliases: ["directional stability", "lateral stability", "dihedral effect", "weathercock stability", "Dutch roll", "spiral mode"]
tags: [sesa2022, concept, stability]
status: complete
parent_lectures: ["[[SESA2022 T6 - Aircraft Aerodynamics and Static Stability]]"]
related_concepts: ["[[Neutral Point and Static Margin]]"]
sources: ["02 - Sources/Stability/Topic 6 Aircraft aerodynamics and static stability_v2.pdf"]
---

# Lateral and Directional Stability

## Definition

> [!note] Definition
> - **Directional (weathercock) stability**: a sideslip $\beta$ produces a yawing moment that turns the nose back into the wind, $C_{n_\beta}>0$.
> - **Lateral stability (dihedral effect)**: sideslip produces a rolling moment that raises the leading wing, $C_{l_\beta}<0$.

## Explanation

| Effect | Source | Sign |
|---|---|---|
| Vertical fin | side force aft of the CG | stabilising (directional) |
| Fuselage | side force ahead of the CG | destabilising (directional) |
| Dihedral | the leading wing sees a higher $\alpha$ in sideslip | stabilising (lateral) |
| High wing | fuselage cross-flow and side force above the CG | stabilising (lateral) |
| Low wing | the reverse | destabilising (lateral) |
| Sweepback | the leading wing has a larger normal velocity | stabilising (lateral) |

**Coupled motions**:
- **Roll damping**: the down-going wing sees a higher $\alpha$, which opposes the roll.
- **Dutch roll**: an oscillatory yaw–roll coupling. It is worse with strong dihedral effect relative to weathercock stability. Yaw dampers fix it.
- **Spiral mode**: bank leads to sideslip, then yaw into the turn, then more bank. It diverges if directional stability dominates lateral stability.
- **Too much lateral stability** (high wing, sweep and dihedral together) makes roll control sluggish and Dutch roll poor. Hence anhedral on the Harrier and on high-wing swept transports (C-5, An-225).
- **Fin sizing** is set by crosswind landing, **engine-out** rudder authority and Dutch roll damping.

These lateral modes are developed dynamically in [[SESA3047 Advanced Aerospace Mechanics & Control]].

## Examples
- Conceptual questions in the static-stability past papers: [[SESA2022 Static Stability Past Paper Questions Solutions]].

## Related
- Parent lectures: [[SESA2022 T6 - Aircraft Aerodynamics and Static Stability]]
- Related concepts: [[Neutral Point and Static Margin]]

## Sources
- `02 - Sources/Stability/Topic 6 Aircraft aerodynamics and static stability_v2.pdf`
