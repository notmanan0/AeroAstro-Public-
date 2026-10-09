---
title: "SESA2027 C1 - Sensing Systems, Sensor Principles and Sensor Fusion"
module: "SESA2027 Aerospace Mechanics & Control"
type: topic
stream: "Part C: Sensing Systems"
order: 10
tags:
  - sesa2027
  - sensors
  - measurement-chain
  - sensor-fusion
aliases: ["Sensing Systems", "Sensor Principles", "IMU Sensor Fusion"]
date: 2026-09-24
status: complete
parent: ["[[SESA2027 Aerospace Mechanics & Control Hub]]"]
prerequisites: ["[[SESA2027 B4 - Robustness, Stability vs Manoeuvrability and Design Process]]"]
next_topics: ["[[SESA2027 C2 - Sensor Characteristics, Dynamics and Design]]"]
key_concepts: ["[[Measurement Chain]]", "[[Wheatstone Bridge and Strain Gauges]]", "[[Accuracy and Precision]]", "[[Complementary Filter]]"]
tutorial_sheets: ["[[SESA2027 Part C Problem Sheet Solutions]]"]
sources: ["02 - Sources/Lectures/Lecture 3.01.pdf", "02 - Sources/Lectures/Lecture 3.02.pdf", "02 - Sources/Lectures/Lecture 3.03.pdf"]
---

# SESA2027 C1 - Sensing Systems, Sensor Principles and Sensor Fusion

> [!abstract] Summary
> A feedback controller never sees the true output $y(t)$. It sees the **measured output** produced by a **sensing system**:
>
> **physical quantity → sensor → signal conditioning → data acquisition (ADC) → processing**
>
> Every measurement carries **noise** (random), **bias** (systematic) and **drift** (slow). Sensing elements work by exploiting a physical effect: resistive, capacitive, inductive, thermoelectric or piezoelectric. No single sensor is perfect. An **IMU** therefore fuses a gyroscope, which is good at high frequency but drifts, with an accelerometer, which is good at low frequency but noisy. The simplest fusion scheme is the **complementary filter**.

## Key Concepts
- [[Measurement Chain]] · [[Accuracy and Precision]] · [[Wheatstone Bridge and Strain Gauges]] · [[Complementary Filter]]

---

## 1. Why sensing matters for control (L3.01)
In the B-part block diagram the feedback path contains a **sensor $H(s)$** and **measurement noise $X_N$**. See [[SESA2027 B4 - Robustness, Stability vs Manoeuvrability and Design Process]].

- The controller acts on the *measured* output, so sensor errors become control errors.
- Pitch control, for example, needs $\theta$, $q$ and $a_z$. These are measured with gyroscopes, accelerometers and IMUs.
- "The flight control computer cannot *see* the aircraft moving. It relies entirely on electrical representations of that motion."

**Sensing system**: a system that measures a physical quantity and converts it into a usable signal for monitoring, analysis or control. It is usually several elements working together, not a single device.

| Class of measured quantity | Examples |
|---|---|
| Motion | Angular rate, acceleration, position, altitude |
| Environmental | Temperature, atmospheric pressure, humidity/icing, radiation |
| Mechanical | Strain, vibration, mechanism position, subsystem status |
| Aerodynamic | Airspeed, static/dynamic pressure, angle of attack |

## 2. The measurement chain
See [[Measurement Chain]].

| Stage | Job |
|---|---|
| **Sensor / sensing element** | Interacts directly with the physical quantity |
| **Signal conditioning** | Makes the raw signal usable: amplify, filter, linearise, offset, protect |
| **Data acquisition (DAQ)** | Sampling, analogue-to-digital conversion (ADC), transmission |
| **Processing / display** | Estimation, control, storage, visualisation |

**Sensor vs transducer**:
- A **sensor** *detects* the quantity. Examples: an accelerometer sensing acceleration, a pressure diaphragm.
- A **transducer** *converts energy* from one form to another, usually into an electrical signal. Examples: a strain gauge (strain → resistance), a thermocouple (temperature difference → voltage).

## 3. Measurement imperfections

