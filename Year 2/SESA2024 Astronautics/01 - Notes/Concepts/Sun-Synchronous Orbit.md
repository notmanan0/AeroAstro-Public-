---
title: "Sun-Synchronous Orbit"
module: "SESA2024 Astronautics"
type: concept
stream: "Remote Sensing Case Study"
aliases: ["SSO", "Sun synchronism", "sun-synchronous", "Sun-synchronous inclination"]
tags: [sesa2024, concept, orbital-mechanics, remote-sensing]
status: lectured
parent_lectures: ["[[SESA2024 12 - Sun- and Earth-Synchronous Orbits]]"]
related_concepts: ["[[Nodal Regression (J2)]]", "[[Repeat Ground Track]]", "[[Local Solar Time and RAAN]]"]
sources: ["02 - Sources/Lectures/Chapter 11/SESA2024 Astronautics - Chapter 11_Sun and Earth synchronous orbits_V1.pdf"]
---

# Sun-Synchronous Orbit

A Sun-synchronous orbit is one whose plane turns eastwards once a year, so that the angle between the plane and the Earth–Sun line stays constant and the spacecraft crosses any given latitude at the same local solar time on every pass.

Remote sensing wants it because change detection needs the same illumination, shadow length and direction on every image of a target. The condition $\phi=\alpha_S-\Omega=$ constant gives $\dot\Omega=\dot\alpha_S=360^\circ/365.25\ \mathrm d=0.9856^\circ$ per day. Thrusting the plane round would cost far too much propellant; instead the Earth's oblateness ($J_2$) makes the node regress at

$$
\dot\Omega=-2.0647\times10^{14}\,a^{-7/2}\cos i\quad(\text{deg/day},\ a\text{ in km}),
$$

which is eastwards only if $\cos i<0$. So Sun-synchronous orbits are retrograde, with $i$ a little over $90^\circ$: about $96^\circ$ at 200 km, $98.2^\circ$ at 700 km and $99.0^\circ$ at 900 km. That inclination still covers almost the whole globe.

The constant angle is chosen through the local solar time of the node, which sets the illumination and the eclipse; the orbit is usually also made Earth-synchronous, which then requires $\tau=(M/N)\times86\,400$ s. Seasonal changes in the Sun's elevation remain.

![[ast_sso_inclination.png|560]]

## Related

- [[SESA2024 12 - Sun- and Earth-Synchronous Orbits#1. Sun-synchronism|Sun-synchronism in the lecture note]] · [[SESA2024 12 - Sun- and Earth-Synchronous Orbits#Inclination for 700 to 900 km|Worked inclinations]]
- [[Nodal Regression (J2)]] · [[Repeat Ground Track]] · [[Local Solar Time and RAAN]]
