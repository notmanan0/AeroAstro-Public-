---
title: "Take-off Ground Run"
module: "SESA1015 Intro to Aero & Astro"
type: concept
tags: [sesa1015, takeoff, ground-run]
aliases: ["Takeoff Ground Roll"]
date: 2026-09-27
status: complete
parent: ["[[SESA1015 M09 - Take-off and Landing Performance]]"]
sources: ["02 - Sources/Mechanics of Flight/Mechanics of Flight - Course Notes.pdf"]
---

# Take-off Ground Run

The runway-axis equation is

$$m\dot V=T-D-\mu(W-L).$$

Using $\dot V=VdV/ds$,

$$\boxed{s_g=\int_0^{V_{LOF}}\frac{mV\,dV}{T-D-\mu(W-L)}}.$$

For constant $T,C_L,C_D$, set

$$A=T-\mu W,\qquad B=\frac12\rho S(C_D-\mu C_L)$$

to obtain

$$s_g=\frac{m}{2B}\ln\frac{A}{A-BV_{LOF}^2}.$$

Lift reduces wheel load and rolling resistance as speed builds. Lift-off speed is normally a stated margin above stall speed.

### Trend check

Higher weight or density altitude increases the target true airspeed and normally lengthens the roll; higher $C_{L,max}$ reduces it.

