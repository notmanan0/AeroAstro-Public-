---
title: "SESA2024 Workbook Ch6 - Attitude Control Solutions"
module: "SESA2024 Astronautics"
type: tutorial
stream: "Spacecraft Subsystems"
tags:
  - sesa2024
  - tutorial-solutions
  - attitude-control
sheet: "Problem Sheet Workbook 2025-26, Chapter 6 (pp. 7-18)"
theory_notes: ["[[SESA2024 06 - Attitude Control]]"]
key_concepts: ["[[Inertia Matrix]]", "[[Momentum Bias and Gyroscopic Rigidity]]", "[[Spacecraft Stabilisation Types]]", "[[Reaction Wheels and Momentum Dumping]]", "[[Attitude Sensors and Torquers]]"]
status: complete
sources: ["02 - Sources/Lectures/SESA2024 Astronautics PROBLEM SHEET WORKBOOK 2025-26 V1.1.pdf"]
---

# SESA2024 Workbook Ch6 - Attitude Control Solutions

> [!abstract] Sheet Info
> Twelve descriptive questions. Q1–11 test the vocabulary of attitude control. Q12 is a design synthesis for a GEO telescope, and it is the model for exam questions that begin "by a qualitative analysis…". The answers below follow the workbook's model solutions and add exam phrasing.

## Theory Links
- [[SESA2024 06 - Attitude Control]]
- Concepts: [[Inertia Matrix]] · [[Momentum Bias and Gyroscopic Rigidity]] · [[Spacecraft Stabilisation Types]] · [[Reaction Wheels and Momentum Dumping]] · [[Attitude Sensors and Torquers]]

---

## Q1: Primary functions of the ACS
1. **Payload pointing**: meet the payload's pointing requirement in accuracy, stability and slew rate (Earth-pointing for comms and remote sensing; arbitrary directions for an observatory).
2. **House-keeping pointing** in every mission phase:
   - arrays to the Sun (power);
   - antennas to the ground station (commands, telemetry, payload data);
   - radiators to deep space (thermal);
   - thrust vector correctly aligned for orbit manoeuvres.
3. **Momentum management**: control the total angular momentum $\mathbf H$ of the spacecraft.

The ACS design requirements are derived from a functional analysis of these activities. In one line: *the ACS manages the rotation (angular momentum) of the spacecraft.*

## Q2: Closed-loop ACS operation (sketch)
Sensors → on-board processor (compares the measured attitude with the demanded attitude) → control law → actuators (torquers) → spacecraft dynamics → back to the sensors.

- The key word is **closed-loop and autonomous**. The loop runs on board without the ground.
- The block diagram is the same as a SESA2027 feedback loop: the plant is $\mathbf T = d(\mathbf I\boldsymbol\omega)/dt$, the sensors are the feedback path, and the torquers are the actuator.
- The ACS relies on services from other subsystems: power, propulsion (thrusters), OBDH (processing) and communications (ground commands).

## Q3: The inertia matrix
**Diagonal terms (moments of inertia)**:

$$I_{xx}=\sum_i m_iR_i^2=\sum_i m_i(y_i^2+z_i^2)=\int_M(y^2+z^2)\,dm$$

They are always positive and measure resistance to angular acceleration. A tennis ball stops easily; a steam-engine flywheel does not.

**Off-diagonal terms (products of inertia)**:

$$I_{xy}=\sum_i m_ix_iy_i=\int_M xy\,dm$$

They measure **unbalance**:
- A symmetric cylinder spinning about $y$ has $I_{xy}=0$, because every element at $(x_i,y_i)$ is cancelled by one at $(-x_i,y_i)$. The rotation is well balanced.
- Adding an asymmetric mass gives $I_{xy}\neq0$ and an unbalanced rotation with **cross-coupling** between axes.

**Why it matters**: it appears in Newton's second law for rotation,

$$\frac{d}{dt}\mathbf H=\frac{d}{dt}([\mathbf I]\boldsymbol\omega)=\mathbf T$$

so the vehicle's response to any control torque is an explicit function of $[\mathbf I]$. You cannot size torquers without it.

## Q4: The four generic stabilisation types
See [[Spacecraft Stabilisation Types]] (lecture slides 21–35).

| Type | Bias? | Mechanism | Examples |
|---|---|---|---|
| 1 Spinner | Yes (large $I\omega$) | whole body spins at 10–60 rpm | Intelsat 1, Meteosat SG, Cluster, small sats |
| 2 Dual-spinner | Yes | spinning rotor plus despun platform | Giotto, Intelsat 2–4 and 6, Galileo |
| 3 Hybrid | Yes (small $I$, large $\omega$) | 3-axis body plus a momentum wheel at about 6500 rpm | Navstar GPS 2R, Eurostar 3000, many comsats |
| 4 3-axis stabilised | No (zero bias) | reaction wheels near zero speed, thrusters | Hubble, JWST, SPOT 5, Magellan, Envisat |

## Q5: External vs internal torques
- **External**: from interaction with the outside world. Examples: an asymmetric area in the airflow gives an aerodynamic torque; a pair of opposed thrusters fires (propellant leaves the system). They **change the total $\mathbf H$** and are the terms on the **RHS** of $d\mathbf H/dt=\sum\mathbf T_{ext}$.
- **Internal**: between two parts of the spacecraft. Example: a reaction-wheel motor torques the wheel, and the wheel reacts equally and oppositely on the motor. **Total $\mathbf H$ is conserved**, and momentum is only redistributed.

