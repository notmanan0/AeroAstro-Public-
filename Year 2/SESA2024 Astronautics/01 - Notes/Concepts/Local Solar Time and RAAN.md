---
title: "Local Solar Time and RAAN"
module: "SESA2024 Astronautics"
type: concept
stream: "Remote Sensing Case Study"
aliases: ["LST", "local solar time", "node local time", "dawn-dusk orbit", "noon-midnight orbit", "10:30 orbit"]
tags: [sesa2024, concept, orbital-mechanics, remote-sensing]
status: lectured
parent_lectures: ["[[SESA2024 13 - Calculating Orbital Elements for a Remote Sensing Mission]]"]
related_concepts: ["[[Sun-Synchronous Orbit]]", "[[Keplerian Orbital Elements]]", "[[Eclipse Duration]]"]
sources: ["02 - Sources/Lectures/SESA2024 Lecture 8.txt", "02 - Sources/Lectures/Chapter 11/SESA2024 Astronautics - Chapter 11_Calculating Orbital Elements_Part 2_V1.pdf"]
---

# Local Solar Time and RAAN

The local solar time (LST) of an orbit's nodes is the solar time on the ground beneath the spacecraft as it crosses the equator; in a Sun-synchronous orbit it is fixed, and choosing it is how the right ascension of the ascending node is chosen.

Sun-synchronism keeps $\phi=\alpha_S-\Omega$ constant, so the plane sits at a fixed angle to the Earth–Sun line, and that angle is the node's LST expressed at $15^\circ$ per hour from noon. Knowing the Sun's right ascension on the launch date, $\Omega=\alpha_S-\phi$ at launch: a noon–midnight orbit has $\phi=0^\circ$ or $180^\circ$, a dawn–dusk orbit $90^\circ$ or $270^\circ$, and a 10:30 node $22.5^\circ$. At a spring-equinox launch ($\alpha_S=0$) a 10:30 descending node gives $\Omega=157.5^\circ$.

The LST is picked from the payload's needs. European optical missions favour a 10:30 descending node, arriving over Europe mid-morning with moderate shadows and before afternoon convective cloud. A dawn–dusk orbit rides the terminator, almost always sunlit, which suits radar and power-hungry missions and lets the array stay fixed. The choice sets the eclipse: about half the orbit for noon–midnight, about a third for 10:00, and short winter eclipses only for dawn–dusk, which then drives the battery, array and thermal design. A Sun-synchronous orbit keeps its node LST, so a 10:00 node stays at 10:00 (2024/25 A7).

![[ast_lst_orbit_planes.png|560]]

## Related

- [[SESA2024 13 - Calculating Orbital Elements for a Remote Sensing Mission#3. The remaining elements|LST and RAAN in the lecture note]] · [[SESA2024 13 - Calculating Orbital Elements for a Remote Sensing Mission#4. The LST sets the eclipse|Effect on eclipse]]
- [[Sun-Synchronous Orbit]] · [[Keplerian Orbital Elements]] · [[Eclipse Duration]]
