---
title: "Reaction Wheels and Momentum Dumping"
module: "SESA2024 Astronautics"
type: concept
stream: "Spacecraft Subsystems"
aliases: ["reaction wheel", "momentum wheel", "wheel desaturation", "momentum dumping", "control moment gyro", "CMG"]
tags: [sesa2024, concept, attitude-control]
status: complete
parent_lectures: ["[[SESA2024 06 - Attitude Control]]"]
related_concepts: ["[[Attitude Sensors and Torquers]]", "[[Momentum Bias and Gyroscopic Rigidity]]", "[[Spacecraft Stabilisation Types]]"]
sources: ["02 - Sources/Lectures/Chapter 6/2025 WEEK 3 Lecture 1 - Chapter 6 - Attitude Control - complete.pdf"]
---

# Reaction Wheels and Momentum Dumping

## Definition

> [!note] Definition
> - A **reaction wheel** is an *internal* torquer. Its motor spins the wheel, and by conservation of $\mathbf H$ the spacecraft counter-rotates: $I_{sc}\omega_{sc} = -I_w\omega_w$.
> - **Momentum dumping** (Europe), or **wheel desaturation** (USA), removes the stored momentum using *external* torquers once the wheel nears its maximum speed.

## Explanation
- **Reaction wheels**: nominally near 0 rpm, used for fine pointing and large slews on 3-axis (zero-bias) spacecraft.
- **Momentum wheels**: nominally about 6500 rpm, used to create bias (hybrid spacecraft).
- **CMGs**: gimballed momentum wheels. Tilting the $\mathbf H$ vector gives large torques (used on ISS-class vehicles).
- **Periodic** momentum (the before and after momenta are equal, for example Earth-pointing in an elliptic orbit) is stored and returned by the wheels **without fuel**. Size the wheel capacity for it.
- **Secular** momentum from external disturbances (aerodynamic, solar pressure, gravity gradient, magnetic) makes the wheel speed creep upward.
- **Dump procedure**:
  1. At the maximum wheel speed, hand pointing control to thrusters or magnetorquers.
  2. Brake the wheel. The internal braking torque would de-point the spacecraft, so the external torquers hold attitude while the wheel slows.
- Only **external** torques can change the total $\mathbf H$, so every spacecraft must carry external torquers.

![[ast_momentum_dumping.png|520]]

## Examples
- Hubble: reaction wheels for slewing; magnetorquers for dumping.
- GEO observatory (workbook Ch6 Q12): 3 orthogonal wheels plus 1 skewed for redundancy. **Magnetorquers** avoid contaminating the optics, but at GEO their effect is weak.
- Exam 2017/18 Q1(iii): "What are internal torquers and how are they used?" (4 marks).

## Related
- [[Attitude Sensors and Torquers]] · [[Momentum Bias and Gyroscopic Rigidity]] · [[Spacecraft Stabilisation Types]]

## Sources
- Chapter 6 lecture slides 41–46; workbook Ch6 Q6, Q8
