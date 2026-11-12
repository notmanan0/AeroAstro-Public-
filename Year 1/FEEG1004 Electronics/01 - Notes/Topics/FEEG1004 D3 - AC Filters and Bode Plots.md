---
title: "FEEG1004 D3 - AC Filters and Bode Plots"
module: "FEEG1004 Electronics"
type: topic
stream: "Part D: AC Circuit Analysis"
order: 3
tags: [feeg1004, ac-circuits, filters, low-pass, high-pass, transfer-function, bode, decibels, cut-off]
aliases: ["AC Analysis 03", "RC filters", "Low-pass filter", "High-pass filter", "Cut-off frequency"]
date: 2026-09-27
status: lectured
coverage: "FEEG1004 Lecture 2025-03-11 (ll. 1–360); FEEG1004 Lecture 2025-03-14 (ll. 1–636); FEEG1004 Lecture 2025-03-18 (ll. 18–102)"
parent: ["[[FEEG1004 Electronics Hub]]"]
prerequisites: ["[[FEEG1004 D2 - Impedance and Phasor Circuit Analysis]]"]
next_topics: ["[[FEEG1004 D4 - AC Power and Power Factor]]"]
key_concepts: ["[[RC Low-Pass and High-Pass Filters]]", "[[Decibels]]", "[[Bode Plot]]", "[[Transfer Function]]"]
tutorial_sheets: ["[[FEEG1004 Tutorial 8 - Filters, Transfer Functions and Power Factor Solutions]]"]
sources:
  - "02 - Sources/S2 AC Analysis/S2-W24 AC Analysis 03 - Filters and Loads - Lecture Slides.pdf"
  - "02 - Sources/S2 AC Analysis/S2 AC Analysis Lecture Notes 2021 - Niu.pdf"
  - "02 - Sources/Lectures/FEEG1004 Lecture 2025-03-11.txt"
  - "02 - Sources/Lectures/FEEG1004 Lecture 2025-03-14.txt"
  - "02 - Sources/Lectures/FEEG1004 Lecture 2025-03-18.txt"
  - "02 - Sources/Tutorial Sheets/Tutorial Sheet 08 - AC Circuits 2 - Filters & Transfer Functions.pdf"
---

# FEEG1004 D3 - AC Filters and Bode Plots

> [!abstract] Summary
> Passive AC filters are frequency-selective voltage dividers: because $Z_C = 1/(j\omega C)$ and $Z_L = j\omega L$ depend on $\omega$, the transfer function $H(j\omega) = \mathbf{V}_{\text{out}}/\mathbf{V}_{\text{in}}$ has a gain $|H(\omega)|$ and a phase $\phi(\omega)$ that vary with frequency. An unloaded series-$R$, shunt-$C$ low-pass filter has $H = 1/(1 + j\omega RC)$ and the series-$C$, shunt-$R$ high-pass filter has $H = j\omega RC/(1 + j\omega RC)$; both have cut-off $\omega_c = 1/(RC)$ ($f_c = 1/(2\pi RC)$), where $|H| = 1/\sqrt{2}$ ($-3.01\ \text{dB}$), output power halves and the phase is $\mp 45^\circ$. On a Bode plot of $20\log_{10}|H|$ against $\log_{10}\omega$, cascaded gains add and a first-order filter reduces to straight-line asymptotes with slopes $0$ and $\pm 20\ \text{dB/decade}$. $RL$ filters have $\omega_c = R/L$, and a load $R_L$ across an $RC$ low-pass filter lowers the pass-band gain to $K = R_L/(R_1 + R_L)$ and raises the corner to $1/(R_{\text{TH}}C)$ with $R_{\text{TH}} = R_1 \parallel R_L$, which an op-amp buffer or active filter avoids.

