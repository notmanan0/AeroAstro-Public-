---
title: "Launch Environment Loads"
module: "SESA1015 Intro to Aero & Astro"
type: concept
tags: [sesa1015, launch, loads, vibration]
aliases: ["Launch Loads"]
date: 2026-09-27
status: complete
parent: ["[[SESA1015 A03 - Launch Environment]]"]
sources: ["02 - Sources/Astronautics/Astronautics - Part 2 - Environment.pdf"]
---

# Launch Environment Loads

Launch load types are not interchangeable:

- quasi-static acceleration: slowly varying inertial load $F=nmg$;
- sine vibration: discrete low-frequency forcing;
- random vibration: broadband PSD in $g^2/\mathrm{Hz}$;
- acoustic loading: distributed fluctuating pressure;
- shock: short high-frequency separation transient;
- aerodynamic loading: max-q, winds and angle of attack.

Random-vibration RMS is obtained from the PSD area:

$$a_{RMS}=\sqrt{\int_{f_1}^{f_2}G_a(f)\,df}.$$

Local response depends on structural modes, damping and interface stiffness. Qualification/acceptance evidence therefore combines analysis with appropriately shaped vibration, acoustic, shock and load tests.

> [!warning] Peak versus duration
> A high microsecond shock peak is not equivalent to the same acceleration sustained through a long burn.

