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
status: lectured
coverage: "L3.07 (digital bridge: conditioning, ADC, sampling, latency, DAC), L3.08 (digital processing); slides only, no recordings"
parent: ["[[SESA2027 Aerospace Mechanics & Control Hub]]"]
prerequisites: ["[[SESA2027 C2 - Sensor Characteristics, Dynamics and Design]]"]
next_topics: []
key_concepts: ["[[ADC Quantisation and Resolution]]", "[[Loading Effect and Buffering]]", "[[Nyquist Sampling and Aliasing]]", "[[Digital Filtering]]", "[[Complementary Filter]]"]
tutorial_sheets: ["[[SESA2027 Part C Problem Sheet Solutions]]"]
sources: ["02 - Sources/Lectures/Lecture 3.07.pdf", "02 - Sources/Lectures/Lecture 3.08.pdf"]
---

# SESA2027 C3 - Signal Conditioning, Digitisation and Digital Filtering

> [!abstract] Summary
> The digital bridge turns a sensor voltage into numbers the flight computer can trust through three transformations: range (scale and offset into the ADC window), time (sampling at $f_s$) and amplitude (quantisation to $2^n$ levels). Clipping, aliasing, loading and coarse resolution destroy information that no software can recover, and every stage adds latency, which costs phase margin as $\phi = -\omega T_d$. Once the samples are in memory, software can smooth, differentiate, integrate, reject outliers and fuse sensors, but every algorithm improves one property by spending another, usually delay.

