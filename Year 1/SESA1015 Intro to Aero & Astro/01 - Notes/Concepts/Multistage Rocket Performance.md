---
title: "Multistage Rocket Performance"
module: "SESA1015 Intro to Aero & Astro"
type: concept
tags: [sesa1015, rocket, staging]
aliases: ["Multistage Delta-v"]
date: 2026-09-27
status: complete
parent: ["[[SESA1015 A05 - Staging and Payload Fraction]]"]
sources: ["02 - Sources/Astronautics/Astronautics - Part 3 - Launch Vehicles.pdf"]
---

# Multistage Rocket Performance

For ideal sequential stages,

$$\boxed{\Delta v_{total}=\sum_i c_i\ln\frac{m_{0,i}}{m_{f,i}}}.$$

Each lower-stage initial mass contains all upper stages and payload. At its burnout, its final mass still includes its own dry mass until separation.

Staging improves performance because spent dry mass is discarded before later acceleration. It also adds:

- duplicate engines/tanks/avionics;
- separation mass and failure modes;
- integration and operations complexity.

The ideal sum must exceed mission $\Delta v$ plus gravity, drag, steering, residual and reserve allowances.

For deeper optimisation, see [[SESA2023 W10 - Rocket Performance, Staging and Power Cycles]].

