---
title: "Earth Orbit Zones"
module: "SESA1015 Intro to Aero & Astro"
type: concept
stream: "Astronautics"
aliases: ["LEO", "MEO", "GEO", "HEO", "Orbit zones", "Low Earth Orbit", "Geostationary Earth Orbit"]
tags: [sesa1015, concept, astronautics, orbits]
status: complete
parent_lectures: ["[[SESA1015 A01 - Astronautics Foundations, Missions and Applications]]"]
related_concepts: ["[[Kepler's Laws]]", "[[Keplerian Orbital Elements]]", "[[Space Mission Architecture]]", "[[Van Allen Radiation Belts]]"]
sources: ["Astronautics Part 1 (Introduction), pp. 4–7"]
---

# Earth Orbit Zones

Earth orbits are grouped by altitude into Low Earth Orbit (LEO, about 160/200 to 2000 km), Medium Earth Orbit (MEO, between LEO and GEO), Geostationary Earth Orbit (GEO, radius 42 164 km) and, in this course, Highly Eccentric Orbit (HEO), whose altitude swings from low perigee to high apogee.

For a circular orbit of radius $r=R_E+h$, gravity supplies the centripetal force, $\mu m/r^2=mv^2/r$, so $v=\sqrt{\mu/r}$ and $T=2\pi\sqrt{r^3/\mu}$ with $\mu=398\,600$ km³/s² and $R_E=6378$ km. This fixes the character of each zone. LEO orbits move at 7.8 to 6.9 km/s and take 88 to 127 min (the ISS at 400 km: 7.67 km/s, 92.6 min, 15.6 orbits a day). A GPS orbit at 20 200 km has a 12 h period. GEO is the radius at which the period equals the sidereal day of 86 164 s, $r=(\mu T^2/4\pi^2)^{1/3}=42\,164$ km, altitude 35 786 km, speed 3.07 km/s; on an equatorial, prograde orbit the satellite then stays over one point of the equator. Using the 86 400 s solar day by mistake gives 42 241 km.

The bounds come from the environment. Below about 160 to 200 km, drag in the residual atmosphere brings a satellite down within days; the Kármán line at 100 km ($r=6478$ km) is the conventional edge of space. The 2000 km top of LEO keeps it under the inner Van Allen belt, while GEO lies in the outer electron belt and highly eccentric orbits cross both belts twice per revolution ([[Van Allen Radiation Belts]]). Each zone suits particular applications: LEO for Earth observation, crewed stations and large broadband constellations; MEO for navigation; GEO for communications and weather; HEO for long dwell over high latitudes.

The orbit-zone figure on p. 6 of Part 1 labels the region beyond GEO "High Earth Orbit", but HEO is used here for Highly Eccentric Orbit throughout, so HEO is defined by its shape, not its height.

## Related

- Topic: [[SESA1015 A01 - Astronautics Foundations, Missions and Applications]] (§2)
- Concepts: [[Kepler's Laws]] · [[Keplerian Orbital Elements]] · [[Van Allen Radiation Belts]] · [[Space Mission Architecture]] · [[Sun-Synchronous Orbit]]
- Later: [[SESA2024 02 - Kepler's Laws and the Orbit Equation]] · [[SESA2024 11 - Payload and Orbit Selection]]
- Sources: Astronautics Part 1, pp. 4–7
