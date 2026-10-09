---
title: "SESA2024 06 - Attitude Control"
module: "SESA2024 Astronautics"
type: topic
stream: "Spacecraft Subsystems"
order: 6
tags:
  - sesa2024
  - attitude-control
  - acs
aliases: ["ACS", "Chapter 6", "Attitude Control Subsystem"]
date: 2026-09-25
status: complete
parent: ["[[SESA2024 Astronautics Hub]]"]
prerequisites: ["[[SESA2024 01 - Systems Engineering and Spacecraft Design]]"]
next_topics: ["[[SESA2024 07 - Spacecraft Propulsion]]"]
key_concepts: ["[[Inertia Matrix]]", "[[Momentum Bias and Gyroscopic Rigidity]]", "[[Spacecraft Stabilisation Types]]", "[[Reaction Wheels and Momentum Dumping]]", "[[Attitude Sensors and Torquers]]"]
tutorial_sheets: ["[[SESA2024 Workbook Ch6 - Attitude Control Solutions]]"]
sources: ["02 - Sources/Lectures/Chapter 6/Chapter 6 - Attitude Control - prerecorded material.pdf", "02 - Sources/Lectures/Chapter 6/2025 Lecture 1 - Chapter 6 - Attitude Control - complete.pdf", "02 - Sources/Lectures/Chapter 6/2025 Lecture 2 - Chapter 6 - Attitude Control - complete.pdf", "02 - Sources/Lectures/Chapter 6/2025 WEEK 3 Lecture 1 - Chapter 6 - Attitude Control - complete.pdf"]
---

# SESA2024 06 - Attitude Control

> [!abstract] Summary
> The ACS points the payload and the housekeeping hardware (arrays, antennas, radiators, thrusters) by **managing the spacecraft's angular momentum** $\mathbf H = [\mathbf I]\boldsymbol\omega$.
> - External torques change $\mathbf H$; internal torques only move it between parts of the spacecraft.
> - **Momentum bias** (a large stored $\mathbf H$) gives gyroscopic rigidity. A torque $T$ only precesses the bias at $\dot\psi = T/H_0$. This leads to four stabilisation types: spinner, dual-spinner, hybrid, 3-axis.
> - Reaction wheels give fine 3-axis control but saturate, so external torquers (thrusters, magnetorquers) must dump momentum.

## Key Concepts
- [[Inertia Matrix]] · [[Momentum Bias and Gyroscopic Rigidity]] · [[Spacecraft Stabilisation Types]] · [[Reaction Wheels and Momentum Dumping]] · [[Attitude Sensors and Torquers]]

---

## 1. Purposes of the ACS
1. Meet the **payload** pointing requirements (direction, accuracy, stability, slew rate). Earth-pointing for comms and remote sensing; diverse directions for observatories.
2. Meet **housekeeping** pointing in all mission phases:
   - power raising → Sun-pointing;
   - communications → Earth-pointing;
   - thermal dissipation → radiators to deep space;
   - thrust-vector direction for engine burns.
3. **Manage the overall angular momentum** of the spacecraft.

**Closed-loop operation**: attitude sensors → on-board processor (compares the measurement with the demand, applies the control law) → torquers → spacecraft dynamics (rotation about the **centre of mass** under torques about the CM). The ACS needs services from power, propulsion, OBDH and comms.

## 2. Rotational dynamics
The translational analogue: $\mathbf L = M\mathbf V$, and $d\mathbf L/dt = \sum\mathbf F_{ext}$. With no force, $\mathbf L$ is constant.

In rotation:

$$
\mathbf H = [\mathbf I]\boldsymbol\omega,\qquad \frac{d\mathbf H}{dt} = \frac{d}{dt}([\mathbf I]\boldsymbol\omega) = \sum\mathbf T_{ext}
$$

With no external torque, **$\mathbf H$ is constant in magnitude and direction.**

### The inertia matrix
See [[Inertia Matrix]].

$$
[\mathbf I] = \begin{bmatrix}I_{xx}&-I_{xy}&-I_{xz}\\-I_{xy}&I_{yy}&-I_{yz}\\-I_{xz}&-I_{yz}&I_{zz}\end{bmatrix}
$$

