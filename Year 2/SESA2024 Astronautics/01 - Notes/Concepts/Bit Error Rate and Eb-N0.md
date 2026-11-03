---
title: "Bit Error Rate and Eb-N0"
module: "SESA2024 Astronautics"
type: concept
stream: "Spacecraft Subsystems"
aliases: ["BER", "bit error rate", "Eb/N0", "energy per bit to noise density", "phase shift keying", "PSK", "noise temperature"]
tags: [sesa2024, concept, communications]
status: lectured
parent_lectures: ["[[SESA2024 09 - Communications]]"]
related_concepts: ["[[Link Budget Equation]]", "[[Payload Data Rate]]"]
sources: ["02 - Sources/Lectures/SESA2024 Lecture Chapter 9 - Communications - prerecord - week 8.txt", "02 - Sources/Lectures/SESA2024 Lecture 2025-11-18.txt"]
---

# Bit Error Rate and Eb-N0

The bit error rate (BER) is the probability that a received bit is wrong; for a given modulation it is fixed by $E_b/N_0$, the energy per bit divided by the noise power spectral density.

If bits arrive at rate $R_b$, each lasts $1/R_b$ and carries energy $E_b=C/R_b$, so

$$
\frac{C}{N_0}=\frac{E_b}{N_0}R_b.
$$

The noise density is $N_0=kT$, with $T$ the system's equivalent noise temperature. A designer picks an acceptable BER (often $10^{-6}$), reads the required $E_b/N_0$ from the modulation's curve (about 10 dB on the course's PSK curve), multiplies by the data rate to get the required $C/N_0$, and puts that into the link budget. For a fixed link, doubling the data rate halves the energy per bit and raises the BER, so data rate and link quality trade against each other.

Phase shift keying is the usual modulation because it keeps the carrier's power and frequency constant, unlike amplitude and frequency shift keying.

![[ast_ber_psk.png|540]]

## Related

- [[SESA2024 09 - Communications#7. From bit error rate to data rate|Bit error rate in the lecture note]]
- [[Link Budget Equation]] · [[Payload Data Rate]]
