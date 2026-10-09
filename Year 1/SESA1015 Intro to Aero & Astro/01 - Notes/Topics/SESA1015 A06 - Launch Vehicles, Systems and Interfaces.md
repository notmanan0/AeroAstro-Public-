---
title: "SESA1015 A06 - Launch Vehicles, Systems and Interfaces"
module: "SESA1015 Intro to Aero & Astro"
type: topic
stream: "Astronautics"
order: 18
tags: [sesa1015, launch-vehicle, interfaces, systems]
aliases: ["SESA1015 Astronautics 6", "Launch Systems and Interfaces"]
date: 2026-09-27
status: complete
parent: ["[[SESA1015 Intro to Aero & Astro Hub]]"]
prerequisites: ["[[SESA1015 A05 - Staging and Payload Fraction]]"]
next_topics: []
key_concepts: ["[[Launch Vehicle Interfaces]]", "[[Space Mission Architecture]]"]
tutorial_sheets: []
sources: ["02 - Sources/Astronautics/Astronautics - Part 3 - Launch Vehicles.pdf"]
---

# SESA1015 A06 - Launch Vehicles, Systems and Interfaces

> [!abstract] Summary
> A launch vehicle is an integrated delivery system: propulsion, propellant tanks, structures, guidance, control, avionics, separation devices, fairing, ground infrastructure and range safety must work as one timed sequence. Payload compatibility is multidimensional—mass and orbit are only the beginning. Mechanical envelope, centre of mass, loads, vibration, shock, cleanliness, electrical services, communications and operations must all close.

## 1. Launch-system architecture

Major elements include:

- propulsion and feed systems;
- propellant tanks and pressurisation;
- primary structure and interstages;
- guidance, navigation and control;
- avionics, telemetry and flight termination/range safety;
- payload adapter and separation system;
- fairing and environmental control;
- launch pad, transport, integration and ground support equipment.

The launch vehicle plus ground and range systems form the launch service.

## 2. Guidance, navigation and control

- **Navigation** estimates position, velocity, attitude and angular rate.
- **Guidance** computes the desired trajectory or steering command.
- **Control** moves thrust vector or aerodynamic surfaces to follow it.

Common actuators include gimballed engines, differential throttling, reaction-control thrusters and, in the atmosphere, fins. Guidance must respect loads, heating, range safety and propellant limits, not only reach the final orbit.

## 3. Structural load path

Thrust generated at the engine passes through stage structure, interstages, adapters and the payload. Tanks may be load-bearing. Interfaces carry:

- axial force;
- shear;
- bending moment;
- torsion;
- local bolt/clamp loads.

Stiffness is as important as strength because deflection and modes affect control stability, clearance and payload response.

## 4. Payload mechanical interface

Compatibility checks include:

- payload mass and centre-of-mass envelope;
- moments of inertia;
- static envelope and fairing clearance;
- adapter diameter and bolt/clamp pattern;
- fundamental-frequency requirements;
- allowable interface loads;
- separation clearance and tip-off rates.

The quoted maximum payload mass applies to a particular orbit, inclination, launch site and recovery/mission profile.

## 5. Electrical and data interface

Before separation, the vehicle may provide:

- power and battery charging;
- purge/heater control;
- discrete commands and inhibits;
- telemetry channels;
- timing and separation signals;
- grounding/bonding.

Safe/arm logic prevents inadvertent deployment or propulsion activation. After separation, responsibility transfers cleanly to the spacecraft's autonomous sequence.

## 6. Environmental interface

The payload user's guide defines envelopes for:

- temperature, humidity and cleanliness during processing;
- fairing pressure and depressurisation;
- acoustic and vibration spectra;
- shock response;
- quasi-static and coupled loads;
- electromagnetic compatibility.

[[SESA1015 A03 - Launch Environment]] explains why each is distinct.

## 7. Mission interface

The service must deliver a specified injection state and accuracy:

- orbit/trajectory and epoch;
- position/velocity dispersions;
- attitude and angular rates at separation;
- coast duration and illumination;
- collision-avoidance manoeuvre after separation.

Injection error can consume spacecraft propellant and shorten mission life.

## 8. Launch-site and Earth-rotation effects

Earth's eastward rotation supplies useful inertial velocity for prograde launches. Benefit depends on latitude and launch azimuth. Safety corridors and population constrain directions. High-inclination or polar launches require suitable sites and may sacrifice rotational benefit.

## 9. Reliability and sequencing

A launch is a tightly sequenced state machine: ignition, release, throttle events, cutoff, separation, restart, fairing release and payload deployment. Fault-management logic must distinguish a sensor fault from a real vehicle anomaly under severe vibration and limited time.

## 10. Interface-control workflow

1. Define mission orbit and injection tolerances.
2. Select candidate launch services from performance data.
3. Check payload envelope, mass properties and adapter.
4. Map all environmental limits and test evidence.
5. Close power, data, grounding and command interfaces.
6. Analyse coupled loads and separation.
7. Rehearse integration, countdown and early-orbit sequences.
8. Baseline changes through interface-control documents.

> [!failure] Common errors
> - Selecting a launcher from payload mass alone.
> - Treating a user-guide envelope as the predicted value rather than a qualification requirement.
> - Ignoring injection dispersion and separation tip-off.
> - Leaving ground operations and inhibits until late design.

## Year 2 bridge

- [[SESA2024 01 - Systems Engineering and Spacecraft Design]] formalises interface control and verification.
- [[SESA2024 03 - Orbital Elements and Conic Sections]] defines the delivered orbit state.
- [[SESA2024 04 - Orbital Energy and the Vis-Viva Equation]] relates injection velocity to orbit energy.
- [[SESA2024 05 - Orbital Transfers and the Hohmann Transfer]] covers the manoeuvres after launch injection.