- **Moments of inertia** $I_{xx} = \int(y^2+z^2)dm > 0$: resistance to angular acceleration.
- **Products of inertia** $I_{xy} = \int xy\,dm$: measures of **unbalance**, which cause **cross-coupling** (a torque about one axis produces rotation about another).
- $[\mathbf I]$ sizes the torquers and appears in every control calculation.

> [!example] 2024/25 A4 (2 marks)
> $[\mathbf I] = \begin{bmatrix}1250&-550&-125\\-550&1250&-650\\-125&-650&2750\end{bmatrix}$ kg m².
>
> The large products of inertia mean the body axes are not principal axes, so it is not built to spin. Answer: **C, 3-axis stabilised**. (Its principal moments are 556, 1698 and 2996 kg m².)

## 3. Gyroscopic precession and momentum bias
- A torque $\mathbf T$ applied for $dt$ adds $\mathbf T\,dt$ to $\mathbf H$, **perpendicular** to $\mathbf H$ if $\mathbf T\perp\mathbf H$.
- The momentum vector therefore *precesses*: the displacement appears **90° later** in the direction of rotation.
- With a large bias $H_0$, the same impulse turns $\mathbf H$ through only a small angle, $d\psi = T\,dt/H_0$. This is **gyroscopic rigidity**:

$$
\dot\psi = \frac{T}{H_0}
$$

![[ast_momentum_dumping.png|520]]

**Momentum bias**:
- ✔ inherent stability against disturbance torques (2022/23 A2: explain with a diagram, 4 marks).
- ✘ one body axis must stay invariantly pointing (usually normal to the orbit plane);
- ✘ it introduces an oscillatory **nutation** mode that must be damped;
- ✘ torque responses differ from an unbiased body.
- Disturbances cause a **secular build-up** of momentum. Only external torques can change the total, so **external torquers are mandatory** on every spacecraft (2016/17 Q1(iii)).

## 4. The four stabilisation types
See [[Spacecraft Stabilisation Types]].

| | 1 Spinner | 2 Dual-spinner | 3 Hybrid (bias wheel) | 4 3-axis (zero bias) |
|---|---|---|---|---|
| How | whole body spins at 10–60 rpm | lower section spins at 10–60 rpm; upper platform despun (for example Earth-pointing) | 3-axis body + momentum wheel(s) at ~6500 rpm | no significant rotating parts, $H\approx0$ |
| $H = I\omega$ | large $I$, small $\omega$ | large $I$, small $\omega$ | **small $I$, large $\omega$** | ~0 |
| Pros | simple, passive, stiff | payload can point; spun section stays simple | 3-axis freedom and large arrays; wheel stores one axis of momentum (±10 % of bias) | full slewing freedom; stable platform; big arrays |
| Cons | body-mounted cells so **power-limited**; complex thermal; limited mounting for non-scanning payloads; comms via despun or omni antenna | despin **bearing and power transfer** (reliability); balance; nutation | nutation; one axis fixed | continuous active control; wheels, thrusters, complexity |
| Examples | Intelsat 1, Meteosat SG, Cluster, small sats | Giotto, Intelsat 2–4 and 6, Galileo | Navstar GPS 2R, Eurostar 3000, many comsats | Hubble, JWST, SPOT 5, Envisat, Magellan |

**Spinner rules**:
- The spin axis has a constant direction only if it is a **principal axis**.
- Long-term stability requires the **axis of maximum inertia**. Minimum-inertia spin is acceptable only for short periods (for example during a transfer burn).
- Equal transverse inertias give constant precession under a torque.
- Nutation is damped passively or actively.

> [!example] 2021/22 A2: why spin suits GEO weather imaging but not LEO
> - In GEO, the Earth disc is small and stays in a fixed direction. A spinner whose spin axis is normal to the orbit plane (parallel to Earth's axis) sweeps its imager across the Earth on each rotation (Meteosat's spin-scan). It is stable, simple and thermally even.
> - In LEO, nadir rotates once per orbit, so an inertially fixed spin axis cannot keep the imager pointed at Earth. A pushbroom imager needs a stable nadir-pointing 3-axis platform.

