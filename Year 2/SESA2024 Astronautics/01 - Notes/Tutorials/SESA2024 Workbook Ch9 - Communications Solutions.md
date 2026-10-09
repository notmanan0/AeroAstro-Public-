---
title: "SESA2024 Workbook Ch9 - Communications Solutions"
module: "SESA2024 Astronautics"
type: tutorial
stream: "Spacecraft Subsystems"
tags:
  - sesa2024
  - tutorial-solutions
  - communications
  - link-budget
sheet: "Problem Sheet Workbook 2025-26, Chapter 9 (pp. 113-122)"
theory_notes: ["[[SESA2024 09 - Communications]]"]
key_concepts: ["[[Link Budget Equation]]", "[[Antenna Gain and Beamwidth]]", "[[EIRP and G-T]]", "[[Bit Error Rate and Eb-N0]]", "[[Decibels]]"]
status: complete
sources: ["02 - Sources/Lectures/SESA2024 Astronautics PROBLEM SHEET WORKBOOK 2025-26 V1.1.pdf"]
---

# SESA2024 Workbook Ch9 - Communications Solutions

> [!abstract] Sheet Info
> Nine questions. Q2, Q3, Q7 and Q9 are numerical, and Q9 (the Pluto downlink) is the full link-budget template. Constants: $c = 3\times10^8$ m/s, $k = 1.38\times10^{-23}$ J/K ($-228.60$ dBW/Hz/K), 1 AU = $1.5\times10^8$ km, dish efficiency $\eta = 0.5$. All numbers were reproduced in Python ✔.

## Theory Links
- [[SESA2024 09 - Communications]]
- Concepts: [[Link Budget Equation]] · [[Antenna Gain and Beamwidth]] · [[EIRP and G-T]] · [[Bit Error Rate and Eb-N0]] · [[Decibels]]

---

## Q1: The atmospheric window (about 1–30 GHz)
- **Below about 500 MHz**: the signal is absorbed or reflected by free electrons in the **ionosphere**.
- **Above about 10 GHz**: there is absorption by **water vapour and O₂**, and above all by **rain** in the troposphere, which can exceed 10 dB above about 10 GHz.
- **Higher end**: ✔ wider bandwidth, so a higher data rate (Shannon), and smaller antennas for the same gain. ✘ rain fade: a downpour at the ground station can seriously attenuate the link.

## Q2 and Q3: Wavelength, gain and beamwidth of a 3 m dish ($\eta = 0.5$)

$$
\lambda = \frac{c}{f},\qquad G = \eta\left(\frac{\pi D}{\lambda}\right)^2,\qquad \theta_{3dB}\approx72\frac{\lambda}{D}\ \text{(degrees)}
$$

| Band | $f$ (Hz) | $\lambda$ (m) | $G$ (dB) | $\theta_{3dB}$ (°) |
|---|---|---|---|---|
| L | $1.5\times10^9$ | 0.2 | 30.45 | 4.8 |
| C | $4\times10^9$ | 0.075 | 38.97 | 1.8 |
| X | $8\times10^9$ | 0.0375 | 44.99 | 0.9 |
| Ku | $14\times10^9$ | 0.0214 | 49.87 | 0.51 |

Example (L-band): $G = 0.5(3\pi/0.2)^2\approx1110$, which is 30.45 dB.

- Doubling $f$ adds 6 dB of gain and halves the beamwidth.
- Doubling $D$ does the same.

![[ast_antenna_gain_beamwidth.png|700]]

## Q4: Digital modulation
- **ASK**: carrier *amplitude* switched between two levels (for example zero for "0").
- **FSK**: carrier *frequency* switched.
- **PSK**: carrier *phase* switched (for example by 180°) at boundaries between dissimilar bits. **PSK is the most widely used.**

(PCM is an *encoding* scheme, not modulation. Telephone example: $f_s = 2\times3.4$ kHz rounded to 8 kHz; 8 kHz × 8 bits = 64 kbps.)

## Q5: Link budget; the meaning of EIRP and $G_R/T_R$

$$
10\log\frac{C}{N_0} = 10\log(P_TG_T)+10\log\frac{G_R}{T_R}-20\log\frac{4\pi\rho}{\lambda}-10\log L_A-10\log k
$$

Derivation: see [[Link Budget Equation]]. The key step is replacing the received power $P_R$ by the carrier $C$ and introducing the noise density $N_0 = kT_R$. The receiver collects noise as well as signal.

- **EIRP** = $P_TG_T$: the power an imaginary **isotropic** radiator at the spacecraft would need to transmit to create the same power flux (W/m²) at the receiver.
- **$G_R/T_R$**: the receiver's figure of merit (sensitivity). It is directly proportional to the received $C/N_0$.

