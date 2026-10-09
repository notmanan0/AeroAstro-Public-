---
title: "SESA2027 Part C Problem Sheet Solutions"
module: "SESA2027 Aerospace Mechanics & Control"
type: tutorial
stream: "Part C: Sensing Systems"
tags:
  - sesa2027
  - tutorial-solutions
  - sensors
  - signal-conditioning
sheet: "Practice Problems: Part C – Sensing Systems (2025–26, Prof A. Cammarano)"
theory_notes: ["[[SESA2027 C1 - Sensing Systems, Sensor Principles and Sensor Fusion]]", "[[SESA2027 C2 - Sensor Characteristics, Dynamics and Design]]", "[[SESA2027 C3 - Signal Conditioning, Digitisation and Digital Filtering]]"]
key_concepts: ["[[Measurement Chain]]", "[[Wheatstone Bridge and Strain Gauges]]", "[[Sensor Dynamic Models]]", "[[ADC Quantisation and Resolution]]", "[[Loading Effect and Buffering]]", "[[Nyquist Sampling and Aliasing]]", "[[Digital Filtering]]", "[[Complementary Filter]]"]
status: complete
sources: ["02 - Sources/Problem Sheets/Problem Sheet-Part C Questions.pdf"]
---

# SESA2027 Part C Problem Sheet Solutions

> [!abstract] Sheet Info
> Thirteen revision questions on Lectures 3.01–3.08. Numerical answers are given to 3 s.f., as the sheet asks, and were verified in Python.
>
> | Q | Answer |
> |---|---|
> | Q2 | $\Delta R/R = 2.40\times10^{-3}$, $\varepsilon = 1.14\times10^{-3}$ |
> | Q4 | $s = -4.20\pm11.2i$, $t_r = 0.150$ s, $OS = 30.9\%$, $t_s = 1.10$ s |
> | Q6 | $\omega_c = 25.0$ rad/s, $f_c = 3.98$ Hz |
> | Q7 | $A_v = 16.5$, $V_{os} = 1.32$ V; 150 mV gives 3.80 V, which **clips** |
> | Q8 | $Q_8 = 19.5$ mV, $Q_{12} = 1.22$ mV, force resolution 4.88 mN |
> | Q9 | 0.909, a 9.09 % loading error |
> | Q10 | $f_s>16$ Hz; $f_N = 25$ Hz; alias at **20 Hz** |
> | Q11 | Delay 0.0200 s; $\alpha = 0.100$ |
> | Q12 | Bias error 1.20 units after 60 s |

## Theory Links
- [[SESA2027 C1 - Sensing Systems, Sensor Principles and Sensor Fusion]] · [[SESA2027 C2 - Sensor Characteristics, Dynamics and Design]] · [[SESA2027 C3 - Signal Conditioning, Digitisation and Digital Filtering]]

---

## Q1: Measurement chain and sensor imperfections

### (i) Block diagram (aircraft pitch-rate measurement)
The chain runs through these stages; see [[Measurement Chain]].

| Stage | Pitch-rate example |
|---|---|
| **Physical quantity** | Aircraft pitch rate $q$ |
| **Sensor / transducer** | MEMS rate gyro. Coriolis force on a vibrating proof mass is sensed capacitively and output as a voltage |
| **Signal conditioning** | Buffer amplifier, gain and offset into the ADC window, anti-alias RC low-pass filter |
| **ADC / DAQ** | Sampling at $f_s$, $n$-bit quantisation to $N[k]$, bus transfer to the flight control computer |
| **Measured output** | Digital samples $q_m[k]$ used by the flight control law (feedback) |

### (ii) Sensor vs transducer
- A **sensor** is the element that *detects* the physical quantity. Aerospace example: the **proof mass of an accelerometer** in an IMU, or a pitot probe sensing total pressure.
- A **transducer** *converts energy* from one form to another, usually to electrical. Examples:
  - a **thermocouple** measuring EGT (temperature difference → voltage, Seebeck);
  - a **strain gauge** on a wing spar (strain → resistance change).