## 5. Torques and torquers
See [[Attitude Sensors and Torquers]].

**External torques (change $\mathbf H$)**:

A. **Natural disturbances**, with approximate altitude ranges:

| Disturbance | Significant where |
|---|---|
| Aerodynamic | < 500 km |
| Gravity gradient | < 30 000–40 000 km |
| Solar radiation pressure | all altitudes |
| Magnetic | < 30 000–40 000 km |
| Thrust misalignment | all altitudes |

B. **Controllable external torquers**:
- **Gas jets (thrusters)**: any torque size; on/off control; need propellant.
- **Magnetorquers**: no propellant, but need power and an **on-board magnetic field model**. They give **no torque about the field line**.
- Adjustable geometry (aero or solar-pressure trim tabs): low torque, no propellant. Example: Eurostar.

A type-B torquer is **essential** for controlling the total angular momentum.

**Internal torques (conserve $\mathbf H$)**:

A. **Disturbances**: mechanisms (array deployment), fuel slosh, astronaut motion.

B. **Controllable**:
- dual-spin mechanisms;
- **reaction wheels** (large slews, nominal speed near 0);
- **momentum wheels** (bias, about 6500 rpm);
- gimballed momentum wheels (**control moment gyros**).

Demo: $I_1\omega_1 = I_2\omega_2$ (conservation).

## 6. Momentum storage and dumping
See [[Reaction Wheels and Momentum Dumping]].
- Wheels store angular momentum. Their motor controls momentum flow between wheel and body, and they provide primary pointing control.
- **Periodic** momentum changes, where the before and after momenta are equal (for example Earth-pointing from an elliptic orbit, where the local vertical rate varies), can be absorbed by sizing the wheel capacity, with **no fuel**.
- **Secular** build-up from disturbances drives the wheel speed upward. At maximum speed, **dump**: torque the wheel down while external torquers hold attitude. This is **momentum dumping** (Europe) or **wheel desaturation** (USA).

## 7. Attitude sensors
**Two categories** (2019/20 A1(iv)):
- **Reference sensors**: give attitude relative to an external reference. Sun sensors, Earth (horizon) sensors, **star sensors/trackers** (arcsecond), magnetometers.
- **Inertial sensors**: measure *changes* in attitude. **Gyroscopes** (rate or rate-integrating) and accelerometers. They drift, so they are periodically updated from reference sensors.

## 8. Impact of the ACS on the spacecraft system
- The stabilisation choice drives the configuration: array type (body-mounted or deployed), payload mounting, antenna design, thermal symmetry.
- The ACS needs **power** (wheels, magnetorquers, processor), **propellant** (thrusters for dumping and slews), and **OBDH** (control law).
- Propulsion burns need thrust-vector control, so the spacecraft may be spun up during a solid-motor burn. For example, OMOTENASHI's retro-motor (2022/23 B1(ii)): spin averages thrust misalignment and gives gyroscopic stiffness.

## Links
- Parent: [[SESA2024 Astronautics Hub]] · Previous: [[SESA2024 05 - Orbital Transfers and the Hohmann Transfer]] · Next: [[SESA2024 07 - Spacecraft Propulsion]]
- Solutions: [[SESA2024 Workbook Ch6 - Attitude Control Solutions]]
- Control theory and Euler angles: [[SESA2027 Aerospace Mechanics & Control Hub]]

## Year 1 foundation
- Angular momentum ([[FEEG1002 D5 - Angular Impulse and Momentum]]), mass moment of inertia and $\sum M = I\alpha$ ([[FEEG1002 D8 - Kinetics of Rigid Bodies]]).
- Magnetorquers use the Lorentz force $F = BIL$ ([[FEEG1004 A2 - Magnetism, Induction and the Lorentz Force]]). Reaction wheels are DC/brushless motors with $T = K_Ti$ and a speed limit set by back EMF ([[FEEG1004 C5 - DC Motors - Torque, Back EMF and Efficiency]]).

## Sources
- Chapter 6 lectures and pre-recorded material (H. Sykulska-Lawrence); Fortescue, Stark & Swinerd, Ch. 9
