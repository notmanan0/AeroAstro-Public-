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
status: lectured
coverage: "L3.01 (slides only), L3.02 (sensing principles), L3.03 (sensor fusion, IMU)"
parent: ["[[SESA2027 Aerospace Mechanics & Control Hub]]"]
prerequisites: ["[[SESA2027 B4 - Robustness, Stability vs Manoeuvrability and Design Process]]"]
next_topics: ["[[SESA2027 C2 - Sensor Characteristics, Dynamics and Design]]"]
key_concepts: ["[[Measurement Chain]]", "[[Wheatstone Bridge and Strain Gauges]]", "[[Accuracy and Precision]]", "[[Complementary Filter]]"]
tutorial_sheets: ["[[SESA2027 Part C Problem Sheet Solutions]]"]
sources: ["02 - Sources/Lectures/Lecture 3.01.pdf", "02 - Sources/Lectures/Lecture 3.02.pdf", "02 - Sources/Lectures/Lecture 3.03.pdf", "02 - Sources/Lectures/Lecture 3.02-3.03 recording.txt"]
---

# SESA2027 C1 - Sensing Systems, Sensor Principles and Sensor Fusion

> [!abstract] Summary
> A feedback controller never sees the true output, only the measured output of a sensing system: physical quantity → sensor → signal conditioning → data acquisition → processing. Every measurement carries noise, bias and drift, and each sensing element exploits one physical effect (resistive, capacitive, inductive, thermoelectric or piezoelectric). Because no sensor is perfect, an IMU fuses a gyroscope (good at high frequency, drifts) with an accelerometer (good at low frequency, noisy), most simply with a complementary filter.

