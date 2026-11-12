---
title: "Complex Impedance"
module: "FEEG1004 Electronics"
type: concept
stream: "Part D: AC Circuit Analysis"
aliases: ["impedance", "reactance", "Z = R + jX", "generalised Ohm's law", "CIVIL", "inductive load", "capacitive load"]
tags: [feeg1004, concept, ac-circuits]
status: complete
parent_lectures: ["[[FEEG1004 D2 - Impedance and Phasor Circuit Analysis]]"]
related_concepts: ["[[Phasor Representation]]", "[[RC Low-Pass and High-Pass Filters]]"]
sources: ["02 - Sources/S2 AC Analysis/S2-W22-23 AC Analysis 02 - Impedance and Phasor Analysis - Lecture Slides.pdf", "02 - Sources/S2 AC Analysis/S2 AC Analysis Lecture Notes 2021 - Niu.pdf"]
---

# Complex Impedance

Complex impedance $Z$ is the ratio of voltage phasor to current phasor for a component or network in sinusoidal steady state, $\mathbf V=Z\mathbf I$. It generalises Ohm's law to AC, with the three basic elements giving

$$
Z=R+jX,\qquad Z_R=R,\qquad Z_L=j\omega L,\qquad Z_C=\frac{1}{j\omega C}=-\frac{j}{\omega C}.
$$

The real part is the **resistance** and the imaginary part is the **reactance**, the opposition to AC that comes from energy storage. In a capacitor the current leads the voltage by $90^\circ$, and in an inductor the voltage leads the current by $90^\circ$; the mnemonic CIVIL (C: I before V; V before I: L) holds both. A network with net $X>0$ is an inductive load, in which the current lags, and one with $X<0$ is a capacitive load, in which it leads. Only the net reactance decides which.

The frequency limits follow from $\omega L$ and $1/\omega C$. An inductor is a short circuit at DC and an open circuit at high frequency; a capacitor is open at DC and a short at high frequency. Series and parallel rules, dividers and every DC network theorem carry over unchanged, with complex arithmetic in place of real.

![[ee_d2_reactance_frequency.png|640]]

In Tutorial 7 Q3, $200\ \Omega$ in series with $150\ \mathrm{mH}$ and $2\ \mu\mathrm F$ at $400\ \mathrm{Hz}$ gives $268\angle41.7^\circ\ \Omega$. In Niu Ex. 1, $3.6+j4.8-j6.25=3.88\angle-21.9^\circ\ \Omega$.

## Related

- [[FEEG1004 D2 - Impedance and Phasor Circuit Analysis]]
- [[Capacitance]] · [[Inductance]] · [[Phasor Representation]] · [[RC Low-Pass and High-Pass Filters]]
- Year 2: [[Transfer Function]]
- Sources: AC Analysis 02–03 slides; Niu AC notes (Figs 11–19)
