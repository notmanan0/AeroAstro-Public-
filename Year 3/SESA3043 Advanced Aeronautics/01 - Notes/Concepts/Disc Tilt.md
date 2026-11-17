---
title: "Disc Tilt"
module: "SESA3043 Advanced Aeronautics"
type: concept
stream: "Chapter 4: Rotor Aerodynamics"
aliases: ["rotor disc tilt", "tip-path-plane angle", "rotor co-ordinate system", "flow velocity parallel to disc plane", "flow velocity perpendicular to disc plane", "overall inflow velocity"]
tags: [sesa3043, concept, rotor, forward-flight]
status: complete
parent_lectures: ["[[SESA3043 4.3 - Rotor in Forward Flight]]"]
related_concepts: ["[[Induced Velocity in Forward Flight]]", "[[Rotor Power Consumption]]"]
sources: ["02 - Sources/Lectures/CH4 Rotor Aerodynamics.pdf"]
---

# Disc Tilt

The disc tilt $\gamma$ is the angle by which a rotor disc is tilted forward from the horizontal in forward flight, which is also the angle of the thrust from the vertical.

The axes are attached to the disc: $x$ forward in the disc plane, $y$ sideways in it, $z$ normal to it. The flight speed $V$ splits into the flow velocity parallel to the disc plane, $V_x=V\cos\gamma$, and the flow velocity perpendicular to it, $V_z=V\sin\gamma$, which passes down through a forward-tilted disc in the same direction as the induced velocity. At the disc the overall inflow velocity is $V'=\sqrt{V_x^2+(V_z+v_i)^2}$.

In steady level flight, with the thrust normal to the disc and the fuselage drag horizontal,

$$
T\sin\gamma=D,\qquad T\cos\gamma=W\qquad\Longrightarrow\qquad \tan\gamma=\frac DW,\quad T=\sqrt{W^2+D^2}.
$$

Multiplying $T\sin\gamma=D$ by $V$ shows that $TV_z=DV$: the power the rotor spends pushing $V_z$ through the disc is the parasite power. For the Lynx at 60 m/s with an assumed $f=1.5$ m², $D=3309$ N, $\gamma=3.62^\circ$ and $T=52\,392$ N, only 0.2 % above the weight. The tilt is set with cyclic pitch.

## Related

- Parent lecture: [[SESA3043 4.3 - Rotor in Forward Flight]]
- Related concepts: [[Induced Velocity in Forward Flight]] · [[Rotor Power Consumption]]

## Sources

- Sources: CH4 Rotor Aerodynamics, slides 72–77, 81–82, 88, 90.
- Notes: written ahead from the slides, 17 Nov 2026.
