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
status: lectured
coverage: "L3.04 (universal limitations), L3.05 (sensors as dynamic systems), L3.06 (sensor design; slides only)"
parent: ["[[SESA2027 Aerospace Mechanics & Control Hub]]"]
prerequisites: ["[[SESA2027 C1 - Sensing Systems, Sensor Principles and Sensor Fusion]]", "[[SESA2027 A4 - Laplace Transforms, Transfer Functions and Step Response]]", "[[SESA2027 A5 - Frequency Response and Bode Plots]]"]
next_topics: ["[[SESA2027 C3 - Signal Conditioning, Digitisation and Digital Filtering]]"]
key_concepts: ["[[Accuracy and Precision]]", "[[Sensor Dynamic Models]]", "[[Step Response Specifications]]", "[[Bode Plot]]"]
tutorial_sheets: ["[[SESA2027 Part C Problem Sheet Solutions]]"]
sources: ["02 - Sources/Lectures/Lecture 3.04.pdf", "02 - Sources/Lectures/Lecture 3.05.pdf", "02 - Sources/Lectures/Lecture 3.06.pdf", "02 - Sources/Lectures/Lecture 3.04 recording.txt", "02 - Sources/Lectures/Lecture 3.05-3.06 recording.txt"]
---

# SESA2027 C2 - Sensor Characteristics, Dynamics and Design

> [!abstract] Summary
> Every sensor is bounded (range, saturation), corrupts the signal (bias and noise) and is not instantaneous (lag and phase shift). A sensor is itself a dynamic system, so it is modelled with the Part A tools as zeroth order ($y = Ku$), first order ($K/(\tau s+1)$) or second order ($K\omega_n^2/(s^2+2\zeta\omega_ns+\omega_n^2)$) and judged by its step response and Bode plot. Design means matching the sensor's bandwidth to the aircraft's dynamics, choosing $\zeta\approx0.7$ for second-order sensors, trading noise against lag when filtering, and placing sensors sensibly on the airframe.

