---
title: "FEEG1004 D1 - AC Waveforms, RMS and Phasors"
module: "FEEG1004 Electronics"
type: topic
stream: "Part D: AC Circuit Analysis"
order: 1
tags: [feeg1004, ac-circuits, waveform, rms, phasor, complex-numbers, euler]
aliases: ["AC Analysis 01", "Phasors", "RMS", "Complex phasor notation"]
date: 2026-09-27
status: lectured
coverage: "FEEG1004 Lecture 2025-02-24 (ll. 13–497); FEEG1004 Lecture 2025-02-28 (ll. 1–558)"
parent: ["[[FEEG1004 Electronics Hub]]"]
prerequisites: ["[[FEEG1004 A5 - Inductors and Electrical Resonance]]", "[[FEEG1004 C2 - AC Synchronous Generators and Three-Phase Systems]]"]
next_topics: ["[[FEEG1004 D2 - Impedance and Phasor Circuit Analysis]]"]
key_concepts: ["[[RMS Value]]", "[[Phasor Representation]]"]
tutorial_sheets: ["[[FEEG1004 Tutorial 7 - Phasors and Complex Impedance Solutions]]"]
sources: ["02 - Sources/S2 AC Analysis/S2-W22 AC Analysis 01 - Phasors and Complex Numbers - Lecture Slides.pdf", "02 - Sources/S2 AC Analysis/S2 AC Analysis Lecture Notes 2021 - Niu.pdf", "02 - Sources/S2 AC Analysis/S2 Complex Numbers for AC Analysis - Niu.pdf", "02 - Sources/Lectures/FEEG1004 Lecture 2025-02-24.txt", "02 - Sources/Lectures/FEEG1004 Lecture 2025-02-28.txt", "02 - Sources/Tutorial Sheets/Tutorial Sheet 07 - AC Circuits 1 - Phasors & Complex Impedance.pdf", "02 - Sources/Tutorial Sheets/Tutorial Sheet 07 - AC Circuits 1 - Phasors & Complex Impedance - Solutions.pdf"]
---

# FEEG1004 D1 - AC Waveforms, RMS and Phasors

> [!abstract] Summary
> In sinusoidal steady state every voltage and current is written in cosine form with an RMS magnitude, $v(t) = V_p\cos(\omega t + \theta) = \sqrt{2}\,V\cos(\omega t + \theta)$, where the RMS value $V = V_p/\sqrt{2} \approx 0.7071\,V_p$ is the DC voltage that gives the same average heating $P = V^2/R = I^2R$ in a resistor. Because a linear circuit driven at one angular frequency $\omega$ responds at that frequency everywhere, each sinusoid is fixed by its RMS magnitude and phase, which Euler's formula $e^{j\theta} = \cos\theta + j\sin\theta$ packs into a stationary complex phasor $\mathbf{V} = Ve^{j\theta} = V\angle\theta$. KCL and KVL hold for phasors, so time-domain differential equations and trigonometric combinations of waveforms become complex algebra.

