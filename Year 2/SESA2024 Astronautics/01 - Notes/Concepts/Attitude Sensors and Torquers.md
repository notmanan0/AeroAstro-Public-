---
title: "Attitude Sensors and Torquers"
module: "SESA2024 Astronautics"
type: concept
stream: "Spacecraft Subsystems"
aliases: ["attitude sensors", "external torques", "internal torques", "disturbance torques", "magnetorquer", "star tracker", "Sun sensor", "gyroscope"]
tags: [sesa2024, concept, attitude-control]
status: complete
parent_lectures: ["[[SESA2024 06 - Attitude Control]]"]
related_concepts: ["[[Reaction Wheels and Momentum Dumping]]", "[[Spacecraft Stabilisation Types]]"]
sources: ["02 - Sources/Lectures/Chapter 6/2025 WEEK 3 Lecture 1 - Chapter 6 - Attitude Control - complete.pdf", "02 - Sources/Lectures/Chapter 6/2025 Lecture 2 - Chapter 6 - Attitude Control - complete.pdf"]
---

# Attitude Sensors and Torquers

## Definition

> [!note] Definition
> - **External torques** come from interaction with the environment and **change** the total $\mathbf H$.
> - **Internal torques** act between parts of the spacecraft and **conserve** $\mathbf H$.
> - **Sensors** come in two categories: **reference** sensors (attitude relative to an external source) and **inertial** sensors (changes in attitude).

## Explanation
**External disturbances** (altitude ranges are approximate):

| Disturbance | Where it matters |
|---|---|
| Aerodynamic | < 500 km |
| Gravity gradient | < 30 000–40 000 km |
| Magnetic | < 30 000–40 000 km |
| Solar radiation pressure | all altitudes |
| Thrust misalignment | all altitudes |

**Controllable external torquers**:
- **Thrusters (gas jets)**: any torque size; on/off; need propellant; plumes can contaminate.
- **Magnetorquers**: $\mathbf T = \mathbf m\times\mathbf B$. Need power and an on-board field model. **No torque about the field line.** Weak at high altitude.
- Adjustable geometry (trim tabs, flaps) using aerodynamic or solar pressure: low torque, no propellant.

**Internal disturbances**: mechanisms (array deployment), fuel slosh, astronaut motion.

**Controllable internal torquers**: dual-spin mechanisms; reaction wheels; momentum wheels; CMGs.

**Sensors**:
- **Reference**:
  - Sun sensors (coarse, safe mode);
  - Earth (horizon) sensors;
  - **star sensors or trackers** (arcsecond);
  - magnetometers.
- **Inertial**: gyroscopes and accelerometers. They drift, so they are recalibrated from reference sensors.

## Examples
- Why must external torquers be carried? Disturbances accumulate momentum, and only an external torque can remove it (2016/17 Q1(iii)).
- Seasat was the lecture's example of an aerodynamic-torque-sensitive LEO spacecraft.
- A GEO telescope (1 arcsec) needs star sensors (guide telescopes), gyros for slewing, and Sun sensors for array pointing and safe mode.

## Related
- [[Reaction Wheels and Momentum Dumping]] · [[Spacecraft Stabilisation Types]]

## Sources
- Chapter 6 lecture slides 37–47
