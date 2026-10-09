---
title: "Rocket Mass Fractions"
module: "SESA1015 Intro to Aero & Astro"
type: concept
tags: [sesa1015, rocket, mass-fraction]
aliases: ["Rocket Mass Bookkeeping", "Structural Coefficient"]
date: 2026-09-27
status: complete
parent: ["[[SESA1015 A04 - Rocket Equation and Launch Performance]]", "[[SESA1015 A05 - Staging and Payload Fraction]]"]
sources: ["02 - Sources/Astronautics/Astronautics - Part 3 - Launch Vehicles.pdf"]
---

# Rocket Mass Fractions

For one stage and what it carries,

$$m_0=m_p+m_s+m_L.$$

Useful definitions:

$$\epsilon=\frac{m_s}{m_s+m_p}\quad\text{(structural coefficient)},$$

$$\lambda=\frac{m_L}{m_0}\quad\text{(payload ratio)},$$

$$MR=\frac{m_0}{m_f}=\frac{m_p+m_s+m_L}{m_s+m_L}.$$

Then

$$\Delta v=c\ln(MR).$$

Payload and dry structure remain in final mass for that burn. For a lower stage, $m_L$ includes the complete wet upper stack, not merely the final satellite.

> [!tip] Mass timeline
> Write ignition, burnout and post-separation masses before calculating any mass ratio.

