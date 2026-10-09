---
title: "SESA2024 03 - Orbital Elements and Conic Sections"
module: "SESA2024 Astronautics"
type: topic
stream: "Mission Analysis"
order: 3
tags:
  - sesa2024
  - orbital-mechanics
  - orbital-elements
aliases: ["Keplerian elements", "Conic sections", "Chapter 5 Lectures 3-4"]
date: 2026-09-25
status: complete
parent: ["[[SESA2024 Astronautics Hub]]"]
prerequisites: ["[[SESA2024 02 - Kepler's Laws and the Orbit Equation]]"]
next_topics: ["[[SESA2024 04 - Orbital Energy and the Vis-Viva Equation]]"]
key_concepts: ["[[Keplerian Orbital Elements]]", "[[Orbit Equation and Conic Sections]]"]
tutorial_sheets: ["[[SESA2024 Workbook Ch5 - Mission Analysis Solutions]]"]
sources: ["02 - Sources/Lectures/Chapter 5/SESA2024 Astronautics - Chapter 5_orbital elements and conic sections_2025-26_V2.pdf"]
---

# SESA2024 03 - Orbital Elements and Conic Sections

> [!abstract] Summary
> Six classical (Keplerian) elements fix an orbit and the spacecraft's place on it:
> - **size and shape** in the plane: $a$, $e$;
> - **orientation** of the plane and ellipse: $i$, $\Omega$, $\omega$;
> - **position**: $\theta$.
>
> In an unperturbed (two-body) orbit only $\theta$ changes. Mission analysis assigns these values from the *payload's* requirements.
>
> The orbit equation is a general **conic**: circle ($e = 0$), ellipse ($0<e<1$), parabola ($e = 1$) or hyperbola ($e>1$).

## Key Concepts
- [[Keplerian Orbital Elements]] · [[Orbit Equation and Conic Sections]]

---

## 1. The six Keplerian elements
![[ast_orbital_elements_3d.png|620]]

| Element | Symbol | Describes | Datum / range |
|---|---|---|---|
| Semi-major axis | $a$ | **size** | $a = (r_p+r_a)/2$ |
| Eccentricity | $e$ | **shape** | $e = (r_a-r_p)/(r_a+r_p)$ |
| Inclination | $i$ | tilt of the orbit plane to the equator | 0–180°, measured at the ascending node |
| Right ascension of the ascending node (RAAN) | $\Omega$ | where the orbit crosses the equator S→N | from the **First Point of Aries ♈** (Sun direction at the spring equinox, in the equatorial plane) |
| Argument of perigee | $\omega$ | where perigee is within the plane | from the ascending node, in the orbit plane |
| True anomaly | $\theta$ | the spacecraft's position | from perigee, in the orbit plane |

