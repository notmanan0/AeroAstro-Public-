---
title: "SESA2024 09 - Communications"
module: "SESA2024 Astronautics"
type: topic
stream: "Spacecraft Subsystems"
order: 9
tags: [sesa2024, communications, link-budget, decibels, antennas]
aliases: ["Comms subsystem", "Link budget", "Chapter 9"]
date: 2026-10-30
status: lectured
coverage: "Week 8 (2025-11-18; start of 2025-11-20) plus the pre-recorded Chapter 9 lecture; revision example 2026-01-06"
parent: ["[[SESA2024 Astronautics Hub]]"]
prerequisites: ["[[SESA2024 08 - Electrical Power Subsystem]]"]
next_topics: ["[[SESA2024 10 - Thermal Control]]"]
key_concepts: ["[[Decibels]]", "[[Antenna Gain and Beamwidth]]", "[[Link Budget Equation]]", "[[EIRP and G-T]]", "[[Bit Error Rate and Eb-N0]]"]
tutorial_sheets: ["[[SESA2024 Workbook Ch9 - Communications Solutions]]"]
sources: ["02 - Sources/Lectures/Chapter 9/2025 WEEK 8 - Chapter 9 - Communications - Lecture slides - complete.pdf", "02 - Sources/Lectures/Chapter 9/2025 Chapter 9 - Communications - Lecture slides.pdf", "02 - Sources/Lectures/SESA2024 Lecture 2025-11-18.txt", "02 - Sources/Lectures/SESA2024 Lecture 2025-11-20.txt", "02 - Sources/Lectures/SESA2024 Lecture Chapter 9 - Communications - prerecord - week 8.txt", "02 - Sources/Lectures/SESA2024 Lecture 2026-01-06.txt"]
---

# SESA2024 09 - Communications

> [!abstract] Summary
> The communications subsystem receives commands from the ground and sends payload and telemetry data down, digitally, as phase-shift-keyed microwave signals in the atmospheric window of about 0.1–30 GHz. Link quality is set by the bit error rate, which fixes the energy per bit over the noise density $E_b/N_0$. The link budget equation, written in decibels, ties that to the transmitter's EIRP, the receiver's figure of merit $G_R/T_R$, the free-space loss and the other losses. The spacecraft designer controls only the EIRP, $P_TG_T$, and trading power against antenna gain is the central design decision.

