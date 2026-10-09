---
title: "SESA1016 T3 - Heat Engines and the Second Law"
module: "SESA1016 Thermofluids"
type: topic
stream: "Part A: Closed-system Thermodynamics"
order: 3
tags: [sesa1016, heat-engine, second-law, efficiency]
aliases: ["Heat Engines"]
date: 2026-09-25
status: complete
parent: ["[[SESA1016 Thermofluids Hub]]"]
prerequisites: ["[[SESA1016 T2 - Work, Heat and the First Law]]"]
next_topics: ["[[SESA1016 T4 - Entropy and Isentropic Relations]]"]
key_concepts: ["[[Thermal Efficiency and COP]]", "[[Entropy Generation]]"]
tutorial_sheets: ["[[SESA1016 Problem Sheet 03 - Heat Engines and Entropy Solutions]]"]
sources: ["02 - Sources/Lectures/Chapter 3.pdf"]
---

# SESA1016 T3 - Heat Engines and the Second Law

> [!abstract] Summary
> A heat engine repeats a thermodynamic cycle, receiving heat from a hot reservoir, rejecting some heat to a cold reservoir and delivering net work. The first law fixes the energy balance; the second law says that no cyclic engine can convert all supplied heat to work. Reversibility defines an upper limit, not a claim that real engines can reach it.

## 1. Why a cycle is necessary

A single expansion can produce work, but a practical engine must return its working fluid to the initial state. Over one cycle every property returns to its starting value:

$$
\Delta U_{cycle}=0\quad\Rightarrow\quad W_{net,out}=Q_{net,in}=Q_H-Q_C
$$

The area enclosed on a $p$-$V$ diagram is the net work. Clockwise cycles produce net work; anticlockwise cycles require net work.

## 2. Thermal efficiency

$$
\boxed{\eta_{th}=\frac{W_{net,out}}{Q_H}=1-\frac{Q_C}{Q_H}}
$$

Efficiency is not $W/Q_C$, nor is it work from one process divided by total heat. Identify the heat input $Q_H$ across all heat-addition legs.

![[tf_heat_engine_energy_flow.png|650]]

## 3. Second law

> [!note] Kelvin-Planck statement
> No device operating in a cycle can receive heat from a single reservoir and convert it entirely into an equivalent amount of work.

Therefore $Q_C>0$ for a cyclic heat engine and $\eta_{th}<1$. The first law alone would permit $Q_C=0$; the second law forbids it.

The second law also gives processes a direction: heat flows spontaneously from hot to cold; friction dissipates mechanical energy; mixing and unrestrained expansion do not reverse themselves.

## 4. Refrigerators and heat pumps

Reversing the desired transfer requires work input:

$$
W_{net,in}=Q_H-Q_C
$$

$$
COP_R=\frac{Q_C}{W_{net,in}},\qquad COP_{HP}=\frac{Q_H}{W_{net,in}}=COP_R+1
$$

A COP can exceed one because it measures heat moved per unit work, not energy conversion efficiency.

## 5. Reversible and irreversible processes

A reversible process is an ideal limiting process that can be reversed without leaving any net change in system **or surroundings**. It requires:

- infinitesimal pressure and temperature differences;
- no friction, viscosity, inelastic deformation or uncontrolled mixing;
- quasi-equilibrium throughout.

Real processes are irreversible. Their departure from reversibility destroys work potential and generates entropy.

## 6. Carnot limit

For an engine operating between fixed reservoir temperatures:

$$
\boxed{\eta_{max}=\eta_C=1-\frac{T_C}{T_H}}
$$

Temperatures are absolute. A proposed engine with $\eta>\eta_C$ violates the second law even if its first-law energy balance closes.

## 7. Feasibility checklist

For any claimed cyclic device:

1. first law: does $Q_H=W+Q_C$?
2. signs: are heat and work directions stated consistently?
3. second law: is $0\le\eta\le\eta_C$?
4. if not, the device is impossible or the data/sign convention is wrong.

## Links

- Previous: [[SESA1016 T2 - Work, Heat and the First Law]]
- Concepts: [[Thermal Efficiency and COP]] · [[Entropy Generation]]
- Tutorial: [[SESA1016 Problem Sheet 03 - Heat Engines and Entropy Solutions]]
- Continues in Propulsion: [[SESA2023 W01 - Thrust, Efficiency, Range and the ISA]] · [[Thermal and Overall Efficiency]]
- Next: [[SESA1016 T4 - Entropy and Isentropic Relations]]

## Sources

- `02 - Sources/Lectures/Chapter 3.pdf`, §§3.1-3.5.