### (iii) Constant pitch-rate bias of 0.8 °/s
The controller acts on $q_m = q+0.8$.
- In a pitch-rate damper regulating $q_m\to0$, the loop drives the **true** pitch rate to $q = -0.8$ °/s. The aircraft steadily pitches nose-down at 0.8 °/s while the controller "believes" it is holding $q = 0$.
- Any attitude estimate obtained by integrating $q_m$ drifts by **0.8 °/s, i.e. 48° per minute**.
- An outer attitude loop with integral action, or a reference sensor, can compensate. Without that, the result is a **steady-state deviation**: an accuracy problem that feedback cannot see.

### (iv) Noisy but unbiased
- **Accuracy is good**: the *mean* of many readings equals the true value, because there is no systematic error.
- **Precision is poor**: individual readings scatter widely ($\sigma$ is large).
- Averaging or filtering can recover the mean, at the cost of delay.
- In control, poor precision causes **actuator jitter**: the controller chases the noise. See [[Accuracy and Precision]].

### (v) Why clipping and aliasing destroy information
An ordinary measurement error (noise, bias) leaves the information in the data, so it can be averaged or calibrated out.
- **Clipping**: every input above the limit maps to the **same** output value. The mapping is many-to-one and cannot be inverted, so the peak's magnitude is gone.
- **Aliasing**: after sampling, a component at $f$ and one at $|f-mf_s|$ produce **identical samples**. The digital data cannot tell a 70 Hz vibration from a genuine 20 Hz motion.

Both happen **before** or **at** the ADC, so no later algorithm can undo them.

---

## Q2: Quarter-bridge strain gauge
Given $V_s = 5$ V, $R = 120$ Ω, $V_G = 3.0$ mV and $G = 2.1$.

### (i) Fractional resistance change

$$
\frac{\Delta R}{R}\approx\frac{4V_G}{V_s} = \frac{4(0.003)}{5} = \boxed{2.40\times10^{-3}}\qquad(\Delta R = 0.288\ \Omega)
$$

### (ii) Strain

$$
\varepsilon = \frac{\Delta R/R}{G} = \frac{2.40\times10^{-3}}{2.1} = \boxed{1.14\times10^{-3}}\ (1140\ \mu\varepsilon)
$$

### (iii) Temperature corruption
- The gauge's resistivity $\rho$ depends on temperature, and thermal expansion strains the gauge and the substrate differently.
- A temperature change therefore changes $R$ even with **no mechanical strain**, and $\Delta R_T$ is indistinguishable from $\Delta R_\varepsilon$ at the bridge output.
- For example, $\Delta R_T/R$ of $10^{-3}$ would appear as about 480 µε of false strain.

### (iv) Half-bridge compensation
- Replace $R_1$, the resistor in the adjacent arm, with a **second identical gauge** at the same temperature. It can be a dummy gauge or, on a beam, a gauge on the opposite face.
- The output depends on the **ratio** $R_2/(R_1+R_2)$. A temperature change adds the same $\Delta R_T$ to both, so it cancels to first order.
- If the second gauge is in compression (opposite face of a cantilever), the strain signals **add**, which doubles the sensitivity: $V_G\approx\frac{V_s}{2}G\varepsilon$.

See [[Wheatstone Bridge and Strain Gauges]].

---

## Q3: Selecting sensing principles

| Task | Principle | Justification |
|---|---|---|
| (i) Wing-root strain | **Resistive** (foil strain gauge in a bridge) | Direct strain → $\Delta R$, zeroth-order (instantaneous), cheap, bonds to the structure; temperature-compensated with a half/full bridge |
| (ii) Turbine exhaust gas temperature | **Thermoelectric** (type K thermocouple) | Works to about 1300 °C (type K), rugged, self-powered, adequate response |
| (iii) MEMS proof-mass displacement | **Capacitive** | Tiny gap changes give measurable $\Delta C$ (fF resolution); easy to integrate on silicon |
| (iv) Landing-gear position | **Inductive** (proximity sensor/LVDT) | Non-contact, robust to dirt, ice and vibration; $L = n^2/(\mathfrak R_0+kd)$ detects the armature gap |
| (v) High-frequency structural vibration | **Piezoelectric** (accelerometer) | High stiffness gives a high $\omega_n$ and wide bandwidth; self-generating; no static response is needed |
| (vi) Pitch-axis angular velocity | **Gyroscopic** (MEMS Coriolis rate gyro) | Measures angular rate directly; accurate at high frequency (bias drift is handled by fusion) |

