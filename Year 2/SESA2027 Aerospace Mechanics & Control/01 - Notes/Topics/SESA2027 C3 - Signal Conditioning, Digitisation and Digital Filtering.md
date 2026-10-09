---
title: "SESA2027 C3 - Signal Conditioning, Digitisation and Digital Filtering"
module: "SESA2027 Aerospace Mechanics & Control"
type: topic
stream: "Part C: Sensing Systems"
order: 12
tags:
  - sesa2027
  - signal-conditioning
  - adc
  - aliasing
  - digital-filtering
aliases: ["Signal Conditioning", "Digital Bridge", "Calibration and Filtering"]
date: 2026-09-24
status: complete
parent: ["[[SESA2027 Aerospace Mechanics & Control Hub]]"]
prerequisites: ["[[SESA2027 C2 - Sensor Characteristics, Dynamics and Design]]"]
next_topics: []
key_concepts: ["[[ADC Quantisation and Resolution]]", "[[Loading Effect and Buffering]]", "[[Nyquist Sampling and Aliasing]]", "[[Digital Filtering]]", "[[Complementary Filter]]"]
tutorial_sheets: ["[[SESA2027 Part C Problem Sheet Solutions]]"]
sources: ["02 - Sources/Lectures/Lecture 3.07.pdf", "02 - Sources/Lectures/Lecture 3.08.pdf"]
---

# SESA2027 C3 - Signal Conditioning, Digitisation and Digital Filtering

> [!abstract] Summary
> The **digital bridge** turns a sensor voltage into numbers the flight computer can trust. It does this through three transformations:
> - **range**: scale and offset into the ADC window;
> - **time**: sampling at $f_s$;
> - **amplitude**: quantisation to $2^n$ levels.
>
> Information can be **destroyed** on the way by clipping, aliasing, loading and coarse resolution, and **no software can recover it**. Every stage adds **latency**, and latency eats phase margin: $\phi = -\omega T_d$. Once the samples are in memory, software can smooth them (moving average, recursive IIR), estimate rates and integrals, reject outliers (median) and fuse sensors (complementary filter). Every algorithm improves one property by spending another, usually delay.

## Key Concepts
- [[ADC Quantisation and Resolution]] · [[Loading Effect and Buffering]] · [[Nyquist Sampling and Aliasing]] · [[Digital Filtering]] · [[Complementary Filter]]

---

## 1. Hardware vs software (L3.07)

| Hardware must *preserve* | Software can *refine* |
|---|---|
| Impedance matching | Calibration |
| Scaling and offsetting | Drift correction |
| Anti-alias filtering | Digital filtering |
| Electrical protection | Sensor fusion |
| **A hardware error means lost information** | **Software cannot recover destroyed data** |

**Three transformations**: $V(t)\to V[k]\to N[k]$. Sampling changes time; quantisation changes amplitude.

## 2. Range transformation: scaling and offsetting
Typical ADC windows are 0–3.3 V (modern MCU), 0–5 V (legacy DAQ) and ±10 V (industrial DAQ). The conditioning circuit is

$$
V_{out} = A_vV_{in}+V_{os},\qquad A_v = \frac{V_{ADC,max}-V_{ADC,min}}{V_{max}-V_{min}},\qquad V_{os} = V_{ADC,min}-A_vV_{min}
$$

> [!example] Lecture example
> A sensor range of ±50 mV mapped into a 0–5 V ADC:
> - $A_v = 5/0.1 = 50$
> - $V_{os} = 0-50(-0.05) = 2.5$ V
> - so $V_{out} = 50V_{in}+2.5$.

**Clipping**: occurs if $V_{out}>V_{ADC,max}$ or $V_{out}<V_{ADC,min}$. The flat top destroys the peak information, and no algorithm can restore it.

![[amc_psc_q7_range_mapping.png|650]]

## 3. Amplitude transformation: ADC resolution
See [[ADC Quantisation and Resolution]].

$$
Q = \frac{V_{ADC,max}-V_{ADC,min}}{2^n},\qquad N[k] = \mathrm{round}\!\left(\frac{V_{out}[k]}{Q}\right),\qquad \hat V[k] = N[k]Q,\qquad |e_q|\le\frac Q2
$$