| Error | Nature | Typical causes | Effect |
|---|---|---|---|
| **Noise** | Random, short-term | Electrical interference, thermal noise, environment | Jitter; poor **precision** |
| **Bias** | Constant offset | Calibration error, manufacturing tolerance, modelling | Consistently high or low; poor **accuracy** |
| **Drift** | Slow change over time | Temperature, ageing, component variation | Error grows; the rate hints at the cause |
| **Limited resolution** | Smallest detectable change | ADC bits, sensor physics | Quantisation steps |

**Filtering trade-off**: a low-pass filter removes high-frequency noise, but it **adds lag, slows the response and reduces bandwidth**. If filtering is too strong, the controller works from stale information. This theme runs through all of Part C.

**Design considerations**: range, accuracy, sensitivity, bandwidth, environment (temperature, vibration), reliability and robustness, and integration with the electronics.

## 4. Sensing principles (L3.02)
**Transduction** is the conversion of energy from one form to another. The sensing element interacts with the measured variable, and the transduction process turns that interaction into an electrical signal.

| Principle | Physical law | Measures |
|---|---|---|
| Resistive | $R = \rho L/A$ | Strain, temperature |
| Capacitive | $C = \varepsilon_0\varepsilon A/d$ | Displacement, pressure, acceleration |
| Inductive | $L = n^2/\mathfrak R$ | Position, motion |
| Thermoelectric | $V = \alpha_T(T_h-T_c)$ (Seebeck) | Temperature |
| Piezoelectric | $q = dF$ | Dynamic force, vibration |

### 4.1 Resistive: strain gauges and the Wheatstone bridge
Stretching a conductor lengthens it and narrows its cross-section, so $R$ rises. The bridge output is

$$
V_G = \left(\frac{R_2}{R_1+R_2}-\frac{R_4}{R_3+R_4}\right)V_s
$$

- The bridge is **balanced** ($V_G = 0$) when all four resistances are equal.
- **Quarter bridge**: the gauge is $R_2 = R+\Delta R$, with all others equal to $R$. Then

$$
V_G = \left(\frac{R+\Delta R}{2R+\Delta R}-\frac12\right)V_s\;\xrightarrow{\ \Delta R\ll R\ }\;\boxed{\frac{\Delta R}{R}\approx\frac{4V_G}{V_s}},\qquad \frac{\Delta R}{R} = G\varepsilon\;\Rightarrow\;V_G = \frac{V_s}{4}G\varepsilon
$$

  $G$ is the gauge factor, about 2 for metal foil.
- **We measure resistance, not strain.** The strain is inferred.
- **Temperature** also changes $\rho$, so a temperature change looks like strain.
- **Half bridge**: put a second, identical gauge in the adjacent arm ($R_1$). Temperature changes both gauges equally and cancels in the ratio.
- On a bending cantilever with one gauge in tension and one in compression, the two strain signals **add**. That doubles the sensitivity while temperature still cancels.

See [[Wheatstone Bridge and Strain Gauges]].

### 4.2 Thermoelectric: thermocouples
- The **Seebeck effect**: two dissimilar conductors joined across a temperature difference generate $V = \alpha_T(T_h-T_c)$.
- Carriers at the hot junction diffuse towards the cold one, and different materials create a net charge imbalance.
- **Self-powered**: no external supply is needed.

Typical figures:
- Range −200 to 1700 °C (types K, R, S).
- Response time ms to s (thermal mass).
- Accuracy ±1–2 °C.

Uses include gas-turbine temperatures (500–1500 °C), exhaust gas temperature (EGT, about 400–900 °C) and spacecraft thermal monitoring.

### 4.3 Capacitive
$C = \varepsilon_0\varepsilon A/d$, with $\varepsilon_0 = 8.85$ pF/m.

| Configuration | Relation |
|---|---|
| Gap change (distance) | $C = \dfrac{\varepsilon_0\varepsilon A}{d+x}$ |
| Area change (relative position) | $C = \dfrac{\varepsilon_0\varepsilon}{d}(A-wx)$ |
| Diaphragm pressure sensor | $\dfrac{\Delta C}{C} = \dfrac{(1-\nu^2)a^4}{16Edt^3}P$ |

