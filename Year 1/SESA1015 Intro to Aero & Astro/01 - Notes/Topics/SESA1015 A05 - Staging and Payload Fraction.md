---
title: "SESA1015 A05 - Staging and Payload Fraction"
module: "SESA1015 Intro to Aero & Astro"
type: topic
stream: "Astronautics"
order: 17
tags: [sesa1015, staging, payload-fraction, mass-ratio]
aliases: ["SESA1015 Astronautics 5", "Rocket Staging"]
date: 2026-09-27
status: complete
parent: ["[[SESA1015 Intro to Aero & Astro Hub]]"]
prerequisites: ["[[SESA1015 A04 - Rocket Equation and Launch Performance]]"]
next_topics: ["[[SESA1015 A06 - Launch Vehicles, Systems and Interfaces]]"]
key_concepts: ["[[Rocket Mass Fractions]]", "[[Multistage Rocket Performance]]"]
tutorial_sheets: []
sources: ["02 - Sources/Astronautics/Astronautics - Part 3 - Launch Vehicles.pdf"]
---

# SESA1015 A05 - Staging and Payload Fraction

> [!abstract] Summary
> A single stage must accelerate its empty tanks, engines and structure all the way to final velocity. Staging discards spent dry mass so later propulsion no longer accelerates it. The total ideal $\Delta v$ is the sum of stage contributions, but the stages are coupled because every lower stage must carry all upper stages and payload. Payload fraction is therefore the sharpest summary of launch difficulty.

## 1. Mass bookkeeping

For a stage plus what it carries,

$$m_0=m_p+m_s+m_L$$

where $m_p$ is propellant, $m_s$ stage dry/structural mass, and $m_L$ everything carried after stage separation.

Useful fractions include

$$\epsilon=\frac{m_s}{m_s+m_p}$$

for stage structural coefficient and

$$\lambda=\frac{m_L}{m_0}$$

for payload ratio relative to that stage's initial mass.

At burnout before jettison,

$$m_f=m_s+m_L.$$

Thus

$$\Delta v=c\ln\left(\frac{m_p+m_s+m_L}{m_s+m_L}\right).$$

## 2. Why staging works

After burnout, $m_s$ cannot contribute more impulse. If retained, it reduces later mass ratio. Jettison removes this dead mass before the next burn.

![[astro_staging.png|760]]

The benefit is largest when discarded mass is large relative to the remaining vehicle. The cost is additional engines, tanks, interfaces, separation hardware, sequencing and failure modes.

## 3. Multistage ideal velocity

For sequential stages,

$$\boxed{\Delta v_{total}=\sum_{i=1}^{N}c_i\ln\frac{m_{0,i}}{m_{f,i}}}.$$

For stage $i$, $m_{0,i}$ includes its own wet mass plus every upper stage and payload. $m_{f,i}$ is the mass immediately before discarding that stage: its dry mass plus the upper stack.

> [!important] Define mass states on a timeline
> Most staging mistakes vanish if every ignition, burnout and separation mass is written explicitly before using a logarithm.

## 4. Payload penalty

Payload appears in the denominator of every stage mass ratio beneath it. Adding one kilogram at orbit requires additional upper-stage propellant and structure, which then requires additional lower-stage propellant. This compounding explains why launch-vehicle payload fraction is small.

## 5. Stage allocation

For idealised equal technologies, distributing $\Delta v$ reasonably across stages can improve payload compared with forcing one stage to supply nearly everything. Real allocation also considers:

- engine sea-level versus vacuum performance;
- thrust-to-weight and burn time;
- atmospheric drag and max-q;
- structural coefficient and tank scale;
- staging altitude/speed and recoverability;
- cost and reliability.

## 6. Parallel and serial staging

- **Serial staging:** one stage burns after another; simple mass timeline.
- **Parallel/stap-on boosters:** stages burn concurrently for some interval and are dropped; thrust and mass-flow histories overlap.
- **Crossfeed:** propellant routing changes which tanks remain full; potentially beneficial but complex.

The simple sum of independent rocket-equation intervals still works only when each interval's masses and effective exhaust velocity are defined correctly.

## 7. Worked two-stage bookkeeping

Consider an upper stage with $m_p=8000\ \mathrm{kg}$, $m_s=1200\ \mathrm{kg}$, payload $=1000\ \mathrm{kg}$ and $c=3400\ \mathrm{m,s^{-1}}$:

$$m_{0,2}=10200\ \mathrm{kg},\qquad m_{f,2}=2200\ \mathrm{kg},$$

$$\Delta v_2=3400\ln(10200/2200)\approx5216\ \mathrm{m,s^{-1}}.$$

For the lower stage, the carried load at ignition is the entire $10200\ \mathrm{kg}$ upper stack, not the $1000\ \mathrm{kg}$ payload alone.

## 8. Reusability trade

Recovery hardware and reserve propellant reduce expendable payload, but reuse can reduce cost, production demand and turnaround risk. “Lower payload” and “worse system” are not synonyms; the objective may be lifecycle cost or launch cadence.

## 9. Workflow

1. Draw the stage stack.
2. Create a mass table at each ignition, burnout and separation.
3. For each burn, identify $m_0$, $m_f$ and $c$.
4. Calculate each logarithmic term separately.
5. Sum ideal contributions.
6. Compare with the mission-plus-loss budget.
7. Check payload and structural fractions for plausibility.

## Year 2 bridge

- [[SESA2023 W10 - Rocket Performance, Staging and Power Cycles]] performs staging optimisation and propulsion-cycle comparisons.
- [[SESA2024 01 - Systems Engineering and Spacecraft Design]] places mass growth and margin inside system budgets.

