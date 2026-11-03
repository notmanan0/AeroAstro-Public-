---
title: "Antenna Gain and Beamwidth"
module: "SESA2024 Astronautics"
type: concept
stream: "Spacecraft Subsystems"
aliases: ["antenna gain", "beamwidth", "3 dB beamwidth", "half-power beamwidth", "parabolic dish", "isotropic radiator", "effective aperture"]
tags: [sesa2024, concept, communications]
status: lectured
parent_lectures: ["[[SESA2024 09 - Communications]]"]
related_concepts: ["[[Link Budget Equation]]", "[[EIRP and G-T]]", "[[Decibels]]"]
sources: ["02 - Sources/Lectures/SESA2024 Lecture 2025-11-20.txt"]
---

# Antenna Gain and Beamwidth

An antenna's gain is the ratio of the peak power flux it produces to the flux an isotropic radiator of the same power would produce, and its beamwidth is the angle between the half-power (3 dB) points of its beam.

An isotropic radiator has a gain of 1 (0 dB). A parabolic dish concentrates the power like a mirror behind a torch bulb. For a circular dish of diameter $D$ and efficiency $\eta$ (0.4–0.8, typically 0.65 in the course) at wavelength $\lambda$,

$$
G=\eta\left(\frac{\pi D}{\lambda}\right)^2,
\qquad
\theta_{3dB}=\frac{72\lambda}{D}\ \text{degrees}.
$$

The gain comes from the general relation $G=4\pi A_{eff}/\lambda^2$ with $A_{eff}=\eta\pi D^2/4$. Doubling the dish diameter quadruples the gain (+6 dB) and halves the beamwidth. At 4 GHz a 1 m dish gives 30.6 dB and 5.4°, a 6 m dish 46.1 dB and 0.9°, and the 25.9 m Goonhilly antenna 58.8 dB and 0.21°.

The trade-off is the heart of the power–gain choice: more gain means less transmitter power for the same EIRP, but a heavier dish that may need deploying, may shadow arrays, and needs tighter pointing. A GEO global-coverage antenna works the other way: its beamwidth must be about 17° to see the whole Earth, which fixes a small dish.

![[ast_antenna_gain_beamwidth.png|560]]

## Related

- [[SESA2024 09 - Communications#5. Antenna gain and beamwidth|Gain and beamwidth in the lecture note]]
- [[Link Budget Equation]] · [[EIRP and G-T]] · [[Decibels]]