> [!summary]- Exam use: quick path
> - **Use it when:** you need an antenna's gain or beamwidth, a required EIRP or transmitter power, an achievable data rate, or a time to downlink a data volume.
> - **Assumptions:** circular parabolic dishes ($\eta=0.65$ unless given); free-space propagation over the slant range; the link budget evaluated for the downlink, which is the power-limited direction.
> - **Method:** 1. $\lambda=c/f$. 2. $G=\eta(\pi D/\lambda)^2$, $\theta_{3dB}=72\lambda/D$ degrees. 3. $C/N_0=E_b/N_0+10\log R_b$ in dB, with $E_b/N_0$ from the BER curve. 4. $C/N_0=\mathrm{EIRP}+G_R/T_R-20\log(4\pi\rho/\lambda)-L_a+228.6$. 5. Solve for the one unknown, then convert out of decibels.
> - **Common mistakes:** slant range in km with wavelength in m in the free-space loss; adding a decibel quantity to a linear one.
> - **Practise:** [[#GEO TV broadcast satellite]] · [[#Voyager at Saturn (2017/18 B3)]]

There is no point putting an instrument in space if its data cannot be brought home. The communications subsystem receives operating commands from the ground and downlinks the payload data and the telemetry describing the spacecraft's health (2025-11-18, ll. 51–75). For some missions, such as communications, navigation and data-relay satellites, it is the payload.

A transmitter spreads power over a sphere that grows with the square of the distance, so very little arrives. A dish concentrates the power into a narrow beam, at the cost of having to be pointed. The receiver must pick a weak signal out of electromagnetic noise from every warm object it sees, and the question is whether enough energy arrives in each bit to tell a one from a zero reliably. Voyager, some 15–16 billion miles away, is the extreme case: its signal takes nearly a day to arrive and is fantastically weak, yet it is still received.

## 1. Decibels

Communications calculations multiply and divide quantities spanning many orders of magnitude, so they are done in decibels, a logarithmic ratio (2025-11-18, ll. 76–175). For a power ratio,

$$
x_{dB}=10\log_{10}\frac{P}{P_{ref}}.
$$

With $P_{ref}=1$ W the unit is the decibel-watt, dBW. Converting back,

$$
P=P_{ref}\times10^{x_{dB}/10}.
$$

Products become sums and quotients become differences, which is the whole reason for using them. The practice conversion set in the lecture: $42.3\ \mathrm{dBW}=10^{4.23}\ \mathrm W=16.98$ kW (l. 160). Decibels are familiar from sound because the ear responds roughly logarithmically, but in communications they are simply ratios.

## 2. The atmospheric window and frequency allocation

Signals travel at the speed of light, $3\times10^8$ m/s, which still means long delays at interplanetary distances (ll. 176–200).

> [!warning] Transcript slip (2025-11-18, ll. 176–195)
> Voyager is put at "15 billion miles" with a light time of "17 and a half hours", now perhaps 18 or 19. Light covers 15 billion miles ($2.4\times10^{13}$ m) in 22.4 hours, and Voyager 1 is now about 15.7 billion miles away, roughly 23 light-hours.

The atmosphere limits which frequencies can be used (ll. 200–250). At low frequencies electrons in the ionosphere absorb and reflect; at high frequencies water vapour, oxygen and rain absorb. The usable window runs from about 0.1 to about 30 GHz, and losses inside it still depend on the weather and on the path length through the atmosphere, which is much longer at a $15^\circ$ elevation than straight up. The window is a finite resource, so the International Telecommunication Union (ITU) allocates bands for fixed and mobile communications, navigation, space research, and tracking, telemetry and command, now to three decimal places in some bands (ll. 251–300). Operators apply in advance, like planning permission, and satellites close together in the geostationary ring must not use frequencies that interfere.

## 3. Encoding, modulation and bandwidth

Space communications are digital, so link quality is measured by the bit error rate (BER), the fraction of bits received wrongly; some errors can be corrected in software (ll. 301–330).

### Encoding: pulse code modulation

An analogue signal, such as a voltage from a microphone, is sampled at regular intervals and each sample is quantised into one of $2^n$ levels, written as an $n$-bit word (ll. 326–420). The Nyquist criterion says the sampling frequency must be at least twice the highest frequency of interest. Speech needs frequencies up to about 4 kHz (hearing tests use 0.5, 1, 2 and 4 kHz), so

$$
f_s=2\times4\ \mathrm{kHz}=8\ \mathrm{kHz},
\qquad
R_b=8000\times8\ \mathrm{bits}=64\ \mathrm{kbit/s}
$$

for one telephone channel with 8-bit (256-level) samples. Despite its name, pulse code modulation is an encoding technique, not a modulation.

### Modulation: shift keying

The bits are carried by changing one property of a carrier wave (ll. 426–525): amplitude (amplitude shift keying), frequency (frequency shift keying) or phase (phase shift keying, PSK). All three are used, but PSK dominates. Amplitude keying means the transmitted power switches on and off, and frequency keying needs more of the tightly allocated spectrum; phase keying keeps both power and frequency constant and just inverts the phase when the bit changes.

### Bandwidth

Each bit in the PSK picture takes at least one carrier cycle, so a higher frequency carries more bits per second. Shannon's law gives the maximum data rate of a channel of bandwidth $B$:

$$
C=B\log_2\left(1+\frac SN\right),
$$

with the bandwidth a direct multiplier (ll. 526–545).

## 4. Noise

Noise is any unwanted interference in the signal, and the receiver must recover the signal from it (ll. 526–575). Sources include lightning, the Sun, the Earth, galactic sources, artificial sources such as vehicles and machinery, the spacecraft's own electronics, and atmospheric emission and scattering. In the revision lecture's 2017/18 B3 answer, Dr Sykulska-Lawrence stressed emission and scattering rather than absorption, since the frequency is chosen inside the window where absorption is small (2026-01-06, ll. 126–200).

Noise is characterised by an equivalent noise temperature $T$. The noise power in bandwidth $B$ and the noise density (per hertz) are

$$
N=kTB,
\qquad
N_0=kT,
$$

with Boltzmann's constant $k=1.38\times10^{-23}$ J/K, so $10\log k=-228.6$ dB.

## 5. Antenna gain and beamwidth

An isotropic antenna radiates equally in all directions; its gain is 1, or 0 dB (2025-11-18, ll. 576–625). A high-gain antenna concentrates the power, like a torch bulb with a parabolic mirror. Its gain is the ratio of the peak power flux to that of an isotropic radiator with the same transmitted power. The beam has a peak on the boresight and falls away; the beamwidth $\theta$ is measured between the half-power points, 3 dB below the peak.

For a circular parabolic dish of diameter $D$ at wavelength $\lambda$, the empirical relations used in the course are (2025-11-20, ll. 26–75)

$$
\theta_{3dB}=\frac{72\lambda}{D}\ \text{degrees},
\qquad
G=\frac{4\pi A_{eff}}{\lambda^2}=\eta\left(\frac{\pi D}{\lambda}\right)^2,
$$

where $A_{eff}=\eta A$ is the effective aperture area and the efficiency $\eta$ is 0.4–0.8, typically 0.65 for these antennas. Gain rises with $D^2$ while beamwidth falls with $D$: a bigger dish gives a stronger, narrower beam that must be pointed more accurately.

The lecture's examples at C band, 4 GHz ($\lambda=0.075$ m), recomputed:

| Dish | $\theta_{3dB}$ | $G$ | $G$ (dB) |
|---|---|---|---|
| 1 m | 5.4° | 1140 | 30.6 |
| 6 m | 0.90° | 41 060 | 46.1 |
| 25.9 m (Goonhilly) | 0.21° | $7.65\times10^5$ | 58.8 |

> [!warning] Transcript slip (2025-11-20, ll. 101–110)
> The 6 m dish is quoted as "64.1 decibels". $0.65(\pi\times6/0.075)^2=41\,060$ is 46.1 dB, and a 6 m dish cannot out-gain the 25.9 m Goonhilly antenna's 58.5–58.8 dB. The digits are transposed.

## 6. The link budget equation

The pre-recorded lecture derives it (ll. 1–100). The downlink matters most for design: the ground station can be given almost unlimited power, the spacecraft cannot (ll. 1–25).

An isotropic transmitter of power $P_T$ spreads it over a sphere of radius $\rho$, the slant range, so the power flux at the receiver is

$$
F=\frac{P_T}{4\pi\rho^2}.
$$

A transmitting antenna of gain $G_T$ multiplies this:

$$
F=\frac{P_TG_T}{4\pi\rho^2}.
$$

The receiver collects the flux over its effective area, $P_R=FA_{eff}$. From the gain relation, $A_{eff}=G_R\lambda^2/4\pi$, so

$$
P_R=\frac{P_TG_T}{4\pi\rho^2}\cdot\frac{G_R\lambda^2}{4\pi}=\frac{P_TG_TG_R}{(4\pi\rho/\lambda)^2}.
$$

The denominator is the free-space loss $L_{FS}=(4\pi\rho/\lambda)^2$. Further losses from atmospheric absorption, rain, mispointing and internal circuits are lumped into $L_a$. Treat the received power as the carrier power $C$ and divide by the noise density $N_0=kT_R$:

$$
\frac{C}{N_0}=\frac{P_TG_T\cdot G_R/T_R}{L_{FS}\,L_a\,k}.
$$

Take $10\log_{10}$ of both sides. The squared free-space loss gives a factor of 20:

$$
\boxed{10\log\frac{C}{N_0}=10\log(P_TG_T)+10\log\frac{G_R}{T_R}-20\log\frac{4\pi\rho}{\lambda}-10\log L_a-10\log k}
$$

with $-10\log k=+228.6$ dB. Term by term (ll. 76–125): the carrier-to-noise-density ratio relates to the BER; $P_TG_T$ is the equivalent isotropic radiated power (EIRP); $G_R/T_R$ is the ground station's figure of merit, its sensitivity; then the free-space loss, the additional losses and the constant.

The losses are fixed by geometry and atmosphere and the figure of merit by the ground station, so on the spacecraft the designer controls only the EIRP. It is the power an isotropic radiator would need to give the same flux at the receiver. The same EIRP can come from high power and low gain or low power and high gain, and that is the power–gain trade-off (ll. 101–130; 2026-01-06, ll. 251–350). A bigger dish saves power but adds mass, may not fit in the fairing without a deployment mechanism (and its risk), may shadow arrays or block payload views, and narrows the beam, tightening the ACS pointing requirement.

## 7. From bit error rate to data rate

If bits arrive at rate $R_b$, each lasts $T_b=1/R_b$, and the energy per bit is $E_b=CT_b=C/R_b$ (pre-recorded lecture, ll. 126–155). Dividing by $N_0$:

$$
\frac{C}{N_0}=\frac{E_b}{N_0}R_b
\quad\Longrightarrow\quad
10\log\frac{C}{N_0}=10\log\frac{E_b}{N_0}+10\log R_b.
$$

For a given modulation, $E_b/N_0$ fixes the BER: more energy per bit, fewer errors. Choosing an acceptable BER (say $10^{-6}$, one wrong bit in a million) sets the required $E_b/N_0$ from the curve (about 10 dB for the course's PSK curve), the data rate then sets $C/N_0$, and the link budget gives the EIRP.

![[ast_ber_psk.png|600]]

## Worked examples

All numbers recomputed in Python, with $c=3\times10^8$ m/s and $10\log k=-228.6$ dB.

### GEO TV broadcast satellite

The pre-recorded lecture's example, from an old past paper (ll. 155–290): a GEO satellite broadcasts TV at 92 Mbit/s to users at a slant range of 38 400 km, at C band, 4 GHz. A user's dish is 0.4 m in diameter with a system noise temperature of 150 K. A BER of $10^{-6}$ is required, and there are 5 dB of additional losses. Estimate the satellite EIRP and, if the spacecraft dish is 2 m and the transponders are 50 % efficient, the transponder electrical power.

$\lambda=3\times10^8/4\times10^9=0.075$ m. Term by term:

$$
10\log\frac{C}{N_0}=10+10\log(92\times10^6)=10+79.64=89.64\ \mathrm{dB},
$$

using $E_b/N_0\approx10$ dB read from the curve for BER $10^{-6}$;

$$
G_R=0.65\left(\frac{\pi\times0.4}{0.075}\right)^2=182.5,
\qquad
10\log\frac{G_R}{T_R}=22.61-21.76=0.85\ \mathrm{dB};
$$

$$
20\log\frac{4\pi\times3.84\times10^7}{0.075}=196.17\ \mathrm{dB}.
$$

Then

$$
\mathrm{EIRP}=89.64-0.85+196.17+5-228.6=61.36\ \mathrm{dBW}.
$$

For the transmitter, $G_T=0.65(\pi\times2/0.075)^2=4562=36.59$ dB, so

$$
10\log P_T=61.36-36.59=24.77\ \mathrm{dBW},
\qquad
P_T=10^{2.477}=300\ \mathrm W,
$$

and at 50 % efficiency the transponders draw 600 W. The lecture's warning: convert the slant range to metres to match the wavelength (ll. 251–260).

### Voyager at Saturn (2017/18 B3)

The revision lecture's question (2026-01-06, ll. 201–520). First, compare 2, 3 and 4 m dishes at X band, 8.5 GHz, with efficiency 0.5. $\lambda=0.03529$ m and $G=0.5(\pi D/\lambda)^2=3962.5D^2$:

| Dish | $G$ | dB | $\theta_{3dB}$ |
|---|---|---|---|
| 2 m | 15 850 | 42.0 | 1.27° |
| 3 m | 35 650 | 45.5 | 0.85° |
| 4 m (deployable) | 63 380 | 48.0 | 0.64° |

Each step up in size lowers the transmitter power needed for a given EIRP but adds mass, tightens pointing, and for the 4 m dish adds a deployment risk.

Second, Voyager stored 0.5 Gbit at the Saturn fly-by and downlinked it from 9.5 AU at 8.5 GHz with an EIRP of 61.2 dBW to a 70 m Deep Space Network dish (efficiency 0.5) with a noise temperature of 25 K. With $E_b/N_0=10$ dB and 3 dB of additional losses, how long does the downlink take?

$$
G_R=3962.5\times70^2=1.94\times10^7,
\qquad
10\log\frac{G_R}{T_R}=72.89-13.98=58.90\ \mathrm{dB}.
$$

With $\rho=9.5\times1.5\times10^{11}$ m, the free-space loss is 294.10 dB. Then

$$
10\log\frac{C}{N_0}=61.2+58.90-294.10-3+228.6=51.60\ \mathrm{dB},
$$

$$
10\log R_b=51.60-10=41.60\ \mathrm{dB},
\qquad
R_b=1.44\times10^4\ \mathrm{bit/s},
$$

$$
t=\frac{0.5\times10^9}{1.44\times10^4}=3.47\times10^4\ \mathrm s=9.6\ \mathrm h.
$$

The lecture's 14 421 bit/s and 9.631 h use 1 AU = $1.5\times10^8$ km; with $1.496\times10^8$ km the answers are 14 510 bit/s and 9.57 h.

## Links

- Parent: [[SESA2024 Astronautics Hub]]
- Previous: [[SESA2024 08 - Electrical Power Subsystem]]
- Next: [[SESA2024 10 - Thermal Control]]
- Concepts: [[Decibels]] · [[Antenna Gain and Beamwidth]] · [[Link Budget Equation]] · [[EIRP and G-T]] · [[Bit Error Rate and Eb-N0]]
- Workbook: [[SESA2024 Workbook Ch9 - Communications Solutions]]
- Data volume in the case study: [[SESA2024 14 - Orbit Control, Drag and Payload Data Rate]]
- Year 1: decibels and Bode plots, [[FEEG1004 D3 - AC Filters and Bode Plots]]

## Sources

- `2025 WEEK 8 - Chapter 9 - Communications - Lecture slides - complete.pdf` with transcripts `SESA2024 Lecture 2025-11-18.txt` and `SESA2024 Lecture 2025-11-20.txt`, ll. 1–135 (Dr H. Sykulska-Lawrence)
- `2025 Chapter 9 - Communications - Lecture slides.pdf` with the pre-recorded transcript `SESA2024 Lecture Chapter 9 - Communications - prerecord - week 8.txt` (link budget derivation, GEO TV example)
- Revision lecture `SESA2024 Lecture 2026-01-06.txt` (2017/18 B3)
- Fortescue, Stark and Swinerd, *Spacecraft Systems Engineering*, Ch. 12

## Self-study tasks

### Core

- [ ] Confirm that 42.3 dBW is 16.98 kW ("do that in your own time", 2025-11-18, ll. 150–160). → [[#1. Decibels]]
- [ ] Confirm the beamwidth and gain of 1 m, 6 m and 25.9 m dishes at 4 GHz ("you can confirm for yourself", 2025-11-20, ll. 76–110). → [[#5. Antenna gain and beamwidth]]
- [ ] The GEO TV broadcast example: EIRP and transponder power. Targets 61.4 dBW and 600 W. → [[#GEO TV broadcast satellite]]
- [ ] 2017/18 B3: noise sources, dish trade-off and the Voyager downlink time ("go through this in your own time", 2026-01-06, ll. 501–510). Target about 9.6 h. → [[#Voyager at Saturn (2017/18 B3)]]
- [ ] Wavelength, gain and beamwidth of a 3 m dish (Workbook Ch9 Q2–Q3). → [[SESA2024 Workbook Ch9 - Communications Solutions#Q2 and Q3. Wavelength, gain and beamwidth of a 3 m dish with efficiency 0.5|Workbook solution]]
- [ ] The link budget and the meaning of EIRP and $G_R/T_R$ (Workbook Ch9 Q5). → [[#6. The link budget equation]] · [[SESA2024 Workbook Ch9 - Communications Solutions#Q5. Link budget, and the meaning of EIRP and G over T|Workbook Q5]]

### Further practice

- [ ] Derive the link budget equation from the power flux of an isotropic radiator (pre-recorded lecture, ll. 1–100). → [[#6. The link budget equation]]
- [ ] The data rate of a PCM telephone channel (2025-11-18, ll. 376–425). → [[#Encoding: pulse code modulation]]
- [ ] Why PSK is the most widely used modulation (asked of the class, ll. 451–500). → [[#Modulation: shift keying]]
- [ ] The atmospheric window, and large spacecraft antennas and the power–gain trade-off (Workbook Ch9 Q1, Q6). → [[#2. The atmospheric window and frequency allocation]]
- [ ] GEO global-coverage antenna at 1.5 GHz, and the Pluto fly-by downlink (Workbook Ch9 Q7, Q9). → [[SESA2024 Workbook Ch9 - Communications Solutions#Q7. GEO global-coverage antenna at 1.5 GHz|Workbook Q7]] · [[SESA2024 Workbook Ch9 - Communications Solutions#Q9. Pluto/Charon fly-by downlink, 2 Gbit at 40 AU|Workbook Q9]]
