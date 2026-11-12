---
title: "SESA1015 A01 - Astronautics Foundations, Missions and Applications"
module: "SESA1015 Intro to Aero & Astro"
type: topic
stream: "Astronautics"
order: 13
tags:
  - sesa1015
  - astronautics
  - orbits
  - missions
  - space-applications
aliases: ["SESA1015 Astronautics 1", "Astronautics Foundations", "Astronautics Introduction"]
date: 2026-09-27
status: lectured
coverage: "Astronautics Part 1 (Introduction), pp. 1–77: Earth's size and shape, the Kármán line, orbit zones (LEO, MEO, GEO, HEO), semi-major axis and inclination, the astronomical unit, seasons and terminology, the history of spaceflight (V-2 to the ISS and Shuttle), space agencies, science and exploration missions, commercial applications (communications, navigation, Earth observation, small satellites), recent highlights and future launch systems"
parent: ["[[SESA1015 Intro to Aero & Astro Hub]]"]
prerequisites: []
next_topics: ["[[SESA1015 A02 - Space Environment]]"]
key_concepts: ["[[Earth Orbit Zones]]", "[[Space Mission Architecture]]", "[[Kepler's Laws]]", "[[Keplerian Orbital Elements]]"]
tutorial_sheets: []
sources: ["02 - Sources/Astronautics/Astronautics - Part 1 - Introduction.pdf"]
---

# SESA1015 A01 - Astronautics Foundations, Missions and Applications

> [!abstract] Summary
> Space is conventionally taken to start at the Kármán line, 100 km above the surface ($r=6478$ km), and Earth orbits are grouped by altitude into LEO (about 160/200 to 2000 km), MEO, GEO ($r=42\,164$ km) and highly eccentric orbits (HEO). Balancing gravity against the centripetal requirement gives the circular-orbit speed $v=\sqrt{\mu/r}$ and period $T=2\pi\sqrt{r^3/\mu}$, so a 400 km orbit takes 92.6 min at 7.67 km/s and an orbit whose period equals the sidereal day sits at 42 164 km. Around these orbits sit the Sun–Earth geometry, sixty years of human and robotic missions, and the commercial services (communications, navigation, Earth observation) that now pay for most of spaceflight.