- For a 5 V range: 8 bit gives $Q = 19.5$ mV, 12 bit gives 1.22 mV, and 16 bit gives 76.3 µV.
- Datasheets define the LSB slightly differently ($2^n$ or $2^n-1$), but the principle is the same: more bits means smaller steps.

![[amc_quantisation.png|600]]

## 4. Loading effect and buffering
See [[Loading Effect and Buffering]]. The sensor's output impedance and the DAQ's input impedance form a **voltage divider**:

$$
V_{meas} = V_{sensor}\frac{Z_{in}}{Z_{out}+Z_{in}},\qquad \varepsilon_{load} = \frac{Z_{out}}{Z_{out}+Z_{in}}
$$

- Lecture example: $Z_{out} = 10$ kΩ and $Z_{in} = 100$ kΩ give $\varepsilon = 9.1\%$. That signal is lost before the computer sees anything.
- **Fix**: a **buffer amplifier** (op-amp voltage follower) with $Z_{in}\to\infty$ and a low output impedance.
- **The measurement system must not disturb the sensor.**

## 5. Time transformation: sampling and aliasing
See [[Nyquist Sampling and Aliasing]].

$$
f_s = \frac1{T_s},\qquad f_N = \frac{f_s}2,\qquad \text{no aliasing if } f_s>2f_{max},\qquad f_{alias} = |f-mf_s|\in[0,f_N]
$$

- Content above $f_N$ **folds** into the low-frequency band. The flight computer then "sees motion that is not physically there" (a ghost signal).
- **Anti-aliasing filter**: an analogue RC filter **before** the ADC, with

$$
\tau = RC\ge\frac{1}{\pi f_s}\quad\Leftrightarrow\quad f_c = \frac{1}{2\pi\tau}\le\frac{f_s}{2} = f_N
$$

- What we lose: high-frequency noise and very fast dynamics.
- What we gain: integrity in the control band.
- In practice, sample at about $10f_{max}$ (see [[SESA2027 B4 - Robustness, Stability vs Manoeuvrability and Design Process]]).

![[amc_psc_q10_aliasing.png|650]]

## 6. Latency

$$
T_d = T_{sensor}+T_{filter}+T_{ADC}+T_{buffer}+T_{processor}+T_{communication}
$$

| Term | Source |
|---|---|
| $T_{filter}$ | Analogue low-pass (larger $\tau$ means more lag) |
| $T_{ADC}$ | Conversion time |
| $T_{buffer}$ | Moving data from registers into FCC memory |
| $T_{processor}$ | Executing the control law |
| $T_{communication}$ | Bus transmission (e.g. ARINC 429) |

A pure delay $e^{-sT_d}$ has unit magnitude but phase $\phi_d(\omega) = -\omega T_d$. So

$$
\boxed{PM_{new} = PM_{old}-\omega_{gc}T_d\ (\text{rad})}
$$

Every stage of delay subtracts directly from the phase margin. See [[Gain and Phase Margins]].

## 7. DAC and zero-order hold
The **DAC** is how the computer "speaks" back. It converts $N[k]$ into $V_{cmd}$ for the actuator electronics (servo drive or valve driver). It does not move the control surface itself.

- **Zero-order hold**: the output is held constant between updates, giving a staircase command.
- **Resolution**:

$$
Q_{DAC} = \frac{V_{DAC,max}-V_{DAC,min}}{2^n},\qquad V_{cmd}[k] = V_{DAC,min}+N[k]Q_{DAC}
$$

  If the ideal steady command lies between two levels, the loop switches between neighbours. This is **actuator hunting** (jitter).

### Data-integrity checks
"A digital signal can look precise but still be physically wrong." Check for:
1. **Clipping**: stuck at the minimum or maximum, so peaks are lost.
2. **Stuck signal**: no variation at all, which means a failed sensor or frozen data.
3. **Rate-limit violation**: a change faster than the physics allows, which means noise or corruption.
4. **Timing error or missing samples**: this breaks the assumptions of a digital controller.

## 8. Digital processing after the ADC (L3.08)
**Signal model**: $y[k] = x[k]+b[k]+n[k]$.
- $x[k]$ is the truth.
- $b[k]$ is bias or drift.
- $n[k]$ is random noise.

A filter is an algorithm $\hat x[k] = F(y[k],y[k-1],\dots)$ that uses **memory** of past samples.

