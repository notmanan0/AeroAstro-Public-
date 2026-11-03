---
title: "SESA2024 01 - Systems Engineering and Spacecraft Design"
module: "SESA2024 Astronautics"
type: topic
stream: "Systems"
order: 1
tags: [sesa2024, systems-engineering, design-process, payload]
aliases: ["Spacecraft Systems Engineering", "Chapter 1", "Chapter 4 Payload"]
date: 2026-10-30
status: lectured
coverage: "Week 1 (Ch 1, 2025-10-02) and Week 9 (Ch 4, 2025-11-25)"
parent: ["[[SESA2024 Astronautics Hub]]"]
prerequisites: []
next_topics: ["[[SESA2024 02 - Kepler's Laws and the Orbit Equation]]", "[[SESA2024 06 - Attitude Control]]"]
key_concepts: ["[[Systems Engineering Design Phases]]", "[[Spacecraft Subsystems]]", "[[Agile Aerospace]]"]
tutorial_sheets: []
sources: ["02 - Sources/Lectures/Chapter 1/SESA2024 Astronautics - Chapter 1 (Systems Eng.) - Lecture 1 2025-26 BB_sys eng_V1.pdf", "02 - Sources/Lectures/Chapter 4/2025 WEEK 9 - Lecture 1 - Chapter 4 - Payload - v1.pdf", "02 - Sources/Lectures/SESA2024 Lecture 2025-09-30.txt", "02 - Sources/Lectures/SESA2024 Lecture 2025-10-02.txt", "02 - Sources/Lectures/SESA2024 Lecture 2025-11-25.txt", "02 - Sources/Lectures/SESA2024 Lecture Dr Deshpande Lecture - Planet Labs.txt"]
---

# SESA2024 01 - Systems Engineering and Spacecraft Design

> [!abstract] Summary
> A spacecraft is a payload, which is the reason for the mission, carried and looked after by a bus of service subsystems: structure, attitude control, propulsion, communications, data handling, power and thermal. Systems engineering turns a customer's mission objective into quantitative design requirements in four steps (objectives, payload, top-level requirements, design requirements) and then trades the subsystems against each other, because none of them can be changed without affecting the rest. The ECSS phases 0 to F organise that work, and the decisions taken up to Phase B fix most of the cost.

