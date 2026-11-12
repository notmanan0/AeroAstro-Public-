---
title: "FEEG1004 A2 - Magnetism, Induction and the Lorentz Force"
module: "FEEG1004 Electronics"
type: topic
stream: "Part A: Electrical Fundamentals and DC Circuits"
order: 2
tags: [feeg1004, fundamentals, magnetism, flux, faraday, lenz, lorentz, maxwell]
aliases: ["Lecture 2a-2b", "Magnetism and induction", "Faraday's law", "Electromagnetism"]
date: 2026-09-27
status: lectured
coverage: "2a Magnetism and Induction (ll. 1-85); 2b Other magnetic effects (ll. 1-152); W3 L2 A 16 October 2024 (ll. 98-117, 216-326, 342-458)"
parent: ["[[FEEG1004 Electronics Hub]]"]
prerequisites: ["[[FEEG1004 A1 - Electrostatics, Potential and Current]]"]
next_topics: ["[[FEEG1004 A3 - DC Circuit Laws - Ohm, KCL, KVL and Dividers]]"]
key_concepts: ["[[Magnetic Flux and Flux Density]]", "[[Faraday's Law and Lenz's Law]]", "[[Lorentz Force]]"]
tutorial_sheets: ["[[FEEG1004 Tutorial 1 - Electrostatics, Magnetism and Resistors Solutions]]", "[[FEEG1004 Tutorial 5 - Faraday, Generators and Transformers Solutions]]"]
sources:
  - "02 - Sources/S1 Fundamentals/S1-W03-2ab Magnetism and Induction - Recorded.pdf"
  - "02 - Sources/S1 Fundamentals/S1-W03 Magnetism - Interactive.pdf"
  - "02 - Sources/Lectures/FEEG1004 Lecture 2020-08-11 - 2a Magnetism and Induction EC 11 August 2020 at 08 58 48.txt"
  - "02 - Sources/Lectures/FEEG1004 Lecture 2020-08-11 - 2b Other magnetic effects EC 11 August 2020 at 09 19 28.txt"
  - "02 - Sources/Lectures/FEEG1004 Lecture 2 - W3 L2 A 16 October 2024 at 10 59 29.txt"
---

# FEEG1004 A2 - Magnetism, Induction and the Lorentz Force

> [!abstract] Summary
> Magnetic flux measures the field passing through an area, and a changing flux linkage induces an EMF, $\mathcal E=-N\,d\Phi/dt$. Moving charges experience the Lorentz force $\mathbf F=q(\mathbf E+\mathbf v\times\mathbf B)$, which gives $F=BIL$ for a straight conductor perpendicular to a uniform magnetic field. Current also creates a magnetic field, so induction and force together explain generators, interacting wires and magnetic braking.

