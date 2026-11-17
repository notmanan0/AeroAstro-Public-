---
title: "Rotor Working States in Axial Flight"
module: "SESA3043 Advanced Aeronautics"
type: concept
stream: "Chapter 4: Rotor Aerodynamics"
aliases: ["normal working state", "helicopter state", "propeller working state", "turbulent wake state", "low speed descent", "modelled descent", "rotor flow states", "descending flight states"]
tags: [sesa3043, concept, rotor, axial-flight, descent]
status: complete
parent_lectures: ["[[SESA3043 4.2 - Rotor in Axial Flight]]"]
related_concepts: ["[[Vortex Ring State]]", "[[Windmill Brake State]]", "[[Autorotation]]", "[[Induced Velocity in Axial Flight]]"]
sources: ["02 - Sources/Lectures/CH4 Rotor Aerodynamics.pdf"]
---

# Rotor Working States in Axial Flight

The flow patterns a rotor passes through as its axial velocity goes from climb through hover to fast descent, named by the direction of the flow above, through and below the disc.

With $\bar V_C=V_C/v_0$ (negative in descent, $\bar V_C=-\bar V_D$), the states and their approximate ranges, read from averaged test data, are:

| State | Range | Flow |
|---|---|---|
| normal working state | $\bar V_C\geq0$ (hover and climb) | down everywhere; climb momentum theory applies |
| low speed descent | small $\bar V_C<0$ | still down through the disc; tip vortices start to recirculate |
| [[Vortex Ring State\|vortex ring state]] | roughly $-1.5<\bar V_C<0$ | down through the disc, up outside the tips, back in from above; downwash up to about $2.4v_0$ |
| turbulent wake state | roughly $-2<\bar V_C<-1.5$ | net flow up through the disc; turbulent, bluff-plate-like wake above it |
| [[Windmill Brake State\|windmill brake state]] | $\bar V_C\leq-2$ | up everywhere; descent momentum theory applies, power extracted |

Only the first and last have a single streamtube with one flow direction, so only they are described by actuator disc theory. The idealised upward slipstream that the descent equation assumes is the **modelled descent**. In the middle states the rotor's downwash and the upward relative wind are of comparable size and oppose each other, and the downwash and power have to come from measurement: power stays near the hover value over much of the vortex ring range instead of falling, and [[Autorotation|ideal autorotation]] ($\bar V_D\approx1.7$) lies in the turbulent wake state.

## Related

- Parent lecture: [[SESA3043 4.2 - Rotor in Axial Flight]]
- Related concepts: [[Vortex Ring State]] · [[Windmill Brake State]] · [[Autorotation]] · [[Induced Velocity in Axial Flight]]

## Sources

- Sources: CH4 Rotor Aerodynamics, slides 57–66 (from Dr S.J.I. Walker, *Powered Lift*, Ch. 4).
- Notes: written ahead from the slides, 17 Nov 2026.