> [!summary]- Exam use: quick path
> - **Use it when:** a question gives a bridge configuration and a voltage (or a strain) and asks for $\Delta R/R$, strain or output voltage; asks which sensing principle suits a measurement and why; or asks why an IMU needs fusion and how a complementary filter works.
> - **Assumptions:** bridge supplied by $V_s$, meter draws no current; small resistance changes ($\Delta R\ll R$) for the quarter-bridge formula; gauge factor $G\approx2$ for metal foil unless given; complementary-filter weights sum to 1.
> - **Method:** 1. Identify the bridge type (quarter, half, full) and which arms hold active gauges. 2. Quarter: $V_G\approx(V_s/4)G\varepsilon$; half (bending, adjacent arms): $(V_s/2)G\varepsilon$; full: $V_sG\varepsilon$. 3. Invert for $\varepsilon$. 4. For fusion: gyro for high frequency (integrate rate), accelerometer for low frequency (gravity direction). 5. Combine $\hat\theta_k=\alpha(\hat\theta_{k-1}+\omega_k\Delta t)+(1-\alpha)\theta_{acc,k}$.
> - **Common mistakes:** using the quarter-bridge formula for a half bridge (the output doubles); claiming a piezoelectric accelerometer can measure gravity (it cannot measure a static load).
> - **Practise:** [[#Worked example: strain from bridge voltages]] · [[SESA2027 Mock Questions#Q10. Strain gauge bridge and complementary filter|Mock Q10]] · [[SESA2027 Part C Problem Sheet Solutions]] (Q1–Q3, Q13)

A controller cannot see the aircraft; it sees numbers that a chain of hardware has produced from the aircraft. Each sensor works by letting the physical quantity change something electrical: strain changes a wire's resistance, displacement changes a capacitor's gap or a magnetic circuit's air gap, a temperature difference drives a thermoelectric voltage, a dynamic force squeezes charge out of a crystal. Each of these is imperfect in its own way: noise, bias, drift, limited resolution, and sometimes blindness to slow signals (piezo) or to fast ones (big thermocouples).

So we combine sensors whose weaknesses lie at different frequencies. A gyro measures rotation rate cleanly, but integrating it to get an angle also integrates its small bias, so the angle wanders off. An accelerometer finds "down" from gravity with no drift, but every vibration and manoeuvre corrupts it. A complementary filter takes the slow part of the accelerometer angle and the fast part of the gyro angle. Because the two filters add up to exactly 1, the true angle passes straight through, and each sensor's error is suppressed where that sensor is weak.

---

## 1. Why sensing matters for control (L3.01)
> [!note] No transcript for L3.01
> There is no recording for L3.01, so this section is from the slides only. L3.02–3.03 were recorded together in one session.

In the B-part block diagram the feedback path contains a sensor $H(s)$ and measurement noise $X_N$. See [[SESA2027 B4 - Robustness, Stability vs Manoeuvrability and Design Process]].

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
| Sensor / sensing element | Interacts directly with the physical quantity |
| Signal conditioning | Makes the raw signal usable: amplify, filter, linearise, offset, protect |
| Data acquisition (DAQ) | Sampling, analogue-to-digital conversion (ADC), transmission |
| Processing / display | Estimation, control, storage, visualisation |

**Sensor vs transducer**:
- A sensor *detects* the quantity. Examples: an accelerometer sensing acceleration, a pressure diaphragm.
- A transducer *converts energy* from one form to another, usually into an electrical signal. Examples: a strain gauge (strain → resistance), a thermocouple (temperature difference → voltage).

## 3. Measurement imperfections

| Error | Nature | Typical causes | Effect |
|---|---|---|---|
| Noise | Random, short-term | Electrical interference, thermal noise, environment | Jitter; poor precision |
| Bias | Constant offset | Calibration error, manufacturing tolerance, modelling | Consistently high or low; poor accuracy |
| Drift | Slow change over time | Temperature, ageing, component variation | Error grows; the rate hints at the cause |
| Limited resolution | Smallest detectable change | ADC bits, sensor physics | Quantisation steps |

**Filtering trade-off**: a low-pass filter removes high-frequency noise, but it adds lag, slows the response and reduces bandwidth. If filtering is too strong, the controller works from stale information. This theme runs through all of Part C.

**Design considerations**: range, accuracy, sensitivity, bandwidth, environment (temperature, vibration), reliability and robustness, and integration with the electronics.

## 4. Sensing principles (L3.02)
Transduction is the conversion of energy from one form to another. The sensing element interacts with the measured variable, and the transduction process turns that interaction into an electrical signal.

| Principle | Physical law | Measures |
|---|---|---|
| Resistive | $R = \rho L/A$ | Strain, temperature |
| Capacitive | $C = \varepsilon_0\varepsilon A/d$ | Displacement, pressure, acceleration |
| Inductive | $L = n^2/\mathfrak R$ | Position, motion |
| Thermoelectric | $V = \alpha_T(T_h-T_c)$ (Seebeck) | Temperature |
| Piezoelectric | $q = dF$ | Dynamic force, vibration |

The lecture groups operating principles into three families (L3.02–3.03, ll. 10–25): electrical-property variation (resistive, capacitive, inductive), energy conversion (thermoelectric, piezoelectric) and field interaction (optical or electromagnetic). The module covers the first two; the third is mentioned only.

These physical relations matter for control because, in the second computer lab, the controller is fed the state "as if you could measure the state perfectly" (L3.02–3.03, ll. 46–54, 1057–1060). In reality a sensing block sits in front of the controller and changes the signal, and the relations in this section are what C2 uses to write the sensors' transfer functions (Bentley, Ch. 8).

### 4.1 Resistive: strain gauges and the Wheatstone bridge
Stretching a conductor lengthens it and narrows its cross-section, so $R$ rises. The bridge output is

$$
V_G = \left(\frac{R_2}{R_1+R_2}-\frac{R_4}{R_3+R_4}\right)V_s
$$

- The bridge is balanced ($V_G = 0$) when all four resistances are equal.
- **Quarter bridge**: the gauge is $R_2 = R+\Delta R$, with all others equal to $R$. Then

$$
V_G = \left(\frac{R+\Delta R}{2R+\Delta R}-\frac12\right)V_s\;\xrightarrow{\ \Delta R\ll R\ }\;\boxed{\frac{\Delta R}{R}\approx\frac{4V_G}{V_s}},\qquad \frac{\Delta R}{R} = G\varepsilon\;\Rightarrow\;V_G = \frac{V_s}{4}G\varepsilon
$$

  $G$ is the gauge factor, about 2 for metal foil.
- Why $G\approx2$: the Poisson effect doubles the change (L3.02–3.03, ll. 77–82). Stretching lengthens the wire and narrows it (metals have $\nu\approx0.3$), so both effects raise $R$. Assumptions: a uniform wire of diameter $D$, axial strain $\varepsilon = dL/L$, lateral strain $dD/D = -\nu\varepsilon$. Start from

$$
R = \frac{\rho L}{A}
$$

  Take logarithms:

$$
\ln R = \ln\rho+\ln L-\ln A
$$

  Differentiate:

$$
\frac{dR}{R} = \frac{d\rho}{\rho}+\frac{dL}{L}-\frac{dA}{A}
$$

  With $A = \pi D^2/4$, $dA/A = 2\,dD/D = -2\nu\varepsilon$:

$$
\frac{dR}{R} = \frac{d\rho}{\rho}+\varepsilon+2\nu\varepsilon
$$

$$
\frac{dR}{R} = \varepsilon(1+2\nu)+\frac{d\rho}{\rho}
$$

  Divide by $\varepsilon$:

$$
G = \frac{dR/R}{\varepsilon} = 1+2\nu+\frac{d\rho/\rho}{\varepsilon}
$$

  For $\nu = 0.3$ the geometric part alone is $1+0.6 = 1.6$; the small change in resistivity under strain (piezoresistance) supplies the rest of a metal's $G\approx2$. In semiconductor gauges the piezoresistive term dominates, giving $G$ of order 100.
- Sensor or transducer? (ll. 96–110) Both. The wire is the sensor, the part that interacts with the strain. The bridge and its other resistors are the transducer that turns the resistance change into a voltage.
- **We measure resistance, not strain.** The strain is inferred.
- Temperature also changes $\rho$, so a temperature change looks like strain.
- **Half bridge**: put a second, identical gauge in the adjacent arm ($R_1$). Temperature changes both gauges equally and cancels in the ratio.
- On a bending cantilever with one gauge in tension and one in compression, the two strain signals add. That doubles the sensitivity while temperature still cancels.

**Quarter-bridge result, line by line.** Set $R_1 = R_3 = R_4 = R$ and $R_2 = R+\Delta R$:

$$
\frac{V_G}{V_s} = \frac{R+\Delta R}{2R+\Delta R}-\frac12
$$

$$
\frac{V_G}{V_s} = \frac{2(R+\Delta R)-(2R+\Delta R)}{2(2R+\Delta R)}
$$

$$
\frac{V_G}{V_s} = \frac{\Delta R}{4R+2\Delta R}
$$

For $\Delta R\ll R$, drop $2\Delta R$ in the denominator:

$$
\frac{V_G}{V_s}\approx\frac{\Delta R}{4R}\quad\Rightarrow\quad\frac{\Delta R}{R}\approx\frac{4V_G}{V_s}
$$

![[amc_wheatstone_cantilever.png|900]]

Half bridge on a cantilever, line by line (assumptions: identical gauges, equal and opposite strains top and bottom, $R_3=R_4=R$). Put the tension gauge in $R_2=R+\Delta R$ and the compression gauge in the adjacent arm $R_1=R-\Delta R$:

$$
\frac{V_G}{V_s}=\frac{R+\Delta R}{(R-\Delta R)+(R+\Delta R)}-\frac12=\frac{R+\Delta R}{2R}-\frac12=\frac{\Delta R}{2R}
$$

$$
V_G=\frac{V_s}{2}\frac{\Delta R}{R}=\frac{V_s}{2}G\varepsilon
$$

Twice the quarter-bridge output, and exactly linear: the $\Delta R$ terms cancel in the denominator. Now add a temperature change that raises both gauges by $\Delta R_T$:

$$
\frac{V_G}{V_s}=\frac{R+\Delta R+\Delta R_T}{2(R+\Delta R_T)}-\frac12=\frac{\Delta R}{2(R+\Delta R_T)}\approx\frac{\Delta R}{2R}
$$

The temperature term has dropped out of the numerator; it survives only as a tiny change of scale. That is the "self-balancing under temperature" the lecturer described (l. 171).

### Worked example: strain from bridge voltages

*(Suggested, not lecturer-set; same method as the Part C sheet Q1–Q2.)* Foil gauges, $G=2.0$, $R=350\ \Omega$, $V_s=5$ V, true strain $\varepsilon=500\ \mu\varepsilon$.

- $\Delta R/R=G\varepsilon=1.0\times10^{-3}$, so $\Delta R=0.35\ \Omega$.
- Quarter bridge, approximate: $V_G=(5/4)\times10^{-3}=1.250$ mV.
- Quarter bridge, exact: $V_G=5\times0.35/(4\times350+2\times0.35)=1.2494$ mV. The linearisation error is $0.05\,\%$.
- Half bridge (bending): $V_G=2.50$ mV. Full bridge (four active gauges): $5.00$ mV.
- Inverting a measured 1.80 mV on the quarter bridge: $\varepsilon=4V_G/(V_sG)=4\times1.8\times10^{-3}/(5\times2)=720\ \mu\varepsilon$.

> [!check] Why amplification is needed
> Millivolt outputs from a 5 V supply are why every bridge is followed by an instrumentation amplifier in the conditioning stage ([[SESA2027 C3 - Signal Conditioning, Digitisation and Digital Filtering#2. Range transformation: scaling and offsetting|C3 §2]]). A 12-bit ADC on a 0–5 V range resolves 1.22 mV, about the whole quarter-bridge signal.

> [!info] Lecturer's practical notes on resistive and thermal sensors (L3.02)
> - Ohm's law with a fixed $\rho$ holds only at constant temperature, because resistivity depends on temperature (ll. 57–68). It holds for metals (conductors), but not necessarily for semiconductors such as silicon, which "sometimes does very, very weird stuff" (ll. 69–76).
> - A resistive sensor adds no phase. With a purely resistive load the current and voltage are in phase, because $R$ is a real number; only the amplitude changes. It behaves "like the proportional gain in the controller" (ll. 207–218).
> - Off-the-shelf strain gauges are usually 120 Ω or 350 Ω (ll. 180–183).
> - The half bridge is "almost a self-balancing bridge under the action of temperature" (l. 171).
> - Small thermocouples respond faster. Large ones lag because they must reach equilibrium with their surroundings, and that lag matters for control, e.g. spacecraft battery thermal management, where "you might have already lost a battery before you can sense" it (ll. 331–346). Tiny thermocouples can be put in series to amplify the signal (ll. 317–318).
> - The Seebeck coefficient depends on the materials, the temperature and the junction geometry (ll. 287–303).

See [[Wheatstone Bridge and Strain Gauges]].

### 4.2 Thermoelectric: thermocouples
- The Seebeck effect: two dissimilar conductors joined across a temperature difference generate $V = \alpha_T(T_h-T_c)$.
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

Other examples from the lecture (ll. 380–395): a humidity sensor, with one plate resting on a gel that swells as it absorbs water, so the gap tracks the humidity; and a water-level gauge, with coaxial cylinders whose capacitance changes as water (higher permittivity) replaces air between them.

**Gap sensitivity is nonlinear.** For the gap configuration with $C_0=\varepsilon_0\varepsilon A/d$:

$$
\frac{dC}{dx}=-\frac{\varepsilon_0\varepsilon A}{(d+x)^2}\quad\Rightarrow\quad\left.\frac{dC}{dx}\right|_{x=0}=-\frac{C_0}{d}
$$

$$
\frac{\Delta C}{C_0}=\frac{d}{d+x}-1=-\frac{x}{d+x}\approx-\frac{x}{d}\quad(x\ll d)
$$

so the sensor is linear only for displacements much smaller than the gap. The area configuration, $C=\varepsilon_0\varepsilon(A-wx)/d$, is linear in $x$ by construction. Small gaps give high sensitivity, which is why MEMS accelerometers use micrometre gaps.

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

The gap $d$ between the armature and the core changes the inductance. This is a displacement sensor, e.g. for landing-gear or actuator position.

Where $k=2/(\mu_0\pi r^2)$ comes from (assumptions: the flux crosses two air gaps, one at each pole of the core, each of length $d$ and circular area $\pi r^2$; air has $\mu=1$; fringing neglected). Each gap is a reluctance $l/(\mu\mu_0A)=d/(\mu_0\pi r^2)$, and the two are in series:

$$
\mathfrak R_{gap}=\frac{2d}{\mu_0\pi r^2}=kd
$$

The iron parts have $\mu\gg1$, so their reluctance $\mathfrak R_0$ is small and constant. The gap dominates, which makes the inductance very sensitive to $d$, and nonlinear in it, like the capacitive gap sensor.

### 4.5 Piezoelectric
- **Mechanics**: $x = F/k$.
- **Direct piezoelectric effect**: $q = Kx = dF$, where $d = K/k$ is the charge sensitivity in C/N.
- Electrically, the crystal is a charge source in parallel with a capacitance $C = \varepsilon_0\varepsilon A/t$.
- The charge leaks away, so there is no output for a static force. Piezoelectric sensors are for dynamic measurement only: vibration and shock.

Why the static output decays: the piezo as a high-pass filter (assumptions: the crystal capacitance $C$ in parallel with a leakage/amplifier resistance $R$). The generated charge is $q=dF$, so the source current is $i=\dot q=d\dot F$. Current balance at the output node:

$$
d\,\dot F=C\dot V+\frac VR
$$

Laplace transform with zero initial conditions:

$$
d\,sF(s)=\left(Cs+\frac1R\right)V(s)
$$

$$
\frac{V(s)}{F(s)}=\frac{d}{C}\cdot\frac{\tau s}{\tau s+1},\qquad\tau=RC
$$

This is a first-order high-pass filter. Its DC gain is zero, so a constant force (or a constant 1 g) gives no steady output; signals well above $1/\tau$ pass with sensitivity $d/C$ (V/N). It is the same transfer-function idea C2 uses for every sensor ([[SESA2027 C2 - Sensor Characteristics, Dynamics and Design#Three model orders (DAP2, Occam's razor)|C2]]).

A gas-hob igniter is a piezo element (L3.02, ll. 975–1051): the click delivers an impact that produces a high voltage and a spark. Electrically the crystal gives a high voltage at very low current and looks like a capacitor, so it can be read as a voltage, a current or a capacitance. Under a constant load the lattice settles into a new equilibrium and the output decays, which is why a piezoelectric accelerometer can't measure gravity, a constant 1 g.

## 5. Sensor fusion and the IMU (L3.03)
Real measurements are imperfect (noise, bias, limited bandwidth), and no single sensor gives complete information. Combining sensors improves accuracy and robustness and extends what can be measured. The design trade-off is between precision, reliability and cost.

**IMU**: measures motion without external references.
- 3-axis accelerometer plus 3-axis gyroscope gives 6 DoF. Adding a magnetometer gives 9 DoF.
- Outputs are linear acceleration and angular velocity in the body frame. Integration gives orientation, velocity and position.

| | Accelerometer | Gyroscope |
|---|---|---|
| Principle | Newton's 2nd law on a proof mass | Coriolis effect (MEMS) |
| Measures | Specific force (includes gravity) | Angular velocity |
| Strength | Good long-term reference (gravity) | Accurate short-term dynamics |
| Weakness | Noisy; affected by manoeuvres; cannot separate acceleration from gravity | Bias integrates into drift; errors accumulate |

### Complementary filter
See [[Complementary Filter]].

$$
\boxed{\hat\theta = \alpha\,\theta_{gyro}+(1-\alpha)\,\theta_{acc}}
$$

- The gyro path is effectively high-pass filtered: it is trusted for fast changes.
- The accelerometer path is effectively low-pass filtered: it is trusted for the slow, steady value.
- The two filters sum to 1, so the true signal passes through undistorted. Each sensor's *error* is removed in the band where that sensor is weak.

![[amc_complementary_filter.png|650]]

The figure shows three things:
- The integrated gyro (red) follows the shape of the motion but wanders off because of bias.
- The accelerometer (orange) has no drift but is buried in noise.
- The complementary estimate with $\alpha = 0.98$ (blue) tracks the truth.

The complementary filter as transfer functions (the slide states the weighted sum; this is why it works). Let the gyro measure $\omega_g=\dot\theta+b$, with a constant bias $b$, and the accelerometer give $\theta_a=\theta+n$, with noise $n$. In continuous time, low-pass the accelerometer angle and high-pass the integrated gyro rate with the same time constant $\tau$:

$$
\hat\theta=\frac{1}{\tau s+1}\theta_a+\frac{\tau s}{\tau s+1}\cdot\frac{\omega_g}{s}=\frac{\theta_a+\tau\,\omega_g}{\tau s+1}
$$

Substitute the sensor models ($\omega_g=s\theta+b$ in Laplace form):

$$
\hat\theta=\frac{\theta+n+\tau s\theta+\tau b}{\tau s+1}=\theta+\frac{n}{\tau s+1}+\frac{\tau\,b}{\tau s+1}
$$

- The true angle passes through with gain exactly 1: the two filters sum to 1.
- Accelerometer noise is low-pass filtered: only its slow part survives.
- A constant gyro bias settles to a bounded angle error $\tau b$ (the step response of $\tau/(\tau s+1)$). Integrating the gyro alone gives $bt$, which grows forever.

![[amc_complementary_filter_bode.png|760]]

**Discrete form.** Discretise $(\tau s+1)\hat\theta=\theta_a+\tau\omega_g$ with a backward difference, $s\hat\theta\to(\hat\theta_k-\hat\theta_{k-1})/\Delta t$:

$$
\tau\frac{\hat\theta_k-\hat\theta_{k-1}}{\Delta t}+\hat\theta_k=\theta_{a,k}+\tau\,\omega_{g,k}
$$

Multiply by $\Delta t$ and collect $\hat\theta_k$:

$$
(\tau+\Delta t)\hat\theta_k=\tau\left(\hat\theta_{k-1}+\omega_{g,k}\Delta t\right)+\Delta t\,\theta_{a,k}
$$

$$
\boxed{\hat\theta_k=\alpha\left(\hat\theta_{k-1}+\omega_{g,k}\Delta t\right)+(1-\alpha)\theta_{a,k},\qquad\alpha=\frac{\tau}{\tau+\Delta t}}
$$

The bracket is the gyro's prediction of the new angle, which is what "$\theta_{gyro}$" means in the slide formula.

> [!example] Numbers: bias bound
> $\Delta t=10$ ms and $\alpha=0.98$ give $\tau=\alpha\Delta t/(1-\alpha)=0.49$ s. A gyro bias of $0.5\ °/\text{s}$ then leaves a steady error of $\tau b=0.25°$. Integrating the same gyro alone for 60 s gives $30°$ of drift. Check from the recursion: at steady state $e=\alpha(e+b\Delta t)$, so $e=\alpha b\Delta t/(1-\alpha)=0.98\times0.5\times0.01/0.02=0.245°$. ✓

The complementary filter is not averaging. An average weights both sensors equally at every frequency, so it would inherit both the gyro drift and the accelerometer noise; the complementary filter gives each sensor a frequency role, the gyro at high frequency and the accelerometer at low frequency.

> [!info] Lecturer intuition on the IMU (L3.03 part of the recording)
> - Integration drifts because integrating means summing, and you sum the noise too, every sample. Over time the summed noise (plus numerical error) becomes a signal of its own (ll. 1113–1143). The integration constant (initial position) is also unknown without an external reference (ll. 1117–1126).
> - Fusion is a trade-off between precision, reliability and cost: more sensors give redundancy but cost more (ll. 1099–1111).
> - A MEMS gyro is a vibrating proof mass on springs. A rotation produces a Coriolis force across the drive direction, which is sensed capacitively (ll. 1192–1220). Accurate short-term, poor long-term.
> - The Kalman filter "is not a filter": it is an estimator that combines several measurements using their noise statistics. It is not taught in this module this year (ll. 1148–1191); it appears in Year 3.

## Lecturer emphasis and exam hints (transcripts)

> [!info] Scope
> - Admin: Part C lab report (ll. 607–619). Six pages, with guiding questions for structure. In effect a summary and critical assessment of the Jupyter notebooks and what you observed in them.
> - L3.02–3.03 contain no explicit exam statements. The lecturer flagged the physical relations as needed for the sensor transfer functions in C2 (ll. 1057–1058).
> - Further reading: Bentley Ch. 8 (sensing elements, l. 1060); Groves, *Principles of GNSS, Inertial, and Multisensor Integrated Navigation Systems*, for the IMU (ll. 1253–1254).

## Transcript slips

> [!warning] Speech-to-text and spoken slips, with the correct version
> | Where | Transcript says | Correct |
> |---|---|---|
> | L3.02–3.03, l. 77 | "resistive conduct, of resistive capacity" | resistive sensors |
> | L3.02–3.03, l. 87 | "an expert in Wisdom Bridge" | Wheatstone bridge |
> | L3.02–3.03, l. 177 | "R2 as Vs minus 2Vg, Vs plus 2Vg" | $R_2 = R(V_s+2V_G)/(V_s-2V_G)$ for the quarter bridge, exactly |
> | L3.02–3.03, ll. 184–185 | gauges "in the region of micro ohm … sorry … kilo ohm" | kΩ (self-corrected) |
> | L3.02–3.03, l. 286 | "B equal alpha delta T" | $V = \alpha\,\Delta T$ |
> | L3.02–3.03, ll. 306–312 | the two thermocouple junction materials "normally are semiconductors" | the standard types (K, R, S) are metal alloys; the slide's "excess electrons / vacancies" picture is an analogy borrowed from semiconductors. Semiconductor thermoelectric elements exist (Peltier devices) but are not the usual thermocouple |
> | L3.02–3.03, l. 405 | "you have done statics last year" | plate bending (the diaphragm formula) |
> | L3.02–3.03, ll. 979–987 | "gas fobs … to enlighten" | gas-hob igniters, to light them |
> | L3.02–3.03, l. 1044 | "a new way of reassessing the cell" | a new equilibrium of the crystal cell |
> | L3.02–3.03, l. 1049 | "most accelerometers have a piezoelectric material in it" | many vibration accelerometers do; the MEMS accelerometers in IMUs are mostly capacitive (§4.3), which is why they can measure gravity |
> | L3.02–3.03, ll. 1063, 1074 | "the MIU", "a magnometer" | IMU, magnetometer |
> | L3.02–3.03, l. 1164 | "impartial information" | partial information |
> | L3.02–3.03, l. 1227 | a capacitive accelerometer cannot tell acceleration from gravity | true of any accelerometer: it measures specific force |

## Terminology and alternative names

| Course term | Also called | Where the course uses it | Note |
|---|---|---|---|
| sensing system / measurement chain | measurement system, instrumentation chain | L3.01 | |
| sensor vs transducer | sensing element vs converter | L3.01 | the course separates detecting from converting energy |
| signal conditioning | front-end electronics, analogue conditioning | L3.01 | |
| data acquisition (DAQ) | ADC stage, digitisation | L3.01 | |
| bias | offset, zero error, systematic error | L3.01 | |
| drift | bias instability (gyros), zero drift | L3.01 | |
| gauge factor $G$ | strain sensitivity, $K$ in some texts | L3.02 | |
| quarter / half / full bridge | one-, two-, four-active-arm bridge | L3.02 | |
| Seebeck coefficient $\alpha_T$ | thermoelectric sensitivity (µV/K) | L3.02 | |
| reluctance $\mathfrak R$ | magnetic resistance | L3.02 | |
| charge sensitivity $d$ | piezoelectric coefficient $d_{33}$ (C/N) | L3.02 | |
| specific force | proper acceleration; what an accelerometer reads | L3.03 | includes the gravity reaction |
| complementary filter weight $\alpha$ | blending factor, filter coefficient | L3.03 | here $\alpha$ weights the gyro; in the C3 IIR filter $\alpha$ weights the new sample, the opposite role |
| IMU | inertial measurement unit; with a magnetometer, AHRS | L3.03 | |
| Kalman filter | optimal estimator | L3.03 (mentioned) | not examined this year |

## Links
- Parent: [[SESA2027 Aerospace Mechanics & Control Hub]] · Previous: [[SESA2027 B4 - Robustness, Stability vs Manoeuvrability and Design Process]] · Next: [[SESA2027 C2 - Sensor Characteristics, Dynamics and Design]]
- Concepts: [[Measurement Chain]] · [[Accuracy and Precision]] · [[Wheatstone Bridge and Strain Gauges]] · [[Complementary Filter]]
- Worked problems: [[SESA2027 Part C Problem Sheet Solutions]] (Q1–Q3, Q13)
- Year 1: [[FEEG1004 E3 - Strain Gauges, Bridges, Pressure and Flow Sensors]] · [[FEEG1004 E2 - Displacement Sensors - Potentiometric, Capacitive and Inductive]]

## Sources
- Lectures 3.01–3.03 (Prof A. Cammarano): slides `Lecture 3.01.pdf`–`Lecture 3.03.pdf`
- Transcript (speech-to-text): `Lecture 3.02-3.03 recording.txt` (one session covering both lectures; no recording of L3.01)
- Bentley, *Principles of Measurement Systems* (Ch. 1, 2, 4, 8)
- Groves, *Principles of GNSS, Inertial, and Multisensor Integrated Navigation Systems* (Ch. 4)
- Figures: `01 - Notes/Figures/generate_amc_c1_figures.py`

## Self-study tasks

No tasks were set in the L3.02–3.03 recording, and L3.01 has no recording. The physical relations were flagged as needed for the sensor transfer functions in C2 (ll. 1057–1058). Every task below is suggested, not lecturer-set.

### Core

- [ ] Derive $\Delta R/R\approx4V_G/V_s$ for a quarter bridge and $V_G=(V_s/2)G\varepsilon$ for a bending half bridge. → [[#4.1 Resistive: strain gauges and the Wheatstone bridge]]
- [ ] Find the bridge output for 500 µε with quarter, half and full bridges, and the strain for a measured voltage. → [[#Worked example: strain from bridge voltages]]
- [ ] Explain why a piezoelectric sensor cannot measure gravity but a capacitive MEMS accelerometer can. → [[#4.5 Piezoelectric]] · [[#4.3 Capacitive]]
- [ ] Explain, using "integration is summation", why a gyro-only attitude estimate drifts and how the complementary filter fixes it. → [[#5. Sensor fusion and the IMU (L3.03)]]
- [ ] Part C sheet Q1–Q3 and Q13. → [[SESA2027 Part C Problem Sheet Solutions]]
- [ ] Mock exam question. → [[SESA2027 Mock Questions#Q10. Strain gauge bridge and complementary filter|Mock Q10]]

### Further practice

- [ ] Derive $G = 1+2\nu+(d\rho/\rho)/\varepsilon$ from $R=\rho L/A$ and explain why metal gauges have $G\approx2$ (suggested). → [[#4.1 Resistive: strain gauges and the Wheatstone bridge]]
- [ ] Derive the piezo transfer function $V/F=(d/C)\,\tau s/(\tau s+1)$ (suggested). → [[#4.5 Piezoelectric]]
- [ ] Show that a constant gyro bias leaves a bounded error $\tau b$ in the complementary filter, then derive the discrete update and $\alpha=\tau/(\tau+\Delta t)$ (suggested). → [[#Complementary filter]]