> [!summary]- Exam use: quick path
> - **Use it when:** a question gives a sensor's order and parameters ($K$, $\tau$, or $\omega_n$ and $\zeta$) and asks for its step-response metrics, its reading at a given frequency, the RC cut-off and attenuation in dB, or a choice of sensor/damping; or asks to distinguish accuracy from precision.
> - **Assumptions:** linear sensor inside its operating range (nonlinear behaviour is not examined, L3.05, l. 229); first-order $K/(\tau s+1)$ or second-order $K\omega_n^2/(s^2+2\zeta\omega_ns+\omega_n^2)$; settling to 1 %.
> - **Method:** 1. Classify the order for the frequency of interest. 2. First order: 63.2 % at $\tau$, $t_r=2.2\tau$, $t_s=4.6\tau$, $f_c=1/(2\pi\tau)$. 3. Second order: $t_r\approx1.8/\omega_n$, $t_s\approx4.6/(\zeta\omega_n)$ (underdamped only), $OS=100e^{-\zeta\pi/\sqrt{1-\zeta^2}}$ %. 4. At frequency $\omega$: $\lvert G\rvert/K=1/\sqrt{(1-r^2)^2+(2\zeta r)^2}$ with $r=\omega/\omega_n$. 5. Pick $\omega_n$ well above the signal and $\zeta\approx0.7$.
> - **Common mistakes:** using $4.6/(\zeta\omega_n)$ for an overdamped sensor (it under-predicts); calling a bias a precision problem (bias is accuracy; noise is precision).
> - **Practise:** [[#Worked example: choosing an accelerometer]] · [[SESA2027 Mock Questions#Q11. Second-order sensor design|Mock Q11]] · [[SESA2027 Part C Problem Sheet Solutions]] (Q4–Q6)

A sensor is a small dynamic system bolted onto a big one. A thermocouple has to warm up before it reads the new temperature: first-order lag. An accelerometer is a tiny mass on a spring: it rings if it is lightly damped and lags if it is heavily damped. A strain gauge, for most purposes, just follows: zeroth order. All the Part A tools apply unchanged: poles, step response, Bode plot.

What matters is the sensor's speed relative to the signal. Well below its corner or natural frequency a sensor is transparent; near it, it distorts; above it, it is blind and late. Lag is the dangerous part for control, because a late measurement is a phase lag inside the loop, and phase lag eats the margins from B3. Every fix trades something: filtering removes noise but adds lag, a stiffer accelerometer is faster but less sensitive, heavier damping removes overshoot but adds delay. The engineering compromise for second-order sensors is $\zeta\approx0.7$, where the magnitude stays flattest and the delay is nearly the same at all frequencies.

---

## 1. Universal limitations (L3.04)
"No sensor is a perfect window to reality." Every sensor:
1. **is bounded**: it measures only within physical limits;
2. **corrupts the signal**: noise, offsets, environmental sensitivity;
3. **is not instantaneous**: physics takes time, so the signal is always delayed.

The lecturer singled out two of these as the hardest (L3.04, ll. 67–139). At design time it is the range: you must know in advance what the system will do, and "the operational range doesn't listen to you", so out-of-range events will happen and the job is to decide which are tolerable and guard against the catastrophic ones. In operation it is the time lag: "that time lag has the capability to move your poles. And moving the poles, it can destabilize the entire system." A loop that is stable with a perfect sensor can go unstable because the correction arrives late and feeds the oscillation instead of damping it.

### Accuracy vs precision
See [[Accuracy and Precision]].

| | Accuracy | Precision (repeatability) |
|---|---|---|
| Meaning | How close the mean is to the true value | How tightly repeated readings cluster |
| Lost through | Systematic error (bias/offset) | Random error (noise) |
| Aircraft example | IMU reads +2° pitch when level | GPS jumps within 5 m when stationary |
| Control impact | Steady-state deviation: the autopilot "levels" to the wrong attitude, causing altitude drift or a skewed approach | Actuation jitter: the controller chases noise, causing servo wear, extra energy use and excited structural modes |
| Fix (L3.04, ll. 161–214) | Offset / recalibration: shift the cloud of readings back. Drifting sensors (gyros) need frequent recalibration, which in an IMU is done by another sensor | Filtering: "even the average is a type of filtering" |

> [!example] Lecturer's examples (L3.04, ll. 187–207)
> - **Bias**: an IMU with a constant 2° pitch bias on landing makes the control system assume the wrong drag and braking capability, so the aircraft may need much more runway than predicted.
> - **Noise**: a GPS altitude that jitters within a 5 m radius makes the controller chase altitude changes that never happened: a rough ride, overworked actuators and wasted fuel.

### Range, sensitivity and saturation
- Span = upper limit − lower limit. Example: a 5–100 PSI sensor has a 95 PSI span.
- **Operating range**: the part of the span where the output is linear.
- **Sensitivity**: the slope, $S = \Delta V/\Delta P$.
- **Saturation**: beyond the limits the output stops being proportional, and at saturation $S = 0$ (the sensor is "blind").
  - *Physical limit*: the diaphragm or spring reaches maximum displacement.
  - *Electrical limit*: the amplifier hits its voltage rails. This is usually in the conditioning, not the sensor.
- **Clipping**: peak information is lost. It is often designed in deliberately, before the sensor itself saturates.
- Dead zone (L3.04, ll. 230–249): at the low end many sensors have a region of zero slope where they do not respond at all. A small but non-zero slope can be corrected by adjusting the sensitivity; a zero slope cannot. Typical conditioning rails are ±5 V or ±10 V (ll. 263–268).

### Noise and SNR
- **Sources**:
  - thermal noise (random electron motion);
  - EMI from motors, radios and power lines;
  - quantisation noise from the ADC. The lecturer's picture (L3.04, ll. 326–336): with bins 2–2.5 V and 2.5–3 V, a 2.3 V signal is recorded only as "somewhere in the 2–2.5 V box", and the lost detail behaves like noise. It is quantified in [[SESA2027 C3 - Signal Conditioning, Digitisation and Digital Filtering|C3]].
- **SNR**: signal strength relative to noise. Below the noise floor, a signal cannot be distinguished.

Time-domain statistics (N readings at constant input):

$$
\mu = \frac1N\sum_{i=1}^Nx_i,\qquad \sigma^2 = \frac{1}{N-1}\sum_{i=1}^N(x_i-\mu)^2
$$

- $\mu\neq0$ means bias (an accuracy problem).
- $\sigma$ is the spread (a precision problem).
- For Gaussian noise, 95 % of readings fall within $\pm2\sigma$.

**Frequency-domain view**:
- Take the Fourier transform of the reading of a constant input.
- White noise has equal power at all frequencies.
- Real sensors show band-limited white noise: flat up to the sensor bandwidth, then rolling off, often with EMI spikes (e.g. motor harmonics).

> [!info] Practical noise points (L3.04)
> - UK mains is 230–240 V at 50 Hz, and its field is picked up by "almost every single possible measurement chain". Expect a 50 Hz spike in lab accelerometer spectra (ll. 293–318).
> - Wi-Fi at 2.4 GHz is many orders of magnitude above aircraft dynamics (a few Hz or less), so low-pass filtering removes it. Only noise inside the band you need to measure is a real problem (ll. 433–475).
> - To characterise noise, hold the measured quantity constant with a trusted reference, record many readings, then take the mean (bias) and standard deviation (precision) (ll. 399–421).
> - As a rule of thumb, the bigger the object, the lower its natural frequencies. A bridge is around 1–5 Hz, aircraft rigid-body modes are a fraction of a hertz, and a MEMS microstructure can be in the MHz range (ll. 451–457).

### Time lag and phase shift
Physical causes:
- thermal inertia (a thermocouple must heat up);
- mechanical/fluid inertia (air in pitot tubing moving a diaphragm);
- signal conditioning (low-pass filters slow the signal on purpose).

- **Time constant $\tau$**: the time to reach 63.2 % of the final value after a step. Piezo accelerometers have a small $\tau$; fluid thermometers a large one.
- Under oscillatory input, the lag appears as a phase shift, and it grows with frequency.

Lag isn't always unwanted (L3.05–3.06 recording, ll. 26–95). Small thermal sensors respond faster and large ones lag, but that thermal inertia is also natural filtering, and it can protect the sensor from damaging temperature peaks when only the average is wanted. Data acquisition adds delay even before any filter, because one processor scans several input channels in turn and reads each only once per scan. Note that a constant time delay and a frequency-dependent phase shift are different things; the first- and second-order models describe the second.

The pattern runs through the whole of Part C: improving one characteristic usually worsens another, and reducing noise increases delay.

## 2. Sensors as dynamic systems (L3.05)
- A sensor has mass, inertia, friction and electromagnetic dynamics. Its output depends on the current input and its history.
- In Part A we neglected sensor dynamics (DAP3). Here we put them back.

**State-space model**:

$$
\dot{\mathbf x} = \mathbf A\mathbf x+\mathbf Bu,\quad y = \mathbf C\mathbf x+\mathbf Du
$$

- $u$ is the aircraft state being measured.
- $\mathbf x$ is the internal sensor state (diaphragm displacement, voltage, ...).
- $y$ is the reported signal.

The ideal sensor would have an output that depends only on the input, $y = Ku$, and not on any internal state (L3.05, ll. 145–224). No real sensor achieves this everywhere, but many do within their linear regime; outside it a sensor needs the general form $\dot{\mathbf x} = \mathbf f(\mathbf x, u)$, which can contain terms such as $\sin x$ or $x^2$. Fast signals break the ideal because a fast-changing input means large accelerations of the sensor's own moving parts, and by $F = ma$ the forces needed to follow it become large, so the sensor's inertia shows up as lag: "the faster you go, the more difficult is to have sensors that actually are transparent."

The internal matrices are hard to find. So in practice we treat the sensor as a black box, $G(s) = Y(s)/U(s)$, and identify it experimentally. Sine sweeps or broadband noise are fed through a spectrum analyser, which gives the Bode magnitude and phase directly. See [[Transfer Function]] and [[Frequency Response Function]].

The choice of identification input matters (L3.05–3.06 recording, ll. 356–412). A sine gives one frequency, so one point of $G(i\omega)$ per test. An impulse or step excites all frequencies but gives only one record, and the step's corner, with its infinite slope, is exactly where a lagging sensor loses the signal (ll. 413–419). White noise has a flat spectrum that excites everything at once and can be averaged over many records, so it is preferred for sensor characterisation; a good spectrum analyser costs around £10 000. Substituting $s = i\omega$ in the Laplace-domain $G(s)$ then gives the frequency response, since "$s$ is a frequency in disguise" (ll. 331–344).

> [!info] Nonlinear sensors are not examined (L3.05, ll. 226–236)
> Outside the linear range a sensor can show bifurcations and sensitivity to initial conditions, which is why designs keep it in the linear regime. "This is not covered in the exam, don't worry."

### Three model orders (DAP2, Occam's razor)
See [[Sensor Dynamic Models]].

| Order | Model | Examples | Character |
|---|---|---|---|
| 0th | $y = Ku$ | Strain gauge, potentiometer, LVDT, thermistor (ignoring thermal mass), squat switch | Instantaneous, no lag; $K$ is the sensitivity |
| 1st | $\tau\dot y+y = Ku$, i.e. $\dfrac{K}{\tau s+1}$ | Thermocouple/temperature probe, pressure sensor with long lines, pitot-static, float fuel gauge | Exponential lag set by $\tau$ |
| 2nd | $\ddot y+2\zeta\omega_n\dot y+\omega_n^2y = K\omega_n^2u$ | Accelerometer, rate gyro, pressure diaphragm, AoA vane, IMU | Mass–spring–damper: overshoot or sluggishness depending on $\zeta$ |

![[amc_sensor_order_step.png|650]]

The model order depends on the signal as well as the sensor (L3.05, ll. 431–464). The same temperature sensor can be zeroth order for a slowly varying temperature and first order for a fast one: "tell me … what frequency you want to measure, and [I'll] tell you how to model that system". A strain gauge is zeroth order for a bridge at 1 Hz or a wing at 10 Hz, but not at MHz.

Why the second-order sensor has $\omega_n^2$ on the right: a base-excited mass–spring–damper (L3.05, ll. 498–514). Take an accelerometer: proof mass $m$ on a spring $k$ and damper $c$ inside a case that moves with acceleration $a(t)$. Let $z$ be the displacement of the mass relative to the case. Newton's second law for the mass, in the inertial frame:

$$
m(\ddot z+a) = -c\dot z-kz
$$

Rearrange:

$$
m\ddot z+c\dot z+kz = -ma
$$

Divide by $m$ and use $\omega_n^2 = k/m$, $2\zeta\omega_n = c/m$:

$$
\ddot z+2\zeta\omega_n\dot z+\omega_n^2z = -a
$$

$$
\ddot z+2\zeta\omega_n\dot z+\omega_n^2z = \omega_n^2\left(-\frac{1}{\omega_n^2}\right)a
$$

This is the course form $\ddot y+2\zeta\omega_n\dot y+\omega_n^2y = K\omega_n^2u$ with $y = z$, $u = a$ and $K = -1/\omega_n^2$. At low frequency $\ddot z$ and $\dot z$ are negligible, so $z\approx-a/\omega_n^2$: the deflection is proportional to the acceleration. That is the lecturer's "elastic force dominates below resonance" argument (ll. 562–577): inertial forces grow as $\omega^2$, so below $\omega_n$ the spring term wins and the sensor reads correctly.

> [!note] A consequence not stated in the lecture
> With $K = -1/\omega_n^2$, raising $\omega_n$ for more bandwidth also reduces the static sensitivity (less deflection per $g$). That is the basic accelerometer trade-off between bandwidth and sensitivity.

### Time-domain metrics
The metrics are the same as in [[SESA2027 A4 - Laplace Transforms, Transfer Functions and Step Response]]:

$$
t_r\approx\frac{1.8}{\omega_n},\qquad t_s\approx\frac{4.6}{\zeta\omega_n}\ (1\%),\ \frac{3}{\zeta\omega_n}\ (5\%),\qquad OS = 100\,e^{-\zeta\pi/\sqrt{1-\zeta^2}}\ \%
$$

The 4.6 comes from $\ln0.01\approx-4.6$, and the 3 from $\ln0.05\approx-3.0$. The second-order formulas are derived in [[SESA2027 A4 - Laplace Transforms, Transfer Functions and Step Response#Deriving the specifications|A4]]; they hold for underdamped sensors only.

First-order step response, line by line (assumptions: $\tau\dot y+y=Ku$, unit step $u=1$ at $t=0$, $y(0)=0$). Laplace transform:

$$
(\tau s+1)Y(s)=\frac Ks\quad\Rightarrow\quad Y(s)=\frac{K}{s(\tau s+1)}=K\left(\frac1s-\frac{\tau}{\tau s+1}\right)=K\left(\frac1s-\frac{1}{s+1/\tau}\right)
$$

$$
y(t)=K\left(1-e^{-t/\tau}\right)
$$

- At $t=\tau$: $y=K(1-e^{-1})=0.632K$, the 63.2 % definition of the time constant.
- 10 % at $t_{10}=-\tau\ln0.9=0.105\tau$ and 90 % at $t_{90}=-\tau\ln0.1=2.303\tau$, so $t_r=2.2\tau$.
- Within 1 % when $e^{-t/\tau}=0.01$: $t_s=4.6\tau$ (5 %: $3\tau$).
- No overshoot, ever: a first-order sensor only lags.

In the frequency domain the same sensor has $\lvert G\rvert=K/\sqrt{1+(\omega\tau)^2}$ and phase $-\tan^{-1}(\omega\tau)$. For $\omega\tau\ll1$ the phase is $\approx-\omega\tau$, which is a pure time delay of $\tau$: well inside its bandwidth, a first-order sensor reports the signal about $\tau$ seconds late.

> [!warning] The second-order rules fail for overdamped sensors
> For $\omega_n=50$ rad/s (computed by simulation): $\zeta=0.3$ gives $t_r=0.026$ s, $OS=37\,\%$, $t_s=0.286$ s (rule 0.307 s); $\zeta=0.7$ gives $t_r=0.043$ s, $OS=4.6\,\%$, $t_s=0.131$ s (rule 0.131 s); $\zeta=1.2$ gives $t_r=0.087$ s, no overshoot, $t_s=0.184$ s, while the rule $4.6/(\zeta\omega_n)$ gives 0.077 s, less than half. Above $\zeta=1$ one real pole moves towards the origin and slows the response; the envelope argument behind $4.6/(\zeta\omega_n)$ no longer applies. $1.8/\omega_n=0.036$ s is a fair rise-time estimate only near $\zeta\approx0.5$.

- **Measurement lag**:
  - none for 0th-order sensors;
  - set by $\tau$ for 1st-order sensors;
  - for 2nd-order sensors, a higher $\omega_n$ reduces lag and a higher $\zeta$ increases it.
- Overshoot gives a false peak. The sensor reports, say, a $q$ larger than reality, which could trigger an aggressive and unnecessary response from the flight control computer.

### Frequency-domain view
- **Low frequency**: the sensor is "transparent"; the output is the input scaled by $K$.
- Near $\omega_n$ (2nd order, low $\zeta$): resonance gives false high readings.
- **High frequency**: the output is attenuated towards zero, and the phase lag grows. Phase lag is critical for loop stability.

Frequency-dependent sensor lag is distinct from frequency-independent delays (digitisation, storage, buses). Those are covered in [[SESA2027 C3 - Signal Conditioning, Digitisation and Digital Filtering]].

## 3. Sensor system design (L3.06)
### Requirements
- **Range with margin**. For example, a maximum pitch rate of ±20 °/s calls for a gyro range of about ±30 °/s.
- **Resolution**: the smallest detectable change.
- Accuracy (static error).
- **Dynamic requirements**:
  - **bandwidth**: accurate magnitude and phase over the frequencies of interest;
  - maximum allowable lag before old data compromises closed-loop stability.

### Selecting the order

| Order | Design strategy | Primary challenge | Impact on the control loop |
|---|---|---|---|
| 0th | Assume $y = Ku$ | No natural smoothing; sensitive to noise, EMI and temperature | Noise → actuator jitter and control effort |
| 1st | Minimise $\tau$: make it well below the airframe's response time | Lag and phase delay | Delayed feedback → reduced stability margins |
| 2nd | High $\omega_n$, then tune $\zeta$ | Overshoot and resonance | Signal distortion → aggressive or misleading control action |

### Optimal damping for second-order sensors

| $\zeta$ | Behaviour | Risk |
|---|---|---|
| $<0.5$ (underdamped) | Fast, large overshoot | False peaks; massive over-reading if the input frequency is near $\omega_n$ |
| $\approx0.7$ | Fastest settling with about 5 % overshoot; flattest magnitude (no resonant peak for $\zeta\ge0.707$) | Engineering optimum |
| $>1$ (overdamped) | No overshoot, sluggish | Large lag: "old" data, reduced margins |

![[amc_psc_q5_damping_tradeoff.png|700]]

**Why about 0.7: flat magnitude and constant delay.** At frequency ratio $r=\omega/\omega_n$ the normalised reading is

$$
\frac{\lvert G\rvert}{K}=\frac{1}{\sqrt{(1-r^2)^2+(2\zeta r)^2}}
$$

Expand the denominator: $(1-r^2)^2+4\zeta^2r^2=1-2(1-2\zeta^2)r^2+r^4$. The $r^2$ term, which is what first pulls the reading away from 1, vanishes when $1-2\zeta^2=0$, i.e. $\zeta=1/\sqrt2=0.707$. Then $\lvert G\rvert/K=1/\sqrt{1+r^4}$, which stays within 2 % up to $r=0.47$ (the "maximally flat" or Butterworth choice). A slightly lower $\zeta\approx0.65$ lets the curve rise a little before it falls and stretches the ±2 % band to $r=0.64$.

The phase is $\phi=-\tan^{-1}\left(2\zeta r/(1-r^2)\right)$. For small $r$, $\phi\approx-2\zeta r=-(2\zeta/\omega_n)\,\omega$: a phase proportional to frequency is a pure time delay of $2\zeta/\omega_n$. Near $\zeta=0.7$ this stays nearly true up to $r\approx1$, so every frequency in the signal is delayed by about the same time and the waveform keeps its shape. Light damping delays low and high frequencies differently, which distorts the measured waveform.

![[amc_sensor_usable_bandwidth.png|760]]

### Worked example: choosing an accelerometer

*(Suggested, not lecturer-set.)* An accelerometer with $f_n=100$ Hz must measure a 20 Hz vibration, so $r=0.2$.

- $\zeta=0.7$: $\lvert G\rvert/K=1/\sqrt{(1-0.04)^2+(0.28)^2}=1/\sqrt{0.9216+0.0784}=1.000$. Phase $-\tan^{-1}(0.28/0.96)=-16.3°$, a delay of $16.3/(360\times20)=2.26$ ms, close to $2\zeta/\omega_n=1.4/628.3=2.23$ ms.
- $\zeta=0.3$: $\lvert G\rvert/K=1/\sqrt{0.9216+0.0144}=1.034$, a 3.4 % over-reading. The delay is only 0.99 ms, but it now varies with frequency.
- Requirement check: to keep a 20 Hz signal within ±2 % at $\zeta=0.7$, need $r\le0.47$, so $f_n\ge20/0.47=43$ Hz. The 100 Hz sensor has margin.

> [!check] Numerical check (Python)
> The amplitude ratios and phases above were recomputed directly from $G(i\omega)$ in Python. The ±2 % limits $r=0.16$ ($\zeta=0.3$), $0.47$ ($\zeta=0.7$) and $0.14$ ($\zeta=1.0$) are read from the same calculation as the figure.

### Placement and interference
- **Aerodynamic**: pitot tubes and AoA vanes must sit in clean flow, away from the fuselage boundary layer and wing downwash, so that $K$ stays constant.
- **Structural**: mount the IMU near the CG. Otherwise wing and fuselage bending modes are mistaken for rigid-body motion.
- **EMI**: shield sensors from power cables, igniters and radio transmitters.
- **Noise sources**:
  - mechanical (engine or rotor vibration, turbulence);
  - electrical (thermal jitter, digitisation).
  - The goal is an SNR high enough that the noise floor never masks a real manoeuvre.

### Bode view and the RC filter
- **Magnitude plot**: shows where the sensor is transparent, where it attenuates and where it resonates.
- **Phase plot**: shows the lag directly. Excessive phase lag at crossover can cause instability or pilot-induced oscillation (PIO).

First-order RC low-pass filter (hardware, placed before the ADC):

$$
G_{filter}(s) = \frac{1}{\tau s+1},\qquad \tau = RC,\qquad \omega_c = \frac1\tau,\quad f_c = \frac{1}{2\pi\tau}
$$

At $\omega_c$: $|G| = 1/\sqrt2$ (−3 dB) and the phase is −45°. Above it, the magnitude falls at −20 dB/dec.

![[amc_psc_q6_rc_filter_bode.png|600]]

**The noise vs lag conflict**:
- A large $\tau$ gives a clean but late signal and a sluggish loop.
- A small $\tau$ gives a fast signal, but noise reaches the actuators, causing wear and jitter.
- Choose $f_c$ high enough not to destabilise the airframe, and low enough to block damaging vibration.

> [!note] L3.06 is not in the recording
> The file `Lecture 3.05-3.06 recording.txt` stops at the 10-minute break after the L3.05 material (ll. 636–638). Section 3 is therefore from the slides only, apart from the points the lecturer pulled forward into L3.05: push $\omega_n$ well above the measurement band (ll. 519–581) and the lag–overshoot trade-off of $\zeta$ (ll. 610–634). He warned that the material is "a little bit scrambled in between the two lectures" and that the figures are in the other slide set (ll. 524–525, 583–585).

## Lecturer emphasis and exam hints (transcripts)

> [!info] Signals in L3.04–L3.05
> - "This helps you also to answer questions at the exam": know that the transfer function is the output/input ratio in the $s$-domain and how to get the frequency response from it (L3.05, ll. 309–344).
> - Nonlinear sensor behaviour is not examined (L3.05, l. 229).
> - The quantities here are used in the following week's laboratory; Python scripts for the time-domain metrics were promised (L3.04, ll. 54–56; L3.05, ll. 605–608).
> - Filtering of noise has its own lecture (L3.04, ll. 212–214): see [[SESA2027 C3 - Signal Conditioning, Digitisation and Digital Filtering]].

## Transcript slips

> [!warning] Speech-to-text and spoken slips, with the correct version
> | Where | Transcript says | Correct |
> |---|---|---|
> | L3.04, l. 11 | "the CISO 2027" | SESA2027 |
> | L3.04, l. 82 | (student) "it limits the operational and political system" | the operational range (the lecturer's reply, ll. 83–85) |
> | L3.04, l. 118 | garbled speech-to-text ("nothing about 그림 not UN") | the student's answer is lost; the lecturer's point follows at ll. 128–139 |
> | L3.04, l. 167 | (student) "you do an offset for lack of precision" | an offset corrects accuracy; filtering corrects precision (ll. 185–186) |
> | L3.04, ll. 188–191 | "if you are lending … drug … the runaway" | landing, drag, runway |
> | L3.04, l. 361 | "the mean defined where your noise floor is" | the mean measures the bias; the noise floor is set by the noise level ($\sigma$) |
> | L3.04, ll. 386–390 | "the real value of the signal is within the two sigma of the mean" | for Gaussian noise about 95 % of readings lie within $\pm2\sigma$ of the mean; a non-zero mean error (bias) is not removed by this |
> | L3.05, l. 67 | "a load pass filter" | low-pass filter |
> | L3.05, l. 70 | "a data queue" | a DAQ (data-acquisition system) |
> | L3.05, l. 122 | "the mayor quantity" | the measured quantity |
> | L3.05, l. 343 | "S equals J omega" | $s = i\omega$ in this course's notation |
> | L3.05, ll. 347–354 | Laplace and Fourier as French army generals; "Fourier transform and Laplace transform are the same thing" | the anecdote is not historically accurate (neither was an army general). The transforms are related, not identical: the Fourier transform is the Laplace transform evaluated on $s = i\omega$, where that exists |
> | L3.05, ll. 396–397 | "Good plot … the both plots" | Bode plots |
> | L3.05, l. 429 | "rate, sorry, there is a typo here" | the lecturer saw a typo on the order-classification slide; the filed slide 13 has "Frist order" for "First order" |
> | L3.05, l. 458 | "potentiometer LBDT" | LVDT |
> | L3.05, ll. 467–470 | first-order sensors "respond both to the input and to the rate of change in the input … the output … depends on the input and its derivative" | in $\tau\dot y+y = Ku$ it is the output and its rate that depend on the input; the input's derivative does not appear |
> | L3.05, l. 480 | "2 omega zeta omega zeta omega n y dot" | $2\zeta\omega_n\dot y$ |
> | L3.05, ll. 518, 548, 621 | "dumping ratio", "dumping force" | damping |
> | L3.05, l. 610 | "when you have Inesha" | inertia |
> | L3.05, ll. 630–631 | overshoot "minus zeta pi over 1 minus zeta squared multiplied 100" | $OS = 100\,e^{-\zeta\pi/\sqrt{1-\zeta^2}}$: do not drop the square root (the same slip as the PS1 Q3 answer, see [[SESA2027 A4 - Laplace Transforms, Transfer Functions and Step Response#4. Time-domain specifications\|A4 §4]]) |

## Terminology and alternative names

| Course term | Also called | Where the course uses it | Note |
|---|---|---|---|
| accuracy | trueness; lost through systematic error | L3.04 | |
| precision | repeatability; lost through random error | L3.04 | |
| span | full-scale range (FSR) | L3.04 | |
| operating range | linear range | L3.04 | |
| sensitivity $S$ or $K$ | gain, scale factor, static sensitivity | L3.04, L3.05 | |
| dead zone | dead band, threshold | L3.04 | |
| noise floor | resolution limit, minimum detectable signal | L3.04 | |
| zeroth / first / second-order sensor | static / first-order lag / second-order (seismic) instrument | L3.05 slide 13 | slide typo "Frist order" |
| time constant $\tau$ (63.2 %) | lag time | L3.04 | |
| black-box model | empirical transfer function, system identification | L3.05 | |
| base-excited mass–spring–damper | seismic instrument, seismic mass | L3.05 | |
| optimal damping $\zeta\approx0.7$ | maximally flat (Butterworth) damping | L3.06 | |
| RC low-pass filter | first-order anti-aliasing filter | L3.06 | |
| pilot-induced oscillation (PIO) | aircraft–pilot coupling (APC) | L3.06 | |

## Links
- Parent: [[SESA2027 Aerospace Mechanics & Control Hub]] · Previous: [[SESA2027 C1 - Sensing Systems, Sensor Principles and Sensor Fusion]] · Next: [[SESA2027 C3 - Signal Conditioning, Digitisation and Digital Filtering]]
- Concepts: [[Accuracy and Precision]] · [[Sensor Dynamic Models]] · [[Step Response Specifications]] · [[Bode Plot]]
- Same maths as the aircraft: [[SESA2027 A4 - Laplace Transforms, Transfer Functions and Step Response]], [[SESA2027 A5 - Frequency Response and Bode Plots]]
- Worked problems: [[SESA2027 Part C Problem Sheet Solutions]] (Q4–Q6)

## Year 1 foundation
- An accelerometer is the SDOF oscillator of [[FEEG1002 D6 - Single Degree of Freedom Vibration]], used below resonance.
- The static vocabulary (sensitivity, resolution, precision, accuracy) and the RC filter first appear in [[FEEG1004 E1 - Measurement Systems and Temperature Sensors]] and [[FEEG1004 D3 - AC Filters and Bode Plots]].

## Sources
- Lectures 3.04–3.06 (Prof A. Cammarano): slides `Lecture 3.04.pdf`–`Lecture 3.06.pdf`
- Transcripts (speech-to-text): `Lecture 3.04 recording.txt`, `Lecture 3.05-3.06 recording.txt` (covers L3.05 only; it ends at the break)
- Bentley, *Principles of Measurement Systems*, Ch. 2–4
- Figures: `01 - Notes/Figures/generate_amc_c2_figures.py`

## Self-study tasks

No tasks were set in the L3.04–L3.05 recordings (the Python scripts were for exploration), and L3.06 is not recorded. Knowing that the transfer function is the output/input ratio and how to get the frequency response from it was flagged as exam-relevant (L3.05, ll. 309–344). Every task below is suggested, not lecturer-set.

### Core

- [ ] Derive $y=K(1-e^{-t/\tau})$ and from it the 63.2 %, $t_r=2.2\tau$ and $t_s=4.6\tau$ results. → [[#Time-domain metrics]]
- [ ] For a second-order sensor with $\omega_n = 50$ rad/s, compare $t_r$, $t_s$ (1 %) and $OS$ for $\zeta = 0.3$, $0.7$ and $1.2$. → [[#Time-domain metrics]]
- [ ] Choose $f_n$ and $\zeta$ for an accelerometer that must read a 20 Hz vibration within 2 %. → [[#Worked example: choosing an accelerometer]]
- [ ] Explain why the step is a poor input for identifying a sensor's transfer function. → [[#2. Sensors as dynamic systems (L3.05)]]
- [ ] Part C sheet Q4–Q6. → [[SESA2027 Part C Problem Sheet Solutions]]
- [ ] Mock exam question. → [[SESA2027 Mock Questions#Q11. Second-order sensor design|Mock Q11]]

### Further practice

- [ ] Derive the base-excited accelerometer equation and show $K = -1/\omega_n^2$. → [[#Three model orders (DAP2, Occam's razor)]]
- [ ] Show that $\zeta=1/\sqrt2$ removes the $r^2$ term of the magnitude and that the low-frequency delay is $2\zeta/\omega_n$. → [[#Optimal damping for second-order sensors]]
