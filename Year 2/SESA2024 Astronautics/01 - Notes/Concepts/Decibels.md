---
title: "Decibels"
module: "SESA2024 Astronautics"
type: concept
stream: "Spacecraft Subsystems"
aliases: ["dB", "dBW", "decibel-watt", "logarithmic ratio"]
tags: [sesa2024, concept, communications]
status: lectured
parent_lectures: ["[[SESA2024 09 - Communications]]"]
related_concepts: ["[[Link Budget Equation]]", "[[Antenna Gain and Beamwidth]]"]
sources: ["02 - Sources/Lectures/SESA2024 Lecture 2025-11-18.txt"]
---

# Decibels

A decibel expresses the ratio of two powers on a logarithmic scale: $x_{dB}=10\log_{10}(P/P_{ref})$; with $P_{ref}=1$ W the unit is the decibel-watt (dBW).

Communications quantities span many orders of magnitude, from kilowatts at the transmitter to around $10^{-17}$ W at a deep-space receiver, and the link budget multiplies and divides them. In decibels products become sums and quotients become differences, so the link budget becomes a column of additions. To convert back, $P=P_{ref}\times10^{x_{dB}/10}$; the lecture's practice example is $42.3\ \mathrm{dBW}=16.98$ kW. A gain of 1 is 0 dB, a factor of 2 is about 3 dB (which is why the half-power beamwidth is the "3 dB" beamwidth), and a factor of 10 is 10 dB. A quantity that enters squared, like the free-space loss $(4\pi\rho/\lambda)^2$, gets a factor of 20 instead of 10.

The commonest slip is to add a decibel quantity to a linear one, for example the data rate in bit/s to $E_b/N_0$ in dB; convert everything first.

## Related

- [[SESA2024 09 - Communications#1. Decibels|Decibels in the lecture note]]
- [[Link Budget Equation]] · [[Antenna Gain and Beamwidth]]
