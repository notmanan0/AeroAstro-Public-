---
title: "FEEG1004 D2 - Impedance and Phasor Circuit Analysis"
module: "FEEG1004 Electronics"
type: topic
stream: "Part D: AC Circuit Analysis"
order: 2
tags: [feeg1004, ac-circuits, impedance, reactance, phasor-analysis, civil, inductive-load, capacitive-load]
aliases: ["AC Analysis 02", "Impedance", "Generalised Ohm's law", "Phasor circuit analysis", "CIVIL"]
date: 2026-09-27
status: lectured
coverage: "FEEG1004 Lecture 2025-03-11 (ll. 43–91); FEEG1004 Lecture 2025-03-14 (ll. 6–47); FEEG1004 Lecture 2025-03-18 (ll. 103–158); main AC Analysis 02 deck written-ahead from slides and Niu notes"
parent: ["[[FEEG1004 Electronics Hub]]"]
prerequisites: ["[[FEEG1004 D1 - AC Waveforms, RMS and Phasors]]", "[[FEEG1004 A6 - Mesh Analysis]]"]
next_topics: ["[[FEEG1004 D3 - AC Filters and Bode Plots]]"]
key_concepts: ["[[Complex Impedance]]", "[[Phasor Representation]]", "[[Current Divider]]", "[[Potential Divider]]"]
tutorial_sheets: ["[[FEEG1004 Tutorial 7 - Phasors and Complex Impedance Solutions]]"]
sources: ["02 - Sources/S2 AC Analysis/S2-W22-23 AC Analysis 02 - Impedance and Phasor Analysis - Lecture Slides.pdf", "02 - Sources/S2 AC Analysis/S2-W24 AC Analysis 03 - Filters and Loads - Lecture Slides.pdf", "02 - Sources/S2 AC Analysis/S2 AC Analysis Lecture Notes 2021 - Niu.pdf", "02 - Sources/S2 AC Analysis/S2 Complex Numbers for AC Analysis - Niu.pdf", "02 - Sources/Lectures/FEEG1004 Lecture 2025-03-11.txt", "02 - Sources/Lectures/FEEG1004 Lecture 2025-03-14.txt", "02 - Sources/Lectures/FEEG1004 Lecture 2025-03-18.txt", "02 - Sources/Tutorial Sheets/Tutorial Sheet 07 - AC Circuits 1 - Phasors & Complex Impedance.pdf", "02 - Sources/Tutorial Sheets/Tutorial Sheet 07 - AC Circuits 1 - Phasors & Complex Impedance - Solutions.pdf"]
---

# FEEG1004 D2 - Impedance and Phasor Circuit Analysis

> [!abstract] Summary
> Writing sinusoidal voltages and currents as complex exponentials $\sqrt{2}\,\mathbf{V}e^{j\omega t}$ and $\sqrt{2}\,\mathbf{I}e^{j\omega t}$ turns $\mathrm{d}/\mathrm{d}t$ into multiplication by $j\omega$, so every linear passive element obeys generalised Ohm's law $\mathbf{V} = Z\mathbf{I}$, with $Z_R = R$, $Z_L = j\omega L = \omega L\angle 90^\circ$ and $Z_C = 1/(j\omega C) = -jX_C = X_C\angle(-90^\circ)$. Current and voltage are in phase in a resistor, voltage leads current by $90^\circ$ in an inductor, and current leads voltage by $90^\circ$ in a capacitor. Every DC analysis tool (series and parallel reduction, potential and current dividers, KCL, KVL, mesh and nodal analysis, superposition and Thévenin's theorem) then carries over with complex arithmetic. A network with equivalent impedance $Z = R + jX$ is an inductive load if $X > 0$ (current lags voltage) and a capacitive load if $X < 0$ (current leads voltage).