| Can do | Cannot do |
|---|---|
| Reduce random fluctuations | Recover clipped peaks |
| Estimate rates and accumulated quantities | Undo aliasing |
| Detect inconsistent samples | Create bandwidth that was never captured |
| Combine complementary measurements | Remove bias without assumptions |

See [[Digital Filtering]].

### Moving average (FIR)

$$
y_f[k] = \frac1N\sum_{i=0}^{N-1}y[k-i],\qquad \text{delay}\approx\frac{N-1}{2}T_s
$$

- **Hidden assumption**: the true signal is roughly constant over the window. If that is wrong, the filter distorts the motion.
- A larger $N$ gives a smoother but later output.

### Recursive low-pass (IIR)

$$
y_f[k] = \alpha y[k]+(1-\alpha)y_f[k-1],\qquad 0<\alpha<1,\qquad \alpha\approx\frac{T_s}{\tau+T_s}
$$

- Rearranged: $y_f[k]-y_f[k-1] = \alpha(y[k]-y_f[k-1])$. The estimate moves by a fraction of the current error.
- This makes the filter itself a **discrete dynamic system** in the measurement path.
- $\alpha\to1$ gives fast tracking but a noisy estimate.
- $\alpha\to0$ gives a smooth but slow estimate.
- **Choosing $\alpha$ is choosing the measurement dynamics.**

### Median filter
A median filter is robust to isolated spikes. For the window $\{1.01, 1.03, 8.50, 1.02, 1.00\}$:
- the mean is 2.512 (contaminated);
- the median is 1.02 (spike ignored).

![[amc_digital_filter_tradeoff.png|700]]

The "software tax" is visible in the figure:
- Heavier smoothing ($\alpha = 0.02$) gives a clean but badly delayed response.
- The moving average passes the spike (at 1.4 s) as a bump.
- The median rejects the spike.

### Derivatives: noise amplifiers

$$
\dot y[k]\approx\frac{y[k]-y[k-1]}{T_s} = \frac{x[k]-x[k-1]}{T_s}+\frac{n[k]-n[k-1]}{T_s}
$$

Dividing small noise differences by a small $T_s$ gives large errors. The practical fix is a **filtered derivative**:

$$
d[k] = \beta d[k-1]+(1-\beta)\frac{y[k]-y[k-1]}{T_s}
$$

This is the same reason the D term of a [[PID Controller]] needs filtering.

### Integrals: bias accumulators
$I[k] = I[k-1]+T_sy[k]$. With a constant bias $b$:

$$
I[k] = I[0]+T_s\sum_{j=1}^kx[j]+\underbrace{kT_sb}_{\text{grows with time}}
$$

Ways to reduce drift, each of which **adds an assumption**:
- estimate the bias during known steady conditions;
- subtract a running baseline;
- apply a high-pass correction;
- reset the integral using an independent reference (e.g. accelerometer or GPS).

The risk is that drift removal also removes **real low-frequency motion**.

### Outlier rejection
Flag a sample if $|y[k]-y[k-1]|>\Delta_{max}$ (the physically possible change per sample). Then hold the last valid value, interpolate, or flag the measurement invalid.

### Complementary filtering as algorithmic fusion

$$
\hat x[k] = \alpha\hat x_{fast}[k]+(1-\alpha)\hat x_{slow}[k]
$$

This assigns **frequency roles** to the two sources; it is not plain averaging. See [[Complementary Filter]] and [[SESA2027 C1 - Sensing Systems, Sensor Principles and Sensor Fusion]].

**Pipeline**: $y[k]$ → **validate** → **filter** → **estimate** → $\hat x[k]$.

> [!important] Final message
> Digital processing can make measurements more useful, but **every improvement encodes an assumption**. For flight control the question is not "is the signal smoother?" but "**is the processed signal still truthful enough for feedback?**"

## Links
- Parent: [[SESA2027 Aerospace Mechanics & Control Hub]] · Previous: [[SESA2027 C2 - Sensor Characteristics, Dynamics and Design]]
- Robustness and noise: [[SESA2027 B4 - Robustness, Stability vs Manoeuvrability and Design Process]]
- Worked problems: [[SESA2027 Part C Problem Sheet Solutions]] (Q7–Q13)

## Sources
- Lectures 3.07–3.08 (Prof A. Cammarano)
- Bentley, *Principles of Measurement Systems*, Ch. 9–10
