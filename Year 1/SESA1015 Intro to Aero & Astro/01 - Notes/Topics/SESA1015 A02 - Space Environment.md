---
title: "SESA1015 A02 - Space Environment"
module: "SESA1015 Intro to Aero & Astro"
type: topic
stream: "Astronautics"
order: 14
tags: [sesa1015, space-environment, radiation, debris, vacuum]
aliases: ["SESA1015 Astronautics 2", "Space Environment"]
date: 2026-09-27
status: complete
parent: ["[[SESA1015 Intro to Aero & Astro Hub]]"]
prerequisites: ["[[SESA1015 A01 - Astronautics Foundations, Missions and Applications]]"]
next_topics: ["[[SESA1015 A03 - Launch Environment]]"]
key_concepts: ["[[Space Environment Hazards]]"]
tutorial_sheets: []
sources: ["02 - Sources/Astronautics/Astronautics - Part 2 - Environment.pdf"]
---

# SESA1015 A02 - Space Environment

> [!abstract] Summary
> “Space” is not an empty, uniform environment. A spacecraft experiences solar radiation, thermal cycling, vacuum, charged particles, ionising radiation, atomic oxygen, plasma, micrometeoroids and human-made debris. Which hazard dominates depends on orbit, shielding, attitude, duration and solar activity. Environmental engineering maps each external cause to a material, electronic, thermal, charging or mechanical effect and then to a design/verification response.

## 1. Hazard map

![[astro_space_environment.png|760]]

The diagram is a guide, not a hard boundary map. Radiation belts vary, the exosphere has no sharp edge, and the debris population changes with altitude, inclination and time.

## 2. Solar inputs

At Earth distance, the Sun supplies electromagnetic radiation and a stream of charged particles.

- Solar flux drives spacecraft temperature and solar-array output.
- Ultraviolet radiation degrades polymers, coatings and optical properties.
- Solar energetic particle events can produce intense short-duration radiation.
- Solar activity changes the upper atmosphere, increasing density and drag in low orbit.

The absorbed solar power of a surface facing the Sun is approximated by

$$P_{abs}=\alpha_sGA\cos\theta$$

where $G$ is solar irradiance and $\alpha_s$ absorptance.

## 3. Thermal environment

In vacuum, external convection is absent. Heat transfer is dominated by:

- radiation to/from the environment;
- conduction through the structure;
- internal dissipation.

Radiated power is

$$P_{rad}=\epsilon\sigma A(T^4-T_{sur}^4).$$

Orbit and attitude create repeated sunlight/eclipse cycles. Temperature gradients cause distortion; cycles cause fatigue; unsuitable temperatures damage batteries, electronics, propellants and optics.

## 4. Vacuum effects

Vacuum can cause:

- material outgassing and optical contamination;
- lubricant evaporation or cold welding;
- pressure differential across sealed volumes;
- altered heat transfer;
- electrical arcing at high voltage.

Materials are selected and baked/tested for vacuum compatibility. A material acceptable in terrestrial equipment may contaminate a sensitive space instrument.

## 5. Radiation

Sources include trapped belt particles, solar particles and galactic cosmic rays. Effects split into:

- **total ionising dose (TID):** accumulated degradation;
- **displacement damage:** lattice damage, important in detectors/solar cells;
- **single-event effects (SEE):** one particle causes upset, latch-up, burnout or transient.

Shielding reduces many particle fluxes but adds mass and can create secondary radiation. Design also uses radiation-tolerant parts, error correction, redundancy, current limiting and operational safe modes.

## 6. Plasma and charging

Charged particles and sunlight can drive spacecraft surfaces to different potentials. Differential charging may discharge and upset or damage electronics. Geometry, conductive coatings, grounding/bonding and material choice control charge paths.

## 7. Atomic oxygen

In low Earth orbit, energetic atomic oxygen attacks exposed polymers and surface coatings. It can erode material and change thermal/optical properties. Protective coatings work only while continuous; pinholes and cracks matter.

## 8. Micrometeoroids and orbital debris

Even small particles carry high kinetic energy because relative speeds are kilometres per second:

$$KE=\frac12mv^2.$$

The response may include shielding, redundancy, orientation, avoidance manoeuvres and acceptance of risk. Trackable objects support conjunction assessment; smaller debris must be handled statistically and structurally.

## 9. Environmental design matrix

| Cause | System effect | Typical mitigation/test |
|---|---|---|
| thermal cycling | fatigue, distortion | thermal-vacuum cycling |
| ionising radiation | parameter drift, failure | shielding, part selection, TID test |
| SEE | upset/latch-up | EDAC, watchdogs, current limiting |
| atomic oxygen | erosion | protective coating/material choice |
| vacuum | outgassing, lubrication failure | vacuum-compatible materials, bake-out |
| debris/MMOD | puncture, impact damage | shields, avoidance, redundancy |
| plasma | charging/arcing | bonding, conductive surfaces, analysis |

## 10. Environment-to-design workflow

1. Define orbit/trajectory, duration and attitude modes.
2. Select environmental models and confidence levels.
3. Convert environment into component-level loads/doses.
4. Apply shielding, layout, materials and operational mitigations.
5. Test representative hardware and workmanship.
6. Track margin as the mission and design change.

> [!failure] Common errors
> - Treating every orbit as the same environment.
> - Using average solar/radiation conditions for a peak survival requirement.
> - Assuming “more shielding” is always beneficial.
> - Treating thermal analysis as only a hot-case problem.

## Year 2 bridge

- [[SESA2024 08 - Electrical Power Subsystem]] uses illumination and radiation to size generation/storage.
- [[SESA2024 10 - Thermal Control]] turns radiative balance into hardware sizing.
- [[SESA2024 14 - Orbit Control, Drag and Payload Data Rate]] connects upper-atmosphere density to orbit decay.
- [[SESA2024 15 - Space Sustainability, Debris and NewSpace]] treats debris risk and mitigation systematically.

