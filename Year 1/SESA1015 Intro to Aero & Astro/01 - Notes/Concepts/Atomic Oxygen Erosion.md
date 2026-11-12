---
title: "Atomic Oxygen Erosion"
module: "SESA1015 Intro to Aero & Astro"
type: concept
stream: "Astronautics"
aliases: ["AO erosion", "Atomic oxygen", "AO fluence", "Surface recession"]
tags: [sesa1015, concept, astronautics, space-environment, materials]
status: complete
parent_lectures: ["[[SESA1015 A02 - Space Environment]]"]
related_concepts: ["[[Exponential Atmosphere and Scale Height]]", "[[Space Environment Hazards]]"]
sources: ["Astronautics Part 2 (Environment), pp. 19–20, 35–37, equation (2.3)"]
---

# Atomic Oxygen Erosion

Atomic oxygen (AO) erosion is the loss of surface material on a spacecraft in low Earth orbit caused by impacts of oxygen atoms, the dominant gas from about 200 km to several hundred kilometres; the recession depth is proportional to the AO fluence $F_0=n_{AO}Vt$.

The fluence counts the atoms that strike unit area of a ram-facing surface. In time $t$ a surface of area $A$ moving at speed $V$ sweeps out a volume $AVt$ and meets every atom in it, $n_{AO}AVt$ of them, so per unit area $F_0=n_{AO}Vt$ in m$^{-2}$. The orbital speed (7.7 km/s) dwarfs the atoms' thermal speed (about 1 km/s), so the surface facing the velocity vector takes almost all the flux and trailing surfaces very little. Each impact delivers about 5 eV, enough to break polymer bonds, and the oxygen then reacts to form volatile products.

Measured recession per $10^{24}$ atoms/m² is 2.8 µm for Kapton, 0.029 µm for Teflon, 0.00035 µm for aluminium (protected by its oxide) and 9.8 µm for silver (whose oxide flakes off). The worked example on pp. 35–36 takes a 10-day Shuttle flight at 300 km during solar maximum with $n_{AO}=10^{15}$ m$^{-3}$ and $V=7.7$ km/s: $F_0=10^{15}\times7.7\times10^3\times8.64\times10^5=6.7\times10^{24}$ m$^{-2}$, so Kapton loses $2.8\times6.7\approx19$ µm. A 25 µm Kapton blanket layer would last about 13 days under the same conditions.

Two common slips are leaving $t$ in days and forgetting how strongly $n_{AO}$ depends on altitude and solar activity: it spans roughly $10^{14}$ to $10^{16}$ m$^{-3}$ at 300 km between low and high activity, and falls with the oxygen scale height of about 58 km ([[Exponential Atmosphere and Scale Height]]). Protective coatings such as silicon oxide work only while they are continuous, because AO undercuts any pinhole or crack.

## Related

- Topic: [[SESA1015 A02 - Space Environment]] (§3 and §6)
- Concepts: [[Exponential Atmosphere and Scale Height]] · [[Space Environment Hazards]]
- Sources: Astronautics Part 2, pp. 19–20, 35–37