- **Apses**: perigee and apogee (Earth); perihelion and aphelion (Sun); periapsis and apoapsis (general).
- **$i < 90^\circ$** is **prograde** (moving with Earth's rotation). **$i > 90^\circ$** is **retrograde**; all Sun-synchronous orbits are retrograde.

### Apsis radii
From $r = a(1-e^2)/(1+e\cos\theta)$:

$$
r_p = a(1-e)\ (\theta = 0^\circ),\qquad r_a = a(1+e)\ (\theta = 180^\circ)
$$

### Undefined elements
- As $i\to0$, **$\Omega$ is undefined**: there is no node.
- As $e\to0$, **$\omega$ is undefined**: there is no perigee.
- Alternative element sets are used for these cases. (This is why a circular Sun-synchronous orbit "has no $\omega$".)

## 2. Real examples

| Object | $a$ | $e$ | $i$ | $\Omega$ | $\omega$ |
|---|---|---|---|---|---|
| Earth (heliocentric) | 149.6 × 10⁶ km | 0.0167 | 7.1° to Sun's equator | 174.9° | 288.1° |
| Mercury | 69.8 × 10⁶ km | 0.2 | 7° | 48° | 29° |
| Starlink v2 | 6861 km | ≈ 0 | 43°, 53°, 70° | varies | – |
| QZSS | 42 164 km | 0.075 | 43° | varies | 270° |
| ISS | 6780 km | 0.00048 | 51° | 0.9° | 353° |
| Comet NEOWISE | 270 AU | 0.9992 | 128° | 61° | 37° |
| 1I/ʻOumuamua | −1.27 AU | **1.201** | 123° | – | 241° |

- ʻOumuamua has a **negative $a$ and $e>1$**, so it is on a hyperbolic (interstellar) trajectory.
- QZSS is geosynchronous but inclined and eccentric, with $\omega$ = 270°. It dwells over Japan near apogee.

## 3. Common orbit categories
1. **LEO, near-equatorial**: parking orbits.
2. **LEO, moderately inclined (about 50°)**: space stations, comms constellations (Starlink).
3. **LEO, near-polar**: Earth observation, comms (Iridium, OneWeb).
4. **HEO (highly eccentric)**: observatories and science missions; comms at high latitude (Molniya).
5. **Semi-synchronous (12 h)**: navigation (GPS).
6. **GEO**: equatorial, circular, $r = 6.6R_E$ = 42 164 km, $\tau$ = 23 h 56 min. Used for comms and weather/EO (Meteosat).

(Exam question: "Describe with sketches four commonly used operational orbits…", 2013/14 and 2018/19, 8 marks.)

## 4. Conic sections
The orbit equation is the polar equation of a **conic section**, the intersection of a cone with a plane:

$$
r = \frac{p}{1+e\cos\theta},\qquad p = a(1-e^2) = h^2/\mu
$$

| $e$ | Conic | $a$ | Energy $\varepsilon = -\mu/2a$ | Physically |
|---|---|---|---|---|
| 0 | circle | $r$ | < 0 | idealisation (Venus, $e$ = 0.007, is nearly circular) |
| 0–1 | ellipse | > 0 | < 0 | closed, bound orbit |
| 1 | parabola | ∞ | 0 | escape at exactly escape speed; idealisation (NEOWISE $e$ = 0.999) |
| > 1 | hyperbola | < 0 | > 0 | unbound fly-by or escape (ʻOumuamua) |

![[ast_conic_sections.png|520]]

- "Exactly circular" and "exactly parabolic" orbits are **not physically feasible**: $e$ would have to be exactly 0 or 1.
- The course concentrates on $0\le e<1$.

## 5. Orbit visualisation tools
The Blackboard Excel tools are not in the vault:
- the orbit visualiser (enter elements, step $\theta$, see $\mathbf r$, $\mathbf V$, $\mathbf h$, the eccentricity vector and the node);
- a ΔV version (tangential burn → new orbit);
- a Hohmann version.

Their purpose is to build intuition. For example: raising $a$ at fixed $r_p$ lowers the speed at apogee; a tangential burn at a point keeps that point common to both orbits.

> [!example] Reading elements from a figure (2023/24 A3, 2024/25 A3)
> Given a sketch of an orbit at noon on the spring equinox (Sun direction = ♈ = $x$-axis):
> - $a$ from $(r_p+r_a)/2$ measured against the Earth's radius;
> - $e = (r_a-r_p)/(r_a+r_p)$;
> - $i$ from the tilt of the plane;
> - $\Omega$ as the angle from the Sun line to the ascending node;
> - $\omega$ from the node to perigee;
> - $\theta$ from perigee to the satellite.
>
> Answers within 10–25 % earn the marks.

## Links
- Parent: [[SESA2024 Astronautics Hub]] · Previous: [[SESA2024 02 - Kepler's Laws and the Orbit Equation]] · Next: [[SESA2024 04 - Orbital Energy and the Vis-Viva Equation]]
- Choosing elements from payload needs: [[SESA2024 11 - Payload and Orbit Selection]], [[SESA2024 13 - Calculating Orbital Elements for a Remote Sensing Mission]]

## Sources
- Chapter 5 Lectures 3–4 (orbital elements and conic sections); Heavens-Above for live element sets