---

## Q4: Second-order sensor, $K = 1$, $\omega_n = 12$ rad/s, $\zeta = 0.35$

### (i) Poles

$$
s = -\zeta\omega_n\pm i\omega_n\sqrt{1-\zeta^2} = -4.20\pm11.2i\ \text{rad/s}
$$

### (ii) Character
**Stable**: $\mathrm{Re}(s) = -4.2<0$. **Oscillatory**: the poles are complex because $\zeta<1$. The damped frequency is $\omega_d = 11.2$ rad/s.

### (iii) Rise time
$t_r\approx1.8/12 = \mathbf{0.150}$ **s**.

### (iv) Overshoot

$$
OS = 100\exp\left(\frac{-0.35\pi}{\sqrt{1-0.1225}}\right) = 100e^{-1.174} = \mathbf{30.9\%}
$$

### (v) Settling time
$t_s\approx4.6/(0.35\times12) = 4.6/4.2 = \mathbf{1.10}$ **s**.

### (vi) Sketch
The response rises to a first peak of 1.31 at $t_p = \pi/\omega_d = 0.28$ s, rings at 11.2 rad/s, and enters the ±1 % band near 1.1 s.

![[amc_psc_q4_sensor_step.png|620]]

A 31 % false peak in an angular-rate sensor would make the flight control computer over-react. This sensor needs more damping.

---

## Q5: Damping trade-off ($\omega_n = 20$ rad/s)

### (i) Qualitative step responses

| Sensor | $\zeta$ | Response |
|---|---|---|
| A | 0.20 | Strongly underdamped: fast rise, **53 % overshoot**, prolonged ringing ($t_s\approx1.15$ s); resonant peak $M_r = 2.55$ (+8.1 dB) at about 19 rad/s |
| B | 0.70 | Near-optimal: quick rise, **about 4.6 % overshoot**, fastest settling ($t_s\approx0.33$ s); flat magnitude response |
| C | 1.20 | Overdamped: real poles at −10.7 and −37.3 rad/s, **no overshoot**, but a slow creeping approach (dominant $\tau\approx0.093$ s) |

![[amc_psc_q5_damping_tradeoff.png|760]]

### (ii) False peaks: Sensor A
With the lowest $\zeta$, the overshoot of about 53 % reports a peak value that never physically occurred. If the input contains content near $\omega_n$, **resonance** amplifies it by up to 2.55×. The controller could respond aggressively to motion that is not there.

### (iii) Excessive lag: Sensor C
With $\zeta>1$ there is no overshoot, but the response is sluggish: the dominant pole at −10.7 rad/s dominates. Below $\omega_n$ its phase lag is the largest of the three (e.g. at $\omega = 5$ rad/s it lags by about 32°, against about 20° for B and 6° for A), so the controller receives stale information and the phase margin is reduced.

### (iv) Best compromise: Sensor B
- $\zeta\approx0.7$ gives the fastest settling with small, predictable overshoot and **no resonant peak** (a maximally flat magnitude).
- The phase is close to linear over the passband, i.e. a near-constant time delay with little waveform distortion.
- It is the standard target for aerospace motion sensors.

### (v) Poor placement
- A transfer-function model assumes the sensor measures only the intended quantity.
- **An IMU far from the CG** picks up wing and fuselage bending modes and rotational acceleration terms ($\dot q\times r$). These appear as spurious signals, possibly near $\omega_n$.
- **A pitot tube or AoA vane in the fuselage boundary layer or wing downwash** sees local flow, not free-stream flow, so its effective sensitivity $K$ changes with $\alpha$ and configuration.
- **Proximity to power cables** injects EMI.
- In all these cases the sensor dynamics may be perfect while the *measured quantity* is wrong.

---

## Q6: RC anti-noise filter, $\tau = 0.04$ s

### (i) Cut-off in rad/s
$\omega_c = 1/\tau = \mathbf{25.0}$ **rad/s**.

### (ii) Cut-off in Hz
$f_c = \omega_c/2\pi = \mathbf{3.98}$ **Hz**.

### (iii)–(iv) Magnitude at three frequencies
$|H_f| = 1/\sqrt{1+(\omega\tau)^2}$:

