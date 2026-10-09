---
title: "SESA2024 09 - Communications"
module: "SESA2024 Astronautics"
type: topic
stream: "Spacecraft Subsystems"
order: 9
tags:
  - sesa2024
  - communications
  - link-budget
aliases: ["Chapter 9", "Link budget", "Comms subsystem"]
date: 2026-09-25
status: complete
parent: ["[[SESA2024 Astronautics Hub]]"]
prerequisites: ["[[SESA2024 08 - Electrical Power Subsystem]]"]
next_topics: ["[[SESA2024 10 - Thermal Control]]"]
key_concepts: ["[[Decibels]]", "[[Antenna Gain and Beamwidth]]", "[[Link Budget Equation]]", "[[EIRP and G-T]]", "[[Bit Error Rate and Eb-N0]]"]
tutorial_sheets: ["[[SESA2024 Workbook Ch9 - Communications Solutions]]"]
sources: ["02 - Sources/Lectures/Chapter 9/2025 Chapter 9 - Communications - Lecture slides.pdf", "02 - Sources/Lectures/Chapter 9/2025 WEEK 8 - Chapter 9 - Communications - Lecture slides - complete.pdf"]
---

# SESA2024 09 - Communications

> [!abstract] Summary
> The comms subsystem receives commands and downlinks payload and telemetry data over microwave links in the **atmospheric window** (about 1–30 GHz).
>
> The **link budget**, in dB, adds the transmitter EIRP and the receiver $G/T$, then subtracts free-space loss, other losses and Boltzmann's constant. The result is $C/N_0$. For a digital link, $C/N_0 = (E_b/N_0)R_b$, and $E_b/N_0$ sets the bit error rate.
>
> Antenna gain $G = \eta(\pi D/\lambda)^2$ and beamwidth $\theta_{3dB}\approx72\lambda/D$ link the dish size to coverage and to the **power–gain trade-off**.

## Key Concepts
- [[Decibels]] · [[Antenna Gain and Beamwidth]] · [[Link Budget Equation]] · [[EIRP and G-T]] · [[Bit Error Rate and Eb-N0]]

---

## 1. Function and the decibel
- **Function**: receive operating commands and data from the ground; downlink payload and telemetry data. Example: Voyager.
- For **comsats, navigation satellites (GPS) and data-relay satellites (TDRSS)**, comms *is* the payload.
- **Decibels** (see [[Decibels]]): $(P_R/P_T)_{dB} = 10\log_{10}(P_R/P_T)$; $P_{dBW} = 10\log_{10}(P/1\ \text{W})$. Example: $P_T$ = 16.98 kW is 42.3 dBW.

## 2. Atmospheric windows and bands
- **Ionospheric absorption and reflection** below about 0.5 GHz, roughly constant.
- **Gaseous absorption** (H₂O, O₂) above about 10 GHz.
- **Rain** is highly variable and gives more than 10 dB above about 10 GHz.
- The window is therefore **about 1–30 GHz**.
- Bands are allocated by the **ITU**: L (1–2 GHz), S (2–4), C (4–8), X (8–12), Ku (12–18), Ka (27–40).
- **Higher frequency**: ✔ more bandwidth (data rate) and smaller dishes. ✘ rain fade.

## 3. Encoding, modulation and bandwidth
- Space links are **digital**, so the measure of quality is the **bit error rate (BER)**.
- **PCM** (pulse code modulation) is an *encoding* technique. Telephone example:
  - $f_{max}$ = 3.4 kHz; Nyquist requires $f_s\ge2f_{max}$, so use 8 kHz;
  - 8-bit words (256 levels) give $R_b = 8000\times8 = 64$ kbps.
- **Digital modulation of the carrier**: ASK (amplitude), FSK (frequency), **PSK (phase), the most widely used** (2014/15 Q1(vii)).
- **Shannon's law**: $R_{max} = B\log_2(1+S/N)$. Data rate needs bandwidth.

## 4. Noise
- Sources: atmospheric emission and scattering; the Sun, Earth and galactic sources; lightning; man-made sources (cars, machinery); internal electronics.
- Characterised by an equivalent **noise temperature** $T$: $N = kTB$, with $k = 1.38\times10^{-23}$ J/K.

## 5. Antenna gain and beamwidth
See [[Antenna Gain and Beamwidth]].
- An **isotropic radiator** has gain 1 (0 dB). A high-gain antenna concentrates power along the boresight.
- $G = \dfrac{\text{max power flux}}{\text{isotropic flux}} = \dfrac{4\pi A_{eff}}{\lambda^2} = \dfrac{4\pi\eta A}{\lambda^2}$, with $0.4<\eta<0.8$.

For a circular dish:

$$
G = \eta\left(\frac{\pi D}{\lambda}\right)^2,\qquad \theta_{3dB}\approx72\frac{\lambda}{D}\ \text{(degrees, half-power beamwidth)}
$$

C-band (4 GHz, $\lambda$ = 0.075 m, $\eta$ = 0.65):

| Dish | $\theta_{3dB}$ | $G$ |
|---|---|---|
| 1 m | 5.4° | 30.6 dB |
| 6 m | 0.9° | 46.1 dB |
| 25.9 m (Goonhilly A) | 0.2° | 58.5 dB |

