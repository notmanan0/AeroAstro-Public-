---
title: "Reaction Wheels and Momentum Dumping"
module: "SESA2024 Astronautics"
type: concept
stream: "Spacecraft Subsystems"
aliases: ["reaction wheel", "momentum wheel", "control moment gyro", "CMG", "wheel desaturation", "momentum dumping", "momentum storage"]
tags: [sesa2024, concept, attitude-control]
status: lectured
parent_lectures: ["[[SESA2024 06 - Attitude Control]]"]
related_concepts: ["[[Attitude Sensors and Torquers]]", "[[Momentum Bias and Gyroscopic Rigidity]]"]
sources: ["02 - Sources/Lectures/SESA2024 Lecture 2025-10-14.txt"]
---

# Reaction Wheels and Momentum Dumping

Reaction wheels, momentum wheels and control moment gyros are internal torquers: flywheels whose motors move angular momentum between the wheel and the spacecraft body without changing the total. Momentum dumping is the use of an external torquer to remove momentum that has built up in them.

A reaction wheel runs at low speed in either direction, nominally near zero, and is used for control: speed it up one way and the body turns the other. A momentum wheel runs fast (about 6500 rpm) in one direction, varied by about ±10 %, to provide bias. A control moment gyro spins at constant speed and is gimballed; tilting it produces large torques through gyroscopic precession, so the ISS uses four of them, but they are heavy and complex.

Wheels can absorb periodic momentum changes indefinitely, without any dumping. An Earth-pointing spacecraft on an elliptical orbit has to turn faster near perigee than near apogee; the wheel absorbs the difference and gives it back each orbit. Secular changes are different. A disturbance torque that acts the same way every orbit, such as drag on a deployed array, makes the wheel spin a little faster each time until it saturates. Before then, an external torquer (thrusters, magnetorquers or trim tabs) holds the attitude while the wheel is slowed down. Europe calls this momentum dumping; the USA calls it wheel desaturation. Wheels cannot dump momentum on their own, because they are internal.

![[ast_wheel_momentum_elliptic.png|600]]

## Related

- [[SESA2024 06 - Attitude Control#6. Momentum storage and dumping|Momentum storage in the lecture note]] · [[SESA2024 06 - Attitude Control#Internal disturbances and torquers|Wheel types]]
- [[Attitude Sensors and Torquers]] · [[Momentum Bias and Gyroscopic Rigidity]]
