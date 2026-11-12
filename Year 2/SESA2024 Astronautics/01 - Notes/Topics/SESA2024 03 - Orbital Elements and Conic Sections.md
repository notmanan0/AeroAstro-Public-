---
title: "SESA2024 03 - Orbital Elements and Conic Sections"
module: "SESA2024 Astronautics"
type: topic
stream: "Mission Analysis"
order: 3
tags: [sesa2024, orbital-mechanics, orbital-elements, conic-sections]
aliases: ["Keplerian elements", "Orbital elements", "Chapter 5 Lectures 3-4", "Conic sections"]
date: 2026-10-30
status: lectured
coverage: "Week 5 (2025-10-28, second half; 2025-10-30)"
parent: ["[[SESA2024 Astronautics Hub]]"]
prerequisites: ["[[SESA2024 02 - Kepler's Laws and the Orbit Equation]]"]
next_topics: ["[[SESA2024 04 - Orbital Energy and the Vis-Viva Equation]]"]
key_concepts: ["[[Keplerian Orbital Elements]]", "[[Orbit Equation and Conic Sections]]"]
tutorial_sheets: ["[[SESA2024 Workbook Ch5 - Mission Analysis Solutions]]"]
sources: ["02 - Sources/Lectures/Chapter 5/SESA2024 Astronautics - Chapter 5_orbital elements and conic sections_2025-26_V2.pdf", "02 - Sources/Lectures/SESA2024 Lecture 2025-10-28 - 1200.txt", "02 - Sources/Lectures/SESA2024 Lecture 2025-10-30.txt", "02 - Sources/Lectures/SESA2024 Lecture 2025-11-11 - Quiz 2 Worked Solutions.txt"]
---

# SESA2024 03 - Orbital Elements and Conic Sections

> [!abstract] Summary
> Six Keplerian elements fix an orbit and the spacecraft's place on it: $a$ and $e$ give its size and shape, $i$, $\Omega$ and $\omega$ orient the plane and the ellipse against the equator and the First Point of Aries, and the true anomaly $\theta$ says where the spacecraft is. Choosing them is what mission analysis means. The orbit equation is the polar form of a conic section, so the same equation covers circles, ellipses, parabolas and hyperbolas, distinguished by $e$.

