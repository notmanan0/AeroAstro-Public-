---
title: "Launch Vehicle Interfaces"
module: "SESA1015 Intro to Aero & Astro"
type: concept
stream: "Astronautics"
aliases: ["Payload Launch Interface", "Payload Fairing", "Dynamic Envelope", "Launcher Selection"]
tags: [sesa1015, concept, astronautics, launch-vehicle]
status: complete
parent_lectures: ["[[SESA1015 A06 - Launch Vehicles, Systems and Interfaces]]"]
related_concepts: ["[[Launch Environment Loads]]", "[[Space Mission Architecture]]", "[[Multistage Rocket Performance]]"]
sources: ["02 - Sources/Astronautics/Astronautics - Part 3 - Launch Vehicles.pdf (pp. 28–29)"]
---

# Launch Vehicle Interfaces

The launch vehicle interfaces are the agreed boundaries between the spacecraft, the launcher and the launch site: what loads, volume, signals, air and heat may cross each one, centred on the payload fairing and the adapter that joins the spacecraft to the upper stage.

The fairing (Part 3, p. 28) encloses the spacecraft through the atmosphere. Its usable diameter is smaller than its outside fairing diameter, and the spacecraft must stay within the dynamic envelope, the space it may occupy including its own vibration under launch loads. The fairing carries air conditioning (clean, cooled, dry air on the pad), access panels for late work on the spacecraft, and the route of the launch-site mechanical and electrical interface; it shields the spacecraft from aeroheating, and electromagnetic interference between launcher, range and spacecraft is kept within limits. The booster adapter at the base carries every load into the upper stage and holds the separation system.

These interfaces are why launcher selection (p. 29) is the main input to spacecraft structural design. It fixes the maximum spacecraft mass for the target orbit, the volume and therefore the stowed configuration of arrays and antennas, the deployment mechanisms that must unfold them, and the mass distribution through a limit on the centre-of-mass height. That limit comes from statics: a lateral acceleration $n_{lat}g$ on a spacecraft of mass $m$ whose centre of mass is $h$ above the separation plane puts a bending moment $m\,n_{lat}\,g\,h$ on the adapter, 44 kN m for 2000 kg at 1.5 m under 1.5 g.

The same spacecraft can be compatible with one launcher and not another even when the mass fits, because the fairing, the adapter or the loads differ. Advertised payloads are also conditional on the orbit: GTO and polar LEO figures are well below LEO figures for every launcher ([[SESA1015 A06 - Launch Vehicles, Systems and Interfaces#Why GTO and polar payloads are smaller|A06]]).

## Related

- Topics: [[SESA1015 A06 - Launch Vehicles, Systems and Interfaces]] · [[SESA1015 A03 - Launch Environment]] · [[SESA2024 01 - Systems Engineering and Spacecraft Design]]
- Concepts: [[Launch Environment Loads]] · [[Space Mission Architecture]] · [[Multistage Rocket Performance]]
- Sources: Astronautics Part 3, pp. 28–29.
