---
title: "Bit Error Rate and Eb-N0"
module: "SESA2024 Astronautics"
type: concept
stream: "Spacecraft Subsystems"
aliases: ["BER", "Eb/N0", "energy per bit", "PSK", "ASK", "FSK", "PCM", "Shannon"]
tags: [sesa2024, concept, communications]
status: complete
parent_lectures: ["[[SESA2024 09 - Communications]]"]
related_concepts: ["[[Link Budget Equation]]", "[[Payload Data Rate]]"]
sources: ["02 - Sources/Lectures/Chapter 9/2025 Chapter 9 - Communications - Lecture slides.pdf"]
---

# Bit Error Rate and Eb/N0

## Definition

> [!note] Definition
> - **BER** is the probability that a bit is received incorrectly. It measures digital link quality.
> - For a given modulation, BER is a function of $E_b/N_0$ (energy per bit ÷ noise density):
> $$\frac{C}{N_0} = \frac{E_b}{N_0}R_b\quad\Longleftrightarrow\quad\Big(\frac{C}{N_0}\Big)_{dB} = \Big(\frac{E_b}{N_0}\Big)_{dB}+10\log R_b$$

## Explanation
- $t_b = 1/R_b$ and $E_b = Ct_b$, so $E_b/N_0 = C/(N_0R_b)$.
- For BPSK, BER = ½ erfc√($E_b/N_0$). **BER = 10⁻⁶ needs ≈ 10.5 dB.**
- **Modulation**:
  - ASK: amplitude;
  - FSK: frequency;
  - **PSK: phase, the most common**.
- **PCM encoding**: sample at $f_s\ge2f_{max}$ (Nyquist) and quantise to $n$-bit words. $R_b = nf_s$. A telephone channel is 8 kHz × 8 bit = 64 kbps.
- **Shannon**: $R_{max} = B\log_2(1+S/N)$. A higher data rate needs more bandwidth or a higher SNR.
- For a fixed link, doubling $R_b$ costs 3 dB of $E_b/N_0$. Because $L_{FS}\propto\rho^2$, the same EIRP supports half the data rate at $\sqrt2$ times the range.

![[ast_ber_psk.png|480]]

## Examples
- Pluto: $E_b/N_0$ = 10 dB, $C/N_0$ = 45.42, so $R_b$ = 35.42 dB-Hz = 3483 bps.
- 2014/15 Q1(vii): three types of digital modulation, and the most common one (4 marks).

## Related
- [[Link Budget Equation]] · [[Payload Data Rate]]

## Sources
- Chapter 9 slides 10–14, 28–29 (equations 9.1, 9.8)
