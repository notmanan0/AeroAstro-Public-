---
title: "Swath Width and Push-Broom Imaging"
module: "SESA2024 Astronautics"
type: concept
stream: "Remote Sensing Case Study"
aliases: ["swath width", "push-broom", "pushbroom", "field of view", "CCD imager", "global coverage", "spatial resolution"]
tags: [sesa2024, concept, remote-sensing, payload]
status: complete
parent_lectures: ["[[SESA2024 11 - Payload and Orbit Selection]]", "[[SESA2024 13 - Calculating Orbital Elements for a Remote Sensing Mission]]"]
related_concepts: ["[[Repeat Ground Track]]", "[[Payload Data Rate]]"]
sources: ["02 - Sources/Lectures/Chapter 11/SESA2024 Astronautics - Chapter 11_Calculating Orbital Elements_V1.pdf"]
---

# Swath Width and Push-Broom Imaging

## Definition

> [!note] Definition
> A **push-broom** imager has a linear detector array across-track. The spacecraft's motion sweeps it along-track.
> $$d = 2h\tan\frac{\beta}{2} = N_{px}\,p,\qquad n_{min} = \frac{2\pi R_E}{d}$$
> - $\beta$ = field of view;
> - $N_{px}$ = pixels (CCD elements) across-track;
> - $p$ = ground pixel size (spatial resolution) at nadir.

## Explanation
- **Advantage over whisk-broom or scanning**: no moving parts, and a long dwell time per pixel (the whole line time), which gives better SNR and geometric fidelity.
- **Coverage**: swaths must touch or overlap at the equator, where tracks are furthest apart. Hence $n\ge2\pi R_E/d$. Coverage fraction $= nd/2\pi R_E$.
- The design is coupled:
  - fixed $\beta$: higher $h$ means a wider swath (better coverage) but coarser pixels;
  - fixed $N_{px}$ and $p$: the swath is fixed, so $h = d/[2\tan(\beta/2)]$.
- Earth curvature is ignored in the course formulas.
- Multi-band instruments have one detector per band. "Paired sampling" (two elements per pixel word) halves the effective pixel count.

## Examples
- Lecture: $\beta$ = 28.96°, $h$ = 800 km, giving $d$ = 413.2 km and $n$ = 96.99.
- Workbook civil: 19 500 px × 20 m = 390 km, so $h$ = 460 km for the 45.95° FOV. Final 619 km, 524.8 km swath, 26.9 m pixels.
- 2017/18 Q4: 8000 elements × 10 m = **80 km**; global coverage every 31 days.
- 2019/20 B3(iv): 8 km swath at 2 m gives **4000 elements** per detector; at 700 km the FOV is $2\tan^{-1}(4/700)$ = **0.65°**.

## Related
- [[Repeat Ground Track]] · [[Payload Data Rate]]

## Sources
- Chapter 11 first pass and calculating orbital elements; workbook 11B
