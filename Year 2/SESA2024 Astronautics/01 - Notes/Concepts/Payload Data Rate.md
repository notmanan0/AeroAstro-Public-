---
title: "Payload Data Rate"
module: "SESA2024 Astronautics"
type: concept
stream: "Remote Sensing Case Study"
aliases: ["data rate", "uncompressed data rate", "sampling time", "ground speed", "data compression"]
tags: [sesa2024, concept, remote-sensing, payload]
status: complete
parent_lectures: ["[[SESA2024 14 - Orbit Control, Drag and Payload Data Rate]]"]
related_concepts: ["[[Swath Width and Push-Broom Imaging]]", "[[Bit Error Rate and Eb-N0]]", "[[Link Budget Equation]]"]
sources: ["02 - Sources/Lectures/SESA2024 Astronautics PROBLEM SHEET WORKBOOK 2025-26 V1.1.pdf"]
---

# Payload Data Rate

## Definition

> [!note] Definition
> $$V_{gd} = \sqrt{\frac{\mu}{a}}\,\frac{R_E}{a},\qquad t_s = \frac{p}{V_{gd}},\qquad R_b = \frac{N_{px}\cdot b\cdot N_{bands}}{t_s}$$
> - $p$ = ground pixel size;
> - $b$ = bits per pixel (or per pixel pair);
> - $N_{px}$ = pixels read per line.

## Explanation
- The sub-satellite point moves more slowly than the spacecraft, by the factor $R_E/a$.
- One image line is read every time the ground track advances one pixel.
- $R_b\propto1/p^2$ for a fixed swath: halving the pixel size doubles the pixels per line *and* the line rate.
- **Paired sampling**: if elements are read in pairs into one word, the words per line are $N/2$ and the ground pixel is two elements wide.
- **Reducing the rate**:
  - fewer bits per pixel;
  - lossless compression (DPCM, entropy coding);
  - binning pixels;
  - dropping or merging bands;
  - imaging only a duty cycle (land, cloud-free);
  - storing and dumping through ground stations or GEO relays (EDRS, TDRSS).

## Examples
| Case | $p$ | $t_s$ | $R_b$ |
|---|---|---|---|
| Workbook civil (19 500 × 3 bands × 8 bit) | 26.9 m | 3.91 ms | **119.6 Mbps** |
| Workbook military (20 000 × 7 bit) | 1.0 m | 0.136 ms | **1.03 Gbps** |
| Handwritten civil (19 500 × 8 bit, one band) | 22 m | 3.1 ms | 50 Mbps |

- Storage: 360 GB at 1.03 Gbps fills in about 46 min.
- A ground-station pass (10° elevation, 277 km) lasts only 277 s.

## Related
- [[Swath Width and Push-Broom Imaging]] · [[Bit Error Rate and Eb-N0]] · [[Link Budget Equation]]

## Sources
- Workbook Ch11B; past papers 2013/14, 2014/15, 2016/17, 2017/18, 2018/19, 2019/20
