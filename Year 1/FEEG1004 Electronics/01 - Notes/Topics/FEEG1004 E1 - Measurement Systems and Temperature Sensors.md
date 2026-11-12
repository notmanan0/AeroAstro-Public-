---
title: "FEEG1004 E1 - Measurement Systems and Temperature Sensors"
module: "FEEG1004 Electronics"
type: topic
stream: "Part E: Transducers and Measurement"
order: 1
tags: [feeg1004, transducers, measurement, sensitivity, resolution, accuracy, precision, rtd, thermistor, thermocouple, adc, aliasing]
aliases: ["Transducers 01", "Measurement systems", "Sensor definitions", "Temperature sensors"]
date: 2026-09-27
status: lectured
coverage: "FEEG1004 Lecture 2025-03-24 (ll. 1–772)"
parent: ["[[FEEG1004 Electronics Hub]]"]
prerequisites:
  - "[[FEEG1004 A3 - DC Circuit Laws - Ohm, KCL, KVL and Dividers]]"
  - "[[FEEG1004 B4 - Operational Amplifiers]]"
  - "[[FEEG1004 D3 - AC Filters and Bode Plots]]"
next_topics: ["[[FEEG1004 E2 - Displacement Sensors - Potentiometric, Capacitive and Inductive]]"]
key_concepts:
  - "[[Transducer Static Characteristics]]"
  - "[[Passive and Active Transducers]]"
  - "[[RTDs and Thermistors]]"
  - "[[Thermocouples and Cold-Junction Compensation]]"
  - "[[Measurement Chain]]"
  - "[[Accuracy and Precision]]"
tutorial_sheets: []
sources:
  - "02 - Sources/S2 Transducers/S2-W26-31 Transducers 01 - Measurement Systems - Lecture Slides.pdf"
  - "02 - Sources/S1 Electronics/S1 Electronics Notes - Diodes Transistors Op-Amps and Digital - Mills.pdf"
  - "02 - Sources/Lectures/FEEG1004 Lecture 2025-03-24.txt"
---

# FEEG1004 E1 - Measurement Systems and Temperature Sensors

> [!abstract] Summary
> A measurement system is a chain: a primary sensing element responds to the physical measurand, a transducer turns that response into an electrical signal, signal conditioning (bridges, amplifiers, cold-junction compensation, anti-aliasing filters) scales and cleans it, and an analogue-to-digital converter (ADC) quantises it for recording, health monitoring or control. Its static quality is described by sensitivity $S=\mathrm dA_{\text{out}}/\mathrm dA_{\text{in}}$, linearity, resolution ($\Delta V=V_{\text{FS}}/2^n$ for an $n$-bit ADC), precision (random spread) and accuracy (absence of systematic bias), and its sampling must satisfy $f_s>2f_{\max}$ to avoid aliasing. Passive transducers such as metallic RTDs (about $+0.39\%\,^\circ\text{C}^{-1}$ for a Pt100) and NTC thermistors (about $-4\%\,^\circ\text{C}^{-1}$, over a narrower range) change resistance and need external excitation. Active transducers such as thermocouples generate their own Seebeck EMF of tens of $\mu\text{V}\,^\circ\text{C}^{-1}$, proportional to the temperature difference between two junctions, so an absolute reading needs cold-junction compensation (CJC) and op-amp amplification.