> [!summary]- Exam use: quick path
> - **Use it when:** a question asks for the transfer function, gain in decibels, phase or cut-off frequency of an $RC$ or $RL$ network, or for the component value that gives a stated attenuation.
> - **Assumptions:** linear passive components in sinusoidal steady state; output unloaded unless a load $R_L$ is given; an ideal op-amp for active filters.
> - **Method:** 1. Identify the filter type from the limits $\omega \to 0$ (capacitor open, inductor short) and $\omega \to \infty$ (capacitor short, inductor open). 2. Write $H(j\omega)$ from the complex voltage divider and clear the inner fraction. 3. Take $|H|$ and $\phi$ as the modulus and argument of numerator over denominator. 4. Find $\omega_c$ from $|H(\omega_c)| = H_{\text{max}}/\sqrt{2}$, reducing a loaded filter to its Thévenin equivalent first. 5. Convert between decibels and linear gain with $|H| = 10^{G_{\text{dB}}/20}$.
> - **Common mistakes:** setting $|H(\omega_c)| = 1/\sqrt{2}$ when the pass-band gain is not 1; writing $f_c = 1/(RC)$ instead of $1/(2\pi RC)$.
> - **Practise:** [[#RC low-pass filter for 50 Hz hum]] · [[FEEG1004 Tutorial 8 - Filters, Transfer Functions and Power Factor Solutions#Q1: Loaded RC low-pass (R_1 = 1 kΩ, C = 10 µF, R_L = 10 kΩ)|Tutorial 8 Q1]]

Practical electrical signals rarely consist of a single sinusoid. The output of a small DC generator driven by a tidal turbine carries the wanted DC voltage together with high-frequency AC ripple from commutator switching and blade turbulence. An electrocardiogram (ECG) sensor produces a millivolt heartbeat waveform contaminated by $50\ \text{Hz}$ mains hum coupled from room wiring, and a multi-way loudspeaker must route bass frequencies to a woofer and treble frequencies to a tweeter. In each case a **filter** placed between source and load passes the wanted frequency band and attenuates the others.

A filter does this with the frequency-dependent reactances of capacitors ($X_C = 1/(\omega C)$) and inductors ($X_L = \omega L$). A reactive element combined with a resistor in a voltage divider gives a transfer function $H(j\omega) = \mathbf{V}_{\text{out}}/\mathbf{V}_{\text{in}}$ that passes some frequencies with near-unity gain and strongly attenuates others. Plotting the magnitude of $H(j\omega)$ in decibels and its phase against logarithmic frequency gives a **Bode plot**, on which a first-order filter reduces to straight-line asymptotes meeting at the half-power cut-off frequency $\omega_c$.

## 1. The transfer function and the four filter types

When a linear circuit of resistors, capacitors and inductors is driven by a steady sinusoidal input $v_{\text{in}}(t) = V_{\text{in},p}\cos(\omega t + \theta_{\text{in}})$ at angular frequency $\omega = 2\pi f$, every node voltage and branch current oscillates at the same angular frequency $\omega$. In the phasor domain ([[FEEG1004 D1 - AC Waveforms, RMS and Phasors]], [[FEEG1004 D2 - Impedance and Phasor Circuit Analysis]]), the input and output are RMS phasors $\mathbf{V}_{\text{in}} = V_{\text{in}}\angle\theta_{\text{in}}$ and $\mathbf{V}_{\text{out}} = V_{\text{out}}\angle\theta_{\text{out}}$. The steady-state behaviour at $\omega$ is then fully described by the **frequency-response transfer function** $H(j\omega)$, often written $H(\omega)$:

$$
\begin{aligned}
H(j\omega) &= \frac{\mathbf{V}_{\text{out}}}{\mathbf{V}_{\text{in}}} \\
&= \frac{V_{\text{out}}\,e^{j\theta_{\text{out}}}}{V_{\text{in}}\,e^{j\theta_{\text{in}}}} \\
&= \frac{V_{\text{out}}}{V_{\text{in}}}\,e^{j(\theta_{\text{out}} - \theta_{\text{in}})} \\
&= |H(\omega)|\,e^{j\phi(\omega)}
\end{aligned}
$$

Two real functions of frequency come from this polar form. The **magnitude response** (amplitude gain) $|H(\omega)| = \dfrac{|\mathbf{V}_{\text{out}}|}{|\mathbf{V}_{\text{in}}|} = \dfrac{V_{\text{out}}}{V_{\text{in}}}$ is the dimensionless ratio of output to input amplitude, the same whether both voltages are in peak or RMS volts. The **phase response** $\phi(\omega) = \angle H(j\omega) = \theta_{\text{out}} - \theta_{\text{in}}$ is the angle by which the output sinusoid leads ($\phi > 0$) or lags ($\phi < 0$) the input at frequency $\omega$, so that

$$
v_{\text{out}}(t) = |H(\omega)|\,V_{\text{in},p}\cos\!\big(\omega t + \theta_{\text{in}} + \phi(\omega)\big)
$$

Filters are classified by the band they transmit, the **pass band** where $|H(\omega)| \approx H_{\text{max}}$, and the band they reject, the **stop band** where $|H(\omega)| \ll H_{\text{max}}$. A **low-pass filter** (LPF) passes DC and low frequencies ($0 \le \omega < \omega_c$) and attenuates high frequencies ($\omega > \omega_c$), smoothing out high-frequency ripple or sensor noise. A **high-pass filter** (HPF) blocks DC ($\omega = 0$) and low frequencies and passes $\omega > \omega_c$, acting as an AC-coupling network that strips away DC offsets. A **band-pass filter** (BPF) passes a window $\omega_{c1} < \omega < \omega_{c2}$ and rejects frequencies on both sides, and a **band-stop** or **notch filter** rejects a narrow band around an interference frequency, such as $50\ \text{Hz}$ mains pickup, while passing frequencies above and below it.

## 2. Unloaded first-order RC filters

### RC low-pass transfer function, magnitude and phase

The simplest passive low-pass filter has a resistor $R$ in series with the source $\mathbf{V}_{\text{in}}$ and takes the output $\mathbf{V}_{\text{out}}$ across a shunt capacitor $C$ between the output node and ground. The output terminals are taken as **unloaded** (open-circuited, $I_{\text{out}} = 0$), so the same current $\mathbf{I}$ flows through $R$ and $C$ in series.

The frequency limits follow from the capacitor reactance $X_C = \dfrac{1}{\omega C}$ before any algebra. At DC and very low frequencies ($\omega \to 0$), $X_C \to \infty$ and the capacitor is an open circuit: no current flows through $R$, no voltage drops across it, and $\mathbf{V}_{\text{out}} \to \mathbf{V}_{\text{in}}$ ($|H| \to 1$). At very high frequencies ($\omega \to \infty$), $X_C \to 0$ and the capacitor is a short circuit to ground, clamping $\mathbf{V}_{\text{out}} \to 0$ ($|H| \to 0$).

The response at any angular frequency $\omega$ follows from treating the series $RC$ network as a complex voltage divider ([[FEEG1004 D2 - Impedance and Phasor Circuit Analysis#Parallel impedances and complex dividers]]) with $Z_R = R$ and $Z_C = \dfrac{1}{j\omega C}$:

$$
\begin{aligned}
\mathbf{V}_{\text{out}} &= \frac{Z_C}{Z_R + Z_C}\,\mathbf{V}_{\text{in}} \\
H(j\omega) = \frac{\mathbf{V}_{\text{out}}}{\mathbf{V}_{\text{in}}} &= \frac{\dfrac{1}{j\omega C}}{R + \dfrac{1}{j\omega C}}
\end{aligned}
$$

Multiplying numerator and denominator by $j\omega C$ clears the inner fraction in one step:

$$
\begin{aligned}
H(j\omega) &= \frac{\left(\dfrac{1}{j\omega C}\right)(j\omega C)}{\left(R + \dfrac{1}{j\omega C}\right)(j\omega C)} \\
&= \frac{1}{1 + j\omega RC}
\end{aligned}
$$

The modulus of a quotient of complex numbers is the quotient of their moduli, $|z_1/z_2| = |z_1|/|z_2|$, and the argument of a quotient is the difference of their arguments, $\angle(z_1/z_2) = \angle z_1 - \angle z_2$. Here the numerator is the positive real number $1 = 1\angle 0^\circ$, and the denominator $1 + j\omega RC$ has real part $1$ and positive imaginary part $\omega RC$:

$$
\begin{aligned}
|1 + j\omega RC| &= \sqrt{1^2 + (\omega RC)^2} = \sqrt{1 + (\omega RC)^2} \\
\angle(1 + j\omega RC) &= \arctan\!\left(\frac{\omega RC}{1}\right) = \arctan(\omega RC)
\end{aligned}
$$

Dividing numerator by denominator gives the magnitude and phase responses of the first-order $RC$ low-pass filter:

$$
\begin{aligned}
|H(\omega)| &= \frac{|1|}{|1 + j\omega RC|} = \frac{1}{\sqrt{1 + (\omega RC)^2}} \\
\phi(\omega) = \angle H(j\omega) &= \angle 1 - \angle(1 + j\omega RC) = 0 - \arctan(\omega RC) = -\arctan(\omega RC)
\end{aligned}
$$

Rationalising instead, by multiplying numerator and denominator by the conjugate $1 - j\omega RC$, separates the real and imaginary parts:

$$
\begin{aligned}
H(j\omega) &= \frac{1 - j\omega RC}{(1 + j\omega RC)(1 - j\omega RC)} \\
&= \frac{1}{1 + (\omega RC)^2} - j\,\frac{\omega RC}{1 + (\omega RC)^2}
\end{aligned}
$$

The two frequency extremes agree with the physical picture. As $\omega \to 0$, $\omega RC \to 0$, so $|H(0)| = \dfrac{1}{\sqrt{1 + 0}} = 1$ and $\phi(0) = -\arctan(0) = 0^\circ$. As $\omega \to \infty$, $\omega RC \gg 1$, so $|H(\omega)| \approx \dfrac{1}{\omega RC} \to 0$, decaying inversely with frequency, and $\phi(\omega) \to -\arctan(\infty) = -90^\circ$ ($-\pi/2\ \text{rad}$). At high frequencies the current is limited by the resistor, $\mathbf{I} \approx \mathbf{V}_{\text{in}}/R$ in phase with $\mathbf{V}_{\text{in}}$, so the capacitor voltage $\mathbf{V}_{\text{out}} = \mathbf{I}/(j\omega C)$ lags the input by nearly $90^\circ$.

### Cut-off frequency and the half-power point

Since $|H(\omega)| = 1/\sqrt{1 + (\omega RC)^2}$ falls smoothly and monotonically from $1$ to $0$, there is no abrupt wall between the pass band and the stop band. By convention the boundary is the **cut-off frequency** $\omega_c$, also called the corner frequency, break frequency, half-power frequency or $-3\ \text{dB}$ bandwidth, at which the real and imaginary parts of the denominator $1 + j\omega RC$ have equal magnitude ($R = X_C$):

$$
\begin{aligned}
\omega_c RC &= 1 \\
\omega_c &= \frac{1}{RC} = \frac{1}{\tau} \quad [\text{rad s}^{-1}]
\end{aligned}
$$

where $\tau = RC$ is the time constant in seconds. With $\omega_c = 2\pi f_c$, the cut-off in hertz is

$$
f_c = \frac{\omega_c}{2\pi} = \frac{1}{2\pi RC} \quad [\text{Hz}]
$$

Substituting $\omega = \omega_c$ ($\omega_c RC = 1$) into the magnitude and phase gives the behaviour at the corner:

$$
\begin{aligned}
|H(\omega_c)| &= \frac{1}{\sqrt{1 + 1^2}} = \frac{1}{\sqrt{2}} \approx 0.7071 \\
\phi(\omega_c) &= -\arctan(1) = -45^\circ = -\frac{\pi}{4}\ \text{rad}
\end{aligned}
$$

The name **half-power point** comes from the average power $P = V_{\text{rms}}^2 / r$ that the output would deliver to a fixed test resistance $r$. At $\omega = 0$, $V_{\text{out}} = V_{\text{in}}$ and the power is the pass-band maximum $P_{\text{max}} = V_{\text{in}}^2 / r$. At $\omega = \omega_c$,

$$
\begin{aligned}
\frac{P(\omega_c)}{P_{\text{max}}} &= \frac{V_{\text{out}}(\omega_c)^2 / r}{V_{\text{in}}^2 / r} \\
&= \left(\frac{V_{\text{out}}(\omega_c)}{V_{\text{in}}}\right)^2 \\
&= |H(\omega_c)|^2 \\
&= \left(\frac{1}{\sqrt{2}}\right)^2 = \frac{1}{2}
\end{aligned}
$$

At $\omega_c = 1/(RC)$ the RMS output voltage has fallen to $1/\sqrt{2} \approx 70.7\%$ of the input, and because power goes as voltage squared, the output power has fallen to half ($50\%$) of its pass-band value.

### RC high-pass filter

Swapping the two components, with the capacitor $C$ in series with $\mathbf{V}_{\text{in}}$ and the unloaded output taken across the shunt resistor $R$, reverses the frequency selectivity. As $\omega \to 0$ the series capacitor is an open circuit ($X_C \to \infty$) and blocks DC current, so $\mathbf{V}_{\text{out}} = \mathbf{I}R \to 0$ ($|H| \to 0$). As $\omega \to \infty$ it is a short circuit ($X_C \to 0$) and passes the full input to the resistor, so $\mathbf{V}_{\text{out}} \to \mathbf{V}_{\text{in}}$ ($|H| \to 1$).

The complex voltage divider with $Z_R = R$ in the numerator gives the transfer function of the unloaded first-order $RC$ high-pass filter:

$$
\begin{aligned}
H(j\omega) = \frac{\mathbf{V}_{\text{out}}}{\mathbf{V}_{\text{in}}} &= \frac{Z_R}{Z_R + Z_C} \\
&= \frac{R}{R + \dfrac{1}{j\omega C}}
\end{aligned}
$$

It has two standard forms. Dividing top and bottom by $R$ puts all the frequency dependence in the denominator:

$$
\begin{aligned}
H(j\omega) &= \frac{\dfrac{R}{R}}{\dfrac{R}{R} + \dfrac{1}{j\omega RC}} \\
&= \frac{1}{1 + \dfrac{1}{j\omega RC}} \\
&= \frac{1}{1 - j\,\dfrac{1}{\omega RC}}
\end{aligned}
$$

Multiplying top and bottom of the original fraction by $j\omega C$ instead clears all the sub-fractions:

$$
H(j\omega) = \frac{j\omega RC}{1 + j\omega RC}
$$

The modulus and argument of either form give the magnitude and phase responses of the first-order $RC$ high-pass filter:

$$
\begin{aligned}
|H(\omega)| &= \frac{1}{\sqrt{1 + \left(\dfrac{1}{\omega RC}\right)^2}} = \frac{\omega RC}{\sqrt{1 + (\omega RC)^2}} \\
\phi(\omega) = \angle H(j\omega) &= 0 - \arctan\!\left(-\frac{1}{\omega RC}\right) = +\arctan\!\left(\frac{1}{\omega RC}\right) = 90^\circ - \arctan(\omega RC)
\end{aligned}
$$

Setting $|H(\omega_c)| = 1/\sqrt{2}$ requires $\dfrac{1}{\omega_c RC} = 1$, which gives the same cut-off frequency as the low-pass circuit:

$$
\omega_c = \frac{1}{RC}, \qquad f_c = \frac{1}{2\pi RC}
$$

At $\omega = \omega_c$, $|H(\omega_c)| = 1/\sqrt{2} \approx 0.7071$ and $\phi(\omega_c) = +\arctan(1) = +45^\circ$: the output leads the input by $45^\circ$, approaching $+90^\circ$ as $\omega \to 0$ and $0^\circ$ as $\omega \to \infty$.

> [!tip] Low-pass and high-pass outputs of the same RC pair
> In any series $RC$ circuit driven by $\mathbf{V}_{\text{in}}$, KVL gives $\mathbf{V}_C + \mathbf{V}_R = \mathbf{V}_{\text{in}}$ at every frequency. Dividing by $\mathbf{V}_{\text{in}}$, the low-pass transfer function (output across $C$) and the high-pass transfer function (output across $R$) sum to one at all frequencies:
> $$H_{\text{LP}}(j\omega) + H_{\text{HP}}(j\omega) = \frac{1}{1 + j\omega RC} + \frac{j\omega RC}{1 + j\omega RC} = 1$$
> Their magnitudes do not sum to 1 ($|H_{\text{LP}}| + |H_{\text{HP}}| \ne 1$), because $\mathbf{V}_C$ and $\mathbf{V}_R$ are $90^\circ$ apart ($\mathbf{V}_R = j\omega RC\,\mathbf{V}_C$). Their squared magnitudes satisfy Pythagoras' theorem instead: $|H_{\text{LP}}(\omega)|^2 + |H_{\text{HP}}(\omega)|^2 = \dfrac{1 + (\omega RC)^2}{1 + (\omega RC)^2} = 1$. At $\omega = \omega_c$ each carries $(1/\sqrt{2})^2 = 1/2$ of the squared voltage.

## 3. Decibels and Bode plots

### Gain in decibels

Filter gains and attenuations routinely span many orders of magnitude (for example $|H|$ from $1$ down to $10^{-4}$) across frequencies from $1\ \text{Hz}$ to $10^6\ \text{Hz}$. On linear axes the whole pass band below $\omega_c$ is squashed against the vertical axis, and attenuations below $0.05$ are indistinguishable from zero. Frequency response is therefore plotted on logarithmic axes using **decibels** ($\text{dB}$).

The bel, from telecommunications, measures the logarithmic ratio of output power $P_{\text{out}}$ to input power $P_{\text{in}}$ as $\log_{10}(P_{\text{out}}/P_{\text{in}})$; one **decibel** is a tenth of a bel:

$$
G_{\text{dB}} = 10\log_{10}\!\left(\frac{P_{\text{out}}}{P_{\text{in}}}\right) \quad [\text{dB}]
$$

When the input and output voltages are referenced across equal resistances $r$, so that $P_{\text{out}} = V_{\text{out}}^2 / r$ and $P_{\text{in}} = V_{\text{in}}^2 / r$, the power ratio is the square of the voltage gain $|H(\omega)| = V_{\text{out}} / V_{\text{in}}$. The power rule $\log_{10}(x^2) = 2\log_{10}(x)$ turns the factor of $10$ for power into $20$ for voltage:

$$
\begin{aligned}
G_{\text{dB}} &= 10\log_{10}\!\left(\frac{V_{\text{out}}^2 / r}{V_{\text{in}}^2 / r}\right) \\
&= 10\log_{10}\!\left[\left(\frac{V_{\text{out}}}{V_{\text{in}}}\right)^2\right] \\
&= 20\log_{10}\!\left(\frac{V_{\text{out}}}{V_{\text{in}}}\right) = 20\log_{10}|H(\omega)|
\end{aligned}
$$

Dividing by $20$ and raising $10$ to that power recovers the linear gain from a decibel value $G_{\text{dB}}$:

$$
|H(\omega)| = \frac{V_{\text{out}}}{V_{\text{in}}} = 10^{G_{\text{dB}} / 20}, \qquad \frac{P_{\text{out}}}{P_{\text{in}}} = 10^{G_{\text{dB}} / 10}
$$

| Linear voltage gain $\|H\| = V_{\text{out}}/V_{\text{in}}$ | Power ratio $P_{\text{out}}/P_{\text{in}} = \|H\|^2$ | Gain in decibels $G_{\text{dB}} = 20\log_{10}\|H\|$ | Physical meaning |
| :--- | :--- | :--- | :--- |
| $100$ | $10\,000$ | $+40\ \text{dB}$ | $100\times$ voltage amplification |
| $10$ | $100$ | $+20\ \text{dB}$ | $10\times$ voltage amplification |
| $\sqrt{2} \approx 1.414$ | $2$ | $+3.01\ \text{dB} \approx +3\ \text{dB}$ | Doubling of power |
| $1$ | $1$ | $0\ \text{dB}$ | Unity gain ($V_{\text{out}} = V_{\text{in}}$, unattenuated pass band) |
| $1/\sqrt{2} \approx 0.7071$ | $0.5$ | $-3.01\ \text{dB} \approx -3\ \text{dB}$ | Half-power cut-off point ($\omega = \omega_c$) |
| $0.1 = 10^{-1}$ | $0.01$ | $-20\ \text{dB}$ | $10\times$ voltage attenuation ($90\%$ reduction in amplitude) |
| $0.01 = 10^{-2}$ | $0.0001$ | $-40\ \text{dB}$ | $100\times$ voltage attenuation ($99\%$ reduction in amplitude) |

### Straight-line Bode asymptotes and roll-off

A **Bode plot** is a pair of graphs sharing a logarithmic frequency axis ($\log_{10}\omega$ or $\log_{10}f$), on which each factor-of-$10$ step in frequency, one **decade**, occupies the same horizontal distance. The Bode magnitude plot shows $G_{\text{dB}}(\omega) = 20\log_{10}|H(\omega)|$ in $\text{dB}$, and the Bode phase plot shows $\phi(\omega) = \angle H(j\omega)$ in degrees (or radians) on a linear vertical axis.

Substituting the $RC$ low-pass magnitude $|H(\omega)| = \big(1 + (\omega/\omega_c)^2\big)^{-1/2}$, with $\omega RC = \omega/\omega_c$, into the decibel definition gives

$$
\begin{aligned}
G_{\text{dB}}(\omega) &= 20\log_{10}\!\left[\left(1 + \left(\frac{\omega}{\omega_c}\right)^2\right)^{-1/2}\right] \\
&= -10\log_{10}\!\left(1 + \left(\frac{\omega}{\omega_c}\right)^2\right)
\end{aligned}
$$

The magnitude curve approaches two straight lines that meet at the corner $\omega = \omega_c$. In the pass band ($\omega \ll \omega_c$), $(\omega/\omega_c)^2 \ll 1$, so $G_{\text{dB}}(\omega) \approx -10\log_{10}(1) = 0\ \text{dB}$, a horizontal line at $0\ \text{dB}$. In the stop band ($\omega \gg \omega_c$), the $1$ inside the logarithm is negligible beside $(\omega/\omega_c)^2$:

$$
\begin{aligned}
G_{\text{dB}}(\omega) &\approx -10\log_{10}\!\left[\left(\frac{\omega}{\omega_c}\right)^2\right] \\
&= -20\log_{10}\!\left(\frac{\omega}{\omega_c}\right) \\
&= -20\log_{10}\omega + 20\log_{10}\omega_c
\end{aligned}
$$

Against $x = \log_{10}(\omega/\omega_c)$, $G_{\text{dB}} \approx -20x$ is a straight line through $0\ \text{dB}$ at $\omega = \omega_c$ with slope $-20\ \text{dB/decade}$. One decade (from $\omega_c$ to $10\omega_c$, or from $10\omega_c$ to $100\omega_c$) adds $1$ to $\log_{10}(\omega/\omega_c)$ and so lowers the gain by $20\ \text{dB}$, a factor of $10$ in voltage amplitude. One **octave**, a factor of $2$ in $\omega$, changes the gain by $-20\log_{10}(2) = -6.02\ \text{dB/octave}$.

The first-order $RC$ high-pass filter mirrors this: $G_{\text{dB}}(\omega) \approx 0\ \text{dB}$ for $\omega \gg \omega_c$, and $G_{\text{dB}}(\omega) \approx +20\log_{10}(\omega/\omega_c)$ for $\omega \ll \omega_c$, rising at $+20\ \text{dB/decade}$ up to the corner. At $\omega = \omega_c$ the two asymptotes meet at $0\ \text{dB}$, while the true curve passes through $-10\log_{10}(1 + 1^2) = -10\log_{10}(2) = -3.01\ \text{dB}$. The largest error of the piecewise-linear approximation is therefore $3.01\ \text{dB}$, at $\omega = \omega_c$.

![[ee_d3_bode_rc_filters.png|900]]

## 4. RL, loaded and active filters

### RL high-pass and low-pass filters

First-order filters can also be built from a resistor $R$ and an inductor $L$ with impedance $Z_L = j\omega L$. An inductor's reactance $X_L = \omega L$ grows linearly with frequency, whereas a capacitor's $X_C = 1/(\omega C)$ falls inversely, so the inductor plays the opposite role: in the shunt branch it gives a high-pass filter, and in the series branch a low-pass filter.

With series $R$ and the unloaded output across a shunt $L$, the complex voltage divider gives the $RL$ high-pass filter:

$$
\begin{aligned}
H_{\text{RL,HP}}(j\omega) = \frac{\mathbf{V}_{\text{out}}}{\mathbf{V}_{\text{in}}} &= \frac{Z_L}{Z_R + Z_L} \\
&= \frac{j\omega L}{R + j\omega L} \\
&= \frac{1}{1 + \dfrac{R}{j\omega L}} = \frac{1}{1 - j\,\dfrac{R}{\omega L}}
\end{aligned}
$$

Its magnitude and phase are

$$
\begin{aligned}
|H_{\text{RL,HP}}(\omega)| &= \frac{1}{\sqrt{1 + \left(\dfrac{R}{\omega L}\right)^2}} = \frac{\omega L}{\sqrt{R^2 + (\omega L)^2}} \\
\phi_{\text{RL,HP}}(\omega) &= +\arctan\!\left(\frac{R}{\omega L}\right) = 90^\circ - \arctan\!\left(\frac{\omega L}{R}\right)
\end{aligned}
$$

As $\omega \to 0$ the inductor is a short circuit ($Z_L \to 0$) and shorts the output to ground ($|H| \to 0$). As $\omega \to \infty$ it is an open circuit ($|Z_L| \to \infty$) and $|H| \to 1$.

With series $L$ and the unloaded output across a shunt $R$, the $RL$ low-pass filter has

$$
\begin{aligned}
H_{\text{RL,LP}}(j\omega) = \frac{\mathbf{V}_{\text{out}}}{\mathbf{V}_{\text{in}}} &= \frac{Z_R}{Z_R + Z_L} \\
&= \frac{R}{R + j\omega L} \\
&= \frac{1}{1 + j\,\dfrac{\omega L}{R}}
\end{aligned}
$$

with magnitude and phase

$$
\begin{aligned}
|H_{\text{RL,LP}}(\omega)| &= \frac{1}{\sqrt{1 + \left(\dfrac{\omega L}{R}\right)^2}} = \frac{R}{\sqrt{R^2 + (\omega L)^2}} \\
\phi_{\text{RL,LP}}(\omega) &= -\arctan\!\left(\frac{\omega L}{R}\right)
\end{aligned}
$$

As $\omega \to 0$ the series inductor is a short circuit, so $|H| \to 1$; as $\omega \to \infty$ it blocks high-frequency current, so $|H| \to 0$.

In both $RL$ circuits the half-power cut-off is where the inductive reactance equals the resistance, $X_L(\omega_c) = \omega_c L = R$:

$$
\omega_c = \frac{R}{L} \quad [\text{rad s}^{-1}], \qquad f_c = \frac{R}{2\pi L} \quad [\text{Hz}]
$$

The $RC$ time constant is $\tau = RC$, whereas the $RL$ time constant is $\tau = L/R$, so the corner frequency is again $\omega_c = 1/\tau = R/L$.

![[ee_t8_q2_rl_filters.png|900]]

### Loaded filters and Thévenin reduction

The unloaded analysis above leaves the filter output terminals open-circuited. In a real circuit the filter drives a next stage whose input resistance acts as a **load resistor** $R_L$ connected in parallel across the output terminals. Consider an $RC$ low-pass filter (series resistor $R_1$, shunt capacitor $C$) loaded by $R_L$ in parallel with $C$.

> [!warning] Cut-off when the pass-band gain is not 1
> An unloaded passive filter has maximum pass-band gain $H_{\text{max}} = 1$, so its half-power condition reads $|H(\omega_c)| = 1/\sqrt{2}$. A loaded filter, or one containing an amplifier, has $H_{\text{max}} = \max_\omega |H(\omega)| \ne 1$, and setting $|H(\omega_c)| = 1/\sqrt{2}$ then gives the wrong frequency. The general half-power definition is
> $$|H(\omega_c)| = \frac{H_{\text{max}}}{\sqrt{2}}$$
> At $\omega = \omega_c$ the decibel gain is $20\log_{10}|H(\omega_c)| = 20\log_{10}H_{\text{max}} - 3.01\ \text{dB}$, that is, $3\ \text{dB}$ below the pass-band plateau, not $-3\ \text{dB}$ absolute.

The loaded transfer function $H(j\omega)$ can be derived in two ways. The first uses a Thévenin equivalent at the capacitor terminals. With the capacitor $C$ disconnected from the output node $X$, the source $\mathbf{V}_{\text{in}}$ and the resistors $R_1$ and $R_L$ seen from $X$ form a purely resistive voltage divider ([[FEEG1004 A7 - Thevenin, Superposition and Relays]]). Its open-circuit voltage $\mathbf{V}_{\text{TH}}$ and its Thévenin resistance $R_{\text{TH}}$, found by replacing the independent source $\mathbf{V}_{\text{in}}$ with a short circuit, are

$$
\begin{aligned}
\mathbf{V}_{\text{TH}} &= \frac{R_L}{R_1 + R_L}\,\mathbf{V}_{\text{in}} = K\,\mathbf{V}_{\text{in}}, \qquad K = \frac{R_L}{R_1 + R_L} \\
R_{\text{TH}} &= R_1 \parallel R_L = \frac{R_1 R_L}{R_1 + R_L}
\end{aligned}
$$

Reconnecting $C$ across this equivalent reduces the loaded network to a standard unloaded $RC$ low-pass filter driven by $K\mathbf{V}_{\text{in}}$ through the series resistance $R_{\text{TH}}$:

$$
\begin{aligned}
\mathbf{V}_{\text{out}} &= \frac{Z_C}{R_{\text{TH}} + Z_C}\,\mathbf{V}_{\text{TH}} \\
H(j\omega) = \frac{\mathbf{V}_{\text{out}}}{\mathbf{V}_{\text{in}}} &= \frac{K}{1 + j\omega R_{\text{TH}}C}
\end{aligned}
$$

The second way combines $R_L$ and $Z_C = 1/(j\omega C)$ in parallel first:

$$
\begin{aligned}
Z_p = R_L \parallel Z_C &= \frac{R_L \cdot \dfrac{1}{j\omega C}}{R_L + \dfrac{1}{j\omega C}} = \frac{R_L}{1 + j\omega R_L C} \\
H(j\omega) = \frac{Z_p}{R_1 + Z_p} &= \frac{\dfrac{R_L}{1 + j\omega R_L C}}{R_1 + \dfrac{R_L}{1 + j\omega R_L C}} \\
&= \frac{R_L}{R_1(1 + j\omega R_L C) + R_L} \\
&= \frac{R_L}{(R_1 + R_L) + j\omega R_1 R_L C}
\end{aligned}
$$

Dividing numerator and denominator by $(R_1 + R_L)$ gives the same first-order form:

$$
H(j\omega) = \frac{\dfrac{R_L}{R_1 + R_L}}{1 + j\omega\left(\dfrac{R_1 R_L}{R_1 + R_L}\right)C} = \frac{K}{1 + j\omega R_{\text{TH}}C}
$$

The magnitude and phase responses of the loaded low-pass filter are therefore

$$
|H(\omega)| = \frac{K}{\sqrt{1 + (\omega R_{\text{TH}}C)^2}}, \qquad \phi(\omega) = -\arctan(\omega R_{\text{TH}}C)
$$

At DC ($\omega = 0$) the maximum pass-band gain is $H_{\text{max}} = |H(0)| = K = \dfrac{R_L}{R_1 + R_L} < 1$. The general cut-off condition $|H(\omega_c)| = \dfrac{H_{\text{max}}}{\sqrt{2}} = \dfrac{K}{\sqrt{2}}$ requires $\omega_c R_{\text{TH}}C = 1$:

$$
\omega_c = \frac{1}{R_{\text{TH}}C} = \frac{R_1 + R_L}{R_1 R_L C} = \frac{1}{R_1 C}\left(1 + \frac{R_1}{R_L}\right)
$$

A finite load resistor therefore has two effects at once. It lowers the pass-band voltage gain from $1$ to $K = \dfrac{R_L}{R_1 + R_L}$, and because $R_{\text{TH}} = R_1 \parallel R_L < R_1$, it raises the corner frequency to $\omega_c = \dfrac{1}{R_{\text{TH}}C} > \dfrac{1}{R_1 C}$. Only when the load resistance is much larger than the filter resistance ($R_L \gg R_1$) do $K \to 1$ and $R_{\text{TH}} \to R_1$.

![[ee_t8_q1_loaded_lowpass.png|900]]

### Cascaded band-pass and active op-amp filters

A **band-pass filter** that passes frequencies between a lower cut-off $\omega_{c,\text{HP}}$ and an upper cut-off $\omega_{c,\text{LP}}$ ($\omega_{c,\text{HP}} < \omega_{c,\text{LP}}$) can be built by cascading a high-pass stage with a low-pass stage. If a passive $RC$ low-pass stage is wired directly across the output of a passive $RC$ high-pass stage, however, the second stage loads the first in the same way as $R_L$ loaded the filter in [[#Loaded filters and Thévenin reduction]].

An operational-amplifier **voltage follower** (unity-gain buffer, [[FEEG1004 B4 - Operational Amplifiers]]) between the two passive stages removes this loading. Its nearly infinite input impedance draws almost no current from the first stage ($R_L \to \infty$), and its nearly zero output impedance drives the second stage as an ideal voltage source. For buffered stages with transfer functions $H_1(j\omega)$ and $H_2(j\omega)$, the overall transfer function is their product, so the decibel gains add:

$$
H_{\text{total}}(j\omega) = H_1(j\omega)\,H_2(j\omega) \implies G_{\text{dB,total}}(\omega) = G_{\text{dB},1}(\omega) + G_{\text{dB},2}(\omega)
$$

An op-amp can also combine amplification and filtering in a single stage, an **active filter**. Replacing the feedback resistor $R_2$ of a standard inverting amplifier ([[FEEG1004 B4 - Operational Amplifiers]]) by $R_2$ in parallel with a feedback capacitor $C$ gives an **active inverting first-order low-pass filter**. For an ideal op-amp, with a virtual earth at the inverting input ($\mathbf{V}_- = \mathbf{V}_+ = 0\ \text{V}$) and zero input bias current, the feedback impedance $Z_f$ is the parallel combination of $R_2$ and $Z_C = 1/(j\omega C)$:

$$
\begin{aligned}
Z_f &= R_2 \parallel \frac{1}{j\omega C} \\
&= \frac{R_2 \cdot \dfrac{1}{j\omega C}}{R_2 + \dfrac{1}{j\omega C}} \\
&= \frac{R_2}{1 + j\omega R_2 C}
\end{aligned}
$$

Equating the input current $\mathbf{I}_1 = \mathbf{V}_{\text{in}}/R_1$ to the feedback current $-\mathbf{V}_{\text{out}}/Z_f$ gives the active low-pass transfer function:

$$
\begin{aligned}
H(j\omega) = \frac{\mathbf{V}_{\text{out}}}{\mathbf{V}_{\text{in}}} &= -\frac{Z_f}{R_1} \\
&= -\frac{R_2 / R_1}{1 + j\omega R_2 C}
\end{aligned}
$$

At low frequencies ($\omega \ll \omega_c$) the capacitor is open and the circuit is an inverting amplifier with pass-band gain $H_{\text{max}} = R_2 / R_1$, set by the resistor ratio. At high frequencies ($\omega \gg \omega_c$) the feedback capacitor shorts out $R_2$ and the gain rolls off at $-20\ \text{dB/decade}$, with corner frequency $\omega_c = \dfrac{1}{R_2 C}$ independent of the load connected to the op-amp output.

## Worked examples

### RC low-pass filter for 50 Hz hum

A sensor output is contaminated by $50\ \text{Hz}$ AC mains interference. Design an unloaded first-order $RC$ low-pass filter with $R = 1\ \text{k}\Omega$ that attenuates the $50\ \text{Hz}$ component by $20\ \text{dB}$: find the capacitance $C$, the corner frequency $f_c$ and the phase shift $\phi$ at $50\ \text{Hz}$.

An attenuation of $20\ \text{dB}$ means the gain at $f = 50\ \text{Hz}$ ($\omega = 2\pi f = 2\pi \times 50 = 100\pi \approx 314.16\ \text{rad s}^{-1}$) is $G_{\text{dB}} = -20\ \text{dB}$. As a linear voltage ratio,

$$
\begin{aligned}
20\log_{10}|H(\omega)| &= -20 \\
\log_{10}|H(\omega)| &= -1 \\
|H(\omega)| &= 10^{-1} = 0.1
\end{aligned}
$$

Substituting $|H(\omega)| = 0.1$ into the first-order $RC$ low-pass magnitude and solving for $\omega RC$:

$$
\begin{aligned}
\frac{1}{\sqrt{1 + (\omega RC)^2}} &= 0.1 \\
\sqrt{1 + (\omega RC)^2} &= 10 \\
1 + (\omega RC)^2 &= 100 \\
(\omega RC)^2 &= 99 \\
\omega RC &= \sqrt{99} \approx 9.9499
\end{aligned}
$$

With $R = 1\ \text{k}\Omega = 1000\ \Omega$ and $\omega = 2\pi(50\ \text{Hz}) = 314.159\ \text{rad s}^{-1}$,

$$
\begin{aligned}
C &= \frac{\sqrt{99}}{2\pi f R} \\
&= \frac{9.9499}{2\pi \times 50\ \text{Hz} \times 1000\ \Omega} \\
&= 3.1671 \times 10^{-5}\ \text{F} = 31.7\ \mu\text{F} \quad (3\text{ s.f.})
\end{aligned}
$$

With $R = 1000\ \Omega$ and $C = 31.671\ \mu\text{F}$, the cut-off frequency is

$$
\begin{aligned}
f_c &= \frac{1}{2\pi RC} \\
&= \frac{1}{2\pi \times 1000\ \Omega \times 3.1671 \times 10^{-5}\ \text{F}} \\
&= \frac{50\ \text{Hz}}{\sqrt{99}} = 5.025\ \text{Hz} \approx 5.03\ \text{Hz}
\end{aligned}
$$

and the phase shift of the $50\ \text{Hz}$ component is

$$
\phi(50\ \text{Hz}) = -\arctan(\omega RC) = -\arctan(\sqrt{99}) = -84.26^\circ
$$

![[ee_d3_filter_design_50hz.png|900]]

> [!check] Straight-line Bode estimate
> On the straight-line Bode plot a first-order low-pass filter rolls off at $-20\ \text{dB/decade}$ above $f_c$, so reaching $-20\ \text{dB}$ at $50\ \text{Hz}$ places $50\ \text{Hz}$ one decade ($10\times$) above the corner: $f_{c,\text{asymp}} = \dfrac{50\ \text{Hz}}{10} = 5.00\ \text{Hz}$, corresponding to $\omega RC = 10$ and $C_{\text{asymp}} = \dfrac{10}{2\pi(50)(1000)} = 31.83\ \mu\text{F}$. Since $\sqrt{99} = 9.950$ differs from $10$ by only $0.5\%$, the full calculation ($f_c = 5.03\ \text{Hz}$, $C = 31.7\ \mu\text{F}$) and the straight-line approximation agree to within $0.5\%$.

### RL high-pass filter with a 3 kHz corner

An unloaded passive filter has a series resistor $R$ between the source $\mathbf{V}_{\text{in}}$ and the output node, and a shunt inductor $L = 0.3\ \text{mH}$ from the output node to ground. Derive $H(j\omega) = \mathbf{V}_{\text{out}}/\mathbf{V}_{\text{in}}$ and identify the filter type, then find the resistance $R$ that sets the cut-off frequency to $f_c = 3\ \text{kHz}$.

The complex divider with $Z_R = R$ and $Z_L = j\omega L$, dividing numerator and denominator by $j\omega L$, gives

$$
\begin{aligned}
H(j\omega) = \frac{\mathbf{V}_{\text{out}}}{\mathbf{V}_{\text{in}}} &= \frac{Z_L}{Z_R + Z_L} \\
&= \frac{j\omega L}{R + j\omega L} \\
&= \frac{1}{1 + \dfrac{R}{j\omega L}} = \frac{1}{1 - j\,\dfrac{R}{\omega L}}
\end{aligned}
$$

with magnitude

$$
|H(\omega)| = \frac{1}{\sqrt{1 + \left(\dfrac{R}{\omega L}\right)^2}}
$$

As $\omega \to 0$, $\dfrac{R}{\omega L} \to \infty$ and $|H(\omega)| \to 0$, since the shunt inductor is a DC short circuit to ground. As $\omega \to \infty$, $\dfrac{R}{\omega L} \to 0$ and $|H(\omega)| \to 1$, since the inductor is a high-frequency open circuit. Low frequencies are rejected and high frequencies pass unattenuated, so the circuit is a first-order $RL$ high-pass filter.

At the half-power cut-off $\omega_c = 2\pi f_c$, $|H(\omega_c)| = 1/\sqrt{2}$ requires $\dfrac{R}{\omega_c L} = 1$:

$$
\begin{aligned}
R &= \omega_c L = 2\pi f_c L \\
&= 2\pi \times (3000\ \text{Hz}) \times (0.3 \times 10^{-3}\ \text{H}) \\
&= 1.8\pi\ \Omega = 5.655\ \Omega \approx 5.65\ \Omega \quad (3\text{ s.f.})
\end{aligned}
$$

> [!check] Reactance equals resistance at the corner
> At $f = f_c = 3000\ \text{Hz}$ the inductive reactance of $L = 0.3\ \text{mH}$ is $X_L = 2\pi(3000\ \text{Hz})(0.3 \times 10^{-3}\ \text{H}) = 5.655\ \Omega = R$. The total series impedance is $Z_T = R + jX_L = 5.655 + j5.655\ \Omega = 5.655\sqrt{2}\angle 45^\circ\ \Omega$, so $|H(f_c)| = \dfrac{|jX_L|}{|Z_T|} = \dfrac{5.655}{5.655\sqrt{2}} = \dfrac{1}{\sqrt{2}}$ and $\phi(f_c) = 90^\circ - 45^\circ = +45^\circ$.

### RC low-pass output at 100 Hz and 10 kHz

An unloaded $RC$ low-pass filter has a series resistor $R = 4.7\ \text{k}\Omega$ ($4700\ \Omega$) and a shunt capacitor $C = 47\ \text{nF}$, and is driven by an input of RMS magnitude $V_{\text{in}} = 10\ \text{V}$. Find the cut-off frequency $f_c$ and the RMS output $V_{\text{out}}$ across the capacitor at (a) $f = 100\ \text{Hz}$ and (b) $f = 10\ \text{kHz}$, then compare with the outputs for $R = 47\ \text{k}\Omega$.

The cut-off frequency is

$$
\begin{aligned}
f_c &= \frac{1}{2\pi RC} \\
&= \frac{1}{2\pi \times 4700\ \Omega \times 47 \times 10^{-9}\ \text{F}} \\
&= \frac{1}{1.38796 \times 10^{-3}\ \text{s}} = 720.5\ \text{Hz}
\end{aligned}
$$

so $100\ \text{Hz}$ lies well inside the pass band ($f \ll f_c$), while $10\ \text{kHz}$ lies more than a decade above the cut-off, in the stop band ($f \gg f_c$).

(a) At $f = 100\ \text{Hz}$ the capacitive reactance and impedance are

$$
\begin{aligned}
X_C &= \frac{1}{2\pi f C} = \frac{1}{2\pi \times 100\ \text{Hz} \times 47 \times 10^{-9}\ \text{F}} = 33\,862.8\ \Omega \\
Z_C &= -j33\,862.8\ \Omega
\end{aligned}
$$

The total series impedance and its magnitude are

$$
\begin{aligned}
Z_T &= R + Z_C = 4700 - j33\,862.8\ \Omega \\
|Z_T| &= \sqrt{4700^2 + (-33\,862.8)^2} = \sqrt{2.209 \times 10^7 + 1.1467 \times 10^9} = 34\,187.4\ \Omega
\end{aligned}
$$

and the RMS current $I$ and output voltage $V_{\text{out}} = I X_C$ are

$$
\begin{aligned}
I &= \frac{V_{\text{in}}}{|Z_T|} = \frac{10\ \text{V}}{34\,187.4\ \Omega} = 0.2925 \times 10^{-3}\ \text{A} = 0.2925\ \text{mA} \\
V_{\text{out}}(100\ \text{Hz}) &= I X_C = (0.2925 \times 10^{-3}\ \text{A})(33\,862.8\ \Omega) = 9.905\ \text{V} \approx 9.91\ \text{V}
\end{aligned}
$$

(b) At $f = 10\ \text{kHz} = 10\,000\ \text{Hz}$, the factor of $100$ in frequency reduces $X_C$ by a factor of $100$:

$$
\begin{aligned}
X_C &= \frac{1}{2\pi \times 10\,000\ \text{Hz} \times 47 \times 10^{-9}\ \text{F}} = 338.63\ \Omega \\
Z_T &= 4700 - j338.63\ \Omega \\
|Z_T| &= \sqrt{4700^2 + (-338.63)^2} = 4712.18\ \Omega
\end{aligned}
$$

so the RMS current and output voltage are

$$
\begin{aligned}
I &= \frac{10\ \text{V}}{4712.18\ \Omega} = 2.1222\ \text{mA} \\
V_{\text{out}}(10\ \text{kHz}) &= (2.1222 \times 10^{-3}\ \text{A})(338.63\ \Omega) = 0.7186\ \text{V} \approx 0.72\ \text{V}
\end{aligned}
$$

With $R = 47\ \text{k}\Omega$ ($47\,000\ \Omega$) the cut-off frequency drops by a factor of $10$ to $f_c = 72.05\ \text{Hz}$, so $100\ \text{Hz}$ is already above cut-off. Then $|Z_T(100\ \text{Hz})| = \sqrt{47\,000^2 + 33\,862.8^2} = 57\,928.3\ \Omega$ and $V_{\text{out}}(100\ \text{Hz}) = 10 \times \dfrac{33\,862.8}{57\,928.3} = 5.85\ \text{V}$, while at $10\ \text{kHz}$, $|Z_T(10\ \text{kHz})| = \sqrt{47\,000^2 + 338.63^2} = 47\,001.2\ \Omega$ and $V_{\text{out}}(10\ \text{kHz}) = 10 \times \dfrac{338.63}{47\,001.2} = 0.0720\ \text{V}$.

> [!check] Quadrature check, $V_R^2 + V_{\text{out}}^2 = V_{\text{in}}^2$
> In a series $RC$ circuit, $\mathbf{V}_R = R\mathbf{I}$ and $\mathbf{V}_C = -jX_C\mathbf{I}$ are $90^\circ$ apart, so their RMS magnitudes must satisfy $V_R^2 + V_{\text{out}}^2 = V_{\text{in}}^2 = 100\ \text{V}^2$. At $100\ \text{Hz}$ ($R = 4.7\ \text{k}\Omega$), $V_R = I R = (0.2925\ \text{mA})(4700\ \Omega) = 1.3748\ \text{V}$ and $V_R^2 + V_{\text{out}}^2 = 1.3748^2 + 9.9050^2 = 1.890 + 98.110 = 100.00\ \text{V}^2$. At $10\ \text{kHz}$, $V_R = (2.1222\ \text{mA})(4700\ \Omega) = 9.9741\ \text{V}$ and $V_R^2 + V_{\text{out}}^2 = 9.9741^2 + 0.7186^2 = 99.484 + 0.516 = 100.00\ \text{V}^2$.

### Loaded RC low-pass filter

A low-pass filter with series resistor $R_1 = 1\ \text{k}\Omega$ and shunt capacitor $C = 10\ \mu\text{F}$ feeds a resistive load $R_L = 10\ \text{k}\Omega$ connected in parallel across $C$ (Tutorial Sheet 8 Q1). Derive the numerical transfer function $H(j\omega)$, the magnitude response $|H(\omega)|$ and the phase response $\phi(\omega)$, then find the loaded cut-off $\omega_c$ (and $f_c$) and the gain $|H(\omega_c)|$ at the corner.

Removing $C$ from the output node $X$ leaves the resistive divider of $R_1 = 1000\ \Omega$ and $R_L = 10\,000\ \Omega$. The DC pass-band gain $K$ and the Thévenin resistance $R_{\text{TH}} = R_1 \parallel R_L$ are

$$
\begin{aligned}
K &= \frac{R_L}{R_1 + R_L} = \frac{10\,000\ \Omega}{1000\ \Omega + 10\,000\ \Omega} = \frac{10}{11} \approx 0.9091 \\
R_{\text{TH}} &= \frac{R_1 R_L}{R_1 + R_L} = \frac{(1000\ \Omega)(10\,000\ \Omega)}{11\,000\ \Omega} = \frac{10\,000}{11}\ \Omega \approx 909.09\ \Omega
\end{aligned}
$$

With $C = 10\ \mu\text{F} = 10^{-5}\ \text{F}$, the loaded time constant is

$$
\tau_{\text{TH}} = R_{\text{TH}}C = \left(\frac{10\,000}{11}\ \Omega\right)(10^{-5}\ \text{F}) = \frac{1}{110}\ \text{s} \approx 9.091 \times 10^{-3}\ \text{s}
$$

Substituting $K$ and $\tau_{\text{TH}}$ into the loaded transfer function from [[#Loaded filters and Thévenin reduction]] gives

$$
\begin{aligned}
H(j\omega) &= \frac{K}{1 + j\omega R_{\text{TH}}C} = \frac{0.9091}{1 + j(9.091 \times 10^{-3}\,\omega)} \\
|H(\omega)| &= \frac{0.9091}{\sqrt{1 + (9.091 \times 10^{-3}\,\omega)^2}} \\
\phi(\omega) &= -\arctan(9.091 \times 10^{-3}\,\omega)
\end{aligned}
$$

The maximum pass-band gain is at $\omega = 0$ and equals $H_{\text{max}} = K = 10/11 = 0.9091$ ($G_{\text{dB}}(0) = 20\log_{10}(10/11) = -0.828\ \text{dB}$). Setting $|H(\omega_c)| = H_{\text{max}}/\sqrt{2} = K/\sqrt{2}$ gives $\omega_c R_{\text{TH}}C = 1$:

$$
\begin{aligned}
\omega_c &= \frac{1}{R_{\text{TH}}C} = 110.0\ \text{rad s}^{-1} \\
f_c &= \frac{\omega_c}{2\pi} = \frac{110.0\ \text{rad s}^{-1}}{2\pi} = 17.51\ \text{Hz} \\
|H(\omega_c)| &= \frac{K}{\sqrt{2}} = \frac{10 / 11}{\sqrt{2}} = 0.6428 \quad (-3.838\ \text{dB})
\end{aligned}
$$

The unloaded filter has $\omega_{c,\text{unloaded}} = \dfrac{1}{R_1 C} = \dfrac{1}{1000 \times 10^{-5}} = 100\ \text{rad s}^{-1}$ and $H_{\text{max}} = 1$, so the $10\ \text{k}\Omega$ load reduces the pass-band gain by $9.1\%$ and raises the corner frequency by $10\%$.

> [!check] Direct evaluation at the loaded corner
> Without Thévenin's theorem, evaluate $Z_p = R_L \parallel Z_C$ directly at $\omega = \omega_c = 110\ \text{rad s}^{-1}$. There $Z_C = \dfrac{1}{j(110)(10^{-5})} = -j\frac{10\,000}{11}\ \Omega = -j909.09\ \Omega$, so $Z_p = \dfrac{R_L Z_C}{R_L + Z_C} = \dfrac{10\,000(-j909.09)}{10\,000 - j909.09} = 81.967 - j901.639\ \Omega$ and
> $$H(j110) = \frac{Z_p}{R_1 + Z_p} = \frac{81.967 - j901.639}{1081.967 - j901.639} = 0.45455 - j0.45455 = 0.6428\angle(-45^\circ)$$
> Both the magnitude $0.6428 = K/\sqrt{2}$ and the phase $-45^\circ$ agree with the Thévenin result.

## Links

- Parent: [[FEEG1004 Electronics Hub]]
- Previous: [[FEEG1004 D2 - Impedance and Phasor Circuit Analysis]]
- Next: [[FEEG1004 D4 - AC Power and Power Factor]]
- Concepts: [[RC Low-Pass and High-Pass Filters]] · [[Decibels]] · [[Bode Plot]] · [[Transfer Function]]
- Tutorial solutions: [[FEEG1004 Tutorial 8 - Filters, Transfer Functions and Power Factor Solutions]] (Q1, Q2)
- The first-order low-pass response $1/(1 + j\omega\tau)$ is the standard first-order lag $G(s) = 1/(1 + s\tau)$ evaluated at $s = j\omega$, which is how it appears in [[SESA2027 A5 - Frequency Response and Bode Plots]] (see also [[Bode Plot]] and [[Transfer Function]]).
- Before an analogue sensor signal is digitised by an ADC, an analogue low-pass anti-aliasing filter must attenuate components above the Nyquist frequency $f_s/2$ ([[Nyquist Sampling and Aliasing]], [[SESA2027 C3 - Signal Conditioning, Digitisation and Digital Filtering]]). First-order thermal and mechanical sensors obey the same frequency response ([[SESA2027 C2 - Sensor Characteristics, Dynamics and Design]], [[Sensor Dynamic Models]]).
- Complementary filtering in flight control blends a low-pass-filtered accelerometer or magnetometer with a high-pass-filtered gyroscope, using the identity $H_{\text{LP}}(j\omega) + H_{\text{HP}}(j\omega) = 1$ from [[#RC high-pass filter]] ([[Complementary Filter]]).
- Decibel addition of cascaded gains and losses underpins spacecraft radio link budgets ([[Decibels]], [[Link Budget Equation]]).

## Sources

- `02 - Sources/S2 AC Analysis/S2-W24 AC Analysis 03 - Filters and Loads - Lecture Slides.pdf`: complex potential divider, unloaded $RC$ low-pass and high-pass derivations, cut-off frequency $f_c = 1/(2\pi RC)$ (slide 4), decibels, Bode magnitude and phase plots, $50\ \text{Hz}$ hum filter design (slides 8–9), $RL$ high-pass example (slide 10), active inverting low-pass filter, $47\ \text{nF}$ numerical example (slides 17–18).
- `02 - Sources/S2 AC Analysis/S2 AC Analysis Lecture Notes 2021 - Niu.pdf` (Section 3: Filters, pp. 16–20): formal derivations of low-pass and high-pass amplitude and phase responses, half-power point $P_{\text{out}} = \frac{1}{2}P_{\text{in}}$, decibel scale and Bode asymptotes.
- `02 - Sources/Lectures/FEEG1004 Lecture 2025-03-11.txt` (ll. 1–360): physical motivation for filters, DC generator ripple removal, step-by-step derivation of $H(\omega) = 1/(1 + j\omega RC)$, modulus and phase rules for complex quotients, and half-power cut-off derivation.
- `02 - Sources/Lectures/FEEG1004 Lecture 2025-03-14.txt` (ll. 1–636): high-pass $RC$ derivation, decibels and log-frequency Bode plots, $-20\ \text{dB}$ at $50\ \text{Hz}$ design problem, $RL$ high-pass filter, loaded filters ($H_{\text{max}}/\sqrt{2}$), band-pass cascades, and active op-amp filters.
- `02 - Sources/Lectures/FEEG1004 Lecture 2025-03-18.txt` (ll. 18–102): recap of loaded and active filters, plus the $4.7\ \text{k}\Omega$ / $47\ \text{nF}$ low-pass calculation at $100\ \text{Hz}$ and $10\ \text{kHz}$.
- `02 - Sources/Tutorial Sheets/Tutorial Sheet 08 - AC Circuits 2 - Filters & Transfer Functions.pdf` (Q1, Q2).

## Self-study tasks

### Core

- [ ] For $R_1 = 1\ \text{k}\Omega$, $C = 10\ \mu\text{F}$ and load $R_L = 10\ \text{k}\Omega$, derive $H(\omega)$, plot $|H(\omega)|$ over $\omega \in [0.1,\ 10^6]\ \text{rad s}^{-1}$ in Python and find $\omega_c$ (Tutorial Sheet 8 Q1; Lecture 2025-03-14, ll. 565–592). → [[#Loaded RC low-pass filter]]; [[FEEG1004 Tutorial 8 - Filters, Transfer Functions and Power Factor Solutions#Q1: Loaded RC low-pass (R_1 = 1 kΩ, C = 10 µF, R_L = 10 kΩ)|Tutorial 8 Q1]]
- [ ] Derive $H(\omega)$, $|H(\omega)|$ and $\omega_c = R/L$ for the series-$R$/shunt-$L$ and series-$L$/shunt-$R$ networks (Tutorial Sheet 8 Q2; Lecture 2025-03-14, ll. 429–531). → [[#RL high-pass and low-pass filters]]; [[#RL high-pass filter with a 3 kHz corner]]; [[FEEG1004 Tutorial 8 - Filters, Transfer Functions and Power Factor Solutions#Q2: RL filters|Tutorial 8 Q2]]
- [ ] With $R = 1\ \text{k}\Omega$, find $C$ and $f_c$ for $-20\ \text{dB}$ attenuation at $50\ \text{Hz}$ (Lecture 2025-03-14, ll. 341–426; AC Analysis 03 slides 8–9). → [[#RC low-pass filter for 50 Hz hum]]
- [ ] Calculate $V_{\text{out}}$ for $V_{\text{in}} = 10\ \text{V}$ at $100\ \text{Hz}$ and $10\ \text{kHz}$ through the $47\ \text{nF}$ low-pass filter (Lecture 2025-03-18, ll. 71–102; AC Analysis 03 slides 17–18). → [[#RC low-pass output at 100 Hz and 10 kHz]]

### Further practice

- [ ] Design an active inverting low-pass filter with $R_1 = 10\ \text{k}\Omega$, a DC pass-band gain of $+20\ \text{dB}$ ($|H(0)| = 10$) and a $-3\ \text{dB}$ cut-off of $f_c = 1\ \text{kHz}$; the answer is $R_2 = 10 R_1 = 100\ \text{k}\Omega$ and $C = \dfrac{1}{2\pi f_c R_2} = 1.59\ \text{nF}$ (suggested, not lecturer-set). → [[#Cascaded band-pass and active op-amp filters]]

## Transcript and slide slips

> [!warning] Niu notes drop the 2π from the cut-off frequency in hertz
> Where: [[#Cut-off frequency and the half-power point]]
> Equation (17) on p. 17 of `02 - Sources/S2 AC Analysis/S2 AC Analysis Lecture Notes 2021 - Niu.pdf` writes the natural cut-off frequency in hertz as "$f_c = \dfrac{\omega_c}{2\pi} = \dfrac{1}{RC}$", dropping the factor of $2\pi$ from the denominator of the final expression. Since $\omega_c = \dfrac{1}{RC}\ \text{rad s}^{-1}$, the cut-off in hertz is $f_c = \dfrac{\omega_c}{2\pi} = \dfrac{1}{2\pi RC}\ \text{Hz}$, as printed correctly on slide 4 of `S2-W24 AC Analysis 03 - Filters and Loads - Lecture Slides.pdf`.

> [!warning] Unit mismatch in the 3 kHz RL high-pass example
> Where: [[#RL high-pass filter with a 3 kHz corner]]
> On slide 10 of `S2-W24 AC Analysis 03 - Filters and Loads - Lecture Slides.pdf`, the schematic gives the inductance as $L = 0.3\ \text{mH}$, the intermediate denominator substitutes $300\ \text{mH}$ ("$2(3.14)(300\ \text{mH}) = 3000\ \text{Hz}$"), and the final line states $R = 5.65\ \text{k}\Omega$, while `FEEG1004 Lecture 2025-03-14.txt` (l. 518) reads "$0.65\ \text{k}\Omega$". For the schematic value $L = 0.3\ \text{mH} = 3 \times 10^{-4}\ \text{H}$ at $f_c = 3\ \text{kHz}$, $R = 2\pi f_c L = 2\pi(3000)(3 \times 10^{-4}) = 5.65\ \Omega$. If the inductance were $L = 300\ \text{mH} = 0.3\ \text{H}$, the required resistance would scale by $10^3$ to $R = 5.65\ \text{k}\Omega$, which is the slide's final value.

> [!warning] Resistor value mismatch (47 kΩ against 4.7 kΩ) and a decimal typo on slide 18 of AC Analysis 03
> Where: [[#RC low-pass output at 100 Hz and 10 kHz]]
> The problem on slides 17–18 of `S2-W24 AC Analysis 03 - Filters and Loads - Lecture Slides.pdf` specifies "a resistor of $47\ \text{k}\Omega$ in series with a capacitor of $47\ \text{nF}$", but the worked solution on slide 18 substitutes $R = 4700\ \Omega$ ($4.7\ \text{k}\Omega$) into $Z_T = 4700 - 33863j\ \Omega$ at $100\ \text{Hz}$ and $Z_T = 4700 - 338.63j\ \Omega$ at $10\ \text{kHz}$. The second line of part (b) on slide 18 also misprints $Z_C = -338.63j\ \Omega$ as "$-33.863j\ \Omega$" before using $338.63\ \Omega$ on the next line. Both the $R = 4.7\ \text{k}\Omega$ and the $R = 47\ \text{k}\Omega$ results are given in [[#RC low-pass output at 100 Hz and 10 kHz]].
