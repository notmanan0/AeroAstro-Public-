---
title: "Rotor Ground Effect"
module: "SESA3043 Advanced Aeronautics"
type: concept
stream: "Chapter 4: Rotor Aerodynamics"
aliases: ["helicopter ground effect", "in ground effect", "out of ground effect", "IGE", "OGE", "wake recirculation", "recirculation", "brownout", "whiteout"]
tags: [sesa3043, concept, rotor, hover, ground-effect]
status: complete
parent_lectures: ["[[SESA3043 4.1 - Rotor in Hover]]"]
related_concepts: ["[[Hover Induced Velocity and Disc Loading]]", "[[Method of Images]]", "[[Lumped Vortex Method]]"]
sources: ["02 - Sources/Lectures/CH4 Rotor Aerodynamics.pdf"]
---

# Rotor Ground Effect

Ground effect is the reduction in induced velocity, and so in induced power for a given thrust, of a rotor hovering close to the ground, which blocks the wake and turns it outwards along the surface.

Out of ground effect the wake contracts and leaves at $v_2=2v_i$, as actuator disc theory assumes. Near the ground the downward flow is stopped and turned into a radial wall jet; the pressure under the rotor rises and the inflow through the disc falls. For the same power the rotor makes more thrust, or for the same thrust it needs less power, which lets a heavily loaded helicopter hover just above the ground when it could not hover higher up. The effect is modelled with an image rotor below the ground plane, the rotor counterpart of the image vortex used for a wing in ground effect ([[Method of Images]], [[SESA3043 2.2 - Lumped Vortex Method|2.2]]). A classical estimate for scale (Cheeseman and Bennett, outside the chapter's formula set) is $T_{IGE}/T_{OGE}=1/\left[1-(R/4z)^2\right]$ at constant power for rotor height $z$, which is 1.07 at $z=R$ and negligible beyond about one diameter.

Two hazards come with it. Near a wall or building the outwash is turned up and back into the rotor, which then hovers in its own downwash (wake recirculation): more power for the same thrust and unsteady loads. Over sand, dust or snow the wall jet lifts loose material that the recirculating flow carries up round the aircraft, and the pilot can lose sight of the ground entirely (brownout, or whiteout over snow).

## Related

- Parent lecture: [[SESA3043 4.1 - Rotor in Hover]]
- Related concepts: [[Hover Induced Velocity and Disc Loading]] · [[Method of Images]] · [[Lumped Vortex Method]]
