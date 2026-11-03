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
sources: ["02 - Sources/Stability/Topic 6 Aircraft aerodynamics and static stability_v2.pdf", "02 - Sources/Lectures/SESA2022 Lecture 2025-11-14.txt … 2025-11-25.txt (2025-26 transcripts)"]
---

# Lateral and Directional Stability

**Directional (weathercock) stability** means a sideslip $\beta$ produces a yawing moment that turns the nose back into the wind, $C_{n_\beta}>0$. **Lateral stability**, or the dihedral effect, means sideslip produces a rolling moment that raises the leading wing, $C_{l_\beta}<0$.

| Effect | Source | Sign |
|---|---|---|
| Vertical fin | side force aft of the CG | stabilising (directional) |
| Fuselage | side force ahead of the CG | destabilising (directional) |
| Dihedral | the leading wing sees a higher $\alpha$ in sideslip | stabilising (lateral) |
| High wing | fuselage cross-flow and side force above the CG | stabilising (lateral) |
| Low wing | the reverse | destabilising (lateral) |
| Sweepback | the leading wing has a larger normal velocity | stabilising (lateral) |

The two kinds of stability interact. Rolling is damped because the down-going wing sees a higher $\alpha$, which opposes the roll. Dutch roll is an oscillatory yaw–roll coupling that gets worse when the dihedral effect is strong compared with weathercock stability; yaw dampers fix it. The spiral mode runs the other way: bank leads to sideslip, then yaw into the turn, then more bank, and it diverges if directional stability dominates lateral stability. Too much lateral stability, from a high wing, sweep and dihedral together, makes roll control sluggish and the Dutch roll poor, which is why the Harrier and high-wing swept transports such as the C-5 and An-225 have anhedral. Fin size is set by crosswind landing, rudder authority with an engine out, and Dutch-roll damping.

The lateral modes are developed dynamically in [[SESA3047 Advanced Aerospace Mechanics & Control Hub|SESA3047 Advanced Aerospace Mechanics & Control]]. In SESA2022 they appear as conceptual questions in [[SESA2022 Static Stability Past Paper Questions Solutions]].

## Related

- Full derivation and worked examples: [[SESA2022 T6 - Aircraft Aerodynamics and Static Stability#6. Lateral and directional stability (25 Nov lecture)|T6 §6]]
- [[Neutral Point and Static Margin]]