## Q6: Large spacecraft antennas and the power–gain trade-off
| ✔ Large dish | ✘ Large dish |
|---|---|
| High gain | Hard to accommodate on the spacecraft and in the launcher fairing (may need deployment) |
| Lower transmitter power needed for a given EIRP | Can shadow arrays or obscure payload fields of view |
| | Narrow $\theta_{3dB}$, so tighter pointing (ACS) requirements |

**Power–gain trade-off**: the link needs a given EIRP $= P_TG_T$ (for example 65 dBW for an interplanetary link).
- In dB, $(P_T)_{dB}+(G_T)_{dB} = 65$.
- How to split it between transmitter power (the power subsystem: arrays, RTG, thermal) and antenna gain (dish size: mass, accommodation, pointing) is a system-level trade-off.

## Q7: GEO global-coverage antenna at 1.5 GHz
Geometry: $\sin\alpha = R_E/R_{GEO} = 1/6.611$, so $\alpha = 8.7^\circ$. The Earth subtends $2\alpha$:

$$
\theta_{3dB} = 2\alpha = 17.4^\circ = 72\frac{\lambda}{D}\Rightarrow D = 72\frac{0.2}{17.4}\approx\mathbf{0.83\ m}
$$

$$
G = 10\log_{10}\left[0.5\left(\frac{0.83\pi}{0.2}\right)^2\right]\approx\mathbf{19.3\ dB}
$$

> [!tip] This exact geometry recurs
> 2022/23 B2 (orbit radius 18 000 km, $\alpha = 20.7^\circ$), 2023/24 B2 (C-band Northern hemisphere) and 2024/25 B2 (12 h GPS orbit) all size the dish so that $\theta_{3dB}$ equals the angle the Earth subtends, $2\sin^{-1}(R_E/r)$.

## Q8: BER
- The BER is the probability that a bit is received wrongly: BER = $10^{-1}$ means one bit in ten is wrong.
- It depends on the energy per bit relative to the noise density, $E_b/N_0$.
- For PSK, BER = $10^{-6}$ needs $E_b/N_0\approx10.5$ dB.

The link to $C/N_0$:

$$
\frac{C}{N_0} = \frac{E_b}{N_0}\cdot\frac{1}{t_b} = \frac{E_b}{N_0}R_b\quad\Rightarrow\quad\Big(\frac{C}{N_0}\Big)_{dB} = \Big(\frac{E_b}{N_0}\Big)_{dB}+10\log R_b
$$

![[ast_ber_psk.png|520]]

## Q9: Pluto/Charon fly-by downlink, 2 Gbit at 40 AU
**Data**: $f = 8.44$ GHz, EIRP = 65 dBW, DSN 70 m dish, $T_R = 28$ K, $E_b/N_0 = 10$ dB, $L_A = 0$, $\eta = 0.5$.

| Term | Working | dB |
|---|---|---|
| EIRP | given | +65.00 |
| $G_R/T_R$ | $\lambda = 0.0355$ m; $G_R = 0.5(\pi70/\lambda)^2 = 1.914\times10^7$; ÷ 28 | +58.35 |
| $L_{FS}$ | $\rho = 40\times1.5\times10^{11}$ m = $6\times10^{12}$ m; $20\log(4\pi\rho/\lambda)$ | −306.53 |
| $L_A$ | given | 0 |
| $k$ | $10\log(1.38\times10^{-23})$ | −(−228.60) |

$$
10+(R_b)_{dB} = 65.00+58.35-306.53-0+228.60\ \Rightarrow\ (R_b)_{dB} = 35.42\ \text{dB}\ \Rightarrow\ R_b = \mathbf{3483\ bit/s}
$$

$$
t = \frac{2\times10^9}{3483} = 5.742\times10^5\ \text{s}\approx159.5\ \text{h}\approx\mathbf{6.6\ days}
$$

![[ast_link_budget_pluto.png|650]]

**Power against dish size**:

$$
P_TG_T = 10^{6.5}\ \Rightarrow\ P_T\eta\Big(\frac{\pi D}{\lambda}\Big)^2 = 10^{6.5}\ \Rightarrow\ P_TD^2 = \frac{10^{6.5}\lambda^2}{\eta\pi^2}\approx\mathbf{810}
$$

| $P_T$ (W) | 810 | 202 | 90 | 50 |
|---|---|---|---|---|
| $D$ (m) | 1 | 2 | 3 | 4 |

**Choice**: far from the Sun, power is scarce (RTG), so favour a large dish and low $P_T$. **About 3–4 m** is a sensible compromise against accommodation and pointing penalties. (New Horizons flew a 2.1 m dish with about 12 W. The real mission had a lower EIRP and took about 15 months to downlink.)

## Sources
- Workbook 2025-26 Chapter 9 questions (p. 113–114) and solutions (p. 117–122)
- Chapter 9 lecture (equations 9.1–9.8) and the GEO TV example