| $\omega$ (rad/s) | $\omega\tau$ | $\lvert H_f\rvert$ | dB | Phase |
|---|---|---|---|---|
| 5 | 0.2 | 0.981 | −0.170 | −11.3° |
| 25 | 1 | 0.707 | −3.01 | −45.0° |
| 100 | 4 | 0.243 | −12.3 | −76.0° |

### (v) Bode sketch
The magnitude is flat at 0 dB (unit DC gain) up to the corner at 25 rad/s, where it is −3 dB. Above the corner it falls at −20 dB/decade. The phase goes from 0° to −90°, passing −45° at the corner.

![[amc_psc_q6_rc_filter_bode.png|600]]

### (vi) Increasing $\tau$
- The cut-off falls, so more noise is removed.
- **But** there is more phase lag at every frequency: at the loop's crossover frequency, the extra lag $\tan^{-1}(\omega_{gc}\tau)$ subtracts directly from the **phase margin**.
- The consequences are a sluggish measured signal, reduced stability margins, possible oscillation or PIO, and the loss of genuine fast dynamics if $f_c$ drops into the aircraft's control band.

---

## Q7: Scaling, offsetting and clipping
The sensor range is $[-80, 120]$ mV and the ADC range is $[0, 3.3]$ V.

### (i) Gain
$A_v = \dfrac{3.3-0}{0.120-(-0.080)} = \dfrac{3.3}{0.200} = \mathbf{16.5}$

### (ii) Offset
$V_{os} = 0-16.5(-0.080) = \mathbf{1.32}$ **V**.

### (iii) Mapping
$\boxed{V_{out} = 16.5V_{in}+1.32}$, with $V_{in}$ in volts.

**Check**: $-0.08\to0$ V and $0.12\to3.30$ V ✔.

### (iv) Input of 150 mV
$V_{out} = 16.5(0.150)+1.32 = \mathbf{3.80}$ **V** $>3.3$ V, so **clipping occurs**. The ADC stores full scale, 3.3 V, which corresponds to 120 mV. Everything above 120 mV, here the extra 30 mV, is lost.

![[amc_psc_q7_range_mapping.png|650]]

### (v) Why clipping cannot be fixed digitally
- Every input from 120 mV upwards gives the same code, so the mapping cannot be inverted.
- The samples contain **no information** about how far the limit was exceeded or for how long the peak lasted.
- Filtering or interpolation can only guess, which means injecting assumptions and not recovering data.
- The fix is in hardware: a wider range mapping (lower gain) and headroom for the maximum expected input.

---

## Q8: ADC resolution (0–5 V)

### (i) 8-bit step
$Q_8 = 5/2^8 = \mathbf{19.5}$ **mV**.

### (ii) 12-bit step
$Q_{12} = 5/2^{12} = \mathbf{1.22}$ **mV**.

### (iii) Maximum rounding error
$|e_q|\le Q/2$, which gives **9.77 mV** for 8 bits and **0.610 mV** for 12 bits.

### (iv) Force resolution
$\Delta F = Q_{12}/S = 1.22\times10^{-3}/0.25 = \mathbf{4.88\times10^{-3}}$ **N** (4.88 mN per code). The maximum error is ±2.44 mN.

### (v) Low resolution as noise or jitter
- **Measurement side**: a slowly varying signal is reported as a staircase. Near a level boundary, noise makes the code flicker between adjacent values. The quantisation error looks like added noise with variance $Q^2/12$, and the D term amplifies it.
- **Command side (DAC)**: if the required steady command lies between two DAC levels, the loop keeps switching between neighbouring codes. This is **actuator hunting** or limit cycling, and it wears servos and can excite structural modes.

See [[ADC Quantisation and Resolution]].

---

## Q9: Loading effect
Given $Z_{out} = 20$ kΩ and $Z_{in} = 200$ kΩ.

### (i) Voltage ratio
$\dfrac{V_{meas}}{V_{sensor}} = \dfrac{200}{220} = \mathbf{0.909}$

### (ii) Loading error
$\varepsilon_{load} = \dfrac{20}{220} = \mathbf{9.09\%}$