## Q6: How a reaction wheel works; momentum dumping
- **Wheel operation**: start with the spacecraft and wheel at rest, so $H=0$. The motor applies an internal torque and the wheel spins up. Total $H$ must stay zero, so the spacecraft counter-rotates, which is how it slews. Stopping the wheel stops the spacecraft. $H=0$ throughout. Example: the **Hubble Space Telescope**.
- **Dumping**: external disturbance torques (aerodynamic, solar pressure, gravity gradient) feed angular momentum into the spacecraft.
  - To hold attitude, the wheel speeds up, absorbing that momentum.
  - Eventually the wheel reaches its **maximum speed (about 6500 rpm)** and cannot absorb any more.
  - Braking the wheel alone would de-point the spacecraft. So control passes to **external torquers** (thrusters, magnetorquers), which hold attitude while the wheel is slowed.
  - This is **momentum dumping** (Europe) or **wheel desaturation** (USA). It is needed because only external torques can remove momentum from the system.

![[ast_momentum_dumping.png|600]]

## Q7: System impacts of Types 1 and 2, and how Types 3 and 4 relieve them
- **Types 1 and 2** are usually cylinders with **body-mounted cells** on the curved surface, sized to fit an aerodynamic launcher fairing. So they are **power-limited**, because only part of the cylinder faces the Sun.
- Other impacts:
  - thermal design complexity;
  - mounting of comms and payload (limited space for non-scanning payloads);
  - mass distribution (balance);
  - for Type 2, the reliability of the despin bearing and the power transfer across it.
- **Types 3 and 4** can deploy large Sun-tracking arrays and give a stable platform for payload mounting.

## Q8: Why wheels are still used on "zero-bias" 3-axis spacecraft
- A 3-axis spacecraft has no significant net $\mathbf H$. Reaction wheels **operate near zero speed nominally**, so they add no significant bias. They only store transient momentum.
- **Momentum wheels** run at about 6500 rpm and are designed to create bias. They are therefore **not** used on Type 4 spacecraft.

## Q9: Passive vs active stabilisation
- **Passive**: little or no ACS effort needed to hold pointing. Examples: gravity-gradient booms, magnetic stabilisation, and spin (gyroscopic rigidity keeps the spin axis inertially fixed).
- **Active**: continuous ACS input. The best example is a 3-axis stabilised spacecraft, which has no inherent stability.

## Q10: Mass distribution for gravity-gradient stabilisation
- It should be **long and thin** (for example a boom with a tip mass).
- Aligned near the local vertical, the inverse-square difference in gravity across the long dimension is maximised, which maximises the restoring gravity-gradient torque.

## Q11: Ideal inertia matrix for a pure spinner (spin axis $z$)

$$[\mathbf I]=\begin{bmatrix}I_{xx}&0&0\\0&I_{xx}&0\\0&0&I_{zz}\end{bmatrix},\qquad I_{zz}>I_{xx}$$

- **Zero products of inertia**: the spin axis is a principal axis, so its direction is constant.
- **$I_{zz}$ maximum**: spin about the axis of maximum inertia for long-term stability. Spin about the minimum axis is acceptable only for short periods.
- **Equal transverse inertias**: gives constant precession in response to a torque.

This is exactly the logic of 2024/25 exam **A4**: the given $[\mathbf I]$ has large products of inertia, so it is not a spinner. The answer is **3-axis stabilised**.

## Q12: GEO astronomical observatory (1 arcsec for up to 1 h)
**(i) Implications of the ~60 rpm rotation phase during transfer**:
- Mechanisms must stow and then deploy the arrays, aperture cover and antenna.
- The mass distribution must be engineered to the spinner form in Q11, with $z$ as the spin axis.
- The nutation mode must be managed (damped).

**(ii) Mission-orbit stabilisation**: **3-axis stabilised, zero bias**.
- The telescope must point anywhere on the celestial sphere (except Sun-exclusion zones).
- The ACS is therefore "busy", and no body axis stays invariantly pointing. A biased system would resist every repoint.

**(iii) Internal torquers**: **reaction wheels**, three on orthogonal body axes plus a fourth on a skewed axis for redundancy. There are no momentum wheels, because they would add bias.

**(iv) External torquers**: their main job is **momentum dumping** from the reaction wheels.
- Hydrazine thrusters are possible, but the plume could contaminate the optics, so their placement is critical.
- **Magnetorquers** are more likely, because they are "clean". (At GEO the geomagnetic field is weak, so this needs checking. The lecture notes that magnetic torques fade beyond about 30 000–40 000 km.)

**(v) Sensors**:
- **Star sensors** are mandatory for arcsecond pointing, probably as purpose-built guide telescopes.
- **Gyros** are needed for the busy slewing activity.
- **Sun sensors** are needed for array pointing, Sun avoidance and recovery from ACS emergencies.

## Sources
- Workbook 2025-26 Chapter 6 questions (p. 7–8) and model solutions (p. 13–18)
- Chapter 6 lecture slides (Sykulska-Lawrence), Fortescue, Stark & Swinerd, Ch. 9