> [!summary]- Exam use: quick path
> - **Use it when:** a sinusoid is given as a trace or a formula and its RMS value, frequency or phasor is wanted, or same-frequency sinusoids must be added, subtracted, multiplied or divided.
> - **Assumptions:** sinusoidal steady state at a single angular frequency; phasor magnitudes are RMS values and angles are measured against a cosine reference.
> - **Method:** 1. Rewrite any sine or negative amplitude as a positive cosine, e.g. $\sin(\omega t + \alpha) = \cos(\omega t + \alpha - 90^\circ)$. 2. Divide the peak by $\sqrt{2}$ for the RMS magnitude. 3. Write $\mathbf{V} = V\angle\theta = V\cos\theta + jV\sin\theta$. 4. Add and subtract in Cartesian form; multiply and divide in polar form. 5. Convert back with a quadrant check and $v(t) = \sqrt{2}\,V\cos(\omega t + \theta)$.
> - **Common mistakes:** reading the phase straight from a sine without subtracting $90^\circ$; taking $\arctan(y/x)$ without adding or subtracting $180^\circ$ when $x < 0$.
> - **Practise:** [[#Waveform parameters and sine-to-cosine phasors]] · [[FEEG1004 Tutorial 7 - Phasors and Complex Impedance Solutions#Q1: Complex-number operations|Tutorial 7 Q1]]

Electrical power is generated, transmitted and distributed almost everywhere as sinusoidal alternating current (AC). Synchronous generators induce sinusoidal EMFs as their rotors turn, transformers step AC voltages up and down efficiently to reduce $I^2R$ transmission losses, and AC circuit breakers can extinguish arcs at the natural current zero-crossings.

When an AC source drives a network of resistors, inductors and capacitors, Kirchhoff's laws still hold at every instant, but the element laws $v_L = L\,\mathrm{d}i/\mathrm{d}t$ and $i_C = C\,\mathrm{d}v_C/\mathrm{d}t$ turn the loop and node equations into coupled linear differential equations. Solving them in the time domain for every branch current is laborious, and unnecessary when only the steady-state response is wanted.

A linear time-invariant circuit driven at one angular frequency $\omega$ responds at that same frequency in every branch, so the time dependence is known in advance. Only two numbers, the RMS amplitude and the phase shift, distinguish one voltage or current from another. Packing them into a single complex number, a **complex phasor**, turns differentiation with respect to time into multiplication by $j\omega$, and the differential equations become DC-style circuit algebra over the complex numbers.

## 1. Sinusoidal waveforms and the cosine convention

### Amplitude, period, frequency and phase

A general sinusoidal voltage $v(t)$ or current $i(t)$ is written as

$$
v(t) = V_p\cos(\omega t + \theta) = V_p\cos(2\pi f t + \theta) = \sqrt{2}\,V\cos(\omega t + \theta).
$$

The table lists the parameters that describe the waveform.

| Symbol | Name | Definition and SI unit | Physical interpretation |
|---|---|---|---|
| $V_p$ (or $V_m$) | Peak (maximum) value | Amplitude from $0$ to the positive or negative crest $[\text{V}]$ | Maximum instantaneous stress on insulation |
| $V_{pp}$ | Peak-to-peak value | $V_{pp} = 2V_p$ $[\text{V}]$ | Total vertical span from trough ($-V_p$) to crest ($+V_p$) on an oscilloscope trace |
| $T$ | Period | Time between two successive positive peaks $[\text{s}]$ | Duration of one complete cycle |
| $f$ | Natural (cyclic) frequency | $f = \dfrac{1}{T}$ $[\text{Hz} = \text{cycles}\,\text{s}^{-1}]$ | Complete cycles per second ($50\ \text{Hz}$ for the UK National Grid, held within $\pm 0.2\ \text{Hz}$ in normal operation) |
| $\omega$ | Angular frequency | $\omega = 2\pi f = \dfrac{2\pi}{T}$ $[\text{rad}\,\text{s}^{-1}]$ | Rate of change of phase angle in radians per second |
| $\theta$ (or $\phi$) | Phase angle | Angle inside the cosine bracket at $t = 0$ $[\text{rad}\text{ or }^\circ]$ | Horizontal angular position of the wave relative to a $\cos(\omega t)$ reference |
| $V$ (or $V_{\text{rms}}$) | RMS value | $V = \dfrac{V_p}{\sqrt{2}} \approx 0.7071\,V_p$ $[\text{V}]$ | Equivalent DC heating voltage; the value AC voltmeters read |

The sign of $\theta$ decides which way the waveform is shifted along the time axis relative to the reference $V_p\cos(\omega t)$. With a negative phase angle, $v(t) = V_p\cos(\omega t - \phi)$ with $\phi > 0$, the crest $\omega t - \phi = 0$ occurs at the positive time $t = \phi/\omega$. The waveform is shifted to the right (delayed), so it **lags** the reference by $\phi$. With a positive phase angle, $v(t) = V_p\cos(\omega t + \phi)$, the crest occurs earlier, at $t = -\phi/\omega < 0$. The waveform is shifted to the left (advanced), so it **leads** the reference by $\phi$.

### Cosine convention and trigonometric identities

A sinusoid can be written with either $\sin$ or $\cos$, the two differing by $90^\circ$ ($\pi/2\ \text{rad}$) of phase, so mixing them in one circuit would corrupt phase comparisons. Every AC voltage and current is written as a cosine with a positive amplitude before its phasor is taken:

$$
v(t) = V_p\cos(\omega t + \phi_1), \qquad i(t) = I_p\cos(\omega t + \phi_2)
$$

A quantity given as a sine, or as a negative cosine or sine, is converted to positive cosine form with the shift identities:

$$
\sin(\omega t + \phi) = \cos(\omega t + \phi - 90^\circ) = \cos\!\left(\omega t + \phi - \frac{\pi}{2}\right)
$$

$$
\cos(\omega t + \phi) = \sin(\omega t + \phi + 90^\circ) = \sin\!\left(\omega t + \phi + \frac{\pi}{2}\right)
$$

$$
-\sin(\omega t + \phi) = \cos(\omega t + \phi + 90^\circ) = \cos\!\left(\omega t + \phi + \frac{\pi}{2}\right)
$$

$$
-\cos(\omega t + \phi) = \cos(\omega t + \phi \pm 180^\circ) = \cos(\omega t + \phi \pm \pi)
$$

The compound-angle and double-angle identities recur in the RMS and AC power derivations:

$$
\sin(\alpha \pm \beta) = \sin\alpha\cos\beta \pm \cos\alpha\sin\beta
$$

$$
\cos(\alpha \pm \beta) = \cos\alpha\cos\beta \mp \sin\alpha\sin\beta
$$

$$
\cos^2\theta = \frac{1 + \cos(2\theta)}{2}, \qquad \sin^2\theta = \frac{1 - \cos(2\theta)}{2}
$$

## 2. RMS value and equivalent heating power

The time-average of a pure sinusoid $v(t) = V_p\cos(\omega t)$ over a full period is zero, because the positive and negative half-cycles cancel. The power dissipated as heat in a resistor depends on $v^2(t)$, however, which is non-negative in both half-cycles.

The **root-mean-square (RMS)** voltage $V$ (and RMS current $I$) is defined as the DC voltage (or current) that produces the same average heating power $P$ in a resistor $R$. In a DC circuit, a constant voltage $V$ drives a constant current $I = V/R$, and the power dissipated is

$$
P_{\text{DC}} = V I = I^2 R = \frac{V^2}{R}.
$$

With $v(t) = V_p\cos(2\pi f t)$ across the same resistance, Ohm's law holds at every instant, so the current is

$$
i(t) = \frac{v(t)}{R} = \frac{V_p}{R}\cos(2\pi f t).
$$

The instantaneous power is the product of voltage and current:

$$
p(t) = v(t)\,i(t) = \left(V_p\cos(2\pi f t)\right)\left(\frac{V_p}{R}\cos(2\pi f t)\right) = \frac{V_p^2}{R}\cos^2(2\pi f t)
$$

Integrating over one period $T = 1/f$ and dividing by $T$ gives the average power:

$$
P_{\text{AC}} = \frac{1}{T}\int_0^T p(t)\,\mathrm{d}t = \frac{1}{T}\int_0^T \frac{V_p^2}{R}\cos^2(2\pi f t)\,\mathrm{d}t
$$

The half-angle identity $\cos^2(2\pi f t) = \dfrac{1 + \cos(4\pi f t)}{2}$ turns the integrand into

$$
P_{\text{AC}} = \frac{V_p^2}{R}\,\frac{1}{T}\int_0^T \frac{1 + \cos(4\pi f t)}{2}\,\mathrm{d}t.
$$

Splitting the integral into the constant term and the cosine term at $2f$,

$$
P_{\text{AC}} = \frac{V_p^2}{2R}\,\frac{1}{T}\left[\int_0^T 1\,\mathrm{d}t + \int_0^T \cos(4\pi f t)\,\mathrm{d}t\right].
$$

Over $t \in [0, T]$ the second integral vanishes, since $4\pi f T = 4\pi$ and $\sin(4\pi) - \sin(0) = 0$:

$$
P_{\text{AC}} = \frac{V_p^2}{2R}\,\frac{1}{T}\left[T + 0\right] = \frac{V_p^2}{2R}
$$

Writing $V_p^2/2$ as a single squared voltage puts $P_{\text{AC}}$ in the form of the DC result $P_{\text{DC}} = V^2/R$:

$$
P_{\text{AC}} = \frac{\left(V_p / \sqrt{2}\right)^2}{R}
$$

Setting $P_{\text{AC}} = P_{\text{DC}}$ gives the RMS voltage and, by the same argument, the RMS current of any sinusoid:

$$
V = V_{\text{rms}} = \frac{V_p}{\sqrt{2}} \approx 0.7071\,V_p, \qquad I = I_{\text{rms}} = \frac{I_p}{\sqrt{2}} \approx 0.7071\,I_p
$$

Conversely, the peak is $\sqrt{2} \approx 1.4142$ times the RMS value ($V_p = \sqrt{2}\,V$). An AC supply or appliance rating quoted without qualification, such as $230\ \text{V}$ UK domestic mains or a $240\ \text{V}$ heater, is the RMS value, so the mains has $V_p = 230\sqrt{2} \approx 325.3\ \text{V}$ and $V_{pp} \approx 650.5\ \text{V}$. Standard AC voltmeters and ammeters are calibrated to display RMS values.

![[ee_d1_ac_waveform_rms.png|900]]

## 3. Rotating vectors, phasors and Euler's formula

### Why time-domain equations become unwieldy

In a lumped-parameter AC circuit, where the components are much smaller than the electromagnetic wavelength and radiated energy is negligible, **Kirchhoff's current law (KCL)** and **Kirchhoff's voltage law (KVL)** hold at every instant:

$$
\sum_{\text{node}} i_k(t) = 0, \qquad \sum_{\text{loop}} v_k(t) = 0
$$

The voltage–current relations of the three passive elements, however, involve time derivatives and integrals:

$$
v_R(t) = R\,i(t), \qquad v_L(t) = L\frac{\mathrm{d}i(t)}{\mathrm{d}t}, \qquad v_C(t) = \frac{1}{C}\int i(t)\,\mathrm{d}t \iff i_C(t) = C\frac{\mathrm{d}v_C(t)}{\mathrm{d}t}
$$

For a single-loop series $RLC$ circuit driven by $v_s(t) = \sqrt{2}\,V\cos(\omega t + \phi)$, KVL gives the integro-differential equation

$$
R\,i(t) + L\frac{\mathrm{d}i(t)}{\mathrm{d}t} + \frac{1}{C}\int i(t)\,\mathrm{d}t = \sqrt{2}\,V\cos(\omega t + \phi).
$$

Differentiating once gives a second-order linear differential equation, and a circuit with $N$ independent energy-storage elements gives an $N$-th order equation. Its time-domain solution contains both the natural transient response, which decays exponentially to zero, and the **sinusoidal steady-state response**. When only the steady state at $\omega$ is needed, phasors bypass the differential equation altogether.

### Phasors as frozen rotating vectors

Consider a vector $\vec{OA}$ of length $I_p = \sqrt{2}\,I$, anchored at the origin $O$ of a plane and rotating counter-clockwise at constant angular velocity $\omega\ \text{rad}\,\text{s}^{-1}$. If it starts at angle $\phi$ from the positive horizontal axis at $t = 0$, its angle at time $t$ is $\theta(t) = \omega t + \phi$, and its projection onto the horizontal axis is

$$
i(t) = I_p\cos(\omega t + \phi) = \sqrt{2}\,I\cos(\omega t + \phi),
$$

while its projection onto the vertical axis traces $\sqrt{2}\,I\sin(\omega t + \phi)$. Every voltage and current in a steady-state circuit rotates counter-clockwise at the same angular speed $\omega$, so their relative angles never change. The rotating vectors can therefore be frozen at $t = 0$, and their lengths scaled by $1/\sqrt{2}$ so that each equals the RMS value $I$ or $V$ read by ammeters and voltmeters.

A **phasor** (from *phase vector*) is this stationary arrow at $t = 0$, with length equal to the RMS magnitude $V$ (or $I$) and angle $\phi$ measured counter-clockwise from the positive horizontal axis. Two phasors $\vec{OA}$ and $\vec{OB}$ with the same angle ($\phi_A = \phi_B$) point the same way; their waveforms are **in phase**, crossing zero and peaking together. Because phasors rotate counter-clockwise as time advances, if $\vec{OB}$ sits an angle $\alpha > 0$ counter-clockwise ahead of $\vec{OA}$ ($\phi_B - \phi_A = \alpha$), then $\vec{OB}$ leads $\vec{OA}$ by $\alpha$ and $\vec{OA}$ lags $\vec{OB}$ by $\alpha$.

Two sinusoids of the same frequency, such as $v_1(t) + v_2(t)$ or $i_1(t) - i_2(t)$, combine by adding their phasors tip-to-tail (the parallelogram rule), or by projecting both arrows onto the horizontal and vertical axes:

$$
X_{\text{tot}} = V_1\cos\phi_1 + V_2\cos\phi_2, \qquad Y_{\text{tot}} = V_1\sin\phi_1 + V_2\sin\phi_2
$$

$$
V_{\text{tot}} = \sqrt{X_{\text{tot}}^2 + Y_{\text{tot}}^2}, \qquad \phi_{\text{tot}} = \arctan\!\left(\frac{Y_{\text{tot}}}{X_{\text{tot}}}\right) \quad \text{(with quadrant check)}
$$

### Complex phasor notation from Euler's formula

Tip-to-tail diagrams work well for two vectors but become cumbersome in multi-mesh circuits. **Euler's formula** links the trigonometric functions to complex exponentials:

$$
e^{j\theta} = \cos\theta + j\sin\theta
$$

Here $j = \sqrt{-1}$ ($j^2 = -1$) is the imaginary unit, written $j$ in electrical engineering so that $i$ and $I$ stay reserved for current. By Euler's formula, a rotating complex exponential with amplitude $\sqrt{2}\,V$ and initial phase $\phi$ expands as

$$
\sqrt{2}\,V e^{j(\omega t + \phi)} = \sqrt{2}\,V\cos(\omega t + \phi) + j\sqrt{2}\,V\sin(\omega t + \phi).
$$

The physical voltage $v(t) = \sqrt{2}\,V\cos(\omega t + \phi)$ is the real part of this exponential. Factoring $e^{j(\omega t + \phi)} = e^{j\phi} e^{j\omega t}$ separates the stationary complex amplitude from the rotating factor $e^{j\omega t}$:

$$
v(t) = \Re\!\left\{\sqrt{2}\,V e^{j(\omega t + \phi)}\right\} = \Re\!\left\{\sqrt{2}\,\underbrace{\left(V e^{j\phi}\right)}_{\mathbf{V}} e^{j\omega t}\right\}
$$

The complex number $\mathbf{V}$, printed in bold capitals or written with an underbar $\underline{V}$ by hand, is the **complex phasor voltage**, and $\mathbf{I}$ is the **complex phasor current**:

$$
\mathbf{V} = V e^{j\phi} = V\angle\phi = V\cos\phi + jV\sin\phi
$$

$$
\mathbf{I} = I e^{j\phi} = I\angle\phi = I\cos\phi + jI\sin\phi
$$

To return from a phasor $\mathbf{V} = V\angle\phi$ to the waveform at angular frequency $\omega$, multiply the RMS modulus by $\sqrt{2}$ and put $\phi$ into $\cos(\omega t + \phi)$:

$$
\mathbf{V} = V\angle\phi \quad \longrightarrow \quad v(t) = \sqrt{2}\,V\cos(\omega t + \phi)
$$

KCL and KVL are sums of same-frequency sinusoids, so they hold directly for the complex phasors as well.

![[ee_d1_phasors.png|900]]

## 4. Complex arithmetic and quadrant conversions

### Rectangular, polar and exponential forms

A complex number $z$ is plotted as the point $(x, y)$, or a vector from the origin, on the **Argand diagram** (the complex plane), with the **real axis** ($\Re$) horizontal and the **imaginary axis** ($\Im$) vertical. It has three equivalent forms. The Cartesian (rectangular) form is

$$
z = x + jy, \qquad x = \Re(z), \quad y = \Im(z).
$$

The imaginary part $\Im(z) = y$ is itself a real number and does not include $j$. The polar (modulus–argument, or Steinmetz) form is

$$
z = r\angle\theta = r(\cos\theta + j\sin\theta),
$$

where $r = |z| = \text{mod}(z) \ge 0$ is the **modulus** (length) and $\theta = \arg(z)$ is the **argument**, the angle from the positive real axis measured counter-clockwise. The exponential (Euler) form is

$$
z = r e^{j\theta}.
$$

In $z = r e^{j\theta}$, as used in calculus or Python's `cmath`, $\theta$ must be in radians; in the engineering notation $r\angle\theta$ it may be written in degrees ($r\angle 30^\circ$) or radians ($r\angle(\pi/6)$).

### Four-quadrant conversion rules

Converting from polar to Cartesian form is direct in all four quadrants, because $\cos\theta$ and $\sin\theta$ carry the correct signs:

$$
x = r\cos\theta, \qquad y = r\sin\theta
$$

Converting from Cartesian to polar form uses the Pythagorean modulus and the inverse tangent:

$$
r = \sqrt{x^2 + y^2}
$$

> [!warning] Check the quadrant of $(x, y)$ before taking $\theta = \arg(x + jy)$
> A calculator's $\tan^{-1}(y/x)$ returns only the principal value in the right half-plane, $-90^\circ < \tan^{-1}(y/x) < +90^\circ$ ($-\pi/2$ to $+\pi/2$). When the real part is negative ($x < 0$), $z = x + jy$ lies in Quadrant II or III, and $180^\circ$ ($\pi\ \text{rad}$) must be added or subtracted to put $\theta$ in the correct quadrant.

The full set of rules for the principal argument is:

| Quadrant on Argand plane | Signs of $x = \Re(z)$ and $y = \Im(z)$ | Principal argument $\theta = \arg(z) \in (-180^\circ, +180^\circ]$ | Angle in radians $\theta \in (-\pi, +\pi]$ |
|---|---|---|---|
| Quadrant I (top-right) | $x > 0,\quad y > 0$ | $\theta = \arctan\!\left(\dfrac{y}{x}\right)$ | $\theta = \arctan\!\left(\dfrac{y}{x}\right)$ |
| Quadrant II (top-left) | $x < 0,\quad y > 0$ | $\theta = \arctan\!\left(\dfrac{y}{x}\right) + 180^\circ$ | $\theta = \arctan\!\left(\dfrac{y}{x}\right) + \pi$ |
| Quadrant III (bottom-left) | $x < 0,\quad y < 0$ | $\theta = \arctan\!\left(\dfrac{y}{x}\right) - 180^\circ$ | $\theta = \arctan\!\left(\dfrac{y}{x}\right) - \pi$ |
| Quadrant IV (bottom-right) | $x > 0,\quad y < 0$ | $\theta = \arctan\!\left(\dfrac{y}{x}\right)$ | $\theta = \arctan\!\left(\dfrac{y}{x}\right)$ |
| Imaginary axis | $x = 0,\quad y \ne 0$ | $+90^\circ$ if $y > 0$;\quad $-90^\circ$ if $y < 0$ | $+\pi/2$ if $y > 0$;\quad $-\pi/2$ if $y < 0$ |

The unit vectors along the axes are:

$$
1 = 1\angle 0^\circ = e^{j0}, \qquad j = 1\angle 90^\circ = e^{j\pi/2}, \qquad -1 = 1\angle 180^\circ = e^{j\pi}, \qquad \frac{1}{j} = -j = 1\angle(-90^\circ) = e^{-j\pi/2}
$$

### Algebraic operations and complex conjugates

Let $z_1 = x_1 + jy_1 = r_1 e^{j\theta_1} = r_1\angle\theta_1$ and $z_2 = x_2 + jy_2 = r_2 e^{j\theta_2} = r_2\angle\theta_2$. Two complex numbers are equal, $z_1 = z_2$, if and only if $x_1 = x_2$ and $y_1 = y_2$, or equivalently $r_1 = r_2$ and $\theta_1 = \theta_2 + 2\pi k$.

Addition and subtraction are done in Cartesian form, adding or subtracting the real and imaginary parts separately:

$$
z_1 \pm z_2 = (x_1 + jy_1) \pm (x_2 + jy_2) = (x_1 \pm x_2) + j(y_1 \pm y_2)
$$

Multiplication can be done in either form. In Cartesian form, expand the brackets and substitute $j^2 = -1$:

$$
z_1 z_2 = (x_1 + jy_1)(x_2 + jy_2) = x_1 x_2 + jx_1 y_2 + jy_1 x_2 + j^2 y_1 y_2 = (x_1 x_2 - y_1 y_2) + j(x_1 y_2 + y_1 x_2)
$$

In polar or exponential form, multiply the moduli and add the arguments:

$$
z_1 z_2 = \left(r_1 e^{j\theta_1}\right)\left(r_2 e^{j\theta_2}\right) = r_1 r_2 e^{j(\theta_1 + \theta_2)} = r_1 r_2\angle(\theta_1 + \theta_2)
$$

The **complex conjugate** $z^*$ of $z = x + jy = r\angle\theta$ reverses the sign of the imaginary part, reflecting the vector in the real axis:

$$
z^* = x - jy = r e^{-j\theta} = r\angle(-\theta)
$$

A complex number times its own conjugate is real, non-negative and equal to the square of the modulus:

$$
z z^* = (x + jy)(x - jy) = x^2 - jxy + jxy - j^2 y^2 = x^2 + y^2 = |z|^2 = r^2
$$

Division is easiest in polar or exponential form: divide the moduli and subtract the denominator's argument from the numerator's:

$$
\frac{z_1}{z_2} = \frac{r_1 e^{j\theta_1}}{r_2 e^{j\theta_2}} = \frac{r_1}{r_2}e^{j(\theta_1 - \theta_2)} = \frac{r_1}{r_2}\angle(\theta_1 - \theta_2)
$$

In Cartesian form, multiply numerator and denominator by the conjugate of the denominator, $z_2^* = x_2 - jy_2$, to make the denominator real:

$$
\frac{z_1}{z_2} = \frac{x_1 + jy_1}{x_2 + jy_2}\times\frac{x_2 - jy_2}{x_2 - jy_2} = \frac{(x_1 x_2 + y_1 y_2) + j(y_1 x_2 - x_1 y_2)}{x_2^2 + y_2^2} = \frac{x_1 x_2 + y_1 y_2}{x_2^2 + y_2^2} + j\,\frac{y_1 x_2 - x_1 y_2}{x_2^2 + y_2^2}
$$

In Python, complex numbers take a trailing `j` (for example `z = 4 + 3j`). `abs(z)` returns $r$, `cmath.phase(z)` returns $\theta$ in radians with the quadrant handled by `atan2`, `cmath.polar(z)` returns `(r, theta_rad)`, and `cmath.rect(r, theta_rad)` converts polar back to Cartesian.

## Worked examples

### Waveform parameters and sine-to-cosine phasors

(1) An oscilloscope shows a sinusoidal voltage with peak-to-peak value $V_{pp} = 40\ \text{V}$ and period $T = 50\ \mu\text{s}$, crossing zero going positive at $t = 0$. Find $V_p$, the RMS voltage $V$, $f$ and $\omega$, and write $v(t)$ in sine and standard cosine forms. (2) Write the standard cosine expressions and the RMS phasors, in polar and Cartesian form, for (a) $v_a(t) = 50\sqrt{2}\cos(377t - 35^\circ)\ \text{V}$, (b) $v_b(t) = 83.6\sin(400t - 15^\circ)\ \text{V}$, (c) $i_c(t) = 90.4\sqrt{2}\cos(754t - 48^\circ)\ \text{mA}$ and (d) $i_d(t) = 3.46\sin(815t + 30^\circ)\ \text{A}$ (Tutorial Sheet 7 Q2).

(1) The peak is half the peak-to-peak span, and the RMS value is the peak over $\sqrt{2}$:

$$
V_p = \frac{V_{pp}}{2} = \frac{40\ \text{V}}{2} = 20.0\ \text{V}, \qquad V = \frac{V_p}{\sqrt{2}} = \frac{20.0\ \text{V}}{\sqrt{2}} = 14.14\ \text{V}
$$

From $T = 50\ \mu\text{s} = 50 \times 10^{-6}\ \text{s}$, the frequency and angular frequency are

$$
f = \frac{1}{T} = \frac{1}{50 \times 10^{-6}\ \text{s}} = 20\,000\ \text{Hz} = 20.0\ \text{kHz},
$$

$$
\omega = 2\pi f = 2\pi(20\,000\ \text{Hz}) = 40\,000\pi\ \text{rad}\,\text{s}^{-1} \approx 1.257 \times 10^5\ \text{rad}\,\text{s}^{-1}.
$$

The wave starts at $v(0) = 0$ going positive, so it is a pure sine, $v(t) = 20\sin(40\,000\pi t)\ \text{V}$. With $\sin(\omega t) = \cos(\omega t - 90^\circ)$ the cosine form is

$$
v(t) = 20\cos(40\,000\pi t - 90^\circ)\ \text{V} = 14.14\sqrt{2}\cos\!\left(40\,000\pi t - \frac{\pi}{2}\right)\ \text{V}.
$$

(2a) $v_a(t) = 50\sqrt{2}\cos(377t - 35^\circ)\ \text{V}$ is already in the form $\sqrt{2}\,V\cos(\omega t + \theta)$, with $V_a = 50.0\ \text{V}$, $\omega = 377\ \text{rad}\,\text{s}^{-1}$ ($f = 377/(2\pi) = 60.0\ \text{Hz}$) and $\theta_a = -35^\circ$:

$$
\mathbf{V}_a = 50\angle(-35^\circ)\ \text{V} = 50\cos(-35^\circ) + j\,50\sin(-35^\circ) = (40.96 - j28.68)\ \text{V}
$$

(2b) For $v_b(t) = 83.6\sin(400t - 15^\circ)\ \text{V}$, the RMS value is the peak $V_p = 83.6\ \text{V}$ over $\sqrt{2}$:

$$
V_b = \frac{83.6\ \text{V}}{\sqrt{2}} = 59.11\ \text{V}
$$

Converting the sine with $\sin(\alpha) = \cos(\alpha - 90^\circ)$,

$$
v_b(t) = 59.11\sqrt{2}\cos(400t - 15^\circ - 90^\circ) = 59.11\sqrt{2}\cos(400t - 105^\circ)\ \text{V}.
$$

Reading off the RMS magnitude and cosine phase gives the phasor:

$$
\mathbf{V}_b = 59.1\angle(-105^\circ)\ \text{V} = 59.11\cos(-105^\circ) + j\,59.11\sin(-105^\circ) = (-15.30 - j57.10)\ \text{V}
$$

(2c) $i_c(t) = 90.4\sqrt{2}\cos(754t - 48^\circ)\ \text{mA}$ is already in standard form, with $I_c = 90.4\ \text{mA}$ and $\theta_c = -48^\circ$:

$$
\mathbf{I}_c = 90.4\angle(-48^\circ)\ \text{mA} = 90.4\cos(-48^\circ) + j\,90.4\sin(-48^\circ) = (60.49 - j67.18)\ \text{mA}
$$

(2d) For $i_d(t) = 3.46\sin(815t + 30^\circ)\ \text{A}$, divide the peak $I_p = 3.46\ \text{A}$ by $\sqrt{2}$:

$$
I_d = \frac{3.46\ \text{A}}{\sqrt{2}} = 2.447\ \text{A} \approx 2.45\ \text{A}
$$

Subtracting $90^\circ$ converts the sine to a cosine:

$$
i_d(t) = 2.45\sqrt{2}\cos(815t + 30^\circ - 90^\circ) = 2.45\sqrt{2}\cos(815t - 60^\circ)\ \text{A}
$$

The RMS current phasor is therefore

$$
\mathbf{I}_d = 2.45\angle(-60^\circ)\ \text{A} = 2.447\cos(-60^\circ) + j\,2.447\sin(-60^\circ) = (1.22 - j2.12)\ \text{A}.
$$

> [!check] Instantaneous values at $t = 0$
> For (b), the original sine gives $v_b(0) = 83.6\sin(-15^\circ) = -21.64\ \text{V}$. The cosine form gives $59.114\sqrt{2}\cos(-105^\circ) = 83.6(-0.25882) = -21.64\ \text{V}$, which is also $\sqrt{2}\,\Re(\mathbf{V}_b) = \sqrt{2}(-15.30\ \text{V}) = -21.64\ \text{V}\ \checkmark$. For (d), $i_d(0) = 3.46\sin(30^\circ) = +1.730\ \text{A}$, and $\sqrt{2}\,\Re(\mathbf{I}_d) = \sqrt{2}(2.4466\cos(-60^\circ)) = 3.46(0.5) = +1.730\ \text{A}\ \checkmark$.

### Adding and subtracting two series sources

Two series voltage sources have

$$
v_1(t) = 60\sqrt{2}\cos(\omega t)\ \text{V}, \qquad v_2(t) = 40\sqrt{2}\cos\!\left(\omega t - \frac{\pi}{3}\right)\ \text{V}.
$$

Use complex phasors to find (1) the sum $v_{\text{sum}}(t) = v_1(t) + v_2(t)$ and (2) the difference $v_{\text{diff}}(t) = v_1(t) - v_2(t)$.

Both waveforms are already in the form $\sqrt{2}\,V\cos(\omega t + \theta)$. For $v_1$ the RMS voltage is $V_1 = 60\ \text{V}$ and the phase is $\theta_1 = 0\ \text{rad}$ ($0^\circ$):

$$
\mathbf{V}_1 = 60\angle 0^\circ = 60(\cos 0 + j\sin 0) = 60(1 + j0) = 60.0 + j0.0\ \text{V}
$$

For $v_2$ the RMS voltage is $V_2 = 40\ \text{V}$ and the phase is $\theta_2 = -\pi/3\ \text{rad} = -60^\circ$:

$$
\mathbf{V}_2 = 40\angle\!\left(-\frac{\pi}{3}\right) = 40\left[\cos\!\left(-\frac{\pi}{3}\right) + j\sin\!\left(-\frac{\pi}{3}\right)\right]
$$

With $\cos(-\pi/3) = 0.5000$ and $\sin(-\pi/3) = -\sqrt{3}/2 \approx -0.86603$,

$$
\mathbf{V}_2 = 40(0.5000 - j0.86603) = (20.0 - j34.641)\ \text{V}.
$$

(1) Adding the real and imaginary parts,

$$
\mathbf{V}_{\text{sum}} = \mathbf{V}_1 + \mathbf{V}_2 = (60.0 + 20.0) + j(0.0 - 34.641) = (80.0 - j34.641)\ \text{V}.
$$

With $x = +80.0 > 0$ and $y = -34.641 < 0$, $\mathbf{V}_{\text{sum}}$ lies in Quadrant IV, where $\theta = \arctan(y/x)$ directly:

$$
V_{\text{sum}} = |\mathbf{V}_{\text{sum}}| = \sqrt{(80.0)^2 + (-34.641)^2} = \sqrt{6400 + 1200} = \sqrt{7600} = 87.18\ \text{V}
$$

$$
\theta_{\text{sum}} = \arctan\!\left(\frac{-34.641}{80.0}\right) = \arctan(-0.43301) = -23.41^\circ = -0.4086\ \text{rad}
$$

So $\mathbf{V}_1 + \mathbf{V}_2 = 87.2\angle(-23.4^\circ)\ \text{V} = 87.2\angle(-0.41\ \text{rad})\ \text{V}$, and

$$
v_{\text{sum}}(t) = v_1(t) + v_2(t) = 87.2\sqrt{2}\cos(\omega t - 0.409)\ \text{V} = 87.2\sqrt{2}\cos(\omega t - 23.4^\circ)\ \text{V}.
$$

(2) Subtracting the components of $\mathbf{V}_2$ from those of $\mathbf{V}_1$,

$$
\mathbf{V}_{\text{diff}} = \mathbf{V}_1 - \mathbf{V}_2 = (60.0 - 20.0) + j(0.0 - (-34.641)) = (40.0 + j34.641)\ \text{V}.
$$

With $x = +40.0 > 0$ and $y = +34.641 > 0$, this lies in Quadrant I:

$$
V_{\text{diff}} = |\mathbf{V}_{\text{diff}}| = \sqrt{(40.0)^2 + (34.641)^2} = \sqrt{1600 + 1200} = \sqrt{2800} = 52.92\ \text{V}
$$

$$
\theta_{\text{diff}} = \arctan\!\left(\frac{34.641}{40.0}\right) = \arctan(0.86603) = +40.89^\circ = +0.7137\ \text{rad}
$$

So $\mathbf{V}_1 - \mathbf{V}_2 = 52.9\angle 40.9^\circ\ \text{V}$, and

$$
v_{\text{diff}}(t) = v_1(t) - v_2(t) = 52.9\sqrt{2}\cos(\omega t + 0.714)\ \text{V} = 52.9\sqrt{2}\cos(\omega t + 40.9^\circ)\ \text{V}.
$$

> [!check] Direct evaluation at $\omega t = 0.70\ \text{rad}$
> At $\omega t = 0.70\ \text{rad}$ the original waveforms give $v_1 = 60\sqrt{2}\cos(0.70) = 84.853 \times 0.76484 = 64.899\ \text{V}$ and $v_2 = 40\sqrt{2}\cos(0.70 - \pi/3) = 56.569 \times \cos(-0.34720) = 56.569 \times 0.94033 = 53.193\ \text{V}$.
> The direct sum $v_1 + v_2 = 64.899 + 53.193 = 118.092\ \text{V}$ matches the phasor result $87.178\sqrt{2}\cos(0.70 - 0.40864) = 123.288\cos(0.29136) = 118.092\ \text{V}\ \checkmark$. The direct difference $v_1 - v_2 = 64.899 - 53.193 = 11.706\ \text{V}$ matches $52.915\sqrt{2}\cos(0.70 + 0.71372) = 74.833\cos(1.41372) = 11.706\ \text{V}\ \checkmark$.

### Complex division and quadrant conversions

Tutorial Sheet 7 Q1(d, e, f, g), showing the conjugate and quadrant steps: (1) evaluate $z_d = \dfrac{1}{0.2 + j0.5}$ and $z_e = \dfrac{14 + j5}{4 - j1}$ in Cartesian form; (2) convert $z_{f1} = 6 + j9$ and $z_{f2} = -21.4 + j33.3$ to polar form $r\angle\theta$ with $\theta$ in degrees; (3) convert $z_{g1} = 10\angle 20^\circ$ and $z_{g2} = 142\angle(-260.3^\circ)$ to Cartesian form.

(1) For $z_d$, multiply numerator and denominator by the conjugate of the denominator, $(0.2 - j0.5)$:

$$
z_d = \frac{1}{0.2 + j0.5}\times\frac{0.2 - j0.5}{0.2 - j0.5} = \frac{0.2 - j0.5}{(0.2)^2 + (0.5)^2}
$$

The denominator is $0.04 + 0.25 = 0.29$, so

$$
z_d = \frac{0.2}{0.29} - j\,\frac{0.5}{0.29} = 0.690 - j1.724 \quad (\text{or } 0.69 - j1.72).
$$

For $z_e$, multiply by the conjugate of the denominator, $(4 + j1)$:

$$
z_e = \frac{(14 + j5)(4 + j1)}{(4 - j1)(4 + j1)} = \frac{14(4) + j14(1) + j5(4) + j^2(5)(1)}{4^2 + 1^2}
$$

Substituting $j^2 = -1$ and simplifying,

$$
z_e = \frac{(56 - 5) + j(14 + 20)}{16 + 1} = \frac{51 + j34}{17} = \frac{51}{17} + j\,\frac{34}{17} = 3 + j2.
$$

(2) For $z_{f1} = 6 + j9$, both $x = +6$ and $y = +9$ are positive, so $z_{f1}$ is in Quadrant I:

$$
r_{f1} = \sqrt{6^2 + 9^2} = \sqrt{36 + 81} = \sqrt{117} = 10.82
$$

$$
\theta_{f1} = \arctan\!\left(\frac{9}{6}\right) = \arctan(1.500) = 56.31^\circ \implies z_{f1} = 10.8\angle 56.3^\circ
$$

For $z_{f2} = -21.4 + j33.3$, the real part is negative ($x = -21.4 < 0$) and the imaginary part positive ($y = +33.3 > 0$), so $z_{f2}$ is in Quadrant II. The modulus is

$$
r_{f2} = \sqrt{(-21.4)^2 + (33.3)^2} = \sqrt{457.96 + 1108.89} = \sqrt{1566.85} = 39.58.
$$

The principal arctangent gives $\arctan(33.3 / (-21.4)) = \arctan(-1.5561) = -57.27^\circ$, which points into Quadrant IV. Adding $180^\circ$ for Quadrant II gives the argument:

$$
\theta_{f2} = -57.27^\circ + 180^\circ = +122.73^\circ \implies z_{f2} = 39.6\angle 122.7^\circ
$$

(3) For $z_{g1} = 10\angle 20^\circ$,

$$
x_{g1} = 10\cos(20^\circ) = 10(0.93969) = 9.40, \qquad y_{g1} = 10\sin(20^\circ) = 10(0.34202) = 3.42
$$

$$
z_{g1} = 9.40 + j3.42
$$

For $z_{g2} = 142\angle(-260.3^\circ)$, which is coterminal with $-260.3^\circ + 360^\circ = +99.7^\circ$ in Quadrant II,

$$
x_{g2} = 142\cos(-260.3^\circ) = 142(-0.16849) = -23.93, \qquad y_{g2} = 142\sin(-260.3^\circ) = 142(+0.98570) = +139.97
$$

$$
z_{g2} = -23.9 + j140.0
$$

> [!check] Reverse multiplication and modulus
> Multiplying $z_e = 3 + j2$ back by the denominator gives $(3 + j2)(4 - j1) = (12 + 2) + j(-3 + 8) = 14 + j5$, the original numerator $\checkmark$. For $z_{f2} = 39.58\angle 122.73^\circ$, $39.583\cos(122.73^\circ) = -21.40$ and $39.583\sin(122.73^\circ) = +33.30\ \checkmark$; omitting the $+180^\circ$ correction and writing $39.6\angle(-57.3^\circ)$ would give $+21.4 - j33.3$, the negative of the correct number. For $z_{g1}$, $\sqrt{(9.40)^2 + (3.42)^2} = \sqrt{88.36 + 11.70} = 10.00\ \checkmark$.

## Links

- Parent: [[FEEG1004 Electronics Hub]]
- Previous: [[FEEG1004 C6 - DC Motor Characteristics and Speed Control]]
- Next: [[FEEG1004 D2 - Impedance and Phasor Circuit Analysis]]
- Concepts: [[RMS Value]] · [[Phasor Representation]]
- Tutorial solutions: [[FEEG1004 Tutorial 7 - Phasors and Complex Impedance Solutions]] (Q1, Q2)
- A complex phasor $\mathbf{V} = V e^{j\theta}$ is the complex amplitude multiplying $e^{j\omega t}$, the same object as the [[Frequency Response Function]] $G(j\omega)$ and the coefficients of the [[Complex Fourier Series]] in [[SESA2027 A5 - Frequency Response and Bode Plots]].
- The phasor steady-state response is the forced particular integral of the [[Method of Undetermined Coefficients]], or the steady-state part of the Laplace-transformed ODE in [[MATH2048 TR2 - Laplace Transforms - Definition, Properties and Solving IVPs]].
- Replacing $x(t) = X\cos(\omega t + \phi)$ with $\Re\{\mathbf{X}e^{j\omega t}\}$ turns $m\ddot{x} + c\dot{x} + kx = F_0\cos\omega t$ into the complex stiffness relation $(k - m\omega^2 + j\omega c)\mathbf{X} = \mathbf{F}$ of structural vibration: [[FEEG1002 D6 - Single Degree of Freedom Vibration]].

## Sources

- `02 - Sources/S2 AC Analysis/S2-W22 AC Analysis 01 - Phasors and Complex Numbers - Lecture Slides.pdf` (slides 1–21: waveform parameters, cosine convention, RMS heating proof, rotating vectors, complex phasor addition, complex arithmetic summary)
- `02 - Sources/S2 AC Analysis/S2 AC Analysis Lecture Notes 2021 - Niu.pdf` (pp. 1–7, 27–28: AC waveforms, RMS derivation, KCL/KVL, Euler's formula and phasors, appendix on complex numbers)
- `02 - Sources/S2 AC Analysis/S2 Complex Numbers for AC Analysis - Niu.pdf` (pp. 1–5: Argand diagram, complex conjugate division, four-quadrant argument table, Euler's formula)
- `02 - Sources/Lectures/FEEG1004 Lecture 2025-02-24.txt` (ll. 13–497: AC waveform definitions, Practice 1 and 2, cosine convention, RMS integral derivation, KCL and KVL in AC circuits)
- `02 - Sources/Lectures/FEEG1004 Lecture 2025-02-28.txt` (ll. 1–558: rotating vectors, RMS phasors, graphical and complex phasor addition of $60\sqrt{2}\cos\omega t$ and $40\sqrt{2}\cos(\omega t - \pi/3)$, complex number conversions)
- `02 - Sources/Tutorial Sheets/Tutorial Sheet 07 - AC Circuits 1 - Phasors & Complex Impedance.pdf` and `02 - Sources/Tutorial Sheets/Tutorial Sheet 07 - AC Circuits 1 - Phasors & Complex Impedance - Solutions.pdf` (Q1 and Q2)

## Self-study tasks

### Core

- [ ] Complete all seven parts of Q1 by hand, without the calculator's complex mode, then verify with its polar–rectangular conversion (Tutorial Sheet 7 Q1(a–g); 2025-02-28 transcript ll. 524–556). → [[#Complex division and quadrant conversions]]; [[FEEG1004 Tutorial 7 - Phasors and Complex Impedance Solutions#Q1: Complex-number operations|Tutorial 7 Q1]].
- [ ] Convert the four waveforms of Q2 and the four practice waveforms $230\sqrt{2}\cos(100\pi t + \pi/6)\ \text{V}$, $50\sqrt{2}\cos(40t)\ \text{A}$, $141\cos(\omega t - \pi/3)\ \text{V}$ and $100\sqrt{2}\sin(100\pi t)\ \text{A}$ into RMS phasors (Tutorial Sheet 7 Q2(a–d); AC Analysis 01 slide 9; 2025-02-24 transcript ll. 436–465). → [[#Waveform parameters and sine-to-cosine phasors]]; [[FEEG1004 Tutorial 7 - Phasors and Complex Impedance Solutions#Q2: Time functions → phasors (rms, cosine reference)|Tutorial 7 Q2]].
- [ ] For $v_1(t) = 60\sqrt{2}\cos(\omega t)\ \text{V}$ and $v_2(t) = 40\sqrt{2}\cos(\omega t - \pi/3)\ \text{V}$, find $v_1(t) - v_2(t)$ both from a phasor subtraction diagram and by Cartesian subtraction (AC Analysis 01 slide 13; 2025-02-28 transcript ll. 338–340). → [[#Adding and subtracting two series sources]].

### Further practice

- [ ] Use $V_{\text{rms}} = \sqrt{\dfrac{1}{T}\int_0^T v^2(t)\,\mathrm{d}t}$ to show that a half-wave rectified sinusoid ($V_p\cos(\omega t)$ for half the period, $0\ \text{V}$ for the other half) has $V_{\text{rms}} = V_p / 2 = 0.500\,V_p$, while a full-wave rectified sinusoid has $V_{\text{rms}} = V_p / \sqrt{2} \approx 0.707\,V_p$ (suggested, not lecturer-set). → [[#2. RMS value and equivalent heating power]].
- [ ] Sketch on one Argand diagram the RMS phasors of $i_1 = 50\sqrt{2}\cos(\omega t)\ \text{A}$, $i_2 = 50\sqrt{2}\cos(\omega t + \pi/2)\ \text{A}$, $v_1 = 30\sqrt{2}\cos(\omega t - \pi/3)\ \text{V}$ and $v_2 = 30\sqrt{2}\sin(\omega t + 2\pi/3)\ \text{V}$, and state the angle by which $v_2$ leads $v_1$ (AC Analysis 01 slide 11; 2025-02-28 transcript ll. 140–204). → [[#Phasors as frozen rotating vectors]].

## Transcript and slide slips

> [!warning] Tutorial 7 solutions print 9.58 + j3.49 for 10∠20° and swap Q1 and Q2
> Where: [[#Complex division and quadrant conversions]]
> `Tutorial Sheet 07 - AC Circuits 1 - Phasors & Complex Impedance - Solutions.pdf` (p. 1) swaps the numbering of Questions 1 and 2 relative to the question sheet. In part (g) of the complex-number question it also converts $10\angle(20^\circ)$ to "$9.58 + j3.49$". That pair has modulus $\sqrt{9.58^2 + 3.49^2} = 10.20 \ne 10$; the correct Cartesian form is $10\cos 20^\circ + j\,10\sin 20^\circ = 9.40 + j3.42$.

> [!warning] Slide 21 writes cmath.polar(x, y) with two arguments
> Where: [[#Algebraic operations and complex conjugates]]
> The reference table at the bottom of slide 21 of `S2-W22 AC Analysis 01 - Phasors and Complex Numbers - Lecture Slides.pdf` gives the rectangular-to-polar conversion as `cmath.polar(x, y)`. In Python's `cmath`, `polar` takes a single complex argument, `cmath.polar(complex(x, y))`; calling `cmath.polar(x, y)` with two arguments raises a `TypeError`.

> [!warning] Missing π in the Quadrant II and III rows of the complex-numbers handout
> Where: [[#Four-quadrant conversion rules]]
> In the four-quadrant table for $\arg z$ on p. 3 of `S2 Complex Numbers for AC Analysis - Niu.pdf`, a font-encoding omission removed the $\pi$ from the Quadrant II and III formulas, leaving `$+ \arctan(y/x)$` for Quadrant II and `$- + \arctan(y/x)$` for Quadrant III. The correct formulas for $x < 0$ are $\pi + \arctan(y/x)$ in Quadrant II ($x < 0, y > 0$) and $-\pi + \arctan(y/x)$ in Quadrant III ($x < 0, y < 0$).