> [!summary]- Exam use: quick path
> - **Use it when:** you must name or read off orbital elements, find $r_p$ and $r_a$, classify an orbit by $e$, or describe the common operational orbits.
> - **Assumptions:** two-body, unperturbed motion, so only $\theta$ changes with time; angles measured in the stated planes and from the stated datums.
> - **Method:** 1. Size and shape: $a=(r_p+r_a)/2$, $e=(r_a-r_p)/(r_a+r_p)$. 2. $i$: angle between the orbit plane and the equator at the ascending node. 3. $\Omega$: from the First Point of Aries to the ascending node, in the equatorial plane. 4. $\omega$: from the ascending node to periapsis, in the orbit plane. 5. $\theta$: from periapsis to the spacecraft, in the orbit plane.
> - **Common mistakes:** measuring $\omega$ from Aries instead of from the node; quoting $\Omega$ for an equatorial orbit or $\omega$ for a circular one, where they are undefined.
> - **Practise:** [[#Worked examples]] · [[SESA2024 2024-25 Exam Solutions#Section A|2024/25 A3]]

The orbit equation ([[SESA2024 02 - Kepler's Laws and the Orbit Equation]]) describes an ellipse in its own plane, with $\theta$ measured from periapsis. That says nothing about where the plane sits in space, or which way the ellipse points within it. The orbit can be pictured as a bent hoop around a globe (2025-10-28, ll. 641–700). With the hoop lying in the equatorial plane, $a$, $e$ and $\theta$ are enough. Tilting it adds an inclination. Spinning the tilted hoop about the polar axis calls for a reference direction to say where it crosses the equator. Rotating the ellipse within its own plane calls for the direction of periapsis. That makes six numbers.

Mission analysis is the job of choosing those six numbers for a spacecraft. The choice is generally driven by the payload requirements, with systems constraints such as thermal limits pushing back (2025-10-28, ll. 521–560). The choice for a remote-sensing satellite is worked through in [[SESA2024 13 - Calculating Orbital Elements for a Remote Sensing Mission]].

## 1. The in-plane elements: a, e and θ

The semi-major axis $a$ sets the size of the orbit and, through Kepler's third law, its period. The eccentricity $e$ sets its shape. The true anomaly $\theta$ is the angle from periapsis to the spacecraft, measured at the focus in the direction of motion; it is the only element that changes in an unperturbed orbit (2025-10-28, ll. 561–620).

The apses are the two ends of the major axis. From the orbit equation $r=a(1-e^2)/(1+e\cos\theta)$, periapsis is at $\theta=0$ where $\cos\theta=1$:

$$
r_p=\frac{a(1-e^2)}{1+e}=\frac{a(1-e)(1+e)}{1+e}=a(1-e).
$$

Apoapsis is at $\theta=180^\circ$ where $\cos\theta=-1$:

$$
r_a=\frac{a(1-e)(1+e)}{1-e}=a(1+e).
$$

In both cases $1-e^2$ is factorised as $(1-e)(1+e)$ and the matching factor cancels (2025-10-30, ll. 23–66).

The names of the apses depend on the central body (2025-10-28, ll. 611–645): perigee and apogee for the Earth, perihelion and aphelion for the Sun, perilune and apolune for the Moon, perijove and apojove for Jupiter, and periapsis and apoapsis in general.

## 2. The orientation elements: i, Ω and ω

![[ast_orbital_elements_3d.png|700]]

The inclination $i$ is the tilt of the orbit plane relative to the equator, measured at the ascending node: $0^\circ$ for an equatorial orbit going round with the Earth, $90^\circ$ for a polar orbit, and up to $180^\circ$. Orbits with $i<90^\circ$ are prograde, moving eastwards with the Earth's rotation; those with $i>90^\circ$ are retrograde, which includes every Sun-synchronous orbit ([[SESA2024 12 - Sun- and Earth-Synchronous Orbits]]).

The right ascension of the ascending node (RAAN) $\Omega$ locates the ascending node, the point where the spacecraft crosses the equator going from the southern to the northern hemisphere. It is measured in the equatorial plane, eastwards from a fixed inertial direction (2025-10-28, ll. 681–720). In effect it is the reference angle that fixes where the orbit plane sits around the polar axis.

The reference direction is the First Point of Aries, ♈. The Earth's axis is tilted by about $23.4^\circ$ and keeps pointing the same way in space as the Earth goes round the Sun. At the June solstice the northern hemisphere leans towards the Sun, and at the December solstice away from it. At the March (spring) equinox, around 20 March, it leans neither way, and the line from the Earth to the Sun then lies in the equatorial plane. That line, extended to the stars, is the First Point of Aries. It makes a natural zero because at the equinox the Sun direction lies in both the equator and the ecliptic, so it is the line of intersection of the two planes (ll. 881–900).

The name comes from antiquity, when the Sun at the March equinox lay in the constellation Aries. The equinoxes precess, and that point is now in Pisces, but the name has stuck (ll. 821–845).

The argument of perigee $\omega$ locates periapsis within the orbit plane. It is measured in the direction of motion from the ascending node to periapsis (ll. 721–735), so it shows whether the apoapsis dwells over the northern or the southern hemisphere. With $\omega=270^\circ$, periapsis is at the most southerly point of the orbit and apoapsis at the most northerly, which is how Molniya and QZSS orbits spend long periods over high northern latitudes.

The six elements are also loosely called the ephemerides. The equivalent state vector, three Cartesian position components and three velocity components, carries the same information (2025-10-30, ll. 507–520).

### When elements are undefined

Two elements lose their meaning in common special cases (2025-10-30, ll. 67–110). If $i=0$ the orbit lies in the equator and never crosses it, so there is no ascending node and $\Omega$ is undefined. If $e=0$ the orbit is a circle with no closest point, so $\omega$ is undefined, and $\theta$ has no periapsis to be measured from. A geostationary orbit has both problems, since it is equatorial and very nearly circular. Different element sets are used for such orbits. A Sun-synchronous orbit is near-circular, so its $\omega$ is not specified.

The elements are also only constant if the motion is unperturbed, which strictly requires two point masses alone in the universe. Any other body, a non-spherical Earth, or drag perturbs them (ll. 111–130). A Sun-synchronous orbit uses the Earth's oblateness deliberately to turn $\Omega$ at the rate needed to follow the Sun.

## 3. Elements of real objects and what perturbations revealed

Elements of planets and spacecraft (slides; 2025-10-30, ll. 111–485):

| Object | $a$ | $e$ | $i$ | $\Omega$ | $\omega$ |
|---|---|---|---|---|---|
| Earth (around the Sun) | $149.6\times10^6$ km (1 AU) | 0.0167 | 7.1° to the Sun's equator (0° to the ecliptic, by definition) | 174.9° | 288.1° |
| Uranus | $2.87\times10^9$ km (19.2 AU) | 0.047 | 6.5° to the Sun's equator | 74° | 97° |
| Mercury | $57.9\times10^6$ km | 0.21 | 7° to the Sun's equator | 48° | 29° |
| Starlink | 6861 km | ≈ 0 | 43°, 53°, 70° | varies | — |
| QZSS | 42 164 km | 0.075 | 43° | varies | 270° |
| ISS | 6780 km | 0.00048 | 51° | 0.9° | 353° |
| Comet NEOWISE | 270 AU (inbound) | 0.9992 | 128° | 61° | 37° |
| 1I/ʻOumuamua | −1.27 AU | 1.201 | 123° | — | 241° |

The Earth reaches perihelion around 3 January and aphelion around 3 July. Counting from 3 January, the true anomaly on 30 October is about $300^\circ$.

> [!check] Earth's true anomaly on 30 October
> From 3 January to 30 October is 300 days. At the mean motion $n=360^\circ/365.25\ \mathrm d$ the angle swept would be $300\times360/365.25=295.7^\circ$. The real rate $\dot\theta=h/r^2$ is slightly faster than average near perihelion and slower near aphelion, but with $e=0.0167$ the difference is under $2^\circ$ (a numerical integration of $\dot\theta=h/r^2$ gives $294^\circ$), so "about $300^\circ$" is the right size.

The table gives radii, not altitudes. With $R_E=6378$ km, Starlink's $a=6861$ km is $6861-6378=483$ km up and the ISS's $a=6780$ km is $6780-6378=402$ km up.

Real orbits are perturbed, as two historical cases show. Uranus, found by William Herschel in 1781, was the first planet discovered since antiquity. Decades of observation showed it drifting off its ellipse, pulled forward and then held back by an unseen body. John Couch Adams and Urbain Le Verrier independently worked backwards from the perturbations to predict where that body must be, and the Berlin Observatory found Neptune within about a degree of Le Verrier's position (ll. 199–265). Le Verrier then tried to explain the slow precession of Mercury's perihelion by the same method and proposed an inner planet, Vulcan, which was never found. The real explanation was Einstein's general relativity, published in 1915, and Mercury's precession was one of its first successful tests (ll. 265–340).

The ISS inclination of $51.6^\circ$ illustrates a launch constraint (ll. 485–505). Launching straight east puts a spacecraft into an orbit with inclination equal to the launch-site latitude, and changing the plane afterwards costs a lot of ΔV, so high-inclination missions prefer high-latitude sites (Rocket Lab's New Zealand pad for polar orbits, for example). $51.6^\circ$ is often described as a compromise between the latitudes of Florida and Kazakhstan. More precisely, it is the lowest inclination that Russian launches from Baikonur ($45.6^\circ$ N) can reach while keeping spent stages away from China, and the Shuttle could still reach it from Florida ($28.5^\circ$ N) at a payload penalty.

## 4. Common operational orbits

There are six categories, which is also the answer to the eight-mark question "Describe with sketches four commonly used operational orbits" (2013/14 and 2018/19):

| Orbit | Typical elements | Used for |
|---|---|---|
| LEO, near-equatorial | a few hundred km, $i\approx0$ | parking orbits before GEO or deep-space departure |
| LEO, moderate inclination | about 400–550 km, $i\approx50^\circ$ | space stations (ISS, Tiangong), Starlink |
| LEO, near-polar | 500–900 km, $i\approx90^\circ$ or Sun-synchronous | Earth observation (whole-Earth coverage as the planet turns underneath), Iridium, OneWeb |
| HEO (highly eccentric) | large $e$, often $i=63.4^\circ$ and $\omega=270^\circ$ (Molniya) | observatories; communications at high latitudes where GEO is low on the horizon |
| Semi-synchronous | $\tau\approx12$ h, $a\approx26\,560$ km | navigation (GPS; Galileo, GLONASS and BeiDou fly nearby medium orbits with periods of about 11 to 14 h) |
| GEO | $i=0$, $e\approx0$, $a=42\,164$ km ($6.6R_E$), $\tau=23$ h 56 min | communications and weather: the satellite stays over one point and sees about a third of the Earth |

QZSS, Japan's regional navigation augmentation, is a variant: geosynchronous ($a=42\,164$ km) but inclined at $43^\circ$ and eccentric with $\omega=270^\circ$, so each satellite lingers near apoapsis over Japan and swings quickly past Australia. Three satellites spaced $120^\circ$ apart keep one high over Japan at all times (ll. 463–480).

## 5. Conic sections

The polar orbit equation $r=p/(1+e\cos\theta)$, with $p=a(1-e^2)=h^2/\mu$, is the equation of a conic section, the curve you get by slicing a cone with a plane (2025-10-30, ll. 551–600). A slice perpendicular to the cone's axis gives a circle, a tilted slice an ellipse, a slice parallel to the side a parabola, and a steeper slice a hyperbola.

![[ast_conic_sections.png|600]]

| $e$ | Conic | $a$ | Bound? | Example |
|---|---|---|---|---|
| 0 | circle | $=r$ | yes | idealisation; Venus has the lowest planetary $e$, 0.007 |
| $0<e<1$ | ellipse | $>0$ | yes | every planet and satellite |
| 1 | parabola | $\to\infty$ | just escapes | idealisation; comet NEOWISE, $e=0.9992$ |
| $>1$ | hyperbola | $<0$ | no | ʻOumuamua, $e=1.20$ |

The sign of $a$ in the table follows from the orbit equation itself. The semi-latus rectum $p=h^2/\mu$ is the radius at $\theta=90^\circ$, so it is positive and finite for every orbit with angular momentum. Write the definition and solve for $a$:

$$
p=a(1-e^2)
$$

$$
a=\frac{p}{1-e^2}.
$$

For $e<1$ the denominator is positive, so $a>0$. As $e\to1$ the denominator tends to zero with $p$ fixed, so $a\to\infty$: a parabola is an ellipse stretched until its far end never closes. For $e>1$ the denominator is negative, so $a<0$. The periapsis radius stays positive in every case, because

$$
r_p=\frac{p}{1+e\cos0}=\frac{p}{1+e}>0.
$$

Parabolas and hyperbolas have a direction in which the denominator $1+e\cos\theta$ reaches zero, at $\cos\theta=-1/e$ ($\theta=180^\circ$ for the parabola); there $r\to\infty$, which is the direction along which the object leaves. For an ellipse $1+e\cos\theta\ge1-e>0$, so $r$ stays finite all the way round.

Exactly circular and exactly parabolic orbits are not physically achievable, because $e$ would have to be exactly 0 or 1 and any perturbation moves it (ll. 595–615). Bound orbits, $0\le e<1$, are the ones that matter for Earth satellites.

The negative $a$ of a hyperbola follows from the apsis formula. For ʻOumuamua, $a=-1.27$ AU and $e=1.201$ give a perihelion radius $r_p=a(1-e)=(-1.27)(-0.201)=0.255$ AU, which is positive as it must be. ʻOumuamua, found in 2017, was the first object identified as coming from outside the Solar System; its light curve suggested a very elongated shape (ll. 617–660). NEOWISE came in from the Oort cloud on a near-parabolic orbit in 2020 and was the brightest comet seen from the northern hemisphere for decades.

## Worked examples

### The length of the year from Earth's elements

Take $a=149.6\times10^9\ \mathrm m$ and $\mu_S=1.327\times10^{20}\ \mathrm{m^3/s^2}$. The cube is

$$
a^3=(149.6\times10^9)^3=3.348\times10^{33}\ \mathrm{m^3},
$$

so

$$
\frac{a^3}{\mu_S}=\frac{3.348\times10^{33}}{1.327\times10^{20}}=2.523\times10^{13}\ \mathrm{s^2},
$$

$$
\tau=2\pi\sqrt{2.523\times10^{13}}=2\pi\times5.023\times10^6=3.156\times10^7\ \mathrm s.
$$

Divide by 3600 for 8767 hours, and by 24 for 365.28 days. The quarter day beyond 365 is why the calendar needs a leap day every four years; the remaining 0.03 day here is rounding in $a$ and $\mu$ (the sidereal year is 365.256 days).

### Apsis altitudes of QZSS and NEOWISE

For QZSS, $a=42\,164$ km and $e=0.075$:

$$
r_a=a(1+e)=45\,326\ \mathrm{km},\qquad r_p=a(1-e)=39\,002\ \mathrm{km},
$$

so the altitudes are $45\,326-6378=38\,948$ km and $39\,002-6378=32\,624$ km. For NEOWISE, $a=270$ AU and $e=0.9992$ give

$$
r_p=a(1-e)=270\times0.0008=0.216\ \mathrm{AU},\qquad r_a=a(1+e)=270\times1.9992=540\ \mathrm{AU},
$$

so its perihelion is closer to the Sun than Mercury's orbit (0.39 AU).

> [!check] Apsis sums
> $r_p+r_a$ must equal $2a$: for QZSS $39\,002+45\,326=84\,328=2\times42\,164$ km, and for NEOWISE $0.216+539.8=540.0=2\times270$ AU. For ʻOumuamua the same formula with $a=-1.27$ AU gives $r_p=(-1.27)(1-1.201)=0.255$ AU, positive as it must be.

### Quiz 2: argument of perigee of a polar orbit

A near-circular polar orbit passes over the North Pole at a known true anomaly, and $\omega$ is required (Quiz 2 walk-through, ll. 81–125). Viewed face-on, the orbit plane shows the geometry. For $i=90^\circ$ the orbit plane contains the polar axis, so the equator appears edge-on as a line through the Earth's centre, the ascending node is where the orbit crosses that line going north, and the North Pole is $90^\circ$ further round, measured in the orbit plane.

![[ast_polar_orbit_omega.png|560]]

The angle from node to spacecraft is the sum of two angles in the orbit plane, node to periapsis ($\omega$) and periapsis to spacecraft ($\theta$):

$$
\text{node to spacecraft}=\omega+\theta.
$$

Over the pole that angle is $90^\circ$:

$$
\omega+\theta=90^\circ
$$

$$
\omega=90^\circ-\theta.
$$

With $\theta=30^\circ$, as in the figure, $\omega=60^\circ$. If $\theta$ were larger than $90^\circ$ the formula would give a negative angle; add $360^\circ$ to bring it into the range $0$–$360^\circ$ (for example $\theta=120^\circ$ gives $\omega=330^\circ$, with periapsis just before the node).

A near-circular orbit still has a periapsis, because a perfect circle is impossible, so $\omega$ is defined even if it is poorly determined.

### Quiz 2: a circular orbit drawn in perspective

A circular orbit drawn at an angle looks elliptical, with the Earth at its centre (Quiz 2 multiple-choice question, ll. 1–20). An ellipse has the central body at a focus, not the centre, so an orbit centred on the Earth must have $e=0$; the apparent flattening is perspective.

## Links

- Parent: [[SESA2024 Astronautics Hub]]
- Previous: [[SESA2024 02 - Kepler's Laws and the Orbit Equation]]
- Next: [[SESA2024 04 - Orbital Energy and the Vis-Viva Equation]]
- Concepts: [[Keplerian Orbital Elements]] · [[Orbit Equation and Conic Sections]]
- Choosing the elements from payload needs: [[SESA2024 11 - Payload and Orbit Selection]] · [[SESA2024 13 - Calculating Orbital Elements for a Remote Sensing Mission]]

## Sources

- `Chapter 5_orbital elements and conic sections_2025-26_V2.pdf` (Dr C. Ryan, after Prof H. Lewis)
- Transcripts `SESA2024 Lecture 2025-10-28 - 1200.txt`, ll. 521–905 (elements, First Point of Aries demonstration) and `SESA2024 Lecture 2025-10-30.txt` (apses, undefined elements, examples, operational orbits, conic sections)
- `SESA2024 Lecture 2025-11-11 - Quiz 2 Worked Solutions.txt`
- Fortescue, Stark and Swinerd, *Spacecraft Systems Engineering*, Ch. 4 and Ch. 5; live element sets from Heavens-Above and satellitemap.space (shown in the lecture)
- Figures: `ast_orbital_elements_3d` and `ast_conic_sections` (`generate_ast_extra_figures.py`), `ast_polar_orbit_omega` (`generate_ast_ch5_elements_figures.py`). Numbers recomputed in Python, including a numerical integration of $\dot\theta=h/r^2$ for the Earth's true anomaly.

## Self-study tasks

### Core

- [ ] Quiz 2: argument of perigee of a near-circular polar orbit when the spacecraft is over the North Pole at a given $\theta$ (walk-through, ll. 81–125). → [[#Quiz 2: argument of perigee of a polar orbit]]
- [ ] Quiz 2: why does an Earth-centred orbit drawn in perspective have $e=0$? (ll. 1–20) → [[#Quiz 2: a circular orbit drawn in perspective]]
- [ ] Show $r_p=a(1-e)$ and $r_a=a(1+e)$ from the orbit equation (2025-10-30, ll. 23–66; Workbook Ch5 Q5). → [[#1. The in-plane elements: a, e and θ]] · [[SESA2024 Workbook Ch5 - Mission Analysis Solutions#Q5. Prove that the apoapsis radius is a(1+e)|Workbook solution]]
- [ ] Describe with sketches four commonly used operational orbits (2013/14 and 2018/19, 8 marks). → [[#4. Common operational orbits]]
- [ ] Read $a$, $e$, $i$, $\Omega$, $\omega$ and $\theta$ off a sketched orbit at the spring equinox (2024/25 A3). → [[#2. The orientation elements: i, Ω and ω]] · [[SESA2024 2024-25 Exam Solutions#Section A|2024/25 A3]]

### Further practice

- [ ] Compute the length of the Earth's year from $a$ and $\mu_S$ (done live, 2025-10-30, ll. 177–200). → [[#The length of the year from Earth's elements]]
- [ ] Say which elements are undefined for a geostationary orbit, and why (2025-10-30, ll. 67–110). → [[#When elements are undefined]]
- [ ] Explore the Blackboard Excel orbit visualiser: change $e$, $a$ and $\theta$ and watch $\mathbf r$, $\mathbf V$ and $\mathbf h$ (ll. 507–550). The tool is not in the vault.
- [ ] Classify an orbit by $e$ and $a$, and find the perihelion of a hyperbolic object with negative $a$. → [[#5. Conic sections]]

## Transcript and slide slips

> [!warning] Transcript slip (2025-10-30, l. 23)
> Where: [[#1. The in-plane elements: a, e and θ]].
>
> The lecture says that at periapsis "the cos of theta is equal to 0". It is $\theta$ that is zero there, so $\cos\theta=1$, which is what the algebra then uses.

> [!warning] Transcript slip (2025-10-28, l. 835)
> Where: [[#2. The orientation elements: i, Ω and ω]].
>
> The lecture attributes the definition to Hipparchus "in 230 BC". Hipparchus worked around 130 BC.

> [!warning] Source problems in the slide tables
> Where: [[#3. Elements of real objects and what perturbations revealed]].
>
> The Mercury slide gives $a=69.82$ million km, which is Mercury's aphelion distance; the semi-major axis is 57.9 million km. On the Uranus and Mercury slides the last three values sit one row out of line with their labels: the angle given against "Inclination" ($97^\circ$ for Uranus, $29^\circ$ for Mercury) is the argument of perihelion, and the angle given "to Sun's equator" is the inclination. The table above puts them in the right columns.

> [!warning] Transcript slips (2025-10-30, ll. 221–475)
> Where: [[#3. Elements of real objects and what perturbations revealed]].
>
> Uranus is said to be "a thousand times further away than the Earth is to the Sun"; at $2.87\times10^9$ km it is about 19 times as far. Neptune is said to have been found "in 1848"; Galle found it at Berlin in September 1846. Starlink at $a=6861$ km is said to be "about 530 kilometres up", and the ISS at $a=6780$ km "about 450 kilometres up"; with $R_E=6378$ km those altitudes are 483 km and 402 km.