> [!summary]- Exam use: quick path
> - **Use it when:** finding a coil's induced voltage, the direction of a magnetic force, or the energy transfers in induction.
> - **Assumptions:** use the normal component of the field; identical flux through all turns for $N\Phi$; uniform field for $BA\cos\theta$ and $BIL$.
> - **Method:** 1. Draw the field and choose positive directions. 2. Find flux or the charge/current direction. 3. Differentiate flux linkage or apply the cross product. 4. Check the sign against Lenz's law or Fleming's left-hand rule.
> - **Common mistakes:** measuring the flux angle from the coil plane rather than its normal; using electron motion as the conventional-current direction.
> - **Practise:** [[#Worked examples]] · [[FEEG1004 Tutorial 1 - Electrostatics, Magnetism and Resistors Solutions#Q5: 10-turn, 0.1 m² coil rotating at 20 Hz in 2 T|Tutorial 1 Q5]]

A magnet produces a field throughout the surrounding space. A coil responds to how much of this field passes through its enclosed area. Moving the coil, turning it or changing the field can change that flux and produce an EMF, even though no battery is connected.

There is also a mechanical effect. A moving charge feels a force perpendicular to its motion and to the magnetic field. When many charges carry current through a wire, their combined force acts on the wire. The induced current can therefore exert a force back on the motion that produced it.

Driving a generator requires mechanical work because its induced current resists the driving motion, so the electrical and mechanical energy transfers are linked. A freely moving conducting ring can lose mechanical energy as heat while its current and magnetic field change.

## 1. Magnetic field and flux

**Magnetic flux density** $\mathbf B$ describes the magnetic field and is measured in tesla, $\mathrm T$. Field lines point from north to south outside a bar magnet and return through it. They form closed loops; there is no isolated magnetic pole in this model. Closer lines represent a stronger field.

A cross, $\times$, represents a field directed into the page. A dot, $\bullet$, represents a field directed out of the page. These symbols specify a direction perpendicular to the drawing, rather than a direction along it.

**Magnetic flux** is the integral of the normal component of the field over an area. A unit normal $\hat{\mathbf n}$ fixes its positive direction:

$$
d\mathbf A=\hat{\mathbf n}\,dA.
$$

Then

$$
\Phi=\int_A\mathbf B\cdot d\mathbf A.
$$

For a planar coil in a uniform field, the angle $\theta$ between $\mathbf B$ and the area normal is constant. Taking the dot product gives

$$
\Phi=\int_A B\cos\theta\,dA.
$$

The constant factors can be taken outside the integral:

$$
\Phi=B\cos\theta\int_A dA.
$$

Therefore

$$
\Phi=BA\cos\theta.
$$

Flux is largest in magnitude when the field is perpendicular to the coil plane. It is zero when the field lies in the plane. Its units are

$$
1\,\mathrm{Wb}=1\,\mathrm{T\,m^2}=1\,\mathrm{V\,s}.
$$

For $N$ turns linking the same flux, the flux linkage is $N\Phi$. Flux per turn and flux linkage must be distinguished when using Faraday's law.

## 2. Faraday's law and Lenz's law

Faraday's law gives the EMF around a coil from the rate of change of its flux linkage:

$$
\mathcal E=-\frac{d(N\Phi)}{dt}.
$$

For a fixed number of turns,

$$
\mathcal E=-N\frac{d\Phi}{dt}.
$$

The sign refers to a chosen positive direction around the winding, paired with the positive area normal by the right-hand rule. Reversing the measurement leads reverses the measured voltage.

**Lenz's law** gives the physical interpretation: if the coil is closed, the induced current creates a field opposing the change in linked flux. An increasing flux is opposed by a field in the opposite direction. A decreasing flux is opposed by a field in the original direction. The induced field opposes the change, rather than necessarily opposing the original field.

An EMF can exist in an open coil without a sustained current. The mechanical opposition associated with induced current depends on the circuit being able to carry that current.

### Reading a flux graph

The EMF is the negative gradient of the flux graph, multiplied by the number of turns. It is zero at a smooth maximum or minimum of flux. A steeply rising flux produces a large negative EMF; a steeply falling flux produces a large positive EMF for the same reference direction.

In the sideways passage of a coil past a bar magnet, flux can reverse sign because the return field crosses the area in the opposite direction. Counting signed crossings explains the sequence of positive flux, zero flux and negative flux. The central negative minimum has zero EMF, despite the large magnitude of flux there.

For a long magnet passing axially through a coil, the simpler pulse picture below applies. Flux rises, reaches a maximum when the magnet is centred, then falls. The two EMF pulses have opposite signs. The curves are qualitative; their plotted amplitudes are normalised.

![[ee_a2_magnet_through_coil.png|900]]

The induced electric field circulates around the changing flux. The electrostatic picture of a single potential whose differences sum to zero around a closed path does not describe this induced EMF by itself.

## 3. Force on moving charges

The Lorentz force law combines electric and magnetic forces:

$$
\mathbf F=q(\mathbf E+\mathbf v\times\mathbf B).
$$

Separating the contributions,

$$
\mathbf F= q\mathbf E+q\mathbf v\times\mathbf B.
$$

For the magnetic part alone, with $\alpha$ the angle between velocity and field,

$$
|\mathbf F_B|=|q|vB\sin\alpha.
$$

A stationary charge has no magnetic force. Motion parallel or antiparallel to the field also gives zero magnetic force. Motion perpendicular to the field gives the largest magnitude for fixed $|q|$, $v$ and $B$.

Fleming's left-hand rule uses the first finger for field, the second finger for conventional current and the thumb for force. For a positive charge, the current finger points along its velocity. For a negative charge, it points opposite to the velocity.

### Checking the particle directions

Right is $+x$, up is $+y$ and out of the page is $+z$. For the negative particle moving upwards in a rightward field,

$$
\mathbf v=v\hat{\mathbf y},\qquad \mathbf B=B\hat{\mathbf x}.
$$

The cross product is

$$
\mathbf v\times\mathbf B=-vB\hat{\mathbf z}.
$$

Multiplying by the negative charge reverses it:

$$
\mathbf F_B=|q|vB\hat{\mathbf z}.
$$

The force is out of the page. The positive particle moving directly left has velocity antiparallel to the field and therefore no magnetic force.

For particles entering upwards into a field out of the page, positive charges initially bend right and negative charges bend left. A straight track is consistent with an uncharged particle under these conditions. Track curvature alone does not establish a particle's mass.

### Why the magnetic force does no work

Instantaneous mechanical power is force dotted with velocity. For the magnetic contribution,

$$
P_B=\mathbf F_B\cdot\mathbf v.
$$

Substituting the Lorentz force,

$$
P_B=q(\mathbf v\times\mathbf B)\cdot\mathbf v.
$$

The cross product is perpendicular to velocity, so

$$
P_B=0.
$$

A magnetic field can change a particle's direction without changing its speed. In a generator, mechanical work and the electric forces associated with charge redistribution account for the electrical energy transfer.

## 4. Force on a current-carrying wire

Consider a straight segment of length $L$ in a uniform field perpendicular to the segment. Suppose the mobile charge within it has total magnitude $Q$ and drift speed $v$. The time taken to move through the segment is

$$
\Delta t=\frac{L}{v}.
$$

Using the definition of current magnitude,

$$
I=\frac{Q}{\Delta t}.
$$

Substituting the transit time,

$$
I=\frac{Qv}{L}.
$$

Multiplying by the segment length,

$$
IL=Qv.
$$

The summed magnetic-force magnitude on those carriers is

$$
F=BQv.
$$

Hence

$$
F=BIL.
$$

With $\mathbf L$ directed along conventional current, the vector form is $\mathbf F=I\mathbf L\times\mathbf B$. For an inclined straight conductor, the magnitude is $BIL\sin\alpha$. The perpendicular-field formula must not be used without checking the geometry.

## 5. Fields from currents and the falling ring

The right-hand grip rule gives the field around a current: the thumb points along conventional current and the curled fingers give the field direction. Electron motion is opposite to that thumb direction.

For two vertical wires, let the left wire carry current upwards and the right wire carry current downwards. At the right wire, the field from the left wire points into the page. Downward current crossed with that field gives a rightward force, away from the left wire. Reversing the right-hand current reverses this force. Opposite parallel currents repel; currents in the same direction attract.

A conducting ring falling towards a magnet experiences increasing linked flux. Motion through the curved field drives charges around the ring; equivalently, Faraday's law predicts an induced EMF. The resulting current has its own magnetic field and exerts a force opposing the approach. With a light ring and a strong magnet, this force is large enough to reverse the fall.

At the lowest turning point, the ring has zero vertical speed but can still carry current. Energy is stored in its magnetic field. As it rises, magnetic energy returns to mechanical energy. Resistance converts part of the energy to heat, so successive bounces decay. The changing field pattern is the sum of the magnet's field and the ring current's field.

Maxwell's equations collect these interactions: charge produces electric field; magnetic field lines close; changing magnetic field produces circulating electric field; and current or changing electric field produces circulating magnetic field. Their differential forms are context here and are not required for the calculations in this topic.

## Worked examples

### Rotating coil and induced voltage

Tutorial Sheet 1 Q5 gives $N=10$, $A=0.1\,\mathrm{m^2}$, $B=2\,\mathrm T$ and rotation frequency $f=20\,\mathrm{Hz}$. Assume a uniform field and constant angular speed, with the coil normal aligned with the field at $t=0$.

Convert cycles per second to angular speed:

$$
\omega=2\pi f.
$$

$$
\omega=2\pi(20\,\mathrm{Hz})=40\pi\,\mathrm{rad\,s^{-1}}.
$$

The flux per turn is

$$
\Phi(t)=BA\cos(\omega t).
$$

$$
\Phi(t)=(2\,\mathrm T)(0.1\,\mathrm{m^2})\cos(40\pi t)=0.2\cos(40\pi t)\,\mathrm{Wb},
$$

where $t$ is in seconds. Differentiate before multiplying by the turns:

$$
\frac{d\Phi}{dt}=-BA\omega\sin(\omega t).
$$

$$
\mathcal E(t)=NBA\omega\sin(\omega t).
$$

$$
\mathcal E(t)=10(2\,\mathrm T)(0.1\,\mathrm{m^2})(40\pi\,\mathrm{rad\,s^{-1}})\sin(40\pi t).
$$

$$
\mathcal E(t)=251.33\sin(40\pi t)\,\mathrm V.
$$

This is a peak amplitude, rather than a peak-to-peak or RMS value. The period is $1/(20\,\mathrm{Hz})=0.050\,\mathrm s$.

![[ee_t1_q5_rotating_coil.png|900]]

> [!check] Flux and voltage extrema
> At $t=0$, flux is at its maximum and EMF is zero. At a quarter-period, $t=0.0125\,\mathrm s$, flux crosses zero and EMF reaches $+251.33\,\mathrm V$. This agrees with the negative-gradient rule.

### Force on an east–west cable

Tutorial Sheet 5 Q3 gives a northward field $B=1\times10^{-4}\,\mathrm T$, cable length $L=10\,\mathrm m$ and current $I=1\,\mathrm{kA}$. Assume that field is uniform along the straight cable. East–west is perpendicular to north, so

$$
F=BIL.
$$

$$
F=(1\times10^{-4}\,\mathrm T)(1\times10^3\,\mathrm A)(10\,\mathrm m).
$$

$$
F=1.00\,\mathrm N.
$$

Eastward conventional current gives an upward force because east crossed with north is up. Westward current gives a downward force. The question specifies the cable orientation without selecting a current direction, so the force direction needs that qualification.

The stated cable resistance does not enter $BIL$ when current is already given. It determines heating: $P=I^2R=(1000\,\mathrm A)^2(0.1\,\Omega)=100\,\mathrm{kW}$.

> [!check] Direction and dimensions
> Reversing current reverses force without changing its $1.00\,\mathrm N$ magnitude. The units also agree: $\mathrm{T\,A\,m}=\mathrm N$.

## Links

- Parent: [[FEEG1004 Electronics Hub]]
- Previous: [[FEEG1004 A1 - Electrostatics, Potential and Current]]
- Next: [[FEEG1004 A3 - DC Circuit Laws - Ohm, KCL, KVL and Dividers]]
- Concepts: [[Magnetic Flux and Flux Density]] · [[Faraday's Law and Lenz's Law]] · [[Lorentz Force]]
- Applications: [[FEEG1004 C1 - Magnetic Circuits, Faraday's Law and Force on Conductors]] · [[Linear Variable Differential Transformer]]

## Sources

- `S1-W03-2ab Magnetism and Induction - Recorded.pdf`, pp. 2–26; `FEEG1004 Lecture 2020-08-11 - 2a Magnetism and Induction EC 11 August 2020 at 08 58 48.txt` (ll. 1–85), and `FEEG1004 Lecture 2020-08-11 - 2b Other magnetic effects EC 11 August 2020 at 09 19 28.txt` (ll. 1–152).
- `S1-W03 Magnetism - Interactive.pdf`, pp. 7, 11–12, 14–19; `FEEG1004 Lecture 2 - W3 L2 A 16 October 2024 at 10 59 29.txt` (ll. 98–117, 216–326, 342–458). Electrostatic revision on pp. 8–10 belongs with A1.
- `Tutorial Sheet 01 - Electrostatics, Magnetism & Resistors.pdf`, Q5; `Tutorial Sheet 05 - Electric Machines 1 - Faraday, Generators & Transformers.pdf`, Q1 and Q3.
- Both numerical examples, quarter-period check and heating calculation checked in Python.

## Self-study tasks

### Core

- [ ] Derive the rotating-coil voltage, stating its phase reference (Tutorial Sheet 1 Q5). → [[FEEG1004 Tutorial 1 - Electrostatics, Magnetism and Resistors Solutions#Q5: 10-turn, 0.1 m² coil rotating at 20 Hz in 2 T|Tutorial 1 Q5]]; full working in [[#Rotating coil and induced voltage]].
- [ ] Sketch flux and EMF for the sideways passage past a magnet (2a transcript ll. 74–84). → [[#Reading a flux graph]].
- [ ] Derive the force on a perpendicular current-carrying wire from the Lorentz force (2b transcript ll. 112–115). → [[#4. Force on a current-carrying wire]].
- [ ] Find the two-particle force directions (2b transcript ll. 96–111), then identify the four track charges (W3 transcript ll. 275–326). → [[#Checking the particle directions]].
- [ ] Explain the falling ring's bounce, field changes and energy losses (W3 transcript ll. 342–425). → [[#5. Fields from currents and the falling ring]].

### Further practice

- [ ] Sketch the axial falling-magnet waveforms and mark maximum EMF and the centred magnet (Tutorial Sheet 5 Q1). → [[FEEG1004 Tutorial 5 - Faraday, Generators and Transformers Solutions#Q1: Bar magnet falling at constant speed through a coil|Tutorial 5 Q1]].
- [ ] Calculate the cable force and state both possible vertical directions (Tutorial Sheet 5 Q3). → [[FEEG1004 Tutorial 5 - Faraday, Generators and Transformers Solutions#Q3: 10 m cable carrying 1 kA DC east–west across a 10⁻⁴ T northward field|Tutorial 5 Q3]].
- [ ] Explain why the two-wire animation's field direction is inconsistent with electron motion (W3 transcript ll. 432–458). → [[#5. Fields from currents and the falling ring]].

## Transcript and slide slips

### Field symbols

> [!warning] Dot and cross directions are reversed briefly
> Where: [[#1. Magnetic field and flux]]
> The W3 transcript ll. 243–245 assigns a dot to an inward field and a cross to an outward field. This is corrected at ll. 301–308: dot is out of the page, cross is into it. Use the corrected convention.

### Falling-ring force

> [!warning] Falling-ring force shorthand omits charge
> Where: [[#3. Force on moving charges]]
> Interactive p. 17 writes $F=B\times v$. The magnetic force on a charge is $\mathbf F_B=q\mathbf v\times\mathbf B$: charge is required and reversing the cross-product order reverses its direction. The complete recorded p. 20 expression gives the correct law.

### Two-wire animation

> [!warning] Electron animation uses the wrong circulating field
> Where: [[#5. Fields from currents and the falling ring]]
> Interactive p. 19 and W3 transcript ll. 449–458 identify a deliberate animation error. If the yellow dots are electrons, conventional current runs opposite to their motion; the drawn field fails the right-hand grip rule.
