---
title: "Payload Data Rate"
module: "SESA2024 Astronautics"
type: concept
stream: "Remote Sensing Case Study"
aliases: ["data rate", "line time", "ground speed", "data compression", "pixel rate"]
tags: [sesa2024, concept, remote-sensing, communications]
status: lectured
parent_lectures: ["[[SESA2024 14 - Orbit Control, Drag and Payload Data Rate]]"]
related_concepts: ["[[Swath Width and Push-Broom Imaging]]", "[[Bit Error Rate and Eb-N0]]", "[[Link Budget Equation]]"]
sources: ["02 - Sources/Lectures/SESA2024 Astronautics PROBLEM SHEET WORKBOOK 2025-26 V1.1.pdf"]
---

# Payload Data Rate

The data rate of a push-broom imager is the number of bits in one image line divided by the time the ground track takes to advance one pixel.

The sub-satellite point moves at $V_{gd}=VR_E/a$, slower than the spacecraft. One line takes $t_s=p/V_{gd}$ for a ground pixel $p$, so with $N_{pix}$ pixels, $b$ bits per pixel and $N_{bands}$ bands,

$$
R_b=\frac{N_{pix}\,b\,N_{bands}}{t_s}.
$$

The workbook's three-band, 19 500-pixel, 8-bit imager with 26.9 m pixels at 619 km has $t_s=3.91$ ms and produces 120 Mbit/s. Finer pixels raise the rate sharply: the 1 m military imager produces about 1 Gbit/s.

The rate must fit the downlink set by the link budget, or be stored and downlinked over ground-station passes. If it does not fit, the data is reduced by lossless coding, fewer bits per pixel (8 to 6 bits cuts 25 %), summing pixels or bands, imaging only land or cloud-free areas, or relaying through data-relay satellites.

## Related

- [[SESA2024 14 - Orbit Control, Drag and Payload Data Rate#3. Payload data rate|Data rate in the topic note]]
- [[Swath Width and Push-Broom Imaging]] · [[Bit Error Rate and Eb-N0]] · [[Link Budget Equation]]