![[ast_antenna_gain_beamwidth.png|700]]

## 6. The link budget
See [[Link Budget Equation]].
- An isotropic transmitter gives a flux of $P_T/4\pi\rho^2$ at range $\rho$. With gain it is $P_TG_T/4\pi\rho^2$.
- Received power: $P_R = \dfrac{P_TG_T}{4\pi\rho^2}A_{eff,R}$.
- Using $A_{eff,R} = G_R\lambda^2/4\pi$:

$$
P_R = P_TG_TG_R\left(\frac{\lambda}{4\pi\rho}\right)^2 = \frac{P_TG_TG_R}{L_{FS}},\qquad L_{FS} = \left(\frac{4\pi\rho}{\lambda}\right)^2
$$

Add other losses $L_A$ (atmosphere, rain, depointing, circuits). Put $C = P_R$ and $N_0 = kT_R$:

$$
\frac{C}{N_0} = P_TG_T\,\frac{1}{L_{FS}}\,\frac{1}{L_A}\,\frac{G_R}{T_R}\,\frac1k
$$

$$
\boxed{\Big(\frac{C}{N_0}\Big)_{dB} = \underbrace{10\log(P_TG_T)}_{\text{EIRP}}+\underbrace{10\log\frac{G_R}{T_R}}_{\text{figure of merit}}-\underbrace{20\log\frac{4\pi\rho}{\lambda}}_{\text{free-space loss}}-10\log L_A-\underbrace{10\log k}_{-228.6}}
$$

- **EIRP** $= P_TG_T$: the power an isotropic radiator would need to transmit to give the same flux at the receiver. See [[EIRP and G-T]].
- **$G_R/T_R$**: receiver sensitivity; $C/N_0\propto G_R/T_R$.
- Deep-space ground stations use **large dishes and cryogenic, low-noise receivers** to maximise $G/T$ against a huge $L_{FS}$ (2021/22 A3). Signals from Saturn are tiny because $L_{FS}\propto\rho^2$ (2022/23 A4).

## 7. Link quality
See [[Bit Error Rate and Eb-N0]].
- Bit time $t_b = 1/R_b$; energy per bit $E_b = Ct_b$.

$$
\frac{C}{N_0} = \frac{E_b}{N_0}\cdot\frac{1}{t_b} = \frac{E_b}{N_0}R_b\quad\Rightarrow\quad\Big(\frac{C}{N_0}\Big)_{dB} = \Big(\frac{E_b}{N_0}\Big)_{dB}+10\log R_b
$$

- For PSK, BER = $10^{-6}$ needs $E_b/N_0\approx10.5$ dB.

![[ast_ber_psk.png|500]]

## 8. Lecture example: GEO direct-to-home TV
**Data**: 92 Mbps at 4 GHz, slant range 38 400 km, user dish 0.4 m, $T_R$ = 150 K, BER $10^{-6}$, extra loss 5 dB. Then a 2 m spacecraft dish and 50 % efficient transponders.

The solution below uses $\eta$ = 0.65 and $E_b/N_0$ = 10.5 dB (from the BER curve):

| Term | Value |
|---|---|
| $\lambda$ | 0.075 m |
| $G_R$ (0.4 m) | 22.61 dB, so $G_R/T_R$ = 22.61 − 21.76 = **0.85 dB/K** |
| $C/N_0$ | 10.5 + 10 log(92 × 10⁶) = **90.1 dB-Hz** |
| $L_{FS}$ | 20 log(4π × 3.84 × 10⁷ / 0.075) = **196.2 dB** |
| **EIRP** | 90.1 − 0.85 + 196.2 + 5 − 228.6 = **61.9 dBW** |
| $G_T$ (2 m) | 36.6 dB, so $P_T$ = 25.3 dBW ≈ **336 W** RF |
| Transponder electrical power | $P_T/0.5$ ≈ **670 W** |

(The answer is sensitive to the $E_b/N_0$ read from the curve. With 11 dB: EIRP 62.4 dBW and about 750 W.)

## 9. Power–gain trade-off
The link fixes the EIRP $= P_TG_T$, but its split is a design choice (2013/14, 2015/16, 2017/18, 2024/25):
- **Larger dish**: more gain, less RF power (and less DC power, array area and thermal load). But it adds mass, accommodation and deployment difficulties, and its **narrow beam needs tighter pointing** (ACS). It may also shadow arrays or block payload fields of view.
- **Smaller dish**: easy to accommodate and wide coverage, but needs a high $P_T$, hence more power and thermal load.
- For **global Earth coverage** from radius $r$: $\theta_{3dB} = 2\sin^{-1}(R_E/r)$, which fixes $D = 72\lambda/\theta_{3dB}$. GEO gives 17.4°.

## Links
- Parent: [[SESA2024 Astronautics Hub]] · Previous: [[SESA2024 08 - Electrical Power Subsystem]] · Next: [[SESA2024 10 - Thermal Control]]
- Solutions: [[SESA2024 Workbook Ch9 - Communications Solutions]] (Pluto link budget)

## Sources
- Chapter 9 lecture (H. Sykulska-Lawrence), equations 9.1–9.8; Fortescue, Stark & Swinerd, Ch. 12
