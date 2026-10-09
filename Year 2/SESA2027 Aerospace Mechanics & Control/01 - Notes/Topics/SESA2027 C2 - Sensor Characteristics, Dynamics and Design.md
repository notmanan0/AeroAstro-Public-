---
title: "SESA2027 C2 - Sensor Characteristics, Dynamics and Design"
module: "SESA2027 Aerospace Mechanics & Control"
type: topic
stream: "Part C: Sensing Systems"
order: 11
tags:
  - sesa2027
  - sensors
  - sensor-dynamics
  - noise
aliases: ["Sensor Characteristics", "Sensor Dynamics", "Sensor Design"]
date: 2026-09-24
status: complete
parent: ["[[SESA2027 Aerospace Mechanics & Control Hub]]"]
prerequisites: ["[[SESA2027 C1 - Sensing Systems, Sensor Principles and Sensor Fusion]]", "[[SESA2027 A4 - Laplace Transforms, Transfer Functions and Step Response]]", "[[SESA2027 A5 - Frequency Response and Bode Plots]]"]
next_topics: ["[[SESA2027 C3 - Signal Conditioning, Digitisation and Digital Filtering]]"]
key_concepts: ["[[Accuracy and Precision]]", "[[Sensor Dynamic Models]]", "[[Step Response Specifications]]", "[[Bode Plot]]"]
tutorial_sheets: ["[[SESA2027 Part C Problem Sheet Solutions]]"]
sources: ["02 - Sources/Lectures/Lecture 3.04.pdf", "02 - Sources/Lectures/Lecture 3.05.pdf", "02 - Sources/Lectures/Lecture 3.06.pdf"]
---

# SESA2027 C2 - Sensor Characteristics, Dynamics and Design

> [!abstract] Summary
> Every sensor is **bounded** (range, saturation), **corrupts** the signal (bias and noise) and is **not instantaneous** (lag and phase shift). A sensor is itself a **dynamic system**, so we model it with the tools from Part A:
> - **zeroth order**: $y = Ku$;
> - **first order**: $K/(\tau s+1)$;
> - **second order**: $K\omega_n^2/(s^2+2\zeta\omega_ns+\omega_n^2)$.
>
> We judge it by rise time, overshoot, settling time and its Bode plot. Design means matching the sensor's bandwidth to the aircraft's dynamics, choosing $\zeta\approx0.7$ for second-order sensors, trading noise against lag when filtering, and placing sensors sensibly on the airframe.

## Key Concepts
- [[Accuracy and Precision]] · [[Sensor Dynamic Models]] · [[Step Response Specifications]] · [[Bode Plot]]

---

## 1. Universal limitations (L3.04)
"No sensor is a perfect window to reality." Every sensor:
1. **is bounded**: it measures only within physical limits;
2. **corrupts the signal**: noise, offsets, environmental sensitivity;
3. **is not instantaneous**: physics takes time, so the signal is always delayed.

### Accuracy vs precision
See [[Accuracy and Precision]].

| | Accuracy | Precision (repeatability) |
|---|---|---|
| Meaning | How close the **mean** is to the true value | How tightly repeated readings cluster |
| Lost through | **Systematic** error (bias/offset) | **Random** error (noise) |
| Aircraft example | IMU reads +2° pitch when level | GPS jumps within 5 m when stationary |
| Control impact | **Steady-state deviation**: the autopilot "levels" to the wrong attitude, causing altitude drift or a skewed approach | **Actuation jitter**: the controller chases noise, causing servo wear, extra energy use and excited structural modes |

### Range, sensitivity and saturation
- **Span** = upper limit − lower limit. Example: a 5–100 PSI sensor has a 95 PSI span.
- **Operating range**: the part of the span where the output is linear.
- **Sensitivity**: the slope, $S = \Delta V/\Delta P$.
- **Saturation**: beyond the limits the output stops being proportional, and at saturation $S = 0$ (the sensor is "blind").
  - *Physical limit*: the diaphragm or spring reaches maximum displacement.
  - *Electrical limit*: the amplifier hits its voltage rails. This is usually in the conditioning, not the sensor.
- **Clipping**: peak information is lost. It is often designed in deliberately, before the sensor itself saturates.

### Noise and SNR
- **Sources**:
  - thermal noise (random electron motion);
  - **EMI** from motors, radios and power lines;
  - **quantisation** noise from the ADC.
- **SNR**: signal strength relative to noise. Below the **noise floor**, a signal cannot be distinguished.

**Time-domain statistics** (N readings at constant input):