> [!summary]- Exam use: quick path
> - **Use it when:** a question asks you to distinguish sensor characteristics, find an ADC resolution or an alias frequency, or compare and apply RTDs, thermistors and thermocouples.
> - **Assumptions:** static calibration for sensitivity and linearity; an ideal $n$-bit ADC over $V_{\text{FS}}$; the RTD polynomial with $T$ in $^\circ\text{C}$ and the thermistor exponential with $T$ in K; a constant Seebeck coefficient $S_{AB}$.
> - **Method:** 1. Find $\Delta V=V_{\text{FS}}/2^n$ and convert to the measurand with the sensitivity. 2. Compare $\Delta V$ with the noise floor; the larger sets the smallest detectable change. 3. Check $f_s>2f_{\max}$, otherwise find $f_{\text{alias}}=|f_{\text{sig}}-kf_s|$. 4. For a thermocouple, $V_{\text{meas}}=S_{AB}(T_{\text{hot}}-T_{\text{ref}})$. 5. Add $V_{\text{CJC}}=S_{AB}(T_{\text{ref}}-0\,^\circ\text{C})$, then scale by the amplifier gain.
> - **Common mistakes:** treating ADC bit resolution as precision when the noise floor is larger than one LSB; reading a thermocouple voltage as if referenced to $0\,^\circ\text{C}$, which under-reads by $T_{\text{ref}}$.
> - **Practise:** [[#ADC resolution, noise floor and aliasing]] · [[#Type J thermocouple with CJC and a thermistor alarm]] (no tutorial sheet is set on this topic)

Aerospace, mechanical and civil systems depend on continuous measurement to run safely. Flight and engine controllers need real-time feedback of temperature, pressure, displacement and flow. **Health and Usage Monitoring Systems** (HUMS) and **Structural Health Monitoring** (SHM) networks track vibration and strain on helicopter gearboxes, jet-engine bearings and bridges, so that spalling or fatigue cracks are found before they cause failure. **Digital twins** feed live sensor streams into physics-based and machine-learning models to predict the remaining useful life of components.

All of this rests on the physical transducer and its analogue front end. If the wrong transducer is chosen for a harsh thermal environment, if its microvolt signal is swamped by $50\ \text{Hz}$ pickup before it reaches the amplifier, or if a high-frequency vibration is sampled below its Nyquist rate without an anti-aliasing filter, no downstream software can recover the lost information.

## 1. The measurement chain

An electronic measurement or **data acquisition** (DAQ) system is a cascade of blocks that turns a non-electrical quantity into calibrated digital data.

![[ee_e1_measurement_chain.png|900]]

The chain starts with the **measurand**, the physical quantity to be determined: linear or angular displacement, velocity, acceleration, vibration, static or dynamic force, fluid pressure, strain, flow rate or temperature. The **primary sensing element** is the mechanical or thermal body that interacts directly with the measurand and converts it into a predictable deformation or thermal state. A flexible diaphragm or bellows deflects under pressure, a cantilever beam or load-cell billet strains under force, a Venturi constriction turns flow velocity into a pressure drop, and a float arm rises with liquid level.

The **transducer** converts the output of the primary element into an electrical parameter: a change in resistance $R$, capacitance $C$ or inductance $L$, or a generated voltage $V$ or current $I$. A foil strain gauge bonded to a pressure diaphragm, for example, turns surface strain into a fractional resistance change $\Delta R/R$.

**Signal conditioning** is the analogue circuitry that turns raw sensor outputs (often microvolts or millivolts, or picofarad capacitance shifts) into a clean, linearised, low-impedance voltage matched to the input range of the digitiser, typically $0$–$10\ \text{V}$ or $\pm5\ \text{V}$, while rejecting out-of-band noise. Its main parts are Wheatstone bridges, op-amp buffers, differential or inverting amplifiers ([[FEEG1004 B4 - Operational Amplifiers]]), cold-junction compensators, demodulators, and RC or active filters ([[FEEG1004 D3 - AC Filters and Bode Plots]]). Finally the **analogue-to-digital converter** samples the conditioned voltage at a fixed clock rate $f_s$ and quantises each sample into an $n$-bit binary number ($2^n$ levels) for logging, digital signal processing, display or closed-loop actuation through a digital-to-analogue converter (DAC).

## 2. Static characteristics

Nine standard terms describe a sensor on a datasheet or a calibrated channel: sensitivity, linearity, resolution, precision, uncertainty, accuracy, repeatability, drift and error.

### Sensitivity and linearity

Let $A_{\text{in}}$ be the input measurand (temperature $T$ in $^\circ\text{C}$, displacement $x$ in mm, pressure $p$ in Pa) and $A_{\text{out}}$ the electrical output (usually $V_{\text{out}}$ in V or mV, or a resistance in $\Omega$). The **sensitivity** $S$, also called responsivity, scale factor or transfer gain, is the local gradient of the static calibration curve:

$$
S = \frac{\mathrm{d}A_{\text{out}}}{\mathrm{d}A_{\text{in}}} \approx \frac{\Delta A_{\text{out}}}{\Delta A_{\text{in}}}.
$$

Typical units are $\text{V mm}^{-1}$, $\text{mV }^\circ\text{C}^{-1}$, $\text{mV Pa}^{-1}$ and $\Omega\ ^\circ\text{C}^{-1}$.

A transducer is **linear** over a range if $S$ is constant there, so that $A_{\text{out}}=S\,A_{\text{in}}+A_0$ is a straight line. A constant scale factor converts any change in output directly into a change in measurand, $\Delta A_{\text{in}}=\Delta A_{\text{out}}/S$, with no look-up table or polynomial inversion and no variation of sensitivity across the span. In a non-linear device the slope varies with the operating point. **Non-linearity** is quantified as the largest deviation between the calibration curve and a reference straight line, expressed as a percentage of full-scale output (% FSO). A non-linear sensor can be linearised in hardware, with op-amp feedback or bridge topologies as in [[FEEG1004 E2 - Displacement Sensors - Potentiometric, Capacitive and Inductive]], or in software with look-up tables or polynomial fits.

![[ee_e1_static_characteristics.png|900]]

### Resolution, precision, uncertainty and accuracy

**Resolution** is the smallest change in the measured quantity that the instrument can detect or display. An $n$-bit ADC spanning a full-scale voltage $V_{\text{FS}}$ divides its range into $N=2^n$ codes, so one least significant bit (LSB) is

$$
\Delta V_{\text{res}} = \frac{V_{\text{FS}}}{2^n}.
$$

Dividing by the system sensitivity gives the smallest resolvable change in the measurand, $\Delta A_{\text{in,res}}=\Delta V_{\text{res}}/S$.

**Precision** is the tightness of clustering of repeated measurements of the same constant input. It is governed by random electronic and thermal noise, hysteresis and short-term fluctuations, and high precision means a small standard deviation $\sigma$ of the readings.

> [!warning] More ADC bits do not mean more precision
> For a $16\text{-bit}$ ADC with $V_{\text{FS}}=10\ \text{V}$ the step is $\Delta V_{\text{res}}=10/2^{16}=10/65\,536=0.1526\ \text{mV}\approx0.15\ \text{mV}$. If the sensor and amplifier have a noise floor of $10\ \text{mV}$, the lowest $\approx6$ bits of the ADC toggle randomly on noise. The smallest physical change that can be reliably distinguished is set by the coarser of the quantisation step and the noise floor. Equally, if an unamplified signal swings across only half or a quarter of $V_{\text{FS}}$, most of the $2^n$ codes go unused, so signal conditioning must scale the signal to fill $V_{\text{FS}}$.

**Uncertainty** is the statistical interval around a measured value within which the true value is expected to lie; it is tied to the standard deviation, e.g. $\pm2\sigma$ for a $95\%$ confidence interval. **Accuracy** is the closeness of the mean of the measured values to the true value. An instrument with high precision (small $\sigma$) but poor accuracy has a systematic **bias** (offset error): its readings form a tight cluster away from the centre of the target in the figure below. A constant bias is deterministic, so a precise but inaccurate sensor can be made accurate by calibration that subtracts the offset, whereas an imprecise (noisy) sensor cannot be fixed by a static offset calibration.

**Repeatability** is the agreement among consecutive measurements of the same quantity under the same conditions over a short time. **Drift** is a slow, unwanted variation of the output that is not caused by any change in $A_{\text{in}}$, commonly from ambient temperature shifts, component ageing or supply sag. **Error** is the algebraic difference between an individual reading and the true value, $\text{Error}=A_{\text{measured}}-A_{\text{true}}$.

![[ee_e1_accuracy_precision.png|900]]

### Sampling, the Nyquist criterion and aliasing

For dynamic quantities such as bearing vibration, shaft whirl or wing flutter, the ADC samples $v(t)$ at intervals $\Delta t=1/f_s$, where $f_s$ is the **sampling frequency** in samples per second (Hz). If the signal contains a component $f_{\text{sig}}$ that is too high relative to $f_s$, the samples cannot distinguish it from a much lower frequency. This artefact is **aliasing**, the same effect that makes helicopter rotor blades or wagon wheels on camera appear to turn slowly or stand still when the frame rate is close to a multiple of the blade-passing rate.

A sinusoid of frequency $f_{\text{sig}}$ sampled at $f_s<2f_{\text{sig}}$ appears in the sampled data as a false low-frequency alias at

$$
f_{\text{alias}} = \big|f_{\text{sig}} - k f_s\big| \quad \left(\text{where } k \in \mathbb{Z} \text{ places } f_{\text{alias}} \le \frac{f_s}{2}\right).
$$

Sampling a $900\ \text{Hz}$ vibration tone at $f_s=1000\ \text{Hz}$, for example, produces a false $100\ \text{Hz}$ wave, $|900-1000|=100\ \text{Hz}$. To prevent aliasing, the **Nyquist sampling criterion** requires the sampling frequency to exceed twice the highest frequency $f_{\max}$ present in the analogue signal:

$$
f_s > 2f_{\text{max}} \quad \Longleftrightarrow \quad f_{\text{max}} < f_{\text{Nyquist}} = \frac{f_s}{2}.
$$

Digital processing cannot undo aliasing once the samples are taken, so an analogue low-pass **anti-aliasing filter** ([[FEEG1004 D3 - AC Filters and Bode Plots]]) must sit in the conditioning block before the ADC to attenuate everything above $f_s/2$.

## 3. Passive and active transducers

Electrical transducers are divided by whether they need an external excitation supply to produce an output. **Passive** transducers change an impedance ($R$, $C$ or $L$) and need an external source to turn that change into a signal; **active** transducers generate a charge, voltage or current directly from a physical effect.

| Category | External excitation required? | Physical mechanism and governing equations | Representative examples |
| :--- | :--- | :--- | :--- |
| Passive transducers | Yes (an external DC or AC voltage or current source) | Measurand alters a passive circuit impedance parameter:<br>• Resistance: $R = \dfrac{\rho\ell}{A}$<br>• Capacitance: $C = \dfrac{\varepsilon_0\varepsilon_r A}{d}$<br>• Inductance: $L = \dfrac{N^2}{\mathcal{R}} = \dfrac{\mu_0\mu_r N^2 A}{\ell}$ | • Metallic RTDs and semiconductor thermistors<br>• Potentiometers and foil/semiconductor strain gauges<br>• Capacitive proximity, MEMS and fuel-level probes<br>• Inductive proximity sensors and LVDTs |
| Active transducers | No (self-generating; converts physical energy directly into electrical energy) | Measurand directly generates a charge, voltage or current via a material/field coupling:<br>• Thermoelectric (Seebeck effect)<br>• Piezoelectric (stress-induced polarisation)<br>• Electromagnetic induction ($\mathcal{E} = -N\,\mathrm{d}\Phi/\mathrm{d}t$) | • Thermocouples (Type J, Type K, etc.)<br>• Piezoelectric accelerometers, dynamic pressure/knock sensors<br>• Moving-coil geophones and DC tachogenerators |
| Optical transducers | Yes (an LED, broadband source or laser) | Measurand modulates light intensity, phase, polarisation or Bragg wavelength $\lambda_B$ | • Fibre Bragg Grating (FBG) and flat-fibre composite strain/temperature sensors<br>• Optical shaft encoders |

An active transducer such as a thermocouple or piezoelectric crystal needs no excitation to generate its raw EMF, but any op-amp or ADC downstream in the conditioning chain still needs its own DC supply rails.

## 4. Temperature transducers

![[ee_e1_temperature_sensors.png|900]]

### RTDs and thermistors

A **resistance temperature detector** (RTD) is a pure-metal resistor, usually platinum, nickel or copper. In a metal the conduction band is populated at all temperatures, so raising $T$ mainly increases the thermal vibration (phonons) of the lattice ions. Electrons scatter more often and the resistivity $\rho(T)$ rises, a **positive temperature coefficient** (PTC). Over a broad range ($-200\,^\circ\text{C}$ to $+850\,^\circ\text{C}$ for platinum) the resistance at Celsius temperature $T$ follows the Callendar–Van Dusen polynomial about the ice-point resistance $R_0=R(0\,^\circ\text{C})$:

$$
R(T) = R_0\big(1 + \alpha_1 T + \alpha_2 T^2 + \dots + \alpha_n T^n\big) \quad (T \text{ in } ^\circ\text{C}).
$$

Differentiating gives $\mathrm dR/\mathrm dT=R_0(\alpha_1+2\alpha_2T+\dots)$, which depends slightly on $T$, so every RTD is weakly non-linear. For platinum, such as the industry-standard **Pt100** with $R_0=100.0\ \Omega$ at $0\,^\circ\text{C}$, $\alpha_1\approx+3.91\times10^{-3}\ ^\circ\text{C}^{-1}$ ($\approx+0.39\%\,^\circ\text{C}^{-1}$) and $|\alpha_2|\approx5.78\times10^{-7}\ ^\circ\text{C}^{-2}$. The quadratic term $\alpha_2T^2$ is therefore less than about $1.5\%$ of the linear term $\alpha_1T$ up to $100\,^\circ\text{C}$, and the linear approximation

$$
R(T) \approx R_0(1 + \alpha_1 T) \implies \frac{\mathrm{d}R}{\mathrm{d}T} \approx \alpha_1 R_0
$$

is accurate to a fraction of a degree near room temperature. Nickel and copper RTDs have steeper, more curved characteristics.

A **thermistor** (thermally sensitive resistor) is made from sintered semiconductor oxides ([[FEEG1004 B1 - Semiconductors and Diodes]]). The standard **negative temperature coefficient** (NTC) thermistor behaves in the opposite way to a metal. A semiconductor has an energy gap $E_g$ between its valence and conduction bands, so raising the absolute temperature $T$ excites many more carriers across the gap according to a Boltzmann exponential factor. This rise in carrier concentration outweighs the extra lattice scattering, and the resistance falls steeply with temperature:

$$
R(T) = R_0\exp\!\left[B\left(\frac{1}{T} - \frac{1}{T_0}\right)\right] \quad (T,\ T_0 \text{ in kelvin}),
$$

where $R_0$ is the rated resistance at the reference temperature $T_0$ (typically $T_0=25\,^\circ\text{C}=298.15\ \text{K}$, e.g. $R_0=10\ \text{k}\Omega$) and $B$ is a material constant in kelvin, typically $B\approx3000$–$4500\ \text{K}$. Differentiating gives the local sensitivity and the fractional temperature coefficient:

$$
\begin{aligned}
\frac{\mathrm{d}R}{\mathrm{d}T} &= R_0\exp\!\left[B\left(\frac{1}{T} - \frac{1}{T_0}\right)\right] \cdot \frac{\mathrm{d}}{\mathrm{d}T}\!\left(\frac{B}{T}\right) \\
&= R(T)\left(-\frac{B}{T^2}\right), \\
\alpha_{\text{NTC}} = \frac{1}{R}\frac{\mathrm{d}R}{\mathrm{d}T} &= -\frac{B}{T^2} \approx -4\%\,^\circ\text{C}^{-1} \quad (\text{at } T \approx 300\ \text{K}).
\end{aligned}
$$

An NTC thermistor therefore has about ten times the fractional sensitivity of an RTD ($\approx-4\%\,^\circ\text{C}^{-1}$ against $+0.39\%\,^\circ\text{C}^{-1}$), which lets it detect millikelvin changes without high-gain amplifiers. The costs are strong exponential non-linearity and a restricted range, typically $-90\,^\circ\text{C}$ to $+130\,^\circ\text{C}$, or up to $300\,^\circ\text{C}$ for glass-encapsulated types. Specialised **PTC thermistors**, made of barium-titanate ceramic, show an abrupt jump in resistance of several orders of magnitude above a Curie switching temperature and are used as self-resetting overcurrent fuses and motor-winding protectors.

### Thermocouples and cold-junction compensation

When wires of two **dissimilar metals** $A$ and $B$ are joined, for example iron and constantan in a **Type J** thermocouple or chromel and alumel in a **Type K**, the difference in their work functions (Fermi levels) makes electrons diffuse across the interface and sets up a temperature-dependent **contact potential**. If the wires are joined at both ends into a loop and the two junctions are at different temperatures $T_{\text{hot}}$ and $T_{\text{ref}}$, the two contact potentials do not cancel and a net thermoelectric EMF drives a current round the loop. This is the **Seebeck effect** (thermoelectric effect).

Breaking one wire to insert a high-impedance voltmeter with copper terminals (metal $C$) creates two new contacts, $A$–$C$ and $B$–$C$, at the meter. When both are at the same temperature $T_{\text{ref}}$, the **law of intermediate metals** makes the pair equivalent to a single $A$–$B$ junction at $T_{\text{ref}}$, so the copper adds no EMF of its own. The open-circuit voltage is then a differential measurement, proportional to the temperature difference between the sensing (hot) junction and the reference (cold) junction:

$$
V_{\text{meas}} = S_{AB}\,(T_{\text{hot}} - T_{\text{ref}}),
$$

where $S_{AB}$ is the relative **Seebeck coefficient** of the pair, a few tens of microvolts per degree: $S_{AB}\approx52\ \mu\text{V}\,^\circ\text{C}^{-1}$ for Type J iron–constantan and $S_{AB}\approx41\ \mu\text{V}\,^\circ\text{C}^{-1}$ for Type K chromel–alumel.

A thermocouple measures only $T_{\text{hot}}-T_{\text{ref}}$, so an absolute reading needs $T_{\text{ref}}$. In laboratory calibration the reference junction sits in an insulated beaker of melting crushed ice and water, which phase equilibrium holds at $0.00\,^\circ\text{C}$. Wire $A$ goes to the positive meter terminal and a second length of wire $A$ from the ice bath goes to the negative terminal, so both meter connections are $A$–Cu at the same room temperature and cancel ($V_1-V_1=0$), leaving $V_{\text{meas}}=S_{AB}(T_{\text{hot}}-0\,^\circ\text{C})=S_{AB}T_{\text{hot}}$.

An ice bath is impractical in an engine bay or on a factory floor, so instruments use electronic **cold-junction compensation**. The $A$ and $B$ wires connect directly to an isothermal terminal block whose temperature $T_{\text{ref}}$ is measured continuously by a silicon IC transistor sensor (or a thermistor or RTD) mounted on the block. The CJC circuit generates an offset $V_{\text{CJC}}=S_{AB}(T_{\text{ref}}-0\,^\circ\text{C})$ equal to the error caused by the block not being at $0\,^\circ\text{C}$, adds it to the raw thermocouple voltage, and a negative-feedback op-amp of closed-loop gain $G$ amplifies the sum:

$$
\begin{aligned}
V_{\text{corr}} &= V_{\text{meas}} + V_{\text{CJC}} \\
&= S_{AB}(T_{\text{hot}} - T_{\text{ref}}) + S_{AB}(T_{\text{ref}} - 0\,^\circ\text{C}) \\
&= S_{AB}\,T_{\text{hot}}, \\
V_{\text{out}} &= G\,V_{\text{corr}} = (G\,S_{AB})\,T_{\text{hot}}.
\end{aligned}
$$

Monolithic thermocouple amplifier ICs combine the CJC sensor and the gain stage for a given thermocouple type (e.g. J or K) and deliver a linearised scale factor such as $10\ \text{mV}\,^\circ\text{C}^{-1}$ directly to a voltmeter or ADC.

| Sensor type | Class | Typical range | Typical sensitivity | Linearity | Strengths and limitations |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Pt100 RTD (platinum metal) | Passive ($R$) | $-200\,^\circ\text{C}$ to $+850\,^\circ\text{C}$ | $+0.385\ \Omega\,^\circ\text{C}^{-1}$ ($\approx +0.39\%\,^\circ\text{C}^{-1}$) | Very good (weak quadratic term) | Highest long-term stability and accuracy; requires excitation current (self-heating care) and has low fractional sensitivity |
| NTC thermistor (semiconductor) | Passive ($R$) | $-90\,^\circ\text{C}$ to $+130\,^\circ\text{C}$ (up to $300\,^\circ\text{C}$) | $\approx -4\%\,^\circ\text{C}^{-1}$ ($-444\ \Omega\,^\circ\text{C}^{-1}$ at $25\,^\circ\text{C}$ for $10\ \text{k}\Omega$) | Poor (exponential $e^{B/T}$) | High sensitivity for small $\Delta T$ near room temperature; limited temperature range and strongly non-linear |
| Thermocouple (e.g. Type J, K) | Active (Seebeck $V$) | $-200\,^\circ\text{C}$ to $>1200\,^\circ\text{C}$ | $41\text{--}52\ \mu\text{V}\,^\circ\text{C}^{-1}$ | Moderate (polynomial tables) | Self-powered, tiny thermal mass, rugged at jet-engine temperatures; the small $\mu\text{V}$ output needs CJC and high-gain low-noise amplification |

## Worked examples

### ADC resolution, noise floor and aliasing

A data acquisition system digitises a conditioned sensor voltage over $V_{\text{FS}}=10.0\ \text{V}$. (a) Find the number of levels $N=2^n$ and the resolution $\Delta V_{\text{res}}$ for $3$-, $6$-, $8$- and $16$-bit ADCs. (b) The input to the $16$-bit ADC has a random noise floor of $V_{\text{noise}}=10.0\ \text{mV}$ peak-to-peak; is the $16$-bit resolution achieved, and how many noise-free bits are there? (c) In a bearing vibration test the ADC samples at $f_s=1.00\ \text{kHz}$ ($1000\ \text{samples s}^{-1}$) without an anti-aliasing filter, and the bearing develops a spalling resonance at $f_{\text{sig}}=900\ \text{Hz}$; find the apparent frequency in the data and the minimum sampling rate that avoids aliasing.

(a) With $\Delta V_{\text{res}}=V_{\text{FS}}/2^n$ and $V_{\text{FS}}=10.0\ \text{V}$,

$$
\begin{aligned}
n = 3:\quad N &= 2^3 = 8\ \text{levels}, &\Delta V_{\text{res}} &= \frac{10.0\ \text{V}}{8} = 1.250\ \text{V} = 1250\ \text{mV}, \\
n = 6:\quad N &= 2^6 = 64\ \text{levels}, &\Delta V_{\text{res}} &= \frac{10.0\ \text{V}}{64} = 0.15625\ \text{V} = 156.3\ \text{mV}, \\
n = 8:\quad N &= 2^8 = 256\ \text{levels}, &\Delta V_{\text{res}} &= \frac{10.0\ \text{V}}{256} = 0.03906\ \text{V} = 39.06\ \text{mV}, \\
n = 16:\quad N &= 2^{16} = 65\,536\ \text{levels}, &\Delta V_{\text{res}} &= \frac{10.0\ \text{V}}{65\,536} = 1.5259 \times 10^{-4}\ \text{V} \approx 0.153\ \text{mV}.
\end{aligned}
$$

If an unamplified signal swung across only $5.0\ \text{V}$ of the $10.0\ \text{V}$ range, only half the codes would be used ($4$ levels at $3$ bits, $32$ at $6$ bits); amplifying by $\times2$ before the ADC doubles the effective resolution.

(b) The $16$-bit ADC resolves $\Delta V_{\text{res}}=0.1526\ \text{mV}$, but the noise floor spans

$$
\frac{V_{\text{noise}}}{\Delta V_{\text{res}}} = \frac{10.0\ \text{mV}}{0.15259\ \text{mV}} = 65.54\ \text{quantisation steps}.
$$

The measurement is therefore precision-limited by the $10.0\ \text{mV}$ noise, and the $0.153\ \text{mV}$ digital resolution is irrelevant unless the noise is filtered out. The number of noise-free subdivisions of the full scale is $10.0\ \text{V}/0.010\ \text{V}=1000$, which corresponds to

$$
n_{\text{eff}} = \log_2\!\left(\frac{V_{\text{FS}}}{V_{\text{noise}}}\right) = \log_2(1000) = \frac{\ln 1000}{\ln 2} = 9.97\ \text{bits} \approx 10\ \text{bits}.
$$

(c) At $f_s=1000\ \text{Hz}$ the Nyquist frequency is $f_s/2=500\ \text{Hz}$. Since $f_{\text{sig}}=900\ \text{Hz}>500\ \text{Hz}$, the signal is undersampled and folds back to

$$
f_{\text{alias}} = |f_s - f_{\text{sig}}| = 1000\ \text{Hz} - 900\ \text{Hz} = 100\ \text{Hz}.
$$

To satisfy the Nyquist criterion for $f_{\max}=900\ \text{Hz}$,

$$
f_s > 2f_{\text{max}} = 2 \times 900\ \text{Hz} = 1800\ \text{Hz} \quad (1.80\ \text{kHz}).
$$

> [!check] The 900 Hz and 100 Hz samples are identical
> The $k$-th sample ($k\in\mathbb Z$) is taken at $t_k=k/f_s=k/1000\ \text{s}$. For $f_{\text{sig}}=900\ \text{Hz}$,
> $$\cos\!\left(2\pi \times 900 \times \frac{k}{1000}\right) = \cos\!\left(2\pi k - 2\pi \times 100 \times \frac{k}{1000}\right) = \cos\!\left(2\pi \times 100\,t_k\right),$$
> so every sample of the $900\ \text{Hz}$ cosine taken at $1000\ \text{Hz}$ equals the corresponding sample of a $100\ \text{Hz}$ cosine.

### Pt100 RTD against NTC thermistor sensitivity

Compare the resistance and sensitivity at $T_1=25\,^\circ\text{C}$ and $T_2=50\,^\circ\text{C}$ of (a) a Pt100 RTD with $R_0=100.0\ \Omega$ at $0\,^\circ\text{C}$, $\alpha_1=3.9083\times10^{-3}\ ^\circ\text{C}^{-1}$ and $\alpha_2=-5.775\times10^{-7}\ ^\circ\text{C}^{-2}$, and (b) an NTC thermistor with $R_{25}=10.00\ \text{k}\Omega$ at $T_0=25\,^\circ\text{C}$ ($298.15\ \text{K}$) and $B=3950\ \text{K}$.

(a) With $T$ in $^\circ\text{C}$, $R(T)=R_0(1+\alpha_1T+\alpha_2T^2)$ gives

$$
\begin{aligned}
R(25\,^\circ\text{C}) &= 100.0\big[1 + (3.9083 \times 10^{-3})(25) + (-5.775 \times 10^{-7})(25)^2\big] \\
&= 100.0\big(1 + 0.097708 - 0.000361\big) = 109.73\ \Omega, \\
R(50\,^\circ\text{C}) &= 100.0\big[1 + (3.9083 \times 10^{-3})(50) + (-5.775 \times 10^{-7})(50)^2\big] \\
&= 100.0\big(1 + 0.195415 - 0.001444\big) = 119.40\ \Omega.
\end{aligned}
$$

The local sensitivity $\mathrm dR/\mathrm dT=R_0(\alpha_1+2\alpha_2T)$ is

$$
\begin{aligned}
\left.\frac{\mathrm{d}R}{\mathrm{d}T}\right|_{25\,^\circ\text{C}} &= 100.0\big[3.9083 \times 10^{-3} + 2(-5.775 \times 10^{-7})(25)\big] = +0.3879\ \Omega\,^\circ\text{C}^{-1} \quad (+0.354\%\,^\circ\text{C}^{-1}), \\
\left.\frac{\mathrm{d}R}{\mathrm{d}T}\right|_{50\,^\circ\text{C}} &= 100.0\big[3.9083 \times 10^{-3} + 2(-5.775 \times 10^{-7})(50)\big] = +0.3851\ \Omega\,^\circ\text{C}^{-1} \quad (+0.322\%\,^\circ\text{C}^{-1}).
\end{aligned}
$$

Over the $25\,^\circ\text{C}$ span the slope changes by only $0.74\%$, so the RTD is close to linear.

(b) In kelvin, $T_0=T_1=25+273.15=298.15\ \text{K}$ and $T_2=50+273.15=323.15\ \text{K}$. At $25\,^\circ\text{C}$, $R(298.15\ \text{K})=10.00\ \text{k}\Omega$. At $50\,^\circ\text{C}$,

$$
\begin{aligned}
R(323.15\ \text{K}) &= 10\,000\,\exp\!\left[3950\left(\frac{1}{323.15\ \text{K}} - \frac{1}{298.15\ \text{K}}\right)\right] \\
&= 10\,000\,\exp\!\big[3950(-2.5948 \times 10^{-4})\big] \\
&= 10\,000\,\exp(-1.02494) \\
&= 3588.2\ \Omega \approx 3.59\ \text{k}\Omega.
\end{aligned}
$$

The local sensitivity $\mathrm dR/\mathrm dT=-R(T)B/T^2$ is

$$
\begin{aligned}
\left.\frac{\mathrm{d}R}{\mathrm{d}T}\right|_{25\,^\circ\text{C}} &= -(10\,000\ \Omega)\frac{3950\ \text{K}}{(298.15\ \text{K})^2} = -444.4\ \Omega\,^\circ\text{C}^{-1} \quad (-4.44\%\,^\circ\text{C}^{-1}), \\
\left.\frac{\mathrm{d}R}{\mathrm{d}T}\right|_{50\,^\circ\text{C}} &= -(3588.2\ \Omega)\frac{3950\ \text{K}}{(323.15\ \text{K})^2} = -135.7\ \Omega\,^\circ\text{C}^{-1} \quad (-3.78\%\,^\circ\text{C}^{-1}).
\end{aligned}
$$

> [!check] Sensitivity against linearity
> Between $25\,^\circ\text{C}$ and $50\,^\circ\text{C}$ the Pt100 changes by $+9.66\ \Omega$ ($+8.8\%$) while the thermistor changes by $-6412\ \Omega$ ($-64.1\%$). Over the same interval the thermistor's $\mathrm dR/\mathrm dT$ falls by a factor of $3.27$ (from $-444.4\ \Omega\,^\circ\text{C}^{-1}$ to $-135.7\ \Omega\,^\circ\text{C}^{-1}$), so its high sensitivity comes with strong exponential non-linearity.

### Type J thermocouple with CJC and a thermistor alarm

A Type J (iron–constantan) thermocouple with $S=52.0\ \mu\text{V}\,^\circ\text{C}^{-1}$ monitors an engine bearing at $T_{\text{hot}}=180\,^\circ\text{C}$, and its wires end at an amplifier block at $T_{\text{ref}}=25.0\,^\circ\text{C}$. Find (a) the raw voltage $V_{\text{meas}}$, (b) the error if $V_{\text{meas}}$ were read as referenced to $0\,^\circ\text{C}$, (c) the compensation voltage $V_{\text{CJC}}$, and (d) the gain $G$ for a calibrated output of $10.0\ \text{mV}\,^\circ\text{C}^{-1}$ ($1.800\ \text{V}$ at $180\,^\circ\text{C}$). Then (e), in a high-temperature warning circuit, a single-supply op-amp comparator on $V_S=+6.0\ \text{V}$ and $0\ \text{V}$ has its inverting input held at $V_{\text{REF}}=+3.0\ \text{V}$ by two equal resistors. Its non-inverting input $V_+$ comes from a divider with the $10\ \text{k}\Omega$ NTC thermistor of [[#Pt100 RTD against NTC thermistor sensitivity]] in the upper arm (to $+6.0\ \text{V}$) and a fixed $R_{\text{set}}$ in the lower arm (to $0\ \text{V}$). Choose $R_{\text{set}}$ so that the warning lamp comes on above $50\,^\circ\text{C}$.

(a) The raw terminal voltage is

$$
\begin{aligned}
V_{\text{meas}} &= S\,(T_{\text{hot}} - T_{\text{ref}}) \\
&= (52.0\ \mu\text{V}\,^\circ\text{C}^{-1})(180\,^\circ\text{C} - 25.0\,^\circ\text{C}) \\
&= (52.0 \times 10^{-6}\ \text{V}\,^\circ\text{C}^{-1})(155.0\,^\circ\text{C}) = 8.060 \times 10^{-3}\ \text{V} = 8.060\ \text{mV}.
\end{aligned}
$$

(b) Dividing $8.060\ \text{mV}$ by $52.0\ \mu\text{V}\,^\circ\text{C}^{-1}$ would indicate $T_{\text{apparent}}=155.0\,^\circ\text{C}$, under-reading the bearing by the full cold-junction offset of $-25.0\,^\circ\text{C}$.

(c) The IC sensor on the block measures $T_{\text{ref}}=25.0\,^\circ\text{C}$ and the CJC circuit generates

$$
V_{\text{CJC}} = S\,(T_{\text{ref}} - 0\,^\circ\text{C}) = (52.0\ \mu\text{V}\,^\circ\text{C}^{-1})(25.0\,^\circ\text{C}) = 1.300\ \text{mV}.
$$

Adding it restores the $0\,^\circ\text{C}$-referenced EMF:

$$
V_{\text{corr}} = V_{\text{meas}} + V_{\text{CJC}} = 8.060\ \text{mV} + 1.300\ \text{mV} = 9.360\ \text{mV} = (52.0\ \mu\text{V}\,^\circ\text{C}^{-1})(180.0\,^\circ\text{C}).
$$

(d) The gain for $10.0\ \text{mV}\,^\circ\text{C}^{-1}$ is

$$
G = \frac{10.0\ \text{mV}\,^\circ\text{C}^{-1}}{52.0\ \mu\text{V}\,^\circ\text{C}^{-1}} = \frac{10.0 \times 10^{-3}}{52.0 \times 10^{-6}} = 192.3,
$$

giving $V_{\text{out}}(180\,^\circ\text{C})=G\,V_{\text{corr}}=192.31\times9.360\ \text{mV}=1.800\ \text{V}$.

(e) The divider feeding $V_+$ has the thermistor $R_T(T)$ above and $R_{\text{set}}$ below, across $+6.0\ \text{V}$:

$$
V_+(T) = 6.0\ \text{V} \times \frac{R_{\text{set}}}{R_T(T) + R_{\text{set}}}.
$$

The comparator switches from $0\ \text{V}$ (lamp off) to $+6.0\ \text{V}$ (lamp on) when $V_+(T)>V_{\text{REF}}=+3.0\ \text{V}$, which happens when $R_T(T)<R_{\text{set}}$ (bridge balance). At $50\,^\circ\text{C}$ the thermistor has $R_T(50\,^\circ\text{C})=3.59\ \text{k}\Omega$, so choose

$$
R_{\text{set}} = R_T(50\,^\circ\text{C}) = 3.59\ \text{k}\Omega.
$$

For $T<50\,^\circ\text{C}$, $R_T(T)>3.59\ \text{k}\Omega$, so $V_+<3.0\ \text{V}$ and $V_{\text{out}}=0\ \text{V}$. As soon as $T$ rises above $50\,^\circ\text{C}$, $R_T(T)$ drops below $3.59\ \text{k}\Omega$, so $V_+>3.0\ \text{V}$ and $V_{\text{out}}\approx+6.0\ \text{V}$, lighting the lamp.

> [!check] Comparator polarity at 25 °C and 100 °C
> At $T=25\,^\circ\text{C}$ ($R_T=10.00\ \text{k}\Omega$), $V_+=6.0\times\dfrac{3.588}{10.00+3.588}=+1.584\ \text{V}<V_{\text{REF}}=3.00\ \text{V}$, so $V_+-V_-=-1.416\ \text{V}<0$ and the output stays at $0\ \text{V}$ (lamp off). At $T=100\,^\circ\text{C}$ ($R_T=0.698\ \text{k}\Omega$), $V_+=6.0\times\dfrac{3.588}{0.698+3.588}=+5.023\ \text{V}>3.00\ \text{V}$, so $V_+-V_-=+2.023\ \text{V}>0$ and the comparator saturates at $+6.0\ \text{V}$ (lamp on).

## Links

- Parent: [[FEEG1004 Electronics Hub]]
- Previous: [[FEEG1004 D4 - AC Power and Power Factor]]
- Next: [[FEEG1004 E2 - Displacement Sensors - Potentiometric, Capacitive and Inductive]]
- Concepts: [[Transducer Static Characteristics]] · [[Passive and Active Transducers]] · [[RTDs and Thermistors]] · [[Thermocouples and Cold-Junction Compensation]] · [[Measurement Chain]] · [[Accuracy and Precision]]
- Year 2 Mechatronics extends these static characteristics to first- and second-order sensor dynamics, bandwidth, and complementary and Kalman sensor fusion in [[SESA2027 C1 - Sensing Systems, Sensor Principles and Sensor Fusion]] and [[SESA2027 C2 - Sensor Characteristics, Dynamics and Design]].
- ADC quantisation noise, sample-and-hold aperture and anti-aliasing filter design are developed in [[SESA2027 C3 - Signal Conditioning, Digitisation and Digital Filtering]] and [[ADC Quantisation and Resolution]].
- Thermocouples measure exhaust-gas and turbine-entry temperatures in jet engines ([[Turbine Entry Temperature and Blade Cooling]], [[SESA2023 W06 - Jet Engine Cycle Analysis - Brayton, Ramjet, Turbojet and Reheat]]), while platinum resistance thermometers and NTC thermistors monitor spacecraft radiators and battery packs ([[SESA2024 10 - Thermal Control]]).

## Sources

- `02 - Sources/S2 Transducers/S2-W26-31 Transducers 01 - Measurement Systems - Lecture Slides.pdf`: instrumentation chain, mechanical measurands, static definitions (sensitivity, linearity, resolution, precision, uncertainty, accuracy, repeatability, drift, error), passive, active and optical transducers, RTDs, thermistors (slide 19), thermocouples, ice-bath reference and cold-junction compensation (slides 21–25).
- `02 - Sources/Lectures/FEEG1004 Lecture 2025-03-24.txt` (ll. 1–772): SHM/HUMS and digital-twin motivation, Safran aero-engine bearing instrumentation, metrological definitions, RTD against thermistor trade-offs, the Seebeck effect and CJC, DAQ signal conditioning, $3$-, $6$-, $8$- and $16$-bit ADC quantisation, Nyquist sampling, the helicopter-rotor and $900\ \text{Hz}$ aliasing examples, and anti-aliasing filters.
- `02 - Sources/S1 Electronics/S1 Electronics Notes - Diodes Transistors Op-Amps and Digital - Mills.pdf`: §1.6.7, pp. 36–37 (NTC and PTC thermistors, BJT relay thermostat); §2.2.3, p. 45 (op-amp bridge-comparator high-temperature warning circuit, the basis of the alarm in the thermocouple worked example).
- Worked-example values recomputed in Python.

## Self-study tasks

### Core

- [ ] Compute $\Delta V_{\text{res}}=10/2^{16}$ and explain why a $10\ \text{mV}$ noise floor makes a $10\ \text{V}$ full-scale system precision-limited rather than resolution-limited (Transducers 01 slides 10–11; Lecture 2025-03-24, ll. 177–210, 570–645). → [[#ADC resolution, noise floor and aliasing]]
- [ ] Explain why a $900\ \text{Hz}$ tone sampled at $1000\ \text{samples s}^{-1}$ appears at $100\ \text{Hz}$, and state the Nyquist requirement (Lecture 2025-03-24, ll. 655–713). → [[#Sampling, the Nyquist criterion and aliasing]]; [[#ADC resolution, noise floor and aliasing]]
- [ ] Compare the resistance–temperature laws, sensitivities and temperature limits of metallic RTDs and semiconductor thermistors (Transducers 01 slide 19; Lecture 2025-03-24, ll. 295–369). → [[#RTDs and thermistors]]; [[#Pt100 RTD against NTC thermistor sensitivity]]
- [ ] Explain why a thermocouple measures a temperature difference, how an ice bath or electronic CJC gives an absolute reading, and how an NTC thermistor drives an op-amp comparator alarm (Transducers 01 slides 21–25; Lecture 2025-03-24, ll. 371–466; Mills §2.2.3 p. 45). → [[#Thermocouples and cold-junction compensation]]; [[#Type J thermocouple with CJC and a thermistor alarm]]

### Further practice

- [ ] A Pt100 excited by a constant $1.00\ \text{mA}$ produces a voltage that rises from $100.0\ \text{mV}$ at $0\,^\circ\text{C}$ to $138.5\ \text{mV}$ at $100\,^\circ\text{C}$ ($\Delta V=38.5\ \text{mV}$). After the $100.0\ \text{mV}$ offset is subtracted, find the gain that maps $0$–$100\,^\circ\text{C}$ onto the full $0$–$10.0\ \text{V}$ range of a $12$-bit ADC, and the resulting temperature resolution per LSB (suggested, not lecturer-set). Answer: $G=10.0\ \text{V}/0.0385\ \text{V}=259.7$ and $\Delta T_{\text{res}}=100\,^\circ\text{C}/2^{12}=0.0244\,^\circ\text{C}$. → [[#Resolution, precision, uncertainty and accuracy]]

## Transcript and slide slips

> [!warning] Unstated change of temperature units between the RTD and thermistor laws (Transducers 01, slide 19)
> Where: [[#RTDs and thermistors]]
> Slide 19 prints the RTD polynomial $R=R_0(1+\alpha_1T+\alpha_2T^2+\dots)$ and the thermistor exponential $R=R_0e^{B(1/T-1/T_0)}$ on the same page and defines "$R_0$ is Resistance at $T=0\,^\circ\text{C}$" above the RTD equation, without noting that $T$ and $T_0$ in the thermistor exponential must be in kelvin, and that $T_0$ for thermistors is normally $298.15\ \text{K}=25\,^\circ\text{C}$. Substituting $T_0=0$ into $1/T_0$ would divide by zero.

> [!warning] "Precise and accurate" said of the biased distribution on slide 13 (Lecture 2025-03-24, ll. 238–241)
> Where: [[#Resolution, precision, uncertainty and accuracy]]
> For the third distribution on slide 13 (a narrow cluster displaced from the bullseye by a bias, labelled `Inaccurate, Precise`), a student answers "Precise and inaccurate" and the reply says "precise and accurate", while going on to describe a cluster that has moved off the bullseye with high precision. A tight cluster displaced by a bias is precise and inaccurate.

> [!warning] "10 increments" for a 1 Hz wave sampled at 1 kHz (Lecture 2025-03-24, ll. 657–660)
> Where: [[#Sampling, the Nyquist criterion and aliasing]]
> Describing the left-hand diagram of a $1\ \text{Hz}$ sinusoid sampled at $1\ \text{kHz}$ ($1000\ \text{samples s}^{-1}$), the recording says "so 10 increments over that period", which refers to the 10 schematic dots drawn on the slide rather than the actual $f_s/f_{\text{sig}}=1000/1=1000$ samples per period.