**Capacitive (MEMS) accelerometer**:
- A proof mass on flexures moves under acceleration, which changes the plate gap.
- Range ±1 g to ±100 g.
- Capacitance changes of fF to pF; resolution down to µg.

### 4.4 Inductive
A magnetic circuit is analogous to an electric one: m.m.f. $= ni = \phi\mathfrak R$.

$$
L = \frac{n^2}{\mathfrak R},\qquad \mathfrak R = \frac{l}{\mu\mu_0A},\qquad \mathfrak R_{tot} = \mathfrak R_{core}+\mathfrak R_{gap}+\mathfrak R_{armature} = \mathfrak R_0+kd,\quad k = \frac{2}{\mu_0\pi r^2}
$$

$$
\boxed{L = \frac{n^2}{\mathfrak R_0+kd}}
$$

The gap $d$ between the armature and the core changes the inductance. This is a **displacement sensor**, e.g. for landing-gear or actuator position.

### 4.5 Piezoelectric
- **Mechanics**: $x = F/k$.
- **Direct piezoelectric effect**: $q = Kx = dF$, where $d = K/k$ is the charge sensitivity in C/N.
- **Electrically**, the crystal is a charge source in parallel with a capacitance $C = \varepsilon_0\varepsilon A/t$.
- The charge leaks away, so there is **no output for a static force**. Piezoelectric sensors are for **dynamic** measurement only: vibration and shock.

## 5. Sensor fusion and the IMU (L3.03)
Real measurements are imperfect (noise, bias, limited bandwidth), and no single sensor gives complete information. Combining sensors improves accuracy and robustness and extends what can be measured. The price is precision vs reliability vs cost.

**IMU**: measures motion without external references.
- 3-axis accelerometer plus 3-axis gyroscope gives 6 DoF. Adding a magnetometer gives 9 DoF.
- Outputs are linear acceleration and angular velocity in the body frame. Integration gives orientation, velocity and position.

| | Accelerometer | Gyroscope |
|---|---|---|
| Principle | Newton's 2nd law on a proof mass | Coriolis effect (MEMS) |
| Measures | **Specific force** (includes gravity) | Angular velocity |
| Strength | Good **long-term** reference (gravity) | Accurate **short-term** dynamics |
| Weakness | Noisy; affected by manoeuvres; cannot separate acceleration from gravity | **Bias integrates into drift**; errors accumulate |

### Complementary filter
See [[Complementary Filter]].

$$
\boxed{\hat\theta = \alpha\,\theta_{gyro}+(1-\alpha)\,\theta_{acc}}
$$

- The gyro path is effectively **high-pass filtered**: it is trusted for fast changes.
- The accelerometer path is effectively **low-pass filtered**: it is trusted for the slow, steady value.
- The two filters sum to 1, so the true signal passes through undistorted. Each sensor's *error* is removed in the band where that sensor is weak.

![[amc_complementary_filter.png|650]]

The figure shows three things:
- The integrated gyro (red) follows the shape of the motion but wanders off because of bias.
- The accelerometer (orange) has no drift but is buried in noise.
- The complementary estimate with $\alpha = 0.98$ (blue) tracks the truth.

> [!tip] Why the complementary filter is not "averaging"
> An average weights both sensors equally at every frequency, so it would inherit **both** the gyro drift and the accelerometer noise. The complementary filter assigns **frequency roles**: gyro at high frequency, accelerometer at low frequency.

## Links
- Parent: [[SESA2027 Aerospace Mechanics & Control Hub]] · Previous: [[SESA2027 B4 - Robustness, Stability vs Manoeuvrability and Design Process]] · Next: [[SESA2027 C2 - Sensor Characteristics, Dynamics and Design]]
- Worked problems: [[SESA2027 Part C Problem Sheet Solutions]] (Q1–Q3, Q13)

## Sources
- Lectures 3.01–3.03 (Prof A. Cammarano)
- Bentley, *Principles of Measurement Systems* (Ch. 1, 2, 4, 8)
- Groves, *Principles of GNSS, Inertial, and Multisensor Integrated Navigation Systems* (Ch. 4)
