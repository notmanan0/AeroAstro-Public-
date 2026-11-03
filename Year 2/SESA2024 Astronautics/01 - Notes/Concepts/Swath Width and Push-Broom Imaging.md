---
title: "Swath Width and Push-Broom Imaging"
module: "SESA2024 Astronautics"
type: concept
stream: "Remote Sensing Case Study"
aliases: ["push-broom", "pushbroom", "whisk-broom", "whiskbroom", "swath width", "field of view", "ground resolution"]
tags: [sesa2024, concept, remote-sensing]
status: lectured
parent_lectures: ["[[SESA2024 11 - Payload and Orbit Selection]]", "[[SESA2024 13 - Calculating Orbital Elements for a Remote Sensing Mission]]"]
related_concepts: ["[[Repeat Ground Track]]", "[[Payload Data Rate]]"]
sources: ["02 - Sources/Lectures/SESA2024 Lecture 2025-12-04.txt", "02 - Sources/Lectures/SESA2024 Lecture 2025-10-07.txt"]
---

# Swath Width and Push-Broom Imaging

A push-broom imager is a line of detectors across the ground track that records one strip of the Earth for each pixel the spacecraft advances, building an image from its own forward motion; the width of ground it covers is the swath width.

For a nadir-pointing instrument with field of view $\beta$ at altitude $h$,

$$
d=2h\tan\frac\beta2,
$$

or $d=N_{pix}\,p$ from the number of pixels and the ground pixel size. The swath grows with altitude while the resolution coarsens, which is part of the first-pass trade between resolution and drag: a $28.96^\circ$ instrument covers 362 km at 700 km and 465 km at 900 km.

A whisk-broom imager instead sweeps a few detectors across the track with a mechanism, or, on a spinner such as Meteosat, with the spin. Push-broom has no moving parts and a longer dwell per pixel, so it gives better signal-to-noise and geometry, and modern Earth observers use it. In the case study, the swath sets the number of distinct ground tracks needed for full coverage, $N\approx2\pi R_E/d$, and the pixel size and ground speed set the data rate.

## Related

- [[SESA2024 11 - Payload and Orbit Selection#2. The push-broom imager|Push-broom imager in the lecture note]] · [[SESA2024 06 - Attitude Control#Type 1: spinner|Whisk-broom on a spinner]]
- [[Repeat Ground Track]] · [[Payload Data Rate]]