> [!summary]- Exam use: quick path
> - **Use it when:** a linear circuit is driven by a single-frequency sinusoidal source in steady state and you need branch currents, element voltages or an equivalent impedance.
> - **Assumptions:** linear $R$, $L$ and $C$ elements; steady state, after transients have died away; one source angular frequency $\omega = 2\pi f$; RMS phasors on a cosine reference.
> - **Method:** 1. Replace sources by RMS phasors and elements by $Z_R$, $Z_L$, $Z_C$ at the source $\omega$. 2. Reduce series and parallel groups, or write KCL, KVL or mesh equations, in complex arithmetic. 3. Use the complex potential or current divider for a single element. 4. Classify the load from the sign of $\Im(Z)$. 5. Convert the answer back to a time function if asked.
> - **Common mistakes:** adding RMS magnitudes $V_R + V_L + V_C$ instead of phasors; putting a branch's own impedance in the numerator of the current divider instead of the opposite branch's.
> - **Practise:** [[#Series RLC circuit near resonance]] · [[FEEG1004 Tutorial 7 - Phasors and Complex Impedance Solutions#Q4: Impedance seen at A–B|Tutorial 7 Q4]]

Once sinusoidal voltages and currents are represented by complex phasors $\mathbf{V}$ and $\mathbf{I}$, the remaining obstacle in AC circuit analysis is the calculus inside the inductor law $v_L = L\,\mathrm{d}i/\mathrm{d}t$ and the capacitor law $i_C = C\,\mathrm{d}v_C/\mathrm{d}t$. Euler's exponential $e^{j\omega t}$ removes it, because differentiating or integrating the exponential returns the same exponential multiplied or divided by $j\omega$:

$$
\frac{\mathrm{d}}{\mathrm{d}t}\!\left(e^{j\omega t}\right) = j\omega e^{j\omega t}, \qquad \int e^{j\omega t}\,\mathrm{d}t = \frac{1}{j\omega}e^{j\omega t}
$$

When every voltage and current in a circuit is proportional to $e^{j\omega t}$, the common time factor cancels from every Kirchhoff loop and node equation. Each resistor, inductor and capacitor is then described by a frequency-dependent complex ratio $Z = \mathbf{V}/\mathbf{I}$, its **complex impedance**, and any steady-state AC network can be solved with the same algebraic rules as a DC resistor network.

At the two ends of the frequency range the reactive elements become familiar DC objects. An inductor passes steady current freely but opposes rapid changes, and a capacitor blocks steady current but passes rapid changes, so their impedances move in opposite directions as $\omega$ rises.

## 1. From the RL differential equation to generalised Ohm's law

Consider a resistor $R$ and an inductor $L$ in series across the sinusoidal supply

$$
v(t) = V_p\cos(\omega t) = \sqrt{2}\,V\cos(\omega t).
$$

KVL around the loop at instant $t$ gives a first-order linear differential equation:

$$
L\frac{\mathrm{d}i(t)}{\mathrm{d}t} + R\,i(t) = v(t) = \sqrt{2}\,V\cos(\omega t)
$$

Because the circuit is linear, the steady-state current in the real time domain is a sinusoid at the same angular frequency $\omega$, with unknown RMS amplitude $I$ and unknown phase angle $\phi$:

$$
i(t) = I_p\cos(\omega t + \phi) = \sqrt{2}\,I\cos(\omega t + \phi)
$$

Differentiating gives $\mathrm{d}i/\mathrm{d}t = -\omega\sqrt{2}\,I\sin(\omega t + \phi)$, and substituting into the KVL equation yields

$$
-L\omega\sqrt{2}\,I\sin(\omega t + \phi) + R\sqrt{2}\,I\cos(\omega t + \phi) = \sqrt{2}\,V\cos(\omega t)
$$

Solving this for $I$ and $\phi$ needs compound-angle expansions of $\sin(\omega t + \phi)$ and $\cos(\omega t + \phi)$. That is laborious even for a two-element loop and becomes intractable in multi-loop networks.

The same substitution is much shorter with complex exponentials. Replace the real excitation $v(t) = \Re\{\sqrt{2}\,V e^{j\omega t}\}$ and the real response $i(t) = \Re\{\sqrt{2}\,I e^{j(\omega t + \phi)}\}$ by their complex counterparts $\tilde{v}(t)$ and $\tilde{i}(t)$:

$$
\tilde{v}(t) = \sqrt{2}\,V e^{j\omega t}, \qquad \tilde{i}(t) = \sqrt{2}\,I e^{j(\omega t + \phi)}
$$

The differential equation in the complex variables is

$$
L\frac{\mathrm{d}\tilde{i}(t)}{\mathrm{d}t} + R\,\tilde{i}(t) = \tilde{v}(t)
$$

Differentiating $\tilde{i}(t) = \sqrt{2}\,I e^{j(\omega t + \phi)}$ with respect to time brings down a factor of $j\omega$:

$$
\frac{\mathrm{d}\tilde{i}(t)}{\mathrm{d}t} = j\omega\sqrt{2}\,I e^{j(\omega t + \phi)}
$$

Substituting $\tilde{i}(t)$, $\mathrm{d}\tilde{i}/\mathrm{d}t$ and $\tilde{v}(t)$ into the differential equation gives

$$
j\omega L\sqrt{2}\,I e^{j(\omega t + \phi)} + R\sqrt{2}\,I e^{j(\omega t + \phi)} = \sqrt{2}\,V e^{j\omega t}
$$

Dividing both sides by $\sqrt{2}$ and writing $e^{j(\omega t + \phi)} = e^{j\omega t} e^{j\phi}$ separates the time factor $e^{j\omega t}$ from the phasors:

$$
j\omega L I e^{j\omega t} e^{j\phi} + R I e^{j\omega t} e^{j\phi} = V e^{j\omega t} e^{j0}
$$

Since $e^{j\omega t} \ne 0$ for all $t$, it cancels from every term, leaving a purely algebraic complex equation:

$$
(R + j\omega L)\,I e^{j\phi} = V e^{j0}
$$

With the voltage phasor $\mathbf{V} = V e^{j0} = V\angle 0^\circ$, the current phasor $\mathbf{I} = I e^{j\phi} = I\angle\phi$ and the **complex impedance** $Z = R + j\omega L$, the differential equation becomes **generalised Ohm's law**:

$$
\mathbf{V} = Z\mathbf{I} \qquad \Longleftrightarrow \qquad \mathbf{I} = \frac{\mathbf{V}}{Z}
$$

For the series $RL$ circuit, dividing $\mathbf{V} = V\angle 0^\circ$ by $Z = R + j\omega L = \sqrt{R^2 + (\omega L)^2}\,\angle\!\left(\arctan\dfrac{\omega L}{R}\right)$ gives both the RMS current $I$ and the phase lag $\phi$ in one step:

$$
\mathbf{I} = I\angle\phi = \frac{V\angle 0^\circ}{\sqrt{R^2 + (\omega L)^2}\,\angle\!\left(\arctan\dfrac{\omega L}{R}\right)} = \frac{V}{\sqrt{R^2 + (\omega L)^2}}\,\angle\!\left(-\arctan\frac{\omega L}{R}\right)
$$

Every steady-state AC circuit problem follows the same three steps:

1. Transform to the phasor domain: redraw the circuit with every time-domain source $v(t), i(t)$ replaced by its RMS phasor $\mathbf{V}, \mathbf{I}$, and every resistor, inductor and capacitor replaced by its impedance $Z_R, Z_L, Z_C$ at the source angular frequency $\omega$.
2. Solve algebraically: apply the DC circuit laws (Ohm's law, series and parallel reduction, voltage and current dividers, KCL and KVL, mesh or Thévenin analysis) in complex arithmetic to find the wanted voltage or current phasors.
3. Transform back to the time domain if asked: convert $\mathbf{I} = I\angle\phi$ to $i(t) = \sqrt{2}\,I\cos(\omega t + \phi)$.

## 2. Impedances of resistors, inductors and capacitors

### Resistor

Let the current $i(t) = \sqrt{2}\,I\cos(\omega t + \phi)$, with phasor $\mathbf{I} = I e^{j\phi} = I\angle\phi$, flow through an ideal resistor $R$. Ohm's law in the time domain gives

$$
v_R(t) = R\,i(t) = \sqrt{2}\,(I R)\cos(\omega t + \phi) = \sqrt{2}\,V_R\cos(\omega t + \phi)
$$

where the RMS resistor voltage is $V_R = I R$. Its phasor is

$$
\mathbf{V}_R = V_R\angle\phi = R I\angle\phi = R I e^{j\phi} = R\mathbf{I}
$$

so the **impedance of a resistor** is

$$
Z_R = \frac{\mathbf{V}_R}{\mathbf{I}} = R = R\angle 0^\circ\ \Omega
$$

It is purely real, independent of $\omega$ and has zero phase angle, so $\mathbf{V}_R$ and $\mathbf{I}_R$ are in phase.

### Inductor and inductive reactance

Let the same current flow through an ideal inductor $L$. Faraday's law of self-induction gives the instantaneous inductor voltage

$$
v_L(t) = L\frac{\mathrm{d}i(t)}{\mathrm{d}t} = L\frac{\mathrm{d}}{\mathrm{d}t}\!\left[\sqrt{2}\,I\cos(\omega t + \phi)\right] = -\sqrt{2}\,\omega L I\sin(\omega t + \phi)
$$

The identity $-\sin(\theta) = \cos(\theta + \pi/2) = \cos(\theta + 90^\circ)$ puts this in cosine form:

$$
v_L(t) = \sqrt{2}\,(\omega L I)\cos\!\left(\omega t + \phi + \frac{\pi}{2}\right)
$$

The RMS inductor voltage is $V_L = \omega L I$ and its phase is $\phi + \pi/2$, so its phasor is

$$
\mathbf{V}_L = \omega L I e^{j(\phi + \pi/2)} = \omega L I\angle\!\left(\phi + \frac{\pi}{2}\right)
$$

Dividing by $\mathbf{I} = I e^{j\phi}$, with Euler's formula giving $e^{j\pi/2} = \cos(\pi/2) + j\sin(\pi/2) = 0 + j(1) = j$, gives the **impedance of an inductor**:

$$
Z_L = \frac{\mathbf{V}_L}{\mathbf{I}} = \omega L e^{j\pi/2} = \omega L\left(\cos\frac{\pi}{2} + j\sin\frac{\pi}{2}\right) = j\omega L = jX_L = \omega L\angle 90^\circ\ \Omega
$$

The positive real quantity $X_L$ is the **inductive reactance**, in ohms, which measures the opposition of the inductance to alternating current:

$$
X_L = \frac{V_L}{I_L} = \omega L = 2\pi f L\ \Omega
$$

Because $Z_L = X_L\angle(+90^\circ)$, multiplying $\mathbf{I}_L$ by $Z_L$ adds $90^\circ$ to the phase angle. In an inductor the current $\mathbf{I}_L$ lags the voltage $\mathbf{V}_L$ by $90^\circ$ ($\pi/2\ \text{rad}$); equivalently, the voltage leads the current by $90^\circ$.

### Capacitor and capacitive reactance

Let the current $i(t) = \sqrt{2}\,I\cos(\omega t + \phi)$ flow into an ideal capacitor $C$. Integrating $i(t) = C\,\mathrm{d}v_C/\mathrm{d}t$ in steady state gives the capacitor voltage

$$
v_C(t) = \frac{1}{C}\int i(t)\,\mathrm{d}t = \frac{1}{C}\int \sqrt{2}\,I\cos(\omega t + \phi)\,\mathrm{d}t = \sqrt{2}\,\frac{I}{\omega C}\sin(\omega t + \phi)
$$

The identity $\sin(\theta) = \cos(\theta - \pi/2) = \cos(\theta - 90^\circ)$ puts this in cosine form:

$$
v_C(t) = \sqrt{2}\,\left(\frac{I}{\omega C}\right)\cos\!\left(\omega t + \phi - \frac{\pi}{2}\right)
$$

The RMS capacitor voltage is $V_C = \dfrac{I}{\omega C}$ and its phase is $\phi - \pi/2$, so its phasor is

$$
\mathbf{V}_C = \frac{I}{\omega C}e^{j(\phi - \pi/2)} = \frac{I}{\omega C}\angle\!\left(\phi - \frac{\pi}{2}\right)
$$

Dividing by $\mathbf{I} = I e^{j\phi}$, with $e^{-j\pi/2} = \cos(-\pi/2) + j\sin(-\pi/2) = 0 - j(1) = -j = \dfrac{1}{j}$, gives the **impedance of a capacitor**:

$$
Z_C = \frac{\mathbf{V}_C}{\mathbf{I}} = \frac{1}{\omega C}e^{-j\pi/2} = \frac{1}{\omega C}\left[\cos\!\left(-\frac{\pi}{2}\right) + j\sin\!\left(-\frac{\pi}{2}\right)\right] = -j\frac{1}{\omega C} = \frac{1}{j\omega C} = -jX_C = X_C\angle(-90^\circ)\ \Omega
$$

The positive real magnitude $X_C$ is the **capacitive reactance**, in ohms:

$$
X_C = \frac{V_C}{I_C} = \frac{1}{\omega C} = \frac{1}{2\pi f C}\ \Omega
$$

$X_C = 1/(\omega C) > 0$ is defined as a positive number, and the minus sign is written explicitly in $Z_C = -jX_C$. Because $Z_C = X_C\angle(-90^\circ)$, in a capacitor the current $\mathbf{I}_C$ leads the voltage $\mathbf{V}_C$ by $90^\circ$ ($\pi/2\ \text{rad}$).

The three results at angular frequency $\omega = 2\pi f$ are collected below.

| Element | Reactance $X$ $[\Omega]$ | Complex impedance $Z$ $[\Omega]$ | Polar form | Phase of $\mathbf{I}$ relative to $\mathbf{V}$ |
|---|---|---|---|---|
| Resistor $R$ | $0$ | $Z_R = R$ | $R\angle 0^\circ$ | In phase ($\theta_v - \theta_i = 0^\circ$) |
| Inductor $L$ | $X_L = \omega L$ | $Z_L = j\omega L = jX_L$ | $X_L\angle(+90^\circ)$ | $\mathbf{I}$ lags $\mathbf{V}$ by $90^\circ$ |
| Capacitor $C$ | $X_C = \dfrac{1}{\omega C}$ | $Z_C = \dfrac{1}{j\omega C} = -jX_C$ | $X_C\angle(-90^\circ)$ | $\mathbf{I}$ leads $\mathbf{V}$ by $90^\circ$ |

> [!tip] CIVIL
> The word CIVIL holds both reactive phase relations. In a capacitor (C), I leads V, giving C-I-V; in an inductor (L), V leads I, giving V-I-L.

![[ee_d2_rlc_phase.png|900]]

### Behaviour at low and high frequencies

The two reactances at the ends of the frequency range give the behaviour of any $RLC$ or filter network before any equation is written. At DC and very low frequencies ($\omega \to 0$), $X_L = \omega L \to 0$, so $Z_L \to 0\ \Omega$ and an inductor behaves as a **short circuit**, a plain piece of wire offering no opposition to steady current. At the same time $X_C = \dfrac{1}{\omega C} \to \infty$, so $|Z_C| \to \infty$ and a capacitor behaves as an **open circuit**, an insulating gap that blocks DC current.

At very high frequencies ($\omega \to \infty$) the roles swap. $X_L = \omega L \to \infty$, so $|Z_L| \to \infty$ and an inductor behaves as an open circuit, because the rapidly alternating flux induces a large opposing back EMF $L\,\mathrm{d}i/\mathrm{d}t$. $X_C = \dfrac{1}{\omega C} \to 0$, so $Z_C \to 0\ \Omega$ and a capacitor behaves as a short circuit: charge flows onto and off the plates so quickly that no voltage builds up across them.

![[ee_d2_reactance_frequency.png|900]]

## 3. Series, parallel and divider networks

### Series impedances, the voltage triangle and resonance

When impedances $Z_1, Z_2, \dots, Z_n$ are in series, the same phasor current $\mathbf{I}$ flows through each. KVL in phasor form, $\mathbf{V} = \mathbf{V}_1 + \mathbf{V}_2 + \dots + \mathbf{V}_n$, makes the total impedance the complex sum

$$
Z_{\text{series}} = \frac{\mathbf{V}}{\mathbf{I}} = Z_1 + Z_2 + \dots + Z_n
$$

For $R$, $L$ and $C$ in series the impedances are $Z_R = R$, $Z_L = jX_L = j\omega L$ and $Z_C = -jX_C = -j/(\omega C)$. Adding real and imaginary parts gives the **series $RLC$ impedance**

$$
Z = R + jX_L - jX_C = R + j(X_L - X_C) = R + j\left(\omega L - \frac{1}{\omega C}\right)
$$

In polar form $Z = |Z|\angle\theta_Z$, with magnitude and phase

$$
|Z| = \sqrt{R^2 + (X_L - X_C)^2} = \sqrt{R^2 + \left(\omega L - \frac{1}{\omega C}\right)^2}, \qquad \theta_Z = \arctan\!\left(\frac{X_L - X_C}{R}\right)
$$

Multiplying each impedance by the common current gives the element voltages: $\mathbf{V}_R = R\mathbf{I}$ in phase with $\mathbf{I}$, $\mathbf{V}_L = jX_L\mathbf{I}$ $90^\circ$ ahead of $\mathbf{I}$, and $\mathbf{V}_C = -jX_C\mathbf{I}$ $90^\circ$ behind $\mathbf{I}$. $\mathbf{V}_L$ and $\mathbf{V}_C$ point in opposite directions along the imaginary axis ($180^\circ$ apart) and both are perpendicular to $\mathbf{V}_R$, so the RMS magnitudes obey the Pythagorean **voltage triangle**

$$
V = |\mathbf{V}| = \sqrt{V_R^2 + (V_L - V_C)^2}
$$

The reactances cancel at the **series resonant angular frequency** $\omega_0$, where $X_L = X_C$:

$$
\omega_0 L = \frac{1}{\omega_0 C} \implies \omega_0 = \frac{1}{\sqrt{LC}}, \qquad f_0 = \frac{1}{2\pi\sqrt{LC}}
$$

There $Z(\omega_0) = R$, the minimum possible impedance, so the current $I = V/|Z|$ is large at or near $\omega_0$.

> [!warning] RMS voltages across reactive elements do not add
> In a series $RC$, $RL$ or $RLC$ circuit, $V_R + V_L + V_C \ne V$; only the complex phasors add, $\mathbf{V}_R + \mathbf{V}_L + \mathbf{V}_C = \mathbf{V}$. Near resonance the individual RMS voltages $V_L = I X_L$ and $V_C = I X_C$ can each be much larger than the supply voltage $V$, because their $+jV_L$ and $-jV_C$ phasors cancel around the loop.

![[ee_d2_rlc_example.png|900]]

### Parallel impedances and complex dividers

When impedances $Z_1, Z_2, \dots, Z_n$ are connected in parallel across a common voltage phasor $\mathbf{V}$, KCL ($\mathbf{I} = \mathbf{I}_1 + \mathbf{I}_2 + \dots + \mathbf{I}_n$) shows that their reciprocals, the complex admittances $Y_k = 1/Z_k$, add:

$$
\frac{1}{Z_{\text{parallel}}} = \frac{1}{Z_1} + \frac{1}{Z_2} + \dots + \frac{1}{Z_n}
$$

For two branches the product-over-sum formula holds over the complex numbers:

$$
Z_{\text{parallel}} = Z_1 \parallel Z_2 = \frac{Z_1 Z_2}{Z_1 + Z_2}
$$

By hand, compute the denominator $Z_1 + Z_2$ in Cartesian form, convert the two numerator factors and the summed denominator to polar form, then multiply and divide the magnitudes and add and subtract the angles.

The two divider rules from [[FEEG1004 A3 - DC Circuit Laws - Ohm, KCL, KVL and Dividers]] carry over with complex impedances. For series impedances $Z_1$ and $Z_2$ across $\mathbf{V}_{\text{in}}$, the **complex potential divider** gives the voltage phasor across $Z_2$ as

$$
\mathbf{V}_2 = \frac{Z_2}{Z_1 + Z_2}\mathbf{V}_{\text{in}}
$$

For parallel impedances $Z_1$ and $Z_2$ fed by a total current phasor $\mathbf{I}_{\text{in}}$, the **complex current divider** puts the opposite branch's impedance in the numerator:

$$
\mathbf{I}_1 = \frac{Z_2}{Z_1 + Z_2}\mathbf{I}_{\text{in}}, \qquad \mathbf{I}_2 = \frac{Z_1}{Z_1 + Z_2}\mathbf{I}_{\text{in}}
$$

The remaining DC methods (KCL, KVL, mesh analysis, nodal analysis, superposition and Thévenin's theorem) carry over in the same way, with every resistance replaced by an impedance and every real number by a complex one.

## 4. Impedance triangles and inductive and capacitive loads

Any two-terminal passive AC network, however many resistors, inductors and capacitors it contains in series or parallel, reduces at a single frequency $\omega$ to one equivalent complex impedance

$$
Z = R + jX = |Z|\angle\theta_Z
$$

where $R = \Re(Z) \ge 0$ is the equivalent series **resistance** and $X = \Im(Z) = X_L - X_C$ is the net **reactance**. Drawing $R$ along the real axis, $jX$ vertically and $Z$ as the hypotenuse gives the right-angled **impedance triangle**, which is the circuit's voltage triangle scaled down by $\mathbf{I}$:

$$
|Z| = \sqrt{R^2 + X^2}, \qquad \theta_Z = \arctan\!\left(\frac{X}{R}\right), \qquad R = |Z|\cos\theta_Z, \qquad X = |Z|\sin\theta_Z
$$

The sign of $X$ puts every reactive load into one of two types. An **inductive load** has $X = \Im(Z) > 0$, so $Z = R + jX$ with $\theta_Z > 0$ and the impedance triangle points up into Quadrant I. Driven by $\mathbf{V} = V\angle\theta_v$, it draws $\mathbf{I} = \dfrac{\mathbf{V}}{Z} = \dfrac{V}{|Z|}\angle(\theta_v - \theta_Z)$, so the current lags the voltage by $\theta_Z \in (0^\circ, 90^\circ]$. Industrial AC motors, transformers, induction furnaces and solenoids are all inductive loads. A circuit containing a capacitor is still an inductive load if $X_L > X_C$: for example, $Z = 1 + j5 - j2 = (1 + j3)\ \Omega = 3.16\angle 71.6^\circ\ \Omega$ draws $\mathbf{I} = 10/(1+j3) = 3.16\angle(-71.6^\circ)\ \text{A}$ from a $10\angle 0^\circ\ \text{V}$ supply.

A **capacitive load** has $X = \Im(Z) < 0$, so $Z = R - j|X|$ with $\theta_Z < 0$ and the triangle points down into Quadrant IV. Driven by $\mathbf{V} = V\angle\theta_v$, it draws $\mathbf{I} = \dfrac{\mathbf{V}}{Z} = \dfrac{V}{|Z|}\angle(\theta_v + |\theta_Z|)$, so the current leads the voltage by $|\theta_Z| \in (0^\circ, 90^\circ]$. A circuit containing an inductor is still a capacitive load at frequencies where $X_C > X_L$: for example, $Z = 2 + j1 - j6 = (2 - j5)\ \Omega = 5.39\angle(-68.2^\circ)\ \Omega$ draws $\mathbf{I} = 10/(2-j5) = 1.86\angle(+68.2^\circ)\ \text{A}$ from a $10\angle 0^\circ\ \text{V}$ supply.

![[ee_d2_impedance_triangles.png|900]]

## Worked examples

### Single elements and a series RC circuit

(a) A $60\ \Omega$ resistive heater is connected across a $240\ \text{V}$ AC supply; find the complex current $\mathbf{I}_R$ and the heating power $P$. (b) An inductor $L = 2.2\ \text{H}$ is connected across $v(t) = 325\cos(314t - 30^\circ)\ \text{V}$; find its inductive reactance $X_L$, impedance $Z_L$ and RMS current phasor $\mathbf{I}_L$. (c) A capacitor $C = 200\ \mu\text{F}$ is connected across $v(t) = 325\cos(314t - 20^\circ)\ \text{V}$; find $X_C$, $Z_C$ and $\mathbf{I}_C$.

Then a resistor $R = 10\ \Omega$ is connected in series with a capacitor $C = 100\ \mu\text{F}$ across $v(t) = 100\sqrt{2}\cos(314t)\ \text{V}$. Find the total impedance $Z$, the RMS current phasor $\mathbf{I}$, the peak current $I_p$, the voltage phasors $\mathbf{V}_R$ and $\mathbf{V}_C$ (from Ohm's law and from the complex potential divider), and the waveforms $v_R(t)$ and $v_C(t)$.

(a) An unqualified "$240\ \text{V}$ AC supply" means the RMS voltage $V = 240\ \text{V}$ at reference phase $0^\circ$, so $\mathbf{V} = 240\angle 0^\circ\ \text{V}$, corresponding to $v(t) = 240\sqrt{2}\cos(\omega t)\ \text{V}$. With $Z_R = 60\angle 0^\circ\ \Omega$,

$$
\mathbf{I}_R = \frac{\mathbf{V}}{Z_R} = \frac{240\angle 0^\circ\ \text{V}}{60\angle 0^\circ\ \Omega} = 4.00\angle 0^\circ\ \text{A}, \qquad P = I_R^2 R = (4.00\ \text{A})^2(60\ \Omega) = 960\ \text{W}
$$

(b) Here $\omega = 314\ \text{rad}\,\text{s}^{-1}$ ($f \approx 50\ \text{Hz}$) and the peak voltage is $V_p = 325\ \text{V}$, so the RMS supply phasor is

$$
\mathbf{V}_L = \frac{325}{\sqrt{2}}\angle(-30^\circ) = 229.8\angle(-30^\circ)\ \text{V} \quad (\approx 230\angle(-30^\circ)\ \text{V})
$$

The inductive reactance and impedance are

$$
X_L = \omega L = (314\ \text{rad}\,\text{s}^{-1})(2.2\ \text{H}) = 690.8\ \Omega \implies Z_L = j690.8\ \Omega = 690.8\angle 90^\circ\ \Omega
$$

and generalised Ohm's law gives the inductor current phasor

$$
\mathbf{I}_L = \frac{\mathbf{V}_L}{Z_L} = \frac{229.8\angle(-30^\circ)\ \text{V}}{690.8\angle 90^\circ\ \Omega} = 0.333\angle(-120^\circ)\ \text{A}
$$

The current lags the voltage by $90^\circ$: $-30^\circ - 90^\circ = -120^\circ$.

(c) The RMS voltage phasor is $\mathbf{V}_C = \dfrac{325}{\sqrt{2}}\angle(-20^\circ) = 229.8\angle(-20^\circ)\ \text{V}$. At $\omega = 314\ \text{rad}\,\text{s}^{-1}$ and $C = 200 \times 10^{-6}\ \text{F}$, the capacitive reactance and impedance are

$$
X_C = \frac{1}{\omega C} = \frac{1}{314 \times 200 \times 10^{-6}} = \frac{1}{0.06280} = 15.92\ \Omega \implies Z_C = -j15.92\ \Omega = 15.92\angle(-90^\circ)\ \Omega
$$

so the capacitor current phasor is

$$
\mathbf{I}_C = \frac{\mathbf{V}_C}{Z_C} = \frac{229.8\angle(-20^\circ)\ \text{V}}{15.92\angle(-90^\circ)\ \Omega} = 14.4\angle(+70^\circ)\ \text{A}
$$

The current leads the voltage by $90^\circ$: $-20^\circ - (-90^\circ) = +70^\circ$.

For the series $RC$ circuit, the supply phasor is $\mathbf{V} = 100\angle 0^\circ\ \text{V}$ at $\omega = 314\ \text{rad}\,\text{s}^{-1}$. The resistor and capacitor impedances are

$$
Z_R = 10.0\ \Omega = 10.0\angle 0^\circ\ \Omega
$$

$$
Z_C = \frac{1}{j\omega C} = \frac{1}{j(314\ \text{rad}\,\text{s}^{-1})(100 \times 10^{-6}\ \text{F})} = -j31.847\ \Omega = 31.847\angle(-90^\circ)\ \Omega
$$

In series they add to

$$
Z = Z_R + Z_C = (10.0 - j31.847)\ \Omega
$$

which lies in Quadrant IV. Its polar form is

$$
|Z| = \sqrt{(10.0)^2 + (-31.847)^2} = \sqrt{100 + 1014.24} = 33.38\ \Omega
$$

$$
\theta_Z = \arctan\!\left(\frac{-31.847}{10.0}\right) = -72.57^\circ \implies Z = 33.38\angle(-72.57^\circ)\ \Omega
$$

The RMS current phasor and the peak current $I_p = \sqrt{2}\,I$ are

$$
\mathbf{I} = \frac{\mathbf{V}}{Z} = \frac{100\angle 0^\circ\ \text{V}}{33.38\angle(-72.57^\circ)\ \Omega} = 2.996\angle 72.57^\circ\ \text{A} \quad (\approx 3.00\angle 72.57^\circ\ \text{A})
$$

$$
I_p = \sqrt{2}\,|\mathbf{I}| = \sqrt{2}(2.996\ \text{A}) = 4.24\ \text{A}
$$

Ohm's law gives the element voltage phasors:

$$
\mathbf{V}_R = \mathbf{I} Z_R = (2.996\angle 72.57^\circ\ \text{A})(10.0\angle 0^\circ\ \Omega) = 29.96\angle 72.57^\circ\ \text{V} \quad (\approx 30.0\angle 72.6^\circ\ \text{V})
$$

$$
\mathbf{V}_C = \mathbf{I} Z_C = (2.996\angle 72.57^\circ\ \text{A})(31.847\angle(-90^\circ)\ \Omega) = 95.41\angle(-17.43^\circ)\ \text{V} \quad (\approx 95.4\angle(-17.4^\circ)\ \text{V})
$$

In the time domain these are

$$
v_R(t) = 30.0\sqrt{2}\cos(314t + 72.6^\circ)\ \text{V}, \qquad v_C(t) = 95.4\sqrt{2}\cos(314t - 17.4^\circ)\ \text{V}
$$

> [!check] Voltage triangle and potential divider
> The scalar magnitudes sum to $29.96 + 95.41 = 125.37\ \text{V} \ne 100\ \text{V}$, but $\mathbf{V}_R$ and $\mathbf{V}_C$ are perpendicular ($72.57^\circ - (-17.43^\circ) = 90.00^\circ$), so their quadrature sum is the supply voltage:
> $$V = \sqrt{V_R^2 + V_C^2} = \sqrt{(29.9578)^2 + (95.4072)^2} = \sqrt{897.47 + 9102.53} = \sqrt{10\,000} = 100.0\ \text{V}\ \checkmark$$
> The complex potential divider gives the same capacitor voltage:
> $$\mathbf{V}_C = \frac{Z_C}{Z_R + Z_C}\mathbf{V} = \frac{31.847\angle(-90^\circ)}{33.380\angle(-72.568^\circ)}\times 100\angle 0^\circ = 95.41\angle(-17.43^\circ)\ \text{V}\ \checkmark$$

### Series RLC circuit near resonance

A series $RLC$ circuit with $R = 3.6\ \Omega$, $L = 1.2\ \text{mH}$ and $C = 0.04\ \text{mF}$ ($40\ \mu\text{F}$) is driven by $v(t) = 140\sqrt{2}\cos(4000t - 10^\circ)\ \text{V}$. Find the total impedance $Z$, the current phasor $\mathbf{I}$, the element voltage phasors $\mathbf{V}_R, \mathbf{V}_L, \mathbf{V}_C$, their time-domain waveforms, and the resonant angular frequency $\omega_0$. Then, for Tutorial Sheet 7 Q3, a resistor $R = 200\ \Omega$, an inductor $L = 150\ \text{mH}$ and a capacitor $C = 2.0\ \mu\text{F}$ are in series at $f = 400\ \text{Hz}$: find $Z$ in Cartesian and polar form, state whether the circuit is inductive or capacitive at $400\ \text{Hz}$, and find its resonant frequency $f_0$.

At $\omega = 4000\ \text{rad}\,\text{s}^{-1}$ the source phasor is $\mathbf{V} = 140\angle(-10^\circ)\ \text{V}$, and the element impedances are

$$
Z_R = R = 3.60\ \Omega
$$

$$
X_L = \omega L = (4000\ \text{rad}\,\text{s}^{-1})(1.2 \times 10^{-3}\ \text{H}) = 4.80\ \Omega \implies Z_L = j4.80\ \Omega = 4.80\angle 90^\circ\ \Omega
$$

$$
X_C = \frac{1}{\omega C} = \frac{1}{(4000\ \text{rad}\,\text{s}^{-1})(0.04 \times 10^{-3}\ \text{F})} = \frac{1}{0.160} = 6.25\ \Omega \implies Z_C = -j6.25\ \Omega = 6.25\angle(-90^\circ)\ \Omega
$$

In series they add to

$$
Z = Z_R + Z_L + Z_C = 3.60 + j4.80 - j6.25 = (3.60 - j1.45)\ \Omega
$$

Since $\Im(Z) = -1.45\ \Omega < 0$, the circuit is capacitive at $\omega = 4000\ \text{rad}\,\text{s}^{-1}$, just below its resonant angular frequency $\omega_0 = \dfrac{1}{\sqrt{LC}} = \dfrac{1}{\sqrt{1.2 \times 10^{-3} \times 0.04 \times 10^{-3}}} = 4564\ \text{rad}\,\text{s}^{-1}$. In polar form,

$$
|Z| = \sqrt{(3.60)^2 + (-1.45)^2} = \sqrt{12.96 + 2.1025} = \sqrt{15.0625} = 3.881\ \Omega
$$

$$
\theta_Z = \arctan\!\left(\frac{-1.45}{3.60}\right) = -21.94^\circ \implies Z = 3.88\angle(-21.9^\circ)\ \Omega
$$

Dividing $\mathbf{V}$ by $Z$ gives the current phasor:

$$
\mathbf{I} = \frac{\mathbf{V}}{Z} = \frac{140\angle(-10^\circ)\ \text{V}}{3.881\angle(-21.94^\circ)\ \Omega} = 36.07\angle(+11.94^\circ)\ \text{A} \quad (\approx 36.1\angle 11.9^\circ\ \text{A})
$$

Multiplying $\mathbf{I}$ by each element's impedance gives the three voltage phasors:

$$
\mathbf{V}_R = \mathbf{I} Z_R = (36.07\angle 11.94^\circ\ \text{A})(3.60\angle 0^\circ\ \Omega) = 129.9\angle 11.9^\circ\ \text{V} \quad (\approx 130\angle 11.9^\circ\ \text{V})
$$

$$
\mathbf{V}_L = \mathbf{I} Z_L = (36.07\angle 11.94^\circ\ \text{A})(4.80\angle 90^\circ\ \Omega) = 173.1\angle 101.9^\circ\ \text{V} \quad (\approx 173\angle 102^\circ\ \text{V})
$$

$$
\mathbf{V}_C = \mathbf{I} Z_C = (36.07\angle 11.94^\circ\ \text{A})(6.25\angle(-90^\circ)\ \Omega) = 225.5\angle(-78.1^\circ)\ \text{V} \quad (\approx 225\angle(-78.1^\circ)\ \text{V})
$$

In the time domain,

$$
\begin{aligned}
i(t) &= 36.1\sqrt{2}\cos(4000t + 11.9^\circ)\ \text{A} \\
v_R(t) &= 130\sqrt{2}\cos(4000t + 11.9^\circ)\ \text{V} \\
v_L(t) &= 173\sqrt{2}\cos(4000t + 102^\circ)\ \text{V} \\
v_C(t) &= 225\sqrt{2}\cos(4000t - 78.1^\circ)\ \text{V}
\end{aligned}
$$

> [!check] KVL closes despite the magnified element voltages
> Both $|\mathbf{V}_L| = 173.1\ \text{V}$ and $|\mathbf{V}_C| = 225.5\ \text{V}$ exceed the $140\ \text{V}$ supply, because $\omega = 4000\ \text{rad}\,\text{s}^{-1}$ is close to $\omega_0 = 4564\ \text{rad}\,\text{s}^{-1}$. In Cartesian form (Python `cmath`):
> $$\begin{aligned} \mathbf{V}_R &= 127.05 + j26.86\ \text{V} \\ \mathbf{V}_L &= -35.82 + j169.40\ \text{V} \\ \mathbf{V}_C &= +46.64 - j220.58\ \text{V} \end{aligned}$$
> Their sum is $\mathbf{V}_R + \mathbf{V}_L + \mathbf{V}_C = (127.05 - 35.82 + 46.64) + j(26.86 + 169.40 - 220.58) = 137.87 - j24.32\ \text{V} \approx 140.0\angle(-10.0^\circ)\ \text{V} = \mathbf{V}\ \checkmark$.

For the Tutorial Sheet 7 Q3 circuit at $f = 400\ \text{Hz}$, the angular frequency is $\omega = 2\pi f = 800\pi = 2513.3\ \text{rad}\,\text{s}^{-1}$ and the reactances are

$$
X_L = \omega L = (2513.3\ \text{rad}\,\text{s}^{-1})(0.150\ \text{H}) = 377.0\ \Omega
$$

$$
X_C = \frac{1}{\omega C} = \frac{1}{(2513.3\ \text{rad}\,\text{s}^{-1})(2.0 \times 10^{-6}\ \text{F})} = 198.9\ \Omega
$$

The total series impedance is

$$
Z = R + j(X_L - X_C) = 200 + j(377.0 - 198.9) = (200 + j178)\ \Omega
$$

with $|Z| = \sqrt{200^2 + 178.05^2} = 267.8\ \Omega$ and $\theta_Z = \arctan(178.05/200) = +41.68^\circ$, so

$$
Z = 268\angle 41.7^\circ\ \Omega
$$

Since $\Im(Z) = +178\ \Omega > 0$, the circuit is inductive at $400\ \text{Hz}$, above its resonant frequency $f_0 = \dfrac{1}{2\pi\sqrt{0.150 \times 2.0 \times 10^{-6}}} = 290.6\ \text{Hz}$.

### Series-parallel reduction and cascaded voltage dividers

A voltage source $\mathbf{V} = 100\angle 20^\circ\ \text{V}$ feeds a series resistor $R_1 = 10\ \Omega$ connected to a parallel combination of an inductor branch $Z_L = j20\ \Omega$ and a series resistor–capacitor branch $Z_{RC} = (15 - j30)\ \Omega$. With $\mathbf{V}_1$ the voltage across the parallel combination and $\mathbf{V}_2$ the voltage across the $-j30\ \Omega$ capacitor, find (a) the parallel impedance $Z_x$ and the total impedance $Z$, (b) the source current phasor $\mathbf{I}$, and (c) $\mathbf{V}_1$ and $\mathbf{V}_2$ by applying the complex potential divider twice.

(a) For the product in the parallel formula, $Z_{RC}$ and $Z_L = j20\ \Omega$ go into polar form:

$$
Z_{RC} = 15 - j30 = \sqrt{15^2 + (-30)^2}\,\angle\!\left(\arctan\frac{-30}{15}\right) = 33.54\angle(-63.43^\circ)\ \Omega, \qquad Z_L = 20\angle 90^\circ\ \Omega
$$

The denominator is the Cartesian sum

$$
Z_L + Z_{RC} = j20 + (15 - j30) = (15 - j10)\ \Omega = \sqrt{15^2 + (-10)^2}\,\angle\!\left(\arctan\frac{-10}{15}\right) = 18.03\angle(-33.69^\circ)\ \Omega
$$

so the parallel impedance $Z_x = Z_L \parallel Z_{RC}$ is

$$
Z_x = \frac{Z_L Z_{RC}}{Z_L + Z_{RC}} = \frac{(20\angle 90^\circ)(33.54\angle(-63.43^\circ))}{18.03\angle(-33.69^\circ)} = \frac{670.8\angle 26.57^\circ}{18.03\angle(-33.69^\circ)} = 37.21\angle 60.26^\circ\ \Omega
$$

Back in Cartesian form, ready to add the series resistor $R_1 = 10\ \Omega$:

$$
Z_x = 37.21\cos(60.26^\circ) + j\,37.21\sin(60.26^\circ) = (18.46 + j32.31)\ \Omega
$$

Adding $R_1$ gives the total input impedance:

$$
Z = R_1 + Z_x = 10 + (18.46 + j32.31) = (28.46 + j32.31)\ \Omega = 43.06\angle 48.62^\circ\ \Omega
$$

Since $\Im(Z) = +32.31\ \Omega > 0$, the circuit as a whole is inductive.

(b) Generalised Ohm's law gives the source current:

$$
\mathbf{I} = \frac{\mathbf{V}}{Z} = \frac{100\angle 20^\circ\ \text{V}}{43.06\angle 48.62^\circ\ \Omega} = 2.32\angle(-28.6^\circ)\ \text{A}
$$

(c) The potential divider between $R_1 = 10\ \Omega$ and the parallel block $Z_x$ gives $\mathbf{V}_1$:

$$
\mathbf{V}_1 = \frac{Z_x}{Z}\mathbf{V} = \frac{37.21\angle 60.26^\circ\ \Omega}{43.06\angle 48.62^\circ\ \Omega}\times 100\angle 20^\circ\ \text{V} = \frac{3721\angle 80.26^\circ}{43.06\angle 48.62^\circ} = 86.4\angle 31.6^\circ\ \text{V}
$$

$\mathbf{V}_1$ lies across the series $RC$ branch $Z_{RC} = 15 - j30\ \Omega$, so a second divider between $15\ \Omega$ and $-j30\ \Omega = 30\angle(-90^\circ)\ \Omega$ gives the capacitor voltage:

$$
\mathbf{V}_2 = \frac{-j30}{15 - j30}\mathbf{V}_1 = \frac{30\angle(-90^\circ)\ \Omega}{33.54\angle(-63.43^\circ)\ \Omega}\times 86.42\angle 31.63^\circ\ \text{V} = \frac{2593\angle(-58.37^\circ)}{33.54\angle(-63.43^\circ)} = 77.3\angle 5.07^\circ\ \text{V}
$$

> [!check] KCL at the parallel node
> With $\mathbf{V}_1 = 86.42\angle 31.63^\circ\ \text{V}$, the inductor branch carries $\mathbf{I}_L = \mathbf{V}_1 / (j20) = 4.321\angle(-58.37^\circ)\ \text{A} = (2.266 - j3.679)\ \text{A}$ and the $15 - j30\ \Omega$ branch carries $\mathbf{I}_{RC} = \mathbf{V}_1 / (15 - j30) = 2.576\angle 95.07^\circ\ \text{A} = (-0.228 + j2.566)\ \text{A}$. Their sum is the source current:
> $$\mathbf{I}_L + \mathbf{I}_{RC} = (2.266 - 0.228) + j(-3.679 + 2.566) = (2.038 - j1.113)\ \text{A} = 2.322\angle(-28.62^\circ)\ \text{A} = \mathbf{I}\ \checkmark$$

### Terminal impedance and a two-stage current divider

Tutorial Sheet 7 Q4 asks for the impedance $Z_{AB}$ seen at terminals $A$ and $B$ of a network made of a $1\ \Omega$ resistor in series with the parallel combination of branch 1 ($0.2\ \Omega$ in series with $-j1\ \Omega$) and branch 2 ($0.5\ \Omega$ in series with $+j3\ \Omega$). In Q5, a current source $\mathbf{I}_s = 20\angle 45^\circ\ \text{A}$ feeds a $2\ \Omega$ shunt resistor in parallel with a series inductor $j3\ \Omega$ carrying current $\mathbf{I}_1$; the inductor feeds a parallel pair of a $4\ \Omega$ resistor (carrying $\mathbf{I}_2$) and a $-j15\ \Omega$ capacitor. Find $\mathbf{I}_1$ and $\mathbf{I}_2$.

(Q4) The two parallel branches are $Z_1 = (0.2 - j1)\ \Omega$ and $Z_2 = (0.5 + j3)\ \Omega$, and the $1\ \Omega$ resistor is in series with $Z_1 \parallel Z_2$:

$$
Z_{AB} = 1 + \frac{(0.2 - j1)(0.5 + j3)}{(0.2 - j1) + (0.5 + j3)}
$$

The numerator expands to $(0.2)(0.5) + j(0.2)(3) - j(1)(0.5) - j^2(1)(3) = (0.1 + 3.0) + j(0.6 - 0.5) = 3.1 + j0.1$ and the denominator is $0.7 + j2.0$:

$$
Z_{AB} = 1 + \frac{3.1 + j0.1}{0.7 + j2.0}
$$

Multiplying top and bottom by the conjugate $(0.7 - j2.0)$, with $0.7^2 + 2.0^2 = 4.49$, rationalises the fraction:

$$
Z_{AB} = 1 + \frac{(3.1 + j0.1)(0.7 - j2.0)}{4.49} = 1 + \frac{2.37 - j6.13}{4.49} = 1 + (0.5278 - j1.3653) = (1.53 - j1.37)\ \Omega
$$

In polar form $Z_{AB} = 2.05\angle(-41.8^\circ)\ \Omega$, which is capacitive since $\Im(Z_{AB}) < 0$.

(Q5) The impedance $Z_r$ to the right of the $2\ \Omega$ shunt is the inductor $j3\ \Omega$ in series with the parallel pair of $4\ \Omega$ and $-j15\ \Omega$:

$$
Z_r = j3 + \frac{4(-j15)}{4 - j15} = j3 + \frac{-j60}{4 - j15}\times\frac{4 + j15}{4 + j15}
$$

Since $4^2 + (-15)^2 = 16 + 225 = 241$ and $(-j60)(4 + j15) = 900 - j240$,

$$
Z_r = j3 + \frac{900 - j240}{241} = j3 + (3.734 - j0.996) = (3.73 + j2.00)\ \Omega = 4.24\angle 28.2^\circ\ \Omega
$$

The first current divider, between the $2\ \Omega$ shunt and $Z_r$, puts the opposite branch ($2\ \Omega$) in the numerator for the current $\mathbf{I}_1$ entering $Z_r$:

$$
\mathbf{I}_1 = \frac{2}{2 + Z_r}\,\mathbf{I}_s = \frac{2}{2 + 3.734 + j2.004}\times 20\angle 45^\circ\ \text{A} = \frac{40\angle 45^\circ}{5.734 + j2.004}
$$

With $5.734 + j2.004 = 6.074\angle 19.26^\circ\ \Omega$,

$$
\mathbf{I}_1 = \frac{40\angle 45^\circ\ \text{A}}{6.074\angle 19.26^\circ} = 6.59\angle 25.7^\circ\ \text{A} = (5.93 + j2.86)\ \text{A}
$$

The second divider splits $\mathbf{I}_1$ between $4\ \Omega$ and $-j15\ \Omega$. The current $\mathbf{I}_2$ through the $4\ \Omega$ resistor has the opposite branch ($-j15\ \Omega = 15\angle(-90^\circ)\ \Omega$) in the numerator and $4 - j15 = 15.524\angle(-75.07^\circ)\ \Omega$ in the denominator:

$$
\mathbf{I}_2 = \frac{-j15}{4 - j15}\,\mathbf{I}_1 = \frac{15\angle(-90^\circ)}{15.524\angle(-75.07^\circ)}\times 6.585\angle 25.74^\circ\ \text{A} = 6.36\angle 10.8^\circ\ \text{A} = (6.25 + j1.19)\ \text{A}
$$

> [!check] KCL across the three parallel branches
> The $2\ \Omega$ shunt carries $\mathbf{I}_{2\Omega} = \mathbf{I}_s - \mathbf{I}_1 = (14.142 + j14.142) - (5.932 + j2.859) = (8.210 + j11.283)\ \text{A} = 13.95\angle 53.96^\circ\ \text{A}$, and the capacitor carries $\mathbf{I}_{-j15} = \dfrac{4}{4 - j15}\mathbf{I}_1 = (-0.318 + j1.666)\ \text{A} = 1.696\angle 100.8^\circ\ \text{A}$. The three return currents sum to the source current:
> $$\mathbf{I}_{2\Omega} + \mathbf{I}_2 + \mathbf{I}_{-j15} = (8.210 + 6.250 - 0.318) + j(11.283 + 1.193 + 1.666) = (14.142 + j14.142)\ \text{A} = 20.0\angle 45.0^\circ\ \text{A} = \mathbf{I}_s\ \checkmark$$

![[ee_t7_phasor_diagrams.png|900]]

## Links

- Parent: [[FEEG1004 Electronics Hub]]
- Previous: [[FEEG1004 D1 - AC Waveforms, RMS and Phasors]]
- Next: [[FEEG1004 D3 - AC Filters and Bode Plots]]
- Concepts: [[Complex Impedance]] · [[Phasor Representation]] · [[Current Divider]] · [[Potential Divider]]
- Tutorial solutions: [[FEEG1004 Tutorial 7 - Phasors and Complex Impedance Solutions]] (Q3, Q4, Q5)
- Evaluating $Z(s) = R + sL + 1/(sC)$ along $s = j\omega$ gives the AC impedance $Z(j\omega)$. Its reciprocal, the admittance $Y(j\omega) = 1/Z(j\omega)$, has a resonant peak that mirrors the mechanical receptance FRF in [[FEEG1002 D6 - Single Degree of Freedom Vibration]] (see also [[Transfer Function]] and [[Frequency Response Function]]).
- The displacement transducers in [[FEEG1004 E2 - Displacement Sensors - Potentiometric, Capacitive and Inductive]] have picofarad capacitances or microhenry inductances; a high excitation frequency $\omega$ brings $X_C = 1/(\omega C)$ down to a measurable kilohm range ([[Capacitive Displacement Sensor]]).
- Radio-frequency transmitters and antennas in [[SESA2024 09 - Communications]] use reactive $LC$ networks to match complex load impedances and prevent signal reflections.

## Sources

- `02 - Sources/S2 AC Analysis/S2-W22-23 AC Analysis 02 - Impedance and Phasor Analysis - Lecture Slides.pdf` (slides 1–20: $Z_R, Z_L, Z_C$ derivations, CIVIL rule, heater, inductor and capacitor examples on slides 12–15, series $RC$ voltage triangle and divider on slide 17, series $RLC$ example on slide 19)
- `02 - Sources/S2 AC Analysis/S2-W24 AC Analysis 03 - Filters and Loads - Lecture Slides.pdf` (slides 2, 14–17: low- and high-frequency impedance limits, inductive and capacitive loads, impedance triangles, $2.2\ \text{k}\Omega + 47\ \text{nF}$ frequency comparison)
- `02 - Sources/S2 AC Analysis/S2 AC Analysis Lecture Notes 2021 - Niu.pdf` (pp. 5–16: $RL$ differential equation to phasor proof, element impedances and the positive-$X_C$ convention with $Z_C = -jX_C$, phase diagrams, $RLC$ Example 1 on p. 13, graphical KVL cable example, series-parallel Fig. 24 example on pp. 15–16)
- `02 - Sources/S2 AC Analysis/S2 Complex Numbers for AC Analysis - Niu.pdf` (pp. 5–7: element impedances, series $LCR$ resonance at $\omega = 1/\sqrt{LC}$, $50\ \text{Hz}$ $LCR$ impedance exercise)
- `02 - Sources/Lectures/FEEG1004 Lecture 2025-03-11.txt` (ll. 43–91: recap of $Z_R, Z_L, Z_C$ and frequency limits), `02 - Sources/Lectures/FEEG1004 Lecture 2025-03-14.txt` (ll. 6–47: DC network theorems in AC circuits), and `02 - Sources/Lectures/FEEG1004 Lecture 2025-03-18.txt` (ll. 103–158: inductive and capacitive loads and impedance triangles)
- `02 - Sources/Tutorial Sheets/Tutorial Sheet 07 - AC Circuits 1 - Phasors & Complex Impedance.pdf` and `02 - Sources/Tutorial Sheets/Tutorial Sheet 07 - AC Circuits 1 - Phasors & Complex Impedance - Solutions.pdf` (Q3, Q4, Q5)
- Worked-example numbers and the Cartesian KVL check computed in Python (`cmath`).

## Self-study tasks

### Core

- [ ] Draw the phasor-domain circuit for $R = 200\ \Omega$, $L = 150\ \text{mH}$ and $C = 2\ \mu\text{F}$ in series at $400\ \text{Hz}$ and find the total impedance $Z$ in polar form (Tutorial Sheet 7 Q3). → [[#Series RLC circuit near resonance]]; [[FEEG1004 Tutorial 7 - Phasors and Complex Impedance Solutions#Q3: 200 Ω + 150 mH + 2 µF in series at 400 Hz|Tutorial 7 Q3]]
- [ ] Find the terminal impedance $Z_{AB}$ of Figure Q4 in Cartesian and polar form and say whether it is inductive or capacitive (Tutorial Sheet 7 Q4). → [[#Terminal impedance and a two-stage current divider]]; [[FEEG1004 Tutorial 7 - Phasors and Complex Impedance Solutions#Q4: Impedance seen at A–B|Tutorial 7 Q4]]
- [ ] Find the branch currents $\mathbf{I}_1$ and $\mathbf{I}_2$ in Figure Q5 when driven by the $20\angle 45^\circ\ \text{A}$ current source (Tutorial Sheet 7 Q5). → [[#Terminal impedance and a two-stage current divider]]; [[FEEG1004 Tutorial 7 - Phasors and Complex Impedance Solutions#Q5: Currents I_1 and I_2 from a 20∠45° A source|Tutorial 7 Q5]]

### Further practice

- [ ] Find the impedance, in Cartesian and polar form, of $R = 100\ \Omega$, $L = 572\ \text{mH}$ and $C = 40\ \mu\text{F}$ in series at $f = 50\ \text{Hz}$, and check $X_L = 179.7\ \Omega$, $X_C = 79.58\ \Omega$ and $Z = (100 + j100.1)\ \Omega = 141.5\angle 45.0^\circ\ \Omega$ (Niu, Complex Numbers for AC Analysis, p. 7). → [[#Series impedances, the voltage triangle and resonance]]
- [ ] For $R = 2.2\ \text{k}\Omega$ in series with $C = 47\ \text{nF}$, compute $X_C$ and $|Z|$ at $f = 100\ \text{Hz}$ ($X_C = 33.86\ \text{k}\Omega$, $|Z| = 33.93\ \text{k}\Omega$, capacitor dominates) and at $f = 10\ \text{kHz}$ ($X_C = 338.6\ \Omega$, $|Z| = 2.226\ \text{k}\Omega$, resistor dominates) (AC Analysis 03 slide 17). → [[#Behaviour at low and high frequencies]]

## Transcript and slide slips

> [!warning] Slide 15 of AC Analysis 02 uses 240 V RMS for a 325 V peak
> Where: [[#Single elements and a series RC circuit]]
> On slide 15 of `S2-W22-23 AC Analysis 02 - Impedance and Phasor Analysis - Lecture Slides.pdf`, the supply across the $200\ \mu\text{F}$ capacitor is $v(t) = 325\cos(314t - 20^\circ)\ \text{V}$, but the solution writes its RMS phasor as $\mathbf{V}_C = 240\angle(-20^\circ)\ \text{V}$ instead of $325/\sqrt{2} = 229.8\ \text{V}$, obtaining $15.1\angle 70^\circ\ \text{A}$, rounded to $\mathbf{I}_C = 15\angle 70^\circ\ \text{A}$. Dividing the peak $325\ \text{V}$ by $\sqrt{2}$ gives $229.8\ \text{V} \approx 230\ \text{V}$ (as slide 12 does for $v(t) = 325\cos(314t - 30^\circ)\ \text{V}$), which yields $\mathbf{I}_C = 229.8\angle(-20^\circ) / 15.92\angle(-90^\circ) = 14.4\angle 70^\circ\ \text{A}$.

> [!warning] Slide 17 of AC Analysis 02 asks for the peak current but gives only the RMS current
> Where: [[#Single elements and a series RC circuit]]
> The problem on slide 17 of `S2-W22-23 AC Analysis 02 - Impedance and Phasor Analysis - Lecture Slides.pdf` asks to "Calculate the peak current flowing into the capacitor" for the $10\ \Omega + 100\ \mu\text{F}$ series circuit across $v(t) = 100\sqrt{2}\cos(314t)\ \text{V}$, but the slide solution stops at the RMS current phasor $\mathbf{I} = 3\angle 72.5676^\circ\ \text{A}$. The peak current is $I_p = \sqrt{2}\,I = 3.00\sqrt{2} = 4.24\ \text{A}$.

> [!warning] Slide 15 of AC Analysis 03 labels the 2 Ω resistor as 1 Ω
> Where: [[#4. Impedance triangles and inductive and capacitive loads]]
> On slide 15 of `S2-W24 AC Analysis 03 - Filters and Loads - Lecture Slides.pdf`, the capacitive load calculation writes $Z = 2 + j1 - j6 = 2 - j5\ \Omega$ and $\mathbf{I} = 10/(2 - j5) = 1.86\angle(+68.2^\circ)\ \text{A}$, but the schematic beside it labels the series resistor "$1\ \Omega$" (copied from the inductive load schematic on slide 14) instead of "$2\ \Omega$".