> [!summary]- Exam use: quick path
> - **Use it when:** a Section A question asks for the design steps, the ECSS phases, a trade-off, a subsystem function, or how a payload requirement drives a subsystem.
> - **Assumptions:** a conventional bespoke spacecraft developed under ECSS; the agile route (Planet) is the exception and must be named as such.
> - **Method:** 1. Name the four steps in order: mission objectives (customer), payload definition (specialist working group), TLRs (systems team), DRs (systems team, per subsystem). 2. Give one example at each step. 3. For a trade-off, name both options and the subsystem that pays for each. 4. For a payload question, follow the requirement to the subsystem it sizes (pointing to ACS, resolution to orbit, data rate to OBDH and comms, power to arrays and batteries, dissipation to thermal). 5. Close with the systems point: one change propagates to the others.
> - **Common mistakes:** putting the TLRs before the payload is defined; listing phases without saying that C, D and E are where system-level work gets expensive.
> - **Practise:** [[#6. Ulysses: a trajectory that decided the power system]] · [[SESA2024 2024-25 Exam Solutions#Section A|2024/25 A1]]

A car is a system too, and Dr Ryan used his own to make the point that matters in this chapter (2025-10-02, ll. 46–75). When a tyre blew out on the A34 he put the spare on and drove away. A car is designed so that one subsystem can be swapped without redesigning the others, but a spacecraft cannot be: it is far away, it usually cannot be serviced, and its subsystems are so interdependent that a different propulsion unit would ripple through power, thermal, structure and attitude control. It also costs a great deal more: excluding CubeSats and SpaceX's mass-produced craft, a typical bespoke satellite costs between \$100 million and \$500 million (ll. 91–100), which makes risk expensive and pushes the industry towards conservative, flight-proven hardware.

The other half of the picture is that almost every spacecraft is designed for one mission. Dr Ryan's joke is that a spacecraft is "just a box of electronics" with two solar panels, but because each mission asks for something different there is "an art to it, there's a creativity to it" (ll. 256–271). Systems engineering is the discipline that keeps that creativity pointed at the customer's objective while the subsystem specialists each pull towards their own favourite solution.

## 1. Payload and bus

INTEGRAL, ESA's gamma-ray observatory, is the lecture's typical spacecraft (slides 4–5; 2025-10-02, ll. 106–166). It has a mass of about 4000 kg, of which about 2000 kg is payload, stands about 5 m high without its arrays, and flew in a highly elliptical orbit with a 3-day period so that it could observe from near apogee. It was launched in October 2002 for a 2 to 3 year mission and retired in 2025, about 23 years later, not because anything broke but because it ran out of propellant; for its last few years it was being pointed with reaction wheels and solar pressure alone (ll. 116–121).

The exploded view splits it into two parts. On top sit the instruments, mounted to a stiff bench. Underneath is the bus, which holds everything else: propulsion, power, data handling and the on-board computer, reaction wheels and star trackers. The name comes from the analogy with a bus, which takes its passengers where they need to go and looks after them on the way: a spacecraft bus delivers the payload to its orbit and then keeps it pointed, powered, warm and talking to the ground for the whole mission (ll. 166–180).

The slides list the subsystems and their functions (slides 6–7), and the course chapters follow the same split:

| Subsystem | Function | Chapter |
|---|---|---|
| Payload | fulfil the mission objectives with sensors or communications hardware | 4 |
| Structure | support the payload and subsystems in all predicted environments | — |
| Attitude control (ACS) | achieve the pointing requirements of payload, power, thermal and comms | 6 |
| Propulsion | provide orbit transfer and control the mission orbit | 7 |
| Communications | provide the link with the ground segment for payload data, telemetry and commands | 9 |
| Data handling | store and process payload, command and health-monitoring data, and pass data between subsystems | — |
| Power | provide electrical power to support payload and subsystem operation | 8 |
| Thermal | provide a benign thermal environment for the payload and subsystems, for reliability | 10 |

The lecture added the reasoning behind several of these rows. The structure is sized by the launch, which lasts only minutes but brings high g-loads, vibration, acoustic noise and a pressure drop from one atmosphere to vacuum (ll. 181–195). Propulsion is tied to the ACS: it trims the orbit after the launcher drops the spacecraft off, keeps it in place during the mission, dumps momentum from the reaction wheels and finally disposes of the spacecraft (ll. 196–215). Comms needs an uplink as well as a downlink, for instance to command a manoeuvre before a solar storm (ll. 226–232). Thermal design aims to keep the inside of a spacecraft near room temperature, on purpose, so that the electronics behave as they did when they were tested on the ground, while the outside swings between roughly +100 °C in sunlight and −100 °C in shadow (ll. 236–255).

> [!warning] Transcript slip (2025-10-02, l. 251)
> The transcript has the outside of the spacecraft "very cold" in "the albedo". Albedo is reflected sunlight, which heats the spacecraft. The cold case is eclipse or deep-space viewing; see [[SESA2024 10 - Thermal Control]].

## 2. What systems engineering is, and who does it

The course definition is on slide 8:

> "Space systems engineering is the science (and art) of developing an operable space system capable of meeting the mission objectives efficiently, within the imposed constraints (such as mass, cost, schedule, etc.)"

A mission with a \$500 million budget involves hundreds of people, organised into teams of subsystem specialists (ll. 271–286). Thales Alenia Space's UK site at Harwell, for instance, now concentrates on the propulsion subsystem alone. Over the teams sits the systems engineer, who does the first-cut analysis in every area, understands how the subsystems interact, and needs the people skills to lead, keep the team productive and run meetings (slide 9).

The last item on that slide is "success requires compromise", and the lecture's example shows why. A propulsion specialist who likes ion thrusters will argue for them because they save propellant. Raising a satellite to geostationary orbit with electric propulsion can take about six months, against about three days with a chemical apogee engine (ll. 301–316). If the customer needs the satellite in service within weeks of launch, the systems engineer has to overrule the specialist and accept the heavier chemical system, because the right answer is the one that works best for the whole spacecraft and the mission, not for one subsystem.

## 3. From mission objective to design requirements

The slides give a four-step chain (slides 10–11), and the order matters because each step needs the one before it.

The customer or user defines the mission objectives. NASA's objective for New Horizons, roughly twenty years ago, was to fly by Pluto and provide imaging and other data to characterise the Pluto/Charon system (ll. 316–331). NASA does not build spacecraft itself, so it took that objective to a spacecraft developer. The customer can equally be ESA or a commercial firm: the lecture's example is a European company that builds synthetic aperture radar payloads for aircraft and now wants a satellite to carry one (ll. 421–435).

A working group of specialists then defines the payload, turning the objective into specific observations and instrument types: a CCD imager, an infrared spectrometer, a field or radiation detector. Some payloads are close to off-the-shelf. Others, like many of the instruments Dr Sykulska-Lawrence designs, are entirely new (ll. 331–346).

The systems team converts those two into top-level requirements (TLRs): the trajectory, the fly-by geometry, the payload operation plan, the mission duration. For a Pluto fly-by that might be "arrive within five to ten years" (ll. 346–355).

Finally the systems team turns the TLRs into design requirements (DRs) for each subsystem. These are quantitative: orbit parameters, ΔV budgets, fields of view, pointing accuracy and stability, slew rates, data storage and the communications link. A trajectory that must reach Pluto within ten years sets a ΔV for the propulsion system, and photographs that must come home set a data rate for comms (ll. 355–375). ΔV, the change of velocity a manoeuvre needs, sets the propellant mass; the lecture quotes roughly 10 km/s from the ground to low Earth orbit and very roughly another 10 km/s from LEO onwards to Pluto (ll. 361–364).

The slide's one-line summary is "payload operation + mission → design requirements". Two Section A questions have asked for this chain directly: 2024/25 A1 asks which two activities must come before the TLRs (the mission objectives and the payload definition), and 2019/20 A1(i) asks for all four steps.

## 4. Initial study logic and trade-offs

Once the DRs exist, the study branches out (slides 13–17; ll. 406–496). The systems team identifies system options, typically several candidate spacecraft that differ in stabilisation type (three-axis, pure spin or dual spin) and in launch vehicle. Each option is analysed, the options are traded against an evaluation measure such as mass or cost, a baseline is selected, and the customer agrees it. The preliminary design that follows carries the system performance and budgets (power, mass, volume), the schedule and cost, and the key technology areas. The customer stays involved throughout, and budgets change: "NASA's just cut the budget for this by \$10 million, so rethink, please" happens regularly (l. 468).

The launch vehicle choice is a good example of how many things feed one decision. In Dr Ryan's experience the drivers are cost and politics (ll. 436–455). SpaceX is cheap; Russian launchers such as Soyuz and Proton, once widely used by Western customers, are no longer available to them. Each launcher also imposes its own load envelope and fairing size. A small launcher such as Rocket Lab's Electron gives a dedicated customer a bespoke orbit and inclination but cannot reach high orbits, whereas a large rideshare can go higher but drops many customers off in the same place (ll. 580–600).

Slide 17 draws the synthesis: the mission objective defines the payload's specification and operation, which together with the orbit and the launch vehicle interface sets the spacecraft design requirements, and trading those against the services (power, thermal, ACS, data handling, comms, propulsion) produces the design concept.

The principal system-level trade-offs are on slides 19–20:

| Area | Options | Why it matters |
|---|---|---|
| Mission analysis | launch vehicle, orbit type, orbit acquisition | a major influence on every subsystem's DRs |
| ACS | three-axis, pure spin, dual spin | also a major influence on every subsystem |
| Propulsion | solid; liquid (monopropellant, bipropellant); electric | EP saves propellant but needs power and time |
| Communications | power versus gain | a bigger dish needs less RF power but tighter pointing |
| Power | solar arrays, RTGs, batteries, fuel cells | set by distance from the Sun and mission length |
| Thermal | passive versus active | heat pipes and heaters cost power and mass |
| Technology | new versus old | see below |
| Other | political, regulatory, commercial | launcher access, frequency allocation, debris rules |

The electric propulsion row shows how the couplings chain together (ll. 616–643). EP needs electrical power, so EP spacecraft carry large solar arrays. In low Earth orbit there is still enough atmosphere at a few hundred kilometres for large flat arrays to raise the drag, so the spacecraft decays faster. Early Starlink satellites are the lecture's example: big, flat, electrically propelled and designed to come down quickly at the end of their lives.

On technology, the slide sets "conservative: minimise cost; minimise schedule; minimise uncertainty" against "innovative: subsystem specialists". The space sector is still conservative, and the electronics inside a typical spacecraft are often 20 to 30 years old because they are tried and tested (ll. 644–660). New technology may perform better, but it needs development and qualification, and the people who push for it are usually the subsystem specialists rather than the project manager. 2021/22 A1 asks why old technology is often chosen.

## 5. Design phases (ECSS)

The process is standardised because it involves so many people and disciplines. The European Cooperation for Space Standardization (ECSS) publishes the standard the course quotes, ECSS-E-ST-10C, *System Engineering General Requirements* (slides 12 and 18; ll. 376–391):

| Phase | Name |
|---|---|
| 0 | Mission analysis / need identification |
| A | Feasibility |
| B | Preliminary definition |
| C | Detailed definition |
| D | Qualification and production |
| E | Operations / utilisation |
| F | Disposal |

What the lecture went through in §§3–4 is phases 0, A and B, up to the preliminary design review (PDR). Getting those right matters because "system level activities during phases C/D/E can be very expensive" (slide 18). After PDR the team grows to develop every subsystem in detail, so a wrong decision made early multiplies in cost as more people build on it (ll. 496–510). Phase D includes qualification: shaking the spacecraft on a vibration table, illuminating it with simulated sunlight and cycling it in a thermal vacuum chamber. Aeolus, ESA's wind-measuring lidar mission built by Airbus at Stevenage, is the lecture's warning: the spacecraft was built while its entirely new instrument was found not to work as designed, and the instrument and spacecraft had to be reworked before launch (ll. 476–490).

Dr Ryan admits his own experience of ECSS on CubeSats was mostly paperwork, because a team of ten in one office can simply talk to each other; the tracking only earns its keep when hundreds of people are involved (ll. 386–400).

Phase F was discussed with the class (ll. 511–571). In low orbit a spacecraft is usually de-orbited so that it burns up in the atmosphere. Geostationary satellites are too high for that to be affordable, so they are boosted into a slightly higher graveyard orbit. A student asked what stops the graveyard filling with colliding wrecks, which leads into [[SESA2024 15 - Space Sustainability, Debris and NewSpace]]: there were about 1000 satellites in low Earth orbit ten years ago and there are now tens of thousands. Space has far more room than a road network, but collision speeds are far higher. Dr Ryan's preference is reuse and refuelling, given that INTEGRAL and many others end only because their tanks are empty.

## 6. Ulysses: a trajectory that decided the power system

Ulysses (slides 21–24; ll. 661–720) was built to observe the Sun's poles, where the magnetic field and particle environment are of particular interest. The planets all orbit close to one plane through the Sun, so to look down on the poles a spacecraft must leave that plane, and turning a heliocentric orbit through a large inclination with propulsion would have been far too expensive. The mission planners instead sent Ulysses out to Jupiter and used a gravity assist to twist the orbit over the Sun's poles.

That trajectory decided the power system. At Jupiter, about 5.2 AU from the Sun, sunlight is about $1/5.2^2\approx1/27$ of its strength at Earth, and the solar cells of the time could not deliver enough power there. Ulysses therefore carried a radioisotope thermoelectric generator (RTG), which produces electricity from the heat of decaying plutonium-238, and has no solar arrays. It was a spinner with an Earth-pointing high-gain antenna. One mission objective (see the poles) led to a trajectory (Jupiter swing-by), which led to the power source (RTG), which shaped the ACS, comms and thermal design.

> [!warning] Transcript slips (2025-10-02, ll. 706–721)
> The RTG is described as producing "100 watts or so". Ulysses' generator delivered about 285 W at launch, falling slowly as the plutonium decayed, so the order of magnitude is right but the figure is low. The lecture also says Ulysses "was going to get launched on the space shuttle" but "didn't" after Challenger. The Challenger loss in 1986 delayed it, and Ulysses was launched by the Space Shuttle Discovery in October 1990.

The second example is Starlink version 1 (ll. 721–750): small satellites of a few hundred kilograms with a single long solar array, designed flat so that sixty could be stacked in one Falcon 9 fairing like flat-pack furniture. The launcher's volume shaped the spacecraft.

## 7. How the payload drives the design (Chapter 4)

Chapter 4 was taught last, at the end of the thermal lecture, because it "brings together the previous 10 chapters" (2025-11-25, ll. 500–530). The payload is the component that fulfils the mission objective, so it is "the reason why it's up there in the first place" and the design cannot start anywhere else. It defines the configuration, sizes the spacecraft and specifies the subsystems.

The chapter groups missions into five categories (ll. 530–560):

| Category | Purpose | Examples |
|---|---|---|
| Communications | civil communications, data relay | Intelsat, Skynet, TDRSS |
| Earth viewing and remote sensing | resources, environment, weather, climate | Landsat, SPOT, Envisat, Meteosat |
| Scientific | observatories, exploration, biology | Hubble, Webb, XMM-Newton, INTEGRAL, Cassini, Deep Impact |
| Other applications | navigation, search and rescue, manufacture | GPS, Galileo, ISS |
| Special purpose (military) | surveillance, intelligence, early warning, military comms | SDI, early-warning satellites |

Two intelligence satellites show how hard a payload can push. An imaging radar satellite uses microwaves because they penetrate cloud and rain, and because the radar carries its own illumination it can image at night (ll. 590–618). Synthetic aperture radar uses the spacecraft's forward motion to synthesise a long antenna, but the physical antenna is still large in one dimension, so the spacecraft has to stow and reliably deploy it. An electronic intelligence satellite, which eavesdrops on communications at high latitudes from a Molniya orbit, needs a deployable reflector about 300 ft across (ll. 620–640). Accommodating something like that dictates the whole configuration.

The slide table of payload requirements and their impact is the core of the chapter (ll. 640–715):

| Payload requirement | What it drives |
|---|---|
| Pointing: accuracy, stability, slew rates | choice of stabilisation; ACS sensors, actuators, processor, mass and power |
| Envelope (size, mass) and accommodation | overall configuration, launcher fit, choice of stabilisation |
| Resolution and coverage | orbit selection: elements, transfer and station-keeping (propellant), ground-station coverage, eclipse duration (power and thermal) |
| Data rate, plus telemetry and command | on-board data storage and processing; comms frequency, bandwidth and the power–gain trade |
| Power: peak and average, duty cycle, emergency mode | array size, battery specification, regulation and distribution, power-subsystem mass |
| Thermal: component tolerances, dissipation | coatings, heaters, radiator placement, mass and power |

Every row ends in mass and power, which is why those two budgets dominate the design reviews. The resolution row is worth following through once: a camera that needs a certain ground resolution sets a maximum altitude, the altitude and the required lighting set the orbital elements, the elements set the eclipse duration, and the eclipse sizes the batteries, the arrays and the heater power. That chain is exactly the Chapter 11 case study ([[SESA2024 11 - Payload and Orbit Selection]] to [[SESA2024 14 - Orbit Control, Drag and Payload Data Rate]]).

Design heritage moderates all this (ll. 724–740). A manufacturer such as Airbus has standard communications platforms and builds on them; a science mission often flies a new instrument on a modified platform, so it carries more risk.

## 8. A different route: agile aerospace (Planet)

The guest lecture by Sanya Deshpande, Director of Engineering Operations at Planet Labs, describes a deliberate departure from the process above (`SESA2024 Lecture Dr Deshpande Lecture - Planet Labs.txt`). Planet's objective is to image the whole land surface every day. It flies more than 150 satellites in two classes: PlanetScope Doves of about 5 kg (3U CubeSats) at about 3 to 5 m resolution, and 21 SkySats of about 100 kg at about 0.6 m. Instead of one large, expensive satellite, it flies many small ones as a single constellation (ll. 61–80). A launch failure or a dead satellite then costs a small fraction of capacity rather than the mission, and the design can be upgraded as satellites are replaced. Planet has had three launch failures among 29 launches without losing its constellation (ll. 101–110).

The method borrows from software development (ll. 141–260). The traditional waterfall approach builds wheels, then axle, chassis and cabin, and only at the end has a car. The agile approach asks for the cheapest thing that gets from A to B now, a skateboard, and improves it to a scooter, a bicycle and eventually a car. Planet redesigned the Dove about fifteen times in seven years, using batteries from electric cars and processors and drives from consumer electronics, and its downlink radios improved by a factor of about 10 000 over that period. It picks an objective function (pixels down per dollar), sets hard constraints (the 3U size, chosen for launch availability, fixed the telescope and the altitude), grades requirements by criticality and confidence rather than "shall" and "should", and replaces PDR and CDR milestones with integration milestones such as a functional satellite test.

The speaker is clear about the limits. Agile development makes schedules hard to predict, needs strict configuration control and margin, and does not suit every mission: "the James Webb Space Telescope could not have been built this way" (ll. 275–285). In exam terms, the ECSS sequence is the default answer and agile development is a contrast you can bring in when a question asks about NewSpace or cost.

## Worked example

### Putting numbers on the INTEGRAL and cost comparisons

*(Suggested, not lecturer-set.)* The lecture quotes three numbers that are worth checking for scale.

INTEGRAL's payload fraction is

$$
\frac{m_{\text{payload}}}{m_{\text{total}}}=\frac{2000}{4000}=0.5,
$$

which is high for a science spacecraft and reflects a heavy telescope on a comparatively simple bus. Its operating life against plan is

$$
\frac{2025-2002}{2.5}=\frac{23}{2.5}\approx9,
$$

so it ran about nine times its nominal mission, limited in the end by propellant.

The cost comparison in the lecture (ll. 76–100) is a car of "a couple of thousand pounds" against a bespoke spacecraft of \$100 million to \$500 million. Ignoring the currency difference,

$$
\log_{10}\frac{1\times10^{8}}{2\times10^{3}}=4.7,
\qquad
\log_{10}\frac{5\times10^{8}}{2\times10^{3}}=5.4,
$$

so the gap is closer to five orders of magnitude than the "three-odd, four-odd" said in the lecture (l. 100). Either way, the conclusion holds: at that price, risk is managed by heritage and testing rather than by replacing parts after a failure.

For Ulysses, the solar flux falls with the square of the distance from the Sun. At 5.2 AU,

$$
\frac{S_{\text{Jupiter}}}{S_{\text{Earth}}}=\frac{1}{5.2^2}=0.037,
$$

so an array that gives 1 kW at Earth would give about 37 W at Jupiter before any temperature or degradation effects. That is the quantitative reason for the RTG.

## Links

- Parent: [[SESA2024 Astronautics Hub]]
- Next: [[SESA2024 06 - Attitude Control]] (the next lecture, 2025-10-07) and [[SESA2024 02 - Kepler's Laws and the Orbit Equation]] (the next chapter in the notes)
- Concepts: [[Systems Engineering Design Phases]] · [[Spacecraft Subsystems]] · [[Agile Aerospace]]
- Applied throughout the case study: [[SESA2024 11 - Payload and Orbit Selection]] · [[SESA2024 13 - Calculating Orbital Elements for a Remote Sensing Mission]]
- Disposal and debris: [[SESA2024 15 - Space Sustainability, Debris and NewSpace]]

## Sources

- `Chapter 1 (Systems Eng.) - Lecture 1 2025-26 BB_sys eng_V1.pdf`, slides 1–25, with transcript `SESA2024 Lecture 2025-10-02.txt` (Dr C. Ryan; slides originally by Prof H. Lewis)
- Module introduction, `SESA2024 Lecture 2025-09-30.txt` (Dr H. Sykulska-Lawrence): lecturers, textbook, assessment
- `2025 WEEK 9 - Lecture 1 - Chapter 4 - Payload - v1.pdf`, with transcript `SESA2024 Lecture 2025-11-25.txt`, ll. 500–755
- Guest lecture, `SESA2024 Lecture Dr Deshpande Lecture - Planet Labs.txt`
- Fortescue, Stark and Swinerd, *Spacecraft Systems Engineering*, Ch. 1 (systems engineering) and Ch. 4 (payload). The module follows the book's chapter numbers but teaches them in a different order (2025-09-30, ll. 406–436).

## Self-study tasks

The workbook has no questions for Chapters 1 and 4, and nothing was set in the lectures beyond the class discussion of disposal methods (2025-10-02, ll. 511–545). The past papers carry the practice.

### Core

- [ ] State the two activities that must come before the top-level requirements, and who carries out each (2024/25 A1). → [[#3. From mission objective to design requirements]] · [[SESA2024 2024-25 Exam Solutions#Section A|solution]]
- [ ] List the four steps from mission objective to design requirements with one example each (2019/20 A1(i)). → [[#3. From mission objective to design requirements]] · [[SESA2024 2019-20 Exam Solutions#Section A (A1)|solution]]
- [ ] Why might a project choose old, flight-proven technology over new technology? (2021/22 A1) → [[#4. Initial study logic and trade-offs]] · [[SESA2024 2021-22 Exam Solutions#Section A|solution]]
- [ ] Name the ECSS design phases and say why decisions before PDR matter most (2013/14 Q1(i)). → [[#5. Design phases (ECSS)]]

### Further practice

- [ ] Name two ways to dispose of a spacecraft at end of life and say which orbit each suits (asked of the class, 2025-10-02, ll. 511–545). → [[#5. Design phases (ECSS)]]
- [ ] For a payload requirement of your choice (pointing, resolution, data rate, power or dissipation), trace the impact through every subsystem it touches, ending in mass and power. → [[#7. How the payload drives the design (Chapter 4)]]
- [ ] Explain how Ulysses' science objective determined its power subsystem, and compute the solar flux ratio at Jupiter. → [[#6. Ulysses: a trajectory that decided the power system]]
- [ ] *(Suggested, not lecturer-set)* Contrast the ECSS phased approach with Planet's agile approach, giving one mission each suits. → [[#8. A different route: agile aerospace (Planet)]]
