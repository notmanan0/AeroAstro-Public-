---
title: "SESA1015 A01 - Astronautics Foundations, Missions and Applications"
module: "SESA1015 Intro to Aero & Astro"
type: topic
stream: "Astronautics"
order: 13
tags: [sesa1015, astronautics, missions, space-applications]
aliases: ["SESA1015 Astronautics 1", "Astronautics Foundations"]
date: 2026-09-27
status: complete
parent: ["[[SESA1015 Intro to Aero & Astro Hub]]"]
prerequisites: []
next_topics: ["[[SESA1015 A02 - Space Environment]]"]
key_concepts: ["[[Space Mission Architecture]]"]
tutorial_sheets: []
sources: ["02 - Sources/Astronautics/Astronautics - Part 1 - Introduction.pdf"]
---

# SESA1015 A01 - Astronautics Foundations, Missions and Applications

> [!abstract] Summary
> Astronautics is the engineering of vehicles and systems that operate beyond the dense atmosphere. A mission begins with a purpose—observe, communicate, navigate, explore or demonstrate—and turns that purpose into measurements, an orbit, a payload, a spacecraft, a launch service, a ground segment and an operations concept. Every later equation sits inside this architecture: an orbit is useful only if it serves the mission, and a launch vehicle is useful only if it inserts the required payload into that orbit.

## 1. What counts as a space mission?

A complete mission is more than the spacecraft. It normally contains:

- a **payload** that produces the mission value;
- a **platform/bus** that keeps the payload powered, pointed, thermally controlled and communicating;
- a **launch segment** that provides injection energy;
- a **ground segment** for command, data reception and processing;
- an **operations concept** describing states, timelines and decisions;
- an **end-of-life plan**.

This is the central systems lesson: success is an end-to-end property.

## 2. Mission classes

| Application | Typical payload need | Orbit/trajectory driver |
|---|---|---|
| Communications | antennas, amplifiers, bandwidth | coverage and latency |
| Navigation/timing | stable clocks and ranging links | geometry and global availability |
| Earth observation | imagers, radar, radiometers | resolution, lighting, revisit |
| Space science | telescopes, fields/particles instruments | viewing geometry and background |
| Planetary exploration | cameras, spectrometers, landers | transfer energy and encounter conditions |
| Human spaceflight | life support, crew safety, return | reliability, radiation and abort options |
| Technology demonstration | novel component/system | affordable access and measurable success |

The mission objective should be measurable. “Observe Earth” is not a usable requirement; “measure sea-surface temperature to stated spatial, temporal and radiometric accuracy” begins to constrain an engineering system.

## 3. From stakeholder need to architecture

The logical flow is

$$\text{need}\rightarrow\text{mission objective}\rightarrow\text{measurement}\rightarrow\text{payload}\rightarrow\text{orbit}\rightarrow\text{system architecture}.$$

Working backwards from a preferred spacecraft is a common design trap. Payload and orbit are coupled: altitude changes coverage, resolution, radiation, drag, link distance, launch energy and lifetime.

## 4. The Solar System as an engineering setting

The Sun dominates the gravitational and radiation environment. Planets, moons, small bodies and interplanetary space supply very different:

- gravitational fields and escape energies;
- atmospheres and entry conditions;
- thermal/radiation environments;
- communication delays and link losses;
- landing surfaces and available resources.

Distance alone does not measure mission difficulty. A close target may have a deep gravity well or severe thermal environment; a distant flyby may avoid capture and landing.

## 5. Historical progression as capability growth

Spaceflight developed through several interacting capabilities:

1. high-energy rocketry;
2. guidance, navigation and control;
3. lightweight structures and thermal protection;
4. reliable electronics and telecommunications;
5. orbital mechanics and tracking;
6. systems engineering and verification;
7. reusable and commercial launch/spacecraft operations.

The useful lesson is not a list of dates but the coupling: no single subsystem creates a space capability on its own.

## 6. Mission success and failure

A mission can fail despite a functioning payload if the orbit, pointing, data link, thermal state, power balance or ground processing is inadequate. Define:

- **mission success criteria**: what outcomes count as success;
- **margins**: mass, power, data, thermal, propellant and schedule reserves;
- **single-point failures**: one failure that loses the mission;
- **fault protection**: detection, isolation and recovery;
- **verification**: evidence that requirements are met.

## 7. A first architecture example

For regional wildfire detection:

1. Need: earlier detection and tracking.
2. Measurement: repeated thermal/visible imaging with specified ground sampling and latency.
3. Payload: calibrated multispectral imager.
4. Orbit: trades coverage, revisit, illumination and downlink access.
5. Bus: pointing stability, onboard processing, power and thermal control.
6. Ground segment: rapid reception and alert delivery.
7. Launch: orbit and rideshare compatibility.

Changing the latency requirement can reshape the constellation and ground network more than changing the camera.

## 8. First-pass questions for any mission

- What physical quantity creates value?
- Where and how often must it be measured?
- What accuracy, resolution and latency are required?
- What environment does the system experience?
- How much $\Delta v$, power and data are needed?
- What can fail, and how will it be detected?
- How does the system reach a safe end state?

## Year 2 bridge

- [[SESA2024 01 - Systems Engineering and Spacecraft Design]] formalises requirements, trades and design phases.
- [[SESA2024 11 - Payload and Orbit Selection]] turns measurement needs into payload/orbit choices.
- [[SESA2024 15 - Space Sustainability, Debris and NewSpace]] adds end-of-life and responsible-use constraints.

