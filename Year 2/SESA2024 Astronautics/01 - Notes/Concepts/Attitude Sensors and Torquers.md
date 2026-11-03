---
title: "Attitude Sensors and Torquers"
module: "SESA2024 Astronautics"
type: concept
stream: "Spacecraft Subsystems"
aliases: ["star tracker", "Sun sensor", "Earth sensor", "magnetometer", "gyroscope", "magnetorquer", "thrusters for attitude control", "disturbance torques", "gravity gradient"]
tags: [sesa2024, concept, attitude-control]
status: lectured
parent_lectures: ["[[SESA2024 06 - Attitude Control]]"]
related_concepts: ["[[Reaction Wheels and Momentum Dumping]]", "[[Spacecraft Stabilisation Types]]"]
sources: ["02 - Sources/Lectures/SESA2024 Lecture 2025-10-09.txt", "02 - Sources/Lectures/SESA2024 Lecture 2025-10-14.txt", "02 - Sources/Lectures/SESA2024 Lecture 2025-10-16.txt"]
---

# Attitude Sensors and Torquers

The ACS measures attitude with reference and inertial sensors and corrects it with torquers, against a background of disturbance torques; torques and torquers are classed as external, which change the spacecraft's total angular momentum, or internal, which only move it around.

The external disturbances are aerodynamic drag (below about 500 km), gravity gradient and magnetic torques (up to about 30 000–40 000 km), solar radiation pressure (all altitudes, about $5\times10^{-6}\ \mathrm{N/m^2}$) and thrust misalignment (1 kN offset 1 mm gives 1 N m). Gravity gradient pulls a long, thin body towards the local vertical and can be used for passive stabilisation. The external torquers are thrusters (any torque, but propellant-limited; twelve to sixteen for pure couples about three axes), magnetorquers (no propellant or moving parts, but slow, small, needing a field model, and with no torque about the field line) and adjustable geometry such as solar trim tabs. Every spacecraft needs at least one, because only an external torque can remove accumulated momentum. Internal disturbances are mechanisms, propellant slosh and crew movement; the internal torquers are wheels and control moment gyros.

Attitude can only be controlled as accurately as it is measured. Reference sensors give the direction to an object in body axes, with accuracy set by the object: star trackers to arcseconds, Sun and Earth-horizon sensors to arcminutes, magnetometers to around a degree. Inertial sensors such as gyroscopes measure changes in attitude, keep working when the reference is hidden, but drift and need recalibrating. Spacecraft carry both.

## Related

- [[SESA2024 06 - Attitude Control#5. Torques and torquers|Torques and torquers in the lecture note]] · [[SESA2024 06 - Attitude Control#7. Attitude sensors|Sensors]]
- [[Reaction Wheels and Momentum Dumping]] · [[Spacecraft Stabilisation Types]]
