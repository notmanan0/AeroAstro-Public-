---
title: "SESA2024 06 - Attitude Control"
module: "SESA2024 Astronautics"
type: topic
stream: "Spacecraft Subsystems"
order: 6
tags: [sesa2024, attitude-control, acs, angular-momentum, stabilisation]
aliases: ["ACS", "Attitude control subsystem", "Chapter 6"]
date: 2026-10-30
status: lectured
coverage: "Weeks 2–3 (2025-10-07, 2025-10-09, 2025-10-14, start of 2025-10-16) plus the pre-recorded Chapter 6 lecture"
parent: ["[[SESA2024 Astronautics Hub]]"]
prerequisites: ["[[SESA2024 01 - Systems Engineering and Spacecraft Design]]"]
next_topics: ["[[SESA2024 07 - Spacecraft Propulsion]]"]
key_concepts: ["[[Inertia Matrix]]", "[[Momentum Bias and Gyroscopic Rigidity]]", "[[Spacecraft Stabilisation Types]]", "[[Reaction Wheels and Momentum Dumping]]", "[[Attitude Sensors and Torquers]]"]
tutorial_sheets: ["[[SESA2024 Workbook Ch6 - Attitude Control Solutions]]"]
sources: ["02 - Sources/Lectures/Chapter 6/2025 WEEK 3 Lecture 1 - Chapter 6 - Attitude Control - complete.pdf", "02 - Sources/Lectures/Chapter 6/Chapter 6 - Attitude Control - prerecorded material.pdf", "02 - Sources/Lectures/SESA2024 Lecture Chapter 6 - Attitude Control - prerecorded material.txt", "02 - Sources/Lectures/SESA2024 Lecture 2025-10-07.txt", "02 - Sources/Lectures/SESA2024 Lecture 2025-10-09.txt", "02 - Sources/Lectures/SESA2024 Lecture 2025-10-14.txt", "02 - Sources/Lectures/SESA2024 Lecture 2025-10-16.txt"]
---

# SESA2024 06 - Attitude Control

> [!abstract] Summary
> The attitude control subsystem (ACS) points the payload, arrays, antennas, radiators and thrusters, and it does so by managing the spacecraft's total angular momentum $\mathbf H=[\mathbf I]\boldsymbol\omega$. Internal torques only move momentum between parts of the spacecraft, while external torques change the total, so every spacecraft must carry at least one external torquer. Storing a large momentum bias gives gyroscopic rigidity, and whether or not to use bias, and how, defines the four stabilisation types: spinner, dual spinner, hybrid and three-axis.