$$
\mu = \frac1N\sum_{i=1}^Nx_i,\qquad \sigma^2 = \frac{1}{N-1}\sum_{i=1}^N(x_i-\mu)^2
$$

- $\mu\neq0$ means bias (an accuracy problem).
- $\sigma$ is the spread (a precision problem).
- For Gaussian noise, 95 % of readings fall within $\pm2\sigma$.

**Frequency-domain view**:
- Take the Fourier transform of the reading of a constant input.
- **White noise** has equal power at all frequencies.
- Real sensors show **band-limited** white noise: flat up to the sensor bandwidth, then rolling off, often with EMI spikes (e.g. motor harmonics).

### Time lag and phase shift
Physical causes:
- **thermal inertia** (a thermocouple must heat up);
- **mechanical/fluid inertia** (air in pitot tubing moving a diaphragm);
- **signal conditioning** (low-pass filters slow the signal on purpose).

- **Time constant $\tau$**: the time to reach **63.2 %** of the final value after a step. Piezo accelerometers have a small $\tau$; fluid thermometers a large one.
- Under oscillatory input, the lag appears as a **phase shift**, and it grows with frequency.

> [!important] Key insight
> Improving one characteristic usually worsens another. Reducing noise increases delay.

## 2. Sensors as dynamic systems (L3.05)
- A sensor has mass, inertia, friction and electromagnetic dynamics. Its output depends on the current input **and** its history.
- In Part A we neglected sensor dynamics (DAP3). Here we put them back.

**State-space model**:

$$
\dot{\mathbf x} = \mathbf A\mathbf x+\mathbf Bu,\quad y = \mathbf C\mathbf x+\mathbf Du
$$

- $u$ is the aircraft state being measured.
- $\mathbf x$ is the internal sensor state (diaphragm displacement, voltage, ...).
- $y$ is the reported signal.

The internal matrices are hard to find. So in practice we treat the sensor as a **black box**, $G(s) = Y(s)/U(s)$, and identify it experimentally. Sine sweeps or broadband noise are fed through a spectrum analyser, which gives the Bode magnitude and phase directly. See [[Transfer Function]] and [[Frequency Response Function]].

### Three model orders (DAP2, Occam's razor)
See [[Sensor Dynamic Models]].

| Order | Model | Examples | Character |
|---|---|---|---|
| **0th** | $y = Ku$ | Strain gauge, potentiometer, LVDT, thermistor (ignoring thermal mass), squat switch | Instantaneous, no lag; $K$ is the sensitivity |
| **1st** | $\tau\dot y+y = Ku$, i.e. $\dfrac{K}{\tau s+1}$ | Thermocouple/temperature probe, pressure sensor with long lines, pitot-static, float fuel gauge | Exponential lag set by $\tau$ |
| **2nd** | $\ddot y+2\zeta\omega_n\dot y+\omega_n^2y = K\omega_n^2u$ | Accelerometer, rate gyro, pressure diaphragm, AoA vane, IMU | Mass–spring–damper: overshoot or sluggishness depending on $\zeta$ |

![[amc_sensor_order_step.png|650]]

### Time-domain metrics
The metrics are the same as in [[SESA2027 A4 - Laplace Transforms, Transfer Functions and Step Response]]:

$$
t_r\approx\frac{1.8}{\omega_n},\qquad t_s\approx\frac{4.6}{\zeta\omega_n}\ (1\%),\ \frac{3}{\zeta\omega_n}\ (5\%),\qquad OS = 100\,e^{-\zeta\pi/\sqrt{1-\zeta^2}}\ \%
$$

The 4.6 comes from $\ln0.01\approx-4.6$, and the 3 from $\ln0.05\approx-3.0$.

- **Measurement lag**:
  - none for 0th-order sensors;
  - set by $\tau$ for 1st-order sensors;
  - for 2nd-order sensors, a higher $\omega_n$ reduces lag and a higher $\zeta$ increases it.
- **Overshoot** gives a **false peak**. The sensor reports, say, a $q$ larger than reality, which could trigger an aggressive and unnecessary response from the flight control computer.

### Frequency-domain view
- **Low frequency**: the sensor is "transparent"; the output is the input scaled by $K$.
- **Near $\omega_n$** (2nd order, low $\zeta$): **resonance** gives false high readings.
- **High frequency**: the output is attenuated towards zero, and the **phase lag** grows. Phase lag is critical for loop stability.

