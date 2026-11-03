---
title: "Link Budget Equation"
module: "SESA2024 Astronautics"
type: concept
stream: "Spacecraft Subsystems"
aliases: ["link budget", "free-space loss", "carrier-to-noise density ratio", "C/N0", "link equation"]
tags: [sesa2024, concept, communications]
status: lectured
parent_lectures: ["[[SESA2024 09 - Communications]]"]
related_concepts: ["[[EIRP and G-T]]", "[[Bit Error Rate and Eb-N0]]", "[[Antenna Gain and Beamwidth]]", "[[Decibels]]"]
sources: ["02 - Sources/Lectures/SESA2024 Lecture Chapter 9 - Communications - prerecord - week 8.txt", "Fortescue, Stark and Swinerd, Spacecraft Systems Engineering, Ch. 12"]
---

# Link Budget Equation

The link budget equation relates the carrier-to-noise-density ratio at a receiver to the transmitter's EIRP, the receiver's figure of merit and the losses along the path:

$$
10\log\frac{C}{N_0}=10\log(P_TG_T)+10\log\frac{G_R}{T_R}-20\log\frac{4\pi\rho}{\lambda}-10\log L_a+228.6.
$$

It follows from the power flux of a transmitter, $P_TG_T/4\pi\rho^2$, collected over the receiver's effective area $G_R\lambda^2/4\pi$, divided by the noise density $kT_R$. The geometric spreading and the effective-area relation combine into the free-space loss $(4\pi\rho/\lambda)^2$, which gives the $20\log$; $L_a$ lumps the atmospheric, rain, pointing and circuit losses; and $-10\log k=228.6$.

Each term is fixed by a different part of the system. The required $C/N_0$ is set by the data rate and the bit error rate, through $C/N_0=(E_b/N_0)R_b$. The free-space and other losses are set by distance, frequency and environment. $G_R/T_R$ belongs to the ground station. That leaves the EIRP as the spacecraft designer's variable, and the downlink is the direction that matters because the spacecraft's power is limited.

In use, every term but one is given or computable, and the equation is solved for the unknown: the EIRP for a GEO TV satellite (61.4 dBW), or the data rate for Voyager's downlink from Saturn (about 14 kbit/s). The usual errors are mixing km and m in $\rho/\lambda$ and adding linear quantities to decibels.

## Related

- [[SESA2024 09 - Communications#6. The link budget equation|Derivation in the lecture note]] · [[SESA2024 09 - Communications#Worked examples|Worked examples]]
- [[EIRP and G-T]] · [[Bit Error Rate and Eb-N0]] · [[Antenna Gain and Beamwidth]] · [[Decibels]]