### (iii) Why this is a data-integrity problem
- The measurement system **changes the quantity it is measuring**: the DAQ current flows through $Z_{out}$ and drops 9 % of the voltage.
- The error is silent, because the data look clean and plausible.
- It varies with $Z_{out}$, which may change with temperature or sensor state, so a one-off calibration will not remove it reliably.
- Every reading downstream inherits it.

### (iv) Buffer amplifier
- An op-amp **voltage follower** has a very high input impedance ($Z_{in}\to\infty$, typically MΩ to GΩ) and a very low output impedance.
- The sensor sees an almost open circuit, so $V_{meas}\approx V_{sensor}$ and the loading error tends to 0.
- The DAQ is then driven by the op-amp, not the sensor.

See [[Loading Effect and Buffering]].

---

## Q10: Sampling and aliasing
The signal has manoeuvre content up to 8 Hz and vibration near 70 Hz.

### (i) Minimum sampling frequency
$f_s>2f_{max} = \mathbf{16}$ **Hz**, to preserve 8 Hz. In practice, sample at roughly 10× that, i.e. about 80 Hz or more.

### (ii) Nyquist frequency
$f_N = 50/2 = \mathbf{25}$ **Hz**.

### (iii) Why 70 Hz cannot be represented
- 70 Hz is above $f_N = 25$ Hz: there are fewer than two samples per cycle (only 0.71 per cycle).
- A sampled sequence cannot represent any frequency above $f_N$. The samples coincide exactly with those of a lower-frequency sinusoid.

### (iv) Alias frequency
$f_{alias} = |f-mf_s|$, choosing the integer $m$ that puts the result in $[0, 25]$ Hz:

$$
|70-1\times50| = \mathbf{20\ Hz}\ (\le25\ ✔),\qquad |70-2\times50| = 30\ \text{Hz}\ (>25,\ \text{reject})
$$

The 70 Hz vibration appears as a **20 Hz ghost**. That is inside the frequency range the flight computer treats as real motion, and only 12 Hz above the manoeuvre band.

![[amc_psc_q10_aliasing.png|650]]

### (v) Why the anti-aliasing filter must be analogue and before the ADC
- Aliasing happens **at the instant of sampling**. After that, the 20 Hz alias and a genuine 20 Hz signal are identical numbers, so no digital filter can separate them.
- The high-frequency content must therefore be **physically removed while the signal is still continuous**, with an analogue low-pass satisfying $f_c\le f_N$ ($\tau = RC\ge1/(\pi f_s)$).
- Ideally the filter attenuates 70 Hz strongly while passing 8 Hz with little phase lag, which may call for a higher $f_s$ or a higher-order filter.

---

## Q11: Digital filtering

### (i) Moving-average delay
$\text{delay}\approx\dfrac{N-1}{2}T_s = \dfrac{4}{2}(0.01) = \mathbf{0.0200}$ **s**.

### (ii) Hidden assumption
The true signal $x[k]$ is **approximately constant over the window** ($NT_s = 0.05$ s), so the differences between samples are treated as noise. If the signal changes significantly within the window (fast manoeuvres, steps), the average smears and delays the real motion. It also works best for **uncorrelated** noise, and it is poor at rejecting spikes.

### (iii) Choice of $\alpha$
- **$\alpha\to1$**: trusts the current sample, so tracking is fast with almost no lag, but the estimate stays noisy (little filtering).
- **$\alpha\to0$**: trusts the previous estimate, so the output is very smooth but responds slowly. It has a long equivalent time constant and large phase lag, and it responds sluggishly to real changes.

### (iv) Value of $\alpha$
$\alpha\approx\dfrac{T_s}{\tau+T_s} = \dfrac{0.01}{0.09+0.01} = \mathbf{0.100}$

![[amc_digital_filter_tradeoff.png|700]]

---

## Q12: Differentiation, integration and data validation

### (i) Derivative amplifies noise

$$
\frac{y[k]-y[k-1]}{T_s} = \frac{x[k]-x[k-1]}{T_s}+\frac{n[k]-n[k-1]}{T_s}
$$

- The noise difference is not small: for independent samples its standard deviation is $\sqrt2\sigma_n$.
- Dividing by a small $T_s$ scales it by $1/T_s$ (×100 at $T_s = 0.01$ s).
- In frequency terms, differentiation has gain $\propto\omega$, so the **high-frequency noise is amplified most**, exactly where the useful signal has least content.