> [!summary]- Exam use: quick path
> - **Use it when:** you must choose a stabilisation type, judge an inertia matrix, size a torque or precession angle, or explain wheels, dumping, torquers or sensors.
> - **Assumptions:** rigid body; rotation about the centre of mass; torques and momenta about the centre of mass; small precession angles.
> - **Method:** 1. Payload pointing first: Earth, Sun or anywhere on the sky; one fixed axis or frequent slews? 2. Fixed axis and simple payload: spinner or dual spinner; big arrays with one stiff axis: hybrid; slewing: three-axis. 3. For a spinner, check $[\mathbf I]$: zero products of inertia, $I_{zz}$ the largest, $I_{xx}=I_{yy}$. 4. Sort torques into external (change $\mathbf H$) and internal (conserve it), and choose an external torquer for dumping. 5. Pair reference sensors with inertial sensors.
> - **Common mistakes:** saying reaction wheels can dump momentum (they are internal and cannot change the total); forgetting that a spinner's body-mounted cells make it power-limited.
> - **Practise:** [[#Inertia matrix from the 2024/25 paper]] · [[SESA2024 Workbook Ch6 - Attitude Control Solutions#Q12. GEO astronomical observatory (1 arcsec for up to 1 h)|Workbook Q12]]

A body orbiting the Earth with no disturbances at all keeps its orientation unchanged: it points at the same distant star while it goes round. Whether that is good depends on the mission. A space telescope wants exactly that; an Earth-imaging camera needs the opposite, because it has to turn once per orbit to keep looking down. The ACS exists to give the payload the pointing it needs, and almost everything about it follows from one fact: a spacecraft can only rotate by exchanging angular momentum, either between its own parts or with the outside world.

Attitude control is therefore harder than it looks, and it is one of the main drivers of the spacecraft design (pre-recorded lecture). The choice of stabilisation type fixes how the arrays are mounted, where the antenna can go, how the radiators are pointed, and how carefully the mass must be distributed.

## 1. What the ACS has to do

It has three jobs:

1. Meet the payload's pointing requirements: direction, accuracy, stability and slew rate. An Earth-pointing camera and a telescope tracking a distant star have very different needs, and the payload is the strongest driver.
2. Meet the housekeeping pointing in every phase of the mission: arrays to the Sun for power, antennas to the ground stations, radiators to deep space for heat rejection, and the thrust vector along the required direction for engine burns. These are usually far less demanding than the payload: a telescope may need arcsecond pointing, a solar array a few degrees.
3. Manage the overall angular momentum of the spacecraft. This underlies the other two.

The third item is not automatic. A spacecraft on an elliptical orbit with a solar array sticking out on one side is meant to hold a fixed attitude. Each time it passes through perigee, drag on the array produces a torque, and the next pass adds another. The momentum keeps building orbit after orbit, so something must be done about it.

The ACS works as a feedback loop. Disturbance torques act on the spacecraft dynamics; attitude sensors measure the result; the on-board processor (or, in older spacecraft, the ground) compares the measurement with the demand and applies a control law; and control torquers act on the spacecraft to correct it. The ACS cannot work alone: it needs power, often propellant, data handling and communications.

![[ast_acs_loop.png|820]]

## 2. Rotational dynamics

Rotational dynamics builds up from the linear case in stages (pre-recorded lecture). For a body moving in a straight line, linear momentum is $\mathbf p=m\mathbf v$. Mass is a scalar, so the momentum is always parallel to the velocity, and Newton's second law says it changes only under an external force:

$$
\frac{d(m\mathbf v)}{dt}=\sum\mathbf F_{ext}.
$$

For rotation about a single axis, mass is replaced by the moment of inertia, because what resists angular acceleration is how the mass is distributed about the axis, not just how much there is. Two wheels of the same mass spinning at the same rate have different angular momenta if one has its mass at the rim. With $h=I_{xx}\omega$,

$$
\frac{dh}{dt}=\sum T_{ext}.
$$

In three dimensions the angular velocity $\boldsymbol\omega$ has three components and the inertia becomes a matrix:

$$
\mathbf H=[\mathbf I]\boldsymbol\omega,
\qquad
\frac{d\mathbf H}{dt}=\sum\mathbf T_{ext}.
$$

With no external torque, $\mathbf H$ is constant in both size and direction.

$\mathbf H$ need not be parallel to $\boldsymbol\omega$, because multiplying by a matrix can reorientate a vector. Physically, the cause is the mass distribution.

### The inertia matrix

$$
[\mathbf I]=\begin{bmatrix}I_{xx}&-I_{xy}&-I_{xz}\\-I_{xy}&I_{yy}&-I_{yz}\\-I_{xz}&-I_{yz}&I_{zz}\end{bmatrix},
\qquad
I_{xx}=\int(y^2+z^2)\,dm,
\qquad
I_{xy}=\int xy\,dm.
$$

The diagonal terms are the moments of inertia: the body's resistance to angular acceleration about each axis. The off-diagonal terms are the products of inertia, and they cause cross-coupling: a uniform drum spins steadily about its axis, but a small mass stuck on its rim makes the imbalance start a wobble about the other two axes. Multiplying out gives the components of $\mathbf H$:

$$
H_x=I_{xx}\omega_x-I_{xy}\omega_y-I_{xz}\omega_z,
$$

$$
H_y=-I_{xy}\omega_x+I_{yy}\omega_y-I_{yz}\omega_z,
$$

$$
H_z=-I_{xz}\omega_x-I_{yz}\omega_y+I_{zz}\omega_z.
$$

If all the products of inertia are zero, the axes are principal axes and $\mathbf H$ is parallel to $\boldsymbol\omega$ whenever the body spins about one of them. If they are not zero, a spin about a body axis produces momentum components about the other two. The 2024/25 A4 matrix of the worked example below, spun about body $z$ at $\boldsymbol\omega=(0,0,0.01)$ rad/s, shows this. Only the third column of $[\mathbf I]$ survives the multiplication:

$$
H_x=-I_{xz}\omega_z=-125\times0.01=-1.25\ \mathrm{N\,m\,s},
$$

$$
H_y=-I_{yz}\omega_z=-650\times0.01=-6.50\ \mathrm{N\,m\,s},
$$

$$
H_z=I_{zz}\omega_z=2750\times0.01=27.5\ \mathrm{N\,m\,s}.
$$

The momentum vector leans away from the spin axis by $\tan^{-1}\!\left(\sqrt{1.25^2+6.50^2}/27.5\right)=13.5^\circ$. With no external torque $\mathbf H$ must stay fixed in space, so the body cannot keep spinning steadily about $z$: the $z$ axis wobbles round $\mathbf H$. That is the cross-coupling the products of inertia cause.

On a real project one engineer watches the rising mass budget and another watches the inertia matrix, because it governs how the vehicle responds to every torque. An aircraft designer likewise needs the roll inertia to size the ailerons for a target roll rate.

## 3. Gyroscopic precession and momentum bias

### Precession

A spinning bicycle wheel held by one end of its axle swings round in a horizontal circle. Gravity on the centre of mass and the reaction at the hand form a torque that would make a stationary wheel tip over (pre-recorded lecture).

In vector terms, a torque $\mathbf T$ acting for a short time $\Delta t$ adds an angular impulse $\mathbf T\,\Delta t$ to $\mathbf H$:

$$
\mathbf H_1=\mathbf H_0+\mathbf T\,\Delta t.
$$

If $\mathbf T$ is perpendicular to $\mathbf H_0$, the impulse and the original momentum form the two shorter sides of a right-angled triangle, with $\mathbf H_1$ as the hypotenuse. The magnitude of the new momentum is

$$
|\mathbf H_1|=\sqrt{H_0^2+(T\,\Delta t)^2}=H_0\sqrt{1+\left(\frac{T\,\Delta t}{H_0}\right)^2}\approx H_0\left[1+\frac12\left(\frac{T\,\Delta t}{H_0}\right)^2\right],
$$

so it changes only to second order in the small ratio $T\,\Delta t/H_0$. The direction changes to first order. The angle $\psi$ between $\mathbf H_0$ and $\mathbf H_1$ is opposite the impulse side of the triangle:

$$
\tan\psi=\frac{T\,\Delta t}{H_0}.
$$

For a small angle in radians, $\tan\psi\approx\psi$:

$$
\psi\approx\frac{T\,\Delta t}{H_0}.
$$

Dividing by $\Delta t$ gives the precession rate $\dot\psi=T/H_0$. A rule of thumb: the displacement appears $90^\circ$ later in the direction of rotation. The mass-element argument behind it: as a small element of the rim travels through the half of its circuit where the torque accelerates it one way, it keeps gaining velocity in that direction, so the largest velocity, and hence the displacement, comes a quarter-turn after the peak acceleration.

### Momentum bias and gyroscopic rigidity

The formula says that the same disturbance impulse turns a large $H_0$ through a smaller angle. A bicycle is easier to balance at speed, and a big-wheeled bike is easier than a small one, because the wheels carry more angular momentum: $I$ grows with the square of the radius and $H=I\omega$ with the spin rate. Deliberately storing a large angular momentum to stiffen one axis is called momentum bias, and the stiffness is gyroscopic rigidity.

![[ast_gyroscopic_rigidity.png|760]]

Bias has costs as well as benefits (pre-recorded lecture):

- The stiff axis should stay in one direction for the whole mission, usually perpendicular to the orbit plane, because reorienting it takes a large torque applied for a long time, which costs fuel.
- A biased body has a nutation mode: hit it with an impulsive torque and the spin axis wobbles, and in space that wobble would continue indefinitely unless damped, so passive or active dampers must be carried. A bicycle wheel's nutation decays quickly in air.
- The torque response changes. An unbiased spacecraft fired with a torque pulse starts turning, coasts at constant rate, and stops with an opposite pulse. A biased one needs a steady torque to turn at a steady rate (it precesses), with nutation laid on top.

### External torquers are compulsory

The ACS engineer can only do two things: move momentum around inside the spacecraft (conservation of angular momentum, no external torque) or change the total with an external torque (Newton's second law). The environment always applies external torques, for example drag in low orbit, so momentum builds up over the mission. A spacecraft that carries nothing able to apply an external torque will eventually lose control. That is why 2016/17 Q1(iii) asks why external torquers are mandatory.

## 4. The four stabilisation types

The first decision is whether to use bias at all. With bias there are three ways to store it: spin the whole body, spin most of it, or spin a small wheel inside it. Without bias the spacecraft is three-axis stabilised. It is one of the most important choices in the design, because every other subsystem has to work around it.

### Type 1: spinner

The whole spacecraft spins, typically at 10 to 60 rpm: a large inertia at a low rate. For long-term stability the inertia matrix has to satisfy three conditions:

1. the spin axis is the axis of maximum moment of inertia, $I_{zz}>I_{xx},I_{yy}$;
2. the products of inertia are zero, so the spin axis is a principal axis and keeps a constant direction;
3. the transverse moments are equal, $I_{xx}=I_{yy}$, so the body is symmetric about the spin axis and responds to a torque with a constant precession.

Spin about the minimum-inertia axis is only acceptable for short periods, such as a solid-motor burn during transfer. Spin is most stable when the mass distribution is symmetric about the spin axis, so every subsystem engineer has to keep their hardware balanced, which is why Cluster carried trim masses that could be adjusted to balance it after the instruments were fitted.

The system consequences: there is no room for large deployable arrays, so the solar cells are body-mounted on the drum and the spacecraft is power-limited; the antenna has to be omnidirectional or despun; payloads that do not scan have limited places to mount; and thermal design is mixed, because radiators are hard to point but the spin evens out the heating. Meteosat Second Generation turns the limitation into a feature: its imager uses the spin to sweep across the Earth one strip per revolution, stepping down a strip each time, which is whiskbroom scanning.

> [!tip] Pushbroom and whiskbroom
> A pushbroom imager has a long line of detectors across the ground track and lets the spacecraft's motion build up the image line by line. A whiskbroom imager has fewer detectors and sweeps them across the track with a mechanism or, on a spinner, the spin itself. Pushbroom has no moving parts, so modern Earth-observation satellites prefer it. Pushbroom sizing is covered in [[Swath Width and Push-Broom Imaging]].

### Type 2: dual spinner

Most of the spacecraft spins for stability, but a despun platform on top stays still and carries, typically, a directional antenna or a payload that must point. That eases the antenna and payload constraints, but the bearing between the two parts has to carry power and signals across a rotating joint (slip rings), which is a reliability worry on a spacecraft nobody can repair. The friction in the bearing is manageable. The spinning section still dominates, so the spacecraft is still largely power-limited, the inertia matrix is still tightly constrained, and nutation still has to be damped.

Giotto, ESA's Halley's Comet fly-by probe, is an example. Spin gave it stability against dust impacts during the fly-by, while a despun high-gain antenna kept the link to Earth. During the encounter it was hit by a dust particle, nutated, and lost contact; spin stability let it recover and continue. Intelsat 6 and the Galileo Jupiter probe also used this type.

### Type 3: hybrid (momentum-bias wheel)

Instead of a large mass spinning slowly, a small wheel spins fast, at thousands of rpm, inside a body that is otherwise three-axis controlled. The same bias $H=I\omega$ comes from small $I$ and large $\omega$. The body is now free to carry large deployable arrays, so the spacecraft is no longer power-limited, and the inertia matrix is much less constrained. The cost is the wheel itself: mass and volume that do nothing for the mission objective except stabilise it, plus nutation still to be dealt with. The wheel's speed can be varied by about ±10 % to store or release momentum about its axis. GPS satellites and the Eurostar 3000 communications platform use this type.

### Type 4: three-axis stabilised (zero bias)

No significant momentum is stored about any axis, so the spacecraft can slew freely to point anywhere. Space telescopes (Hubble, JWST), Earth observers (SPOT 5, Envisat) and Magellan, which mapped Venus by radar near periapsis and turned its dish to Earth near apoapsis, are all three-axis. Hubble does carry reaction wheels, but they run near zero speed and are not there to create bias. The cost is continuous active control.

| | 1 Spinner | 2 Dual spinner | 3 Hybrid | 4 Three-axis |
|---|---|---|---|---|
| Bias from | large $I$, slow spin (10–60 rpm) | most of body spinning | small wheel, thousands of rpm | none |
| Arrays | body-mounted: power-limited | body-mounted: power-limited | deployable | deployable |
| Antenna | omni or despun | despun directional | fixed directional | fixed directional |
| Inertia matrix | tightly constrained | tightly constrained | relaxed | free |
| Nutation | yes | yes | yes | no |
| Examples | Meteosat SG, Cluster | Giotto, Intelsat 6, Galileo | GPS, Eurostar 3000 | Hubble, JWST, SPOT 5, Envisat, Magellan |

## 5. Torques and torquers

Torques split two ways. External torques come from interaction with the environment and change the total angular momentum; internal torques come from interaction between parts of the spacecraft and conserve it. In each category there are disturbance torques, which happen to the spacecraft, and torquers, which the ACS controls.

### External disturbance torques

| Disturbance | Where it matters most | Notes |
|---|---|---|
| Aerodynamic | below about 500 km (felt up to about 1000 km) | depends on shape, deployables and attitude |
| Gravity gradient | up to about 30 000–40 000 km | depends on the inertia matrix: long, thin bodies such as telescopes and space stations feel it most |
| Solar radiation pressure | all altitudes | about $5\times10^{-6}\ \mathrm{N/m^2}$ near the Earth; dominant above roughly 500 km for large, asymmetric shapes |
| Magnetic | up to about 30 000–40 000 km | on-board currents interact with the Earth's field |
| Thrust misalignment | all altitudes, during burns | 1 kN offset by 1 mm from the centre of mass gives 1 N m |

Gravity gradient arises because gravity falls off as $1/r^2$: a long body tilted from the local vertical has its lower end pulled slightly harder than its upper end, and the difference rotates it towards the vertical, which is its stable orientation. It can be used deliberately for passive stabilisation; one example is a long, thin ocean-measuring satellite, and Workbook Q10 asks for the mass distribution that suits it. Magnetic torques are also used passively, often on CubeSats. Solar radiation pressure acts at every altitude in Earth orbit, so a disturbance torque that depends on the spacecraft's shape exists at all orbital altitudes (Quiz 1 walk-through).

### External torquers

Every spacecraft must carry at least one external torquer. **Thrusters** give any torque size, with on/off control that can be pulsed finely, but they use finite propellant. A pure couple about one axis in both senses needs four thrusters, so three axes need twelve, and redundancy can take it to sixteen, each with its feed lines.

**Magnetorquers** are electromagnets along each axis, often with a diagonal spare. They use no propellant and have no moving parts, only power, but their torque is small and slow. It exists only where there is a well-known magnetic field, so an on-board field model is needed, and because the torque is $\mathbf m\times\mathbf B$ there is none about the field line.

**Adjustable geometry**, such as trim tabs on the array, uses solar radiation pressure. It needs no propellant and gives very low torque, but keeping a GEO satellite on station a year longer can be worth millions.

### Internal disturbances and torquers

Internal disturbances are mechanisms (deploying or rotating arrays, moving sensors), propellant slosh, and astronauts pushing off walls. The controllable internal torquers are wheels: a flywheel with most of its mass at the rim, plus a motor and electronics.

| Device | Speed | Use |
|---|---|---|
| Reaction wheel | low, either direction, nominally near zero | control: spin it one way and the body turns the other |
| Momentum wheel | high (about 6500 rpm), one direction, ±10 % | bias for gyroscopic stiffness |
| Control moment gyro | constant speed, gimballed | large torques on large spacecraft, e.g. the ISS |

A person standing on a turntable and holding a wheel shows all three: spinning the wheel up turns them the other way, spinning an already-spinning wheel faster turns them further, and tilting the spinning wheel (gimballing) pulls them round through gyroscopic precession. The ISS has four CMGs whose momenta cancel in their neutral position; tilting them sets the station turning, and when all four line up they are saturated and the Russian segment's thrusters must hold attitude while they are returned to neutral. CMGs are heavy and complex, so only large spacecraft use them.

## 6. Momentum storage and dumping

Wheels store angular momentum; their motor controls the flow between wheel and body, and they provide the primary pointing control.

Some momentum changes are periodic. A satellite in a circular orbit can stay Earth-pointing by rotating once per orbit at a constant rate. On an elliptical orbit the orbital angular rate $\dot\theta=h/r^2$ varies, by Kepler's second law, so the body has to turn faster at perigee than at apogee. Doing that with thrusters would burn propellant all the time. A wheel can absorb the difference instead: it gives momentum to the body near perigee and takes it back near apogee, and after one orbit everything returns to where it started. Sizing the wheel capacity for this avoids using external torquers for any manoeuvre whose before and after momenta are equal.

Other changes are secular. With a solar array that feels a drag torque at every perigee pass, the external torque adds the same impulse each orbit. The wheel has to spin a little faster every time to hold attitude, and eventually reaches its maximum speed, at which point it is saturated and control would be lost. Before that, the momentum must be dumped: the wheel is torqued back down while an external torquer (thrusters pulsing, or magnetorquers over a longer period) holds the attitude. Europe calls this momentum dumping; the USA calls it wheel desaturation. Using magnetorquers or trim tabs continuously keeps dumping small and saves propellant.

![[ast_wheel_momentum_elliptic.png|800]]

## 7. Attitude sensors

The ACS cannot control attitude more accurately than it can measure it: if you can only measure to ±1°, you can only control to ±1°. There are two families (2019/20 A1(iv)):

- Reference sensors give the direction to a reference object in body axes. Their accuracy is limited by the reference: star trackers reach arcseconds, Sun sensors and Earth (horizon) sensors arcminutes, magnetometers degrees, and GPS can also be used. One arcminute is $1/60$ of a degree and one arcsecond $1/3600$.
- Inertial sensors, such as gyroscopes, measure changes in attitude only. They keep working while the reference object is eclipsed or below the horizon, but they drift and must be recalibrated against a reference sensor.

On an aircraft at night, a passenger can track a star through the window (reference) or, with the blind closed, feel the turn through the inner ear (inertial). The star can disappear behind cloud and the inner ear drifts, so both are used. Real spacecraft fly both: the Shuttle carried star trackers and an inertial measurement unit, as did Aeolus. MEMS technology, as in phone accelerometers, has changed what is possible.

## 8. On-board processing and operating modes

Modern on-board computers close the loop thousands of times a second, so routine control is done on board, with the ground monitoring and resetting and making high-level decisions such as which target to slew to; thirty years ago much more had to go to the ground. Early in the design you define the payload operation plan and the ACS modes: an initial acquisition mode, which finds the Sun and Earth before any sensitive sensor is exposed and doubles as the safe mode (used during solar storms, for example); a thruster control mode for station-keeping and momentum dumping; and a normal mode with wheels and fine sensors running.

## 9. Impact of the ACS on the spacecraft

The stabilisation type and the pointing requirements have a profound effect on the configuration. Types 1 and 2 bring limited power from body-mounted cells, awkward radiator placement, restricted antennas and payload mounting, the bearing reliability issue for type 2, tight inertia-matrix control and nutation damping. Types 3 and 4 allow big arrays and directional antennas but bring large temperature gradients across a non-spinning body, and type 3 still needs nutation damping. There are many workable designs, and the best one has changed over the years as sensors and computing have improved.

## Worked examples

### Inertia matrix from the 2024/25 paper

2024/25 A4 gives

$$
[\mathbf I]=\begin{bmatrix}1250&-550&-125\\-550&1250&-650\\-125&-650&2750\end{bmatrix}\ \mathrm{kg\,m^2}
$$

and asks which stabilisation type it suits. The products of inertia are large (550 and 650 kg m² against moments of 1250–2750), so the body axes are not principal axes and a spin about $z$ would wobble. It is not a spinner; it is three-axis stabilised. The eigenvalues, the principal moments, are 556, 1698 and 2996 kg m² (computed with NumPy), so even about its principal axes it has no symmetry pair to satisfy the spinner's third condition.

> [!check] Trace and principal axis
> The sum of the eigenvalues equals the trace of the matrix: $556+1698+2996=5250=1250+1250+2750$ kg m². The largest principal axis has direction cosines $(0.047,-0.362,0.931)$ in body axes, so it lies $21^\circ$ from body $z$ ($\cos^{-1}0.931=21.4^\circ$). Even the best spin axis is well off the body axis a designer would have chosen.

### Precession of a spinner under a small torque

*(Suggested, not lecturer-set.)* A spinner with $I_{zz}=500\ \mathrm{kg\,m^2}$ spins at 30 rpm, so

$$
H_0=500\times30\times\frac{2\pi}{60}=1571\ \mathrm{N\,m\,s}.
$$

A disturbance torque of $10^{-4}$ N m perpendicular to the spin axis acts for one day:

$$
\psi=\frac{T\,\Delta t}{H_0}=\frac{10^{-4}\times86\,400}{1571}=5.5\times10^{-3}\ \mathrm{rad}=0.32^\circ.
$$

A momentum wheel of $I=0.05\ \mathrm{kg\,m^2}$ at 6500 rpm stores

$$
H_w=0.05\times6500\times\frac{2\pi}{60}=34.0\ \mathrm{N\,m\,s},
$$

so the same impulse of 8.64 N m s gives $T\,\Delta t/H_w=0.254$. That is no longer small: the small-angle form says $14.5^\circ$, while $\tan^{-1}0.254=14.2^\circ$. Either way, a hybrid gets much less stiffness than a spinner unless it dumps or controls actively.

### Thrust misalignment during a burn

For example, a 1 kN engine whose thrust line misses the centre of mass by 1 mm produces

$$
T=Fd=1000\times0.001=1\ \mathrm{N\,m}.
$$

Over a 100 s burn that is an angular impulse of 100 N m s, three times the 34 N m s wheel above. Large burns are therefore controlled with thrusters, or the spacecraft is spun up during a solid-motor burn so that the misalignment averages out and the spin gives rigidity (the OMOTENASHI retro-motor in 2022/23 B1).

### Wheel momentum for Earth-pointing on an ellipse

*(Suggested, not lecturer-set; the elliptical-orbit pointing case.)* A spacecraft with pitch inertia 800 kg m² is on a 500 by 6500 km altitude orbit ($r_p=6878$ km, $r_a=12\,878$ km, $e=0.304$) and must stay Earth-pointing. Earth-pointing means the body turns at the orbital rate $\dot\theta$. The orbit has $a=(6878+12\,878)/2=9878$ km, and the angular momentum is

$$
h=\sqrt{\mu a(1-e^2)}=\sqrt{398\,600\times9878\times(1-0.304^2)}=5.979\times10^4\ \mathrm{km^2/s}.
$$

From $h=r^2\dot\theta$ the orbital rate at each apsis is

$$
\dot\theta_p=\frac{h}{r_p^2}=\frac{5.979\times10^4}{6878^2}=1.264\times10^{-3}\ \mathrm{rad/s},
\qquad
\dot\theta_a=\frac{h}{r_a^2}=\frac{5.979\times10^4}{12\,878^2}=3.60\times10^{-4}\ \mathrm{rad/s}.
$$

The body's angular momentum about pitch therefore changes by

$$
\Delta H=800\,(1.264-0.360)\times10^{-3}=0.72\ \mathrm{N\,m\,s}
$$

every half orbit, and a reaction wheel with at least that capacity absorbs it with no propellant. This is the periodic curve in the figure in §6.

## Links

- Parent: [[SESA2024 Astronautics Hub]]
- Previous: [[SESA2024 01 - Systems Engineering and Spacecraft Design]]
- Next: [[SESA2024 07 - Spacecraft Propulsion]]
- Concepts: [[Inertia Matrix]] · [[Momentum Bias and Gyroscopic Rigidity]] · [[Spacecraft Stabilisation Types]] · [[Reaction Wheels and Momentum Dumping]] · [[Attitude Sensors and Torquers]]
- Workbook: [[SESA2024 Workbook Ch6 - Attitude Control Solutions]]
- Feedback control and Euler angles: [[SESA2027 Aerospace Mechanics & Control Hub]] · [[Euler Angles and Rotation Matrices]]
- Year 1: angular momentum, [[FEEG1002 D5 - Angular Impulse and Momentum]]; mass moment of inertia, [[FEEG1002 D8 - Kinetics of Rigid Bodies]]; magnetorquers and the Lorentz force, [[FEEG1004 A2 - Magnetism, Induction and the Lorentz Force]]; wheel motors, [[FEEG1004 C5 - DC Motors - Torque, Back EMF and Efficiency]]

## Sources

- `Chapter 6 - Attitude Control - prerecorded material.pdf` with transcript `SESA2024 Lecture Chapter 6 - Attitude Control - prerecorded material.txt` (rotational dynamics, inertia matrix, precession, bias)
- Chapter 6 live lectures (Dr H. Sykulska-Lawrence): `SESA2024 Lecture 2025-10-07.txt` (purposes, spinner), `SESA2024 Lecture 2025-10-09.txt` (dual spinner, hybrid, three-axis, external disturbances), `SESA2024 Lecture 2025-10-14.txt` (torquers, wheels, momentum storage, sensors) and `SESA2024 Lecture 2025-10-16.txt`, ll. 76–290 (sensors, modes, system impact)
- `SESA2024 Lecture 2025-10-28 - Quiz 1 Worked Solutions - Drop In session.txt`
- Fortescue, Stark and Swinerd, *Spacecraft Systems Engineering*, Ch. 9
- Figures: `generate_ast_ch6_attitude_figures.py` (`ast_acs_loop`, `ast_gyroscopic_rigidity`, `ast_wheel_momentum_elliptic`) and `ast_momentum_dumping` (`generate_ast_extra_figures.py`). Matrix and precession numbers recomputed with NumPy.

## Self-study tasks

### Core

- [ ] Primary functions of the ACS and the closed-loop sketch (Workbook Ch6 Q1–Q2). → [[#1. What the ACS has to do]] · [[SESA2024 Workbook Ch6 - Attitude Control Solutions#Q1. Primary functions of the ACS|Workbook Q1]]
- [ ] The four generic stabilisation types, with pros, cons and examples (Workbook Ch6 Q4; asked of the class, 2025-10-07 and 2025-10-09). → [[#4. The four stabilisation types]] · [[SESA2024 Workbook Ch6 - Attitude Control Solutions#Q4. The four generic stabilisation types|Workbook Q4]]
- [ ] The ideal inertia matrix for a pure spinner, and the 2024/25 A4 matrix (Workbook Ch6 Q11; derived with the class, 2025-10-07, ll. 326–400). → [[#Type 1: spinner]] · [[#Inertia matrix from the 2024/25 paper]] · [[SESA2024 Workbook Ch6 - Attitude Control Solutions#Q11. Ideal inertia matrix for a pure spinner with spin axis z|Workbook Q11]]
- [ ] External versus internal torques, and why an external torquer is mandatory (Workbook Ch6 Q5; 2016/17 Q1(iii)). → [[#External torquers are compulsory]] · [[SESA2024 Workbook Ch6 - Attitude Control Solutions#Q5. External vs internal torques|Workbook Q5]]
- [ ] How a reaction wheel works, and momentum dumping (Workbook Ch6 Q6). → [[#6. Momentum storage and dumping]] · [[SESA2024 Workbook Ch6 - Attitude Control Solutions#Q6. How a reaction wheel works; momentum dumping|Workbook Q6]]
- [ ] Quiz 1: does any disturbance torque depend on shape at all orbital altitudes? (Quiz 1 walk-through, ll. 1–30) → [[#External disturbance torques]]

### Further practice

- [ ] Explain gyroscopic rigidity with a vector diagram (2022/23 A2, 4 marks; pre-recorded lecture, ll. 251–300). → [[#Momentum bias and gyroscopic rigidity]]
- [ ] Reference versus inertial sensors (2019/20 A1(iv)). → [[#7. Attitude sensors]]
- [ ] The GEO astronomical observatory ACS design (Workbook Ch6 Q12). → [[SESA2024 Workbook Ch6 - Attitude Control Solutions#Q12. GEO astronomical observatory (1 arcsec for up to 1 h)|Workbook Q12]]
- [ ] Why spin suits GEO weather imaging but not LEO imaging (2021/22 A2). → [[#Type 1: spinner]] · [[SESA2024 2021-22 Exam Solutions#Section A|2021/22 Section A]]
- [ ] Mass distribution for gravity-gradient stabilisation, and passive versus active stabilisation (Workbook Ch6 Q9–Q10). → [[#External disturbance torques]] · [[SESA2024 Workbook Ch6 - Attitude Control Solutions#Q10. Mass distribution for gravity-gradient stabilisation|Workbook Q10]]
- [ ] Count the thrusters needed for pure couples about three axes, with redundancy (asked of the class, 2025-10-14, ll. 90–130). → [[#External torquers]]