> [!summary]- Exam use: quick path
> - **Use it when:** a question gives a sensor range and an ADC window and asks for gain, offset, clipping or resolution; gives impedances and asks for the loading error; gives a signal and sampling frequencies and asks for the alias or the anti-alias RC; gives a latency and a crossover and asks for the phase-margin loss; or asks for the delay, smoothing or failure mode of a digital filter.
> - **Assumptions:** linear conditioning $V_{out}=A_vV_{in}+V_{os}$; ideal $n$-bit ADC with $Q=\text{range}/2^n$; first-order RC anti-alias filter; pure delay $e^{-sT_d}$ for latency; white measurement noise.
> - **Method:** 1. $A_v=\Delta V_{ADC}/\Delta V_{sensor}$, $V_{os}=V_{ADC,min}-A_vV_{min}$; check the extremes for clipping. 2. $Q=\text{range}/2^n$, error $\le Q/2$. 3. Loading $\varepsilon=Z_{out}/(Z_{out}+Z_{in})$. 4. $f_{alias}=\lvert f-mf_s\rvert$ folded into $[0,f_s/2]$; RC with $f_c\le f_s/2$. 5. $\Delta PM=-\omega_{gc}T_d$ (convert to degrees); moving-average delay $(N-1)T_s/2$.
> - **Common mistakes:** forgetting that $f_{alias}$ must land in $[0,f_N]$ (pick the $m$ that does); leaving $\omega_{gc}T_d$ in radians when subtracting from a PM in degrees.
> - **Practise:** [[#9. Worked example: one channel from sensor to number]] · [[SESA2027 Mock Questions#Q12. Range mapping, ADC and aliasing|Mock Q12]] · [[SESA2027 Part C Problem Sheet Solutions]] (Q7–Q12)

Between the sensor and the flight computer lies a digital bridge that turns a continuous voltage into a stream of integers. It squeezes the voltage into the ADC's window (range), chops time into samples (time) and rounds each sample to the nearest of $2^n$ levels (amplitude). Each step can destroy information for good: a peak that exceeds the window is clipped flat; a vibration faster than half the sampling rate is folded down and masquerades as slow motion; a high-impedance sensor loses part of its signal to the instrument reading it. Once that has happened, no software can undo it, which is why these jobs belong to hardware.

After the ADC, software can clean the samples: average to remove noise, differentiate to get rates, integrate to get totals, reject spikes, fuse sensors. Each of these steps adds delay. A smoothing filter averages over past samples, so its output lags the signal, and every stage of latency is a pure phase lag that comes straight off the phase margin designed in Part B. The question at each step is not "is it smoother?" but "is it still true enough, soon enough, to feed back?"

---

## 1. Hardware vs software (L3.07)

| Hardware must *preserve* | Software can *refine* |
|---|---|
| Impedance matching | Calibration |
| Scaling and offsetting | Drift correction |
| Anti-alias filtering | Digital filtering |
| Electrical protection | Sensor fusion |
| A hardware error means lost information | Software cannot recover destroyed data |

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

**Where $A_v$ and $V_{os}$ come from.** The map is a straight line through two points: the sensor minimum must land on the ADC minimum, and the sensor maximum on the ADC maximum:

$$
A_vV_{min}+V_{os}=V_{ADC,min},\qquad A_vV_{max}+V_{os}=V_{ADC,max}
$$

Subtract the first from the second to eliminate $V_{os}$:

$$
A_v(V_{max}-V_{min})=V_{ADC,max}-V_{ADC,min}\quad\Rightarrow\quad A_v=\frac{V_{ADC,max}-V_{ADC,min}}{V_{max}-V_{min}}
$$

Back-substitute into the first: $V_{os}=V_{ADC,min}-A_vV_{min}$.

**Clipping**: occurs if $V_{out}>V_{ADC,max}$ or $V_{out}<V_{ADC,min}$. The flat top destroys the peak information, and no algorithm can restore it.

![[amc_psc_q7_range_mapping.png|650]]

## 3. Amplitude transformation: ADC resolution
See [[ADC Quantisation and Resolution]].

$$
Q = \frac{V_{ADC,max}-V_{ADC,min}}{2^n},\qquad N[k] = \mathrm{round}\!\left(\frac{V_{out}[k]}{Q}\right),\qquad \hat V[k] = N[k]Q,\qquad |e_q|\le\frac Q2
$$

- For a 5 V range: 8 bit gives $Q = 19.5$ mV, 12 bit gives 1.22 mV, and 16 bit gives 76.3 µV.
- Datasheets define the LSB slightly differently ($2^n$ or $2^n-1$), but the principle is the same: more bits means smaller steps.

Quantisation as noise (an addition to the slides; assumptions: the signal moves over many levels, so the rounding error $e_q$ is equally likely anywhere in $[-Q/2,Q/2]$). The probability density is $1/Q$ on that interval, so the mean is zero and the variance is

$$
\sigma_q^2=\int_{-Q/2}^{Q/2}e^2\,\frac1Q\,de=\frac1Q\left[\frac{e^3}{3}\right]_{-Q/2}^{Q/2}=\frac{1}{Q}\cdot\frac{2}{3}\cdot\frac{Q^3}{8}=\frac{Q^2}{12}
$$

$$
\sigma_q=\frac{Q}{\sqrt{12}}
$$

A 12-bit converter on 0–5 V has $Q=1.22$ mV and $\sigma_q=0.35$ mV RMS. This is the "quantisation noise" listed among the noise sources in [[SESA2027 C2 - Sensor Characteristics, Dynamics and Design#Noise and SNR|C2]]. Each extra bit halves $Q$ and lowers the noise floor by $20\log_{10}2=6$ dB.

![[amc_quantisation.png|600]]

## 4. Loading effect and buffering
See [[Loading Effect and Buffering]]. The sensor's output impedance and the DAQ's input impedance form a voltage divider:

$$
V_{meas} = V_{sensor}\frac{Z_{in}}{Z_{out}+Z_{in}},\qquad \varepsilon_{load} = \frac{Z_{out}}{Z_{out}+Z_{in}}
$$

- Lecture example: $Z_{out} = 10$ kΩ and $Z_{in} = 100$ kΩ give $\varepsilon = 9.1\%$. That signal is lost before the computer sees anything.
- Line by line: the same current $i=V_{sensor}/(Z_{out}+Z_{in})$ flows through both impedances, and the DAQ sees only the drop across its own input, $V_{meas}=iZ_{in}$. The missing fraction is $1-Z_{in}/(Z_{out}+Z_{in})=Z_{out}/(Z_{out}+Z_{in})$. For $\varepsilon<1\,\%$ you need $Z_{in}>99Z_{out}$, hence the rule of thumb "input impedance at least 100 times the source impedance".
- **Fix**: a buffer amplifier (op-amp voltage follower) with $Z_{in}\to\infty$ and a low output impedance.
- The measurement system must not disturb the sensor.

## 5. Time transformation: sampling and aliasing
See [[Nyquist Sampling and Aliasing]].

$$
f_s = \frac1{T_s},\qquad f_N = \frac{f_s}2,\qquad \text{no aliasing if } f_s>2f_{max},\qquad f_{alias} = |f-mf_s|\in[0,f_N]
$$

- Content above $f_N$ folds into the low-frequency band. The flight computer then "sees motion that is not physically there" (a ghost signal).

**Why the alias frequency is $\lvert f-mf_s\rvert$.** Sample $x(t)=\cos(2\pi ft)$ at $t=kT_s=k/f_s$:

$$
x[k]=\cos\left(2\pi\frac{f}{f_s}k\right)
$$

Replace $f$ by $f-mf_s$ for any integer $m$:

$$
\cos\left(2\pi\frac{f-mf_s}{f_s}k\right)=\cos\left(2\pi\frac{f}{f_s}k-2\pi mk\right)=\cos\left(2\pi\frac{f}{f_s}k\right)
$$

since $mk$ is an integer. The samples are identical, so the computer cannot tell $f$ from $f-mf_s$. Because cosine is even, $-(f-mf_s)$ gives the same samples too. Exactly one of these candidates lies in $[0,f_s/2]$: that is the frequency the computer reports. A 70 Hz vibration sampled at 50 Hz therefore appears at $\lvert70-50\rvert=20$ Hz (Part C sheet Q10).
- **Anti-aliasing filter**: an analogue RC filter before the ADC, with

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

**Why a delay has unit magnitude and phase $-\omega T_d$.** A delay shifts the signal, $y(t)=x(t-T_d)$. Its transform is $Y(s)=e^{-sT_d}X(s)$ (the time-shift rule in [[SESA2027 A4 - Laplace Transforms, Transfer Functions and Step Response#2. Properties and standard transforms (MATH2048 L11–13 recap)|A4]]). At $s=i\omega$:

$$
e^{-i\omega T_d}=\cos\omega T_d-i\sin\omega T_d,\qquad\lvert e^{-i\omega T_d}\rvert=1,\qquad\angle e^{-i\omega T_d}=-\omega T_d
$$

The delay leaves the gain crossover where it was and rotates the phase there by $-\omega_{gc}T_d$ radians, which is the boxed result. Note it grows linearly with frequency: fast loops are far more delay-sensitive than slow ones.

![[amc_delay_phase_erosion.png|760]]

## 7. DAC and zero-order hold
The DAC is how the computer "speaks" back. It converts $N[k]$ into $V_{cmd}$ for the actuator electronics (servo drive or valve driver). It does not move the control surface itself.

- **Zero-order hold**: the output is held constant between updates, giving a staircase command.
- **Resolution**:

$$
Q_{DAC} = \frac{V_{DAC,max}-V_{DAC,min}}{2^n},\qquad V_{cmd}[k] = V_{DAC,min}+N[k]Q_{DAC}
$$

  If the ideal steady command lies between two levels, the loop switches between neighbours. This is actuator hunting (jitter).

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

A filter is an algorithm $\hat x[k] = F(y[k],y[k-1],\dots)$ that uses memory of past samples.

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

**Where the delay comes from.** Feed in a ramp, $y[k]=ck$. The output is the average of $c\,k, c(k-1),\dots,c(k-N+1)$:

$$
y_f[k]=\frac cN\sum_{i=0}^{N-1}(k-i)=c\left(k-\frac{1}{N}\cdot\frac{(N-1)N}{2}\right)=c\left(k-\frac{N-1}{2}\right)
$$

The output is the input shifted back by $(N-1)/2$ samples, i.e. $(N-1)T_s/2$ seconds: the centre of the window. Because the weights are symmetric this delay is the same at every frequency (figure below).

**How much noise it removes.** For independent noise samples of variance $\sigma^2$, the average of $N$ of them has variance $\sigma^2/N$, so the noise standard deviation falls by $\sqrt N$. Halving the noise costs four times the window and four times the delay.

### Recursive low-pass (IIR)

$$
y_f[k] = \alpha y[k]+(1-\alpha)y_f[k-1],\qquad 0<\alpha<1,\qquad \alpha\approx\frac{T_s}{\tau+T_s}
$$

- Rearranged: $y_f[k]-y_f[k-1] = \alpha(y[k]-y_f[k-1])$. The estimate moves by a fraction of the current error.
- This makes the filter itself a discrete dynamic system in the measurement path.
- $\alpha\to1$ gives fast tracking but a noisy estimate.
- $\alpha\to0$ gives a smooth but slow estimate.
- Choosing $\alpha$ is choosing the measurement dynamics.

**Where $\alpha\approx T_s/(\tau+T_s)$ comes from.** Start from the analogue RC low-pass, $\tau\dot y_f+y_f=y$, and replace the derivative with a backward difference:

$$
\tau\frac{y_f[k]-y_f[k-1]}{T_s}+y_f[k]=y[k]
$$

Multiply by $T_s$ and collect $y_f[k]$:

$$
(\tau+T_s)\,y_f[k]=\tau\,y_f[k-1]+T_s\,y[k]
$$

$$
y_f[k]=\frac{T_s}{\tau+T_s}\,y[k]+\frac{\tau}{\tau+T_s}\,y_f[k-1]
$$

which is the recursive filter with $\alpha=T_s/(\tau+T_s)$ and $1-\alpha=\tau/(\tau+T_s)$. Inverting, $\tau=T_s(1-\alpha)/\alpha$: at $T_s=10$ ms, $\alpha=0.2$ is a 40 ms filter and $\alpha=0.05$ a 190 ms filter. At low frequency the delay equals $\tau$, as for any first-order lag ([[SESA2027 C2 - Sensor Characteristics, Dynamics and Design#Time-domain metrics|C2]]).

![[amc_ma_iir_frequency_response.png|780]]

*The moving average has a constant delay but lets bands of high-frequency noise through between its nulls. The recursive filter attenuates smoothly, but its delay is largest exactly at the low frequencies the controller cares about.*

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

Dividing small noise differences by a small $T_s$ gives large errors. Quantitatively, if $n[k]$ is white with standard deviation $\sigma$, then $n[k]-n[k-1]$ has variance $\sigma^2+\sigma^2=2\sigma^2$, so the noise on the rate estimate is

$$
\sigma_{\dot y}=\frac{\sqrt2\,\sigma}{T_s}
$$

An attitude signal with $\sigma=0.01°$ sampled at $T_s=10$ ms gives a rate noise of $1.41\ °/\text{s}$: a 0.01° jitter becomes a rate error comparable to a real manoeuvre. Sampling faster makes it worse. The practical fix is a filtered derivative:

$$
d[k] = \beta d[k-1]+(1-\beta)\frac{y[k]-y[k-1]}{T_s}
$$

This is the same reason the D term of a [[PID Controller]] needs filtering.

### Integrals: bias accumulators
$I[k] = I[k-1]+T_sy[k]$. With a constant bias $b$:

$$
I[k] = I[0]+T_s\sum_{j=1}^kx[j]+\underbrace{kT_sb}_{\text{grows with time}}
$$

Ways to reduce drift, each of which adds an assumption:
- estimate the bias during known steady conditions;
- subtract a running baseline;
- apply a high-pass correction;
- reset the integral using an independent reference (e.g. accelerometer or GPS).

The risk is that drift removal also removes real low-frequency motion.

### Outlier rejection
Flag a sample if $|y[k]-y[k-1]|>\Delta_{max}$ (the physically possible change per sample). Then hold the last valid value, interpolate, or flag the measurement invalid.

### Complementary filtering as algorithmic fusion

$$
\hat x[k] = \alpha\hat x_{fast}[k]+(1-\alpha)\hat x_{slow}[k]
$$

This assigns frequency roles to the two sources; it is not plain averaging. See [[Complementary Filter]] and [[SESA2027 C1 - Sensing Systems, Sensor Principles and Sensor Fusion]]. The transfer-function derivation, the discrete update and the bounded bias error $\tau b$ are in [[SESA2027 C1 - Sensing Systems, Sensor Principles and Sensor Fusion#Complementary filter|C1]]. Note that $\alpha$ there weights the gyro (the fast source), whereas $\alpha$ in the recursive low-pass above weights the new sample; the symbol is reused with different roles.

**Pipeline**: $y[k]$ → validate → filter → estimate → $\hat x[k]$.

Digital processing can make measurements more useful, but every improvement encodes an assumption. For flight control the question is not whether the signal is smoother but whether the processed signal is still truthful enough for feedback.

## 9. Worked example: one channel from sensor to number

*(Suggested, not lecturer-set; it strings together the Part C sheet methods.)* A pitch-rate gyro outputs ±50 mV for ±100 °/s with an output impedance of 10 kΩ. The FCC has a 12-bit, 0–5 V ADC sampling at 100 Hz, and the pitch loop crosses over at 3 rad/s.

1. **Range**: $A_v=5/0.1=50$, $V_{os}=2.5$ V. A 120 °/s manoeuvre gives 60 mV, i.e. $V_{out}=5.5$ V: clipped. Design the window with margin (C2: about 1.5× the expected maximum).
2. **Resolution**: $Q=5/4096=1.22$ mV at the ADC, i.e. $1.22/50=24.4$ µV at the sensor, or $0.049\ °/\text{s}$ per count. Quantisation noise $Q/\sqrt{12}\to0.014\ °/\text{s}$ RMS.
3. **Loading**: into a 100 kΩ input, 9.1 % of the signal is lost; a voltage follower fixes it.
4. **Aliasing**: $f_N=50$ Hz. A 70 Hz engine vibration would appear at 20 Hz. Anti-alias RC with $f_c\le50$ Hz needs $\tau\ge1/(\pi\times100)=3.2$ ms.
5. **Latency**: if the RC (about 3 ms), conversion, buffering and bus add up to $T_d=50$ ms, the loop loses $3\times0.05=0.15$ rad $=8.6°$ of phase margin. A 10-sample moving average would add another 45 ms and another $7.7°$.

> [!check] Numbers (Python)
> $5/4096=1.221$ mV; $1.221/\sqrt{12}=0.352$ mV; $10/110=0.0909$; $1/(100\pi)=3.18$ ms; $3\times0.05\times180/\pi=8.59°$; $3\times0.045\times180/\pi=7.73°$. ✓

## Terminology and alternative names

| Course term | Also called | Where the course uses it | Note |
|---|---|---|---|
| digital bridge | data-acquisition chain, front end | L3.07 | course-specific name |
| range transformation (scaling and offsetting) | gain and offset (level shifting), span and zero adjustment | L3.07 | |
| amplitude transformation | quantisation | L3.07 | |
| time transformation | sampling, discretisation | L3.07 | |
| $Q$ | LSB (least significant bit), code width, resolution | L3.07 | |
| loading effect | impedance loading, source loading | L3.07 | |
| buffer amplifier | voltage follower, unity-gain buffer, impedance converter | L3.07 | |
| Nyquist frequency $f_N=f_s/2$ | folding frequency | L3.07 | |
| anti-aliasing filter | pre-sampling filter | L3.07 | |
| latency $T_d$ | transport delay, dead time | L3.07 | |
| zero-order hold | sample-and-hold (on the output side) | L3.07 | |
| actuator hunting | limit cycling, chatter | L3.07 | |
| moving average (FIR) | boxcar filter, running mean | L3.08 | |
| recursive low-pass (IIR) | exponential moving average (EMA), exponential smoothing | L3.08 | $\alpha$ weights the new sample |
| filtered derivative | dirty derivative, band-limited differentiator | L3.08 | |
| outlier rejection | rate-limit check, spike filter | L3.08 | |

## Links
- Parent: [[SESA2027 Aerospace Mechanics & Control Hub]] · Previous: [[SESA2027 C2 - Sensor Characteristics, Dynamics and Design]]
- Concepts: [[ADC Quantisation and Resolution]] · [[Loading Effect and Buffering]] · [[Nyquist Sampling and Aliasing]] · [[Digital Filtering]] · [[Complementary Filter]]
- Robustness and noise: [[SESA2027 B4 - Robustness, Stability vs Manoeuvrability and Design Process]]
- Worked problems: [[SESA2027 Part C Problem Sheet Solutions]] (Q7–Q13)

## Sources
- Lectures 3.07–3.08 (Prof A. Cammarano): slides only. No recordings of L3.07 or L3.08 were filed, so this note has no transcript backfill. Related lecturer comments from earlier recordings: sampling at about 10× the signal frequency (L2.06, ll. 84–90; L2.07, ll. 408–416) and the 50 Hz mains EMI peak (L3.04, ll. 293–318), both in [[SESA2027 C2 - Sensor Characteristics, Dynamics and Design|C2]] and [[SESA2027 B4 - Robustness, Stability vs Manoeuvrability and Design Process|B4]].
- Bentley, *Principles of Measurement Systems*, Ch. 9–10
- Figures: `01 - Notes/Figures/generate_amc_c3_figures.py`

## Self-study tasks

L3.07 and L3.08 have no recordings in the vault, so nothing set aloud is captured. The Part C problem sheet covers this material (Q7–Q12) and also the Part C computer lab. Every other task below is suggested, not lecturer-set.

### Core

- [ ] Map a ±50 mV sensor into 0–5 V, find $Q$ for 12 bits and check a given peak for clipping. → [[#2. Range transformation: scaling and offsetting]] · [[#3. Amplitude transformation: ADC resolution]]
- [ ] Find the alias of a 70 Hz signal sampled at 50 Hz and the RC needed to prevent it. → [[#5. Time transformation: sampling and aliasing]]
- [ ] Compute the phase-margin loss from a 50 ms latency at $\omega_{gc}=3$ rad/s. → [[#6. Latency]]
- [ ] Work the whole channel example closed-book. → [[#9. Worked example: one channel from sensor to number]]
- [ ] Part C sheet Q7–Q12. → [[SESA2027 Part C Problem Sheet Solutions]]
- [ ] Mock exam question. → [[SESA2027 Mock Questions#Q12. Range mapping, ADC and aliasing|Mock Q12]]

### Further practice

- [ ] Prove that $f$ and $f-mf_s$ give identical samples, and derive $\sigma_q=Q/\sqrt{12}$. → [[#5. Time transformation: sampling and aliasing]] · [[#3. Amplitude transformation: ADC resolution]]
- [ ] Derive the moving-average delay $(N-1)T_s/2$ and the recursive-filter $\alpha=T_s/(\tau+T_s)$. → [[#Moving average (FIR)]] · [[#Recursive low-pass (IIR)]]
- [ ] Show $\sigma_{\dot y}=\sqrt2\sigma/T_s$ for a difference derivative and explain why sampling faster makes it worse. → [[#Derivatives: noise amplifiers]]