> [!summary]- Exam use: quick path
> - **Use it when:** a question asks for the speed, period or radius of a circular orbit, the altitude band of an orbit, the GEO radius, the payload mass fraction of a launcher, a distance in AU or a light time, or what a named mission or orbit is for.
> - **Assumptions:** circular orbit about a spherical Earth ($\mu=398\,600$ km$^3$/s$^2$, $R_E=6378$ km equatorial); altitude $h$ is measured from $R_E$, so $r=R_E+h$; GEO uses the sidereal day, 86 164 s, not 86 400 s.
> - **Method:** 1. Convert altitude to radius, $r=R_E+h$. 2. Speed $v=\sqrt{\mu/r}$. 3. Period $T=2\pi r/v=2\pi\sqrt{r^3/\mu}$. 4. For a required period, invert: $r=(\mu T^2/4\pi^2)^{1/3}$. 5. Check the answer against the zone: LEO about 7 to 8 km/s and 1.5 to 2 h, GEO 3.07 km/s and 23.93 h.
> - **Common mistakes:** using $h$ instead of $r$ in $\sqrt{\mu/r}$; using the 24 h solar day for GEO (gives 42 241 km, 77 km too high).
> - **Practise:** [[#Orbit numbers for the ISS and GEO]] · [[#Self-study tasks]]

The Earth is almost a sphere of radius 6378 km, flattened slightly at the poles. Above it the atmosphere thins roughly exponentially, and by 100 km it is too thin for a wing to fly: an aircraft would need orbital speed to generate enough lift, so the boundary between aeronautics and astronautics is drawn there. Anything that is to stay above that height without thrust must be in orbit, that is, falling around the Earth fast enough that the ground curves away beneath it as quickly as it falls. That single balance between gravity and the curvature of the path fixes the speed and the period of every circular orbit.

Orbits are chosen for what they let a spacecraft do. Low orbits give close views of the ground and short communication links but sweep past any one place in a few minutes; geostationary orbit, 36 000 km up, has a period equal to one rotation of the Earth, so the satellite hangs over one point on the equator, which suits broadcasting and weather imaging. Navigation constellations sit in between, in medium Earth orbit. The missions from Sputnik-era rocketry to Rosetta and the ISS each pick an orbit or trajectory to serve a purpose, and several show what goes wrong when one element of the system fails.

---

## 1. The Earth and where space begins

The Earth's equatorial radius is 6378 km and its polar radius 6357 km (Part 1, p. 3). The difference comes from rotation, which flattens the planet into an oblate spheroid. The flattening is

$$
f=\frac{R_{eq}-R_{pol}}{R_{eq}}
$$

$$
=\frac{6378-6357}{6378}
$$

$$
=0.00329\approx\frac{1}{304}.
$$

Positions on the surface use latitude (parallels, measured north or south of the equator) and longitude (meridians, measured east or west of the prime meridian through Greenwich).

The commonly used boundary of space is the **Kármán line**, 100 km (62 miles) above the surface (p. 4). Measured from the Earth's centre it lies at

$$
r=R_E+h=6378+100=6478\ \text{km}.
$$

The line is a convention, not a physical edge: density keeps falling smoothly above it (see [[SESA1015 A02 - Space Environment]]), and satellites below about 200 km decay within days because of drag. Even so, 100 km is a sensible choice because at that height an aeroplane would need nearly orbital speed (7.84 km/s from §2) to hold itself up aerodynamically.

## 2. Circular orbits and the orbit zones

![[astro_a01_orbit_zones.png|900]]

### Circular-orbit speed and period

Take a satellite of mass $m$ in a circular orbit of radius $r$ about a spherical Earth of mass $M$. The only force is gravity, directed towards the centre:

$$
F=\frac{GMm}{r^2}=\frac{\mu m}{r^2},\qquad \mu=GM=398\,600\ \text{km}^3/\text{s}^2 .
$$

Uniform motion on a circle at speed $v$ needs a centripetal force $mv^2/r$ towards the centre. Gravity supplies it, so

$$
\frac{\mu m}{r^2}=\frac{mv^2}{r}.
$$

Cancel $m$ and multiply by $r$:

$$
v^2=\frac{\mu}{r},
$$

$$
v=\sqrt{\frac{\mu}{r}} .
$$

The period is the circumference divided by the speed:

$$
T=\frac{2\pi r}{v}
$$

$$
=2\pi r\sqrt{\frac{r}{\mu}}
$$

$$
=2\pi\sqrt{\frac{r^3}{\mu}} .
$$

The satellite's mass has dropped out, so a spanner and a space station at the same radius orbit together. Speed falls as $r^{-1/2}$ and period grows as $r^{3/2}$, which is [[Kepler's Laws|Kepler's third law]] for a circle.

![[astro_a01_circular_speed_period.png|900]]

### The zones

Earth orbits are grouped by altitude (pp. 5–6):

| Zone | Altitude or radius | Circular speed | Period | Typical use |
|---|---|---|---|---|
| LEO, Low Earth Orbit | about 160/200 to 2000 km altitude | 7.81 to 6.90 km/s | 88 to 127 min | ISS (about 400 km), Earth observation, small satellites |
| MEO, Medium Earth Orbit | between LEO and GEO | e.g. 3.87 km/s at 20 200 km | 12 h at 20 200 km | navigation (GPS, Galileo, GLONASS) |
| GEO, Geostationary Earth Orbit | radius 42 164 km (altitude 35 786 km) | 3.07 km/s | 23.93 h | communications, weather (Meteosat) |
| HEO, Highly Eccentric Orbit | elliptical, low perigee and high apogee | varies around the orbit | hours | high-latitude coverage, science |

The lower edge of LEO is set by drag: below about 160 to 200 km the residual atmosphere brings a satellite down within days. The upper edge, 2000 km, keeps LEO under the inner Van Allen belt ([[SESA1015 A02 - Space Environment#4. The magnetic field and trapped radiation|A02 §4]]). HEO here means Highly Eccentric Orbit; some figures use it for "High Earth Orbit", the region beyond GEO (p. 6 footnote).

### Why GEO sits at 42 164 km

A satellite stays over one point on the equator if its orbit is circular, equatorial, prograde and has a period equal to one rotation of the Earth relative to the stars. That rotation, the **sidereal day**, is shorter than the 24 h solar day. In one solar day the Earth moves about $360°/365.256=0.986°$ along its orbit round the Sun, so to bring the Sun back to the same meridian the Earth has to turn through $360.986°$, not $360°$. Turning through $360°$ therefore takes

$$
T_{sid}=\frac{86\,400}{1+1/365.256}
$$

$$
=86\,164\ \text{s}=23\ \text{h}\ 56\ \text{min}\ 4\ \text{s}.
$$

Setting $T=T_{sid}$ in the period formula and solving for $r$:

$$
T^2=\frac{4\pi^2r^3}{\mu}
$$

$$
r^3=\frac{\mu T^2}{4\pi^2}
$$

$$
r=\left(\frac{\mu T_{sid}^2}{4\pi^2}\right)^{1/3}
$$

$$
=\left(\frac{398\,600\times86\,164^2}{4\pi^2}\right)^{1/3}=42\,164\ \text{km}.
$$

The altitude is $42\,164-6378=35\,786$ km and the speed $\sqrt{398\,600/42\,164}=3.07$ km/s. Using 86 400 s instead gives 42 241 km, and a satellite there would drift west by about $1°$ a day.

> [!tip] Orbit is about speed, not height
> Per kilogram, raising a mass from the surface to 400 km costs $\mu(1/R_E-1/r)=398\,600\,(1/6378-1/6778)=3.69$ MJ, while giving it the orbital speed of 7.67 km/s costs $\tfrac12v^2=29.4$ MJ, eight times as much. Reaching orbit is mainly a matter of going sideways fast, which is why the rocket equation of [[SESA1015 A04 - Rocket Equation and Launch Performance]] is written in terms of velocity increment.

## 3. Orbital elements: semi-major axis and inclination

The position of a satellite in an Earth orbit fixed relative to the stars is specified by six **orbital elements**. Two of them are needed in this module (p. 7). The **semi-major axis** $a$ sets the size of the orbit; for a circular orbit it equals the radius, so it fixes $v$ and $T$ through §2. The **inclination** $i$ is the angle between the orbit plane and the equatorial plane.

![[astro_a01_inclination.png|900]]

The orbit plane cuts the equatorial plane along the **line of nodes**. The **ascending node** is the point where the satellite crosses the equator heading north, and the inclination is measured there, from the equator to the direction of motion. An orbit with $i=0°$ is equatorial (GEO), one with $i=90°$ passes over both poles, and one with $i>90°$ is retrograde, moving against the Earth's rotation. Because the orbit plane passes through the Earth's centre, the ground track reaches latitudes up to $\pm i$ (or $\pm(180°-i)$ for a retrograde orbit) and no further: the ISS, at $i=51.6°$, reaches 51.6° N, just north of Southampton at 50.9° N, but never comes near the poles. The other four elements, and the general ellipse, are developed in [[Keplerian Orbital Elements]] (SESA2024).

## 4. The Sun–Earth geometry

The Earth's mean orbital radius about the Sun is 149 597 871 km, defined as one **astronomical unit** (AU) (p. 9). Two numbers follow directly. Light covers 1 AU in

$$
t=\frac{149\,597\,871}{299\,792.458}=499\ \text{s}=8.3\ \text{min},
$$

and the Earth's mean orbital speed is the circumference over the year,

$$
v_E=\frac{2\pi\times149\,597\,871}{365.256\times86\,400}=29.8\ \text{km/s}.
$$

The same 29.8 km/s comes from $\sqrt{\mu_\odot/r}$ with $\mu_\odot=1.327\times10^{11}$ km$^3$/s$^2$, which confirms that the circular-orbit result of §2 applies about any central body.

The Earth's spin axis is tilted $23.5°$ to the normal of its orbital plane and keeps pointing the same way in space through the year (p. 10). Near 21 June the northern hemisphere leans towards the Sun (northern summer solstice); near 21 December it leans away (winter solstice); at the equinoxes in March and September the axis is side-on to the Sun and day and night are equal everywhere. The **terminator** is the line dividing the sunlit and dark hemispheres. The **noon meridian** is the meridian facing the Sun, where local time is midday, and the **midnight meridian** is the one opposite.

![[astro_a01_solstice_geometry.png|900]]

The tilt sets the height of the noon Sun. The Sun's declination $\delta$ (its angle north of the equatorial plane) runs between $+23.44°$ at the June solstice and $-23.44°$ at the December solstice. On the noon meridian, the local vertical at latitude $\phi$ makes angle $\phi$ with the equatorial plane and the Sun direction makes angle $\delta$ with it, so the Sun is $|\phi-\delta|$ from the vertical. The elevation above the horizon is therefore

$$
e_{noon}=90°-|\phi-\delta| .
$$

For Southampton, $\phi=50.9°$ N:

| Date | $\delta$ | $e_{noon}$ |
|---|---|---|
| June solstice | $+23.44°$ | $90-27.46=62.5°$ |
| equinoxes | $0°$ | $90-50.9=39.1°$ |
| December solstice | $-23.44°$ | $90-74.34=15.7°$ |

The same geometry, seen from orbit, decides how long a satellite spends in the Earth's shadow and which local solar time it crosses the equator at ([[Eclipse Duration]] and [[Sun-Synchronous Orbit]], SESA2024).

## 5. Spaceflight history as capability growth

Modern rocketry starts with Wernher von Braun's liquid-propellant V-2 and his 1934 thesis on the liquid-propellant rocket (p. 11). After the war von Braun became chief architect of the Saturn V (pp. 13–15), the launcher of the Apollo programme: 111 m tall, about 3 039 000 kg at lift-off, about 129 300 kg to orbit. Its payload mass fraction is

$$
\frac{M_{payload}}{M_{total}}=\frac{129\,300}{3\,039\,000}=0.0425=4.3\% ,
$$

so more than 95% of what leaves the pad is propellant and structure that never reaches orbit. That fraction is the central constraint of launch-vehicle design and is derived from the rocket equation in [[SESA1015 A04 - Rocket Equation and Launch Performance]] and [[SESA1015 A05 - Staging and Payload Fraction]].

Apollo 11 landed on the Moon in July 1969, and Lunar Reconnaissance Orbiter images from 2009 show the descent stages and tracks the crews left (pp. 16–18). Crewed presence in orbit then grew through a sequence of stations: Skylab (1973–1979), Mir (1986–2001) and the International Space Station (from 1998, planned to about 2030) (pp. 19–22). The Space Shuttle (1981–2011, Space Transportation System, missions numbered STS-) flew about 135 missions with five orbiters: Columbia, Challenger, Discovery and Atlantis, with Endeavour built to replace Challenger after its loss in 1986; Columbia was lost in 2003 (pp. 23–27). Space tourism and crewed Mars missions are the current extensions of human spaceflight (pp. 28–29).

No single subsystem made any of this possible. Saturn V needed high-energy propulsion, but also guidance, lightweight structures, reliable electronics, tracking and the systems engineering that tied them together.

### Space agencies

The national and regional space agencies are NASA (USA), ESA (Europe), Roscosmos (Russia), CSA (Canada), JAXA (Japan), CNSA (China) and ISRO (India) (p. 30).

## 6. Science and exploration missions

Space telescopes avoid the atmosphere, which blurs visible light and absorbs most infrared, ultraviolet and X-ray radiation ([[SESA1015 A02 - Space Environment#2. The Sun|A02 §2]]). Hubble (1990) works in the visible and near ultraviolet; ESA's Herschel and Planck observed in the infrared and microwave; XMM-Newton (X-ray Multi Mirror) is an X-ray observatory; the James Webb Space Telescope is the infrared successor to Hubble (pp. 31–34).

Planetary exploration began with flybys. Pioneer and Voyager (launched 1977) toured the outer planets (pp. 35–36). On 14 September 2020 Voyager 1 was 150.52 AU from Earth, having reached interstellar space in August 2012, and Voyager 2 was 124.92 AU away. In kilometres and light time, Voyager 1 was

$$
150.52\times1.496\times10^{8}=2.25\times10^{10}\ \text{km},\qquad t=\frac{2.25\times10^{10}}{299\,792}\ \text{s}=20.9\ \text{h},
$$

so a command takes almost a day to arrive, and any fault response has to be autonomous. Galileo (launched 1989) was the first spacecraft to orbit Jupiter (1995) and dropped a probe into its atmosphere; it was deliberately ended in 2003 to avoid contaminating an icy moon (pp. 37–38). Cassini–Huygens, a joint NASA/ESA/ASI mission launched in 1997, was the first to orbit Saturn (2004); its Huygens probe landed on Titan, the first landing in the outer Solar System, and Cassini was destroyed in Saturn's atmosphere on 15 September 2017 (pp. 39–43). ESA's Rosetta met comet 67P in 2014; its lander Philae bounced twice because the harpoons did not deploy and the hold-down thruster did not fire, and came to rest in the shadow of a cliff; the mission ended with Rosetta's descent to the comet on 30 September 2016 (pp. 44–50).

Mars shows the failure modes plainly (pp. 51–62). ESA's Mars Express entered orbit in 2004, but its Beagle 2 lander was lost. Mars Polar Lander failed during its descent. Mars Climate Orbiter performed an incorrect orbit insertion burn, entered the atmosphere and broke up; the error is generally traced to one team supplying thruster impulse in imperial units where the navigation software expected SI units. Phoenix (2008) and Curiosity (touchdown 5 August 2012) succeeded. Curiosity's landing ellipse was 12 × 4 miles against Viking's 176 × 64 miles in 1976 (p. 58); since an ellipse's area is $\pi ab$, the ratio of areas is

$$
\frac{12\times4}{176\times64}=\frac{48}{11\,264}=\frac{1}{235},
$$

a measure of how much entry guidance improved in 36 years. Genesis (2001) returned samples of the solar wind (p. 63).

## 7. Commercial applications

Most money in space now comes from services (pp. 64–71). Communications satellites, mostly in GEO, relay television, telephony and data. Navigation constellations in MEO broadcast precise time and position: the US Global Positioning System (GPS), Europe's Galileo, Russia's GLONASS and China's BeiDou (COMPASS), plus regional systems; each is often loosely called a "GPS system". Earth observation covers weather (Meteosat Second Generation in GEO) and environmental monitoring (ENVISAT, launched 2002, contact lost in 2012). Small satellites and CubeSats, such as the University of Southampton's UoS3, have made space accessible to universities, and large LEO constellations (SpaceX, OneWeb, Planet Labs and others) aim at global broadband and daily imaging.

Each application points to an orbit, and choosing the orbit for the purpose is the first step of [[Space Mission Architecture]]:

| Application | What the payload needs | Orbit or trajectory |
|---|---|---|
| Communications | fixed pointing from the ground, wide coverage | GEO; or large LEO constellations for low latency |
| Navigation | several satellites visible everywhere, stable clocks | MEO constellations |
| Weather imaging | continuous view of one hemisphere | GEO |
| Earth observation | high resolution, global revisit | LEO (often sun-synchronous) |
| Astronomy | above the atmosphere, stable thermal and pointing | LEO (Hubble) or far from Earth (JWST) |
| Planetary science | reach the target, survive its environment | interplanetary transfer, flyby, orbit or landing |
| Human spaceflight | life support, safe return, crew access | LEO (ISS); lunar orbit for Artemis |

## 8. Recent highlights and future directions

Highlights of 2019–2020 (p. 72) include the 50th anniversary of Apollo 11, ESA/NASA Solar Orbiter (launched 10 February 2020), China's Tianwen-1 Mars mission (orbiter, lander and rover), NASA's Perseverance rover (launched 30 July 2020, landed 18 February 2021) and SpaceX's crewed Dragon flight to the ISS on 30 May 2020, the first crewed launch from the USA in nine years.

NASA's Artemis programme aims to return astronauts to the Moon, using the Space Launch System (SLS) and the Orion spacecraft, with the Lunar Gateway in lunar orbit (pp. 73–75). The target dates (p. 75) are forecasts from 2019–2021; Artemis I, the uncrewed test of SLS and Orion, flew in November 2022.

Cheaper access to space is coming from commercial and reusable launchers, such as SpaceX's Falcon Heavy (first flight February 2018) and Rocket Lab's Electron from New Zealand, and from air-breathing propulsion: NASA's X-43 scramjet demonstrator and Reaction Engines' Skylon spaceplane concept, successor to HOTOL (pp. 76–77). Air-breathing engines carry no oxidiser for the atmospheric part of the ascent, which attacks the small payload fraction of §5 directly; see [[SESA1015 A06 - Launch Vehicles, Systems and Interfaces]].

## Worked examples

### Orbit numbers for the ISS and GEO

**ISS at 400 km.** With $r=6378+400=6778$ km,

$$
v=\sqrt{\frac{398\,600}{6778}}=7.669\ \text{km/s},
$$

$$
T=2\pi\sqrt{\frac{6778^3}{398\,600}}=5553\ \text{s}=92.6\ \text{min},
$$

$$
\frac{86\,400}{5553}=15.6\ \text{orbits per day}.
$$

**Edges of LEO.** At 200 km, $r=6578$ km gives $v=7.78$ km/s and $T=88.5$ min; at 2000 km, $r=8378$ km gives $v=6.90$ km/s and $T=127.2$ min.

**GEO.** From §2, $r=42\,164$ km, $v=3.07$ km/s and $T=86\,164$ s $=23.93$ h, one orbit per sidereal day.

> [!check] Numerical check
> $v\,T=7.669\times5553=42\,590$ km and $2\pi\times6778=42\,587$ km, so speed, period and radius agree to rounding. For GEO, $3.0747\times86\,164=264\,928$ km against $2\pi\times42\,164=264\,925$ km.

### Noon Sun over Southampton

At the equinox the Sun is in the equatorial plane, $\delta=0$, so $e_{noon}=90°-50.9°=39.1°$. At the June solstice $e_{noon}=90°-(50.9°-23.44°)=62.5°$, and at the December solstice $e_{noon}=90°-(50.9°+23.44°)=15.7°$. A south-facing solar panel at Southampton therefore sees the noon Sun swing through $46.9°=2\times23.44°$ over the year.

## Terminology and alternative names

| Course term | Also called | Note |
|---|---|---|
| HEO, Highly Eccentric Orbit | Highly Elliptical Orbit; Molniya orbit (one common example) | the p. 6 figure uses "High Earth Orbit" for the region beyond GEO; the course uses Highly Eccentric throughout |
| Kármán line | edge of space, 100 km line | 100 km (62 miles) altitude |
| COMPASS | BeiDou, BeiDou-2 | China's navigation system |

## Links

- Parent: [[SESA1015 Intro to Aero & Astro Hub]] · Next: [[SESA1015 A02 - Space Environment]]
- Astronautics stream: [[SESA1015 A03 - Launch Environment]] · [[SESA1015 A04 - Rocket Equation and Launch Performance]] · [[SESA1015 A05 - Staging and Payload Fraction]] · [[SESA1015 A06 - Launch Vehicles, Systems and Interfaces]]
- Concepts: [[Earth Orbit Zones]] · [[Space Mission Architecture]] · [[Kepler's Laws]] · [[Keplerian Orbital Elements]] · [[Rocket Mass Fractions]]
- Later in the degree: [[SESA2024 02 - Kepler's Laws and the Orbit Equation]] and [[SESA2024 03 - Orbital Elements and Conic Sections]] generalise §2 and §3 to ellipses; [[SESA2024 11 - Payload and Orbit Selection]] turns the application table of §7 into a design method; [[SESA2024 12 - Sun- and Earth-Synchronous Orbits]] uses the Sun–Earth geometry of §4; [[SESA2024 01 - Systems Engineering and Spacecraft Design]] formalises mission architecture.

## Sources

- SESA1015 Astronautics Part 1, Introduction (Dr S.J.I. Walker), pp. 1–77: Earth and orbit zones pp. 3–10; history pp. 11–29; space agencies p. 30; science missions pp. 31–63; commercialisation pp. 64–71; recent highlights and future pp. 72–77.
- Constants used: $\mu=398\,600.4$ km$^3$/s$^2$, $\mu_\odot=1.327\times10^{11}$ km$^3$/s$^2$, $c=299\,792.458$ km/s, sidereal year 365.256 days. All numbers in this note were recomputed in Python; the figures come from `01 - Notes/Figures/generate_astro_a01_figures.py`.
- The Mars Climate Orbiter unit mismatch in §6 and the Artemis I flight date in §8 are added context, not on the slides.

## Self-study tasks

### Core

- [ ] Answer the question marks on the slides: where space starts (p. 4), the LEO altitude range (p. 5), the Earth–Sun distance (p. 9) and the axial tilt (p. 10). → [[#1. The Earth and where space begins]] · [[#The zones]] · [[#4. The Sun–Earth geometry]]
- [ ] Derive $v=\sqrt{\mu/r}$ and $T=2\pi\sqrt{r^3/\mu}$ from Newton's law of gravitation, then compute $v$, $T$ and orbits per day at 200, 400 and 2000 km (suggested, not lecturer-set). → [[#Circular-orbit speed and period]] · [[#Orbit numbers for the ISS and GEO]]
- [ ] Derive the GEO radius from the sidereal day, explaining why 86 164 s and not 86 400 s (suggested, not lecturer-set). → [[#Why GEO sits at 42 164 km]]

### Further practice

- [ ] For each application on pp. 64–71, name the orbit it uses and why (suggested, not lecturer-set). → [[#7. Commercial applications]]
- [ ] Reread the payload mass fraction of the Saturn V (p. 15) and the Voyager distances (p. 36) and check the numbers in the note. → [[#5. Spaceflight history as capability growth]] · [[#6. Science and exploration missions]]

## Transcript and slide slips

> [!warning] Slide slip (Part 1, p. 1)
> Where: [[#Sources]].
>
> The footer of the title slide reads "SESA2024 - Astronautics"; the deck is the SESA1015 Astronautics introduction, reused from the Year 2 module.

> [!warning] Slide slip (Part 1, p. 6)
> Where: [[#The zones]].
>
> The orbit-zone figure labels the region beyond GEO "HEO Zone (High Earth Orbit)", while the footnote on the same slide defines HEO as Highly Eccentric Orbit for the rest of the course. Read HEO as Highly Eccentric Orbit.