### (ii) Role of $\beta$ in the filtered derivative
$d[k] = \beta d[k-1]+(1-\beta)\frac{y[k]-y[k-1]}{T_s}$ is a recursive low-pass applied to the raw difference.
- **$\beta\to0$** gives the raw (noisy) derivative.
- **$\beta\to1$** gives a very smooth but delayed rate estimate.
- $\beta$ sets the trade-off between noise suppression and rate-estimate lag. The equivalent time constant is $\tau\approx T_s\beta/(1-\beta)$.

### (iii) Accumulated bias error
After 60 s there are $k = 60/0.01 = 6000$ steps, so

$$
\Delta I = kT_sb = 6000\times0.01\times0.02 = \boxed{1.20\ \text{units}}
$$

The error grows linearly with time, without bound.

### (iv) Drift reduction
Strategies:
- **estimate the bias during known steady conditions** (e.g. on the ground or in trimmed flight) and subtract it;
- **subtract a running baseline** or apply a **high-pass (washout)** correction;
- **reset or blend the integral with an independent reference**, e.g. a complementary filter with the accelerometer, GPS or a magnetometer.

**Risk**: drift removal assumes that slow content is error. It may also remove **genuine low-frequency motion** (a slow real climb, turn or steady rate). A bias estimate taken when the vehicle was not really stationary puts a wrong offset into every later reading.

### (v) Four data-integrity checks
1. **Clipping or saturation**: is the value stuck at a range limit?
2. **Stuck or frozen signal**: is there no variation over time, suggesting a failed sensor or stale data?
3. **Rate-limit or physical-consistency violation**: is $|y[k]-y[k-1]|>\Delta_{max}$, i.e. a change faster than physics allows?
4. **Timing**: are samples missing, late or duplicated, breaking the $T_s$ assumption?

Further checks include range checks against physical bounds and cross-checks between redundant sensors.

---

## Q13: Complementary filter for pitch
$\hat\theta[k] = \alpha\hat\theta_{gyro}[k]+(1-\alpha)\hat\theta_{acc}[k]$

### (i) Why neither sensor alone is ideal
- **Gyro**: integrating $q$ gives smooth, accurate short-term attitude, but any bias integrates into **unbounded drift** (Q12(iii)).
- **Accelerometer**: the gravity direction gives an absolute, drift-free long-term reference. But it measures **specific force**, so manoeuvre accelerations and vibration corrupt the tilt estimate, making it noisy and wrong in the short term.

### (ii) Meaning of $\alpha$
$\alpha$ sets the **crossover between the two sensors in frequency**.
- The gyro path is effectively high-passed and the accelerometer path low-passed.
- The equivalent time constant is $\tau\approx\alpha T_s/(1-\alpha)$. Below about $1/\tau$ the accelerometer is trusted; above it, the gyro.
- For example, $\alpha = 0.98$ at $T_s = 0.01$ s gives $\tau\approx0.49$ s.

### (iii) $\alpha$ too close to 1
The estimate relies almost entirely on the integrated gyro, so the accelerometer correction becomes negligible. The attitude is smooth but **drifts** away from the truth, and the correction is too weak or too slow to remove gyro bias.

### (iv) $\alpha$ too close to 0
The estimate relies mainly on the accelerometer. It is **noisy** and distorted during manoeuvres and vibration, because linear accelerations are misread as tilt. The gyro's good short-term dynamics are wasted.

### (v) Not ordinary averaging
- An ordinary average weights both estimates equally at *all* frequencies, so it inherits **both** the gyro drift and the accelerometer noise.
- The complementary filter **assigns frequency roles**: each sensor is used only in the band where it is reliable.
- The two weighting filters sum to 1, so the true signal passes undistorted while each sensor's error is rejected in its bad band.

![[amc_complementary_filter.png|650]]

See [[Complementary Filter]].

## Related
- [[SESA2027 Practice Problems 1 Solutions]] · [[SESA2027 Practice Problems 2 Solutions]] · [[SESA2027 Aerospace Mechanics & Control Hub]] · [[SESA2027 Formula Sheet]]