Frequency-dependent sensor lag is distinct from **frequency-independent delays** (digitisation, storage, buses). Those are covered in [[SESA2027 C3 - Signal Conditioning, Digitisation and Digital Filtering]].

## 3. Sensor system design (L3.06)
### Requirements
- **Range with margin**. For example, a maximum pitch rate of ±20 °/s calls for a gyro range of about ±30 °/s.
- **Resolution**: the smallest detectable change.
- **Accuracy** (static error).
- **Dynamic requirements**:
  - **bandwidth**: accurate magnitude and phase over the frequencies of interest;
  - **maximum allowable lag** before old data compromises closed-loop stability.

### Selecting the order

| Order | Design strategy | Primary challenge | Impact on the control loop |
|---|---|---|---|
| 0th | Assume $y = Ku$ | No natural smoothing; sensitive to noise, EMI and temperature | Noise → actuator jitter and control effort |
| 1st | **Minimise $\tau$**: make it well below the airframe's response time | Lag and phase delay | Delayed feedback → reduced stability margins |
| 2nd | **High $\omega_n$, then tune $\zeta$** | Overshoot and resonance | Signal distortion → aggressive or misleading control action |

### Optimal damping for second-order sensors

| $\zeta$ | Behaviour | Risk |
|---|---|---|
| $<0.5$ (underdamped) | Fast, large overshoot | False peaks; massive over-reading if the input frequency is near $\omega_n$ |
| **$\approx0.7$** | Fastest settling with about 5 % overshoot; flattest magnitude (no resonant peak for $\zeta\ge0.707$) | **Engineering optimum** |
| $>1$ (overdamped) | No overshoot, sluggish | Large lag: "old" data, reduced margins |

![[amc_psc_q5_damping_tradeoff.png|700]]

### Placement and interference
- **Aerodynamic**: pitot tubes and AoA vanes must sit in **clean flow**, away from the fuselage boundary layer and wing downwash, so that $K$ stays constant.
- **Structural**: mount the IMU **near the CG**. Otherwise wing and fuselage bending modes are mistaken for rigid-body motion.
- **EMI**: shield sensors from power cables, igniters and radio transmitters.
- **Noise sources**:
  - mechanical (engine or rotor vibration, turbulence);
  - electrical (thermal jitter, digitisation).
  - The goal is an SNR high enough that the noise floor never masks a real manoeuvre.

### Bode view and the RC filter
- **Magnitude plot**: shows where the sensor is transparent, where it attenuates and where it resonates.
- **Phase plot**: shows the lag directly. Excessive phase lag at crossover can cause instability or **pilot-induced oscillation (PIO)**.

**First-order RC low-pass filter** (hardware, placed before the ADC):

$$
G_{filter}(s) = \frac{1}{\tau s+1},\qquad \tau = RC,\qquad \omega_c = \frac1\tau,\quad f_c = \frac{1}{2\pi\tau}
$$

At $\omega_c$: $|G| = 1/\sqrt2$ (−3 dB) and the phase is −45°. Above it, the magnitude falls at −20 dB/dec.

![[amc_psc_q6_rc_filter_bode.png|600]]

**The noise vs lag conflict**:
- A **large $\tau$** gives a clean but late signal and a sluggish loop.
- A **small $\tau$** gives a fast signal, but noise reaches the actuators, causing wear and jitter.
- **Choose $f_c$ high enough not to destabilise the airframe, and low enough to block damaging vibration.**

## Links
- Parent: [[SESA2027 Aerospace Mechanics & Control Hub]] · Previous: [[SESA2027 C1 - Sensing Systems, Sensor Principles and Sensor Fusion]] · Next: [[SESA2027 C3 - Signal Conditioning, Digitisation and Digital Filtering]]
- Same maths as the aircraft: [[SESA2027 A4 - Laplace Transforms, Transfer Functions and Step Response]], [[SESA2027 A5 - Frequency Response and Bode Plots]]
- Worked problems: [[SESA2027 Part C Problem Sheet Solutions]] (Q4–Q6)

## Year 1 foundation
- An accelerometer is the SDOF oscillator of [[FEEG1002 D6 - Single Degree of Freedom Vibration]], used below resonance.
- The static vocabulary (sensitivity, resolution, precision, accuracy) and the RC filter first appear in [[FEEG1004 E1 - Measurement Systems and Temperature Sensors]] and [[FEEG1004 D3 - AC Filters and Bode Plots]].

## Sources
- Lectures 3.04–3.06 (Prof A. Cammarano)
- Bentley, *Principles of Measurement Systems*, Ch. 2–4
